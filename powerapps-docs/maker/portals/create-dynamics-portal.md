---
title: Dynamics 365 環境を使用してポータルを作成する |Microsoft Docs
description: Dynamics 365 環境でポータルを作成する手順。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: e81fde2c5f756c9a7f08bfcd6438efca6321a420
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/11/2019
ms.locfileid: "72975497"
---
# <a name="create-a-portal-with-dynamics-365-environment"></a>Dynamics 365 環境でポータルを作成する

Dynamics 365 でモデル駆動型アプリを含む環境を選択した場合は、「[ポータルテンプレート](portal-templates.md)」で説明されているポータルを作成できます。

1.  [PowerApps にサインインします](http://web.powerapps.com)。

2.  左側のウィンドウで **[作成]** を選択し、 **[検索テンプレート]** フィールドに「**ポータル**」と入力して、Dynamics 365 ポータルのすべてのテンプレートを表示します。

    > [!div class=mx-imgBorder]
    > ![Dynamics 365 ポータルテンプレート](media/dynamics-portals.png "dynamics 365 ポータルテンプレート")  

3.  必要なポータルテンプレートを選択します。

4.  [ポータルの作成] ウィンドウで、ポータルの名前と web サイトのアドレスを入力し、ドロップダウンリストから言語を選択します。 完了したら、 **[作成]** を選択します。 作成プロセスは、「 [Common Data Service スターターポータルの作成](create-portal.md)」セクションで説明した手順と同じです。

> [!NOTE]
> - 古いポータルアドオンを購入し、アドオンを使用してポータルをプロビジョニングする場合は、 **Dynamics 365 管理センター**のページにアクセスする必要があります。 詳細情報:[ポータルのプロビジョニング](https://docs.microsoft.com/en-gb/dynamics365/customer-engagement/portals/provision-portal)
> - 以前のポータルアドオンを使用してポータルをプロビジョニングした場合でも、 [make.powerapps.com](https://make.powerapps.com)からカスタマイズして管理することができます。
> - [Make.powerapps.com](https://make.powerapps.com)からポータルをプロビジョニングしても、以前のポータルアドオンは使用されません。 また、これらのポータルは、 **Dynamics 365 管理センター**ページの **[アプリケーション]** タブには表示されません。
> - Common Data Service starter ポータルは、 **Dynamics 365 管理センター**ページから作成することはできません。
> - テナントでポータルの作成を無効にするには、「[テナントでポータルの作成を無効](create-portal.md#disable-portal-creation-in-a-tenant)にする」を参照してください。

