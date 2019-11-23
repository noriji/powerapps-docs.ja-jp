---
title: Replace および Substitute 関数 | Microsoft Docs
description: 構文を含む PowerApps の Replace および Substitute 関数の参照情報
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 12/02/2018
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: ff0e016f6ab1ad4f66651ccd3cfa2711f1d85a38
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/07/2019
ms.locfileid: "71992385"
---
# <a name="replace-and-substitute-functions-in-powerapps"></a>PowerApps の Replace および Substitute 関数
テキストの文字列の一部を別の文字列に置換します。

## <a name="description"></a>説明
**Replace** 関数は、開始位置と長さによって、置換するテキストを識別します。  

**Substitute** 関数は、文字列を照合することで、置換するテキストを識別します。 複数の一致が見つかった場合は、それらのすべてを置換するか、置き換えることができます。

1 つの文字列を渡すと、変更された文字列が戻り値として返されます。 文字列を含む単一列[テーブル](../working-with-tables.md)を渡すと、変更された文字列の単一列テーブルが戻り値として返されます。 複数列テーブルがある場合は、[テーブルの使用](../working-with-tables.md)に関するページの説明に従って、そのテーブルを単一列テーブルにすることができます。

## <a name="syntax"></a>構文
**Replace**( *String*, *StartingPosition*, *NumberOfCharacters*, *NewString* )

* *String* - 必須。 操作の対象となる文字列。
* *StartingPosition* - 必須。 置換を開始する文字の位置。 *String* の最初の文字の位置は 1 です。
* *NumberOfCharacters* - 必須。 *String* で置換する文字の数。
* *NewString* - 必須。 置換後の文字列。 この引数の文字数は、*NumberOfCharacters* 引数とは異なっていてもかまいません。

**Substitute**( *String*, *OldString*, *NewString* [, *InstanceNumber* ] )

* *String* - 必須。 操作の対象となる文字列。
* *OldString* - 必須。 置換の対象となる文字列。
* *NewString* - 必須。 置換後の文字列。 *OldString* と *NewString* の長さは異なっていてもかまいません。
* *InstanceNumber* - 省略可能。 この引数を使用して、 *String*に複数のインスタンスが含まれている場合に置き換える*oldstring*のインスタンスを指定します。 この引数を指定しない場合、すべてのインスタンスが置き換えられます。

**Replace**( *SingleColumnTable*, *StartingPosition*, *NumberOfCharacters*, *NewString* )

* *SingleColumnTable* - 必須。 操作対象となる複数の文字列の単一列テーブル。
* *StartingPosition* - 必須。 置換を開始する文字の位置。  テーブルの各文字列の最初の文字の位置は 1 です。
* *NumberOfCharacters* - 必須。 各文字列で置換する文字の数。
* *NewString* - 必須。  置換後の文字列。 この引数の文字数は、*NumberOfCharacters* 引数とは異なっていてもかまいません。

**Substitute**( *SingleColumnTable*, *OldString*, *NewString* [, *InstanceNumber* ] )

* *SingleColumnTable* - 必須。 操作対象となる複数の文字列の単一列テーブル。
* *OldString* - 必須。  置換の対象となる文字列。
* *NewString* - 必須。  置換後の文字列。 *OldString* と *NewString* の長さは異なっていてもかまいません。
* *InstanceNumber* - 省略可能。 この引数を使用して、 *String*に複数のインスタンスが含まれている場合に置き換える*oldstring*のインスタンスを指定します。 この引数を指定しない場合、すべてのインスタンスが置き換えられます。

## <a name="examples"></a>例

| 数式 | 説明 | 結果 |
|---------|-------------|--------|
| **Replace ("abcdefghijk"、&nbsp;6、&nbsp;5、&nbsp;"*")** | "Abcdefghijk" 内の5文字を、6番目の文字 ("f") で始まる1つの "*" 文字に置き換えます。 | "abcde...z * k" |
| **Replace (&nbsp;"2019"、&nbsp;3、&nbsp;2、&nbsp;"20"&nbsp;)** | "2019" の最後の2文字を "20" で置き換えます。 | "2020" |
| **Replace (&nbsp;"123456"、&nbsp;1、&nbsp;3、&nbsp;"_"&nbsp;)** | "123456" の最初の3文字を単一の "_" 文字に置き換えます。 | "456" | 
| **代替 (&nbsp;"Sales&nbsp;Data"、&nbsp;"Sales"、&nbsp;"Cost"&nbsp;)** | "Sales" の文字列 "Cost" に置き換えられます。 | "コストデータ" | 
| **代替 ("Quarter&nbsp;1,&nbsp;2018", "1", "2", 1)** | 4番目の引数 (*インスタンス番号*) に1が指定されているため、"1" の最初のインスタンスのみが "2" に置き換えられます。 |  "Quarter 2, 2018" |
| **代替 ("Quarter&nbsp;1,&nbsp;2011", "1", "2", 3)** | 4番目の引数 (*インスタンス番号*) に3が指定されているため、"1" の3番目のインスタンスのみが "2" に置き換えられます。 | "Quarter 1, 2012" |
| **代替 ("Quarter&nbsp;1,&nbsp;2011", "1", "2")** | 4番目の引数 (*インスタンス番号*) が指定されていないため、"1" のすべてのインスタンスを "2" に置き換えます。 | "Quarter 2, 2022" |
| **Replace (<br>[&nbsp;"Quarter&nbsp;1、&nbsp;2018"、<br>"Quarter&nbsp;2、&nbsp;2011"、<br>"Quarter&nbsp;4、&nbsp;2019"]、<br>9、1、"3")** | 単一列テーブルの各レコードの9番目の文字を "3" に置き換えます。 | [&nbsp;"Quarter&nbsp;3、&nbsp;2018"、<br>"Quarter&nbsp;3、&nbsp;2011"、<br>"Quarter&nbsp;3、&nbsp;2019"&nbsp;] |
| **代替 (<br>[&nbsp;"四半期&nbsp;1、&nbsp;2018"、<br>"Quarter&nbsp;1、&nbsp;2011"、<br>"Q1,&nbsp;2019"&nbsp;]、<br>"1"、"3"、1)** | 4番目の引数 (*インスタンス番号*) には値1が指定されているので、単一列テーブルの各レコードの "1" の最初のインスタンスのみが "3" と置き換えられます。 | [&nbsp;"四半期&nbsp;3、&nbsp;2018"、<br>"Quarter&nbsp;3、&nbsp;2011"、<br>"Q3,&nbsp;2019"&nbsp;] |
| **代替 (<br>[&nbsp;"四半期&nbsp;1、&nbsp;2018"、<br>"Quarter&nbsp;1、&nbsp;2011"、<br>"Q1、&nbsp;2019"&nbsp;]、<br>"1"、"3")** | 4番目の引数 (*インスタンス番号*) が指定されていないため、では、単一列テーブルの各レコードについて "1" のすべてのインスタンスが "3" に置き換えられます。 | [&nbsp;"四半期&nbsp;3、&nbsp;2038"、<br>"Quarter&nbsp;3、&nbsp;2033"、<br>"Q3,&nbsp;2039"&nbsp;] |  
 


