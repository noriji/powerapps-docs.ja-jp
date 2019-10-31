---
title: モデル駆動型アプリの業務ルールおよびフローによるカスタム ビジネス ロジックの適用 | MicrosoftDocs
description: アプリで使用可能なビジネス ロジックのさまざまな種類について説明する
ms.custom: ''
ms.date: 08/02/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
ms.assetid: 0b4e6602-5701-4859-81cc-6f6fe50901b2
caps.latest.revision: 44
author: Mattp123
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="apply-custom-business-logic-with-business-rules-and-flows-in-model-driven-apps"></a>モデル駆動型アプリの業務ルールおよびフローによるカスタム ビジネス ロジックの適用

一貫したビジネス プロセスの定義と実施は、ユーザーがモデル駆動型アプリを使用する大きな理由の1つです。 一貫性のあるプロセスにより、モデル駆動型アプリを使用するものが、一連の手動の手順を忘れずに実行することに集中するのではなく、自分たちの仕事に確実に集中することができます。 

## <a name="business-rules"></a>業務ルール

業務ルールは、変化が急速で、よく使用される業務ルールを実装および保守するための、単純なインターフェイスを提供します。 業務ルールの*スコープ*は、業務ルールが実行される場所を定義します。

|||  
|-|-|  
|**このアイテムを選択する場合…**|**スコープは次に設定されます...**|  
|**エンティティ**|すべてのフォームとサーバー|  
|**すべてのフォーム**|すべてのフォーム|  
|特定のフォーム (例えば、**取引先企業**フォームです)|このフォームのみ| 

モデル駆動型アプリのフォームに対する業務ルールを定義する方法の詳細については、[モデル駆動型アプリ フォームでロジックを適用するための業務ルールの作成](create-business-rules-recommendations-apply-logic-form.md) を参照してください。

> [!NOTE]
> エンティティに対する業務ルールを定義し、*キャンバス アプリ*および*モデル駆動型アプリ*の両方にサーバー レベルで適用されるようにするには、[エンティティに対する業務ルールの定義](/powerapps/maker/common-data-service/data-platform-create-business-rule) を参照してください。

## <a name="flows"></a>フロー  
  
Microsoft Flow にはいくつかの種類のプロセスがあり、それぞれ異なる目的のためにデザインされています。  

-   自動化されたフロー。 イベントによってトリガーされたら 1 つまたは複数のタスクを自動的に実行するフローを作成します。 詳細: [フローの作成](/flow/get-started-logic-flow)。
    
-   ボタン フロー。 モバイル デバイスでボタンをタップするだけで反復的なタスクを実行できます。 詳細: [ボタン フローについて](/flow/introduction-to-button-flows)
  
-   スケジュールされたフロー。 1 日 1 回、特定の日付、または特定期間後のようなスケジュールで 1 つ以上のタスクを実行するフローを作成します。 詳細: [スケジュールに従ったフローの実行](/flow/run-scheduled-tasks)
  
-   業務プロセス フロー。  業務プロセス フローを作成することによって、データを一貫して入力し、アプリで作業するたびに同じステップを実行するように確認します。 詳細: [業務プロセス フローの概要](/flow/business-process-flows-overview)

-   ワークフローおよびアクション Dynamics 365 カスタマイザーは、ワークフローと動作である従来の Common Data Service プロセスを使い慣れていることが考えられます。 詳細: [ワークフロー プロセスの使用](/flow/workflow-processes)と[操作の概要](/flow/actions)
  
## <a name="next-step"></a>次の手順

[モデル駆動型アプリ フォームでロジックを適用するための業務ルールの作成](create-business-rules-recommendations-apply-logic-form.md)

### <a name="see-also"></a>関連項目

[ビジネス ロジックを Common Data Service に適用する](../common-data-service/cds-processes.md)
