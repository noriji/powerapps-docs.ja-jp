---
title: ログおよびトレース (Common Data Service) | Microsoft Docs
description: プラグインのデバッグを支援するために、トレース ログを使用してプラグイン実行情報を保存します。
ms.custom: ''
ms.date: 09/19/2019
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
# <a name="tracing-and-logging"></a>トレースおよびログ

トレースを使用して、プラグインまたはユーザー定義ワークフロー活動 (カスタム コード) のトラブルシューティングを行います。 トレースは、コードの失敗の原因を診断する補助として、ランタイム情報を記録することによって、開発者を支援します。 トレースは同期実行または非同期実行に対応しています。
  
Common Data Service の実行時のトレース情報の記録は、<xref:Microsoft.Xrm.Sdk.ITracingService> という名前のサービスによって提供されます。 ユーザー定義コードによってこのサービスに提供された情報は、次に示す 3 つの異なる場所に記録できます。  

- **トレース ログ**  
  
    トレース ログ レコードは [PluginTraceLog エンティティ](reference/entities/plugintracelog.md)に記録されます。 これらのレコードの作成は、 [トレース ログの有効化](#enable-trace-logging)で説明されるトレースの設定によって制御されます。

    このデータは、 **設定** に移動して **プラグイン トレース ログ** タイルを選択することによって、モデル駆動型アプリ内に見つけることができます。 このタイルは、割り当てられたセキュリティ ロールでトレース ログのエンティティ レコードにアクセスできる場合にのみ表示されます。

    [トレースの使用](debug-plug-in.md#use-tracing) で示された例あるいは [プラグイン追跡ビューア](#plug-in-trace-viewer) コミュニティ ツールを活用すると、 ブラウザーでWeb APIを利用してデータを表示することが簡単になります。

    > [!IMPORTANT]
    > トレース ログは、特に多数のトレースと例外が生成されたときは、組織の保存領域を占有します。 トレースログは、デバッグとトラブルシューティングの場合にのみオンにして、調査の完了後はオフにする必要があります。  
  
- **エラー ダイアログ**  
  
     プラットフォームから例外を返す同期登録プラグインまたはユーザー定義ワークフロー活動は、ログオンしているユーザーに提示される Web アプリケーション内に、エラー ダイアログ ボックスが表示されます。 ユーザーは、ダイアログにある**ログ ファイルのダウンロード**ボタンを選択して、例外とトレース出力を格納しているログを表示することができます。  
  
- **システム ジョブ**  
  
     例外を返す、非同期の登録済みのプラグインまたはユーザー定義の活動の場合、トレース情報は、Web アプリケーションの**システム ジョブ**フォームの**詳細**領域に表示されます。  
  
<a name="bkmk_trace-settings"></a>

## <a name="enable-trace-logging"></a>トレース ログの有効化

トレース ログを作成するかどうかは、 [組織](/powerapps/developer/common-data-service/reference/entities/organization) エンティティ [PluginTraceLogSetting](/powerapps/developer/common-data-service/reference/entities/organization#BKMK_PluginTraceLogSetting) 属性値の値によって異なります。

トレース ログを有効にするには、プログラムでこの値を更新するか、Web アプリケーションで、 **設定** > **管理** > **システム設定** に移動します。 **カスタマイズ**タブで、**プラグイン トレース ログへのログ記録を有効化**という名前のドロップダウン メニューを見つけて、使用可能なオプションから 1 つを選択します。  
  
|Value|オプション|説明|  
|------------|-----------------|-----------------|  
|0|オフ|トレース ログへの書き込みは無効です。 **PluginTraceLog** レコードが作成されません。 ただし、ログが書き込まれていない場合でも、ユーザー定義コードはそれでも <xref:Microsoft.Xrm.Sdk.ITracingService.Trace(System.String,System.Object[])> メソッドを呼び出すことができます。|  
|1|例外|ユーザー定義コードから例外がプラットフォームに渡されると、トレース情報がログに書き込まれます。|  
|2|すべて|コードの完了時に、またはユーザー定義コードから例外がプラットフォームに渡されたときに、トレース情報がログに書き込まれます。|  
  
トレース ログの設定が**例外**に設定されている場合、ユーザー定義コードが例外をプラットフォームに返したとき、トレース ログのレコードが作成され、トレース情報はもう一つの場所にも書き込まれます。 同期して実行されるユーザー定義コードの場合は、情報はエラー ダイアログ ボックスでユーザーに表示されます。それ以外の、非同期のコードの場合は、情報は関連するシステム ジョブに書き込まれます。  

## <a name="write-to-the-tracing-service"></a>トレース サービスへの書き込み

トレース サービスに書き込む前に、最初に、渡された実行コンテキストからトレース サービス オブジェクトを取得する必要があります。 その後、ユーザー定義コードに、<xref:Microsoft.Xrm.Sdk.ITracingService.Trace(System.String,System.Object[])> 呼び出しを追加するだけす。このメソッドの呼び出しで関連する診断情報が渡されます。  

  
 ```csharp
//Extract the tracing service for use in debugging plug-ins.
 ITracingService tracingService =
     (ITracingService)serviceProvider.GetService(typeof(ITracingService));

 // Use the tracing service 
 tracingService.Trace("Write your message here.");
 
```

次に、プラグインまたはユーザー定義ワークフロー活動を作成して展開します。 組織によってサポートされ、有効になっていて、前のセクションで説明したとおりに、Web ダイアログまたはシステム ジョブでユーザーにも利用できるようになっている場合、ユーザー定義コードの実行中に、**Trace** メソッドを呼び出しで提供された情報は、<xref:Microsoft.Xrm.Sdk.ITracingService> によってトレース ログのエンティティ レコードに書き込まれます。 トレース ログに書き込まれるトレース情報は、トレース設定で構成されます。 詳細については、[トレース ログを有効にする](#bkmk_trace-settings) を参照してください。  
  
> [!NOTE]
> ユーザー定義コードがデータベース トランザクション内で実行され、トランザクションのロールバックを引き起こす例外が発生した場合、コードによるすべてのエンティティ データの変更は取り消されます。 ただし、[PluginTraceLog](reference/entities/plugintracelog.md) レコードは、ロールバックが完了しても残ります。  
  
## <a name="additional-information-about-the-tracing-service"></a>トレース サービスに関する追加情報

<xref:Microsoft.Xrm.Sdk.ITracingService> は提供された情報を **Trace** メソッドを使用して 1 つにまとめます。 ユーザー定義コードの実行が正常に完了した後、または例外がスローされた後、情報は新しい [PluginTraceLog](reference/entities/plugintracelog.md) レコードに書き込まれます。  

各トレース呼び出しは、 [PluginTraceLog](reference/entities/plugintracelog.md) 属性と [MessageBlock](reference/entities/plugintracelog.md#BKMK_MessageBlock) 属性に新たな行として記録されます。 10kbのテキストしか書きこみができません。 この制限を満たすために古いトレース行は削除され、最新の行のみが保存されます。
  
[PluginTraceLog](reference/entities/plugintracelog.md) レコードには有効期限があります。 一括削除ジョブがバックグラウンドで 1 日に 1 回実行されて、作成から 24 時間経過したレコードを削除します。 

> [!CAUTION]
> このジョブを無効にしたり、発生頻度を調整できますが、あとで元の設定に戻すことができないとパフォーマンスの問題の原因となることがよくあります。

## <a name="community-tools"></a>コミュニティ ツール

 ### <a name="plug-in-trace-viewer"></a>プラグイン追跡ビューア

**プラグイン追跡ビューア** は、XrmToolbox コミュニティが開発したツールです。 コミュニティ開発ツールの詳細については、[Common Data Service のコミュニティ](community-tools.md) を参照してください。

> [!NOTE]
> コミュニティ ツールは Microsoft の製品ではなく、コミュニティ ツールに対するサポートは提供されません。 このツールに関するご質問は、その発行元にお問い合わせください。 詳細: [XrmToolBox](https://www.xrmtoolbox.com)。  

### <a name="see-also"></a>関連項目

[プラグイン](plug-ins.md)  
[プラグインのデバッグ](debug-plug-in.md#use-tracing)  
[トレース ログの表示](tutorial-write-plug-in.md#view-trace-logs)  
[トレース サービスの使用](write-plug-in.md#use-the-tracing-service)  
[PluginTraceLog エンティティ](reference/entities/plugintracelog.md)