---
title: 'チュートリアル: adal.js で SimpleSPA アプリケーションを登録および構成する (Common Data Service)| Microsoft Docs'
description: このチュートリアルでは、adal.js および Cross-origin Resource Sharing (CORS) を使用して Common Data Service のデータをアクセスするために、最も単純化された Single Page Application (SPA) の登録および構成プロセスについて説明されます。
keywords: ''
ms.date: 08/26/2019
ms.service: powerapps
ms.custom:
  - ''
ms.topic: article
ms.assetid: a327d2ff-e252-61cf-1190-6a974130ef19
author: paulliew
ms.author: nabuthuk
manager: ryjones
ms.reviewer: null
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---

# <a name="walkthrough-registering-and-configuring-a-spa-application-with-adaljs"></a>チュートリアル: adal.js で SPA アプリケーションを登録および構成する

このチュートリアルでは、adal.js および Cross-origin Resource Sharing (CORS) を使用して Common Data Service のデータをアクセスするために、最も単純化された Single Page Application (SPA) の登録および構成プロセスについて説明されます。 詳細: [OAuth を使用するクロス オリジン リソース共有を使用して単一ページのアプリケーションを Common Data Service に接続する](oauth-cross-origin-resource-sharing-connect-single-page-application.md)
  
## <a name="prerequisites"></a>前提条件  
  
- PowerApps Common Data Service  
  
- Office 365 には、管理者ロールを持つ Common Data Service システム ユーザー アカウントが必要です。  
  
- アプリケーションの登録のための Azure サブスクリプション。 試用アカウントも有効です。  
  
- Visual Studio 2017  
  
<a name="bkmk_goal"></a>

## <a name="goal-of-this-walkthrough"></a>このチュートリアルの目標

このチュートリアルを完了すると、Visual Studio を使用して simple SPA アプリケーションを実行できるようになり、ユーザーが Common Data Service からのデータを認証して取得できる機能が提供されます。 このアプリケーションは、サンプルの HTML ページで構成されています。  

アプリケーションをデバッグする場合、最初に**ログイン**ボタンのみが表示されます。  

**ログイン**をクリックすると、サインイン ページにリダイレクトされ、資格情報を入力します。  

資格情報を入力した後は、HTML ページに戻り、そこでは**ログイン**ボタンが非表示となり、**ログアウト**ボタンと**取引先企業の取得**ボタンが表示されるようになります。 また、ユーザー アカウントからの情報を使用した挨拶も表示されるようになります。  

**取引先企業の取得**ボタンをクリックし、Common Data Service 組織から 10 件の取引先企業レコードの一覧を取得します。 次のスクリーンショットに示すとおり、**取引先企業の取得**ボタンが無効になります:  
  
![SimpleSPA ページ](media/simple-spa.png "SimpleSPA ページ")  

> [!NOTE]
> 認証をサポートする操作がなされるため、Common Data Service からのデータの最初の読み込みが遅くなる場合がありますが、後続の操作はさらに速くなります。  

最後に **ログアウト** ボタンをクリックしてログアウトします。  

> [!NOTE]
> この SPA アプリケーションは、堅牢な SPA アプリケーションを開発するパターンを表記することを目的としたものではありません。 アプリケーションの登録および構成におけるプロセスにフォーカスを設定することが簡素化されています。  

<a name="bkmk_createwebapp"></a>

## <a name="create-a-web-application-project"></a>Web アプリケーション プロジェクトの作成  
  
1. Visual Studio 2017 を使用して新しい **ASP.NET Web アプリケーション**プロジェクトを作成し、**空** テンプレートを使用します。 プロジェクトに任意の名前を付けることがでます。  
  
    Visual Studio の以前のバージョンもほぼ使用できますが、この手順では Visual Studio 2017 の使用について説明します。  
  
2. `SimpleSPA.html` という名前の新しい HTML ページをプロジェクトに追加し、次のコードを貼り付けます:  
  
    ```html  
    <!DOCTYPE html>  
    <html>  
    <head>  
     <title>Simple SPA</title>  
     <meta charset="utf-8" />  
     <script src="https://secure.aadcdn.microsoftonline-p.com/lib/1.0.17/js/adal.min.js"></script>  
     <script type="text/javascript">  
      "use strict";  
  
      //Set these variables to match your environment  
      var organizationURI = "https://[organization name].crm.dynamics.com"; //The URL of your Common Data Service organization  
      var tenant = "[xxx.onmicrosoft.com]"; //The name of the Azure AD organization you use  
      var clientId = "[client id]"; //The ClientId you got when you registered the application  
      var pageUrl = "http://localhost:[PORT #]/SimpleSPA.html"; //The URL of this page in your development environment when debugging.  
  
      var user, authContext, message, errorMessage, loginButton, logoutButton, getAccountsButton, accountsTable, accountsTableBody;  
  
      //Configuration data for AuthenticationContext  
      var endpoints = {  
       orgUri: organizationURI  
      };  
  
      window.config = {  
       tenant: tenant,  
       clientId: clientId,  
       postLogoutRedirectUri: pageUrl,  
       endpoints: endpoints,  
       cacheLocation: 'localStorage', 
      };  
  
      document.onreadystatechange = function () {  
       if (document.readyState == "complete") {  
  
        //Set DOM elements referenced by scripts  
        message = document.getElementById("message");  
        errorMessage = document.getElementById("errorMessage");  
        loginButton = document.getElementById("login");  
        logoutButton = document.getElementById("logout");  
        getAccountsButton = document.getElementById("getAccounts");  
        accountsTable = document.getElementById("accountsTable");  
        accountsTableBody = document.getElementById("accountsTableBody");  
  
        //Event handlers on DOM elements  
        loginButton.addEventListener("click", login);  
        logoutButton.addEventListener("click", logout);  
        getAccountsButton.addEventListener("click", getAccounts);  
  
        //call authentication function  
        authenticate();  
  
        if (user) {  
         loginButton.style.display = "none";  
         logoutButton.style.display = "block";  
         getAccountsButton.style.display = "block";  
  
         var helloMessage = document.createElement("p");  
         helloMessage.textContent = "Hello " + user.profile.name;  
         message.appendChild(helloMessage)  
  
        }  
        else {  
         loginButton.style.display = "block";  
         logoutButton.style.display = "none";  
         getAccountsButton.style.display = "none";  
        }  
  
       }  
      }  
  
      // Function that manages authentication  
      function authenticate() {  
       //OAuth context  
       authContext = new AuthenticationContext(config);  
  
       // Check For & Handle Redirect From AAD After Login  
       var isCallback = authContext.isCallback(window.location.hash);  
       if (isCallback) {  
        authContext.handleWindowCallback();  
       }  
       var loginError = authContext.getLoginError();  
  
       if (isCallback && !loginError) {  
        window.location = authContext._getItem(authContext.CONSTANTS.STORAGE.LOGIN_REQUEST);  
       }  
       else {  
        errorMessage.textContent = loginError;  
       }  
       user = authContext.getCachedUser();  
  
      }  
  
      //function that logs in the user  
      function login() {  
       authContext.login();  
      }  
      //function that logs out the user  
      function logout() {  
       authContext.logOut();  
       accountsTable.style.display = "none";  
       accountsTableBody.innerHTML = "";  
      }  
  
    //function that initiates retrieval of accounts  
      function getAccounts() {  
  
       getAccountsButton.disabled = true;  
       var retrievingAccountsMessage = document.createElement("p");  
       retrievingAccountsMessage.textContent = "Retrieving 10 accounts from " + organizationURI + "/api/data/v9.1/accounts";  
       message.appendChild(retrievingAccountsMessage)  
  
       // Function to perform operation is passed as a parameter to the acquireToken method  
       authContext.acquireToken(organizationURI, retrieveAccounts)  
  
      }  
  
    //Function that actually retrieves the accounts  
      function retrieveAccounts(error, token) {  
       // Handle ADAL Errors.  
       if (error || !token) {  
        errorMessage.textContent = 'ADAL error occurred: ' + error;  
        return;  
       }  
  
       var req = new XMLHttpRequest()  
       req.open("GET", encodeURI(organizationURI + "/api/data/v9.1/accounts?$select=name,address1_city&$top=10"), true);  
       //Set Bearer token  
       req.setRequestHeader("Authorization", "Bearer " + token);  
       req.setRequestHeader("Accept", "application/json");  
       req.setRequestHeader("Content-Type", "application/json; charset=utf-8");  
       req.setRequestHeader("OData-MaxVersion", "4.0");  
       req.setRequestHeader("OData-Version", "4.0");  
       req.onreadystatechange = function () {  
        if (this.readyState == 4 /* complete */) {  
         req.onreadystatechange = null;  
         if (this.status == 200) {  
          var accounts = JSON.parse(this.response).value;  
          renderAccounts(accounts);  
         }  
         else {  
          var error = JSON.parse(this.response).error;  
          console.log(error.message);  
          errorMessage.textContent = error.message;  
         }  
        }  
       };  
       req.send();  
      }  
      //Function that writes account data to the accountsTable  
      function renderAccounts(accounts) {  
       accounts.forEach(function (account) {  
        var name = account.name;  
        var city = account.address1_city;  
        var nameCell = document.createElement("td");  
        nameCell.textContent = name;  
        var cityCell = document.createElement("td");  
        cityCell.textContent = city;  
        var row = document.createElement("tr");  
        row.appendChild(nameCell);  
        row.appendChild(cityCell);  
        accountsTableBody.appendChild(row);  
       });  
       accountsTable.style.display = "block";  
      }  
  
     </script>  
     <style>  
      body {  
       font-family: 'Segoe UI';  
      }  
  
      table {  
       border-collapse: collapse;  
      }  
  
      td, th {  
       border: 1px solid black;  
      }  
  
      #errorMessage {  
       color: red;  
      }  
  
      #message {  
       color: green;  
      }  
     </style>  
    </head>  
    <body>  
     <button id="login">Login</button>  
     <button id="logout" style="display:none;">Logout</button>  
     <button id="getAccounts" style="display:none;">Get Accounts</button>  
     <div id="errorMessage"></div>  
     <div id="message"></div>  
     <table id="accountsTable" style="display:none;">  
      <thead><tr><th>Name</th><th>City</th></tr></thead>  
      <tbody id="accountsTableBody"></tbody>  
     </table>  
    </body>  
    </html>  
  
    ```  
  
3. SimpleSPA.html ファイルで右クリックし、**開始ページに設定** を選択してこのページをプロジェクトの開始ページに設定します。  
  
4. プロジェクトのプロパティでは、**Web** を選択し、**サーバー**では、**Project URL** を記録します。 `http://localhost:62111/` のようになる必要があります。 生成されるポート番号を記録します。 次の手順でこれが必要になります。  
  
5. SimpleSPA.html ページ内では、次の構成変数を見つけ、それに応じて設定します。 チュートリアルの次の部分が完了した後に、`clientId` が設定できるようになります。  
  
    ```javascript  
    //Set these variables to match your environment  
    var organizationURI = "https://[organization name].crm.dynamics.com"; //The URL to connect to PowerApps Common Data Service  
    var tenant = "[xxx.onmicrosoft.com]"; //The name of the Azure AD organization you use  
    var clientId = "[client id]"; //The ClientId you got when you registered the application  
    var pageUrl = "http://localhost:[PORT #]/SimpleSPA.html"; //The URL of this page in your development environment when debugging.  
  
    ```  
  
## <a name="register-the-application"></a>アプリケーションの登録  
  
1. 管理者権限を持つアカウントを使用して [Azure portal](https://go.microsoft.com/fwlink/?linkid=2083908) にサインインします。 アプリの登録に使用するものと同じ Office 365 サブスクリプション (テナント) のアカウントを使用する必要があります。 左のナビゲーション ウィンドウで **管理** アイテムを展開し、**Azure AD** を選択することによって、Microsoft 365 管理センターから Azure ポータルにもアクセスできます。  
  
    > [!NOTE]
    > ユーザーが Azure テナント (アカウント) を持っていないか、または持っているが Office 365 Azure でのサブスクリプションCommon Data Serviceが Azure サブスクリプションで使用できない場合は、トピック[設定Azure Active Directoryの手順に従って開発者サイト](https://docs.microsoft.com/en-us/office/developer-program/office-365-developer-program)にアクセスし、2 つのアカウントを関連付けます。<br/><br/> アカウントがない場合は、クレジット カードを使用して、アカウントにサインアップすることができます。 ただし、このトピックの手順を実行して 1 つまたは複数のアプリケーションを登録する場合は、アカウントは無料なのでクレジット カードに請求はありません。 詳細: [Active Directory 価格設定詳細](http://azure.microsoft.com/pricing/details/active-directory/)。  
  
2. ページの左側の列で、**Azure Active Directory** をクリックします。 左側の列をスクロールして、**Azure Active Directory** アイコンおよびラベルを参照する必要があります。  
  
3. 次に開くパネルで **エンタープライズ アプリケーション** を選択します。

   ![エンタープライズ アプリケーションを選択](media/register-spa-app-registration.PNG)

4. **新しいアプリケーション** (ページの上部付近) を選択し、次に **独自のアプリを追加** から **開発中のアプリケーション** を選択します。  

   ![開発中のアプリケーションを選択](media/register-spa-app-you-developing.PNG)
  
5. 次に **OK、アプリ登録に移動して新しいアプリケーションを登録する** をクリックします。

   ![OK を選択し、アプリ登録に移動します。](media/register-spa-take-me-app-reg.PNG)

6. 次に **新しいアプリケーションを登録** (ページの上部付近) をクリックします。  

   ![新しいアプリケーションの登録を選択します。](media/register-spa-new-reg.PNG)
  
7. 次の情報を入力します:  
  
   - **名前**<br />アプリケーションの名前。

   - **サポートされているアカウントの種類**<br />**組織ディレクトリ内のアカウント** を選択します。

   - **リダイレクト URL**<br />これは、ユーザーがサインインした後にリダイレクトされる URL です。 ドロップダウン リストで **Web** を選択します。 Visual Studio でデバッグするため、その URL は [Web アプリケーション プロジェクトの作成](#bkmk_createwebapp)手順の 4 から取得したポート番号を表記する `http://localhost:####/SimpleSPA.html` となります。 そしてページの最後で **登録** をクリックします。

   ![詳細を入力](media/new-app-registration-page.png)

8. 新しく登録されたアプリケーションのタブで **アプリケーション (クライアント) ID** をコピーします。 この値に対して、SimpleSPA.html ページの `clientId` 変数を設定します。 **Web アプリケーション プロジェクトの作成**手順の 5 を参照してください。  

9. 次に **API アクセス許可** をクリックして **アクセス許可の追加** を選択します。

   ![必要なアクセス許可を選択](media/azure-api-permissions-page.png)

10. **Microsoft API** タブ配下の **Dynamics CRM** を選択します。

    ![API の選択から Dynamics CRM Online を選択します](media/app-registration-select-api-page.png)

11. **委任されたアクセス許可** タブを儒リックし、すべてのアクセス許可を選択して、ページの最後で **アクセス許可の追加** をクリックします。

    ![委任されたすべてのアクセス許可を選択](media/app-registration-delegate-permissions-page.png)

12. そして **完了** を選択します。 **Dynamics CRM** の行が追加されたことを確認します。

13. 次に **API アクセス許可** タブを閉じます。登録済みアプリ タブで **マニフェスト** を選択します。

14. `"oauth2AllowImplicitFlow": false,` という行を見つけ、そして `false` を `true` に変更し **保存** をクリックしてファイルを保存します。

    ![マニフェスト ファイルで oauth2AllowImplicitFlow を true に設定します。](media/register-spa-edit-manifest.PNG)

15. アプリケーションの実行を成功させるため、管理者の承認を付与する必要もあります。 そのためには、Azure 管理ポータルでテナント管理者としてログインし **Azure Active Directory** を選択します。 次に **エンタープライズ アプリケーション** をクリックして、表示されるアプリケーションの一覧からいま作成したアプリケーションを選択します。

    ![アプリケーションに管理者の承認を付与](media/simple-spa-admin-consent.PNG)

16. 次に先に示したように **API アクセス許可** を選択して `<your AAD Org name>` **に管理者の承認を付与** します。

    ![管理者の承認を付与ボタンをクリック](media/simple-spa-admin-consent-button.PNG)

17. このボタンクリックすると、ログイン ウィンドウが開いて要求されたアクセス許可をアプリケーションに付与するかどうか尋ねられます。 続行するには **同意する** をクリックします。

    ![同意をクリックして要求されたアクセス許可を付与](media/simple-spa-admin-consent-click-accept.PNG)

18. 完了したら、アプリケーションのデバッグに進みます。

> [!NOTE]
> 登録したアプリの **認証** タブで **ID トークン** オプションを有効にする必要があります。

## <a name="debugging-the-application"></a>アプリケーションのデバッグ  
  
1.  Microsoft Edge または Google Chrome を使用するようにブラウザーを設定します。  
  
    > [!NOTE]
    > Internet Explorer ではこの状況でのデバッグに対応していません。  
  
2.  [F5] キーを押して、デバッグを開始します。 [チュートリアルのゴール](walkthrough-registering-configuring-simplespa-application-adal-js.md#bkmk_goal) で、説明する動作を考慮する必要があります。  
  
予期している結果が得られない場合は、アプリケーションの登録時および `SimpleSPA.html` コードの構成時にセットしたときの値を再確認します。  
  
## <a name="see-also"></a>関連項目  
 [クライアント アプリケーション作成](connect-cds.md)<br />
 [チュートリアル: アプリをAzure Active Directoryに登録します](walkthrough-register-app-azure-active-directory.md) <br />
 [サーバー間 (S2S) の認証を使用して Web アプリケーションを作成する](build-web-applications-server-server-s2s-authentication.md)<br />
 [OAuth を使用するクロス オリジン リソース共有を使用して Common Data Service の単一ページのアプリケーションへ接続する](oauth-cross-origin-resource-sharing-connect-single-page-application.md)