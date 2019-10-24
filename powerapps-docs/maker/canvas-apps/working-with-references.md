---
title: レコード参照とポリモーフィックな参照を理解する |Microsoft Docs
description: キャンバスアプリでレコード参照とポリモーフィック参照を操作する
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 09/14/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: deea21dd97ee71a74973393b7d6714a8c55ba969
ms.sourcegitcommit: 57b968b542fc43737330596d840d938f566e582a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2019
ms.locfileid: "71989466"
---
# <a name="understand-record-references-and-polymorphic-lookups-in-canvas-apps"></a>キャンバスアプリでのレコード参照とポリモーフィックな参照について

学校で研究論文を書いたときに、最後に参照の一覧を提供したことがあります。 実際に使用した背景資料のコピーは含まれていませんが、web リンク、ブックのタイトルと作成者、またはその他の情報によって、だれかが元のソースを追跡できるようにしました。 さまざまな種類のソースを1つのリストに混在させることができます。オーディオ録音の横には、それぞれ固有の詳細情報が記載されています。 たとえば、Wikipedia の記事には、多くの場合、[参照の長い一覧](https://en.wikipedia.org/wiki/Microsoft#References)が含まれています。

キャンバスアプリでは、多くの場合、データソースからダウンロードされたレコードのコピーを操作します。 [**検索**](functions/function-filter-lookup.md)機能と[**フィルター**](functions/function-filter-lookup.md)関数、および[**ギャラリー**](controls/control-gallery.md)コントロールの**選択さ**れたプロパティを使用して、目的の特定のレコードを識別します。 **フィルター**または**選択さ**れているすべてのレコードは同じエンティティ型であるため、単純なフィールドを使用できます。*フィールド*表記。 多くの場合、これらのコピーには参照情報が含まれているため、 [**Patch**](functions/function-patch.md)関数を使用して元のソースを更新できます。

Canvas apps では、*レコード参照*もサポートしています。 研究論文の参照と同様に、レコード参照は、レコードの完全なコピーを含まないレコードを参照します。 このような参照は、任意のエンティティのレコードを参照できます。 また、研究論文の参照と同様に、複数のエンティティのレコードを1つの列に混在させることができます。

レコード参照に対する多くの操作は、レコードの操作と同じです。 レコード参照を相互に比較したり、完全なレコードに比較したりすることができます。 レコード参照の値は、完全なレコードでの検索と同様に、 **Patch**関数で設定できます。

重要な使用方法の違いが1つあります。最初に参照先のエンティティを確立することなく、レコード参照のフィールドに直接アクセスすることはできません。 これは、キャンバスアプリでは、数式を記述するときにすべての型が認識される必要があるためです。 アプリが実行されるまで、レコード参照の種類がわからないため、単純なを使用することはできません。*フィールド*表記を直接入力します。 まず、 [**istype**](functions/function-astype-istype.md)の関数を使用してエンティティ型を動的に特定し、次にを使用する必要があります。[**Astype**](functions/function-astype-istype.md)関数の結果の*フィールド*表記。

*エンティティ型*は、エンティティ内の各レコードのスキーマを参照します。 各エンティティには、名前とデータ型が異なる一意のフィールドセットがあります。 エンティティの各レコードは、その構造を継承します。2つのレコードが同じエンティティから取得された場合、同じエンティティ型になります。

## <a name="polymorphic-lookups"></a>ポリモーフィック参照

Common Data Service は、レコード間のリレーションシップをサポートします。 **Accounts**エンティティの各レコードには、 **Contacts**エンティティのレコードに対する**主要な連絡先**参照フィールドがあります。 参照で参照できるのは**連絡先**のレコードのみで、たとえば**Teams**エンティティのレコードを参照することはできません。 この最後の詳細は、参照できるフィールドを常に把握しているので重要です。

Common Data Service では、セット内の任意のエンティティからのレコードを参照できるポリモーフィックな参照もサポートされています。 たとえば、 **[所有者]** フィールドは、 **Users**エンティティまたは**Teams**エンティティ内のレコードを参照できます。 異なるレコードの同じルックアップフィールドが、異なるエンティティ内のレコードを参照している可能性があります。 この場合、どのフィールドが使用可能になるかは常にわかりません。

キャンバスレコードの参照は、Common Data Service でのポリモーフィックな検索を使用するように設計されています。 また、このコンテキストの外部でレコード参照を使用することもできます。これは、2つの概念がどのように異なるかを示しています。

次のセクションでは、**所有者**の検索を使用して、これらの概念について説明します。

## <a name="show-the-fields-of-a-record-owner"></a>レコードの所有者のフィールドを表示する

Common Data Service のすべてのエンティティには、**所有者**フィールドが含まれています。 このフィールドを削除することはできません。別のフィールドを追加することはできません。常に値が必要です。

このフィールドを**Account**エンティティに表示するには、次のようにします。

1. [この PowerApps サイト](http://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)を開きます。
1. 左側のナビゲーションバーで、[**データ** > **エンティティ**] を選択します。
1. エンティティの一覧で [Account] \ (**アカウント**\) を選択します。
1. 右上隅にあるフィルター一覧 (既定では**既定値**に設定されています) を開き、 **[すべて]** を選択します。
1. **[所有者]** フィールドが表示されるまで下にスクロールします。

 > [!div class="mx-imgBorder"]
 > アカウントエンティティ ](media/working-with-references/owner-field.png) の ![Owner フィールド

このルックアップフィールドは、 **Teams**エンティティまたは**Users**エンティティからのレコードを参照できます。 これらのエンティティのすべてのレコードが**所有者**になる権限を持っているわけではありません。問題が発生した場合は、サポートされている役割を確認してください。

次の図は、**アカウントの単純**なギャラリーを示しています。ここでは、 **accounts**エンティティがデータソースとしてアプリに追加されています。

> [!div class="mx-imgBorder"]
> ギャラリーコントロールに表示される ![Accounts ](media/working-with-references/accounts-gallery.png)

> [!IMPORTANT]
> このトピックでは、Common Data Service に付属しているサンプルデータの一部ではない名前とその他の値を示しています。 この手順では、特定の結果に対してコントロールを構成する方法を正確に説明しますが、エクスペリエンスは組織のデータによって異なります。

ギャラリーに各アカウントの所有者を表示するには、式**ThisItem.Owner.Name**を使用することが必要になる場合があります。 ただし、**チーム**エンティティの 名前 フィールドは **チーム名** で、**ユーザー**エンティティの 名前 フィールドは **フルネーム** です。 アプリを実行するまでは、使用している検索の種類を認識できません。また、**アカウント**エンティティ内のレコードによって異なる場合があります。

この分散に適合する数式が必要です。 また、**所有者**(この場合は**ユーザー**と**チーム**) のエンティティ型のデータソースも追加する必要があります。 次の3つのデータソースをアプリに追加します。

> [!div class="mx-imgBorder"]
> データペインの ![Accounts、チーム、およびユーザーのエンティティ ](media/working-with-references/accounts-datasources.png)

これらのデータソースが配置されたので、次の式を使用して、ユーザーまたはチームの名前を表示します。

```powerapps-dot
If( IsType( ThisItem.Owner, [@Teams] ),
    "Team: " & AsType( ThisItem.Owner, [@Teams] ).'Team Name',
    "User: " & AsType( ThisItem.Owner, [@Users] ).'Full Name' )
```

> [!div class="mx-imgBorder"]
> [所有者] フィールドが表示された状態で、ギャラリーコントロールに表示 ![Accounts ](media/working-with-references/accounts-displayowner.png)

この数式では、 **istype**関数が**Teams**エンティティに対して**Owner**フィールドをテストします。 そのエンティティ型の場合、 **astype**関数はそれを**チーム**レコードにキャストします。 この時点で、を使用して、**チーム名**を含む**Teams**エンティティのすべてのフィールドにアクセスでき*ます。フィールド*表記。 [**所有者]** フィールドが **[Teams]** エンティティ内のレコードではないことが**istype**によって判断された場合、 **[所有者]** フィールドは必須 (*空白*にすることはできません) であるため、そのフィールドは**Users**エンティティ内のレコードである必要があります。

グローバルエンティティ型を使用していることを確認するために、 **[@Teams]** および **[@Users]** には、[グローバルなあいまい](functions/operators.md#disambiguation-operator)を排除する演算子を使用しています。 この場合は必要ありませんが、フォームを作成することをお勧めします。 1対多のリレーションシップは、多くの場合、ギャラリーのレコードのスコープ内で競合するため、混乱を避けることができます。

レコード参照のフィールドを使用するには、最初に**astype**関数を使用して、それを特定のエンティティ型にキャストする必要があります。 使用するエンティティ型がシステムによって認識されないため、 **[所有者]** フィールドから直接フィールドにアクセスすることはできません。

**Astype**関数は、 **Owner**フィールドが要求されているエンティティ型と一致しない場合にエラーを返します。そのため、 **IfError**関数を使用すると、この式を簡略化できます。 まず、試験的な機能の**数式レベルのエラー管理**を有効にします。

> [!div class="mx-imgBorder"]
> 数式レベルのエラー管理を有効にする ![Experimental スイッチ ](media/working-with-references/accounts-iferror.png)

次に、前の数式を次の式に置き換えます。

```powerapps-dot
IfError(
    "Team: " & AsType( ThisItem.Owner, [@Teams] ).'Team Name',
    "User: " & AsType( ThisItem.Owner, [@Users] ).'Full Name' )
```

## <a name="filter-based-on-an-owner"></a>所有者に基づいてフィルター処理する

これで、レコード参照を操作するための最も難しい作業が完了しました。 その他のユースケースは、レコードのフィールドにアクセスしないため、より簡単です。 ここでは、フィルター処理について説明します。

ギャラリーの上に**コンボボックス**コントロールを追加し、新しいコントロールの次のプロパティを設定します。

- **項目**: `Users`
- **Selectmultiple**: `false`

> [!div class="mx-imgBorder"]
> Items プロパティが Users に設定されるギャラリー上のコンボボックスコントロール ![Added ](media/working-with-references/filter-insert-combobox.png)

このコンボボックスから選択した特定のユーザーでギャラリーをフィルター処理するには、ギャラリーの**Items**プロパティを次の数式に設定します。

```powerapps-dot
Filter( Accounts, Owner = ComboBox1.Selected )
```

> [!div class="mx-imgBorder"]
> コンボボックスコントロールで設定された値に基づいてギャラリーを ![Filtered ](media/working-with-references/filter-accounts.png)

> [!IMPORTANT]
> 手順を正確に実行すると、このトピックの手順が正確になります。 ただし、コントロールの名前が異なる場合は、名前によってコントロールを参照する数式は失敗します。 同じ型のコントロールを削除して追加すると、コントロールの名前の末尾にある数値が変更されます。 エラーを表示する数式には、すべてのコントロールの正しい名前が含まれていることを確認します。

レコードの参照を他のレコード参照または完全なレコードと比較しているため、 **istype**または**astype**を使用する必要はありません。 アプリは、ComboBox1 のエンティティ型を認識して**います。** これは、**ユーザー**エンティティから派生しているためです。 所有者がチームであるアカウントがフィルター条件に一致しません。

ユーザーまたはチームによるフィルター処理をサポートすることで、少し掘り下げていくことができます。

1. ギャラリーのサイズを変更し、コンボボックスを移動して、画面の上部付近にスペースを作成し、ギャラリーの上に[**ラジオ**コントロール](controls/control-radio.md)を挿入して、新しいコントロールに対して次のプロパティを設定します。

    - **項目**: `[ "All", "Users", "Teams" ]`
    - **レイアウト**: `Layout.Horizontal`

1. **コンボボックス**コントロールの場合は、このプロパティを設定します (コンボボックスが表示されなくなった場合は、ラジオコントロールの**ユーザー**を選択します)。

    - **Visible**: `Radio1.Selected.Value = "Users"`

1. **コンボボックス**コントロールをコピーして貼り付け、コピーを元のに直接移動して、コピー用に次のプロパティを設定します。

    - **項目**: `Teams`
    - **Visible**: `Radio1.Selected.Value = "Teams"`

    アプリでは、ラジオコントロールの状態に応じて、一度に1つのコンボボックスのみが表示されます。 相互に直接配置されているため、内容を変更するコントロールと同じように見えます。

1. 最後に、**ギャラリー**コントロールの**Items**プロパティを次の数式に設定します。

    ```powerapps-dot
    Filter( Accounts,
        Radio1.Selected.Value = "All"
        Or (Radio1.Selected.Value = "Users" And Owner = ComboBox1.Selected)
        Or (Radio1.Selected.Value = "Teams" And Owner = ComboBox1_1.Selected)
    )
    ```

    > [!div class="mx-imgBorder"]
    > すべてのレコードまたは特定のユーザーまたはチーム ](media/working-with-references/filter-combobox.png) を示す ![Filtered ギャラリー

これらの変更により、すべてのレコードを表示したり、ユーザーまたはチームに基づいてフィルターを適用したりすることができます。

> [!div class="mx-imgBorder"]
> オプションコントロールとコンボボックスに基づいてフィルター処理されたさまざまな結果を表示する ![Animation ](media/working-with-references/filter-allthree.gif)

数式は完全に委任可能なです。 ラジオボタンの値を比較している部分はすべてのレコードの定数であり、フィルターの残りの部分が Common Data Service に送信される前に評価されます。

所有者の種類をフィルター処理する場合は、 **istype**関数を使用できますが、まだ委任可能なていません。

> [!div class="mx-imgBorder"]
> IsType を使用して所有者の種類別に ![Filter ](media/working-with-references/filter-bytype.png)

## <a name="update-the-owner-by-using-patch"></a>Patch を使用して所有者を更新する

**[所有者]** フィールドは、他の検索と同じ方法で更新できます。 現在選択されているアカウントの所有者を最初のチームに設定するには、次のようにします。

```powerapps-dot
Patch( Accounts, Gallery1.Selected, { Owner: First( Teams ) } )
```

この方法は、アプリが**最初の (チーム)** の種類を認識しているため、通常の参照とは異なります。 最初のユーザーを代わりに使用する場合は、その部分を**最初の (Users)** に置き換えます。 **Patch**関数は、 **Owner**フィールドをこの2つのエンティティ型のどちらかに設定できることを認識しています。

この機能をアプリに追加するには:

1. **[ツリービュー]** ペインで、**ラジオ**コントロールと2つの**コンボボックス**コントロールを同時に選択します。

1. 省略記号メニューで、[**これらの項目をコピー**する] を選択します。

    > [!div class="mx-imgBorder"]
    > ツリービューを使用した複数のコントロールの ![Copy ](media/working-with-references/patch-copy.png)

1. 同じメニューで、 **[貼り付け]** を選択します。

    > [!div class="mx-imgBorder"]
    > ツリービューを使用した複数のコントロールの ![Paste ](media/working-with-references/patch-paste.png)

1. コピーしたコントロールをギャラリーの右側に移動します。

    > [!div class="mx-imgBorder"]
    > ギャラリーの右側に ![Moved コピーされたコントロール ](media/working-with-references/patch-position.png)

1. コピーした**ラジオ**コントロールを選択し、次のプロパティを変更します。

    - 項目: `[ "Users", "Teams" ]`
    - 既定値: `If( IsType( Gallery1.Selected.Owner, Users ), "Users", "Teams" )`

    > [!div class="mx-imgBorder"]
    > ラジオコントロールからすべての選択肢を ![Removed ](media/working-with-references/patch-noall.png) 

1. **ラジオ**コントロールで **[ユーザー]** を選択すると、ユーザーを一覧表示する**コンボボックス**コントロールが表示されます。

1. 表示されている**コンボボックス**コントロールを選択し、 **DefaultSelectedItems**プロパティを次の数式に設定します。

    ```powerapps-dot
    If( IsType( Gallery1.Selected.Owner, Users ),
        AsType( Gallery1.Selected.Owner, Users ),
        Blank()
    )
    ```

    > [!div class="mx-imgBorder"]
    > [ユーザー] コンボボックスに設定された ![Default プロパティ ](media/working-with-references/patch-default-users.png)

1. **ラジオ**コントロールで、 **[チーム]** を選択して、チームを一覧表示する**コンボボックス**コントロールが表示されるようにします。

1. ユーザーに対して表示されている非表示の**コンボボックス**コントロールから選択を取得する**ラジオ**コントロールを選択します。

1. チームに対して表示される**コンボボックス**コントロールを選択し、その**DefaultSelectedItems**プロパティを次の数式に設定します。

    ```powerapps-dot
    If( IsType( Gallery1.Selected.Owner, Teams ),
        AsType( Gallery1.Selected.Owner, Teams ),
        Blank()
    )
    ```

    > [!div class="mx-imgBorder"]
    > Teams コンボボックスに設定された ![Default プロパティ ](media/working-with-references/patch-default-teams.png)

1. **ボタン**コントロールを挿入し、**コンボボックス**コントロールの下に移動して、ボタンの**Text**プロパティを `"Patch Owner"` に設定します。

1. ボタンの**Onselect**プロパティを次の数式に設定します。

    ```powerapps-dot
    Patch( Accounts, Gallery1.Selected,
        { Owner: If( Radio1_1.Selected.Value = "Users",
                ComboBox1_2.Selected,
                ComboBox1_3.Selected ) } )
    ```

    > [!div class="mx-imgBorder"]
    > ボタンコントロールに設定 ![Formula ](media/working-with-references/patch-button.png)

コピーした**ラジオ**コントロールと**コンボボックス**コントロールは、ギャラリーで現在選択されているアカウントの所有者を表示します。 同じコントロールで、ボタンを選択して、アカウントの所有者を任意のチームまたはユーザーに設定できます。

> [!div class="mx-imgBorder"]
> ユーザーまたはチームのいずれかの所有者の修正プログラムを示す ![Animation ](media/working-with-references/patch-allthree.gif)

## <a name="show-the-owner-by-using-a-form"></a>フォームを使用して所有者を表示する

カスタムカードを追加することで、フォーム内に**所有者**フィールドを表示できます。 このドキュメントの執筆時点では、フォームコントロールを使用してフィールドの値を変更することはできません。

1. **編集フォーム**コントロールを挿入し、サイズを変更して、右下隅に移動します。

1. 画面の右側の **[プロパティ]** タブで、 **[データソース]** の一覧を開き、 **[アカウント]** を選択します。

    > [!div class="mx-imgBorder"]
    > 空白の値を持つ追加フィールドを表示する ![Form コントロール ](media/working-with-references/form-insert.png)  

1. フォームの**Item**プロパティを `Gallery1.Selected` に設定します。

    > [!div class="mx-imgBorder"]
    > ギャラリー内の選択した項目から設定された追加フィールドを表示する ![Form コントロール ](media/working-with-references/form-item.png)

1. 画面の右側の **[プロパティ]** タブで、フィールドの **[編集]** を選択します。

1. **[フィールド]** ウィンドウで省略記号を選択し、 **[カスタムカードの追加]** を選択します。

    > [!div class="mx-imgBorder"]
    > カスタムカードを追加するための ![Command ](media/working-with-references/form-customcard.png)

    フォームコントロールの下部に新しいカードが表示されます。

1. 必要に応じてカードのサイズを変更して、すべてのテキストを表示します。

    > [!div class="mx-imgBorder"]
    > ![Inserted カスタムカード、空白の ](media/working-with-references/form-inserted-customcard.png)

1. カスタムカードに**ラベル**コントロールを挿入し、ラベルの**Text**プロパティをギャラリーで使用した数式に設定します。

    ```powerapps-dot
    If( IsType( ThisItem.Owner, Teams ),
        "Team: " & AsType( ThisItem.Owner, Teams ).'Team Name',
        "User: " & AsType( ThisItem.Owner, Users ).'Full Name' )
    ```

    > [!div class="mx-imgBorder"]
    > ラベルコントロールの所有者フィールドを示す ![Custom カード ](media/working-with-references/form-displayowner.png)

ギャラリーでの選択ごとに、レコードの所有者を含む、アカウントのフィールドがフォームに表示されます。 **Patch**ボタンを使用して所有者を変更すると、フォームコントロールにもその変更が表示されます。

> [!div class="mx-imgBorder"]
> ギャラリー内の変更に応答するフォームコントロールを示す ![Animation ](media/working-with-references/form-allthree.gif)

## <a name="show-the-fields-of-a-customer"></a>顧客のフィールドを表示する

Common Data Service では、**顧客**参照フィールドは、**所有者**と非常によく似た別のポリモーフィックなルックアップです。

**所有者**はエンティティごとに1つに制限されますが、エンティティには、0、1、または複数の**顧客**参照フィールドを含めることができます。 **Contacts**システムエンティティには、**顧客**参照フィールドである "**会社名**" フィールドが含まれています。

> [!div class="mx-imgBorder"]
> "会社名" フィールドを顧客データ型として表示する ![Contact エンティティは必要ありません ](media/working-with-references/customer-companyname.png)

新しいフィールドの**customer**データ型を選択することにより、さらに**顧客**のルックアップフィールドをエンティティに追加できます。

![フィールドを作成するときのデータ型の一覧からの顧客データ型](media/working-with-references/customer-datatype.png)

**顧客**参照フィールドは、 **Accounts**エンティティまたは**Contacts**エンティティのいずれかのレコードを参照できます。 これらのエンティティで**istype**型と**astype**型の関数を使用します。そのため、これらの関数をデータソースとして追加することをお勧めします (**チーム**と**ユーザー**を配置したままにすることができます)。

> [!div class="mx-imgBorder"]
> データペインの ![Accounts、チーム、ユーザー、および連絡先のエンティティ ](media/working-with-references/customer-datasources.png)

**[顧客]** フィールドと **[所有者]** フィールドの扱いは同様であるため、アプリを文字どおりにコピーできます (**ファイル** >  名前を付け**て保存**し、別の名前を指定してから、単純な置換を行うことができます)。

| Location | **所有者**のサンプル | **顧客**のサンプル |
|----------|-----------|------------------|
| 至る | **責任** | **' カスタマー名 '** |
| 至る | **ユーザ** | **企業** |
| 至る | **担当** | **連絡先** |
| ギャラリーの**Items**プロパティ | **企業** | **連絡先** |
| フォームの**Items**プロパティ | **企業** | **連絡先** |
| **Patch**の1番目の引数<br>ボタンの**Onselect**プロパティ | **企業** | **連絡先** |
| ラジオの**Items**プロパティをフィルター処理します | **[&nbsp; "All"、&nbsp; "Users"、&nbsp; "Teams" &nbsp;]** | **[&nbsp; "All"、&nbsp; "Accounts"、&nbsp; "Contacts" &nbsp;]** |
| Patch radio の**Items**プロパティ | **["ユーザー"、"Teams"]** | **["Accounts", "Contacts"]** |
| コンボボックスの**Visible**プロパティ | **"ユーザー"** と **"チーム"** | **"アカウント"** と **"連絡先"** |

たとえば、新しいギャラリーには、次の**Items**プロパティが必要です。

```powerapps-dot
Filter( Contacts,
    Radio1.Selected.Value = "All"
    Or (Radio1.Selected.Value = "Accounts" And 'Company Name' = ComboBox1.Selected)
    Or (Radio1.Selected.Value = "Contacts" And 'Company Name' = ComboBox1_1.Selected)
)
```

> [!div class="mx-imgBorder"]
> 単純な変更が適用された所有者アプリから派生したアプリ ![Customer ](media/working-with-references/customer-simple-update.png)

**顧客**と**所有者**の間の2つの重要な違いは、ギャラリー内の数式とフォームを更新する必要があることです。

1. これらのエンティティ型を名前で参照すると、**アカウント**と**連絡先**の間の一対多のリレーションシップが優先されます。 **アカウント**ではなく **\[ \@Accounts]** を使用します。**連絡先**ではなく、 **\[ \@Contacts]** を使用します。 [グローバルなあいまい排除演算子](functions/operators.md#disambiguation-operator)を使用することにより、エンティティ型を**Istype**種類と**astype**で参照していることを確認します。 この問題は、ギャラリーおよびフォームコントロールのレコードコンテキストにのみ存在します。

1. **[所有者]** フィールドには値を指定する必要がありますが、 **Customer**フィールドは*空白*にすることができます。 型名を指定せずに正しい結果を表示するには、 [ **isblank**関数](functions/function-isblank-isempty.md)を使用してこのケースをテストし、代わりに空のテキスト文字列を表示します。

これらの変更はどちらも、フォームのカスタムカードに表示されるのと同じ数式に含まれています。また、ギャラリーの label コントロールの**Text**プロパティにも表示されます。

```powerapps-dot
If( IsBlank( ThisItem.'Company Name' ), "",
    IsType( ThisItem.'Company Name', [@Accounts] ),
        "Account: " & AsType( ThisItem.'Company Name', [@Accounts] ).'Account Name',
    "Contact: " & AsType( ThisItem.'Company Name', [@Contacts] ).'Full Name'
)
```

> [!div class="mx-imgBorder"]
> ギャラリーのサブタイトルラベルコントロールの Text プロパティに ![Update ](media/working-with-references/customer-update.png)

これらの変更により、 **Contacts**エンティティの **[Company Name]** フィールドを表示および変更できます。

> [!div class="mx-imgBorder"]
> 連絡先を選択して他のコントロールとフォームを変更する方法を示す ![Animation ](media/working-with-references/customer-allthree.gif)

## <a name="understand-regarding-lookup-fields"></a>ルックアップフィールドについて

[**関連**参照] フィールドは、このトピックで既に使用しているものとは若干異なります。 まず、このトピックで説明したパターンを適用し、その他のテクニックについて学習します。

**Fax**エンティティだけを使用して開始できます。 このエンティティには、**アカウント**、**連絡先**、およびその他のエンティティを参照することのできる、参照フィールドに関するポリモーフィックな**関連**があります。 アプリを**顧客**向けに取得し、 **fax**用に変更することができます。

| Location | **顧客**のサンプル | **Fax**のサンプル |
|----------|-----------|------------------|
| 至る | **' カスタマー名 '** | **件** |
| ギャラリーの**Items**プロパティ | **連絡先** | **☆** |
| フォームの**Items**プロパティ | **連絡先** | **☆** |
| **Patch**の1番目の引数<br> ボタンの**Onselect**プロパティ | **連絡先** | **☆** |

ここでも、データソースを追加する必要があります。今回は**fax**用です。 **[表示]** タブの **[データソース]** を選択します。

> [!div class="mx-imgBorder"]
> アカウント、チーム、ユーザー、連絡先、および Fax の各エンティティを表示する ![Data ウィンドウ ](media/working-with-references/faxes-datasources.png)

に**関する**重要な違いは、**アカウント**と**連絡先**に限定されないことです。 実際、エンティティの一覧はカスタムエンティティによって拡張できます。 ほとんどのアプリは変更せずにこの点に対応できますが、ギャラリーのラベルとフォームの式を更新する必要があります。

```powerapps-dot
If( IsBlank( ThisItem.Regarding ), "",
    IsType( ThisItem.Regarding, [@Accounts] ),
        "Account: " & AsType( ThisItem.Regarding, [@Accounts] ).'Account Name',
    IsType( ThisItem.Regarding, [@Contacts] ),
        "Contacts: " & AsType( ThisItem.Regarding, [@Contacts] ).'Full Name',
    ""
)
```

> [!div class="mx-imgBorder"]
> 参照に関するサブタイトルコントロールのテキストプロパティを ![Updated ](media/working-with-references/regarding-label.png)

これらの変更を行った後、**所有者**と**顧客**の参照と同様に、**関連**する参照を操作します。

> [!div class="mx-imgBorder"]
> ギャラリー内の項目を選択すると、他のコントロールとフォームがどのように変わるかを示す ![Animation ](media/working-with-references/regarding-allthree.gif)

## <a name="understand-regarding-relationships"></a>リレーションシップについて

に**つい**ては、前者が多対一の関係を伴うため、 **Owner**と**Customer**とは異なります。 定義上、逆の一対多リレーションシップでは、**最初の (Accounts) を作成できます。Fax**。

では、エンティティの定義をバックアップして見てみましょう。 Common Data Service では、 **fax**、**タスク**、**電子メール**、**メモ**、**電話**、**文字**、**チャット**などのエンティティが[*アクティビティ*](../../developer/common-data-service/activity-entities.md)として指定されます。 独自の[カスタムアクティビティエンティティ](../../developer/common-data-service/custom-activities.md)を作成することもできます。 活動エンティティを表示または作成すると、その設定が **[その他の設定]** の下に表示されます。

![エンティティを作成するときのアクティビティエンティティの設定](media/working-with-references/activity-entitytype.png)

その他のエンティティは、エンティティの設定で*アクティビティタスク*として有効になっている場合、アクティビティエンティティに関連付けることができます。 **アカウント**、**連絡先**、およびその他の多くの標準エンティティは、指定されています ([その他の**設定**] の下)。

![エンティティを作成するときのアクティビティタスクの設定](media/working-with-references/activity-entityuse.png)

すべてのアクティビティエンティティとアクティビティ-タスクエンティティには、暗黙のリレーションシップがあります。 画面の上部にある **[すべて]** にフィルターを変更した場合は、 **[fax]** エンティティを選択し、 **[リレーションシップ]** タブを選択すると、 **[関連]** 検索 の対象になるすべてのエンティティが表示されます。

> [!div class="mx-imgBorder"]
> 多対一のリレーションシップについて表示されている Fax エンティティの ![Relationships ](media/working-with-references/activity-manytoone.png)

**Accounts**エンティティのリレーションシップを表示すると、**関連**するルックアップフィールドのソースにすることができるすべてのエンティティが表示されます。

> [!div class="mx-imgBorder"]
> 1対多のリレーションシップについて表示されている Account エンティティの ![Relationships ](media/working-with-references/activity-onetomany.png)

どのような意味があるのでしょうか。

- 数式を記述するときは、アクティビティエンティティの一覧が固定されていないことを考慮する必要があり、独自に作成することもできます。 この数式では、予期していなかったアクティビティエンティティを適切に処理する必要があります。
- アクティビティタスクとアクティビティには、一対多のリレーションシップがあります。 アカウントに関連するすべての fax を簡単に確認できます。

アプリでこの概念を調べるには、次のようにします。

1. 別の画面を追加します。

    > [!div class="mx-imgBorder"]
    > 空の画面を ![Insert ](media/working-with-references/activitypointer-newscreen.png)

1. ギャラリーコントロールを挿入し、サイズを変更して、画面の左側に移動します。

1. 画面の右側の **[プロパティ]** タブで、ギャラリーの**項目**を**Accounts**に設定します。

    > [!div class="mx-imgBorder"]
    > プロパティウィンドウのアカウントに項目を ![Set ](media/working-with-references/activitypointer-accounts.png)

1. ギャラリーのレイアウトを **[タイトル]** に設定し、タイトル フィールドを  **[Account Name]** に設定します。

    > [!div class="mx-imgBorder"]
    > [プロパティ] ペインのギャラリーコントロールのタイトルにレイアウトを ![Set ](media/working-with-references/activitypointer-account-name.png)

1. 2つ目のギャラリーを追加し、サイズを変更して、画面の右側に移動します。

1. 新しいギャラリーの**Items**プロパティを `Gallery2.Selected.Faxes` に設定します。

    このステップでは、特定のアカウントの fax のフィルター処理された一覧を返します。

    > [!div class="mx-imgBorder"]
    > fax を表示するギャラリーの Items プロパティを ![Set し ](media/working-with-references/activitypointer-faxes.png)

1. ギャラリーのレイアウトを **タイトル と サブタイトル** に設定し、タイトル フィールドを **件名** フィールド (小文字の**件名**) で表示するように設定します。

    > [!div class="mx-imgBorder"]
    > タイトルを件名フィールドに ![Set ](media/working-with-references/activitypointer-subject.png)

アカウントの一覧で項目を選択すると、fax の一覧にそのアカウントの fax のみが表示されます。

> [!div class="mx-imgBorder"]
> fax の一覧を運転しているアカウントギャラリーの選択内容を示す ![Animation ](media/working-with-references/activitypointer-allthree.gif)

## <a name="activity-entity"></a>アクティビティエンティティ

前のセクションで説明したように、アカウントのすべての fax を表示できます。 ただし、fax、電子メールメッセージ、電話、およびその他のやり取りなど、アカウントのすべてのアクティビティを表示することもできます。

後者のシナリオでは、 **Activity**エンティティを使用します。 このエンティティを表示するには、右上隅の **[すべて]** をオンにして、エンティティの一覧からフィルターを削除します。

> [!div class="mx-imgBorder"]
> アクティビティエンティティを示すエンティティの ![List ](media/working-with-references/activitypointer-entity.png)

**アクティビティ**エンティティは特殊です。 **Fax**エンティティにレコードを追加するたびに、システムによって、すべてのアクティビティエンティティで共通のフィールドを持つレコードが**アクティビティ**エンティティに作成されます。 これらのフィールドのうち、**件名**は最も興味深いものの1つです。

前の例では、1行だけを変更することで、すべてのアクティビティを表示できます。 @No__t_0 を `Gallery2.Selected.Activities` に置き換えます。

> [!div class="mx-imgBorder"]
> 2番目のギャラリーの Items プロパティの ![Change、fax からアクティビティへの変更 ](media/working-with-references/activitypointer-gallery.png)

レコードは**アクティビティ**エンティティから取得されますが、 **istype**関数を使用して、アクティビティの種類を識別できます。 ここでも、エンティティ型で**istype**種類を使用する前に、データソースを追加する必要があります。

> [!div class="mx-imgBorder"]
> IsType 関数に必要なすべてのエンティティを表示している ![Data ペイン ](media/working-with-references/activity-datasources.png)

この数式を使用すると、ギャラリー内のラベルコントロールにレコードの種類を表示できます。

```powerapps-dot
If( IsType( ThisItem, [@Faxes] ), "Fax",
    IsType( ThisItem, [@'Phone Calls'] ), "Phone Call",
    IsType( ThisItem, [@'Email Messages'] ), "Email Message",
    IsType( ThisItem, [@Chats] ), "Chat",
    "Unknown"
)
```

> [!div class="mx-imgBorder"]
> fax、電話、およびその他のアクティビティに関する情報を表示するには、text プロパティを数式に ![Set ](media/working-with-references/activitypointer-type.png)

また、 **astype**を使用して、特定の型のフィールドにアクセスすることもできます。 たとえば、次の数式は各活動の種類を決定し、電話の場合**は電話番号エンティティから**電話番号と通話の方向を表示します。

```powerapps-dot
If( IsType( ThisItem, [@Faxes] ), "Fax",
    IsType( ThisItem, [@'Phone Calls'] ),
       "Phone Call: " &
       AsType( ThisItem, [@'Phone Calls'] ).'Phone Number' &
       " (" & AsType( ThisItem, [@'Phone Calls'] ).Direction & ")",
    IsType( ThisItem, [@'Email Messages'] ), "Email Message",
    IsType( ThisItem, [@Chats] ), "Chat",
    "Unknown"
)
```

> [!div class="mx-imgBorder"]
> 電話の詳細情報を ![Expanded text プロパティ ](media/working-with-references/activitypointer-phonecall.png)

その結果、アプリにはアクティビティの完全な一覧が表示されます。 **[件名]** フィールドは、すべての種類のアクティビティについて表示されます。これは、数式が考慮するかどうかによって決まります。 把握しているアクティビティの種類については、各アクティビティに関する型名と種類固有の情報を表示できます。

> [!div class="mx-imgBorder"]
> さまざまな種類のアクティビティに関する情報を示す ![Completed 画面 ](media/working-with-references/activitypointer-complete.png)

## <a name="notes-entity"></a>Notes エンティティ

これまでは、すべての**関連**例はアクティビティに基づいていますが、 **note**エンティティは別のケースを表しています。

エンティティを作成するときに、添付ファイルを有効にすることができます。

> [!div class="mx-imgBorder"]
> エンティティの作成時に添付ファイルとメモを ![Enabling ](media/working-with-references/notes-entity.png)

添付ファイルを有効にするためのチェックボックスをオンにした場合は、次の図に示すように、note**エンティティと**の**関連**関係を作成します。

> [!div class="mx-imgBorder"]
> 一対多のリレーションシップを介したメモへのリレーションシップを示す ![Account エンティティ ](media/working-with-references/notes-relationships.png)

この違い以外に、アクティビティを使用するのと同じ方法で、**関連**ルックアップを使用します。 次の例のように、添付ファイルに対して有効になっているエンティティには、**メモ**と一対多の関係があります。

`First( Accounts ).Notes`

> [!NOTE]
> このドキュメントの執筆時点では、 **note**エンティティに**関連**する参照は使用できません。 **[関連]** フィールドに基づいて読み取りやフィルター処理を行うことはできません。また、 **Patch**を使用してフィールドを設定することもできません。
>
> ただし、逆**メモ**の一対多リレーションシップを使用できるので、添付ファイルが有効になっているレコードのメモの一覧をフィルター処理できます。 また、[**関連付け**](functions/function-relate-unrelate.md)関数を使用してレコードの**Notes**テーブルにメモを追加することもできますが、次の例のように、最初にメモを作成する必要があります。
>
>`Relate( ThisItem.Notes, Patch( Notes, Defaults( Notes ), { Title: "A new note" } ) )`

## <a name="activity-parties"></a>アクティビティパーティ

このドキュメントの執筆時点では、キャンバスアプリではアクティビティパーティはサポートされていません。