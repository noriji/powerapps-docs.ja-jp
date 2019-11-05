---
title: Choices 関数 | Microsoft Docs
description: 構文を含む PowerApps の Choices 関数の参照情報
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 06/15/2018
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: c9b84a8ce89863d94b9f3e4ac390c88e194a2894
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2019
ms.locfileid: "73540190"
---
# <a name="choices-function-in-powerapps"></a>PowerApps の Choices 関数
ルックアップ列で使用可能な値のテーブルを返します。

## <a name="description"></a>Description
**Choices** 関数は、ルックアップ列で使用可能な値のテーブルを返します。  

**Choices** 関数を使用して、ユーザーが選択する選択肢の一覧を提供します。 この関数は、編集フォームで[**コンボ ボックス**](../controls/control-combo-box.md) コントロールと共によく使用されます。

ルックアップの場合、**Choices** が返すテーブルは、ルックアップに関連付けられている外部テーブルと一致します。 **Choices** を使用することにより、追加データ ソースとして外部テーブルを追加する必要がなくなります。 **Choices** は、外部テーブルのすべての列を返します。

**Choices** はテーブルを返すので、[**Filter**](function-filter-lookup.md)、[**Sort**](function-sort.md)、[**AddColumns**](function-table-shaping.md)、その他すべてのテーブル操作関数を使って、テーブルをフィルター、並べ替え、整形できます。 

現時点で、**Choices** を[委任](../delegation-overview.md)することはできません。 この制限によりアプリで問題がある場合は、データ ソースとして外部エンティティを追加し、それを直接使用してください。 

[**ShowColumns**](function-table-shaping.md)、[**Search**](function-filter-lookup.md)、その他のテーブル関数とは異なり、**Choices** では列名を文字列にして二重引用符で囲む必要はありません。 列を直接参照するのと同じように、式を指定します。

列参照は、データ ソースに対して直接行う必要があります。 たとえば、データ ソースが **Accounts** でルックアップが **SLA** の場合、列参照は **Accounts.SLA** になります。 参照は、関数、変数、またはコントロールを経由することはできません。 この例を拡張し、**Accounts** が **Gallery** コントロールにフィードされる場合は、式 **Gallery.Selected.SLA** を使って選択されたアカウントの SLA を参照します。 ただし、この参照はコントロールを経由したので、**Columns** 関数に渡されることはできません。やはり **Accounts.SLA** を使う必要があります。

現時点では、参照列は SharePoint と Common Data Service でのみ使用できます。

## <a name="syntax"></a>構文
**Choices**( *column-reference* )

* *column-reference* – 必須。  データ ソースのルックアップ列です。 列名を二重引用符で囲まないでください。 参照は、データ ソースの列に対して直接行う必要があり、関数またはコントロールを経由してはなりません。

## <a name="examples"></a>例

#### <a name="choices-for-a-lookup"></a>ルックアップの選択肢

1. Common Data Service で[データベースを作成](../../../administrator/create-database.md)し、 **[サンプルアプリとデータを含める]** ボックスをオンにします。

    **Accounts** などの多数のエンティティが作成されます。

    **注**: エンティティ名は、PowerApps Studio の make.powerapps.com と複数形で単数形になっています。

    ![Common Data Service for Apps の Account エンティティのフィールドの一部を一覧表示します。 "主要連絡先" はルックアップフィールドです。](media/function-choices/entity-account.png)

    **Accounts** エンティティには **Primary Contact** 列があり、これは **連絡先** エンティティに対するルックアップです。  

    ![Common Data Service の Contact エンティティのフィールドの部分的な一覧](media/function-choices/entity-contact.png)

    各アカウントについて、連絡先が主連絡先として指定されているか、または主連絡先が "*ブランク*" になっています。

1. **Accounts** エンティティから[アプリを生成](../data-platform-create-app.md)します。

1. 左端近くにある画面とコントロールの一覧で、**EditScreen1** が表示されるまで下にスクロールし、そのすぐ下にある **EditForm1** を選択します。

    ![左側のナビゲーション バーで、EditScreen1 の EditForm1 を選択する](media/function-choices/select-editform.png)

1. 右側のペインの **[プロパティ]** タブで、 **[フィールドの編集]** を選択します。

    ![データペインを開く](media/function-choices/open-data-pane.png)

1. **[フィールド]** ウィンドウで、 **[フィールドの追加]** を選択します。

1. "**主要連絡先**" フィールドを検索し、チェックボックスをオンにして、 **[追加]** を選択します。

    ![Accounts を選択して [データ] ウィンドウを開く](media/function-choices/field-list.png)

    **主要連絡先**フィールドがフォームの下部に表示されます。 フィールドにエラーが表示されている場合は、 **[表示]** タブの **[データソース]** を選択し、**アカウント**データソースの省略記号 (...) を選択して、最新の情報に **[更新]** を選択します。

1. (省略可能) **Primary Contact** フィールドをフィールド一覧の下部から先頭にドラッグします。

1. **Primary Contact** のカードで、**コンボ ボックス** コントロールを選択します。

    このコントロールの**Items**プロパティは、最初の例のように表示名で列を識別する数式、または2番目の例のように論理名を使用して、列を識別する数式に設定されます。

   - **Choices( Accounts.'Primary Contact' )**
   - **Choices( Accounts.primarycontactid )**

     ![フォーム コントロールを含むキャンバス画面。 主要連絡先カード内のコンボボックスコントロールが選択されていて、数式の選択 (Accounts. 主要連絡先) を含む Items プロパティが表示されます。](media/function-choices/accounts-primary-contact.png)

1. **[ホーム]** タブの **[新しい画面]** を選択し、 **[空白]** を選択します。

1. **[挿入]** タブの **[データ テーブル]** を選択します。

1. **データテーブル**コントロールの**Items**プロパティを次の数式に設定します。

     **Choices( Accounts.'Primary Contact' )**

1. **データテーブル**コントロールの中央で、開始するリンクをクリックして **[フィールド...]** を選択し、表示するフィールドのチェックボックスをオンにします ( **firstname** 、 **lastname**など)。

     ![データ テーブル コントロールを含むキャンバス画面。 Items プロパティは式 Choices( Accounts.'Primary Contact' ) に設定され、テーブルには Contacts エンティティの最初のレコード セットの firstname 列と lastname 列が表示されている](media/function-choices/full-accounts-pc.png)