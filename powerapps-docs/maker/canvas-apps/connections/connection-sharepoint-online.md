---
title: SharePoint 接続の概要 | Microsoft Docs
description: SharePoint の使用可能な機能、応答、および例を参照してください。
author: NickWaggoner
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 04/03/2019
ms.author: niwaggon
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: ae82166b9cc21de1e25f99f7606ce7b95b2152b9
ms.sourcegitcommit: 57b968b542fc43737330596d840d938f566e582a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2019
ms.locfileid: "71993975"
---
# <a name="connect-to-sharepoint-from-a-canvas-app"></a>キャンバスアプリから SharePoint に接続する

![SharePoint](./media/connection-sharepoint-online/sharepointicon.png)

SharePoint サイトに接続してカスタムリストからアプリを自動的に生成するか、既存のアプリにデータを追加する前に接続を作成するか、アプリを最初から作成します。

データが置かれている場所に応じて、次のいずれかまたは両方の方法を取ることができます。

- SharePoint Online サイトまたはオンプレミスサイトのカスタムリストのデータを表示します。
- ライブラリで画像を表示し、ビデオまたはオーディオファイルを再生する (SharePoint Online のみ)。

## <a name="generate-an-app"></a>アプリを生成する

カスタムリストのデータを管理する場合は、PowerApps で[自動的に3画面のアプリを生成](../app-from-sharepoint.md)することができます。 ユーザーは、最初の画面で一覧を参照し、2番目の画面に項目の詳細を表示し、3番目の画面で項目を作成または更新できます。

> [!NOTE]
> SharePoint リストに**選択肢**、**ルックアップ**、または**ユーザーまたはグループ**の列が含まれている場合は、このトピックの「[ギャラリーにデータを表示](connection-sharepoint-online.md#show-list-columns-in-a-gallery)する」を参照してください。

## <a name="create-a-connection"></a>接続を作成する

1. [PowerApps にサインイン](http://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)し、左側のナビゲーションバーで [**データ** > **接続**] を選択し、左上隅にある **[新しい接続]** を選択します。

    > [!div class="mx-imgBorder"]
    > 左側のナビゲーションバーでデータ > 接続を ![Select、左上隅にある [新しい接続] を選択します。](./media/connection-sharepoint-online/new-connection.png)

1. 右上隅にある検索ボックスに「 **sharepoint**」と入力するか貼り付け、 **[sharepoint]** を選択します。

    > [!div class="mx-imgBorder"]
    > 右上隅にある検索ボックス ![In、SharePoint を入力するか貼り付け、[SharePoint] を選択します。](./media/connection-sharepoint-online/select-sharepoint.png)

1. 次のいずれかの手順を実行します。

    - SharePoint Online に接続するには、 **[直接接続 (クラウドサービス)]** を選択し、 **[作成]** を選択して、資格情報を入力します (メッセージが表示された場合)。

        > [!div class="mx-imgBorder"]
        > SharePoint Online に接続 ![To には、[直接接続 (クラウドサービス)] を選択し ](./media/connection-sharepoint-online/select-online.png)

        接続が作成され、既存のアプリにデータを追加したり、アプリを最初から作成したりすることができます。

    - オンプレミスサイトに接続するには、[オン**プレミスデータゲートウェイを使用して接続**する] を選択します。

        > [!div class="mx-imgBorder"]
        > [オンプレミスのサイトに接続 ![To には、[オンプレミスデータゲートウェイを使用して接続する] を選択し ](./media/connection-sharepoint-online/select-onprem.png)

        認証の種類として **[Windows]** を指定し、資格情報を入力します (資格情報にドメイン名が含まれる場合は、 *<ドメイン>\<エイリアス>* 形式で入力します)。

        > [!div class="mx-imgBorder"]
        > ![Specify の資格情報 ](./media/connection-sharepoint-online/specify-creds.png)

        **[ゲートウェイの選択]** で、使用するゲートウェイを選択し、 **[作成]** を選択します。

        > [!NOTE]
        > オンプレミスデータゲートウェイがインストールされていない場合は、ゲートウェイを[インストール](../gateway-reference.md)し、アイコンを選択して、ゲートウェイの一覧を更新します。

        > [!div class="mx-imgBorder"]
        > ゲートウェイ ](./media/connection-sharepoint-online/choose-gateway.png) の ![Choose

        接続が作成され、既存のアプリにデータを追加したり、アプリを最初から作成したりすることができます。

## <a name="add-data-to-an-existing-app"></a>既存のアプリにデータを追加する

1. PowerApps Studio で、更新するアプリを開き、 **[表示]** タブを選択し、 **[データソース]** を選択します。

    > [!div class="mx-imgBorder"]
    > ![On 表示] タブをクリックし、[データソース] を選択し ](./media/connection-sharepoint-online/view-data-sources.png)

1. **データ**ペインで、[**データソース** > **SharePoint**に追加] を選択します。

1. **[SharePoint サイトへの接続]** で、 **[最近使っ]** たサイト の一覧でエントリを選択します (または、使用するサイトの URL を入力または貼り付け)、 **[接続]** を選択します。

    > [!div class="mx-imgBorder"]
    > ![Select サイト ](./media/connection-sharepoint-online/select-sp-site.png)

1. **[一覧の選択]** で、使用する**ドキュメント**または1つ以上の一覧のチェックボックスをオンにし、 **[接続]** を選択します。

    > [!div class="mx-imgBorder"]
    > 一覧を選択 ![Under には、使用するドキュメントまたは1つ以上の一覧のチェックボックスをオンにし、[接続] を選択し ](./media/connection-sharepoint-online/select-sp-tables.png)

    すべての種類のリストが既定で表示されるわけではありません。 PowerApps ではカスタム リストはサポートされますが、テンプレート ベースのリストはサポートされません。 使用するリストの名前が表示されない場合は、一番下までスクロールし、[**カスタムテーブル名を入力**してください] と表示されているボックスにリストの名前を入力します。

    > [!div class="mx-imgBorder"]
    > [カスタムリスト名を入力してください] ボックスの一覧の名前 ![Type ます。](./media/connection-sharepoint-online/custom-list.png)

    データソースまたはソースがアプリに追加されます。

## <a name="build-your-own-app-from-scratch"></a>独自のアプリを最初から作成する

「[アプリを最初から作成](../get-started-create-from-blank.md)する」の概念を Excel ではなく SharePoint に適用します。

## <a name="show-list-columns-in-a-gallery"></a>ギャラリーにリスト列を表示する

カスタムリストにこれらの種類の列が含まれている場合は、数式バーを使用してそのギャラリー内の1つまたは複数の**ラベル**コントロールの**Text**プロパティを設定することにより、そのデータを**ギャラリー**コントロールに表示します。

- **選択**列または**参照**列の場合は、この項目を指定し**ます。** _ColumnName_ **。** 列にデータを表示する値。

    たとえば、**Location** という名前の**選択肢**列がある場合は「**ThisItem.Location.Value**」と指定し、**PostalCode** という名前の**ルックアップ**列がある場合は「**ThisItem.PostalCode.Value**」と指定します。

- **個人またはグループ**の列の場合は、この項目を指定し**ます。** _ColumnName_ **。DisplayName**を指定すると、ユーザーまたはグループの表示名が表示されます。

    たとえば、**Manager** という名前の**ユーザーまたはグループ**列の名前を表示する場合は、「**ThisItem.Manager.DisplayName**」と指定します。

    メール アドレスや役職など、ユーザーに関する別の情報を表示することもできます。 オプションの完全な一覧を表示するには、この項目を指定し**ます。** _ColumnName_ **。** (末尾のピリオドを含む)。

    > [!NOTE]
    > **CreatedBy**列の場合は、この項目を指定します **。** この場合、リスト内で項目を作成したユーザーの表示名が表示されます。 **ModifiedBy** 列のリストの項目を変更したユーザーの表示名を表示するには、「**ThisItem.Editor.DisplayName**」と指定します。

- **マネージメタデータ**列の場合は、この項目を指定し**ます。** _ColumnName_ **。** 列にデータを表示するラベル。

    たとえば、**Languages** という名前の **管理されたメタデータ**列がある場合は「**ThisItem.Languages.Label**」と指定します。

## <a name="show-data-from-a-library"></a>ライブラリからデータを表示する

SharePoint ライブラリに複数のイメージがある場合は、表示するイメージをユーザーが指定できるように、**ドロップダウン**コントロールをアプリに追加できます。 **ギャラリー**コントロールなどの他のコントロールや、ビデオなどの他の種類のデータにも同じ原則を適用できます。

1. まだ[接続を作成](#create-a-connection)していない場合は、[既存のアプリにデータを追加](#add-data-to-an-existing-app)します。

1. **ドロップダウン**コントロールを追加し、 **ImageList**という名前を指定します。

1. **ImageList**の**Items**プロパティを**Documents**に設定します。

1. 右側のウィンドウの **[プロパティ]** タブで、 **[値]** ボックスの一覧を開き、 **[名前]** を選択します。

    ライブラリ内のイメージのファイル名が**ImageList**に表示されます。

    > [!div class="mx-imgBorder"]
    > イメージの ![List ](./media/connection-sharepoint-online/dropdown-items.png)

1. **イメージ**コントロールを追加し、 **image**プロパティを次の式に設定します。

    `ImageList.Selected.'Link to item'`

1. F5 キーを押し、 **[ImageList]** で別の値を選択します。

    指定したイメージが表示されます。

    > [!div class="mx-imgBorder"]
    > ![Sample イメージ ](./media/connection-sharepoint-online/golden-honey.png)

SharePoint ライブラリからデータを表示するためのより複雑な方法を示す[サンプルアプリをダウンロード](https://pwrappssamples.blob.core.windows.net/samples/spdoclib_blogapp.msapp)できます。

1. アプリをダウンロードした後、 [PowerApps Studio](https://us.create.powerapps.com/studio/#)を開き、左側のナビゲーションバーで **[開く]** を選択し、 **[参照]** を選択します。
1. **[開く]** ダイアログボックスで、ダウンロードしたファイルを見つけて開き、このトピックの最初の2つの手順に従って、データソースとして SharePoint ライブラリを追加します。

> [!NOTE]
> 既定では、このアプリには[委任の警告](../delegation-overview.md)が表示されますが、ライブラリに含まれる項目が500未満の場合は無視できます。

この1画面アプリでは、左下隅の一覧に、ライブラリ内のすべてのファイルが表示されます。

- ファイルを検索するには、上部の [検索] ボックスに1つ以上の文字を入力するか、貼り付けます。
- ライブラリにフォルダーが含まれている場合は、タイトルバーの直下にあるフォルダーの一覧でフィルターアイコンを選択すると、ファイルの一覧をフィルター処理できます。

目的のファイルが見つかったら、それを選択して、右上にある**ビデオ**、**画像**、または**オーディオ**コントロールに表示します。

> [!div class="mx-imgBorder"]
> ![Sample イメージ ](./media/connection-sharepoint-online/library-app.png)

## <a name="known-issues"></a>既知の問題

### <a name="lists"></a>表示

PowerApps では、スペースを含む列名を読み取ることができますが、スペースは、16進数のエスケープコード **"\_x0020 \_"** で置き換えられます。 たとえば、SharePoint の **"Column Name"** は、PowerApps のデータ レイアウトに表示されるときや数式で使用されるときは **"Column_x0020_Name"** と表示されます。

すべての種類の列がサポートされているわけではありません。また、すべての種類の列でサポートされている種類の列もありません。

| 列の種類 | サポート | 既定のカード |
| --- | --- | --- |
| 1 行テキスト |はい |View text |
| 複数行テキスト |はい |View text |
| 選択肢 |はい |ルックアップの表示<br>ルックアップの編集<br>複数選択の表示<br>複数選択の編集 |
| Number |はい |パーセンテージの表示<br>評価の表示<br>View text |
| 通貨 |はい |パーセンテージの表示<br>評価の表示<br>View text |
| 日付と時刻 |はい |View text |
| ルックアップ |はい |ルックアップの表示<br>ルックアップの編集<br>複数選択の表示<br>複数選択の編集 |
| ブール値 (はい/いいえ) |はい |View text<br>トグルの表示 |
| 人物またはグループ |はい |ルックアップの表示<br>ルックアップの編集<br>複数選択の表示<br>複数選択の編集 |
| ハイパーリンク |はい |URL の表示<br>View text |
| 画像 |はい (読み取り専用) |画像の表示<br>View text |
| 添付ファイル |はい (読み取り専用) |添付ファイルの表示|
| 集計値 |はい (読み取り専用) | |
| タスクの結果 |いいえ | |
| 外部データ |いいえ | |
| 管理されたメタデータ |はい (読み取り専用) | |
| 評価 |いいえ | |

### <a name="libraries"></a>ライブラリ

- PowerApps からライブラリにファイルをアップロードすることはできません。
- Pdf ビューアーコントロールのライブラリから PDF ファイルを表示することはできません。
- PowerApps Mobile では、**ダウンロード**機能がサポートされていません。
- ユーザーが PowerApps Mobile または Windows 10 アプリでアプリを実行する場合は、 **Launch**関数を使用してライブラリコンテンツをギャラリーに表示します。

## <a name="next-steps"></a>次の手順

- [データ ソースからデータを表示する方法](../add-gallery.md)を学習する。
- [詳細を表示する方法とレコードを作成または更新する方法](../add-form.md)を学習する。
- 接続できる他の種類の[データ ソース](../connections-list.md)を確認する。
