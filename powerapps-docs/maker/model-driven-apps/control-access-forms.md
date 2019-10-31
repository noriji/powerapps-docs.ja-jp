---
title: PowerApps でモデル駆動型アプリのフォームへのアクセスを制御する | MicrosoftDocs
description: メイン フォームへのアクセスを制御する方法
ms.custom: ''
ms.date: 06/18/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
author: Mattp123
ms.assetid: 15d123e0-b604-45dd-ab34-0b37787a04bb
caps.latest.revision: 33
ms.author: matp
manager: kvivek
tags: null
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="control-access-to-model-driven-app-forms"></a>モデル駆動型アプリへのアクセスを制御する

 メイン フォームへのアクセスを制御する方法には、次の 2 つがあります。  
  
- **メイン フォームを非アクティブにする**  
  
     メイン フォームはアクティブまたは非アクティブな状態に設定することができます。 この機能は、主に Common Data Service 環境アップグレードに含まれている新しいフォームを管理する目的で実装されていますが、ユーザーにメインフォームを使用させない用途で使用することもできます。   
  
- **メイン フォームへセキュリティ ロールを割り当てる**  
  
     メイン フォームを特定のグループが使用できるようにするために、これを使用します。  
  
 組織のさまざまなユーザーがさまざまな方法で同じデータとやり取りすることがあります。 管理者はレコード内の情報の迅速な取り込みができることに依存する場合があり、サービス要員はデータ入力を簡素化するフォームを必要とする場合があります。 さまざまなユーザーのグループが所属するセキュリティ ロールにフォームを割り当てることによって、さまざま要件に対応できます。  
  
 詳細な手順については、[フォームへのセキュリティ ロールの割り当て](https://docs.microsoft.com/dynamics365/customer-engagement/admin/assign-security-roles-form) を参照してください。  
  
 複数のメイン フォームまたは別の種類のフォームがエンティティに定義されている場合は、ユーザーが自分たちのセキュリティ ロールに基づいてどのフォームを使用できるかを選択できます。 各エンティティはどのユーザーのフォームでも表示できる必要があるので、少なくとも 1 つのフォームを "フォールバック" フォームとして指定する必要があります。フォールバック フォームとは、明示的にフォームに割り当てられていないセキュリティ ロールを持つユーザーに対して表示されるフォームです。  
  
> [!NOTE]
>  簡易作成、簡易表示、そしてカード フォームをセキュリティ ロールに割り当てることはできません。  
  
 フォーム エディター内またはフォーム グリッドからセキュリティ ロールをメイン フォームに割り当てることができます。 ただし、エンティティのフォームが 1 つだけの場合、**セキュリティ ロールの割り当て**ダイアログ ボックスの**フォールバックとして有効**オプションをクリアできません。 この場合、フォームにセキュリティ ロールを割り当て済みであっても、そのフォームはフォールバック用に有効であるため、含めなかったセキュリティ ロールに関連付けられているユーザーは引き続きフォームを表示できます。  
  
 エンティティの 2 つ目のメイン フォームを作成した後は、どちらかのフォームについて **フォールバックとして有効** オプションをクリアできます。 少なくとも 1 つのフォームがフォールバック用に有効になっていることがシステムによって必ず確認されます。  
  
 複数のメイン フォームがある場合、ユーザーに表示できるフォームのいずれかが既定で表示されるフォームになるように制御する、フォームの順序を指定できます。 ユーザーが使用できるフォームが複数ある場合、ユーザーはフォームを変更することが可能であり、選択したフォームは、別のフォームを選択するまで既定のフォームとなります。 この設定はブラウザーに保存されます。 別のコンピューターまたはブラウザーを使用する場合、元の既定のフォームが表示されます。  
  
## <a name="strategies-to-manage-the-fallback-form"></a>フォールバック フォームの管理方法  
 フォールバック ファームの管理方法は次のとおりです。  
  
<a name="BKMK_DoNotUseMultipleForms"></a>   
### <a name="all-users-view-the-same-form"></a>すべてのユーザーが同じフォームを表示  
 エンティティで複数のフォームが必要ない場合、フォールバック フォームは不要です。  
  
<a name="BKMK_Contingecyform"></a>   
### <a name="create-a-contingency-form"></a>代替フォームの作成  
 ロールベースのフォームを使用して、ユーザーが表示または編集する情報を制限する場合は、最小限の情報が表示されるフォームの作成を検討してください。 次に、**セキュリティ ロールの割り当て**ダイアログ ボックスで、**選択されている次のセキュリティ ロールに対してのみ表示する**を選択し、システム管理者以外のロールは選択せずに、**フォールバックとして有効**を選択します。 結果的に、このフォームはシステム管理者および特定のフォームに関連付けられていないセキュリティ ロールを持つユーザーを除くユーザーには表示されません。 フォームには HTML Web リソースを含めることができます。このリソースには、フォームに表示されている情報が少ない理由に関する情報、およびフォームに関連付けられているセキュリティ ロールへの追加を要求する方法またはフォームの新しいセキュリティ ロールを含める方法に関する情報へのリンクが含まれます。  
  
> [!NOTE]
>  web リソースはフォーム ヘッダーまたはフッターに含めることができません。  
  
<a name="BKMK_CreateGenericForm"></a>   
## <a name="create-a-generic-form"></a>汎用フォームの作成  
 ロールベースのフォームを使用して、ユーザーの役割を基にユーザー エクスペリエンスをカスタマイズする場合は、汎用フォームをフォールバック フォームとして設定し、すべてのユーザーに対してそのフォームを表示するよう構成できます。 次に、特定のセキュリティ ロール用にカスタマイズしたフォームを作成し、そのフォームを必要とするセキュリティ ロールに対してのみ表示するよう構成します。 これらのフォームをフォールバック用に有効にしないでください。 最後に、**フォーム**の一覧で、**フォームの順序**ダイアログを使用して、特殊性の高い順にランク付けを表示するフォームを指定します。 フォールバック フォームは一覧の一番下に表示されます。 この方法では、ユーザーの役割に合わせてカスタマイズされていないフォームが既定のフォームとして表示されますが、必要に応じてフォーム セレクターを使用して、最も一般的なフォームを選択することもできます。 選択したフォームは、別のフォームを選択するまで既定のフォームになります。  
  
<a name="BKMK_UseFormScripting"></a>   
## <a name="use-form-scripting"></a>フォーム スクリプトを使用する  
クライアント API フォーム コンテキスト (formContext) は、フォームまたは、現在のコードが実行される、簡易表示コントロールまたは編集可能グリッドの列などの、フォーム上のアイテムへの参照を提供します。 詳細: [クライアント API フォーム コンテキスト](/dynamics365/customer-engagement/developer/clientapi/clientapi-form-context)

> [!IMPORTANT]
> Xrm.Page オブジェクトは[非推奨](/dynamics365/get-started/whats-new/customer-engagement/important-changes-coming#some-client-apis-are-deprecated)となっているため、渡された実行コンテキスト・オブジェクトの [getFormContext](/powerapps/developer/model-driven-apps/clientapi/reference/executioncontext/getformcontext) メソッドを使用して、該当するフォームまたはフォーム上の項目へと参照を戻す必要があります。
<!-- 
 Finally, in the web application it is possible, but not recommended, for a developer to use scripts in the form Onload event to use the [Xrm.Page.ui.formSelector.items collection](http://go.microsoft.com/fwlink/p/?LinkID=513300) to query available forms and use the navigate method to direct users to a specific form. Remember that the [navigate method](http://go.microsoft.com/fwlink/p/?LinkID=513301) will cause the form to load again (and the Onload event to occur again). Your logic in the event handler should always check some condition before you use the navigate method to avoid an endless loop or unnecessarily restrict users options to navigate between forms.  
  
 This approach will not work for Dynamics 365 for tablets because multiple forms are not available for selection.  -->

### <a name="see-also"></a>関連項目  

[フォームへのセキュリティ ロールの割り当て](https://docs.microsoft.com/dynamics365/customer-engagement/admin/assign-security-roles-form)
