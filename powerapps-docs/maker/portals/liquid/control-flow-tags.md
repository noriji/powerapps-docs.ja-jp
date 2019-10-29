---
title: ポータルに制御フロータグを使用する |MicrosoftDocs
description: ポータルで使用できる制御フロータグについて説明します。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 77fcc7db0adf68cd6decbcc95e11d8e803761535
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/11/2019
ms.locfileid: "72975106"
---
# <a name="control-flow-tags"></a>制御フロー タグ

制御フロータグは、実行する必要があるコードのブロックと、特定の条件に基づいてどのようなコンテンツをレンダリングする必要があるかを決定します。 条件は、使用可能な[液体演算子](liquid-operators.md)を使用して構築されるか、または[指定された値の真または](liquid-conditional-operators.md)すべてに基づいて作成されます。  

## <a name="if"></a>もし

特定の条件が満たされた場合に、コードのブロックを実行します。

```
{% if user.fullname == 'Dave Bowman' %}

Hello, Dave.

{% endif %}
```

## <a name="unless"></a>だけ

If の場合と同様に、特定の条件が満たされ**ない**場合にコードのブロックが実行される点が異なります。

```
{% unless page.title == 'Home' %}

This is not the Home page.

{% endunless %}
```

## <a name="elsifelse"></a>elsif/else

If ブロックまたは block 以外の条件を追加します。

```
{% if user.fullname == 'Dave Bowman' %}

Hello, Dave.

{% elsif user.fullname == 'John Smith' %}

Hello, Mr. Smith.

{% else %}

Hello, stranger.

{% endif %}
```

## <a name="casewhen"></a>case/when

変数を別の値と比較し、値ごとに異なるコードブロックを実行する switch ステートメント。

```
{% case user.fullname %}

{% when 'Dave Bowman' %}

Hello, Dave.

{% when 'John Smith' %}

Hello, Mr. Smith.

{% else %}

Hello, stranger.

{% endcase %}
```

### <a name="see-also"></a>関連項目

[イテレーションタグ](iteration-tags.md)<br>
[可変タグ](variable-tags.md)<br>
[テンプレートタグ](template-tags.md)<br>
[PowerApps common data service エンティティタグ](portals-entity-tags.md)
