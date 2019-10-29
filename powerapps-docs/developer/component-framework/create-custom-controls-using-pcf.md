---
title: コードコンポーネントを作成してビルドする |Microsoft Docs
description: PowerApps component framework ツールを使用してコンポーネントの作成を開始する
keywords: PowerApps コンポーネントフレームワーク、コードコンポーネント、コンポーネントフレームワーク
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 06/20/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2cbf58a-9112-45c2-b823-2c07a310714c
ms.openlocfilehash: 9a02b64321564b0a09e6b53223f13748358d76cf
ms.sourcegitcommit: 7c1e70e94d75140955518349e6f9130ce3fd094e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/29/2019
ms.locfileid: "73025774"
---
# <a name="create-and-build-a-code-component"></a>コードコンポーネントの作成とビルド

このトピックでは、PowerApps CLI を使用してコードコンポーネントを作成および配置する方法について説明します。 [MICROSOFT POWERAPPS CLI](https://aka.ms/PowerAppsCLI)がインストールされていることを確認します。

## <a name="create-a-new-component"></a>新しいコンポーネントの作成

開始するには、PowerApps CLI をインストールした後で、 **FOR VS 2017 の開発者コマンドプロンプトを**開きます。

1. VS 2017 の開発者コマンドプロンプトで、name\Documents\My_code_Component `mkdir <Specify the folder name>`コマンドを使用して*C:\Users\your*など、ローカルコンピューター上に新しいフォルダーを作成します。
2. コマンド `cd <specify your new folder path>` を使用して、新しく作成したフォルダーにアクセスします。
3. コマンドを使用していくつかの基本パラメーターを渡すことによって、新しいコンポーネントプロジェクトを作成します。

    `pac pcf init --namespace <specify your namespace here> --name <Name of the code component> --template <component type>`
 
   > [!NOTE]
   > 現在、PowerApps CLI は、モデル駆動型アプリ用の**フィールド**と**データセット**という2種類のコンポーネントをサポートしています。  キャンバスアプリの場合、この実験的なプレビューでサポートされているのは**フィールド**の種類のみです。

4. 必要なすべてのプロジェクトの依存関係を取得するには、コマンド `npm install` を実行します。
5. 任意の開発環境でプロジェクトフォルダー `C:\Users\<your name>\Documents\<My_code_Component>` を開き、コードコンポーネントの開発を開始します。 開始する最も簡単な方法は、`C:\Users\<your name>\Documents\<My_code_Component>` ディレクトリにアクセスした後、コマンドプロンプトから `code .` を実行することです。 このコマンドにより、コンポーネントプロジェクトが Visual Studio Code で開きます。
6. マニフェスト、コンポーネントロジック、スタイルなど、コンポーネントに必要なアーティファクトを実装し、コンポーネントプロジェクトをビルドします。 詳細情報:[サンプルコンポーネントの実装](implementing-controls-using-typescript.md)

## <a name="build-your-component"></a>コンポーネントをビルドする

コンポーネントプロジェクトをビルドするには、Visual Studio Code の `package.json` が含まれているプロジェクトフォルダーを開き、(Ctrl + Shift + B) コマンドを使用して、ビルドオプションを選択します。 または、[開発者コマンドプロンプト for VS 2017] ウィンドウの [`npm run build`] コマンドを使用して、コンポーネントをすばやくビルドすることもできます。

> [!TIP]
> ビルド操作中またはビルド操作後にコンポーネントをデバッグする方法については、「[コードコンポーネントのデバッグ](debugging-custom-controls.md)」を参照してください。

TypeScript でコンポーネントロジックの実装が完了したら、ソリューションを Common Data Service にインポートできるように、すべてのコードコンポーネント要素をソリューションファイルにバンドルする必要があります。 詳細情報:[コードコンポーネントのパッケージ化](import-custom-controls.md)

## <a name="known-configuration-issues-and-workarounds"></a>既知の構成の問題と回避策

**Msbuild エラー MSB4036:**

1. プロジェクトファイル内のタスクの名前は、タスククラスの名前と同じになります。
2. Task クラスは public で、ITask インターフェイスを実装しています。
3. タスクは、プロジェクトファイル内の *\<UsingTask >* または path ディレクトリにある *. tasks ファイルで正しく宣言されています。

**解決**

1. Visual Studio インストーラーを開きます。 
1. Visual Studio 2017 の場合は、 **[変更]** を選択します。 
1. **個々のコンポーネント**を選択します。
1. コードツール で、 **NuGet ターゲット & ビルドタスク** をオンにします。

**パブリッシャープレフィックス**

0\.4.3 よりも前の PowerApps CLI ツールバージョンを使用してコンポーネントを作成した場合は、ソリューションファイルを Common Data Service に再インポートしようとするとエラーが発生します。 新しくインポートされたコンポーネント名には、その一意性を確保し、競合を回避するために、パブリッシャーのプレフィックスを追加するため、このエラーがスローされます。

**回避策**:

- 関連するコンポーネントを含むソリューションを Common Data Service から削除します。 コンポーネントが既にフォームまたはグリッドで構成されている場合は、コンポーネントソリューションが構成に依存していたため、最初にコンポーネントを削除する必要があります。  
- 最新の CLI バージョンでビルドされたコンポーネントの更新プログラムを使用して、新しいソリューションをインポートします。
- 新しくインポートされたコンポーネントは、フォームまたはグリッドで構成できるようになりました。  


<!--2. When the components are created with the publisher prefix in mixed or upper case using the new CLI tooling version, it throws an error while importing the solution. This happens because the updated tooling version (0.4.3 and newer) now enforces the platform standard for lower case publisher prefix.

   **Workaround**:

    Update the solution and customizations to ensure that the associated prefix is modified to lower case and import the new solution into Common Data Service.-->


### <a name="see-also"></a>関連項目

[コードコンポーネントのデバッグ](debugging-custom-controls.md)<br/>
[コードコンポーネントのパッケージ化](import-custom-controls.md)<br/>
[フィールドまたはエンティティへのコードコンポーネントの追加](add-custom-controls-to-a-field-or-entity.md)<br/>
[既存のコードコンポーネントの更新](updating-existing-controls.md)<br/>
[PowerApps コンポーネントフレームワーク API リファレンス](reference/index.md)<br/>
[PowerApps コンポーネントフレームワークの概要](overview.md)
