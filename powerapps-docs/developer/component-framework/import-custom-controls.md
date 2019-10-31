---
title: コンポーネントのインポート | Microsoft Docs
description: コード コンポーネントのインポート処理
keywords: null
ms.author: nabuthuk
manager: kvivek
ms.date: 06/20/2019
ms.service: powerapps
ms.suite: ''
ms.topic: article
author: Nkrb
---

# <a name="package-a-code-component"></a>コード コンポーネントをパッケージ化する

このトピックでは、コード コンポーネントを Common Data Service にインポートする方法について説明します。 PowerApps CLIを使用してコード コンポーネントを実装した後、次の手順としては、すべてのコード コンポーネント要素をソリューション ファイルにバンドルし、ソリューション ファイルを  Common Data Service にインポートします。これによりランタイムでコード コンポーネントを表示できるようになります。

ソリューション ファイルを作成してインポートする手順を示します:

1. 新しいフォルダーを作成し、`mkdir Solutions` コマンドを使用して **ソリューション** (任意の名前を選択できます) と名前を付けます。 コマンド `cd Solutions` を使用して、ディレクトリに移動します。

2. コマンド `pac solution init --publisher-name <enter your publisher name> --publisher-prefix <enter your publisher name>` を使用して新しいソリューション プロジェクトを作成します。 このソリューション プロジェクトは、Common Data Service へのインポートに使用するソリューション zip ファイルに、コード コンポーネントをバンドルするために使用されます。

   > [!NOTE]
   > `publisher-name` と `publisher-prefix` の値は環境に固有である必要があります。
 
3. 新しいソリューション プロジェクトを作成したら、この **ソリューション** フォルダーを作成したコンポーネントが配置された場所に参照する必要があります。 以下のコマンド を使用して参照を追加することができます。 この参照は、構築中にどのコード コンポーネントを追加すべきかについてをソリューション プロジェクトに通知し、単一のソリューション プロジェクト内で複数のコンポーネントへの参照を追加することができます。

   ```CLI   
    pac solution add-reference --path <path to your PowerApps component framework project>
   ```

3. ソリューション プロジェクトから zip ファイルを生成するには、ソリューション プロジェクトのディレクトリに移動して、`msbuild /t:build /restore` コマンドを使用してプロジェクトを構築する必要があります。 このコマンドは *MSBuild* を使用して、復元の一部として *NuGet* の依存関係をプルダウンすることで、ソリューション プロジェクトを構築します。 初めてソリューションプロジェクトを構築する際には `/restore` のみを使用します。 以降の各構築処理ごとに、`msbuild`コマンドを実行することができます。

    > [!NOTE]
    > - msbuild 15.9.*がパスに存在しない場合は、VS2017の開発者コマンドプロンプトを開いて `msbuild` コマンドを実行します。
    > - *デバッグ* 構成でソリューションをビルドして、アンマネージド ソリューション パッケージを生成します。 管理ソリューション パッケージは、*リリース* 構成でソリューションを構築することにより生成されます。 これらの設定は `cdsproj` ファイルで  `SolutionPackageType` プロパティを指定することでオーバーライドできます。
    > - 運用ビルドを発行するために`Release` にmsbuild構成を設定できます。 例: `msbuild /p:configuration=Release`。
    > - ソリューションで `msbuild` コマンドを実行している際に、*曖昧なプロジェクト名*というエラーが発生した場合。 その場合は、同じでないソリューション名とプロジェクト名をダブルクリックします。

4. 生成されたソリューション ファイルは、ビルド正常に行なわれたら `\bin\debug\` フォルダー内に配置されます。
5. [ソリューションをCommon Data Service](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/customize/import-update-upgrade-solution) に Web ポータルを使用して手動でインポートするか、[組織に対する認証](#authenticating-to-your-organization)と[デプロイ](#deploying-code-components)セクションを参照して、PowerApps CLI コマンドを使用してインポートします。

## <a name="authenticating-to-your-organization"></a>組織への認証

コード コンポーネントは、Common Data Service 組織へ認証をおこない、その後更新されたコンポーネントをプッシュすることで、PowerApps CLI から直接デプロイできます。 認証プロファイルを作成するには、次の手順に従って、Common Data Service に接続し、更新したコンポーネントをプッシュします。 
 
1. 次のコマンドを使用して、認証プロファイルを作成します。 
 
    ```CLI
    pac auth create --url <your Common Data Service org’s url> 
    ```
 
2. 前に認証プロファイルを作成した場合は、次のコマンドを使用してすべての既存プロファイルを表示できます。 

   ```CLI
    pac auth list 
   ```
 
3. 前に作成した認証プロファイル間を切り替えるには、次のコマンドを使用します: 
   
   ```CLI
    Pac auth select --index <index of the active profile>
    ``` 
 
4. 組織に関する基本的な情報を見つけるには、以下のコマンドを使用します。 接続は規定の認証プロファイルを使用しておこなわれます。 

    ```CLI
    pac org who 
    ```
 
5. 特定の認証プロファイルを削除するには、`pac auth delete --index < index of the profile >` コマンドを使用します。 
6. ローカル コンピューターからすべての認証プロファイルを削除するには、`pac auth clear` コマンドを使用します。 この操作は、ローカル コンピュータから `authprofile.json` ファイルとトークン キャッシュ ファイルを完全に削除するため不可逆です。 

## <a name="deploying-code-components"></a>コード コンポーネントのデプロイ 

正常に認証プロファイルを作成したら、すべて最新の変更で Common Data Service インスタンスにコード コンポーネントをプッシュし始めることができます。 `push` 機能は、コード コンポーネントのバージョン管理要件をバイパスし、コード コンポーネントをインポートするために自分でソリューション (cdsproj) を作成する必要がないことから、内部開発者のサイクル開発を高速化します。 `push` 機能を使用するには、次の項目の手順に従ってください。

1. 有効な認証のプロファイルを作成したことを確認します。
2. コード コンポーネントのプロジェクトが作成されたルート ディレクトリに移動します。
3. `pac pcf push --publisher-prefix <your publisher prefix>` コマンドを実行します。

   > [!NOTE]
   > `push` コマンドで使用する公開元は、コンポーネントを含むソリューションの公開元の接頭辞と一致させる必要があります。

## <a name="how-to-remove-components-from-a-solution"></a>ソリューションからコンポーネントを削除する方法

ソリューション ファイルからコード コンポーネントを削除する場合は:

1.  ソリューション プロジェクト ディレクトリの `cdsproj` ファイルを編集し、コンポーネントへの参照を削除します。 以下は、コンポーネント リファレンスの例です:

```XML
<ItemGroup>
    <ProjectReference Include="..\pcf_component\pcf_component.pcfproj">
      <Project>0481bd83-ffb0-4b70-b526-e0b3dd63e7ef</Project>
      <Name>pcf_component </Name>
      <Targets>Build</Targets>
      <ReferenceOutputAssembly>false</ReferenceOutputAssembly>
      <OutputItemType>Content</OutputItemType>
      <CopyToOutputDirectory>Always</CopyToOutputDirectory>
    </ProjectReference>
</ItemGroup>
```

2. コマンドを実行して再構築 (またはクリーンアップ) を実行します。
   
    ```CLI
    msbuild /t:rebuild
    ```

### <a name="see-also"></a>関連項目

[コンポーネントをモデル駆動型アプリに追加する](add-custom-controls-to-a-field-or-entity.md)<br/>
[アプリにコンポーネントを追加する](component-framework-for-canvas-apps.md#add-components-to-a-canvas-app)<br/>
[PowerApps Component Framework API の参照](reference/index.md)<br/>
[PowerApps Component Framework の概要](overview.md)
