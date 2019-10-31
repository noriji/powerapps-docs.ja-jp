---
title: プラグインで外部呼び出しをする場合のタイムアウトを設定する | MicrosoftDocs
description: 外部呼び出しがプラグイン内での応答を期待する時間の長さを制限します
services: ''
suite: powerapps
documentationcenter: na
author: JimDaly
manager: ryjones
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 08/19/2019
ms.author: jdaly
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="set-timeout-when-making-external-calls-in-a-plug-in"></a>プラグインで外部呼び出しをする場合のタイムアウトを設定する

**カテゴリ**: パフォーマンス

**影響の可能性**: 高い

<a name='symptoms'></a>

## <a name="symptoms"></a>現象

プラグインがすぐに応答に失敗する外部 Web 要求を行った場合、プラグインは完全な既定のタイムアウト期間待機し、その後失敗します。 この期間により、トランザクションが長くなり、他の操作に影響を与える可能性があります。 プラグインが登録されている場合:

- 同期的に、次のことが発生することがあります。

    - モデル駆動アプリが応答しない
    - クライアント対話が遅くなる
    - ブラウザーが応答を停止する

- 非同期的には、プラグインの実行が失敗する前に長い時間を要する可能性があります。 

<a name='guidance'></a>

## <a name="guidance"></a>ガイダンス

.Net Http クライアントの既定のタイムアウト値は 100 秒です。プラグインが完了するまでに使用できる時間より 20 秒短いだけです。 呼び出し元サービスが応答する、期待されるベースライン時間を確立することをお勧めします。 この通常の応答時間より長くなるほど、最終的に失敗する可能性が高くなります。 パフォーマンス ベスト プラクティスとして、既定のタイムアウト期間の期限切れを許可するよりもすぐに失敗することをお勧めします。 外部サービスへの呼び出しが待機する期間を制御する必要があります。

設定する必要があるタイムアウト値は、サービスにより異なります。 たとえば、サービスのパフォーマンスを監視できる場合、要求の 99.999% が成功する期間を調べ、その期間に数秒のバッファーを追加してタイムアウト期間を設定できます。 これにより、ときどき生じる外れ値が、プラグインのパフォーマンスに法外な影響を与えることがなくなります。

[System.Net.Http.HttpClient クラス](/dotnet/api/system.net.http.httpclient)を使っている場合、タイムアウトを 15 秒に設定しているこの例に示すように、`Timeout` 値を明示的に設定できます。

```csharp
using (HttpClient client = new HttpClient())
{
  client.Timeout = TimeSpan.FromMilliseconds(15000); //15 seconds
  client.DefaultRequestHeaders.ConnectionClose = true; //Set KeepAlive to false
  

  HttpResponseMessage response =  client.GetAsync(webAddress).Result; //Make sure it is synchonrous
  response.EnsureSuccessStatusCode();

  string responseText = response.Content.ReadAsStringAsync().Result; //Make sure it is synchonrous
  tracingService.Trace(responseText);
  //Log success in the Plugin Trace Log:
  tracingService.Trace("HttpClientPlugin completed successfully.");
}
```

[System.Net.WebClient クラス](/dotnet/api/system.net.webclient)を使っている場合、派生クラスを作成し、基本 [GetWebRequest メソッド](/dotnet/api/system.net.webclient.getwebrequest)を上書きしてタイムアウトを設定できます。

```csharp
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
```

次に、プラグイン コードでこのクラスを使用できます。

```csharp
using (CustomWebClient client = new CustomWebClient())
{
  byte[] responseBytes = client.DownloadData(webAddress);
  string response = Encoding.UTF8.GetString(responseBytes);
  tracingService.Trace(response);
  //Log success in the Plugin Trace Log:
  tracingService.Trace("WebClientPlugin completed successfully.");
}
```

<a name='seealso'></a>

### <a name="see-also"></a>関連項目

[サンプル: 隔離されたプラグインからの Web アクセス](../../org-service/samples/web-access-plugin.md)<br />
[プラグインで外部ホストを操作するときは、キープアライブを false に設定する](set-keepalive-false-interacting-external-hosts-plugin.md)
