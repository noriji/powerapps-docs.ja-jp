---
title: ポータルを使用して顧客の問題を識別および修正する | MicrosoftDocs
description: ポータルを使用して顧客の問題を識別および修正する方法について説明します。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: null
ms.date: 08/30/2019
ms.author: shjais
ms.reviewer: null
---

# <a name="portal-checker"></a>ポータル チェッカー

[!include[cc-beta-prerelease-disclaimer](../../../includes/cc-beta-prerelease-disclaimer.md)]

ポータル チェッカーは、ポータルの一般的な問題を特定するためにポータル管理者が使用できるセルフサービス診断ツールです。 ポータル チェッカーは、さまざまな構成パラメーターを調べることでポータルで問題を特定し、修正方法に関する提案を示すことができます。

ポータル チェッカーを すると、結果がグリッド形式で **診断結果** セクションに表示されます。 結果グリッドには、次の列があります。

- **問題**: 顧客が直面する最上位の問題が表示されます (パフォーマンスの問題など)。
- **カテゴリ**: 問題を分類できる最上位の領域が表示されます (たとえば、プロビジョニング、ソリューションのアップグレードなど)。
- **結果**: 問題の状態が表示されます (たとえば、エラー、警告など)。

既定では、グリッドの情報は、**結果** 列で、エラー、警告、合格の順序で並べ替えられます。

> [!div class=mx-imgBorder]
> ![診断結果](../media/diagnostic-results.png "診断結果")

問題を展開し、詳細情報と軽減の手順を表示できます。 軽減に操作が必要な場合、操作を実行するボタンが表示されます。 軽減が役立ったかどうかに関するフィードバックを送信することもできます。

> [!div class=mx-imgBorder]
> ![診断結果での問題の展開](../media/diagnostic-results-issue-expand.png "診断結果での問題の展開")

必要に応じて、診断検査を再実行できます。更新されたデータで結果が更新されます。

> [!NOTE]
> ポータルがオフになったか IP アドレス フィルタリングが有効な場合、特定のチェックはポータルで実行されません。

ポータル チェッカー ツールにより診断される一般的な問題の一覧については、[ポータル チェッカーにより診断される一般的なポータルの問題とそのベスト プラクティス](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/portals/portal-faq)を参照してください。

ポータル チェッカーを実行する方法を説明します。

1.  [PowerApps ポータル管理センター](admin-overview.md) を開きます。

2.  **ポータルチェッカーの実行**へと移動します。

    > [!div class=mx-imgBorder]
    > ![ポータル チェッカーの実行](../media/run-diagnostics.png "ポータル チェッカーの実行")

3.  **ポータルチェッカーの実行**を選択します。 診断セッションが開始し、顧客の問題に関するデータを収集します。 結果は、**診断結果** セクションに表示されます。

    > [!div class=mx-imgBorder]
    > ![診断結果](../media/diagnostic-results.png "診断結果")

4.  診断検査を再実行するには、**結果の更新** を選択します。

    > [!div class=mx-imgBorder]
    > ![診断結果の更新](../media/diagnostic-results-refresh.png "診断結果の更新")
