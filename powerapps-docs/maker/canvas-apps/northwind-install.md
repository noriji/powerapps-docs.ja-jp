---
title: Northwind Traders データベースとアプリをインストールする |Microsoft Docs
description: 環境に Northwind データベースとアプリをインストールして、リレーショナル概念を調査します。
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 06/06/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 3a2c3b468c7ccc09c49221c65113e66b562f5ed1
ms.sourcegitcommit: 7c1e70e94d75140955518349e6f9130ce3fd094e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/29/2019
ms.locfileid: "71990849"
---
# <a name="install-northwind-traders-database-and-apps"></a>Northwind Traders データベースとアプリをインストールする

[この一連のトピック](northwind-orders-canvas-part1.md)の手順に従うことで、Common Data Service のサンプルデータベースに実装されているリレーショナルデータの概念を確認できます。 また、データを管理し、そのようなアプリを作成することによって実用的なエクスペリエンスを得るために、キャンバスとモデル駆動の両方のサンプルビジネスアプリケーションを探索することもできます。 この最初のトピックでは、Northwind Traders データベースを独自の環境にインストールする方法について説明します。また、サンプルアプリにアクセスして、編集用に開いて、それらがどのように構築されたかを確認することもできます。

Northwind Traders は、注文、製品、顧客、サプライヤー、および小規模企業のその他のさまざまな側面を管理する架空の組織です。 このサンプルは、Microsoft Access の最初のバージョンで表示されており、引き続きアクセステンプレートとして利用できます。

## <a name="prerequisites"></a>前提条件

- Common Data Service をサポートする PowerApps ライセンス。 30日間[無料試用版ライセンスをご利用](../signup-for-powerapps.md)いただけます。
- Common Data Service データベースを持つ環境。 適切なアクセス許可がある場合は[、このような環境を作成](https://docs.microsoft.com/power-platform/admin/create-environment)できます。

## <a name="download-the-solution"></a>ソリューションをダウンロードする

> [!div class="nextstepaction"]
> [Northwind Traders のソリューションファイルをダウンロードする](https://pwrappssamples.blob.core.windows.net/samples/NorthwindTraders_1_0_0_6.zip)

この[ソリューション](../../developer/common-data-service/introduction-solutions.md)ファイル (.zip) には、エンティティ、オプションセット、およびビジネスプロセスの定義が含まれています。キャンバスとモデル駆動型アプリと共に使用されるその他のすべての要素。

## <a name="install-the-solution"></a>ソリューションをインストールする

1. [PowerApps](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)にサインインし、Common Data Service データベースを含む環境で作業していることを確認します。

1. 左側のナビゲーションウィンドウで、 **[ソリューション]** を選択し、画面の上部近くにあるツールバーの **[インポート]** を選択します。

    > [!div class="mx-imgBorder"]
    > ![ソリューションの表示とインポート-ソリューションのエントリポイント](media/northwind-install/solution-import.png)

1. **[ソリューションパッケージの選択]** ページで、 **[参照]** を選択します。

    > [!div class="mx-imgBorder"]
    > パッケージを選択する前に [ソリューションパッケージの選択] ページ ![](media/northwind-install/select-solution2.png)

1. ダウンロードしたファイルを見つけて、 **[開く]** を選択します。

    別の場所を選択しない限り、ファイルはダウンロードフォルダーに保存されます。

1. 正しいファイルがある場合 (バージョン番号が異なる場合があります)、 **[次へ]** を選択します。

    > [!div class="mx-imgBorder"]
    > [パッケージの選択後にソリューションパッケージを選択] ページ ![](media/northwind-install/confirm-solution2.png)

1. ソリューションの **[情報]** ページで、ソリューションと発行元の名前が正しい場合は **[次へ]** を選択します。

    > [!div class="mx-imgBorder"]
    > [ソリューション情報の ![] ページ](media/northwind-install/confirm-publisher.png)

1. **[インポートオプション]** ページで、 **[インポート]** を選択して SDK メッセージの処理を確認します。この場合、このサンプルで必要となります。

    > [!div class="mx-imgBorder"]
    > ![インポートオプション ページ](media/northwind-install/confirm-sdk.png)

    次の数分間にソリューションをインストールすると、別のページが表示され、進行状況が表示されます。

    > [!div class="mx-imgBorder"]
    > ![進行状況バー](media/northwind-install/solution-progress.png)

    インストールが完了すると、元のページに結果が表示されます。

    > [!div class="mx-imgBorder"]
    > ソリューションのインポートページを ![](media/northwind-install/solution-success.png)

1. **[閉じる]** を選びます。

## <a name="load-the-sample-data"></a>サンプルデータの読み込み

1. **[アプリ]** を選択し、 **[Northwind サンプルデータ]** を選択します。

    ソリューションをインストールした直後に Northwind アプリが表示されない場合は、数分待ちます。

    > [!div class="mx-imgBorder"]
    > アプリの一覧で Northwind データベースを ![](media/northwind-install/sample-data-app.png)

1. アプリが Common Data Service と対話するためのアクセス許可を求められたら、 **[許可]** を選択します。

    > [!div class="mx-imgBorder"]
    > Common Data Service](media/northwind-install/sample-data-permission.png) の ![の同意] ダイアログボックス

1. アプリが読み込まれ、サンプルエンティティにレコードが含まれていないことが示されたら、 **[データの読み込み]** を選択してエンティティを設定します。

    > [!div class="mx-imgBorder"]
    > サンプル Data Manager の [データの読み込み] ボタン ![](media/northwind-install/sample-data-load.png)

    アプリによってデータが読み込まれると、アプリの上部に3月のドットが表示され、レコード数が増加します。

    エンティティは、レコード間のリレーションシップを確立できるように、特定の順序で読み込まれます。 たとえば、 **Order Details**エンティティには、最初に読み込まれる**Orders**および**Order Products**エンティティとの多対一のリレーションシップがあります。

    [キャンセル] を選択すると、いつでもプロセスをキャンセルできます。 [**データの削除** **]** を選択すると、いつでもデータを削除できます。

    > [!div class="mx-imgBorder"]
    > データが読み込まれるときのサンプル Data Manager の ![](media/northwind-install/sample-data-progress.png)

    データの読み込みが完了すると、最後の行 (**多対多リレーションシップ**) が**完了**し、 **[データの読み込み]** ボタンと **[データの削除]** ボタンが再び有効になります。

    > [!div class="mx-imgBorder"]
    > データが読み込まれた後のサンプル Data Manager ![](media/northwind-install/sample-data-complete.png)

## <a name="sample-apps"></a>サンプル アプリ

Northwind ソリューションには、このデータと対話するための次のアプリが含まれています。

- Northwind の注文 (キャンバス)
- Northwind の注文 (モデル駆動型)

これらのアプリは、前の手順でアプリを開いたときと同じ方法で開くことができます。

### <a name="canvas"></a>キャンバス

このシングルスクリーンアプリには、 **Orders**エンティティの単純なマスター詳細ビューが用意されています。このビューでは、注文の注文と各品目の概要を表示および編集できます。 注文の一覧が左端近くに表示され、その一覧の矢印を選択して、その注文の概要と詳細を表示できます。 詳細につい[ては、Northwind Traders 用キャンバスアプリの概要に関するトピック](northwind-orders-canvas-overview.md)を参照してください。

> [!div class="mx-imgBorder"]
> Northwind キャンバスアプリ](media/northwind-install/orders-canvas.png) での注文と詳細の ![一覧

### <a name="model-driven"></a>モデル駆動

このアプリは、キャンバスアプリと同じデータ ( **Orders**エンティティ内) で動作します。 注文の一覧で、その番号を選択して、注文に関する詳細情報を表示します。

> [!div class="mx-imgBorder"]
> Northwind モデル駆動型アプリでの注文の ![一覧](media/northwind-install/orders-model.png)

注文の概要が別の形式で表示されます。

> [!div class="mx-imgBorder"]
> モデル駆動型アプリ](media/northwind-install/orders-model-2.png) での ![の順序の詳細

フォームを下にスクロールすると、キャンバスアプリと同じ行項目が表示されます。

> [!div class="mx-imgBorder"]
> モデル駆動型アプリ](media/northwind-install/orders-model-3.png) で注文の詳細を ![する

## <a name="do-it-yourself"></a>自分で実行する

このトピックで既に説明したキャンバスアプリを作成する手順については、手順に従って説明します。  この手順は、次の3つの部分に分かれています。

1. [注文ギャラリーを作成](northwind-orders-canvas-part1.md)します。
1. [概要フォームを作成](northwind-orders-canvas-part2.md)します。
1. [詳細ギャラリーを作成](northwind-orders-canvas-part3.md)します。

先に進む必要がある場合は、各パーツの開始点アプリがソリューションに含まれています。  アプリの一覧で、 **Northwind Orders (Canvas)** を探します。最初にパート1を開始します。

この[アプリの概要](northwind-orders-canvas-overview.md)では、ユーザーインターフェイス、データソース、およびリレーションシップの使用方法について説明します。

> [!div class="nextstepaction"]
> [まず概要を読む](northwind-orders-canvas-overview.md)
