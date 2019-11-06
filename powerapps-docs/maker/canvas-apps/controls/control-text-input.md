---
title: 'テキスト入力コントロール: リファレンス | Microsoft Docs'
description: プロパティとサンプルを含むテキスト入力コントロールに関する情報
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
ms.openlocfilehash: e17f580a98013f385080ea1189281607825ce7a8
ms.sourcegitcommit: 8e42a5996799d9831f8c5a52b0b051a6088d9ce7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/06/2019
ms.locfileid: "73649895"
---
# <a name="text-input-control-in-powerapps"></a>PowerApps のテキスト入力コントロール
ユーザーがテキスト、数値、およびその他のデータを入力できるボックス。

## <a name="description"></a>Description
ユーザーは、テキスト入力コントロールに入力してデータを指定できます。 アプリの構成方法に応じて、そのデータをデータ ソースに追加したり、一時的な値を計算するために使用したり、他の方法で組み込んだりすることができます。

## <a name="key-properties"></a>主要なプロパティ
**[Default](properties-core.md)** – ユーザーが変更する前のコントロールの初期値です。

**[Text](properties-core.md)** – コントロールに表示されるテキスト、またはコントロールにユーザーが入力するテキストです。

## <a name="additional-properties"></a>その他のプロパティ
**[AccessibleLabel](properties-accessibility.md)** – スクリーン リーダー用のラベルです。

**[Align](properties-text.md)** – コントロールの水平方向の中心に対するテキストの位置です。

**[BorderColor](properties-color-border.md)** – コントロールの境界線の色です。

**[BorderStyle](properties-color-border.md)** – コントロールの境界線を **Solid** (実線)、**Dashed** (破線)、**Dotted** (点線)、**None** (なし) のいずれに指定します。

**[BorderThickness](properties-color-border.md)** – コントロールの境界線の太さです。

**Clear** – テキスト入力コントロールに、ユーザーがタップまたはクリックして、そのコントロールの内容をクリアできる "X" を表示するかどうかを指定します。

**[Color](properties-color-border.md)** – コントロールのテキストの色です。

**DelayOutput** – true に設定した場合、1/2 秒の遅延の後、ユーザー入力が登録されます。  負荷のかかる操作をユーザーがテキストの入力を完了するまで遅らせる場合 (つまり入力が他の数式で使用される際にフィルタ処理する場合) に便利です。

**[DisplayMode](properties-core.md)** – コントロールで、ユーザー入力を許可するか (**Edit**)、データの表示のみを許可するか (**View**)、許可しないか (**Disabled**) を設定します。

**[DisabledBorderColor](properties-color-border.md)** – コントロールの **[DisplayMode](properties-core.md)** プロパティが **Disabled** に設定されている場合のコントロールの境界線の色です。

**[DisabledColor](properties-color-border.md)** – コントロールの **[DisplayMode](properties-core.md)** プロパティが **Disabled** に設定されている場合のコントロール内のテキストの色です。

**[DisabledFill](properties-color-border.md)** – コントロールの **[DisplayMode](properties-core.md)** プロパティが **Disabled** に設定されている場合のコントロールの背景色です。

**[Fill](properties-color-border.md)** – コントロールの背景色です。

**[FocusedBorderColor](properties-color-border.md)** – コントロールにフォーカスがあるときのコントロールの境界線の色です。

**[FocusedBorderThickness](properties-color-border.md)** – コントロールにフォーカスがあるときのコントロールの境界線の太さです。

**[Font](properties-text.md)** – テキストを表記するフォントのファミリー名です。

**[FontWeight](properties-text.md)** – コントロール内のテキストの太さです。**Bold** (太字)、**Semibold** (中太)、**Normal** (標準)、**Lighter** (細字) から指定します。

**Format** – ユーザー入力を数字のみに制限するか、すべてのテキストを許可するかを指定します。

**[Height](properties-size-location.md)** – コントロールの上端と下端の距離です。

**HintText** - テキスト入力コントロールが空の場合に表示される薄いグレーのテキストです。

**[HoverBorderColor](properties-color-border.md)** – コントロール上にユーザーがマウス ポインターを重ねているときのコントロールの境界線の色です。

**[HoverColor](properties-color-border.md)** – コントロールにユーザーがマウス ポインターを重ねているときのコントロール内のテキストの色です。

**[HoverFill](properties-color-border.md)** – コントロールにユーザーがマウス ポインターを重ねているときのコントロールの背景色です。

**[Italic](properties-text.md)** – コントロール内のテキストを斜体にするかどうかを指定します。

**[LineHeight](properties-text.md)** – テキストの行間やリスト内の項目間などの距離です。

**MaxLength** – ユーザーがテキスト入力コントロールに入力できる文字数です。

**Mode** – コントロールのモードは、**SingleLine**、**MultiLine**、または **Password** です。

**[OnChange](properties-core.md)** – ユーザーが (スライダーを調整するなどして) コントロールの値を変更した場合のアプリの反応を指定します。

**[OnSelect](properties-core.md)** – ユーザーがコントロールをタップまたはクリックした場合のアプリの反応を指定します。

**[PaddingBottom](properties-size-location.md)** – コントロール内のテキストとそのコントロールの下端間の距離です。

**[PaddingLeft](properties-size-location.md)** – コントロール内のテキストとそのコントロールの左端間の距離です。

**[PaddingRight](properties-size-location.md)** – コントロール内のテキストとそのコントロールの右端間の距離です。

**[PaddingTop](properties-size-location.md)** – コントロール内のテキストとそのコントロールの上端間の距離です。

**[PressedBorderColor](properties-color-border.md)** – コントロールをユーザーがタップまたはクリックしたときのコントロールの境界線の色です。

**[PressedColor](properties-color-border.md)** – コントロールをユーザーがタップまたはクリックしたときのコントロール内のテキストの色です。

**[PressedFill](properties-color-border.md)** – コントロールをユーザーがタップまたはクリックしたときのコントロールの背景色です。

**[RadiusBottomLeft](properties-size-location.md)** – コントロールの左下隅を丸める度合いです。

**[RadiusBottomRight](properties-size-location.md)** – コントロールの右下隅を丸める度合いです。

**[RadiusTopLeft](properties-size-location.md)** – コントロールの左上隅を丸める度合いです。

**[RadiusTopRight](properties-size-location.md)** – コントロールの右上隅を丸める度合いです。

**[Reset](properties-core.md)** – コントロールを既定値に戻すかどうかを指定します。

**[Size](properties-text.md)** – コントロールに表示されるテキストのフォント サイズです。

**[Strikethrough](properties-text.md)** – コントロールに表示されるテキストに取り消し線を付けるかどうかを指定します。

**[TabIndex](properties-accessibility.md)** – 他のコントロールに関連するキーボード ナビゲーションの順序です。

**[Tooltip](properties-core.md)** – ポインターをコントロールに合わせたときに表示される説明テキストです。

**[Underline](properties-text.md)** – コントロールに表示されるテキストの下に線を引くかどうかを指定します。

**Virtualkeyboard mode** –アプリユーザーのタッチスクリーンに表示される仮想キーボード、テキスト、または数値の種類です。 **Format**プロパティによって既定値が決定されます。 デバイスのサポートは異なります。 IOS を実行しているデバイスには、バージョン12.2 以降がインストールされている必要があります。 Android の推奨バージョンは9.0 で、数値キーボードの機能は Android デバイスによって異なります。 Windows 10 では、このプロパティはサポートされていません。  

**[Visible](properties-core.md)** – コントロールを表示するか非表示にするかを指定します。

**[Width](properties-size-location.md)** – コントロールの左端と右端の間の距離です。

**[X](properties-size-location.md)** – コントロールの左端とその親コンテナー (親コンテナーがない場合は画面) の左端間の距離です。

**[Y](properties-size-location.md)** – コントロールの上端とその親コンテナー (親コンテナーがない場合は画面) の上端間の距離です。

## <a name="related-functions"></a>関連する関数
[**DateTimeValue**( *String* )](../functions/function-datevalue-timevalue.md)

## <a name="examples"></a>例
### <a name="collect-data"></a>データの収集
1. 2 つのテキスト入力コントロールを追加し、それらに **inputFirst** と **inputLast** という名前を付けます。
   
    [コントロールの追加、命名、構成についてはこちらをご覧ください](../add-configure-controls.md)。
2. ボタンを追加し、その **[Text](properties-core.md)** プロパティを **Add** に設定し、その **[OnSelect](properties-core.md)** プロパティを次の式に設定します。<br>
   **Collect(Names, {FirstName:inputFirst.Text, LastName:inputLast.Text})**
   
    **[Collect](../functions/function-clear-collect-clearcollect.md)** 関数または[その他の関数](../formula-reference.md)については各関連記事を参照してください。
3. 縦/垂直方向にテキスト ギャラリーを追加し、その **[Items](properties-core.md)** プロパティを **Names** に設定し、**Subtitle1** の **[Text](properties-core.md)** プロパティを **ThisItem.FirstName** に設定します。
4. (省略可能) テンプレート ギャラリーで、下部の **Body1** というラベルを削除し、ギャラリーの **[TemplateSize](control-gallery.md)** プロパティを **80** に設定します。
5. F5 キーを押して、**inputFirst** と **inputLast** に文字列を入力して、 **[追加]** ボタンをクリックまたはタップします。
6. (省略可能) 他の名前をコレクションに追加し、Esc キーを押して、既定のワークスペースに戻ります。

### <a name="prompt-for-a-password"></a>パスワードの入力を求める

1. テキスト入力コントロールを追加し、それに **inputPassword** という名前を付けて、その **Mode** プロパティを **Password** に設定します。

1. ラベルを追加し、その **[Text](properties-core.md)** プロパティを次の数式に設定します。<br>
   **If(inputPassword.Text = "P@ssw0rd", "Access granted", "Access denied")**

    **[If](../functions/function-if.md)** 関数や[その他の関数](../formula-reference.md)については各関連記事を参照してください。

1. F5 キーを押し、**inputPassword** に **P@ssw0rd** と入力します。

    パスワードの入力が完了すると、ラベルの **Access denied** の表示が停止し、**Access granted** の表示が開始されます。

1. 既定のワークスペースに戻るには、Esc キーを押します。

1. (省略可能) 矢印などのコントロールを追加し、それを別の画面に移動するように構成し、ユーザーがパスワードを入力した後にのみ表示します。

1. (省略可能) ボタンを追加し、その **[Text](properties-core.md)** プロパティに **Sign in** と表示されるように設定し、タイマーを追加して、ユーザーが間違ったパスワードを入力して、 **[Sign in]** ボタンをクリックまたはタップした場合に、一定の時間テキスト入力コントロールを無効にします。


## <a name="accessibility-guidelines"></a>アクセシビリティ ガイドライン
### <a name="color-contrast"></a>色のコントラスト
* [標準の色のコントラスト要件](../accessible-apps-color.md)が適用されます。

### <a name="screen-reader-support"></a>スクリーン リーダーのサポート
* **[AccessibleLabel](properties-accessibility.md)** が存在する必要があります。

### <a name="keyboard-support"></a>キーボードのサポート
* **[TabIndex](properties-accessibility.md)** を 0 以上にして、キーボード ユーザーがそこに移動できるようにする必要があります。
* フォーカス インジケーターは明確に表示する必要があります。 これを実現するには **[FocusedBorderColor](properties-color-border.md)** と **[FocusedBorderThickness](properties-color-border.md)** を使用します。
 
