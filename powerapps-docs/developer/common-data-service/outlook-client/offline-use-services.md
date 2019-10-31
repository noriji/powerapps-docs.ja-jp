---
title: サービスをオフラインで使用する (Common Data Service) | Microsoft Docs
description: さまざまなサービスをオフラインで使用する方法について説明します。 オフラインでサポートされているいくつかのメッセージがあります。 IOrganizationService のメッセージがオフラインで機能するかどうかは、そのメッセージの SdkMessage.Availability 属性をチェックすることでも確認できます。
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: sriharibs
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---

# <a name="offline-use-of-services"></a>サービスをオフラインで使用する

オフライン アクセス対応の Dynamics 365 for Outlook を使用すると、サーバーから切断しても作業を継続できます。  
  
 また、イベントおよびプラグイン インフラストラクチャにより、同じ API およびプログラミング モデルを使ってソリューション全体の開発投資を活用することができます。 <xref:Microsoft.Xrm.Sdk.IOrganizationService> メソッドと Common Data Service OData サービス メソッドは、オンラインとオフラインの両方で機能します。 `Create` または `Update` などのメソッドをオフラインで使用すると、データがローカルで書き込まれ、その後ユーザーがサーバーに接続したときにこれらの操作がサーバーに再生されます。  
  
 メッセージがオフラインでサポートされるかどうかの詳細については、「<xref:Microsoft.Crm.Sdk.Messages>」を参照してください。 <xref:Microsoft.Xrm.Sdk.IOrganizationService> メッセージがオフラインで機能するかどうかは、そのメッセージの `SdkMessage.Availability` 属性をチェックして確認することもできます。 複数種類のエンティティで使用されるメッセージの場合、操作対象のエンティティでそのメッセージをオフラインで使用できるかどうかを確認するためには、`SdkMessageFilter.Availability` 属性もチェックする必要があります。 たとえば、`Create` メッセージはオフラインで使用できますが、キュー、ユーザー、またはサービス拠点のエンティティには使用できません。  
  
 オフライン アクセス対応の Dynamics 365 for Microsoft Office Outlook では、デバッグを目的としてトレースできます。 イベント ビューアーおよびプラットフォームのトレースの詳細に関する詳細については、「[Dynamics 365 の監視とトラブルシューティング](https://technet.microsoft.com/library/hh699694.aspx)」を参照してください。  
  
### <a name="see-also"></a>関連項目  
 
 <xref:Microsoft.Xrm.Sdk.IOrganizationService>   
 [組織のサービスのメソッド](/dynamics365/customer-engagement/developer/org-service/organization-service-methods)   
 <xref:Microsoft.Xrm.Sdk.IOrganizationService.Create*>   
 <xref:Microsoft.Xrm.Sdk.IOrganizationService.Update*>