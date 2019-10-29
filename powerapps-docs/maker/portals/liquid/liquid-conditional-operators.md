---
title: ポータルに液体の条件演算子を使用する |MicrosoftDocs
description: ポータルで使用できる液体条件演算子について説明します。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: def132ebc0f8ef93121b10b221479a2452a1d4fb
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/11/2019
ms.locfileid: "72975014"
---
# <a name="available-liquid-conditional-operators"></a>使用可能な液体条件演算子

条件付きステートメントで使用する場合 (の**場合**を**除く**)、一部の液体値は true として扱われ、一部は false として扱われます。

液体では、null とブール値 false が false として扱われます。それ以外のすべての値は true として扱われます。 空の文字列、空の配列などは、true として扱われます。 例を示します。

```
{% assign empty_string =  %}
{% if empty_string %}
<p>This will render.</p>
{% endif %}
```
必要に応じて、特別な値を空にして、空の文字列と配列をテストできます。

```
{% unless page.title == empty %}
<h1>{{ page.title }}</h1>
{% endunless %}
```
特殊サイズプロパティを使用して、[液体の種類](liquid-types.md)、液体の[種類](liquid-types.md)、または液体の[種類](liquid-types.md)のサイズをテストすることもできます。

```
{% if page.children.size > 0 %}
<ul>
{% for child in page.children %}
<li>{{ child.title }}</li>
{% endfor %}
</ul>
{% endif %}
```

## <a name="summary"></a>まとめ

|                           | True | False |
|---------------------------|------|-------|
| True                      | ×    |       |
| False                     |      | ×     |
| 空白                      |      | ×     |
| String                    | ×    |       |
| 空の文字列              | ×    |       |
| 0                         | ×    |       |
| 1、3.14                   | ×    |       |
| 配列またはディクショナリ       | ×    |       |
| 空の配列またはディクショナリ | ×    |       |
| 素材                    | ×    |       |

### <a name="see-also"></a>関連項目

[Web テンプレートを使用してソースコンテンツを保存する](store-content-web-templates.md)  
[冷却演算子について](liquid-operators.md)  
[液体の種類](liquid-types.md)  
[液体オブジェクト](liquid-objects.md)  
[液体タグ](liquid-tags.md)  
[液体フィルター](liquid-filters.md)  
