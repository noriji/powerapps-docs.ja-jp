---
title: クライアント | Microsoft Docs
description: ''
keywords: ''
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4ce41c82-bf4a-4d34-9344-5311c24d76de
ms.openlocfilehash: 17bcd34226be7b2e0b863849defdce532a0b99a8
ms.sourcegitcommit: 7c1e70e94d75140955518349e6f9130ce3fd094e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/29/2019
ms.locfileid: "73025631"
---
# <a name="client"></a>Client

[!INCLUDE [client-description](includes/client-description.md)]

## <a name="syntax"></a>構文

`context.client;`

## <a name="available-for"></a>利用可能な対象 

モデル駆動型アプリとキャンバスアプリ (試験段階プレビュー)

## <a name="properties"></a>プロパティ

### <a name="disablescroll"></a>disableScroll

コンポーネントのスクロール機能を無効にします。

**種類**: `boolean`

## <a name="methods"></a>メソッド

|B | Description |利用可能な対象|
| ------------- |-------------|------|
|[getClient](client/getclient.md)|[!INCLUDE [getclient-description](client/includes/getclient-description.md)]|モデル駆動型アプリとキャンバスアプリ (試験段階プレビュー)|
|[getFormFactor](client/getformfactor.md)|[!INCLUDE [getformfactor-description](client/includes/getformfactor-description.md)]|モデル駆動型アプリとキャンバスアプリ (試験段階プレビュー)|
|[System.web.clientservices.connectivitystatus.isoffline](client/isoffline.md)|[!INCLUDE [isoffline-description](client/includes/isoffline-description.md)]|モデル駆動型アプリ|

## <a name="example"></a>例 

```TypeScript
private createHTMLTableElement(): HTMLTableElement {
    let tableElement: HTMLTableElement = document.createElement("table");
    tableElement.setAttribute("class", "SampleControlHtmlTable_HtmlTable");
    let key: string = "Example Method";
    let value: string = "Result";
    tableElement.appendChild(this.createHTMLTableRowElement(key, value, true));
    key = "getFormFactor()";
    value = String(this._context.client.getFormFactor());
    tableElement.appendChild(this.createHTMLTableRowElement(key, value, false));
    key = "getClient()";
    value = String(this._context.client.getClient());
    tableElement.appendChild(this.createHTMLTableRowElement(key, value, false));
}
```

### <a name="related-topics"></a>関連トピック

[PowerApps コンポーネントフレームワーク API リファレンス](../reference/index.md)<br/>
[PowerApps コンポーネントフレームワークの概要](../overview.md)