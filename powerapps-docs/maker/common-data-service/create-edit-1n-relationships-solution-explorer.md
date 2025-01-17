---
title: 'ソリューション エクスプローラーを使用して 1:N (1 対多) または N:1 (多対 1) のエンティティ関連付けを作成および編集する | MicrosoftDocs'
description: PowerApps ソリューション エクスプローラーを使用して 1 対多または多 対 1 のエンティティ関連付けを作成する方法について説明します
ms.custom: ''
ms.date: 10/28/2018
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

# <a name="create-and-edit-1n-one-to-many-or-n1-many-to-one-entity-relationships-using-solution-explorer"></a>ソリューション エクスプローラーを使用して 1:N (1 対多) または N:1 (多対 1) のエンティティ関連付けを作成および編集する 

ソリューション エクスプローラーでは Common Data Service において、 1:N (1 対多) または N:1 (多対 1) のエンティティの関係性を作成または編集することができます。

[PowerApps ポータル](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)では一般的なオプションのほどんとを構成できますが、特定のオプションはソリューション エクスプローラーを使用してのみ設定できます。 詳細: 
- [1:N (一対多) または N:1 (多対一) の関連付けを作成する](create-edit-1n-relationships.md)
- [PowerApps ポータルを使用して 1:N (1 対多) または N:1 (多対 1) のエンティティ関連付けを作成および編集する](create-edit-1n-relationships-portal.md)
  
## <a name="open-solution-explorer"></a>ソリューション エクスプローラーを開きます

作成するユーザー定義関連付けの名前の一部はカスタマイズの接頭辞です。 これは、作業中のソリューションの発行者に基づいて設定されます。 カスタマイズの接頭辞に注意を払う場合は、カスタマイズの接頭辞がこのエンティティに対して必要な接頭辞であるアンマネージド ソリューションで作業するようにします。 詳細: [ソリューション発行者の接頭辞を変更する](change-solution-publisher-prefix.md) 

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

## <a name="view-entity-relationships"></a>エンティティの関連付けを表示する

ソリューション エクスプローラーで、**エンティティ** を展開し、エンティティを選択します。 そのエンティティ内で、**1:N の関連付け**または **N:1 の関連付け**を選択します。

![エンティティの関連付けを表示する](media/view-1n-entity-relationships-solution-explorer.png)

## <a name="create-relationships"></a>関連付けの作成

[エンティティ関連付けを表示](#view-entity-relationships)しているとき、コマンド バーから **新しい一対多関連付け** または **新しい多対一関連付け** を選択します。

> [!NOTE]
> コマンドを使用できない場合は、エンティティには、ユーザー定義の関連付けを作成する権限がありません。

いずれのオプションでも次のようなフォームが開きます。 違いは、**主エンティティ** と **関連エンティティ** フィールドのどちらが設定されるかです。

![新しい 1 対多関連付けフォーム](media/new-1n-entity-relationship-form-solution-explorer.png)

- **1:N の関連付け** では、**主エンティティ** は現在のエンティティに設定されます
- **N:1 の関連付け** では、**関連エンティティ** は現在のエンティティに設定されます

以下のフィールドは、エンティティ関連付けを保存するために設定する必要があります。

|必須フィールド|説明|
|--|--|
|**主エンティティ**|このエンティティは、関連エンティティで作成される検索フィールドのターゲットの種類となります。|
|**関連エンティティ**|このエンティティには、主エンティティ レコードとエンティティ レコードを関連付けるために検索フィールドが追加されます。|
|**名前**|関連付けの名前。 主エンティティおよび関連エンティティの値に基づいて値が生成されます。 このフィールドには、ソリューション発行者のカスタマイズ接頭辞が適用されます。|
|**参照フィールド表示名**|検索フィールドのローカライズ可能なテキストが関連エンティティに作成されます。 通常は、主エンティティの表示名と同じです。 <br /> これは後で変更できます。|
|**検索フィールド名**|検索フィールドの名前が関連エンティティで作成されます。 **検索フィールド表示名** に基づいて値が生成されます。 このフィールドには、ソリューション発行者のカスタマイズ接頭辞が適用されます。|

![エンティティの関連付けの保存ボタン](media/save-entity-icon-solution-explorer.png)をクリックすると、エンティティを保存して編集を続けることができます。 詳細情報: [関連付けの編集](#edit-relationships)

> [!NOTE]
> **名前** または **検索フィールド名** の値が既にシステムに存在する場合、保存するとエラーが表示されます。 一意になるように値を編集して再試行します。

## <a name="edit-relationships"></a>関連付けの編集

[エンティティの関連付けを表示](#view-entity-relationships)しているときに、編集するエンティティを選択します。 次のエンティティの関連付けプロパティを、関連付けを作成してから編集できます。

> [!NOTE]
> マネージド ソリューションの発行者は、ソリューションの一部として関連付けの一部のカスタマイズを回避できます。

### <a name="entity-relationship-properties"></a>エンティティ関連付けプロパティ

これらのプロパティは、関連付けに関するものです。

|フィールド|説明|
|--|--|
|**検索可能**|この関連付けがモデル駆動型アプリの高度な検索に表示されるかどうか。 業務上重要でない関連付けの場合は、**いいえ** を選択します。|
|**階層**|このオプションは、自己参照の関連付けでのみ有効になります。 エンティティの階層を定義するときにエンティティは対象とするかどうか。<br />**重要**: このプロパティを設定すると、このプロパティに依存するようにロールアップ フィールド、プロセス、ビューを構成できる場合があります。 この値を後で変更した場合、階層に依存する機能は機能しません。 <br />詳細情報: [階層的に関連するデータを定義およびクエリする](define-query-hierarchical-data.md)|

### <a name="lookup-field"></a>検索フィールド

関連エンティティで作成された検索フィールドのプロパティです。 プロパティはここで編集するか、検索フィールドを直接編集できます。 一部のフィールド プロパティでは関連付けから編集をすることができません。 詳細: [フィールドの編集](create-edit-field-solution-explorer.md#edit-a-field)

|フィールド|説明|
|--|--|
|**表示名**|検索フィールドのローカライズ可能なテキストが関連エンティティに作成されます。|
|**フィールド要件**|モデル駆動型アプリ内のフォームを保存する前にフィールドにデータが必要かどうか。 詳細情報: [フィールド要件オプション](create-edit-field-solution-explorer.md#field-requirement-options)|
|**説明**|フィールドの目的に関するユーザーへの指示を入力します。 これらの説明は、フィールドのラベルにマウス ポインターを置いたときに、モデル駆動型アプリのユーザーに対してツールヒントとして表示されます。|

### <a name="navigation-pane-item-for-primary-entity"></a>[主エンティティのナビゲーション ウィンドウ項目]

関連レコードを表示するには、主エンティティから移動できます。 このデータは、関連エンティティ レコードの表示方法を制御するために、モデル駆動型アプリにより使用されます。 これらの設定は、フォーム エディターを使用しても編集できます。

|フィールド|説明|
|--|--|
|**表示オプション**|関連エンティティの一覧を表示する方法。 詳細情報: [表示オプション](#display-options)|
|**カスタム ラベル**|**表示オプション** として **カスタム ラベルを使用する** を選択した場合に、複数名の代わりに使用するローカライズ可能なテキストを指定します。|
|**表示領域**|この一覧を表示するために使用できるグループの 1 つを選択します。 使用可能なオプションは **詳細** (*共通* グループ用)、**マーケティング**、**営業**、および **サービス** です。 |
|**表示順序**|ナビゲーション アイテムが選択した表示領域のどこに含まれるかを制御します。 指定できる値の範囲は 10,000 から始まります。 値の小さいナビゲーション ウィンドウ項目は、値の大きい他の関係よりも上に表示されます。|

<!-- TODO: Not sure whether Display Area or Display Order are still used anymore. Might only be used in the Outlook client?-->

#### <a name="display-options"></a>表示オプション

これらは、使用可能な表示オプションです。

|オプション|説明|
|--|--|
|**表示しない**|この関連付けの関連エンティティを表示しません。|
|**カスタム ラベルを使用する**|このオプションを選択すると、**カスタム ラベル** フィールドが有効になり、複数名の代わりに使用されるローカライズ可能なテキストを指定できます。|
|**複数形の名前を使用する**|関連するエンティティに定義した複数形の表示名を使用します。|

### <a name="relationship-behavior"></a>関連付け動作

ここでは、関連エンティティの標準動作を定義できます。 この情報は、データ整合性が確保され、会社の業務プロセスを自動化できるため重要です。

例を見てみましょう。  
  
新しい営業担当者がいて、別の営業担当者に割り当てている既存の営業案件をその新しい営業担当者に割り当てると仮定します。 各営業案件レコードには、それに関連付けられた一連タスク活動があります。 以前の所有者に再割り当てしたいまたは新しい営業担当者に割り当てたいアクティブな営業案件を簡単に見つけることができます。 しかし、営業案件に関連付けられているタスク活動の場合にはどうですか。 各タスクを開き、新しい営業担当者に割り当てるかどうかを一つずつ考慮したいですか。 したくないでしょう。 その代わり、関連付けが標準規則を自動的に適用するようにできます。 これらの規則は再割り当てする営業案件に関連付けられているタスク レコードにのみ適用されます。 次のオプションがあります。  
  
- すべてのタスク活動を再割り当てします。  
- すべてのタスクを再割り当てします。 
- タスクを全く再割り当てしません。  
- 現時点では、すべてのタスクを営業案件の以前の所有者に再割り当てします。  
  
関連付けは、主エンティティ レコードのレコードで実行された操作が関連するすべてのエンティティ レコードにどのように伝播するかを制御できます。   

特定の操作を実行するときに適用できる複数の種類の動作があります。

#### <a name="behaviors"></a>動作

これらは、構成可能な動作です。

|動作|説明|
|--|--|
|**アクティブ レコードのみに伝播**|すべてのアクティブな関連エンティティ レコードで操作を実行します。|
|**すべてのレコードに伝播**|すべての関連エンティティ レコードで操作を実行します。|
|**伝播しない**|何もしません。|
|**関連付けの解除**|すべての関連レコードの検索値を削除します。|
|**制限する**|関連エンティティ レコードが存在するときは、主エンティティ レコードが削除されないようにします。|
|**同一所有者のレコードのみに伝播**|主エンティティ レコードと同じユーザーによって所有されているすべての関連エンティティ レコードで操作を実行します。|

#### <a name="actions"></a>操作

これらは、特定の動作をトリガーできる操作です。

|フィールド|説明|Options|
|--|--|--|
|**割り当て**|主エンティティ レコードが別のレコードに割り当てられると、どうなりますか?|すべてのレコードに伝播<br />アクティブ レコードのみに伝播<br />同一所有者のレコードのみに伝播<br />伝播しない|
|**リペアレント**|上位下位の関連付けの関連エンティティの検索値が変更されると、どうなりますか。<br />詳細情報: [エンティティの上位下位の関連付け](#parental-entity-relationships)|すべてのレコードに伝播<br />アクティブ レコードのみに伝播<br />同一所有者のレコードのみに伝播<br />伝播しない|
|**共有**|主エンティティ レコードが共有されると、どうなりますか。|すべてのレコードに伝播<br />アクティブ レコードのみに伝播<br />同一所有者のレコードのみに伝播<br />伝播しない|
|**削除**|主エンティティ レコードが削除されると、どうなりますか。|すべてのレコードに伝播<br />リンクの解除<br />制限する|
|**共有の解除**|主エンティティ レコードの共有が解除されると、どうなりますか。|すべてのレコードに伝播<br />アクティブ レコードのみに伝播<br />同一所有者のレコードのみに伝播<br />伝播しない|
|**マージ**|主エンティティ レコードの共有がマージされると、どうなりますか。|すべてのレコードに伝播<br />伝播しない|
|**ロールアップ ビュー**|この関連付けに関連付けられているロールアップ ビューの希望する動作は何ですか。 |すべてのレコードに伝播<br />アクティブ レコードのみに伝播<br />同一所有者のレコードのみに伝播<br />伝播しない|

<!-- TODO: I find no official docs related to rollup views, but plenty of hits online: https://www.google.com/search?q=Dynamics+365++%27rollup+view%27 -->



#### <a name="type-of-behavior-options"></a>動作の種類オプション

一連の標準の動作を選択するか、別個に構成するかどうかを選択するには、**動作の種類** フィールドを使用します。 

|オプション|説明|
|--|--|
|**上位下位**|**割り当てる**: すべてのレコードに伝播<br />**リペアレント**: すべてのレコードに伝播<br />**共有**: すべてのレコードに伝播<br />**削除**: すべてのレコードに伝播<br />**共有の解除**: すべてのレコードに伝播<br />**結合**: 伝播しない<br />**ロールアップ ビュー**: 伝播しない \| すべてのレコードに伝播<br />|
|**参照**|**割り当てる**: 伝播しない<br />**リペアレント**: 伝播しない<br />**共有**: 伝播しない<br />**削除**: 関連付けの解除<br />**共有の解除**: 伝播しない<br />**結合**: 伝播しない<br />**ロールアップ ビュー**: 伝播しない \| すべてのレコードに伝播<br />|
|**参照、削除制限**|**割り当てる**: 伝播しない<br />**リペアレント**: 伝播しない<br />**共有**: 伝播しない<br />**削除**: 制限する<br />**共有の解除**: 伝播しない<br />**結合**: 伝播しない<br />**ロールアップ ビュー**: 伝播しない \| すべてのレコードに伝播<br />|
|**構成可能な伝播**|使用できるオプションによって各アクションごとに目的の動作を構成できます。|

> [!NOTE]
> いずれかのエンティティが上位下位の関連付けに既に参加している場合、**親** オプションを選択できなくなる場合があります。 詳細情報: [エンティティの上位下位の関連付け](#parental-entity-relationships)
> 
> **構成可能な伝播** を使用して、別の**動作の種類**と関連付けられたアクションに対する動作と一致するように、アクションに対する動作を設定する場合、関連付けを保存すると、**動作の種類**が他の種類に自動的に設定されます。  



## <a name="delete-relationships"></a>関連付けの削除

[エンティティの関連付けを表示](#view-entity-relationships)している間、削除するエンティティの関連付けを選択し、![削除コマンド](media/delete.gif) コマンドをクリックします。

関連付けを削除すると、関連エンティティの検索フィールドが削除されます。

> [!NOTE]
> 依存関係がある関連付けは削除できません。 たとえば、関連エンティティのフォームに検索フィールドを追加した場合は、関連付けを削除する前にフィールドをフォームから削除する必要があります。

## <a name="parental-entity-relationships"></a>エンティティの上位下位の関連付け

1:N の関連付けを持つことができるエンティティの各ペアの間には、1:N の関連付けが複数存在する場合があります。 その場合でも、エンティティの上位下位の関連付けを考慮できるのは、通常、そのような関連付けの中の 1 つだけです。

エンティティの上位下位の関連付けは、次の表の**上位下位である**列のカスケード オプションのいずれかが真であるような、1:N のエンティティの関連付けです。

|目的|上位下位である|上位下位ではない|  
|------------|--------------|------------------|  
|**割り当て**|すべてのレコードに伝播<br />同一所有者のレコードのみに伝播<br />アクティブ レコードのみに伝播|伝播しない|  
|**削除**|すべてのレコードに伝播|リンクの解除<br />制限する|  
|**リペアレント**|すべてのレコードに伝播<br />同一所有者のレコードのみに伝播<br />アクティブ レコードのみに伝播|伝播しない|  
|**共有**|すべてのレコードに伝播<br />同一所有者のレコードのみに伝播<br />アクティブ レコードのみに伝播|伝播しない|  
|**共有の解除**|すべてのレコードに伝播<br />同一所有者のレコードのみに伝播<br />アクティブ レコードのみに伝播|伝播しない|  

たとえば、新しい顧客エンティティを作成し、取引先企業エンティティとの 1:N のエンティティ関係を追加して、顧客エンティティが関連エンティティである場合、**上位下位である**列のオプションを使用するように、そのエンティティ関係に対する操作を構成できます。 後で、顧客エンティティとの別の 1:N エンティティ関係を、顧客エンティティを参照元エンティティとして追加する場合は、**上位下位ではない**列のオプションを使用するような操作だけを構成できます。

通常、これは各エンティティ ペアには上位下位の関連付けが 1 つだけ存在することを意味します。 複数の種類のエンティティに対して、関連エンティティでの関連付けの検索を実行できる場合があります。

たとえば、エンティティに顧客検索がある場合、取引先担当者または取引先企業エンティティを参照できます。 2 つの異なる上位下位の 1:N エンティティ関係が存在します。

すべての活動エンティティには、関係する検索フィールドを使用して関連付けることができるエンティティに対する、似た一連のエンティティの上位下位の関連付けがあります。

<a name="BKMK_RelationshipBehaviorLimitations"></a>   

### <a name="limitations-on-behaviors-you-can-set"></a>設定できる動作の制限
  
上位下位の関連付けのため、エンティティ関係を定義するときを覚えておく必要があるいくつかの制限があります。  
  
- 伝播する関連システム エンティティとの関連付けにおいて、ユーザー定義エンティティを主エンティティにすることはできません。 つまり、主ユーザー定義エンティティと関連システム エンティティの間の関連付けには、**すべてのレコードに伝播**、**アクティブ レコードのみに伝播**、または**同一所有者のレコードのみに伝播**のアクションを設定できません。  
- アクションが**すべてのレコードに伝播**、**アクティブ レコードのみに伝播**、または**同一所有者のレコードのみに伝播**に設定された別の関連付けの関連エンティティとして、新しい関連付けの関連エンティティが既に存在する場合、新しい関連付けのアクションを**すべてのレコードに伝播**、**アクティブ レコードのみに伝播**、または**同一所有者のレコードのみに伝播**に設定することはできません。 これにより、複数の親関連付けを持つ関連付けの作成を防ぎます。  

### <a name="see-also"></a>関連項目

[エンティティ間の関連付けの作成および編集](create-edit-entity-relationships.md)<br />
[1:N (一対多) または N:1 (多対一) の関連付けを作成および編集する](create-edit-1n-relationships.md)<br />
[PowerApps ポータルを使用して 1:N (1 対多) または N:1 (多対 1) のエンティティ関連付けを作成および編集する](create-edit-1n-relationships-portal.md)<br />
[N:N (多対多) の関連付けを作成する](create-edit-nn-relationships.md)

