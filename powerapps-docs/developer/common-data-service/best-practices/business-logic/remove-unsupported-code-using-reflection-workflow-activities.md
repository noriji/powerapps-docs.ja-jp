---
title: カスタム ワークフロー アクティビティーでリフレクションを使用している非対応コードを削除する | MicrosoftDocs
description: このトピックで説明されているコード スニペットがカスタム ワークフロー アクティビティに存在する場合は削除する必要があります。
services: ''
suite: powerapps
documentationcenter: na
author: JimDaly
manager: ryjones
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 18/15/2019
ms.author: jdaly
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="remove-unsupported-code-that-uses-reflection-in-custom-workflow-activities"></a>カスタム ワークフロー アクティビティーでリフレクションを使用している非対応コードを削除する

**カテゴリ**: 信頼性

**影響の可能性**: 高い

<a name='symptoms'></a>

## <a name="symptoms"></a>現象

リフレクションを使用している非対応のコードを含むワークフロー アクティビティーは、今後数か月で使用できなくなりますので、削除する必要があります。

ワークフローの拡張が失敗し、エラー メッセージ `Could not load file or assembly 'Microsoft.Crm.Workflow, Version=` が表示されます。 バージョン番号は異なる場合がありますが、多くの場合は `6.0.0.0` です。


<a name='guidance'></a>

## <a name="guidance"></a>ガイダンス

カスタム ワークフロー アクティビティに、以下のようなコードがないかどうかを検索して削除する必要があります:

```
var type = Type.GetType("Microsoft.Crm.Workflow.SynchronousRuntime.WorkflowContext, Microsoft.Crm.Workflow, Version=6.0.0.0");
type.GetProperty("ProxyTypesAssembly").SetValue(serviceFactory, typeof(YourServiceContext).Assembly, null); 
```

カスタム ワークフロー アクティビティー内でこれらのリフレクションを使用しているコードを見つけた場合は、削除して、それを含むアセンブリを再コンパイルした上で更新する必要があります。

<a name='problem'></a>

## <a name="problematic-patterns"></a>問題となるパターン

現在では、このコードは何の働きもしません。 このコードは約7年前に、事前バインド型を使用する際に発生した問題の回避策として追加されていたようです。 

このコードを含むスニペットは、この問題に関係のない多くのQ&Aフォーラムに投稿されています。 Stack Overflow には問題の解決策としてこのスニペットが投稿されています [CRM2011の IWorkflowContext がアクセスするサービスで EnableProxyTypes を実行する方法](https://stackoverflow.com/questions/9230117/how-to-enableproxytypes-on-a-service-accessed-from-the-iworkflowcontext-in-crm-2/45948206)

事前バインド型のサポートに関する根本的な問題は修正されていますが、このコードはカスタム ワークフロー アクティビティーのコードベースにまだ残っています。 本来このコードはサポートされていないものですが、今まで悪影響を与えることもありませんでした。 しかし今後数ヶ月のうちに、このコードを含むカスタムワークフローに悪影響を与えることが想定されています。


<a name='additional'></a>

## <a name="additional-information"></a>追加情報

現在リフレクションは使用することができません。 このコードは、内部コードを反映させる目的で、ホワイトリストに含まれている内部アセンブリを参照しています。 これが、現在エラーを表示しない理由です。 ただし、将来的に一般的な制限が解除されると、ワークフロー アクティビティに悪影響を与えます。

運用中のビジネスロジックを壊すことなく、カスタム ワークフロー アクティビティ内でより優れた機能を提供するには、全ユーザーがコードベースを確認し、このような参照を削除する必要があります。

<a name='seealso'></a>

### <a name="see-also"></a>関連項目

[ワークフローの拡張機能](../../workflow/workflow-extensions.md)
