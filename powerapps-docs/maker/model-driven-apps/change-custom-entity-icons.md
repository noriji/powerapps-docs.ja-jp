---
title: PowerApps でモデル駆動型アプリのカスタム エンティティ アイコンを変更する | MicrosoftDocs
definition: Learn how to change the icon for a custom entity
ms.custom: ''
ms.date: 05/17/2018
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
ms.assetid: 477f9792-8207-49ef-8968-45274b5355a8
caps.latest.revision: 19
ms.author: matp
manager: kvivek
tags:
  - Links to topic not migrated
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="change-model-driven-app-custom-entity-icons"></a>モデル駆動型アプリのユーザー定義エンティティのアイコンの変更 

ユーザー定義エンティティを作成すると、自動的に既定のアイコンが割り当てられます。 すべてのユーザー定義エンティティが同じアイコンを既定で使用します。 ユーザー定義エンティティの外観を区別するには、ユーザー定義アイコンを表示します。 システム エンティティのアイコンは変更できません。  
  
 各ユーザー定義エンティティに以下の 3 種類のエンティティ アイコンをアップロードできます。 

|アイコンの種類  |説明  |
|---------|---------|
|**統一インターフェイス アイコン**|スケーラブル ベクター グラフィックス (.svg) アイコン |
|**Web アプリケーション内のアイコン**|.svg、.gif、.png、または .jpg 形式のイメージ、サイズは 16x16 ピクセル。|
|**エンティティ フォームのアイコン**|.svg、.gif、.png、または .jpg 形式のイメージ、サイズは 32x32 ピクセル。|

> [!NOTE]
> すべての画像ファイルは 10 KB 以下である必要があります。
>
> **Web アプリケーション内のアイコン**または**エンティティ フォームのアイコン**としてスケーラブル ベクター グラフィックス (.svg) 画像を使用する場合、既定のサイズを設定する必要があります。 SVG は XML ドキュメントであるため、[svg](https://developer.mozilla.org/docs/Web/SVG/Element/svg) 要素の [width](https://developer.mozilla.org/docs/Web/SVG/Attribute/width) および [height](https://developer.mozilla.org/docs/Web/SVG/Attribute/height) 値をテキスト エディターで編集し、画像の既定のサイズを定義できます。

アイコンの各種類は Web リソースとして保存されます。 まず Web リソースを作成した後、それらを使用するようにアイコンを設定するか、値を設定するときに **新規** を選択して **レコードの検索** ダイアログ内に新しい Web リソースを作成することができます。 詳細: [Web リソースを作成または編集してアプリを拡張](create-edit-web-resources.md)

## <a name="set-the-icons-for-a-custom-entity"></a>ユーザー定義エンティティのアイコンを設定します。

エンティティ アイコンを設定するには、ソリューション エクスプローラーを使用する必要があります。

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

### <a name="set-entity-icons"></a>エンティティのアイコンの設定

1. コマンド バーで、**アイコンの更新**を選択します。  
  
2. **新しいアイコンの選択** ダイアログ ボックスの **Web クライアント** タブの **Web アプリケーション内のアイコン** または **エンティティ フォームのアイコン** にある、**新規アイコン** の右で、**参照** ボタン ![[検索]ボタン](media/lookup-button-4.gif) を選択します。
3. 適切な Web リソースを選択するか作成し、**OK** を選択します。 
4. **統一インターフェイス** タブで、**新しいアイコン** フィールドに対して同じ操作を行います。
5. **OK** をクリックして **新しいアイコンの選択** ダイアログを閉じる
6. コマンド バーの**ファイル**メニューで、**保存**を選択します。  
7. 変更が完了したら、公開します。 ソリューション エクスプローラーでエンティティを選択しているときに、コマンド バーの **公開** を選択します。
  
## <a name="community-tools"></a>コミュニティ ツール

**[Iconator](https://www.xrmtoolbox.com/plugins/MscrmTools.Iconator/)** は XrmToolbox コミュニティが PowerApps 向けに開発したツールです。 コミュニティが開発したツールについては [Common Data Service の開発者ツール](/powerapps/developer/common-data-service/developer-tools) トピックをご覧ください。

> [!NOTE]
> コミュニティ ツールは Microsoft の製品ではなく、コミュニティ ツールに対するサポートは提供されません。 このツールに関するご質問は、その発行元にお問い合わせください。 詳細: [XrmToolBox](https://www.xrmtoolbox.com)。

## <a name="next-steps"></a>次のステップ  
[エンティティの作成](../common-data-service/create-edit-entities.md)<br />
[エンティティの編集](../common-data-service/edit-entities.md)
