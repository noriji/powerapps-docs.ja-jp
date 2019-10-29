---
title: PowerApps コンポーネントフレームワークの概要 |Microsoft Docs
description: PowerApps コンポーネントフレームワークを使用してコードコンポーネントを作成し、フォーム、ビュー、およびダッシュボードのデータを表示して操作するための拡張エクスペリエンスを提供します。
keywords: コンポーネントフレームワーク、コードコンポーネント、PowerApps コントロール
author: nkrb
manager: kvivek
ms.date: 09/05/2019
ms.service: powerapps
ms.custom:
- dyn365-a11y
- dyn365-developer
ms.topic: article
ms.assetid: 7923e36d-3640-49f7-9f2f-c97358a632db
ms.author: nabuthuk
ms.openlocfilehash: a9f157dfb3d0a7d29cebadee935c84826ae040d6
ms.sourcegitcommit: 7c1e70e94d75140955518349e6f9130ce3fd094e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/29/2019
ms.locfileid: "73025653"
---
# <a name="powerapps-component-framework-overview"></a>PowerApps コンポーネントフレームワークの概要

PowerApps コンポーネントフレームワークを使用すると、プロの開発者やアプリメーカーは、モデル駆動型アプリとキャンバスアプリ (試験的プレビュー) のコードコンポーネントを作成して、ユーザーがフォーム、ビュー、データを表示して操作するためのユーザーエクスペリエンスを向上させることができます。とダッシュボード。 例:

- 数値テキスト値を表示するフィールドを `dial` または `slider` コードコンポーネントで置き換えます。
- リストを `Calendar` や `Map` のように、データセットにバインドされたまったく異なる視覚効果に変換します。

> [!IMPORTANT]
> - PowerApps コンポーネントフレームワークは、キャンバスアプリの実験的なプレビュー段階であり、モデル駆動型アプリの GA でも使用できます。 これは、モデル駆動型アプリでサポートされているすべての Api がキャンバスアプリでまだサポートされていない可能性があることを意味します。
> - 既定では、PowerApps component framework はモデル駆動型アプリに対して有効になっています。 キャンバスアプリでこの機能を有効にするには、「[キャンバスアプリの可用性](component-framework-for-canvas-apps.md)」を参照してください。
> - [!INCLUDE[cc_preview_features_definition](../../includes/cc-preview-features-definition.md)]
> - キャンバスアプリでは、*データセット*の種類ではなく、コードコンポーネントの*フィールド*の種類のみがサポートされます。


Powerapps コンポーネントフレームワークを使用して、さまざまな PowerApps 機能全体で使用できるコードコンポーネントを作成します。 HTML web リソースとは異なり、コードコンポーネントは同じコンテキストの一部としてレンダリングされ、他のコンポーネントと同時に読み込まれるため、ユーザーにとってシームレスなエクスペリエンスを実現します。 開発者は、すべての HTML、CSS、TypeScript または JavaScript ファイルを1つのソリューションパッケージファイルにバンドルできます。 コードコンポーネントは、さまざまなエンティティやフォームに対して何度も再利用できます。

コードコンポーネントは、コンポーネントライフサイクル管理、コンテキストデータとメタデータアクセス、Web API を使用したシームレスなサーバーアクセス、ユーティリティとデータの書式設定方法、カメラなどのデバイス機能などの機能を公開するフレームワーク Api の豊富なセットにアクセスします。場所とマイクに加えて、ダイアログ、参照、およびフルページレンダリングなどの使いやすい UX 要素もあります。  

開発者やアプリメーカーは、最新の web プラクティスを使用したり、外部ライブラリの機能を活用して高度なユーザー操作を作成したりすることができます。 フレームワークは、コンポーネントのライフサイクルを自動的に処理し、アプリケーションのビジネスロジックを保持し、パフォーマンスを最適化します (非同期の Iframe はこれ以上ありません)。 コンポーネントの定義、依存関係、および構成はすべて、[ソリューション](https://docs.microsoft.com/dynamics365/customer-engagement/customize/solutions-overview)にパッケージ化し、環境間で移動することができ、 [appsource](https://appsource.microsoft.com/en-us/marketplace/apps?page=1&product=dynamics-365)を使用して配布できます。  

## <a name="related-topics"></a>関連トピック

[コードコンポーネントとは](custom-controls-overview.md)<br/>
[キャンバスアプリの可用性](component-framework-for-canvas-apps.md)<br/>
[コードコンポーネントの作成とビルド](create-custom-controls-using-pcf.md)<br/>
[開発者向け PowerApps](https://docs.microsoft.com/powerapps/#pivot=home&panel=developer)

