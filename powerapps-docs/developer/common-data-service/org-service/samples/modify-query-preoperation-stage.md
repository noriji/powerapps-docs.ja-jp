---
title: 'サンプル: PreOperation ステージのクエリを変更する (Common Data Service) | Microsoft Docs'
description: このサンプルは、RetrieveMultiple 要求の PreOperation ステージ内に定義したクエリを変更するプラグインの作成方法を示します。
ms.custom: ''
ms.date: 09/23/2019
ms.reviewer: ''
ms.service: powerapps
ms.topic: samples
author: JimDaly
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="sample-modify-query-in-preoperation-stage"></a>サンプル: PreOperation ステージのクエリを変更する

このサンプルは、`RetrieveMultiple` 要求の `PreOperation` ステージ内に定義したクエリを変更するプラグインの作成方法を示します。

プラグインのデータのフィルター処理は、`PostOperation` 段階に対して一般的に行われます。 <xref:Microsoft.Xrm.Sdk.EntityCollection.Entities> データは検査でき、返される必要がないエンティティはコレクションから削除されます。 ただしこのパターンは、ページ内に返されたレコード件数が目的のページ サイズと異なる可能性がある問題を示します。

このサンプルではさまざまな方法が説明されています。 取得後のフィルタ エンティティではなく、クエリに対する変更が実行される前に、`PreOperation` ステージのクエリへの変更が適用されます。 

このサンプルで示された主な点は、<xref:Microsoft.Xrm.Sdk.Messages.RetrieveMultipleRequest.Query>が<xref:Microsoft.Xrm.Sdk.Query.QueryBase> から派生した 3 つの異なる種類の 1 つです。 任意の種類のクエリを格納できるように、プラグイン コードは、クエリの種類を検出する必要があり、また、適切なフィルターの種類を実装する必要があります。

サンプルは [ここ](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/RetrieveMultipleAccountPreOperation) からダウンロードできます。

## <a name="how-to-run-this-sample"></a>このサンプルを実行する方法

1. [サンプル](https://github.com/Microsoft/PowerApps-Samples) リポジトリをダウンロードまたは複製して、ローカル コピーを用意します。 このサンプルは、PowerApps-Samples-master\cds\orgsvc\C#\RetrieveMultipleAccountPreOperation にあります。
1. Visual Studio でサンプル ソリューションを開き、プロジェクトのプロパティに移動して、ビルド中にアセンブリが署名されることを確認してください。 サンプルのアセンブリ (RetrieveMultipleAccountPreOperation.dll) をビルドするには F6 を押下します。
1. プラグイン登録ツールを実行して、 `Account` エンティティの `RetrieveMultiple` メッセージの `PreOperation` ステージについて、Common Data Service サーバーのサンドボックスとデータベースのアセンブリを登録します。 
1. アプリを使用するか、プラグインをトリガーするアカウントを取得するようにコードを作成します。 下記の [このサンプルをテストするコード](#code-to-test-this-sample) の例を参照してください。
1. テストを完了したらアセンブリとステップの登録を解除します。

## <a name="what-this-sample-does"></a>このサンプルの概要

実行した場合、プラグインでは、非アクティブな取引先企業レコードは、最も一般的なクエリの種類に対しては返されないことを確認してください。<xref:Microsoft.Xrm.Sdk.Query.QueryExpression> および <xref:Microsoft.Xrm.Sdk.Query.FetchExpression>。

<xref:Microsoft.Xrm.Sdk.Query.QueryByAttribute> は、使用可能なクエリのうちの 3 つ目の種類です。 複雑なクエリをサポートしないため、複雑なフィルターを使用する場合、この方法を適用できません。 幸い、このクエリは頻繁には使用されません。 この種類のクエリを `PreValidation`ステージで <xref:Microsoft.Xrm.Sdk.InvalidPluginExecutionException> をスローして拒否できます。

## <a name="how-this-sample-works"></a>このサンプルがどのように動作するか

[このサンプルの概要](#what-this-sample-does) で説明されているシナリオをシミュレートするために、サンプルは次のことを行います。

1. 入力パラメーターに `Query` と名前付けされたパラメーターが含まれていることを確認します。
1. 予期される 3 つの種類の一つとしてキャストを試行してクエリの種類をテストします。
1. クエリの種類に応じて、クエリは次の方法で変更されます。

### <a name="fetchexpression"></a>FetchExpression

1. FetchXml を含む <xref:Microsoft.Xrm.Sdk.Query.FetchExpression.Query> 値を<xref:System.Xml.Linq.XDocument> に含めて解析します。
1. `entity` 要素 `attribute` 属性が `account` エンティティを指定することを確認します。
1. `statecode` 属性をテストする条件のクエリで `filter` 要素をすべてテストします。
1. その属性に基づく既存の条件を削除します。
1. 新しい `filter` を、1 (非アクティブ) に等しくない `statecode` の取引先企業のみが返されることを要求するクエリに追加します。
1. 変更済みのクエリを、<xref:Microsoft.Xrm.Sdk.Query.FetchExpression.Query> 値に設定します。

```csharp
if (fetchExpressionQuery != null)
{
    tracingService.Trace("Found FetchExpression Query");

    XDocument fetchXmlDoc = XDocument.Parse(fetchExpressionQuery.Query);
    //The required entity element
    var entityElement = fetchXmlDoc.Descendants("entity").FirstOrDefault();
    var entityName = entityElement.Attributes("name").FirstOrDefault().Value;

    //Only applying to the account entity
    if (entityName == "account")
    {
        tracingService.Trace("Query on Account confirmed");

        //Get all filter elements
        var filterElements = entityElement.Descendants("filter");

        //Find any existing statecode conditions
        var stateCodeConditions = from c in filterElements.Descendants("condition")
                                    where c.Attribute("attribute").Value.Equals("statecode")
                                    select c;

        if (stateCodeConditions.Count() > 0)
        {
            tracingService.Trace("Removing existing statecode filter conditions.");
        }
        //Remove statecode conditions
        stateCodeConditions.ToList().ForEach(x => x.Remove());


        //Add the condition you want in a new filter
        entityElement.Add(
            new XElement("filter",
                new XElement("condition",
                    new XAttribute("attribute", "statecode"),
                    new XAttribute("operator", "neq"), //not equal
                    new XAttribute("value", "1") //Inactive
                    )
                )
            );
    }


    fetchExpressionQuery.Query = fetchXmlDoc.ToString();

}
```

### <a name="queryexpression"></a>QueryExpression

1. <xref:Microsoft.Xrm.Sdk.Query.QueryExpression.EntityName> が `account` エンティティであることを確認します。
1. <xref:Microsoft.Xrm.Sdk.Query.QueryExpression.Criteria>を使用してループします。<xref:Microsoft.Xrm.Sdk.Query.FilterExpression.Filters> 収集
1. `RemoveAttributeConditions` の方法を繰り返して使用し、statecode 属性をテストしたり削除したりする　<xref:Microsoft.Xrm.Sdk.Query.ConditionExpression> インスタンスを検索します。
1. 新しい <xref:Microsoft.Xrm.Sdk.Query.FilterExpression> を　 <xref:Microsoft.Xrm.Sdk.Query.QueryExpression.Criteria>に追加します。<xref:Microsoft.Xrm.Sdk.Query.FilterExpression.Filters> 1 (非アクティブ) に等しくない `statecode` の取引先企業のみが返されることを要求するコレクション。

```csharp
if (queryExpressionQuery != null)
{
    tracingService.Trace("Found Query Expression Query");
    if (queryExpressionQuery.EntityName.Equals("account"))
    {
        tracingService.Trace("Query on Account confirmed");

        //Recursively remove any conditions referring to the statecode attribute
        foreach (FilterExpression fe in queryExpressionQuery.Criteria.Filters)
        {
            //Remove any existing criteria based on statecode attribute
            RemoveAttributeConditions(fe, "statecode", tracingService);
        }

        //Define the filter
        var stateCodeFilter = new FilterExpression();
        stateCodeFilter.AddCondition("statecode", ConditionOperator.NotEqual, 1);
        //Add it to the Criteria
        queryExpressionQuery.Criteria.AddFilter(stateCodeFilter);
    }

}
```

#### <a name="removeattributeconditions-method"></a>RemoveAttributeConditions メソッド

特定の名前付き属性に対する任意の条件を削除する再帰的方法

```csharp
/// <summary>
/// Removes any conditions using a specific named attribute
/// </summary>
/// <param name="filter">The filter that may have a condition using the attribute</param>
/// <param name="attributeName">The name of the attribute that should not be used in a condition</param>
/// <param name="tracingService">The tracing service to use</param>
private void RemoveAttributeConditions(FilterExpression filter, string attributeName, ITracingService tracingService)
{

    List<ConditionExpression> conditionsToRemove = new List<ConditionExpression>();

    foreach (ConditionExpression ce in filter.Conditions)
    {
        if (ce.AttributeName.Equals(attributeName))
        {
            conditionsToRemove.Add(ce);
        }
    }

    conditionsToRemove.ForEach(x =>
    {
        filter.Conditions.Remove(x);
        tracingService.Trace("Removed existing statecode filter conditions.");
    });

    foreach (FilterExpression fe in filter.Filters)
    {
        RemoveAttributeConditions(fe, attributeName, tracingService);
    }
}
```

### <a name="querybyattribute"></a>QueryByAttribute

<xref:Microsoft.Xrm.Sdk.Query.QueryByAttribute> では複雑なフィルターがサポートされていないため、プラグイン トレース ログに対するメッセージのみを作成してください。 

このクエリの種類を完全に使用しない場合、操作を防ぐため、<xref:Microsoft.Xrm.Sdk.InvalidPluginExecutionException>をスローできますが、`PreValidation` 段階で適用することが望ましいとされます。

```csharp
if (queryByAttributeQuery != null)
{
    tracingService.Trace("Found Query By Attribute Query");
    //Query by attribute doesn't provide a complex query model that 
    // can be manipulated
}
```

## <a name="code-to-test-this-sample"></a>このサンプルをテストするコード

次のコードは、プラグインをトリガーする同じクエリを実行する 5 つの異なる方法を示します。 

特定の条件を指定すると、この場合は `address1_city` 属性値、これは唯一のアクティブなレコードのみが一致する属性値ですが、これらのクエリがそのレコードだけを返します。

次に、そのレコードを非アクティブ化、再度このコードを実行します。 レコードが返されません。

```csharp
try
{
    string account_city_value = "ValueForTesting";

    //QueryByAttribute
    var queryByAttribute = new QueryByAttribute("account")
    {
        TopCount = 1,
        ColumnSet = new ColumnSet("accountid", "name")
    };
    queryByAttribute.AddAttributeValue("address1_city", account_city_value);
    queryByAttribute.AddOrder("name", OrderType.Descending);

    //QueryExpression
    var queryExpression = new QueryExpression("account")
    { ColumnSet = new ColumnSet("accountid", "name"), TopCount = 1 };
    queryExpression.Orders.Add(new OrderExpression("name", OrderType.Descending));
    var qeFilter = new FilterExpression(LogicalOperator.And);
    qeFilter.AddCondition(new ConditionExpression("address1_city", ConditionOperator.Equal, account_city_value));
    queryExpression.Criteria = qeFilter;

    //Fetch
    var fetchXml = $@"<fetch mapping='logical' count='1'>
                <entity name='account'>  
                    <attribute name='accountid'/>
                    <attribute name='name'/>
                    <order attribute='name' descending='true' />
                    <filter>
                    <condition attribute='address1_city' operator='eq' value='{account_city_value}' />
                    </filter>
                </entity>  
            </fetch>";

    var fetchExpression = new FetchExpression(fetchXml);

    //Get results:
    var queryByAttributeResults = service.RetrieveMultiple(queryByAttribute);
    var queryExpressionResults = service.RetrieveMultiple(queryExpression);
    var fetchExpressionResults = service.RetrieveMultiple(fetchExpression);

    //WebAPI
    string WebAPIAccountName = string.Empty;

    Dictionary<string, List<string>> ODataHeaders = new Dictionary<string, List<string>>() {
    {"Accept", new List<string>(){"application/json" } },
    {"OData-MaxVersion", new List<string>(){ "4.0" } },
    {"OData-Version", new List<string>(){ "4.0" } }};


    HttpResponseMessage response = service.ExecuteCrmWebRequest(HttpMethod.Get,
        $"accounts?$select=accountid,name&$top=1&$orderby=name desc&$filter=address1_city eq '{account_city_value}'",
        string.Empty,
        ODataHeaders);
    if (response.IsSuccessStatusCode)
    {
        var results = response.Content.ReadAsStringAsync().Result;
        var jsonResults = JObject.Parse(results);
        var accounts = (JArray)jsonResults.GetValue("value");
        if (accounts.Count > 0)
        {
            var account = accounts.First();
            WebAPIAccountName = account.Value<string>("name");
        }

    }

    else
    {
        Console.WriteLine(response.ReasonPhrase);
    }

    //Using Fetch with Web API
    string FetchWebAPIAccountName = string.Empty;
    HttpResponseMessage fetchResponse = service.ExecuteCrmWebRequest(HttpMethod.Get,
    $"accounts?fetchXml=" + Uri.EscapeDataString(fetchXml),
    string.Empty,
    ODataHeaders);
    if (fetchResponse.IsSuccessStatusCode)
    {

        var results = fetchResponse.Content.ReadAsStringAsync().Result;
        var jsonResults = JObject.Parse(results);
        var accounts = (JArray)jsonResults.GetValue("value");
        if (accounts.Count > 0)
        {
            var account = accounts.First();
            FetchWebAPIAccountName = account.Value<string>("name");
        }
    }

    else
    {
        Console.WriteLine(fetchResponse.ReasonPhrase);
    }

    string no_records_message = "No records returned";

    Console.WriteLine("QueryByAttribute Account Returned: {0}", queryByAttributeResults.Entities.Count > 0 ?
        queryByAttributeResults.Entities[0]["name"] : no_records_message);
    Console.WriteLine("QueryExpression Account Returned: {0}", queryExpressionResults.Entities.Count > 0 ?
        queryExpressionResults.Entities[0]["name"] : no_records_message);
    Console.WriteLine("Fetch Account Returned: {0}", fetchExpressionResults.Entities.Count > 0 ?
        fetchExpressionResults.Entities[0]["name"] : no_records_message);
    Console.WriteLine("WebAPI Account Returned: {0}", WebAPIAccountName != string.Empty ?
        WebAPIAccountName : no_records_message);
    Console.WriteLine("WebAPI Fetch Account Returned: {0}", FetchWebAPIAccountName != string.Empty ?
        FetchWebAPIAccountName : no_records_message);

}
catch (Exception ex)
{

    throw ex;
}
```

### <a name="see-also"></a>関連項目

[結果を PreOperation RetrieveMultiple を使用してフィルター処理したときに、すべての種類のクエリを実行する](../../best-practices/business-logic/implement-all-types-of-queries-when-filtering-preoperation-retrievemultiple.md)