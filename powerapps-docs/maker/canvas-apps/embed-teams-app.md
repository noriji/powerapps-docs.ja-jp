---
title: Teams にアプリを埋め込む |Microsoft Docs
description: PowerApps で作成したアプリを Microsoft Teams に埋め込み、共有することができます。
author: matthewbolanos
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/29/2019
ms.author: mabolan
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: e2cce61533bf86063d907882024a5a83c2e03fb7
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2019
ms.locfileid: "73538992"
---
# <a name="embed-an-app-in-teams"></a>Teams にアプリを埋め込む

作成した PowerApps は、Microsoft Teams に直接埋め込むことによって共有できます。 完了すると、ユーザーは [ **+** ] を選択して、チーム内**のチームチャネル**または会話にアプリを追加できます。 アプリは、**チームのタブ**の下にタイルとして表示されます。

管理者はアプリをアップロードして、テナント内の**すべて**のチームに対して [**すべてのタブ] セクション**に表示されるようにすることができます。 「 [Microsoft Teams でのアプリの共有」を](https://docs.microsoft.com/power-platform/admin/embed-app-teams)参照してください。

> [!NOTE]
> Team カスタムアプリポリシーは、カスタムアプリのアップロードを許可するように設定する必要があります。 アプリをチームに埋め込むことができない場合は、管理者に連絡して、[カスタムアプリ設定](https://docs.microsoft.com/MicrosoftTeams/teams-custom-app-policies-and-settings#custom-app-policy-and-settings)がセットアップされているかどうかを確認してください。

## <a name="prerequisites"></a>前提条件

- 有効な[PowerApps ライセンス](https://docs.microsoft.com/power-platform/admin/pricing-billing-skus)が必要です。
- アプリをチームに埋め込むには、 [PowerApps を使用して作成され](data-platform-create-app.md)た既存のアプリが必要です。

## <a name="download-the-app"></a>アプリをダウンロードする

1. [Make.powerapps.com](https://make.powerapps.com)にサインインし、メニューの **[アプリ]** を選択します。

    ![アプリの一覧を表示する](./media/embed-teams-app/file-apps2.png "アプリの一覧を表示する")

2. チームで共有するアプリの **[その他のアクション]** (...) を選択し、 **[チームに追加]** を選択します。

    ![アプリの詳細](./media/embed-teams-app/add-to-teams.png "チームに追加")

3. チームに追加 パネルで、**ダウンロード** を選択します。 PowerApps は、アプリに既に設定されているアプリの説明とロゴを使用して、Teams マニフェストファイルを生成します。

    ![アプリの詳細](./media/embed-teams-app/download-app.png "アプリのダウンロード")

## <a name="add-the-app-as-a-personal-app"></a>アプリを個人用アプリとして追加する

1. アプリを個人用アプリとして、またはチャネルまたはメッセージ交換にタブとして追加するには、左側のナビゲーションで **[アプリ]** を選択し、 **[カスタムアプリのアップロード]** を選択します。

    > [!NOTE]
    > カスタムアプリの**アップロード**は、チームの管理者がカスタムアプリ[ポリシー](https://docs.microsoft.com/microsoftteams/teams-app-setup-policies)を作成し、 **[カスタムアプリのアップロードを許可する]** がオンになっている場合にのみ表示されます。

    ![[アプリをタブとして追加]](./media/embed-teams-app/upload-custom-app.png "カスタムアプリをアップロードする")

2. **[追加]** を選択してアプリを個人用アプリとして追加するか、 **[チームに追加]** を選択して既存のチャネルまたはメッセージ交換内のタブとしてアプリを追加します。

## <a name="publish-the-app-to-the-teams-catalogue"></a>Teams カタログにアプリを発行する

管理者の場合は、Microsoft Teams カタログに[アプリを発行](https://docs.microsoft.com/microsoftteams/tenant-apps-catalog-teams)することもできます。

### <a name="see-also"></a>関連項目

[Microsoft Teams へようこそ](https://docs.microsoft.com/MicrosoftTeams/teams-overview)
