---
title: XRMツールに PowerShell cmdlets を使用して Common Data Service に接続する (Common Data Service)| Microsoft Docs
description: Get-CrmConnection や Get-CrmOrganizations などの XRMツール の PowerShell cmdlets を使用して Common Data Service に接続し、現在のユーザーがアクセスできる組織を取得する方法を説明します。
ms.custom: ''
ms.date: 03/27/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
  - Dynamics 365 (online)
ms.assetid: 81816457-c963-46ca-b350-615fa75f56a7
caps.latest.revision: 27
author: MattB-msft
ms.author: nabuthuk
manager: kvivek
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="use-powershell-cmdlets-for-xrm-tooling-to-connect-to-common-data-service"></a>XRMツールにPowerShell cmdlets を使用して Common Data Serviceに接続する

XRMツールでは、次の **Windows PowerShell** cmdletsを使用して Common Data Service に接続し、現在のユーザーがアクセス権を持つ組織を取得できます: cmdletsは `Get-CrmConnection` と `Get-CrmOrganizations` です。  

 
<a name="Prereq"></a>   

## <a name="prerequisites"></a>前提条件  
  
-  XRM ツールのコマンドレットを使用するにはバージョン 3.0 以降の **PowerShell** が必要です。 バージョンを確認するには **PowerShell** のウィンドウを開き次のコマンドを実行します: `$Host`  
  
-  実行ポリシーを設定して署名済みの **PowerShell** スクリプトを実行します。 それには **PowerShell** ウィンドウを **administrator** として開き、次のコマンドを実行します: `Set-ExecutionPolicy -ExecutionPolicy RemoteSigned`  
  
<a name="register"></a>   

## <a name="acquire-the-microsoftxrmtoolingcrmconnectorpowershell-cmdlet"></a>Microsoft.Xrm.Tooling.CrmConnector.PowerShell cmdlet を取得する 

**Microsoft.Xrm.Tooling.CrmConnector.PowerShell** cmdletを使用するには、インストールをする必要があります。 XRMツール である PowerShell cmdlet は、[PowerShell Gallery](https://www.powershellgallery.com/packages/Microsoft.Xrm.Tooling.CrmConnector.PowerShell)で使用することができます。 cmdlet のダウンロードとインストールをします。
  
PowerShell または PowerShell ISE を管理モードで開き、次のコマンドを実行します:

   ```powershell
  Install-Module -Name Microsoft.Xrm.Tooling.CrmConnector.PowerShell
   ```  
既にモジュールをインストールしている場合は、次のコマンドで更新できます:

   ```powershell
  Update-Module -Name Microsoft.Xrm.Tooling.CrmConnector.PowerShell
   ```
    
以上で、 **Microsoft.Xrm.Tooling.CrmConnector.PowerShell** cmdletを使用する準備ができました。 登録した関数を一覧表示するには、PowerShellウィンドウで次のコマンドを実行します:  
  
   ```powershell
  Get-Help “Crm”  
   ```  


<a name="RetrieveOrgs"></a>   

## <a name="use-the-cmdlet-to-retrieve-organizations-from-common-data-service"></a>コマンドレットを使用して、Common Data Service から組織を取得  

`Get-CrmOrganizations` コマンドレットを使用して、アクセスできる組織を取得します。  
  

1.  Common Data Service インスタンスに接続する資格情報を入力します。 次のコマンドを実行すると、Common Data Service インスタンスに接続するためのユーザー名とパスワードの入力が要求され、それらは `$Cred` 変数に保存されます。  

  
    ```powershell  
    $Cred = Get-Credential  
    ```  
2. 次のコマンドを使用して組織を取得し、その情報を `$CRMOrgs` 変数に格納します

    - Common Data Service インスタンスに接続している場合:  
  
        ```powershell  
        $CRMOrgs = Get-CrmOrganizations -Credential $Cred -DeploymentRegion NorthAmerica –OnlineType Office365  
        ```  
  
        > [!NOTE]
        > `DeploymentRegion` パラメーターの有効な値は、`NorthAmerica`、`EMEA`、`APAC`、`SouthAmerica`、`Oceania`、`JPN`、`CAN`、`IND`、および `NorthAmerica2` です。 `OnlineType` パラメーターの場合には、`Office365` を指定します。
  
  
3.  手順 2 でコマンドを実行するときに、入力した資格情報が検証されます。 コマンドの実行が成功したら、次のコマンドを入力してから Enter キーを押し、アクセスできる組織を表示します。  
  
      ```powershell  
      $CRMOrgs  
      ```  
      > [!div class="mx-imgBorder"]
      > ![Common Data Service組織情報](../media/xrmtooling-powershell-1.png "Common Data Service")
  

> [!TIP]
> 取得した Common Data Service 組織を格納するために使用された変数 (この場合は、`$CRMOrgs`) を、`Get-CrmConnection` コマンドレットとともに使用して、Common Data Service に接続できます。 組織名を指定するには、コマンド `$CRMOrgs.UniqueName` を使用します。  
>   
> `$CRMOrgs` 変数に格納されている組織の値が複数の場合は、コマンド `$CRMOrgs[n-1]` を使用して `nth` の組織を参照できます。 たとえば、`$CRMOrgs` 変数の 2 番目の組織の一意の名前を参照するには、コマンド `$CRMOrgs[1].UniqueName` を使用します。
  
<a name="ConnecttoCRM"></a>
   
## <a name="use-the-cmdlet-to-connect-to-common-data-service"></a>コマンドレットを使用して Common Data Service に接続  

`Get-CrmConnection` コマンドレットを使用して Common Data Service インスタンスに接続します。 このコマンドレットにより、XRM ツール共通ログイン コントロールを使用して資格情報を指定して Common Data Service に接続できるし、または資格情報をインライン パラメーターとして指定することができます。 詳細: [XRM ツールの共通ログイン コントロールを使用する](use-xrm-tooling-common-login-control-client-applications.md)

> [!IMPORTANT]
> `Get-CrmConnection` コマンドレットを使用する前に、次のコマンドを使用して PowerShell によるTLS 1.2の使用を強制し、 Common Data Service インスタンスに接続してください。<br/>
> `[System.Net.ServicePointManager]::SecurityProtocol = [System.Net.SecurityProtocolType]::Tls12`<br/>
> Common Data Service 接続に関する TLS 1.2 要件の詳細については、次を参照してください [ブログ: Common Data Service 接続セキュリティに関する更新](https://blogs.msdn.microsoft.com/crm/2017/09/28/updates-coming-to-dynamics-365-customer-engagement-connection-security/)   
  
### <a name="connect-to-common-data-service-by-using-the-common-login-control"></a>共通ログイン コントロールを使用して Common Data Service に接続  
  
1.  共通ログイン コントロールを使用して資格情報を提供し、Common Data Service に接続する場合は、次のコマンドを使用します。 接続情報は、後で使用できるように、`$CRMConn` 変数に保存されます。  
  
    ```powershell  
    $CRMConn = Get-CrmConnection -InteractiveMode  
    ```  
  
2. **LoginControl** ダイアログ ボックスが表示されます。 Common Data Service インスタンスに接続するための資格情報を指定し、**ログイン**をクリックします。    
  
### <a name="connect-to-common-data-service-by-specifying-credentials-inline"></a>資格情報をインラインで指定して Common Data Service に接続  
  
1.  Common Data Serviceに接続するには、次のコマンドを使用します。 これらのコマンドは、先に作成した `$Cred` 変数を使用して、組織を取得すると同時に、資格情報を保存します。 接続情報は `$CRMConn` 変数に保存されます。

     - Common Data Service インスタンスに接続する場合:

        ```powershell  
        $CRMConn = Get-CrmConnection -Credential $Cred -DeploymentRegion <Deployment region name> –OnlineType Office365 –OrganizationName <OrgName>  
        ```
        > [!NOTE]
        > `DeploymentRegion` パラメーターの有効な値は、`NorthAmerica`、`EMEA`、`APAC`、`SouthAmerica`、`Oceania`、`JPN`、`CAN`、`IND` および `NorthAmerica2` です。 `OnlineType` パラメーターの場合には、`Office365` を指定します。 
  
        > [!NOTE]
        > 前のすべてのコマンドの `OrganizationName` パラメーターについて、組織の一意の名前またはフレンドリ名を指定できます。 また、`Get-CrmOrganizations` コマンドレットを使用して取得して `$CRMOrgs` 変数に保存した、組織の一意の名前またはフレンドリ名も使用できます。 たとえば、`$CRMOrgs[x].UniqueName` または `$CRMOrgs[x].FriendlyName` を使用できます。  
  
2.  手順 1 でコマンドを実行するときに、入力した資格情報が検証されます。 コマンドレットの実行が成功したら、次のコマンドを入力してから Enter キーを押し、接続情報と状態を表示します。  

      ```powershell  
       $CRMConn  
       ```  

       > [!div class="mx-imgBorder"]
       > ![Common Data Service 接続情報と状態](../media/xrm-tooling-powershell-2.png "Common Data Service 接続情報と状態") 

  
### <a name="see-also"></a>関連項目
  
[XRMツールAPIを使用してCommon Data Serviceに接続する](use-crmserviceclient-constructors-connect.md)<br />
[XRM ツールを使用して Windows のクライアント アプリケーションを作成する](build-windows-client-applications-xrm-tools.md)<br />
[ブログ: Common Data Serviceでデータ操作およびユーザー設定とシステム設定を行う PowerShell モジュール](http://blogs.msdn.com/b/crm/archive/2015/09/25/powershell-module-for-performing-data-operations-and-manipulating-user-and-system-settings-in-crm.aspx)
