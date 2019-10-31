---
title: QueryExpression クラスの使用 (Common Data Service) | Microsoft Docs
description: QueryExpression クラスを使用して、IOrganizationService.QueryBase) メソッドまたは RetrieveMultipleRequest メッセージで使用する複雑なクエリを作成します。
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
# <a name="use-the-queryexpression-class"></a>QueryExpression クラスの使用

Common Data Service では、<xref:Microsoft.Xrm.Sdk.Query.QueryExpression> クラスを使用して、<xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.RetrieveMultiple*> メソッドまたは <xref:Microsoft.Xrm.Sdk.Messages.RetrieveMultipleRequest> メッセージによってクエリの結果セットを絞り込むことができます。 <xref:Microsoft.Xrm.Sdk.Query.QueryExpression> に対するクエリ パラメーターは、<xref:Microsoft.Xrm.Sdk.Query.ConditionExpression>、<xref:Microsoft.Xrm.Sdk.Query.ColumnSet>、および <xref:Microsoft.Xrm.Sdk.Query.FilterExpression> の各クラスを使用して設定できます。  
  
 <xref:Microsoft.Xrm.Sdk.Query.QueryExpression> クラスを使用すると、複雑なクエリを作成できます。 <xref:Microsoft.Xrm.Sdk.Query.QueryByAttribute> クラスは、指定した値と属性が一致するエンティティを簡単に検索できるように設計されています。  
  
 次の表に、クエリ式を作成する際に設定するプロパティを一覧表示します。  
  
|プロパティ|説明|  
|--------------|-----------------|  
|<xref:Microsoft.Xrm.Sdk.Query.QueryExpression.EntityName>|取得するエンティティの種類を指定します。 クエリ式では、1 種類のエンティティのコレクションのみ取得できます。|  
|<xref:Microsoft.Xrm.Sdk.Query.QueryExpression.ColumnSet>|取得する一連の属性 (列) を指定します。|  
|<xref:Microsoft.Xrm.Sdk.Query.QueryExpression.Criteria>|クエリの結果をフィルターする複雑な条件式および論理フィルター式を指定します。|  
|<xref:Microsoft.Xrm.Sdk.Query.QueryExpression.Distinct>|クエリの結果に重複するレコードを含めるかどうかを指定します。|  
|<xref:Microsoft.Xrm.Sdk.Query.QueryExpression.LinkEntities>|複数のエンティティ種類間のリンクを指定します。|  
|<xref:Microsoft.Xrm.Sdk.Query.QueryExpression.Orders>|クエリでレコードを返す順序を指定します。|  
|<xref:Microsoft.Xrm.Sdk.Query.QueryExpression.PageInfo>|クエリで返されるページ数、およびページごとのレコード数を指定します。|  
  
<a name="record_count"></a>   
## <a name="record-count"></a>レコードのカウント  
 クエリで返るレコードの数を調べるには、クエリを実行する前に <xref:Microsoft.Xrm.Sdk.Query.PagingInfo.ReturnTotalRecordCount> プロパティを true に設定します。 これを行うと、<xref:Microsoft.Xrm.Sdk.EntityCollection.TotalRecordCount> が設定されます。 それ以外の場合、この値は -1 になります。  
  
## <a name="example"></a>例  
 次のサンプルは、<xref:Microsoft.Xrm.Sdk.Query.QueryExpression> クラスの使用方法を示します。  
  
```csharp  
//  Query using ConditionExpression and FilterExpression  
ConditionExpression condition1 = new ConditionExpression();  
condition1.AttributeName = "lastname";  
condition1.Operator = ConditionOperator.Equal;  
condition1.Values.Add("Brown");              
  
FilterExpression filter1 = new FilterExpression();  
filter1.Conditions.Add(condition1);  
  
QueryExpression query = new QueryExpression("contact");  
query.ColumnSet.AddColumns("firstname", "lastname");  
query.Criteria.AddFilter(filter1);  
  
EntityCollection result1 = _serviceProxy.RetrieveMultiple(query);  
Console.WriteLine();Console.WriteLine("Query using Query Expression with ConditionExpression and FilterExpression");  
Console.WriteLine("---------------------------------------");  
foreach (var a in result1.Entities)  
{  
    Console.WriteLine("Name: " + a.Attributes["firstname"] + " " + a.Attributes["lastname"]);  
}  
Console.WriteLine("---------------------------------------");  
```  
  
### <a name="see-also"></a>関連項目  
 [QueryExpression でクエリを作成する](build-queries-with-queryexpression.md)   
 [ColumnSet クラスの使用](use-the-columnset-class.md)   
 [ConditionExpression クラスの使用](use-conditionexpression-class.md)   
 [FilterExpression クラスの使用](use-filterexpression-class.md)   
 <xref:Microsoft.Xrm.Sdk.Query.QueryExpression>