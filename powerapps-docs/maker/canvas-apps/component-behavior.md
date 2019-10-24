---
title: コンポーネントの動作の数式 |Microsoft Docs
description: コンポーネントベースのアクションが発生したときに1つ以上のタスクを実行するようにアプリをトリガーします。
author: yifwang
ms.service: powerapps
ms.topic: article
ms.date: 9/30/2019
ms.author: yifwang
ms.reviewer: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: baf7e74581819b3ea21542f30f96a0a6f517c0d5
ms.sourcegitcommit: 57b968b542fc43737330596d840d938f566e582a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2019
ms.locfileid: "71705043"
---
# <a name="behavior-formulas-for-components"></a>コンポーネントの動作に関する数式

> [!IMPORTANT]
> この機能は引き続き試験段階であり、既定では無効になっています。 詳細については、「[試験機能とプレビュー機能](working-with-experimental.md)」を参照してください。

イベントによってコンポーネントインスタンスの変更がトリガーされたときに実行される1つまたは複数の[動作の数式](working-with-formulas-in-depth.md)を指定します。 たとえば、コンポーネントの**onreset**プロパティを、コンポーネントインスタンスで**reset**関数を実行したときに、初期化を実行し、入力をクリアし、値をリセットする1つ以上の数式に設定します。

## <a name="onreset"></a>OnReset

コンポーネントマスターを選択した状態で、プロパティのドロップダウンリスト (数式バーの左側) で **[Onreset]** を選択し、1つまたは複数の数式を入力します。

> [!div class="mx-imgBorder"]
> ![OnReset の例 ](./media/component-behavior/example-onreset.png)

**Onreset**をテストするには、コンポーネントをリセットするようにコントロールを構成します。 たとえば、ボタンの**Onselect**プロパティを「 **Reset**(*ComponentName*)」という数式に設定します。

### <a name="example---reset-timer"></a>例-タイマーのリセット

> [!div class="mx-imgBorder"]
> ![OnReset の例 ](./media/component-behavior/Resettimer.gif)

このタイムピッカーコンポーネントでは、時刻の表示に2つの変数が使用されています。 ピッカーがリセットされたら、これらの変数を既定値にリセットします (たとえば、12:12)。  コンポーネントの OnReset プロパティには、次の式があります。 **Set (selec、12)。設定 (_ 分、12)**

リセットをトリガーするには、画面にアクセスし、コンポーネントのインスタンスを挿入します。 ボタンを追加し、 **reset (TimerComponent_instance)** を呼び出して onselect をトリガーするボタンの onselect を構成します。

> [!div class="mx-imgBorder"]
> ![Reset ボタン ](./media/component-behavior/reset-button.png)

## <a name="update-onreset-using-custom-property"></a>カスタムプロパティを使用して OnReset を更新する

コンポーネントの外部からコンポーネントインスタンスをリセットするだけでなく、内部から OnReset をトリガーするもう1つの方法もあります。 "**値の変更時に OnReset を発生させる**" は、カスタム入力プロパティを作成するときのオプションです。このプロパティの値を変更して、コンポーネントの onreset をトリガーすることができます。 このメソッドは、既定値を簡単に設定およびリセットするように設計されています。 

> ![OnReset の例](./media/component-behavior/property-trigger.png)

### <a name="example"></a>例

> [!div class="mx-imgBorder"]
> ![OnReset の例 ](./media/component-behavior/updateordernumber2.gif)

ここでは、注文番号を確認し、数値を更新する例を示します。 数値の上下のコンポーネントは、注文の数を増減するために使用されます。 左側のギャラリーを選択すると、既定の数値の上下のコンポーネントがリセットされ、選択したツールの順序番号が表示されます。 "**値の変更時に OnReset を発生させる" と**、入力の変更時に既定値をリセットできるようになりました。 

これを行うには、"既定の入力" プロパティの [値が変更され**たときに OnReset を発生させる**] チェックボックスをオンにします。 コンポーネントの**Onreset**が設定されるように設定されてい**ます (値は ' Numeric Up down ')。DefaultValue)** 。 Numericvalue は、現在の順序の値を格納する変数です。 テキスト入力コントロールの**既定値**を**If (Isblank ((numericvalue), ' Numeric up down ') に設定します。DefaultValue、Numericvalue)** 。 
