---
title: ポータルに液体の種類を使用する |MicrosoftDocs
description: ポータルで使用できる液体の種類について説明します。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: dd6da4788f6563c2026f57914c8156caedfadad3
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/11/2019
ms.locfileid: "72974945"
---
# <a name="available-liquid-types"></a>使用可能な液体の種類

液体オブジェクトは、 **String**、 **Number**、 **Boolean**、 **Array**、 **Dictionary**、 **DateTime**、または**Null**の7つの基本型のいずれかを返すことができます。 液体変数は、 **assign**タグまたは**capture**タグを使用して初期化できます。

## <a name="string"></a>String

文字列は、テキストを単一引用符または二重引用符で囲むことによって宣言されます。

```
{% assign string_a = Hello World! %}

{% assign string_b = 'Single quotes work too.' %}
```

Size プロパティを使用して、文字列内の文字数を取得します。

```
{{ string_a.size }} <!-- Output: 12 -->
```

## <a name="number"></a>Number

整数または浮動小数点数を使用できます。

```
{% assign pi = 3.14 %}

{% if page.title.size > 100 %}

This page has a long title.

{% endif %}
```

## <a name="boolean"></a>Boolean

ブール値は true または false です。

```
{% assign x = true %}

{% assign y = false %}

{% if x %}

This will be rendered, because x is true.

{% endif %}
```

## <a name="array"></a>配列

配列は、任意の型の値のリストを保持します。 \[ \]を使用して (0 から始まる) インデックスで特定の項目にアクセスし、 **for タグ**を使用して反復処理し、size プロパティを使用して配列内の項目数を取得できます。

```
{% for view in entitylist.views %}

{{ view.name }}

{% endfor %}

{{ entitylist.views[0] }}

{% if entitylist.views.size > 0 %}

This entity list has {{ entitylist.views.size }} views.

{% endif %}
```

## <a name="dictionary"></a>バイナリ

ディクショナリは、文字列キーによってアクセスできる値のコレクションを保持します。 指定された項目には、\[ \]を使用して文字列キーでアクセスできます。また、 **for タグ**を使用して反復処理し、size プロパティを使用してディクショナリ内の項目数を取得することもできます。

```
{{ request.params[ID] }}

{% if request.params.size > 0 %}

The request parameters collection contains some items.

{% endif %}
```

## <a name="datetime"></a>DateTime

DateTime オブジェクトは、特定の日付と時刻を表します。

```
{{ page.modifiedon | date: 'f' }}
```

## <a name="null"></a>空白

Null は空または存在しない値を表します。 Null 値を返しようとする出力は、何も表示されません。 条件では、false として扱われます。

```
{% if request.params[ID] %}

This will render if the ID request parameter is NOT null.

{% endif %}
```

### <a name="see-also"></a>関連項目

[Web テンプレートを使用してソースコンテンツを保存する](store-content-web-templates.md)  
[冷却演算子について](liquid-operators.md)  
[付](liquid-conditional-operators.md)  
[液体オブジェクト](liquid-objects.md)  
[液体タグ](liquid-tags.md)  
[液体フィルター](liquid-filters.md)  