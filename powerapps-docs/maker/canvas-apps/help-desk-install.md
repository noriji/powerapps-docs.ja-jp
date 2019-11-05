---
title: キャンバス アプリ用の Help Desk サンプルをインストールして構成する | Microsoft Docs
description: PowerApps でキャンバス アプリ用の Help Desk サンプルをインストールして構成する詳細な手順を示します。
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
ms.openlocfilehash: dd5d8b8e6757b18feb5da03c503b19e689ca3efe
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2019
ms.locfileid: "73541244"
---
# <a name="install-and-configure-the-help-desk-sample-in-powerapps"></a>PowerApps で Help Desk サンプルをインストールして構成する

PowerApps でキャンバス アプリ用の Help Desk サンプルをインストールして構成する詳細な手順を示します。

この手順の推定所要時間: **10 - 15 分**

> [!TIP]
> この手順のデモについては、こちらの[ビデオ](https://youtu.be/z4cdtD6hB_4)をご覧ください。

## <a name="overview-of-the-sample"></a>サンプルの概要

ヘルプデスクは、エンドユーザーをサポート担当者に接続するためのユーザーフレンドリなエクスペリエンスを提供します。 最も重要な質問に対する回答をすばやく検索し、開いているチケットの進行状況を追跡し、以前の要求の詳細を確認します。 このアプリをお使いの環境に合わせるには、少し設定が必要です。

![Help Desk PowerApp の開始画面](./media/help-desk-install/Login-screen.png)

> [!TIP]
> Help Desk PowerApp サンプルの使い方については、こちらの[ビデオ](https://youtu.be/sl5fXwwnvzI)をご覧ください。

## <a name="prerequisites"></a>前提条件

- PowerApps に[サインアップ](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)。
- 有効な SharePoint Online ライセンスと、リストを作成するアクセス許可を持っている必要があります。

## <a name="create-the-helpdesk-sharepoint-list"></a>HelpDesk (ヘルプデスク) SharePoint リストを作成する

このリストは、Help Desk のチケットを格納します。

1. Web ブラウザーを開き、 https://admin.microsoft.com に移動します。
2. SharePoint リストを作成するアクセス許可を持つアカウントでログインします。
3. HelpDesk (ヘルプデスク) リストを作成するサイト コレクションに移動します。
4. Web ページの右上にある**歯車アイコン**をクリックします。
5. **[アプリの追加]** をクリックします。
6. **[アプリの検索]** ボックスに、「**Custom (カスタム)** 」と入力します。
7. **検索アイコン**をクリックします。
8. **[カスタム リスト]** アプリをクリックします。
9. **[名前]** ボックスに、「**HelpDesk (ヘルプデスク)** 」と入力します。

    > [!IMPORTANT]
    > リストに別の名前を使う場合は、書き留めておいてください。以降のインストールと構成のプロセスで、HelpDesk (ヘルプデスク) となっているすべての箇所を置き換える必要があります。

10. **[作成]** をクリックします。

### <a name="create-description-column"></a>Description (説明) 列を作成する

1. HelpDesk (ヘルプデスク) リストの横にある省略記号を選択して、 **[設定]** をクリックします。
2. **[列の作成]** をクリックします。
3. **[列名]** ボックスに「**Description (説明)** 」と入力します。
4. **[type of information in this column is]\(この列の情報の種類\)** ラジオ ボタン リストで、 **[複数行テキスト]** を選択します。
5. **[Require that this column contains information]\(この列への情報の入力を必須にする\)** ラジオ ボタン リストで、 **[はい]** を選択します。
6. **[Specify the type of text to allow]\(使用可能なテキストの種類を指定してください\)** ラジオ ボタン リストで、 **[書式なしテキスト]** を選択します。
7. **[OK]** をクリックします。

### <a name="create-category-column"></a>Category (カテゴリ) 列を作成する

1. **[列の作成]** をクリックします。
2. **[列名]** ボックスに「**Category (カテゴリ)** 」と入力します。
3. **[type of information in this column is]\(この列の情報の種類\)** ラジオ ボタン リストで、 **[選択肢]** を選択します。
4. **[Type each choice on a separate line]\(それぞれの行に選択肢を入力してください\)** ボックスに、次の値をそれぞれ別の行に入力します。 
    - ラップトップ/PC 機器の問題
    - ラップトップ/PC ソフトウェアの問題
5. **[固有の値を適用する]** ラジオ ボタン リストで、 **[いいえ]** を選択します。
6. **[選択肢の表示形式]** ラジオ ボタン リストで、 **[ドロップダウン メニュー]** を選択します。
7. **[既定値]** ボックスに、「**ラップトップ/PC 機器の問題**」と入力します。
8. **[OK]** をクリックします。

### <a name="create-percentcomplete-column"></a>PercentComplete (完了率) 列を作成する

1. **[列の作成]** をクリックします。
2. **[列名]** ボックスに「**PercentComplete (完了率)** 」と入力します。
3. **[type of information in this column is]\(この列の情報の種類\)** ラジオ ボタン リストで、 **[Number (1, 10, 100)]\(数値 (1、1.0、100)\)** を選択します。
4. **[Require that this column contains information]\(この列への情報の入力を必須にする\)** ラジオ ボタン リストで、 **[いいえ]** を選択します。
5. **[OK]** をクリックします。

### <a name="create-priority-column"></a>Priority (優先度) 列を作成する

1. **[列の作成]** をクリックします。
2. **[列名]** ボックスに「**Priority (優先度)** 」と入力します。
3. **[type of information in this column is]\(この列の情報の種類\)** ラジオ ボタン リストで、 **[選択肢]** を選択します。
4. **[Type each choice on a separate line]\(それぞれの行に選択肢を入力してください\)** ボックスに、次の値をそれぞれ別の行に入力します。 
    - 高
    - 程度
    - 低
5. **[固有の値を適用する]** ラジオ ボタン リストで、 **[いいえ]** を選択します。
6. **[選択肢の表示形式]** ラジオ ボタン リストで、 **[ドロップダウン メニュー]** を選択します。
7. **[既定値]** ボックスに、「**低**」と入力します。
8. **[OK]** をクリックします。

### <a name="create-taskstatus-column"></a>タスク ステータス列を作成します。

1. **[列の作成]** をクリックします。
2. **[列名]** ボックスに「**TaskStatus (タスク ステータス)** 」と入力します。
3. **[type of information in this column is]\(この列の情報の種類\)** ラジオ ボタン リストで、 **[選択肢]** を選択します。
4. **[Type each choice on a separate line]\(それぞれの行に選択肢を入力してください\)** ボックスに、次の値をそれぞれ別の行に入力します。 
    - 未開始
    - 進行中
    - 完了
    - 延期
    - CSR 待ち
5. **[固有の値を適用する]** ラジオ ボタン リストで、 **[いいえ]** を選択します。
6. **[選択肢の表示形式]** ラジオ ボタン リストで、 **[ドロップダウン メニュー]** を選択します。
7. **[既定値]** ボックスに、「**未開始**」と入力します。
8. **[OK]** をクリックします。

### <a name="create-assignedto-column"></a>AssignedTo (担当者) 列を作成する

1. **[列の作成]** をクリックします。
2. **[列名]** ボックスに「**AssignedTo (担当者)** 」と入力します。
3. **[type of information in this column is]\(この列の情報の種類\)** ラジオ ボタン リストで、 **[ユーザーまたはグループ]** を選択します。
4. **[Require that this column contains information]\(この列への情報の入力を必須にする\)** ラジオ ボタン リストで、 **[いいえ]** を選択します。
5. **[複数選択できるようにする]** ラジオ ボタン リストで、 **[いいえ]** を選択します。
6. **[OK]** をクリックします。

### <a name="edit-title-column"></a>"タイトル" 列を編集する

1. **[タイトル]** 列のリンクをクリックします。
2. **[Require that this column contains information]\(この列への情報の入力を必須にする\)** ラジオ ボタン リストで、 **[いいえ]** を選択します。
3. **[OK]** をクリックします。

## <a name="download-the-app"></a>アプリをダウンロードする

1.  PowerApps パッケージを[ダウンロード](https://pappsfeprodwestuscontent.blob.core.windows.net/sampleapps/helpdesk/docs/HelpDesk(SP_List).zip)し、コンピューターに保存します。

## <a name="create-connections"></a>接続を作成する

1.  Web ブラウザーで、 [make.powerapps.com](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)に移動します。
2.  サインアップに使用したものと同じ資格情報でサインインします。
3.  左側のメニューで **[データ]** 、 **[接続]** の順に選択します。
    
### <a name="create-office-365-outlook-connection"></a>Office 365 Outlook 接続を作成する

1.  **[+ 新しい接続]** をクリックします。
2.  **[検索]** ボックスに、「**Office 365 Outlook**」と入力します。
3.  一覧で **Office 365 Outlook** を選びます。
4.  **[作成]** をクリックします。
5.  ポップアップ ウィンドウで、ログインに使ったアカウントを選びます。

### <a name="create-sharepoint-connection"></a>SharePoint 接続を作成する

1.  **[+ 新しい接続]** をクリックします。
2.  **[検索]** ボックスに、「**SharePoint**」と入力します。
3.  一覧で **SharePoint** を選びます。
4.  **[作成]** をクリックします。
5.  ポップアップ ウィンドウで、ログインに使ったアカウントを選びます。

### <a name="create-office-365-users-connection"></a>Office 365 ユーザー接続を作成する

1.  **[+ 新しい接続]** をクリックします。
2.  **[検索]** ボックスに、「**Office 365 ユーザー**」と入力します。
3.  一覧で **Office 365 ユーザー**を選びます。
4.  **[作成]** をクリックします。
5.  ポップアップ ウィンドウで、ログインに使ったアカウントを選びます。

## <a name="import-the-app"></a>アプリをインポートする

1. Web ブラウザーで、 https://make.powerapps.com に移動します。
2. サインアップに使用したものと同じ資格情報でサインインします。
3. 左側のメニューで **[アプリ]** を選択します。 
4. **[パッケージのインポート (プレビュー)]** をクリックします。
    
   ![パッケージ インポート画面](./media/help-desk-install/import-package.png)

5. **[アップロード]** ボタンをクリックして、前のステップでダウンロードした PowerApp パッケージを選びます。
6. **[アプリ]** および **[フロー]** リソースの種類で、 **[インポートの設定]** を **[新しく作成する]** に設定します。
7. **SharePoint** と **Outlook** の接続で、 **[インポートの設定]** を **[インポート時に選択する]** に設定します。
    
   ![インポート設定画面](./media/help-desk-install/import-settings.png)

8. **SharePoint 接続**の**赤いアイコン**をクリックします。
9. 接続の一覧で、自分のユーザー名の項目をクリックします。

   ![インポート設定画面](./media/help-desk-install/import-settings-sharepoint.png)

10. **[保存]** をクリックします。
11. **Office 365 Outlook 接続**の**赤いアイコン**をクリックします。
12. 接続の一覧で、自分のユーザー名の項目をクリックします。

    ![インポート設定画面](./media/help-desk-install/import-settings-office365outlook.png)

13. **[保存]** をクリックします。

    > [!TIP] 
    > 完了すると次のようになります。

    ![インポート設定画面](./media/help-desk-install/import-settings-done.png)

14. **[インポート]** をクリックして、プロセスが完了するまで待ちます。

    ![インポート設定画面](./media/help-desk-install/import-done.png)

## <a name="configure-the-app-to-use-the-sharepoint-list"></a>SharePoint リストを使用するようにアプリを構成する

1. [次の手順] で、 **[アプリを開く]** をクリックします。
2. アクセスの許可を求められたら、 **[許可]** をクリックします。

### <a name="delete-connections"></a>接続を削除する

1. **[ビュー]** タブで **[データソース]** を選択します。
1. **[データ]** ウィンドウで、 **[ヘルプデスク]** の横にある省略記号 (...) を選択し、 **[削除]** を選択します。

### <a name="helpdesk-list"></a>HelpDesk (ヘルプデスク) リスト

1. **[ビュー]** タブで **[データソース]** を選択します。
1. **[データ]** ウィンドウで、 **[データ ソースの追加]**  >  **[新しい接続]**  >  **[SharePoint]**  >  **[作成]** の順に選択します。
1. **[最近利用したサイト]** 一覧で、HelpDesk (ヘルプデスク) リストを作成した SharePoint サイトを選びます。

    > [!TIP] 
    > サイトが一覧に表示されない場合は、テキスト ボックスに SharePoint サイトの URL を入力するか貼り付けて、 **[移動]** を選択します。

1. 一覧の上部にある**検索**ボックスに、**ヘルプデスク**に入力するか貼り付けます。
1. **[ヘルプデスク]** の横にあるチェックボックスをオンにし、 **[接続]** を選択します。

### <a name="update-admin-list"></a>管理者一覧を更新する

1. **LoginScreen** を選びます。
2. ドロップダウンで **OnStart** を選びます。
3. 式ウィンドウを展開し、**AdminList** コレクションを探します。
4. <strong>user@microsoft.com</strong> を実際のヘルプデスク管理者に置き換えます。

    ![管理者一覧を更新する](./media/help-desk-install/Change-admin.png)
    
   > [!TIP]
   > 複数の管理者がいる場合は、コンマを使用して管理者の一覧を区切ります。 例: "admin1@microsoft.com","admin2@microsoft.com"。
   > AdminList のアドレスが PowerApps で必要な形式と一致していることを確認するには、[表示] > [変数] > [グローバル] > [MyProfile] の順に選び、"Mail" 列のメール形式を調べます。

1. **[ファイル]**  >  **[保存]**  >  **[発行]**  >  **[このバージョンの発行]** の順に選択します。

## <a name="modify-the-flow"></a>フローを変更する

1.  左側のメニューで **[フロー]** をクリックします。
2.  サインインを求められたら、サインアップに使用したものと同じ資格情報でサインインします。
3.  上部のメニューで **[マイ フロー]** を選択します。
4.  **Helpデスクフロー**フローの横にある鉛筆アイコンをクリックします。 
 
    ![フロー編集画面](./media/help-desk-install/edit-flow.png)

5.  **Get items** アクションを展開します。 
6.  作成した HelpDesk (ヘルプデスク) SharePoint リストと一致するように、 **[サイト アドレス]** と **[リスト名]** を変更します。
    
    ![フロー編集画面](./media/help-desk-install/edit-flow-getitems.png)

    > [!TIP] 
    > 手入力する必要はありません。ドロップダウン リストで選択できます。

7.  **Switch** を展開します。
8.  **未開始**ケースを展開します。
9.  **Case not started** アクションを展開します。
10. **[宛先]** をヘルプデスク管理者のメール アドレスに変更します。

    ![フロー編集画面](./media/help-desk-install/edit-flow-condition-send-email.png) 

11. **[フローの更新]** をクリックします。

## <a name="play-the-app"></a>アプリを再生する

1. Web ブラウザーで **[アプリ]** をクリックします。
2. ヘルプデスクアプリの横にある省略記号 ([...]) をクリックします。
3. **[開く]** をクリックします。 

> [!TIP]
> Help Desk PowerApp サンプルの使い方については、こちらの[ビデオ](https://youtu.be/sl5fXwwnvzI)をご覧ください。

## <a name="next-steps"></a>次の手順
- [SharePoint リスト フォームをカスタマイズ](https://docs.microsoft.com/powerapps/maker/canvas-apps/customize-list-form)
- [コントロールの追加と構成](https://docs.microsoft.com/powerapps/maker/canvas-apps/add-configure-controls)
- [SharePoint リストまたはライブラリのアクセス許可の編集と管理](https://support.office.com/article/edit-and-manage-permissions-for-a-sharepoint-list-or-library-02d770f3-59eb-4910-a608-5f84cc297782)
