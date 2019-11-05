---
title: SQL Server の接続の概要 | Microsoft Docs
description: Azure SQL またはオンプレミス SQL Server データベースに接続するための操作手順
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.date: 07/12/2016
ms.author: lanced
ms.reviewer: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: bcadf4abfd55a317cf67196c9ba2158a001a015a
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2019
ms.locfileid: "73541132"
---
# <a name="connect-to-sql-server-from-powerapps"></a>PowerApps から SQL Server に接続する
![SQL Server アイコン](./media/connection-azure-sqldatabase/sqlicon.png)

Azure またはオンプレミス データベースで SQL Server に接続し、PowerApps でそこから情報を表示できるようにします。

## <a name="prerequisites"></a>前提条件

* PowerApps に[サインアップ](../../signup-for-powerapps.md)し、サインアップに使用したのと同じ資格情報を入力して[サインイン](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)します。
* 主キーを持つテーブルが 1 つ以上含まれるデータベースに関して次の情報を集めます。
  
  * データベースの名前
  * データベースがホストされているサーバーの名前
  * データベースに接続するための有効なユーザー名/パスワード
  * データベースへの接続に必要な認証の種類
    
    この情報がない場合、使用するデータベースの管理者にお問い合わせください。
* オンプレミス データベースの場合、自分と共有された[データ ゲートウェイ](../gateway-management.md)を特定します (あるいはデータ ゲートウェイを作成します)。
  
    > [!NOTE]
  > ゲートウェイとオンプレミス接続は、ユーザーの[既定の環境](../working-with-environments.md)でのみ作成し、使用できます。

## <a name="generate-an-app-automatically"></a>アプリを自動的に生成する
1. PowerApps Studio の **[ファイル]** メニュー (画面左側) の **[新規]** をクリックまたはタップします。
   
    ![[ファイル] メニューの [新規] オプション](./media/connection-azure-sqldatabase/file-new.png)
2. **[データを使用して開始]** で、コネクタの行端にある右矢印をクリックまたはタップします。
3. 使用するデータベースへの接続が既に与えられている場合、それをクリックまたはタップし、手順 7 に進んでください。
4. **[新しい接続]** をクリックまたはタップし、 **[SQL Server]** をクリックまたはタップします。
   
    ![SQL Server 接続を追加する](./media/connection-azure-sqldatabase/add-sql-connection.png)
5. 次の手順のいずれかを実行します。
   
   * **[直接接続 (クラウド サービス)]** を指定し、サーバー名、データベース名、ユーザー名、使用するデータベースのパスワードを入力するか、貼り付けます。
     
       ![Azure のデータベースに接続する](./media/connection-azure-sqldatabase/connect-azure.png)
   * **[オンプレミス データ ゲートウェイを使用する接続]** を指定し、サーバー名、データベース名、ユーザー名、使用するデータベースのパスワードを入力するか貼り付けて、認証の種類とゲートウェイを指定します。
     
       ![オンプレミス データベースに接続する](./media/connection-azure-sqldatabase/connect-onprem.png)
     
       > [!NOTE]
     > ゲートウェイがない場合、[ゲートウェイをインストール](../gateway-reference.md)し、 **[ゲートウェイ一覧を最新の情報に更新]** をクリックまたはタップします。
6. **[接続]** をクリックまたはタップします。
7. **[データセットの選択]** のオプションをクリックまたはタップし、 **[テーブルの選択]** のオプションをクリックまたはタップし、 **[接続]** をクリックまたはタップします。
   
    PowerApps により、3 つの画面にデータを表示するアプリが作成されます。 ヒューリスティックスにより表示するデータの種類が提案されますが、場合によっては、自分のニーズに合わせて UI をカスタマイズする必要があります。
8. アプリのカスタマイズは、「[Create an app from Excel](../get-started-create-from-data.md)」 (Excel からアプリを作成する) にある説明と同様の手法で行います。最初にアプリのレイアウトを変更します。

## <a name="build-an-app-from-scratch"></a>アプリをゼロから作成
1. PowerApps のサインアップに使用したものと同じアカウントで [powerapps.com](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) にサインインします。
2. 左側のナビゲーション バーで、 **[接続]** をクリックまたはタップします。  
   
    ![接続を管理する](./media/connection-azure-sqldatabase/manage-connections.png)
3. 右上隅で **[新しい接続]** をクリックまたはタップし、 **[SQL Server]** をクリックまたはタップします。
4. 次の手順のいずれかを実行します。
   
   * **[直接接続 (クラウド サービス)]** を指定し、サーバー名、データベース名、ユーザー名、使用するデータベースのパスワードを入力するか、貼り付けます。
     
       ![Azure のデータベースに接続する](./media/connection-azure-sqldatabase/connect-azure-portal.png)
   * **[オンプレミス データ ゲートウェイを使用する接続]** を指定し、サーバー名、データベース名、ユーザー名、使用するデータベースのパスワードを入力するか貼り付けて、認証の種類とゲートウェイを指定します。
     
       ![Azure のデータベースに接続する](./media/connection-azure-sqldatabase/connect-onprem-portal.png)
     
       > [!NOTE]
     > ゲートウェイがない場合、[ゲートウェイをインストール](../gateway-reference.md)し、時計回りアイコンをクリックまたはタップし、一覧を更新します。
5. **[作成]** をクリックまたはタップして接続を作成します。
6. 「[アプリをゼロから作成](../get-started-create-from-blank.md)」の説明と同様の手法でアプリを作成します。

## <a name="update-an-existing-app"></a>既存のアプリを更新する
1. PowerApps Studio で、更新するアプリを開きます。
2. リボンの **[ビュー]** タブで、 **[データ ソース]** をクリックまたはタップします。
3. 右側のウィンドウで、 **[データ ソースの追加]** をクリックまたはタップします。
   
    ![データ ソースの追加](./media/connection-azure-sqldatabase/add-data-source.png)
4. **[新しい接続]** をクリックまたはタップし、 **[SQL Server]** をクリックまたはタップし、 **[接続]** をクリックまたはタップします。
5. 次の手順のいずれかを実行します。
   
   * **[直接接続 (クラウド サービス)]** を指定し、サーバー名、データベース名、ユーザー名、使用するデータベースのパスワードを入力するか、貼り付けます。
     
       ![Azure のデータベースに接続する](./media/connection-azure-sqldatabase/connect-azure-fromblank.png)
   * **[オンプレミス データ ゲートウェイを使用する接続]** を指定し、サーバー名、データベース名、ユーザー名、使用するデータベースのパスワードを入力するか貼り付けて、認証の種類とゲートウェイを指定します。
     
       ![Azure のデータベースに接続する](./media/connection-azure-sqldatabase/connect-onprem-fromblank.png)
     
       > [!NOTE]
     > ゲートウェイがない場合、[ゲートウェイをインストール](../gateway-reference.md)し、円アイコンをクリックまたはタップし、一覧を更新します。
6. **[接続]** をクリックまたはタップします。
7. **[データセットの選択]** で、オプションをクリックまたはタップします。
8. **[テーブルの選択]** で 1 つまたは複数のチェック ボックスをオンにし、 **[接続]** をクリックまたはタップします。

## <a name="next-steps"></a>次の手順
* [データ ソースからデータを表示する方法](../add-gallery.md)を学習する。
* [詳細を表示する方法とレコードを作成または更新する方法](../add-form.md)を学習する。
* 接続できる他の種類の[データ ソース](../connections-list.md)を確認する。  
* 表形式のデータ ソースの[表とレコードを理解する](../working-with-tables.md)。

<!--NotAvailableYet
## View the available functions ##
This connection includes the following functions:

| Function Name |  Description |
| --- | --- |
|[GetItems](connection-azure-sqldatabase.md#getitems) | Retrieves rows from a SQL table |
|[PostItem](connection-azure-sqldatabase.md#postitem) | Inserts a new row into a SQL table |
|[GetItem](connection-azure-sqldatabase.md#getitem) | Retrieves a single row from a SQL table |
|[DeleteItem](connection-azure-sqldatabase.md#deleteitem) | Deletes a row from a SQL table |
|[PatchItem](connection-azure-sqldatabase.md#patchitem) | Updates an existing row in a SQL table |
|[GetTables](connection-azure-sqldatabase.md#gettables) | Retrieves tables from a SQL database |

### GetItems
Get rows: Retrieves rows from a SQL table

#### Input properties

| Name| Data Type|Required|Description|
| ---|---|---|---|
|table|string|yes|Name of SQL table|
|$skip|integer|no|Number of entries to skip (default = 0)|
|$top|integer|no|Maximum number of entries to retrieve (default = 256)|
|$filter|string|no|An ODATA filter query to restrict the number of entries|
|$orderby|string|no|An ODATA orderBy query for specifying the order of entries|

### PostItem
Insert row: Inserts a new row into a SQL table

#### Input properties

| Name| Data Type|Required|Description|
| ---|---|---|---|
|table|string|yes|Name of SQL table|
|item| |yes|Row to insert into the specified table in SQL|

#### Output properties

| Property Name | Data Type | Required | Description |
|---|---|---|---|
|value|array|No | |


### GetItem
Get row: Retrieves a single row from a SQL table

#### Input properties

| Name| Data Type|Required|Description|
| ---|---|---|---|
|table|string|yes|Name of SQL table|
|id|string|yes|Unique identifier of the row to retrieve|

#### Output properties

| Property Name | Data Type | Required | Description |
|---|---|---|---|
|ItemInternalId|string|No | |


### DeleteItem
Delete row: Deletes a row from a SQL table

#### Input properties

| Name| Data Type|Required|Description|
| ---|---|---|---|
|table|string|yes|Name of SQL table|
|id|string|yes|Unique identifier of the row to delete|

#### Output properties
None.

### PatchItem
Update row: Updates an existing row in a SQL table

#### Input properties

| Name| Data Type|Required|Description|
| ---|---|---|---|
|table|string|yes|Name of SQL table|
|id|string|yes|Unique identifier of the row to update|
|item| |yes|Row with updated values|

#### Output properties

| Property Name | Data Type | Required | Description |
|---|---|---|---|
|ItemInternalId|string|No | &nbsp; |


### GetTables
Get tables: Retrieves tables from a SQL database

#### Input properties
None.

#### Output properties

| Property Name | Data Type | Required | Description |
|---|---|---|---|
|value|array|No | Can output the Name and DisplayName properties |

### ExecuteProcedure
Execute stored procedure: Executes a stored procedure in SQL

#### Input properties

| Name| Data Type|Required|Description|
| ---|---|---|---|
|procedure|string|yes|Procedure name|
|parameters| |yes|Input parameters|

#### Output properties
Result of the stored procedure execution.

| Property Name | Data Type | Required | Description |
|---|---|---|---|
|OutputParameters|object|No | Output parameter values |
|ReturnCode|integer|No | Return code of a procedure |
|ResultSets|object|No | Result sets|

-->
