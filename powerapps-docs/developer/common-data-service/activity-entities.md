---
title: 活動エンティティ (Common Data Service) | Microsoft Docs
description: Dynamics 365 (online) では、活動とは、ユーザーまたはチームが顧客に連絡するときに実行する、レターを送ったり電話をかけたりすることなどのタスクです。
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: mayadumesh
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="activity-entities"></a>活動エンティティ

Common Data Service では、活動とは、ユーザーまたはチームが顧客に連絡するときに実行する、レターを送ったり電話をかけたりすることなどのタスクです。 ユーザーやチームは各自の活動を作成したり、活動を遂行する第三者に活動を割り当てたり、他のユーザーやチームと活動を共有することができます。 活動はカレンダーに入力可能なアクションであり、活動には、アクションがいつ実行されたか、またはいつ実行されるかを特定するための時間領域 (開始時間、停止時間、期限、期間) が存在します。 また、活動が表すアクションを判断するための基本プロパティ (情報カテゴリ、説明など) が存在します。 活動の状態は、オープン、取り消し、完了のいずれかです。 完了状態には、活動がどのように完了したかを明らかにする数種類のサブ状態値が関連付けられます。  
  
 活動には、1 人以上の関係者 (Common Data Service では活動関係者と呼ばれます) が関与します。 会議活動の場合は、会議に出席している取引先担当者やユーザーが関係者となります。 電話活動や FAX 活動の場合は、通話の発信者とその受信者が関係者となります。 次の図は、活動エンティティの関連付けを示しています。  
  
 ![活動の図](media/entity-model-activity.gif "活動の図")  
  
 インスタント メッセージング (IM) や SMS など、今日のビジネスで必要な通信手段をサポートするために、Common Data Service でユーザー定義の活動を作成できます。  
  
 **その他の活動エンティティ**  
  
-   スケジュール活動により、サービスやリソースのスケジュールを設定し、その結果、作業のスケジュールを定義できます。 スケジュール活動のエンティティは、`Appointment`、`ServiceAppointment`、および `RecurringAppointmentMaster` です。 詳細については、「[スケジュールと予定のエンティティ](/dynamics365/customer-engagement/developer/schedule-appointment-entities)」を参照してください。  
  
-   マーケティング活動 `CampaignResponse` を使用すると、マーケティング キャンペーンに対する顧客からの反応を取得できます。一方、`CampaignActivity` エンティティは、キャンペーンの 1 つのステップを表します。 詳細については、「[キャンペーン エンティティ](/dynamics365/customer-engagement/developer/campaign-entities)」を参照してください。  
  
-   営業支援システム エンティティである `OpportunityClose`、`OrderClose`、および `QuoteClose` の活動はこれらのイベントそれぞれの情報を取り込みます。 詳細については、「[営業エンティティ (潜在顧客、営業案件、競合企業、見積もり、受注、請求書)](/dynamics365/customer-engagement/developer/sales-entities-lead-opportunity-competitor-quote-order-invoice)」を参照してください。  
  
-   顧客サービス エンティティである `IncidentResolution` 活動は、サポート案件の解決に関する情報を取り込みます。 詳細については、「[インシデント (サポート案件) エンティティ](/dynamics365/customer-engagement/developer/incident-case-entities)」を参照してください。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [Dynamics 365 のユーザー定義活動](custom-activities.md)  
  
 [活動ポインター (活動) エンティティ](activitypointer-activity-entity.md)  
  
 [活動関係者エンティティ](activityparty-entity.md)  
  
 [タスク活動、FAX 活動、電話活動、およびレター活動のエンティティ](task-fax-phone-call-letter-activity-entities.md)  
  
 [電子メール活動エンティティ](email-activity-entities.md)  
  
 [活動エンティティのサンプル コード](/dynamics365/customer-engagement/developer/sample-code-activity-entities)  
  
## <a name="related-sections"></a>関連セクション  
   
 [サーバー側の同期エンティティ](server-side-synchronization-entities.md)  
  
 [エンティティ メタデータのカスタマイズ](customize-entity-metadata.md)
