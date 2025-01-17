---
title: ポータルの条件付きステップの種類を構成する |MicrosoftDocs
description: ポータルの条件付きステップの種類を追加および構成する手順。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: ec3e568b239bf66c0d4554e244d5afef2d5ef673
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2019
ms.locfileid: "73553672"
---
# <a name="add-a-conditional-step-type"></a>条件付きステップの種類を追加する

Web フォームステップは、ステップで式を評価する必要があることを示す "条件" 型にすることができます。 式が true に評価されると、次の手順が表示されます。 式が false と評価され、"次のステップの条件に失敗しました" が指定されている場合、その手順が表示されます。 現在のエンティティは、式の評価に使用されるターゲットです。 レコードソースの既定値は、前の手順のレコードソースになります。

## <a name="attributes"></a>属性

| 名前                         | Description                                                                                                                                                                                                                          |
|------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| フィルター                    | 評価する条件式                                                                                                                                                                                           |
| 条件に失敗した場合の次のステップ | 条件付きステップの種類は、他の条件とは異なり、次の2つのステップの参照を持ちます。 既定の次のステップ参照は、条件が true と評価された場合に尊重されます。 このプロパティは、条件が false と評価される次のステップを設定します。 |

使用可能なオペランドは次のとおりです。

| オペランド    | 種類                   |
|---------------|------------------------|
| =, ==         | str                 |
| !=            | 等しくない             |
| &gt;          | より大きい           |
| &lt;          | より小さい              |
| &gt;=         | 以上 |
| &lt;=         | 以下    |
| &             | And                    |
| \|             | Or                     |
| !             | Not                    |
| =\*、= =\*、-= | という感じで                   |
| ! =\*          | 次のものに等しくない               |

## <a name="format"></a>形式

式の形式は次のとおりです。

\[エンティティ属性の論理名\] \[オペランド\] \[値\]

例:

新しい\_カテゴリコード = 750101

条件には複数の式を含めることができます。 かっこを使用して、入れ子になった式をグループ化することができます。次に例を示します。

新しい\_カテゴリコード = 750101 & gendercode = 2

-   新しい\_カテゴリコード = 750101 & (gendercode = 2 | gendercode = 3)

-   新しい\_名 = Jane Doe

-   new\_の両方のオプションフィールド = true

-   new\_true optionfield = false

### <a name="see-also"></a>関連項目

[ポータルの構成](configure-portal.md)  
[エンティティフォームの定義](entity-forms.md)  
[ポータルの Web フォームの手順](web-form-steps.md)  
[フォームの読み込み/読み込みタブのステップの種類](load-form-step.md)  
[リダイレクトステップの種類](add-redirect-step.md)  
[カスタム JavaScript の追加](add-custom-javascript.md)  

