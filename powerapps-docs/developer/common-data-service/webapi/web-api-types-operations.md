---
title: Web API の種類および操作 (Common Data Service)| Microsoft Docs
description: このトピックでは、Web API と連携して使用できるものについて説明し、重要なトピックの紹介、またサービスおよびメタデータ ドキュメントから生成されたドキュメントとシステム エンティティの種類、関数、およびアクションのドキュメントから必要な情報を見つける方法の紹介を行います。
ms.custom: ''
ms.date: 04/30/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: d80cfb87-d4f1-4c75-bcc8-4f54d1351e26
caps.latest.revision: 27
author: brandonsimons
ms.author: susikka
manager: shujoshi
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="web-api-types-and-operations"></a>Web API の種類および操作

Web API を使用するには、使用できるものに関する情報を検索する必要があります。 サービスについては、ユーザーがアクセスできるサービスおよびメタデータ ドキュメントで説明されています。 このトピックでは重要な概念を紹介し、サービスおよびメタデータ ドキュメントから生成されたドキュメント、メタデータ ドキュメント、およびシステム エンティティの種類、関数、アクションのドキュメントから必要な情報を検索する方法を説明します。 

<a name="bkmk_terminology"></a>
  
## <a name="terminology"></a>用語 

Web API は、精通する必要のある特定の用語を使用する OData v4 標準を使用して実装されます。 *エンティティ データ モデル (EDM)* は OData サービスで公開されるデータを表すのに使用される抽象データ モデルです。 以下の表は、[OData バージョン 4.0 パート 1: Protocol Plus Errata 02](http://docs.oasis-open.org/odata/odata/v4.0/errata02/os/complete/part1-protocol/odata-v4.0-errata02-os-part1-protocol-complete.html) で定義された、理解する必要のある用語の抜粋リストです。  
  
|用語|定義|  
|----------|----------------|  
|*エンティティの種類*|キーを持つ名前付き構造化の種類です。 名前付きプロパティと、エンティティ間の関連付けを定義します。 エンティティの種類は、他のエンティティの種類の単一の継承から派生する場合があります。|  
|*エンティティ*|エンティティの種類のインスタンス (取引先企業、営業案件など)。|  
|*エンティティ セット*|エンティティの名前付きコレクション (たとえば、取引先企業は、取引先企業のエンティティを含むエンティティ セット)。 エンティティ キーはエンティティ セット内のエンティティを一意に識別します|  
|*複合型*|プロパティ セットで構成される、キーを持たない名前付き構造化の種類です。 複合型は、一般的にモデル エンティティのプロパティの値や、パラメーター、操作の戻り値として使用されます。|  
|*列挙の種類*または *Enum の種類*|整数を基盤とする名前付き定数の値を持つ名前付きプリミティブの種類です。|  
|*関数*|追加のフィルター操作、関数またはアクションなど、さらなるコンポジションをサポートする場合のある、副作用のない操作です|  
|*操作*|データ変更などの副作用を許容し、非決定論的な動作を回避するよう構成できない操作です|  
  
<a name="bkmk_servicedocs"></a>
  
## <a name="service-documents"></a>サービス ドキュメント

Web API の詳細については、2 つのサービス ドキュメントを参照してください。  
  
<a name="bkmk_serviceDocument"></a>

### <a name="service-document"></a>サービス ドキュメント

ブラウザのアドレス フィールドに入力されている次のクエリは、組織で利用できるすべてのエンティティ セットの完全なリストである *サービス ドキュメント* を返します。 *[組織 URI]* は、組織の URL を表すことに留意してください。  
  
```  
  
[Organization URI]/api/data/v9.0  
  
```  
  
 エンティティ セットは JSON 配列の形式で返されます。 配列の各項目には、表に示すように、3 つのプロパティがあります。  
  
|プロパティ|説明|  
|--------------|-----------------|  
|`name`|エンティティ セットの名前です。 このデータはエンティティの <xref href="Microsoft.Dynamics.CRM.EntityMetadata?text=EntityMetadata EntityType" /> `EntitySetName` プロパティからのデータです。|  
|`kind`|Web API にはエンティティ セットのみ表示されています。|  
|`url`|この値は name プロパティと同じで、エンティティのデータを取得するためのリソース パスの一部を表します。|  
  
 この情報は、`GET` 要求を使用して取得することができ、使用できるエンティティ セットの一覧をサービスを使用して入手すると役に立つことがあります。  
  
<a name="bkmk_csdl"></a>

### <a name="csdl-metadata-document"></a>CSDL $metadata ドキュメント
 
次の URL に対する `GET` 要求は、比較的大きな (3.5 MB 以上) Common Schema Definition Language (CSDL) ドキュメント、またはサービスによって公開されるデータおよび操作を示す*メタデータ ドキュメント*を返します。  
  
```http  
GET [Organization URI]/api/data/v9.0/$metadata  
```  
  
このドキュメントは、サービスに厳密に型指定したオブジェクトを提供するクラスを生成するためのデータ ソースとして使用できます。 生成されたクラスを使用しない場合、代わりにこの情報から生成されたドキュメントを確認する必要がある場合があります。 [Web API リファレンス](/dynamics365/customer-engagement/web-api/about)は、一般的な追加ソリューションをインストールしてあるシステムから取得された、主にこの文書からの情報を使用します。  
  
このドキュメントに関する詳細については、[OData バージョン 4.0 パート 3: Common Schema Definition Language (CSDL) Plus Errata 02](http://docs.oasis-open.org/odata/odata/v4.0/odata-v4.0-part3-csdl.html) を参照してください。  
  
> [!TIP]
>  このトピックを読み進める前に、組織で使用する `$metadata` をダウンロードし、説明されている種類、関数、アクションが `$metadata` やサポート ドキュメントにどのように含まれているかを確認してください。  
>   
>  URL に移動することにより、ブラウザを使用してそのドキュメントを表示またはダウンロードできます。  

<a name="bkmk_metannot"></a>

### <a name="metadata-annotations"></a>メタデータの注釈

メタデータ ドキュメントには、メタデータ要素およびサービスの機能に関する追加情報を提供するいくつかの種類の `Annotation` 要素が含まれます。  v9.x 以降、これらの注釈は、明示的に要求されない限り、デフォルトのメタデータ ドキュメントには含まれません。 これらの注釈は、メタデータ ドキュメントのサイズを増加させてしまい、必ずしも必要ではありません。  
  
 注釈を含めるには、メタデータ ドキュメントを要求するときに 2 つのオプションがあります。  
  
-   URL に `?annotations=true` クエリ文字列パラメーターを追加します。  
  
-   要求に `Prefer: odata.include-annotations="*"` ヘッダーを追加します。  
  
各 `Annotation` 要素には、注釈の種類を示す `Term` 属性が含まれます。 OData V4 で使用できるすべての注釈の定義は、[OData Vocabularies バージョン 4.0](http://docs.oasis-open.org/odata/odata-vocabularies/v4.0/csprd01/odata-vocabularies-v4.0-csprd01.html) で参照できます。 以下の表で、Web API で使用されるいくつかの例を示します。  
  
|用語|説明|  
|----------|-----------------|  
|`Org.OData.Core.V1.Description`|entitytype またはプロパティの説明。|  
|`Org.OData.Core.V1.Permissions`|アクセス許可が制限されている場合にプロパティに使用可能なアクセス許可のリスト。  通常、これはプロパティが読み取り専用であることを示すために、単一の `<EnumMember>Org.OData.Core.V1.PermissionType/Read</EnumMember>` 子要素を持つプロパティに表示されます。|  
|`Org.OData.Core.V1.Computed`|プロパティが計算されるかどうか。 これらも通常は読み取り専用です。|  
|`OData.Community.Keys.V1.AlternateKeys`|エンティティに対して定義された代替キーを記述する要素のコレクションが含まれています。 詳細: [代替キー](#bkmk_alternateKeys)|  
|`Org.OData.Capabilities.V1.IndexableByKey`|entityset が OData URL 規則に従ってキー値をサポートするかどうか。|  
|`Org.OData.Capabilities.V1.SkipSupported`|entityset が `$skip` をサポートするかどうか。|  
|`Org.OData.Capabilities.V1.SearchRestrictions`|`$search` 式に対するどんな種類の制限が entityset に適用されているか。|  
|`Org.OData.Capabilities.V1.CountRestrictions`|`/$count` パス接尾辞および $count=true システム クエリ オプションに対するどんな種類の制限があるか。|  
|`Org.OData.Capabilities.V1.NavigationRestrictions`|OData URL 規則に従ってプロパティを移動するのにどのような制限があるか。|  
|`Org.OData.Capabilities.V1.ChangeTracking`|このサービスまたはエンティティ セットの変更履歴機能。|  
|`Org.OData.Capabilities.V1.ConformanceLevel`|このサービスによって達成された適合レベル。|  
|`Org.OData.Capabilities.V1.FilterFunctions`|`$filter` でサポートされている関数と演算子のリスト。|  
|`Org.OData.Core.V1.DereferenceableIDs`|エンティティ ID が特定されたエンティティを見つける URL かどうか。|  
|`Org.OData.Core.V1.ConventionalIDs`|エンティティ ID が OData URL 規則に従うかどうか。|  
|`Org.OData.Capabilities.V1.AsynchronousRequestsSupported`|サービスが非同期要求設定をサポートするかどうか。|  
|`Org.OData.Capabilities.V1.BatchContinueOnErrorSupported`|サービスがエラー時続行設定をサポートするかどうか。  この設定は、`$batch` 要求をサポートします。|  
|`Org.OData.Capabilities.V1.CrossJoinSupported`|このコンテナー内のエンティティ セットに対するクロス ジョインがサポートされているかどうか。|  
|`Org.OData.Capabilities.V1.SupportedFormats`|フォーマット パラメーターを含む、サポートされるフォーマットのメディア タイプ。|  
  
<a name="bkmk_entityTypes"></a>

## <a name="entity-types"></a>エンティティの種類

<xref:Microsoft.Dynamics.CRM.EntityTypeIndex> は、ビジネス データを格納している Web API を通して公開されるシステム エンティティの種類の一覧です。 エンティティの種類は、キーを持つ名前付き構造化の種類です。 名前付きプロパティと、エンティティ間の関連付けを定義します。 エンティティの種類は、他のエンティティの種類の単一の継承から派生する場合があります。 <xref:Microsoft.Dynamics.CRM.MetadataEntityTypeIndex> は、システム メタデータの管理に使用されるエンティティの種類の一覧です。 どちらもエンティティの種類ですが、その使用方法は異なります。 モデル エンティティの使用についての詳細は、「[Web API を Common Data Service メタデータで使用する](use-web-api-metadata.md)」を参照してください。 各エンティティの種類には、`$metadata` 内の `EntityType` 要素が含まれています。 次は、プロパティおよびナビゲーション プロパティが削除された `$metadata` からの <xref href="Microsoft.Dynamics.CRM.account?text=account EntityType" /> の定義です。  
  
```xml  
<EntityType Name="account" BaseType="mscrm.crmbaseentity">  
  <Key>  
    <PropertyRef Name="accountid" />  
  </Key>  
  <!--Properties and navigation properties removed for brevity-->  
  <Annotation Term="Org.OData.Core.V1.Description" String="Business that represents a customer or potential customer. The company that is billed in business transactions." />  
</EntityType>  
```  
  
SDK ドキュメントの各 `EntityType` 参照ページでは、使用できる場合、次の情報の表示に `$metadata` からの情報を使用します。  
  
|情報|説明|  
|-----------------|-----------------|  
|**説明**|エンティティの説明です。<br /><br /> <xref href="Microsoft.Dynamics.CRM.EntityMetadata?text=EntityMetadata EntityType" /> `Description` プロパティ情報は、`Term` 属性値が Org.OData.Core.V1.Description である `Annotation` 要素を使用している `EntityType` 要素に含まれています。|  
|**コレクション URL**|各種類のコレクションにアクセスするための URL です。<br /><br /> <xref href="Microsoft.Dynamics.CRM.EntityMetadata?text=EntityMetadata EntityType" /> `EntitySetName` プロパティ情報は、`$metadata` `EntityContainer` 要素を使用して含まれます。 各 `EntitySet` 要素の `Name` 属性は、URL からデータがどのようにアクセスされるかを管理します。|  
|**ベースの種類**|これがエンティティの種類が継承するエンティティの種類です。<br /><br /> `EntityType` 要素の `BaseType` 属性は、エンティティの種類の名前を含みます。 この名前には、Microsoft.Dynamics.CRM 名前空間のエイリアスである mscrm が接頭辞として付加されます。 詳細: [種類の継承](web-api-types-operations.md#bkmk_typeInheritance)|  
|**表示名**|この情報は `$metadata` に含まれておらず、<xref href="Microsoft.Dynamics.CRM.EntityMetadata?text=EntityMetadata EntityType" /> `DisplayName` プロパティから取得されます。|  
|**主キー**|エンティティのインスタンスを参照する一意の識別子を含む、属性の値です。<br /><br /> <xref href="Microsoft.Dynamics.CRM.EntityMetadata?text=EntityMetadata EntityType" /> `PrimaryIdAttribute` プロパティの値は、`EntityType` `Key` 要素に含まれます。 各エンティティには、主キーを 1 つだけ設定できます。<br /><br /> 代替キーは表示されていません。 詳細: [代替キー](web-api-types-operations.md#bkmk_alternateKeys)|  
|**主属性**|多くのエンティティは主属性の値の設定を必要とするので、便宜上含まれています。<br /><br /> この情報は `$metadata` に含まれておらず、メタデータ <xref href="Microsoft.Dynamics.CRM.EntityMetadata?text=EntityMetadata EntityType" /> `PrimaryNameAttribute` プロパティから取得されます。|  
|**プロパティ**|「[プロパティ](web-api-types-operations.md#bkmk_properties)」を参照してください。|  
|**単一値ナビゲーション プロパティ**|「[単一値ナビゲーション プロパティ](web-api-types-operations.md#bkmk_singleValuedNavigationProperties)」を参照してください。|  
|**コレクション値ナビゲーション プロパティ**|「[コレクション値ナビゲーション プロパティ](web-api-types-operations.md#bkmk_collectionvaluedNavProperties)」を参照してください。|  
|**エンティティの種類にバインドされた操作**|操作が特定のエンティティの種類にバインドされている場合、便宜上表示されます。|  
|**エンティティの種類を使用する操作**|この一覧では、エンティティの種類を使用する場合がある操作を示します。 これは、パラメーター内の現在の種類を参照するすべての操作対する参照を収集することで、または戻り値として取得されます。|  
|**エンティティの種類から継承するエンティティの種類**|この一覧では、エンティティの種類から直接継承する任意のエンティティの種類を示します。 詳細については、「[種類の継承](web-api-types-operations.md#bkmk_typeInheritance)」を参照してください。|  
  
<a name="bkmk_changeentitysetname"></a>
 
### <a name="change-the-name-of-an-entity-set"></a>エンティティ セット名の変更
 
既定では、エンティティ セット名は <xref href="Microsoft.Dynamics.CRM.EntityMetadata?text=EntityMetadata EntityType" /> `LogicalCollectionName` (<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata> `LogicalCollectionName`) プロパティの値と一致します。 異なるエンティティ セット名を使用して対応したいユーザー定義エンティティがある場合、異なる名前を使用するように <xref href="Microsoft.Dynamics.CRM.EntityMetadata?text=EntityMetadata EntityType" /> `EntitySetName` (<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata> `EntitySetName`) プロパティの値を更新できます。  
  
<a name="bkmk_alternateKeys"></a>

### <a name="alternate-keys"></a>代替キー

Common Data Service では代替キーを作成できますが、 既定のエンティティには主キーのみ表示されます。  
  
 システム エンティティには代替キーは定義されていません。 エンティティに代替キーを定義すると、`$metadata` `EntityType` 要素に次のような `Annotation` として含まれます。  
  
```  
<Annotation Term="OData.Community.Keys.V1.AlternateKeys">  
  <Collection>  
    <Record Type="OData.Community.Keys.V1.AlternateKey">  
      <PropertyValue Property="Key">  
        <Collection>  
          <Record Type="OData.Community.Keys.V1.PropertyRef">  
            <PropertyValue Property="Alias" String="key name" />  
            <PropertyValue Property="Name" PropertyPath="key name" />  
          </Record>  
        </Collection>  
      </PropertyValue>  
    </Record>  
  </Collection>  
</Annotation>  
```  
  
代替キーに関する情報は Web API を使用する <xref href="Microsoft.Dynamics.CRM.EntityMetadata?text=EntityMetadata EntityType" /> `Keys` コレクション値ナビゲーション プロパティを使用するメタデータ、または組織のサービスを使用する <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata> `Keys` プロパティから取得できます。  
  
<a name="bkmk_typeInheritance"></a>
 
### <a name="type-inheritance"></a>種類の継承

継承は、一般的なプロパティの共有と、エンティティの種類をグループに分類することを可能にします。 Web API 内のすべてのエンティティの種類は、次の 2 つのエンティティの種類から継承します。 すべてのビジネス エンティティの種類は <xref href="Microsoft.Dynamics.CRM.crmbaseentity?text=crmbaseentity EntityType" /> から継承し、すべてのモデル エンティティは <xref href="Microsoft.Dynamics.CRM.crmmodelbaseentity?text=crmmodelbaseentity EntityType" /> から継承します。  
  
|ベース エンティティ|説明|  
|-----------------|-----------------|  
|<xref href="Microsoft.Dynamics.CRM.crmbaseentity?text=crmbaseentity EntityType" />|すべてのビジネス エンティティはのこのエンティティから継承します。 プロパティはありません。 抽象ベース エンティティとしての役割のみを果たします。|  
|<xref href="Microsoft.Dynamics.CRM.activitypointer?text=activitypointer EntityType" />|すべての活動エンティティはのこのエンティティから継承します。 活動エンティティに、一般的なプロパティのセットおよびナビゲーション プロパティを定義します。|  
|<xref href="Microsoft.Dynamics.CRM.principal?text=principal EntityType" />|<xref href="Microsoft.Dynamics.CRM.systemuser?text=systemuser EntityType" /> および <xref href="Microsoft.Dynamics.CRM.team?text=team EntityType" /> は、このエンティティから一般的な ownerid プロパティを継承します。|  
|<xref href="Microsoft.Dynamics.CRM.crmmodelbaseentity?text=crmmodelbaseentity EntityType" />|<xref href="Microsoft.Dynamics.CRM.MetadataBase?text=MetadataBase EntityType" /> のみ、このエンティティから直接継承します。 プロパティはありません。 抽象ベース エンティティとしての役割のみを果たします。|  
|<xref href="Microsoft.Dynamics.CRM.MetadataBase?text=MetadataBase EntityType" />)|すべてのメタデータ エンティティは、このエンティティから継承します。 これは、すべてのメタデータ エンティティに `MetadataId` および `HasChanged` プロパティを提供します。|  
|<xref href="Microsoft.Dynamics.CRM.AttributeMetadata?text=AttributeMetadata EntityType" />|異なる種類の属性を表すすべてのモデル エンティティは、このエンティティから継承します。|  
|<xref href="Microsoft.Dynamics.CRM.EnumAttributeMetadata?text=EnumAttributeMetadata EntityType" />|一連のオプションを含む属性を表すモデル エンティティは、このエンティティから継承します。|  
|<xref href="Microsoft.Dynamics.CRM.OptionSetMetadataBase?text=OptionSetMetadataBase EntityType" />|このモデル エンティティの種類は、それから継承する <xref href="Microsoft.Dynamics.CRM.BooleanOptionSetMetadata?text=BooleanOptionSetMetadata EntityType" /> および <xref href="Microsoft.Dynamics.CRM.OptionSetMetadata?text=OptionSetMetadata EntityType" /> モデル エンティティの種類が使用する一般的なプロパティのセットを提供します。|  
|<xref href="Microsoft.Dynamics.CRM.RelationshipMetadataBase?text=RelationshipMetadataBase EntityType" />|このモデル エンティティの種類は、それから継承する <xref href="Microsoft.Dynamics.CRM.ManyToManyRelationshipMetadata?text=ManyToManyRelationshipMetadata EntityType" /> および <xref href="Microsoft.Dynamics.CRM.OneToManyRelationshipMetadata?text=OneToManyRelationshipMetadata EntityType" /> モデル エンティティの種類が使用する一般的なプロパティのセットを提供します。|  
  
<a name="bkmk_properties"></a>
 
## <a name="properties"></a>プロパティ

各エンティティの種類には、属性に対応する宣言済プロパティがある場合があります。 <xref:Microsoft.Dynamics.CRM.EntityTypeIndex> および <xref:Microsoft.Dynamics.CRM.MetadataEntityTypeIndex> の内容では、ベース エンティティの種類から継承されたプロパティは、各エンティティの種類の宣言済プロパティの一覧にまとまられています。 継承は、各プロパティの説明で実行されます。  
  
`$metadata` `EntityType` 要素では、各プロパティが、コードで設定するプロパティに対応する `Name` 属性を持つ `Property` 要素に含まれます。 `Type` 属性の値は、プロパティのデータの種類を指定します。 ビジネス エンティティの種類のプロパティは、一般的に OData プリミティブの種類を使用します。  
  
`$metadata` で定義される <xref href="Microsoft.Dynamics.CRM.account?text=account EntityType" /> `name` プロパティの例を次に示します。  
  
```  
<Property Name="name" Type="Edm.String" Unicode="false">  
  <Annotation Term="Org.OData.Core.V1.Description" String="Type the company or business name." />  
</Property>  
```  
  
プロパティの説明は、Org.OData.Core.V1.Description という `Term` 属性のプロパティを持つ `Annotation` 要素で使用できます。 この説明は、<xref href="Microsoft.Dynamics.CRM.AttributeMetadata?text=AttributeMetadata EntityType" /> `Description` 属性の値から取得されます。 説明を持たないプロパティもあります。  
  
各プロパティは計算される場合があります。 これにより、システムによって値が設定される場合があります。 これは、Org.OData.Core.V1.Computed という `Term` 属性の値を持つ `Annotation` 要素内で指定されています。  
  
各プロパティには、更新できるかどうかの制限がある場合もあります。 これは、Org.OData.Core.V1.Permissions という `Term` 属性の値を持つ `Annotation` 要素内で定義されています。 これの唯一のオプション セットは Org.OData.Core.V1.PermissionType/Read であり、プロパティが読み取り専用であることを示します。  
  
<a name="bkmk_primitives"></a>

### <a name="primitive-types"></a>プリミティブの種類
 
OData はさまざまなデータの種類をサポートしますが、Common Data Service はそのすべては使用しません。 次の表は、Common Data Service 組織のサービスの種類がどのように OData プリミティブの種類にマップされているかを示します。  
  
|組織のサービスの種類|Web API の種類|内容|  
|-------------------------------|------------------|-----------------|  
|BigInt|Edm.Int64|署名済 64 ビット整数|  
|Boolean|Edm.Boolean|バイナリ値ロジック|  
|CalendarRules|単一値ナビゲーション プロパティ|<xref href="Microsoft.Dynamics.CRM.calendarrule?text=calendarrule EntityType" /> の特定の単一値ナビゲーション プロパティです。|  
|顧客|単一値ナビゲーション プロパティ|この種類のプロパティを持つエンティティの顧客は、それぞれの単一値ナビゲーション プロパティを使用する account または contact エンティティの種類に設定された単一値ナビゲーション プロパティである場合があります。 それぞれの単一値コレクション プロパティのどちらかが設定されると、他方が消去されます。|  
|日時|Edm.DateTimeOffset|うるう秒のない、タイム ゾーンのオフセットを持つ日付と時刻 <br />OData に DateTime の種類はありません。|  
|小数|Edm.Decimal|固定された小数以下の精度およびスケールを持つ数値|  
|Double|Edm.Double|IEEE 754 binary64 浮動小数点数 (小数点以下 15～17 桁)|  
|EntityName|Edm.String|UTF-8 文字のシーケンス|  
|画像|Edm.Binary|バイナリ データ|  
|Integer|Edm.Int32|署名済 32 ビット整数|  
|検索|単一値ナビゲーション プロパティ|特定のエンティティに対する参照|  
|ManagedProperty|適用なし|内部のみで使用。|  
|メモ|Edm.String|UTF-8 文字のシーケンス|  
|金額|Edm.Decimal|固定された小数以下の精度およびスケールを持つ数値|  
|所有者|単一値ナビゲーション プロパティ|<xref href="Microsoft.Dynamics.CRM.principal?text=principal EntityType" /> への参照です。 systemuser および team エンティティの種類はどちらも、ownerid プロパティを prinicipal エンティティの種類から継承します。|  
|Picklist|Edm.Int32|署名済 32 ビット整数|  
|都道府県|Edm.Int32|署名済 32 ビット整数|  
|状態|Edm.Int32|署名済 32 ビット整数|  
|String|Edm.String|UTF-8 文字のシーケンス|  
|Uniqueidentifier|Edm.Guid|16 バイト (128 ビット) の一意の識別子|  

<!-- TODO:
|PartyList|Collection-valued navigation property to the `activityparty` entity type.|The activitypartyparticipationtypemask property contains a value to represent the role of the participant. See [Activity Party Types](../activityparty-entity.md#ActivityPartyTypes) for more information.|   -->

<a name="bkmk_lookupProperties"></a>
 
### <a name="lookup-properties"></a>検索プロパティ

ほとんどの単一値ナビゲーション プロパティには、命名規則として `_<name>_value` を使用する計算された読み取り専用のプロパティがあり、`<name>` は単一値ナビゲーション プロパティの名前と一致します。 このパターンの例外として、エンティティ内の検索属性に複数の種類のエンティティ参照を指定できる場合があります。 一般的な例えとして、`incident` 要素の `customerid` 属性が `contact` または `account` である参照として設定されている場合です。 <xref href="Microsoft.Dynamics.CRM.incident?text=incident EntityType" /> [単一値ナビゲーション プロパティ](/dynamics365/customer-engagement/web-api/incident?view=dynamics-ce-odata-9#Single-valued_navigation_properties)では、`customerid_account` および `customerid_contact` は、営業案件に関連付けられた顧客を反映する個別の単一値ナビゲーション プロパティです。 両方 `customerid` にバインドされているため、これら単一値ナビゲーション プロパティの 1 つを設定すると、他方が null に設定されます。 <xref href="Microsoft.Dynamics.CRM.incident?text=incident EntityType" /> [プロパティ](/dynamics365/customer-engagement/web-api/incident?view=dynamics-ce-odata-9#Properties)では、どちらかの単一値ナビゲーション プロパティに設定されている値と同じ値が含まれる `_customerid_value` 検索プロパティがあります。  
  
通常、検索プロパティの使用はできるだけ避け、対応する単一値ナビゲーション プロパティを使用します。 これらのプロパティは、一部の統合シナリオに役立つ場合があるために含まれています。 これらのプロパティは、適用された変更を対応する単一値ナビゲーション プロパティを使用して反映するのみのため、読み取り専用および計算されたプロパティです。  
  
クエリに検索プロパティを含めると、単一値ナビゲーション プロパティで表されない基盤とする属性に設定されているデータの追加情報を提供する注釈を含めるよう要求できます。 詳細については、[検索プロパティに関するデータの取得](query-data-web-api.md#bkmk_lookupProperty)を参照してください。  
  
<a name="bkmk_navprops"></a>

## <a name="navigation-properties"></a>ナビゲーション プロパティ

OData では、ナビゲーション プロパティを使用すると、現在のエンティティと関連付けられたデータにアクセスすることができます。 エンティティの取得時に、関連データを含めるためにナビゲーション プロパティを拡張することができます。 ナビゲーション プロパティには、単一値とコレクション値の 2 種類があります。  
  
<a name="bkmk_singleValuedNavigationProperties"></a>
 
### <a name="single-valued-navigation-properties"></a>単一値ナビゲーション プロパティ

これらプロパティは、多対一関係をサポートし、別のエンティティに対する参照が設定できるような検索属性に対応します。 `$metadata` `EntityType` 要素では、これらは `Type` で属性が単一の種類に設定されている `NavigationProperty` 要素として定義されます。 `$metadata` の <xref href="Microsoft.Dynamics.CRM.account?text=account EntityType" /> `createdby` 単一値のナビゲーション プロパティの例を次に示します。  
  
```xml  
<NavigationProperty Name="createdby" Type="mscrm.systemuser" Nullable="false" Partner="lk_accountbase_createdby">  
 <ReferentialConstraint Property="_createdby_value" ReferencedProperty="systemuserid" />  
</NavigationProperty>  
```  
  
単一値のナビゲーション プロパティを表すすべてのナビゲーション プロパティは、`Partner` 属性の値によって示された、対応するコレクション値ナビゲーション プロパティを持ちます。 個々の単一値のナビゲーション プロパティは、関連する要素の GUID 値の取得に使用できる、計算された読み取り専用の検索プロパティを表す `Property` 属性の値を持つ `ReferentialConstraint` 要素を持ちます。 詳細は、[検索プロパティ](web-api-types-operations.md#bkmk_lookupProperties)を参照してください。  
  
<a name="bkmk_collectionvaluedNavProperties"></a>

### <a name="collection-valued-navigation-properties"></a>コレクション値ナビゲーション プロパティ

これらのプロパティは一対多または多対多の関連付けに対応します。 `$metadata` `EntityType` 要素では、これらは `Type` で属性が種類のコレクションに設定されている `NavigationProperty` 要素として定義されます。 次に示すものは、一対多の関連付けを表す <xref href="Microsoft.Dynamics.CRM.account?text=account EntityType" /> `Account_Tasks` コレクション値ナビゲーション プロパティを示します。  
  
```xml  
<NavigationProperty Name="Account_Tasks" Type="Collection(mscrm.task)" Partner="regardingobjectid_account_task" />  
```  
  
コレクション値ナビゲーション プロパティが多対多の関連付けを表す場合は、ナビゲーション プロパティの名前とパートナーの名前は同じです。 次に示すものは、多対多の関連付けを表す <xref href="Microsoft.Dynamics.CRM.account?text=account EntityType" /> `accountleads_association` コレクション値ナビゲーション プロパティを示します。  
  
```xml  
<NavigationProperty Name="accountleads_association" Type="Collection(mscrm.lead)" Partner="accountleads_association" />  
```  
  
Web API の使用時は、一対多と多対多の関連付けの違いは重要ではありません。 エンティティの関連付け方法は、関連付けの種類に関係なく同じです。 多対多の関連付けは裏で交差エンティティを使用しますが、<xref:Microsoft.Dynamics.CRM.EntityTypeIndex> にはいくつかの特別なシステムの交差エンティティしか含まれていません。 たとえば、<xref href="Microsoft.Dynamics.CRM.campaignactivityitem?text=campaignactivityitem EntityType" /> は正確には交差エンティティですが、通常の交差エンティティよりも多くのプロパティを持つため含まれています。  
  
通常の交差エンティティは、多対多の関連付けを維持するために必要な 4 つの基本プロパティのみを持ちます。 エンティティ間にユーザー定義の多対多関連付けを作成すると、関連付けをサポートするために通常の交差エンティティが作成されます。 多対多の関連付け関係する操作を実行するのにナビゲーション プロパティを使用する必要があるため、通常の交差エンティティはドキュメントに記載されていませんが、Web API で使用できます。 これら交差エンティティの種類は、*\<交差エンティティの論理名>* + ’コレクション’ という命名規則を使用するエンティティ セット名を使用してアクセスできます。 たとえば、`[Organization URI]/api/data/v9.0/contactleadscollection` を使用して contactleads 交差エンティティの種類から情報を取得できます。 これら通常の交差エンティティは、変更の追跡を適用したい場合にのみ使用します。  
  
<a name="bkmk_actions"></a>

## <a name="actions"></a>操作

*アクション*は、データ変更などの副作用を許容し、非決定論的な動作を回避するよう構成できない操作です。  
  
 この <xref:Microsoft.Dynamics.CRM.ActionIndex> トピックでは、使用できる各システム アクションが一覧表示されます。 詳細: [Web API アクションの使用](use-web-api-actions.md) を参照してください。  
  
<a name="bkmk_functions"></a>
 
## <a name="functions"></a>関数

*関数* は、追加のフィルター操作、関数、アクションなど、さらなるコンポジションをサポートする場合のある、副作用のない操作です。  
  
 Web API では関数が 2 種類定義されています。  
  
-   この <xref:Microsoft.Dynamics.CRM.FunctionIndex> トピックでは、使用できる各システム関数が一覧表示されます。  
  
-   <xref:Microsoft.Dynamics.CRM.QueryFunctionIndex> トピックでは、クエリの条件として使用することを目的とした関数が一覧表示されます。  
  
 詳細は、[Web API 機能を使用](use-web-api-functions.md)を参照してください。  
  
<a name="bkmk_complexTypes"></a>
 
## <a name="complex-types"></a>複合型

*複合型*は、プロパティ セットで構成される、キーを持たない名前付き構造化の種類です。 複合型は、一般的にモデル エンティティのプロパティの値や、パラメーター、操作の戻り値として使用されます。  
  
<xref:Microsoft.Dynamics.CRM.ComplexTypeIndex> は、すべてのシステム複合型を一覧表示します。 *複合型*は、プロパティ セットで構成される、キーを持たない名前付き構造化の種類です。 これらは、一般的にモデル エンティティのプロパティの値や、パラメーター、操作の戻り値として使用されます。 次は、$metadata からの <xref href="Microsoft.Dynamics.CRM.WhoAmIResponse?text=WhoAmIResponse ComplexType" /> です。  
  
```xml  
<ComplexType Name="WhoAmIResponse">  
  <Property Name="BusinessUnitId" Type="Edm.Guid" Nullable="false" />  
  <Property Name="UserId" Type="Edm.Guid" Nullable="false" />  
  <Property Name="OrganizationId" Type="Edm.Guid" Nullable="false" />  
</ComplexType>  
```  
  
<a name="bkmk_EnumTypes"></a>
 
## <a name="enumeration-types"></a>列挙の種類
 
*列挙の種類* または *EnumTypes* は、整数を基盤とする名前付き定数の値を持つ名前付きプリミティブの種類です。  
  
<xref:Microsoft.Dynamics.CRM.EnumTypeIndex> は、すべてのシステム列挙の種類を一覧表示します。 *列挙の種類* は、整数を基盤とする名前付き定数の値を持つ名前付きプリミティブの種類です。 次は、$metadata からの <xref href="Microsoft.Dynamics.CRM.AccessRights?text=AccessRights EnumType" /> です。  
  
```  
<EnumType Name="AccessRights">  
  <Member Name="None" Value="0" />  
  <Member Name="ReadAccess" Value="1" />  
  <Member Name="WriteAccess" Value="2" />  
  <Member Name="AppendAccess" Value="4" />  
  <Member Name="AppendToAccess" Value="16" />  
  <Member Name="CreateAccess" Value="32" />  
  <Member Name="DeleteAccess" Value="65536" />  
  <Member Name="ShareAccess" Value="262144" />  
  <Member Name="AssignAccess" Value="524288" />  
</EnumType>  
```  
  
### <a name="see-also"></a>関連項目  

[Common Data Service Web API の使用](overview.md)<br />
[Web API を使用して Common Data Service を認証する](authenticate-web-api.md)<br />
[Web API を使用して演算を実行する](perform-operations-web-api.md)<br/>

