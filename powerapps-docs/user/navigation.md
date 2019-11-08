---
title: モデル駆動型アプリでのナビゲーションの基本 | MicrosoftDocs
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 10/03/2019
ms.author: mkaur
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: f0b095b3cb69eb7b6fd373b28eb2255291c7893a
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2019
ms.locfileid: "73543528"
---
#  <a name="basic-navigation-in-a-model-driven-app"></a>モデル駆動型アプリでのナビゲーションの基本 

モデル駆動型アプリで作業領域に移動したり、新しいレコードを作成したり、検索したり、他のタスクを実行したりするにはナビゲーション バーを使用します。

> [!div class="mx-imgBorder"]
> ![モデル駆動型アプリの nav](media/nav.png "モデル駆動型アプリの nav")

1. このサイト マップは、既定で拡大され維持されます。
2. 現在使用しているサブ領域は、アプリのどの部分に現在いるのかを示すために、強調表示されます。
3. **最近**のアイテムと**ピン留め**されたアイテムは、簡単にアクセスできるように上部にあります。 
4. アプリを切り替えるには、領域スイッチャーを使用します。
5. コマンド バー上のアイコンは、コマンド間の違いを表すために違う色になっています。
  
## <a name="get-back-to-recent-records-items-or-view"></a>最近のレコード、アイテムまたはビューに戻る
ユーザーは、大半の時間、同じレコードで作業します。 たとえば、常に同じ連絡先やアカウントにアクセスします。 また、同じデータの一覧 (ビュー) を何度も使用します。 サイト マップを使用すると、最近使用したレコードやビューにすぐに戻ることができます。 また、レコードやビューをピン留めして、探しやすくすることも可能です。 
  
1. **[サイト マップ]** から **[最近]** を選択します。
  
2. **[最近]** から再度使用するレコード、アイテム、ビューを選択します。 

## <a name="pin-records-items-or-view"></a>レコード、アイテムまたはビューをピン留めする

1. **[サイト マップ]** から **[最近]** を選択し、最近アクセスしたアイテムの一覧を展開します。
2. 最近の一覧でアイテムの横のピン留めアイコンを選択すると、それがピン留めされた一覧に追加されます。

   > [!div class="mx-imgBorder"]
   > ![ピン留めされたレコード](media/pinnedrecords.png "ピン留めされたレコード")

## <a name="unpin-records-items-or-view"></a>レコード、アイテム、またはビューのピン留めを解除する

1. **[サイト マップ]** から **[ピン留め]** を選択し、ピン留めされたアイテムの一覧を展開します。
2. アイテムの横のピン留め解除のアイコンを選択すと、一覧からそれが削除されます。  

   > [!div class="mx-imgBorder"]
   > ![レコードの固定解除](media/unpinnedrecords.png "レコードの固定解除")

## <a name="record-set-navigation"></a>レコードのセットのナビゲーション 
事前設定されたビューとクエリを使用して、複数のレコード間を移動できます。 レコードを使用したナビゲーションでは、作業一覧を失うことなく、一覧のレコード間を移動し、元に簡単に戻ることができるので、ユーザーの生産性が高まります。

> [!div class="mx-imgBorder"]
> ![レコードセットのナビゲーション](media/recordset.png "レコードのセットのナビゲーション")

## <a name="reference-panel"></a>参照パネル
参照パネルは、使用している画面から移動せずに、作業を終えられる優れた方法です。 別の画面に移動せずに、参照しているレコードのコンテキスト内で、ケースやアカウントの機会など、その他の関連するものを参照できます。

> [!div class="mx-imgBorder"]
> ![参照パネル](media/reference-panel.png "参照パネル")

 [参照] パネルの詳細については、次のビデオをご覧ください。

<div class="embeddedvideo"><iframe src="https://www.microsoft.com/videoplayer/embed/d8224c3f-6e20-4b8e-9d0d-b0f5602c7708" frameborder="0" allowfullscreen=""></iframe></div>

## <a name="notifications"></a>通知 

フォームに表示される通知には、"情報"、"警告"、および "エラー" の3種類があります。 通知は常にヘッダーの真上のフォームの上部にあります。

エラー通知を選択すると、エラーが発生したフォーム上のフィールドに移動します。

![通知の例](media/notifications.png "通知の例")

通知が 1 つのみある場合は、行が 1 つ表示されます。

![シングル通知の例](media/single_notification.png "シングル通知の例")

通知が 2 つ以上ある場合は、通知の数が表示されます。 各メッセージを表示するには、シェブロンを選択します。

![複数の通知の例](media/multiple_notification.png "複数の通知の例")

## <a name="grids"></a>む

統合インターフェイスのグリッドが改善され、画面に表示できるデータの量が増加しました。 また、グリッドには、最後のフィルターを記憶し、順序を並べ替えるなどのフィルターオプションも強化されています。 

グリッド領域でデータを取得すると、システムがデータの取得中に機能していることを示す読み込みインジケーターが表示されます。

メイングリッドページでは、他の場所に移動して戻ると、フィルター、並べ替え、およびページの状態が記憶されます。 これには、クイック検索、列のフィルター処理、ページ番号などが含まれます。 ページ外のナビゲーションが初期状態で開きます。


   > [!div class="mx-imgBorder"]
   > ![グリッドの状態を記憶する](media/grid-remember-state-on-back-navigate.gif "グリッドの状態を記憶する")


ジャンプバーでは、最初に並べ替えられたフィールドを使用します。 並べ替えの変更が行われていない場合、ジャンプバーはプライマリフィールドを使用します。 

   > [!div class="mx-imgBorder"]
   > ![グリッドの状態を記憶する](media/jumpbar-filter-on-sorted-column.gif "グリッドの状態を記憶する")
   

**[アクティビティの種類]** フィールドをフィルター処理して、複数のフィルター処理の種類を選択できます。 また、owner、status、reason などの関連エンティティフィールドをフィルター処理することもできます。

   > [!div class="mx-imgBorder"]
   > ![グリッドフィルター処理](media/grid-activity-type-column-filter.gif "グリッドフィルター処理")
   
階層アイコンを選択すると、階層のフォームに移動します。

   > [!div class="mx-imgBorder"]
   > ![階層アイコン](media/grid-row-hierarchy-icon.png "階層アイコン")
   
また、新しいタブまたはウィンドウで、プライマリフィールドとルックアップフィールドを開くこともできます。

   > [!div class="mx-imgBorder"]
   > ![新しいウィンドウで開く](media/newtab.png "[新しいウィンドウで開く]")


