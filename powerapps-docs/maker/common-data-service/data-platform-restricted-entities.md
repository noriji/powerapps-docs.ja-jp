---
title: Dynamics 365 のライセンスを必要とする制限付きエンティティ | Microsoft Docs
description: Dynamics 365 ライセンスが必要な Common Data Service の制限付きエンティティの一覧です。
author: lancedMicrosoft
manager: kfile
ms.service: powerapps
ms.component: cds
ms.topic: reference
ms.date: 05/01/2018
ms.author: lanced
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="restricted-entities-requiring-dynamics-365-licenses"></a>Dynamics 365 のライセンスを必要とする制限付きエンティティ

> [!IMPORTANT]
> このトピックは最新ではなく、2019 年 10 月 1 日から適用される最新のライセンス変更を反映するため、間もなく更新されます。 エンティティに対するライセンス要件の最新情報については、 [PowerApps ライセンス ガイド](https://go.microsoft.com/fwlink/?linkid=2085130) を参照してください。

アプリ作成者は Common Data Service で使用可能なほとんどのエンティティを使用し、 PowerApps Plan 1 ライセンス のみを持つユーザー向けにアプリおよびフローを作成することができます。 ただし、一部のエンティティには、アプリ ユーザーが PowerApps Plan 2 または Microsoft Flow Plan 2 ライセンスを持つことを必要とする複雑なビジネス ロジックが含まれます (詳細については、 [エンティティ ライセンスの要件](data-platform-entity-licenses.md) を参照してください)。 Dynamics 365 製品に関連付けられているさらに小さいエンティティ セットについて、エンティティ内でレコードの作成、更新、または削除を行う必要がある場合、キャンバスおよびモデル駆動型アプリのユーザーは対応する Dynamics 365 製品のライセンスを持っていることが必要です。 これらを*制限付き*エンティティと呼びます。

エンティティは、以下の理由により、Dynamics 365 ライセンスに制限される場合があります。

* エンティティは、通常、アプリケーション外で使用されない製品固有の構成データの保存と管理に使用されます。
* エンティティには、Dynamics 365 製品内で使用される特定の方法のデータの作成および管理を行う高度なロジックが付いています。

アプリまたはフローがエンティティから情報を読み取るだけの場合、Dynamics 365 ライセンスは必要ではなく、該当する PowerApps または Microsoft Flow ライセンスを持っていれば十分です。 

## <a name="restricted-entities-for-create-update-and-delete-operations"></a>作成、更新、および削除操作のための制限付きエンティティ
エンティティ内に保存されているデータの作成、更新、または削除を行う PowerApps および Microsoft Flow アプリ ユーザーに対する制限付きエンティティおよび関連付けられている Dynamics 365 ライセンスの要件を次の表に示します。 

|エンティティ  |論理名  |必要なライセンス  |
|---------|---------|---------|
実績 |msdyn_actual |Dynamics 365 for Field Service <br> **または** Dynamics 365 for Project Service Automation<br>**または** Dynamics 365 Customer Engagement 計画 <br> **または** Dynamics 365 プラン
契約ビジネス プロセス |msdyn_bpf_baa0a411a239410cb8bded8b5fdd88e3 |Dynamics 365 for Field Service<br>**または** Dynamics 365 Customer Engagement 計画 <br> **または** Dynamics 365 プラン
予約仕訳帳 | msdyn_bookingjournal|Dynamics 365 for Field Service<br>**または** Dynamics 365 Customer Engagement 計画 <br> **または** Dynamics 365 プラン
予約設定メタデータ | msdyn_bookingsetupmetadata|Dynamics 365 for Field Service <br> **または** Dynamics 365 for Project Service Automation<br>**または** Dynamics 365 Customer Engagement 計画 <br> **または** Dynamics 365 プラン
予約タイムスタンプ | msdyn_bookingtimestamp|Dynamics 365 for Field Service<br>**または** Dynamics 365 Customer Engagement 計画 <br> **または** Dynamics 365 プラン
サポート案件 | incident | Dynamics 365 for Customer Service Enterprise Edition <br>**または** Dynamics 365 Customer Engagement 計画 <br> **または** Dynamics 365 プラン
サポート案件から作業指示書ビジネス プロセス |msdyn_bpf_989e9b1857e24af18787d5143b67523b |Dynamics 365 for Field Service<br>**または** Dynamics 365 Customer Engagement 計画 <br> **または** Dynamics 365 プラン
構成 |msdyn_configuration |Dynamics 365 for Field Service <br> **または** Dynamics 365 for Project Service Automation<br>**または** Dynamics 365 Customer Engagement 計画 <br> **または** Dynamics 365 プラン
権利 | 権利 | Dynamics 365 for Customer Service Enterprise Edition <br>**または** Dynamics 365 Customer Engagement 計画 <br> **または** Dynamics 365 プラン
見積行|msdyn_estimateline|Dynamics 365 for Project Service Automation<br>**または** Dynamics 365 Customer Engagement 計画 <br> **または** Dynamics 365 プラン
見積もり|msdyn_estimate |Dynamics 365 for Project Service Automation<br>**または** Dynamics 365 Customer Engagement 計画 <br> **または** Dynamics 365 プラン
ファクト|msdyn_fact |Dynamics 365 for Project Service Automation<br>**または** Dynamics 365 Customer Engagement 計画 <br> **または** Dynamics 365 プラン
Field Service の設定 |msdyn_fieldservicesetting |Dynamics 365 for Field Service<br>**または** Dynamics 365 Customer Engagement 計画 <br> **または** Dynamics 365 プラン
Field Service システム ジョブ |msdyn_fieldservicesystemjob |Dynamics 365 for Field Service<br>**または** Dynamics 365 Customer Engagement 計画 <br> **または** Dynamics 365 プラン
目標 | goal | Dynamics 365 for Sales Professional、 <br>**または** Dynamics 365 for Sales, Enterprise Edition、 <br>**または** Dynamics 365 Customer Engagement 計画 <br> **または** Dynamics 365 プラン
在庫仕訳帳 |msdyn_inventoryjournal |Dynamics 365 for Field Service<br>**または** Dynamics 365 Customer Engagement 計画 <br> **または** Dynamics 365 プラン
請求書プロセス |msdyn_bpf_d8f9dc7f099f44db9d641dd81fbd470d |Dynamics 365 for Project Service Automation<br>**または** Dynamics 365 Customer Engagement 計画 <br> **または** Dynamics 365 プラン
行動 | 行動 | Dynamics 365 for Marketing <br> **または** Dynamics 365 Customer Engagement 計画 <br> **または** Dynamics 365 プラン
サポート情報の記事 | ナレッジ記事 | Dynamics 365 for Customer Service Enterprise Edition <br>**または** Dynamics 365 Customer Engagement 計画 <br> **または** Dynamics 365 プラン
組織単位 |msdyn_organizationalunit |Dynamics 365 for Field Service <br> **または** Dynamics 365 for Project Service Automation<br>**または** Dynamics 365 Customer Engagement 計画 <br> **または** Dynamics 365 プラン
製品在庫 |msdyn_productinventory |Dynamics 365 for Field Service<br>**または** Dynamics 365 Customer Engagement 計画 <br> **または** Dynamics 365 プラン
プロジェクト パラメーター|msdyn_projectparameter |Dynamics 365 for Project Service Automation<br>**または** Dynamics 365 Customer Engagement 計画 <br> **または** Dynamics 365 プラン
プロジェクト ステージ| msdyn_bpf_665e73aa18c247d886bfc50499c73b82|Dynamics 365 for Project Service Automation<br>**または** Dynamics 365 Customer Engagement 計画 <br> **または** Dynamics 365 プラン
プロジェクト タスクの依存関係|msdyn_projecttaskdependency |Dynamics 365 for Project Service Automation<br>**または** Dynamics 365 Customer Engagement 計画 <br> **または** Dynamics 365 プラン
プロジェクト タスク|msdyn_projecttask |Dynamics 365 for Project Service Automation<br>**または** Dynamics 365 Customer Engagement 計画 <br> **または** Dynamics 365 プラン
プロジェクト チーム メンバー|msdyn_projecteam |Dynamics 365 for Project Service Automation<br>**または** Dynamics 365 Customer Engagement 計画 <br> **または** Dynamics 365 プラン
発注書ビジネス プロセス | msdyn_bpf_2c5fe86acc8b414b8322ae571000c799|Dynamics 365 for Field Service<br>**または** Dynamics 365 Customer Engagement 計画 <br> **または** Dynamics 365 プラン
リソース割り当ての詳細 (廃止)|msdyn_resourceassignmentdetail |Dynamics 365 for Project Service Automation<br>**または** Dynamics 365 Customer Engagement 計画 <br> **または** Dynamics 365 プラン
リソース割り当て|msdyn_resourceassignment |Dynamics 365 for Project Service Automation<br>**または** Dynamics 365 Customer Engagement 計画 <br> **または** Dynamics 365 プラン
リソース制限 (廃止) |msdyn_workorderresourcerestriction | Dynamics 365 for Field Service<br>**または** Dynamics 365 Customer Engagement 計画 <br> **または** Dynamics 365 プラン
ルーティング規則セット | routingrule | Dynamics 365 for Customer Service Enterprise Edition <br>**または** Dynamics 365 Customer Engagement 計画 <br> **または** Dynamics 365 プラン
スケジュール ボードの設定 |msdyn_scheduleboardsetting |Dynamics 365 for Field Service <br> **または** Dynamics 365 for Project Service Automation<br>**または** Dynamics 365 Customer Engagement 計画 <br> **または** Dynamics 365 プラン
スケジュール パラメーター |msdyn_schedulingparameter |Dynamics 365 for Field Service <br> **または** Dynamics 365 for Project Service Automation<br>**または** Dynamics 365 Customer Engagement 計画 <br> **または** Dynamics 365 プラン
SLA| sla | Dynamics 365 for Customer Service Enterprise Edition <br>**または** Dynamics 365 Customer Engagement 計画 <br> **または** Dynamics 365 プラン
システム ユーザーのスケジューラ設定 |msdyn_systemuserschedulersetting|Dynamics 365 for Field Service <br> **または** Dynamics 365 for Project Service Automation<br>**または** Dynamics 365 Customer Engagement 計画 <br> **または** Dynamics 365 プラン
トランザクション接続|msdyn_transactionconnection |Dynamics 365 for Project Service Automation<br>**または** Dynamics 365 Customer Engagement 計画 <br> **または** Dynamics 365 プラン
トランザクション発生元|msdyn_transactionorigin |Dynamics 365 for Project Service Automation<br>**または** Dynamics 365 Customer Engagement 計画 <br> **または** Dynamics 365 プラン
トランザクションの種類|msdyn_transactiontype |Dynamics 365 for Project Service Automation<br>**または** Dynamics 365 Customer Engagement 計画 <br> **または** Dynamics 365 プラン
一意の番号|msdyn_uniquenumber |Dynamics 365 for Field Service<br>**または** Dynamics 365 Customer Engagement 計画 <br> **または** Dynamics 365 プラン
作業指示書ビジネス プロセス |msdyn_bpf_d3d97bac8c294105840e99e37a9d1c39 |Dynamics 365 for Field Service<br>**または** Dynamics 365 Customer Engagement 計画 <br> **または** Dynamics 365 プラン
作業指示書の詳細の生成キュー (廃止)|msdyn_workorderdetailsgenerationqueue |Dynamics 365 for Field Service<br>**または** Dynamics 365 Customer Engagement 計画 <br> **または** Dynamics 365 プラン

## <a name="licensing"></a>ライセンス
PowerApps と Dynamics 365 ライセンスの詳細については、 [ライセンスの概要](../../administrator/pricing-billing-skus.md) ページを参照してください。

