---
title: 'チュートリアル: モデル駆動型アプリで最初のクライアント スクリプトを記述する | MicrosoftDocs'
ms.date: 10/31/2018
ms.service: powerapps
ms.topic: conceptual
applies_to: Dynamics 365 (online)
ms.assetid: 73dfc13c-a18c-42fc-b511-a37896c2f893
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="walkthrough-write-your-first-client-script"></a>チュートリアル: 最初のクライアント スクリプトを記述する

最初のクライアント スクリプトを記述して物事を把握することができます。 では始めましょう。

## <a name="objective"></a>目標

このチュートリアルを完了すると、モデル駆動型アプリで JavaScript コードを使用することができます。これには、次のハイレベルなステップが関係します。

- ビジネス上の課題の解決するために JavaScript コードを記述する
- モデル駆動型アプリで Web リソースとして JavaScript コードをアップロードする
- モデル駆動型アプリの異なるクライアント側のイベントに Webリソース で Javascript 関数を関連付ける。

チュートリアルでは、重要な事実に注意を向け、必要に応じて実際のメソッドを参照します。

## <a name="step-1-write-your-custom-javascript-code"></a>ステップ 1: カスタム JavaScript コードを記述する

最初のステップは、クライアント スクリプトを使用して解決するビジネス上の課題を特定します。 特定した後、ビジネス上の課題に対処できるカスタム ビジネス ロジックを含む JavaScript コードを記述する必要があります。 

モデル駆動型アプリには、JavaScript エディタがありません。 そのため、[Notepad++](https://notepad-plus-plus.org/)、[Visual Studio Code](https://code.visualstudio.com/docs/languages/javascript)、[Microsoft Visual Studio](https://docs.microsoft.com/scripting/javascript/) など、JavaScript ファイルの編集機能をサポートする外部作成ツールを活用する必要があります。

このトピックのチュートリアルで使用する完全なコード サンプルを確認できます。

コードの詳細を確認しましょう。
 
### <a name="detailed-code-explanation"></a>コードの詳細な説明

- **名前空間の定義**: コードはカスタム スクリプトの名前空間を定義することから開始します。 ベスト プラクティスとして、他のライブラリの関数によって関数が上書きされるのを避けるために名前空間を使用した JavaScript ライブラリを必ず作成します。

    ```JavaScript
    var Sdk = window.Sdk || {};
    ``` 
    ここでは、このライブラリで定義されるすべての関数は `Sdk.[functionName]` として使用できます。

- **グローバル変数の定義**: 次のセクションは、スクリプトで使用するグローバル変数を定義します。 ユーザー名を取得するためにフォーム コンテキストを調べる必要がなくなりました。 コンテキスト情報は **Xrm.Utility.**[getGlobalContext](reference/xrm-utility/getGlobalContext.md) メソッドを使用してグローバルで利用できるようになりました。

    ```JavaScript
    // Define some global variables
    var myUniqueId = "_myUniqueId"; // Define an ID for the notification
    var currentUserName = Xrm.Utility.getGlobalContext().userSettings.userName; // get current user name
    var message = currentUserName + ": Your JavaScript code in action!";
    ```
- **OnLoad イベントで実行するコード**: このセクションには、アカウント フォームがロードすると実行されるコードが含まれます。 たとえば、新しい取引先企業レコードを作成する、または既存の取引先企業レコードを開くときです。

    コードは、`executionContext` オブジェクトを使用して `formContext` オブジェクトを取得します。 後にフォーム イベントにコードをアタッチするとき、[実行コンテキスト](clientapi-execution-context.md) をこの関数に渡すオプションを選択するようにします。 次に、[setFormNotification](reference/formContext-ui/setFormNotification.md) メソッドを使用してフォーム レベル通知を表示します。 次に、5 秒後に通知をクリアする [clearFormNotification](reference/formContext-ui/clearFormNotification.md) メソッドの実行を遅らせるために **setTimeOut** メソッドを使用します。

    ```JavaScript
    // Code to run in the form OnLoad event
    this.formOnLoad = function (executionContext) {
        var formContext = executionContext.getFormContext();

        // display the form level notification as an INFO
        formContext.ui.setFormNotification(message, "INFO", myUniqueId);
        
        // Wait for 5 seconds before clearing the notification
        window.setTimeout(function () { formContext.ui.clearFormNotification(myUniqueId); }, 5000);        
    }
    ```
- **OnChange イベントで実行するコード**: このセクションのコードは、取引先企業フォームの**取引先企業名**フィールドに関連付けられるため、取引先企業名の値を変更した場合に**のみ**実行されます。

    コードは、取引先企業名で「Contoso」について大文字小文字を区別しない検索を行い、存在すれば、取引先企業フォームの一部のフィールドで値を自動的に設定します。

    ```JavaScript
    // Code to run in the attribute OnChange event 
    this.attributeOnChange = function (executionContext) {
        var formContext = executionContext.getFormContext();

        // Automatically set some field values if the account name contains "Contoso"
        var accountName = formContext.getAttribute("name").getValue();
        if (accountName.toLowerCase().search("contoso") != -1) {
            formContext.getAttribute("websiteurl").setValue("http://www.contoso.com");
            formContext.getAttribute("telephone1").setValue("425-555-0100");
            formContext.getAttribute("description").setValue("Website URL, Phone and Description set using custom script.");
        }
    }
    ```

- **OnSaveイベントで実行するコード**: このセクションのコードは、[openAlertDialog](reference/xrm-navigation/openalertdialog.md) メソッドを使用して通知ダイアログ ボックスを表示します。 このダイアログ ボックスで表示されるメッセージには、**OK** ボタンがあります。ユーザーは **OK** をクリックして通知を閉じることができます。

    この関数では実行コンテキストを渡すわけではありません。**Xrm.Utility.** メソッドの実行に必要ではないからです。 

    ```JavaScript
    // Code to run in the form OnSave event 
    this.formOnSave = function () {
        // Display an alert dialog
        Xrm.Navigation.openAlertDialog({ text: "Record saved." });
    }
    ```

## <a name="step-2-add-your-javascript-code-in-a-script-web-resource"></a>ステップ 2: スクリプト Web リソースで JavaScript コードを追加する

コードの準備ができたので、モデル駆動型アプリのイベントに関連付けます。 モデル駆動型アプリの [スクリプト Web リソース](../script-jscript-web-resources.md) を使用して、モデル駆動型アプリのインスタンスにインスタンスをアップロードし、イベントと関連付けます。

1. ブラウザーでモデル駆動型アプリのインスタンスにアクセスし、**設定** > **カスタマイズ**に移動します。
2. カスタマイズ領域で、**システムのカスタマイズ**をクリックします。
3. ソリューション エクスプローラーの**コンポーネント**で、**Web リソース**を選択します。  
4. **新規**を選択して、Web リソースを作成します。
5. 新しい Web リソース ダイアログで、Web リソースの**名前**と**表示名**を指定します。 例: "mySampleScript.js" および "サンプル: チュートリアル" スクリプトです。 
6. **種類**ドロップダウン リストで、**スクリプト (JScript)** を選択します。 **ファイルの選択**を選択して JavaScript コードを含むファイルをアップロードするか、**テキスト エディター**を選択してエディターに JavaScript コードを貼り付けます。
    ![Web リソースの作成](../media/clientapi_walkThrough-img1.png)
1. JavaScript コードを含む Web リソースを作成するには**保存**を選択します。
2. Web リソースを公開するには、**公開**を選択します。

## <a name="step-3-associate-script-web-resource-to-a-form"></a>ステップ 3: スクリプト Web リソースをフォームに関連付ける

コードの関数をイベントに関連付けるために、JavaScript コードを含む Web リソースをモデル駆動型アプリのフォームに関連付けます。 このチュートリアルび JavaScript コードが取引先企業レコードを対象ｎしているため、Web リソースを取引先企業フォームに関連付けます。

1. ブラウザーでモデル駆動型アプリのインスタンスにアクセスし、**Sales** > **取引先企業**または**サービス** > **取引先企業**に移動します。
2. 取引先企業レコードを開き、**フォーム**を選択してフォーム エディターを開きます。

    ![フォーム エディターを開く](../media/clientapi_walkThrough-img2.png)
1. フォーム エディターで、**フォーム プロパティ**を開きます。
2. **フォーム プロパティ**ダイアログ ボックスの**イベント**タブで、**追加**をクリックして Webリソースを検索して追加します。

    ![追加​​](../media/clientapi_walkThrough-img3.png)
1. 次のダイアログ ボックスで、Web リソース名を検索し、選択してから**追加**をクリックして、取引先企業フォームの JavaScript ライブラリとして追加します。

    ![レコードの検索](../media/clientapi_walkThrough-img4.png)

これにより、**フォーム プロパティ**ダイアログの**イベント ハンドラー**セクションで、Web リソースが選択できるようになります。 JavaScript コードには、フォームの適切なイベントに関連付けられる 3 つの関数があります。

1. **イベント ハンドラー**セクションで、コントロールとして**フォーム**を選択し、**イベント**として **OnLoad** を選択し、**追加**をクリックして OnLoad イベントにイベント ハンドラーを追加します。

   ![フォーム OnLoad](../media/clientapi_walkThrough-img5.png)
1. **ハンドラー プロパティ**ダイアログ ボックスで次を行います。   

    - **ライブラリ**ドロップダウン リストから Web リソースの名前を選択し、**関数**フィールドで **Sdk.formOnLoad** を指定します。 関数名は JavaScript コードの [名前空間].[関数]です。
    - この関数にパラメーターとして実行コンテキストを渡すには、**実行コンテキストを最初のパラメーターとして渡す**を選択します。 コードの関数の定義を確認すると、関数の定義に **executionContext** オブジェクトを渡しており、このオプションを選択するとそれらが関連付けられます。
    
      ![フォーム OnLoad](../media/clientapi_walkThrough-img6.png)

1. **OK** をクリックして**フォームのプロパティ**ダイアログ ボックスを閉じます。
2. **イベント ハンドラー**セクションで、今度は**イベント**として **OnLoad** を選択し、**追加**をクリックして フォーム OnSave イベントにイベント ハンドラーを追加します。

    ![フォーム OnSave](../media/clientapi_walkThrough-img7.png)

1. **ハンドラー プロパティ**ダイアログ ボックスで、**ライブラリ**ドロップダウン リストから Web リソースの名前を選択し、**関数**フィールドで **Sdk.formOnSave** を指定します。 実行コンテキストは **Sdk.formOnSave** 関数コードでは必要とされないため、今回は関数に渡しません。

    ![フォーム OnSave](../media/clientapi_walkThrough-img8.png)

1. **OK** をクリックして**フォームのプロパティ**ダイアログ ボックスを閉じます。
2. **イベント ハンドラー**セクションで、コントロールとして**取引先企業名**を選択し、イベントとして **OnChange** を選択し、**追加**をクリックして OnChange イベントにイベント ハンドラーを追加します。

    ![フォーム OnSave](../media/clientapi_walkThrough-img9.png)

1. **ハンドラー プロパティ**ダイアログ ボックスで次を行います。   

    - **ライブラリ**ドロップダウン リストから Web リソースの名前を選択し、**関数**フィールドで **Sdk.attributeOnChange** を指定します。
    - この関数にパラメーターとして実行コンテキストを渡すには、**実行コンテキストを最初のパラメーターとして渡す**を選択します。 コードの関数の定義を確認すると、関数の定義に **executionContext** オブジェクトを渡しており、このオプションを選択するとそれらが関連付けられます。
    
      ![属性 OnChange](../media/clientapi_walkThrough-img10.png) 
1. **OK** をクリックして**フォームのプロパティ**ダイアログ ボックスを閉じます。
2. フォーム エディターに戻るには、**フォームのプロパティ**ダイアログ ボックスで **OK** をクリックします。
3. **保存**をクリックして、フォームの変更を保存します。
4. フォームの変更を公開するには、**公開**をクリックします。

これで完了です。 JavaScript コードで指定したカスタム ビジネス ロジックを使用するように取引先企業フォームを構成する手順が完了しました。

## <a name="test-your-javascript-code"></a>JavaScript コードのテスト

モデル駆動型アプリのインスタンスで変更が反映されるよう、ブラウザーを更新することが推奨されています。 このチュートリアルで構成したカスタム ビジネス ロジックをテストするには、次を行います。

1. モデル駆動型アプリのインスタンスにサインインします。
2. **取引先企業**に移動して、新しい取引先企業を開くか作成します。 この場合、取引先企業フォームを読み込むために既存の取引先企業を開きます。 自分のユーザー名が含まれる通知が表示され、5 秒後に自動で非表示になります。

      ![フォーム レベルの通知](../media/clientapi_walkThrough-img11.png)

1. 取引先企業名を編集して「Contoso」を名前に追加し、Tab キーを押して次のフィールドに移動します。 これにより OnChange イベントが発生し、コードで指定した値によって**電話**、**Web サイト**、および**説明**フィールドが更新されます。

      ![値の自動設定](../media/clientapi_walkThrough-img12.png)

1. 最後に**保存**をクリックすると OnSave イベントが発生し、コードで構成したメッセージと共に通知ダイアログが表示されます。 **OK** をクリックして通知を閉じます。

      ![通知ダイアログ](../media/clientapi_walkThrough-img13.png)

## <a name="complete-sample-code-used-in-the-walkthrough"></a>チュートリアルで使用した完全なコード サンプル

```JavaScript
// A namespace defined for the sample code
// As a best practice, you should always define 
// a unique namespace for your libraries
var Sdk = window.Sdk || {};
(function () {
    // Define some global variables
    var myUniqueId = "_myUniqueId"; // Define an ID for the notification
    var currentUserName = Xrm.Utility.getGlobalContext().userSettings.userName; // get current user name
    var message = currentUserName + ": Your JavaScript code in action!";

    // Code to run in the form OnLoad event
    this.formOnLoad = function (executionContext) {
        var formContext = executionContext.getFormContext();

        // display the form level notification as an INFO
        formContext.ui.setFormNotification(message, "INFO", myUniqueId);

        // Wait for 5 seconds before clearing the notification
        window.setTimeout(function () { formContext.ui.clearFormNotification(myUniqueId); }, 5000);
    }

    // Code to run in the attribute OnChange event 
    this.attributeOnChange = function (executionContext) {
        var formContext = executionContext.getFormContext();

        // Automatically set some field values if the account name contains "Contoso"
        var accountName = formContext.getAttribute("name").getValue();
        if (accountName.toLowerCase().search("contoso") != -1) {
            formContext.getAttribute("websiteurl").setValue("http://www.contoso.com");
            formContext.getAttribute("telephone1").setValue("425-555-0100");
            formContext.getAttribute("description").setValue("Website URL, Phone and Description set using custom script.");
        }
    }

    // Code to run in the form OnSave event 
    this.formOnSave = function () {
        // Display an alert dialog
        Xrm.Navigation.openAlertDialog({ text: "Record saved." });
    }
}).call(Sdk);
```