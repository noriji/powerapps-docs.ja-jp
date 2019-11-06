---
title: 'イメージ コントロール: リファレンス | Microsoft Docs'
description: 各種プロパティとサンプルを含むイメージ コントロールに関する情報
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
ms.openlocfilehash: fb0ce1bca968d0e23dc10544a824b340ab336936
ms.sourcegitcommit: 8e42a5996799d9831f8c5a52b0b051a6088d9ce7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/06/2019
ms.locfileid: "73650456"
---
# <a name="image-control-in-powerapps"></a>PowerApps のイメージ コントロール
ローカル ファイルやデータ ソースの画像を表示するコントロールです。

## <a name="description"></a>Description
アプリに**イメージ** コントロールを 1 つまたは複数追加すると、データ セットに含まれていない個々の画像を表示したり、データ ソースのレコードの画像を組み合わせたりすることができます。

## <a name="key-properties"></a>主要なプロパティ
**[Image](properties-visual.md)** – イメージ、オーディオ、マイクの各コントロールに表示される画像の名前です。

## <a name="additional-properties"></a>その他のプロパティ
**[AccessibleLabel](properties-accessibility.md)** – スクリーン リーダー用のラベルです。

**ApplyEXIFOrientation** - 画像とともに埋め込まれたEXIF のデータで指定された向きを、自動的に適用するかどうかを指定します。

**AutoDisableOnSelect** – OnSelect の動作の実行時にコントロールを自動で無効化するかどうかを指定します。

**[BorderColor](properties-color-border.md)** – コントロールの境界線の色です。

**[BorderStyle](properties-color-border.md)** – コントロールの境界線を **Solid** (実線)、**Dashed** (破線)、**Dotted** (点線)、**None** (なし) のいずれに指定します。

**[BorderThickness](properties-color-border.md)** – コントロールの境界線の太さです。

**CalculateOriginalDimensions** – **OriginalHeight** プロパティと **OriginalWidth** プロパティを有効にします。

**[DisplayMode](properties-core.md)** – コントロールで、ユーザー入力を許可するか (**Edit**)、データの表示のみを許可するか (**View**)、許可しないか (**Disabled**) を設定します。

**[DisabledBorderColor](properties-color-border.md)** – コントロールの **[DisplayMode](properties-core.md)** プロパティが **Disabled** に設定されている場合のコントロールの境界線の色です。

**[DisabledFill](properties-color-border.md)** – コントロールの **[DisplayMode](properties-core.md)** プロパティが **Disabled** に設定されている場合のコントロールの背景色です。

**[Fill](properties-color-border.md)** – コントロールの背景色です。

**FlipHorizontal** - 画像を表示する前に水平方向に反転するかどうかを指定します。

**FlipVertical** - 画像を表示する前に垂直方向に反転するかどうかを指定します。

**[FocusedBorderColor](properties-color-border.md)** – コントロールにフォーカスがあるときのコントロールの境界線の色です。

**[FocusedBorderThickness](properties-color-border.md)** – コントロールにフォーカスがあるときのコントロールの境界線の太さです。

**[Height](properties-size-location.md)** – コントロールの上端と下端の距離です。

**[HoverBorderColor](properties-color-border.md)** – コントロール上にユーザーがマウス ポインターを重ねているときのコントロールの境界線の色です。

**[HoverFill](properties-color-border.md)** – コントロールにユーザーがマウス ポインターを重ねているときのコントロールの背景色です。

**[ImagePosition](properties-visual.md)** – 画面またはコントロールのサイズが画像と異なる場合の、画面またはコントロール内の画像の位置です (**Fill** (フィル)、**Fit** (サイズに合わせる)、**Stretch** (伸ばす)、**Tile** (タイル表示)、または **Center** (中央に表示))。

**ImageRotation** - 画像を表示する前に回転させる方法を指定します。  値には、なし、時計回り (CW) に 90 度、反時計回り (CCW) に 90 度、時計回りに 180 度を設定できます。

**[OnSelect](properties-core.md)** – ユーザーがコントロールをタップまたはクリックした場合のアプリの反応を指定します。

**OriginalHeight** – 画像の元の高さです。**CalculateOriginalDimensions** プロパティで有効にします。

**OriginalWidth** – 画像の元の幅です。**CalculateOriginalDimensions** プロパティで有効にします。

**[PaddingBottom](properties-size-location.md)** – コントロール内のテキストとそのコントロールの下端間の距離です。

**[PaddingLeft](properties-size-location.md)** – コントロール内のテキストとそのコントロールの左端間の距離です。

**[PaddingRight](properties-size-location.md)** – コントロール内のテキストとそのコントロールの右端間の距離です。

**[PaddingTop](properties-size-location.md)** – コントロール内のテキストとそのコントロールの上端間の距離です。

**[PressedBorderColor](properties-color-border.md)** – コントロールをユーザーがタップまたはクリックしたときのコントロールの境界線の色です。

**[PressedFill](properties-color-border.md)** – コントロールをユーザーがタップまたはクリックしたときのコントロールの背景色です。

**[RadiusBottomLeft](properties-size-location.md)** – コントロールの左下隅を丸める度合いです。

**[RadiusBottomRight](properties-size-location.md)** – コントロールの右下隅を丸める度合いです。

**[RadiusTopLeft](properties-size-location.md)** – コントロールの左上隅を丸める度合いです。

**[RadiusTopRight](properties-size-location.md)** – コントロールの右上隅を丸める度合いです。

**[TabIndex](properties-accessibility.md)** – 他のコントロールに関連するキーボード ナビゲーションの順序です。

**[Tooltip](properties-core.md)** – ポインターをコントロールに合わせたときに表示される説明テキストです。

**Transparency** – 画像の背後にあるコントロールを表示する度合いです。

**[Visible](properties-core.md)** – コントロールを表示するか非表示にするかを指定します。

**[Width](properties-size-location.md)** – コントロールの左端と右端の間の距離です。

**[X](properties-size-location.md)** – コントロールの左端とその親コンテナー (親コンテナーがない場合は画面) の左端間の距離です。

**[Y](properties-size-location.md)** – コントロールの上端とその親コンテナー (親コンテナーがない場合は画面) の上端間の距離です。

## <a name="related-functions"></a>関連する関数
[**Remove**( *DataSource*, ThisItem )](../functions/function-remove-removeif.md)

## <a name="examples"></a>例
### <a name="show-an-image-from-a-local-file"></a>ローカル ファイルの画像の表示
1. **[ファイル]** メニューの **[メディア]** をクリックまたはタップして、 **[参照]** をクリックまたはタップします。
2. 追加する画像ファイルをクリックまたはタップし、 **[開く]** をクリックまたはタップしてから Esc キーを押して既定のワークスペースに戻ります。
3. **イメージ** コントロールを追加し、**Image** プロパティを追加したファイルの名前に設定します。

    [コントロールの追加および構成](../add-configure-controls.md)についてはこちらをご覧ください。

    指定した画像が**イメージ** コントロールに表示されます。

### <a name="show-a-set-of-images-from-a-data-source"></a>データ ソースの画像セットの表示
1. こちらの [Excel ファイル](https://pwrappssamples.blob.core.windows.net/samples/FlooringEstimates.xlsx)をダウンロードして、ローカル デバイスに保存します。
2. PowerApps Studio で、アプリを作成するか開き、右のウィンドウで **[データ ソースの追加]** をクリックまたはタップします。

    右のウィンドウに **[データ ソースの追加]** が表示されない場合、左のナビゲーション バーの画面をどれかクリックまたはタップします。
3. **[静的データをアプリに追加します]** をクリックまたはタップして、ダウンロードした Excel ファイルをクリックまたはタップし、 **[開く]** をクリックまたはタップします。
4. **[Flooring Estimates]** (フローリングの見積り) チェック ボックスをオンにして、 **[接続]** をクリックまたはタップします。
5. **ギャラリー** コントロールと画像を追加し、 **[Items](properties-core.md)** プロパティを **FlooringEstimates** に設定します。

    [コントロールの追加および構成](../add-configure-controls.md)についてはこちらをご覧ください。

    **ギャラリー** コントロールに、ダウンロードした Excel ファイルに含まれるリンクに基づくカーペット製品、硬木の製品、およびタイル製品の画像が表示されます。


## <a name="accessibility-guidelines"></a>アクセシビリティ ガイドライン
### <a name="color-contrast"></a>色のコントラスト
* グラフィックがボタンとして使用される場合、[標準の色のコントラスト要件](../accessible-apps-color.md)が適用されます。
* 純粋に装飾でないイメージの場合、イメージ内のコントラストの問題を確認すること検討してください。

### <a name="screen-reader-support"></a>スクリーン リーダーのサポート
* グラフィックがボタンとして使用されるか、単なる装飾用ではない場合は、 **[AccessibleLabel](properties-accessibility.md)** が存在する必要があります。
* グラフィックが純粋に装飾用である場合は、 **[AccessibleLabel](properties-accessibility.md)** を空または空の文字列 **""** にする必要があります。 それにより、スクリーン リーダーでグラフィックが無視されます。
* グラフィックが冗長な情報を提供する場合は、 **[AccessibleLabel](properties-accessibility.md)** を空または空の文字列 **""** にすることができます。
  * たとえば、 **[AccessibleLabel](properties-accessibility.md)** が**設定**に設定された歯車の**イメージ**があるとします。 このイメージは、ボタンとしては使用されません。 同じく **[設定]** と表示される **[ラベル](control-text-box.md)** の横にあります。 スクリーン リーダーは、イメージを**設定**と読み上げ、ラベルをもう一度**設定**と読み上げます。 これは不必要に冗長です。 この場合、**イメージ**に **[AccessibleLabel](properties-accessibility.md)** は必要ありません。

    > [!IMPORTANT]
    > スクリーン リーダーは、 **[AccessibleLabel](properties-accessibility.md)** が空の場合でも、 **[TabIndex](properties-accessibility.md)** が 0 以上の**イメージ**を常に読み上げます。 これらはボタンとしてレンダリングされるためです。 **[AccessibleLabel](properties-accessibility.md)** が指定されていない場合、スクリーン リーダーは単純にグラフィックを**ボタン**として読み上げます。

### <a name="keyboard-support"></a>キーボードのサポート
* グラフィックをボタンとして使用する場合は、 **[TabIndex](properties-accessibility.md)** を 0 以上にする必要があります。 こうすることで、キーボード ユーザーがそこに移動できるようになります。
* グラフィックをボタンとして使用する場合は、フォーカス インジケーターを明確に表示する必要があります。 これを実現するには **[FocusedBorderColor](properties-color-border.md)** と **[FocusedBorderThickness](properties-color-border.md)** を使用します。

    > [!NOTE]
  > **[TabIndex](properties-accessibility.md)** が 0 以上の場合、**イメージ**はボタンとしてレンダリングされます。 視覚的な外観は変わりませんが、スクリーン リーダーはイメージをボタンとして正しく識別します。 **[TabIndex](properties-accessibility.md)** が 0 未満の場合、**イメージ**はイメージとして識別されます。
