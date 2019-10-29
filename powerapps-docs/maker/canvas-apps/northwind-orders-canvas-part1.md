---
title: キャンバスアプリで注文ギャラリーを作成する |Microsoft Docs
description: Northwind Traders のデータを管理するために、canvas アプリで注文ギャラリーを作成する
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
ms.openlocfilehash: ac6586067105d5f6cd1ce2aab5568450804fe4c6
ms.sourcegitcommit: 7c1e70e94d75140955518349e6f9130ce3fd094e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/29/2019
ms.locfileid: "71991370"
---
# <a name="create-an-order-gallery-in-a-canvas-app"></a>キャンバスアプリでの注文書ギャラリーの作成

Northwind Traders データベースで架空のデータを管理するために、キャンバスアプリで注文ギャラリーを作成する手順について説明します。 このトピックは、Common Data Service でリレーショナルデータに対するビジネスアプリケーションを構築する方法について説明するシリーズの一部です。 最適な結果を得るには、次のトピックを参照してください。

1. 注文ギャラリーを作成します (**このトピック**)。
1. [概要フォームを作成](northwind-orders-canvas-part2.md)します。
1. [詳細ギャラリーを作成](northwind-orders-canvas-part3.md)します。

> [!div class="mx-imgBorder"]
> 画面領域の ![定義](media/northwind-orders-canvas-part1/orders-parts.png)

## <a name="prerequisites"></a>前提条件

- [Northwind Traders データベースとアプリをインストール](northwind-install.md)します。
- Northwind Traders 用[キャンバスアプリの概要](northwind-orders-canvas-overview.md)に関するトピックをご覧ください。

## <a name="create-a-blank-app"></a>空のアプリを作成する

1. [PowerApps にサインイン](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)し、空のタブレットアプリを作成します。

    > [!div class="mx-imgBorder"]
    > 空のタイルからキャンバスアプリを ![](media/northwind-orders-canvas-part1/start-01.png)

1. アプリの名前を自由に指定し、 **[作成]** を選択します。

    > [!div class="mx-imgBorder"]
    > 空のダイアログボックスからキャンバスアプリを ![](media/northwind-orders-canvas-part1/start-02.png)

    データソースとコントロールをアプリに追加できるように、PowerApps Studio が開きます。

    > [!div class="mx-imgBorder"]
    > ![PowerApps Studio](media/northwind-orders-canvas-part1/start-03.png)

1. 数式バーから数式の結果を直接表示するための試験的な[機能](working-with-experimental.md)を有効にします。

    1. **[ファイル]** メニューの **[アプリの設定]** を選択し、 **[詳細設定]** を選択します。
    1. 機能の一覧の一番下までスクロールし、[**数式バーの結果ビューを有効**にする] をオンにします。

        > [!div class="mx-imgBorder"]
        > 試験的な機能の一覧を ![](media/northwind-orders-canvas-part1/start-04.png)

1. 左上隅の [戻る] 矢印をクリックして、空白のキャンバスに戻ります。

## <a name="add-the-data"></a>データを追加する

1. **[表示]** タブで **[データソース]** を選択し、**データ**ペインで **[データソースの追加]** を選択します。

    > [!div class="mx-imgBorder"]
    > ![ビュー、データソース、データソースの追加](media/northwind-orders-canvas-part1/datasource-01.png) を選択します。

1. **[Common Data Service]** を選択します。

    接続の一覧に**Common Data Service**が表示されない場合は、 **[新しい接続]** を選択して追加します。

    > [!div class="mx-imgBorder"]
    > ![接続の一覧](media/northwind-orders-canvas-part1/datasource-02.png)

1. **[エンティティの選択]** で **「orders**」と入力し、 **[注文]** チェックボックスをオンにして、 **[接続]** を選択します。

    > [!div class="mx-imgBorder"]
    > エンティティの一覧を ![](media/northwind-orders-canvas-part1/datasource-03.png)

    **注文**データソースをアプリに追加しました。

    > [!div class="mx-imgBorder"]
    > ![データペイン](media/northwind-orders-canvas-part1/datasource-04.png)

    **Orders**エンティティには、さまざまな種類のフィールドが多数含まれています。

    > [!div class="mx-imgBorder"]
    > Orders エンティティのフィールドの一覧を ![](media/northwind-orders-canvas-part1/datasource-05.png)

    各フィールドには、**表示名**と**名前**があります。これは、論理名と呼ばれることもあります。 どちらの名前も同じことを意味します。 通常は、アプリをビルドするときに表示名を使用しますが、手順に記載されているように、より暗号化された**名前**が必要になる場合もあります。

1. PowerApps Studio で、右上隅にある閉じるアイコン (x) を選択して**データ**ペインを閉じます。

## <a name="create-the-order-gallery"></a>注文ギャラリーを作成する

1. **[挿入]** タブで [**ギャラリー**  >  **[縦]** を選択して[**ギャラリー**](controls/control-gallery.md)コントロールを追加し、注文を表示します。

    > [!div class="mx-imgBorder"]
    > ![挿入、ギャラリー、垂直方向の空白](media/northwind-orders-canvas-part1/orders-01.png)

1. 数式バーで、ギャラリーの**Items**プロパティを次の数式に設定します。

    ```powerapps-dot
    Sort( Orders, 'Order Number', Descending )
    ```

    Sort 関数は、リストを順に[**並べ替え**](functions/function-sort.md)て、最も新しい順序 (最も高い順序の番号) が最初に表示されるようにします。

    > [!div class="mx-imgBorder"]
    > ギャラリーのアイテムの ![プロパティの設定](media/northwind-orders-canvas-part1/orders-02.png)

1. 右端の **[プロパティ]** タブで、 **[レイアウト]** リストを開きます。

    > [!div class="mx-imgBorder"]
    > レイアウトオプションの一覧を ![](media/northwind-orders-canvas-part1/orders-03.png)

1. オプションの一覧で、 **[タイトルとサブタイトル]** を選択します。

    > [!div class="mx-imgBorder"]
    > レイアウトを選択 ![には](media/northwind-orders-canvas-part1/orders-04.png)

    ギャラリーのテンプレートに2つの[**ラベル**](controls/control-text-box.md)コントロールが追加されます。 既定では、これらのコントロールは**Orders**エンティティの2つの列を表示します。これは、次に変更します。 ギャラリーのテンプレートは、エンティティ内のレコードごとに垂直方向にレプリケートされます。

1. **データ**ペインを閉じた場合は、右端の **[プロパティ]** タブで、 **[編集]** ( **[フィールド]** の横) を選択します。

1. **データ**ペインで **[Title1]** を選択します (または、ギャラリーのテンプレートで上部のラベルを選択します)。

1. 数式バーで、ラベルの**Text**プロパティを次の式に設定します。

    ```powerapps-dot
    "Order " & ThisItem.'Order Number'
    ```

    > [!div class="mx-imgBorder"]
    > タイトルラベルの Text プロパティ](media/northwind-orders-canvas-part1/orders-06.png) を設定 ![

    注文番号は、各ギャラリーアイテムの上部に表示されます。 ギャラリーテンプレートでは、この**アイテム**によって**Order**エンティティ内のすべてのフィールドへのアクセスが許可されます。

1. **データ**ペインで、 **[Subtitle1]** を選択します (または、ギャラリーのテンプレートで下のラベルを選択します)。

    > [!div class="mx-imgBorder"]
    > ![サブタイトルラベル](media/northwind-orders-canvas-part1/orders-07.png) を選択します

1. 数式バーで、ラベルの**Text**プロパティを次の式に設定します。

    ```powerapps-dot
    ThisItem.Customer.Company
    ```

    > [!div class="mx-imgBorder"]
    > サブタイトルラベルの Text プロパティを設定 ![](media/northwind-orders-canvas-part1/orders-08.png)

    この数式を入力すると、しばらくの間、赤い波線が表示されることがあります。 数式バーの外側を選択し、そのカーソルを数式バーに戻すと、エラーが表示されます。 エラーが引き続き発生する場合、または値が表示されない場合は、**表示** タブを選択し、**データソース** を選択します。次に、データソース名の右側にある省略記号 (...) を選択して、 **Orders**エンティティを更新します。

    この項目を指定すると、 **Orders**エンティティと**Customers**エンティティの間に多対一のリレーションシップを利用し、各注文に関連付けられている顧客レコードを取得することになります **。** 顧客レコードから、 **Company**列のデータを抽出して表示します。

    **Orders**エンティティから、 **Customer**エンティティなどの他のエンティティへのすべてのリレーションシップを表示できます。

    > [!div class="mx-imgBorder"]
    > リレーションシップの一覧を ![](media/northwind-orders-canvas-part1/orders-09.png)

1. 右上隅にある [閉じる] アイコン (x) を選択して、**データ**ペインを閉じます。

## <a name="show-each-orders-status"></a>各注文の状態を表示する

この手順では、ギャラリーにラベルの領域を追加し、データに基づいて各注文の状態を異なる色で表示するように構成します。

1. ギャラリーのテンプレートで、最初のラベルの幅を**Title1**に下げます。

    > [!div class="mx-imgBorder"]
    > ギャラリーのテンプレートで Title1 を ![](media/northwind-orders-canvas-part1/status-01.png)

1. 2番目のラベル**Subtitle1**を使用して、前の手順を繰り返します。

    > [!div class="mx-imgBorder"]
    > ギャラリーのテンプレートで Subtitle1 を ![](media/northwind-orders-canvas-part1/status-02.png)

1. ギャラリーテンプレート (またはテンプレート内のコントロール) を選択した状態で、 **[挿入]** タブの **[ラベル]** を選択します。

    > [!div class="mx-imgBorder"]
    > ラベル](media/northwind-orders-canvas-part1/status-03.png) を追加 ![には

1. 新しいラベルを**Title1**ラベルの右側に移動します。

    > [!div class="mx-imgBorder"]
    > ラベルの移動とサイズ変更を ![](media/northwind-orders-canvas-part1/status-04.png)

1. 新しいラベルの**Text**プロパティを次の式に設定します。

    ```powerapps-dot
    ThisItem.'Order Status'
    ```

    > [!div class="mx-imgBorder"]
    > Text プロパティを設定 ![](media/northwind-orders-canvas-part1/status-05.png)

    **Orders**エンティティでは、 **Order Status**フィールドは**orders status**オプションセットの値を保持します。 オプションセットは、他のプログラミングツールの列挙に似ています。 各オプションセットはデータベースで定義されているため、ユーザーはセット内のオプションのみを指定できます。 **Orders Status**オプションの設定は、ローカルではなくグローバルでもあるため、他のエンティティで使用できます。

    > [!div class="mx-imgBorder"]
    > ![Orders ステータスオプションセット](media/northwind-orders-canvas-part1/status-06.png)

    セット内の各オプションには、ラベルに表示すると表示される名前が付いています。 これらの名前はローカライズできます。アプリは、英語のユーザーが**Apple**を選択した場合、フランス語のユーザーが**Pomme**を選択した場合、またはスペイン語のユーザーが**Manzana**を選択した場合と同じオプションを認識します。 このため、このトピックでは後ほど説明するように、ハードコーディングされた文字列に依存する数式をオプションに対して作成することはできません。

    数式では、スペースが含まれているため、**注文状態**を単一引用符で囲む必要があります。 ただし、この名前は、PowerApps の他の名前 ( **Customer**や**Company**など) と同じように機能します。

1. **[ホーム]** タブで、状態ラベルのフォントサイズを20ポイントに増やし、テキストを右揃えにします。

    > [!div class="mx-imgBorder"]
    > フォントサイズと配置を変更 ![](media/northwind-orders-canvas-part1/status-07.png)

1. 数式バーで、状態ラベルの**Color**プロパティを次の数式に設定します。

    ```powerapps-dot
    Switch( ThisItem.'Order Status',
        'Orders Status'.Closed, Green,
        'Orders Status'.New, Black,
        'Orders Status'.Invoiced, Blue,
        'Orders Status'.Shipped, Purple
    )
    ```

    > [!div class="mx-imgBorder"]
    > 状態ラベルの Color プロパティを設定 ![](media/northwind-orders-canvas-part1/status-08.png)

    PowerApps では、セット内の各オプションにハードコーディングされた文字列に依存する数式を作成できません。これは、オプション名がローカライズされている場合に、このような式が不適切な結果を生成する可能性があるためです。 代わりに、**スイッチ**関数は、ユーザーの設定に基づいてラベルに表示される文字列に基づいて色を決定します。

    この数式を使用すると、前の図に示したように、異なるステータス値が異なる色で表示されます。

## <a name="display-each-orders-total"></a>各注文の合計を表示する

1. ギャラリーのテンプレートであるギャラリーの最初の項目を選択します。

    > [!div class="mx-imgBorder"]
    > ギャラリーテンプレートを選択 ![](media/northwind-orders-canvas-part1/aggregate-01.png)

1. **[挿入]** タブで、 **[ラベル]** を選択して別のラベルを追加します。

    > [!div class="mx-imgBorder"]
    > ラベル](media/northwind-orders-canvas-part1/aggregate-02.png) を追加 ![には

1. [状態] ラベルの下に表示されるように、新しいラベルを移動します。

    > [!div class="mx-imgBorder"]
    > 新しいラベルのサイズ変更と移動を ![](media/northwind-orders-canvas-part1/aggregate-03.png)

1. 数式バーで、新しいラベルの**Text**プロパティを次の数式に設定します。

    ```powerapps-dot
    Text( Sum( ThisItem.'Order Details', Quantity * 'Unit Price' ), "[$-en-US]$ #,###.00" )
    ```

    > [!div class="mx-imgBorder"]
    > 注文の合計コストを計算するための ![式](media/northwind-orders-canvas-part1/aggregate-04.png)

    この数式では、 [**Sum**](functions/function-aggregates.md)関数は、一対多のリレーションシップを通じて**order**エンティティ内の各レコードに関連付けられている**order Details**エンティティ内のレコードを追加します。 これらの行項目はそれぞれの順序を構成し、同じ一対多の関係を使用して、画面の右下の領域にある行項目の表示と編集を行います。

    この数式では、複雑な集計関数 (乗算の合計など) の委任がサポートされていないため、青い下線と[委任の警告](delegation-overview.md)が表示されます。これは Common Data Service ではありません。 この例では、500行の項目を超える順序が含まれていないため、この情報は無視してかまいません。 別のアプリで必要な場合は、**アプリの設定**で制限を増やすことができます。

    この数式の[**Text**](functions/function-text.md)関数は、通貨記号を追加し、結果を桁区切り記号と小数点の区切り記号で書式設定します。 この数式には、米国英語 ( **[$-en-us]** ) とドル記号 ( **$** ) の言語タグが記述されています。 言語タグを削除すると、言語設定に基づいて、そのタグが1つに置き換えられ、そのタグの適切な形式がラベルに表示されます。 ドル記号を残すと、ユーザーの設定に基づいて適切な通貨記号がラベルに表示されます。 ただし、ドル記号を好きな記号に置き換えることによって、別の記号を強制的に表示することができます。

1. **[ホーム]** タブで、最新のラベルのフォントサイズを20ポイントに変更し、テキストを右揃えにします。

    > [!div class="mx-imgBorder"]
    > ラベルのフォントサイズと配置を変更 ![](media/northwind-orders-canvas-part1/aggregate-05.png)

1. ギャラリーを画面の左端に移動し、ギャラリーの幅を小さくしてスペースを閉じます。

1. ギャラリーの高さは画面とほぼ同じになるように大きくしますが、タイトルバーの上部には小さなスペースを残しておきます。タイトルバーは、次のトピックの先頭に追加します。

    > [!div class="mx-imgBorder"]
    > ギャラリーの移動とサイズ変更を ![](media/northwind-orders-canvas-part1/aggregate-06.png)

## <a name="summary"></a>まとめ

要約すると、次の要素を含む注文ギャラリーを追加することで、シングルスクリーンキャンバスアプリの作成を開始しました。

- 注文番号を表示する式: `"Orders " & ThisItem.OrderNumber`
- 多対一リレーションシップのフィールド: `ThisItem.Customer.Company`
- Set 内のオプションの名前を示すラベル: `ThisItem.'Order Status'`
- ラベルに表示される set のオプションに基づいて書式を変更するラベル: `Switch( ThisItem.'Order Status', 'Orders Status'.Closed, Green, ...`
- 一対多のリレーションシップに対する複雑な集計関数: `Sum( ThisItem.'Order Details', Quantity * 'Unit Price' )`

## <a name="next-topic"></a>次のトピック

次のトピックでは、作成したギャラリーでユーザーが選択した任意の順序の概要を表示および編集するための[**編集フォーム**](controls/control-form-detail.md)コントロールを追加します。

> [!div class="nextstepaction"]
> [概要フォームを作成する](northwind-orders-canvas-part2.md)