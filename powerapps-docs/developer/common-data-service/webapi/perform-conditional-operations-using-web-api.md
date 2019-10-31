---
title: Web API (Common Data Service) を使って条件付き操作を実行する| Microsoft Docs
description: Web API を使用して特定の操作を実行するかどうかおよびその方法を決定する、条件の作成方法について説明します。
ms.custom: ''
ms.date: 08/31/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: 771002b0-825a-462d-bbf0-1aeba4b726c8
caps.latest.revision: 16
author: brandonsimons
ms.author: jdaly
ms.reviewer: susikka
manager: annbe
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="perform-conditional-operations-using-the-web-api"></a>Web API を使用する条件付き演算を実行する

Common Data Service により、*ETags* として知られている標準 HTTP リソースのバージョン管理メカニズムに依存する条件付き演算のセットをサポートします。  
  
<a name="bkmk_ETags"></a>
  
## <a name="etags"></a>ETag

HTTP プロトコルは、リソースの特定のバージョンを識別するために、*エンティティ タグ*、または省略して [ETag](https://msdn.microsoft.com/library/dd541486.aspx) を定義します。 ETags は不透明の識別子であるため、その正確な値は実装に依存します。 ETag 値は 2 つの種類で表示されます: 厳密と緩い検証です。 厳密検証により、特定の URI によって識別されるユニークなリソースは、対応する ETag の値が変わらない場合は、バイナリ レベル上同一となることが示されています。 緩い検証は、同じ ETag の値におけるリソースの表示は、意味的に同等であることを保証するのみです。  
  
Common Data Service により、各エンティティ インスタンスに対して軽く検証する `@odata.etag` プロパティが生成され、このプロパティは取得した各エンティティ レコードに自動で返されます。 詳細については、「[Web API を使用してエンティティを取得する](retrieve-entity-using-web-api.md)」を参照してください。  
  
<a name="bkmk_ifMatchHeaders"></a>
 
## <a name="if-match-and-if-none-match-headers"></a>If-Match ヘッダーおよび If-None-Match ヘッダー

[If-Match](https://tools.ietf.org/html/rfc7232#section-3.1) と [If-None-Match](https://tools.ietf.org/html/rfc7232#section-3.2) ヘッダーを ETag の値と共に使用し、リソースの現在のバージョンが最後に取得したものと一致するか、以前のバージョンと一致するか、またはすべてのバージョンと一致しないかを確認します。  これらの比較を行うことによって、条件付きの操作サポートのベースが作られます。 Common Data Service は条件付き検索、オプティミスティック同時実行、および制限付き upsert 操作をサポートする ETags を提供します。
 
コレクション値ナビゲーション プロパティを展開するクエリは、最新の変更を反映しないそれらのプロパティのキャッシュされたデータを返す場合があります。 ブラウザのキャッシュを上書きするには、`If-None-Match` ヘッダーと値 `null` を使用することをお勧めします。 詳細については、「[HTTP ヘッダー](compose-http-requests-handle-errors.md#bkmk_headers)」を参照してください。 `If-None-Match` ヘッダーと特定の ETag 値を使用すると、変更されたデータのみが返されるようになります。
  
> [!WARNING]
> クライアント コードは ETag の特定値に、または平等または不平等以外の ETag 間の明確な関連付けに意味を持たせることはできません。 たとえば、リソースの新バージョンの ETag 値がそれ以前のバージョンの ETag 値を超えることは保証されません。 また、新しい ETag 値を生成するのに使用されるアルゴリズムはサービスのリリース通知なしに変更する場合があります。  
  
<a name="bkmk_DetectIfChanged"></a>

## <a name="conditional-retrievals"></a>条件付き検索

Etags により、同じレコードに複数回アクセスするときは、いつでもレコードの検索を最大限に活用することができます。 以前にレコードを取得している場合、最後に取得されてから変更している場合にのみ、取得されたデータを要求するために、`If-None-Match` ヘッダーを含む ETag 値を渡すことができます。 データが変更されている場合、要求は、要求の本体の最新データを含む 200 (OK) HTTP ステータスを返します。 データが変更されていない場合、エンティティが変更されていないことを示す HTTP ステータス コード 304 (Not Modified) が返されます。 次のサンプルのメッセージ ペアは、データが最後に取得されて以来変更されていない場合、`00000000-0000-0000-0000-000000000001` に等しい `accountid` を含む取引先企業エンティティのデータを返します。  

> [!NOTE]
> 条件付き検索は、オプティミスティック同時実行が有効になっているエンティティに対してのみ機能します。 次に示す Web API 要求を使用して、エンティティでオプティミスティック同時実行が有効になっているかどうかを確認します。 オプティミスティック同時実行が有効になっているエンティティでは、<xref href="Microsoft.Xrm.Sdk.Metadata.EntityMetadata.IsOptimisticConcurrencyEnabled?text=EntityMetadata.IsOptimisticConcurrencyEnabled" /> プロパティが `true` に設定されます。

> ```HTTP
> GET [Organization URI]/api/data/v9.0/EntityDefinitions(LogicalName='<Entity Logical Name>')?$select=IsOptimisticConcurrencyEnabled
> ```
<!-- TODO:
> For more information about optimistic concurrency, see [Reduce potential data loss using optimistic concurrency](../org-service/reduce-potential-data-loss-using-optimistic-concurrency.md).   -->

 **要求**  
```http  
GET [Organization URI]/api/data/v9.0/accounts(00000000-0000-0000-0000-000000000001)?$select=accountcategorycode,accountnumber,creditonhold,createdon,numberofemployees,name,revenue   HTTP/1.1  
Accept: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
If-None-Match: W/"468026"  
```  
  
 **応答**  
```json  
HTTP/1.1 304 Not Modified  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
```  
  
<a name="bkmk_limitUpsertOperations"></a>
  
## <a name="limit-upsert-operations"></a>upsert 操作の制限

upsert は、エンティティが存在しない場合にエンティティを作成することによって本来機能します。それ以外の場合は、既存のエンティティを更新します。 ただし、作成または更新のいずれかを阻止するために、ETags は upserts をさらに制限するのに使用できます。  
  
<a name="bkmk_preventCreateOnUpsert"></a>
 
### <a name="prevent-create-in-upsert"></a>upsert での作成の阻止

データを更新するとき、エンティティが意識して削除された可能性が見られる場合、そのエンティティの再作成を望まないでしょう。 これを阻止するには、`If-Match` ヘッダーを 「*」 の値を持つ要求に追加します。  
  
 **要求**  
```http  
PATCH [Organization URI]/api/data/v9.0/accounts(00000000-0000-0000-0000-000000000001) HTTP/1.1  
Content-Type: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
If-Match: *  
  
{  
    "name": "Updated Sample Account ",  
    "creditonhold": true,  
    "address1_latitude": 47.639583,  
    "description": "This is the updated description of the sample account",  
    "revenue": 6000000,  
    "accountcategorycode": 2  
}  
```  
  
 **応答**  
 エンティティが存在する場合、ステータス 204 (No Content) の通常応答を受け取ります。 エンティティが存在しない場合は、ステータス 404 (Not Found) の次の応答を受け取ります。  
  
```json  
HTTP/1.1 404 Not Found  
OData-Version: 4.0  
Content-Type: application/json; odata.metadata=minimal  
  
{  
 "error": {  
  "code": "",  
  "message": "account With Id = 00000000-0000-0000-0000-000000000001 Does Not Exist",  
  "innererror": {  
   "message": "account With Id = 00000000-0000-0000-0000-000000000001 Does Not Exist",  
   "type": "System.ServiceModel.FaultException`1[[Microsoft.Xrm.Sdk.OrganizationServiceFault, Microsoft.Xrm.Sdk, Version=8.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35]]",  
   "stacktrace": <stack trace removed for brevity>  
  }  
 }  
}  
```  
  
<a name="bkmk_preventUpdateInUpsert"></a>
  
### <a name="prevent-update-in-upsert"></a>upsert での更新の阻止

データを挿入する場合、同じ `id` 値を持つレコードがシステムにすでに存在している可能性があり、その更新を望まないでしょう。 これを阻止するには、`If-None-Match` ヘッダーを 「*」 の値を持つ要求に追加します。  
  
 **要求**  
```http  
PATCH [Organization URI]/api/data/v9.0/accounts(00000000-0000-0000-0000-000000000001) HTTP/1.1  
Content-Type: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
If-None-Match: *  
  
{  
    "name": "Updated Sample Account ",  
    "creditonhold": true,  
    "address1_latitude": 47.639583,  
    "description": "This is the updated description of the sample account",  
    "revenue": 6000000,  
    "accountcategorycode": 2  
}  
```  
  
 **応答**  
 エンティティが存在しない場合、ステータス 204 (No Content) の通常応答を受け取ります。 エンティティが存在する場合、ステータス 412 (Precondition Failed) の次の応答を受け取ります。  
  
```json  
HTTP/1.1 412 Precondition Failed  
OData-Version: 4.0  
Content-Type: application/json; odata.metadata=minimal  
  
{  
  "error":{  
   "code":"",  
   "message":"A record with matching key values already exists.",  
   "innererror":{  
    "message":"Cannot insert duplicate key.",  
    "type":"System.ServiceModel.FaultException`1[[Microsoft.Xrm.Sdk.OrganizationServiceFault, Microsoft.Xrm.Sdk, Version=8.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35]]",  
    "stacktrace":<stack trace removed for brevity>  
    }  
  }  
}  
```  
  
<a name="bkmk_Applyoptimisticconcurrency"></a>

## <a name="apply-optimistic-concurrency"></a>オプティミスティック同時実行の適用

最後に取得されてからエンティティが変更されているかどうかを検出するためにオプティミスティック同時実行を使用できます。 更新または削除するエンティティが、取得して以降サーバー上で変更された場合、更新または削除操作を完了させない方が望ましいでしょう。 ここに示すパターンを適用することによって、この状態の検出、エンティティの最新バージョンの取得、操作をやり直すかどうかを再評価するために必要な条件の適用を行うことができます。  
  
<a name="bkmk_Applyoptimisticconcurrencyondelete"></a>

### <a name="apply-optimistic-concurrency-on-delete"></a>削除でのオプティミスティック同時実行の適用

`00000000-0000-0000-0000-000000000001` の `accountid` を持つ取引先企業の以下の削除要求は、`If-Match` ヘッダーと共に送信される ETag 値が現在の値とは異なるので失敗します。 値が一致する場合、204 ステータス (No Content) が予想されます。  
  
 **要求**

```http  
DELETE [Organization URI]/api/data/v9.0/accounts(00000000-0000-0000-0000-000000000001) HTTP/1.1  
If-Match: W/"470867"  
Accept: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
```  
  
 **応答**

```json  
HTTP/1.1 412 Precondition Failed  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
  
{  
  "error":{  
    "code":"","message":"The version of the existing record doesn't match the RowVersion property provided.",  
    "innererror":{  
      "message":"The version of the existing record doesn't match the RowVersion property provided.",  
      "type":"System.ServiceModel.FaultException`1[[Microsoft.Xrm.Sdk.OrganizationServiceFault, Microsoft.Xrm.Sdk, Version=8.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35]]",  
"stacktrace":"  <stack trace details omitted for brevity>  
    }  
  }  
}  
```  
  
<a name="bkmk_Applyoptimisticconcurrencyonupdate"></a>

### <a name="apply-optimistic-concurrency-on-update"></a>更新でのオプティミスティック同時実行の適用

`00000000-0000-0000-0000-000000000001` の `accountid` を持つ取引先企業の以下の更新要求は、`If-Match` ヘッダーと共に送信される ETag 値が現在の値とは異なるので失敗します。 値が一致する場合、204 ステータス (No Content) が予想されます。  
  
 **要求**

```http  
PATCH [Organization URI]/api/data/v9.0/accounts(00000000-0000-0000-0000-000000000001) HTTP/1.1  
If-Match: W/"470867"  
Accept: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
  
{"name":"Updated Account Name"}  
```  
  
 **応答**

```json  
HTTP/1.1 412 Precondition Failed  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
  
{  
  "error":{  
    "code":"","message":"The version of the existing record doesn't match the RowVersion property provided.",  
    "innererror":{  
      "message":"The version of the existing record doesn't match the RowVersion property provided.",  
      "type":"System.ServiceModel.FaultException`1[[Microsoft.Xrm.Sdk.OrganizationServiceFault, Microsoft.Xrm.Sdk, Version=8.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35]]",  
"stacktrace":"  <stack trace details omitted for brevity>  
    }  
  }  
}  
```  
  
### <a name="see-also"></a>関連項目

[Web API 条件付き演算サンプル (C#)](samples/conditional-operations-csharp.md)<br />
[Web API 条件付き演算のサンプル (クライアント側の JavaScript)](samples/conditional-operations-client-side-javascript.md)<br />
[Web API を使用して演算を実行する](perform-operations-web-api.md)<br />
[HTTP 要求の作成とエラーの処理](compose-http-requests-handle-errors.md)<br />
[Web API を使用したクエリ データ](query-data-web-api.md)<br />
[Web API を使用してエンティティを作成する](create-entity-web-api.md)<br />
[Web API を使用してエンティティを取得する](retrieve-entity-using-web-api.md)<br />
[Web API を使用したエンティティの更新と削除](update-delete-entities-using-web-api.md)<br />
[Web API を使用したエンティティの関連付けと関連付け解除](associate-disassociate-entities-using-web-api.md)<br />
[Web API 関数の使用](use-web-api-functions.md)<br />
[Web API アクションの使用](use-web-api-actions.md)<br />
[Web API を使用してバッチ操作を実行する](execute-batch-operations-using-web-api.md)<br />
[Web API を使用して別のユーザーを偽装する](impersonate-another-user-web-api.md)
