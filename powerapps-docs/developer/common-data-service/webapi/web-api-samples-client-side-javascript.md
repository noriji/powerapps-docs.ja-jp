---
title: Web API データ操作のサンプル (クライアント側の JavaScript) (Common Data Service)| Microsoft Docs
description: このトピックには、クライアント側の JavaScript を使用して実装されたさまざまな Web API サンプルに関する説明が記載されています
ms.custom: ''
ms.date: 10/31/2018
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: a32e9a04-7bc1-41dd-b9af-bb4f21a613c6
caps.latest.revision: 15
author: brandonsimons
ms.author: jdaly
ms.reviewer: susikka
manager: annbe
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="web-api-data-operations-samples-client-side-javascript"></a>Web API データ操作のサンプル (クライアント側の JavaScript)


このトピックでは、クライアント側 JavaScript を使用する Web API サンプルに関する一般的な理解を深めます。 各サンプルは、Common Data Service Web API のさまざまな部分に注目しますが、それらはすべて、このトピックで説明されている類似したプロセスと構造をフォローします。  

<a name="bkmk_listOfSamples"></a>   
## <a name="web-api-samples-using-client-side-javascript"></a>クライアント側の JavaScript を使用する Web API のサンプル  
 次のサンプルは、ここで説明されるパターンを使用します:  
  
|サンプル|サンプル グループ|説明|  
|------------|------------------|-----------------|  
|[Web API 基本操作のサンプル (クライアント側の JavaScript)](samples/basic-operations-client-side-javascript.md)|[Web API Operations 操作のサンプル](web-api-basic-operations-sample.md)|Common Data Service エンティティ レコードの作成、取得、更新、削除、関連付け、および関連付け解除の各操作を実行する方法を説明します。|  
|[Web API クエリ データのサンプル (クライアント側の JavaScript)](samples/query-data-client-side-javascript.md)|[Web API クエリ データのサンプル](web-api-query-data-sample.md)|OData v4 クエリ構文と機能および Common Data Service クエリ機能を使用する方法を説明します。 定義済みクエリに関する作業のデモンストレーションを含み、FetchXML を使用してクエリを実行します。|  
|[Web API 条件付き演算のサンプル (クライアント側の JavaScript)](samples/conditional-operations-client-side-javascript.md)|[Web API 条件付き演算サンプル](web-api-conditional-operations-sample.md)|条件付きの操作の実行方法を示します。 これらの操作の動作は、指定した条件によって異なります。|  
|[Web API 機能およびアクションのサンプル (クライアント側 JavaScript)](samples/functions-actions-client-side-javascript.md)|[Web API 機能およびアクションのサンプル](web-api-functions-actions-sample.md)|ユーザー定義アクションを含む、バインドされた関数とバインドされていない関数およびアクションの使用方法を説明します。|  
  
<a name="bkmk_howToDownload"></a>   
## <a name="how-to-download-the-source-code-for-the-sample"></a>サンプルのソース コードのダウンロード方法。  
 各サンプルのソース・コードは [MSDN コード ギャラリー](https://code.msdn.microsoft.com/site/search?f%5b0%5d.type=user&f%5b0%5d.value=microsoft%20dynamics%20crm%20sdk%20documentation%20team) で入手可能です。 各サンプルをダウンロードするリンクが、そのサンプルの各ページに含まれています。  
  
 サンプルをダウンロードした後で、圧縮されたファイルを解凍します。 C# フォルダー内の各サンプルで Microsoft Visual Studio 2015 ソリューションを検索します。プロジェクトは空の ASP.NET Web アプリケーション プロジェクトだからです。 Common Data Service ソリューションは、インポートして実行できるようにダウンロード形式でも提供されます。  
  
> [!NOTE]
>  Visual Studio または ASP.NET のどちらも Common Data Service 用にクライアント サイドの JavaScript を開発するために必要ではありませんが、MSDN コード ギャラリー サイトではコンテナとして Visual Studio にファイルが含まれている必要があります。  ただし、Visual Studio は JavaScript の記述に関して向上したエクスペリエンスを提供します。  
  
<a name="bkmk_HowToImport"></a>   
## <a name="how-to-import-the-common-data-service-solution-that-contains-the-sample"></a>サンプルを含む Common Data Service のソリューションをインポートする方法。  
 それぞれのプロジェクトの中に、Common Data Service 管理ソリューションのファイルがあります。 このファイルの名前は、サンプルのプロジェクト名によって異なりますが、ファイル名は `_managed.zip` で終わります。  
  
 Common Data Service ソリューションを Common Data Service サーバーにインポートするには、次の手順を実行してください。  
  
1.  ダウンロードした ZIP ファイルの中身を解凍して、Common Data Service ソリューション ファイルを見つけます。このファイルも ZIP 形式のファイルです。 たとえば `Basic Operations` サンプルをダウンロードした場合は、`WebAPIBasicOperations\WebAPIBasicOperations_1_0_0_0_managed.zip` という名前の Common Data Service ソリューション ZIP ファイルを見つけます。  
  
2.  Common Data Service UI で、**設定 > ソリューション** に移動します。 このページには、Common Data Service サーバーのソリューションの一覧が表示されます。 このソリューションのインポートを完了した後、そのサンプルのソリューション名が一覧に表示されます (例: **Web API の基本操作**)。  
  
3.  **インポート** をクリックして、インポート ダイアログの指示に従って、このアクションを完了します。  
  
<a name="bkmk_howToRunSample"></a>   
## <a name="how-to-run-the-sample-to-see-the-script-in-action"></a>サンプルを実行して実行中のスクリプトを確認する方法  
 サンプル プログラムは、Common Data Service 内から Web リソースとして実行します。 インポートされたソリューションには、サンプル データを使用するか、または削除するかを選択できるオプションがある構成ページがあります。またサンプル プログラムを開始するためのボタンもあります。
  
 サンプルを実行するには、次の手順を実行します。  
  
1.  Common Data Service の **すべてのソリューション** ページで、ソリューションの名前をクリックします (例: **Web API の基本操作** リンク)。 これにより、新しいウィンドウのソリューションのプロパティが開きます。  
  
2.  左側のナビゲーション メニューで **構成** をクリックします。  
  
3.  **サンプルの開始** ボタンをクリックしてサンプル コードを実行します。  
  
<a name="bkmk_commonElements"></a>   
## <a name="common-elements-found-in-each-sample"></a>各サンプルの共通要素  
 次の一覧は、これらのサンプルでの共通要素に注目しています。  
  
-   `Sdk.startSample` 機能は、ユーザーが HTML ページの **サンプルの開始** ボタンをクリックすると呼ばれます。 `Sdk.startSample` 関数はグローバル変数を初期化し、チェーン内の最初の操作を開始します。  
  
-   プログラム出力およびエラー メッセージは、ブラウザーのデバッガー コンソールに送信されます。 これらの出力を表示するには、サンプルを実行する前に、コンソール ウィンドウを開きます。  Internet Explorer および Microsoft Edge のコンソール ウィンドウを含む開発者ツールにアクセスするには F12 キーを押します。  
  
-   これらのサンプルは、モダンなブラウザーでサポートされている、ブラウザーにネイティブな [ES6-Promise](https://msdn.microsoft.com/library/dn802826\(v=vs.94\).aspx) の実装を使用します。 Internet Explorer の場合、このサンプルは [ES6-Promise polyfill](https://github.com/stefanpenner/es6-promise) を使用します。Internet Explorer が Common Data Service によりサポートされている唯一のブラウザーであり、この機能のネイティブ サポートがないからです。  
  
     Promise は、必要ありません。 類似のやり取りはコールバック関数を使用して実行できます。  
  
-   `Sdk.request` 関数は、パラメーターとして渡される情報に基づく要求を処理する必要があります。 各サンプルの必要に応じて、渡されるパラメータは異なる場合があります。 詳細についてはそのサンプルのソース コードを参照してください。  
  
    ```javascript  
    /**  
     * @function request  
     * @description Generic helper function to handle basic XMLHttpRequest calls.  
     * @param {string} action - The request action. String is case-sensitive.  
     * @param {string} uri - An absolute or relative URI. Relative URI starts with a "/".  
     * @param {object} data - An object representing an entity. Required for create and update actions.  
     * @returns {Promise} - A Promise that returns either the request object or an error object.  
     */  
    Sdk.request = function (action, uri, data) {  
        if (!RegExp(action, "g").test("POST PATCH PUT GET DELETE")) { // Expected action verbs.  
            throw new Error("Sdk.request: action parameter must be one of the following: " +  
                "POST, PATCH, PUT, GET, or DELETE.");  
        }  
        if (!typeof uri === "string") {  
            throw new Error("Sdk.request: uri parameter must be a string.");  
        }  
        if ((RegExp(action, "g").test("POST PATCH PUT")) && (data === null || data === undefined)) {  
            throw new Error("Sdk.request: data parameter must not be null for operations that create or modify data.");  
        }  
  
        // Construct a fully qualified URI if a relative URI is passed in.  
        if (uri.charAt(0) === "/") {  
            uri = clientUrl + webAPIPath + uri;  
        }  
  
        return new Promise(function (resolve, reject) {  
            var request = new XMLHttpRequest();  
            request.open(action, encodeURI(uri), true);  
            request.setRequestHeader("OData-MaxVersion", "4.0");  
            request.setRequestHeader("OData-Version", "4.0");  
            request.setRequestHeader("Accept", "application/json");  
            request.setRequestHeader("Content-Type", "application/json; charset=utf-8");  
            request.onreadystatechange = function () {  
                if (this.readyState === 4) {  
                    request.onreadystatechange = null;  
                    switch (this.status) {  
                        case 200: // Success with content returned in response body.  
                        case 204: // Success with no content returned in response body.  
                            resolve(this);  
                            break;  
                        default: // All other statuses are unexpected so are treated like errors.  
                            var error;  
                            try {  
                                error = JSON.parse(request.response).error;  
                            } catch (e) {  
                                error = new Error("Unexpected Error");  
                            }  
                            reject(error);  
                            break;  
                    }  
  
                }  
            };  
            request.send(JSON.stringify(data));  
        });  
    };  
    ```  
  
     `Sdk.request` 関数は Promise を返します。 Promise によってラップされた要求が完了した場合、Promise は解決されるか、または拒否されます。 解決される場合、次の `then` メソッドの関数が呼び出されます。 拒否される場合、次の `catch` メソッドの関数が呼び出されます。 `then` メソッド内の関数自体が Promise を返す場合は、連続する `then` メソッドの一連の操作が続行します。 Promise を返すことにより、これらのサンプル操作を共に、多くの開発者に好まれる方法で、従来のコールバック関数にチェインします。 Promise に関する詳細については、[JavaScript Promise](https://msdn.microsoft.com/library/dn802826\(v=vs.94\).aspx)を参照してください。  
  
### <a name="see-also"></a>関連項目

[Common Data Service Web API の使用](overview.md)<br />
[Web API のサンプル](web-api-samples.md)<br />
[Web API のサンプル (C#)](web-api-samples-csharp.md)   
 
