---
title: プロジェクト申請を処理するキャンバス アプリを生成する | Microsoft Docs
description: このタスクでは、3 つの画面を備えた基本的なキャンバス アプリを SharePoint リストから直接生成します。
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
ms.openlocfilehash: 9bfd103d2f8e6503e2897855a0d424807b9573e6
ms.sourcegitcommit: 0f0b26122be28d674af0833247b491e9367c4932
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2019
ms.locfileid: "73899419"
---
# <a name="generate-a-canvas-app-to-handle-project-requests"></a>プロジェクト申請を処理するキャンバス アプリを生成する
> [!NOTE]
> この記事は、SharePoint Online での PowerApps の使用、Power オートメーション、および Power BI に関するチュートリアルシリーズの一部です。 シリーズ全般に関することや、関連するファイルのダウンロードの詳細については、[シリーズの概要](sharepoint-scenario-intro.md)に関する記事をご覧ください。

SharePoint リストの用意ができたため、最初のアプリを作成し、カスタマイズできます。 PowerApps は SharePoint に統合されているため、基本の *3 つの画面アプリ*をリストから直接、簡単に生成できます。 このアプリを使用すると、各リスト アイテムの概要と詳細情報を表示し、既存のリスト アイテムを更新し、新規リスト アイテムを作成できます。 リストから直接アプリを作成すると、アプリがそのリストの*ビュー*として表示されます。 その後、そのアプリをブラウザーや携帯電話で実行できます。

> [!TIP]
> このシナリオ用の[ダウンロード パッケージ](https://aka.ms/o4ia0f)には、このアプリの完成版 (project-requests-app.msapp) が含まれています。

## <a name="step-1-generate-an-app-from-a-sharepoint-list"></a>手順 1: SharePoint リストからアプリを生成する

1. 作成した **Project Requests** リストで、 **[PowerApps]** 、 **[アプリの作成]** の順にクリックまたはタップします。
   
    ![アプリを作成する](./media/sharepoint-scenario-generate-app/02-01-01-create-app.png)

2. アプリに「Project Requests アプリ」のような名前を指定し、 **[作成]** をクリックまたはタップします。 アプリの準備が整うと、PowerApps Studio でそのアプリが開きます。
   
    ![アプリの名前を指定する](./media/sharepoint-scenario-generate-app/02-01-02-create-app-name.png)

## <a name="step-2-review-the-app-in-powerapps-studio"></a>手順 2: PowerApps Studio でアプリを確認する

1. PowerApps Studio では、既定では左側のナビゲーション バーに、画面の階層ビューとアプリのコントロールが表示されます。
   
    ![階層ビューが表示された PowerApps Studio](./media/sharepoint-scenario-generate-app/02-02-01-studio-screens-hierarchy.png)

2. サムネイル アイコンをクリックまたはタップしてビューを切り替えます。
   
    ![PowerApps Studio ビュー セレクター](./media/sharepoint-scenario-generate-app/02-02-02-studio-view-selector.png)

3. 各画面をクリックまたはタップして画面を中央のウィンドウに表示します。 画面は 3 つあります。
   
    (a). **ブラウズ**画面では、リストから収集されたデータを参照、並べ替え、およびフィルター処理できます。
    
    (b). **詳細**画面では、項目の詳細を表示できます。
    
    (c). **編集/作成**画面では、既存の項目を編集したり、新規の項目を作成したりできます。
      
      ![サムネイル ビューが表示された PowerApps Studio](./media/sharepoint-scenario-generate-app/02-02-03-studio-screens-thumbnails.png)

## <a name="step-3-customize-the-apps-browse-screen"></a>手順 3: アプリのブラウズ画面をカスタマイズする

1. ブラウズ画面をクリックまたはタップします。
   
    この画面には*ギャラリー*を含む*レイアウト*が配置され、リスト アイテムのほか、検索バーや並べ替えボタンなどの他の*コントロール*も表示されます。

2. 1 つ目を除く任意のレコードをクリックまたはタップして **BrowseGallery1** ギャラリーを選択します。
   
    ![ギャラリーを参照する](./media/sharepoint-scenario-generate-app/02-03-01-browse-gallery.png)

3. 右側のウィンドウで、 **[プロパティ]** から **[Project Requests]\(プロジェクト依頼\)** をクリックまたはタップします。 

4. 次の一覧と一致するフィールドを更新します。
   
   * **[RequestDate]**

   * **Requestor**

   * **Title**

     ![ギャラリー フィールド](./media/sharepoint-scenario-generate-app/02-03-02-gallery-fields.png)

5. **BrowseGallery1** を選択したまま、**Items** プロパティを選択します。
   
    ![Items プロパティ](./media/sharepoint-scenario-generate-app/02-03-03-items.png)

6. 数式を **SortByColumns(Filter('Project Requests', StartsWith(Title, TextSearchBox1.Text)), "Title", If(SortDescending1, Descending, Ascending))** のように変更します。
   
    ![数式バー](./media/sharepoint-scenario-generate-app/02-03-04-formula.png)
   
    これにより、PowerApps での既定ではなく、**Title** フィールドを基に、並べ替えおよび検索を行うことができます。 詳細については、「[数式の詳細](#formula-deep-dive)」をご覧ください。

6. **[ファイル]** 、 **[保存]** の順にクリックまたはタップします。 ![アプリに戻るアイコン](./media/sharepoint-scenario-generate-app/icon-back-to-app.png)をクリックまたはタップして、アプリに戻ります。

## <a name="step-4-review-the-apps-details-screen-and-edit-screen"></a>手順 4: アプリの詳細画面を確認し、画面を編集する
1. 詳細画面をクリックまたはタップします。
   
    この画面には*表示フォーム*を含む別のレイアウトが配置され、そこにギャラリーで選択した項目の詳細が表示されます。 また、項目を編集および削除するためのコントロールと、参照画面に戻るためのコントロールも表示されます。
   
    ![詳細表示フォーム](./media/sharepoint-scenario-generate-app/02-04-01-details.png)

4. 編集画面をクリックまたはタップします。
   
    この画面には、選択した項目を編集したり、新規項目を作成したりするための*編集フォーム*が表示されます (参照画面から直接この画面に移動した場合)。 編集内容を保存または破棄するためのコントロールがあります。

    ![編集フォーム](./media/sharepoint-scenario-generate-app/02-04-03-edit.png)

## <a name="step-5-run-the-app-from-the-list"></a>手順 5: リストからアプリを実行する

1. **Project Requests** リストで、 **[All Items]\(すべての項目\)** 、 **[Project Requests アプリ]** の順にクリックまたはタップします。
   
    ![Project Requests アプリを表示する](./media/sharepoint-scenario-generate-app/02-05-01-view-app.png)
2. **[開く]** をクリックすると、新しいブラウザー タブでアプリが開きます。
   
    ![Project Requests アプリを開く](./media/sharepoint-scenario-generate-app/02-05-02-open-app.png)

3. アプリで ![詳細に移動アイコン](./media/sharepoint-scenario-generate-app/icon-details-arrow.png) をクリックまたはタップし、参照ギャラリーの最初の項目を表示します。
   
    ![最初のギャラリー項目](./media/sharepoint-scenario-generate-app/02-05-04-first-item.png)

4. 右上にある ![鉛筆の編集アイコン](./media/sharepoint-scenario-generate-app/icon-pencil.png) をクリックまたはタップし、項目を編集します。

5. 最後の語の "グループ" を "チーム" に変更して **Description** フィールドを更新し、![チェック マーク アイコン](./media/sharepoint-scenario-generate-app/icon-check-mark.png)をクリックまたはタップします。
   
   ![[Description] フィールドを更新する](./media/sharepoint-scenario-generate-app/02-05-07-edit.png)

6. [ブラウザー] タブを閉じます。

7. **Project Requests** リストに戻り、 **[Project Requests アプリ]** 、 **[All Items]\(すべての項目\)** の順にクリックまたはタップします。
   
   ![すべての項目を表示する](./media/sharepoint-scenario-generate-app/02-05-08-view-all.png)
8. アプリから行った変更を確認します。
   
    ![編集内容を確認する](./media/sharepoint-scenario-generate-app/02-05-09-verify-edit.png)

これは非常に単純なアプリで、基本的なカスタマイズをいくつか行っただけですが、面白いものをすばやく構築できます。 次のタスクに移りますが、必要に応じて、アプリについてさらに深く考察し、コントロールと数式がどのように連携してアプリの動作を制御するかを確認してください。

## <a name="formula-deep-dive"></a>数式の詳細
このセクションは省略可能ですが、数式の使用方法を深く理解するのに役立ちます。 このタスクの手順 3 では、**BrowseGallery1** の **Items** プロパティの数式を変更しました。 具体的には、PowerApps の既定フィールドではなく**Title** フィールドを使用するように、並び替えと検索を変更しました。 次に、変更した式を示します。

**SortByColumns ( Filter ( 'Project Requests', StartsWith ( Title, TextSearchBox1.Text ) ), "Title", If ( SortDescending1, Descending, Ascending ) )**

この数式はどのような処理を行うのでしょうか。 ギャラリーに表示されるデータのソースを判別し、[検索] ボックスに入力されたテキストを基にデータをフィルター処理し、アプリの [並べ替え] ボタンを基に結果を並べ替えます。 この数式では、*関数*を使用して処理を行います。 関数は、パラメーター (入力) を受け取り、演算 (フィルター処理など) を実行し、値 (出力) を返します。

* [**SortByColumns** 関数](functions/function-sort.md)は、1 つ以上の列に基づいてテーブルを並べ替えます。
* [**Filter** 関数](functions/function-filter-lookup.md)は、指定した数式を満たすテーブル内のレコードを検索します。
* [**StartsWith** 関数](functions/function-startswith.md)は、あるテキスト文字列が別のテキスト文字列で始まるかどうかをテストします。
* [**If** 関数](functions/function-if.md)は、条件が true の場合はある値を返し、同じ条件が false の場合は別の値を返します。

これらの関数を数式に組み込むと、次のようになります。

1. [検索] ボックスにテキストを入力すると、**StartsWith** 関数は、このテキストと、リスト内の **Title** 列にある各文字列の最初の文字を比較します。
   
    **StartsWith ( Title, TextSearchBox1.Text )**
   
    たとえば、[検索] ボックスに「de」と入力すると、"Desktop" や "Device" で始まる項目を含む 4 つの結果が表示されます。 "Mobile devices" の項目は「de」*で始まる*項目ではないため、表示されません。

2. **Filter** 関数は **Project Requests** テーブルの行を*返します*。 [検索] ボックスに比較するテキストがない場合、**Filter** はすべての行を返します。
   
    **Filter ( 'Project Requests', StartsWith ( Title, TextSearchBox1.Text )**

3. **If** 関数は、変数 **SortDescending1** の設定が true か false かをチェックします (アプリの [並べ替え] ボタンで設定)。 その後、この関数は **Descending** または **Ascending** の値を返します。
   
    **If ( SortDescending1, Descending, Ascending )**

4. これで、**SortByColumns** 関数がギャラリーを並べ替えることができます。 ここでは **Title** フィールドを基に並べ替えられていますが、これを検索で使用するのとは別のフィールドにすることもできます。

ここまでお読みいただき、この数式の仕組みや、関数と他の要素を組み合わせて、アプリに必要な動作を制御する方法について理解を深めていただけると幸いです。 詳細については、「[PowerApps の数式のリファレンス](formula-reference.md)」をご覧ください。

## <a name="next-steps"></a>次の手順
このチュートリアル シリーズの次の手順では、[プロジェクトの承認を管理するフローを作成](sharepoint-scenario-approval-flow.md)します。

