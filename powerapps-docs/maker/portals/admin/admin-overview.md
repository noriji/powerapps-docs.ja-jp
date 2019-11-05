---
title: PowerApps ポータル管理センターの概要 |MicrosoftDocs
description: PowerApps ポータル管理センターに関する情報です。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 6f8434a6a395931fc4edfe02913f47536b4a709d
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2019
ms.locfileid: "73543070"
---
# <a name="powerapps-portals-admin-center"></a>PowerApps ポータル管理センター

PowerApps ポータル管理センターでは、ポータルで高度な管理操作を実行できます。 ポータルが正常にプロビジョニングされると、管理センターが使用できるようになります。

## <a name="open-powerapps-portals-admin-center"></a>PowerApps ポータル管理センターを開く

1. PowerApps ホームページの **[最近使ったアプリ]** セクションに移動し、ポータルを見つけます。

    > [!div class=mx-imgBorder]
    > ![最近使用したアプリ](../media/recent-apps.png "最近使用したアプリ")  

2. **その他のコマンド (...)**  > **設定** を選択します。

    > [!div class=mx-imgBorder]
    > ![ポータルの設定オプション](../media/portal-settings-option.png "ポータルの設定オプション")

3. ポータルの **[設定]** ウィンドウで、 **[管理]** を選択します。

    > [!div class=mx-imgBorder]
    > ![ポータルの設定ウィンドウ](../media/portal-settings-admin.png "ポータルの設定ウィンドウ")

## <a name="add-yourself-as-an-owner-of-the-azure-ad-application"></a>Azure AD アプリケーションの所有者として自分を追加する

グローバル管理者ではなく、既にプロビジョニングされているポータルを管理しようとした場合、またはプロビジョニングが失敗した場合に再送信する場合は、ポータルに接続されている Azure Active Directory (Azure AD) アプリケーションの所有者である必要があります。

1. PowerApps ポータル管理センターにアクセスし、ポータルの **[詳細]** タブを開きます。

2. **[アプリケーション ID]** フィールドから値をコピーします。

    > [!div class=mx-imgBorder]
    > ![ポータルの [詳細] タブ](../media/portal-details-admin.png "ポータルの [詳細] タブ")

3. テナントに関連付けられている Azure AD にアクセスします。 管理されていない[ディレクトリを管理者として引き継ぐ [!include[](../../../includes/proc-more-information.md)] Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-manage-o365-subscription)

4. Azure AD で、コピーしたアプリケーション ID を使用してアプリの登録を検索します。 **マイアプリ**から**すべてのアプリ**への切り替えが必要になる場合があります。

5. このアプリ登録の所有者として、ユーザーまたはグループを追加します。 [アプリへのアクセスの管理](https://docs.microsoft.com/azure/active-directory/active-directory-managing-access-to-apps)[!include[](../../../includes/proc-more-information.md)]

    > [!Note]
    > このタスクは、組織の全体管理者またはこのアプリケーションの既存の所有者が実行できます。

6. 自分自身を所有者として追加した後、PowerApps ポータル管理センターページをもう一度開きます。