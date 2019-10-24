---
title: Northwind Traders 用キャンバスアプリの概要 |Microsoft Docs
description: ''
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 05/17/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 48966659ca12ada12448543492731fff8431fbde
ms.sourcegitcommit: 57b968b542fc43737330596d840d938f566e582a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2019
ms.locfileid: "71995824"
---
# <a name="overview-of-the-canvas-app-for-northwind-traders"></a>Northwind Traders 用キャンバスアプリの概要

[環境にインストール](northwind-install.md)した Northwind Traders データベースでリレーショナルデータを管理するためのキャンバスアプリについて説明します。 次に、後続のトピックの手順に従って、このアプリを最初から作成します。これにより、リレーショナルデータを操作できるようになります。

このトピックでは、次の項目について説明します。

- アプリユーザーがアプリでリレーショナルデータを表示および管理する方法。
- アプリを駆動するデータの種類。
- これらの種類のデータ間のリレーションシップが作成された方法。

アプリユーザーは、1つの画面で、注文の表示、更新、作成、および削除を行うことができます。

> [!div class="mx-imgBorder"]
> ![Complete キャンバスアプリ ](media/northwind-orders-canvas-part1/orders-finished.png)

## <a name="explore-the-user-interface"></a>ユーザーインターフェイスを調べる

### <a name="order-gallery"></a>注文ギャラリー

アプリの左端にあるギャラリーには、注文番号、状態、顧客の名前、注文の総コストなど、注文の一覧が表示されます。 ユーザーは、リストをスクロールして注文を検索し、注文の矢印を選択してその詳細を表示できます。 詳細につい[ては、「注文書ギャラリーを作成](northwind-orders-canvas-part1.md)する」を参照してください。

### <a name="summary-form"></a>概要フォーム

右上隅のフォームには、注文ギャラリーでユーザーが選択した注文が要約されています。 概要には、ギャラリーと同じ情報の多くが含まれますが、概要には、注文が作成および支払いされた日付と、注文を管理した従業員の名前と画像が表示されます。 ユーザーは、タイトルバーの右端付近にあるアイコンを選択して、フォーム内のデータを変更したり、それらの変更を保存したり、キャンセルしたり、順序を削除したりできます。 詳細情報:[概要フォームを作成](northwind-orders-canvas-part2.md)します。

### <a name="detail-gallery"></a>詳細ギャラリー

右下隅には、選択した注文に含まれる製品とその数量に関する情報が別のギャラリーに表示されます。 このギャラリー内の各アイテムは、注文の詳細として知られています。 アプリユーザーは、その下にあるコントロールを使用して、ギャラリー内の任意の項目を追加および削除できます。 詳細につい[ては、「詳細ギャラリーを作成](northwind-orders-canvas-part3.md)する」を参照してください。

> [!div class="mx-imgBorder"]
> 画面領域の ![Definition ](media/northwind-orders-canvas-part1/orders-parts.png)

## <a name="explore-the-data-sources"></a>データソースを探索する

このアプリを作成するには、5つのエンティティとオプションセットのデータを表示します。 実際、このアプリのほとんどの領域には、複数のエンティティのデータが表示されます。 たとえば、注文ギャラリーには次の情報が含まれています。

- 注文番号は、 **Orders**エンティティ内のフィールドです。
- この状態**は、orders エンティティの**別のフィールドであり、 **orders status**オプションセットのオプションです。
- 顧客名は**Customers**エンティティのフィールドです。
- 合計コストは、 **Order Details**エンティティ内のデータに基づいて計算されます。

概要には、注文の一覧と同じ情報がいくつか含まれていますが、注文を管理した従業員の名前と画像も含まれています。 この情報は、 **Employees**エンティティのフィールドから取得されます。 詳細ギャラリーでは、 **Order Details**エンティティ内のレコードが表示されます。これらの詳細の各製品は、 **order Products**エンティティ内のレコードです。

## <a name="explore-the-relationships"></a>リレーションシップを調べる

同じギャラリーまたはフォーム内の異なるソース (エンティティなど) のデータを表示できます。これらのエンティティには、データベースで作成されたリレーションシップがあるためです。

### <a name="many-to-one-relationships"></a>多対一リレーションシップ

たとえば、顧客と注文ごとの従業員に関する情報は、 **Customers**エンティティと**Employees**エンティティに存在します。 そのため、 **orders**エンティティには、これらのエンティティとの多対一のリレーションシップがあります。これは、注文が多数あり、それぞれが1人の顧客のみが配置でき、1人の従業員だけが管理できるようになるためです。

各注文には、注文に含まれる製品とその数量を表す1つ以上の行アイテムもあります。 各行項目は**Order Details**エンティティ内のレコードで、 **order Products**エンティティから各製品に関する情報を取得します。 それぞれの詳細は1つの製品のみを識別しますが、各製品は複数の詳細に表示できます。 そのため、 **Order Details**エンティティには、 **order Products**エンティティとの多対一のリレーションシップがあります。

### <a name="one-to-many-relationships"></a>一対多のリレーションシップ

各注文には複数の行項目を含めることができますが、各行項目は1つの注文にのみ関連します。 そのため、 **Orders**エンティティには、 **Order Details**エンティティと一対多のリレーションシップがあります。

### <a name="dot-notation-for-relationships"></a>リレーションシップのドット表記 

エンティティ間のリレーションシップに基づいてデータを表示するには、ドットプロパティセレクターを使用して、あるエンティティから別のエンティティへのリレーションシップ間を移動します。  たとえば、 **Orders**エンティティ内の各レコードは**Customers**エンティティから情報を取得するため、注文ギャラリーで顧客名を表示できます。 このギャラリーでは、ラベルの**Text**プロパティを次の式に設定して、この動作を構成します。<br>`ThisItem.Customer.Company`

この**項目**では、 **Orders**エンティティ内のレコードを指定し、注文を行った顧客に関する**Customers**エンティティから情報を取得します。 この場合、式では、顧客の会社名が表示されることを指定します。 ただし、その顧客のレコード全体が引き出されているので、その顧客の電子メールアドレスなどを簡単に表示できます。

あるエンティティから別のエンティティに移動するもう1つの例として、ユーザーが別のギャラリーで選択したレコードと別のエンティティ内のレコードに基づいて、1つのエンティティにレコードを表示するようにギャラリーに指定できます。 注文の詳細を表示するには、詳細ギャラリーの**Items**プロパティを次の式に設定します。<br>`Gallery1.Selected.'Order Details'`

この場合、Gallery1.selected は、前の例で示し**たように**、 **Orders**エンティティ内のレコードを指定し**ます**。 ただし、この式は、前の式と同じレコードを1つだけ取得しません。 代わりに、レコードのテーブル全体を取得して、各製品の名前と単位あたりのコスト (**注文製品**エンティティに反映) と数量 (**注文の詳細**エンティティに反映) を表示します。

## <a name="do-it-yourself"></a>自分で実行する

詳細な手順に従って、Northwind Orders canvas アプリを作成できます。  この手順は、次の3つの部分に分かれています。

1. [注文ギャラリーを作成](northwind-orders-canvas-part1.md)します。
1. [概要フォームを作成](northwind-orders-canvas-part2.md)します。
1. [詳細ギャラリーを作成](northwind-orders-canvas-part3.md)します。

先に進む必要がある場合は、各パーツの開始点アプリがソリューションに含まれています。  アプリの一覧で、 **Northwind Orders (Canvas)** を探します。最初にパート1を開始します。

> [!div class="nextstepaction"]
> [注文ギャラリーを作成して続行する](northwind-orders-canvas-part1.md)
