---
title: リスト ボックス、ドロップダウン リスト、またはラジオ ボタンをキャンバス アプリに追加する | Microsoft Docs
description: PowerApps で、キャンバス アプリに複数選択オプションを作成または構成する
author: fikaradz
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/24/2018
ms.author: fikaradz
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 211a5be4a97780a440bf151157576a5ab56933a5
ms.sourcegitcommit: 57b968b542fc43737330596d840d938f566e582a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2019
ms.locfileid: "71987491"
---
# <a name="add-a-list-box-a-drop-down-list-or-radio-buttons-to-a-canvas-app"></a>リスト ボックス、ドロップダウン リスト、またはラジオ ボタンをキャンバス アプリに追加する

キャンバス アプリで (たとえば複数列テーブルから) 1 つの列のデータを表示し、ユーザーが一覧の項目を 1 つまたは複数選択できるようにします。

- リスト ボックスを追加して、ユーザーが複数のオプションを選択できるようにします。
- ドロップダウン リストを追加して、必要な画面領域を小さくします。
- 特定のデザイン効果のために、一連のラジオ ボタンを追加します。

このトピックではリスト ボックスとラジオ ボタンに焦点が当てられていますが、ドロップダウン リストにも同じ原則を適用できます。

[!INCLUDE [app-customization-requirements](../../includes/app-customization-requirements.md)]

## <a name="create-a-simple-list"></a>単純なリストを作成する

1. **リスト ボックス** コントロールを追加して **MyListBox** という名前を付け、その **Items** プロパティを次の式に設定します。

    ```["circle","triangle","rectangle"]```  <br/>

    デザイナーは次のようになります。

    ![][4]

4. **[挿入]** タブで **[アイコン]** を選択し、円を選択し、それを **MyListBox** の下に移動します。

    ![][5]  

5. 三角形と四角形を追加し、**MyListBox** の下に図形を並べます。

    ![][6]  

6. 次の図形の **[Visible](controls/properties-core.md)** プロパティを次の関数に設定します。  

   | 図形 | 設定する Visible 関数 |
   | --- | --- |
   | 円 |```If("circle" in MyListBox.SelectedItems.Value, true)``` |
   | 三角形 |```If("triangle" in MyListBox.SelectedItems.Value, true)``` |
   | 四角形 |```If("rectangle" in MyListBox.SelectedItems.Value, true)``` |

7. Alt キーを押しながら、**MyListBox** 内の図形を 1 つまたは複数選択します。

    選択した図形のみが表示されます。

以上の手順では、式を利用して項目リストを作成しました。 これは自分の作業内の他の要素に適用できます。 たとえば、**ドロップダウン** コントロールを利用し、製品の画像や説明などを表示できます。

## <a name="add-radio-buttons"></a>ラジオ ボタンを追加する
1. **[ホーム]** タブの **[新しい画面]** を選択し、 **[空白]** を選択します。

2. **[挿入]** タブで **[コントロール]** を選択し、**ラジオ** を選択します。

    ![][10]  

3. **ラジオ** コントロールの名前を **Choices** に変更し、その **[Items](controls/properties-core.md)** プロパティをこの式に設定します。  
   ```["red","green","blue"]```  <br/>

    ![][12]  

    必要に応じて、すべてのオプションが表示されるようにコントロールのサイズを変更します。

4. **[挿入]** タブで **[アイコン]** を選択し、円を選択します。

5. 円の **[Fill](controls/properties-color-border.md)** プロパティを次の関数に設定します。  
   ```If(Choices.Selected.Value = "red", Red, Choices.Selected.Value = "green", Green, Choices.Selected.Value = "blue", Blue)```  

    この数式では、選択したラジオ ボタンに基づいて円の色が変わります。

6. この例のように **ラジオ** コントロールの下に円を移動します。

    ![][14]  

7. Alt キーを押しながら別のラジオ ボタンを選択すると、円の色が変わります。

[1]: ./media/add-list-box-drop-down-list-radio-button/preview.png
[2]: ./media/add-list-box-drop-down-list-radio-button/listbox.png
[3]: ./media/add-list-box-drop-down-list-radio-button/renamelistbox.png
[4]: ./media/add-list-box-drop-down-list-radio-button/itemslistbox.png
[5]: ./media/add-list-box-drop-down-list-radio-button/circle.png
[6]: ./media/add-list-box-drop-down-list-radio-button/allshapes.png
[10]: ./media/add-list-box-drop-down-list-radio-button/radiobutton.png
[12]: ./media/add-list-box-drop-down-list-radio-button/itemsradio.png
[14]: ./media/add-list-box-drop-down-list-radio-button/radiocircle.png
[15]: ./media/add-list-box-drop-down-list-radio-button/dropdown.png
