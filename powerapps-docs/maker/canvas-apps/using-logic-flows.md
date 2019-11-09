---
title: キャンバス アプリでフローを開始する | Microsoft Docs
description: ユーザーによるボタンの選択などのイベントがキャンバス アプリで発生した後に 1 つ以上のタスクを実行するフローを作成します。
author: stepsic-microsoft-com
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 12/07/2018
ms.author: stepsic
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 636e9f853ada9816e87232348e5ce7ef6df2cedc
ms.sourcegitcommit: 0f0b26122be28d674af0833247b491e9367c4932
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2019
ms.locfileid: "73898321"
---
# <a name="start-a-flow-in-a-canvas-app"></a>キャンバス アプリでフローを開始する

Power の自動化を使用して、canvas アプリでイベントが発生したときに1つ以上のタスクを実行するロジックを作成できます。 たとえば、ユーザーが選択したときに、SharePoint リストのアイテムの作成、電子メールまたは会議出席依頼の送信、クラウドへのファイルの追加、またはこれらのすべての処理を実行するようにボタンを構成できます。 アプリ内の任意のコントロールは、フローを開始するように構成できます。フローは、PowerApps を閉じた後でも実行し続けます。

> [!NOTE]
> ユーザーがアプリ内からフローを実行する場合、そのユーザーは、フローで指定されたタスクを実行する権限を持っている必要があります。 それ以外の場合、フローは失敗します。

## <a name="prerequisites"></a>前提条件

- PowerApps に[サインアップ](../signup-for-powerapps.md)。
- [コントロールを構成する](add-configure-controls.md)方法を確認しておきます。

## <a name="create-a-flow"></a>フローの作成

1. [PowerApps にサインインします](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)。

1. 左側のナビゲーションバーで **[ビジネスロジック]** を選択し、 **[フロー]** を選択します。

1. **[マイフロー]** ページの左上隅にある **[新規]** 作成 を選択し、一 **[から作成]** を選択します。

    ![テンプレートを使用せずにフローを作成するオプション](./media/using-logic-flows/create-from-blank.png)

1. 表示されるページの下部にある [検索] を選択して、数**百の接続とトリガーを検索**します。

1. 検索ボックスに「 **powerapps**」と入力し、 **powerapps**アイコンを選択します。

    ![PowerApps トリガーの作成](./media/using-logic-flows/set-trigger.png)
    
1. 次のページで、PowerApps アイコンをもう一度選択し、 **[新しいステップ]** を選択します。

1. **[コネクタとアクションの検索]** というボックスで、次の例のようにフローのアクションを指定します。

   1. ボックスに「 **SharePoint** 」と入力し、 **[アクション]** の一覧で **[アイテムの作成]** を選択します。

       ![SharePoint 項目を作成するオプション](./media/using-logic-flows/create-sharepoint-item.png)

   1. ダイアログが表示されたら、SharePoint に接続するための資格情報を指定します。

   1. **[Site Address]\(サイトのアドレス\)** ボックスに、リストを含む SharePoint Online サイトの URL を入力するか貼り付けます。

       > [!NOTE]
       > リストの名前を URL に追加しないでください。

   1. **[リスト名]** ボックスで、使用する一覧を指定します。
   
       ![リストの指定](./media/using-logic-flows/list-fields.png)

   1. リスト内のフィールドの入力ボックス ( **[タイトル]** など) を選択し、動的コンテンツ ウィンドウで **[詳細を表示]** を選択し、 **[PowerApps で確認]** を選択します。 

       ![[タイトル] フィールドに [PowerApps で確認] パラメーターを追加する](./media/using-logic-flows/ask-in-powerapps.png)

1. optional指定したアドレスに承認メールを送信したり、別のデータソースに関連エントリを作成するなど、追加の手順を1つ以上指定します。

1. 左上隅の近くに、フローの名前を入力するか貼り付け、右上隅にある **[保存]** を選択します。

## <a name="add-a-flow-to-an-app"></a>アプリへのフローの追加
1. 左側のナビゲーションバーで、 **[作成]** を選択します。

1. [空白] タイル**からキャンバスアプリ**にマウスポインターを移動し、[**このアプリを作成**する] を選択します。

1. **[テキスト入力](controls/control-text-input.md)** コントロールを追加し、**RecordTitle** という名前を付けます。

1. **[ボタン](controls/control-button.md)** コントロールを追加し、**RecordTitle** の下に移動します。

1. **[ボタン](controls/control-button.md)** コントロールを選択した状態で、 **[アクション]** タブの **[フロー]** を選択します。

    ![[アクション] タブの [フロー] オプション](./media/using-logic-flows/action-tab.png)

1. 表示されたウィンドウで、前の手順で作成したフローを選択します。

    > [!NOTE]
   > 作成したフローが選べない場合は、フローを作成した環境に PowerApps が設定されているかどうかを確認します。

    ![カスタマイズ ウィンドウからフローを追加する](./media/using-logic-flows/add-flow-from-pane.png)

1. 数式バーで、自動的に追加された数式の末尾に「**RecordTitle.Text)** 」と入力するか貼り付けます。

    ![フローを含む OnSelect プロパティ](./media/using-logic-flows/onselect-with-flow.png)

## <a name="test-the-flow"></a>フローのテスト
1. **テキスト入力**コントロールをダブルクリックし、テキストを入力するか貼り付けます。

1. Alt キーを押しながら、 **[ボタン](controls/control-button.md)** コントロールを選択します。

    SharePoint アイテムが、タイトルとして指定したテキストと共に指定したリストに作成されます。 フローの実行時にリストが開いていたときは、変更内容を表示するためにブラウザー ウィンドウを更新することが必要な場合があります。
