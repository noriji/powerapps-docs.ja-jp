---
title: XRM ツールを使用して Windows クライアント アプリケーションを構築する (Common Data Service) | Microsoft Docs
description: XRM ツールは Common Data Service 用 Windows クライアント アプリケーションを作成するためのサポートを提供する一連の API です。
ms.custom: ''
ms.date: 03/27/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
  - Dynamics 365 (online)
ms.assetid: e2f22576-1705-4854-a804-a1ca232c0cfc
caps.latest.revision: 33
author: MattB-msft
ms.author: nabuthuk
manager: kvivek
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="build-windows-client-applications-using-the-xrm-tools"></a>XRM ツールを使用して Windows のクライアント アプリケーションを作成する

XRM ツールは、Common Data Service の Windows クライアント アプリケーションの構築をサポートする Common Data Service アセンブリ API (組織サービスとディスカバリ サービス) に構築された一連の API です。 次の共有機能を提供します。  
  
- Common Data Service インスタンスにサインインする認証モードをすべてサポートします。  
- Common Data Service インスタンスの認証と接続の PowerShell サポートを提供します。  
- マルチスレッド環境の Common Data Service で実行される操作のためのスレッド セーフを提供します。 詳細 [コンポーネントのマルチスレッド](https://msdn.microsoft.com/library/vstudio/3es4b6yy.aspx)、[コンポーネントのマルチスレッド](https://msdn.microsoft.com/library/vstudio/a8544e2s.aspx)  
- Windows クライアント アプリケーションから Common Data Service への一貫したサインイン操作のために、Common Data Service で共通の Windows Presentation Foundation ログイン コントロールを提供します。  
- サインイン資格情報の安全な格納、最初のサインイン後に Common Data Service に自動的にサインインするための、保存された資格情報の再利用をサポートします。  
- Provides built-in diagnostic tracing and performance reporting of the actions performed in Common Data Service で実行されたアクションの組み込み診断トレースおよびパフォーマンス レポートをサポートし、これにより組織の要求に基づいて構成できます。  

## <a name="components-of-xrm-tooling"></a>XRM ツールのコンポーネント  

XRM ツールには以下の 3 種類のコンポーネントがあります。  
  
- **開発者用インターフェイス**: これにより、Common Data Service SDK アセンブリ API のための下位レベル相互通信、およびラッパー メソッドを提供します。 それぞれの通話のパフォーマンスを判定できるように、組込み診断機能を持つ Common Data Service を呼び出すためのスレッド セーフ環境を提供する、搭載 API です。 また、デバッグ サポートのための、トレース リスナーの標準セットを提供します。 このコンポーネントの名前空間は <xref:Microsoft.Xrm.Tooling.Connector> です。  
  
- **共通ログイン コントロール**: これは、Common Data Service へのサインイン エクスペリエンスのための共通ユーザー インターフェースを提供する、WPF ユーザー コントロールです。 ログイン コントロールは、Common Data Service でサポートされているすべての認証モードに対するサポートを提供します。 共通ログイン コントロールは、資格情報、プロファイルを安全に格納するための組み込み暗号化を備え、Common Data Service に対して自動サインインを実行時にそれを再利用します。 このコンポーネントの名前空間は <xref:Microsoft.Xrm.Tooling.CrmConnectControl> です。  
  
- **Web Resource Utility**: これは Common Data Service の Web リソースの 2 つのタイプ、イメージおよび XML からの情報に対するアクセス サポートを提供します。 Common Data Service Web リソースからのイメージにアクセスし、WPF BitmapImage オブジェクトとして返すことができます。 同様に、XML Web リソースを文字列として返すことができます。 このコンポーネントの名前空間は <xref:Microsoft.Xrm.Tooling.WebResourceUtility> です。  
  
## <a name="client-applications-that-use-xrm-tooling"></a>XRM ツールを使用するクライアント アプリケーション

Common Data Service の現在のバージョンの以下のアプリケーションは、クライアント アプリケーションから Common Data Service にサインインするとき、ユーザーの認証に共通 WPF ログイン コントロールを使用します。  
  
- Unified Service Desk。 詳細: [Unified Service Desk の拡張](/dynamics365/customer-engagement/unified-service-desk/extend-unified-service-desk)

<!--Package Deployer tool. More information: [Deploy packages using Package Deployer and Windows PowerShell](../../administrator/deploy-packages-using-package-deployer-windows-powershell.md)-->   

<!--Configuration Migration tool. More information [Manage your configuration data](../../administrator/manage-configuration-data.md)-->  
  
### <a name="see-also"></a>関連項目

[サンプル: XRM ツール API のクイック スタート](sample-quick-start-xrm-tooling-api.md)<br />
[ブログ: Common Data Serviceでデータ操作およびユーザー設定とシステム設定を行う PowerShell モジュール](http://blogs.msdn.com/b/crm/archive/2015/09/25/powershell-module-for-performing-data-operations-and-manipulating-user-and-system-settings-in-crm.aspx)

