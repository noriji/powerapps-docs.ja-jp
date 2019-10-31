---
title: レポート機能をモデル駆動型アプリに追加
ms.custom: ''
ms.date: 08/16/2019
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: Mattp123
ms.assetid: b4098c96-bce1-4f57-804f-8694e6254e81
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="add-reporting-features-to-your-model-driven-app"></a>レポート機能をモデル駆動型アプリに追加

PowerApps アプリに有益な事業情報をユーザーに提供するレポートを含めることができます。 このレポートは SQL Server Reporting Services に基づいており、典型的な SQL Server Reporting Services レポートで使用できる機能と同じ一連の機能を備えています。

> [!div class="mx-imgBorder"] 
> ![](media/progress-against-goals-report.png "目標に対しての進行状況の標準レポート")

システム レポートは、すべてのユーザーが使用できます。 ユーザーが作成または所有するレポートは、特定の同僚またはチームと共有することや、すべてのユーザーがレポートを使用できるように、組織に対してそのレポートを使用可能にすることができます。 これらのレポートは Common Data Service に独自の FetchXML クエリを使用して、データを取得してレポートを作成します。 PowerApps アプリで作成したレポートは、フェッチ ベースのレポートです。

> [!NOTE]
> レポート機能は、タブレットや電話などのモバイル デバイス上で実行されているキャンバス アプリやモデル駆動型アプリでは機能しません。 

<!-- Reports can be built in either of the following ways.

- From a model-driven app using the report wizard. More information: [Create or edit a report using the Report Wizard](/dynamics365/customer-engagement/basics/create-edit-copy-report-wizard) 
- Create custom reports using SQL Server Data Tools and Report Authoring Extensions. More information: [Reporting and Analytics Guide](/dynamics365/customer-engagement/analytics/reporting-analytics-with-dynamics-365)  -->


## <a name="add-reporting-to-a-unified-interface-app"></a>レポートを統一インターフェイス アプリに追加
フェッチ ベースのレポート機能をアプリに追加できます。それにより、ユーザーがレポートを実行、共有、作成、および編集できます。 これを行うためには、アプリのサイト マップにレポート エンティティを追加します。 

1. [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) にサインインして、編集用の既存アプリを開きます。 
2. アプリ デザイナーで、**サイト マップ**の隣りの![サイト マップ編集のための鉛筆アイコン](media/ccf-pencil-icon.png)を選択します。 
3. サイトマップ デザイナーで**追加**を選択し、その後**領域**を選択します。 
4. **タイトル** ボックスに、*レポート*などの領域のタイトル名を入力します。 
5. 前の手順で名前を付けた領域を選択し、**追加**、**グループ**の順に選択して、グループ内の**タイトル** ボックスに*レポート*などのグループ タイトル名を入力します。 
6. 前の手順で名前を付けたグループを選択し、**追加**、**サブエリア**の順に選択して、次のプロパティを含めます。 

   - **Type**。 **エンティティ**を選択します。
   - **エンティティ**。 エンティティの一覧から**レポート** エンティティを選択します。  
   - **タイトル**。 *レポート*など、わかりやすいタイトルを入力します。

      ![サイトマップにレポートを追加](media/report-entity-sitemap.png)

7. **保存して閉じる**を選択してアプリ デザイナーに戻ります。 


8. アプリ デザイナーで**保存**を選択し、**公開**を選択します。

これでアプリには**レポート**領域が表示され、ユーザーはアクセス許可を持つレポートを表示、実行、割り当て、共有、および編集できます。また、レポート ウィザードを使って新しいレポートを作成することもできます。 

> [!div class="mx-imgBorder"] 
> ![](media/report-feature-in-app.png "レポート ビュー")

## <a name="options-for-creating-new-reports"></a>新規レポートを作成するオプション
次の 2 つの方法のいずれかで新しいレポートを作成できます。
- レポート ウィザードを使用します。 レポートが有効化されているモデル駆動型アプリを開き、レポート ウィザードを実行して新しいレポートを作成します。 レポート ウィザードでは、テーブル レポートおよびグラフ レポートが作成されます。これには、ドリルスルー レポートおよび上位 N 件レポートが含まれます。 詳細情報: [レポート ウィザードを使用してレポートを作成する](../../user/create-report-with-wizard.md) 
- レポート作成拡張を使用します。 Visual Studio、SQL Server Data Tools、レポート作成拡張を使用して、フェッチベースの Reporting Services レポートを新規作成またはカスタマイズできます。 詳細については次を参照してください: [ SQL Server Data Tools使用して新たなレポートを作成する](/dynamics365/customer-engagement/analytics/create-a-new-report-using-sql-server-data-tools)

## <a name="report-visibility"></a>レポート表示
取引先企業エンティティの取引先企業概要レポートなど、標準エンティティ レポートはすべてのアプリ ユーザーが利用できます。 レポートを所有するユーザーはレポートを特定の同僚やチームと共有できます。 システム管理者とシステム カスタマイザーは組織全体の可視性を備えたレポートを使用可能にし、すべてのユーザーがレポートを使用できるようにします。 レポートを共有する方法については [他のユーザーやチームとレポートを共有する](../../user/work-with-reports.md#share-a-report-with-other-users-or-teams) を参照してください。 

## <a name="reports-in-solutions"></a>ソリューションでのレポート
レポートはソリューションに対応しています。 コンポーネントとしてソリューションに追加されたレポートは、PowerApps の機能およびユーザー インターフェイスを拡張するソフトウェアの 1 つの単位になります。 ソリューションに追加できるレポートは組織に表示できるものに限られます。

レポートが組織で表示可能かどうか確認する方法: レポートの一覧からモデル駆動型アプリを開き、レポートを選択して **編集** を選択します。 **管理**タブで**公開対象**が**組織**に設定されているかどうかを確認します。 

> [!div class="mx-imgBorder"] 
> ![](media/report-scope.png "組織レベル レポートの表示")

レポートのスナップショットは、ソリューションの一部として追加、インポート、エクスポートできます。 モデル駆動型アプリでは、レポート、サブレポート、レポート カテゴリ、レポート表示領域、およびレポート関連のレコードの種類がレポート セットのコンポーネントと見なされます。 ソリューションの更新を非上書きモードでインポートする際に、カスタマイズされたレポート セットのコンポーネントが存在した場合、そのソリューションによるレポートの更新はすべて無視されます。

## <a name="related-topics"></a>関連トピック
[レポートに関する作業](/powerapps/user/work-with-reports)<br/>
[レポート ウィザードを使用したレポートの作成](/powerapps/user/create-report-with-wizard)<br/>
[PowerApps の外部からレポートを追加する](/powerapps/user/add-existing-report)<br/>
[レポートの既定のフィルターの編集](/powerapps/user/edit-report-filter)<br/>
[レポートのトラブルシューティング](/powerapps/user/troubleshoot-reports)
