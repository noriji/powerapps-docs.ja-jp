---
title: PowerApps ポータルのライフサイクルについて |MicrosoftDocs
description: PowerApps ポータルのライフサイクルに関する情報と、試用版から運用環境に変換する方法について説明します。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: c2ee82be5526cce41451c8a703971c0f97d32ea0
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/11/2019
ms.locfileid: "72977314"
---
# <a name="about-portal-lifecycle"></a>ポータルのライフサイクルについて

ポータルは常に評価版として作成されます。 30日後に有効期限が切れる試用版ポータルは、その機能を無料で試すのに役立ちます。 有効期限が切れた後、ポータルは中断され、シャットダウンされます。 中断してから7日後に、試用版ポータルが削除されます。 中断、中断、削除、試用から運用への変換など、ポータルのライフサイクルステージが変更されるたびに、トーストおよび電子メールで通知を受け取ります。

管理者は、試用版または中断されたポータルを運用ポータルに変換できます。 試用版ポータルを運用環境に変換するときに、環境が運用環境でもあることを確認します。 試用版のポータルを、試用環境で運用環境に変換することはできません。 試用ポータルが作成されている環境を削除すると、ポータルも削除されます。

最初のポータルは、テナントの環境で自由に作成できます。 複数のポータルを作成する必要がある場合は、テナントに 1 GB の未使用のストレージ領域が必要です。

## <a name="stages-in-portal-lifecycle"></a>ポータルのライフサイクルのステージ

### <a name="trial-portal"></a>試用版ポータル

ポータルは、常に試用版ポータルとして作成されます。 必要なライセンスを持っている場合は、PowerApps ポータル管理センターから運用環境に変換することができます。 試用版ポータルを運用環境に変換する方法については、「[試用版ポータルから運用環境への変換](#convert-a-trial-portal-to-production)」を参照してください。

試用版ポータルを運用環境に変換するには、外部ユーザーのために必要なアドオン、または内部ユーザーのライセンスが必要です。 ライセンスの詳細については、 [powerapps と Microsoft Flow ライセンス](https://docs.microsoft.com/en-us/power-platform/admin/powerapps-flow-licensing-faq)に関する Faq と[powerapps ポータルライセンス](https://docs.microsoft.com/en-us/power-platform/admin/powerapps-flow-licensing-faq#can-you-share-more-details-regarding-the-new-powerapps-portals-licensing)に関する説明を参照してください。

### <a name="suspended-portal"></a>中断されたポータル

引き続き、PowerApps ポータル管理センターで、試用ポータルの有効期限に関する通知が表示されます。 試用版ポータルは30日後に有効期限が切れます。 試用期間内にポータルを運用環境に変換しないと、ポータルがシャットダウンされ、中断状態になります。 有効期限が切れた後、ポータルにアクセスすることはできません。

ただし、中断されたポータルは、中断後7日以内に運用環境に変換することができます。 

### <a name="deleted-portal"></a>削除されたポータル

7日間の中断期間内にポータルを運用環境に変換しないと、ポータルは削除されます。 ポータルデータは環境から削除されませんが、環境内でポータルによって使用される領域は解放され、新しいポータルを作成することができます。

## <a name="convert-a-trial-portal-to-production"></a>試用版ポータルを運用環境に変換する

PowerApps ポータル管理センターに表示される通知から、試用版ポータルを運用環境に変換することができます。

> [!NOTE]
> 試用版ポータルを運用環境に変換するには、次のいずれかのロールが割り当てられている必要があります。
> - 全体管理者
> - システム管理者

[PowerApps ポータル管理センター](admin-overview.md)を開き、[[ポータルの詳細](portal-details.md)] タブに移動すると、 **[種類]** フィールドの下に表示される評価版の有効期限に関する通知が表示されます。

> [!div class=mx-imgBorder]
> ポータルの [![詳細] タブ]の評価版の通知 ((../media/admin-center-convert-notif.png "ポータルの [詳細] タブ"))

管理センターの他のページでは、通知がページの上部に表示されます。

> [!div class=mx-imgBorder]
> 他のタブの評価版の![通知](../media/admin-center-convert-notif-all.png "他のタブでの通知")

試用版ポータルを運用環境に変換するには:

1.  通知で、 **[変換]** を選択します。

2.  **[確認]** を選択します。

    > [!div class=mx-imgBorder]
    > 運用環境の試用版から(../media/trial-to-prod-confirm.png "運用環境への")評価![の]確認
