---
title: ポータルを使用して Power BI 統合を設定する |MicrosoftDocs
description: ポータルとの Power BI 統合をセットアップする方法について説明します。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 6a471dba2f91ca869ad9ba9da46f6e02cb2a643d
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2019
ms.locfileid: "73543024"
---
# <a name="set-up-power-bi-integration"></a>Power BI 統合を設定する

Power BI は、シンプルで対話型の視覚化を使用して洞察を提供するための最適なツールの1つです。 ポータルの web ページで Power BI からダッシュボードとレポートを表示するには、PowerApps ポータル管理センターから Power BI 視覚化を有効にする必要があります。 また、Power BI Embedded サービスの統合を有効にすることで、Power BI の新しいワークスペースで作成されたダッシュボードとレポートを埋め込むこともできます。

> [!NOTE]
> - 適切な Power BI ライセンスを持っている必要があります。
> - Power BI Embedded サービスを使用するには、適切な Power BI Embedded ライセンスを持っている必要があります。 詳細については、「[ライセンス](https://docs.microsoft.com/power-bi/developer/embedded-faq#licensing)」を参照してください。

## <a name="enable-power-bi-visualization"></a>Power BI の視覚エフェクトを有効にする

Power BI 視覚エフェクトを有効にすると、powerbi 液体タグを使用して、ポータルの web ページにダッシュボードとレポートを埋め込むことができます。

1.  [PowerApps ポータル管理センター](admin-overview.md)を開きます。

2.  **Power BI ビジュアライゼーション > 有効**にするには**Power BI 統合のセットアップ**に関するページを参照してください。

    > [!div class=mx-imgBorder]
    > ![Power BI の視覚エフェクトを有効にする](../media/enable-power-bi-visualization.png "Power BI の視覚エフェクトを有効にする")

3.  確認メッセージで **[有効化]** を選択します。 Power BI の視覚エフェクトが有効になっている間、ポータルは再起動され、数分間利用できなくなります。 Power BI の視覚エフェクトが有効になっていると、メッセージが表示されます。

カスタマイザーは[powerbi](../liquid/portals-entity-tags.md#powerbi)液体タグを使用して、ポータルの web ページに Power BI ダッシュボードとレポートを埋め込むことができます。 Power BI のコンテンツを埋め込むときに、カスタマイザーは[フィルターパラメーター](https://docs.microsoft.com/power-bi/service-url-filters)を使用して、パーソナライズされたビューを作成できます。 詳細情報: [Powerbi 液体タグ](../liquid/portals-entity-tags.md#powerbi)

### <a name="disable-power-bi-visualization"></a>Power BI の視覚エフェクトを無効にする

1.  [PowerApps ポータル管理センター](admin-overview.md)を開きます。

2.  **Power BI 統合のセットアップ**に関するページを参照して**Power BI の視覚化を無効** > してください。

    > [!div class=mx-imgBorder]
    > ![Power BI の視覚エフェクトを無効にする](../media/disable-power-bi-visualization.png "Power BI の視覚エフェクトを無効にする")

3. 確認メッセージで **[無効]** を選択します。 Power BI の視覚エフェクトが無効になっている間は、ポータルが再起動され、数分間利用できなくなります。 Power BI の視覚エフェクトを無効にすると、メッセージが表示されます。

## <a name="enable-power-bi-embedded-service"></a>Power BI Embedded サービスを有効にする

Power BI Embedded サービスを有効にすると、Power BI の新しいワークスペースで作成されたダッシュボードとレポートを埋め込むことができます。 ダッシュボードとレポートは、powerbi 液体タグを使用して、ポータルの web ページに埋め込まれます。

**前提条件**: Power BI Embedded サービスを有効にする前に、Power BI の新しいワークスペースにダッシュボードとレポートが作成されていることを確認してください。 ワークスペースを作成したら、グローバル管理者に管理者アクセス権を付与します。これにより、ワークスペースが PowerApps ポータル管理センターに表示されます。 新しいワークスペースを作成し、それらへのアクセスを追加する方法の詳細については、「 [Power BI で新しいワークスペースを作成](https://docs.microsoft.com/power-bi/service-create-the-new-workspaces)する」を参照してください。

**Power BI Embedded サービスの制限**事項: 制限事項については、「[考慮事項と制限](https://docs.microsoft.com/power-bi/developer/embed-service-principal#considerations-and-limitations)事項」を参照してください。

> [!NOTE]
> Powerbi 液体タグが機能するように Power BI 視覚エフェクトが有効になっていることを確認します。

1. [PowerApps ポータル管理センター](admin-overview.md)を開きます。

2. **Power BI Embedded サービスを有効に**する > **Power BI 統合のセットアップ**に関するページを参照してください。

    > [!div class=mx-imgBorder]
    > ![Power BI Embedded サービスを有効にする](../media/enable-powerbi-embedded-button.png "Power BI Embedded サービスを有効にする")

3. [ **Power BI Embedded サービスの統合を有効に**する] ウィンドウで、ダッシュボードとレポートの表示に使用するワークスペースを選択し、ポータルで**選択したワークスペース**の一覧に Power BI 移動します。

    > [!div class=mx-imgBorder]
    > ![Power BI ワークスペースの選択](../media/enable-powerbi-embedded-window.png "Power BI ワークスペースの選択")
    
    > [!NOTE]
    > 選択した**ワークスペース**の一覧にワークスペースを追加すると、数分後にデータベースとレポートが表示されます。
    

4. **[有効]** を選択します。 Power BI Embedded サービスが有効になっている間、ポータルが再起動され、数分間利用できなくなります。 Power BI Embedded サービスが有効になっていると、メッセージが表示されます。

ここで、セキュリティグループを作成し、それを Power BI アカウントに追加する必要があります。 詳細については、「[セキュリティグループを作成して Power BI アカウントに追加する](#create-security-group-and-add-to-power-bi-account)」を参照してください。

### <a name="create-security-group-and-add-to-power-bi-account"></a>セキュリティグループを作成して Power BI アカウントに追加する

Power BI Embedded サービス統合を有効にした後、Azure Active Directory でセキュリティグループを作成し、メンバーを追加してから、Power BI 管理ポータルを使用して Power BI にセキュリティグループを追加する必要があります。 これにより、新しい Power BI ワークスペースで作成されたダッシュボードとレポートをポータルに表示できるようになります。

> [!NOTE]
> Power BI Embedded サービスを有効にするために使用したのと同じグローバル管理者アカウントでサインインする必要があります。

**手順 1: セキュリティグループを作成する**

1. ディレクトリのグローバル管理者アカウントを使用して[Azure portal](https://portal.azure.com)にサインインします。

2. **[Azure Active Directory]** 、 **[グループ]** の順に選択し、 **[新しいグループ]** を選択します。

3. **[グループ]** ページで、次の情報を入力します。

    - **グループの種類**: セキュリティ。

    - **グループ名**: ポータル Power BI Embedded サービス。

    - [**グループの説明]** : このセキュリティグループは、ポータルと Power BI Embedded サービスの統合に使用されます。

    - **メンバーシップの種類**: 割り当て済み。

      > [!div class=mx-imgBorder]
      > ![Power BI Embedded サービスのセキュリティグループの作成](../media/powerbi-embed-security-group.png "Power BI Embedded サービスのセキュリティグループの作成")

4. **[作成]** を選択します。

**手順 2: グループメンバーを追加する**

**前提条件**: メンバーをセキュリティグループに追加する前に、ポータルのアプリケーション ID を持っている必要があります。 ポータルのアプリケーション ID は、 [PowerApps ポータル管理センター](admin-overview.md)の **[ポータルの詳細]** タブで確認できます。

1. ディレクトリのグローバル管理者アカウントを使用して[Azure portal](https://portal.azure.com)にサインインします。

2. **[Azure Active Directory]** を選択し、 **[グループ]** を選択します。

3. **[グループ-すべてのグループ]** ページで、**ポータル Power BI Embedded サービス**グループを検索し、それを選択します。

    > [!div class=mx-imgBorder]
    > ![Power BI Embedded サービスのセキュリティグループを検索して選択します。](../media/search-security-group.png "Power BI Embedded サービスのセキュリティグループを検索して選択します。")

4. ポータルの**Power BI Embedded サービスの概要** ページで、**管理** 領域から **メンバー** を選択します。

5. **[メンバーの追加]** を選択し、テキストボックスにポータルのアプリケーション ID を入力します。

6. 検索結果からメンバーを選択し、[**選択]** を選択します。

    > [!div class=mx-imgBorder]
    > ![Power BI Embedded サービスのセキュリティグループにメンバーを追加する](../media/add-member-powerbi-embed.png "Power BI Embedded サービスのセキュリティグループにメンバーを追加する")

**手順 3: Power BI セットアップ**

1. ディレクトリのグローバル管理者アカウントを使用して[Power BI](https://powerbi.microsoft.com)にサインインします。

2. Power BI サービスの右上にある **[設定]** を選択し、 **[管理ポータル]** を選択します。

    > [!div class=mx-imgBorder]
    > ![Power BI サービスで管理ポータルを選択します](../media/select-admin-portal.png "Power BI サービスで管理ポータルを選択します")

3. **[テナント設定]** を選択します。

4. **[開発者の設定]** セクションで、 **[サービスプリンシパルに Power BI api の使用を許可する]** を選択します。

5. **[特定のセキュリティグループ]** フィールドで、**ポータル Power BI Embedded サービス**グループを検索し、それを選択します。

    > [!div class=mx-imgBorder]
    > ![Power BI 管理ポータルでのセキュリティグループの追加](../media/add-sg-powerbi.png "Power BI 管理ポータルでのセキュリティグループの追加")

6. **[適用]** を選択します。

これで、カスタマイザーは[powerbi](../liquid/portals-entity-tags.md#powerbi)液体タグを使用して、ポータルの web ページに新しい Power BI ワークスペースから Power BI ダッシュボードとレポートを埋め込むことができるようになりました。 Power BI Embedded サービスを使用するには、認証の種類を**powerbiembedded**として指定する必要があります。 Power BI のコンテンツを埋め込むときに、カスタマイザーは[フィルターパラメーター](https://docs.microsoft.com/power-bi/service-url-filters)を使用して、パーソナライズされたビューを作成できます。 詳細については、「 [Powerbi 液体タグ](../liquid/portals-entity-tags.md#powerbi)」を参照してください。


### <a name="manage-the-power-bi-embedded-service"></a>Power BI Embedded サービスを管理する

1. [PowerApps ポータル管理センター](admin-overview.md)を開きます。

2. **Power BI Embedded サービスの管理** > **Power BI 統合のセットアップ**に関するページを参照してください。

    > [!div class=mx-imgBorder]
    > ![Power BI Embedded サービスの管理](../media/manage-powerbi-embedded-button.png "Power BI Embedded サービスの管理")

3. **[Power BI Embedded サービスの統合の管理]** ウィンドウで、ダッシュボードとレポートの表示に使用する Power BI ワークスペースを削除または移動し、ポータルで選択し**たワークスペース**の一覧に表示する必要があります。

    > [!div class=mx-imgBorder]
    > ![Power BI ワークスペースの選択](../media/manage-powerbi-embedded-window.png "Power BI ワークスペースの選択")
    
    > [!NOTE]
    > 選択した**ワークスペース**の一覧からワークスペースを削除した後、変更が反映されるまで最大1時間かかることがあります。 それまでは、データベースとレポートがポータルに表示され、問題はありません。

4. **[保存]** を選択します。

### <a name="disable-the-power-bi-embedded-service"></a>Power BI Embedded サービスを無効にする

1.  [PowerApps ポータル管理センター](admin-overview.md)を開きます。

2.  **Power BI Embedded サービスの管理** > **Power BI 統合のセットアップ**に関するページを参照してください。

    > [!div class=mx-imgBorder]
    > ![Power BI Embedded サービスの管理](../media/manage-powerbi-embedded-button.png "Power BI Embedded サービスの管理")

3. **[Power BI Embedded サービスの統合の管理]** ウィンドウで、 **[Power BI Embedded サービス統合を無効にする]** を選択します。

    > [!div class=mx-imgBorder]
    > ![Power BI Embedded サービスを無効にする](../media/disable-powerbi-embedded-window.png "Power BI Embedded サービスを無効にする")

4. **[保存]** を選択します。

5. 確認メッセージで [ **OK]** を選択します。 Power BI Embedded サービスが無効になっている間は、ポータルが再起動され、数分間利用できなくなります。 Power BI Embedded サービスが無効になっていると、メッセージが表示されます。

## <a name="privacy-notice"></a>プライバシーに関する声明  

[!INCLUDE[cc_privacy_powerbi_tiles_dashboards](../../../includes/cc-privacy-powerbi-tiles-dashboards.md)]

### <a name="see-also"></a>関連項目

[powerbi 液体タグ](../liquid/portals-entity-tags.md#powerbi)<br>[ポータルで Power BI レポートまたはダッシュボードを web ページに追加  
には](add-powerbi-report.md)
