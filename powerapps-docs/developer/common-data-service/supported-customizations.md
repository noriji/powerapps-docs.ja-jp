---
title: Common Data Service のサポートされているカスタマイズ (Common Data Service) | Microsoft Docs
description: PowerApps ポータルにあるツールまたはドキュメントで説明されているツールを使用して、Common Data Service をカスタマイズする方法を説明します。
ms.custom: ''
ms.date: 01/25/2019
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: shmcarth
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---

<!-- This is the portion of the old topic that applies to Common Data Service
https://docs.microsoft.com/dynamics365/customer-engagement/developer/supported-extensions
 -->


# <a name="supported-customizations-for-common-data-service"></a>Common Data Service のサポートされているカスタマイズ

PowerApps ポータルで入手できるツール、または公式ドキュメントに説明されているツールを使用して、Common Data Service をカスタマイズすることができます。 これらのカスタマイズはサポートされており、アップグレードが可能です。

ここに記述されている以外の方法を使用して行われたカスタマイズについてはサポートされず、更新時や Common Data Service へのアップグレード時に問題が生じる場合があります。 詳細については、「[サポートされていないカスタマイズ](#unsupported-customizations)」を参照してください。

docs.microsoft.com、msdn.microsoft.com、または technet.microsoft.com のような Microsoft サイトで公開されている技術資料に記載のトピックはサポートされていますが、アップグレードできない可能性があります。


## <a name="customizations-using-powerapps-portal"></a>PowerApps ポータルを使用したカスタマイズ

Common Data Service には、カスタマイズに使用できるさまざまなツールが用意されています。 PowerApps ポータルおよび Web アプリケーションを使用したカスタマイズは完全にサポートされており、すべてアップグレード可能です。

次のカスタマイズ方法を使用すると、完全にサポートされるカスタマイズを実行できます。

- PowerApps ポータルまたはソリューション エクスプローラーのカスタマイズ。 詳細については、[Common Data Service とは](../../maker/common-data-service/data-platform-intro.md)を参照してください。

- Web アプリケーションの設定。 詳細については、[PowerApps の管理](../../administrator/admin-guide.md)を参照してください。

- Reporting Services。 詳細については、[モデル駆動型アプリにレポートを追加](/powerapps/maker/model-driven-apps/add-reporting-to-app)を参照してください。

> [!NOTE]
> 完全なサポートとは、開発者サポートでカスタマイズをサポートできること、およびアプリケーション サポートでそれらの変更を実行する顧客をサポートできることを意味します。

Web アプリケーションのカスタマイズ ツールを使用する方法の詳細については、[Common Data Service とは](../../maker/common-data-service/data-platform-intro.md)を参照してください。


## <a name="customizations-applied-using-code"></a>コードを使用して適用されたカスタマイズ

開発者受けのこのサイトのドキュメント、技術記事、およびこのサイトのサンプル コードと、Common Data Service 開発者サポート チームによってリリースされる情報は、コードを使用して適用されるカスタマイズの領域に含まれます。 具体的な操作とそのサポートおよびアップグレードのレベルは後ほどこのトピックで説明します。

### <a name="common-data-service-web-services"></a>Common Data Service の Web サービス

Web サービスの使用が完全にサポートされます。 これには、Web API、組織サービス、検出サービス、および組織データ サービスが含まれます。 Microsoft では API の下位互換性の維持に努めていますが、機能の追加のために API が変更される場合もあります。 また、エンティティの属性も将来のバージョンで変更される可能性があります。

### <a name="solution-file"></a>ソリューション ファイル

アンマネージド ソリューションファイルの変更は、このドキュメントに記載のとおりサポートされています。 次の手順で、モデル駆動型アプリの一定のカスタマイズ タスクが実行できます。

1. ソリューション コンポーネントをアンマネージド ソリューションとしてエクスポートします。
2. ソリューション パッケージの内容を抽出します。
3. customizations.xml ファイルの編集
4. ソリューション ファイルを再パッケージ化します。
5. 変更後のソリューションをインポートします。

> [!NOTE]
> `Customizations.xml` ファイルへの変更は `CustomizationsSolution.xsd` スキーマに準拠する必要があります。 詳細については、[カスタマイズ ソリューション ファイル スキーマ](customization-solutions-file-schema.md)を参照してください。

サポートされているタスクでこの手順を使用して実行できるものは次のとおりです。

- リボンのユーザー設定。
- サイトマップを使用したアプリケーション ナビゲーションのカスタマイズ。
- FormXml を使用したフォームおよびダッシュボードのカスタマイズ。
- 保存済みクエリのカスタマイズ。

### <a name="plug-ins"></a>プラグイン

このドキュメントで説明されているプラグイン メカニズムを使用したユーザー定義によるビジネス ロジックの作成は完全にサポートされており、アップグレード可能です。 プラグインは、サンドボックス (分離モード) でのみ登録および実行できます。 詳細: [プラグイン](plug-ins.md)

### <a name="workflow-extensions"></a>ワークフローの拡張機能

ワークフロー ルールから呼び出されるユーザー定義ワークフロー活動 (アセンブリ) の作成は完全にサポートされており、アップグレード可能です。 ユーザー定義ワークフロー活動は、サンドボックス (分離モード) で登録および実行のみできます。 詳細: [ワークフロー拡張](workflow/workflow-extensions.md)

## <a name="support-for-net-framework-versions"></a>.NET Framework バージョンのサポート

次で、Microsoft .NET Framework 4.6.2. を使用して記述されたカスタム コードのサポートに関して考慮すべき事項について説明します。

- Web サービスを呼び出す Microsoft .NET Framework 4.6.2 以上を使用して作成された Web サービス クライアントは、Common Data Service で完全にサポートされています。

    > [!IMPORTANT]
    > ユーザー定義のクライアント アプリケーションを作成するには、Microsoft .NET フレームワーク 4.6.2 またはそれ以降を使用します。 Transport Level Security (TLS) 1.2 またはそれより優れたセキュリティを使用するアプリケーションのみが接続を許可されます。 TLS 1.2 は .NET Framework 4.5.2 で使用される既定のプロトコルではありませんが、.NET Framework 4.6.2 内にあります。


- プラグイン アセンブリまたはユーザー定義ワークフロー活動として Common Data Service で使用される Microsoft .NET Framework 4.6.2 を使用して作成された .NET アセンブリはすべてサポートされています。

## <a name="unsupported-customizations"></a>サポートされていないカスタマイズ

このドキュメントで説明されたメソッドまたは Common Data Service のいずれのツールも使用しないで実行された Common Data Service の変更はサポートされず、Common Data Service の更新時またはアップグレード時に保存されません。 このドキュメントおよびサポート ドキュメントに文書化されていないものはすべてサポートされません。 また、サポートされていない変更を加えると、修正プログラムや Service Pack によって更新する際、または Common Data Service をアップグレードする際に問題が生じる可能性があります。 

次は、よく質問されるサポートされていない操作の種類の一覧です:

- 次を除く Common Data Service のダイナミックリンク ライブラリ (DLL) の参照。

    - Microsoft.Crm.Outlook.Sdk.dll
    - Microsoft.Crm.Sdk.Proxy.dll
    - Microsoft.Xrm.Sdk.dll
    - Microsoft.Xrm.Sdk.Data.dll
    - Microsoft.Xrm.Sdk.Deployment.dll
    - Microsoft.Xrm.Sdk.Workflow.dll
    - Microsoft.Xrm.Tooling.Connector.dll
    - Microsoft.Xrm.Tooling.CrmConnectControl.dll
    - Microsoft.Xrm.Tooling.PackageDeployment.CrmPackageExtentionBase.dll
    - Microsoft.Xrm.Tooling.WebResourceUtility.dll

- Web API、組織サービス、展開サービス、探索サービス、組織データ サービス の Web サービスにある、文書化されたアプリケーション プログラミング インターフェイス (API) 以外の API の使用。

- プラグインおよびワークフロー アセンブリには、それぞれの dll 内にすべての必要なロジックが含まれている必要があります。 プラグインはいくつかのコア .Net アセンブリを参照する場合があります。 とはいえ、グラフィックス デザイン インターフェイスなどの下位の Windows API とやり取りする .Net アセンブリへの依存関係はサポートされていません。 以前は Dynamics 365 ではアセンブリがこれらのインターフェイスを参照することを許可していましたが、セキュリティ標準に準拠するため、この動作への変更が必須です。

- Common Data Service の標準アセンブリ (Microsoft.Crm.*.dll) のプラグイン アセンブリの作成、または `pluginassembly` を作成したプラットフォームのアップデートや削除はサポートされていません。

- ソリューション ファイルの編集による、リボン、フォーム、サイトマップ、または保存されたクエリ以外のソリューション コンポーネントの編集はサポートされていません。 詳細については、[カスタマイズを編集するタイミング](when-edit-customization-file.md)を参照してください。 ソリューション ファイルの定義による新しいソリューション コンポーネントの定義はサポートされていません。 ソリューションと共にエクスポートされた Web リソース ファイルの編集はサポートされていません。 [管理ソリューションの保守](maintain-managed-solutions.md)に記載されている手順を除いて、マネージド ソリューションの内容の編集はサポートされていません。

### <a name="outlook-client"></a>Outlook クライアント
- Dynamics 365 フォームに対する変更、Office Outlook への新しいフォーム (カスタム .aspx ページなど) の直接追加、または .pst ファイルの変更。 これらの変更はアップグレードされません。
- サポート ツール以外のツールを使用してカスタマイズを行う。

### <a name="see-also"></a>関連項目

[モデル駆動型アプリケーションに対するサポートされているカスタマイズ](../model-driven-apps/supported-customizations.md)




