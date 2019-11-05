---
title: テンプレートを操作する |Microsoft Docs
description: ポータルでテンプレートを操作する方法について説明します。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 207a1abdfc8145c38b8d6222f71281ce714e8947
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2019
ms.locfileid: "73542385"
---
# <a name="work-with-templates"></a>テンプレートを操作する

組み込みテンプレートは、プロビジョニングしたポータルに応じて利用できます。 テンプレートを編集するには、コードエディターを使用します。 たとえば、Common Data Service starter ポータルをプロビジョニングするときに使用できる組み込みテンプレートは次のとおりです。

- 既定の studio テンプレート
- タイトル付きページ
- 子リンクがあるページ


> [!NOTE]
> **既定の studio テンプレート**、**プロファイル**、および**検索**テンプレートを編集しないことをお勧めします。

コードエディターでテンプレートを開くには、次のようにします。

1.  [ポータルを編集](manage-existing-portals.md#edit)して PowerApps ポータル Studio で開きます。  

2.  画面の左側にある toolbelt から [**テンプレート**![テンプレート] アイコン](media/templates-icon.png "テンプレートアイコン")を選択します。 使用可能なテンプレートが表示されます。  

    > [!div class=mx-imgBorder]
    > ![テンプレートペイン](media/templates-pane.png "テンプレートペイン")  

3.  コードエディターで開くには、必要なテンプレートを選択します。

4.  コードを編集し、変更を保存します。

> [!NOTE]
> - また、詳細な構成のために、ソースコードエディターで液体タグを追加することもできます。 詳細情報:[水冷テンプレートの使用](liquid/liquid-overview.md)
> - [ポータル管理アプリ](configure/configure-portal.md)を使用して作成したページテンプレートは、 **[テンプレート]** ウィンドウにも表示されます。
