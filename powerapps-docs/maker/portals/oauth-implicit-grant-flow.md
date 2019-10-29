---
title: ポータル内で OAuth 2.0 の暗黙的な許可フローを使用する |MicrosoftDocs
description: ポータルで OAuth 暗黙的許可フローを使用して、外部 Api に対するクライアント側の呼び出しを行い、それらをセキュリティで保護する方法について説明します。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 06db149e5f86696ecffae38fe05e23198d72ecb5
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/11/2019
ms.locfileid: "72974508"
---
# <a name="use-oauth-20-implicit-grant-flow-within-your-portal"></a>ポータル内で OAuth 2.0 の暗黙的な許可フローを使用する 

この機能により、顧客は外部 Api に対してクライアント側の呼び出しを行い、OAuth の暗黙的な許可フローを使用してセキュリティを保護することができます。 OAuth 2.0 の暗黙的な許可フローに従う承認のために外部 Api によって使用されるユーザー id 情報を格納する、セキュリティで保護されたアクセストークンを取得するためのエンドポイントを提供します。 サインインしているユーザーの id 情報は、外部の AJAX 呼び出しに安全な方法で渡されます。 これは、開発者が認証コンテキストを渡すのを支援するだけでなく、ユーザーがこのメカニズムを使用して Api をセキュリティで保護するのにも役立ちます。

OAuth 2.0 の暗黙的な許可フローは、クライアントが ID トークンを取得するために呼び出すことができるエンドポイントをサポートします。 この目的では、[承認](#authorize-endpoint-details)と[トークン](#token-endpoint-details)の2つのエンドポイントが使用されます。

## <a name="authorize-endpoint-details"></a>エンドポイントの詳細を承認する 

承認エンドポイントの URL は、`<portal_url>/_services/auth/authorize`です。 承認エンドポイントは、次のパラメーターをサポートしています。

| パラメーター   | 必須。 | Description                             |
|---------------|-----------|---------------------------------------|
| client_id      | はい       | 承認エンドポイントを呼び出すときに渡される文字列。 クライアント ID が[ポータルに登録](#register-client-id-for-implicit-grant-flow)されていることを確認する必要があります。 それ以外の場合は、エラーが表示されます。 クライアント ID は、トークン内の要求に `aud` および `appid` パラメーターとして追加されます。また、クライアントは、返されたトークンがそのアプリ用であることを検証するために使用できます。<br>最大長は36文字です。 英数字とハイフンのみがサポートされています。 |
| redirect_uri      | はい       | 認証応答を送受信できるポータルの URL です。 これは、呼び出しで使用される特定の `client_id` に登録する必要があり、登録されている値とまったく同じ値にする必要があります。            |
| 状態       | いいえ        | 要求に含まれる値。トークンの応答でも返されます。 使用する任意のコンテンツの文字列を指定できます。 通常、クロスサイト要求偽造攻撃を防ぐために、ランダムに生成された一意の値が使用されます。<br>最大の長さは20文字です。              |
| nonce   | いいえ        | 結果の ID トークンに要求として含まれるクライアントによって送信される文字列値。 クライアントはこの値を検証して、トークン再生攻撃を軽減できます。 最大の長さは20文字です。      |
| response_type         | いいえ        | このパラメーターでは、値として `token` のみがサポートされます。 これにより、承認エンドポイントに対して2回目の要求を行うことなく、アプリが承認エンドポイントからアクセストークンをすぐに受け取ることができます。                               |
|||

### <a name="successful-response"></a>成功した応答

承認エンドポイントは、応答 URL 内の次の値をフラグメントとして返します。

- **token**: トークンは、ポータルの秘密キーによってデジタル署名された JSON Web トークン (JWT) として返されます。
- **状態**: 状態パラメーターが要求に含まれている場合、同じ値が応答に表示されます。 アプリでは、要求と応答の状態値が同一であることを確認する必要があります。
- **expires_in**: アクセストークンが有効な時間の長さ (秒単位)。

たとえば、正常な応答は次のようになります。

```
GET https://aadb2cplayground.azurewebsites.net/#token=eyJ0eXAiOiJKV1QiLCJhbGciOI1NisIng1dCI6Ik5HVEZ2ZEstZnl0aEV1Q&expires_in=3599&state=arbitrary_data_you_sent_earlier
```

### <a name="error-response"></a>エラー応答

承認エンドポイントのエラーは、次の値を持つ JSON ドキュメントとして返されます。

- **エラー ID**: エラーの一意の識別子。
- **エラーメッセージ**: 認証エラーの根本原因を特定するのに役立つ特定のエラーメッセージです。
- **相関 ID**: デバッグのために使用される GUID。 診断ログが有効になっている場合は、サーバーエラーログに相関 ID が表示されます。
- **Timestamp**: エラーが生成された日時。

エラーメッセージは、サインインしているユーザーの既定の言語で表示されます。 ユーザーがサインインしていない場合は、ユーザーがサインインするためのサインインページが表示されます。 たとえば、エラー応答は次のようになります。

```
{"ErrorId": "PortalSTS0001", "ErrorMessage": "Client Id provided in the request is not a valid client Id registered for this portal. Please check the parameter and try again.", "Timestamp": "4/5/2019 10:02:11 AM", "CorrelationId": "7464eb01-71ab-44bc-93a1-f221479be847" }
```

## <a name="token-endpoint-details"></a>トークンエンドポイントの詳細

`/token` エンドポイントに対して要求を行うことによって、トークンを取得することもできます。 これは、承認エンドポイントが別のページ (redirect_uri) のトークンロジックを処理するのとは異なり、トークンエンドポイントは同じページのトークンロジックを処理します。 トークンエンドポイントの URL は、`<portal_url>/_services/auth/token`です。 トークンエンドポイントは、次のパラメーターをサポートしています。

| パラメーター   | 必須。 | Description                             |
|---------------|-----------|---------------------------------------|
| client_id      | いいえ       | 承認エンドポイントを呼び出すときに渡される文字列。 クライアント ID が[ポータルに登録](#register-client-id-for-implicit-grant-flow)されていることを確認する必要があります。 それ以外の場合は、エラーが表示されます。 クライアント ID は、トークン内の要求に `aud` および `appid` パラメーターとして追加されます。また、クライアントは、返されたトークンがそのアプリ用であることを検証するために使用できます。<br>最大長は36文字です。 英数字とハイフンのみがサポートされています。 |
| redirect_uri      | いいえ       | 認証応答を送受信できるポータルの URL です。 これは、呼び出しで使用される特定の `client_id` に登録する必要があり、登録されている値とまったく同じ値にする必要があります。            |
| 状態       | いいえ        | 要求に含まれる値。トークンの応答でも返されます。 使用する任意のコンテンツの文字列を指定できます。 通常、クロスサイト要求偽造攻撃を防ぐために、ランダムに生成された一意の値が使用されます。<br>最大の長さは20文字です。              |
| nonce   | いいえ        | 結果の ID トークンに要求として含まれるクライアントによって送信される文字列値。 クライアントはこの値を検証して、トークン再生攻撃を軽減できます。 最大の長さは20文字です。      |
| response_type         | いいえ        | このパラメーターでは、値として `token` のみがサポートされます。 これにより、承認エンドポイントに対して2回目の要求を行うことなく、アプリが承認エンドポイントからアクセストークンをすぐに受け取ることができます。                               |
|||

> [!NOTE]
> `client_id`、`redirect_uri`、`state`、および `nonce` のパラメーターは省略可能ですが、統合が安全であることを確認するために使用することをお勧めします。

### <a name="successful-response"></a>成功した応答

トークンエンドポイントは、状態と expires_in を応答ヘッダー、トークンをフォーム本文で返します。

### <a name="error-response"></a>エラー応答

トークンエンドポイントのエラーは、次の値を持つ JSON ドキュメントとして返されます。

- **エラー ID**: エラーの一意の識別子。
- **エラーメッセージ**: 認証エラーの根本原因を特定するのに役立つ特定のエラーメッセージです。
- **相関 ID**: デバッグのために使用される GUID。 診断ログが有効になっている場合は、サーバーエラーログに相関 ID が表示されます。
- **Timestamp**: エラーが生成された日時。

エラーメッセージは、サインインしているユーザーの既定の言語で表示されます。 ユーザーがサインインしていない場合は、ユーザーがサインインするためのサインインページが表示されます。 たとえば、エラー応答は次のようになります。

```
{"ErrorId": "PortalSTS0001", "ErrorMessage": "Client Id provided in the request is not a valid client Id registered for this portal. Please check the parameter and try again.", "Timestamp": "4/5/2019 10:02:11 AM", "CorrelationId": "7464eb01-71ab-44bc-93a1-f221479be847" }
```

## <a name="validate-id-token"></a>ID トークンの検証

ID トークンを取得するだけでは、ユーザーを認証するのに十分ではありません。また、トークンの署名を検証し、アプリの要件に基づいてトークン内の要求を検証する必要があります。 パブリックトークンエンドポイントは、ポータルの公開キーを提供します。このキーは、ポータルによって提供されるトークンの署名を検証するために使用できます。 パブリックトークンエンドポイントの URL は、`<portal_url>/_services/auth/publickey`です。

## <a name="turn-implicit-grant-flow-on-or-off"></a>暗黙的な許可フローを有効または無効にする

既定では、暗黙的な許可フローが有効になっています。 暗黙的な許可フローを無効にする場合は、 **Connector/ImplicitGrantFlowEnabled**サイト設定の値を**False**に設定します。

このサイト設定をポータルで使用できない場合は、適切な値を使用して[新しいサイト設定を作成](configure/configure-site-settings.md#manage-portal-site-settings)する必要があります。

## <a name="configure-token-validity"></a>トークンの有効性の構成

既定では、トークンは15分間有効です。 トークンの有効性を変更する場合は、 **ImplicitGrantFlow/TokenExpirationTime**サイト設定の値を必要な値に設定します。 値は秒単位で指定する必要があります。 最大値は1時間で、最小値は1分にする必要があります。 正しくない値 (英数字など) が指定されている場合は、既定値の15分が使用されます。 最大値より大きい値または最小値より小さい値を指定した場合、既定では最大値と最小値が使用されます。

たとえば、トークンの有効性を30分に設定するには、 **ImplicitGrantFlow/TokenExpirationTime**サイト設定の値を**1800**に設定します。 トークンの有効性を1時間に設定するには、 **ImplicitGrantFlow/TokenExpirationTime**サイト設定の値を**3600**に設定します。

## <a name="register-client-id-for-implicit-grant-flow"></a>暗黙的な許可フローのクライアント ID を登録する

このフローが許可されているポータルにクライアント ID を登録する必要があります。 クライアント ID を登録するには、次のサイト設定を作成する必要があります。

|サイト設定|Value|
|------|------|
|ImplicitGrantFlow/RegisteredClientId|このポータルで許可されている有効なクライアント ID 値。 値はセミコロンで区切る必要があり、英数字とハイフンを含めることができます。 最大長は36文字です。|
|ImplicitGrantFlow/{ClientId}/RedirectUri|特定のクライアント ID に対して許可されている有効なリダイレクト Uri。 値はセミコロンで区切る必要があります。 指定された URL は、ポータルの有効な web ページである必要があります。|
|||

## <a name="sample-code"></a>サンプルコード

次のサンプルコードを使用すると、PowerApps ポータル Api で OAuth 2.0 の暗黙的な許可を使用する方法を始めることができます。

### <a name="use-portal-oauth-token-with-an-external-web-api"></a>外部 Web API でポータルの OAuth トークンを使用する

このサンプルは ASP.NET ベースのプロジェクトであり、PowerApps ポータルによって発行された ID トークンを検証するために使用されます。 完全なサンプルについては、「[外部 WEB API でのポータルの OAuth トークンの使用](https://github.com/microsoft/PowerApps-Samples/tree/master/portals/ExternalWebApiConsumingPortalOAuthTokenSample)」を参照してください。

### <a name="authorize-endpoint-sample"></a>エンドポイントの承認のサンプル

このサンプルでは、承認エンドポイントが、リダイレクトされた URL で ID トークンをフラグメントとして返す方法を示します。 また、暗黙的な許可でサポートされている状態の検証についても説明します。 このサンプルについては、「[承認エンドポイントのサンプル](https://github.com/microsoft/PowerApps-Samples/blob/master/portals/AuthorizeEndpoint.js)」を参照してください。

### <a name="token-endpoint-sample"></a>トークンエンドポイントのサンプル

このサンプルでは、getAuthenticationToken 関数を使用して、PowerApps ポータルのトークンエンドポイントを使用して ID トークンを取得する方法を示します。 このサンプルについては、「[トークンエンドポイントのサンプル](https://github.com/microsoft/PowerApps-Samples/blob/master/portals/TokenEndpoint.js)」を参照してください。
