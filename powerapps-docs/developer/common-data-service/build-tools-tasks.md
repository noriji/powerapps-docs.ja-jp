---
title: 構築ツールのタスク| Microsoft Docs
description: 'PowerApps Build Tools は、一連の PowerApps 固有の Azure DevOps 構築タスクです。これを使用することで PowerApps のアプリケーション ライフサイクルの管理にあたって、ツールやスクリプトを手動でダウンロードする必要がなくなります。 このトピックでは、利用可能なタスクについて説明します。 '
ms.custom: ''
ms.date: 07/21/2019
ms.reviewer: Dean-Haas
ms.service: powerapps
ms.topic: article
author: mikkelsen2000
ms.author: pemikkel
manager: kvivek
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---

# <a name="build-tools-tasks"></a>ツール構成タスク

[!INCLUDE [cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

PowerApps Build Tools の一部として、数種類の構築タスクを利用することができ、これによって Azure DevOps を使用してアプリケーションのライフサイクルを自動化することができます。
  
## <a name="helper-task"></a>ヘルパー タスク

PowerApps ツールのインストーラは、構築とパイプラインのリリースにおける最初のタスクとして必要になります。 このタスクでは、エージェントに必要となる一連の PowerApps のツールをインストールし、PowerApps 構築タスクを実行します。 このタスクには、追加の構成は不要です。

## <a name="quality-check"></a>品質のチェック

PowerApps チェッカー タスクは、一連の最良の規則に対してソリューションの静的分析チェックを実行し、ソリューションの構築時に誤って導入した可能性のある問題パターンを特定します。

| **パラメーター** | **説明** |
| --- | --- |
| PowerApps チェッカーサービス  |   PowerApps チェッカーのサービス エンドポイントを選択します。 サービス エンドポイントは **プロジェクト設定** 配下の **サービスの接続** で定義されています。  **注意:** この特定のタスクにのみ使用する必要があるサービス接続の種類は「PowerApps チェッカー」であり、これはサービス プリンシパル接続です。 タスクが使用する前に、サービスプリンシパルを構成する方法の詳細情報については [こちら](https://aka.ms/buildtoolsconnection)を参照してください。  |
| 分析を行うファイルの場所  | ローカルのファイルを参照するか、SASのURLから参照するかを指定します。 
| 分析を行うローカルファイル/解析するファイルのSAS URI |  分析を行うzipファイルのパスとファイル名を指定します。   ワイルドカードを使用することができます。 たとえば、すべてのサブフォルダのzipファイルを指定するには **\*.zip と入力します。 ファイルを直接指定するか、Sasのuriからファイルを参照することができます。   |
|  ルールセット |   適用するルールセットを指定します。 次の二つのルールセットを使用できます:  **ソリューションのチェッカー:** [メーカー ポータル](https://make.powerapps.com/) から実行するルールセットと同じです。    **AppSource:** これは、 [AppSource](https://appsource.microsoft.com/en-US/)に公開されるに先立って、アプリケーションを認証するために使用される拡張ルールセットです。   |

### <a name="configure-service-connection-for-powerapps-checker"></a>PowerApps チェッカーのサービス接続を構成する

PowerApps タスク チェッカーを構成する前に、PowerApps チェッカー サービスへの接続に使用するサービス プリンシパルを定義する必要があります。 PowerApps チェッカーサービスの基盤と認証については [こちら](https://docs.microsoft.com/en-us/powershell/powerapps/overview?view=pa-ps-latest#get-started-using-the-microsoftpowerappscheckerpowershell-module) を参照してください。ただし、開始するにあたっての必要となるすべての情報は以下にて解説しています。

以下では、[AzureAD PowerShell モジュール](https://docs.microsoft.com/en-us/powershell/module/azuread/?view=azureadps-2.0) を使用して必要な Azure Active Directory (AAD) アプリケーションを生成し、クライアント シークレットを追加後に、それを使用して PowerApps チェッカー接続文字列の構成を行います。

> [!NOTE]
> この手順を完了するには、PowerApps (P1/P2) または D365 CE にライセンスされた AAD テナントにサービスプリンシパルを作成するための権限が必要となります。 

1. 管理者権限で PowerShell コマンドを開きます。
![Powershell コマンドウィンドウ](media/pscommand.png "Powershell コマンドウィンドウ")
2. PowerShellで次のコマンドを実行します: *Install-Module -Name AzureAD*
![Install-Module コマンド](media/pscommand-install.png "Install-Module コマンド 画面")
 
3.  このコマンドでは、PSGalleryのモジュールを信頼するように求められます。 **A (すべて はい)** を選択します。
1. 以下の内容をコピーし、 PowerShell プロンプトに貼り付けます:

```powershell 
function New-PowerAppsCheckerAzureADApplication
{
    [CmdletBinding()]
    param(
        [Parameter(Mandatory = $true)]
        [Guid]
        $TenantId,
        [Parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [string]
        $ApplicationDisplayName
    )
    # Using AzureAD as the RM modules, AzureRm.Resource and AzureRm.Profile, do not allow for setting RequiredResourceAccess
    Import-Module AzureAD | Out-Null
    try
    {
        Connect-AzureAD -TenantId $TenantId | Out-Null
    }
    catch [Microsoft.Open.Azure.AD.CommonLibrary.AadAuthenticationFailedException]
    {
        Write-Error "Received a failure result from the connecting to AzureAD, $($_.Exception.Message). Stopping."
        return
    }
    $graphSignInAndReadProfileRequirement = New-Object -TypeName "Microsoft.Open.AzureAD.Model.RequiredResourceAccess"
    $acc1 = New-Object -TypeName "Microsoft.Open.AzureAD.Model.ResourceAccess" -ArgumentList "e1fe6dd8-ba31-4d61-89e7-88639da4683d","Scope"
    $graphSignInAndReadProfileRequirement.ResourceAccess = $acc1
    $graphSignInAndReadProfileRequirement.ResourceAppId = "00000003-0000-0000-c000-000000000000"

    $powerAppsCheckerApiRequirement = New-Object -TypeName "Microsoft.Open.AzureAD.Model.RequiredResourceAccess"
    $acc1 = New-Object -TypeName "Microsoft.Open.AzureAD.Model.ResourceAccess" -ArgumentList "d533b86d-8f67-45f0-b8bb-c0cee8da0356","Scope"
    $acc2 = New-Object -TypeName "Microsoft.Open.AzureAD.Model.ResourceAccess" -ArgumentList "640bd519-35de-4a25-994f-ae29551cc6d2","Scope"
    $powerAppsCheckerApiRequirement.ResourceAccess = $acc1,$acc2
    $powerAppsCheckerApiRequirement.ResourceAppId = "c9299480-c13a-49db-a7ae-cdfe54fe0313"

    $application = New-AzureADApplication -DisplayName $ApplicationDisplayName -PublicClient $true -ReplyUrls "urn:ietf:wg:oauth:2.0:oob" -RequiredResourceAccess $graphSignInAndReadProfileRequirement, $powerAppsCheckerApiRequirement
    if ($application -eq $null -or $application.AppId -eq $null)
    {
        Write-Error "Unable to create the application as requested."
    }
    else
    {
        Write-Host "The application $($application.AppId):$ApplicationDisplayName was created in the tenant, $TenantId. You may need to have an administrator grant consent. If running in a userless process, you will need to add a secret or certificate in which to authenticate." 
    }
    return $application
}

# Login to AAD as your user
Connect-AzureAD

# Establish your tenant ID
$tenantId = (Get-AzureADTenantDetail).ObjectId

# Create the AAD application registration using the AzureAD module and the sample script
$newApp = New-PowerAppsCheckerAzureADApplication -ApplicationDisplayName "PowerApps Checker Client" -TenantId $tenantId

# Next step => create a secret via the Admin portal, CLI, or PowerShell module.
 ```

5.  プロンプトが表示されたら、 **A (常に実行)** を選択します。
![PowerShell コマンド画面](media/pscommand-always-run.png "PowerShell コマンドスクリーンョット")
6. ログイン ダイアログが表示されます。 サインインしてください。 場合によっては2回サインインする必要があるかもしれない点に留意してください。
7. スクリプトが完了すると、アプリケーションID と テナントがコマンド ウィンドウに表示されます。
8. 次に、 [Azure AD](https://portal.azure.com) にログインしてクライアント シークレットを取得します。
9. Microsoft Azure で **Azure Active Directory –> アプリ 登録 -> PowerApps チェッカー クライアント** と順に選択します。
![Azureでチェッカークライアントを選択する](media/azure-select-checker.png "Azure のスクリーンショット")
10. 左のナビゲーション ウィンドウの **管理**配下にある **証明書とシークレット** を選択します。
11. **証明書とシークレット** 画面の **証明書とシークレット**配下の **新規クライアント シークレット**を選択します。 
12. クライアント シークレットの説明を入力し、有効期限の設定を選択して、 **追加**をクリックします。
13. 次の画面に表示されるクライアント シークレットの値をコピーします。 
![クライアント シークレットを値コピーする](media/client-secret-copy.png "クライアント シークレットのスクリーンショット")
    > [!NOTE]
    > クライアント シークレットが表示されるのはこの時だけです。
14. PowerApps チェッカー サービス接続を開いて、**サービス プリンシパル キー** フィールドにクライアント シークレットを貼り付けて **OK** をクリックします。

これで [PowerApps チェッカー ビルド タスク](https://aka.ms/buildtoolsdoc) で接続を使用する準備が整いました。 

## <a name="solution-tasks"></a>ソリューション タスク

タスクでこの設定には、ソリューションに対してアクションを実行、以下のタスクが含まれます:

### <a name="powerapps-import-solution"></a>PowerApps インポート ソリューション

ソリューションのインポートでは、対象の環境にソリューションをインポートします。

| **パラメーター** | **説明** |
|----|----|
| PowerApps 環境 URL  | ソリューションのインポートを行う対象の環境のサービス エンドポイント。 たとえば、*https://powerappsbuildtools.crm.dynamics.com* などとします。  サービス エンドポイントは **プロジェクト設定** 配下の **サービスの接続** で定義することができます。 |
| ソリューション入力ファイル  | 対象の環境へのインポートを行う solution.zip ファイルのパスとファイル名称。 例: *$(Build.ArtifactStagingDirectory)\$(SolutionName).zip*。
 |
> [!NOTE] 
> 変数を使用することで、パイプラインのさまざまな部分に重要なデータを簡単に取り込むことができます。 事前定義された変数の包括的なリストは、 [こちら](https://docs.microsoft.com/en-us/azure/devops/pipelines/build/variables?view=azure-devops&tabs=yaml)で確認することができます。

### <a name="powerapps-export-solution"></a>PowerApps エクスポート ソリューション

ソリューションのエクスポート タスクは、元となる環境からソリューションをエクスポートします。

| **パラメーター** | **説明** |
|----------|-------------|
| PowerApps 環境 URL | ソリューションのエクスポートを行う対象の環境のサービス エンドポイント。  **プロジェクト設定**の **サービスの接続 -> 一般的なサービスの接続** で定義されています。 |
| ソリューション名 | エクスポートを行うソリューションの名称。 ここでは常にソリューションの「名称」を使用します。 「表示名称」ではありません。 |
| ソリューション出力ファイル | 対象の環境へのエクスポートを行う solution.zip ファイルのパスとファイル名称。 例: *$(Build.ArtifactStagingDirectory)\$(SolutionName).zip*。 |

> [!NOTE] 
> 変数を使用することで、パイプラインのさまざまな部分に重要なデータを簡単に取り込むことができます。 事前定義された変数の包括的なリストは、 こちらで確認することができます。
 
### <a name="powerapps-unpack-solution"></a>PowerApps 展開ソリューション

ソリューションの展開タスクでは、圧縮されたソリューションファイルを複数のXMLファイルやその他形式のファイルへの分解を行うことで、これらファイルをソース コントロール システムでより簡単に管理できるようになります。

| **パラメーター** | **説明** |
|------------|---------|
| ソリューション入力ファイル | 展開をする solution.zip ファイルのパスと名称を指定します。 |
| ソリューションを展開する対象のフォルダ | ソリューションの展開を行う対象のフォルダとパス。 |
| ソリューションの種類 | 展開するソリューションの種類:  **管理されていないソリューション** (推奨) : *管理されていないソリューションのみをリポジトリ*、 **管理対象のソリューション**、 **またはその両方** へと展開する必要があります。 |


### <a name="powerapps-pack-solution"></a>PowerApps 圧縮ソリューション

ソース コントロールに表示されているソリューションを solution.zip へと圧縮すると、このファイルを、目的の環境へとインポートすることができます。

| **パラメーター** | **説明** |
|------------|---------|
| ソリューション出力ファイル | solution.zip ファイルのパスとファイル名称を指定してソリューションの圧縮を行います。 |
| 圧縮をするソリューションの対象フォルダ | 圧縮をするソリューションのパスと対象のフォルダです。 |
| ソリューションの種類 | 圧縮をするソリューションの種類:  **管理されていないソリューション** (推奨) : **管理対象のソリューション**、 **またはその両方**、 |

### <a name="publish-customizations"></a>カスタマイズの公開

カスタマイズの公開タスクは、環境内のすべてのカスタマイズを公開します。

| **パラメーター** | **説明** |
|------------|---------|
| PowerApps 環境 URL | カスタマイズの発行をする環境のサービス エンドポイントです。  これは、 **プロジェクト設定** 配下の **サービスの接続** で定義されています。 |

### <a name="powerapps-set-solution-version"></a>PowerApps セット ソリューション バージョン 

セット ソリューション バージョンのタスクは、ソリューションのバージョンを更新します。

| **パラメーター** | **説明** |
|---------------------------|----|
| PowerApps 環境 URL  | パッケージを展開する対象とする環境のサービス エンドポイントです。  これは、 **プロジェクト設定** 配下の **サービスの接続** で定義されています。 |
| パッケージ ファイル  | 展開するパッケージのパスとファイル名称です。 |

### <a name="powerapps-deploy-package"></a>PowerApps 展開パッケージ

パッケージの展開タスクでは環境にパッケージを展開します。 パッケージの展開を行うと、単一のソリューションがいるの場合とは異なり、複数のソリューション、データ、コードを環境に展開するオプションが提供されます。

| **パラメーター** | **説明** |
|---------------------------|----|
| PowerApps 環境 URL  | 更新を行うソリューションを含む環境のサービス エンドポイントです。  これは、 **プロジェクト設定** 配下の **サービスの接続** で定義されています。 |
| ソリューション名  | バージョン番号を設定するソリューションの名称です。 |

## <a name="environment-management-tasks"></a>環境管理のタスク

環境管理タスクは、共通の環境管理機能を自動化するために使用され、これには以下のタスクが含まれます:

### <a name="powerapps-create-environment"></a>PowerApps 環境の作成

環境作成のタスクは、環境の作成を行います。

> [!NOTE]
> 新しい環境は、追加の環境作成に対するライセンスが付与されている、または処理可能な容量が存在する場合にのみ、プロビジョニングすることができます。

| **パラメーター** | **説明** |
|---------|-----------|
| 展開地域 | 環境を展開する領域です。 |
| インスタンスの種類 | 展開するインスタンスの種類です。 オプションはサンドボックス環境、または実稼働環境です。 |
| 基本言語 | 環境の基本言語です。 |
| ドメイン名 | これは、URLの一部を構成する環境固有の文字列です。 たとえば、ある環境が次のURLを使用している場合: *https://powerappsbuildtasks.crm.dynamics.com*、ドメイン名は 「powerappsbuildtasks」です。  注意: 既に使用されているドメインを入力した場合、タスクは0から始まる数値をURLに追加します。 上記例では、URLは、 *https://powerappsbuildtasks0.crm.dynamics.com*になります。 |
| フレンドリ名 | 環境のフレンドリーネームです。 |

### <a name="powerapps-delete-environment"></a>PowerApps 環境の削除

環境削除のタスクは、環境の削除を行います。

| **パラメーター** | **説明** |
|---------|-----------|
| PowerApps 環境 URL  | 削除する環境のサービス エンドポイントです。  これは、 **プロジェクト設定** 配下の **サービスの接続** で定義されています。 |

### <a name="powerapps-backup-environment"></a>PowerApps 環境のバックアップ

環境のバックアップ タスクは、環境のバックアップを行います。 

| **パラメーター** | **説明** |
|---------|-----------|
| PowerApps 環境 URL  | バックアップをする環境のサービス エンドポイントです。  これは、 **プロジェクト設定** 配下の **サービスの接続** で定義されています。 |
| バックアップ ラベル  | バックアップを割り当てるラベルです。  |

### <a name="powerapps-copy-environment"></a>PowerApps 環境のコピー

環境のコピー タスクは対象の環境に環境のコピーを行います。 2つの種類のコピーを利用できます: 完全コピー、および最小コピー。 完全コピーではデータとソリューションのメタデータ (カスタマイズ) の両方がコピーされますが、最小コピーではソリューションのメタデータのみがコピーされ、実際のデータはコピーされません。

> [!NOTE]
> このタスクは、D365 CE 環境でのみ使用することができます。  

| **パラメーター** | **説明** |
|---------|-----------|
| PowerApps ソース環境の URL  | コピー元の環境のサービス エンドポイントです。  これは、 **プロジェクト設定** 配下の **サービスの接続** で定義されています。 |
| PowerApps ターゲット環境の URL  | コピー先の環境のサービス エンドポイントです。  これは、 **プロジェクト設定** 配下の **サービスの接続** で定義されています。 |
