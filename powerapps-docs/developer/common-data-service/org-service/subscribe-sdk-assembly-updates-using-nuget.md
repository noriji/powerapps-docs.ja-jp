---
title: NuGet を使用した SDK のアセンブリ更新の購読 (Common Data Service) | Microsoft Docs
description: .NET SDK アセンブリと一部のコマンドライン ツールは、ソフトウェア配布のWebサイト nuget.org から利用できます。アプリケーションプロジェクトで NuGet パッケージを使用すると、SDK アセンブリおよびツールの最新リリースでプロジェクトを最新の状態に保つことができます。
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: brandonsimons
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="subscribe-to-sdk-assembly-updates-using-nuget"></a>NuGet を使用した SDK のアセンブリ更新の購読

.NET SDK アセンブリと一部のコマンドライン ツールは、ソフトウェア配布のWebサイト [nuget.org](http://www.nuget.org) から利用できます。アプリケーションプロジェクトで NuGet パッケージを使用すると、SDK アセンブリおよびツールの最新リリースでプロジェクトを最新の状態に保つことができます。 Visual Studio はバージョン 2010 以降でこの機能をサポートしています。Visual Studio で開発を行わない開発者用に、スタンドアロン型 NuGet クライアントもあります。 プロジェクトで NuGet パッケージを使用する他の利点は、アセンブリの参照と依存関係が自動的に処理されることです。  
  
<a name="BKMK_GetNuGetPackages"></a>

## <a name="where-to-find-the-nuget-sdk-packages"></a>NuGet SDK パッケージの入手先

NuGet SDK は、[crmsdk](https://www.nuget.org/profiles/crmsdk) プロファイルにあります。 これらは正式な Common Data Service パッケージです。 一覧のパッケージのいずれかを選択し、パッケージの詳細ページに移動します。 以下は、Common Data Service に関連する現在の NuGet パッケージです。  


|パッケージ|説明|
|---------|---------|
|[Microsoft.CrmSdk.CoreAssemblies](https://www.nuget.org/packages/Microsoft.CrmSdk.CoreAssemblies/)|Microsoft.Crm.Sdk.Proxy.dll および Microsoft.Xrm.Sdk.dll アセンブリとツールが含まれています。|
|[Microsoft.CrmSdk.CoreTools](https://www.nuget.org/packages/Microsoft.CrmSdk.CoreTools/)|Microsoft Dynamics 365 チーム作成の SDK ツールが含まれています。|
|[Microsoft.CrmSdk.Deployment](https://www.nuget.org/packages/Microsoft.CrmSdk.Deployment/)|Microsoft.Xrm.Sdk.Deployment.dll アセンブリが含まれています。|
|[Microsoft.CrmSdk.Outlook](https://www.nuget.org/packages/Microsoft.CrmSdk.Outlook/)|Microsoft.Crm.Outlook.dll アセンブリが含まれています。|
|[Microsoft.CrmSdk.WebApi.Samples.HelperCode](https://www.nuget.org/packages/Microsoft.CrmSdk.WebApi.Samples.HelperCode/)|PowerApps ドキュメント チームが作成した C# ヘルパーコード。 このコードは Web API で使用します。 これらのクラスは、設置型とオンライン展開、エラー処理、および接続文字列の設定の両方にWebサービス認証を提供します。 これらのクラスは、Web API のサンプルで使用されます|
|[Microsoft.CrmSdk.Workflow](https://www.nuget.org/packages/Microsoft.CrmSdk.Workflow/)|Microsoft.Xrm.Sdk.Workflow.dll アセンブリが含まれています|
|[Microsoft.CrmSdk.XrmTooling.CoreAssembly](https://www.nuget.org/packages/Microsoft.CrmSdk.XrmTooling.CoreAssembly/)|Microsoft.Xrm.Tooling.Connector アセンブリが含まれています。 |
|[Microsoft.CrmSdk.XrmTooling.CrmConnector.PowerShell](https://www.nuget.org/packages/Microsoft.CrmSdk.XrmTooling.CrmConnector.PowerShell/)|Xrm.Tooling.Connector Powershell のアセンブリが含まれています |
|[Microsoft.CrmSdk.XrmTooling.PackageDeployment.PowerShell](https://www.nuget.org/packages/Microsoft.CrmSdk.XrmTooling.PackageDeployment.PowerShell/)| Package Deployer Powershell のアセンブリが含まれています。        |
|[Microsoft.CrmSdk.XrmTooling.PackageDeployment.Wpf](https://www.nuget.org/packages/Microsoft.CrmSdk.XrmTooling.PackageDeployment.Wpf/)|Dynamics 365 Package Deployer が含まれています|
|[Microsoft.CrmSdk.XrmTooling.PackageDeployment](https://www.nuget.org/packages/Microsoft.CrmSdk.XrmTooling.PackageDeployment/)|Microsoft.Xrm.Tooling.PackageDeployment.CrmPackageExtentionBase.dll アセンブリが含まれています。|
|[Microsoft.CrmSdk.XrmTooling.PluginRegistrationTool](https://www.nuget.org/packages/Microsoft.CrmSdk.XrmTooling.PluginRegistrationTool/)|Microsoft Dynamics 365 用のプラグイン アセンブリ、ワークフロー アセンブリ、仮想エンティティ、サービスエンドポイントを管理するために必要なプラグイン登録ツールが含まれています。|
|[Microsoft.CrmSdk.XrmTooling.WpfControls](https://www.nuget.org/packages/Microsoft.CrmSdk.XrmTooling.WpfControls/)|Microsoft.Xrm.Tooling.CrmConnectControl.dll、Microsoft.Xrm.Tooling.Ui.St yles.dll、Microsoft.Xrm.Tooling.WebResourceUtility.dllアセンブリが含まれています。|

## <a name="how-to-install-a-package-in-your-project"></a>プロジェクトでパッケージをインストールする方法  
 プロジェクトに NuGet パッケージをインストールするための詳細は、[ダイアログを使用した NuGet パッケージの管理](http://docs.nuget.org/docs/start-here/managing-nuget-packages-using-the-dialog)を参照してください。  

## <a name="download-tools-from-nuget"></a>NuGet からツールをダウンロード

[NuGet からのツールのダウンロード](../download-tools-nuget.md)のトピックで PowerShell スクリプトを使用して NuGet からの開発で使用するツールをダウンロードできます。
  
### <a name="see-also"></a>関連項目  
 [NuGetドキュメント](/nuget/)   
 [インストール中NuGet](http://docs.nuget.org/docs/start-here/installing-nuget)