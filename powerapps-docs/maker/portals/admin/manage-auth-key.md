---
title: ポータルを Common Data Service 環境に接続する |MicrosoftDocs
description: ポータルを Common Data Service 環境に接続する方法と、認証キーを更新する方法について説明します。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 31632f4de1834855c696baa1b4b651ed777c8abd
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/11/2019
ms.locfileid: "72977498"
---
# <a name="connect-to-a-common-data-service-environment-using-a-portal"></a>ポータルを使用して Common Data Service 環境に接続する

ポータルは、Azure Active Directory アプリケーションを使用して Common Data Service 環境に接続します。 アプリケーションは、ポータルがプロビジョニングされているのと同じテナントに作成されます。 アプリケーションは、ポータルのプロビジョニング処理中に Common Data Service 環境に登録されます。

ポータルを![Common Data Service 環境に接続]する(../media/connect-with-dynamics.png "Common Data Service の環境とポータルを接続する")

各ポータルには、同じ Common Data Service 環境に接続されているかどうかに関係なく、別の Azure Active Directory アプリケーションが関連付けられています。 ポータル用に作成された既定の Azure Active Directory 認証プロバイダーは、同じ Azure Active Directory アプリケーションを使用してポータルを認証します。 承認は、ポータルにアクセスするユーザーに割り当てられた web ロールによって適用されます。

Azure Active Directory で、関連付けられているポータルアプリケーションを確認できます。 このアプリケーションの名前は Microsoft CRM ポータルになり、ポータル ID は Azure Active Directory アプリケーションの **[アプリ ID URI]** フィールドに表示されます。 ポータルをプロビジョニングする担当者がこのアプリケーションを所有しています。 このアプリケーションを削除または変更することはできません。また、ポータル機能を無効にすることもできます。 PowerApps ポータル管理センターからポータルを管理するには、アプリケーションの所有者である必要があります。

## <a name="authentication-key"></a>認証キー

ポータルが Azure Active Directory アプリケーションを使用して Common Data Service に接続するには、Azure Active Directory アプリケーションに接続されている認証キーが必要です。 このキーは、ポータルをプロビジョニングするときに生成され、このキーのパブリックな部分が Azure Active Directory アプリケーションに自動的にアップロードされます。

> [!IMPORTANT]
> 認証キーは2年後に有効期限が切れます。 ポータルが引き続き Common Data Service 環境に接続できるようにするには、2年ごとに更新する必要があります。 キーを更新しないと、ポータルが動作しなくなります。  

### <a name="authentication-key-details"></a>認証キーの詳細

認証キーの詳細は、PowerApps ポータル管理センターとポータルに表示されます。

**PowerApps ポータル管理センター**

1. [PowerApps ポータル管理センター](admin-overview.md)を開きます。

2. **[ポータル認証キーの管理]** を選択します。 認証キーは、有効期限と拇印と共に表示されます。

   > [!div class=mx-imgBorder]
   > Powerapps ポータルでの![認証キーの詳細](../media/manage-auth-key.png "powerapps ポータルの管理センター認証キーの詳細 powerapps ポータル管理センター")

**サイト**

1. ポータルに管理者としてサインインします。

2. URL < portal_path > に移動します。 認証キーの有効期限が表示されます。 

   > [!div class=mx-imgBorder]
   > ![ポータルサービスページ](../media/portal-services-page.png "ポータルサービスページ")

> [!NOTE]
> 認証キーの情報を表示するには、同じブラウザーセッションでポータルにサインインする必要があります。また、すべての web サイトのアクセス許可を持っている必要があります。

### <a name="authentication-key-expiration-notification"></a>認証キーの有効期限の通知

認証キーの有効期限が切れる前に、電子メール、PowerApps ポータル管理センター、ポータルによって通知されます。

**Email**

ポータルに接続している組織の電子メール通知にサインアップしたユーザーに電子メールが送信されます。 電子メール通知のサインアップに関する詳細情報:[管理者への電子メール通知の管理](https://docs.microsoft.com/dynamics365/customer-engagement/admin/manage-email-notifications)

電子メール通知は、次の間隔で送信されます。 
- 90日 
- 60日 
- 30日 
- 15日 
- 7日間 
- 6日 
- 5日 
- 4日 
- 3日 
- 2日 
- 1日 
- 12時間 
- 6時間 
- 3時間

また、キーの有効期限が切れると、毎日1週間まで有効期限が切れると通知されます。

> [!NOTE]
> - 間隔は、キーの有効期限から UTC で計算されます。
> - 電子メールは、上に示した間隔と正確に一致するとは限りません。 電子メール通知が遅延しているか、失われている可能性があります。 キーの有効期限もオンラインで確認してください。

**PowerApps ポータル管理センター**

キーの有効期限に関するメッセージがページの上部に表示されます。

> [!div class=mx-imgBorder]
> Powerapps ポータルでの![認証キーの通知](../media/portal-admin-center-auth-notif.png "powerapps ポータルでの認証キー")の通知管理センター

**サイト**

Portal_path >/の < URL に移動すると、キーの有効期限に関する通知がページの下部に表示されます。

> [!NOTE]
> 同じブラウザーセッションでポータルにサインインする必要があり、すべての web サイトのアクセス許可が割り当てられている必要があります。

> [!div class=mx-imgBorder]
> ポータルでの![認証キーの]通知 (ポータル(../media/portal-service-page-auth-notif.png "で")の認証キー通知)

## <a name="renew-portal-authentication-key"></a>ポータル認証キーを更新する

ポータルが Common Data Service 環境に接続できるようにするには、2年ごとにキーを更新する必要があります。

> [!NOTE]
> キーを更新するには、ポータルを管理するためのアクセス許可が必要です。

1. [PowerApps ポータル管理センター](admin-overview.md)を開きます。

2. **[ポータル認証キーの管理]** を選択します。 認証キーは、有効期限と拇印と共に表示されます。

    > [!div class=mx-imgBorder]
    > ![ポータル認証キー]の管理(../media/manage-portal-auth-key.png "ポータルの認証")キーの管理

3. **[キーの更新]** を選択します。

4. メッセージで **[更新]** を選択します。 更新プロセスが開始され、メッセージが表示されます。

> [!NOTE]
> - このプロセスはバックグラウンドで実行されますが、ポータルは一度だけ再起動します。
> - キーを更新すると、2年間更新されます。
> - このプロセスには 5 ~ 7 分かかります。

### <a name="troubleshooting"></a>トラブルシューティング

キーの更新に失敗した場合は、次の操作と共にエラーメッセージが表示されます。

- **認証キーの更新を再試行**します。 この操作では、ポータル認証キーの更新プロセスを再開できます。 更新プログラムが何度も失敗する場合は、Microsoft サポートに問い合わせてください。

    > [!div class=mx-imgBorder]
    > ![ポータル認証キー更新]の再試行(../media/retry-auth-key-update.png "ポータル認証キーの更新")