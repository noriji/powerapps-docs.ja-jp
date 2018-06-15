---
title: Excel でエンティティ データを開く | Microsoft Docs
description: エンティティ データを Excel で開いてその場で閲覧したり編集したりします。
author: clwesene
manager: kfile
ms.service: powerapps
ms.component: cds
ms.topic: conceptual
ms.date: 05/21/2018
ms.author: clwesene
ms.openlocfilehash: 8dbf6088104270d9251b70eec9adf0642de2f879
ms.sourcegitcommit: 68fc13fdc2c991c499ad6fe9ae1e0f8dab597139
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34445875"
---
# <a name="open-entity-data-in-excel"></a>Excel でエンティティ データを開く
Microsoft Excel でエンティティ データを開くことで、Microsoft PowerApps Excel アドインを使用して迅速かつ簡単にデータを表示して編集することができます。 PowerApps Excel アドインには Microsoft Excel 2016 が必要です。

![Excel アドイン](./media/data-platform-cds-excel-addin/ExcelAddin.png "PowerApps Excel アドイン")

## <a name="open-entity-data-in-excel"></a>Excel でエンティティ データを開く
1. [powerapps.com](https://web.powerapps.com) で、**[データ]** セクションを展開し、左側のナビゲーション ウィンドウで **[エンティティ]** をクリックまたはタップします。 すべてのエンティティが表示されます。
2. 関心があるエンティティの右側の省略記号 (...) をクリックします。
3. **[Excel で開く]** をクリックして、生成されたブックを開きます。 このブックには、エンティティのバインディング情報、ご使用の環境へのポインター、PowerApps Excel アドインへのポインターが含まれています。  
4. Excel で **[編集を有効にする]** をクリックすると、PowerApps Excel アドインが実行できる状態になります。 Excel アドインは、Excel ウィンドウの右側にあるウィンドウで実行されます。
5. PowerApps Excel アドインの初回実行時は、Excel アドインの実行を許可するために、**[このアドインを信頼]** をクリックしてください。
6. サインインを求められた場合は、**[サインイン]** をクリックし、[powerapps.com](https://web.powerapps.com) で使用したのと同じ資格情報を使用してサインインします。 Excel アドインは前のサインイン コンテキストを使用し、可能な場合は自動的にサインインします。 そのため、Excel アドインの右上のユーザー名を確認します。

選択したエンティティのデータを Excel アドインが自動的に読み取ります。 Excel アドインがデータを読み取るまで、ブックにデータは存在しないので注意してください。

## <a name="view-and-refresh-data-in-excel"></a>Excel でのデータの表示と更新
Excel アドインがエンティティ データをブックに読み込んだら、Excel アドインの **[最新の情報に更新]** をクリックして、いつでもデータを更新できます。

## <a name="edit-data-in-excel"></a>Excel でのデータの編集
必要に応じてエンティティ データを変更した後で、Excel アドインで **[発行]** をクリックして、発行することができます。

レコードを編集するには、ワークシートのセルを選択し、セルの値を変更します。

新しいレコードを追加するには、次の手順のいずれかに従います。

* ワークシートの任意の場所をクリックし、Excel アドインで **[新規]** をクリックします。
* ワークシートの最後の行をクリックし、カーソルがその行の最後の列から移動するまで Tab キーを押します。新しい行が作成されます。
* ワークシートのすぐ下にある行をクリックし、セルにデータを入力し始めます。 そのセルからフォーカスを移動すると、新しい行を含めるためにワークシートが展開されます。

レコードを削除するには、次の手順のいずれかに従います。

* 削除するワークシートの行の横にある行番号を右クリックし、**[削除]** をクリックします。
* 削除するワークシートの行を右クリックし、**[削除]** > **[テーブルの行]** の順にクリックします。

## <a name="add-or-remove-columns"></a>列の追加と削除
デザイナーを使用して、ワークシートに自動的に追加される列とエンティティを調整することができます。

1. **[オプション]** ボタン (歯車のアイコン) をクリックし、**[デザインの有効化]** チェック ボックスをオンにして、Excel アドインのデータ ソース デザイナーを有効にします。
2. Excel アドインで **[デザイン]** をクリックします。 すべてのデータ ソースが一覧表示されます。
3. データ ソースの横にある **[編集]** ボタン (鉛筆のアイコン) をクリックします。
4. 必要に応じて、次のように **[選択されたフィールド]** フィールドでリストを調整します。
   * **[使用可能なフィールド]** フィールドのフィールドを **[選択されたフィールド]** フィールドに追加するには、該当するフィールドをクリックし、**[追加]** をクリックします。 または、フィールドをダブルクリックします。
   * **[選択されたフィールド]** フィールドからフィールドを削除するには、該当するフィールドをクリックし、**[削除]** をクリックします。 または、フィールドをダブルクリックします。
   * フィールドの順序を変更するには、**[選択されたフィールド]** フィールドで該当するフィールドをクリックし、**[上へ]** または **[下へ]** をクリックします。
5. **[更新]** をクリックしてデータ ソースに変更を適用し、**[完了]** をクリックしてデザイナーを終了します。 フィールド (列) が追加されている場合は、**[最新の情報に更新]** をクリックすると、更新されたデータ セットが取り込まれます。

> [!NOTE]
> 常に、ブックに ID フィールドと必要なフィールドが含まれるようにします。そうしないと、発行するときにエラーが発生する可能性があります。

> [!NOTE]
> 参照フィールドを追加するときは、ID フィールドと表示フィールドの両方を必ず追加してください。

## <a name="troubleshooting"></a>トラブルシューティング
いくつかの簡単な手順で解決できる問題がいくつかあります。

* 編集や新しいレコードの作成をサポートしていないエンティティがあります。そのようなエンティティは、Excel で開いてデータを表示することはできますが、発行は無効になります。
* 正しいレコードが参照されるように参照フィールドを編集するには、アドインを使う必要があります。コピーしてフィールドに貼り付けたり、フィールドに直接入力したりして、これらのフィールドを更新することは、サポートされていません。


ここに記載されていない問題が発生した場合は、[サポート ページ](https://powerapps.microsoft.com/support/)からお問い合わせください。

## <a name="next-steps"></a>次の手順
* [エンティティのフィールドを管理する](data-platform-manage-fields.md)
* [エンティティ間のリレーションシップを定義する](data-platform-entity-lookup.md)
* [Common Data Service for Apps を使用してアプリを生成する](../canvas-apps/data-platform-create-app.md)
* [Common Data Service for Apps を使用してアプリを最初から作成する](../canvas-apps/data-platform-create-app-scratch.md)
