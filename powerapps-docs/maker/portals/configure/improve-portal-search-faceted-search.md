---
title: ファセット検索を使用してポータルの検索を向上させる |MicrosoftDocs
description: ファセット検索を有効または無効にする手順。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 6b605acf1d11ecbc98760810f390f63c9a27a0a6
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2019
ms.locfileid: "73552338"
---
# <a name="use-faceted-search-to-improve-portal-search"></a>ファセット検索を使用してポータルの検索を向上させる

ポータルコンテンツは、コンテンツの特性に基づくフィルターを使用して検索できます。 ファセットポータル検索によって実装されるフィルターを使用すると、従来の検索よりも迅速に必要なコンテンツを検索できます。

## <a name="enable-or-disable-faceted-search"></a>ファセット検索を有効または無効にする

ポータルでは、すぐに使用できるファセット検索が有効になっています。 これを制御または有効にするには、次の手順を実行します。

1. [ポータル管理アプリ](configure-portal.md)を開き、[**ポータル**&gt; **Web**サイト &gt;**サイトの設定**] にアクセスします。
2. [ **Search/FacetedView** site] 設定を選択します。 
3. **値**を**True**に変更して、ファセット検索を無効にするか**False**にします。

ファセットビューの1つの部分を無効にするには、次のようにします。

1. [ポータル管理アプリ](configure-portal.md)を開き、[**ポータル**&gt; **Web テンプレート**] にアクセスします。
2. 無効にするビューを選択します (つまり、ナレッジマネージメント–上位の評価された記事)。
3. ページの上部にある **[非アクティブ化]** を選択します。

## <a name="group-entities-as-part-of-a-record-type-for-faceted-view"></a>ファセットビューのレコードの種類の一部としてエンティティをグループ化する

サイト設定の**search/RecordTypeFacetsEntities**を使用すると、類似したエンティティをグループ化して、ユーザーが検索結果をフィルター処理する論理的な方法を持つことができます。 たとえば、フォーラム、フォーラム投稿、およびフォーラムスレッドに対して個別のオプションを使用する代わりに、これらのエンティティは [フォーラム] レコードの種類の下にグループ化されます。

**[ポータル]** &gt; **[Websites]** &gt; **[サイト設定]** の順に開き、 **[Search/RecordTypeFacetsEntities]** Site 設定を開きます。 

各エンティティの前に、 **「フォーラム:** 」という語が付いていることに注意してください。 これは、最初の値がとしてグループ化された名前であるためです。 この単語は、ポータルで使用されている言語に基づいて翻訳されます。

## <a name="use-faceted-search-to-improve-knowledge-search-results"></a>ファセット検索を使用してナレッジ検索結果を向上させる

ファセット検索を使用すると、ポータルでは、左端に検索フィルターを設定できるので、フォーラム、ブログ、ナレッジ記事などの項目を選択できます。 特定の検索の種類に対して追加のフィルターが追加されます。 たとえば、ナレッジ項目は、顧客が必要とするコンテンツを検索できるように、レコードの種類、変更日、評価、および製品によってフィルター処理できます。 また、右端には、顧客の選択した関連性または表示数 (ナレッジ項目に固有) に基づいて結果を並べ替えるドロップダウンボックスもあります。 次に、使用可能なフィルターの例を示した画面キャプチャを示します。

![フィルターを使用して検索結果を向上させる](../media/faceted-search-filter.png "フィルターを使用して検索結果を向上させる")
