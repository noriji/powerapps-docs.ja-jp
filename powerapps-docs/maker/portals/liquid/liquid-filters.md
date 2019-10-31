---
title: ポータル用 Liquid フィルターを使用する | MicrosoftDocs
description: ポータルで使用可能な Liquid のフィルターについて説明します。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: null
ms.date: 08/30/2019
ms.author: shjais
ms.reviewer: null
---

# <a name="available-liquid-filters"></a>使用可能な Liquid フィルター

Liquid フィルターは文字列、数字、変数、およびオブジェクトの出力を変更するために使用されます。 これらは、| によって適用される値とは区切られています。

`{{ 'hal 9000' | upcase }} <!-- Output: HAL 9000 -->`

パラメーターを受け入れるフィルターもあります。 またフィルターを組み合わせて左から右の順序に適用することもできます。

```
{{ 2 | times: 2 | minus: 1 }} <!-- Output: 3 -->

{{ "Hello, " | append: user.firstname }} <!-- Output: Hello, Dave -->
```
下のセクションでは、さまざまなフィルターについて説明します。 

## <a name="array-filters"></a>配列のフィルター

配列のフィルターは、[配列](liquid-types.md#array)の操作をする際に使用します。  

### <a name="batch"></a>バッチ

配列を、指定したサイズの複数の配列に分割します。

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

**出力**

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

### <a name="concat"></a>concat (連結)

2 つの配列を 1 つの新しい配列に連結します。

パラメーターとして 1 つの要素がある場合、concat は、指定の要素を最後に置く、元の配列から構成される新しい配列を返します。

**コード**

```
Group #1: {{ group1 | join: ', ' }}

Group #2: {{ group2 | join: ', ' }}

Group #1 + Group #2: {{ group1 | concat: group2 | join: ', ' }}

Group #1 + Leslie: {{ group1 | concat: 'Leslie' | join: ', ' }}
```

**出力**

```
Group #1: John, Pete, Hannah

Group #2: Joan, Bill

Group #1 + Group #2: John, Pete, Hannah, Joan, Bill

Group #1 + Leslie: John, Pete, Hannah, Leslie
```

### <a name="except"></a>except (除外)

配列内で、指定した属性について指定した値を持たない、すべてのオブジェクトを選択します。 (これは **where** の反対です。)

**コード**

```
{% assign redmond = entityview.records | except: 'address1_city', 'Redmond' %}

{% for item in redmond %}

{{ item.fullname }}

{% endfor %}
```

**出力**

```
Jack Robinson
```

### <a name="first"></a>第 1

配列の最初の要素を返します。

タグ内で使用する必要がある場合など、ドットを使用する特殊表記でも first を使用することができます。

**コード**

```
{% assign words = This is a run of text | split:   %}

{{ words | first }}

{% if words.first == This %}

The first word is This.

{% endif %}
```

**出力**

```
This

The first word is This.
```

### <a name="group_by"></a>グループ化

指定した属性で、配列の項目をグループ化します。

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

**出力**

```
Redmond:

John Smith

Dave Thomas

Jake Johnson

New York:

Jack Robinson
```

### <a name="join"></a>join (結合)

パラメーターで渡される文字を使用して、配列の要素を結合します。 結果は、単一の文字列になります。

**コード**

```
{% assign words = This is a run of text | split:   %}

{{ words | join: ,  }}
```

**出力**

```
This, is, a, run, of, text
```

### <a name="last"></a>最終

配列の最後の要素を返します。

タグ内で使用する必要がある場合など、ドットを使用する特殊表記でも last を使用することができます。

**コード**

```
{% assign words = This is a run of text | split:   -%}

{{ words | last }}

{% if words.last == text -%}

The last word is text.

{% endif -%}
```

**出力**

```
text

The last word is text.
```

### <a name="order_by"></a>order\_by

指定した属性で配列要素を並べ替えた配列要素を返します。

オプションで、2 番目のパラメーターとして desc を指定すると、昇順のかわりに降順で要素を並べ替えます。

**コード**

```
{{ entityview.records | order_by: 'fullname' | join: ', ' }}

{{ entityview.records | order_by: 'fullname', 'desc' | join: ', ' }}
```

**出力**

```
Dave Thomas, Jack Robinson, Jake Johnson, John Smith

John Smith, Jake Johnson, Jack Robinson, Dave Thomas
```

### <a name="random"></a>random (ランダム)

配列から、ランダムに選択された単一の項目を返します。

**コード**

```
{{ group1 | join: ', ' }}

{{ group1 | random }}
```

**出力**

```
John, Pete, Hannah

Pete
```

### <a name="select"></a>select (選択)

配列の各項目について指定した属性の値を選択し、これらの値を配列として返します。

**コード**

```
{{ entityview.records | select: 'address1_city' | join: ', ' }}
```

**出力**

```
Redmond, New York
```

### <a name="shuffle"></a>shuffle (シャッフル)

配列に使用すると、同じ項目を含んだ、ランダムな順で並び替えられた新しい配列を返します。

**コード**

```
{{ group1 | join: ', ' }}

{{ group1 | shuffle | join: ', ' }}
```

**出力**

```
John, Pete, Hannah

Hannah, John, Pete
```

### <a name="size"></a>size (サイズ)

配列内の項目の数を返します。

タグ内で使用する必要がある場合など、ドットを使用する特殊表記でも size を使用することができます。

**コード**

```
{% assign words = This is a run of text | split:   -%}

{{ words | size }}

{% if words.size == 6 -%}

The text contains 6 words.

{% endif -%}
```

**出力**

```
6

The text contains 6 words.
```

### <a name="skip"></a>skip (スキップ)

配列内で指定した数の項目をスキップし、残りの配列を返します。

**コード**

```
{% assign words = This is a run of text | split:   %}

{{ words | skip: 3 | join: ', ' }}
```

**出力**

```
run, of, text
```

### <a name="take"></a>take (取り出し)

配列から指定した数の項目を取り出し、取り出した項目を返します。

**コード**

```
{% assign words = This is a run of text | split:   %}

{{ words | take: 3 | join: ', ' }}
```
**出力**

```

This, is, a
```

### <a name="then_by"></a>then\_by

すでに **order\_by** で並び替えられている配列に、後続の並び替え基準を追加します。

オプションで、2 番目のパラメーターとして desc を指定すると、昇順のかわりに降順で要素を並べ替えます。

**コード**

```
{{ entityview.records | order_by: 'address1_city' | then_by: 'fullname' | join: ', ' }}

{{ entityview.records | order_by: 'address1_city' | then_by: 'fullname', 'desc' | join: ', ' }}
```

**出力**

```
Dave Thomas, Jack Robinson, Jake Johnson, John Smith

John Smith, Jake Johnson, Jack Robinson, Dave Thomas
```

### <a name="where"></a>ここで、

配列内で、指定した属性について指定した値を持つ、すべてのオブジェクトを選択します。

**コード**

```
{% assign redmond = entityview.records | where: 'address1_city', 'Redmond' %}

{% for item in redmond %}

{{ item.fullname }}

{% endfor %}
```

**出力**

```
John Smith

Dave Thomas

Jake Johnson
```


## <a name="date-filters"></a>日付フィルター

日付フィルターは、日付の計算や、DateTime 値のさまざまな形式への変換に使用します。

### <a name="date"></a>日付

.NET の書式設定文字列を使用して DateTime 値を書式設定します。

[標準の日付および時刻の書式設定文字列](https://docs.microsoft.com/en-us/dotnet/standard/base-types/standard-date-and-time-format-strings)  

[カスタムの日付および時刻の書式設定文字列](https://docs.microsoft.com/en-us/dotnet/standard/base-types/custom-date-and-time-format-strings)  

**コード**

```
{{ now | date: 'g' }}

{{ now | date: 'MMMM dd, yyyy' }}
```

**出力**

```
5/7/2018 7:20 AM

May 07, 2018
```

### <a name="date_add_days"></a>date\_add\_days

DateTime 値に、整数または小数の日数を加算します。 パラメーターは正および負を使用できます。

**コード**

```
{{ now }}

{{ now | date_add_days: 1 }}

{{ now | date_add_days: -2.5 }}
```

**出力**

```
5/7/2018 7:20:46 AM

5/8/2018 7:20:46 AM

5/4/2018 7:20:46 PM
```

### <a name="date_add_hours"></a>date\_add\_hours

DateTime 値に、整数または小数の時間を加算します。 パラメーターは正および負を使用できます。

**コード**

```
{{ now }}

{{ now | date_add_hours: 1 }}

{{ now | date_add_hours: -2.5 }}
```

**出力**

```
5/7/2018 7:20:46 AM

5/7/2018 8:20:46 AM

5/7/2018 4:50:46 AM
```

### <a name="date_add_minutes"></a>date\_add\_minutes

DateTime 値に、整数または小数の分を加算します。 パラメーターは正および負を使用できます。

**コード**

```
{{ now }}

{{ now | date_add_minutes: 10 }}

{{ now | date_add_minutes: -2.5 }}
```


**出力**

```
5/7/2018 7:20:46 AM

5/7/2018 7:30:46 AM

5/7/2018 7:18:16 AM
```

### <a name="date_add_months"></a>date\_add\_months

DateTime 値に、整数の月を加算します。 パラメーターは正および負を使用できます。

**コード**

```
{{ now }}

{{ now | date_add_months: 1 }}

{{ now | date_add_months: -2 }}
```

**出力**

```
5/7/2018 7:20:46 AM

6/7/2018 7:20:46 AM

3/7/2018 7:20:46 AM
```

### <a name="date_add_seconds"></a>date\_add\_seconds

DateTime 値に、整数または小数の秒を加算します。 パラメーターは正および負を使用できます。

**コード**

```
{{ now }}

{{ now | date_add_seconds: 10 }}

{{ now | date_add_seconds: -1.25 }}
```

**出力**

```
5/7/2018 7:20:46 AM

5/7/2018 7:20:56 AM

5/7/2018 7:20:45 AM
```

### <a name="date_add_years"></a>date\_add\_years

DateTime 値に、整数の年を加算します。 パラメーターは正および負を使用できます。

**コード**

```
{{ now }}

{{ now | date_add_years: 1 }}

{{ now | date_add_years: -2 }}
```

**出力**

```
5/7/2018 7:20:46 AM

5/7/2019 7:20:46 AM

5/7/2016 7:20:46 AM
```

### <a name="date_to_iso8601"></a>date\_to\_iso8601

DateTime 値を [ISO 8601](http://en.wikipedia.org/wiki/ISO_8601) 標準に従って書式設定します。 [*Atom フィード*](http://tools.ietf.org/html/rfc4287) や HTML5 の &lt;時間&gt; 要素を作成する場合に役立ちます。  

**コード**

```
{{ now | date_to_iso8601 }}
```

**出力**

```
2018-05-07T07:20:46Z
```

### <a name="date_to_rfc822"></a>date\_to\_rfc822

DateTime 値を [RFC 822](https://www.ietf.org/rfc/rfc0822.txt) 標準に従って書式設定します。 [*RSS フィード*](http://cyber.law.harvard.edu/rss/rss.html) を作成する場合に役立ちます。  

**コード**

```
{{ now | date_to_rfc822 }}
```

**出力**

```
Mon, 07 May 2018 07:20:46 Z
```


## <a name="entity-list-filters"></a>エンティティ リスト フィルター

特定の [entitylist](liquid-objects.md#entitylist) 属性値を使用するため、およびエンティティ リスト ビューを作成するために、エンティティ リスト フィルターを使用します。  

### <a name="current_sort"></a>current\_sort

指定された並べ替えを定義する式は、指定された属性を並べ替える現在方向を返します。

**コード**

```
{{ 'name ASC, createdon DESC' | current_sort: 'createdon' }}
```

**出力**

```
DESC
```

### <a name="metafilters"></a>metafilters

[entitylist](liquid-objects.md#entitylist) filter\_definition JSON 値を解析してフィルター オプション グループ オブジェクトにします。  

metafilters には現在の属性フィルター クエリと現在の [entitylist](liquid-objects.md#entitylist) がオプションで提供され、返されたフィルター オブジェクトを選択または選択解除のいずれかにフラグ設定できるようになります。

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

### <a name="reverse_sort"></a>reverse\_sort

指定された並べ替えの向きとは逆の向きを返します。

**コード**

```
<!-- Sort direction is not case-sensitive -->

{{ 'ASC' | reverse_sort }}

{{ 'desc' | reverse_sort }}
```

**出力**

```
DESC

ASC
```


## <a name="math-filters"></a>Math フィルター

Math フィルターは、[数値](liquid-types.md#number) による、数学的操作の実行を可能にします。  

すべてのフィルターと同じように、Math フィルターはつなげることが可能で、左から右の順に適用されます。

**コード**

```
{{ 10 | times: 2 | minus: 5 | divided_by: 3 }}
```

**出力**

```
5
```

### <a name="ceil"></a>ceil

最近似値の整数に最も近い上の値に四捨五入します。

**コード**

```
{{ 4.6 | ceil }}

{{ 4.3 | ceil }}
```

**出力**

```
5

5
```

### <a name="divided_by"></a>divided\_by

異なる数で数を分けます。

**コード**

```
{{ 10 | divided_by: 2 }}

{{ 10 | divided_by: 3 }}

{{ 10.0 | divided_by: 3 }}
```

**出力**

```
5

3

3.333333
```

### <a name="floor"></a>floor

最近似値の整数に最も近い下の値に四捨五入します。

**コード**

```
{{ 4.6 | floor }}

{{ 4.3 | floor }}
```

**出力**

```
4

4
```

### <a name="minus"></a>minus

別の数から数を減算します。

**コード**

```
<!-- entityview.page = 11 -->

{{ entityview.page | minus: 1 }}

{{ 10 | minus: 1.1 }}

{{ 10.1 | minus: 1 }}
```

**出力**

```
10

9

9.1
```

### <a name="modulo"></a>modulo

別の数で数を分割し、残りの数を返します。

**コード**

```
{{ 12 | modulo: 5 }}
```

**出力**

```
2
```

### <a name="plus"></a>plus

他の数に数を追加します。

**コード**

```
<!-- entityview.page = 11 -->

{{ entityview.page | plus: 1 }}

{{ 10 | plus: 1.1 }}

{{ 10.1 | plus: 1 }}
```

**出力**

```
12

11

11.1
```

### <a name="round"></a>round

最近似値の整数、または指定された小数点で値を四捨五入します。

**コード**

```
{{ 4.6 | round }}

{{ 4.3 | round }}

{{ 4.5612 | round: 2 }}
```

**出力**

```
5

4

4.56
```

### <a name="times"></a>times

異なる数で数を乗数します。

**コード**

```
{{ 10 | times: 2 }}

{{ 10 | times: 2.2 }}

{{ 10.1 | times: 2 }}
```

**出力**

```
20

20

20.2
```


## <a name="string-filters"></a>文字列フィルター

文字列フィルタは、[文字列](liquid-types.md#string) を処理します。  

### <a name="append"></a>追加

別の文字列の末尾に文字列を追加します。

**コード**

```
{{ 'filename' | append: '.js' }}
```

**出力**

```
filename.js
```

### <a name="capitalize"></a>**capitalize**

文字列の最初の単語の先頭を大文字にします。

**コード**

```
{{ 'capitalize me' | capitalize }}
```

**出力**

```
Capitalize Me
```

### <a name="downcase"></a>**downcase**

文字列を小文字に変換します。

**コード**

```
{{ 'MIxed Case TExt' | downcase }}
```

**出力**

```
mixed case text
```

### <a name="escape"></a>**escape**

HTML のエスケープ文字列。

**コード**

```
{{ '<p>test</p>' | escape }}
```

**出力**

```
&lt;p&gt;test&lt;/p&gt;
```

### <a name="newline_to_br"></a>**newline\_to\_br**

文字列の中の改行位置に、改行の HTML タグ &lt;br /&gt; を挿入します。

**コード**

```
{% capture text %}

A

B

C

{% endcapture %}

{{ text | newline_to_br }}
```

**出力**

```
A<br />

B<br />

C<br />
```

### <a name="prepend"></a>**prepend**

別の文字列の先頭に文字列を追加します。

**コード**

```
{{ 'Jane Johnson' | prepend: 'Dr. ' }}
```

**出力**

```
Dr. Jane Johnson
```

### <a name="remove"></a>**remove**

文字列から特定のサブストリングをすべて削除します。

**コード**

```
{{ 'Hello, Dave. How are you, Dave?' | remove: 'Dave' }}
```

**出力**

```
Hello, . How are you, ?
```

### <a name="remove_first"></a>**remove\_first**

文字列から最初の特定のサブストリングを削除します。

**コード**

```
{{ 'Hello, Dave. How are you, Dave?' | remove_first: 'Dave' }}
```

**出力**

```
Hello, . How are you, Dave?
```

### <a name="replace"></a>**replace**

文字列から特定のサブストリングをすべて別の文字列に置換します。

**コード**

```
{{ 'Hello, Dave. How are you, Dave?' | replace: 'Dave', 'John' }}
```

**出力**

```
Hello, John. How are you, John?
```

### <a name="replace_first"></a>**replace\_first**

文字列から最初の特定のサブストリングを別の文字列に置換します。

**コード**

```
{{ 'Hello, Dave. How are you, Dave?' | replace_first: 'Dave', 'John' }}
```

**出力**

```
Hello, John. How are you, Dave?
```

### <a name="split"></a>**split**

split フィルタは、サブストリングをパラメーターとして受け取ります。 そのサブストリングは、文字列を配列に分割する際の区切り文字として使用されます。

**コード**

```
{% assign words = This is a demo of the split filter | split: ' ' %}

First word: {{ words.first }}

First word: {{ words[0] }}

Second word: {{ words[1] }}

Last word: {{ words.last }}

All words: {{ words | join: ', ' }}
```

**出力**

```
First word: This

First word: This

Second word: is

Last word: filter

All words: This, is, a, demo, of, the, split, filter
```

### <a name="strip_html"></a>**strip\_html**

文字列のすべての HTML タグを除去します。

**コード**

```
<p>Hello</p>
```

**出力**

```
Hello
```

### <a name="strip_newlines"></a>**strip\_newlines**

文字列からすべての改行を除去します。

**コード**

```
{% capture text %}

A

B

C

{% endcapture %}

{{ text | strip_newlines }}
```

**出力**

```
ABC
```

### <a name="text_to_html"></a>**text\_to\_html**

プレーン テキストを単純な HTML として整形します。 すべてのテキストが HTML にエンコードされます。改行で区切られたテキストのブロックは、パラグラフ タグ &lt;p&gt; で囲われます。単一の改行は &lt;br&gt; に置換されます。URL はハイパーリンクに変換されます。

**コード**

```
{{ note.notetext | text_to_html }}
```

**出力**

```
<p>This is the first paragraph of notetext. It contains a URL: <a href="http://example.com/" rel="nofollow">http://example.com</a></p>

<p>This is a second paragraph.</p>
```

### <a name="truncate"></a>**truncate**

文字列を指定された文字数で切り出します。 省略記号 (...) が文字列に付けられ、これも文字数に含まれます。

**コード**

```
{{ 'This is a long run of text.' | truncate: 10 }}
```

**出力**

```
This is...
```

### <a name="truncate_words"></a>**truncate\_words**

文字列を指定された単語数で切り出します。 切り出した文字列には省略記号 (...) が付けられます。

**コード**

```
{{ 'This is a long run of text.' | truncate_words: 3 }}
```

**出力**

```
This is a...
```

### <a name="upcase"></a>**upcase**

文字列を大文字に変換します。

**コード**

```
{{ 'MIxed Case TExt' | upcase }}
```

**出力**

```
MIXED CASE TEXT
```

### <a name="url_escape"></a>**url\_escape**

文字列を URL エスケープして、URL として含められるようにします。

**コード**

```
{{ 'This & that//' | url_escape }}
```

**出力**

```
This+%26+that%2F%2F
```

### <a name="xml_escape"></a>**xml\_escape**

文字列を XML エスケープして、XML 出力の中で使用できるようにします。

**コード**

```
{{ '<p>test</p>' | xml_escape }}
```

**出力**

```
&lt;p&gt;test&lt;/p&gt;
```


## <a name="type-filters"></a>フィルターの入力

型のフィルターにより、ある型の値を他の型の値に変換することができます。

### <a name="boolean"></a>**boolean**

文字列値をブール値に変換しようとします。 この値がすでにブール値である場合は、変更されずに返されます。 値がブール値に変換できない場合は、null が返されます。

また、このフィルターは"on"、"有効化"、または "はい" を "true" として、"off"、"無効"、および "いいえ" を "false" として受け取ります。

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

### <a name="decimal"></a>**decimal**

文字列値を 10 進数に変換しようとします。 この値がすでに 10 進数である場合は、変更されずに返されます。 値が 10 進数に変換できない場合は、null が返されます。

**コード**

```
{{ 10.1 | decimal }}

{{ '3.14' | decimal }}

{{ 'text' | decimal | default: 3.14 }}
```

**出力**

```
10.1

3.14

3.14
```

### <a name="integer"></a>**integer**

文字列値を整数に変換しようとします。 この値がすでに整数である場合は、変更されずに返されます。 値が整数に変換できない場合は、null が返されます。

**コード**

```
{{ 10 | integer }}

{{ '10' | integer }}

{{ '10.1' | integer }}

{{ 'text' | integer | default: 2 }}
```

**出力**

```
10

10


2
```

### <a name="string"></a>**string**

値を文字列に変換しようとします。 この値がすでに文字列である場合は、変更されずに返されます。 値が null である場合、null 値が返されます。



## <a name="url-filters"></a>URL フィルター

URL フィルターにより、URL の一部の構築または抽出ができます。

### <a name="add_query"></a>**add\_query**

URL にクエリ文字列パラメーターを追加します。 URL にパラメーターが既に存在する場合は、パラメーター値が更新されます。

このフィルターが完全な絶対 URL に適用される場合、更新された絶対 URL が結果です。 パスに適用される場合、更新されたパスが結果です。

**コード**

```
{{ 'http://example.com/path?page=1' | add_query: 'foo', 'bar' }}

{{ '/path?page=1' | add_query: 'page', 2 }}
```

**出力**

```
http://example.com/path?page=1&foo=bar

/path?page=2
```

### <a name="base"></a>**base**

指定された URL のベース URL を取得します。

**コード**

```
{{ 'http://example.com/path?foo=bar&page=2' | base }}
```

**出力**

```
http://example.com
```

### <a name="host"></a>**host**

URL のホスト パーツを取得します。

**コード**

```
{{ 'http://example.com/path?foo=bar&page=2' | host }}
```

**出力**

```
example.com
```

### <a name="path"></a>**path**

URL のパス パーツを取得します。

**コード**

```
{{ 'http://example.com/path?foo=bar&page=2' | path }}

{{ '/path?foo=bar&page=2' | path }}
```

**出力**

```
/path

/path
```

### <a name="path_and_query"></a>**path\_and\_query**

URL のパスとクエリ パーツを取得します。

**コード**

```
{{ 'http://example.com/path?foo=bar&page=2' | path_and_query }}

{{ '/path?foo=bar&page=2' | path_and_query }}
```

**出力**

```
/path?foo=bar&page=2

/path?foo=bar&page=2
```

### <a name="port"></a>**port**

URL のポート番号を取得します。

**コード**

```
{{ 'http://example.com/path?foo=bar&page=2' | port }}

{{ 'https://example.com/path?foo=bar&page=2' | port }}

{{ 'https://example.com:9000/path?foo=bar&page=2' | port }}
```

**出力**

```
80

443

9000
```

### <a name="remove_query"></a>**remove\_query**

URL からクエリ文字列パラメーターを削除します。 URL にパラメーターが存在しない場合、URL は変更されずに返されます。

このフィルターが完全な絶対 URL に適用される場合、更新された絶対 URL が結果です。 パスに適用される場合、更新されたパスが結果です。

**コード**

```
{{ 'http://example.com/path?page=1' | remove_query: 'page' }}

{{ '/path?page=1' | remove_query: 'page' }}
```

**出力**

```
http://example.com/path

/path
```

### <a name="scheme"></a>**scheme**

URL のスキーム パーツを取得します。

**コード**

```
{{ 'http://example.com/path?foo=bar&page=2' | scheme }}

{{ 'https://example.com/path?foo=bar&page=2' | scheme }}
```

**出力**

```
http

https
```


## <a name="additional-filters"></a>追加フィルター

これらのフィルターは便利な一般的機能を提供します。

### <a name="default"></a>**default**

割り当てられた値 (例 null) なしで、すべての変数の既定値を返します

**コード**

```
{{ snippets[Header] | default: 'My Website' }}
```

**出力**

```
<!-- If a snippet with the name Header returns null -->

My Website
```

### <a name="file_size"></a>**file\_size**

バイト数を表わしている数値に適用され、適切なスケール単位で書式設定されたファイルの数を返します。

オプションでは、結果における小数点以下の桁数を管理するために、詳細な precision パラメーターを渡すことができます。 既定の precision は 1 です。

**コード**

```
{{ 10000000 | file_size }}

{{ 2050 | file_size: 0 }}

{{ entity.notes.first.filesize | file_size: 2 }}
```

**出力**

```
9.5 MB

2 KB

207.14 KB
```

### <a name="has_role"></a>**has\_role**

[ユーザー](liquid-objects.md#user) に適用され、ユーザーが指定されたロールに属している場合は true を返します。 そうではない場合、false が返されます。  

**コード**

```
{% assign is_admin = user | has_role: 'Administrators' %}

{% if is_admin %}

User is an administrator.

{% endif %}
```

### <a name="liquid"></a>**liquid**

流動コードとして文字列を表示します。 このコードは現在の流動実行コンテキスト (変数など) にアクセスできます。

> [!Note] 
> このフィルターは注意して使用する必要があり、一般的に、ポータル コンテンツの作成者または流動コードを記述する信頼できるその他のユーザーの排他的管理下にある値のみが適用されます。

**コード**

```
{{ page.adx_copy | liquid }}
```

### <a name="see-also"></a>関連項目

[Web テンプレートを使用したソース コンテンツの保存](store-content-web-templates.md)  
[Liquid の演算子の認識](liquid-operators.md) 
[Liquid の種類](liquid-types.md)  
[Liquid オブジェクト](liquid-objects.md)  
[Liquid タグ](liquid-tags.md)  
[Liquid フィルター](liquid-filters.md)  
