---
title: ルールの作成 | Microsoft Docs
description: ルールを作成してアプリ ロジックを構築するための詳しい手順
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/23/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: d104bc88fb8f5306a9d086fa04bc946b6a719129
ms.sourcegitcommit: c3e7be17c8b39bf17b2089ad3bd424e63b5645e5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/24/2019
ms.locfileid: "72822100"
---
# <a name="create-a-rule-in-canvas-apps"></a>キャンバスアプリでルールを作成する
指定した条件に基づいてアプリを自動的に変更するためのルールを作成します。 たとえば、状態に基づいてリスト項目を赤、黄、または緑で表示したり、特定のユーザー (管理者など) に対してのみ承認ボタンを表示したりします。 ルールは、さまざまなコントロールに追加できます。 このトピックでは、**スライダー** コントロールの値が 70 を超えている場合に、**ラベル**のテキストの色を変更するルールを追加します。

> [!IMPORTANT]
> 2019年10月14日より、キャンバスアプリのルール機能は非推奨となりました。 詳細については、「[ブログ: キャンバスルール機能の廃止](https://powerapps.microsoft.com/blog/canvas-rules-feature-deprecation/)」を参照してください。

## <a name="add-a-rule"></a>ルールの追加
1. コントロールを選択します (またはコントロールを追加し、選択されたままにします)。

    このトピックでは、[ラベルとスライダーを追加](add-configure-controls.md)して、ラベルの **Text** プロパティを **Slider1.Value** に設定し、スライダーを選択します。

1. 右側のパネルで、 **[ルール]** をクリックまたはタップして、 **[新しいルール]** をクリックまたはタップします。

    ![新しいルールの作成](./media/working-with-rules/new-rule.png)

    1 つまたは複数のルールが既に定義されているコントロールを選択すると、クリックまたはタップで、それらのうちのどれでも編集することができます。  

## <a name="add-a-condition"></a>条件の追加
条件とは、true または false を評価する式です (値が 70 を超えているかどうかなど)。 テンプレートに基づいて、または最初から式を記述して、UI (Intellisense) のガイダンスに基づいて式をカスタマイズできます。

1. **[条件の追加]** をクリックまたはタップして、テンプレートをクリックするか、または **[ユーザー設定条件]** をクリックします。

    このトピックでは、 **[次の値より大きい]** をクリックまたはタップします。

    ![条件の追加](./media/working-with-rules/rule-conditions.png)

1. どのような場合にルールを適用するかを定義する式を更新します。

    このトピックでは、この式が取る値を 0 から 70 に変更します。 <br>**Slider1.Value > 70**

## <a name="add-an-action"></a>アクションの追加
アクションは、ルールが適用されたときの動作を定義します。 PowerApps では、コントロールに加えた変更に基づいて、自動的にアクションを作成できます。

1. **[アクションの定義]** をクリックまたはタップします。

    ![アクションの定義](./media/working-with-rules/rule-define-actions.png)

1. 確認ダイアログ ボックスで **[始めましょう]** をクリックまたはタップして、PowerApps で次の変更を 1 つまたは複数のアクションとしてキャプチャできるようにします。

1. 条件が true のときに希望通りに動作するように、1 つまたは複数のコントロールを構成します。

    このトピックでは、ラベルの色を変更します。

    ![プロパティのキャプチャ](./media/working-with-rules/rule-capture-properties.png)

1. (省略可能) **[アクションの表示]** をクリックまたはタップして、変更を確認します。

    ![アクションの確認](./media/working-with-rules/rule-review-actions.png)

1. アクションの追加が完了したら、 **[完了]** をクリックまたはタップします。

1. ルールの条件とアクションを確認します。

    ![ルールの確認](./media/working-with-rules/rule-review.png)

## <a name="rename-the-rule"></a>ルール名の変更

1. **[Rule1]** をポイントし、[編集] ボタンをクリックまたはタップします。

    ![ルール名のポイント](./media/working-with-rules/hover-over-rules_name.png)

1. ルールの新しい名前を入力します。

    ![ルール名の変更](./media/working-with-rules/rename-rule.png)

1. **[完了]** をクリックまたはタップしてエディターを閉じます。

## <a name="test-the-rule"></a>ルールのテスト
1. F5 キーを押して (または右上隅の再生ボタンをクリックして) アプリをプレビューします。

    ![プレビューを開く](./media/working-with-rules/open-preview.png)

1. true に指定した条件を作成し、アクションが希望通りに動作することを確認します。

    このトピックでは、スライダーを 70 よりも大きい値に設定して、ラベルのテキストの色が変わることを確認します。

## <a name="see-all-rules"></a>すべてのルールの表示
既定では、 **[ルール]** タブでは、ルールの条件またはルールのアクションで選択したコントロールおよび使用されているすべての子コントロールのルールのみが表示されます。 アプリですべてのルールを表示するには、 **[このコントロールのルールのみを表示する]** チェック ボックスをオフにします。

![フィルターの削除](./media/working-with-rules/rules-filter.png)

## <a name="known-limitations"></a>既知の制限
この記事の執筆時点では、次のものがあります。

* 条件の一部として、フォームまたはギャラリーの **ThisItem** プロパティを指定することはできません。
