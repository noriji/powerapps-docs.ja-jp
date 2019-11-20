---
title: キャンバス アプリのシステム要件、制限、構成値 | Microsoft Docs
description: PowerApps に組み込まれているキャンバス アプリのシステム要件、制限、構成値
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/30/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 1c8591790fe14d184f5d5e4ef5fc79ff0bfe0e2a
ms.sourcegitcommit: 01fefd7a06bf5d6509acd0bb54ea6479208cbbc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/19/2019
ms.locfileid: "74177893"
---
# <a name="system-requirements-limits-and-configuration-values-for-canvas-apps"></a>キャンバス アプリのシステム要件、制限、構成値
このトピックには、PowerApps についての、デバイス プラットフォーム、Web ブラウザーの要件、制限と構成値が含まれています。

## <a name="supported-platforms-for-running-canvas-apps-using-the-powerapps-app"></a>PowerApps アプリを使用してキャンバス アプリを実行するためにサポートされているプラットフォーム

| **最小構成** | **推奨** |
| --- | --- |
| iOS 12 or later |iOS 12 or later|
| Android 7 or later |Android 7 or later |
| Windows 8.1 以降 (PC のみ) |Windows 10 Fall Creators Update と少なくとも 8 GB の RAM)|

> [!NOTE]
> We currently don't support new features on Windows platform for PowerApps app. Features such as the Improved Common Data Service option and guest access are not available on this platform. We recommend using a web player on Windows to leverage the full set of capabilities. Updates to the PowerApps app for Windows platform will be announced in future.

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
| Brazil | 191.233.203.192 - 191.233.203.207、104.214.19.48 - 104.214.19.63、13.65.86.57、104.41.59.51 |
| カナダ | 13.71.170.208 - 13.71.170.223, 13.71.170.224 - 13.71.170.239, 52.237.24.126, 40.69.106.240 - 40.69.106.255, 52.242.35.152|
| ヨーロッパ | 13.69.227.208 - 13.69.227.223, 52.178.150.68, 13.69.64.208 - 13.69.64.223, 52.174.88.118, 137.117.161.181|
| インド  | 104.211.81.192 - 104.211.81.207, 52.172.211.12, 40.78.194.240 - 40.78.194.255, 13.71.125.22, 104.211.146.224 - 104.211.146.239, 104.211.189.218 |
| 日本 | 13.78.108.0 - 13.78.108.15, 13.71.153.19, 40.74.100.224 - 40.74.100.239, 104.215.61.248 |
| 南米 | 191.233.203.192 - 191.233.203.207、104.214.19.48 - 104.214.19.63、13.65.86.57、104.41.59.51 |
| United Kingdom | 51.140.148.0 - 51.140.148.15、51.140.80.51、51.140.211.0 - 51.140.211.15、51.141.47.105 |
| 米国 | 13.89.171.80 - 13.89.171.95, 52.173.245.164, 40.71.11.80 - 40.71.11.95, 40.71.249.205, 40.70.146.208 - 40.70.146.223, 52.232.188.154, 52.162.107.160 - 52.162.107.175, 52.162.242.161, 40.112.243.160 - 40.112.243.175, 104.42.122.49 |
| 米国 (早期アクセス)  | 13.71.195.32 - 13.71.195.47, 52.161.102.22, 13.66.140.128 - 13.66.140.143, 52.183.78.157 |

## <a name="required-services"></a>必要なサービス
この一覧で、PowerApps Studio が通信するすべてのサービスと用途を確認できます。 ネットワークでこれらのサービスをブロック**しないでください**。

| ドメイン | プロトコル | 使用するサービス |
| --- | --- | --- |
| management.azure.com |https |RP |
| msmanaged-na.azure-apim.net |https |コネクタ/API のランタイム |
| login.microsoft.com<br>login.windows.net<br>login.microsoftonline.com<br>secure.aadcdn.microsoftonline-p.com |https |ADAL |
| graph.microsoft.com<br>graph.windows.net |https |Azure Graph - For getting user info (e.g., profile photo) |
| gallery.azure.com |https |サンプルおよびテンプレート アプリ |
| \*.azure-apim.net |https |API のハブ - ロケールごとに異なるサブドメイン |
| \*.powerapps.com |https | create.powerapps.com, make.powerapps.com, content.powerapps.com, and make.powerapps.com |
| \*.azureedge.net |https | create.powerapps.com, make.powerapps.com, content.powerapps.com, and make.powerapps.com |
| \*.blob.core.windows.net |https | Blob Storage |
| \*.flow.microsoft.com | https | create.powerapps.com, make.powerapps.com, content.powerapps.com, and make.powerapps.com |
| *.dynamics.com | https | Common Data Service |
| vortex.data.microsoft.com |https |製品利用統計情報 |
| localhost | https | PowerApps Mobile

> [!NOTE]
> VPN を使用している場合は、PowerApps Mobile のトンネリングから localhost を除外するように構成する必要があります。

## <a name="size-limits"></a>Size limits

You can find information about size limits on text, hyperlinks, images, and media in [Data types](functions/data-types.md#text-hyperlink-image-and-media).

## <a name="powerapps-per-app-plan"></a>PowerApps per app plan

PowerApps per app plan allows individual users to run 2 applications on a single portal for a specific business scenario based on the full capabilities of PowerApps. This plan provides an easy way for users to get started with the platform before broader scale adoption.

After an admin allocates PowerApps per app plan to an environment, they're assigned to unlicensed users when an app in that environment is shared with them. You can see how an admin allocates per app plans [here](https://docs.microsoft.com/power-platform/admin/capacity-add-on).

Follow these steps to turn off the assigning per app plans for users when an app is shared with them:

- Choose the **App**.
- Select **Settings**.
- Change the **Auto assign per app passes** toggle under **Pass assignment**.

The **Auto assign per app passes** toggle appears in all app setting.

> [!NOTE]
> Disabling the per app plan is currently available for only canvas apps.  Model-driven apps and Portals will have this ability in the future.
>
> The ability to control per app plan assignment for an app is only available for apps that are in an environment that had Per app plans allocated in the [Power Platform Admin center](https://admin.powerplatform.microsoft.com).  

### <a name="app-settings"></a>App Settings

![Canvas app settings](./media/limits-and-config/app_settings.png "Canvas app settings")

### <a name="pass-assignment"></a>Pass assignment

![Canvas app settings pass assignment](./media/limits-and-config/app_settings_pass_assignment.png "Canvas app settings pass assignment")
