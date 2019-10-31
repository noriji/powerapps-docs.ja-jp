---
title: Postman を使用して Web API で演算を実行する (アプリ用 Common Data Service) | MicrosoftDocs
description: Postman を使用して Web API 要求を構成して送信する方法を説明します。
ms.custom: null
ms.date: 03/22/2019
ms.reviewer: null
ms.service: powerapps
ms.suite: null
ms.tgt_pltfrm: null
ms.topic: article
ms.assetid: AB50128B-D8E3-47A3-A0F8-9594EF6B7022
caps.latest.revision: 7
author: susikka
ms.author: susikka
manager: shujoshi
search.audienceType:
  - developer
search.app:
  - D365CE
---

# <a name="use-postman-to-perform-operations-with-the-web-api"></a>Postman を使用してその Web API で操作を実行する

Postman を使用して Web API 要求を構成および送信し、応答を表示します。 このトピックでは、Postman を使用して作成、取得、更新、および削除 (CRUD) 操作を実行して機能とアクションを使用する Web API 要求を作成する方法について説明します。

> [!IMPORTANT]
> [Postman 環境の設定](setup-postman-environment.md) で説明されている手順を使用して作成された環境が必要です。

[Postman 環境の設定](setup-postman-environment.md) の手順を使用して作成した環境は、要求に対して基本 URL を提供する `{{webapiurl}}` Postman 変数を作成します。 要求の URL を定義するこの変数を追加します。

使用する HTTP メソッドと値は実行する操作の種類によって異なります。 次のセクションでは一般的な操作の例を示します。

## <a name="retrieve-multiple-records"></a>複数のレコードの取得

`GET` 要求を使用して、レコードのセットを取得します。 次の例では、最初の 3 つの取引先企業レコードを取得します。

> [!NOTE]
> Web API 要求には特定の HTTP ヘッダーを含める必要があります。 すべての要求には、`Accept` ヘッダー値として `application/json` を含める必要があります。予期される応答がない場合でも、含める必要があります。 現在の OData バージョンは `4.0` なので、ヘッダー `OData-Version: 4.0` が含まれます。 `OData-MaxVersion` ヘッダーを含むため、OData の新しいリリースがある場合もバージョンに関する曖昧さはありません。 詳細: [HTTP ヘッダー](compose-http-requests-handle-errors.md#http-headers)。

**例**


`GET` `{{webapiurl}}accounts?$select=name,accountnumber&$top=3`

![Postman を使用した複数のレコードの取得](media/postman-retrieve-multiple.png "Postman を使用した複数のレコードの取得")

応答の本文は次のようになります。

```json
{
    "@odata.context": "https://yourorg.crm.dynamics.com/api/data/v9.0/$metadata#accounts(name,accountnumber)",
    "value": [
        {
            "@odata.etag": "W/\"2291741\"",
            "name": "Contoso Ltd",
            "accountnumber": null,
            "accountid": "9c706dc8-d2f5-e711-a956-000d3a328903"
        },
        {
            "@odata.etag": "W/\"2291742\"",
            "name": "Fourth Coffee",
            "accountnumber": null,
            "accountid": "a2706dc8-d2f5-e711-a956-000d3a328903"
        },
        {
            "@odata.etag": "W/\"2291743\"",
            "name": "Contoso Ltd",
            "accountnumber": null,
            "accountid": "9c3216b8-3efb-e711-a957-000d3a328903"
        }
    ]
}
```

詳細については、[Web API を使用するクエリ データ](query-data-web-api.md)を参照してください。

## <a name="retrieve-a-particular-record"></a>特定のレコードの取得

`GET` 要求を使用してレコードを取得します。 次の例は、特定の取引先企業から 2 つのプロパティを取得して、関連する取引先責任者に関する情報を展開して氏名を含めます。


`GET` `{{webapiurl}}accounts(`*&lt;accountid&gt;*`)?$select=name,accountnumber&$expand=primarycontactid($select=fullname)`

![Postman を使用してレコードを取得する](media/postman-retrieve-record.png "Postman を使用してレコードを取得する")

応答の本文は次のようになります。

```json
{
    "@odata.context": "https://yourorg.crm.dynamics.com/api/data/v9.0/$metadata#accounts(name,accountnumber,primarycontactid(fullname))/$entity",
    "@odata.etag": "W/\"2291742\"",
    "name": "Fourth Coffee",
    "accountnumber": null,
    "accountid": "a2706dc8-d2f5-e711-a956-000d3a328903",
    "primarycontactid": {
        "@odata.etag": "W/\"1697263\"",
        "fullname": "Susie Curtis",
        "contactid": "a3706dc8-d2f5-e711-a956-000d3a328903"
    }
}
```
詳細については、[Web API を使用してエンティティを取得する](retrieve-entity-using-web-api.md)を参照してください。

## <a name="create-a-record"></a>レコードの作成

`POST` 要求を使用して、レコードを作成するデータを送信します。 エンティティ セット名 -- この場合は `accounts` -- に URL を設定し、そしてここで示すようにヘッダーを設定します。

`POST` `{{webapiurl}}accounts`

![Web API を使用して新しいレコードを作成する](media/postman-create-records.png "Web API を使用して新しいレコードを作成する")

作成する取引先企業に関する情報を使用して要求の本体を設定します。

![Web API を使用してレコードを作成する要求の本体](media/postman-create-record-body.png "Web API を使用してレコードを作成する要求の本体")

この要求を送信するとき、本体は空になりますが、作成された取引先企業の ID は `OData-EntityId` ヘッダー値にあります。

詳細については、[Web API を使用してエンティティを作成する](create-entity-web-api.md)を参照してください。

## <a name="update-a-record"></a>レコードの更新

ここで示すように、`PATCH` メソッドを使用してエンティティ レコードを更新します。

`PATCH` `{{webapiurl}}accounts(`*&lt;accountid&gt;*`)`

![Web API を使用してレコードを更新する](media/postman-update-record.png "Web API を使用してレコードを更新する")

この要求を送信するとき、応答の本体は空になりますが、更新された取引先企業の ID は `OData-EntityId` ヘッダー値にあります。

詳細については、[Web API を使用してエンティティを更新および削除する](update-delete-entities-using-web-api.md)を参照してください。

## <a name="delete-a-record"></a>レコードを削除する

`DELETE` メソッドを使用して既存のレコードを削除します。

`DELETE` `{{webapiurl}}accounts(`*&lt;accountid&gt;*`)`

![Web API を使用してレコードを削除する](media/postman-delete-record.png "Web API を使用してレコードを削除する")

この要求を送信するとき、指定された `accountid` を持つ取引先企業レコードは削除されます。

詳細については、[Web API を使用してエンティティを更新および削除する](update-delete-entities-using-web-api.md)を参照してください。

## <a name="use-a-function"></a>関数の使用

[Web API 関数リファレンス](https://docs.microsoft.com/dynamics365/customer-engagement/web-api/functions?view=dynamics-ce-odata-9) に一覧表示されている関数を持つ `GET` 要求を使用して、Web API で再使用可能な操作を実行します。 以下の例は <xref href="Microsoft.Dynamics.CRM.RetrieveDuplicates?text=RetrieveDuplicates function" /> を使用する Web API 要求を送信して、指定したレコードの重複を検知し取得する方法を示します。

|||
|----|----|
|`GET`|`{{webapiurl}}RetrieveDuplicates(BusinessEntity=@p1,MatchingEntityName=@p2,PagingInfo=@p3)?@p1={'@odata.type':'Microsoft.Dynamics.CRM.account','accountid':'`*&lt;accountid&gt;*`'}&@p2='account'&@p3={'PageNumber':1,'Count':50}`|

![関数を使用する Web API 要求を作成する](media/postman-use-function.png "関数を使用する Web API 要求を作成する")

関数はコレクションまたは複合型のいずれかを返します。 前述の <xref href="Microsoft.Dynamics.CRM.RetrieveDuplicates?text=RetrieveDuplicates function" /> からの応答は次のようになります:

```json
{
        {
    "@odata.context": "https://yourorgname.crm.dynamics.com/api/data/v9.0/$metadata#accounts",
    "value": [
        <Omitted for brevity: JSON data for any matching accounts including all properties>
    ]
}
}
```

詳細: [Web API 機能を使用](use-web-api-functions.md) を参照してください。

## <a name="use-an-action"></a>アクションを使用する

`POST` 要求と [Web API アクション リファレンス](https://docs.microsoft.com/dynamics365/customer-engagement/web-api/actions?view=dynamics-ce-odata-9) に一覧表示されているアクションを使用して、副作用がある操作を実行します。

このサンプルは <xref href="Microsoft.Dynamics.CRM.BulkDetectDuplicates?text=BulkDetectDuplicates action" /> の使用方法を示します。

`POST` `{{webapiurl}}BulkDetectDuplicates`

![アクションを使用する Web API 要求を作成する](media/postman-use-action.png "アクションを使用する Web API 要求を作成する")

先に示した例の要求は、バックグラウンドで実行される非同期的な重複データ検出ジョブを送信します。 重複データは、このエンティティの種類に対する公開済みの重複データ ルールに従って検出されます。 <xref href="Microsoft.Dynamics.CRM.BulkDetectDuplicatesResponse?text=BulkDetectDuplicatesResponse ComplexType" /> は <xref href="Microsoft.Dynamics.CRM.BulkDetectDuplicates?text=BulkDetectDuplicates action" /> からの応答として戻されます。 応答には `JobId` プロパティが含まれ、これには重複レコードを検出して記録する非同期重複データ検出ジョブの GUID が含まれます。

詳細: [Web API アクションの使用](use-web-api-actions.md) を参照してください。

## <a name="see-also"></a>関連項目

[Web API で Postman を使用する](use-postman-web-api.md)<br>
[Web API を使用して演算を実行する](perform-operations-web-api.md)
