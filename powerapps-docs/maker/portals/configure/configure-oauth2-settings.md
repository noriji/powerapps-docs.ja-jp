---
title: ポータルの OAuth2 プロバイダー設定を構成する |MicrosoftDocs
description: ポータルの OAuth2 プロバイダー設定を追加して構成する方法について説明します。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/18/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 25a26e6298fa3257f3db6d04ffd2937e8e71d3a1
ms.sourcegitcommit: 57b968b542fc43737330596d840d938f566e582a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2019
ms.locfileid: "72978533"
---
# <a name="configure-oauth2-provider-settings-for-portals"></a>ポータルの OAuth2 プロバイダー設定を構成する

OAuth 2.0 ベースの外部 id プロバイダーでは、"クライアント ID" と "クライアントシークレット" のペアを取得するために、サードパーティのサービスに "アプリケーション" を登録する必要があります。 多くの場合、このアプリケーションでは、id プロバイダーがユーザーをポータル (証明書利用者) に返信できるようにするリダイレクト URL を指定する必要があります。 クライアント ID とクライアントシークレットは、証明書利用者から id プロバイダーへのセキュリティで保護された接続を確立するために、ポータルサイト設定として構成されます。 設定は、 [[!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)]AccountAuthenticationOptions](https://msdn.microsoft.com//library/microsoft.owin.security.microsoftaccount.microsoftaccountauthenticationoptions.aspx)、 [TwitterAuthenticationOptions](https://msdn.microsoft.com//library/microsoft.owin.security.twitter.twitterauthenticationoptions.aspx)、 [FacebookAuthenticationOptions](https://msdn.microsoft.com//library/microsoft.owin.security.facebook.facebookauthenticationoptions.aspx)、および[GoogleOAuth2AuthenticationOptions](https://msdn.microsoft.com//library/microsoft.owin.security.google.googleoauth2authenticationoptions.aspx)クラスのプロパティに基づいています。  

サポートされているプロバイダーは次のとおりです。

- [!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)] アカウント
- Twitter
- Facebook
- Google
- LinkedIn
- Yahoo

## <a name="create-oauth-applications"></a>OAuth アプリケーションの作成

一般に、OAuth プロバイダーがリダイレクト URI 値を必要とするアプリ設定を使用する場合は、プロバイダーがリダイレクト URI 検証を実行する方法に応じて <http://portal.contoso.com/or> http://portal.contoso.com/signin-\ [プロバイダー\] を指定します (一部のプロバイダーでは、完全な URL パスをと共に指定する必要があります。ドメイン名)。 リダイレクト URI で \[プロバイダーの\] の代わりにプロバイダーの名前を置き換えます。

### <a name="google"></a>Google

[Google OAuth2 API 資格情報の手順](https://developers.google.com/accounts/docs/OpenIDConnect#appsetup)  

1. [Google 開発者コンソール](https://console.developers.google.com/)を開く  
2. API プロジェクトを作成するか、既存のプロジェクトを開きます。
3. [**Api & auth** &gt;**api**] にアクセスし、 **[ソーシャル api]** で **[Google + API]** を選択し、 **[api の有効化]** を選択します。
4. **Api & 認証**&gt;**同意画面**にアクセスします。
    - **電子メールアドレス**を指定してください。
    - カスタムの**製品名**を指定してください。
    - **[保存]** を選択します。
5. [**Api & auth** &gt;の**資格情報**] にアクセスし、新しいクライアント ID を作成します。
   - アプリケーションの種類:**Web アプリケーション**
   - 承認された [!INCLUDE[pn-javascript](../../../includes/pn-javascript.md)] オリジン: http://portal.contoso.com
   - 承認されたリダイレクト Uri: http://portal.contoso.com/signin-google 
   - **[クライアント ID の作成]** を選択します。

### <a name="facebook-app-settings"></a>Facebook アプリの設定

1. [Facebook 開発者アプリダッシュボード](https://developers.facebook.com/apps)を開く  
2. **[新しいアプリの追加]** を選択します。
3. **[Web サイト]** を選択します。
4. **[スキップしてアプリ ID を作成する]** を選択します。
    - **表示名**を指定します。
    - **カテゴリ**を選択してください。
    - **[アプリ ID の作成]** を選択します。

5. 新しいアプリのダッシュボードで、 **[設定]** [&gt;**基本**] (タブ) にアクセスし、次の詳細を追加します。
    - アプリケーションドメイン (オプション): portal.contoso.com 
    - 連絡先の電子メール:*選択した電子メールアドレス&lt;&gt;* 
    - **[プラットフォームの追加]** を選択し、 **[web サイト]** を選択します。 
    - サイトの URL: http://portal.contoso.com/ または http://portal.contoso.com/signin-facebook

6. **[変更の保存]** を選択します。
7. [**状態] & [確認**&gt; の**状態**] タブを開きます。
8. アプリとそのすべての機能を一般公開で使用できるようにするよう求めるメッセージが表示されたら、[**はい]** を選択します。 この設定を有効にするには、上記の手順5で有効なデータを入力しておく必要があります。

### <a name="includecc-microsoftincludescc-microsoftmd-application-settings"></a>アプリケーション設定の [!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)]

1. [[!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)] アカウントデベロッパーセンター](https://account.live.com/developers/applications/index)を開く  
2. **[アプリケーションの作成]** を選択し、**アプリケーション名**を指定します。
3. [**同意**する] を選択して、使用条件に同意します。
4. [**設定**&gt;**API 設定**] にアクセスし、[リダイレクト URL] を http://portal.contoso.com/signin-microsoft に設定します。 

### <a name="twitter-apps-settings"></a>Twitter アプリの設定

1. [Twitter アプリケーション管理](https://apps.twitter.com/)を開きます。 
2. **[新しいアプリの作成]** を選択します。

    - アプリの**名前**と**説明**を指定します。
    - Web サイトの URL を http://portal.contoso.com として設定します。
    - コールバック URL を http://portal.contoso.com または http://portal.contoso.com/signin-twitter として設定します。

3. **[Twitter アプリケーションの作成]** を選択します。

### <a name="linkedin-app-settings"></a>LinkedIn アプリの設定

1. [LinkedIn Developer Network](https://www.linkedin.com/secure/developer)を開きます。  
2. **[新しいアプリケーションの追加]** を選択します。

    - **アプリケーション名**、**説明**などを指定します。
    - Web サイトの URL を http://portal.contoso.com として設定します。
    - OAuth ユーザーアグリーメント/既定のスコープを設定する: r\_basicprofie と r\_emailaddress
    - Set OAuth 2.0 リダイレクト url: http://portal.contoso.com/signin-linkedin 。

3. **[アプリケーションの追加]** を選択します。

### <a name="yahoo-ydn-app-settings"></a>! YDN アプリの設定

1. [Yahoo! Developer Network](https://developer.yahoo.com/apps)を開きます。
2. **[アプリの作成]** を選択します。
    
    - **アプリケーション名**を指定してください。
    - アプリケーションの種類: **Web アプリケーション**。
    - コールバックドメイン: portal.contoso.com

3. **[アプリの作成]** を選択します。

## <a name="create-site-settings-by-using-oauth2"></a>OAuth2 を使用してサイト設定を作成する

各プロバイダーのアプリケーションダッシュボードには、各アプリケーションのクライアント ID (アプリ ID、コンシューマーキー) とクライアントシークレット (アプリシークレット、コンシューマーシークレット) が表示されます。 ポータルサイトの設定を構成するには、次の2つの値を使用します。

>[!Note]
> 標準 OAuth2 構成で必要となるのは、次の設定のみです (Facebook を例として)。
> - `Authentication/OpenAuth/Facebook/ClientId`
> - `Authentication/OpenAuth/Facebook/ClientSecret`

サイト設定名の `[provider]` タグを特定の id プロバイダー名 (Facebook、Google、Yahoo、[!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)]、LinkedIn、Twitter) に置き換えます。

|**サイト設定名**                                           |**Description**                                                                                                                                                                                                                                                                                                                                      |
|-----------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 認証/登録/ExternalLoginEnabled                | 外部アカウントのサインインと登録を有効または無効にします。 既定値: true                                                                                                                                                                                                                                                                         |
| Authentication/OpenAuth/\[provider\]/ClientId                   | 必須。 プロバイダーアプリケーションからのクライアント ID 値。 アプリ ID またはコンシューマーキーと呼ばれることもあります。  旧バージョンとの互換性のために次の設定名が許可されています: Authentication/OpenAuth/Twitter/ConsumerKey <ul><li>Authentication/OpenAuth/Facebook/AppId</li><li>Authentication/OpenAuth/LinkedIn/ConsumerKey</li> |
| Authentication/OpenAuth/\[プロバイダー\]/clientsecret               | 必須。 プロバイダーアプリケーションからのクライアントシークレット値。 アプリシークレットまたはコンシューマーシークレットと呼ばれることもあります。  旧バージョンとの互換性のために次の設定名が許可されています: Authentication/OpenAuth/Twitter/ConsumerSecret <ul><li>Authentication/OpenAuth/Facebook/AppSecret</li><li>Authentication/OpenAuth/LinkedIn/ConsumerSecret</li> |
| Authentication/OpenAuth/\[provider\]/AuthenticationType         | OWIN authentication ミドルウェア型。 例: yahoo。 [authenticationoptions. authenticationtype](https://msdn.microsoft.com//library/microsoft.owin.security.authenticationoptions.authenticationtype.aspx)。                                                                                                                                |  
| Authentication/OpenAuth/\[provider\]/Scope                      | 要求するアクセス許可のコンマ区切りの一覧。 [microsoft accountauthenticationoptions。スコープ](https://msdn.microsoft.com//library/microsoft.owin.security.microsoftaccount.microsoftaccountauthenticationoptions.scope.aspx)。                                                                                                                |  
| Authentication/OpenAuth/\[プロバイダー\]/キャプション                    | ユーザーがサインインユーザーインターフェイスに表示できるテキスト。 [microsoft accountauthenticationoptions。キャプション](https://msdn.microsoft.com//library/microsoft.owin.security.microsoftaccount.microsoftaccountauthenticationoptions.caption.aspx)。                                                                                              |  
| Authentication/OpenAuth/\[provider\]/backchanneltimeout         | バックチャネル通信のタイムアウト値 (ミリ秒)。 [microsoft accountauthenticationoptions。 backchanneltimeout](https://msdn.microsoft.com//library/microsoft.owin.security.microsoftaccount.microsoftaccountauthenticationoptions.backchanneltimeout.aspx)。                                                                         |  
| Authentication/OpenAuth/\[プロバイダー\]/tcp/ip パス               | ユーザーエージェントが返されるアプリケーションの基本パス内の要求パス。 [microsoft accountauthenticationoptions./パス](https://msdn.microsoft.com//library/microsoft.owin.security.microsoftaccount.microsoftaccountauthenticationoptions.callbackpath.aspx)。                                                         |  
| Authentication/OpenAuth/\[provider\]/SignInAsAuthenticationType | **UserClaimsIdentity**を実際に発行するための、別の認証ミドルウェアの名前。 [signinasauthenticationtype を選択](https://msdn.microsoft.com//library/microsoft.owin.security.microsoftaccount.microsoftaccountauthenticationoptions.signinasauthenticationtype.aspx)します。 |  
| Authentication/OpenAuth/\[provider\]/AuthenticationMode         | OWIN 認証ミドルウェアモード。 [authenticationmode を選択](https://msdn.microsoft.com//library/microsoft.owin.security.authenticationoptions.authenticationmode.aspx)します。                                                                                                                                       |  

### <a name="see-also"></a>関連項目

[ポータル認証を構成する](configure-portal-authentication.md)  
[ポータルの認証 id を設定する](set-authentication-identity.md)  
[ポータル  の OPEN ID Connect プロバイダー設定](configure-openid-settings.md)  
[ポータルの WS-FEDERATION プロバイダーの設定](configure-ws-federation-settings.md)  
[ポータルの SAML 2.0 プロバイダー設定](configure-saml2-settings.md)
