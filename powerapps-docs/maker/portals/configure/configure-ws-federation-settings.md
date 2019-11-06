---
title: ポータルの WS-FEDERATION プロバイダー設定を構成する |MicrosoftDocs
description: ポータルの WS-FEDERATION プロバイダー設定を追加して構成する方法について説明します。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/18/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 2a668f501a54472da0335344997c049794794783
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2019
ms.locfileid: "73542706"
---
# <a name="configure-ws-federation-provider-settings-for-portals"></a>ポータルの WS-FEDERATION プロバイダー設定を構成する

1つの [!INCLUDE[pn-active-directory](../../../includes/pn-active-directory.md)] フェデレーションサービスサーバーを id プロバイダーとして追加 (または他の[ws-federation](https://msdn.microsoft.com/library/bb498017.aspx)準拠の Security Token Service) できます。 また、1つの[[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] ACS](https://azure.microsoft.com/documentation/articles/active-directory-dotnet-how-to-use-access-control/)名前空間を個々の id プロバイダーのセットとして構成することもできます。 AD FS と ACS の両方の設定は、 [WsFederationAuthenticationOptions](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.aspx)クラスのプロパティに基づいています。

## <a name="create-an-ad-fs-relying-party-trust"></a>AD FS 証明書利用者信頼を作成する

AD FS 管理ツールを使用して、**信頼関係**&gt;**証明書利用者信頼**にアクセスします。

1.  **[証明書利用者信頼の追加]** を選択します。
2.  ようこそ: **開始** を選択します。
3.  データソースの選択: **証明書利用者に関するデータを手動で入力する** を選択し、**次へ** を選択します。
4.  [表示名の指定]:**名前**を入力し、 **[次へ]** を選択します。
    例: https://portal.contoso.com/
5.  プロファイルの選択:  **AD FS 2.0 プロファイル** を選択し、**次へ** を選択します。
6.  証明書の構成: **[次へ]** を選択します。
7.  URL の構成: **[Ws-federation パッシブプロトコルのサポートを有効にする]** チェックボックスをオンにします。

証明書利用者 WS-FEDERATION パッシブプロトコル URL: 「 https://portal.contoso.com/signin-federation 」と入力します。

-   注: AD FS には、ポータルを**HTTPS**で実行する必要があります。

    > [!Note]
    > 作成されるエンドポイントの設定は次のとおりです。エンドポイントの種類: **ws-federation**
    > -   バインド: **POST**
    > -   インデックス: n/a (0)
    > -   URL: **https://portal.contoso.com/signin-federation**

8.  Id の構成: https://portal.contoso.com/ を指定し、 **[追加]** を選択して、 **[次へ]** を選択します。
    該当する場合は、追加の証明書利用者ポータルごとにさらに多くの id を追加できます。 ユーザーは、使用可能なすべての id に対して認証できるようになります。
9.  発行承認規則を選択する: **[すべてのユーザーにこの証明書利用者へのアクセスを許可する]** を選択し、 **[次へ]** を選択します。
10.  信頼の追加の準備完了: **[次へ]** を選択します。
11.  **[閉じる]** を選びます。

**名前 ID**要求を証明書利用者信頼に追加します。

**[!INCLUDE[pn-ms-windows-short](../../../includes/pn-ms-windows-short.md)] アカウント名**を**名前 ID**要求 (入力方向の要求の変換) に変換します。
- 入力方向の要求の種類: Windows アカウント名
- 出力方向の要求の種類: 名前 ID
- 発信名 ID の形式: 指定されていません
- すべての要求値をパススルーする

### <a name="create-ad-fs-site-settings"></a>AD FS サイト設定の作成

上記の AD FS 証明書利用者信頼を参照するポータルサイト設定を適用します。

> [!Note]
> 標準 AD FS (STS) 構成では、次の設定のみが使用されます (値の例を含む)。
> - Authentication/WsFederation/ADFS/MetadataAddress- https://adfs.contoso.com/FederationMetadata/2007-06/FederationMetadata.xml
> - Authentication/WsFederation/ADFS/AuthenticationType- https://adfs.contoso.com/adfs/services/trust
>   - フェデレーションメタデータのルート要素で**entityID**属性の値を使用します (上記のサイト設定の値であるブラウザーで**metadataaddress URL**を開きます)。
> - Authentication/WsFederation/ADFS/Wtrealm- https://portal.contoso.com/
> - Authentication/WsFederation/ADFS/Wreply- https://portal.contoso.com/signin-federation

**Ws-federation メタデータ**は、AD FS サーバーで次のスクリプトを実行して **[!INCLUDE[pn-powershell-short](../../../includes/pn-powershell-short.md)]** で取得できます。

```
Import-Module adfs
Get-ADFSEndpoint -AddressPath /FederationMetadata/2007-06/FederationMetadata.xml
```


|                      サイト設定名                      |                                                                                                                                                                                                                                                 Description                                                                                                                                                                                                                                                 |
|-------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|      認証/登録/ExternalLoginEnabled       |                                                                                                                                                                                                                外部アカウントのサインインと登録を有効または無効にします。 既定値: true                                                                                                                                                                                                                 |
|      Authentication/WsFederation/ADFS/MetadataAddress       | 必須。 AD FS (STS) サーバーの[ws-federation](https://msdn.microsoft.com/library/bb498017.aspx)メタデータ URL。 通常、パス:/Federationmetadata.xml/2007-06/Federationmetadata.xml で終わります。 例:<https://adfs.contoso.com/FederationMetadata/2007-06/FederationMetadata.xml>。 詳細については、「 [WsFederationAuthenticationOptions](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.metadataaddress.aspx)」を参照してください。 |
|     Authentication/WsFederation/ADFS/AuthenticationType     |            必須。 OWIN authentication ミドルウェア型。 フェデレーションメタデータ XML のルートにある[entityID](https://docs.microsoft.com/azure/active-directory/develop/active-directory-federation-metadata)属性の値を指定します。 例: https://adfs.contoso.com/adfs/services/trust 。 詳細については、「 [Authenticationoptions. AuthenticationType](https://msdn.microsoft.com/library/microsoft.owin.security.authenticationoptions.authenticationtype.aspx)」を参照してください。             |
|          Authentication/WsFederation/ADFS/Wtrealm           |                                                                                                              必須。 AD FS 証明書利用者の識別子。 例: `https://portal.contoso.com/`。 詳細については、「 [WsFederationAuthenticationOptions. Wtrealm](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.wtrealm.aspx)」を参照してください。                                                                                                               |
|           Authentication/WsFederation/ADFS/Wreply           |                                                                                                     必須。 AD FS WS-FEDERATION パッシブエンドポイント。 例: https://portal.contoso.com/signin-federation 。 詳細については、「 [WsFederationAuthenticationOptions](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.wreply.aspx)」を参照してください。                                                                                                     |
|          Authentication/WsFederation/ADFS/キャプション           |                                                                                                           しない. ユーザーがサインインユーザーインターフェイスに表示できるテキスト。 既定値: ADFS。 詳細については、「 [WsFederationAuthenticationOptions](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.caption.aspx)」を参照してください。                                                                                                            |
|        Authentication/WsFederation/ADFS//のパス        |                                                                                                             認証コールバックを処理するオプションの制約付きパス。 詳細については、「 [WsFederationAuthenticationOptions path](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.callbackpath.aspx)」を参照してください。                                                                                                              |
|       Authentication/WsFederation/ADFS/SignOutWreply        |                                                                                                                               サインアウト時に使用される ' wreply ' 値。詳細については、「 [WsFederationAuthenticationOptions. SignOutWreply](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.signoutwreply.aspx)」を参照してください。                                                                                                                               |
|     Authentication/WsFederation/ADFS/BackchannelTimeout     |                                                                                                         バックチャネル通信のタイムアウト値。 例: 00:05:00 (5 分)。 詳細については、「 [WsFederationAuthenticationOptions](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.backchanneltimeout.aspx)」を参照してください。                                                                                                         |
| Authentication/WsFederation/ADFS/RefreshOnIssuerKeyNotFound |                                                                                  SecurityTokenSignatureKeyNotFoundException の後にメタデータの更新を試行するかどうかを決定します。 詳細については、「 [WsFederationAuthenticationOptions. RefreshOnIssuerKeyNotFound](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.refreshonissuerkeynotfound.aspx)」を参照してください。                                                                                  |
|      Authentication/WsFederation/ADFS/UseTokenLifetime      |                                                                                                   認証セッションの有効期間 (cookie など) が認証トークンの有効期間と一致する必要があることを示します。 [WsFederationAuthenticationOptions を有効](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.usetokenlifetime.aspx)にします。                                                                                                   |
|     Authentication/WsFederation/ADFS/AuthenticationMode     |                                                                                                                                            OWIN 認証ミドルウェアモード。 詳細については、「 [Authenticationoptions](https://msdn.microsoft.com/library/microsoft.owin.security.authenticationoptions.authenticationmode.aspx)」を参照してください。                                                                                                                                             |
| Authentication/WsFederation/ADFS/SignInAsAuthenticationType |                                                                                            ClaimsIdentity を作成するときに使用される AuthenticationType。 詳細については、「 [WsFederationAuthenticationOptions. SignInAsAuthenticationType](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.signinasauthenticationtype.aspx)」を参照してください。                                                                                            |
|       Authentication/WsFederation/ADFS/ValidAudiences       |                                                                                                                                         対象者の Url のコンマ区切りの一覧。 詳細については、「 [Tokenvalidationparameters. allowedaudiences](https://msdn.microsoft.com/library/system.identitymodel.tokens.tokenvalidationparameters.allowedaudiences.aspx)」を参照してください。                                                                                                                                          |
|        Authentication/WsFederation/ADFS/ValidIssuers        |                                                                                                                                              発行者の Url のコンマ区切りの一覧。 詳細については、「 [Tokenvalidationparameters. ValidIssuers](https://msdn.microsoft.com/library/system.identitymodel.tokens.tokenvalidationparameters.validissuers.aspx)」を参照してください。                                                                                                                                               |
|         Authentication/WsFederation/ADFS/ClockSkew          |                                                                                                                                                                                                                               時間を検証するときに適用するクロックスキュー。                                                                                                                                                                                                                                |
|       Authentication/WsFederation/ADFS/NameClaimType        |                                                                                                                                                                                                                     名前クレームを格納するために ClaimsIdentity によって使用される要求の種類。                                                                                                                                                                                                                      |
|       Authentication/WsFederation/ADFS/RoleClaimType        |                                                                                                                                                                                                                     ロール要求を格納するために ClaimsIdentity によって使用される要求の種類。                                                                                                                                                                                                                      |
|   Authentication/WsFederation/ADFS/RequireExpirationTime    |                                                                                                                                                                                                                     トークンが "有効期限" の値を持つ必要があるかどうかを示す値。                                                                                                                                                                                                                      |
|    Authentication/WsFederation/ADFS/RequireSignedTokens     |                                                                                                                                                                       署名されていない場合に、<https://ddue.schemas.microsoft.com/authoring/2003/5> が有効であるかどうかを示す値。                                                                                                                                                                       |
|      Authentication/WsFederation/ADFS/SaveSigninToken       |                                                                                                                                                                                                               セッションの作成時に元のトークンが保存されるかどうかを制御するブール値。                                                                                                                                                                                                                |
|       Authentication/WsFederation/ADFS/ValidateActor        |                                                                                                                                                                                                   JwtSecurityToken を検証する必要があるかどうかを示す値。                                                                                                                                                                                                    |
|      Authentication/WsFederation/ADFS/ValidateAudience      |                                                                                                                                                                                                               トークンの検証中に対象ユーザーを検証するかどうかを制御するブール値。                                                                                                                                                                                                               |
|       Authentication/WsFederation/ADFS/ValidateIssuer       |                                                                                                                                                                                                                トークンの検証中に発行者が検証されるかどうかを制御するブール値。                                                                                                                                                                                                                |
|      Authentication/WsFederation/ADFS/ValidateLifetime      |                                                                                                                                                                                                               トークンの検証中に有効期間が検証されるかどうかを制御するブール値。                                                                                                                                                                                                               |
|  Authentication/WsFederation/ADFS/ValidateIssuerSigningKey  |                                                                                                                                                         (SecurityToken xmlns =<https://ddue.schemas.microsoft.com/authoring/2003/5> に署名されている、system.servicemodel. SecurityKey) の検証が呼び出されるかどうかを制御するブール値。                                                                                                                                                          |
|            Authentication/WsFederation/ADFS/Whr             |                                                                                                                                       Id プロバイダーのリダイレクト URL に "whr" パラメーターを指定します。 詳細については、「 [Wsfederation](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/windows-identity-foundation/wsfederation)」を参照してください。                                                                                                                                       |

## <a name="ws-federation-settings-for-includepn-azure-active-directoryincludespn-azure-active-directorymd"></a>[!INCLUDE[pn-azure-active-directory](../../../includes/pn-azure-active-directory.md)] の WS-FEDERATION 設定

前のセクションでは、AD FS について説明します。これは、[!INCLUDE[pn-azure-active-directory](../../../includes/pn-azure-active-directory.md)] ([[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] ad](https://msdn.microsoft.com/library/azure/mt168838.aspx)) にも適用できます。これは、[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] ad は、標準の[ws-federation](https://docs.microsoft.com/azure/active-directory/develop/active-directory-developers-guide)準拠の Security Token Service のように動作するためです。 まず、 [[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] 管理ポータル](https://msdn.microsoft.com/library/azure/hh967611.aspx#bkmk_azureportal)にサインインし、既存のディレクトリを作成または選択します。 ディレクトリが使用可能な場合は、手順に従って、ディレクトリに[アプリケーションを追加](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications)します。

1.  ディレクトリの **[アプリケーション]** メニューで、 **[追加]** を選択します。
2.  **[組織で開発中のアプリケーションを追加する]** を選択します。
3.  アプリケーションのカスタム**名**を指定し、[ **web アプリケーションまたは web API**の種類] を選択します。
4.  **[サインオン URL]** と **[アプリ ID URI]** には、 https://portal.contoso.com/ の両方のフィールドにポータルの url を指定します。
    - これは、 **Wtrealm**サイト設定値に対応します。
5.  この時点で、新しいアプリケーションが作成されます。 メニューの **[構成]** セクションにアクセスします。
6.  [Single sign-on] \ (**シングルサインオン**\) セクションで、最初の**応答 url**エントリを更新して、 https://portal.contoso.com/signin-azure-ad URL にパスを含めます。
    - これは、 **Wreply**サイト設定値に対応します。
7.  フッターの **[保存]** を選択します。
8.  フッターメニューで、 **[エンドポイントの表示]** を選択し、 **[フェデレーションメタデータドキュメント]** フィールドをメモします。

    - これは、 **Metadataaddress**サイト設定値に対応しています。
    - この URL をブラウザーウィンドウに貼り付けて、フェデレーションメタデータ XML を表示し、ルート要素の**entityID**属性を確認します。
    - これは、 **AuthenticationType**サイト設定値に対応しています。

> [!Note]
> 標準 [!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] AD 構成では、次の設定のみが使用されます (値の例を含む)。
> - Authentication/WsFederation/ADFS/MetadataAddress- https://login.microsoftonline.com/01234567-89ab-cdef-0123-456789abcdef/federationmetadata/2007-06/federationmetadata.xml
> - Authentication/WsFederation/ADFS/AuthenticationType- https://sts.windows.net/01234567-89ab-cdef-0123-456789abcdef/
>   - フェデレーションメタデータのルート要素で**entityID**属性の値を使用します (上記のサイト設定の値であるブラウザーで**metadataaddress URL**を開きます)。
> - Authentication/WsFederation/ADFS/Wtrealm- https://portal.contoso.com/
> - Authentication/WsFederation/ADFS/Wreply- https://portal.contoso.com/signin-azure-ad

### <a name="see-also"></a>関連項目

[ポータル認証を構成する](configure-portal-authentication.md)  
[ポータルの認証 id を設定する](set-authentication-identity.md)  
[ポータルの OAuth2 プロバイダーの設定](configure-oauth2-settings.md)  
[ポータルの Open ID Connect プロバイダー設定](configure-openid-settings.md)  
[ポータルの SAML 2.0 プロバイダー設定](configure-saml2-settings.md)  
