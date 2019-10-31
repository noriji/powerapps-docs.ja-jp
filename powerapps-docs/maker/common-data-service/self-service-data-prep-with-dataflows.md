---
title: PowerApps のデータフローでセルフサービス データを準備する | MicrosoftDocs
description: データ準備のための PowerApps でのデータフローの使用方法を説明します
ms.custom: ''
ms.date: 08/05/2019
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
ms.assetid: null
caps.latest.revision: null
ms.author: matp
manager: kvivek
tags: null
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---


<!--note from editor: I think "dataflows" should be lowercase based on this entry in the Microsoft style guide (scroll down to find dataflows): https://styleguides.azurewebsites.net/Styleguide/Read?id=2696&topicid=42299 -->



# <a name="self-service-data-prep-with-dataflows"></a>データフローでセルフサービス データを準備する
[!INCLUDE [cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

データ量が増え続けている中で、堅牢な構成を持った実用的な情報にデータをまとめる際の困難も、同様に増え続けています。 大量のデータをすぐに実行できるインサイトにすばやく変換するには、アプリ、AI での作業、または分析の準備が整ったデータが必要です。 PowerApps ポータルのセルフサービス データ準備を使用して、Common Data Service、または組織内の Azure Data Lake Storage Gen2 取引先企業にわずか数クリックでデータを移行して読み込むことができます。

データフローは、組織が異種ソースからのデータを統合して、それを消費に備え準備する際に役立つように導入されました。 親しみやすいセルフサービス ツールを使用してビッグ データを取り込み、移行し、統合し、エンリッチするためのデータフローを簡易作成できます。 データフローを作成するときは、データソース接続、ETL (抽出、移行、読み込み) ロジック、および宛先を定義して結果のデータに読み込むことができます。 作成後、データフローを実行する頻度を表示するには、データフロー更新スケジュールを構成します。 また、新しいモデル駆動型演算エンジンによって、データを準備するプロセスはデータフローの顧客がより管理しやすく、より決定しやすく、また扱いやすいものになっています。 データフローを使用すると、かつてデータ IT 組織で作成し監督する必要があったタスク（完了までに数時間または数日間を要する）を、アプリ作成者、ビジネス アナリストやレポート作成者などのデータ サイエンティストでない個人であっても数回クリックするだけで処理できるようになりました。


データフローは、データをエンティティに格納します。 エンティティはデータベース内にデータを格納する方法と同様に、データの格納に使用される一連のレコードです。 顧客は、ユーザー定義エンティティのスキーマを定義したり、Common Data Model の標準エンティティを活用したりできます。
Common Data Model で使用される、ビジネス、分析的アプリケーションのために共有して使用するデータ言語です。 Common Data Model メタデータ システムでは、たとえば PowerApps、Power BI、一部の Dynamics 365 アプリ (モデル駆動型アプリ)、Azure など、アプリケーションと業務プロセス全体にわたってデータと意味に一貫性を持たせます。そしてここで一般的なデータ モデルと一致させてデータを格納します。 そして、データフローの結果としてのエンティティは、次のいずれかで保存できます:

-   **Common Data Service。** PowerApps と Microsoft Flow を使用してビルドされた、ビジネス アプリケーションで使用されるデータを、安全に格納し、管理できます。

-   **Azure Data Lake Storage Gen2。** Power BI、Azure Data、AI サービス、またはレイクのデータを読み取るカスタム ビルドの基幹業務アプリケーションを使用して、組織内のユーザーと共同作業できます。 [Common Data Model フォルダー](https://go.microsoft.com/fwlink/?linkid=2045304) で Azure Data Lake Storage Gen2 取引先企業格納データにデータを読み込むデータフロー。 **Common Data Model フォルダー** には、データを交換を促進し、組織の Azure Data Lake Storage アカウントに共有記憶域層として格納したデータを生成または消費するサービス全体で完全な相互運用性を有効にする標準形式のスキーマ データおよびメタデータを含みます。

データフローを使用して、Excel、Azure SQL Database、SharePoint、Azure Data Explorer、Salesforce、Oracle Database などを含む、サポートされているオンプレミスおよびクラウド ベースの一意の巨大なデータ ソースからデータを取り込むことができます。

データ ソースを選択した後、Power Query のわずかなコードを記述するだけで、またはコードをまったく記述することなくエクスペリエンスを使用して、データを変換し、Common Data Model の標準エンティティにマッピングするか、ユーザー定義エンティティを作成できます。 上級ユーザーは、データフローの M 言語を直接編集してデータフローを完全にカスタマイズできます。これは、数百万人の Power BI Desktop および Excel ユーザーが既に知っている Power Query エクスペリエンスに似ています。

データフローを作成し保存したら、クラウドで実行する必要があります。
データフローをトリガーして手動で実行するか、Power Platform データフロー サービスを実行する頻度をスケジュールするかを選択できます。 データフローで実行が完了すると、データを使用できます。 データフローのデータを Common Data Serviceに読み込むには、Common Data Service のコネクタを PowerApps、Microsoft Flow、Excel、さらに Common Data Service コネクタをサポートする他のすべてのアプリケーションで使用できます。 組織の Azure Data Lake Storage Gen2 アカウントに格納されているデータフローから使用する場合、Power BI Desktop の Power Platform データフロー コネクタを使用するか、レイクのファイル ディレクトリに直接アクセスします。

## <a name="how-to-use-dataflows"></a>データフローの使用方法
データフロー技術のバックグラウンドで表示される、前のセクション。 このセクションでは、データフローが組織でどのように使用できるかを学べるようにツアーをご利用ください。

> [!NOTE]
> データフローを使用するには、有料の PowerApps プランを使用する必要がありますが、データフローを使用することによって別々に請求されることはありません。 

### <a name="load-data-to-common-data-service"></a>Common Data Service へのデータの読み込み
PowerApps アプリケーションで使用される [Common Data Service](https://docs.microsoft.com/en-us/powerapps/maker/common-data-service/data-platform-intro) のエンティティを設定しても使用できます。 数回のクリック操作で、オンラインのデータとオンプレミスのソース データのソースを統合できます。

<!--from editor: In the last sentence above, should it change to "...on-premises data sources." ? -->


### <a name="extend-the-common-data-model-for-your-business-needs"></a>ビジネス ニーズ向けの Common Data Model を拡張する
Common Data Model で拡張、ビルドを行う組織の場合、データフローを使用してビジネス インテリジェンス担当者が標準エンティティをカスタマイズしたり、または新しく作成したりできます。 この、データ モデルをカスタマイズするセルフサービスの方法を使用すると、組織に合わせてカスタマイズされている Power BI ダッシュボードをビルドするためのデータフローを使用できるようになります。

### <a name="extend-your-capabilities-with-azure-data-and-ai-services"></a>Azure Data and AI サービスで機能を拡張する
Power Platform データフローでは、データフローのデータを Azure Data Lake Storage Gen2 のアカウントに格納するように設定できます。 環境が組織の Data Lake に接続すると、データ科学者および開発者は、Azure Machine Learning、Azure Databricks、Azure Data Factoryなどの強力な Azure 製品を活用できます。

組織の Azure Data Lake に存在するデータフローを作成する方法など Azure Data Lake Storage Gen2 とデータフローとの統合の詳細については、 [データフローと Azure Data Lake の統合（プレビュー）](/power-bi/service-dataflows-azure-data-lake-integration)を参照してください。

## <a name="summary-of-self-service-data-prep-for-big-data-in-powerapps"></a>PowerApps のビッグ データのための、セルフサービス データの準備の概要
データフローを使用すればビジネス データからより優れた制御とより高速のインサイトを実行できるという複数のシナリオと例があります。 組織内の他のユーザーは、Common Data Service、Power BI の Power Platform データフロー コネクタ、あるいは組織の Azure Data Lake Storage Gen2 アカウントのデータフローの **Common Data Service** フォルダーへの直接アクセスのいずれかを介することによってデータフローを活用できます。 Common Data Model で定義された標準データモデル（スキーマ）を使用すると、ビジネス アプリケーションはエンティティのスキーマに依存し、データがどのように作成されたのか、またはどのデータソースからなのかを抽出できます。 データフローがスケジュールの実行を完了すると、データは、アプリ、フロー、BI インサイトのモデリングと作成の準備を非常に短期間で整えることができます ... かつては、作成に数か月、あるいはそれ以上かかっていました。

Common Data Model の標準た形式により、組織内のユーザーは、迅速かつ簡単に、自動のビジュアルとレポートを生成するアプリを作成できます。 次のものが挙げられますが、これらに限定されるわけではありません:

-   さまざまなソースのデータを Common Data Model 標準エンティティにマッピングして、データを統合し、既知のスキーマを活用してすぐに使用できるアプリケーションを駆動できるようにします。

-   独自のユーザー定義エンティティを作成して、組織全体でデータを統合します

-   データフロー データを活用する Power BI レポートとダッシュボードの作成。

-   組織の Azure Data Lake Storage Gen2 アカウントを経由して Azure Data and AI サービスとの統合を実現する

## <a name="next-steps"></a>次のステップ

この記事では、PowerApps のセルフサービス データ準備の概要と、ユーザーが使用できる方法について説明しています。 次のトピックでは、データフローの一般的な使用方法の詳細について説明します。

-   [PowerApps でのデータフローの作成と使用](https://go.microsoft.com/fwlink/?linkid=2100076)

-   [Common Data Service のエンティティにデータを追加する](https://go.microsoft.com/fwlink/?linkid=2100075)

-   [Azure Data Lake Storage Gen2 をデータフロー ストレージに接続する](https://go.microsoft.com/fwlink/?linkid=2099973)

-   [オンプレミスのデータ ソースとともにデータフローを使用する](https://go.microsoft.com/fwlink/?linkid=2100077)

Power Query とスケジュールされている更新については、これらの項目を参照してください:

-   [Power BI Desktop のクエリの概要](/power-bi/desktop-query-overview)

-   [スケジュールされている更新の構成](/power-bi/refresh-scheduled-refresh)

Common Data Model の詳細については、概要の記事を参照してください:

-   [Common Data Model - 概要](/powerapps/common-data-model/overview)

