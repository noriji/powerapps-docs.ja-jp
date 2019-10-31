---
title: Postman 環境の設定 (Common Data Service for Apps)| MicrosoftDocs
description: Common Data Service 環境に接続する Postman 環境を設定と構成する方法を説明します。
ms.custom: null
ms.date: 04/09/2019
ms.reviewer: null
ms.service: powerapps
ms.suite: null
ms.tgt_pltfrm: null
ms.topic: article
ms.assetid: 955BA444-A53D-4843-9429-833B1636E2B4
caps.latest.revision: 7
author: susikka
ms.author: susikka
manager: shujoshi
search.audienceType:
  - developer
search.app:
  - D365CE
---

# <a name="set-up-a-postman-environment"></a>Postman 環境の設定

Postman を使用すると、Common Data Service インスタンスに接続して、Web API 要求を構成および送信し、応答を表示できます。 認証管理は多くの人たちにとって課題となります。 このトピックでは Postman 環境を Common Data Service 環境で機能するように構成する方法について説明します。

ユーザーが接続するために使用する一連の変数を保存するために Postman 環境を使用できます。 これらの値には、次の構文を使用することで postman 内でアクセスできます: `{{name}}`。 Postman 変数の詳細については [Postman のドキュメント > 変数](https://www.getpostman.com/docs/v6/postman/environments_and_globals/variables) を参照してください。

## <a name="prerequisites"></a>前提条件

* 接続できる PowerApps Common Data Service 環境が必要です。 
* [Postman デスクトップ アプリケーション](https://www.getpostman.com/apps) をダウンロードおよびインストールします。

<a name="bkmk_connectcds"></a> 

## <a name="connect-with-your-common-data-service-environment"></a>Common Data Service 環境に接続

この環境では、すべての Common Data Service 環境で登録されるアプリケーションのクライアント ID を使用します。 
 
これらの説明で提供されている `clientid` および `callback` の値を使用できます。  ただし、独自のアプリケーションを構築するときは、独自の Azure Active Directory (Azure AD) アプリケーションを登録する必要があります。
 
独自の Azure AD アプリケーションを登録するには、[チュートリアル: Azure Active Directory への Common Data Service アプリの登録](../walkthrough-register-app-azure-active-directory.md)に記載される手順を参照してください。

Common Data Service インスタンスと接続するのに使用できる Postman 環境を作成するには、これらのステップを使用します:

1. Postman デスクトップ アプリケーションを起動します。
1. 右上隅の **環境オプション** の歯車アイコンをクリックします。 
1. 新しい環境を追加するには **環境の管理** ダイアログ ボックスで **追加** ボタンを選択します。
  
  ![追加ボタンをクリックして新しい Postman 環境を追加する](media/postman-manage-env.png "追加ボタンをクリックして新しい Postman 環境を追加する")<br>
  
1. 開くダイアログ ボックスに、環境の名前を入力します。 それから、編集領域へ次のキーと値のペアを追加します。<br>

    | 変数名 | Value |
    |----|---|
    |`url`|`https://<add your environment name, like ‘myorg.crm’>.dynamics.com`|
    |`clientid`|`51f81489-12ee-4a9e-aaae-a2591f45987d`|
    |`version`|`9.0`|
    |`webapiurl`|`{{url}}/api/data/v{{version}}/`|
    |`callback`|`https://callbackurl`|
    |`authurl`|`https://login.microsoftonline.com/common/oauth2/authorize?resource={{url}}`|

    ![新しい Postman 環境を作成してオンライン インスタンスと接続する](media/postman-add-online-env.png "新しい Postman 環境を作成してオンライン インスタンスと接続する")<br>
1. インスタンス URL のプレースホルダー値を Common Data Service インスタンスの URL と置換して、**追加**をクリックして環境を保存します。

1. **環境の管理** ダイアログ ボックスを閉じます。  

### <a name="generate-an-access-token-to-use-with-your-environment"></a>環境で使用するアクセス トークンの生成

**OAuth 2.0**を使用して接続するには、アクセス トークンが必要です。 新しいアクセス トークンを取得するには、次のステップを実行します:

1. 作成した新しい環境が選択されていることを確認します。
1. **認証**タブを選択します。
1. **種類**を**OAuth 2.0**に設定します。
1. 作成した環境を選択していることを確認します。
1. **新しいアクセス トークンの取得** を選択

    ![認証タブで、種類を OAuth 2.0 に設定する](media/postman-set-type.png)<br>
1. ダイアログ ボックスに以下の値を設定します。 **種類の許可** ドロップダウン メニューから `Implicit` を選択します。 **トークン名** を任意のものに設定して、そのほかのキーは既定値のままに設定できます。<br>

    ![新しいアクセス トークンの取得](media/postman-access-token.png "新しいアクセス トークンの取得")<br>

    > [!NOTE]
    > 異なるユーザーの資格情報を使用して複数の Common Data Service インスタンス用に Postman の環境を構成している場合、Postman によってキャッシュされた Cookie を削除することが必要な場合があります。 **送信** ボタンの下にある **Cookie** リンクを選択して、**Cookie の管理** ダイアログ ボックスから保存されたクッキーを削除します。<br>![Cookie の削除](media/postman-cookies.png "Cookie の削除")<br>
    > これらの Cookie の一部は非常に永続的です。 グループでそれらの一部を削除できるものもあれば、他は個別に削除する必要がある場合もあります。   Cookie が残っていないことを確認するには、これを 2 回する必要がある場合があります。

1. **トークンの要求** を選択します。 これを行うと、Azure Active Directory のログイン ページが表示されます。 ユーザー名とパスワードを入力します。
1. トークンが生成されたら、一番下にスクロールして **トークンの使用** を選択します。 これにより **アクセス トークンの管理** ダイアログ ボックスが閉じます。 
1. トークンを追加すると、必要に適用するトークンを選択できます。 **使用できるトークン** ドロップダウン リストで、作成したばかりのトークンを選択します。 認証ヘッダーが API Web 要求に追加されます。

接続を確認するステップについては、[接続のテスト](#test-your-connection) を参照してください。

## <a name="test-your-connection"></a>接続のテスト

Common Data Service インスタンスと接続するテストのための新しい Web API 要求を作成します。 <xref href="Microsoft.Dynamics.CRM.WhoAmI?text=WhoAmI function" />を使用するには、次の操作を実行します。
1. HTTP メソッドとして `GET` を選択し、編集スペースで `{{webapiurl}}WhoAmI` を追加します。
  ![WhoAmI 関数要求](media/postman-whoami-request.png "WhoAmI 関数要求")
2. この要求を送信するには **送信** を選択します。
3. 要求が成功した場合は <xref href="Microsoft.Dynamics.CRM.WhoAmI?text=WhoAmI Function" /> によって返される <xref href="Microsoft.Dynamics.CRM.WhoAmIResponse?text=WhoAmIResponse ComplexType" /> からのデータを確認します。

## <a name="see-also"></a>関連項目

[Postman を使用して操作を実行する](use-postman-perform-operations.md)<br>
[チュートリアル: Common Data Service アプリを Azure Active Directory に登録する](../walkthrough-register-app-azure-active-directory.md)
