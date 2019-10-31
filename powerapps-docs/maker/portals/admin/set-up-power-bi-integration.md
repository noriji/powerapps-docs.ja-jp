---
title: ポータルとの Power BI の統合の設定 | MicrosoftDocs
description: ポータルとの Power BI の統合の設定方法を説明します。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: null
ms.date: 07/18/2019
ms.author: shjais
ms.reviewer: null
---

# <a name="set-up-power-bi-integration"></a>Power BI 統合の設定

[!include[cc-beta-prerelease-disclaimer](../../../includes/cc-beta-prerelease-disclaimer.md)]

Power BI は、簡単な対話型のビジュアル化を使用した洞察を提供する最適なツールのひとつです。 ポータルの Web ページの Power BI からダッシュボードおよびレポートを表示するには、ポータル管理センターから Power BI ビジュアル化を有効にする必要があります。 Power BI Embedded サービス統合を有効にすることで、Power BI の新しいワークスペースで作成されたダッシュボードとレポートを埋め込むこともできます。

> [!NOTE]
> - 適切な Power BI ライセンスが必要です。
> - Power BI Embedded サービスを使用するには、適切な Power BI Embedded ライセンスが必要です。 詳細については、[ライセンス](https://docs.microsoft.com/en-us/power-bi/developer/embedded-faq#licensing)を参照してください。

## <a name="enable-power-bi-visualization"></a>Power BI のビジュアル化を有効にする

Power BI ビジュアル化を有効にすると、POWERBI の Liquid タグを使用してポータルの Web ページにダッシュボードおよびレポートを埋め込むことができます。

1.  [PowerApps ポータル管理センター](admin-overview.md) を開きます。

2.  **Power BI 統合の設定** > **Power BI ビジュアル化を有効にする**の順に移動します。

    > [!div class=mx-imgBorder]
    > ![Power BI のビジュアル化を有効にする](../media/enable-power-bi-visualization.png "Power BI のビジュアル化を有効にする")

3.  確認メッセージで、**有効にする**を選択します。 Power BI のビジュアル化が有効化される間、ポータルが再起動されるため数分間使用できなくなります。 Power BI の統合が有効になっている場合に、メッセージが表示されます。

カスタマイズの際に、[Power BI](../liquid/portals-entity-tags.md#powerbi) のLiquid タグを使用して、Power BI ダッシュボードおよびレポートをポータルの Web ページに埋め込むことができます。 カスタマイズで Power BI コンテンツを埋め込むとき、[フィルター パラメーター](https://docs.microsoft.com/en-us/power-bi/service-url-filters)を使用して、個人用ビューを作成できます。 詳細: [Power BI の Liquid タグ](../liquid/portals-entity-tags.md#powerbi)

### <a name="disable-power-bi-visualization"></a>Power BI のビジュアル化を無効にする

1.  [PowerApps ポータル管理センター](admin-overview.md) を開きます。

2.  **Power BI 統合の設定** > **Power BI ビジュアル化を無効にする**の順に移動します。

    > [!div class=mx-imgBorder]
    > ![Power BI のビジュアル化を無効にする](../media/disable-power-bi-visualization.png "Power BI のビジュアル化を無効にする")

3. 確認メッセージで、**無効にする**を選択します。 Power BI のビジュアル化が無効にされる間、ポータルが再起動されるため数分間使用できなくなります。 Power BI の統合が無効になっているとき、メッセージが表示されます。

## <a name="enable-power-bi-embedded-service"></a>Power BI Embedded サービスを有効にする

Power BI サービス統合を有効にすることで、Power BI Embedded の新しいワークスペースで作成されたダッシュボードとレポートを埋め込むこともできます。 ダッシュボードとレポートは powerbi Liquid タグを使用してポータルの Web ページに埋め込まれます。

**前提条件**: Power BI Embedded サービスを有効にする前に、Power BI の新しいワークスペースでダッシュボードおよびレポートを作成したことを確認します。 ワークスペースを作成したら、グローバル管理者への管理者アクセスを提供し、ワークスペースがポータル管理センターに表示されるようにします。 新しいワークスペースを作成し、それらへのアクセスを追加する方法の詳細については、[Power BI での新しいワークスペース (プレビュー) の作成](https://docs.microsoft.com/en-us/power-bi/service-create-the-new-workspaces)を参照してください。

**Power BI Embedded サービスの制限**: 制限については、[考慮事項と制限](https://docs.microsoft.com/en-us/power-bi/developer/embed-service-principal#considerations-and-limitations)を参照してください。

> [!NOTE]
> powerbi Liquid タグが機能するために Power BI のビジュアル化が有効になっていることを確認します。

1. [PowerApps ポータル管理センター](admin-overview.md) を開きます。

2. **Power BI 統合の設定** > **Power BI Embedded サービス (プレビュー) を有効にする**の順に移動します。

    > [!div class=mx-imgBorder]
    > ![Power BI Embedded サービスの有効化](../media/enable-powerbi-embedded-button.png "Power BI Embedded サービスの有効化")

3. **Power BI Embedded サービス統合の有効化**ウィンドウで、Power BI ダッシュボードおよびレポートをポータルに表示する必要があるワークスペースを選択し、**選択済みワークスペース の一覧**に移動します。

    > [!div class=mx-imgBorder]
    > ![ Power BI ワークスペースの選択](../media/enable-powerbi-embedded-window.png " Power BI ワークスペースの選択")
    
    > [!NOTE]
    > ワークスペースを **選択済みワークスペース** の一覧に追加すると、数分後にデータベースとレポートが表示されます。
    

4. **有効化** を選択します。 Power BI Embedded Embedded サービスが無効化される間、ポータルが再起動されるため、数分間使用できなくなります。 Power BI Embedded サービスが有効になっている場合に、メッセージが表示されます。

ここで、セキュリティ グループを作成し、Power BI アカウントに追加する必要があります。 詳細については、[セキュリティ グループを作成し、Power BI アカウントに追加](#create-security-group-and-add-to-power-bi-account)を参照してください。

### <a name="create-security-group-and-add-to-power-bi-account"></a>セキュリティ グループを作成し、Power BI アカウントに追加する

Power BI Embedded サービス統合を有効にしたら、Azure Active Directory でセキュリティ グループを作成し、そこにメンバーを追加した後、Power BI の管理ポータルを通じて Power BI にセキュリティ グループを追加する必要があります。 これにより、新しい Power BI ワークスペースで作成されたダッシュボードとレポートをポータルに表示できるようになります。

> [!NOTE]
> Power BI Embedded サービスを有効にするために使用したのと同じグローバル管理者アカウントとしてサインインする必要があります。

**ステップ 1: セキュリティ グループを作成する**

1. ディレクトリのグローバル管理者アカウントを使用して、[Azure ポータル](https://portal.azure.com)にサインインします。

2. **Azure Active Directory**、**グループ**、**新しいグループ**の順に選択します。

3. **グループ** ページで以下の情報を入力します。

    - **グループの種類**: セキュリティ。

    - **グループ名**: ポータル Power BI Embedded サービス。

    - **グループの説明**: このセキュリティ グループは、ポータルおよび Power BI Embedded サービス統合に使用されます。

    - **メンバーシップの種類**: 割り当て済み。

      > [!div class=mx-imgBorder]
      > ![Power BI Embedded サービスのセキュリティ グループを 作成します](../media/powerbi-embed-security-group.png "Power BI Embedded サービスのセキュリティ グループを 作成します")

4. **作成**を選びます。

**ステップ 2: グループ メンバーを追加する**

**前提条件**: セキュリティ グループにメンバーを追加する前に、ポータルのアプリケーション ID を用意しておいてください。 ポータルの申請 ID は、[PowerApps ポータル管理センター](admin-overview.md)の **ポータルの詳細** タブで使用できます。

1. ディレクトリのグローバル管理者アカウントを使用して、[Azure ポータル](https://portal.azure.com)にサインインします。

2. **Azure Active Directory** を選択して、**グループ**を選択します。

3. **グループ - すべてのグループ** ページから、**ポータル Power BI Embedded サービス** グループを検索し、それを選択します。

    > [!div class=mx-imgBorder]
    > ![Power BI Embedded サービスのセキュリティ グループを検索して選択](../media/search-security-group.png "Power BI Embedded サービスのセキュリティ グループを検索して選択")

4. **ポータル Power BI Embedded サービスの概要** ページの**管理**領域から**メンバー**を選択します。

5. **メンバーの追加** を選択し、テキスト ボックスにポータルのアプリケーション ID を入力します。

6. 検索結果からメンバーを選択し、**選択** を選択します。

    > [!div class=mx-imgBorder]
    > ![Power BI Embedded サービスのセキュリティ グループにメンバーを追加](../media/add-member-powerbi-embed.png "Power BI Embedded サービスのセキュリティ グループにメンバーを追加")

**手順3: Power BI セットアップ**

1. ディレクトリのグローバル管理者アカウントを使用して、[Power BI](https://powerbi.microsoft.com) にサインインします。

2. 設定Power BI サービスの右上の**設定**を選択し、**管理ポータル**を選択します。

    > [!div class=mx-imgBorder]
    > ![Power BI サービスで管理ポータルを選択](../media/select-admin-portal.png "Power BI サービスで管理ポータルを選択")

3. **テナント設定** を選択します。

4. **開発者設定** セクションで、**サービス プリンシパルに Power BI API の使用を許可するPower BIを選択します**。

5. **特定のセキュリティ グループ** フィールドで、**ポータル Power BI Embedded サービス** グループを検索して選択します。

    > [!div class=mx-imgBorder]
    > ![Power BI 管理ポータルでのセキュリティ グループの追加](../media/add-sg-powerbi.png "Power BI 管理ポータルでのセキュリティ グループの追加")

6. **適用**を選択します。

カスタマイズの際に、[Power BI](../liquid/portals-entity-tags.md#powerbi) のLiquid タグを使用して、Power BI ダッシュボードおよびレポートを新しい Power BI ワークスペースからポータルの Web ページに埋め込むことができるようになりました。 Power BI Embedded サービスを使用するには、認証の種類として**powerbiembedded**を指定する必要があります。 カスタマイズで Power BI コンテンツを埋め込むとき、[フィルター パラメーター](https://docs.microsoft.com/en-us/power-bi/service-url-filters)を使用して、個人用ビューを作成できます。 詳細: [Power BI の Liquid タグ](../liquid/portals-entity-tags.md#powerbi)。

### <a name="manage-the-power-bi-embedded-service"></a>Power BI Embedded サービスを管理する

1. [PowerApps ポータル管理センター](admin-overview.md) を開きます。

2. **Power BI 統合の設定** > **Power BI Embedded サービス (プレビュー) を有効にする**の順に移動します。

    > [!div class=mx-imgBorder]
    > ![Power BI Embedded サービス統合を管理する](../media/manage-powerbi-embedded-button.png "Power BI Embedded サービス統合を管理する")

3. **Power BI Embedded サービス統合の管理**ウィンドウで、 ダッシュボードおよびレポートをポータルに表示する必要がある Power BI ワークスペースを削除または移動し、**選択済みワークスペース**の一覧に移動します。

    > [!div class=mx-imgBorder]
    > ![Power BI ワークスペースの選択](../media/manage-powerbi-embedded-window.png "Power BI ワークスペースの選択")
    
    > [!NOTE]
    > **選択済みワークスペース**からワークスペースを削除した後、変更が反映されるまで最大 1 時間かかります。 それまでの間、データベースとレポートは問題なくポータルに表示されます。

4. **保存**を選択します。

### <a name="disable-the-power-bi-embedded-service"></a>Power BI Embedded サービスの無効化

1. [PowerApps ポータル管理センター](admin-overview.md) を開きます。

2.  **Power BI 統合の設定** > **Power BI Embedded サービス (プレビュー) を有効にする**の順に移動します。

    > [!div class=mx-imgBorder]
    > ![Power BI Embedded サービス統合を管理する](../media/manage-powerbi-embedded-button.png "Power BI Embedded サービス統合を管理する")

3. **Power BI Embedded サービス統合**の管理ウィンドウで、**Power BI Embedded サービス統合の無効化** を選択します。

    > [!div class=mx-imgBorder]
    > ![Power BI Embedded サービスの無効化](../media/disable-powerbi-embedded-window.png "Power BI Embedded サービスの無効化")

4. **保存**を選択します。

5. 確認メッセージで、**OK** を選択します。 Power BI Embedded Embedded サービスが無効化される間、ポータルが再起動されるため、数分間使用できなくなります。 Power BI Embedded サービスが無効化されると、メッセージが表示されます。

## <a name="privacy-notice"></a>プライバシーに関する声明  

[!INCLUDE[cc_privacy_powerbi_tiles_dashboards](../../../includes/cc-privacy-powerbi-tiles-dashboards.md)]

### <a name="see-also"></a>関連項目

[Power BIの Liquid タグ](../liquid/portals-entity-tags.md#powerbi)<br> 
[Power BI レポートまたはダッシュボードをポータルの Web ページに追加](add-powerbi-report.md)
