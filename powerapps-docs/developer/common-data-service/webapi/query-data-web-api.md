---
title: Web API を使用してデータのクエリを実行する (Common Data Service)| Microsoft Docs
description: Common Data Service Web APIを使用して Common Data Service データをクエリするさまざまな方法と、これらのクエリに適用できるさまざまなシステム クエリ オプションについて説明します。
ms.custom: ''
ms.date: 09/10/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: fc3ade34-9c4e-4c33-88a4-aa3842c5eee1
caps.latest.revision: 78
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
# <a name="query-data-using-the-web-api"></a>Web API を使用したクエリ データ

エンティティ セットのデータを取得する場合は、`GET` 要求を使用します。 データを取得するときは、クエリ オプションを適用して、データのために必要な条件、および返されるエンティティ プロパティを設定することができます。  
    
<a name="bkmk_basicQuery"></a>
 
## <a name="basic-query-example"></a>ベーシック クエリの例

 この例は、取引先企業エンティティ セットをクエリし、`$select` および `$top` システム クエリ オプションを使用して、最初の 3 つの取引先企業の名前プロパティを返します。  
  
 **要求**

```http 
GET [Organization URI]/api/data/v9.1/accounts?$select=name
&$top=3 HTTP/1.1  
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
   "@odata.context":"[Organization URI]/api/data/v9.1/$metadata#accounts(name)",
   "value":[  
      {  
         "@odata.etag":"W/\"501097\"",
         "name":"Fourth Coffee (sample)",
         "accountid":"89390c24-9c72-e511-80d4-00155d2a68d1"
      },
      {  
         "@odata.etag":"W/\"501098\"",
         "name":"Litware, Inc. (sample)",
         "accountid":"8b390c24-9c72-e511-80d4-00155d2a68d1"
      },
      {  
         "@odata.etag":"W/\"501099\"",
         "name":"Adventure Works (sample)",
         "accountid":"8d390c24-9c72-e511-80d4-00155d2a68d1"
      }
   ]
}
 
```  
  
<a name="bkmk_limits"></a>

## <a name="limits-on-number-of-entities-returned"></a>返されるエンティティ数の制限

 小さなページ サイズを指定しない限り、各リクエストに対して最大 5000 のエンティティが返されます。 クエリ フィルターの条件と一致するエンティティがさらに存在する場合、`@odata.nextLink` プロパティが結果と共に返されます。 `@odata.nextLink` プロパティの値を新しい `GET` 要求と共に使用して、次のページのデータを返します。  
  
> [!NOTE]
>  モデル エンティティのクエリには、制限またはページ付けがありません。 詳細: [Web API を使用したクエリ メタデータ](query-metadata-web-api.md)  

<a name="bkmk_limitResults"></a>

### <a name="use-top-query-option"></a>`$top` クエリ オプションを使用する

`$top` システム クエリ オプションを使用して、返される結果の数を制限することができます。 次の例では、最初の 3 つの取引先企業のエンティティのみを返します。  
  
```http 
GET [Organization URI]/api/data/v9.1/accounts?$select=name,revenue&$top=3  
```  
  
> [!NOTE]
>  `$top` を使用して結果を制限すると、`odata.maxpagesize` の基本設定が適用されることを防ぎます。 `odata.maxpagesize` 基本設定または `$top` を使用することができますが、同時に両方を使用することはできません。 `odata.maxpagesize` の詳細については、「[ページに戻すエンティティ数の指定](query-data-web-api.md#bkmk_specifyNumber)」を参照してください。  
>   
>  また、`$top` を `$count` と共に使用しないでください。  

<a name="bkmk_specifyNumber"></a>

### <a name="specify-the-number-of-entities-to-return-in-a-page"></a>ページに戻すエンティティ数の指定

`odata.maxpagesize` の基本設定値を使用して、応答で返されるエンティティ数を要求します。  
  
> [!NOTE]
>  5000 を超える `odata.maxpagesize` 基本設定の値を使用することはできません。  
  
 次の例は accounts エンティティ セットをクエリし、最初の 3 つのアカウントのために `name` プロパティを戻します。  
  
 **要求**

```http 
GET [Organization URI]/api/data/v9.1/accounts?$select=name HTTP/1.1  
Accept: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Prefer: odata.maxpagesize=3  
```  
  
 **応答**  

```http 
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
Content-Length: 402  
Preference-Applied: odata.maxpagesize=3  
  
{  
   "@odata.context":"[Organization URI]/api/data/v9.1/$metadata#accounts(name)",
   "value":[  
      {  
         "@odata.etag":"W/\"437194\"",
         "name":"Fourth Coffee (sample)",
         "accountid":"7d51925c-cde2-e411-80db-00155d2a68cb"
      },
      {  
         "@odata.etag":"W/\"437195\"",
         "name":"Litware, Inc. (sample)",
         "accountid":"7f51925c-cde2-e411-80db-00155d2a68cb"
      },
      {  
         "@odata.etag":"W/\"468026\"",
         "name":"Adventure Works (sample)",
         "accountid":"8151925c-cde2-e411-80db-00155d2a68cb"
      }
   ],
   "@odata.nextLink":"[Organization URI]/api/data/v9.1/accounts?$select=name&$skiptoken=%3Ccookie%20pagenumber=%222%22%20pagingcookie=%22%253ccookie%2520page%253d%25221%2522%253e%253caccountid%2520last%253d%2522%257b8151925C-CDE2-E411-80DB-00155D2A68CB%257d%2522%2520first%253d%2522%257b7D51925C-CDE2-E411-80DB-00155D2A68CB%257d%2522%2520%252f%253e%253c%252fcookie%253e%22%20/%3E"
}
  
```  
  
 `@odata.nextLink` プロパティの値を使用して、次のレコードのセットを要求します。 値に対する追加のシステム クエリ オプションを変更または追加しないでください。 追加ページのすべての後続要求に対して、元の要求で使用したものと同じ odata.maxpagesize 基本設定値を使用する必要があります。 また、返された結果または `@odata.nextLink` プロパティの値をキャッシュし、以前取得したページが返されるようにします。  
  
> [!NOTE]
>  `@odata.nextLink` プロパティの値は URI エンコードされます。 送信前に値を URI エンコードすると、URL 内の XML Cookie 情報によりエラーが発生します。  
  
<a name="bkmk_applyqueryOptions"></a>

## <a name="apply-system-query-options"></a>システム クエリ オプションの適用

 エンティティ セットのために URL に追加する各システム クエリ オプションは、クエリ文字列の構文を使用して追加されます。 最初のクエリは [?] の後に追加され、それ以降のクエリ オプションは [&] を使用して分離されます。 すべてのクエリ オプションは、次の例のように大文字と小文字が区別されます。  
  
```http 
GET [Organization URI]/api/data/v9.1/accounts?$select=name,revenue
&$top=3
&$filter=revenue gt 100000  
```  
  
<a name="bkmk_requestProperties"></a>
 
## <a name="request-specific-properties"></a>特定のプロパティの要求

 `$select` システム クエリ オプションを使用して、以下の例に示すように、返されるプロパティを制限します。  
  
```http 
GET [Organization URI]/api/data/v9.1/accounts?$select=name,revenue  
```  
  
> [!IMPORTANT]
>  これはパフォーマンスのベスト プラクティスです。 プロパティが `$select` を使用して指定されない場合、すべてのプロパティが返されます。  
  
 特定の種類のプロパティを要求すると、さらに追加の読み取り専用プロパティが自動的に返されることを予期できます。  
  
 金額値を要求した場合、`_transactioncurrencyid_value` 検索プロパティが返されます。 このプロパティには取引通貨の GUID 値のみが含まれますので、この値を使用することにより <xref href="Microsoft.Dynamics.CRM.transactioncurrency?text=transactioncurrency EntityType" /> を使用して通貨に関する情報を取得できます。 または、コメントを要求することにより、同じ要求の追加データも取得できます。 詳細: [検索プロパティに関するデータの取得](#bkmk_lookupProperty)  
  
 アドレスの複合属性の一部のプロパティを要求する場合は、複合プロパティも取得します。 たとえば、クエリ要求が、取引先担当者の `address1_line1` プロパティの場合は、`address1_composite` プロパティも返されます。 
  
<a name="bkmk_filter"></a>
 
## <a name="filter-results"></a>結果のフィルター

 `$filter` システム クエリ オプションを使用して、エンティティが返される条件を設定します。  
  
<a name="bkmk_buildInFilterOperators"></a>

### <a name="standard-filter-operators"></a>標準フィルタ演算子

 Web API は、以下の表にリストされる標準 OData フィルタ演算子をサポートしています。  
  
|演算子|内容|例|  
|--------------|-----------------|-------------|  
|**比較演算子**|||  
|`eq`|等号|`$filter=revenue eq 100000`|  
|`ne`|等しくない|`$filter=revenue ne 100000`|  
|`gt`|より大きい|`$filter=revenue gt 100000`|  
|`ge`|以上|`$filter=revenue ge 100000`|  
|`lt`|より小さい|`$filter=revenue lt 100000`|  
|`le`|以下|`$filter=revenue le 100000`|  
|**論理演算子**|||  
|`and`|論理積|`$filter=revenue lt 100000 and revenue gt 2000`|  
|`or`|論理和|`$filter=contains(name,'(sample)') or contains(name,'test')`|  
|`not`|論理否定|`$filter=not contains(name,'sample')`|  
|**グループ化演算子**|||  
|`( )`|優先順位によるグループ化|`(contains(name,'sample') or contains(name,'test')) and revenue gt 5000`|  
  
> [!NOTE]
>  これは [11.2.5.1.1 組み込みフィルター処理](http://docs.oasis-open.org/odata/odata/v4.0/errata02/os/complete/part1-protocol/odata-v4.0-errata02-os-part1-protocol-complete.html) の一部です。 算術演算子と比較演算子は Web API ではサポートされていません。  
  
<a name="bkmk_buildInQueryFunctions"></a>

### <a name="standard-query-functions"></a>標準クエリ機能  
 
Web API では、以下の標準 OData 文字列クエリ機能がサポートされています。
 
|機能|例|  
|--------------|-------------|  
|`contains`|`$filter=contains(name,'(sample)')`|  
|`endswith`|`$filter=endswith(name,'Inc.')`|  
|`startswith`|`$filter=startswith(name,'a')`|  
  
> [!NOTE]
>  これは [11.2.5.1.2 組み込みフィルター処理](http://docs.oasis-open.org/odata/odata/v4.0/errata02/os/complete/part1-protocol/odata-v4.0-errata02-os-part1-protocol-complete.html) の一部です。 `Date`、`Math`、`Type`、`Geo` および他の文字列機能は Web API ではサポートされません。  
  
### <a name="common-data-service-web-api-query-functions"></a>Common Data Service Web API クエリ機能
 
Common Data Service には、パラメーターを受入れ、ブール値を返し、クエリでフィルター条件として使用できる、様々な特別な関数が用意されています。 これらの関数の一覧は、<xref:Microsoft.Dynamics.CRM.QueryFunctionIndex>を参照してください。 以下は <xref href="Microsoft.Dynamics.CRM.Between?text=Between Function" />の例で、5 ～ 2000 の間の従業員数の取引先企業を検索します。  
  
```http 
GET [Organization URI]/api/data/v9.1/accounts?$select=name,numberofemployees
&$filter=Microsoft.Dynamics.CRM.Between(PropertyName='numberofemployees',PropertyValues=["5","2000"])  
```  
  
詳細: [関数を使用してクエリを作成する](use-web-api-functions.md#bkmk_composeQueryWithFunctions) 

<a name="bkmk_LambdaOperators"></a>

### <a name="use-lambda-operators"></a>ラムダ演算子を使用する

Web APIでは、 `any` と `all` の2つのラムダ演算子を使用して、コレクションのブール式を評価することができます。

<a name ="bkmk_anyoperator"></a>

### <a name="any-operator"></a>`any` 演算子

`any` 演算子は、適用されたブール式がコレクションのメンバーに対して `true` である場合は `true` を返し、それ以外の場合は `false`を返します。 引数を指定しない`any` 演算子は、コレクションが空ではない場合に `true` を返します。

**例**

以下の例では、件名に「sometext」 が含まれる電子メールが1つ以上ある、すべてのアカウント エンティティ レコードを取得する方法を示しています。

```http
GET [Organization URI]/api/data/v9.1/accounts?$select=name
&$filter=Account_Emails/any(o:contains(o/subject,'sometext')) HTTP/1.1
Prefer: odata.include-annotations="*"
Accept: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0 
```
<a name ="bkmk_alloperator"></a>

### <a name="all-operator"></a>`all` 演算子

`all` 演算子は、適用されたブール式がコレクションのすべてのメンバに対して `true` である場合は `true` を返し、それ以外の場合は `false`を返します。

**例**

以下の例では、関連するすべてのタスクがクローズされている、すべての取引先企業エンティティ レコードを取得する方法を示しています。

```http
GET [Organization URI]/api/data/v9.1/accounts?$select=name
&$filter=Account_Tasks/all(o:o/statecode eq 1) HTTP/1.1
Prefer: odata.include-annotations="*"
Accept: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0 
```

次の例では、件名に「sometext」が含まれ、ステートコードがアクティブな電子メールが1つ以上ある、すべての取引先企業エンティティ レコードを取得する方法を示しています。

```http
GET [Organization URI]/api/data/v9.1/accounts?$select=name
&$filter=Account_Emails/any(o:contains(o/subject,'sometext') and 
o/statecode eq 0) HTTP/1.1
Prefer: odata.include-annotations="*"
Accept: application/json
OData-MaxVersion: 4.0
OData-Version: 4.0
``` 

以下の例は、 `any` と `all` 演算子を使用してネストされたクエリーを作成する方法を示しています。

```http
GET [Organization URI]/api/data/v9.1/accounts?$select=name
&$filter=(contact_customer_accounts/any(c:c/jobtitle eq 'jobtitle' and 
c/opportunity_customer_contacts/any(o:o/description ne 'N/A'))) and 
endswith(name,'{0}') HTTP/1.1
Prefer: odata.include-annotations="*"
Accept: application/json
OData-MaxVersion: 4.0
OData-Version: 4.0
```

### <a name="filter-parent-records-based-on-values-of-child-records"></a>子レコードの値に基づいて親レコードをフィルター処理する

以下の例では、[any 演算子](#bkmk_anyoperator)を使用して、以下のものを持つすべての取引先企業レコードを取得する方法を示しています:

- リンクされた営業案件レコードの予算のいずれかが 300 以上の場合、かつ
- 営業案件レコードの摘要に記述がない、または
- 営業案件レコードの摘要に 「*不適切*」 という語句が含まれている。

**要求**

```http
GET [Organization URI]/api/data/v9.1/accounts?$select=name
&$filter=not opportunity_customer_accounts/any(o:o/description eq null and 
o/budgetamount le 300 or 
contains(o/description, 'bad')) and 
opportunity_customer_accounts/any() and 
endswith(name,'{0}') HTTP/1.1
Accept: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0 
```

<a name="BKMK_FilterNavProperties"></a>

### <a name="filter-records-based-on-single-valued-navigation-property"></a>単一値のナビゲーション プロパティに基づくレコードのフィルター処理

ナビゲーション プロパティを使用すると、現在のエンティティと関連付けられたデータにアクセスすることができます。 *単一値* ナビゲーション プロパティは、多対 1 関係をサポートし、別のエンティティに対する参照が設定できるような検索属性に対応します。 詳細については次を参照してください: [ナビゲーション プロパティ](web-api-types-operations.md#bkmk_navprops)  
  
単一値ナビゲーション プロパティの値に基づき、エンティティ セットをフィルター処理することができます。 たとえば、指定された取引先企業の、子取引先企業を取得することができます。  
  
たとえば、次のようなものです。  
  
-   **指定された取引先担当者 ID に一致するすべての取引先企業を取得する**  
  
**要求** 
 
```http 
GET [Organization URI]/api/data/v9.1/accounts?$select=name
&$filter=primarycontactid/contactid eq a0dbf27c-8efb-e511-80d2-00155db07c77 HTTP/1.1  
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
"@odata.context":"[Organization URI]/api/data/v9.1/$metadata#accounts(name)",
"value":[  
        {  
            "@odata.etag":"W/\"513479\"",
            "name":"Adventure Works (sample)",
            "accountid":"3adbf27c-8efb-e511-80d2-00155db07c77"
        },
        {  
            "@odata.etag":"W/\"514057\"",
            "name":"Blue Yonder Airlines (sample)",
            "accountid":"3edbf27c-8efb-e511-80d2-00155db07c77"
        }
    ]
}  
```  

-   **指定された取引先企業 ID に対する子会社を取得**  
  
**要求**  

```http 
GET [Organization URI]/api/data/v9.1/accounts?$select=name
&$filter=parentaccountid/accountid eq 3adbf27c-8efb-e511-80d2-00155db07c77  
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
"@odata.context":"[Organization URI]/api/data/v9.1/$metadata#accounts(name)",
"value":[  
        {  
            "@odata.etag":"W/\"514058\"",
            "name":"Sample Child Account 1",
            "accountid":"915e89f5-29fc-e511-80d2-00155db07c77"
        },
        {  
            "@odata.etag":"W/\"514061\"",
            "name":"Sample Child Account 2",
            "accountid":"03312500-2afc-e511-80d2-00155db07c77"
        }
    ]
}   
```

### <a name="filter-results-based-on-values-of-collection-valued-navigation-properties"></a>コレクション値ナビゲーション プロパティの値に基づいて結果をフィルター処理します。

> [!NOTE]
> `$expand` で `$filter` を使用して、取得操作で関連レコードの結果をフィルターすることは可能です。 コレクション値ナビゲーション プロパティ名の後に、かっこで囲まれるシステム クエリ オプションのセミコロン区切りリストを使用できます。 `$expand` でサポートされているクエリ オプションは `$select`、`$filter`、`$top`、および `$orderby` です。 詳細: [拡張されたエンティティに適用するためのオプション](retrieve-entity-using-web-api.md#options-to-apply-to-expanded-entities)。

コレクション値ナビゲーション プロパティの値に基づいて結果をフィルター処理する 2 つのオプションを次に示します:

1. **ラムダ演算子を使用してクエリを構築する**

ラムダ演算子を使用することで、リンク エンティティの収集プロパティの値にフィルターを適用することができます。 以下の例では、 `team` および `teammembership` エンティティ タイプにリンクされている、 `systemuser` エンティティ タイプのレコードを取得します。つまり、「CITTEST」 という名前のチームの管理者を兼ねている `systemuser` レコードを取得します。

```http
GET [Organization URI]/api/data/v9.1/systemusers?$filter=(teammembership_association/any(t:t/name eq 'CITTEST'))
&$select=fullname,businessunitid,title,address1_telephone1,systemuserid
&$orderby=fullname
Accept: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
```
詳細については次を参照してください: [ラムダ演算子を使用する](#bkmk_LambdaOperators)

2. **複数の操作を使用して、コレクションの値に基づく個々のエンティティの結果フィルター処理を繰り返します**

上記の例と同じ結果を得るには、2つのエンティティ タイプのレコードを取得し、一方のエンティティのコレクションの値を他方のエンティティの値と繰り返し照合することで、コレクションの値に基づいてエンティティをフィルター処理します。

以下の例の手順に従って、反復メソッドを使用して結果をフィルターする方法を理解します。

1. <xref href="Microsoft.Dynamics.CRM.team" />._administratorid_value 値の個別一覧を入手してください。
      - `GET [OrganizationURI]/api/data/v9.1/teams?$select=_administratorid_value&$filter=_administrator_value ne null`
      - 次に戻り値をループ処理して重複を取り除き、個別一覧を取得します。 すなわち、新しい配列を作成し、クエリ結果をループしてそれぞれが新しい配列にすでに存在するかどうかを確認し、存在しない場合は追加します。 これで個別の `systemuserid` 値の一覧を与えます。
      - JavaScript と C# でこれをする方法は異なりますが、基本的に同じ結果が得られます。
2. `systemuserid` 値をステップ 1 で収集した一覧と比較する <xref href="Microsoft.Dynamics.CRM.ContainValues?text=ContainValues Query Function" /> を使用したクエリ <xref href="Microsoft.Dynamics.CRM.systemuser" />。

<a name="bkmk_order"></a>
 
## <a name="order-results"></a>順番の結果

 項目が返される順番を、`$orderby` システム クエリ オプションを使用して指定します。 `asc` または `desc` 接尾辞を使用して、それぞれ昇順または降順を指定します。 接尾辞が適用されない場合、既定は昇順です。 以下の例では、取引先企業の名前および売り上げプロパティを、売り上げを昇順で、名前を降順で取得します。  
  
```http 
GET [Organization URI]/api/data/v9.1/accounts?$select=name,revenue
&$orderby=revenue asc,name desc
&$filter=revenue ne null  
```  
<a name="bkmk_AggregateGroup"></a>

## <a name="aggregate-and-grouping-results"></a>結果の集計およびグループ化

`$apply` を使用すると、データを動的に集計およびグループ化することができます。  `$apply` を使用する可能性のある例:

|使用例|例|
|--------------|-------------| 
|クエリ内の一意のステータスのリスト|`accounts?$apply=groupby((statuscode))`|
|予想値合計の集計|`opportunities?$apply=aggregate(estimatedvalue with sum as total)`|
|予想値およびステータスに基づく取引の平均サイズ|`opportunities?$apply=groupby((statuscode),aggregate(estimatedvalue with average as averagevalue)`|
|ステータスに基づく予測値の合計|`opportunities?$apply=groupby((statuscode),aggregate(estimatedvalue with sum as total))`|
|アカウント名ごとの業案件の売上合計|`opportunities?$apply=groupby((parentaccountid/name),aggregate(estimatedvalue with sum as total))`|
|「WA」 の取引先企業の取引先責任者名|`accounts?$apply=filter(address1_stateorprovince eq 'WA')/groupby((primarycontactid/fullname))`|
|最後に作成されたレコードの日時|`accounts?$apply=aggregate(createdon with max as lastCreate)`|
|最初に作成されたレコードの日時|`accounts?$apply=aggregate(createdon with min as firstCreate)`|

集計機能は 50,000 レコードのコレクションに制限されます。  Common Data Service での集約機能の使用に関する詳細は、次を参照してください: [FetchXML を使用してクエリを構築する](../use-fetchxml-construct-query.md)

OData データ集計の追加の詳細はこちらを参照してください: [データ集計用 OData 拡張 バージョン 4.0](http://docs.oasis-open.org/odata/odata-data-aggregation-ext/v4.0/cs01/odata-data-aggregation-ext-v4.0-cs01.html)。  Common Data Service はこれらの集計手法のサブセットのみをサポートすることに注意してください。


<a name="bkmk_useParameterAliases"></a>
  
## <a name="use-parameter-aliases-with-system-query-options"></a>システム クエリ オプションを持つパラメーター エイリアスを使用します

 `$filter` および `$orderby` システム クエリ オプションのために、パラメーター エイリアスを使用することができます。 パラメーター エイリアスは、1 つの要求の中で同じ値を複数回使用することができます。 エイリアスが値が割り当てられていない場合は、空白であると判断します。  
  
 パラメーター エイリアスなし:

```http  
GET [Organization URI]/api/data/v9.1/accounts?$select=name,revenue
&$orderby=revenue asc,name desc
&$filter=revenue ne null  
```  
  
 パラメーター エイリアスあり:

```http  
GET [Organization URI]/api/data/v9.1/accounts?$select=name,revenue
&$orderby=@p1 asc,@p2 desc
&$filter=@p1 ne @p3&@p1=revenue&@p2=name  
```  
  
 また、関数を使用するとき、パラメーター エイリアスを使用することもできます。 詳細: [Web API 機能を使用](use-web-api-functions.md)  
    
<a name="bkmk_retrieveCount"></a>
 
## <a name="retrieve-a-count-of-entities"></a>エンティティ数の取得

 `$count` システム クエリ オプションを `true` の値と共に使用して、フィルター条件と一致するエンティティ数を最大 5000 含めます。  
  
> [!NOTE]
>  カウント値はシステム内のエンティティの総数を表すものではありません。 これは、返されるエンティティ数の最大数により制限されています。 詳細は: [返されるエンティティ数の制限](#bkmk_limits)  
  
 応答の `@odata.count` プロパティには、`odata.maxpagesize` 基本設定の制限に関係なく、フィルター条件と一致するエンティティ数が含まれます。  
  
> [!NOTE]
>  `$top` を `$count` と共に使用しないでください。  
  
 次の例では、名前に "sample" が含まれるという条件と一致する 10 の取引先企業があることが示されますが、最初の 3 つの取引先企業のみが返されます。  
  
 **要求**

```http 
GET [Organization URI]/api/data/v9.1/accounts?$select=name
&$filter=contains(name,'sample')
&$count=true HTTP/1.1  
Accept: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Prefer: odata.maxpagesize=3  
```  
  
 **応答** 
 
```http 
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
Preference-Applied: odata.maxpagesize=3  
  
{  
   "@odata.context":"[Organization URI]/api/data/v9.1/$metadata#accounts(name)",
   "@odata.count":10,
   "value":[  
      {  
         "@odata.etag":"W/\"502482\"",
         "name":"Fourth Coffee (sample)",
         "accountid":"655eaf89-f083-e511-80d3-00155d2a68d3"
      },
      {  
         "@odata.etag":"W/\"502483\"",
         "name":"Litware, Inc. (sample)",
         "accountid":"675eaf89-f083-e511-80d3-00155d2a68d3"
      },
      {  
         "@odata.etag":"W/\"502484\"",
         "name":"Adventure Works (sample)",
         "accountid":"695eaf89-f083-e511-80d3-00155d2a68d3"
      }
   ],
   "@odata.nextLink":"[Organization URI]/api/data/v9.1/accounts?$select=name&$filter=contains(name,'sample')&$skiptoken=%3Ccookie%20pagenumber=%222%22%20pagingcookie=%22%253ccookie%2520page%253d%25221%2522%253e%253caccountid%2520last%253d%2522%257b695EAF89-F083-E511-80D3-00155D2A68D3%257d%2522%2520first%253d%2522%257b655EAF89-F083-E511-80D3-00155D2A68D3%257d%2522%2520%252f%253e%253c%252fcookie%253e%22%20istracking=%22False%22%20/%3E"
}

  
```  
  
 カウント以外のデータを返さないようにするには、`$count` を任意のコレクションに適用して、値のみを取得します。  
  
 **要求**  

```http 
GET [Organization URI]/api/data/v9.1/accounts/$count HTTP/1.1  
Accept: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
```  
  
 **応答**  
```http 
HTTP/1.1 200 OK  
Content-Type: text/plain  
OData-Version: 4.0  
  
10  
```  
  
<a name="bkmk_includeFormattedValues"></a>

## <a name="include-formatted-values"></a>書式設定値を含める

 プロパティが結果と共にフォーマットされた値を受け取るようにしたいときは、`odata.include-annotations` 基本設定を `OData.Community.Display.V1.FormattedValue` の値で使用します。 応答には、以下の命名規則と一致するプロパティと共に、これらの値が含まれます。  
  
```  
<propertyname>@OData.Community.Display.V1.FormattedValue  
```  
 次の例は、取引先企業用のエンティティ セットをクエリし、フォーマットされた値をサポートするプロパティを含む、最初のレコードを返します。  
  
 **要求**

```http 
GET [Organization URI]/api/data/v9.1/accounts?$select=name,donotpostalmail,accountratingcode,numberofemployees,revenue
&$top=1 HTTP/1.1  
Accept: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Prefer: odata.include-annotations="OData.Community.Display.V1.FormattedValue"  
```  
  
 **応答**  
```http 
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
Preference-Applied: odata.include-annotations="OData.Community.Display.V1.FormattedValue"  
  
{  
   "@odata.context":"[Organization URI]/api/data/v9.1/$metadata#accounts(name,donotpostalmail,accountratingcode,numberofemployees,revenue)",
   "value":[  
      {  
         "@odata.etag":"W/\"502170\"",
         "name":"Fourth Coffee (sample)",
         "donotpostalmail@OData.Community.Display.V1.FormattedValue":"Allow",
         "donotpostalmail":false,
         "accountratingcode@OData.Community.Display.V1.FormattedValue":"Default Value",
         "accountratingcode":1,
         "numberofemployees@OData.Community.Display.V1.FormattedValue":"9,500",
         "numberofemployees":9500,
         "revenue@OData.Community.Display.V1.FormattedValue":"$100,000.00",
         "revenue":100000,
         "accountid":"89390c24-9c72-e511-80d4-00155d2a68d1",
         "transactioncurrencyid_value":"50b6dd7b-f16d-e511-80d0-00155db07cb1"
      }
   ]
}
```  

<a name="bkmk_retrieverelatedentities"></a>

## <a name="retrieve-related-entities-with-query"></a>クエリーを使用して関連エンティティを取得する

ナビゲーション プロパティの `$expand` システム クエリ オプションを使用して、関連エンティティからどのデータが返されるかをコントロールします。 詳細については次を参照してください: [クエリを使用して関連エンティティを取得する](retrieve-related-entities-query.md)

<a name="bkmk_lookupProperty"></a>

## <a name="retrieve-data-about-lookup-properties"></a>検索プロパティに関するデータの取得

 クエリに検索プロパティが含まれる場合、これらのプロパティ内のデータに関する追加情報を提供する、注釈を要求することができます。 通常、同じデータは、単一値のナビゲーション プロパティの知識、および関連するエンティティに含まれるデータを使用して生成することができます。 ただし、プロパティが、複数の種類のエンティティを参照する可能性がある検索属性である場合、この情報から検索プロパティがどの種類のエンティティを参照するか知ることができます。 詳細: [検索プロパティ](web-api-types-operations.md#bkmk_lookupProperties)  
  
 これらのプロパティで使用できる、2 種類の追加の注釈があります。  
  
|Annotation|内容|  
|----------------|-----------------|  
|Microsoft.Dynamics.CRM.associatednavigationproperty|エンティティへの参照を含む、単一値のナビゲーション プロパティの名前。|  
|Microsoft.Dynamics.CRM.lookuplogicalname|検索が参照するエンティティの論理名。|  
  
 また、これらのプロパティには、「[書式設定値を含める](query-data-web-api.md#bkmk_includeFormattedValues)」で説明されているように、フォーマットされた値を含めることができます。 書式設定されている値と同様に、`odata.include-annotations` 基本設定セットを使用して、適切な特定の注釈の種類に対して他の注釈を返したり、値に `"*"` を設定して 3 つすべてを返すことができます。 次の例では、インシデント エンティティの `_customerid_value` 検索プロパティおよびそれに含まれる注釈に関する情報を取得するための、要求および応答を示します。  
  
 **要求**  

```http 
GET [Organization URI]/api/data/v9.1/incidents(39dd0b31-ed8b-e511-80d2-00155d2a68d4)?$select=title,_customerid_value
&$expand=customerid_contact($select=fullname) HTTP/1.1  
Accept: application/json  
Content-Type: application/json; charset=utf-8  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Prefer: odata.include-annotations="*"  
```  
  
 **応答**  

```http 
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
Preference-Applied: odata.include-annotations="*"  
  
{  
    "@odata.context":"[Organization URI]/api/data/v9.1/$metadata#incidents(title,_customerid_value,customerid_contact(fullname))/$entity",
    "@odata.etag":"W/\"504696\"",
    "_customerid_value@Microsoft.Dynamics.CRM.associatednavigationproperty":"customerid_contact",
    "_customerid_value@Microsoft.Dynamics.CRM.lookuplogicalname":"contact",
    "_customerid_value@OData.Community.Display.V1.FormattedValue":"Susanna Stubberod (sample)",
    "_customerid_value":"7ddd0b31-ed8b-e511-80d2-00155d2a68d4",
    "incidentid":"39dd0b31-ed8b-e511-80d2-00155d2a68d4",
    "customerid_contact":{  
        "@odata.etag":"W/\"503587\"",
        "fullname":"Susanna Stubberod (sample)",
        "contactid":"7ddd0b31-ed8b-e511-80d2-00155d2a68d4"
    }
} 
```  
  
<a name="bkmk_expandRelated"></a>

## <a name="retrieve-related-entities-by-expanding-navigation-properties"></a>ナビゲーション プロパティの拡張による関連エンティティの取得
 
<a bkmk="bkmk_retrieverelatedentityexpandcollectionnavprop"></a>

### <a name="retrieve-related-entities-by-expanding-collection-valued-navigation-properties"></a>コレクション値ナビゲーション プロパティの拡張による関連エンティティの取得

コレクション値ナビゲーション パラメーターを拡張してエンティティ セットの関連エンティティを取得すると、`@odata.nextLink` プロパティが関連エンティティに返されます。 `@odata.nextLink` プロパティの値を新しい `GET` 要求と共に使用して、必要なデータを返す必要があります。  

次の例は、上位 5 件の取引先企業レコードに割り当てられたタスクを取得します。  
  
**要求**

```http 
GET [Organization URI]/api/data/v9.1/accounts?$top=5
&$select=name
&$expand=Account_Tasks($select=subject,scheduledstart) HTTP/1.1  
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
   "@odata.context":"[Organization URI]/api/data/v9.1/$metadata#accounts(name,Account_Tasks,Account_Tasks(subject,scheduledstart))",
   "value":[  
      {  
         "@odata.etag":"W/\"513475\"",
         "name":"Fourth Coffee (sample)",
         "accountid":"36dbf27c-8efb-e511-80d2-00155db07c77",
         "Account_Tasks":[  

         ],
         "Account_Tasks@odata.nextLink":"[Organization URI]/api/data/v9.1/accounts(36dbf27c-8efb-e511-80d2-00155db07c77)/Account_Tasks?$select=subject,scheduledstart"
      },
      {  
         "@odata.etag":"W/\"513477\"",
         "name":"Litware, Inc. (sample)",
         "accountid":"38dbf27c-8efb-e511-80d2-00155db07c77",
         "Account_Tasks":[  

         ],
         "Account_Tasks@odata.nextLink":"[Organization URI]/api/data/v9.1/accounts(38dbf27c-8efb-e511-80d2-00155db07c77)/Account_Tasks?$select=subject,scheduledstart"
      },
      {  
         "@odata.etag":"W/\"514074\"",
         "name":"Adventure Works (sample)",
         "accountid":"3adbf27c-8efb-e511-80d2-00155db07c77",
         "Account_Tasks":[  

         ],
         "Account_Tasks@odata.nextLink":"[Organization URI]/api/data/v9.1/accounts(3adbf27c-8efb-e511-80d2-00155db07c77)/Account_Tasks?$select=subject,scheduledstart"
      },
      {  
         "@odata.etag":"W/\"513481\"",
         "name":"Fabrikam, Inc. (sample)",
         "accountid":"3cdbf27c-8efb-e511-80d2-00155db07c77",
         "Account_Tasks":[  

         ],
         "Account_Tasks@odata.nextLink":"[Organization URI]/api/data/v9.1/accounts(3cdbf27c-8efb-e511-80d2-00155db07c77)/Account_Tasks?$select=subject,scheduledstart"
      },
      {  
         "@odata.etag":"W/\"514057\"",
         "name":"Blue Yonder Airlines (sample)",
         "accountid":"3edbf27c-8efb-e511-80d2-00155db07c77",
         "Account_Tasks":[  

         ],
         "Account_Tasks@odata.nextLink":"[Organization URI]/api/data/v9.1/accounts(3edbf27c-8efb-e511-80d2-00155db07c77)/Account_Tasks?$select=subject,scheduledstart"
          }
       ]
    }
 
```  

<a bkmk="bkmk_retrieverelatedentitysingleandcollectionnavprop"></a>
  
### <a name="retrieve-related-entities-by-expanding-both-single-valued-and-collection-valued-navigation-properties"></a>単一値とコレクション値の両方のナビゲーション プロパティを拡張して、関連するエンティティを取得します

次の例では、単一値とコレクション値の両方のナビゲーション プロパティを使用して、エンティティセットの関連エンティティを拡張する方法を示します。 既に説明しているように、コレクション値ナビゲーション プロパティを拡張してエンティティ セットの関連エンティティを取得すると、関連エンティティの `@odata.nextLink` プロパティが返されます。 `@odata.nextLink` プロパティの値を新しい `GET` 要求と共に使用して、必要なデータを返す必要があります。  
  
この例では、上位 3 件の取引先企業に割り当てられた取引先担当者およびタスクを取得します。  
  
**要求**

```http 
GET [Organization URI]/api/data/v9.1/accounts?$top=3
&$select=name
&$expand=primarycontactid($select=contactid,fullname),Account_Tasks($select=subject,scheduledstart)  HTTP/1.1  
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
   "@odata.context":"[Organization URI]/api/data/v9.1/$metadata#accounts(name,primarycontactid,Account_Tasks,primarycontactid(contactid,fullname),Account_Tasks(subject,scheduledstart))",
   "value":[  
      {  
         "@odata.etag":"W/\"550614\"",
         "name":"Fourth Coffee (sample)",
         "accountid":"5b9648c3-68f7-e511-80d3-00155db53318",
         "primarycontactid":{  
            "contactid":"c19648c3-68f7-e511-80d3-00155db53318",
            "fullname":"Yvonne McKay (sample)"
         },
         "Account_Tasks":[  

         ],
         "Account_Tasks@odata.nextLink":"[Organization URI]/api/data/v9.1/accounts(5b9648c3-68f7-e511-80d3-00155db53318)/Account_Tasks?$select=subject,scheduledstart"
      },
      {  
         "@odata.etag":"W/\"550615\"",
         "name":"Litware, Inc. (sample)",
         "accountid":"5d9648c3-68f7-e511-80d3-00155db53318",
         "primarycontactid":{  
            "contactid":"c39648c3-68f7-e511-80d3-00155db53318",
            "fullname":"Susanna Stubberod (sample)"
         },
         "Account_Tasks":[  

         ],
         "Account_Tasks@odata.nextLink":"[Organization URI]/api/data/v9.1/accounts(5d9648c3-68f7-e511-80d3-00155db53318)/Account_Tasks?$select=subject,scheduledstart"
      },
      {  
         "@odata.etag":"W/\"550616\"",
         "name":"Adventure Works (sample)",
         "accountid":"5f9648c3-68f7-e511-80d3-00155db53318",
         "primarycontactid":{  
            "contactid":"c59648c3-68f7-e511-80d3-00155db53318",
            "fullname":"Nancy Anderson (sample)"
         },
         "Account_Tasks":[  

         ],
         "Account_Tasks@odata.nextLink":"[Organization URI]/api/data/v9.1/accounts(5f9648c3-68f7-e511-80d3-00155db53318)/Account_Tasks?$select=subject,scheduledstart"
      }
   ]
}
  
```  
<a name="BKMK_changetracking"></a>

## <a name="use-change-tracking-to-synchronize-data-with-external-systems"></a>変更の追跡を使用してデータを外部システムに同期

変更の追跡機能を使用することで、データが最初に抽出された後、あるいはデータが最後に同期された後で変更されたデータを検出し、データの同期を効率的に維持することができます。 エンティティの変更は、`odata.track-changes` を基本設定ヘッダーとして追加し、Web API リクエストを使用して追跡できます。 プリファレンス ヘッダーの `odata.track-changes` は、エンティティの変更を取得するために使用する、デルタ リンクを返すことを要求します。

詳細については次を参照してください: [変更の追跡を使用して、データを外部システムと同期する](../use-change-tracking-synchronize-data-external-systems.md)

### <a name="see-also"></a>関連項目

[Web API クエリ データのサンプル (C#)](samples/query-data-csharp.md)<br />
[Web API クエリ データのサンプル (クライアント側の JavaScript)](samples/query-data-client-side-javascript.md)<br />
[Web API を使用して演算を実行する](perform-operations-web-api.md)<br />
[HTTP 要求の作成とエラーの処理](compose-http-requests-handle-errors.md)<br />
[Web API を使用してエンティティを作成する](create-entity-web-api.md)<br />
[Web API を使用してエンティティを取得する](retrieve-entity-using-web-api.md)<br />
[Web API を使用したエンティティの更新と削除](update-delete-entities-using-web-api.md)<br />
[Web API を使用したエンティティの関連付けと関連付け解除](associate-disassociate-entities-using-web-api.md)<br />
[Web API 関数の使用](use-web-api-functions.md)<br />
[Web API アクションの使用](use-web-api-actions.md)<br />
[Web API を使用してバッチ操作を実行する](execute-batch-operations-using-web-api.md)<br />
[Web API を使用して別のユーザーを偽装する](impersonate-another-user-web-api.md)<br />
[Web API を使用する条件付き演算を実行する](perform-conditional-operations-using-web-api.md)
