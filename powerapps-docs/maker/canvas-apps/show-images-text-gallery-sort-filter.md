---
title: ギャラリーでのデータの表示、並べ替え、およびフィルター | Microsoft Docs
description: ギャラリーを使って画像やテキストを表示します。 PowerApps で画像の並べ替えとフィルター処理を行います。
author: adrianorth
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 06/02/2015
ms.author: aorth
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 3144f2f6517cbaa641227ff7b2f9482ed1d2e476
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2019
ms.locfileid: "73542451"
---
# <a name="show-sort-and-filter-data-in-a-powerapps-gallery"></a>PowerApps ギャラリーでのデータの表示、並べ替え、およびフィルター
さまざまな製品についての画像やテキストを表示して、その情報を並べ替えたりフィルター処理したりするためのギャラリーを作成します。

PowerApps では、ちょうどカタログで商品を見るときのように、関連性のある項目をギャラリーを使って表示することができます。 商品の名前や価格など、製品に関する情報を表示するうえでギャラリーは最適な手段といえます。 このトピックでは、ギャラリーを作成し、Excel と似た関数を使ってその情報を並べ替えたりフィルター処理したりします。 また、項目が選択されたときに、その周囲に枠線を表示します。

> [!NOTE]
> このトピックでは、タブレット アプリを使用します。 スマートフォン アプリを使うこともできますが、コントロールの一部はサイズ変更が必要となります。
> 
> 

### <a name="prerequisites"></a>前提条件
* PowerApps に[サインアップ](../signup-for-powerapps.md)し、サインアップに使用したのと同じ資格情報で[サインイン](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)します。
* [テンプレート](get-started-test-drive.md)、[データ](get-started-create-from-data.md)、または[ゼロ](get-started-create-from-blank.md)からタブレット アプリを作成します。
* [コントロールを構成する](add-configure-controls.md)方法を確認しておきます。
* これらの手順では、[CreateFirstApp](https://pwrappssamples.blob.core.windows.net/samples/CreateFirstApp.zip) をサンプルの入力データとして使用します (.jpg 画像が含まれています)。 この zip ファイルには、Excel に変換できる XML ファイルが含まれています。 変換できなくても、.zip ファイル内のファイルは PowerApps によって自動的に読み取られ、正常にインポートされます。 このサンプル データをダウンロードして使用することも、独自のデータをインポートすることもできます。

## <a name="show-data-in-a-gallery"></a>ギャラリーのデータの表示
1. サンプル データを使用して、**Inventory** という名前のコレクションを作成します。 手順を次に示します。  
   
   1. **[挿入]** タブで **[コントロール]** を選択し、 **[インポート]** を選択します。
      
      ![][1]  
   2. インポート コントロールの **[OnSelect](controls/properties-core.md)** プロパティを次の数式に設定します。  
      **Collect (Inventory, Import1)**
      
      ![][12]  
   3. **[データのインポート]** ボタンを選択してエクスプローラーを開きます。 *CreateFirstApp.zip* を選択し、 **[開く]** を選択します。
   4. **[ファイル]** メニューの **[コレクション]** を選択します。 Inventory コレクションにインポートしたデータの一覧が表示されます。
      
      ![][3]  
      
      作成した Inventory コレクションには、5 つの商品の情報 (デザイン画像、商品名、在庫数) が含まれています。
      
      > [!NOTE]
      > インポート コントロールの目的は、Excel と同様のデータをインポートしてコレクションを作成することです。 インポート コントロールによってデータがインポートされるのは、アプリの作成時とアプリのプレビュー時です。 現在、アプリの発行時には、データはインポートされません。
      > 
      > 
2. 戻る矢印を選択してデザイナーに戻ります。
3. **[挿入]** タブの **[ギャラリー]** をクリックまたはタップし、 **[水平]** ギャラリーをクリックまたはタップします。
   
    ![][4]
4. 右側のウィンドウで、タイトルとサブタイトルを配置するオプションをクリックまたはタップします。
   
    ![][15]
5. ギャラリーの **[Items](controls/properties-core.md)** プロパティを **Inventory** に設定します。
   
    ![][5]
6. ギャラリーの名前を **ProductGallery** に変更し、他のコントロールの邪魔にならない位置にギャラリーを移動します。 商品が 3 つ表示されるようにギャラリーのサイズを変更します。
   
    ![][6]
7. ギャラリーの最初の項目で、一番下のラベルを選択します。  
   
    ![][7]  
   
   > [!NOTE]
   > ギャラリーで最初の項目を変更すると、ギャラリー内のその他すべての項目が自動的に変更されます。  
   > 
   > 
8. ラベルの **[Text](controls/properties-core.md)** プロパティを次の式に設定します。  
    **この項目は、在庫** <br/>
   
    この設定によって、商品ごとの在庫数がラベルに表示されます。

![][8]  

> [!NOTE]
> 既定では、一番上のラベルの **[Text](controls/properties-core.md)** プロパティが ```ThisItem.ProductName``` に設定されます。 これは、コレクション内の他の項目に変更できます。 たとえば、コレクションに *ProductDescription* フィールドまたは *Price* フィールドがある場合は、ラベルを ```ThisItem.ProductDescription``` または ```ThisItem.Price``` に設定できます。
> 
> 

上記の手順を使用して、.jpg 画像を含むデータをコレクションにインポートしました。 その後、データを表示するギャラリーを追加し、商品ごとの在庫数が表示されるようにラベルを構成しました。

## <a name="highlight-the-gallery-item-you-select"></a>選択したギャラリー項目を強調表示する
1. ギャラリーで、最初の項目 "*以外*" の項目を選択します。 編集アイコンが表示されます (左上隅)。 編集アイコンを選択します。  
   ![][9]  
2. **[挿入]** タブの **[図形]** を選択し、四角形を選択します。 各ギャラリー項目に、青い実線の四角形が表示されます。
3. **[ホーム]** タブの **[塗りつぶし]** を選択し、 **[塗りつぶしなし]** を選択します。
4. **[枠線]** を選択し、 **[枠線の種類]** を選択して、実線を選択します。
5. 再度 **[枠線]** を選択し、太さを 3 に設定します。 ギャラリー項目を囲むように四角形のサイズを変更します。 これでギャラリー内の各項目に青い枠線が設定され、次のように表示されます。  
   ![][10]  
6. **[図形]** タブの **[表示]** を選択し、数式バーに次の数式を入力します。  
   
    **If (IsSelected、true)**
   
    ギャラリーで現在選択されている項目の周囲に青色の四角形が表示されます。 いくつかのギャラリー項目を選択し、選択した各項目の周囲に四角形が表示されることを確認します。 また、 **[プレビュー]** (![][2]) を開いて、作成中のアプリを表示、テストすることもできます。

> [!TIP]
> 四角形を選択し、 **[ホーム]** タブの **[並べ替え]** を選択して、 **[最背面へ移動]** を選択します。 この機能を使うと、ギャラリー項目を選択する際に、枠線が邪魔になりません。
> 
> 

上記の手順を使用して、ギャラリーで現在選択されている項目の周囲に枠線を追加しました。

## <a name="sort-and-filter-items-in-the-gallery"></a>ギャラリーで項目の並べ替えとフィルター処理を実行する
以下の手順では、ギャラリー項目を昇順と降順で並べ替えます。 また、選択した在庫数でギャラリー項目を "フィルター処理" するためのスライダー コントロールを追加します。

#### <a name="sort-in-ascending-or-descending-order"></a>昇順または降順で並べ替える
1. ギャラリーで、最初の項目 "*以外*" の項目を選択します。
2. この時点では、 **[Items](controls/properties-core.md)** プロパティが Inventory (コレクションの名前) に設定されています。 これを次のように変更します。  
   
    **Sort(Inventory, ProductName)**
   
    この操作を実行すると、ギャラリーのアイテムを商品名で昇順に並べ替えます。![][11]  
   
    降順を試してみましょう。 ギャラリーの **[Items](controls/properties-core.md)** プロパティを次の数式に設定します。  
   
    Sort(Inventory, ProductName, Descending)  

#### <a name="add-a-slider-control-and-filter-items-in-the-gallery"></a>スライダー コントロールを追加してギャラリーの項目をフィルター処理する
1. スライダー コントロールを追加 ( **[挿入]** タブの **[コントロール]** ) し、その名前を **StockFilter** に変更して、ギャラリーの下に移動します。
2. ユーザーが在庫数の範囲外の値に設定できないようにスライダーを構成します。  
   
   1. **[Content (内容)]** タブの **[最小値]** を選択し、次の式を入力します。  
      ```Min(Inventory, UnitsInStock)```  
   2. **[Content (内容)]** タブの **[最大値]** を選択し、次の式を入力します。  
      ```Max(Inventory, UnitsInStock)```
3. ギャラリーで、最初の項目 "*以外*" の項目を選択します。 ギャラリーの **[Items](controls/properties-core.md)** プロパティを次の式に設定します。  
   ```Filter(Inventory, UnitsInStock<=StockFilter.Value)```
4. **[プレビュー]** で、ギャラリーの最大数量と最小数量の間の値にスライダーを調整します。 スライダーを調整すると、選択した値より少ない商品だけがギャラリーに表示されます。  
   ![][13]  

さらにフィルターを追加してみましょう。

1. デザイナーに戻ります。
2. **[挿入]** タブの **[テキスト]** を選択し、 **[入力テキスト]** を選択して、新しいコントロールの名前を **NameFilter** に変更します。 テキスト コントロールをスライダーの下に移動します。
3. ギャラリーの **[Items](controls/properties-core.md)** プロパティを次の式に設定します。  
   ```Filter(Inventory, UnitsInStock<=StockFilter.Value && NameFilter.Text in ProductName)```
4. **[プレビュー]** で、スライダーを *30* に設定し、入力テキスト コントロールにアルファベットの「*g*」を入力します。 ギャラリーには、在庫数が 30 未満で、"*かつ*" 名前にアルファベットの "g" を含む商品のみが表示されます。  
   ![][14]  

## <a name="tips-and-tricks"></a>ヒントとコツ
* 作成した内容は、いつでもプレビュー ボタン (![][2]) を選択して表示し、テストすることができます。
* アプリの設計時に、コントロールのサイズを変更したり、クリック アンド ドラッグでコントロールを移動したりできます。
* プレビュー ウィンドウを閉じるには、**Esc** キーを押すか、 **[X]** を選択します。
* ギャラリーの使用時に、すべてのギャラリー項目に変更を加えるには、ギャラリーの先頭の項目を選択します。 たとえば、最初の項目を選択して、ギャラリーのすべての項目に枠線を追加します。
* ギャラリーのプロパティを更新するには、ギャラリーの最初の項目 "*以外*" のいずれかの項目を選択します。 たとえば、2 つ目の項目を選択して、*Items* や *ShowScrollbar* など、(ギャラリー内の項目ではなく) ギャラリー自体に適用するプロパティを更新します。  

## <a name="what-you-learned"></a>学習した内容
このトピックでは次の操作を行いました。

* コレクションを作成し、.jpg 画像を含むデータをそのコレクションにインポートして、そのデータをギャラリーに表示しました。
* ギャラリーの各画像の下に、その項目の在庫数を表示するラベルを構成しました。
* 選択した項目の周囲に枠線を追加しました。
* 項目を商品名の昇順と降順で並べ替えました。
* 商品を在庫数と商品名でフィルタ―処理するためにスライダー コントロールと入力テキスト コントロールを追加しました。

[1]: ./media/show-images-text-gallery-sort-filter/import.png
[2]: ./media/show-images-text-gallery-sort-filter/preview.png
[3]: ./media/show-images-text-gallery-sort-filter/inventorycollection.png
[4]: ./media/show-images-text-gallery-sort-filter/insert-vertical.png
[5]: ./media/show-images-text-gallery-sort-filter/itemsinventory.png
[6]: ./media/show-images-text-gallery-sort-filter/threeimages.png
[7]: ./media/show-images-text-gallery-sort-filter/firstitem.png
[8]: ./media/show-images-text-gallery-sort-filter/bottomlabel.png
[9]: ./media/show-images-text-gallery-sort-filter/editgallery.png
[10]: ./media/show-images-text-gallery-sort-filter/border.png
[11]: ./media/show-images-text-gallery-sort-filter/sort.png
[12]: ./media/show-images-text-gallery-sort-filter/onselect.png
[13]: ./media/show-images-text-gallery-sort-filter/slider.png
[14]: ./media/show-images-text-gallery-sort-filter/inputandslider.png
[15]: ./media/show-images-text-gallery-sort-filter/select-overlay.png
