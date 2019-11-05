---
title: ポータルでの Azure storage の有効化 |MicrosoftDocs
description: Azure のより大きなファイルストレージ機能を利用するために、ポータルで Azure storage を有効にする方法について説明します。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 3da40cfdcb88726384218c4b1df370c301f8ac16
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2019
ms.locfileid: "73542561"
---
# <a name="enable-azure-storage"></a>Azure Storage を有効にする

ポータルの Azure Storage 統合により、同じインターフェイスを使用し、既定の添付ファイルの場合と同じユーザーエクスペリエンスを提供することで、Azure のより大きなファイルストレージ機能を利用できます。 この機能は、web ファイル、エンティティフォーム、および web フォームに対してサポートされています。

デプロイモデルとして**Resource manager**を使用してストレージアカウントを作成する必要があります。 [Azure ストレージアカウントを作成](https://docs.microsoft.com/azure/storage/storage-create-storage-account#create-a-storage-account)[!include[More information](../../includes/proc-more-information.md)] ます。

ストレージアカウントを実行した後、ポータルには、ストレージアカウントの検索方法をアプリケーションに伝える特定のグローバル設定が必要です。 ポータル管理アプリで、 **[設定]** **[新規作成]** の順に > 、 **[Filestorage/cloudstorageaccount]** という名前の新しい設定を追加します。

> [!NOTE]
> ファイルの最大アップロードサイズは 125 MB です。

FileStorage/CloudStorageAccount の値を検索するには、[!include[Azure portal](../../includes/pn-azure-portal.md)]から接続文字列を取得する必要があります。

1. [!include[Azure portal](../../includes/pn-azure-portal.md)]にサインインします。

2. ストレージアカウントに移動します。

3. **[アクセスキー]** を選択します。

    ![Azure portal から接続文字列の値を探します](media/key-azure-storage.png "Azure portal から接続文字列の値を探します。")

4. 結果のパネルで、 **[接続文字列]** というラベルの付いたフィールドを見つけます。 値をコピーする必要があるフィールドの横にある**コピー**アイコンを選択し、その値を新しい設定に貼り付けます。

    ![プライマリ接続文字列値](media/primary-connection-string-azure-storage.png "プライマリ接続文字列値")

    ![クラウドストレージアカウントのポータル設定](media/portal-site-setting-cloud-storage-account.png "クラウドストレージアカウントのポータル設定")

## <a name="specify-the-storage-container"></a>ストレージコンテナーを指定する

ストレージアカウントに Azure Blob コンテナーがまだない場合は、[!include[Azure portal](../../includes/pn-azure-portal.md)]を使用して追加する必要があります。

[ポータル管理アプリ](configure/configure-portal.md)で、 **[設定]** **[新規作成]** の順に > 、コンテナーの名前を値として使用して、" **filestorage/CloudStorageContainerName**" という名前の新しい設定を追加します。

![クラウドストレージコンテナーのポータル設定](media/portal-site-setting-cloud-storage-container.png "クラウドストレージコンテナーのポータル設定")

## <a name="add-cors-rule"></a>CORS ルールの追加

次のように、Azure Storage アカウントにクロスオリジンリソース共有 (CORS) ルールを追加する必要があります。そうしないと、クラウドアイコンではなく通常の添付ファイルアイコンが表示されます。

- **許可されるオリジン**: ドメインを指定します。 たとえば、contoso.crm.dynamics.com のようになります。
- **許可される動詞**: GET、PUT、DELETE、HEAD、POST
- **許可されるヘッダー**: 元のドメインが CORS 要求に指定できる要求ヘッダーを指定します。 たとえば、"x-ms-メタデータ\*"、"x--メタターゲット\*" などです。 
- **公開**されるヘッダー: CORS 要求への応答で送信され、ブラウザーによって要求の発行者に公開される応答ヘッダーを指定します。 たとえば、「\*のようになります。
- **最大有効期間 (秒)** : ブラウザーがプレフライトオプション要求をキャッシュする最大時間を指定します。 たとえば、200のようになります。
 
[Azure Storage サービスの CORS サポートの](https://docs.microsoft.com/rest/api/storageservices/cross-origin-resource-sharing--cors--support-for-the-azure-storage-services)[!include[More information:](../../includes/proc-more-information.md)]

## <a name="add-site-settings"></a>サイト設定の追加

**ポータル** > **サイト設定**から、次のサイト設定を追加します。 [ポータルサイト設定を管理](configure/configure-site-settings.md#manage-portal-site-settings)[!include[More information:](../../includes/proc-more-information.md)] ます。

|名前|Value|
|-----|-----|
|WebFiles/CloudStorageAccount|FileStorage/CloudStorageAccount 設定に指定されているものと同じ接続文字列を指定してください。|
|WebFiles/StorageLocation|AzureBlobStorage|
|||

ポータルで子ファイルを作成し、Azure Blob アドレス URL に完全修飾名 (コンテナーと共に) を記述できるようになりました。 これらの設定を使用すると、ポータルで Azure Storage との間でファイルのアップロードとダウンロードを開始できます。 ただし、 [Azure Storage への添付ファイルのアップロードを有効にするために web リソースを追加](add-web-resource.md)し、それを使用するように[エンティティフォーム](configure-notes.md#notes-configuration-for-entity-forms)または[web フォーム](configure-notes.md#notes-configuration-for-web-forms)を構成するまで、この機能を最大限に活用することはできません。

### <a name="see-also"></a>関連項目

[Web リソースの追加](add-web-resource.md)

[メモの構成](configure-notes.md)
