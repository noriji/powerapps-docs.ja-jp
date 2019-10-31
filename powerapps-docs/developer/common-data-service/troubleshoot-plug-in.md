---
title: プラグインのトラブルシューティング (アプリの場合Common Data Service)| Microsoft Docs
description: プラグインが原因で発生する可能性があるエラーと、その修正方法に関する情報が含まれます。
ms.custom: ''
ms.date: 09/18/2019
ms.reviewer: ''
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
# <a name="troubleshoot-plug-ins"></a>プラグインのトラブルシューティング 

このトピックには、プラグインが原因で発生する可能性があるエラーと、その修正方法に関する情報が含まれます。

## <a name="transaction-errors"></a>トランザクション エラー

トランザクションに関連する 2 種類の一般的なエラーがあります。 

エラー コード: `-2146893812`<br />
エラー メッセージ: `ISV code reduced the open transaction count. Custom plug-ins should not catch exceptions from OrganizationService calls and continue processing.`

エラー コード: `-2147220911`<br />
エラー メッセージ: `There is no active transaction. This error is usually caused by custom plug-ins that ignore errors from service calls and continue processing.`

> [!NOTE]
> 上位エラーが最近追加されました。 これは、問題を含むプラグイン内のコンテキスト内ですぐに発生します。 下位エラーは、引き続きさまざまな状況で発生する可能性があります (通常はユーザー定義ワークフロー活動が関係する状況)。 別のプラグインの問題が原因の可能性があります。

このメッセージを理解するには、同期プラグイン内でデータ操作に関連したエラーが発生した場合に、操作全体のトランザクションが終了することを認識する必要があります。

詳細: [Common Data Serviceで拡張可能なカスタマイズ設計](scalable-customization-design/overview.md)

最も一般的な原因は、開発者が成功する*可能性がある*操作を試行できると単に信じることで、失敗したとき、その操作を try / catch ブロックでラップして、エラーを吸収しようとします。

これはクライアント アプリケーションでは有効ですが、プラグイン実行中にはデータ操作の失敗によってトランザクション全体がロール バックされます。 エラーを吸収できないので、必ず <xref:Microsoft.Xrm.Sdk.InvalidPluginExecutionException> を返す必要があります。

## <a name="error-sql-error-execution-timeout-expired"></a>エラー: SQL エラー: 実行タイムアウト期限切れ

エラー コード: `-2147204783`<br />
エラー メッセージ: `Sql error: 'Execution Timeout Expired.  The timeout period elapsed prior to completion of the operation or the server is not responding.'`

SQL タイムアウト エラーの発生には様々な理由があります。

### <a name="blocking"></a>ブロック

ブロックは SQL タイムアウト エラーの最も一般的な原因であり、これは操作が別の SQL トランザクションがロックしたリソースを待っています。 このエラーは、システムがデータの整合性とユーザーのパフォーマンスに影響を与える長時間の要求から保護しているためです。

ブロックは並行した他の操作が原因の可能性があります。 あなたのコードはテスト環境では独立して問題なく動作するにも関わらず、複数のユーザーがプラグインのロジックを起動した場合にのみ発生する状況の影響を受ける場合があります。

プラグインを書くときは、スケーラブルなカスタマイズの設計方法を理解することが重要です。 詳細: [Common Data Serviceで拡張可能なカスタマイズ設計](scalable-customization-design/overview.md)

### <a name="cascade-operations"></a>カスケード操作

レコードの割り当てや削除などプラグインで行う特定の操作が、関連レコードのカスケード操作を開始することがあります。 これらのアクションが関連レコードにロックを適用し、その後のデータ操作をブロックして SQL タイムアウトを発生させる可能性があります。 

プラグインのデータ操作でこれらのカスケード操作の影響を考慮する必要があります。 詳細: [エンティティ関係の動作](../../maker/common-data-service/entity-relationship-behavior.md)

これらの動作は環境によって異なる方法で構成できるため、環境が同じように設定されていない限り動作を再現するのは困難です。

### <a name="indexes-on-new-entities"></a>新しいエンティティのインデックス

プラグインが最近作成されたエンティティや属性を使用して操作を実行している場合、インデックスを管理する Azure SQL の機能のいくつかは数日後に効果が出る場合があります。

## <a name="errors-due-to-user-privileges"></a>ユーザー特権によるエラー

クライアント アプリケーションではユーザーが実行を許可されていないコマンドを無効にできます。 プラグインにはこれがありません。 あなたのコードは、呼び出し元のユーザーが実行する特権を持っていない自動化を含んでいる可能性があります。

ユーザーに **ユーザーのコンテキストで実行** 値を設定することで、正しい特権を確かに持っているユーザーのコンテキストで実行するようプラグインを登録できます。 または他のユーザーに偽装して操作を実行できます。 詳細:
 - [プラグインの登録](register-plug-in.md)
 - [ユーザーを偽装する](impersonate-a-user.md)

<!-- But if you prefer that the logic in your plug-in adapt to the privileges that the calling user has, you really need to verify the user's privileges in your code.

TODO: Add content that shows how to do this -->

## <a name="error-message-size-exceeded-when-sending-context-to-sandbox"></a>エラー: コンテキストをサンドボックスに送信するとき Message のサイズが超過しました

<!-- This is the error code for an unexpected error we should be providing a specific error code. Bug 1470173 is tracking this. -->
エラー コード: `-2147220970`<br />
エラー メッセージ: `Message size exceeded when sending context to Sandbox. Message size: ### Mb`

このエラーは、Message ペイロードが 116.85 MB を大きく超え、**かつ**プラグインがメッセージに登録されている場合に発生します。 エラー Message には、エラーを引き起こしたペイロードのサイズが含まれています。
 
この制限はアプリケーションを実行しているユーザーが、リソースの制約に基づいて互いに干渉できないようにします。 この制限は、Common Data Serviceプラットフォームの可用性およびパフォーマンス特性に対する脅威となる、並外れて大きな Message ペイロードに対する一定レベルの保護を与えるのに役立ちます。
 
116.85 MB は、このサポート案件では極端に大きなサイズといえます。 この案件が発生する可能性が高い状況は、大規模なバイナリ ファイルを含む複数の関連するレコードを持つレコードを回収するときです。
 
このエラーが表示された場合、次のように対応できます。

1.  Message に対するプラグインを削除します。 Message に登録されたプラグインが無い場合は、操作は失敗なく実行できます。
2.  カスタム クライアントでエラーが発生した場合、1 つの操作で作業を行うことがないようにコードを変更できます。 その代わり、より小さいパーツのデータを回復するためのコードを記述します。

## <a name="error-the-given-key-was-not-present-in-the-dictionary"></a>エラー: 付与されたキーは、ディクショナリにありませんでした

Common Data Service 多くの場合、キーおよび値のコレクションを表す抽象 <xref:Microsoft.Xrm.Sdk.DataCollection`2> クラスから派生したクラスが使用されます。 たとえば、プラグインで<xref:Microsoft.Xrm.Sdk.IExecutionContext>。<xref:Microsoft.Xrm.Sdk.IExecutionContext.InputParameters> プロパティは <xref:Microsoft.Xrm.Sdk.DataCollection`2> クラスから派生した <xref:Microsoft.Xrm.Sdk.ParameterCollection> です。  これらのクラスは基本的に、キー名を使用して特定の値にアクセスするディクショナリ オブジェクトです。

### <a name="error-codes"></a>エラー コード 

このエラーは、コードのキー値がコレクションに存在しない場合に発生します。 これは、プラットフォーム エラーではなく、ランタイム エラーです。 このエラーがプラグイン内で発生するとき、エラー コードはエラーがキャッチされたかどうかによって異なります。

[プラグインでの例外処理](handle-exceptions.md)で説明されているように、開発者が例外をキャッチして<xref:Microsoft.Xrm.Sdk.InvalidPluginExecutionException>が返された場合、次のエラーが返されます。

エラー コード: `-2147220891`<br />
エラー メッセージ: `ISV code aborted the operation.`

ただし、このエラーに関しては、開発者がコンポーネントを適切にキャッチせず、次のエラーが返されることは共通です。

エラー コード: `-2147220956`<br />
エラー メッセージ: `An unexpected error occurred from ISV code.`

> [!NOTE]
> 「ISV」は*独立系ソフトウェア ベンダー*を意味します。

### <a name="causes"></a>原因

このエラーは、設計時によく発生し、つづりの間違いまたは正しくないケーシングの使用が原因です。 キー値は、大文字と小文字が区別されます。

実行時のエラーは、開発者が値が存在しないときに存在していると仮定することに起因する場合が多くあります。 たとえば、エンティティの更新用に登録されたプラグインには、変更されるような値のみが<xref:Microsoft.Xrm.Sdk.Entity>に含まれます。<xref:Microsoft.Xrm.Sdk.Entity.Attributes> を使用します。

### <a name="prevention"></a>防止

このエラーを防ぐには、キーの存在を確認後にそれを使用して値にアクセスする必要があります。 

たとえば、エンティティの属性にアクセスする場合は、<xref:Microsoft.Xrm.Sdk.Entity>を次のように使用できます。<xref:Microsoft.Xrm.Sdk.Entity.Contains(System.String)> 次のコードに示されるように、属性がエンティティに存在するかどうかを確認する方法

```csharp
// Obtain the execution context from the service provider.  
IPluginExecutionContext context = (IPluginExecutionContext)
    serviceProvider.GetService(typeof(IPluginExecutionContext));

// The InputParameters collection contains all the data passed in the message request.  
if (context.InputParameters.Contains("Target") &&
    context.InputParameters["Target"] is Entity)
    {
    // Obtain the target entity from the input parameters.  
    Entity entity = (Entity)context.InputParameters["Target"];

    //Check whether the name attribute exists.
    if(entity.Contains("name"))
    {
        string name = entity["name"];
    }
```

一部の開発者は<xref:Microsoft.Xrm.Sdk.Entity>を使用します。<xref:Microsoft.Xrm.Sdk.Entity.GetAttributeValue``1(System.String)> エンティティ属性にアクセスするときにこのエラーを回避するための方法で、この方法は、属性が存在しないときにこの種類の規定値を返すことに注意してください。 既定値が null の場合は、適切に機能します。 しかし、`DateTime` でそうであるように、既定値が null を返さない場合は、返された値は null というよりも `1/1/0001 00:00` になります。