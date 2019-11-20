Package Deployer ツールの PowerShell ファイルは、[NuGet パッケージ](https://go.microsoft.com/fwlink/?linkid=859211)として提供されています。 ファイルを使用するには、**nuget.exe** を使用してファイルをローカル コンピューターにダウンロードし、展開する必要があります。<br/><br/>

**nuget.exe** を <https://www.nuget.org/downloads> からダウンロードし、コンピューター (**d:\\** など) に保存します。 その後、コマンド プロンプトで次のコマンドを実行し、パッケージの内容をフォルダー (たとえば **PD-PowerShell**) に展開します。<br/>

`d:\nuget install Microsoft.CrmSdk.XrmTooling.PackageDeployment.PowerShell -Version [VERSION] -O d:\PD-PowerShell`<br/><br/>
    
Package Deployer ツールの PowerShell ファイルを展開した後、`[ExtractedLocation]\tools` フォルダーに移動して必要なファイルを見つけます。 
