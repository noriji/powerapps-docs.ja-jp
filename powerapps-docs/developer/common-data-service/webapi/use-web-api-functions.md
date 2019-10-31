---
title: Web API 関数を使用する (Common Data Service)| Microsoft Docs
description: 関数は Common Data Service からデータを取得する GET 要求で使用される再利用可能な操作です
ms.custom: ''
ms.date: 09/05/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: c6de9c12-e8e3-4ed5-a6ed-18ade572065f
caps.latest.revision: 45
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
# <a name="use-web-api-functions"></a>Web API 関数の使用

関数とアクションは、Web API を使って実行できる再利用可能な操作を表します。 Web API の関数は 2 種類あります。  
  
**関数**  
`GET` 要求と「<xref:Microsoft.Dynamics.CRM.FunctionIndex>」に示されている関数を使用して、副作用がない操作を実行します。 一般に、これらの関数は、データを取得します。 コレクションまたは複合型のいずれかを返します。 これらの各関数には、組織サービスに対応するメッセージがあります。  
  
**クエリ関数**  
「<xref:Microsoft.Dynamics.CRM.QueryFunctionIndex>」に記載されている関数を使用して、クエリの作成の際にプロパティと値を評価します。 これらの各関数には、対応する <xref:Microsoft.Xrm.Sdk.Query.ConditionOperator> の値があります。  
  
<a name="bkmk_passParametersToFunctions"></a>

## <a name="passing-parameters-to-a-function"></a>関数にパラメーターを渡す
  
パラメーターを必要とする関数の場合、パラメーターを使用して値を渡すことをお勧めします。 たとえば、<xref href="Microsoft.Dynamics.CRM.GetTimeZoneCodeByLocalizedName?text=GetTimeZoneCodeByLocalizedName Function" /> を使用する場合、`LocalizedStandardName` および `LocaleId` パラメーターの値を含める必要があります。 次に示すようなインライン構文を使用できます。  
  
```http
GET [Organization URI]/api/data/v9.0/GetTimeZoneCodeByLocalizedName(LocalizedStandardName='Pacific Standard Time',LocaleId=1033)  
```  
  
ただし、インライン構文での DateTimeOffset 値の使用については、「[DateTimeOffset as query parameter (クエリ パラメーターとしての DateTimeOffset) #204](https://github.com/OData/WebApi/issues/204)」の記事で説明されているように未解決の問題があります。  
  
したがって、次のコード例に示すように、パラメーターとして値を渡すことお勧めします。 このベスト プラクティスを使用すると、`DateTimeOffset` に適用される未解決の懸案事項を回避できます。  
  
```http
GET [Organization URI]/api/data/v9.0/GetTimeZoneCodeByLocalizedName(LocalizedStandardName=@p1,LocaleId=@p2)?@p1='Pacific Standard Time'&@p2=1033  
```  
  
また、パラメーター値が複数回使用される場合、URL の合計の長さを短くするために、パラメーター エイリアスを使用してパラメーターの値を再利用できます。  
  
<a name="bkmk_passCrmEntityReference"></a>

## <a name="pass-reference-to-an-entity-to-a-function"></a>エンティティに対する参照を関数に渡す

特定の関数は既存のエンティティに対する参照を渡す必要があります。 たとえば、次の関数には <xref href="Microsoft.Dynamics.CRM.crmbaseentity?text=crmbaseentity EntityType" /> を必要とするパラメーターがあります。  
  
||||  
|-|-|-|  
|<xref href="Microsoft.Dynamics.CRM.CalculateRollupField?text=CalculateRollupField Function" />|<xref href="Microsoft.Dynamics.CRM.IncrementKnowledgeArticleViewCount?text=IncrementKnowledgeArticleViewCount Function" />|<xref href="Microsoft.Dynamics.CRM.InitializeFrom?text=InitializeFrom Function" />|  
|<xref href="Microsoft.Dynamics.CRM.IsValidStateTransition?text=IsValidStateTransition Function" />|<xref href="Microsoft.Dynamics.CRM.RetrieveDuplicates?text=RetrieveDuplicates Function" />|<xref href="Microsoft.Dynamics.CRM.RetrieveLocLabels?text=RetrieveLocLabels Function" />|  
|<xref href="Microsoft.Dynamics.CRM.RetrievePrincipalAccess?text=RetrievePrincipalAccess Function" />|<xref href="Microsoft.Dynamics.CRM.RetrieveRecordWall?text=RetrieveRecordWall Function" />|<xref href="Microsoft.Dynamics.CRM.ValidateRecurrenceRule?text=ValidateRecurrenceRule Function" />|  
  
既存のエンティティに対して参照を渡す場合、エンティティの `@odata.id` コメントを URI に使用します。 たとえば、<xref href="Microsoft.Dynamics.CRM.RetrievePrincipalAccess?text=RetrievePrincipalAccess Function" /> を使用している場合、次の URI を使用して特定の取引先担当者に対するアクセス権の取得を指定できます。  
  
```http
GET [Organization URI]/api/data/v9.0/systemusers(af9b3cf6-f654-4cd9-97a6-cf9526662797)/Microsoft.Dynamics.CRM.RetrievePrincipalAccess(Target=@tid)?@tid={'@odata.id':'contacts(9f3162f6-804a-e611-80d1-00155d4333fa)'}
```  
  
`@odata.id` コメントは完全な URI を指定できますが、相対 URI も指定できます。  
  
<a name="bkmk_boundAndUnboundFunctions"></a>
 
## <a name="bound-and-unbound-functions"></a>バインドされた関数とバインドされていない関数

「<xref:Microsoft.Dynamics.CRM.FunctionIndex>」に記載されている関数のみをバインドすることができます。 クエリ関数はバインドされることはありません。  
  
<a name="bkmk_boundFunctions"></a>

### <a name="bound-functions"></a>バインドされた関数

[CSDL メタデータ ドキュメント](web-api-types-operations.md#bkmk_csdl) では、`Function` 要素がバインドされた関数を表す場合、その要素には、`true` の値を持つ `IsBound` 属性が指定されています。 関数内に定義された最初の `Parameter` 要素は、関数がバインドされているエンティティを表します。 パラメーターの `Type` 属性がコレクションである場合、関数はエンティティのコレクションにバインドされています。 例として、CSDL での <xref href="Microsoft.Dynamics.CRM.CalculateTotalTimeIncident?text=CalculateTotalTimeIncident Function" /> と <xref href="Microsoft.Dynamics.CRM.CalculateTotalTimeIncidentResponse?text=CalculateTotalTimeIncidentResponse ComplexType" /> の定義を次に示します。  
  
```xml
<ComplexType Name="CalculateTotalTimeIncidentResponse">  
  <Property Name="TotalTime" Type="Edm.Int64" Nullable="false" />  
</ComplexType>  
<Function Name="CalculateTotalTimeIncident" IsBound="true">  
  <Parameter Name="entity" Type="mscrm.incident" Nullable="false" />  
  <ReturnType Type="mscrm.CalculateTotalTimeIncidentResponse" Nullable="false" />  
</Function>  
```  
  
このバインドされた関数は、組織サービスで使用される <xref:Microsoft.Crm.Sdk.Messages.CalculateTotalTimeIncidentRequest> と同等です。 Web API でこの関数は <xref:Microsoft.Crm.Sdk.Messages.CalculateTotalTimeIncidentRequest>.<xref:Microsoft.Crm.Sdk.Messages.CalculateTotalTimeIncidentRequest.IncidentId> プロパティを表す <xref href="Microsoft.Dynamics.CRM.incident?text=incident EntityType" />  にバインドされます。 この関数は、<xref:Microsoft.Crm.Sdk.Messages.CalculateTotalTimeIncidentResponse> を返すのではなく、<xref href="Microsoft.Dynamics.CRM.CalculateTotalTimeIncidentResponse?text=CalculateTotalTimeIncidentResponse ComplexType" /> を返します。 関数が複合型を返す場合、複合型の定義は、CSDL で関数の定義のすぐ上に表示されます。  
  
バインドされた関数を呼び出すには、関数の完全な名前を URL に追加し、関数名に続くかっこ内に名前付きパラメーターを含めます。 関数の完全名には、名前空間 `Microsoft.Dynamics.CRM` が含まれています。 バインドされていない関数には、完全な名前を使用しないでください。  
  
> [!IMPORTANT]
>  バインドされた関数は、最初のパラメーター値を設定するために URI を使って呼び出す必要があります。 名前付きパラメーターの値として設定することはできません。  
  
次の例は、`incident` エンティティにバインドされた <xref href="Microsoft.Dynamics.CRM.CalculateTotalTimeIncident?text=CalculateTotalTimeIncident Function" /> の使用例を示しています。  
  
 **要求**

```http
GET [Organization URI]/api/data/v9.0/incidents(90427858-7a77-e511-80d4-00155d2a68d1)/Microsoft.Dynamics.CRM.CalculateTotalTimeIncident() HTTP/1.1  
Accept: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
```  
  
 **応答**
 
```http 
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
  
{  
  "@odata.context":"[Organization URI]/api/data/v9.0/$metadata#Microsoft.Dynamics.CRM.CalculateTotalTimeIncidentResponse","TotalTime":30  
}  
```  
  
<a name="bkmk_unboundFunctions"></a>
 
### <a name="unbound-functions"></a>バインドされていない関数

<xref href="Microsoft.Dynamics.CRM.WhoAmI?text=WhoAmI Function" />はエンティティにバインドされていません。 CSDL で `IsBound` 属性を使用せずに定義されます。  
  
```xml
<ComplexType Name="WhoAmIResponse">  
  <Property Name="BusinessUnitId" Type="Edm.Guid" Nullable="false" />  
  <Property Name="UserId" Type="Edm.Guid" Nullable="false" />  
  <Property Name="OrganizationId" Type="Edm.Guid" Nullable="false" />  
</ComplexType>  
<Function Name="WhoAmI">  
  <ReturnType Type="mscrm.WhoAmIResponse" Nullable="false" />  
</Function>  
```  
  
この関数は <xref:Microsoft.Crm.Sdk.Messages.WhoAmIRequest> に対応し、<xref href="Microsoft.Dynamics.CRM.WhoAmIResponse?text=WhoAmIResponse ComplexType" /> (組織サービスで使用される <xref:Microsoft.Crm.Sdk.Messages.WhoAmIResponse> に対応する) を返します。 この関数にパラメーターはありません。  
  
バインドされていない関数を呼び出すときは、次の例のように関数名だけを使用します。  
  
 **要求**

```http
GET [Organization URI]/api/data/v9.0/WhoAmI() HTTP/1.1  
Accept: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
```  
  
 **応答**

```http
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
{  
 "@odata.context": "[Organization URI]/api/data/v9.0/$metadata#Microsoft.Dynamics.CRM.WhoAmIResponse",  
 "BusinessUnitId": "ded5a64f-f06d-e511-80d0-00155db07cb1",  
 "UserId": "d96e9f55-f06d-e511-80d0-00155db07cb1",  
 "OrganizationId": "4faf1f34-f06d-e511-80d0-00155db07cb1"  
}  
```  
  
<a name="bkmk_composeQueryWithFunctions"></a>

## <a name="compose-a-query-with-functions"></a>関数を使用してクエリを作成する

クエリが返すデータを制御するために関数で使用できる 2 つの方法があります。 特定の関数では、関数から返される列や条件をコントロールでき、クエリ関数を使用してクエリ内の条件を評価することができます。  
  
<a name="bkmk_composableFunctions"></a>
  
### <a name="composable-functions"></a>構成可能な関数

<xref:Microsoft.Dynamics.CRM.FunctionIndex> でリストされた一部の機能は、エンティティのコレクションを返します。 これらの関数のサブセットは、*構成可能*です。つまり、追加の `$select` または `$filter` システム クエリ オプションを含めることで、どの列が結果で返されるかをコントロールできます。 これらの関数には、CSDL の `IsComposable` 属性があります。 これらの各関数には、<xref:Microsoft.Xrm.Sdk.Query.ColumnSet> または <xref:Microsoft.Xrm.Sdk.Query.QueryBase> のいずれかの型パラメーターを受け取る、組織サービスに対応するメッセージがあります。 OData システム クエリ オプションが同じ機能を提供します。そのため、これらの関数には、組織サービスの対応するメッセージと同じパラメーターはありません。 次の表は、このリリースの構成可能な関数の一覧を示します。  
  
||||  
|-|-|-|  
|<xref href="Microsoft.Dynamics.CRM.GetDefaultPriceLevel?text=GetDefaultPriceLevel Function" />|<xref href="Microsoft.Dynamics.CRM.RetrieveAllChildUsersSystemUser?text=RetrieveAllChildUsersSystemUser Function" />|<xref href="Microsoft.Dynamics.CRM.RetrieveBusinessHierarchyBusinessUnit?text=RetrieveBusinessHierarchyBusinessUnit Function" />|  
|<xref href="Microsoft.Dynamics.CRM.RetrieveByGroupResource?text=RetrieveByGroupResource Function" />|<xref href="Microsoft.Dynamics.CRM.RetrieveByResourceResourceGroup?text=RetrieveByResourceResourceGroup Function" />|<xref href="Microsoft.Dynamics.CRM.RetrieveMembersBulkOperation?text=RetrieveMembersBulkOperation Function" />|  
|<xref href="Microsoft.Dynamics.CRM.RetrieveParentGroupsResourceGroup?text=RetrieveParentGroupsResourceGroup Function" />|<xref href="Microsoft.Dynamics.CRM.RetrieveSubGroupsResourceGroup?text=RetrieveSubGroupsResourceGroup Function" />|<xref href="Microsoft.Dynamics.CRM.RetrieveUnpublishedMultiple?text=RetrieveUnpublishedMultiple Function" />|  
|<xref href="Microsoft.Dynamics.CRM.SearchByBodyKbArticle?text=SearchByBodyKbArticle Function" />|<xref href="Microsoft.Dynamics.CRM.SearchByKeywordsKbArticle?text=SearchByKeywordsKbArticle Function" />|<xref href="Microsoft.Dynamics.CRM.SearchByTitleKbArticle?text=SearchByTitleKbArticle Function" />|  
  
<a name="bkmk_queryevaluationFunctions"></a>
  
### <a name="query-functions"></a>クエリ関数

「<xref:Microsoft.Dynamics.CRM.QueryFunctionIndex>」に記載されている関数は、クエリを作成するために使用することを目的にしています。 これらの関数は、[組込みクエリ関数](query-data-web-api.md#bkmk_buildInQueryFunctions)と同様の方法で使用できますが、いくつかの重要な違いがあります。  
  
関数の完全な名前を使用し、パラメーターの名前を含める必要があります。 次の例は、<xref href="Microsoft.Dynamics.CRM.LastXHours?text=LastXHours Function" />を使用して、過去 12 か月間に変更されたすべての取引先企業エンティティを返す方法を示しています。  
  
```http
GET [Organization URI]/api/data/v9.0/accounts?$select=name,accountnumber&$filter=Microsoft.Dynamics.CRM.LastXHours(PropertyName=@p1,PropertyValue=@p2)&@p1='modifiedon'&@p2=12  
```  

#### <a name="limitations-of-query-functions"></a>クエリ関数の制限

クエリ関数の制限の 1 つは、`not` 演算子を使ってクエリ関数を否定できない点です。

たとえば、<xref href="Microsoft.Dynamics.CRM.EqualUserId?text=EqualUserId Function" /> を使用した次のクエリはエラー `Not operator along with the Custom Named Condition operators is not allowed` で失敗します。

```http
GET [Organization URI]/api/data/v9.1/systemusers?$select=fullname,systemuserid&$filter=not Microsoft.Dynamics.CRM.EqualUserId(PropertyName=@p1)&@p1='systemuserid'
```
いくつかのクエリ関数には、コンパニオンにによって拒否されたクエリ関数があります。 たとえば、<xref href="Microsoft.Dynamics.CRM.NotEqualUserId?text=NotEqualUserId Function" /> を使用できます。 次のクエリは、正しい結果を返します。

```http
GET [Organization URI]/api/data/v9.1/systemusers?$select=fullname,systemuserid&$filter=Microsoft.Dynamics.CRM.NotEqualUserId(PropertyName=@p1)&@p1='systemuserid'
```

他のクエリ関数は、さまざまな方法で拒否することができます。 たとえば、次のような <xref href="Microsoft.Dynamics.CRM.Last7Days?text=Last7Days Function" /> を否定するとします (上記と同じエラーで失敗します)。

```http
GET [Organization URI]/api/data/v9.1/accounts?$select=name&$filter=not Microsoft.Dynamics.CRM.Last7Days(PropertyName=@p1)&@p1='createdon'
```
代わりに、次のような <xref href="Microsoft.Dynamics.CRM.OlderThanXDays?text=OlderThanXDays Function" /> を使用します。

```http
GET [Organization URI]/api/data/v9.1/accounts?$select=name&$filter=Microsoft.Dynamics.CRM.OlderThanXDays(PropertyName=@p1,PropertyValue=@p2)&@p1='createdon'&@p2=7
```

### <a name="see-also"></a>関連項目

[Web API 機能およびアクションのサンプル (C#)](samples/functions-actions-csharp.md)<br />
[Web API 機能およびアクションのサンプル (クライアント側 JavaScript)](samples/functions-actions-client-side-javascript.md)<br />
[Web API を使用して演算を実行する](perform-operations-web-api.md)<br />
[HTTP 要求の作成とエラーの処理](compose-http-requests-handle-errors.md)<br />
[Web API を使用したクエリ データ](query-data-web-api.md)<br />
[Web API を使用してエンティティを作成する](create-entity-web-api.md)<br />
[Web API を使用してエンティティを取得する](retrieve-entity-using-web-api.md)<br />
[Web API を使用したエンティティの更新と削除](update-delete-entities-using-web-api.md)<br />
[Web API を使用したエンティティの関連付けと関連付け解除](associate-disassociate-entities-using-web-api.md)<br />
[Web API アクションの使用](use-web-api-actions.md)<br />
[Web API を使用してバッチ操作を実行する](execute-batch-operations-using-web-api.md)<br />
[Web API を使用して別のユーザーを偽装する](impersonate-another-user-web-api.md)<br />
[Web API を使用する条件付き演算を実行する](perform-conditional-operations-using-web-api.md)
