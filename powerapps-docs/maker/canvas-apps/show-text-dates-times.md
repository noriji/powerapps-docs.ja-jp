---
title: キャンバス アプリにテキスト、日付、および時刻を表示する | Microsoft Docs
description: PowerApps で、キャンバス アプリにテキスト、日付、および時刻を表示します
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 10/16/2016
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: fdaf242dec8500f1f50603e5ccb981b12197e2da
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2019
ms.locfileid: "73541762"
---
# <a name="show-text-dates-and-times-in-powerapps"></a>PowerApps でテキスト、日付、および時刻を表示する
PowerApps で、日付と時刻をキャンバス アプリに追加し、その書式を設定することによって、必要な部分だけを表示したりロケールを反映したりすることができます。 また、2 つの日付間の時間を計算したり、指定した日付から一定時間前または後の日付を計算したりすることも可能です。 さらに、日付を変換して年と月と日の要素に分解したり、逆に年と月と日の要素から日付に変換したりすることができます。時刻も同様です。時と分と秒の要素に分解したり、時と分と秒の要素から時刻に変換したりすることができます。

たとえば、株式取引やクライアントとのミーティングに関するデータを追加するとしましょう。データは、ユーザーや外部ソースから取得する場合もあれば、PowerApps で作成された別のアプリから取得する場合もあります。 そのデータにミリ秒単位の時刻が含まれていれば、わかりやすくするために、最も近い分単位に丸めることができます。 重要なマイルストーンまでの残り日数を計算するとします。 クライアントとのミーティングを 5 日おきにスケジューリングする場合は、それらの日付を自動的に計算できます。 1985 年 5 月 10 日という日付について、年と月と日の要素がそれぞれ異なるフィールドに格納されていれば、それらを 1 つの値に統合することができます。 日付の構成要素を個別に扱うアプリであれば、逆に日付を個々の構成要素に分解することもできます。

## <a name="prerequisites"></a>前提条件

* PowerApps に[サインアップ](../signup-for-powerapps.md)し、サインアップに使用したのと同じ資格情報を入力して[サインイン](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)します。
* PowerApps で、アプリを作成するか既存のアプリを開きます。
* PowerApps で[コントロールを構成する](add-configure-controls.md)方法について確認します。

## <a name="show-text-in-a-label-control"></a>ラベル コントロールでのテキストの表示
**[ラベル](controls/control-text-box.md)** コントロールにテキストを表示するには、その **[Text](controls/properties-core.md)** プロパティの値を設定します。 このプロパティを設定するには、コントロールに直接値を入力するか、数式バーに式を入力します。

* コントロールに直接入力した場合は、入力した内容がそのまま表示されます。
* 数式バーに式を入力した場合は、その式の結果がコントロールに表示されます。

次に例をいくつか示します。

1. **ShowText** という名前の **[ラベル](controls/control-text-box.md)** コントロールを追加し、その **[Text](controls/properties-core.md)** プロパティを次の数式に設定します。
   <br>**Now()**
   
    ご使用のコンピューターのロケールが "en-us" に設定されている場合、現在の日付と時刻が " " 形式で表示されます。<br>*/mm/dd/yyyy hh:mm AM/PM*
   
    ご使用のコンピューターのロケールが "fr-fr" などに設定されている場合、現在の日付と時刻は次の形式で表示されます。 <br>*/mm/dd/yyyy hh:mm AM/PM*
2. **ShowText** の **[Text](controls/properties-core.md)** プロパティを次の数式に設定します。
   <br>**DateDiff(Today(), DateValue("01/01/2020"))**
   
    ![今日から 2020 年 1 月 1 日までの日数](./media/show-text-dates-times/date-diff-text.png)
   
    次の関数を使用すると、今日から 2020 年 1 月 1 日までの日数が表示されます。
   
   * **DateDiff**。2 つの日付の間の日数、四半期数、または年数を計算します。
   * **Today**。その時点の日付を値として計算します。
   * **DateValue**。二重引用符で囲まれたリテラル文字列を、計算の適用対象として使用できる値に変換します。
3. **BirthDate** という名前の **[テキスト入力](controls/control-text-input.md)** コントロールを追加し、**ShowText** の下に移動します。

4. **BirthDate** に、自分が生まれた月と日 (例: **05/18**) を入力します。

5. **ShowText** の **[Text](controls/properties-core.md)** プロパティを次の数式に設定します。
   <br>**DateDiff(Today(), DateValue(BirthDate.Text))**
   
    ![今日から誕生日までの日数](./media/show-text-dates-times/birth-diff.png)
   
    **ShowText** には、今日の日付から **BirthDate** に入力した日付までの日数が表示されます。 今年の誕生日が既に過ぎている場合、**ShowText** には負の値が表示されます。

## <a name="format-dates-and-times-by-using-datetimevalue"></a>DateTimeValue を使用して日時の書式を設定する
日時をテキスト文字列から値に変換すると、さまざまな方法で書式設定して計算に使用できます。 書式設定には、組み込みのオプションとカスタム オプションを使用できます。

> [!NOTE]
> **[DateTimeValue](functions/function-datevalue-timevalue.md)** 関数と **[DateValue](functions/function-datevalue-timevalue.md)** 関数は、次のいずれかの形式の日付を値に変換することができます。  
> 
> * MM/DD/YYYY  
> * DD/MM/YYYY  
> * DD Mon YYYY  
> * Month DD, YYYY  
> 
> 

1. **ArrivalDateTime** という名前の **[テキスト入力](controls/control-text-input.md)** コントロールを追加し、次の形式で日時を入力します。
   <br>**5/10/85 6:15 AM**
2. **ShowDate** という名前の **[ラベル](controls/control-text-box.md)** コントロールを追加し、その **[Text](controls/properties-core.md)** プロパティを次の数式に設定します。
   <br>**DateTimeValue(ArrivalDateTime.Text)**
   
    ![日付/時刻をテキストから値に変換する](./media/show-text-dates-times/date-value.png)
   
    **ShowDate** に表示される情報は、入力したテキストと同じですが、テキストから値に変換され、設定されている書式が異なります。 たとえば、年が 2 桁ではなく 4 桁で表示されます。
3. **ShowDate** の **[Text](controls/properties-core.md)** プロパティを次の数式に変更します。
   <br>**DateTimeValue(ArrivalDateTime.Text, "fr")**
   
    ![日付/時刻の値をフランス語の書式で表示する](./media/show-text-dates-times/date-value-fr.png)
   
    **ShowDate** では、フランスのユーザーの予想どおり、月の前に日が表示されます。
   
   > [!TIP]
   > Intellisense で他のロケールの一覧を表示するには、開始二重引用符だけを残して、終わり二重引用符と **fr** を数式から削除します。
   > 
   > ![ロケールの一覧を表示する](./media/show-text-dates-times/locale-list.png)
   > 
   > 
4. 組み込みの書式のいずれかを使用するには、**ShowDate** の **[Text](controls/properties-core.md)** プロパティを次の数式に変更します。
   <br>**Text(DateTimeValue(ArrivalDateTime.Text), DateTimeFormat.LongDateTime)**
   
    ![日付/時刻の値をフランス語の書式で表示する](./media/show-text-dates-times/long-date-time.png)
   
    **ShowDate** には、曜日、日付、時刻が表示されます。
   
   > [!TIP]
   > **DateTimeFormat** パラメーターは、他のいくつかの組み込みの書式をサポートしています。 先ほどの数式から **LongDateTime** を削除すると、その一覧を表示できます。
   > 
   > 
5. カスタム書式を使用するには、**ShowDate** の **[Text](controls/properties-core.md)** プロパティを次の数式に変更します。
   <br>**Text(DateTimeValue(ArrivalDateTime.Text), "mm/dd/yyyy hh:mm:ss.fff AM/PM")**
   
    ![日付/時刻の値をフランス語の書式で表示する](./media/show-text-dates-times/format-milliseconds.png)
   
    **ShowDate** には、指定した書式で日付/時刻の値 (ミリ秒を含む) が表示されます。
   
   > [!TIP]
   > 時刻を 10 分の 1 秒の位または 100 分の 1 秒の位に丸めるには、この数式に **hh:mm:ss.f** または **hh:mm:ss.ff** を指定します。
   > 
   > 

## <a name="format-a-date-by-using-datevalue"></a>DateValue を使用して日付の書式を設定する

1. **ArrivalDate** という名前の **[テキスト入力](controls/control-text-input.md)** コントロールを追加し、そこに日付を入力します (例: **5/10/85**)。

2. **FormatDate** という名前の **[ラベル](controls/control-text-box.md)** コントロールを追加し、その **[Text](controls/properties-core.md)** プロパティを次の数式に設定します。
   <br>**DateValue(ArrivalDate.Text)**
   
    **FormatDate** には、入力した日付が表示されます。ただし、年は 4 桁で表示されます。
3. **FormatDate** の **[Text](controls/properties-core.md)** プロパティを次の数式に設定します。
   <br>**DateValue(ArrivalDate.Text, "fr")**
   
    **ShowDate** には、フランスのユーザーの予想どおり、月の前に日が表示されます。
4. 組み込みの書式のいずれかを使用するには、**FormatDate** の **[Text](controls/properties-core.md)** プロパティを次の数式に設定します。
   <br>**Text(DateValue(ArrivalDate.Text), DateTimeFormat.LongDate)**
   
    **FormatDate** には、曜日、月、日、年が表示されます。
5. カスタム書式を使用するには、**FormatDate** の **[Text](controls/properties-core.md)** プロパティを次の数式に設定します。
   <br>**Text(DateValue(ArrivalDate.Text), "yy/mm/dd")**
   
    **FormatDate** には、指定した書式で日付が表示されます。

## <a name="format-a-time-using-datetimevalue"></a>DateTimeValue を使用して時刻の書式を設定する

1. **ArrivalTime** という名前の **[テキスト入力](controls/control-text-input.md)** コントロールを追加し、そこに「**6:15 AM**」と入力します。

2. **ShowTime** という名前の **[ラベル](controls/control-text-box.md)** コントロールを追加します。

3. 組み込みの書式のいずれかを使用するには、**ShowTime** の **[Text](controls/properties-core.md)** プロパティを次の数式に設定します。
   <br>**Text(DateTimeValue(ArrivalTime.Text), DateTimeFormat.LongTime)**
   
    **ShowTime** には、指定した時刻 (秒を含む) が表示されます。
4. カスタム書式を使用するには、**ShowTime** の **[Text](controls/properties-core.md)** プロパティを次の式に設定します。
   <br>**Text(DateTimeValue(ArrivalTime.Text), "hh:mm:ss.fff AM/PM")**
   
    **ShowTime** には、指定した時刻 (秒とミリ秒を含む) が表示されます。
   
   > [!TIP]
   > 時刻を 10 分の 1 秒の位または 100 分の 1 秒の位に丸めるには、この数式に **hh:mm:ss.f** または **hh:mm:ss.ff** を指定します。
   > 
   > 

## <a name="show-the-time-between-dates"></a>日付間の時間を表示する

1. **Start** と **End** という名前の 2 つの **[テキスト入力](controls/control-text-input.md)** コントロールを追加します。

2. **Start** には「**4/1/2015**」と入力し、**End** には「**1/1/2016**」と入力します。

3. **DateDiff** という名前の **[ラベル](controls/control-text-box.md)** コントロールを追加し、その **[Text](controls/properties-core.md)** プロパティを次の数式に設定します。
   <br>**DateDiff(DateValue(Start.Text), DateValue(End.Text))**
   
    ![2 つの日付を比較する](./media/show-text-dates-times/date-diff.png)
   
    **DateDiff** には、2015 年 4 月 1 日から 2016 年 1 月 1 日までの日数である "**275**" が表示されます。
4. **DateDiff** の **[Text](controls/properties-core.md)** プロパティを次の数式に設定します。  <br>**DateDiff(DateValue(Start.Text), DateValue(End.Text), Months)**
   
    **DateDiff** には、2015 年 4 月 1 日から 2016 年 1 月 1 日までの月数である "**9**" が表示されます。 **Months** を **Quarters** または **Years** に置き換えると、時間が四半期単位や年単位で表示されます。

## <a name="identify-a-date-before-or-after-another-date"></a>特定の日付から前後した日付を特定する

1. **Start** という名前の **[テキスト入力](controls/control-text-input.md)** コントロールを追加し、そこに「**5/10/1985**」と入力します。

2. **DateAdd** という名前の **[ラベル](controls/control-text-box.md)** コントロールを追加し、その **[Text](controls/properties-core.md)** プロパティを次の数式に設定します。
   <br>**DateAdd(DateValue(Start.Text), 3)**
   
    ![3 日を加算する](./media/show-text-dates-times/date-add.png)
   
    **DateAdd** には、**Start** の日付の 3 日後である "**5/13/1985**" が表示されます。
3. **DateAdd** の **[Text](controls/properties-core.md)** プロパティを次の数式に設定します。
   <br>**DateAdd(DateValue(Start.Text), -3)**
   
    ![3 日を減算する](./media/show-text-dates-times/date-subtract.png)
   
    **DateAdd** には、**Start** の日付の 3 日前である "**5/7/1985**" が表示されます。
4. **DateAdd** の **[Text](controls/properties-core.md)** プロパティを次の数式に変更します。
   <br>**DateAdd(DateValue(Start.Text), 3, Months)**
   
    ![3 か月を加算する](./media/show-text-dates-times/date-add-months.png)
   
    このラベルには、**Start** の日付の 3 か月後である "**8/10/1985**" が表示されます。 **Months** を **Quarters** または **Years** に置き換えると、**Start** の日付から指定した四半期数または年数だけ前または後の日付が特定されます。

## <a name="calculate-dates-based-on-years-months-and-days"></a>年、月、日に基づいて日付を計算する

1. **Year**、**Month**、**Day** という名前の 3 つの **[ドロップダウン](controls/control-drop-down.md)** コントロールを追加します。

2. **Year** の **[Items](controls/properties-core.md)** プロパティを次の数式に設定します。
   <br>**Table({Year:"2014"}, {Year:"2015"}, {Year:"2016"})**

3. **Month** の **[Items](controls/properties-core.md)** プロパティを次の数式に設定します。
   <br>**Table({Month:"1"}, {Month:"2"}, {Month:"3"}, {Month:"4"}, {Month:"5"}, {Month:"6"}, {Month:"7"}, {Month:"8"}, {Month:"9"}, {Month:"10"}, {Month:"11"}, {Month:"12"})**

4. **Day** の **[Items](controls/properties-core.md)** プロパティを次の数式に設定します。
   <br>**Table({Day:"1"}, {Day:"2"}, {Day:"3"}, {Day:"4"}, {Day:"5"}, {Day:"6"}, {Day:"7"}, {Day:"8"}, {Day:"9"}, {Day:"10"}, {Day:"11"}, {Day:"12"}, {Day:"13"}, {Day:"14"}, {Day:"15"}, {Day:"16"}, {Day:"17"}, {Day:"18"}, {Day:"19"}, {Day:"20"}, {Day:"21"}, {Day:"22"}, {Day:"23"}, {Day:"24"}, {Day:"25"}, {Day:"26"}, {Day:"27"}, {Day:"28"}, {Day:"29"}, {Day:"30"}, {Day:"31"})**

5. **[ラベル](controls/control-text-box.md)** コントロールを追加し、その **[Text](controls/properties-core.md)** プロパティを次の数式に設定します。
   <br>**Text(Date(Value(Year.Selected.Value), Value(Month.Selected.Value), Value(Day.Selected.Value)), DateTimeFormat.LongDate)**
   
    既定では "**Wednesday, January 1, 2014**" が表示されます。 **[ドロップダウン](controls/control-drop-down.md)** コントロールで別の値を選択して、 **[ラベル](controls/control-text-box.md)** コントロールの日付を変更します。

想定外のデータを変換しなければならない場合があります。 **[ドロップダウン](controls/control-drop-down.md)** コントロールではなく **[テキスト入力](controls/control-text-input.md)** コントロールを追加した場合、ユーザーは誤った日付 (5 月 45 日など) を入力する可能性があります。 **[Date](functions/function-date-time.md)** 関数は、異常なデータを次のように処理します。

* 年の値が 0 以上で 1899 以下の場合は、年を計算するために、その値が 1900 に加算されます。
* 年の値が 1900 以上で 9999 以下の場合は、その値が年として使用されます。
* 年の値が 0 未満または 10000 以上の場合は、エラー値が返されます。
* 月の値が 12 を超える場合、その月数が、指定した年の最初の月に加算されます。
* 月の値が 1 未満である場合、その月数に 1 を加えた値が、指定した年の最初の月から減算されます。
* 指定された月の日数より日の値が大きい場合は、月の初日にその日数が加算され、翌月の対応する日付が返されます。
* 日の値が 1 未満の場合は、その日数に 1 を加えた数が、指定された月の初日から減算されます。

## <a name="calculate-times-based-on-hours-minutes-and-seconds"></a>時、分、秒に基づいて時刻を計算する

1. **Hour** と **Minute** という名前の 2 つの**ドロップダウン** リストを追加します。

2. **Hour** の **[Items](controls/properties-core.md)** プロパティを次の数式に設定します。
   <br>**Table({Hour:"9"}, {Hour:"10"}, {Hour:"11"}, {Hour:"12"}, {Hour:"13"}, {Hour:"14"}, {Hour:"15"}, {Hour:"16"}, {Hour:"17"})**

3. **Minute** の **[Items](controls/properties-core.md)** プロパティを次の数式に設定します。
   <br>**Table({Minute:"0"}, {Minute:"15"}, {Minute:"30"}, {Minute:"45"})**

4. **[ラベル](controls/control-text-box.md)** コントロールを追加し、その **[Text](controls/properties-core.md)** プロパティを次の数式に設定します。  
   <br>**Text(Time(Value(Hour.Selected.Value), Value(Minute.Selected.Value), 0), DateTimeFormat.ShortTime)**

5. **[Hour]** で **15** を、 **[Minute]** で **45** を選択します。
   
    **[ラベル](controls/control-text-box.md)** コントロールに "**3:45 PM**" と表示されます。
   
    ユーザーが選択できる時間の範囲を広げ、分数をより正確に指定することができるように、**Hour** と **Minute** にエントリを追加することもできます。 さらに、3 つ目の **[ドロップダウン](controls/control-drop-down.md)** コントロールを追加して、ユーザーが秒数を指定できるようにすることもできます。 3 つ目のリストを追加した場合は、 **[ラベル](controls/control-text-box.md)** コントロールの **[Text](controls/properties-core.md)** プロパティを次の式に設定します。<br>**Text(Time(Value(Hour.Selected.Value), Value(Minute.Selected.Value), Value(Second.Selected.Value)), DateTimeFormat.LongTime)**

