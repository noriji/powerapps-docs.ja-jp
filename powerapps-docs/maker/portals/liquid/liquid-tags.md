---
title: ポータルの Liquid タグを使用する | MicrosoftDocs
description: ポータルで使用可能な Liquid のタグについて説明します。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: null
ms.date: 08/30/2019
ms.author: shjais
ms.reviewer: null
---

# <a name="available-liquid-tags"></a>使用可能な Liquid タグ

タグは、実行すべき処理をテンプレートに伝えるプログラミング ロジックを構成しています。 タグは、{% %} にパッケージ化されています。

```
{% if user.fullname == 'Dave Bowman' %} Hello, Dave. {% endif %}
```

## <a name="whitespace-control"></a>空白スペースのコントロール

Liquid は通常、現状のままのすべての空白スペースと共に、変数や各タグ ブロックを除くすべての文字を表示します。 余分な空白スペースが必要ではない場合もありますが、適切にテンプレートを作成したいなら、空白スペースが必要となります。

開始ブロック タグや終了ブロック タグにハイフン (-) を追加することによって、先頭および末尾のすべての空白スペースの削除をエンジンに通知できます。

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

[Liquid の種類](liquid-types.md)  
[Liquid オブジェクト](liquid-objects.md)  
[Liquid フィルター](liquid-filters.md) 
