---
title: Azure storage web リソースをフォームに追加する |MicrosoftDocs
description: Azure storage web リソースをフォームに追加して、Azure Storage への添付ファイルのアップロードを有効にする手順について説明します。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: c735513bc0a8f325aaf0debca2170131d45178dc
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2019
ms.locfileid: "73543125"
---
# <a name="add-the-azure-storage-web-resource-to-a-form"></a>Azure Storage Web リソースをフォームに追加する

Common Data Service に直接アップロードするのではなく Azure Storage にアップロードされた添付ファイルは Common Data Service でメモを使用して管理できます。

特定のフォームからの添付ファイルを Azure Storage にアップロードできるようにするには、そのフォームに web リソースを追加し、[組織の Azure Storage を構成](enable-azure-storage.md)する必要があります。

> [!Note]
> この例では、フォームが潜在顧客エンティティの潜在顧客フォームに追加されます。 既存のフォームを編集する場合は注意が必要です。

ポータルを使用してファイル (たとえば、.zip) を Azure Storage にアップロードすると、エンティティのメモと添付ファイルのプレースホルダーが表示されます。

![フォーム上の添付ファイル](media/notes-attachment-lead-form.png "フォーム上の添付ファイルのプレースホルダー")

添付ファイルが .zip という名前になっていることに注意してください。 既定では、Common Data Service には Azure ファイルの構想がないため、このプレースホルダー .txt ファイルは Common Data Service に格納されます。 プレースホルダーファイルの Azure Storage コンテキストには、ファイルの詳細が表示されます。
```
{
 Name: attachment.zip,
 Type: application/x-zip-compressed,
 Size: 24890882,
 "Url": "https://accountname.blob.core.windows.net/storage/81a9a9491c36e51182760026833bcf82/attachment.zip"
}
```

Azure に格納されているファイルを表示して操作するには、web リソース adx. annotations .html をフォームに追加する必要があります。 前提条件として、ユーザーが adx_setting に対する読み取りアクセス権を持っていることを確認します。 そうしないと、web リソースが正しく表示されません。

1. 関連するフォームのフォームエディターで、 **[挿入]** タブの **[Web リソース]** を選択します。

2. **[Web リソース]** ボックスで、 **[adx_annotations]** を選択します。

3. リソースの名前とラベルを入力します。

4. **[カスタムパラメーター (データ)]** ボックスに、「 **azureenabled = true**」と入力します。 <br>この方法では、Azure のサポートを有効にせずに web リソースを使用することもできます。この場合、ほぼ完全に既定のコントロールと同様に機能します。</br>

5. **[書式設定]** タブで、任意の書式設定規則を選択します。 **[境界線の表示]** チェックボックスをオフにすることをお勧めします。

6. [ **OK]** を選択してリソースを保存します。

7. 必要に応じて、既存のメモコントロールを削除したり、既定で非表示に設定されているタブやセクションに移動したりすることもできます。

8. フォームを保存し、変更を発行します。

   ![Web リソースの追加](media/add-web-resource.png "Web リソースの追加")

新しいコントロールがページに表示されるようになり、Azure Storage で添付ファイルを管理できるようになります。

![フォーム上の Azure ファイル添付ファイル](media/azure-file-attachment-lead-form.png "フォーム上の Azure ファイル添付ファイル")

このファイルが Azure Storage に格納されていることを示すために、ペーパークリップアイコンがクラウドアイコンに置き換えられました。 添付ファイルは引き続き Common Data Service に保存できます。これらのファイルは、ペーパークリップアイコンで示されます。

> [!Note]
> 次のように、Azure Storage アカウントにクロスオリジンリソース共有 (CORS) ルールを追加する必要があります。そうしないと、クラウドアイコンではなく通常の添付ファイルアイコンが表示されます。
> - **許可されるオリジン**: ドメインを指定します。 たとえば、contoso.crm.dynamics.com のようになります。
> - **許可される動詞**: GET、PUT、DELETE、HEAD、POST
> - **許可されるヘッダー**: 元のドメインが CORS 要求に指定できる要求ヘッダーを指定します。 たとえば、"x-ms-メタデータ\*"、"x--メタターゲット\*" などです。 このシナリオでは、* を指定する必要があります。そうしないと、web リソースが正しく表示されません。
> - **公開**されるヘッダー: CORS 要求への応答で送信され、ブラウザーによって要求の発行者に公開される応答ヘッダーを指定します。 たとえば、「\*のようになります。
> - **最大有効期間 (秒)** : ブラウザーがプレフライトオプション要求をキャッシュする最大時間を指定します。 たとえば、200のようになります。
> 
> [Azure Storage サービスの CORS サポートを](https://docs.microsoft.com/rest/api/storageservices/cross-origin-resource-sharing--cors--support-for-the-azure-storage-services)[!include[More information](../../includes/proc-more-information.md)] します。

添付ファイルが画像の場合、コントロールは Common Data Service または Azure Storage に格納されているかどうかをサムネイルとして表示します。

> [!Note]
> サムネイル機能は、サイズが 1 MB 未満のイメージに制限されています。

![メモのサムネイル](media/notes-thumbnail.png "メモのサムネイル")

## <a name="cors-protocol-support"></a>CORS プロトコルのサポート

[クロスオリジンリソース共有 (CORS)](https://www.w3.org/TR/cors/)プロトコルは、応答を別のドメインと共有できるかどうかを示す一連のヘッダーで構成されます。
CORS を構成するには、次のサイト設定を使用します。

|                 名前                  |                                                                            Description                                                                            |
|---------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| HTTP/Access-Allow-Credentials | このヘッダーの有効な値は true (大文字と小文字が区別されます) です。 資格情報が不要な場合は、このヘッダーを完全に省略します (値を false に設定するのではなく)。 |
|   HTTP/アクセス制御-ヘッダー   |                                                   サポートされている HTTP 要求ヘッダーのコンマ区切りの一覧。                                                   |
|   HTTP/アクセス制御メソッド   |                                      GET、POST、OPTIONS など、許可されている HTTP 要求メソッドのコンマ区切りのリスト。                                       |
|   HTTP/アクセス制御-オリジン    |                   リソースにアクセスできるようにするには、\*を指定します。 それ以外の場合は、リソースにアクセスできる URI を指定します。                   |
|  HTTP/アクセス制御-ヘッダー   |                リソースが使用して公開できる単純な応答ヘッダー以外の、HTTP ヘッダー名のコンマ区切りのリスト。                 |
|      HTTP/Access Control-最長有効期間      |                                                       結果をキャッシュできる最大秒数。                                                        |
|                                       |                                                                                                                                                                   |

