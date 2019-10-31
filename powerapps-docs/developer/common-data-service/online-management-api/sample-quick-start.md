---
title: 'クイックスタート サンプル: オンライン管理 API を使用して Common Data Service 環境を取得する| MicrosoftDocs'
description: C＃ サンプルは、Online Management API への認証方法と、Office 365 テナントからすべての Common Data Service の環境を取得する方法を示しています。
ms.date: 10/01/2019
ms.service: powerapps
ms.topic: conceptual
ms.assetid: 63600a55-a1f0-491f-83f6-b3252566d27e
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
---
# <a name="quick-start-sample-retrieve-common-data-service-environements-using-online-management-api"></a>クイックスタート サンプル: オンライン管理 API を使用して Common Data Service 環境を取得する 

C＃ サンプルは、Online Management API への認証方法と、Office 365 テナントからすべての Common Data Service の環境を取得する方法を示しています。

サンプルでは、OAuth 2.0 プロトコルを使用して Online Management API に簡単に認証し、要求ヘッダーにあるアクセス トークンを渡すために、認証 [ヘルパー コード](sample-authentication-helper.md) を使用しています。

## <a name="what-this-sample-does"></a>このサンプルの概要

サンプルでは次のタスクを実行します:

1. **ConnectToAPI** メソッドを使用し、Online Management API に接続します。

    a. 認証ヘルパー コードの **DiscoverAuthority** メソッドを呼び出して、権限情報を入手するためにサービス URL に渡します。

    b. HttpClient インスタンスを使用して、Online Management API サービスに接続します。

    c. API サービスのベース アドレスと最大実行時間を指定します。
1. **RetrieveInstancesAsync** メソッドを使用し、Office 365 テナント内のすべての Customer Enagement のインスタンスを取得するための http 要求を実行し、応答を表示します。

## <a name="run-this-sample"></a>このサンプルの実行
このサンプルを実行する前に次があることを確認します:
- Office 365 テナントの管理者ロールの 1 つ。 [Office 365 管理者ロール](get-started-online-management-api.md#office-365-admin-roles)を参照
- Visual Studio 2015 以降では、NuGet パッケージにアセンブリをダウンロード / 復元するには、インターネット接続が必要です。
- .NET Framework 4.6.2

サンプルを実行するには:
1. サンプルを[ダウンロードし](https://code.msdn.microsoft.com/Sample-Retrieve-Customer-94e4076d)、展開します。
2. 展開された場所にある C＃ フォルダーの Visual Studio ソリューション ファイル (.sln) をダブルクリックし、Visual Studio でソリューションを開きます。
3. **Programs.cs** ファイルでは、対象地域が北米以外である場合は、異なるサービス URL を指定します。 世界各国の地域におけるサービス URL 値の一覧については、「[サービス URL](get-started-online-management-api.md#service-url)」を参照してください。
    ```csharp
    //TODO: Change this value if your Office 365 tenant is in a different region than North America

    private static string _serviceUrl = "https://admin.services.crm.dynamics.com";
    ```
4. **HelperCode** > **AuthenticationHelper.cs** ファイルでは、`_clientId` 値および `_redirectURL` 値を適切に更新します。

    ```csharp
    // TODO: Substitute your app registration values here.
    // These values are obtained on registering your application with the 
    // Azure Active Directory.
    private static string _clientId = "<GUID>";    //e.g. "e5cf0024-a66a-4f16-85ce-99ba97a24bb2"
    private static string _redirectUrl = "<Url>";  //e.g. "app://e5cf0024-a66a-4f16-85ce-99ba97a24bb2"
    ```
5. 変更を保存し、F5 を押すか、または**デバッグ** > **デバッグ開始**を選択し、デバッグを開始します。

## <a name="code-sample-listing"></a>コード サンプル一覧 

完全なサンプル コードを次に示します。

```csharp
using Microsoft.Crm.Sdk.Samples.HelperCode;
using System;
using System.Net.Http;
using System.Threading.Tasks;


namespace Microsoft.Crm.Sdk.Samples
{
    /// <summary>
    /// This sample retrieves Customer Engagement instances
    /// in your Office 365 tenant.
    /// </summary>    

    class RetrieveInstances
    {
        private HttpClient httpClient;

        //TODO: Change this value if your Office 365 tenant is in a different region than North America
        private static string _serviceUrl = "https://admin.services.crm.dynamics.com";

        private void ConnectToAPI()
        {
            Console.WriteLine("Connecting to the Online Management API service...");

            // Discover authority for the Online Management API service
            var authority = Authentication.DiscoverAuthority(_serviceUrl);

            // Authenticate to the Online Management API service by 
            // passing in the discovered authority 
            Authentication auth = new Authentication(authority.Result.ToString());            

            // Use an HttpClient object to connect to Online Management API service.           
            httpClient = new HttpClient(auth.ClientHandler, true);

            // Specify the API service base address and the max period of execution time 
            httpClient.BaseAddress = new Uri(_serviceUrl);
            httpClient.Timeout = new TimeSpan(0, 2, 0);            
        }

        public async Task RetrieveInstancesAsync()
        {
            HttpRequestMessage myRequest = new HttpRequestMessage(HttpMethod.Get, "/api/v1.1/instances");
            HttpResponseMessage myResponse = await httpClient.SendAsync(myRequest);

            if (myResponse.IsSuccessStatusCode)
            {
                var result = myResponse.Content.ReadAsStringAsync().Result;
                Console.WriteLine("Your instances retrieved from Office 365 tenant: \n{0}", result);
            }
            else
            {
                Console.WriteLine("The request failed with a status of '{0}'",
                       myResponse.ReasonPhrase);
            }
        }

        static public void Main(string[] args)
        {
            RetrieveInstances app = new RetrieveInstances();
            try
            {
                // Connect to the Online Management API. 
                app.ConnectToAPI();

                // Run your request
                Task.WaitAll(Task.Run(async () => await app.RetrieveInstancesAsync()));
            }
            catch (System.Exception ex) { DisplayException(ex); }
            finally
            {
                if (app.httpClient != null)
                { app.httpClient.Dispose(); }
                Console.WriteLine("Press <Enter> to exit the program.");
                Console.ReadLine();
            }
        }

        /// <summary> Helper method to display exceptions </summary> 
        private static void DisplayException(Exception ex)
        {
            Console.WriteLine("The application terminated with an error.");
            Console.WriteLine(ex.Message);
            while (ex.InnerException != null)
            {
                Console.WriteLine("\t* {0}", ex.InnerException.Message);
                ex = ex.InnerException;
            }
        }
    }
}
```

### <a name="related-topics"></a>関連トピック  

[Online Management API で始める](get-started-online-management-api.md)

[Online Management API でサポートする操作](operations-supported.md)

[Online Management API 参照](/rest/api/admin.services.crm.dynamics.com)
