---
title: キャンバス アプリ用の Expense Report サンプルをインストールして構成する | Microsoft Docs
description: PowerApps でキャンバス アプリ用の Expense Report サンプルをインストールして構成する詳細な手順を示します。
author: matthewbolanos
manager: kvivek
ms.service: powerapps
ms.topic: sample
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/29/2019
ms.author: mabolan
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: afdeb89b0bd026b20e0c940b05be60d4d3238b81
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2019
ms.locfileid: "73540221"
---
# <a name="install-and-configure-the-expense-report-sample-for-canvas-apps-in-powerapps"></a>PowerApps でキャンバス アプリ用の Expense Report サンプルをインストールして構成する

Expense Report サンプルをインストールして構成する詳細な手順を示します。 また、[こちら](https://aka.ms/previewmyexpenses)からサンプル アプリをプレビューすることもできます。

この手順の推定所要時間: **10 - 15 分**

> [!TIP]
> Expense Report サンプル アプリの使い方のデモについては、[こちらのビデオ](https://youtu.be/kJXZPILfbwU)をご覧ください。 

経費報告書を送信から承認に追跡します。 明細項目を個々の経費として集計し、準備ができたら承認を得るために送信します。 このアプリをお使いの環境に合わせるには、少し設定が必要です。

![Expense Report PowerApp の開始画面](./media/expense-report-install/expense-report-powerapp.png)

> [!TIP]
> Expense Report サンプルの使い方については、[このビデオ](https://youtu.be/kJXZPILfbwU)をご覧ください。

## <a name="prerequisites"></a>前提条件

- PowerApps に[サインアップ](../signup-for-powerapps.md)。

## <a name="create-the-expenses-list"></a>Expenses (経費) リストを作成する

このリストは経費レポートを格納します。

1. Web ブラウザーを開き、 https://admin.microsoft.com に移動します。
2. リストを作成するアクセス許可を持つアカウントでログインします。
3. Expenses (経費) リストを作成するサイト コレクションに移動します。
4. Web ページの右上にある歯車アイコンをクリックします。
5. **[アプリの追加]** をクリックします。
6. **[アプリの検索]** ボックスに、「**Custom (カスタム)** 」と入力します。
7. **検索アイコン**をクリックします。
8. **[カスタム リスト]** アプリをクリックします。
9. **[名前]** ボックスに「**Expenses**」と入力します。

    > [!IMPORTANT]
    > リストに別の名前を使う場合は、書き留めておいてください。以降のインストールと構成のプロセスで、Expenses となっているすべての箇所を置き換える必要があります。

10. **[作成]** をクリックします。

### <a name="create-cost-center-column"></a>コスト センター列を作成する

1. **Expenses (経費)** リストをクリックします。
2. Web ページの右上にある歯車アイコンをクリックします。
3. **[リストの設定]** をクリックします。
4. **[列の作成]** をクリックします。
5. **[列名]** ボックスに「**コスト センター**」と入力します。
6. **[type of information in this column is]\(この列の情報の種類\)** ラジオ ボタン リストで、 **[選択肢]** を選択します。
7. **[Type each choice on a separate line]\(それぞれの行に選択肢を入力してください\)** ボックスに、次の値をそれぞれ別の行に入力します。 
    - エクスプローラー
    - Contoso
8. **[既定値]** ボックスに、「**Microsoft**」と入力します。
9. **[OK]** をクリックします。

### <a name="create-comments-column"></a>Comments (コメント) 列を作成する

1. **[列の作成]** をクリックします。
2. **[列名]** ボックスに「**Comments (コメント)** 」と入力します。
3. **[type of information in this column is]\(この列の情報の種類\)** ラジオ ボタン リストで、 **[複数行テキスト]** を選択します。
4. **[OK]** をクリックします。

### <a name="create-status-column"></a>Status (状態) 列を作成する

1. **Expenses (経費)** リストをクリックします。
2. Web ページの右上にある**歯車アイコン**をクリックします。
3. **[リストの設定]** をクリックします。
4. **[列の作成]** をクリックします。
5. **[列名]** ボックスに「**Status (状態)** 」と入力します。
6. **[type of information in this column is]\(この列の情報の種類\)** ラジオ ボタン リストで、 **[選択肢]** を選択します。
7. **[Type each choice on a separate line]\(それぞれの行に選択肢を入力してください\)** ボックスに、次の値をそれぞれ別の行に入力します。 
    - 開き
    - 行わ
    - Approved
8. **[既定値]** ボックスに、「**オープン**」と入力します。
9. **[OK]** をクリックします。

### <a name="create-approvername-column"></a>ApproverName (承認者名) 列を作成する

1. **[列の作成]** をクリックします。
2. **[列名]** ボックスに「**ApproverName (承認者名)** 」と入力します。
3. **[type of information in this column is]\(この列の情報の種類\)** ラジオ ボタン リストで、 **[ユーザーまたはグループ]** を選択します。
4. **[Require that this column contains information]\(この列への情報の入力を必須にする\)** ラジオ ボタン リストで、 **[はい]** を選択します。
5. **[OK]** をクリックします。

### <a name="create-datesubmitted-column"></a>DateSubmitted (提出日) 列を作成する

1. **[列の作成]** をクリックします。
2. **[列名]** ボックスに「**DateSubmitted (提出日)** 」と入力します。
3. **[type of information in this column is]\(この列の情報の種類\)** ラジオ ボタン リストで、 **[日付と時刻]** を選択します。
4. **[Require that this column contains information]\(この列への情報の入力を必須にする\)** ラジオ ボタン リストで、 **[はい]** を選択します。
5. **[OK]** をクリックします。

### <a name="create-startdate-column"></a>StartDate (開始日) 列を作成する

1. **[列の作成]** をクリックします。
2. **[列名]** ボックスに「**StartDate (開始日)** 」と入力します。
3. **[type of information in this column is]\(この列の情報の種類\)** ラジオ ボタン リストで、 **[日付と時刻]** を選択します。
4. **[Require that this column contains information]\(この列への情報の入力を必須にする\)** ラジオ ボタン リストで、 **[はい]** を選択します。
5. **[OK]** をクリックします。

### <a name="create-enddate-column"></a>EndDate (終了日) 列を作成する

1. **[列の作成]** をクリックします。
2. **[列名]** ボックスに「**EndDate (終了日)** 」と入力します。
3. **[type of information in this column is]\(この列の情報の種類\)** ラジオ ボタン リストで、 **[日付と時刻]** を選択します。
4. **[Require that this column contains information]\(この列への情報の入力を必須にする\)** ラジオ ボタン リストで、 **[はい]** を選択します。
5. **[OK]** をクリックします。

## <a name="create-the-lineitems-list"></a>LineItems (明細項目) リストを作成する

このリストは、各経費レポートに関連付けられている明細項目を格納します。

1. Expense (明細項目) リストを作成したサイト コレクションに移動します。
2. Web ページの右上にある歯車アイコンをクリックします。
3. **[アプリの追加]** をクリックします。
4. **[アプリの検索]** ボックスに、「**Custom (カスタム)** 」と入力します。
5. **検索アイコン**をクリックします。
6. **[カスタム リスト]** アプリをクリックします。
7. **[名前]** ボックスに「**LineItems**」と入力します。

    > [!IMPORTANT] 
    > リストに別の名前を使う場合は、書き留めておいてください。以降のインストールと構成のプロセスで、LineItems となっているすべての箇所を置き換える必要があります。

8. **[作成]** をクリックします。
 
### <a name="create-category-column"></a>Category (カテゴリ) 列を作成する

1. **LineItems (明細項目)** リストをクリックします。
2. Web ページの右上にある歯車アイコンをクリックします。
3. **[リストの設定]** をクリックします。
4. **[列の作成]** をクリックします。
5. **[列名]** ボックスに「**Category (カテゴリ)** 」と入力します。
6. **[type of information in this column is]\(この列の情報の種類\)** ラジオ ボタン リストで、 **[選択肢]** を選択します。
7. **[Type each choice on a separate line]\(それぞれの行に選択肢を入力してください\)** ボックスに、次の値をそれぞれ別の行に入力します。 
    - 食べ物と飲み物
    - 輸送
    - ビジネス ニーズ
8. **[既定値]** ボックスに、「**食べ物と飲み物**」と入力します。
9. **[OK]** をクリックします。

### <a name="create-cost-column"></a>Cost (コスト) 列を作成する

1. **[列の作成]** をクリックします。
2. **[列名]** ボックスに「**Cost (コスト)** 」と入力します。
3. **[type of information in this column is]\(この列の情報の種類\)** ラジオ ボタン リストで、 **[Number (1, 10, 100)]\(数値 (1、1.0、100)\)** を選択します。
4. **[Require that this column contains information]\(この列への情報の入力を必須にする\)** ラジオ ボタン リストで、 **[はい]** を選択します。
5. **[OK]** をクリックします。

### <a name="create-date-column"></a>Date (日付) 列を作成する

1. **[列の作成]** をクリックします。
2. **[列名]** ボックスに「**Date (日付)** 」と入力します。
3. **[type of information in this column is]\(この列の情報の種類\)** ラジオ ボタン リストで、 **[日付と時刻]** を選択します。
4. **[Require that this column contains information]\(この列への情報の入力を必須にする\)** ラジオ ボタン リストで、 **[はい]** を選択します。
5. **[OK]** をクリックします。

### <a name="create-description-column"></a>Description (説明) 列を作成する

1. **[列の作成]** をクリックします。
2. **[列名]** ボックスに「**Description (説明)** 」と入力します。
3. **[type of information in this column is]\(この列の情報の種類\)** ラジオ ボタン リストで、 **[複数行テキスト]** を選択します。
4. **[Require that this column contains information]\(この列への情報の入力を必須にする\)** ラジオ ボタン リストで、 **[はい]** を選択します。
5. **[Specify the type of text to allow]\(使用可能なテキストの種類を指定してください\)** ラジオ ボタン リストで、 **[書式なしテキスト]** を選択します。
6. **[OK]** をクリックします。

### <a name="create-reportid-column"></a>ReportID (レポート ID) 列を作成する

1. **[列の作成]** をクリックします。
2. **[列名]** ボックスに「**ReportID (レポート ID)** 」と入力します。
3. **[type of information in this column is]\(この列の情報の種類\)** ラジオ ボタン リストで、 **[参照 (このサイトにある既存の情報)]** を選択します。
4. **[Require that this column contains information]\(この列への情報の入力を必須にする\)** ラジオ ボタン リストで、 **[はい]** を選択します。
5. **[情報の取得先]** ドロップダウン リストで、作成した **Expense (経費)** リストを選びます。
6. **[この列]** ドロップダウン リストで、**ID** を選びます。
7. **[OK]** をクリックします。

### <a name="edit-title-column"></a>"タイトル" 列を編集する

1. **[タイトル]** 列のリンクをクリックします。
2. **[Require that this column contains information]\(この列への情報の入力を必須にする\)** ラジオ ボタン リストで、 **[いいえ]** を選択します。
3. **[OK]** をクリックします。

## <a name="download-the-expense-report-app"></a>Expense Report アプリをダウンロードする

1. Web ブラウザーで次のリンクに移動します。

    [https://pappsfeprodwestuscontent.blob.core.windows.net/sampleapps/myexpenses/docs/MyExpenses(SP_List).zip](https://pappsfeprodwestuscontent.blob.core.windows.net/sampleapps/myexpenses/docs/MyExpenses(SP_List).zip)

2. Expense Report PowerApps サンプル パッケージをダウンロードして、お使いのコンピューターに保存します。

## <a name="create-connections"></a>接続を作成する

1.  Web ブラウザーで、 [make.powerapps.com](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)に移動します。
2.  サインアップに使用したものと同じ資格情報でサインインします。
3.  左側のメニューで **[接続]** を選択します。

### <a name="create-an-approvals-connection"></a>承認接続を作成する

1.  **[+ 新しい接続]** をクリックします。
2.  **[検索]** ボックスに、「**承認**」と入力します。
3.  一覧で "**承認**" を選びます。
4.  **[作成]** をクリックします。
    
### <a name="create-an-office-365-outlook-connection"></a>Office 365 Outlook 接続を作成する

1.  **[+ 新しい接続]** をクリックします。
2.  **[検索]** ボックスに、「**Office 365 Outlook**」と入力します。
3.  一覧で **Office 365 Outlook** を選びます。
4.  **[作成]** をクリックします。
5.  ポップアップ ウィンドウで、ログインに使ったアカウントを選びます。

### <a name="create-a-sharepoint-connection"></a>SharePoint 接続を作成する

1.  **[+ 新しい接続]** をクリックします。
2.  **[検索]** ボックスに、「**SharePoint**」と入力します。
3.  一覧で **SharePoint** を選びます。
4.  **[作成]** をクリックします。
5.  ポップアップ ウィンドウで、ログインに使ったアカウントを選びます。

## <a name="import-the-app"></a>アプリをインポートする

1. Web ブラウザーで、 https://make.powerapps.com に移動します。
1. サインアップに使用したものと同じ資格情報でサインインします。
1. 左側のナビゲーション バーで、 **[アプリ]** 、 **[パッケージのインポート (プレビュー)]** の順に選択します。

    ![パッケージ インポート画面](./media/expense-report-install/import-package.png)

1. **[アップロード]** を選択し、先ほどダウンロードしたパッケージを選択します。
1. **[アプリ]** および **[フロー]** リソースの種類で、 **[インポートの設定]** を **[新しく作成する]** に設定します。
1. **SharePoint** と **Outlook** の接続で、 **[インポートの設定]** を **[インポート時に選択する]** に設定します。

    ![インポート設定画面](./media/expense-report-install/import-settings.png)

1. **SharePoint 接続**の赤いアイコンを選択します。
1. 接続の一覧で、自分のユーザー名の項目を選択します。

    ![インポート設定画面](./media/expense-report-install/import-settings-sharepoint.png)

1. **[保存]** を選択します。
1. **承認接続**の赤いアイコンを選択します。
1. 接続の一覧で、自分のユーザー名の項目を選択します。

    ![インポート設定画面](./media/expense-report-install/import-settings-approvals.png)

1. **[保存]** を選択します。
1. **Office 365 Outlook 接続**の赤いアイコンを選択します。
1. 接続の一覧で、自分のユーザー名の項目を選択します。

    ![インポート設定画面](./media/expense-report-install/import-settings-office365outlook.png)

1. **[保存]** を選択します。

    > [!TIP] 
    > 完了すると次のようになります。

    ![インポート設定画面](./media/expense-report-install/import-settings-done.png)

1. **[インポート]** を選択して、プロセスが完了するまで待ちます。

    ![インポート設定画面](./media/expense-report-install/import-done.png)

## <a name="configure-the-app-to-use-the-sharepoint-lists"></a>SharePoint リストを使用するようにアプリを構成する

1. Web ブラウザーで **[アプリ]** を選択します。
2. Expense Report アプリの隣の省略記号 (...) を選択します。
3. **[Web で編集]**  >  **[許可]** の順に選択します。

### <a name="delete-connections"></a>接続を削除する
1. **[ビュー]** タブで **[データソース]** を選択します。
1. **[データ]** ウィンドウで、 **[Expenses (経費)]** の隣の省略記号 (...) を選択してから、 **[削除]** を選択します。
1. 前の手順を繰り返して、 **[LineItems (明細項目)]** データ ソースを削除します。

### <a name="expenses-list"></a>Expenses (経費) リスト

1. **[ビュー]** タブで **[データソース]** を選択します。
1. **[データ]** ウィンドウで、 **[データ ソースの追加]**  >  **[新しい接続]**  >  **[SharePoint]**  >  **[作成]** の順に選択します。
1. **[最近利用したサイト]** 一覧で、Expenses (経費) リストを作成した SharePoint サイトを選びます。

    > [!TIP] 
    > サイトが一覧に表示されない場合は、テキスト ボックスに SharePoint サイトの URL を入力するか貼り付けて、 **[移動]** を選択します。

1. 一覧の先頭にある **[検索]** ボックスに、「**Expenses**」と入力するか貼り付けます。
1. **[Expenses (経費)]** の隣のチェックボックスをオンにし、 **[接続]** を選択します。

### <a name="lineitems-list"></a>LineItems (明細項目) リスト

1. **[ビュー]** タブで **[データソース]** を選択します。
1. **[データ]** ウィンドウで、 **[SharePoint]** を選択します。
1. **[最近利用したサイト]** 一覧で、LineItems (明細項目) リストを作成した SharePoint サイトを選びます。

    > [!TIP] 
    > サイトが一覧に表示されない場合は、テキスト ボックスに SharePoint サイトの URL を入力するか貼り付けて、 **[移動]** を選択します。

1. 一覧の先頭にある **[検索]** ボックスに、「**LineItems**」と入力するか貼り付けます。
1. **[LineItems (明細項目)]** の隣のチェックボックスをオンにし、 **[接続]** を選択します。
1. **[ファイル]**  >  **[保存]**  >  **[発行]**  >  **[このバージョンの発行]** の順に選択します。

## <a name="modify-the-flow"></a>フローを変更する

1. 左側のナビゲーション バーで **[フロー]** を選びます。
1. サインインを求められたら、サインアップに使用したものと同じ資格情報を入力します。
1. 画面の上部で、 **[マイ フロー]** を選択します。
1. **[ApproveExpense (経費の承認)]** フローの隣の鉛筆アイコンを選択します。

    ![フロー編集画面](./media/expense-report-install/edit-flow.png)

1. **Get items** アクションを展開します。 
1. SharePoint で作成した Expense (経費) リストと一致するように、 **[サイト アドレス]** と **[リスト名]** を変更します。

    ![フロー編集画面](./media/expense-report-install/edit-flow-getitems.png)

    > [!TIP] 
    > 手入力する必要はありません。ドロップダウン リストで選択できます。

1. **Condition** を展開します。
1. **If yes** セクションを展開します。
1. **Change item status to Approved** アクションを展開します。
1. SharePoint で作成した Expense (経費) リストと一致するように、 **[サイト アドレス]** と **[リスト名]** を変更します。

    ![フロー編集画面](./media/expense-report-install/edit-flow-condition-ifyes.png) 

    > [!TIP] 
    > 手入力する必要はありません。ドロップダウン リストで選択できます。

1. **If no** セクションを展開します。
1. **Change item status to Open** アクションを展開します。
1. SharePoint で作成した Expense (経費) リストと一致するように、 **[サイト アドレス]** と **[リスト名]** を変更します。 

    ![フロー編集画面](./media/expense-report-install/edit-flow-condition-ifno.png)

    > [!TIP] 
    > 手入力する必要はありません。ドロップダウン リストで選択できます。

14. **[フローの更新]** を選択します。

## <a name="play-the-app"></a>アプリを再生する

1. Web ブラウザーで **[アプリ]** を選択します。
1. Expense Report アプリの隣の省略記号 (...) を選択し、 **[Open]\(開く\)** を選択します。

## <a name="next-steps"></a>次の手順
- [SharePoint リスト フォームをカスタマイズ](https://docs.microsoft.com/powerapps/maker/canvas-apps/customize-list-form)
- [コントロールの追加と構成](https://docs.microsoft.com/powerapps/maker/canvas-apps/add-configure-controls)
- [SharePoint リストまたはライブラリのアクセス許可の編集と管理](https://support.office.com/article/edit-and-manage-permissions-for-a-sharepoint-list-or-library-02d770f3-59eb-4910-a608-5f84cc297782)
