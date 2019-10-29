---
title: ポータルでの液体演算子の使用 |MicrosoftDocs
description: ポータルで使用可能な液体演算子について説明します。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 4a27a5364a4ae12fecc3a72dbb52115e415dcdb8
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/11/2019
ms.locfileid: "72976532"
---
# <a name="understand-liquid-operators"></a>液体演算子について

液体は、すべての一般的な論理演算子と比較演算子にアクセスできます。 これら**は、など**のタグで使用できます **。**

## <a name="basic-operators"></a>基本的な演算子

| ==    | str                          |
|-------|---------------------------------|
| !=    | 等しくない                  |
| &gt;  | 超                    |
| &lt;  | 未満                       |
| &gt;= | 以上        |
| &lt;= | 以下           |
| または    | 条件 A **or**条件 B  |
| そして   | 条件 A**および**条件 B |

## <a name="contains"></a>は

文字列内に部分文字列が存在するかどうかのテストを含みます。

```
{% if page.title contains 'Product' %}

The title of this page contains the word Product.

{% endif %}
```

contains は、文字列の配列内に文字列が存在するかどうかをテストすることもできます。

## <a name="startswith"></a>startswith

startswith は、文字列が特定の部分文字列で始まるかどうかをテストします。

```
{% if page.title startswith 'Profile' %}

This is a profile page.

{% endif %}
```

## <a name="endswith"></a>endswith

endswith は、文字列が特定の部分文字列で終わるかどうかをテストします。

```
{% if page.title endswith 'Forum' %}

This is a forum page.

{% endif %}
```

### <a name="see-also"></a>関連項目

[Web テンプレートを使用してソースコンテンツを保存する](store-content-web-templates.md)  
[液体の種類](liquid-types.md)  
[付](liquid-conditional-operators.md)  
[液体オブジェクト](liquid-objects.md)  
[液体タグ](liquid-tags.md)  
[液体フィルター](liquid-filters.md) 