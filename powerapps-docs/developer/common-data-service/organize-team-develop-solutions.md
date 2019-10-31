---
title: ソリューション開発のためのチーム編成 (Common Data Service) | Microsoft Docs
description: このドキュメントでは、複数の開発者が同じソリューションで作業する場合に使用するいくつかの戦略をリストします。
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: shmcarth
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="organize-your-team-to-develop-solutions"></a>ソリューション開発のためのチーム編成

複数の開発者が同一のソリューションで作業する場合、各開発者が他の開発者の作業に干渉せずにカスタマイズできる環境が必要になることがあります。 また、開発環境からテスト環境やユーザー受け入れテスト (UAT) 環境へのソリューションの移行も必要になることがあります。  
  
<a name="BKMK_StrategiesForTeamDev"></a>   
## <a name="strategies-for-team-development"></a>チーム開発の戦略  
 次にチームによるソリューション開発を管理する方法の一部を示します。  
  
-   [単一の組織で 1 つのマスター ソリューションを開発](organize-team-develop-solutions.md#BKMK_SingleOrgMasterSolution)  
  
-   [単一の組織で複数の開発者ソリューションとマスター ソリューションを開発](organize-team-develop-solutions.md#BKMK_SingleOrgMultipleDeveloper)  
  
-   [各開発者がそれぞれ単一の組織を担当](organize-team-develop-solutions.md#BKMK_OneOrgPerDev)  
  
<a name="BKMK_SingleOrgMasterSolution"></a>   
### <a name="single-organization-one-master-solution"></a>単一の組織で 1 つのマスター ソリューションを開発  
 単一の組織で複数の開発者が作業することはできますが、別のコンポーネントで作業するように注意する必要があります。 これは、前提条件となるマネージド ソリューション (共有ライブラリ) が最初にインストールされている場合には簡単な方法です。  
  
<a name="BKMK_SingleOrgMultipleDeveloper"></a>   
### <a name="single-organization-multiple-developer-solutions--master-solution"></a>単一の組織で複数の開発者ソリューションとマスター ソリューションを開発  
 単一の組織内で、各開発者が個別のアンマネージド ソリューションを作成することができます。 各ソリューションには、マスター ソリューションのサブセットが含まれます。 各ソリューション コンポーネントは、単一のアンマネージド ソリューション内にのみ存在します。 開発者は、割り当てられたアンマネージド ソリューションに既存のソリューション コンポーネントを追加することはできません。 これにより、変更されるコンポーネントを明確に分離することができます。 各開発者のソリューションには、マスター ソリューションに含まれるコンポーネントへの参照が含まれているため、変更を統合する必要はありません。  
  
<a name="BKMK_OneOrgPerDev"></a>   
### <a name="one-organization-per-developer"></a>各開発者がそれぞれ単一の組織を担当  

 各開発者が自分の組織で作業できます。 Common Data Service への変更を確認するには、各開発者はソリューションをアンマネージド ソリューションとしてエクスポートする必要があります。 その後、各開発者の組織のソリューションはマスター ソリューションにインポートされます。 マスター ソリューションを使用してマネージド ソリューションをエクスポートします。  
  
<a name="BKMK_DeployingSolutionsFromDevThroughToProduction"></a>   
## <a name="deploy-solutions-from-development-through-test-and-production-environments"></a>開発環境からテスト環境および運用環境までのソリューションの展開  
 開発組織では、ソリューションはさまざまなテスト環境やステージング環境に展開されて分析され、最終的に運用環境に展開されます。 ホワイトペーパー [Microsoft Dynamics CRM 2011 および CRM Online ソリューションの開発からテスト、運用環境への展開](http://go.microsoft.com/fwlink/p/?LinkId=232288)では、Dynamics 365 の実際のソリューションを、テスト環境および運用環境全体にわたって展開する方法について、自動化を利用した、信頼性が高く繰り返し可能なやり方の中で紹介しています。 また、Common Data Service でソリューションを展開およびテストする際の制約についても説明しています。  
  
### <a name="see-also"></a>関連項目  
 [ソリューション開発の計画](/dynamics365/customer-engagement/developer/plan-solution-development)   
 [ソリューションのモジュール化](organize-solutions.md)   
 