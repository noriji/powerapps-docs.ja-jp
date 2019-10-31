---
title: Power Platform データフローでオンプレミス データ ゲートウェイを使う | MicrosoftDocs
description: Power Platform データフローでオンプレミス データ ゲートウェイを使う方法について説明します
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
# <a name="using-an-on-premises-data-gateway-in-power-platform-dataflows"></a>Power Platform データフローでオンプレミス データ ゲートウェイを使う
[!INCLUDE [cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

Power Platform データフローと、オンプレミス SQL Server データベースやオンプレミス SharePoint サイトなどクラウドではないデータ ソースの間でデータを簡単かつセキュリティ移行するため、オンプレミス データ ゲートウェイをインストールします。
管理者権限を持つすべてのゲートウェイを表示し、それらのゲートウェイのアクセス許可および接続を管理できます。

ゲートウェイを使用すると、以下のような接続を使用してオンプレミス データに接続できます。

-   SharePoint

-   SQL Server

-   Oracle

-   Informix

-   Filesystem

-   DB2

## <a name="prerequisites"></a>前提条件

-   PowerApps アカウント。 持っていない場合は、 [30 日間無料でサインアップできます](https://docs.microsoft.com/en-us/powerapps/maker/signup-for-powerapps)。

-   ゲートウェイの管理者権限。 これらのアクセス許可は、インストールするゲートウェイにより既定で提供されます。 管理者が、他のユーザーにゲートウェイのアクセス許可を与えることができます。 

-   オンプレミス ゲートウェイを使用してオンプレミス データへのアクセスをサポートするライセンス。 詳細については、[適切な PowerApps プランの検索ページ](https://powerapps.microsoft.com/pricing/)の「データとシステムに接続」を参照してください。

-   ゲートウェイおよびオンプレミス接続は、ユーザーの既定の環境で作成および使用できます。 詳細: [環境および Microsoft PowerApps に関する作業](../canvas-apps/working-with-environments.md)

## <a name="install-a-gateway"></a>ゲートウェイをインストールする
1.  [powerapps.com](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) の左側のナビゲーション ウィンドウで、**ゲートウェイ**を選択します。

    ![左側のナビゲーション バーのゲートウェイ](media/nav-pane-gateways.png)

2.  一覧からゲートウェイを選択してください。 ゲートウェイの管理者権限がない場合、[ゲートウェイをすぐにインストール](http://go.microsoft.com/fwlink/?LinkID=820931)を選択し、ウィザードのプロンプトに従います。

     ![ゲートウェイ インストール](media/install-gateway-now.png)

     ゲートウェイのインストール方法の詳細については、[オンプレミス データ ゲートウェイを理解する](../canvas-apps/gateway-reference.md)を参照してください。

## <a name="use-an-on-premises-data-source-in-a-dataflow"></a>データフローでオンプレミス データ ソースを使用する
1. データ ソース リストからオンプレミス データ ソースを選択します。

   ![オンプレミス データ ソースを選択します。](media/on-premises-data-sources.png)

2. オンプレミス データにアクセスするために使用される社内ゲートウェイに接続の詳細を提供します。 ゲートウェイ自体を選択すし、選択したゲートウェイの資格情報を提供する必要があります。 管理者となっているゲートウェイだけが一覧に表示されます。

    ![接続の詳細を指定する](media/connection-creds.png)

特定のデータフローに使用するエンタープライズ ゲートウェイを変更し、データフロー オーサリング ツールを使用してすべてのクエリに割り当てられているゲートウェイを変更できます。

> [!NOTE]
> データフローは、新しいゲートウェイを使用して必要なデータ ソースを検索または作成しようとします。 これを行うことができない場合、必要なすべてのデータフローが選択したゲートウェイから使用可能になるまでゲートウェイを変更できません。


## <a name="view-and-manage-gateway-permissions"></a>ゲートウェイのアクセス許可を表示および管理する
1.  [powerapps.com](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) の左側のナビゲーション ウィンドウで、**ゲートウェイ** を選択して、目的のゲートウェイを選択します。

2.  ゲートウェイにユーザーを追加するには、**ユーザー** を選択してユーザーまたはグループを指定し、アクセス許可レベルを指定します。

    -   **使用できます。** このアクセス許可を持つユーザーは、アプリケーションやフローを使用するゲートウェイで接続を作成できますが、ゲートウェイを共有することはできません。 アプリケーションを実行するが共有しないユーザーにこのアクセス許可を使用します。

    -   **使用および共有可能。** このアクセス許可を持つユーザーは、アプリケーションやフローを使用するゲートウェイで接続を作成でき、アプリを共有しているときにゲートウェイを自動的に共有できます。 他のユーザーまたは組織とアプリケーションを共有する必要があるユーザーには、このアクセス許可を使用します。

    -   **管理。** 管理者は、ユーザーの追加、使用可能なすべてのデータ ソースへの接続の作成、ゲートウェイの削除など、ゲートウェイをフル コントロールできます。

      **使用可能** および **使用および共有可能** アクセス許可レベルでは、ゲートウェイ経由で接続するデータ ソースを選択します。

## <a name="view-and-manage-gateway-connections"></a>ゲートウェイ接続を表示および管理する
1.  *powerapps.com* の左側のナビゲーション バーで、**ゲートウェイ** を選択して、目的のゲートウェイを選択します。

2.  目的のアクションを実行します。 
    - 詳細を表示する、設定を編集する、またはゲートウェイを削除するには、**接続** を選択して接続を選択します。
    - 接続を共有するには、**共有** を選択し、ユーザーの追加または削除を行います。

      > [!NOTE]
      > SQL Server 接続などの一部の接続の種類のみを共有できます。 詳細については、[PowerApps でキャンバス アプリケーションのリソースを共有する](../canvas-apps/share-app-resources.md)を参照してください。 <br />
      >
      > 接続の管理方法についての詳細は、[PowerApps でキャンバス アプリケーション接続を管理する](../canvas-apps/add-manage-connections.md)を参照してください。


## <a name="limitations"></a>制限
エンタープライズ ゲートウェイとデータフローを使用する場合の既知の制限がいくつかあります。

-   各データフローは、1 つのゲートウェイのみ使用できます。 したがって、すべてのクエリは、同じゲートウェイを使用して構成する必要があります。

-   ゲートウェイを変更すると、データフロー全体が変わります。

-   複数のゲートウェイが必要な場合、ベスト プラクティスは、複数のデータフロー (ゲートウェイごとに 1 つずつ) を作成し、コンピューティングまたはエンティティ参照機能を使ってデータを統合することです。

-   データフローは、エンタープライズ ゲートウェイを使用してのみサポートされます。 個人用ゲートウェイは、ドロップダウン リストおよび設定画面での選択には使用できません。

ゲートウェイの問題のトラブルシューティングについて、またはネットワークのゲートウェイ サービスの構成については、[オンプレミス データ ゲートウェイを理解する](../canvas-apps/gateway-reference.md)を参照してください。

## <a name="next-steps"></a>次のステップ

- [PowerApps でのデータフローの作成と使用について](create-and-use-dataflows.md)

- [パワークエリを使用して Common Data Service エンティティにデータを追加する](data-platform-cds-newentity-pq.md)

- [Azure Data Lake Storage Gen2 をデータフロー ストレージに接続する](/power-bi/service-dataflows-connect-azure-data-lake-storage-gen2)


