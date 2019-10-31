---
title: ポータルにイテレーションタグを使用する |MicrosoftDocs
description: ポータルで使用できるイテレーションタグについて説明します。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 600ddb0ac6e016acf057e592ac638b4e07ddf8ba
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/11/2019
ms.locfileid: "72976509"
---
# <a name="iteration-tags"></a>イテレーション タグ

イテレーションタグは、コードのブロックを繰り返し実行または表示するために使用されます。

## <a name="for"></a>の

コードのブロックを繰り返し実行します。 これは、配列またはディクショナリ内の項目を反復処理するために最も一般的に使用されます。

For タグブロック内では、 [forloop オブジェクト](liquid-objects.md#forloop)を使用できます。  

**コード**

```
{% for child_page in page.children %}

<a href={{ child_page.url }}>{{ child_page.title }}</a>

{% endfor %}
```

**Output**

```
<a href=/parent/child1/>Child 1</a>

<a href=/parent/child2/>Child 2</a>

<a href=/parent/child3/>Child 3</a>
```

### <a name="parameters"></a>パラメーター

ののこれらのパラメーターは、単独で、または組み合わせて使用できます。

**制限**

指定された数の項目の後にループを終了します。

**コード**

```
{% for child_page in page.children limit:2 %}

<a href={{ child_page.url }}>{{ child_page.title }}</a>

{% endfor %}
```

**Output**

```
<a href=/parent/child1/>Child 1</a>

<a href=/parent/child2/>Child 2</a>
```

**影**

指定されたインデックスでループを開始します。

**コード**

```
{% for child_page in page.children offset:1 %}

<a href={{ child_page.url }}>{{ child_page.title }}</a>

{% endfor %}
```

**Output**

```
<a href=/parent/child2/>Child 2</a>

<a href=/parent/child3/>Child 3</a>
```

**範囲**

ループする数値の範囲を定義します。

**コード**

```
{% assign n = 4 %}

{% for i in (2..n) %}

{{ i }}

{% endfor %}

{% for i in (10..14) %}

{{ i }}

{% endfor }}
```

**Output**

```
2 3 4

10 11 12 14
```

**逆**

最後の項目から順に、ループを逆順に反復処理します。

**コード**

```
{% for child_page in page.children reversed %}

<a href={{ child_page.url }}>{{ child_page.title }}</a>

{% endfor %}
```

**Output**

```
<a href=/parent/child3/>Child 3</a>

<a href=/parent/child2/>Child 2</a>

<a href=/parent/child1/>Child 1</a>
```

## <a name="cycle"></a>切っ

文字列のグループをループし、パラメーターとして渡された順序で出力します。 各サイクルが呼び出されるたびに、パラメーターとして渡された次の文字列が出力されます。

**コード**

```
{% for item in items %}

<div class={% cycle 'red', 'green', 'blue' %}> {{ item }} </div>

{% end %}
```

**Output**

```
<div class=red> Item one </div>

<div class=green> Item two </div>

<div class=blue> Item three </div>

<div class=red> Item four </div>

<div class=green> Item five</div>
```

## <a name="tablerow"></a>tablerow

HTML テーブルを生成します。 &gt; &lt;テーブルを開始し、&lt;/テーブル&gt; HTML タグを閉じる必要があります。

Tablerow タグブロック内では、 [tablerowloop](liquid-objects.md#tablerowloop)を使用できます。  

**コード**

```
<table>

{% tablerow child_page in page.children %}

{{ child_page.title }}

{% endtablerow %}

</table>
```

**Output**

```
<table>

<tr class=row1>

<td class=col1>

Child Page 1

</td>

<td class=col2>

Child Page 2

</td>

<td class=col3>

Child Page 3

</td>

<td class=col4>

Child Page 4

</td>

</tr>

</table>
```

### <a name="parameters"></a>パラメーター

Tablerowcan のこれらのパラメーターは、単独で、または組み合わせて使用します。

**Output**

```
<table>

<tr class=row1>

<td class=col1>

Child Page 1

</td>

<td class=col2>

Child Page 2

</td>

</tr>

<tr class=row2>

<td class=col3>

Child Page 3

</td>

<td class=col4>

Child Page 4

</td>

</tr>

</table>
```

**コード**

```
<table>

{% tablerow child_page in page.children cols:2 %}

{{ child_page.title }}

{% endtablerow %}

</table>
```

生成されたテーブルに必要な行の数を指定します。

**cols**

**制限**

指定された数の項目の後にループを終了します。

**コード**

```
<table>

{% tablerow child_page in page.children limit:2 %}

{{ child_page.title }}

{% endtablerow %}

</table>
```

**Output**

```
<table>

<tr class=row1>

<td class=col1>

Child Page 1

</td>

<td class=col2>

Child Page 2

</td>

</tr>

</table>

offset
```

指定されたインデックスでループを開始します。

**コード**

```
<table>

{% tablerow child_page in page.children offset:2 %}

{{ child_page.title }}

{% endtablerow %}

</table>
```

**Output**

```
<table>

<tr class=row1>

<td class=col1>

Child Page 3

</td>

<td class=col2>

Child Page 4

</td>

</tr>

</table>
```

**範囲**

ループする数値の範囲を定義します。

**コード**

```
<table>

{% tablerow i in (1..3) %}

{{ i }}

{% endtablerow %}

</table>
```

### <a name="see-also"></a>関連項目

[コントロールフロータグ](control-flow-tags.md)
[変数タグ](variable-tags.md)
[テンプレートタグ](template-tags.md)
[PowerApps common data Service エンティティタグ](portals-entity-tags.md)
