---
title: ソリューション チェッカーを使用した PowerApps でのアプリの検証 | Microsoft Docs
description: ソリューションを検証するには、ソリューションのチェッカーを使用します。
author: Mattp123
manager: kvivek
ms.service: powerapps
ms.component: cds
ms.topic: article
ms.date: 07/09/2019
ms.author: matp
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="use-solution-checker-to-validate-your-model-driven-apps-in-powerapps"></a>ソリューション チェッカーを使用した PowerApps でのモバイル駆動型アプリの検証

複雑なビジネス要件を満たすため、モデル駆動型アプリの作成者はCommon Data Service プラットフォームをカスタマイズして拡張できるという非常に高度なソリューションを作成することになりがちです。 高度な実装により、パフォーマンス、安定性、信頼性の問題が生じるリスクが増加し、ユーザーの作業に悪影響を与える可能性があります。 これらの問題を解決する方法を特定して理解することは、複雑で時間がかかることがあります。 ソリューション チェッカー機能を使用すると、一連のベスト プラクティス ルールに対してソリューションで機能豊富なスタティック分析チェックを実行し、これらの問題となるパターンを識別できます。 チェックが完了すると、特定された問題、影響を受けるコンポーネントとコード、各問題を解決する方法が説明されたするドキュメントへのリンクが一覧になった詳細なレポートを受け取ります。

ソリューション チェッカーは、これらのソリューション コンポーネントを分析します: 
- Common Data Serviceプラグイン
- Common Data Serviceユーザー定義のワークフロー活動 
- Common Data Service Web リソース (HTML および JavaScript)
- SDK メッセージ手順などの Common Data Service 構成 

ソリューション チェッカーは、環境からエクスポートできるアンマネージド ソリューションを使用します。 

> [!NOTE]
> - このトピックでは、PowerApps メーカー ポータルのソリューション チェッカーを実行する方法を説明します。 サービスと直接やりとりしても使用できる PowerShell モジュールもご用意しています。 Microsoft.PowerApps.Checker.PowerShell モジュールは、オンプレミスおよびオンライン環境のサポート バージョンに関するマネージド ソリューションおよびアンマネージド ソリューションの分析用途でのみ使用でき、自動化またはサービスをお使いのビルドに統合してパイプラインを解放することができます。 詳細: [Microsoft.PowerApps.Checker.PowerShell の概要]( /powershell/powerapps/overview?view=pa-ps-latest#get-started-using-the-microsoftpowerappscheckerpowershell-module) 
> - ソリューション チェッカーでは、ECMAScript 6 (2015) 以降のバージョンを使用した JavaScript を含むソリューションを使用しません。 これらのバージョンのいずれかを使用した JavaScript が検出されると、Web リソースの JS001 構文は問題報告されます。

## <a name="enable-the-solution-checker"></a>ソリューション チェッカーを有効にする
すべての Common Data Service 環境では、既定でソリューションチェッカーが有効となっています。 **ソリューション チェッカー**のメニュー項目は、PowerApps の **ソリューション** 領域で非管理ソリューションを選択した場合に使用することができます。 **ソリューション チェッカー** メニューで、**実行** オプションが使用できない場合は、PowerApps のチェッカーソリューションをインストールすることで有効にすることができます。 これをインストールするには、次の手順を実行します。   

1. [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) にサインインし、ソリューション チェッカーを有効にする Common Data Service 環境を選択します。 
2. 左のナビゲーション ウィンドウで、**ソリューション** を選択します。
3. ツール バーで、**ソリューション チェッカー** を選択し、**インストール** を選択します。これにより、Microsoft AppSource ページが開きます。 ブラウザーでページがブロックされた場合、ポップアップ ウィンドウを許可する必要があります。 

   > [!div class="mx-imgBorder"]
   > ![ソリューション チェッカーのインストール](media/solution-checker-install.png "ソリューション チェッカーのインストール")

4. AppSource ページで **無料試用版** を選択します。 

5. 同意した場合、契約条件に同意し、PowerApps チェッカー ソリューションをインストールする環境を選択します。 
6. インストールが完了したら、PowerApps サイトの **ソリューション** リストを更新して、リューション チェッカーが使用可能であることを確認してください。  
7. ソリューションを確認するには、[ソリューション チェッカーを実行します](#run-the-solution-checker)。


<!-- ### Components created with the PowerApps checker
When you install the PowerApps checker these solution specific components are created. 
- Entities: The entities that are created are required to store the results of solution analysis and the status of analysis jobs in your environment.
   - Analysis Component
   - Analysis Job
   - Analysis Result
- System job: A system job is created so admins can remove solution analysis data from the environment. The job contains a configuration value, currently set to remove the solution analysis data after 60 days, which an administrator can override. 
- Security Roles: Two security roles, **Export Customizations**, and **Solution Checker** are created. These roles are required to export the solution for analysis, and storing the analysis results to the entities in your environment.
- User principle: The **PowerApps Advisor** user is created that allows the checker to authenticate with your Common Data Service environment and assign the two security roles, Export Customizations and Solution Checker. The PowerApps Advisor is an application user and does not consume a license.  -->

## <a name="run-the-solution-checker"></a>ソリューション チェッカーを実行する
環境に PowerApps チェッカーをインストールしたら、PowerApps の **ソリューション** 領域でアンマネージド ソリューションを選択すると **ソリューション チェッカー** メニュー項目が利用可能になります。 

1. [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) にサインインします。 
2. 左側のウィンドウで、**ソリューション**を選択します。 
3. 分析するアンマネージド ソリューションの横で、**...** を選択し、**ソリューション チェッカー**をポイントして**実行**を選択します。 

   > [!div class="mx-imgBorder"]
   > ![ソリューション チェッカー コマンドを実行する](media/solution-checker-run.png "ソリューション チェッカー コマンドを実行する")

4.  **ソリューション** ページの右上にあるステータス ウィンドウに、**ソリューション チェッカーの実行** が表示されます。 

    > [!div class="mx-imgBorder"]
    > ![ソリューション チェッカーのステータス](media/solution-checker-status.png "ソリューション チェッカーのステータス")
   
    以下に注意します。
    - ソリューション チェッカーが分析を完了するまで、数分間かかる場合があります。 
    
    - この間、**実行…**  状態と、**ソリューション** リストの **ソリューション チェック** 列に表示されます。 
    
    - チェックが完了したら、電子メール通知を受け取り、PowerApps サイトの **通知** 領域に通知が表示されます。  

5.  チェックが完了したら、[レポートを表示します](#review-the-solution-checker-report)。

## <a name="cancel-a-check"></a>チェックを取り消す

環境でソリューション チェックを送信すると、**ソリューション**ページの右上領域の状態ウィンドウでチェックを取り消すことができます。 

チェックを取り消すと、ソリューション チェックが実行を停止し、ソリューション チェック状態が以前の状態に戻ります。 

## <a name="solution-checker-states"></a>ソリューション チェッカーの状態
環境にソリューション チェッカーをインストールすると、**ソリューション チェック** 列が **ソリューション** リストで使用可能になります。 この列には、ソリューションのソリューション分析状態が表示されます。 

|都道府県  |説明  |
|---------|---------|
|実行されていない    | ソリューションはまったく分析されていません。        |
|実行中     | ソリューションが分析されています。       |
|完了できなかった     |  ソリューションの分析が要求されましたが、分析が正常に完了しませんでした。       |
|*日時* 現在の結果   | ソリューションの分析が完了し、結果をダウンロードできます。      |
|完了できなかった。 *日時* 現在の結果     | 最新の分析要求が正常に完了しませんでした。 最後の正常な結果をダウンロードできます。         |
|Microsoft がチェック     | これは、Microsoft の管理ソリューションです。 ソリューションの分析は、これらのソリューションで使用できません。         |
|発行元がチェック     | これは、サードパーティの管理ソリューションです。 現在、ソリューション分析は、これらのソリューションで利用できません。        |


## <a name="review-the-solution-checker-report"></a>ソリューション チェッカー レポートを確認
解析チェックが完了すると、ポータルで解析レポートを表示したり、Webブラウザからレポートをダウンロードすることができます。 ポータルでは、 **問題**、 **場所** 、 **重大度** 別に結果をフィルタリング、グループ化し、ソリューションで検出された問題の詳細情報を表示することができます。 

1. 左側のウィンドウで、**ソリューション**を選択します。
2. ソリューション チェッカーレポートを表示する非管理ソリューションの横に配置されている、 **...** を選択し、 **ソリューション チェッカー** をポイントして **結果を表示する** を選択します。  
3. 問題を選択すると、解決方法の詳細およびガイダンスが表示されます。

    > [!div class="mx-imgBorder"] 
    > ![](media/solution-checker-viewresults.png "ソリューション チェッカー 結果の表示")

ソリューションチェックの結果は、ダウンロードすることも可能です。 ソリューションのチェッカーのzipファイルが、Webブラウザで指定したフォルダにダウンロードされます。ダウンロードレポートは [!INCLUDE [pn-excel-short](../../includes/pn-excel-short.md)] 形式で、ソリューションで検出された問題の影響度、種類、場所の特定に有用な視覚化情報が含まれています。 問題の解決方法に関する詳細なガイダンスへのリンクも提供されます。 

1. 左側のウィンドウで、**ソリューション**を選択します。
2. ソリューション チェッカー レポートをダウンロードするアンマネージドソリューションの横に配置されている、 **...** を選択し、 **ソリューション チェッカー** をポイントして **結果のダウンロード** を選択します。  
3. ソリューション チェッカーの ZIP ファイルは、Web ブラウザーによって指定されたフォルダーにダウンロードされます。

レポート内の各列の概要を以下に示します。

|レポート フィールド |説明  |コンポーネントに適用   |
|---------|---------|---------|
|問題     |   ソリューションで識別される問題のタイトル。      | すべて        |
|カテゴリ     | 問題の分類が識別されます。**パフォーマンス**、**使用状況**、または **サポート可能性** などです。      |  すべて     |
|重要度     | 検出された問題の潜在的な影響を表します。 使用可能な影響の種類は、**高**、**中**、**下**、および**情報**です。         |  すべて       |
|ガイダンス     |  問題、影響、推奨されるアクションの詳細が記載された記事へのリンク。       |  すべて       |
|コンポーネント     |  問題が特定されたソリューション コンポーネントです。        |   すべて      |
|Location     |  アセンブリや JavaScript ファイル名など、特定された問題が発生したコンポーネントの場所やソース ファイルです。        |  すべて       |
|行番号     |  影響を受ける Web リソース コンポーネントの問題の行番号参照。       |  Web リソース       |
|モジュール     | アセンブリで特定された問題が検出されたモジュール名。     |   プラグインまたはユーザー定義ワークフロー活動      |
|型     | アセンブリで識別された問題の種類。        | プラグインまたはユーザー定義ワークフロー活動        |
|メンバー     |  アセンブリで識別された問題のメンバー。      | プラグインまたはユーザー定義ワークフロー活動        |
|ステートメント     | 問題が発生したコード ステートメントまたは構成。        |  すべて       |
|コメント     | 高レベルな解決手順が含まれる問題に関する詳細。         |  すべて       |


## <a name="best-practice-rules-used-by-solution-checker"></a>ソリューション チェッカーにより使用される推奨事項ルール

|ソリューション コンポーネント   |ルール名  |ルールの説明  |
|---------|---------|---------|
|プラグインまたはワークフロー活動   | [il-specify-column](http://go.microsoft.com/fwlink/?LinkID=398563&error=il-specify-column&client=PAChecker&source=featuredocs)  | Common Data Service クエリ API を通じてすべての列を選択しないでください。     |
|プラグインまたはワークフロー活動   | [meta-remove-dup-reg](http://go.microsoft.com/fwlink/?LinkID=398563&error=meta-remove-dup-reg&client=PAChecker&source=featuredocs)     | 重複する Common Data Service プラグインの登録を避けてください。     |
|プラグインまたはワークフロー活動   | [il-turn-off-keepalive](http://go.microsoft.com/fwlink/?LinkID=398563&error=il-turn-off-keepalive&client=PAChecker&source=featuredocs)   | Common Data Service プラグインで外部ホストを操作するときは、キープアライブを false に設定します。     |
|プラグインまたはワークフロー活動   | [il-avoid-unpub-metadata](http://go.microsoft.com/fwlink/?LinkID=398563&error=il-avoid-unpub-metadata&client=PAChecker&source=featuredocs)   | 非公開 Common Data Service メタデータの取得を避けてください。     |
|プラグインまたはワークフロー活動   | [il-avoid-batch-plugin](http://go.microsoft.com/fwlink/?LinkID=398563&error=il-avoid-batch-plugin&client=PAChecker&source=featuredocs)   | Common Data Service プラグインおよびワークフロー活動では、バッチ要求の型は使用しないでください。    |
|プラグインまたはワークフロー活動   | [meta-avoid-reg-no-attribute](http://go.microsoft.com/fwlink/?LinkID=398563&error=meta-avoid-reg-no-attribute&client=PAChecker&source=featuredocs)  | Common Data Service プラグイン登録にフィルター属性を含めます。    |
|プラグインまたはワークフロー活動   | [meta-avoid-reg-retrieve](http://go.microsoft.com/fwlink/?LinkID=398563&error=meta-avoid-reg-retrieve&client=PAChecker&source=featuredocs)  | Retrieve および RetrieveMultiple メッセージ用に登録された Common Data Service プラグインを使用するときは注意してください。    |
|プラグインまたはワークフロー活動   | [meta-remove-inactive](http://go.microsoft.com/fwlink/?LinkID=398563&error=meta-remove-inactive&client=PAChecker&source=featuredocs)    | Common Data Service で非アクティブ構成を削除します。    |
|プラグインまたはワークフロー活動   | [il-meta-avoid-crm2011-depr-message](http://go.microsoft.com/fwlink/?LinkID=398563&error=il-avoid-crm2011-depr-message&client=PAChecker&source=featuredocs)  | Microsoft Dynamics CRM 2011 の削除済みメッセージを使用しないでください。     |
|プラグインまたはワークフロー活動   | [meta-avoid-crm4-event](http://go.microsoft.com/fwlink/?LinkID=398563&error=meta-avoid-crm4-event&client=PAChecker&source=featuredocs) | Microsoft Dynamics CRM 4.0 プラグイン登録ステージを使用しないでください。    |
|プラグインまたはワークフロー活動   | [il-avoid-specialized-update-ops](http://go.microsoft.com/fwlink/?LinkID=398563&error=il-avoid-specialized-update-ops&client=PAChecker&source=featuredocs)  | Common Data Service で特殊な更新操作要求を使用しないでください。    | 
| プラグインまたはワークフロー活動 |  [il-use-autonumber-feature](http://go.microsoft.com/fwlink/?LinkID=398563&error=il-use-autonumber-feature&client=PAChecker)  |カスタム自動付番ではなく、自動付番機能ソリューションを使用します。 | 
| プラグインまたはワークフロー活動  | [il-avoid-parallel-plugin](http://go.microsoft.com/fwlink/?LinkID=398563&error=il-avoid-parallel-plugin&client=PAChecker)  | 並列パターンは、プラグイン内では使用しないでください。  |
| プラグインまたはワークフロー活動  | [il-avoid-lock-plugin](http://go.microsoft.com/fwlink/?LinkID=398563&error=il-avoid-lock-plugin&client=PAChecker)  | プラグインの静的メンバーのロックをしないでください。  |
| プラグインまたはワークフロー活動  | [meta-avoid-retrievemultiple-annotation](http://go.microsoft.com/fwlink/?LinkID=398563&error=meta-avoid-retrievemultiple-annotation&client=PAChecker)  | アノテーションの RetrieveMultiple でプラグインを登録しないでください。  |
|Web リソース  | [web-use-async](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-use-async&client=PAChecker&source=featuredocs)  |  HTTP および HTTPS リソースを非同期に操作します。   |
|Web リソース  | [meta-remove-invalid-form-handler](http://go.microsoft.com/fwlink/?LinkID=398563&error=meta-remove-invalid-form-handler&client=PAChecker&source=featuredocs)  | 無効な Common Data Service フォーム イベント登録を修正するか、または削除します。   |
|Web リソース  | [meta-remove-orphaned-form-element](http://go.microsoft.com/fwlink/?LinkID=398563&error=meta-remove-orphaned-form-element&client=PAChecker&source=featuredocs)  | 孤立した Common Data Service フォーム イベント登録を修正するか、または削除します。   |
|Web リソース  | [web-avoid-modals](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-avoid-modals&client=PAChecker&source=featuredocs)  | モーダル ダイアログを使用しないでください。   |
|Web リソース  | [web-avoid-crm2011-service-odata](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-avoid-crm2011-service-odata&client=PAChecker&source=featuredocs)   | Microsoft Dynamics CRM 2011 OData 2.0 エンドポイントをターゲットにしないでください。     |
|Web リソース  | [web-avoid-crm2011-service-soap](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-avoid-crm2011-service-soap&client=PAChecker&source=featuredocs)  | Microsoft Dynamics CRM 2011 SOAP サービスをターゲットにしないでください。   |
|Web リソース  | [web-avoid-browser-specific-api](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-avoid-browser-specific-api&client=PAChecker&source=featuredocs) | Internet Explorer レガシー API またはブラウザーのプラグインを使用しないでください。   |
|Web リソース  | [web-avoid-2011-api](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-avoid-2011-api&client=PAChecker&source=featuredocs)  | 廃止された Microsoft Dynamics CRM 2011 オブジェクト モデルを使用しないでください。  |
|Web リソース  | [web-use-relative-uri](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-use-relative-uri&client=PAChecker&source=featuredocs)   | 絶対 Common Data Service エンドポイント URL を使用しないでください。    |
|Web リソース  | [web-use-client-context](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-use-client-context&client=PAChecker&source=featuredocs)  | クライアント コンテキストを使用してください。   |
|Web リソース  | [web-use-dialog-api-param](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-use-dialog-api-param&client=PAChecker&source=featuredocs)   | ダイアログ API パラメーターを使用します。   |
|Web リソース  | [web-use-org-setting](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-use-org-setting&client=PAChecker&source=featuredocs)   | 組織設定を使用します。   |
|Web リソース  | [web-use-grid-api](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-use-grid-api&client=PAChecker&source=featuredocs)   | グリッド API を使用します。    |
|Web リソース  | [web-avoid-isActivityType](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-avoid-isActivityType&client=PAChecker&source=featuredocs)   | Xrm.Utility.isActivityType メソッドを新しい Xrm.Utility.getEntityMetadata に置き換えます。リボン ルールは使用しないでください。    |
|Web リソース  | [meta-avoid-silverlight](http://go.microsoft.com/fwlink/?LinkID=398563&error=meta-avoid-silverlight&client=PAChecker&source=featuredocs)   | Silverlight Web リソースの使用は廃止されました。   |
| Web リソース  | [web-remove-debug-script](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-remove-debug-script&client=PAChecker)  | 非開発環境にデバッグのスクリプトを追加することは避けてください。  | 
| Web リソース  | [web-use-strict-mode](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-use-strict-mode&client=PAChecker)  | 可能な場合は厳密なモードを使用します。  | 
| Web リソース  | [web-use-strict-equality-operators](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-use-strict-equality-operators&client=PAChecker)  | 厳密等価演算子の使用。  | 
| Web リソース  | [web-avoid-eval](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-avoid-eval&client=PAChecker)  | 「eval」 関数または同等の機能を使用しないでください。  | 


### <a name="see-also"></a>関連項目
[ Common Data Serviceに関するベスト プラクティスとガイダンス](../../developer/common-data-service/best-practices/index.md)<br />
[モデル駆動型アプリのベスト プラクティスとガイダンス](../../developer/model-driven-apps/best-practices/index.md)<br />
[ソリューション チェッカーの一般的な問題と解決策](common-issues-resolutions-solution-checker.md)<br />
