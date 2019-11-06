---
title: '列 コントロール: リファレンス | Microsoft Docs'
description: このトピックでは、Microsoft PowerApps の列のコントロールに関する情報を示します。
author: chmoncay
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 06/05/2017
ms.author: chmoncay
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 21bc7e025515397fa853e5de7f2df574a3768935
ms.sourcegitcommit: 8e42a5996799d9831f8c5a52b0b051a6088d9ce7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/06/2019
ms.locfileid: "73650645"
---
# <a name="column-control-in-powerapps"></a>PowerApps の列コントロール
[**データ テーブル**](control-data-table.md) コントロールの単一フィールドに表示エクスペリエンスを指定します。

## <a name="description"></a>Description
[**データ テーブル**](control-data-table.md) コントロールは、表形式でデータセットを表示し、その表形式の各列は**列**コントロールによって表されます。 **列**コントロールでは、アプリ メーカーが列の外観と動作をカスタマイズするために使用できるプロパティを提供します。

## <a name="capabilities"></a>機能
### <a name="now-available"></a>提供開始
* **列**コントロールの幅の変更。
* **列**コントロールのテキストの変更。
* **列**コントロールの値をクリックまたはタップして移動。

### <a name="not-yet-available"></a>現時点では利用不可
* **列**コントロールのスタイルのカスタマイズ。

### <a name="known-issues"></a>既知の問題
* **Visible** プロパティは、まだ機能していません。

## <a name="properties"></a>プロパティ
* **DisplayName** – 列のヘッダーに表示されるテキストです。
  
  > [!NOTE]
  > このプロパティの名前は、すぐに **HeaderText** に変更されます。
  > 
  > 
* **IsHyperlink** – ハイパーリンクであることを示すために、列のデータに下線を付けるかどうかを示す値です。
* [**Width**](properties-size-location.md) – **列**コントロールの左端と右端の間の距離です。

## <a name="examples"></a>例
### <a name="resize-a-column"></a>列のサイズを変更する
1. 空白のタブレット アプリを作成します。
2. **[挿入]** タブで、 **[データ テーブル]** をクリックまたはタップして、画面全体をカバーするように、**データ テーブル** コントロールのサイズを変更します。
3. 右側のウィンドウで、 **[データ ソースが選択されていません]** の右側にある下矢印をクリックまたはタップしてから、 **[データ ソースの追加]** をクリックまたはタップします。
4. 接続の一覧で、Common Data Service データベースの接続をクリックまたはタップします。
5. エンティティの一覧で、 **[アカウント]** をクリックまたはタップしてから、 **[接続]** をクリックまたはタップします。
   
    **データ テーブル** コントロールが初期化され、既定のフィールドのセットが表示されます。
6. **Full name** 列をクリックまたはタップします。
   
    ![選択された列コントロール](./media/control-column/pre-resize-column.png)
7. 右側にあるガイドをドラッグして、フィールドのサイズを変更します。
   
    ![サイズが変更された列コントロール](./media/control-column/post-resize-column.png)


## <a name="accessibility-guidelines"></a>アクセシビリティ ガイドライン
### <a name="screen-reader-support"></a>スクリーン リーダーのサポート
* **DisplayName** が存在する必要があります。
