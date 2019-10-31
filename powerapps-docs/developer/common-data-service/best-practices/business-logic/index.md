---
title: '開発者向け: Common Data Service のプラグインとワークフローの開発に関する最良の導入手法とガイド | Microsoft Docs'
description: PowerApps で Common Data Service の開発者のための、プラグインとワークフロー開発に関するベスト プラクティスとガイド。
services: ''
suite: powerapps
documentationcenter: na
author: jowells
manager: austinj
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 9/23/2019
ms.author: jowells
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="best-practices-and-guidance-regarding-plug-in-and-workflow-development-for-the-common-data-service"></a>Common Data Serviceのプラグインとワークフローの開発に関する最良の導入手法とガイド

以下のリストには、Common Data Service でのプラグインおよびワークフロー開発における、最良の導入手法とガイドが含まれています。

|ベスト プラクティス  |説明  |
|---------|---------|
|[プラグインおよびワークフロー活動でバッチ要求の種類の使用を回避する](avoid-batch-requests-plugin.md)     |プラグインまたはワークフロー活動では ExecuteMultipleRequest または ExecuteTransactionRequest メッセージ要求クラスを使用すべきではありません。         |
|[詳細: IPlugin の実装をステートレスとして開発する](develop-iplugin-implementations-stateless.md)     |IPlugin を実装するクラス メンバーは、データの不整合性やパフォーマンスの問題につながる可能性のある潜在的なスレッドの安全性の問題にさらされます。         |
|[プラグイン ステップ登録を重複させない](do-not-duplicate-plugin-step-registration.md)     |プラグイン ステップ登録を重複させると、同じメッセージまたはイベントに対してプラグインが複数回実行されます。         |
|[プラグインおよびワークフロー アクティビティ内でパラレル実行を使用しないでください](do-not-use-parallel-execution-in-plug-ins.md)|プラグインまたはカスタム ワークフロー アクティビティ内では、マルチスレッドまたは並列スレッドはサポートされていません。|
|[結果を PreOperation RetrieveMultiple を使用してフィルター処理したときに、すべての種類のクエリを実行する](implement-all-types-of-queries-when-filtering-preoperation-retrievemultiple.md)|すべてのアプリケーションの、最適なパフォーマンスと一貫した結果を得るには、RetrieveMultiple の PreOperation に登録されたプラグインを使用できるすべての種類のクエリに対してフィルター処理を実行する必要があります|
|[プラグイン登録にフィルター属性を含める](include-filtering-attributes-plugin-registration.md)     |フィルター属性がプラグイン登録ステップで設定されていないと、そのイベントに更新メッセージが発生するたびにプラグインが実行します。         |
|[retrieve および RetrieveMultiple メッセージ用のプラグインの登録を制限する](limit-registration-plugins-retrieve-retrievemultiple.md)     |同期プラグイン ロジックを Retrieve および RetrieveMultiple メッセージ イベントに追加すると速度低下が発生する可能性があります。         |
|[ユーザー定義のアセンブリ開発を最適化する](optimize-assembly-development.md)     |個々のプラグイン/ユーザー定義ワークフロー活動を単一のカスタム アセンブリに統合してパフォーマンスおよび保守性を改善し、アセンブリ サイズがサンドボックス アセンブリ サイズの上限に近い場合は、プラグイン / ユーザー定義ワークフロー活動をユーザー定義アセンブリに移動することを検討してください。         |
|[カスタム ワークフロー アクティビティーでリフレクションを使用している非対応コードを削除する](remove-unsupported-code-using-reflection-workflow-activities.md)|リフレクションを使用している非対応のコードを含むワークフロー アクティビティーは、今後数か月で使用できなくなりますので、削除する必要があります。|
|[プラグインで外部ホストを操作するときは、キープアライブを false に設定する](set-keepalive-false-interacting-external-hosts-plugin.md)     |キープアライブ プロパティを HTTP 要求ヘッダーで True に設定します。明示的に false に定義されていない場合、プラグインの実行時間が長くなる可能性があります。         |
|[プラグインで外部呼び出しをする場合のタイムアウトを設定する](set-timeout-for-external-calls-from-plug-ins.md)     |外部呼び出しがプラグイン内での応答を期待する時間の長さを制限します。|   
|[プラグインおよびワークフロー活動で InvalidPluginExecutionException を使用する](use-invalidpluginexecutionexception-plugin-workflow-activities.md)     |エラーをプラグインまたはワークフロー活動で上げる場合は InvalidPluginExecutionException を使用します。         |

### <a name="see-also"></a>関連項目

[コードを使用してビジネス ロジックの適用](../../apply-business-logic-with-code.md)<br />
[ビジネス プロセスを拡張するためのプラグインの使用](../../plug-ins.md)<br />
[ワークフローの拡張機能](../../workflow/workflow-extensions.md)<br />