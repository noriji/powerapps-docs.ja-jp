---
title: Excel ファイルに画像を保存する | Microsoft Docs
description: クラウド ストレージ アカウントの Excel テーブルに画像を保存する方法
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 06/15/2016
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 7b6f1056a6d2b5ceaf1fcefe1ccc7d583470450c
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2019
ms.locfileid: "73541718"
---
# <a name="how-to-save-images-in-an-excel-file-and-then-add-these-images-to-your-app"></a>画像を Excel ファイルに保存してアプリに追加する方法

このチュートリアルの内容:

* Excel ファイルを作成してテーブルとして書式設定します。
* OneDrive for Business への接続を作成します。 任意のクラウド ストレージ アカウントが機能します。 このチュートリアルでは、OneDrive for Business を使用します。
* ペン入力コントロールを使ったアプリを作成します。
* ペン入力コントロールから作成した画像を Excel ファイルに保存します。
* Excel ファイルに保存されている画像をアプリで表示します。

[!INCLUDE [app-customization-requirements](../../includes/app-customization-requirements.md)]
* [データ ソースの追加](add-data-connection.md)方法を確認します。

## <a name="create-the-excel-file-as-a-table"></a>Excel ファイルをテーブルとして作成する

1. 空の Excel ファイルで、列に "**Image [image]** " という名前を付けます。
2. 次の手順を使用してテーブルを作成します。    
   
   1. 任意の行の任意の列のデータを選択します。 たとえば、 **[Image]** を選択します。
   2. **[挿入]** リボンの **[テーブル]** を選択します。
   3. ダイアログ ウィンドウで、 **[先頭行をテーブルの見出しとして使用する]** を選択し、 **[OK]** を選択します。
      
      Excel ファイルがテーブル形式になりました。 Excel におけるテーブルの書式設定について詳しくは、[データをテーブルとして書式設定](https://support.office.com/article/Format-an-Excel-table-6789619F-C889-495C-99C2-2F971C0E2370)する方法についてのページを参照してください。
   4. テーブルに、**Drawings** と名前を付けます。  
      
      ![テーブルの名前を Drawings に変更する](./media/tutorial-working-with-images-in-excel/drawings-table.png)
3. Excel ファイルに **SavePen.xlsx** という名前を付けて、ご利用のクラウド ストレージ アカウント (OneDrive for Business、Dropbox など) に保存します。

## <a name="create-an-app-with-the-pen-control"></a>ペン コントロールを使ったアプリを作成する
1. PowerApps で、[空のアプリ](get-started-create-from-blank.md)を作成します。
2. アプリで、クラウド ストレージ アカウントを[データ ソース](add-data-connection.md)として追加します。 データ ソースとして追加したら、**SavePen.xlsx** を接続として追加し、**Drawings** テーブルを選択します。  
   ![接続](./media/tutorial-working-with-images-in-excel/savepen.png)  
   
   Drawings テーブルが、データ ソースとして一覧表示されます。
3. **[挿入]** メニューで、 **[テキスト]** 、 **[ペン入力]** の順に選択します。 名前を **MyPen** に変更します。  
   
   ![名前の変更](./media/tutorial-working-with-images-in-excel/rename-mypen.png)
4. **ボタン** コントロールを追加し ( **[挿入]** メニュー)、その **OnSelect** プロパティを次の数式に設定します。  
   `Patch(Drawings, Defaults(Drawings), {Image:MyPen.Image})`
5. **イメージ ギャラリー** コントロールを追加し ( **[挿入]** メニューの **[ギャラリー]** )、その **Items** プロパティを `Drawings` に設定します。 ギャラリー コントロールの **Image** プロパティが自動的に `ThisItem.Image` に設定されます。
   
   画面は次のようになります。  
   
   ![サンプル画面](./media/tutorial-working-with-images-in-excel/screen.png)  
6. F5 キーを押すか、[プレビュー]\(![](./media/tutorial-working-with-images-in-excel/preview.png)) を選択します。 MyPen で何かを描画し、ボタンを選択します。 ギャラリー コントロールの最初の画像に、描画したものが表示されます。 他の何かを絵に追加して、ボタンを選択します。 ギャラリー コントロールの 2 番目の画像に、描画したものが表示されます。
   
   プレビュー ウィンドウを閉じます。
7. クラウド ストレージ アカウントに移動します。 自動的に作成された新しい **SavePen_images** フォルダーが存在します。 最新の情報に更新しないと新しいフォルダーが表示されない場合があります。 このフォルダーには、それぞれのファイル名の ID が付けられて保存されたイメージが格納されます。
   
    SavePen.xlsx を開きます。 Image 列に、これらの新しい画像のパスが表示されます。

## <a name="add-the-image-in-an-excel-file-to-your-app"></a>Excel ファイル内の画像をアプリに追加する
もう 1 つ例を紹介します。画像をクラウド ストレージ アカウントに保存し、アプリから Excel テーブルを使って画像を表示することができます。

この例では、いくつかの .jpeg ファイルを格納している [CreateFirstApp.zip](https://pwrappssamples.blob.core.windows.net/samples/CreateFirstApp.zip) を使用します。

> [!NOTE]
> Excel ファイルから画像を表示するときは、それらの画像のパスにスラッシュを使う必要があります。 PowerApps で (前の手順のように) 画像を Excel テーブルに保存すると、パスに円記号が使用されます。 前の例で使用した **SavePen_images** を使用することもできますが、 その場合は、円記号ではなくスラッシュを使用するように Excel テーブル内のパスを変更してください。 そうしないと、画像は表示されません。  

1. [CreateFirstApp.zip](https://pwrappssamples.blob.core.windows.net/samples/CreateFirstApp.zip) をダウンロードし、**Assets** フォルダーをクラウド ストレージ アカウントに抽出します。
2. Excel スプレッドシートで、次のようなテーブルを作成します。
   
    ![Jackets テーブル](./media/tutorial-working-with-images-in-excel/jackets.png)
3. テーブルに **Jackets** という名前を付けます。 Excel ファイルに **Assets.xlsx** という名前を付けます。 また、**Assets** フォルダーの名前も **Assets_images** に変更してください。
4. アプリで、データ ソースとして、**Jackets** テーブルを追加します。  
5. **イメージのみ**コントロールを追加し ( **[挿入]** メニューの **[ギャラリー]** )、その **Items** プロパティを `Jackets` に設定します。  
   
    ![Items プロパティ](./media/tutorial-working-with-images-in-excel/items-jackets.png)
   
    ギャラリーがそれらの画像で自動的に更新されます。  
   
    ![ジャケット画像](./media/tutorial-working-with-images-in-excel/images.png)

Items プロパティを設定すると、Excel テーブルが、**PowerAppsId** という新しい列で自動的に更新されます。

Excel テーブル内の画像のパスは、URL になっていてもかまいません。 [Flooring Estimates](https://pwrappssamples.blob.core.windows.net/samples/FlooringEstimates.xlsx) サンプル ファイルをクラウド ストレージ アカウントにダウンロードして、`FlooringEstimates` テーブルをデータ ソースとしてアプリに追加し、ギャラリー コントロールを `FlooringEstimates` に設定してください。 ギャラリーは自動的にイメージで更新されます。

## <a name="learn-more"></a>詳細情報
[画像、ビデオ、またはサウンドを追加する](add-images-pictures-audio-video.md)  
[アプリでデータを折れ線グラフ、円グラフ、棒グラフで表示する](use-line-pie-bar-chart.md)  
[PowerApps におけるテーブルとレコードについて](working-with-tables.md)

