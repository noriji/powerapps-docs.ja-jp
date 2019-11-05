---
title: Dynamics 365 | でモデル駆動型アプリを含む環境でポータルを作成するMicrosoft Docs
description: Dynamics 365 でモデル駆動型アプリを含む環境でポータルを作成する方法について説明します。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 50459f3fcd9ebe8894196f934c1b1d2275c490c4
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2019
ms.locfileid: "73542627"
---
# <a name="create-a-portal-in-an-environment-containing-model-driven-apps-in-dynamics-365"></a>Dynamics 365 でモデル駆動型アプリを含む環境でポータルを作成する

Dynamics 365 でモデル駆動型アプリを含む環境を選択した場合 (Dynamics 365 Sales や Dynamics 365 カスタマーサービスなど)、[ポータルテンプレート](portal-templates.md)で説明されているポータルを作成できます。

1.  [PowerApps にサインインします](https://make.powerapps.com)。

2.  左側のウィンドウで **[作成]** を選択し、 **[検索テンプレート]** フィールドに「**ポータル**」と入力して、Dynamics 365 ポータルのすべてのテンプレートを表示します。

    > [!div class=mx-imgBorder]
    > ![Dynamics 365 ポータルテンプレート](media/dynamics-portals.png "Dynamics 365 ポータルテンプレート")  

3.  必要なポータルテンプレートを選択します。

4.  [ポータルの作成] ウィンドウで、ポータルの名前と web サイトのアドレスを入力し、ドロップダウンリストから言語を選択します。 完了したら、 **[作成]** を選択します。 作成プロセスは、「 [Common Data Service スターターポータルの作成](create-portal.md)」セクションで説明した手順と同じです。

> [!NOTE]
> - 古いポータルアドオンを購入し、アドオンを使用してポータルをプロビジョニングする場合は、 **Dynamics 365 管理センター**のページにアクセスする必要があります。 詳細情報:[古いポータルアドオンを使用してポータルをプロビジョニング](provision-portal-add-on.md)する
> - 以前のポータルアドオンを使用してポータルをプロビジョニングした場合でも、 [make.powerapps.com](https://make.powerapps.com)からカスタマイズして管理することができます。
> - [Make.powerapps.com](https://make.powerapps.com)からポータルをプロビジョニングしても、以前のポータルアドオンは使用されません。 また、これらのポータルは、 **Dynamics 365 管理センター**ページの **[アプリケーション]** タブには表示されません。
> - Common Data Service starter ポータルは、 **Dynamics 365 管理センター**ページから作成することはできません。
> - テナントでポータルの作成を無効にするには、「[テナントでポータルの作成を無効](create-portal.md#disable-portal-creation-in-a-tenant)にする」を参照してください。

