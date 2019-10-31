---
title: コードコンポーネントの作成と構築 | Microsoft Docs
description: PowerApps component framework ツールを使用してコンポーネントを作成する
keywords: PowerApps component framework、コード コンポーネント、コンポーネント フレームワーク
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 06/20/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2cbf58a-9112-45c2-b823-2c07a310714c
---

# <a name="create-and-build-a-code-component"></a>コードコンポーネントを作成、構築する

このトピックでは、 PowerApps CLIコンポーネントを使用してコードを作成および展開する方法を説明します。 [Microsoft PowerApps CLI](https://aka.ms/PowerAppsCLI) がインストールされていることが前提となります。

## <a name="create-a-new-component"></a>新しいコンポーネントの作成

開始するには、 PowerApps CLI をインストールした後で **開発者向けコマンド プロンプト for Visual Studio 2017** を開きます。

1. 開発者向けコマンド プロンプト for Visual Studio 2017 で、ローカルにに新規フォルダを作成します。作成例としては、 *C:\Users\your name\Documents\My_PCF_Component* using the command `mkdir <Specify the folder name>`です。
2. コマンド `cd <specify your new folder path>` を使用して、新しく作成したフォルダに移動します。
3. 以下のコマンドを実行し、いくつかの基本パラメータを渡して新しいコンポーネントプロジェクトを作成します:

    `pac pcf init --namespace <specify your namespace here> --name <put component name here> --template <component type>`
 
   > [!NOTE]
   > 現在 PowerApps CLI supports では、次の2つのコンポーネントに対応しています: **フィールド** 、 **データセット**.  キャンバスのアプリケーションの場合、 **フィールド** タイプはこのプレビューでサポートされています。

4. 必要なプロジェクトの依存関係をすべて取得するには、コマンド `npm install` を実行します。
5. 任意の開発者環境でプロジェクト フォルダ ( `C:\Users\<your name>\Documents\<My_PCF_Component>` ) を開き、コード コンポーネントの開発を始めます。 最も手軽に開始するには、 `C:\Users\<your name>\Documents\<My_PCF_Component>` に移動してコマンド プロンプトで `code .` を実行する方法があります。 このコマンドは、 Visual Studio コードにあるコンポーネントプロジェクトを開きます。

## <a name="build-your-component"></a>コンポーネントを構築する

コンポーネント プロジェクト を構築するには、 Visual Studio コードで `package.json` を含むプロジェクトのフォルダを開きます。(Ctrl-Shift-B) コマンドを使用して、構築オプションを選択します。 あるいは、VS 2017 ウィンドウの開発者向けコマンド プロンプトで `npm run build` コマンドを使用して、簡単にコンポーネントを構築することができます。

> [!TIP]
> 構築中、または構築完了後にコンポーネントのデバッグを行うには、 [コード コンポーネントのデバッグ](debugging-custom-controls.md) を参照してください。

タイプスクリプトでコンポーネントロジックの実装が完了したら、すべてのコード コンポーネント要素をソリューション ファイルにバンドルする必要があります。それによって Common Data Service にソリューションをインポートすることが出来ます。 詳細: [コード コンポーネントをパッケージ化する](import-custom-controls.md)

## <a name="known-configuration-issues-and-workarounds"></a>設定に関する既知の問題と回避策

**Msbuild エラー MSB4036:**

1. プロジェクト ファイルのタスク名はタスク クラスの名前と同じです。
2. タスク クラスはパブリックで Microsoft.Build.Framework.ITask インターフェイスを実装しています。
3. タスクは、プロジェクト ファイルの *\<UsingTask>* または、 パス ディレクトリに格納されている、 *.tasks ファイルにて正しく宣言されています。

**解決方法:**

1. Visual Studio インストーラーを開きます。 
1. For VS 2017 では、 **修正** を選択します。 
1. 個々のコンポーネント をクリックします。
1. コード ツール配下の **NuGet ターゲットと構築タスク** を確認します。

**発行元の接頭辞**

コンポーネントが、 PowerApps CLI ツールの 0.4.3, よりも低いバージョンで作成されている場合は、ソリューション ファイルを Common Data Service へと再インポートする際にエラーが表示されます。 このエラーが表示されるのは、新しくインポートされたコンポーネントの名称に、その一意性と競合を回避する目的で発行元の接頭辞が付加されてるためです。

**回避策**:

- Common Data Serviceから関連するコンポーネントを含むソリューションを削除します。 コンポーネントが既にフォームまたはグリッドに構成されている場合は、コンポーネントソリューションは構成に依存しているため、最初にコンポーネントソリューションを削除する必要があります。  
- 最新のCLIバージョンで構築されたコンポーネントを含む、新たなソリューションをインポートしてください。
- 新たに読み込まれたコンポーネントは、フォームまたはグリッド上で設定できるようになっています。  


<!--2. When the components are created with the publisher prefix in mixed or upper case using the new CLI tooling version, it throws an error while importing the solution. This happens because the updated tooling version (0.4.3 and newer) now enforces the platform standard for lower case publisher prefix.

   **Workaround**:

    Update the solution and customizations to ensure that the associated prefix is modified to lower case and import the new solution into Common Data Service.-->


### <a name="see-also"></a>関連項目

[コード コンポーネントのデバッグ](debugging-custom-controls.md)<br/>
[コード コンポーネントをパッケージ化する](import-custom-controls.md)<br/>
[コード コンポーネントをフィールドやエンティティに追加する](add-custom-controls-to-a-field-or-entity.md)<br/>
[既存のコード コンポーネントを更新する](updating-existing-controls.md)<br/>
[PowerApps Component Framework API の参照](reference/index.md)<br/>
[PowerApps Component Framework の概要](overview.md)
