---
title: '無線コントロール: リファレンス | Microsoft Docs'
description: 各種プロパティとサンプルを含むラジオ コントロールに関する情報
author: chmoncay
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 07/06/2018
ms.author: chmoncay
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: cba6b072721efa04ce28606cd027939823c2f7c9
ms.sourcegitcommit: 8e42a5996799d9831f8c5a52b0b051a6088d9ce7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/06/2019
ms.locfileid: "73649771"
---
# <a name="radio-control-in-powerapps"></a>PowerApps のラジオ コントロール

複数のオプションが表示され、ユーザーは一度に 1 つだけ選択できる入力コントロール。

## <a name="description"></a>Description

HTML の標準的な入力コントロールである**ラジオ** コントロールは、少数の相互に排他的なオプションに使用するのに最適です。

このコントロールは、横または縦のレイアウトにできます。

## <a name="key-properties"></a>主要なプロパティ

**[Default](properties-core.md)** – ユーザーが変更する前のコントロールの値です。

**[Items](properties-core.md)** – ギャラリー、リスト、グラフなどのコントロールに表示されるデータのソースです。

**Layout** – オプションを縦または横にレイアウトします。

**[Value](properties-core.md)** – 入力コントロールの値です。

**Selected** –選択された項目を表すデータレコード。

## <a name="all-properties"></a>すべてのプロパティ

**[Align](properties-text.md)** – コントロールの水平方向の中心に対するテキストの位置です。

**[BorderColor](properties-color-border.md)** – コントロールの境界線の色です。

**[BorderStyle](properties-color-border.md)** – コントロールの境界線を **Solid** (実線)、**Dashed** (破線)、**Dotted** (点線)、**None** (なし) のいずれに指定します。

**[BorderThickness](properties-color-border.md)** – コントロールの境界線の太さです。

**[Color](properties-color-border.md)** – コントロールのテキストの色です。

**[DisplayMode](properties-core.md)** – コントロールで、ユーザー入力を許可するか (**Edit**)、データの表示のみを許可するか (**View**)、許可しないか (**Disabled**) を設定します。

**[DisabledBorderColor](properties-color-border.md)** – コントロールの **[DisplayMode](properties-core.md)** プロパティが **Disabled** に設定されている場合のコントロールの境界線の色です。

**[DisabledColor](properties-color-border.md)** – コントロールの **[DisplayMode](properties-core.md)** プロパティが **Disabled** に設定されている場合のコントロール内のテキストの色です。

**[DisabledFill](properties-color-border.md)** – コントロールの **[DisplayMode](properties-core.md)** プロパティが **Disabled** に設定されている場合のコントロールの背景色です。

**[Fill](properties-color-border.md)** – コントロールの背景色です。

**[FocusedBorderColor](properties-color-border.md)** – コントロールにフォーカスがあるときのコントロールの境界線の色です。

**[FocusedBorderThickness](properties-color-border.md)** – コントロールにフォーカスがあるときのコントロールの境界線の太さです。

**[Font](properties-text.md)** – テキストを表記するフォントのファミリー名です。

**[FontWeight](properties-text.md)** – コントロール内のテキストの太さです。**Bold** (太字)、**Semibold** (中太)、**Normal** (標準)、**Lighter** (細字) から指定します。

**[Height](properties-size-location.md)** – コントロールの上端と下端の距離です。

**[HoverColor](properties-color-border.md)** – コントロールにユーザーがマウス ポインターを重ねているときのコントロール内のテキストの色です。

**[HoverFill](properties-color-border.md)** – コントロールにユーザーがマウス ポインターを重ねているときのコントロールの背景色です。

**[Italic](properties-text.md)** – コントロール内のテキストを斜体にするかどうかを指定します。

**[LineHeight](properties-text.md)** – テキストの行間やリスト内の項目間などの距離です。

**[OnChange](properties-core.md)** – ユーザーが (スライダーを調整するなどして) コントロールの値を変更した場合のアプリの反応を指定します。

**[OnSelect](properties-core.md)** – ユーザーがコントロールをタップまたはクリックした場合のアプリの反応を指定します。

**[PaddingBottom](properties-size-location.md)** – コントロール内のテキストとそのコントロールの下端間の距離です。

**[PaddingLeft](properties-size-location.md)** – コントロール内のテキストとそのコントロールの左端間の距離です。

**[PaddingRight](properties-size-location.md)** – コントロール内のテキストとそのコントロールの右端間の距離です。

**[PaddingTop](properties-size-location.md)** – コントロール内のテキストとそのコントロールの上端間の距離です。

**[PressedColor](properties-color-border.md)** – コントロールをユーザーがタップまたはクリックしたときのコントロール内のテキストの色です。

**[PressedFill](properties-color-border.md)** – コントロールをユーザーがタップまたはクリックしたときのコントロールの背景色です。

**RadioBackgroundFill** – ラジオボタン コントロールの円の背景色です。

**RadioBorderColor** – ラジオボタン コントロールに含まれる各オプションの円の色です。

**RadioSelectionFill** – ラジオボタン コントロールで選択されたオプションの円の内側に表示される色です。

**RadioSize** – ラジオボタン コントロールの円の直径です。

**[Reset](properties-core.md)** – コントロールを既定値に戻すかどうかを指定します。

**Selectedtext (非推奨)** –選択された項目を表す文字列値。

**[Size](properties-text.md)** – コントロールに表示されるテキストのフォント サイズです。

**[Strikethrough](properties-text.md)** – コントロールに表示されるテキストに取り消し線を付けるかどうかを指定します。

**[TabIndex](properties-accessibility.md)** – 他のコントロールに関連するキーボード ナビゲーションの順序です。

**[Tooltip](properties-core.md)** – ポインターをコントロールに合わせたときに表示される説明テキストです。

**[Underline](properties-text.md)** – コントロールに表示されるテキストの下に線を引くかどうかを指定します。

**[Visible](properties-core.md)** – コントロールを表示するか非表示にするかを指定します。

**[Width](properties-size-location.md)** – コントロールの左端と右端の間の距離です。

**[X](properties-size-location.md)** – コントロールの左端とその親コンテナー (親コンテナーがない場合は画面) の左端間の距離です。

**[Y](properties-size-location.md)** – コントロールの上端とその親コンテナー (親コンテナーがない場合は画面) の上端間の距離です。

## <a name="related-functions"></a>関連する関数

[**Distinct**( *DataSource*, *ColumnName* )](../functions/function-distinct.md)

## <a name="example"></a>例

1. **ラジオ** コントロールを追加して **Pricing** という名前を付け、 **[Items](properties-core.md)** プロパティを次の式に設定します。

    **["標準", "プレミアム"]**

    [コントロールの追加、命名、構成についてはこちらをご覧ください](../add-configure-controls.md)。

2. **[ラベル](control-text-box.md)** コントロールを追加して**ラジオ** コントロールの下に移動させ、 **[ラベル](control-text-box.md)** コントロールの **[Text](properties-core.md)** プロパティを次の式に設定します。

    **If("プレミアム" in Pricing.Selected.Value, "$200/日", "$150/日")**

    **[If](../functions/function-if.md)** 関数や[その他の関数](../formula-reference.md)については各関連記事を参照してください。

3. Alt キーを押したまま、**ラジオ** コントロールのいずれかのオプションを選択します。

    **[ラベル](control-text-box.md)** コントロールに、選択内容に合ったテキストが表示されます。

4. (省略可能) Alt キーを押しながら他のオプションを選択して、適切なテキストが表示されることを確認します。

## <a name="accessibility-guidelines"></a>アクセシビリティ ガイドライン

### <a name="color-contrast"></a>色のコントラスト

[標準の色のコントラスト要件](../accessible-apps-color.md)に加えて、次のものの間の色でコントラストが適切になるようにします。

* **RadioSelectionFill** と **RadioBackgroundFill**
* **RadioBackgroundFill** と **[Fill](properties-color-border.md)**

### <a name="screen-reader-support"></a>スクリーン リーダーのサポート

* すべてのオプションに確実に **[Value](properties-core.md)** を設定します。
* **ラジオ** コントロールの直前に **[ラベル](control-text-box.md)** を追加して、見出しとして表示することを検討してください。

### <a name="keyboard-support"></a>キーボードのサポート

* キーボード ユーザーが移動できるように、 **[TabIndex](properties-accessibility.md)** プロパティを 0 以上に設定します。
* フォーカス インジケーターがはっきり見えるように、 **[FocusedBorderColor](properties-color-border.md)** プロパティと **[FocusedBorderThickness](properties-color-border.md)** プロパティを設定します。
