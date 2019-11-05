---
title: PowerApps の Cognitive Services を使用する | Microsoft Docs
description: Azure Cognitive Services Text Analytics API を使用してテキストを分析する基本的なキャンバスアプリを作成します。
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 12/08/2017
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: a998ca743fe693645adaabbd32d4d3110c12068a
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2019
ms.locfileid: "73540853"
---
# <a name="use-cognitive-services-in-powerapps"></a>PowerApps の Cognitive Services を使用する
この記事では、 [Azure Cognitive Services Text Analytics API](https://docs.microsoft.com/azure/cognitive-services/text-analytics/overview)を使用してテキストを分析する基本的なキャンバスアプリを作成する方法について説明します。 Text Analytics API の設定方法と、[Text Analytics コネクタ](https://docs.microsoft.com/connectors/cognitiveservicestextanalytics/)を使って、Text Analytics API に接続する方法を説明します。 次に、API を呼び出すキャンバス アプリを作成する方法を説明します。

> [!NOTE]
> PowerApps でアプリを構築するのに慣れていない場合は、この記事を読み進める前に、「[アプリを最初から作成する](get-started-create-from-blank.md)」を読まれることをお勧めします。

## <a name="introduction-to-azure-cognitive-services"></a>Azure Cognitive Services の概要
Azure Cognitive Services は、アプリケーションをよりインテリジェント、魅力的、検出可能にするために使用できる Api、Sdk、およびサービスのセットです。 これらのサービスを利用すると、感情や動画の検出、顔や音声および画像の認識、音声や言語の理解などのインテリジェントな機能を簡単にアプリケーションに追加できます。

この記事では "言葉の理解" に注目して、Text Analytics API を使用します。 この API を使用すると、テキストからセンチメント、キー フレーズ、トピックおよび言語を検出できます。 まず API のデモを試したあと、プレビュー版にサインアップしてみましょう。

### <a name="try-out-the-text-analytics-api"></a>Text Analytics API の試用
API のオンライン デモが用意されています。このデモでは、API の動作や、サービスが返す JSON を見ることができます。

1. [Text Analytics API](https://azure.microsoft.com/services/cognitive-services/text-analytics/) ページに進みます。

2. 「**アクションからご覧ください**」セクションで、サンプルのテキストを使用するか、独自のテキストを入力します。 その後、 **[分析]** をクリックまたはタップしてください。 
   
    ![Text Analytics API デモ](./media/cognitive-services-api/text-analytics-demo.png)

3. ページには、[分析された**テキスト**] タブに書式設定された結果と、 **json の json**応答が表示されます[。 json は](https://json.org/)、データ (この場合は、Text Analytics API によって返されるデータ) を表す方法です。

## <a name="sign-up-for-the-text-analytics-api"></a>Text Analytics API へのサインアップ
API は無料のプレビュー版として利用でき、Azure サブスクリプションに関連付けられます。 API は Azure Portal から管理します。

1. Azure サブスクリプションをまだお持ちでない場合は、[無料のサブスクリプションにサインアップします](https://azure.microsoft.com/free/)。

2. この[ページ](https://ms.portal.azure.com/#create/Microsoft.CognitiveServicesTextAnalytics)では、このイメージに示されているように、Text Analytics API の情報を入力します。 **[F0]** (無料) 価格レベルを選択します。
   
    ![Text Analytics API の作成](./media/cognitive-services-api/azure-create.png)

5. 左下隅の **[作成]** をクリックまたはタップします。

6. **[ダッシュボード]** で、作成した API をクリックまたはタップします。
   
    ![Azure ダッシュボード](./media/cognitive-services-api/azure-dashboard.png)

7. **[キー]** をクリックまたはタップします。
   
    ![Azure メニュー](./media/cognitive-services-api/azure-menu-keys.png)

8. 画面右側のキーの 1 つをコピーします。 後で API への接続を作成するときに、このキーを使用します。
   
    ![API キー](./media/cognitive-services-api/azure-keys.png)

## <a name="build-the-app"></a>アプリのビルド
Text Analytics API が起動し、実行中になったため、PowerApps から接続したり、API を呼び出すアプリケーションをビルドしたりできます。 これは、Text Analytics API ページのデモと同様の機能を備えた 1 画面構成のアプリです。 このビルドを始めましょう。

### <a name="create-the-app-and-add-a-connection"></a>アプリの作成と接続の追加
まず、空の携帯電話アプリを作成し、**Text Analytics** コネクタを使って接続を追加します。 これらのタスクの詳細については、「[アプリを最初から作成する](get-started-create-from-blank.md)」と「[PowerApps で接続を管理する](add-manage-connections.md)」をご覧ください。

1. [powerapps.com](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) で、 **[空白から開始]**  > ![電話アプリのアイコン ](./media/cognitive-services-api/icon-phone-app.png) (電話) > **[Make this app]\(このアプリの作成\)** の順に選択します。

    ![空白から開始](./media/cognitive-services-api/start-from-blank.png)

2. PowerApps Studio の中央のウィンドウで **[データに接続]** を選択します。

3. **[データ]** パネルで、 **[新しい接続]**  >  **[テキスト分析]** をクリックまたはタップします。

4. キーを **[アカウント キー]** にコピーし、 **[作成]** をクリックまたはタップします。
   
    ![テキスト分析コネクタ](./media/cognitive-services-api/create-connection-ta.png)

### <a name="add-controls-to-the-app"></a>アプリへのコントロールの追加
アプリの作成の次の手順では、すべてのコントロールを追加します。 通常アプリをビルドするときは、コントロールに都度数式を追加しますが、今回はまずコントロールに注目し、次のセクションでいくつかの数式を追加します。 次の画像は、すべてのコントロールを備えたアプリを示しています。

![完成したアプリ](./media/cognitive-services-api/finished-app-no-data.png)

この画面を作成するには、以下の手順に従います。 コントロール名を指定すると、その名前が次のセクションの数式で使用されます。

1. **[ホーム]** タブで、 **[新しい画面]** 、 **[スクロール可能な画面]** の順にクリックまたはタップします。 

2. **[Screen2]\(画面 2\)** で、 **[タイトル]** を選択し、それを**テキスト分析**に変更します。

3. 概要説明のテキスト用に、 **[ラベル]** コントロールを追加します。

4. 分析するテキストを入力できるように、 **[テキスト入力]** コントロールを追加します。 コントロールに **tiTextToAnalyze** と名前を付けます。 アプリは次のように表示されます。
   
    ![タイトル、サブタイトル、およびテキスト入力を備えたアプリ](./media/cognitive-services-api/partial-app-step1.png)

5. 実行する API 操作を選択できるように、3 つの **[チェック ボックス]** コントロールを追加します。 コントロールにそれぞれ **[chkLanguage]** 、 **[chkPhrases]** 、および **[chkSentiment]** と名前を付けます。

6. 実行する操作を選択した後、API を呼び出すことができるように、ボタンを追加します。 アプリは次のように表示されます。
   
    ![チェック ボックスとボタンを備えたアプリ](./media/cognitive-services-api/partial-app-step2.png)

7. 3 つの **[ラベル]** コントロールを追加します。 最初の 2 つは、Language API と Sentiment API の呼び出し結果を保持します。3 つ目は、画面下部のギャラリーの概要説明に使用します。

8. **[空の垂直ギャラリー]** コントロールを追加し、 **[ラベル]** コントロールをギャラリーに追加します。 ギャラリーには、キー フレーズ API の呼び出しの結果が保持されます。 アプリは次のように表示されます。
   
    ![ラベルおよびギャラリーを備えたアプリ](./media/cognitive-services-api/partial-app-step3.png)

9. 左のウィンドウで、 **[Screen1]\(画面 1\)** > 省略記号 ( **[. . .]** ) > **[削除]** の順番に選択します (このアプリには、この画面は不要です)。

Text Analytics API を呼び出すことに焦点を当てるため、アプリをシンプルな状態にしてきましたが、選択したチェック ボックスに基づいてコントロールの表示や非表示を行うロジックを追加したり、ユーザーがオプションを選択しない場合のエラー処理を追加したりすることもできます。

### <a name="add-logic-to-make-the-right-api-calls"></a>右側の API 呼び出しを行うロジックの追加
さて、見栄えの良いアプリになりましたが、まだ何も実行していません。 すぐに修正していきます。 しかし詳しい説明に進む前に、アプリが従うパターンを理解しておきましょう。

1. アプリは選択されたチェック ボックスに基づいて、特定の API 呼び出しを行います。 **[Analyze text]\(テキスト分析\)** をクリックまたはタップすると、アプリは 1 つ、2 つ、または 3 つの API 呼び出しを行います。

2. このアプリは API が返すデータを 3 つの異なる[コレクション](working-with-variables.md#use-a-collection)、つまり **languageCollect**、**sentimentCollect**、および **phrasesCollect** に格納します。

3. このアプリは、ラベルの 2 つの **Text** プロパティとギャラリーの **Items** プロパティを、3 つのコレクションの内容に基づいて更新します。

それを踏まえて、ボタンの **[OnSelect]** プロパティに数式を追加しましょう。 ここがすべてのマジックが起きるところです。

```powerapps-dot
If( chkLanguage.Value = true,
    ClearCollect( languageCollect, 
        TextAnalytics.DetectLanguage(
            {
                numberOfLanguagesToDetect: 1, 
                text: tiTextToAnalyze.Text
            }
        ).detectedLanguages.name
    )
);

If( chkPhrases.Value = true,
    ClearCollect( phrasesCollect, 
        TextAnalytics.KeyPhrases(
            {
                language: "en", 
                text: tiTextToAnalyze.Text
            }
        ).keyPhrases
    )
);

If( chkSentiment.Value = true,
    ClearCollect( sentimentCollect, 
        TextAnalytics.DetectSentiment(
            {
                language: "en", 
                text: tiTextToAnalyze.Text
            }
        ).score
    )
)
```

ここでちょっとしたことが起きているので、詳しく見てみましょう。

* **If** ステートメントは簡単です - 特定のチェック ボックスが選択されたら、その操作を実行する API を呼び出します。

* 各呼び出しでは、適切なパラメーターを指定します。

  * 3 つの呼び出しすべてで、入力テキストとして **tiTextToAnalyze.Text** を指定します。

  * **DetectLanguage()** で、**numberOfLanguagesToDetect** を 1 にハードコーディングしますが、アプリ内のロジックに基づいて、このパラメーターを渡すこともできます。

  * で**は、"(** )" と " **()** " を使用すると、**言語**は "en" としてハードコーディングされますが、アプリのロジックに基づいてこのパラメーターを渡すことができます。 たとえば、まず言語を検出し、次に **DetectLanguage()** が返すものに基づいて、このパラメーターを設定できます。

* 呼び出しが行われるごとに、結果を適切なコレクションに追加します。

    * **languageCollect** には、テキストから特定された言語**名**を追加します。

    * **phrasesCollect** には、テキストから特定された **keyPhrases** を追加します。

    * **sentimentCollect** には、テキストに対するセンチメントの**スコア**を追加します。その値は 0 から 1 で、1 なら 100% ポジティブです。

### <a name="display-the-results-of-the-api-calls"></a>API 呼び出しの結果の表示
API 呼び出しの結果を表示するには、各コントロールで適切なコレクションを参照します。

1. 言語ラベルの **Text** プロパティを `"The language detected is " & First(languageCollect).name` に設定します。
   
    **First()** 関数は、**languageCollect** の最初 (かつ、この場合では唯一) のレコードを返し、そのレコードに関連付けられた**名** (唯一のフィールド) を表示します。

2. センチメント ラベルの **Text** プロパティを `"The sentiment score is " & Round(First(sentimentCollect.Value).Value, 3)\*100 & "% positive."` に設定します。
   
    この数式では **First()** 関数も使用して、最初であり唯一のレコードから **値** (0 から 1) を取得し、その値をパーセント形式にします。

3. キー フレーズ ギャラリーの **Items** プロパティを `phrasesCollect` に設定します。
   
    今度はギャラリーと連動しているため、**First()** 関数で 1 つの値を抽出する必要はありません。 コレクションを参照し、ギャラリーにキー フレーズをリストとして表示します。

## <a name="run-the-app"></a>アプリの実行

アプリが完成したので、起動して動作を確認します。右上隅の [実行] ボタンをクリックまたはタップします。 ![アプリの実行](./media/cognitive-services-api/icon-run-app.png). 次の画像では、3 つのオプションすべてが選択されており、テキストは、Text Analytics API ページの既定のテキストと同じものです。

![完成したアプリとデータ](./media/cognitive-services-api/finished-app.png)

このアプリの出力を、この記事の最初の Text Analytics API のページと比較すると、同じ結果になることがわかります。

これで Text Analytics API に関する理解を深め、この API をアプリに組み込む方法について楽しんでご覧いただけたなら幸いです。 Microsoft の記事で、詳しく取り上げてほしい Cognitive Services (または他の一般的なサービス) が他にある場合はお知らせください。 いつものように、コメントにフィードバックや質問があればお寄せください。

