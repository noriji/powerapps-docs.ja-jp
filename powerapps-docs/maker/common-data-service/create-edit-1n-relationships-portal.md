---
title: PowerApps ポータルを使用して 1 対多または多対 1 のエンティティ関連付けを作成、編集する | MicrosoftDocs
description: PowerApps ポータルを使用して 1 対多または多 対 1 のエンティティ関連付けを作成する方法について説明します
ms.custom: ''
ms.date: 06/11/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
author: Mattp123
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="create-and-edit-one-to-many-or-many-to-one-entity-relationships-using-powerapps-portal"></a>PowerApps ポータルを使用して 1 対多または多対 1 のエンティティ関連付けを作成、編集する

[PowerApps ポータル](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) では、  Common Data Serviceの 1:N (1 対多) または N:1 (多対 1) の関連付けを簡単に作成、編集することができます。

ポータルでは一般的なオプションのほどんとを構成できますが、特定のオプションはソリューション エクスプローラーを使用してのみ設定できます。 詳細: 
- [1:N (一対多) または N:1 (多対一) の関連付けを作成および編集する](create-edit-1n-relationships.md)
- [ソリューション エクスプローラーを使用して 1:N (1 対多) または N:1 (多対 1) のエンティティ関連付けを作成および編集する](create-edit-1n-relationships-solution-explorer.md)

## <a name="view-entity-relationships"></a>エンティティの関連付けを表示する

1. [PowerApps ポータル](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)から、 **モデル駆動型** または **キャンバス** 設計モードを選択します。
2. **データ** > **エンティティ** を選択し、表示する関連付けを持つエンティティを選択します。
3. **関連付け** タブでは、次のビューを選択できます。 

 |ビュー|説明|
 |--|--|
 |**すべて**| エンティティのすべての関連付けを表示する|
 |**ユーザー定義**|エンティティのカスタム関連付けのみを表示する|
 |**既定**|エンティティの標準関連付けのみを表示する|
<!-- TODO: What is the actual difference between All and Default? -->

![アカウント エンティティの関連付け](media/view-account-relationships-portal.png)

## <a name="create-relationships"></a>関連付けの作成

[エンティティ関連付けを表示](#view-entity-relationships)しているとき、コマンド バーで **関連付けを追加** を選択し、**多対 1** または **1 対多** を選択します。

![関連付けの種類を選択する](media/add-relationship-menu-portal.png)

> [!NOTE]
> **多対多** の関連付けに関する詳細は、「[N:N (多対多) の関連付けを作成する](create-edit-nn-relationships.md)」を参照してください。

<!-- This may change going forward, but this is the way it is now. #2534972 -->
> [!Important]
> ポータルは、ソリューション エクスプローラーとは異なる用語を使用します。 ソリューション エクスプローラーの **主エンティティ** は、ポータルでは **現在のエンティティ** となります。

選択肢に応じて、次のいずれかが表示されます。

<!-- These are the correct screenshots from the UI as of 6/11/18 -->
|型|パネル|
|--|--|
|**多対 1**|![多対 1 の関連付けパネル](media/many-to-one-relationship-panel.png)|
|**1 対多**|![1 対多の関連付けパネル](media/one-to-many-relationship-panel.png)|

2つのエンティティ間で関連付けを作成をするには、 **関連エンティティ** を選択します。 

> [!NOTE]
> いずれかを選択すると、検索フィールドが *現在の* エンティティで作成されます。

エンティティを選択すると、関連付けの詳細を編集できます。 この例では、複数の取引先担当者のエンティティ レコードを 1 つの取引先企業に関連付けることができます。

<!-- These are the correct screenshots from the UI as of 6/11/18 -->
![1 対多の関連付けの取引先企業と取引先担当者](media/One-to-many-account-contact.png)

保存する前に表示された既定値を編集できます。 **関連付けの名前** および **参照フィールドの説明** の値を表示するために、**そのほかのオプション** を選択します

|フィールド|説明|
|--|--|
|**参照フィールド表示名**|検索フィールドのローカライズ可能なテキストが関連エンティティで作成されます。<br />これは、後で編集できます。|
|**検索フィールド名**|検索フィールドの名前が関連エンティティで作成されます。|
|**リレーションシップ名**|作成される関連付けの名前。|
|**検索フィールドの説明**|検索フィールドの説明。 モデル駆動型アプリでは、これは、ユーザーがフィールド上にマウス カーソルを置いたときにツールヒントとして表示されます。 <br />これは、後で編集できます。|

エンティティの編集を続行できます。 構成した関連付けを作成するには、**エンティティの保存** を選択します。

## <a name="edit-relationships"></a>関連付けの編集

[エンティティの関連付けを表示](#view-entity-relationships)しているときに、編集する関連付けを選択します。

> [!NOTE]
> それぞれの関連付けは、**多対 1** または **1 対多** の関連付けとして主エンティティまたは関連エンティティ内にあります。 いずれの場所でも編集できますが、同じ関連付けを持っています。
>
> マネージド ソリューションの発行者は、ソリューションの一部として関連付けの一部のカスタマイズを回避できます。

編集できる唯一のフィールドは、**検索フィールド表示名** および **検索フィールドの説明** です。 これらは、関連エンティティの検索フィールドのプロパティでも編集できます。 詳細: [フィールドの編集](create-edit-field-portal.md#edit-a-field)

## <a name="delete-relationships"></a>関連付けの削除

[エンティティの関連付けを表示](#view-entity-relationships)しているときに、削除する関連付けを選択します。

![エンティティの関連付けを削除する](media/delete-entity-relationship-portal.png)

省略記号 (**...**) をクリックするときに、コマンド バーまたは行ショートカット メニューの **関連付けの削除** コマンドを使用することができます。

関連付けを削除すると、関連エンティティの検索フィールドが削除されます。

> [!NOTE]
> 依存関係がある関連付けは削除できません。 たとえば、関連エンティティのフォームに検索フィールドを追加した場合は、関連付けを削除する前にフィールドをフォームから削除する必要があります。

### <a name="see-also"></a>関連項目

[エンティティ間の関連付けの作成および編集](create-edit-entity-relationships.md)<br />
[1:N (一対多) または N:1 (多対一) の関連付けを作成および編集する](create-edit-1n-relationships.md)<br />
[ソリューション エクスプローラーを使用して 1:N (1 対多) または N:1 (多対 1) のエンティティ関連付けを作成および編集する](create-edit-1n-relationships-solution-explorer.md)<br />
[フィールドを編集する](create-edit-field-portal.md#edit-a-field)
