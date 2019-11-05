---
title: ポータルのサイト設定を構成する |MicrosoftDocs
description: ポータルのサイト設定と、組織内のすべてのポータルのグローバル設定を追加して構成する方法について説明します。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/18/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 19dca44c26565bc55dcfaace48987b69dd0a195f
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2019
ms.locfileid: "73542724"
---
# <a name="configure-site-settings-for-portals"></a>ポータルのサイト設定を構成する

サイト設定は、ポータルの動作や視覚スタイルを変更するために web サイトコードによって使用される、構成可能な名前付きの値です。 通常、開発者は web サイトのコードを作成するときに、さまざまなコンポーネントのサイト設定を参照して、エンドユーザーが設定値を変更して web サイトを変更できるようにします。コードを変更したり、再コンパイルしたり、web サイトを再デプロイしたりする必要はありません。

PowerApps ポータルのインストールに用意されているサンプルポータルには、背景スタイル、テキストの色、レイアウトの幅など、サイト内の多くの視覚要素を変更するために使用できる、さまざまなスタイル用の構成可能なサイト設定がいくつか含まれています。
次の種類のサイト設定を管理できます。

- **グローバルポータルの設定**: これらの設定は、追加する Common Data Service 環境に関連付けられているすべてのポータルに適用されます。
- **ポータルサイトの設定**: これらの設定は、追加される Common Data Service 環境に関連付けられている特定のポータル (web サイトレコード) に適用されます。


## <a name="manage-portal-site-settings"></a>ポータルサイト設定の管理

1. [[ポータルの設定](../manage-existing-portals.md#settings)] にアクセスし、 **[サイトの設定]** を選択します。

2. 新しい設定を作成するには、 **[新規]** を選択します。

3. 既存の設定を編集するには、グリッドに表示されている**サイト設定**を選択します。

4. 表示されるフィールドの値を指定します。 

    - **Name**: 適切な設定を取得するために web サイトコードによって参照されるラベル。 この名前は、関連付けられている web サイトで一意である必要があります。これは、設定を取得するコードが、一致する名前を持つ最初のレコードを取得するためです。
    
    - **Website**: 関連付けられている web サイト。 
    
    - **値**: 設定
    
    - **説明**: 設定または特別な指示の目的。

5. **[保存して閉じる]** を選択します。

> [!NOTE] 
> Bing マップの統合は、ドイツのソブリン Cloud ではサポートされていません。 この環境で Bingmaps/credentials 設定を作成しようとすると、エラーメッセージが表示されます。

## <a name="portal-site-settings"></a>ポータルサイトの設定

|名前|Value|Description|
|----|-----|-----------|
|認証/登録/RequiresConfirmation|FALSE |ブール値 true を指定すると、電子メール確認が有効になり、オープン登録が無効になります。 既定値: False |
|認証/登録/RequiresInvitation|FALSE |ブール値 true を指定すると、招待コード機能が有効になり、オープン登録が無効になります。 既定値: False |
|会議名|ポータルカンファレンス|特定のポータルの会議を表す adx_conference レコードの名前。|
|ヘルプデスク/CaseEntitlementEnabled|本来|ヘルプデスクケースの権利が有効になっているかどうかを示すブール値。 既定値: false|
|ヘルプデスク/たわみ/DefaultSelectedProductName| |Producttypecode 値が100000001に等しい製品が複数存在する場合に、ヘルプデスクケースに表示されるドロップダウンで既定で選択されている製品レコードの名前。|
|プロファイル/ForceSignUp|FALSE|"True" に設定した場合、ブール値を指定すると、ユーザーは自分のプロファイル情報を更新してから、web サイトのコンテンツにアクセスできるようになります。 既定値: False|
|プロファイル/ShowMarketingOptionsPanel|本来|プロファイルのマーケティング通信設定を指定するためのフィールドを一覧表示するパネルを表示するかどうかを示すブール値。 既定値: False|
|検索/有効化|本来|検索が有効かどうかを示すブール値です。|
|検索/フィルター|コンテンツ: adx_webpage;イベント: adx_event、adx_eventschedule<br>ブログ: adx_blog、adx_blogpost、adx_blogpostcomment;<br>フォーラム: adx_communityforum、adx_communityforumthread、adx_communityforumpost;<br>アイデア: adx_ideaforum、adx_idea、adx_ideacomment;<br>問題: adx_issueforum、adx_issue、adx_issuecommentヘルプデスク: インシデント|検索論理名フィルターオプションのコレクション。 ここで値を定義すると、サイト全体の検索にドロップダウンフィルターオプションが追加されます。 この値は、名前と値のペアの形式で、コロンで区切られた名前と値、およびセミコロンで区切られたペアである必要があります。<br>例: "フォーラム: adx_communityforum, adx_communityforumthread, adx_communityforumpost;ブログ: adx_blog、adx_blogpost、adx_blogpostcomment|
|検索/IndexQueryName|ポータルの検索|ポータル検索クエリで使用されるシステムビューの名前。 既定: ポータル検索|
|検索/クエリ|\+ (@Query) タイトル:(@Query) logicalname: adx_webpage ~ 0.9 ^ 0.2<br> -adx_webfile ~ 0.9 adx_partialurl:(@Query)<br> logicalname: adx_blogpost ~ 0.9 ^ 0.1-logicalname: adx_communityforumthread ~ 0.9|サイト検索のクエリを上書きして、追加の重みとフィルターを適用します。 @Query は、ユーザーが入力したクエリテキストです。 Lucene クエリ構文リファレンス: [https://lucene.apache.org/core/old_versioned_docs/versions/2_9_1/queryparsersyntax.html](https://lucene.apache.org/core/old_versioned_docs/versions/2_9_1/queryparsersyntax.html)| 
|検索/ステマー|英語|ポータル検索のステミングアルゴリズムで使用される言語です。 既定値: 英語|
|顧客サポート/DisplayAllUserActivitiesOnTimeline|FALSE| |
|Authentication/[Protocol]/[Provider]/allowcontactmappingwithemail| |電子メールに基づく連絡先レコードへの自動関連付けを許可します。 詳細については、[ここ](azure-ad-b2c.md#allow-auto-association-to-a-contact-record-based-on-email)をクリックしてください。|
|||

ポータルのさまざまな機能に関連したサイト設定については、以下を参照してください。

- [認証 id](set-authentication-identity.md)
- [Azure AD B2C プロバイダー](azure-ad-b2c.md)
- [OAuth 2.0](configure-oauth2-settings.md)
- [Open ID Connect](configure-openid-settings.md)
- [WS-FEDERATION](configure-ws-federation-settings.md)
- [SAML 2.0](configure-saml2-settings.md)
- [Id プロバイダーを Azure AD B2C に移行する](migrate-identity-providers.md)
- [添付ファイルのコンテンツ内を検索する](search-file-attachment.md)
- [日付と時刻フィールドの動作と形式](behavior-format-date-time-field.md)
- [位置情報の追加](add-geolocation.md)
- [一般的なデータ保護規則の実装](https://docs.microsoft.com/dynamics365/customer-engagement/portals/implement-gdpr)
- [ヘッダーとフッターの出力キャッシュを有効にする](https://docs.microsoft.com/dynamics365/customer-engagement/portals/enable-header-footer-output-caching)

## <a name="manage-global-portal-settings"></a>グローバルポータルの設定を管理する

1. [[ポータルの設定](../manage-existing-portals.md#settings)] にアクセスし、 **[サイトの設定]** を選択します。

2. **設定**&gt;**設定**にアクセスします。

3. 新しい設定を作成するには、 **[新規]** を選択します。

4. 既存の設定を編集するには、グリッドに表示されている**サイト設定**を選択します。

5. 表示されるフィールドの値を指定します。 

    - **名前**: 適切な設定を取得するためにコードによって参照される一意の名前。

    - **値**: 設定

    - **説明**: 設定または特別な指示の目的。

6. **[保存して閉じる]** を選択します。

> [!NOTE] 
> Bing マップの統合は、ドイツのソブリン Cloud ではサポートされていません。 この環境で BinMap/Key または Adxstudio/ProductivityPack/BingMap/Key 設定を作成しようとすると、エラーメッセージが表示されます。


