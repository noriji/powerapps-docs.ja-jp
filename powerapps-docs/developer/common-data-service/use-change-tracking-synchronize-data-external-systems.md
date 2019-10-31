---
title: 変更の追跡を使用してデータを外部システムに同期する (Common Data Service)| Microsoft Docs
description: 新しい変更追跡機能では、データが最初に抽出されてから、または最後に同期されてからどのデータが変更されたかを検出して、同期されるデータを効率の良い方法で維持する方法を提供します
ms.custom: ''
ms.date: 10/31/2018
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
# <a name="use-change-tracking-to-synchronize-data-with-external-systems"></a>変更の追跡を使用してデータを外部システムに同期

Common Data Service の新しい変更追跡機能は、データが最初に抽出されてから、または最後に同期されてからどのデータが変更されたかを検出することによって、データの同期を効率の良い方法で維持する方法を提供します。 以前は、この新しい機能がなかったので、Common Data Service のどのレコードが変更されたかを決定する、信頼性のある効率の良いメカニズムを構築することは困難でした。 このトピックでは、エンティティの変更を取得する方法について説明します。  
  
<a name="BKMK_enable"></a>   
## <a name="enable-change-tracking-for-an-entity"></a>エンティティに対する変更の追跡を有効化  

 エンティティの変更を検索するには、その前に、機能の変更がこのエンティティに対して有効になっていることを確認します。 この機能は、カスタマイズ ユーザー インターフェイス (UI) を使用することによって、またはプログラムで <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.ChangeTrackingEnabled> プロパティを `True` に設定することによって有効にすることができます。 コメント `Org.OData.Capabilities.V1.ChangeTracking` が、変更追跡機能が有効にされたエンティティ セットに追加されます。 エンティティ メタデータのコメントを表示するには、以下のことを行います 

 ```http 
 GET [Organization URI]/api/data/v9.0/$metadata?annotations=true
 ```
 メタデータのコメントの詳細については、「[メタデータの注釈](webapi/web-api-types-operations.md#bkmk_metannot)」を参照してください。
 
 カスタマイズ ユーザー インターフェイス (UI) の使用の詳細については、「[変更の追跡を有効にしてデータの同期を制御](https://technet.microsoft.com/library/3fa9c316-9dc9-4b28-9abf-43a3fce5b01d.aspx)」を参照してください。  
  
<a name="BKMK_webapi"></a>   
## <a name="retrieve-changes-for-an-entity-using-the-web-api"></a>Web API を使用してエンティティの変更を取得する  
エンティティの変更は、`odata.track-changes` を基本設定ヘッダーとして追加し、Web API リクエストを使用して追跡できます。 基本設定ヘッダー `odata.track-changes` は *差分リンク* が返され、続いてエンティティの変更の取得に使用されることを要求するために使用します。

差分リンクは、クライアントが結果に対する後続の変更を取得するために使用する、不透明なサービス生成リンクです。 それらは、変更が追跡されている結果のセットを記述する定義的なクエリに基づいています。たとえば、差分リンクを含む結果を生成した要求です。 差分リンクは、変更が追跡されているエンティティのコレクションと、変更を追跡するための開始点をエンコードします。 差分リンクに関する詳細については、「[OASIS OData バージョン 4.0 - 差分リンク](http://docs.oasis-open.org/odata/odata/v4.0/cs01/part1-protocol/odata-v4.0-cs01-part1-protocol.html#_Toc365046305)」を参照してください

<a name="BKMK_webapiexample"></a>   
## <a name="retrieve-changes-in-entities-using-web-api-example"></a>Web API 例を使用してエンティティの変更を取得します

この例では、Web API を使用して取引先企業データに加えられた変更を取得する方法を示しています。

要求
```http
GET [Organization URI]/org1/api/data/v9.0/accounts?$select=name,accountnumber,telephone1,fax HTTP/1.1
Prefer: odata.track-changes
Cache-Control: no-cache
OData-Version: 4.0
Content-Type: application/json
```
応答
```json
{
  "@odata.context":"[Organization URI]/api/data/v9.0/$metadata#accounts(name,accountnumber,telephone1,fax)",
"@odata.deltaLink": "[Organization URI]/api/data/v9.0/accounts?$select=name,accountnumber,telephone1,fax&$deltatoken=919042%2108%2f22%2f2017%2008%3a10%3a44",
"value":[
           {
              "@odata.etag":"W/\"915244\"",
              "name":"Monte Orton",
              "accountnumber":null,
              "telephone1":"555000",
              "fax":"10101",
              "accountid":"60c4e274-0d87-e711-80e5-00155db19e6d"
           }
       ]
}
```
上記の例から返された差分リンクは、エンティティの変更をフェッチするために使用できます。 この例では新しい取引先企業が作成され、既存の取引先企業が削除されました。 以下の例に示すように、以前の要求返された差分リンクはこれらの変更を取得します。

要求
```http
GET [Organization URI]/api/data/v9.0/accounts?$select=name,accountnumber,telephone1,fax&$deltatoken=919042%2108%2f22%2f2017%2008%3a10%3a44
```
応答
```json
{
          "@odata.context":"[Organization URI]/data/v9.0/$metadata#accounts(name,telephone1,fax)/$delta",
          "@odata.deltaLink":"[Organization URI]/api/data/v9.0/accounts?$select=name,telephone1,fax&$deltatoken=919058%2108%2f22%2f2017%2008%3a21%3a20",
"value":
    [
        {
            "@odata.etag":"W/\"915244\"",
            "name":"Monte Orton",
            "telephone1":"555000",
            "fax":"10101",
            "accountid":"60c4e274-0d87-e711-80e5-00155db19e6d"
        },
        {
            "@odata.context":"[Organization URI]/api/data/v9.0/$metadata#accounts/$deletedEntity",
            "id":"2e451703-c686-e711-80e5-00155db19e6d",
            "reason":"deleted"
        }
    ]
}
```
最初の変更追跡要求で返された差分リンクの応答には、別の差分リンクが含まれています。 この差分リンクは、エンティティにそれ以降に行われたすべての変更を取得するのに役立ちます。 最初の変更追跡要求が呼び出された後にエンティティの変更が発生しなかった場合は、空の JSON 応答が返されます。

<a name="bkmk_count"></a>
## <a name="retrieve-count-of-the-changes-made-in-entities-using-web-api"></a>Web API を使用してエンティティで行われた変更の数を取得します。
以下の例に示すように、最初の変更追跡要求から返された差分リンクに `$count` を追加して変更回数を取得できます。

要求
```http
GET [Organization URI]/api/data/v9.0/accounts/$count?$deltatoken=919042%2108%2f22%2f2017%2008%3a10%3a44
```

<a name="bkmk_unsupported"></a>
## <a name="query-options-not-supported-in-change-tracking-web-api-request"></a>変更追跡 Web API 要求でサポートされていないクエリ オプション
Web API 要求で `odata.track-changes` をヘッダーとして使用する場合は、システム クエリ オプション `$filter`、`$orderby` および `$top` はサポートされません。 「変更追跡が有効になっている場合は、`$filter`/ `$orderby`/ `$top` クエリ パラメーターはサポートされません。」という内容のエラー メッセージ Web API 要求でこれらのクエリ オプションを使用する場合に返されます。

<a name="BKMK_retrieve"></a>   
## <a name="retrieve-changes-for-an-entity-using-the-organization-service"></a>組織サービスを使用してエンティティの変更を取得する
 エンティティに対する変更の追跡を有効にすると、<xref:Microsoft.Xrm.Sdk.Messages.RetrieveEntityChangesRequest> メッセージを使用して、そのエンティティの変更を取得できます。 このメッセージは、最初に使用されるときは、エンティティのすべてのレコードを返し、そのデータは外部の記憶域に入力するために使用できます。 また、このメッセージは、次の <xref:Microsoft.Xrm.Sdk.Messages.RetrieveEntityChangesRequest> メッセージの使用で返されるバージョン番号を返します。これによって、このバージョン番号が返された以降に発生した変更に対するデータのみが返されます。  
  
 エンティティの変更の取得に際しては、以下の制限に注意ください。  
  
- 変更の取得では、1 つのエンティティのみが追跡されます。 バージョンまたはトークンなしで変更の取得が実行された場合、サーバーは、それをシステムの最小バージョンとして処理して、すべてのレコードを新規として返します。 削除済みのオブジェクトは返されません。  
  
- 最後のトークンが既定値の 90 日以内である場合、変更は返されます。 それが 90 日 を超えている場合は、すべてのレコードが返されます。  
  
- クライアントにエンティティに対する変更のセット、たとえば、バージョン 1 が存在し、次の変更のクエリの前にレコードが作成され、そのレコードが削除された場合、初めに削除されたアイテムがクライアントに存在しない場合でも、そのアイテムを取得します。  
  
- レコードは、サーバー側ロジックによって決定される順序で取得されます。 通常、エンド ユーザーは、常に、最初に新規のまたは更新されたすべてのレコード (バージョン番号で並べ替え) と、それに続く削除されたレコードを取得します。  3000 レコードが作成または更新され、2000 レコードが削除された場合は、Common Data Service は 5000 レコードのコレクションを返します。これは、最初の 3000 エントリが新規または更新されたレコードで構成され、後の 2000 エントリが削除されたレコードの分です。  
  
- 新規または更新された アイテムのコレクションが 5000 を超える場合、コレクションを複数ページで表示できます。  
  
<a name="BKMK_SampleCode"></a>   
## <a name="sample-code"></a>サンプル コード  
 次のコード スニペットは、`RetrieveEntityChangesRequest` メッセージを使用してエンティティの変更を取得する方法を示しています。 完全なサンプルについては、「[変更の追跡を使用して外部システムにデータを同期](http://go.microsoft.com/fwlink/p/?LinkId=533957)」を参照してください。  
  
```csharp
string token;

// Initialize page number.
int pageNumber = 1;
List<Entity> initialrecords = new List<Entity>();

// Retrieve records by using Change Tracking feature.
RetrieveEntityChangesRequest request = new RetrieveEntityChangesRequest();
request.EntityName = _customBooksEntityName.ToLower();
request.Columns = new ColumnSet("sample_bookcode", "sample_name", "sample_author");
request.PageInfo = new PagingInfo() { Count = 5000, PageNumber = 1, ReturnTotalRecordCount = false };


// Initial Synchronization. Retrieves all records as well as token value.
Console.WriteLine("Initial synchronization....retrieving all records.");
while (true)
{
    RetrieveEntityChangesResponse response = (RetrieveEntityChangesResponse)_serviceProxy.Execute(request);

    initialrecords.AddRange(response.EntityChanges.Changes.Select(x => (x as NewOrUpdatedItem).NewOrUpdatedEntity).ToArray());
    initialrecords.ForEach(x => Console.WriteLine("initial record id:{0}", x.Id));
    if (!response.EntityChanges.MoreRecords)
    {
        // Store token for later query
        token = response.EntityChanges.DataToken;
        break;

    }
    // Increment the page number to retrieve the next page.
    request.PageInfo.PageNumber++;
    // Set the paging cookie to the paging cookie returned from current results.
    request.PageInfo.PagingCookie = response.EntityChanges.PagingCookie;
}

```  
  
### <a name="see-also"></a>関連項目  
 [エンティティの代替キーの定義](define-alternate-keys-entity.md)   
 [代替キーの使用](use-alternate-key-create-record.md)   
 [Upsert を使用して Dynamics 365 を外部データで更新](use-upsert-insert-update-record.md)
