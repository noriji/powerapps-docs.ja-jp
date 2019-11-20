Package Deployer ツールは [NuGet パッケージ](https://go.microsoft.com/fwlink/?linkid=859205)として提供されています。 Package Deployerを使用するには、**nuget.exe.** を使用してファイルをローカル コンピューターにダウンロードし、展開する必要があります。<br/><br/>

**nuget.exe** を <https://www.nuget.org/downloads> からダウンロードし、コンピューター (**d:\\** など) に保存します。 その後、コマンド プロンプトで次のコマンドを実行し、パッケージの内容をコンピューター上のフォルダー (たとえば **PD**) に展開します。<br/>

`d:\nuget install Microsoft.CrmSdk.XrmTooling.PackageDeployment.Wpf -Version [VERSION] -O d:\PD`<br/><br/>
    
Package Deployer ツールを展開した後、`[ExtractedLocation]\tools` フォルダーに移動して **PackageDeployer.exe** ファイルを見つけます。 
