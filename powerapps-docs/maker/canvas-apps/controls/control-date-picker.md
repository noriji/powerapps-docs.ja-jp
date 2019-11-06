---
title: '日付の選択コントロール: リファレンス | Microsoft Docs'
description: 各種プロパティとサンプルを含む日付の選択コントロールに関する情報
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
ms.openlocfilehash: 4a7def7990723e9531c4c7a3075c3c2259a45a37
ms.sourcegitcommit: 8e42a5996799d9831f8c5a52b0b051a6088d9ce7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/06/2019
ms.locfileid: "73650606"
---
# <a name="date-picker-control-in-powerapps"></a>PowerApps の日付の選択コントロール
クリックまたはタップして日付を指定できるコントロールです。

## <a name="description"></a>Description
**[テキスト入力](control-text-input.md)** コントロールの代わりに**日付の選択**コントロールを追加すると、ユーザーが適切な形式で日付を指定しやすくなります。

## <a name="key-properties"></a>主要なプロパティ
**DefaultDate** – 日付コントロールの初期値 (ユーザーが変更していない場合) です。

**SelectedDate** – 日付コントロールで現在選択されている日付です。  この日付は現地時刻で表されます。

**Format** – コントロールで日付を表示するときのテキスト形式です。日付はユーザーが指定します。 このプロパティを **ShortDate** (既定) または **LongDate** に設定すると、このコントロールの **Language** プロパティに基づいて日付の形式を指定できます。 また、言語に関係なく同じ形式を使用する場合は、このプロパティを **yyyy/mm/dd** などの式に設定できます。 例:

* ユーザーが 2017 年の最終日をクリックまたはタップし、**Format** プロパティが **ShortDate** に、**Language** プロパティが **en-us** に設定されている場合、コントロールは **12/31/2017** を表示します。
* ユーザーが 2017 年の最終日をクリックまたはタップし、**Format** プロパティが **LongDate** に、**Language** プロパティが **fr-fr** に設定されている場合、コントロールは **dimanche 31 decembre 2017** を表示します。

**Language** –月の名前など、日付の書式設定に使用される言語を決定します。 このプロパティが指定されていない場合、ユーザーのデバイス設定によって言語が決定します。 サポートされている値は、"EN-US" と "FR" です。

## <a name="additional-properties"></a>その他のプロパティ
**[AccessibleLabel](properties-accessibility.md)** – スクリーン リーダー用のラベルです。

**[BorderColor](properties-color-border.md)** – コントロールの境界線の色です。

**[BorderStyle](properties-color-border.md)** – コントロールの境界線を **Solid** (実線)、**Dashed** (破線)、**Dotted** (点線)、**None** (なし) のいずれに指定します。

**[BorderThickness](properties-color-border.md)** – コントロールの境界線の太さです。

**[Color](properties-color-border.md)** – コントロールのテキストの色です。

**[DisplayMode](properties-core.md)** – コントロールで、ユーザー入力を許可するか (Edit)、データの表示のみを許可するか (View)、許可しないか (Disabled) を設定します。

**[DisabledBorderColor](properties-color-border.md)** – コントロールの **[DisplayMode](properties-core.md)** プロパティが **Disabled** に設定されている場合のコントロールの境界線の色です。

**[DisabledColor](properties-color-border.md)** – コントロールの **[DisplayMode](properties-core.md)** プロパティが **Disabled** に設定されている場合のコントロール内のテキストの色です。

**[DisabledFill](properties-color-border.md)** – コントロールの **[DisplayMode](properties-core.md)** プロパティが **Disabled** に設定されている場合のコントロールの背景色です。

**EndYear** – 日付の選択コントロールでユーザーが設定可能な最後の年です。

**[Fill](properties-color-border.md)** – コントロールの背景色です。

**[FocusedBorderColor](properties-color-border.md)** – コントロールにフォーカスがあるときのコントロールの境界線の色です。

**[FocusedBorderThickness](properties-color-border.md)** – コントロールにフォーカスがあるときのコントロールの境界線の太さです。

**[Font](properties-text.md)** – テキストを表記するフォントのファミリー名です。

**[FontWeight](properties-text.md)** – コントロール内のテキストの太さです。**Bold** (太字)、**Semibold** (中太)、**Normal** (標準)、**Lighter** (細字) から指定します。

**[Height](properties-size-location.md)** – コントロールの上端と下端の距離です。

**IconFill** – 日付の選択コントロール アイコンの前景色。

**IconBackground** – 日付の選択コントロール アイコンの背景色。

**Inputtextplaceholder** –日付が入力されていない場合に表示される指示テキストです。

**[Italic](properties-text.md)** – コントロール内のテキストを斜体にするかどうかを指定します。

**[OnSelect](properties-core.md)** – ユーザーがコントロールをタップまたはクリックした場合のアプリの反応を指定します。

**[PaddingBottom](properties-size-location.md)** – コントロール内のテキストとそのコントロールの下端間の距離です。

**[PaddingLeft](properties-size-location.md)** – コントロール内のテキストとそのコントロールの左端間の距離です。

**[PaddingRight](properties-size-location.md)** – コントロール内のテキストとそのコントロールの右端間の距離です。

**[PaddingTop](properties-size-location.md)** – コントロール内のテキストとそのコントロールの上端間の距離です。

**[Size](properties-text.md)** – コントロールに表示されるテキストのフォント サイズです。

**StartYear** – 日付の選択コントロールでユーザーが設定可能な最初の年です。

**[TabIndex](properties-accessibility.md)** – 他のコントロールに関連するキーボード ナビゲーションの順序です。

**[Visible](properties-core.md)** – コントロールを表示するか非表示にするかを指定します。

**[Width](properties-size-location.md)** – コントロールの左端と右端の間の距離です。

**[X](properties-size-location.md)** – コントロールの左端とその親コンテナー (親コンテナーがない場合は画面) の左端間の距離です。

**[Y](properties-size-location.md)** – コントロールの上端とその親コンテナー (親コンテナーがない場合は画面) の上端間の距離です。

## <a name="related-functions"></a>関連する関数
**[Year](../functions/function-datetime-parts.md)** ( *DateTimeValue* )

## <a name="example"></a>例
1. **日付の選択**コントロールを追加して、**Deadline** という名前を付けます。

    [コントロールの追加、命名、構成についてはこちらをご覧ください](../add-configure-controls.md)。
2. **[ラベル](control-text-box.md)** コントロールを追加し、その **[Text](properties-core.md)** プロパティを次の数式に設定します。
   <br>**DateDiff(Today(), Deadline.SelectedDate) & " days to go!"**

    **[DateDiff](../functions/function-dateadd-datediff.md)** 関数や[その他の関数](../formula-reference.md)の詳細については各関連記事をご覧ください。
3. F5 キーを押して **Deadline** の日付を選択し、 **[OK]** をクリックまたはタップします。

    **[ラベル](control-text-box.md)** コントロールに、当日から選択した日付までの日数が表示されます。
4. 既定のワークスペースに戻るには、Esc キーを押します。


## <a name="accessibility-guidelines"></a>アクセシビリティ ガイドライン
### <a name="color-contrast"></a>色のコントラスト
* [標準の色のコントラスト要件](../accessible-apps-color.md)が適用されます。

### <a name="screen-reader-support"></a>スクリーン リーダーのサポート
* **[AccessibleLabel](properties-accessibility.md)** が存在する必要があります。

### <a name="keyboard-support"></a>キーボードのサポート
* **[TabIndex](properties-accessibility.md)** を 0 以上にして、キーボード ユーザーがそこに移動できるようにする必要があります。
* フォーカス インジケーターは明確に表示する必要があります。 これを実現するには **[FocusedBorderColor](properties-color-border.md)** と **[FocusedBorderThickness](properties-color-border.md)** を使用します。

> [!TIP]
> カレンダーが開いたら、pageup キー**と pagedown**キー**を押して**、月間を移動し、 **shift** + pageup キーを**押しながら pagedown キーを押し**て、年の間を移動します。
