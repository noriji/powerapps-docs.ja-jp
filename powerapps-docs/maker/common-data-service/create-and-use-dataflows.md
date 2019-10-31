---
title: PowerApps でのデータフローの作成と使用について | MicrosoftDocs
description: PowerApps でのデータフローの作成と使用について説明します
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
# <a name="create-and-use-dataflows-in-powerapps"></a>PowerApps でのデータフローの作成と使用について
[!INCLUDE [cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

PowerApps にて利用可能となった高度なデータ プレパレーションでは、データフローと呼ばれるデータの集合を作成することができます。ここでは、様々なソースのビジネスデータとの接続、データの保全、データの変換、変換したデータの Common Data Service あるいは Azure Data Lake Gen2 ストレージのアカウントへの読み込み、を行うことができます。

データフローは、 PowerApps サービス内の環境で作成、管理されるエンティティ (テーブルと類似しています) の集合です。 データフローが作成された環境から直接、データフローにエンティティを追加、編集することができ、データの更新スケジュールの管理もすることができます。

PowerApps ポータルでのデータフローの作成が完了したら、 Common Data Service コネクタまたは Power BI Desktop データフローコネクタを使用してデータを取得することが出来ます。このどちらを使用するかはデータフローの作成先によって変わります。

データフローの使用にあたっては3つの主要な手順があります:

1.  PowerApps にてデータフローを作成します。 出力されたデータを読み込む場所 (データの取得元) と、Power Query の手順を選択し、専用のMicrosoft ツールを使用してデータの変換を行います。

2.  スケジュールのデータフローが実行されます。 これはデータフローが読み込み、変換するデータを Power Platform データフローが更新する頻度です。

3.  指定したストレージに読み込んだデータを使用します。 アプリケーション、ワークフロー、 Power BI レポート 、ダッシュボードの作成することができます。また、Azure Data Factory、 Azure Databricks などの Azure データサービスやCommon Data Model フォルダ標準をサポートする他のサービスを使用して、組織のレイクにあるデータフローの Common Data Model フォルダに直接接続することができます。

以下のセクションでは、これらの各手順について説明しており、各手順を完了するにあたって使用するツールの理解を深めることができます。 

## <a name="create-a-dataflow"></a>データフローの作成
データフローはひとつの環境内に作成されます。 したがって、それらの表示や管理は同環境からのみ行うことができます。 また、ワークフローでデータのデータを抽出するユーザーは、レコードを作成した環境へのアクセスができる必要があります。

> [!NOTE]
> 既定の環境で Azure Data Lake Storage Gen2 にデータを読み込むデータフローの作成には、現在対応していません。

1.  PowerAppsにサインインし、自分がどの環境に割り当てられているかを確認し、コマンド バーの右側に環境スイッチャーがあることを確認してください。

    ![環境スイッチャー](media/environment-switcher.png)

2.  左側のナビゲーション ウィンドウで、 **データ**の横にある矢印を選択します。

    ![データの選択](media/data-select.png)

3.  **データ** リストから **データフロー** を選択し、 **新規データフロー** を選択します。

    ![データフローの作成](media/create-a-dataflow.png)

4.  **読み込み対象を選択する** ページで、エンティティを保存する格納先を選択します。 データフローはエンティティを Common Data Service 、あるいは自社組織の Azure Data Lake storage に保存することが出来ます。 データを読み込む先を指定したら、データのワークフローの **名前** を入力し、 **作成** を選択します。

    ![読み込み対象の選択](media/select-load-target.png)

     > [!IMPORTANT]
     > データフローの所有者になることができるのは、作成者１人のみです。 所有者のみがデータフローを編集することが出来ます。 データのワークフローによって作成されたのデータに対する承認とアクセス権については、データの読み込みを行った場所によって変わってきます。 Common Data Service に読み込まれたデータは、 Common Data Service コネクタを介して利用することができ、データにアクセスするユーザーは Common Data Service に許可される必要があります。
     > Azure Data Lake Gen2 ストレージアカウントに読み込まれたデータは Power Platform データフロー コネクタ経由でアクセスでき、そのデータにアクセスするには、そのデータが作成された環境内のメンバーシップが必要です。

5. **データ ソースの選択** ページで、エンティティが保存されているデータソースを選択し、 **作成する**を選択します。 表示されたデータ ソースを選択して、データ フロー エンティティを作成することができます。 

    ![データ ソースの選択](media/choose-data-source.png)

6. データソースを選択したら、データ ソースへの接続に使用するアカウント情報を含む接続先設定の入力を求められます。

    ![データソースへの接続](media/data-source-provide-cred.png)

7. 接続がされたら、エンティティに使用するデータを選択してください。 データとソースを選択すると、 Power Platform Dataflowサービスは続いてデータフロー内のデータを最新の状態に保つために、データソースに再接続します。これは、この設定プロセスの後半で選択する頻度で行われます。


    ![データを選択します](media/choose-data.png)

エンティティで使用するデータを選択したら、データフローエディタを使用して、そのデータをデータフローで使用するために必要な形式に成形または変換することができます。

## <a name="use-the-dataflow-editor-to-shape-or-transform-data"></a>データフローエディタを使用してデータを成形または変換する
Power BI Desktop のPower Query エディタと同様に、Power Query の編集機能を使用して、選択したデータをエンティティに最も適した形式に成形することができます。 Power Query に関する詳細については、 [Power BI Desktopにおけるクエリの概要](/power-bi/desktop-query-overview)を参照してください。

クエリ エディタがステップごとに作成するコードを確認する場合や、独自のシェーピング コードを作成する場合には、高度なエディタを使用することができます。

![詳細エディター](media/advanced-editor.png)

## <a name="dataflows-and-the-common-data-model"></a>データフローと Common Data Model 
データフローエンティティには、ビジネスデータを Common Data Model に簡単にマッピングし、Microsoft やサードパーティのデータで拡張し、機械学習に簡単にアクセスできる新たなツールが含まれています。 これらの新機能を活用することで、ビジネス データに関するインテリジェントで実用的な情報を提供することができます。 以下に説明するクエリーの編集手順で変換を完了すると、Common Data Modelで定義されているように、データソーステーブルの列を標準エンティティフィールドにマッピングすることができます。 標準エンティティには、Common Data Model で定義された既知のスキーマがあります。

このアプローチと Common Data Model に関する詳細情報については、 [Common Data Model](/powerapps/common-data-model/overview) を参照してください。

データフローで Common Data Model を活用するには、 **クエリの編集** ダイアログの **標準にマッピング** の変換を選択します。 表示された **エンティティのマッピング** 画面で、マッピングを行う標準エンティティを選択します。

![標準エンティティにマッピングする](media/map-to-standard-entity.png)

標準フィールドにソース列をマッピングすると、以下が発生します:

1.  ソース列には標準フィールド名が使用されます (名称が異なる場合はカラムの名前が変更されます)。 

2.  ソース列は、標準フィールドのデータ型を取得します。 

Common Data Model の標準を保持するには、マッピングされていないすべての標準フィールドは *NULL* 値となります。

マッピングされていないソース列はすべて残留し、マッピングの結果がユーザー定義のフィールドを持つ標準エンティティとなります。

選択が完了し、エンティティとそのデータ設定が完了したら、次の手順 (データフローの更新頻度の選択) に進みます。

## <a name="set-the-refresh-frequency"></a>更新頻度の設定
エンティティの定義が完了したら、接続されたデータソースごとの更新頻度を設定します。

1. データフローでは、データを最新の状態に保つためにデータ更新のプロセスを使用しています。 **Power Platform データフロー設定ツール**では、データフローを任意のスケジュール間隔で手動または自動での更新を選択することが出来ます。 更新を自動的に設定するには、 **自動的に更新する** を選択します。

   ![自動で更新する](media/refresh-automatically.png)

2. データフローの更新頻度、開始日と時間をUTC時間で入力します。

3. **作成**を選択します。
<!-- 
## Connect to your dataflow in Power BI Desktop
Once you’ve created your dataflow and you have scheduled the refresh frequency
for each data source that will populate the model, you’re ready for the final task, which is connecting to your dataflow from within Power BI Desktop.

To connect to the dataflow, in Power BI Desktop select **Get Data** > **Power Platform** > **Power Platform dataflows** > **Connect**.

![Connect to the dataflow](media/get-data.png)

Navigate to the environment where you saved your dataflow, select
the dataflow, and then select the entities that you created from the list.

You can also use the search bar, near the top of the window, to quickly find the
name of your dataflow or entities from among many dataflow entities.

When you select the entity and then select the **Load** button, the entities
appear in the **Fields** pane in Power BI Desktop, and appear and behave just
like tables from any other dataset. -->

## <a name="using-dataflows-stored-in-azure-data-lake-storage-gen2"></a>Azure Data Lake Storage Gen2に格納されているデータフローを使用する
組織によっては、データフローの作成と管理に独自のストレージを使用する場合が想定されます。 要件に従ってストレージアカウントを正しく設定していればば、データフローを Azure Data Lake Storage Gen2 と統合することができます。 詳細情報: [データフロー ストレージに Azure Data Lake Storage Gen2を接続する](/power-bi/service-dataflows-connect-azure-data-lake-storage-gen2) 

## <a name="troubleshooting-data-connections"></a>データ接続のトラブルシューティング
データフローのデータソースへと接続すると、問題が発生する場合があります。 このセクションでは、問題発生時のトラブルシューティングをご案内します。

-   **Salesforce コネクタ** Salesforce の試用アカウントをデータフローで使用すると、接続エラーとなりますが特に何のメッセージも表示されません。 これを解決するには、Salesforce の運用アカウント、または開発アカウントを使用してください。

-   **SharePoint  コネクタ** SharePoint サイトのルートアドレスを指定していることを確認してください。これにはサブフォルダやドキュメントを含めません。 例として、 *https://microsoft.sharepoint.com/teams/ObjectModel* のような形のリンクを使用してください。


-   **JSON ファイル コネクタ** 現在は、 JSON ファイルへの接続には、基本認証のみを使用することができます。 たとえば、 *https://XXXXX.blob.core.windows.net/path/file.json?sv=2019-01-01&si=something&sr=c&sig=123456abcdefg* のようなURLには現在対応していません。

-   **Azure SQL Data Warehouse.** データフローは、Azure SQLデータ ウェアハウスの Azure Active Directory 認証に現在対応していません。 このような場合には基本認証を使用してください。

## <a name="next-steps"></a>次のステップ
以下の記事では、データフローを使用するにあたっての詳細情報とシナリオを提供しています:

-   [Common Data Service のエンティティにデータを追加する](data-platform-cds-newentity-pq.md)

-   [オンプレミスのデータ ソースでデータ フローを使用する](using-dataflows-with-on-premises-data.md)

-   [Azure Data Lake Storage Gen2 をデータフロー ストレージに接続する](/power-bi/service-dataflows-connect-azure-data-lake-storage-gen2)

Common Data Model の詳細については、次を参照してください:

-   [Common Data Model - 概要](/powerapps/common-data-model/overview)

-   [GitHub で Common Data Model スキーマとエンティティに関する詳細を理解する](https://github.com/Microsoft/CDM)
