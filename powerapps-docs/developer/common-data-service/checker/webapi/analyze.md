---
title: 分析の呼び出し | Microsoft Docs
description: PowerApps チェッカーの Web API を使用して POST 要求を構成し、分析要求ジョブを開始する方法を説明します。
ms.custom: ''
ms.date: 06/04/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: a2c771f4-7eb6-4445-af2d-f775619ac3e8
caps.latest.revision: 21
author: mhuguet
ms.author: mhuguet
ms.reviewer: pehecke
manager: maustinjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---

# <a name="invoke-analysis"></a>分析の呼び出し

[!INCLUDE [cc-beta-prerelease-disclaimer](../../../../includes/cc-beta-prerelease-disclaimer.md)]

分析ジョブは、`POST` 要求を `analyze` ルートに送信することによって開始されます。 分析は、通常 1 分以上続く長時間のプロセスです。 API はまず何らかの基本的な検証を行い、ジョブを送信することでバックエンドで要求を開始し、そしてス状態コード 202 と `Location` ヘッダー、あるいは適切なエラーの詳細で応答します。 `Location` ヘッダー値は、要求の状態を確認し、その結果の URL を取得するために使うことができます。 ルールやルールセットのリスト、分析から除外するファイルなど、基準に基づいてジョブを調整する `POST` アクションによるさまざまなオプションがあります。 次を使用して分析を開始できます。`[Geographical URL]/api/analyze?api-version=1.0`。


> [!NOTE]
>  状態チェックの間隔は 15～60 秒空けることをお勧めします。 分析の実行には通常 1～5 分かかります。<br /> この API には OAuth トークンが必要です。

<a name="bkmk_headers"></a>

## <a name="headers"></a>ヘッダー

|Name|型|予想値|必須?|
|---|---|---|---|
|認証|文字列|Azure Active Directory (AAD) アプリケーション ID クレームを含む OAuth 1 ベアラー トークン。|はい|
|x-ms-tenant-id|GUID|アプリケーションのテナントの ID。|はい|
|x-ms-correlation-id|GUID|分析実行の識別子。 実行全体 (アップロード、分析、状態) に同じ ID を指定する必要があります。|はい|
|引き受け|object|`application/json, application/x-ms-sarif-v2`|はい|
|言語の承諾|文字列|言語コード (たとえば、 en-US)。 既定値は en-US です。 複数の言語が提供されている場合は、最初の言語が優先されます。 ただし、すべての翻訳 (言語がサポートされている場合) が含まれます。|いいえ

<a name="bkmk_body"></a>

## <a name="body"></a>本文

### <a name="commonly-used-options"></a>通常オプション:

|プロパティ|型|予想値|必須?|
|---|---|---|---|
|sasUriList|文字列の配列|単一のソリューション、複数のソリューション ファイルを含む zip ファイル、またはパッケージをダウンロードするためのサービス アクセスを提供する URI の一覧。|あり|
|ruleSets|カスタムの配列|0 以上|なし|
|ruleSets.id|guid|ルールセットの ID。ルールセット API のクエリを行うことにより見つけることができます。|いいえ、でもこれは通常使うものです。 これか、ruleCodes を使う必要があります。|
|ruleCodes.code|文字列|望ましいルールの ID。ルールセット API およびルール API のクエリを行うことにより見つけることができます。|いいえ、これか、ruleSets を使う必要があります。|
|fileExclusions|文字列の配列|除外するファイル名またはファイル名パターンの一覧。 ファイル名の先頭または末尾にワイルドカードとして "*" を使用するためのサポートが存在します (たとえば、\*jquery.dll および \*jquery\*)。|なし|

<a name="bkmk_responses"></a>

## <a name="expected-responses"></a>予想回答

|HTTP 状態コード|シナリオ|結果|
|---|---|---|
|202|分析要求が受け入れられ、状態チェック URI が `Location` ヘッダーに返されました|本体に結果が見つかりませんでした
|400|zip 以外のファイルが送信されたか、パラメーターが正しくないか、ファイルにウイルスに含まれていました|本体に結果が見つかりませんでした|
|409|重複した `x-ms-correlation-id` ヘッダー値の要求が送られました|本体に結果が見つかりませんでした|

### <a name="expected-response-headers"></a>予想回答ヘッダー

|Name|型|予想値|必須?|
|---|---|---|---|
|Location|Uri|現在の状態のクエリと結果の取得に使用する URL|はい|

<a name="bkmk_analyzeExample"></a>

## <a name="example-initiate-an-analysis"></a>例: 分析の開始

これは、_AppSource 認証_ ルールセット、単一ファイル、そして名前にテキスト _jquery_ および _json_ を含む除外ファイルで分析ジョブを開始する例です。

**要求**

```http
POST [Geographical URI]/api/analyze?api-version=1.0
Accept: application/json
Content-Type: application/json; charset=utf-8
x-ms-correlation-id: 9E378E56-6F35-41E9-BF8B-C0CC88E2B832
x-ms-tenant-id: F2E60E49-CB87-4C24-8D4F-908813B22506

{
    "ruleSets": [{
        "id": "0ad12346-e108-40b8-a956-9a8f95ea18c9"
    }],
    "sasUriList": ["https://testenvfakelocation.blob.core.windows.net/mySolution.zip"],
    "fileExclusions": ["*jquery*", "*json*"]
}
```

**応答**

```http
HTTP/1.1 202 Accepted
Content-Type: application/json; charset=utf-8
Location: [Geographical URI]/api/status/9E378E56-6F35-41E9-BF8B-C0CC88E2B832&api-version=1.0
```

### <a name="see-also"></a>関連項目

[PowerApps チェッカーの Web API を使用する](overview.md)<br />
[ルールセットの一覧の取得](retrieve-rulesets.md)<br />
[ルールの一覧の取得](retrieve-rules.md)<br />
[ファイルのアップロード](upload-file.md)<br />
[分析状態の確認](check-status.md)<br />
