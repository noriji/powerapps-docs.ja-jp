---
title: プロジェクトを管理するキャンバス アプリを作成する | Microsoft Docs
description: このタスクでは、キャンバス アプリを最初から作成します。 ユーザーはこのアプリを使用してプロジェクトの管理者を割り当てたり、プロジェクトの詳細な情報を更新したりできます。
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 06/12/2017
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: aa927559c13726bd2d780c7ce3841c5a53317c8f
ms.sourcegitcommit: 0f0b26122be28d674af0833247b491e9367c4932
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2019
ms.locfileid: "73899212"
---
# <a name="create-a-canvas-app-to-manage-projects"></a>プロジェクトを管理するキャンバス アプリを作成する
> [!NOTE]
> この記事は、SharePoint Online での PowerApps の使用、Power オートメーション、および Power BI に関するチュートリアルシリーズの一部です。 シリーズ全般に関することや、関連するファイルのダウンロードの詳細については、[シリーズの概要](sharepoint-scenario-intro.md)に関する記事をご覧ください。

このタスクでは、キャンバス アプリを最初から作成します。 ユーザーはこのアプリを使用してプロジェクトの管理者を割り当てたり、プロジェクトの詳細な情報を更新したりできます。 最初のアプリで学習したときと同じコントロールと数式がいくつか出てきますが、今回はそのときよりも多くの機能を自分で作成します。 今回の方がより複雑ですが、より多くのことが学べますので、学習して損しません。

> [!TIP]
> このシナリオの[ダウンロード パッケージ](https://aka.ms/o4ia0f)には、このアプリの完成版 (project-details-app.msapp) が含まれています。

## <a name="quick-review-of-powerapps-studio"></a>PowerApps Studio の復習
PowerApps Studio は 3 つのウィンドウと 1 つのリボンで構成されているため、PowerPoint でスライド デッキを作成するのと同じような感覚でアプリを作成できます。

1. 左側のナビゲーション バー。アプリのすべての画面の階層ビューとコントロールが表示され、画面のサムネイルも表示されます
2. 中央のウィンドウ。作業しているアプリの画面が表示されます
3. 右側のウィンドウ。レイアウトやデータ ソースなどのオプションを設定します
4. プロパティ ドロップダウン リスト。数式を適用するプロパティを選択します
5. 数式バー。アプリの動作を定義する数式を (Excel のように) 追加します
6. リボン。コントロールを追加し、デザイン要素をカスタマイズします

![PowerApps Studio](./media/sharepoint-scenario-build-app/04-00-00-powerapps-studio.png)

## <a name="step-1-create-screens"></a>手順 1: 画面を作成する
復習はほどほどにして、さっそくアプリの作成を開始しましょう。

### <a name="create-and-save-the-app"></a>アプリの作成と保存
1. PowerApps Studio で、 **[新規]** をクリックまたはタップして、 **[空のアプリ]** の下にある **[電話レイアウト]** をクリックまたはタップします。
   
    ![空のアプリ - 電話レイアウト](./media/sharepoint-scenario-build-app/04-01-01-blank-phone-app.png)
2. **[ファイル]** をクリックまたはタップして、 **[アプリの設定]** タブを開きます。 "プロジェクト管理アプリ" という名前を入力します。
   
    ![アプリ名](./media/sharepoint-scenario-build-app/04-01-02-app-name.png)
3. **[名前を付けて保存]** をクリックまたはタップして、アプリの保存先がクラウドであることを確認したら、右下隅にある **[保存]** をクリックします。
   
    ![クラウドに保存](./media/sharepoint-scenario-build-app/04-01-03-save-to-cloud.png)

4. 右上にある ![アプリに戻るアイコン](./media/sharepoint-scenario-build-app/icon-back-to-app.png) をクリックまたはタップしてアプリに戻ります。

### <a name="add-four-screens-to-the-app"></a>アプリに 4 つの画面を追加する
この手順では、アプリに 4 つの空の画面を作成します。 画面の目的に応じて、画面のレイアウトが異なります。 後の手順で、これらの画面に内容を追加します。

| **画面** | **目的** |
| --- | --- |
| **SelectTask** |開始画面。他の画面に移動します |
| **AssignManager** |承認されたプロジェクトに管理者を割り当てます |
| **ViewProjects** |プロジェクトの一覧と概要情報を表示します |
| **UpdateDetails** |プロジェクトの詳細を表示したり、更新したりします |

1. **[ホーム]** タブで、 **[新しい画面]** 、 **[スクロール可能な画面]** の順にクリックまたはタップします。
   
    ![スクロール可能な画面](./media/sharepoint-scenario-build-app/04-01-03a-scrollable-screen.png)
2. 画面の名前を「**SelectTask**」に変更します。
   
    ![画面の名前変更](./media/sharepoint-scenario-build-app/04-01-04-rename-screen.png)
3. 追加の画面を作成し、名前を変更します。
   
   1. **[新しい画面]** 、 **[スクロール可能な画面]** の順にクリックまたはタップします。 画面の名前を「**AssignManager**」に変更します。
   2. **[新しい画面]** 、 **[リスト画面]** の順にクリックまたはタップします。 画面の名前を「**ViewProjects**」に変更します。
   3. **[新しい画面]** 、 **[フォーム画面]** の順にクリックまたはタップします。 画面の名前を「**UpdateDetails**」に変更します。
4. **Screen 1** の横にある省略記号 ( **. . .** ) を選択し、 **[削除]** をクリックまたはタップします。
   
    ![画面の削除](./media/sharepoint-scenario-build-app/04-01-04a-delete-screen.png)

アプリは次のように表示されます。

![アプリのすべての画面](./media/sharepoint-scenario-build-app/04-01-05-all-screens.png)

## <a name="step-2-connect-to-a-sharepoint-list"></a>手順 2: SharePoint リストに接続する
この手順では、 **Project Details** SharePoint リストに接続します。 このアプリでは 1 つのリストを使用するだけですが、アプリを拡張するときは両方に簡単に接続できます。

1. 左側のナビゲーション バーで、**SelectTask** 画面をクリックまたはタップします。
2. 右側のウィンドウで、 **[データ ソースの追加]** をクリックまたはタップします。
   
    ![データに接続する](./media/sharepoint-scenario-build-app/04-02-01-connect.png)
3. **[新しい接続]** をクリックまたはタップします。
   
    ![新しい接続](./media/sharepoint-scenario-build-app/04-02-02-new-connection.png)
4. **[SharePoint]** をクリックまたはタップします。
   
    ![SharePoint 接続](./media/sharepoint-scenario-build-app/04-02-03-sharepoint-connection.png)
5. **[直接接続 (クラウド サービス)]** を選択して、 **[作成]** をクリックまたはタップします。
   
    ![直接接続 (クラウド サービス)](./media/sharepoint-scenario-build-app/04-02-03a-sharepoint-cloud.png)
6. SharePoint の URL を入力し、 **[移動]** をクリックまたはタップします。
   
    ![接続先の SharePoint の URL](./media/sharepoint-scenario-build-app/04-02-04-sharepoint-url.png)
7. **Project Details** リストを選択し、 **[接続]** をクリックまたはタップします。
   
    ![Project Details リストの選択](./media/sharepoint-scenario-build-app/04-02-05-sharepoint-lists.png)
   
    右側のウィンドウにある **[データ ソース]** タブに、作成した接続が表示されます。
   
    ![[データ ソース] タブ](./media/sharepoint-scenario-build-app/04-02-06-data-sources.png)

## <a name="step-3-build-the-selecttask-screen"></a>手順 3: SelectTask 画面を作成する
この手順では、PowerApps のコントロール、数式、書式設定オプションを使用して、アプリの他の画面に移動する方法を説明します。

### <a name="update-the-title-and-insert-introductory-text"></a>タイトルを更新して概要テキストを挿入する
1. 左側のナビゲーション バーで、**SelectTask** 画面を選択します。
2. 中央のウィンドウで既定の **[Title]** を選択し、数式バーで **Text** プロパティを "Contoso Project Management" に更新します。
   
    ![数式バーの Text プロパティ](./media/sharepoint-scenario-build-app/04-03-02-text-property.png)
3. **[挿入]** タブで、 **[ラベル]** をクリックまたはタップし、上部のバナーの下にラベルをドラッグします。
   
    ![ラベルの追加](./media/sharepoint-scenario-build-app/04-03-03-text-default.png)
4. 数式バーで、ラベルに次のプロパティを設定します。
   
   * **Color** プロパティ = **DarkGray**

   * **Size** プロパティ = **18**

   * **Text** プロパティ = "**Click or tap a task to continue..."**
     
     ![ラベルのテキストの変更](./media/sharepoint-scenario-build-app/04-03-04-text-updated.png)

### <a name="add-two-navigation-buttons"></a>2 つのナビゲーション ボタンを追加する
1. **[挿入]** タブで、 **[ボタン]** をクリックまたはタップし、ラベルの下にボタンをドラッグします。
   
    ![[追加] ボタン](./media/sharepoint-scenario-build-app/04-03-05-button-default.png)
2. 数式バーで、ボタンに次のプロパティを設定します。
   
   * **OnSelect** プロパティ = **Navigate(AssignManager, Fade)** アプリを実行してこのボタンをクリックすると、アプリの 2 番目の画面に移動する際にフェードして画面が切り替わります。

   * **Text** プロパティ = **"Assign Manager"**

3. テキストに合わせてボタンのサイズを変更します。
   
    ![ボタンのテキストの更新](./media/sharepoint-scenario-build-app/04-03-06-button-updated.png)
4. 次のプロパティを持つ別のボタンを挿入します。
   
   * **OnSelect** プロパティ = **Navigate(ViewProjects, Fade)**

   * **Text** プロパティ = **"Update Details"**
     
     ![ボタンのテキストの更新](./media/sharepoint-scenario-build-app/04-03-08-buttons-final.png)
     
     > [!NOTE]
     > ボタンのラベルは **Update Details** ですが、最初に **ViewProjects** 画面に移動して、更新するプロジェクトを選択します。

### <a name="run-the-app"></a>アプリの実行
アプリの完成にはまだほど遠いですが、一度アプリを実行してみることができます。

1. **SelectTask** 画面をクリックまたはタップします (アプリは常に PowerApps Studio のプレビュー モードで選択した画面から開始します)。

2. 右上にある ![アプリの実行アイコン](./media/sharepoint-scenario-build-app/icon-run-arrow.png) をクリックまたはタップし、アプリを実行します。

3. ボタンのいずれか 1 つをクリックまたはタップして別の画面に移動します。

4. 右上にある ![アプリ プレビューを閉じるアイコン](./media/sharepoint-scenario-build-app/icon-close-preview.png) をクリックまたはタップしてアプリを閉じます。

## <a name="step-4-build-the-assignmanager-screen"></a>手順 4: AssignManager 画面を作成する
この手順では、承認後にまだ管理者が割り当てられていないプロジェクトを、ギャラリーを使用してすべて表示します。 他のコントロールを追加することで、管理者を割り当てられるようになります。

> [!NOTE]
>  プロジェクトのすべてのフィールド (管理者フィールドも含む) を編集できるページをあとでアプリ内に作成しますが、このような画面も作成したほうが出来栄えが良くなります。

1. ここまでに行った変更を保存します。

2. 左側のナビゲーション バーで、**AssignManager** 画面をクリックまたはタップします。

### <a name="update-the-title-and-insert-introductory-text"></a>タイトルを更新して概要テキストを挿入する

1. **[Title]** を **Assign Manager** に変更します。

2. 次のプロパティをラベルに追加します。
   
   * **Color** プロパティ = **DarkGray**

   * **Size** プロパティ = **18**

   * **Text** プロパティ = "**Select a project, then assign a manager"**
     
     ![管理者の割り当てのレイアウト](./media/sharepoint-scenario-build-app/04-04-01-layout.png)

### <a name="add-a-back-arrow-to-return-to-the-selecttask-screen"></a>SelectTask 画面に戻るための戻る矢印を追加する

1. 画面の上部に表示される青色のバーをクリックまたはタップします。

2. **[挿入]** タブで、 **[アイコン]** 、 **[左]** の順にクリックまたはタップします。
   
    ![左矢印の挿入](./media/sharepoint-scenario-build-app/04-04-02-icon-left.png)

3. 青色のバーの左側に矢印を移動し、次のプロパティを設定します。
   
   * **Color** プロパティ = **White**

   * **Height** プロパティ = **40**

   * **OnSelect** プロパティ = **Navigate(SelectTask, Fade)**

   * **Width** プロパティ = **40**
     
     ![戻るボタンの追加](./media/sharepoint-scenario-build-app/04-04-03-left-arrow.png)

### <a name="add-and-modify-a-gallery"></a>ギャラリーを追加して変更する

1. **[挿入]** タブで、 **[ギャラリー]** 、 **[縦]** の順にクリックまたはタップします。
   
    ![縦方向のギャラリーの追加](./media/sharepoint-scenario-build-app/04-04-04-gallery.png)

2. 右側のウィンドウにある **[レイアウト]** メニューから、 **[タイトル、サブタイトル、本文]** を選択します。 
   
    ![ギャラリー レイアウトの変更](./media/sharepoint-scenario-build-app/04-04-04a-gallery-layout.png)
   
    ギャラリーに適切なレイアウトが作成されましたが、既定のサンプル テキストが表示されたままです。 次にこれを修正します。
   
    ![既定のテキストが表示されているギャラリー](./media/sharepoint-scenario-build-app/04-04-05-gallery-default.png)

3. ギャラリーに次のプロパティを設定します。
   
   * **BorderThickness** プロパティ = **1**

   * **BorderStyle** プロパティ = **Dotted**

   * **Items** プロパティ = **Filter('Project Details', PMAssigned="Unassigned")** 管理者が割り当てられていないプロジェクトのみがギャラリーに表示されます。
     
     ![リストからのテキストが表示されているギャラリー](./media/sharepoint-scenario-build-app/04-04-06-gallery-updated.png)

4. 右側のウィンドウで、次の一覧と一致するフィールドを更新します。
   
   * **ApprovedDate**

   * **Status**

   * **Title**
     
     ![ギャラリー フィールド](./media/sharepoint-scenario-build-app/04-04-07-gallery-fields.png)

5. 必要に応じて、ギャラリー内のラベルのサイズを変更し、最初のギャラリー項目から矢印を削除します (このギャラリー内から別の場所に移動する必要はありません)。
   
    ![矢印アイコンの削除](./media/sharepoint-scenario-build-app/04-04-07a-remove-arrow.png)
   
    画面は次のように表示されます。
   
    ![書式設定されたギャラリー](./media/sharepoint-scenario-build-app/04-04-07b-gallery-size-text.png)

### <a name="change-the-color-of-an-item-if-its-selected"></a>選択された場合の項目の色を変更する

1. ギャラリーを選択し、**TemplateFill** プロパティを **If (ThisItem.IsSelected=true, Orange, White)** に設定します。

2. ギャラリー内の項目を選択します。 画面は次のように表示されます。
   
    ![選択した項目が表示されているギャラリー](./media/sharepoint-scenario-build-app/04-04-08-gallery-selected.png)

### <a name="add-a-label-text-input-and-ok-button-to-submit-manager-assignments"></a>管理者の割り当てを送信するための、ラベル、テキスト入力、OK ボタンを追加する

1. 作業していたギャラリーの外側をクリックまたはタップします。

2. **[挿入]** タブで、 **[ラベル]** をクリックまたはタップします。 ギャラリーの下のラベルを左側にドラッグします。 ラベルに次のプロパティを設定します。
   
   * **Size** プロパティ = **20**

   * **Text** プロパティ = **"Manager:"**
   
   ![管理者ラベルの追加](./media/sharepoint-scenario-build-app/04-04-09-controls-text.png)

3. **[挿入]** タブで、 **[テキスト]** 、 **[テキスト入力]** の順にクリックまたはタップします。 ギャラリーの下のテキスト入力を中央にドラッグします。 ドロップダウンに次のプロパティを設定します。
   
   * **Default** プロパティ = **""**

   * **Height** プロパティ = **60**

   * **Size** プロパティ = **20**

   * **Width** プロパティ = **250**
   
   ![テキスト入力の追加](./media/sharepoint-scenario-build-app/04-04-10-controls-text-box.png)

4. **[挿入]** タブで、 **[ボタン]** をクリックまたはタップします。 ギャラリーの下のボタンを右側にドラッグします。 ボタンに次のプロパティを設定します。
   
   * **Height** プロパティ = **60**

   * **OnSelect** プロパティ = **Patch('Project Details', LookUp('Project Details', ID = Gallery1.Selected.ID), {PMAssigned: TextInput1.Text})** 詳細については、「[Formula deep-dive (数式の詳細)](#formula-deep-dive)」をご覧ください。

   * この数式で、**Project Details** リストを更新し、PMAssigned フィールドの値を設定します。

   * **Size** プロパティ = **20**

   * **Text** プロパティ = **"OK"**

   * **Width** プロパティ = **80**
   
   ![OK ボタンの追加](./media/sharepoint-scenario-build-app/04-04-11-controls-button.png)

完成した画面は次のように表示されます。

![管理者の割り当て完成画面](./media/sharepoint-scenario-build-app/04-04-12-complete.png)

## <a name="step-5-build-the-viewprojects-screen"></a>手順 5: ViewProjects 画面を作成する
この手順では、**ViewProjects** 画面でギャラリーのプロパティを変更します。 このギャラリーで **Project Details** リストの項目が表示されます。 この画面で項目を選択し、**UpdateDetails** 画面で詳細を編集します。

1. 左側のナビゲーション バーで、**ViewProjects** 画面をクリックまたはタップします。

2. **[Title]** を **"View Projects"** に変更します。

3. 左側のナビゲーション バーで、**ViewProjects** の下にある **BrowserGallery1** をクリックまたはタップします。

4. 右側のウィンドウにある **[レイアウト]** メニューから、 **[タイトル、サブタイトル、本文]** を選択します。 
   
    ![ギャラリー レイアウトの変更](./media/sharepoint-scenario-build-app/04-04-04a-gallery-layout.png)
   
    ギャラリーに適切なレイアウトが作成され、既定のサンプル テキストが表示されています。
   
    ![既定のテキストが表示されているギャラリー](./media/sharepoint-scenario-build-app/04-04-04b-gallery-default.png)

5. 更新ボタン ![更新アイコン](./media/sharepoint-scenario-build-app/icon-refresh.png) を選択し、その **OnSelect** プロパティを **Refresh('Project Details')** に設定します。

6. 新しい項目ボタン ![新規追加アイコン](./media/sharepoint-scenario-build-app/icon-add-item.png) を選択し、その **OnSelect** プロパティを **NewForm(EditForm1); Navigate(UpdateDetails, ScreenTransition.None)** に設定します。

### <a name="add-a-back-arrow-to-return-to-the-selecttask-screen"></a>SelectTask 画面に戻るための戻る矢印を追加する

1. 左側のナビゲーション バーで、**AssignManager** 画面をクリックまたはタップします。

2. ここに追加した戻る矢印を選択し、コピーします。

3. 矢印を **ViewProjects** 画面に貼り付けて、更新ボタンの左側に配置します。 
   
    ![戻るボタン](./media/sharepoint-scenario-build-app/04-05-04-left-arrow-v.png)
   
    **OnSelect** プロパティの **Navigate(SelectTask, Fade)** も含め、プロパティのすべてがコピーされます。

### <a name="change-the-data-source-for-the-browsegallery1-gallery"></a>BrowseGallery1 ギャラリーのデータ ソースを変更する

1. **BrowseGallery1** ギャラリーを選択し、ギャラリーの **Items** プロパティを **SortByColumns(Filter('Project Details', StartsWith(Title, TextSearchBox1.Text)), "Title", If(SortDescending1, Descending, Ascending))** に設定します。
   
    これにより、ギャラリーのデータ ソースが **Project Details** リストに設定され、その **[Title]** フィールドを使用して検索や並べ替えが行われるようになります。

2. 最初のギャラリー項目にある ![詳細矢印アイコン](./media/sharepoint-scenario-build-app/icon-details-arrow.png) を選択し、**OnSelect** プロパティを **Navigate(UpdateDetails, None)** に設定します。
   
    ![ プロジェクトの表示ギャラリー - 最初の選択項目](./media/sharepoint-scenario-build-app/04-05-05b-gallery-arrow-v.png)

3. 右側のウィンドウで、次の一覧と一致するフィールドを更新します。
   
   * **Status**

   * **PMAssigned**

   * **Title**
     
     ![ギャラリー フィールド](./media/sharepoint-scenario-build-app/04-05-06-gallery-fields.png)
     
     完成した画面は次のように表示されます。
     
     ![完成したプロジェクトの表示画面](./media/sharepoint-scenario-build-app/04-05-07-viewprojects-final.png)

## <a name="step-6-build-the-updatedetails-screen"></a>手順 6: UpdateDetails 画面を作成する
この手順では、**UpdateDetails** 画面の編集フォームをデータ ソースに接続し、いくつかのプロパティとフィールドを変更します。 この画面で、 **[プロジェクトの表示]** 画面で選択したプロジェクトの詳細を編集します。

1. 左側のナビゲーション バーで、**UpdateDetails** 画面をクリックまたはタップします。

2. **[Title]** を **"Update Details"** に変更します。

3. 左側のナビゲーション バーで、**UpdateDetails** の下にある **EditForm1** をクリックまたはタップします。

4. フォームに次のプロパティを設定します。
   
   * **DataSource** プロパティ = **'Project Details'**

   * **Item** プロパティ = **BrowseGallery1.Selected**

5. フォームを選択したまま、右側のウィンドウで、次の順番で表示されるフィールドのチェックボックスをクリックまたはタップします。
   
   * **Title**

   * **PMAssigned**

   * **Status**

   * **ProjectedStartDate**

   * **ProjectedEndDate**

   * **ProjectedDays**

   * **ActualDays**
     
     ![フォームのフィールドの編集](./media/sharepoint-scenario-build-app/04-06-03-edit-fields.png)
6. キャンセル ボタン ![キャンセル アイコン](./media/sharepoint-scenario-build-app/icon-cancel.png) を選択し、その **OnSelect** プロパティを **ResetForm(EditForm1); Back()** に設定します。

7. 保存ボタン ![チェック マーク保存アイコン](./media/sharepoint-scenario-build-app/icon-check-mark.png) を選択し、**OnSelect** の数式が **SubmitForm(EditForm1)** になっていることを確認します。 編集フォーム コントロールを使用するため、以前使用した **Patch()** ではなく **Submit()** を使用できます。

完成した画面は次のように表示されます (フィールドが空白の場合は、必ず **[プロジェクトの表示]** 画面で項目を選択してください)。

![完成した Update Details 画面](./media/sharepoint-scenario-build-app/04-06-06-edit-final.png)

## <a name="step-7-run-the-app"></a>手順 7: アプリを実行する
アプリが完成したので、実行して動作を確認します。 SharePoint サイトにアプリへのリンクを追加します。 ブラウザーでアプリを実行することもできますが、アプリを他の人に共有して実行してもらう必要がある場合もあります。 詳細については、「[アプリの共有](https://powerapps.microsoft.com/guided-learning/learning-manage-share-apps)」をご覧ください。

### <a name="add-a-link-to-the-app"></a>アプリへのリンクを追加する
1. Office 365 アプリ起動ツールで、**PowerApps** をクリックまたはタップします。
   
    ![Office 365 アプリ起動ツール内の PowerApps](./media/sharepoint-scenario-build-app/04-07-02a-waffle.png)

2. PowerApps で、**Project Management アプリ**の省略記号 ( **. . .** ) を選択して **[開く]** をクリックまたはタップします。
   
    ![Project Management アプリの選択](./media/sharepoint-scenario-build-app/04-07-02b-select-app.png)

3. ブラウザーでアプリのアドレス (URL) をコピーします。
   
    ![アプリの URL のコピー](./media/sharepoint-scenario-build-app/04-07-02ba-copy-url.png)

4. SharePoint で、 **[リンクの編集]** をクリックまたはタップします。
   
    ![SharePoint サイトのリンクの編集](./media/sharepoint-scenario-build-app/04-07-02c-edit-links.png)

5. **[(+) link]\((+) リンク\)** をクリックまたはタップします。
   
    ![SharePoint サイトへのアプリ リンクの追加](./media/sharepoint-scenario-build-app/04-07-02d-add-link.png)

6. 「Project Management アプリ」と入力し、アプリのアドレスを貼り付けます。
   
    ![リンクのプロパティの編集](./media/sharepoint-scenario-build-app/04-07-02e-link-dialog.png)

7. **[OK]** 、 **[保存]** の順にクリックまたはタップします。
   
    ![リンクの変更の保存](./media/sharepoint-scenario-build-app/04-07-02f-save.png)

### <a name="assign-a-manager-to-a-project"></a>プロジェクトに管理者を割り当てる
SharePoint サイトでアプリの準備ができたので、続いてプロジェクト承認者のロールに基づき、管理者が割り当てられていないプロジェクトを探し、プロジェクトの 1 つに管理者を割り当てます。 次に、プロジェクト管理者のロールに基づき、自分たちに割り当てられているプロジェクトに関する情報を追加します。

1. 最初に、SharePoint の **Project Details** リストを見てみましょう。 2 つのプロジェクトで、 **[PMAssigned]** 列の値が **Unassigned** になっています。 アプリ内でこれらを確認します。
   
    ![SharePoint リスト内の未割り当てプロジェクト](./media/sharepoint-scenario-build-app/04-07-01-unassigned.png)

2. 作成したアプリへのリンクをクリックまたはタップします。

3. 最初の画面で、 **[Assign Manager]** をクリックまたはタップします。
   
    ![アプリの概要画面](./media/sharepoint-scenario-build-app/04-07-03-intro-screen.png)

4. **[Assign Manager]** 画面で、リストに 2 つの未割り当てプロジェクトが表示されています。 **新しい BI ソフトウェア** プロジェクトを選択します。
   
    ![選択した項目が表示されているギャラリー](./media/sharepoint-scenario-build-app/04-07-04-selected.png)

5. **[管理者]** のテキスト入力欄に、「Joni Sherman」と入力して **[OK]** をクリックします。
   
    変更がリストに反映されてギャラリーが更新されると、残りの未割り当てプロジェクトのみが表示されます。
   
    ![プロジェクトへの管理者の割り当て](./media/sharepoint-scenario-build-app/04-07-05-updated.png)

6. SharePoint リストに戻り、ページを更新します。 プロジェクトのエントリが更新されてプロジェクト管理者名が表示されます。
   
    ![SharePoint リストに割り当てられたプロジェクト管理者](./media/sharepoint-scenario-build-app/04-07-07-assigned.png)

### <a name="update-details-for-the-project"></a>プロジェクトの詳細の更新

1. ![戻るアイコン](./media/sharepoint-scenario-build-app/icon-back.png) をクリックまたはタップして最初の画面に戻り、 **[Update Details]** をクリックまたはタップします。
   
   ![アプリの概要画面](./media/sharepoint-scenario-build-app/04-07-08-intro-screen.png)

2. **[プロジェクトの表示]** 画面で、検索ボックスに「New」と入力します。
   
   ![アプリのギャラリー内で検索](./media/sharepoint-scenario-build-app/04-07-09-search-new.png)

3. **新しい BI ソフトウェア**項目の ![詳細矢印アイコン](./media/sharepoint-scenario-build-app/icon-details-arrow.png) をクリックします。
   
   ![選択したギャラリー項目](./media/sharepoint-scenario-build-app/04-07-10-select-project.png)

4. **[Update Details]** 画面で、次の値を設定します。
   
   * **[ProjectedStartDate]** フィールド = "3/6/2017"

   * **[ProjectedEndDate]** フィールド = "3/24/2017"

   * **[ProjectedDays]** フィールド = "15"
   
   ![項目の詳細の更新](./media/sharepoint-scenario-build-app/04-07-11-update.png)

5. 右上にある ![チェック マーク アイコン](./media/sharepoint-scenario-build-app/icon-check-mark.png) をクリックまたはタップして、SharePoint リストに変更を適用します。

6. アプリを閉じて、リストに戻ります。 プロジェクトのエントリが更新されて変更日時が表示されます。
   
    ![SharePoint リストの更新](./media/sharepoint-scenario-build-app/04-07-11-updated-list.png)

## <a name="formula-deep-dive"></a>数式の詳細
このセクションは、PowerApps の数式に関する 2 つ目の省略可能なセクションです。 最初の詳細では、PowerApps が生成し、3 画面アプリ内のブラウズ ギャラリーで使用される数式の 1 つを確認しました。 この詳細では、2 つ目のアプリの **AssignManager** 画面で使用する数式を確認します。 数式は次のとおりです。

**Patch (' Project Details ', LookUp (' Project Details ', ID = Gallery1.Selected.ID), {PMAssigned: TextInput1})**

この数式について説明します。 ギャラリーで項目を選択して **[OK]** ボタンをクリックすると、この数式は **Project Details** リストを更新し、 **[PMAssigned]** 列にテキスト入力で指定した値を設定します。 この数式は、次の関数を使用します。

* [**Patch** 関数](functions/function-patch.md)は、データ ソースの 1 つ以上のレコードを変更します。

* [**LookUp** 関数](functions/function-filter-lookup.md)は、テーブル内で数式を満たす最初のレコードを検索します。

これらの関数を数式に組み込むと、次のようになります。

1. **[OK]** ボタンをクリックすると、**Patch** 関数が呼び出されて **Project Details** リストを更新します。

2. **Patch** 関数内で、**LookUp** 関数は **Project Details** リストのどの行を更新するのかを特定します。 選択したギャラリー項目の ID とリスト内の ID を比較することで特定しています。 たとえば、ID を 12 とすると、**新しい BI ソフトウェア**のエントリが更新されます。

3. **Patch** 関数は正しい ID を取得すると、 **[PMAssigned]** フィールドを更新して **TextInput1.Text** 内の値に設定します。

## <a name="next-steps"></a>次の手順
このチュートリアル シリーズの次の手順では、[プロジェクトを分析する Power BI レポートを作成](sharepoint-scenario-build-report.md) します。

