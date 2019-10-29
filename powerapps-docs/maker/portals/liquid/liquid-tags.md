---
title: ポータルに液体タグを使用する |MicrosoftDocs
description: ポータルで使用可能な液体タグについて説明します。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: b04c6447911d1a884627bd2cbb4ad7b74b9c5ce5
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/11/2019
ms.locfileid: "72976555"
---
# <a name="available-liquid-tags"></a>使用可能な液体タグ

タグは、テンプレートに対して実行する操作を指示するプログラミングロジックを構成します。 タグは {%%} にラップされています。

```
{% if user.fullname == 'Dave Bowman' %} Hello, Dave. {% endif %}
```

## <a name="whitespace-control"></a>空白コントロール

通常、液体は変数とタグブロックの外側のすべてをそのままで、すべての空白をそのままレンダリングします。 余分な空白を必要としない場合もありますが、テンプレートをきれいに書式設定する必要があります。これには空白が必要です。

開始または終了ブロックタグにハイフン (-) を追加することで、すべての先頭または末尾の空白を除去するようにエンジンに指示できます。

**コード**

```
{% for i in (1..5) --%}

{{ i }}

{%-- endfor %}
```

**Output**

```
12345
```
### <a name="see-also"></a>関連項目

[液体の種類](liquid-types.md)  
[液体オブジェクト](liquid-objects.md)  
[液体フィルター](liquid-filters.md) 
