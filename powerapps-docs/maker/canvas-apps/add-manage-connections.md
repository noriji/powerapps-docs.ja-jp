---
title: キャンバス アプリからの接続を追加および管理する | Microsoft Docs
description: キャンバス アプリからデータ ソース (SharePoint、SQL Server、OneDrive for Business など) への接続を追加、削除、更新する
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 03/09/2017
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: e8f40f9cd3b15dddfd9fdadbcd15495e33464967
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2019
ms.locfileid: "73540909"
---
# <a name="manage-canvas-app-connections-in-powerapps"></a>PowerApps でキャンバス アプリの接続を管理する
[powerapps.com](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) で、1 つまたは複数のデータ ソースへの接続を作成したり、接続を削除したり、接続の資格情報を更新したりします。

ご利用のキャンバス アプリのデータ接続では、SharePoint、SQL Server、Office 365、OneDrive for Business、Salesforce、Excel などの多くの[データ ソース](connections-list.md)に接続できます。

この記事の後の次のステップは、以下の例のように、データ ソースのデータをアプリで表示し、管理することです。

* OneDrive for Business に接続し、アプリで Excel ブックのデータを管理する。
* SharePoint サイトにあるリストを更新する。
* SQL Server に接続し、アプリからテーブルを更新する。
* Office 365 で電子メールを送信する。
* ツイートを送信する。
* Twilio に接続し、アプリから SMS メッセージを送信する。

## <a name="prerequisites"></a>前提条件
1. PowerApps に[サインアップ](../signup-for-powerapps.md)。
2. サインアップに使用した資格情報で [powerapps.com](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) にサインインします。

## <a name="background-on-data-connections"></a>データ接続の背景
ほとんどの PowerApps アプリでは、クラウド サービスに格納されている**データ ソース**と呼ばれる外部情報を使用します。 一般的な例は、OneDrive for Business に格納されている Excel ファイル内のテーブルです。 これらのデータ ソースには、アプリから**接続**を使用してアクセスできます。

最も一般的なデータ ソースの種類はテーブルで、情報の取得および保存に使用できます。 データ ソースへの接続を使用すると、Microsoft Excel ブック、SharePoint リスト、SQL テーブル、およびその他の多くの形式でデータの読み書きを行うことができ、それらを OneDrive for Business、DropBox、SQL Server などのクラウド サービスに格納できます。

電子メール、カレンダー、twitter、通知など、テーブル以外の種類のデータソースもあります。

**[ギャラリー](controls/control-gallery.md)** 、 **[フォームの表示](controls/control-form-detail.md)** 、および **[フォームの編集](controls/control-form-detail.md)** コントロールを使用すると、データ ソースからデータを読み書きするアプリを簡単に作成できます。 最初に、[データ フォームについて](working-with-forms.md)の記事をご覧ください。

[powerapps.com](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) で接続を作成し、管理するだけでなく、次のようなタスクを実行した場合にも接続を作成できます。

* カスタム SharePoint リストなど、[データからのアプリ](app-from-sharepoint.md)を自動的に生成します。
* [接続の追加](add-data-connection.md)に関するページの手順に従って、既存のアプリを更新するかアプリを最初から作成する。
* 別のユーザーが作成したアプリを開き、[自分と共有する](share-app.md)。

> [!NOTE]
> 代わりに PowerApps Studio を使用する場合は、 **[ファイル]** メニューを開き、 **[接続]** をクリックまたはタップすると、[powerapps.com](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) が開くので、そこで接続の作成と管理を行うことができます。

## <a name="create-a-new-connection"></a>新しい接続を作成する
1. [powerapps.com](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) にまだログインしていない場合は、ログインします。
2. 左側のナビゲーション バーで、 **[接続]** をクリックまたはタップします。
   
    ![接続の管理](./media/add-manage-connections/open-connections.png)
3. 右上隅にある **[新しい接続]** をクリックまたはタップします。
   
    ![接続追加](./media/add-manage-connections/add-connection.png)
4. 表示された一覧からコネクタをクリックまたはタップして、画面の指示に従います。
   
   ![接続追加](./media/add-manage-connections/choose-connection.png)
5. **[作成]** ボタンをクリックまたはタップします。
   
   ![接続追加](./media/add-manage-connections/create-connection.png)
6. 画面の指示に従います。 コネクタによっては、資格情報の入力や特定のデータ セットの指定などの手順の実行が要求されることがあります。 **Microsoft Translator** などでは要求されません。
   
   たとえば、次のコネクタでは、使用する前に追加情報の入力を求められます。
   
   * [SharePoint](connections/connection-sharepoint-online.md)
   * [SQL Server](connections/connection-azure-sqldatabase.md)

新しいコネクタが **[Connections (接続)]** に表示され、[アプリに追加](add-data-connection.md)できるようになります。

## <a name="update-or-delete-a-connection"></a>接続の更新または削除
接続の一覧で、更新または削除する接続を見つけて、接続の右側にある省略記号 (3 ドット記号) をクリックまたはタップします。

![接続の更新](./media/add-manage-connections/auth-or-delete.png)

* 接続の資格情報を更新するには、キー アイコンをクリックまたはタップし、その接続の資格情報を入力します。
* 接続を削除するには、ごみ箱アイコンをクリックまたはタップします。
* 情報アイコンをクリックまたはタップすると、接続の詳細が表示されます。

