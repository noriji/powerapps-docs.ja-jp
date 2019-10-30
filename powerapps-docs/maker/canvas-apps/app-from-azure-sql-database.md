---
title: Azure SQL Database | からキャンバスアプリを作成します。Microsoft Docs
description: のデータからキャンバスアプリを作成する方法について説明し Azure SQL Database
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 10/29/2019
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: dd5fbbd05ac021b2362c387de845c8a3e1eb33a8
ms.sourcegitcommit: 80a9f5073eefe8813f672569e452e6af9ee72d79
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/29/2019
ms.locfileid: "73050239"
---
# <a name="preview-create-a-canvas-app-from-azure-sql-database"></a>プレビュー: Azure SQL Database からキャンバスアプリを作成する

[このトピックはプレリリース資料であり、変更されることがあります。]

このトピックでは、Azure SQL Database のデータを使用して、PowerApps でアプリを数分で作成します。 ビジネスニーズに合わせてカスタマイズし、任意のデバイスで共有できる、完全に機能するアプリをお客様のデータと共に利用できます。

> [!IMPORTANT]
> - これはプレビュー機能です。
> - プレビュー機能では、可用性と制限された機能が制限される場合があります。 プレビュー機能は、公式リリースの前に提供されており、お客様が早期にアクセスしてフィードバックを提供することができます。

## <a name="prerequisites"></a>前提条件

- ブラウザーでポップアップが有効になっている必要があります。
- Azure サブスクリプションが必要です。 </br>Azure サブスクリプションをお持ちでない場合は、[無料アカウントを作成](https://azure.microsoft.com/free/)してください。
- 既存の SQL Database にアクセスする必要があります。 </br> 既存の SQL Database がない場合は、[新しいデータベースを作成](https://docs.microsoft.com/azure/sql-database/sql-database-single-database-get-started?tabs=azure-portal)します。
- PowerApps リージョンの[IP アドレスまたは Azure サービス](#app-access-to-sql-database)へのアクセスを、ファイアウォール設定の SQL Database に許可する必要があります。
- SQL Database テーブルには、text データ型の列が少なくとも1つ必要です。
- 有効な PowerApps ライセンスが必要です。または、 [30 日間の試用版ライセンス](../signup-for-powerapps.md)にサインアップしてください。

## <a name="create-an-app"></a>アプリを作成する

1. [Azure Portal](https://portal.azure.com)にサインインします。
2. SQL Database に移動します。
3. [PowerApps] を選択します。

    
    ![SQL Database オプションの PowerApps オプション](./media/app-from-azure-sql-database/powerapps-link-azure-portal.png "SQL Database 内の PowerApps オプション")

    > [!NOTE]
    > PowerApps のライセンスをお持ちでない場合は、評価版を開始するためのリンクを含む青色の情報バーが表示されます。 試用版の開始を選択すると、新しいタブが表示され、ライセンスにサインアップします。 完了したら Azure portal に戻り、ブレードを更新して続行します。

4. "Site インスペクション"、"Fundraiser"、"Budget Tracker" など、アプリの名前を入力します。

5. SQL 認証パスワードを入力し、必要に応じてユーザー名を変更します。
6. アプリの作成に使用するドロップダウンリストからテーブルを選択します。

7. **[作成]** を選択します。


    ![アプリの情報を指定する](./media/app-from-azure-sql-database/powerapps-create-page-azure-portal.png "アプリの情報を指定する")

    [PowerApps Studio](https://create.powerapps.com/studio/)が新しいタブで開きます。ポップアップがブロックされている場合は、ポップアップを許可して再試行するようにブラウザーを更新します。 作成されると、SQL Database のデータを含む3ページアプリが作成されます。

## <a name="accessing-your-app"></a>アプリへのアクセス

作成したアプリに再度アクセスするには、 [make.powerapps.com](https://make.powerapps.com)にアクセスしてください。

## <a name="app-environment-and-region"></a>アプリの環境とリージョン

この方法で作成したアプリは、テナントの[既定の環境](https://docs.microsoft.com/power-platform/admin/environments-overview#the-default-environment)を使用し、この環境のリージョンにデプロイします。 デプロイされたアプリのリージョンまたはテナントの既定の環境を[管理センター](https://docs.microsoft.com/power-platform/admin/regions-overview#how-do-i-find-out-where-my-app-is-deployed)から見つけることができます。 特定の環境にあるすべてのアプリを確認するには、 [make.powerapps.com](https://make.powerapps.com)に移動し、リボンから**環境**を選択して、左側の **[アプリ]** を選択します。

## <a name="app-access-to-sql-database"></a>SQL Database へのアプリアクセス

IP アドレスまたは Azure サービスとして SQL Database に接続するように PowerApps を構成できます。

### <a name="app-access-using-ip-address"></a>IP アドレスを使用したアプリアクセス

[Powerapps のシステム要件](limits-and-config.md#ip-addresses)では、アプリのリージョンに応じて powerapps が使用する IP アドレスが一覧表示されます。

このアクセスを構成するには、Transact-sql ストアドプロシージャまたは Azure portal を使用できます。

- SQL Database または SQL Server レベルのファイアウォール規則用のストアドプロシージャ[sp_set_firewall_rule](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-set-firewall-rule-azure-sql-database?view=azuresqldb-current) 。
- SQL Server レベルのファイアウォール規則の[Azure portal](https://docs.microsoft.com/azure/sql-database/sql-database-firewall-configure) 。

### <a name="app-access-as-an-azure-service"></a>Azure サービスとしてのアプリアクセス

PowerApps は、Azure portal を使用して**Azure サービスコントロールへのアクセスを許可**SQL Database に接続できます。 このアクセスを構成するには、 [Azure portal](https://portal.azure.com/)にサインインし、ポータル内を**SQL Server**に移動します。 **ファイアウォールと仮想ネットワーク** を選択し、**Azure のサービスとリソースにこのサーバーへのアクセスを許可**する を オン に設定します。 **[保存]** を選択して変更を送信します。

> [!IMPORTANT]
> このコントロールを [オン] のままにした場合、Azure SQL Database サーバーは、azure の境界内の任意のサブネットからの通信を受け入れます。つまり、Azure のデータセンターに定義されている範囲内にある IP アドレスの1つから発信されます。 コントロールを ON に設定したままにすると、セキュリティの観点からアクセスが過剰になる可能性があります。

## <a name="limitations"></a>事項

- アプリ名には、文字、数字、'-'、' ('、') '、または ' _ ' のみを含めることができます。
- PowerApps で SQL Database に接続するには、SQL 認証が必要です。
- Azure portal からキャンバスアプリを作成するときは、1つのテーブルのみを選択できます。 さらに多くのデータ接続を追加してテーブルやその他のデータソースを追加する場合は、アプリを作成した後でアプリをカスタマイズします。
- PowerApps は、VNet サービスエンドポイントを使用して SQL Database に接続できません。 詳細については、「 [VNet サービスエンドポイント経由のアクセスの許可](https://docs.microsoft.com/azure/sql-database/sql-database-vnet-service-endpoint-rule-overview)」を参照してください。

## <a name="other-considerations"></a>その他の考慮事項

- SQL Database するアプリのアクセスは、[このアプリを共有](share-app.md)するすべてのユーザーに暗黙的に共有されます。 SQL 認証資格情報に、データの読み取りと書き込みのための適切なアクセス権があることを確認します。 </br> たとえば、異なる SQL 認証資格情報を使用して同じ SQL Database に接続し、読み取りと読み取り/書き込みのアクセス権を分離する別のアプリを作成できます。
- パフォーマンスに関する考慮事項については、スロットルの制限、デリゲート可能関数と操作、既知の問題、およびこの機能が使用する[SQL Database](https://docs.microsoft.com/connectors/sql/)コネクタの制限事項を確認してください。
- 既定以外の環境用のアプリを作成する必要がある場合は、 [make.powerapps.com](https://make.powerapps.com)からアプリを作成し、SQL Database のデータを使用してテナント用の別のリージョンを作成します。

## <a name="next-steps"></a>次の手順

このクイックスタートでは、Azure portal を使用して、SQL Database のデータを使用してアプリを作成しました。 次の手順として、ビジネスニーズに合わせて、コントロール、イメージ、ロジックを使用してアプリをカスタマイズします。

> [!div class="nextstepaction"]
> [PowerApps でキャンバスアプリインターフェイスを設計する](add-configure-controls.md)

## <a name="see-also"></a>関連項目

- [PowerApps でキャンバスアプリを共有する](share-app.md) </br>
- [PowerApps でキャンバスアプリにデータ接続を追加する](add-data-connection.md#add-data-source)</br>
- [Microsoft Learn: PowerApps でキャンバスアプリをカスタマイズする](https://docs.microsoft.com/learn/modules/customize-apps-in-powerapps/)
