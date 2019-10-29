---
title: よく寄せられる質問 |Microsoft Docs
description: PowerApps ポータルでよく寄せられる質問。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: eb7228f669fe8c36e25a18f4db0c7e4c4964a42d
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/11/2019
ms.locfileid: "72976693"
---
# <a name="powerapps-portals-faq"></a>PowerApps ポータルに関する FAQ

よく寄せられる質問の一覧をコンパイルし、簡単な回答を提供して、情報をすばやく取得できます。

## <a name="im-getting-an-error-that-only-one-portal-can-be-created"></a>1つのポータルだけを作成できるというエラーが発生しています。

現時点では、各種類のポータルは、言語ごとに1つの環境でのみ作成できます。 複数のポータルを作成しようとすると、次のようなエラーメッセージが表示されます。

> [!div class=mx-imgBorder]
> ポータルによって![作成されたエラー]の最大(media/portal-max-error.png "数がポータルで作成された")エラー

ポータルをさらに作成するには、エラーメッセージの **[新しい環境の作成]** リンクを使用して、新しい環境を作成する必要があります。 ポータルの作成の詳細については、「[ポータルを作成する](create-portal.md)」を参照してください。

## <a name="im-getting-an-error-that-i-cant-delete-my-portal"></a>ポータルを削除できないというエラーが発生します。

ポータルを削除するための十分な特権がない場合は、次のようなエラーが表示されます。

> [!div class=mx-imgBorder]
> ポータルの![削除エラー](media/portal-delete-error.png "ポータルの削除エラー")

ポータルおよび必要な権限を削除する方法については、「 [Delete a portal](manage-existing-portals.md#delete)」を参照してください。

## <a name="im-getting-an-error-that-i-cant-create-a-portal"></a>ポータルを作成できないというエラーが発生します。

環境でポータルを作成するための十分な特権がない場合は、次のようなエラーが表示されます。

> [!div class=mx-imgBorder]
> ポータル![作成エラー](media/portal-create-error.png "ポータル作成エラー")

ポータルの作成と必要な権限の詳細については、「[ポータルを作成する](create-portal.md)」を参照してください。

## <a name="im-getting-the-message-your-data-isnt-quite-ready"></a>"データの準備ができていません" というメッセージが表示されます。

場合によっては、データベースの作成に時間がかかり、ホームページで正しい状態が反映されないことがあります。 この場合、次のメッセージが表示されます。

> [!div class=mx-imgBorder]
> 準備(media/data-not-ready.png "さ")れていない![データ]データの準備ができていません

[データベースの作成] プロンプトが表示されない場合や、データが完全に準備できていない場合は、[**空白] タイルからポータル**を選択する前に、PowerApps ホームページを更新してみてください。

## <a name="im-getting-an-error-that-i-dont-have-required-permissions-to-create-azure-active-directory-applications"></a>Azure Active Directory アプリケーションを作成するために必要なアクセス許可がないというエラーが表示されます。

ポータルを作成すると、新しいアプリケーションとしてポータルが、テナントに関連付けられている Azure Active Directory に登録されます。 Azure Active Directory テナントにアプリケーションを登録するための十分なアクセス許可がない場合は、次のようなエラーが表示されます。

> [!div class=mx-imgBorder]
> ![Azure Active Directory エラー](media/azure-ad-error.png "Azure Active Directory エラー")

Azure Active Directory でアプリケーションを作成して登録するには、テナント管理者に連絡して、テナントの**アプリの登録**設定を有効にする必要があります。 詳細については、「[必要なアクセス許可](https://docs.microsoft.com/en-us/azure/active-directory/develop/howto-create-service-principal-portal#required-permissions)」を参照してください。

## <a name="im-getting-an-error-that-portal-creation-is-blocked-in-this-tenant-by-global-administrator"></a>このテナントでは、グローバル管理者によってポータルの作成がブロックされているというエラーが発生します。

グローバル管理者がテナントでポータルの作成をブロックした場合、次のようなエラーが表示されます。

> [!div class=mx-imgBorder]
> ![ポータルの作成がブロック]されたエラー(media/portal-create-blocked-error.png "ポータルの作成ブロックエラー")

管理者以外のユーザーがポータルを作成できるようにするには、全体管理者に連絡する必要があります。

グローバル管理者の場合は、PowerShell を使用して `disablePortalsCreationByNonAdminUsers` テナントレベルの設定を無効にする必要があります。 PowerShell ウィンドウで次のコマンドを実行します (管理者として PowerShell を実行します)。

```
Set-TenantSettings -RequestBody @{ "disablePortalsCreationByNonAdminUsers" = $false }
```

詳細情報:[テナントでポータルの作成を無効にする](create-portal.md#disable-portal-creation-in-a-tenant)

## <a name="im-getting-an-error-that-i-dont-have-appropriate-license-to-access-this-website"></a>この web サイトにアクセスするための適切なライセンスを持っていないことを示すエラーが表示されます。

認証されたページにアクセスするためにポータルを使用する組織の内部ユーザーは、ポータルが接続されている環境にライセンスを割り当てる必要があります。 内部ユーザーのポータルのユーザー権限の詳細については、[こちら](https://docs.microsoft.com/en-us/power-platform/admin/powerapps-flow-licensing-faq#can-you-clarify-the-use-rights-to-portals-for-internal-users)を参照してください。 環境にライセンスが割り当てられていない場合、内部ユーザーには次のようなエラーが表示されます。

> [!div class=mx-imgBorder]
> ![ポータルログインエラー](media/portal-login-error.png "ポータルのログインエラー")

