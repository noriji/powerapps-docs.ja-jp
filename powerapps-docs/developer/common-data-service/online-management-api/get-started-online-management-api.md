---
title: Common Data Service のオンライン管理 API に関する入門 | MicrosoftDocs
description: Common Data Service のための Online Admin API の開始に役立つ基本情報を提供します。
ms.date: 09/30/2019
ms.service: powerapps
ms.topic: conceptual
ms.assetid: c292c148-01f0-41f6-a2fe-7ed05a01a733
author: KumarVivek
ms.author: kvivek
manager: annbe
search.audienceType:
  - developer
search.app:
  - PowerApps
---
# <a name="get-started-with-online-management-api"></a>Online Management API に関する入門情報 

このトピックでは、Common Data Service のための Online Admin API の開始に役立つ基本情報を提供します。

## <a name="office-365-admin-roles"></a>Office 365 管理者ロール

Online Management API を使用するには、 Office 365 のテナントで割り当てられた次の管理者ロールのいずれかを持っている必要があります:

- グローバル管理者
- サービス管理者

これらのロールについては、 [ Office 365 の管理者ロールについて](https://support.office.com/en-us/article/About-Office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d)を参照してください。

## <a name="service-url"></a>サービス URL

サービス URL は REST APIにアクセスするためのエンドポイント アドレスを定義します。 Online Management API を使用して操作を実行するには、次の形式で URL を指定する必要があります:

`{ServiceUrl}/api/v1.2/{resource}`

たとえば、北米の Office 365 テナントのインスタンスを取得するには、 **入手** リクエストで次の URL に渡すことができます:

`https://admin.services.crm.dynamics.com/api/v1.2/instances`


以下の表は、世界中の Office 365 データセンターの Online Management API のサービス URL を示しています。

|場所 | サービス URL |
|---------|-------------|
|北米 | https://admin.services.crm.dynamics.com |
|北米 2 | https://admin.services.crm9.dynamics.com |
|ヨーロッパ、中東、およびアフリカ (EMEA) | https://admin.services.crm4.dynamics.com |
|アジア太平洋 (APAC) | https://admin.services.crm5.dynamics.com |
|オセアニア | https://admin.services.crm6.dynamics.com |
|日本 (JPN) | https://admin.services.crm7.dynamics.com |
|南米 | https://admin.services.crm2.dynamics.com |
|インド (IND) | https://admin.services.crm8.dynamics.com |
|カナダ | https://admin.services.crm3.dynamics.com |
|英国 (UK) | https://admin.services.crm11.dynamics.com |
|フランス | https://admin.services.crm12.dynamics.com |

## <a name="standard-headers"></a>標準ヘッダー

Online Management API は、次の規格要求および応答ヘッダーがあります。

### <a name="request-headers"></a>要求ヘッダー

| ヘッダー​​ | 種類​​ | 内容  |
|--------|------|--------------|
|**言語の承諾**|String|応答に優先する言語を指定します。 ヘッダーに関する詳細: [言語の承諾 (MDN Webドキュメント) ](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Accept-Language)|
|**認証**|String|資格情報を指定して、Online Management API サービスでユーザーを認証します。 ヘッダーに関する詳細: [認証 (MDN Web ドキュメント) ](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Authorization)|

要求でのこれらのヘッダーの設定については、「[Online Management API の使用を認証](authentication.md)」を参照してください。

### <a name="response-headers"></a>応答ヘッダー

| ヘッダー​​ | 内容  |
|--------|--------------|
|**操作場所**|長期実行操作の場合、操作照会の位置を確認するための操作照会の場所を指定します。 たとえば、次のようになります。<br />`https://admin.services.crm.dynamics.com/operations/{operationid}`|
|**後に試行**|長期実行操作の場合は、操作状況を再度照会するまでの推奨期間を秒単位で指定します。 例: **30**|
    
### <a name="related-topics"></a>関連トピック  

[Online Management API の使用を認証する](authentication.md)

[Online Management API でサポートする操作](operations-supported.md)

[Online Management API 参照](/rest/api/admin.services.crm.dynamics.com)
