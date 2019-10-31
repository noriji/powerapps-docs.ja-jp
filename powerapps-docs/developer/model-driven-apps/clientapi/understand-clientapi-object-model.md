---
title: モデル駆動型アプリにおけるクライアント API のオブジェクト モデルを理解する | Microsoft Docs
ms.date: 10/31/2018
ms.service: powerapps
ms.topic: conceptual
applies_to:
  - Dynamics 365 (online)
ms.assetid: 3335aec5-6b48-4ef6-8d49-2833b177f318
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="understand-the-client-api-object-model"></a>クライアント API オブジェクト モデルについて



モデル駆動型アプリにおけるクライアント API のオブジェクト モデルは、JavaScript を使用したモデル駆動型アプリでカスタム ビジネス ロジックを適用するため、下記に示すオブジェクトとメソッドを提供します。
- 属性値を取得または設定します。
- ユーザー インターフェイス要素の表示および非表示。
- 属性ごとに複数のコントロールを参照します。
- エンティティごとに複数のフォームをアクセスします。
- フォーム ナビゲーション アイテムの操作。
- 業務プロセス フローのコントロールとやり取りします。

Customer Engagement で JavaScript コードを効果的に記述して使用するためには、モデル駆動型アプリにおけるクライアント API のオブジェクト モデルを理解することが重要です。

## <a name="root-objects-in-the-client-api-object-model"></a>クライアント API オブジェクト モデルのルート オブジェクト

クライアント API オブジェクト モデルのルートには、次のコンテキストと Xrm オブジェクトがあります:

|オブジェクト|内容|
|--|--|
|**executionContext**|モデル駆動型アプリにおけるフォームおよびグリッド内の、イベントの実行コンテキストを表します。<br/>詳細については、「[クライアント API 実行コンテキスト](clientapi-execution-context.md)」を参照してください。|
|**formContext** |現在のコードが実行されるフォームまたはフォーム上のアイテムへの参照を提供します。 **formContext** オブジェクトを使用するには、**executionContext**.[getFormContext](reference/executioncontext/getFormContext.md) メソッドを使用します。<br/>詳細については、「[クライアント API フォーム実行コンテキスト](clientapi-form-context.md)」を参照してください。|
|**gridContext** |現在のコードが実行されるフォーム上のグリッドまたはサブグリッドへの参照を提供します。<br/>詳細については、「[クライアント API グリッド コンテキスト](clientapi-grid-context.md)」を参照してください。|
|**Xrm**| フォーム、グリッド、サブグリッド、コントロール、または属性のデータや UI に直接影響しない操作を実行するためのグローバル オブジェクトを提供します。 たとえば、Web API を使用してフォームをナビゲートし、レコードを作成および管理します。<br/>詳細: 「[クライアント API Xrmオブジェクト](clientapi-xrm.md)」|

### <a name="related-topics"></a>関連トピック

[クライアントAPIグローバルコンテキスト](clientapi-xrm.md#client-api-global-context)<br/>
[クライアント API 参照](reference.md)








