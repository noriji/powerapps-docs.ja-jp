---
title: ポータルの SAML 2.0 プロバイダー設定を構成する |MicrosoftDocs
description: ポータルの SAML 2.0 プロバイダー設定を追加して構成する方法について説明します。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/18/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: af5b0ae8eddb68127c7271fccb4696a23fedfc60
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2019
ms.locfileid: "73542741"
---
# <a name="configure-saml-20-provider-settings-for-portals"></a>ポータルの SAML 2.0 プロバイダー設定を構成する

外部認証を提供するには、1つまたは複数の[SAML 2.0](https://docs.oasis-open.org/security/saml/Post2.0/sstc-saml-tech-overview-2.0-cd-02.html)準拠の id プロバイダー (IdP) を追加します。 このドキュメントでは、サービスプロバイダーとして機能するポータルと統合するために、さまざまな id プロバイダーを設定する方法について説明します。  

## <a name="ad-fs-idp"></a>AD FS (IdP)

[!include[](../../../includes/pn-active-dir-fed-svcs-ad-fs.md)]などの id プロバイダーの設定。

### <a name="create-an-ad-fs-relying-party-trust"></a>AD FS 証明書利用者信頼を作成する

> [!Note]
> これらの手順を [!INCLUDE[pn-powershell-short](../../../includes/pn-powershell-short.md)] スクリプトで実行する方法については、以下の「 [PowerShell を使用した AD FS の構成](#configure-ad-fs-by-using-powershell)」を参照してください。

[!include[](../../../includes/pn-adfs-short.md)] 管理ツールを使用して、[**サービス** > **要求の説明**] にアクセスします。

1.  **[要求の追加の説明]** を選択します。
2.  要求を指定します。

    -  表示名:**永続的な識別子**

    -  要求識別子: **urn: oasis: names: tc: SAML: 2.0: nameid-format: persistent**

    -  **[有効]** チェックボックス: このフェデレーションサービスが受け入れることができる要求の種類として、フェデレーションメタデータにこの要求の説明を公開します。

    -  **[有効]** チェックボックス: このフェデレーションサービスが送信できる要求の種類として、フェデレーションメタデータにこの要求の説明を公開します。

3.  **[OK]** を選択します。

[!include[](../../../includes/pn-adfs-short.md)] 管理ツールを使用して、[**信頼関係** >**証明書利用者信頼**] を選択します。

1. **[証明書利用者信頼の追加]** を選択します。
2. ようこそ: **開始** を選択します。
3. データソースの選択: **証明書利用者に関するデータを手動で入力する** を選択し、**次へ** を選択します。
4. 表示名の指定: 名前を入力し、**次へ** を選択します。
   例: https://portal.contoso.com/
5. プロファイルの選択:  **AD FS 2.0 プロファイル** を選択し、**次へ** を選択します。
6. 証明書の構成: **[次へ]** を選択します。
7. URL の構成: **[SAML 2.0 WebSSO プロトコルのサポートを有効にする]** チェックボックスをオンにします。
   証明書利用者 SAML 2.0 SSO サービス URL: https://portal.contoso.com/signin-saml2 を入力します
   - 注: [!include[](../../../includes/pn-adfs-short.md)] には、ポータルを HTTPS で実行する必要があります。

   > [!Note] 
   > 結果のエンドポイントには次の設定があります。 
   > - エンドポイントの種類: **SAML アサーションの使用エンドポイント**             
   > - バインド: **POST**                                            
   > - インデックス: n/a (0)                                              
   > - URL: **https://portal.contoso.com/signin-saml2**

8. Id の構成: https://portal.contoso.com/を指定し、 **[追加]** を選択して、 **[次へ]** を選択します。
   該当する場合は、追加の証明書利用者ポータルごとに id を追加できます。 ユーザーは、使用可能なすべての id に対して認証できるようになります。
9. 発行承認規則を選択する: **[すべてのユーザーにこの証明書利用者へのアクセスを許可する]** を選択し、 **[次へ]** を選択します。
10. 信頼の追加の準備完了: **[次へ]** を選択します。
11. **[閉じる]** を選びます。

**名前 ID**要求を証明書利用者信頼に追加します。

**[!INCLUDE[pn-ms-windows-short](../../../includes/pn-ms-windows-short.md)] アカウント名**を**名前 ID**要求 (入力方向の要求の変換) に変換します。

- 入力方向の要求の種類: **[!INCLUDE[pn-ms-windows-short](../../../includes/pn-ms-windows-short.md)] アカウント名**

- 出力方向の要求の種類:**名前 ID**

- 送信名 ID の形式:**永続的な識別子**

- すべての要求値をパススルーする

### <a name="create-site-settings"></a>サイト設定の作成

上記の [!include[](../../../includes/pn-adfs-short.md)] 証明書利用者信頼を参照するポータルサイト設定を適用します。

> [!Note]
> 標準 [!include[](../../../includes/pn-adfs-short.md)] (IdP) 構成では、次の設定 (値の例を含む) のみを使用します。 Authentication/SAML2/ADFS/MetadataAddress-<https://adfs.contoso.com/FederationMetadata/2007-06/FederationMetadata.xml>  
> - Authentication/SAML2/ADFS/AuthenticationType- https://adfs.contoso.com/adfs/services/trust    
>   -   フェデレーションメタデータのルート要素で**entityID**属性の値を使用します (上記のサイト設定の値であるブラウザーで**metadataaddress URL**を開きます)。 
> - Authentication/SAML2/ADFS/ServiceProviderRealm- https://portal.contoso.com/  
> - Authentication/SAML2/ADFS/AssertionConsumerServiceUrl- https://portal.contoso.com/signin-saml2  
>   **フェデレーションメタデータ**は、[!include[](../../../includes/pn-adfs-short.md)] サーバーで次のスクリプトを実行することによって **[!INCLUDE[pn-powershell-short](../../../includes/pn-powershell-short.md)]** で取得できます: `Import-Module adfs`
>   `Get-ADFSEndpoint -AddressPath /FederationMetadata/2007-06/FederationMetadata.xml`

[Provider] タグのラベルを置き換えることで、複数の IdP services を構成できます。 各一意のラベルは、IdP に関連する設定のグループを形成します。 例: ADFS、[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD、MyIdP


| サイト設定名                                             | 説明                                                                                                                                                                                                                                                                                                                                                                                                                             |
|---------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 認証/登録/ExternalLoginEnabled              | 外部アカウントのサインインと登録を有効または無効にします。 既定値: true                                                                                                                                                                                                                                                                                                                                                            |
| Authentication/SAML2/[provider]/metadataaddress             | 必須。 [!include[](../../../includes/pn-adfs-short.md)] (STS) サーバーの[ws-federation](https://msdn.microsoft.com/library/bb498017.aspx)メタデータ URL。 通常、パス:/Federationmetadata.xml/2007-06/Federationmetadata.xml で終わります。 例: `https://adfs.contoso.com/FederationMetadata/2007-06/FederationMetadata.xml`。 [!include[](../../../includes/proc-more-information.md)] [WsFederationAuthenticationOptions](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.metadataaddress.aspx) |  
| Authentication/SAML2/[provider]/AuthenticationType          | 必須。 OWIN authentication ミドルウェア型。 フェデレーションメタデータ XML のルートにある[entityID](https://docs.microsoft.com/azure/active-directory/develop/active-directory-federation-metadata)属性の値を指定します。 例: `https://adfs.contoso.com/adfs/services/trust`。 [!include[](../../../includes/proc-more-information.md)] [Authenticationoptions. AuthenticationType](https://msdn.microsoft.com/library/microsoft.owin.security.authenticationoptions.authenticationtype.aspx)                                                            |  
| Authentication/SAML2/[provider]/serviceproviderrealm<br>または <br>Authentication/SAML2/[provider]/Wtrealm                      | 必須。 [!include[](../../../includes/pn-adfs-short.md)] 証明書利用者の識別子。 例: `https://portal.contoso.com/`。 [!include[](../../../includes/proc-more-information.md)] [WsFederationAuthenticationOptions Wtrealm](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.wtrealm.aspx)                       |  
| Authentication/SAML2/[provider]/AssertionConsumerServiceUrl<br>または<br>Authentication/SAML2/[provider]/Wreply                       | 必須。 [!include[](../../../includes/pn-adfs-short.md)] SAML コンシューマーアサーションエンドポイント。 例: https://portal.contoso.com/signin-saml2。 [!include[](../../../includes/proc-more-information.md)] [WsFederationAuthenticationOptions](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.wreply.aspx)                                                                                                                                                                                                  |  
| Authentication/SAML2/[プロバイダー]/キャプション                     | しない. ユーザーがサインインユーザーインターフェイスに表示できるテキスト。 既定値: [プロバイダー]。 [!include[](../../../includes/proc-more-information.md)] [WsFederationAuthenticationOptions](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.caption.aspx)                |  
| Authentication/SAML2/[プロバイダ]/tcp/ip パス                | 認証コールバックを処理するオプションの制約付きパス。 [!include[](../../../includes/proc-more-information.md)] [WsFederationAuthenticationOptions パス](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.callbackpath.aspx)                                                                                                                                                                                                                      |  
| Authentication/SAML2/[provider]/backchanneltimeout          | バックチャネル通信のタイムアウト値。 例: 00:05:00 (5 分)。 [!include[](../../../includes/proc-more-information.md)] [WsFederationAuthenticationOptions timeout](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.backchanneltimeout.aspx)                                                                                                                                                                                                                   |  
| Authentication/SAML2/[provider]/UseTokenLifetime            | 認証セッションの有効期間 (cookie など) が認証トークンの有効期間と一致する必要があることを示します。 [WsFederationAuthenticationOptions を有効](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.usetokenlifetime.aspx)にします。                                                                                                                                                                               |  
| Authentication/SAML2/[provider]/AuthenticationMode          | OWIN 認証ミドルウェアモード。 [!include[](../../../includes/proc-more-information.md)] [Authenticationoptions. AuthenticationMode](https://msdn.microsoft.com/library/microsoft.owin.security.authenticationoptions.authenticationmode.aspx)                                                                                                                                                                                                                                                                              |  
| Authentication/SAML2/[provider]/SignInAsAuthenticationType  | ClaimsIdentity を作成するときに使用される AuthenticationType。 [!include[](../../../includes/proc-more-information.md)] [WsFederationAuthenticationOptions SignInAsAuthenticationType](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.signinasauthenticationtype.aspx)                                                                                                                                                                                                 |  
| Authentication/SAML2/[provider]/validオーディエンス              | 対象者の Url のコンマ区切りのリスト。 [Tokenvalidationparameters を [!include[](../../../includes/proc-more-information.md)] します。 allowedaudiences](https://msdn.microsoft.com/library/system.identitymodel.tokens.tokenvalidationparameters.allowedaudiences.aspx)                                                                                                                                                                                                                                                                          |  
| Authentication/SAML2/[プロバイダ]/clockskew                   | 時間を検証するときに適用するクロックスキュー。                                                                                                                                                                                                                                                                                                                                                                                          |
| Authentication/SAML2/[provider]/RequireExpirationTime       | トークンが有効期限の値を持つ必要があるかどうかを示す値。                                                                                                                                                                                                                                                                                                                                                                      |
| Authentication/SAML2/[プロバイダ]/validateaudience            | トークンの検証中に対象ユーザーを検証するかどうかを制御するブール値。                                                                                                                                                                                                                                                                                                                                                         |

### <a name="idp-initiated-sign-in"></a>IdP が開始したサインイン

[!include[](../../../includes/pn-adfs-short.md)] では、SAML 2.0[仕様](https://docs.oasis-open.org/security/saml/Post2.0/sstc-saml-tech-overview-2.0-cd-02.html#5.1.4.IdP-Initiated%20SSO:%20POST%20Binding|outline)の IdP によって開始される[シングルサインオン (SSO)](https://technet.microsoft.com/library/jj127245.aspx)プロファイルがサポートされています。 IdP によって開始された SAML 要求にポータル (サービスプロバイダー) が正常に応答するには、 [Relaystate](https://blogs.technet.com/b/askds/archive/2012/09/27/ad-fs-2-0-relaystate.aspx)パラメーターを適切にエンコードする必要があります。  

SAML RelayState パラメーターにエンコードされる基本文字列値は、 **ReturnUrl =/content/sub-content/** の形式にする必要があります。 **/content/sub-content/** は、ポータル (サービスプロバイダー) で移動する web ページへのパスです。 このパスは、ポータル上の任意の有効な web ページで置き換えることができます。 文字列値はエンコードされ、 **rpid =&lt;url でエンコードされた rpid&gt;& RelayState =&lt;url エンコードされた relaystate&gt;** という形式のコンテナー文字列に配置されます。 この文字列全体が再度エンコードされ、エンコードされた**RPID/RelayState&gt;<https://adfs.contoso.com/adfs/ls/idpinitiatedsignon.aspx?RelayState=&lt;URL>** 形式の別のコンテナーに追加されます。

たとえば、サービスプロバイダーのパス **/content/sub-content/** と証明書利用者 ID **https://portal.contoso.com/** を指定した場合は、次の手順で URL を作成します。

ReturnUrl =/content/sub-content/の値をエンコードします。

-   ReturnUrl% 2Fcontent% 2Fsub を取得するには

<!-- -->

-   値をエンコード https://portal.contoso.com/

<!-- -->

-   https %3 を取得するには、%2 F %2 F ポータル. contoso .com% 2F

<!-- -->

-   値 RPID = https %3 A %2 F %2 F portal. contoso .com% 2F & RelayState = ReturnUrl% 3D% 2Fcontent% 2Fsub% 2F をエンコードします。

<!-- -->

-   RPID %3 D https %2 5 3A %2 5 2F %2 5 2Fportal% 252F% 26RelayState% 3DReturnUrl% 252F% 252Fcontent% 252Fsub-content% 252F を取得するには

<!-- -->

-   AD FS IdP によって開始された SSO パスを前に付加して最終的な URL を取得する

<!-- -->

-   https://adfs.contoso.com/adfs/ls/idpinitiatedsignon.aspx?RelayState=RPID%3Dhttps%253A%252F%252Fportal.contoso.com%252F%26RelayState%3DReturnUrl%253D%252Fcontent%252Fsub-content%252F

次の [!INCLUDE[pn-powershell-short](../../../includes/pn-powershell-short.md)] スクリプトを使用すると、URL を作成できます (Get-IdPInitiatedUrl という名前のファイルに保存します)。

```
<#

.SYNOPSIS 

Constructs an IdP-initiated SSO URL to access a portal page on the service provider.

.PARAMETER path

The path to the portal page.

.PARAMETER rpid

The relying party identifier.

.PARAMETER adfsPath

The AD FS IdP initiated SSO page.

.EXAMPLE

PS C:\\> .\\Get-IdPInitiatedUrl.ps1 -path "/content/sub-content/" -rpid "https://portal.contoso.com/" -adfsPath "https://adfs.contoso.com/adfs/ls/idpinitiatedsignon.aspx"

#>

param

(

[parameter(mandatory=$true,position=0)]

$path,

[parameter(mandatory=$true,position=1)]

$rpid,

[parameter(position=2)]

$adfsPath = https://adfs.contoso.com/adfs/ls/idpinitiatedsignon.aspx

)

$state = ReturnUrl=$path

$encodedPath = [uri]::EscapeDataString($state)

$encodedRpid = [uri]::EscapeDataString($rpid)

$encodedPathRpid = [uri]::EscapeDataString("RPID=$encodedRpid&RelayState=$encodedPath")

$idpInitiatedUrl = {0}?RelayState={1} -f $adfsPath, $encodedPathRpid

Write-Output $idpInitiatedUrl
```

## <a name="saml-20-settings-for-includepn-azure-active-directoryincludespn-azure-active-directorymd"></a>[!INCLUDE[pn-azure-active-directory](../../../includes/pn-azure-active-directory.md)] の SAML 2.0 設定

前のセクションでは [!include[](../../../includes/pn-adfs-short.md)] を[[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] ad](https://msdn.microsoft.com/library/azure/mt168838.aspx)に適用することもできます。これは [!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] ad が標準の[SAML 2.0](https://msdn.microsoft.com/library/azure/dn195591.aspx)&ndash;準拠 IdP のように動作するためです。 開始するには、 [[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] 管理ポータル](https://msdn.microsoft.com/library/azure/hh967611.aspx#bkmk_azureportal)にサインインし、既存のディレクトリを作成または選択します。 ディレクトリが使用可能な場合は、手順に従ってアプリケーションをディレクトリに[追加](https://msdn.microsoft.com/library/azure/dn132599.aspx)します。  

1.  ディレクトリの **[アプリケーション]** メニューで、 **[追加]** を選択します。
2.  **[組織で開発中のアプリケーションを追加する]** を選択します。
3.  アプリケーションのカスタム名を指定し、[ **web アプリケーションまたは WEB API**の種類] を選択します。
4.  **[サインオン URL]** と **[アプリ ID URI]** には、 https://portal.contoso.com/の両方のフィールドにポータルの url を指定します。
    これは、 **Serviceproviderrealm** (Wtrealm) サイト設定値に対応します。
5. この時点で、新しいアプリケーションが作成されます。 メニューの **[構成]** セクションにアクセスします。

    [Single sign-on] \ (**シングルサインオン**\) セクションで、最初の**応答 url**エントリを更新して、 https://portal.contoso.com/signin-azure-adURL にパスを含めます。

    これは、 **AssertionConsumerServiceUrl** (wreply) サイト設定値に対応します。

6. フッターメニューで、 **[エンドポイントの表示]** を選択し、 **[フェデレーションメタデータドキュメント]** フィールドをメモします。

これは、 **Metadataaddress**サイト設定値に対応しています。

-   この URL をブラウザーウィンドウに貼り付けて、フェデレーションメタデータ XML を表示し、ルート要素の**entityID**属性を確認します。
-   これは、**AuthenticationType**サイト設定値に対応しています。

> [!Note]
> 標準 [!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] AD 構成では、次の設定 (値の例を含む) のみが使用されます。 Authentication/SAML2/[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD/MetadataAddress-<https://login.microsoftonline.com/01234567-89ab-cdef-0123-456789abcdef/federationmetadata/2007-06/federationmetadata.xml> 
> - Authentication/SAML2/[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD/AuthenticationType-<https://sts.windows.net/01234567-89ab-cdef-0123-456789abcdef/>  
> - フェデレーションメタデータのルート要素で**entityID**属性の値を使用します (上記のサイト設定の値であるブラウザーで**metadataaddress URL**を開きます)。 
> - Authentication/SAML2/[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD/ServiceProviderRealm-<https://portal.contoso.com/>  
> - Authentication/SAML2/[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD/AssertionConsumerServiceUrl-<https://portal.contoso.com/signin-azure-ad>                                                                                   |

## <a name="shibboleth-identity-provider-3"></a>Id プロバイダー3を持つ

IdP サービスとしての規則を正しく[構成するに](https://wiki.shibboleth.net/confluence/display/IDP30/Home)は、次のガイドラインに従います。 次の例では、IdP がドメイン https://idp.contoso.comでホストされていることを前提としています。  

フェデレーションメタデータ URL が https://idp.contoso.com/idp/shibboleth

-   IdP は、永続的な識別子を生成または提供するように構成する必要があります。 指示に従って、[永続的な識別子の生成](https://wiki.shibboleth.net/confluence/display/IDP30/NameIDGenerationConfiguration)を有効にします。  

-   IdP フェデレーションメタデータ (&lt;IDPSSODescriptor&gt;) は、 [SSO リダイレクトバインド](https://shibboleth.net/about/advanced.html)を含めるように構成する必要があります。 [例](https://wiki.shibboleth.net/confluence/display/SHIB2/MetadataExample)。  

```
<SingleSignOnService Binding="urn:oasis:names:tc:SAML:2.0:bindings:HTTP-Redirect"

Location=https://idp.contoso.com/idp/profile/SAML2/Redirect/SSO/>
```

[Metadata-providers](https://wiki.shibboleth.net/confluence/display/IDP30/MetadataConfiguration)を設定して、サービスプロバイダー (証明書利用者) を構成します。  

-   各サービスプロバイダーのフェデレーションメタデータ (&lt;Spの&gt;) には、Assertion Consumer Service ポストバインドが含まれている必要があります。 1つの方法として、 [Filesystemmetadataprovider](https://wiki.shibboleth.net/confluence/display/IDP30/FilesystemMetadataProvider)を使用し、次のものを含む構成ファイルを参照します。  

```
<AssertionConsumerService index=1 isDefault=true

Binding="urn:oasis:names:tc:SAML:2.0:bindings:HTTP-POST"

Location=https://portal.contoso.com/signin-saml2/>
```

Location 属性は、**AssertionConsumerServiceUrl** (wreply) 設定に対応しています。

-   サービスプロバイダーのフェデレーションメタデータでは、 **AuthenticationType**の設定に対応する Entitydescriptor の**entityID**属性を指定する必要があります。

**&lt;EntityDescriptor entityID =<https://portal.local.contoso.com/&gt>;...**

> [!Note] 
> 標準の "指定された Bboleth" 構成では、次の設定のみが使用されます (値の例を含む)。   
> Authentication/SAML2 https://idp.contoso.com/idp/shibboleth///   
> -   Authentication/SAML2//AuthenticationType- https://idp.contoso.com/idp/shibboleth 
> -   フェデレーションメタデータのルート要素で**entityID**属性の値を使用します (上記のサイト設定の値であるブラウザーで**metadataaddress URL**を開きます)。  
> -   Authentication/SAML2///https://portal.contoso.com////////// 
> -   Authentication/SAML2//AssertionConsumerServiceUrl- https://portal.contoso.com/signin-saml2 

### <a name="idp-initiated-sign-in"></a>IdP が開始したサインイン

IdP は、SAML 2.0[仕様](https://docs.oasis-open.org/security/saml/Post2.0/sstc-saml-tech-overview-2.0-cd-02.html#5.1.4.IdP-Initiated%20SSO:%20POST%20Binding|outline)で開始された[SSO](https://wiki.shibboleth.net/confluence/display/SHIB2/IdPUnsolicitedSSO)プロファイルをサポートしています。 IdP によって開始された SAML 要求にポータル (サービスプロバイダー) が正常に応答するには、RelayState パラメーターを適切にエンコードする必要があります。  

SAML RelayState パラメーターにエンコードされる基本文字列値は、 **ReturnUrl =/content/sub-content/** の形式にする必要があります。 **/content/sub-content/** は、ポータル (サービスプロバイダー) で移動する web ページへのパスです。 このパスは、ポータル上の任意の有効な web ページで置き換えることができます。 完全な IdP によって開始される SSO URL は <https://idp.contoso.com/idp/profile/SAML2/Unsolicited/SSO?providerId=&lt;URL> エンコードされたプロバイダー ID&gt;& target =&lt;URL でエンコードされたリターンパス&gt;の形式である必要があります。

たとえば、サービスプロバイダーのパス **/content/sub-content/** と証明書利用者の ID が指定されている場合、最終的な URL は https://idp.contoso.com/idp/profile/SAML2/Unsolicited/SSO?providerId=https%3A%2F%2Fportal.contoso.com%2F&target=ReturnUrl%3D%2Fcontent%2Fsub-content%2F **https://portal.contoso.com/**

次の [!INCLUDE[pn-powershell-short](../../../includes/pn-powershell-short.md)] スクリプトを使用すると、URL を作成できます (Get-ShibbolethIdPInitiatedUrl という名前のファイルに保存します)。

```
<# 

.SYNOPSIS

Constructs an IdP initiated SSO URL to access a portal page on the service provider.

.PARAMETER path

The path to the portal page.

.PARAMETER providerId

The relying party identifier.

.PARAMETER shibbolethPath

The Shibboleth IdP-initiated SSO page.

.EXAMPLE

PS C:\\> .\\Get-ShibbolethIdPInitiatedUrl.ps1 -path "/content/sub-content/" -providerId "https://portal.contoso.com/" -shibbolethPath "https://idp.contoso.com/idp/profile/SAML2/Unsolicited/SSO"

#>

param

(

[parameter(mandatory=$true,position=0)]

$path,

[parameter(mandatory=$true,position=1)]

$providerId,

[parameter(position=2)]

$shibbolethPath = https://idp.contoso.com/idp/profile/SAML2/Unsolicited/SSO

)

$state = ReturnUrl=$path

$encodedPath = [uri]::EscapeDataString($state)

$encodedRpid = [uri]::EscapeDataString($providerId)

$idpInitiatedUrl = {0}?providerId={1}&target={2} -f $shibbolethPath, $encodedRpid, $encodedPath

Write-Output $idpInitiatedUrl
```

## <a name="configure-ad-fs-by-using-powershell"></a>PowerShell を使用した AD FS の構成

[!include[](../../../includes/pn-adfs-short.md)] で証明書利用者信頼を追加するプロセスは、[!include[](../../../includes/pn-adfs-short.md)] サーバーで次の [!INCLUDE[pn-powershell-short](../../../includes/pn-powershell-short.md)] スクリプトを実行することによっても実行できます (内容を Add-AdxPortalRelyingPartyTrustForSaml という名前のファイルに保存します)。 スクリプトを実行した後、ポータルサイト設定の構成を続行します。

```
<# 

.SYNOPSIS

Adds a SAML 2.0 relying party trust entry for a website.

.PARAMETER domain

The domain name of the portal.

.EXAMPLE

PS C:\\> .\\Add-AdxPortalRelyingPartyTrustForSaml.ps1 -domain portal.contoso.com

#>

param

(

[parameter(Mandatory=$true,Position=0)]

$domain,

[parameter(Position=1)]

$callbackPath = /signin-saml2

)

$VerbosePreference = Continue

$ErrorActionPreference = Stop

Import-Module adfs

Function Add-CrmRelyingPartyTrust

{

param (

[parameter(Mandatory=$true,Position=0)]

$name

)

$identifier = https://{0}/ -f $name

$samlEndpoint = New-ADFSSamlEndpoint -Binding POST -Protocol SAMLAssertionConsumer -Uri (https://{0}{1} -f $name, $callbackPath)

$identityProviderValue = Get-ADFSProperties | % { $_.Identifier.AbsoluteUri }

$issuanceTransformRules = @'

@RuleTemplate = MapClaims

@RuleName = Transform [!INCLUDE[pn-ms-windows-short](../../../includes/pn-ms-windows-short.md)] Account Name to Name ID claim

c:[Type == "https://schemas.microsoft.com/ws/2008/06/identity/claims/windowsaccountname"]

=> issue(Type = "https://schemas.xmlsoap.org/ws/2005/05/identity/claims/nameidentifier", Issuer = c.Issuer, OriginalIssuer = c.OriginalIssuer, Value = c.Value, ValueType = c.ValueType, Properties["https://schemas.xmlsoap.org/ws/2005/05/identity/claimproperties/format"] = "urn:oasis:names:tc:SAML:2.0:nameid-format:persistent");

@RuleTemplate = LdapClaims

@RuleName = Send LDAP Claims

c:[Type == "https://schemas.microsoft.com/ws/2008/06/identity/claims/windowsaccountname", Issuer == "AD AUTHORITY"]

=> issue(store = "[!INCLUDE[pn-active-directory](../../../includes/pn-active-directory.md)]", types = ("https://schemas.xmlsoap.org/ws/2005/05/identity/claims/givenname", "https://schemas.xmlsoap.org/ws/2005/05/identity/claims/surname", "https://schemas.xmlsoap.org/ws/2005/05/identity/claims/emailaddress"), query = ";givenName,sn,mail;{{0}}", param = c.Value);

'@ -f $identityProviderValue

$issuanceAuthorizationRules = @'

@RuleTemplate = AllowAllAuthzRule

=> issue(Type = https://schemas.microsoft.com/authorization/claims/permit, Value = true);

'@

Add-ADFSRelyingPartyTrust -Name $name -Identifier $identifier -SamlEndpoint $samlEndpoint -IssuanceTransformRules $issuanceTransformRules -IssuanceAuthorizationRules $issuanceAuthorizationRules

}

# add the 'Identity Provider' claim description if it is missing

if (-not (Get-ADFSClaimDescription | ? { $_.Name -eq Persistent Identifier })) {

Add-ADFSClaimDescription -name "Persistent Identifier" -ClaimType "urn:oasis:names:tc:SAML:2.0:nameid-format:persistent" -IsOffered:$true -IsAccepted:$true

}

# add the portal relying party trust

Add-CrmRelyingPartyTrust $domain
```

### <a name="see-also"></a>関連項目

[ポータル認証を構成する](configure-portal-authentication.md)  
[ポータルの認証 id を設定する](set-authentication-identity.md)  
[ポータルの OAuth2 プロバイダーの設定](configure-oauth2-settings.md)  
[ポータルの Open ID Connect プロバイダー設定](configure-openid-settings.md)  
[ポータルの WS-FEDERATION プロバイダーの設定](configure-ws-federation-settings.md)  
