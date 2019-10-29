---
title: ポータルのベース URL を変更する |MicrosoftDocs
description: ポータルのベース URL を変更する方法について説明します。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: cfc2fd0ca753aebfe7bc77b73c7e7ec1ca011387
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/11/2019
ms.locfileid: "72977475"
---
# <a name="change-the-base-url-of-a-portal"></a>ポータルのベース URL を変更する

ポータルのベース URL は、プロビジョニング後に変更できます。 たとえば、ポータルのプロビジョニング時にベース URL として `contosocommunity.microsoftcrmportals.com` を選択した場合は、後で要件を満たすように `contosocommunityportal.microsoftcrmportals.com` に変更できます。

> [!NOTE]
> ポータルのベース URL を変更すると、古い URL はアクセスできなくなり、他の顧客がポータルで使用できるようになります。

1.  [PowerApps ポータル管理センター](admin-overview.md)を開きます。

2.  **[ポータルアクション]**  >  **[ベース URL の変更]** に移動します。 

    > [!div class=mx-imgBorder]
    > ポータルの![ベース url の変更](../media/change-base-url-action.png "ポータルのベース url")の変更

3.  [ベース URL の変更] ウィンドウで、ポータルの新しいベース URL を入力します。

    > [!div class=mx-imgBorder]
    > ![ポータルの新しいベース url を指定]するポータル(../media/change-base-url.png "の新しいベース url を指定")する

4.  確認ウィンドウで **[URL の変更]** を選択します。

## <a name="troubleshooting"></a>トラブルシューティング

このセクションでは、ポータルのベース URL を変更する際の問題のトラブルシューティングについて説明します。

### <a name="changing-the-base-url-fails"></a>ベース URL の変更が失敗する

ポータルのベース URL を変更できない場合は、次の図のようなエラーが表示されます。

> [!div class=mx-imgBorder]
> ポータル(../media/change-base-url-error.png "のベース url を変更しているときに") ![、ポータルのベース url を変更中にエラーが発生し]ました

通常、これらは一時的なエラーであり、ベース url の変更を再試行するには **[ベース url の変更]** を選択する必要があります。 問題が解決しない場合は、Microsoft サポートにお問い合わせください。
