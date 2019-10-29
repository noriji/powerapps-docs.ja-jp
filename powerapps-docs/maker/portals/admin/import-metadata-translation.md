---
title: メタデータ変換のインポート |MicrosoftDocs
description: メタデータ変換をインポートする手順。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/21/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: f05a0dfb6424b11e71cf5bf4324d5e3db03a7897
ms.sourcegitcommit: 57b968b542fc43737330596d840d938f566e582a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2019
ms.locfileid: "72977981"
---
# <a name="import-metadata-translation"></a>メタデータ変換のインポート

ポータルをプロビジョニングすると、ポータルに関連するソリューションが組織にインストールされます。 ソリューションのインストール中、ソリューションメタデータの変換 (フィールド名、フォーム名、ビュー名など) は、組織で現在アクティブになっている言語に対してのみインストールされます。 将来、新しい言語を有効にすると、新しくアクティブ化された言語のメタデータは自動的にインストールされません。 新しくアクティブ化された言語のメタデータ変換を取得するには、PowerApps ポータル管理センターからメタデータ翻訳をインポートする必要があります。

## <a name="to-import-metadata-translation"></a>メタデータ変換をインポートするには

1.  [PowerApps ポータル管理センター](admin-overview.md)を開きます。

2.  ポータルの **[アクション]** に移動して、**最新のメタデータ翻訳 > 取得**します。 ポータルソリューションを更新するかどうかを確認する確認ウィンドウが表示されます。

3.  **[更新]** を選択します。 ポータルソリューションは、最新のメタデータ翻訳で更新されます。

> [!Note]
> - ポータルパッケージの最新バージョンが利用可能な場合は、更新されません。 ポータルソリューションは、同じバージョンで更新されます。 利用可能な最新のパッケージに基づいてポータルソリューションをアップグレードするには、ソリューション管理センターにアクセスする必要があります。
> - ユーザーが Common Data Service のデータを変更した場合、既存のデータは更新時に上書きされません。
> - ポータルソリューションがインストールされている場合、ソリューションの更新をトリガーすることはできません。