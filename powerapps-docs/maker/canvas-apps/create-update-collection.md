---
title: キャンバスアプリでコレクションを作成および更新する |Microsoft Docs
description: キャンバスアプリにコレクションを作成し、コレクションに項目を追加して、そこから1つまたはすべての項目を削除する
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 01/28/2019
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 1c930c233f96a481700748960f90d731be397af0
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2019
ms.locfileid: "73540337"
---
# <a name="create-and-update-a-collection-in-a-canvas-app"></a>キャンバスアプリでのコレクションの作成と更新

コレクションを使用して、ユーザーがアプリで管理できるデータを格納します。 コレクションは、製品リスト内の製品など、類似した項目のグループです。 コレクションなどのさまざまな種類の変数の詳細については[、「キャンバスアプリ変数](working-with-variables.md)について」を参照してください。

## <a name="prerequisites"></a>前提条件

- PowerApps に[サインアップ](../signup-for-powerapps.md)し、サインアップに使用したのと同じ資格情報を入力して[サインイン](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)します。
- PowerApps で、アプリを作成するか既存のアプリを開きます。
- PowerApps で[コントロールを構成する](add-configure-controls.md)方法について確認します。

## <a name="create-a-multicolumn-collection"></a>複数列のコレクションを作成する

1. PowerApps Studio で、**テキスト入力**コントロールを追加します。

    ![テキスト入力コントロールを挿入する](./media/create-update-collection/add-textbox.png)

1. 左側のナビゲーションウィンドウで省略記号を選択し、[名前の**変更**] を選択し、「 **ProductName**」と入力して、コントロールの名前を変更します。

    ![コントロールの名前を変更する](./media/create-update-collection/rename-textbox.png)

1. **ドロップダウン**コントロールを追加します。

    ![ドロップダウンリストの追加](./media/create-update-collection/add-dropdown.png)

1. **ドロップダウン**コントロールの**色**の名前を変更し、プロパティ ボックスの一覧で  **Items** プロパティが選択されていることを確認します。

    ![Items プロパティ](./media/create-update-collection/items-property.png)

1. 数式バーで、 **Dropdownsample**を次の式に置き換えます。

    `["Red","Green","Blue"]`

1. **ボタン**コントロールを追加し、 **Text**プロパティを **"Add"** に設定し、その**onselect**プロパティを次の数式に設定します。

    ```powerapps-dot
    Collect(
        ProductList,
        {
            Product: ProductName.Text,
            Color: Colors.Selected.Value
        }
    )
    ```

1. F5 キーを押して、いくつかのテキストを**ProductName**に入力し、 **[色]** でオプションを選択して、 **[追加]** を選択します。

    ![アプリのプレビュー](./media/create-update-collection/preview-add.png)

1. 前の手順を少なくとも2回繰り返してから、Esc キーを押します。

1. **[ファイル]** メニューの **[コレクション]** をクリックして、作成したコレクションを表示します。

    ![コレクションの表示](./media/create-update-collection/show-collection.png)

## <a name="show-a-collection"></a>コレクションを表示する

1. 縦方向の**ギャラリー**コントロールを追加します。

    ![縦方向のギャラリーの追加](./media/create-update-collection/add-gallery.png)

1. ギャラリーの**Items**プロパティを**productlist**に設定します。

1. **データ**ペインで、サブタイトル] フィールドを **[色]** に設定し、[タイトル フィールドを「 **Product**」に設定します。

    ![ギャラリーの Items プロパティを設定し、表示されるフィールドを変更します。](./media/create-update-collection/configure-gallery.png)

1. **データ**ペインを閉じてギャラリーを選択し、 **[レイアウト]** フィールドを **[タイトルとサブタイトル]** に設定します。

    ![ギャラリーの Items プロパティを設定し、表示されるフィールドを変更します。](./media/create-update-collection/change-layout.png)

    画面は次の例のようになります。

    ![最初の画面の例](./media/create-update-collection/screen-example1.png)

## <a name="remove-one-or-all-items"></a>1つまたはすべての項目を削除する

1. ギャラリーの下部近くをクリックまたはタップし、左上隅にある鉛筆アイコンをクリックまたはタップして、ギャラリーテンプレートを選択します。

    ![ギャラリーテンプレートの選択](./media/create-update-collection/select-template.png)

1. ギャラリーテンプレートに**ごみ箱**アイコンを追加します。

    ![ごみ箱アイコンの追加](./media/create-update-collection/trash-icon.png)

1. アイコンの**Onselect**プロパティを次の数式に設定します。

    `Remove(ProductList, ThisItem)`

1. ギャラリーの外側で、ボタンを追加し、 **Text**プロパティを **"Clear"** に設定し、その**onselect**プロパティを次の数式に設定します。

    `Clear(ProductList)`

1. Alt キーを押したまま、項目の**ごみ箱**アイコンを選択してコレクションから項目を削除するか、 **[クリア]** ボタンを選択してコレクションからすべての項目を削除します。

## <a name="put-a-sharepoint-list-into-a-collection"></a>SharePoint リストをコレクションに挿入する

1. [SharePoint リストへの接続を作成します](connections/connection-sharepoint-online.md#create-a-connection)。

1. ボタンを追加して、その **[OnSelect](controls/properties-core.md)** プロパティをこの関数に設定し、以下の *ListName* を SharePoint リストの名前に置き換えます。<br>

    `Collect(MySPCollection, ListName)`

    この関数では、**MySPCollection** という名前の、SharePoint リストと同じデータを含むコレクションを作成します。

1. Alt キーを押しながら、ボタンを選択します。

1. optional作成したコレクションをプレビューするには、 **[ファイル]** メニューの **[コレクション]** を選択します。

SharePoint リストのデータ (日付、選択肢、people など) をギャラリーに表示する方法の詳細については[、「ギャラリーでリスト列を表示する」](connections/connection-sharepoint-online.md#show-list-columns-in-a-gallery)を参照してください。 フォームにデータを表示する方法 (ドロップダウンリスト、日付のピッカー、および people ピッカー) については、「[フォームコントロールと表示フォームコントロールを編集](controls/control-form-detail.md)する」を参照してください。

## <a name="next-steps"></a>次の手順

- **Collect**関数の[リファレンストピック](functions/function-clear-collect-clearcollect.md)を確認します。
- [Addcolumns、dropcolumns、RenameColumns、および showcolumns](functions/function-table-shaping.md)関数を使用して、コレクション内のデータを整形する方法について説明します。
