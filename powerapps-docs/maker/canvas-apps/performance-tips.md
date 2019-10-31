---
title: キャンバス アプリのパフォーマンスを最適化する | Microsoft Docs
description: このトピックのベスト プラクティスに従い、PowerApps で作成するキャンバス アプリのパフォーマンスを改善します。
author: yingchin
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 06/17/2019
ms.author: yingchin
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 9943678815b53df048ad197e3cdcbd56f4070fa3
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/07/2019
ms.locfileid: "71995788"
---
# <a name="optimize-canvas-app-performance-in-powerapps"></a>PowerApps でキャンバス アプリのパフォーマンスを最適化する
Microsoft は PowerApps で実行されるあらゆるアプリのパフォーマンス改善に取り組んでいますが、 このトピックのベスト プラクティスに従うことでも、作成するキャンバス アプリのパフォーマンスを改善できます。

ユーザーがアプリを開くと、次の一連の段階を実行してからユーザー インターフェイスが表示されます。 
1. **ユーザーを認証する** - ユーザーが以前にアプリを開いたことがない場合、アプリに必要な接続の資格情報でサインインするようにユーザーに求めます。 同じユーザーが再びアプリを開くとき、組織のセキュリティに関する方針によっては、資格情報の入力が再び求められることがあります。 
2. **メタデータを取得する** - アプリを実行している PowerApps プラットフォームのバージョンやデータの取得元など、メタデータを取得します。 
3. **アプリを初期化する** - **OnStart** プロパティに指定されているタスクを実行します。 
4. **画面をレンダリングする** - アプリによってデータが入力されたコントロールで最初の画面をレンダリングします。 ユーザーが他の画面を開くと、アプリによって同じプロセスでその画面がレンダリングされます。  

## <a name="limit-data-connections"></a>データ接続を制限する 
**同じアプリから 30 を超えるデータ ソースに接続しないでください**。 アプリからは、各コネクタにサインインするように新しいユーザーにも止められます。そのため、コネクタが追加されるたびに、アプリの起動に必要な時間が増えます。 アプリの実行中、そのソースからのデータがアプリによって要求されるとき、各コネクタで CPU リソース、メモリ、ネットワーク帯域幅が必要になります。 

アプリの実行中、[Microsoft Edge](https://docs.microsoft.com/microsoft-edge/devtools-guide/network) または [Google Chrome](https://developers.google.com/web/tools/chrome-devtools/network-performance/) で開発者ツールをオンにすることで、アプリのパフォーマンスを簡単に測定できます。 OneDrive 上の Common Data Service、Azure SQL、SharePoint、Excel など、30を超えるデータソースのデータを頻繁に要求した場合、アプリのデータを返すのに15秒以上かかる可能性が高くなります。  

## <a name="limit-the-number-of-controls"></a>コントロールの数を制限する 
**500 を超えるコントロールを同じアプリに追加しないでください**。 PowerApps によって、各コントロールをレンダリングするための HTML DOM が生成されます。 コントロールを追加すると、PowerApps に必要な生成時間が増えます。 

個別コントロールではなく、ギャラリーを使用することで、同じ結果を得たり、アプリを速く起動したりできることもあります。 また、同じ画面でコントロールの種類を減らす方法も有効な場合があります 一部のコントロール (PDF ビューユー、データ テーブル、コンボ ボックスなど) は大きな実行スクリプトを取り込み、レンダリングに時間がかかります。 

## <a name="optimize-the-onstart-function"></a>OnStart 関数を最適化する
[**ClearCollect**](functions/function-clear-collect-clearcollect.md) 関数を使用し、ユーザー セッション中に変わらない場合、データをローカルでキャッシュします。 また、データ ソースを同時に読み込むには、[**Concurrent**](functions/function-concurrent.md) 関数を使用します。

[この参照トピック](functions/function-concurrent.md)で紹介しているように、**Concurrent** を利用し、データを読み込むためにアプリが必要とする時間を半分に減らすことができます。

**Concurrent** 関数なしでは、この数式は 4 つのテーブルを一度に 1 つずつ読み込みます。

```
ClearCollect( Product, '[SalesLT].[Product]' );
ClearCollect( Customer, '[SalesLT].[Customer]' );
ClearCollect( SalesOrderDetail, '[SalesLT].[SalesOrderDetail]' );
ClearCollect( SalesOrderHeader, '[SalesLT].[SalesOrderHeader]' )
```

お使いのブラウザーに対して開発者ツールのこの動作を確認できます。

![シリアル ClearCollect](./media/performance-tips/perfconcurrent1.png)
    
**Concurrent** 関数で同じ数式を囲み、操作に必要となる全体的時間を減らすことができます。

```
Concurrent( 
    ClearCollect( Product, '[SalesLT].[Product]' ),
    ClearCollect( Customer, '[SalesLT].[Customer]' ),
    ClearCollect( SalesOrderDetail, '[SalesLT].[SalesOrderDetail]' ),
    ClearCollect( SalesOrderHeader, '[SalesLT].[SalesOrderHeader]' ))
```

この変更により、アプリによってテーブルが並列で取り込まれます。 

![並列 ClearCollect](./media/performance-tips/perfconcurrent2.png)  

## <a name="cache-lookup-data"></a>ルックアップ データのキャッシュ
**Set** 関数を使用し、ルックアップ テーブルからのデータをローカルでキャッシュし、ソースからデータをと繰り替え取得することを回避します。 この手法により、セッション中にデータがおそらく変わらなければ、パフォーマンスが最適化されます。 この例のように、データはソースから 1 回取得され、ユーザーがアプリを終了するまで、ローカルで参照されます。 

```
Set(CustomerOrder, Lookup(Order, id = “123-45-6789”));
Set(CustomerName, CustomerOrder.Name);
Set(CustomerAddress, CustomerOrder.Address);
Set(CustomerEmail, CustomerOrder.Email);
Set(CustomerPhone, CustomerOrder.Phone);
```

連絡先情報は頻繁に変更されません。既定値やユーザー情報も同じです。 そのため、一般的には、**Defaults** 関数や **User** 関数でもこの手法を使用できます。 

## <a name="avoid-controls-dependency-between-screens"></a>画面間のコントロール依存を回避する
パフォーマンスを向上させるために、アプリの画面は必要に応じてメモリに読み込まれます。 たとえば、画面1が読み込まれ、その数式の1つが画面2のコントロールのプロパティを使用している場合、この最適化は妨げられる可能性があります。 画面1を表示する前に、依存関係を満たすために画面2を読み込む必要があります。 画面2が画面3に依存していて、画面4に別の依存関係があるとします。 この依存関係チェーンによって、多くの画面が読み込まれる可能性があります。

このため、画面間の数式の依存関係は避けてください。 場合によっては、グローバル変数またはコレクションを使用して、画面間で情報を共有できます。

例外が発生しています。 前の例では、画面2から移動するだけで画面1を表示できます。 画面2は、スクリーン1が読み込まれたときに既にメモリに読み込まれています。 画面2の依存関係を達成するために追加の作業は必要ありません。そのため、パフォーマンスに影響はありません。

## <a name="use-delegation"></a>委任を使用する
可能であれば、処理のためにローカル デバイスにデータを読み出す代わりに、データ処理をデータ ソースに委任する関数を使用します。 アプリでデータをローカル処理する必要がある場合、操作にはたくさんの処理能力、メモリ、ネットワーク帯域幅が必要になります。これは特にデータ セットが大きい場合に当てはまります。

[この一覧](delegation-list.md)でご覧いただけるように、さまざまなデータ ソースでさまざまな関数からの委任に対応しています。

![委任を使用する](./media/performance-tips/perfdelegation1.png)

たとえば、SharePoint リストの場合、[**Filter**](functions/function-filter-lookup.md) 関数からの委任はサポートされていますが、[**Search**](functions/function-filter-lookup.md) 関数からの委任はサポートされていません。 そのため、SharePoint リストに含まれる項目が 500 を超える場合、ギャラリーの項目を検索するには、**Search** の代わりに **Filter** を使用してください。 その他のヒントについては、「[Working with large SharePoint lists in PowerApps](https://powerapps.microsoft.com/blog/powerapps-now-supports-working-with-more-than-256-items-in-sharepoint-lists/)」 (PowerApps で大きな SharePoint リストを扱う) というブログ投稿を参照してください。 

## <a name="use-delayed-load"></a>遅延読み込みを使用する
アプリに画面が 10 個以上あり、ルールがなく、(複数の画面にあり、データ ソースに直接バインドされた) たくさんのコントロールがある場合、[遅延読み込み](working-with-experimental.md)の実験機能をオンにしてください。 この種類のアプリを作成するとき、この機能を有効にしない場合、開いていない画面も含め、すべての画面のコントロールにデータを入力する必要があるため、アプリのパフォーマンスが低下することがあります。 また、ユーザーがレコードを追加したときなど、データ ソースが変わるときは必ずアプリのすべての画面を更新する必要があります。

## <a name="working-with-large-data-sets"></a>大きなデータ セットを操作する
委任できるデータ ソースと数式を使用してアプリのパフォーマンスを維持し、ユーザーが必要とするあらゆる情報にアクセスできるようにします。委任できないクエリのために、2000 というデータ行上限に到達しないようにします。 ユーザーがデータを検索、フィルター処理、並べ替えできるデータレコード列については、[SQL Server](https://docs.microsoft.com/sql/relational-databases/sql-server-index-design-guide?view=sql-server-2017) と [SharePoint](https://support.office.com/article/Add-an-index-to-a-SharePoint-column-f3f00554-b7dc-44d1-a2ed-d477eac463b0) に関するドキュメントで説明されているように、列のインデックスが効率的に設計されています。  

## <a name="republish-apps-regularly"></a>アプリを定期的に再発行する
PowerApps プラットフォームからパフォーマンス改善と追加機能を得るには、アプリを再発行します ([こちらのブログ投稿](https://powerapps.microsoft.com/blog/republish-your-apps-to-get-performance-improvements-and-additional-features/)をご覧ください)。

## <a name="avoid-repeating-the-same-formula-in-multiple-places"></a>複数の場所で同じ数式を繰り返さないようにする
複数のプロパティが同じ数式を実行する場合 (特に複雑な場合) は、1回設定してから、それ以降のプロパティの最初のプロパティの出力を参照することを検討してください。 たとえば、コントロール A、B、C、D、E の**DisplayMode**プロパティを同じ複合式に設定しないでください。 代わりに、の**displaymode**プロパティを複雑な数式に設定し、B の**displaymode**プロパティをの**displaymode**プロパティの結果に設定します。 C、D、E の場合は同様です。

## <a name="enable-delayoutput-on-all-text-input-controls"></a>すべてのテキスト入力コントロールに対して DelayOutput を有効にします
**テキスト入力**コントロールの値を参照する複数の数式またはルールがある場合は、そのコントロールの**delayedoutput**プロパティを true に設定します。 このコントロールの**Text**プロパティは、クイック連続で入力されたキーストロークになったがある場合にのみ更新されます。 数式またはルールは何度も実行されず、アプリのパフォーマンスが向上します。

## <a name="avoid-using-formupdates-in-rules-and-formulas"></a>ルールと数式でのフォームの使用を避ける
ルールまたは式の中でユーザー入力値を参照する場合は、を使用して、すべてのフォームのデータカードを反復処理し、毎回レコードを作成し**ます。** アプリの効率を高めるには、データカードまたはコントロール値から直接値を参照します。

## <a name="next-steps"></a>次の手順
アプリのパフォーマンスを最大化し、アプリの保守を容易にするための[コーディング標準](https://aka.ms/powerappscanvasguidelines)を確認します。
