---
title: Errors 関数 | Microsoft Docs
description: 構文と例を含む PowerApps の Errors 関数の参照情報
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 11/11/2015
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 114474696f85980da315b6dd225250dc1b197805
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/07/2019
ms.locfileid: "71992796"
---
# <a name="errors-function-in-powerapps"></a>PowerApps の Errors 関数
[データ ソース](../working-with-data-sources.md)に対する以前の変更のエラー情報を提供します。

## <a name="overview"></a>概要
エラーは、データ ソースの[レコード](../working-with-tables.md#records)が変更されたときに発生する場合があります。  ネットワーク障害、不適切なアクセス許可、編集の競合など、多くの原因が考えられます。  

**[Patch](function-patch.md)** 関数とその他のデータ関数は、直接エラーを返しません。 代わりに、操作の結果が返されます。 データ関数の実行後、**Errors** 関数を使用して、エラーの詳細を取得することができます。  **IsEmpty( Errors ( ... ) )** という数式にある **[IsEmpty]** 関数で、エラーの存在を確認することができます。

**[Validate](function-validate.md)** 関数と **[DataSourceInfo](function-datasourceinfo.md)** 関数を使用すると、一部のエラーを発生前に回避することができます。  エラーの対処方法と回避方法の詳細な推奨事項については、[データ ソースの操作](../working-with-data-sources.md)に関するページを参照してください。

## <a name="description"></a>説明
**Errors** 関数は、エラーの[テーブル](../working-with-tables.md)を返します。このテーブルには、次の[列](../working-with-tables.md#columns)が含まれています。

* **Record**。  データ ソース内のエラーが発生したレコード。  レコードの作成中にエラーが発生した場合、この列は "*空白*" になります。
* **Column**。  エラーの原因となった列 (エラーの原因が 1 つの列にある場合)。 そうでない場合は、"*空白*" になります。
* **Message**。  エラーの説明。  このエラー文字列は、エンド ユーザーに表示できます。  このメッセージはデータ ソースによって生成される場合があり、長くなったり、ユーザーにとっては無意味な元の列名が含まれていたりする可能性があることに注意してください。
* **Error**。  次に示すような、エラーを解決できるように数式で使用できるエラー コード。

| ErrorKind | 説明 |
| --- | --- |
| ErrorKind.Conflict |同じレコードに対して別の変更が行われた結果、変更が競合しています。  **[Refresh](function-refresh.md)** 関数を使用して、レコードを再読み込みし、もう一度変更を試してください。 |
| ErrorKind.ConstraintViolation |1 つ以上の制約に違反しました。 |
| ErrorKind.CreatePermission |レコードを作成しようとしましたが、現在のユーザーにはレコードを作成するためのアクセス許可がありません。 |
| ErrorKind.DeletePermission |レコードを削除しようとしましたが、現在のユーザーにはレコードを削除するためのアクセス許可がありません。 |
| ErrorKind.EditPermission |レコードを編集しようとしましたが、現在のユーザーにはレコードを編集するためのアクセス許可がありません。 |
| ErrorKind.GeneratedValue |データ ソースによって自動的に生成される列を変更しようとしました。 |
| ErrorKind.MissingRequired |必要な列の値がレコードに見つかりません。 |
| ErrorKind.None |エラーはありません。 |
| ErrorKind.NotFound |レコードを編集または削除しようとしましたが、レコードが見つかりませんでした。  別のユーザーがレコードを変更した可能性があります。 |
| ErrorKind.ReadOnlyValue |読み取り専用の列を変更しようとしました。 |
| ErrorKind.Sync |データ ソースによってエラーが報告されました。  詳細については、Message 列を確認してください。 |
| ErrorKind.Unknown |エラーが発生しましたが、種類が不明です。 |
| ErrorKind.Validation |一般的な検証の問題が検出されました。この問題は他のどの種類にも当てはまりませんでした。 |

関数に *Record* 引数を指定すると、データ ソース全体または選択した行のみにエラーが返されます。  

**[Patch](function-patch.md)** またはその他のデータ関数は、レコードが作成できなかった場合などに、"*空白*" の値を返すことがあります。 **Errors** には "*空白*" を渡すことができます。その場合は、適切なエラー情報が返されます。  その後、同じデータ ソースに対してデータ関数を使用すると、エラー情報が消去されます。

エラーがない場合、**Errors** によって返されるテーブルは[空](function-isblank-isempty.md)になるため、 **[IsEmpty](function-isblank-isempty.md)** 関数を使用してテストすることができます。

## <a name="syntax"></a>構文
**Errors**( *DataSource* [, *Record* ] )

* *DataSource* – 必須。 エラーを返すデータ ソース。
* *Record* – 省略可能。  エラーを返す特定のレコード。 この引数を指定しない場合は、データ ソース全体のエラーが返されます。

## <a name="examples"></a>例
### <a name="step-by-step"></a>ステップ バイ ステップ
この例では、**IceCream** データ ソースを操作します。

![](media/function-errors/icecream.png)

ユーザーは、アプリを使用して Chocolate レコードをデータ入力フォームに読み込み、**Quantity** の値を 90 に変更します。  操作対象のレコードは、[コンテキスト変数](../working-with-variables.md#use-a-context-variable) **EditRecord** に配置されています。

* **UpdateContext ({レコードの場合:最初 (Filter (IceCream, フレーバー = "チョコレート"))})**

データ ソースでこの変更を行うには、次のように **[Patch](function-patch.md)** 関数を使用します。

* **Patch( IceCream, EditRecord, Gallery.Updates )**

ここでは、 **{Quantity: に評価さ**れます。** 90}** 。**Quantity**プロパティのみが変更されているためです。

残念ながら、 **[Patch](function-patch.md)** 関数が呼び出される直前に、他のユーザーによって Chocolate の **Quantity** が 80 に変更されます。  PowerApps はこれを検出し、競合する変更が行われないようにします。  この状況を次の数式で確認できます。

* **IsEmpty( Errors( IceCream, EditRecord ) )**

**false** が返されます。**Errors** 関数は次のテーブルを返したためです。

| レコード | 列 | メッセージ | エラー |
| --- | --- | --- | --- |
| 特徴"チョコレート"、Quantity:100} |"*空白*" |"別のユーザーにより変更しようとしているレコードは変更されています。 レコードを再読み込みしてからやり直してください。" |ErrorKind.Conflict |

このエラーをユーザーに表示するためのラベルをフォーム上に配置することができます。

* エラーを表示するには、ラベルの **[Text](../controls/properties-core.md)** プロパティを次の数式に設定します。<br>
  **Label.Text = First(Errors( IceCream, EditRecord )).Message**

ユーザーが効率的に競合を解決できるように、フォームに **Reload** ボタンを追加することもできます。

* 競合が発生した場合にのみボタンを表示するには、ボタンの **[Visible](../controls/properties-core.md)** プロパティを次の数式に設定します。<br>
    **!IsEmpty( Lookup( Errors( IceCream, EditRecord ), Error = ErrorKind.Conflict ) )**
* ユーザーがボタンを選択したときに変更を元に戻すには、そのボタンの **[OnSelect](../controls/properties-core.md)** プロパティを次の数式に設定します。<br>
    **ReloadButton.OnSelect = Revert( IceCream, EditRecord )**

