---
title: 初めてサインインする | Microsoft Docs
description: すべてのアプリ作成者向けの新しいホームです。
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 08/06/2018
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: f4babe6356ab0be34b6b08a3d158462b58cbb0cd
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2019
ms.locfileid: "73541226"
---
# <a name="sign-in-to-powerapps-for-the-first-time"></a>PowerApps に始めてサインインします

[PowerApps](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) にサインインすると、独自のアプリを作成したり、ご自分または他のユーザーが作成したアプリを開いたり、関連するタスクを実行したりするためのさまざまなオプションをそのサイトで利用できるようになります。 これらのタスクは、アクセス権が得られる 1 つまたは複数のライセンスの識別などの最もシンプルなものから、特定のデータ ソースへのカスタム接続の作成などのより高度なものまで多岐にわたります。

次の 3 つの一般的な領域で、オプションを選択できます。

- ページの上部に配置されたヘッダー

    ![ヘッダー](media/intro-maker-portal/header.png)

- ページの左端に配置されたナビゲーション バー

    ![ナビゲーション バー](media/intro-maker-portal/nav-bar.png)

- ページ中央に目立つように配置された複数の大きなアイコン

    ![ホーム ページの中央領域](media/intro-maker-portal/center-area.png)

最良の結果を得るために、ホーム ページを適切な環境に確実に設定することから始めます。

## <a name="choose-an-environment"></a>環境を選択する

アプリ、フロー、データ接続、Common Data Service のエンティティのどちらを作成する場合でも、PowerApps で行う操作の多くは特定の環境に含まれています。 さまざまな種類の作業の間には環境によって境界が作成されます。たとえば、組織ではさまざまな部門ごとに個別の環境が用意されています。 組織の多くでは環境を使用することで、まだ開発中のアプリと、幅広く使用する準備が整っているアプリとを分離しています。 複数の環境にアクセスできる場合もあれば 1 つの環境にしかアクセスできない場合もあります。さらに、適切なアクセス許可があれば、独自の環境を作成できる場合があります。

自分が置かれている環境を確認するには、ヘッダーの右側近くにある環境スイッチャーを見つけてください。

![環境スイッチャー](media/intro-maker-portal/environment-switcher.png)

1 つの環境でアプリを作成する場合は、別の環境からそのアプリを確認することはできません。 さらに、あなたのアプリを別の人が実行する場合、その人にはアプリが作成された環境へのアクセス権が必要となります。

> [!IMPORTANT]
> アプリ、フロー、または同様のコンポーネントを作成する "*前に*"、自分が適切な環境にいることを確認してください。 環境間でのコンポーネントの移動は簡単に行うことができます。

詳細については、[環境の概要](../../administrator/environments-overview.md)を参照してください。

## <a name="choose-an-app-type"></a>アプリの種類を選択する

PowerApps では、次のような種類のアプリを作成し、実行することができます。

- **キャンバス アプリ** では、カスタム UI の設計、およびさまざまなソースからのデータへの接続がサポートされています。
- **モデル駆動型アプリ**には標準の UI があり、Common Data Service でのみデータに接続します。 ただし、ビュー、ダッシュボード、およびさまざまな種類のビジネス ロジックなど、他の要素をより簡単に作成することができます。

Common Data Service データベースを持つ環境を選択した場合は、同じ**ホーム**ページからキャンバスまたはモデル駆動型アプリを作成できます。

## <a name="play-or-edit-an-app"></a>アプリを再生または編集する

自分で作成したアプリがある場合 (または、他のだれかが作成したアプリを共有している場合)、 **[ホーム]** ページまたは **[アプリ]** ページからそれを再生または編集することができます。

**[アプリ]** ページでは、最近開いたかどうかなどの条件に基づいてアプリの一覧をフィルター処理できます。

![アプリの一覧](./media/intro-maker-portal/find-apps.png)

また、右上隅の近くにある検索バーに 1 つまたは複数の文字を入力して、アプリを検索することもできます。 目的のアプリが見つかったら、バナー アイコンを選択してそのアプリを再生または編集します。

## <a name="create-an-app"></a>アプリを作成する

**[ホーム]** ページから、次のいくつかの方法でアプリを作成することができます。

- [データ セットからキャンバス アプリを自動的に生成する](data-platform-create-app.md)
- [キャンバス アプリのビルド済みサンプルをカスタマイズする](open-and-run-a-sample-app.md)
- [空の画面からキャンバス アプリをビルドする](data-platform-create-app-scratch.md)
- [モデル駆動型アプリを作成する](../model-driven-apps/overview-model-driven-samples.md)
- [モデル駆動型アプリのビルド済みサンプルをカスタマイズする](../model-driven-apps/build-first-model-driven-app.md)

## <a name="learn-more"></a>詳細情報

キャンバス アプリまたはモデル駆動型アプリの詳細については、次の 2 つの方法で検索できます。

- 左側のナビゲーション バーで **[詳細情報]** を選びます。
- ヘッダーで、疑問符アイコンを選択します。

    ![省略記号メニューが開いた状態でのモデル駆動型アプリの一覧](media/intro-maker-portal/help-icon.png)

どちらのオプションを選択した場合も、PowerApps コミュニティ (他の組織内のユーザーと情報を共有できる) および PowerApps ブログ (最新の機能の発表される) へのリンクが表示されます。

## <a name="other-common-tasks"></a>その他の一般的なタスク

ヘッダーおよび左側のナビゲーション バーにあるオプションを選択することにより、アプリを作成し開くこと以外のタスクも行うことができます。

### <a name="from-the-header"></a>ヘッダーから

- 下矢印を選択して、アプリを実行できるモバイル クライアントまたはその他のクライアントをダウンロードします。

    詳細については、[アプリの検索と実行](../../user/index.md)に関するページを参照してください。

- 歯車アイコンを選択して、データ ソースへの接続、PowerApps 用のご自分の 1 つまたは複数のライセンスの識別、管理タスクを実行できるページを開くなどのタスクを行います。

    詳細については、次のトピックを参照してください。

  - [キャンバス アプリ コネクタの概要](connections-list.md)
  - [キャンバス アプリ用のカスタム コネクタのビルドと認定](register-custom-api.md)
  - [オンプレミス データ ゲートウェイの管理](gateway-management.md)
  - [PowerApp の管理](../../administrator/index.md)
  - [ライセンスの概要](../../administrator/pricing-billing-skus.md)
  - [モデル駆動型アプリのビルドの概要](../model-driven-apps/model-driven-app-overview.md)

### <a name="from-the-left-navigation-bar"></a>左側のナビゲーション バーから

以下のタスクを行うことで、ご利用のアプリの機能を拡張できます。

- [Common Data Service](../common-data-service/data-platform-intro.md)でエンティティ、オプションセット、データ統合を管理します。
- [Microsoft Flow](https://docs.microsoft.com/flow/getting-started) でのビジネス ロジックの構成。
- [ソリューション](../../developer/common-data-service/introduction-solutions.md)の作成、パッケージ化、および保守。
