---
title: Dynamics 365 ポータルで web サイトのアクセス許可を作成する |MicrosoftDocs
description: ポータルで web サイトのアクセス許可を作成して要素に関連付ける方法について説明します。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 0ac02992498204efc42a52e736284ea134ed42f5
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2019
ms.locfileid: "73551027"
---
# <a name="create-website-access-permissions"></a>Web サイトのアクセス許可を作成する

Web サイトのアクセス許可は、web[ロール](create-web-roles.md)に関連付けられたアクセス許可セットであり、web ページだけではなく、ポータル内のさまざまなコンテンツ管理要素をフロントエンドで編集することを許可します。 アクセス許可の設定によって、ポータルで管理できるコンポーネントが決まります。

| 名前                         | Description                                                                                      |
|------------------------------|--------------------------------------------------------------------------------------------------|
| コンテンツスニペットの管理      | スニペットコントロールを編集できるようにします。                                                          |
| サイトマーカーの管理          | サイトマーカーを使用するハイパーリンクを編集できるようにします                                           |
| Web リンクセットの管理         | Web リンクセットから web リンクを削除する[など、web リンクセットを編集](manage-web-links.md)できるようにします。 |
| パブリッシュしていないエンティティのプレビュー | 発行状態が Draft のポータルで公開されているエンティティを表示できます。             |
|||

Web サイトのアクセス許可を作成し、web ロールに追加するには、次のようにします。

1. [ポータル管理アプリ](configure-portal.md)を開きます。

2. **ポータル** > **Web サイトのアクセス許可**にアクセスします。

3. **[新規]** を選択します。

4. **[全般]** で、名前と web サイトを入力し、必要なアクセス許可を選択します。

5. **[Web ロール]** で、アクセス許可を関連付ける web ロールを選択して追加します。

6. 変更を保存します。

    ![Web サイトのアクセス許可の作成](../media/website-access-permission.png "Web サイトのアクセス許可の作成")  
