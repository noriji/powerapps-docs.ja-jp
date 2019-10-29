---
title: ポータルのサーバー側キャッシュをクリアする |MicrosoftDocs
description: ポータルでキャッシュを直ちに更新する方法について説明します。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 8351ca8d3befec80a9e97da03ca62980383b01b1
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/11/2019
ms.locfileid: "72976003"
---
# <a name="clear-the-server-side-cache-for-a-portal"></a>ポータルのサーバー側キャッシュのクリア

ポータルの管理者は、ポータル全体のサーバー側のキャッシュをクリアして、Common Data Service から更新されたデータがポータルにすぐに反映されるようにすることができます。 Common Data Service からの更新は、非同期モードでポータルに伝達されるため、Common Data Service でデータが更新されてから、ポータルに更新されたデータが表示されるまでの間に遅延が発生する可能性があります。 この遅延をなくすには&mdash;たとえば、ポータルの構成との競合が発生したときに、すぐにポータルでキャッシュを更新するように強制することができ&mdash;ます。

> [!NOTE]
> キャッシュ更新の SLA (Common Data Service とポータル間のデータ転送) は15分です。

サーバー側のキャッシュをクリアするには

1.  ポータルに管理者としてサインインします。

2.  次のように URL に移動します。 `<portal_path>/_services/about`

3.  **[キャッシュのクリア]** を選択します。 

サーバー側のキャッシュが削除され、Common Data Service からデータが再読み込みされます。 ポータルサーバー側キャッシュをクリアすると、Common Data Service からデータが再読み込みされている間に、ポータルのパフォーマンスが低下することがあります。

> [!div class=mx-imgBorder]
> ![ポータルキャッシュのクリア](../media/clear-portal-cache.png "ポータルキャッシュのクリア")
