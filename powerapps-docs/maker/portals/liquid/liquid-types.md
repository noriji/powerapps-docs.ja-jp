---
title: ポータルの Liquid の種類を使用する | MicrosoftDocs
description: ポータルで使用可能な Liquid の種類について説明します。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: null
ms.date: 08/30/2019
ms.author: shjais
ms.reviewer: null
---

# <a name="available-liquid-types"></a>使用可能な Liquid の種類

流動オブジェクトは、7 つの基本的な種類のうち 1 つを返します。**文字列**、**数値**、**ブール値**、**配列**、**辞書**、**日時**、および **Null** があります。 流動変数は、**assign** タグ (割り当て) または **capture** (取得) タグで初期化できます。

## <a name="string"></a>文字列

文字列は、単一引用符または二重引用符でテキストを囲むことで宣言します。

```
{% assign string_a = Hello World! %}

{% assign string_b = 'Single quotes work too.' %}
```

サイズ プロパティを使用して、文字列の文字数を取得します。

```
{{ string_a.size }} <!-- Output: 12 -->
```

## <a name="number"></a>数値

[数値] は、整数または小数を指定できます。

```
{% assign pi = 3.14 %}

{% if page.title.size > 100 %}

This page has a long title.

{% endif %}
```

## <a name="boolean"></a>ブール値

ブール値は、true または false のいずれかになります。

```
{% assign x = true %}

{% assign y = false %}

{% if x %}

This will be rendered, because x is true.

{% endif %}
```

## <a name="array"></a>配列

配列は、任意の種類の値のリストを保持します。 \[ \] を使用した (ゼロ ベースの) インデックスによる特定の項目へのアクセス、**for タグ**を使用した反復処理、およびサイズ プロパティを使用した配列内の項目数の取得が可能です。

```
{% for view in entitylist.views %}

{{ view.name }}

{% endfor %}

{{ entitylist.views[0] }}

{% if entitylist.views.size > 0 %}

This entity list has {{ entitylist.views.size }} views.

{% endif %}
```

## <a name="dictionary"></a>辞書

辞書は、文字列キーでアクセスできる値の集合を保持します。 \[ \] を使用した文字列キーによる特定の項目へのアクセスや、**for タグ**を使用した反復処理、およびサイズ プロパティを使用した辞書内の項目数の取得が可能です。

```
{{ request.params[ID] }}

{% if request.params.size > 0 %}

The request parameters collection contains some items.

{% endif %}
```

## <a name="datetime"></a>日時

DateTime オブジェクトは、特定の日時を表します。

```
{{ page.modifiedon | date: 'f' }}
```

## <a name="null"></a>Null

Null は空または存在しない値を表します。 null 値を返す場合、出力には何も表示されません。 条件の中で、これは false として処理されます。

```
{% if request.params[ID] %}

This will render if the ID request parameter is NOT null.

{% endif %}
```

### <a name="see-also"></a>関連項目

[Web テンプレートを使用したソース コンテンツの保存](store-content-web-templates.md)  
[Liquid の演算子の認識](liquid-operators.md)  
[条件](liquid-conditional-operators.md)  
[Liquid オブジェクト](liquid-objects.md)  
[Liquid タグ](liquid-tags.md)  
[Liquid フィルター](liquid-filters.md)  