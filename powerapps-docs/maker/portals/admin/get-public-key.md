---
title: ポータルの公開キーをダウンロードする |MicrosoftDocs
description: ポータルの公開キーをダウンロードする方法について説明します。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 39e909acb325bd870f73e16a72da78b4bec07c79
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/11/2019
ms.locfileid: "72975980"
---
# <a name="download-public-key-of-portal"></a>ポータルの公開キーをダウンロードする

ポータルの公開キーは、Dynamics 365 のモデル駆動型アプリに対して、ポータルの認証された訪問者と連携するようにライブアシスタンスを構成するために使用されます。 CafeX による[Live Assist](https://www.cafex.com/en/products/live-assist-dynamics-365/)は、ユーザーがポータルにライブチャットアシスタントを埋め込むためのチャットソリューションを提供します。 公開キーを使用してポータルにチャットを埋め込む方法の詳細については[、「Dynamics Customer ポータルでの認証](https://www.liveassistfor365.com/en/support/authenticated-visitors-in-the-dynamics-customer-portal/)された訪問者」を参照してください。

1. [PowerApps ポータル管理センター](admin-overview.md)を開きます。

2.  **[ポータルアクション]**  >  **[公開キーの取得]** に移動します。 キーが表示されます。

    > [!div class=mx-imgBorder]
    > ポータルの公開キー![を取得する]ポータル(../media/get-public-key.png "の公開")キーを取得する

3.  テキストファイルでキーをダウンロードするには、 **[テキストとしてダウンロード]** を選択します。

または、次の URL に移動して公開キーを取得することもできます: `<portal_base_URL>/_ services/auth/publickey` 

> [!NOTE]
> ポータルが現在プロビジョニングされている場合、または組織でパッケージのインストールが完了していない場合は、公開キーをダウンロードしようとするとエラーが表示されます。 ポータルのプロビジョニングが完了し、ポータルが起動して実行されるまで待つ必要があります。
