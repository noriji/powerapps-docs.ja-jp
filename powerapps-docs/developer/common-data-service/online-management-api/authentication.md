---
title: Common Data Service のオンライン管理 API を使用するための認証 | MicrosoftDocs
description: 環境関連のオペレーションを実行するためのオンライン管理 API への認証に関する情報を提供します。
ms.date: 11/27/2017
ms.service: crm-online
ms.topic: conceptual
ms.assetid: c292c148-01f0-41f6-a2fe-7ed05a01a733
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - D365CE
---
# <a name="authenticate-to-use-the-online-management-api"></a>Online Management API の使用を認証

Online Management API は、OAuth 2.0 プロトコル をサポートし認証します。 [Azure Active Directory (AAD)](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-whatis) を使用して、有効な OAuth 2.0 アクセス トークン を取得して認証し、Online Management API へのリクエストの **認証** ヘッダーを使い送ります。

Online Management API で使用する推奨認証 API は、[Azure Active Directory Authentication Library (ADAL)](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries) で、これはさまざまなプラットフォームやプログラミング言語で利用できます。 

## <a name="how-to-authenticate"></a>認証の方法。

これらは、Online Management API サービスを認証するための広範な手順です。 

1. アプリの *clientId* と *redirectUrl* 値を得るため Azure Active Directory でアプリを登録します。 詳細は、[チュートリアル: Azure Active Directory でアプリを登録](/powerapps/developer/common-data-service/walkthrough-register-app-azure-active-directory) の "OAuth 認証のアプリ登録" セクションを確認します。

1. 認証 [ヘルパー コード](sample-authentication-helper.md) のステップ # 1 から得られた値を指定します。

    ```csharp
    // TODO: Substitute your app registration values here.
    // These values are obtained on registering your application with the 
    // Azure Active Directory.
    private static string _clientId = "<GUID>";    //e.g. "e5cf0024-a66a-4f16-85ce-99ba97a24bb2"
    private static string _redirectUrl = "<Url>";  //e.g. "app://s7cf7712-b773-4f16-92b3-34cs97a25cc7"
    ```

1. サービス URL に基づいて Online Management API の権限情報を検出します。 北米地域の場合、サービス URL は次のとおりです:**https://admin.services.crm.dynamics.com**。 地域固有のサービス URL については、[サービス URL](get-started-online-management-api.md#service-url) を参照してください<br /> Azure Active Directory チャレンジ・フォーマットを使用して、API のサービス URL に基づいて権限情報を判別します。<br />また、次のステップでアクセス トークンを取得するために使用される Online Management API (サービス URL とは異なる) のリソースも決定しています。

    ```csharp
    public static async Task<string> DiscoverAuthority(string _serviceUrl)
    {
        try
        {
            AuthenticationParameters ap = await AuthenticationParameters.CreateFromResourceUrlAsync(
                    new Uri(_serviceUrl + "/api/aad/challenge"));
            _resource = ap.Resource;
            return ap.Authority;
        }
        catch (HttpRequestException e)
        {
            throw new Exception("An HTTP request exception occurred during authority discovery.", e);
        }
        catch (Exception e)
        {
            throw e;
        }
    }
    ```
1. 前の手順で見つけたリソースをクライアント ID とともに使用し、クライアント アプリの URL 値をリダイレクトしてアクセ ストークンを取得します。 アクセス トークンを取得または更新するには、サービス URL ではなくリソースを使用する必要があります。

    ```csharp
    public AuthenticationResult AcquireToken()
    {
        return _authContext.AcquireToken(_resource, _clientId, new Uri(_redirectUrl),
                PromptBehavior.Always);
    }        
    ```

1. アクセス トークンを取得したら、メッセージ要求の**認証**ヘッダーをアクセス トークン値に設定し、トークン タイプを**負担者**と指定する必要があります。 また、**言語の承諾**ヘッダーを設定して応答で優先する言語を指定します。 認証の `SendAsync` メソッドは、全てのメッセージ リクエストにこれらのヘッダー値を設定します。

    ```csharp
    protected override Task<HttpResponseMessage> SendAsync(
                HttpRequestMessage request, System.Threading.CancellationToken cancellationToken)
    {
        // It is a best practice to refresh the access token before every message request is sent. Doing so
        // avoids having to check the expiration date/time of the token. This operation is quick.
        request.Headers.Authorization = new AuthenticationHeaderValue("Bearer", _auth.AcquireToken().AccessToken);
        
        // Set the "Accept-Language" header
        request.Headers.Add("Accept-Language", "en-US");

        return base.SendAsync(request, cancellationToken);
    }
    ```

Online Management API に対して、メッセージを実行するように設定されています。 Office 365 テナントのすべての Common Data Service 環境を取得する方法を示すサンプル コードについては、[クイック スタート サンプル: テナントの環境を取得](sample-quick-start.md) で確認してください。


### <a name="related-topics"></a>関連トピック  

[サンプル: Online Management API の認証ヘルパー](sample-authentication-helper.md)

[Online Management API で始める](get-started-online-management-api.md)

[Online Management API 参照](/rest/api/admin.services.crm.dynamics.com)
