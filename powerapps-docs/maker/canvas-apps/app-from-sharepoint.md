---
title: SharePoint リストからキャンバス アプリを作成する | Microsoft Docs
description: PowerApps で、SharePoint リストのデータを管理するキャンバス アプリを自動的に生成する
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 10/24/2018
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 101c77b7bdd84e2d2ed31febc441e54944eb9fa3
ms.sourcegitcommit: fa6ad01cf6d025d46564d755915caaa9db517c41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/25/2019
ms.locfileid: "72902445"
---
# <a name="generate-a-canvas-app-in-powerapps-from-a-sharepoint-list"></a>PowerApps で SharePoint リストからキャンバス アプリを作成する

このトピックでは、PowerApps を使用することで、SharePoint リスト内の項目に基づいてキャンバス アプリを自動的に作成します。 PowerApps または SharePoint Online 内からアプリを作成することができます。 PowerApps 内では、データ ゲートウェイを介して[オンプレミスの SharePoint サイトに接続](connections/connection-sharepoint-online.md#create-a-connection)した場合、そのサイト内のリストに基づいてアプリを作成することができます。

作成するアプリには、次の 3 つの画面が含まれます。

- 参照画面では、リスト内のすべての項目をスクロールすることができます。
- 詳細画面では、リスト内の項目の 1 つについてすべての情報を表示することができます。
- 編集画面では、項目の作成または既存の項目に関する情報の更新を行うことができます。

このトピックで示す概念および手法は、SharePoint 内の任意のリストに適用できます。 次の手順に正確に行うには:

1. SharePoint Online サイトで、**SimpleApp** という名前のリストを作成します。
2. **Title** という名前の列内で、**バニラ**、**チョコレート**、**イチゴ**のエントリを作成します。

テキスト、日付、数字、通貨など、さまざまな種類の多くの列を含むはるかに複雑なリストを作成する場合でも、アプリを作成するための原則に変わりはありません。

> [!IMPORTANT]
> PowerApps は全種類の SharePoint データをサポートするわけではありません。 詳細については、「[Known issues (既知の問題)](connections/connection-sharepoint-online.md#known-issues)」を参照してください。

## <a name="generate-an-app-from-within-powerapps"></a>PowerApps 内からアプリを作成する

1. [PowerApps にサインインします](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)。

1. **[Make your own app]\(独自アプリの作成\)** の下の **[Start from data]\(データから開始\)** にポインターを合わせ、 **[このアプリの作成]** を選択します。

    ![アプリを作成するためのオプション](./media/app-from-sharepoint/start-from-data.png)

1. SharePoint タイルで、 **[携帯電話レイアウト]** を選択します。

    ![アプリを作成するためのオプション](./media/app-from-sharepoint/sharepoint-tile.png)

1. **[直接接続]** オプションを選択し、 **[作成]** を選択します。

    ![接続の作成](./media/app-from-sharepoint/create-connection.png)

1. **[SharePoint サイトへの接続]** で、SharePoint Online サイトの URL を入力するか貼り付け、 **[移動]** を選択します。

    この例のように、リストの名前ではなくサイトの URL のみを含めます。<br>`https://microsoft.sharepoint.com/teams/Contoso`

1. **[リストを選択してください]** で、**SimpleApp** を選択し、 **[接続]** を選択します。

    数分待機すると、アプリがブラウザー画面に開き、一覧で作成した項目が表示されます。 リストに **Title** 以外の列が含まれている場合は、アプリにそのデータが表示されます。 画面上部あたりのタイトル バーに、リストの更新、リストの並べ替え、リスト内の項目の作成用のアイコンが表示されます。 オプションで、タイトル バーの下の検索ボックスを使用して、入力または貼り付けたテキストで一覧をフィルタリングできます。 

    ![ブラウズ画面](./media/app-from-sharepoint/browse-screen.png)

    このアプリを使用したり、他のユーザーと共有する前に、さらに変更を加えたいことでしょう。 続行する前に、ベスト プラクティスとして、Ctrl キーと S キーを押し、これまでの作業を保存します。 アプリの名前を指定し、 **[保存]** を選択します。

## <a name="generate-an-app-from-within-sharepoint-online"></a>SharePoint Online 内からアプリを作成する

SharePoint Online コマンド バーからカスタム リストのアプリを作成する場合、アプリはそのリストのビューとして表示されます。 Web ブラウザーだけでなく、iOS または Android デバイスでもアプリを実行できます。

1. SharePoint Online でカスタム リストを開き、コマンド バーで **[PowerApps]** 、 **[アプリの作成]** の順に選択します。

    ![アプリを作成する](./media/app-from-sharepoint/generate-new-app.png)

2. 表示されるパネルに、使用するアプリの名前を入力し、 **[作成]** を選択します。

    ![アプリの名前の指定](./media/app-from-sharepoint/app-name.png)

    新しいタブが Web ブラウザーに表示され、SharePoint リストに基づいて自動的に生成したアプリが表示されます。 PowerApps Studio にアプリが表示され、カスタマイズすることができます。

    ![既定のアプリ](./media/app-from-sharepoint/default-app.png)

3. (省略可能) ご利用の SharePoint リスト用のブラウザー タブを更新し (それを選択してから、たとえば、F5 キーを押すことにより)、次に以下の手順を行って、アプリを実行または管理します。

    - (別のブラウザー タブで) アプリを実行するには、 **[開く]** を選択します。
    - 組織内の他のユーザーがアプリを実行できるようにするには、 **[Make this view public]\(このビューを公開する\)** を選択します。

        ご利用のアプリを他のユーザーが編集できるようにするには、 **[編集可能]** アクセス許可を使用して[そのアプリを共有](share-app.md)します。

    - SharePoint からビューを削除するには、 **[Remove this view]\(このビューを削除する\)** を選択します。

        PowerApps からアプリを削除するには、[アプリを削除します](delete-app.md)。

> [!NOTE]
> 現在、SharePoint リストから作成されたアプリは、PowerApps Mobile には表示されません。

## <a name="next-steps"></a>次の手順
このトピックでは、SharePoint リスト内のデータを管理するアプリを作成しました。 次の手順として、より複雑なリストからアプリを生成し、ニーズに合わせて ([参照] 画面から) アプリをカスタマイズします。

> [!div class="nextstepaction"]
> [既定の参照画面のカスタマイズ](customize-layout-sharepoint.md)
