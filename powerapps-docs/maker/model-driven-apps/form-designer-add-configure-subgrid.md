---
title: フォームでサブグリッド コンポーネントを追加して構成する | MicrosoftDocs
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



<!-- note from editor: I recommend removing the hyphen from "sub-grid" based on the style guide entry for sub: https://styleguides.azurewebsites.net/Styleguide/Read?id=2700&topicid=28872. I didn't change it here because I don't know how wide an impact that might have. -->


# <a name="add-and-configure-a-sub-grid-component-on-a-form"></a>フォームでサブグリッド コンポーネントを追加して構成する  
レコードの詳細の表示するフォームは、表形式の関連するレコードや非関連レコードの一覧を表示するサブグリッド コンポーネントを使用できます。 メーカーはフォーム デザイナーを使用してサブグリッド コンポーネントを追加して構成できます。

## <a name="add-a-sub-grid-component"></a>サブグリッド コンポーネントのの追加
サブグリッド コンポーネントは、その他のコンポーネントの追加方法と同じ方法で追加します。 詳細: [フォームでコンポーネントを追加、構成、移動、削除する](add-move-configure-or-delete-components-on-form.md)

## <a name="configure-a-sub-grid-component"></a>サブグリッド コンポーネントの構成
これらは、フォーム デザイナーを使用してフォームでサブグリッド コンポーネントを使用する場合に、構成に使用できるプロパティです。


|面積   |Name  |説明  |
|---------|---------|---------|
| **表示オプション** | **ラベル** | ユーザーに表示されるサブグリッドのローカライズ可能なラベル。 <br /><br />このプロパティが必要です。|
| **表示オプション** |  **名前** |  スクリプト内でサブグリッドが参照されたとき使用される一意の名前。 名前には、英数字とアンダースコアのみを使用できます。 <br /><br />このプロパティが必要です。 |
| **表示オプション** | **電話の非表示** |  サブグリッドは非表示にして、電話の画面のフォームの要約版バージョンをレンダーできます。 |
| **表示オプション** | **関連するレコードの表示** |  選択すると、サブグリッドにはフォームに表示されている現在のレコードに関連するレコードのみが表示されます。 <br /><br />**エンティティ**ドロップダウン リストは、現在のエンティティと関連するエンティティのみ一覧表示するようにフィルター処理もされます。 |
| **表示オプション** | **エンティティ** |  サブグリッドで表示したいレコードのエンティティ。 <br /><br />**関連レコードを表示**が選択されている場合、現在のエンティティと関連するエンティティのみを表示するように、エンティティの一覧がフィルターされます。 エンティティ名に加えて、参照フィールドの名前は、括弧内にも表示されます。 |
| **表示オプション** | **既定のビュー** |  サブグリッド内の記録のリストを取得して表示するために使用される**エンティティ**プロパティ内で選択された、エンティティのビュー。 |
| **表示オプション** | **ユーザーがビューを変更することを許可** |  選択すると、アプリ ユーザーは**既定ビュー**から**エンティティ**プロパティで選択したエンティティの別のビューへと変更することができます。 |
| **表示オプション** | **すべてのビューを表示** |  選択すると、アプリ ユーザーは**既定ビュー**から**エンティティ**プロパティで選択したエンティティのすべてのその他のビューへと変更することができます。 <br /><br />このプロパティは、**ユーザーがビューを変更することを許可**が選択された場合にのみ使用できます。 |
| **表示オプション** | **選択されたビュー** |  アプリ ユーザーが**規定ビュー**から/へと変更できる **エンティティ**プロパティ内で選択されたエンティティのビューのリスト。 <br /><br />このプロパティは、**ユーザーがビューを変更することを許可**が選択され、**すべてのビューを表示**がクリアになっている場合にのみ利用できます。 |

## <a name="see-also"></a>関連項目
[モデル駆動型フォーム デザイナーの概要](form-designer-overview.md)  
[フォーム デザイナーを使用してフォームを作成、編集、構成する](create-and-edit-forms.md)  
[フォーム上のフィールドを追加、構成、移動、削除する](add-move-or-delete-fields-on-form.md)  
[フォーム上のコンポーネントを追加、構成、移動、削除する](add-move-configure-or-delete-components-on-form.md)  
[フォーム上のセクションを追加、構成、移動、削除する](add-move-or-delete-sections-on-form.md)  
[フォーム上のタブを追加、構成、移動、削除する](add-move-or-delete-tabs-on-form.md)  
[フォーム デザイナーでヘッダーのプロパティを構成する](form-designer-header-properties.md)  
[フォームで簡易表示コンポーネントを追加して構成する](form-designer-add-configure-quickview.md)  
[フォームの検索コンポーネントを構成する](form-designer-add-configure-lookup.md)  
[フォーム デザイナーのツリー ビューを使用](using-tree-view-on-form.md)  
[フィールドの作成および編集](../common-data-service/create-edit-field-portal.md)  
