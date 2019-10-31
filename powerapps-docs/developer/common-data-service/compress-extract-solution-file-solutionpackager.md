---
title: SolutionPackager ツール (Common Data Service) | Microsoft Docs
description: SolutionPackager は、ソース制御システムによって容易に管理できるように、Common Data Service の圧縮されたソリューション ファイルを複数の XML ファイルに逆分解できるツールです。
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: shmcarth
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="solutionpackager-tool"></a>SolutionPackager ツール 

SolutionPackager は、 Common Data Service の圧縮されたソリューションファイルを複数のXMLファイルやその他のファイルに可逆的に分解し、これらのファイルをソースコントロールシステムで容易に管理できるようにするツールです。 以下のセクションでは、ツールの実行方法と、管理ソリューションとアンマネージド ソリューションでツールを使用する方法を示します。  
  
<a name="bkm_where"></a>   

## <a name="where-to-find-the-solutionpackager-tool"></a>SolutionPackager ツールの場所  

 SolutionPackager ツール が [Microsoft.CrmSdk.CoreTools](https://www.nuget.org/packages/Microsoft.CrmSdk.CoreTools) NuGet パッケージの一部として配布されます。 ダウンロード方法については、[NuGet からツールをダウンロード](download-tools-nuget.md)を参照してください。
  
<a name="arguments"></a>   

## <a name="solutionpackager-command-line-arguments"></a>SolutionPackager のコマンドライン引数  

 SolutionPackager は、次の表で特定されるパラメーターで起動できるコマンドライン ツールです。  
  
|引数|説明|  
|--------------|-----------------|  
|/アクション: {抽出&#124;パック}|必須。 実行されるアクション。 このアクションは、ソリューションの .zip ファイルをフォルダーへ展開するか、またはフォルダーを .zip ファイルへ圧縮するかのいずれかです。|  
|/zipfile: \<ファイルパス>|必須。 ソリューションの .zip ファイルのパスおよびファイル名。 展開時に、ファイルが存在している必要があり、読み取られます。 圧縮時に、ファイルが置き換えられます。|  
|/folder: \<フォルダー パス>|必須。 フォルダーへのパス。 展開時に、このフォルダが作成され、それにコンポーネント ファイルが実装されます。 圧縮時には、このフォルダーが既に存在していて、前に展開されたコンポーネント ファイルが格納されている必要があります。|  
|/packagetype: {アンマネージド&#124;マネージド&#124;両方}|省略可。 処理するパッケージの種類。 既定値は Unmanaged です。 パッケージの種類は .zip ファイルまたはコンポーネント ファイル内から読み取ることができるので、ほとんどの場合、この引数は省略されることがあります。 展開と Both が指定されているとき、管理ソリューションおよびアンマネージド ソリューションの .zip ファイルが存在している必要があり、処理されて単一のフォルダーへ格納されます。 圧縮と Both が指定されているときは、管理ソリューションおよびアンマネージド ソリューションの .zip ファイルが 1 つのフォルダーから生成されます。 詳細については、このトピックの後のところにある、管理ソリューションおよびアンマネージド ソリューションを使用した作業についてのセクションを参照してください。|  
|/allowWrite:{はい&#124;いいえ}|省略可。 既定値は Yes です。 この引数は、展開時のみ使用されます。  /allowWrite:No が指定されると、ツールはすべての操作を行いますが、ファイルを作成または削除することはできません。 展開の操作は、既存のファイルを上書きまたは削除することなく安全に評価できます。|  
|/allowDelete:{はい&#124;いいえ&#124;プロンプト}|省略可。 既定値は Prompt です。 この引数は、展開時のみ使用されます。 /allowDelete:Yes が指定されると、予定されていない /folder パラメータによって指定されるフォルダーに存在するすべてのファイルが自動的に削除されます。 /allowDelete:No が指定されると、削除は実行されません。 /allowDelete:Prompt が指定されると、ユーザーは、すべての削除操作を許可または拒否することをコンソールから要求されます。 /allowWrite:No が指定されているときは、/allowDelete:Yes が指定されていても、削除が起きないことに注意してください。|  
|/clobber|省略可。 この引数は、展開時のみ使用されます。 /clobber が指定されていると、読み取り専用属性が設定されているファイルは上書きまたは削除されます。 指定されていないときは、読み取り専用属性が設定されているファイルは、上書きまたは削除されません。|  
|/errorlevel: {オフ&#124;エラー&#124;警告&#124;情報&#124;詳細}|省略可。 既定値は Info です。 この引数は、出力するログ情報のレベルを指示します。|  
|/map: \<ファイルパス>|省略可。 ファイル マッピング ディレクティブを含む .xml ファイルのパスおよび名前。 展開時に使用されると、通常、/folder パラメータによって指定されるフォルダー内から通常読み込まれるファイルは、マッピング ファイルで指定された別の場所から読み取られます。 圧縮操作時に、ディレクティブに一致するファイルは作成されません。|  
|/nologo|省略可。 実行時にメッセージを表示しません。|  
|/log: \<ファイルパス>|省略可。 ログ ファイルへのパスおよび名前。 ファイルに既に存在する場合、新しいログ情報がファイルに追加されます。|  
|@ \<ファイルパス>|省略可。 ツールのコマンド ライン引数を格納しているファイルへのパスおよび名前。|  
|/sourceLoc:  \<string>|省略可。 このトピックではテンプレート リソース ファイルを生成し、これは抽出でのみ有効です。<br /><br /> 有効な値は、`auto` またはエクスポートする言語の LCID/ISO コードです。 この引数を使用すると、指定ロケールからの文字列リソースは、中立の .resx ファイルとして抽出されます。 スイッチの `auto` フォーム、もしくは単にロング フォームまたはショート フォームが指定されると、基本的なロケールまたはソリューションが使用されます。 コマンドのショート フォーム /src を使用できます。|  
|/localize|任意。 すべての文字列リソースを展開するか、.resx ファイルに統合します。 コマンドのショート フォーム /loc を使用できます。|  
  
<a name="use_command"></a>   

## <a name="use-the-map-command-argument"></a>/map コマンド引数の使用  

以下の説明で、SolutionPackager ツールへの /map 引数の使用を詳述します。  
  
自動化したビルド システムでビルドされる、.xap Silverlight ファイルおよびプラグイン アセンブリなどのファイルは、通常は、ソース コントロールにチェックインされません。 Web リソースは、SolutionPackager ツールと直接互換性のない場所のソース コントロールに既にある場合があります。 /map パラメーターを含めることにより、SolutionPackager ツールに、通常実行している Extract フォルダ内からではなく、別の場所から当該ファイルを読み取って圧縮するように指示することができます。 /map パラメーターは、マッピング ディレクティブを含む XML ファイルの名前とそのパスを指定する必要があります。このディレクティブは、SolutionPackager  に指示して、名前とパスでファイルを照合し、一致したファイルを見つけるための別の場所を示します。 次の情報はすべてのディレクティブに平等に適用されます。  
  
- 同一のファイルと一致するものを含む、複数のディレクティブが表示されることがあります。 ファイルの始めに表示されているディレクティブは、後に表示されているディレクティブよりも優先されます。  
  
- ファイルをディレクティブと照合する場合、少なくとも 1 つの別の場所にそのファイルが見つかる必要があります。 一致する代替が見つからない場合、SolutionPackager がエラーを発生します。  
  
- フォルダーとファイルのパスには絶対パスまたは相対パスがあります。 相対パスは、/folder パラメーターによって指定されるフォルダーから常に評価されます。  
  
- 環境変数は、%variable% 構文を使用して指定できます。  
  
- フォルダのワイルドカード "**" は、"すべてのサブフォルダー内" を意味するために使用できます。 これは、"c:\folderA\\\*\*" などのパスの最終の部分としてのみ使用できます。  
  
- ファイル名のワイルドカードは、“*.ext” または "\*.\*" の形式でのみ使用できます。 他のパターンはサポートされていません。  
  
  3 種類のディレクティブ マッピングは、その使用方法を示す例とともに、ここに記載されています。  
  
<a name="Folder_mapping"></a>   

### <a name="folder-mapping"></a>フォルダーのマッピング  

次に、フォルダのマッピングの詳細を示します。  
  
**XML 形式**

`<Folder map="folderA" to="folderB" />`  
  
**内容**

"folderA" に一致するファイル パスは、"folderB" に切り替わります。  
  
- それぞれの下にあるサブフォルダーの階層は正確に一致する必要があります。  
  
- フォルダーのワイルドカードはサポートされていません。  
  
- ファイル名が指定されていない場合があります。  
  
  **例**

  ```xml  
  <Folder map="folderA" to="folderB" />  
  <Folder map="folderA\folderB" to="..\..\folderC\" />  
  <Folder map="WebResources\subFolder" to="%base%\WebResources" />  
  ```  
  
<a name="file_mapping"></a>   

### <a name="file-to-file-mapping"></a>ファイルとファイルのマッピング  

次に、ファイル対ファイルのマッピングの詳細を示します。  
  
 **XML 形式**

`<FileToFile map="path\filename.ext" to="path\filename.ext" />`  
  
**説明**

`map` パラメーターに一致するファイルが、`to` パラメーターで指定される名前とパスから読み取られます。  
  
 `map` パラメーターの場合:  
  
- ファイル名を指定する必要があります。 パスは省略可能です。 パスが指定されない場合、すべてのフォルダーのファイルが照合される可能性があります。  
  
- ファイル名のワイルドカードはサポートされていません。  
  
- フォルダーのワイルドカードはサポートされます。  
  
  `to` パラメーターの場合:  
  
- ファイル名とパスを指定する必要があります。  
  
- ファイル名が、`map` パラメーター内の名前と異なる場合があります。  
  
- ファイル名のワイルドカードはサポートされていません。  
  
- フォルダーのワイルドカードはサポートされます。  
  
**例**

```xml  
  <FileToFile map="assembly.dll" to="c:\path\folder\assembly.dll" />  
  <FileToFile map="PluginAssemblies\**\this.dll" to="..\..\Plugins\**\that.dll" />  
  <FileToFile map="Webresrouces\ardvark.jpg" to="%SRCBASE%\CrmPackage\WebResources\JPG format\aardvark.jpg" />  
```  
  
<a name="file_path_mapping"></a>   

### <a name="file-to-path-mapping"></a>ファイルとパスのマッピング  

次に、ファイル対パスのマッピングの詳細を示します。  
  
**XML 形式**

`<FileToPath map="path\filename.ext" to="path" />`  
  
**説明**  
 
`map` パラメーターに一致するファイルが、`to` パラメーターで指定されるパスから読み取られます。  
  
`map` パラメーターの場合:  
  
- ファイル名を指定する必要があります。 パスは省略可能です。 パスが指定されない場合、すべてのフォルダーのファイルが照合される可能性があります。  
  
- ファイル名のワイルドカードがサポートされています。  
  
- フォルダーのワイルドカードはサポートされます。  
  
`to` パラメーターの場合:  
  
- パスを指定する必要があります。  
  
- フォルダーのワイルドカードはサポートされます。  
  
- ファイル名を指定する必要はありません。  
  
  **例**

```xml  
  <FileToPath map="assembly.dll" to="c:\path\folder" />  
  <FileToPath map="PluginAssemblies\**\this.dll" to="..\..\Plugins\bin\**" />  
  <FileToPath map="*.jpg" to="%SRCBASE%\CrmPackage\WebResources\JPG format\" />  
  <FileToPath map="*.*" to="..\..\%ARCH%\%TYPE%\drop" />  
```  
  
<a name="Example_mapping"></a>   

### <a name="example-mapping"></a>マッピング例  
次の XML コード サンプルは、CRMDevTookitSample という名前の 開発者ツール プロジェクトから、SolutionPackager ツールによる Web リソースと 2 つの既定の生成されたアセンブリの読み取りを可能にする完全なマッピング ファイルを示しています。  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Mapping>  
       <!-- Match specific named files to an alternate folder -->  
       <FileToFile map="CRMDevTookitSamplePlugins.dll" to="..\..\Plugins\bin\**\CRMDevTookitSample.plugins.dll" />  
       <FileToFile map="CRMDevTookitSampleWorkflow.dll" to="..\..\Workflow\bin\**\CRMDevTookitSample.Workflow.dll" />  
       <!-- Match any file in and under WebResources to an alternate set of sub-folders -->  
       <FileToPath map="WebResources\*.*" to="..\..\CrmPackage\WebResources\**" />  
       <FileToPath map="WebResources\**\*.*" to="..\..\CrmPackage\WebResources\**" />  
</Mapping>  
```  
  
<a name="managed"></a>   

## <a name="managed-and-unmanaged-solutions"></a>管理ソリューションとアンマネージド ソリューション  

 Common Data Service  の圧縮されたソリューション (.zip) ファイルは、ここに示す 2 種類のいずれかでエクスポートできます。  
  
 **マネージド ソリューション**  
 組織へのインポートの準備が整っている完全なソリューションです。 いったんインポートされると、コンポーネントをさらに任意にカスタマイズすることは可能ですが、コンポーネントを追加または削除することはできません。 これは、ソリューションの開発が完了したときにお勧めします。  
  
 **アンマネージド ソリューション**  
 追加、削除または変更の内容に制限のないオープン ソリューション。 これは、ソリューション開発時に推奨されます。  
  
 圧縮されるソリューション ファイルの形式は、管理またはアンマネージドの種類に基づいて異なります。 SolutionPackager は、いずれかの種類の圧縮されたソリューション ファイルを処理します。 ただし、ツールは一方の種類から他方の種類に変更できません。 ソリューション ファイルを別の種類へ、たとえば、アンマネージドから管理へ変換する唯一の方法は、アンマネージド ソリューション .zip ファイルを Common Data Service サーバーへインポートし、そのソリューションを管理ソリューションとしてエクスポートすることです。  
  
 SolutionPackager は、 /PackageType:Both パラメーターを通して、アンマネージド ソリューションと管理ソリューションの  .zipファイルを組み合わせたセットとして処理できます。 この操作を実行するには、次のように、.zip ファイルに名前を付けて、ソリューションを 2 回それぞれの種類でエクスポートする必要があります。  
  
|||  
|-|-|  
|アンマネージド .zipファイル: AnyName.zip|マネージド .zipファイル: AnyName_managed.zip|  
  
 ツールは、マネージド zip ファイルがアンマネージド ファイルと同じフォルダーにあることを前提としており、管理コンポーネントとアンマネージド コンポーネントにある差異を保持する 1 つのフォルダーに両方のファイルを展開します。  
  
 ソリューションがアンマネージドと管理の両方で展開された後、作成する種類を  /PackageType パラメーターを使用して指定することで、その単一のフォルダーから各種類を個別にまたは両方を圧縮することができます。 両方を指定すると、2 つの .zip ファイルが、上記の命名規則を使用して生成されます。 2 つから構成された管理およびアンマネージド フォルダーから圧縮されるときに /PackageType パラメーターが欠落している場合、既定は単一のアンマネージド  ファイルを作成することです。  
  
## <a name="troubleshooting"></a>トラブルシューティング  

Visual Studio 2012 を使用してソリューションパッケージャで作成されたリソースファイルを編集する場合、次のようなメッセージが再パック時に表示されることがあります。 `“Failed to determine version id of the resource file <filename>.resx the resource file must be exported from the solutionpackager.exe tool in order to be used as part of the pack process.”` 。これは、 Visual Studio がリソースファイルのメタデータタグをデータタグに置き換えるために発生します。  
  
#### <a name="workaround"></a>回避策  
  
1. 任意のテキスト エディタでリソース ファイルを開き、次タグを検索および更新します。  
  
   ```xml  
   <data name="Source LCID" xml:space="preserve">  
   <data name="Source file" xml:space="preserve">  
   <data name="Source package type" xml:space="preserve">  
   <data name="SolutionPackager Version" mimetype="application/x-microsoft.net.object.binary.base64">  
  
   ```  
  
2. ノード名を `<data>` から `<metadata>` に変更します。  
  
    たとえば、次の文字列です。  
  
   ```xml  
   <data name="Source LCID" xml:space="preserve">  
     <value>1033</value>  
   </data>  
  
   ```  
  
    以下に変更します。  
  
   ```xml  
   <metadata name="Source LCID" xml:space="preserve">  
     <value>1033</value>  
   </metadata>  
  
   ```  
  
   これにより、ソリューション パッケージャーがリソース ファイルを読み取りおよびインポートすることができます。 この問題は、Visual Studio リソース エディターを使用する場合にのみ観察されています。  
  
### <a name="see-also"></a>関連項目  
 [ソリューション ファイルでのソース コントロールの使用](use-source-control-solution-files.md)<br/>   
 [ソリューション コンポーネント ファイル リファレンス](solution-component-file-reference-solutionpackager.md)<br/>   
 [ソリューションの概要](introduction-solutions.md)
