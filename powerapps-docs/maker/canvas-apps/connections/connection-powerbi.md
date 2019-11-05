---
title: Power BI の接続の概要 | Microsoft Docs
description: 使用可能な Power BI の接続を参照してください
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/12/2016
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 100b69583593bd506cb6860890ee3dfcfc82ebdf
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2019
ms.locfileid: "73540436"
---
# <a name="connect-to-power-bi-from-powerapps"></a>PowerApps から Power BI に接続する
![Power BI](./media/connection-powerbi/powerbiicon.png)

Power BI は、データを分析し、洞察を共有するビジネス分析用ツール群です。 すべてのデバイスで使用できる豊富なダッシュ ボードで、お客様のビジネスを監視し、すばやく回答を取得します。 アプリでは、Power BI サービスで設定しているデータ アラートの状態を確認できます。 Power BI でのデータ アラートの詳細については、[ドキュメント ページ](https://docs.microsoft.com/power-bi/service-set-data-alerts)を参照してください。

このトピックでは、アプリで Power BI の接続を使用する方法を説明し、使用可能な関数の一覧を表示します。

## <a name="prerequisites"></a>前提条件
* [サインアップ](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)していること
* Power BI の [接続](https://powerapps.microsoft.com/tutorials/add-manage-connections/) を追加していること
* [テンプレート](https://powerapps.microsoft.com/tutorials/get-started-test-drive/)、[データ](https://powerapps.microsoft.com/tutorials/get-started-create-from-data/)、または[ゼロ](https://powerapps.microsoft.com/tutorials/get-started-create-from-blank/)からアプリを作成していること

## <a name="use-the-power-bi-connection-in-your-app"></a>アプリで Power BI の接続を使用する
### <a name="list-the-alerts-that-youve-set-up-in-the-power-bi-service"></a>Power BI サービスで設定したアラートを一覧表示します
1. **[挿入]** メニューで、 **[ギャラリー]** を選択し、 **[テキスト ギャラリー]** のいずれかを追加します。
2. 現在のユーザーのアラートを表示するには、ギャラリーの [[項目]](../controls/properties-core.md) プロパティを次の数式に設定します。

   `PowerBI.GetAlerts()`

ギャラリーは、アラートの一覧で更新されます。 各アラートについて、アラートの名前、アラートの ID 番号、およびアラートが構成されたグループ ワークスペースの ID が表示されます。 アラートの詳細情報を取得するには、アラート ID が必要です。

### <a name="view-the-status-of-an-alert"></a>アラートの状態を表示します
アラートの状態を表示するには、上記の手順から取得したアラート ID で CheckAlertStatus 関数を呼び出します。

アラート ID は、リテラル文字列 (例: "1234") として、または GetAlerts () 呼び出しを使用して設定されるギャラリーセクションへの参照として渡すことができます (例: Gallery1.selected. alertId)。

続行するには、ラベルを追加し、その [[テキスト]](../controls/properties-core.md) プロパティをこれらの数式のいずれかに設定します。

* `PowerBI.CheckAlertStatus( /* alert ID that you received from GetAlert */ ).alertTitle`
* `PowerBI.CheckAlertStatus( /* alert ID that you received from GetAlert */ ).currentTileValue`
* `PowerBI.CheckAlertStatus( /* alert ID that you received from GetAlert */ ).alertThreshold`
* `PowerBI.CheckAlertStatus( /* alert ID that you received from GetAlert */ ).isAlertTriggered`

ラベルは、アラートの現在の状態が更新されます。

## <a name="view-the-available-functions"></a>使用可能な関数の確認
この接続には、次の関数が含まれています。

| 関数名 | Description |
| --- | --- |
| GetAlerts |Power BI サービスで設定したアラートを一覧表示します |
| CheckAlertStatus |特定のアラートの状態を確認します |

## <a name="getalerts"></a>GetAlerts
Power BI サービスで設定したアラートを一覧表示します。

#### <a name="input-properties"></a>入力プロパティ
なし。

#### <a name="output-properties"></a>出力プロパティ

| プロパティ名 | データ型 | 必須 | Description |
| --- | --- | --- | --- |
| 値 |配列 |いいえ |Power BI サービスで設定したデータ アラートの配列。 配列内の各要素は次のものを含みます。 <ul><li>alertTitle: アラートのタイトル</li><li>alertId: アラートの ID</li><li>groupId: アラートが作成されたグループの ID</li></ul> |

## <a name="checkalertstatus"></a>CheckAlertStatus
アラートの状態を確認します。

> [!NOTE]
> このエンドポイントへの要求は、あまり頻繁に呼び出されるとアラートごとに調整されます。

#### <a name="input-properties"></a>入力プロパティ

| プロパティ名 | データ型 | 必須 | Description |
| --- | --- | --- | --- |
| alertId |整数 |はい |GetAlerts によって返される、アラートの ID |

#### <a name="output-properties"></a>出力プロパティ

| プロパティ名 | データ型 | 必須 | Description |
| --- | --- | --- | --- |
| tileValue |数 |いいえ |アラートがトリガーされたときのタイルの値 |
| tileUrl |string |いいえ |アラートがあるタイルの URL |
| alertTitle |string |いいえ |アラートの名前 |
| isAlertTriggered |ブール値 |いいえ |アラートが現在トリガーされているかどうか |
| alertThreshold |数 |いいえ |アラームがトリガーされるしきい値 |

## <a name="helpful-links"></a>便利なリンク
[利用可能な接続](../connections-list.md)をすべて表示する。  
アプリに[接続を追加する](../add-manage-connections.md)方法を確認する。

