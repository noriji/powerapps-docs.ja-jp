---
title: Dynamics 365 Power BI コンテンツ パックのカスタマイズ | MicrosoftDocs
description: 使用可能な Power BI コンテンツ パックを修正して Dynamics 365 データで使用する方法を学習します。
keywords: PBI
ms.date: 09/30/2017
ms.service: crm-online
ms.custom: null
ms.topic: article
applies_to:
  - Dynamics 365 for Customer Engagement (online)
ms.assetid: 424d7f29-de44-4ce0-94f1-be8777ad6485
author: Mattp123
ms.author: matp
manager: amyla
ms.reviewer: null
ms.suite: null
ms.tgt_pltfrm: null
caps.latest.revision: 16
topic-status: Drafting
tags: null
search.audienceType:
  - customizer
search.app:
  - D365CE
---

# <a name="customize-dynamics-365-apps-power-bi-content-packs"></a>Dynamics 365 アプリ Power BI コンテンツ パックのカスタマイズ

Power BI は業務データをビジュアル化するのに使用するサービスとツールの総合コレクションです。  コンテンツ パックは、標準データ モデルに基づいて Power BI を使用して、Dynamics 365 Sales、Service、Marketing アプリ データを簡単にビジュアル化および分析するために用意されています。 コンテンツ パックは、多数の営業、サービス、またはマーケティング レポート シナリオに役立つ一連のエンティティとフィールドで構築されています。  
  
 Dynamics 365 アプリはカスタム フィールドで拡張されます。 これらのカスタム フィールドは自動的に Power BI モデルには表示されません。 このトピックでは、Power BI モデルのカスタム フィールドを含むコンテンツ パックに含まれているレポートを編集または拡張できる様々な方法について説明します。  
    
<a name="PBI_edit_first"></a>   
## <a name="do-this-before-you-customize-a-content-pack-for-power-bi-reports"></a>Power BI レポートのコンテンツ パックをカスタマイズする前にこれを実行する  
 
コンテンツ パックをカスタマイズする前に、以下の情報を確認し、必要に応じて各手順を実行します。  
  
### <a name="meet-the-requirements"></a>要件を満たす  
  
- [Power BI サービスの登録](http://powerbi.com/)  
  
- [Power BI Desktop](https://powerbi.microsoft.com/desktop) Power BI レポートを編集するアプリケーション  
  
- カスタマイズするコンテンツ パックの PBIX ファイル。  
  
  -   [Dynamics CRM Online Sales Manager PBIX をダウンロード](http://download.microsoft.com/download/9/2/B/92BCBDCE-CE01-4BC9-A306-2A92653B683E/Sales%20Manager.pbix)  
  
  -   [Dynamics CRM Online Service Manager PBIX をダウンロード](http://download.microsoft.com/download/9/2/B/92BCBDCE-CE01-4BC9-A306-2A92653B683E/Customer%20Service%20Manager.pbix)  
  
  -   [Microsoft Dynamics 365 Process Analyzer PBIX をダウンロード](http://download.microsoft.com/download/9/2/B/92BCBDCE-CE01-4BC9-A306-2A92653B683E/Process%20Analyzer%20-1.34b.pbix)  
  
  Dynamics 365 コンテンツ パックは、現在、英語 (米国) でしかサポートされていません。  
  
### <a name="prepare-a-content-pack-for-customization"></a>コンテンツ パックのカスタマイズの作成  
  
> [!IMPORTANT]
>  OData フィードをインスタンスに接続するには、コンテンツ パックをカスタマイズする前に以下に説明されている手順に従う必要があります。  
> 
> 現在、 Power BI サービスは Dynamics 365 バージョン 9.0 OData エンドポイントと互換性がありません。 Power BI サービスでバージョン 9.0 OData エンドポイントを使用しようとすると、エラー メッセージ「フィードのメタデータ ドキュメントが無効のようです」が表示されます。 この非互換性を回避するには、Dynamics 365 バージョン 8.2 OData エンドポイントを使用します。エンドポイントの異なるバージョンの詳細については、 [HTTP 要求の作成とエラーの処理](../../developer/common-data-service/webapi/compose-http-requests-handle-errors.md) を参照してください。
  
1. Power BI Desktopを起動します。  
  
    **ファイル** > **オープン** を選択し、Sales Manager.bpix などのコンテンツ パックを開き、 **オープン** を選択します。  
  
    コンテンツ パック内のレポートの複数ページは、Power BI Desktop で読み込まれおよび表示されます。  
  
2. Power BI Desktop リボンで、 **クエリの編集** を選択します。  
  
3. クエリ エディターの左側ナビゲーション ウィンドウにある **クエリ** で、 **CRMServiceUrl** クエリを選択し、リボンで **詳細エディター** を選択します。 ソース定義で、 **base.crm.dynamics.com** をアプリ インスタンス URLに置き換えます。 たとえば、組織名が *Contoso* である場合、URL は次のようになります:  
  
    Source = "https://*contoso*.crm.dynamics.com/api/data/v8.0/"  
  
4. **完了** を選択し、クエリ エディターで **閉じる & 適用** を選択します。  
  
5. OData フィードへのアクセス ダイアログが表示され、 **組織のアカウント** を選択し、 **サインイン** を選択します。  
  
   ![[OData フィードへのアクセス] ダイアログ](media/pbi-odata-signin.PNG "[OData フィードへのアクセス] ダイアログ")  
  
6. サインイン ページが表示されたら、 インスタンスに認証するための資格情報を入力します。  
  
7. OData フィードへのアクセス ダイアログで、 **接続** を選択します。  
  
    コンテンツ パックのクエリが更新されます。 この処理には数分かかる可能性があります。  
  
<a name="PBI_edit_report"></a>   
## <a name="customize-adynamics-365-content-pack"></a>Dynamics 365 コンテンツ パック のカスタマイズ  
 [レポートに表示される日付の形式を変更](#PBI_edit_date)  
  
 [取引先企業以外の任意のエンティティのレポートにカスタム フィールドを追加する](#PBI_edit_field)  
  
 [取引先企業エンティティのレポートにカスタム フィールドを追加する](#PBI_field_Account)  
  
 [オプション セット フィールドをレポートに追加する](#PBI_optionset_field)  
  
 [クエリする行数を増やす](#BPI_increaserows)  
  
<a name="PBI_edit_date"></a>   
### <a name="convert-a-datetime-field-to-a-date-field-for-reporting"></a>レポート用の日時フィールドを日付フィールドに変換する  
 Dynamics 365 アプリでは、一部の日付が日付/時刻/時間帯の形式で保存されており、レポートにデータを収集する上で優先形式ではない可能性があります。 エンティティのフィールドでは、レポートに表示される日付を変換できます。 たとえば、[営業案件の作成日] フィールドは、作成された営業案件を日によってレポートするために、日付に変換できます。  
  
1. Power BI Desktop で、 **クエリの編集** を選択します。  
  
2. クエリ エディターの左側ナビゲーション ウィンドウにある **クエリ** で、 **営業案件** エンティティ クエリの **予測クローズ日** などの変更する日付フィールドがあるクエリを選択します。  
  
3. *推定クローズ日*などの列見出しを右クリックし、**種類の変更**をポイントした後に、**日付**などの別のデータの種類を選択します。  
  
   ![Power BI Desktop でデータ型を変更する](media/pbi-changeformat.PNG "Power BI Desktop でデータ型を変更する")  
  
4. **閉じる & 適用** を選択して、クエリ エディターを閉じます。  
  
5. Power BI のメインページにて、 **変更の適用** を選択して、関連するレポートを更新します。  
  
<a name="PBI_edit_field"></a>   
### <a name="add-a-custom-field-to-a-report"></a>カスタム フィールドをレポートに追加する  
 次の手順では、日付、文字列、または数字であるカスタム フィールドを、取引先企業エンティティを除く、すべてのエンティティのレポートに追加する方法を説明します。  
  
> [!NOTE]
>  取引先企業エンティティにフィールドを追加するには、[取引先企業エンティティのレポートにカスタム フィールドを追加する](#PBI_field_Account) を参照してください。 オプション セット型のフィールドを追加するには、[オプション セット フィールドをレポートに追加する](#PBI_optionset_field) を参照してください。  
  
1. Power BI Desktop で、 **クエリの編集** を選択します。  
  
2. クエリ エディターの左側ナビゲーション ウィンドウにある **クエリ** で、 **営業案件** エンティティ クエリなど、レポート上で使用できるようにするカスタム フィールドがあるクエリを選択します。  
  
3. 右側ウィンドウの **APPLIED STEPS** で、 **その他の列の削除** の横にある ![設定ボタン](media/mp-ua-r16-settings.png "設定ボタン") 設定ボタン を選択します。  
  
4. **列の選択** リストは、カスタム フィールドを含むエンティティのすべてのフィールドを表示します。 必要なカスタム フィールドを選択し、 **OK** を選択します。  
  
    エンティティのクエリは更新され、列は、選択したカスタム フィールドのエンティティ テーブルに追加されます。  
  
5. 右側のウィンドウの **APPLIED STEPS** で、 **Lang – 列の名前を変更する** を選択し、 **詳細エディター** を選択した後に、フィールドのマッピングをエンティティ クエリに追加します。 たとえば、営業案件エンティティのカスタム フィールド名が *int_forecast* であり、表示名が *予測* である場合は、エンティティは次のように表示されます。  
  
   ```  
   {"int_forecast","Forecast"}  
   ```  
  
   ![レポート上のカスタム フィールドにマッピングを追加](media/pbi-addfieldmapping.png "レポート上のカスタム フィールドにマッピングを追加")  
  
6. フィールド マッピングを追加した後、[詳細エディター] の下に構文エラーが表示されていないことを確認します。 また、大文字と小文字の区別を含め、フィールド名が列見出しに表示されている通りに正確に表示されていることを確認します。 構文エラーまたテーブル エラーが検出されないときは、 **完了** を選択します。  
  
7. クエリ エディターで、**閉じる & 適用**をクリックします。  
  
    カスタム フィールドは、右側のウィンドウのエンティティの**フィールド**で表示され、新規または既存のレコードに追加できます。  
  
<a name="PBI_field_Account"></a>   
## <a name="add-a-custom-field-to-a-report-for-the-account-entity"></a>取引先企業エンティティのレポートにカスタム フィールドを追加する  
 取引先企業クエリは Fetch XML を使用してクエリをフィルター処理するため、フィールドを追加するステップは、OData を使用する他のエンティティ クエリとは異なります。 カスタム フィールドを OData クエリ エンティティに追加するには、[カスタム フィールドをレポートに追加する](#PBI_edit_field) を参照してください。  
  
1. エンコードされた Fetch XML クエリを、取引先企業エンティティにコピーします。 これを行うには、次の手順を実行します。  
  
   1.  Power BI Desktop で、 **クエリの編集** を選択します。  
  
   2.  クエリ エディターの左側ナビゲーション ウィンドウにある **クエリ** で、 **取引先企業** エンティティ クエリを選択し、リボンで **詳細エディター** を選択します。  
  
   3.  %3 Cfetch で始まる最初の行から fetch%3E で終わるエンコードされた FetchXML 全体をコピーします。  
  
   4.  コピーするエンコード済み FetchXML はこのような内容です:  
  
        %3Cfetch%20version%3D%221.0%22%20output-format%3D%22xml-platform%22%20mapping%3D%22logical%22%20distinct%3D%22true%22%3E%3Centity%20name%3D%22account%22%3E%3Cattribute%20name%3D%22territorycode%22%20%2F%3E%3Cattribute%20name%3D%22customersizecode%22%20%2F%3E%3Cattribute%20name%3D%22owningbusinessunit%22%20%2F%3E%3Cattribute%20name%3D%22ownerid%22%20%2F%3E%3Cattribute%20name%3D%22originatingleadid%22%20%2F%3E%3Cattribute%20name%3D%22revenue%22%20%2F%3E%3Cattribute%20name%3D%22sic%22%20%2F%3E%3Cattribute%20name%3D%22marketcap%22%20%2F%3E%20%3Cattribute%20name%3D%22parentaccountid%22%20%2F%3E%3Cattribute%20name%3D%22owninguser%22%20%2F%3E%3Cattribute%20name%3D%22accountcategorycode%22%20%2F%3E%3Cattribute%20name%3D%22marketcap_base%22%20%2F%3E%3Cattribute%20name%3D%22customertypecode%22%20%2F%3E%3Cattribute%20name%3D%22address1_postalcode%22%20%2F%3E%3Cattribute%20name%3D%22numberofemployees%22%20%2F%3E%3Cattribute%20name%3D%22accountratingcode%22%20%2F%3E%3Cattribute%20name%3D%22address1_longitude%22%20%2F%3E%3Cattribute%20name%3D%22revenue_base%22%20%2F%3E%3Cattribute%20name%3D%22createdon%22%20%2F%3E%3Cattribute%20name%3D%22name%22%20%2F%3E%3Cattribute%20name%3D%22address1_stateorprovince%22%20%2F%3E%3Cattribute%20name%3D%22territoryid%22%20%2F%3E%3Cattribute%20name%3D%22accountclassificationcode%22%20%2F%3E%3Cattribute%20name%3D%22businesstypecode%22%20%2F%3E%3Cattribute%20name%3D%22address1_country%22%20%2F%3E%3Cattribute%20name%3D%22accountid%22%20%2F%3E%3Cattribute%20name%3D%22address1_latitude%22%20%2F%3E%3Cattribute%20name%3D%22modifiedon%22%20%2F%3E%3Cattribute%20name%3D%22industrycode%22%20%2F%3E%3Clink-entity%20name%3D%22opportunity%22%20from%3D%22parentaccountid%22%20to%3D%22accountid%22%20alias%3D%22ab%22%3E%3Cfilter%20type%3D%22and%22%3E%3Ccondition%20attribute%3D%22opportunityid%22%20operator%3D%22not-null%22%20%2F%3E%3Ccondition%20attribute%3D%22modifiedon%22%20operator%3D%22last-x-days%22%20value%3D%22365%22%20%2F%3E%3C%2Ffilter%3E%3C%2Flink-entity%3E%3C%2Fentity%3E%3C%2Ffetch%3E  
  
2. エンコードされた FetchXML をデコードします。 有効なエンコードされた FetchXML である必要があり、いったんデコードされるとこれと類似する必要があります:  
  
    \<fetch version="1.0" output-format="xml-platform" mapping="logical" distinct="true"> \<entity name="account"> \<attribute name="territorycode" /> \<attribute name="customersizecode" /> \<attribute name="owningbusinessunit" /> \<attribute name="ownerid" /> \<attribute name="originatingleadid" /> \<attribute name="revenue" /> \<attribute name="sic" /> \<attribute name="marketcap" />  \<attribute name="parentaccountid" /> \<attribute name="owninguser" /> \<attribute name="accountcategorycode" /> \<attribute name="marketcap_base" /> \<attribute name="customertypecode" /> \<attribute name="address1_postalcode" /> \<attribute name="numberofemployees" /> \<attribute name="accountratingcode" /> \<attribute name="address1_longitude" /> \<attribute name="revenue_base" /> \<attribute name="createdon" /> \<attribute name="name" /> \<attribute name="address1_stateorprovince" /> \<attribute name="territoryid" /> \<attribute name="accountclassificationcode" /> \<attribute name="businesstypecode" /> \<attribute name="address1_country" /> \<attribute name="accountid" /> \<attribute name="address1_latitude" /> \<attribute name="modifiedon" /> \<attribute name="industrycode" /> \<link-entity name="opportunity" from="parentaccountid" to="accountid" alias="ab"> \<filter type="and"> \<condition attribute="opportunityid" operator="not-null" /> \<condition attribute="modifiedon" operator="last-x-days" value="365" /> \</filter> \</link-entity> \</entity> \</fetch>  
  
   > [!TIP]
   >  多くの URL エンコーダーとデコーダー ツールは Web で入手可能です。  
  
3. Fetch XML では、カスタム エンティティを \<entity> ノード間の属性ノードとして追加します。 たとえば、*customclassificationcode* という名前のカスタム フィールドを追加するには、**industrycode** などの別の属性ノードの後にノードを追加します。  
  
   ```  
  
   <attribute name="industrycode" />  
   <attribute name=" customclassificationcode "/>  
   <link-entity name="opportunity" from="parentaccountid" to="accountid" alias="ab">  
   ```  
  
4. 更新された Fetch XML を URL エンコードします。 新しいカスタム属性を含む Fetch XML は、エンコードする必要があり、コンテント パックで用意されている既存の OData フィード クエリを置き換えるのに使用される必要があります。 これを実行するには、更新された FetchXML をクリップボードにコピーし、URL エンコーダーに貼り付けます。  
  
5. エンコードされた FetchXML URL を OData フィードに貼り付けます。 これを実行するには、既存のエンコード済み FetchXML を置き換える **Query=[fetchXml=** テキストの後の引用符の間に、エンコードされた URL を貼り付け、 **完了** を選択します。  
  
    下記のスクリーン ショットは、左端の引用語句がある場所を示しています。  
  
   ![エンコードされた URL を OData フィードに貼り付け](media/pbi-acct-encoded-url.PNG "エンコードされた URL を OData フィードに貼り付け")  
  
6. 右側ウィンドウの **APPLIED STEPS** で、 **その他の列の削除** の横にある ![設定ボタン](media/mp-ua-r16-settings.png "設定ボタン") 設定ボタン を選択します。  
  
7. [列の選択] リストは、カスタム フィールドを含むエンティティのすべてのフィールドを表示します。 先ほど Fetch XML クエリに追加した *customclassificationcode* などのカスタム フィールドを選択し、 **OK** を選択します。  
  
   > [!NOTE]
   >  [列の選択] で選択するフィールド名と FetchXML クエリに追加するフィールド名は一致する必要があります。  
  
    エンティティのクエリは更新され、列は、選択したカスタム フィールドのエンティティ テーブルに追加されます。  
  
8. クエリ エディターで、 **閉じる & 適用** を選択します。  
  
    カスタム フィールドは、右側のウィンドウのエンティティの**フィールド**で表示され、新規または既存のレコードに追加できます。  
  
<a name="PBI_optionset_field"></a>   
## <a name="add-a-custom-option-set-field-to-a-report"></a>カスタム オプション セット フィールドをレポートに追加する  
 オプション セット フィールドは複数の値から選択することができます。 標準オプション セット フィールドの例として、営業案件における [評価] および [Sales Stage] フィールドがあります。 次の値とラベルが含まれている営業案件のメイン フォームに、カスタム オプション セット フィールドがあるとします。  
  
 ![カスタム オプション セットの例](media/pbi-custom-option-set-example.PNG "カスタム オプション セットの例")  
  
 レポートにカスタム オプション セット フィールドを追加するには、これらの手順に従います。  
  
1. カスタム フィールドの列を追加します。  
  
   -   クエリ エディターの左側ナビゲーション ウィンドウにある **クエリ** では、 *営業案件* エンティティなどの関連するカスタム オプション セットを持つエンティティを選択します。  
  
   -   右側ウィンドウの **APPLIED STEPS** で、 **その他の列の削除** の横にある ![設定ボタン](media/mp-ua-r16-settings.png "設定ボタン") 設定ボタン を選択します。  
  
   -   [列の選択] リストは、カスタム フィールドを含むエンティティのすべてのフィールドを表示します。 *new_customoptionset* などのカスタム フィールドを選択し、次に、 **OK** を選択します。  
  
   -   **保存** を選択し、確認メッセージが表示されたら、 **適用** を選択します。  
  
        カスタム フィールドの列は、エンティティ テーブルに表示されます。  
  
2. オプション セット クエリを作成します。  
  
   1.  Power BI Desktop で、 **クエリの編集** を選択します。  
  
   2.  クエリ エディターの左側のナビゲーション ウィンドウにある **クエリ** で、レポートに追加するオプション セットと最も類似しているオプション セット フィールドを持つ **表の作成** グループのクエリを選択します。 この例では、**SalesStageOptionSet** クエリには 4 つのオプションがあるため、良い選択です。  
  
   3.  **詳細エディター** を選択します。  
  
        オプション セットのクエリが表示されます。  
  
   ![オプション セット クエリの作成](media/pbi-makeoptionsetquery.png "オプション セット クエリの作成")  
  
   4.  クエリ全体をクリップボードにコピーします。 後に参照するためにメモ帳などのテキスト エディターに貼り付けることができます。  
  
   5.  クエリ エディターで、 **表の作成** グループを右クリックし、 **新しいクエリ** を選択し、次に **空白のクエリ** を選択します。  
  
   6.  右側のウィンドウの **名前** で、 *CustomOptionSet* などの名前を入力し、Enter キーを押します。  
  
   7.  **詳細エディター** を選択します。  
  
   8.  詳細エディターで先ほどコピーしたクエリを貼り付けます。  
  
   9. 既存値とオプションをユーザー定義値とオプションに置き換えます。 この例では、これを変更します。  
  
       ```  
       let  
           Source = #table({"Value","Option"},{{0,"Qualify"},{1,"Develop"},{2,"Propose"},{3,"Close"}})  
       in  
           Source  
  
       ```  
  
        結果として、次を実現します。  
  
       ```  
       let  
           Source = #table({"Value","Option"},{{0,"A"},{1,"B"},{2,"C"},{3,"D"},{4,"E"}})  
       in  
           Source  
  
       ```  
  
   10. 構文エラーがないことを確認し、 **完了** を選択し、詳細エディターを閉じます。 値とオプションの表が [クエリ エディター] に表示されます。  
  
   ![新しいオプション セット クエリ](media/pbi-optionsetquerycreated.png "新しいオプション セット クエリ")  
  
   11. **保存** を選択し、確認メッセージが表示されたら、 **適用** を選択します。  
  
3. エンティティおよびカスタム オプション セットの表に対して、統合クエリを挿入します。  
  
   1.  クエリ エディターの左側のウィンドウにある **エンティティ** で、カスタム オプション セットを含むエンティティを選択します。 この例では、**営業案件**エンティティ クエリが選択されています。  
  
   2.  リボンで **クエリの統合** を選択し、ステップを挿入するように要求されたら、 **挿入** を選択します。  
  
   3.  統合ダイアログで、 *new_optionset* などのカスタム オプション セットの列見出しを選択します。 ドロップダウン リストで、先ほど作成したオプション セット クエリから該当するものを選択します。  オプション セットのテーブルが表示されたら、選択するために **値** 列見出しを選択します。  
  
   ![テーブル マージの選択項目](media/pbi-merge-tables.png "テーブル マージの選択項目")  
  
   4.  バインディングの種類を **左外部 (最初からすべて、2 番目からマッチング)** のままにし、 **OK** を選択します。  
  
       > [!TIP]
       >  統合クエリの名前を変更します。 **APPLIED STEPS** で、作成された統合クエリを右クリックし、 **名前の変更** を選択し、 *Merge CustomOptionSet* などのわかりやすい名前を入力します。  
  
4. ラベルのみが表示されるように列を定義します。  
  
   1.  クエリ エディターの左側のウィンドウにある エンティティ で、カスタム オプション セットを含むエンティティを選択します。 この例では、**営業案件**エンティティ クエリが選択されています。  
  
   2.  右側のウィンドウの **APPLIED STEPS** で、 **Expanded SalesStage** などの展開されたクエリの 1 つをクリックし、統合された列を明白にします。  
  
   3.  先ほど実行したクエリ統合の段階で作成された新しい列の列見出しを見つけ、選択します。  
  
   4.  **変換** タブで、 **展開** を選択します。  
  
   5.  [新しい列の展開] ダイアログで、値に対応している列をクリアします (ラベルのみを列に表示する必要があるため)。 **完了**を選択します。  
  
   ![ラベルを示す列を選択](media/pbi-expand-column.png "ラベルを示す列を選択")  
  
   6.  **保存** を選択し、確認メッセージが表示されたら、 **適用** を選択します。  
  
5. レポート作成のために列名を変更します。  
  
   1.  クエリ エディターの左側のウィンドウにある **エンティティ** で、カスタム オプション セットを含むエンティティを選択します。 この例では、**営業案件**エンティティ クエリが選択されています。  
  
   2.  **詳細エディター** を選択します。  
  
   3.  名前を変更した列品目を追加し、構文エラーがないか確認し、 **完了** を選択します。 この例では、先ほど作成したカスタム オプション セットの列名は、**NewColumn** であり、*カスタム オプション セット*に変更されました。  
  
   ![レポート内に表示する列の名前を変更](media/pbi-rename-column.png "レポート内に表示する列の名前を変更")  
  
   4.  **保存** を選択し、確認メッセージが表示されたら、 **適用** を選択します。  
  
6. **閉じる & 適用** を選択して、クエリ エディターを閉じます。  
  
    カスタム オプション セットを Power BI レポートの作成に使用できるようになりました。  
  
<a name="BPI_increaserows"></a>   
## <a name="increase-the-number-of-rows-queried"></a>クエリする行数を増やす  
 既定では、 コンテンツ パックのすべての Power BI エンティティ クエリは 100,000 行を超えることはできません。 クエリできる行数を増やすには、次の手順に従います。  
  
> [!IMPORTANT]
>  行数の制限を増やすことは、レポートの更新時間に多大な影響を及ぼす可能性があります。 また、Power BI サービスはクエリの実行に 30 分間の制限を設けています。 行数の制限を増やすときは注意してください。  
  
1. Power BI Desktop で、 **クエリの編集** を選択します。  
  
2. クエリ エディターの左側のナビゲーション ウィンドウにある **クエリ** で、 **潜在顧客** エンティティなど、行数の制限を増やすエンティティ クエリを選択します。  
  
3. 右側のウィンドウの **APPLIED STEPS** で、 **1 行目をキープ** を選択します。  
  
4. フィルターされた行数を増やします。 たとえば、150,000 まで増やすには、Table.FirstN を ("フィルターされた行番号"、100001) Table.FirstN ("フィルターされた行番号"、150000) に変更します。  
  
5. 右側のウィンドウの **APPLIED STEPS** で、 **行数の確認** を選択します。  
  
6. 手順の 1 つとして **>100,000** を見つけます。  
  
   ![行数の値を増やす](media/pbi-increaserowcount.png "行数の値を増やす")  
  
7. *150,000* などのさらに大きい値に増やします。  
  
8. クエリ エディターで、 **閉じる & 適用** を選択します。  
  
<a name="BPI_publish"></a>   
## <a name="publish-your-report-to-the-power-bi-service"></a>Power BI のサービスにレポートを公開します  
 組織内での共有を目的とした、ほとんどのデバイスからでもアクセス可能なレポートを公開します。  
  
1. Power BI Desktop メイン ページの **Home** タブ リボンで、 **公開** を選択します。  
  
2. Power BI のサービスへのサインインを求めるメッセージが表示された場合、 **サインイン** を選択します。  
  
3. 複数の対象先がある場合は、該当するものを選択し、 **公開** を選択します。  
  
### <a name="see-also"></a>関連項目  
 [Dynamics 365 Customer Engagement (on-premises) で Power BI を使用する](use-power-bi.md)
