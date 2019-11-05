---
title: ポータルのエラーログを表示し、Azure Blob storage に格納する |MicrosoftDocs
description: ポータルのエラーログを表示し、Azure Blob storage アカウントに保存する方法について説明します。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 7989c15b0c5c4cf50d4b55f518244758afc067e1
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2019
ms.locfileid: "73542920"
---
# <a name="view-portal-error-logs"></a>ポータルのエラー ログを表示する

ポータル管理者または開発者は、PowerApps ポータルを使用して顧客の web サイトを作成できます。 開発者にとっての一般的なタスクの1つは、ポータルの開発中に問題をデバッグすることです。 デバッグを支援するために、ポータルの問題に関する詳細なエラーログにアクセスできます。 ポータルのエラーログを取得する方法は複数あります。

## <a name="custom-error"></a>カスタムエラー

ポータルでサーバー側の例外が発生した場合、既定では、ユーザーフレンドリなエラーメッセージを含むカスタマイズされたエラーページが表示されます。 エラーメッセージを構成するには、「[カスタムエラーメッセージを表示](#display-a-custom-error-message)する」を参照してください。

ただし、デバッグの目的で、ASP.NET 詳細エラーページ (YSOD) を確認することをお勧めします。 詳細なエラーページを使用すると、サーバーエラーの完全なスタックを取得できます。

> [!div class=mx-imgBorder]
> ![死亡の黄色のスクリーン](../media/ysod.png "死亡の黄色のスクリーン")

YSOD を有効にするには、ポータルで[カスタムエラーを無効](#disable-custom-error)にする必要があります。

> [!NOTE]
> 開発段階ではカスタムエラーを無効にし、有効にした後でカスタムエラーを有効にすることをお勧めします。

カスタムエラーの詳細:[カスタムエラーページの表示](https://docs.microsoft.com/aspnet/web-forms/overview/older-versions-getting-started/deploying-web-site-projects/displaying-a-custom-error-page-cs)

### <a name="disable-custom-error"></a>カスタムエラーの無効化

ポータルで、サーバー側の例外が発生した場合に詳細な例外メッセージが表示されるように、ポータルでカスタムエラーを無効にすることができます。

1. [PowerApps ポータル管理センター](admin-overview.md)を開きます。

2. **[ポータルの操作]**  > 使用して、**カスタムエラーを無効**にします。

   > [!div class=mx-imgBorder]
   > ![カスタムエラーの無効化](../media/disable-custom-errors.png "カスタムエラーの無効化")

3. 確認メッセージで **[無効]** を選択します。 カスタムエラーは無効になっていますが、ポータルは再起動され、使用できなくなります。 カスタムエラーが無効になると、メッセージが表示されます。

### <a name="enable-custom-error"></a>カスタムエラーを有効にする

ポータルでカスタムエラーを有効にすると、YSOD の代わりにプロフェッショナルな外観のページを表示できます。 このページでは、アプリケーションで例外が発生した場合に、意味のある情報を提供します。

1. [PowerApps ポータル管理センター](admin-overview.md)を開きます。

2. **[ポータルの操作]**  > 使用して、**カスタムエラーを有効**にします。

   > [!div class=mx-imgBorder]
   > ![カスタムエラーを有効にする](../media/enable-custom-errors.png "カスタムエラーを有効にする")

3. 確認メッセージで **[有効化]** を選択します。 カスタムエラーが有効になっている間、ポータルは再起動され、使用できなくなります。 カスタムエラーが有効になると、メッセージが表示されます。

> [!NOTE]
> - ポータルが接続されているインスタンスを変更すると、[カスタムエラー] 設定が [有効] に設定されます。 必要に応じて、カスタムエラーを再度無効にする必要があります。
> - ポータルが接続されているインスタンスが変更されているときは、カスタムエラーを有効または無効にしないでください。それ以外の場合は、エラーメッセージが表示されます。

### <a name="display-a-custom-error-message"></a>カスタムエラーメッセージを表示する

一般的なエラーではなく、洗練されたカスタムエラーを表示するようにポータルを構成できます。

カスタムエラーを定義するには、コンテンツスニペット `Portal Generic Error`を使用します。 このスニペットで定義されている内容は、エラーページに表示されます。 このコンテンツスニペットはすぐに使用できないため、作成する必要があります。 コンテンツスニペットの**種類**には、 **Text**または**HTML**を指定できます。 コンテンツスニペットを作成または編集するには、「[コンテンツスニペットを使用](../configure/customize-content-snippets.md)してコンテンツをカスタマイズする」を参照してください。

> [!NOTE]
> 液体コードがコンテンツスニペットに記述されている場合は、スキップされ、レンダリングされません。

カスタムエラーを有効にすると、エラーページに次の構造でメッセージが表示されます。

<Content Snippet> 
<Error ID >
<Date and time>
<Portal ID>

次に、HTML 型のコンテンツスニペットを使用したカスタムエラーメッセージの例を示します。

これはカスタムエラーです。ここをクリックして、エラーのスクリーンショットを含むサポートチケットをファイルにお寄せください

> [!div class=mx-imgBorder]
> ![カスタムエラーメッセージ](../media/custom-error-message.png "カスタムエラーメッセージ")

> [!NOTE]
> ポータルが Common Data Service に接続できないためにコンテンツスニペットを取得できない場合、またはスニペットが Common Data Service で使用できない場合は、エラーメッセージが表示されます。

## <a name="access-portal-error-logs"></a>ポータルのエラーログにアクセスする

ポータルを開発して発行した後も、ポータルのログにアクセスして、顧客から報告された問題をデバッグできる必要があります。 ログにアクセスするには、所有している Azure Blob ストレージアカウントにすべてのアプリケーションエラーを送信するようにポータルを構成します。 ポータルのエラーログにアクセスすることにより、問題の詳細を確認できるので、顧客のクエリに効率的に対応できます。 Azure Blob storage にポータルのエラーログを取得するには、PowerApps ポータル管理センターから診断ログを有効にする必要があります。

> [!NOTE]
> ポータルが接続されている Common Data Service インスタンスを変更すると、診断ログが無効になります。 診断ログを再度有効にする必要があります。

### <a name="enable-diagnostic-logging"></a>診断ログを有効にする

1. [PowerApps ポータル管理センター](admin-overview.md)を開きます。

2. **[ポータルアクション]** にアクセス > **診断ログを有効に**します。

   > [!div class=mx-imgBorder]
   > ![診断ログを有効にする](../media/enable-diagnostic-logging.png "診断ログを有効にする")

3. **[診断ログを有効にする]** ウィンドウで、次の値を入力します。

   - **Azure Blob Storage service の接続文字列**: ポータルのエラーログを格納する Azure Blob Storage サービスの URL。 URL の最大長は2048文字です。 URL が2048文字を超える場合は、エラーメッセージが表示されます。 接続文字列の詳細については[Azure Storage 接続文字列の構成](https://docs.microsoft.com/azure/storage/common/storage-configure-connection-string)」を参照してください。
   - **[保有期間**: 期間] を選択すると、ポータルのエラーログが blob ストレージに保持されます。 選択した期間が経過すると、エラーログが削除されます。 次のいずれかの値を選択できます。
     - 1日
     - 7日間
     - 30日
     - 60日
     - 90日
     - 180日
     - いつも

   既定では、保有期間は30日です。
  
   > [!div class=mx-imgBorder]
   > ![診断ログの有効化ウィンドウ](../media/enable-diagnostic-logging-window.png "診断ログの有効化ウィンドウ")

4. **[構成]** をクリックします。

診断ログを構成すると、Azure ストレージアカウントに新しい**テレメトリログ**blob コンテナーが作成され、コンテナーに格納されている blob ファイルにログが書き込まれます。 次のスクリーンショットは、Azure storage explorer の**テレメトリ-ログ**blob コンテナーを示しています。

> [!div class=mx-imgBorder]
> ![Azure ブログストレージアカウント](../media/azure-blob-storage.png "Azure ブログストレージアカウント")

診断ログが正常に有効になると、次の操作を実行できるようになります。
- **診断ログの構成の更新**: ポータルの診断ログの構成を更新または削除できます。
- **診断ログを無効**にする: ポータルの診断ログの構成を無効にすることができます。
 
### <a name="update-diagnostic-logging"></a>診断ログの更新

1. [PowerApps ポータル管理センター](admin-overview.md)を開きます。

2. ポータルの **[アクション]**  >  **[診断ログの構成の更新]** にアクセスします。

   > [!div class=mx-imgBorder]
   > ![診断ログの構成の更新](../media/update-diagnostic-logging.png "診断ログの構成の更新")

3. [診断ログの更新] 構成ウィンドウで、次の値を入力します。
   - **Azure Blob Storage サービスの接続文字列を更新しますか?** : Azure Blob Storage サービスの接続文字列を更新するかどうかを指定できます。 既定では、これが選択されています。
   - **Azure Blob Storage service の接続文字列**: ポータルのエラーログを格納する Azure Blob Storage サービスの URL。 URL の最大長は2048文字です。 URL が2048文字を超える場合は、エラーメッセージが表示されます。 このフィールドは、 **[Azure Blob Storage サービスの接続文字列を更新しますか?]** チェックボックスがオンになっている場合にのみ表示されます。 接続文字列の詳細については[Azure Storage 接続文字列の構成](https://docs.microsoft.com/azure/storage/common/storage-configure-connection-string)」を参照してください。
   - **[保有期間**: 期間] を選択すると、ポータルのエラーログが blob ストレージに保持されます。 選択した期間が経過すると、エラーログが削除されます。 次のいずれかの値を選択できます。
     - 1日
     - 7日間
     - 30日
     - 60日
     - 90日
     - 180日
     - いつも

   既定では、保有期間は30日です。

   > [!div class=mx-imgBorder]
   > ![診断ログの構成ウィンドウの更新](../media/update-diagnostic-logging-window.png "診断ログの構成ウィンドウの更新")

4. **[更新]** をクリックします。

### <a name="disable-diagnostic-logging"></a>診断ログを無効にする

1. [PowerApps ポータル管理センター](admin-overview.md)を開きます。

2. ポータルの **[操作]**  > 使用して、**診断ログを無効**にします。

   > [!div class=mx-imgBorder]
   > ![診断ログを無効にする](../media/disable-diagnostic-logging.png "診断ログを無効にする")

3. 確認メッセージで **[無効]** をクリックします。

## <a name="display-plugin-error"></a>プラグインエラーの表示

ポータルの開発中に発生することが多いもう1つのシナリオは、Common Data Service 環境に記述されたカスタムプラグインとビジネスロジックによって生成されるエラーです。 これらのエラーは、通常、[カスタムエラーを無効](#disable-custom-error)にするか、[診断ログを有効](#enable-diagnostic-logging)にすることによってアクセスできます。 ただし、場合によっては、これらのエラーをポータルに直接表示して、問題をより迅速に診断する方が高速です。 これを行うには、ポータル画面で Common Data Service からカスタムプラグインエラーを表示するようにポータルを構成します。

カスタムプラグインエラーを表示するには、`Site/EnableCustomPluginError` サイト設定を作成し、その値を True に設定します。 カスタムプラグインエラーは、一般的なエラーではなく画面に表示されます。 エラーには、完全なスタックトレースではなく、プラグインエラーのメッセージ部分のみが表示されます。

カスタムプラグインエラーが表示される画面を次に示します。 
- エンティティの一覧 
    - レコードの取得 
- エンティティフォーム 
    - Retrieve 
    - 作成/更新など 
- Web フォーム 
    - Retrieve 
    - 作成/更新など

サイト設定が存在しない場合、既定では false として扱われ、プラグインエラーは表示されません。
