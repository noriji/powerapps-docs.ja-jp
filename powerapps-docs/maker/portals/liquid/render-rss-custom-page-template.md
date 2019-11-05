---
title: ポータルのカスタムページテンプレートを使用して RSS フィードを表示する |MicrosoftDocs
description: カスタムページテンプレートを作成し、それを使用して RSS フィードを表示する方法について説明します。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 240af2f54e153490794358dc1598b72a16fe1c38
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2019
ms.locfileid: "73543319"
---
# <a name="create-a-custom-page-template-to-render-an-rss-feed"></a>RSS フィードを表示するカスタムページテンプレートを作成する
この例では、液体と Web テンプレートページテンプレートを使用して、ニュース記事の[RSS フィード](https://en.wikipedia.org/wiki/RSS)を表示するカスタムページテンプレートを作成します。 [web テンプレートを使用してソースコンテンツを格納 [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] に](store-content-web-templates.md)は  

## <a name="step-1-create-a-new-powerapps-view"></a>手順 1: 新しい PowerApps ビューを作成する

まず、フィードのデータを読み込むために使用する新しい PowerApps ビューを作成します。 この例では、Web ページのビューを作成し、このエンティティを使用して記事を格納します。 このビューを使用して、結果の並べ替えとフィルター処理を構成し、水冷テンプレートで使用するエンティティ属性を列として含めることができます。

![ページテンプレートを編集する](../media/edit-page-template.png "ページテンプレートを編集する")  

## <a name="step-2-create-a-web-template-for-rss-feed"></a>手順 2: RSS フィード用の web テンプレートを作成する

この手順では、RSS フィード用の web テンプレートを作成します。 このテンプレートは、web サイトの特定の web ページに適用されます。そのため、このページのタイトルと概要をフィードのタイトルと説明として使用します。 ここでは、entityview タグを使用して、新しく作成したニュース記事ビューを読み込みます。 [PowerApps common data service エンティティタグ](portals-entity-tags.md)を [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] します。 また、Web テンプレートの **[MIME の種類]** フィールドを application/rss + xml に設定します。 これは、テンプレートがレンダリングされるときに応答のコンテンツの種類がどのようになるかを示します。  

![RSS フィード用の web テンプレートを構成する](../media/web-template-rss-feed.png "RSS フィード用の web テンプレートを構成する")  

### <a name="rss-feed-web-template"></a>RSS フィード (Web テンプレート)

```xml
<?xml version=1.0 encoding=UTF-8 ?>
<rss version=2.0>
  <channel>
    <title>{{ page.title | xml_escape }}</title>
    <description>{{ page.description | strip_html | xml_escape }}</description>
    <link>{{ request.url | xml_escape }}</link>
    {% entityview logical_name:'adx_webpage', name:'News Articles', page_size:20 -%}
      {% for item in entityview.records %}
        <item>
          <title>{{ item.adx_name | xml_escape }}</title>
          <description>{{ item.adx_copy | escape }}</description>
          <link>{{ request.url | base | xml_escape }}{{ item.url | xml_escape }}</link>
          <guid>{{ item.id | xml_escape }}</guid>
          <pubDate>{{ item.createdon | date_to_rfc822 }}</pubDate>
        </item>
      {% endfor -%}
    {% endentityview %}
  </channel>
</rss>
```

## <a name="step-3-create-a-page-template-to-assign-rss-feed-template"></a>手順 3: RSS フィードテンプレートを割り当てるページテンプレートを作成する

次に、新しいページテンプレートを作成します。これにより、web サイトの任意の web ページに RSS フィードテンプレートを割り当てることができます。 フィードのページ全体の応答を表示するために、[ **Web サイトのヘッダーとフッターを使用**する] の選択を解除することに注意してください。

![RSS フィードのページテンプレートを構成する](../media/page-template-rss-feed.png "RSS フィードのページテンプレートを構成する")  

## <a name="step-4-create-a-web-page-to-host-rss-feed"></a>手順 4: RSS フィードをホストする web ページを作成する

次に、フィードをホストする RSS フィードテンプレートを使用して新しい web ページを作成します。 この新しい web ページを要求すると、RSS フィード XML が送信されます。

![RSS フィードの例](../media/rss-feed-example.png "RSS フィードの例")  

この例では、液体、Web テンプレート、PowerApps ビュー、ポータルコンテンツ管理機能を組み合わせて、カスタム RSS フィードを作成する方法を説明しました。 これらの機能を組み合わせることにより、あらゆるポータルアプリケーションに強力なカスタマイズ機能を追加できます。

### <a name="see-also"></a>関連項目

[液体と web テンプレートページテンプレートを使用してカスタムページテンプレートを作成する](create-custom-template.md)  
[現在のページに関連付けられているエンティティの一覧を表示します](render-entity-list-current-page.md)  
[Web サイトヘッダーとプライマリナビゲーションバーを表示する](render-site-header-primary-navigation.md)  
[ハイブリッドナビゲーションを使用して、最大3レベルのページ階層を表示します](hybrid-navigation-render-page-hierachy.md)  

