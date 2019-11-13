---
title: And 関数、Or 関数、Not 関数 | Microsoft Docs
description: 構文と例を含む PowerApps の And 関数、Or 関数、Not 関数の参照情報
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
ms.openlocfilehash: a2b04e6a752ade561ec1b95658bcacda759b1a1c
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/07/2019
ms.locfileid: "71992563"
---
# <a name="and-or-and-not-functions-in-powerapps"></a>PowerApps の And 関数、Or 関数、Not 関数

比較とテストの結果を操作するためによく使用される、ブール値の論理関数について説明します。

## <a name="description"></a>説明

**And** 関数は、すべての引数が **true** の場合に **true** を返します。

**Or** 関数は、引数のいずれかが **true** の場合に **true** を返します。

**Not** 関数は、引数が **false** の場合は **true** を、引数が **true** の場合は **false** を返します。

これらの関数は、Excel の場合と同じように動作します。 また、Visual Basic または JavaScript 構文を使用して、これらの同じ操作を実行するために[演算子](operators.md)を使用することもできます。

| 関数の表記 | Visual Basic 演算子の表記 | JavaScript 演算子の表記 |
| -------------|------------|--------|
| **And (x, y)** | **x と y** | **x & & y** |
| **Or (x, y)** | **x または y** | **x &#124; &#124; y** |
| **Not (x)** | **X 以外** | **!閉じる** |

これらの関数では論理値が扱われます。 数値または文字列を直接渡すことはできません。代わりに、比較またはテストを行う必要があります。 たとえば、この論理式**x > 1**は、 **x**が**1**より大きい場合はブール値**true**に評価されます。 **X**が**1**未満の場合、式は**false**と評価されます。

## <a name="syntax"></a>構文

**And**( *LogicalFormula1*, *LogicalFormula2* [, *LogicalFormula3*, ... ] )<br>
**Or**( *LogicalFormula1*, *LogicalFormula2* [, *LogicalFormula3*, ... ] )<br>
**Not**( *LogicalFormula* )

- *LogicalFormula(s)* - 必須。  評価と処理の対象となる論理式。

## <a name="examples"></a>例

このセクションの例では、次のグローバル変数を使用します。

- ** = ** *false*
- **b** = *true*
- **x** = 10
- **y** = 100
- **s** = "Hello World"

アプリでこれらのグローバル変数を作成するには、[**ボタン**](../controls/control-button.md)コントロールを挿入し、その**onselect**プロパティを次の数式に設定します。

```powerapps-dot
Set( a, false ); Set( b, true ); Set( x, 10 ); Set( y, 100 ); Set( s, "Hello World" )
```

(Alt キーを押しながらクリックして) ボタンを選択し、[**ラベル**](../controls/control-text-box.md)コントロールの**Text**プロパティを次の表の最初の列の数式に設定します。

| 数式 | 説明 | 結果 |
|---------|-------------|--------|
| **And (a, b)** | **A**と**b**の値をテストします。  引数の1つが*false*であるため、関数は*false*を返します。 | *false* |
| **a および b** | 前の例と同じ Visual Basic 表記法を使用します。 | *false* |
| **a & & b** | 前の例と同じです。 JavaScript 表記を使用します。 | *false* |
| **または (a, b)** | **A**と**b**の値をテストします。 引数のいずれかが*true*であるため、関数は*true*を返します。 | *true* |
| **a または b** | 前の例と同じ Visual Basic 表記法を使用します。 | *true* |
| **a &#124; &#124; b** | 前の例と同じです。 JavaScript 表記を使用します。 | *true* |
| **Not (a)** | の**値をテストします。** 引数が*false*の場合、関数は逆の結果を返します。 | *true* |
| **ではありません。** | 前の例と同じ Visual Basic 表記法を使用します。 | *true* |
| **!ある** | 前の例と同じです。 JavaScript 表記を使用します。 | *true* |
| **Len (&nbsp;s&nbsp;)&nbsp;<&nbsp;20 および&nbsp;Not Blank (&nbsp;s&nbsp;)** &nbsp; | の長さが20未満であるかどうか、および**空白** **の値**でないかどうかをテストします。 長さが20未満で、値が空白ではありません。 したがって、結果は*true*になります。 | *true* |
| **または (&nbsp;Len (&nbsp;s&nbsp;)&nbsp;<&nbsp;10、x&nbsp;<&nbsp;100、y&nbsp;<&nbsp;100&nbsp;)** | **S**の長さが10未満であるかどうか、 **x**が100未満であるかどうか、 **y**が100未満かどうかをテストします。 1番目と3番目の引数は false ですが、2番目の引数は true です。 したがって、この関数は*true*を返します。 | *true* |
| **Not IsBlank (&nbsp;s&nbsp;)** | **S**が*空白*であるかどうかをテストします。 *false*を返します。 **Not**は、この結果の逆を返します。これは*true*です。 | *true* |