---
title: キャンバスアプリでの AsType 関数と IsType 関数 |Microsoft Docs
description: 構文と例を含むキャンバスアプリの AsType 関数と IsType 関数の参照情報
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 05/17/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 0ecb30a5a452a6ee092ccf9bc9d47f6182ef60ab
ms.sourcegitcommit: 7c1e70e94d75140955518349e6f9130ce3fd094e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/29/2019
ms.locfileid: "71993009"
---
# <a name="astype-and-istype-functions-in-canvas-apps"></a>キャンバスアプリの AsType 機能と IsType の関数

特定のエンティティ型 (**istype**) のレコード参照を確認し、その参照を特定の型 (**astype**) として扱います。

## <a name="description"></a>Description

詳細については、「[レコード参照とポリモーフィック参照](../working-with-references.md)について」を参照してください。

参照フィールドは、通常、特定のエンティティ内のレコードを参照します。 エンティティ型が適切に確立されているため、単純なドット表記を使用して参照のフィールドにアクセスできます。 たとえば、 **First (Accounts) のようになります。主要連絡先 '. '氏名 '** **Accounts**エンティティから**Contacts**エンティティの**主要連絡先**レコードにウォーク**し、氏名フィールドを**抽出します。

Common Data Service は、次の例のように、一連のエンティティのレコードを参照できるポリモーフィックなルックアップフィールドもサポートしています。

| ルックアップフィールド | 参照可能 |
|--------------|--------------|
| **責任** | **ユーザー**または**チーム** |
| **顧客** | **アカウント**または**連絡先** |
| **件** | **アカウント**、**連絡先**、**ナレッジ項目**など |

<!--note from editor: Change "Knowledge Articles" to "Knowledge Base articles" if that is what is being referenced.   -->

キャンバスアプリの数式では、レコード参照を使用してポリモーフィックな検索を行うことができます。 レコード参照は異なるエンティティを参照することがあるため、数式を記述するときに使用できるフィールドがわかりません。 *。フィールド*表記は使用できません。 これらの式は、実行時にアプリが検出するレコードに適合する必要があります。

**Istype**関数は、レコード参照が特定のエンティティ型を参照しているかどうかをテストします。 関数は、ブール値の TRUE または FALSE を返します。

**Astype**関数は、レコード参照を特定のエンティティ型として処理します。これは "*キャスト*" と呼ばれることもあります。 結果は、エンティティのレコードであるかのように使用できます。また、を使用することもでき*ます。* そのレコードのすべてのフィールドにアクセスするためのフィールド表記。 参照が特定の型ではない場合、エラーが発生します。

これらの関数を一緒に使用して、まずレコードのエンティティ型をテストし、次にフィールドが使用可能になるようにその型のレコードとして扱います。

```powerapps-dot
If( IsType( First( Accounts ).Owner, Users ),
    AsType( First( Accounts ).Owner, Users ).'Full Name',
    AsType( First( Accounts ).Owner, Teams ).'Team Name'
)
```

これらの関数は、レコード参照のフィールドにアクセスする場合にのみ必要です。 たとえば、次のように、[**フィルター**](function-filter-lookup.md)関数では、 **Istype**または**astype**なしでレコード参照を使用できます。

```powerapps-dot
Filter( Accounts, Owner = First( Users ) )
```

同様に、 [**Patch**](function-patch.md)関数でレコード参照を使用することもできます。

```powerapps-dot
Patch( Accounts, First( Accounts ), { Owner: First( Teams ) } )
```  

[**ギャラリー**](../controls/control-gallery.md)または[**編集フォーム**](../controls/control-form-detail.md)コントロール内などでレコードコンテキストで使用される場合、エンティティ型を参照するには、[グローバルあいまい排除演算子](operators.md#disambiguation-operator)を使用する必要がある場合があります。 たとえば、次の数式は、**会社名**が**顧客**参照である連絡先の一覧を表示しているギャラリーに対して有効です。

```powerapps-dot
If( IsType( ThisItem.'Company Name', [@Accounts] ),
    AsType( ThisItem.'Company Name', [@Accounts] ).'Account Name',
    AsType( ThisItem.'Company Name', [@Contacts] ).'Full Name'
)
```

どちらの関数でも、エンティティに接続されているデータソースの名前を使用して型を指定します。 数式を機能させるには、テストまたはキャストする任意の種類のデータソースをアプリに追加する必要もあります。 たとえば、エンティティからの**所有者**の参照とレコードを使用して**istype**型指定と**astype**を使用する場合は、**ユーザー**エンティティをデータソースとして追加する必要があります。 アプリで実際に使用しているデータソースのみを追加できます。参照が参照できるすべてのエンティティを追加する必要はありません。

レコード参照が*空白*の場合、 **ISTYPE**は FALSE を返し、 **astype**は*空白*を返します。 *空*のレコードのすべてのフィールドは*空白*になります。

## <a name="syntax"></a>構文

**Astype**( *recordreference*、 *EntityType* )

- *Recordreference* -必須。 レコード参照。多くの場合、複数のエンティティのいずれかのレコードを参照できる参照フィールドです。
- *EntityType* -必須。 テスト対象の特定のエンティティ。

**Istype**( *recordreference*、 *EntityType* )

- *Recordreference* -必須。 レコード参照。多くの場合、複数のエンティティのいずれかのレコードを参照できる参照フィールドです。
- *EntityType* -必須。 レコードのキャスト先となる特定のエンティティ。

## <a name="example"></a>例

[レコード参照とポリモーフィック](../working-with-references.md)な参照については、さまざまな例が含まれています。

1. タブレット用の空のキャンバスアプリを作成します。

1. **[表示]** タブで **[データソース]** を選択し、**連絡先**エンティティと**アカウント**エンティティをデータソースとして追加します。
    > [!div class="mx-imgBorder"]
    > 2つのデータソースを含む空のアプリを ![する: アカウントと連絡先](media/function-astype-istype/contacts-add-datasources.png)

1. 垂直方向に**空**の**ギャラリー**コントロールを挿入します。

    > [!div class="mx-imgBorder"]
    > 空の垂直レイアウトでギャラリーコントロールを挿入 ![には](media/function-astype-istype/contacts-customer-gallery.png)

1. 画面の右側の **[プロパティ]** タブで、ギャラリーの**Items**プロパティを**Contacts**に設定します。

    > [!div class="mx-imgBorder"]
    > プロパティペインで連絡先に項目を設定 ![](media/function-astype-istype/contacts-customer-datasource.png)

1. ギャラリーのレイアウトを [**タイトル] と [サブタイトル**] に設定します。

    > [!div class="mx-imgBorder"]
    > ![[プロパティ] ペインからレイアウトピッカーを開き](media/function-astype-istype/contacts-customer-layout.png)

    > [!div class="mx-imgBorder"]
    > タイトルとサブタイトルにレイアウトを設定 ![](media/function-astype-istype/contacts-customer-flyout.png)

1. **データ**ペインで、 **Title1**の一覧を開き、 **[フルネーム]** を選択します。

    > [!div class="mx-imgBorder"]
    > タイトルの値を ![設定](media/function-astype-istype/contacts-customer-title.png)

1. **Subtitle1** label コントロールを選択します。

    > [!div class="mx-imgBorder"]
    > 字幕値を ![設定](media/function-astype-istype/contacts-customer-subtitle.png)

1. **Subtitle1**の**Text**プロパティを次の数式に設定します。

    ```powerapps-dot
    If( IsBlank( ThisItem.'Company Name' ), "--",
        IsType( ThisItem.'Company Name', [@Accounts] ),
            "Account: " & AsType( ThisItem.'Company Name', [@Accounts] ).'Account Name',
        "Contact: " & AsType( ThisItem.'Company Name', [@Contacts] ).'Full Name'
    )
    ```

    > [!div class="mx-imgBorder"]
    > ![画面が表示されるようになりました。ギャラリーには、アカウントと連絡先が混在してい](media/function-astype-istype/contacts-customer-complete.png)

    ギャラリーのサブタイトルには、次の値が表示されます。
    - "**会社名**" が*空白*の場合は "--" になります。
    - 「Account:」と入力し、 **[Company name]** フィールドがアカウントを参照している場合は**Accounts**エンティティの **[account name]** フィールドを選択します。
    - 「Contact:」と入力し、 **[会社名]** フィールドで連絡先が参照されている場合は、 **Contacts**エンティティの "**氏名**" フィールドに入力します。

    結果は、このトピックの結果とは異なる場合があります。これは、変更されたサンプルデータを使用して結果の追加の種類を表示するためです。
