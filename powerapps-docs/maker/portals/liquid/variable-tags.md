---
title: ポータルに変数タグを使用する |MicrosoftDocs
description: ポータルで使用できる可変タグについて説明します。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: fa375909ad3e909e70b3477d4e7ba0f24691fc0c
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/11/2019
ms.locfileid: "72974416"
---
# <a name="variable-tags"></a>変数タグ

変数タグは、新しい液体変数を作成するために使用されます。

## <a name="assign"></a>割り当てる

新しい変数を作成します。 割り当てでは、[フィルター](liquid-filters.md)を使用して値を変更することもできます。  

**コード**

```
{% assign is_valid = true %}

{% if is_valid %}

It is valid.

{% endif %}

{% assign name = dave bowman' | upcase %}

{{ name }}
```

**Output**

```
It is valid.

DAVE BOWMAN
```

## <a name="capture"></a>占領

ブロック内のコンテンツをキャプチャし、変数に割り当てます。 このコンテンツは、後で出力タグを使用して表示できます。

**コード**

```
{% capture hello %}Hello, {{ user.fullname }}.{% endcapture %}

{{ hello }}

{{ hello }}
```

**Output**

```
Hello, DAVE BOWMAN.

Hello, DAVE BOWMAN.
```

### <a name="see-also"></a>関連項目

[制御フロータグ](control-flow-tags.md)<br>
[イテレーションタグ](iteration-tags.md)<br>
[テンプレートタグ](template-tags.md)<br>
[PowerApps common data service エンティティタグ](portals-entity-tags.md)
