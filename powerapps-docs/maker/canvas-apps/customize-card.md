---
title: Canvas アプリでカードをカスタマイズする |Microsoft Docs
description: キャンバスアプリの詳細または編集フォームでカードに表示される既定のコントロールを変更する
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 03/18/2018
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 5bcf1515f72bdce0872f91c64b5ac4fe5028ee2c
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/07/2019
ms.locfileid: "71985914"
---
# <a name="customize-a-card-in-a-canvas-app"></a>キャンバスアプリでカードをカスタマイズする

基本的なカスタマイズ (カードのロック解除を伴わないカスタマイズ) は、コントロールの変更などによって行います。 高度なカスタマイズは、カードのロックを解除し、既定では利用できないコントロールをカードに追加するなどして行います。

概要については、「[Understand data cards (データ カードについて)](working-with-cards.md)」をご覧ください。

## <a name="prerequisites"></a>前提条件

- [コントロールを追加して構成](add-configure-controls.md)する方法について学ぶ。
- このトピックは、一般的な概念についてのみ確認できます。また、次のトピックの手順を最初に完了した場合は、手順に従って操作することもできます。

    1. [アプリを生成します](data-platform-create-app.md)。
    1. [そのギャラリーをカスタマイズします](customize-layout-sharepoint.md)。
    1. [フォームをカスタマイズします](customize-forms-sharepoint.md)。

## <a name="customize-a-locked-card"></a>ロックされたカードのカスタマイズ

この手順では、カードのロックを解除せずに、 **[テキスト入力](controls/control-text-input.md)** コントロールを **[スライダー] (コントロール/コントロールスライダーの md**コントロール) に置き換えます。

1. 生成してカスタマイズしたアプリで、左側のナビゲーションバーの **[EditForm1]** を選択し、右側のウィンドウの **[プロパティ]** タブで **[フィールドの編集]** を選択します。

1. フィールドの一覧で、 **[Number Of Employees]** の下矢印を選択し、 **[コントロールの種類]** の下の一覧を開きます。

    > [!div class="mx-imgBorder"]
    > 数値カードのオプションのドロップダウンリスト ![](./media/customize-card/card-selector.png)

1. **[スライダーの編集]** を選択します。

    画面に変更内容が反映されます。

    > [!div class="mx-imgBorder"]
    > スライダーコントロールを使用した EditForm1 の ![](./media/customize-card/add-slider.png)

## <a name="unlock-and-customize-a-card"></a>カードのロック解除とカスタマイズ

この手順では、カードのロックを解除し、追加した**スライダー**コントロールの**Max**プロパティを更新します。

1. **EditForm1**で、 **Employees カードの数**の**スライダー**コントロールを選択します。

    > [!div class="mx-imgBorder"]
    > ![スライダーを選択し](./media/customize-card/select-slider.png)

1. 右側のウィンドウの **[詳細設定]** タブで、ロックアイコンを選択してカードのロックを解除します。

    > [!div class="mx-imgBorder"]
    > カードのロック解除 ![](./media/customize-card/lock-icon.png)

1. **スライダー**コントロールの**Max**プロパティを1万に設定します。

    > [!div class="mx-imgBorder"]
    > [詳細設定] タブの [最大 ![] プロパティ](./media/customize-card/max-property.png)

    **スライダー**コントロールにより、より正確な値が表示されます。

    > [!div class="mx-imgBorder"]
    > ![スライダーの範囲: 0 ~ 10000](./media/customize-card/final-slider.png)

## <a name="next-steps"></a>次の手順

これでアプリを生成し、ギャラリー、フォーム、カードをカスタマイズする方法の基礎を理解したので、[独自のアプリを新規に作成する](data-platform-create-app-scratch.md)ことができます。