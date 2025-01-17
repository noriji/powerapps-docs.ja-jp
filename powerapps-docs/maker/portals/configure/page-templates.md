---
title: PowerApps ポータルでページテンプレートを作成および管理する |MicrosoftDocs
description: PowerApps ポータルでページテンプレートを作成および管理する方法について説明します。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: ef4f61e7b9165d8d2c4abbc70c0bce65957665ab
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2019
ms.locfileid: "73551694"
---
# <a name="create-and-manage-page-templates"></a>ページテンプレートの作成と管理

Web ページはポータルサイトマップ内のノードであり、ポータルユーザーがアクセスできるコンテンツを表しますが、ページテンプレートは、web サイト全体で一貫したルックアンドフィールを維持するための手段を提供する実際の .aspx ページを表します。 ページテンプレートは、ASP.NET ページ、マスターページ、カスケードスタイルシート (CSS)、ユーザーコントロール、およびサーバーコントロールを使用して作成されます。

サイトの新しい web ページを作成するときに、フロントサイド発行を使用するか、ポータルインターフェイスを使用するかにかかわらず、ポータルのユーザーにページのコンテンツを表示するページテンプレートを選択する必要があります。

Web ページとページテンプレートの違いは、URL と実際の .aspx ページの違いであり、コンテンツを表示するためのブループリントとして機能することがよくあります。 各 web ページは、ユーザーが移動できるサイト内の特定の URL を表します。 ユーザーが URL に移動すると、その URL に関連付けられているコンテンツが表示されます。 ただし、web ページには、コンテンツの表示方法に関する情報は含まれていません。  これは、ユーザーに表示される HTML を生成する実際の .aspx ページであるページテンプレートによって決定されます。

新しい web ページを作成する場合は、既存のテンプレートの一覧からページテンプレートを選択する必要があります。 各スタートポータルには、いくつかのページテンプレートが含まれています。 これらのポータルを独自の web サイトのベースとして使用する場合、ポータルの機能をデモンストレーションする基本的な方法として、これらのテンプレートは便利です。 ただし、ポータルの開発者は、これらのページのレイアウトを大幅に変更する必要があります。 ほとんどの場合、"ページ" ページテンプレートは一般的な目的で使用するページテンプレートになります。このテンプレートを使用する web ページには、コンテンツが表示され、ナビゲーションアイテムとして表示される子ページのリストも表示されます。

## <a name="manage-page-templates"></a>ページテンプレートの管理

新しいページテンプレートを作成する必要があるのは、web サイト (ポータル開発者のタスク) のコンテンツを表示するための新しい .aspx ページを作成する場合のみです。 実際には、単純にサイトのレイアウトをカスタマイズするために、ポータルの開発者は、既存の .aspx ページを変更するだけで済みます。

1. [ポータル管理アプリ](configure-portal.md)をペンします。

2. **ポータル** > **ページテンプレート**にアクセスします。

3. 新しいページテンプレートを作成するには、 **[新規]** を選択します。

4. 既存のページテンプレートを編集するには、[ページテンプレート名] を選択します。

5. フィールドに適切な値を入力します。

6. **[保存して閉じる]** を選択します。

### <a name="page-template-attributes"></a>ページテンプレート属性

|名前 |Description |
|-----|--------|
|名前    |参照に使用されるテンプレートの名前。   |
|用   |関連付けられている web サイト。   |
|種類   |テンプレートの種類。レンダリングする内容をテンプレートでどのように決定するかを制御します。<ul><li>**書き換え**: 指定された ASP.NET テンプレートを表示するために、[URL の書き換え] フィールドを使用します。</li><li>**Web テンプレート**: web テンプレートフィールドを使用して、指定された web テンプレートを表示します。</li></ul>   |
|URL の書き換え   |コンテンツを表示する物理 ASP.NET ページ (または、.ashx などの他のリソース) のパス。<br> このフィールドは、 **[種類]** ボックスの一覧から **[URL の書き換え]** が選択されている場合にのみ表示されます。 |
|Web テンプレート   |このテンプレートを表示するために使用される web テンプレートへの参照。<br>このフィールドは、 **[種類]** ボックスの一覧から **[Web テンプレート]** が選択されている場合にのみ表示されます。  |
|既定値   |[はい] の場合、クライアント側編集ツールのドロップダウンに割り当てられた既定のテンプレートが使用されます。   |
|エンティティ名   |このテンプレートが表示する必要があるページエンティティ型。 これは、コンテンツの作成者に適切なテンプレートを選択するために、フロントサイド編集システムによって使用されます。<br>通常、これは Web ページ (adx_webpage) になりますが、フォーラム、フォーラムスレッド、ブログ、ブログ投稿など、別のポータルエンティティになることがあります。   |
|Description  |このテンプレートの説明。フロント側編集ユーザーの利点があります。 |
|||

