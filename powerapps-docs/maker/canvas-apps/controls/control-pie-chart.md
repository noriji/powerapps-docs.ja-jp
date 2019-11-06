---
title: '円グラフ コントロール: リファレンス | Microsoft Docs'
description: 各種プロパティとサンプルを含む円グラフ コントロールに関する情報
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
ms.openlocfilehash: 2037de5ab55839b5908fb4789ca3fcda6836f4d9
ms.sourcegitcommit: 8e42a5996799d9831f8c5a52b0b051a6088d9ce7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/06/2019
ms.locfileid: "73650342"
---
# <a name="pie-chart-control-in-powerapps"></a>PowerApps の円グラフ コントロール
互いに比較した相対値を表示するコントロールです。

## <a name="description"></a>Description
左端の列にラベルを、左から 2 番目の列に値を含むテーブルの相対的なデータを表示する場合は、**円グラフ** コントロールを追加します。

このコントロールは、タイトルの **[ラベル](control-text-box.md)** 、グラフのグラフィック、および**凡例**の 3 つのコントロールを含むグループ化されたコントロールです。

## <a name="chart-key-properties"></a>グラフの主要なプロパティ
**[Items](properties-core.md)** – ギャラリー、リスト、グラフなどのコントロールに表示されるデータのソースです。

**ShowLabels** – 円グラフに、各ウェッジに関連付けられた値を表示するかどうかを指定します。

## <a name="additional-chart-properties"></a>その他のグラフのプロパティ
**[BorderColor](properties-color-border.md)** – コントロールの境界線の色です。

**[BorderStyle](properties-color-border.md)** – コントロールの境界線を **Solid** (実線)、**Dashed** (破線)、**Dotted** (点線)、**None** (なし) のいずれに指定します。

**[BorderThickness](properties-color-border.md)** – コントロールの境界線の太さです。

**[Color](properties-color-border.md)** – コントロールのテキストの色です。

**[DisplayMode](properties-core.md)** – コントロールで、ユーザー入力を許可するか (**Edit**)、データの表示のみを許可するか (**View**)、許可しないか (**Disabled**) を設定します。

**[DisabledBorderColor](properties-color-border.md)** – コントロールの **[DisplayMode](properties-core.md)** プロパティが **Disabled** に設定されている場合のコントロールの境界線の色です。

**Explode** – 円グラフ内のウェッジ間の距離です。

**[Font](properties-text.md)** – テキストを表記するフォントのファミリー名です。

**[Height](properties-size-location.md)** – コントロールの上端と下端の距離です。

**[HoverBorderColor](properties-color-border.md)** – コントロール上にユーザーがマウス ポインターを重ねているときのコントロールの境界線の色です。

**ItemBorderColor** – 円グラフ内の各ウェッジの周りの境界線の色です。

**ItemBorderThickness** – 円グラフ内の各ウェッジの周りの境界線の太さです。

**ItemColorSet** – グラフ内の各データ ポイントの色です。

**LabelPosition** – ウェッジを基準とした、円グラフ内のラベルの場所です。

**[OnSelect](properties-core.md)** – ユーザーがコントロールをタップまたはクリックした場合のアプリの反応を指定します。

**[PressedBorderColor](properties-color-border.md)** – コントロールをユーザーがタップまたはクリックしたときのコントロールの境界線の色です。

**[Size](properties-text.md)** – コントロールに表示されるテキストのフォント サイズです。

**[TabIndex](properties-accessibility.md)** – 他のコントロールに関連するキーボード ナビゲーションの順序です。

**[Visible](properties-core.md)** – コントロールを表示するか非表示にするかを指定します。

**[Width](properties-size-location.md)** – コントロールの左端と右端の間の距離です。

**[X](properties-size-location.md)** – コントロールの左端とその親コンテナー (親コンテナーがない場合は画面) の左端間の距離です。

**[Y](properties-size-location.md)** – コントロールの上端とその親コンテナー (親コンテナーがない場合は画面) の上端間の距離です。

## <a name="related-functions"></a>関連する関数
[**Max**( *DataSource*, *ColumnName* )](../functions/function-aggregates.md)

## <a name="example"></a>例
1. **[[ボタン]](control-button.md)** コントロールを追加し、 **[OnSelect](properties-core.md)** プロパティに次の式を設定します。<br>
   **Collect(Revenue2015, {Product:"Europa", Revenue:27000}, {Product:"Ganymede", Revenue:26300}, {Product:"Callisto", Revenue:29200})**
   
    [コントロールの追加および構成](../add-configure-controls.md)についてはこちらをご覧ください。
   
    **[Collect](../functions/function-clear-collect-clearcollect.md)** 関数または[その他の関数](../formula-reference.md)については各関連記事を参照してください。
2. F5 キーを押して、 **[ボタン](control-button.md)** コントロールをクリックまたはタップしてから、Esc キーを押して既定のワークスペースに戻ります。
3. **円グラフ** コントロールを追加し、その **[Items](properties-core.md)** プロパティを **Revenue2015** に設定します。
   
    **円グラフ** コントロールには、他の製品に関連した製品ごとの収益データが表示されます。


## <a name="accessibility-guidelines"></a>アクセシビリティ ガイドライン
### <a name="color-contrast"></a>色のコントラスト
以下の間には適切な色のコントラストが必要です。
* **ItemColorSet** の各項目
* **ItemColorSet** の各項目と背景色
* **[Color](properties-color-border.md)** と背景色

### <a name="screen-reader-support"></a>スクリーン リーダーのサポート
* タイトルとして機能するには、グラフのグラフィックの直前に **[ラベル](control-text-box.md)** を配置する必要があります。

    > [!NOTE]
  > グラフのグラフィックと**凡例**はスクリーン リーダー ユーザーには表示されません。 代わりに、表形式のデータが表示されます。 また、ボタンを順にクリックしてグラフ内のデータを選択することもできます。

### <a name="low-vision-support"></a>弱視のサポート
* **凡例**が必要です。
* **ShowLabels** を **true** に設定することを検討してください。 こうすることで、弱視のユーザーは個々の円スライスが何を表すかを素早く判断できるようになります。
* **LabelPosition** を **LabelPosition.Outside** に設定することを検討してください。 こうすることで、より一貫した色のコントラストになるので、ラベルの読みやすさが向上します。

### <a name="keyboard-support"></a>キーボードのサポート
* **[TabIndex](properties-accessibility.md)** を 0 以上にして、キーボード ユーザーがそこに移動できるようにする必要があります。

    > [!NOTE]
  > キーボード ユーザーがグラフに移動すると、グラフ内のデータを選択するボタンを順にクリックすることができます。
