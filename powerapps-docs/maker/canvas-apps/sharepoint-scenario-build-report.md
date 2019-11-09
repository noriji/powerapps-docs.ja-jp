---
title: Power BI レポートを作成してプロジェクトを分析する | Microsoft Docs
description: このタスクでは、2 つの SharePoint リストをベースに Power BI レポートを作成します。
author: fikaradz
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 01/10/2018
ms.author: fikaradz
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 9693e45da894348acd27b96f73d1358819812ae4
ms.sourcegitcommit: 0f0b26122be28d674af0833247b491e9367c4932
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2019
ms.locfileid: "73900349"
---
# <a name="create-a-power-bi-report-to-analyze-projects"></a>Power BI レポートを作成してプロジェクトを分析する
> [!NOTE]
> この記事は、SharePoint Online での PowerApps の使用、Power オートメーション、および Power BI に関するチュートリアルシリーズの一部です。 シリーズ全般に関することや、関連するファイルのダウンロードの詳細については、[シリーズの概要](sharepoint-scenario-intro.md)に関する記事をご覧ください。

このタスクでは、2 つの SharePoint リストをベースに Power BI レポートを作成します。 リストのデータを Power BI Desktop に取り込み、少し修正を加えたり、基本的なデータ モデリングを行ったりします。その後、データの分析に役立つ視覚エフェクトを作成します。

> [!TIP]
> このシナリオの[ダウンロード パッケージ](https://aka.ms/o4ia0f)には、このレポートの完成版 (project-analysis.pbix) が含まれています。

## <a name="quick-review-of-power-bi-desktop"></a>Power BI Desktop の復習
レポートの作成に進む前に、Power BI Desktop について復習しましょう。 Power BI Desktop は多くの機能を備えた強力なツールであるため、このタスクで使用する領域の概要に的をしぼって説明します。 Power BI Desktop には、**レポート** ビュー、**データ** ビュー、**リレーションシップ** ビューという 3 つの主な作業領域または *ビュー* があります。 Power BI Desktop には、別のウィンドウで開く**クエリ エディター**も含まれています。

次の画面には、Power BI Desktop の左側に 3 つのビュー アイコンが、上から**レポート**、**データ**、**リレーションシップ**の順に表示されています。 左側の黄色のバーは、現在のビューを示しています。下の画像には、**レポート** ビューが表示されています。 ビューを変更するには、これら 3 つのアイコンのいずれかを選択します。

![Power BI Desktop のビュー](./media/sharepoint-scenario-build-report/05-00-00-tabs.png)

**レポート** ビューには、5 つの主な領域があります。

1. リボン。レポートや視覚エフェクトに関連する一般的なタスクが表示されます。
2. **レポート** ビューまたはキャンバス。ここに視覚エフェクトを作成し、配置します。
3. 画面下部の **[ページ]** タブ領域。レポート ページを選択したり追加したりします。
4. **[視覚化]** ウィンドウ。ここで視覚エフェクトの変更、色や軸のカスタマイズ、フィルターの適用、フィールドのドラッグなどを行います。
5. **[フィールド]** ウィンドウ。**レポート** ビューや **[視覚化]** ウィンドウの **[フィルター]** 領域に、クエリの要素やフィルターをドラッグできます。

![Power BI Desktop のタブ、ビュー、ウィンドウ](./media/sharepoint-scenario-build-report/05-00-01-report.png)

**データ** ビューには、3 つの主な領域があります。

1. リボン。下の画像では **[モデリング]** タブが選択されています。 このタブでは、計算テーブルや列を作成し、データ モデルにその他の変更を加えます。
2. 中央のウィンドウ。選択したテーブルのデータを表示します。
3. **[フィールド]** ウィンドウ。レポートのフィールドの表示方法を管理します。

![Power BI Desktop のデータ ビュー](./media/sharepoint-scenario-build-report/05-00-02-data.png)

**リレーションシップ** ビューはこのタスクでは使用しませんが、後ほど Power BI Desktop にリスト データを取り込んだ後で確認できます。

**クエリ エディター**では、クエリを作成してデータを変換し、絞り込んだデータ モデルを Power BI Desktop に読み込みます。 **クエリ エディター**には、4 つの主な領域があります。

1. リボン。取り込んだデータを整形したり変換したりするためのさまざまなオプションがあります。
2. 左側のウィンドウ。クエリが一覧表示され、クエリを選択、表示、整形できます。
3. 中央のウィンドウ。選択したクエリのデータが表示され、データを整形できます。
4. **[クエリの設定]** ウィンドウ。クエリのプロパティと、適用したデータの変換ステップが一覧表示されます。

![Power BI Desktop のクエリ エディター](./media/sharepoint-scenario-build-report/05-00-03-query.png)

## <a name="step-1-get-data-into-power-bi-desktop"></a>手順 1: Power BI Desktop にデータを取り込む
この手順では、まず 2 つのリストに接続します。 次に、データ分析に必要のない列を削除してデータをクリーンアップします。 また、計算が正しく動作するように、残りの列のデータ型をいくつか変更します。 Power BI Desktop でデータを取得したりクリーニングしたりする方法の詳細については、ガイド学習コースの「[データの取得](https://powerbi.microsoft.com/guided-learning/powerbi-learning-1-1-overview-of-power-bi-desktop)」セクションをご覧ください。

### <a name="connect-to-sharepoint-lists"></a>SharePoint リストに接続する
1. Power BI Desktop の **[ホーム]** タブで、 **[データを取得]** 、 **[さらに表示…]** の順にクリックまたはタップします。
   
    ![データを取得](./media/sharepoint-scenario-build-report/05-01-01-get-data.png)
2. **[データを取得]** ダイアログ ボックスで、 **[SharePoint Online リスト]** 、 **[接続]** の順にクリックまたはタップします。
   
    ![SharePoint リストへの接続](./media/sharepoint-scenario-build-report/05-01-02-sharepoint-list.png)
3. SharePoint サイトの URL を入力し、 **[OK]** をクリックまたはタップします。
   
    ![SharePoint リストの URL](./media/sharepoint-scenario-build-report/05-01-03-sharepoint-url.png)
4. 次のダイアログ ボックスが表示された場合は、正しい資格情報でサインインしていることを確認し、 **[接続]** をクリックまたはタップします。
   
    ![SharePoint リストの資格情報](./media/sharepoint-scenario-build-report/05-01-04-credentials.png)
5. **Project Details** と **Project Requests** を選択し、 **[編集]** をクリックまたはタップします。
   
    ![SharePoint リストの選択](./media/sharepoint-scenario-build-report/05-01-05-list-navigator.png)
   
    リストがクエリ エディターでテーブルとして表示されます。
   
    ![クエリ エディターのテーブル](./media/sharepoint-scenario-build-report/05-01-06-query-editor.png)

### <a name="remove-unnecessary-columns-from-the-tables"></a>不要な列をテーブルから削除する
1. 左側のナビゲーション ウィンドウで、**Project Details** をクリックまたはタップします。
2. 中央のウィンドウで、 **[FileSystemObjectType]** 列を選択し、 **[列の削除]** をクリックまたはタップします。
   
    ![列の削除](./media/sharepoint-scenario-build-report/05-01-07-remove-column.png)
3. **[Id]** 列の後ろにある 2 つの列 ( **[ServerRedirectedEmbedURL]** と **[ContentTypeId]** ) を削除します。 
   > [!TIP]
   > Shift キーを使用して両方の列を選択し、 **[列の削除]** をクリックまたはタップします。
4. **[PMAssigned]** 列の右側にあるすべての列 (合計 22 列) を削除します。 テーブルは次の画像のようになります。
   
    ![クエリ エディターの Project Details テーブル](./media/sharepoint-scenario-build-report/05-01-08-table-details.png)
5. 今度は **Project Requests** でこのプロセスを最後まで繰り返します。 **[FileSystemObjectType]** 、 **[ServerRedirectedEmbedURL]** 、 **[ContentTypeId]** 、および右側にあるすべての **[承認済み]** 列 (合計 22 列) を削除します。 テーブルは次の画像のようになります。
   
    ![ クエリ エディターの Project Requests テーブル](./media/sharepoint-scenario-build-report/05-01-09-table-requests.png)

### <a name="change-the-data-type-on-project-details-columns"></a>Project Details 列のデータ型を変更する
1. **[ProjectedDays]** 列を選択し、 **[データ型: すべて]** 、 **[整数]** の順にクリックまたはタップします。
   
    ![データ型を整数に変更](./media/sharepoint-scenario-build-report/05-01-10-datatype-number.png)
2. 前述の手順を **[ActualDays]** 列でも繰り返します。
3. **[ApprovedDate]** 列を選択し、 **[データ型: すべて]** 、 **[日付]** の順にクリックまたはタップします。
   
    ![ データ型を日付に変更](./media/sharepoint-scenario-build-report/05-01-11-datatype-date.png)

4. 前述の手順を **[ProjectedStartDate]** 列と **[ProjectedEndDate]** 列でも繰り返します。

### <a name="change-the-data-type-on-project-requests-columns"></a>Project Requests 列のデータ型を変更する

1. **[EstimatedDays]** 列を選択し、 **[データ型: すべて]** 、 **[整数]** の順にクリックまたはタップします。

2. **[RequestDate]** 列を選択し、 **[データ型: すべて]** 、 **[日付]** の順にクリックまたはタップします。

### <a name="apply-and-save-changes"></a>変更を適用して保存する

1. **[ホーム]** タブで **[閉じて適用]** をクリックしてクエリ エディターを閉じ、Power BI Desktop のメイン ウィンドウに戻ります。
   
    ![変更を閉じて適用](./media/sharepoint-scenario-build-report/05-01-12-close-apply.png)

2. **[ファイル]** 、 **[保存]** の順にクリックまたはタップし、“project-analysis.pbix” というファイル名で保存します。

## <a name="step-2-improve-the-data-model"></a>手順 2: データ モデルを改善する
SharePoint リストから Power BI Desktop へのデータの取り込みが完了したので、次にデータ モデリングを行います。 データ モデリングには時間がかかる場合がありますが、Power BI Desktop のリスト データからより多くの情報を得られる興味深い方法を簡単にご紹介します。

* 2 つのテーブルの相互関係を変更する
* 日付テーブルを追加して平日に基づいて計算できるようにする
* 計算列を追加してプロジェクトのマイルストーン間の期間を計算する
* メジャーを追加してプロジェクトの予測日数と実績日数の差異を計算する

この手順が完了すれば、モデルの機能強化を活用する視覚エフェクトを作成できます。 Power BI Desktop でのデータのモデリングについて詳しくは、ガイド学習コースの「[モデリング](https://powerbi.microsoft.com/guided-learning/powerbi-learning-2-1-intro-modeling-data)」セクションをご覧ください。

### <a name="change-table-relationships"></a>テーブル間のリレーションシップを変更する
Power BI Desktop でリストを取り込むと、両方のテーブルの **[Id]** 列に基づいてこのリスト間のリレーションシップが作成されます。 正確には、**Project Requests** テーブルの **[Id]** 列と、**Project Details** テーブルの **[RequestId]** 列とのリレーションシップです。 それを修正します。

1. **データ ビュー** アイコンをクリックまたはタップします。
   
    ![データ ビュー](./media/sharepoint-scenario-build-report/05-02-01-data-view.png)

2. **[モデリング]** タブで、 **[リレーションシップの管理]** をクリックまたはタップします。 データ モデリングの手順では、最後まで**データ** ビューのこのタブ上で作業を行います。
   
    ![リレーションシップの管理](./media/sharepoint-scenario-build-report/05-02-02-manage-relationships.png)

3. 既存のリレーションシップが選択されていることを確認し、 **[削除]** をクリックまたはタップします。その後、確認のためにもう一度 **[削除]** をクリックまたはタップします。
   
    ![リレーションシップの削除](./media/sharepoint-scenario-build-report/05-02-03-delete-relationship.png)

4. **[新規]** をクリックして、別のリレーションシップを作成します。

5. **[リレーションシップの作成]** ダイアログ ボックスで次の作業を行います。
   
   1. 最初のテーブルで、 **[Project Requests]** を選択して **[Id]** 列を選択します。
   
   2. 2 つ目のテーブルで、 **[Project Details]** を選択して **[RequestId]** 列を選択します。
   
   3. 画面は次の画像のように表示されます。 準備ができたら **[OK]** 、 **[閉じる]** の順にクリックまたはタップします。
      
       ![リレーションシップの削除](./media/sharepoint-scenario-build-report/05-02-04-create-relationship.png)

### <a name="add-a-date-table-to-make-date-based-calculations-easier"></a>日付テーブルを追加して、日付ベースでの計算を簡単に行えるようにする
1. **[新しいテーブル]** をクリックまたはタップします。
   
    ![新しいテーブル](./media/sharepoint-scenario-build-report/05-02-05-modeling-table.png)
2. 次の数式を数式バーに入力します: **Dates = CALENDARAUTO()**
   
    ![Dates = CALENDARAUTO() と入力された数式バー](./media/sharepoint-scenario-build-report/05-02-06-formula-bar.png)
   
    この数式は、日付列 1 つを含む "**Dates**" というテーブルを作成します。 このテーブルには、お使いの他のテーブルのすべての日付が含まれています。また、日付が追加された場合 (データが更新された場合) は、自動で更新されます。
   
    この数式とこのセクションのその他の数式では、Power BI や他のテクノロジで使用されている数式言語の Data Analysis Expressions (DAX) を使用します。 詳細については、「[Power BI Desktop における DAX の基本事項](https://docs.microsoft.com/power-bi/desktop-quickstart-learn-dax-basics)」をご覧ください。
3. Enter キーを押して、 **[Dates]** テーブルを作成します。
   
    ![[Dates] テーブル](./media/sharepoint-scenario-build-report/05-02-07-date-table.png)

### <a name="add-a-calculated-column-to-the-dates-table"></a>[Dates] テーブルに計算列を追加する
1. [Dates] テーブルを表示した状態で、 **[新しい列]** をクリックまたはタップします。
   
    ![新しい列](./media/sharepoint-scenario-build-report/05-02-00-modeling-column.png)
2. 次の数式を数式バーに入力します: **IsWeekDay = SWITCH(WEEKDAY(Dates[Date]), 1,0,7,0,1)**
   
    この数式は、 **[Date]** 列の日付が平日かどうかを決定します。 日付が平日なら **[IsWeekDay]** 列の値が 1 になり、そうでない場合は 0 になります。
3. Enter キーを押して、 **[Dates]** テーブルに **[IsWeekDay]** 列を追加します。
   
    ![[IsWeekDay] 列の追加](./media/sharepoint-scenario-build-report/05-02-08-column-isweekday.png)

### <a name="add-a-calculated-column-to-the-project-details-table"></a>Project Details テーブルに計算列を追加する
1. 右側のウィンドウで、**Project Details** テーブル、 **[新しい列]** の順にクリックまたはタップします。
   
    ![新しい列](./media/sharepoint-scenario-build-report/05-02-00-modeling-column.png)
2. 次の数式を数式バーに入力します。
   
    ```dax
    ApprovedStartDiff = CALCULATE(SUM(Dates[IsWeekday]),
       DATESBETWEEN(Dates[Date],
          'Project Details'[ApprovedDate],
          'Project Details'[ProjectedStartDate]
      )
    )
    ```
   
    この数式は、プロジェクトが承認された日からプロジェクトの開始予定日までの日数を計算します。 **[Dates]** テーブルの **[IsWeekday]** 列を使用し、平日のみをカウントします。
3. Enter キーを押して、**Project Details** テーブルに **[ApprovedStartDiff]** 列を追加します。
   
    ![[ApprovedStartDiff] 列の追加](./media/sharepoint-scenario-build-report/05-02-09-column-approvedstartdiff.png)

### <a name="add-a-calculated-column-to-the-project-requests-table"></a>Project Requests テーブルに計算列を追加する
1. 右側のウィンドウで、 **[Project Requests]** テーブル、 **[新しい列]** の順にクリックまたはタップします。
   
    ![新しい列](./media/sharepoint-scenario-build-report/05-02-00-modeling-column.png)
2. 次の数式を数式バーに入力します。
   
    ```dax
    RequestDateAge = CALCULATE(SUM(Dates[IsWeekday]),
       DATESBETWEEN(Dates[Date],
          'Project Requests'[RequestDate],
          NOW()
       )
    )
    ```
   
    この数式は、プロジェクトが要求された日から、本日の日付 (NOW()) までの日数を計算します。 先ほど同様、この数式は平日のみをカウントします。 この列は、保留期間が最も長いプロジェクトの検索に使用します。
3. Enter キーを押して、 **[Project Requests]** テーブルに **[RequestDateAge]** 列を追加します。
   
    ![[RequestDateAge] 列の追加](./media/sharepoint-scenario-build-report/05-02-10-column-requestdateage.png)

### <a name="add-a-measure-to-the-project-details-table"></a>Project Details テーブルにメジャーを追加する
1. 右側のウィンドウで、**Project Details** テーブル、 **[新しいメジャー]** の順にクリックまたはタップします。
   
    ![新しいメジャー](./media/sharepoint-scenario-build-report/05-02-00-modeling-measure.png)
2. 次の数式を数式バーに入力します。
   
    ```dax
    VarProjectedActual = DIVIDE(
        SUM('Project Details'[ActualDays]) - SUM('Project Details'[ProjectedDays]),
        SUM('Project Details'[ProjectedDays])
    )
    ```
   
    この数式は、プロジェクトの実績日数と予測日数との差異を計算します。 この数式を計算列ではなくメジャーとして追加することで、レポートでのデータのフィルター方法や集計方法に関わらず、正しい結果を返すことができます。
3. Enter キーを押して、**Project Details** テーブルに **[VarProjectedActual]** メジャーを追加します。
   
    ![[VarProjectedActual] メジャーの追加](./media/sharepoint-scenario-build-report/05-02-11-measure-varprojectedactual.png)

### <a name="add-a-measure-to-the-project-requests-table"></a>Project Requests テーブルにメジャーを追加する
1. 右側のウィンドウで、 **[Project Requests]** テーブル、 **[新しいメジャー]** の順にクリックまたはタップします。
   
    ![新しいメジャー](./media/sharepoint-scenario-build-report/05-02-00-modeling-measure.png)
2. 次の数式を数式バーに入力します。
   
    ```dax
    MaxDaysPending = MAXX(
        FILTER('Project Requests', 'Project Requests'[Approved]="Pending"),
        'Project Requests'[RequestDateAge]
    )
    ```
   
    この数式は、先ほど定義した計算列に基づいて、保留期間が最も長いプロジェクトを検索します。
3. Enter キーを押して、 **[Project Requests]** テーブルに **[MaxDaysPending]** メジャーを追加します。
   
    ![[MaxDaysPending] メジャーの追加](./media/sharepoint-scenario-build-report/05-02-12-measure-maxdayspending.png)

## <a name="step-3-create-report-visualizations"></a>手順 3: レポートの視覚エフェクトを作成する
データの分析について考えるときに、多くの人が思い浮かべる段階まで到達しました。視覚エフェクトを作成することで、データのパターンを見つけることができます。 この手順では、4 つの視覚エフェクトを作成します。

* プロジェクトの予測日数と実績日数を示す縦棒グラフ
* 各プロジェクトの差異を示す縦棒グラフ
* 保留期間が最も長いプロジェクトを示すカード
* プロジェクトの承認日から開始予定日までの期間を示すテーブル

Power BI Desktop でこれらのレポートの視覚エフェクトを作成してから、Power BI サービスにデータとレポートを発行します。これにより、ダッシュボードの作成と共有が可能になります。 Power BI Desktop でのレポートの作成について詳しくは、ガイド学習コースの「[視覚エフェクト](https://powerbi.microsoft.com/guided-learning/powerbi-learning-3-1-intro-visualizations)」セクションをご覧ください。

### <a name="create-a-bar-chart-to-show-projected-versus-actual"></a>予測と実績を示す棒グラフを作成する
1. **レポート ビュー** アイコンをクリックまたはタップします。 Power BI Desktop での残りの作業では、最後までこのビューを使用します。
   
    ![レポート ビュー](./media/sharepoint-scenario-build-report/05-03-01-report-view.png)
2. 右側の **[視覚化]** ウィンドウで、 **[集合縦棒グラフ]** をクリックまたはタップします。
   
    ![視覚エフェクト - 集合縦棒グラフ](./media/sharepoint-scenario-build-report/05-03-00-visuals-column.png)
3. **[フィールド]** ウィンドウの **[Project Details]** から **[PMAssigned]** と **[Title]** をドラッグして、 **[視覚化]** ウィンドウの **[軸]** にドロップします。
   
    ![[視覚化] ウィンドウの [軸]](./media/sharepoint-scenario-build-report/05-03-00-axis.png)
4. **[フィールド]** ウィンドウの **[Project Details]** から **[ActualDays]** と **[ProjectedDays]** をドラッグして、 **[視覚化]** ウィンドウの **[値]** にドロップします。
   
    ![[視覚化] ウィンドウの [値]](./media/sharepoint-scenario-build-report/05-03-03-value-projected.png)
5. 視覚エフェクトは次の画像のように表示されます。
   
    ![[PMAssigned] ごとの [ProjectedDays] と [ActualDays]](./media/sharepoint-scenario-build-report/05-03-04-chart-projected.png)
6. **[フィールド]** ウィンドウの **[Project Details]** から **[Status]** をドラッグし、 **[視覚化]** ウィンドウの **[フィルター]** 領域にドロップしてから、 **[完了]** チェック ボックスをオンにします。
   
   ![[Status] 列によるフィルター](./media/sharepoint-scenario-build-report/05-03-05-filters-projected.png)
   
   完了したプロジェクトのみを表示するフィルターがグラフに設定されました。予測した日数と実際の日数を比較しているところなので、これは理にかなっています。
7. グラフの左上隅にある矢印をクリックして、プロジェクト管理者とプロジェクトの階層を上下に移動できます。 次の画像は、プロジェクトの詳細がどのように表示されるかを示しています。
   
   ![縦棒グラフの詳細](./media/sharepoint-scenario-build-report/05-03-06-chart-projected-drill.png)

### <a name="create-a-bar-chart-to-show-variance-from-projected"></a>予測との差異を示す棒グラフを作成する
1. 先ほど作成した視覚エフェクトの外側のキャンバスをクリックまたはタップします。
2. 右側の **[視覚化]** ウィンドウで、 **[集合縦棒グラフ]** をクリックまたはタップします。
   
    ![視覚エフェクト - 集合縦棒グラフ](./media/sharepoint-scenario-build-report/05-03-00-visuals-column.png)
3. **[フィールド]** ウィンドウの **[Project Details]** から **[PMAssigned]** と **[Title]** をドラッグして、 **[視覚化]** ウィンドウの **[軸]** にドロップします。
   
    ![[視覚化] ウィンドウの [軸]](./media/sharepoint-scenario-build-report/05-03-00-axis.png)
4. **[フィールド]** ウィンドウの **[Project Details]** から **[VarProjectedActual]** をドラッグし、 **[視覚化]** ウィンドウの **[値]** にドロップします。
   
    ![[視覚化] ウィンドウの [値]](./media/sharepoint-scenario-build-report/05-03-07a-value-variance.png)
5. **[フィールド]** ウィンドウの **[Project Details]** から **[Status]** をドラッグし、 **[視覚化]** ウィンドウの **[フィルター]** 領域にドロップしてから、 **[完了]** チェック ボックスをオンにします。
   
    ![[Status] 列によるフィルター](./media/sharepoint-scenario-build-report/05-03-07b-filters-variance.png)
   
    視覚エフェクトは次の画像のように表示されます。
   
    ![[PMAssigned] ごとの [VarProjectedActual]](./media/sharepoint-scenario-build-report/05-03-08-chart-variance.png)
   
    このグラフを見れば、Irvin Sayers と Joni Sherman によって実行されたそれぞれのプロジェクトにどの程度のばらつきがあるのか一目瞭然です。 プロジェクトごとのばらつきを詳しく確認し、予測日数が実績日数より多かったのか少なかったのかを確認します。
   
    ![[Title] ごとの [VarProjectedActual]](./media/sharepoint-scenario-build-report/05-03-09-chart-variance-drill.png)
6. さらに視覚エフェクトを作成する前に、既に作成した視覚エフェクトを移動したりサイズ変更したりして、横に並べます。
   
    ![グラフを横に並べる](./media/sharepoint-scenario-build-report/05-03-10-two-charts.png)

### <a name="create-a-card-that-shows-the-longest-pending-project"></a>保留期間が最も長いプロジェクトを示すカードを作成する
1. 先ほど作成した視覚エフェクトの外側のキャンバスをクリックまたはタップします。
2. 右側の **[視覚化]** ウィンドウで、 **[カード]** をクリックまたはタップします。
   
    ![視覚エフェクト - カード](./media/sharepoint-scenario-build-report/05-03-11-visuals-card.png)
3. **[フィールド]** ウィンドウの **[Project Requests]** から **[MaxDaysPending]** をドラッグし、 **[視覚化]** ウィンドウの **[フィールド]** にドロップします。
   
    ![[視覚化] ウィンドウの [フィールド]](./media/sharepoint-scenario-build-report/05-03-12-value-max.png)
4. **[書式]** (ペイント ローラー) をクリックまたはタップして、 **[罫線]** を **[オン]** に設定します。
   
    ![書式ペインター - 罫線](./media/sharepoint-scenario-build-report/05-03-13a-format.png)
5. **[タイトル]** を **[オン]** に設定し、「承認プロジェクトの最大保留日数」と入力します。
   
    ![タイトルの追加](./media/sharepoint-scenario-build-report/05-03-13b-title.png)
   
    視覚エフェクトは次の画像のように表示されます。
   
    ![ 承認プロジェクトの最大保留日数](./media/sharepoint-scenario-build-report/05-03-14-chart-max.png)
   
    このレポートを発行したあと、このタイルを使用して、保留中のプロジェクトの最大値が特定のしきい値に達した場合に、アラートをトリガーするようにします。

### <a name="create-a-table-that-shows-the-time-between-project-approval-and-projected-start-date"></a>プロジェクトの承認日から開始予定日までの期間を表示するテーブルを作成する
1. 先ほど作成した視覚エフェクトの外側のキャンバスをクリックまたはタップします。
2. 右側の **[視覚化]** ウィンドウで、 **[テーブル]** をクリックまたはタップします。
   
    ![視覚エフェクト - テーブル](./media/sharepoint-scenario-build-report/05-03-15-visuals-table.png)
3. **[フィールド]** ウィンドウの **[Project Details]** から **[PMAssigned]** 、 **[Title]** 、 **[ApprovedStartDiff]** をドラッグして、 **[視覚化]** ウィンドウの **[値]** にドロップします。
   
    ![[視覚化] ウィンドウの [値]](./media/sharepoint-scenario-build-report/05-03-16-value-diff.png)
4. **[フィールド]** ウィンドウの **[Project Details]** から **[ProjectedStartDate]** をドラッグし、 **[視覚化]** ウィンドウの **[フィルター]** 領域にドロップし、 **[(空白)]** 以外のすべての日付を選択します。
   
    ![[ProjectedStartDate] によるフィルター](./media/sharepoint-scenario-build-report/05-03-17-filters-diff.png)
5. すべてのデータが表示されるようにテーブルの列のサイズを調整し、 **[ApprovedStartDiff]** で降順に並び替えます。 視覚エフェクトは次の画像のように表示されます。
   
    ![[ApprovedStartDiff] の値が表示されたテーブル](./media/sharepoint-scenario-build-report/05-03-18-chart-diff.png)
6. **[値]** の領域で、 **[ApprovedStartDiff]** の下矢印をクリックまたはタップしてから、 **[平均]** をクリックまたはタップします。 これで、プロジェクトの承認日から開始予定日までにかかった平均日数を確認できるようになりました。
   
    ![平均の計算](./media/sharepoint-scenario-build-report/05-03-20a-average-menu.png)
7. **[ApprovedStartDiff]** の下矢印をもう一度クリックまたはタップし、 **[条件付き書式]** 、 **[バックグラウンドのカラー スケール]** の順にクリックまたはタップします。
   
   ![条件付き書式](./media/sharepoint-scenario-build-report/05-03-20b-conditional-menu.png)
8. 次に示すように **[最小]** と **[最大]** フィールドの色を設定し、 **[OK]** をクリックまたはタップします。
   
   ![条件付き書式のオプション](./media/sharepoint-scenario-build-report/05-03-21-conditional-dialog.png)
   
   視覚エフェクトは次の画像のように表示されます。
   
   ![条件付き書式の完了](./media/sharepoint-scenario-build-report/05-03-22-chart-diff-completed.png)
   
   ご覧のように、Irvin Sayers が実行するプロジェクトは承認から開始までの期間が長い傾向があります。 割り当てられた管理者以外の要因がある可能性もありますが、これは詳しく調べてみる価値がありそうです。

レポートに関するセクションはこれで終了です。SharePoint からインポートし、Power BI Desktop でクリーンアップおよびモデリングしたデータをベースとしたレポートが完成しました。 すべてが手順どおりに進んでいれば、レポートは次の画像のように表示されているはずです。

![完成したレポート](./media/sharepoint-scenario-build-report/05-03-23-report-completed.png)

## <a name="next-steps"></a>次の手順
このチュートリアル シリーズの次の手順では、[Power BI プロジェクトのレポートを発行してダッシュボードを作成](sharepoint-scenario-publish-report.md)します。

