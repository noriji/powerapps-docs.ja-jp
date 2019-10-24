---
title: Concat および Concatenate 関数 | Microsoft Docs
description: 構文と例を含む PowerApps の Concat および Concatenate 関数の参照情報
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 05/23/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 0a56230539990ce51cc9270f71d8c2b7c9a1db73
ms.sourcegitcommit: 57b968b542fc43737330596d840d938f566e582a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2019
ms.locfileid: "71992894"
---
# <a name="concat-and-concatenate-functions-in-powerapps"></a>PowerApps の Concat および Concatenate 関数

テキストの個々の文字列および[テーブル](../working-with-tables.md)内の文字列を連結します。

## <a name="description"></a>Description

**Concatenate** 関数は、個々の文字列の組み合わせおよび文字列の単一列テーブルを連結します。 この関数を個々の文字列で使用する場合は、 **&** [演算子](operators.md)を使用することと同じです。

**Concat** 関数は、テーブルのすべての[レコード](../working-with-tables.md#records)に適用される数式の結果を連結して、単一の文字列を生成します。 この関数は、 **[Sum](function-aggregates.md)** 関数が数値をまとめるように、テーブルの文字列をまとめます。

[!INCLUDE [record-scope](../../../includes/record-scope.md)]

文字列を部分文字列のテーブルに分割するには、 [**split**](function-split.md)関数または[**matchall**](function-ismatch.md)関数を使用します。

## <a name="syntax"></a>構文

**Concat**( *Table*, *Formula* )

- *Table* - 必須。  操作の対象となるテーブル。
- *Formula* - 必須。  テーブルのレコードに適用する数式。

**Concatenate**( *String1* [, *String2*, ...] )

- *String(s)* - 必須。  個々の文字列の組み合わせまたは文字列の単一列テーブル。

## <a name="examples"></a>例

このセクションの例では、次のグローバル変数を使用します。

- **FirstName** = "Jane"
- **LastName** = "Doe"
- **Products**  = 、2つの列と4つの行で ![Table ](media/function-concatenate/products.png)

アプリでこれらのグローバル変数を作成するには、[**ボタン**](../controls/control-button.md)コントロールを挿入し、その**onselect**プロパティを次の数式に設定します。

```powerapps-dot
Set( FirstName, "Jane" ); Set( LastName, "Doe" );
Set( Products,
    Table(
        { Name: "Violin", Type: "String" },
        { Name: "Cello", Type: "String" },
        { Name: "Trumpet", Type: "Wind" }
    )
)
```

(Alt キーを押しながらクリックして) ボタンを選択します。

### <a name="concatenate-function-and-the--operator"></a>連結関数と & 演算子

これらの例では、[**ラベル**](../controls/control-text-box.md)コントロールの**Text**プロパティを、次の表の最初の列の数式に設定します。

| 数式 | Description | 結果 |
|---------|-------------|--------|
| **連結 (&nbsp;LastName、&nbsp; "、&nbsp;"、&nbsp;FirstName &nbsp;)** | **LastName**の値、文字列 **","** (コンマの後にスペースが続く)、および**FirstName**の値を連結します。 | "Doe, &nbsp;Jane" |
| **LastName &nbsp; & &nbsp; ", &nbsp;" &nbsp; & &nbsp;FirstName** | 関数の代わりに **&** 演算子を使用する点を除いて、前の例と同じです。 | "Doe, &nbsp;Jane" |
| **連結 (&nbsp;FirstName、&nbsp; "&nbsp;"、&nbsp;LastName &nbsp;)** | **FirstName**の値、文字列 **""** (1 つのスペース)、および**LastName**の値を連結します。 | "Jane &nbsp;Doe" |
| **FirstName &nbsp; & &nbsp; "&nbsp;" &nbsp; & &nbsp;LastName** | 前の例と同じですが、関数の代わりに **&** 演算子を使用します。 | "Jane &nbsp;Doe" |

### <a name="concatenate-with-a-single-column-table"></a>単一列テーブルと連結する

この例では、空の垂直の[**ギャラリー**](../controls/control-gallery.md)コントロールを追加し、その**Items**プロパティを次の表の数式に設定してから、ギャラリーテンプレートにラベルを追加します。

| 数式 | Description | 結果 |
|---------|-------------|--------|
| **連結 ("Name: &nbsp;", &nbsp;Products. Name, ", &nbsp;Type: &nbsp;", &nbsp;Products)** | **Products**テーブル内の各レコードについて、は文字列 **"name:"** 、製品名、文字列 **"、型:"** 、および製品の種類を連結します。  | ![製品の表](media/function-concatenate/single-column.png) |

### <a name="concat-function"></a>Concat 関数

これらの例では、ラベルの**Text**プロパティを、次の表の最初の列の数式に設定します。

| 数式 | Description | 結果 |
|---------|-------------|--------|
| **Concat (Products、Name & ",")** | **製品**のレコードごとに式**名 & ","** を評価し、結果を連結して1つのテキスト文字列にします。  | "Violin, &nbsp;Cello, &nbsp;Trumpet, &nbsp;" |
| **Concat (Filter (&nbsp;Products、&nbsp;Type &nbsp; = &nbsp; "String" &nbsp;)、Name & ",")** | 式の**名前 & "," を**評価し、フィルターの**種類が "String"** である**製品**のレコードごとに、結果を1つのテキスト文字列に連結します。   | "Violin, &nbsp;Cello, &nbsp;" |

### <a name="trimming-the-end"></a>終了のトリミング

最後の2つの例には、結果の末尾に "," が追加されています。 関数は、テーブル内のすべてのレコードの**名前**値に、最後のレコードを含めてコンマとスペースを追加します。

場合によっては、これらの余分な文字は問題になりません。 たとえば、ラベルに結果を表示した場合、1つのスペースの区切り記号は表示されません。 これらの余分な文字を削除する場合は、 [**Left**](function-left-mid-right.md)関数または[**Match**](function-ismatch.md)関数を使用します。

これらの例では、ラベルの**Text**プロパティを、次の表の最初の列の数式に設定します。

| 数式 | Description | 結果 |
|---------|-------------|--------|
| **Left (Concat (&nbsp;Products、&nbsp;Name &nbsp; & &nbsp; "、&nbsp;" &nbsp;)、Len (&nbsp;Concat (&nbsp;Products、0Name 1 2 3 "、4" 5) 6) 7t_18 92)** | **Concat**の結果を返しますが、余分な区切り記号を形成する最後の2文字を削除します。 | "Violin, &nbsp;Cello, &nbsp;Trumpet" |
| **Match (Concat (&nbsp;Products、&nbsp;Name &nbsp; & &nbsp; "、&nbsp;" &nbsp;)、"^ (?&lt;trim &gt;. *)、0 $ ")。 trim** | 文字列の先頭から末尾 ($) までの**Concat**の文字を返しますが、末尾には不要なコンマとスペースは含まれません。 | "Violin, &nbsp;Cello, &nbsp;Trumpet" |

### <a name="split-and-matchall"></a>Split と MatchAll

Separator**を区切り記号と共に**使用した場合は、 **Split**関数と**matchall**関数を組み合わせることで、操作を元に戻すことができます。

これらの例では、空白の垂直方向のギャラリーを追加し、その**Items**プロパティを次の表の数式に設定してから、ギャラリーテンプレートにラベルを追加します。

| 数式 | Description | 結果 |
|---------|-------------|--------|
| **Split (Concat (&nbsp;Products、&nbsp;Name &nbsp; & &nbsp; "、&nbsp;" &nbsp;)、"、")** | テキスト文字列を区切り記号 **","** で分割します。 文字列はコンマとスペースで終わります。そのため、結果の最後の行は空の文字列になります。  | ![Table](media/function-concatenate/split.png) |
| **MatchAll (Concat (&nbsp;Products、&nbsp;Name &nbsp; & &nbsp; "、&nbsp;" &nbsp;)、"[^ \s,] +")。FullMatch** | スペースやコンマ以外の文字に基づいてテキスト文字列を分割します。 この数式は、文字列の末尾にある余分なコンマとスペースを削除します。 | ![Table](media/function-concatenate/matchall.png)