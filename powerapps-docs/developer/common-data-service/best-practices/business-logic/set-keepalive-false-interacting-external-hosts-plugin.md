---
title: プラグインで外部ホストを操作するときは、キープアライブを false に設定する | MicrosoftDocs
description: キープアライブ プロパティを HTTP 要求ヘッダーで True に設定します。明示的に false に定義されていない場合、プラグインの実行時間が長くなる可能性があります。
services: ''
suite: powerapps
documentationcenter: na
author: jowells
manager: austinj
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 8/21/2019
ms.author: jowells
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="set-keepalive-to-false-when-interacting-with-external-hosts-in-a-plug-in"></a>プラグインで外部ホストを操作するときは、キープアライブを false に設定する

**カテゴリ**: パフォーマンス

**影響の可能性**: 高い

<a name='symptoms'></a>

## <a name="symptoms"></a>現象

プラグインが外部の Web 要求を行い、クローズドな接続で `KeepAlive` を使用しようとしている場合、最終的には、プラグインによる Web 要求の実行は失敗します。 プラグインが登録されている場合:

- 同期的に、次のことが発生することがあります。

    - モデル駆動アプリが応答しない
    - クライアント対話が遅くなる
    - ブラウザーが応答を停止する

- 非同期的には、プラグインの実行が失敗する前に長い時間を要する可能性があります。 

<a name='guidance'></a>

## <a name="guidance"></a>ガイダンス

1. HTTP 1.1では、他で宣言されていない限り、すべての接続が永続します (`KeepAlive` は true)。 プラグインは独立して実行されるため、Sandbox サービスはそれらを短期間の実行であると解釈しますが、これにより、一般的に `KeepAlive` の恩恵を受けられなくなります。 外部サービスへの接続に関する問題を避けるために、プラグイン内で `KeepAlive` を無効にすることをお勧めします。特定の外部サービスがパフォーマンス上の理由で永続セッションの使用から恩恵を受けている場合、接続が閉じられないようにするためにアイドルタイムアウト (30 秒) の半分の間隔で積極的に `KeepAlive` を送ってください。

次の例は、外部サービスへの接続を確立するために使用する方法に基づいて ``KeepAlive` を false に明示的に定義する方法を示しています。

- `HttpWebRequest` 
    ```csharp
    HttpWebRequest req = WebRequest.Create("https://www.contoso.com/api/stuff") as HttpWebRequest;
    
    if (req != null)
    {
        req.KeepAlive = false;
        HttpWebResponse response = (HttpWebResponse)req.GetResponse();
    }
    ```

-  `WebClient` 
    ```csharp
    private string RequestString(Uri location)
    {
        using (var client = new MyWebClient())
        {
            return client.DownloadString(location);
        }
    }

    internal class MyWebClient : WebClient
    {
        // Overrides the GetWebRequest method and sets keep alive to false
        protected override WebRequest GetWebRequest(Uri address)
        {
            HttpWebRequest req = (HttpWebRequest)base.GetWebRequest(address);
            req.KeepAlive = false;

            return req;
        }
    }
    ```

- `WCF ClientBase< T >` インスタンス 
    ```csharp
    OrganizationServiceClient client = null;
    
    try
    {
        var address = new EndpointAddress("https://www.contoso.com/Custom.svc");
        var transport = new HttpsTransportBindingElement();
        transport.KeepAliveEnabled = false;
    
        var binding = new CustomBinding(transport);
    
        client = new OrganizationServiceClient(binding, address);
    
        WhoAmIResponse response = client.Execute(new WhoAmIRequest()) as WhoAmIResponse;
    }
    catch (Exception ex)
    {
        client.Abort();
    }
    finally
    {
        client.Close();
    }
    ```

- `WCF ChannelFactory< TChannel >` 静的メソッド 
    ```csharp
    IRequestChannel channel = null;
    try
    {
        var address = new EndpointAddress("https://www.contoso.com/Custom.svc");
        var transport = new HttpsTransportBindingElement();
        transport.KeepAliveEnabled = false;
    
        var binding = new CustomBinding(transport);
    
        channel = ChannelFactory<IRequestChannel>.CreateChannel(binding, address);
    
        Message request = Message.CreateMessage(MessageVersion.Soap12, "some action", "message body");
        Message response = channel.Request(request);
    }
    catch (Exception ex)
    {
        channel.Abort();
    }
    finally
    {
        channel.Close();
    }
    ```

- `WCF ChannelFactory< TChannel >` インスタンス 
    ```csharp
    ChannelFactory<IRequestChannel> factory = null;
    IRequestChannel channel = null;
    try
    {
        var address = new EndpointAddress("https://www.contoso.com/Custom.svc");
        var transport = new HttpsTransportBindingElement();
        transport.KeepAliveEnabled = false;
    
        var binding = new CustomBinding(transport);
    
        factory = new ChannelFactory<IRequestChannel>(binding, address);
        channel = factory.CreateChannel();
    
        Message request = Message.CreateMessage(MessageVersion.Soap12, "some action", "message body");
        Message response = channel.Request(request);
    }
    catch (Exception ex)
    {
        channel.Abort();
        factory.Abort();
    }
    finally
    {
        channel.Close();
        factory.Close();
    }
    ```

<a name='problem'></a>

## <a name="problematic-patterns"></a>問題となるパターン

非WCFインタラクションのための `KeepAlive` の既定値をオーバーライドするために、HttpWebRequest を利用して Web サーバーとのインタラクションを実行するというアプローチをとる必要がありますが、最初は `KeepAlive` のプロパティを false にする必要があります。

次の例は、外部サービスへの接続を確立するために使用する方法に基づいた問題のあるパターンを示しています。

> [!WARNING]
> これらのパターンは、回避する必要があります。

- `HttpWebRequest`

    ```csharp
    WebRequest request = WebRequest.Create("https://www.contoso.com/api/stuff");
    //KeepAlive not explicitly defined as true.  However, default behavior is KeepAlive = true.
    HttpWebResponse response = (HttpWebResponse)request.GetResponse();
    response.Close();
    ```

- `WebClient`

    ```csharp
    using (var client = new WebClient())
    {
        string url = "https://www.contoso.com/api/stuff";
        //KeepAlive not explicitly defined as true.  However, default behavior is KeepAlive = true.
        string result = client.DownloadString(url);
    }
    ```

- `WCF ClientBase< T >` インスタンス

    ```csharp
    OrganizationServiceClient client = null;
    
    try
    {
        var address = new EndpointAddress("https://www.contoso.com/Custom.svc");
        var binding = new BasicHttpsBinding();
        //KeepAlive not explicitly defined as true.  However, default behavior is KeepAlive = true.
        client = new OrganizationServiceClient(binding, address);
    
        WhoAmIResponse response = client.Execute(new WhoAmIRequest()) as WhoAmIResponse;
    }
    catch (Exception ex)
    {
        client.Abort();
    }
    finally
    {
        client.Close();
    }
    ```

- `WCF ChannelFactory< TChannel >` 静的メソッド

    ```csharp
    IRequestChannel channel = null;
    try
    {
        var address = new EndpointAddress("https://www.contoso.com/Custom.svc");
        var binding = new BasicHttpsBinding();
        //KeepAlive not explicitly defined as true.  However, default behavior is KeepAlive = true.
    
        channel = ChannelFactory<IRequestChannel>.CreateChannel(binding, address);
    
        Message request = Message.CreateMessage(MessageVersion.Soap12, "some action", "message body");
        Message response = channel.Request(request);
    }
    catch (Exception ex)
    {
        channel.Abort();
    }
    finally
    {
        channel.Close();
    }
    ```

- `WCF ChannelFactory< TChannel >` インスタンス

    ```csharp
    ChannelFactory<IRequestChannel> factory = null;
    IRequestChannel channel = null;
    try
    {
        var address = new EndpointAddress("https://www.contoso.com/Custom.svc");
        var binding = new BasicHttpsBinding();
        //KeepAlive not explicitly defined as true.  However, default behavior is KeepAlive = true.
    
        factory = new ChannelFactory<IRequestChannel>(binding, address);
        channel = factory.CreateChannel();
    
        Message request = Message.CreateMessage(MessageVersion.Soap12, "some action", "message body");
        Message response = channel.Request(request);
    }
    catch (Exception ex)
    {
        channel.Abort();
        factory.Abort();
    }
    finally
    {
        channel.Close();
        factory.Close();
    }
    ```

<a name='additional'></a>

## <a name="additional-information"></a>追加情報

外部サービスを操作するプラグインは、実行時間が異常に長くなる可能性があります。 この問題は、外部Webサーバーに発行された HTTP リクエスト ([KeepAlive プロパティ](https://msdn.microsoft.com/library/system.net.httpwebrequest.keepalive.aspx)) によるものです。 `KeepAlive` プロパティが true に設定されているかまったく定義されていない (デフォルトの振る舞いが true) 場合、セッションがネットワークデバイスの設定により期限切れになっても、サーバー上の Sandbox クライアントは永続セッションを試み続けます。 実行時間が長くなった原因は、接続が最終的にリセットされるまでネットワークがリクエストを再試行したためです。

> [!IMPORTANT]
> これは、 [System.Net.WebClient](https://msdn.microsoft.com/library/system.net.webclient.aspx)、 [System.Net.WebRequest](https://msdn.microsoft.com/library/system.net.webrequest.aspx) または [System.Net.HttpWebRequest](https://msdn.microsoft.com/library/system.net.httpwebrequest.aspx) を使用して、Web サーバーへの HTTP リクエストを開始するすべてのコードと、HTTP を使用したChannelFactory または ClientBase を介して直接的または [ChannelFactory\<TChannel>](https://docs.microsoft.com/dotnet/api/system.servicemodel.channelfactory-1) または [ClientBase\<T>](https://docs.microsoft.com/dotnet/api/system.servicemodel.clientbase-1) を介して間接的に HTTP トランスポートのバインドを使用する Windows Communications Foundation (WCF) クライアント通信に影響します。

この動作はエンドユーザーに対して透過的であり、実行がネットワークがあるので従来のログは遅れます。  プラグインを同期イベントとして登録されている場合は、これらの登録操作中にユーザーが断続的なパフォーマンスの問題を経験し、モデル駆動アプリが応答しなくなる可能性があります。  プラグインが非同期的に登録されている場合、問題は、プラグインの実行時間を調べ、実行が通常もしくは予想より長くかかることがわかったときのみ発見されます。

<a name='seealso'></a>

### <a name="see-also"></a>関連項目

[サンプル: 隔離されたプラグインからの Web アクセス](../../org-service/samples/web-access-plugin.md)<br />
[負荷分散 (WCF)](https://msdn.microsoft.com/library/ms730128.aspx)<br />
[HttpTransportBindingElement.KeepAliveEnabled プロパティ](https://msdn.microsoft.com/library/system.servicemodel.channels.httptransportbindingelement.keepaliveenabled.aspx)<br />
[HttpWebRequest.KeepAlive プロパティ](https://msdn.microsoft.com/library/system.net.httpwebrequest.keepalive.aspx)<br />
