---
title: Web ページ (HTML) の Web リソース (モデル駆動型アプリ) | MicrosoftDocs
description: このトピックでは、HTML Webリソースおよび機能と制限を実行する方法を扱います
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: KumarVivek
ms.author: kvivek
manager: shilpas
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="webpage-html-web-resources"></a>Webpage (HTML) の Web リソース

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/webpage-html-web-resources -->

Web ページ (HTML) の Web リソースを使用して、クライアント拡張のためのユーザー インターフェイス要素を作成します。

<a name="BKMK_Capabilities"></a>

## <a name="capabilities-of-html-web-resources"></a>HTML web リソースの機能

HTML Web リソースはユーザーのブラウザーにストリームされるので、ユーザーのブラウザーで表示される任意のコンテンツを含めることができます。  

<a name="BKMK_Limitations"></a>

## <a name="limitations-of-html-web-resources"></a>HTML web リソースの制限  

- サーバーで実行する必要のあるコードを HTML Web リソースに含めることはできません。 ASP.NET のページを HTML Web リソースとしてアップロードすることはできません。

- HTML Web リソースでは、限られた数のクエリ文字列パラメーターのみ受け取ることができます。 [HTML Web リソースへのパラメーターの引き渡し](webpage-html-web-resources.md#BKMK_PassingParametersToWebResources)  

<a name="BKMK_UsingTextEditor"></a>

## <a name="use-the-text-editor-for-html-web-resources"></a>HTML Web リソースでテキスト エディターを使用する

 Web リソース フォームに付属のテキスト エディターは、非常に単純な HTML の編集に使用します。 高度な HTML ドキュメントの場合は、外部エディターでコードを編集し、**参照**ボタンを使用してファイルのコンテンツをアップロードする必要があります。

 たとえば、スクリプトを使用してページのコンテンツを表示する複雑な HTML ページの先頭部分は次のようになります。

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html>
<head>
 <title></title>
 <script src="Script/Script.js" type="text/javascript"></script>
 <link href="CSS/Styles.css" rel="stylesheet" type="text/css" />
</head>
<body onload="SDK.ImportWebResources.showData()">
 <div id="results" />
</body>
</html>
```

 テキスト エディターでドキュメントを開いて保存した後、この HTML は次のように変更されます。  

```html
<HTML><HEAD><TITLE></TITLE>
<META charset=utf-8></HEAD>
<BODY contentEditable=true onload=SDK.ImportWebResources.showData()>
<SCRIPT type=text/javascript src="Script/Script.js"></SCRIPT>
 <LINK rel=stylesheet type=text/css href="CSS/Styles.css">
<DIV id=results></DIV></BODY></HTML>
```

<a name="BKMK_PreventEditing"></a>

## <a name="prevent-editing-of-web-resources-for-managed-solutions"></a>管理ソリューションの Web リソースの編集の禁止

テキスト エディターで変更される Web リソースには HTML 用の機能があるため、管理プロパティを使用して、複雑な HTML Web リソースをマネージド ソリューションに対してカスタマイズ可能なリソースとして設定することをお勧めします。 ソリューションのウィンドウに Web リソースを表示する場合は、**管理プロパティ**ダイアログ ボックスを使用して**カスタマイズ可能**プロパティを `false` に設定します。  

<a name="BKMK_ReferencingOtherWebResources"></a>

## <a name="reference-other-web-resources-from-an-html-web-resource"></a>HTML Web リソースからの他の Web リソースの参照

 いずれかの Web リソース ファイルの種類を使用する一連の関連ファイルをモデル駆動型アプリ外で作成できます。 常に相対パスを使用し、Web サイトのフォルダー構造を反映する一貫性のある命名規則を使用して各 Web リソースをインポートすると、Web リソースとしてインポートされた関連する CSS、JScript、イメージ、および Silverlight のファイルへのリンクが HTML Web リソースで維持されます。  

 たとえば、次の [フォルダー]/ファイル構造を使用する Web アプリケーション プロジェクトを作成するとします。  

-   page.htm

-   [スタイル]

    -   style.css
  
-   [Scripts] 
  
    -   script.js
  
 これらのファイルを Web リソースとしてインポートする場合、ソリューション発行者のカスタマイズの接頭辞は "new" で、次の方法で名前を付けることができます。  
  
-   `new_/page.htm`  
  
-   `new_/Styles/style.css`  
  
-   `new_/Scripts/script.js`  
  
 このパターンに従うと、`new_/page.htm` HTML Web リソースでは、以下の例に示すように、相対パスを使用する最も一般的な方法で他のファイルを参照できます。  

```html
<script src="Scripts/script.js" type="text/javascript"></script>
<link href="Styles/style.css" rel="stylesheet" type="text/css" />
```

 ソリューションのすべての Web リソースでは、ソリューション発行者のカスタマイズの接頭辞は仮想ルート フォルダーになります。 カスタマイズの接頭辞を変更する場合、HTML Web リソース内の相対パスは変更されません。  
  
> [!NOTE]
>  - フォームに追加された HTML Web リソースは、フォームに読み込まれた JavaScript ライブラリによって定義されたグローバル オブジェクトを使用できません。 HTML Web リソースは、`parent.Xrm.Page` または `parent.Xrm.Utility` を使用することによって、フォーム内の `Xrm.Page` または `Xrm.Utility` オブジェクトとやりとりできますが、フォーム スクリプトによって定義されたグローバル オブジェクトはその親を使用してアクセスできません。 HTML Web リソースは、フォームに読み込まれたスクリプトに左右されないようにするために、HTML Web リソース内で必要とするライブラリを読み込む必要があります。  
> - web リソース間のコードに含まれる参照は、ソリューションの依存関係として追跡されません。  

 また、Web リソースはオフライン アクセス対応 Dynamics 365 for Microsoft Office Outlook のユーザー用としてもダウンロードされるので、ユーザーはオフライン作業中に Web リソースのコンテンツにアクセスできます。  

<a name="BKMK_PassingParametersToWebResources"></a>

## <a name="pass-parameters-to-html-web-resources"></a>HTML Web リソースへのパラメーターの引き渡し

 HTML Web リソースでは、次の表に示すパラメーターのみ受け取ることができます。

|パラメーター|Name|内容|
|---------------|----------|-----------------|
|typename|エンティティ名|エンティティの名前。|
|種類|エンティティの種類コード|特定の組織内のエンティティを一意に識別する整数です。|
|ID|オブジェクトの GUID|レコードを表す GUID です。|
|orgname|組織名|組織の一意の名前です。|
|userlcid|ユーザー言語コード|現在のユーザーが使用している言語コードの識別子です。|
|orglcid|組織言語コード|組織の基本言語を表す言語コードの識別子です。|
|data|任意のデータ パラメーター|渡すことのできる任意の値です。|
|formid|フォーム ID|フォーム ID を表す GUID です。|
|entrypoint|エントリ ポイント|文字列値。 このパラメーターは、エンティティのユーザー定義のヘルプ コンテンツとして開かれる Web リソースにオプション値として渡されます。 有効にした場合、ユーザー定義のヘルプ URL は、「form」または「hierarchychart」のいずれかの値を含みます。|
|pagemode||内部のみで使用|
|セキュリティ||社外秘。|
|tabSet||社外秘。|

 複数の値がデータ パラメーターで渡された場合、自動的にエンコードされます。 ロジックも、HTML Web リソースのスクリプトを使用して複数のパラメーターをデコードするために含める必要があります。 「[サンプル: データ パラメーターを使用した Web リソースへの複数の値の引き渡し](sample-pass-multiple-values-web-resource-through-data-parameter.md)」トピックでは、複数のパラメーター値の引き渡しに対処する 1 つの方法を示しています。  

### <a name="see-also"></a>関連項目
 [Web リソース](web-resources.md)   
 [アクセス可能な Web リソースの作成](create-accessible-web-resources.md)   
 [スタイルシート (CSS) ウェブ リソースを使用する](css-web-resources.md)   
 [スクリプト (JScript) Web リソースの使用](script-jscript-web-resources.md)   
 [データ (XML) Web リソースの使用](data-xml-web-resources.md)   
 [画像 (JPG、PNG、GIF、ICO) Web リソースの使用](image-web-resources.md)   
 [スタイル シート (XSL) Web リソースの使用](stylesheet-xsl-web-resources.md)
