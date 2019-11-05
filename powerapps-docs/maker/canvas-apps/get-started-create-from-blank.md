---
title: Excel データを基にして最初からキャンバス アプリを作成する | Microsoft Docs
description: このチュートリアルでは、2 画面のキャンバス アプリを作成して、ユーザーが Excel ファイル内のレコードを作成、編集、および削除できるようにします。
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 03/26/2019
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 81426f24eea958b40f6d03da787a729603ec6f7f
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2019
ms.locfileid: "73537024"
---
# <a name="create-a-canvas-app-from-scratch-based-on-excel-data"></a>Excel データを基にして最初からキャンバス アプリを作成する

Excel データを基にしてテーブルとして書式設定された独自のキャンバス アプリを最初から作成した後、必要に応じて、他のソースからデータを追加します。 このチュートリアルの手順では、2 つの画面を持ったアプリを作成します。 1 つは、一連のレコードをユーザーが閲覧するための画面です。 もう 1 つは、ユーザーがレコードを作成したり、レコードのフィールドを更新したり、レコード全体を削除したりするための画面です。 この方法は、[アプリを自動的に生成する](get-started-create-from-data.md)よりも時間がかかりますが、経験豊富なアプリ作成者は自分のニーズに合わせて最適なアプリを構築できます。

## <a name="prerequisites"></a>前提条件

このチュートリアルの手順に厳密に従うには、最初に次のサンプル データを使って Excel ファイルを作成します。

1. このデータをコピーし、Excel ファイルに貼り付けます。

    | StartDay | StartTime | Volunteer | Backup |
    | --- | --- | --- | --- |
    | Saturday |10am-noon |Vasquez |Kumashiro |
    | Saturday |noon-2pm |Ice |Singhal |
    | Saturday |2pm-4pm |Myk |Mueller |
    | Sunday |10am-noon |Li |Adams |
    | Sunday | noon-2pm |Singh |Morgan |
    | Sunday | 2pm-4pm |Batye |Nguyen |

2. そのデータを **Schedule** という名前のテーブルとして書式設定し、PowerApps が情報を解析できるようにします。

    詳細については、「[Excel でテーブルを書式設定する](how-to-excel-tips.md)」をご覧ください。

3. ファイルを「 **eventsignup .xlsx**」という名前で保存し、閉じてから、OneDrive などの[クラウドストレージアカウント](connections/cloud-storage-blob-connections.md)にアップロードします。

> [!IMPORTANT]
> 独自の Excel ファイルを使って、このチュートリアルの一般的な概念だけを確認できます。 ただし、Excel ファイル内のデータは、テーブルとして書式設定されている必要があります。 詳細については、「[Excel でテーブルを書式設定する](how-to-excel-tips.md)」をご覧ください。

## <a name="open-a-blank-app"></a>空のアプリを開く

1. [PowerApps にサインインします](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)。

1. **[自分のアプリを作成する]** で **[キャンバス アプリを一から作成]** を選択します。

    > [!div class="mx-imgBorder"]
    >![空白のキャンバス アプリを作成する](./media/get-started-create-from-blank/blank-app.png)

1. アプリに名前を指定し、 **[電話]** を選択し、 **[作成]** を選択します。

    携帯電話や他のデバイス (タブレットなど) 用のアプリを最初から設計できます。 このトピックでは、携帯電話用のアプリの設計について説明します。

    > [!div class="mx-imgBorder"]
    >![アプリの名前と形式を指定する](./media/get-started-create-from-blank/excel-demo.png)

    PowerApps Studio で、携帯電話用の空のアプリが作成されます。

1. **[PowerApps Studio へようこそ]** ダイアログ ボックスが開いたら、 **[スキップ]** を選びます。

## <a name="connect-to-data"></a>データに接続する

1. 画面の中央で **[データに接続]** を選択します。

1. **[データ]** ウィンドウで、クラウド ストレージ アカウントへの接続が表示される場合は、それを選びます。 それ以外の場合は、次の手順で接続を追加します。

    1. **[新しい接続]** を選び、お使いのクラウド ストレージ アカウントのタイルを選んで、 **[作成]** を選びます。
    2. メッセージが表示されたら、そのアカウントの資格情報を指定します。

1. **[Excel ファイルの選択]** で、**eventsignup** の最初の何文字かを入力するか貼り付けて、一覧をフィルター処理し、アップロードしたファイルを選びます。

1. **[テーブルの選択]** で、**Schedule** のチェック ボックスをオンにして、 **[接続]** を選びます。

1. **[データ]** ウィンドウの右上隅の閉じるアイコン (X) を選択してそれを閉じます。

## <a name="create-the-view-screen"></a>表示画面を作成する

1. **[ホーム]** タブで、 **[新しい画面]** の横にある下向き矢印を選んで画面の種類の一覧を開き、 **[リスト]** を選びます。

    画面が追加され、いくつかの既定のコントロールが表示されます (検索ボックスや **[ギャラリー](controls/control-gallery.md)** コントロールなど)。 ギャラリーは、検索ボックスの下の画面全体に広がる領域になります。

1. 新しい画面上部の **[ラベル](controls/control-text-box.md)** コントロールを選び、 **[Title]** を「**View records**」に置き換えます。

     ![タイトル バーの変更](./media/get-started-create-from-blank/change-title-bar.png)

1. 左のナビゲーション バーで、**BrowseGallery1** を選びます。

    ギャラリーの周囲にハンドルの付いた選択ボックスが表示されます。

    ![リスト画面を追加する](./media/get-started-create-from-blank/select-gallery.png)

1. 右側のウィンドウの **[プロパティ]** タブで **[レイアウト]** メニューの下向き矢印を選択します。

    ![[レイアウト] メニューを開く](./media/get-started-create-from-blank/select-layout.png)

1. **[Title, subtitle, and body]** \(タイトル、サブタイトル、本文\) を選択します。

1. 数式バーの **[CustomGallerySample]** を「**Schedule**」に置き換え、**SampleText** の両インスタンスを **Volunteer** に置き換えます。

1. 数式バーの右端で下向き矢印を選択し、 **[テキストの書式設定]** を選択します。

    数式が、この例と一致します。

    ```powerapps-dot
    SortByColumns(
        Search(
            Schedule,
            TextSearchBox1.Text,
            "Volunteer"
        ),
        "Volunteer",
        If(
            SortDescending1,
            SortOrder.Descending,
            SortOrder.Ascending
        )
    )
    ```

1. 右側のウィンドウの **[プロパティ]** タブで **[フィールド]** ラベルの横の **[編集]** を選択します。

1. **[Title2]** ボックスで、 **[ボランティア]** を選択し、 **[Subtitle2]** ボックスで **[Startday]** を選択し、 **[Body1]** ボックスで **[StartTime]** を選択します。

1. **[データ]** ウィンドウの右上隅の閉じるアイコン (X) を選択してそれを閉じます。

ユーザーは、この式の **SortByColumns** 関数と **Search** 関数に基づいて、ボランティア名でギャラリーを並べ替えたりフィルター処理したりできます。

- ユーザーが検索ボックスに文字を入力すると、**Volunteer** フィールドにその文字が含まれるレコードだけがギャラリーに表示されます。
- ユーザーが (タイトル バーの更新ボタンとプラス ボタンの間の) 並べ替えボタンを選ぶと、ギャラリーのレコードは **Volunteer** フィールドの値に基づいて (ユーザーがボタンを選んだ回数に応じて) 昇順または降順に並べ替えられます。

これらの関数とその他の関数の詳細については、[数式の参照に関するページ](formula-reference.md)をご覧ください、

## <a name="create-the-change-screen"></a>変更画面を作成する

1. **[ホーム]** タブで **[新しい画面]** の横の下向き矢印を選択し、 **[フォーム]** を選択します。

1. 左のナビゲーション バーの **EditForm1** を選択します。

1. 右側のウィンドウの **[プロパティ]** タブで **[データ ソース]** の横の下向き矢印を選択し、表示されたリストで **[スケジュール(Schedule)]** を選択します。

1. 今指定したデータ ソースの下の **[フィールドの編集]** を選択します。

1. **[フィールド]** ウィンドウで **[フィールドの追加]** を選択し、各フィールドのチェック ボックスをオンにし、 **[追加]** を選択します。

1. 各フィールドの名前の横の矢印を選択して展開し、**Volunteer** フィールドを上にドラッグし、フィールドのリストの上部にそれが表示されるようにします。

     ![フィールドの順序を変更する](./media/get-started-create-from-blank/reorder-fields.png)

1. **[フィールド]** ウィンドウの右上隅の閉じるアイコン (X) を選択してそれを閉じます。

1. フォームを選び、次の式を数式バーに入力するか貼り付けて、その **Item** プロパティに設定します。

    `BrowseGallery1.Selected`

1. 画面上部の **[ラベル](controls/control-text-box.md)** コントロールを選び、 **[Title]** を「**Change records**」に置き換えます。

    ![タイトル バーの変更](./media/get-started-create-from-blank/change-title-bar2.png)

## <a name="delete-and-rename-screens"></a>画面の削除と名前の変更

1. 左のナビゲーション バーで、**Screen1** の省略記号 [...] を選び、 **[削除]** を選びます。

    ![画面の削除](./media/get-started-create-from-blank/delete-screen.png)

1. **Screen2** の省略記号 [...] を選んで **[名前の変更]** を選び、「**ViewScreen**」と入力するか貼り付けます。

1. **Screen3** の省略記号 [...] を選んで **[名前の変更]** を選び、「**ChangeScreen**」と入力するか貼り付けます。

## <a name="configure-icons-on-the-view-screen"></a>表示画面のアイコンを構成する

1. **ViewScreen** 画面の上部で、円形の矢印アイコンを選びます。

    ![レコードを追加](./media/get-started-create-from-blank/refresh-icon.png)

1. そのアイコンの **OnSelect** プロパティに次の式を設定します。

    `Refresh(Schedule)`

    ユーザーがこのアイコンを選ぶと、**Schedule** からのデータが Excel ファイルのデータで更新されます。

    この関数とその他の関数について詳しくは、[数式のリファレンス](formula-reference.md)をご覧ください。

1. **ViewScreen** の右上隅で、プラス アイコンを選びます。

    ![レコードを追加](./media/get-started-create-from-blank/add-record.png)

1. そのアイコンの **OnSelect** プロパティに次の式を設定します。

    `NewForm(EditForm1);Navigate(ChangeScreen,ScreenTransition.None)`

    このアイコンをユーザーが選ぶと、レコードを作成しやすいように各フィールドが空の状態で **ChangeScreen** が表示されます。

1. ギャラリーの最初のレコードの右向き矢印を選びます。

    ![矢印を選ぶ](./media/get-started-create-from-blank/select-arrow.png)

1. 矢印の **OnSelect** プロパティに次の式を設定します。

    `EditForm(EditForm1); Navigate(ChangeScreen, ScreenTransition.None)`

    ユーザーがこのアイコンを選ぶと、**ChangeScreen** の各フィールドに選んだレコードのデータが表示され、ユーザーはいっそう簡単にレコードを編集または削除できます。

## <a name="configure-icons-on-the-change-screen"></a>変更画面のアイコンを構成する

1. **ChangeScreen** で、左上隅の "x" アイコンを選びます。

    ![[キャンセル] アイコン](./media/get-started-create-from-blank/cancel-icon.png)

1. そのアイコンの **OnSelect** プロパティに次の式を設定します。

    `ResetForm(EditForm1);Navigate(ViewScreen, ScreenTransition.None)`

    ユーザーがこのアイコンを選ぶと、ユーザーがこの画面で行ったすべての変更が破棄されて、表示画面が開きます。

1. 右上隅にあるチェックマーク アイコンを選びます。

    ![チェックマーク アイコン](./media/get-started-create-from-blank/checkmark-icon.png)

1. チェックマークの **OnSelect** プロパティに次の式を設定します。

    `SubmitForm(EditForm1); Navigate(ViewScreen, ScreenTransition.None)`

    ユーザーがこのアイコンを選ぶと、ユーザーがこの画面で行ったすべての変更が保存されて、表示画面が開きます。

1. **[挿入]** タブで **[アイコン]** を選んでから、**ごみ箱**アイコンを選びます。

1. 新しいアイコンの **Color** プロパティを **White** に設定し、新しいアイコンをチェックマーク アイコンの隣に移動します。

    ![[ごみ箱] アイコン](./media/get-started-create-from-blank/trash-icon.png)

1. ごみ箱アイコンの **Visible** プロパティに次の式を設定します。

    `EditForm1.Mode = FormMode.Edit`

    このアイコンは、フォームが **[新規]** モードではなく、 **[編集]** モードのときのみ表示されます。

1. ごみ箱アイコンの **OnSelect** プロパティに次の式を設定します。

    `Remove(Schedule, BrowseGallery1.Selected); Navigate(ViewScreen, ScreenTransition.None)`

    ユーザーがこのアイコンを選ぶと、選ばれているレコードがデータ ソースから削除され、表示画面が開きます。

## <a name="test-the-app"></a>アプリケーションをテストする

1. **ViewScreen** を選んだ後、F5 キーを押して (または右上隅の**プレビュー** アイコンを選んで) プレビューを開きます。

    ![プレビュー モードを開始](./media/get-started-create-from-blank/open-preview.png)

1. 検索ボックスに文字を 1 つ以上入力し、ボランティア名に基づいてリストをフィルター処理します。

1. ボランティア名に基づいてデータを昇順または降順で表示するために、並べ替えアイコンを 1 回以上選択します。

1. レコードを追加します。

1. 追加したレコードを更新してから、変更を保存します。

1. 追加したレコードを更新してから、変更を取り消します。

1. 追加したレコードを削除します。

1. Esc キーを押して (または右上隅の閉じるアイコンを選んで)、プレビュー モードを閉じます。

## <a name="next-steps"></a>次の手順

- 他のデバイスから実行できるように、Ctrl + S キーを押してアプリをクラウドに保存する。
- 他のユーザーが実行できるように[アプリを共有](share-app.md)する。
- 標準フォームを作らずにデータを管理できる、**Patch** などの[関数](working-with-formulas.md)について詳しく学習してください。
- [ソリューションにこのアプリをリンク](add-app-solution.md)することにより、たとえば、別の環境にデプロイしたり、AppSource に発行できるようになります。
