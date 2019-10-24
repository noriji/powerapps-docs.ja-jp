---
title: キャンバス アプリのシステム要件、制限、構成値 | Microsoft Docs
description: PowerApps に組み込まれているキャンバス アプリのシステム要件、制限、構成値
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/15/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 0ce5218143a8283690cdaf7c1d9be2b1da3d629e
ms.sourcegitcommit: 57b968b542fc43737330596d840d938f566e582a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2019
ms.locfileid: "72393143"
---
# <a name="system-requirements-limits-and-configuration-values-for-canvas-apps"></a>キャンバス アプリのシステム要件、制限、構成値
このトピックには、PowerApps についての、デバイス プラットフォーム、Web ブラウザーの要件、制限と構成値が含まれています。

## <a name="supported-platforms-for-running-canvas-apps-using-the-powerapps-app"></a>PowerApps アプリを使用してキャンバス アプリを実行するためにサポートされているプラットフォーム

| **最小構成** | **推奨** |
| --- | --- |
| iOS 9.3 以降 |iOS 10 以降と少なくとも 2 GB の RAM |
| Android 5 以降 |Android 7 以降と少なくとも 4 GB の RAM |
| Windows 8.1 以降 (PC のみ) |Windows 10 Fall Creators Update と少なくとも 8 GB の RAM)|

> [!NOTE]
> 現在、Windows platform for PowerApps アプリの新機能はサポートされていません。 強化された Common Data Service オプションやゲストアクセスなどの機能は、このプラットフォームでは使用できません。 すべての機能を利用するには、Windows で web プレーヤーを使用することをお勧めします。 Windows プラットフォーム用の PowerApps アプリの更新プログラムは、今後発表される予定です。

## <a name="supported-browsers-for-running-canvas-apps"></a>キャンバス アプリを実行するためにサポートされているブラウザー

| **ブラウザー** | **オペレーティング システム** |
| --- | --- |
| Google Chrome (最新バージョン)<br>(推奨) |Windows 7 SP1、8.1、および 10 <br>Android 5 以降 <br>iOS 8 以降<br>macOS |
| Microsoft Edge (最新バージョン)<br>(推奨) |Windows 10 |
| Microsoft Internet Explorer 11 (互換表示オフ) |Windows 7 SP1、8.1、および 10 |
| Mozilla Firefox (最新バージョン) |Windows 7 SP1、8.1、および 10 <br> Android 5 以降 <br>iOS 8 以降 <br>macOS |
| Apple Safari (最新バージョン) |iOS 8 以降 <br>macOS |

## <a name="supported-browsers-for-powerapps-studio"></a>PowerApps Studio がサポートされているブラウザー

| **ブラウザー** | **オペレーティング システム** |
| --- | --- |
| Google Chrome (最新バージョン)<br>(推奨) |Windows 7 SP1、8.1、および 10 <br>macOS |
| Microsoft Edge (最新バージョン)<br>(推奨) |Windows 10 |
| Microsoft Internet Explorer 11 (互換表示オフ) |Windows 7 SP1、8.1、および 10 |

## <a name="request-limits"></a>要求の制限
次の制限は、1 つの送信要求ごとに適用されます。

| 名前 | 制限 |
| --- | --- |
| タイムアウト |180 秒 |
| 再試行回数 |4 |

> [!NOTE]
> 再試行回数が異なる場合があります。 エラーの状況によっては、再試行は無意味です。

## <a name="ip-addresses"></a>IP アドレス
PowerApps からの要求では、アプリが存在する[環境](../../administrator/environments-overview.md)のリージョンによって、使用する IP アドレスが異なります。 PowerApps のシナリオで利用できる完全修飾ドメイン名は公開されていません。

アプリ経由で接続される API (たとえば、SQL API や SharePoint API) から行われる呼び出しでは、このトピックの後半で説明する IP アドレスを使用します。

たとえば、Azure SQL データベース用に IP アドレスをホワイトリスト登録する必要がある場合は、これらのアドレスを使用する必要があります。

> [!IMPORTANT]
>   既存の構成がある場合は、PowerApps アプリが存在するリージョンについてこの一覧の IP アドレスが追加され、対応付けられるように、2018 年 9 月 30 日の前にできるだけ早く更新してください。

| リージョン | 送信 IP |
| --- | --- |
| アジア | 13.75.36.64 - 13.75.36.79, 13.67.8.240 - 13.67.8.255, 52.175.23.169, 52.187.68.19 |
| オーストラリア  | 13.70.72.192 - 13.70.72.207, 13.72.243.10, 13.77.50.240 - 13.77.50.255, 13.70.136.174 |
| ブラジル | 191.233.203.192 - 191.233.203.207、104.214.19.48 - 104.214.19.63、13.65.86.57、104.41.59.51 |
| カナダ | 13.71.170.208 - 13.71.170.223, 13.71.170.224 - 13.71.170.239, 52.237.24.126, 40.69.106.240 - 40.69.106.255, 52.242.35.152|
| ヨーロッパ | 13.69.227.208 - 13.69.227.223, 52.178.150.68, 13.69.64.208 - 13.69.64.223, 52.174.88.118, 137.117.161.181|
| インド  | 104.211.81.192 - 104.211.81.207, 52.172.211.12, 40.78.194.240 - 40.78.194.255, 13.71.125.22, 104.211.146.224 - 104.211.146.239, 104.211.189.218 |
| 日本 | 13.78.108.0 - 13.78.108.15, 13.71.153.19, 40.74.100.224 - 40.74.100.239, 104.215.61.248 |
| 南米 | 191.233.203.192 - 191.233.203.207、104.214.19.48 - 104.214.19.63、13.65.86.57、104.41.59.51 |
| 英国 | 51.140.148.0 - 51.140.148.15、51.140.80.51、51.140.211.0 - 51.140.211.15、51.141.47.105 |
| 米国 | 13.89.171.80 - 13.89.171.95, 52.173.245.164, 40.71.11.80 - 40.71.11.95, 40.71.249.205, 40.70.146.208 - 40.70.146.223, 52.232.188.154, 52.162.107.160 - 52.162.107.175, 52.162.242.161, 40.112.243.160 - 40.112.243.175, 104.42.122.49 |
| 米国 (早期アクセス)  | 13.71.195.32 - 13.71.195.47, 52.161.102.22, 13.66.140.128 - 13.66.140.143, 52.183.78.157 |

## <a name="required-services"></a>必要なサービス
この一覧で、PowerApps Studio が通信するすべてのサービスと用途を確認できます。 ネットワークでこれらのサービスをブロック**しないでください**。

| ドメイン | プロトコル | 使用するサービス |
| --- | --- | --- |
| management.azure.com |https |RP |
| msmanaged-na.azure-apim.net |https |コネクタ/API のランタイム |
| login.microsoft.com<br>login.windows.net<br>login.microsoftonline.com<br>secure.aadcdn.microsoftonline-p.com |https |ADAL |
| graph.microsoft.com<br>graph.windows.net |https |Azure Graph-ユーザー情報を取得する場合 (例: プロファイル写真) |
| gallery.azure.com |https |サンプルおよびテンプレート アプリ |
| \*。 azure-apim.net |https |API のハブ - ロケールごとに異なるサブドメイン |
| \*。 powerapps.com |https | create.powerapps.com、make.powerapps.com、content.powerapps.com、および web.powerapps.com |
| \*。 azureedge.net |https | create.powerapps.com、make.powerapps.com、content.powerapps.com、および web.powerapps.com |
| \*。 blob.core.windows.net |https | Blob Storage |
| \*。 flow.microsoft.com | https | create.powerapps.com、make.powerapps.com、content.powerapps.com、および web.powerapps.com |
| vortex.data.microsoft.com |https |製品利用統計情報 |
| localhost | https | PowerApps Mobile

> [!NOTE]
> VPN を使用している場合は、PowerApps Mobile のトンネリングから localhost を除外するように構成する必要があります。

## <a name="size-limits"></a>サイズ制限

テキスト、ハイパーリンク、画像、メディアのサイズ制限に関する情報については、「[データ型](functions/data-types.md#text-hyperlink-image-and-media)」を参照してください。

## <a name="powerapps-per-app-plan"></a>アプリプランごとの PowerApps

アプリプランごとの PowerApps を使用すると、個々のユーザーは、PowerApps のすべての機能に基づいて、特定のビジネスシナリオに対して1つのポータルで2つのアプリケーションを実行できます。 このプランでは、大規模なスケーリングを導入する前に、ユーザーが簡単にプラットフォームを使い始めることができます。

管理者がアプリプランごとに PowerApps を環境に割り当てると、アプリがユーザーと共有されるときに、既定でユーザーに割り当てられます。

次の手順に従って、アプリを共有するときにユーザーに割り当てられるアプリごとのプランをオフにします。

- **アプリ**を選択します。
- **[設定]** を選択します。
- **パス割り当て**の下にある **[アプリごとの自動割り当て]** の切り替えを変更します。

**[アプリごとの自動割り当て]** 切り替えは、すべてのアプリ設定で表示されます。

> [!NOTE]
> 現在、アプリごとのプランの無効化は、キャンバスアプリでのみ使用できます。  モデル駆動型アプリとポータルは、今後この機能を利用できるようになります。

### <a name="app-settings"></a>アプリの設定

![キャンバスアプリの設定](./media/limits-and-config/app_settings.png "キャンバスアプリの設定")

### <a name="pass-assignment"></a>パスの割り当て

![キャンバスアプリの設定パスの割り当て](./media/limits-and-config/app_settings_pass_assignment.png "キャンバスアプリの設定パスの割り当て")
