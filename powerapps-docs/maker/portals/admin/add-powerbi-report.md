---
title: Power BI レポートまたはダッシュボードをポータルの Web ページに追加 | MicrosoftDocs
description: ポータルの Web ページへ Power BI レポートまたはダッシュボードを追加するための手順。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: null
ms.date: 07/18/2019
ms.author: shjais
ms.reviewer: null
---


# <a name="add-a-power-bi-report-or-dashboard-to-a-web-page-in-portal"></a>Power BI レポートまたはダッシュボードをポータルの Web ページに追加

[!include[cc-beta-prerelease-disclaimer](../../../includes/cc-beta-prerelease-disclaimer.md)]

[powerbi](../liquid/portals-entity-tags.md#powerbi) Liquid タグを使用して、Power BI レポートまたはダッシュボードをポータルの Web ページへ追加できます。 Web ページの**コピー**フィールドまたは Web テンプレートの**ソース**フィールドにタグを追加できます。 Power BI の新しいワークスペースに、作成した Power BI レポートやダッシュボードを追加する場合、認証の種類を powerbi Liquid タグの powerbiembedded として指定する必要があります。

たとえば、次のようなものです。 

```
{% powerbi path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000001/ReportSection01" %}
```

> [!NOTE]
> powerbi Liquid タグの認証の種類として AAD を指定した場合、安全な Power BI レポートやダッシュボードをポータルの Web ページに追加する前に、必要なユーザーと共有する必要があります。 詳細: [Power BI ワークスペースの共有](https://docs.microsoft.com/en-us/power-bi/service-how-to-collaborate-distribute-dashboards-reports#collaborate-with-coworkers-in-an-app-workspace) と [Power BI ダッシュボードとレポートの共有](https://docs.microsoft.com/en-us/power-bi/service-share-dashboards)。

## <a name="get-the-path-of-a-dashboard-or-report"></a>ダッシュボードまたはレポートのパスを取得します。

1.  [Power BI](https://powerbi.microsoft.com/) にサインインします。

2.  ポータルで埋め込むダッシュボードまたはレポートを開きます。

3.  アドレス バーから URL をコピーします。

    > [!div class=mx-imgBorder]
    > ![Power BI ダッシュボードのパスを取得](../media/powerbi-dashboard-url.png "Power BI ダッシュボードのパスを取得")

## <a name="get-the-id-of-a-dashboard-tile"></a>ダッシュボード タイルの ID を取得

1.  [Power BI](https://powerbi.microsoft.com/) にサインインします。

2.  ポータルでタイルを埋め込むダッシュボードを開きます。

3.  タイルをポイントし、**その他のオプション**を選択してから、**フォーカス モードで開く**を選択します。

    > [!div class=mx-imgBorder]
    > ![フォーカス モードで Power BI ダッシュボード タイルを開く](../media/powerbi-dashboard-tile-focus.png "フォーカス モードで Power BI ダッシュボード タイルを開く")

4.  アドレス バーで URL からのタイル ID をコピーします。 タイル ID は /tiles/ の後ろの値です。

    > [!div class=mx-imgBorder]
    > ![Power BI ダッシュボード タイル ID](../media/powerbi-dashboard-tile-id.png "Power BI ダッシュボード タイル ID")


### <a name="see-also"></a>関連項目

[Power BIの Liquid タグ](../liquid/portals-entity-tags.md#powerbi)<br> 
[Power BI 統合の設定](set-up-power-bi-integration.md)
