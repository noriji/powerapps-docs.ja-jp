---
title: ポータルにテンプレートタグを使用する |MicrosoftDocs
description: ポータルで使用できるテンプレートタグについて説明します。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 4475e9e2ccc474a6eeb3e7a2e959b360b3250aa8
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2019
ms.locfileid: "73543286"
---
# <a name="template-tags"></a>テンプレート タグ

テンプレートタグは、さまざまな方法でテンプレートの出力を制御し、複数のテンプレートを組み合わせて1つの出力にすることを許可します。

## <a name="include"></a>用意

名前によって、あるテンプレートの内容を別のテンプレートに含めます。 PowerApps ポータルでは、この他のテンプレートのソースは通常、 [web テンプレート](store-content-web-templates.md)になります。 これにより、複数の場所で共通のテンプレートフラグメントを再利用できます。  

テンプレートを別のテンプレートに含めると、含まれているテンプレートは親テンプレートで定義されている任意の変数にアクセスできるようになります。

`{% include 'My Template' %}`

任意の数の名前付きパラメーターを include タグに渡すこともできます。 これらは、含まれているテンプレートの変数として定義されます。

`{% include 'My Template' a:x, b:y %}`

## <a name="block"></a>帯

テンプレートの継承を実現するために、拡張と組み合わせて使用されます。 「使用するための拡張」を参照してください。

## <a name="extends"></a>拡張

ブロックタグと組み合わせて使用され、テンプレートの継承を提供します。 これにより、複数のテンプレートで共有レイアウトを使用しながら、親レイアウトの特定の領域を上書きすることができます。

PowerApps ポータルでは、タグに指定された親テンプレート名は、通常、 [web テンプレート](store-content-web-templates.md)の名前を参照します。  

拡張を使用する場合は、テンプレートの最初のコンテンツにする必要があり、その後に1つ以上のブロックタグを指定できます。

親テンプレートで定義されているブロックがオーバーライドされていない場合は、親テンプレート (存在する場合) の内容がレンダリングされます。

## <a name="comment"></a>comment

レンダリングされていないコードを液体テンプレート内に残すことができます。 ブロック内のすべてのコンテンツはレンダリングされず、内の液体コードは実行されません。

**コード**

`Hello{% comment %}, {{ user.fullname }}{% endcomment %}. My name is Charles.`

**Output**

`Hello. My name is Charles.`

## <a name="raw"></a>素材

ページで液体コードを解析して実行しなくても出力できるようにします。

**Output**

`Hello, {{ user.fullname }}. My name is Charles.`

### <a name="see-also"></a>関連項目

[制御フロータグ](control-flow-tags.md)<br>
[イテレーションタグ](iteration-tags.md)<br>
[可変タグ](variable-tags.md)<br>
[PowerApps common data service エンティティタグ](portals-entity-tags.md)
