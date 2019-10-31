---
title: ポータルで反復タグを使用する | MicrosoftDocs
description: ポータルで使用可能な反復タグについて説明します
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: null
ms.date: 08/30/2019
ms.author: shjais
ms.reviewer: null
---

# <a name="iteration-tags"></a>反復タグ

反復タグは、コードのブロックを繰り返し実行/表示するのに使用します。

## <a name="for"></a>用

コードのブロックを繰り返し実行します。 最も一般的な用途は、配列またはディクショナリの項目の反復です。

for タグ ブロック内では [forloop オブジェクト](liquid-objects.md#forloop)が使用可能です。  

**コード**

```
{% for child_page in page.children %}

<a href={{ child_page.url }}>{{ child_page.title }}</a>

{% endfor %}
```

**出力**

```
<a href=/parent/child1/>Child 1</a>

<a href=/parent/child2/>Child 2</a>

<a href=/parent/child3/>Child 3</a>
```

### <a name="parameters"></a>パラメーター

これらの for のパラメーターは、単独または組み合わせて使用できます。

**リミット**

特定の項目数の後、ループが終了します。

**コード**

```
{% for child_page in page.children limit:2 %}

<a href={{ child_page.url }}>{{ child_page.title }}</a>

{% endfor %}
```

**出力**

```
<a href=/parent/child1/>Child 1</a>

<a href=/parent/child2/>Child 2</a>
```

**オフセット**

特定のインデックスでループを開始します。

**コード**

```
{% for child_page in page.children offset:1 %}

<a href={{ child_page.url }}>{{ child_page.title }}</a>

{% endfor %}
```

**出力**

```
<a href=/parent/child2/>Child 2</a>

<a href=/parent/child3/>Child 3</a>
```

**範囲**

ループする値の範囲を定義します。

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

**出力**

```
2 3 4

10 11 12 14
```

**予約済み**

ループを最後の項目から逆に反復します。

**コード**

```
{% for child_page in page.children reversed %}

<a href={{ child_page.url }}>{{ child_page.title }}</a>

{% endfor %}
```

**出力**

```
<a href=/parent/child3/>Child 3</a>

<a href=/parent/child2/>Child 2</a>

<a href=/parent/child1/>Child 1</a>
```

## <a name="cycle"></a>サイクル

文字列のグループをループし、パラメーターとして渡された順序で出力されます。 サイクルが呼び出されるたびに、パラメーターとして渡された次の文字列が出力されます。

**コード**

```
{% for item in items %}

<div class={% cycle 'red', 'green', 'blue' %}> {{ item }} </div>

{% end %}
```

**出力**

```
<div class=red> Item one </div>

<div class=green> Item two </div>

<div class=blue> Item three </div>

<div class=red> Item four </div>

<div class=green> Item five</div>
```

## <a name="tablerow"></a>テーブル行

HTML テーブルを生成します。 開始 &lt;table&gt; と終了 &lt;/table&gt; HTML タグで囲う必要があります。

テーブル行のタグ ブロック内では [tablerowloop](liquid-objects.md#tablerowloop) が利用できます。  

**コード**

```
<table>

{% tablerow child_page in page.children %}

{{ child_page.title }}

{% endtablerow %}

</table>
```

**出力**

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

これらの tablerowcan のパラメーターは、単独または組み合わせて使用できます。

**出力**

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

生成されたテーブルに必要な行数を指定します。

**cols**

**リミット**

特定の項目数の後、ループが終了します。

**コード**

```
<table>

{% tablerow child_page in page.children limit:2 %}

{{ child_page.title }}

{% endtablerow %}

</table>
```

**出力**

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

特定のインデックスでループを開始します。

**コード**

```
<table>

{% tablerow child_page in page.children offset:2 %}

{{ child_page.title }}

{% endtablerow %}

</table>
```

**出力**

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

ループする値の範囲を定義します。

**コード**

```
<table>

{% tablerow i in (1..3) %}

{{ i }}

{% endtablerow %}

</table>
```

### <a name="see-also"></a>関連項目

[制御フロー タグ](control-flow-tags.md)
[変数タグ](variable-tags.md)
[テンプレート タグ](template-tags.md)
[PowerApps Common Data Serviceエンティティ タグ](portals-entity-tags.md)
