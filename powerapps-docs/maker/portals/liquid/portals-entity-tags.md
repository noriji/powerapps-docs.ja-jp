---
title: ポータルの PowerApps Common Data Service エンティティ タグを使用する | MicrosoftDocs
description: ポータルで使用可能な PowerApps Common Data Service エンティティ タグについて説明します。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: null
ms.date: 08/30/2019
ms.author: shjais
ms.reviewer: null
---

# <a name="powerapps-common-data-service-entity-tags"></a>PowerApps Common Data Service エンティティ タグ

PowerApps エンティティ タグを PowerApps データの読み込みおよび表示のために使用するか、または他の PowerApps ポータル フレームワーク サービスを使用します。 これらのタグは、流動言語に対する PowerApps 固有の拡張機能です。

## <a name="chart"></a>グラフ

Web ページに PowerApps グラフを追加します。 グラフ タグは、Web ページの [コピー] フィールドまたは Web テンプレートの [ソース] フィールドに追加できます。 PowerApps グラフを Web ページに追加する手順については、[ポータルでグラフを Web ページに追加する](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/portals/add-chart) を参照してください。

```
{% chart id:"EE3C733D-5693-DE11-97D4-00155DA3B01E" viewid:"00000000-0000-0000-00AA-000010001006" %}
```

### <a name="parameters"></a>パラメーター

グラフ タグには、グラフ id と viewid という 2 つのパラメーターがあります。

**グラフ ID**

グラフのビジュアル化 ID です。 グラフをエクスポートしてこれを取得できます。

**viewid**

ビュー エディターで開いたときのエンティティの ID。 

## <a name="powerbi"></a>PowerBI

Power BI ダッシュボードおよびページ内レポートを追加する タグは、Web ページの**コピー**フィールドまたは Web テンプレートの**ソース**フィールドに追加できます。 ポータル内のwebページに Power BI レポートまたはダッシュボードを追加する手順については、 [ポータル内のwebページに Power BI レポートまたはダッシュボードを追加](../admin/add-powerbi-report.md)を参照してください。

> [!NOTE]
> タグを機能させるには、ポータル アドミン センターにて[ Power BI の統合を有効化](../admin/set-up-power-bi-integration.md) する必要があります。 Power BI の統合が有効化されていない場合は、ダッシュボードまたはレポートは表示されません。

### <a name="parameters"></a>パラメーター

PowerBI タグは、次のパラメーターを受け取ります:

**path**

Power BI レポートまたはダッシュボードのパス。 Power BI レポートまたは、ダッシュボードが安全な場合、認証タイプを指定する必要があります。

```
{% powerbi path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000001/ReportSection01" %}
```

**認証の種類**

Power BI レポートまたはダッシュボードに必要な認証のタイプ。 このパラメーターで有効な値は下記です:

- **アノニマス**: Web Power BI レポートに公開処理を埋め込むことができます。 既定の認証の種類は匿名です。

- **AAD**: 安全な Power BI レポートまたはダッシュボードを Power BI Azure Active Directory  認証済みユーザーと共有することができます。

- **powerbiembedded**: Power BI 安全なレポートまたはダッシュボードを Power BI ライセンスまたは Azure Active Directory 認証設定を持っていない外部ユーザーと共有できます。 Power BI Embedded サービス設定に関する情報については、 [ Power BI Embedded サービスを有効にする](../admin/set-up-power-bi-integration.md#enable-power-bi-embedded-service)を参照してください。 

安全な Power BI レポートまたはダッシュボードを追加する際は、それらが Dynamics 365 ポータル Azure Active Directory または Power BI Embedded サービスと共有されていることを確認します。 

> [!NOTE]
> `authentication_type` パラメータの値は大文字と小文字を区別しません。

```
{% powerbi authentication_type:"AAD" path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000001/ReportSection01" %}
```

1 つまたは複数の値でレポートにフィルターを適用することもできます。 レポートのフィルター処理の構文は次のとおりです。

URL?filter=**Table**/**Field** eq '**value**'

たとえば、Bert Hair という名前の取引先担当者のデータが表示されるようにレポートをフィルター処理するとします。 URL に以下を追加する必要があります。

?filter=Executives/Executive eq 'Bert Hair'

完全なコードは次のとおりです。

```
{% powerbi authentication_type:"AAD" path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000001/ReportSection01?filter=Executives/Executive eq 'Bert Hair'" %}
```

レポートのフィルター処理の詳細: [URL でクエリ文字列パラメーターを使用してレポートをフィルター処理する](https://docs.microsoft.com/en-us/power-bi/service-url-filters)

> [!NOTE]
> 匿名レポートは、フィルター処理をサポートしていません。 

以下のように `capture ` Liquid 変数を使用して動的パスを作成することもできます。

```
{% capture pbi_path %}https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000001/ReportSection01?filter=Executives/Executive eq '{{user.id}}'{% endcapture %}
{% powerbi authentication_type:"AAD" path:pbi_path %}
```

Liquid 変数の詳細: [変数タグ](variable-tags.md)

**tileid**

ダッシュボードの指定タイルが表示されます。 タイルの ID を設定してください。

```
{% powerbi authentication_type:"AAD" path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/dashboards/00000000-0000-0000-0000-000000000001" tileid:"00000000-0000-0000-0000-000000000002" %}
```

**roles**

Power BI レポートに割り当てられた役割 このパラメータが有効になるのは、 **authentication_type** パラメータが **powerbiembedded**に設定されている場合のみです。

Power BI にて役割を定義し、レポートに割り当てている場合は、 **powerbi** Liquidタグで適切な役割を指定する必要があります。 ロールを使用すると、レポートに表示するデータをフィルタすることができます。 セミコロンで区切った複数の役割を指定することができます。 Power BIにおける役割の定義に関する詳細情報については、 [ Power BIの行レベルセキュリティ (RLS)](https://docs.microsoft.com/en-us/power-bi/service-admin-rls) を参照してください。

```
{% powerbi authentication_type:"powerbiembedded" path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000000/ReportSection2" roles:"Region_East,Region_West" %}
```

Power BI レポートに役割を割り当てていても、Liquidタグで  **roles** パラメータを指定しなかった場合、またはパラメータで役割を指定しなかった場合には、エラーが表示されます。

> [!TIP]
> ポータルで定義されたWeb役割を Power BI 役割として使用する場合は、変数を定義してWebの役割を割り当てることができます。 その後、Liquidタグで定義された変数を使用することができます。
>
> たとえば、ポータルで Region_East と Region_West という2つのWebの役割を定義した場合、 次のコードを使用して結合することができます:  `{% assign webroles = user.roles | join: ", " %}`
>
> 上記のコード スニペットでは、 `webroles` が変数となり、そこにRegion_EastとRegion_WestのWebロールが格納されます。
>
> `webroles` 変数をLiquidタグにて次のように使用します:
>
> `{% powerbi authentication_type:"powerbiembedded" path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000000/ReportSection2" roles:webroles%}`

## <a name="editable"></a>編集可能

取得した、ポータルで編集可能なものとしての PowerApps ポータル CMS オブジェクトを、そのオブジェクトのコンテンツ編集権限を持つユーザーに対して表示します。 編集可能なオブジェクトとして [ページ](liquid-objects.md#page)、[スニペット](liquid-objects.md#snippets)、および [Web リンク](liquid-objects.md#weblinks) があります。  

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

編集可能に表示される最初のパラメーターは、編集可能なオブジェクトです。 たとえば、これは、Web リンク セット、スニペット、または現在のページの場合があります。 オプションの 2 番目のパラメーターでは、属性名や、表示および編集されるこのオブジェクト内のキーを指定します。 たとえば、これは、エンティティ属性の名前、またはスニペットの名前の場合があります。

これらの最初のパラメーターの後では、タグは多数の名前の付けられたオプションのパラメーターをサポートします。

**クラス**

このタグによって表示されるルート要素のクラス属性値を指定します。

**既定**

編集可能アイテムに値がないサポート案件に表示される既定値。

**エスケープ**

このタグによって表示される値がエンコードされた HTML かどうかを指定するブール値。 これは既定で false です。

**liquid**

このタグによって表示されるテキスト値内で見つかった流動テンプレート コードを処理するかどうか指定するブール値。 これは既定で true です。

**タグ**

このタグによって表示される container HTML タグの名前です。 このタグは、既定で div 要素です。 一般的には、このパラメーターの値として、div または span を選択することをお勧めします。

**タイトル**

コンテンツ編集インターフェイス内でこの編集可能アイテムのラベルを指定します。 何も指定されていない場合は、わかりやすいラベルが自動的に生成されます。

**タイプ**

編集可能なテキスト値のために提供された、編集インターフェイスの種類を表す文字列値です。 このパラメーターの有効な値は html または text です。 既定値は html です。

## <a name="entitylist"></a>エンティティリスト

特定のエンティティ リストを名前または ID により読み込みます。 タグ ブロック内で使用できる [entitylist オブジェクト](liquid-objects.md#entitylist)を使用して、エンティティ リストのプロパティにアクセスすることができるようになります。 エンティティ リストの実績結果レコードを表示するには、ブロック内で [entityview](#entityview) タグを使用します。  

エンティティ リストが正常に読み込まれると、ブロック内のコンテンツが表示されます。 エンティティ リストが見つからないと、ブロック コンテンツは表示されません。

```
{% entitylist name:My Entity List %}

Loaded entity list {{ entitylist.adx_name }}.

{% endentitylist %}
```
既定では、エンティティリスト オブジェクトには、変数名「エンティティリスト」が与えられます。 必要に応じて、別の変数名を与えることができます。

```
{% entitylist my_list = name:My Entity List %}

Loaded entity list {{ my_list.adx_name }}.

{% endentitylist %}
```

### <a name="parameters"></a>パラメーター

読み込むエンティティ リストを選択するには id、名前、またはキーのうちの **1 つのみ**を入力します。

**ID**

[GUID](http://en.wikipedia.org/wiki/Globally_unique_identifier) ID によってエンティティ リストを読み込みます。 ID は、GUID として解析できる文字列である必要があります。  

```
{% entitylist id:936DA01F-9ABD-4d9d-80C7-02AF85C822A8 %}

Loaded entity list {{ entitylist.adx_name }}.

{% endentitylist %}
```

通常、リテラル GUID 文字列は使用されません。 代わりに ID が、他の変数の GUID プロパティを使用して指定されます。

```
{% entitylist id:page.adx_entitylist.id %}

Loaded entity list {{ entitylist.adx_name }}.

{% endentitylist %}
```

**名前**

名前によってエンティティ リストを読み込みます。

```
{% entitylist name:My Entity List %}

Loaded entity list {{ entitylist.adx_name }}.

{% endentitylist %}
```

**キー**

ID **または** 名前によってエンティティ リストを読み込みます。 提供されたキー値が [GUID](http://en.wikipedia.org/wiki/Globally_unique_identifier) として解析できる場合、エンティティ リストは ID によって読み込まれます。 それ以外の場合は、名前によって読み込まれます。

```
<!-- key_variable can hold an ID or name -->

{% entitylist key:key_variable %}

Loaded entity list {{ entitylist.adx_name }}.

{% endentitylist %}
```

**language\_code**

読み込まれるためにラベルがローカライズされたエンティティ リストを選択するための PowerApps 整数言語コード。 language\_code が指定されていない場合は、ポータル アプリケーション PowerApps 接続の既定の言語が使用されます。

```
{% entitylist name:"My Entity List", language_code:1033 %}

Loaded entity list {{ entitylist.adx_name }}.

{% endentitylist %}
```

## <a name="entityview"></a>エンティティビュー

特定の PowerApps ビューを名前または ID により読み込みます。 ビュー列メタデータのプロパティ、ページ付けされた結果レコードなどは、タグ ブロック内で使用可能な [entityview オブジェクト](liquid-objects.md#entityview)を使用してアクセスすることができます。  

ビューが正常に読み込まれると、ブロック内のコンテンツが表示されます。 ビューが見つからないと、ブロック コンテンツは表示されません。

```
{% entityview logical_name:'contact', name:"Active Contacts" %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

既定では、エンティティビュー オブジェクトには、変数名「エンティティビュー」が与えられます。 必要に応じて、別の変数名を与えることができます。

```
{% entityview my_view = logical_name:'contact', name:"Active Contacts" %}

Loaded entity view with {{ my_view.total_records }} total records.

{% endentityview %}
```

エンティティビューがエンティティリスト ブロック内でネストされる場合、既定の構成 (結果ページ サイズ、フィルター オプション、など) がエンティティの一覧から継承されます。 ID または名前パラメーターのビューがエンティティビューに提供されていない場合、囲まれているエンティティリストから既定のビューが読み込まれます。

```
{% entitylist id:page.adx_entitylist.id %}

{% entityview %}

Loaded default view of the entity list associated with the current page, with {{ entityview.total_records }} total records.

{% endentityview %}

{% endentitylist %}
```

### <a name="parameters"></a>パラメーター

ID **または** logical\_name の**いずれか**に名前を提供し、読み込む PowerApps ビューを選択します。 いずれも入力しない場合、または entityview タグが entitylist タグ内でネストされている場合は、囲まれた entitylist の既定のビューが読み込まれます。

**ID**

ID は、GUID として解析できる文字列である必要があります。

```
{% entityview id:936DA01F-9ABD-4d9d-80C7-02AF85C822A8 %}

Loaded entity view {{ entityview.name }}.

{% endentityview %}
```

通常、リテラル GUID 文字列は使用されません。 代わりに ID が、他の変数の GUID プロパティを使用して指定されます。

```
{% entityview id:request.params.view %}

Loaded entity view {{ entityview.name }} using view query string request parameter.

{% endentityview %}
```

**logical\_name**

読み込むためのビューの PowerApps エンティティの論理名。 名前と連携して使用する必要があります。

```
{% entityview logical_name:'contact', name:"Active Contacts" %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

**名前**

読み込むためのビューの PowerApps 名。 logical\_name と連携して使用する必要があります。

```
{% entityview logical_name:'contact', name:"Active Contacts" %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

**フィルター**

ビューの結果にユーザーまたはアカウントごとにフィルター処理するかどうかを指定します。 user または account の文字列値を持つ必要があります。

```
{% entityview id:request.params.view, filter:'user' %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

一般的な使用事例は、[リクエスト](liquid-objects.md#request)に基づいてこのパラメーターを設定することです。  

```
{% entityview id:request.params.view, filter:request.params.filter %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

**メタフィルター**

ビューの結果をフィルター処理することによって、エンティティ リストの metadata のフィルター式を指定します。 このパラメーターは、エンティティビューがエンティティリストに連係して使用される場合にのみ有効です。 通常、このパラメーターは、[リクエスト](liquid-objects.md#request)に基づいて設定されます。  

```
{% entitylist id:page.adx_entitylist.id %}

{% entityview id:request.params.view, metafilter:request.params.mf %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}

{% endentitylist %}
```

**オーダー**

ビューの結果を並べ替えるための並べ替え式を指定します。 並べ替え式には、後に ASC または DESC が続く、エンティティの属性の論理名を 1 つ以上含むことができます。

```
{% entityview id:request.params.view, order:'name ASC, createdon DESC' %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

一般的な使用事例は、[リクエスト](liquid-objects.md#request)に基づいてこのパラメーターを設定することです。  

```
{% entityview id:request.params.view, order:request.params.order %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

**ページ**

読み込むビューの結果ページを指定します。 このパラメーターを指定しない場合は、結果の最初のページが読み込まれます。

このパラメータは、整数値、または整数として解析できる文字列を渡される必要があります。 このパラメーターに値が入力されましたが、その値が null 、または整数として解析できないその他の値の場合、結果の最初のページが読み込まれます。

```
{% entityview id:request.params.view, page:2 %}

Loaded page {{ entityview.page }} of entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

一般的な使用事例は、[リクエスト](liquid-objects.md#request)に基づいてこのパラメーターを設定することです。  

```
{% entityview id:request.params.view, page:request.params.page %}

Loaded page {{ entityview.page }} of entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

**page\_size**

現在の結果ページに読み込む結果の数を指定します。 このパラメータに値が指定されず、[entitylist](#entitylist) ブロック内で entityview が使用されている場合、エンティティ リスト ページ サイズが使用されます。 エンティティリスト ブロック内に存在しない場合、10 の既定値を使用します。

このパラメータは、整数値、または整数として解析できる文字列を渡される必要があります。 このパラメーターに値が入力されましたが、その値が null 、または整数として解析できないその他の値の場合、既定のページ サイズが使用されます。

```
{% entityview id:request.params.view, page_size:20 %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

一般的な使用事例は、[リクエスト](liquid-objects.md#request)に基づいてこのパラメーターを設定することです。  

```
{% entityview id:request.params.view, page_size:request.params.pagesize %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

**検索**

ビューの結果をフィルター処理することによって、検索式を指定します。 単純なキーワード検索式は、キーワードで始まる属性かどうかによってフィルター処理されます。 ワイルドカード\*も式に含めることができます。

```
{% entityview id:request.params.view, search:'John\*' %}

Loaded entity view with {{ entityview.total_records }} total matching records.

{% endentityview %}
```

一般的には、[リクエスト](liquid-objects.md#request)に基づいて、このパラメーターを設定するために使用されます。それにより、検索フィルターをユーザーの入力に基づいて設定することができます。  
```
{% entityview id:request.params.view, search:request.params.search %}

Loaded entity view with {{ entityview.total_records }} total matching records.

{% endentityview %}
```

**enable\_entity\_permissions**

ビューの結果をフィルター処理するエンティティ権限を適用するかどうかを指定します。 既定では、この値は false に設定されています。 エンティティビューがエンティティリスト ブロック内で使用されている場合、このパラメーターの値は、エンティティ リスト構成から継承されます。

このパラメーターは、[boolean](liquid-types.md#boolean) 値、またはブール値 (true または false) として解析できる文字列のいずれかが渡される必要があります。 このパラメーターに値が入力されましたが、その値が null、またはブール値として解析できないその他の値の場合、既定の false が使用されます。  

```
{% entityview id:request.params.view, enable_entity_permissions:true %}

Loaded entity view with {{ entityview.total_records }} total records to which the user has read permission.

{% endentityview %}
```

**language\_code**

読み込むためのエンティティ ビューのローカライズされたラベル (列見出しラベルなど) を選択するための PowerApps 整数言語コード。 language\_code が指定されていない場合は、ポータル アプリケーション PowerApps 接続の既定の言語が使用されます。

エンティティビューがエンティティリスト ブロック内で使用されている場合、このパラメーターの値は、エンティティリストの構成から継承されます。

```
{% entityview logical_name:'contact', name:"Active Contacts", language_code:1033 %}

Loaded entity view {{ entityview.name }}.

{% endentitylist %}
```

## <a name="searchindex"></a>検索インデックス

ポータル検索インデックスに対してクエリを実行します。 一致の結果は、タグ ブロック内で使用可能な [searchindex](liquid-objects.md#searchindex) を使用してアクセスすることができます。  

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

既定では、検索インデックス オブジェクトには、変数名「検索インデックス」が与えられます。 必要に応じて、別の変数名を与えることができます。

```
{% searchindex liquid_search = query: 'support', page: params.page, page_size: 10 %}

{% if liquid_search.results.size > 0 %}

...

{% endif %}

{% endsearchindex %}
```

### <a name="parameters"></a>パラメーター

検索インデックス タグは、次のパラメーターを受け取ります。

**クエリ**

結果に一致させるために使用するクエリ。 このパラメーターの目的は、インデックス クエリのユーザー指定部分を受け取ることです (ある場合)。

```
{% searchindex query: 'support' %}

...

{% endsearchindex %}
```

一般的な使用事例は、[リクエスト](liquid-objects.md#request)に基づいてこのパラメーターを設定することです。  

```
{% searchindex query: request.params.query %}

...

{% endsearchindex %}
```

このパラメーターは、[Lucene クエリ パーサー構文](http://lucene.apache.org/core/2_9_4/queryparsersyntax.html)をサポートします。

**フィルター**

結果に一致させるために追加で使用するクエリ。 このパラメーターの目的は、必要に応じて、開発者が指定した結果のためのフィルターを受け取ることです。

```
{% searchindex query: request.params.query, filter: '+statecode:0' %}

...

{% endsearchindex %}
```

このパラメーターは、[Lucene クエリ パーサー構文](http://lucene.apache.org/core/2_9_4/queryparsersyntax.html)をサポートします。  

> [!Note]     
> フィルターとクエリの違いは、どちらも Lucene クエリ パーサー構文を受け取りますが、クエリの目的が、ߝ ほとんどのエンド ユーザーがこの構文を注意していないことが予想されるときに、この構文が解析される方法についてより寛容であることです。 そのため、この構文の失敗に基づいてクエリを解析した場合、すべてのクエリは、クエリ テキストとしてエスケープされ、送信されます。 一方 filter では、無効な構文の場合には厳しく分析され、エラーが返ります。

**logical\_names**

結果と一致する PowerApps エンティティの論理名は、コンマ区切り文字列として制限されます。 指定しない場合は、すべての一致するエンティティが返されます。

```
{% searchindex query: request.params.query, logical_names: 'kbarticle,incident' %}

...
>
{% endsearchindex %}
```
**ページ**

返される検索結果ページ。 指定しない場合は、最初のページ (1) が返されます。

```
{% searchindex query: request.params.query, page: 2 %}

...

{% endsearchindex %}
```

一般的な使用事例は、[リクエスト](liquid-objects.md#request)に基づいてこのパラメーターを設定することです。  

```
{% searchindex query: request.params.query, page: request.params.page %}

...

{% endsearchindex %}
```

**page\_size**

返される結果ページのサイズ。 指定しない場合は、既定のサイズ 10 が使用されます。

```
{% searchindex query: request.params.query, page_size: 20 %}

...

{% endsearchindex %}
```

## <a name="entityform"></a>entityform

名前または ID により、PowerApps の構成済みエンティティ フォームを完全に表示します。  

> [!Note]
> エンティティフォーム タグは、ページ テンプレートに基づく <em>[Web テンプレート](store-content-web-templates.md)–</em> 内に表示されたコンテンツでのみ使用できます。 リライト ベース ページ テンプレート内のタグを使用しているときは、何も表示されません。 1 ページに表示できるのは、1 つのエンティティフォームまたは Web フォーム タグだけです。 2 番目のエンティティフォームまたは Web フォームは表示されません。       

`{% entityform name: 'My Entity Form' %}`

### <a name="parameters"></a>パラメーター

**名前**

読み込むエンティティ フォームの名前。

`{% entityform name:My Entity Form %}`

### <a name="webform"></a>**Web フォーム**

名前または ID により、Web フォームの PowerApps 構成をすべて表示します。 Web フォーム タグは、ページ テンプレートに基づく [Web テンプレート](store-content-web-templates.md)内に表示されたコンテンツでのみ使用することができます。 リライト ベース ページ テンプレート内のタグを使用しているときは、何も表示されません。 1 ページに表示できるのは、1 つのエンティティフォームまたは Web フォーム タグだけです。 2 番目のエンティティフォームまたは Web フォームは表示されません。                
`{% webform name: 'My Web Form' %}`

### <a name="parameters"></a>パラメーター

**名前**

読み込む Web フォームの名前。

`{% webform name:My Web Form %}`

### <a name="see-also"></a>関連項目

[制御フロー タグ](control-flow-tags.md)<br>
[反復タグ](iteration-tags.md)<br>
[変数タグ](variable-tags.md)<br>
[テンプレート タグ](template-tags.md)
