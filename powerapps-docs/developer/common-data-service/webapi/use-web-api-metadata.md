---
title: Web API とメタデータの使用 (Common Data Service) | Microsoft Docs
description: このセクションでは、Web API を Web API メタデータ EntityType リファレンス に含まれているエンティティの種類と一緒に使用する方法に関するガイダンスを提供しています。
ms.custom: ''
ms.date: 04/22/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
author: brandonsimons
ms.author: susikka
manager: shujoshi
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="use-the-web-api-with-metadata"></a>Web API をメタデータで使用する

組織サービスを使用して実行できるすべてのメタデータ操作を、Web API を使用して実行できます。 このセクションでは、Web API を <xref:Microsoft.Dynamics.CRM.MetadataEntityTypeIndex> に含まれているエンティティの種類と一緒に使用する方法に関するガイダンスを提供しています。  


 次の表に示すように、メタデータ エンティティを使用して操作を実行するための、4 つの公開エンティティ セット パスがあります。  
  
|エンティティ セット パス|説明|  
|---------------------|-----------------|  
|*[組織 URI]*/api/data/v9.0/EntityDefinitions|<xref href="Microsoft.Dynamics.CRM.EntityMetadata?text=EntityMetadata EntityType" /> エンティティを含む|  
|*[組織 URI]*/api/data/v9.0/RelationshipDefinitions|<xref href="Microsoft.Dynamics.CRM.ManyToManyRelationshipMetadata?text=ManyToManyRelationshipMetadata EntityType" /> および <xref href="Microsoft.Dynamics.CRM.OneToManyRelationshipMetadata?text=OneToManyRelationshipMetadata EntityType" /> は、両方とも <xref href="Microsoft.Dynamics.CRM.RelationshipMetadataBase?text=RelationshipMetadataBase EntityType" /> から継承されているため、含まれる。|  
|*[組織 URI]*/api/data/v9.0/GlobalOptionSetDefinitions|グローバルに定義されている <xref href="Microsoft.Dynamics.CRM.BooleanOptionSetMetadata?text=BooleanOptionSetMetadata EntityType" /> および <xref href="Microsoft.Dynamics.CRM.OptionSetMetadata?text=OptionSetMetadata EntityType" /> エンティティは、両方とも <xref href="Microsoft.Dynamics.CRM.OptionSetMetadata?text=OptionSetMetadata EntityType" /> から継承されているため含まれる。|  
|*[組織 URI]*/api/data/v9.0/ManagedPropertyDefinitions|内部のみで使用します。|  
  
各メタデータ エンティティの種類は、<xref href="Microsoft.Dynamics.CRM.MetadataBase?text=MetadataBase EntityType" /> から継承した `MetadataId` を一意の識別子プロパティとして使用します。 すべてのメタデータ エンティティには `MetadataId` がありますが、それらすべてを直接クエリすることはできません。 たとえば、属性を含む `EntityMetadata` エンティティのコンテキストでのみ、属性に対してクエリや操作を実行できます。  
  
これらのエンティティは、ビジネスおよびアプリケーション データを格納しているエンティティとは本質的に異なります。例えば:  
  
- メタデータ エンティティのプロパティは、 <xref href="Microsoft.Dynamics.CRM.crmbaseentity?text=crmbaseentity EntityType" /> から継承されたエンティティのプロパティに対して使用されるプリミティブ データの種類ではなく、<xref:Microsoft.Dynamics.CRM.ComplexTypeIndex> および <xref:Microsoft.Dynamics.CRM.EnumTypeIndex> で定義された多くの複雑な enum 型を使用します。  
  
- メタデータ エンティティは異なる命名規則に従い、組織サービスのアセンブリで使用される Pascal 形式の命名スタイルを維持します。  
  
- メタデータ エンティティは、継承した内容をより幅広く使用するため、必要なデータを取得するためにキャストの実行が必要な場合があります。  
  
## <a name="in-this-section"></a>このセクションの内容 

[Web API を使用したクエリ メタデータ](query-metadata-web-api.md)<br />
RESTful クエリ スタイルを使用してメタデータを照会するために Web API を使用できます。  

[名前または MetadataId でのメタデータの取得](retrieve-metadata-name-metadataid.md)<br />
メタデータのクエリを実行して構成の変更をお使いのアプリケーションに適用することができます。 メタデータ アイテムの主要プロパティの 1 つが判明している場合は、Web API を使用してメタデータの定義を取得できます。  

[Web API を使用してエンティティ定義を作成および更新](create-update-entity-definitions-using-web-api.md)<br />
Web API を使用してエンティティや属性を作成および更新して、組織サービス <xref:Microsoft.Xrm.Sdk.Messages.CreateEntityRequest>、 <xref:Microsoft.Xrm.Sdk.Messages.UpdateEntityRequest>、 <xref:Microsoft.Xrm.Sdk.Messages.CreateAttributeRequest> および <xref:Microsoft.Xrm.Sdk.Messages.UpdateAttributeRequest> の場合と同様の結果を達成することができます。  

[Web API を使用してエンティティ関係を作成および更新する](create-update-entity-relationships-using-web-api.md)<br />
エンティティが他のエンティティとの関連付けに使用できるかどうかを確認し、Web API を使用して、そのような関連付けを作成したり更新することができます。  

### <a name="see-also"></a>関連項目

[環境のメタデータの参照](../browse-your-metadata.md)<br />
[Common Data Service Web API の使用](overview.md)
