---
title: UpdateContext 関数 | Microsoft Docs
description: 構文と例を含む PowerApps の UpdateContext 関数の参照情報
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 11/08/2015
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 7750ad239df87e99d2321be20293b64153110fc1
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/07/2019
ms.locfileid: "71991824"
---
# <a name="updatecontext-function-in-powerapps"></a>PowerApps の UpdateContext 関数
現在の画面の[コンテキスト変数](../working-with-variables.md#use-a-context-variable)を作成または更新します。

## <a name="overview"></a>概要
**UpdateContext** 関数を使用すると、コンテキスト変数を作成できます。コンテキスト変数とは、ユーザーがボタンを押した回数やデータ操作の結果など、一定の情報を一時的に格納する際に使用する変数です。

コンテキスト変数のスコープは 1 画面に限定されています。このため、別の画面のコンテキスト変数を参照する数式を作成することはできません。 他のプログラミング ツールの使用経験がある方は、コンテキスト変数をローカル変数とほぼ同じものだと考えてもよいでしょう。  アプリ全体で使用できるグローバル変数を操作するには、[**Set**](function-set.md) 関数を使用します。  

PowerApps では基本的に、ユーザーがアプリを操作すると、数式が自動的に再計算されます。  しかし、コンテキスト変数には再計算が実行されません。このため、コンテキスト変数を使うと、アプリの作成や理解が難しくなることがあります。  コンテキスト変数を使用する前に、[変数の利用](../working-with-variables.md)に関するページをもう一度確認してください。

## <a name="description"></a>説明
コンテキスト変数を作成または更新するには、[UpdateContext](../working-with-tables.md#records) 関数に**レコード**を 1 つ渡す必要があります。 各レコードでは、変数の名前の定義または照合に使用するデータとしての[列](../working-with-tables.md#columns)の名前と、その変数に設定する値を指定します。

* 以前に定義した変数の名前を指定した場合には、**UpdateContext** によって変数が指定された値に設定されます。
* まだ存在しない変数の名前を指定した場合には、**UpdateContext** ではその名前の変数を作成したうえで、その変数に対して指定された値を設定します。
* 以前に変数を定義していたものの、**UpdateContext** の数式の中でその変数を指定しなかった場合には、その変数の値は以前と同じになります。

コンテキスト変数は、**UpdateContext** または [**Navigate** 関数](function-navigate.md)を使用すると暗黙的に作成されます。  明示的な宣言は必要ありません。  **UpdateContext** と **Navigate** のコンテキスト変数への参照をすべて削除すると、コンテキスト変数は存在しなくなります。  変数をクリアするには、その値を [**Blank** 関数](function-isblank-isempty.md)の結果に設定します。

作成環境の [ファイル] メニューの [変数] ビューで、変数の値、定義、使用について確認できます。

数式でコンテキスト変数を参照するときは、その変数の列名を使用します。 たとえば、**UpdateContext( { ShowLogo: true } )** では、**ShowLogo** というコンテキスト変数を作成したうえで、値 **true** を設定します。 この関数を実行した後は、数式でこの **ShowLogo** という名前を指定することによって、このコンテキスト変数の値を使用できます。  **ShowLogo** を画像コントロールの **Visible** プロパティの数式として記述した場合には、このコンテキスト変数の値が **true** と **false** のどちらであるかに応じてコントロールの表示と非表示を切り替えることができます。

具体例はこのトピックで後ほど紹介しますが、コンテキスト変数には以下をはじめとするさまざまな情報を格納できます。

* 単一の値
* レコード
* テーブル
* オブジェクト参照
* 数式の結果

アプリが終了するまで、コンテキスト変数の値は保持されます。  コンテキスト変数を定義して、特定の画面についてその値を設定した場合には、ユーザーが別の画面に切り替えた場合でも、設定した情報がそのまま維持されます。  アプリを終了すると、コンテキスト変数の値は失われ、アプリが再読み込みされたときに再作成されます。  

コンテキスト変数はいずれも、そのスコープが 1 画面だけにとどまります。 ある画面についてコンテキスト変数を定義し、その値を別の画面から変更する場合には、 **[Navigate](function-navigate.md)** 関数に基づく数式を作成する必要があります。  または、グローバル変数を使用します。

**UpdateContext** には戻り値がないため、[動作の数式](../working-with-formulas-in-depth.md) の中でのみ使用できます。

## <a name="syntax"></a>構文
**UpdateContext**( *UpdateRecord* )

* *UpdateRecord* – 必須。 1 つ以上の列の名前と、その列の値を含むレコード。 指定した列と値それぞれについて、コンテキスト変数が作成または更新されます。

**UpdateContext**( { *ContextVariable1*: *Value1* [, *ContextVariable2*: *Value2* [, ... ] ] } )

* *ContextVariable1* - 必須。  作成または更新するコンテキスト変数の名前。
* *Value1* - 必須。  コンテキスト変数に割り当てる値。
* *ContextVariable2*: *Value2*, ... - 省略可能。 追加で作成または更新するコンテキスト変数とその値。

## <a name="examples"></a>例

| 数式 | 説明 | 結果 |
| --- | --- | --- |
| **UpdateContext( {&nbsp;Counter:&nbsp;1&nbsp;} )** |コンテキスト変数 **Counter** を作成または変更し、その値を **1** に設定します。 |**Counter** に値 **1** が設定されます。 この変数は、数式で名前 **Counter** を使用することによって参照できます。 |
| **UpdateContext( {&nbsp;Counter:&nbsp;2&nbsp;} )** |前の例のコンテキスト変数 **Counter** の値を **2** に設定します。 |**Counter** に値 **2** が設定されます。 |
| **UpdateContext( {&nbsp;Name:&nbsp;"Lily",&nbsp;Score:&nbsp;10&nbsp;} )** |**Name** と **Score** の 2 つのコンテキスト変数を作成または変更し、値をそれぞれ **Lily** と **10** に設定します。 |**Name** に値 **Lily**、**Score** に値 **10** が設定されます。 |
| **UpdateContext( {&nbsp;Person:&nbsp;{&nbsp;Name:&nbsp;"Milton", Address:&nbsp;"1&nbsp;Main&nbsp;St"&nbsp;}&nbsp;} )** |コンテキスト変数 **Person** を作成または変更し、その値をレコードに設定します。 このレコードには、**Name** と **Address** の 2 つの列が存在します。 **Name** 列の値は **Milton**、**Address** 列の値は **1 Main St** です。 |**Person** にレコード **{&nbsp;Name:&nbsp;"Milton", Address:&nbsp;"1&nbsp;Main&nbsp;St"&nbsp;}&nbsp;}** の値が設定されます。<br><br>このレコード全体を参照する場合には、名前 **Person** を使用します。このレコードの個別の列を参照する場合には、**Person.Name** または **Person.Address** を使用します。 |
| **UpdateContext( {&nbsp;Person: Patch(&nbsp;Person,&nbsp;{Address:&nbsp;"2&nbsp;Main&nbsp;St"&nbsp;}&nbsp;) }&nbsp;)** |**[Patch](function-patch.md)** 関数と連携してコンテキスト変数 **Person** の **Address** 列の値を **2 Main St** に設定します。 |**Person** にレコード **{&nbsp;Name:&nbsp;"Milton", Address:&nbsp;"2&nbsp;Main&nbsp;St"&nbsp;}&nbsp;}** の値が設定されます。 |

### <a name="step-by-step-example"></a>ステップバイステップの例
1. 既定の画面に **Source** という名前を付けてから、画面を 1 つ追加して、その画面の名前を **Target** に設定します。
2. **Source** 画面にボタンを 2 つ追加し、その一方の **[Text](../controls/properties-core.md)** プロパティに「**English**」、もう一方に「**Spanish**」を、それぞれ入力します。
3. **English[ ボタンの ](../controls/properties-core.md)** OnSelect プロパティに、次の式を設定します。<br>**Navigate(Target, ScreenTransition.Fade, {Language:"English"})**
4. **Spanish[ ボタンの ](../controls/properties-core.md)** OnSelect プロパティを次の数式に設定します。<br>**Navigate(Target, ScreenTransition.Fade, {Language:"Spanish"})**
5. **Target** 画面にラベルを追加し、その **[Text](../controls/properties-core.md)** プロパティを次の式に設定します。<br>**If(Language="English", "Hello!", "Hola!")**
6. **Target** 画面の **[挿入]** タブで **[図形]** を選択し、戻る矢印を選択します。
7. 戻る矢印の **[OnSelect](../controls/properties-core.md)** プロパティを次の式に設定します。<br>**Navigate(Source, ScreenTransition.Fade)**
8. **Source** 画面で F5 キーを押し、いずれかの言語のボタンを選択します。

    **Target** 画面に、選択した場ボタンに対応する言語のラベルが表示されます。
9. 戻る矢印を選択して **Source** 画面に戻り、もう一方の言語のボタンを選択します。

    **Target** 画面に、選択した場ボタンに対応する言語のラベルが表示されます。
10. Esc キーを押して既定のワークスペースに戻ります。

[その他の例](../add-screen-context-variables.md)

