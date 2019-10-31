---
title: Dynamics 365 アプリで Power BI を使用 | MicrosoftDocs
ms.custom: null
ms.date: 12/07/2018
ms.reviewer: null
ms.service: crm-online
ms.suite: null
ms.tgt_pltfrm: null
ms.topic: article
applies_to:
  - Dynamics 365 for Customer Engagement  (online)
  - Dynamics 365 for Customer Engagement  Version 9.x
ms.assetid: 48997010-a47c-4e16-b7d2-f55d7a52ba19
caps.latest.revision: 36
author: Mattp123
ms.author: matp
manager: kvivek
search.audienceType:
  - admin
search.app:
  - D365CE
  - Powerplatform
---
# <a name="use-power-bi"></a>Power BI の使用

Power BI クラウド サービスは、Common Data Service アプリと連係して、セルフサービス型の分析ソリューションを提供します。 Power BI は、表示されるアプリのデータを最新の状態に自動的に更新します。 ユーザーは、Power BI Desktop または Microsoft Excel では、レポートの作成に Power Query を、モデル駆動型アプリのダッシュボードの共有とデータの更新に Power BI を使用して、強力な新しい方法でアプリのデータを操作することができます。  
  
<a name="PowerBIGetstarted"></a>   
## <a name="get-started-using-power-bi-with-dynamics-365-for-customer-engagement-apps-online"></a>Power BI と Dynamics 365 for Customer Engagement アプリ (オンライン) の使い方の基本  
 Power BI のための Dynamics 365 アプリのコンテンツ パックを使用すると、営業、サービス、マーケティング データに簡単にアクセスして分析することができます。  
  
 コンテンツ パックを使用して Power BI ダッシュボードを作成するには、次の手順に従います。  
  
1. まだ完了していない場合は、[Power BI に登録します](http://powerbi.com/)。  
  
2. Power BI にサインインした後、**データセット**領域で**データを取得**を選択し、**サービス**の下にある**取得**を選択し、次のコンテンツ パックから選択します。  
  
   - **Dynamics 365 用営業分析**  
  
   - **Dynamics 365 用顧客分析**  
  
   - **Microsoft Dynamics 365 - Social Engagement**  
  
3. Sales Analytics および Service Analytics のコンテンツ パックについては、*<https://OrganizationName.crm.dynamics.com>* などのインスタンスの URL を入力します。ここで、*OrganizationName* は インスタンスの組織名です。**次へ** を選択します。  
  
   > [!NOTE]
   >  データ センターが北アメリカ外に位置する場合 crm.dynamics.com のドメイン名は crm2.dynamics.com、crm3.dynamics.com、crm4.dynamics.com などのように異なる場合があります。ドメイン名を見つけるには、アプリの Web アプリで **設定** > **カスタマイズ** > **開発者リソース** の順に移動します。 一覧表示された URL は正しいドメイン名を表示します。  
  
    マーケティング コンテンツ パックについては、URL を *<https://OrganizationName.marketing.dynamics.com/analytics>* として入力し、ここで *OrganizationName* は Dynamics 365 のインスタンスの組織名で、**次へ** を選択します  
  
4. **認証方法**で **oAuth2** を選択します。  
  
5. インスタンス データがインポートされ、複数のビジュアル化が利用できるようになります。  
  
> [!TIP]
>  選択したコンテンツ パックが Web ブラウザーで開けない場合、Power BI ワークプレースの左のウィンドウの**ダッシュボード**の下にあるコンテンツ パックをクリックします。  
  
### <a name="content-packs-available-for-download"></a>ダウンロードできるコンテンツ パックです。  
 Dynamics 365 コンテンツ パックは、アプリの既定の標準のエンティティをサポートします。 ただし、.PBIX ファイルをダウンロードし、Power BI Desktop を使用することで、次のコンテンツをカスタマイズできます。コンテンツ パックをカスタマイズしてから、それを Power BI サービスにアップロードします。  
  
- [Dynamics CRM Online セールス マネージャ .PBIX をダウンロードする](http://download.microsoft.com/download/9/2/B/92BCBDCE-CE01-4BC9-A306-2A92653B683E/Sales%20Manager.pbix)  
  
- [Dynamics 365 for Customer Engagement アプリ (オンライン) の Service Manager .PBIX のダウンロード](http://download.microsoft.com/download/9/2/B/92BCBDCE-CE01-4BC9-A306-2A92653B683E/Customer%20Service%20Manager.pbix)  
  
  Connected Field Service の Power BI レポート テンプレートによって、ユーザーは接続されているデバイスの最新の状況を表示する Power BI レポートの発行が可能になります。  
  
- [Connected Field Service for Dynamics 365 for Customer Engagement 用の Power BI レポート テンプレートのダウンロード](http://download.microsoft.com/download/E/B/5/EB5ED97A-A36A-4CAE-8C04-333A1E463B4F/PowerBI%20Report%20Template%20for%20Connected%20Field%20Service%20for%20Microsoft%20Dynamics%20365.pbix)  
  
 コンテンツ パックのカスタマイズ方法に関する詳細は、[Customize Dynamics 365 for Customer Engagement アプリの Power BI コンテンツ パック を参照してください](customize-power-bi-content-packs.md)。 
  
<a name="BPI_embed"></a>   
## <a name="embed-power-bi-visualizations-on-personal-dashboards"></a>個人のダッシュボードに Power BI のビジュアル化を埋め込む  
 ユーザーが個人のダッシュボードに Power BI のビジュアル化を埋め込む前に、組織全体の設定を有効にする必要があります。  
  
> [!NOTE]
>  既定では Power BI のビジュアル化の埋め込みは無効になっており、ユーザーがタイルを個人のダッシュボードに埋め込むことできるようになるには、その前に有効にする必要があります。  
  
### <a name="enable-power-bi-visualizations-in-the-organization"></a>組織における Power BI のビジュアル化を有効にする  
  
1. システム管理者セキュリティ ロールを持つユーザーとして Dynamics 365 にサインインします。  
  
2. **設定** > **管理** > **システムの設定**の順に移動します。  
  
3. **Power BIのビジュアル化の埋め込みを許可**オプションの**レポート**タブで、有効にするには**はい**を、無効にするには**いいえ**を選択します。  
  
4. **OK** を選びます。  
  
個人のダッシュボードに Power BI タイルを追加する方法に関する詳細は、[個人のダッシュボードに Power BI タイルを埋め込む](/dynamics365/customer-engagement/on-premises/basics/add-edit-power-bi-visualizations-dashboard.md#embed--power-bi-tiles-on-your-personal-dashboard)を参照してください。  
  
Power BI ダッシュボードを個人のダッシュボードに追加する方法の詳細については、[個人用ダッシュボードに Power BI ダッシュボードを追加する](/dynamics365/customer-engagement/on-premises/basics/add-edit-power-bi-visualizations-dashboard.md)を参照してください。  
  
<a name="CRMOnline_PBIDesktop"></a>   
## <a name="use-power-bi-desktop-to-connect-directly-to-your-instance"></a>Power BI Desktop を使用して、インスタンスに直接に接続します。  
 Power BI Desktop を使用してインスタンスに接続すると、カスタム レポートおよびダッシュボードを作成し、Power BI サービスで使用することができます。  
  
### <a name="requirements"></a>要件  
  
- Power BI サービス登録  
  
- Power BI Desktop  
  
- Dynamics 365 インスタンス  
  
### <a name="connect"></a>接続  
  
1. Power BI Desktopを起動します。  
  
2. [ホーム] タブで**データを取得**を選択し、**その他**を選択します。  
  
3. [データを取得] の一覧で、**Dynamics 365 Online** をクリックします。  
  
4. Dynamics 365 の OData エンドポイントの URL を入力します。 この URL と同じ形式にする必要があり、*OrganizationName* は組織名です。**v8.1** がバージョンです。 **OK** を選びます。  
  
    https://<em>OrganizationName</em>.api.crm.dynamics.com/api/data/*v8.1*  
  
> [!IMPORTANT]
> さまざまなエンドポイント バージョンの詳細については、[Web API URL とバージョン]( https://msdn.microsoft.com/library/gg334391.aspx#bkmk_url_and_versions)を参照してください。
 
> [!TIP]
>  OData エンドポイント URL を検索できます。 **設定** > **カスタマイズ** > **開発者リソース**の順に移動し、URL を **Instance Web API** で探します。  
  
5. [OData フィードへのアクセス] ダイアログで、**組織のアカウント**を選択し、**接続**を選択します。  
  
   > [!NOTE]
   >  インスタンスにサインインしていない場合は、[OData フィードへのアクセス] ダイアログで **サインイン** を選択してから、[接続] を選択します。  
  
6. 組織データベース エンティティのテーブルが Power BI Desktop のナビゲータ ウィンドウに表示されます。 既定とユーザー定義エンティティの両方を選択できます。 Power BI Desktop でのレポート作成に関する詳細は、[Power BI サポート: Power BI Desktop のレポート ビュー](https://powerbi.microsoft.com/documentation/powerbi-desktop-report-view/) を参照してください。  
  
   ![エンティティ テーブルを選択](media/pbi-select-entity-table.PNG "エンティティ テーブルを選択")  
  
   > [!TIP]
   >  同様の手順で Excel Power Query を使用して Dynamics 365 に接続できます。Excel の **Power Query** タブで、**その他のデータ ソース** を選択します。  
  

