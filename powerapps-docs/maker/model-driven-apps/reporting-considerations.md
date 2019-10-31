---
title: レポートに関する考慮事項 | MicrosoftDocs
ms.custom: null
ms.date: 09/27/2019
ms.reviewer: null
ms.service: crm-online
ms.suite: null
ms.tgt_pltfrm: null
ms.topic: article
applies_to:
  - Dynamics 365 for Customer Engagement (online)
  - powerapps
ms.assetid: cb1bb002-8300-43bb-ab75-99e7a9c9c35d
caps.latest.revision: 11
author: Mattp123
ms.author: matp
manager: kvivek
tags:
  - MigrationHO
search.audienceType:
  - customizer
search.app:
  - D365CE
---
# <a name="reporting-considerations"></a>レポートに関する考慮事項

モデル駆動型アプリには、決定を導き、顧客とより効果的に対話するために役立つビジネス データを見分けるための、多くの機能が用意されています。  機能には、ビュー、グラフ、ダッシュボード、および SQL Server Reporting Services レポートが含まれます。 また、Microsoft Excel 統合も含まれており、これにより Power BI 機能 [PowerView](https://support.office.com/article/power-view-overview-and-learning-5380e429-3ee0-4be2-97b7-64d7930020b6)、[PowerPivot](https://support.office.com/article/power-pivot-overview-and-learning-f9001958-7901-4caa-ad80-028a6d2432ed)、および [PowerQuery](https://support.office.com/article/power-query-overview-and-learning-ed614c81-4b00-4291-bd3a-55d80767f81d) を使用して、簡単にセルフ サービスのレポートを作成することができます。 アプリ データベース内に保持するデータ量は増え続けるため、大きなデータセットをレポートして視覚化するために、BI 戦略を考慮し、最も効果的なメカニズムを判断することは今まで以上に重要になります。  
  
 環境では、レポートのインフラストラクチャは共有され、データベースと区別されます。 この構造では、顧客はレポートの実行に必要なリソースを共有することができますが、各レポートは顧客の個々のデータベース インスタンスに対して実行されます。  さらに、 ビジネス目標のために実行するときはいつでも、必要な数のレポートを実行できます。  レポートには時間制限が設定されていません。  
  
 Common Data Service に内蔵されているレポート機能は、より短い期間のデータセットでレポートを実行できるように設計されています。 これを考慮して、次の固定設定に留意してください。  
  
- レポートやクエリは最大で 5 分間実行できます。 最大期間に到達すると、レポートはタイムアウトし、ユーザーにメッセージが表示されます。 5 分間以内で、レポートやクエリは 50,000 レコードを超える大きなデータセットに及ぶことができます。これにより、レポート操作上の大半の要求を満たすための、顕著な柔軟性が提供されます。  
  
- クエリ応答を改善するため、詳細レポートにおいて大量のレコードの表示を最小限に抑えることをお勧めします。 それには、適切なフィルターを適用して、返されるレコードの数を削減します。 集計または要約レポートを作成するとき、クエリは fetch 詳細レコードに対してではなく、クエリに対して集計を追加して、レポート内で集計を実行する必要があります。  これは、Fetch XML の集計を使用して実行できます。 <!-- More information: [Use FetchXML aggregation](../developer/use-fetchxml-aggregation.md)  -->
  
- ダッシュボードに表示されるグラフおよびグリッドでは、ユーザー アプリで 50,000 行未満のデータセットを持つクエリを実行することができます。 ユーザーが 50,000 行以上のデータセットに及ぶダッシュボード クエリを実行する場合、「レコード数の上限を超えています。 レコード数を減らしてください。」というメッセージが返されます。  データセットを適切に設定すると、アプリの最適なパフォーマンスが保証されます。  
 
  
<a name="BKMK_ReportTips"></a>   
## <a name="tips-and-solutions-for-reporting"></a>レポートに関するヒントとソリューション  
 通常、大半の組織のレポートでは、次の設定で十分です。 ユーザーがこれらの設定を超えないようにし、レポート クエリのパフォーマンス全般を向上させるため、次のベスト プラクティスを検討してください。  
  
- カスタム レポートまたはダッシュボードを作成するとき、レポート内に時間ベースのフィルターを追加して、現在の月または四半期などに結果を制限することにより、より短い期間に及ぶ小さなデータセットをクエリするように設計します。  
  
- 結果を返すために必要なエンティティの数を制限することをお勧めします。 これは、クエリを実行し、その一連の結果を返すために必要な時間の削減に役立ちます。  
  
- 詳細レポートに表示されるレコードの数を減らすことをお勧めします。 タイムアウトを削減するため、クエリが返すレコードの数を削減する適切なフィルターを使用できます。  
  
- 集計レポートまたは要約レポートの場合、クエリは Fetch 詳細レコードに対してではなく、データベースに対して集計を追加するために使用し、SQL Server Reporting Services レポート内で集計を実行する必要があります。  
  
- 業務に適切な時は、既定 (標準) のレポートおよびダッシュボードを実行します。 これらのレポートとダッシュボードは、ユーザーのデータベースごとにクエリするように設計されているため、ほとんどの場合はデータセットの制限を超えません。  
  
  ユーザーがこれらの設定を超えるレポートを実行する必要がある場合、複雑なレポートに必要なサポートのための、以下のオプションを確認することをお勧めします。 両方のオプションは、データ統合ソリューションを使用することにより、レポートの作業負荷を Common Data Service から別のデータストアに効果的に解放します。  
  
- [アダプター](reporting-considerations.md#BKMK_ThirdPartyAdapt) は SQL Server Integration Services (SSIS) と連動して、アプリ データとの統合能力を拡張するために使用されます。  
  
- 抽出変換ロード [(ETL) ツール ](reporting-considerations.md#BKMK_ETL) では、複数のデータ ソースを結合、または SSIS が使用されない場合にデータ倉庫ソリューションに対してデータを抽出することによりデータの解析を作成する一連の新しいツールが用意されています。 ETL ツールは、Common Data Service に接続してデータを移動する包括的なソリューションを提供します。  
  
> [!IMPORTANT]
>  これらのツールを使用するときは、非業務時間にデータの移動または同期を実行することをお勧めします。  
  
 必要に応じて、大きなレポートの実行に特定して使用されるデータのオフライン コピーを作成する場合など、特定のレポートに必要なソリューションを提供する多数の Microsoft Dynamics パートナーを用意しています。  これらのパートナーは、使用できるデータ統合ツールの知識が豊富です。 詳細: [Dynamics 365 パートナーを探す](https://dynamics.microsoft.com/partners/find-a-partner/)  
  
<a name="BKMK_ThirdPartyAdapt"></a>   
## <a name="third-party-adapters-for-ssis"></a>SSIS のサードパーティ アダプター  
  
-   [CozyRoc SSIS+ Dynamics 365/CRM のコンポーネント](http://www.cozyroc.com/ssis/dynamics-crm)  
  
-   [Dynamics 365 の KingswaySoft SSIS 統合ツールキット](https://www.kingswaysoft.com/products/ssis-integration-toolkit-for-microsoft-dynamics-365)  
  
-   [Dynamics 365 の CData SSIS のコンポーネント](https://www.cdata.com/ssis/components/)  
  
-   [Dynamics 365 の Team4 SSIS コネクタ](https://www.team4.de/microsoft-dynamics-365-crm/)  
  
<!--    [PragmaticWorks TaskFactory SSIS Source/Destination for Dynamics CRM](http://pragmaticworks.com/Products/Task-Factory/Features/DynamicsCRMSource.aspx)  -->
  
<a name="BKMK_ETL"></a>   
## <a name="etl-tools"></a>ETL ツール  
  
-   [TIBCO Dynamics 365 統合](https://www.tibco.com/solutions/microsoft-dynamics-365-integration)  <br />
  
<!--   [Productivity tools from Informatica](https://community.informatica.com/community/search.jspa?peopleEnabled=true&userID=&containerType=14&container=2002&spotlight=true&resultTypes=solution&q=dynamics+CRM)  -->
  
### <a name="see-also"></a>関連項目  
 [オーサリング拡張子のレポート (SQL Server Data Tools サポートを使って)](http://www.microsoft.com/download/details.aspx?id=45013) <br />
  
 [Microsoft Power Query for Excel の概要](http://office.microsoft.com/en-ca/excel-help/introduction-to-microsoft-power-query-for-excel-HA104003940.aspx?CTT=5&origin=HA104003813)   <br />
 [Dynamics 365 for Customer Engagement OData Feeds と Power Query: [レコード]とは](https://community.dynamics.com/crm/b/survivingcrm/archive/2014/02/16/dynamics-crm-odata-feeds-and-power-query-what-s-the-record.aspx)   <br />
 

