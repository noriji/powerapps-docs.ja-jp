---
title: 'サンプル: プラグインからの Web アクセス (Common Data Service) | Microsoft Docs'
description: このサンプルは、 Web 上にあるリソースにアクセスできるプラグインの書き込み方法を示します。
ms.custom: ''
ms.date: 8/19/2019
ms.reviewer: ''
ms.service: powerapps
ms.topic: samples
author: JimDaly
ms.author: pehecke
manager: kvivek
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="sample-web-access-from-a-plug-in"></a>サンプル: プラグインからの Web アクセス

このサンプルは、 Web サービスもしくはフィードのようなリソースにアクセスできるプラグインの書き込み方法を示します。 この呼び出しに認められる時間の長さを制限する方法も示します。 サンプルは [ここ](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/WebAccessPlugin) からダウンロードできます。

## <a name="how-to-run-this-sample"></a>このサンプルを実行する方法

1. [サンプル](https://github.com/Microsoft/PowerApps-Samples) リポジトリをダウンロードまたは複製して、ローカル コピーを用意します。 このサンプルは、PowerApps-Samples-master\cds\orgsvc\C#\WebAccessPlugin にあります。
1. 2 つのプラグイン クラスの例があります。 
    - WebClientPlugin は [WebClient Class](/dotnet/api/system.net.webclient) を使用
    - HttpClientPlugin は [HttpClient Class](/dotnet/api/system.net.http.httpclient) を使用
1. Visual Studio でサンプル ソリューションを開き、プロジェクトのプロパティに移動して、ビルド中にアセンブリが署名されることを確認してください。 サンプルのアセンブリ (WebAccessPlugin.dll) をビルドするには F6 を押します。
1. プラグイン登録ツールを実行して Common Data Service サーバーのサンドボックスおよびデータベースにアセンブリを登録します。 
1. どちらのプラグインの種類でも、ステップを登録するときは、セキュリティ保護されていない設定フィールドに Web URI 文字列 (例: `http://www.microsoft.com`) を指定します。
    - 何も指定しない場合、既定値 `http://www.bing.com` が使用されます。
1. アプリを使用するかコードを記述して適切な操作を実行し、メッセージとプラグインを登録したエンティティの要求を呼び出します。
1. プラグインを実行すると、呼び出しの期間が15 秒の制限を超えた場合、エラーがスローされます。 それ以外の場合、正常に実行されます。
1. テストを完了したらアセンブリとステップの登録を解除します。

## <a name="what-this-sample-does"></a>このサンプルの概要

実行すると、プラグインは、指定した Web サービス アドレス (つまり既定のアドレス) から Web ページ データをダウンロードします。 要求が 15 秒の制限を超えた場合、[InvalidPluginExecutionException](/dotnet/api/microsoft.xrm.sdk.invalidpluginexecutionexception) がスローされ、詳細がプラグイン トレース ログに書き込まれます。

- `WebClientPlugin` プラグインが失敗した場合、プラグイン トレース ログに次のようなものが書き込まれます。
    ```
    Downloading the target URI: http://www.bing.com
    Exception: Microsoft.Xrm.Sdk.InvalidPluginExecutionException: The timeout elapsed while attempting to issue the request. ---> System.Net.WebException: The operation has timed out
      at System.Net.WebClient.DownloadDataInternal(Uri address, WebRequest& request)
      at System.Net.WebClient.DownloadData(Uri address)
      at PowerApps.Samples.WebClientPlugin.Execute(IServiceProvider serviceProvider)
      --- End of inner exception stack trace ---
      at PowerApps.Samples.WebClientPlugin.Execute(IServiceProvider serviceProvider)
    ```

- `HttpClientPlugin` プラグインが失敗した場合、プラグイン トレース ログに次のようなものが書き込まれます。
    ```
    Downloading the target URI: http://www.bing.com
    Inner Exceptions:
      Exception: System.Threading.Tasks.TaskCanceledException: A task was canceled.
    Exception: Microsoft.Xrm.Sdk.InvalidPluginExecutionException: An exception occurred while attempting to issue the request.
       at PowerApps.Samples.HttpClientPlugin.Execute(IServiceProvider serviceProvider)
    ```
    [TaskCanceledException](/dotnet/api/system.threading.tasks.taskcanceledexception) は、タスクがキャンセルされる理由についてややあいまいです。 タイムアウトによるエラーを明示的に検出する方法を示すより詳細なソリューションについては、ブログ投稿 [HttpClient 処理のより優れたタイムアウト処理](https://thomaslevesque.com/2018/02/25/better-timeout-handling-with-httpclient/)を参照してください。

## <a name="how-this-sample-works"></a>このサンプルがどのように動作するか

[このサンプルの概要](#what-this-sample-does) で説明されているシナリオをシミュレートするために、サンプルは次のことを行います。

### <a name="setup"></a>セットアップ

1. Web アドレス値について、コンストラクタの安全でない設定パラメータをチェックします。それ以外の場合は、既定値が使用されます。
2. 登録されるプラグインによっては、[WebClient Class](/dotnet/api/system.net.webclient) または [HttpClient Class](/dotnet/api/system.net.http.httpclient) クラスが、プラグインの `Execute` メソッドにより使用され、Web ページ データがダウンロードされます。
3. 呼び出しが指定された 15 秒の期間を超えた場合、[InvalidPluginExecutionException](/dotnet/api/microsoft.xrm.sdk.invalidpluginexecutionexception) がスローされ、エラーについての詳細がプラグイン トレース ログに書かれます。

### <a name="demonstrate"></a>使用方法

#### <a name="webclientplugin-plugin"></a>WebClientPlugin プラグイン

1. 派生した `CustomWebClient` クラスを使って、`WebClient` クラスで使用できない [WebRequest.Timeout プロパティ](/dotnet/api/system.net.webrequest.timeout)を設定します。

   ````
    /// <summary>
    /// A class derived from WebClient with 15 second timeout and KeepAlive disabled
    /// </summary>
    public class CustomWebClient : WebClient
    {
      protected override WebRequest GetWebRequest(Uri address)
      {
        HttpWebRequest request = (HttpWebRequest)base.GetWebRequest(address);
        if (request != null)
        {
          request.Timeout = 15000; //15 Seconds
          request.KeepAlive = false;
          
        }
        return request;
      }
    }
    ````

1. [WebClient.DownloadData メソッド](/dotnet/api/system.net.webclient.downloaddata)を使用し、リソースからデータをダウンロードします。
1. 予想される [WebException クラス](/dotnet/api/system.net.webexception)を解析し、[Status プロパティ](/dotnet/api/system.net.webexception.status)を使用してエラーの原因がタイムアウトかどうかを判断する方法を示します。

#### <a name="httpclientplugin-plugin"></a>HttpClientPlugin プラグイン

1. [HttpClient クラス](/dotnet/api/system.net.http.httpclient)を使い、[Timeout プロパティ](/dotnet/api/system.net.http.httpclient.timeout)を使って操作の完了までに許容される時間を制限します。
1. 予想される [AggregateException クラス](/dotnet/api/system.aggregateexception)を取得し、予想される [TaskCanceledException](/dotnet/api/system.threading.tasks.taskcanceledexception) の内部例外を調べます


### <a name="see-also"></a>関連項目

[外部 Web リソースにアクセスする](../../access-web-services.md)<br/>
[プラグインの登録](../../register-plug-in.md)