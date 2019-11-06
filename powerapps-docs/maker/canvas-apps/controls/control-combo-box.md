---
title: 'コンボ ボックス コントロール: リファレンス | Microsoft Docs'
description: 各種プロパティとサンプルを含むコンボ ボックス コントロールに関する情報
author: chmoncay
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 09/13/2017
ms.author: chmoncay
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 8c4316c8f4aac11903aaad8cb624ff881173b403
ms.sourcegitcommit: 8e42a5996799d9831f8c5a52b0b051a6088d9ce7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/06/2019
ms.locfileid: "73650620"
---
# <a name="combo-box-control-in-powerapps"></a>PowerApps のコンボ ボックス コントロール
ユーザーが、提供された選択肢から選択できるようにするコントロール。  検索と複数選択をサポートしています。

## <a name="description"></a>Description
**コンボ ボックス**コントロールで、選択する項目を検索することができます。  検索は、SearchField プロパティについてサーバー側で実行されるので、パフォーマンスが非常に大規模なデータ ソースによって影響を受けることはありません。  

単一選択モードまたは複数選択モードは SelectMultiple プロパティを介して構成されます。

選択する項目を検索するとき、[データ] ウィンドウの [レイアウト] 設定を変更することで、項目ごとに、1 つのデータ値、2 つの値、または画像および 2 つの値 (Person) の表示を選択できます。

## <a name="people-picker"></a>メンバーの選択
**コンボ ボックス**をメンバーの選択に使用するには、[データ] ウィンドウの [レイアウト] 設定で **Person** テンプレートを選択し、メンバーの下に表示される関連データのプロパティを構成します。

## <a name="key-properties"></a>主要なプロパティ
**[項目](properties-core.md)** – 選択を行う元となるデータのソース。

**DefaultSelectedItems** –ユーザーがコントロールを操作する前に最初に選択された項目。

**SelectedItems** – ユーザーの操作の結果として得られる、選択されている項目の一覧。

**SelectMultiple** – ユーザーが、単一の項目を選択するか、複数の項目を選択するか。

**IsSearchable** – 選択する前にユーザーが項目を検索できるかどうか。

**SearchFields** - ユーザーがテキストを入力するときに検索されるデータ ソースのデータ フィールド。  複数のフィールドを検索するには、ComboBox1.SearchFields = ["MyFirstColumn", "MySecondColumn"] と設定します

## <a name="additional-properties"></a>その他のプロパティ
**[AccessibleLabel](properties-accessibility.md)** – スクリーン リーダー用のラベルです。

**[BorderColor](properties-color-border.md)** – コントロールの境界線の色です。

**[BorderStyle](properties-color-border.md)** – コントロールの境界線を **Solid** (実線)、**Dashed** (破線)、**Dotted** (点線)、**None** (なし) のいずれに指定します。

**[BorderThickness](properties-color-border.md)** – コントロールの境界線の太さです。

**DisplayFields** – 検索によって返される各項目に対して表示されるフィールドの一覧。  プロパティの [オプション] タブで、データ ペインを使用して構成するのが最も簡単です。

**[DisplayMode](properties-core.md)** – コントロールで、ユーザー入力を許可するか (**Edit**)、データの表示のみを許可するか (**View**)、許可しないか (**Disabled**) を設定します。

**[FocusedBorderColor](properties-color-border.md)** – コントロールにフォーカスがあるときのコントロールの境界線の色です。

**[FocusedBorderThickness](properties-color-border.md)** – コントロールにフォーカスがあるときのコントロールの境界線の太さです。

**[Height](properties-size-location.md)** – コントロールの上端と下端の距離です。

**InputTextPlaceholder** – 項目が選択されていない場合、エンドユーザーに表示される指示テキスト。

**OnChange** – ユーザーが選択を変更したときのアプリの応答の仕方。

**OnNavigate** – ユーザーが項目をクリックしたときのアプリの応答の仕方。

**[OnSelect](properties-core.md)** – ユーザーがコントロールをタップまたはクリックした場合のアプリの反応を指定します。

**[TabIndex](properties-accessibility.md)** – 他のコントロールに関連するキーボード ナビゲーションの順序です。

**[Visible](properties-core.md)** – コントロールを表示するか非表示にするかを指定します。

**[Width](properties-size-location.md)** – コントロールの左端と右端の間の距離です。

**[X](properties-size-location.md)** – コントロールの左端とその親コンテナー (親コンテナーがない場合は画面) の左端間の距離です。

**[Y](properties-size-location.md)** – コントロールの上端とその親コンテナー (親コンテナーがない場合は画面) の上端間の距離です。

## <a name="example"></a>例
1. **[挿入]** タブで、 **[コントロール]** メニューを開き、 **[コンボボックス]** を選択します。  

1. 右側のペインの **[プロパティ]** タブで、 **[データソースの選択]** の一覧 (**項目**の横) を開き、データソースを追加または選択します。

1. 同じタブで、 **[編集]** を選択します ( **[フィールド]** の横)。

1. **データ**ペインで、 **[プライマリテキスト]** ボックスを開き、**コンボボックス**コントロールに表示する列を選択します。

1. Alt キーを押しながら下矢印を選択して、**コンボボックス**コントロールを開きます。

    コントロールには、指定したデータソースで指定した列のデータが表示されます。
    
1. optional最初のレコードを既定で表示するには、 **DefaultSelectedItems**プロパティを次の式に設定します。 *DataSource*は実際のデータソースの名前に置き換えてください。

    `First(DataSource)`

## <a name="accessibility-guidelines"></a>アクセシビリティ ガイドライン
### <a name="color-contrast"></a>色のコントラスト
以下の間には適切な色のコントラストが必要です。
* **ChevronFill** と **ChevronBackground**
* **ChevronHoverFill** と **ChevronHoverBackground**
* **SelectionColor** と **SelectionFill**
* **SelectionFill** と **[Fill](properties-color-border.md)**
* **SelectionTagColor** と **SelectionTagFill**

これは、[標準の色のコントラスト要件](../accessible-apps-color.md)に追加されるものです。

### <a name="screen-reader-support"></a>スクリーン リーダーのサポート
* **[AccessibleLabel](properties-accessibility.md)** が存在する必要があります。

    > [!NOTE]
  > タッチ スクリーンでは、スクリーン リーダーのユーザーはコンボ ボックスの内容を順番に移動できます。 コンボ ボックスは、選択したときに内容の表示または非表示を切り替えるボタンとして機能します。

### <a name="keyboard-support"></a>キーボードのサポート
* **[TabIndex](properties-accessibility.md)** を 0 以上にして、キーボード ユーザーがそこに移動できるようにする必要があります。
* フォーカス インジケーターは明確に表示する必要があります。 これを実現するには **[FocusedBorderColor](properties-color-border.md)** と **[FocusedBorderThickness](properties-color-border.md)** を使用します。

    > [!NOTE]
  > Tab キーを押すと、コンボ ボックスに移動またはコンボ ボックスから移動します。 方向キーを押すと、コンボ ボックスの別の内容に移動します。 ドロップ ダウンが開いているときに Esc キーを押すと、ドロップ ダウンは閉じます。
