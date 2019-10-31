---
title: プロジェクトの承認を管理するフローを作成する | Microsoft Docs
description: このタスクでは、プロジェクトの承認プロセスを進めるフローを作成します。
author: stepsic-microsoft-com
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 01/09/2018
ms.author: stepsic
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 9dc1fa02737b49261dc76a06e208cea578e80dea
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2019
ms.locfileid: "73182594"
---
# <a name="create-a-flow-to-manage-project-approvals"></a>プロジェクトの承認を管理するフローを作成する
> [!NOTE]
> この記事は、SharePoint Online で PowerApps、Microsoft Flow、Power BI を使用するチュートリアル シリーズの一部です。 シリーズ全般に関することや、関連するファイルのダウンロードの詳細については、[シリーズの概要](sharepoint-scenario-intro.md)に関する記事をご覧ください。

このタスクでは、プロジェクトの承認プロセスを進めるフローを作成します。 Microsoft Flow は SharePoint と統合されているため、リストから直接、簡単にフローを作成できます。 作成するフローは、項目が **Project Requests** リストに追加されると、トリガーされます。 フローがプロジェクトの承認者に電子メールを送信し、承認者は申請を電子メールで直接承認または拒否します。 その後、フローはプロジェクト申請者に承認または拒否の電子メールを送信し、SharePoint リストを適宜更新します。

## <a name="step-1-configure-the-flow-template"></a>手順 1: フロー テンプレートを構成する
1. **Project Requests** リストで、 **[フロー]** 、 **[フローの作成]** の順にクリックまたはタップします。
   
    ![フローの作成](./media/sharepoint-scenario-approval-flow/03-01-01-create-flow.png)
2. 右側のウィンドウで、 **[新しいアイテムが追加されたときに承認を開始する]** をクリックまたはタップします。
   
    ![承認フローの作成](./media/sharepoint-scenario-approval-flow/03-01-02-approval-flow.png)
3. サインインをまだ行っていない場合、SharePoint と Outlook にサインインし、 **[続行]** をクリックまたはタップします。
   
    ![テンプレートを使用してサインイン](./media/sharepoint-scenario-approval-flow/03-01-03-continue.png)
   
    このフローのテンプレートが、完了待ちの状態で表示されます。 フロー内のボックスは手順を表します。 これらは前の手順からの入力と、ユーザーが指定した入力を受け取ります。 各手順は後続の手順に出力を渡すことができます。
   
    ![承認テンプレート](./media/sharepoint-scenario-approval-flow/03-01-04-template.png)
4. **[担当者]** ボックスに、テナントで有効な名前を入力します。
   
    ![承認の電子メールの問い合わせ先](./media/sharepoint-scenario-approval-flow/03-01-05-approval-email.png)
   
    フローの次のボックスでは、プロジェクトの承認者の決定に応答し、 **[はいの場合]** または **[いいえの場合]** の 2 つの*分岐*のいずれかにフローをルーティングします。
   
    ![承認条件](./media/sharepoint-scenario-approval-flow/03-01-06-condition.png)

## <a name="step-2-create-actions-for-approve--yes"></a>手順 2: 承認アクションを作成する = yes
既定では、この分岐によって申請者に承認の電子メールが送信されます。 プロジェクトが承認されているため、**Project Requests** リストも更新され、**Project Details** リストに項目が追加されます。

1. **[はいの場合]** の分岐で、 **[Inform item creator of approval]\(項目作成者に承認を通知する\)** 、 **[編集]** の順にクリックまたはタップして、申請者に送信された電子メールの既定のオプションを表示します。
   
    ![電子メールの設定を編集する](./media/sharepoint-scenario-approval-flow/03-01-07-yes-email.png)
2. 既定では、電子メールはリスト アイテムを作成したユーザーに対して送信されます。ユーザーは件名とメッセージ本文を確認できます。 これらは必要に応じて更新できます。
   
    ![既定の電子メールの設定](./media/sharepoint-scenario-approval-flow/03-01-07a-yes-email-defaults.png)
3. **[Add an Action]\(アクションの追加\)** をクリックまたはタップします。
   
    ![アクションの追加](./media/sharepoint-scenario-approval-flow/03-00-01-add-action.png)
4. **[アクションを選択してください]** から "SharePoint" を検索し、 **[SharePoint – Update item]\(SharePoint – 項目の更新\)** をクリックまたはタップします。
   
    ![項目の更新アクション](./media/sharepoint-scenario-approval-flow/03-00-02-update.png)
5. SharePoint サイトの URL とリスト名を入力します。
   
    ![項目の更新パラメーター](./media/sharepoint-scenario-approval-flow/03-00-03-update-list.png)
6. **[ID]** ボックスを選択し、 *[ダイナミック コンテンツ]* ダイアログ ボックスで **ID** をクリックまたはタップします。
   
    ![リスト ID ダイナミック コンテンツ](./media/sharepoint-scenario-approval-flow/03-00-04-list-id.png)
   
    ダイナミック コンテンツは、前の手順を基にフロー全体で使用できます。 ここでは、SharePoint リストの情報が利用可能です。また、作成するアクションでこれを使用できます。
7. **[Title]** ボックスを選択して、[ダイナミック コンテンツ] ダイアログ ボックスで "Title" を検索し、 **[Title]** をクリックまたはタップします。
   
    ![リスト タイトル ダイナミック コンテンツ](./media/sharepoint-scenario-approval-flow/03-00-05-list-title.png)
8. **[Approved]** ボックスで「Yes」と入力します。 フローのこの部分は次の図のように表示されます。
   
    ![リストの更新](./media/sharepoint-scenario-approval-flow/03-01-08-yes-update-complete.png)
9. **[Add an Action]\(アクションの追加\)** を再度クリックまたはタップします。 今回は、承認済みプロジェクトの **Project Details** リストに項目を追加します。
   
    ![アクションの追加](./media/sharepoint-scenario-approval-flow/03-00-01-add-action.png)
10. **[アクションを選択してください]** から "SharePoint" を選択し、 **[SharePoint – Create item]\(SharePoint – 項目の作成\)** をクリックまたはタップします。
    
    ![項目の作成アクション](./media/sharepoint-scenario-approval-flow/03-01-09-create.png)
11. SharePoint サイトの URL とリスト名を入力します。
    
    ![項目の作成パラメーター](./media/sharepoint-scenario-approval-flow/03-01-10-yes-create-list.png)
12. **[Title]** ボックスを選択して、[ダイナミック コンテンツ] ダイアログ ボックスで "Title" を検索し、 **[Title]** をクリックまたはタップします。
    
    ![リスト タイトル ダイナミック コンテンツ](./media/sharepoint-scenario-approval-flow/03-00-05-list-title.png)
13. **[RequestId]** ボックスを選択し、[ダイナミック コンテンツ] ダイアログ ボックスで **[ID]** をクリックまたはタップします。
    
    ![リスト ID ダイナミック コンテンツ](./media/sharepoint-scenario-approval-flow/03-00-04-list-id.png)
14. **[PMAssigned]** ボックスで「Unassigned」と入力します。 フローのこの部分は次の図のように表示されます。
    
    ![項目の作成の完了](./media/sharepoint-scenario-approval-flow/03-01-11-yes-create-complete.png)

## <a name="step-3-review-action-for-approve--no"></a>手順 3: 承認アクションを確認する = no
既定では、この分岐によって申請者に拒否の電子メールが送信されます。 **Project Requests** リストも更新します。 プロジェクトは現在進行していないため、**Project Details** リストには項目を追加しません。

1. **[いいえの場合]** の分岐で、 **[Inform item creator of rejection]\(項目作成者に拒否を通知する\)** 、 **[編集]** の順にクリックまたはタップして、申請者に送信された電子メールの既定のオプションを表示します。
   
    ![電子メールの設定を編集する](./media/sharepoint-scenario-approval-flow/03-01-12-no-email.png)
2. 既定では、電子メールはリスト アイテムを作成したユーザーに対して送信されます。ユーザーは件名とメッセージ本文を確認できます。 これらは必要に応じて更新できます。
   
    ![既定の電子メールの設定](./media/sharepoint-scenario-approval-flow/03-01-13-no-email-defaults.png)
3. **[Add an Action]\(アクションの追加\)** をクリックまたはタップします。
   
    ![アクションの追加](./media/sharepoint-scenario-approval-flow/03-00-01-add-action.png)
4. **[アクションを選択してください]** から "SharePoint" を検索し、 **[SharePoint – Update item]\(SharePoint – 項目の更新\)** をクリックまたはタップします。
   
    ![項目の更新アクション](./media/sharepoint-scenario-approval-flow/03-00-02-update.png)
5. SharePoint サイトの URL とリスト名を入力します。
   
    ![項目の更新パラメーター](./media/sharepoint-scenario-approval-flow/03-00-03-update-list.png)
6. **[ID]** ボックスを選択し、[ダイナミック コンテンツ] ダイアログ ボックスで **ID** をクリックまたはタップします。
   
    ![リスト ID ダイナミック コンテンツ](./media/sharepoint-scenario-approval-flow/03-00-04-list-id.png)
7. **[Title]** ボックスを選択して、[ダイナミック コンテンツ] ダイアログ ボックスで "Title" を検索し、 **[Title]** をクリックまたはタップします。
   
    ![リスト タイトル ダイナミック コンテンツ](./media/sharepoint-scenario-approval-flow/03-00-05-list-title.png)
8. **[Approved]** ボックスで「No」と入力します。 フローのこの部分は次の図のように表示されます。
   
    ![リストの更新](./media/sharepoint-scenario-approval-flow/03-01-08-no-update-complete.png)
9. 画面の右上で **[フローの作成]** をクリックまたはタップします。
   
    フローが完了しました。ボックスを折りたたむと、次の図のようになります。
   
    ![完了フロー](./media/sharepoint-scenario-approval-flow/03-01-16-flow-complete.png)

10. 画面の右上で **[完了]** をクリックまたはタップします。
   
    ![[完了] ボタン](./media/sharepoint-scenario-approval-flow/03-01-15a-done-button.png)

## <a name="step-4-run-the-approval-flow"></a>手順 4: 承認フローを実行する
1. **Project Requests** リストで、 **[クイック編集]** をクリックして、次のような項目を追加します。
   
   * **[Title]** = "New monitor for Megan"

   * **[Description]** = "Megan が 24 インチのモニターを必要としている"

   * **[ProjectType]** = "新規ハードウェア"

   * **[RequestDate]** = "02/03/2017"

   * **[Requestor]** = "Megan Bowen"

   * **[EstimatedDays]** = "1"

   * **[Approved]** = "保留中"

     ![リストに追加される項目](./media/sharepoint-scenario-approval-flow/03-02-01-list-add.png)
2. 完了したら、ページの最上部で **[完了]** をクリックします。
   
    ![完了チェック マーク](./media/sharepoint-scenario-approval-flow/03-02-02-done.png)
3. 承認者の電子メール アカウントの受信トレイを確認します。 次のような電子メールを受け取っています。
   
    ![Allan Deyoung への電子メール](./media/sharepoint-scenario-approval-flow/03-02-03-allan-email.png)
4. **[承認]** または **[拒否]** をクリックすると、フローは別のプロセスを実行し、次のようなフィードバックを直接電子メールで受け取ります。
   
    ![承認アクションの完了](./media/sharepoint-scenario-approval-flow/03-02-04-action-complete.png)
5. フローは、次の図のとおり、Allan の返答を含む電子メールを Megan に送信します。 この電子メールは Megan *から*送信されます。それは、彼女がフローを所有しているためです。
   
    ![Megan Bowen への電子メール](./media/sharepoint-scenario-approval-flow/03-02-05-megan-email.png)

## <a name="next-steps"></a>次の手順
このチュートリアル シリーズの次の手順では、[プロジェクトを管理するアプリを作成](sharepoint-scenario-build-app.md)します。

