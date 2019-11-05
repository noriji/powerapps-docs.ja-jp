---
title: PowerApps でポータルを作成する |Microsoft Docs
description: PowerApps でポータルを作成する手順。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: b818db8fb72fe36fcc7ea049a4e5b4cfb17eb0d9
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2019
ms.locfileid: "73542653"
---
# <a name="create-a-common-data-service-starter-portal"></a>Common Data Service starter ポータルを作成する

PowerApps でポータルを構築する機能を使用すると、外部ユーザーと内部ユーザーの web サイトを作成して、Common Data Service に格納されているデータと対話できるようになります。

ポータルを作成すると、次のような利点があります。

- データは Common Data Service に格納されるため、SharePoint、Dynamics 365 のモデル駆動型アプリ、Salesforce などのデータソースの場合と同様に、PowerApps から接続を作成する必要はありません。 ポータルで表示または管理するエンティティを指定するだけです。

- Web ページにコンポーネントを追加して構成することで、WYSIWYG PowerApps ポータル Studio でポータルを設計できます。

ポータルは、新しい環境で作成することも、既存の環境に作成することもできます。

**[新しい環境の作成]** リンクを使用して新しい環境でポータルを作成することを選択した場合は、必要なポータル (エンティティ、データ、スターターポータルテンプレートなど) が環境の作成時にインストールされます。 この方法では、ポータルは数分でプロビジョニングされます。

ポータルを使用せずに既存の環境でポータルを作成することを選択した場合、前提条件が最初にインストールされ、その後ポータルが作成されます。 この方法では、ポータルのプロビジョニングに時間がかかることがあり、ポータルがプロビジョニングされると通知されます。

PowerApps で選択されている環境に基づいて、Dynamics 365 のモデル駆動型アプリを含む環境で、Common Data Service のスターターポータルまたはポータルを作成できます。

環境の使用に関する詳細:[環境と Microsoft PowerApps の](https://docs.microsoft.com/powerapps/maker/canvas-apps/working-with-environments)使用

利用可能なポータルテンプレートの詳細情報:[ポータルテンプレート](portal-templates.md)

ポータルを作成するには:

1.  [PowerApps にサインインします](https://make.powerapps.com)。  

2.  **[独自のアプリを作成する]** で、 **[ポータル]** を選択します。

3.  選択した環境にポータルの前提条件が含まれていない場合は、別の環境を選択するか、新しい環境を作成するかを提案する**空のウィンドウから、ポータル**にメッセージが表示されます。

    > [!div class=mx-imgBorder]
    > ![新しい環境メッセージの作成](media/create-portal-message.png "新しい環境メッセージの作成")

4.  現在の環境に進む場合は、次の手順で説明するように、ウィンドウに必要な情報を入力します。 新しい環境を作成する場合は、「[新しい環境を作成](#create-new-environment)する」を参照してください。

5.  ポータルの [**空**のウィンドウ] で、ポータルの名前と web サイトのアドレスを入力し、ドロップダウンリストから言語を選択します。 完了したら、 **[作成]** を選択します。

    > [!div class=mx-imgBorder]
    > ![新しいポータルの作成](media/create-new-portal.png "新しいポータルの作成")  

**[作成]** を選択すると、ポータルがプロビジョニングを開始し、[通知](#portal-provisioning-notifications)によってプロビジョニングの状態が表示されます。

ポータルの前提条件がインストールされていない環境でポータルを作成した場合は、プロビジョニングの状態もグリッドに表示されます。

> [!div class=mx-imgBorder]
> ![グリッド通知](media/provision-progress-notif.png "グリッド通知")

ポータルが正常にプロビジョニングされると、状態が更新され、ポータルがグリッドに表示されます。

> [!div class=mx-imgBorder]
> ![プロビジョニングされたポータル](media/recent-apps.png "プロビジョニングされたポータル")

PowerApps ポータル Studio でポータルを編集するには、「[ポータルを編集](manage-existing-portals.md#edit)する」を参照してください。

> [!NOTE]
> - 1つのテナントで最大5つのポータルを作成できます。 ただし、環境内で作成された各種類のポータルは1つだけです。
> - ポータルをプロビジョニングするための十分な特権がない場合は、エラーが表示されます。 ポータルを作成するには、Common Data Service のシステム管理者ロールが必要です。 また、ユーザーレコードの**クライアントアクセスライセンス (CAL) 情報**で、**アクセスモード**を **[読み取り/書き込み]** に設定する必要があります。
> - 古いポータルアドオンを購入し、アドオンを使用してポータルをプロビジョニングする場合は、 **Dynamics 365 管理センター**のページにアクセスする必要があります。 詳細情報:[古いポータルアドオンを使用してポータルをプロビジョニング](provision-portal-add-on.md)する
> - 以前のポータルアドオンを使用してポータルをプロビジョニングした場合でも、 [make.powerapps.com](https://make.powerapps.com)からカスタマイズして管理することができます。
> - [Make.powerapps.com](https://make.powerapps.com)からポータルをプロビジョニングしても、以前のポータルアドオンは使用されません。 また、これらのポータルは、 **Dynamics 365 管理センター**ページの **[アプリケーション]** タブには表示されません。
> - Common Data Service starter ポータルは、 **Dynamics 365 管理センター**ページから作成することはできません。
> - PowerApps ポータルは、フランス地域では使用できません。

## <a name="create-new-environment"></a>新しい環境の作成

**空のウィンドウからポータル**に用意されているオプションを使用して環境を作成するときは、次の手順に従います。

1.  **[新しい環境]** ウィンドウで、環境の名前を入力し、ドロップダウンリストから地域と環境の種類を選択します。 環境の作成後にリージョンを変更することはできません。 完了したら、 **[環境の作成]** を選択します。

    > [!div class=mx-imgBorder]
    > ![新しい環境の作成](media/create-new-environment.png "新しい環境の作成")  

2.  環境が作成されると、ダイアログボックスに確認メッセージが表示され、データベースを作成するように求められます。 **[データベースの作成]** を選択して、Common Data Service へのアクセスを有効にします。

    > [!NOTE]
    > データベースを作成するためのプロンプトが自動的に表示されない場合があります。 この場合は、新しい環境にアクセスし、[空] タイル**からポータル**をもう一度選択する必要があります。

    > [!div class=mx-imgBorder]
    > ![新しい環境が作成されました](media/new-environment-created.png "新しい環境が作成されました")  

3.  データベースの格納データの通貨と言語を選択します。 データベースの作成後に通貨や言語を変更することはできません。 完了したら、 **[データベースの作成]** を選択します。 データベースは、ポータルがプロビジョニングされた後にサンプルコンテンツをすばやく開始できるようにするスターターポータルを使用して作成されます。

    > [!NOTE]
    > **[スターターポータルを含める]** オプションは、ポータルの **[空白]** ウィンドウで指定されたオプションを使用して環境を作成する場合にのみ使用できます。 このオプションは、PowerApps 管理センターから環境を作成する場合は使用できません。

    > [!div class=mx-imgBorder]
    > ![新しいデータベースの作成](media/create-new-database.png "新しいデータベースの作成") 

    Common Data Service にデータベースを作成するのに数分かかる場合があります。 データベースが作成されると、PowerApps ホームページの環境の一覧で新しい環境が選択され、ポータル管理アプリが作成されます。 このアプリは実際のポータルではなく、事前構成アクティビティを実行できるモデル駆動型のコンパニオンアプリです。 これで、外部に接続する web サイトを設計するためのポータルの作成に進むことができます。

    > [!div class=mx-imgBorder]
    > ![ポータル管理アプリ](media/portal-mgmt-app.png "ポータル管理アプリ")

4. 環境とデータベースを作成したら、 **[独自のアプリ]** を作成する で **[ポータル]** を選択します。 

    > [!NOTE]
    > データベースが作成されていても、create database プロンプトがまだ表示されている場合は、[空] タイル**からポータル**を選択する前に、PowerApps ホームページを更新する必要があります。


## <a name="portal-provisioning-notifications"></a>ポータルプロビジョニングの通知

**[作成]** を選択すると、ポータルがプロビジョニングを開始し、通知によってプロビジョニングの状態が表示されます。

**トーストとしての通知**

**[作成]** を選択してポータルをプロビジョニングすると、次の通知が表示されます。

> [!div class=mx-imgBorder]
> ![トースト通知](media/toast-notif.png "トースト通知") 

**通知ウィンドウの通知**

プロビジョニング要求が正常に配置されると、**通知**ウィンドウに次の通知が表示されます。

プロビジョニング中に通知が表示されます

> [!div class=mx-imgBorder]
> ![ウィンドウ通知](media/pane-notif.png "ウィンドウ通知") 

プロビジョニングが正常に完了したことを示す通知が表示される

> [!div class=mx-imgBorder]
> ![プロビジョニングの成功通知](media/provision-complete-notif.png "プロビジョニングの成功通知") 

ポータルのプロビジョニングが失敗した場合、通知は同様に表示されます。
  
**電子メールによる通知**

プロビジョニング要求が正常に配置されると、ポータルを作成するユーザーに確認の電子メール通知が送信されます。 また、ポータルのプロビジョニングが完了した後に、電子メールがユーザーに送信されます。

## <a name="disable-portal-creation-in-a-tenant"></a>テナントでのポータルの作成を無効にする

グローバル管理者は、管理者以外がテナントでポータルを作成できないようにするには、PowerShell を使用して `disablePortalsCreationByNonAdminUsers` テナントレベルの設定を有効にします。 PowerShell コマンドレットを実行するには、最初に必要なモジュールをインストールする必要があります。 必要な PowerShell モジュールのインストールについては、「[インストール](https://docs.microsoft.com/power-platform/admin/powerapps-powershell#installation)」を参照してください。

モジュールをインストールしたら、PowerShell ウィンドウで次のコマンドを実行します (管理者として PowerShell を実行します)。

```
Set-TenantSettings -RequestBody @{ "disablePortalsCreationByNonAdminUsers" = $true }
```

管理者は、次のいずれかの Azure ロールを持っているユーザーです。

- 全体管理者
- Dynamics 365 サービス管理者
- 電源プラットフォームサービス管理者

上記の Azure ロールを所有していないユーザーは、管理者以外のユーザーと見なされます。

テナントでポータルの作成が無効になっていると、管理者以外の管理者には次のようなエラーが表示されます。

> [!div class=mx-imgBorder]
> ![ポータルの作成がブロックされたエラー](media/portal-create-blocked-error.png "ポータルの作成がブロックされたエラー")
