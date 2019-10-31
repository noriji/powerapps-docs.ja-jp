---
title: ポータル内で OAuth 2.0 暗黙的許可フローを使用する | MicrosoftDocs
description: クライアント側で外部 API を呼び出す方法と、Dynamics 365 ポータルで OAuth の暗黙的な許可フローを使用してそれらを保護する方法を説明します。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: null
ms.date: 08/30/2019
ms.author: shjais
ms.reviewer: null
---

# <a name="use-oauth-20-implicit-grant-flow-within-your-portal"></a>ポータル内で OAuth 2.0 の暗黙的な許可フローを使用する 

この機能により、顧客はクライアント側で外部 API を呼び出して、OAuth の暗黙的な許可フローを使用してそれらを保護できます。 これは、OAuth 2.0 の暗黙的な許可フローに従った承認で外部 API によって使用される、ユーザー ID 情報を含む安全なアクセス トークンを取得するためのエンドポイントを提供します。 サインインしたユーザーの ID 情報は、安全な方法で外部 AJAX 呼び出しに渡されます。 これは開発者が認証コンテキストを渡すのに役立つだけでなく、このメカニズムを使うことでユーザーが API を安全にするのを助けます。

OAuth 2.0 の暗黙的な許可フローは、クライアントが ID トークンを取得するために呼び出せるエンドポイントをサポートします。 この目的で使用されるふたつのエンドポイント: [承認](#authorize-endpoint-details) と [トークン](#token-endpoint-details)。

## <a name="authorize-endpoint-details"></a>エンドポイントの詳細を承認する 

承認エンドポイントの URL は: `<portal_url>/_services/auth/authorize`。 承認エンドポイントは次のパラメーターをサポートします:

| パラメーター   | 必須? | 説明                             |
|---------------|-----------|---------------------------------------|
| client_id      | あり       | 承認エンドポイントへの呼び出し時に渡される文字列。 クライアント ID は [ポータルに登録されている](#register-client-id-for-implicit-grant-flow) 必要があります。 そうでない場合はエラーが表示されます。 クライアント ID はトークンのクレームに `aud` や `appid` パラメータとして追加され、返されたトークンが自分のアプリ用であることを検証するためにクライアントが使用できます。<br>最大長は 36 文字です。 英数字とハイフンのみがサポートされます。 |
| redirect_uri      | あり       | 認証応答を送受信できるポータルの URL。 コールで使用された特定の `client_id` に登録される必要があり、そして登録されたものと全く同じ値である必要があります。            |
| 状態       | なし        | トークン応答にも返される要求に含まれる値。 使用したいどんなコンテンツの文字列でも構いません。 通常はランダムに生成された一意の値が、クロスサイト リクエスト フォージェリ攻撃を防ぐために使用されます。<br>最大長は 20 文字です。              |
| その場合   | なし        | クライアントから送信された文字列値で、結果の ID トークンに要求として含まれます。 そしてクライアントはこの値を検証してトークンリプレイ攻撃を軽減できます。 最大長は 20 文字です。      |
| response_type         | なし        | このパラメーターは `token` だけを値としてサポートします。 これにより、承認エンドポイントに 2 度目の要求を行うことなく、アプリは承認エンドポイントから直ちにアクセス トークンを受け取ることができます。                               |
|||

### <a name="successful-response"></a>正常な応答

承認エンドポイントは、以下の値を応答 URL でフラグメントとして返します:

- **トークン**: トークンはポータルの秘密鍵でデジタル署名された JSON Web トークン (JWT) として返されます。
- **状態**: 状態パラメーターが要求に含まれる場合、同じ値が応答に表示されます。 アプリは要求と応答の状態値が同じであることを確認する必要があります。
- **expires_in**: アクセス トークンの有効期間 (秒単位)。

たとえば、正常な応答は下記のようです:

```
GET https://aadb2cplayground.azurewebsites.net/#token=eyJ0eXAiOiJKV1QiLCJhbGciOI1NisIng1dCI6Ik5HVEZ2ZEstZnl0aEV1Q&expires_in=3599&state=arbitrary_data_you_sent_earlier
```

### <a name="error-response"></a>エラー応答

承認エンドポイントのエラーは、次の値の JSON ドキュメントとして返されます:

- **エラー ID**: エラーの一意の識別子です。
- **エラー メッセージ**: 認証エラーの根本原因を特定するのに役立つ特定のエラー メッセージ。
- **関連付け ID**: デバッグ目的に使用される GUID。 診断ログを有効にすると、関連付け ID はサーバー エラー ログに表示されます。
- **Timestamp**: エラーが発生した日時。

エラー メッセージはサインインしたユーザーの既定言語で表示されます。 ユーザーがサインインしていない場合は、ユーザーにサインインを促すサインイン ページが表示されます。 たとえば、エラー応答は下記のようです:

```
{"ErrorId": "PortalSTS0001", "ErrorMessage": "Client Id provided in the request is not a valid client Id registered for this portal. Please check the parameter and try again.", "Timestamp": "4/5/2019 10:02:11 AM", "CorrelationId": "7464eb01-71ab-44bc-93a1-f221479be847" }
```

## <a name="token-endpoint-details"></a>トークン エンドポイントの詳細

`/token` エンドポイントに要求してトークンを取得することもできます。 承認エンドポイントがトークン ロジックを別のページ (redirect_uri) で処理する方法は承認エンドポイントと異なります。そのため、トークンエンドポイントは同じページ上のトークン ロジックを処理します。 トークン エンドポイントの URL は: `<portal_url>/_services/auth/token`。 トークン エンドポイントは次のパラメーターをサポートします:

| パラメーター   | 必須? | 説明                             |
|---------------|-----------|---------------------------------------|
| client_id      | なし       | 承認エンドポイントへの呼び出し時に渡される文字列。 クライアント ID は [ポータルに登録されている](#register-client-id-for-implicit-grant-flow) 必要があります。 そうでない場合はエラーが表示されます。 クライアント ID はトークンのクレームに `aud` や `appid` パラメータとして追加され、返されたトークンが自分のアプリ用であることを検証するためにクライアントが使用できます。<br>最大長は 36 文字です。 英数字とハイフンのみがサポートされます。 |
| redirect_uri      | なし       | 認証応答を送受信できるポータルの URL。 コールで使用された特定の `client_id` に登録される必要があり、そして登録されたものと全く同じ値である必要があります。            |
| 状態       | なし        | トークン応答にも返される要求に含まれる値。 使用したいどんなコンテンツの文字列でも構いません。 通常はランダムに生成された一意の値が、クロスサイト リクエスト フォージェリ攻撃を防ぐために使用されます。<br>最大長は 20 文字です。              |
| その場合   | なし        | クライアントから送信された文字列値で、結果の ID トークンに要求として含まれます。 そしてクライアントはこの値を検証してトークンリプレイ攻撃を軽減できます。 最大長は 20 文字です。      |
| response_type         | なし        | このパラメーターは `token` だけを値としてサポートします。 これにより、承認エンドポイントに 2 度目の要求を行うことなく、アプリは承認エンドポイントから直ちにアクセス トークンを受け取ることができます。                               |
|||

> [!NOTE]
> `client_id`、`redirect_uri`、`state` そして `nonce` パラメータはオプションですが、統合の安全を確実にするために使用することをお勧めします。

### <a name="successful-response"></a>正常な応答

トークン エンドポイントは状態と expires_in を応答ヘッダーとして返し、トークンをフォームの本文に返します。

### <a name="error-response"></a>エラー応答

トークン エンドポイントのエラーは、次の値の JSON ドキュメントとして返されます:

- **エラー ID**: エラーの一意の識別子です。
- **エラー メッセージ**: 認証エラーの根本原因を特定するのに役立つ特定のエラー メッセージ。
- **関連付け ID**: デバッグ目的に使用される GUID。 診断ログを有効にすると、関連付け ID はサーバー エラー ログに表示されます。
- **Timestamp**: エラーが発生した日時。

エラー メッセージはサインインしたユーザーの既定言語で表示されます。 ユーザーがサインインしていない場合は、ユーザーにサインインを促すサインイン ページが表示されます。 たとえば、エラー応答は下記のようです:

```
{"ErrorId": "PortalSTS0001", "ErrorMessage": "Client Id provided in the request is not a valid client Id registered for this portal. Please check the parameter and try again.", "Timestamp": "4/5/2019 10:02:11 AM", "CorrelationId": "7464eb01-71ab-44bc-93a1-f221479be847" }
```

## <a name="validate-id-token"></a>ID トークンの検証

ID トークンを取得するだけではユーザーの認証に十分ではありません; トークンの署名を検証し、アプリの要件に基づいてトークン内の要求を確認する必要もあります。 公開トークン エンドポイントはポータルの公開鍵を提供し、それをポータルが提供したトークンの署名を検証するために使用できます。 公開トークン エンドポイントの URL は: `<portal_url>/_services/auth/publickey`。

## <a name="turn-implicit-grant-flow-on-or-off"></a>暗黙的な許可フローをオンまたはオフにする

既定で、暗黙的な許可フローは有効です。 暗黙的な許可フローをオフにしたい場合は **Connector/ImplicitGrantFlowEnabled** サイト設定の値を **False** にします。

このサイト設定がポータルで利用できない場合は、適切な値で [新しいサイト設定を作成](configure-site-settings.md#manage-portal-site-settings) する必要があります。

## <a name="configure-token-validity"></a>トークンの有効性を構成する

既定では、トークンは15分間有効です。 トークンの有効性を変更する場合は **ImplicitGrantFlow/TokenExpirationTime** サイト設定の値を必要な値に設定してください。 値は秒単位で指定する必要があります。 最大値で 1 時間が可能で、最小値は 1 分にする必要があります。 不正な値 (たとえば英数字) が指定されると、既定値の 15 分が使用されます。 最大値より大きい値や最小値より小さい値を指定した場合、既定では最大値と最小値がそれぞれ使用されます。

たとえばトークンの有効期間を 30 分に設定するには **ImplicitGrantFlow/TokenExpirationTime** サイト設定の値を **1800** にします。 トークンの有効期間を 1 時間に設定するには **ImplicitGrantFlow/TokenExpirationTime** サイト設定の値を **3600** にします。

## <a name="register-client-id-for-implicit-grant-flow"></a>暗黙的な許可フローにクライアント ID を登録する

このフローが許可されたポータルにクライアント ID を登録する必要があります。 クライアント ID を登録するには、次のサイト設定を作成する必要があります:

|サイト設定|Value|
|------|------|
|ImplicitGrantFlow/RegisteredClientId|このポータルで許可されている有効なクライアント ID 値。 値はセミコロンで区切る必要があり、英数字とハイフンを使用できます。 最大長は 36 文字です。|
|ImplicitGrantFlow/{ClientId}/RedirectUri|特定のクライアント ID に許可された有効なリダイレクト URI。 値はセミコロンで区切る必要があります。 提供された URL はポータルの有効なWeb ページである必要があります。|
|||

## <a name="sample-code"></a>サンプル コード

以下のサンプルコードを使用することで、Dynamics 365 ポータル API で OAuth 2.0 の暗黙的な許可を利用することができます。

### <a name="use-portal-oauth-token-with-an-external-web-api"></a>外部Web API でポータル OAuth トークンを使用する

このサンプルは、ASP.NET ベースのプロジェクトで、Dynamics 365 ポータルが発行する ID トークンの検証に使用されます。 この完全なサンプルは、 [外部Web API でポータル OAuth トークンを使用する](https://github.com/microsoft/PowerApps-Samples/tree/master/portals/ExternalWebApiConsumingPortalOAuthTokenSample) で確認することができます。

### <a name="authorize-endpoint-sample"></a>Authorize Endpoint のサンプル

この例では、Authorize Endpoint がリダイレクト先URLの断片としてIDトークンを返す方法を示しています。 また、暗黙的な許可でサポートしている状態検証に対応しています。 サンプルでは、 [Authorize Endpointのサンプル](https://github.com/microsoft/PowerApps-Samples/blob/master/portals/AuthorizeEndpoint.js) で確認することができます。

### <a name="token-endpoint-sample"></a>トークン エンドポイントのサンプル

このサンプルは、getAuthenticationToken 関数と Dynamics 365 ポータルのトークン エンドポイントを使用して、 ID トークンをフェッチする方法を示しています。 このサンプルは、 [トークン エンドポイントのサンプル](https://github.com/microsoft/PowerApps-Samples/blob/master/portals/TokenEndpoint.js) で確認することができます。
