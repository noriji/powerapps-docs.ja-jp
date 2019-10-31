---
title: フォームで検索コンポーネントを構成する | MicrosoftDocs"
ms.custom: ''
ms.date: 08/26/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - PowerApps
author: Aneesmsft
ms.author: matp
manager: kvivek
tags:
  - PowerApps maker portal impact
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="configure-a-lookup-component-on-a-form"></a>フォームで検索コンポーネントを構成する  
検索フィールドは別のエンティティのレコードにリンクするために使用できます。 検索コンポーネントは検索フィールドがフォームに追加されると自動的に使用されます。 メーカーはフォーム デザイナーを使用して検索コンポーネントを構成できます。

## <a name="configure-a-lookup-component"></a>検索コンポーネントを構成する
これらは、フォーム デザイナーを使用してフォームで検索コンポーネントを作成する場合に、構成するために使用できるプロパティです。


<!--from editor: "Drop-down" should only be an adjective. In the following table, is it a list? A menu? -->


|面積  |Name  |説明  |
|---------|---------|---------|
| **表示オプション** | **エンティティ** |  検索フィールドが接続する関連エンティティ。 |
| **表示オプション** | **既定のビュー** |  アプリのユーザーが検索ドロップダウンで選択できるレコードの一覧を取得および表示するために使用できる、**エンティティ** プロパティで選択されたエンティティのビュー。 |
| **表示オプション** | **ユーザーがビューを変更することを許可** |  選択すると、アプリ ユーザーは**既定ビュー**から**エンティティ**プロパティで選択したエンティティの別のビューへと変更することができます。 |
| **表示オプション** | **すべてのビューを表示** |  選択すると、アプリ ユーザーは**既定ビュー**から**エンティティ**プロパティで選択したエンティティのすべてのその他のビューへと変更することができます。 <br /><br />このプロパティは、**ユーザーがビューを変更することを許可**が選択された場合にのみ使用できます。 |
| **表示オプション** | **選択されたビュー** |  アプリ ユーザーが**規定ビュー**から/へと変更できる **エンティティ**プロパティ内で選択されたエンティティのビューのリスト。 <br /><br />このプロパティは、**ユーザーがビューを変更することを許可**が選択され、**すべてのビューを表示**が非選択となっている場合にのみ利用できます。 |

## <a name="see-also"></a>関連項目
[モデル駆動型フォーム デザイナーの概要](form-designer-overview.md)  
[フォーム デザイナーを使用してフォームを作成、編集、構成する](create-and-edit-forms.md)  
[フォーム上のフィールドを追加、構成、移動、削除する](add-move-or-delete-fields-on-form.md)  
[フォーム上のコンポーネントを追加、構成、移動、削除する](add-move-configure-or-delete-components-on-form.md)  
[フォーム上のセクションを追加、構成、移動、削除する](add-move-or-delete-sections-on-form.md)  
[フォーム上のタブを追加、構成、移動、削除する](add-move-or-delete-tabs-on-form.md)  
[フォーム デザイナーでヘッダーのプロパティを構成する](form-designer-header-properties.md)  
[フォームでサブグリッド コンポーネントを追加して構成する](form-designer-add-configure-subgrid.md)  
[フォームで簡易表示コンポーネントを追加して構成する](form-designer-add-configure-quickview.md)  
[フォーム デザイナーのツリー ビューを使用](using-tree-view-on-form.md)  
[フィールドの作成および編集](../common-data-service/create-edit-field-portal.md)  
