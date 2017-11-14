---
title: "Common Data Service エンティティの詳細 | Microsoft Docs"
description: "ビジネス データとプロセスをマップするエンティティを定義して使用します"
services: 
suite: powerapps
documentationcenter: na
author: mgblythe
manager: anneta
editor: 
tags: 
featuredvideoid: JJa6n_YaD-w
courseduration: 8m
ms.service: powerapps
ms.devlang: na
ms.topic: get-started-article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 12/09/2016
ms.author: mblythe
ms.openlocfilehash: 3239a2c90edcd4274f9fabbbb47bd110c3ebcee6
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/07/2017
---
# <a name="understand-entities"></a>エンティティについて
このセクションの最初のトピックでは、Common Data Service について説明しました。Common Data Service には共通のデータ モデルが含まれています。 モデルにはエンティティが含まれています。 エンティティは共有データのチャンクで、変更、保存、取得、および対話することができます。 このトピックでは、エンティティ、フィールド、およびデータ型について詳しく説明します。

## <a name="standard-entities"></a>標準エンティティ
共通のデータ モデルには、さまざまな一般的なビジネス ニーズに対応する標準エンティティのセットが付属しています。 標準エンティティの一部を以下に示します。

![Common Data Service の標準エンティティ](./media/learning-common-data-service-entities/standard-entities.png)

エンティティはカテゴリ別に分類されているので、ソリューション内で通常連動するエンティティを簡単に確認できます。

| 機能グループ | 説明 |
| --- | --- |
| Customer Service |Customer Service のエンティティを使用して、顧客から寄せられた問題について、追跡、エスカレーション、文書化などの管理を行うことができます。 |
| Foundation |Foundation のエンティティには、他のエンティティ グループのほぼすべてに関連する情報が含まれます。 このグループには、住所や通貨などのエンティティが含まれています。 |
| People、Organizations、Groups |これらのエンティティには、従業員、契約社員、寄贈者、ボランティア、ファン、同窓生、家族など、やり取りする可能性のある人や組織の豊富なセットが含まれています。 |
| Purchasing |Purchasing のエンティティを使用して、購入ソリューションを作成できます。 |
| セールス |Sales のエンティティを使用して、潜在顧客と案件の追跡から、連絡先の管理、注文の受け付けと配送、請求書の送信まで、エンド ツー エンドのセールス ソリューションを作成できます。 |

## <a name="fields-and-data-types"></a>フィールドとデータ型
各エンティティには、変更や削除ができない既定のフィールドのセットが含まれています。 そうしたフィールドの一部 (**Contact ID** (連絡先 ID) など) はエンティティに固有のフィールドです。 それ以外 (**Created on date time** (作成日時) など) はすべてのエンティティに共通のフィールドです。 標準エンティティは、フィールドを追加することで拡張できます。 **[Add field]** (フィールドの追加) をクリックまたはタップして、新しいフィールドのプロパティを指定するだけです。

![Contact (連絡先) エンティティのフィールドとデータ型](./media/learning-common-data-service-entities/contact-entity-fields.png)

まったく異なるエンティティが必要 (標準エンティティの拡張では不十分) な場合は、カスタム エンティティを作成します。 カスタム エンティティの作成については、次のトピックで説明します。

エンティティの各フィールドは、Number などのデータ型を持っています。 単一の汎用データ型ではなくさまざまなデータ型があれば、アプリですばらしい処理を行うことができるので、便利です。 たとえば、Number 型のフィールドを使用する場合は、ユーザーがそのフィールドを編集するときに、アプリでスライダー コントロールを使用できます。 12 種類以上のデータ型から選択することができます。次の一覧に代表的な型をいくつか示します。

* 基本的な型。Text、Number など
* より複雑な型。Email、Phone など
* 特殊な型。Lookup (リレーションシップを作成する)、Picklist (フィールドの固定値セットを保持する) など  

## <a name="working-with-entities"></a>エンティティの操作
エンティティを開くと、多くの情報といくつか実行できる操作が表示されます。 使用可能なタブと、エンティティ データを管理するために実行できるアクションを簡単に確認しましょう。

![エンティティのタブ](./media/learning-common-data-service-entities/entity-tabs.png)

* **Fields (フィールド)**: 「フィールドとデータ型」と「フィールドの追加」を参照してください。これらはすべて上記の説明の通りです。
* **Key (キー)**: エンティティ内の各行を識別するフィールド。Contact (連絡先) エンティティの Contact ID (連絡先 ID) など。
* **Relationships (リレーションシップ)**: 関連するエンティティ間のつながり。Product (製品) と Product category (製品カテゴリ) など。 この例は次のトピックで確認します。
* **Field groups (フィールド グループ)**: さまざまな動作を制御するために使用します。PowerApps でアプリの画面を作成するときに自動的に表示するフィールドなど。
* **Data (データ)**: サンプル データと、インポート後の独自のデータを参照します。

![エンティティのアクション](./media/learning-common-data-service-entities/entity-actions.png)

* **Open in Excel (Excel で開く)**: PowerApps アドインをインストールしてある場合は、このオプションを使って Excel でデータを表示して編集します。
* **Import data (データのインポート)**: Excel および CSV ファイルからデータを取り込みます。
* **Export data (データのエクスポート)**: データを Excel ファイルにエクスポートします。
* **Export template (テンプレートのエクスポート)**: ファイルを作成し、エンティティにインポートして戻せるように、エンティティの構造を Excel ファイルにエクスポートします。
* **Settings (設定)** と **Delete (削除)**: 標準エンティティでは利用できません。

## <a name="connecting-to-a-standard-entity-in-powerapps-studio"></a>PowerApps Studio での標準エンティティの接続
エンティティとはどういうものか理解したところで、PowerApps Studio で Contact (連絡先) エンティティに接続する方法を見てみましょう。 **[New]** (新規) をクリックして、**[Common Data Service]** の下の **[Phone layout]** (電話レイアウト) をクリックします。 左側に使用できるデータ接続、右側にエンティティのリストが表示されます。 自力で接続して、エンティティからアプリを生成してみてください。

![PowerApps Studio でエンティティに接続する](./media/learning-common-data-service-entities/connect-to-standard-entity.png)

次のトピックでは、カスタム エンティティとエンティティ間のリレーションシップを作成する方法について説明します。
