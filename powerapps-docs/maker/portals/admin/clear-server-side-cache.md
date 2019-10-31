---
title: ポータルのサーバー側キャッシュをクリアする | MicrosoftDocs
description: ポータルで強制的にキャッシュを更新させる指示。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: null
ms.date: 07/18/2019
ms.author: shjais
ms.reviewer: null
---

# <a name="clear-the-server-side-cache-for-a-portal"></a>ポータルのサーバー側キャッシュをクリアにします

[!include[cc-beta-prerelease-disclaimer](../../../includes/cc-beta-prerelease-disclaimer.md)]

ポータル管理者として、Common Data Services からの更新されたデータがポータルにすぐに反映されるよう、ポータル全体のサーバー側キャッシュをクリアできます。 Common Data Services からの更新は非同期モードでポータルに伝えられるので、Common Data Services で更新された時刻のデータおよびポータルで表示される更新されたデータの時刻との間に遅れがあるかもしれません。 この遅延&mdash;を排除するには、例えば、ポータルの構成&mdash;に影響を与える場合、ポータルがキャッシュを迅速に更新するよう強制することができます。

> [!NOTE]
> キャッシュ リフレッシュの SLA (Common Data Services とポータル間のデータ転送) は 15 分です。

サーバー側のキャッシュをクリアする

1.  ポータルに管理者としてサインインします。

2.  次のような URL に移動します: `<portal_path>/_services/about`

3.  **キャッシュのクリア**を選択します。 

サーバー側のキャッシュが削除され、データが Common Data Services から再度読み込まれます。 ポータルのサーバー側キャッシュをクリアすることにより、Common Data Services から再度読み込みをしている間、一時的にポータル パフォーマンスが低下することに注意してください。

> [!div class=mx-imgBorder]
> ![ポータル キャッシュのクリア](../media/clear-portal-cache.png "ポータル キャッシュのクリア")
