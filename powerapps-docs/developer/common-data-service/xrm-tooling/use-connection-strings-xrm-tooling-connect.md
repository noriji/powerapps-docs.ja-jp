---
title: XRM ツールの接続文字列を使用して Common Data Service に接続する (Common Data Service) | Microsoft Docs
description: XRM ツールによって、接続文字列を使用した Common Data Service 環境への接続が可能になります
ms.custom: ''
ms.date: 03/27/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: a98b2fce-df49-4b60-91f4-a4446aa61cd3
caps.latest.revision: 21
author: MattB-msft
ms.author: nabuthuk
manager: kvivek
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="use-connection-strings-in-xrm-tooling-to-connect-to-common-data-service"></a>XRM ツールの接続文字列を使用して Common Data Service に接続する

Common Data Service では、 XRM ツールによって、接続文字列を使用した Common Data Service 環境への接続が可能になります これは **SQL Server** で使用される接続文字列の概念と似ています。 接続文字列は、最大限のセキュリティを得るために構成セクションを暗号化する機能を含むネイティブ サポートを、構成ファイルに備えています。 これにより、Common Data Service 環境に接続する際に、使用しているアプリケーションにハード コーディングしない Common Data Service 接続を展開時に構成することができます。  


<a name="Create"></a> 

## <a name="create-a-connection-string"></a>接続文字列の作成

 以下の例のように、この接続文字列をプロジェクトの `app.config` または `web.config` ファイルで指定します。  
  
```xml  
<connectionStrings>  
    <add name="MyCDSServer" connectionString="AuthType=Office365;Url=http://contoso:8080/Test;UserName=jsmith@contoso.onmicrosoft.com; 
  Password=passcode" />  
</connectionStrings>  
```  
  
> [!IMPORTANT]
> `app.config` ファイルまたは `web.config file` にアカウント パスワードなどの機密情報を追加する場合は、適切なセキュリティ対策を講じてその情報を保護してください。  
  
 接続文字列を作成したら、それを使用して <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient> オブジェクトを作成します。  
  
```csharp  
//Use the connection string named "MyCDSServer"  
//from the configuration file  
CrmServiceClient svc = new CrmServiceClient(ConnectionString);  
```  
  
> [!NOTE]
> コード内の以下の `using` ディレクティブを使用して、`System.Configuration` 名前空間を参照し、コード内の接続文字列にアクセスする必要があります: `using System.Configuration;`  
  
 <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient> オブジェクトを作成したら、そのオブジェクトを使用して Common Data Service でアクションを実行することができます。 詳細: [Common Data Service で XRM ツールを使用してアクションを実行する](use-xrm-tooling-execute-actions.md)  
  
<a name="Parameters"></a>

## <a name="connection-string-parameters"></a>接続文字列パラメーター

 接続文字列には、セミコロンで区切られた一連の名前=値の組が含まれまています。 次の表は、任意の受注で入力できる、サポートされるパラメーターを一覧表示しています。  
  
|パラメーター名|説明|  
|--------------------|-----------------|  
|`ServiceUri`、`Service Uri`、`Url`または`Server`|Common Data Service 環境の URL を指定します。 URL は、http または https プロトコルを使用することができ、ポートはオプションです。 http プロトコルの既定ポートは 80 で、https プロトコルの既定ポートは 443 です。 サーバー URL の形式は通常 `https://`*`<organization-name>`*`.crm.dynamics.com`です。<br /><br /> 組織名は必須です。|  
|`Domain`|ユーザーの資格情報を検証するドメインを指定します。|  
|`UserName`、`User Name`、`UserId`または`User Id`|資格情報に関連付けられたユーザーの ID 名を指定します。|  
|`Password`|資格情報に関連付けられたユーザー名のパスワードを指定します。|  
|`HomeRealmUri` または `Home Realm Uri`|ホーム レルムの Uri を指定します。|  
|`AuthenticationType` または `AuthType`|Common Data Service 環境に接続するための認証の種類を指定します。 有効な値は次のとおりです: `AD`, `IFD` (AD FS 有効化)、`OAuth` または `Office365`。<br /><br /> -    `AD` および `IFD` は、Common Data Service 設置型環境でのみ許可されています。<br />-   `OAuth` は、Common Data Service および設置型環境でのみ許可されています。<br />-   `Office365` は、Common Data Service 環境にのみ許可されています。|  
|`RequireNewInstance`|接続がまだアクティブの間に再呼び出しされた場合に、既存の接続を再利用するかどうかを指定します。 既定値は既存の接続が再利用されることを示す `false` です。 `true` に設定した場合、これによりシステムは強制的に固有の接続を作成します。|  
|`ClientId`、`AppId` または `ApplicationId`|Azure Active Directory または Active Directory フェデレーション サービス (AD FS) にアプリケーションを登録したとき割り当てた `ClientID` を指定します。<br /><br /> このパラメータは認証の種類が `OAuth` として指定されている場合にのみ適用されます。|  
|`RedirectUri` または `ReplyUrl`|Azure Active Directory または Active Directory フェデレーション サービス (AD FS) に登録したときの、アプリケーションのリダイレクト URI を指定します。<br /><br /> このパラメータは認証の種類が `OAuth` として指定されている場合にのみ適用されます。|  
|`TokenCacheStorePath`|ユーザー トークンのキャッシュに保存する必要がある場所の完全なパスを指定します。 実行プロセスには指定されたパスへのアクセス権があるべきです。 このパスを設定し構成することが、このプロセスの役割です。<br /><br /> このパラメータは認証の種類が `OAuth` として指定されている場合にのみ適用されます。|  
|`LoginPrompt`|資格情報が提供されていない場合に資格情報の入力を促すかどうかを指定します。 有効な値は:<br /><br /> -   `Always`: 常に資格情報を指定するようユーザーを促す。<br />-   `Auto`: プロンプトを表示するかどうかを、ログイン コントロール インターフェイスで選択することをユーザーに許可する。<br />-   `Never`: 資格情報を指定するようユーザーを促さない。 使用している接続方法にユーザー インターフェースがない場合は、この値を使用してください。<br /><br /> このパラメータは認証の種類が `OAuth` として指定されている場合にのみ適用されます。|  
|`StoreName` または `CertificateStoreName`|サムプリントで識別された証明書を見つけることができる店舗名を指定します。 設定した場合、サムプリントが必要です。|
|`Thumbprint` または `CertThumbprint`| S2S 接続時に使用する証明書のサムプリントを指定します。 設定した場合、AppID が必要であり、UserId とパスワード値は無視されます。|
|`SkipDiscovery`|特定のインスタンスの接続 URI を決定するためにインスタンス検出を呼び出すかどうかを指定します。 NuGet リリース Microsoft.CrmSdk.XrmTooling.CoreAssembly バージョン 9.0.2.7 の時点で、規定は true です。 以前のバージョンの既定は false です。 <br/> 注意: true に設定された場合、ユーザーがターゲット インスタンスの正しい URI を正確に指定することが重要です。|

<a name="Examples"></a>

## <a name="connection-string-examples"></a>接続文字列の例
 
次の例は、on-ine の展開および認証シナリオに接続するための接続文字列の使用方法を示しています。 設置型および IFD 展開インスタンスの接続文字列の例は、次に示す Dynamics 365 Customer Engagement (on-premises) ドキュメントで入手可能になりました: [XRM ツールで接続文字列を使用して Customer Engagement に接続する](/dynamics365/customer-engagement/on-premises/developer/xrm-tooling/use-connection-strings-xrm-tooling-connect) 

### <a name="named-account-using-office-365"></a>Office 365 を使用している取引先企業  
  
```xml
<add name="MyCDSServer" 
 connectionString="
  AuthType=Office365;
  Username=jsmith@contoso.onmicrosoft.com; 
  Password=passcode;
  Url=https://contoso.crm.dynamics.com"/>  
```  
  
### <a name="oauth-using-named-account-in-office-365-with-ux-to-prompt-for-authentication"></a>認証のプロンプトに Office 365 で UX と一緒に取引先企業を使用している OAuth  
  
```xml
<add name="MyCDSServer"
 connectionString="
  AuthType=OAuth;
  Username=jsmith@contoso.onmicrosoft.com;
  Password=passcode;
  Url=https://contosotest.crm.dynamics.com;
  AppId=<GUID>;
  RedirectUri =app://<GUID>;
  TokenCacheStorePath =c:\MyTokenCache;
  LoginPrompt=Auto"/>  
```  

### <a name="certificate-based-authentication"></a>クレームベース認証

```xml
<add name="MyCDSServer" 
  connectionString="
  AuthType=Certificate;
  SkipDiscovery=true;
  url={InstanceUri};
  thumbprint={CertThumbPrintId};
  ClientId={AppId};
  RequireNewInstance=true"
  />
```

<a name="ConnectionStatus"></a>

## <a name="determine-your-connection-status"></a>接続状態を決定する

 接続要求が成功したかどうかを決定するには、<xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient><xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient.IsReady>  プロパティ。 **true** の場合、接続が成功し、実行する準備ができています。 それ以外の場合は、接続失敗の原因として、<xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient>.<xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient.LastCrmError> および <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient>.<xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient.LastCrmException> プロパティの値を確認します。  
  
### <a name="see-also"></a>関連項目

[XRM ツールを使用して Windows のクライアント アプリケーションを作成する](build-windows-client-applications-xrm-tools.md)<br />
[CrmServiceClient コンストラクターを使用した Common Data Service への接続](use-crmserviceclient-constructors-connect.md)<br />
[XRM ツールを使用して Common Data Service でアクションを実行](use-xrm-tooling-execute-actions.md)<br />
<xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient>
