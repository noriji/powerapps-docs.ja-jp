---
title: キャンバス アプリの PowerApps Component Framework | Microsoft Docs
description: キャンバス アプリのコード コンポーネントを作成する
keywords: null
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 08/31/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5d100dc3-bd82-4b45-964c-d90eaebc0735
---

# <a name="powerapps-component-framework-for-canvas-apps"></a>キャンバス アプリの PowerApps Component Framework

> [!IMPORTANT]
> この機能はまだ実験的であり既定で無効になっています。 詳細については [実験的機能とプレビュー機能](../../maker/canvas-apps/working-with-experimental.md) を参照してください。

PowerApps Component Framework を使用すると、アプリ作成者はアプリ内やアプリ全体で使用するコード コンポーネントを作成できます。 詳細: [PowerApps Component Framework の概要](overview.md) 

この実験的プレビューでは、PowerApps component framework により、アプリ作成者は PowerApps CLI ツールを使用してコード コンポーネントを作成、デバッグ、インポート、キャンバス アプリに追加できます。 この実験的プレビューでは特定の API のみがサポートされています。 それぞれの API がキャンバス アプリをサポートしているか確認することを推奨します。 

> [!WARNING]
> コード コンポーネントには Microsoft が生成していない可能性があるコードが含まれており、セキュリティ トークンやデータにアクセスする可能性があります。 コード コンポーネントをアプリに追加するときは、コード コンポーネント ソリューションが信頼できるソースのものであることを確認してください。

## <a name="prerequisites"></a>前提条件

1. 環境で PowerApps コンポーネント機能を有効にするには、システム管理者特権が必要です。

> [!IMPORTANT]
> 既定で PowerApps Component Framework はモデル駆動型アプリに対して有効です。

## <a name="enable-powerapps-component-framework-feature"></a>PowerApps Component Framework 機能を有効にする

アプリにコード コンポーネントを追加するには、使用するそれぞれの環境で PowerApps Component Framework 機能を有効にする必要があります。 環境がアプリ内でコード コンポーネントを使用するようにする方法:

1. [PowerApps](https://powerapps.microsoft.com/en-us/) にサインインします。

2. **設定** アイコンをクリックして **管理センター** を選択します。
    
    ![設定の管理センター](media/select-admin-center-from-settings.png "設定の管理センター") 

3. この機能を有効にする環境を選択し、**...** をクリックしてから **設定** を選択します。

4. **製品** タブで **機能** を選択します。

   ![PCF の有効化](media/enable-pcf-feature.png "PCF の有効化")

5. 利用可能な機能のリストから **キャンバス アプリの PowerApps Component Framework** のスイッチをオンにします。

6. ここで、コード コンポーネントを追加するアプリを開き **ファイル** > **アプリ設定** に移動して、**詳細設定** を選択します。

   ![PCF のコンポーネントを有効にする](media/enable-components-for-pcf.png "PCF のコンポーネントを有効にする")
   
7. **実験的機能** セクションの下の **コンポーネント** スイッチをオンにします。

## <a name="implementing-code-components"></a>コード コンポーネントの実装

環境で PowerApps Component Framework 機能を有効にしたら、コード コンポーネントのロジックの実装を開始できます。 [サンプル コンポーネントを実装する](implementing-controls-using-typescript.md) のトピックでは、カスタム ロジック、マニフェスト ファイル、デバッグ プロセスの実装、ソリューション zip ファイルの作成、ソリューションの Common Data Service へのインポートから、直接コード コンポーネントを作成するプロセスをステップごとに説明します。

> [!NOTE]
> コード コンポーネントの実装は、モデル駆動型アプリとキャンバス アプリ (実験的プレビュー) の両方で同じです。 唯一の違いはコード コンポーネントの追加です。 

## <a name="add-components-to-a-canvas-app"></a>キャンバス アプリにコンポーネントを追加する

キャンバス アプリにコード コンポーネントを追加する方法:

> [!NOTE]
> モデル駆動型アプリのフィールドやエンティティにコード コンポーネントを追加する方法は [モデル駆動型アプリにコード コンポーネントを追加する](add-custom-controls-to-a-field-or-entity.md) を参照してください。

1. PowerApps Studio に移動します。
2. コード コンポーネントを追加する新しいキャンバス アプリを作成するか、既存のアプリを編集します。

   > [!IMPORTANT]
   > 次のステップに進む前に、ソリューションの zip ファイルがすでに Common Data Service に [インポート](https://docs.microsoft.com/en-us/powerapps/maker/common-data-service/import-update-export-solutions) されていることを確認してください。

3. **挿入** > **コンポーネント** > **コンポーネントをインポート** の順にクリックします。 
 
    ![コンポーネントの挿入](media/insert-components-import.png "コンポーネントの挿入")

4. **コード (実験的)** タブを選択し、リストからコンポーネントを追加して **インポート** をクリックします。 これで **コンポーネント** メニューにサンプル コンポーネントが追加されます。

    ![サンプル コンポーネントのインポート](media/import-component-add-sample-component.png "サンプル コンポーネントのインポート")

5. **コンポーネント** に移動し、コンポーネントを選択してアプリに追加します。

   ![サンプル コンポーネントを追加](media/add-sample-component-from-list.png "サンプル コンポーネントを追加")

## <a name="delete-a-code-component"></a>コード コンポーネントの削除 

キャンバス アプリからコード コンポーネントを削除するには、削除するコード コンポーネントを選択してメニューの **削除** ボタンを押します。 コード コンポーネントをアプリから削除すると、すべてのコード コンポーネント要素がアプリとアプリ パッケージから削除されます。 

## <a name="updating-existing-code-components"></a>既存のコード コンポーネントを更新する

コード コンポーネントを更新する場合は、マニフェスト ファイルで *バージョン* 属性を指定し、最新の変更がランタイムに反映されるようにします。 キャンバス アプリの場合、既存のコード コンポーネントを更新するときに *バージョン* 属性を更新する必要はありません。 設計上、キャンバス アプリは最新のコード コンポーネントを取得して実行時に表示します。 同じコンポーネントは単一バージョンのみがキャンバス アプリに存在できます。

> [!NOTE]
> 既存のコード コンポーネントが更新されるのは PowerApps Studio でアプリを閉じたとき、または再度開いたときだけです。 アプリを再度開くと、コード コンポーネントを更新するように求められます。 コード コンポーネントを削除したり、コード コンポーネントをアプリに追加し直すだけでは、コンポーネントは更新されません。

## <a name="see-also"></a>関連項目

[PowerApps Component Framework の概要](overview.md)<br/>
[サンプル コンポーネントを実装する](implementing-controls-using-typescript.md)

