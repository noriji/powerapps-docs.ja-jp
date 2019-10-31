---
title: PowerApps のソリューションを使用する | Microsoft Docs
description: ソリューションを使用してアプリを作成またはカスタマイズする方法を学習します
ms.custom: ''
ms.date: 06/17/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
author: caburk
ms.assetid: 72bacfbb-96a3-4daa-88ff-11bdaaac9a3d
caps.latest.revision: 57
ms.author: caburk
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="use-solutions-in-powerapps"></a>PowerApps でのソリューションの使用

 PowerApps の左側のナビゲーションから **ソリューション** を選択するとソリューションの一覧を表示できます。 ソリューションを 1 つ選択すると、そのコンポーネントをすべて表示することができます。 
 
> [!div class="mx-imgBorder"]  
> ![すべてのコンポーネントのデモ ソリューション](media/solution-all-items-list.PNG "すべてのコンポーネントのデモ ソリューション")  
 
> [!NOTE]
>  ソリューション エクスペリエンスはオンラインもしくは version 9.1.0.267 以降で利用可能です。 バージョンを確認するには、[PowerApps 管理センター](https://admin.powerapps.com/)> **環境** > 環境を選択 > **詳細** タブにアクセスします。以前のバージョン環境の場合は、ソリューションを選択するとクラシック エクスペリエンスで開きます。  
 
 ソリューションのすべてのコンポーネントはアイテムをスクロールすることで参照できます。 一覧に 100 項目以上ある場合は **次の 100 項目を読み込む** を選択して続きを参照します。 
 
> [!div class="mx-imgBorder"]  
> ![コンポーネントをさらに読み込む](media/load-more.PNG "コンポーネントをさらに読み込む")  

 ## <a name="search-and-filter-in-a-solution"></a>ソリューションの検索とフィルター
 
 名前で特定のコンポーネントを検索することもできます。 
 
> [!div class="mx-imgBorder"]  
> ![コンポーネントの検索](media/solution-search-box.png "コンポーネントの検索")  
 
 または一覧のすべてのアイテムをコンポーネントの種類でフィルター処理します。
  
> [!div class="mx-imgBorder"]  
> ![コンポーネントを種類でフィルター](media/solution-filter.PNG "コンポーネントを種類でフィルター")  
 
 ## <a name="contextual-commands"></a>コンテキスト コマンド
 
 ソリューションが既定もしくは管理されている場合、それぞれのコンポーネントを選択するとその種類によってコマンド バーで利用できる操作が変化します。 
 
> [!div class="mx-imgBorder"]  
> ![コンポーネントの特定のコマンド](media/component-commands.png "コンポーネントの特定のコマンド")  
 
 どのコンポーネントも選択しない場合は、コマンド バーはソリューション自体に適用される操作を表示します。 
 
> [!div class="mx-imgBorder"]  
> ![ソリューションの特定のコマンド](media/solution-commands.PNG "ソリューションの特定のコマンド")  
 
 ## <a name="create-components-in-a-solution"></a>ソリューションに新しいコンポーネントを作成する
 既定もしくはアンマネージドのソリューションでは **新規** コマンドを使用して異なる種類のコンポーネントを作成することができます。 選択したコンポーネントの種類によって、この先の作成エクスペリエンスは異なります。 作成が完了したコンポーネントはそのソリューションに追加されます。 
 
> [!div class="mx-imgBorder"]  
> ![ソリューションに新しいコンポーネントを作成する](media/solution-new-component.PNG "ソリューションに新しいコンポーネントを作成する")  
 
 ## <a name="add-an-existing-component-to-a-solution"></a>既存のコンポーネントをソリューションに追加する
 
 ソリューションが既定ではなくアンマネージドの場合、 **既存を追加** コマンドを使用してソリューション内にすでに存在するコンポーネントを取り込みます。  
 
> [!div class="mx-imgBorder"]  
> ![既存のコンポーネントをソリューションに追加する](media/solution-add-existing-component.PNG "既存のコンポーネントをソリューションに追加する")  
  
 管理されたソリューションでは、特定のコマンドのみ利用できるため以下のメッセージが表示されます。 コンポーネントをカスタマイズするために作成した別のアンマネージド ソリューションに追加する必要があります。 そのコンポーネントはカスタマイズ可能でない場合があります。 詳細: [管理プロパティ](solutions-overview.md#managed-properties)

> [!div class="mx-imgBorder"]  
> ![マネージド ソリューション](media/managed-solution.PNG "マネージド ソリューション")  

 カスタマイズの多くには、エンティティが関係します。 現在のソリューション内で全てのエンティティの一覧を表示するには **エンティティ** フィルターを使用します。それは何らかの方法でカスタマイズすることもできます。 下記に示す取引先企業エンティティのスクリーンショットのように、エンティティを開くとその一部であるコンポーネントが表示されます。 
   
> [!div class="mx-imgBorder"]  
> ![展開されて取引先企業エンティティを表示したデモ ソリューション](media/solution-entity-account.png "展開されて取引先企業エンティティを表示したデモ ソリューション")  

## <a name="classic-solution-explorer"></a>クラシック ソリューション エクスプローラー

PowerApps では、左側のナビゲーション ウィンドウで **ソリューション** を選択するとクラシック ソリューション エクスプローラーが表示されます。その後、コマンド バーの **クラシックに切り替え** を選択してください。 クラシック ソリューション エクスプローラーとは、以前は PowerApps の **設定 > 高度なカスタマイズ** から利用できたものです。 

## <a name="known-limitations"></a>既知の制限

- カスタム コネクタはソリューションで使用できません。
- キャンバス アプリは接続を認証するためソリューションのインポートの後に実行する必要があります。
- 管理ソリューションにキャンバス アプリがパッケージされている場合、対象の環境でも編集できます。ただし、再公開はできません。
- マネージド ソリューションを削除しても別のキャンバス アプリのバージョンにロールバックしません。 
-   キャンバス アプリ アクセス (CRUD とセキュリティ) は PowerApps のマネージド エンティティであり、Common Data Service (Common Data Service) のデータベースではありません
-   Common Data Service キャンバス アプリを呼び出す CDS API はブロックされており、何も返しません。 
-   ソリューションから作成されたキャンバス アプリは共同所有者として AAD セキュリティ グループと共有できません。
-   キャンバス アプリはクラシック ソリューション エクスプローラーに表示されません。
- ソリューションから作成されたフローは、[チーム フロー] 一覧に表示されません。
- ボタンにトリガーされたフローはソリューションで利用できません。
- キャンバス アプリにトリガーされたフローはソリューションで利用できません。
- Excel など Microsoft 365 アプリケーションからトリガーされたフローは、ソリューションで使用できません。
- SharePoint に接続するフローはソリューションで利用できません。
- ソリューション フローが会社認証をサポートしません。 たとえば、フローへのアクセスは、ワークフローの作成元である SharePoint リストに対するアクセスを行うに基づいて自動的に付与されません。

 ソリューションの各コンポーネントのカスタマイズの詳細については、以下のトピックを参照してください:  
  
-   エンティティ、エンティティの関連付け、フィールドおよびメッセージのカスタマイズについては、[メタデータ](create-edit-metadata.md) を参照してください。  
  
-   エンティティ フォームについては、[フォーム](../model-driven-apps/create-design-forms.md) を参照してください。  
  
-   プロセスについては、[プロセス](../model-driven-apps/guide-staff-through-common-tasks-processes.md) を参照してください。  
  
-   業務ルールについては、[業務ルール](../model-driven-apps/create-business-rules-recommendations-apply-logic-form.md) を参照してください。  
