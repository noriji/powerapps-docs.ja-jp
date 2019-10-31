---
title: ポータル エラー ログの表示と Azure Blob Storage への保存 | MicrosoftDocs
description: ポータル エラー ログの表示方法とそのエラー ログを Azure Blob Storage アカウントに保存する方法を説明します。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: null
ms.date: 07/18/2019
ms.author: shjais
ms.reviewer: null
---

# <a name="view-portal-error-logs"></a>ポータル エラー ログの表示

[!include[cc-beta-prerelease-disclaimer](../../../includes/cc-beta-prerelease-disclaimer.md)]

ポータル管理者または開発者は、PowerApps ポータルを使用して顧客の Web サイトを作成できます。 開発者の一般的なタスクは、ポータルの作成時に問題をデバッグすることです。 デバッグを助けるために、ポータルのすべての問題に関する詳細なエラー ログにアクセスできます。 ポータルのエラー ログは複数の方法で取得できます。

## <a name="custom-error"></a>カスタム エラー

ご使用のポータルでサーバー側の例外が発生すると、ユーザー フレンドリなエラー メッセージを含むカスタマイズしたエラー ページが既定で表示されます。 エラー メッセージを構成するには、[カスタム エラー メッセージの表示](#display-a-custom-error-message)を参照してください。

ただし、デバッグの目的の場合は、死のイエロー スクリーン (YSOD) とも呼ばれる、ASP.NET の詳細エラー ページを参照することをお勧めします。 この詳細エラー ページにより、フルスタックのサーバー エラーを取得することが容易になります。

> [!div class=mx-imgBorder]
> ![死のイエロー スクリーン](../media/ysod.png "死のイエロー スクリーン")

YSOD を有効にするには、ポータルでの [カスタム エラーを無効にする](#disable-custom-error)必要があります。

> [!NOTE]
> 開発フェーズにあるときだけカスタム エラーを無効にし、正式にサービスを開始した時点でカスタム エラーを有効にすることをお勧めします。

カスタム エラーの詳細: [カスタム エラー ページの表示](https://docs.microsoft.com/en-us/aspnet/web-forms/overview/older-versions-getting-started/deploying-web-site-projects/displaying-a-custom-error-page-cs)

### <a name="disable-custom-error"></a>カスタム エラーを無効にする

サーバー側で例外が発生した場合に詳細な例外メッセージを表示するように、ポータルでのカスタム エラーを無効にできます。

1. [PowerApps ポータル管理センター](admin-overview.md) を開きます。

2. **ポータル アクション** > **カスタム エラーを無効にする**に順に移動します。

   > [!div class=mx-imgBorder]
   > ![カスタム エラーを無効にする](../media/disable-custom-errors.png "カスタム エラーを無効にする")

3. 確認メッセージで、**無効にする**を選択します。 カスタム エラーの無効化の処理中は、ポータルは再起動しますが使用できません。 カスタム エラーが無効になると、メッセージが表示されます。

### <a name="enable-custom-error"></a>カスタム エラーを有効にする

ポータルでのカスタム エラーを有効にして、YSOD ではなく、プロフェッショナルなデザインのページを表示することができます。 このページは、アプリケーションで例外が発生した場合に、有益な情報を提供します。

1. [PowerApps ポータル管理センター](admin-overview.md) を開きます。

2. **ポータル アクション** > **カスタム エラーを有効にする**に順に移動します。

   > [!div class=mx-imgBorder]
   > ![カスタム エラーを有効にする](../media/enable-custom-errors.png "カスタム エラーを有効にする")

3. 確認メッセージで、**有効にする**を選択します。 カスタム エラーの有効化の処理中は、ポータルは再起動しますが使用できません。 カスタム エラーが有効になると、メッセージが表示されます。

> [!NOTE]
> - ポータルが接続されているインスタンスを変更した場合、カスタム エラーの設定が有効化に設定されます。 必要に応じて、カスタム エラーを再度無効にする必要があります。
> - ポータルが接続されているインスタンスの変更中にカスタム エラーを有効または無効にすることはできません。そうしなかった場合、エラー メッセージが表示されます。

### <a name="display-a-custom-error-message"></a>カスタム エラー メッセージの表示

ポータルを構成して、一般的なエラーではなく、プロフェッショナルなデザインのカスタム エラーを表示することができます。

カスタム エラーを定義するには、そのコンテンツ スニペット `Portal Generic Error` を使用します。 このスニペットに定義されたコンテンツがエラー ページに表示されます。 このコンテンツ スニペットはすぐには使用できません。作成する必要があります。 コンテンツ スニペットの**種類**には**テキスト**または **HTML** があります。 コンテンツ スニペットの作成または編集をするには、[コンテンツ スニペットを使用したコンテンツのカスタマイズ​​](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/portals/customize-content-snippets) を参照してください。

> [!NOTE]
> コンテンツ スニペットに流動コードが記述されている場合、その流体コードは表示されません。

カスタム エラーを有効にすると、エラー ページにメッセージが次の構造で表示されます。

<Content Snippet> 
<Error ID >
<Date and time>
<Portal ID>

以下に、HTML タイプのコンテンツ スニペットを使用した、カスタム エラー メッセージの例を示します。

これはカスタム エラーです。ここをクリックして、エラーのスクリーンショットの入ったサポート チケットを提出してください。

> [!div class=mx-imgBorder]
> ![カスタム エラー メッセージ](../media/custom-error-message.png "カスタム エラー メッセージ")

> [!NOTE]
> ポータルが Common Data Service に接続できないためにコンテンツ スニペットを取得できない場合、またはコンテンツ スニペットが Common Data Service で得られない場合、エラー メッセージが表示されます。

## <a name="access-portal-error-logs"></a>ポータル エラー ログへのアクセス

ポータルを開発して公開した後、顧客から報告された問題をデバッグするために、さらにポータル ログにアクセス可能にする必要があります。 ログにアクセスするには、所有する Azure Blob Storage アカウントにすべてのアプリケーション エラーを送信するように、ポータルを構成することができます。 ポータル エラー ログにアクセスすると、問題の詳細を把握できるので、顧客のクエリに効率的に対応できます。 ポータル エラー ログを Azure Blob Storage に入力するためには、ポータル管理センターからの診断ログを有効にする必要があります。

> [!NOTE]
> ポータルが接続されている Dynamics 365 インスタンスを変更した場合、診断ログが無効になります。 診断ログを再度有効にする必要があります。

### <a name="enable-diagnostic-logging"></a>診断ログを有効にする

1. [PowerApps ポータル管理センター](admin-overview.md) を開きます。

2. **ポータル アクション** > **診断ログを有効にする**に順に移動します。

   > [!div class=mx-imgBorder]
   > ![診断ログを有効にする](../media/enable-diagnostic-logging.png "診断ログを有効にする")

3. **診断ログを有効にする** ウィンドウで、次の値を入力します。

   - **Azure Blob Storage サービスの接続文字列**: ポータル エラー ログを格納する Azure Blob Storage サービスの URL。 この URL の長さの上限は 2048 文字です。 URL の長さが 2048 文字を超えると、エラー メッセージが表示されます。 接続文字列の詳細: [Azure Storage 接続文字列の構成](https://docs.microsoft.com/en-us/azure/storage/common/storage-configure-connection-string)
   - **保持期間の選択**: Blob Storage でポータル エラー ログを保持する期間。 エラー ログは選択した期間が経過すると削除されます。 次のいずれかの値を選択できます。
     - 1 日
     - 7 日間
     - 30 日間
     - 60 日間
     - 90 日間
     - 180 日間
     - 常時

   既定では、保持期間は 30 日です。
  
   > [!div class=mx-imgBorder]
   > ![診断ログを有効にするウィンドウ](../media/enable-diagnostic-logging-window.png "診断ログを有効にするウィンドウ")

4. **構成**をクリックします。

診断ログの構成が完了すると、新しい**テレメトリー ログ** Blob コンテナーが Azure Storage アカウントに作成され、ログがそのコンテナーに格納されている Blob ファイルに書き込まれます。 次のスクリーンショットは、Azure Storage Explorer の**テレメトリー ログ** Blob コンテナーを示しています。

> [!div class=mx-imgBorder]
> ![Azure Blob Storage アカウント](../media/azure-blob-storage.png "Azure Blob Storage アカウント")

診断ログが正常に有効になると、以下の操作が使用可能になります。
- **診断ログの構成の更新**: ポータルの診断ログの構成の更新または削除を可能にします。
- **診断ログを無効にする**: ポータルの診断ログの構成を無効にすることができます。
 
### <a name="update-diagnostic-logging"></a>診断ログの更新

1. [PowerApps ポータル管理センター](admin-overview.md) を開きます。

2. **ポータル アクション** > **診断ログの構成の更新**の順に進みます。

   > [!div class=mx-imgBorder]
   > ![診断ログの構成の更新](../media/update-diagnostic-logging.png "診断ログの構成の更新")

3. [診断ログの構成の更新] ウィンドウで、次の値を入力します。
   - **Azure Blob Storage サービスの接続文字列を更新しますか。**: Azure Blob Storage サービスの接続文字列を更新するかどうかを指定できます。 既定ではオンです。
   - **Azure Blob Storage サービスの接続文字列**: ポータル エラー ログを格納する Azure Blob Storage サービスの URL。 この URL の長さの上限は 2048 文字になります。 URL の長さが 2048 文字を超えると、エラー メッセージが表示されます。 このフィールドは、**Azure Blob Storage サービスの接続文字列を更新しますか。** チェック ボックスがオンになっている場合にのみ表示されます。 接続文字列の詳細: [Azure Storage 接続文字列の構成](https://docs.microsoft.com/en-us/azure/storage/common/storage-configure-connection-string)
   - **保持期間の選択**: Blob Storage でポータル エラー ログを保持する期間。 エラー ログは選択した期間が経過すると削除されます。 次のいずれかの値を選択できます。
     - 1 日
     - 7 日間
     - 30 日間
     - 60 日間
     - 90 日間
     - 180 日間
     - 常時

   既定では、保持期間は 30 日です。

   > [!div class=mx-imgBorder]
   > ![診断ログの構成の更新ウィンドウ](../media/update-diagnostic-logging-window.png "診断ログの構成の更新ウィンドウ")

4. **更新**をクリックします。

### <a name="disable-diagnostic-logging"></a>診断ログを無効にする

1. [PowerApps ポータル管理センター](admin-overview.md) を開きます。

2. **ポータル アクション** > **診断ログを無効にする**に順に移動します。

   > [!div class=mx-imgBorder]
   > ![診断ログを無効にする](../media/disable-diagnostic-logging.png "診断ログを無効にする")

3. 確認メッセージで、**無効にする**をクリックします。

## <a name="display-plugin-error"></a>プラグイン エラーの表示

ポータルの開発中によく発生するもう 1 つのシナリオは、Dynamics 365 組織で記述されたカスタムのプラグインおよびビジネス ロジックによって生成されるエラーです。 通常、これらのエラーには、[カスタム エラーを無効にする](#disable-custom-error)または[診断ログを有効にする](#enable-diagnostic-logging)でアクセスできます。 ただし、問題を素早く診断するには、これらのエラーをポータルに直接表示することがより速い場合があります。 これを行うために、カスタム プラグイン エラーをポータルのスクリーンに表示するようにポータルを設定できます。

カスタム プラグイン エラーを表示するには、サイト設定 `Site/EnableCustomPluginError` を作成し、その値を True に設定します。 一般的なエラーではなく、カスタム プラグイン エラーが画面に表示されます。 このエラーは、完全なスタック トレースではなく、プラグイン エラーのメッセージ部分のみを表示します。

以下に、カスタム プラグイン エラーが表示される画面を示します。 
- エンティティ リスト 
    - レコードの取得 
- エンティティ フォーム 
    - 取得 
    - 作成/更新など 
- Web フォーム 
    - 取得 
    - 作成/更新など

サイト設定が存在しない場合は、既定でサイト設定は false として扱われ、プラグイン エラーは表示されません。
