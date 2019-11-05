---
title: キャンバス アプリを Web サイトなどのサービスに統合する | Microsoft Docs
description: Web サイトやその他のサービスにキャンバス アプリを埋め込みます。
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 08/28/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 99594d99aa0ab1ae4971f3ec2eb1987bb7dcfbcc
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2019
ms.locfileid: "73539020"
---
# <a name="integrate-canvas-apps-into-websites-and-other-services"></a>キャンバス アプリを Web サイトなどのサービスに統合する
作成するアプリは、ユーザーが作業を行うときに使用できるときに最も役に立ちます。 Iframe にキャンバスアプリを埋め込むことで、これらのアプリを web サイトやその他のサービス (Power BI や SharePoint など) に統合することができます。

このトピックでは、アプリを埋め込むためのパラメーターを設定する方法を説明した後で、Asset Ordering (資産の注文) アプリを Web サイトに埋め込みます。

![埋め込みアプリが表示された Power BI ダッシュボード](./media/embed-apps-dev/embed-dashboard.png)

次の制限事項を考慮してください。

- 埋め込みアプリにアクセスできるのは、同じテナント内の PowerApps ユーザーだけです。
- Internet Explorer 11 を使用して PowerApps にアクセスするには、互換表示をオフにする必要があります。

Iframe を使用せずに、キャンバスアプリを SharePoint Online に統合することもできます。 詳細につい[ては、「PowerApps web パーツを使用する](https://support.office.com/article/use-the-powerapps-web-part-6285f05e-e441-408a-99d7-aa688195cd1c)」を参照してください。

## <a name="set-uri-parameters-for-your-app"></a>アプリの URI パラメーターの設定
アプリを埋め込む場合は、まず Uniform Resource Identifier (URI) のパラメーターを設定して、iframe がアプリの場所を認識できるようにします。 URI の形式は次のとおりです。

```
https://apps.powerapps.com/play/[AppID]?source=iframe
```

> [!IMPORTANT]
> 2019年8月の時点で、URI 形式は https://make.powerapps.com/webplayer から https://apps.powerapps.com/play に変更されました。 新しい URI 形式を使用するように埋め込み iframe を更新してください。 以前の形式への参照は、互換性を確保するために新しい URI にリダイレクトされます。
>
> 以前の形式:
> 
> https\://make.powerapps.com/webplayer/iframeapp? source = iframe & appId =/providers/Microsoft.PowerApps/apps/[AppID]

この URI の [AppID]\('[' と ']' を含む) を、対象のアプリの ID に置き換えるだけです。 ID を調べる方法は後で説明しますが、その前に、URI で使用できるすべてのパラメーターを以下に示します。

* **[appID]** -実行するアプリの ID を提供します。
* **tenantid** -ゲストアクセスをサポートするオプションのパラメーターで、アプリを開くテナントを決定します。 
* **screenColor** - ユーザーのアプリの読み込みエクスペリエンスを向上するために使用します。 このパラメーターは [RGBA (赤の値、緑の値、青の値、アルファ)](../canvas-apps/functions/function-colors.md) の形式で、アプリが読み込まれるときの画面の色を制御します。 アプリのアイコンと同じ色に設定することをお勧めします。
* **source** - アプリには影響しませんが、埋め込みのソースを示すわかりやすい名前を追加することをお勧めします。
* 最後に、[Param() 関数](../canvas-apps/functions/function-param.md) を使用してカスタムパラメーターを追加すると、その値をアプリで使用できます。 これは `[AppID]&amp;param1=value1` のように、URI の末尾に追加されます。 これらのパラメーターは、アプリの起動中にのみ読み取られます。 これらを変更する必要がある場合は、アプリを再起動する必要があります。 [Appid] の後の最初の項目にのみ "?" が必要であることに注意してください。その後、次に示すように "&" を使用します。 

### <a name="get-the-app-id"></a>アプリ ID を調べる
アプリの ID は powerapps.com で調べることができます。 埋め込むアプリに対して次の手順を実行します。

1. [powerapps.com](https://powerapps.microsoft.com) の **[アプリ]** タブで、省略記号 ( **. . .** ) をクリックまたはタップし、 **[詳細]** を選択します。
   
    ![アプリの詳細の表示](./media/embed-apps-dev/details.png)
1. **アプリ ID** をコピーします。
   
    ![詳細からのアプリ ID のコピー](./media/embed-apps-dev/app-id.png)
1. URI の `[AppID]` 値を置き換えます。 資産の注文アプリの場合、URI は次のようになります。
   
    ```
    https://apps.powerapps.com/play/76897698-91a8-b2de-756e-fe2774f114f2?source=iframe
    ```

## <a name="embed-your-app-in-a-website"></a>Web サイトにアプリを埋め込む
アプリの埋め込みは、サイトの HTML コード (または、Power BI や SharePoint などの iframe をサポートするその他のサービス) に iframe を追加することと同じほど、簡単にできるようになりました。

```html
<iframe width="[W]" height="[H]" src="https://apps.powerapps.com/play/[AppID]?source=website&screenColor=rgba(165,34,55,1)" allow="geolocation; microphone; camera"/>
```

iframe の幅と高さの値を指定し、`[AppID]` を対象のアプリの ID で置き換えます。

> [!NOTE]
> `allow="geolocation; microphone; camera"` を iframe HTML コードに含めて、アプリが Google Chrome でこれらの機能を使用できるようにします。

次の図は、サンプルの Contoso 社 Web サイトに埋め込まれた資産の注文アプリを示しています。

![埋め込みアプリが表示された Contoso 社 Web サイト](./media/embed-apps-dev/contoso-website.png)

アプリのユーザーの認証に関して、次の点に注意してください。

- Web サイトが Azure Active Directory (AAD) ベースの認証を使用する場合は、追加のサインインは必要ありません。
- Web サイトが他のサインイン機構を使用する場合や、認証されない場合は、iframe でユーザーに対してサインイン プロンプトが表示されます。 アプリの作成者がアプリをユーザーと共有していれば、ユーザーはサインイン後にアプリを実行できるようになります。

このように、アプリの埋め込みは簡単で有用です。 埋め込みにより、Web サイトや Power BI ダッシュボード、SharePoint ページなどの、担当者やお客様が業務を行う場所にアプリを配置できます。
