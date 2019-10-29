---
title: ポータルの OpenID Connect プロバイダー設定を構成する |MicrosoftDocs
description: ポータルに OpenID Connect プロバイダー設定を追加して構成する方法について説明します。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/18/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 0dba1794f15a710e43feaec3ca6d4d2dbc9c5fc3
ms.sourcegitcommit: 57b968b542fc43737330596d840d938f566e582a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2019
ms.locfileid: "72978487"
---
# <a name="configure-open-id-connect-provider-settings-for-portals"></a>ポータルの Open ID Connect プロバイダーの設定を構成する

[OpenID connect](http://openid.net/connect/)外部 id プロバイダーは、Open ID Connect[仕様](http://openid.net/developers/specs/)に準拠するサービスです。 プロバイダーを統合するには、プロバイダーに関連付けられている機関 (または発行者) の URL を検索する必要があります。 構成 URL は、認証ワークフロー中に必要なメタデータを提供する機関から特定できます。 プロバイダーの設定は、 [Openidconnectauthenticationoptions](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.aspx)クラスのプロパティに基づいています。

権限の Url の例を次に示します。

- [Google](https://developers.google.com/identity/protocols/OpenIDConnect): <https://accounts.google.com/><https://accounts.google.com/.well-known/openid-configuration>
- [[!INCLUDE[pn-azure-active-directory](../../../includes/pn-azure-active-directory.md)]](https://msdn.microsoft.com/library/azure/mt168838.aspx): [https://login.microsoftonline.com/&lt 、[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] AD アプリケーション&gt;/](https://login.microsoftonline.com/contoso.onmicrosoft.com/.well-known/openid-configuration)

各 OpenID Connect プロバイダーには、アプリケーションの登録 (OAuth 2.0 プロバイダーの場合と同様) とクライアント Id の取得も含まれます。機関の URL と生成されるアプリケーションクライアント Id は、ポータルと id プロバイダーの間で外部認証を有効にするために必要な設定です。

> [!Note]
> 現在、基になるライブラリが互換性の問題があるリリースの初期段階にあるため、Google OpenID Connect エンドポイントはサポートされていません。 代わりに、ポータルエンドポイント[の OAuth2 プロバイダー設定](configure-oauth2-settings.md)を使用できます。

## <a name="openid-settings-for-includepn-azure-active-directoryincludespn-azure-active-directorymd"></a>[!INCLUDE[pn-azure-active-directory](../../../includes/pn-azure-active-directory.md)] の OpenID 設定

開始するには、 [[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] 管理ポータル](https://msdn.microsoft.com/library/azure/hh967611.aspx#bkmk_azureportal)にサインインし、既存のディレクトリを作成または選択します。 ディレクトリが使用可能な場合は、手順に従って、ディレクトリに[アプリケーションを追加](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications)します。  

1. ディレクトリの **[アプリケーション]** メニューで、 **[追加]** を選択します。
2. **[組織で開発中のアプリケーションを追加する]** を選択します。
3. アプリケーションのカスタム**名**を指定し、種類として **[web アプリケーションや web API]** を選択します。
4. **[サインオン URL]** と **[アプリ ID URI]** には、両方のフィールドにポータルの url を指定し https://portal.contoso.com/
5. この時点で、新しいアプリケーションが作成されます。 メニューの **[構成]** セクションに移動します。

    [Single sign-on] \ (**シングルサインオン**\) セクションで、最初の**応答 url**エントリを更新して、url: http://portal.contoso.com/signin-azure-ad にパスを含めます。 これは、 **Redirecturi**サイト設定値に対応します。

6. **[プロパティ]** セクションで、 **[クライアント ID]** フィールドを見つけます。 これは、 **ClientId**サイト設定値に対応しています。
7. フッターメニューで、 **[エンドポイントの表示]** を選択し、 **[フェデレーションメタデータドキュメント]** フィールドをメモします。

URL の左側の部分は**Authority**の値であり、次のいずれかの形式になっています。

- https://login.microsoftonline.com/01234567-89ab-cdef-0123-456789abcdef/
- https://login.microsoftonline.com/contoso.onmicrosoft.com/

サービス構成 URL を取得するには、Federationmetadata.xml/2007-06/Federationmetadata.xml パスの末尾をパスの well-known/openid 構成に置き換えます。 たとえば、<https://login.microsoftonline.com/contoso.onmicrosoft.com/.well-known/openid-configuration>

これは、 **Metadataaddress**サイト設定値に対応しています。

### <a name="related-site-settings"></a>関連サイトの設定

上記のアプリケーションを参照しているポータルサイト設定を適用します。

> [!Note]
> 標準 [!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] AD 構成では、次の設定のみが使用されます (値の例を含む)。                                 
> - Authentication/OpenIdConnect/[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD/Authority-<https://login.microsoftonline.com/01234567-89ab-cdef-0123-456789abcdef/>                                                    
> - Authentication/OpenIdConnect/[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD/ClientId-fedcba98-7654-3210-fedc-ba9876543210                                      
>   クライアント ID と機関 URL は同じ値を含んでいないため、個別に取得する必要があります。           
> - Authentication/OpenIdConnect/[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD/RedirectUri- https://portal.contoso.com/signin-azure-ad
 
\[プロバイダーの\] タグのラベルを置き換えることで、複数の id プロバイダーを構成できます。 一意の各ラベルは、id プロバイダーに関連する設定のグループを形成します。 例: [!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD、MyIdP


|                          サイト設定名                           |                                                                                                                                                                                                         Description                                                                                                                                                                                                          |
|----------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|           認証/登録/ExternalLoginEnabled           |                                                                                                                                                                         外部アカウントのサインインと登録を有効または無効にします。 既定値: true                                                                                                                                                                         |
|         Authentication/OpenIdConnect/\[プロバイダー\]/機関          |                                               必須。 OpenIdConnect 呼び出しを行うときに使用する機関。 例: `https://login.microsoftonline.com/contoso.onmicrosoft.com/`。 詳細については、「[Openidconnectauthenticationoptions](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.authority.aspx)」を参照してください。                                                |
|      Authentication/OpenIdConnect/\[プロバイダー\]/metadataaddress       | メタデータを取得するための探索エンドポイント。 通常、パス:/. well-known/openid-configuration で終わります。 例: `https://login.microsoftonline.com/contoso.onmicrosoft.com/.well-known/openid-configuration`。 詳細については、「[Openidconnectauthenticationoptions. MetadataAddress](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.metadataaddress.aspx)」を参照してください。 |
|     Authentication/OpenIdConnect/\[プロバイダー\]/AuthenticationType     |                                   OWIN authentication ミドルウェア型。 サービス構成メタデータの発行者の値を指定します。 例: `https://sts.windows.net/contoso.onmicrosoft.com/`。 詳細については、「 [Authenticationoptions. AuthenticationType](https://msdn.microsoft.com/library/microsoft.owin.security.authenticationoptions.authenticationtype.aspx)」を参照してください。                                   |
|          Authentication/OpenIdConnect/\[プロバイダー\]/ClientId          |                                                  必須。 プロバイダーアプリケーションからのクライアント ID 値。 "アプリ ID" または "コンシューマーキー" と呼ばれることもあります。 詳細については、「 [Openidconnectauthenticationoptions. ClientId](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.clientid.aspx)」を参照してください。                                                   |
|        Authentication/OpenIdConnect/\[プロバイダー\]/clientsecret        |                                              プロバイダーアプリケーションからのクライアントシークレット値。 "アプリシークレット" または "コンシューマーシークレット" と呼ばれることもあります。 詳細については、「 [Openidconnectauthenticationoptions. ClientSecret](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.clientsecret.aspx)」を参照してください。                                              |
|        Authentication/OpenIdConnect/\[プロバイダー\]/redirecturi         |                                                        しない. AD FS WS-FEDERATION パッシブエンドポイント。 例: https://portal.contoso.com/signin-saml2 。 詳細については、「 [Openidconnectauthenticationoptions. RedirectUri](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.redirecturi.aspx)」を参照してください。                                                        |
|          Authentication/OpenIdConnect/\[プロバイダー\]/キャプション           |                                                              しない. ユーザーがサインインユーザーインターフェイスに表示できるテキスト。 既定値: \[プロバイダー\]です。 詳細については、「 [Openidconnectauthenticationoptions](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.caption.aspx)」を参照してください。                                                               |
|          Authentication/OpenIdConnect/\[プロバイダー\]/Resource          |                                                                                                       ' Resource '。 詳細については、「 [Openidconnectauthenticationoptions. Resource](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.resource.aspx)」を参照してください。                                                                                                        |
|        Authentication/OpenIdConnect/\[プロバイダー\]/responsetype        |                                                                                                ' Response\_type ' です。 詳細については、「 [Openidconnectauthenticationoptions. ResponseType](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.responsetype.aspx)」を参照してください。                                                                                                 |
|           Authentication/OpenIdConnect/\[provider\]/Scope            |                                                                                要求するアクセス許可のスペースで区切られた一覧。 既定値: openid。 詳細については、「 [Openidconnectauthenticationoptions. スコープ](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.scope.aspx)」を参照してください。                                                                                 |
|        Authentication/OpenIdConnect/\[プロバイダー\]/tcp/ip パス        |                      認証コールバックを処理するオプションの制約付きパス。 指定されておらず、RedirectUri が使用可能な場合は、RedirectUri からこの値が生成されます。 詳細については、「 [Openidconnectauthenticationoptions. のパス](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.callbackpath.aspx)」を参照してください。                      |
|     Authentication/OpenIdConnect/\[プロバイダー\]/backchanneltimeout     |                                                                バックチャネル通信のタイムアウト値。 例: 00:05:00 (5 分)。 詳細については、「 [Openidconnectauthenticationoptions. BackchannelTimeout](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.backchanneltimeout.aspx)」を参照してください。                                                                |
| Authentication/OpenIdConnect/\[プロバイダー\]/RefreshOnIssuerKeyNotFound |                                      SecurityTokenSignatureKeyNotFoundException の後にメタデータの更新を試行するかどうかを決定します。 詳細については、「 [Openidconnectauthenticationoptions. RefreshOnIssuerKeyNotFound](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.refreshonissuerkeynotfound.aspx)」を参照してください。                                       |
|      Authentication/OpenIdConnect/\[プロバイダー\]/UseTokenLifetime      |                                               認証セッションの有効期間 (cookie など) が認証トークンの有効期間と一致する必要があることを示します。 詳細については、「 [Openidconnectauthenticationoptions](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.usetokenlifetime.aspx)」を参照してください。                                               |
|     Authentication/OpenIdConnect/\[プロバイダー\]/AuthenticationMode     |                                                                                                     OWIN 認証ミドルウェアモード。 詳細については、「 [Authenticationoptions](https://msdn.microsoft.com/library/microsoft.owin.security.authenticationoptions.authenticationmode.aspx)」を参照してください。                                                                                                     |
| Authentication/OpenIdConnect/\[プロバイダー\]/SignInAsAuthenticationType |                                                   ClaimsIdentity を作成するときに使用される AuthenticationType。 詳細については、「 [Openidconnectauthenticationoptions. SignInAsAuthenticationType](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.signinasauthenticationtype.aspx)」を参照してください。                                                   |
|   Authentication/OpenIdConnect/\[プロバイダー\]/postlogoutredirecturi    |                                                                                 ' Post\_logout\_redirect\_uri ' です。 詳細については、「 [Openidconnectauthenticationoptions](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.postlogoutredirecturi.aspx)」を参照してください。                                                                                 |
|       Authentication/OpenIdConnect/\[プロバイダー\]/validオーディエンス       |                                                                                                  対象者の Url のコンマ区切りのリスト。 詳細については、「 [Tokenvalidationparameters. allowedaudiences](https://msdn.microsoft.com/library/system.identitymodel.tokens.tokenvalidationparameters.allowedaudiences.aspx)」を参照してください。                                                                                                  |
|        Authentication/OpenIdConnect/\[プロバイダー\]/ValidIssuers        |                                                                                                       発行者の Url のコンマ区切りのリスト。 詳細については、「 [Tokenvalidationparameters. ValidIssuers](https://msdn.microsoft.com/library/system.identitymodel.tokens.tokenvalidationparameters.validissuers.aspx)」を参照してください。                                                                                                       |
|         Authentication/OpenIdConnect/\[プロバイダー\]/clockskew          |                                                                                                                                                                                        時間を検証するときに適用するクロックスキュー。                                                                                                                                                                                        |
|       Authentication/OpenIdConnect/\[プロバイダー\]/nameclaimtype        |                                                                                                                                                                              名前クレームを格納するために ClaimsIdentity によって使用される要求の種類。                                                                                                                                                                              |
|       Authentication/OpenIdConnect/\[プロバイダー\]/roleclaimtype        |                                                                                                                                                                              ロール要求を格納するために ClaimsIdentity によって使用される要求の種類。                                                                                                                                                                              |
|   Authentication/OpenIdConnect/\[プロバイダー\]/RequireExpirationTime    |                                                                                                                                                                              トークンが "有効期限" の値を持つ必要があるかどうかを示す値。                                                                                                                                                                              |
|    Authentication/OpenIdConnect/\[プロバイダー\]/requiresignedtoken     |                                                                                                                               署名されていない場合に、<http://ddue.schemas.microsoft.com/authoring/2003/5> が有効であるかどうかを示す値。                                                                                                                                |
|      Authentication/OpenIdConnect/\[プロバイダー\]/savesignintoken       |                                                                                                                                                                        セッションの作成時に元のトークンが保存されるかどうかを制御するブール値。                                                                                                                                                                        |
|       Authentication/OpenIdConnect/\[プロバイダー\]/validateactor        |                                                                                                                                                            JwtSecurityToken を検証する必要があるかどうかを示す値。                                                                                                                                                            |
|      Authentication/OpenIdConnect/\[プロバイダー\]/validateaudience      |                                                                                                                                                                       トークンの検証中に対象ユーザーを検証するかどうかを制御するブール値。                                                                                                                                                                        |
|       Authentication/OpenIdConnect/\[プロバイダー\]/validateissuer       |                                                                                                                                                                        トークンの検証中に発行者が検証されるかどうかを制御するブール値。                                                                                                                                                                         |
|      Authentication/OpenIdConnect/\[プロバイダー\]/ValidateLifetime      |                                                                                                                                                                       トークンの検証中に有効期間が検証されるかどうかを制御するブール値。                                                                                                                                                                        |
|  Authentication/OpenIdConnect/\[プロバイダー\]/ValidateIssuerSigningKey  |                                                                                                                  (SecurityToken xmlns =<http://ddue.schemas.microsoft.com/authoring/2003/5> に署名されている、system.servicemodel. SecurityKey) の検証が呼び出されるかどうかを制御するブール値。                                                                                                                  |
|                                                                      |                                                                                                                                                                                                                                                                                                                                                                                                                              |

## <a name="enable-authentication-using-a-multi-tenant-azure-active-directory-application"></a>マルチテナント Azure Active Directory アプリケーションを使用して認証を有効にする

[!include[](../../../includes/pn-azure-active-directory.md)]に登録されているマルチテナントアプリケーションを使用して、特定のテナントだけでなく [!include[](../../../includes/pn-azure-shortest.md)] の任意のテナントからの [!include[](../../../includes/pn-azure-active-directory.md)] ユーザーを受け入れるようにポータルを構成できます。 マルチテナントを有効にするには、[!include[](../../../includes/pn-azure-active-directory.md)] アプリケーションで**マルチテナント**スイッチを **[はい]** に設定します。

![Azure Active Directory アプリケーションでのマルチテナントの有効化](../media/enable-multi-tenancy.png "Azure Active Directory アプリケーションでのマルチテナントの有効化")

### <a name="related-site-settings"></a>関連サイトの設定

[Provider] タグのラベルを置き換えることで、複数の id プロバイダーを構成できます。 一意の各ラベルは、id プロバイダーに関連する設定のグループを形成します。 次のサイト設定をポータルで作成または構成して、マルチテナントアプリケーションを使用した [!include[](../../../includes/pn-azure-active-directory.md)] に対する認証をサポートすることができます。

|サイト設定名    |Description   |
|---|---|
|Authentication/OpenIdConnect/[provider]/Authority   |OpenIdConnect 呼び出しを行うときに使用する機関。 例: `https://login.microsoftonline.com/common`   |
|Authentication/OpenIdConnect/[provider]/ClientId   |プロバイダーアプリケーションからのクライアント ID 値。 アプリ ID またはコンシューマーキーと呼ばれることもあります。   |
|Authentication/OpenIdConnect/[provider]/externallogoutenabled   |外部アカウントのサインアウトと登録を有効または無効にします。 この値を True に設定します。   |
|Authentication/OpenIdConnect/[provider]/issuerfilter   |すべてのテナントのすべての発行者に一致するワイルドカードベースのフィルター。 ほとんどの場合、次の値を使用して `https://sts.windows.net/*/`   |
|Authentication/OpenIdConnect/[provider]/redirecturi  |プロバイダーが認証応答を送信する応答 URL の場所。例: `https://portal.contoso.com/signin-oidc` |
|Authentication/OpenIdConnect/[provider]/validateissuer   |トークンの検証中に発行者が検証されるかどうかを制御するブール値。 この値を False に設定します。   |
|||

### <a name="see-also"></a>関連項目
[ポータル認証を構成する](configure-portal-authentication.md)  
[ポータルの認証 id を設定する](set-authentication-identity.md)  
[ポータルの OAuth2 プロバイダーの設定](configure-oauth2-settings.md)  
[ポータルの WS-FEDERATION プロバイダーの設定](configure-ws-federation-settings.md)  
[ポータルの SAML 2.0 プロバイダー設定](configure-saml2-settings.md)  

