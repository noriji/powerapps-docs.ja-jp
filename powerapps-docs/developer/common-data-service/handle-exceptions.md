---
title: プラグインで例外を処理する (Common Data Service) | Microsoft Docs
description: プラグインが呼び出し元に例外を返す場合のシステムの動作について理解します。
ms.custom: ''
ms.date: 09/20/2019
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: pehecke
manager: kvivek
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="handle-exceptions-in-plug-ins"></a>プラグインでの例外の処理

プラグインが例外を D365 システムに返すことを許可する場合、考えられる結果は 2 つあります。例外に関する情報が記録またはユーザーに表示されているか、または処理されている現在のメッセージ要求がキャンセルされているかです。 次に説明する正確な動作は、プラグインの実行方法 (サンドボックス内かどうか、または同期か非同期か) によって異なります。

<a name='cancelling-an-operation'></a>

## <a name="cancelling-the-current-operation"></a>現在の操作のキャンセル

コードは、例外をスローしたり D365 システムに不明な例外を返したりすることで、現在のメッセージ要求の処理操作をキャンセルできます。 プラグインの呼び出し元に返されたいずれかの例外で現在の操作は取り消されるので、スローされる例外を管理するためにコーディング ベスト プラクティスを適用し、例外に現在の操作の取り消しを許可するかどうかを決定することが重要です。

ビジネス ロジックが操作を取り消す必要があることを指示する場合、<xref:Microsoft.Xrm.Sdk.InvalidPluginExecutionException> 例外をスローし、操作が表示取り消された理由を説明するメッセージを提供する必要があります。

理想的なのは、**PreValidation** ステージで登録された同期プラグインを使用してのみ操作をキャンセルすることです。 このステージは*通常*、データベース トランザクションの外部で実行されます。 トランザクションに達する前に操作を取り消すことは、キャンセルされた操作がロールバックされる必要があるため、非常に推奨されています。 操作をロールバックすることには重要なリソースが必要で、システムのパフォーマンスに影響します。 **PreOperation**および **PostOperation**ステージの操作は常に、データベース トランザクション内にあります。

**PreValidation**ステージは、別の操作のロジックで開始される場合、トランザクション内になる場合もあります。 たとえば、取引先企業の作成の**PreOperation**ステージのタスク エンティティ レコードを作成する場合、タスクの作成はイベント実行パイプラインを通って渡され、**PreValidation**ステージ内で発生しますが、取引先企業のエンティティ レコードを作成するトランザクションの一部です。 <xref:Microsoft.Xrm.Sdk.IExecutionContext>.<xref:Microsoft.Xrm.Sdk.IExecutionContext.IsInTransaction> の値で操作がトランザクション内にあるかどうかを判断できます。 プロパティに設定します。

## <a name="how-the-system-handles-plug-in-exceptions"></a>システムがプラグインの例外を処理する方法

同期プラグイン内で <xref:Microsoft.Xrm.Sdk.InvalidPluginExecutionException> 例外をスローすると、メッセージを含むエラー ダイアログがユーザーに表示されます。 メッセージを提供しない場合、一般的なエラー ダイアログがユーザーに表示されます。 例外のいずれか他の種類がスローされる場合、ユーザーには一般的なメッセージを含むエラー ダイアログが表示され、例外のメッセージとスタック トレースが [PluginTraceLog エンティティ](reference/entities/plugintracelog.md) に記述されます。

非同期に登録されたプラグインの例外メッセージは、Web アプリケーションの**システム ジョブ**領域で表示できる、システムジョブ [AsyncOperation エンティティ](reference/entities/asyncoperation.md) レコードに記録されます。 ダイアログはユーザーに表示されません。 非同期プラグインはキューに登録したデータベース トランザクションに関係しないため、トランザクションを取り消すことはできません。

> [!NOTE]
> 統一インターフェイスでは、エラー ダイアログはHTMLでエンコードされたコンテンツやメッセージをサポートしていません。
