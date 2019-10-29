---
title: PowerApps で利用可能なポータルテンプレート |Microsoft Docs
description: PowerApps で使用できるさまざまなポータルテンプレートについて説明します。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 8914bdf9415299651285b452cb1587dad03ce55d
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/11/2019
ms.locfileid: "72977659"
---
# <a name="portal-templates"></a>ポータルのテンプレート

選択した環境に基づいて、PowerApps で Common Data Service starter ポータルまたは Dynamics 365 ポータルを作成できます。

> [!NOTE]
> 既存のポータルと既存のポータルテンプレート (コミュニティ、パートナー、従業員のセルフサービス、カスタマーセルフサービス) は、PowerApps ポータル Studio では完全にはサポートされておらず、一部のコンポーネントはレンダリングされない場合があります。 ただし、残りのコンポーネントの編集は、通常どおり行うことができます。 

## <a name="environment-with-common-data-service"></a>Common Data Service がある環境

Common Data Service が含まれている環境を選択した場合は、Common Data Service スターターポータルを作成できます。 Common Data Service starter portal には、すぐに使い始めるためのサンプルデータが付属しています。 また、次の組み込みのサンプルページも用意されています。

- 既定の studio テンプレート
- タイトル付きページ
- 子リンクがあるページ

## <a name="environment-with-model-driven-apps-in-dynamics-365"></a>Dynamics 365 でモデル駆動型アプリを使用する環境 

Dynamics 365 (Dynamics 365 Sales、Dynamics 365 Customer Service、Dynamics 365 Field Service、Dynamics 365 Marketing、Dynamics 365 Project Service Automation) でモデル駆動型アプリを含む環境を選択した場合は、次のポータルを作成できます。:

- **カスタマーセルフサービスポータル**: 顧客のセルフサービスポータルを使用すると、セルフサービスのナレッジへのアクセス、リソースのサポート、ケースの進行状況の表示、フィードバックの提供を行うことができます。
- **パートナーポータル**: パートナーポータルを使用すると、リセラー、ディストリビューター、サプライヤー、パートナーを持つすべての組織が、共有活動のすべてのステージにリアルタイムでアクセスできるようになります。

    > [!NOTE]
    > 各オプションを有効にするには、Dynamics 365 組織にフィールドサービスパッケージとプロジェクトサービスパッケージがインストールされている必要があります。 詳細については、「 [Project Service Automation の統合](https://docs.microsoft.com/en-us/dynamics365/portals/integrate-project-service-automation)」および「[フィールドサービスの統合](https://docs.microsoft.com/en-us/dynamics365/portals/integrate-field-service)」を参照してください。

- **従業員のセルフサービスポータル**: 従業員のセルフサービスポータルは、一般的なタスクを合理化し、すべての従業員に明確な知識のあるソースを持つことで、効率的で十分な情報を得られた従業員を作成します。
- **コミュニティポータル**: コミュニティポータルでは、お客様と専門家の間でピアツーピアの相互作用を活用して、サポート技術情報の記事、フォーラム、ブログから利用可能なナレッジのカタログを有機拡張し、フィードバックを提供します。コメントと評価
- **空のポータル**: 外部および内部ユーザーとデータを共有するための web サイトを作成します。 このテンプレートには、すぐに作業を開始するためのサンプルページが付属しています。 

## <a name="portal-templates-features"></a>ポータルテンプレートの機能

次の表は、各ポータルテンプレートに関連付けられている機能をまとめたものです。

| 機能 | カスタマーセルフサービスポータル | パートナーポータル | 従業員のセルフサービスポータル | コミュニティポータル | 空のポータル | Common Data Service スターターポータル|
|------------------|---------------|----------------|---------------|------------------|---------------|------|
| 国際対応 | •  | • | • | • | • |• |
| 複数言語のサポート | •  | • | • | • | • |• |
| ポータルの管理| • | • | • | • | •  |• |
| カスタマイズと拡張性  | •   | •  | •   | •  | • |• |
| テーマ   | •   | •   | •    | •   | •   |• |
| コンテンツ管理                     | •                            |                | •                            | •                |               |
| ナレッジ管理                   | •                            | •              | •                            | •                |               |
| サポート/ケース管理                | •                            |                | •                            | •                |               |
| フォーラム                                 | •                            |                | •                            | •                |               |
| ファセット検索                         | •                            |                | •                            |                  |               |
| プロファイルの管理                     | •                            |                | •                            |                  |               |
| フォーラムスレッドの購読              | •                            |                | •                            |                  |               |
| Comments                               | •                            |                | •                            | •                |               |
| [!INCLUDE[pn-azure-shortest](../../includes/pn-azure-shortest.md)] AD 認証                |                              |                | •                            |                  |               |
| よい                                  |                              |                |                              | •                |               |
| Blog                                  |                              |                |                              | •                |               |
| Project Service Automation の統合 |                              | •              |                              |                  |               |
| フィールドサービスの統合              |                              | •              |                              |                  |               |
| パートナーのオンボード                     |                              | •              |                              |                  |               |
| ポータルベース  |  •    | •      |  •| •| •|• |
| ポータルのワークフロー|  •| •|  •| •| •|• |
| Web 通知|  •| •|  •| •| •|• |
| [!INCLUDE[cc-microsoft](../../includes/cc-microsoft.md)] Id|   •|  •|  •|   •| •|• |
| Id ワークフロー| •|  •| •|   •| •|• |
| Web フォーム|  •| •|    •| •| •|• |
| 皆様|   •|  •|  •| •| •|• |
||
