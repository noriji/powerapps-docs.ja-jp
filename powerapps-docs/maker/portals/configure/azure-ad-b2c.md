---
title: ポータルの Azure AD B2C プロバイダーの設定 |MicrosoftDocs
description: ポータルの Azure AD B2C プロバイダー設定を有効にする手順。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/18/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: aead447bbab7f6e5758cdea0a9c6be5c0e8f41e2
ms.sourcegitcommit: 57b968b542fc43737330596d840d938f566e582a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2019
ms.locfileid: "72978395"
---
# <a name="azure-ad-b2c-provider-settings-for-portals"></a>ポータルの Azure AD B2C プロバイダーの設定

[!include[Azure](../../../includes/pn-azure-shortest.md)] Active Directory (Azure AD) は、従業員または内部認証のために Office 365 および Dynamics 365 サービスの電源を入れます。 [!include[Azure](../../../includes/pn-azure-shortest.md)] Active Directory B2C は、その認証モデルの拡張機能であり、ローカルの資格情報を使用した外部の顧客サインインと、さまざまな一般的なソーシャル id プロバイダーとのフェデレーションを可能にします。

ポータルの所有者は、ポータルで id プロバイダーとして [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C を受け入れるように構成できます。 [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C では、フェデレーションの Open ID Connect がサポートされています。

ポータルの id プロバイダーとして [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C を構成するプロセスでは、ポータルの構成時に後で使用する複数の値が生成されます。 これらの値は、次の表で確認できます。 ポータルの構成中に、変数名をここでメモした値に置き換えます。

| 変数名     | Value | Description                                                           |
|-------------------|-------|-----------------------------------------------------------------------|
| アプリケーション名  |       | 証明書利用者としてポータルを表すアプリケーションの名前 |
| アプリケーション ID    |       | Azure Active Directory B2C で作成されたアプリケーションに関連付けられているアプリケーション ID。  |
| ポリシー-サインイン URL |       | メタデータエンドポイントで定義されている発行者 (iss) の URL。                |
| フェデレーション-名前   |       | ' B2C ' などのフェデレーションプロバイダーの種類を識別する一意の名前。 これは、この特定のプロバイダーの構成設定をグループ化するために、サイト設定名に使用されます。                                                                      |
| | | |

### <a name="use-azure-ad-b2c-as-an-identity-provider-for-your-portal"></a>ポータルの id プロバイダーとして Azure AD B2C を使用する

1. [Azure portal](https://portal.azure.com/)にサインインします。
2. [Azure AD B2C テナントを作成](https://docs.microsoft.com/azure/active-directory-b2c/active-directory-b2c-get-started)します。
3. 左端のナビゲーションバーで [ **[!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C** ] を選択します。
4. [Azure アプリケーションを作成](https://docs.microsoft.com/azure/active-directory-b2c/active-directory-b2c-app-registration#register-a-web-application)します。

   > [!Note]
   > **[暗黙的なフローを許可]** する フィールドで [**はい]** を選択し、 **[応答 URL]** フィールドにポータルの URL を指定する必要があります。 **[応答 URL]** フィールドの値は、[ポータルドメイン]/Signin-[フェデレーション名] の形式にする必要があります。 たとえば、`https://contosocommunity.microsoftcrmportals.com/signin-B2C`のようにします。

5. アプリケーション名をコピーし、前の表のアプリケーション名の値として入力します。
6. [アプリケーション ID] をコピーし、前の表の [アプリケーション ID] の値として入力します。
7. [サインアップまたはサインインポリシーを作成](https://docs.microsoft.com/azure/active-directory-b2c/active-directory-b2c-reference-policies#create-a-sign-up-or-sign-in-policy)します。
8. ポリシーを選択し、 **[編集]** を選択します。
9. [**トークン]、[セッション & SSO 構成**] を選択します。
10. **[発行者 (iss) 要求]** の一覧から、パスに **/tfp**が含まれている URL を選択します。
11. ポリシーを保存します。
12. **[このポリシーのメタデータエンドポイント]** フィールドで URL を選択します。
13. [発行者] フィールドの値をコピーし、前の表のポリシーとサインインの URL の値として入力します。 

## <a name="portal-configuration"></a>ポータルの構成

[!include[Azure](../../../includes/pn-azure-shortest.md)]で B2C テナントを作成して構成した後、Open ID Connect プロトコルを使用して [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C とフェデレーションするようにポータルを構成する必要があります。 B2C&mdash;などの AD B2C&mdash;を [!include[Azure](../../../includes/pn-azure-shortest.md)] するには、フェデレーションの一意の名前を作成し、上記の表の*federation-name*変数の値として保存する必要があります。

### <a name="configure-your-portal"></a>ポータルの構成
1. ポータル管理アプリを開きます。
2. **ポータル** > **web サイト**にアクセスします。
3. [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C を有効にする必要がある web サイトレコードを選択します。
4. **[サイトの設定]** にアクセスします。
5. 次のサイト設定を作成します。
   -   **名前**: Authentication/OpenIdConnect/[Federation-Name]/Authority

       **値**: [ポリシー-サインイン URL]
   -   **名前**: Authentication/OpenIdConnect/[Federation-Name]/ClientId

       **値**: [アプリケーション ID]
   -   **名前**: Authentication/OpenIdConnect/[Federation-Name]/redirecturi

       **値**: [ポータルドメイン]/Signin-[フェデレーション名]

       たとえば、`https://mysite.com/signin-b2c` 
6. フェデレーションサインアウトをサポートするには、次のサイト設定を作成します。
   - **名前**: Authentication/OpenIdConnect/[Federation-Name]/externallogoutenabled

     **値**: true
7. 1つの id プロバイダーにポータルをハードコーディングするには、次のサイト設定を作成します。
   - **名前**: Authentication/Registration/LoginButtonAuthenticationType

     **値**: [ポリシー-サインイン URL]

8. パスワードのリセットをサポートするには、[ここで](#password-reset)説明する必要なサイト設定を作成します。
9. 要求のマッピングをサポートするには、[ここで](#claims-mapping)説明する必要なサイト設定を作成します。

関連するサイト設定の完全な一覧については、[こちら](#related-site-settings)を参照してください。

### <a name="password-reset"></a>パスワードのリセット

[!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C ローカルアカウントを使用したパスワードのリセットをサポートする場合は、次のサイト設定が必要です。

| サイト設定                                                        | Description                                                                                                          |
|---------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------|
| Authentication/OpenIdConnect/[Federation-Name/PasswordResetPolicyId | パスワードリセットポリシーの ID。                                                                                     |
| Authentication/OpenIdConnect/[Federation-Name]/ValidIssuers         | [ポリシー-サインイン URL] とパスワードリセットポリシーの発行者を含む、発行者のコンマ区切りの一覧。 |
|Authentication/OpenIdConnect/[Federation-Name]/defaultpolicyid | サインインまたはサインアップポリシーの ID。|
|||

### <a name="related-site-settings"></a>関連サイトの設定

ポータルで次のサイト設定を作成または構成して、id プロバイダーとして [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C をサポートすることができます。


| サイト設定                                                         | Description                                                                                                                                                                                                                                                        |
|----------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Authentication/Registration/ProfileRedirectEnabled                   | サインインに成功した後に、ポータルがユーザーをプロファイルページにリダイレクトできるかどうかを指定します。 既定では、true に設定されています。                                                                                                                                            |
| 認証/登録/EmailConfirmationEnabled                 | 電子メールの検証が必要かどうかを指定します。 既定では、true に設定されています。                                                                                     |
| Authentication/Registration/LocalLoginEnabled                        | ローカルサインインが必要かどうかを指定します。 既定では、true に設定されています。                                                                        |
| 認証/登録/ExternalLoginEnabled                     | 外部認証を有効または無効にします。       |
| 認証/登録/AzureADLoginEnabled                      | 外部 id プロバイダーとして [!include[Azure](../../../includes/pn-azure-shortest.md)] AD を有効または無効にします。 既定では、true に設定されています。                                                                                                                                                                      |
| Authentication/OpenIdConnect/[Federation-Name]/externallogoutenabled | フェデレーションサインアウトを有効または無効にします。True に設定すると、ユーザーはポータルからサインアウトするときに、フェデレーションサインアウトユーザーエクスペリエンスにリダイレクトされます。 False に設定すると、ユーザーはポータルからのみサインアウトされます。 既定では、false に設定されています。               |
| Authentication/LoginTrackingEnabled                                  | ユーザーの最後のサインインの追跡を有効または無効にします。 True に設定すると、連絡先レコードの [**最後に成功**したサインイン] フィールドに日付と時刻が表示されます。 既定では、これは false に設定されています。                                                            |
| Authentication/OpenIdConnect/[Federation-Name]/registrationenabled   | 既存の id プロバイダーの登録要件を有効または無効にします。 True に設定すると、サイト設定の [認証/登録/有効化] も [true] に設定されている場合にのみ、既存のプロバイダーに対して登録が有効になります。 既定では、true に設定されています。 |
|Authentication/OpenIdConnect/[Federation-Name]/postlogoutredirecturi |ユーザーがサインアウトした後にリダイレクトする、ポータル内の URL を指定します。 |
| | |

### <a name="related-content-snippet"></a>関連するコンテンツスニペット

ユーザーが招待を受けた後にユーザーの登録が無効になっている場合は、次のコンテンツスニペットを使用してメッセージを表示します。

**名前**: Account/Register/RegistrationDisabledMessage

**値**: 登録が無効になっています。

## <a name="customize-the-includeazureincludespn-azure-shortestmd-ad-b2c-user-interface"></a>[!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C ユーザーインターフェイスをカスタマイズする

[!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C では、ユーザーインターフェイスのカスタマイズがサポートされています。 サインアップとサインインのシナリオでユーザーエクスペリエンスをカスタマイズできます。

### <a name="step-1-create-a-web-template"></a>手順 1: web テンプレートを作成する
次の値を使用して、web テンプレートを作成します。

**[名前]** : [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C カスタムページ

**ソース**: 次のサンプル web テンプレートソース HTML を使用します。

```html
<!DOCTYPE html>
<html lang=en-US>
  <head>
    <meta charset=utf-8>
    <meta name=viewport content=width=device-width, initial-scale=1.0>
    <meta http-equiv=X-UA-Compatible content=IE=edge>
    <title>
      {{ page.title | h }}
    </title>
                        <link href={{ request.url | base }}/bootstrap.min.css rel=stylesheet>
                        <link href={{ request.url | base }}/theme.css rel=stylesheet>
                        <style>
                          .page-heading {
            padding-top: 20px;
      }
      .page-copy {
            margin-bottom: 40px;
      }
      .highlightError {
        border: 1px solid #cb2027!important;
        background-color: #fce8e8!important;
      }
      .attrEntry .error.itemLevel {
        display: none;
        color: #cb2027;
        font-size: .9em;
      }
      .error {
        color: #cb2027;
      }
      .entry {
        padding-top: 8px;
        padding-bottom: 0!important;
      }
      .entry-item {
        margin-bottom: 20px;
      }
      .intro {
        display: inline;
        margin-bottom: 5px;
      }
      .pageLevel {
          width: 293px;
          text-align: center;
          margin-top: 5px;
          padding: 5px;
          font-size: 1.1em;
          height: auto;
      }
      #panel, .pageLevel, .panel li, label {
          display: block;
      }
      #forgotPassword {
          font-size: .75em;
          padding-left: 5px;
      }
      #createAccount {
          margin-left: 5px;
      }
      .working {
          display: none;
          background: url(data:image/gif;base64,R0lGODlhbgAKAPMAALy6vNze3PTy9MTCxOTm5Pz6/Ly+vNTS1Pz+/�N0Jp6BUJ9EBIISAQAh+QQJCQAKACxRAAIABgAGAAAEE1ClYU4RIIMTdCaegVCfRASCEgEAOw==) no-repeat;
          height: 10px;
          width: auto;
      }
      .divider {
        margin-top: 20px;
        margin-bottom: 10px;
      }
      .divider h2 {
        display: table;
        white-space: nowrap;
        font-size: 1em;
        font-weight: 700;
      }
      .buttons {
        margin-top: 10px;
      }
      button {
            width:auto;
            min-width:50px;
            height:32px;
            margin-top:2px;
            -moz-border-radius:0;
            -webkit-border-radius:0;
            border-radius:0;
            background:#2672E6;
            border:1px solid #FFF;
            color:#fff;
            transition:background 1s ease 0s;
            font-size:100%;
            padding:0 2px
      }

      button:hover {
            background:#0F3E83;
            border:1px solid #3079ed;
            -moz-box-shadow:0 0 0;
            -webkit-box-shadow:0 0 0;
            box-shadow:0 0 0
      }
      .password-label label {
        display: inline-block;
        vertical-align: baseline;
      }
      img {
            border:0
      }
      .divider {
            margin-top:20px;
            margin-bottom:10px
      }
      .divider h2 {
            display:table;
            white-space:nowrap;
            font-size:1em;
            font-weight:700
      }
      .divider h2:after,.divider h2:before {
            border-top:1px solid #B8B8B8;
            content:'';
            display:table-cell;
            position:relative;
            top:.7em;
            width:50%
      }
      .divider h2:before {
            right:1.8%
      }
      .divider h2:after {
            left:1.8%
      }
      .verificationErrorText {
            color:#D63301
      }
      .options div {
            display:inline-block;
            vertical-align:top;
            margin-top:7px
      }
      .accountButton,.accountButton:hover {
            background-image:url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACAAAAAgCAMAAABEpIrGAAAAh1BMVEX///9QUFBOTk5LS0tERERCQkI/Pz9ISEg6OjpGRkZNTU08PDyAgID09PSlpaWWlpZxcXFgYGBZWVlUVFT6+vrx8fHt7e3s7Ozo6Oji4uLJycnGxsa4uLiqqqqgoKCNjY2JiYmGhoZra2tmZmb7+/vu7u7d3d3U1NTNzc2+vr67u7usrKx7e3vprNQnAAAA8klEQVQ4y63Q127DMAxAUZpDwyMeSdqsNqu7/f/va6zahgGJKAr0vgk6DyQh+6V/BiTOOeNRA9zuAWBdM6WBlPDTvaUUoAuMrT0mgNvA1IJjQB3MKjACvp6DK0WAH+agtH8H9jQHLUUgz7Uhx8xOXzNESxirLCYA2mw8tacI5FyIYXq8A9ge2Qs6oTnw2e2ruho2rjBcXJ4ADh3jBOQLQnVhRFx2gNDZ4ACogbHXj/ft9Dj5AcgbJFu5AThQWuYBIGmgtAFQo4EFB+CPGthJAPypgY3BHsheA5UNwLyAvsYNoDyroKUe4EoFTQ/yDtTONvsGUJ8KTUYyH+UAAAAASUVORK5CYII=);
            background-repeat:no-repeat
      }
      .accountButton {
            border:1px solid #FFF;
            color:#FFF;
            margin-left:0;
            margin-right:2px;
            transition:background-color 1s ease 0s;
            -moz-border-radius:0;
            -webkit-border-radius:0;
            border-radius:0;
            text-align:center;
            word-wrap:break-word;
            height:34px;
            width:158px;
            padding-left:30px;
            background-color:#505050;
      }
      .accountButton:hover {
            background-color:#B9B9B9;
            border:1px solid #FFF;
            -moz-box-shadow:0 0 0;
            -webkit-box-shadow:0 0 0;
            box-shadow:0 0 0
      }
      .accountButton:focus {
            outline:gold solid 1px
      }
      #MicrosoftAccountExchange {
            background-image:url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACAAAAAgCAMAAABEpIrGAAAAPFBMVEU1pe/////t+v4uoe5btvNixPVVwfUsoe9tyfXU7/y95vu24vrd9f5NtfLH6/ys3/o/sPE6qfD2/f+f2vnAysuQAAAAaElEQVQ4y93SORKAIAwFUEGCsoT1/nd1JkkDFhY24qt+8VMkk20lu6DAaVBOBsVKsuO8aYo08IqlYyxoRTQExfyKheRIgu5Yl4KoVhSUgNOhoiYRsmb5g2u+LtzXDNOhjKgoAZ9/8k8uZWsGqcIav5wAAAAASUVORK5CYII=);
            background-color:#33A7F2
      }
      #MicrosoftAccountExchange:hover {
            background-color:#ADDBF9
      }
      #GoogleExchange {
            background-image:url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACAAAAAgCAMAAABEpIrGAAAAb1BMVEXcTkH////cTD/bSj3ZQDLYOyzaRDbeV0vbSDrZPS/66Obyv7rsnpfpkorjcWfgZlvXOCr++Pj5393haFz88/L88fD67Or319T1zsv1zsrxuLPuqaLuqKLoi4LlfXTgYlbWMyTWMiPwtrHwta/fXVH/sCIIAAAAmElEQVQ4y+2RyQ7DIBBDMcwAIXvovqXb/39jRaX0AEmr5px3tSV7PGLhX6TVRFpN61l9zPNS6kn9gDcXO67zDnCnO2BCiNIyMtgKKJgyY2zQ68JEDtqju0nFTcOsxPUMw1GDDUqt+tY51/YNVlhvacTgEfCDIY0Q/lkBSg4RaUmmDo4/JdMzHy1Q2ejMeCj6PrXQP5+1MI8X0Y4HL4c826EAAAAASUVORK5CYII=);
            background-color:#DC4E41
      }
      #GoogleExchange:hover {
            background-color:#F1B8B3
      }
      #TwitterExchange {
            background-image:url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACAAAAAgCAMAAABEpIrGAAAAdVBMVEVgqd3///9Ypdtdp9xaptxSotpQodlNn9lWo9pUo9rX6Pa+2vGTw+iLvuZlqt79/P7K4PO62O+y0+6hyutysuD2+fzi7vne6/fT5PTE3fKs0O2lzeuZx+l7tuJqrd71+Pzz9vzn8PnQ4/SCueSAueNsrt9InNh7sQwBAAAAwklEQVQ4y92PRw6EMAwAXeIkdBbY3uv/n7gSAoLDD5hbPCPZgZVihEgYgNSUpmfS7bfbtHS2nReyL2Qoc+yp8ZRAwCEWjgGAPQ7sssKoAGsWBrrgyMZCwD77Uel+59E3Tt14xZ7qlY7BRf1CDgeMKMw8sBXGlKxWtLGvHCgkQ80m0YHpjjq4sQ74pn1mISLJVSAMiwJO98l/TWSNF1eGKzqKfZ7Vj0mnHHwodpP+WIYlZP373DTtVWxYr2FD3pOBdfIHhOAHYHQI9VgAAAAASUVORK5CYII=);
            background-color:#60A9DD
      }
      #TwitterExchange:hover {
            background-color:#BFDCF1
      }
      #FacebookExchange {
            background-image:url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACAAAAAgCAMAAABEpIrGAAAAaVBMVEU7W5z///85Wps3WJsiRo8xU5fw8vYyUpY0VZiAj70pS5OBkb0vUpb7+fwsTpTR1ud6irllerBPaqX09fnx8vfs7fSQoMZxg7VsgLNGY6FCX58ZP4v++/7r7vTZ3OupstGIlsFWcalDYaCK3qwDAAAAnklEQVQ4y+XQyw7CIBAFUBgc5VUoWGtb3/7/RyoYkyZAiSsXvdt7kstA/hRg/B0GpZ6byQ3Dw0NBaH+lMYRle3T0kwayACRdBrr/gnN+QtpQWv8cR4DswiUAjozlz4RdF8AmlnmwjaDQImoZwQkRedoToUS7D+ColGoTwQidx8oEQDMHN1MBva5MOL70SCHuE1TOhOpHrRt0FWAOP4IX8PsG2qEOR30AAAAASUVORK5CYII=);
            background-color:#3B5B9C
      }
      #FacebookExchange:hover {
            background-color:#B0BDD7
      }
      #LinkedInExchange {
            background-image:url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACAAAAAgCAMAAABEpIrGAAAAb1BMVEUAe7b///8AdrMklscAc7EAeLUAcbB5ttifzeMqmckAdLIAaqz7+/6PxeAShr0CgLkAba4nmMctksTv9Puw1eij0OWGvNtfrNJNo80YjMAeib/D4vGt3Oy82+yfzOOCvtyJvdx3tddirtI/ncoxmMj9KsrQAAAAw0lEQVQ4y9WSVw7DIAxAG8CkjJDVzO5x/zMWk0RNJaB/kfo+sGUeCMvstgI4J7F9aS5NxSLnTWLpZVDgexTqIiycUNBhgTxRyCKPYJ3dl7sITCkO+FyLXaWU310DscASOesf3ahWChGJ5cb4ASO5Joiu2EegWEmZa1c3yUwOHmHNuQgJup4CgF8YlKpcMhKvkNmb1REz6hdetsyziIBldv8lpH8ouGm28zQFCu2SOSAXlJYGYCgpFThEMFPm/zCryja8Acy7CRfMrcKPAAAAAElFTkSuQmCC);
            background-color:#0077B5
      }
      #LinkedInExchange:hover {
            background-color:#99CAE1
      }
      #AmazonExchange {
            background-image:url(https://images-na.ssl-images-amazon.com/images/G/01/lwa/btnLWA_gold_156x32.png);
            background-color:#FFF;
            color:transparent
      }

      #next {
            -moz-user-select:none;
            user-select:none;
            cursor:pointer;
            width:auto;
            padding-left:10px;
            padding-right:10px;
            height:30.5px;
            -moz-border-radius:0;
           -webkit-border-radius:0;
            border-radius:0;
            background:#2672E6;
            border:1px solid #FFF;
            color:#fff;
            transition:background 1s ease 0s;
            font-size:100%
      }
      #next:hover {
            background:#0F3E83;
            border:1px solid #FFF;
            box-shadow:0 0 0
      }
      #next:hover,.accountButton:hover {
            -moz-box-shadow:0 0 0;
            -webkit-box-shadow:0 0 0;
            box-shadow:0 0 0;
      }
                        </style>
  </head>
  <body>
    <div class=navbar navbar-inverse navbar-static-top role=navigation>
      <div class=container>
        <div class=navbar-header>
          <div class=visible-xs-block>
            {{ snippets[Mobile Header] }}
          </div>
          <div class=visible-sm-block visible-md-block visible-lg-block navbar-brand>
            {{ snippets[Navbar Left] }}
          </div>
        </div>
      </div>
    </div>
    <div class=container>
      <div class=page-heading>
        <ul class=breadcrumb>
          <li>
            <a href={{ request.url | base }} title=Home>Home</a>
          </li>
          <li class=active>{{ page.title | h}}</li>
        </ul>
        {% include 'Page Header' %}
     </div>
     <div class=row>
      <div class=col-md-12>
        {% include 'Page Copy' %}
        <div id=api></div>
      </div>
     </div>
    </div>
    <footer role=contentinfo>
      <div class=footer-top hidden-print>
        <div class=container>
          <div class=row>
            <div class=col-md-6 col-sm-12 col-xs-12 text-left>
               {{ snippets[About Footer] }}
            </div>
            <div class=col-md-6 col-sm-12 col-xs-12 text-right>
              <ul class=list-social-links>
                <li><a href=#><span class=sprite sprite-facebook_icon></span></a></li>
                <li><a href=#><span class=sprite sprite-twitter_icon></span></a></li>
                <li><a href=#><span class=sprite sprite-email_icon></span></a></li>
              </ul>
            </div>
          </div>
        </div>
      </div>
      <div class=footer-bottom hidden-print>
        <div class=container>
          <div class=row>
            <div class=col-md-4 col-sm-12 col-xs-12 text-left>
               {{ snippets[Footer] | liquid }}
            </div>
            <div class=col-md-8 col-sm-12 col-xs-12 text-left >
            </div>   
          </div>
        </div>
      </div>
    </footer>
  </body>
</html>
```
### <a name="step-2-create-a-page-template"></a>手順 2: ページテンプレートを作成する

次のページテンプレートを作成します。
- **[名前]** : [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C カスタムページ
- **種類**: Web テンプレート
- **Web テンプレート**: [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C カスタムページ
- **Web サイトのヘッダーとフッターを使用する**: このチェックボックスをオフにします

### <a name="step-3-create-a-webpage"></a>手順 3: web ページを作成する

次の web ページを作成します。
- **名前**: サインイン
- **親**ページ: ホーム
- **部分的な Url**: azure-ad-b2c-サインイン
- **ページテンプレート**: [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C カスタムページ
- **発行状態**: 発行済み

### <a name="step-4-create-site-settings"></a>手順 4: サイト設定を作成する

クロスオリジンリソース共有 (CORS) を構成して [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C がカスタムページを要求し、サインインまたはサインアップユーザーインターフェイスを挿入できるようにするには、サイト設定が必要です。 次のサイト設定を作成します。

| 名前                              | Value                             |
|-----------------------------------|-----------------------------------|
| HTTP/アクセス制御メソッド | GET、OPTIONS                      |
| HTTP/アクセス制御-オリジン  | `https://login.microsoftonline.com` |
| | |

その他の CORS 設定の完全な一覧については、「 [cors プロトコルのサポート](../add-web-resource.md#cors-protocol-support)」を参照してください。

### <a name="step-5-includeazureincludespn-azure-shortestmd-configuration"></a>手順 5: [!include[Azure](../../../includes/pn-azure-shortest.md)] 構成

1. [!include[Azure portal](../../../includes/pn-azure-portal.md)]にサインインします。
2. [ **[!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C テナント管理**] ブレードに移動します。
3. **サインアップまたはサインインポリシー** >  **[設定]** に移動します。 使用可能なポリシーの一覧が表示されます。
4. 編集するポリシーを選択します。
5. **[編集]** を選択します。
6. **[ポリシーの編集]**  > **ページの UI カスタマイズ** > 統合された**サインアップまたはサインインページの**選択
7. [**カスタムページ**の使用 **] を [はい]** に設定します。
8. **カスタムページ URI**を、この手順の手順3で作成した [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C カスタムページ web ページの URL に設定します。 たとえば、`https://mydomain.com/azure-ad-b2c-sign-in`のようにします。
9. **[OK]** を選択します。

## <a name="claims-mapping"></a>要求のマッピング

ユーザーが初めてサインインしたとき、またはその後、フェデレーション id プロバイダーは、ユーザーのサインインに関して、そのデータベースに基づいてクレームを提供します。 これらの要求は、id プロバイダーで構成できます。

### <a name="includeazureincludespn-azure-shortestmd-ad-b2c-email-claims"></a>AD B2C 電子メール要求の [!include[Azure](../../../includes/pn-azure-shortest.md)]

AD B2C [!include[Azure](../../../includes/pn-azure-shortest.md)] は、電子メール要求をコレクションとして送信します。 ポータルは、コレクションで指定された最初の電子メールを、連絡先のプライマリ電子メールアドレスとして受け入れます。

### <a name="claims-to-support-sign-up-scenarios"></a>サインアップシナリオをサポートするための要求

Common Data Service に存在しない新しい顧客がプロビジョニングされると、入力方向の要求を使用して、ポータルによって作成される新しい連絡先レコードをシードすることができます。 一般的な要求には、姓と名、電子メールアドレス、および電話番号を含めることができますが、構成することは可能です。 次のサイト設定が必要です。

**名前**: Authentication/openidconnect/[Federation-Name]/registrationclaimsmdump

**説明**: 登録時に作成された連絡先レコードの属性に要求値をマップするために使用される論理名/要求ペアの一覧。

**形式**: attribute1 = claim1、attribute2 = claim2、attribute3 = claim3

例: firstname =<http://schemas.xmlsoap.org/ws/2005/05/identity/claims/givenname,lastname=http://schemas.xmlsoap.org/ws/2005/05/identity/claims/surname,jobtitle=jobTitle>

> [!NOTE]
> 電子メールアドレスが連絡先のプライマリ電子メール (emailaddress1) にマップされていることを確認します。 連絡先レコードにセカンダリ電子メール (emailaddress2) または連絡用電子メール (emailaddress3) を追加して電子メールにマップした場合、id 情報は連絡先に追加されず、の登録に使用された電子メールアドレスを使用して新しいアドレス帳が作成されます。プライマリ電子メール (emailaddress1)。

### <a name="claims-to-support-sign-in-scenarios"></a>サインインシナリオをサポートするための要求

Common Data Service と id プロバイダーのデータは直接リンクされていないため、データが同期されない可能性があります。ポータルには、Common Data Service で更新するために、サインインイベントから受け入れたい要求の一覧が含まれている必要があります。 これらの要求は、サインインシナリオから送信される要求のサブセットまたはそれと同等のものにすることができます。 キーポータルの一部の属性を上書きしないようにする必要があるため、この設定は、サインイン要求のマッピングとは別に構成する必要があります。 次のサイト設定が必要です。

**名前**: Authentication/openidconnect/[Federation-Name]/loginclaimsmdump

**説明**: サインイン後に作成された連絡先レコードの属性に要求値をマップするために使用される論理名/要求ペアの一覧。

**形式**: attribute1 = claim1、attribute2 = claim2、attribute3 = claim3

例: firstname =<http://schemas.xmlsoap.org/ws/2005/05/identity/claims/givenname,lastname=http://schemas.xmlsoap.org/ws/2005/05/identity/claims/surname,jobtitle=jobTitle> 

要求名は、サインインポリシーのアプリケーション要求の属性の横に表示される [要求の種類] フィールドです。

### <a name="allow-auto-association-to-a-contact-record-based-on-email"></a>電子メールに基づく連絡先レコードへの自動関連付けを許可する 

メールが関連付けられた連絡先レコードを持っているお客様は、電子メール検証メカニズムを使用して、外部ユーザーが [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C でサインインする web サイトを起動します。 新しいサインインは、重複するレコードを作成するのではなく、既存の連絡先レコードに関連付ける必要があります。 この機能は、アクティブな id を持たない連絡先のみを正常にマップします。また、電子メールアドレスは一意である必要があります (複数の連絡先レコードに関連付けられていません)。 次のサイト設定が必要です。

**名前**: Authentication/[Protocol]/[Provider]/allowcontactmappingwithemail

**説明**: 連絡先が対応する電子メールにマップされるかどうかを指定します。 True に設定すると、この設定によって、一意の連絡先レコードが対応する電子メールアドレスに関連付けられ、ユーザーが正常にサインインした後に、外部 id プロバイダーが連絡先に自動的に割り当てられます。 既定では、false に設定されています。
