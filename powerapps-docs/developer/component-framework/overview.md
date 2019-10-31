---
title: PowerApps component framework の概要 | MicrosoftDocs
description: PowerApps component framework を使用してコード コンポーネントを作成し、ユーザー エクスペリエンスを強化したフォーム、ビュー、ダッシュボードでデータを表示しながら作業できます。
keywords: component framework、コード コンポーネント、PowerApps 制御
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
---

# <a name="powerapps-component-framework-overview"></a>PowerApps component frameworkの概要

PowerApps component frameworkを使用してモデル駆動型アプリ向けにコード コンポーネントおよびキャンバス アプリ (実験段階のプレビュー) を作成し、フォーム、ビュー、ダッシュボードでデータを表示しながら作業でき、強化されたユーザー エクスペリエンスを体験していただけます。 たとえば、次のようなものです。

- 数値テキスト値を表示するフィールドを `dial` や `slider` コンポーネントに置き換えます。
- リストを `Calendar` や `Map` のようにデータセットに結び付けられた全く異なる視覚的エクスペリエンスに変換します。

 
> [!IMPORTANT]
> - PowerApps component framework は、キャンバス アプリ向けの実験用プレビュー内と、モデル駆動型アプリ向けの GA 内にあります。 これは、モデル駆動型アプリでサポートされているすべての API が、キャンバス アプリではサポートされていない場合があることを意味します。
> - 既定で PowerApps Component Framework はモデル駆動型アプリに対して有効です。 キャンバス アプリでこの機能を有効にするには、 [キャンバス アプリの可用性](component-framework-for-canvas-apps.md)を参照してください。
> - [!INCLUDE[cc_preview_features_definition](../../includes/cc-preview-features-definition.md)]
> - キャンバス アプリでは、コード コンポーネントの *フィールド*の種類のみがサポートされ、*データセット* の種類はサポートされていません。


PowerApps component framework を使用すると、専門的な開発者とアプリ メーカーは、完全で幅広い PowerApps の機能全体で使えるコード コンポーネントを作成できます。 HTML Web リソースとは異なり、コード コンポーネントは同じコンテキストの一部として表示されると同時に、他のコンポーネントとして読み込むことができ、シームレスなエクスペリエンスを提供しています。 開発者は、すべての HTML、CSS、TypeScript または JavaScript ファイルを、単一のソリューション パッケージファイルでバンドルできます。 コード コンポーネントは、異なるエンティティとフォームにわたって何回でも再利用できます。

カスタム コンポーネントを使用することによって、コード コンポーネント ライフサイクル 管理、コンテキスト データおよびメタデータ アクセス、Web API を介したシームレスなサーバー アクセス、ユーティリティとデータの書式設定方法、カメラ、位置、マイクなどのデバイス機能と、ダイアログなどの UX 要素の簡単な呼び出し、検索、全画面表示などのような機能を公開する、豊富なフレームワーク API にアクセスできます。  


開発者とアプリ メーカーは最新の Web プラクティスを利用でき、また、外部ライブラリの力を活用して高度なユーザー対話を作成できます。 フレームワークはコンポーネントのライフサイクルを自動的に処理し、アプリケーションのビジネス ロジックを保持し、パフォーマンスを最適化します (もう非同期 IFrames は不要です)。 組織定義、依存関係、構成はすべて [ソリューション](https://docs.microsoft.com/dynamics365/customer-engagement/customize/solutions-overview) にパッケージできます。また、 [アプリ ソース](https://appsource.microsoft.com/en-us/marketplace/apps?page=1&product=dynamics-365) に組み込んで出荷できます。  

## <a name="related-topics"></a>関連トピック

[コード コンポーネントとは](custom-controls-overview.md)<br/>
[キャンバス アプリの可用性](component-framework-for-canvas-apps.md)<br/>
[コード コンポーネントの作成と展開](create-custom-controls-using-pcf.md)<br/>
[開発者向け PowerApps](https://docs.microsoft.com/powerapps/#pivot=home&panel=developer)

