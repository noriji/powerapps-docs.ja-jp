---
title: プラグインを使用してビジネスプロセス (Common Data Service) を拡大する | Microsoft Docs
description: プラグインは、 Common Data Service にアップロードできる .NET アセンブリです。 アセンブリ内のクラスはイベント フレームワーク内の特定のイベント (ステップ) に登録できます。 クラス内のコードは、プラットフォームの既定の動作を拡張または変更できるよう、イベントに応答する手段を提供します。
ms.custom: ''
ms.date: 03/27/2019
ms.reviewer: phecke
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="use-plug-ins-to-extend-business-processes"></a>ビジネス プロセスを拡張するためのプラグインの使用

プラグインは、 Common Data Service にアップロードできる .NET アセンブリです。 アセンブリ内のクラスはイベント フレームワーク内の特定のイベント (ステップ) に登録できます。 クラス内のコードは、プラットフォームの既定の動作を拡張または変更できるよう、イベントに応答する手段を提供します。

> [!IMPORTANT]
> 可能な限り、ビジネスロジックを定義するいくつかの宣言型オプションの 1 つを適用することを最初に検討する必要があります。 詳細: [Common Data Service でビジネスロジックを適用](../../maker/common-data-service/cds-processes.md)<br/><br/>
> 宣言型プロセスが要件を満たさない場合、プラグインを使用します。

ステップに登録できるアセンブリのクラスは <xref:Microsoft.Xrm.Sdk.IPlugin> インターフェイスを実装する必要があります。 このインターフェイスは単一のメソッド <xref:Microsoft.Xrm.Sdk.IPlugin.Execute*> を公開しています。 登録されたクラスを持つイベントが発生すると、`Execute` メソッドにコンテキスト データが渡されます。 `Execute` メソッドでは、次の処理が可能です:

- イベントを取り消してユーザーにエラーを表示
- 操作中のデータに変更を加える
- 組織サービスを使用して他のアクションを開始し、自動化を追加

プラグインは同期または非同期で実行するよう構成できます。 同期プラグインは、プラグインのコードが完了するまで、操作を待機させます。 これは、システムの認識されたパフォーマンスに影響します。 非同期プラグインの操作はキューに置かれて操作が完了した後に実行され、最小限の中断で操作を完了できます。

## <a name="when-to-use-plug-ins"></a>プラグインを使用する場合

ワークフローとプラグインは、カスタム ビジネス ロジックを適用する選択肢としてよく比較されます。 ワークフローとプラグインの機能には重複が多くみられます。プラグインはワークフローが実行できることはすべて実行できますが、逆は成り立ちません。 しかし、ワークフローで実行できない場合は必ずプラグインを使わなければならないという意味ではありません。 プラグインを使用せずに要件を満たせる、別の機能があります。 

- ワークフローでは、複数のワークフローで使用できるコードで再使用可能な条件およびアクションを作成できる、カスタム ワークフロー拡張 (ワークフロー活動) を使用できます。 

- 計算フィールドおよびロールアップ フィールドは、以前はワークフローを使用しなければ実行できなかった機能を提供します。

- ユーザー定義アクションは、ワークフローに似た種類のプロセスで、他のワークフローまたは Web サービス エンドポイントから呼び出せる再利用可能なメッセージを作成できます。

- Azure Service Bus 統合および Web hook を使用して、多くのさまざまなリソースを使用してロジックを適用できる外部システムにデータを格納できます。

- Microsoft Flow は、以前はプラグインを使用して実行されていた多くの機能を提供します。

利用できる多くの選択肢があります。 各選択肢を評価し、要件に適合する最適な方法を理解する必要があります。

### <a name="advantages-of-plug-ins"></a>プラグインを使用する利点

プラグインを使用する主な利点は次のとおりです:

- プラグインは高性能です。 適切に作成されたプラグインは、ビジネス ロジックを適用する最も効率の良い方法を提供します。
- プラグインは強力です。 多くの開発者は、自分のスキルや知識を使用してロジックを定義し、組織サービスまたは外部サービスをコード内で直接使用するために機能を使用することを好みます。 経験豊かなプラグイン開発者は、非常に高い生産性を発揮できます。

### <a name="disadvantages-of-plug-ins"></a>プラグインの欠点

- プラグインの作成および管理には、開発者は特別なスキルを要求されます。 開発者に支払う給料は高く、多くの事業において、必要な時に雇うことができません。 ビジネス プロセスは急速に変化する可能性があり、開発者なしで変更できる選択肢があれば、システムはより素早く適合できます。
- プラグインは悪用される可能性があります。 不適切に作成されたプラグインは、環境のパフォーマンスに大きな影響を与える可能性があります。 プラグインの強力な力は、制限を加え、システム全体に与える影響を考慮した上で適用する必要があります。


## <a name="next-steps"></a>次の手順

次のチュートリアルとハウツー トピックは、プラグインの作成方法を説明しています。

### <a name="tutorials"></a>チュートリアル

このトピックは、いくつかの簡単なプラグインを作成するプロセスについて説明しています。

- [チュートリアル: プラグインを書き込み登録する](tutorial-write-plug-in.md)
- [チュートリアル: プラグインをデバッグする](tutorial-debug-plug-in.md)
- [チュートリアル: プラグインを更新する](tutorial-update-plug-in.md)

### <a name="how-to-topics"></a>ハウツー トピック

これらのトピックはプラグインの作成で使用する詳細情報を提供します。

- [プラグインを記述する](write-plug-in.md)
- [例外処理](handle-exceptions.md)
- [プラグインの登録](register-plug-in.md)
- [プラグインのデバッグ](debug-plug-in.md)
 
このトピックでは、プラグインの作成またはデバッグ、またはプラグインのパフォーマンスの分析に関する追加情報を提供します。

- [ユーザーを偽装する](impersonate-a-user.md)
- [トレースおよびログ](logging-tracing.md)
- [パフォーマンスを解析する](analyze-performance.md)
- [外部 Web リソースにアクセスする](access-web-services.md)
