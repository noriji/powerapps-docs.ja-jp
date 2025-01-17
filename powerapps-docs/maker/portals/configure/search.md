---
title: PowerApps ポータルでのグローバル検索 |MicrosoftDocs
description: ポータルでのグローバル検索のしくみについて説明します。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: da142a452e903b890b1b395262771228e245140c
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2019
ms.locfileid: "73551625"
---
# <a name="search"></a>Search

PowerApps ポータルでは、ポータルのグローバル検索機能を使用して、複数のエンティティでレコードを検索できます。 エンティティ一覧の検索機能を使用して、エンティティリストのレコード内を検索することもできます。 

ポータルのエンティティリスト検索機能では、バックエンドで FetchXML を使用して、エンティティリストに定義されている列を検索し、結果を表示します。 

グローバル検索では、Lucene.Net に基づく外部検索インデックスが使用され、複数のエンティティとフィールド内で一度に検索するために使用されます。

## <a name="global-search"></a>グローバル検索

ポータルをグローバルに検索することで、複数のエンティティにわたるレコードを検索することができます。 また、複数の列を検索し、エンティティのどの列を検索可能にするかを構成することもできます。

グローバル検索の利点の中には、次の機能があります。
- エンティティ内の任意のフィールドで、検索語句に一致する単語を検索します。 一致には、ストリーム、ストリーミング、ストリーミングなどの変化形語を含めることができます。
- 一致した単語の数などの要因、またはテキスト内の互いに近接しているものに基づいて、検索可能なすべてのエンティティの検索結果を関連性で並べ替えて返します。
- 検索結果内の一致項目を強調表示します。
- 検索結果をさらにフィルター処理するために使用できるファセットオプションを提供します。

グローバル検索では、一致条件が高いほど、結果に表示されます。 検索語句のより多くの単語が相互に近接している場合は、一致する関連性が高くなります。 検索語が見つかるテキストの量が少ないほど、関連性が高くなります。 たとえば、検索語が会社名と住所で見つかった場合は、大規模な記事で見られる言葉とは遠く離れているものと一致していることがあります。 結果は1つの一覧に返されるので、一致する作業が強調表示された状態で、別のレコードの後に1つずつ表示されます。 

以下のセクションでは、PowerApps ポータルでのグローバル検索のしくみと、使用可能なさまざまな構成オプションについて説明します。

## <a name="entities-searchable-in-portal-global-search"></a>ポータルのグローバル検索で検索可能なエンティティ

適切なソリューションパッケージがインストールされ、検索がポータルに追加されている場合、ポータル web サイト内で次のエンティティを検索できます。 インデックスが作成される列は、[検索] ビューの列で構成されます。この列はカスタマイズできます。  リスト内の各エンティティには、次に示すように、インデックス付けされた既定の属性セットがあります。
- サポート情報記事
    - ナレッジ項目のメモと添付ファイルも検索できます。 詳細情報:[添付ファイルのコンテンツ内の検索](search-file-attachment.md)
    - アーティクルは、パブリッシュされていて、その内部専用フィールドが false に設定されている場合にのみ検索できます。
- ブログ 
- ブログの投稿 
- ブログ投稿コメント 
- フォーラム 
- フォーラムの投稿 
- フォーラムスレッド 
- 好ましく 
- アイデアコメント 
- アイデアフォーラム 
- Web ファイル 
    - Web ファイルの添付ファイルの内容も検索できます。 詳細情報:[添付ファイルのコンテンツ内の検索](search-file-attachment.md)
- Web ページ 
- インシデント 

> [!NOTE]
> ここに一覧表示されているエンティティとは別に、ポータルでグローバル検索に対して他のエンティティを有効にすることはできません。

## <a name="fields-searchable-in-global-search"></a>グローバル検索で検索可能なフィールド

任意のエンティティの検索/IndexQueryName サイト設定で定義されたビューで使用できるすべてのフィールドは、グローバル検索でインデックスが作成され、検索可能です。 

Search/IndexQueryName の既定値は "Portal Search" です。

どのエンティティでもビューを使用できない場合、インデックスは作成されず、結果はグローバル検索に表示されません。

> [!NOTE]
> Search/IndexQueryName サイト設定の値を変更する場合は、[[フル検索インデックスの再構築](#rebuild-full-search-index)] セクションで定義されている手順を使用して、手動でビルドのインデックスを再作成する必要があります。

## <a name="related-site-settings"></a>関連サイトの設定

次のサイト設定は、グローバル検索に関連しています。

| 名前    | 既定値     | Description       |
|-----------------------|--------------------|-------------|
| 検索/有効化 | True  | 検索が有効かどうかを示すブール値です。 値を false に設定すると、ポータルのグローバル検索が無効になります。<br>既定の web テンプレートを使用していて、この設定をオフにした場合、検索ボックスはヘッダーおよび検索ページには表示されません。 また、検索ページの直接の URL にヒットした場合でも、結果は返されません。  |
| 検索/フィルター  | コンテンツ: adx_webpage;イベント: adx_event、adx_eventscheduleブログ: adx_blog、adx_blogpost、adx_blogpostcomment;フォーラム: adx_communityforum、adx_communityforumthread、adx_communityforumpost、アイデア: adx_ideaforum、adx_idea、adx_ideacomment、issue: adx_issueforum、adx_issue、adx_issuecomment;ヘルプデスク: インシデント | 検索論理名フィルターオプションのコレクション。 ここで値を定義すると、グローバル検索にドロップダウンフィルターオプションが追加されます。 この値は、名前と値のペアの形式で、コロンで区切られた名前と値、およびセミコロンで区切られたペアである必要があります。 例: "フォーラム: adx_communityforum, adx_communityforumthread, adx_communityforumpost;ブログ: adx_blog、adx_blogpost、adx_blogpostcomment  |
| 検索/IndexQueryName   | ポータルの検索  | インデックスと検索を有効にしたエンティティのフィールドを定義するためにポータル検索クエリで使用されるシステムビューの名前。   |
| 検索/クエリ  | \+ (@Query) (title:(@Query) adx_partialurl) logicalname: adx_webpage\~0.9 ^ 0.2-: adx_webfile\~0.9:(@Query) logicalname: adx_blogpost\~0.9 ^ 0.1-logicalname: adx_communityforumthread\~0.9   | この設定により、ユーザーがポータルに表示される既定の検索ボックスに入力する重みとフィルターがクエリに追加されます。 既定値では、@Query はユーザーによって入力されたクエリテキストです。<br>この値を変更する方法の詳細については、「 [Lucene query 構文](https://lucene.apache.org/core/old_versioned_docs/versions/2_9_1/queryparsersyntax.html)」を参照してください。<br>**重要**: この重み付けとフィルター処理は、ポータルの既定の検索ページにある検索ボックスにのみ適用されます。 液体検索タグを使用して独自の検索ページを作成する場合、この設定は適用されません。 |
| 検索/ステマー  | 英語    | ポータル検索のステミングアルゴリズムで使用される言語です。   |
| 検索/FacetedView  | True   | これにより、検索結果のファセットが有効になります。 True に設定すると、ファセットは検索ページに結果と共に表示されます。  |
| 添付ファイルの検索/インデックスの検索   | True    | サポート技術情報の記事および web ファイルのメモ添付ファイルのコンテンツにインデックスを作成するかどうかを示します。 既定では、False に設定されています。 詳細情報:[添付ファイルのコンテンツ内の検索](search-file-attachment.md)    |
| 検索/RecordTypeFacetsEntities  | ブログ: adx_blog、adx_blogpostフォーラム: adx_communityforum、adx_communityforumthread、adx_communityforumpost、アイデア: adx_ideaforum、adx_idea、ダウンロード: annotation、adx_webfile    | これにより、検索ページの [レコードの種類] ファセットでエンティティがどのようにグループ化されるかが決まります。 この設定の形式は次のようになります。 <br>"DisplayNameinRecordTypeFacet1:logicalnameofentity1,logicalnameofentity2;DisplayNameinRecordTypeFacet2:logicalnameofentity3,logicalnameofentity4" <br>レコードの種類ファセットの表示名は、UI に表示されます。 このファセットグループは、構成で定義されたエンティティの結果を結合します。   |
| KnowledgeManagement/DisplayNotes | True   | サポート技術情報の記事の添付ファイルにインデックスを作成するかどうかを示します。 既定では、False に設定されています。 |
|||

## <a name="related-content-snippets"></a>関連するコンテンツスニペット

次のコンテンツスニペットは、グローバル検索に関連しています。

| 名前   | 既定値  | Description   |
|------------------|-----------------|--------------------|
| ヘッダー/検索/ラベル| Search| このコンテンツスニペットは、ポータルのヘッダーの検索ボックスに表示されるウォーターマークテキストを決定します。<br>![検索ラベル](../media/search-label.png "検索ラベル")    |
| ヘッダー/検索/ツールヒント| Search  | このコンテンツスニペットは、ポータルヘッダーの検索アイコンにマウスポインターを合わせると表示されるツールヒントテキストを決定します。<br>![検索ツールヒント](../media/search-tooltip.png "検索ツールヒント")  |
| Search/Default/FilterText| すべての   | このコンテンツスニペットは、検索ボックスの横にある [フィルター] ドロップダウンリストに表示される既定のテキストを決定します。<br>![フィルターテキストの検索](../media/search-filter-text.png "フィルターテキストの検索")  |
| 検索/ファセット/すべて| すべての| このコンテンツスニペットは、検索結果ページの [レコードの種類] ファセットの "すべてのレコードのファセット" に表示される既定のテキストを決定します。<br>![すべてのファセット](../media/facet-all.png "すべてのファセット") |
| 検索、ファセット/ClearConstraints   | すべてクリア  | このコンテンツスニペットは、[検索結果] ページに適用されているすべてのファセットをリセットするボタンのラベルを決定します。<br>![すべてのファセットをリセット](../media/facet-clear-all.png "すべてのファセットをリセット") |
| 検索/ファセット/ダウンロード   | ダウンロード   | このコンテンツスニペットは、[レコードの種類] ファセットの [注釈の添付ファイル] および [web ファイルレコード] の検索結果に表示されるラベルを決定します。<br>![ファセットのダウンロード](../media/facet-download.png "ファセットのダウンロード")|
| 検索/ファセット/Less    | 表示を減らす  | このコンテンツスニペットは、ファセットの結果を折りたたむボタンのラベルを決定します。<br>![表示するファセットを表示しない](../media/facet-show-less.png "表示するファセットを表示しない") |
| 検索/ファセット/ModifiedDate  | 更新日  | このコンテンツスニペットは、変更された日付ファセットに対して表示されるヘッダーのラベルを決定します。<br>![更新日](../media/facet-modified-date.png "変更日ファセット")   |
| 検索/ファセット/その他   | さらに表示  | このコンテンツスニペットは、ファセットの結果を展開するボタンのラベルを決定します。<br>![さらにファセットを表示](../media/facet-show-more.png "さらにファセットを表示")  |
| 検索/ファセット/製品  | Products | このコンテンツスニペットは、Products ファセットのラベルを決定します。<br>![Products ファセット](../media/facet-product.png "Products ファセット")  |
| 検索/ファセット/評価   | 評価   | このコンテンツスニペットは、評価ファセットのラベルを決定します。<br>![評価ファセット](../media/facet-rating.png "評価ファセット")  |
| 検索/ファセット/RecordType   | レコードの種類 | このコンテンツスニペットは、レコードの種類のファセットのラベルを決定します。<br>![レコード型ファセット](../media/facet-record-type.png "レコード型ファセット")     |
| 検索/ファセット/順序の AverageUserRating | 平均ユーザー評価 | このコンテンツスニペットでは、[検索結果] ページの [並べ替え] ドロップダウンリストにある [平均ユーザー評価で並べ替え] オプションに対して表示されるラベルを決定します。<br>![平均ユーザー評価で並べ替え](../media/sort-avg-user-rating.png "平均ユーザー評価で並べ替え")  |
| 検索/ファセット/順序/関連性| 関連性| このコンテンツスニペットでは、[検索結果] ページの [並べ替え] ドロップダウンリストにある [関連性に基づいて並べ替え] オプションに対して表示されるラベルを決定します。<br>![関連性順に並べ替え](../media/sort-relevance.png "関連性順に並べ替え")|
| 検索/ファセット/順序の付いた/ビュー| カウントの表示| このコンテンツスニペットは、[検索結果] ページの [並べ替え] ドロップダウンリストにある [ビュー数で並べ替え] オプションに対して表示されるラベルを決定します。<br>![表示数で並べ替え](../media/sort-view-count.png "表示数で並べ替え")|
|||

## <a name="entity-specific-handling"></a>エンティティ固有の処理

- **ケース**: 既定では、検索可能なケースは、 **[Web に公開]** フィールドが**True**に設定されている**解決済み**の状態のみです。 この動作を変更するには、ケースエンティティのポータルの検索ビューを更新し、ポータルの検索ビューで使用できるフィルターを削除します。 ただし、このチェックボックスがオフになっている場合は、Customer Service-Case web テンプレートが適切に変更されていることを確認することが重要です。この web テンプレートでは、すべてのユーザーがアクティブであり、web に公開されていないケースを表示することが制限されているためです。 Web テンプレートが変更されていない場合は、検索結果にケースが表示されます。 ただし、これらを選択すると、[アクセス許可の拒否] エラーと共に [ケースの詳細] web ページが表示されます。

- **ナレッジベース**: ナレッジ項目は、**内部**フィールドが **[いいえ]** に設定されている**公開済み**の状態の場合にのみ検索できます。 この動作は変更できません。 ナレッジ項目では、次のように、検索結果で特別な機能を使用することもできます。

    - **ファセット**: 2 つの特殊なファセットは、ナレッジ項目に対してのみ使用できます。また、検索結果でナレッジ項目レコードを利用できる場合に表示されます。

        - **評価ファセット**: このファセットを使用すると、ナレッジ項目の平均評価に基づいて検索結果をフィルター処理できます。

        - **製品ファセット**: このファセットを使用すると、ナレッジ項目に関連付けられている製品に基づいて検索結果をフィルター処理できます。

    - **添付ファイルの検索**: この機能を使用すると、ナレッジ項目に関連付けられている添付ファイルやメモを検索できます。 これにより、ポータルで公開されているノートまたは添付ファイルのメモの説明、タイトル、添付ファイル名、添付ファイルの内容を検索できます。 詳細情報:[添付ファイルのコンテンツ内の検索](search-file-attachment.md)

## <a name="special-characters-and-syntax-supported-by-search"></a>検索でサポートされている特殊文字と構文

ポータルのグローバル検索の一部として、検索結果をより適切にフィルター処理するために、さまざまな特殊文字と構文がサポートされています。 これらの特殊文字と構文は、次のグループに広く分割されています。

- **用語**: 検索のためにユーザーが入力したすべてのクエリが、用語と演算子に解析されます。 用語の種類は次のとおりです。 

    - **1**つの用語: 単一の語句は単一の単語です。 たとえば、クエリ {hello world} は、"hello" と "world" という2つの単一の用語に解析されます。 各用語は個別に検索されます。 このため、クエリ {hello world} では、"hello" または "world" という用語を含むすべてのレコードが検索結果に表示されます。

    - **語句**: 語句は、二重引用符 ("") で囲まれた用語のグループです。 たとえば、クエリ {"hello world"} は、"hello world" という語句として解析されます。 各句は完全に検索されます。 したがって、クエリ {"hello world"} では、完全な語句 "hello world" を含むすべてのレコードが検索結果に表示され、"hello" または "world" のみを含むすべてのレコードが表示されません。

    各検索クエリは、ブール演算子を使用して結合され、複雑なクエリを作成する、任意の型のうちの1つまたは複数の用語で構成できます。

- **用語の修飾子**

    - **ワイルドカード検索**: 検索クエリの1つの条件内で使用できるワイルドカードの種類は2つあります (句クエリ内ではありません)。単一文字のワイルドカード検索と複数の文字のワイルドカード検索です。

        - **1 文字のワイルドカード検索**: 1 文字のワイルドカード検索を実行するには、疑問符 (?) 記号を使用します。 1文字のワイルドカード検索では、単一の文字が置換された用語が検索されます。 たとえば、"text" または "test" を検索するには、検索クエリを "te? t" として使用できます。

        - **複数文字のワイルドカード検索**: 複数の文字のワイルドカード検索を実行するには、アスタリスク (\*) 記号を使用します。 複数の文字のワイルドカード検索では、0個以上の文字が検索対象になります。 たとえば、テスト、テスト、またはテスト担当者を検索するには、検索クエリを "test" として使用し*ます。クエリの途中で、複数の文字のワイルドカード検索を使用することもできます。たとえば、"te*t" のようにします。

        > [!NOTE]
        > - \* または? を使用することはできません。 検索の最初の文字としての記号。
        > - ワイルドカード検索は、語句クエリでは使用できません。 たとえば、クエリを "地獄 * world" として使用すると、"hello world" というテキストの結果は表示されません。

    - **近接検索**: 近接検索を使用すると、特定の距離内にある単語を相互に検索することができます。 たとえば、単語 "Picture" と "ぼやけ" をそれぞれ10語の中に表示する場合は、近接検索を使用できます。
    
        近接検索を実行するには、クエリの末尾にティルダ (~) 記号を使用します。 たとえば、単語 "Picture" と "ぼやけ" をそれぞれ10の単語の中に表示する場合、クエリは "画像がぼやけています" ~ 10 のようになります。

    - **用語のブースト**: グローバル検索では、検索条件に基づいて一致するドキュメントの関連性レベルが提供されます。 用語をブーストするには、検索する用語の最後に、増幅率 (数値) を指定してキャレット (^) 記号を使用します。 増加率が高いほど、用語の関連性が高くなります。

        ブーストを使用すると、用語を上げることでドキュメントの関連性を制御できます。 たとえば、スマートテレビを検索していて、スマートな用語をより関連性の高いものにするには、^ 記号を使用して、用語の横にあるブースト係数を使用してください。 「Smart ^ 4 TV」と入力します。 これにより、スマートという用語のドキュメントがより関連性の高いものとして表示されるようになります。

        次の例のように、語句の語句を上げることもできます。スマート TV ^ 4 の新しいテレビ。 この場合、"スマート TV" という語句は、"新しいテレビ" と比較してブーストされます。

        既定では、ブースト係数は1です。 ブースト係数は正の値である必要がありますが、1より小さくなることがあります (たとえば、0.2)。

- **ブール**演算子: ブール演算子を使用して、条件を組み合わせることができます。 グローバル検索では、ブール演算子として、OR、AND、NOT、"+"、および "-" がサポートされています。

    > [!NOTE]
    > ブール演算子は大文字で記述する必要があります。

    - **また**は: or 演算子は、既定の組み合わせ演算子です。 つまり、2つの項の間にブール演算子がない場合は、OR 演算子が使用されます。 OR 演算子は、2つの用語をリンクし、いずれかの条件がレコード内に存在する場合は一致するレコードを検索します。 これは、集合を使用する共用体に相当します。 Symbol | |は、またはという語の代わりに使用できます。 たとえば、検索クエリ "スマート TV" (引用符を除く) は、スマートまたはテレビの単語が含まれているすべてのレコードを検索します。 このクエリは、"スマートまたはテレビ"、"スマート | |" として記述することもできます。TV」

    - **および:** AND 演算子は、両方の用語が1つのドキュメントのテキスト内の任意の場所に存在するレコードと一致します。 これは、セットを使用した積集合に相当します。 記号 & & は、との代わりに使用できます。 たとえば、検索クエリ "スマートとテレビ" (引用符を除く) では、スマートとテレビの語句を含むすべてのレコードが検索されます。 このクエリは、"スマート & & テレビ" として記述することもできます。

    - **Not**: not 演算子は、ではなく、用語を含むレコードを除外します。 これは、セットを使用した場合と同じです。 シンボル。 NOT の代わりに使用できます。 たとえば、検索クエリ "スマートではない" (引用符を除く) は、"スマート" という単語が含まれているが、"TV" がないすべてのレコードを検索します。 このクエリは、"スマート! TV」

    - **正符号 (+) 記号**: 正符号 (+) 記号 (必須演算子とも呼ばれます) では、"+" 記号の後の用語がレコード内の任意の場所に存在する必要があります。 たとえば、"スマート + TV" という検索クエリでは、"TV" が存在している必要があるすべてのレコードが検索され、"スマート" という単語が表示されることもあります。 

    - **負符号 (–) 記号**: マイナス記号 (-) は、禁止演算子とも呼ばれ、"-" 記号の後にある語句を含むドキュメントを除外します。 たとえば、検索クエリ "スマート TV" では、"スマート" という単語があるすべてのレコードが検索され、"TV" が存在していないことを示します。

- **グループ化**: ポータルのグローバル検索では、かっこを使用して句をグループ化し、サブクエリを形成できます。 これは、クエリのブールロジックを制御する場合に非常に便利です。 たとえば、"HD" または "Smart" という用語のいずれかが存在するが、"TV" が常に存在するすべてのレコードを検索する場合、クエリは "(HD または Smart) AND TV" (引用符を除く) として記述できます。

## <a name="liquid-search-tag"></a>液体検索タグ

Searchindex タグを使用すると、水冷テンプレートからポータルのグローバル検索を呼び出すことができます。 詳細情報: [searchindex](../liquid/portals-entity-tags.md#searchindex)

> [!IMPORTANT]
> Searchindex タグを使用する場合、ファセットは結果の一部として返されません。また、ファセットをフィルターとして適用することもできません。

## <a name="update-search-index"></a>検索インデックスの更新

PowerApps ポータルでの検索インデックスの更新は、キャッシュの無効化と同様に自動的に行われます。 ただし、次の点に注意してください。

- 検索を有効にしたすべてのエンティティでは、変更通知メタデータフラグが有効になっている必要があります。そうしないと、ポータルに変更が通知されず、検索インデックスは更新されません。

- 変更は、ポータルの検索に反映されるまでに最大30分かかることがあります。 ただし、変更の95% は15分以内に更新されます。 添付ファイルが含まれている場合は、添付ファイルのサイズによっては時間がかかることがあります。

- 短時間でレコードの一括データ移行または一括更新を実行した後に、完全インデックスを手動で再構築することをお勧めします。 詳細については、「[フル検索インデックスの再構築](#rebuild-full-search-index)」を参照してください。

## <a name="rebuild-full-search-index"></a>フル検索インデックスの再構築

完全検索インデックスの再構築は、次の場合に必ず必要です。

- 検索プロパティのメタデータを変更するには、特定のクエリ固有のサイト設定の変更や、エンティティの検索ビューの変更などを行います。
- データの一括移行または更新が実行されます。
- ポータルに関連付けられている web サイトレコードは、Common Data Service 環境で変更されます。

ポータルから完全検索インデックスを再構築することもできます。
1.  ポータルに管理者としてサインインします。
2.  次のように URL に移動します。 `<portal_path>/_services/about`
3.  **[検索インデックスの再構築]** を選択します。

> [!IMPORTANT]
> フルインデックス再構築は非常に負荷のかかる操作であり、使用している時間帯にはポータルをダウンさせる可能性があるため、この操作は行わないでください。

## <a name="remove-an-entity-from-global-search"></a>グローバル検索からエンティティを削除する

場合によっては、ポータルのグローバル検索から特定のエンティティを完全に削除して、顧客が適切な結果を迅速に得られるようにすることが必要になる場合があります。

次の例では、ポータルのグローバル検索からケースエンティティを削除します。

### <a name="step-1-block-case-entity-from-getting-indexed"></a>手順 1: ブロックケースエンティティからインデックスを取得する

ケースエンティティでインデックスを取得しないようにするには、ポータルによってインデックスが作成されるレコードセットを定義するケースエンティティのビューの名前を変更する必要があります (Search/IndexQueryName サイト設定で定義)。 既定では、ビューの名前は [ポータル検索] です。

1.  [ポータル管理アプリ](configure-portal.md)を開きます。

2.  ページの上部にあるツールバーから**設定**アイコンを選択し、 **[詳細設定]** を選択します。

2.  **設定** > **カスタマイズ** > **カスタマイズしてシステムをカスタマイズ**します。

    ![システムをカスタマイズする](../media/customize-system.png "システムをカスタマイズする")

3.  [カスタマイズ] ダイアログで、左側のナビゲーションウィンドウにある [**コンポーネント** > **エンティティ** > **ケース**] に移動します。 

4.  **ケース**エンティティを展開し、 **[ビュー]** を選択します。

5.  一覧から**ポータルの検索**ビューを選択し、表示エディターで開きます。

    ![ケースビュー](../media/case-view.png "ケースビュー")

6.  ビューエディターで、 **[プロパティの表示]** を選択します。

    ![エディターの表示](../media/view-editor.png "エディターの表示")

7.  要件に従って、ビューの名前を変更します。 新しい名前に "Portal Search" という用語が含まれていないことを確認します。

    ![プロパティの表示](../media/view-properties.png "プロパティの表示")

8.  変更を保存し、ビューエディターを閉じます。

9.  **[すべてのカスタマイズの発行]** を選択します。

10. 「[フル検索インデックスの再構築](#rebuild-full-search-index)」セクションの説明に従って、完全なインデックスを再構築します。

> [!NOTE]
> この例では、ビューを直接編集することによって、アンマネージレイヤーで変更を行います。 マネージドソリューションを使用してこれを行うこともできます。

### <a name="step-2-remove-case-entity-from-the-ui"></a>手順 2: UI からケースエンティティを削除する

手順 1. で説明されている操作を実行した後、ケースエンティティはインデックスの取得から停止されます。 UI サーフェイス領域からケースエンティティを削除するには、ポータルのグローバル検索に関連付けられているサイト設定を変更する必要があります。 次のサイト設定を変更する必要があります。

検索/フィルター: 検索ページのフィルター、およびサイトのヘッダーの検索ボックスからケースエンティティが削除されます。 既定値は次のとおりです: `Content:adx_webpage,adx_webfile;Blogs:adx_blog,adx_blogpost;Forums:adx_communityforum,adx_communityforumthread,adx_communityforumpost;Ideas:adx_ideaforum,adx_idea;Help Desk:incident;Knowledge:knowledgearticle`

このサイト設定の値から `Help Desk:incident;` を削除して、UI の検索ボックスの横にあるフィルターからインシデントエンティティが削除されるようにする必要があります。

変更後の値は次のようになります。

`Content:adx_webpage,adx_webfile;Blogs:adx_blog,adx_blogpost;Forums:adx_communityforum,adx_communityforumthread,adx_communityforumpost;Ideas:adx_ideaforum,adx_idea;Knowledge:knowledgearticle`

このサイト設定が変更されると、ケースエンティティは、検索ページおよびヘッダー内のフィルターから削除されます。

![ページの検索](../media/search-on-page.png "ページの検索")

![ヘッダー内の検索](../media/search-in-header.png "ヘッダー内の検索")
