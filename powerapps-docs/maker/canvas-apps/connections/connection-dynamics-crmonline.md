---
title: Dynamics 365 の接続の概要 | Microsoft Docs
description: Dynamics 365 のデータを管理するためのアプリを作成します
author: Mattp123
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.date: 07/12/2017
ms.author: matp
ms.reviewer: ''
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 48605d97a8b311f806ff3556474d9bc5f32260e1
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2019
ms.locfileid: "73541096"
---
# <a name="connect-to-dynamics-365-from-powerapps"></a>PowerApps から Dynamics 365 に接続する
PowerApps を使うと、ほとんどまたはまったくコードを記述しないで、モバイル アプリをすばやく生成、カスタマイズ、共有、実行することができます。 Dynamics 365 コネクタを使うことにより、組織と共有する便利なモバイル アプリをほんの数分で作成できます。

このトピックでは、ユーザーが Dynamics 365 の連絡先を参照、追加、削除、更新できるアプリを作成する手順について説明します。 ユーザーは、[ブラウザー](../../../user/run-app-browser.md)または携帯電話などの[モバイル デバイス](../../../user/run-app-client.md)で、アプリを実行できます。

## <a name="prerequisite"></a>前提条件
このチュートリアルに従って作業するには、Dynamics 365 サブスクリプションを含む Microsoft Office 365 アカウントが必要です。

## <a name="create-a-connection"></a>接続を作成する
1. [PowerApps にサインインします](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)。
2. 左のナビゲーション ウィンドウで、 **[接続]** をクリックします。
   
    ![[ファイル] メニューの [接続] オプション](./media/connection-dynamics-crmonline/file-connections.png)
3. 右上隅にある **[新しい接続]** をクリックします。
   
    ![新しい接続](./media/connection-dynamics-crmonline/new-connection.png)
4. 接続の一覧で、 **[Dynamics 365]** をクリックまたはタップします。
   
    ![[ファイル] メニューの [接続] オプション](./media/connection-dynamics-crmonline/connection-d365.png)
5. ダイアログ ボックスで、 **[作成]** をクリックします。
   
    ![接続の作成](./media/connection-dynamics-crmonline/create-connection.png)
6. **[Sign in to your account]** (アカウントにサインイン) ダイアログ ボックスで、Dynamics 365 (オンライン) テナントの資格情報を入力します。
   
    接続が作成されます。

## <a name="generate-an-app-automatically"></a>アプリを自動的に生成する
1. [PowerApps にサインイン](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)し、左下隅の **[新しいアプリ]** をクリックします。
   
    ![新しいアプリ](./media/connection-dynamics-crmonline/new-app.png)
2. **[データを使用して開始]** で、 **[Dynamics 365]** タイルの **[携帯電話レイアウト]** をクリックします。
   
    ![PowerApps によって Dynamics 365 コネクタが選択される](./media/connection-dynamics-crmonline/phonelayout.png)
3. **[接続]** で、使う接続を選び、アプリで管理する Dynamics 365 のインスタンスに対応するデータセットを選びます。
4. **[テーブルの選択]** で **[連絡先]** をクリックし、 **[接続]** をクリックします。
5. 左側のナビゲーション バーで、右上のアイコンをクリックまたはタップしてサムネイル表示に切り替えます。
   
    ![表示の切り替え](./media/connection-dynamics-crmonline/toggle-view.png)

PowerApps で、連絡先のレコードに基づいた 3 画面のアプリが生成されます。

* **BrowseScreen1**。 ユーザーがアプリを開くと、この画面が既定で表示されます。 左側のナビゲーション バーでは、他の 2 つの画面の上にこの画面のサムネイルが表示されます。
* **DetailScreen1**。 ユーザーが **BrowseScreen1** でアイテムをクリックすると、この画面が表示されます。  左側のナビゲーション バーでは、他の 2 つの画面の間に **DetailScreen1** のサムネイルが表示されます。
* **EditScreen1**。 ユーザーが **DetailScreen1** でアイテムの編集アイコンをクリックすると、この画面が表示されます。 左側のナビゲーション バーでは、他の 2 つの画面の下に **EditScreen1** のサムネイルが表示されます。

アプリは初期状態のままでも実行できますが、各画面の情報を調整することでさらに便利にできます。

## <a name="customize-browsescreen1"></a>BrowseScreen1 をカスタマイズする
この手順では、各連絡先の姓と名を表示するように **BrowseScreen1** を構成します。 データは姓でアルファベット順に並べ替えられ、2 列のグリッドに画像が表示されます。

1. **BrowseScreen1** で、1 つ目以外の任意のレコードをクリックして、ギャラリーを選びます。
   
    ![レイアウトを選択する](./media/connection-dynamics-crmonline/select-gallery.png)
2. 右側のウィンドウで、 **[データ]** タブをクリックまたはタップします。
3. レイアウトの一覧で、2 列のグリッドに画像とテキストが表示されるレイアウトをクリックまたはタップします。
   
    このオプションを表示するにはスクロールする必要があるかもしれません。
   
    ![レイアウトを選択する](./media/connection-dynamics-crmonline/select-layout.png)
4. 次の式をコピーし、ギャラリーを選択したまま、数式バーに式を貼り付けます ( **[fx]** ボタンの右側)。
   
    `SortByColumns(Search(Filter(Contacts,statuscode=1), TextSearchBox1.Text, "lastname"), "lastname", If(SortDescending1, Descending, Ascending))`
5. 右側のウィンドウで、上のドロップダウン リストを **[firstname]** に設定し、真ん中のドロップダウン リストを **[lastname]** に設定します。
   
    ![Body1 を選択する](./media/connection-dynamics-crmonline/firstname-lastname.png)
6. (省略可能) **[ファイル]** メニューの **[名前を付けて保存]** をクリックし、アプリの名前を入力して、 **[保存]** をクリックします。
   
    既定では、アプリはクラウドに保存されます。 ローカルにアプリを保存するには、 **[このコンピューター]** をクリックします。

## <a name="customize-detailsscreen1-and-editscreen1"></a>DetailsScreen1 と EditScreen1 をカスタマイズする
1. 左側のナビゲーション バーで中央のサムネイルをクリックし、**DetailsScreen1** を選びます。
2. **DetailScreen1** で、タイトル バーの下の任意の箇所をクリックして、右側のウィンドウにカスタマイズ オプションを表示します。
   
    ![フォームのカスタマイズを表示する](./media/connection-dynamics-crmonline/show-customization.png)
3. 右側のウィンドウで、各フィールドの目のアイコンをクリックして、非表示状態にします。
   
    ![フィールドを非表示にする](./media/connection-dynamics-crmonline/hide-field.png)
4. タイトル バーの下の任意の箇所をクリックして、**Form1** を選びます。
   
    ![Form1 を選ぶ](./media/connection-dynamics-crmonline/select-form1.png)
5. 右側のウィンドウで、各フィールドの目のアイコンをクリックして、連絡先ごとに画像 (テーブルに含まれる場合) と他の 4 つのフィールドが表示されるようにします。
   
   * **entityimage**
   * **firstname**
   * **lastname**
   * **mobilephone**
   * **emailaddress1**
     
     右側のウィンドウは次の図のようになります。
     
     ![Form1 を選ぶ](./media/connection-dynamics-crmonline/show-fields.png)
6. 左側のナビゲーション バーで一番下のサムネイルをクリックして、**EditScreen1** を選びます。
7. この手順を繰り返して、**DetailsScreen1** と同じように **EditScreen1** をカスタマイズします。
8. (省略可能) アプリを保存します。

## <a name="next-steps"></a>次の手順
* 左側のナビゲーション バーで **BrowseScreen1** をクリックし、F5 キーを押すか、右上隅の ![プレビュー モード](./media/connection-dynamics-crmonline/runpowerapp.png) をクリックして、プレビュー モードでアプリをテストします。
* [アプリを共有します](../share-app.md)。
* [2 番目のデータ ソースを追加します](../add-data-connection.md)。

