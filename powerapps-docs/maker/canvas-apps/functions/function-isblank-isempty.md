---
title: Blank、Coalesce、IsBlank、および IsEmpty 関数 | Microsoft Docs
description: 構文と例を含む PowerApps の Blank、Coalesce、IsBlank、および IsEmpty 関数の参考情報
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.component: canvas
ms.date: 08/27/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: d932d43bd9474f3cd7ca63ef0ef0a51a9e74ca91
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/07/2019
ms.locfileid: "71984734"
---
# <a name="blank-coalesce-isblank-and-isempty-functions-in-powerapps"></a>PowerApps の Blank、Coalesce、IsBlank、および IsEmpty 関数
値が空白であるかどうか、または、[テーブル](../working-with-tables.md)に[レコード](../working-with-tables.md#records)が含まれていないかどうかをテストし、*空白*の値を作成する方法を提供します。

## <a name="overview"></a>概要
"*空白*" は、"値がない" または "不明な値" の場合のプレースホルダーです。  たとえば、 **[コンボボックス](../controls/control-combo-box.md)** コントロールの**選択さ**れたプロパティは、ユーザーが選択を行っていない場合は*空白*になります。 多くのデータソースは、NULL 値を格納して返すことができます。これは、PowerApps では*空白*として表されます。

PowerApps では、プロパティまたは計算された値を*空白*にすることができます。  たとえばブール値は通常、**true** と **false** のいずれかの値になります。  ただし、これらの2つに加えて、状態が不明であることを示す*空白*にすることもできます。  これは、Microsoft Excel に似ています。ワークシートセルは、内容のない空白として開始されますが、値**TRUE**または**FALSE** (その他) を保持できます。 いつでも、セルの内容を消去して、*空白*の状態に戻すことができます。

*空の文字列*は、文字を含まない文字列を参照します。  [ **Len**関数](function-len.md)は、このような文字列に対して0を返します。この関数は、`""`間に何も含まれない2つの二重引用符で記述できます。  コントロールとデータソースの中には、"値なし" の条件を示すために空の文字列を使用するものがあります。  アプリの作成を簡単にするために、 **Isblank**関数と**合体**関数は、*空白*値と空の文字列の両方をテストします。    

**IsEmpty**関数のコンテキストでは、*空*はレコードを含まないテーブルに固有です。 テーブル構造は完全で、[列](../working-with-tables.md#columns)の名前は付いているものの、テーブル内にデータがありません。 最初は空だったテーブルにレコードを追加して空でない状態にした後で、レコードを削除してもう一度空にすることができます。

> [!NOTE]
> 移行期間中です。  これまでは、エラーを報告するために*空白*も使用されているので、有効な "no value" をエラーから区別できません。  このため、現時点では、*空白*値の格納はローカルコレクションでのみサポートされています。  [ファイル] メニューの [アプリの設定]、[詳細設定]、[試験的な機能] の順に "数式レベルのエラー管理" の試験的な機能を有効にすると、他のデータソースに*空白*値を格納できます。  現在、この機能を完了するために積極的に取り組んでおり、エラーからの*空白*値の適切な分離を完了しています。

## <a name="description"></a>説明
**空白**関数は、"*空白*" の値を返します。 この関数を使用して、これらの値をサポートするデータ ソースに NULL 値を格納して、フィールドから値を効率的に削除します。

**Isblank**関数は、*空白*の値または空の文字列をテストします。  テストには、アプリケーションの作成を容易にする空の文字列が含まれています。一部のデータソースとコントロールでは、値が存在しない場合に空の文字列が使用されるためです。  特別に*空*の値をテストするには、 **isblank**ではなく `if( Value = Blank(), ...` を使用します。

**合体**関数は、引数を順番に評価し、*空白*または空の文字列ではない最初の値を返します。  この関数を使用すると、*空白*の値または空の文字列を別の値に置き換えることができます。ただし、*空白*でも空でもない文字列値は変更されません。  すべての引数が*空白*または空の文字列の場合、関数は*空白*を返します。これにより、空の文字列*を空の値に*変換するための**適切な方法を作成でき**ます。  **Coalesce** のすべての引数は同じ型である必要があります。たとえば、数値とテキスト文字列を混在させることはできません。  

`Coalesce( value1, value2 )` は、より簡潔な `If( Not IsBlank( value1 ), value1, Not IsBlank( value2 ), value2 )` であり、 **value1**と**value2**は2回評価される必要はありません。  [ **If**関数](function-if.md)は、ここに示すような "else" 式がない場合は、*空白*を返します。

**IsEmpty** 関数は、テーブル内にレコードがあるかどうかをテストします。 これは、 **[CountRows](function-table-counts.md)** 関数を使用してゼロの有無をチェックするのと同じことです。 **IsEmpty** は、 **[Errors](function-errors.md)** 関数と組み合わせることで、データソース エラーのチェックに使用できます。

**IsBlank** と **IsEmpty** のどちらの関数の戻り値も、ブール値の **true** または **false** です。

## <a name="syntax"></a>構文
**空白**()

**Coalesce**(*Value1* [, *Value2*, ... ])

* *Value(s)* – 必須。 テストする値。  各値は、空で*はなく空*の文字列ではない値が見つかるまで順番に評価されます。  この時点より後の値は評価されません。  

**IsBlank**( *Value* )

* *Value* – 必須。 *空白*の値または空の文字列をテストする値。

**IsEmpty**( *Table* )

* *Table* - 必須。 レコードの有無をテストするテーブル。

## <a name="examples"></a>例
### <a name="blank"></a>空白
> [!NOTE]
> 現時点で、次の例はローカル コレクションでのみ機能します。  [ファイル] メニューの [アプリの設定]、[詳細設定]、[試験的な機能] の順に "数式レベルのエラー管理" の試験的な機能を有効にすると、他のデータソースに*空白*値を格納できます。  現在、この機能を完了するために積極的に取り組んでおり、エラーからの*空白*値の分離を完了しています。

1. アプリを最初から作成し、**ボタン** コントロールを追加します。
2. ボタンの **[OnSelect](../controls/properties-core.md)** プロパティを次の数式に設定します。

    ```powerapps-dot
    ClearCollect( Cities, { Name: "Seattle", Weather: "Rainy" } )
    ```
3. アプリをプレビューし、追加したボタンをクリックまたはタップして、プレビューを終了します。  
4. **[ファイル]** メニューの **[コレクション]** をクリックまたはタップします。

     **[Cities]** (都市) コレクションが表示され、"Seattle" および "Rainy" の 1 つのレコードが表示されます。

    ![天気が Rainy (雨) の Seattle (シアトル) を示すコレクション](./media/function-isblank-isempty/seattle-rainy.png)
5. 戻る矢印をクリックまたはタップして、既定のワークスペースに戻ります。
6. **ラベル** コントロールを追加し、その **Text** プロパティを次の数式に設定します。

    ```powerapps-dot
    IsBlank( First( Cities ).Weather )
    ```

    **[Weather]** (天気) フィールドに値 ("Rainy" (雨)) が含まれているため、ラベルには **false** と表示されます。
7. 2 つ目のボタンを追加し、その **OnSelect** プロパティを次の数式に設定します。

    ```powerapps-dot
    Patch( Cities, First( Cities ), { Weather: Blank() } )
    ```
8. アプリをプレビューし、追加したボタンをクリックまたはタップして、プレビューを終了します。  

    **Cities (都市)** の最初のレコードの **[Weather]** (天気) フィールドは、"*空白*" に置き換えられ、そこに設定されていた "Rainy" は削除されます。

    ![[Weather] (天気) フィールドが空白の、Seattle を示すコレクション](./media/function-isblank-isempty/seattle-blank.png)

    **[Weather]** (天気) フィールドに値が含まれていないため、ラベルには **true** と表示されます。

### <a name="coalesce"></a>Coalesce

| 数式 | 説明 | 結果 |
| --- | --- | --- |
| **合体 (&nbsp;Blank ()、&nbsp;1&nbsp;)** |**空白**関数からの戻り値をテストします。常に "*空白*" の値が返されます。 最初の引数が*空*であるため、*空白*以外の文字列が見つかるまで、次の引数が評価されます。 |**1** |
| **合体 ("", 2)** |空の文字列である最初の引数をテストします。 最初の引数は空の文字列であるため、*空でない値と*空でない文字列が見つかるまで、次の引数を評価し続けます。 |**2** |
| **合体 (Blank ()、""、Blank ()、""、3、4)** |**合体**は引数リストの先頭から開始し、各引数は、*空白*以外の値と空でない文字列が見つかるまで順番に評価されます。  この場合、最初の4つの引数はすべて*空白*または空の文字列を返します。そのため、評価は5番目の引数に続きます。 5番目の引数は*空白*でも空でもない文字列であるため、ここでは評価を停止します。 5 番目の引数の値が返され、6 番目の引数は評価されません。 |**3** |
| **合体 ("")** | 空の文字列である最初の引数をテストします。 最初の引数は空の文字列であり、引数がそれ以上ないため、関数は*空白*を返します。   |"*空白*" |

### <a name="isblank"></a>IsBlank
1. アプリを最初から作成し、テキスト入力コントロールを追加して **FirstName** という名前を付けます。
2. ラベルを追加し、その **[Text](../controls/properties-core.md)** プロパティを次の数式に設定します。

    ```powerapps-dot
    If( IsBlank( FirstName.Text ), "First Name is a required field." )
    ```

    既定では、テキスト入力コントロールの **[Text](../controls/properties-core.md)** プロパティは **"Text input"** に設定されています。 このプロパティには値が含まれており、空白ではないため、ラベルにはメッセージが表示されません。
3. テキスト入力コントロールから、スペースを含めたすべての文字を削除します。

    **[Text](../controls/properties-core.md)** プロパティには文字が含まれなくなったため、空の文字列になり、 **Isblank (FirstName)** は**true**になります。 必須フィールドのメッセージが表示されます。

他のツールを使用して検証を実行する方法については、 **[Validate](function-validate.md)** 関数と[データ ソースの操作方法](../working-with-data-sources.md)をご確認ください。  

他には次のような例があります。

| 数式 | 説明 | 結果 |
| --- | --- | --- |
| **IsBlank (&nbsp;Blank ()&nbsp;)** |**空白**関数からの戻り値をテストします。常に "*空白*" の値が返されます。 |**true** |
| **IsBlank( "" )** |文字が含まれていない文字列。 |**true** |
| **IsBlank( "Hello" )** |1 つ以上の文字が含まれている文字列。 |**false** |
| **IsBlank( *AnyCollection* )** |[コレクション](../working-with-data-sources.md#collections)が存在するため、レコードがなくとも空白ではありません。 空のコレクションの有無をチェックするには、代わりに **IsEmpty** を使用します。 |**false** |
| **IsBlank( Mid( "Hello", 17, 2 ) )** |**[Mid](function-left-mid-right.md)** の開始文字が文字列の範囲外になっています。  そのため、空の文字列が返されます。 |**true** |
| **IsBlank( If( false, false ) )** |**ElseResult[ がない ](function-if.md)** If 関数。  条件が常に **false** になるため、この **[If](function-if.md)** は常に "*空白*" を返します。 |**true** |

### <a name="isempty"></a>IsEmpty
1. アプリを最初から作成し、**ボタン** コントロールを追加します。
2. ボタンの **[OnSelect](../controls/properties-core.md)** プロパティを次の数式に設定します。

    **Collect( IceCream, { Flavor: "Strawberry", Quantity: 300 }, { Flavor: "Chocolate", Quantity: 100 } )**
3. アプリをプレビューし、追加したボタンをクリックまたはタップして、プレビューを終了します。  

    **IceCream** という名前のコレクションが作成されます。このデータには、次のデータが含まれます。

    ![](media/function-isblank-isempty/icecream-strawberry-chocolate.png)

    このコレクションには 2 つのレコードがあり、空ではありません。 **IsEmpty( IceCream )** は **false** を返し、**CountRows( IceCream )** は **2** を返します。
4. 2 つ目のボタンを追加し、その **[OnSelect](../controls/properties-core.md)** プロパティを次の数式に設定します。

    **Clear( IceCream )**
5. アプリをプレビューし、2 つ目のボタンをクリックまたはタップして、プレビューを終了します。  

    これでコレクションは空になりました。

    ![](media/function-isblank-isempty/icecream-clear.png)

    **[Clear](function-clear-collect-clearcollect.md)** 関数でコレクションからすべてのレコードが削除され、コレクションは空になっています。 **IsEmpty( IceCream )** は **true** を返し、**CountRows( IceCream )** は **0** を返します。

以下の例のように、**IsEmpty** を使用して、計算されたテーブルが空かどうかをテストすることもできます。

| 数式 | 説明 | 結果 |
| --- | --- | --- |
| **IsEmpty( [&nbsp;1,&nbsp;2,&nbsp;3 ] )** |単一列テーブルに 3 つのレコードが含まれており、テーブルは空ではありません。 |**false** |
| **IsEmpty( [&nbsp;] )** |単一列テーブルにレコードが含まれておらず、テーブルは空です。 |**true** |
| **IsEmpty( Filter( [&nbsp;1,&nbsp;2,&nbsp;3&nbsp;], Value > 5 ) )** |単一列テーブルに 5 より大きい値が含まれていません。  フィルター処理後のテーブルにはレコードが含まれておらず、テーブルは空です。 |**true** |

