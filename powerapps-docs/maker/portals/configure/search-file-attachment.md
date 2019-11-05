---
title: ポータルで添付ファイルのコンテンツ内を検索する |MicrosoftDocs
description: ポータルで、添付ファイルのコンテンツ内を検索するようにポータルを構成する方法について説明します。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 52d7701ac84072c84886ea86969f28809d0e7960
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2019
ms.locfileid: "73551648"
---
# <a name="search-within-file-attachment-content"></a>添付ファイルのコンテンツ内を検索する

メモの添付ファイルを使用して、サポート技術情報の記事にダウンロード可能なファイルを含めることができます。 Web ファイルを使用して、ダウンロード可能なコンテンツを含む FAQ ページを作成することもできます。

ポータルを構成して、サポート技術情報の記事の添付ファイルの内容をポータルユーザーが検索できるようにすることができます。 これにより、ユーザーが探している情報を見つけることができます。

サポート技術情報の記事では、定義済みのプレフィックスを持つメモの添付ファイルのインデックスが作成されます。 Web ファイルでは、最新のメモの添付ファイルにインデックスが付けられます。

添付ファイルのインデックスを作成するには、次のサイト設定を作成し、その値を**True**に設定する必要があります。

|サイト設定|Description|
|------------|-----------|
|添付ファイルの検索/インデックスの検索|サポート技術情報の記事および web ファイルのメモ添付ファイルのコンテンツにインデックスを作成するかどうかを示します。 既定では、 **False**に設定されています。|
|KnowledgeManagement/DisplayNotes|サポート技術情報の記事の添付ファイルにインデックスを作成するかどうかを示します。 既定では、 **False**に設定されています。|
|||

> [!NOTE]
> 検索できるのは、ナレッジ項目に関連付けられているファイルだけです。 Web ファイルに添付されているファイルは検索できません。

語句を検索すると、検索結果に添付ファイルも含まれます。 検索用語がメモの添付ファイルと一致する場合は、対応するサポート技術情報の記事へのリンクも表示されます。 ダウンロード可能な添付ファイルを表示するには、左側のウィンドウで **[レコードの種類]** の下の **[ダウンロード]** を選択します。 **ダウンロード**ラベルを変更するには、[検索]/[ファセット]/[ダウンロード] コンテンツスニペットを編集します。 既定では、値は **[ダウンロード]** に設定されています。

![添付ファイルのダウンロード](../media/search-attachment-content.png "添付ファイルのダウンロード") 

> [!NOTE]
> - この機能を使用するには、[関連性の検索を有効](https://docs.microsoft.com/dynamics365/customer-engagement/admin/configure-relevance-search-organization)にする必要があります。 詳細情報:[関連性検索](https://docs.microsoft.com/dynamics365/customer-engagement/basics/relevance-search-results)
 
## <a name="update-portal-configurations"></a>ポータルの構成を更新する

2018年4月より前のポータルを既に所有していて、ポータルを最新バージョンにアップグレードした場合は、次の構成を使用して、新しいポータルのインストールと同じユーザーエクスペリエンスを持つ必要があります。

**コンテンツスニペット**

注釈および web ファイルのダウンロードの検索結果に表示されるラベルを変更するには、コンテンツスニペットの検索、ファセット、ダウンロードを作成し、必要に応じてその値を設定します。 既定値は **ダウンロード**中です。

**Web ファイル**

Web ファイルに関連付けられている添付ファイルのコンテンツにインデックスを作成できるようになりました。 CSS ファイルやイメージファイル (たとえば、ブートストラップ、.css、.jpg など) の既存の web ファイルを更新して、検索から除外することができます。 

1. [ポータル管理アプリ](configure-portal.md)を開き、[**ポータル** > **Web ファイル**] にアクセスします。
2. 検索から除外するファイルを開きます。
3. **[その他]** の **[検索から除外]** フィールドで [**はい]** を選択します。

**Web テンプレート**

ファセット検索結果テンプレート web テンプレートが改訂され、サポート技術情報の記事に関連付けられているファイルが、関連する記事リンクを含むプライマリ検索結果項目として表示されます。 ファセット検索結果テンプレート web テンプレートを次のソースに更新する必要があります。

```
{% assign openTag = '{{' %}
{% assign closingTag = '}}' %}
{%raw%}
  <script id=search-view-results type=text/x-handlebars-template>
   {{#if items}}
    <div class=page-header>
     <h3>{%endraw%}{{openTag}} stringFormat {{ resx.Search_Results_Format_String }} firstResultNumber lastResultNumber itemCount {{closingTag}}{%raw%}
      <em class=querytext>{{{query}}}</em>
      {{#if isResetVisible}}
       <a class="btn btn-default btn-sm facet-clear-all" role="button" title="{%endraw%}{{ snippets['Search/Facet/ClearConstraints'] | default: res['Search_Filter_Clear_All'] }}{%raw%}" tabIndex="0">{%endraw%}{{ snippets['Search/Facet/ClearConstraints'] | default: res['Search_Filter_Clear_All'] }}{%raw%}</a>
      {{/if}}
     </h3>
    </div>
   <ul>
    {{#each items}}
     <li>
      <h3><a title={{title}} href={{url}}>{{#if parent}}<span class=glyphicon glyphicon-file pull-left text-muted aria-hidden=true></span>{{/if}}{{title}}</a></h3>
      <p class=fragment>{{{fragment}}}</p>
      {{#if parent}}
       <p class=small related-article>{%endraw%}{{ resx.Related_Article }}{%raw%}: <a title={{parent.title}} href={{parent.absoluteUrl}}>{{parent.title}}</a></p>
      {{/if}}
      <ul class=note-group small list-unstyled>
       {{#if relatedNotes}}
        {{#each relatedNotes}}
         <li class=note-item>
         {{#if isImage}}
          <a target=_blank title={{title}} href={{absoluteUrl}}><span class=glyphicon glyphicon-file aria-hidden=true></span>&nbsp;{{title}}</a>
         {{else}}
          <a title={{title}} href={{absoluteUrl}}><span class=glyphicon glyphicon-file aria-hidden=true></span>&nbsp;{{title}}</a>
         {{/if}}
         <p class=fragment text-muted>{{{fragment}}}</p>
         </li>
        {{/each}}
        {{/if}}
      </ul>
     </li>
    {{/each}}
   </ul>
   {{else}}
    <h2>{%endraw%}{{ resx.Search_No_Results_Found }}{%raw%}<em class=querytext>{{{query}}}</em>
     {{#if isResetVisible}}
      <a class="btn btn-default btn-sm facet-clear-all" role="button" title="{%endraw%}{{ snippets['Search/Facet/ClearConstraints'] | default: res['Search_Filter_Clear_All'] }}{%raw%}" tabIndex="0">{%endraw%}{{ snippets['Search/Facet/ClearConstraints'] | default: res['Search_Filter_Clear_All'] }}{%raw%}</a>
     {{/if}}
    </h2>
   {{/if}}
  </script>
{%endraw%}
```

**サイトの設定**

`\_logicalname:annotation~0.9^0.25` の値を [検索/クエリ] サイト設定に追加する必要があります。 追加した後の値は次のようになります。
```
+(@Query) \_title:(@Query) \_logicalname:knowledgearticle~0.9^0.3 \_logicalname:annotation~0.9^0.25 \_logicalname:adx_webpage~0.9^0.2 -\_logicalname:adx_webfile~0.9 adx_partialurl:(@Query) \_logicalname:adx_blogpost~0.9^0.1 -\_logicalname:adx_communityforumthread~0.9
```

ナレッジベースのアーティクルおよび web ファイルに関連付けられた注釈を1つのファセットにグループ化するようにファセットを構成するには、Search/RecordTypeFacetsEntities サイト設定名を編集し、その値に `;Downloads:annotation,adx_webfile` を追加します。

ナレッジ項目に関連付けられている添付ファイルがポータルと検索結果に表示されるようにするには、 **KnowledgeManagement/DisplayNotes**サイト設定を編集し、その値を**True**に設定します。 サイト設定**KnowledgeManagement/備考フィルター**には、メモのノートテキストフィールドにプレフィックスを付ける必要があるプレフィックス値が含まれています。指定されたプレフィックス値を持つメモのみがポータルに表示されます。 既定では、値は \*WEB\*ですが、サイト設定を使用して変更することができます。

メモに関連付けられている添付ファイルのインデックス作成を有効にするには、**検索/インデックス添付**ファイルのサイト設定を作成し、その値を**True**に設定します。
