---
title: JSON 関数 |Microsoft Docs
description: 構文を含む PowerApps の JSON 関数の参照情報
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 05/02/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: ba852093da05c3fa69cc47b219a0bef65908c170
ms.sourcegitcommit: 57b968b542fc43737330596d840d938f566e582a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2019
ms.locfileid: "71992629"
---
# <a name="json-function-in-powerapps"></a>PowerApps の JSON 関数

テーブル、レコード、または値の JSON テキスト文字列を生成します。

## <a name="description"></a>Description

**Json**関数は、データ構造の JAVASCRIPT OBJECT NOTATION (json) 表現をテキストとして返します。これにより、ネットワーク上での格納や転送に適しています。 [ECMA-404](http://www.ecma-international.org/publications/files/ECMA-ST/ECMA-404.pdf)および[IETF RFC 8259](https://tools.ietf.org/html/rfc8259)では、JavaScript やその他のプログラミング言語で広く使用されている形式について説明しています。

キャンバスアプリは、次の表に示す[データ型](data-types.md)をサポートしており、テキスト表現の詳細が示されています。

| データ型 | Description | 結果の例 |
|-----------|-------------|---------|
| **演算** | *true*または*false*。 | `true` |
| **色** | 色の8桁の16進数表現を含む文字列。 この表現は #*rrggbbaa*の形式になります。ここで、 *rr*は赤のコンポーネント、 *gg*は緑、 *bb*は青、 *aa*はアルファチャネルです。 アルファチャネルの場合、 **00**は完全に透明で、 **ff**は完全に不透明です。 この文字列を[**Colorvalue**](function-colors.md)関数に渡すことができます。  | `"#102030ff"` |
| **通貨** | ユーザーの言語に適した小数点区切り文字を使用する数値。 必要に応じて、科学的表記法が使用されます。 | `1.345` |
| **予定** | ISO 8601 **yyyy-mm-dd**形式の日付を含む文字列。 | `"2019-03-31"` |
| **/** | ISO 8601 の日付/時刻を含む文字列。 日付/時刻値は、末尾の "Z" が示すように UTC で表示されます。  | `"2019-03-31T22:32:06.822Z"`  |
| **GUID** | GUID 値を含む文字列。 文字は小文字です。 | `"751b58ac-380e-4a04-a925-9f375995cc40"`
| **イメージ、メディア** | **Includebinarydata**を指定した場合、メディアファイルは文字列でエンコードされます。 Http: または https: URL スキームを使用する Web 参照は変更されません。 インメモリバイナリデータへの参照は、 ["data:*mime*; base64,..."](https://en.wikipedia.org/wiki/Data_URI_scheme)形式でエンコードされます。 インメモリデータには、ユーザーが[**カメラ**](../controls/control-camera.md)コントロールと、appres: および BLOB: URL スキームを使用したその他の参照を使用してキャプチャする画像が含まれます。| `"data:image/jpeg;base64,/9j/4AA..."` |
| **少数** | ユーザーの言語に適した小数点区切り文字を使用する数値。 必要に応じて、科学的表記法が使用されます。 | `1.345` |
| **オプション &nbsp;set** | 表示に使用されるラベルではなく、オプションセットの数値。 この数値は、言語に依存しないために使用されます。  | `1001` |
| **ごと** | ISO 8601 *hh: mm: ss. fff*形式を含む文字列。  | `"23:12:49.000"` |
| **録音** | フィールドとその値のコンマ区切りのリスト ( **{** と **}** )。 この表記は、キャンバスアプリのレコードの場合と似ていますが、名前は常に二重引用符で囲まれています。 この形式では、多対一のリレーションシップに基づくレコードはサポートされません。  | `{ "First Name": "Fred", "Age": 21 }` |
| **一覧** | レコードの **[** および **]** の間のコンマ区切りの一覧。 この形式では、一対多のリレーションシップに基づくテーブルはサポートされません。  | `[ { "First Name": "Fred", "Age": 21 }, { "First Name": "Jean", "Age": 20 } ]` |
| **2つの &nbsp;option** | 表示に使用されるラベルではなく、 *true*または*false*の2つのオプションのブール値。 ブール値は、言語に依存しないために使用されます。 | `false` |
| **Hyperlink、Text** | 二重引用符で囲まれた文字列。 関数は、埋め込みの二重引用符を円記号でエスケープし、改行文字を "\n" に置き換え、その他の標準的な JavaScript の置換を行います。 | `"This is a string."` |

オプションの*Format*引数を指定して、結果の読み取り方法とサポートされていないデータ型およびバイナリデータ型の処理方法を制御します。 既定では、出力はできるだけコンパクトになります。不要なスペースや改行は不要で、サポートされていないデータ型とバイナリデータは使用できません。 **@No__t_1**演算子を指定する場合は、複数の形式を組み合わせることができます。

| JSONFormat 列挙型 | Description |
|-----------------|-------------|
| **Cd-r** | 既定値。  出力は、スペースや改行を追加しなくても、できるだけコンパクトになります。 |
| **IndentFour** | 読みやすさを向上させるために、出力には各列および入れ子レベルの改行が含まれており、インデントレベルごとに4つのスペースが使用されます。 |
| **IncludeBinaryData** | 結果には、イメージ、ビデオ、およびオーディオクリップの列が含まれます。 この形式は、結果のサイズを大幅に増やし、アプリのパフォーマンスを低下させる可能性があります。 |
| **IgnoreBinaryData** | 結果には、イメージ、ビデオ、またはオーディオクリップの列は含まれません。 **Includebinarydata**も**ignorebinarydata**も指定しない場合、関数はバイナリデータを検出するとエラーを生成します。 |
| **IgnoreUnsupportedTypes** | サポートされていないデータ型を使用することはできますが、結果には含まれません。 既定では、サポートされていないデータ型によってエラーが生成されます。 |

結果に含まれるデータを制御し、サポートされていないデータ型を削除するには、 [ **showcolumns**関数と**dropcolumns** ](function-table-shaping.md)関数を使用します。

**JSON**はメモリとコンピューティング集中型の両方になる可能性があるため、この関数は[動作関数](../working-with-formulas-in-depth.md)でのみ使用できます。 **JSON**の結果を[変数](../working-with-variables.md)にキャプチャして、データフローで使用することができます。

列に表示名と論理名の両方がある場合、結果には論理名が含まれます。 表示名はアプリユーザーの言語を反映しているため、共通サービスへのデータ転送には不適切です。

## <a name="syntax"></a>構文

**JSON**( *DataStructure* [, *Format* ])

* *DataStructure* –必須。 JSON に変換するデータ構造体。  テーブル、レコード、およびプリミティブ値がサポートされ、任意に入れ子になっています。
* *Format* -省略可能。  **Jsonformat**列挙値。 既定値は**Compact**です。この場合、改行やスペースは追加されず、バイナリデータとサポートされていない列はブロックされます。

## <a name="examples"></a>例

### <a name="hierarchical-data"></a>階層データ

1. [**ボタン**](../controls/control-button.md)コントロールを挿入し、その**onselect**プロパティを次の数式に設定します。

    ```powerapps-dot
    ClearCollect( CityPopulations,
        { City: "London",    Country: "United Kingdom", Population: 8615000 },
        { City: "Berlin",    Country: "Germany",        Population: 3562000 },
        { City: "Madrid",    Country: "Spain",          Population: 3165000 },
        { City: "Hamburg",   Country: "Germany",        Population: 1760000 },
        { City: "Barcelona", Country: "Spain",          Population: 1602000 },
        { City: "Munich",    Country: "Germany",        Population: 1494000 }
    );
    ClearCollect( CitiesByCountry, GroupBy( CityPopulations, "Country", "Cities" ) )
    ```

1. Alt キーを押しながらボタンを選択します。

    **CitiesByCountry**コレクションは、このデータ構造を使用して作成されます。このデータ構造を表示するには、 **[ファイル]** メニューの **[コレクション]** を選択し、コレクションの名前を選択します。

    > [!div class="mx-imgBorder"]
    > ![CitiesByCountry コレクション ](media/function-json/cities-grouped.png)

    このコレクションを表示するには、[**ファイル** > **アプリの設定** >  詳細  >  設定] を選択し、 **[** **数式バーの結果ビューを有効に**する] を選択し、数式バーでコレクションの名前を選択してから、数式バーの下のコレクション名の横にある下矢印。

    > [!div class="mx-imgBorder"]
    > 数式バーの結果ビューでの ![Collection ](media/function-json/cities-grouped-resultview.png)

1. 別のボタンを挿入し、その**Onselect**プロパティを次の数式に設定します。

    ```powerapps-dot
    Set( CitiesByCountryJSON, JSON( CitiesByCountry ) )
    ```

    この数式は、グローバル変数**CitiesByCountryJSON**を**CitiesByCountry**の JSON 表現に設定します。

1. Alt キーを押しながらボタンを選択します。

1. [**ラベル**](../controls/control-text-box.md)コントロールを挿入し、 **Text**プロパティをこの変数に設定します。

    ```powerapps-dot
    CitiesByCountryJSON
    ```

    ラベルは、次の結果を示しています。この結果はすべて、スペースを含まない1行になり、ネットワーク経由の送信に適しています。

    ```json
    [{"Cities":[{"City":"London","Population":8615000}],"Country":"United Kingdom"},{"Cities":[{"City":"Berlin","Population":3562000},{"City":"Hamburg","Population":1760000},{"City":"Munich","Population":1494000}],"Country":"Germany"},{"Cities":[{"City":"Madrid","Population":3165000},{"City":"Barcelona","Population":1602000}],"Country":"Spain"}]
    ```

1. 2番目のボタンの数式を変更して、出力を読みやすくします。

    ```powerapps-dot
    Set( CitiesByCountryJSON, JSON(CitiesByCountry, JSONFormat.IndentFour ))
    ```

1. Alt キーを押しながら2番目のボタンを選択します。

    ラベルは、読みやすい結果を示しています。

    ```json
    [
        {
            "Cities": [
                {
                    "City": "London",
                    "Population": 8615000
                }
            ],
            "Country": "United Kingdom"
        },
        {
            "Cities": [
                {
                    "City": "Berlin",
                    "Population": 3562000
                },
                {
                    "City": "Hamburg",
                    "Population": 1760000
                },
                {
                    "City": "Munich",
                    "Population": 1494000
                }
            ],
            "Country": "Germany"
        },
        {
            "Cities": [
                {
                    "City": "Madrid",
                    "Population": 3165000
                },
                {
                    "City": "Barcelona",
                    "Population": 1602000
                }
            ],
            "Country": "Spain"
        }
    ]
    ```

### <a name="images-and-media-in-base64"></a>Base64 のイメージとメディア

1. [**イメージ**](../controls/control-image.md)コントロールを追加します。

    このコントロールは、 **Sampleimage**をこのコントロールに取り込みます。

1. [**ボタン**](../controls/control-button.md)コントロールを追加し、その**onselect**プロパティをこの数式に設定します。

    ```powerapps-dot
    Set( ImageJSON, JSON( SampleImage, JSONFormat.IncludeBinaryData ) )
    ```

1. Alt キーを押しながらボタンを選択します。

1. ラベルを追加し、 **Text**プロパティをこの変数に設定します。

    ```powerapps-dot
    ImageJSON
    ```

1. コントロールのサイズを変更し、必要に応じてフォントサイズを縮小して、結果のほとんどを表示します。

    ラベルには、 **JSON**関数によってキャプチャされたテキスト文字列が表示されます。

    ```json
    "data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0idXRmLTgiPz4NCjxzdmcgdmVyc2lvbj0iMS4xIg0KCSB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHhtbG5zOnhsaW5rPSJodHRwOi8vd3d3LnczLm9yZy8xOTk5L3hsaW5rIiB4bWxuczphPSJodHRwOi8vbnMuYWRvYmUuY29tL0Fkb2JlU1ZHVmlld2VyRXh0ZW5zaW9ucy8zLjAvIg0KCSB4PSIwcHgiIHk9IjBweCIgd2lkdGg9IjI3MHB4IiBoZWlnaHQ9IjI3MHB4IiBlbmFibGUtYmFja2dyb3VuZD0ibmV3IDAgMCAyNzAgMjcwIiB4bWw6c3BhY2U9InByZXNlcnZlIj4NCgk8ZyBjbGFzcz0ic3QwIj4NCgkJPHJlY3QgeT0iMC43IiBmaWxsPSIjRTlFOUU5IiB3aWR0aD0iMjY5IiBoZWlnaHQ9IjI2OS4zIi8+DQoJCTxwb2x5Z29uIGZpbGw9IiNDQkNCQ0EiIHBvaW50cz0iMjc3LjksMTg3LjEgMjQ1LDE0My40IDE4OC42LDIwMi44IDc1LDgwLjUgLTQuMSwxNjUuMyAtNC4xLDI3MiAyNzcuOSwyNzIiLz4NCgkJPGVsbGlwc2UgZmlsbD0iI0NCQ0JDQSIgY3g9IjIwMi40IiBjeT0iODQuMSIgcng9IjI0LjQiIHJ5PSIyNC4zIi8+DQoJPC9nPg0KPC9zdmc+"
    ```
