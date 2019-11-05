---
title: Twitter の接続の概要 | Microsoft Docs
description: いくつかの例が付いた Twitter への接続方法の段階的説明とすべての機能の紹介
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 07/12/2017
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: f58f8e15d1bd522bd9c24d7e3e1dfe9a69b4d257
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2019
ms.locfileid: "73541025"
---
# <a name="connect-to-twitter-from-powerapps"></a>PowerApps から Twitter に接続する
![Twitter](./media/connection-twitter/twittericon.png)

Twitter では、Twitter アカウントからツイートの投稿、ツイート、タイムライン、フレンド、フォロワーの取得を行うことができます。

こうした情報を、アプリのラベルに表示できます。 たとえば、入力テキスト ボックスを追加し、ユーザーにツイート テキストの入力を要求し、ツイートを "投稿" するボタンを追加することができます。 同様の方法で、ツイートを取得または検索し、アプリのラベルまたはギャラリー コントロールにテキストを表示できます。

このトピックでは、Twitter 接続の作成方法とアプリでの Twitter 接続の使用方法を説明し、使用可能な関数の一覧を示します。

[!INCLUDE [connection-requirements](../../../includes/connection-requirements.md)]

## <a name="connect-to-twitter"></a>Twitter への接続
1. PowerApps を開き、 **[新規]** を選んで **[空のアプリ]** を作成します。 携帯電話またはタブレットのレイアウトを選択します。 タブレットのレイアウトの方がワークスペースが広くなります。  

   ![空のアプリを開く](./media/connection-twitter/blank-app.png)
2. 右側のウィンドウで **[データ]** タブをクリックまたはタップし、 **[データソースの追加]** をクリックまたはタップします。
3. **[新しい接続]** 、 **[Twitter]** の順に選択します。  

    ![Twitter への接続](./media/connection-twitter/addconnection.png)

    ![Twitter への接続](./media/connection-twitter/add-twitter.png)
4. **[接続]** を選び、Twitter サインイン用の資格情報を入力して、 **[Authorize app (アプリの承認)]** を選びます。
5. **[データ ソースの追加]** を選びます。 **[データ ソース]** の下に接続が表示されます。  
    ![[オプション] ウィンドウを閉じる](./media/connection-twitter/twitterdatasource.png)

Twitter 接続が作成され、アプリに追加されます。 これで、この接続を使用できるようになりました。

## <a name="use-the-twitter-connection-in-your-app"></a>アプリで Twitter 接続を使用する
### <a name="show-a-timeline"></a>タイムラインを表示する
1. **[挿入]** メニューで、 **[ギャラリー]** を選択し、いずれかの**テキスト付き**ギャラリーを追加します。
2. タイムラインが表示されるようにします。  

   * 現在のユーザーのタイムラインを表示するには、ギャラリーの **[Items](../controls/properties-core.md)** プロパティを次の式に設定します。

       `Twitter.HomeTimeline().TweetText`  
       `Twitter.HomeTimeline({maxResults:3}).TweetText`  
   * 別のユーザーのタイムラインを表示するには、ギャラリーの **[Items](../controls/properties-core.md)** プロパティを次の式に設定します。  

       `Twitter.UserTimeline( *TwitterHandle* ).TweetText`

       二重引用符で囲んだ Twitter ハンドルまたは同等の値を入力します。 たとえば、`"satyanadella"` または `"powerapps"` と式に直接入力します。
   * **Tweep** という名前のテキスト入力コントロールを追加し、Default プロパティを `Tweep.Text` に設定します。 Tweep テキスト ボックスに、`satyanadella` などの Twitter ハンドルを入力します (引用符と @ 記号は除去します)。

       ギャラリー コントロールで、Items プロパティを次の式に設定します。  

       `Twitter.UserTimeline(Tweep.Text, {maxResults:5}).TweetText`

       ギャラリー コントロールに、入力した Twitter ハンドルのツイートが自動的に表示されます。

     > [!TIP]
     > これらの式の一部は、**maxResults** 引数を使って、タイムラインに最新のツイートを *x* 個表示します。
3. ギャラリーの **Items** プロパティを `Twitter.HomeTimeline()` に設定します。

    ギャラリーを選択すると、右側のペインにそのギャラリーのオプションが表示されます。
4. 1 番目のリストで **[TweetText]** 、2 番目のリストで **[TweetedBy]** 、3 番目のリストで **[CreatedAt]** を選択します。

    ギャラリーに、選択したプロパティの値が表示されるようになります。

### <a name="show-followers"></a>フォロワーを表示する
1. **テキスト付き**ギャラリーを使って、フォロワーの一部を表示します。  

   * 現在のユーザーのフォロワーを表示するには、ギャラリーの **[Items](../controls/properties-core.md)** プロパティを次の式に設定します。  

       `Twitter.MyFollowers()`  
       `Twitter.MyFollowers({maxResults:3})`
   * 別のユーザーのフォロワーを表示するには、ギャラリーの **[Items](../controls/properties-core.md)** プロパティを次の式に設定します。  

       `Twitter.Followers( *TwitterHandle* )`

       二重引用符で囲んだ Twitter ハンドルまたは同等の値を入力します。 たとえば、`"satyanadella"` または `"powerapps"` と式に直接入力します。
   * **Tweep** という名前のテキスト入力コントロールを追加し、Default プロパティを `Tweep.Text` に設定します。 Tweep テキスト ボックスに、`satyanadella` などの Twitter ハンドルを入力します (引用符と @ 記号は除去します)。

       ギャラリー コントロールで、Items プロパティを次の式に設定します。  

       `Twitter.Followers(Tweep.Text, {maxResults:5})`

       ギャラリー コントロールに、入力した Twitter ハンドルをフォローしているユーザーが自動的に表示されます。

     > [!TIP]
     > これらの式の一部は、**maxResults** 引数を使って、タイムラインに最新のツイートを *x* 個表示します。
2. ギャラリーの **Items** プロパティを `Twitter.MyFollowers()` に設定します。

    ギャラリーを選択すると、右側のペインにそのギャラリーのオプションが表示されます。
3. 2 番目のリストで **[UserName]** を選択し、3 番目のリストで **[FullName]** を選択します。

    ギャラリーに、選択したプロパティの値が表示されるようになります。

### <a name="show-followed-users"></a>フォローされているユーザーを表示する
1. **テキスト付き**ギャラリーを使って、フォローされているユーザーの一部を表示します。  

   * 現在のユーザーがフォローしているユーザーを表示するには、ギャラリーの **[Items](../controls/properties-core.md)** プロパティを次の式に設定します。  

       `Twitter.MyFollowing()`  
       `Twitter.MyFollowing({maxResults:3})`
   * 別のユーザーがフォローしているユーザーを表示するには、ギャラリーの **[Items](../controls/properties-core.md)** プロパティを次の式に設定します。

       `Twitter.Following( *TwitterHandle* )`

       二重引用符で囲んだ Twitter ハンドルまたは同等の値を入力します。 たとえば、`"satyanadella"` または `"powerapps"` と式に直接入力します。
   * **Tweep** という名前のテキスト入力コントロールを追加し、Default プロパティを `Tweep.Text` に設定します。 Tweep テキスト ボックスに、`satyanadella` などの Twitter ハンドルを入力します (引用符と @ 記号は除去します)。

       ギャラリー コントロールで、Items プロパティを次の式に設定します。  

       `Twitter.Following(Tweep.Text, {maxResults:5})`

       ギャラリー コントロールに、自分がフォローして他のハンドルが自動的に表示されます。

     ギャラリーを選択すると、右側のペインにそのギャラリーのオプションが表示されます。
2. **[Body1]** リストで **[Description]** を、 **[Heading1]** リストで **[UserName]** を、 **[Subtitle1]** リストで **[FullName]** を、それぞれ選択します。

    ギャラリーに、選択したプロパティの値が表示されるようになります。

### <a name="show-information-about-a-user"></a>ユーザーについての情報を表示する
ラベルを追加し、その **[Text](../controls/properties-core.md)** プロパティを次の数式のいずれかに設定します。  

* `twitter.User( *TwitterHandle* ).Description`
* `twitter.User( *TwitterHandle* ).FullName`
* `twitter.User( *TwitterHandle* ).Location`
* `twitter.User( *TwitterHandle* ).UserName`
* `twitter.User( *TwitterHandle* ).FollowersCount`
* `twitter.User( *TwitterHandle* ).FriendsCount`
* `twitter.User( *TwitterHandle* ).Id`
* `twitter.User( *TwitterHandle* ).StatusesCount`

二重引用符で囲んだ Twitter ハンドルまたは同等の値を入力します。 たとえば、`"satyanadella"` または `"powerapps"` と式に直接入力します。

または、このトピックで行っているように、入力テキスト コントロールを使って Twitter ハンドルを入力することもできます。

### <a name="search-tweets"></a>ツイートを検索する
1. **テキスト付き**ギャラリーを使用し、その **[Items](../controls/properties-core.md)** プロパティを次の式に設定します。  

    `Twitter.SearchTweet( *SearchTerm* ).TweetText`

    *SearchTerm* は、二重引用符で囲んで入力するか、同等の値を参照します。 たとえば、`"PowerApps"` または `"microsoft"` と式に直接入力します。

    または、このトピックで行っているように、**入力テキスト** コントロールを使って検索語句を指定することもできます。

    > [!TIP]
   > maxResults を使って最初の 5 つの結果を表示します。  

    `Twitter.SearchTweet(SearchTerm.Text, {maxResults:5}).TweetText`
2. ギャラリーの **Items** プロパティを `Twitter.SearchTweet(SearchTerm.Text, {maxResults:5})` に設定します。

    ギャラリーを選択すると、右側のペインにそのギャラリーのオプションが表示されます。
3. 1 番目のリストで **[TweetText]** 、2 番目のリストで **[TweetedBy]** 、3 番目のリストで **[CreatedAt]** を選択します。

    ギャラリーに、選択したプロパティの値が表示されるようになります。

### <a name="send-a-tweet"></a>ツイートを送信する
1. テキスト入力コントロールを追加し、名前を **MyTweet** に変更します。
2. ボタンを追加し、その **[OnSelect](../controls/properties-core.md)** プロパティを次の式に設定します。  
    `Twitter.Tweet({tweetText: MyTweet.Text})`
3. F5 キーを押すか、[プレビュー] ボタン (![](./media/connection-twitter/preview.png)) を選びます。 **MyTweet** にテキストを入力し、ボタンを選択して入力したテキストをツイートします。
4. Esc キーを押して既定のワークスペースに戻ります。

## <a name="view-the-available-functions"></a>使用可能な関数の確認
この接続には、次の関数が含まれています。

| 関数名 | Description |
| --- | --- |
| [UserTimeline](connection-twitter.md#usertimeline) |指定したユーザーが投稿した最も最近のツイートのコレクションを取得します |
| [HomeTimeline](connection-twitter.md#hometimeline) |最近のツイートを取得し、自分と自分のフォロワーに投稿をリツイートします |
| [SearchTweet](connection-twitter.md#searchtweet) |指定したクエリに一致する、関連するツイートのコレクションを取得します |
| [Followers](connection-twitter.md#followers) |指定したユーザーをフォローしているユーザーを取得します |
| [MyFollowers](connection-twitter.md#myfollowers) |自分をフォローしているユーザーを取得します |
| [Following](connection-twitter.md#following) |指定したユーザーがフォローしているユーザーを取得します |
| [MyFollowing](connection-twitter.md#myfollowing) |自分がフォローしているユーザーを取得します |
| [User](connection-twitter.md#user) |指定したユーザーに関する詳細情報を取得します (例: ユーザー名、説明、フォロワー数など) |
| [Tweet](connection-twitter.md#tweet) |ツイートします |
| [OnNewTweet](connection-twitter.md#onnewtweet) |検索クエリに一致するツイートが新しく投稿されたときに、ワークフローをトリガーします |

### <a name="usertimeline"></a>UserTimeline
ユーザーのタイムラインを取得する: 指定したユーザーが投稿した最も最近のツイートのコレクションを取得します

#### <a name="input-properties"></a>入力プロパティ

| 名前 | データ型 | 必須 | Description |
| --- | --- | --- | --- |
| userName |string |はい |Twitter ハンドルです |
| maxResults |整数 |いいえ |取得するツイートの最大数です (例: {maxResults:5}) |

#### <a name="output-properties"></a>出力プロパティ

| プロパティ名 | データ型 | 必須 | Description |
| --- | --- | --- | --- |
| TweetText |string |はい | |
| TweetId |string |いいえ | |
| CreatedAt |string |いいえ | |
| RetweetCount |整数 |はい | |
| TweetedBy |string |はい | |
| MediaUrls |配列 |いいえ | |

### <a name="hometimeline"></a>HomeTimeline
ホーム タイムラインを取得する: 最近のツイートを取得し、自分と自分のフォロワーに投稿をリツイートします

#### <a name="input-properties"></a>入力プロパティ

| 名前 | データ型 | 必須 | Description |
| --- | --- | --- | --- |
| maxResults |整数 |いいえ |取得するツイートの最大数です (例: {maxResults:5}) |

#### <a name="output-properties"></a>出力プロパティ

| プロパティ名 | データ型 | 必須 | Description |
| --- | --- | --- | --- |
| TweetText |string |はい | |
| TweetId |string |いいえ | |
| CreatedAt |string |いいえ | |
| RetweetCount |整数 |はい | |
| TweetedBy |string |はい | |
| MediaUrls |配列 |いいえ | |

### <a name="searchtweet"></a>SearchTweet
ツイートを検索する: 指定したクエリに一致する、関連するツイートのコレクションを取得します

#### <a name="input-properties"></a>入力プロパティ

| 名前 | データ型 | 必須 | Description |
| --- | --- | --- | --- |
| searchQuery |string |はい |クエリ テキストです (Twitter でサポートされている任意のクエリ演算子を使用できます: https://www.twitter.com/search) |
| maxResults |整数 |いいえ |取得するツイートの最大数です (例: {maxResults:5}) |

#### <a name="output-properties"></a>出力プロパティ

| プロパティ名 | データ型 | 必須 | Description |
| --- | --- | --- | --- |
| TweetText |string |はい | |
| TweetId |string |いいえ | |
| CreatedAt |string |いいえ | |
| RetweetCount |整数 |はい | |
| TweetedBy |string |はい | |
| MediaUrls |配列 |いいえ | |

### <a name="followers"></a>Followers
フォロワーを取得する: 指定したユーザーをフォローしているユーザーを取得します

#### <a name="input-properties"></a>入力プロパティ

| 名前 | データ型 | 必須 | Description |
| --- | --- | --- | --- |
| userName |string |はい |ユーザーの Twitter ハンドルです |
| maxResults |整数 |いいえ |取得するユーザーの最大数です (例: {maxResults:5}) |

#### <a name="output-properties"></a>出力プロパティ

| プロパティ名 | データ型 | 必須 | Description |
| --- | --- | --- | --- |
| FullName |string |はい | |
| Location |string |はい | |
| Id |整数 |いいえ | |
| UserName |string |はい | |
| FollowersCount |整数 |いいえ | |
| Description |string |はい | |
| StatusesCount |整数 |いいえ | |
| FriendsCount |整数 |いいえ | |

### <a name="myfollowers"></a>MyFollowers
自分のフォロワーを取得する: 自分をフォローしているユーザーを取得します

#### <a name="input-properties"></a>入力プロパティ

| 名前 | データ型 | 必須 | Description |
| --- | --- | --- | --- |
| maxResults |整数 |いいえ |取得するユーザーの最大数です (例: {maxResults:5}) |

#### <a name="output-properties"></a>出力プロパティ

| プロパティ名 | データ型 | 必須 | Description |
| --- | --- | --- | --- |
| FullName |string |はい | |
| Location |string |はい | |
| Id |整数 |いいえ | |
| UserName |string |はい | |
| FollowersCount |整数 |いいえ | |
| Description |string |はい | |
| StatusesCount |整数 |いいえ | |
| FriendsCount |整数 |いいえ | |

### <a name="following"></a>Following
フォローしているユーザーを取得する: 指定したユーザーがフォローしているユーザーを取得します

#### <a name="input-properties"></a>入力プロパティ

| 名前 | データ型 | 必須 | Description |
| --- | --- | --- | --- |
| userName |string |はい |ユーザーの Twitter ハンドルです |
| maxResults |整数 |いいえ |取得するユーザーの最大数です (例: {maxResults:5}) |

#### <a name="output-properties"></a>出力プロパティ

| プロパティ名 | データ型 | 必須 | Description |
| --- | --- | --- | --- |
| FullName |string |はい | |
| Location |string |はい | |
| Id |整数 |いいえ | |
| UserName |string |はい | |
| FollowersCount |整数 |いいえ | |
| Description |string |はい | |
| StatusesCount |整数 |いいえ | |
| FriendsCount |整数 |いいえ | |

### <a name="myfollowing"></a>MyFollowing
自分がフォローしているユーザーを取得する: 自分がフォローしているユーザーを取得します

#### <a name="input-properties"></a>入力プロパティ

| 名前 | データ型 | 必須 | Description |
| --- | --- | --- | --- |
| maxResults |整数 |いいえ |取得するユーザーの最大数です (例: {maxResults:5}) |

#### <a name="output-properties"></a>出力プロパティ

| プロパティ名 | データ型 | 必須 | Description |
| --- | --- | --- | --- |
| FullName |string |はい | |
| Location |string |はい | |
| Id |整数 |いいえ | |
| UserName |string |はい | |
| FollowersCount |整数 |いいえ | |
| Description |string |はい | |
| StatusesCount |整数 |いいえ | |
| FriendsCount |整数 |いいえ | |

### <a name="user"></a>User
ユーザーを取得する: 指定したユーザーに関する詳細情報を取得します (例: ユーザー名、説明、フォロワー数など)

#### <a name="input-properties"></a>入力プロパティ

| 名前 | データ型 | 必須 | Description |
| --- | --- | --- | --- |
| userName |string |はい |ユーザーの Twitter ハンドルです |

#### <a name="output-properties"></a>出力プロパティ

| プロパティ名 | データ型 | 必須 | Description |
| --- | --- | --- | --- |
| FullName |string |はい | |
| Location |string |はい | |
| Id |整数 |いいえ | |
| UserName |string |はい | |
| FollowersCount |整数 |いいえ | |
| Description |string |はい | |
| StatusesCount |整数 |いいえ | |
| FriendsCount |整数 |いいえ | |

### <a name="tweet"></a>ツイートします
新しいツイートを投稿する: ツイートします

#### <a name="input-properties"></a>入力プロパティ

| 名前 | データ型 | 必須 | Description |
| --- | --- | --- | --- |
| tweetText |string |いいえ |投稿するテキストです (例: {tweetText:"こんにちは"} |
| body |string |いいえ |投稿するメディアです |

#### <a name="output-properties"></a>出力プロパティ

| プロパティ名 | データ型 | 必須 | Description |
| --- | --- | --- | --- |
| TweetId |string |はい | |

### <a name="onnewtweet"></a>OnNewTweet
新しいツイートがあったときの処理: 検索クエリに一致するツイートが新しく投稿されたときに、ワークフローをトリガーします

#### <a name="input-properties"></a>入力プロパティ

| 名前 | データ型 | 必須 | Description |
| --- | --- | --- | --- |
| searchQuery |string |はい |クエリ テキストです (Twitter でサポートされている任意のクエリ演算子を使用できます: https://www.twitter.com/search) |

#### <a name="output-properties"></a>出力プロパティ

| プロパティ名 | データ型 | 必須 | Description |
| --- | --- | --- | --- |
| 値 |配列 |いいえ | |

## <a name="helpful-links"></a>便利なリンク
[利用可能な接続](../connections-list.md)をすべて表示する。  
アプリに[接続を追加する](../add-manage-connections.md)方法を確認する。

