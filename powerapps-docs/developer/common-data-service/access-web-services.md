---
title: 外部 Web サービスにアクセスする (Common Data Service) | MicrosoftDocs
description: カスタム プラグインもしくはワークフロー活動から Web サービスにアクセスする方法について説明します。
ms.custom: ''
ms.date: 8/19/2019
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: pehecke
manager: kvivek
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="access-external-web-services"></a>外部 Web サービスにアクセスする

プラグインとカスタム ワークフロー活動は、HTTP および HTTPS プロトコルを介してネットワークにアクセスできます。 この機能によって、ソーシャル サイト、ニュース フィード、Web サービスなどの一般的な Web サービスにアクセスできます。 このサンドボックスの機能には、次の Web アクセス制限が適用されます。  
  
- 許可されるプロトコルは HTTP および HTTPS だけです。
- localhost (ループバック) へのアクセスは許可されません。
- IP アドレスは使用できません。 DNS による名前解決を必要とする名前付き Web アドレスを使用する必要があります。
- 匿名認証がサポートされ、その使用が推奨されます。 ログオン ユーザーの資格情報を入力または保存する必要はありません。

Webhook および [!INCLUDE [pn_azure_service_bus](../../includes/pn_azure_service_bus.md)] の使用を含む Web サービスにアクセスする別の方法。 これらのトピックの詳細については以下で提供されるリンクを参照してください。

## <a name="how-to-access-external-web-services"></a>外部 Web サービスにアクセスする方法

最近、多くの人が [System.Net.Http.HttpClient Class](/dotnet/api/system.net.http.httpclient) に精通しています。 `HttpClient` は .NET 4.5 で導入され、現在も利用可能な [System.Net.WebClient Class](/dotnet/api/system.net.webclient) を超える重要な機能を提供します。

[.NET チームは WebClient を新規開発に推奨していない](/dotnet/api/system.net.webclient?#remarks) ため、新しいプラグインには `HttpClient` を使用する必要があります。 ただし、`WebClient` を使用した古いコードを見つけたら置き換える必要があるという意味ではありません。 `HttpClient` が提供するほとんどの利点は、プラグインで必ずしも利点を提供するわけではありません。 `HttpClient` は再利用されることを意図しており、既定では非同期です。 プラグイン内で複数の HTTP 要求を行う場合を除き、`WebClient` は 1 つの要求のために設計されています。 `HttpClient` は既定で非同期のため、通常の使用パターンから外れてコードを追加し、強制的に操作を同期的に実行する必要があります。通常は `await` キーワードを削除し、非同期呼び出しに `.Result` を付加します。

`WebClient` は使用する基盤の HTTP メソッドを明確に公開しない [UploadData](/dotnet/api/system.net.webclient.uploaddata) や [DownloadFile](/dotnet/api/system.net.webclient.downloadfile) などの単純な同期メソッドを提供します。しかし、`POST` の代わりに `PATCH` を使用する場合は、[UploadString(String, String, String)](/dotnet/api/system.net.webclient.uploadstring#System_Net_WebClient_UploadString_System_String_System_String_System_String_) などの特定の上書きを使用して設定できます。

ほとんどの場合、プラグイン以外では `HttpClient` を使用できます。 プラグイン内でも、必要に応じて `WebClient` を使用できます。

## <a name="best-practices"></a>ベスト プラクティス

以下のベスト プラクティスのトピックで説明します:

- [プラグインで外部ホストを操作するときは、キープアライブを false に設定する](best-practices/business-logic/set-keepalive-false-interacting-external-hosts-plugin.md)
- [プラグインで外部呼び出しをする場合のタイムアウトを設定する](best-practices/business-logic/set-timeout-for-external-calls-from-plug-ins.md)

外部呼び出しに適切な `Timeout` 期間を設定して `KeepAlive` を無効にする必要があります。 詳細は、これらのトピックを参照してください。


## <a name="see-also"></a>関連項目

[プラグイン](plug-ins.md)<br />
[ワークフローの拡張機能](workflow/workflow-extensions.md)<br />
[Azure統合](azure-integration.md)<br />
[Webhook の使用](use-webhooks.md)<br />
[サンプル: 隔離されたプラグインからの Web アクセス](org-service/samples/web-access-plugin.md)
