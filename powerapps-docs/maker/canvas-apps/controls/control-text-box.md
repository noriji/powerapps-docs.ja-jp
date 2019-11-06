---
title: 'ラベル コントロール: リファレンス | Microsoft Docs'
description: 各種プロパティとサンプルを含むラベル コントロールに関する情報
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
ms.openlocfilehash: 66de4ee34cf52f3c351fe3f9c624596e5dd1211d
ms.sourcegitcommit: 8e42a5996799d9831f8c5a52b0b051a6088d9ce7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/06/2019
ms.locfileid: "73649837"
---
# <a name="label-control-in-canvas-apps"></a>キャンバスアプリのラベルコントロール

テキスト、数値、日付、通貨などのデータを表示するボックスです。

## <a name="description"></a>Description

ラベルには、入力した内容がそのまま表示されるリテラル文字列として、またはテキスト文字列に評価される数式として指定したデータが表示されます。 ラベルは通常、他のコントロール (画面を識別するためのバナーなど) の外側に、別のコントロール (評価コントロール、オーディオ コントロールなど) を識別するラベルとして、またはギャラリー内の項目に関する特定の種類の情報を示すために表示されます。

## <a name="key-properties"></a>主要なプロパティ

**[Autoheight](properties-core.md)** –ラベルの高さが自動的に拡大され、すべてのテキストが表示されるようにする場合は true に設定します。 割り当てた高さでテキストを切り捨てる場合は false に設定します。

**[Color](properties-color-border.md)** – コントロールのテキストの色です。

**[Font](properties-text.md)** – テキストを表記するフォントのファミリー名です。

**[Text](properties-core.md)** – コントロールに表示されるテキスト、またはコントロールにユーザーが入力するテキストです。

**[DelayOutput](properties-core.md)**  – テキスト入力時に操作を遅延させる場合は true に設定します。

## <a name="additional-properties"></a>その他のプロパティ

**[Align](properties-text.md)** – コントロールの水平方向の中心に対するテキストの位置です。

**AutoHeight** – **[Text](properties-core.md)** プロパティの内容がコントロールで一度に表示できる文字数を超えている場合に、自動的に **[Height](properties-size-location.md)** プロパティを大きくするかどうかを指定します。

**[BorderColor](properties-color-border.md)** – コントロールの境界線の色です。

**[BorderStyle](properties-color-border.md)** – コントロールの境界線を **Solid** (実線)、**Dashed** (破線)、**Dotted** (点線)、**None** (なし) のいずれに指定します。

**[BorderThickness](properties-color-border.md)** – コントロールの境界線の太さです。

**[DisplayMode](properties-core.md)** – コントロールで、ユーザー入力を許可するか (**Edit**)、データの表示のみを許可するか (**View**)、許可しないか (**Disabled**) を設定します。

**[DisabledBorderColor](properties-color-border.md)** – コントロールの **[DisplayMode](properties-core.md)** プロパティが **Disabled** に設定されている場合のコントロールの境界線の色です。

**[DisabledColor](properties-color-border.md)** – コントロールの **[DisplayMode](properties-core.md)** プロパティが **Disabled** に設定されている場合のコントロール内のテキストの色です。

**[DisabledFill](properties-color-border.md)** – コントロールの **[DisplayMode](properties-core.md)** プロパティが **Disabled** に設定されている場合のコントロールの背景色です。

**[Fill](properties-color-border.md)** – コントロールの背景色です。

**[FocusedBorderColor](properties-color-border.md)** – コントロールにフォーカスがあるときのコントロールの境界線の色です。

**[FocusedBorderThickness](properties-color-border.md)** – コントロールにフォーカスがあるときのコントロールの境界線の太さです。

**[FontWeight](properties-text.md)** – コントロール内のテキストの太さです。**Bold** (太字)、**Semibold** (中太)、**Normal** (標準)、**Lighter** (細字) から指定します。

**[Height](properties-size-location.md)** – コントロールの上端と下端の距離です。

**[HoverBorderColor](properties-color-border.md)** – コントロール上にユーザーがマウス ポインターを重ねているときのコントロールの境界線の色です。

**[HoverColor](properties-color-border.md)** – コントロールにユーザーがマウス ポインターを重ねているときのコントロール内のテキストの色です。

**[HoverFill](properties-color-border.md)** – コントロールにユーザーがマウス ポインターを重ねているときのコントロールの背景色です。

**[Italic](properties-text.md)** – コントロール内のテキストを斜体にするかどうかを指定します。

**[LineHeight](properties-text.md)** – テキストの行間やリスト内の項目間などの距離です。

**[Live](properties-accessibility.md)** –スクリーンリーダーがラベルの**Text**プロパティの値に対する変更をどのように表示するかを指定します。

* **Off**に設定されている場合、スクリーンリーダーは変更をアナウンスしません。
* "**丁寧**" に設定されている場合、スクリーンリーダーは、スクリーンリーダーの読み上げ中に発生した変更を発表する前に読み上げを終了します。
* **Assertive**に設定すると、スクリーンリーダーは、スクリーンリーダーの読み上げ中に発生したすべての変更を通知するために、自身を中断します。

**[OnSelect](properties-core.md)** – ユーザーがコントロールをタップまたはクリックした場合のアプリの反応を指定します。

**Overflow** – ラベルの **Wrap** プロパティが **true** に設定され、 **[Text](properties-core.md)** プロパティの値がコントロールで一度に表示できる文字数を超えている場合に、ラベルにスクロール バーを表示するかどうかを指定します。

**[PaddingBottom](properties-size-location.md)** – コントロール内のテキストとそのコントロールの下端間の距離です。

**[PaddingLeft](properties-size-location.md)** – コントロール内のテキストとそのコントロールの左端間の距離です。

**[PaddingRight](properties-size-location.md)** – コントロール内のテキストとそのコントロールの右端間の距離です。

**[PaddingTop](properties-size-location.md)** – コントロール内のテキストとそのコントロールの上端間の距離です。

**[PressedBorderColor](properties-color-border.md)** – コントロールをユーザーがタップまたはクリックしたときのコントロールの境界線の色です。

**[PressedColor](properties-color-border.md)** – コントロールをユーザーがタップまたはクリックしたときのコントロール内のテキストの色です。

**[PressedFill](properties-color-border.md)** – コントロールをユーザーがタップまたはクリックしたときのコントロールの背景色です。

**Role** -見出し1などのラベルテキストのセマンティックロール。 ラベルのスタイルは変更されませんが、出力はスクリーンリーダーによって解釈されるように正しい意味を持ちます。

**[Size](properties-text.md)** – コントロールに表示されるテキストのフォント サイズです。

**[Strikethrough](properties-text.md)** – コントロールに表示されるテキストに取り消し線を付けるかどうかを指定します。

**[TabIndex](properties-accessibility.md)** – 他のコントロールに関連するキーボード ナビゲーションの順序です。

**[Tooltip](properties-core.md)** – ポインターをコントロールに合わせたときに表示される説明テキストです。

**[Underline](properties-text.md)** – コントロールに表示されるテキストの下に線を引くかどうかを指定します。

**[VerticalAlign](properties-text.md)** – コントロールの垂直方向の中心に対するコントロール上でのテキストの位置です。

**[Visible](properties-core.md)** – コントロールを表示するか非表示にするかを指定します。

**[Width](properties-size-location.md)** – コントロールの左端と右端の間の距離です。

**Wrap** – 長すぎてラベルに収まらないテキストを次の行に折り返すかどうかを指定します。

**[X](properties-size-location.md)** – コントロールの左端とその親コンテナー (親コンテナーがない場合は画面) の左端間の距離です。

**[Y](properties-size-location.md)** – コントロールの上端とその親コンテナー (親コンテナーがない場合は画面) の上端間の距離です。

## <a name="related-functions"></a>関連する関数

[**Text**( *Number*, "*FormatCodes*" )](../functions/function-text.md)

## <a name="examples"></a>例

### <a name="show-a-literal-string"></a>リテラル文字列を表示する

* ラベルを追加し、その **[Text](properties-core.md)** プロパティを **"Hello, world"** (二重引用符を含む) に設定します。
  
    [コントロールの追加および構成](../add-configure-controls.md)についてはこちらをご覧ください。

### <a name="show-the-result-of-a-formula"></a>数式の結果を表示する

* ラベルを追加し、 **[Text](properties-core.md)** プロパティを次のような数式に設定します。<br>
  **Today()**
  
    > [!NOTE]
  > 数式を指定する場合、その数式の引数がリテラル文字列でない限り、引用符は使用しないでください。 引数にリテラル文字列を使用する場合は、数式ではなく、引数を二重引用符で囲みます。
  
    **[Today](../functions/function-now-today-istoday.md)** 関数または[その他の関数](../formula-reference.md)については各関連記事を参照してください。

### <a name="show-data-in-a-gallery"></a>ギャラリーのデータの表示

この手順では、**CityPopulations** というコレクションを作成し、ヨーロッパのさまざまな都市の人口に関するデータを格納します。 次に、3 つのラベルを含むギャラリーにデータを表示し、各ラベルに表示するデータの種類を指定します。

1. ボタンを追加し、 **[OnSelect](properties-core.md)** プロパティを次の数式に設定します。<br>
   **ClearCollect(CityPopulations, {City:"London", Country:"United Kingdom", Population:8615000}, {City:"Berlin", Country:"Germany", Population:3562000}, {City:"Madrid", Country:"Spain", Population:3165000}, {City:"Rome", Country:"Italy", Population:2874000}, {City:"Paris", Country:"France", Population:2273000}, {City:"Hamburg", Country:"Germany", Population:1760000}, {City:"Barcelona", Country:"Spain", Population:1602000}, {City:"Munich", Country:"Germany", Population:1494000}, {City:"Milan", Country:"Italy", Population:1344000})**
2. F5 キーを押して、ボタンを選択し、Esc キーを押します。
3. テキスト ギャラリーを追加し、その **[Items](properties-core.md)** プロパティを **CityPopulations** に設定します。

    ギャラリーを選択すると、右側のペインにそのギャラリーのオプションが表示されます。
4. **Gallery1** ペインで、上部の一覧を **Population** に、中央の一覧を **City** に、下部の一覧を **Country** にそれぞれ設定します。

## <a name="accessibility-guidelines"></a>アクセシビリティ ガイドライン

名前とは異なり、**ラベル** コントロールを別のコントロールのラベルとして使用する必要はありません。 任意のテキストを表示するために使用できます。

**ラベル**は、 **[OnSelect](properties-core.md)** ビヘイビアーを指定してボタンまたはリンクとして使用できます。 この方法で使用する場合、ボタンと同様のアクセシビリティの考慮事項があります。

### <a name="color-contrast"></a>色のコントラスト

以下の間には適切な色のコントラストが必要です。

* **[色](properties-color-border.md)** と **[塗りつぶし](properties-color-border.md)**
* その他の[標準の色のコントラスト要件](../accessible-apps-color.md)が適用されます (ボタンまたはリンクとして使用される場合)

### <a name="screen-reader-support"></a>スクリーン リーダーのサポート

* **[Text](properties-core.md)** を指定する必要があります。
* スクリーンリーダーが**Text**プロパティの値に変更を通知する場合は、 **[Live](properties-accessibility.md)** を**丁寧**または**Assertive**に設定する必要があります。

  > [!NOTE]
  > **[TabIndex](properties-accessibility.md)** が 0 以上の場合、スクリーン リーダーは**ラベル**をボタンとして扱います。

### <a name="low-vision-support"></a>弱視のサポート

* **ラベル**をリンクとして使用する場合、リンクのように見えるようにします。
  * **[Underline](properties-text.md)** を **true** に設定します
  * **[HoverColor](properties-color-border.md)** は **[Color](properties-color-border.md)** と異なる色にします

### <a name="keyboard-support"></a>キーボードのサポート

* テキストをボタンまたはリンクとして使用する場合は、 **[TabIndex](properties-accessibility.md)** を 0 以上にする必要があります。 こうすることで、キーボード ユーザーがそこに移動できるようになります。
* テキストをボタンまたはリンクとして使用する場合は、フォーカス インジケーターを明確に表示する必要があります。 これを実現するには **[FocusedBorderColor](properties-color-border.md)** と **[FocusedBorderThickness](properties-color-border.md)** を使用します。
