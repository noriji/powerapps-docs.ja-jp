---
title: モデル駆動型アプリの統合インターフェイスを使用したユーザーエクスペリエンスの向上 |MicrosoftDocs
ms.custom: ''
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 9/23/2019
ms.author: mduelae
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 76241ae2e26752a98e32e7ad72c54780da3934ae
ms.sourcegitcommit: 7c1e70e94d75140955518349e6f9130ce3fd094e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/29/2019
ms.locfileid: "71705327"
---
# <a name="enhanced-user-experience-with-the-unified-interface-for-model-driven-apps"></a>モデル駆動型アプリ用の統合インターフェイスによるユーザーエクスペリエンスの向上 

モデル駆動型アプリの統合インターフェイスは、デスクトップ、ノート pc、タブレット、電話のいずれでも、デバイス間で一貫性のあるアクセス可能なユーザーエクスペリエンスを提供します。 アプリは、画面上のコンポーネントを reflowing してスケールします。 応答性の高いデザインは、画面のサイズに基づいて環境に合わせて調整されるので、使用可能な領域が多いほど、より多くの情報を表示できます。

> [!div class="mx-imgBorder"]
> ![統合インターフェイスが画面に適合](media/Reflow.png "統合インターフェイスが画面に適合")

> [!NOTE]
> レガシ web クライアントは非推奨となり、2020年10月1日より前に、お客様は統合インターフェイスに移行する必要があります。 詳細については、「[ブログ: 統合インターフェイスに移動するタイムラインの発表](https://cloudblogs.microsoft.com/dynamics365/it/2019/09/10/announcing-the-timeline-to-move-to-unified-interface/)」を参照してください。 移行方法の詳細については、「[移行のクイックスタート](https://docs.microsoft.com/en-us/powerapps/maker/model-driven-apps/transition-web-app)」を参照してください。

## <a name="navigation"></a>領域

メニューオプションを使用すると、システム内のさまざまなアプリを迅速に移動できます。 これらの機能により、最近表示したレコードとお気に入りにピン留めされたお気に入りにすばやくアクセスできます。 

> [!div class="mx-imgBorder"]
> ![モデル駆動型アプリの nav](media/nav.png "モデル駆動型アプリの nav")

1. 既定では、サイトマップが展開され、保持されます。
2. 現在のサブエリアは、アプリ内の場所を示すために強調表示されています。
3. **最近**のアイテムと**ピン留め**されたアイテムは、簡単にアクセスできるように上部にあります。 
4. アプリを切り替えるには、領域スイッチャーを使用します。
5. コマンド バー上のアイコンは、コマンド間の違いを表すために違う色になっています。

詳細については、「[モデル駆動型アプリの基本ナビゲーション](navigation.md)」を参照してください。

## <a name="dashboards-and-charts"></a>ダッシュボードとグラフ
統合インターフェイスアプリ内から、すべてのシステムとユーザーのダッシュボードにアクセスできます。 対話型ダッシュボードは、豊富な対話型ダッシュボード機能を備えたすべてのレコードの種類で使用できるようになりました。 詳細については、「[ダッシュボードとグラフを使用して進行状況を追跡する](track-your-progress-with-dashboard-and-charts.md)」を参照してください。

## <a name="timeline-control"></a>タイムライン コントロール 
タイムラインビューを使用すると、読みやすいビューで1ページのレコードで顧客のコミュニケーションを追跡することで、チームとの共同作業を行うことができます。 投稿や音声の添付ファイルから、電子メールやメモまで、あらゆるものを確認できます。 これにより、通信スレッド全体を簡単に確認できるようになります。 詳細については、「[予定、電子メール、通話、メモ、またはタスクのアクティビティをタイムラインに追加する](add-activities.md)」を参照してください。

## <a name="business-process"></a>ビジネスプロセス 
ビジネスプロセスフローは、ドッキングメカニズムによって改善されています。 ビジネスプロセスのステージを画面にドッキングして、ビジネスプロセスフローにおけるタスクに集中することができます。 これは、プロセスの段階に複雑な手順が含まれている場合に特に便利です。 詳細については、「[ビジネスプロセスの操作](work-with-business-processes.md)」を参照してください。

## <a name="accessibility"></a>アクセシビリティ
アクセシビリティエクスペリエンスが向上したため、スクリーンリーダーを使用して画面上の情報を可聴サウンドに変換し、点字リーダーに出力して、より多くの人がアプリを使用できるようにします。 詳細については、「[スクリーンリーダーを使用](screen-reader.md)する」を参照してください。

## <a name="create-a-unified-interface-app"></a>統合インターフェイスアプリを作成する
統合インターフェイスで独自のエクスペリエンスを作成するための要件がある場合は、アプリデザイナーを使用してモデル駆動型アプリを作成できます。 「[モデル駆動型アプリの構築の概要」を](https://docs.microsoft.com/powerapps/maker/model-driven-apps/model-driven-app-overview)参照してください。

![新しい統合インターフェイスアプリの作成](media/uci-model-driven-app.png "新しい統合インターフェイスアプリの作成")

## <a name="unified-interface-community"></a>統合インターフェイスコミュニティ

統合インターフェイス[コミュニティサイト](https://community.dynamics.com/365/unified-interface/)に移動して、統一されたインターフェイスへのスムーズな移行を計画して実行し、ブログ、ウェビナー、ビデオ、イベントなどのエキスパートや同僚と協力するための支援を受けることができます。
