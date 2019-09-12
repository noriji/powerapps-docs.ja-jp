---
title: フォームデザイナでヘッダーのプロパティを構成する | MicrosoftDocs
ms.custom: ''
ms.date: 08/02/2019
ms.reviewer: ''
ms.service: crm-online
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

# <a name="configure-header-properties-in-the-form-designer"></a>フォーム デザイナーでヘッダーのプロパティを構成する
作業者はフォームを使用しているユーザーのニーズに合わせてモデル駆動型のアプリケーション フォームのヘッダー密度を制御できます。

## <a name="high-density-header"></a>高密度ヘッダー
高密度フォームのヘッダーにより、重要な情報が常にユーザーに表示されます。 高密度ヘッダーを使用すると、レコードのタイトルが切り捨てられることがありません。 長いレコードタイトルも複数行を使って表示されます。 同様に、高密度ヘッダーでは、最大で4つまでのフィールド値がヘッダーに直接表示され、切り捨てられたり非表示になったりすることがありません。  

重要な情報が常に表示されるようにするために、フレームワークは読み取り専用のフィールド値を表示し、ユーザーはヘッダーのフィールド値を直接編集することができません。 カスタム コントロールや Webリソースなどの視覚表現にも対応していません。

フォームでヘッダーの密度が指定されていない場合や、新しいフォームが作成された場合、フレームワークでは既定で高密度ヘッダーが使用されます。

> [!div class="mx-imgBorder"] 
> ![高密度フォームのヘッダー](media/form-header-high-density.png "高密度フォームのヘッダー")
    
## <a name="low-density-header"></a>低密度ヘッダー
フォームヘッダーの密度が低い場合は、ヘッダーのフィールド値を直接編集することができます。 カスタム コントロールや Webリソースなどの視覚表現にも対応しています。  
  
ただし、重要な情報が切り捨てられたり、表示されなくなったりすることが発生しやすいことが想定されます。 低密度のヘッダーでは、ヘッダーに表示されるフィールド値だけでなく、レコードタイトルも切り捨てられます。 多くの場合、ヘッダーに1つから2つのフィールドのみが表示されますが、残りのフィールドは表示されずポップアップに格納されます。この表示しきれない部分を表示するには、余分なクリックをする必要があります。

> [!div class="mx-imgBorder"] 
> ![低密度フォームのヘッダー](media/form-header-low-density.png "低密度フォームのヘッダー")

### <a name="configuring-header-density"></a>ヘッダー密度の構成

駆動型モデルのフォームのヘッダーの密度を構成するには、次の手順に従います。
1.  フォーム デザイナーを開いて [フォームの作成または編集をします](create-and-edit-forms.md)。
2.  フォームのプレビューでヘッダーを選択するか、 [ツリービュー](using-tree-view-on-form.md)を使用してフォームヘッダーを選択します。
3.  プロパティ ウィンドウで、高密度フォームヘッダーを使用する場合は **高密度** を選択し、低密度フォームヘッダーを使用する場合はこれをクリアします。
4.  コマンド バーで、 **保存** を選択してフォームを保存するか、 **公開** を選択して変更を保存すると同時にユーザーに公開します。

> [!NOTE]
> 新しいフォーム デザイナーを使用してください。 従来のフォームデザイナには、ヘッダーの密度を設定する機能はありません。

## <a name="header-flyout"></a>ヘッダーのポップアップ
ヘッダーのポップアップは、ユーザーがフォームのヘッダーで山形マークを選択すると表示されます。 これにより、ユーザーはフィールド値を編集したり、フォームヘッダーの一部であるカスタムコントロールやWebリソースなどを視覚化して表示することができます。

ヘッダのポップアップの動作は、ヘッダ密度の設定によって異なります。

### <a name="high-density-header-flyout"></a>高密度ヘッダーのポップアップ
高密度のフォームヘッダーを使用すると、ヘッダーのポップアップには、ヘッダーに直接表示される4つのフィールドを含むすべてのヘッダーフィールドが表示されます。 フレームワークでは、高密度ヘッダーが使用されている場合、既定でヘッダーのポップアップが表示されます。 高密度ヘッダを使用することで、ヘッダーのポップアップの表示/非表示をコントロールできます。

> [!div class="mx-imgBorder"] 
> ![高密度ヘッダーのヘッダーポップアップ](media/form-header-flyout-high-density.png "高密度ヘッダーのヘッダーポップアップ")

### <a name="low-density-header-flyout"></a>低密度ヘッダーのポップアップ
フォームヘッダーが低密度の場合、ヘッダーのポップアップには表示しきれないフィールドのみが表示されます (たとえば、フォームの幅の設定が原因でフォームがヘッダーに直接表示できないフィールドなど)。 また、ヘッダーのポップアップは、ヘッダーのフィールド数とフォームの幅の設定に基づいて、自動的に表示または非表示になります。 低密度ヘッダーを使用すると、ヘッダーのポップアップの表示/非表示を制御できません。

> [!div class="mx-imgBorder"] 
> ![低密度ヘッダーのヘッダーポップアップ](media/form-header-flyout-low-density.png "低密度ヘッダーのヘッダーポップアップ")

### <a name="show-or-hide-the-header-flyout"></a>ヘッダーのポップアップの表示または非表示
モデル駆動型フォームのヘッダーポップアップを表示または非表示にするには、以下の手順に従います。

1.  フォーム デザイナーを開いて [フォームの作成または編集をします](create-and-edit-forms.md)。
2.  フォームのプレビューでフォーム ヘッダーを選択するか、 [ツリービュー](using-tree-view-on-form.md) を使用してフォーム ヘッダーを選択します。
3.  プロパティ ウィンドウで、高密度フォームヘッダーを使用するには **高密度** を選択します。 
4.  プロパティペインで、 **ヘッダーのポップアップを表示する** を選択してヘッダーのポップアップを表示するか、選択を解除してヘッダーのポップアップを非表示にします。
5.  コマンド バーで、 **保存** を選択してフォームを保存するか、 **公開** を選択して変更を保存すると同時にユーザーに公開します。

> [!NOTE]
> - 新しいフォームデザイナーを使用して下さい。従来の フォームデザイナーには、ヘッダーのポップアップを表示または非表示にする機能はありません。   
> - ヘッダーのポップアップの表示/非表示は、高密度フォームヘッダを使用する場合にのみ制御することができます。 低密度のヘッダーを使用すると、ヘッダーのフィールド数とフォームの幅に基づいて、ヘッダーのポップアップが自動的に表示または非表示になります。

## <a name="form-designer-messages-related-to-form-headers"></a>フォームヘッダーに関連するフォーム デザイナーのメッセージ
新しいフォームデザイナーまたは従来のフォームデザイナーを使用してフォームを編集すると、フォームヘッダーに関連するメッセージが表示される場合があります。 以下に、各メッセージの詳細と表示される原因を示します。

### <a name="weve-upgraded-your-form-to-show-a-high-density-header-that-displays-more-data-you-can-edit-this-setting-in-the-properties-of-the-header"></a>フォームがアップグレードされました。より多くのデータを表示することができる高密度のヘッダーが実装されました。 この設定は、ヘッダーのプロパティで編集することができます。 
このメッセージは、新しいメインフォームを作成したとき (「名前を付けて保存」 アクションを使用した場合を含む) や、ヘッダーの密度が設定されていないメインフォームを編集したときに、フォームデザイナに表示されます。  
  
フレームワークはデフォルトで高密度ヘッダーに設定されており、このメッセージは作業者がその動作を認識するのに役立ちます。 前述のように手動でフォームヘッダーの密度を設定することで、いつでも既定のフレームワークを上書きできます。

### <a name="this-form-isnt-using-high-density-header-access-the-setting-in-the-header-properties-high-density-header-helps-display-more-data"></a>このフォームでは高密度ヘッダーが使用されていません。ヘッダーのプロパティの設定にアクセスしてください。 高密度ヘッダーでは、より多くのデータを表示することができます。 
このメッセージは、低密度ヘッダーを使用するように設定された編集用のメインフォームを作業者が開いた際に、フォームデザイナに表示されます。      
  
このメッセージは、高密度ヘッダーとその利点についての認識を高めるにあたって役立ちます。

### <a name="field-moved-to-header-flyout-the-header-supports-displaying-up-to-four-read-only-field-values-the-field-field-display-name-will-now-only-be-available-from-the-flyout"></a>フィールドがヘッダーのポップアップに移動しました: ヘッダーには、最大で4つまでの読み取り専用のフィールド値を表示することができます。 *[field display name]* フィールドはポップアップからのみ利用することができます。
このメッセージは、フォームがヘッダーのポップアップを表示した状態で高密度ヘッダーを使用している場合に、フォームデザイナーに表示されます。  
  
高密度ヘッダーでは、ヘッダーの最初の4つのフィールドの値が読み取り専用で表示されます。 ヘッダーの上部4つの位置にフィールドを追加すると、ヘッダーに直接表示されていた既存のフィールドが拡張され、ヘッダーのポップアップにのみ表示されるようになります。      
  
このメッセージは、作業者に変更を通知し、処理を続行するかどうかを確認します。

### <a name="header-field-limit-exceeded-the-header-supports-displaying-up-to-four-read-only-field-values-remove-unused-fields-to-add-more"></a>ヘッダーのフィールド制限を超えました: ヘッダーには、最大で4つまでの読み取り専用のフィールド値を表示することができます。 フィールドを追加するには、未使用のフィールドを削除してください。 
このメッセージは、フォームがヘッダーのポップアップを非表示にした状態で高密度ヘッダーを使用している場合に、フォームデザイナーに表示されます。  
  
高密度ヘッダーでは、ヘッダーに最大で4つまでの読取り専用のフィールド値を表示することができます。 ヘッダーのポップアップは非表示であるため、ユーザは追加のフィールドを見ることができません。  
  
このメッセージは、ヘッダーに既に4つのフィールドが設定されていることを作業者に通知し、ユーザーが見ることのできなしフィールドがヘッダーに追加されないように機能します。

### <a name="header-does-not-display-custom-components-the-header-supports-displaying-up-to-four-read-only-field-values-remove-the-custom-component-from-the-field-before-adding-it-to-the-header"></a>ヘッダーはカスタム コンポーネントに対応していません: ヘッダーには、最大で4つまでの読み取り専用のフィールド値を表示することができます。 カスタム コンポーネントをフィールドから削除してください。  
このメッセージは、フォームがヘッダーのポップアップを非表示にした状態で高密度ヘッダーを使用している場合に、フォームデザイナーに表示されます。  
  
高密度ヘッダーは、ヘッダー内の読み取り専用のフィールド値を表示します。 ヘッダーのポップアップが非表示になっているため、ユーザーはヘッダーのフィールドに関連付けられているカスタムコンポーネントを表示することができません。  
  
このメッセージは、ヘッダーにカスタム コンポーネントが関連付けられているフィールドが追加されようとしており、フィールドをヘッダーに追加する前にカスタム コンポーネントを削除する必要がある旨を作業者に通知します。 これは、ユーザーがヘッダー内のカスタムコンポーネントを見ることができないためです。

### <a name="header-displays-read-only-field-values-the-header-supports-displaying-up-to-four-read-only-field-values-to-provide-editability-to-the-user-add-the-field-to-a-section-in-the-form"></a>ヘッダーには読取り専用フィールド値を表示します :ヘッダーには、最大で4つまでの読み取り専用のフィールド値を表示することができます。 編集可能とするには、フォームのセクションにフィールドを追加してください。  
このメッセージは、フォームがヘッダーのポップアップを非表示にした状態で高密度ヘッダーを使用している場合に、フォームデザイナーに表示されます。  
  
高密度ヘッダーは、ヘッダー内の読み取り専用のフィールド値を表示します。 ヘッダーのポップアップは非表示であるため、フィールドの値を編集することはできません。  
  
このメッセージでは、ヘッダーに追加されたすべてのフィールドが読み取り専用となり、ユーザーが編集できるフィールドもフォーム内のセクションに追加する必要がある旨を通知します。

### <a name="header-field-values-are-not-editable-moving-a-field-from-the-body-to-the-header-will-display-as-a-read-only-value-to-maintain-editability-copy-the-field-to-the-header"></a>ヘッダー フィールド値を編集することはできません: フィールドをボディからヘッダーに移動すると、読み取り専用の値として表示されます。 編集可能性を維持するには、フィールドをヘッダーにコピーしてください。  
このメッセージは、ヘッダーのポップアップを非表示にした高密度ヘッダーを使用しているフォームの場合にのみ、フォームデザイナーに表示されます。  
  
高密度ヘッダーは、ヘッダー内の読み取り専用のフィールド値を表示します。 ヘッダーのポップアップは非表示であるため、フィールドの値を編集することはできません。  
  
このメッセージは、フォームのボディからフォームのヘッダーにフィールドを移動しようとしていることを意味しています。 これをすることで、読み取り専用となります。 フィールドをヘッダーに移動するか、フィールドのコピーをヘッダーに追加するかを選択できます。 フィールドをヘッダーに移動すると、フォームボディの本来の場所でユーザーが編集することができなくなります。 フィールドのコピーをヘッダーに追加すると、フィールドは元の場所に残り、ユーザーはフォームのボディ内で引き続き編集することができます。

### <a name="form-headers-now-default-to-high-density-to-display-more-data-use-the-new-form-designer-to-edit-header-density"></a>高密度のフォームヘッダーが既定となり、より多くのデータが表示されるようになりました。 新しいフォームデザイナーを使用して、ヘッダーの密度を編集します。  
このメッセージは、低密度ヘッダーを使用するように設定されているメインフォームを編集などの目的で開いた場合に、旧式のフォームデザイナーで表示されます。  
  
このメッセージによって、高密度ヘッダーとその利点についての認識が高めることができ、新しいフォーム デザイナーへと切り替えてヘッダー密度を設定するように促します。  

### <a name="this-form-is-using-high-density-header-for-the-best-authoring-experience-with-this-form-use-the-new-form-designer"></a>このフォームは高密度ヘッダーを使用しています。 このフォームのオーサリングを最適化するには、新しいフォームデザイナーを使用してください。 
 このメッセージは、高密度ヘッダーを使用するように設定されているメインフォームを編集などの目的で開いた場合に、旧式のフォームデザイナーで表示されます。  
  
旧式のフォームデザイナーでは、WYSIWYG オーサリング エクスペリエンスが提供されていません。 フォームヘッダーに加えた変更に対して、その影響を検出したり、警告をすることができません。 たとえば、ヘッダーのポップアップを非表示にして高密度ヘッダーを使用しているフォームを編集する場合に、旧式のフォームデザイナーでは、ヘッダーに4つ以上のフィールドを追加できますが、これらのフィールドをユーザーは利用することができません。  
  
このメッセージは、高密度ヘッダーを使用しているフォームを編集する際に、新しいフォームデザイナーを使用する必要があることを作業者に通知します。 これにより、フォームヘッダーに対する変更の影響を作業者が認識することができるようになります。

## <a name="see-also"></a>関連項目
[モデル駆動型フォーム デザイナーの概要](form-designer-overview.md)  
[フォーム デザイナーを使用してフォームを作成または編集](create-and-edit-forms.md)  
[フォーム デザイナーを使用してフォームのフィールドを追加、移動、または削除](add-move-or-delete-fields-on-form.md)  
[フォーム デザイナーを使用してフォームのセクションを追加、移動、または削除](add-move-or-delete-sections-on-form.md)  
[フォーム デザイナーを使用してフォームのタブを追加、移動、または削除](add-move-or-delete-tabs-on-form.md)  
[フォーム デザイナーで使用可能なプロパティ](form-designer-properties.md)  
[フォーム デザイナーでヘッダーのプロパティを構成する](form-designer-header-properties.md)  
[フォーム デザイナーのツリー ビューを使用](using-tree-view-on-form.md)  
[フィールドの作成および編集](../common-data-service/create-edit-field-portal.md)