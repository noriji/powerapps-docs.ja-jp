---
title: 'HTML テキスト コントロール: リファレンス | Microsoft Docs'
description: 各種プロパティとサンプルを含む HTML テキスト コントロールに関する情報
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
ms.openlocfilehash: d514342bc51cdd6aa737da1b893530d702127bd1
ms.sourcegitcommit: 8e42a5996799d9831f8c5a52b0b051a6088d9ce7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/06/2019
ms.locfileid: "73650490"
---
# <a name="html-text-control-in-powerapps"></a>PowerApps の HTML テキスト コントロール
テキストを表示し、書式設定のための HTML タグを変換するボックスです。

## <a name="description"></a>Description
**HTML テキスト** コントロールは、プレーンテキストや数値を表示するだけでなく、HTML タグ (改行なしスペースなど) の変換も行います。

## <a name="key-properties"></a>主要なプロパティ
**[Color](properties-color-border.md)** – コントロールのテキストの色です。

**[Font](properties-text.md)** – テキストを表記するフォントのファミリー名です。

**HtmlText** – HTML テキスト コントロールに表示される、HTML タグを含む可能性のあるテキストです。

## <a name="additional-properties"></a>その他のプロパティ
**[BorderColor](properties-color-border.md)** – コントロールの境界線の色です。

**[BorderStyle](properties-color-border.md)** – コントロールの境界線を **Solid** (実線)、**Dashed** (破線)、**Dotted** (点線)、**None** (なし) のいずれに指定します。

**[BorderThickness](properties-color-border.md)** – コントロールの境界線の太さです。

**[DisplayMode](properties-core.md)** – コントロールで、ユーザー入力を許可するか (**Edit**)、データの表示のみを許可するか (**View**)、許可しないか (**Disabled**) を設定します。

**[DisabledBorderColor](properties-color-border.md)** – コントロールの **[DisplayMode](properties-core.md)** プロパティが **Disabled** に設定されている場合のコントロールの境界線の色です。

**[DisabledFill](properties-color-border.md)** – コントロールの **[DisplayMode](properties-core.md)** プロパティが **Disabled** に設定されている場合のコントロールの背景色です。

**[Fill](properties-color-border.md)** – コントロールの背景色です。

**[Height](properties-size-location.md)** – コントロールの上端と下端の距離です。

**[HoverBorderColor](properties-color-border.md)** – コントロール上にユーザーがマウス ポインターを重ねているときのコントロールの境界線の色です。

**[OnSelect](properties-core.md)** – ユーザーがコントロールをタップまたはクリックした場合のアプリの反応を指定します。

**[PaddingBottom](properties-size-location.md)** – コントロール内のテキストとそのコントロールの下端間の距離です。

**[PaddingLeft](properties-size-location.md)** – コントロール内のテキストとそのコントロールの左端間の距離です。

**[PaddingRight](properties-size-location.md)** – コントロール内のテキストとそのコントロールの右端間の距離です。

**[PaddingTop](properties-size-location.md)** – コントロール内のテキストとそのコントロールの上端間の距離です。

**[Size](properties-text.md)** – コントロールに表示されるテキストのフォント サイズです。

**[Tooltip](properties-core.md)** – ポインターをコントロールに合わせたときに表示される説明テキストです。

**[Visible](properties-core.md)** – コントロールを表示するか非表示にするかを指定します。

**[Width](properties-size-location.md)** – コントロールの左端と右端の間の距離です。

**[X](properties-size-location.md)** – コントロールの左端とその親コンテナー (親コンテナーがない場合は画面) の左端間の距離です。

**[Y](properties-size-location.md)** – コントロールの上端とその親コンテナー (親コンテナーがない場合は画面) の上端間の距離です。

## <a name="related-functions"></a>関連する関数
[**Find**( *FindString*, *WithinString* )](../functions/function-find.md)

## <a name="example"></a>例
1. **[ラベル](control-text-box.md)** コントロールを追加して **Source** という名前を付け、その **[Text](properties-core.md)** プロパティを次の文字列に設定します。

"\<p>私たちは、\&nbsp;非常に \&quot;深い\&quot; グローバリゼーションおよびローカライズを行いました。\<p>"

[コントロールの追加、命名、構成についてはこちらをご覧ください](../add-configure-controls.md)。

1. **HTML テキスト** コントロールを追加し、その **HtmlText** プロパティを次の値に設定します。<br>
   **Source.Text**
   
     **HTML テキスト** コントロールは **[ラベル](control-text-box.md)** コントロールと同じテキストを表示しますが、タグを適切な文字に変換します。


## <a name="accessibility-guidelines"></a>アクセシビリティ ガイドライン
**HTML テキスト**は対話型にするためのものではありません。 テキストの表示目的にのみ使用してください。

### <a name="color-contrast"></a>色のコントラスト
以下の間には適切な色のコントラストが必要です。
* **[色](properties-color-border.md)** と **[塗りつぶし](properties-color-border.md)**
* カスタムの色とその背景があるテキスト

### <a name="screen-reader-support"></a>スクリーン リーダーのサポート
* **HtmlText** を指定する必要があります。

### <a name="keyboard-support"></a>キーボードのサポート
* **HtmlText** には、`<button>`、`<a>`、`<input>` などの対話型の要素を含めることはできません。 PowerApps の **[TabIndex](properties-accessibility.md)** システムでは、**HtmlText** 内の要素は考慮されません。
