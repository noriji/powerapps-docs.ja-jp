---
title: ポータルで web ページに Power BI レポートまたはダッシュボードを追加する |MicrosoftDocs
description: ポータルの web ページに Power BI レポートまたはダッシュボードを追加する方法について説明します。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 3735a0ef1a26fdd19b7bfb7f6db717cf9bd07861
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/11/2019
ms.locfileid: "72976164"
---
# <a name="add-a-power-bi-report-or-dashboard-to-a-web-page-in-portal"></a>ポータルで Web ページに Power BI レポートまたはダッシュボードを追加する

[Powerbi](../liquid/portals-entity-tags.md#powerbi)液体タグを使用すると、ポータルの web ページに Power BI レポートまたはダッシュボードを追加できます。 タグは、web ページの **[コピー]** フィールド、または web テンプレートの **[ソース]** フィールドに追加できます。 Power BI の新しいワークスペースで作成された Power BI レポートまたはダッシュボードを追加する場合は、認証の種類として powerbi 液体タグに powerbiembedded を指定する必要があります。

例: 

```
{% powerbi path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000001/ReportSection01" %}
```

> [!NOTE]
> Powerbi 液体タグの認証の種類として AAD を指定した場合は、セキュリティで保護された Power BI レポートまたはダッシュボードをポータルの web ページに追加する前に、必要なユーザーと共有する必要があります。 詳細については、「 [Power BI ワークスペースの共有](https://docs.microsoft.com/power-bi/service-how-to-collaborate-distribute-dashboards-reports#collaborate-with-coworkers-in-an-app-workspace)」と「[ダッシュボードとレポートの共有 Power BI](https://docs.microsoft.com/power-bi/service-share-dashboards)」を参照してください。

## <a name="get-the-path-of-a-dashboard-or-report"></a>ダッシュボードまたはレポートのパスを取得する

1.  [Power BI](https://powerbi.microsoft.com/)にサインインします。

2.  ポータルに埋め込むダッシュボードまたはレポートを開きます。

3.  アドレスバーから URL をコピーします。

    > [!div class=mx-imgBorder]
    > ![Power BI ダッシュボードのパスを取得]する(../media/powerbi-dashboard-url.png "Power BI ダッシュボードのパスを取得")する

## <a name="get-the-id-of-a-dashboard-tile"></a>ダッシュボードタイルの ID を取得します

1.  [Power BI](https://powerbi.microsoft.com/)にサインインします。

2.  ポータルにタイルを埋め込むダッシュボードを開きます。

3.  タイルをポイントし、 **[その他のオプション]** を選択し、 **[フォーカスモードで開く]** を選択します。

    > [!div class=mx-imgBorder]
    > フォーカス![モードでダッシュボードタイルを開く Power BI](../media/powerbi-dashboard-tile-focus.png "フォーカスモードで Power BI ダッシュボードタイルを開く")

4.  アドレスバーの URL からタイル ID をコピーします。 タイル ID は/tiles/. の後の値です。

    > [!div class=mx-imgBorder]
    > ダッシュボードタイル id(../media/powerbi-dashboard-tile-id.png "Power BI")ダッシュボードタイル id の![Power BI]


### <a name="see-also"></a>関連項目


[powerbi 液体タグ](../liquid/portals-entity-tags.md#powerbi)<br>[Power BI 統合](set-up-power-bi-integration.md)のセットアップ  

