---
title: カスタムページテンプレートを作成するには、ポータルの液体と web テンプレートページテンプレートを使用します。MicrosoftDocs
description: 液体演算子を使用してカスタムページテンプレートを作成する方法について説明します。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 7717bd75fe7149ea3b0af957055975ad10e752ae
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/11/2019
ms.locfileid: "72975060"
---
# <a name="create-a-custom-page-template"></a>カスタム ページ テンプレートを作成する

この例では、液体と、web テンプレートに基づくページテンプレートを使用して、カスタムページテンプレートを作成します。 [web テンプレートを使用してソースコンテンツを格納](store-content-web-templates.md)[!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] ます。 私たちの目標は、 [web リンク](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/portals/manage-web-links)を左側のナビゲーションとして使用する単純な2列のテンプレートを作成することです。ページの内容は右側にあります。 

## <a name="step-1-create-a-web-template-and-write-the-liquid-template-code"></a>手順 1: web テンプレートを作成し、液体テンプレートコードを記述する

まず、Web テンプレートを作成し、液体テンプレートコードを記述します。 このテンプレートの一般的な要素は、今後のテンプレートで再利用される可能性があります。 ここでは、特定のテンプレートを使用して拡張する共通の基本テンプレートを作成します。 この基本テンプレートでは、階層リンクとページタイトル/ヘッダーを提供し、1列のレイアウトを定義します。

> [!div class=mx-imgBorder]
![Web テンプレート1列レイアウト](../media/web-template-two-column-layout.png "web テンプレート1列レイアウト")

> [!TIP]
> ブロックと拡張タグ:[テンプレートタグ](template-tags.md#extends)を使用したテンプレートの継承について説明します。

### <a name="two-column-layout-web-template"></a>2列のレイアウト (Web テンプレート)

```xml
<div class=container>
  <div class=page-heading>
    <ul class=breadcrumb>
      {% for crumb in page.breadcrumbs -%}
        <li>
          <a href={{ crumb.url }}>{{ crumb.title }}</a>
        </li>
      {% endfor -%}
      <li class=active>{{ page.title }}</li>
    </ul>
    <div class=page-header>
      <h1>{{ page.title }}</h1>
    </div>
  </div>
  <div class=row>
    <div class=col-sm-4 col-lg-3>
      {% block sidebar %}{% endblock %}
    </div>
    <div class=col-sm-8 col-lg-9>
      {% block content %}{% endblock %}
    </div>
  </div>
</div>
```

## <a name="step-2-create-a-new-web-template-that-extends-our-base-layout-template"></a>手順 2: 基本レイアウトテンプレートを拡張する新しい web テンプレートを作成する

ナビゲーションリンクの現在のページに関連付けられているナビゲーション web リンクセットを使用して、基本レイアウトテンプレートを拡張する新しい web テンプレートを作成します。

> [!div class=mx-imgBorder]
![Web テンプレート web リンク左側ナビゲーションレイアウト](../media/web-template-weblinks-left-navigation-layout.png "web テンプレート web リンク左ナビゲーションレイアウト")  

> [!TIP]
> [Weblinks](liquid-objects.md#weblinks)オブジェクトを使用して web リンクセットを読み込む方法について理解を深めます。

### <a name="weblinks-left-navigation-web-template"></a>Web リンクの左側のナビゲーション (Web テンプレート)

```xml
{% extends 'Two Column Layout' %}

{% block sidebar %}
  {% assign weblinkset_id = page.adx_navigation.id %}
  {% if weblinkset_id %}
    {% assign nav = weblinks[page.adx_navigation.id] %}
    {% if nav %}
      <div class=list-group>
        {% for link in nav.weblinks %}
          <a class=list-group-item href={{ link.url }}>
            {{ link.name }}
          </a>
        {% endfor %}
      </div>
    {% endif %}
  {% endif %}
{% endblock %}

{% block content %}
  <div class=page-copy>
    {{ page.adx_copy }}
  </div>
{% endblock %}
```

## <a name="step-3-create-a-new-page-template-based-on-the-web-template"></a>手順 3: web テンプレートに基づいて新しいページテンプレートを作成する

この手順では、前の手順で作成した web テンプレートに基づいて新しいページテンプレートを作成します。

> [!div class=mx-imgBorder]
![ページテンプレート web リンク左側のナビゲーションレイアウト](../media/page-template-weblinks-left-navigation-layout.png "ページテンプレート weblinks の左側のナビゲーションレイアウト")  

## <a name="step-4-create-a-web-page-to-display-content"></a>手順 4: コンテンツを表示する web ページを作成する

次に、ページテンプレートを使用する web ページを作成し、関連付けられた Web リンクを設定して、結果を取得します。

> [!div class=mx-imgBorder]
左ナビゲーション(../media/web-page-left-navigation.png "を含む") ![web ページ (]左ナビゲーション)  

### <a name="see-also"></a>関連項目

[RSS フィードを表示するカスタムページテンプレートを作成する](render-rss-custom-page-template.md)  
[現在のページに関連付けられているエンティティの一覧を表示します](render-entity-list-current-page.md)  
[Web サイトヘッダーとプライマリナビゲーションバーを表示する](render-site-header-primary-navigation.md)  
[ハイブリッドナビゲーションを使用して、最大3レベルのページ階層を表示します](hybrid-navigation-render-page-hierachy.md)  

