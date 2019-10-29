---
title: PowerApps で既存のポータルを管理する |Microsoft Docs
description: PowerApps でポータルを管理する方法について説明します。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: f21671368bfdaf9623a294c86b113b6b62f028e7
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/11/2019
ms.locfileid: "72976440"
---
# <a name="manage-existing-portals-in-powerapps"></a>PowerApps で既存のポータルを管理する

作成したポータルは、PowerApps ホームページの **[最近使ったアプリ]** セクションに表示されます。

> [!div class=mx-imgBorder]
> 最近使用し![たアプリの](media/recent-apps.png "最近")のアプリ  

アプリを管理するには、ポータルの [**その他のコマンド**( **.** .)] を選択し、コンテキストメニューからアクションを選択します。

> [!div class=mx-imgBorder]
> ![ポータルアプリオプション](media/portal-app-options.png "ポータルアプリオプション")  

## <a name="edit"></a>編集

[PowerApps ポータル Studio](portal-designer-anatomy.md)を開いて、ポータルのコンテンツとコンポーネントを編集します。  

> [!div class=mx-imgBorder]
> ![ポータルメーカー](media/portal-maker.png "ポータル")の作成者  

## <a name="browse"></a>参照

ポータルを開いて web サイトを参照します。 これにより、顧客に表示されるポータルを確認することができます。

> [!div class=mx-imgBorder]
> ![ポータル web]サイト(media/portal-website.png "ポータル web サイト")  

または、 [PowerApps ポータル Studio](portal-designer-anatomy.md)で **[Web サイトの参照]** を選択して web サイトを参照し、web サイトに加えた変更を表示することもできます。 Web サイトの URL が新しいタブに表示されます。

## <a name="share"></a>共有

ポータルを内部または外部のユーザーと共有します。 「**このポータルを共有**する」ウィンドウに記載されている手順に従います。

> [!div class=mx-imgBorder]
> ![ポータル](media/share-portal.png "共有")ポータルを共有する  

### <a name="share-with-internal-users"></a>内部ユーザーと共有する

ポータルを内部ユーザーと共有するには、まずセキュリティロールを作成してから、ユーザーをセキュリティロールに割り当てて、ポータルを使用できるようにする必要があります。

> [!NOTE]
> Common Data Service のユーザーとして、ポータルエンティティに対する適切な権限がない場合は、"この環境でソリューションを表示するためのアクセス権がありません" などのエラーが表示されることがあります。 または "この環境で Web サイトを表示するためのアクセス権がありません"。 対応する Common Data Service データベースでは、システム管理者のセキュリティロールを使用することをお勧めします。

#### <a name="step-1-create-a-security-role"></a>手順 1: セキュリティロールを作成する

1.  **[このポータルを共有]** する ウィンドウの **[セキュリティロールの作成]** で、 **[セキュリティロール]** を選択します。 構成されているすべてのセキュリティロールの一覧が表示されます。

2.  操作 ツールバーで、**新規** を選択します。

3.  **[新しいセキュリティロール]** ウィンドウで、ロール名を入力します。

4.  ポータルで使用されるすべてのエンティティの特権を設定します。

5.  セキュリティロールの構成が完了したら、ツールバーの **[保存して閉じる]** を選択します。

セキュリティロールと特権の詳細については、「[セキュリティロールと特権](https://docs.microsoft.com/dynamics365/customer-engagement/admin/security-roles-privileges)」を参照してください。  

#### <a name="step-2-assign-users-to-the-security-role"></a>手順 2: ユーザーをセキュリティロールに割り当てる

1.  **[このポータルを共有]** する ウィンドウの **[ユーザーをセキュリティロールに割り当てる]** で、 **[ユーザー]** を選択します。 すべてのユーザーの一覧が表示されます。

2.  セキュリティロールを割り当てるユーザーを選択します。

3.  **[ロールの管理]** を選びます。

    > [!NOTE]
    > コマンドバーに **[ロールの管理]** ボタンが表示されない場合は、URL で forceuci を0に設定してクライアントを変更する必要があります。 たとえば、 https://&lt;org\_url&gt;/main? pagetype = entitylist & etn = & forceUCI = 0

4.  **[ユーザーロールの管理]** ダイアログボックスで、前の手順で作成したセキュリティロールを選択し、[ **OK]** を選択します。

### <a name="share-with-external-users"></a>外部ユーザーと共有する

ポータルは匿名で動作し、外部ユーザーがアクセスできるようにする必要があります。 外部ユーザーのロールとアクセス許可を管理するための高度な機能を試す場合は、「[ポータルで使用する連絡先の構成](https://docs.microsoft.com/dynamics365/customer-engagement/portals/configure-contacts)、ポータル[への連絡先の招待](https://docs.microsoft.com/dynamics365/customer-engagement/portals/invite-contacts)、[ポータルの web ロールの作成](https://docs.microsoft.com/dynamics365/customer-engagement/portals/create-web-roles)、[エンティティのアクセス許可の割り当て」を参照してください。](https://docs.microsoft.com/dynamics365/customer-engagement/portals/assign-entity-permissions).  

## <a name="settings"></a>設定

ポータルの設定が表示され、ポータルの名前を変更できます。 PowerApps ポータル管理センターでのポータルの管理や、サイト設定の操作などの高度な操作を実行することもできます。 設定には、PowerApps ポータル管理センターとサイト設定へのリンクが用意されています。 詳細については、 [「高度なポータル管理](admin/admin-overview.md)」と「[サイト設定の構成](configure/configure-site-settings.md)」を参照してください。  

> [!div class=mx-imgBorder]
> ![ポータル設定](media/portal-settings.png "ポータルの設定")  

## <a name="delete"></a>デリート

ポータルとホストされているリソースを削除します。 ポータルを削除すると、その URL にアクセスできなくなります。 ポータルを削除しても、使用している環境に存在するポータルの構成やソリューションには影響しません。そのまま残ります。
ポータルの構成を環境から完全に削除するには、手動でポータルの構成を削除する必要があります。 これを行うには、ポータル管理アプリを使用して、ポータルの対応する web サイトレコードを削除します。

> [!NOTE]
> ポータルを削除するための十分な特権がない場合は、エラーが表示されます。 ポータルを削除するには、システム管理者ロールが必要です。 また、Azure Active Directory では、ポータルアプリケーションの所有者である必要があります。 ポータルを作成するユーザーは、既定で所有者であり、ポータルを削除できます。 自分自身を所有者として追加する方法については、「 [Azure AD アプリケーションの所有者として自分を追加](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/portals/manage-portal#to-add-yourself-as-an-owner-of-the-azure-ad-application)する」を参照してください。

## <a name="details"></a>詳細

ポータルの所有者、作成日と最終変更日時、ポータルの URL などの詳細が表示されます。

> [!div class=mx-imgBorder]
> ポータルの![詳細](media/portal-details.png "ポータルの詳細")  

