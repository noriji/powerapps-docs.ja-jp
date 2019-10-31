---
title: Azure Data Lake Storage Gen2 をデータフロー ストレージに接続する | MicrosoftDocs
description: Azure Data Lake Storage Gen2 をデータフロー ストレージに接続する方法
ms.custom: ''
ms.date: 09/05/2019
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
# <a name="connect-azure-data-lake-storage-gen2-for-dataflow-storage"></a>Azure Data Lake Storage Gen2 をデータフロー ストレージに接続する

[!INCLUDE [cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

データフローの構成をすることでそのデータをAzure Data Lake Storage Gen2 のアカウントに保存することが出来ます。 この記事では、そのために必要となる一般的な手順を説明し、その手順に沿ったガイダンスとベスト・プラクティスを記載しています。 

定義およびデータ ファイルを data lake に格納するようにデータ フローを構成すると、以下のような利点があります。
- Azure Data Lake Storage Gen2は、きわめて拡張性の高いデータのストレージ機能を提供します。
- Azure データサービスの GitHub サンプルが示しているように、IT部門の開発者は Dataflow データと定義ファイルを利用して、Azure データと人工知能(AI) サービスを利用することができます。
- これにより、開発者のリソースをデータフローと Azure に使用して、データフローのデータを内部アプリケーションと基幹業務ソリューションに統合することができます。

## <a name="requirements"></a>要件
データフローに Azure Data Lake Storage Gen2 を使用するには、以下が必要となります:
- PowerApps の新しい環境 PowerApps では、 Azure Data Lake Storage Gen2 を処理の対象先として使用してデータフローを作成することができます。 この作業を行うに当たっては環境内での認証が必要になります。 
- Azure のサブスクリプション ID。 Azure Data Lake Storage Gen2 を使用するには、Azure のサブスクリプションが必要となります。
- リソース グループ。 既存のリソースグループを使用するか、新規で作成することが出来ます。
- Azure Storage アカウント。 ストレージのアカウントは Data Lake Storage Gen2 の機能を有効にしておく必要があります。

> [!TIP]
> Azure サブスクリプションがない場合は、 [無料の試用アカウント](https://azure.microsoft.com/free/) を作成してください。

## <a name="prepare-your-azure-data-lake-storage-gen2-for-power-platform-dataflows"></a>Power Platform データフロー の Azure Data Lake Storage Gen2 を準備します。
Power BI を Azure Data Lake Storage Gen2 のアカウントと設定をする前に、ストレージ アカウントの作成および、設定が必要となります。 Power Platform のデータフロー要件は以下のとおりです。
1.  ストレージのアカウントは、 PowerApps のテナントと同じ Azure Active Directory テナントに作成する必要があります。
2.  ストレージアカウントは、使用する PowerApps 環境と同じ領域で作成することを推奨します。 PowerApps 環境の場所を確認するには、管理者に問い合わせてください。
3.  ストレージのアカウントは 階層型名前空間の機能を有効にしておく必要があります。
4.  ストレージのアカウントの所有者権限が付与されている必要があります。

以下のセクションでは、 Azure Data Lake Storage Gen2アカウントの構成に必要な手順について説明します。

## <a name="create-the-storage-account"></a>ストレージ アカウントを作成する
[Azure Data Lake Storage Gen2 ストレージアカウントを作成する](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-quickstart-create-account) に記載されている手順に従ってください。
1.  Power BI テナントを同じ場所を選択し、ストレージを StorageV2 (general purpose v2) として設定してください 。
2.  階層型名前空間を有効にしている必要があります。 
3.  レプリケーション設定に地理冗長ストレージへの読み取りアクセス権を指定しておくことを推奨します。



<!--from editor: I haven't heard of Athena before. Is it the Amazon service, https://aws.amazon.com/athena/? If so, it probably should be identified as Amazon at first mention. -->


## <a name="create-a-cross-origin-resource-sharing-cors-rule-for-the-athena-service"></a>Athena サービスに対するオリジン間リソース共有(CORS) のルールを作成する

> [!NOTE]
> Power Platform は Athena サービスを利用して data lake を PowerApps 環境に接続します。 このセクションでは、Athenaサービスをデータフロー用に設定できるように、ストレージ アカウントに役割を付与する必要があります。

続いてに、Athenaサービスが Webブラウザおよび PowerApps ポータル経由で、ストレージ アカウントにアクセスできるように設定する必要があります。 Webブラウザは、Webページが別のドメインのAPIを呼び出すことを防ぐ [同一生成元ポリシー](http://www.w3.org/Security/wiki/Same_Origin_Policy) として知られているセキュリティ制限を実装しています。CORSは、あるドメイン (起点のドメイン) が別のドメインのAPIを呼び出す安全な方法を提供します。 CORS の詳細については、 [CORS の仕様](http://www.w3.org/TR/cors/) を参照してください。

Azure ポータルの設定ページで作成したストレージアカウントの手順に従ってください。 CORSのメニュー項目で、BLOBサービスを選択して以下の情報を入力します。 

|設定  |Value  |
|---------|---------|
|許可されているオリジン   | https://athena-ui-prod.trafficmanager.net     |
|許可されている方法   |  DELETE、 GET、 HEAD、 MERGE、 POST、 OPTIONS、 PUT、 PATCH   |
|許可されているヘッダー   | *    |
|公開されているヘッダー   | *    |
|最大時間 |   *  |


以下の画像は Athena サービス向けに構成された CORS のルールを示しています。

![CORS のルール](media/dataflows-cores-rule.png)

## <a name="connect-your-azure-data-lake-storage-gen2-to-powerapps"></a>Azure Data Lake Storage Gen2 を PowerApps に接続する
Azure ポータルで Azure Data Lake Storage Gen2 のアカウントを設定が完了したら、特定のデータフローまたは PowerApps 環境に接続することができます。 レイクを環境に接続することで、環境内の他の作業者や管理者がデータフローを作成することができ、レイク内のデータを保存することができます。 

Azure Data Lake Storage Gen2 のアカウントとデータフローを接続するには、以下の手順に従ってください:
1.  [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)にサインインし、どの環境に接続したのかを確認します。 環境切り替え機能はヘッダーの右側に配置されています。 
2. 左側のナビゲーション ウィンドウで、 **データ**の横にある矢印を選択します。

   ![PowerApps  メーカー ポータルデータ タブ](media/powerapps-portal-data.png)

3. 表示されたリストにて、 **データフロー** を選択し、コマンド バー上の **新規データフロー**を選択します。

   ![新規データフローの作成](media/new-dataflow.png) 

4. 分析エンティティを選択します。 これらのエンティティは、Azure Data Lake Store Gen2 アカウントに保存するデータを指定します。 

   ![分析エンティティの選択](media/select-analytical-entities.png)

## <a name="select-the-storage-account-to-use-for-dataflow-storage"></a>データフロー ストレージを使用するストレージアカウントを選択する
ストレージアカウントが環境と関連付けられていない場合は、 **data lake に関連付ける** のダイアログ ボックスが表示されます。 サインインを行い、前述の手順で作成した data lake を確認する必要があります。 この例では、data lake は環境に関連付けらていないため、環境追加を促すメッセージが表示されます。 



<!--from editor: Should "storage account" be in bold because it's something the user has to select? --"

1. Select storage account.

    The **Select Storage Account** screen appears.
    
    ![Select storage account](media/select-storage-account.png)
    
2. Select the **Subscription ID** of the storage account.
3. Select the **Resource group name** in which the storage account was created.
4. Enter the **Storage account name**.
5. Select **Save**.

Once these steps are successfully completed, your Azure Data Lake Storage Gen2 account is connected to Power Platform Dataflows and you can continue to create a dataflow.

## Considerations and limitations
There are a few considerations and limitations to keep in mind when working with your dataflow storage:
- Linking an Azure Data Lake Store Gen2 account for dataflow storage is not supported in the default environment.
- Once a dataflow storage location is configured for a dataflow, it can't be changed.
- By default, any member of the environment can access dataflow data using the Power Platform Dataflows Connector. However, only the owners of a dataflow can access its files directly in Azure Data Lake Storage Gen2. To authorize additional people to access the dataflows data directly in the lake, you must authorize them to the dataflow’s CDM folder in the data lake or the data lake itself.
- When a dataflow is deleted, its CDM folder in the lake will also be deleted. 

> [!IMPORTANT]
> You shouldn't change files created by dataflows in your organization’s lake or add files to a dataflow’s CDM folder. Changing files might damage dataflows or alter their behavior and is not supported. Power Platform Dataflows only grants read access to files it creates in the lake. If you authorize other people or services to the filesystem used by Power Platform Dataflows, only grant them read access to files or folders in that filesystem.

## Frequently asked questions
*What if I had previously created dataflows in my organization’s Azure Data Lake Storage Gen2 and would like to change their storage location?*

   You can't change the storage location of a dataflow after it was created.

*When can I change the dataflow storage location of an environment?*

   Changing the environment's dataflow storage location is not currently supported. 

## Next steps
This article provided guidance about how to connect an Azure Data Lake Storage Gen2 account for dataflow storage. 

For more information about dataflows, the Common Data Model, and Azure Data Lake Storage Gen2, see these articles:
- [Self-service data prep with dataflows](https://go.microsoft.com/fwlink/?linkid=2099972)
- [Creating and using dataflows in PowerApps](https://go.microsoft.com/fwlink/?linkid=2100076)
- [Connect Azure Data Lake Storage Gen2 for dataflow storage](https://go.microsoft.com/fwlink/?linkid=2099973)
- [Add data to an entity in Common Data Service](https://go.microsoft.com/fwlink/?linkid=2100075)

For more information about Azure storage, see this article:
- [Azure Storage security guide](https://docs.microsoft.com/azure/storage/common/storage-security-guide)

For more information about the Common Data Model, see these articles:
- [Common Data Model - overview](https://docs.microsoft.com/powerapps/common-data-model/overview) 
- [Common Data Model folders](https://go.microsoft.com/fwlink/?linkid=2045304)
- [CDM model file definition](https://go.microsoft.com/fwlink/?linkid=2045521)

You can ask questions in the [PowerApps Community](https://go.microsoft.com/fwlink/?linkid=2099971).
