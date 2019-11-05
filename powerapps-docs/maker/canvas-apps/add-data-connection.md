---
title: キャンバス アプリへのデータ接続の追加 | Microsoft Docs
description: 既存のキャンバス アプリや空のアプリにデータ接続を追加できます
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 04/06/2018
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 420728d60555c3aeaf5fd5e844a900d412b0c3ef
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2019
ms.locfileid: "73540963"
---
# <a name="add-a-data-connection-to-a-canvas-app-in-powerapps"></a>PowerApps でキャンバス アプリにデータ接続を追加する

PowerApps で、既存のキャンバス アプリまたはゼロから作成するアプリにデータ接続を追加します。 アプリは、SharePoint、Common Data Service、Salesforce、OneDrive など、[他の多くのデータソース](connections-list.md)に接続できます。

この記事の後に来る[次のステップ](#next-steps)は、以下に示す例のように、接続したデータ ソースのデータをアプリで表示および管理することです。

* OneDrive に接続し、アプリ内で Excel ブックのデータを管理する。
* Twilio に接続し、アプリから SMS メッセージを送信する。
* Common Data Service に接続し、アプリからエンティティを更新します。
* SQL Server に接続し、アプリからテーブルを更新する。

## <a name="prerequisites"></a>前提条件

PowerApps に[サインアップ](../signup-for-powerapps.md)し、サインアップに使用したのと同じ資格情報を入力して[サインイン](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)します。

## <a name="open-a-blank-app"></a>空のアプリを開く

1. **[ホーム]** タブで、 **[キャンバスアプリを空白から]** を選択します。

1. アプリの名前を指定し、 **[作成]** を選択します。

1. **[PowerApps Studio へようこそ]** ダイアログ ボックスが表示されたら、 **[スキップ]** を選択します。

## <a name="add-data-source"></a>データ ソースの追加

1. 中央のペインで、 **[データに接続]** を選択して**データ**ペインを開きます。

    これが既存のアプリで、画面に既にコントロールが含まれている場合は、[**データソース**の > **表示**] を選択して同じウィンドウを開きます。

1. **[データソースの追加]** を選択します。

1. 接続の一覧に必要なものが含まれている場合は、それを選択してアプリに追加します。 それ以外の場合、次のステップに進んでください。

    ![既存の接続を選択する](./media/add-data-connection/choose-existing-connection.png)

1. **[新しい接続]** を選択して、接続の一覧を表示します。

    ![接続の追加](./media/add-data-connection/add-connection.png)

1. 検索バーで、接続の最初の数文字を入力するか貼り付けてから、接続が表示されたらそれを選択します。

    ![接続の検索](./media/add-data-connection/search-connections.png)

1. **[作成]** を選択して、接続の作成とアプリへの追加の両方を行います。

    **Office 365 Outlook** などのコネクタでは、追加の手順を実行しなくても、すぐにデータを表示できます。 コネクタによっては、資格情報の入力や、特定のデータ セットの指定などの手順が要求されることがあります。 たとえば、[SharePoint](connections/connection-sharepoint-online.md) と [SQL Server](connections/connection-azure-sqldatabase.md) では、使用する前に追加情報の入力を求められます。 [Common Data Service](connections/connection-common-data-service.md)では、エンティティを選択する前に環境を変更できます。

## <a name="identify-or-change-a-data-source"></a>データ ソースの特定または変更
アプリを更新する際、ギャラリー、フォーム、または別のコントロールに表示されるデータ ソースを特定または変更する必要があることがあります。 たとえば、他のユーザーが作成したアプリや、前に作成したアプリを更新するときに、データソースを識別する必要がある場合があります。

1. データソースを特定または変更するギャラリーなどのコントロールを選択します。

    右側のウィンドウの **[プロパティ]** タブにデータ ソース名が表示されます。

    ![接続の識別](./media/add-data-connection/identify-connection.png)

1. データソースに関する詳細情報を表示したり、データソースを変更したりするには、名前の横にある下矢印を選択します。

    現在のデータソースに関する詳細情報が表示され、別のソースを選択または作成できます。

    ![接続の変更](./media/add-data-connection/change-connection.png)

## <a name="next-steps"></a>次の手順

* Excel、SharePoint、Common Data Service、SQL Server などのソースのデータを表示および更新するには、[ギャラリーを追加](add-gallery.md)し、[フォームを追加](add-form.md)します。
* [Office 365 Outlook](connections/connection-office365-outlook.md)、[Twitter](connections/connection-twitter.md)、[Microsoft Translator](connections/connection-microsoft-translator.md) などのソースの場合は、各コネクタに用意された機能を使用して表示や更新を行います。
