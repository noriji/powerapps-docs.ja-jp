---
title: WebHooks を使用してサーバー イベントの外部ハンドラーを作成する (Common Data Service)| Microsoft Docs
description: webhook を使用してサーバーで発生するイベントに関するデータを Web アプリケーションに送信できます。 ｗebhook は、Web API およびサービスをパブリッシュ/サブスクライブ モデルと接続するためのライトウェイト HTTP パターンです。 ｗebhook の送信側は、イベントに関する情報を使用して受信側のエンドポイントに要求を行うことで、受信側にイベントについて通知します。
ms.custom: ''
ms.date: 09/04/2019
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: brandonsimons
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="use-webhooks-to-create-external-handlers-for-server-events"></a>ｗebhook を使用してサーバー イベント用に外部ハンドラーを作成する

Common Data Service により、webhooks を使用してサーバーで発生するイベントに関するデータを Web アプリケーションに送信できます。 ｗebhook は、Web API およびサービスをパブリッシュ/サブスクライブ モデルと接続するためのライトウェイト HTTP パターンです。 ｗebhook の送信側は、イベントに関する情報を使用して受信側のエンドポイントに要求を行うことで、受信側にイベントについて通知します。

ｗebhook を使用すると、開発者と ISV は Common Data Service のデータを、外部サービスでホストされている自らのカスタム コードに統合できます。 ｗebhook モデルを使用することにより、認証ヘッダーまたはクエリ文字列パラメーター キーを使用してエンドポイントを保護できます。 これは、Azure Service Bus 統合用に現在使用できる SAS 認証モデルよりも簡単です。

webhook モデルと Azure Service Bus 統合とのどちらを選ぶか選択する場合、次の点に留意します。

- Azure Service Bus はハイスケール処理に向いており、Common Data Service が多くのイベントをプッシュする場合にフルキュー メカニズムを提供します。
- webhook は、ご使用のホステッド Web サービスがメッセージを処理できるポイントまでのみスケールできます。
- webhook では同期および非同期のステップが可能です。 Azure Service Bus は非同期の手順でのみ有効になります。
- webhook は JSON ペイロードの送信 POST 要求のみを送信し、任意のプログラミング言語または任意の場所でホストされる Webアプリケーションで使用できます。
- webhook と Azure Service Bus のいずれも、プラグインまたはユーザー定義のワークフロー活動から呼び出すことができます。


## <a name="get-started"></a>はじめに

webhook の使用には3つの部分があります。

- webhook 要求を使用するためにサービスを作成または構成する。
- Common Data Service サービスで webhook のステップを登録する。または、
- プラグインまたはユーザー定義ワークフロー活動から webhook を呼び出す。 

### <a name="start-by-registering-a-test-webhook"></a>テスト webhook の登録により開始する

Common Data Service から webhook 要求を使用するようにサービスを作成して構成する方法を理解するには、webhook の登録方法を理解することから開始することが重要です。 詳細: [webhook の登録](register-web-hook.md)

webhook の例を登録した場合、渡されたコンテキスト データを確認するために要求ログ サイトを使用できます。 詳細: [要求ログ サイトで webhook 登録をテストする](test-webhook-registration.md)

> [!TIP]
> テスト webhook を登録するための手順を完了して、渡されたコンテキスト データを調べると、このトピックの情報の残りをより簡単に理解するようにできます。 これらの手順を完了し、このトピックに返します。

<a name="create-or-configure"></a>

## <a name="create-or-configure-a-service-to-consume-webhook-requests"></a>webhook 要求を使用するためにサービスを作成または構成する

webhook は幅広い技術を使用して適用できる単なるパターンです。 使用する必要のあるフレームワーク、プラットフォーム、またはプログラミング言語はありません。 自分のスキルやノウハウを駆使して適切なソリューションを提供します。 

[Azure Functions](https://azure.microsoft.com/services/functions/) は webhook を使用してソリューションを提供する優れた方法ですが、必須要件ではありません。 このセクションでは、具体的なソリューションに対するガイドを提供するのではなく、ご自分のサービスに付加価値をもたらすデータの受け渡しについて取り上げます。

「[要求ログ サイトで webhook 登録をテストする](test-webhook-registration.md)」で示したように、テスト webhook ステップを登録して、要求ログ サイトを使用してご自分のアプリケーションが処理できる特定のデータの種類を取得できます。 

### <a name="data-passed-to-the-service"></a>サービスに受け渡されるデータ

要求には、クエリ文字列、ヘッダー データ、および要求本文の 3 種類のデータがあります。

#### <a name="query-string"></a>クエリ文字列

「[認証オプション](register-web-hook.md#authentication-options)」で説明されているように、webhook で **WebhookKey** または **HttpQueryString** オプションを使用するよう構成されている場合は、クエリ文字列として受け渡される唯一のデータは認証値となる可能性があります。 

#### <a name="header-data"></a>ヘッダー データ

**HttpHeader** 認証オプションを選択すると、サービスが要求するキー/値のペアを使用する必要があります。

サービスに受け渡される他のデータについては次の表に示されています。


|Key|値の説明|
|---------|---------|
|`x-request-id`|要求の一意の識別子|
|`x-ms-dynamics-organization`|要求を送信するテナントの名前|
|`x-ms-dynamics-entity-name`|実行コンテキスト データで渡されるエンティティの論理名。|
|`x-ms-dynamics-request-name`|webhook のステップが登録されたイベントの名前。|
|`x-ms-correlation-request-id`|任意の拡張機能の種類を追跡するための一意の識別子。 このプロパティは、無限ループ防止のためにプラットフォームで使用されます。 ほとんどの場合、このプロパティは無視できます。 この値は、操作全体で生じた事柄を把握するためにテレメトリをクエリできるため、テクニカル サポートを扱う際に使用できます。
|`x-ms-dynamics-msg-size-exceeded`|HTTP ペイロード サイズが 256KB を超えた場合にのみ送信。|


#### <a name="request-body"></a>要求本文

本文には、<xref:Microsoft.Xrm.Sdk.RemoteExecutionContext> クラスのインスタンスの JSON 値を表す文字列が含まれます。 これは Azure サービス バス統合に受け渡されるのと同じデータです。 

作成したサービスは、サービスが機能を提供するために必要な関連情報アイテムを抽出するために、このデータを解析する必要があります。 データの解析方法は、使用している技術と設定によって異なります。

> [!IMPORTANT]
> 特定の Service Bus による最適化のために、.NET 型の開発者がその <xref:Microsoft.Xrm.Sdk.RemoteExecutionContext> オブジェクトのために JSON 形式の要求メッセージ本文を 非シリアル化することはお勧めできません。 そうではなく、[JObject](https://www.newtonsoft.com/json/help/html/T_Newtonsoft_Json_Linq_JObject.htm) を、メッセージ本文を解析するために使用します。

次の例は、次のプロパティで登録されているステップに渡されるシリアル化 JSON データを示しています。


|プロパティ|内容|
|---------|---------|
|**メッセージ**|更新プログラム|
|**主エンティティ**|取引先担当者|
|**副エンティティ**|なし|
|**フィルタリング属性**|名、姓|
|**ユーザーのコンテキストで実行**|呼び出し元ユーザー|
|**実行する順番**|1|
|**実行のイベント パイプライン ステージ**|PostOperation|
|**実行モード**|非同期|

```json
{
    "BusinessUnitId": "e2b9dd85-e89e-e711-8122-000d3aa2331c",
    "CorrelationId": "b374239d-4233-41a9-8b17-a86cb4f737b5",
    "Depth": 1,
    "InitiatingUserId": "75c2dd85-e89e-e711-8122-000d3aa2331c",
    "InputParameters": [{
        "key": "Target",
        "value": {
            "__type": "Entity:http:\/\/schemas.microsoft.com\/xrm\/2011\/Contracts",
            "Attributes": [{
                "key": "firstname",
                "value": "James"
            }, {
                "key": "contactid",
                "value": "6d81597f-0f9f-e711-8122-000d3aa2331c"
            }, {
                "key": "fullname",
                "value": "James Glynn (sample)"
            }, {
                "key": "yomifullname",
                "value": "James Glynn (sample)"
            }, {
                "key": "modifiedon",
                "value": "\/Date(1506384247000)\/"
            }, {
                "key": "modifiedby",
                "value": {
                    "__type": "EntityReference:http:\/\/schemas.microsoft.com\/xrm\/2011\/Contracts",
                    "Id": "75c2dd85-e89e-e711-8122-000d3aa2331c",
                    "KeyAttributes": [],
                    "LogicalName": "systemuser",
                    "Name": null,
                    "RowVersion": null
                }
            }, {
                "key": "modifiedonbehalfby",
                "value": null
            }],
            "EntityState": null,
            "FormattedValues": [],
            "Id": "6d81597f-0f9f-e711-8122-000d3aa2331c",
            "KeyAttributes": [],
            "LogicalName": "contact",
            "RelatedEntities": [],
            "RowVersion": null
        }
    }],
    "IsExecutingOffline": false,
    "IsInTransaction": false,
    "IsOfflinePlayback": false,
    "IsolationMode": 1,
    "MessageName": "Update",
    "Mode": 1,
    "OperationCreatedOn": "\/Date(1506409448000-0700)\/",
    "OperationId": "4af10637-4ea2-e711-8122-000d3aa2331c",
    "OrganizationId": "4ef5b371-e89e-e711-8122-000d3aa2331c",
    "OrganizationName": "OrgName",
    "OutputParameters": [],
    "OwningExtension": {
        "Id": "75417616-4ea2-e711-8122-000d3aa2331c",
        "KeyAttributes": [],
        "LogicalName": "sdkmessageprocessingstep",
        "Name": null,
        "RowVersion": null
    },
    "ParentContext": {
        "BusinessUnitId": "e2b9dd85-e89e-e711-8122-000d3aa2331c",
        "CorrelationId": "b374239d-4233-41a9-8b17-a86cb4f737b5",
        "Depth": 1,
        "InitiatingUserId": "75c2dd85-e89e-e711-8122-000d3aa2331c",
        "InputParameters": [{
            "key": "Target",
            "value": {
                "__type": "Entity:http:\/\/schemas.microsoft.com\/xrm\/2011\/Contracts",
                "Attributes": [{
                    "key": "firstname",
                    "value": "James"
                }, {
                    "key": "contactid",
                    "value": "6d81597f-0f9f-e711-8122-000d3aa2331c"
                }],
                "EntityState": null,
                "FormattedValues": [],
                "Id": "6d81597f-0f9f-e711-8122-000d3aa2331c",
                "KeyAttributes": [],
                "LogicalName": "contact",
                "RelatedEntities": [],
                "RowVersion": null
            }
        }, {
            "key": "SuppressDuplicateDetection",
            "value": false
        }],
        "IsExecutingOffline": false,
        "IsInTransaction": false,
        "IsOfflinePlayback": false,
        "IsolationMode": 1,
        "MessageName": "Update",
        "Mode": 1,
        "OperationCreatedOn": "\/Date(1506409448000-0700)\/",
        "OperationId": "4af10637-4ea2-e711-8122-000d3aa2331c",
        "OrganizationId": "4ef5b371-e89e-e711-8122-000d3aa2331c",
        "OrganizationName": "OneFarm",
        "OutputParameters": [],
        "OwningExtension": {
            "Id": "75417616-4ea2-e711-8122-000d3aa2331c",
            "KeyAttributes": [],
            "LogicalName": "sdkmessageprocessingstep",
            "Name": null,
            "RowVersion": null
        },
        "ParentContext": null,
        "PostEntityImages": [],
        "PreEntityImages": [],
        "PrimaryEntityId": "6d81597f-0f9f-e711-8122-000d3aa2331c",
        "PrimaryEntityName": "contact",
        "RequestId": null,
        "SecondaryEntityName": "none",
        "SharedVariables": [{
            "key": "ChangedEntityTypes",
            "value": [{
                "__type": "KeyValuePairOfstringstring:#System.Collections.Generic",
                "key": "feedback",
                "value": "Update"
            }, {
                "__type": "KeyValuePairOfstringstring:#System.Collections.Generic",
                "key": "contract",
                "value": "Update"
            }, {
                "__type": "KeyValuePairOfstringstring:#System.Collections.Generic",
                "key": "salesorder",
                "value": "Update"
            }, {
                "__type": "KeyValuePairOfstringstring:#System.Collections.Generic",
                "key": "connection",
                "value": "Update"
            }, {
                "__type": "KeyValuePairOfstringstring:#System.Collections.Generic",
                "key": "socialactivity",
                "value": "Update"
            }, {
                "__type": "KeyValuePairOfstringstring:#System.Collections.Generic",
                "key": "postfollow",
                "value": "Update"
            }, {
                "__type": "KeyValuePairOfstringstring:#System.Collections.Generic",
                "key": "incident",
                "value": "Update"
            }, {
                "__type": "KeyValuePairOfstringstring:#System.Collections.Generic",
                "key": "invoice",
                "value": "Update"
            }, {
                "__type": "KeyValuePairOfstringstring:#System.Collections.Generic",
                "key": "entitlement",
                "value": "Update"
            }, {
                "__type": "KeyValuePairOfstringstring:#System.Collections.Generic",
                "key": "lead",
                "value": "Update"
            }, {
                "__type": "KeyValuePairOfstringstring:#System.Collections.Generic",
                "key": "opportunity",
                "value": "Update"
            }, {
                "__type": "KeyValuePairOfstringstring:#System.Collections.Generic",
                "key": "quote",
                "value": "Update"
            }, {
                "__type": "KeyValuePairOfstringstring:#System.Collections.Generic",
                "key": "socialprofile",
                "value": "Update"
            }, {
                "__type": "KeyValuePairOfstringstring:#System.Collections.Generic",
                "key": "contact",
                "value": "Update"
            }]
        }],
        "Stage": 30,
        "UserId": "75c2dd85-e89e-e711-8122-000d3aa2331c"
    },
    "PostEntityImages": [{
        "key": "AsynchronousStepPrimaryName",
        "value": {
            "Attributes": [{
                "key": "fullname",
                "value": "James Glynn (sample)"
            }, {
                "key": "contactid",
                "value": "6d81597f-0f9f-e711-8122-000d3aa2331c"
            }],
            "EntityState": null,
            "FormattedValues": [],
            "Id": "6d81597f-0f9f-e711-8122-000d3aa2331c",
            "KeyAttributes": [],
            "LogicalName": "contact",
            "RelatedEntities": [],
            "RowVersion": null
        }
    }],
    "PreEntityImages": [],
    "PrimaryEntityId": "6d81597f-0f9f-e711-8122-000d3aa2331c",
    "PrimaryEntityName": "contact",
    "RequestId": null,
    "SecondaryEntityName": "none",
    "SharedVariables": [],
    "Stage": 40,
    "UserId": "75c2dd85-e89e-e711-8122-000d3aa2331c"
}
```
> [!IMPORTANT]
> 全体の HTTP ペイロードのサイズが 256KB を超えると、`x-ms-dynamics-msg-size-exceeded` ヘッダーが含まれ、次の <xref:Microsoft.Xrm.Sdk.RemoteExecutionContext> プロパティが削除されます。
> 
> - <xref:Microsoft.Xrm.Sdk.RemoteExecutionContext.ParentContext>
> - <xref:Microsoft.Xrm.Sdk.RemoteExecutionContext.InputParameters>
> - <xref:Microsoft.Xrm.Sdk.RemoteExecutionContext.PreEntityImages>
> - <xref:Microsoft.Xrm.Sdk.RemoteExecutionContext.PostEntityImages>
> 
>一部の操作では、次のプロパティは含まれません。

## <a name="invoke-a-webhook-from-a-plugin-or-workflow-activity"></a>プラグインまたはワークフロー活動から webhook を呼び出す

webhook はサービス エンドポイントの一種であるため、Azure Service Bus エンドポイントで行うのと同様に、プラグインやワークフロー活動でステップを登録することなく呼び出すことができます。  [ServiceEndpointId](reference/entities/serviceendpoint.md#BKMK_ServiceEndpointId) を <xref:Microsoft.Xrm.Sdk.IServiceEndpointNotificationService> インターフェイスに提供する必要があります。 詳細については、次の Azure Service Bus のサンプルを参照してください: 
- [サンプル: Azure 対応のカスタム プラグイン](org-service/samples/azure-aware-custom-plugin.md)
- [サンプル: Azure 対応のユーザー定義ワークフロー活動](org-service/samples/azure-aware-custom-workflow-activity.md)


## <a name="troubleshoot-web-hook-registrations"></a>web hook 登録のトラブルシューティング

webhook 比較的簡単です。 サービスは要求を送信して応答を評価します。 システムは応答の本文で返されたデータを解析できず、応答の `StatusCode` 値だけを見ます。

タイムアウトは 60 秒です。 通常は、タイムアウト期間前、または応答の `StatusCode` 値が成功または失敗を示す `2xx` の範囲内にない場合、応答は返されません。 返されたエラーが次の表にある場合は例外です。

|`StatusCode`|内容|
|-|-|
|`502`|誤ったゲートウェイ|
|`503`|サービスは使用できません|
|`504`|ゲートウェイのタイムアウト|

これらのエラーは、再度の試みによって解決される可能性がある問題を示しています。 webhook サービスは、これらのエラー コードが返されたときにのみさらに 1 回試行します。

### <a name="asynchronous-webhooks"></a>非同期 webhooks

webhook が非同期的で実行するために登録されている場合、エラー詳細については、システム ジョブを確認できます。 詳細: [特定のステップで失敗した非同期ジョブをクエリする](register-web-hook.md#query-failed-asynchronous-jobs-for-a-given-step)

### <a name="synchronous-webhooks"></a>同期 webhooks

[!INCLUDE [synchronous-webhook-error](includes/synchronous-webhook-error.md)]

## <a name="next-steps"></a>次のステップ
[webhook の登録](register-web-hook.md)<br />
[要求ログ サイトで webhook 登録をテストする](test-webhook-registration.md)

### <a name="see-also"></a>関連項目

[プラグインを記述する](write-plug-in.md)<br />
[プラグインの登録](register-plug-in.md)<br />
[Common Data Service での非同期サービス](asynchronous-service.md)<br />
[サンプル: Azure 対応のカスタム プラグイン](org-service/samples/azure-aware-custom-plugin.md)<br />
[サンプル: Azure 対応のユーザー定義ワークフロー活動](org-service/samples/azure-aware-custom-workflow-activity.md)<br />
[Azure Functions](https://azure.microsoft.com/services/functions/)<br />
[ServiceEndpoint エンティティ](reference/entities/serviceendpoint.md)<br />
[SdkMessageProcessingStep エンティティ](reference/entities/sdkmessageprocessingstep.md)<br />
[AsynchronousOperations エンティティ](reference/entities/asyncoperation.md)<br />
<xref:Microsoft.Xrm.Sdk.RemoteExecutionContext><br />
<xref:Microsoft.Xrm.Sdk.IServiceEndpointNotificationService><br />
