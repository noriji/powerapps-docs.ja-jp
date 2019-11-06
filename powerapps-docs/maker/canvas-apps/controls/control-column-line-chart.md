---
title: '縦棒グラフ コントロールと折れ線グラフ コントロール: リファレンス | Microsoft Docs'
description: 各種プロパティとサンプルを含む縦棒グラフ コントロールと折れ線グラフ コントロールに関する情報
author: chmoncay
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.date: 10/25/2016
ms.author: chmoncay
ms.reviewer: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 355793d572f6c4b6578d6cabff221c79e0724a93
ms.sourcegitcommit: 8e42a5996799d9831f8c5a52b0b051a6088d9ce7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/06/2019
ms.locfileid: "73650671"
---
# <a name="column-chart-and-line-chart-controls-in-powerapps"></a>PowerApps での縦棒グラフ コントロールと折れ線グラフ コントロール
X 軸と Y 軸からなるグラフとしてデータを表示するコントロールです。

## <a name="description"></a>Description
**縦棒グラフ** コントロールと**折れ線グラフ** コントロールはグループ化されたコントロールです。 各グループには、タイトルの **[ラベル](control-text-box.md)** 、グラフのグラフィック、および**凡例**の 3 つのコントロールが含まれています。

## <a name="chart-key-properties"></a>グラフの主要なプロパティ
**[Items](properties-core.md)** – ギャラリー、リスト、グラフなどのコントロールに表示されるデータのソースです。

**NumberOfSeries** – 縦棒グラフまたは折れ線グラフに反映されるデータ列の数です。

## <a name="additional-chart-properties"></a>その他のグラフのプロパティ
**[BorderColor](properties-color-border.md)** – コントロールの境界線の色です。

**[BorderStyle](properties-color-border.md)** – コントロールの境界線を **Solid** (実線)、**Dashed** (破線)、**Dotted** (点線)、**None** (なし) のいずれに指定します。

**[BorderThickness](properties-color-border.md)** – コントロールの境界線の太さです。

**[Color](properties-color-border.md)** – コントロールのテキストの色です。

**[DisabledBorderColor](properties-color-border.md)** – コントロールの **[DisplayMode](properties-core.md)** プロパティが **Disabled** に設定されている場合のコントロールの境界線の色です。

**[DisplayMode](properties-core.md)** – コントロールで、ユーザー入力を許可するか (**Edit**)、データの表示のみを許可するか (**View**)、許可しないか (**Disabled**) を設定します。

**[Font](properties-text.md)** – テキストを表記するフォントのファミリー名です。

**GridStyle** – 縦棒グラフまたは折れ線グラフで、X 軸と Y 軸のどちらか一方または両方を表示するか、または両方とも表示しないかを指定します。

**[Height](properties-size-location.md)** – コントロールの上端と下端の距離です。

**[HoverBorderColor](properties-color-border.md)** – コントロール上にユーザーがマウス ポインターを重ねているときのコントロールの境界線の色です。

**ItemColorSet** – グラフ内の各データ ポイントの色です。

**ItemsGap** – 縦棒グラフの縦棒間の距離です。

* **ItemsGap** プロパティは、**縦棒グラフ** コントロールでは使用できますが、**折れ線グラフ** コントロールでは使用できません。

**Markers** – 縦棒グラフまたは折れ線グラフで各データ ポイントの値を表示するかどうかを指定します。

**MarkerSuffix** – **Markers** プロパティが **true** に設定されている縦棒グラフで、各値の後に表示するテキストです。

* **MarkerSuffix** プロパティは、**縦棒グラフ** コントロールでは使用できますが、**折れ線グラフ** コントロールでは使用できません。

**MinimumBarWidth** – 縦棒グラフの縦棒の表示に可能な最も狭い幅です。

* **MinimumBarWidth** プロパティは、**縦棒グラフ** コントロールでは使用できますが、**折れ線グラフ** コントロールでは使用できません。

**[OnSelect](properties-core.md)** – ユーザーがコントロールをタップまたはクリックした場合のアプリの反応を指定します。

**[PaddingBottom](properties-size-location.md)** – コントロール内のテキストとそのコントロールの下端間の距離です。

**[PaddingLeft](properties-size-location.md)** – コントロール内のテキストとそのコントロールの左端間の距離です。

**[PaddingRight](properties-size-location.md)** – コントロール内のテキストとそのコントロールの右端間の距離です。

**[PaddingTop](properties-size-location.md)** – コントロール内のテキストとそのコントロールの上端間の距離です。

**[PressedBorderColor](properties-color-border.md)** – コントロールをユーザーがタップまたはクリックしたときのコントロールの境界線の色です。

**SeriesAxisMax** – 縦棒グラフまたは折れ線グラフの Y 軸の最大値です。

* **SeriesAxisMax** プロパティは、**縦棒グラフ** コントロールでは使用できますが、**折れ線グラフ** コントロールでは使用できません。

**SeriesAxisMin** – 縦棒グラフの Y 軸の最小値を決める値です。

* **SeriesAxisMin** プロパティは、**縦棒グラフ** コントロールでは使用できますが、**折れ線グラフ** コントロールでは使用できません。

**[Size](properties-text.md)** – コントロールに表示されるテキストのフォント サイズです。

**[TabIndex](properties-accessibility.md)** – 他のコントロールに関連するキーボード ナビゲーションの順序です。

**[Visible](properties-core.md)** – コントロールを表示するか非表示にするかを指定します。

**[Width](properties-size-location.md)** – コントロールの左端と右端の間の距離です。

**[X](properties-size-location.md)** – コントロールの左端とその親コンテナー (親コンテナーがない場合は画面) の左端間の距離です。

**XLabelAngle** – 縦棒グラフまたは折れ線グラフの X 軸の下に表示されるラベルの角度です。

**[Y](properties-size-location.md)** – コントロールの上端とその親コンテナー (親コンテナーがない場合は画面) の上端間の距離です。

**YAxisMax** – 折れ線グラフの Y 軸の最大値です。

* **YAxisMax** プロパティは、**折れ線グラフ** コントロールでは使用できますが、**縦棒グラフ** コントロールでは使用できません。

**YAxisMin** – 折れ線グラフの Y 軸の最小値です。

* **YAxisMin** プロパティは、**折れ線グラフ** コントロールでは使用できますが、**縦棒グラフ** コントロールでは使用できません。

**YLabelAngle** – 折れ線グラフまたは縦棒グラフの Y 軸の横に表示されるラベルの角度です。

## <a name="related-functions"></a>関連する関数
[**Max**( *DataSource*, *ColumnName* )](../functions/function-aggregates.md)

## <a name="example"></a>例
1. **[[ボタン]](control-button.md)** コントロールを追加し、 **[OnSelect](properties-core.md)** プロパティに次の式を設定します。<br>
   **Collect(Revenue, {Year:"2013", Europa:24000, Ganymede:22300, Callisto:21200}, {Year:"2014", Europa:26500, Ganymede:25700, Callisto:24700},{Year:"2014", Europa:27900, Ganymede:28300, Callisto:25600})**
   
    [コントロールの追加および構成](../add-configure-controls.md)についてはこちらをご覧ください。
   
    **[Collect](../functions/function-clear-collect-clearcollect.md)** 関数または[その他の関数](../formula-reference.md)については各関連記事を参照してください。
2. F5 キーを押して、 **[ボタン](control-button.md)** コントロールをクリックまたはタップしてから、Esc キーを押して既定のワークスペースに戻ります。
3. **縦棒グラフ** コントロールまたは**折れ線グラフ** コントロールを追加し、 **[Items](properties-core.md)** プロパティを **Revenue** に、**NumberOfSeries** プロパティを **3** に設定します。
   
    コントロールに、過去 3 年間の各製品の売上データが表示されます。


## <a name="accessibility-guidelines"></a>アクセシビリティ ガイドライン
### <a name="color-contrast"></a>色のコントラスト
以下の間には適切な色のコントラストが必要です。
* **ItemColorSet** の各項目
* **ItemColorSet** の各項目と背景色
* **[Color](properties-color-border.md)** と背景色

### <a name="screen-reader-support"></a>スクリーン リーダーのサポート
* タイトルとして機能するには、グラフのグラフィックの直前に **[ラベル](control-text-box.md)** を配置する必要があります。
* グラフのグラフィックの概要を追加することを検討してください。 たとえば、"折れ線グラフは、今年の 3 月から 8 月の売上が着実に増加していることを示しています" などです。

    > [!NOTE]
  > グラフのグラフィックと**凡例**はスクリーン リーダー ユーザーには表示されません。 代わりに、表形式のデータが表示されます。 また、ボタンを順にクリックしてグラフ内のデータを選択することもできます。

### <a name="low-vision-support"></a>弱視のサポート
* 複数の系列が表示されている場合は、**凡例**が必要です。
* **GridStyle** を両方の軸を示す GridStyle.All に設定することを検討してください。 こうすることで、すべてのユーザーがデータの規模を正確に判断できるようになります。
* **縦棒グラフ**の場合は、**Markers** を **true** に設定することを検討してください。 こうすることで、弱視のユーザーが列の値を判断できるようになります。

### <a name="keyboard-support"></a>キーボードのサポート
* **[TabIndex](properties-accessibility.md)** を 0 以上にして、キーボード ユーザーがそこに移動できるようにする必要があります。

    > [!NOTE]
  > キーボード ユーザーがグラフに移動すると、グラフ内のデータを選択するボタンを順にクリックすることができます。
