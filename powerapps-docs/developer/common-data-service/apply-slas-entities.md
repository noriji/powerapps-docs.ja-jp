---
title: エンティティに SLA を適用する (Common Data Service) | Microsoft Docs
description: SLA を適用するエンティティを有効にすることによって、カスタム エンティティにSLAを適用する方法について。 また、SLA KPI を作成することもできます。
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="apply-slas-to-entities"></a>エンティティへの SLA の適用

Common Data Service のサービス レベル契約 (SLA) は、サービス レベルの達成を示す指標または主要業績評価指標 (KPI) の定義の対象となる品目を含めることによって、顧客に対して提供することに組織が同意するサービスまたはサポートのレベルを定義することを支援します。 カスタム エンティティと以下のシステム エンティティに SLA を適用できます。  
  
-   定期的な予定 (RecurringAppointmentMaster) を除くすべての活動エンティティ (電子メール、タスク、予定など)  
  
-   Account  
  
-   取引先担当者   
  
-   請求書   
  
-   インシデント (サポート案件)  
  
-   営業案件  
  
-   見積もり  
  
-   潜在顧客  
  
-   受注 (SalesOrder) (受注)   
  
<a name="EnableSLAs"></a> 
  
## <a name="enable-entities-for-applying-slas"></a>適用する SLA に対してエンティティを有効化  

 エンティティに SLA を適用するには、エンティティに対して、<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.IsSLAEnabled> 属性を true に設定する必要があります。 この設定は、有効にした後は変更できません。 `Incident` エンティティは既定で SLA に対して有効になっています。  
  
 また、カスタマイズ ツールを使用して、エンティティを SLA に対して有効にすることもできます。 詳細: [サービス レベル契約のエンティティを有効化](/dynamics365/customer-engagement/customer-service/enable-entities-service-level-agreements)  
  
 エンティティを SLA に対して有効にすると、`SLAId` および `SLAInvokedId` などの新しい SLA 関連の属性がそのエンティティに自動的に追加されます。  
  
<a name="CreateSLAKPI"></a>   

## <a name="create-sla-kpis"></a>SLA KPI の作成  

 エンティティの SLA KPI をプログラムで作成するには、SLA 対応エンティティに対する検索属性を作成してから、`SLAKPIInstance` エンティティに対してその属性の関連付けを設定します。  
  
<a name="ApplySLA"></a>
   
## <a name="apply-slas-to-entity-records"></a>エンティティ レコードに SLA を適用する  

 Common Data Service Web クライアントを使用して、SLA 対応エンティティの SLA を作成し、新しいエンティティ レコードに自動的に適用されるように、そのエンティティに対する既定として SLA を設定できます。  
  
 ただし、ユーザー定義ビジネス要件に基づいてエンティティ レコードに SLA を手動で適用する場合は、プログラム的にエンティティ レコードを更新して、必要な有効な SLA レコードに `SLAId` 属性値を設定できます。  
  
<a name="Limitations"></a>   

## <a name="limitations-to-applying-slas-in-dynamics-365-online"></a>Dynamics 365 (online) での SLA の適用の制限  

 Common Data Service では、次の制限が、Common Data Service インスタンス (組織) 単位で、SLA に適用されます。  
  
-   アクティブな SLA を適用できる最大 7 つのエンティティを持つことができます。 この制限を超えた場合、SLA をアクティブ化するとエラーが発生します。  
  
-   アクティブな SLA のエンティティごとに、最大 5 つの SLA KPI を持つことができます。 この制限を超えた場合、SLA をアクティブ化するとエラーが発生します。 この制限は、`Incident` エンティティには適用されません。  
  
### <a name="see-also"></a>関連項目  
 [拡張サービス レベル アグリーメント (SLA)](/dynamics365/customer-engagement/admin/enhanced-service-level-agreements)