---
title: ポータル向けのLiquid とWeb テンプレート ページを使用してユーザー定義ページのテンプレートを作成する | MicrosoftDocs
description: Liquid の演算子を使用してカスタム ページ テンプレートを作成するための手順。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: null
ms.date: 08/30/2019
ms.author: shjais
ms.reviewer: null
---

# <a name="create-a-custom-page-template"></a>ユーザー定義ページ テンプレートを作成する

この例では、流動および Web テンプレートに基づくページ テンプレートを使用することにより、カスタム ページ テンプレートを作成します。 [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [Web テンプレートを使用したソース コンテンツの保存](store-content-web-templates.md)。 目標は、左側のナビゲーションとして [Web リンク セット](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/portals/manage-web-links)を使用し、右側にページの内容のあるシンプルな 2 列のテンプレートを作成することです。 

## <a name="step-1-create-a-web-template-and-write-the-liquid-template-code"></a>ステップ 1: Web テンプレートを作成し、流動テンプレート コードを記述

まず、Web テンプレートを作成し、流動テンプレート コードを記述します。 将来のテンプレートでこのテンプレートのいくつかの共通要素を再利用する可能性があります。 したがって、特定のテンプレートで拡張する共通の基本テンプレートを作成します。 基本テンプレートでは、階層リンクとページ タイトル / ヘッダーを提供し、かつ 1 列レイアウトを定義します:

> [!div class=mx-imgBorder]
![Web テンプレート 1 列レイアウト](../media/web-template-two-column-layout.png "Web テンプレート 1 列レイアウト")

> [!TIP]
> ブロックおよび拡張タグを使用してテンプレートの継承を読み取ります: [テンプレート タグ](template-tags.md#extends)

### <a name="two-column-layout-web-template"></a>2 列レイアウト (Web テンプレート)

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

## <a name="step-2-create-a-new-web-template-that-extends-our-base-layout-template"></a>ステップ 2: 基本のレイアウト テンプレートを拡張する新しい Web テンプレートを作成

ナビゲーション リンクの現在のページに関連付けられているナビゲーション Web リンクのセットを使用して、基本レイアウト テンプレートを拡張する新しい Web テンプレートを作成します。

> [!div class=mx-imgBorder]
![Web テンプレート Web リンク左側のナビゲーション レイアウト](../media/web-template-weblinks-left-navigation-layout.png "Web テンプレート Web リンク左側のナビゲーション レイアウト")  

> [!TIP]
> [Web リンク](liquid-objects.md#weblinks) オブジェクトを用いて Web リンク セットを読み込む方法について理解してください。

### <a name="weblinks-left-navigation-web-template"></a>Web リンクの左ナビゲーション (Web テンプレート)

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

## <a name="step-3-create-a-new-page-template-based-on-the-web-template"></a>ステップ 3: この Web テンプレートに基づき新しいページ テンプレートを作成

このステップでは、前の手順で作成した Web テンプレートに基づく新しいページ テンプレートを作成します。

> [!div class=mx-imgBorder]
![ページ テンプレート Web リンク左側のナビゲーション レイアウト](../media/page-template-weblinks-left-navigation-layout.png "ページ テンプレート Web リンク左側のナビゲーション レイアウト")  

## <a name="step-4-create-a-web-page-to-display-content"></a>ステップ 4: コンテンツを表示する Web ページを作成

今、残っている作業は、ページ テンプレートを使用した、関連する Web リンク セットのある Web ページを作成し、結果を得ることです。

> [!div class=mx-imgBorder]
![左側のナビゲーションのある Web ページ](../media/web-page-left-navigation.png "左側のナビゲーションのある Web ページ")  

### <a name="see-also"></a>関連項目

[RSS フィードを表示するカスタム ページ テンプレートの作成](render-rss-custom-page-template.md)  
[現在のページに関連付けられているエンティティの表示](render-entity-list-current-page.md)  
[Web サイト ヘッダーとプライマリ ナビゲーション バーの表示](render-site-header-primary-navigation.md)  
[ハイブリッド ナビゲーションの使用により、ページ階層のレベルを 3 つまで描画](hybrid-navigation-render-page-hierachy.md)  

