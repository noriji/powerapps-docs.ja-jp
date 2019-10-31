---
title: モデル駆動型アプリ ダッシュボードを作成または編集する | MicrosoftDocs
ms.custom: ''
ms.date: 05/23/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - PowerApps
ms.assetid: 641885d2-4a08-41b8-b914-d9a244e4d5b1
caps.latest.revision: 10
ms.author: matp
manager: kvivek
author: Mattp123
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="create-or-edit-model-driven-app-dashboards"></a>モデル駆動型アプリ ダッシュボードを作成または編集する

ユーザー ダッシュボードとシステム ダッシュボードの 2 種類のダッシュボードがあります。 アプリ ユーザーは、特権を持つユーザーがアプリ領域にいるときのみ見られるダッシュボードを作成できます。 管理者またはカスタマイザーは、公開されるとすべてのアプリ ユーザーに対して表示されるシステム ダッシュボードを作成またはカスタマイズします。 ユーザーは自分のユーザー ダッシュボードを既定のダッシュボードとして設定し、システム ダッシュボードに上書きするよう選択できます。 このトピックはシステム ダッシュボードに焦点を当てます。  
  
<a name="BKMK_createdashboard"></a>   
## <a name="create-a-new-dashboard"></a>新しいダッシュボードを作成します  
  
1.  [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) にサインインします。

    > [!IMPORTANT]
    > **モデル駆動型** デザイン モードがない場合は、[環境の作成](https://docs.microsoft.com/powerapps/administrator/create-environment)が必要となることがあります。   
  
2. **データ** を展開して **エンティティ** を選択し、**取引先企業** エンティティなど、ダッシュボードのベースとするエンティティを選択した後、**ダッシュボード** タブを選択します。 

3. ツール バーで、**ダッシュボードの追加** を選択し、2 列、3 列、または 4 列のレイアウトを選択します。  
  
4.  **ダッシュボード: 新規**ダイアログ ボックスにダッシュボードの名前を入力します。  
  
5.  いずれかのコンポーネント領域を選択し、グラフまたはリストのアイコンを選択します。  
  
     ダッシュボードには最大 6 つのコンポーネントを含めることができます。  
  
6.  たとえば、グラフを追加するには、**コンポーネントの追加**ダイアログ ボックスで、**レコードの種類**、**ビュー**、および**グラフ**の値を選択し、**追加**を選択してダッシュボードにグラフを追加します。  
  
7.  ダッシュボードに対するコンポーネントの追加が終了した時、**保存**、**公開**の順に選択します。  
  
<a name="BKMK_editdashboard"></a>   
## <a name="edit-an-existing-dashboard"></a>既存のダッシュボードの編集  
  
1. [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) にサインインします。

    > [!IMPORTANT]
    > **モデル駆動型** デザイン モードがない場合は、[環境の作成](https://docs.microsoft.com/powerapps/administrator/create-environment)が必要となることがあります。    
  
2. **データ** を展開して **エンティティ** を選択し、**取引先企業** エンティティなど、ダッシュボードのベースとするエンティティを選択した後、**ダッシュボード** タブを選択します。  

3. ダッシュボードを開き、コンポーネント領域の 1 つを選択してから、ツール バーで **コンポーネントの編集**を選択します。  
  
4.  **プロパティの設定** ダイアログ ボックスで、エンティティの変更、既定のビュー、グラフ セレクターの追加、モバイル アプリでダッシュボードを使用できるようにするなど、グラフまたはリストに変更を加えることができます。 終了したら、**設定**を選択します。  
  
     設定ダッシュボードのコンポーネント プロパティの詳細については、「[ダッシュボードに組み込むグラフまたはリストのプロパティ設定](set-properties-chart-list-included-dashboard.md)」を参照してください。  
  
4.  変更を完了したら、それを保存してから公開します。  
  
 追加のシステム ダッシュボードで実行できるタスクには、以下のものが含まれます。  
  
    -   ダッシュボードからリストまたはグラフを削除する  
  
    -   ダッシュボードに対してリストまたはグラフを追加する  
  
    -   既定のダッシュボードを設定する  
  
    -   セキュリティ ロールを使用して、特定のロールのみに対してダッシュボードが表示されるようにする    
  
## <a name="next-steps"></a>次のステップ  
[ダッシュボードに組み込むグラフまたはリストのプロパティ設定](set-properties-chart-list-included-dashboard.md)
