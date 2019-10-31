---
title: Dynamics 365 ポータル構成の移行 | MicrosoftDocs
description: Dynamics 365 ポータル構成の移行方法を説明します。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: null
ms.date: 08/30/2019
ms.author: shjais
ms.reviewer: null
---

# <a name="migrate-dynamics-365-portals-configuration"></a>Dynamics 365 ポータル構成の移行

[!include[cc-beta-prerelease-disclaimer](../../../includes/cc-beta-prerelease-disclaimer.md)]

ポータル開発には、ポータル エンド ユーザーのための望ましいエクスペリエンスを実現するための、複数の構成およびカスタマイズが含まれます。

Dynamics 365 ポータル インスタンスの開発または構成が完了した後、最新の Dynamics 365 ポータル構成を、開発環境からテスト環境へ、あるいは実稼働環境へ移行することもできます。 移行には、ソースの Dynamics 365 インスタンスからの既存の構成のエクスポートと、ターゲットの Dynamics 365 インスタンスへのインポートが含まれています。

構成データをエクスポートするには、Configuration Migration ツールおよびポータル固有の構成スキーマ ファイルを使用する必要があります。 このツールの詳細については、[構成データの管理](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/admin/manage-configuration-data)を参照してください。

> [!NOTE]
> - 最新のバージョンの Configuration Migration ツールの使用を推奨いたします。 構成移行ツールは NuGet からダウンロードすることができます。 ツールのダウンロードについては、 [NuGetからツールをダウンロード](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/download-tools-nuget)を参照してください。
> - 構成移行のスキーマ ファイルでサポートされている Dynamics 365 ポータルの最小バージョンのソリューションは 8.4.0.275 です。 ただし、最新バージョンのソリューションを使用することをお勧めします。

スキーマ ファイルは次のポータルの種類に対して使用することができます。
- [コミュニティ ポータル](https://go.microsoft.com/fwlink/p/?linkid=2019704)
- [顧客セルフサービス ポータル](https://go.microsoft.com/fwlink/p/?linkid=2019705)
- [パートナー ポータル](https://go.microsoft.com/fwlink/p/?linkid=2019803)
- [従業員セルフサービス ポータル](https://go.microsoft.com/fwlink/p/?linkid=2019802)
- [カスタム ポータル](https://go.microsoft.com/fwlink/p/?linkid=2019804)

既定のスキーマ ファイルには、すべてのポータル エンティティ、関連付け、および各エンティティの一意性の定義に関する情報が含まれています。 詳細については、[ポータル構成データのエクスポート](#export-portal-configuration-data)を参照してください。

組織データをエクスポートした後、ターゲット環境にそれをインポートする必要があります。 詳細については、[ポータル構成データのインポート](#import-portal-configuration-data)を参照してください。

> [!NOTE]
> スキーマ ファイルは、スキーマを最初から作成するために必要な労力を軽減するために提供されます。 スキーマはツールで用意されている標準的な方法を使用して実装に合わせて調整することができます。 スキーマ ファイルは、Configuration Migration ツールで読み込み、エンティティ、属性などを追加、削除、変更して変更することができます。

## <a name="export-portal-configuration-data"></a>ポータル構成データのエクスポート

ポータル構成データは、ポータル固有の構成データ スキーマ ファイルを使用して、ソース システムからエクスポートすることができます。

1.  Configuration Migration ツールをダウンロードして目的のフォルダーに解凍することができます。

2.  ユーザーのポータルの種類のために用意された上記のリンクを使用して、ポータル構成スキーマ ファイルをダウンロードします。

3.  **DataMigrationUtility.exe** ファイルを `<your_folder>\Tools\ConfigurationMigration` フォルダーでダブルクリックして、Configuration Migration ツールを実行し、メイン画面から**データのエクスポート**を選択し、**続行**を選択します。
    
    > [!div class=mx-imgBorder]
    > ![構成データのエクスポート](../media/export-config-data.png "構成データのエクスポート")

4.  **ログイン**画面で、認証の詳細を指定し、データのエクスポート元の Dynamics 365 インスタンスに接続します。 Dynamics 365 インスタンスに複数の組織があり、データをエクスポートする組織を選択する場合、**使用可能な組織の一覧を表示する**チェック ボックスを選択し、**ログイン**を選択します。

    > [!div class=mx-imgBorder]
    > ![認証の詳細を指定してデータのエクスポート元の Dynamics 365 インスタンスに接続](../media/export-config-login.png "認証の詳細を指定してデータのエクスポート元の Dynamics 365 インスタンスに接続")

5.  複数の組織があり、**使用可能な組織の一覧を常に表示する**チェック ボックスを前のステップでオンにした場合、次の画面で接続する組織を選択することができます。 接続する Dynamics 365 組織を選択します。 

    > [!NOTE]
    > 複数の組織がない場合、この画面は表示されません。

6.  **スキーマ ファイル**では、データのエクスポートに使用するポータル固有の構成スキーマ ファイルを参照して選択します。

7.  **データ ファイルに保存**では、エクスポートするデータ ファイルの名前および場所を指定します。

    > [!div class=mx-imgBorder]
    > ![スキーマおよびターゲット ファイルを指定](../media/export-config-file-name.png "スキーマおよびターゲット ファイルを指定")

8.  **データのエクスポート**を選択します。 クスポートが完了すると、画面の下部に、エクスポートの進行状況とエクスポートされたファイルの場所が表示されます。

    > [!div class=mx-imgBorder]
    > ![構成データのエクスポートの進行状況](../media/export-config-status.png "構成データのエクスポートの進行状況")

    > [!IMPORTANT]
    > Configuration Migration ツールはエンティティ内のレコードのフィルター処理はサポートしません。 既定では、選択したエンティティのすべてのレコードがエクスポートされます。 そのため、複数の Web サイト レコードを作成済みの場合は、すべての Web サイト レコードがエクスポートされます。

9.  **終了**を選択して、ツールを閉じます。

## <a name="import-portal-configuration-data"></a>ポータル構成データのインポート

1.  Configuration Migration ツールを実行してメイン画面で**データのインポート**を選択し、 **続行**を選択します。

    > [!div class=mx-imgBorder]
    > ![構成データのインポート](../media/import-config-data.png "構成データのインポート")

2.  **ログイン**画面で、認証の詳細を指定し、データのエクスポート元の Dynamics 365 インスタンスに接続します。 Dynamics 365 インスタンスに複数の組織があり、データをエクスポートする組織を選択する場合、**使用可能な組織の一覧を表示する**チェック ボックスを選択し、**ログイン**を選択します。

3.  複数の組織があり、**使用可能な組織の一覧を常に表示する**チェック ボックスを前のステップでオンにした場合、次の画面で接続する組織を選択することができます。 接続する Dynamics 365 組織を選択します。 

    > [!NOTE]
    > - 複数の組織がない場合、この画面は表示されません。
    > - 構成をインポートする計画がある組織に、ポータル ソリューションがインストール済みであることを確認します。

4.  次の画面で、インポートするデータ ファイル (.zip) を指定するように求められます。 データ ファイルを参照して選択し、**データのインポート**を選択します。 

    > [!div class=mx-imgBorder]
    > ![構成データのインポートの進行状況](../media/import-config-status.png "構成データのインポートの進行状況")

5.  次の画面にレコードのインポートの状態が表示されます。 データのインポートは複数のパスで実行され、最初に依存データのキュー中に基盤データをインポートし、続くパスで依存データをインポートし、データ依存またはリンクを処理します。 これにより、クリーンで一貫性のあるデータ インポートができます。 

6.  **終了**を選択して、ツールを閉じます。 
