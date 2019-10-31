---
title: ソリューションの階層の表示 | MicrosoftDocs
description: ソリューションの階層を使用する方法を説明します。
keywords: null
ms.date: 04/18/2019
ms.service: powerapps
ms.custom: null
ms.topic: article
ms.assetid: null
author: Mattp123
ms.author: matp
manager: kvivek
ms.reviewer: null
ms.suite: null
ms.tgt_pltfrm: null
caps.latest.revision: null
topic-status: Drafting
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

<!--note from editor: Best practice is that H1 title and title in metadata are different.    -->

# <a name="view-solution-layers"></a>ソリューションの階層の表示
ソリューションの階層を使用すると、ある期間のソリューションの変更によって発生したすべてのコンポーネントの変更を表示できます。 ソリューションの階層内で、コンポーネントの特定の変更されたビューと変更されていないプロパティの詳細を表示するためにドリルダウンできます。 

ソリューションの階層: 
-   ソリューションがコンポーネントを変更した順序を確認しましょう。 
-   コンポーネントへの変更を含む、特定のソリューション内のコンポーネントのすべてのプロパティを表示しましょう。 
-   ソリューションの変更によって導入されたコンポーネントの変更詳細を表示することによって、依存関係やソリューションの階層の問題に関するトラブルシューティングに使用できます。

## <a name="view-the-solution-layers-for-a-component"></a>コンポーネントのソリューションの階層を表示する
ソリューション エクスプローラーの **コンポーネント** リストまたは **依存関係の詳細** ダイアログ ボックスから、ソリューションの階層にアクセスできます。 

<!--note from editor: In step 2 below, does the page display a name at top? If so, use the same capitalization in text. -->

1. **コンポーネント** 一覧からソリューション階層を表示するには、 [ソリューション エクスプローラー](../model-driven-apps/advanced-navigation.md#solution-explorer) を開きます。 **コンポーネント** 一覧で、**取引先企業**などのコンポーネントを選択して、ツール バーの **ソリューションの階層** を選択します。 

   > [!div class="mx-imgBorder"] 
   > ![ソリューション階層ボタン](media/solution-layers-toolbar.png "ソリューション階層ボタン")

2. ソリューション階層 ページが表示されます。 最新のレイヤーが一番上になるように、 個々の表示されている **取引先企業** エンティティのようなコンポーネントの各階層が表示されます。 ソリューションの階層の詳細を表示するには、それを選択します。 

   > [!div class="mx-imgBorder"] 
   > ![ソリューション階層リスト](media/solution-layers-list.png "ソリューション階層リスト")

3. **ソリューション階層** ダイアログ ボックスで、**変更されたプロパティ** タブには特定のソリューション階層の一部として変更されたプロパティだけが表示されます。 

   > [!div class="mx-imgBorder"] 
   > ![ソリューション階層変更プロパティ](media/solution-layers-change-prop.png "ソリューション階層変更プロパティ")

4. **すべてのプロパティ** タブを選択して、変更されたプロパティと変更されていないプロパティを含む、ソリューションの階層のすべてのプロパティを表示します。 

   > [!div class="mx-imgBorder"] 
   > ![ソリューション階層変更プロパティ](media/solution-layers-all-prop.png "ソリューション階層変更プロパティ")

### <a name="see-also"></a>関連項目
[ソリューションの概要](solutions-overview.md)
