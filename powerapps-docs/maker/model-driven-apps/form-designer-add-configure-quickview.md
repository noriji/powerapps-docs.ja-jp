---
title: フォームで簡易表示コンポーネントを追加して構成する | MicrosoftDocs
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

# <a name="add-and-configure-a-quick-view-component-on-a-form"></a>フォームで簡易表示コンポーネントを追加して構成する  
レコードの詳細を表示するメイン フォームは、関連するレコード (参照) の読み取り専用の詳細を表示するための簡易表示コンポーネントを使用できます。 簡易表示コンポーネントによって表示されるデーターは、関連エンティティの簡易表示フォームによって定義されます。 参照など関連するレコードがない場合は、簡易表示コンポーネントは自動的に非表示になります。

## <a name="add-a-quick-view-component"></a>簡易表示コンポーネントを追加する
簡易表示コンポーネントは、その他のコンポーネントの追加方法と同じ方法で追加します。 詳細: [フォームでコンポーネントを追加、構成、移動、削除する](add-move-configure-or-delete-components-on-form.md)

## <a name="configure-a-quick-view-component"></a>簡易表示コンポーネントの構成
フォーム デザイナーを使用してフォームで簡易表示コンポーネントを使用する場合、構成するために使用できるプロパティがあります。


<!--note from editor: "Drop-down" should be used only as an adjective. In the following table, is it a list? A menu? (It's used three times in line 44.) --> 


|面積   |Name  |説明  |
|---------|---------|---------|
|**表示オプション** | **ラベル** | ユーザーに表示される簡易表示のローカライズ可能なラベル。 <br /><br /> このプロパティが必要です。 |
| **表示オプション** | **名前** |  スクリプト内で簡易表示が参照されたとき使用される一意の名前。 名前には、英数字とアンダースコアのみを使用できます。 <br /> <br />このプロパティが必要です。 |
| **表示オプション**  | **ラベルの非表示** |  選択すると、簡易表示ラベルは非表示になります。 |
| **表示オプション**  | **簡易表示フォーム** |  アプリ ユーザーに表示される簡易表示フォームの一覧。 <br /><br />簡易表示フォームの一覧を構成するには <br /><br /> **フォームの選択**を選択して、**参照**ドロップダウンで、簡易表示フォームを表示したい検索フィールドを選択します。 <br /><br />**参照**ドロップダウンで選択した参照フィールドによって、一つまたは複数のエンティティに対して選択できる簡易表示フォームのドロップダウンが表示されます。 |

## <a name="see-also"></a>関連項目
[モデル駆動型フォーム デザイナーの概要](form-designer-overview.md)  
[フォーム デザイナーを使用してフォームを作成、編集、構成する](create-and-edit-forms.md)  
[フォーム上のフィールドを追加、構成、移動、削除する](add-move-or-delete-fields-on-form.md)  
[フォーム上のコンポーネントを追加、構成、移動、削除する](add-move-configure-or-delete-components-on-form.md)  
[フォーム上のセクションを追加、構成、移動、削除する](add-move-or-delete-sections-on-form.md)  
[フォーム上のタブを追加、構成、移動、削除する](add-move-or-delete-tabs-on-form.md)  
[フォーム デザイナーでヘッダーのプロパティを構成する](form-designer-header-properties.md)  
[フォームでサブグリッド コンポーネントを追加して構成する](form-designer-add-configure-subgrid.md)  
[フォームの検索コンポーネントを構成する](form-designer-add-configure-lookup.md)  
[フォーム デザイナーのツリー ビューを使用](using-tree-view-on-form.md)  
[フィールドの作成および編集](../common-data-service/create-edit-field-portal.md)  
