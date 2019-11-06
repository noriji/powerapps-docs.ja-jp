---
title: 'ドロップ ダウン コントロール: リファレンス | Microsoft Docs'
description: 各種プロパティとサンプルを含むドロップ ダウン コントロールに関する情報
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
ms.openlocfilehash: 53e78383733af1b5fdb71f5649d342f07605340e
ms.sourcegitcommit: 8e42a5996799d9831f8c5a52b0b051a6088d9ce7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/06/2019
ms.locfileid: "73650569"
---
# <a name="drop-down-control-in-powerapps"></a>PowerApps のドロップ ダウン コントロール
ユーザーがそれを開く場合を除き、最初の項目のみを表示するリストです。

## <a name="description"></a>Description
**ドロップダウン** コントロールを使うと、特にリストに多数の選択肢が含まれている場合に画面スペースを節約できます。 ユーザーが下向き矢印を選択して選択肢を表示しない限り、コントロールが使うのは 1 行のみです。  コントロールは、最大で 500 の項目を表示します。

## <a name="key-properties"></a>主要なプロパティ
**[Default](properties-core.md)** – ユーザーが別の値を指定する前のコントロールの初期値です。

**[Items](properties-core.md)** – コントロールに表示される、項目を含むデータのソースです。 ソースに列が複数ある場合、コントロールの **Value** プロパティを表示するデータの列に設定します。
  
**Value** – (データ ソースに複数の列がある場合など) コントロールに表示するデータの列です。

**Selected** –選択された項目を表すデータレコード。

**Allowemptyselection** –項目が選択されていない場合に、コントロールが空の選択を示すかどうかを指定します。 アプリユーザーは、空の項目を選択して選択を解除することもできます。

## <a name="additional-properties"></a>その他のプロパティ
**[AccessibleLabel](properties-accessibility.md)** – スクリーン リーダー用のラベルです。

**[BorderColor](properties-color-border.md)** – コントロールの境界線の色です。

**[BorderStyle](properties-color-border.md)** – コントロールの境界線を **Solid** (実線)、**Dashed** (破線)、**Dotted** (点線)、**None** (なし) のいずれに指定します。

**[BorderThickness](properties-color-border.md)** – コントロールの境界線の太さです。

**ChevronBackground** – ドロップダウン リストの下向き矢印の背景色です。

**ChevronBackground** – ドロップダウン リストの下向き矢印の色です。

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

**[HoverBorderColor](properties-color-border.md)** – コントロール上にユーザーがマウス ポインターを重ねているときのコントロールの境界線の色です。

**[HoverColor](properties-color-border.md)** – コントロールにユーザーがマウス ポインターを重ねているときのコントロール内のテキストの色です。

**[HoverFill](properties-color-border.md)** – コントロールにユーザーがマウス ポインターを重ねているときのコントロールの背景色です。

**[Italic](properties-text.md)** – コントロール内のテキストを斜体にするかどうかを指定します。

**[OnChange](properties-core.md)** – ユーザーが (スライダーを調整するなどして) コントロールの値を変更した場合のアプリの反応を指定します。

**[OnSelect](properties-core.md)** – ユーザーがコントロールをタップまたはクリックした場合のアプリの反応を指定します。

**[PaddingBottom](properties-size-location.md)** – コントロール内のテキストとそのコントロールの下端間の距離です。

**[PaddingLeft](properties-size-location.md)** – コントロール内のテキストとそのコントロールの左端間の距離です。

**[PaddingRight](properties-size-location.md)** – コントロール内のテキストとそのコントロールの右端間の距離です。

**[PaddingTop](properties-size-location.md)** – コントロール内のテキストとそのコントロールの上端間の距離です。

**[PressedBorderColor](properties-color-border.md)** – コントロールをユーザーがタップまたはクリックしたときのコントロールの境界線の色です。

**[PressedColor](properties-color-border.md)** – コントロールをユーザーがタップまたはクリックしたときのコントロール内のテキストの色です。

**[PressedFill](properties-color-border.md)** – コントロールをユーザーがタップまたはクリックしたときのコントロールの背景色です。

**[Reset](properties-core.md)** – コントロールを既定値に戻すかどうかを指定します。

**Selectedtext (非推奨)** –選択された項目を表す文字列値。

**[SelectionColor](properties-color-border.md)** – リスト内で選択された項目のテキストの色、またはペン コントロールの選択ツールの色です。

**[SelectionFill](properties-color-border.md)** – リストで選択された項目またはペン コントロールの選択領域の背景色です。

**[Size](properties-text.md)** – コントロールに表示されるテキストのフォント サイズです。

**[Strikethrough](properties-text.md)** – コントロールに表示されるテキストに取り消し線を付けるかどうかを指定します。

**[TabIndex](properties-accessibility.md)** – 他のコントロールに関連するキーボード ナビゲーションの順序です。

**[Tooltip](properties-core.md)** – ポインターをコントロールに合わせたときに表示される説明テキストです。

**[Underline](properties-text.md)** – コントロールに表示されるテキストの下に線を引くかどうかを指定します。

**[Visible](properties-core.md)** – コントロールを表示するか非表示にするかを指定します。

**[Width](properties-size-location.md)** – コントロールの左端と右端の間の距離です。

**[X](properties-size-location.md)** – コントロールの左端とその親コンテナー (親コンテナーがない場合は画面) の左端間の距離です。

**[Y](properties-size-location.md)** – コントロールの上端とその親コンテナー (親コンテナーがない場合は画面) の上端間の距離です。

## <a name="example"></a>例

### <a name="simple-list"></a>シンプルなリスト

1. **ドロップ ダウン** コントロールを追加し、その **[Items](properties-core.md)** プロパティを以下の式に設定します。

    `["Seattle", "Tokyo", "London", "Johannesburg", "Rio de Janeiro"]`

    [コントロールの追加、命名、構成についてはこちらをご覧ください](../add-configure-controls.md)。

1. ALT キーを押しながらコントロールの下矢印を選択し、リストの項目を表示します。

### <a name="list-from-a-data-source"></a>データ ソースからのリスト
この手順の原則は、テーブルを[提供するすべてのデータソース](../connections-list.md#tables)に適用されますが、これらの手順を正確に実行するには、Common Data Service データベースが作成され、サンプルデータが追加されている環境を開く必要があります。

1. [空のアプリを開き](../data-platform-create-app-scratch.md#open-a-blank-app)、次いで [**Accounts** エンティティ](../data-platform-create-app-scratch.md#specify-an-entity)を指定します。

1. **ドロップ ダウン** コントロールを追加し、 **[Items](properties-core.md)** プロパティを以下の式に設定します。

    `Distinct(Accounts, address1_city)`

    この数式では、**Accounts** エンティティの市区町村がすべて表示されます。 複数のレコードの市区町村が同じである場合、重複するものは、 **[Distinct](../functions/function-distinct.md)** 関数によりドロップダウン コントロールで非表示となります。

1. (オプション) **ドロップダウン** コントロールを **Cities** に名前変更し、垂直方向の **Gallery** コントロールを追加し、ギャラリーの **[Items](properties-core.md)** プロパティをこの数式に設定します。

    `Filter(Accounts, address1_city = Cities.Selected.Value)`

    この **[Filter](../functions/function-filter-lookup.md)** 関数は、市区町村が **Cities** コントロールの選択された値と一致する **Accounts** エンティティのレコードのみを表示します。

## <a name="accessibility-guidelines"></a>アクセシビリティ ガイドライン
### <a name="color-contrast"></a>色のコントラスト
以下の間には適切な色のコントラストが必要です。
* **ChevronFill** と **ChevronBackground**
* **ChevronHoverFill** と **ChevronHoverBackground**
* **SelectionColor** と **SelectionFill**
* **SelectionFill** と **[Fill](properties-color-border.md)**

これは、[標準の色のコントラスト要件](../accessible-apps-color.md)に追加されるものです。

### <a name="screen-reader-support"></a>スクリーン リーダーのサポート
* **[AccessibleLabel](properties-accessibility.md)** が存在する必要があります。

### <a name="keyboard-support"></a>キーボードのサポート
* **[TabIndex](properties-accessibility.md)** を 0 以上にして、キーボード ユーザーがそこに移動できるようにする必要があります。
* フォーカス インジケーターは明確に表示する必要があります。 これを実現するには **[FocusedBorderColor](properties-color-border.md)** と **[FocusedBorderThickness](properties-color-border.md)** を使用します。
