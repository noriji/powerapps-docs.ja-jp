---
title: ポータルに液体フィルターを使用する |MicrosoftDocs
description: ポータルで使用できる液体フィルターについて説明します。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 996b31766641376e9a01cbefc876f3eb2b7aabc7
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2019
ms.locfileid: "73543252"
---
# <a name="available-liquid-filters"></a>使用可能な液体フィルター

液体フィルターは、文字列、数値、変数、およびオブジェクトの出力を変更するために使用されます。 これらは、| によって適用されている値から分離されています。

`{{ 'hal 9000' | upcase }} <!-- Output: HAL 9000 -->`

一部のフィルターではパラメーターを受け取ります。 また、フィルターを組み合わせて、左から右に適用することもできます。

```
{{ 2 | times: 2 | minus: 1 }} <!-- Output: 3 -->

{{ "Hello, " | append: user.firstname }} <!-- Output: Hello, Dave -->
```
以下のセクションでは、さまざまなフィルターについて説明します。 

## <a name="array-filters"></a>配列フィルター

配列フィルターは、配列を操作するために使用さ[れます。](liquid-types.md#array)  

### <a name="batch"></a>バッチ

配列を指定されたサイズの複数の配列に分割します。

**コード**

```
{% assign batches = entityview.records | batch: 2 %}

{% for batch in batches %}

<ul>

{% for item in batch %}

<li>{{ item.fullname }}</li>

{% endfor %}

</ul>

{% endfor %}
```

**Output**

```
<ul>

<li>John Smith</li>

<li>Dave Thomas</li>

</ul>

<ul>

<li>Jake Johnson</li>

<li>Jack Robinson</li>

</ul>
```

### <a name="concat"></a>concat

2つの配列を連結して1つの新しい配列を作成します。

1つの項目がパラメーターとして指定されている場合、concat は、指定された項目を最後の要素として、元の配列で構成される新しい配列を返します。

**コード**

```
Group #1: {{ group1 | join: ', ' }}

Group #2: {{ group2 | join: ', ' }}

Group #1 + Group #2: {{ group1 | concat: group2 | join: ', ' }}

Group #1 + Leslie: {{ group1 | concat: 'Leslie' | join: ', ' }}
```

**Output**

```
Group #1: John, Pete, Hannah

Group #2: Joan, Bill

Group #1 + Group #2: John, Pete, Hannah, Joan, Bill

Group #1 + Leslie: John, Pete, Hannah, Leslie
```

### <a name="except"></a>ば

指定した属性に値が指定されていない配列内のすべてのオブジェクトを選択します。 (これは**where**の逆です)。

**コード**

```
{% assign redmond = entityview.records | except: 'address1_city', 'Redmond' %}

{% for item in redmond %}

{{ item.fullname }}

{% endfor %}
```

**Output**

```
Jack Robinson
```

### <a name="first"></a>まずは

配列の最初の要素を返します。

最初は、タグ内で使用する必要がある場合に、特殊なドット表記で使用することもできます。

**コード**

```
{% assign words = This is a run of text | split:   %}

{{ words | first }}

{% if words.first == This %}

The first word is This.

{% endif %}
```

**Output**

```
This

The first word is This.
```

### <a name="group_by"></a>group_by

指定された属性で配列内の項目をグループ化します。

**コード**

```
{% assign groups = entityview.records | group_by: 'address1_city' %}

{% for group in groups %}

{{ group.key }}:

{% for item in group.items %}

{{ item.fullname }}

{% endfor %}

{% endfor %}
```

**Output**

```
Redmond:

John Smith

Dave Thomas

Jake Johnson

New York:

Jack Robinson
```

### <a name="join"></a>結合

パラメーターとして渡された文字で配列の要素を結合します。 結果は1つの文字列になります。

**コード**

```
{% assign words = This is a run of text | split:   %}

{{ words | join: ,  }}
```

**Output**

```
This, is, a, run, of, text
```

### <a name="last"></a>前の

配列の最後の要素を返します。

last は、タグ内で使用する必要がある場合に、特殊なドット表記でも使用できます。

**コード**

```
{% assign words = This is a run of text | split:   -%}

{{ words | last }}

{% if words.last == text -%}

The last word is text.

{% endif -%}
```

**Output**

```
text

The last word is text.
```

### <a name="order_by"></a>\_順序

配列の要素の指定した属性によって並べ替えられた配列の要素を返します。

必要に応じて、desc を2番目のパラメーターとして指定すると、昇順ではなく降順で要素を並べ替えることができます。

**コード**

```
{{ entityview.records | order_by: 'fullname' | join: ', ' }}

{{ entityview.records | order_by: 'fullname', 'desc' | join: ', ' }}
```

**Output**

```
Dave Thomas, Jack Robinson, Jake Johnson, John Smith

John Smith, Jake Johnson, Jack Robinson, Dave Thomas
```

### <a name="random"></a>無作為

配列からランダムに選択された単一の項目を返します。

**コード**

```
{{ group1 | join: ', ' }}

{{ group1 | random }}
```

**Output**

```
John, Pete, Hannah

Pete
```

### <a name="select"></a>クリック

配列内の各項目について、指定した属性の値を選択し、これらの値を配列として返します。

**コード**

```
{{ entityview.records | select: 'address1_city' | join: ', ' }}
```

**Output**

```
Redmond, New York
```

### <a name="shuffle"></a>シャッフル

配列に適用され、同じ項目を持つ新しい配列をランダムな順序で返します。

**コード**

```
{{ group1 | join: ', ' }}

{{ group1 | shuffle | join: ', ' }}
```

**Output**

```
John, Pete, Hannah

Hannah, John, Pete
```

### <a name="size"></a>幅

配列内の項目の数を返します。

また、サイズは、タグ内で使用する必要がある場合に、特殊なドット表記で使用することもできます。

**コード**

```
{% assign words = This is a run of text | split:   -%}

{{ words | size }}

{% if words.size == 6 -%}

The text contains 6 words.

{% endif -%}
```

**Output**

```
6

The text contains 6 words.
```

### <a name="skip"></a>skip

配列内の指定された数の項目をスキップし、残りの項目を返します。

**コード**

```
{% assign words = This is a run of text | split:   %}

{{ words | skip: 3 | join: ', ' }}
```

**Output**

```
run, of, text
```

### <a name="take"></a>長時間

配列から指定された数の項目を取得し、取得した項目を返します。

**コード**

```
{% assign words = This is a run of text | split:   %}

{{ words | take: 3 | join: ', ' }}
```
**Output**

```

This, is, a
```

### <a name="then_by"></a>その後、\_

に**よって\_順序**に従って既に並べ替えられている配列に後続の順序を追加します。

必要に応じて、desc を2番目のパラメーターとして指定すると、昇順ではなく降順で要素を並べ替えることができます。

**コード**

```
{{ entityview.records | order_by: 'address1_city' | then_by: 'fullname' | join: ', ' }}

{{ entityview.records | order_by: 'address1_city' | then_by: 'fullname', 'desc' | join: ', ' }}
```

**Output**

```
Dave Thomas, Jack Robinson, Jake Johnson, John Smith

John Smith, Jake Johnson, Jack Robinson, Dave Thomas
```

### <a name="where"></a>どこ

指定された属性の値が指定されている配列内のすべてのオブジェクトを選択します。

**コード**

```
{% assign redmond = entityview.records | where: 'address1_city', 'Redmond' %}

{% for item in redmond %}

{{ item.fullname }}

{% endfor %}
```

**Output**

```
John Smith

Dave Thomas

Jake Johnson
```


## <a name="date-filters"></a>日付フィルター

日付フィルターを使用して、日付の算術計算や、DateTime 値からさまざまな形式への変換を行うことができます。

### <a name="date"></a>予定

.NET 書式指定文字列を使用して DateTime 値の書式を設定します。

[標準の日付と時刻の書式指定文字列](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings)  

[カスタム日時書式指定文字列](https://docs.microsoft.com/dotnet/standard/base-types/custom-date-and-time-format-strings)  

**コード**

```
{{ now | date: 'g' }}

{{ now | date: 'MMMM dd, yyyy' }}
```

**Output**

```
5/7/2018 7:20 AM

May 07, 2018
```

### <a name="date_add_days"></a>\_日\_追加日

DateTime 値に、指定された整数部と小数部から成る日数を加算します。 パラメーターには、正または負の値を指定できます。

**コード**

```
{{ now }}

{{ now | date_add_days: 1 }}

{{ now | date_add_days: -2.5 }}
```

**Output**

```
5/7/2018 7:20:46 AM

5/8/2018 7:20:46 AM

5/4/2018 7:20:46 PM
```

### <a name="date_add_hours"></a>\_時間\_追加する日付

DateTime 値に、指定された整数部と小数部から成る時間数を加算します。 パラメーターには、正または負の値を指定できます。

**コード**

```
{{ now }}

{{ now | date_add_hours: 1 }}

{{ now | date_add_hours: -2.5 }}
```

**Output**

```
5/7/2018 7:20:46 AM

5/7/2018 8:20:46 AM

5/7/2018 4:50:46 AM
```

### <a name="date_add_minutes"></a>\_分を追加\_日付

DateTime 値に、指定された整数部と小数部から成る分数を加算します。 パラメーターには、正または負の値を指定できます。

**コード**

```
{{ now }}

{{ now | date_add_minutes: 10 }}

{{ now | date_add_minutes: -2.5 }}
```


**Output**

```
5/7/2018 7:20:46 AM

5/7/2018 7:30:46 AM

5/7/2018 7:18:16 AM
```

### <a name="date_add_months"></a>\_月を追加\_日付

指定された月数を DateTime 値に加算します。 パラメーターには、正または負の値を指定できます。

**コード**

```
{{ now }}

{{ now | date_add_months: 1 }}

{{ now | date_add_months: -2 }}
```

**Output**

```
5/7/2018 7:20:46 AM

6/7/2018 7:20:46 AM

3/7/2018 7:20:46 AM
```

### <a name="date_add_seconds"></a>\_秒数を加算\_日付

DateTime 値に、指定された整数部と小数部から成る秒数を加算します。 パラメーターには、正または負の値を指定できます。

**コード**

```
{{ now }}

{{ now | date_add_seconds: 10 }}

{{ now | date_add_seconds: -1.25 }}
```

**Output**

```
5/7/2018 7:20:46 AM

5/7/2018 7:20:56 AM

5/7/2018 7:20:45 AM
```

### <a name="date_add_years"></a>\_年を追加\_日付

指定された年単位の数を DateTime 値に加算します。 パラメーターには、正または負の値を指定できます。

**コード**

```
{{ now }}

{{ now | date_add_years: 1 }}

{{ now | date_add_years: -2 }}
```

**Output**

```
5/7/2018 7:20:46 AM

5/7/2019 7:20:46 AM

5/7/2016 7:20:46 AM
```

### <a name="date_to_iso8601"></a>\_に\_日付

[ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)標準に従って DateTime 値の書式を設定します。 [*Atom フィード*](https://tools.ietf.org/html/rfc4287)、または HTML5 &lt;time&gt; 要素を作成するときに便利です。  

**コード**

```
{{ now | date_to_iso8601 }}
```

**Output**

```
2018-05-07T07:20:46Z
```

### <a name="date_to_rfc822"></a>\_rfc822 に\_日付

[RFC 822](https://www.ietf.org/rfc/rfc0822.txt)標準に従って DateTime 値の書式を設定します。 [*RSS フィード*](https://cyber.law.harvard.edu/rss/rss.html)を作成するときに便利です。  

**コード**

```
{{ now | date_to_rfc822 }}
```

**Output**

```
Mon, 07 May 2018 07:20:46 Z
```


## <a name="entity-list-filters"></a>エンティティリストフィルター

エンティティリストフィルターは、特定の[entitylist](liquid-objects.md#entitylist)属性値を操作するために使用され、エンティティリストビューを作成するのに役立ちます。  

### <a name="current_sort"></a>現在の\_並べ替え

並べ替え式を指定すると、指定された属性の現在の並べ替え方向が返されます。

**コード**

```
{{ 'name ASC, createdon DESC' | current_sort: 'createdon' }}
```

**Output**

```
DESC
```

### <a name="metafilters"></a>メタフィルター

[Entitylist](liquid-objects.md#entitylist)フィルター\_definition JSON 値をフィルターオプショングループオブジェクトに解析します。  

メタフィルターは、必要に応じて、現在の属性フィルタークエリと現在の[entitylist](liquid-objects.md#entitylist)を使用して指定することができます。これにより、返されたフィルターオブジェクトのフラグをオンまたはオフにすることができます。

**コード**

```
{% assign filters = entitylist | metafilters: params.mf, entityview %}
{% if filters.size > 0 %}
  <ul id=entitylist-filters>
    {% for filter in filters %}
      <li class=entitylist-filter-option-group>
        {% if filter.selection_mode == 'Single' %}
          {% assign type = 'radio' %}
        {% else %}
          {% assign type = 'checkbox' %}
        {% endif %}
        <h4 class=entitylist-filter-option-group-label
          data-filter-id={{ filter.id | h }}>
          {{ filter.label | h }}
        </h4>
        <ul>
          {% for option in filter.options %}
            <li class=entitylist-filter-option>
              {% if option.type == 'text' %}
                <div class=input-group entitylist-filter-option-text>
                  <span class=input-group-addon>
                    <span class=fa fa-filter aria-hidden=true></span>
                  </span>
                  <input class=form-control
                    type=text
                    name={{ filter.id | h }}
                    value={{ option.text | h }} />
                </div>
              {% else %}
                <div class={{ type | h }}>
                  <label>
                    <input
                      type={{ type | h }}
                      name={{ filter.id | h }}
                      value={{ option.id | h }}
                      {% if option.checked %}
                        checked=checked
                        data-checked=true{% endif %}
                      />
                    {{ option.label | h }}
                  </label>
                </div>
              {% endif %}
            </li>
          {% endfor %}
        </ul>
      </li>
    {% endfor %}
  </ul>
  <button class=btn btn-default data-serialized-query=mf data-target=#entitylist-filters>Apply Filters</button>
{% endif %}
```

### <a name="reverse_sort"></a>逆順\_並べ替え

並べ替えの方向を指定した場合は、逆の並べ替え方向が返されます。

**コード**

```
<!-- Sort direction is not case-sensitive -->

{{ 'ASC' | reverse_sort }}

{{ 'desc' | reverse_sort }}
```

**Output**

```
DESC

ASC
```


## <a name="math-filters"></a>数値演算フィルター

数値演算フィルターを使用すると、[数値](liquid-types.md#number)に対して数値演算を実行できます。  

すべてのフィルターと同様に、数値演算フィルターを連結して、左から右へ順に適用できます。

**コード**

```
{{ 10 | times: 2 | minus: 5 | divided_by: 3 }}
```

**Output**

```
5
```

### <a name="ceil"></a>ceil

最も近い整数に値を丸めます。

**コード**

```
{{ 4.6 | ceil }}

{{ 4.3 | ceil }}
```

**Output**

```
5

5
```

### <a name="divided_by"></a>分割された\_

数値を別の数値で除算します。

**コード**

```
{{ 10 | divided_by: 2 }}

{{ 10 | divided_by: 3 }}

{{ 10.0 | divided_by: 3 }}
```

**Output**

```
5

3

3.333333
```

### <a name="floor"></a>階数

最も近い整数に値を丸めます。

**コード**

```
{{ 4.6 | floor }}

{{ 4.3 | floor }}
```

**Output**

```
4

4
```

### <a name="minus"></a>除く

数値を別の数値から減算します。

**コード**

```
<!-- entityview.page = 11 -->

{{ entityview.page | minus: 1 }}

{{ 10 | minus: 1.1 }}

{{ 10.1 | minus: 1 }}
```

**Output**

```
10

9

9.1
```

### <a name="modulo"></a>剰余

数値を別の数値で除算し、剰余を返します。

**コード**

```
{{ 12 | modulo: 5 }}
```

**Output**

```
2
```

### <a name="plus"></a>プラス

数値を別の数値に加算します。

**コード**

```
<!-- entityview.page = 11 -->

{{ entityview.page | plus: 1 }}

{{ 10 | plus: 1.1 }}

{{ 10.1 | plus: 1 }}
```

**Output**

```
12

11

11.1
```

### <a name="round"></a>誤差

最も近い整数または指定した小数点以下の桁数に値を丸めます。

**コード**

```
{{ 4.6 | round }}

{{ 4.3 | round }}

{{ 4.5612 | round: 2 }}
```

**Output**

```
5

4

4.56
```

### <a name="times"></a>複数

数値を別の数値で乗算します。

**コード**

```
{{ 10 | times: 2 }}

{{ 10 | times: 2.2 }}

{{ 10.1 | times: 2 }}
```

**Output**

```
20

20

20.2
```


## <a name="string-filters"></a>文字列フィルター

文字列フィルターは[文字列](liquid-types.md#string)を操作します。  

### <a name="append"></a>追記

文字列を別の文字列の末尾に追加します。

**コード**

```
{{ 'filename' | append: '.js' }}
```

**Output**

```
filename.js
```

### <a name="capitalize"></a>**文字**

文字列の最初の単語を大文字にします。

**コード**

```
{{ 'capitalize me' | capitalize }}
```

**Output**

```
Capitalize Me
```

### <a name="downcase"></a>**downcase**

文字列を小文字に変換します。

**コード**

```
{{ 'MIxed Case TExt' | downcase }}
```

**Output**

```
mixed case text
```

### <a name="escape"></a>**付ける**

文字列を HTML でエスケープします。

**コード**

```
{{ '<p>test</p>' | escape }}
```

**Output**

```
&lt;p&gt;test&lt;/p&gt;
```

### <a name="newline_to_br"></a>**改行\_\_br**

文字列内の改行のたびに、&lt;br/&gt; 改行 HTML タグを挿入します。

**コード**

```
{% capture text %}

A

B

C

{% endcapture %}

{{ text | newline_to_br }}
```

**Output**

```
A<br />

B<br />

C<br />
```

### <a name="prepend"></a>**ド**

文字列を別の文字列の先頭に付加します。

**コード**

```
{{ 'Jane Johnson' | prepend: 'Dr. ' }}
```

**Output**

```
Dr. Jane Johnson
```

### <a name="remove"></a>**から**

文字列からすべての部分文字列を削除します。

**コード**

```
{{ 'Hello, Dave. How are you, Dave?' | remove: 'Dave' }}
```

**Output**

```
Hello, . How are you, ?
```

### <a name="remove_first"></a>**最初に\_を削除する**

文字列から最初に見つかった部分文字列を削除します。

**コード**

```
{{ 'Hello, Dave. How are you, Dave?' | remove_first: 'Dave' }}
```

**Output**

```
Hello, . How are you, Dave?
```

### <a name="replace"></a>**ら**

文字列のすべての出現箇所を部分文字列に置換します。

**コード**

```
{{ 'Hello, Dave. How are you, Dave?' | replace: 'Dave', 'John' }}
```

**Output**

```
Hello, John. How are you, John?
```

### <a name="replace_first"></a>**最初\_置換**

文字列の最初の出現箇所を部分文字列で置換します。

**コード**

```
{{ 'Hello, Dave. How are you, Dave?' | replace_first: 'Dave', 'John' }}
```

**Output**

```
Hello, John. How are you, Dave?
```

### <a name="split"></a>**分配**

分割フィルターは、パラメーターとして部分文字列を受け取ります。 文字列を配列に分割するには、区切り記号として部分文字列を使用します。

**コード**

```
{% assign words = This is a demo of the split filter | split: ' ' %}

First word: {{ words.first }}

First word: {{ words[0] }}

Second word: {{ words[1] }}

Last word: {{ words.last }}

All words: {{ words | join: ', ' }}
```

**Output**

```
First word: This

First word: This

Second word: is

Last word: filter

All words: This, is, a, demo, of, the, split, filter
```

### <a name="strip_html"></a>**\_html のストリップ**

文字列からすべての HTML タグを取り除きます。

**コード**

```
<p>Hello</p>
```

**Output**

```
Hello
```

### <a name="strip_newlines"></a>**\_改行の削除**

文字列から改行を取り除きます。

**コード**

```
{% capture text %}

A

B

C

{% endcapture %}

{{ text | strip_newlines }}
```

**Output**

```
ABC
```

### <a name="text_to_html"></a>**html\_するテキスト\_**

プレーンテキスト文字列を単純な HTML として書式設定します。 すべてのテキストは HTML エンコードされ、空白行で区切られたテキストのブロックは段落 &lt;p&gt; タグに折り返されます。1つの改行は &lt;br&gt;に置き換えられ、Url はハイパーリンクに変換されます。

**コード**

```
{{ note.notetext | text_to_html }}
```

**Output**

```
<p>This is the first paragraph of notetext. It contains a URL: <a href="https://example.com/" rel="nofollow">https://example.com</a></p>

<p>This is a second paragraph.</p>
```

### <a name="truncate"></a>**切捨て**

文字列を指定された文字数まで切り捨てます。 文字列に省略記号 (...) が追加され、文字数に含まれています。

**コード**

```
{{ 'This is a long run of text.' | truncate: 10 }}
```

**Output**

```
This is...
```

### <a name="truncate_words"></a>**\_語の切り捨て**

文字列を指定された数の単語まで切り捨てます。 省略記号 (...) が切り捨てられた文字列に追加されます。

**コード**

```
{{ 'This is a long run of text.' | truncate_words: 3 }}
```

**Output**

```
This is a...
```

### <a name="upcase"></a>**upcase**

文字列を大文字に変換します。

**コード**

```
{{ 'MIxed Case TExt' | upcase }}
```

**Output**

```
MIXED CASE TEXT
```

### <a name="url_escape"></a>**url\_エスケープ**

URI-URL に含める文字列をエスケープします。

**コード**

```
{{ 'This & that//' | url_escape }}
```

**Output**

```
This+%26+that%2F%2F
```

### <a name="xml_escape"></a>**xml\_エスケープ**

Xml-XML 出力に含める文字列をエスケープします。

**コード**

```
{{ '<p>test</p>' | xml_escape }}
```

**Output**

```
&lt;p&gt;test&lt;/p&gt;
```


## <a name="type-filters"></a>型フィルター

型フィルターを使用すると、ある型の値を他の型に変換できます。

### <a name="boolean"></a>**演算**

文字列値からブール値への変換を試みます。 値が既にブール値の場合は、そのまま返されます。 値をブール値に変換できない場合は null が返されます。

このフィルターでは、on、enabled、または yes を true として、off、disabled、および no を false として使用することもできます。

**コード**

```
{{ true | boolean }}

{{ 'false' | boolean }}

{{ 'enabled' | boolean }}

{{ settings['something/enabled'] | boolean | default: false }}
```

**Output**

```
true

false

true

false
```

### <a name="decimal"></a>**位**

文字列値から10進数への変換を試みます。 値が既に10進数である場合は、変更されずに返されます。 値を10進数値に変換できない場合は、null が返されます。

**コード**

```
{{ 10.1 | decimal }}

{{ '3.14' | decimal }}

{{ 'text' | decimal | default: 3.14 }}
```

**Output**

```
10.1

3.14

3.14
```

### <a name="integer"></a>**以外**

文字列値を整数に変換しようとします。 値が既に整数である場合は、変更されずに返されます。 値を整数に変換できない場合は、null が返されます。

**コード**

```
{{ 10 | integer }}

{{ '10' | integer }}

{{ '10.1' | integer }}

{{ 'text' | integer | default: 2 }}
```

**Output**

```
10

10


2
```

### <a name="string"></a>**文字列**

値から文字列形式への変換を試みます。 値が既に文字列の場合は、変更されずに返されます。 値が null の場合は null が返されます。



## <a name="url-filters"></a>URL フィルター

URL フィルターを使用すると、Url の一部を構築または抽出できます。

### <a name="add_query"></a>**\_クエリの追加**

URL にクエリ文字列パラメーターを追加します。 パラメーターが URL に既に存在する場合は、パラメーター値が更新されます。

このフィルターを完全絶対 URL に適用すると、更新された絶対 URL が結果になります。 パスに適用されている場合は、更新されたパスが結果になります。

**コード**

```
{{ 'https://example.com/path?page=1' | add_query: 'foo', 'bar' }}

{{ '/path?page=1' | add_query: 'page', 2 }}
```

**Output**

```
https://example.com/path?page=1&foo=bar

/path?page=2
```

### <a name="base"></a>**常用**

指定された URL のベース URL を取得します。

**コード**

```
{{ 'https://example.com/path?foo=bar&page=2' | base }}
```

**Output**

```
https://example.com
```

### <a name="host"></a>**ホスト**

URL のホスト部分を取得します。

**コード**

```
{{ 'https://example.com/path?foo=bar&page=2' | host }}
```

**Output**

```
example.com
```

### <a name="path"></a>**道**

URL のパス部分を取得します。

**コード**

```
{{ 'https://example.com/path?foo=bar&page=2' | path }}

{{ '/path?foo=bar&page=2' | path }}
```

**Output**

```
/path

/path
```

### <a name="path_and_query"></a>**パス\_と\_クエリ**

URL のパスとクエリ部分を取得します。

**コード**

```
{{ 'https://example.com/path?foo=bar&page=2' | path_and_query }}

{{ '/path?foo=bar&page=2' | path_and_query }}
```

**Output**

```
/path?foo=bar&page=2

/path?foo=bar&page=2
```

### <a name="port"></a>**ポート**

URL のポート番号を取得します。

**コード**

```
{{ 'https://example.com/path?foo=bar&page=2' | port }}

{{ 'https://example.com/path?foo=bar&page=2' | port }}

{{ 'https://example.com:9000/path?foo=bar&page=2' | port }}
```

**Output**

```
80

443

9000
```

### <a name="remove_query"></a>**\_クエリの削除**

URL からクエリ文字列パラメーターを削除します。 URL にパラメーターが存在しない場合、URL は変更されずに返されます。

このフィルターを完全絶対 URL に適用すると、更新された絶対 URL が結果になります。 パスに適用されている場合は、更新されたパスが結果になります。

**コード**

```
{{ 'https://example.com/path?page=1' | remove_query: 'page' }}

{{ '/path?page=1' | remove_query: 'page' }}
```

**Output**

```
https://example.com/path

/path
```

### <a name="scheme"></a>**体系**

URL のスキーム部分を取得します。

**コード**

```
{{ 'https://example.com/path?foo=bar&page=2' | scheme }}

{{ 'https://example.com/path?foo=bar&page=2' | scheme }}
```

**Output**

```
http

https
```


## <a name="additional-filters"></a>追加のフィルター

これらのフィルターは、便利な一般的な機能を提供します。

### <a name="default"></a>**標準**

値が割り当てられていない変数 (つまり null) の既定値を返します。

**コード**

```
{{ snippets[Header] | default: 'My Website' }}
```

**Output**

```
<!-- If a snippet with the name Header returns null -->

My Website
```

### <a name="file_size"></a>**ファイル\_サイズ**

バイト数を表す数値に適用された場合は、適切なスケールの単位を使用して、書式設定されたファイルサイズを返します。

必要に応じて、有効桁数のパラメーターを渡して、結果の小数点以下の桁数を制御できます。 既定の有効桁数は1です。

**コード**

```
{{ 10000000 | file_size }}

{{ 2050 | file_size: 0 }}

{{ entity.notes.first.filesize | file_size: 2 }}
```

**Output**

```
9.5 MB

2 KB

207.14 KB
```

### <a name="has_role"></a>**ロールが\_**

[ユーザーに](liquid-objects.md#user)適用されます。ユーザーが特定のロールに属している場合は true を返します。 そうでない場合は false を返します。  

**コード**

```
{% assign is_admin = user | has_role: 'Administrators' %}

{% if is_admin %}

User is an administrator.

{% endif %}
```

### <a name="liquid"></a>**計**

文字列を液体コードとしてレンダリングします。 このコードは、現在の液体実行コンテキスト (変数など) にアクセスできます。

> [!Note] 
> このフィルターは注意して使用する必要があります。通常、このフィルターは、ポータルコンテンツの作成者の排他制御下にある値、または液体コードを記述するために信頼できる他のユーザーにのみ適用する必要があります。

**コード**

```
{{ page.adx_copy | liquid }}
```

### <a name="see-also"></a>関連項目

[Web テンプレートを使用してソースコンテンツを保存する](store-content-web-templates.md)  
液体の 
液体[型](liquid-types.md)に[つい](liquid-operators.md)て  
[液体オブジェクト](liquid-objects.md)  
[液体タグ](liquid-tags.md)  
[液体フィルター](liquid-filters.md)  
