---
title: キャンバス アプリの項目の一覧を表示する | Microsoft Docs
description: ギャラリーを使用して、キャンバス アプリの項目の一覧を表示し、条件を指定して一覧をフィルター処理します。
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 09/28/2017
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 6d48b7b6ef1d9d691b733bea9af6ce74d0f2b07a
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2019
ms.locfileid: "73540927"
---
# <a name="show-a-list-of-items-in-powerapps"></a>PowerApps の項目の一覧の表示

キャンバス アプリに **[ギャラリー](controls/control-gallery.md)** コントロールを追加して、任意のデータ ソースからの項目の一覧を表示します。 このトピックでは、データ ソースとして Excel を使用します。 テキスト入力 **[コントロールのフィルター条件に一致する項目のみを表示するように](controls/control-text-input.md)ギャラリー** コントロールを構成して、一覧をフィルター処理します。

## <a name="prerequisites"></a>前提条件

- PowerApps で[コントロールを追加して構成する](add-configure-controls.md)方法について確認します。

- サンプル データを設定するには、次の処理を行います。
    1. [この Excel ファイル](https://az787822.vo.msecnd.net/documentation/get-started-from-data/FlooringEstimates.xlsx)をダウンロードして、チュートリアルのサンプル データを取得します。

    2. Excel ファイルを OneDrive for Business などの[クラウド ストレージ アカウント](connections/cloud-storage-blob-connections.md)にアップロードします。

- 空のアプリを開きます。
    1. [PowerApps にサインインします](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)。

    1. **[自分のアプリを作成する]** で **[キャンバス アプリを一から作成]** を選択します。

    1. アプリに名前を指定し、 **[電話]** を選択し、 **[作成]** を選択します。

    1. **[PowerApps Studio へようこそ]** ダイアログ ボックスが表示されたら、 **[スキップ]** を選択します。

    1. Excel ファイル内の [FlooringEstimates](add-data-connection.md) テーブルへの**接続を追加**します。

## <a name="add-a-gallery-to-a-blank-screen"></a>空の画面にギャラリーを追加する

1. **[挿入]** タブで **[ギャラリー]** を選択し、 **[縦]** を選択します。

    ![縦方向のギャラリーの追加](./media/add-gallery/gallery-dropdown.png)

1. 右側のペインの **[プロパティ]** タブで、 **[アイテム]** ボックスの一覧を開き、 **[Flooring 見積もら]** を選択します。

    ![Flooring の見積もり](./media/add-gallery/select-layout.png)

1. optional **[レイアウト]** ボックスの一覧で、別のオプションを選択します。

## <a name="add-a-gallery-in-a-screen"></a>画面でのギャラリーの追加

1. **[ホーム]** タブで、[**新しい画面** > **リスト画面**] を選択します。

    **ギャラリー**コントロールや、検索バーなどのその他のコントロールを含む画面が表示されます。

1. ギャラリーの **Items** プロパティを `FlooringEstimates` に設定します。

    **ギャラリー** コントロールに、サンプル データが表示されます。

    ![データの表示](./media/add-gallery/show-data-default.png)

## <a name="add-a-control-to-the-gallery-control"></a>ギャラリー コントロールにコントロールを追加する
他のカスタマイズを行う前に、**ギャラリー**コントロールのレイアウトが必要なものと最も厳密に一致していることを確認してください。 ギャラリーテンプレートをさらに変更**して、** **ギャラリー**コントロール内のすべてのデータをどのように表示するかを決定できます。

1. **ギャラリー**コントロールの下部の近くをクリックまたはタップし、左上隅にある鉛筆アイコンを選択して、テンプレートを選択します。

    ![ギャラリー テンプレートの編集](./media/add-gallery/edit-item.png)

2. テンプレートを選択した状態で、 **[ラベル](controls/control-text-box.md)** コントロールを追加し、テンプレート内の他のコントロールと重ならないように、追加したコントロールを移動し、サイズを変更します。

    ![ラベルの追加](./media/add-gallery/add-text-box.png)

3. ギャラリーを選択し、右側のウィンドウの **[プロパティ]** タブで、 **[フィールド]** の横にある **[編集]** を選択します。

4. この手順の最初の方で追加したラベルを選択して、 **[データ]** ウィンドウに強調表示されたリストを表示します。

    ![ドロップダウン リストの表示](./media/add-gallery/open-dropdown.png)

5. このリストで **[価格]** をクリックまたはタップします。

    **ギャラリー** コントロールに新しい値が表示されます。

    ![最終ギャラリー](./media/add-gallery/final-gallery.png)

## <a name="filter-and-sort-a-gallery"></a>ギャラリーのフィルター処理と並べ替え
**ギャラリー[ コントロールの ](controls/properties-core.md)** Items プロパティで、表示する項目を指定します。 この手順では、フィルター条件と順序に基づいてどのレコードを表示するかも決定するように、そのプロパティを構成します。

![検索ボックスと並べ替えアイコン](./media/add-gallery/text-search-box.png)

1. **ギャラリー[ コントロールの ](controls/properties-core.md)** Items プロパティを次の数式に設定します。

    ```powerapps-dot
    Sort
        (If
            (IsBlank(TextSearchBox1.Text),
            FlooringEstimates,
            Filter(
                FlooringEstimates,
                TextSearchBox1.Text in Text(Name)
            )
        ),
        Name,
        If(
            SortDescending1,
            SortOrder.Descending,
            SortOrder.Ascending
        )
    )
    ```

    この数式内の関数について詳しくは、「[数式のリファレンス](formula-reference.md)」をご覧ください。

1. [検索] ボックスをダブルクリックし、その中に製品名の一部またはすべてを入力します。

    フィルター条件に一致する項目のみが表示されます。

1. Alt キーを押しながら並べ替えアイコンを1回以上選択して、並べ替え順序を切り替えます。

    レコードは、製品名に基づいてアルファベット順の昇順と降順を切り替えます。

## <a name="highlight-the-selected-item"></a>選択した項目を強調表示する
**ギャラリー**コントロールの**templatefill**プロパティを、次の例に似た数式に設定しますが、必要に応じて異なる色を指定できます。

**If(ThisItem.IsSelected, LightCyan, White)**

## <a name="change-the-default-selection"></a>既定の選択を変更する
**ギャラリー** コントロールの **Default** プロパティを、既定で選択するレコードに設定します。 たとえば、 **FlooringEstimates**データソースの5番目の項目を指定できます。

**Last(FirstN(FlooringEstimates, 5))**

この例では、**FlooringEstimates** データ ソースの **Hardwood** カテゴリにある、最初の項目を指定します。

**First(Filter(FlooringEstimates, Category = "Hardwood"))**

## <a name="next-steps"></a>次の手順
[フォーム](working-with-forms.md)と[数式](working-with-formulas.md)を使用する方法について確認しておきます。
