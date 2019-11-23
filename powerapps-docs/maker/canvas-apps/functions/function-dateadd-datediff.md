---
title: DateAdd、DateDiff、および TimeZoneOffset 関数 | Microsoft Docs
description: 構文と例を含む PowerApps の DateAdd、DateDiff、および TimeZoneOffset 関数の参照情報
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 05/23/2017
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 8108dbc1c78ba57e989f7bebeb8bd0f42f696360
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/07/2019
ms.locfileid: "71985143"
---
# <a name="dateadd-datediff-and-timezoneoffset-functions-in-powerapps"></a>PowerApps の DateAdd、DateDiff、および TimeZoneOffset 関数
日付/時刻値に加算または日付/時刻値の差を検出し、ローカル時刻と UTC の間で変換します。

## <a name="description"></a>説明
**DateAdd** 関数は、日付/時刻値にいくつかの単位の値を追加します。 結果は新しい日付/時間値です。 また、負の値を指定して、日付/時刻値からいくつかの単位の値を減算することもできます。

**DateDiff** 関数は、2 つの日付/時間値の差を返します。 結果は、いくつかの単位の値です。

どちらの関数でも、単位は **Milliseconds**、**Seconds**、**Minutes**、**Hours**、**Days**、**Months**、**Quarters**、**Years** のいずれかです。  既定では、どちらの関数も単位として **Days** を使用します。

**TimeZoneOffset** 関数はユーザーのローカル時刻と UTC (協定世界時) の差を分で返します。   

**DateAdd** と **TimeZoneOffset** を使用して、ユーザーのローカル時刻と UTC (協定世界時) 間で変換できます。  **TimeZoneOffset** はローカル時刻を UTC に変換します。それを減算 (負の数を加算) することで、UTC からローカル時刻に変換します。

詳細については[、「Date、Time、および DateTime データ型](/data-types#date-time-and-datetime)」および「日付[と時刻の操作](../show-text-dates-times.md)」も参照してください。

## <a name="syntax"></a>構文
**DateAdd**( *DateTime*, *Addition* [, *Units* ] )

* *DateTime* - 必須。 操作する日付/時刻値。
* *Addition* - 必須。 *DateTime* に追加する数値 (単位は *Units*)。
* *Units* - 省略可能。 追加する *Units* の種類: **Milliseconds**、**Seconds**、**Minutes**、**Hours**、**Days**、**Months**、**Quarters**、**Years** のいずれかです。  指定しない場合は、**Days** が使用されます。

**DateDiff**( *StartDateTime*, *EndDateTime* [, *Units* ] )

* *StartDateTime* - 必須。 開始の日付/時刻値。
* *EndDateTime* - 必須。 終了の日付/時刻値。
* *Units* - 省略可能。 追加する *Units* の種類: **Milliseconds**、**Seconds**、**Minutes**、**Hours**、**Days**、**Months**、**Quarters**、**Years** のいずれかです。  指定しない場合は、**Days** が使用されます。

**TimeZoneOffset**( [ *DateTime* ] )

* *DateTime* - 省略可能です。  オフセットを取得する日付/時刻値。  既定では、現在の日付/時刻が使用されます。

## <a name="examples"></a>例
これらすべての例では、現在の日付と時刻を **July 15, 2013, 1:02 PM** と想定しています。

### <a name="simple-dateadd"></a>単純な DateAdd

| 数式 | 説明 | 結果 |
| --- | --- | --- |
| **Text( DateAdd( Now(), 3 ),<br>"dd-mm-yyyy hh:mm" )** |現在の日付と時刻に 3 日 (既定の単位) を加算します。 |"18-07-2013 13:02" |
| **Text( DateAdd( Now(), 4, Hours ),<br>"dd-mm-yyyy hh:mm" )** |現在の日付と時刻に 4 時間を加算します。 |"15-07-2013 17:02" |
| **Text( DateAdd( Today(), 1, Months ),<br>"dd-mm-yyyy hh:mm" )** |現在の日付に時刻のない 1 か月を加算します。**Today** は時刻のコンポーネントを返さないため、時刻はありません。 |"15-08-2013 00:00" |
| **Text( DateAdd( Now(), &#8209;30, Minutes ),<br>"dd-mm-yyyy hh:mm" )** |現在の日付と時刻から 30 分を減算します。 |"15-07-2013 12:32" |

### <a name="simple-datediff"></a>単純な DateDiff

| 数式 | 説明 | 結果 |
| --- | --- | --- |
| **DateDiff( Now(), DateValue("1/1/2014") )** |既定の **Days** を単位として 2 つの単位の差を返します。 |170 |
| **DateDiff( Now(), DateValue("1/1/2014"), Months )** |**Months** を単位として 2 つの値の差を返します。 |6 |
| **DateDiff( Now(), Today(), Minutes )** |現在の日付/時刻と現在の日付のみ (時刻なし) の差を分の単位で返します。  **Now** は **Today** よりも後であるため、結果は負になります。 |-782 |

### <a name="converting-to-utc"></a>UTC への変換
UTC (協定世界時) に変換する場合は、指定された時刻の **TimeZoneOffset** を追加します。  

たとえば、現在の日付と時刻が太平洋夏時間 (PDT、UTC-7) の **July 15, 2013, 1:02 PM** であるとします。  UTC で表した現在の時刻を確認するには、以下を使用します。

* **DateAdd( Now(), TimeZoneOffset(), Minutes )**

**TimeZoneOffset** は既定で現在の時刻になります。そのため引数として渡す必要はありません。

結果を表示するには、**Text** 関数を使用し、*dd-mm-yyyy hh:mm* という形式を指定すると、**15-07-2013 20:02** が返されます。

### <a name="converting-from-utc"></a>UTC からの変換
UTC から変換するには、**TimeZoneOffset** を (負の値を加算することによって) 減算します。

たとえば、UTC で表した **July 15, 2013, 8:02 PM** という日付と時刻が、**StartTime** という名前の変数に格納されているとします。 ユーザーのタイム ゾーンに合わせて時刻を調整するには、以下を使用します。

* **DateAdd (StartTime、&minus;TimeZoneOffset (StartTime)、Minutes)**

**TimeZoneOffset** の前に負の符号が付いています。これは、オフセットを加算するのではなく減算するためです。

結果を表示するには、**Text** 関数を使用し、*dd-mm-yyyy hh:mm* という形式を指定すると、ユーザーのタイム ゾーンが太平洋夏時間であれば **15-07-2013 13:02** が返されます。

