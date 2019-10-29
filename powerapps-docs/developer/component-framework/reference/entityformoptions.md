---
title: EntityFormOptions |Microsoft Docs
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
ms.assetid: 418871c0-59dc-4a7c-a8f9-9364a19f7662
ms.openlocfilehash: 0ed2d2b13fa084fe1521e90304b7e3ead4ccac27
ms.sourcegitcommit: 7c1e70e94d75140955518349e6f9130ce3fd094e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/29/2019
ms.locfileid: "73025465"
---
# <a name="entityformoptions"></a>EntityFormOptions

エンティティフォームに関するすべての情報へのアクセスを提供します。

## <a name="available-for"></a>利用可能な対象 

モデル駆動型アプリ

## <a name="properties"></a>プロパティ

### <a name="createfromentity"></a>createFromEntity

マップされた属性値に基づいて既定値を提供するレコードを指定します。 参照オブジェクトには、エンティティ型、id、および名前の各プロパティがあります。

**型**: [Entityreference](entityreference.md)

### <a name="entityid"></a>entityId

フォームを表示するエンティティレコードの一意の Id。 

**種類**: `string`

### <a name="entityname"></a>entityName

フォームを表示するエンティティの論理名。 

**種類**: `string`

### <a name="formid"></a>formId

表示するフォームインスタンスの ID。

**種類**: `string`

### <a name="height"></a>height

表示するフォームウィンドウの高さ (ピクセル単位)。

**種類**: `number`

### <a name="openinnewwindow"></a>openInNewWindow

フォームを新しいウィンドウに表示するかどうかを指定します。

**種類**: `boolean`

### <a name="usequickcreateform"></a>useQuickCreateForm

簡易作成フォームを開くかどうかを指定します。 この値を指定しない場合、既定で false が渡されます。 

**種類**: `boolean`

### <a name="width"></a>width

表示するフォームウィンドウの幅 (ピクセル単位)。

**種類**: `boolean`

### <a name="windowposition"></a>windowPosition

画面上のウィンドウの位置を指定します。

**種類**: `number`

WindowPosition 値は、次の有効な値を持つ数値です。

|Value|位置|
|---|---|
|1|点|
|2|並列|


## <a name="example"></a>例

```TypeScript
private onRowClick(event: Event): void {
    let rowRecordId = (event.currentTarget as HTMLTableRowElement).getAttribute(
      RowRecordId
    );
    if (rowRecordId) {
      let entityreference = this.contextObj.parameters.simpleTableGrid.records[
        rowRecordId
      ].getNamedreference();
      let entityFormOptions = {
        entityName: entityreference.entityType!,
        entityId: entityreference.id
      };
      this.contextObj.navigation.openForm(entityFormOptions);
    }
  }
```

### <a name="related-topics"></a>関連トピック

[PowerApps コンポーネントフレームワーク API リファレンス](../reference/index.md)<br/>
[PowerApps コンポーネントフレームワークの概要](../overview.md)