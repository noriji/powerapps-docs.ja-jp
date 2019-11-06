---
title: 'シェイプ コントロールとアイコン コントロール: リファレンス | Microsoft Docs'
description: 各種プロパティとサンプルを含むシェイプ コントロールとアイコン コントロールに関する情報
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
ms.openlocfilehash: 7cbc7d0a51a4bab24214f31321264d3347fbb152
ms.sourcegitcommit: 8e42a5996799d9831f8c5a52b0b051a6088d9ce7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/06/2019
ms.locfileid: "73649737"
---
# <a name="shape-controls-and-icon-controls-in-powerapps"></a>PowerApps のシェイプ コントロールとアイコン コントロール
見た目と動作のプロパティが構成できるグラフィックスです。

## <a name="description"></a>Description
これらのコントロールには、矢印、幾何学的図形、アクション アイコン、記号などがあり、塗りつぶし、サイズ、位置などのプロパティを構成できます。 ユーザーがコントロールを選択した場合にアプリが応答するように、 **[Onselect](properties-core.md)** プロパティを構成することもできます。

## <a name="key-properties-icons-and-shapes"></a>キーのプロパティ (アイコンと図形)
**[Fill](properties-color-border.md)** – コントロールの背景色です。

**[Onselect](properties-core.md)** –ユーザーがコントロールを選択したときにアプリがどのように応答するかを指定します。

## <a name="key-properties-icons-only"></a>キーのプロパティ (アイコンのみ)

**Icon** -表示するアイコンの種類 (たとえば、[ShoppingCart **] または**[])。 

**Rotation** -アイコンを回転する角度の数値。 

**Color** -名前または RGBA 値によるアイコンの色です。

## <a name="additional-properties"></a>その他のプロパティ
**[AccessibleLabel](properties-accessibility.md)** – スクリーン リーダー用のラベルです。

**[DisplayMode](properties-core.md)** – コントロールで、ユーザー入力を許可するか (**Edit**)、データの表示のみを許可するか (**View**)、許可しないか (**Disabled**) を設定します。

**[FocusedBorderColor](properties-color-border.md)** – コントロールにフォーカスがあるときのコントロールの境界線の色です。

**[FocusedBorderThickness](properties-color-border.md)** – コントロールにフォーカスがあるときのコントロールの境界線の太さです。

**[Height](properties-size-location.md)** – コントロールの上端と下端の距離です。

**[HoverFill](properties-color-border.md)** – コントロールにユーザーがマウス ポインターを重ねているときのコントロールの背景色です。

**[PressedBorderColor](properties-color-border.md)** –ユーザーがコントロールを選択したときのコントロールの境界線の色です。

**[PressedFill](properties-color-border.md)** –ユーザーがコントロールを選択したときのコントロールの背景色です。

**[TabIndex](properties-accessibility.md)** – 他のコントロールに関連するキーボード ナビゲーションの順序です。

**[Visible](properties-core.md)** – コントロールを表示するか非表示にするかを指定します。

**[Width](properties-size-location.md)** – コントロールの左端と右端の間の距離です。

**[X](properties-size-location.md)** – コントロールの左端とその親コンテナー (親コンテナーがない場合は画面) の左端間の距離です。

**[Y](properties-size-location.md)** – コントロールの上端とその親コンテナー (親コンテナーがない場合は画面) の上端間の距離です。

## <a name="related-functions"></a>関連する関数

[**Navigate**( *ScreenName*, *ScreenTransition* )](../functions/function-navigate.md)

## <a name="example"></a>例

1. 既定の **[スクリーン](control-screen.md)** コントロールに **Target** という名前を付け、 **[ラベル](control-text-box.md)** コントロールを追加して **Target** を表示するように **[Text](properties-core.md)** プロパティを設定します。

    [コントロールの追加および構成](../add-configure-controls.md)についてはこちらをご覧ください。

1. **[スクリーン](control-screen.md)** コントロールを追加し、**Source** という名前を付けます。

1. **Source** に **シェイプ** コントロールを追加し、 **[OnSelect](properties-core.md)** プロパティに次の式を設定します。

  `Navigate(Target, ScreenTransition.Fade)`
  
1. F5 キーを押してから、**シェイプ**コントロールを選択します。

    **[Target]\(ターゲット)** 画面が表示されます。

1. (省略可能) Esc キーを押して既定のワークスペースに戻り、**Target** に**シェイプ** コントロールを追加して、**シェイプ** コントロールの **[OnSelect](properties-core.md)** プロパティに次の式を設定します。

  `Navigate(Source, ScreenTransition.Fade)`

## <a name="accessibility-guidelines"></a>アクセシビリティ ガイドライン

### <a name="color-contrast"></a>色のコントラスト

以下は、ボタンとして使用されるグラフィックまたは単なる装飾用ではないグラフィックにのみ適用されます。

アイコンの場合:
- **[色](properties-color-border.md)** と **[塗りつぶし](properties-color-border.md)**
- その他の[標準の色のコントラスト要件](../accessible-apps-color.md)が適用されます (ボタンとして使用される場合)

境界線のある図形の場合:
- **[BorderColor](properties-color-border.md)** およびコントロールの外部の色
- **[FocusedBorderColor](properties-color-border.md)** およびコントロールの外部の色 (ボタンとして使用される場合)

境界線のない図形の場合:
- **[Fill](properties-color-border.md)** およびコントロールの外部の色
- **[PressedFill](properties-color-border.md)** およびコントロールの外部の色 (ボタンとして使用される場合)
- **[HoverFill](properties-color-border.md)** およびコントロールの外部の色 (ボタンとして使用される場合)

### <a name="screen-reader-support"></a>スクリーン リーダーのサポート
- グラフィックがボタンとして使用されている場合、または装飾のためだけではない場合は、 **[AccessibleLabel](properties-accessibility.md)** を空でない文字列に設定する必要があります。

- **[AccessibleLabel](properties-accessibility.md)** は空または空の文字列 **""** でなければなりません。グラフィックが冗長な情報を提供しているか、単に装飾のためのものです。 この値を指定すると、スクリーンリーダーはグラフィックを無視します。

たとえば、**設定**アイコンの **[AccessibleLabel](properties-accessibility.md)** プロパティを **[設定]** に設定することができます。 このアイコンはボタンとしては使用されません。 **[設定]** という **[ラベル](control-text-box.md)** の横に表示されます。 スクリーンリーダーは、アイコンとラベルの両方を**設定**として読み取ります。これは不必要に冗長です。 この場合、アイコンは **[AccessibleLabel](properties-accessibility.md)** を必要としません。

> [!IMPORTANT]
> **[AccessibleLabel](properties-accessibility.md)** が空の文字列に設定され、 **[TabIndex](properties-accessibility.md)** が0以上に設定されている場合、スクリーンリーダーはアイコンまたは図形を**ボタン**として読み取ります。 このようなアイコンや図形は、ボタンとしてレンダリングされます。 

### <a name="keyboard-support"></a>キーボードのサポート
- グラフィックがボタンとして使用されている場合は、 **[TabIndex](properties-accessibility.md)** を0以上にする必要があります。 アイコンまたは図形にこの値を設定した場合、キーボードユーザーはそのアイコンに移動できます。

- グラフィックがボタンとして使用されている場合は、フォーカスインジケーターを明確に表示する必要があります。 この結果を得るには、 **[FocusedBorderColor](properties-color-border.md)** と **[FocusedBorderThickness](properties-color-border.md)** を使用します。

    > [!NOTE]
    > **[TabIndex](properties-accessibility.md)** が 0 以上の場合、アイコンまたは図形はボタンとしてレンダリングされます。 画面の外観は変更されませんが、スクリーンリーダーはイメージをボタンとして正しく識別します。 **[TabIndex](properties-accessibility.md)** が 0 未満の場合、アイコンまたは図形はイメージとして識別されます。
