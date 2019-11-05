---
title: ポータルで PowerApps Common Data Service エンティティタグを使用する |MicrosoftDocs
description: ポータルで使用できる PowerApps Common Data Service エンティティタグについて説明します。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: b6efc3e176602d366315b9b54b66593005051e55
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2019
ms.locfileid: "73543263"
---
# <a name="powerapps-common-data-service-entity-tags"></a>PowerApps Common Data Service エンティティタグ

Powerapps エンティティタグは、PowerApps データを読み込んで表示したり、他の PowerApps ポータルフレームワークサービスを使用したりするために使用されます。 これらのタグは、液体言語の PowerApps 固有の拡張機能です。

## <a name="chart"></a>グラフ

PowerApps グラフを web ページに追加します。 グラフタグは、web ページの [コピー] フィールド、または Web テンプレートの [ソース] フィールドで追加できます。 Web ページに PowerApps グラフを追加する手順については、「[ポータルでの web ページへのグラフの追加](../configure/add-chart.md)」を参照してください。

```
{% chart id:"EE3C733D-5693-DE11-97D4-00155DA3B01E" viewid:"00000000-0000-0000-00AA-000010001006" %}
```

### <a name="parameters"></a>パラメーター

グラフタグには、グラフ id と viewid という2つのパラメーターが用意されています。

**グラフ id**

グラフの視覚化 ID。 これを取得するには、グラフをエクスポートします。

**viewid**

ビューエディターで開かれたときのエンティティの ID。 

## <a name="powerbi"></a>powerbi

Power BI のダッシュボードとレポートをページ内に追加します。 タグは、web ページの **[コピー]** フィールド、または web テンプレートの **[ソース]** フィールドで追加できます。 ポータルの web ページに Power BI レポートまたはダッシュボードを追加する手順については、「[ポータルで Power BI レポートまたはダッシュボードを web ページに追加](../admin/add-powerbi-report.md)する」を参照してください。

> [!NOTE]
> タグを機能させるには、PowerApps ポータル管理センターから[Power BI 統合を有効](../admin/set-up-power-bi-integration.md)にする必要があります。 Power BI 統合が有効になっていない場合、ダッシュボードまたはレポートは表示されません。

### <a name="parameters"></a>パラメーター

Powerbi タグは、次のパラメーターを受け取ります。

**道**

Power BI レポートまたはダッシュボードのパス。 Power BI レポートまたはダッシュボードがセキュリティで保護されている場合は、認証の種類を指定する必要があります。

```
{% powerbi path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000001/ReportSection01" %}
```

**authentication_type**

Power BI レポートまたはダッシュボードに必要な認証の種類。 このパラメーターの有効な値は次のとおりです。

- **Anonymous**: web Power BI レポートへのパブリッシュを埋め込むことができます。 既定の認証の種類は Anonymous です。

- **AAD**: セキュリティで保護された Power BI レポートまたはダッシュボードを Power BI Azure Active Directory 認証済みユーザーに共有できます。

- **powerbiembedded**: セキュリティで保護された Power BI レポートまたはダッシュボードを、Power BI ライセンスを持たない外部ユーザーまたは Azure Active Directory 認証の設定を使用して共有できます。 Power BI Embedded サービスのセットアップの詳細については、「 [Enable Power BI Embedded service](../admin/set-up-power-bi-integration.md#enable-power-bi-embedded-service)」を参照してください。 

セキュリティで保護された Power BI レポートまたはダッシュボードを追加するときに、それがポータル Azure Active Directory または Power BI Embedded サービスと共有されていることを確認します。 

> [!NOTE]
> `authentication_type` パラメーターの値では大文字と小文字が区別されません。

```
{% powerbi authentication_type:"AAD" path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000001/ReportSection01" %}
```

また、1つまたは複数の値に対してレポートをフィルター処理することもできます。 レポートをフィルター処理する構文は次のとおりです。

URL? filter =**テーブル**/**フィールド**eq '**値**'

たとえば、Bert 髪という名前の連絡先のデータを表示するようにレポートをフィルター処理するとします。 URL は次のように追加する必要があります。

? filter = 役員/役員 eq ' Bert ヘア '

完成したコードは次のようになります。

```
{% powerbi authentication_type:"AAD" path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000001/ReportSection01?filter=Executives/Executive eq 'Bert Hair'" %}
```

レポートのフィルター処理に関する詳細: [URL でクエリ文字列パラメーターを使用してレポートをフィルター処理する](https://docs.microsoft.com/power-bi/service-url-filters)

> [!NOTE]
> 匿名レポートはフィルター処理をサポートしていません。 

次のように `capture ` 液体変数を使用して、動的パスを作成することもできます。

```
{% capture pbi_path %}https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000001/ReportSection01?filter=Executives/Executive eq '{{user.id}}'{% endcapture %}
{% powerbi authentication_type:"AAD" path:pbi_path %}
```

液体変数の詳細については、「[可変タグ](variable-tags.md)」を参照してください。

**タイル id**

指定されたダッシュボードのタイルを表示します。 タイルの ID を指定する必要があります。

```
{% powerbi authentication_type:"AAD" path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/dashboards/00000000-0000-0000-0000-000000000001" tileid:"00000000-0000-0000-0000-000000000002" %}
```

**ロール**

Power BI レポートに割り当てられたロール。 このパラメーターは、 **authentication_type**パラメーターが**powerbiembedded**に設定されている場合にのみ機能します。

Power BI でロールを定義し、それらをレポートに割り当てている場合は、 **powerbi**液体タグに適切なロールを指定する必要があります。 ロールを使用すると、レポートに表示されるデータをフィルター処理できます。 複数のロールは、コンマで区切って指定できます。 Power BI でのロールの定義の詳細については、「 [Power BI を使用した行レベルのセキュリティ (RLS)](https://docs.microsoft.com/power-bi/service-admin-rls)」を参照してください。

```
{% powerbi authentication_type:"powerbiembedded" path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000000/ReportSection2" roles:"Region_East,Region_West" %}
```

ロールが Power BI レポートに割り当てられていて、液体タグで**roles**パラメーターを指定しなかった場合、またはパラメーターでロールを指定しなかった場合は、エラーが表示されます。

> [!TIP]
> ポータルで定義されている web ロールを Power BI ロールとして使用する場合は、変数を定義し、その変数に web ロールを割り当てることができます。 その後、定義された変数を液体タグで使用できます。
>
> たとえば、ポータルで Region_East と Region_West として2つの web ロールを定義したとします。 これらのコードを結合するには、次のコードを使用します: `{% assign webroles = user.roles | join: ", " %}`
>
> 上記のコードスニペットでは、`webroles` は変数であり、Region_East および Region_West web ロールが格納されます。
>
> 次のように、液体タグで `webroles` 変数を使用します。
>
> `{% powerbi authentication_type:"powerbiembedded" path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000000/ReportSection2" roles:webroles%}`

## <a name="editable"></a>'94'5c

指定された PowerApps ポータル CMS オブジェクトを、ポータルで編集可能として表示します。ユーザーは、そのオブジェクトに対するコンテンツ編集アクセス許可を持っています。 編集可能なオブジェクトには、[ページ](liquid-objects.md#page)、[スニペット](liquid-objects.md#snippets)、および[web リンク](liquid-objects.md#weblinks)があります。  

```
{% editable page 'adx_copy' type: 'html', title: 'Page Copy', escape: false, liquid: true %}

{% editable snippets Header type: 'html' %}

<!--

An editable web link set required a specific DOM structure, with

certain classes on the containing element, as demonstrated here.

-->

{% assign primary_nav = weblinks[Primary Navigation] %}

{% if primary_nav %}

<div {% if primary_nav.editable %}class=xrm-entity xrm-editable-adx_weblinkset{% endif %}>

<ul>

<!-- Render weblinks... -->

</ul>

{% editable primary_nav %}

</div>

{% endif %}
```

### <a name="parameters"></a>パラメーター

編集可能に指定された最初のパラメーターは編集可能なオブジェクトです。 たとえば、web リンクセット、スニペット、現在のページなどがあります。 省略可能な2番目のパラメーターは、表示および編集するオブジェクト内の属性名またはキーを指定します。 これには、エンティティ属性の名前、またはスニペットの名前を指定できます。たとえば、のようになります。

これらの初期パラメーターの後、タグはいくつかのオプションの名前付きパラメーターをサポートしています。

**講義**

このタグによって表示されるルート要素のクラス属性値を指定します。

**標準**

編集可能な項目に値がない場合に表示される既定値。

**付ける**

このタグによって表示される値が HTML エンコードされるかどうかを示すブール値。 既定では、これは false です。

**計**

このタグによって表示されるテキスト値内に存在する液体テンプレートコードが処理されるかどうかを示すブール値。 これは、既定では true です。

**番号**

このタグによって表示されるコンテナー HTML タグの名前。 既定では、このタグによって div 要素が表示されます。 一般に、このパラメーターの値として div または span のどちらかを選択することをお勧めします。

**題**

コンテンツ編集インターフェイス内の編集可能なこの項目のラベルを指定します。 何も指定されていない場合は、わかりやすいラベルが自動的に生成されます。

**各種**

編集可能なテキスト値について、表示される編集インターフェイスの種類を示す文字列値。 このパラメーターの有効な値は、html またはテキストです。 既定値は html です。

## <a name="entitylist"></a>entitylist

指定されたエンティティリストを名前または ID で読み込みます。 エンティティリストのプロパティには、タグブロック内で使用できる[entitylist オブジェクト](liquid-objects.md#entitylist)を使用してアクセスできます。 エンティティリストの実際の結果レコードを表示するには、ブロック内で[entityview](#entityview)タグを使用します。  

エンティティリストが正常に読み込まれると、ブロック内のコンテンツがレンダリングされます。 エンティティリストが見つからない場合、ブロックコンテンツはレンダリングされません。

```
{% entitylist name:My Entity List %}

Loaded entity list {{ entitylist.adx_name }}.

{% endentitylist %}
```
既定では、entitylist オブジェクトには、変数名 entitylist が指定されます。 必要に応じて、別の変数名を指定することもできます。

```
{% entitylist my_list = name:My Entity List %}

Loaded entity list {{ my_list.adx_name }}.

{% endentitylist %}
```

### <a name="parameters"></a>パラメーター

Id、名前、またはキーの**いずれか1つだけ**を指定して、読み込むエンティティリストを選択します。

**番号**

[GUID](https://en.wikipedia.org/wiki/Globally_unique_identifier) ID を使ってエンティティリストを読み込みます。 id は、GUID として解析できる文字列である必要があります。  

```
{% entitylist id:936DA01F-9ABD-4d9d-80C7-02AF85C822A8 %}

Loaded entity list {{ entitylist.adx_name }}.

{% endentitylist %}
```

一般に、リテラル GUID 文字列は使用されません。 代わりに、別の変数の GUID プロパティを使用して id が指定されます。

```
{% entitylist id:page.adx_entitylist.id %}

Loaded entity list {{ entitylist.adx_name }}.

{% endentitylist %}
```

**指定**

名前を指定してエンティティリストを読み込みます。

```
{% entitylist name:My Entity List %}

Loaded entity list {{ entitylist.adx_name }}.

{% endentitylist %}
```

**レジストリ**

ID**または**名前を指定してエンティティリストを読み込みます。 指定されたキー値を[GUID](https://en.wikipedia.org/wiki/Globally_unique_identifier)として解析できる場合、エンティティリストは ID で読み込まれます。 それ以外の場合は、名前で読み込まれます。

```
<!-- key_variable can hold an ID or name -->

{% entitylist key:key_variable %}

Loaded entity list {{ entitylist.adx_name }}.

{% endentitylist %}
```

**言語\_コード**

読み込むエンティティリストのローカライズされたラベルを選択する PowerApps 整数言語コード。 言語\_コードが指定されていない場合は、ポータルアプリケーション PowerApps 接続の既定の言語が使用されます。

```
{% entitylist name:"My Entity List", language_code:1033 %}

Loaded entity list {{ entitylist.adx_name }}.

{% endentitylist %}
```

## <a name="entityview"></a>entityview

名前または ID を指定して、特定の PowerApps ビューを読み込みます。 ビューのߝビューの列メタデータ、改ページ位置の結果レコードなどのプロパティは、タグブロック内で使用できる[entityview オブジェクト](liquid-objects.md#entityview)を使用してアクセスできます。  

ビューが正常に読み込まれると、ブロック内のコンテンツがレンダリングされます。 ビューが見つからない場合、ブロックコンテンツはレンダリングされません。

```
{% entityview logical_name:'contact', name:"Active Contacts" %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

既定では、entityview オブジェクトには entityview という変数名が割り当てられます。 必要に応じて、別の変数名を指定することもできます。

```
{% entityview my_view = logical_name:'contact', name:"Active Contacts" %}

Loaded entity view with {{ my_view.total_records }} total records.

{% endentityview %}
```

Entityview が entityview ブロック内で入れ子になっている場合は、エンティティリストから既定の構成 (結果ページサイズ、フィルターオプションなど) が継承されます。 Entityview にビュー id または name パラメーターが指定されていない場合は、それを囲む entityview から既定のビューが読み込まれます。

```
{% entitylist id:page.adx_entitylist.id %}

{% entityview %}

Loaded default view of the entity list associated with the current page, with {{ entityview.total_records }} total records.

{% endentityview %}

{% endentitylist %}
```

### <a name="parameters"></a>パラメーター

読み込む PowerApps ビューを選択するには **、id** **または**論理\_名を指定します。 どちらも指定されておらず、entityview タグが entityview タグ内に入れ子になっている場合は、それを囲む entityview の既定のビューが読み込まれます。

**番号**

id は、GUID として解析できる文字列である必要があります。

```
{% entityview id:936DA01F-9ABD-4d9d-80C7-02AF85C822A8 %}

Loaded entity view {{ entityview.name }}.

{% endentityview %}
```

一般に、リテラル GUID 文字列は使用されません。 代わりに、別の変数の GUID プロパティを使用して id が指定されます。

```
{% entityview id:request.params.view %}

Loaded entity view {{ entityview.name }} using view query string request parameter.

{% endentityview %}
```

**論理\_名**

読み込むビューの PowerApps エンティティ論理名。 Name と組み合わせて使用する必要があります。

```
{% entityview logical_name:'contact', name:"Active Contacts" %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

**指定**

読み込むビューの PowerApps 名。 論理\_名と組み合わせて使用する必要があります。

```
{% entityview logical_name:'contact', name:"Active Contacts" %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

**フィルター**

ユーザーまたはアカウントで表示結果をフィルター処理するかどうかを指定します。 ユーザーまたはアカウントの文字列値を持つ必要があります。

```
{% entityview id:request.params.view, filter:'user' %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

一般的なユースケースでは、[要求](liquid-objects.md#request)に基づいてこのパラメーターを設定します。  

```
{% entityview id:request.params.view, filter:request.params.filter %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

**メタフィルター**

ビューの結果をフィルター処理するために使用するエンティティリストメタデータフィルター式を指定します。 このパラメーターは、entityview が entityview と組み合わせて使用されている場合にのみ有効です。 ほとんどの場合、このパラメーターは[要求](liquid-objects.md#request)に基づいて設定されます。  

```
{% entitylist id:page.adx_entitylist.id %}

{% entityview id:request.params.view, metafilter:request.params.mf %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}

{% endentitylist %}
```

**順序**

ビューの結果を並べ替えるための並べ替え式を指定します。 並べ替え式には、1つまたは複数のエンティティ属性の論理名と、その後に ASC または DESC の並べ替え方向を含めることができます。

```
{% entityview id:request.params.view, order:'name ASC, createdon DESC' %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

一般的なユースケースでは、[要求](liquid-objects.md#request)に基づいてこのパラメーターを設定します。  

```
{% entityview id:request.params.view, order:request.params.order %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

**改**

読み込むビューの結果ページを指定します。 このパラメーターを指定しない場合、結果の最初のページが読み込まれます。

このパラメーターには、整数値か、または整数として解析できる文字列を渡す必要があります。 このパラメーターに値が指定されているが、値が null であるか、または整数として解析できない場合は、結果の最初のページが読み込まれます。

```
{% entityview id:request.params.view, page:2 %}

Loaded page {{ entityview.page }} of entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

一般的なユースケースでは、[要求](liquid-objects.md#request)に基づいてこのパラメーターを設定します。  

```
{% entityview id:request.params.view, page:request.params.page %}

Loaded page {{ entityview.page }} of entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

**ページ\_サイズ**

現在の結果ページに読み込む結果の数を指定します。 このパラメーターに値が指定されておらず、entityview が[entityview](#entitylist)ブロック内で使用されている場合は、エンティティリストページのサイズが使用されます。 Entitylist ブロック内に存在しない場合は、既定値の10が使用されます。

このパラメーターには、整数値か、または整数として解析できる文字列を渡す必要があります。 このパラメーターに値が指定されていても、値が null であるか、または整数として解析できない場合は、既定のページサイズが使用されます。

```
{% entityview id:request.params.view, page_size:20 %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

一般的なユースケースでは、[要求](liquid-objects.md#request)に基づいてこのパラメーターを設定します。  

```
{% entityview id:request.params.view, page_size:request.params.pagesize %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

**サーチ**

ビューの結果をフィルター処理するために使用する検索式を指定します。 単純なキーワード検索式では、属性がキーワードで始まるかどうかによってフィルター処理が行われます。 ワイルドカード \* を式に含めることもできます。

```
{% entityview id:request.params.view, search:'John\*' %}

Loaded entity view with {{ entityview.total_records }} total matching records.

{% endentityview %}
```

一般的なユースケースでは、ユーザー入力に基づいて検索フィルターを設定できるように、[要求](liquid-objects.md#request)に基づいてこのパラメーターを設定します。  
```
{% entityview id:request.params.view, search:request.params.search %}

Loaded entity view with {{ entityview.total_records }} total matching records.

{% endentityview %}
```

**\_エンティティ\_アクセス許可を有効にする**

ビューの結果にエンティティ権限フィルターを適用するかどうかを指定します。 既定では、このパラメーターは false に設定されています。 Entityview が entityview ブロック内で使用されている場合、このパラメーターの値はエンティティリストの構成から継承されます。

このパラメーターは、[ブール](liquid-types.md#boolean)値またはブール値として解析できる文字列 (true、false) のいずれかに渡す必要があります。 このパラメーターに値が指定されていても、値が null であるか、またはブール型として解析できない場合は、既定値の false が使用されます。  

```
{% entityview id:request.params.view, enable_entity_permissions:true %}

Loaded entity view with {{ entityview.total_records }} total records to which the user has read permission.

{% endentityview %}
```

**言語\_コード**

読み込まれるエンティティビューのローカライズされたラベル (列ヘッダーラベルなど) を選択するための PowerApps 整数言語コード。 言語\_コードが指定されていない場合は、ポータルアプリケーション PowerApps 接続の既定の言語が使用されます。

Entityview が entityview ブロック内で使用されている場合、entityview は entityview からその言語コードの構成を継承します。

```
{% entityview logical_name:'contact', name:"Active Contacts", language_code:1033 %}

Loaded entity view {{ entityview.name }}.

{% endentitylist %}
```

## <a name="searchindex"></a>searchindex

ポータルの検索インデックスに対してクエリを実行します。 その後、照合結果には、タグブロック内で使用できる[searchindex](liquid-objects.md#searchindex)を使用してアクセスできます。  

```
{% searchindex query: 'support', page: params.page, page_size: 10 %}

{% if searchindex.results.size > 0 %}

<p>Found about {{ searchindex.approximate_total_hits }} matches:</p>

<ul>

{% for result in searchindex.results %}

<li>

<h3><a href={{ result.url | escape }}>{{ result.title | escape }}</a></h3>

<p>{{ result.fragment }}</p>

</li>

{% endfor %}

</ul>

{% else %}

<p>Your query returned no results.</p>

{% endif %}

{% endsearchindex %}
```

既定では、検索インデックスオブジェクトには、変数名 searchindex が指定されます。 必要に応じて、別の変数名を指定することもできます。

```
{% searchindex liquid_search = query: 'support', page: params.page, page_size: 10 %}

{% if liquid_search.results.size > 0 %}

...

{% endif %}

{% endsearchindex %}
```

### <a name="parameters"></a>パラメーター

Searchindex タグは、次のパラメーターを受け入れます。

**照会**

結果を照合するために使用されるクエリ。 このパラメーターは、インデックスクエリのユーザー指定の部分 (存在する場合) を受け入れることを目的としています。

```
{% searchindex query: 'support' %}

...

{% endsearchindex %}
```

一般的なユースケースでは、[要求](liquid-objects.md#request)に基づいてこのパラメーターを設定します。  

```
{% searchindex query: request.params.query %}

...

{% endsearchindex %}
```

このパラメーター[は、Lucene クエリパーサー構文を](https://lucene.apache.org/core/2_9_4/queryparsersyntax.html)サポートしています。

**フィルター**

結果の照合に使用される追加のクエリ。 このパラメーターは、必要に応じて、開発者が指定した結果のフィルターを受け入れることを目的としています。

```
{% searchindex query: request.params.query, filter: '+statecode:0' %}

...

{% endsearchindex %}
```

このパラメーター[は、Lucene クエリパーサー構文を](https://lucene.apache.org/core/2_9_4/queryparsersyntax.html)サポートしています。  

> [!Note]     
> フィルターとクエリの違いは、どちらも Lucene クエリパーサーの構文を受け入れるが、ほとんどのエンドユーザーがこの構文を認識しないと想定されているように、この構文がどのように解析されるかをߝにすることを目的としています。 このため、この構文に基づくクエリの解析が失敗した場合、クエリ全体がエスケープされ、クエリテキストとして送信されます。 一方、フィルターは厳密に解析され、無効な構文の場合はエラーを返します。

**論理\_名**

一致する結果が制限される PowerApps エンティティの論理名を、コンマ区切りの文字列として指定します。 指定しない場合は、一致するすべてのエンティティが返されます。

```
{% searchindex query: request.params.query, logical_names: 'kbarticle,incident' %}

...
>
{% endsearchindex %}
```
**改**

返される検索結果ページ。 指定しない場合、最初のページ (1) が返されます。

```
{% searchindex query: request.params.query, page: 2 %}

...

{% endsearchindex %}
```

一般的なユースケースでは、[要求](liquid-objects.md#request)に基づいてこのパラメーターを設定します。  

```
{% searchindex query: request.params.query, page: request.params.page %}

...

{% endsearchindex %}
```

**ページ\_サイズ**

返される結果ページのサイズ。 指定しない場合、既定のサイズの10が使用されます。

```
{% searchindex query: request.params.query, page_size: 20 %}

...

{% endsearchindex %}
```

## <a name="entityform"></a>entityform

PowerApps で構成されたエンティティフォームを名前または ID で完全にレンダリングします。  

> [!Note]
> Entityform タグは、  <em>[web テンプレート](store-content-web-templates.md)</em>ベースのページテンプレート内でレンダリングされるコンテンツでのみ使用できます。 リライトベースのページテンプレート内でタグを使用しようとしても、何も表示されません。 1ページにつき1つの entityform または web フォームタグのみを表示できます。 最初のエンティティフォームまたは web フォームタグはレンダリングされません。       

`{% entityform name: 'My Entity Form' %}`

### <a name="parameters"></a>パラメーター

**指定**

読み込みたいエンティティフォームの名前。

`{% entityform name:My Entity Form %}`

### <a name="webform"></a>**webform**

PowerApps で構成された web フォームを名前または ID で完全にレンダリングします。 Web フォームタグは、 [web テンプレート](store-content-web-templates.md)ベースのページテンプレート内でレンダリングされるコンテンツでのみ使用できます。 リライトベースのページテンプレート内でタグを使用しようとしても、何も表示されません。 1ページにつき1つの entityform または web フォームタグのみを表示できます。 最初のエンティティフォームまたは web フォームタグはレンダリングされません。                
`{% webform name: 'My Web Form' %}`

### <a name="parameters"></a>パラメーター

**指定**

読み込みたい Web フォームの名前。

`{% webform name:My Web Form %}`

### <a name="see-also"></a>関連項目

[制御フロータグ](control-flow-tags.md)<br>
[イテレーションタグ](iteration-tags.md)<br>
[可変タグ](variable-tags.md)<br>
[テンプレートタグ](template-tags.md)
