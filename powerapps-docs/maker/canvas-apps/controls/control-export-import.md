---
title: 'エクスポート コントロールおよびインポート コントロール: リファレンス | Microsoft Docs'
description: 各種プロパティとサンプルを含むエクスポート コントロールおよびインポート コントロールに関する情報
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
ms.openlocfilehash: 942b4b1f5f10cf17d2a33e9f9604661256d99ea6
ms.sourcegitcommit: 8e42a5996799d9831f8c5a52b0b051a6088d9ce7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/06/2019
ms.locfileid: "73650542"
---
# <a name="export-control-and-import-control-in-powerapps"></a>PowerApps のエクスポート コントロールおよびエクスポート コントロール
ローカル ファイルにデータをエクスポートするコントロールと、そのデータを PowerApps 内の別のアプリにインポートするコントロール。

## <a name="description"></a>Description
同じデータを使用する複数のアプリを作成し、これら以外のアプリとはそのデータを共有しない場合には、**エクスポート** コントロールと**インポート** コントロールを使用してデータをエクスポートおよびインポートできます。 データをエクスポートすると、別のコンピューターにコピー可能な圧縮ファイルが作成されます。このファイルは、PowerApps 以外のプログラムでは読み取ることはできません。

## <a name="warning"></a>警告
アプリでこの機能を有効にすると、セキュリティが弱まりデータが漏洩する可能性があります。  インポートするファイルは認定済みの信頼できるファイルのみとし、エクスポートするデータは機密情報または取扱いに注意が必要なもの以外のみとするようにユーザーに指示することが推奨されます。

## <a name="limitations"></a>事項
エクスポート機能は、Web ブラウザーではサポートされていません。

## <a name="key-properties"></a>主要なプロパティ
**Data** – ローカル ファイルにエクスポートするコレクションの名前です。

* **Data** プロパティは、**エクスポート** コントロールでは使用できますが**インポート** コントロールでは使用できません。

**[OnSelect](properties-core.md)** – ユーザーがコントロールをタップまたはクリックした場合のアプリの反応を指定します。

## <a name="additional-properties"></a>その他のプロパティ
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

**[HoverBorderColor](properties-color-border.md)** – コントロール上にユーザーがマウス ポインターを重ねているときのコントロールの境界線の色です。

**[HoverColor](properties-color-border.md)** – コントロールにユーザーがマウス ポインターを重ねているときのコントロール内のテキストの色です。

**[HoverFill](properties-color-border.md)** – コントロールにユーザーがマウス ポインターを重ねているときのコントロールの背景色です。

**[Italic](properties-text.md)** – コントロール内のテキストを斜体にするかどうかを指定します。

**[Padding](properties-size-location.md)** – [インポート] ボタンまたは [エクスポート] ボタンのテキストと、ボタンの縁との距離です。

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

**[Text](properties-core.md)** – コントロールに表示されるテキスト、またはコントロールにユーザーが入力するテキストです。

**[Underline](properties-text.md)** – コントロールに表示されるテキストの下に線を引くかどうかを指定します。

**[VerticalAlign](properties-text.md)** – コントロールの垂直方向の中心に対するコントロール上でのテキストの位置です。

**[Visible](properties-core.md)** – コントロールを表示するか非表示にするかを指定します。

**[Width](properties-size-location.md)** – コントロールの左端と右端の間の距離です。

**[X](properties-size-location.md)** – コントロールの左端とその親コンテナー (親コンテナーがない場合は画面) の左端間の距離です。

**[Y](properties-size-location.md)** – コントロールの上端とその親コンテナー (親コンテナーがない場合は画面) の上端間の距離です。

## <a name="example"></a>例
1. **[[ボタン]](control-button.md)** コントロールを追加し、 **[OnSelect](properties-core.md)** プロパティに次の式を設定します。
   <br>**ClearCollect(Products, {Name:"Europa", Price:"10.99"}, {Name:"Ganymede", Price:"12.49"}, {Name:"Callisto", Price:"11.79"})**
   
    [コントロールの追加、命名、構成についてはこちらをご覧ください](../add-configure-controls.md)。
   
    **[ClearCollect](../functions/function-clear-collect-clearcollect.md)** 関数または[その他の関数](../formula-reference.md)については各関連記事を参照してください。
2. F5 キーを押し、 **[ボタン](control-button.md)** コントロールをクリックまたはタップしてから、Esc キーを押します。
3. **[エクスポート]** コントロールを追加し、**Data** プロパティに **Products**を設定します。
4. F5 キーを押して、**エクスポート** コントロールをクリックまたはタップしてから、データのエクスポート先のファイル名を指定します。
5. **[保存]** をクリックまたはタップしてから、Esc キーを押して既定のワークスペースに戻ります。
6. 新規アプリまたは既存のアプリに **[インポート]** コントロールを追加して **MyData** という名前を付け、 **[OnSelect](properties-core.md)** プロパティに次の式を設定します。<br>
   **Collect(ImportedProducts, MyData.Data)**
7. F5 キーを押して、 **[MyData]** をクリックまたはタップしてからエクスポートしたファイルをクリックまたはタップし、 **[開く]** をクリックまたはタップします。
8. Esc キーを押し、 **[ファイル]** メニューの **[コレクション]** をクリックまたはタップして、エクスポート済みのデータが現在のアプリに存在することを確認します。


## <a name="accessibility-guidelines"></a>アクセシビリティ ガイドライン
**Export** と **Import** は特殊なボタンなので、 **[ボタン](control-button.md)** と同じガイドラインが適用されます。
