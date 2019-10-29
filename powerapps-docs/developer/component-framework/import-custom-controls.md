---
title: コンポーネントのインポート |Microsoft Docs
description: このトピックでは、コードコンポーネントをインポートする方法について説明します。
keywords: ''
ms.author: nabuthuk
manager: kvivek
ms.date: 06/20/2019
ms.service: powerapps
ms.suite: ''
ms.topic: article
author: Nkrb
ms.openlocfilehash: 4bb581e06102ac351b3202d30fa8d418951fa291
ms.sourcegitcommit: 7c1e70e94d75140955518349e6f9130ce3fd094e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/29/2019
ms.locfileid: "73025678"
---
# <a name="package-a-code-component"></a>コードコンポーネントのパッケージ化

このトピックでは、コードコンポーネントを Common Data Service にインポートする方法について説明します。 PowerApps CLI を使用してコードコンポーネントを実装した後、次の手順は、すべてのコードコンポーネント要素をソリューションファイルにバンドルし、ソリューションファイルを Common Data Service にインポートして、実行時にコードコンポーネントを確認できるようにすることです。

ソリューションファイルを作成してインポートするには:

1. コマンド `mkdir Solutions`を使用して、サンプルコンポーネントフォルダー内に新しいフォルダーを作成し、**ソリューション**(または任意の名前) に名前を指定します。 コマンド `cd Solutions` を使用してディレクトリに移動します。

2. コマンド `pac solution init --publisher-name <enter your publisher name> --publisher-prefix <enter your publisher prefix>` を使用して、新しいソリューションプロジェクトを作成します。 ソリューションプロジェクトは、コードコンポーネントを Common Data Service へのインポートに使用されるソリューション zip ファイルにバンドルするために使用されます。

   > [!NOTE]
   > `publisher-name` と `publisher-prefix` の値は、環境によって一意である必要があります。
 
3. 新しいソリューションプロジェクトが作成されたら、**ソリューション**フォルダーを参照して、作成したサンプルコンポーネントが配置されている場所を確認します。 次に示すコマンドを使用して、参照を追加できます。 この参照は、ビルド中に追加する必要のあるコードコンポーネントについてソリューションプロジェクトに通知します。 1つのソリューションプロジェクトに複数のコンポーネントへの参照を追加できます。

   ```CLI   
    pac solution add-reference --path <path to your PowerApps component framework project>
   ```

3. ソリューションプロジェクトから zip ファイルを生成するには、ソリューションプロジェクトディレクトリにアクセスし、コマンド `msbuild /t:build /restore` を使用してプロジェクトをビルドします。 このコマンドは、 *MSBuild*を使用して、復元の一環として*NuGet*の依存関係を取得し、ソリューションプロジェクトをビルドします。 `/restore` は、ソリューションプロジェクトが初めてビルドされるときにのみ使用します。 その後のすべてのビルドに対して、コマンド `msbuild` を実行できます。


    > [!NOTE]
    > - Msbuild 15.9. * がパスにない場合は、VS 2017 の開発者コマンドプロンプトを開いて、`msbuild` コマンドを実行します。
    > - *デバッグ*構成でソリューションをビルドすると、アンマネージドソリューションパッケージが生成されます。 マネージドソリューションパッケージは、*リリース*構成でソリューションをビルドすることによって生成されます。 これらの設定は、`cdsproj` ファイルで `SolutionPackageType` プロパティを指定することによってオーバーライドできます。
    > - Msbuild 構成を `Release` に設定して、運用ビルドを発行できます。 例: `msbuild /p:configuration=Release`
    > - ソリューションで `msbuild` コマンドを実行するときに*プロジェクト名があいまい*であるというエラーが発生した場合は、ソリューション名とプロジェクト名が同じでないことを確認してください。

4. 生成されたソリューションファイルは、ビルドが成功した後、`\bin\debug\` フォルダー内に配置されます。
5. Web ポータルを使用して[Common Data Service にソリューション](https://docs.microsoft.com/powerapps/maker/common-data-service/import-update-export-solutions)を手動でインポートするか、PowerApps CLI コマンドを使用してインポートするには、「組織と[デプロイ](#deploying-code-components)の認証」セクション[を](#authenticating-to-your-organization)参照してください。

## <a name="authenticating-to-your-organization"></a>組織に対する認証

Common Data Service 組織に認証して、更新されたコンポーネントをプッシュすることで、PowerApps CLI から直接コードコンポーネントをデプロイできます。 認証プロファイルを作成し、Common Data Service に接続して、更新されたコンポーネントをプッシュするには、次の手順に従います。 
 
1. 次のコマンドを使用して、認証プロファイルを作成します。 
 
    ```CLI
    pac auth create --url <your Common Data Service org’s url> 
    ```
 
2. 以前に認証プロファイルを作成した場合は、次のコマンドを使用して、既存のすべてのプロファイルを表示できます。 

   ```CLI
    pac auth list 
   ```
 
3. 以前に作成した認証プロファイルを切り替えるには、次のコマンドを使用します。 
   
   ```CLI
    Pac auth select --index <index of the active profile>
    ``` 

4. 組織に関する基本的な情報を取得するには、次のコマンドを使用します。 接続は、既定の認証プロファイルを使用して作成されます。 

    ```CLI
    pac org who 
    ```
 
5. 特定の認証プロファイルを削除するには、コマンド `pac auth delete --index < index of the profile >` を使用します。 
6. ローカルコンピューターからすべての認証プロファイルをクリアする場合は、コマンド `pac auth clear` を使用します。 この操作は元に戻すことができます。ローカルコンピューターから `authprofile.json` ファイルとトークンキャッシュファイルを完全に削除します。 

## <a name="deploying-code-components"></a>コードコンポーネントの配置 

認証プロファイルが正常に作成されたら、最新の変更をすべて使用して、コードコンポーネントの Common Data Service インスタンスへのプッシュを開始できます。 `push` 機能は、コードコンポーネントのバージョン管理要件をバイパスし、ソリューション (cdsproj) をビルドしてコードコンポーネントをインポートする必要がないため、開発者が開発するサイクルの開発を高速化します。 `push` 機能を使用するには、次の手順を実行します。

1. 有効な認証プロファイルが作成されていることを確認します。
2. コードコンポーネントプロジェクトが作成されたルートディレクトリに移動します。
3. コマンド `pac pcf push --publisher-prefix <your publisher prefix>` を実行します。

   > [!NOTE]
   > `push` コマンドで使用するパブリッシャープレフィックスは、コンポーネントが含まれるソリューションの発行者プレフィックスと一致している必要があります。

## <a name="how-to-remove-components-from-a-solution"></a>ソリューションからコンポーネントを削除する方法

ソリューションファイルからコードコンポーネントを削除するには、次のようにします。

1.  ソリューションプロジェクトディレクトリの `cdsproj` ファイルを編集し、コンポーネントへの参照を削除します。 コンポーネント参照の例を次に示します。

   ```XML
   <ItemGroup>
       <Projectreference Include="..\pcf_component\pcf_component.pcfproj">
         <Project>0481bd83-ffb0-4b70-b526-e0b3dd63e7ef</Project>
         <Name>pcf_component </Name>
         <Targets>Build</Targets>
         <referenceOutputAssembly>false</referenceOutputAssembly>
         <OutputItemType>Content</OutputItemType>
         <CopyToOutputDirectory>Always</CopyToOutputDirectory>
       </Projectreference>
   </ItemGroup>
   ```

2. 次のコマンドを使用してリビルド (またはクリーン) を実行します。
   
    ```CLI
    msbuild /t:rebuild
    ```

### <a name="see-also"></a>関連項目

[モデル駆動型アプリ内のフィールドまたはエンティティへのコードコンポーネントの追加](add-custom-controls-to-a-field-or-entity.md)<br/>
[キャンバスアプリにコンポーネントを追加する](component-framework-for-canvas-apps.md#add-components-to-a-canvas-app)<br/>
[PowerApps コンポーネントフレームワーク API リファレンス](reference/index.md)<br/>
[PowerApps コンポーネントフレームワークの概要](overview.md)
