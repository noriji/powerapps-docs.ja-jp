---
title: モデル駆動型フォーム デザイナを使用してフォームの作成、編集、構成をする | MicrosoftDocs
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

# <a name="create-edit-or-configure-forms-using-the-form-designer"></a>フォーム デザイナーを使用してフォームを作成、編集、構成する 
新しいフォームデザイナーを使用して、モデル駆動型アプリケーションのフォームを作成、編集、構成をします。 

> [!IMPORTANT]
> 新しいモデル駆動型フォーム デザイナは、現在のところ名刺フォームの編集に対応していません。 詳細: [フォームの種類](types-forms.md)

## <a name="create-a-form"></a>フォームの作成 
1. [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) にサインインします。 
2. 左のナビゲーション ウィンドウで、**データ**を展開してから、**エンティティ**を選択します。 
3. 取引先企業エンティティなどのエンティティを選択してから、**フォーム**タブを選択します。 
4. **フォームの追加** をクリックし、以下のいずれかを選択します。
    - **メイン フォーム**  
    新しいフォームのコンテンツは、既存のメイン フォームの定義を使用して入力されます。 複数のメイン フォームが存在する場合は、フォーム順序のリストの一番上にあるフォームを使用して新しいフォームに入力されます。 
    - **簡易作成フォーム**
    - **簡易表示フォーム**
5. フォームへの変更が完了したら、 **保存** を選択してフォームを保存し、 **公開** を選択して、アプリケーションのユーザーに変更内容を公開します。  

## <a name="edit-a-form"></a>フォームの編集 
1. [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) にサインインします。 
2. 左のナビゲーション ウィンドウで、**データ**を展開してから、**エンティティ**を選択します。 
3. 取引先企業エンティティなどのエンティティを選択してから、**フォーム**タブを選択します。
4. 編集を行うフォームの名称を選択します。  
    - フォームの行を選択し、コマンドバーにて **フォームの編集 (プレビュー)** を選択することもできます。
    - 他の方法としては、フォーム名称の隣の **...** を選択し、メニューにて **フォームの編集 (プレビュー)** を選択することもできます。 
5. フォームへの変更が完了したら、 **保存** を選択してフォームを保存し、 **公開** を選択して、アプリケーションのユーザーに変更内容を公開します。 

## <a name="configure-a-form"></a>フォームを構成する
これらは、フォーム デザイナーを使用してフォームを作成、編集する場合に、フォームを構成する目的で使用することができるプロパティです。

|Name  |説明  |
|---------|---------|
|**タイトル**  | 他のメーカー、あるいはアプリケーションのユーザーにとって意味がある名前を入力します。 この名前はアプリケーションのユーザーに表示されます。 ユーザーがひとつのエンティティの複数のフォームにアクセス権を持っている場合は、利用可能なフォームを区別する目的でこの名前を使用します。 <br /><br />このプロパティが必要です。 |
|**説明** |  フォームがその他のメイン フォームとは異なる点を表す説明を入力します。 この説明は、ソリューション エクスプローラーのエンティティのフォーム一覧にのみ表示されます。 |
|**最大幅** | フォームの幅を制限する最大幅 (ピクセル単位) の設定。 既定値は 1900 です。 <br /><br />このプロパティが必要です。 |
|**イメージの表示** | そのエンティティに **プライマリ イメージ** がある場合はそれを表示します。 この設定によってフォームのヘッダーに画像フィールドが表示されるようになります。 <br /><br /> エンティティのオプションについては、「エンティティのオプションを有効化または無効化」を参照してください。 |

## <a name="see-also"></a>関連項目
[モデル駆動型フォーム デザイナーの概要](form-designer-overview.md)  
[フォーム上のフィールドを追加、構成、移動、削除する](add-move-or-delete-fields-on-form.md)  
[フォーム上のコンポーネントを追加、構成、移動、削除する](add-move-configure-or-delete-components-on-form.md)  
[フォーム上のセクションを追加、構成、移動、削除する](add-move-or-delete-sections-on-form.md)  
[フォーム上のタブを追加、構成、移動、削除する](add-move-or-delete-tabs-on-form.md)  
[フォーム デザイナーでヘッダーのプロパティを構成する](form-designer-header-properties.md)  
[フォームでサブグリッド コンポーネントを追加して構成する](form-designer-add-configure-subgrid.md)  
[フォームで簡易表示コンポーネントを追加して構成する](form-designer-add-configure-quickview.md)  
[フォームの検索コンポーネントを構成する](form-designer-add-configure-lookup.md)  
[フォーム デザイナーのツリー ビューを使用](using-tree-view-on-form.md)  
[フィールドの作成および編集](../common-data-service/create-edit-field-portal.md)  
