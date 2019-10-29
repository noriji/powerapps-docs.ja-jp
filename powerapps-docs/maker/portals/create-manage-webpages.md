---
title: Web ページの作成と管理 |Microsoft Docs
description: ポータルで web ページを作成して管理する方法について説明します。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: b62f6a811d2f2e6c5218ef601f18d69357d15ba9
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/11/2019
ms.locfileid: "72977015"
---
# <a name="create-and-manage-webpages"></a>Web アプリを作成および管理する

Web ページは、web サイト内の一意の URL によって識別されるドキュメントです。 これは、web サイトの中核となるオブジェクトの1つであり、他の web ページとの親子関係を通じて web サイトの階層を構築します。

> [!NOTE]
> PowerApps ポータル Studio を使用してポータルをカスタマイズした場合、web サイトのユーザーはパフォーマンスに影響します。 ライブポータルでは、ピーク時以外の時間帯に変更を行うことをお勧めします。

## <a name="create-webpage"></a>Web ページの作成

1.  [ポータルを編集](manage-existing-portals.md#edit)して PowerApps ポータル Studio で開きます。  

2.  コマンドバーの **[新しいページ]** をクリックし、**レイアウト**または**固定レイアウト**からページを選択します。

    > [!div class=mx-imgBorder]
    > ![新しい web ページを作成]する(media/create-webpage.png "新しい web ページを")作成する

    > [!NOTE]
    > - **レイアウト**を使用してページを作成すると、ページ全体を柔軟に編集できます。 **固定レイアウト**には、ポータルのプロビジョニングの一部としてインストールされるページテンプレートと、[ポータル管理アプリ](configure/configure-portal.md)を使用して作成されたカスタムページテンプレートが含まれています。
    > - **レイアウト**オプションを使用して作成されるページについては、新しい**既定の studio テンプレート**ページテンプレートがインストールされます。

3.  画面の右側の [プロパティ] ウィンドウで、次の情報を入力します。

    - **[名前]** : ページの名前。 この値は、ページのタイトルとしても使用されます。

    - **[部分的な url]** : このページのポータル url を作成するために使用される url パスセグメント。

    - **Template**: ポータルでこのページを表示するために使用されるページテンプレート。 必要に応じて、一覧から別のテンプレートを選択することもできます。

        > [!div class=mx-imgBorder]
        > ![web ページのプロパティ]の(media/webpage-props.png "web ページのプロパティ")

作成した web ページが追加され、その階層が **[ページ]** ウィンドウに表示されます。 **ページ**ウィンドウを表示するには、画面の左側にある toolbelt の [**ページ**![ページ]] アイコン(media/pages-icon.png "ページアイコン")をクリックします。  

たとえば、ポータル用にいくつかの web ページを作成したとします。 ページ階層は次のようになります。

> [!div class=mx-imgBorder]
> ![ページペイン](media/pages-pane.png "ページのウィンドウ")  

Web サイトの主要なメニューは、web ページの階層に基づいて自動的に作成されます。 これは、**既定**のメニューと呼ばれます。 カスタムメニューを作成して、web サイトに表示することもできます。 詳細情報:[カスタムメニューの追加](compose-page.md#add-a-custom-menu)

> [!div class=mx-imgBorder]
> ![web サイトナビゲーション](media/website-navigation.png "web サイトのナビゲーション")

Dynamics 365 環境で作成されたポータルを使用していて、メニューをページ階層と同じにする場合は、**ナビゲーションメニュー**の一覧から **[既定]** を選択する必要があります。

> [!div class=mx-imgBorder]
> ![既定のナビゲーションメニュー]の(media/navigation-menu-default.png "既定のナビゲーションメニュー")

## <a name="manage-webpage"></a>Web ページの管理

1.  [ポータルを編集](manage-existing-portals.md#edit)して PowerApps ポータル Studio で開きます。  

2.  画面左側の toolbelt から [**ページ**![ページ] アイコン](media/pages-icon.png "ページアイコン")を選択します。  

3.  管理するページの上にマウスポインターを移動し、管理する web ページの**省略記号**ボタン ([...]) を選択します。 交互. 管理するページを右クリックします。

4.  コンテキストメニューから必要な操作を選択します。

    - **既定のメニューで非表示に**する: 既定のメニューを使用して、サイトマップにページを表示しないようにします。

    - **既定のメニューで表示**: 既定のメニューを使用して、サイトマップにページを表示します。

    - **子ページの追加**: 選択したページに子ページを追加します。 子ページは、その親ページのページテンプレートを継承します。

    - **ホームページとして設定**: ページをホームページとして設定します。 新しいホームページの URL は web サイトのルートに設定され、それに応じて古いページの URL も更新されます。

    - **上へ移動**: 階層内でページを上に移動します。

    - **下へ移動**: 階層内でページを下へ移動します。

        > [!NOTE]
        > ページを上下に移動することは、同じレベルの複数のページでサポートされています。

    - サブページの**昇格**: インデントを下げ、子ページを階層内の前のページのレベルに設定します。

    - サブページを**作成**する: インデントを増やし、ページを階層内の前のページの子ページにします。

    - **削除**: ページを削除します。

        > [!div class=mx-imgBorder]
        > ![web ページの管理オプション](media/webpage-manage-options.png "web ページの管理オプション")  




