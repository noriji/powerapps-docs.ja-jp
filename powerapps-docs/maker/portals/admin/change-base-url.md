---
title: ポータルの基本 URL を変更する | MicrosoftDocs
description: ポータルの基本 URL の変更方法を説明します。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: null
ms.date: 07/18/2019
ms.author: shjais
ms.reviewer: null
---

# <a name="change-the-base-url-of-a-portal"></a>ポータルの基本 URL を変更する

[!include[cc-beta-prerelease-disclaimer](../../../includes/cc-beta-prerelease-disclaimer.md)]

プロビジョニングの後、ポータルの基本 URL を変更することができます。 たとえば、ポータルをプロビジョニングするときに `contosocommunity.microsoftcrmportals.com` を基本 URL として選択する場合、要件を満たすように後から `contosocommunityportal.microsoftcrmportals.com` に変更することができます。

> [!NOTE]
> ポータルの基本 URL を変更すると、古い URL にアクセスすることはできなくなり、それらのポータルを使用する他の顧客に対して使用可能になります。

1.  [PowerApps ポータル管理センター](admin-overview.md) を開きます。

2.  **ポータル アクション** > **基本 URL の変更**の順に移動します。 

    > [!div class=mx-imgBorder]
    > ![ポータルの基本 URL の変更](../media/change-base-url-action.png "ポータルの基本 URL の変更")

3.  基本 URL ウィンドウで、ポータルの新しい基本 URL を入力します。

    > [!div class=mx-imgBorder]
    > ![ポータルの新しい基本 URL の指定](../media/change-base-url.png "ポータルの新しい基本 URL の指定")

4.  確認メッセージで**URL の変更**を選択します。

## <a name="troubleshooting"></a>トラブルシューティング​​

このセクションは、ポータルの基本 URL を変更するときの問題のトラブルシューティングに関する情報を提供します。

### <a name="changing-the-base-url-fails"></a>基本 URL を変更が失敗する

ポータルの基本 URL の変更が失敗する場合、次の画像に示すようにエラーが表示されます。

> [!div class=mx-imgBorder]
> ![ポータルの基本 URL の変更中のエラー](../media/change-base-url-error.png "ポータルの基本 URL の変更中のエラー")

通常、これらは一次的エラーであり、**基本 URL の変更**を選択して基本 URL の変更を再試行する必要があります。 イシューが解決しない場合は、Microsoft サポートにお問い合わせください。
