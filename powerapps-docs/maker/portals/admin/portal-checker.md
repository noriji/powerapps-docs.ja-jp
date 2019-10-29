---
title: ポータルを使用して顧客の問題を特定して修正する |MicrosoftDocs
description: ポータルを使用して顧客の問題を特定し、修正する方法について説明します。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: b361efd6a1f44485e9b7337e3e5b3a29c1a826d4
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/11/2019
ms.locfileid: "72976187"
---
# <a name="portal-checker"></a>ポータルチェッカー

ポータルチェッカーは、ポータルでの一般的な問題を特定するためにポータル管理者が使用できるセルフサービス診断ツールです。 ポータルチェッカーは、さまざまな構成パラメーターを確認し、その修正方法に関する提案を提供することで、ポータルの問題を特定するのに役立ちます。

ポータルチェッカーを実行すると、結果が **[診断結果]** セクションにグリッド形式で表示されます。 結果グリッドには、次の列があります。

- **問題**: お客様が直面している最上位レベルの問題を表示します。たとえば、パフォーマンスの問題があります。
- [**カテゴリ]** : 懸案事項を分類できる最上位レベルの領域を表示します。たとえば、プロビジョニング、ソリューションのアップグレードなどです。
- **結果**: 問題の状態を表示します。たとえば、error、warning などです。

既定では、グリッド内の情報は、[エラー]、[警告]、および [パス] の順に、**結果**列によって並べ替えられます。

> [!div class=mx-imgBorder]
> 診断![結果]の(../media/diagnostic-results.png "診断結果")

問題を拡張して、詳細な情報と軽減手順を確認できます。 軽減策に何らかのアクションが必要な場合は、アクションを実行するボタンが表示されます。 また、軽減策が役立つかどうかについてのフィードバックを提供することもできます。

> [!div class=mx-imgBorder]
> 診断結果![の問題を拡張]して(../media/diagnostic-results-issue-expand.png "、診断結果に問題を展開する")

必要に応じて、診断チェックを再実行できます。これにより、更新されたデータで結果が更新されます。

> [!NOTE]
> ポータルがオフになっている場合、または IP アドレスフィルターが有効になっている場合は、特定の診断チェックがポータルで実行されません。

ポータルチェッカーツールで診断される一般的な問題の一覧については、「[ポータルチェッカーによって診断される一般的なポータルの問題とそのベストプラクティス](https://docs.microsoft.com/dynamics365/customer-engagement/portals/portal-faq)」を参照してください。

ポータルチェッカーを実行するには:

1.  [PowerApps ポータル管理センター](admin-overview.md)を開きます。

2.  **実行ポータルチェッカー**にアクセスします。

    > [!div class=mx-imgBorder]
    > ポータル![チェッカーの]実行(../media/run-diagnostics.png "ポータルチェッカーの実行")

3.  **[ポータルチェッカーの実行]** を選択します。 診断セッションが開始され、顧客の問題に関するデータが収集されます。 結果は、 **[診断結果]** セクションに表示されます。

    > [!div class=mx-imgBorder]
    > 診断![結果]の(../media/diagnostic-results.png "診断結果")

4.  診断チェックを再実行するには、 **[結果の更新]** を選択します。

    > [!div class=mx-imgBorder]
    > ![診断結果]の更新の(../media/diagnostic-results-refresh.png "診断結果")の更新
