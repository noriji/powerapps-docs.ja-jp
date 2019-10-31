---
title: ポータルで変数タグを使用する | MicrosoftDocs
description: ポータルで使用可能な変数タグについて説明します
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: null
ms.date: 08/30/2019
ms.author: shjais
ms.reviewer: null
---

# <a name="variable-tags"></a>変数タグ

変数タグは、新しい Liquid 変数の作成に使用されます。

## <a name="assign"></a>割り当て

新しい変数を作成します。 また、割り当ては[フィルター](liquid-filters.md)を使用して値を変更することができます。  

**コード**

```
{% assign is_valid = true %}

{% if is_valid %}

It is valid.

{% endif %}

{% assign name = dave bowman' | upcase %}

{{ name }}
```

**出力**

```
It is valid.

DAVE BOWMAN
```

## <a name="capture"></a>取得

ブロック内のコンテンツを取得し、変数に割り当てます。 このコンテンツは、出力タグを使用して後で表示できます。

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

[制御フロー タグ](control-flow-tags.md)<br>
[反復タグ](iteration-tags.md)<br>
[テンプレート タグ](template-tags.md)<br>
[PowerApps common data service エンティティ タグ](portals-entity-tags.md)
