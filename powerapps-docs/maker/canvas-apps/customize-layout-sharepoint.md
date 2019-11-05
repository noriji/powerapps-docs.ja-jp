---
title: チュートリアル - 生成されたアプリのギャラリーをカスタマイズする | Microsoft Docs
description: このチュートリアルでは、PowerApps で自動的に生成されたアプリのギャラリーと他の要素に表示されるデータをカスタマイズします。
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: tutorial
ms.custom: canvas
ms.reviewer: ''
ms.date: 05/06/2018
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 6b3a33f327aab7e4f02c954dbd31c412e35dd661
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2019
ms.locfileid: "73539176"
---
# <a name="tutorial-customize-a-gallery-in-powerapps"></a>チュートリアル: PowerApps でのギャラリーのカスタマイズ

このチュートリアルでは、Microsoft PowerApps で自動的に生成されたアプリで、ギャラリーと呼ばれるレコードの一覧をカスタマイズし、他の変更を行います。 これらの変更を行わなくてもユーザーはアプリ内のデータを管理できますが、組織のニーズに合わせてカスタマイズすれば、アプリが使いやすくなります。

たとえば、このチュートリアルのギャラリーは、既定で次の図と一致します。 メール アドレスは他の種類のデータより目立つように表示され、ユーザーはそのアドレスのテキストに基づいてギャラリーの並べ替えやフィルター処理を行うことができます。

![既定のギャラリー](./media/customize-layout-sharepoint/gallery-before.png)

ただし、ユーザーはメール アドレスよりたとえばアカウント名の方に関心がある場合もあるので、組織にとって重要なデータを基にして強調表示、並べ替え、フィルターが行われるようにギャラリーを構成します。 さらに、アプリ内の他の画面と区別するため、既定の画面のタイトルを変更します。

![最終ギャラリー](./media/customize-layout-sharepoint/gallery-after.png)

また、タッチ画面やマウス ホイールを使用できないユーザーでもギャラリー全体を見ることができるように、スクロール バーを追加します。

> [!div class="checklist"]
> * ギャラリーのレイアウトを変更する
> * ギャラリーに表示されるデータの種類を変更する
> * ユーザーがデータの並べ替えと検索に使用できる列を変更する
> * 画面のタイトルを変更する
> * スクロールバーを表示する

このチュートリアルでは、特定のデータ ソースから既に生成されているアプリを使います。 ただし、SharePoint リスト、Excel テーブル、または他のデータ ソースのいずれが基になっていても、PowerApps で生成するすべてのアプリに、同じ概念が適用されます。

PowerApps にサインアップしていない場合は、始める前に[無料でサインアップ](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)してください。

## <a name="prerequisites"></a>前提条件

Common Data Service の**Accounts**エンティティから[アプリを生成](data-platform-create-app.md)します。

## <a name="open-the-generated-app"></a>生成されたアプリを開く

1. [PowerApps](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) にサインインし、左端近くにある **[アプリ]** を選びます。

1. 生成したアプリを探し、その省略記号アイコン **[...]** を選んで、 **[編集]** を選びます。

    ![編集用にアプリを開く](./media/customize-layout-sharepoint/open-app.png)

1. **[PowerApps Studio へようこそ]** ダイアログ ボックスが表示されたら、 **[スキップ]** を選択します。

## <a name="change-the-layout"></a>レイアウトを変更する

1. 左のナビゲーション ウィンドウで、**BrowseGallery1** を選びます。

    ギャラリーを選ぶと、ハンドルの付いた選択ボックスがその周囲に表示されます。

    ![ギャラリーを選択](media/customize-layout-sharepoint/select-gallery-1.png)

1. 右側のウィンドウの **[プロパティ]** タブで、 **[レイアウト]** の下にあるオプションの一覧を開き、タイトルのみを表示するオプションを選択します。

    ![タイトルのみのレイアウトを選択する](./media/customize-layout-sharepoint/choose-layout.png)

1. **フィールド** の横にある **編集** を選択し、タイトル ボックスの下矢印を選択します。

    このコントロールの名前は **Title1** のように末尾が数字になっていますが、数字は行った他のアクションによっては異なる場合があります。

1. オプションの一覧で **[Account name]** を選択し、**データ**ペインを閉じます。

    ギャラリーに各アカウントの名前が表示されます。

    ![最終ギャラリー](./media/customize-layout-sharepoint/final-gallery.png)

## <a name="change-sort-and-search-columns"></a>並べ替え列と検索列を変更する

1. 前のセクションの説明に従ってギャラリーを選びます。

    ![ギャラリーを選択](./media/customize-layout-sharepoint/select-gallery-title.png)

1. 左上隅のプロパティ一覧に **Items** が表示されていることを確認します。

    ![Items プロパティ](./media/customize-layout-sharepoint/items-property.png)

    このプロパティの値が数式バーに表示されます。 このプロパティを設定して、ギャラリーのデータ ソースだけでなく、ユーザーがデータの並べ替えや検索を行うことができる列も指定します。

1. この数式をコピーし、数式バーに貼り付けます。

    ```SortByColumns(Search(Accounts, TextSearchBox1.Text, "name"), "name", If(SortDescending1, Descending, Ascending))```

    この数式を使うと、次のようになります。

    * ユーザーが検索バーに 1 つ以上の文字を入力すると、入力したテキストが含まれるアカウント名のみがギャラリーに表示されます。
    * ユーザーが並べ替えアイコンを選ぶと、選んだ回数に応じて、アカウント名のアルファベットの昇順または降順に、ギャラリーが並べ替えられます。

     これらの関数とその他の関数の詳細については、[数式の参照に関するページ](formula-reference.md)をご覧ください、

### <a name="test-sorting-and-searching"></a>並べ替えと検索のテスト

1. F5 キーを押して (または、右上隅の再生ボタンを選んで)、プレビュー モードを開きます。

    ![プレビュー モードを開始](./media/customize-layout-sharepoint/open-preview.png)

1. 参照セクションの右上隅にある並べ替えボタンを少なくとも 1 回選んで、アルファベットに基づく表示順を昇順または降順に変更します。

    ![並べ替えボタンのテスト](./media/customize-layout-sharepoint/sort-button.png)

1. 検索ボックスに「**k**」と入力し、その文字を含むアカウント名だけを表示します。

    ![検索バーのテスト](./media/customize-layout-sharepoint/test-filter.png)

1. 検索バーからテキストをすべて削除し、Esc キーを押して (または、右上隅の閉じるアイコンを選んで)、プレビュー モードを終了します。

## <a name="change-the-screen-title"></a>画面のタイトルを変更する

1. 画面のタイトルをクリックするかタップして、タイトルを選びます。

    ![画面タイトルを選択](./media/customize-layout-sharepoint/select-title.png)

1. プロパティの一覧に **Text** が表示されていることを確認し、数式バーの **Accounts** を **Browse** に置き換えます (二重引用符はそのままにします)。

    ![画面タイトルの更新](./media/customize-layout-sharepoint/change-screen-title.png)

    画面に変更内容が反映されます。

    ![新しい画面タイトル](./media/customize-layout-sharepoint/new-screen-title.png)

## <a name="show-a-scrollbar"></a>スクロールバーを表示する

ユーザーがタッチ画面もマウス ホイールも使用していない場合は、ユーザーがコントロール上にマウス ポインターを置いたときにスクロール バーが表示されるようにギャラリーを構成します。 このように、ユーザーは画面にすべてのアカウントを同時に表示できない場合でも、すべてのアカウントを表示できます。

1. 最初の手順の説明に従ってギャラリーを選択します。

    ![ギャラリーを選択](./media/customize-layout-sharepoint/select-gallery-sorted.png)

1. ギャラリーの [ **scrollbar の表示]** プロパティを**true**に設定します。

## <a name="next-steps"></a>次の手順

このチュートリアルでは、ギャラリーをカスタマイズし、生成されたアプリ内のレコードを参照するために既定の画面に他の変更を行いました。 詳細を表示し、アカウントを作成または更新するための既定の画面をカスタマイズすることもできます。 参照画面にギャラリーが含まれるように、アプリの他の 2 つの画面にはフォームが含まれます。 たとえば、フォームに表示されるデータの種類とその順序を変更できます。

> [!div class="nextstepaction"]
> [フォームをカスタマイズ](customize-forms-sharepoint.md)
