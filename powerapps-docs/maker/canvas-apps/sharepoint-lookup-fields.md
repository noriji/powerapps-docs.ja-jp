---
title: キャンバス アプリのルックアップ フィールドを使用して SharePoint リスト間のリレーションシップを作成する | Microsoft Docs
description: PowerApps で、キャンバス アプリのルックアップ フィールドを使用して SharePoint リスト間のリレーションシップを作成します。
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 01/20/2017
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 2c1cce350c394d2809de4c3354b7b471af987236
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2019
ms.locfileid: "73541404"
---
# <a name="how-to-link-sharepoint-lists-using-a-lookup-field-in-powerapps"></a>PowerApps でルックアップ フィールドを使用して SharePoint リストをリンクする方法

このチュートリアルでは、キャンバス アプリのルックアップ フィールドを使用して 2 つの SharePoint リストを関連付ける方法について説明します。

## <a name="overview"></a>概要

SharePoint には、次の 2 種類のルックアップ フィールドがあります。

* **ルックアップ**: 別のリストへのリンクです。たとえば、*Orders* リストには、*Customer* リスト内の顧客にリンクするルックアップ フィールドがあります。
* **選択肢**: フィールドをクリックまたはタップすると小さなメニューが表示され、そこから項目を選択することができます。

このチュートリアルでは、このような種類のルックアップ フィールドを使用するアプリを作成します。

### <a name="why-use-a-lookup-field"></a>ルックアップ フィールドを使用する理由

企業内のデータは大きく複雑です。 SharePoint リスト内のデータは、別のリスト内のデータと関連していることが少なくありません。 ルックアップ フィールドは、そうしたビジネス データを 1 つにまとめる代表的な方法といえます。

たとえば、**Orders** リストのルックアップ フィールドを **Customers** リストにリンクすれば、どの顧客からの注文であるかがわかります。 **Orders** リストのルックアップ フィールドを使うことで、**Customers** リストから他のデータを取得することができるのです。 また、ルックアップ フィールドを使って **Orders** リストを **Product** リストに接続すれば、注文された製品について必要な情報 (製品の写真や仕様、製造元の詳細など) を取り込むこともできます。

### <a name="what-are-choice-fields-used-for"></a>選択肢フィールドの用途
**選択肢**フィールドは、ごく短いリストに使用します。といっても、独立したリストを作成するのではなく、小さなメニューにリストの値を登録しておき、**選択肢**フィールドをクリックまたはタップしたときにこのメニューが表示されるので、いずれかの値を選択します。

顧客のステータス コード、製品の入手可能性、都道府県コードなど、基本的にデータの件数がさほど多くなく、内容も固定的なリストがその用途となります。 実際には、このようなデータを独立したリストとして実装し、**ルックアップ** フィールドを使用してそのリストにリンクすることもできます。ただし、通常は、**選択肢**フィールドとして実装した方が、簡単で手間もかかりません。

## <a name="create-the-lists-in-sharepoint"></a>SharePoint でリストを作成する
このチュートリアルでは、**Assets** と **RepairShop** という 2 つの SharePoint カスタム リストをリンクします。 **Assets** リストの目的は、チームのハードウェア機器を追跡することです。 ハードウェアは故障することがあるので、それを修理できる近隣の業者を **RepairShop** リストで追跡します。

### <a name="the-lookup-fields-used-in-this-example"></a>この例で使用するルックアップ フィールド
**RepairShop** リストでは、業者を識別するためのフィールドとして *ContactEmail* が使用されています。 **Assets** リストの各行で参照する値をあらかじめ用意しておくために、RepairShop リストを先に定義します。

**Assets** リストには 2 つのルックアップ フィールドがあります。

* 1 つは、*RepairShop* という、種類が**ルックアップ**のフィールドです。電子メール アドレスを使用して、**RepairShop** リスト内のエントリを参照します。
* もう 1 つは *AssetType* です。種類が**選択肢**のフィールドで、ハードウェア資産の種類を列挙します。

通常は、これら以外にも、追跡すべき情報に応じてフィールドを定義することになるでしょう。

### <a name="define-the-repairshop-list-and-add-data"></a>RepairShop リストの定義とデータの追加
この作業を最初に行っておくことで、**Assets** リストにデータを追加すると、**RepairShop** のエントリを *Assets.RepairShop* ルックアップ フィールドから選択することができます。

1. SharePoint サイトで、新しい **RepairShop** リストを作成します。

    ![](./media/sharepoint-lookup-fields/new-list.png)

2. **1 行テキスト**という種類の *ContactEmail* フィールドを追加します。

    ![](./media/sharepoint-lookup-fields/add-email-field.png)

3. 他にも必要なフィールドがあれば追加します。

4. **[+ 新規]** をクリックまたはタップして、サンプル データをリストに入力します。少なくとも 3 行は追加しましょう。*ContactEmail* の値が重複しないようにしてください。 資産を修理する必要が生じたとき、このいずれかを選択することになります。

    ![](./media/sharepoint-lookup-fields/add-repair-shops.png)

### <a name="define-the-assets-list"></a>Assets リストの定義
1. SharePoint サイトで、新しい **Assets** リストを作成します。

2. プラス記号をクリックまたはタップし、 **[展開表示]** を選択します。

    ![](./media/sharepoint-lookup-fields/choose-more-type.png)

3. **選択肢**という種類の *AssetType* フィールドを追加し、選択肢メニューに表示する値を **[それぞれの行に選択肢を入力してください]** ボックスに入力します。 その後、 **[OK]** をクリックまたはタップしてください。

    ![](./media/sharepoint-lookup-fields/define-choice-column.png)

4. さらにもう 1 つのフィールドを追加します。手順 2. と同様、プラス記号をクリックまたはタップし、 **[展開表示]** を選択します。

5. **ルックアップ**という種類の *RepairShop* フィールドを追加し、 **[情報の取得先]** ボックスから **[RepairShop]** を選択して、 **[この列]** ボックスから *[ContactEmail]* を選択します。 その後、 **[OK]** をクリックまたはタップしてください。

    ![](./media/sharepoint-lookup-fields/setup-lookup-column.png)

6. 他にも必要なフィールドがあれば追加します。

## <a name="create-an-app-from-the-assets-list"></a>Assets リストからアプリを作成する
このアプリを使用して **Assets** リストにデータを追加します。

1. [PowerApps Studio にサインインします](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)。 PowerApps を初めて利用する場合は、組織の電子メール アドレスを使って[無料でサインアップします](https://powerapps.microsoft.com)。

2. **[ファイル]** メニュー (画面左側) の **[新規]** をクリックまたはタップし、 **[SharePoint]** をクリックまたはタップします。

    ![](./media/sharepoint-lookup-fields/create-app.png)

1. **[最近利用したサイト]** の一覧から SharePoint サイトを選択するか、該当するサイトの URL を直接テキスト ボックスに入力します。 **[移動]** をクリックまたはタップします。

    ![](./media/sharepoint-lookup-fields/choose-sharepoint-site.png)

1. SharePoint サイトからメインのリスト (この例では **Assets**) を選択します。 右下隅の **[接続]** ボタンをクリックまたはタップします。

    ![](./media/sharepoint-lookup-fields/choose-main-list.png)


## <a name="add-data-to-the-assets-list"></a>Assets リストにデータを追加する
ここで、アプリを実行し、詳細の表示画面でルックアップ フィールドがどのように表示されるかを確認することができます。

1. F5 キーを押すか、[プレビュー]\(![](./media/sharepoint-lookup-fields/preview.png)) を選択します。

2. 右上隅にある **+** 記号をクリックまたはタップしてエントリを追加します。

3. この資産の**タイトル**を入力します。

4. **[AssetType]** のドロップダウン矢印をクリックまたはタップします。 表示される値は、このフィールドの作成時に入力した値です。 いずれかのエントリを選択します。

    ![](./media/sharepoint-lookup-fields/fill-asset-type-3.png)

5. **[RepairShop]** のドロップダウン矢印をクリックまたはタップします。 いずれかのエントリを選択します。

    ![](./media/sharepoint-lookup-fields/fill-repair-shop-3.png)

6. 右上隅にあるチェック マークをクリックまたはタップして新しいエントリを保存します。

7. (省略可能) この手順を繰り返して、必要な数だけ項目をリストに追加します。

8. Esc キーを押して既定のワークスペースに戻ります。

## <a name="for-more-information"></a>BLOB の詳細については、
* [ルックアップのサポートと新しいサンプル アプリの紹介](https://powerapps.microsoft.com/blog/support-for-lookups/)
* [パフォーマンス、更新ボタン、ForAll、複数のフィールド ルックアップ](https://powerapps.microsoft.com/blog/performance-refresh-forall-multiple-field-lookups-531/)
* [Common Data Service データベースを使用してアプリを生成する](data-platform-create-app.md)
* [Common Data Service データベースを使用してアプリを最初から作成する](data-platform-create-app-scratch.md)
