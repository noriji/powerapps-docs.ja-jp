---
title: ポータル用 Liquid の条件演算子を使用する | MicrosoftDocs
description: ポータルで使用可能な Liquid の条件演算子について説明します。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: null
ms.date: 08/30/2019
ms.author: shjais
ms.reviewer: null
---

# <a name="available-liquid-conditional-operators"></a>使用可能な Liquid の条件演算子

条件付きステートメント (**if**、**unless**) で使用される流動値の一部は true として扱われ、一部は false として扱われます。

Liquid では、null およびブール値 false は false として扱われ、他のすべては true として扱われます。 空の文字、空の配列などは true として扱われます。 たとえば、

```
{% assign empty_string =  %}
{% if empty_string %}
<p>This will render.</p>
{% endif %}
```
特殊空の値を必要に応じて使用し、空の文字列および空の配列に対してテストできます。

```
{% unless page.title == empty %}
<h1>{{ page.title }}</h1>
{% endunless %}
```
また、特殊サイズプロパティを使用して [Liquid の種類](liquid-types.md)、[Liquid の種類](liquid-types.md) あるいは [Liquid の種類](liquid-types.md) のサイズもテストできます。

```
{% if page.children.size > 0 %}
<ul>
{% for child in page.children %}
<li>{{ child.title }}</li>
{% endfor %}
</ul>
{% endif %}
```

## <a name="summary"></a>概要

|                           | 正 | 誤 |
|---------------------------|------|-------|
| 正                      | ×    |       |
| 誤                     |      | ×     |
| Null                      |      | ×     |
| 文字列                    | ×    |       |
| 空の文字列              | ×    |       |
| 0                         | ×    |       |
| 1、3.14                   | ×    |       |
| 配列またはディクショナリ       | ×    |       |
| 空の配列またはディクショナリ | ×    |       |
| オブジェクト                    | ×    |       |

### <a name="see-also"></a>関連項目

[Web テンプレートを使用したソース コンテンツの保存](store-content-web-templates.md)  
[Liquid の演算子の認識](liquid-operators.md)  
[Liquid の種類](liquid-types.md)  
[Liquid オブジェクト](liquid-objects.md)  
[Liquid タグ](liquid-tags.md)  
[Liquid フィルター](liquid-filters.md)  
