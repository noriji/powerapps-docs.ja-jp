---
title: Common Data Service | に接続します。Microsoft Docs
description: Common Data Service に接続して、PowerApps でアプリを構築するために使用する方法について説明します。
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: ''
ms.date: 04/22/2019
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 0970cbd51f351352c218dab3f220c6d5baa35435
ms.sourcegitcommit: 0f0b26122be28d674af0833247b491e9367c4932
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2019
ms.locfileid: "73897759"
---
# <a name="connect-to-common-data-service"></a>Common Data Service への接続

ユーザーがデータを管理できるように、Common Data Service にビジネスデータを安全に格納したり、PowerApps でリッチなアプリを構築したりすることができます。 また、そのデータを、Dynamics 365 の電源自動化、Power BI、データなどのソリューションに統合することもできます。

既定では、Common Data Service コネクタは、アプリの現在の環境のデータに接続します。 アプリが別の環境に移動した場合、コネクタは新しい環境のデータに接続します。 この動作は、1つの環境を使用するアプリ、または開発からテスト環境への移行のために ALM プロセスに従うアプリに適しています。

Common Data Service コネクタを使用してデータソースを追加する場合は、環境を変更してから1つまたは複数のエンティティを選択することができます。 既定では、アプリは現在の環境のデータに接続し、UI はエンティティの一覧に対して **(現在)** を表示します。

> [!div class="mx-imgBorder"]
> 既定の環境](media/connection-common-data-service/common-data-service-connection-change-environment.png) の ![

**[変更]** を選択した場合は、現在の環境に加えて、または現在の環境の代わりに、別の環境を使用してデータをプルするように指定できます。

> [!div class="mx-imgBorder"]
> その他の環境の ![](media/connection-common-data-service/common-data-service-connection-select-environment.png)

検索ボックスの下に、選択した環境の名前が表示されます。

> [!div class="mx-imgBorder"]
> 新しい環境の ![](media/connection-common-data-service/common-data-service-connection-after-change-environment.png)

Common Data Service コネクタは、Dynamics 365 コネクタより堅牢で、機能のパリティに近づいています。

詳細情報: [Common Data Service とは何ですか](../../common-data-service/data-platform-intro.md)。
