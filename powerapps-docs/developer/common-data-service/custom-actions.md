---
title: 独自のアクションの作成 (Common Data Service) | Microsoft Docs
description: アクションは Common Data Service の機能を拡張するために役立つカスタム メッセージです。 独自のアクションの作成方法について学習する
ms.custom: ''
ms.date: 09/20/2019
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="create-your-own-actions"></a>独自のアクションの作成

*アクション*と呼ばれるユーザー定義メッセージを作成することで、Common Data Service の機能を拡張できます。 これらの操作に要求と応答のクラスが関連付けられ、Web API アクションが生成されます。 アクションの一般的な使用方法は、新しいドメイン特有の機能を組織の Web サービスに追加すること、または組織の複数の Web サービス メッセージ要求を 1 つの要求に結合することです。 たとえば、サポートコール センターで、作成、割り当て、および 更新メッセージを単一の新しいエスカレート メッセージと結合することがあります。  
  
アクションのビジネス ロジックには、ワークフローを使用して実行されます。 アクションが作成されると、関連リアルタイム ワークフローが自動的に登録され、実行パイプラインのメイン操作ステージで実行されます。 
  
  
<a name="about_actions"></a>   

## <a name="about-action-definitions"></a>アクションの定義について  

 アクションはリアルタイムワークフローのような `Workflow` エンティティ レコードを使用して定義します。 アクションの内容および機能についてのまとめは、次の一覧に載せられています。  
  
- 一つのエンティティに関連付けることも、グローバル(任意の特定のエンティティに関連付けられない場合)とすることもできます。  
  
- イベント実行パイプラインのメイン操作ステージで実行されます。  
  
- イベント実行パイプラインの操作前および操作後の段階で登録されたプラグインの起動がサポートされています。  
  
- アクション ステータスをアクティブにしている間だけ、事後操作および事前操作の段階で、プラグインを登録できます。  
  
- Web API または `organization.svc` および `organization.svc/web` エンドポイントを介して使用可能です。  
  
- JavaScript の Web リソースを使用して実装できます。 
  
- 呼び出し元ユーザーのセキュリティ コンテキストで常に実行します。  
  
- プラグインのステップがアクションに登録されている間は、レコードを削除することはできません。  
  
- 構成設定によって、任意に、現在のデータベース トランザクションに参加できます。  
  
- 実行できるのがユーザー、部署、または組織に限定される場合、範囲はサポートされていません。 アクションは常に組織のスコープ内で実行します。  
  
- 入力および出力パラメーターをサポートします。  
  
- データの変更の監査をサポートします。  
  
- オフライン クライアントではサポートされていません。  
  
- Web サービス メソッド呼び出しによって起動できます。  
  
- ワークフローから直接起動できます。  
  
<a name="bkmk_permissions"></a> 
  
## <a name="required-permissions"></a>必要なアクセス許可
  
 アクションのリアルタイム ワークフローをアクティブ化して、実行するには、リアルタイム プロセスのアクティブ化 (`prvActivateSynchronousWorkflow`) というセキュリティ特権が必要です。 これは、ワークフローの作成に必要な特権への追加です。  

  
<a name="bkmk_package"></a>   

## <a name="package-an-action-for-distribution"></a>配布の操作をパッケージする

 Common Data Service 組織にインポートできるように操作を配布するには、Common Data Service ソリューションに操作を追加します。 これは、Web アプリケーションを使用して、**設定** > **カスタマイズ** > **ソリューション**と移動して容易に実行できます。 ソリューションを作成するコードを記述できます。 ソリューションについての詳細は、 [ソリューションの概要](introduction-solutions.md) を参照してください。  
  
<a name="bkmk_gentypes"></a>

## <a name="generate-early-bound-types-for-an-action"></a>操作用の事前バインド型を生成する

 CrmSvcUtil ツールを使用して、アプリケーション コードに含めるアクションに対する要求と応答クラスを生成することができます。 ただし、これらのクラスを生成する前に、操作をアクティブ化してください。  
  
CrmSvcUtil.exe をダウンロードするには、[NuGet からツールをダウンロード](download-tools-NuGet.md) を参照してください。
 
 次のサンプルは Common Data Service のコマンド ラインからツールを実行するときの構文を示しています。 取引先企業およびサーバーに適したパラメーター値を指定します。  
  
```ms-dos  
CrmSvcUtil.exe /interactivelogin ^
/out:<outputFilename>.cs ^
/namespace:<outputNamespace> ^
/serviceContextName:<serviceContextName> ^
/generateActions
```  
  
 `/generateActions` パラメーターを使用していることに注意してください。 詳細: [組織サービスの事前バインドクラスを生成する](org-service/generate-early-bound-classes.md)  
  
 実行する操作に対して生成された要求および応答クラスの事前バインドまたは遅延バインド型を使用できます。  
  
<a name="bkmk_executeWebAPI"></a>

## <a name="execute-an-action-using-the-web-api"></a>Web API を使用してアクションを実行する

新しいアクションを作成すると、そのアクションは Web API で作成されます。 アクションがエンティティのコンテキストで作成される場合、アクションはそのエンティティにバインドされます。 それ以外の場合は、バインドされていないアクションです。 詳細: [Web API アクションの使用](webapi/use-web-api-actions.md) を参照してください。  
  
<a name="bkmk_execute"></a>

## <a name="execute-an-action-using-the-organization-service"></a>組織サービスを使用して操作を実行する

組織 Web サービスを使用し、管理コードを使用して操作を実行するには、次の手順に従います。  
  
1. アプリケーションのプロジェクトで、CrmSvcUtil ツールを使用して生成された、事前バインド型ファイルの種類を含めます。  
  
2. アプリケーション コードで、アクションの要求を初期化して、必要なプロパティを入力します。  
  
3. <xref:Microsoft.Xrm.Sdk.IOrganizationService.Execute*>を呼び出し、要求を引数として渡します。  
  
   アプリケーション コードを実行する前に、操作が有効になっていることを確認します。 そうでない場合、ランタイム エラーが表示されます。  
  
<a name="BKMK_JavaScript"></a>   

### <a name="execute-an-action-using-a-javascript-web-resource"></a>JavaScript の Web リソースを使用して操作を実行する

すべてのシステム操作と同じように Web API を使用してアクションを実行できます。 詳細: [Web API アクションの使用](webapi/use-web-api-actions.md) を参照してください。  

  
<a name="bkmk_execute-process"></a>

## <a name="execute-an-action-using-a-process"></a>プロセスを使用して操作を実行

ワークフロー、ダイアログ、またはそのほかのプロセス アクションから任意のアクションを実行できます。 Web アプリケーションのプロセス フォームの**ステップの追加**ドロップ ダウンで、**アクションの実行**アイテムを選択することで、アクティブ化されたユーザー定義アクションがプロセスで使用可能になります。 プロセス ステップにこのステップが追加されると、このステップで提供される**アクション**リストから新しいユーザー定義アクション (または任意のアクション) を選択できます。 このステップで**プロパティの設定**を選択して、ユーザー定義アクションで必要な入力パラメーターを指定します。  
  
> [!NOTE]
>  ユーザー定義アクションに、たとえば、Picklist、Entity、または Entity Collection などのサポートされていないパラメーターの種類が存在する場合は、そのユーザー定義アクションは**アクション**リストには表示されません。  
  
既存の <xref:Microsoft.Xrm.Sdk.IExecutionContext.Depth> プラットフォームのチェックによって、無限ループが確実に発生しないようにします。 深さの制限の詳細については、「<xref:Microsoft.Xrm.Sdk.Deployment.WorkflowSettings.MaxDepth>」を参照してください。  
  
<a name="bkmk_longrunning"></a>

## <a name="watch-out-for-long-running-actions"></a>長時間の操作を監視する

操作のリアルタイム ワークフローの手順の 1 つがユーザー定義ワークフロー活動の場合、そのユーザー定義ワークフロー活動が隔離されたサンドボックス ランタイム環境で実行され、サンドボックス プラグインを管理する場合と同じように、2 分間のタイムアウト制限が課されます。 ただし、操作自体にかかる全体的な時間に制限はありません。 また、ロールバックが有効で、操作がトランザクションに参加している場合、SQL Server のタイムアウトが適用されます。  

> [!TIP]
>  ベスト プラクティスとして、長時間かかる操作は、.NET の非同期操作やバックグラウンド プロセスを使用して Common Data Service 外で実行することをお勧めします。  
  
### <a name="see-also"></a>関連項目  
 [アクションの使用](/flow/actions)<br />
 [イベント実行パイプライン](event-framework.md#event-execution-pipeline)<br />
 [従来の Common Data Service ワークフロー](/flow/workflow-processes)<br />

