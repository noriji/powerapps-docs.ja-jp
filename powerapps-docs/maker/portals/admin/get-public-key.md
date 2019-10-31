---
title: ポータルの公開キーのダウンロード | MicrosoftDocs
description: ポータルの公開キーのダウンロード方法を説明します。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: null
ms.date: 09/16/2019
ms.author: shjais
ms.reviewer: null
---

# <a name="download-public-key-of-portal"></a>ポータルの公開キーのダウンロード

[!include[cc-beta-prerelease-disclaimer](../../../includes/cc-beta-prerelease-disclaimer.md)]

ポータルの公開キーは、ポータルの認証済み訪問者と作業する Dynamics 365 のモデル駆動型アプリの Live Assist を構成するために使用します。 CafeX の [Live Assist](https://www.cafex.com/en/products/live-assist-dynamics-365/) は、ユーザーが自分のポータルにライブ チャット アシスタンスを埋め込むことができる、チャット ソリューションを提供します。 ポータルにチャットを埋め込む公開キーの使用方法については、[Dynamics カスタマー ポータルの認証済みビジター](https://www.liveassistfor365.com/en/support/authenticated-visitors-in-the-dynamics-customer-portal/)を参照してください

1. [PowerApps ポータル管理センター](admin-overview.md) を開きます。

2.  **ポータル アクション** > **公開キーの取得**の順に移動します。 キーが表示されます。

    > [!div class=mx-imgBorder]
    > ![ポータルの公開キーの取得](../media/get-public-key.png "ポータルの公開キーの取得")

3.  **テキストとしてダウンロード**を選択してテキスト ファイルでキーをダウンロードします。

または、URL: `<portal_base_URL>/_ services/auth/publickey` に移動することで公開キーを取得することもできます。 

> [!NOTE]
> ポータルが現在プロビジョニング中である場合、またはパッケージのインストールが組織内で終了していない場合に、公開キーのダウンロードを試みるとエラーが表示されます。 ポータルのプロビジョニングが完了してポータルが稼働するまで待機する必要があります。
