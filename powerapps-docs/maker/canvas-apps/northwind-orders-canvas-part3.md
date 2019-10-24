---
title: キャンバスアプリで詳細ギャラリーを作成する |Microsoft Docs
description: Northwind Traders のデータを管理するためのキャンバスアプリで詳細ギャラリーを作成する
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 04/25/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 7a975669d1e22289b7152b830808631992389a1f
ms.sourcegitcommit: 57b968b542fc43737330596d840d938f566e582a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2019
ms.locfileid: "71991628"
---
# <a name="create-a-detail-gallery-in-a-canvas-app"></a>キャンバスアプリで詳細ギャラリーを作成する

Northwind Traders データベースで架空のデータを管理するためのキャンバスアプリで詳細ギャラリーを作成する手順について説明します。 このトピックは、Common Data Service でリレーショナルデータに対するビジネスアプリケーションを構築する方法について説明するシリーズの一部です。 最適な結果を得るには、次のトピックを参照してください。

1. [注文ギャラリーを作成](northwind-orders-canvas-part1.md)します。
1. [概要フォームを作成](northwind-orders-canvas-part2.md)します。
1. 詳細ギャラリーを作成します (**このトピック**)。

> [!div class="mx-imgBorder"]
> 画面領域の ![Definition ](media/northwind-orders-canvas-part1/orders-parts.png)

## <a name="prerequisites"></a>前提条件

このトピックの前半で説明したように、このトピックを開始する前に、データベースをインストールする必要があります。 次に、注文書ギャラリーと概要フォームを作成するか、 **Northwind Orders (キャンバス)-Begin Part 3**アプリを開きます。このアプリには、そのギャラリーとそのフォームが既に含まれています。

## <a name="create-another-title-bar"></a>別のタイトルバーを作成する

1. 画面の上部で、タイトルバーとして機能する[**ラベル**](controls/control-text-box.md)コントロールを選択し、Ctrl + C キーを押してコピーします。次に、Ctrl + V キーを押して貼り付けます。

    > [!div class="mx-imgBorder"]
    > タイトルバーを ![Copy して貼り付ける ](media/northwind-orders-canvas-part3/details-01.png)

1. [概要] フォームのすぐ下に表示されるように、コピーのサイズを変更して移動します。

1. 次のいずれかの方法で、コピーからテキストを削除します。

    - テキストをダブルクリックして選択し、Del キーを押します。
    - ラベルの**Text**プロパティを空の文字列 ( **""** ) に設定します。

    > [!div class="mx-imgBorder"]
    > タイトルバーのコピーからテキストを ![Remove ](media/northwind-orders-canvas-part3/details-02.png)

## <a name="add-a-gallery"></a>ギャラリーを追加する

1. **空の垂直**レイアウトで[**ギャラリー**](controls/control-gallery.md)コントロールを挿入します。

    > [!div class="mx-imgBorder"]
    > 空の垂直方向のギャラリーを ![Add ](media/northwind-orders-canvas-part3/details-03.png)

    注文の詳細を表示する新しいギャラリーが左上隅に表示されます。

    > [!div class="mx-imgBorder"]
    > 注文の ![Default 場所-詳細ギャラリー ](media/northwind-orders-canvas-part3/details-04.png)

1. **データ**ペインを閉じ、詳細ギャラリーを新しいタイトルバーの下の右下隅にサイズ変更して移動します。

    > [!div class="mx-imgBorder"]
    > 注文の ![Final 場所-詳細ギャラリー ](media/northwind-orders-canvas-part3/details-05.png)

1. 詳細ギャラリーの**Items**プロパティを次の数式に設定します。

    ```powerapps-dot
    Gallery1.Selected.'Order Details'
    ```

    > [!div class="mx-imgBorder"]
    > 詳細ギャラリーの Items プロパティを ![Set ](media/northwind-orders-canvas-part3/details-06.png)

    エラーが表示された場合は、注文書ギャラリーが**gallery1.selected**という名前であることを確認します (左端近くの**ツリービュー**ペイン)。 ギャラリーに別の名前が付いている場合は、名前を**gallery1.selected**に変更します。

    2つのギャラリーをリンクしました。 ユーザーが注文ギャラリーで注文を選択すると、その選択によって**Orders**エンティティ内のレコードが識別されます。 この注文に1つ以上の行項目が含まれている場合、 **Orders**エンティティ内のレコードは**order details**エンティティ内の1つ以上のレコードにリンクされ、それらのレコードのデータは詳細ギャラリーに表示されます。 この動作は、 **Orders**エンティティと**Order Details**エンティティの間に作成された一対多のリレーションシップを反映しています。 指定した数式は、ドット表記を使用してそのリレーションシップを "ウォーク" します。

    > [!div class="mx-imgBorder"]
    > Orders エンティティと Order Details エンティティの ![One 対多リレーションシップ ](media/northwind-orders-canvas-part3/schema-orders-rel.png)

## <a name="show-product-names"></a>製品名の表示

1. 詳細ギャラリーで、[**挿入] タブから [アイテムの追加**] を選択し、ギャラリーテンプレートを選択します。

    > [!div class="mx-imgBorder"]
    > 詳細ギャラリーのテンプレートを ![Select ](media/northwind-orders-canvas-part3/details-07.png)

    ギャラリー自体ではなく、ギャラリーテンプレートを選択していることを確認します。 境界ボックスは、ギャラリーの境界内に少しだけ配置する必要があり、ギャラリーの高さよりも短くなる可能性があります。 このテンプレートにコントロールを挿入すると、ギャラリー内の各項目に対してコントロールが繰り返し表示されます。

1. **[挿入]** タブで、詳細ギャラリーにラベルを挿入します。

    ギャラリー内にラベルが表示されます。そうでない場合は、もう一度やり直してください。ただし、ラベルを挿入する前に、ギャラリーのテンプレートを選択してください。

    > [!div class="mx-imgBorder"]
    > 詳細ギャラリーにラベルを ![Add ](media/northwind-orders-canvas-part3/details-08.png)

1. 新しいラベルの**Text**プロパティを次の数式に設定します。

    ```powerapps-dot
    ThisItem.Product.'Product Name'
    ```

    テキストが表示されない場合は、注文書ギャラリーの下部付近にある **[注文 0901]** の矢印を選択します。

1. フルテキストが表示されるようにラベルのサイズを変更します。

    > [!div class="mx-imgBorder"]
    > 製品名を注文の詳細に ![Show ](media/northwind-orders-canvas-part3/details-09.png)

    この式は、 **Order Details**エンティティ内のレコードからウォークします。 このレコードは、多対一のリレーションシップによって**注文製品**エンティティに対して次の**項目**に保持されます。

    > [!div class="mx-imgBorder"]
    > Order Details エンティティと Order Product エンティティの間の ![Many 対一のリレーションシップ ](media/northwind-orders-canvas-part3/schema-orderdetails-rel.png)

    **製品名**フィールド (および使用するその他のフィールド) は、次のように抽出されます。

    > [!div class="mx-imgBorder"]
    > Order Products エンティティの ![Fields ](media/northwind-orders-canvas-part3/schema-products-fields.png)

## <a name="show-product-images"></a>製品イメージの表示

1. **[挿入]** タブで、[**イメージ**](controls/control-image.md)コントロールを詳細ギャラリーに挿入します。

    > [!div class="mx-imgBorder"]
    > ![Insert image コントロール ](media/northwind-orders-canvas-part3/details-10.png)

1. イメージとラベルを左右に並べて移動します。

    > [!TIP]
    > コントロールのサイズと位置をきめ細かく制御するには、alt キーを押したままサイズ変更または移動を開始し、Alt キーを押しながらコントロールのサイズ変更や移動を続けます。

    > [!div class="mx-imgBorder"]
    > ![Move image コントロール ](media/northwind-orders-canvas-part3/details-11.png)

1. イメージの**image**プロパティを次の数式に設定します。

    ```powerapps-dot
    ThisItem.Product.Picture
    ```

    ここでも、式は、この注文詳細に関連付けられている製品を参照し、**画像**フィールドを抽出して表示します。

    > [!div class="mx-imgBorder"]
    > ![Show 製品イメージ ](media/northwind-orders-canvas-part3/details-12.png)

1. 複数の**注文明細**レコードが一度に表示されるように、ギャラリーのテンプレートの高さを小さくします。

    > [!div class="mx-imgBorder"]
    > ギャラリーのテンプレートを ![Shorten ](media/northwind-orders-canvas-part3/details-13.png)

## <a name="show-product-quantity-and-cost"></a>製品の数量とコストを表示する

1. **[挿入]** タブで、詳細ギャラリーに別のラベルを挿入し、そのサイズを変更して、新しいラベルを製品情報の右側に移動します。

1. 新しいラベルの**Text**プロパティを次の式に設定します。

    ```powerapps-dot
    ThisItem.Quantity
    ```

    この数式は、 **Order Details**エンティティから直接情報を取得します (リレーションシップは必要ありません)。

    > [!div class="mx-imgBorder"]
    > ![Show の製品数量 ](media/northwind-orders-canvas-part3/details-13b.png) 

1. **[ホーム]** タブで、このコントロールの配置を**右**に変更します。

    > [!div class="mx-imgBorder"]
    > ![Change アラインメント ](media/northwind-orders-canvas-part3/details-14.png)

1. **[挿入]** タブで、詳細ギャラリーに別のラベルを挿入し、ラベルのサイズを変更して、数量ラベルの右側に移動します。

1. 新しいラベルの**Text**プロパティを次の数式に設定します。

    ```powerapps-dot
    Text( ThisItem.'Unit Price', "[$-en-US]$ #,###.00" )
    ```

    言語タグ ( **[$-en-us]** ) を含めない場合、言語と地域に基づいて追加されます。 別の言語タグを使用する場合は、右角かっこ ( **]** ) の直後にある **$** を削除し、その位置に独自の通貨記号を追加します。

    > [!div class="mx-imgBorder"]
    > ![Show 単価 ](media/northwind-orders-canvas-part3/details-15.png)

1. **[ホーム]** タブで、このコントロールの配置を**右**に変更します。

    > [!div class="mx-imgBorder"]
    > ![Change アラインメント ](media/northwind-orders-canvas-part3/details-16.png)

1. **[挿入]** タブで、詳細ギャラリーに別のラベルコントロールを挿入し、新しいラベルをサイズ変更して、単価の右側に移動します。

1. 新しいラベルの**Text**プロパティを次の数式に設定します。

    ```powerapps-dot
    Text( ThisItem.Quantity * ThisItem.'Unit Price', "[$-en-US]$ #,###.00" )
    ```

    ここでも、言語タグ ( **[$-en-us]** ) を含めない場合、言語と地域に基づいて追加されます。 タグが異なる場合は、閉じ角かっこ ( **]** ) の直後に **$** ではなく、独自の通貨記号を使用します。

    > [!div class="mx-imgBorder"]
    > ![Show の延長価格 ](media/northwind-orders-canvas-part3/details-17.png)

1. **[ホーム]** タブで、このコントロールの配置を**右**に変更します。

    > [!div class="mx-imgBorder"]
    > ![Change アラインメント ](media/northwind-orders-canvas-part3/details-18.png)

    これで、詳細ギャラリーにコントロールが追加されました。

1. **[ツリービュー]** ペインで **[Screen1]** を選択し、詳細ギャラリーが選択されていないことを確認します。

## <a name="add-text-to-the-new-title-bar"></a>新しいタイトルバーにテキストを追加する

1. **[挿入]** タブで、画面に別のラベルを挿入します。

    > [!div class="mx-imgBorder"]
    > ![Insert ラベル ](media/northwind-orders-canvas-part3/details-19.png)

1. 2番目のタイトルバーで、製品の画像の上に新しいラベルのサイズを変更して移動し、 **[ホーム]** タブでテキストの色を白に変更します。

1. ラベルのテキストをダブルクリックし、「 **Product**:」と入力します。

    > [!div class="mx-imgBorder"]
    > 製品 ](media/northwind-orders-canvas-part3/details-20.png) にラベルテキストを ![Change

1. Product ラベルをコピーして貼り付け、[quantity] 列の上にあるコピーのサイズを変更して移動します。

1. 新しいラベルのテキストをダブルクリックし、「 **Quantity**:」と入力します。

    > [!div class="mx-imgBorder"]
    > ラベルのテキストを Quantity ](media/northwind-orders-canvas-part3/details-21.png) に ![Change

1. Quantity ラベルをコピーして貼り付け、そのサイズを変更して、そのコピーを単位価格列の上に移動します。

1. 新しいラベルのテキストをダブルクリックし、「 **Unit Price**:」と入力します。

    > [!div class="mx-imgBorder"]
    > ラベルテキストを ![Change 単位価格 ](media/northwind-orders-canvas-part3/details-22.png)

1. ユニット価格ラベルをコピーして貼り付け、拡張価格列の上にあるコピーのサイズを変更して移動します。

1. 新しいラベルのテキストをダブルクリックし、「 **Extended**:」と入力します。

    > [!div class="mx-imgBorder"]
    > 拡張 ](media/northwind-orders-canvas-part3/details-23.png) へのラベルテキストの ![Change

## <a name="display-order-totals"></a>注文合計の表示

1. 詳細ギャラリーの高さを小さくして、画面の下部に注文合計の領域を確保します。

    > [!div class="mx-imgBorder"]
    > ![Shorten の順序-詳細なギャラリー ](media/northwind-orders-canvas-part3/sum-01.png)

1. 画面の中央にタイトルバーをコピーして貼り付け、画面の下部にコピーを移動します。

    > [!div class="mx-imgBorder"]
    > タイトルバーを ![Copy し、コピーを下端に移動 ](media/northwind-orders-canvas-part3/sum-02.png)

1. 中央のタイトルバーから製品ラベルをコピーして貼り付け、 **[Quantity]** 列の左側にある下部のタイトルバーにコピーを移動します。

1. 新しいラベルのテキストをダブルクリックし、次のテキストを入力します。<br>**注文合計:**

    > [!div class="mx-imgBorder"]
    > 注文合計の ![Add ラベル ](media/northwind-orders-canvas-part3/sum-03.png)

1. "注文-合計" ラベルをコピーして貼り付け、[注文-合計] ラベルの右側にコピーを移動します。

1. 新しいラベルの**Text**プロパティを次の数式に設定します。

    ```powerapps-dot
    Sum( Gallery1.Selected.'Order Details', Quantity )
    ```

    この数式は委任の警告を示していますが、1つの注文に500以上の製品が含まれていないため、無視してかまいません。

1. **[ホーム]** タブで、新しいラベルのテキストの配置を**右**に設定します。

    > [!div class="mx-imgBorder"]
    > ![Change アラインメント ](media/northwind-orders-canvas-part3/sum-04.png)

1. このラベルコントロールをコピーして貼り付け、サイズを変更して、**拡張**列の下にコピーします。

1. コピーの**Text**プロパティを次の数式に設定します。

    ```powerapps-dot
    Text( Sum( Gallery1.Selected.'Order Details', Quantity * 'Unit Price' ), "[$-en-US]$ #,###.00" )
    ```

    この数式は委任の警告を示していますが、1つの注文に500以上の製品が含まれていないため、無視してかまいません。

    > [!div class="mx-imgBorder"]
    > 注文 ](media/northwind-orders-canvas-part3/sum-05.png) の総コスト ![Show

## <a name="add-space-for-new-details"></a>新しい詳細用の領域を追加する

どのギャラリーでもデータを表示できますが、更新したりレコードを追加したりすることはできません。 詳細ギャラリーで、ユーザーが**Order Details**エンティティでレコードを構成し、そのレコードを注文に挿入できる領域を追加します。

1. 詳細ギャラリーの高さを小さくして、そのギャラリーの単一項目の編集スペースを確保できるようにします。

    この領域では、ユーザーが注文の詳細を追加できるようにコントロールを追加します。

    > [!div class="mx-imgBorder"]
    > 詳細ギャラリーを ![Shorten ](media/northwind-orders-canvas-part3/add-details-01.png)

1. **[挿入]** タブで、ラベルを挿入し、そのサイズを詳細ギャラリーの下に移動します。

    > [!div class="mx-imgBorder"]
    > ラベルを ![Insert ](media/northwind-orders-canvas-part3/add-details-02.png)

1. 新しいラベルのテキストをダブルクリックし、del キーを押します。

1. **[ホーム]** タブで、新しいラベルの**塗りつぶし**の色を **[ライトブルー]** に設定します。

    > [!div class="mx-imgBorder"]
    > ラベルの塗りつぶしを薄い青に ![Change ](media/northwind-orders-canvas-part3/add-details-03.png)

## <a name="add-the-order-details-data-source"></a>Order Details データソースを追加する

1. **[表示]** タブで **[データソース]** を選択し、**データ**ペインで **[データソースの追加]** を選択します。

    > [!div class="mx-imgBorder"]
    > データソース ](media/northwind-orders-canvas-part3/add-details-04.png) の ![Add

1. **Common Data Service**の選択:

    > [!div class="mx-imgBorder"]
    > ![Select Common Data Service ](media/northwind-orders-canvas-part3/add-details-05.png)

1. **データ**ペインの上部にある [検索] ボックスに「 **order** 」と入力し、 **[order Details]** チェックボックスをオンにして、ウィンドウの下部にある **[接続]** を選択します。

    > [!div class="mx-imgBorder"]
    > ![Specify Order details エンティティ ](media/northwind-orders-canvas-part3/add-details-06.png)

    アプリに別のデータソースを追加しました。

    > [!div class="mx-imgBorder"]
    > データソースの ![List ](media/northwind-orders-canvas-part3/add-details-07.png)

    アプリは1対多の関係を読み取ることができますが、アプリではまだ変更を書き戻すことができないため、このデータソースを追加する必要があります。 アプリは、関連エンティティに直接変更を加える必要があります。

1. **データ**ペインを閉じます。

## <a name="select-a-product"></a>製品を選択してください

1. **[挿入]** タブで、[**コントロール** > **コンボボックス**] を選択します。

    > [!div class="mx-imgBorder"]
    > ![Insert コンボボックス ](media/northwind-orders-canvas-part3/add-details-08.png)

    左上隅に[**コンボボックス**](controls/control-combo-box.md)コントロールが表示されます。

1. コンボボックスの**Items**プロパティを次の数式に設定します。

    ```powerapps-dot
    Choices( 'Order Details'.Product )
    ```

    > [!div class="mx-imgBorder"]
    > コンボボックスの Items プロパティを ![Set ](media/northwind-orders-canvas-part3/add-details-09.png)

    [**Choice**](functions/function-choices.md)関数は、 **Order Details**エンティティの**Product**フィールドに使用可能なすべての値のテーブルを返します。 このフィールドは多対一のリレーションシップで参照されるため、**選択**すると**Order Products**エンティティ内のすべてのレコードが返されます。

    > [!NOTE]
    > **選択肢**をオプションセットと共に使用して、すべてのオプションのテーブルを返すこともできます。 手順では、この方法については説明しませんでしたが、概要フォームに**注文の状態**を表示するコンボボックスを追加したときに既に使用しています。

1. **データ**ペインで、**プライマリテキスト**リストを開き、 **[nwind_productname]** を選択します。 

1. **[Searchfield]** の一覧を開き、 **[nwind_productname]** を選択します。

    この場合、**データ**ペインでは表示名がサポートされていないため、論理名を指定します。

    > [!div class="mx-imgBorder"]
    > コンボボックスのプライマリテキストを ![Set ](media/northwind-orders-canvas-part3/add-details-10.png)

1. **データ**ペインを閉じます。

1. 右端の **[プロパティ]** タブで、下にスクロールし、 **[複数選択を許可]** する をオフにして、 **[検索を許可]** する がオンになっていることを確認します。

    > [!div class="mx-imgBorder"]
    > 複数の選択を ![Disable して検索を有効にする ](media/northwind-orders-canvas-part3/add-details-12.png)

1. 次のように、コンボボックスのサイズを変更して、詳細ギャラリーの product name 列のすぐ下にある薄い青色の領域に移動します。

    > [!div class="mx-imgBorder"]
    > ![Move コンボボックス ](media/northwind-orders-canvas-part3/add-details-13.png)

    このコンボボックスで、ユーザーは、アプリによって作成される注文の**詳細**レコードの**Product**エンティティ内のレコードを指定します。

1. Alt キーを押しながら、コンボボックスの下矢印を選択します。

    > [!TIP]
    > Alt キーを押したままにすると、プレビューモードを開かずに PowerApps Studio のコントロールと対話できます。

1. 表示された製品の一覧で、製品を選択します。

    > [!div class="mx-imgBorder"]
    > コンボボックスに製品を ![Select ](media/northwind-orders-canvas-part3/add-details-14.png)

## <a name="add-a-product-image"></a>製品イメージを追加する

1. **[挿入]** タブで、[**メディア** > **イメージ**] を選択します。

    > [!div class="mx-imgBorder"]
    > ![Insert image コントロール ](media/northwind-orders-canvas-part3/add-details-15.png)

    [**イメージ**](controls/control-image.md)コントロールは、左上隅に表示されます。

    > [!div class="mx-imgBorder"]
    > イメージコントロールの ![Default の場所 ](media/northwind-orders-canvas-part3/add-details-16.png)

1. 画像のサイズを変更し、他の製品イメージの下にある薄い青の領域に移動し、コンボボックスの横に移動します。

1. イメージの**image**プロパティを次のように設定します。

    ```powerapps-dot
    ComboBox1.Selected.Picture
    ```

    > [!div class="mx-imgBorder"]
    > イメージの Image プロパティを ![Set ](media/northwind-orders-canvas-part3/add-details-17.png)

    ここでは、従業員の写真を概要フォームに表示するために使用したのと同じトリックを使用しています。 コンボボックスの**選択**したプロパティによって、ユーザーが選択した製品 ( **[画像]** フィールドなど) のすべてのレコードが返されます。

## <a name="add-a-quantity-box"></a>数量ボックスの追加

1. **[挿入]** タブで、[**テキスト** > **テキスト入力**] を選択します。

    > [!div class="mx-imgBorder"]
    > ![Add テキスト入力ボックス ](media/northwind-orders-canvas-part3/add-details-18.png)

    左上隅に[**テキスト入力**](controls/control-text-input.md)コントロールが表示されます。

    > [!div class="mx-imgBorder"]
    > テキスト入力ボックスの ![Default の場所 ](media/northwind-orders-canvas-part3/add-details-19.png)

1. テキスト入力ボックスのサイズを変更し、詳細ギャラリーの quantity 列の下にあるコンボボックスの右側に移動します。

    > [!div class="mx-imgBorder"]
    > ![Resize と移動テキスト-入力ボックス ](media/northwind-orders-canvas-part3/add-details-20.png)

    このテキスト入力ボックスを使用すると、ユーザーは**Order Details**レコードの**Quantity**フィールドを指定します。

1. このコントロールの**既定**のプロパティを **""** に設定します。

    > [!div class="mx-imgBorder"]
    > テキスト入力ボックスの * * 既定の * * プロパティを ![Set ](media/northwind-orders-canvas-part3/add-details-21.png)

1. **[ホーム]** タブで、このコントロールのテキストの配置を**右**に設定します。

    > [!div class="mx-imgBorder"]
    > ![Change アラインメント ](media/northwind-orders-canvas-part3/add-details-22.png)

## <a name="show-the-unit-and-extended-prices"></a>ユニットと拡張価格を表示する

1. **[挿入]** タブで、**ラベル**コントロールを挿入します。

    ラベルは、画面の左上隅に表示されます。

    > [!div class="mx-imgBorder"]
    > ラベルを ![Insert ](media/northwind-orders-canvas-part3/add-details-23.png)

1. ラベルのサイズを変更し、テキスト入力コントロールの右側に移動し、ラベルの**text**プロパティを次の数式に設定します。

    ```powerapps-dot
    Text( ComboBox1.Selected.'List Price', "[$-en-US]$ #,###.00" )
    ```

    > [!div class="mx-imgBorder"]
    > ラベルの Text プロパティを ![Set ](media/northwind-orders-canvas-part3/add-details-24.png)

    このコントロールは、 **Order Products**エンティティの**表示価格**を表示します。 この値により、 **Order Details**レコードの**Unit Price**フィールドが決定されます。

    > [!NOTE]
    > このシナリオでは、値は読み取り専用ですが、他のシナリオでは、アプリユーザーが変更するためにを呼び出すことがあります。 その場合は、**テキスト入力**コントロールを使用し、その**既定**のプロパティを [**価格の表示]** に設定します。

1. **[ホーム]** タブで、リスト価格ラベルのテキストの配置を **[右]** に設定します。

    > [!div class="mx-imgBorder"]
    > ![Change アラインメント ](media/northwind-orders-canvas-part3/add-details-25.png)

1. List-price ラベルをコピーして貼り付け、そのサイズを変更して、リスト価格ラベルの右側にコピーします。

1. 新しいラベルの**Text**プロパティを次の数式に設定します。

    ```powerapps-dot
    Text( Value(TextInput1.Text) * ComboBox1.Selected.'List Price', "[$-en-US]$ #,###.00" )
    ```

    > [!div class="mx-imgBorder"]
    > 新しいラベルの Text プロパティを ![Set ](media/northwind-orders-canvas-part3/add-details-27.png)

    このコントロールは、アプリユーザーが指定した数量と、アプリユーザーが選択した製品の表示価格に基づいて、拡張された価格を表示します。 これは、アプリユーザーのための情報です。

1. Quantity のテキスト入力コントロールをダブルクリックし、数値を入力します。

    **拡張**価格ラベルは、新しい値が表示されるように再計算されます。

    > [!div class="mx-imgBorder"]
    > 数量を ![Specify し、延長価格を表示 ](media/northwind-orders-canvas-part3/add-details-28.png)

## <a name="add-an-add-icon"></a>追加アイコンを追加する

1. **[挿入]** タブで、 **[追加]**  >  **[アイコン]** を選択します。

    > [!div class="mx-imgBorder"]
    > ![Insert 追加アイコン ](media/northwind-orders-canvas-part3/add-details-29.png)

    アイコンが画面の左上隅に表示されます。

    > [!div class="mx-imgBorder"]
    > [追加] アイコンの ![Default の場所 ](media/northwind-orders-canvas-part3/add-details-30.png)

1. このアイコンを明るい青い領域の右端に移動し、アイコンの**Onselect**プロパティを次の数式に設定します。

    ```powerapps-dot
    Patch( 'Order Details',
        Defaults('Order Details'),
        {
            Order: Gallery1.Selected,
            Product: ComboBox1.Selected,
            Quantity: Value(TextInput1.Text),
            'Unit Price': ComboBox1.Selected.'List Price'
        }
    );
    Refresh( Orders );
    Reset( ComboBox1 );
    Reset( TextInput1 )
    ```

    > [!div class="mx-imgBorder"]
    > アイコンの OnSelect プロパティを ![Set ](media/northwind-orders-canvas-part3/add-details-31.png)

    一般に、 [**Patch**](functions/function-patch.md)関数はレコードを更新し、作成します。この数式の特定の引数は、関数が行う変更を正確に決定します。

    - 最初の引数は、関数がレコードを更新または作成するデータソース (この場合は**Order Details**エンティティ) を指定します。
    - 2番目の引数は、3番目の引数で特に指定されていない限り、関数が**Order Details**エンティティの既定値を持つレコードを作成することを指定します。
    - 3番目の引数は、新しいレコードの4つの列にユーザーの値が含まれることを指定します。

      - **Order**列には、ユーザーが注文ギャラリーで選択した注文の番号が含まれます。
      - **Product**列には、製品を表示するコンボボックスでユーザーが選択した製品の名前が含まれます。
      - **Quantity**列には、ユーザーがテキスト入力ボックスに指定した値が含まれます。
      - **[単価]** 列には、ユーザーがこの注文明細に対して選択した製品の表示価格が表示されます。

    > [!NOTE]
    > 製品を表示するコンボボックスでアプリユーザーが選択したすべての製品について、( **Order Products**エンティティ内の) 任意の列のデータを使用する数式を作成できます。 ユーザーが**Order Products**エンティティでレコードを選択すると、そのコンボボックスに製品の名前が表示されるだけでなく、製品の単価がラベルに表示されます。 Canvas アプリ内の各参照値は、主キーだけでなく、レコード全体を参照します。

    **Refresh**関数を使用すると、 **Orders**エンティティには、**注文の詳細**エンティティに追加したレコードが確実に反映されます。 **Reset**関数を使用すると、製品、数量、および単価データがクリアされ、ユーザーは同じ順序で別の注文明細を簡単に作成できるようになります。

1. F5 キーを押して、 **[追加]** アイコンを選択します。

    順序には、指定した情報が反映されます。

    > [!div class="mx-imgBorder"]
    > 注文の詳細を追加する ![Animation ](media/northwind-orders-canvas-part3/add-details.gif)

1. optional別の項目を注文に追加します。

1. Esc キーを押してプレビューモードを終了します。

## <a name="remove-an-order-detail"></a>注文明細の削除

1. 画面の中央で、詳細ギャラリーのテンプレートを選択します。

    > [!div class="mx-imgBorder"]
    > ![Select ギャラリーテンプレート ](media/northwind-orders-canvas-part3/remove-details-01.png)

1. **[挿入]** タブで、[**ごみ箱** > **アイコン**] を選択します。

    > [!div class="mx-imgBorder"]
    > ごみ箱アイコンの ![Insert ](media/northwind-orders-canvas-part3/remove-details-02.png)

    ギャラリーのテンプレートの左上隅にごみ箱アイコンが表示されます。

    > [!div class="mx-imgBorder"]
    > アイコンの ![Default の場所 ](media/northwind-orders-canvas-part3/remove-details-03.png)

1. [ごみ箱] アイコンのサイズを変更して、詳細ギャラリーのテンプレートの右側に移動し、アイコンの**Onselect**プロパティを次の数式に設定します。

    ```powerapps-dot
    Remove( 'Order Details', ThisItem ); Refresh( Orders )
    ```

    > [!div class="mx-imgBorder"]
    > アイコンの OnSelect プロパティを ![Set ](media/northwind-orders-canvas-part3/remove-details-04.png)

    このドキュメントの作成時点では、リレーションシップから直接レコードを削除することはできません。そのため、 [**remove**](functions/function-remove-removeif.md)関数は、関連エンティティから直接レコードを削除します。 この**項目**では、削除するレコードを指定します。これは、ごみ箱アイコンが表示される詳細ギャラリーの同じレコードから取得されます。

    この場合も、操作はキャッシュされたデータを使用するので、 **Refresh**関数は、アプリが関連エンティティの1つを変更したことを**注文**エンティティに通知します。

1. F5 キーを押してプレビューモードを開き、注文から削除する各**注文の詳細**レコードの横にあるごみ箱アイコンを選択します。

1. 注文からさまざまな注文の詳細を追加および削除してみてください。

    > [!div class="mx-imgBorder"]
    > 注文の詳細を追加および削除する ![Animation ](media/northwind-orders-canvas-part3/remove-details.gif)

## <a name="in-conclusion"></a>結論

要約すると、注文の詳細を表示する別のギャラリーを追加し、アプリの注文の詳細を追加および削除するコントロールを追加しました。 これらの要素を使用したのは次のとおりです。

- 1対多のリレーションシップを通じて注文ギャラリーにリンクされた2番目のギャラリーコントロール**読み込む gallery2**  =  `Gallery1.Selected.'Order Details'`
- **Order Details**エンティティから**order Products**エンティティへの多対一のリレーションシップ: `ThisItem.Product.'Product Name'` と `ThisItem.Product.Picture`
- 製品の一覧を取得するための**選択肢**は次のとおりです: `Choices( 'Order Details'.Product' )`
- 完全な多対一の関連レコードとしてのコンボボックスの**選択され**たプロパティ: `ComboBox1.Selected.Picture` および `ComboBox1.Selected.'List Price'`
- **Order Details**レコードを作成する**Patch**関数: `Patch( 'Order Details', Defaults( 'Order Details' ), ... )`
- **Order Details**レコードを削除する**Remove**関数: `Remove( 'Order Details', ThisItem )`

この一連のトピックでは、キャンバスアプリで Common Data Service 関係とオプションセットを使用して教育を行う方法を簡単に説明しました。 アプリを運用環境にリリースする前に、フィールドの検証、エラー処理、およびその他多くの要因について検討する必要があります。
