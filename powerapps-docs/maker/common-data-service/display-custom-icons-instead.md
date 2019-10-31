---
title: PowerApps でリスト ビューに値とともにユーザー定義アイコンを表示 | MicrosoftDocs
description: ビューにユーザー定義アイコンを表示する方法を説明する
ms.custom: ''
ms.date: 02/14/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
author: Mattp123
ms.assetid: af866aed-2586-4b6f-bb1c-3519baae3645
caps.latest.revision: 25
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="display-custom-icons-alongside-values-in-list-views"></a>リスト ビューに値とともにユーザー定義アイコンを表示

<a name="GridIcons"></a>   

 PowerApps 環境の管理者とカスタマイザーは、ビューにグラフィックスを追加して、JavaScriptを使用した列の値に基づいてグラフィックを選択するために使用するロジックを設定できます。 この機能により、テキストまたは数値とともにアイコンを表示するリスト ビューをカスタマイズできます。 

> [!div class="mx-imgBorder"] 
> ![](media/icon-in-opportunity-view.png " [評価] 列にアイコンとテキスト値を表示する [すべての営業案件] ビュー")
  
> [!NOTE]
>  グリッド アイコンは、Web インターフェイスにのみ表示されます。 [!INCLUDE[pn_Outlook_short](../../includes/pn-outlook-short.md)] やモバイル アプリでは表示されません。  
  
### <a name="add-custom-graphics-and-javascript-as-web-resources"></a>Webリソースのようなユーザー定義のグラフィックおよびJavaScriptの追加  
  
1.  カスタマイズに必要な新しいグラフィック ファイルを作成します。 16 x 16 ピクセル アイコンのサイズをお勧めします (より大きな画像は縮小されます)。  
  
2.  どの値にどのアイコンを表示するかを確定する 1 つ以上の JavaScript 関数を書き込みます (通常、カスタマイズする列ごとに 1 つの関数が必要になります)。 各関数は、イメージ名およびツールヒントのテキストを含む配列を入力して返すように、行データ オブジェクトおよび言語 (LCID) コードを受け入れる必要があります。 関数の例については、このトピックの後半にある「[サンプル JavaScript 関数](#SampleJavascript)」を参照してください。  
  
3.  管理者としてお使いの環境にサインインして、ソリューション エクスプローラーを開きます。  
  
4.  **既定のソリューション**のポップアップ ウィンドウが開きます。 ここで、**コンポーネント** > **Web リソース**に順に移動します。  
  
5.  ユーザー定義のグラフィックを 1 つずつ Web リソースとしてアップロードします。 新しいWebリソースを作成するには、ツール バーの**新規**ボタンを選択します。 リソースを作成しやすいように別のポップアップ ウィンドウが開きます。 次の手順を実行します。  
  
    1.  新しいリソースにわかりやすい**名前**を付けます。 これは、JavaScriptコードから各グラフィックを参照するのに使用する名前です。  
  
    2.  グラフィック ファイルの保存に使用したグラフィック フォーマット (PNG、JPEG、または GIF) に**種類**を設定します。  
  
    3.  ファイル ブラウザー ウィンドウを開くには、**ファイルを選択**を選択します。 これを使用してグラフィック ファイルを検索したり、選択したりします。  
  
    4.  必要で応じて、**表示名**および**説明**を追加します。  
  
    5.  **保存**を選択してから、**Webリソース**ウィンドウを閉じます。  
  
6.  手元にある各グラフィック ファイルに対して前の手順を繰り返します。  
  
7.  ここで、最終 Web リソースとして JavaScript を追加します。 新しいWebリソースを作成するには、ツール バーで**新規**を選択します。 リソースを作成しやすいように別のポップアップ ウィンドウが開きます。 次の手順を実行します。  
  
    1.  新しいリソースにわかりやすい**名前**を付けます。  
  
    2.  **種類**を**スクリプト (JScript)** に設定します。  
  
    3.  **テキスト エディター** (**種類**設定の横) を選択してテキスト エディター ウィンドウを開きます。 ここにJavaScriptコードを貼り付け、**OK**を選択して保存します。  
  
    4.  必要で応じて、**表示名**および**説明**を追加します。  
  
    5.  **保存**を選択してから、**Webリソース**ウィンドウを閉じます。  
  
8.  **既定のソリューション**ポップアップ ウィンドウを開いた状態で、**コンポーネント** > **エンティティ**ツリーを展開し、カスタマイズするエンティティを見つけます。  
  
9. エンティティを展開し、**ビュー**アイコンを選択します。  
  
10. 選択したエンティティのビューの一覧が表示されます。 一覧からビューを選択します。 次に、ツールバーの**その他の操作**ドロップダウン リストを開き、**編集**を選択します。  
  
11. ポップアップ ウィンドウが、選択したビューを編集するためのコントロールとともに開きます。 これはビューに含まれる各列を示します。 ターゲット列を選択してから、**タスク**ボックスの**プロパティの変更**を選択します。 **列のプロパティの変更**ダイアログが開きます。ここで次の設定を行います:  
  
    - **Web リソース**: JavaScript 関数を保持するために作成した Web リソースの名前を指定します (一覧から選択するには**参照**を選択します)。  
  
    - **関数名**: 選択した列およびビューを変更するために入力した関数名を入力します。  
  
12. **OK** を選択して**列のプロパティの変更**ダイアログを閉じます。  
  
13. **保存して閉じる**を選択してビューを保存します。  
  
14. 必要に応じて、各エンティティ、ビュー、および列に対してこれらの手順を繰り返します。  
  
15. 準備ができたら、**すべてのカスタマイズの公開**を選択して変更を公開します。 その後、**既定のソリューション**ウィンドウを閉じます。  
  
<a name="SampleJavascript"></a>   

### <a name="sample-javascript-function"></a>サンプル JavaScript 関数  
 ユーザー定義アイコンとヒントを表示する JavaScript 関数には、次の 2 つの引数が表示されます: layoutxml で指定された行オブジェクト全体と呼び出し側ユーザーのロケール ID (LCID)。 LCID パラメーターでは、複数の言語でツールヒントのテキストを指定できます。 環境によってサポートされている言語の詳細については、 [言語を有効にする](/dynamics365/customer-engagement/admin/enable-languages) および [言語パックのインストールまたはアップグレード](/dynamics365/customer-engagement/on-premises/install-or-upgrade-language-packs)を参照してください。 コードで使用できるロケール ID (LCID) 値の一覧については、「[Microsoft によって割り当てられるロケール ID](https://go.microsoft.com/fwlink/?linkid=829588)」を参照してください。

  
 事前定義された限定のオプション セットを持つオプション セット型の属性にカスタムアイコンを追加する可能性が最も高いと想定される場合は、ラベルの代わりにオプションの整数値を使用して、ローカライズ問題を回避することを確認します。  
  
 次のサンプル コードは、3 つの値 (1: 高、2: 中、3: 低) のうち 1 つに基づいて、opportunityratingcode (評価) 属性でアイコンおよびヒントを表示します。 サンプル コードは、ローカライズしたツールヒントのテキストを表示する方法についても示します。 このサンプルを機能させるには、new_Hot、new_Warm、および new_Cold の名前で、16 x 16イメージの3つのイメージWebリソースを作成する必要があります。  

> [!IMPORTANT]
> このサンプルでは、Dynamics 365 Sales アプリとともに使用できる営業案件エンティティが必要になります。
  
```javascript
function displayIconTooltip(rowData, userLCID) {      
    var str = JSON.parse(rowData);  
    var coldata = str.opportunityratingcode_Value;  
    var imgName = "";  
    var tooltip = "";  
    switch (parseInt(coldata,10)) { 
        case 1:  
            imgName = "new_Hot";  
            switch (userLCID) {  
                case 1036:  
                    tooltip = "French: Opportunity is Hot";  
                    break;  
                default:  
                    tooltip = "Opportunity is Hot";  
                    break;  
            }  
            break;  
        case 2:  
            imgName = "new_Warm";  
            switch (userLCID) {  
                case 1036:  
                    tooltip = "French: Opportunity is Warm";  
                    break;  
                default:  
                    tooltip = "Opportunity is Warm";  
                    break;  
            }  
            break;  
        case 3:  
            imgName = "new_Cold";  
            switch (userLCID) {  
                case 1036:  
                    tooltip = "French: Opportunity is Cold";  
                    break;  
                default:  
                    tooltip = "Opportunity is Cold";  
                    break;  
            }  
            break;  
        default:  
            imgName = "";  
            tooltip = "";  
            break;  
    }  
    var resultarray = [imgName, tooltip];  
    return resultarray;  
}  
```  
  
 <!-- This results in displaying icons with tooltips in the **Rating** column that depend on the value in each row. The result could look like this:  
  
 ![Custom column graphics example](../customize/media/custom-column-graphics-example.png "Custom column graphics example")  -->
 
 ### <a name="see-also"></a>関連項目
[モデル駆動型アプリのビューについて](../model-driven-apps/create-edit-views.md)
