---
title: キャンバス アプリの変数について | Microsoft Docs
description: キャンバス アプリの状態、コンテキスト変数、およびコレクションを操作するための参照情報
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 02/28/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 036de37aa2593254d6ae665f8546fe4038dd922d
ms.sourcegitcommit: 7c1e70e94d75140955518349e6f9130ce3fd094e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/29/2019
ms.locfileid: "71994837"
---
# <a name="understand-canvas-app-variables-in-powerapps"></a>PowerApps のキャンバス アプリの変数について

Visual Basic や JavaScript などの別のプログラミング ツールを使ってきた方は、**変数はどこにあるのか**という疑問を抱くことでしょう。 PowerApps は若干異なり、別のアプローチが必要です。 キャンバス アプリをビルドする際に、変数の説明に進む代わりに、**Excel で何をしようとしているか**を考えてください。

他のツールでは、明示的に計算を実行し、その結果を変数に格納していたことでしょう。 ところが、PowerApps と Excel のどちらも、入力データが変更されると自動的に数式が再計算されます。そのため、通常は変数を作成したり更新したりする必要はありません。 可能な限りこの方法に従うことで、アプリをより簡単に作成、理解、維持することができます。

場合によっては、PowerApps で変数を使用する必要があります。これにより、[動作の数式](working-with-formulas-in-depth.md)を追加して Excel のモデルを拡張します。 これらの数式が実行されるのは、ユーザーがボタンを選択したときなどです。 動作の数式の中では、他の数式で使用する変数を設定すると便利なことがよくあります。

一般的には、変数の使用を避けてください。 ただし、変数を使わないと目的の動作が得られないこともあります。 変数は、値を設定する関数に表示されるときに、暗黙的に作成および型指定されます。 

## <a name="translate-excel-into-powerapps"></a>Excel を PowerApps に変換する

### <a name="excel"></a>Excel

それでは、Excel のしくみを確認しましょう。 セルには、数値や文字列などの値、または他のセルの値に基づく数式を含めることができます。 ユーザーがセルに別の値を入力すると、新しい値に応じてすべての数式が自動的に再計算されます。 この動作を実現するためにプログラミングは必要ありません。

次の例では、セル**A3**が数式**A1 + A2**に設定されています。 **A1**または**A2**が変更された場合、 **A3**は変更を反映するために自動的に再計算されます。 この動作では、数式自体の外部でコーディングを行う必要はありません。

![Excel の2つの数値の合計を再計算するアニメーション](media/working-with-variables/excel-recalc.gif)

Excel に変数がありません。 数式が含まれるセルの値は入力内容に基づいて変化しますが、数式の結果を記憶してそれをセルや他の場所に格納する方法はありません。 セルの値を変更すると、スプレッドシート全体が変更される可能性があり、それ以前に計算された値はすべて失われます。 Excel のユーザーは、セルをコピーして貼り付けることができますが、それはユーザーが手動で制御するものであり、数式では不可能です。

### <a name="powerapps"></a>PowerApps

PowerApps で作成したアプリの動作は、Excel と非常によく似ています。 セルを更新する代わりに、画面上の任意の場所にコントロールを追加し、数式で使用するために名前を付けることができます。

たとえば、 **TextInput1**と**TextInput2**という名前の **[ラベル](controls/control-text-box.md)** コントロールと、 **Label1**という名前の2つの **[テキスト入力](controls/control-text-input.md)** コントロールを追加することで、アプリで Excel の動作をレプリケートできます。 その後、 **Label1**の **[Text](controls/properties-core.md)** プロパティを**TextInput1 + TextInput2**に設定すると、 **TextInput1**と**TextInput2**に含まれるすべての数値の合計が自動的に表示されます。

![PowerApps の2つの数値の合計の計算](media/working-with-variables/recalc1.png)

**Label1**コントロールが選択され、画面の上部にある数式バーにその **[テキスト](controls/properties-core.md)** 式が表示されていることに注意してください。 ここで、数式が **TextInput1 + TextInput2** となっていることがわかります。 Excel ブック内のセル間に依存関係が作成されるのと同様に、この数式によってこれらのコントロール間に依存関係が作成されます。  **TextInput1**の値を変更してみましょう。

![PowerApps の2つの数値の合計を計算するアニメーション](media/working-with-variables/recalc2.gif)

**Label1**の数式が自動的に再計算され、新しい値が表示されます。

PowerApps では、数式を使用して、コントロールのプライマリ値だけでなく、書式設定などのプロパティも決定できます。 次の例では、ラベルの **[Color](controls/properties-color-border.md)** プロパティに設定された数式により、負の値は自動的に赤で表示されます。 **[If](functions/function-if.md)** 関数は Excel と非常によく似ています。

`If( Value(Label1.Text) < 0, Red, Black )`

![条件付き書式のアニメーション](media/working-with-variables/recalc-color.gif)

数式は、さまざまなシナリオで利用できます。

* デバイスの GPS を使用した場合、**Location.Latitude** と **Location.Longitude** を使用する数式によって、マップ コントロールに現在の位置を表示できます。  移動すると、マップによって位置が自動的に追跡されます。
* 他のユーザーが[データ ソース](working-with-data-sources.md)を更新できます。  たとえば、チームの他のメンバーが SharePoint リスト内の項目を更新する場合があります。  データ ソースを更新すると、依存するすべての数式が自動的に再計算され、更新されたデータが反映されます。 この例をさらに進めて、ギャラリーの **[Items](controls/properties-core.md)** プロパティを数式 **Filter( SharePointList )** に設定すると、新しくフィルター処理された[レコード](working-with-tables.md#records) セットが自動的に表示されます。

### <a name="benefits"></a>利点

数式をしたアプリの作成には多くの利点があります。

* Excel を知っていれば PowerApps もわかります。 モデルと数式の言語は同じです。
* 他のプログラミング ツールを使用したことがある場合は、これらの例を実現するためにどれだけの量のコードが必要になるかを考えてみてください。  Visual Basic では、各テキスト入力コントロールの変更イベント用にイベント ハンドラーを記述する必要があります。  このそれぞれで計算を実行するコードは冗長であり、不一致が生じる可能性があります。また、共通のサブルーチンを記述することが必要になる場合もあります。  PowerApps では、1 行の数式 1 つでこのすべての処理を実現しました。
* ここで、 **Label1**のテキストがどこから来ているかを理解するために、" **[テキスト](controls/properties-core.md)** " プロパティの式を正確に調べることができます。  ほかに、このコントロールのテキストを変更する方法はありません。  従来のプログラミング ツールでは、プログラムのどこからでも、任意のイベント ハンドラーまたはサブルーチンでラベルの値を変更できました。  これにより、変数がいつどこで変更されたかを追跡するのが難しくなります。
* ユーザーは、スライダー コントロールを変更した後に考えを変えた場合、スライダーを元の値に戻すことができます。  アプリでは以前と変わらず同じコントロールが表示されるため、まるで何も変わっていないかのように見えます。  "what if" を試したり要求したりした場合でも、Excel の場合と同様、派生的な問題は発生しません。  

一般的に、数式を使用して効果を得ることができれば楽になります。 PowerApps の数式エンジンをうまく利用しましょう。  

## <a name="know-when-to-use-variables"></a>変数を使用するタイミングを把握する

単純な加算器に変更を加えて、累計機能を備えた昔ながらの計算機のように動作するようにしましょう。 **[Add]** ボタンを選択すると、数値が累計に加算されます。 **[Clear]** ボタンを選択すると、累計が 0 にリセットされます。

| '95'5c | Description |
|----|----|
| <style>img {max width: none}</style> ![アプリには、テキスト入力コントロール、ラベル、2つのボタンがあり](media/working-with-variables/button-changes-state-1.png) | アプリが開始されると、実行中の合計は0になります。<br><br>赤い点は、ユーザーが**77**を入力したテキスト入力ボックスにユーザーの指を表します。 |
| ![テキスト入力コントロールに77が含まれており、[追加] ボタンが押されています。](media/working-with-variables/button-changes-state-2.png) | ユーザーは **[追加]** ボタンを選択します。 |
| ![合計が77で、別の77が追加されています](media/working-with-variables/button-changes-state-3.png) | 77が累計に追加されます。<br><br>ユーザーはもう一度 **[追加]** ボタンを選択します。 |
| ![合計は、クリアされる前の154です。](media/working-with-variables/button-changes-state-4.png) | 77はもう一度累計に追加され、結果は154になります。<br><br>ユーザーは **[クリア]** ボタンを選択します。 |
| ![合計がクリアされます。](media/working-with-variables/button-changes-state-5.png) | 実行中の合計が0にリセットされます。 |

ここで作成する計算機では、Excel に存在しない機能、つまりボタンを使用しています。 このアプリでは、数式だけを使用して累計を計算することはできません。なぜなら、値はユーザーが行う一連の操作によって異なるからです。 代わりに、累計を手動で記録して更新する必要があります。 ほとんどのプログラミング ツールでは、この情報を "*変数*" に格納します。

場合によっては、アプリが目的の動作を行うために変数が必要になります。  ただし、このアプローチには注意が必要です。

* 累計を手動で更新する必要があります。 この処理は自動再計算では実行されません。
* 累計は、他のコントロールの値に基づいて計算できません。 累計は、ユーザーが **[Add]** ボタンを選択した回数と、選択したときにテキスト入力コントロールに格納されていた値に基づきます。 ユーザーが 77 を入力した後で **[Add]** を 2 回選択したのか、加算する値に 24 と 130 を指定したのか、 合計が 154 になった後でその違いを見分けることはできません。
* 合計に対する変更は、異なる経路から生じている可能性があります。 この例では、 **[Add]** ボタンでも **[Clear]** ボタンでも合計を更新できます。 アプリが期待どおりに動作しない場合、どちらかのボタンに問題の原因があるのでしょうか。

## <a name="use-a-global-variable"></a>グローバル変数を使用する

計算機を作成するには、累計を保持する変数が必要です。 PowerApps で使用できる最も単純な変数は、*グローバル変数*です。  

グローバル変数は次のように機能します。

* **[Set](functions/function-set.md)** 関数を使用して、グローバル変数の値を設定します。  **Set( MyVar, 1 )** とすることで、グローバル変数 **MyVar** の値を **1** に設定します。
* **Set** 関数とともに使用した名前を参照すると、グローバル変数を使用できます。  この場合、**MyVar** は **1** を返します。
* グローバル変数は、文字列、数値、レコード、[テーブル](working-with-tables.md)など、すべての値を保持できます。

それでは、グローバル変数を使用して計算機を作り直してみましょう。

1. **TextInput1** という名前のテキスト入力コントロールと、**Button1** および **Button2** という名前の 2 つのボタンを追加します。

2. **Button1** の **[Text](controls/properties-core.md)** プロパティを **"Add"** に設定し、**Button2** の **Text** プロパティを **"Clear"** に設定します。

3. ユーザーが **[Add]** ボタンを選択するたびに累計を更新するために、 **[OnSelect](controls/properties-core.md)** プロパティを次の数式に設定します。

    **Set (RunningTotal、RunningTotal、TextInput1)**

    この数式が単に存在する場合は、 **+** 演算子により、数値を保持するグローバル変数として**runningtotal**が設定されます。 アプリの任意の場所で**Runningtotal**を参照できます。 ユーザーがこのアプリを開くたびに、 **Runningtotal**の初期値は*空白*になります。

    ユーザーが最初に **[追加]** ボタンを選択し、実行 を **[設定](functions/function-set.md)** すると、 **runningtotal**は**runningtotal + TextInput1**の値に設定されます。

    ![[追加] ボタンの OnSelect プロパティが Set 関数に設定されています。](media/working-with-variables/global-variable-1.png)

4. ユーザーが **[Clear]** ボタンを選択するたびに累計を **0** に設定するために、 **[OnSelect](controls/properties-core.md)** プロパティを次の数式に設定します。

    **Set( RunningTotal, 0 )**

    ![Clear ボタンの OnSelect プロパティが Set 関数に設定されています](media/working-with-variables/global-variable-2.png)

5. **[ラベル](controls/control-text-box.md)** コントロールを追加し、 **[Text](controls/properties-core.md)** プロパティを **RunningTotal** に設定します。

    この数式は自動的に再計算され、ユーザーが選択したボタンに基づいて変更される **RunningTotal** の値が表示されます。

    ![ラベルの Text プロパティは、変数の名前に設定されます。](media/working-with-variables/global-variable-3.png)

6. アプリをプレビューします。前述のように計算機が完成しました。 テキスト ボックスに数値を入力して **[追加]** ボタンを数回クリックします。 準備ができたら、Esc キーを押して作成環境に戻ります。

    ![テキスト入力コントロールには値が含まれ、ラベルには累計が含まれます。](media/working-with-variables/global-variable-4.png)

7. グローバル変数の値を表示するには、 **[ファイル]** メニューを選択し、左側のペインで **[変数]** を選択します。

    ![[ファイル] メニューの [変数] オプション](media/working-with-variables/global-variable-file-1.png)

8. 変数が定義されて使用されているすべての場所を表示するには、変数を選択します。

    ![変数が使用されている場所の一覧](media/working-with-variables/global-variable-file-2.png)

## <a name="types-of-variables"></a>変数の種類

PowerApps には、次の3種類の変数があります。

| 変数の種類 | 適用範囲 | Description | を確立する関数 |
| --- | --- | --- | --- |
| グローバル変数 |App |使い方が最も単純です。 数値、テキスト文字列、ブール値、レコード、テーブルなどを保持し、アプリ内のどこからでも参照できます。 |[**Set**](functions/function-set.md) |
| コンテキスト変数 |画面 |他の言語のプロシージャにパラメーターを渡す場合など、画面に値を渡すのに最適です。 は、1つの画面からのみ参照できます。 |[**UpdateContext**](functions/function-updatecontext.md)<br>[**Navigate**](functions/function-navigate.md) |
| コレクション |App |アプリ内のどこからでも参照できるテーブルを保持します。 全体として設定するのではなく、テーブルのコンテンツごとに変更できます。 後で使用するためにローカル デバイスに保存できます。 |[**Collect**](functions/function-clear-collect-clearcollect.md)<br>[**ClearCollect**](functions/function-clear-collect-clearcollect.md) |

## <a name="create-and-remove-variables"></a>変数の作成と削除

**Set**、 **updatecontext**、 **Navigate**、 **collect**、または**clearcollect**関数に出現すると、すべての変数が暗黙的に作成されます。 変数とその型を宣言するには、アプリ内の任意の場所で、これらの関数のいずれかにそれを含める必要があります。 これらの関数は変数を作成しません。変数に値を入力するだけです。 他のプログラミングツールの場合と同じように、変数を明示的に宣言することはできません。また、すべての型指定は使用法から暗黙的に宣言されます。

たとえば、 **Onselect**式が**Set (X, 1)** と等しいボタンコントロールがあるとします。 この数式は、 **X**を数値型の変数として設定します。 数式の中で**X**を数値として使用できます。アプリを開いた後、ボタンを選択する前に、その変数の値は*空白*になります。 このボタンを選択すると、 **X**の値が**1**になります。

別のボタンを追加し、その**Onselect**プロパティを**設定 (X、"Hello")** に設定した場合、型 (テキスト文字列) が前の**set** (number) の型と一致しないため、エラーが発生します。 変数のすべての暗黙的な定義は、型に同意する必要があります。 ここでも、数式に**X**と記述したのは、これらの数式のいずれかが実際に実行されていたためではなかったからです。

変数を削除するには、変数を暗黙的に設定する**Set**、 **updatecontext**、 **Navigate**、 **collect**、または**clearcollect**関数をすべて削除します。 これらの関数がない場合、変数は存在しません。 また、変数への参照は、エラーの原因になるため、削除する必要があります。

## <a name="variable-lifetime-and-initial-value"></a>変数の有効期間と初期値

すべての変数は、アプリの実行中にメモリに保持されます。 アプリが閉じられると、変数に保持されていた値は失われます。

**Patch**関数または**Collect**関数を使用して、データソースに変数の内容を格納できます。 [**SaveData**](functions/function-savedata-loaddata.md)関数を使用して、ローカルデバイスのコレクションに値を格納することもできます。

ユーザーがアプリを開くと、すべての変数の初期値は*空白*になります。

## <a name="reading-variables"></a>読み取り (変数を)

変数の名前を使用して、その値を読み取ります。 たとえば、次の式を使用して変数を定義できます。

`Set( Radius, 12 )`

次に、数値を使用できる場所であればどこにでも**Radius**を使用でき、 **12**に置き換えられます。

`Pi() * Power( Radius, 2 )`

コンテキスト変数にグローバル変数またはコレクションと同じ名前を指定すると、コンテキスト変数が優先されます。 ただし、あいまいさを解消する[演算子](functions/operators.md#disambiguation-operator) **@ [Radius]** を使用する場合は、グローバル変数またはコレクションを参照できます。

## <a name="use-a-context-variable"></a>コンテキスト変数を使用する

グローバル変数の代わりにコンテキスト変数を使用した計算機の作成方法を説明します。

コンテキスト変数のしくみは次のとおりです。

* コンテキスト変数を暗黙的に確立および設定するには、 **[Updatecontext](functions/function-updatecontext.md)** 関数または **[Navigate](functions/function-navigate.md)** 関数を使用します。 アプリが起動すると、すべてのコンテキスト変数の初期値は*空白*になります。
* コンテキスト変数は、レコードを使用して更新します。 他のプログラミング ツールでは、一般的に、"x = 1" のように、代入には "=" を使用します。 コンテキスト変数の場合は、代わりに **{ x: 1 }** を使用します。 コンテキスト変数を使用する場合は、record 構文を使用せずに名前を直接使用します。
* **[Navigate](functions/function-navigate.md)** 関数を使用して画面を表示する場合は、コンテキスト変数を設定することもできます。 画面がプロシージャまたはサブルーチンの一種であると考えられる場合、この方法は、他のプログラミングツールでのパラメーターの引き渡しに似ています。
* **[Navigate](functions/function-navigate.md)** を除き、コンテキスト変数は、名前を取得する場所である単一の画面のコンテキストに制限されます。 このコンテキスト以外でコンテキスト変数を使用または設定することはできません。
* コンテキスト変数では、文字列、数値、レコード、[テーブル](working-with-tables.md)など、任意の値を保持できます。

それでは、コンテキスト変数を使用して計算機を作り直してみましょう。

1. **TextInput1** という名前のテキスト入力コントロールと、**Button1** および **Button2** という名前の 2 つのボタンを追加します。

2. **Button1** の **[Text](controls/properties-core.md)** プロパティを **"Add"** に設定し、**Button2** の **Text** プロパティを **"Clear"** に設定します。

3. ユーザーが **[Add]** ボタンを選択するたびに累計を更新するために、 **[OnSelect](controls/properties-core.md)** プロパティを次の数式に設定します。

    **UpdateContext ({RunningTotal: RunningTotal + TextInput1})**

    この数式が単に存在する場合は、 **+** 演算子により、数値を保持するコンテキスト変数として**runningtotal**が設定されます。 この画面の任意の場所で、 **Runningtotal**を参照できます。 ユーザーがこのアプリを開くたびに、 **Runningtotal**の初期値は*空白*になります。

    ユーザーが初めて **[Add]** ボタンと **[updatecontext](functions/function-updatecontext.md)** を選択したときに、 **runningtotal**は**runningtotal + TextInput1**の値に設定されます。

    ![[追加] ボタンの OnSelect プロパティ](media/working-with-variables/context-variable-1.png)

4. ユーザーが **[Clear]** ボタンを選択するたびに累計を **0** に設定するために、 **[OnSelect](controls/properties-core.md)** プロパティを次の数式に設定します。

    **UpdateContext( { RunningTotal: 0 } )**

    ここでも、 **[UpdateContext](functions/function-updatecontext.md)** を数式 **UpdateContext( { RunningTotal: 0 } )** で使用します。

    ![Clear ボタンの OnSelect プロパティ](media/working-with-variables/context-variable-2.png)

5. **[ラベル](controls/control-text-box.md)** コントロールを追加し、 **[Text](controls/properties-core.md)** プロパティを **RunningTotal** に設定します。

    この数式は自動的に再計算され、ユーザーが選択したボタンに基づいて変更される **RunningTotal** の値が表示されます。

    ![ラベルの Text プロパティ](media/working-with-variables/context-variable-3.png)

6. アプリをプレビューします。前述のように計算機が完成しました。 テキスト ボックスに数値を入力して **[追加]** ボタンを数回クリックします。 準備ができたら、Esc キーを押して作成環境に戻ります。

    ![テキスト入力コントロールに値が表示され、ラベルに "累計" が表示されます。](media/working-with-variables/context-variable-4.png)

7. 画面に移動する際にコンテキスト変数の値を設定できます。 これはある画面から別の画面に "コンテキスト" または "パラメーター" を渡すのに役立ちます。 この手法をデモンストレーションするには、画面を挿入し、ボタンを挿入して、その**Onselect**プロパティを次の数式に設定します。

    **Navigate( Screen1, None, { RunningTotal: -1000 } )**

    ![ボタンの OnSelect プロパティ](media/working-with-variables/context-variable-5.png)

    Alt キーを押したまま、このボタンを選択して**Screen1**を表示し、コンテキスト変数**runningtotal**を-1000 に設定します。

    ![Screen1 が開かれています](media/working-with-variables/context-variable-6.png)

8. コンテキスト変数の値を表示するには、 **[ファイル]** メニューを選択し、左側のペインで **[変数]** を選択します。

    ![[ファイル] メニューの [変数] オプション](media/working-with-variables/context-variable-file-1.png)

9. コンテキスト変数が定義および使用されている場所を表示するには、コンテキスト変数を選択します。

    ![変数が使用されている場所の一覧](media/working-with-variables/context-variable-file-2.png)

## <a name="use-a-collection"></a>コレクションを使用する

最後に、コレクションを使用した計算機の作成方法を説明します。  コレクションは、変更が容易なテーブルを保持しているため、この計算機に値が入力されたときに、それぞれの値を "紙テープ" に記録するようにします。

コレクションのしくみは次のとおりです。

* コレクションを作成および設定するには、 **[ClearCollect](functions/function-clear-collect-clearcollect.md)** 関数を使用します。  代わりに **[Collect](functions/function-clear-collect-clearcollect.md)** 関数を使用できますが、実質的には、古い変数を置き換えるのではなく別の変数が必要になります。  
* コレクションは一種のデータ ソース、すなわちテーブルです。 コレクションの単一の値にアクセスするには、 **[First](functions/function-first-last.md)** 関数を使用し、結果のレコードから 1 つのフィールドを抽出します。 **[ClearCollect](functions/function-clear-collect-clearcollect.md)** で単一の値を使用した場合、これは次の例のように **Value** フィールドになります。<br>
**First(** *VariableName* **).Value**

それでは、コレクションを使用して計算機を作り直してみましょう。

1. **TextInput1** という名前の **[テキスト入力](controls/control-text-input.md)** コントロールと、**Button1** および **Button2** という名前の 2 つのボタンを追加します。

2. **Button1** の **[Text](controls/properties-core.md)** プロパティを **"Add"** に設定し、**Button2** の **Text** プロパティを **"Clear"** に設定します。

3. ユーザーが **[Add]** ボタンを選択するたびに累計を更新するために、 **[OnSelect](controls/properties-core.md)** プロパティを次の数式に設定します。

    **Collect( PaperTape, TextInput1.Text )**

    この数式が単に存在する場合、テキスト文字列の単一列テーブルを保持するコレクションとして**用紙テープ**が設定されます。 このアプリの任意の場所で、**用紙のテープ**を参照できます。 ユーザーがこのアプリを開くたびに、**用紙カセット**は空のテーブルになります。

    この数式を実行すると、コレクションの末尾に新しい値が追加されます。 1つの値を追加しているので、 **Collect**によって単一列テーブルに自動的に配置され、列の名前は value になります。この**値**は後で使用します。

    ![[追加] ボタンの OnSelect プロパティ](media/working-with-variables/papertape-1.png)

4. ユーザーが **[クリア]** ボタンを選択したときに用紙のテープを消去するには、 **[onselect](controls/properties-core.md)** プロパティを次の数式に設定します。

    **Clear( PaperTape )**

    ![Clear ボタンの OnSelect プロパティ](media/working-with-variables/papertape-2.png)

5. 累計を表示するために、ラベルを追加し、 **[Text](controls/properties-core.md)** プロパティを次の数式に設定します。

    **Sum( PaperTape, Value )**

    ![ラベルの Text プロパティ](media/working-with-variables/papertape-3.png)

6. 計算機を実行するために、F5 キーを押してプレビューを開き、テキスト入力コントロールに数値を入力して、ボタンを選択します。

    ![テキスト入力コントロールに値が表示され、ラベルに累計が示されます。](media/working-with-variables/papertape-run-1.png)

7. 既定のワークスペースに戻るには、Esc キーを押します。

8. 紙テープを表示するには、**データ テーブル** コントロールを挿入し、その **[Items](controls/properties-core.md)** プロパティを次の数式に設定します。

    **PaperTape**

    右側のウィンドウで、 **[値]** 列を選択して表示します。

    ![コレクションに追加された値を示すデータテーブル](media/working-with-variables/papertape-4.png)

9. コレクション内の値を確認するために、 **[ファイル]** メニューの **[コレクション]** を選択します。

    ![用紙テープコレクションのプレビュー](media/working-with-variables/papertape-file.png)

10. コレクションを格納および取得するには、2つのボタンコントロールを追加し、その**Text**プロパティを**読み込ん**で**保存**するように設定します。 **Load**ボタンの**onselect**プロパティを次の数式に設定します。

     **Clear( PaperTape ); LoadData( PaperTape, "StoredPaperTape", true )**

     **LoadData**によって格納された値がコレクションの末尾に追加されるため、まずコレクションをクリアする必要があります。

     ![[読み込み] ボタンの OnSelect プロパティ](media/working-with-variables/papertape-5.png)

11. **[保存]** ボタンの**onselect**プロパティを次の数式に設定します。

     **SaveData( PaperTape, "StoredPaperTape" )**

     ![[保存] ボタンの OnSelect * プロパティ](media/working-with-variables/papertape-6.png)

12. F5 キーを押してもう一度プレビューを表示し、テキスト入力コントロールに数値を入力してボタンを選択します。 **[保存]** ボタンを選択します。 アプリを閉じて再読み込みし、 **[読み込み]** ボタンを選択してコレクションを再読み込みします。

> [!NOTE]
> PowerApps Mobile の**SaveData**および**LoadData**関数。ただし、powerapps 用の web プレーヤーは PowerApps Studio ません。