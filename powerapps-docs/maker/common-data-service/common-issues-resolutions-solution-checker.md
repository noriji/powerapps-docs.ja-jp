---
title: ソリューション チェッカーの一般的な問題と解決策 | Microsoft Docs
description: ' ソリューション チェッカーにおける一般的な問題と解決策の一覧'
keywords: ''
ms.date: 02/11/2019
ms.service: powerapps
ms.custom:
  - ''
ms.topic: article
ms.assetid: caa4e3f2-9700-49b8-87ed-8a68e8878b02
author: jowells1
ms.author: jowells
manager: austinj
ms.reviewer: null
robots: 'noindex,nofollow'
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="common-issues-and-resolutions-for-solution-checker"></a>ソリューション チェッカーの一般的な問題と解決策

この記事ではソリューション チェッカーの使用中に発生する可能性がある一般的な問題について説明します。 適用対象には回避策を示します。

## <a name="youre-unable-to-use-solution-checker-to-run-analysis-or-download-results"></a>ソリューション チェッカーを使用して分析の実行や結果のダウンロードができない

ソリューション チェックや、結果のダウンロードの要求を送信した直後に、処理が完了せずに次のようなエラーメッセージが表示される:

> ***[ソリューション名称]** のソリューション チェックを実行することができませんでした。再度実行をしてください。*

実行が可能な時に、ソリューション チェッカーは潜在的な原因と解決手順の詳細へのリンクを含む特定のエラーメッセージが返されます。 詳細については **さらに詳しく** を選択してください。

![エラー メッセージ バー](media/solution-checker-missing-roles-error.png)

分析のバックグラウンド処理中に発生した障害は、**'Couldn't be completed'** ステータスで失敗すると PowerApps ポータルでエラー メッセージを返して要求者に電子メール通知を送信します。 

![エラー ステータス](media/solution-checker-exception-status.png)

ポータル通知を選択すると、本ページにリンクがされ、詳細なトラブルシューティングを行います。 提供された一般的な問題にてエラーが解決できなかった場合、参照番号が返されます。 この参照番号をMicrosoftサポートに提供することで、詳細な調査が行われます。

![エラーの通知](media/solution-checker-failure-notification.png)

## <a name="solution-checker-fails-due-to-unsupported-version-of-powerapps-checker"></a>サポートされていないバージョンの PowerApps チェッカーによりソリューション チェッカーが失敗する

ソリューション チェッカーは PowerApps チェッカー アプリで有効化される機能です。  バージョン **1.0.0.47** よりも前のバージョンの PowerApps チェッカー アプリをインストールした場合、ソリューション チェッカーの実行が正常に完了しない場合があります。 PowerApps チェッカーのバージョンを [!INCLUDE [pn-dyn-365-admin-center](../../includes/pn-dyn-365-admin-center.md)] からアップグレードする必要があります。 

ただし、バージョンが **1.0.0.45** より前の PowerApps チェッカーがインストールされている場合は、ソリューションを削除して再インストールすることをお勧めします。 最近のスキーマの変更により、PowerApps チェッカーの **1.0.0.45** より前のバージョンからのアップグレードは失敗する可能性があります。

ソリューション チェッカーの過去の結果を保持したい場合は、前回の実行からの結果をエクスポートするか、または [データをExcel にエクスポート](../../user/export-data-excel.md) を使用してすべてのソリューション チェッカーのデータを以下のエンティティからエクスポートします:

- 分析コンポーネント
- 分析ジョブ
- 分析結果
- 分析結果の詳細

### <a name="how-to-uninstall-powerapps-checker"></a>PowerApps チェッカーをアンインストールする方法

PowerApps チェッカー ソリューションをアンインストールする方法:

1. システム管理者またはシステム カスタマイザーとして https://web.powerapps.com/environments にアクセスして PowerApps ポータルを開きます。
2. **ソリューション**を選択します。
3. **PowerApps チェッカー** を選択し、ソリューション ツールバーで **削除** を選択します。

### <a name="how-to-install-powerapps-checker"></a>PowerApps チェッカーをインストールする方法

PowerApps チェッカーを Common Data Service 環境に再インストールする方法:

1. システム管理者またはシステム カスタマイザーとして、https://web.powerapps.com/environments にアクセスして PowerApps ポータルを開きます。
2. **ソリューション**を選択します。
3. ソリューション ツールバーで **ソリューション チェッカー** を選択し、次に **Install** を選択します。

## <a name="solution-checker-cant-access-organizations-in-administration-mode"></a>ソリューションチェッカー は管理者モードでは組織にアクセスすることができません

[管理者モード](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/admin/manage-sandbox-instances#administration-mode) に設定された組織は、システム管理者およびシステム カスタマイザの役割を持つユーザーだけに意図的なアクセスを制限を行います。 PowerApps チェッカー アプリケーション ID に既定でこれらのロールが割り当てられておらず、このモードで動作する組織にアクセスできません。

ソリューションチェッカー をこの組織にて使用するには、管理者モードを無効にする必要があります。

### <a name="how-to-disable-administration-mode"></a>管理者モードを無効にする

組織のインスタンスで管理者モードを無効にするには:

1. Dynamics 365 インスタンス ピッカーを開きます: https://port.crm.dynamics.com/G/Instances/InstancePicker.aspx。
2. ソリューション チェッカーの実行に問題がある組織のインスタンスを選択します。
3. **管理** を選択します。<br/>
![インスタンスの管理](media/solution-checker-instance-admin.png)

4. **管理者モードを有効にする** を削除し、 **保存**を選択します。<br/>
![管理モードの無効化](media/solution-checker-instance-disable-admin-mode.png)

5. ソリューション チェッカーを再実行

## <a name="solution-checker-fails-due-to-missing-security-roles"></a>セキュリティ役割が存在しないことに起因するソリューションチェッカーのエラー

ソリューションチェッカーを使用するユーザーには、 2つのセキュリティ役割が必要となります。これにより Common Data Service の組織と連携に必要な権限が与えられます。 これらのロールのいずれかが **'PowerApps チェッカー'** ユーザーに割り当てられていない場合、分析の実行、結果のダウンロード、キャンセルの実行は失敗します。 これは予期しないユーザーがセキュリティ役割を削除してしまうような自動化処理が実装されている場合に発生します。 以下のセキュリティ役割はには必要とされる最低限の権限が含まれています:

- カスタマイズのエクスポート
- ソリューション チェッカー

### <a name="how-to-assign-missing-security-roles"></a>不足しているセキュリティ役割の割り当て

足りないセキュリティ ロールを PowerApps チェッカー ユーザーに割り当てる方法:

1. Common Data Service の組織を開き、 **設定** > **セキュリティ** > **ユーザー**に移動します。
2. ユーザーのリストから **'PowerApps チェッカー'** ユーザーを選択します。
3. コマンドバーにて、 **役割の管理** を選択します。
4. **カスタマイズのエクスポート** と **ソリューション チェッカー** の役割のチェックボックスを選択し、 **OK** を選択します。<br/>
![必要なセキュリティ役割](media/solution-checker-required-roles.png)

5. ソリューション チェッカーを再実行

## <a name="solution-checker-fails-due-to-restricted-access-mode"></a>アクセスモードが制限されていることに起因するソリューションチェッカーのエラー

ソリューションチェッカーを使用するユーザーには、 **非対話型** または **読み書き** のアクセスモードが必要となります。これにより Common Data Service の組織と連携に必要な権限が与えられます。 アクセスモードが **管理者** のような値に変更されている場合は、分析の実行、結果のダウンロード、キャンセルの実行は失敗します。

この問題を解決するには「非対話型」アクセス モードで **'PowerApps チェッカー'** アプリケーション ユーザーを更新する必要があります。

### <a name="how-to-update-user-access-mode"></a>ユーザーのアクセスモードを更新する

PowerApps チェッカー ユーザーのアクセス モードを更新する方法:

1. Common Data Service の組織を開き、 **設定** > **セキュリティ** > **ユーザー**に移動します。
2. ユーザーのリストから **'PowerApps チェッカー'** ユーザーを選択し、ダブルクリックでユーザー フォームを開きます。
3. フォームの **管理** > **クライアント アクセス ライセンス (CAL) 情報** へとスクロールします。
4. **アクセスモード** のドロップダウンリストコントロールから **非対話型** を選択します。<br/>
![[アクセス モード]](media/solution-checker-access-mode.png)

5. 変更を保存してユーザーフォームを閉じます。
6. ソリューション チェッカーを再実行

## <a name="solution-checker-fails-due-to-disabled-first-party-application-in-aad"></a>AADでファースト パーティのアプリケーションが無効になっていることが原因で、ソリューション チェッカーがエラーとなる

ソリューション チェッカー (PowerApps-アドバイザー) で使用するファースト パーティのエンタープライズ アプリケーション ID を、Azure Active Directory (AAD) で無効化することはできません。 これが無効になっていると、要求されたユーザーの代理として Common Data Service とその他の必要なリソース プロバイダのベアラー トークンを要求する際に、IDの認証ができません。 

次の手順に従って、AADにてアプリケーションIDが無効になっていないことを確認し、必要に応じてアプリケーションを有効にします。

### <a name="how-to-verify-andor-modify-application-enabled-status"></a>アプリケーションの有効状態を確認/変更する

PowerApps-アドバイザー エンタープライズ アプリケーション ID の有効化状態を確認や変更する方法

1. [Azure Active Directory (AAD) ポータル](https://aad.portal.azure.com/) にてご利用のテナントにアクセスします。
2. **エンタープライズ アプリケーション**に移動します。
3. **すべてのアプリケーション** を選択して **'PowerApps-アドバイザー'** を検索します。<br/>
![PowerApps-アドバイザー アプリを検索](media/solution-checker-search-advisor-app.png)

4. **'PowerApps-アドバイザー'** を選択してアプリの詳細を表示します。
5. **プロパティ** を選択します。
6. **ユーザーをサインインできるようにする** の状態を確認します。 **いいえ** になっている場合は、アプリケーションは無効となります。<br/>
![無効にされたエンタープライズアプリ](media/solution-checker-disabled-app.png)

7. ラジオボタンを **はい** に変更します。 このアプリケーション オブジェクト<br/>
![PowerApps-アドバイザー アプリの有効化](media/solution-checker-enable-app.png)

8. **保存**を選択します。 このアプリケーションが有効になりました。 変更が適用されるまで数分かかる場合があります。
9. ソリューション チェッカーを再実行

> [!IMPORTANT]
> エンタープライズ アプリケーションを編集するには、 Azure Active Directory (AAD) にて管理者権限を持っている必要があります。

## <a name="solution-checker-fails-to-export-solutions-with-draft-business-process-flow-components"></a>ソリューション チェッカーにてドラフト版のビジネス プロセス フローのコンポーネントを使用してソリューションをエクスポートするとエラーになります

まだ有効にされたことのないビジネス プロセス フローのドラフト版がソリューションに含まれている場合、ソリューション チェッカーは分析用のソリューションのエクスポートに失敗します。 このエラーはソリューション チェッカーに限って発生するものではなく、基となっている (カスタム) エンティティ コンポーネントに依存するビジネス プロセスフローがまだに有効化されておらず、作成されていないことが原因です。 この問題は、ソリューション エクスプローラ内からビジネス プロセスフローが有効化されている場合にも発生します。

問題についての詳細と解決の手順については、 [KB 文書 #4337537: 無効なエクスポート - 不足しているビジネス プロセス エンティティ](https://support.microsoft.com/en-hk/help/4337537/invalid-export-business-process-entity-missing) を参照してください。

## <a name="solution-checker-fails-to-export-patched-solutions"></a>ソリューション チェッカーがパッチを適用したソリューションをエクスポートできない

ソリューションに [修正プログラム](https://docs.microsoft.com/powerapps/developer/common-data-service/create-patches-simplify-solution-updates) が適用済の場合、ソリューション チェッカーは分析のためのソリューションをエクスポートできません。 ソリューションに修正プログラムが適用されていると、元のソリューションがロックされそのソリューションを親ソリューションとして識別する依存修正プログラムが組織内に存在する限り、変更またはエクスポートができません。

この問題を解決するには、新しく作成されたソリューションに関連するすべてのパッチが含まれるように、ソリューションの完全なコピーを作成します。 これによりソリューションのロックが解除され、ソリューションをシステムからエクスポートできます。  詳細については、 [ソリューションの完全なコピーをする](use-segmented-solutions-patches-simplify-updates.md#clone-a-solution) を参照してください。

## <a name="solution-checker-will-not-analyze-empty-solutions"></a>ソリューション チェッカーは、空白のソリューションの分析をすることはできません。

ソリューション チェッカーに分析対象のコンポーネントが含まないソリューションをエクスポートした場合、以降の処理は中止され、処理は失敗となります。 ソリューション チェッカーに送信したソリューションに少なくとも1つのコンポーネントが含まれていることを確認してください。

## <a name="solution-checker-fails-to-export-large-solutions"></a>ソリューション チェッカーが大規模なソリューションをエクスポートできない

Common Data Service 環境からの大規模なソリューションのエクスポートが失敗すす場合は、エクスポート処理のリクエストにタイムアウトの例外処理が関係していることが考えられます。 これは処理に20分以上かかっている場合に発生します。 既定のソリューションのような大規模なソリューションは、この時間設定を超過する可能性があり、チェック処理は失敗します。 エクスポートの過程でソリューション チェッカーがタイプアウトを検出した場合、ジョブが失敗となるまで3回やり直しを行い、処理失敗の通知がされるまでは1時間以上かかることがあります。

分析対象のコンポーネント数を削減し、より小規模のソリューションを作成することが回避方法となります。 プラグイン アセンブリ コンポーネントが多数あることが原因でソリューションのサイズが大きくなっている場合は、 [カスタムアセンブリ開発の最適化](../../developer/common-data-service/best-practices/business-logic/optimize-assembly-development.md) のガイドを参照してください。 

> [!IMPORTANT]
> 誤検知を最小限に抑えるために、確実に依存するカスタマイズを追加してください。 ソリューションを作成してこれらのコンポーネントを追加する場合は、以下を含めます:
> - プラグインを追加するときは、プラグインの SDK メッセージ処理手順を含めます。
> - エンティティ フォームを追加するときは、フォーム イベントに添付された JavaScript Web リソースを含めます。  
> - JavaScript Webリソースを追加するときは、すべての依存する JavaScript Web リソースを含めます。
> - HTML Webリソースを追加するときは、HTML Webリソース内に定義されている依存スクリプトをすべて含めます。
> - カスタム ワークフローを追加するときは、ワークフロー内で使用されているアセンブリを含めます。

## <a name="line-number-references-for-issues-in-html-resources-with-embedded-javascript-are-not-correct"></a>JavaScript が埋め込まれた HTML リソースで問題の行番号参照が不正 

HTML Web リソースがソリューション チェッカーで処理されるときに、HTML Web リソースは HTML Web リソース内の JavaScript とは別に処理されます。 このため、HTML Web リソースの `<script>` の中に見つかった不正な行番号は正しくありません。

## <a name="web-unsupported-syntax-issue-for-web-resources"></a>Web リソースにおける Web-unsupported-syntax 問題

ソリューション チェッカーは、ECMAScript 6 (2015) またはそれ以降のバージョンには現在対応していません。 ソリューションチェッカーが ECMAScript 6 またはそれ以降のバージョンを使用したJavaScriptを分析する場合、Webリソースに対する web-supported-syntax の問題が報告されます。  

## <a name="multiple-violations-reported-for-plug-ins-and-workflow-activities-based-on-call-scope"></a>呼び出しスコープに基づいてプラグインとワークフロー活動について報告された複数の違反

問題が呼び出し側コンテキストのみに関連するプラグインとワークフロー活動ルールの場合、ソリューション チェッカー ツールが IPlugin インターフェースの実装で分析を開始して、実装の範囲で問題を検出するために呼び出しグラフを切り替えます。  場合によっては、問題が検出されたのと同じ場所に多数の呼び出しパスが到達することがあります。  この問題は呼び出しスコープに関連しているため、ツールはそのスコープに基づいてレポートして、個別の場所ではなくより良い影響を把握できます。 そのため、複数の問題が解決すべき単一の場所を参照することがあります。

## <a name="see-also"></a>関連項目
[ Common Data Serviceに関するベスト プラクティスとガイダンス](../../developer/common-data-service/best-practices/index.md)<br/>
[モデル駆動型アプリのベスト プラクティスとガイダンス](../../developer/model-driven-apps/best-practices/index.md)<br/>
