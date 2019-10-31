---
title: PowerApps でポータルの作成 | Microsoft Docs
description: PowerApps のポータルを作成するための手順。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: null
ms.date: 10/02/2019
ms.author: shjais
ms.reviewer: null
---

# <a name="create-a-common-data-service-starter-portal"></a>Common Data Service スターター ポータルの作成

[!include[cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

PowerApps でポータルを構築する機能を使用すると、外部および内部ユーザー用のWeb サイトを作成して、 Common Data Service に保存されたデータを操作することができます 。

これらは、ポータルを作成する利点です:

- データは Common Data Service に保存されているため、 SharePoint や Dynamics 365 モデル駆動型アプリ、Salesforce などのデータソースを使用する場合のように、 PowerApps から接続を作成する必要はありません。 ポータルで表示または管理するエンティティを指定するだけです。

- Web ページに追加して構成することにより、WYSIWIG ポータル デザイナーを介してポータルを設計できます。

新しい環境または既存の環境でポータルを作成できます。

**新しい環境を作成します** リンクを使用して、新しい環境でポータルを作成することを選択した場合、エンティティ、データ、スターター ポータル テンプレートなどの必須ポータルの前提条件が、環境の作成時に、インストールされます。 この方法では、ポータルは数分でプロビジョニングされます。

ポータルの前提条件がない既存の環境でポータルを作成する場合は、前提条件が最初にインストールされてから、ポータルが作成されます。 この方法では、ポータルのプロビジョニングに時間がかかることがあり、ポータルがプロビジョニングされると通知を受け取ります。

選択した環境に基づいて PowerApps で Common Data Service スターター ポータル、 または Dynamics 365 ポータルを作成できます。

環境に関する作業の詳細: [環境と Microsoft PowerApps に関する作業](https://docs.microsoft.com/en-us/powerapps/maker/canvas-apps/working-with-environments)

使用可能なポータル テンプレートの詳細: [ポータル テンプレート](portal-templates.md)

ポータルを作成するには:

1.  [PowerApps](http://web.powerapps.com) にサインインします。  

2.  **自分のアプリを作成する** で **空のポータル (プレビュー)** を選択します。

3.  選択した環境にポータルの前提条件が含まれていない場合、別環境を選択するか、または新しい環境を作成することを提案する **空のポータル (プレビュー)** ウィンドウにメッセージが表示されます。

    > [!div class=mx-imgBorder]
    > ![新しい環境メッセージの作成](media/create-portal-message.png "新しい環境メッセージの作成")

4.  現在の環境で続行することを選択した場合、次の手順で説明するように、ウィンドウに必要な情報を入力します。 新しい環境を作成するを選択する場合、 [新しい環境の作成](#create-new-environment) を参照してください。

5.  **空のポータル (プレビュー)** ウィンドウで、ポータルの名前およびWeb サイトのアドレスを入力し、ドロップダウン リストから言語を選択します。 完了したら、 **作成** を選択します。

    > [!div class=mx-imgBorder]
    > ![新しいポータルの作成](media/create-new-portal.png "新しいポータルの作成")  

**作成** を選択した後、ポータルはプロビジョニングを開始し、プロビジョニングの状態が [通知](#portal-provisioning-notifications) によって表示されます。

ポータルの前提条件がインストールされていない環境でポータルを作成した場合、プロビジョニングの状態もグリッドに表示されます:

> [!div class=mx-imgBorder]
> ![グリッド 通知](media/provision-progress-notif.png "グリッド 通知")

ポータルが正常にプロビジョニングされると、状態は更新され、ポータルはグリッドで表示されます:

> [!div class=mx-imgBorder]
> ![プロビジョニングされたポータル](media/recent-apps.png "プロビジョニングされたポータル")

ポータル デザイナー で ポータルを編集するには、 [ポータルの編集](manage-existing-portals.md#edit) を参照してください。

> [!NOTE]
> - テナントに最大 5 つポータルを作成できます。 ただし、環境内で作成した種類の 1 つのポータルである必要があります。
> - ポータルをプロビジョニングする十分な特権がない場合は、エラーが表示されます。 ポータルを作成するには、 Common Data Service に システム管理者または少なくともシステム カスタマイザーのロールが必要です。 ユーザー レコードの **クライアント アクセス ライセンス (CAL) 情報** で **アクセス モード** を **読み取り/書き込み** に設定する必要があります。

## <a name="create-new-environment"></a>新しい環境の作成

**空のポータル (プレビュー)** ウィンドウに用意されているオプションを使用して環境を作成する場合、次の手順に従います。

1.  **新しい環境** ウィンドウで、環境の名前を入力し、ドロップダウン リストのリージョンと環境の種類を選択します。 環境の作成後に、リージョンを変更することはできません。 終了したら、 **環境の作成** を選択します。

    > [!div class=mx-imgBorder]
    > ![新しい環境の作成](media/create-new-environment.png "新しい環境の作成")  

2.  環境が作成されると、ダイアログ ボックスに確認メッセージが表示され、データベースを作成するよう求められます。 **データベースの作成** を選択して、 Common Data Service へのアクセスを有効にします。

    > [!NOTE]
    > データベースを作成するためのプロンプトが自動的に表示されない場合があります。 この場合、新しい環境に移動し、再度、 **空のポータル** タイルを選択する必要があります。

    > [!div class=mx-imgBorder]
    > ![作成された新しい環境](media/new-environment-created.png "作成された新しい環境")  

3.  データベースに保存されたデータの通貨と言語を選択します。 データベースが作成されると、通貨や言語を変更できません。 終了したら、 **データベースの作成** を選択します。 データベースはスターター ポータルで作成されます。これにより、ポータルがプロビジョニングされるとサンプル コンテンツをすぐに開始できます。

    > [!NOTE]
    > **スターター ポータルを含む** オプションは、 **空のポータル (プレビュー)** ウィンドウに表示されるオプションを使用する環境を作成する場合にのみ使用できます。 このオプションは、 PowerApps 管理センターから環境を作成する場合、利用できません。

    > [!div class=mx-imgBorder]
    > ![新しいデータベースの作成](media/create-new-database.png "新しいデータベースの作成") 

    Common Data Service にデータベースを作成するには、数分かかる場合があります。 データベースを作成した後は、新しい環境は、 PowerApps ホーム ページの環境リストでが選択され、ポータル管理 アプリが作成されます。 このアプリは、実際のポータルではなく、高度な管理活動を実行可能にするモデル駆動型の付属アプリです。 外部接続型Web サイトをデザインするためのポータルの作成に進むことができます。

    > [!div class=mx-imgBorder]
    > ![ポータル管理アプリ](media/portal-mgmt-app.png "ポータル管理アプリ")

4. 環境とデータベースを作成後、 **自分のアプリを作成する** の **空のポータル (プレビュー)** を選択します。 

    > [!NOTE]
    > データベースが作成されても、データベース作成プロンプトが引き続き表示される場合は、 **空のポータル (プレビュー)** タイルを選択する前に、 PowerApps ホーム ページを更新する必要があります。


## <a name="portal-provisioning-notifications"></a>ポータル プロビジョニング 通知

**作成** を選択した後、ポータルはプロビジョニングを開始し、プロビジョニングの状態が通知によって表示されます。

**トーストとして通知**

次の通知は、ポータルをプロビジョニングするために **作成** を選択したときに表示されます。

> [!div class=mx-imgBorder]
> ![トースト通知](media/toast-notif.png "トースト通知") 

**通知ウィンドウの通知**

プロビジョニング要求が正常に配置されると、次の通知が **通知** ウィンドウに表示されます。

進行中のプロビジョニングに対して表示される通知

> [!div class=mx-imgBorder]
> ![ウィンドウ通知](media/pane-notif.png "ウィンドウ通知") 

正常完了したプロビジョニングに対して表示される通知

> [!div class=mx-imgBorder]
> ![プロビジョニング成功通知](media/provision-complete-notif.png "プロビジョニング成功通知") 

ポータル プロビジョニングが失敗した場合は、同様に通知が表示されます。
  
## <a name="disable-portal-creation-in-a-tenant"></a>テナントでポータル作成の無効化

全体管理者として、管理者以外のユーザーがテナントでポータルの作成をできないようにするには、PowerShellで `disablePortalsCreationByNonAdminUsers` のテナント レベル設定を有効にすること実行できます。 PowerShell コマンドレットを実行するには、最初に、必須モジュールをインストールする必要があります。 必須 PowerShell モジュールのインストールについては、 [インストール](https://docs.microsoft.com/en-us/power-platform/admin/powerapps-powershell#installation) を参照してください。

モジュールをインストールしたら、PowerShell ウィンドウで次のコマンドを実行します (PowerShellを管理者として実行)。

```
Set-TenantSettings -RequestBody @{ "disablePortalsCreationByNonAdminUsers" = $true }
```

管理者は、次の Azure ロールの 1 つを持つユーザーです:

-  グローバル管理者
- Dynamics 365 サービス管理者
- Power Platform サービス管理者

前述 Azure ロールのいずれにも持っていないユーザーは、管理者以外のユーザーと見なされます。

ポータルの作成がテナントで無効とされると、管理者以外のユーザーには、次のエラーが表示されます:

> [!div class=mx-imgBorder]
> ![ポータル作成ブロックエラー](media/portal-create-blocked-error.png "ポータル作成ブロックエラー")

