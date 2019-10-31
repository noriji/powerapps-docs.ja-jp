---
title: 'クイックスタート: 従来の Web クライアント アプリケーションの統合インターフェイスへの移行 | MicrosoftDocs'
description: 旧式のWebクライアントアプリケーションを統合インターフェイスに移行する
ms.custom: ''
ms.date: 09/11/2019
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
ms.assetid: 14c4c18c-927c-4ea2-ba66-0531285a99a7
caps.latest.revision: 25
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="quick-start-for-transitioning-your-legacy-web-client-application-to-unified-interface"></a>クイックスタート: 従来の Web クライアント アプリケーションの統合インターフェイスへの移行

統一インターフェイス フレームワークは、応答性を高める Web 設計原則を使用して、すべての画面サイズ、デバイス、表示方向に最適な表示および操作エクスペリエンスを提供します。 このクイックスタート トピックでは、新しい非本番環境を使用して、従来の Web クライアント アプリケーションを統合インターフェイスに移行する方法について説明します。 

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE3JwWU]

既存の非本番環境を使用してWeb クライアント アプリケーションを移行するには、[既存の環境を使用して、統合インターフェイスで旧式のWebクライアント アプリケーションを検証するためのクイックスタート](transition-web-app-existing.md)を参照してください。 
## <a name="prerequisites"></a>前提条件
- 従来の Web クライアント アプリケーション。 
- 必須ではありませんが、現在の導入または開発サイクルに影響を与えないために、非本番環境を使用してアプリケーションのテストをすることを推奨します。 詳細については次を参照してください: [サンドボックス インスタンスの管理](/dynamics365/admin/manage-sandbox-instances)

## <a name="prepare-the-environment"></a>環境の準備
まず、非本番環境を選択し、 **統合インターフェイスのみを使用する** モードを有効にします。このモードでは、環境内のすべてのモデル駆動型アプリに統合インターフェイスが使用されます。 これには、元々旧式の Web クライアント用に構成された Dynamics 365 アプリケーションモジュールも含まれています。

1. [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) にサインインし、**環境** を選択し、サンドボックス環境を選択します。 

2. **設定** > **動作** を選択し、 **統合インターフェイスのみを使用する** を有効にします。

   > [!div class="mx-imgBorder"] 
   > ![統合インターフェイスのみを使用する設定](media/use-unified-interface-only-pac.png)

これは、設定領域で設定することもできます。 **設定** > **管理** > **システム設定** へと移動し、 **一般** タブにて **統合インターフェイスのみを使用する** を **はい**に設定します。

> [!div class="mx-imgBorder"] 
> ![新しい統合インターフェイスのみを使用する](media/use-unified-interface-only.png "新しい統合インターフェイスのみを使用する")


> [!NOTE]
> 環境を以前の状態に戻す必要がある場合は、 統合インタフェースの設定を切り替えることで元のインタフェースに戻すことができます。 詳細については次を参照してください: [統合インターフェイスのみを有効にする](/dynamics365/customer-engagement/admin/enable-unified-interface-only)

## <a name="run-and-validate-your-application-in-the-unified-interface"></a>統合インターフェイスでのアプリケーションの実行と検証
元々Webクライアントアプリケーションであったアプリケーションを実行します。 **統合インターフェイスのみを使用する**を有効にすると、本来Webクライアント用に設定されていたアプリケーションを含む、環境内で使用可能となっているすべてのアプリケーションが統合インターフェイスを使用することに留意してください。

アプリケーションを実行するには、[PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) にサインインし、**アプリ** を選択して実行するアプリケーションを選択します。 または、*https://contoso.crm.dynamics.com/apps/* など、**マイ アプリ** ページに直接アクセスすることもできます。

### <a name="validate-your-app-processes-and-customizations"></a>アプリケーション、プロセス、およびカスタマイズの検証 
すべての使用例を考慮したテストを行うことを推奨します。 最も重要なテストケースから開始することも、論理的な設計パターンにまとめてテストをすることも可能です。 統合インターフェイスは応答性の高い設計がなされているため、画面解像度が異なる複数のデバイスでテストをすることを推奨します。 アプリケーションのテストを進めていく中で、行ったカスタマイズが統合インターフェイスと互換性があること、および再設計が必要な機能や不足している機能について認識することができます。 これらの要素を確認するにあたっての計画設定をし、Microsoft のコミュニティフォーラムに質問やフィードバックを投稿してください。 

> [!IMPORTANT]
> Common Data Service および Dynamics 365 のモデル駆動型アプリの現在のバージョンには、いくつかの非推奨な機能が含まれています。 使用しているアプリケーションで非推奨の機能を確認し、必要に応じて新しい機能に置き換える必要があります。 詳細: [重要な変更 (非推奨) の予定](/dynamics365/get-started/whats-new/customer-engagement/important-changes-coming)

### <a name="dynamics-365-apps"></a>Dynamics 365 アプリ
Dynamics 365 Field Service または Dynamics 365 Project Service Automation アプリケーションを使用していて、統合インターフェイスをテストする場合は、統合インターフェイスでこれらのアプリケーションを検証する前に、新しいサンドボックス環境を設定し、本番環境のコピーを作成して最新の Field Service のバージョンおよび Project Service Automation のバージョンにアップグレードする必要があります。 これを行うには、次の手順を実行します。

1. 新しいサンドボックス環境を [Power Platform 管理センター](https://admin.powerplatform.microsoft.com/environments) または [Dynamics 365 管理センター](https://port.crm.dynamics.com/)から作成します。 詳細については次を参照してください: [サブスクリプションにインスタンスを追加する](/dynamics365/customer-engagement/admin/add-instance-subscription)

2. Dynamics 365 Field Service または Dynamics 365 Project Service Automation アプリを含む運用環境を新しいサンドボックス環境にコピーします。 これを行うには、 Power Platform 管理センターにて運用環境を開き、 **コピー** を選択します。

    > [!div class="mx-imgBorder"] 
    > ![環境のコピー](media/ppac-copy-environment.png "環境のコピー")

3. **環境のコピー** ページで **すべて**を選択し、 **上書きする環境の選択** リストから、新しいサンドボックス環境を選択して、 **コピー**を選択します。 

    > [!div class="mx-imgBorder"] 
    > ![環境の上書](media/ppac-copy-overwrite.png "環境の上書")

4. **環境の上書** ダイアログ ボックスが表示されます。 正しい環境を選択し、正しいオプションが選択されていることを確認してから、 **確認**を選択します。 

5. コピーが正常に完了すると、確認メッセージが表示されます。 

6. メニューバーで **ソリューションの管理** を選択し、 **ソリューション** エリアを開きます。 

    > [!div class="mx-imgBorder"] 
    > ![ソリューションの管理](media/ppac-manage-solutions.png "ソリューションの管理")

    > [!IMPORTANT]
    > **管理モード** が有効になっている場合は、 これを無効にすることで **ソリューション** のエリアを表示できるようなります。 詳細については次を参照してください: [管理モード](/power-platform/admin/sandbox-environments#administration-mode)

7. Field Service または Project Service Automation ソリューションを見つけて選択します。 **アップグレード** のオプションが有効になっている必要があります。 これを選択してアップグレードを行います。 

    > [!div class="mx-imgBorder"] 
    > ![ソリューションのアップグレード](media/ppac-upgrade-solution.png "ソリューションのアップグレード")
    
> [!NOTE]
> 統合インターフェイス上の Field Service および Project Service Automation の最新バージョンは、新しく作成されたインスタンスに対しては既定で使用可能となっています。 古いバージョンがインストールされている既存の環境をアップグレードする場合は、 [Microsoft カスタマーサポート](https://go.microsoft.com/fwlink/?LinkId=853505)に連絡してアップグレードの依頼をする必要があります。 

詳細については、次を参照してください: [Dynamics 365 for Field Service の最新バージョン](/dynamics365/customer-engagement/field-service/version-history#latest-versions) と  [Dynamics 365 for Project Service Automation ホーム ページのアップグレード](/dynamics365/customer-engagement/project-service/upgrade-psa-home-page)

## <a name="next-steps"></a>次のステップ
実装担当チームまたはパートナーは、調査結果に基づいてアプリケーションを統合インターフェイスに移行にあたって必要な作業量を見積もり、潜在的なユーザビリティの向上を発見することができます。 統合インターフェイスでは複数の新機能を利用できるため、アプリケーションを利用するユーザーの価値を高めることができます。 

統合インターフェイスへの移行は、最新のユーザーインターフェイスを作成、既存のプロセスを再確認、およびそのプロセスの有効性、あるいは改善が必要であることを確認するには最良の機会となります。 さらに、アプリケーションがビジネスの要件を反映しているかどうか、既存のアプリをさまざまなチームやロールの複数のアプリに分散できるかどうかを検討するのにも適しています。
詳細については次を確認してください: [アプリ デザイナーを使用してモデル駆動型アプリを設計する](design-custom-business-apps-using-app-designer.md)  

### <a name="see-also"></a>関連項目
<!-- Unified Interface transition community (link tbd) <br />  -->
[統合インターフェイスの活用プレイブック](unified-interface-playbook.md) <br />
[ユーザエクスペリエンスと統合インターフェイスへの移行](approaching-unified-interface.md) <br />
[Unified Interface について](/dynamics365/customer-engagement/admin/about-unified-interface) <br />
[PowerApps におけるモデル駆動型アプリとは?](model-driven-app-overview.md) <br />
[アプリを統一インターフェイスに更新する](/dynamics365/customer-engagement/admin/update-apps-to-unified-interface) <br />
[モデル駆動型アプリの対話型エクスペリエンス ダッシュボードの構成](configure-interactive-experience-dashboards.md) <br />
[モデル駆動型アプリのデータのビジュアル化のためのカスタム コントロールの使用](use-custom-controls-data-visualizations.md) <br />
[PowerApps Component Framework の概要](/powerapps/developer/component-framework/overview) <br />
[全ユーザー向けの統合インターフェイス](/power-platform-release-plan/2019wave2/microsoft-powerapps/unified-interface-app-everybody)

