---
title: Common Data Service | からキャンバスアプリを生成します。Microsoft Docs
description: PowerApps で、データを管理するためのキャンバスアプリを自動的に生成し Common Data Service
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: quickstart
ms.custom: canvas
ms.reviewer: ''
ms.date: 05/06/2018
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 7175ac7d96989de4abd7e9fa3446631ca04d5f1b
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2019
ms.locfileid: "73540141"
---
# <a name="generate-a-canvas-app-from-common-data-service-in-powerapps"></a>PowerApps で Common Data Service からキャンバスアプリを生成する

PowerApps では、 [Common Data Service](../common-data-service/data-platform-intro.md)のサンプルアカウントの一覧に基づいて、キャンバスアプリが自動的に生成されます。 このアプリでは、すべてのアカウントの参照、1 つのアカウントの詳細の表示、アカウントの作成、更新および削除が可能です。

PowerApps にサインアップしていない場合は、始める前に[無料でサインアップ](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)してください。

## <a name="prerequisites"></a>前提条件

このクイックスタートを実行するには、[環境](https://docs.microsoft.com/power-platform/admin/database-security#predefined-security-roles)作成者のセキュリティロールに割り当てられている必要があります。また、Common Data Service 内のデータベースが作成され、データが含まれ、更新が許可されている[環境に切り替える](working-with-environments.md)必要があります。 そのような環境がなく、管理者権限を保持している場合、この要件に合う[環境を作成](https://docs.microsoft.com/power-platform/admin/environments-administration#create-an-environment)します。

## <a name="generate-an-app"></a>アプリを生成する

1. [PowerApps](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) にサインインし、必要に応じて、このトピックで前に説明したように環境を切り替えます。

1. **[Make your own app]\(独自アプリの作成\)** の下の **[Start from data]\(データから開始\)** にポインターを合わせ、 **[このアプリの作成]** を選択します。

    ![アプリを作成するためのオプション](./media/data-platform-create-app/start-from-data.png)

1. **[Common Data Service]** タイルで、 **[電話レイアウト]** を選びます。

    ![接続タイル](./media/data-platform-create-app/connection-tile.png)

1. **[テーブルの選択]** で、 **[アカウント]** を選び、 **[接続]** を選びます。

1. **[PowerApps Studio へようこそ]** ダイアログ ボックスが表示されたら、 **[スキップ]** を選択します。

ブラウザー画面でアプリが開き、ギャラリーと呼ばれるコントロールにアカウントの一覧が表示されます。 画面上部近くのタイトル バーには、ギャラリー内のデータの更新、ギャラリー内のデータのアルファベット順の並べ替え、およびギャラリーへのデータの追加を行うアイコンが表示されます。 オプションで、タイトル バーの下の検索ボックスを使用して、入力または貼り付けたテキストに基づいてギャラリーのデータをフィルタリングできます。 

既定で、ギャラリーにはメール アドレス、市区町村、アカウント名が表示されます。 「[次のステップ](data-platform-create-app.md#next-steps)」を見ていただくとわかるように、ギャラリーをカスタマイズして、データの表示方法を変更したり、他の種類のデータを表示したりすることさえできます。

![ブラウズ画面](./media/data-platform-create-app/browse-screen.png)

## <a name="save-the-app"></a>アプリの保存
このアプリを使用したり、他のユーザーと共有する前に、さらに変更を加えたいことでしょう。 続行する前に、ベスト プラクティスとして作業を保存します。

1. 左上隅にある **[ファイル]** タブを選びます。

1. **[アプリ設定]** ページで、アプリ名を **AppGen** に設定し、背景色を濃い赤に変更し、アイコンをチェック マークに変更します。

    ![アプリの設定ページ](./media/data-platform-create-app/app-settings.png)

1. 左端近くの **[保存]** を選んでから、左下隅の **[保存]** を選びます。

## <a name="next-steps"></a>次の手順
このクイックスタートでは、Common Data Service でアカウントに関するサンプルデータを管理するアプリを作成しました。 次の手順では、ニーズに合わせて既定のブラウザー画面のギャラリーと他の要素をカスタマイズします。

> [!div class="nextstepaction"]
> [ギャラリーをカスタマイズします](customize-layout-sharepoint.md)。
