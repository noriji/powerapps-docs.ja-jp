---
title: 'ボタン コントロール: リファレンス | Microsoft Docs'
description: 各種プロパティとサンプルを含むボタン コントロールに関する情報
author: chmoncay
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.date: 10/25/2016
ms.author: chmoncay
ms.reviewer: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 750b02bdd3363f03ad0f32ae1fcbc59d7c5c3f3e
ms.sourcegitcommit: 8e42a5996799d9831f8c5a52b0b051a6088d9ce7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/06/2019
ms.locfileid: "73650735"
---
# <a name="button-control-in-powerapps"></a>PowerApps のボタン コントロール
クリックまたはタップするとアプリを操作できるコントロールです。

## <a name="description"></a>Description
ユーザーが**ボタン** コントロールをクリックまたはタップしたときに 1 つ以上の数式を実行するように、このコントロールの **[OnSelect](properties-core.md)** プロパティを構成します。

## <a name="key-properties"></a>主要なプロパティ
**[OnSelect](properties-core.md)** – ユーザーがコントロールをタップまたはクリックした場合のアプリの反応を指定します。

**[Text](properties-core.md)** – コントロールに表示されるテキスト、またはコントロールにユーザーが入力するテキストです。

## <a name="additional-properties"></a>その他のプロパティ
**[Align](properties-text.md)** – コントロールの水平方向の中心に対するテキストの位置です。

**AutoDisableOnSelect** – **OnSelect** の動作の実行時にコントロールを自動で無効化します。

**[BorderColor](properties-color-border.md)** – コントロールの境界線の色です。

**[BorderStyle](properties-color-border.md)** – コントロールの境界線を **Solid** (実線)、**Dashed** (破線)、**Dotted** (点線)、**None** (なし) のいずれに指定します。

**[BorderThickness](properties-color-border.md)** – コントロールの境界線の太さです。

**[Color](properties-color-border.md)** – コントロールのテキストの色です。

**[DisplayMode](properties-core.md)** – コントロールで、ユーザー入力を許可するか (**Edit**)、データの表示のみを許可するか (**View**)、許可しないか (**Disabled**) を設定します。

**[DisabledBorderColor](properties-color-border.md)** – コントロールの **[DisplayMode](properties-core.md)** プロパティが **Disabled** に設定されている場合のコントロールの境界線の色です。

**[DisabledColor](properties-color-border.md)** – コントロールの **[DisplayMode](properties-core.md)** プロパティが **Disabled** に設定されている場合のコントロール内のテキストの色です。

**[DisabledFill](properties-color-border.md)** – コントロールの **[DisplayMode](properties-core.md)** プロパティが **Disabled** に設定されている場合のコントロールの背景色です。

**[FocusedBorderColor](properties-color-border.md)** – コントロールにフォーカスがあるときのコントロールの境界線の色です。

**[FocusedBorderThickness](properties-color-border.md)** – コントロールにフォーカスがあるときのコントロールの境界線の太さです。

**[Fill](properties-color-border.md)** – コントロールの背景色です。

**[Font](properties-text.md)** – テキストを表記するフォントのファミリー名です。

**[FontWeight](properties-text.md)** – コントロール内のテキストの太さです。**Bold** (太字)、**Semibold** (中太)、**Normal** (標準)、**Lighter** (細字) から指定します。

**[Height](properties-size-location.md)** – コントロールの上端と下端の距離です。

**[HoverBorderColor](properties-color-border.md)** – コントロール上にユーザーがマウス ポインターを重ねているときのコントロールの境界線の色です。

**[HoverColor](properties-color-border.md)** – コントロールにユーザーがマウス ポインターを重ねているときのコントロール内のテキストの色です。

**[HoverFill](properties-color-border.md)** – コントロールにユーザーがマウス ポインターを重ねているときのコントロールの背景色です。

**[Italic](properties-text.md)** – コントロール内のテキストを斜体にするかどうかを指定します。

**[PaddingBottom](properties-size-location.md)** – コントロール内のテキストとそのコントロールの下端間の距離です。

**[PaddingLeft](properties-size-location.md)** – コントロール内のテキストとそのコントロールの左端間の距離です。

**[PaddingRight](properties-size-location.md)** – コントロール内のテキストとそのコントロールの右端間の距離です。

**[PaddingTop](properties-size-location.md)** – コントロール内のテキストとそのコントロールの上端間の距離です。

**Pressed** – コントロールが押されている間は  *true* 、それ以外の時は *false* になります。

**[PressedBorderColor](properties-color-border.md)** – コントロールをユーザーがタップまたはクリックしたときのコントロールの境界線の色です。

**[PressedColor](properties-color-border.md)** – コントロールをユーザーがタップまたはクリックしたときのコントロール内のテキストの色です。

**[PressedFill](properties-color-border.md)** – コントロールをユーザーがタップまたはクリックしたときのコントロールの背景色です。

**[RadiusBottomLeft](properties-size-location.md)** – コントロールの左下隅を丸める度合いです。

**[RadiusBottomRight](properties-size-location.md)** – コントロールの右下隅を丸める度合いです。

**[RadiusTopLeft](properties-size-location.md)** – コントロールの左上隅を丸める度合いです。

**[RadiusTopRight](properties-size-location.md)** – コントロールの右上隅を丸める度合いです。

**[Size](properties-text.md)** – コントロールに表示されるテキストのフォント サイズです。

**[Strikethrough](properties-text.md)** – コントロールに表示されるテキストに取り消し線を付けるかどうかを指定します。

**[TabIndex](properties-accessibility.md)** – 他のコントロールに関連するキーボード ナビゲーションの順序です。

**[Tooltip](properties-core.md)** – ポインターをコントロールに合わせたときに表示される説明テキストです。

**[Underline](properties-text.md)** – コントロールに表示されるテキストの下に線を引くかどうかを指定します。

**[VerticalAlign](properties-text.md)** – コントロールの垂直方向の中心に対するコントロール上でのテキストの位置です。

**[Visible](properties-core.md)** – コントロールを表示するか非表示にするかを指定します。

**[Width](properties-size-location.md)** – コントロールの左端と右端の間の距離です。

**[X](properties-size-location.md)** – コントロールの左端とその親コンテナー (親コンテナーがない場合は画面) の左端間の距離です。

**[Y](properties-size-location.md)** – コントロールの上端とその親コンテナー (親コンテナーがない場合は画面) の上端間の距離です。

## <a name="related-functions"></a>関連する関数
**[Navigate( *ScreenName* 、 *ScreenTransitionValue* )](../functions/function-navigate.md)**

## <a name="examples"></a>例
### <a name="add-a-basic-formula-to-a-button"></a>ボタンに基本的な数式を追加する
1. **[テキスト入力](control-text-input.md)** コントロールを追加し、 **Source** という名前を付けます。
   
    [コントロールの追加、命名、構成についてはこちらをご覧ください](../add-configure-controls.md)。
2. **ボタン** コントロールを追加し、 **[Text](properties-core.md)** プロパティを "Add" に設定して、 **[OnSelect](properties-core.md)** プロパティを次の式に設定します。<br>
   **UpdateContext({Total:Total + Value(Source.Text)})**
   
    **[UpdateContext](../functions/function-updatecontext.md)** 関数や[その他の関数](../formula-reference.md)については各関連記事を参照してください。
3. **[ラベル](control-text-box.md)** コントロールを追加し、 **[Text](properties-core.md)** プロパティを **Total** に設定して、**F5** キーを押します。
4. "**Source**" から既定のテキストを消去し、数値を入力して、"**Add**" をクリックまたはタップします。
   
    **[ラベル](control-text-box.md)** コントロールに、入力した数値が表示されます。
5. "**Source**" から数値を消去し、別の数値を入力して、"**Add**" をクリックまたはタップします。
   
    **[ラベル](control-text-box.md)** コントロールに、入力した 2 つの数値の合計が表示されます。
6. (省略可) 前のステップを 1 回以上繰り返します。
7. Esc キーを押して (または、右上隅の閉じるアイコンをクリックまたはタップして)、既定のワークスペースに戻ります。

### <a name="configure-a-button-with-multiple-formulas"></a>複数の数式を使用してボタンを構成する
入力と入力の間に**テキスト入力**コントロールをクリアする数式を追加します。

1. "**Source**" の **[HintText](control-text-input.md)** プロパティを "Enter a number" に設定します。
2. "**Add**" の **[OnSelect](properties-core.md)** プロパティを次の数式に設定します。
   
    **UpdateContext({Total:Total + Value(Source.Text)});<br>UpdateContext({ClearInput: ""})**
   
    > [!NOTE]
   > 複数の数式はセミコロン " **;** " で区切ります。
3. "**Source**" の **[Default](properties-core.md)** プロパティを **ClearInput** に設定します。
4. **F5** キーを押し、複数の数値を一緒に追加してアプリをテストします。

### <a name="add-another-button-to-reset-the-total"></a>合計をリセットするもう 1 つのボタンを追加する
計算と計算の間に合計をクリアする 2 番目のボタンを追加します。

1. もう 1 つの**ボタン** コントロールを追加し、 **[Text](properties-core.md)** プロパティを "Clear" に設定して、 **[OnSelect](properties-core.md)** プロパティを次の数式に設定します。
   
    **UpdateContext({Total:0})**
2. **F5** キーを押し、複数の数値を一緒に追加して、 **[クリア]** をクリックまたはタップして合計をクリアします。

### <a name="change-a-buttons-appearance"></a>ボタンの外観を変更する
#### <a name="change-a-buttons-shape"></a>ボタンの形を変更する
PowerApps の既定では、角の丸い四角形の**ボタン** コントロールが作成されます。 **ボタン** コントロールの形に基本的な変更を加えることができます。そのためには、 **[Height](properties-size-location.md)** 、 **[Width](properties-size-location.md)** 、 **[Radius](properties-size-location.md)** の各プロパティを変更します。

> [!NOTE]
> [アイコンとシェイプ](control-shapes-icons.md)には、さまざまなデザインが用意されていて、**ボタン** コントロールで実行できるのと同じ基本的な機能のいくつかを実行できます。 ただし、 **[アイコンとシェイプ](control-shapes-icons.md)** に **[Text](properties-core.md)** プロパティはありません。

1. **ボタン** コントロールを追加し、 **[Height](properties-size-location.md)** プロパティと **[Width](properties-size-location.md)** プロパティを **300** に設定して、大きな正方形のボタンを作成します。
2. **[RadiusTopLeft](properties-size-location.md)** 、 **[RadiusTopRight](properties-size-location.md)** 、 **[RadiusBottomLeft](properties-size-location.md)** 、 **[RadiusBottomRight](properties-size-location.md)** の各プロパティを変更して、四隅の曲率の量を調整します。 異なるいくつかのシェイプの例を次に示します。それぞれ 300 x 300 の正方形のボタンを基にしています。
   
   * 4 つすべての **[Radius](properties-size-location.md)** 値を **150** に設定して円を作成します。
   * **[RadiusTopLeft](properties-size-location.md)** と **[RadiusBottomRight](properties-size-location.md)** の値を **300** に設定して、葉の形をした**ボタン**を作成します。
   * **[RadiusTopLeft](properties-size-location.md)** と **[RadiusTopRight](properties-size-location.md)** の値を **300** に設定し、 **[RadiusBottomLeft](properties-size-location.md)** と **[RadiusBottomRight](properties-size-location.md)** の値を **100** に設定して、タブの形をしたボタンを作成します。

#### <a name="change-a-buttons-color-when-you-hover-over-it"></a>ホバーしたときのボタンの色を変更する
既定では、**ボタン** コントロールにマウスでホバーすると、塗りつぶしの色が 20% だけ暗くなります。 **[HoverFill](properties-color-border.md)** プロパティを変更することで、この動作を変更できます。そのためには **[ColorFade](../functions/function-colors.md)** 関数を使用します。 **[ColorFade](../functions/function-colors.md)** の数式を正の比率に設定すると、ボタンにホバーしたときの色が薄くなります。一方、負の比率を設定すると、色が濃くなります。

* 作成したいずれかのボタンの **[HoverFill](properties-color-border.md)** プロパティで **[ColorFade](../functions/function-colors.md)** の比率を変更し、その効果を確認します。

**ボタン** コントロールの色を指定する別の方法として、 **[HoverFill](properties-color-border.md)** プロパティを、 **[ColorFade](../functions/function-colors.md)** 関数ではなく **[ColorValue](../functions/function-colors.md)** 関数を含む数式 **ColorValue("Red")** など に変更する方法もあります。

> [!NOTE]
> 色の値には、CSS 色定義を名前か 16 進値のいずれかで指定できます。

* 作成したいずれかのボタンで、 **[ColorFade](../functions/function-colors.md)** 関数を **[ColorValue](../functions/function-colors.md)** 関数に置き換え、効果を確認します。


## <a name="accessibility-guidelines"></a>アクセシビリティ ガイドライン
### <a name="color-contrast"></a>色のコントラスト
* [標準の色のコントラスト要件](../accessible-apps-color.md)が適用されます。

### <a name="screen-reader-support"></a>スクリーン リーダーのサポート
* **[Text](properties-core.md)** を指定する必要があります。

### <a name="keyboard-support"></a>キーボードのサポート
* **[TabIndex](properties-accessibility.md)** を 0 以上にして、キーボード ユーザーがそこに移動できるようにする必要があります。
* フォーカス インジケーターは明確に表示する必要があります。 これを実現するには **[FocusedBorderColor](properties-color-border.md)** と **[FocusedBorderThickness](properties-color-border.md)** を使用します。
 
