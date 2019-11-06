---
title: 'トグル コントロール: リファレンス | Microsoft Docs'
description: 各種プロパティとサンプルを含むトグル コントロールに関する情報です
author: chmoncay
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/25/2016
ms.author: chmoncay
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: be21e2b0c24d7b4aaf9da12b0793899fd95acd06
ms.sourcegitcommit: 8e42a5996799d9831f8c5a52b0b051a6088d9ce7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/06/2019
ms.locfileid: "73649805"
---
# <a name="toggle-control-in-powerapps"></a>PowerApps のトグル コントロール
ユーザーがハンドルを動かすことでオンまたはオフにできるコントロールです。

## <a name="description"></a>Description
トグルは最近の GUI 向けのデザインですが、動作はチェック ボックスと同じです。

## <a name="key-properties"></a>主要なプロパティ
**[Default](properties-core.md)** – ユーザーが変更する前のコントロールの初期値です。

**[Value](properties-core.md)** – 入力コントロールの値です。

## <a name="additional-properties"></a>その他のプロパティ
**[AccessibleLabel](properties-accessibility.md)** – スクリーン リーダー用のラベルです。

**[BorderColor](properties-color-border.md)** – コントロールの境界線の色です。

**[BorderStyle](properties-color-border.md)** – コントロールの境界線を **Solid** (実線)、**Dashed** (破線)、**Dotted** (点線)、**None** (なし) のいずれに指定します。

**[BorderThickness](properties-color-border.md)** – コントロールの境界線の太さです。

**[DisplayMode](properties-core.md)** – コントロールで、ユーザー入力を許可するか (**Edit**)、データの表示のみを許可するか (**View**)、許可しないか (**Disabled**) を設定します。

**[DisabledBorderColor](properties-color-border.md)** – コントロールの **[DisplayMode](properties-core.md)** プロパティが **Disabled** に設定されている場合のコントロールの境界線の色です。

**FalseFill** - トグルが無効な場合の、トグルの塗りつぶし色です。

**FalseHoverFill** - トグルが無効な場合の、トグルのポイント時の塗りつぶし色です。

**FalseText** - トグルが無効な場合に表示されるテキストです。

**[Fill](properties-color-border.md)** – コントロールの背景色です。

**[FocusedBorderColor](properties-color-border.md)** – コントロールにフォーカスがあるときのコントロールの境界線の色です。

**[FocusedBorderThickness](properties-color-border.md)** – コントロールにフォーカスがあるときのコントロールの境界線の太さです。

**HandleFill** – トグル ハンドルの塗りつぶし色。

**[Height](properties-size-location.md)** – コントロールの上端と下端の距離です。

**[HoverBorderColor](properties-color-border.md)** – コントロール上にユーザーがマウス ポインターを重ねているときのコントロールの境界線の色です。

**[OnChange](properties-core.md)** – ユーザーが (スライダーを調整するなどして) コントロールの値を変更した場合のアプリの反応を指定します。

**OnCheck** – チェック ボックスまたはトグルの値が **true** に変わったときの、アプリの反応を指定します。

**[OnSelect](properties-core.md)** – ユーザーがコントロールをタップまたはクリックした場合のアプリの反応を指定します。

**OnUncheck** – チェック ボックスまたはトグルの値が **false** に変わったときの、アプリの反応を指定します。

**[PressedBorderColor](properties-color-border.md)** – コントロールをユーザーがタップまたはクリックしたときのコントロールの境界線の色です。

**RailFill** – 値が **false** の場合の、トグル コントロール内の四角形の背景色、またはスライダー コントロールのハンドルの右側の線の色です。

**RailHoverFill** – 値が **false** の場合に、トグル コントロールまたはスライダーにポインターを合わせたときの、トグル コントロール内の四角形の背景色、またはスライダー コントロールのハンドルの右側の線の色です。

**[Reset](properties-core.md)** – コントロールを既定値に戻すかどうかを指定します。

**ShowLabel** - テキスト ラベルをトグル コントロールの横に表示するかどうかを指定します。

**[TabIndex](properties-accessibility.md)** – 他のコントロールに関連するキーボード ナビゲーションの順序です。

**TextPosition** - ラベルをトグル コントロールの右側と左側のどちらにするかを指定します。

**[Tooltip](properties-core.md)** – ポインターをコントロールに合わせたときに表示される説明テキストです。

**TrueFill** - トグルが有効な場合の、トグルの塗りつぶし色です。

**TrueHoverFill** - トグルが有効な場合の、トグルのポイント時の塗りつぶし色です。

**TrueText** - トグルが有効な場合に表示されるテキストです。

**ValueFill** – 値が **true** の場合の、トグル コントロール内の四角形の背景色、またはスライダー コントロールのハンドルの左側の線の色です。

**ValueHoverFill** – 値が **true** の場合に、トグル コントロールまたはスライダーをポイントしたときの、トグル コントロール内の四角形の背景色、またはスライダー コントロールのハンドルの左側の線の色です。

**[Visible](properties-core.md)** – コントロールを表示するか非表示にするかを指定します。

**[Width](properties-size-location.md)** – コントロールの左端と右端の間の距離です。

**[X](properties-size-location.md)** – コントロールの左端とその親コンテナー (親コンテナーがない場合は画面) の左端間の距離です。

**[Y](properties-size-location.md)** – コントロールの上端とその親コンテナー (親コンテナーがない場合は画面) の上端間の距離です。

## <a name="related-functions"></a>関連する関数
[**If**( *Condition*, *Result* )](../functions/function-if.md)

## <a name="example"></a>例
1. トグルを追加し、名前を **MemberDiscount** にします。

    [コントロールの追加、命名、構成についてはこちらをご覧ください](../add-configure-controls.md)。
2. ラベルを追加し、その **[Text](properties-core.md)** プロパティを次の数式に設定します。
   <br>**If(MemberDiscount.Value = true, "Price: $75", "Price: $100")**

    **[If](../functions/function-if.md)** 関数や[その他の関数](../formula-reference.md)については各関連記事を参照してください。
3. F5 キーを押し、**MemberDiscount** の値を変更します。

    **MemberDiscount** がオンかオフかに応じて、ラベルに異なる価格が表示されます。
4. 既定のワークスペースに戻るには、Esc キーを押します。


## <a name="accessibility-guidelines"></a>アクセシビリティ ガイドライン
### <a name="color-contrast"></a>色のコントラスト
以下の間には適切な色のコントラストが必要です。
* **HandleFill** と **FalseFill**
* **HandleFill** と **FalseHoverFill**
* **HandleFill** と **TrueFill**
* **HandleFill** と **TrueHoverFill**
* **Fill** とコントロールの外側の色
* **FalseHoverFill** とコントロールの外側の色
* **TrueFill** とコントロールの外側の色
* **TrueHoverFill** とコントロールの外側の色

これは、[標準の色のコントラスト要件](../accessible-apps-color.md)に追加されるものです。

### <a name="screen-reader-support"></a>スクリーン リーダーのサポート
* **[AccessibleLabel](properties-accessibility.md)** が存在する必要があります。
* **FalseText** を指定する必要があります。
* **TrueText** を指定する必要があります。

### <a name="low-vision-support"></a>弱視のサポート
* ユーザーがトグル値をすばやく判断できるように、**ShowLabel** を **true** に設定することを検討してください。

### <a name="keyboard-support"></a>キーボードのサポート
* **[TabIndex](properties-accessibility.md)** を 0 以上にして、キーボード ユーザーがそこに移動できるようにする必要があります。
* フォーカス インジケーターは明確に表示する必要があります。 これを実現するには **[FocusedBorderColor](properties-color-border.md)** と **[FocusedBorderThickness](properties-color-border.md)** を使用します。
