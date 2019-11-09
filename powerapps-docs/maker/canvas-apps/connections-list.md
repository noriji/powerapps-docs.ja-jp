---
title: キャンバス アプリ用のコネクタの概要 | Microsoft Docs
description: キャンバス アプリの構築に使用できるすべての有効な接続の概要
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 08/28/2017
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 907ac3cf53709edd5a8b523479ec99816c6eec9c
ms.sourcegitcommit: 0f0b26122be28d674af0833247b491e9367c4932
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2019
ms.locfileid: "73897835"
---
# <a name="overview-of-canvas-app-connectors-for-powerapps"></a>PowerApps 用のキャンバス アプリ コネクタの概要
データは、PowerApps でビルドするものを含め、ほとんどのアプリの中核にあります。 *データ ソース*に格納されたデータは、*接続*を作成することでアプリに取り込まれます。 接続は特定の*コネクタ*を使用してデータ ソースと通信します。 PowerApps には SharePoint、SQL Server、Office 365、Salesforce、Twitter などの一般的なサービスやオンプレミスのデータ ソースのためのコネクタがあります。 キャンバス アプリへのデータの追加を開始するには、[PowerApps でのデータ接続の追加](add-data-connection.md)に関するページを参照してください。

コネクタから、データの**テーブル**または**アクション**が提供される場合があります。 コネクタの中には、テーブルのみを提供するもの、アクションのみを提供するもの、そして両方を提供するものがあります。 また、ご利用のコネクタは、標準コネクタのまたはカスタム コネクタのいずれかとなります。

## <a name="tables"></a>テーブル

ご利用のコネクタでテーブルが提供されている場合は、使用するテーブル ソースを追加してから、管理するデータ ソース内でテーブルを選択します。 PowerApps では、ご利用のアプリにテーブル データが取得されると共に、ご利用のデータ ソース内のデータが自動的に更新されます。 たとえば、**Lessons** という名前のテーブルが含まれているデータ ソースを追加してから、数式バー内でギャラリーやフォームなどのコントロールの **Items** プロパティを次の値に設定することができます。

 ![プレーン データ ソースの Items プロパティ](./media/connections-list/ItemPropertyPlain.png)

データを表示するコントロールの**Items**プロパティをカスタマイズすることで、アプリが取得するデータを指定できます。 前の例に続けて、**Lessons** テーブル内のデータを並べ替えまたはフィルター処理することができます。そのためには、その名前を、**Search** 関数および **SortByColumn** 関数で引数として使用します。 次の図において、**Items** プロパティが設定された数式では、**TextSearchBox1** 内のテキストに基づいてデータの並べ替えおよびフィルター処理を行うように指定されています。 

 ![拡張されたデータ ソースの Items プロパティ](./media/connections-list/ItemPropertyExpanded.png)

テーブルを使用して数式をカスタマイズする方法の詳細については、次のトピックを参照してください。

  [PowerApps のデータ ソースについて](working-with-data-sources.md)<br> 
  [Excel データからアプリを生成する](get-started-create-from-data.md)<br> 
  [アプリを最初から作成する](get-started-create-from-blank.md)<br>
  [PowerApps におけるテーブルとレコードについて](working-with-tables.md)

  > [!NOTE]
  > Excel データ内のデータに接続するには、そのブックを OneDrive のようなクラウド ストレージ サービスでホストする必要があります。 詳細については、「[クラウド ストレージ接続](connections/cloud-storage-blob-connections.md)」を参照してください。

## <a name="actions"></a>措置

ご利用のコネクタによってアクションが提供される場合も、前に行ったように使用するデータ ソースを選択する必要があります。 ただし、次の手順としては、テーブルを選択するのでなく、コントロールをアクションに手動で接続します。そのためには、ご利用のデータを表示するコントロールの **Items** プロパティを編集します。 **Items** プロパティを設定した数式では、データを取得するアクションが指定されています。 たとえば、Yammer に接続してから、**Items** プロパティをデータ ソースの名前に設定した場合、アプリによってデータは取得されません。 コントロールにデータを設定するには、**GetMessagesInGroup(5033622).messages** のようなアクションを指定します。

![アクション データ ソースの Items プロパティ](./media/connections-list/ItemPropertyAction.png)

アクション コネクタ用のカスタム データ更新プログラムに対処する必要がある場合は、**Patch** 関数を含む数式を作成します。 数式内で、アクションと、アクションにバインドするフィールドとを特定します。  

カスタム更新のために数式をカスタマイズする方法の詳細については、次のトピックを参照してください。

[Patch](functions/function-patch.md)<br>[Collect](functions/function-clear-collect-clearcollect.md)<br>[Update](functions/function-update-updateif.md)

> [!NOTE]
>  **PowerApps は動的スキーマでは機能しません**。 "動的スキーマ" とは、同じアクションが異なる列を持つ別のテーブルを返す可能性を意味します。 テーブル内の列が異なる可能性のある条件としては、アクションの入力パラメーター、アクションを実行しているユーザーまたはロール、およびユーザーが作業しているグループなどがあります。 たとえば、SQL Server のストアドプロシージャでは、異なる入力を使用して実行すると、異なる列が返される場合があります。 動的スキーマを使用するアクションの場合、コネクタのドキュメントは、**この操作の出力が動的**であることを示しています。 戻り値として。 これに対して、Power の自動化は動的スキーマを使用して機能し、シナリオの回避策を提供する場合があります。

## <a name="popular-connectors"></a>一般的なコネクタ

次の表には最も一般的なコネクタに関する詳細情報へのリンクが含まれています。 すべてのコネクタの一覧については、「[すべてのコネクタ](https://docs.microsoft.com/connectors/)」をご覧ください。

| &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; |
| --- | --- | --- | --- | --- |
| ![Common Data Service](./media/connections-list/cdm.png) |[**Common Data Service**](../common-data-service/data-platform-intro.md) |&nbsp; |![Office 365 Outlook](./media/connections-list/office365.png) |[**Office 365 Outlook**](connections/connection-office365-outlook.md) |
| ![SharePoint](./media/connections-list/sharepoint.png) |[**SharePoint**](connections/connection-sharepoint-online.md) |&nbsp; |![Excel](./media/connections-list/excel.png) |[**Excel**](connections/connection-excel.md) |
| ![SQL Server](./media/connections-list/sql.png) |[**SQL Server**](connections/connection-azure-sqldatabase.md) |&nbsp; |![OneDrive for Business](./media/connections-list/onedrive.png) |[**OneDrive for Business**](connections/cloud-storage-blob-connections.md) |
| ![Dynamics 365](./media/connections-list/dynamics-365.png) |[**Dynamics 365**](connections/connection-dynamics-crmonline.md) |&nbsp; |![OneDrive](./media/connections-list/onedrive.png) |[**OneDrive**](connections/cloud-storage-blob-connections.md) |
| ![Office 365 Users](./media/connections-list/office365.png) |[**Office 365 Users**](connections/connection-office365-users.md) |&nbsp; |![Dropbox](./media/connections-list/dropbox.png) |[**Dropbox**](connections/cloud-storage-blob-connections.md) |

## <a name="standard-and-custom-connectors"></a>標準コネクタとカスタム コネクタ
PowerApps では、上記に一覧したような一般的に使用されている多くのデータ ソース用に "*標準*" コネクタが提供されています。 使用するデータ ソースの種類に対して PowerApps から標準コネクタが提供されている場合は、そのコネクタを使用する必要があります。 自分で構築したサービスなど、別の種類のデータ ソースに接続する必要がある場合は、「[Microsoft Flow でカスタム コネクタを登録して使用する](../canvas-apps/register-custom-api.md)」を参照してください。

## <a name="all-standard-connectors"></a>すべての標準コネクタ
すべての標準コネクタの一覧については、[Microsoft Connector リファレンス](https://docs.microsoft.com/connectors/)に関するページを参照してください。 Premium コネクタを使用するには、PowerApps Plan 1 または Plan 2 が必要です。 詳細については、[PowerApps のプラン](https://powerapps.microsoft.com/pricing/)に関するページをご覧ください。

[PowerApps フォーラム](https://powerusers.microsoft.com/t5/PowerApps-Community/ct-p/PowerApps1)では特定のコネクタについて質問することができます。さらに [PowerApps のアイデア](https://powerusers.microsoft.com/t5/PowerApps-Ideas/idb-p/PowerAppsIdeas)に関するページでは、追加すべきコネクタまたは他の改善事項を提案することができます。
