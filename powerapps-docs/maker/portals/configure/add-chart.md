---
title: ポータルでの web ページへのグラフの追加 |MicrosoftDocs
description: モデル駆動型アプリで作成されたグラフをポータルの web ページに追加する方法について説明します。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 3cc2e390b988689e9a21317d80aa7d94d2ea9e6d
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2019
ms.locfileid: "73553879"
---
# <a name="add-a-chart-created-in-a-model-driven-app-to-a-webpage-in-portal"></a>モデル駆動型アプリで作成されたグラフをポータルの web ページに追加する

グラフを web ページに追加するには、[グラフ](../liquid/portals-entity-tags.md#chart)という液体を使用します。 グラフの液体タグは、Web ページの **[コピー]** フィールドまたは[Web テンプレート](../liquid/store-content-web-templates.md)の **[ソース]** フィールドに追加できます。
 
たとえば、{% chart id: EE3C733D-5693-DE11-97D4-00155DA3B01E%}

![グラフの例](../media/dynamics365-chart-example.png "グラフの例")

ビューの ID (保存されているクエリ) を指定して、クエリをフィルター処理することもできます。 例:

<!—Leads by Source – Open Leads -->

{% chart id: "EE3C733D-5693-DE11-97D4-00155DA3B01E" viewid: "00000000-0000-0000-00AA-000010001006"%}

## <a name="get-the-id-of-a-chart"></a>グラフの ID を取得する

1.  ターゲットエンティティ (たとえば、 **Sales** > **潜在顧客**) に移動します。
2.  **[グラフ]** 領域を展開します。
3.  目的のグラフを選択します。
4.  **[その他のコマンド]** を選択し、 **[グラフのエクスポート]** を選択します。

    ![グラフをエクスポートする](../media/export-dynamics365-chart.png "グラフをエクスポートする")

5. エクスポートされたグラフの XML ファイルをテキストエディターで開きます。
6. \<visualizationid\> タグの値をコピーします。

    ![グラフの chartid を取得します。](../media/dynamics365-chart-chartid.png "グラフのグラフ ID を取得する")

7. 次の例のように、visualizationid の値をグラフ ID パラメーターの液体チャートタグ宣言に貼り付けます。

    {% chart id: EE3C733D-5693-DE11-97D4-00155DA3B01E%}。

## <a name="get-the-id-of-a-view"></a>ビューの ID を取得します。

表示エディターを開いて、液体チャートタグと共に使用するビュー ID を取得する必要があります。
 
1.  ターゲットエンティティ (たとえば、 **Sales** > **潜在顧客**) に移動します。
2.  [ビュー] ドロップダウンヘッダーから目的のビューを選択します。
3.  ツールバーの **[表示]** を選択します。 [表示] ウィンドウが開きます。

    ![ビューエディターで潜在顧客を表示する](../media/dynamics365-chart-view.png "ビューエディターで潜在顧客を表示する")

4. [ビュー] ウィンドウの URL から**id**値をコピーします。

    ![ビューエディターからビュー id を取得する](../media/dynamics365-chart-viewid.png "ビューエディターからビュー ID を取得する")

5. この ID を viewid パラメーターの液体チャートタグ宣言に貼り付けます。次に例を示します。

    <!—Leads by Source – Open Leads -->

    {% chart id: "EE3C733D-5693-DE11-97D4-00155DA3B01E" viewid: "00000000-0000-0000-00AA-000010001006"%}

## <a name="entity-permission-requirement"></a>エンティティのアクセス許可の要件

グラフでクエリ対象のエンティティに対して読み取り権限がアサートされます。 匿名ユーザーまたは認証済みユーザーがグラフを表示できるようにするには、適切な[エンティティアクセス許可](assign-entity-permissions.md)レコードが作成され、該当する[web ロール](create-web-roles.md)に割り当てられていることを確認する必要があります。 
 
アクセス許可が付与されていない場合、ユーザーにはアクセス拒否メッセージが表示されます。

## <a name="unsupported-charts-and-chart-types"></a>サポートされていないグラフとグラフの種類

次のグラフの種類は、現在、ポータルではサポートされていません。
- ドーナツ
- 番号

次の表に、ポータルで現在サポートされていないグラフを示します。

| グラフ名                              | グラフ ID                             | エンティティ型      |
|-----------------------------------------|--------------------------------------|------------------|
| オーナータググラフによるアカウント           | be178262-6142-4b41-85b7-4ccedc62cfd9 | 顧客          |
| オーナータググラフによるアクティビティ         | c83b331e-87c7-488c-b8e7-89a6098ea102 | activitypointer  |
| 優先順位別アクティビティ-ドーナツグラフ | d3f6c1eb-2e4b-428b-8949-682a311ae057 | activitypointer  |
| アカウント別の連絡先                     | 2ff3ebea-6310-4dde-b3a1-e1144ea42b7b | 接点          |
| 国別の連絡先                     | ea89e2ad-2602-4333-8724-aa5775d66b77 | 接点          |
| 優先連絡方法別の連絡先    | 751b7456-308e-4568-a3a9-47135aae833a | 接点          |
| 目標の進行状況 (カウント)                   | a93b8f7b-9c68-df11-ae90-00155d2e3002 | goal             |
| 目標の進行状況 (Money)                   | aec6d51c-ea67-df11-ae90-00155d2e3002 | goal             |
| 今日のターゲットと実績 (カウント)      | 1b697c8e-9a6f-df11-986c-00155d2e3002 | goal             |
| 今日のターゲットと実績 (Money)      | 1e697c8e-9a6f-df11-986c-00155d2e3002 | goal             |
| アカウント別のケース                        | 38872e4f99-e511-80da-00155dc1b253 | incident         |
| 優先度別のケース                       | 0f0fb995-9d6f-453c-b26d-8f443e42e676 | incident         |
| 製品別のケース                        | 17c3f166-5b22-4476-819b-b05da2e8d24f | incident         |
| この月の所有者の期限が切れる記事   | 47d696ad-7c3b-e511-80d1-00155db10d2b | knowledgearticle |
| 所有者別                                | 330068fd833be511-80d1-00155db10d2b | knowledgearticle |
| 件名別                              | bcd3f9a5-913b-e511-80d1-00155db10d2b | knowledgearticle | 
| | |
