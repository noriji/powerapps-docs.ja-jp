---
title: PowerApps の既存ポータルの管理 | Microsoft Docs
description: PowerApps のポータルを管理するための手順。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: null
ms.date: 07/18/2019
ms.author: shjais
ms.reviewer: null
---

# <a name="manage-existing-portals-in-powerapps"></a>PowerApps で既存のポータルを管理する

[!include[cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

ポータルを作成すると、PowerApps のホームページの **最近のアプリ** セクションに表示されます。

> [!div class=mx-imgBorder]
> ![最近のアプリ](media/recent-apps.png "最近のアプリ")  

アプリを管理するには、ポータルの **そのほかのコマンド** (**…**) 選択して、コンテキスト メニューからアクションを選択します。

> [!div class=mx-imgBorder]
> ![ポータル アプリのオプション](media/portal-app-options.png "ポータル アプリのオプション")  

## <a name="edit"></a>編集

[ポータル デザイナー](portal-designer-anatomy.md) を開き、ポータル コンテンツおよびコンポーネントを編集します。  

> [!div class=mx-imgBorder]
> ![ポータル作成元](media/portal-maker.png "ポータル作成元")  

## <a name="browse"></a>参照

ポータルを開くと、Web サイトを閲覧できます。 これにより、顧客にどう見えるかがポータルで確認できます。

> [!div class=mx-imgBorder]
> ![ポータル Web サイト](media/portal-website.png "ポータル Web サイト")  

または、 Web サイトでの変更を表示するには、 **Web サイトを閲覧する**を [ポータル デザイナー](portal-designer-anatomy.md) を選択すると、ポータルを開いて Web サイトを閲覧できます。 Web サイトは、Web サイトの URL を含む新しいタブで開きます。

## <a name="share"></a>共有

内部または外部ユーザーとポータルを共有できます。 **このポータルを共有する** ウィンドウで説明した手順に従ってください。

> [!div class=mx-imgBorder]
> ![ポータルの共有](media/share-portal.png "ポータルの共有")  

### <a name="share-with-internal-users"></a>内部ユーザーと共有します。

内部ユーザーとポータルを共有するには、セキュリティ ロールをまず作成し、該当ユーザーをセキュリティ ロールに割り当てて、ポータルを使用できるようにする必要があります。

> [!NOTE]
> Common Data Service のユーザーとしてポータルのエンティティに対する適切な特権を持っていないときは、「この環境でソリューションを表示するためのアクセス権を持っていません」などのエラーメッセージが表示される場合があります。 また、「この環境で Web サイトを表示するためのアクセス許可がありません」と表示される場合もあります。 このプレビューでは、ユーザーが、**システム管理者** または、対応する Common Data Service データベース内の少なくとも **システム カスタマイザー** というセキュリティ ロールに含まれるようにすることをお勧めします。

#### <a name="step-1-create-a-security-role"></a>ステップ 1: セキュリティ ロールを作成する

1.  **このポータルの共有** ウィンドウの **セキュリティ ロールの作成** で、**セキュリティ ロール** を選択します。 すべての構成済みのセキュリティ ロールの一覧が表示されます。

2.  [操作] ツール バーで、**新規**を選択します。

3.  **新規のセキュリティ ロール** ウィンドウで、ロールの名前を入力します。

4.  ポータルで使用されるすべてのエンティティの特権を設定します。

5.  セキュリティ ロールの構成を終了する場合、ツール バー上で**保存して閉じる**を選択します。

セキュリティ ロールおよび特権の詳細については、[セキュリティ ロールおよび特権](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/admin/security-roles-privileges)を参照してください。  

#### <a name="step-2-assign-users-to-the-security-role"></a>ステップ 2: ユーザーをセキュリティ ロールに割り当てる

1.  **このポータルの共有** ウィンドウで、**セキュリティ ロールへのユーザーの割り当て** の、**ユーザー** を選択します。 すべてのユーザーの一覧が表示されます。

2.  セキュリティ ロールを割り当てるユーザーを選択します。

3.  **ロールの管理**を選択します。

    > [!NOTE]
    > コマンド バーの **ロールの管理** ボタンが表示されない場合は、URL の forceUCI を 0 に設定し、クライアントを変更する必要があります。 たとえば、https://&lt;org\_url&gt;/main.aspx?pagetype=entitylist&etn=systemuser&forceUCI=0

4.  **ユーザー ロールの管理** ダイアログ ボックスで、前に作成したセキュリティ ロールを選び、**OK** を選びます。

### <a name="share-with-external-users"></a>外部ユーザーと共有する

ポータルは、匿名で機能させる必要があります。また、外部ユーザーがアクセスできる必要があります。 外部ユーザーのロールおよびアクセス許可を管理する高度な機能を試行する場合、[ポータルでの使用に関する連絡先の構成](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/portals/configure-contacts)、[ポータルに取引先担当者を招待する](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/portals/invite-contacts)、[ポータルの Web ロールの作成](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/portals/create-web-roles)、[エンティティのアクセス許可の割り当て](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/portals/assign-entity-permissions)を参照してください。  

## <a name="settings"></a>設定

ポータル設定を表示して、ポータルの名前を変更できるようにします。 ポータル管理センターでのポータル管理や、サイト設定を使用する作業するなど、高度な操作も実行できます。 構成では、PowerApps ポータル管理センターとサイトの設定へのリンクが提供されます。 詳細については、[ポータルの管理](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/portals/manage-portal) と [ポータルのサイト設定の構成](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/portals/configure-site-settings)を参照してください。  

> [!div class=mx-imgBorder]
> ![ポータルの設定](media/portal-settings.png "ポータルの設定")  

## <a name="delete"></a>削除

ポータルおよびホスト リソースを削除します。 ポータルを削除すると、URL にアクセスできなくなりなります。 ポータルの削除は、環境に存在するポータルの構成またはソリューションに影響しません。現状のまま残ります。
環境からポータル組織を削除するには、ポータル構成を手動で削除する必要があります。 これには、ポータル管理アプリを使用し、ポータルに対応する Web レコードを削除します。

> [!NOTE]
> ポータルを削除する特権がない場合、エラーが表示されます。 ポータルを削除するには、システム カスタマイザーまたはシステム管理者ロールが必要です。 また、ユーザーは、Azure Active Directory のポータル アプリケーションの所有者である必要があります。 ポータルを作成するユーザーは既定で所有者とされ、ポータルを削除できます。 所有者としてユーザー自身を追加するには、[Azure AD の所有者として自分を追加する](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/portals/manage-portal#to-add-yourself-as-an-owner-of-the-azure-ad-application)を参照してください。

## <a name="details"></a>詳細

ポータルの所有者、作成および最終変更された日付と時刻、ポータルの URL などの詳細表示。

> [!div class=mx-imgBorder]
> ![ポータルの詳細](media/portal-details.png "ポータルの詳細")  

