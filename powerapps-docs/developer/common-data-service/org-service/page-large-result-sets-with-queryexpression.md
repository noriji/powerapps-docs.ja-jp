---
title: QueryExpression 使用して大量の結果セットをページングする (Common Data Service) | Microsoft Docs
description: ページング Cookie 機能を使用すると、アプリケーションの大きなデータセットのページングを高速化できます。 この機能は、FetchXML クエリと QueryExpression クエリの両方で使用できます。
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
# <a name="page-large-result-sets-with-queryexpression"></a>QueryExpression を使用して大きな結果セットをページングする

Common Data Service では、ページング Cookie 機能を使用して、アプリケーション内での大きなデータセットのページングを高速化できます。 この機能は、FetchXML クエリと <xref:Microsoft.Xrm.Sdk.Query.QueryExpression> クエリの両方で使用できます。 レコード セットのクエリにページング Cookie 機能を使用すると、クエリ結果にページング Cookie の値が含まれます。 システムのパフォーマンスを向上するには、次のレコード セットを取得するときにこの値を渡します。  
  
 <xref:Microsoft.Xrm.Sdk.Query.QueryExpression> と FetchXML では、ページング Cookie の形式が異なります。 <xref:Microsoft.Crm.Sdk.Messages.QueryExpressionToFetchXmlRequest> メッセージまたは<xref:Microsoft.Crm.Sdk.Messages.FetchXmlToQueryExpressionRequest> メッセージを使用して、クエリ形式を別の形式に変換すると、ページング Cookie の値は無視されます。 また、連続していないページを要求した場合も、ページング Cookie の値は無視されます。  
  
<a name="QueryExpression"></a>   
## <a name="using-a-paging-cookie-with-queryexpression"></a>QueryExpression でのページング Cookie の使用  
 次のサンプルは、ページング Cookie をクエリ式で使用する方法を示しています。 サンプル コード全体は、「[サンプル: ページング Cookie を使用した QueryExpression の使用](../org-service/samples/use-queryexpression-with-a-paging-cookie.md)」を参照してください。  
  
```csharp
// Query using the paging cookie.
// Define the paging attributes.
// The number of records per page to retrieve.
int queryCount = 3;

// Initialize the page number.
int pageNumber = 1;

// Initialize the number of records.
int recordCount = 0;

// Define the condition expression for retrieving records.
ConditionExpression pagecondition = new ConditionExpression();
pagecondition.AttributeName = "parentaccountid";
pagecondition.Operator = ConditionOperator.Equal;
pagecondition.Values.Add(_parentAccountId);

// Define the order expression to retrieve the records.
OrderExpression order = new OrderExpression();
order.AttributeName = "name";
order.OrderType = OrderType.Ascending;

// Create the query expression and add condition.
QueryExpression pagequery = new QueryExpression();
pagequery.EntityName = "account";
pagequery.Criteria.AddCondition(pagecondition);
pagequery.Orders.Add(order);
pagequery.ColumnSet.AddColumns("name", "emailaddress1");                   

// Assign the pageinfo properties to the query expression.
pagequery.PageInfo = new PagingInfo();
pagequery.PageInfo.Count = queryCount;
pagequery.PageInfo.PageNumber = pageNumber;

// The current paging cookie. When retrieving the first page, 
// pagingCookie should be null.
pagequery.PageInfo.PagingCookie = null;
Console.WriteLine("Retrieving sample account records in pages...\n");
Console.WriteLine("#\tAccount Name\t\tEmail Address"); 

while (true)
{
    // Retrieve the page.
    EntityCollection results = _serviceProxy.RetrieveMultiple(pagequery);
    if (results.Entities != null)
    {
        // Retrieve all records from the result set.
        foreach (Account acct in results.Entities)
        {
            Console.WriteLine("{0}.\t{1}\t{2}", ++recordCount, acct.Name,
                               acct.EMailAddress1);
        }
    }

    // Check for more records, if it returns true.
    if (results.MoreRecords)
    {
        Console.WriteLine("\n****************\nPage number {0}\n****************", pagequery.PageInfo.PageNumber);
        Console.WriteLine("#\tAccount Name\t\tEmail Address");

        // Increment the page number to retrieve the next page.
        pagequery.PageInfo.PageNumber++;
        
        // Set the paging cookie to the paging cookie returned from current results.
        pagequery.PageInfo.PagingCookie = results.PagingCookie;
    }
    else
    {
        // If no more records are in the result nodes, exit the loop.
        break;
    }
}
```

### <a name="see-also"></a>関連項目  
 [QueryExpression でクエリを作成する](build-queries-with-queryexpression.md)   
 [サンプル: ページング Cookie を使用した QueryExpression の使用](samples/use-queryexpression-with-a-paging-cookie.md)   
 [サンプル: 一対多関連付けでの取得](/dynamics365/customer-engagement/developer/retrieve-with-one-to-many-relationship)   
 [QueryExpression クラスの使用](use-queryexpression-class.md)   
 [FetchXML による大量の結果セットのページング](page-large-result-sets-with-fetchxml.md)