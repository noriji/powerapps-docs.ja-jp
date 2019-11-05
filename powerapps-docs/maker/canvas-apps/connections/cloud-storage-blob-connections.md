---
title: クラウド ストレージ接続の概要 | Microsoft Docs
description: クラウド ストレージ アカウントに接続し、アプリで Excel データを表示する方法について説明します。
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.date: 07/12/2016
ms.author: lanced
ms.reviewer: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 41536592493a2f17b187829fb778d2a6ca94134a
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2019
ms.locfileid: "73540762"
---
# <a name="connect-to-cloud-storage-from-powerapps"></a>PowerApps からクラウド ストレージに接続する
PowerApps には、クラウド ストレージ接続がいくつか用意されています。 いずれかの接続を利用し、Excel ファイルを保存したり、それに含まれる情報をアプリ全体で利用したりできます。 接続の種類:  

| **Azure Blob** | **Box** | **Dropbox** | **Google ドライブ** | **OneDrive** | **OneDrive<br>for Business** |
| --- | --- | --- | --- | --- | --- |
| ![アイコン](./media/cloud-storage-blob-connections/blobicon.png) |![API アイコン][boxicon] |![API アイコン][dropboxicon] |![API アイコン][googledriveicon] |![API アイコン][onedriveicon] |![API アイコン][onedriveforbusinessicon] |

[!INCLUDE [connection-requirements](../../../includes/connection-requirements.md)]

* データがテーブルとして[書式設定されている Excel ファイル](https://support.office.com/article/Create-an-Excel-table-in-a-worksheet-E81AA349-B006-4F8A-9806-5AF9DF0AC664):
  
  1. Excel ファイルを開き、使用するデータの任意のセルを選択します。
  2. **[挿入]** タブの **[テーブル]** を選択します。
  3. **[Save as Table (テーブルとして保存)]** ダイアログ ボックスで **[My table has headers (先頭行をテーブルの見出しとして使用する)]** チェックボックスを選択し、 **[OK]** を選択します。
  4. 変更を保存します。

## <a name="connect-to-the-cloud-storage-connection"></a>クラウド ストレージ接続に接続する
1. [powerapps.com](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) で、 **[管理]** を展開し、 **[接続]** を選択します。  
   
    ![接続を選択する](./media/cloud-storage-blob-connections/connections.png)
2. **[新しい接続]** を選択し、クラウド ストレージ接続を選択します。 たとえば、 **[OneDrive]** を選択します。
3. クラウド ストレージ アカウントのユーザー名とパスワードが求められます。 それらを入力し、 **[サインイン]** を選択します。  
    ![ユーザー名とパスワードを入力する](./media/cloud-storage-blob-connections/signin.png)
   
    サインインしたら、アプリ内でこの接続を利用できます。
4. アプリ内のリボンの **[ビュー]** タブで、 **[データ ソース]** をクリックまたはタップします。 右側のウィンドウで、 **[データ ソースの追加]** をクリックまたはタップし、使用するクラウド ストレージ接続をクリックまたはタップしてから Excel テーブルを選択します。
5. **[接続]** を選択します。
   
    そのテーブルがデータ ソースとして一覧表示されます。
   
    ![Excel テーブルを選択する](./media/cloud-storage-blob-connections/selecttable.png)
   
    > [!NOTE]
   > Excel データはテーブルとして書式設定されている必要があります。

## <a name="using-the-excel-data-in-your-app"></a>アプリで Excel データを使用する
1. **[挿入]** タブで **ギャラリー**を選択し、**テキスト付き** ギャラリー コントロールを選択します。
2. ギャラリーの **[Items](../controls/properties-core.md)** プロパティを Excel テーブルに設定します。 たとえば、Excel テーブルの名前が **Table1** の場合、Table1 に設定します。  
   
    ![Items プロパティ](./media/cloud-storage-blob-connections/itemsproperty.png)  
   
    ギャラリーは Excel テーブルからの情報で自動的に更新されます。
3. ギャラリーで、2 番目または 3 番目の**ラベル** コントロールを選択します。 既定では、2 番目の **Text** プロパティが表示されます。3 番目のラベルは自動的に `ThisItem.something` に設定されます。 これらのラベルはテーブルの任意の列に設定できます。
   
    次の例では、2 番目のラベルが `ThisItem.Name` に設定され、3 番目のラベルが `ThisItem.Notes` に設定されています。  
   
    ![2 番目のラベル](./media/cloud-storage-blob-connections/items-secondtextbox.png)  
   
    ![3 番目のラベル](./media/cloud-storage-blob-connections/items-thirdtextbox.png)  
   
    サンプル出力:  
    ![2 番目と 3 番目のラベル](./media/cloud-storage-blob-connections/secondthirdtextboxes.png)
   
> [!NOTE]
> 実際には、1 番目のボックスはイメージ コントロールです。 Excel テーブルにイメージがない場合、イメージ コントロールを削除し、その場所にラベルを追加できます。 [コントロールの追加および構成](../add-configure-controls.md)に関する記事をご覧ください。

「[テーブルとレコードについて](../working-with-tables.md)」に詳しい説明といくつかの例があります。  

## <a name="sharing-your-app"></a>アプリの共有
[お客様のアプリ](../share-app.md)、コネクタなどの[リソース](../share-app-resources.md)、お客様の組織内の他のユーザーの[データ](../share-app-data.md)を共有できます。

Dropbox のフォルダーを共有する場合は、共有フォルダーをユーザーの Dropbox アカウントにアタッチする必要があります。

Excel ファイルに関連するコネクタには、[いくつかの制限](#sharing-excel-tables)があります。

## <a name="known-limitations"></a>既知の制限
アプリで Excel 接続を利用しようとしたとき、 **[Data type unsupported (サポートされていないデータ型)]** または **[Not formatted as a table (表として書式設定されていません)]** が表示された場合、[データを表として書式設定](https://support.office.com/article/Create-an-Excel-table-in-a-worksheet-E81AA349-B006-4F8A-9806-5AF9DF0AC664)してください。

Excel データに計算列が含まれる場合、それを利用してアプリを作成することはできません。そのデータを既存のアプリに追加することはできません。

### <a name="sharing-excel-tables"></a>Excel のテーブルの共有
Excel のテーブル内にあるデータを共有する方法:

* OneDrive for Business の場合は、ファイル自体を共有します。
* OneDrive の場合は、メディアの種類にかかわらず、ファイルが含まれているフォルダーを共有し、URL ではなくファイルのパスを指定します。
* Dropbox または Google ドライブの場合は、ファイルまたはフォルダーを共有します。

## <a name="helpful-links"></a>便利なリンク
[利用可能な接続](../connections-list.md)をすべて表示する。  
アプリに[接続](../add-manage-connections.md)と[データ ソース](../add-data-connection.md)を追加する方法を確認する。  
表形式のデータ ソースの[表とレコードを理解する](../working-with-tables.md)。  
「[Show a list of items](../add-gallery.md)」 (アイテムのリストを表示) と「[Show images and text in a gallery](../show-images-text-gallery-sort-filter.md)」 (ギャラリーでイメージとテキストを表示) でも追加のギャラリー リソースを確認できます。

<!--Icon references-->
[boxicon]: ./media/cloud-storage-blob-connections/boxicon.png
[dropboxicon]: ./media/cloud-storage-blob-connections/dropboxicon.png
[googledriveicon]: ./media/cloud-storage-blob-connections/googledriveicon.png
[onedriveicon]: ./media/cloud-storage-blob-connections/onedriveicon.png
[onedriveforbusinessicon]: ./media/cloud-storage-blob-connections/onedriveforbusinessicon.png
