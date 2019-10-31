---
title: 'サンプル: Dynamics 365 for Customer Engagement の API のオンライン管理のヘルパーを認証 | MicrosoftDocs'
description: Online Management API に認証するヘルパー コード。
ms.date: 11/27/2017
ms.service: crm-online
ms.topic: conceptual
applies_to: Dynamics 365 for Customer Engagement (online)
ms.assetid: a96fff7c-814e-4fa1-98b6-7a2875ee0234
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - D365CE
---
# <a name="sample-authentication-helper-for-the-online-management-api"></a>サンプル: Online Management API の認証ヘルパー 

ヘルパー コードのサンプルでは、OAuth 2.0 プロトコルを使用して Online Management API に簡単に認証し、メッセージのヘッダーにあるアクセス トークンを渡すための次のメソッドを提供しています。

## <a name="discoverauthority-method"></a>DiscoverAuthority 方法
このメソッドでは、Azure AD チャレンジを発行して、API のサービス URL に基づいて権限情報を検出します。 Online Management API サービス URL の一覧については、「[サービス URL](get-started-online-management-api.md#service-url)」を参照してください。 

## <a name="acquiretoken-method"></a>AcquireToken メソッド
このメソッドは、検出されたリソースと、Azure AD で登録したアプリのクライアント ID とリダイレクト URL に基づいたアクセス トークンを取得します。 API のサービス URL ではなく、リソースを使用していることに注意してください。これら 2 つは異なります。


## <a name="sendasync-method"></a>SendAsync メソッド

これは、クライアント アプリケーションでメッセージ要求に**承認**ヘッダーと**言語の承諾**ヘッダーを追加するカスタム HTTP ハンドラーです。

## <a name="code-sample-listing"></a>コード サンプル一覧 

完全認証ヘルパーのサンプル コードを次に示します。

```csharp
using Microsoft.IdentityModel.Clients.ActiveDirectory;
using System;
using System.Net.Http;
using System.Net.Http.Headers;
using System.Threading.Tasks;

namespace Microsoft.Crm.Sdk.Samples.HelperCode
{
    /// <summary>
    /// Manages authentication to the Online Management API service.
    /// Uses Microsoft Azure Active Directory Authentication Library (ADAL) 
    /// to handle the OAuth 2.0 protocol. 
    /// </summary>
    public class Authentication
    {
        private HttpMessageHandler _clientHandler = null;
        private AuthenticationContext _authContext = null;
        private string _authority = null;        
        private string _serviceUrl = null;

        // Static variable to hold the Resource. This will be discovered
        // and then used later for acquiring access token
        private static string _resource = null;        

        // TODO: Substitute your app registration values here.
        // These values are obtained on registering your application with the 
        // Azure Active Directory.
        private static string _clientId = "<GUID>";     //e.g. "e5cf0024-a66a-4f16-85ce-99ba97a24bb2"
        private static string _redirectUrl = "<Url>";  //e.g. "app://s7cf7712-b773-4f16-92b3-34cs97a25cc7"

        #region Constructors
        /// <summary>
        /// Base constructor.
        /// </summary>
        public Authentication() { }

        /// <summary>
        /// Custom constructor that allows adding an authority determined asynchronously before 
        /// instantiating the Authentication class.
        /// </summary>                
        /// <param name="authority">The URL of the authority.</param>
        public Authentication(string authority)
            : base()
        {
            Authority = authority;
            SetClientHandler();
        }
        #endregion Constructors

        #region Properties
        /// <summary>
        /// The authentication context.
        /// </summary>
        public AuthenticationContext Context
        {
            get
            { return _authContext; }

            set
            { _authContext = value; }
        }

        /// <summary>
        /// The HTTP client message handler.
        /// </summary>
        public HttpMessageHandler ClientHandler
        {
            get
            { return _clientHandler; }

            set
            { _clientHandler = value; }
        }


        /// <summary>
        /// The URL of the authority to be used for authentication.
        /// </summary>
        public string Authority
        {
            get
            {
                if (_authority == null)
                {
                    var authority = DiscoverAuthority(_serviceUrl.ToString());
                    _authority = authority.Result.ToString();
                }


                return _authority;
            }

            set { _authority = value; }
        }
        #endregion Properties

        #region Methods
        /// <summary>
        /// Discover the authentication authority asynchronously.
        /// </summary>
        /// <param name="serviceUrl">The specified endpoint address</param>
        /// <returns>The URL of the authentication authority on the specified endpoint address, or an empty string
        /// if the authority cannot be discovered.</returns>
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

        /// <summary>
        /// Returns the authentication result for the configured authentication context.
        /// </summary>
        /// <returns>The refreshed access token.</returns>
        /// <remarks>Refresh the access token before every service call to avoid having to manage token expiration.</remarks>
        public AuthenticationResult AcquireToken()
        {
            return _authContext.AcquireToken(_resource, _clientId, new Uri(_redirectUrl),
                PromptBehavior.Always);
        }

        /// <summary>
        /// Sets the client message handler.
        /// </summary>
        private void SetClientHandler()
        {
            _clientHandler = new OAuthMessageHandler(this, new HttpClientHandler());
            _authContext = new AuthenticationContext(Authority, false);
        }

        #endregion Methods

        /// <summary>
        /// Custom HTTP client handler that adds the "Authorization" and "Accept-Language" headers to message requests.
        /// </summary>
        class OAuthMessageHandler : DelegatingHandler
        {
            Authentication _auth = null;

            public OAuthMessageHandler(Authentication auth, HttpMessageHandler innerHandler)
                : base(innerHandler)
            {
                _auth = auth;
            }

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
        }
    }
}
```

### <a name="related-topics"></a>関連トピック  

[Online Management API で始める](get-started-online-management-api.md)

[Online Management API でサポートする操作](operations-supported.md)

[Online Management API 参照](/rest/api/admin.services.crm.dynamics.com)
