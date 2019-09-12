---
title: 'クイックスタート: 既存の環境を使用して、統合インターフェイスで旧式のWebクライアント アプリケーションを検証する | MicrosoftDocs'
description: 旧式のWebクライアントから統合インターフェイスへの移行を計画し、実行する方法を説明します。
ms.custom: ''
ms.date: 07/24/2019
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
caps.latest.revision: 25
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---


<!--editor comment: I notice two mentions of Dynamics 365 Home page and both are followed by the URL but the text isn't linked. Just want to point that out in case it wasn't intentional. -->


# <a name="quick-start-for-using-an-existing-environment-to-validate-your-legacy-web-client-app-with-the-unified-interface"></a>クイックスタート: 既存の環境を使用して、統合インターフェイスで旧式のWebクライアント アプリケーションを検証する

このクイックスタート トピックでは、既存の環境を使用して現在の構成あるいは既定のソリューションに基づいた、統合インターフェイス アプリケーションを作成する方法について説明します。 これにより、既存の旧式のWebクライアントアプリケーションを並行稼働しながら、統合インターフェイスを調査、テストすることができます。 これにより、ユーザーは環境を切り替えて並列のビューを表示することができます。 新しいサンドボックス環境を作成することでテスト環境を分離し、統合インターフェースのエクスペリエンスのみを表示する方法については、 [クイックスタート: Dynamics 365 for Customer Engagement apps レガシーWebクライアントアプリケーションから統合インターフェイスへの移行](transition-web-app.md) を参照してください。

> [!IMPORTANT]
>  Dynamics 365 for Field Serviceおよび Dynamics 365 for Project Service Automation アプリの環境の場合は、 [Dynamics 365 for Customer Engagement apps](transition-web-app.md#dynamics-365-for-customer-engagement-apps) を参照してください。

## <a name="prerequisites"></a>前提条件 
- 既存の Dynamics 365 for Sales 、または Service legacy web クライアント アプリケーション 
- 必須ではありませんが、非本番環境を使用してアプリケーションをテストすることを推奨します。 詳細については次を参照してください: [サンドボックス インスタンスの管理](/dynamics365/customer-engagement/admin/manage-sandbox-instances) 

## <a name="overview"></a>概要 
このトピックは、統合インターフェイスへの移行を計画/実行する必要がある、旧式のWebクライアントアプリケーションを現在使用しているユーザーを対象としています。 並列環境をセットアップするには、現在の既定のソリューションを元にして新しいアプリケーションを作成します。 これによって既存の作業に影響を与えることなく、現在の開発サンドボックス環境内で実行することができます。

この記事に記載している手順を完了すると、適切な役割を持つユーザーは、Dynamics 365 for Customer Engagement ドロップダウン アプリケーション リスト、または Dynamics 365 ホームページ (http://home.dynamics.com) のアプリケーションリストに新しいアプリケーションが表示されるようになります。

![アプリ の一覧](media/app-list.png)

このトピックで説明されているタスクをソリューションを使用する開発環境で完了すると、ソリューションをテスト環境にインポートして、より多くのユーザーが使い慣れた環境で、アプリケーションをテストおよび比較できるようになります。 

アプリケーション ライフサイクル管理(ALM) および開発運用プロセスに従います。 ソリューションのコンテキスト内にて説明されているすべての手順を実行することを推奨します。 開発環境でアプリケーションをテスト/検証が完了したら、運用環境などでパイロットプログラムとしてより多くのユーザーに公開、さらに掘り下げたアプリケーションのテストをすることができます。 モデル駆動のアプリとサイトマップをソリューションの中に配置することで、この新しいアプリを作成した環境から、既存のプロセスに沿ってアプリをエクスポートすることができます。 

## <a name="process-for-validating-your-legacy-web-client-app-in-an-existing-environment"></a>既存の環境で旧式のWebクライアントアプリケーションを検証するプロセス
 
既存の環境で旧式のWebクライアント アプリケーションを検証するには、以下の3つの手順を実行します:  

1.  既定のソリューションに基づいた新しいソリューションを作成する。
2.  新規駆動型モデル アプリを作成する 
3.  アプリのプロパティを構成する  

直近で [クイックスタート: Dynamics 365 for Customer Engagement apps レガシー Web クライアントアプリケーションから統合インターフェイスへの移行](transition-web-app.md) に示されている手順で、開発環境の **統合インターフェイスのみを使用する** モードを **オン** に切り替えている場合は、この設定を **オフ** に切り替えることで、既存の旧式Webクライアントアプリケーションを実行することができます。

### <a name="create-a-new-solution-thats-based-on-the-default-solution"></a>既定のソリューションに基づいた新しいソリューションを作成する。
1. [PowerApps メーカー ポータル](https://make.powerapps.com) にサインインします。   
2. 環境のリストから、目的の環境を選択します。  
3. 左のナビゲーション ウィンドウで、**ソリューション** を選択します。 
4. メニューバーで **新規ソリューション**を選択します。 
5. **新規ソリューション** ウィンドウで、以下のプロパティを入力します: 
   - **[名前]**. ソリューションの名前を入力します。 名前の例としては、 *統一インターフェイス アプリ*です。 
   - **発行者** 組織で使用する発行者を選択します。 既存のカスタマイズについては、必ずカスタマイズの管理ルールに従ってください。 これにより、モデル駆動型アプリケーションとそのサイトマップのスキーマ名称が既存の標準と一致するようになります。 
   - **バージョン**. これは、ソリューションの既存の標準と管理ルールに従って設定する必要があります。 
6. **作成**を選びます。  
7. ソリューションのリストに新しいソリューションが作成されます。 これを選択してソリューションを開き、次のセクションに進みます。 

### <a name="create-a-new-model-driven-app-in-the-new-solution"></a>新しいソリューションで新しいモデル駆動型アプリを作成する
この手順では、既存のカスタマイズを活用する新たなアプリケーションを作成し、統合インターフェイスでカスタマイズを実行できるようにします。 前述のセクションで作成した新しいソリューションのコンテナ内にアプリケーションを作成します。  

1. メニュー バーの **新規**で、 **アプリ** をポイントし、選択 **モデル駆動型アプリ**を選択します。
2. **新規アプリの作成** ページで、以下のプロパティを入力します。 
   - **[名前]**. アプリケーションの相応する名前を入力します。 たとえば、 *アプリケーションの名称* + *新規* または *統合インターフェーステスト*. 
   - **一意の名前**: これは、ソリューションの接頭辞と、指定したアプリケーション名の簡略版で始まります。 変更することも、そのままにしておくこともできます。  
   - **説明**。 *新しい統合インタフェースのテスト用*などのアプリケーションに関する説明を追加します。  
3. **既存のソリューションを使用してアプリケーションを作成する**を選択し、 **次へ**を選択します。 
4. **ソリューションの選択** リストにて **既定のソリューション** を選択し、 **サイトマップの選択** リストから **サイトマップ** を選択し、 **完了**を選択します。  

   > [!div class="mx-imgBorder"] 
   > ![既存のソリューションを選択する](media/select-existing-solution.png "既存のソリューションを選択する")

5. App Designer が開き、既定のソリューションに存在したすべてのアプリのコンポーネントが表示されます。 **発行**を選択します。  
6. 公開プロセスの完了後、 **プレイ**を選択します。  

ブラウザに新しいウィンドウが開き、既定の Dynamics 365 for Customer Engagement アプリケーション に存在したすべてのエンティティ、サイトマップ、サイトマップのカスタマイズを含む、新たなモデル駆動型アプリケーションが表示されます。  

> [!div class="mx-imgBorder"] 
> ![新規統合インターフェースアプリ](media/new-unified-interface-app.png "新規統合インターフェースアプリ")

PowerApps メーカーポータル **ソリューション** エリアのブラウザ タブに戻ると、新しいモデル駆動型アプリケーションと、共通する名前の サイトマップ クライアント 拡張機能は、両方とも作成したソリューションの一部であることに注意してください。  

> [!div class="mx-imgBorder"] 
> ![ソリューションの資産](media/solution-assets.png "ソリューションの資産")

この手順では、ソリューション内に新しいモデル駆動型アプリケーションを作成し、テスト環境または評価環境にインポートすることができます。 新しいアプリをすぐに体験することもできますが、その前に次の手順で新しいアプリの設定をいくつか行います。 これにより、他のユーザーとの共有することが可能になります。

### <a name="configure-app-properties"></a>アプリのプロパティを構成する
モデル駆動型アプリのプロパティーを設定するにあたって、必要な作業は以下のとおりです: 

- 管理者以外のユーザーがアプリケーションを使用できるように、新しいアプリケーションにユーザーロールの割り当てを行います。  
- わかりやすいURLにカスタマイズすることで、ユーザーが新しいアプリへのショートカットを簡単に共有したり、ブックマークしたり、覚えやすくなります。 


1. *環境の URL*/**apps** へと移動します。 URLは次のような形式です: https://*ご利用の環境*.crm.dynamics.com/apps これにより、環境内のすべてのAppのリストが表示されます。 
2. 作成した新しいモデル駆動型アプリを探します。  
3. アプリのタイルで省略記号を選択し、 **ロールの管理**を選択します。   

   > [!div class="mx-imgBorder"] 
   > ![ロールの管理](media/select-app-ellipsis.png "ロールの管理")

4. 使用可能なロールの領域が右側のウィンドウに一覧表示されます。 必要に応じてロールを選択し、管理者以外のユーザーにアプリケーションへのアクセス権を付与します。 

    > [!IMPORTANT]
    > すべてのユーザーに、 **モデル駆動型アプリ** 権限への **読み取り** アクセス権を含む1つ以上のセキュリティ ロールが付与されている必要があります。 この権限は、セキュリティーロールの カスタマイズ タブにあります。 この権限を持たないユーザーがモデル駆動型アプリを開くと、エラーとなります。  システム管理者およびシステム カスタマイザのセキュリティーロールでは、この権限がすでに有効となっていることに留意してください。 
 
   > [!div class="mx-imgBorder"] 
   > ![モデル駆動型アプリの権限](media/model-driven-app-privilege.png "モデル駆動型アプリの権限")

5. 必要に応じて、 **ロールの管理** ウィンドウで **アプリ URLの接頭辞** を展開して、モデル駆動型アプリのわかりやすいURLにカスタマイズすることができます。 ほとんどすべてのものを指定できることに留意してください。 たとえば、 *new* と入力すると、プレビューに次のURLが表示されます *https://YourEnvironment.crm.dynamics.com/apps/new*.   

   > [!div class="mx-imgBorder"] 
   > ![アプリURLの接頭辞](media/app-url-suffix.png "アプリURLの接頭辞")

   これによって、使いやすく共有しやすいURLになり、ユーザが統合インターフェースを直接起動して使用することができます。 このリンクをブックマークすると便利になります。 

6. **保存**を選択します。 

これで、適切なロールを持つユーザは、Dynamics 365 for Customer Engagement ドロップダウンのアプリ リスト、あるいは Dynamics 365 Home page (http://home.dynamics.com) の両方のアプリ リストで新しいアプリを確認することができます。 
  
   ![アプリのリスト](media/app-list.png "アプリのリスト")

**統合インターフェイスのみを使用する** モードが **オフ** に設定されていると、ユーザが環境のルートURLに移動しても、以前と同様に既定の **Dynamics 365 – カスタム** アプリケーションが表示されます。 これは、統合インターフェース アプリケーションのテストおよび作業をしている状態で、既存の旧式のWebクライアント アプリケーションの運用を継続している場合に発生する可能性があります。  

## <a name="compare-your-new-app-to-the-default-dynamics-365-app"></a>新しいアプリと既定の Dynamics 365 アプリを比較する  
ここまでの手順で、アプリケーションを起動する準備ができました。 新しい統合インターフェース アプリ と Dynamics 365 カスタム アプリの比較をすることができます。両者とも同じ環境にあるため、同一のデータ、ユーザーロール、ビジネスルール、ワークフロー、プラグインなどを使用して比較することができます。 これにより、主要な基礎部分がすべて存在していることを組織に認識させ、それと同時に新しい統合インターフェイスの機能強化について模索をすることができます。  

> [!TIP]
> 一つのモニターに複数のアプリを並べて表示したい場合は、Windows キーと左矢印キー (または右矢印キー) を同時に押して、同じモニター上でブラウザー 画面を分割することができます。 

> [!NOTE]
> ナビゲーションの変更やボタンとアクションのリボンの詳細なカスタマイズなど、既定のサイトマップで引き続きカスタマイズを行う場合は、別のモデル駆動型アプリを作成してこのプロセスを繰り返すか、モデル駆動型アプリに関連する新しいサイトマップで同じカスタマイズを実行する必要があります。  

## <a name="validate-your-new-app"></a>アプリの検証をする  
統合インターフェイスを表示するアプリケーションでは、アプリケーション、プロセス、およびカスタマイズの検証を開始して、移行がどのように表示されるかを特定することができます。 すべてのテストケースを実施することを推奨しますが、最も重要なテストケースから始めたることも、論理的な設計パターンにまとめてテストをすることも可能です。 統合インターフェイスは応答性の高い設計がなされているため、常に画面解像度が異なる複数のデバイスでテストをすることを推奨します。 アプリケーションのテストを進めていく中で、行ったカスタマイズが統合インターフェイスと互換性があること、および再設計が必要な機能や不足している機能について認識することができます。  

> [!IMPORTANT]
> Common Data Service および Dynamics 365 for Customer Engagement アプリケーションの現在のバージョンには、いくつかの非推奨な機能が含まれています。 使用しているアプリケーションで非推奨の機能を確認し、必要に応じて新しい機能に置き換える必要があります。 詳細については次を確認してください: [ Dynamics 365 Customer Engagementで行われる重要な変更(非推奨)](/dynamics365/get-started/whats-new/customer-engagement/important-changes-coming)

> [!TIP]
> PowerApps のチェッカー ツールは、ソリューションのコンポーネントの品質チェックをサポートします。  詳細については次を確認してください: [ソリューション チェッカーをを使用して、PowerApps のモデル駆動型アプリケーションを検証する](../common-data-service/use-powerapps-checker.md)

## <a name="next-steps"></a>次のステップ
実装担当チームまたはパートナーは、調査結果に基づいてアプリケーションを統合インターフェイスに移行にあたって必要な作業量を見積もり、潜在的なユーザビリティの向上を発見することができます。 統合インターフェイスでは複数の新機能を利用できるため、アプリケーションを利用するユーザーの価値を高めることができます。 

統合インターフェイスへの移行は、最新のユーザーインターフェイスを作成、既存のプロセスを再確認、およびそのプロセスの有効性、あるいは改善が必要であることを確認するには最良の機会となります。 さらに、アプリケーションがビジネスの要件を反映しているかどうか、既存のアプリをさまざまなチームやロールの複数のアプリに分散できるかどうかを検討するのにも適しています。
詳細については次を確認してください: [アプリ デザイナーを使用してモデル駆動型アプリを設計する](design-custom-business-apps-using-app-designer.md) 

### <a name="see-also"></a>関連項目
<!-- Unified Interface transition community (link tbd) <br />  -->
[統合インターフェイスの活用プレイブック](unified-interface-playbook.md) <br />
[ユーザエクスペリエンスと統合インターフェイスへの移行](approaching-unified-interface.md) <br />
[Unified Interface について](/dynamics365/customer-engagement/admin/about-unified-interface) <br />
[PowerApps におけるモデル駆動型アプリとは](model-driven-app-overview.md) <br />
[アプリを統一インターフェイスに更新する](/dynamics365/customer-engagement/admin/update-apps-to-unified-interface) <br />
[モデル駆動型アプリの対話型エクスペリエンス ダッシュボードの構成](configure-interactive-experience-dashboards.md) <br />
[モデル駆動型アプリのデータのビジュアル化のためのカスタム コントロールの使用](use-custom-controls-data-visualizations.md) <br />
[PowerApps component framework の概要](/powerapps/developer/component-framework/overview) <br />
[全ユーザー向けの統合インターフェイス](/power-platform-release-plan/2019wave2/microsoft-powerapps/unified-interface-app-everybody)