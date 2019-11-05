---
title: SharePoint Online 統合シナリオの一通りの手順 | Microsoft Docs
description: このチュートリアル シリーズで構築したシナリオ全体について説明します。
author: NickWaggoner
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 06/12/2017
ms.author: niwaggon
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: ed4b729926cc8a818f8c2d47b98656c91b934788
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2019
ms.locfileid: "73542482"
---
# <a name="walk-end-to-end-through-the-completed-sharepoint-online-integration-scenario"></a>完成した SharePoint Online 統合シナリオ全体の説明
> [!NOTE]
> この記事は、SharePoint Online で PowerApps、Microsoft Flow、Power BI を使用するチュートリアル シリーズの一部です。 シリーズ全般に関することや、関連するファイルのダウンロードの詳細については、[シリーズの概要](sharepoint-scenario-intro.md)に関する記事をご覧ください。

このチュートリアル シリーズでは、キャンバス アプリとフローの構築からレポートの作成と SharePoint への埋め込みに至るまで、幅広い内容を説明しました。 多くのことを学び、これらのテクノロジの統合の仕組みをしっかりと理解し、お客様自身のニーズに応じてキャンバス アプリやフロー、レポートを SharePoint に統合できるようになっていただきたいと思います。 このチュートリアル シリーズを終える前にシナリオ全体をおさらいして、すべての部分がどのように連携しているかを見ていきましょう。

## <a name="step-1-add-a-project-to-the-project-requests-list"></a>手順 1: Project Requests リストにプロジェクトを追加する
1. **Project Requests** リストで、 **[All Items]\(すべての項目\)** 、 **[Project Requests アプリ]** の順にクリックまたはタップします。
   
    ![Project Requests アプリの表示](./media/sharepoint-scenario-summary/09-00-01-view-app.png)
2. **[開く]** をクリックすると、新しいブラウザー タブでアプリが開きます。
   
    ![Project Requests アプリを開く](./media/sharepoint-scenario-summary/09-00-02-open-app.png)
3. アプリで ![項目の追加アイコン](./media/sharepoint-scenario-summary/icon-add-item.png) をクリックまたはタップし、新しい項目を作成します。
4. フォームに次の値を記入します。
   
   * **[Title]** = "設計チームのモバイル デバイス"

   * **[Approved]** = "保留中"

   * **[Description]** = "設計チームは今後 Contoso 提供のデバイスを使用する"

   * **[EstimatedDays]** = "30"

   * **[ProjectType]** = "新規ハードウェア"

   * **[RequestDate]** = "03/01/2017"

   * **[Requestor]** = "Emily Braun"
     
     ![Project Requests 編集フォーム](./media/sharepoint-scenario-summary/09-01-01-app-new.png)
5. 右上にある ![チェック マーク アイコン](./media/sharepoint-scenario-summary/icon-check-mark.png)をクリックまたはタップし、ブラウザーのタブを閉じます。
6. **Project Requests** リストに戻り、 **[Project Requests アプリ]** 、 **[All Items]\(すべての項目\)** の順にクリックまたはタップします。
   
    ![すべての項目を表示する](./media/sharepoint-scenario-summary/09-01-01a-view-all.png)
7. リストで新しいエントリを確認します。
   
    ![新しいエントリが追加された SharePoint リスト](./media/sharepoint-scenario-summary/09-01-02-list-new.png)

## <a name="step-2-approve-the-project"></a>手順 2: プロジェクトを承認する
1. 手順 1 で項目が追加されると、フローが実行されて承認メールが送信されます。 承認者の電子メール アカウントの受信トレイを確認します。
   
    ![承認依頼メール](./media/sharepoint-scenario-summary/09-02-01-allan-email.png)
2. **[承認]** をクリックします。 フローによって別のプロセスが実行され、次のようなフィードバックを直接電子メールで受け取ります。
   
    ![アクションの完了](./media/sharepoint-scenario-summary/09-02-01a-action-complete.png)
3. 申請者の電子メール アカウントの受信トレイを確認すると、承認メールが届いています。
   
    ![申請者への承認メール](./media/sharepoint-scenario-summary/09-02-02-megan-email.png)
4. リストで更新されたエントリを確認します。
   
    ![エントリが更新された SharePoint リスト](./media/sharepoint-scenario-summary/09-02-03-yes.png)

## <a name="step-3-assign-a-manager-to-the-project"></a>手順 3: プロジェクトに管理者を割り当てる
1. 最初に、SharePoint の **Project Details** リストを見てみましょう。 新しいプロジェクトの **[PMAssigned]** 列の値が **[未割り当て]** になっています。
   
    ![未割り当ての SharePoint リスト項目](./media/sharepoint-scenario-summary/09-03-01-unassigned.png)
2. SharePoint サイトの左側のナビゲーションで、 **[Project Management アプリ]** をクリックまたはタップします。
3. 最初の画面で、 **[Assign Manager]** をクリックまたはタップします。
   
    ![プロジェクトへの管理者の割り当て](./media/sharepoint-scenario-summary/09-03-02-intro-screen.png)
4. **[Assign Manager]** 画面で、リストに 2 つの未割り当てプロジェクトが表示されています。 **設計チームのモバイル デバイス** プロジェクトを選択します。
   
    ![アプリで選択された未割り当てのプロジェクト](./media/sharepoint-scenario-summary/09-03-03-selected.png)
5. **[管理者]** のテキスト入力欄に、「Joni Sherman」と入力して **[OK]** をクリックします。
   
    変更がリストに反映されてギャラリーが更新されると、残りの未割り当てプロジェクトのみが表示されます。
   
    ![プロジェクトに割り当てられた管理者](./media/sharepoint-scenario-summary/09-03-04-updated.png)
6. アプリを閉じて、SharePoint リストに戻ります。 プロジェクトのエントリが更新されてプロジェクト管理者名が表示されます。
   
    ![割り当て済みの SharePoint リスト項目](./media/sharepoint-scenario-summary/09-03-05-assigned.png)

## <a name="step-4-add-time-estimates-for-the-project"></a>手順 4: プロジェクトの時間の見積を追加する
1. ![戻るアイコン](./media/sharepoint-scenario-summary/icon-back.png) をクリックまたはタップして最初の画面に戻り、 **[Update Details]** をクリックまたはタップします。
   
    ![プロジェクトの詳細の更新](./media/sharepoint-scenario-summary/09-04-00-intro-screen.png)
2. **[プロジェクトの表示]** 画面で、検索ボックスに「モバイル」と入力します。
   
    ![アプリで検索](./media/sharepoint-scenario-summary/09-04-01-search-mobile.png)
3. **[設計チームのモバイル デバイス]** の項目の![詳細を表示する矢印アイコン](./media/sharepoint-scenario-summary/icon-details-arrow.png)をクリックします。
   
    ![更新するプロジェクトの選択](./media/sharepoint-scenario-summary/09-04-02-select-project.png)
4. **[Update Details]** 画面で、次の値を設定します。
   
   * **[Status]** フィールド = "未着手"

   * **[ProjectedStartDate]** フィールド = "3/6/2017"

   * **[ProjectedEndDate]** フィールド = "3/24/2017"

   * **[ProjectedDays]** フィールド = "15"
     
     ![プロジェクトの詳細の更新](./media/sharepoint-scenario-summary/09-04-03-update.png)
5. 右上にある ![チェック マーク アイコン](./media/sharepoint-scenario-summary/icon-check-mark.png) をクリックまたはタップして、SharePoint リストに変更を適用します。
6. アプリを閉じて、リストに戻ります。 プロジェクトのエントリが更新されて変更日時が表示されます。
   
   ![情報が更新された SharePoint リスト](./media/sharepoint-scenario-summary/09-04-04-updated-list.png)

## <a name="step-5-review-report-data-for-existing-projects"></a>手順 5: 既存のプロジェクトのレポート データを確認する
1. SharePoint Online で、 **[サイト コンテンツ]** 、 **[サイト ページ]** の順にクリックまたはタップします。
2. 以前に作成した **[プロジェクト分析]** ページを開きます。
   
    ![埋め込まれたプロジェクト分析レポート](./media/sharepoint-scenario-summary/09-05-01-report-complete.png)
3. 差異の視覚エフェクトを確認します。
   
    ![差異を示すグラフ](./media/sharepoint-scenario-summary/09-05-02-chart-variance.png)
   
    この視覚エフェクトを作成したときにも気がつきましたが、Irvin Sayers が実行したプロジェクトと Joni Sherman が実行したプロジェクトではさらに多くの差異があります。
4. この視覚エフェクトを詳しく見ると、差異の大半は見積よりも大幅に時間のかかった 2 つのプロジェクトに由来することがわかります。
   
    ![差異の詳細を示すグラフ](./media/sharepoint-scenario-summary/09-05-03-chart-variance-drill.png)
5. プロジェクトの承認から開始予定日までの期間を示すテーブルを確認します。
   
    ![開始日との差を示すテーブル](./media/sharepoint-scenario-summary/09-05-04-chart-diff-completed.png)
   
    この視覚エフェクトを作成したときにも気がつきましたが、Irvin Sayers が担当したプロジェクトは開始までの期間が長く、特に 2 つのプロジェクトは他のプロジェクトよりも大幅に時間がかかっています。

## <a name="step-6-respond-to-pending-project-delays"></a>手順 6: 保留中のプロジェクトの遅延に対応する
1. Power BI サービスで、**project-analysis** のデータセットをクリックまたはタップし、 **[今すぐ更新]** をクリックまたはタップします。 更新することで、保留中のプロジェクトに設定したアラートがトリガーされます。
   
    ![データセットを今すぐ更新](./media/sharepoint-scenario-summary/09-06-01-refresh.png)
2. 更新が完了すると、右上の**通知センター**に新しい通知アイコンが表示されます。
   
    ![Power BI 通知センター](./media/sharepoint-scenario-summary/09-06-02-alert.png)
   
    表示には時間がかかる場合があるため、すぐに表示されない場合は再度確認してください。
3. 通知センターを開いて、発生したアラートの詳細を確認します。
   
    ![データ アラートの通知](./media/sharepoint-scenario-summary/09-06-03-notification.png)
4. アラートを作成したユーザー (ここでは Megan Bowen) の受信トレイをチェックします。
   
    ![Power BI からのアラート メール](./media/sharepoint-scenario-summary/09-06-04-email-powerbi.png)
5. データ アラート フローに追加したユーザー (ここでは Allan DeYoung) の受信トレイをチェックします。
   
    ![Microsoft Flow からのアラート メール](./media/sharepoint-scenario-summary/09-06-05-email-flow.png)
6. 保留中のプロジェクトに関する情報を取得したら、元の画面に戻って、注意を払うべきプロジェクトを承認できます。

今回の一通りの手順と、このチュートリアル シリーズはこれで終了です。 引き続き次のサイトもぜひご覧ください。

* [PowerApps](https://www.powerapps.com/)
* [Microsoft Flow](https://flow.microsoft.com)
* [Power BI](https://www.powerbi.com)
* [Power Users Community](https://powerusers.microsoft.com/)
* [SharePoint](https://sharepoint.microsoft.com)
* [Microsoft Tech Community](https://techcommunity.microsoft.com/)

このシリーズのフィードバック、追加事項のご提案、または今回ご紹介したテクノロジの活用に役立つ追加のコンテンツに関してご意見のある方は、下のコメント欄にご記入ください。

