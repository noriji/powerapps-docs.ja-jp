---
title: Web サービスのエラー コード (Common Data Service) | Microsoft Docs
description: 'このトピックでは、コードをデバッグする際に発生する可能性のあるエラー コードの一覧を示します。 '
ms.custom: ''
ms.date: 05/09/2019
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: brandonsimons
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---

# <a name="web-service-error-codes"></a>Web サービス エラー コード

このトピックでは、コードをデバッグする際に発生する可能性のあるエラー コードの一覧を示します。

<a name="BKMK_CRMErrors"></a>   

## <a name="common-data-service-errors"></a>Common Data Service エラー 

 次の一覧は、Common Data Service で使用されるエラー コードを示します。 詳細については [コードで例外を処理](handle-exceptions-code.md) を参照してください。  

> [!div class="mx-tdBreakAll"]
>
> |エラー|メッセージ|
> |---|---|
> |**名前**:<br />AccessDenied<br />**16 進数**:<br />80048405<br />**数値**:<br />-2147187707|アクセスが拒否されました。|
> |**名前**:<br />AccessDeniedSharePointRecord<br />**16 進数**:<br />80060904<br />**数値**:<br />-2147088124|Dynamics 365 の SharePoint レコードで、アクセスが拒否されました。|
> |**名前**:<br />AccessTokenExpired<br />**16 進数**:<br />8005F101<br />**数値**:<br />-2147094271|要求されたリソースには認証が必要です。|
> |**名前**:<br />AccountDoesNotExist<br />**16 進数**:<br />80040502<br />**数値**:<br />-2147220222|アカウントが存在しません。|
> |**名前**:<br />AccountLoopBeingCreated<br />**16 進数**:<br />80040507<br />**数値**:<br />-2147220217|この上位下位の関連付けを作成すると、取引先企業の階層にループが生成されます。|
> |**名前**:<br />AccountLoopExists<br />**16 進数**:<br />80040506<br />**数値**:<br />-2147220218|取引先企業の階層にループが存在します。|
> |**名前**:<br />ActionCardDisabledError<br />**16 進数**:<br />80071100<br />**数値**:<br />-2147020544|アクション カードの機能が有効になっていません。|
> |**名前**:<br />ActionCardInvalidStateCodeException<br />**16 進数**:<br />80071103<br />**数値**:<br />-2147020541|無効な状態コードが条件式に渡されました。|
> |**名前**:<br />ActionStepInvalidPipelineStageid<br />**16 進数**:<br />8006040e<br />**数値**:<br />-2147089394|ActionStep は無効なパイプライン ステージ ID を参照します。|
> |**名前**:<br />ActionStepInvalidProcessAction<br />**16 進数**:<br />8006041c<br />**数値**:<br />-2147089380|ActionStep {0} は無効なプロセス アクション {1} を参照しています。|
> |**名前**:<br />ActionStepInvalidProcessid<br />**16 進数**:<br />8006040d<br />**数値**:<br />-2147089395|ActionStep は無効なプロセス ID を参照します。|
> |**名前**:<br />ActionStepInvalidStageid<br />**16 進数**:<br />8006040c<br />**数値**:<br />-2147089396|ActionStep は無効なステージ ID を参照します。|
> |**名前**:<br />ActionSupportNotEnabled<br />**16 進数**:<br />80060382<br />**数値**:<br />-2147089534| アクション ステップが含まれているビジネス プロセスをエクスポートできません。アクション ステップのサポートは、まだパブリック プレビュー機能であり、現在この組織で有効になっていません。|
> |**名前**:<br />ActivePropertyValidationFailed<br />**16 進数**:<br />80061001<br />**数値**:<br />-2147086335|非アクティブなプロパティ インスタンスを作成することはできません。|
> |**名前**:<br />ActiveQueueItemAlreadyExists<br />**16 進数**:<br />80040526<br />**数値**:<br />-2147220186|アクティブなキュー アイテムは、指定されたオブジェクトに既に存在します。 このオブジェクトに対する複数のアクティブなキュー アイテムを作成できません。|
> |**名前**:<br />ActiveSlaCannotEdit<br />**16 進数**:<br />8004F871<br />**数値**:<br />-2147157903|アクティブな SLA を編集することはできません。 SLA を非アクティブ化してから編集してください。|
> |**名前**:<br />ActiveStageIdDoesNotMatchLastStageInTraversedPath<br />**16 進数**:<br />80060455<br />**数値**:<br />-2147089323|アクティブなステージ ID ‘{0}’ が、渡ったパス ‘{1}’ の最後のステージ ID と一致しません。 システム管理者にお問い合わせください。|
> |**名前**:<br />ActiveStageIDIsNull<br />**16 進数**:<br />80060449<br />**数値**:<br />-2147089335|ビジネス プロセスの更新エラー: アクティブ ステージ ID を空にできません。|
> |**名前**:<br />ActiveStageIsNotOnLeadEntity<br />**16 進数**:<br />80100002<br />**数値**:<br />-2146435070|'リード' エンティティのアクティブなステージではありません。|
> |**名前**:<br />ActivityAnalysisOrganizationUpdateError<br />**16 進数**:<br />80044275<br />**数値**:<br />-2147204491|リレーションシップ分析組織の設定は、リレーションシップ分析ソリューションがインストールされている場合にのみ、有効にすることができます。|
> |**名前**:<br />ActivityCannotHaveRelatedActivities<br />**16 進数**:<br />8004F121<br />**数値**:<br />-2147159775|活動として定義されたユーザー定義エンティティは、活動との関連付けを設定できません。|
> |**名前**:<br />ActivityEntityCannotBeActivityParty<br />**16 進数**:<br />80048501<br />**数値**:<br />-2147187455|アクティブな エンティティは、活動関係者でもありません|
> |**名前**:<br />ActivityInvalidObjectTypeCode<br />**16 進数**:<br />80043513<br />**数値**:<br />-2147207917|無効な種類コードが、スローするメソッドにより指定されました|
> |**名前**:<br />ActivityInvalidSessionToken<br />**16 進数**:<br />80043512<br />**数値**:<br />-2147207918|無効なセッション トークンはスローするメソッドに渡されました|
> |**名前**:<br />ActivityMetadataUpdate<br />**16 進数**:<br />8004F126<br />**数値**:<br />-2147159770|活動のために指定されたメタデータは無効です。|
> |**名前**:<br />ActivityMustHaveRelatedNotes<br />**16 進数**:<br />8004F123<br />**数値**:<br />-2147159773|活動として定義されたユーザー定義エンティティは、既定でメモへの関連付けを設定する必要があります。|
> |**名前**:<br />ActivityPartyObjectTypeNotAllowed<br />**16 進数**:<br />80043506<br />**数値**:<br />-2147207930|指定したオブジェクトの種類の活動関係者を作成できません。|
> |**名前**:<br />AdminProfileCannotBeEditedOrDeleted<br />**16 進数**:<br />8004F50C<br />**数値**:<br />-2147158772|システム管理者フィールド セキュリティ プロファイルを変更または削除できません。|
> |**名前**:<br />AdvancedSimilarityAzureSearchUnexpectedError<br />**16 進数**:<br />80061696<br />**数値**:<br />-2147084650|検索の実行中に予期しないエラーが発生しました。 後でもう一度試してみてください。|
> |**名前**:<br />AggregateInnerQuery<br />**16 進数**:<br />8004D2B1<br />**数値**:<br />-2147167567|内部クエリを集計クエリにすることはできません。|
> |**名前**:<br />AggregateQueryRecordLimitExceeded<br />**16 進数**:<br />8004E023<br />**数値**:<br />-2147164125|レコード数の上限を超えています。 レコード数を減らしてください。|
> |**名前**:<br />AlreadyLinkedToAnotherAttribute<br />**16 進数**:<br />8004F0FE<br />**数値**:<br />-2147159810|指定されたリンクされた属性は、他の属性に既にリンクされています。|
> |**名前**:<br />AppConfigFeatureNotEnabled<br />**16 進数**:<br />80072200<br />**数値**:<br />-2147016192|アプリ内カスタマイズのアプリ構成機能が有効ではありません。|
> |**名前**:<br />ApplicationMetadataConverterFailed<br />**16 進数**:<br />8005F231<br />**数値**:<br />-2147093967|問題が発生しました。 操作をやり直すか、アプリを再起動してください。|
> |**名前**:<br />ApplicationMetadatadaCreateFailed<br />**16 進数**:<br />8005F233<br />**数値**:<br />-2147093965|問題が発生しました。 操作をやり直すか、アプリを再起動してください。|
> |**名前**:<br />ApplicationMetadatadaNullData<br />**16 進数**:<br />8005F232<br />**数値**:<br />-2147093966|問題が発生しました。 操作をやり直すか、アプリを再起動してください。|
> |**名前**:<br />ApplicationMetadatadaUpdateFailed<br />**16 進数**:<br />8005F234<br />**数値**:<br />-2147093964|問題が発生しました。 操作をやり直すか、アプリを再起動してください。|
> |**名前**:<br />ApplicationMetadataFailedWithContinue<br />**16 進数**:<br />8005F241<br />**数値**:<br />-2147093951|サーバーの構成の変更に問題がありました。  アプリケーションを引き続き使用できますが、変更を保存できないなどの問題が発生する可能性があります。 Dynamics 365 管理者に連絡して、[詳細情報] に示された情報を伝えてください。|
> |**名前**:<br />ApplicationMetadataGetPreviewMetadataUnknownError<br />**16 進数**:<br />8005F230<br />**数値**:<br />-2147093968|問題が発生しました。 操作をやり直すか、アプリを再起動してください。|
> |**名前**:<br />ApplicationMetadataPrepareCustomizationsAppLock<br />**16 進数**:<br />8005F237<br />**数値**:<br />-2147093961|お客様のユーザーに対してカスタマイズの準備をしている間に、問題が発生しました。 この問題が解決されるまで、一部のクライアント上のユーザーは、カスタマイズ更新プログラムをダウンロードすることはできません。|
> |**名前**:<br />ApplicationMetadataPrepareCustomizationsRetrieverError<br />**16 進数**:<br />8005F235<br />**数値**:<br />-2147093963|サーバーの構成の変更に問題がありました。  ユーザーはアプリケーションを引き続き使用できますが、変更を保存できないなどの問題が発生する可能性があります。|
> |**名前**:<br />ApplicationMetadataPrepareCustomizationsTimeout<br />**16 進数**:<br />8005F236<br />**数値**:<br />-2147093962|申し訳ございません。クライアントのカスタマイズの変更を処理できませんでした。  原因として、ユーザーに対して大量のエンティティが有効になっているか、多数の言語が有効になっている可能性があります。  ユーザーのカスタマイズはこの問題が解決されるまで処理されません。|
> |**名前**:<br />ApplicationMetadataPrepareCustomizationsUnknownError<br />**16 進数**:<br />8005F226<br />**数値**:<br />-2147093978|問題が発生しました。 操作をやり直すか、アプリを再起動してください。|
> |**名前**:<br />ApplicationMetadataRetrieveUnknownError<br />**16 進数**:<br />8005F229<br />**数値**:<br />-2147093975|問題が発生しました。 操作をやり直すか、アプリを再起動してください。|
> |**名前**:<br />ApplicationMetadataRetrieveUserContextUnknownError<br />**16 進数**:<br />8005F227<br />**数値**:<br />-2147093977|問題が発生しました。 操作をやり直すか、アプリを再起動してください。|
> |**名前**:<br />ApplicationMetadataSyncAppLock<br />**16 進数**:<br />8005F244<br />**数値**:<br />-2147093948|申し訳ありません。サーバーがビジーであるため、今すぐ構成をダウンロードできません。 変更は数分後に利用可能になります。  数分待ってからもう一度サインインします。|
> |**名前**:<br />ApplicationMetadataSyncAppLockWithContinue<br />**16 進数**:<br />8005F245<br />**数値**:<br />-2147093947|申し訳ありません。サーバーがビジーであるため、今すぐ構成変更をダウンロードできません。 変更は数分後に利用可能になります。  その間アプリを引き続き使用でき、後に変更をダウンロードするよう通知されます。 または、数分間待ち、アプリケーションを再起動し、やり直すためにプロンプトを受け入れます。|
> |**名前**:<br />ApplicationMetadataSyncFailed<br />**16 進数**:<br />8005F240<br />**数値**:<br />-2147093952|サーバーの構成の変更に問題がありました。  アプリケーションを読み込めません。Dynamics 365 管理者に問い合わせてください。|
> |**名前**:<br />ApplicationMetadataSyncTimeout<br />**16 進数**:<br />8005F242<br />**数値**:<br />-2147093950|申し訳ございません。サーバー構成の変更をダウンロードできませんでした。  原因として、接続速度の遅さ、またはモバイル使用に対し大量のエンティティが有効になっていることが考えられます。  接続を確認して、やり直してください。  この問題が続く場合は、Dynamics 365 管理者に問い合わせてください。|
> |**名前**:<br />ApplicationMetadataSyncTimeoutWithContinue<br />**16 進数**:<br />8005F243<br />**数値**:<br />-2147093949|申し訳ございません。サーバー構成の変更をダウンロードできませんでした。  原因として、接続速度の遅さ、またはモバイル使用に対し大量のエンティティが有効になっていることが考えられます。  接続を確認して、やり直してください。 アプリは引き続き古い構成で使用できます。しかし、保存時のエラーなど何らかの問題が発生することがあります。  この問題が続く場合は、Dynamics 365 管理者に問い合わせてください。|
> |**名前**:<br />ApplicationMetadataSyncUnknownError<br />**16 進数**:<br />8005F228<br />**数値**:<br />-2147093976|問題が発生しました。 操作をやり直すか、アプリを再起動してください。|
> |**名前**:<br />ApplicationMetadataUserValidationUnknownError<br />**16 進数**:<br />8005F225<br />**数値**:<br />-2147093979|問題が発生しました。 操作をやり直すか、アプリを再起動してください。|
> |**名前**:<br />ApplicationNotRegisteredWithDeployment<br />**16 進数**:<br />80041d49<br />**数値**:<br />-2147214007|この組織用に作成する前に、アプリケーションをレベル展開で登録し有効化する必要があります|
> |**名前**:<br />ApplicationProfileMustContainEntity<br />**16 進数**:<br />80071131<br />**数値**:<br />-2147020495|アプリケーション プロファイルには 1 つ以上のエンティティを含めてください。|
> |**名前**:<br />ApplicationUserCannotBeUpdated<br />**16 進数**:<br />80041d48<br />**数値**:<br />-2147214008|OAuth アプリケーションを代表するユーザーを更新することはできません|
> |**名前**:<br />AppLockTimeout<br />**16 進数**:<br />8004Ed47<br />**数値**:<br />-2147160761|applock を取得する前にタイムアウトが期限切れになりました。|
> |**名前**:<br />ApplyActiveSLAOnly<br />**16 進数**:<br />80055001<br />**数値**:<br />-2147135487|アクティブなサービス レベル アグリーメント (SLA) は、サポート案件のみに適用できます。|
> |**名前**:<br />AppModuleComponentEntityMustHaveFormOrView<br />**16 進数**:<br />80050115<br />**数値**:<br />-2147155691|エンティティ “{0}” は、アプリに少なくとも 1 つのフォームまたはビューがあります。|
> |**名前**:<br />AppModuleFeatureNotEnabled<br />**16 進数**:<br />80050117<br />**数値**:<br />-2147155689|機能は、この組織に対して有効になっていません。|
> |**名前**:<br />AppModuleMustHaveOnlyValidClientEntity<br />**16 進数**:<br />8005012A<br />**数値**:<br />-2147155670|“{0}“ エンティティは選択されたクライアントに対して無効であり、実行時に表示されません。|
> |**名前**:<br />AppModuleNotContainMOCAEnabledEntity<br />**16 進数**:<br />80050118<br />**数値**:<br />-2147155688|サポートされているクライアントとして MOCA を使用するアプリ モジュールには、少なくとも 1 つの MOCA 対応エンティティが必要です|
> |**名前**:<br />AppModuleNotReferEntity<br />**16 進数**:<br />8005011D<br />**数値**:<br />-2147155683|アプリ モジュールが 1 つ以上のエンティティを参照していません|
> |**名前**:<br />AppModulesImportError<br />**16 進数**:<br />80050123<br />**数値**:<br />-2147155677|アプリ モジュールのインポート中にエラーが発生しました|
> |**名前**:<br />AppModuleWithClientExists<br />**16 進数**:<br />80050127<br />**数値**:<br />-2147155673|アプリを作成できませんでした。 既にこのクライアントの種類のアプリがあります。|
> |**名前**:<br />AppointmentDeleted<br />**16 進数**:<br />8004E106<br />**数値**:<br />-2147163898|予定エンティティ インスタンスはすでに削除されています。|
> |**名前**:<br />AppointmentScheduleNotSet<br />**16 進数**:<br />80040275<br />**数値**:<br />-2147220875|Outlook との同期のために、終了スケジュールおよび開始スケジュールを予定に設定する必要があります。|
> |**名前**:<br />ArgumentDirectionMismatch<br />**16 進数**:<br />80060388<br />**数値**:<br />-2147089528|引数 {0} の方向が一致しません。|
> |**名前**:<br />ArgumentTypeMismatch<br />**16 進数**:<br />80060387<br />**数値**:<br />-2147089529|引数 {0} の種類が一致しません。|
> |**名前**:<br />ArrayMappingFoundForSingletonParameter<br />**16 進数**:<br />8004037f<br />**数値**:<br />-2147220609|配列変換パラメーター マッピングは、単一パラメーター用に定義されます。|
> |**名前**:<br />ArticleIsPublished<br />**16 進数**:<br />800404fe<br />**数値**:<br />-2147220226|この記事はすでに公開状態にあるため、更新または削除はできません|
> |**名前**:<br />AssociateProductFailureDifferentUom<br />**16 進数**:<br />80061040<br />**数値**:<br />-2147086272|製品をバンドルに追加できません。 製品の出荷単位一覧に属している製品出荷単位を使用する必要があります。|
> |**名前**:<br />AssociationRoleOrdinalInvalid<br />**16 進数**:<br />80048468<br />**数値**:<br />-2147187608|関連付けロール序数は無効です - 1 または 2 にする必要があります。|
> |**名前**:<br />AsyncCommunicationError<br />**16 進数**:<br />80044307<br />**数値**:<br />-2147204345|この非同期操作の処理中に通信エラーが発生しました。|
> |**名前**:<br />AsyncNetworkError<br />**16 進数**:<br />80044306<br />**数値**:<br />-2147204346|ネットワークにアクセス中にエラーが発生しました。|
> |**名前**:<br />AsyncOperationCannotCancel<br />**16 進数**:<br />80044F00<br />**数値**:<br />-2147201280|このシステム ジョブを取り消すことができません。|
> |**名前**:<br />AsyncOperationCannotDeleteUnlessCompleted<br />**16 進数**:<br />8004416a<br />**数値**:<br />-2147204758|完了状態にある場合を除き、非同期操作を削除できません。|
> |**名前**:<br />AsyncOperationCannotPause<br />**16 進数**:<br />80044F01<br />**数値**:<br />-2147201279|このシステム ジョブを一時停止できません。|
> |**名前**:<br />AsyncOperationCannotUpdateNonrecurring<br />**16 進数**:<br />80044168<br />**数値**:<br />-2147204760|定期的でないジョブの定期的なアイテム パターンは更新できません。|
> |**名前**:<br />AsyncOperationCannotUpdateRecurring<br />**16 進数**:<br />80044169<br />**数値**:<br />-2147204759|サポートされていないジョブの種類の定期的なアイテム パターンは更新できません。|
> |**名前**:<br />AsyncOperationInvalidStateChange<br />**16 進数**:<br />80044162<br />**数値**:<br />-2147204766|状態の遷移が無効なため、ターゲットの状態を設定できませんでした。|
> |**名前**:<br />AsyncOperationInvalidStateChangeToComplete<br />**16 進数**:<br />80044165<br />**数値**:<br />-2147204763|状態の遷移が無効なため、ターゲットの状態を完了に設定できませんでした。|
> |**名前**:<br />AsyncOperationInvalidStateChangeToReady<br />**16 進数**:<br />80044166<br />**数値**:<br />-2147204762|状態の遷移が無効なため、ターゲットの状態を準備完了に設定できませんでした。|
> |**名前**:<br />AsyncOperationInvalidStateChangeToSuspended<br />**16 進数**:<br />80044167<br />**数値**:<br />-2147204761|状態の遷移が無効なため、ターゲットの状態を一時停止に設定できませんでした。|
> |**名前**:<br />AsyncOperationInvalidStateChangeUnexpected<br />**16 進数**:<br />80044163<br />**数値**:<br />-2147204765|状態が別のプロセスにより変更されたため、ターゲットの状態を設定できませんでした。|
> |**名前**:<br />AsyncOperationMissingId<br />**16 進数**:<br />80044164<br />**数値**:<br />-2147204764|更新プログラムの実行には AsyncOperationId が必要です。|
> |**名前**:<br />AsyncOperationPostponed<br />**16 進数**:<br />80040328<br />**数値**:<br />-2147220696|{1} 分で {0} 回失敗したため、この操作は延期されています|
> |**名前**:<br />AsyncOperationPostponedByExceptionCountThrottle<br />**16 進数**:<br />80060917<br />**数値**:<br />-2147088105|現在、このアクションを完了できません。 延期されました。 後でやり直します。|
> |**名前**:<br />AsyncOperationSuspendedOrLocked<br />**16 進数**:<br />80040339<br />**数値**:<br />-2147220679|>このインポートに関連付けられたバックグラウンド ジョブは、中断またはロックされています。 このインポートを削除するには、ワークプレースで [インポート] をクリックしてインポートを開き、次に [システム ジョブ] をクリックし、中断されているジョブを再開します。|
> |**名前**:<br />AsyncOperationTypeIsNotRecognized<br />**16 進数**:<br />80044303<br />**数値**:<br />-2147204349|非同期処理の操作の種類は認識されませんでした。|
> |**名前**:<br />AsyncOperationTypeThrottled<br />**16 進数**:<br />80060916<br />**数値**:<br />-2147088106|サーバーがビジー状態のため、ジョブを完了できませんでした。 まもなくジョブを再試行します。|
> |**名前**:<br />AttachmentBlocked<br />**16 進数**:<br />80043e09<br />**数値**:<br />-2147205623|添付ファイルが無効な種類、または大きすぎます。 ダウンロードまたはアップロードはできません。|
> |**名前**:<br />AttachmentInvalidFileName<br />**16 進数**:<br />80044a08<br />**数値**:<br />-2147202552|添付ファイルの名前に無効な文字が含まれています。|
> |**名前**:<br />AttachmentNotFound<br />**16 進数**:<br />80048493<br />**数値**:<br />-2147187565|添付ファイルへの参照が見つかりませんでした。|
> |**名前**:<br />AttachmentNotRelatedToEmail<br />**16 進数**:<br />80050006<br />**数値**:<br />-2147155962|この添付ファイルは電子メールに属していません。|
> |**名前**:<br />AttributeCannotBeUpdated<br />**16 進数**:<br />80060413<br />**数値**:<br />-2147089389|属性 - {0} は業務プロセス フローで更新することはできません|
> |**名前**:<br />AttributeCannotBeUsedInAggregate<br />**16 進数**:<br />80060559<br />**数値**:<br />-2147089063|属性が {0} の場合は計算式の集計関数では使用できません。|
> |**名前**:<br />AttributeDeprecated<br />**16 進数**:<br />80044335<br />**数値**:<br />-2147204299|"エンティティ '{1}' の属性 '{0}' は非推奨です。"|
> |**名前**:<br />AttributeDoesNotSupportLocalizedLabels<br />**16 進数**:<br />80044198<br />**数値**:<br />-2147204712|指定された属性は、ローカライズされたラベルをサポートしません。|
> |**名前**:<br />AttributeFormulaDefinitionIsEmpty<br />**16 進数**:<br />80060439<br />**数値**:<br />-2147089351|計算式が空です。|
> |**名前**:<br />AttributeIsNotCustomAttribute<br />**16 進数**:<br />80047009<br />**数値**:<br />-2147192823|指定された属性は、ユーザー定義属性ではありません|
> |**名前**:<br />AttributeIsNotFacetable<br />**16 進数**:<br />80060305<br />**数値**:<br />-2147089659|属性が {1} facetable ではないため、エンティティに {0} 対するユーザー検索ファセットを設定できません。 続行のためにリストから削除してください。|
> |**名前**:<br />AttributeNotCreatedForOfficeGraphError<br />**16 進数**:<br />80044237<br />**数値**:<br />-2147204553|officegraph の属性を有効にするサポートが使用できないため、この属性は作成できません。|
> |**名前**:<br />AttributeNotOfTypePicklist<br />**16 進数**:<br />8004033c<br />**数値**:<br />-2147220676|この属性は、ドロップダウン リスト、ブール値、または状態 / ステータス属性にはマップされていません。 ただし、それに ListValueMap 要素を含めました。  この不整合を修正してから、もう一度このデータ マップをインポートしてください。|
> |**名前**:<br />AttributeNotOfTypeReference<br />**16 進数**:<br />80040390<br />**数値**:<br />-2147220592|この属性は、参照属性としてはマップされていません。 ただし、それに ReferenceMap 要素を含めました。  この不整合を修正してから、もう一度このデータ マップをインポートしてください。|
> |**名前**:<br />AttributeNotSecured<br />**16 進数**:<br />8004F508<br />**数値**:<br />-2147158776|1 つまたは複数のフィールドがフィールドレベルのセキュリティに対して有効ではありません。 フィールド レベル セキュリティは、カスタマイズを公開するまで有効になっていません。|
> |**名前**:<br />AttributeNotUpdatedForOfficeGraphError<br />**16 進数**:<br />80044238<br />**数値**:<br />-2147204552|officegraph の属性を有効にするサポートが使用できないため、この属性は更新できません。|
> |**名前**:<br />AttributePermissionIsInvalid<br />**16 進数**:<br />8004F50E<br />**数値**:<br />-2147158770|ID={2} をもつフィールド '{1}' のアクセス許可 '{0}' は無効です。|
> |**名前**:<br />AttributePermissionReadIsMissing<br />**16 進数**:<br />8004F504<br />**数値**:<br />-2147158780|セキュリティで保護されたフィールドに対する読み取りアクセス許可がありません。 要求された操作が完了しませんでした。|
> |**名前**:<br />AttributePermissionUpdateIsMissingDuringShare<br />**16 進数**:<br />8004F503<br />**数値**:<br />-2147158781|セキュリティで保護されたフィールドに対する更新アクセス許可がありません。 要求された操作が完了しませんでした。|
> |**名前**:<br />AttributePermissionUpdateIsMissingDuringUpdate<br />**16 進数**:<br />8004F507<br />**数値**:<br />-2147158777|ユーザーに AttributePrivilegeUpdate がなく、更新操作中にセキュリティで保護された属性の共有アクセス許可が与えられていません|
> |**名前**:<br />AttributePrivilegeCreateIsMissing<br />**16 進数**:<br />8004F502<br />**数値**:<br />-2147158782|セキュリティで保護されたフィールドに対する作成アクセス許可がありません。 要求された操作が完了しませんでした。|
> |**名前**:<br />AttributePrivilegeInvalidToUnsecure<br />**16 進数**:<br />8004F50D<br />**数値**:<br />-2147158771|セキュリティで保護されているフィールドのフィールド レベルのセキュリティを変更するには、適切なアクセス許可が必要です。|
> |**名前**:<br />AttributesExceeded<br />**16 進数**:<br />80061501<br />**数値**:<br />-2147085055|属性は、4 より大きい値を指定できません|
> |**名前**:<br />AttributeSharingCreateDuplicate<br />**16 進数**:<br />8004F50B<br />**数値**:<br />-2147158773|属性は既に共有されています。|
> |**名前**:<br />AttributeSharingCreateShouldSetReadOrAndUpdateAccess<br />**16 進数**:<br />8004F509<br />**数値**:<br />-2147158775|セキュリティで保護された属性を共有する際には、読み取り、更新、またはその両方のアクセス権を設定する必要があります。 属性 ID: {0}|
> |**名前**:<br />AttributeSharingUpdateInvalid<br />**16 進数**:<br />8004F50A<br />**数値**:<br />-2147158774|readAccess と updateAccess の両方が false です: Update の代わりに Delete を呼び出します。|
> |**名前**:<br />AttributeTypeNotSupportedForCalculatedField<br />**16 進数**:<br />80050221<br />**数値**:<br />-2147155423|計算/ロールアップ フィールドは MultiSelectPicklist 属性の種類ではサポートされていません。|
> |**名前**:<br />AttributeTypeNotSupportedForGroupByOrderByQuery<br />**16 進数**:<br />80050224<br />**数値**:<br />-2147155420|GroupBy または OrderBy クエリは、MultiSelectPickList 属性の種類ではサポートされていません。|
> |**名前**:<br />AttributeUpdateNotAllowed<br />**16 進数**:<br />80060463<br />**数値**:<br />-2147089309|業務プロセス フローの更新に失敗しました。 ワークフロー "{1}" の属性 "{0}" の更新は許可されていません。|
> |**名前**:<br />AuthenticateToServerBeforeRequestingProxy<br />**16 進数**:<br />8004D228<br />**数値**:<br />-2147167704|プロキシを要求する前に serverType: {0} へ認証します。|
> |**名前**:<br />AutoDataCaptureAuthorizationFailureException<br />**16 進数**:<br />80091042<br />**数値**:<br />-2146889662|追跡対象でない電子メールを取得するための適切な Office 365 ライセンスがありません。 システム管理者にお問い合わせください。|
> |**名前**:<br />AutoDataCaptureDisabledError<br />**16 進数**:<br />80091041<br />**数値**:<br />-2146889663|自動取り込みの機能が有効になっていません。|
> |**名前**:<br />AutoDataCaptureResponseRetrievalFailureException<br />**16 進数**:<br />80091043<br />**数値**:<br />-2146889661|Exchange から未追跡の電子メールをフェッチ中にエラーが発生しました。|
> |**名前**:<br />AzureApplicationIdNotFound<br />**16 進数**:<br />8004F510<br />**数値**:<br />-2147158768|CorrelationID {1} を使用する Azure Active Directory (Azure AD) で、アプリケーション ID {0} が見つかりませんでした。 アプリケーションが Azure AD に登録されていることを確認してください。|
> |**名前**:<br />AzureApplicationIdNotFoundInOrgDB<br />**16 進数**:<br />8004F512<br />**数値**:<br />-2147158766|Azure applicationid が見つかりません。 CRM データベースでアプリケーション ID {0} を見つけることができませんでした。 アプリケーション ID を修正して更新を再送信します。|
> |**名前**:<br />AzureOperationResponseTimedOut<br />**16 進数**:<br />80061635<br />**数値**:<br />-2147084747|Azure 操作要求は、提示されたタイムアウト期間内に反応を返しませんでした。 操作を再試行するか、操作のタイムアウトを増やしてください。|
> |**名前**:<br />AzureRecommendationModelBuildNotExist<br />**16 進数**:<br />80061604<br />**数値**:<br />-2147084796|使用するモデル バージョンに対応する Azure レコメンデーション モデル ビルドが存在していません。|
> |**名前**:<br />AzureRecommendationModelNotExist<br />**16 進数**:<br />80061603<br />**数値**:<br />-2147084797|Azure レコメンデーション モデルが見つかりません。|
> |**名前**:<br />AzureServiceConnectionCascadeDeleteFailed<br />**16 進数**:<br />80061636<br />**数値**:<br />-2147084746|1 つまたは複数のモデルは接続を使用します。 この接続を使用しているすべてのモデルを削除してから、接続の削除をやり直してください。|
> |**名前**:<br />AzureServiceConnectionInvalidUri<br />**16 進数**:<br />80061630<br />**数値**:<br />-2147084752|有効なサービス URL を指定します。|
> |**名前**:<br />AzureSqlDatabaseResourceLimitExceededError<br />**16 進数**:<br />80072323<br />**数値**:<br />-2147015901|データベースのリソースの上限に達しました。 詳細については例外を確認してください。|
> |**名前**:<br />AzureSqlDatabaseStorageQuotaExceededError<br />**16 進数**:<br />80072325<br />**数値**:<br />-2147015899|データベースの記憶域制限に達しました。|
> |**名前**:<br />AzureSqlMaxConcurrentWorkersLimitExceededError<br />**16 進数**:<br />80072324<br />**数値**:<br />-2147015900|検出された同時実行要求が多すぎます。|
> |**名前**:<br />AzureWebAppPluginsDisabled<br />**16 進数**:<br />80050241<br />**数値**:<br />-2147155391|Azure WebApp ベースのプラグインが組織で無効になっています。|
> |**名前**:<br />BadAuthTicket<br />**16 進数**:<br />8004A102<br />**数値**:<br />-2147180286|認証のために指定されたチケットは無効です|
> |**名前**:<br />BadRequest<br />**16 進数**:<br />8005F100<br />**数値**:<br />-2147094272|要求が、サーバーにより理解されませんでした。|
> |**名前**:<br />BaseAttributeNameNotPresentError<br />**16 進数**:<br />80044240<br />**数値**:<br />-2147204544|condition xml 内に BaseAttribute 名が存在する必要があります。|
> |**名前**:<br />BaseCurrencyCannotBeDeactivated<br />**16 進数**:<br />80048cf4<br />**数値**:<br />-2147185420|基本通貨を非アクティブ化することはできません。|
> |**名前**:<br />BaseCurrencyNotDeletable<br />**16 進数**:<br />80048cff<br />**数値**:<br />-2147185409|組織の基本通貨を削除することはできません。|
> |**名前**:<br />BaseCurrencyOverflow<br />**16 進数**:<br />80048cec<br />**数値**:<br />-2147185428|このレコードで指定された通貨の設定されている為替レートを使用すると、生成された {0} の値が、基本通貨 ({1})に許容されている最大値よりも大きくなります。|
> |**名前**:<br />BaseCurrencyUnderflow<br />**16 進数**:<br />80048ceb<br />**数値**:<br />-2147185429|このレコードで指定された通貨の設定されている為替レートを使用すると、生成された {0} の値が、基本通貨 ({1})に許容されている最小値よりも小さくなります。|
> |**名前**:<br />BaseMatchingAttributeNotSameError<br />**16 進数**:<br />80044245<br />**数値**:<br />-2147204539|ベース属性と一致する属性は同じ種類である必要があります。|
> |**名前**:<br />BaseUnitDoesNotExist<br />**16 進数**:<br />80043b1c<br />**数値**:<br />-2147206372|基本出荷単位が存在しません。|
> |**名前**:<br />BaseUnitNotDeletable<br />**16 進数**:<br />80043b03<br />**数値**:<br />-2147206397|スケジュールの基本出荷単位は削除できません。|
> |**名前**:<br />BaseUnitNotNull<br />**16 進数**:<br />80043b17<br />**数値**:<br />-2147206377|標準出荷単位の値として基本出荷単位を使用しないでください。 この値は常に null にする必要があります。|
> |**名前**:<br />BaseUomNameNotSpecified<br />**16 進数**:<br />80043810<br />**数値**:<br />-2147207152|baseuomname が指定されていません|
> |**名前**:<br />BDK_E_ADDRESS_VALIDATION_FAILURE<br />**16 進数**:<br />8004B540<br />**数値**:<br />-2147175104|{0}  |
> |**名前**:<br />BDK_E_AGREEMENT_ALREADY_SIGNED<br />**16 進数**:<br />8004B541<br />**数値**:<br />-2147175103|{0}  |
> |**名前**:<br />BDK_E_AUTHORIZATION_FAILED<br />**16 進数**:<br />8004B542<br />**数値**:<br />-2147175102|{0}  |
> |**名前**:<br />BDK_E_AVS_FAILED<br />**16 進数**:<br />8004B543<br />**数値**:<br />-2147175101|{0}  |
> |**名前**:<br />BDK_E_BAD_CITYNAME_LENGTH<br />**16 進数**:<br />8004B544<br />**数値**:<br />-2147175100|{0}  |
> |**名前**:<br />BDK_E_BAD_STATECODE_LENGTH<br />**16 進数**:<br />8004B545<br />**数値**:<br />-2147175099|{0}  |
> |**名前**:<br />BDK_E_BAD_ZIPCODE_LENGTH<br />**16 進数**:<br />8004B546<br />**数値**:<br />-2147175098|{0}  |
> |**名前**:<br />BDK_E_BADXML<br />**16 進数**:<br />8004B547<br />**数値**:<br />-2147175097|{0}  |
> |**名前**:<br />BDK_E_BANNED_PAYMENT_INSTRUMENT<br />**16 進数**:<br />8004B548<br />**数値**:<br />-2147175096|{0}  |
> |**名前**:<br />BDK_E_BANNEDPERSON<br />**16 進数**:<br />8004B549<br />**数値**:<br />-2147175095|{0}  |
> |**名前**:<br />BDK_E_CANNOT_EXCEED_MAX_OWNERSHIP<br />**16 進数**:<br />8004B54A<br />**数値**:<br />-2147175094|{0}  |
> |**名前**:<br />BDK_E_COUNTRY_CURRENCY_PI_MISMATCH<br />**16 進数**:<br />8004B54B<br />**数値**:<br />-2147175093|{0}  |
> |**名前**:<br />BDK_E_CREDIT_CARD_EXPIRED<br />**16 進数**:<br />8004B54C<br />**数値**:<br />-2147175092|{0}  |
> |**名前**:<br />BDK_E_DATE_EXPIRED<br />**16 進数**:<br />8004B54D<br />**数値**:<br />-2147175091|{0}  |
> |**名前**:<br />BDK_E_ERROR_COUNTRYCODE_MISMATCH<br />**16 進数**:<br />8004B54E<br />**数値**:<br />-2147175090|{0}  |
> |**名前**:<br />BDK_E_ERROR_COUNTRYCODE_REQUIRED<br />**16 進数**:<br />8004B54F<br />**数値**:<br />-2147175089|{0}  |
> |**名前**:<br />BDK_E_EXTRA_REFERRAL_DATA<br />**16 進数**:<br />8004B550<br />**数値**:<br />-2147175088|{0}  |
> |**名前**:<br />BDK_E_GUID_EXISTS<br />**16 進数**:<br />8004B551<br />**数値**:<br />-2147175087|{0}  |
> |**名前**:<br />BDK_E_INVALID_ADDRESS_ID<br />**16 進数**:<br />8004B552<br />**数値**:<br />-2147175086|{0}  |
> |**名前**:<br />BDK_E_INVALID_BILLABLE_ACCOUNT_ID<br />**16 進数**:<br />8004B553<br />**数値**:<br />-2147175085|{0} 指定された請求アカウントが無効です。  または、objectID が正しい種類にも関わらず、識別するアカウントはシステムに存在しません。|
> |**名前**:<br />BDK_E_INVALID_BUF_SIZE<br />**16 進数**:<br />8004B554<br />**数値**:<br />-2147175084|{0}  |
> |**名前**:<br />BDK_E_INVALID_CATEGORY_NAME<br />**16 進数**:<br />8004B555<br />**数値**:<br />-2147175083|{0}  |
> |**名前**:<br />BDK_E_INVALID_COUNTRY_CODE<br />**16 進数**:<br />8004B556<br />**数値**:<br />-2147175082|{0}  |
> |**名前**:<br />BDK_E_INVALID_CURRENCY<br />**16 進数**:<br />8004B557<br />**数値**:<br />-2147175081|{0}  |
> |**名前**:<br />BDK_E_INVALID_CUSTOMER_TYPE<br />**16 進数**:<br />8004B558<br />**数値**:<br />-2147175080|{0}  |
> |**名前**:<br />BDK_E_INVALID_DATE<br />**16 進数**:<br />8004B559<br />**数値**:<br />-2147175079|{0}  |
> |**名前**:<br />BDK_E_INVALID_EMAIL_ADDRESS<br />**16 進数**:<br />8004B55A<br />**数値**:<br />-2147175078|{0}  |
> |**名前**:<br />BDK_E_INVALID_FILTER<br />**16 進数**:<br />8004B55B<br />**数値**:<br />-2147175077|{0}  |
> |**名前**:<br />BDK_E_INVALID_GUID<br />**16 進数**:<br />8004B55C<br />**数値**:<br />-2147175076|{0}  |
> |**名前**:<br />BDK_E_INVALID_INPUT_TO_TAXWARE_OR_VERAZIP<br />**16 進数**:<br />8004B55D<br />**数値**:<br />-2147175075|{0}  |
> |**名前**:<br />BDK_E_INVALID_LOCALE<br />**16 進数**:<br />8004B55E<br />**数値**:<br />-2147175074|{0}  |
> |**名前**:<br />BDK_E_INVALID_OBJECT_ID<br />**16 進数**:<br />8004B55F<br />**数値**:<br />-2147175073|{0}  請求システムはオブジェクトを見つけることができません (例: アカウント、サブスクリプションまたはオファリング)。|
> |**名前**:<br />BDK_E_INVALID_OFFERING_GUID<br />**16 進数**:<br />8004B560<br />**数値**:<br />-2147175072|{0}  |
> |**名前**:<br />BDK_E_INVALID_PAYMENT_INSTRUMENT_STATUS<br />**16 進数**:<br />8004B561<br />**数値**:<br />-2147175071|{0}  |
> |**名前**:<br />BDK_E_INVALID_PAYMENT_METHOD_ID<br />**16 進数**:<br />8004B562<br />**数値**:<br />-2147175070|{0}  |
> |**名前**:<br />BDK_E_INVALID_PHONE_TYPE<br />**16 進数**:<br />8004B563<br />**数値**:<br />-2147175069|{0}  |
> |**名前**:<br />BDK_E_INVALID_POLICY_ID<br />**16 進数**:<br />8004B564<br />**数値**:<br />-2147175068|{0}  |
> |**名前**:<br />BDK_E_INVALID_REFERRALDATA_XML<br />**16 進数**:<br />8004B565<br />**数値**:<br />-2147175067|{0}  |
> |**名前**:<br />BDK_E_INVALID_STATE_FOR_COUNTRY<br />**16 進数**:<br />8004B566<br />**数値**:<br />-2147175066|{0}  |
> |**名前**:<br />BDK_E_INVALID_SUBSCRIPTION_ID<br />**16 進数**:<br />8004B567<br />**数値**:<br />-2147175065|{0} 指定されたサブスクリプション ID が無効です。  または、ObjectId が正しい種類であり、SCS の有効なアカウントをポイントしているにも関わらず、識別するサブスクリプションは SCS に存在しません。|
> |**名前**:<br />BDK_E_INVALID_TAX_EXEMPT_TYPE<br />**16 進数**:<br />8004B568<br />**数値**:<br />-2147175064|{0}  |
> |**名前**:<br />BDK_E_MEG_CONFLICT<br />**16 進数**:<br />8004B569<br />**数値**:<br />-2147175063|{0}  |
> |**名前**:<br />BDK_E_MULTIPLE_CITIES_FOUND<br />**16 進数**:<br />8004B56A<br />**数値**:<br />-2147175062|{0}  |
> |**名前**:<br />BDK_E_MULTIPLE_COUNTIES_FOUND<br />**16 進数**:<br />8004B56B<br />**数値**:<br />-2147175061|{0}  |
> |**名前**:<br />BDK_E_NON_ACTIVE_ACCOUNT<br />**16 進数**:<br />8004B56C<br />**数値**:<br />-2147175060|{0}  |
> |**名前**:<br />BDK_E_NOPERMISSION<br />**16 進数**:<br />8004B56D<br />**数値**:<br />-2147175059|{0}  呼び出し元パートナーがこのメソッドにアクセスできない、または依頼者が指定された検索 PUID を検索するアクセス許可を持っていない場合です。|
> |**名前**:<br />BDK_E_OBJECT_ROLE_LIMIT_EXCEEDED<br />**16 進数**:<br />8004B56E<br />**数値**:<br />-2147175058|{0}  |
> |**名前**:<br />BDK_E_OFFERING_ACCOUNT_CURRENCY_MISMATCH<br />**16 進数**:<br />8004B56F<br />**数値**:<br />-2147175057|{0}  |
> |**名前**:<br />BDK_E_OFFERING_COUNTRY_ACCOUNT_MISMATCH<br />**16 進数**:<br />8004B570<br />**数値**:<br />-2147175056|{0}  |
> |**名前**:<br />BDK_E_OFFERING_NOT_PURCHASEABLE<br />**16 進数**:<br />8004B571<br />**数値**:<br />-2147175055|{0}  |
> |**名前**:<br />BDK_E_OFFERING_PAYMENT_INSTRUMENT_MISMATCH<br />**16 進数**:<br />8004B572<br />**数値**:<br />-2147175054|{0}  |
> |**名前**:<br />BDK_E_OFFERING_REQUIRES_PI<br />**16 進数**:<br />8004B573<br />**数値**:<br />-2147175053|{0}  |
> |**名前**:<br />BDK_E_PARTNERNOTINBILLING<br />**16 進数**:<br />8004B574<br />**数値**:<br />-2147175052|{0}  |
> |**名前**:<br />BDK_E_PAYMENT_PROVIDER_CONNECTION_FAILED<br />**16 進数**:<br />8004B575<br />**数値**:<br />-2147175051|{0}  |
> |**名前**:<br />BDK_E_POLICY_DEAL_COUNTRY_MISMATCH<br />**16 進数**:<br />8004B577<br />**数値**:<br />-2147175049|{0}  |
> |**名前**:<br />BDK_E_PRIMARY_PHONE_REQUIRED<br />**16 進数**:<br />8004B576<br />**数値**:<br />-2147175050|{0}  |
> |**名前**:<br />BDK_E_PUID_ROLE_LIMIT_EXCEEDED<br />**16 進数**:<br />8004B578<br />**数値**:<br />-2147175048|{0}  |
> |**名前**:<br />BDK_E_RATING_FAILURE<br />**16 進数**:<br />8004B579<br />**数値**:<br />-2147175047|{0}  |
> |**名前**:<br />BDK_E_REQUIRED_FIELD_MISSING<br />**16 進数**:<br />8004B57A<br />**数値**:<br />-2147175046|{0}  |
> |**名前**:<br />BDK_E_STATE_CITY_INVALID<br />**16 進数**:<br />8004B57B<br />**数値**:<br />-2147175045|{0}  |
> |**名前**:<br />BDK_E_STATE_INVALID<br />**16 進数**:<br />8004B57C<br />**数値**:<br />-2147175044|{0}  |
> |**名前**:<br />BDK_E_STATE_ZIP_CITY_INVALID<br />**16 進数**:<br />8004B57D<br />**数値**:<br />-2147175043|{0}  |
> |**名前**:<br />BDK_E_STATE_ZIP_CITY_INVALID2<br />**16 進数**:<br />8004B57E<br />**数値**:<br />-2147175042|{0}  |
> |**名前**:<br />BDK_E_STATE_ZIP_CITY_INVALID3<br />**16 進数**:<br />8004B57F<br />**数値**:<br />-2147175041|{0}  |
> |**名前**:<br />BDK_E_STATE_ZIP_CITY_INVALID4<br />**16 進数**:<br />8004B580<br />**数値**:<br />-2147175040|{0}  |
> |**名前**:<br />BDK_E_STATE_ZIP_COVERS_MULTIPLE_CITIES<br />**16 進数**:<br />8004B581<br />**数値**:<br />-2147175039|{0}  |
> |**名前**:<br />BDK_E_STATE_ZIP_INVALID<br />**16 進数**:<br />8004B582<br />**数値**:<br />-2147175038|{0}  |
> |**名前**:<br />BDK_E_TAXID_EXPDATE<br />**16 進数**:<br />8004B583<br />**数値**:<br />-2147175037|{0}  |
> |**名前**:<br />BDK_E_TOKEN_BLACKLISTED<br />**16 進数**:<br />8004B584<br />**数値**:<br />-2147175036|{0}  |
> |**名前**:<br />BDK_E_TOKEN_EXPIRED<br />**16 進数**:<br />8004B585<br />**数値**:<br />-2147175035|{0}  |
> |**名前**:<br />BDK_E_TOKEN_NOT_VALID_FOR_OFFERING<br />**16 進数**:<br />8004B586<br />**数値**:<br />-2147175034|{0}  |
> |**名前**:<br />BDK_E_TOKEN_RANGE_BLACKLISTED<br />**16 進数**:<br />8004B587<br />**数値**:<br />-2147175033|{0}  |
> |**名前**:<br />BDK_E_TRANS_BALANCE_TO_PI_INVALID<br />**16 進数**:<br />8004B588<br />**数値**:<br />-2147175032|{0}  |
> |**名前**:<br />BDK_E_UNKNOWN_SERVER_FAILURE<br />**16 進数**:<br />8004B589<br />**数値**:<br />-2147175031|{0} 不明なサーバーの障害。|
> |**名前**:<br />BDK_E_UNSUPPORTED_CHAR_EXIST<br />**16 進数**:<br />8004B58A<br />**数値**:<br />-2147175030|{0}  |
> |**名前**:<br />BDK_E_USAGE_COUNT_FOR_TOKEN_EXCEEDED<br />**16 進数**:<br />8004B58F<br />**数値**:<br />-2147175025|{0} 請求トークンは既に使用されています。|
> |**名前**:<br />BDK_E_VATID_DOESNOTHAVEEXPDATE<br />**16 進数**:<br />8004B58B<br />**数値**:<br />-2147175029|{0}  |
> |**名前**:<br />BDK_E_ZIP_CITY_MISSING<br />**16 進数**:<br />8004B58C<br />**数値**:<br />-2147175028|{0}  |
> |**名前**:<br />BDK_E_ZIP_INVALID<br />**16 進数**:<br />8004B58D<br />**数値**:<br />-2147175027|{0} 請求先郵便番号エラー。|
> |**名前**:<br />BDK_E_ZIP_INVALID_FOR_ENTERED_STATE<br />**16 進数**:<br />8004B58E<br />**数値**:<br />-2147175026|{0} 請求先郵便番号エラー。|
> |**名前**:<br />BidsAuthenticationError<br />**16 進数**:<br />8005E003<br />**数値**:<br />-2147098621|サーバー {0} の認証中にエラーが発生しました。|
> |**名前**:<br />BidsAuthenticationFailed<br />**16 進数**:<br />8005E006<br />**数値**:<br />-2147098618|サーバー {0} に接続を試みると、認証に失敗しました。 ユーザー名またはパスワードが正しくありません。|
> |**名前**:<br />BidsInvalidConnectionString<br />**16 進数**:<br />8005E000<br />**数値**:<br />-2147098624|入力された接続文字列は無効です。 使用法: ServerUrl[;OrganizationName][;HomeRealmUrl]|
> |**名前**:<br />BidsInvalidUrl<br />**16 進数**:<br />8005E001<br />**数値**:<br />-2147098623|入力された URL {0} は無効です。|
> |**名前**:<br />BidsNoOrganizationsFound<br />**16 進数**:<br />8005E004<br />**数値**:<br />-2147098620|ユーザーに関する組織は見つかりませんでした。|
> |**名前**:<br />BidsOrganizationNotFound<br />**16 進数**:<br />8005E005<br />**数値**:<br />-2147098619|ユーザーに関する組織 {0} は見つかりませんでした。|
> |**名前**:<br />BidsServerConnectionFailed<br />**16 進数**:<br />8005E002<br />**数値**:<br />-2147098622|サーバー {0}に接続できませんでした。|
> |**名前**:<br />BillingNoSettingError<br />**16 進数**:<br />8004B531<br />**数値**:<br />-2147175119|請求アプリケーションの構成設定 [{0}] が見つかりませんでした。|
> |**名前**:<br />BillingPartnerCertificate<br />**16 進数**:<br />8004B530<br />**数値**:<br />-2147175120|請求に使用する正しいパートナー証明書を特定できませんでした。  発行者: {0}  件名: {1}  識別された一致: [{2}]  名前の一致: [{3}]  有効なすべての証明書: [{4}]。|
> |**名前**:<br />BillingRetrieveKeyError<br />**16 進数**:<br />8004B538<br />**数値**:<br />-2147175112|請求書のセッション キー: "{0}" を取得できませんでした|
> |**名前**:<br />BillingTestConnectionError<br />**16 進数**:<br />8004B532<br />**数値**:<br />-2147175118|請求書は使用できません: IsServiceAvailable を呼び出し 'False' を返しました。|
> |**名前**:<br />BillingTestConnectionException<br />**16 進数**:<br />8004B533<br />**数値**:<br />-2147175117|請求書 TestConnection の例外。|
> |**名前**:<br />BillingUnknownErrorCode<br />**16 進数**:<br />8004B536<br />**数値**:<br />-2147175114|請求エラー コード [{0}] は例外 {1} と共にスローされました|
> |**名前**:<br />BillingUnknownException<br />**16 進数**:<br />8004B537<br />**数値**:<br />-2147175113|請求エラーは例外 {0} と共にスローされました|
> |**名前**:<br />BillingUnmappedErrorCode<br />**16 進数**:<br />8004B535<br />**数値**:<br />-2147175115|請求エラー コード [{0}] は例外 {1} と共にスローされました|
> |**名前**:<br />BillingUserPuidNullError<br />**16 進数**:<br />8004B534<br />**数値**:<br />-2147175116|ユーザー Puid が必要ですが、null です。|
> |**名前**:<br />BookFirstInstanceFailed<br />**16 進数**:<br />8004E10E<br />**数値**:<br />-2147163890|最初のインスタンスを予約するのに失敗しました。|
> |**名前**:<br />BooleanOptionOutOfRange<br />**16 進数**:<br />8004431C<br />**数値**:<br />-2147204324|ブール値属性のオプションは、0 または 1 のどちらかの値である必要があります。|
> |**名前**:<br />BothConnectionSidesAreNeeded<br />**16 進数**:<br />80048218<br />**数値**:<br />-2147188200|このつながりの両側について、名前を入力するか、ロールを選択する必要があります。|
> |**名前**:<br />BPFEntityAlreadyExists<br />**16 進数**:<br />80060384<br />**数値**:<br />-2147089532|この名前の BPF エンティティが既に存在します。|
> |**名前**:<br />BpfEntityServiceIsNull<br />**16 進数**:<br />80060446<br />**数値**:<br />-2147089338|ビジネス プロセスの作成または更新時のエラー: BpfEntityService は Null にできません。|
> |**名前**:<br />BpfFactoryIsNull<br />**16 進数**:<br />80060447<br />**数値**:<br />-2147089337|ビジネス プロセスの作成または更新時のエラー: BpfFactory は Null にできません。|
> |**名前**:<br />BpfInstanceAlreadyExists<br />**16 進数**:<br />80060397<br />**数値**:<br />-2147089513|ターゲット レコードの業務プロセス フローは既に存在するため、作成できませんでした。 システム管理者にお問い合わせください。|
> |**名前**:<br />BpfVisitorIsNull<br />**16 進数**:<br />80060448<br />**数値**:<br />-2147089336|ビジネス プロセスの作成または更新時のエラー: BpfVisitor は Null にできません。|
> |**名前**:<br />BulkDeleteChildFailure<br />**16 進数**:<br />80048459<br />**数値**:<br />-2147187623|子ジョブの一括削除の 1 つに失敗しました。|
> |**名前**:<br />BulkDeleteRecordDeletionFailure<br />**16 進数**:<br />80048435<br />**数値**:<br />-2147187659|レコードを削除することはできません。|
> |**名前**:<br />BulkDetectInvalidEmailRecipient<br />**16 進数**:<br />80048422<br />**数値**:<br />-2147187678|その電子メール受信者は存在しないか、電子メール受信者の電子メールアドレスが無効です。|
> |**名前**:<br />BulkMailOperationFailed<br />**16 進数**:<br />8004502D<br />**数値**:<br />-2147200979|電子メール広告ジョブが完了しましたが {0} エラーがあります。 電子メール アドレスがない、または電子メールを送信するアクセス許可がないため、失敗が発生したかもしれません。 電子メール アドレスが見つからないレコードを確認するには、高度な検索を使用します。 電子メールのアクセス許可を増やす必要がある場合は、システム管理者に問い合わせてください。|
> |**名前**:<br />BulkMailServiceNotAccessible<br />**16 進数**:<br />80048304<br />**数値**:<br />-2147187964|Microsoft Dynamics 365 電子メール広告サービスが起動していません。|
> |**名前**:<br />BundleCannotContainBundle<br />**16 進数**:<br />8004F972<br />**数値**:<br />-2147157646|バンドルにバンドルを追加することはできません。|
> |**名前**:<br />BundleCannotContainProductFamily<br />**16 進数**:<br />8004F992<br />**数値**:<br />-2147157614|バンドルに製品ファミリを追加することはできません。|
> |**名前**:<br />BundleCannotContainProductKit<br />**16 進数**:<br />80061014<br />**数値**:<br />-2147086316|バンドルにセット製品を追加することはできません。|
> |**名前**:<br />BundleMaxPropertyLimitExceeded<br />**16 進数**:<br />8008100E<br />**数値**:<br />-2146955250|このバンドルはプロパティが多すぎるため公開できません。 該当組織のバンドルには、{0} 個を超えるプロパティを設定できません。|
> |**名前**:<br />BusinessManagementInvalidUserId<br />**16 進数**:<br />80041d1f<br />**数値**:<br />-2147214049|ユーザー ID [{0}] が無効です。|
> |**名前**:<br />BusinessManagementLoopBeingCreated<br />**16 進数**:<br />80041d21<br />**数値**:<br />-2147214047|この上位下位の関連付けを作成すると、事業階層にループが生成されます。|
> |**名前**:<br />BusinessManagementLoopExists<br />**16 進数**:<br />80041d20<br />**数値**:<br />-2147214048|事業階層にループが存在します。|
> |**名前**:<br />BusinessManagementObjectAlreadyExists<br />**16 進数**:<br />8004022a<br />**数値**:<br />-2147220950|特定の名前を持つオブジェクトは既に存在します。|
> |**名前**:<br />BusinessNotEnabled<br />**16 進数**:<br />8004032c<br />**数値**:<br />-2147220692|指定した部署は無効になっています。|
> |**名前**:<br />BusinessProcessFlowDefinitionOutdated<br />**16 進数**:<br />80060375<br />**数値**:<br />-2147089547|業務プロセス フローの定義がプロセス アクションと同期していないため、このアクションを完了できません。 業務プロセス フローを更新するには、Dynamics 365 システム管理者に連絡してください。|
> |**名前**:<br />BusinessProcessFlowMissingEntityErrorMessage<br />**16 進数**:<br />80060440<br />**数値**:<br />-2147089344|ビジネス プロセス '{0}' をインポートできませんでした。対応するビジネス プロセス エンティティ '{1}' がソリューションに含まれていません。|
> |**名前**:<br />BusinessProcessFlowStepHasInvalidParent<br />**16 進数**:<br />80060405<br />**数値**:<br />-2147089403|{0} 親はタイプが {1} ではありません|
> |**名前**:<br />BusinessRuleEditorSupportsOnlyIfConditionBranch<br />**16 進数**:<br />80060008<br />**数値**:<br />-2147090424|業務ルール エディターは If 条件を 1 つのみサポートします。 ルールを修正してください。|
> |**名前**:<br />BusinessUnitCannotBeDisabled<br />**16 進数**:<br />80041d59<br />**数値**:<br />-2147213991|部署を無効にできませんでした: システム管理者の役割を持つアクティブなユーザーが部署のサブツリーの外側に存在しません。|
> |**名前**:<br />BusinessUnitDefaultTeamOwnsRecords<br />**16 進数**:<br />80041d62<br />**数値**:<br />-2147213982|部署の既定のチームはレコードを所有します。 部署を削除することはできません。|
> |**名前**:<br />BusinessUnitHasChildAndCannotBeDeleted<br />**16 進数**:<br />80041d61<br />**数値**:<br />-2147213983|下位の部署を持つ部署は、削除することはできません。|
> |**名前**:<br />BusinessUnitIsNotDisabledAndCannotBeDeleted<br />**16 進数**:<br />80041d60<br />**数値**:<br />-2147213984|無効ではない部署を削除することはできません。|
> |**名前**:<br />BusinessUnitQueuesAssociatedWithBU<br />**16 進数**:<br />80072526<br />**数値**:<br />-2147015386|id = {1}、Name = {2} でこの BusinessUnit を参照するキューが {0} あります。 この部署を削除する前にキューを削除するか、別の部署に割り当ててください。|
> |**名前**:<br />CalculatedFieldsAssignmentMismatch<br />**16 進数**:<br />8006042b<br />**数値**:<br />-2147089365|{1} 型の {0} を {2} 型に設定することはできません。|
> |**名前**:<br />CalculatedFieldsCyclicReference<br />**16 進数**:<br />80060431<br />**数値**:<br />-2147089359|循環参照が作成されるために、計算フィールド {1} でフィールド {0} を使用できません。|
> |**名前**:<br />CalculatedFieldsDateOnlyBehaviorTypeMismatch<br />**16 進数**:<br />8006043a<br />**数値**:<br />-2147089350|フィールドの "日付のみ" の種類だけを使用できます。|
> |**名前**:<br />CalculatedFieldsDepthExceeded<br />**16 進数**:<br />80060432<br />**数値**:<br />-2147089358|{1} フィールドには既に深さ {2} の計算フィールド チェーンがあるために、{0} フィールドを作成または更新できません。|
> |**名前**:<br />CalculatedFieldsDivideByZero<br />**16 進数**:<br />8006042d<br />**数値**:<br />-2147089363|ゼロを評価する {0} で除算することはできません。|
> |**名前**:<br />CalculatedFieldsEntitiesExceeded<br />**16 進数**:<br />80060433<br />**数値**:<br />-2147089357|フィールド {1} には親レコードを使用する追加計算式が含まれるために、フィールド {0} を作成または更新できません。|
> |**名前**:<br />CalculatedFieldsFeatureNotEnabled<br />**16 進数**:<br />80060422<br />**数値**:<br />-2147089374|計算フィールド機能は使用できません|
> |**名前**:<br />CalculatedFieldsFunctionMismatch<br />**16 進数**:<br />8006042c<br />**数値**:<br />-2147089364|現在の関数で {1} 型の {0} は使用できません。|
> |**名前**:<br />CalculatedFieldsInvalidAttribute<br />**16 進数**:<br />80060428<br />**数値**:<br />-2147089368|{0} フィールドが存在しません。|
> |**名前**:<br />CalculatedFieldsInvalidAttributes<br />**16 進数**:<br />8006042e<br />**数値**:<br />-2147089362|計算式は、存在しない属性 {0} を参照しています。|
> |**名前**:<br />CalculatedFieldsInvalidEntity<br />**16 進数**:<br />80060423<br />**数値**:<br />-2147089373|計算式に無効な参照 {0} が含まれています。|
> |**名前**:<br />CalculatedFieldsInvalidFunction<br />**16 進数**:<br />80060427<br />**数値**:<br />-2147089369|{0} 関数が存在しません。|
> |**名前**:<br />CalculatedFieldsInvalidSourceTypeMask<br />**16 進数**:<br />80060438<br />**数値**:<br />-2147089352|この計算式は、定義が無効なフィールド {0} への参照を含んでいるため、保存できません。|
> |**名前**:<br />CalculatedFieldsInvalidValue<br />**16 進数**:<br />8006042f<br />**数値**:<br />-2147089361|計算式は、存在しない値を参照しています。|
> |**名前**:<br />CalculatedFieldsInvalidValues<br />**16 進数**:<br />80060430<br />**数値**:<br />-2147089360|計算式は、存在しない値 {0} を参照しています。|
> |**名前**:<br />CalculatedFieldsInvalidXaml<br />**16 進数**:<br />80060424<br />**数値**:<br />-2147089372|{0} フィールドの XAML 計算式の定義が無効です。|
> |**名前**:<br />CalculatedFieldsNonCalculatedFieldAssignment<br />**16 進数**:<br />80060425<br />**数値**:<br />-2147089371|計算式の定義を持つことができるのは、計算フィールドのみです。|
> |**名前**:<br />CalculatedFieldsPrimitiveOverflow<br />**16 進数**:<br />8006042a<br />**数値**:<br />-2147089366|値 {0} を種類 {1} に変換することはできません。|
> |**名前**:<br />CalculatedFieldsTimeInvBehaviorTypeMismatch<br />**16 進数**:<br />8006043b<br />**数値**:<br />-2147089349|フィールドの "タイム ゾーン非依存の日時" の種類だけを使用できます。|
> |**名前**:<br />CalculatedFieldsTypeMismatch<br />**16 進数**:<br />80060426<br />**数値**:<br />-2147089370|現在の演算子で {1} 型の {0} は使用できません。|
> |**名前**:<br />CalculatedFieldsUserLocBehaviorTypeMismatch<br />**16 進数**:<br />8006043c<br />**数値**:<br />-2147089348|フィールドの "ユーザー ローカルの日時" の種類だけを使用できます。|
> |**名前**:<br />CalculatedFieldUsedInRollupFieldCannotBeComplex<br />**16 進数**:<br />80060550<br />**数値**:<br />-2147089072|1 つまたは複数のロールアップ フィールドはこの計算フィールドに依存します。 この計算フィールドでは、ロールアップ フィールド、ロールアップ フィールドを使っている別の計算フィールドまたは関連エンティティのフィールドを使うことはできません。|
> |**名前**:<br />CalculateNowOverflowError<br />**16 進数**:<br />80060558<br />**数値**:<br />-2147089064|オーバフロー エラーにより計算が失敗しました。|
> |**名前**:<br />CallerCannotChangeOwnDomainName<br />**16 進数**:<br />80044161<br />**数値**:<br />-2147204767|呼び出し元は独自のドメイン名を変更できません|
> |**名前**:<br />CalloutException<br />**16 進数**:<br />8004025b<br />**数値**:<br />-2147220901|コールアウト例外が発生しました。|
> |**名前**:<br />CampaignActivityAlreadyPropagated<br />**16 進数**:<br />80040326<br />**数値**:<br />-2147220698|このキャンペーン活動は既に配布されています。 キャンペーン活動は、複数回配布することはできません。|
> |**名前**:<br />CampaignActivityClosed<br />**16 進数**:<br />80040331<br />**数値**:<br />-2147220687|このキャンペーン活動はクローズされたか、取り消されました。 クローズされたか取り消されたキャンペーン活動は配布できません。|
> |**名前**:<br />CampaignNotSpecifiedForCampaignActivity<br />**16 進数**:<br />80040309<br />**数値**:<br />-2147220727|RegardingObjectId は必須フィールドです。|
> |**名前**:<br />CampaignNotSpecifiedForCampaignResponse<br />**16 進数**:<br />8004030a<br />**数値**:<br />-2147220726|RegardingObjectId は必須フィールドです。|
> |**名前**:<br />CanAssociateOnlyMobileOfflineEnabledEntityToProfileItem<br />**16 進数**:<br />8006099E<br />**数値**:<br />-2147087970|{0} は Mobile Offline に対して有効にする必要があります。|
> |**名前**:<br />CanAssociateOnlyMobileOfflineEnableEntityToProfileItem<br />**16 進数**:<br />8006099C<br />**数値**:<br />-2147087972|このエンティティで Mobile Offline を有効にする必要があります。|
> |**名前**:<br />CanAssociateOnlyOneEntityPerProfileItem<br />**16 進数**:<br />8006099D<br />**数値**:<br />-2147087971|Mobile Offline プロファイル レコードには、エンティティごとに 1 つの Mobile Offline プロファイル アイテム レコードのみ追加できます。 |
> |**名前**:<br />CancelActiveChildCaseFirst<br />**16 進数**:<br />8003F451<br />**数値**:<br />-2147224495|親サポート案件を取り消す前に、アクティブな子サポート案件をキャンセルしてください。|
> |**名前**:<br />CannotAcceptEmail<br />**16 進数**:<br />8005E20B<br />**数値**:<br />-2147098101|送信しようとする電子メールは Microsoft Dynamics 365 で受理できません。 理由コード: {0}。|
> |**名前**:<br />CannotAccessExchangeOptinStatus<br />**16 進数**:<br />80071110<br />**数値**:<br />-2147020528|Exchange optin の状態にアクセスできません。|
> |**名前**:<br />CannotActivateMailboxForDisabledUserOrQueue<br />**16 進数**:<br />8005E230<br />**数値**:<br />-2147098064|メールボックスに関連付けられているユーザーまたはキューが無効の状態であるため、メールボックスをアクティブ化できません。 メールボックスはアクティブなユーザー/キューに対してのみアクティブ化することができます。|
> |**名前**:<br />CannotActivateRecord<br />**16 進数**:<br />80081017<br />**数値**:<br />-2146955241|廃止された製品ファミリ、またはバンドルは追加できません。 さらに製品ファミリの一部である廃止された製品をアクティブ化することはできません。|
> |**名前**:<br />CannotActOnBehalfOfAnotherUser<br />**16 進数**:<br />8004A110<br />**数値**:<br />-2147180272|ユーザーには別のユーザーの代わりに操作する特権がありません。|
> |**名前**:<br />CannotActOnBehalfOfExternalParty<br />**16 進数**:<br />80061116<br />**数値**:<br />-2147086058|ユーザーには外部パーティの代わりに操作する特権がありません。|
> |**名前**:<br />CannotAddActivityPartyEntityToMobileOfflineProfileItem<br />**16 進数**:<br />800609AD<br />**数値**:<br />-2147087955|Mobile Offline プロファイル項目に ActivityParty エンティティを追加できません。このエンティティはアクティビティ エンティティがプロファイルに追加されると自動的に追加されます。|
> |**名前**:<br />CannotAddBundleToItself<br />**16 進数**:<br />80061031<br />**数値**:<br />-2147086287|バンドルにそれ自体を追加することはできません。|
> |**名前**:<br />CannotAddBundleToPricelist<br />**16 進数**:<br />80061007<br />**数値**:<br />-2147086329|バンドル製品 {1} が価格表に記載されていないため、バンドル {0} を価格表に追加できません。|
> |**名前**:<br />CannotAddBusinessDataLocalizedLabelEntityToMobileOfflineProfileItem<br />**16 進数**:<br />800609AC<br />**数値**:<br />-2147087956|Mobile Offline プロファイル項目に BusinessDataLocalizedLabel エンティティを追加できません。このエンティティは Product エンティティがプロファイルに追加されると自動的に追加されます。|
> |**名前**:<br />CannotAddDraftFamilyProductBundleToCases<br />**16 進数**:<br />8004F984<br />**数値**:<br />-2147157628|製品ファミリ、ドラフト製品、ドラフト バンドルは追加できません。|
> |**名前**:<br />CannotAddIntersectEntityToMobileOfflineProfileItem<br />**16 進数**:<br />800609AB<br />**数値**:<br />-2147087957|Mobile Offline プロファイル項目に交差エンティティを追加できません。エンティティは親エンティティがプロファイルに追加されると自動的に追加されます。|
> |**名前**:<br />CannotAddKitToItself<br />**16 進数**:<br />80061032<br />**数値**:<br />-2147086286|セット製品にそれ自体を追加することはできません。|
> |**名前**:<br />CannotAddMembersToDefaultTeam<br />**16 進数**:<br />8004830B<br />**数値**:<br />-2147187957|既定の部署チームにメンバーを追加することはできません。|
> |**名前**:<br />CannotAddNewBooleanValue<br />**16 進数**:<br />8004431D<br />**数値**:<br />-2147204323|ブール値属性にオプションを追加することはできません。|
> |**名前**:<br />CannotAddNewStateValue<br />**16 進数**:<br />8004431E<br />**数値**:<br />-2147204322|状態属性に状態オプションを追加することはできません。|
> |**名前**:<br />CannotAddNonCustomizableComponent<br />**16 進数**:<br />8004F015<br />**数値**:<br />-2147160043|カスタマイズできないため、コンポーネントは {0} {1} 追加できません|
> |**名前**:<br />CannotAddOrActonBehalfAnotherUserPrivilege<br />**16 進数**:<br />8004Ed43<br />**数値**:<br />-2147160765|"別のユーザーの代わりに操作します" 特権は、追加または削除することはできません。|
> |**名前**:<br />CannotAddParentToAKit<br />**16 進数**:<br />80061015<br />**数値**:<br />-2147086315|セット製品の親レコードを指定することはできません。|
> |**名前**:<br />CannotAddPricelistToProductFamily<br />**16 進数**:<br />8004F902<br />**数値**:<br />-2147157758|価格表に製品ファミリを追加することはできません。|
> |**名前**:<br />CannotAddProduct<br />**16 進数**:<br />8004F908<br />**数値**:<br />-2147157752|アクティブな製品のみを追加できます。|
> |**名前**:<br />CannotAddProductBundleToKit<br />**16 進数**:<br />80061022<br />**数値**:<br />-2147086302|セット製品にバンドルを追加することはできません。|
> |**名前**:<br />CannotAddProductFamilyToKit<br />**16 進数**:<br />80061023<br />**数値**:<br />-2147086301|セット製品に製品ファミリを追加することはできません。|
> |**名前**:<br />CannotAddProductToBundle<br />**16 進数**:<br />8004F976<br />**数値**:<br />-2147157642|このバンドルに製品を追加することはできません。このバンドルの {0} の制限に達しました。|
> |**名前**:<br />CannotAddProductToKit<br />**16 進数**:<br />80061024<br />**数値**:<br />-2147086300|製品ファミリに属する製品をセット製品に追加することはできません。|
> |**名前**:<br />CannotAddProductToRetiredKit<br />**16 進数**:<br />80061026<br />**数値**:<br />-2147086298|廃止されたセット製品に製品を追加することはできません。|
> |**名前**:<br />CannotAddQueueItemsToInactiveQueue<br />**16 進数**:<br />80040522<br />**数値**:<br />-2147220190|選択したユーザーには、このキューのアイテムを処理するための権限がありません。|
> |**名前**:<br />CannotAddRetiredProduct<br />**16 進数**:<br />80061033<br />**数値**:<br />-2147086285|廃止製品との製品リレーションシップを作成することはできません。|
> |**名前**:<br />CannotAddRetiredProductToKit<br />**16 進数**:<br />80061027<br />**数値**:<br />-2147086297|廃止された製品をセット製品に追加することはできません。|
> |**名前**:<br />CannotAddRetiredProductToPricelist<br />**16 進数**:<br />80061009<br />**数値**:<br />-2147086327|廃止された製品を価格表に追加することはできません。|
> |**名前**:<br />CannotAddSingleQueueEnabledEntityToQueue<br />**16 進数**:<br />8004051c<br />**数値**:<br />-2147220196|既に別のキューに存在しているため、キューにエンティティ レコードを追加することはできません。|
> |**名前**:<br />CannotAddSolutionComponentWithoutRoots <br />**16 進数**:<br />8004F018<br />**数値**:<br />-2147160040|この項目は有効なソリューション コンポーネントではありません。 ソリューション コンポーネントの詳細については、Microsoft Dynamics 365 SDK のドキュメントを参照してください。|
> |**名前**:<br />CannotAddUserToMobileOfflineProfile<br />**16 進数**:<br />800609A6<br />**数値**:<br />-2147087962|ユーザーのロールが設定されていないか、Dynamics 365 モバイル用特権がロールに関連付けられていないため、このユーザーをこの Mobile Offline プロファイルに追加することはできません。|
> |**名前**:<br />CannotAddWorkflowActivationToSolution <br />**16 進数**:<br />8004F00C<br />**数値**:<br />-2147160052|ソリューションには、ワークフローのアクティブ化を追加できません |
> |**名前**:<br />CannotAssignAddressBookFilters<br />**16 進数**:<br />80048448<br />**数値**:<br />-2147187640|アドレス帳のフィルターを割り当てることはできません|
> |**名前**:<br />CannotAssignOfflineFilters<br />**16 進数**:<br />800404ff<br />**数値**:<br />-2147220225|オフライン フィルターを割り当てることはできません|
> |**名前**:<br />CannotAssignOutlookFilters<br />**16 進数**:<br />80040264<br />**数値**:<br />-2147220892|Outlook フィルターを割り当てることはできません|
> |**名前**:<br />CannotAssignRolesOrProfilesToAccessTeam<br />**16 進数**:<br />80048331<br />**数値**:<br />-2147187919|アクセス チームにロールまたはプロファイルを割り当てることはできません。|
> |**名前**:<br />CannotAssignRolesToSupportUser<br />**16 進数**:<br />80041d51<br />**数値**:<br />-2147213999|サポート ユーザーは読み取り専用で、他のロールを割り当てることはできません|
> |**名前**:<br />CannotAssignSupportUser<br />**16 進数**:<br />80041d44<br />**数値**:<br />-2147214012|サポート ユーザー ロールをユーザーに割り当てることはできません。|
> |**名前**:<br />CannotAssignToAccessTeam<br />**16 進数**:<br />80048340<br />**数値**:<br />-2147187904|レコードをアクセス チームに割り当てることができません。 レコードを所有者チームに割り当てることができます。|
> |**名前**:<br />CannotAssignToDisabledBusiness<br />**16 進数**:<br />8004032d<br />**数値**:<br />-2147220691|指定された部署は無効になっているため、割り当てることができません。|
> |**名前**:<br />CannotAssociateExternalPartyItem<br />**16 進数**:<br />80061117<br />**数値**:<br />-2147086057|外部パーティとして有効化されているエンティティ レコードに、複数の外部パーティ アイテムを関連付けることはできません。|
> |**名前**:<br />CannotAssociateInactiveItemToCampaign<br />**16 進数**:<br />80040304<br />**数値**:<br />-2147220732|非アクティブな項目をキャンペーンに関連付けることはできません。|
> |**名前**:<br />CannotAssociateInvalidEntityToProfileItem<br />**16 進数**:<br />8006099B<br />**数値**:<br />-2147087973|オブジェクトの種類コードが無効です。|
> |**名前**:<br />CannotAssociateProductFamily<br />**16 進数**:<br />8004F999<br />**数値**:<br />-2147157607|製品ファミリとの関係を作成することはできません。|
> |**名前**:<br />CannotAssociateRetiredBundles<br />**16 進数**:<br />80081011<br />**数値**:<br />-2146955247|廃止バンドルとの製品関係を作成することはできません。|
> |**名前**:<br />CannotAssociateRetiredProducts<br />**16 進数**:<br />8004F974<br />**数値**:<br />-2147157644|廃止製品との製品関係を作成することはできません。|
> |**名前**:<br />CannotBindToSession<br />**16 進数**:<br />80040254<br />**数値**:<br />-2147220908|別のセッション、既にバインドされているセッションにバインドすることはできません。|
> |**名前**:<br />CannotCancelInvoice<br />**16 進数**:<br />80100001<br />**数値**:<br />-2146435071|請求書は、アクティブまたは支払い済みの状態でないためキャンセルできません。|
> |**名前**:<br />CannotChangeAccessModeForInternetMarketingUser<br />**16 進数**:<br />80045035<br />**数値**:<br />-2147200971|インターネット マーケティング ユーザーはシステム ユーザーです。 アクセス モードを変更できません。|
> |**名前**:<br />CannotChangeAttributeRequiredLevel<br />**16 進数**:<br />8004D293<br />**数値**:<br />-2147167597|レベルを必要とする属性は、SystemRequired から変更できません|
> |**名前**:<br />CannotChangeConvertRuleState<br />**16 進数**:<br />800608F4<br />**数値**:<br />-2147088140|[変換ルール] のアクティブ化中にエラーが発生しました。ワークフローで特権の確認をしてもう一度やり直すか、システム管理者にお問い合わせください。|
> |**名前**:<br />CannotChangeDaysSinceRecordLastModified<br />**16 進数**:<br />800609A4<br />**数値**:<br />-2147087964|レコードが最後に修正されてからの日数を設定または変更するには、このエンティティで Mobile Offline を有効にする必要があります。|
> |**名前**:<br />CannotChangeInvitationStatusForInternetMarketingUser<br />**16 進数**:<br />80045036<br />**数値**:<br />-2147200970|インターネット マーケティング ユーザーはシステム ユーザーです。 招待の状態を変更することはできません。|
> |**名前**:<br />CannotChangeProductRelationship<br />**16 進数**:<br />80061013<br />**数値**:<br />-2147086317|廃止製品の製品リレーションシップを追加または変更することはできません。|
> |**名前**:<br />CannotChangeSelectedBundleToAnotherValue<br />**16 進数**:<br />8004F986<br />**数値**:<br />-2147157626|バンドルが既存の製品として選択されている場合は、そのバンドルを別の値に変更することはできません。|
> |**名前**:<br />CannotChangeSelectedProductWithBundle<br />**16 進数**:<br />8004F987<br />**数値**:<br />-2147157625|製品が既存の製品として選択されている場合は、その製品をバンドルに変更することはできません。|
> |**名前**:<br />CannotChangeState<br />**16 進数**:<br />8004F863<br />**数値**:<br />-2147157917|[SLA] のアクティブ化中にエラーが発生しました。ワークフローで特権の確認をしてもう一度やり直すか、システム管理者にお問い合わせください。|
> |**名前**:<br />CannotChangeStateOfNonpublicView<br />**16 進数**:<br />80040279<br />**数値**:<br />-2147220871|非アクティブ化、およびアクティブ化できるのは、共有ビューのみです。|
> |**名前**:<br />CannotChangeTeamTypeDueToOwnership<br />**16 進数**:<br />80048337<br />**数値**:<br />-2147187913|チームが所有するレコードがあるため、チームの種類を変更できません。|
> |**名前**:<br />CannotChangeTeamTypeDueToRoleOrProfile<br />**16 進数**:<br />80048336<br />**数値**:<br />-2147187914|チームにセキュリティ ロールまたはフィールド セキュリティ プロファイルが割り当てられているため、チームの種類を変更できません。|
> |**名前**:<br />CannotClearChannelPropertyGroupFromConvertRule<br />**16 進数**:<br />800608ED<br />**数値**:<br />-2147088147|チャネル プロパティ グループが 1 つ以上のステップで使用されています。 ルールを保存またはアクティブ化する前に、レコードを使用する条件とステップからプロパティを削除します。|
> |**名前**:<br />CannotCloneBundleAsProductLimitExceeded<br />**16 進数**:<br />8004F985<br />**数値**:<br />-2147157627|この新しいバンドルは、バンドルに含めることができる許容数 {0} を超える製品を含んでいるため、作成できません。|
> |**名前**:<br />CannotCloneBundleWithRetiredProducts<br />**16 進数**:<br />80061034<br />**数値**:<br />-2147086284|廃止された製品を含むバンドルを複製することはできません。|
> |**名前**:<br />CannotCloneProductKit<br />**16 進数**:<br />80061020<br />**数値**:<br />-2147086304|セット製品を複製することはできません。|
> |**名前**:<br />CannotCloseCase<br />**16 進数**:<br />8004F456<br />**数値**:<br />-2147158954|この操作を完了できません。 サポート案件に対して定義されている状態の移行ルールにより、1 つ以上の子サポート案件をクローズすることができません。|
> |**名前**:<br />CannotConnectToSelf<br />**16 進数**:<br />80048217<br />**数値**:<br />-2147188201|レコードをそれ自身に接続することはできません。|
> |**名前**:<br />CannotConvertBundleToKit<br />**16 進数**:<br />80061030<br />**数値**:<br />-2147086288|バンドルをセット製品に変換することはできません。|
> |**名前**:<br />CannotConvertProductAssociatedWithBundleToKit<br />**16 進数**:<br />80061018<br />**数値**:<br />-2147086312|バンドルの一部である製品をセット製品に変換することはできません。|
> |**名前**:<br />CannotConvertProductAssociatedWithFamilyToKit<br />**16 進数**:<br />80061016<br />**数値**:<br />-2147086314|製品ファミリに属する製品をセット製品に変換することはできません。|
> |**名前**:<br />CannotConvertProductFamilyToKit<br />**16 進数**:<br />80061029<br />**数値**:<br />-2147086295|製品ファミリをセット製品に変換することはできません。|
> |**名前**:<br />CannotCopyIncompatibleListType<br />**16 進数**:<br />80040306<br />**数値**:<br />-2147220730|異なる種類のリストをコピーすることはできません。|
> |**名前**:<br />CannotCopyStaticList<br />**16 進数**:<br />8004F704<br />**数値**:<br />-2147158268|この操作は動的リストに対してのみ有効です。|
> |**名前**:<br />CannotCreateActivityRelationship<br />**16 進数**:<br />80047006<br />**数値**:<br />-2147192826|活動との関連付けは、この操作では作成できません。|
> |**名前**:<br />CannotCreateAddressBookFilters<br />**16 進数**:<br />80048447<br />**数値**:<br />-2147187641|アドレス帳のフィルターを作成することはできません|
> |**名前**:<br />CannotCreateCase<br />**16 進数**:<br />80060853<br />**数値**:<br />-2147088301|このサポート案件を既定の権利として作成することはできません。指定された顧客に残りの時間がありません。|
> |**名前**:<br />CannotCreateComponentDefinition<br />**16 進数**:<br />80072001<br />**数値**:<br />-2147016703|新しいコンポーネント定義の作成はサポートされていません|
> |**名前**:<br />CannotCreateExternalPartyWithSameCorrelationKey<br />**16 進数**:<br />80061112<br />**数値**:<br />-2147086062|同じ関連付けキー値を持つ外部パーティ レコードが既に存在します。|
> |**名前**:<br />CannotCreateFromSupportUser<br />**16 進数**:<br />80041d46<br />**数値**:<br />-2147214010|サポート ユーザー ロールからのロールを作成することはできません。|
> |**名前**:<br />CannotCreateKitOfTypeFamilyOrBundle<br />**16 進数**:<br />80061012<br />**数値**:<br />-2147086318|種類がバンドルまたは製品ファミリであるセット製品は作成できません。|
> |**名前**:<br />CannotCreateOrEnablePositionDueToParentPositionIsDisabled<br />**16 進数**:<br />80048344<br />**数値**:<br />-2147187900|親ポジションが無効になっている場合は、子ポジションを作成したり有効にしたりすることはできません。|
> |**名前**:<br />CannotCreateOutlookFilters<br />**16 進数**:<br />80040263<br />**数値**:<br />-2147220893|Outlook フィルターを作成することはできません|
> |**名前**:<br />CannotCreatePluginInstance<br />**16 進数**:<br />8004A201<br />**数値**:<br />-2147180031|プラグインのインスタンスを作成できません。 プラグインの種類の定義が抽象になっていないことと、Dynamics 365 SDK でサポートされているパブリック コンストラクターを持っていることを確認します。|
> |**名前**:<br />CannotCreatePropertyOptionSetItem<br />**16 進数**:<br />80081013<br />**数値**:<br />-2146955245|データの種類がオプション セットに設定されているプロパティを参照するプロパティのオプション セット項目レコードのみを作成できます。|
> |**名前**:<br />CannotCreateQueueItemInactiveObject<br />**16 進数**:<br />8004051e<br />**数値**:<br />-2147220194|非アクティブ化されたオブジェクトを、キューに追加することはできません。|
> |**名前**:<br />CannotCreateResponseForTemplate<br />**16 進数**:<br />80040312<br />**数値**:<br />-2147220718|テンプレート キャンペーンに対して CampaignResponse を作成できません。|
> |**名前**:<br />CannotCreateSLAForEntity<br />**16 進数**:<br />80055005<br />**数値**:<br />-2147135483|サービス レベル アグリーメント (SLA) の作成が有効になっていないため、このエンティティでは SLA を作成できません|
> |**名前**:<br />CannotCreateSyncUserIsLicensedField<br />**16 進数**:<br />80041d4d<br />**数値**:<br />-2147214003|プロパティ IsLicensed は同期ユーザー作成に対して設定することはできません。|
> |**名前**:<br />CannotCreateSyncUserObjectMissing<br />**16 進数**:<br />80041d4b<br />**数値**:<br />-2147214005|これは、この組織に有効な Microsoft Online Services ID ではありません。|
> |**名前**:<br />CannotCreateSystemOrDefaultTheme<br />**16 進数**:<br />800608D5<br />**数値**:<br />-2147088171|システム テーマまたは既定のテーマを作成できません。 システム テーマまたは既定のテーマは組み込みでのみ作成できます。|
> |**名前**:<br />CannotCreateUpdateSourceAttribute<br />**16 進数**:<br />80044804<br />**数値**:<br />-2147203068|指標の種類が件数の場合、ソース属性の作成/更新は無効です。|
> |**名前**:<br />CannotDeactivateDefaultView<br />**16 進数**:<br />8004027a<br />**数値**:<br />-2147220870|既定のビューは非アクティブ化できません。|
> |**名前**:<br />CannotDeactivateGuestProfile<br />**16 進数**:<br />80061105<br />**数値**:<br />-2147086075|このゲスト チャネル アクセス プロファイルは非アクティブとして設定できません。|
> |**名前**:<br />CannotDefineMultipleValuesOnOwnerFieldInProfileItemEntityFilter<br />**16 進数**:<br />80071129<br />**数値**:<br />-2147020503|このフィールドに複数の値を定義できません。|
> |**名前**:<br />CannotDeleteActiveCaseCreationRule<br />**16 進数**:<br />8004F880<br />**数値**:<br />-2147157888|アクティブな規則を削除することはできません。 レコード作成および更新ルールを非アクティブ化​​してから削除してください。|
> |**名前**:<br />CannotDeleteActiveRecordCreationRuleItem<br />**16 進数**:<br />8004F894<br />**数値**:<br />-2147157868|アクティブなレコード作成のルール アイテムは削除できません。 レコード作成ルールを非アクティブ化​​してから削除してください。|
> |**名前**:<br />CannotDeleteActiveRule<br />**16 進数**:<br />8004F850<br />**数値**:<br />-2147157936|アクティブなルーティング規則を削除することはできません。 ルールを非アクティブ化して削除してください。|
> |**名前**:<br />CannotDeleteActiveSla<br />**16 進数**:<br />8004F870<br />**数値**:<br />-2147157904|アクティブな SLA を削除することはできません。 SLA を非アクティブ化してから削除してください。|
> |**名前**:<br />CannotDeleteAppModuleAdministration<br />**16 進数**:<br />80050130<br />**数値**:<br />-2147155664|このアプリを削除できません。|
> |**名前**:<br />CannotDeleteAppModuleClientType<br />**16 進数**:<br />80050129<br />**数値**:<br />-2147155671|このアプリを削除できません。|
> |**名前**:<br />CannotDeleteAsBackgroundOperationInProgress<br />**16 進数**:<br />8004032b<br />**数値**:<br />-2147220693|このレコードは Microsoft Dynamics 365 で現在使用されているため、削除できません。 後でもう一度試してみてください。 この問題が解決しない場合は、システム管理者にお問い合わせください。|
> |**名前**:<br />CannotDeleteAsItIsReadOnly<br />**16 進数**:<br />80040228<br />**数値**:<br />-2147220952|このオブジェクトは読み取り専用なので、削除できません。|
> |**名前**:<br />CannotDeleteAttributeUsedInWorkflow<br />**16 進数**:<br />80045030<br />**数値**:<br />-2147200976|この属性は 1 つ以上のワークフローで使用されており、削除できません。 この属性を使用するワークフローのシステム ジョブをキャンセル​​し、属性を使用するワークフローを削除または変更し、属性を再び削除するよう試みます。|
> |**名前**:<br />CannotDeleteBaseMoneyCalculationAttribute<br />**16 進数**:<br />80048cfe<br />**数値**:<br />-2147185410|基本の通貨計算属性の削除は無効です。|
> |**名前**:<br />CannotDeleteCannedView<br />**16 進数**:<br />8004022f<br />**数値**:<br />-2147220945|システム定義ビューは削除できません。|
> |**名前**:<br />CannotDeleteCDSUser<br />**16 進数**:<br />80041d5a<br />**数値**:<br />-2147213990|Common Data Service ユーザーのロールは削除できません。|
> |**名前**:<br />CannotDeleteChannelAccessProfileRule<br />**16 進数**:<br />80061108<br />**数値**:<br />-2147086072|アクティブなチャネル アクセス プロファイル ルールを削除することはできません。 ルールを非アクティブ化してから削除してください。|
> |**名前**:<br />CannotDeleteChannelProperty<br />**16 進数**:<br />800608EB<br />**数値**:<br />-2147088149|変換ルールで参照されているチャネル プロパティを削除することはできません。|
> |**名前**:<br />CannotDeleteChildAttribute<br />**16 進数**:<br />80047016<br />**数値**:<br />-2147192810|子属性の削除は無効です。|
> |**名前**:<br />CannotDeleteCustomEntityUsedInWorkflow<br />**16 進数**:<br />8004502C<br />**数値**:<br />-2147200980|ワークフローで使用されるエンティティは削除できません。|
> |**名前**:<br />CannotDeleteDefaultProfile<br />**16 進数**:<br />8006099A<br />**数値**:<br />-2147087974|このプロファイルを削除するには、最初に、既定の Mobile Offline プロファイルではなくなるように設定する必要があります。|
> |**名前**:<br />CannotDeleteDefaultStatusOption<br />**16 進数**:<br />80044341<br />**数値**:<br />-2147204287|既定の状態オプションを削除することはできません。|
> |**名前**:<br />CannotDeleteDefaultTeam<br />**16 進数**:<br />80048307<br />**数値**:<br />-2147187961|既定の部署チームは削除できません。|
> |**名前**:<br />CannotDeleteDueToAssociation<br />**16 進数**:<br />80040227<br />**数値**:<br />-2147220953|削除しようとするオブジェクトは、別のオブジェクトに関連付けられ、削除することはできません。|
> |**名前**:<br />CannotDeleteDueToBasketEntityAssociation<br />**16 進数**:<br />80061612<br />**数値**:<br />-2147084782|対応するバスケット エンティティが存在する場合は、推奨事項エンティティは削除できません。|
> |**名前**:<br />CannotDeleteDynamicPropertyInRetiredState<br />**16 進数**:<br />8004F892<br />**数値**:<br />-2147157870|廃止された製品のプロパティを削除することはできません。|
> |**名前**:<br />CannotDeleteDynamicPropertyInUse<br />**16 進数**:<br />80081003<br />**数値**:<br />-2146955261|トランザクションに使用している廃止されたプロパティは削除できません。|
> |**名前**:<br />CannotDeleteEnumOptionsFromAttributeType<br />**16 進数**:<br />80044323<br />**数値**:<br />-2147204317|候補リスト、および状態属性からのみオプションを削除できます。|
> |**名前**:<br />CannotDeleteGuestProfile<br />**16 進数**:<br />80061104<br />**数値**:<br />-2147086076|このゲスト チャネル アクセス プロファイルは削除できません。|
> |**名前**:<br />CannotDeleteInheritedDynamicProperty<br />**16 進数**:<br />80081014<br />**数値**:<br />-2146955244|製品ファミリから継承されるプロパティを削除することはできません。|
> |**名前**:<br />CannotDeleteInUseAttribute<br />**16 進数**:<br />80048418<br />**数値**:<br />-2147187688|選択された属性は、現在発行中の 1 つまたは複数の重複データ検出ルールで参照されているため、削除できません。|
> |**名前**:<br />CannotDeleteInUseComponent<br />**16 進数**:<br />8004F01F<br />**数値**:<br />-2147160033|{0}({1}) コンポーネントは他のコンポーネント {2} によって参照されているため削除できません。 参照されているコンポーネントの一覧については、RetrieveDependenciesForDeleteRequest を使用してください。|
> |**名前**:<br />CannotDeleteInUseEntity<br />**16 進数**:<br />80048420<br />**数値**:<br />-2147187680|選択したエンティティは、現在公開処理中の 1 つまたは複数の重複データ検出ルールで参照されているため、削除できません。|
> |**名前**:<br />CannotDeleteInUseOptionSet<br />**16 進数**:<br />80048417<br />**数値**:<br />-2147187689|このオプション セットは削除できません。 このオプション セットを参照するエンティティの現在のセットは次のとおりです: {0}。 このオプション セットを削除する前にこれらの参照が削除される必要があります|
> |**名前**:<br />CannotDeleteLastEmailAttribute<br />**16 進数**:<br />80046FFF<br />**数値**:<br />-2147192833|レコードの種類が電子メールに対して有効になっているため、このフィールドは削除できません。|
> |**名前**:<br />CannotDeleteMetadata<br />**16 進数**:<br />8004F032<br />**数値**:<br />-2147160014|現在のコンポーネント (名前='{0}', id='{1}') の操作 '{2}' は、マネージド プロパティの次の条件の評価中に失敗しました: '{3}'|
> |**名前**:<br />CannotDeleteMetricWithGoals<br />**16 進数**:<br />80044800<br />**数値**:<br />-2147203072|この目標指標は 1 つ以上の目標で使用されており、削除できません。|
> |**名前**:<br />CannotDeleteNonLeafNode<br />**16 進数**:<br />8004F200<br />**数値**:<br />-2147159552|リーフに関する声明のみ削除できます。 この文は他の幾つかの文の上位にあります。|
> |**名前**:<br />CannotDeleteNotOwnedDynamicProperty<br />**16 進数**:<br />80081006<br />**数値**:<br />-2146955258|製品ファミリから継承される動的プロパティを削除することはできません。|
> |**名前**:<br />CannotDeleteOneNoteTableOfContent<br />**16 進数**:<br />800608B7<br />**数値**:<br />-2147088201|このファイルには OneNote ノートブック セクションへのリンクが含まれているため削除できません。 ノートブックの内容を削除するには、OneNote でノートブックを開き内容を削除してください。 ノートブックを削除するには、SharePoint を開きノートブックを削除してください。|
> |**名前**:<br />CannotDeleteOnlineRecord<br />**16 進数**:<br />8005F248<br />**数値**:<br />-2147093944|このレコードは、オフライン モードでは存在しないため削除できません。|
> |**名前**:<br />CannotDeleteOptionSet<br />**16 進数**:<br />80048404<br />**数値**:<br />-2147187708|選択した OptionSet を削除できません|
> |**名前**:<br />CannotDeleteOrCancelSystemJobs<br />**16 進数**:<br />80044F02<br />**数値**:<br />-2147201278|このシステム ジョブはシステムに必要なため、取り消しまたは削除できません。 このジョブは、一時停止、再開、または延期することしかできません。|
> |**名前**:<br />CannotDeleteOverriddenProperty<br />**16 進数**:<br />80081100<br />**数値**:<br />-2146955008|このプロパティは、1 つ以上の子レコードに対して上書きされているため、削除できません。 プロパティの上書きされたバージョンを削除してから、製品ファミリ階層を再公開し、このプロパティを削除してください。|
> |**名前**:<br />CannotDeletePartnerSolutionWithOrganizations<br />**16 進数**:<br />8004A10e<br />**数値**:<br />-2147180274|パートナー ソリューションを、それに関連付けられる 1 つ以上の組織として削除することはできません|
> |**名前**:<br />CannotDeletePartnerWithPartnerSolutions<br />**16 進数**:<br />8004A10d<br />**数値**:<br />-2147180275|パートナーを、それに関連付けられる 1 つ以上のソリューションとして削除することはできません|
> |**名前**:<br />CannotDeletePrimaryUIAttribute<br />**16 進数**:<br />80047002<br />**数値**:<br />-2147192830|プライマリ UI の属性の削除は無効です。|
> |**名前**:<br />CannotDeleteProductFromActiveBundle<br />**16 進数**:<br />80061010<br />**数値**:<br />-2147086320|アクティブな製品または改訂中の製品はバンドルから削除できません。|
> |**名前**:<br />CannotDeleteProductStatusCode<br />**16 進数**:<br />80081016<br />**数値**:<br />-2146955242|システムによって生成されたステータスは削除できません。|
> |**名前**:<br />CannotDeleteProfileWithExternalPartyItem<br />**16 進数**:<br />80061107<br />**数値**:<br />-2147086073|このチャネル アクセス プロファイルは、外部パーティ アイテムに関連付けられているため削除できません。 関連付けを削除し、やり直してください。|
> |**名前**:<br />CannotDeleteProfileWithProfileRules<br />**16 進数**:<br />80061106<br />**数値**:<br />-2147086074|このチャネル アクセス プロファイルは 1 つ以上のチャネル アクセス プロファイル ルールで使用されているため、削除できません。 このプロファイルをチャネル アクセス プロファイル ルールから削除した後でやり直してください。|
> |**名前**:<br />CannotDeletePropertyOverriddenByBundleItem<br />**16 進数**:<br />80081015<br />**数値**:<br />-2146955243|このプロパティは、1 つ以上の関連バンドル製品で上書きされているため、削除できません。 このプロパティの上書きされたバージョンを関連バンドル製品から削除し、変更したバンドルを再公開してから、やり直してください。|
> |**名前**:<br />CannotDeleteQueueWithQueueItems<br />**16 進数**:<br />80631117<br />**数値**:<br />-2140991209|このキューにはアイテムが割り当てられているため、削除できません。 これらのアイテムを別のユーザー、チーム、またはキューに割り当て、もう一度やり直してください。|
> |**名前**:<br />CannotDeleteQueueWithRouteRules<br />**16 進数**:<br />80731118<br />**数値**:<br />-2139942632|1 つ以上のルーティング規則セットがこのキューを使用するため、このキューは削除できません。 ルーティング規則セットからキューを削除したうえで、やり直してください。|
> |**名前**:<br />CannotDeleteRelatedSla<br />**16 進数**:<br />8004F859<br />**数値**:<br />-2147157927|SLA レコードを削除できませんでした。 もう一度やり直すか、システム管理者にお問い合わせください。|
> |**名前**:<br />CannotDeleteRestrictedPublisher<br />**16 進数**:<br />8004F006<br />**数値**:<br />-2147160058|制限された発行元を削除しようとしています。|
> |**名前**:<br />CannotDeleteRestrictedSolution<br />**16 進数**:<br />8004F005<br />**数値**:<br />-2147160059|制限されたソリューションを削除しようとしています。|
> |**名前**:<br />CannotDeleteSupportUser<br />**16 進数**:<br />80041d42<br />**数値**:<br />-2147214014|サポート ユーザーのロールは削除できません。|
> |**名前**:<br />CannotDeleteSysAdmin<br />**16 進数**:<br />80041d2e<br />**数値**:<br />-2147214034|システム管理者ロールは削除できません。|
> |**名前**:<br />CannotDeleteSystemCustomizer<br />**16 進数**:<br />80041d4a<br />**数値**:<br />-2147214006|システム カスタマイザー ロールは削除できません。|
> |**名前**:<br />CannotDeleteSystemEmailTemplate<br />**16 進数**:<br />80048432<br />**数値**:<br />-2147187662|システム電子メール テンプレートは削除できません。|
> |**名前**:<br />CannotDeleteSystemForm<br />**16 進数**:<br />8004F652<br />**数値**:<br />-2147158446|システム フォームは削除できません。|
> |**名前**:<br />CannotDeleteSystemTheme<br />**16 進数**:<br />800608DA<br />**数値**:<br />-2147088166|システム テーマは削除できません。|
> |**名前**:<br />CannotDeleteTeamOwningRecords<br />**16 進数**:<br />8004830E<br />**数値**:<br />-2147187954|レコードを所有するチームを削除できません。 レコードを再割り当てし、やり直してください。|
> |**名前**:<br />CannotDeleteUpdateInUseRule<br />**16 進数**:<br />80048428<br />**数値**:<br />-2147187672|重複データ検出ルールは現在使用中であり、更新または削除できません。 後でもう一度お試しください。|
> |**名前**:<br />CannotDeleteUserMailbox<br />**16 進数**:<br />8005E200<br />**数値**:<br />-2147098112|ユーザーまたはキューに関連付けられているメールボックスは削除できません。|
> |**名前**:<br />CannotDeleteUserProfile<br />**16 進数**:<br />800609A3<br />**数値**:<br />-2147087965|アクティブな Mobile Offline プロファイルは削除できません。 すべてのユーザーをプロファイルから削除して、やり直してください。|
> |**名前**:<br />CannotDeserializeRequest<br />**16 進数**:<br />8004416f<br />**数値**:<br />-2147204753|SDK の要求をシリアル化解除することはできません。|
> |**名前**:<br />CannotDeserializeWorkflowInstance<br />**16 進数**:<br />8004501F<br />**数値**:<br />-2147200993|ワークフロー インスタンスをシリアル化解除することはできません。 このエラーの原因として、ワークフローが、登録を解除されたユーザー定義活動を参照していることが考えられます。|
> |**名前**:<br />CannotDeserializeXamlWorkflow<br />**16 進数**:<br />80045020<br />**数値**:<br />-2147200992|ワークフローを表す Xaml は、DynamicActivity でシリアル化解除することはできません。|
> |**名前**:<br />CannotDisableAutoCreateAccessTeams<br />**16 進数**:<br />80048338<br />**数値**:<br />-2147187912|チーム テンプレートが関連付けられている状態で、自動作成アクセス チーム設定を無効にすることはできません。|
> |**名前**:<br />CannotDisableDuplicateDetection<br />**16 進数**:<br />80048462<br />**数値**:<br />-2147187614|重複データ検出ジョブが現在処理中であるため、重複データ検出を無効にできません。 後でもう一度試してみてください。|
> |**名前**:<br />CannotDisableInternetMarketingUser<br />**16 進数**:<br />80045033<br />**数値**:<br />-2147200973|Internet Marketing Partner のユーザーを無効にすることはできません。 このユーザーはユーザー ライセンスを消費せず、課金されません。|
> |**名前**:<br />CannotDisableMobileOfflineFlagForEntity<br />**16 進数**:<br />800609A5<br />**数値**:<br />-2147087963|Mobile Offline プロファイルで使用されているため、このエンティティの Mobile Offline フラグは無効にできません。|
> |**名前**:<br />CannotDisableMobileOfflineFlagForImportEntity<br />**16 進数**:<br />80071111<br />**数値**:<br />-2147020527|ソリューション インポートを使用して {0} エンティティのモバイル オフラインを無効にできません。 このエンティティをオフライン モードで使用したくない場合は、カスタマイズ画面から [モバイル オフラインを有効にする] を非選択にします。|
> |**名前**:<br />CannotDisableOrDeletePositionDueToAssociatedUsers<br />**16 進数**:<br />80048343<br />**数値**:<br />-2147187901|このポジションから関連するすべてのユーザーが削除されるまで、このポジションは削除できません。|
> |**名前**:<br />CannotDisableRelevanceSearchManagedProperty<br />**16 進数**:<br />80060303<br />**数値**:<br />-2147089661|{0} エンティティは現在、外部検索インデックスに同期されています。  [外部検索インデックスとの同期の有効化が可能] プロパティを [False] に設定するには、外部検索インデックスからエンティティを削除する必要があります。|
> |**名前**:<br />CannotDisableSysAdmin<br />**16 進数**:<br />80041d2f<br />**数値**:<br />-2147214033|システム管理者ロールを持つ唯一のユーザーの場合、ユーザーを無効にすることはできません。|
> |**名前**:<br />CannotDisableTenantAdmin<br />**16 進数**:<br />80041d65<br />**数値**:<br />-2147213979|Microsoft Office 365 の全体管理者ロールまたはサービス管理者ロールを付与されているユーザーは、Microsoft Dynamics 365 Online で無効にすることができません。 先に Microsoft Office 365 ロールを削除してから、やり直してください。|
> |**名前**:<br />CannotEditActiveRule<br />**16 進数**:<br />8004F851<br />**数値**:<br />-2147157935|アクティブなルーティング規則を編集することはできません。 ルールを非アクティブ化して削除してください。|
> |**名前**:<br />CannotEditActiveSla<br />**16 進数**:<br />8004F860<br />**数値**:<br />-2147157920|アクティブな SLA は削除できません。削除する SLA を非アクティブ化するか、システム管理者に問い合わせてください。|
> |**名前**:<br />CannotEnableDuplicateDetection<br />**16 進数**:<br />80048421<br />**数値**:<br />-2147187679|重複データ検出は、1 つまたは複数のルールが現在公開処理中のため、有効にできません。|
> |**名前**:<br />CannotEnableEntityForRelevanceSearch<br />**16 進数**:<br />80060302<br />**数値**:<br />-2147089662|マネージド プロパティの構成が原因で、エンティティ {0} の関連性検索を有効にできません。|
> |**名前**:<br />CannotExceedFilterLimit<br />**16 進数**:<br />8004027c<br />**数値**:<br />-2147220868|同期フィルターの制限を超えることはできません。|
> |**名前**:<br />CannotExecuteRequestBecauseHttpsIsRequired<br />**16 進数**:<br />8004852C<br />**数値**:<br />-2147187412|この種類の要求には HTTPS プロトコルが必要です。HTTPS プロトコルを有効にしてからやり直してください。|
> |**名前**:<br />CannotFindDomainAccount<br />**16 進数**:<br />80044342<br />**数値**:<br />-2147204286|無効なドメイン アカウントです。|
> |**名前**:<br />CannotFindObjectInQueue<br />**16 進数**:<br />800404eb<br />**数値**:<br />-2147220245|オブジェクトは、指定されたキューで見つかりませんでした|
> |**名前**:<br />CannotFindUserQueue<br />**16 進数**:<br />800404ec<br />**数値**:<br />-2147220244|ユーザー キューが見つかりません|
> |**名前**:<br />CannotFollowInactiveEntity<br />**16 進数**:<br />8004F6A3<br />**数値**:<br />-2147158365|非アクティブなレコードはフォローできません。 |
> |**名前**:<br />CannotGrantAccessToAddressBookFilters<br />**16 進数**:<br />80048446<br />**数値**:<br />-2147187642|アドレス帳フィルターへのアクセス権の付与はできません|
> |**名前**:<br />CannotGrantAccessToOfflineFilters<br />**16 進数**:<br />80040271<br />**数値**:<br />-2147220879|オフライン フィルターへのアクセス権の付与はできません|
> |**名前**:<br />CannotGrantAccessToOutlookFilters<br />**16 進数**:<br />80040268<br />**数値**:<br />-2147220888|Outlook フィルターへのアクセス権の付与はできません|
> |**名前**:<br />CannotHaveDuplicateYomi<br />**16 進数**:<br />80047018<br />**数値**:<br />-2147192808|1 つの属性は、1 度に 1 つの yomi のみ結び付けられます。|
> |**名前**:<br />CannotHaveMultipleDefaultFilterTemplates<br />**16 進数**:<br />8004027d<br />**数値**:<br />-2147220867|単一のエンティティに対して、複数の既定の同期テンプレートを使用することはできません。|
> |**名前**:<br />CannotImportNullStringsForBaseLanguage<br />**16 進数**:<br />80044246<br />**数値**:<br />-2147204538|ワークシート {0}、行 {1}は、列 {2} にある基本言語翻訳文字列が null です。|
> |**名前**:<br />CannotInviteDisabledUser<br />**16 進数**:<br />8004D212<br />**数値**:<br />-2147167726|無効なユーザーに招待状を送信することはできません|
> |**名前**:<br />CannotLocateRecordForWorkflowActivity<br />**16 進数**:<br />80045031<br />**数値**:<br />-2147200975|このワークフロー ジョブで要求されたレコードが見つかりませんでした。|
> |**名前**:<br />CannotMakeReadOnlyUser<br />**16 進数**:<br />80041d38<br />**数値**:<br />-2147214024|システム管理者ロールを持つ最後の読み取り専用でないユーザーの場合、ユーザーを読み取り専用ユーザーにすることはできません。|
> |**名前**:<br />CannotMakeSelfReadOnlyUser<br />**16 進数**:<br />80041d39<br />**数値**:<br />-2147214023|自分を読み取り専用ユーザーにすることはできません|
> |**名前**:<br />CannotMergeCase<br />**16 進数**:<br />8004F457<br />**数値**:<br />-2147158953|統合を実行することができませんでした。 サポート案件に対して定義されている状態の移行ルールにより、選択した 1 つ以上のサポート案件を取り消すことができません。|
> |**名前**:<br />CannotModifyAccessToAddressBookFilters<br />**16 進数**:<br />80048445<br />**数値**:<br />-2147187643|アドレス帳フィルターに対するアクセス権の変更はできません|
> |**名前**:<br />CannotModifyAccessToOfflineFilters<br />**16 進数**:<br />80040272<br />**数値**:<br />-2147220878|オフライン フィルターに対するアクセス権の変更はできません|
> |**名前**:<br />CannotModifyAccessToOutlookFilters<br />**16 進数**:<br />80040269<br />**数値**:<br />-2147220887|Outlook フィルターに対するアクセス権の変更はできません|
> |**名前**:<br />CannotModifyOldDataFromImport<br />**16 進数**:<br />80040376<br />**数値**:<br />-2147220618|Microsoft Dynamics 365 で対応するレコードには最新のデータがあり、このレコードは無視されました。|
> |**名前**:<br />CannotModifyPatchedSolution<br />**16 進数**:<br />80048538<br />**数値**:<br />-2147187400|次の修正プログラム: {0} が適用されているため、ソリューションは変更できません。|
> |**名前**:<br />CannotModifyReportOutsideSolutionIfManaged<br />**16 進数**:<br />8004F038<br />**数値**:<br />-2147160008|管理ソリューションはソリューション パッケージに存在しないレポートを更新するすることができません。|
> |**名前**:<br />CannotModifyRollupDependentField<br />**16 進数**:<br />80060555<br />**数値**:<br />-2147089067|ロールアップ フィールド {0} はこのフィールドを作成しました。 直接修正することはできません。|
> |**名前**:<br />CannotModifySpecialUser<br />**16 進数**:<br />80041d33<br />**数値**:<br />-2147214029|'SYSTEM' および 'INTEGRATION' ユーザーへの変更は許可されていません。|
> |**名前**:<br />CannotModifySupportUser<br />**16 進数**:<br />80041d43<br />**数値**:<br />-2147214013|サポート ユーザーのロールは修正できません。|
> |**名前**:<br />CannotModifySysAdmin<br />**16 進数**:<br />80041d31<br />**数値**:<br />-2147214031|システム管理者ロールは修正できません。|
> |**名前**:<br />CannotOverrideOwnedDynamicProperty<br />**16 進数**:<br />80081005<br />**数値**:<br />-2146955259|製品ファミリから継承されていないプロパティを上書きすることはできません。|
> |**名前**:<br />CannotOverrideProperty<br />**16 進数**:<br />8004F887<br />**数値**:<br />-2147157881|このプロパティの別の上書きされたバージョンが既に存在するため、このプロパティを上書きできません。 以前に上書きされたバージョンを削除し、もう一度やり直してください。|
> |**名前**:<br />CannotOverridePropertyFromDifferentHierarchy<br />**16 進数**:<br />8004F914<br />**数値**:<br />-2147157740|異なる製品階層に属するプロパティを上書きすることはできません。|
> |**名前**:<br />CannotOverwriteActiveComponent<br />**16 進数**:<br />8004F016<br />**数値**:<br />-2147160042|マネージド ソリューションは、アンマネージド基本インスタンスがある ID={2} を持つ {0} コンポーネント {1} を上書きできません。  このエラーは、ほとんどの場合、次の状況で発生します。アンマネージド ソリューションがターゲット システム上に新しいアンマネージド {0} コンポーネントをインストールした後に、同じ発行者のマネージド ソリューションがその同じ {0} コンポーネントをマネージド コンポーネントとしてインストールしようとします。  これによって、ターゲット システム上で、許可されないソリューションの無効な多層化が発生します。|
> |**名前**:<br />CannotOverwriteProperty<br />**16 進数**:<br />80061036<br />**数値**:<br />-2147086282|このプロパティの別の上書きされたバージョンが既に存在するため、このプロパティを上書きできません。 以前に上書きされたバージョンを削除し、もう一度やり直してください。|
> |**名前**:<br />CannotPayNonActiveInvoice<br />**16 進数**:<br />80100000<br />**数値**:<br />-2146435072|請求書は、アクティブ状態でないため支払いできません。|
> |**名前**:<br />CannotPropagateCamapaignActivityForTemplate<br />**16 進数**:<br />80040311<br />**数値**:<br />-2147220719|キャンペーン テンプレートに CampaignActivity を実行 (配布) できません。|
> |**名前**:<br />CannotProvisionPartnerSolution<br />**16 進数**:<br />8004A10f<br />**数値**:<br />-2147180273|パートナー ソリューションは既にプロビジョニングされた、またはプロビジョニング中であるかのどちらかであるため、準備することができません。|
> |**名前**:<br />CannotPublishAppModule<br />**16 進数**:<br />80050114<br />**数値**:<br />-2147155692|アプリで検証エラーが見つかったため、アプリを公開できません。|
> |**名前**:<br />CannotPublishBundleWithProductStateDraftOrRetire<br />**16 進数**:<br />8004F907<br />**数値**:<br />-2147157753|関連付けられた製品がドラフト状態、廃止状態、または変更中であるために、このバンドルを公開できません。|
> |**名前**:<br />CannotPublishChildOfNonActiveProductFamily<br />**16 進数**:<br />8004F909<br />**数値**:<br />-2147157751|このレコードは、公開されていない製品ファミリに属しているため公開できません。|
> |**名前**:<br />CannotPublishEmptyRule<br />**16 進数**:<br />80048414<br />**数値**:<br />-2147187692|条件が指定されていません。 条件を追加し、重複データ検出ルールを公開します。|
> |**名前**:<br />CannotPublishInactiveRule<br />**16 進数**:<br />80048413<br />**数値**:<br />-2147187693|選択した重複データ検出ルールは、非アクティブとしてマークされます。 公開前に、ルールをアクティブ化する必要があります。|
> |**名前**:<br />CannotPublishKitWithProductStateDraftOrRetire<br />**16 進数**:<br />8004F916<br />**数値**:<br />-2147157738|関連付けられた製品がドラフト状態、廃止状態、または変更中であるために、このセット製品を公開できません。|
> |**名前**:<br />CannotPublishMoreRules<br />**16 進数**:<br />80048419<br />**数値**:<br />-2147187687|選択したレコードの種類には、公開済みルールの最大数があります。 このレコードの種類に対する既存のルールの公開を取り下げるか、それを削除してからやり直してください。|
> |**名前**:<br />CannotPublishNestedBundle<br />**16 進数**:<br />80061011<br />**数値**:<br />-2147086319|バンドルを含むバンドルを公開することはできません。 このバンドルからすべてのバンドルを削除してから、公開し直してください。|
> |**名前**:<br />CannotQualifyLead<br />**16 進数**:<br />80081018<br />**数値**:<br />-2146955240|取引先企業を作成するためのアクセス許可がないため、このリードを見込みありと評価できません。 システム管理者に依頼して取引先企業を作成し、やり直してください。|
> |**名前**:<br />CannotQueryBaseTableWithAggregates<br />**16 進数**:<br />8004F00D<br />**数値**:<br />-2147160051|ベース テーブルのクエリが無効です。  集計は、ベース テーブル クエリに含めることはできません。|
> |**名前**:<br />CannotRelateObjectTypeToCampaign<br />**16 進数**:<br />80040307<br />**数値**:<br />-2147220729|指定されたオブジェクトの種類はサポートされていません|
> |**名前**:<br />CannotRelateObjectTypeToCampaignActivity<br />**16 進数**:<br />8004030d<br />**数値**:<br />-2147220723|指定されたオブジェクトの種類はサポートされていません|
> |**名前**:<br />CannotRemoveComponentFromDefaultSolution<br />**16 進数**:<br />8004F000<br />**数値**:<br />-2147160064|ソリューション コンポーネントを既定のソリューションから削除できません。|
> |**名前**:<br />CannotRemoveComponentFromSolution<br />**16 進数**:<br />8004F021<br />**数値**:<br />-2147160031|ソリューション {2} で、ソリューション コンポーネント {0} {1} が見つかりません。|
> |**名前**:<br />CannotRemoveComponentFromSystemSolution<br />**16 進数**:<br />8004F035<br />**数値**:<br />-2147160011|ソリューション コンポーネントをシステム ソリューションから削除できません。|
> |**名前**:<br />CannotRemoveFromSupportUser<br />**16 進数**:<br />80041d45<br />**数値**:<br />-2147214011|ユーザーをサポート ユーザー ロールから削除できません。|
> |**名前**:<br />CannotRemoveFromSysAdmin<br />**16 進数**:<br />80041d30<br />**数値**:<br />-2147214032|ロールを持つ唯一のユーザーである場合、ユーザーはシステム管理者ロールから削除できません。|
> |**名前**:<br />CannotRemoveMembersFromDefaultTeam<br />**16 進数**:<br />8004830C<br />**数値**:<br />-2147187956|既定の部署チームからメンバーを削除することはできません。|
> |**名前**:<br />CannotRemoveNonListMember<br />**16 進数**:<br />80048458<br />**数値**:<br />-2147187624|指定した項目は指定したリストのメンバーではありません。|
> |**名前**:<br />CannotRemoveProductFromPricelist<br />**16 進数**:<br />80061008<br />**数値**:<br />-2147086328|この製品は、1 つ以上のバンドルによって参照されているため、価格表から削除できません。|
> |**名前**:<br />CannotRemoveSysAdminProfileFromSysAdminUser<br />**16 進数**:<br />8004F505<br />**数値**:<br />-2147158779|システム管理者のプロファイルはシステム管理者ロールを持つユーザーから削除できません|
> |**名前**:<br />CannotRemoveTenantAdminFromSysAdminRole<br />**16 進数**:<br />80041d64<br />**数値**:<br />-2147213980|Microsoft Office 365 の全体管理者ロールまたはサービス管理者ロールを付与されているユーザーは、Microsoft Dynamics 365 のシステム管理者セキュリティ ロールから削除することができません。 先に Microsoft Office 365 ロールを削除してから、やり直してください。|
> |**名前**:<br />CannotResetAppointmentsToDraft<br />**16 進数**:<br />8004026a<br />**数値**:<br />-2147220886|予定を下書きにリセットすることはできません。|
> |**名前**:<br />CannotResetSysAdminInvite<br />**16 進数**:<br />8004D214<br />**数値**:<br />-2147167724|システム管理者ロールを持つ唯一のユーザーに対する招待状はリセットできません。|
> |**名前**:<br />CannotRetireProduct<br />**16 進数**:<br />8004F915<br />**数値**:<br />-2147157739|この製品は、アクティブなバンドルまたは価格表に属しているために廃止できません。 廃止する前にバンドル、または価格表から削除してください。|
> |**名前**:<br />CannotRetireProductFromActiveBundle<br />**16 進数**:<br />8004F997<br />**数値**:<br />-2147157609|この製品は、アクティブなバンドルまたは価格表の一部であるため廃止できません。 廃止する前にすべてのバンドル、または価格表から削除してください。|
> |**名前**:<br />CannotRevokeAccessToAddressBookFilters<br />**16 進数**:<br />80048444<br />**数値**:<br />-2147187644|アドレス帳フィルターに対するアクセス権を取り消すことはできません|
> |**名前**:<br />CannotRevokeAccessToOfflineFilters<br />**16 進数**:<br />80040273<br />**数値**:<br />-2147220877|オフライン フィルターに対するアクセス権を取り消すことはできません|
> |**名前**:<br />CannotRevokeAccessToOutlookFilters<br />**16 進数**:<br />80040270<br />**数値**:<br />-2147220880|Outlook フィルターに対するアクセス権を取り消すことはできません|
> |**名前**:<br />CannotRouteInactiveQueueItem<br />**16 進数**:<br />80040527<br />**数値**:<br />-2147220185|非アクティブ化されているキュー アイテムに対してルーティングを実行することはできません。|
> |**名前**:<br />CannotRoutePrivateQueueItemNonmember<br />**16 進数**:<br />80631121<br />**数値**:<br />-2140991199|このプライベート キュー アイテムを選択したユーザーに割り当てることはできません。|
> |**名前**:<br />CannotRouteToNonQueueMember<br />**16 進数**:<br />80731119<br />**数値**:<br />-2139942631|このアイテムをキュー以外のメンバーにルーティングすることはできません。|
> |**名前**:<br />CannotRouteToQueue<br />**16 進数**:<br />800404ea<br />**数値**:<br />-2147220246|処理中キューで [作業] にルートすることはできません|
> |**名前**:<br />CannotRouteToSameQueue<br />**16 進数**:<br />8004051b<br />**数値**:<br />-2147220197|キュー アイテムは同じキューにルーティングすることはできません|
> |**名前**:<br />CannotSecureAttribute<br />**16 進数**:<br />8004F501<br />**数値**:<br />-2147158783|フィールドは '{0}' セキュリティ保護可能ではありません|
> |**名前**:<br />CannotSecureEntityKeyAttribute<br />**16 進数**:<br />80060896<br />**数値**:<br />-2147088234|フィールドは {0} は、エンティティ キー ( {1} )の一部であるため、セキュリティ保護可能ではありません。 保護可能にするには、すべてのエンティティ キーからフィールドを削除してください。|
> |**名前**:<br />CannotSelectReadOnlyPublisher<br />**16 進数**:<br />8004F034<br />**数値**:<br />-2147160012|ソリューションの読み取り専用の発行元のみ選択します。|
> |**名前**:<br />CannotSendInviteToDuplicateWindowsLiveId<br />**16 進数**:<br />8004D215<br />**数値**:<br />-2147167723|この WLID の複数ユーザーがいるため、招待状を送信することはできません。|
> |**名前**:<br />CannotSetCaseOnHold<br />**16 進数**:<br />80055000<br />**数値**:<br />-2147135488|このサポート案件の状態の種類を保留に設定するアクセス許可がありません。 システム管理者にお問い合わせください。|
> |**名前**:<br />CannotSetEntitlementTermsDecrementBehavior<br />**16 進数**:<br />80060851<br />**数値**:<br />-2147088303|このサポート案件レコードの権利期間を減少させられるかどうかを指定するための適切な特権を持っていません。|
> |**名前**:<br />CannotSetEntityOnHold<br />**16 進数**:<br />80055004<br />**数値**:<br />-2147135484|このレコードを保留にするアクセス許可がありません。 システム管理者にお問い合わせください。|
> |**名前**:<br />CannotSetInactiveViewAsDefault<br />**16 進数**:<br />8004027b<br />**数値**:<br />-2147220869|非アクティブなビューは既定のビューに設定できません。|
> |**名前**:<br />CannotSetParentDefaultTeam<br />**16 進数**:<br />80048308<br />**数値**:<br />-2147187960|既定の部署チームの上位は設定できません。|
> |**名前**:<br />CannotSetProductAsParent<br />**16 進数**:<br />8004F998<br />**数値**:<br />-2147157608|製品ファミリのみをの親として選択できます。|
> |**名前**:<br />CannotSetPublishRetiredProductsToDraft<br />**16 進数**:<br />80061035<br />**数値**:<br />-2147086283|公開または廃止された製品レコードをドラフト状態に設定することはできません。|
> |**名前**:<br />CannotSetSolutionSystemAttributes<br />**16 進数**:<br />8004F008<br />**数値**:<br />-2147160056|システム属性 ({0}) はインストールまたはアップグレードの範囲外に設定することはできません。|
> |**名前**:<br />CannotSetWindowsLiveIdForInternetMarketingUser<br />**16 進数**:<br />80045034<br />**数値**:<br />-2147200972|Internet Marketing Partner ユーザーの Windows Live ID は変更できません。 このユーザーはユーザー ライセンスを消費せず、課金されません。|
> |**名前**:<br />CannotShareSystemManagedTeam<br />**16 進数**:<br />80048339<br />**数値**:<br />-2147187911|システムによって生成されたアクセス チームとの間でレコードを共有したり共有を解除したりすることはできません。|
> |**名前**:<br />CannotShareWithOwner<br />**16 進数**:<br />80040214<br />**数値**:<br />-2147220972|アイテムは、所有ユーザーと共有することはできません。|
> |**名前**:<br />CannotSpecifyAttendeeForAppointmentPropagation<br />**16 進数**:<br />8004031c<br />**数値**:<br />-2147220708|予定の配布に対して出席者を指定できません|
> |**名前**:<br />CannotSpecifyBothProductAndProductDesc<br />**16 進数**:<br />80043afb<br />**数値**:<br />-2147206405|同じレコードに 'productid' と 'productdescription' の両方を設定することはできません。|
> |**名前**:<br />CannotSpecifyBothUomAndProductDesc<br />**16 進数**:<br />80043afa<br />**数値**:<br />-2147206406|同じレコードに 'uomid' と 'productdescription' の両方を設定することはできません。|
> |**名前**:<br />CannotSpecifyCommunicationAttributeOnActivityForPropagation<br />**16 進数**:<br />8004031e<br />**数値**:<br />-2147220706|配布に対して活動の通信属性を指定できません|
> |**名前**:<br />CannotSpecifyOrganizerForAppointmentPropagation<br />**16 進数**:<br />8004031a<br />**数値**:<br />-2147220710|予定の配布に対して開催者を指定できません|
> |**名前**:<br />CannotSpecifyOwnerForActivityPropagation<br />**16 進数**:<br />80040327<br />**数値**:<br />-2147220697|活動の配布に対して所有者を指定できません|
> |**名前**:<br />CannotSpecifyRecipientForActivityPropagation<br />**16 進数**:<br />8004031d<br />**数値**:<br />-2147220707|活動の配布に対して受信者を指定できません。|
> |**名前**:<br />CannotSpecifySenderForActivityPropagation<br />**16 進数**:<br />8004031b<br />**数値**:<br />-2147220709|予定の配布に対して送信者を指定できません|
> |**名前**:<br />CannotUndeleteLabel<br />**16 進数**:<br />8004F003<br />**数値**:<br />-2147160061|削除としてマークされていないラベルの削除を取り消そうとしています。|
> |**名前**:<br />CannotUninstallReferencedProtectedSolution<br />**16 進数**:<br />8004F020<br />**数値**:<br />-2147160032|ID '{1}' の '{0}' がソリューション '{2}' で必要なため、このソリューションをアンインストールできません。 {2} ソリューションをアンインストールし、もう一度やり直してください。|
> |**名前**:<br />CannotUninstallWithDependencies<br />**16 進数**:<br />8004F01D<br />**数値**:<br />-2147160035|ソリューションの依存関係が存在するため、アンインストールできません。|
> |**名前**:<br />CannotUpdateActiveModernFlow<br />**16 進数**:<br />80060466<br />**数値**:<br />-2147089306|公開されたモダン フロー プロセスのプロパティ "{0}" を更新できません。|
> |**名前**:<br />CannotUpdateAppDefaultValueForStateAttribute<br />**16 進数**:<br />80044343<br />**数値**:<br />-2147204285|状態 (statecode) 属性の既定値は更新できません。|
> |**名前**:<br />CannotUpdateAppDefaultValueForStatusAttribute<br />**16 進数**:<br />80044344<br />**数値**:<br />-2147204284|ステータス (statecode) 属性の既定値は使用できません。 既定のステータスは、関連する状態 (statecode) 属性オプションで設定されます。|
> |**名前**:<br />CannotUpdateAppModuleClientType<br />**16 進数**:<br />80050128<br />**数値**:<br />-2147155672|このアプリのクライアントの種類を変更できません。|
> |**名前**:<br />CannotUpdateAppModuleUniqueName<br />**16 進数**:<br />80050119<br />**数値**:<br />-2147155687|一意の名前は変更できません。|
> |**名前**:<br />CannotUpdateAzureActiveDirectoryObjectIdField<br />**16 進数**:<br />80041d4f<br />**数値**:<br />-2147214001|プロパティ AzureActiveDirectoryObjectId を変更することはできません。|
> |**名前**:<br />CannotUpdateBecauseItIsReadOnly<br />**16 進数**:<br />8004022e<br />**数値**:<br />-2147220946|このオブジェクトは読み取り専用なので、更新できません。|
> |**名前**:<br />CannotUpdateCampaignForCampaignActivity<br />**16 進数**:<br />8004030b<br />**数値**:<br />-2147220725|上位キャンペーンは更新できません。|
> |**名前**:<br />CannotUpdateCampaignForCampaignResponse<br />**16 進数**:<br />8004030c<br />**数値**:<br />-2147220724|上位キャンペーンは更新できません。|
> |**名前**:<br />CannotUpdateDeactivatedQueueItem<br />**16 進数**:<br />8004051d<br />**数値**:<br />-2147220195|この項目は非アクティブ化されます。 この項目を使用するには、再アクティブ化してもう一度やり直してください。|
> |**名前**:<br />CannotUpdateDefaultField<br />**16 進数**:<br />800608D8<br />**数値**:<br />-2147088168|isDefaultTheme 属性は更新できません。|
> |**名前**:<br />CannotUpdateDefaultSolution<br />**16 進数**:<br />8004F009<br />**数値**:<br />-2147160055|既定のソリューション属性{0} {1} は、インストールまたはアップグレードでのみ設定することができます。  値 {0} は変更できません。|
> |**名前**:<br />CannotUpdateDelaySendTimeForEmailWhenEmailIsNotInProperState<br />**16 進数**:<br />80050020<br />**数値**:<br />-2147155936|電子メールが下書きでないか、送信するようにスケジュールされていないため、電子メールの遅延送信時間を更新できません。|
> |**名前**:<br />CannotUpdateDelaySendTimeWhenEEFeatureNotEnabled<br />**16 進数**:<br />80050021<br />**数値**:<br />-2147155935|電子メール エンゲージメントが組織に対して有効になっていないため、電子メールの遅延送信時間を更新できません。|
> |**名前**:<br />CannotUpdateDraftProducts<br />**16 進数**:<br />8004F975<br />**数値**:<br />-2147157643|ドラフト製品のみを更新できます。|
> |**名前**:<br />CannotUpdateEmailStatisticForEmailNotFollowed<br />**16 進数**:<br />80050002<br />**数値**:<br />-2147155966|電子メールがフォローされていないため、電子メールの統計情報を更新できません。|
> |**名前**:<br />CannotUpdateEmailStatisticForEmailNotSent<br />**16 進数**:<br />80050001<br />**数値**:<br />-2147155967|電子メールが送信されていないため、電子メールの統計情報を更新できません。|
> |**名前**:<br />CannotUpdateEmailStatisticWhenEEFeatureNotEnabled<br />**16 進数**:<br />80050018<br />**数値**:<br />-2147155944|電子メール エンゲージメントが組織に対して有効になっていないため、電子メールの統計情報を更新できません。|
> |**名前**:<br />CannotUpdateEntitlement<br />**16 進数**:<br />80060852<br />**数値**:<br />-2147088302|既定として設定できるのは、アクティブな権利レコードのみです。|
> |**名前**:<br />CannotUpdateEntitySetName<br />**16 進数**:<br />8004F663<br />**数値**:<br />-2147158429|EntitySetName は OOB エンティティに対して更新されません|
> |**名前**:<br />CannotUpdateExternalPartyWithSameCorrelationKey<br />**16 進数**:<br />80061114<br />**数値**:<br />-2147086060|同じ関連付けキー値を持つ外部パーティ レコードが既に存在します。|
> |**名前**:<br />CannotUpdateGoalPeriodInfoChildGoal<br />**16 進数**:<br />80044901<br />**数値**:<br />-2147202815|下位目標の目標期間に関連する属性は更新できません。|
> |**名前**:<br />CannotUpdateGoalPeriodInfoClosedGoal<br />**16 進数**:<br />80044910<br />**数値**:<br />-2147202800|クローズした下位目標が 1 つ以上あるため、この目標の期間は変更できません。|
> |**名前**:<br />CannotUpdateManagedSolution<br />**16 進数**:<br />8004F024<br />**数値**:<br />-2147160028|ネージド ソリューションであるため、ソリューション {0} を更新できません。|
> |**名前**:<br />CannotUpdateMetricOnChildGoal<br />**16 進数**:<br />80044900<br />**数値**:<br />-2147202816|下位目標の指標は更新できません。|
> |**名前**:<br />CannotUpdateMetricOnGoalWithChildren<br />**16 進数**:<br />80044902<br />**数値**:<br />-2147202814|下位目標が関連付けられている目標の指標は更新できません。|
> |**名前**:<br />CannotUpdateMetricWithGoals<br />**16 進数**:<br />80044803<br />**数値**:<br />-2147203069|この目標指標が 1 つ以上の目標で使用されているため、このレコードへの変更を保存できません。|
> |**名前**:<br />CannotUpdateNameDefaultTeam<br />**16 進数**:<br />8004830A<br />**数値**:<br />-2147187958|既定の部署チーム名は更新できません。|
> |**名前**:<br />CannotUpdateNonCustomizableString<br />**16 進数**:<br />80044247<br />**数値**:<br />-2147204537|ワークシート {0}、行 {1}、列 {2} にある翻訳文字列は、カスタマイズできません。|
> |**名前**:<br />CannotUpdateObjectBecauseItIsInactive<br />**16 進数**:<br />80040230<br />**数値**:<br />-2147220944|オブジェクトは、非アクティブなため更新できません。|
> |**名前**:<br />CannotUpdateOpportunityCurrency<br />**16 進数**:<br />80048479<br />**数値**:<br />-2147187591|この営業案件には関連付けられている [製品の見積もり] と [受注] があるため、通貨は使用できません。  通貨を変更する場合は、すべての製品/見積もり/受注を削除してから通貨を変更するか、または適切な通貨で新しい営業案件を作成します。|
> |**名前**:<br />CannotUpdateOrgDBOrgSettingWhenOffline<br />**16 進数**:<br />80048515<br />**数値**:<br />-2147187435|組織データベースに格納される組織の設定はオフラインの場合は設定することができません。|
> |**名前**:<br />CannotUpdateParentAndDependents<br />**16 進数**:<br />8004480c<br />**数値**:<br />-2147203060|親の更新時には、指標または期間属性を更新できません。|
> |**名前**:<br />CannotUpdatePrivateOrWIPQueue<br />**16 進数**:<br />800404ee<br />**数値**:<br />-2147220242|プライベートまたは WIP Bin キューの更新または削除は許可されていません|
> |**名前**:<br />CannotUpdateProductCurrency<br />**16 進数**:<br />80048cfa<br />**数値**:<br />-2147185414|価格設定方法の割合による価格表品目があるため、製品の通貨は更新できません。|
> |**名前**:<br />CannotUpdateQuoteCurrency<br />**16 進数**:<br />8004480e<br />**数値**:<br />-2147203058|この見積りには関連付けられている [製品] があるため、通貨は使用できません。 通貨を変更する場合は、すべての [製品] を削除してから通貨を変更するか、または適切な通貨で新しい見積もりを作成します。|
> |**名前**:<br />CannotUpdateReadOnlyPublisher<br />**16 進数**:<br />8004F033<br />**数値**:<br />-2147160013|読み取り専用の発行元のみ更新します。|
> |**名前**:<br />CannotUpdateRestrictedPublisher<br />**16 進数**:<br />8004F017<br />**数値**:<br />-2147160041|制限された発行者 ({0}) は更新することができません。|
> |**名前**:<br />CannotUpdateRestrictedSolution<br />**16 進数**:<br />8004F00A<br />**数値**:<br />-2147160054|制限されたソリューション ({0}) は更新することができません。|
> |**名前**:<br />CannotUpdateRollupAttributeWithClosedGoals<br />**16 進数**:<br />80044801<br />**数値**:<br />-2147203071|関連する目標指標がクローズした 1 つ以上の目標で使用されているため、ロールアップ フィールド定義への変更を保存できません。|
> |**名前**:<br />CannotUpdateRollupFields<br />**16 進数**:<br />80044911<br />**数値**:<br />-2147202799|作成 / 更新要求で isoverride が true に設定されている場合、ロールアップ フィールドに書き込むことはできません。|
> |**名前**:<br />CannotUpdateSolutionPatch<br />**16 進数**:<br />8004F042<br />**数値**:<br />-2147159998|バージョン {0} のソリューション修正プログラムはすでに存在します。 修正プログラムの更新はサポートされていません。|
> |**名前**:<br />CannotUpdateSupportUser<br />**16 進数**:<br />80041d47<br />**数値**:<br />-2147214009|サポート ユーザー ロールは更新できません。|
> |**名前**:<br />CannotUpdateSyncUserIsLicensedField<br />**16 進数**:<br />80041d4c<br />**数値**:<br />-2147214004|プロパティ IsLicensed を変更することはできません。|
> |**名前**:<br />CannotUpdateSyncUserIsSyncWithDirectoryField<br />**16 進数**:<br />80041d4e<br />**数値**:<br />-2147214002|プロパティ IsSyncUserWithDirectory を変更することはできません。|
> |**名前**:<br />CannotUpdateSystemEntityIcons<br />**16 進数**:<br />8004F653<br />**数値**:<br />-2147158445|システム エンティティのアイコンは更新できません。|
> |**名前**:<br />CannotUpdateSystemTheme<br />**16 進数**:<br />800608D6<br />**数値**:<br />-2147088170|システム テーマは変更できません。|
> |**名前**:<br />CannotUpdateTemplateIdForEmailInNonDraftState<br />**16 進数**:<br />80050017<br />**数値**:<br />-2147155945|電子メールが既に送信されたか、または下書き状態でないため、テンプレートを更新できません。|
> |**名前**:<br />CannotUpdateTriggerForPublishedRules<br />**16 進数**:<br />80060002<br />**数値**:<br />-2147090430|トリガーが、公開済みのルールで追加/削除/更新されることはありません。|
> |**名前**:<br />CannotUpdateUnpublishedDeleteInstance<br />**16 進数**:<br />8004F00F<br />**数値**:<br />-2147160049|更新しようとするコンポーネントが削除されました。|
> |**名前**:<br />CannotUseOpportunitySetStateMessage<br />**16 進数**:<br />80100005<br />**数値**:<br />-2146435067|このメッセージは、営業案件の状態を {0} に設定するために使用できません。 営業案件の状態を {1} に設定するには、代わりに {1} メッセージを使用します。|
> |**名前**:<br />CannotUseUserCredentials<br />**16 進数**:<br />8005E229<br />**数値**:<br />-2147098071|電子メール コネクタは、メールボックス エンティティで指定された資格情報を使用できません。 これはユーザーが非許可に設定したために起きた可能性があります。 資格情報の取得方法を変更するか、電子メール コネクタで資格情報の使用を許可してください。|
> |**名前**:<br />CanOnlySetActiveOrDraftProductFamilyAsParent<br />**16 進数**:<br />8004F906<br />**数値**:<br />-2147157754|ドラフト状態またはアクティブ状態の製品ファミリのみを親として設定できます。|
> |**名前**:<br />CantSaveRecordInOffline<br />**16 進数**:<br />8005F214<br />**数値**:<br />-2147093996|このレコードはオフライン時には保存できません。|
> |**名前**:<br />CantSetIsGuestProfile<br />**16 進数**:<br />8006111A<br />**数値**:<br />-2147086054|IsGuestProfile フィールドの値は、内部でのみ使用するため、設定または変更することはできません。|
> |**名前**:<br />CantUpdateOnlineRecord<br />**16 進数**:<br />8005F224<br />**数値**:<br />-2147093980|このレコードは、オフライン モードでは存在しないため更新できません。|
> |**名前**:<br />CanvasAppsExpectedFileMissing<br />**16 進数**:<br />80072356<br />**数値**:<br />-2147015850|ソリューションは想定される資産ファイルを指定しましたが、そのファイルは見つからないか無効でした。|
> |**名前**:<br />CanvasAppsInvalidSolutionFileContent<br />**16 進数**:<br />80072354<br />**数値**:<br />-2147015852|キャンバス アプリをインポートする要求は、少なくとも 1 つの資産ファイルを含む必要があります。|
> |**名前**:<br />CanvasAppsNotEnabled<br />**16 進数**:<br />80072351<br />**数値**:<br />-2147015855|キャンバス アプリの作成および編集が有効になっていません。|
> |**名前**:<br />CanvasAppsServiceRequestClientFailure<br />**16 進数**:<br />80072352<br />**数値**:<br />-2147015854|PowerApps サービスへの要求がクライアント障害で失敗しました。|
> |**名前**:<br />CanvasAppsServiceRequestServerFailure<br />**16 進数**:<br />80072353<br />**数値**:<br />-2147015853|PowerApps サービスへの要求がサーバー障害で失敗しました。|
> |**名前**:<br />CanvasAppsUnexpectedCanvasAppId<br />**16 進数**:<br />80072355<br />**数値**:<br />-2147015851|以前存在した値が予期されたときに、PowerApps サービスへの要求で新しい canvasappid が生成されました。|
> |**名前**:<br />CanvasAppVersionDoesNotMatchLatestPublishedVersion<br />**16 進数**:<br />80072358<br />**数値**:<br />-2147015848|キャンバス アプリの最新の公開バージョンが、Dynamics サービスから認識されるバージョンと一致しません。|
> |**名前**:<br />CanvasAppVersionMissingOrInvalid<br />**16 進数**:<br />80072357<br />**数値**:<br />-2147015849|キャンバス アプリのアプリ バージョンが設定されていないか、無効な値でした。|
> |**名前**:<br />CAPolicyValidationFailedLateBind<br />**16 進数**:<br />80072561<br />**数値**:<br />-2147015327|ユーザーは管理者限定の場所にいます。|
> |**名前**:<br />CascadeDeleteNotAllowDelete<br />**16 進数**:<br />80048103<br />**数値**:<br />-2147188477|オブジェクトの削除は許可されていません|
> |**名前**:<br />CascadeFailToCreateNativeDAWrapper<br />**16 進数**:<br />80048108<br />**数値**:<br />-2147188472|アンマネージド データ アクセス ラッパーを作成できませんでした|
> |**名前**:<br />CascadeInvalidExtraConditionValue<br />**16 進数**:<br />80048101<br />**数値**:<br />-2147188479|無効な追加条件値|
> |**名前**:<br />CascadeInvalidLinkType<br />**16 進数**:<br />80048102<br />**数値**:<br />-2147188478|無効な CascadeLink の種類|
> |**名前**:<br />CascadeInvalidLinkTypeTransition<br />**16 進数**:<br />80044155<br />**数値**:<br />-2147204779|システム エンティティ カスケード アクションのリンクの種類が無効です。|
> |**名前**:<br />CascadeMergeInvalidSpecialColumn<br />**16 進数**:<br />80048106<br />**数値**:<br />-2147188474|特別な形式の結合の列名が無効です。|
> |**名前**:<br />CascadeProxyEmptyCallerId<br />**16 進数**:<br />8004810b<br />**数値**:<br />-2147188469|空の呼び出し元 ID|
> |**名前**:<br />CascadeProxyInvalidNativeDAPtr<br />**16 進数**:<br />80048109<br />**数値**:<br />-2147188471|無効なアンマネージド データ オブジェクト アクセスのポインター|
> |**名前**:<br />CascadeProxyInvalidPrincipalType<br />**16 進数**:<br />8004810a<br />**数値**:<br />-2147188470|無効なセキュリティ プリンシパルの種類です。|
> |**名前**:<br />CascadeRemoveLinkOnNonNullable<br />**16 進数**:<br />80048104<br />**数値**:<br />-2147188476|CascadeDelete は、外部キーの NULL 値が許容される際に RemoveLink として定義されます|
> |**名前**:<br />CascadeReparentOnNonUserOwned<br />**16 進数**:<br />80048107<br />**数値**:<br />-2147188473|非ユーザーの所有するエンティティで、カスケード リペアレントは実行できません|
> |**名前**:<br />CaseAlreadyResolved<br />**16 進数**:<br />800404cf<br />**数値**:<br />-2147220273|このサポート案件は既に解決済みです。 サポート案件レコードを閉じてもう一度開くと、更新内容を表示できます。|
> |**名前**:<br />CaseStateChangeInvalid<br />**16 進数**:<br />8006074<br />**数値**:<br />134242420|状態の移行ルールのため、現在の状態からサポート案件を解決することはできません。 サポート案件の状態を変更して、それを解決するよう試みるか、またはシステム管理者にお問い合わせください。|
> |**名前**:<br />CategoryDataTypeInvalid<br />**16 進数**:<br />8004E01A<br />**数値**:<br />-2147164134|ビジュアル化のデータ記述が無効です。 いずれかのカテゴリのグループの属性の種類が無効です。 データ記述を修正します。|
> |**名前**:<br />CategoryNotSetToBusinessProcessFlow<br />**16 進数**:<br />80060404<br />**数値**:<br />-2147089404|カテゴリは、ビジネス プロセス フローのカテゴリの作成時に BusinessProcessFlow に設定されている必要があります|
> |**名前**:<br />CDSOrgNotSupported<br />**16 進数**:<br />80044510<br />**数値**:<br />-2147203824|この組織で Dynamics 365 for Outlook はサポートされていません。|
> |**名前**:<br />CertificateNotFound<br />**16 進数**:<br />8005E239<br />**数値**:<br />-2147098055|指定された証明書が見つかりません。|
> |**名前**:<br />ChangeTrackingDisabledForMobileOfflineError<br />**16 進数**:<br />800609A1<br />**数値**:<br />-2147087967|Mobile Offline が既に有効になっているため、このエンティティの変更履歴は無効にできません。|
> |**名前**:<br />ChangeTrackingNotEnabledForEntity<br />**16 進数**:<br />80072491<br />**数値**:<br />-2147015535|エンティティ {0} は変更の追跡が有効になっていません。|
> |**名前**:<br />ChangeTrackingNotEnabledForRelatedEntities<br />**16 進数**:<br />80072492<br />**数値**:<br />-2147015534|両方の関連エンティティが変更追跡に対して有効になっていないため、交差エンティティ {0} に対して変更を取得できません。|
> |**名前**:<br />ChannelAccessProfileRuleAlreadyInDraftState<br />**16 進数**:<br />80061115<br />**数値**:<br />-2147086059|下書きのチャネル アクセス プロファイル ルールを非アクティブ化することはできません。|
> |**名前**:<br />ChannelPropertyGroupAlreadyExistsWithSameSourceType<br />**16 進数**:<br />800608EC<br />**数値**:<br />-2147088148|指定したソースの種類には、レコードが既に存在します。 もう 1 つ作成することはできません。|
> |**名前**:<br />ChannelPropertyNameInvalid<br />**16 進数**:<br />800608F2<br />**数値**:<br />-2147088142|チャネル プロパティ名が無効です。 名前には'_'、数字およびアルファベット文字のみ使用できます。 異なる名前を選択して、やり直してください。|
> |**名前**:<br />ChartAreaCategoryMismatch<br />**16 進数**:<br />8004E005<br />**数値**:<br />-2147164155|グラフ エリアの数は、項目の数に等しくする必要があります。|
> |**名前**:<br />ChartTypeNotSupportedForComparisonChart<br />**16 進数**:<br />8004E018<br />**数値**:<br />-2147164136|このグラフの種類は、比較グラフでサポートされていません。|
> |**名前**:<br />ChartTypeNotSupportedForMultipleSeriesChart<br />**16 進数**:<br />8004E021<br />**数値**:<br />-2147164127|グラフの種類の系列 {0} は複数系列のグラフではサポートされていません。|
> |**名前**:<br />CheckPrivilegeGroupForUserOnPremiseError<br />**16 進数**:<br />80048401<br />**数値**:<br />-2147187711|PrivUserGroup セキュリティ グループのメンバーであるアカウントを選択し、やり直してください。|
> |**名前**:<br />CheckPrivilegeGroupForUserOnSplaError<br />**16 進数**:<br />80048400<br />**数値**:<br />-2147187712|ルート部署に属する Dynamics 365 システム管理者アカウントを選択し、やり直してください。|
> |**名前**:<br />ChildBusinessDoesNotExist<br />**16 進数**:<br />80041d22<br />**数値**:<br />-2147214046|下位部署 ID が無効です。|
> |**名前**:<br />ChildUserDoesNotExist<br />**16 進数**:<br />80041d26<br />**数値**:<br />-2147214042|下位ユーザー ID が無効です。|
> |**名前**:<br />ChildWorkflowNotFound<br />**16 進数**:<br />8004502F<br />**数値**:<br />-2147200977|このワークフローが使用する複数の子ワークフローが公開または削除されているため、実行できません。 子ワークフローを確認し、このワークフローを再度実行してください。|
> |**名前**:<br />ChildWorkflowParameterMismatch<br />**16 進数**:<br />80045048<br />**数値**:<br />-2147200952|親ワークフローの提供する引数が子ワークフローにリンクされた指定されたパラメーターと一致しないため、このワークフローを実行することはできません。 親ワークフローで子ワークフローの参照を確認し、このワークフローを再度実行します。|
> |**名前**:<br />CircularDependency<br />**16 進数**:<br />80071157<br />**数値**:<br />-2147020457|他のソリューションとの循環依存関係のため、ソリューション操作が失敗しました。 詳細については例外を確認してください: {0}|
> |**名前**:<br />ClientAuthCanceled<br />**16 進数**:<br />8004D224<br />**数値**:<br />-2147167708|認証はユーザーによって取り消されました。|
> |**名前**:<br />ClientAuthNoConnectivity<br />**16 進数**:<br />8004D226<br />**数値**:<br />-2147167706|接続されていません。|
> |**名前**:<br />ClientAuthNoConnectivityOffline<br />**16 進数**:<br />8004D225<br />**数値**:<br />-2147167707|オフライン モードで実行されている場合、接続されていません。|
> |**名前**:<br />ClientAuthOfflineInvalidCallerId<br />**16 進数**:<br />8004D227<br />**数値**:<br />-2147167705|オフラインの SDK 呼び出しはオフラインのユーザー コンテキストで行う必要があります。|
> |**名前**:<br />ClientAuthSignedOut<br />**16 進数**:<br />8004D221<br />**数値**:<br />-2147167711|ユーザーはサインアウトしました|
> |**名前**:<br />ClientAuthSyncIssue<br />**16 進数**:<br />8004D223<br />**数値**:<br />-2147167709|プロセス間の同期に失敗しました。|
> |**名前**:<br />ClientServerDateTimeMismatch<br />**16 進数**:<br />80044503<br />**数値**:<br />-2147203837|コンピューターの日付 / 時間が 5 分以上サーバーと同期されていません。|
> |**名前**:<br />ClientServerEmailAddressMismatch<br />**16 進数**:<br />80044504<br />**数値**:<br />-2147203836|Outlook の電子メール アドレス、および Dynamics 365 ユーザーのアドレスは一致しません。|
> |**名前**:<br />ClientUpdateAvailable<br />**16 進数**:<br />8004D294<br />**数値**:<br />-2147167596|Dynamics 365 for Outlook に使用できる更新プログラムがあります。|
> |**名前**:<br />ClientVersionTooHigh<br />**16 進数**:<br />80044501<br />**数値**:<br />-2147203839|Outlook クライアントのこのバージョンは、Dynamics 365 組織と互換性がありません (現在のバージョン {0} は高すぎます)。|
> |**名前**:<br />ClientVersionTooLow<br />**16 進数**:<br />80044500<br />**数値**:<br />-2147203840|Outlook クライアントのこのバージョンは、Dynamics 365 組織と互換性がありません (現在のバージョン {0} は低すぎます)。|
> |**名前**:<br />CloneSolutionException<br />**16 進数**:<br />80048539<br />**数値**:<br />-2147187399|ソリューションの複製操作に失敗しました。|
> |**名前**:<br />CloneSolutionPatchException<br />**16 進数**:<br />80061771<br />**数値**:<br />-2147084431|修正プログラム '{0}' には、インストールする修正プログラムのバージョンと一致する、またはそれよりも新しいバージョン ({1}) があります。|
> |**名前**:<br />CloneTitleTooLong<br />**16 進数**:<br />80071112<br />**数値**:<br />-2147020526|検証エラーが発生しました。 mobileofflineprofile エンティティの [名前] 属性の長さが許可されている最大長である 200 を超えています。|
> |**名前**:<br />CloseActiveChildCaseFirst<br />**16 進数**:<br />8003F452<br />**数値**:<br />-2147224494|親サポート案件をクローズする前に、アクティブな子サポート案件をクローズしてください。|
> |**名前**:<br />ColorStripAttributesExceeded<br />**16 進数**:<br />80061500<br />**数値**:<br />-2147085056|カラー ストリップ セクションに複数の属性を割り当てることはできません|
> |**名前**:<br />ColorStripAttributesInvalid<br />**16 進数**:<br />80061502<br />**数値**:<br />-2147085054|カラー ストリップ セクションには、種類が "2 つのオプション"、"オプション セット"、および "ステータス" である属性しか設定できません。|
> |**名前**:<br />CombinedManagedPropertyFailure<br />**16 進数**:<br />8004F027<br />**数値**:<br />-2147160025|現在の操作 ({2}) 内の現在のコンポーネント (名前 ={0}、ID={1}) の評価は、少なくとも 1 つのマネージド プロパティの評価中に失敗しました: {3}|
> |**名前**:<br />CommandNotSupported<br />**16 進数**:<br />80154B52<br />**数値**:<br />-2146088110|コマンドは、オフライン モードではサポートされません。|
> |**名前**:<br />CommunicationBlocked<br />**16 進数**:<br />80044506<br />**数値**:<br />-2147203834|ソケットの例外が原因で、通信がブロックされています。|
> |**名前**:<br />ComponentDefinitionDoesNotExists<br />**16 進数**:<br />8004F019<br />**数値**:<br />-2147160039|コンポーネントの種類に {0} コンポーネント定義は存在しません。|
> |**名前**:<br />ConcurrencyVersionMismatch<br />**16 進数**:<br />80060882<br />**数値**:<br />-2147088254|既存レコードのバージョンは、提供された RowVersion のプロパティに対応していません。|
> |**名前**:<br />ConcurrencyVersionNotProvided<br />**16 進数**:<br />80060883<br />**数値**:<br />-2147088253|ConcurrencyBehavior の値が IfVersionMatches の場合、RowVersion のプロパティを指定する必要があります。|
> |**名前**:<br />ConcurrentOperationFailure<br />**16 進数**:<br />80071154<br />**数値**:<br />-2147020460|現在の {0} 操作は、別の同時実行操作が同時に実行されているため失敗しました。 後でやり直してください。|
> |**名前**:<br />ConditionAttributesNotAnSubsetOfStepAttributes<br />**16 進数**:<br />80060436<br />**数値**:<br />-2147089354|条件の属性は、ステージ: {0} に対するステップでの属性のサブセットではありません|
> |**名前**:<br />ConditionBranchDoesHaveSetNextStageOnlyChildInXaml<br />**16 進数**:<br />80060434<br />**数値**:<br />-2147089356|条件分岐は、子として SetNextStage のみを含めることができます。|
> |**名前**:<br />ConditionStepCountInXamlExceedsMaxAllowed<br />**16 進数**:<br />80060435<br />**数値**:<br />-2147089355|{0} は 1 つ以上の {1} を持つことはできません。|
> |**名前**:<br />ConfigDBCannotDeleteDefaultOrganization<br />**16 進数**:<br />8004D23B<br />**数値**:<br />-2147167685|既定の {0} 組織は、MSCRM_CONFIG データベースから削除することはできません。|
> |**名前**:<br />ConfigDBCannotDeleteObjectDueState<br />**16 進数**:<br />8004D232<br />**数値**:<br />-2147167694|MSCRM_CONFIG データベースから、この状態" =({2}) で値 = ({1}) を持つ '{0}' を削除できません|
> |**名前**:<br />ConfigDBCannotUpdateObjectDueState<br />**16 進数**:<br />8004D237<br />**数値**:<br />-2147167689|MSCRM_CONFIG データベースから、この状態" =({2}) で値 = ({1}) を持つ '{0}' を更新できません|
> |**名前**:<br />ConfigDBCascadeDeleteNotAllowDelete<br />**16 進数**:<br />8004D233<br />**数値**:<br />-2147167693|MSCRM_CONFIG データベースから、子 '{2}' 参照による値 = ({1}) を持つ '{0}' は削除できません|
> |**名前**:<br />ConfigDBDuplicateRecord<br />**16 進数**:<br />8004D231<br />**数値**:<br />-2147167695|重複 '{0}' 値 = ({1}) は MSCRM_CONFIG データベースに存在します|
> |**名前**:<br />ConfigDBObjectDoesNotExist<br />**16 進数**:<br />8004D230<br />**数値**:<br />-2147167696|'{0}' 値 = ({1}) は MSCRM_CONFIG データベースには存在しません|
> |**名前**:<br />ConfigMissingDescription<br />**16 進数**:<br />80044197<br />**数値**:<br />-2147204713|説明を指定してください。|
> |**名前**:<br />ConfigNullPrimaryKey<br />**16 進数**:<br />80044196<br />**数値**:<br />-2147204714|主キーは Null 値が許容されません。|
> |**名前**:<br />ConfigurationPageNotValidForSolution<br />**16 進数**:<br />8004701D<br />**数値**:<br />-2147192803|ソリューション構成ページは、対応するソリューション内に存在する必要があります。|
> |**名前**:<br />ConfigureClaimsBeforeIfd<br />**16 進数**:<br />8004D266<br />**数値**:<br />-2147167642|インターネットに接続する展開を構成するには、クレームベース認証を構成する必要があります。|
> |**名前**:<br />ConfiguredUserIsDifferentThanSuppliedUser<br />**16 進数**:<br />80044508<br />**数値**:<br />-2147203832|構成されたユーザーは指定されたユーザーとは異なります。|
> |**名前**:<br />ConflictForOverriddenPropertiesEncountered<br />**16 進数**:<br />80081010<br />**数値**:<br />-2146955248|このレコードは公開できません。 このレコードの変更されたプロパティのいずれかが継承されたバージョンと競合しています。 競合するプロパティを削除してからやり直してください。|
> |**名前**:<br />ConflictingProvisionTypes<br />**16 進数**:<br />8004B02C<br />**数値**:<br />-2147176404|サービス コンポーネント {0} には競合するプロビジョニングの種類があります。|
> |**名前**:<br />ConnectionCannotBeEnabledOnThisEntity<br />**16 進数**:<br />80048214<br />**数値**:<br />-2147188204|この {0} エンティティで ID {1} の接続を有効にできません。|
> |**名前**:<br />ConnectionExists<br />**16 進数**:<br />80048208<br />**数値**:<br />-2147188216|接続は既に存在します。|
> |**名前**:<br />ConnectionInvalidStartEndDate<br />**16 進数**:<br />80048209<br />**数値**:<br />-2147188215|開始日 / 終了日が無効です。|
> |**名前**:<br />ConnectionNotSupported<br />**16 進数**:<br />80048213<br />**数値**:<br />-2147188205|選択したレコードはつながりをサポートしていません。 接続を追加することはできません。|
> |**名前**:<br />ConnectionObjectsMissing<br />**16 進数**:<br />80048210<br />**数値**:<br />-2147188208|接続するオブジェクトがどちらも見つかりません。|
> |**名前**:<br />ConnectionRoleNotValidForObjectType<br />**16 進数**:<br />80048215<br />**数値**:<br />-2147188203|レコードの種類 {0} は、つながりロール {1}の使用に対して定義されていません。|
> |**名前**:<br />ConnectionTimeOut<br />**16 進数**:<br />80071024<br />**数値**:<br />-2147020764|ネットワーク接続がタイムアウトしたため、ドキュメントをコピーできません。後でもう一度試すか、システム管理者にお問い合わせください。|
> |**名前**:<br />ConnectorNotEnabled<br />**16 進数**:<br />80072600<br />**数値**:<br />-2147015168|コネクタの作成および編集が有効になっていません。|
> |**名前**:<br />ContactDoesNotExist<br />**16 進数**:<br />80040503<br />**数値**:<br />-2147220221|取引先担当者が存在しません。|
> |**名前**:<br />ContactLoopBeingCreated<br />**16 進数**:<br />8004050a<br />**数値**:<br />-2147220214|この上位下位の関連付けを作成すると、取引先担当者の階層にループが生成されます。|
> |**名前**:<br />ContactLoopExists<br />**16 進数**:<br />80040509<br />**数値**:<br />-2147220215|取引先担当者の階層にループが存在します。|
> |**名前**:<br />ContextIsNull<br />**16 進数**:<br />80060445<br />**数値**:<br />-2147089339|ビジネス プロセスの作成または更新時のエラー: コンテキストは Null にできません。|
> |**名前**:<br />ContractDetailDiscountAmount<br />**16 進数**:<br />80044413<br />**数値**:<br />-2147204077|契約の割引の種類で '割合' の割引がサポートされていません。|
> |**名前**:<br />ContractDetailDiscountAmountAndPercent<br />**16 進数**:<br />80044414<br />**数値**:<br />-2147204076|'金額' と '割合' の両方を設定することはできません。|
> |**名前**:<br />ContractDetailDiscountPercent<br />**16 進数**:<br />80044412<br />**数値**:<br />-2147204078|契約の割引の種類で '金額' の割引がサポートされていません。|
> |**名前**:<br />ContractInvalidAllotmentTypeCode<br />**16 進数**:<br />80043205<br />**数値**:<br />-2147208699|サービス単位のコードが無効です。|
> |**名前**:<br />ContractInvalidBillToAddress<br />**16 進数**:<br />8004320f<br />**数値**:<br />-2147208689|契約の請求先住所が無効です。|
> |**名前**:<br />ContractInvalidBillToCustomer<br />**16 進数**:<br />80043210<br />**数値**:<br />-2147208688|契約の請求先顧客が無効です。|
> |**名前**:<br />ContractInvalidContract<br />**16 進数**:<br />80043213<br />**数値**:<br />-2147208685|契約が無効です。|
> |**名前**:<br />ContractInvalidContractTemplate<br />**16 進数**:<br />80043211<br />**数値**:<br />-2147208687|契約テンプレートは無効です。|
> |**名前**:<br />ContractInvalidCustomer<br />**16 進数**:<br />8004320d<br />**数値**:<br />-2147208691|契約の顧客は無効です。|
> |**名前**:<br />ContractInvalidDatesForRenew<br />**16 進数**:<br />80043218<br />**数値**:<br />-2147208680|更新した契約の開始日または終了日は、同じ契約番号を持ち、請求書を作成済みか、アクティブな契約と重複することはできません。|
> |**名前**:<br />ContractInvalidDiscount<br />**16 進数**:<br />80044193<br />**数値**:<br />-2147204717|値引きが合計価格を超えることはできません。|
> |**名前**:<br />ContractInvalidPrice<br />**16 進数**:<br />80043215<br />**数値**:<br />-2147208683|価格は無効です。|
> |**名前**:<br />ContractInvalidServiceAddress<br />**16 進数**:<br />8004320e<br />**数値**:<br />-2147208690|契約のサービス住所が無効です。|
> |**名前**:<br />ContractInvalidStartEndDate<br />**16 進数**:<br />80043202<br />**数値**:<br />-2147208702|開始日 / 終了日または請求開始日 / 請求終了日が無効です。|
> |**名前**:<br />ContractInvalidState<br />**16 進数**:<br />80043203<br />**数値**:<br />-2147208701|契約の状態は無効です。|
> |**名前**:<br />ContractLineInvalidState<br />**16 進数**:<br />80043204<br />**数値**:<br />-2147208700|契約品目の状態は無効です。|
> |**名前**:<br />ContractNoLineItems<br />**16 進数**:<br />8004320c<br />**数値**:<br />-2147208692|この契約には契約品目がありません。|
> |**名前**:<br />ContractTemplateDoesNotExist<br />**16 進数**:<br />80043206<br />**数値**:<br />-2147208698|契約テンプレートが存在しません。|
> |**名前**:<br />ContractTemplateNoAbbreviation<br />**16 進数**:<br />8004320b<br />**数値**:<br />-2147208693|略名を NULL にすることはできません。|
> |**名前**:<br />ControlIdIsNotUnique<br />**16 進数**:<br />80060411<br />**数値**:<br />-2147089391|Xaml で コントロール ID {0} が一意ではありません。|
> |**名前**:<br />ControlIdIsNullOrEmpty<br />**16 進数**:<br />80072344<br />**数値**:<br />-2147015868|コントロール ID を Null または空にできません|
> |**名前**:<br />ConvertFetchDataSetError<br />**16 進数**:<br />8004832e<br />**数値**:<br />-2147187922|フェッチ データ セットの処理中に、予期しないエラーが発生しました。|
> |**名前**:<br />ConvertReportToCrmError<br />**16 進数**:<br />8004832d<br />**数値**:<br />-2147187923|指定されたレポートを Dynamics 365 形式への変換中に、予期しないエラーが発生しました。|
> |**名前**:<br />ConvertRuleActivateDeactivateByNonOwner<br />**16 進数**:<br />8004F886<br />**数値**:<br />-2147157882|この変換ルール セットをアクティブ化または非アクティブ化できるのは所有者だけです。|
> |**名前**:<br />ConvertRuleAlreadyActive<br />**16 進数**:<br />80060731<br />**数値**:<br />-2147088591|選択された ConvertRule は既にアクティブ状態です。 別のレコードを選択してからやり直してください|
> |**名前**:<br />ConvertRuleAlreadyInDraftState <br />**16 進数**:<br />80060732<br />**数値**:<br />-2147088590|選択された ConvertRule は既にドラフト状態です。 別のレコードを選択してからやり直してください|
> |**名前**:<br />ConvertRuleInvalidAutoResponseSettings<br />**16 進数**:<br />8004F879<br />**数値**:<br />-2147157895|自動応答用の電子メール テンプレートを選択するか、自動応答オプションを [いいえ] に設定してください。|
> |**名前**:<br />ConvertRulePermissionToPerformAction<br />**16 進数**:<br />80060733<br />**数値**:<br />-2147088589|ConvertRules およびプロセスに対してこの操作を実行するために必要なアクセス許可がありません。|
> |**名前**:<br />ConvertRuleQueueIdMissingForEmailSource<br />**16 進数**:<br />8004F896<br />**数値**:<br />-2147157866|キューの値が必要です。 キューに値を入力してください。|
> |**名前**:<br />ConvertRuleResponseTemplateValidity<br />**16 進数**:<br />80060730<br />**数値**:<br />-2147088592|グローバルまたはサポート案件のいずれかのテンプレートを選択してください。|
> |**名前**:<br />CopyGenericError<br />**16 進数**:<br />80071027<br />**数値**:<br />-2147020761|ファイルをコピーしているときにエラーが発生しました。 後でもう一度お試しください。 この問題が解決しない場合は、システム管理者にお問い合わせください。|
> |**名前**:<br />CopyNotAllowedForInternetMarketing<br />**16 進数**:<br />80048474<br />**数値**:<br />-2147187596|インターネット マーケティング キャンペーン活動を持つ重複のキャンペーンは許可されていません|
> |**名前**:<br />CorruptedHiddensheetData<br />**16 進数**:<br />800609B7<br />**数値**:<br />-2147087945|非表示シート データが破損しています。|
> |**名前**:<br />CouldNotDecryptOAuthToken<br />**16 進数**:<br />8005F110<br />**数値**:<br />-2147094256|Yammer OAuth トークンを暗号化解除できませんでした。 もう一度 Yammer の構成を再試行してください。|
> |**名前**:<br />CouldNotFindQueueItemInQueue<br />**16 進数**:<br />80040524<br />**数値**:<br />-2147220188|指定された SourceQueueId でターゲットと関連付けられているキュー アイテムが見つかりませんでした。 SourceQueueId または [ターゲット] が無効であるか、またはキュー アイテムが存在しないかのどちらかです。|
> |**名前**:<br />CouldNotObtainLockOnResource<br />**16 進数**:<br />80044339<br />**数値**:<br />-2147204295|データベース リソース ロックを取得できませんでした。 詳細については、「http://docs.microsoft.com/dynamics365/customer-engagement/customize/best-practices-workflow-processes#limit-the-number-of-workflows-that-update-the-same-entity」を参照してください。|
> |**名前**:<br />CouldNotReadAccessToken<br />**16 進数**:<br />8005F105<br />**数値**:<br />-2147094267|空でないコードが渡されましたが、システムがユーザーの Yammer アクセス トークンを読み込めませんでした。|
> |**名前**:<br />CouldNotSetLocationTypeToOneNote<br />**16 進数**:<br />80060905<br />**数値**:<br />-2147088123|ドキュメントの場所を表す場所の種類を OneNote に設定できません。|
> |**名前**:<br />CountSpecifiedWithoutOrder<br />**16 進数**:<br />8004E01F<br />**数値**:<br />-2147164129|ビジュアル化のデータ記述は、件数属性の受注ノードを指定していないため無効です。|
> |**名前**:<br />CreatePropertyError<br />**16 進数**:<br />8004F889<br />**数値**:<br />-2147157879|{0} プロパティの保存中にエラーが発生しました。|
> |**名前**:<br />CreatePropertyInstanceError<br />**16 進数**:<br />8004F890<br />**数値**:<br />-2147157872|{0} プロパティ インスタンスの保存中にエラーが発生しました。|
> |**名前**:<br />CreatePublishedWorkflowDefinitionWorkflowDependency<br />**16 進数**:<br />8004500A<br />**数値**:<br />-2147201014|公開されたワークフロー定義に対する、ワークフローの依存関係を作成することはできません。|
> |**名前**:<br />CreateRecurrenceRuleFailed<br />**16 進数**:<br />8004E101<br />**数値**:<br />-2147163903|定期的なアイテムのルールは作成できません。|
> |**名前**:<br />CreateWorkflowActivationWorkflowDependency<br />**16 進数**:<br />80045009<br />**数値**:<br />-2147201015|ワークフロー アクティベーションに関連付けられている、ワークフローの依存関係を作成することはできません。|
> |**名前**:<br />CreateWorkflowDependencyForPublishedTemplate<br />**16 進数**:<br />80045019<br />**数値**:<br />-2147200999|公開されたワークフロー テンプレートに対する、ワークフローの依存関係を作成することはできません。|
> |**名前**:<br />CrmConstraintEvaluationError<br />**16 進数**:<br />80040261<br />**数値**:<br />-2147220895|CRM 制約の評価エラーが発生しました。|
> |**名前**:<br />CrmConstraintParsingError<br />**16 進数**:<br />80040262<br />**数値**:<br />-2147220894|CRM 制約の解析エラーが発生しました。|
> |**名前**:<br />CrmExpressionBodyParsingError<br />**16 進数**:<br />8004025e<br />**数値**:<br />-2147220898|CRM 式本文の解析エラーが発生しました。|
> |**名前**:<br />CrmExpressionEvaluationError<br />**16 進数**:<br />80040260<br />**数値**:<br />-2147220896|CRM 式の評価エラーが発生しました。|
> |**名前**:<br />CrmExpressionParametersParsingError<br />**16 進数**:<br />8004025f<br />**数値**:<br />-2147220897|CRM 式パラメーターの解析エラーが発生しました。|
> |**名前**:<br />CrmExpressionParsingError<br />**16 進数**:<br />8004025d<br />**数値**:<br />-2147220899|CRM 式の解析エラーが発生しました。|
> |**名前**:<br />CrmHttpError<br />**16 進数**:<br />8006088A<br />**数値**:<br />-2147088246|Dynamics 365 の Web API でエラーが発生しました。|
> |**名前**:<br />CrmImpersonationError<br />**16 進数**:<br />80040245<br />**数値**:<br />-2147220923|CRM AutoReimpersonator でエラーが発生しました。|
> |**名前**:<br />CrmLiveAddOnAddLicenseLimitReached<br />**16 進数**:<br />8004B056<br />**数値**:<br />-2147176362|ご使用のサブスクリプションで、最大数のユーザー ライセンスを使用できます。  追加ライセンスについては、1-877-Dynamics 365-CHOICE (276-2464) で営業窓口にお問い合わせください。|
> |**名前**:<br />CrmLiveAddOnAddStorageLimitReached<br />**16 進数**:<br />8004B057<br />**数値**:<br />-2147176361|ストレージの消費量がこの環境に割り当てられた最大ストレージ制限に達しました。 試用環境には限られたリソースが割り当てられます。 試用版環境を使用していない場合は、サポートに連絡してください。|
> |**名前**:<br />CrmLiveAddOnDataChanged<br />**16 進数**:<br />8004B05C<br />**数値**:<br />-2147176356|アカウントに対して最近実行された変更により、この時点でこれらの変更を実行することはできません。   このウィザードを閉じて、後でやり直してください。  問題が続く場合は、1-877-Dynamics 365-CHOICE (276-2464) で営業窓口にお問い合わせください。|
> |**名前**:<br />CrmLiveAddOnOrgInNoUpdateMode<br />**16 進数**:<br />8004B059<br />**数値**:<br />-2147176359|変更をこの時点で処理することはできません。 お客様の組織は現在更新中です。  アカウントが変更されていません  このウィザードを閉じて、後でやり直してください。  問題が続く場合は、1-877-Dynamics 365-CHOICE (276-2464) で営業窓口にお問い合わせください。|
> |**名前**:<br />CrmLiveAddOnRemoveStorageLimitReached<br />**16 進数**:<br />8004B058<br />**数値**:<br />-2147176360|組織では最小限のストレージが許可されています。  組織に追加され、使用されていないストレージのみ削除できます。|
> |**名前**:<br />CrmLiveAddOnUnexpectedError<br />**16 進数**:<br />8004B055<br />**数値**:<br />-2147176363|請求システムへのアクセスでエラーが発生しました。  要求をこの時点で処理することはできません。  アカウントが変更されていません  このウィザードを閉じて、後でやり直してください。  問題が続く場合は、1-877-Dynamics 365-CHOICE (276-2464) で営業窓口にお問い合わせください。|
> |**名前**:<br />CrmLiveCannotFindExternalMessageProvider<br />**16 進数**:<br />8004B051<br />**数値**:<br />-2147176367|外部メッセージ プロバイダーは、キュー アイテムの種類: {0}に対して配置することができませんでした。|
> |**名前**:<br />CrmLiveDnsDomainAlreadyExists<br />**16 進数**:<br />8004B048<br />**数値**:<br />-2147176376|ドメインは、既に DNS テーブルに存在します。|
> |**名前**:<br />CrmLiveDnsDomainNotFound<br />**16 進数**:<br />8004B047<br />**数値**:<br />-2147176377|ドメインは、DNS テーブルで見つかりませんでした。|
> |**名前**:<br />CrmLiveDuplicateWindowsLiveId<br />**16 進数**:<br />8004B046<br />**数値**:<br />-2147176378|このユーザー名を持つユーザーが既に存在します。|
> |**名前**:<br />CrmLiveExecuteCustomCodeDisabled<br />**16 進数**:<br />8004B063<br />**数値**:<br />-2147176349|この組織に対するカスタム コード機能の実行が無効になります。|
> |**名前**:<br />CrmLiveGenericError<br />**16 進数**:<br />8004B000<br />**数値**:<br />-2147176448|要求の処理中にエラーが発生しました。|
> |**名前**:<br />CrmLiveInternalProvisioningError<br />**16 進数**:<br />8004B003<br />**数値**:<br />-2147176445|準備システムで予期しないエラーが発生しました。|
> |**名前**:<br />CrmLiveInvalidEmail<br />**16 進数**:<br />8004B05D<br />**数値**:<br />-2147176355|無効な電子メール アドレスが入力されました。|
> |**名前**:<br />CrmLiveInvalidExternalMessageData<br />**16 進数**:<br />8004B052<br />**数値**:<br />-2147176366|外部メッセージ データにはいくつかの無効なデータがあります。  データ: {0} 外部メッセージ: {1}|
> |**名前**:<br />CrmLiveInvalidInvoicingAccountNumber<br />**16 進数**:<br />8004B05B<br />**数値**:<br />-2147176357|この請求取引先企業番号は、無効な文字が含まれているため無効です。|
> |**名前**:<br />CrmLiveInvalidPhone<br />**16 進数**:<br />8004B05E<br />**数値**:<br />-2147176354|無効な電話番号が入力されました。|
> |**名前**:<br />CrmLiveInvalidQueueItemSchedule<br />**16 進数**:<br />8004B039<br />**数値**:<br />-2147176391|QueueItem に無効な開始日 {0} と終了日 {1} のスケジュールが含まれています。|
> |**名前**:<br />CrmLiveInvalidSetupParameter<br />**16 進数**:<br />8004B005<br />**数値**:<br />-2147176443|Dynamics 365 Online 設定へのパラメーターが、正しくないかまたは指定されていません。|
> |**名前**:<br />CrmLiveInvalidTaxId<br />**16 進数**:<br />8004B064<br />**数値**:<br />-2147176348|無効な TaxId が入力されました。|
> |**名前**:<br />CrmLiveInvalidZipCode<br />**16 進数**:<br />8004B05F<br />**数値**:<br />-2147176353|無効な郵便番号が入力されました。|
> |**名前**:<br />CrmLiveInvoicingAccountIdMissing<br />**16 進数**:<br />8004B045<br />**数値**:<br />-2147176379|sku の請求書に対して、取引先企業番号 (SAP ID) の請求書を空にすることはできません。|
> |**名前**:<br />CrmLiveMissingActiveDirectoryGroup<br />**16 進数**:<br />8004B002<br />**数値**:<br />-2147176446|指定された Active Directory グループが存在しません。|
> |**名前**:<br />CrmLiveMissingServerRolesInScaleGroup<br />**16 進数**:<br />8004B007<br />**数値**:<br />-2147176441|scalegroup には、必要なサーバー ロールがありません。 1 ミラーリング監視サーバーおよび 2 SQL Server がプロビジョニングに必要です。|
> |**名前**:<br />CrmLiveMonitoringOrganizationExistsInScaleGroup<br />**16 進数**:<br />8004B026<br />**数値**:<br />-2147176410|scalegroup では 1 つの監視組織のみ使用することができます。|
> |**名前**:<br />CrmLiveMultipleWitnessServersInScaleGroup<br />**16 進数**:<br />8004B006<br />**数値**:<br />-2147176442|ScaleGroup は指定された複数の監視サーバーを持っています。 1 つのスケール グループに、1 つの監視サーバーのみ設定できます。|
> |**名前**:<br />CrmLiveOrganizationDeleteFailed<br />**16 進数**:<br />8004B02E<br />**数値**:<br />-2147176402|組織を削除しているときにエラーが発生しました。|
> |**名前**:<br />CrmLiveOrganizationDetailsNotFound<br />**16 進数**:<br />8004B030<br />**数値**:<br />-2147176400|組織の詳細が見つかりません。|
> |**名前**:<br />CrmLiveOrganizationDisableFailed<br />**16 進数**:<br />8004B054<br />**数値**:<br />-2147176364|組織を無効にするのに失敗しました。|
> |**名前**:<br />CrmLiveOrganizationEnableFailed<br />**16 進数**:<br />8004B053<br />**数値**:<br />-2147176365|組織を有効にするのに失敗しました。|
> |**名前**:<br />CrmLiveOrganizationFriendlyNameTooLong<br />**16 進数**:<br />8004B032<br />**数値**:<br />-2147176398|指定された組織名が長すぎます。|
> |**名前**:<br />CrmLiveOrganizationFriendlyNameTooShort<br />**16 進数**:<br />8004B031<br />**数値**:<br />-2147176399|指定された組織名が短すぎます。|
> |**名前**:<br />CrmLiveOrganizationProvisioningFailed<br />**16 進数**:<br />8004B001<br />**数値**:<br />-2147176447|組織をプロビジョニングしているときにエラーが発生しました。|
> |**名前**:<br />CrmLiveOrganizationUniqueNameInvalid<br />**16 進数**:<br />8004B035<br />**数値**:<br />-2147176395|指定された一意の名前は無効です。|
> |**名前**:<br />CrmLiveOrganizationUniqueNameReserved<br />**16 進数**:<br />8004B036<br />**数値**:<br />-2147176394|一意の名前は既に使用されています。|
> |**名前**:<br />CrmLiveOrganizationUniqueNameTooLong<br />**16 進数**:<br />8004B034<br />**数値**:<br />-2147176396|指定された一意の名前が長すぎます。|
> |**名前**:<br />CrmLiveOrganizationUniqueNameTooShort<br />**16 進数**:<br />8004B033<br />**数値**:<br />-2147176397|指定された一意の名前が短すぎます。|
> |**名前**:<br />CrmLiveOrganizationUpgradeFailed<br />**16 進数**:<br />8004B014<br />**数値**:<br />-2147176428|Crm 組織のアップグレードに失敗しました。|
> |**名前**:<br />CrmLiveQueueItemDoesNotExist<br />**16 進数**:<br />8004B004<br />**数値**:<br />-2147176444|キューには、指定されたキュー アイテムが存在しません。 このアイテムは削除されたか、その ID が正しく指定されなかった可能性があります|
> |**名前**:<br />CrmLiveQueueItemTimeInPast<br />**16 進数**:<br />8004B040<br />**数値**:<br />-2147176384|QueueItem では、過去に開始または終了するようスケジュールすることができません。|
> |**名前**:<br />CrmLiveRegisterCustomCodeDisabled<br />**16 進数**:<br />8004B062<br />**数値**:<br />-2147176350|この組織に対するカスタム コード機能の登録が無効になります。|
> |**名前**:<br />CrmLiveServerCannotHaveWitnessAndDataServerRoles<br />**16 進数**:<br />8004B008<br />**数値**:<br />-2147176440|サーバーは、ミラーリング監視とデータ サーバー ロールの両方を持つことはできません。|
> |**名前**:<br />CrmLiveSupportOrganizationExistsInScaleGroup<br />**16 進数**:<br />8004B025<br />**数値**:<br />-2147176411|scalegroup では 1 つのサポート組織のみ使用することができます。|
> |**名前**:<br />CrmLiveUnknownCategory<br />**16 進数**:<br />8004B05A<br />**数値**:<br />-2147176358|この指定されたカテゴリは無効です。|
> |**名前**:<br />CrmLiveUnknownSku<br />**16 進数**:<br />8004B041<br />**数値**:<br />-2147176383|この指定された Sku は無効です。|
> |**名前**:<br />CrmMalformedExpressionError<br />**16 進数**:<br />8004025c<br />**数値**:<br />-2147220900|CRM 不正形式エラーが発生しました。|
> |**名前**:<br />CrmQueryExpressionNotInitialized<br />**16 進数**:<br />8004024d<br />**数値**:<br />-2147220915|QueryExpression は初期化されていません。 正しく初期化したインスタンスを作成するために、エンティティ名を含むコンストラクターを使用してください。|
> |**名前**:<br />CrmSecurityError<br />**16 進数**:<br />80040256<br />**数値**:<br />-2147220906|CrmSecurity でエラーが発生しました。|
> |**名前**:<br />CrmSQLCharLengthTooLong<br />**16 進数**:<br />80073001<br />**数値**:<br />-2147012607|検証エラーが発生しました。 提供された文字列値が長すぎます。|
> |**名前**:<br />CrmSqlGovernorDatabaseRequestDenied<br />**16 進数**:<br />8004A001<br />**数値**:<br />-2147180543|サーバーがビジー状態で、要求が完了しませんでした。 後でもう一度試してみてください。|
> |**名前**:<br />CrmSQLNetworkingError<br />**16 進数**:<br />80073000<br />**数値**:<br />-2147012608|ネットワーク エラーにより、この操作は失敗しました。 やり直してください。|
> |**名前**:<br />CrmSQLUniqueIndexOrConstraintViolation<br />**16 進数**:<br />80073002<br />**数値**:<br />-2147012606|操作が一意の制約を持つ属性に重複する値を挿入しようとしました。|
> |**名前**:<br />CRMUserDoesNotExist<br />**16 進数**:<br />80040354<br />**数値**:<br />-2147220652|指定したドメイン名とユーザー ID の Microsoft Dynamics 365 ユーザーが存在しません|
> |**名前**:<br />CrossEntityRelationshipInvalidOperation<br />**16 進数**:<br />80092006<br />**数値**:<br />-2146885626|複数のエンティティにまたがるステージ移行が無効です。 指定された関連付けは変更できません。|
> |**名前**:<br />CurrencyCannotBeNullDueToNonNullMoneyFields<br />**16 進数**:<br />80048cfb<br />**数値**:<br />-2147185413|通貨を null にすることはできません。|
> |**名前**:<br />CurrencyFieldMissing<br />**16 進数**:<br />8004E026<br />**数値**:<br />-2147164122|種類が通貨のロールアップ フィールドを計算する場合、レコード通貨が必要です。 通貨を指定してからやり直してください。|
> |**名前**:<br />CurrencyNotEqual<br />**16 進数**:<br />80048cea<br />**数値**:<br />-2147185430|{0} の通貨は、{1}の通貨に対応しません。|
> |**名前**:<br />CurrencyRequiredForDiscountTypeAmount<br />**16 進数**:<br />80048cf7<br />**数値**:<br />-2147185417|通貨は、割引の種類の金額に対して null にすることはできません。|
> |**名前**:<br />CustomActionMustBeMarked<br />**16 進数**:<br />80060381<br />**数値**:<br />-2147089535|BPF アクション ステップとして使用するには、カスタム アクションを「業務プロセス フローのアクション ステップとして」とマークする必要があります。|
> |**名前**:<br />CustomActivityCannotBeMailMergeEnabled<br />**16 進数**:<br />8004F124<br />**数値**:<br />-2147159772|活動として定義されているカスタム エンティティの差し込み印刷を有効にすることはできません。|
> |**名前**:<br />CustomActivityInvalid<br />**16 進数**:<br />8004501D<br />**数値**:<br />-2147200995|無効なユーザー定義の活動です。|
> |**名前**:<br />CustomActivityMustHaveOfflineAvailability<br />**16 進数**:<br />8004F122<br />**数値**:<br />-2147159774|活動として定義されたユーザー定義エンティティは、オフラインで使用できるようにする必要があります。|
> |**名前**:<br />CustomControlsDependentPropertyConfiguration<br />**16 進数**:<br />80160002<br />**数値**:<br />-2146041854|プロパティ "{0}" は、プロパティ "{1}" に値が割り当てられた後にのみ構成できます。|
> |**名前**:<br />CustomControlsImportError<br />**16 進数**:<br />80160000<br />**数値**:<br />-2146041856|カスタム コントロールのインポート中にエラーが発生しました。 このソリューションをインポートし直してください。|
> |**名前**:<br />CustomControlsPropertySetConfiguration<br />**16 進数**:<br />80160003<br />**数値**:<br />-2146041853|プロパティ "{0}" は、対応するデータセット "{1}" ビューに値が割り当てられないと、構成できません。|
> |**名前**:<br />CustomerIsInactive<br />**16 進数**:<br />80040517<br />**数値**:<br />-2147220201|非アクティブな顧客は、オブジェクトの親として設定できません。|
> |**名前**:<br />CustomerOpportunityRoleExists<br />**16 進数**:<br />80048202<br />**数値**:<br />-2147188222|顧客営業案件ロールが存在します。|
> |**名前**:<br />CustomerRelationshipCannotBeDeleted<br />**16 進数**:<br />8004847d<br />**数値**:<br />-2147187587|この関連付け {1} は {0} 属性によって要求されており、削除できません。 この関連付けを削除するには、検索属性を先に削除してください。|
> |**名前**:<br />CustomerRelationshipExists<br />**16 進数**:<br />80048201<br />**数値**:<br />-2147188223|顧客リレーションシップは既に存在します。|
> |**名前**:<br />CustomImageAttributeOnlyAllowedOnCustomEntity<br />**16 進数**:<br />80048531<br />**数値**:<br />-2147187407|ユーザー定義のイメージ属性は、ユーザー定義エンティティのみに追加することができます。|
> |**名前**:<br />CustomOperationNotActivated<br />**16 進数**:<br />80045052<br />**数値**:<br />-2147200942|このプロセスに関連付けられたプロセス アクションがアクティブ化されていません。|
> |**名前**:<br />CustomParentingSystemNotSupported<br />**16 進数**:<br />80047102<br />**数値**:<br />-2147192574|ユーザー定義エンティティは、システム エンティティとの上位関係で関連付けられていません|
> |**名前**:<br />CustomPeriodGoalHavingExtraInfo<br />**16 進数**:<br />80044904<br />**数値**:<br />-2147202812|カスタム期間型の目標の場合、会計年度および会計期間属性は空白のままである必要があります。|
> |**名前**:<br />CustomPeriodGoalMissingInfo<br />**16 進数**:<br />80044907<br />**数値**:<br />-2147202809|カスタム期間型の目標の場合、goalstartdate と goalenddate 属性にデータを設定する必要があります。|
> |**名前**:<br />CustomReflexiveRelationshipNotAllowedForEntity<br />**16 進数**:<br />8004432C<br />**数値**:<br />-2147204308|このエンティティはユーザー定義の再帰関係では無効です|
> |**名前**:<br />CustomWorkflowActivitiesNotSupported<br />**16 進数**:<br />80045051<br />**数値**:<br />-2147200943|ユーザー定義のワークフロー活動は有効ではありません。|
> |**名前**:<br />CyclicalRelationship<br />**16 進数**:<br />80047004<br />**数値**:<br />-2147192828|指定した関連付けでサイクルが発生します。|
> |**名前**:<br />CyclicDependency<br />**16 進数**:<br />80071156<br />**数値**:<br />-2147020458|循環コンポーネント依存関係が検出されました。 詳細については例外を確認してください。 無効な依存関係を修正して、もう一度操作を試行してください。 詳細: {0}|
> |**名前**:<br />CyclicReferencesNotSupported<br />**16 進数**:<br />8004417F<br />**数値**:<br />-2147204737|入力には循環参照を含んでおり、サポートされていません。|
> |**名前**:<br />DatabaseCallsBlockedFailure<br />**16 進数**:<br />80072401<br />**数値**:<br />-2147015679|この呼び出しで許可されていないデータベースへの呼び出しが発生する可能性があります。|
> |**名前**:<br />DatacenterNotAvailable<br />**16 進数**:<br />8004B065<br />**数値**:<br />-2147176347|このデータセンター エンドポイントは、現在この組織では利用できません。|
> |**名前**:<br />DataColumnsNumberMismatch<br />**16 進数**:<br />80040345<br />**数値**:<br />-2147220667|フィールドの数が列見出しの数と異なります。|
> |**名前**:<br />DataEngineQueryThrottling<br />**16 進数**:<br />80048544<br />**数値**:<br />-2147187388|このクエリは調整の最適化と競合するため実行できません。|
> |**名前**:<br />DatafieldNameShouldBeNull<br />**16 進数**:<br />8006041b<br />**数値**:<br />-2147089381|ActionStep {0} が無効な DataFieldName {1} を参照しています。|
> |**名前**:<br />DataMigrationManagerMandatoryUpdatesNotInstalled<br />**16 進数**:<br />80044336<br />**数値**:<br />-2147204298|データ移行マネージャの初めての構成が取り消されました。 構成が完了するまで、データ移行マネージャは使用できません。|
> |**名前**:<br />DataMigrationManagerUnknownProblem<br />**16 進数**:<br />80044333<br />**数値**:<br />-2147204301|データ移行マネージャで不明なエラーが発生したため続行できません。 やり直すには、データ移行マネージャを再起動します。|
> |**名前**:<br />DatasheetNotAvailable<br />**16 進数**:<br />800609B5<br />**数値**:<br />-2147087947|データ シートを使用できません。|
> |**名前**:<br />DataSourceInitializeFailedErrorCode<br />**16 進数**:<br />8005F210<br />**数値**:<br />-2147094000|このアクションをやり直してください。 問題が解決しない場合は、ソリューションの {0} を確認するか、{#Brand_CRM} 管理者に問い合わせてください。 それでも解決しない場合には {1}に問い合わせてください。|
> |**名前**:<br />DataSourceOfflineErrorCode<br />**16 進数**:<br />8005F211<br />**数値**:<br />-2147093999|オフラインのため、この操作に失敗しました。 再接続してからやり直してください。|
> |**名前**:<br />DataSourceProhibited<br />**16 進数**:<br />8004830D<br />**数値**:<br />-2147187955|フェッチ ベース以外のデータ ソースは、このレポートで使用できません|
> |**名前**:<br />DataStoreKeyNotFoundErrorCode<br />**16 進数**:<br />8005F21d<br />**数値**:<br />-2147093987|キー '{0}' 付きのローカル ストアにはありません|
> |**名前**:<br />DataSyncNoContent<br />**16 進数**:<br />80072512<br />**数値**:<br />-2147015406|データ同期コンテンツがありません|
> |**名前**:<br />DataSyncRequestAccepted<br />**16 進数**:<br />80072511<br />**数値**:<br />-2147015407|データ同期要求を受理しました|
> |**名前**:<br />DataTableNotAvailable<br />**16 進数**:<br />800609B0<br />**数値**:<br />-2147087952|元のデータ テーブルが、削除または名前変更されています。|
> |**名前**:<br />DataTypeMismatchForLinkedAttribute<br />**16 進数**:<br />8004F0FC<br />**数値**:<br />-2147159812|リンクされた属性で、データ タイプの不一致が見つかりました。|
> |**名前**:<br />DateTimeFormatFailed<br />**16 進数**:<br />8004025a<br />**数値**:<br />-2147220902|書式設定された日時の値を生成できませんでした。|
> |**名前**:<br />DecimalValueOutOfRange<br />**16 進数**:<br />80044330<br />**数値**:<br />-2147204304|検証エラーが発生しました。 入力した 10 進数値が、この属性に対して許可された値の範囲外です。|
> |**名前**:<br />DecoupleChildEntity<br />**16 進数**:<br />80048206<br />**数値**:<br />-2147188218|子エンティティを分離することはできません。|
> |**名前**:<br />DecoupleUserOwnedEntity<br />**16 進数**:<br />80048207<br />**数値**:<br />-2147188217|ユーザーが所有するエンティティを分離することができるのみです。|
> |**名前**:<br />DecreasingDaysWillDeleteOlderData<br />**16 進数**:<br />80060992<br />**数値**:<br />-2147087982|日数を減らすと、指定した日数より前の Mobile Offline データが削除されます。|
> |**名前**:<br />DefaultSiteCollectionUrlChanged<br />**16 進数**:<br />8004F100<br />**数値**:<br />-2147159808|この操作が作成された後、既定のサイト コレクション URL がこの組織に変更されました。|
> |**名前**:<br />DefaultSiteMapDeleteFailure<br />**16 進数**:<br />80048070<br />**数値**:<br />-2147188624|既定のサイト マップは削除できません。|
> |**名前**:<br />DelegatedAdminUserCannotBeCreateNorUpdated<br />**16 進数**:<br />80041d67<br />**数値**:<br />-2147213977|代理管理者ユーザーは更新できません|
> |**名前**:<br />DeleteActiveWorkflowTemplateDependency<br />**16 進数**:<br />8004501A<br />**数値**:<br />-2147200998|公開されたワークフロー テンプレートから、ワークフローの依存関係を削除することはできません。|
> |**名前**:<br />DeletePublishedWorkflowDefinitionWorkflowDependency<br />**16 進数**:<br />80045006<br />**数値**:<br />-2147201018|公開されたワークフロー定義に対する、ワークフローの依存関係を削除することはできません。|
> |**名前**:<br />DeleteWorkflowActivation<br />**16 進数**:<br />80045004<br />**数値**:<br />-2147201020|ワークフローのアクティブ化は削除できません。|
> |**名前**:<br />DeleteWorkflowActivationWorkflowDependency<br />**16 進数**:<br />80045005<br />**数値**:<br />-2147201019|ワークフローのアクティブ化に関連付けられている、ワークフローの依存関係を削除することはできません。|
> |**名前**:<br />DeleteWorkflowActiveDefinition<br />**16 進数**:<br />8004500F<br />**数値**:<br />-2147201009|アクティブなワークフローの定義を削除することはできません。|
> |**名前**:<br />DeleteWorkflowActiveTemplate<br />**16 進数**:<br />8004501C<br />**数値**:<br />-2147200996|アクティブなワークフロー テンプレートを削除することはできません。|
> |**名前**:<br />DelveActionHubAttributeMissingInResponseException<br />**16 進数**:<br />80071002<br />**数値**:<br />-2147020798|Exchange の oData 応答に属性が存在しません。|
> |**名前**:<br />DelveActionHubAuthorizationFailureException<br />**16 進数**:<br />80071007<br />**数値**:<br />-2147020793|アクションを表示するための適切な Office 365 ライセンスがありません。 システム管理者にお問い合わせください。|
> |**名前**:<br />DelveActionHubDisabledError<br />**16 進数**:<br />80071000<br />**数値**:<br />-2147020800|Delve アクション ハブ機能が有効になっていません。|
> |**名前**:<br />DelveActionHubInvalidResponseFormatException<br />**16 進数**:<br />80071004<br />**数値**:<br />-2147020796|応答形式が無効です。|
> |**名前**:<br />DelveActionHubInvalidStateCodeException<br />**16 進数**:<br />80071003<br />**数値**:<br />-2147020797|無効な状態コードが条件式に渡されました。|
> |**名前**:<br />DelveActionHubResponseRetievalFailureException<br />**16 進数**:<br />80071005<br />**数値**:<br />-2147020795|Exchange からアクションをフェッチ中にエラーが発生しました。|
> |**名前**:<br />DelveActionHubS2SSetupFailureException<br />**16 進数**:<br />80071008<br />**数値**:<br />-2147020792|Exchange による Delve アクション ハブ用のサーバー間認証が設定されていません。|
> |**名前**:<br />DependencyAlreadyExists<br />**16 進数**:<br />8004F01A<br />**数値**:<br />-2147160038|{0} 依存関係は既に {1}({2}) および {3}({4}) 間で存在しています。  {5} 依存関係を作成することもできません。|
> |**名前**:<br />DependencyTableNotEmpty<br />**16 進数**:<br />8004F01B<br />**数値**:<br />-2147160037|依存関係テーブルが正常に完了するため、初期化の時点で空である必要があります。|
> |**名前**:<br />DependencyTrackingClosed<br />**16 進数**:<br />8004F025<br />**数値**:<br />-2147160027|現在のトランザクション コンテキストより後の依存関係を処理する、無効な試みはクローズされました。|
> |**名前**:<br />DeploymentServiceCannotChangeStateForDeploymentService<br />**16 進数**:<br />8004D262<br />**数値**:<br />-2147167646|展開サービス サーバー ロールが含まれているため、このサーバーの状態を変更することはできません。|
> |**名前**:<br />DeploymentServiceCannotDeleteOperationInProgress<br />**16 進数**:<br />8004D265<br />**数値**:<br />-2147167643|現在処理中のため、展開サービスは指定した操作を削除できません。|
> |**名前**:<br />DeploymentServiceNotAllowOperation<br />**16 進数**:<br />8004D261<br />**数値**:<br />-2147167647|{0} の展開サービスは、{1} 操作を許可していません。|
> |**名前**:<br />DeploymentServiceNotAllowSetToThisState<br />**16 進数**:<br />8004D260<br />**数値**:<br />-2147167648|{0} の展開サービスは、[有効] または [無効] の状態を許可します。 状態を {1} に設定することはできません。|
> |**名前**:<br />DeploymentServiceOperationIdentifierNotFound<br />**16 進数**:<br />8004D264<br />**数値**:<br />-2147167644|展開サービスは指定した識別子を持つ遅延操作を見つけることができませんでした。|
> |**名前**:<br />DeploymentServiceRequestValidationFailure<br />**16 進数**:<br />8004D263<br />**数値**:<br />-2147167645|1 つ以上の検証チェックに失敗したため、展開サービスは要求を処理できません。|
> |**名前**:<br />DeprecatedFormActivation<br />**16 進数**:<br />8004F662<br />**数値**:<br />-2147158430|このフォームは以前のリリースで廃止されており、もう使用できません。 変更内容を別のフォームに移行してください。 廃止予定のフォームは将来的にシステムから削除されます。|
> |**名前**:<br />DeprecatedMobileFormsCreation<br />**16 進数**:<br />8004F667<br />**数値**:<br />-2147158425|モバイル フォームは廃止されました。 新しい Mobile Express フォームを作成できません。|
> |**名前**:<br />DeprecatedMobileFormsEdit<br />**16 進数**:<br />8004F668<br />**数値**:<br />-2147158424|モバイル フォームは廃止されました。 モバイル フォーム エディターを開けません。|
> |**名前**:<br />DeprovisionRIAccessNotAllowed<br />**16 進数**:<br />80044274<br />**数値**:<br />-2147204492|リレーションシップ インサイトは、システム管理者だけが無効にすることができます。|
> |**名前**:<br />DesignerAccessDenied<br />**16 進数**:<br />80050100<br />**数値**:<br />-2147155712|要求された操作を実行するための十分な特権がありません。 詳細については、管理者に問い合わせてください。|
> |**名前**:<br />DesignerInvalidParameter<br />**16 進数**:<br />80050101<br />**数値**:<br />-2147155711|指定された {0} は正しくないか、欠落しています。 正しい {1} でやり直してください。|
> |**名前**:<br />DestinationFolderNotExists<br />**16 進数**:<br />80071022<br />**数値**:<br />-2147020766|ドキュメントをコピーできません。 コピー先のドキュメントの場所が存在しません。|
> |**名前**:<br />DialogNameCannotBeNull<br />**16 進数**:<br />80060873<br />**数値**:<br />-2147088269|"DialogName は、ダイアログを入力する際 null にすることはできません|
> |**名前**:<br />DisabledCRMAddinLoadFailure<br />**16 進数**:<br />80044202<br />**数値**:<br />-2147204606|Microsoft Dynamics 365 機能の読み込み中にエラーが発生しました。 Outlook を再起動してください。 問題が解決しない場合は、システム管理者に問い合わせてください。|
> |**名前**:<br />DisabledCRMClientVersionHigher<br />**16 進数**:<br />80044204<br />**数値**:<br />-2147204604|Microsoft Dynamics 365 のクライアントを使用する前に、Microsoft Dynamics 365 Server のアップグレードが必要です。 迅速なサポートが必要な場合、システム管理者に支援を依頼してください。|
> |**名前**:<br />DisabledCRMClientVersionLower<br />**16 進数**:<br />80044203<br />**数値**:<br />-2147204605|この Microsoft Dynamics 365 組織 {0} でオフライン モードをサポートしていない Microsoft Dynamics 365 for Outlook のバージョンを実行しています。 互換性のあるバージョンの Dynamics 365 for Outlook にアップグレードする必要があります。 現在のバージョンの Dynamics 365 for Outlook が、互換性のあるバージョンへのアップグレードの対象としてサポートされていることを確認してください。|
> |**名前**:<br />DisabledCRMGoingOffline<br />**16 進数**:<br />80044200<br />**数値**:<br />-2147204608|オフライン同期の発生中に Microsoft Dynamics 365 の機能を使用できません。|
> |**名前**:<br />DisabledCRMGoingOnline<br />**16 進数**:<br />80044201<br />**数値**:<br />-2147204607|オンライン同期の発生中に Microsoft Dynamics 365 の機能を使用できません。|
> |**名前**:<br />DisabledCRMOnlineCrmNotAvailable<br />**16 進数**:<br />80044206<br />**数値**:<br />-2147204602|Microsoft Dynamics 365 Server を使用できません。|
> |**名前**:<br />DisabledCRMPostOfflineUpgrade<br />**16 進数**:<br />80044205<br />**数値**:<br />-2147204603|Microsoft Dynamics 365 クライアントがオンラインに戻るまで、Microsoft Dynamics 365 の機能を使用できません。|
> |**名前**:<br />DisableRIFeatureNotAllowed<br />**16 進数**:<br />80044280<br />**数値**:<br />-2147204480|組織に対してリレーションシップ インサイトを無効にするには、システム管理者特権が必要です。|
> |**名前**:<br />DiscountAmount<br />**16 進数**:<br />80043b20<br />**数値**:<br />-2147206368|割引の種類で '割合' の割引がサポートされていません。|
> |**名前**:<br />DiscountAmountAndPercent<br />**16 進数**:<br />80043b1f<br />**数値**:<br />-2147206369|'金額' と '割合' の両方を設定することはできません。|
> |**名前**:<br />DiscountPercent<br />**16 進数**:<br />80043b21<br />**数値**:<br />-2147206367|割引の種類で '金額' の割引がサポートされていません。|
> |**名前**:<br />DiscountRangeOverlap<br />**16 進数**:<br />80043b02<br />**数値**:<br />-2147206398|新しい数量が、既存の数量により扱われる範囲に重なっています。|
> |**名前**:<br />DiscountTypeAndPriceLevelCurrencyNotEqual<br />**16 進数**:<br />80048cf8<br />**数値**:<br />-2147185416|割引の通貨は、割引の種類の金額に対する価格表の通貨に一致する必要があります。|
> |**名前**:<br />DiskSpaceNotEnough<br />**16 進数**:<br />80050124<br />**数値**:<br />-2147155676|Temp フォルダーに十分なスペースがありません。|
> |**名前**:<br />DistributeListAssociatedVary<br />**16 進数**:<br />80048453<br />**数値**:<br />-2147187629|このキャンペーン活動は配布できません。 差し込み印刷活動は、すべてのレコードの種類が同一のマーケティング リストでのみ実行できます。 このキャンペーン活動では、マーケティング リストを削除することによりその他が同じレコードの種類になるようにし、もう一度やり直してください。|
> |**名前**:<br />DistributeNoListAssociated<br />**16 進数**:<br />80048454<br />**数値**:<br />-2147187628|このキャンペーン活動は配布できません。 関連付けられたマーケティング リストがありません。 マーケティング リストを少なくとも 1 つ追加てからやり直してください。|
> |**名前**:<br />DocumentManagementDisabled<br />**16 進数**:<br />8004F0FF<br />**数値**:<br />-2147159809|この組織ではドキュメント管理が無効になっています。|
> |**名前**:<br />DocumentManagementDisabledForEmail<br />**16 進数**:<br />80050010<br />**数値**:<br />-2147155952|添付ファイルをフォローするには、電子メール エンティティに対してドキュメント管理を有効にする必要があります。 ドキュメント管理を有効にするために管理者にお問い合わせください。|
> |**名前**:<br />DocumentManagementDisabledOnEntity<br />**16 進数**:<br />80060908<br />**数値**:<br />-2147088120|OneNote 統合を有効にするには、このエンティティに対してドキュメント管理を有効にする必要があります。|
> |**名前**:<br />DocumentManagementIsDisabled<br />**16 進数**:<br />8004F312<br />**数値**:<br />-2147159278|この組織に対するドキュメント管理が有効になっていません。|
> |**名前**:<br />DocumentManagementIsDisabledOnEntity<br />**16 進数**:<br />80071011<br />**数値**:<br />-2147020783|ドキュメント レコメンデーションを有効にするには、このエンティティに対してドキュメント管理を有効にする必要があります。|
> |**名前**:<br />DocumentManagementNotEnabledNoPrimaryField<br />**16 進数**:<br />8004F313<br />**数値**:<br />-2147159277|名前 {0} id {1} のこのエンティティにプライマリ フィールドが定義されていないため、ドキュメント管理を有効にできませんでした。|
> |**名前**:<br />DocumentRecommendationsFCBOff<br />**16 進数**:<br />80071019<br />**数値**:<br />-2147020775|ドキュメント サジェスチョン機能が有効になっていません。|
> |**名前**:<br />DocumentTemplateFeatureNotEnabled<br />**16 進数**:<br />800608C9<br />**数値**:<br />-2147088183|ドキュメント テンプレート機能が有効になっていません。|
> |**名前**:<br />DocxExportGeneratingWordFailed<br />**16 進数**:<br />800608CD<br />**数値**:<br />-2147088179|Word 文書の生成中にエラーが発生しました。 やり直してください。|
> |**名前**:<br />DocxValidationFailed<br />**16 進数**:<br />800608CE<br />**数値**:<br />-2147088178|選択されたファイルがテンプレート レイアウトと一致しないため、アップロードに失敗しました。 テンプレート レイアウトのファイルを選択してもう一度お試しください。|
> |**名前**:<br />DoNotTrackItem<br />**16 進数**:<br />80044228<br />**数値**:<br />-2147204568|選択されているアイテムは追跡できません。|
> |**名前**:<br />DownloadAllEntityRecordsChangedOrCreatedWithinTheseDays<br />**16 進数**:<br />8006098F<br />**数値**:<br />-2147087985|この日数内で変更または作成されたすべてのエンティティ レコードをダウンロードします。|
> |**名前**:<br />DownloadRelatedDataOnlyMustHaveRelationship<br />**16 進数**:<br />80071140<br />**数値**:<br />-2147020480|プロファイル '{1}' のエンティティ '{0}' は、フィルター ダウンロード関連のデータのみで構成されています。ただし、プロファイル項目の関連付けでこのエンティティに指定された関係はありません。 エンティティが関連データのみをダウンロードするように設定されている場合は、このエンティティへのプロファイル項目の関連付けを指定する必要があります。|
> |**名前**:<br />DraftBundleToProduct<br />**16 進数**:<br />8004F994<br />**数値**:<br />-2147157612|ドラフト バンドルには、製品のみを追加できます。|
> |**名前**:<br />DuplicateAliasFound<br />**16 進数**:<br />8004E00B<br />**数値**:<br />-2147164149|データの説明が無効です。 重複したエイリアスが見つかりました。|
> |**名前**:<br />DuplicateApplicationUser<br />**16 進数**:<br />8004F511<br />**数値**:<br />-2147158767|既に存在するアプリケーション ID = {0} を作成しようとしています。|
> |**名前**:<br />DuplicateAppModuleUniqueName<br />**16 進数**:<br />8005011F<br />**数値**:<br />-2147155681|入力された名前は既に使用されています。|
> |**名前**:<br />DuplicateAttributePhysicalName<br />**16 進数**:<br />80060304<br />**数値**:<br />-2147089660|エンティティ {1} の属性 {0} は既に存在します。|
> |**名前**:<br />DuplicateAttributeSchemaName<br />**16 進数**:<br />80047013<br />**数値**:<br />-2147192813|指定された名前の属性は既に存在しています|
> |**名前**:<br />DuplicateChannelPropertyName<br />**16 進数**:<br />800608F1<br />**数値**:<br />-2147088143|チャネル プロパティは指定された名前で既に存在しています。 もう 1 つ作成することはできません。|
> |**名前**:<br />DuplicateCheckNotEnabled<br />**16 進数**:<br />80048412<br />**数値**:<br />-2147187694|重複データ検出が有効になっていません。 重複データ検出を有効にするには、[設定] をクリックし、[データ管理] をクリックしてから [重複データ検出設定] をクリックします。|
> |**名前**:<br />DuplicateCheckNotSupportedOnEntity<br />**16 進数**:<br />80048410<br />**数値**:<br />-2147187696|重複データ検出は、このレコードの種類ではサポートされません。|
> |**名前**:<br />DuplicateComponentInSolutionXml<br />**16 進数**:<br />80071153<br />**数値**:<br />-2147020461|XML に重複コンポーネントがあります。|
> |**名前**:<br />DuplicateDetectionNotSupportedOnAttributeType<br />**16 進数**:<br />80048430<br />**数値**:<br />-2147187664|重複データ検出が選択した属性のデータの種類でサポートされていないため、ルールの条件を作成または更新することはできません。|
> |**名前**:<br />DuplicateDetectionRulesWereUnpublished<br />**16 進数**:<br />8004F039<br />**数値**:<br />-2147160007|おそらくエンティティが変更されているため、このエンティティの重複データ検出ルールが公開されていません。|
> |**名前**:<br />DuplicateDetectionTemplateNotFound<br />**16 進数**:<br />80048424<br />**数値**:<br />-2147187676|Microsoft Dynamics 365 が電子メール通知テンプレートを取得できませんでした。|
> |**名前**:<br />DuplicateDisplayCollectionName<br />**16 進数**:<br />80047012<br />**数値**:<br />-2147192814|特定の表示コレクション名を持つオブジェクトは既に存在します。|
> |**名前**:<br />DuplicateDisplayName<br />**16 進数**:<br />80047011<br />**数値**:<br />-2147192815|特定の表示名を持つオブジェクトは既に存在します。|
> |**名前**:<br />DuplicatedJobId<br />**16 進数**:<br />80071152<br />**数値**:<br />-2147020462|パラメーター ImportJobId は一意である必要があります。|
> |**名前**:<br />DuplicatedJobIdDueToConcurrency<br />**16 進数**:<br />80071155<br />**数値**:<br />-2147020459|既に使用されているため、提供された JobId ({0}) を使用してソリューション ジョブを作成できません。 これは別のソリューション操作が進行中であることを示す場合があります。 後でやり直してください。|
> |**名前**:<br />DuplicatedPrivilege<br />**16 進数**:<br />8004140f<br />**数値**:<br />-2147216369|特権 {0} が重複しています。|
> |**名前**:<br />DuplicateFileNamesInZip<br />**16 進数**:<br />80048484<br />**数値**:<br />-2147187580|2 つ以上のファイルが同じ名前です。 ファイル名は一意である必要があります。|
> |**名前**:<br />DuplicateGroupByFound<br />**16 進数**:<br />8004E01B<br />**数値**:<br />-2147164133|データの説明が無効です。 同じ属性をグループとして複数回使用することはできません。|
> |**名前**:<br />DuplicateHeaderColumn<br />**16 進数**:<br />80040338<br />**数値**:<br />-2147220680|重複する列見出しが存在します。|
> |**名前**:<br />DuplicateIsoCurrencyCode<br />**16 進数**:<br />80048cf3<br />**数値**:<br />-2147185421|重複した通貨レコードを挿入することはできません。 同じ通貨コードを持つ通貨は、既にシステムに存在します。|
> |**名前**:<br />DuplicateLookupFound<br />**16 進数**:<br />80040352<br />**数値**:<br />-2147220654|重複する参照が検出されました|
> |**名前**:<br />DuplicateMapName<br />**16 進数**:<br />80048443<br />**数値**:<br />-2147187645|指定した名前のデータ マップは既に存在します。|
> |**名前**:<br />DuplicateName<br />**16 進数**:<br />80047010<br />**数値**:<br />-2147192816|特定の名前を持つオブジェクトは既に存在します|
> |**名前**:<br />DuplicateOfflineFilter<br />**16 進数**:<br />80048449<br />**数値**:<br />-2147187639|1 つのレコードの種類につき、ローカル データ グループを 1 つだけ作成できます。|
> |**名前**:<br />DuplicateOutlookAppointment<br />**16 進数**:<br />80040274<br />**数値**:<br />-2147220876|Outlook から登録された予定は Dynamics 365 ですでに追跡中です。|
> |**名前**:<br />DuplicatePrimaryNameAttribute<br />**16 進数**:<br />8004701E<br />**数値**:<br />-2147192802|新しい {2} 属性は {1} エンティティののプライマリ名属性として設定されます。 {1} エンティティでは {0} 属性がプライマリ名属性として既に設定されています。 1 つのエンティティに設定できるプライマリ名属性は 1 つのみです。|
> |**名前**:<br />DuplicatePrivilegeInRolecontrol<br />**16 進数**:<br />80061118<br />**数値**:<br />-2147086056|チャネル アクセス プロファイル特権配列に重複した特権参照が含まれています。|
> |**名前**:<br />DuplicateProductPriceLevel<br />**16 進数**:<br />80043b08<br />**数値**:<br />-2147206392|この製品と出荷単位の組み合わせは、この価格表に価格が存在します。|
> |**名前**:<br />DuplicateProductRelationship<br />**16 進数**:<br />8004F891<br />**数値**:<br />-2147157871|同じ製品および関連製品との製品関係が既に存在します。|
> |**名前**:<br />DuplicateRecord<br />**16 進数**:<br />80040237<br />**数値**:<br />-2147220937|SQL の整合性の違反により操作は失敗しました。|
> |**名前**:<br />DuplicateRecordEntityKey<br />**16 進数**:<br />80060892<br />**数値**:<br />-2147088238|エンティティ キー {0} が違反しました。 {1} の同じ値を持つレコードが既に存在しています。 重複レコードは作成できません。 1 つ以上の一意の値を選択してから、やり直してください。|
> |**名前**:<br />DuplicateRecordsFound<br />**16 進数**:<br />80040333<br />**数値**:<br />-2147220685|現在のレコードに対する重複レコードが既に存在するため、レコードは作成または更新されませんでした。|
> |**名前**:<br />DuplicateReportVisibility<br />**16 進数**:<br />80040495<br />**数値**:<br />-2147220331|同じ ReportId および VisibilityCode の ReportVisibility が既に存在しています。 重複は許可されていません。|
> |**名前**:<br />DuplicateSalesTeamMember<br />**16 進数**:<br />80048341<br />**数値**:<br />-2147187903|追加しようとしているユーザーは、既に営業チームのメンバーです。|
> |**名前**:<br />DuplicateUIStatementRootsFound<br />**16 進数**:<br />8004F201<br />**数値**:<br />-2147159551|指定された uniscript には 1 つのルート文しか設定できません。|
> |**名前**:<br />DynamicPropertyDefaultValueNeeded<br />**16 進数**:<br />80061038<br />**数値**:<br />-2147086280|このプロパティは必須で読み取り専用であるため、既定値を指定する必要があります。|
> |**名前**:<br />DynamicPropertyInstanceMissingRequiredColumns<br />**16 進数**:<br />8008100A<br />**数値**:<br />-2146955254|プロパティ インスタンスを更新することはできません。 次のフィールドがあることを確認してください: dynamicpropertyid、dynamicpropertyoptionsetvalueid、および regardingobjectid。|
> |**名前**:<br />DynamicPropertyInstanceUpdateValuesDifferentRegarding<br />**16 進数**:<br />8008100B<br />**数値**:<br />-2146955253|さまざまな製品品目を参照するため、プロパティ インスタンスは保存することができませんでした。|
> |**名前**:<br />DynamicPropertyInvalidRegardingForUpdate<br />**16 進数**:<br />80081004<br />**数値**:<br />-2146955260|公開済みか、または廃止された製品のプロパティを作成または変更することはできません。|
> |**名前**:<br />DynamicPropertyInvalidStateChange<br />**16 進数**:<br />80081001<br />**数値**:<br />-2146955263|非アクティブなプロパティをアクティブ状態に設定することはできません。|
> |**名前**:<br />DynamicPropertyInvalidStateForDelete<br />**16 進数**:<br />80081002<br />**数値**:<br />-2146955262|アクティブ状態のプロパティを削除することはできません。|
> |**名前**:<br />DynamicPropertyInvalidStateForUpdate<br />**16 進数**:<br />80081000<br />**数値**:<br />-2146955264|下書き状態ではないプロパティを更新することはできません。|
> |**名前**:<br />DynamicPropertyOptionSetInvalidStateForUpdate<br />**16 進数**:<br />8008100C<br />**数値**:<br />-2146955252|下書き状態ではないプロパティのプロパティ オプション セット項目は変更できません。|
> |**名前**:<br />EditorOnlySupportAndOperatorForLogicalConditions<br />**16 進数**:<br />80060005<br />**数値**:<br />-2147090427|ルール式にはサポートされていない論理演算子が含まれています。 エディターは、論理条件の AND 演算子のみをサポートします。|
> |**名前**:<br />EditQueryInDynamicExcelNotSupported<br />**16 進数**:<br />800609B8<br />**数値**:<br />-2147087944|Excel ファイルをエクスポートした後は、動的スプレッドシートのクエリを編集できません。 変更を加える場合は、Dynamics 365 に戻って再度エクスポートします。|
> |**名前**:<br />EESiteDBFetchFailure<br />**16 進数**:<br />80050025<br />**数値**:<br />-2147155931|サイト DB からデータを取得できません。|
> |**名前**:<br />EmailAlreadyExistsInDestinationQueue<br />**16 進数**:<br />80040523<br />**数値**:<br />-2147220189|この電子メールを指定されたキューに追加することはできません。 この電子メールのキュー アイテムは、既にキューに存在します。 キューからのアイテムを削除してから、もう一度やり直してください。|
> |**名前**:<br />EmailDoesNotExist<br />**16 進数**:<br />80050007<br />**数値**:<br />-2147155961|指定された添付ファイルに対応する電子メールは存在しません。|
> |**名前**:<br />EmailEngagementFeatureDisabled<br />**16 進数**:<br />80050003<br />**数値**:<br />-2147155965|電子メール添付ファイルをフォローする、またはフォローを取り消すには、現在の組織に対して電子メール エンゲージメント機能を有効にしてください。|
> |**名前**:<br />EmailEngagementFeatureDisabledForAttachmentTracking<br />**16 進数**:<br />80050015<br />**数値**:<br />-2147155947|電子メール添付ファイルをフォローするには、この組織に対して電子メール エンゲージメント機能を有効にしてください。|
> |**名前**:<br />EmailInteractionsFetchFailure<br />**16 進数**:<br />80050022<br />**数値**:<br />-2147155934|電子メールの対話を取得できません。|
> |**名前**:<br />EmailMessageSizeExceeded<br />**16 進数**:<br />8005E237<br />**数値**:<br />-2147098057|電子メール サイズは、展開で指定された MaximumMessageSizeLimit を超えています。|
> |**名前**:<br />EmailMonitoringDeProvisionFailed<br />**16 進数**:<br />80050014<br />**数値**:<br />-2147155948|電子メール エンゲージメント機能のプロビジョニング解除に失敗しました|
> |**名前**:<br />EmailMonitoringNotProvisioned<br />**16 進数**:<br />80050011<br />**数値**:<br />-2147155951|RI プロビジョニング サービスが失敗しました。|
> |**名前**:<br />EmailMonitoringProvisionFailed<br />**16 進数**:<br />80050012<br />**数値**:<br />-2147155950|電子メール エンゲージメント機能のプロビジョニングに失敗しました|
> |**名前**:<br />EmailNotFollowed<br />**16 進数**:<br />80050008<br />**数値**:<br />-2147155960|対応する電子メールがフォローされていないため、この添付ファイルをフォローできません。|
> |**名前**:<br />EmailOpenActionCardCreationFailure<br />**16 進数**:<br />80050024<br />**数値**:<br />-2147155932|電子メールを開けるアクション カードを作成できません。|
> |**名前**:<br />EmailRecipientNotSpecified<br />**16 進数**:<br />80040b04<br />**数値**:<br />-2147218684|電子メールを送信するには、少なくとも 1 人の宛先を指定する必要があります|
> |**名前**:<br />EmailReminderActionCardCreationFailure<br />**16 進数**:<br />80050023<br />**数値**:<br />-2147155933|電子メール アラーム アクション カードを作成できません。|
> |**名前**:<br />EmailRouterFileTooLargeToProcess<br />**16 進数**:<br />8005F031<br />**数値**:<br />-2147094479|1 つまたは複数の E-mail Router 構成ファイルが処理可能なサイズを超えています。|
> |**名前**:<br />EmailServerProfileADBasedAuthenticationProtocolNotAllowed<br />**16 進数**:<br />8005E23C<br />**数値**:<br />-2147098052|組織で使用する認証プロトコルを Negotiate または NTLM に設定できません。設定するには Active Directory が必要です。 システム管理者に連絡して、Active Directory ベースの認証プロトコルを有効にするように依頼してください。|
> |**名前**:<br />EmailServerProfileAutoDiscoverNotAllowed<br />**16 進数**:<br />8005E204<br />**数値**:<br />-2147098108|サーバー URL および場所の自動検出は、Exchange 電子メール サーバーの種類としてのみ使用できます。|
> |**名前**:<br />EmailServerProfileBasicAuthenticationProtocolNotAllowed<br />**16 進数**:<br />8005E23D<br />**数値**:<br />-2147098051|セキュリティで保護されたチャンネルを使用して資格情報を送信する必要があるため、指定認証プロトコルは使用できません。 システム管理者に連絡して、セキュリティで保護されていないチャンネルで基本認証プロトコルを有効にするように依頼してください。|
> |**名前**:<br />EmailServerProfileDelegateAccessNotAllowed<br />**16 進数**:<br />8005E235<br />**数値**:<br />-2147098059|SMTP 電子メール サーバーの種類に対して、代理人アクセスの自動許可は使用できません。|
> |**名前**:<br />EmailServerProfileImpersonationNotAllowed<br />**16 進数**:<br />8005E236<br />**数値**:<br />-2147098058|Non Exchange 電子メール サーバーの種類では、偽装は使用できません。|
> |**名前**:<br />EmailServerProfileInvalidAuthenticationProtocol<br />**16 進数**:<br />8005E23B<br />**数値**:<br />-2147098053|認証プロトコルは指定したサーバーおよび接続の種類に対して無効です。 詳細については、システム管理者に問い合わせてください。|
> |**名前**:<br />EmailServerProfileInvalidCredentialRetrievalForExchange<br />**16 進数**:<br />8005E203<br />**数値**:<br />-2147098109|電子メール サーバーの種類の接続の種類として情報なし [(匿名)] を使用することはできません。|
> |**名前**:<br />EmailServerProfileInvalidCredentialRetrievalForOnline<br />**16 進数**:<br />8005E202<br />**数値**:<br />-2147098110|Microsoft Dynamics 365 Online に対する接続の種類として [Windows 統合] または [匿名認証] を使用できません。|
> |**名前**:<br />EmailServerProfileInvalidServerLocation<br />**16 進数**:<br />8005E20A<br />**数値**:<br />-2147098102|指定されたサーバーの場所 {0} が無効です。 サーバーの場所を修正して、やり直してください。|
> |**名前**:<br />EmailServerProfileLocationNotRequired<br />**16 進数**:<br />8005E205<br />**数値**:<br />-2147098107|サーバーの場所の自動検出が [はい] に設定されているとき、受信 / 送信電子メール サーバーの場所を指定することはできません。|
> |**名前**:<br />EmailServerProfileNotAssociated<br />**16 進数**:<br />8005E222<br />**数値**:<br />-2147098078|電子メール サーバー プロファイルは現在のメールボックスに関連付けられていません。 メールの送信および受信のために有効なプロファイルを関連付けてください。|
> |**名前**:<br />EmailServerProfileSslRequiredForOnline<br />**16 進数**:<br />8005E201<br />**数値**:<br />-2147098111|Microsoft Dynamics 365 Online に SSL を false として設定できません。|
> |**名前**:<br />EmailServerProfileSslRequiredForOnPremise<br />**16 進数**:<br />8005E234<br />**数値**:<br />-2147098060|この Dynamics 365 展開には、外部の電子メール サーバーとの契約による SSL の使用が必須です。|
> |**名前**:<br />EmptyCommandOrEntity<br />**16 進数**:<br />80154B51<br />**数値**:<br />-2146088111|コマンドまたはエンティティ名は空にできません。|
> |**名前**:<br />EmptyContent<br />**16 進数**:<br />80040365<br />**数値**:<br />-2147220635|ファイルが空です。|
> |**名前**:<br />EmptyEntityFilterXml<br />**16 進数**:<br />80071118<br />**数値**:<br />-2147020520|FetchXML がありません。|
> |**名前**:<br />EmptyFileForImport<br />**16 進数**:<br />80048487<br />**数値**:<br />-2147187577|選択したファイルにデータが含まれていません。|
> |**名前**:<br />EmptyFilesInZip<br />**16 進数**:<br />80048486<br />**数値**:<br />-2147187578|圧縮 (.zip) ファイルまたは .cab ファイル内の 1 つ以上のファイルにデータが含まれていません。 ファイルを確認してから再度お試しください。|
> |**名前**:<br />EmptyHeaderColumn<br />**16 進数**:<br />80040337<br />**数値**:<br />-2147220681|列見出しを空白にすることはできません。|
> |**名前**:<br />EmptyHeaderRow<br />**16 進数**:<br />80040366<br />**数値**:<br />-2147220634|ファイルの最初の行は空になります。|
> |**名前**:<br />EmptyImportFileRow<br />**16 進数**:<br />80040347<br />**数値**:<br />-2147220665|空の行です。|
> |**名前**:<br />EmptyRecord<br />**16 進数**:<br />80040373<br />**数値**:<br />-2147220621|レコードが空です|
> |**名前**:<br />EmptySecretInDataSource<br />**16 進数**:<br />80044818<br />**数値**:<br />-2147203048|データ ソースのシークレットがソリューションに含まれていません。 ソリューションのインポート後にシークレットを追加するには、データ ソースを編集する必要があります。|
> |**名前**:<br />EmptySiteMapXml<br />**16 進数**:<br />8004F402<br />**数値**:<br />-2147159038|サイトマップ xml が空です。|
> |**名前**:<br />EmptyXml<br />**16 進数**:<br />80040202<br />**数値**:<br />-2147220990|空の XML。|
> |**名前**:<br />EnableMobileOfflineDisableChangeTrackingError<br />**16 進数**:<br />800609A2<br />**数値**:<br />-2147087966|Mobile Offline クライアントが有効になっているため、このエンティティの変更履歴を有効にする必要があります。|
> |**名前**:<br />EnableRIFeatureNotAllowed<br />**16 進数**:<br />80044279<br />**数値**:<br />-2147204487|リレーションシップ インサイトのテナント情報を更新するには、システム管理者特権が必要です。|
> |**名前**:<br />EndUserNotificationTypeNotValidForEmail<br />**16 進数**:<br />8004D291<br />**数値**:<br />-2147167599|EndUserNotification の種類: {0} に電子メールを送信できません。|
> |**名前**:<br />EntitiesExceedMaxAllowed<br />**16 進数**:<br />80060415<br />**数値**:<br />-2147089387|1 つのプロセス フローで 5 個を超えるエンティティを扱うことはできません。 エンティティの一部を削除してから、もう一度試してみてください。|
> |**名前**:<br />EntitiesInViewNotAvailableOffline<br />**16 進数**:<br />80071125<br />**数値**:<br />-2147020507|参照されている 1 つまたは複数のエンティティはオフラインで使用できません。|
> |**名前**:<br />EntitiesInViewNotInProfile<br />**16 進数**:<br />80071124<br />**数値**:<br />-2147020508|このビューの 1 つ以上のエンティティは、このプロファイルの一部ではありません。|
> |**名前**:<br />EntitlementAlreadyInactiveState<br />**16 進数**:<br />80060615<br />**数値**:<br />-2147088875|アクティブ状態にある権利をアクティブ化することはできません。|
> |**名前**:<br />EntitlementAlreadyInCanceledState<br />**16 進数**:<br />80044208<br />**数値**:<br />-2147204600|キャンセル状態にある権利を取り消すことはできません。|
> |**名前**:<br />EntitlementAlreadyInDraftState<br />**16 進数**:<br />80060614<br />**数値**:<br />-2147088876|下書き状態にある権利を非アクティブ化することはできません。|
> |**名前**:<br />EntitlementBlankTerms<br />**16 進数**:<br />80060622<br />**数値**:<br />-2147088862|合計時間を空白にすることはできません。 値を入力してからやり直してください。|
> |**名前**:<br />EntitlementChannelInvalidState<br />**16 進数**:<br />80060603<br />**数値**:<br />-2147088893|関連付けられた権利の状態が "下書き" でない場合、権利チャネルの期間を作成、変更、または削除することはできません。|
> |**名前**:<br />EntitlementChannelWithoutEntitlementId<br />**16 進数**:<br />80060612<br />**数値**:<br />-2147088878|権利または権利テンプレートに権利チャネルを関連付けます。|
> |**名前**:<br />EntitlementEditDraft<br />**16 進数**:<br />80060613<br />**数値**:<br />-2147088877|編集できるのは下書きの権利のみです。|
> |**名前**:<br />EntitlementInvalidRemainingTerms<br />**16 進数**:<br />80060624<br />**数値**:<br />-2147088860|残りの期間の数が合計時間を超えることはできません。|
> |**名前**:<br />EntitlementInvalidStartEndDate<br />**16 進数**:<br />80060600<br />**数値**:<br />-2147088896|開始日は、終了日より後にすることはできません|
> |**名前**:<br />EntitlementInvalidState<br />**16 進数**:<br />80060601<br />**数値**:<br />-2147088895|"アクティブ" または "待機中" の状態にある権利を削除することはできません|
> |**名前**:<br />EntitlementInvalidTerms<br />**16 進数**:<br />80060604<br />**数値**:<br />-2147088892|残りの時間が負の値にならないように、合計時間の値に、より高い値を指定してください。|
> |**名前**:<br />EntitlementNotActiveInAssociationToCase<br />**16 進数**:<br />80060616<br />**数値**:<br />-2147088874|この権利にはサポート案件を作成できません。権利がアクティブ状態ではありません。|
> |**名前**:<br />EntitlementTemplateTotalTerms<br />**16 進数**:<br />80060620<br />**数値**:<br />-2147088864|割り当てタイプがサポート案件の数である場合、合計時間を小数の値にはできません。 整数を指定してください。|
> |**名前**:<br />EntitlementTotalTerms<br />**16 進数**:<br />80060619<br />**数値**:<br />-2147088871|割り当てタイプがサポート案件の数である場合、合計時間を小数の値にはできません。 整数を指定してください。|
> |**名前**:<br />EntityCannotBeChildInCustomRelationship<br />**16 進数**:<br />8004432D<br />**数値**:<br />-2147204307|このエンティティはユーザー定義の上位関係の下位として有効でないか、すでに上位関係の下位にあります|
> |**名前**:<br />EntityCannotHaveOwnedByMeFilter<br />**16 進数**:<br />80071136<br />**数値**:<br />-2147020490|プロファイル '{1}' のエンティティ '{0}' で OwnedByMe は true に設定されています。 このプロパティは '{0}' エンティティの有効なプロパティではありません。|
> |**名前**:<br />EntityCannotHaveOwnedByMyTeamFilter<br />**16 進数**:<br />80071137<br />**数値**:<br />-2147020489|プロファイル '{1}' のエンティティ '{0}' で OwnedByMyTeam は true に設定されています。 このプロパティは '{0}' エンティティの有効なプロパティではありません。|
> |**名前**:<br />EntityCannotParticipateInEntityAssociation<br />**16 進数**:<br />80044332<br />**数値**:<br />-2147204302|このエンティティは、エンティティ関連付けに参加できません|
> |**名前**:<br />EntityDupCheckNotSupportedSystemWide<br />**16 進数**:<br />80048431<br />**数値**:<br />-2147187663|重複データ検出は、選択したエンティティの 1 つ以上の組織で有効になっていません。 重複データ検出ジョブを開始できません。|
> |**名前**:<br />EntityExceedsMaxActiveBusinessProcessFlows<br />**16 進数**:<br />80060420<br />**数値**:<br />-2147089376|{0} エンティティがアクティブな業務プロセス フローの最大数を超えています。 制限値は {1}です。|
> |**名前**:<br />EntityFilterContainerMustNotBeNullFormatString<br />**16 進数**:<br />80071132<br />**数値**:<br />-2147020494|エンティティ '{0}' に指定されたフィルターがありません。 少なくとも 1 つのフィルターを定義する必要があります。|
> |**名前**:<br />EntityGroupNameOrEntityNamesMustBeProvided<br />**16 進数**:<br />80060205<br />**数値**:<br />-2147089915|パラメーターが指定されていません。 EntityGroupName または EntityNames を入力してください。|
> |**名前**:<br />EntityHasNoStateCode<br />**16 進数**:<br />80047015<br />**数値**:<br />-2147192811|指定されたエンティティに状態コードはありません。|
> |**名前**:<br />EntityInstanceIsNull<br />**16 進数**:<br />80060444<br />**数値**:<br />-2147089340|ビジネス プロセスの作成または更新時のエラー: エンティティ インスタンスは Null にできません。|
> |**名前**:<br />EntityInstantiationFailed<br />**16 進数**:<br />80040243<br />**数値**:<br />-2147220925|エンティティ インスタンス サービスのインスタンス化に失敗しました。|
> |**名前**:<br />EntityIsIntersect<br />**16 進数**:<br />8004830F<br />**数値**:<br />-2147187953|指定されたエンティティは、交差するエンティティです|
> |**名前**:<br />EntityIsLocked<br />**16 進数**:<br />80043b1d<br />**数値**:<br />-2147206371|このエンティティは既にロックされています。|
> |**名前**:<br />EntityIsNotBusinessProcessFlowEnabled<br />**16 進数**:<br />80060421<br />**数値**:<br />-2147089375|エンティティ {0} の IsBusinessProcessEnabled プロパティは false です。|
> |**名前**:<br />EntityIsNotCustomizable<br />**16 進数**:<br />80047008<br />**数値**:<br />-2147192824|指定されたエンティティ名がカスタマイズ可能ではありません。|
> |**名前**:<br />EntityIsNotEnabledForExternalParty<br />**16 進数**:<br />8006111B<br />**数値**:<br />-2147086053|外部パーティに対して有効化されていないエンティティに関連付けられている外部パーティ アイテムを作成 / 更新することはできません。|
> |**名前**:<br />EntityIsNotEnabledForFollow<br />**16 進数**:<br />8004F6A2<br />**数値**:<br />-2147158366|このエンティティは、フォローされるための許可が有効になっていません。 |
> |**名前**:<br />EntityIsNotEnabledForFollowUser<br />**16 進数**:<br />8004F6A1<br />**数値**:<br />-2147158367|このエンティティは、フォローされるための許可が有効になっていません。 |
> |**名前**:<br />EntityIsUnlocked<br />**16 進数**:<br />80043b1e<br />**数値**:<br />-2147206370|このエンティティは既にロック解除されています。|
> |**名前**:<br />EntityKeyNameExists<br />**16 進数**:<br />80060893<br />**数値**:<br />-2147088237|名前が {0} のエンティティ キーが、エンティティ {1} に既に存在します。|
> |**名前**:<br />EntityKeyNotDefined<br />**16 進数**:<br />80060890<br />**数値**:<br />-2147088240|指定されているキー属性は、{0} エンティティに対して定義されているキーではありません|
> |**名前**:<br />EntityKeyWithSelectedAttributesExists<br />**16 進数**:<br />80060894<br />**数値**:<br />-2147088236|選択された属性を持つエンティティ キーが、エンティティに既に存在します。|
> |**名前**:<br />EntityLimitExceeded<br />**16 進数**:<br />80060200<br />**数値**:<br />-2147089920|MultiEntitySearchで、組織用に定義されたエンティティ数の上限を超えました。|
> |**名前**:<br />EntityLoopBeingCreated<br />**16 進数**:<br />80040387<br />**数値**:<br />-2147220601|この上位下位の関連付けを作成すると、このエンティティ階層にループが生成されます。|
> |**名前**:<br />EntityLoopExists<br />**16 進数**:<br />80040386<br />**数値**:<br />-2147220602|このエンティティの階層にループが存在します。|
> |**名前**:<br />EntityMetadataSyncFailed<br />**16 進数**:<br />8005F238<br />**数値**:<br />-2147093960|サーバー構成に問題がありました。  サーバーの構成の変更に問題がありました。  アプリケーションを読み込めません。Dynamics 365 管理者に問い合わせてください。|
> |**名前**:<br />EntityMetadataSyncFailedWithContinue<br />**16 進数**:<br />8005F239<br />**数値**:<br />-2147093959|サーバーの構成の変更に問題がありました。  アプリは引き続き古い構成で使用できます。しかし、保存時のエラーなど何らかの問題が発生することがあります。  Dynamics 365 管理者にお問い合わせください。 |
> |**名前**:<br />EntityNotEnabledForAutoCreatedAccessTeams<br />**16 進数**:<br />80048334<br />**数値**:<br />-2147187916|このエンティティは自動作成のアクセス チームに対して有効になっていません。|
> |**名前**:<br />EntityNotEnabledForCharts<br />**16 進数**:<br />8004E00C<br />**数値**:<br />-2147164148|グラフは、指定された主エンティティの種類コード: {0}で有効ではありません。|
> |**名前**:<br />EntityNotEnabledForThisDevice<br />**16 進数**:<br />8005F200<br />**数値**:<br />-2147094016|このデバイスで表示するのに、エンティティが無効です|
> |**名前**:<br />EntityNotRule<br />**16 進数**:<br />8004E112<br />**数値**:<br />-2147163886|コレクションの名は、定期的なアイテムのルールではありません。|
> |**名前**:<br />EntityReferenceArgumentsNotBound<br />**16 進数**:<br />80060395<br />**数値**:<br />-2147089515|種類が EntityReference である必須の引数は何らかのエンティティにバインドされている必要があります。|
> |**名前**:<br />EntityRelationshipRoleCustomLabelsMissing<br />**16 進数**:<br />80044328<br />**数値**:<br />-2147204312|エンティティ関係ロールに UseCustomLabels の表示オプションがある場合、カスタム ラベルが提供されます|
> |**名前**:<br />EntityRelationshipSchemaNameNotUnique<br />**16 進数**:<br />8004432B<br />**数値**:<br />-2147204309|指定された名前の関連付けは、既に存在しています。 一意の名前を指定してください。|
> |**名前**:<br />EntityRelationshipSchemaNameRequired<br />**16 進数**:<br />8004432A<br />**数値**:<br />-2147204310|エンティティ関係には名前が必要です|
> |**名前**:<br />EntityTypeNotSupported<br />**16 進数**:<br />80100008<br />**数値**:<br />-2146435064|{0} エンティティはこのメッセージをサポートしていません。|
> |**名前**:<br />EntityTypeSpecifiedForDashboard<br />**16 進数**:<br />8004E30B<br />**数値**:<br />-2147163381|エンティティの種類がは、ダッシュボードに対して指定できません。|
> |**名前**:<br />ErrorConnectingToDiscoveryService<br />**16 進数**:<br />8004B066<br />**数値**:<br />-2147176346|顧客探索サービスへの接続を試みる際のエラー。|
> |**名前**:<br />ErrorConnectingToOrganizationService<br />**16 進数**:<br />8004B068<br />**数値**:<br />-2147176344|顧客組織サービスへの接続を試みる際のエラー。|
> |**名前**:<br />ErrorDeleteStatementTextIsReferenced<br />**16 進数**:<br />8004F203<br />**数値**:<br />-2147159549|UI スクリプト ステートメント テキストが 1 つ以上の ui スクリプト ステートメントで参照されているため、削除できません。|
> |**名前**:<br />ErrorFetchingBaseUrl<br />**16 進数**:<br />80044290<br />**数値**:<br />-2147204464|組織 ID {0} の基本 URL をフェッチできません。 例外の詳細 {1}|
> |**名前**:<br />ErrorFetchingRIProvisionStatus<br />**16 進数**:<br />80044291<br />**数値**:<br />-2147204463|組織 ID {0} の RI プロビジョニング状態をフェッチできません。 例外の詳細 {1}|
> |**名前**:<br />ErrorGeneratingActionHub<br />**16 進数**:<br />80071001<br />**数値**:<br />-2147020799|エラーが発生しました。 後でもう一度お試しください。|
> |**名前**:<br />ErrorGeneratingInvitation<br />**16 進数**:<br />8004B013<br />**数値**:<br />-2147176429|招待トークンの作成で、一部内部エラーが発生しました。後でやり直してください。|
> |**名前**:<br />ErrorImportInvalidForPublishedScript<br />**16 進数**:<br />8004F216<br />**数値**:<br />-2147159530|公開済み UI スクリプトにデータを保存できません。 UI スクリプトの公開を取り下げて、もう一度やり直してください。|
> |**名前**:<br />ErrorIncreate<br />**16 進数**:<br />80040359<br />**数値**:<br />-2147220647|Microsoft Dynamics 365 レコードを作成できませんでした|
> |**名前**:<br />ErrorInDelete<br />**16 進数**:<br />8004035a<br />**数値**:<br />-2147220646|Microsoft Dynamics 365 レコードを削除できませんでした|
> |**名前**:<br />ErrorInFetchingEmailEngagementProvisioningStatus<br />**16 進数**:<br />80050013<br />**数値**:<br />-2147155949|電子メール エンゲージメント機能のプロビジョニング状態のフェッチ中にエラーが発生しました。|
> |**名前**:<br />ErrorInFieldWidthIncrease<br />**16 進数**:<br />80044351<br />**数値**:<br />-2147204271|フィールドの幅を拡大するときにエラーが発生しました。|
> |**名前**:<br />ErrorInImportConfig<br />**16 進数**:<br />80040323<br />**数値**:<br />-2147220701|インポート構成にエラーがあるため、一括インポートを処理することはできません。|
> |**名前**:<br />ErrorInParseRow<br />**16 進数**:<br />80040346<br />**数値**:<br />-2147220666|行を解析できませんでした。 通常、これは行が長すぎるために起こります。|
> |**名前**:<br />ErrorInSetState<br />**16 進数**:<br />80040357<br />**数値**:<br />-2147220649|Microsoft Dynamics 365 レコードの状態またはステータスを設定できませんでした|
> |**名前**:<br />ErrorInStoringImportFile<br />**16 進数**:<br />80048497<br />**数値**:<br />-2147187561|インポート ファイルをデータベースに保存するときにエラーが発生しました。|
> |**名前**:<br />ErrorInUnzip<br />**16 進数**:<br />80048483<br />**数値**:<br />-2147187581|アップロードされた 圧縮 (.zip) ファイルまたは .cab (.zip) ファイルの展開中にエラーが発生しました。 ファイルがパスワードで保護されていないことを確認して、ファイルをもう一度アップロードしてください。 この問題が解決しない場合は、システム管理者にお問い合わせください。|
> |**名前**:<br />ErrorInUnzipAlternate<br />**16 進数**:<br />80048503<br />**数値**:<br />-2147187453|アップロードされた 圧縮 (.zip) ファイルの展開中にエラーが発生しました。 もう一度ファイルのアップロードをやり直してください。 この問題が解決しない場合は、システム管理者にお問い合わせください。|
> |**名前**:<br />ErrorInUpdate<br />**16 進数**:<br />80040358<br />**数値**:<br />-2147220648|Microsoft Dynamics 365 レコードを更新できませんでした|
> |**名前**:<br />ErrorInvalidFileNameChars<br />**16 進数**:<br />8004F214<br />**数値**:<br />-2147159532|Microsoft Excel のファイル名に次の文字を使用できません: *  \ : > < | ? " /. 有効な文字を使用してファイルの名前を変更し、やり直してください。|
> |**名前**:<br />ErrorInvalidUIScriptImportFile<br />**16 進数**:<br />8004F211<br />**数値**:<br />-2147159535|ファイルの種類はサポートされていません。 インポート対象として XML ファイルを選択してください。|
> |**名前**:<br />ErrorMigrationProcessExcessOnServer<br />**16 進数**:<br />8005F034<br />**数値**:<br />-2147094476|サーバーが別の移行プロセスを処理するのにビジー状態です。 少し時間を置いてやり直してください。|
> |**名前**:<br />ErrorMimeTypeNullOrEmpty<br />**16 進数**:<br />8004F215<br />**数値**:<br />-2147159531|UploadFromBase64DataUIScriptRequest 方法の MimeType のプロパティ値が null または空です。 有効なプロパティ値を指定して、やり直してください。|
> |**名前**:<br />ErrorNoActiveRoutingRuleExists<br />**16 進数**:<br />8004F874<br />**数値**:<br />-2147157900|現在このサポート案件をルーティングするためのアクティブなルールがありません。|
> |**名前**:<br />ErrorNoQueryData<br />**16 進数**:<br />8004F220<br />**数値**:<br />-2147159520|エラーが発生しました。 データが存在しないか、またはデータを表示する特権がないかのどちらかです。 システム管理者にお問い合わせください。|
> |**名前**:<br />ErrorOnFeatureStatusChange<br />**16 進数**:<br />80044289<br />**数値**:<br />-2147204471|組織 ID {1} の {0} 機能を有効化 / 無効化できません。 例外の詳細 {2}。|
> |**名前**:<br />ErrorOnGetRecord<br />**16 進数**:<br />80044286<br />**数値**:<br />-2147204474|テーブル {0} のレコードをフェッチ中にエラーが発生しました。 例外の詳細 {1}。|
> |**名前**:<br />ErrorOnGetRIProvisionStatus<br />**16 進数**:<br />80044282<br />**数値**:<br />-2147204478|組織 ID {0} のリレーションシップ インサイトのプロビジョニング状態を取得できません。 例外の詳細 {1}。|
> |**名前**:<br />ErrorOnGetRITenantEndPoint<br />**16 進数**:<br />80044283<br />**数値**:<br />-2147204477|組織 ID {0} のリレーションシップ インサイトのテナント エンドポイント情報を取得できません。 例外の詳細 {1}。|
> |**名前**:<br />ErrorOnQryPropertyBagCollection<br />**16 進数**:<br />80044287<br />**数値**:<br />-2147204473|すべての {0} 列がクエリから返されませんでした。|
> |**名前**:<br />ErrorOnStartOfRIProvision<br />**16 進数**:<br />80044284<br />**数値**:<br />-2147204476|組織 ID {0} のプロビジョニングを開始できません。 例外の詳細 {1}。|
> |**名前**:<br />ErrorOnTenantVerifyUpdate<br />**16 進数**:<br />80044285<br />**数値**:<br />-2147204475|組織 ID {0} のテナント情報を確認または更新できません。 例外の詳細 {1}。|
> |**名前**:<br />ErrorPropertyBagCollectionMissedColumn<br />**16 進数**:<br />80044288<br />**数値**:<br />-2147204472|テーブル {1} の {0} 列がありません。|
> |**名前**:<br />ErrorReactivatingComponentInstance<br />**16 進数**:<br />8004F004<br />**数値**:<br />-2147160060|ラベルの削除取り消し後、再アクティブ化するための基になるラベルはありません。|
> |**名前**:<br />ErrorScriptCannotDeletePublishedScript<br />**16 進数**:<br />8004F209<br />**数値**:<br />-2147159543|公開済みの UI スクリプトは削除できません。 まず公開を取り下げる必要があります。|
> |**名前**:<br />ErrorScriptCannotUpdatePublishedScript<br />**16 進数**:<br />8004F213<br />**数値**:<br />-2147159533|公開済みの UI スクリプトは更新できません。 まず公開を取り下げる必要があります。|
> |**名前**:<br />ErrorScriptFileParse<br />**16 進数**:<br />8004F212<br />**数値**:<br />-2147159534|XML ファイルの解析中にエラーが発生しました。|
> |**名前**:<br />ErrorScriptInitialStatementNotInScript<br />**16 進数**:<br />8004F207<br />**数値**:<br />-2147159545|このスクリプトの最初の説明文は、このスクリプトに属しません。|
> |**名前**:<br />ErrorScriptInitialStatementNotRoot<br />**16 進数**:<br />8004F208<br />**数値**:<br />-2147159544|最初の説明文は、ルート文であり、以前の文設定と同じではありません。|
> |**名前**:<br />ErrorScriptLanguageNotInstalled<br />**16 進数**:<br />8004F206<br />**数値**:<br />-2147159546|指定された言語が Dynamics 365 のインストールでサポートされていません。 [有効] な言語の一覧については、システム管理者に確認してください。|
> |**名前**:<br />ErrorScriptPublishMalformedScript<br />**16 進数**:<br />8004F20B<br />**数値**:<br />-2147159541|指定された UI スクリプトは公開できません。 末尾が終了スクリプトまたは次のスクリプト アクション ノードではないパスが、UI スクリプトに1 つまたは複数含まれています。 パスを修正して、公開し直してください。|
> |**名前**:<br />ErrorScriptPublishMissingInitialStatement<br />**16 進数**:<br />8004F20A<br />**数値**:<br />-2147159542|指定された UI スクリプトは公開できません。 最初のステートメント番号の値を指定してから、公開し直してください|
> |**名前**:<br />ErrorScriptSessionCannotCreateForDraftScript<br />**16 進数**:<br />8004F204<br />**数値**:<br />-2147159548|公開されていない UI スクリプトの UI スクリプト セッションは作成できません。|
> |**名前**:<br />ErrorScriptSessionCannotSetStateForDraftScript<br />**16 進数**:<br />8004F20D<br />**数値**:<br />-2147159539|公開されていない UI スクリプトの UI スクリプト セッションの状態は設定できません。|
> |**名前**:<br />ErrorScriptSessionCannotUpdateForDraftScript<br />**16 進数**:<br />8004F205<br />**数値**:<br />-2147159547|公開されていない UI スクリプトの UI スクリプト セッションは更新できません。|
> |**名前**:<br />ErrorScriptStatementResponseTypeOnlyForPrompt<br />**16 進数**:<br />8004F20E<br />**数値**:<br />-2147159538|プロンプトではないステートメントに対する、応答コントロールの種類を関連付けることはできません。|
> |**名前**:<br />ErrorScriptUnpublishActiveScript<br />**16 進数**:<br />8004F20C<br />**数値**:<br />-2147159540|このスクリプトは使用中で、アクティブなセッション (status-reason=incomplete) があります。 アクティブ セッション (status-reason=cancelled) を終了し、公開取り下げをやり直してください。|
> |**名前**:<br />ErrorsInEmailRouterMigrationFiles<br />**16 進数**:<br />8005F032<br />**数値**:<br />-2147094478|移行する E-mail Router ファイルが無効です|
> |**名前**:<br />ErrorsInImportFiles<br />**16 進数**:<br />8004034a<br />**数値**:<br />-2147220662|無効なインポート用ファイル|
> |**名前**:<br />ErrorsInProfileRuleWorkflowActivation<br />**16 進数**:<br />80061119<br />**数値**:<br />-2147086055|このプロファイル ルールをアクティブ化することはできません。 このプロファイル ルールにより参照されるレコードの種類に対する必要なアクセス許可がありません。|
> |**名前**:<br />ErrorsInSlaWorkflowActivation<br />**16 進数**:<br />80048535<br />**数値**:<br />-2147187403|このサービス レベル アグリーメント (SLA) をアクティブ化することはできません。 この SLA により参照されるレコードの種類に対する必要なアクセス許可がありません。|
> |**名前**:<br />ErrorsInWorkflowDefinition<br />**16 進数**:<br />80048455<br />**数値**:<br />-2147187627|指定されたワークフローでエラーがあり、公開することはできません。 ワークフローを開き、エラーを削除してからやり直してください。|
> |**名前**:<br />ErrorStatementDeleteOnlyForDraftScript<br />**16 進数**:<br />8004F210<br />**数値**:<br />-2147159536|下書きでない UI スクリプトの UI スクリプト ステートメントは削除できません。|
> |**名前**:<br />ErrorStatementOnlyForDraftScript<br />**16 進数**:<br />8004F20F<br />**数値**:<br />-2147159537|下書きでない UI スクリプトの UI スクリプト ステートメントは作成できません。|
> |**名前**:<br />ErrorTemplate<br />**16 進数**:<br />80050102<br />**数値**:<br />-2147155710|{0}|
> |**名前**:<br />ErrorUIScriptPromptMissing<br />**16 進数**:<br />8004F221<br />**数値**:<br />-2147159519|アクティブ化しているダイアログには、プロンプト/応答がありません。|
> |**名前**:<br />ErrorUpdateStatementTextIsReferenced<br />**16 進数**:<br />8004F202<br />**数値**:<br />-2147159550|この UI スクリプト ステートメント テキストは 1 つ以上の公開済みの ui スクリプトで参照されているため、更新できません。|
> |**名前**:<br />ErrorUploadingReport<br />**16 進数**:<br />80048298<br />**数値**:<br />-2147188072|Microsoft Dynamics 365 にレポートを追加しようとしているときにエラーが発生しました。 レポートの追加を再実行してください。 この問題が解決しない場合は、システム管理者にお問い合わせください。|
> |**名前**:<br />EventNotSupportedForBusinessRule<br />**16 進数**:<br />80060001<br />**数値**:<br />-2147090431|イベント {0} は、クライアント側の業務ルールでサポートされていません。|
> |**名前**:<br />EventTypeAndControlNameAreMismatched<br />**16 進数**:<br />80060003<br />**数値**:<br />-2147090429|このイベントの種類およびコントロール名の組み合わせは想定外です|
> |**名前**:<br />EvoStsAuthorizationServerRecordCreationFailureException<br />**16 進数**:<br />80071006<br />**数値**:<br />-2147020794|Evo STS の認証レコードの作成中にデータベース操作が失敗しました。|
> |**名前**:<br />ExceedCustomEntityQuota<br />**16 進数**:<br />8004b042<br />**数値**:<br />-2147176382|ユーザー定義エンティティの制限に達しました。|
> |**名前**:<br />ExceededLimitForAllowedFacetableAttributes<br />**16 進数**:<br />80060306<br />**数値**:<br />-2147089658|許可されている facetable 属性の制限が 4 であるため、エンティティ {0} 対するユーザー検索ファセットを設定できません。 続行のためにいくつかの属性を削除してください。|
> |**名前**:<br />ExceededNumberOfRecordsCanFollow<br />**16 進数**:<br />8004F6A0<br />**数値**:<br />-2147158368|フォローできるレコードの最大数を越えました。 フォローを開始をするために、レコードのフォロー取り消しをしてください。|
> |**名前**:<br />ExceededRollupFieldsPerEntityQuota<br />**16 進数**:<br />80060543<br />**数値**:<br />-2147089085|名前 {2} および id {1} を持つエンティティに対して、名前 {4} が id {3} を持つロールアップ フィールドを追加できません。 このレコードの種類に許可される {0} の最大値に到達しました。|
> |**名前**:<br />ExceededRollupFieldsPerOrgQuota<br />**16 進数**:<br />80060542<br />**数値**:<br />-2147089086|ロールアップ フィールドを追加できません。 組織に許可される {0} の最大値に到達しました。|
> |**名前**:<br />ExcelFileNotFound<br />**16 進数**:<br />80060805<br />**数値**:<br />-2147088379|要求されたファイルが見つかりませんでした。|
> |**名前**:<br />ExcelOnlineNotUpdated<br />**16 進数**:<br />80060808<br />**数値**:<br />-2147088376|指定されたタイムアウト時間内に Excel Online ファイル {0} が Wopi サーバーから更新されませんでした。|
> |**名前**:<br />ExchangeAutodiscoverError<br />**16 進数**:<br />8004503A<br />**数値**:<br />-2147200966|AutoDiscover は、指定したメールボックスに対する Exchange Web サービス URL が見つかりませんでした。 指定されたメールボックス アドレスと資格情報が正しいこと、および、Autodiscover が有効で正しく構成されていることを確認してください。|
> |**名前**:<br />ExchangeCardAttributeMissingInResponseException<br />**16 進数**:<br />80071102<br />**数値**:<br />-2147020542|Exchange の oData 応答に属性が存在しません。|
> |**名前**:<br />ExchangeCardInvalidResponseFormatException<br />**16 進数**:<br />80071104<br />**数値**:<br />-2147020540|応答形式が無効です。|
> |**名前**:<br />ExchangeCardS2SSetupFailureException<br />**16 進数**:<br />80071105<br />**数値**:<br />-2147020539|Exchange によるアクション カード用のサーバー間認証が設定されていません。|
> |**名前**:<br />ExchangeOptinNotEnabled<br />**16 進数**:<br />80071106<br />**数値**:<br />-2147020538|Exchange optin が有効になっていません。|
> |**名前**:<br />ExchangeRateOfBaseCurrencyNotUpdatable<br />**16 進数**:<br />80048cf5<br />**数値**:<br />-2147185419|基本通貨の為替レートを変更することはできません。|
> |**名前**:<br />ExecuteNotOnDemandWorkflow<br />**16 進数**:<br />80045046<br />**数値**:<br />-2147200954|ワークフローはオンデマンドまたは子ワークフローとしてマークされている必要があります。|
> |**名前**:<br />ExecuteUnpublishedWorkflow<br />**16 進数**:<br />80045047<br />**数値**:<br />-2147200953|ワークフローは公開済み状態でなければなりません。|
> |**名前**:<br />ExistingExternalReport<br />**16 進数**:<br />80040488<br />**数値**:<br />-2147220344|同じ名前のレポートが既に存在するため、レポートを外部使用のために公開できませんでした。 SQL Server Reporting Services でレポートを削除するかまたはこのレポートの名前を変更し、もう一度やり直してください。|
> |**名前**:<br />ExistingParentalRelationship<br />**16 進数**:<br />80048205<br />**数値**:<br />-2147188219|上位関係は既に存在します。|
> |**名前**:<br />ExpansionRequestIsOutsideExpansionWindow<br />**16 進数**:<br />8004E10C<br />**数値**:<br />-2147163892|系列は CutOffWindow 用に既に展開されています。|
> |**名前**:<br />ExpectingAtLeastOneBusinessRuleStep<br />**16 進数**:<br />80060011<br />**数値**:<br />-2147090415|少なくとも 1 つ以上の業務ルール ステップが必要です。|
> |**名前**:<br />ExpiredAuthTicket<br />**16 進数**:<br />8004A101<br />**数値**:<br />-2147180287|認証のために指定されたチケットは期限切れです|
> |**名前**:<br />ExpiredEntitlementActivate<br />**16 進数**:<br />80060617<br />**数値**:<br />-2147088873|期限切れの権利をアクティブ化することはできません。|
> |**名前**:<br />ExpiredKey<br />**16 進数**:<br />8004A106<br />**数値**:<br />-2147180282|ハッシュ値を計算するために指定されるキーは期限切れですが、アクティブ キーのみが有効です。  期限切れキー: {0}。|
> |**名前**:<br />ExpiredOAuthToken<br />**16 進数**:<br />80041d52<br />**数値**:<br />-2147213998|OAuth トークンは有効期限が切れています|
> |**名前**:<br />ExpiredVersionStamp<br />**16 進数**:<br />80044352<br />**数値**:<br />-2147204270|クライアントに関連付けられているバージョン スタンプが期限切れになりました。 完全な同期を実行します。|
> |**名前**:<br />ExportDefaultAsPackagedError<br />**16 進数**:<br />80048048<br />**数値**:<br />-2147188664|既定のソリューションをパッケージとしてエクスポートできません。|
> |**名前**:<br />ExportManagedSolutionError<br />**16 進数**:<br />80048036<br />**数値**:<br />-2147188682|ソリューションのエクスポートでエラーが発生しました。 マネージド ソリューションはエクスポートできません。|
> |**名前**:<br />ExportMissingSolutionError<br />**16 進数**:<br />80048037<br />**数値**:<br />-2147188681|ソリューションのエクスポートでエラーが発生しました。 ソリューションはこのシステムに存在しません。|
> |**名前**:<br />ExportSolutionError<br />**16 進数**:<br />80048035<br />**数値**:<br />-2147188683|ソリューションのエクスポートでエラーが発生しました。|
> |**名前**:<br />ExportToExcelOnlineFeatureNotEnabled<br />**16 進数**:<br />80060804<br />**数値**:<br />-2147088380|Excel Online へのエクスポート機能が有効になっていません。|
> |**名前**:<br />ExportToXlsxFeatureNotEnabled<br />**16 進数**:<br />800608C1<br />**数値**:<br />-2147088191|Excel ファイルへのエクスポート機能が有効になっていません。|
> |**名前**:<br />ExpressionNotSupportedForEditor<br />**16 進数**:<br />80060004<br />**数値**:<br />-2147090428|エディターでサポートされていない式がルールに含まれています。|
> |**名前**:<br />ExternalNameExists<br />**16 進数**:<br />80046F8F<br />**数値**:<br />-2147192945|指定された名前のエンティティは既にデータ ソースに存在します - {0}。 新しい外部名を指定してください。|
> |**名前**:<br />ExternalSearchAttributeLimitExceeded<br />**16 進数**:<br />80060300<br />**数値**:<br />-2147089664|インデックス付きフィールドの最大数に達しました。 関連性検索の構成を更新して、インデックス付きフィールド {1} の合計数を {0} より少なくなるように減らしてください。|
> |**名前**:<br />ExtraPartyInformation<br />**16 進数**:<br />80040316<br />**数値**:<br />-2147220714|追加のパーティ情報は、この操作で提供されるべきではありません。|
> |**名前**:<br />FailedToDeserializeAsyncOperationData<br />**16 進数**:<br />80044304<br />**数値**:<br />-2147204348|非同期操作データをシリアル化解除できませんでした。|
> |**名前**:<br />FailedToGetNetworkServiceName<br />**16 進数**:<br />80047103<br />**数値**:<br />-2147192573|NetworkService アカウントのローカライズ名を取得できませんでした|
> |**名前**:<br />FailedToLoadAssembly<br />**16 進数**:<br />8004024e<br />**数値**:<br />-2147220914|アセンブリを読み込むことができませんでした|
> |**名前**:<br />FailedToScheduleActivity<br />**16 進数**:<br />80047000<br />**数値**:<br />-2147192832|活動をスケジュールできませんでした。|
> |**名前**:<br />FailToDeleteConnectorFromExternalPartner<br />**16 進数**:<br />80072601<br />**数値**:<br />-2147015167|外部パートナーからターゲット コネクタを削除できませんでした。|
> |**名前**:<br />FallbackCardFormDeactivation<br />**16 進数**:<br />8004F664<br />**数値**:<br />-2147158428|この操作を完了できません。 アクティブなカード フォームが少なくとも 1 つ必要です。|
> |**名前**:<br />FallbackFormDeactivation<br />**16 進数**:<br />8004F661<br />**数値**:<br />-2147158431|この操作を完了できません。 アクティブなメイン フォームが少なくとも 1 つ必要です。|
> |**名前**:<br />FallbackFormDeletion<br />**16 進数**:<br />8004F654<br />**数値**:<br />-2147158444|{1} エンティティに対する唯一の {0} 種類のフォールバック形式であるため、このフォームを削除できません。 各エンティティは、各フォームの種類に対して少なくとも 1 つのフォールバック フォームを持っている必要があります。|
> |**名前**:<br />FallbackMainInteractionCentricFormDeactivation<br />**16 進数**:<br />8004F666<br />**数値**:<br />-2147158426|この操作を完了できません。 アクティブな MainInterationCentric フォームが少なくとも 1 つ必要です。|
> |**名前**:<br />FallbackQuickFormDeactivation<br />**16 進数**:<br />8004F665<br />**数値**:<br />-2147158427|この操作を完了できません。 アクティブな簡易入力フォームが少なくとも 1 つ必要です。|
> |**名前**:<br />FaxNoData<br />**16 進数**:<br />80043516<br />**数値**:<br />-2147207914|送信するデータがないので FAX を送信することはできません。 送付状、FAX 添付書類、または FAX の説明のうち、少なくとも 1 つを指定してください。|
> |**名前**:<br />FaxNoSupport<br />**16 進数**:<br />80043517<br />**数値**:<br />-2147207913|この種類の添付書類が許可されていないか、この種類の添付書類では FAX 機器への仮想プリントがサポートされていないので、FAX を送信できません。|
> |**名前**:<br />FaxSendBlocked<br />**16 進数**:<br />80043510<br />**数値**:<br />-2147207920|受信者は、FAX の受信を許可していません。|
> |**名前**:<br />FaxServiceNotRunning<br />**16 進数**:<br />80043511<br />**数値**:<br />-2147207919|Microsoft Windows FAX サービスが起動されていないか、インストールされていません。|
> |**名前**:<br />FeatureNotEnabled<br />**16 進数**:<br />80061113<br />**数値**:<br />-2147086061|この操作を完了できませんでした。お客様の組織では、この機能が有効にされていません。|
> |**名前**:<br />FederatedEndpointError<br />**16 進数**:<br />80044505<br />**数値**:<br />-2147203835|目的の認証エンドポイントへのアクセスをブロックするため、ユーザー名 ADFS エンドポイントを有効化します。|
> |**名前**:<br />FeedbackFeatureNotEnabled<br />**16 進数**:<br />80061770<br />**数値**:<br />-2147084432|フィードバック機能が有効になっていません。|
> |**名前**:<br />FeedbackMinMaxRequired<br />**16 進数**:<br />80061772<br />**数値**:<br />-2147084430|最小値および最大値は必須です。|
> |**名前**:<br />FeedbackMinRatingValue<br />**16 進数**:<br />80061774<br />**数値**:<br />-2147084428|送信された評価の最小値 {0} は、送信された評価の最大値 {1} よりも小さい必要があります。|
> |**名前**:<br />FeedbackRatingValue<br />**16 進数**:<br />80061773<br />**数値**:<br />-2147084429|評価は {0} から {1} までの値である必要があります。|
> |**名前**:<br />FetchDataSetQueryTimeout<br />**16 進数**:<br />8005E00E<br />**数値**:<br />-2147098610|{0} 秒後にフェッチ データ セット クエリがタイムアウトしました。 クエリのタイムアウトの値を増やし、もう一度実行してください。|
> |**名前**:<br />FieldLevelSecurityNotSupported<br />**16 進数**:<br />80044817<br />**数値**:<br />-2147203049|フィールド レベルのセキュリティは仮想エンティティでサポートされていません。|
> |**名前**:<br />FileInUse<br />**16 進数**:<br />80048837<br />**数値**:<br />-2147186633|別のアプリケーションで使用されているので、ファイルを読み取ることができません。|
> |**名前**:<br />FileNotFound<br />**16 進数**:<br />80048440<br />**数値**:<br />-2147187648|添付ファイルが見つかりませんでした。|
> |**名前**:<br />FilePickerErrorApplicationInSnapView<br />**16 進数**:<br />8005F20D<br />**数値**:<br />-2147094003|このアクションをやり直してください。 問題が解決しない場合は、ソリューションの {0} を確認するか、{#Brand_CRM} 管理者に問い合わせてください。 それでも解決しない場合には {1}に問い合わせてください。|
> |**名前**:<br />FilePickerErrorAttachmentTypeBlocked<br />**16 進数**:<br />8005F204<br />**数値**:<br />-2147094012|このアクションをやり直してください。 問題が解決しない場合は、ソリューションの {0} を確認するか、{#Brand_CRM} 管理者に問い合わせてください。 それでも解決しない場合には {1}に問い合わせてください。|
> |**名前**:<br />FilePickerErrorFileSizeBreached<br />**16 進数**:<br />8005F205<br />**数値**:<br />-2147094011|このアクションをやり直してください。 問題が解決しない場合は、ソリューションの {0} を確認するか、{#Brand_CRM} 管理者に問い合わせてください。 それでも解決しない場合には {1}に問い合わせてください。|
> |**名前**:<br />FilePickerErrorFileSizeCannotBeZero<br />**16 進数**:<br />8005F206<br />**数値**:<br />-2147094010|このアクションをやり直してください。 問題が解決しない場合は、ソリューションの {0} を確認するか、{#Brand_CRM} 管理者に問い合わせてください。 それでも解決しない場合には {1}に問い合わせてください。|
> |**名前**:<br />FilePickerErrorUnableToOpenFile<br />**16 進数**:<br />8005F207<br />**数値**:<br />-2147094009|このアクションをやり直してください。 問題が解決しない場合は、ソリューションの {0} を確認するか、{#Brand_CRM} 管理者に問い合わせてください。 それでも解決しない場合には {1}に問い合わせてください。|
> |**名前**:<br />FileReadError<br />**16 進数**:<br />80048437<br />**数値**:<br />-2147187657|ファイル システムからのファイルの読み取りでエラーが発生しました。 このファイルの読み取りアクセス許可があることを確認し、ファイルの移行をもう一度実行してください。|
> |**名前**:<br />FileSizeExceeded<br />**16 進数**:<br />80071026<br />**数値**:<br />-2147020762|ドキュメントをコピーできません。 選択されたファイルが、128 MB のサイズ制限の上限値を超えています。|
> |**名前**:<br />FileStoreFeatureNotEnabled<br />**16 進数**:<br />80072520<br />**数値**:<br />-2147015392|この組織で機能が有効になっていません|
> |**名前**:<br />FileTypeNotSupported<br />**16 進数**:<br />800609B4<br />**数値**:<br />-2147087948|指定されたファイルの種類はテンプレートとしてサポートされていません。|
> |**名前**:<br />FilteredDuetoAntiSpam<br />**16 進数**:<br />80040325<br />**数値**:<br />-2147220699|スパム対応設定によりこの顧客はフィルターされます。|
> |**名前**:<br />FilteredDuetoInactiveState<br />**16 進数**:<br />8004032a<br />**数値**:<br />-2147220694|この顧客は非アクティブ状態のためフィルターされます。|
> |**名前**:<br />FilteredDuetoMissingEmailAddress<br />**16 進数**:<br />8004032e<br />**数値**:<br />-2147220690|電子メール アドレスがないためこの顧客はフィルターされます。|
> |**名前**:<br />FinalMergedEntityIsNull<br />**16 進数**:<br />80060443<br />**数値**:<br />-2147089341|ビジネス プロセスの作成または更新時のエラー: 最終結合エンティティは Null にできません。|
> |**名前**:<br />FirstStageIdInTraversedPathDoesNotMatchFirstStageIdInBusinessProcess<br />**16 進数**:<br />80060456<br />**数値**:<br />-2147089322|渡ったパス ‘{0}’ の最初のステージ ID が、ビジネス プロセス ‘{1}’ の最初のステージ ID と一致しません。 システム管理者にお問い合わせください。|
> |**名前**:<br />FiscalPeriodGoalMissingInfo<br />**16 進数**:<br />80044903<br />**数値**:<br />-2147202813|会計期間型の目標の場合、会計期間属性を設定する必要があります。|
> |**名前**:<br />FiscalSettingsAlreadyUpdated<br />**16 進数**:<br />80043809<br />**数値**:<br />-2147207159|会計設定が既に更新されています。 更新できるのは 1 回のみです。|
> |**名前**:<br />FlowIsNotActive<br />**16 進数**:<br />80060469<br />**数値**:<br />-2147089303|フロー ステップで使用するには、モダン フローがアクティブである必要があります。|
> |**名前**:<br />FlowMissingRecord<br />**16 進数**:<br />80050262<br />**数値**:<br />-2147155358|このフローをトリガーするには、少なくとも 1 つのレコードを選択する必要があります。|
> |**名前**:<br />FlowServiceClientError<br />**16 進数**:<br />80060467<br />**数値**:<br />-2147089305|フロー クライアント エラーがステータス コード "{0}"、詳細情報 "{1}" で返されました。|
> |**名前**:<br />FlowTriggerNotificationDisabled<br />**16 進数**:<br />80072342<br />**数値**:<br />-2147015870|組織に対してフロー トリガー通知が無効になっています。|
> |**名前**:<br />FlowTriggerNotificationFailed<br />**16 進数**:<br />80072341<br />**数値**:<br />-2147015871|http ポスト中にフロー トリガー通知の呼び出しが失敗しました。 詳細については例外を確認してください。|
> |**名前**:<br />FolderDoesNotExist<br />**16 進数**:<br />80060901<br />**数値**:<br />-2147088127|フォルダーは存在しません。|
> |**名前**:<br />無効<br />**16 進数**:<br />8005F102<br />**数値**:<br />-2147094270|サーバーはリクエストを履行するのを拒否します。|
> |**名前**:<br />FormDoesNotExist<br />**16 進数**:<br />80048406<br />**数値**:<br />-2147187706|フォームは存在しません|
> |**名前**:<br />FormTransitionError<br />**16 進数**:<br />80040242<br />**数値**:<br />-2147220926|システムがエンティティ フォーム {0} をアンマネージドからマネージドに遷移できないため、インポートは失敗しました。 少なくとも 1 つの完全 (ルート) コンポーネントをマネージド ソリューションに追加し、再度インポートします。|
> |**名前**:<br />ForwardMailboxCannotAssociateWithUser<br />**16 進数**:<br />8005E207<br />**数値**:<br />-2147098105|特定のユーザーまたはキューの転送用メールボックスを作成できません。  関連フィールドを削除しやり直してください。|
> |**名前**:<br />ForwardMailboxEmailAddressRequired<br />**16 進数**:<br />8005E211<br />**数値**:<br />-2147098095|転送用メールボックスの場合、電子メール アドレスは必須フィールドです。|
> |**名前**:<br />ForwardMailboxUnexpectedIncomingDeliveryMethod<br />**16 進数**:<br />8005E212<br />**数値**:<br />-2147098094|転送用メールボックスの受信メールの配信方法は、[なし] または [Router] のみです。|
> |**名前**:<br />ForwardMailboxUnexpectedOutgoingDeliveryMethod<br />**16 進数**:<br />8005E213<br />**数値**:<br />-2147098093|転送用メールボックスの送信メールの配信方法は、[なし] のみです。|
> |**名前**:<br />GenericActiveDirectoryError<br />**16 進数**:<br />80041d37<br />**数値**:<br />-2147214025|Active Directory エラー。|
> |**名前**:<br />GenericAzureActiveDirectoryError<br />**16 進数**:<br />80041d54<br />**数値**:<br />-2147213996|Azure Active Directory エラー。|
> |**名前**:<br />GenericImportTranslationsError<br />**16 進数**:<br />80060752<br />**数値**:<br />-2147088558|トランザクション インポート ファイルを処理中にエラーが発生しました。|
> |**名前**:<br />GenericManagedPropertyFailure<br />**16 進数**:<br />8004F026<br />**数値**:<br />-2147160026|現在の操作 ({2}) 内の現在のコンポーネント (名前={0}、ID={1}) の評価は、マネージド プロパティの次の条件の評価中に失敗しました: {3}|
> |**名前**:<br />GenericMetadataSyncFailed<br />**16 進数**:<br />8005F246<br />**数値**:<br />-2147093946|問題が発生しました。 操作をやり直すか、アプリを再起動してください。|
> |**名前**:<br />GenericMetadataSyncFailedWithContinue<br />**16 進数**:<br />8005F247<br />**数値**:<br />-2147093945|申し訳ございません。サーバー構成の変更のダウンロードに問題が発生しました。  アプリは引き続き古い構成で使用できます。しかし、保存時のエラーなど何らかの問題が発生することがあります。  この問題が続く場合は、Dynamics 365 管理者に問い合わせて、'詳細情報' を選択する際に利用可能な情報を提供してください。|
> |**名前**:<br />GenericTransformationInvocationError<br />**16 進数**:<br />8004037b<br />**数値**:<br />-2147220613|変換は無効なデータを返しました。|
> |**名前**:<br />GetPhotoFromGalleryFailed<br />**16 進数**:<br />8005F208<br />**数値**:<br />-2147094008|このアクションをやり直してください。 問題が解決しない場合は、ソリューションの {0} を確認するか、{#Brand_CRM} 管理者に問い合わせてください。 それでも解決しない場合には {1}に問い合わせてください。|
> |**名前**:<br />GetTenantIdFailure<br />**16 進数**:<br />80071109<br />**数値**:<br />-2147020535|TenantId の取得中にエラーが発生しました。|
> |**名前**:<br />GoalAttributeAlreadyMapped<br />**16 進数**:<br />80044807<br />**数値**:<br />-2147203065|指定された目標属性の指標の詳細は既に存在します。|
> |**名前**:<br />GoalMissingPeriodTypeInfo<br />**16 進数**:<br />80044908<br />**数値**:<br />-2147202808|目標期間の種類は、目標の作成時に指定される必要があります。 このフィールドを null に設定することはできません。|
> |**名前**:<br />GoalPercentageAchievedValueOutOfRange<br />**16 進数**:<br />8004F682<br />**数値**:<br />-2147158398|計算された値は許容範囲内にないため、達成率値は 0 に設定されました。|
> |**名前**:<br />GoOfflineBCPFileSize<br />**16 進数**:<br />80044224<br />**数値**:<br />-2147204572|クライアントは BCP ファイルをダウンロードできませんでした。 システム管理者に問い合わせて、オフラインにし直してください。|
> |**名前**:<br />GoOfflineDbSizeLimit<br />**16 進数**:<br />80044222<br />**数値**:<br />-2147204574|オフライン データベースの記憶域の上限に達しました。 ローカル データ グループを変更して、オフライン状態にするデータ量を減らしてください。|
> |**名前**:<br />GoOfflineEmptyFileForDelete<br />**16 進数**:<br />80044230<br />**数値**:<br />-2147204560|削除用のデータ ファイルが空です。|
> |**名前**:<br />GoOfflineFailedMoveData<br />**16 進数**:<br />80044225<br />**数値**:<br />-2147204571|クライアントはデータをダウンロードできませんでした。 システム管理者に問い合わせて、オフラインにし直してください。|
> |**名前**:<br />GoOfflineFailedPrepareMsde<br />**16 進数**:<br />80044226<br />**数値**:<br />-2147204570|MSDE の準備に失敗しました。 システム管理者に問い合わせて、オフラインにし直してください。|
> |**名前**:<br />GoOfflineFailedReloadMetadataCache<br />**16 進数**:<br />80044227<br />**数値**:<br />-2147204569|Microsoft Dynamics 365 for Outlook をオフラインにできませんでした。 オフラインにし直してください。|
> |**名前**:<br />GoOfflineFileWasDeleted<br />**16 進数**:<br />80044229<br />**数値**:<br />-2147204567|データ ファイルは、クライアントへ送信される前にサーバーで削除されました。|
> |**名前**:<br />GoOfflineGetBCPFileException<br />**16 進数**:<br />80044221<br />**数値**:<br />-2147204575|Dynamics 365 server が要求を処理できませんでした。 システム管理者に問い合わせて、オフラインにし直してください。|
> |**名前**:<br />GoOfflineMetadataVersionsMismatch<br />**16 進数**:<br />80044220<br />**数値**:<br />-2147204576|クライアントおよびサーバー メタデータのバージョンは、サーバーの新しいカスタマイズにより異なります。 オフラインにし直してください。|
> |**名前**:<br />GoOfflineServerFailedGenerateBCPFile<br />**16 進数**:<br />80044223<br />**数値**:<br />-2147204573|Dynamics 365 server は BCP ファイルを生成できませんでした。 システム管理者に問い合わせて、オフラインにし直してください。|
> |**名前**:<br />GraphApiS2SSetupFailureException<br />**16 進数**:<br />80044260<br />**数値**:<br />-2147204512|Exchange による Office Graph API 用のサーバー間認証が設定されていません。|
> |**名前**:<br />GuidNotPresent<br />**16 進数**:<br />80040362<br />**数値**:<br />-2147220638|この行で必要なグローバル一意識別子 (GUID) は存在しません|
> |**名前**:<br />HeaderValueDoesNotMatchAttributeDisplayLabel<br />**16 進数**:<br />80040370<br />**数値**:<br />-2147220624|タイトル行が属性表示ラベルと一致しません。|
> |**名前**:<br />HiddenPropertyValidationFailed<br />**16 進数**:<br />80061000<br />**数値**:<br />-2147086336|非表示プロパティのプロパティ インスタンスを作成することはできません。|
> |**名前**:<br />HiddensheetNotAvailable<br />**16 進数**:<br />800609B6<br />**数値**:<br />-2147087946|非表示シートを使用できません。|
> |**名前**:<br />HierarchicalOperationFailed<br />**16 進数**:<br />8008100F<br />**数値**:<br />-2146955249|この操作はこの階層で完了できませんでした。 {0} に対してこの操作の実行中にエラーが発生しました。 エラーを修正するためにこの製品に対して操作を個別に実行できます。その後で、全階層に対して操作をやり直してください。|
> |**名前**:<br />HierarchyCalculateLimitReached<br />**16 進数**:<br />80060547<br />**数値**:<br />-2147089081|マスター レコードの階層の深さ制限 {0} に達したため、計算をオンラインで実行できません。|
> |**名前**:<br />HipInvalidCertificate<br />**16 進数**:<br />8004Ed45<br />**数値**:<br />-2147160763|HIP を使用するための証明書は無効です。|
> |**名前**:<br />HipNoSettingError<br />**16 進数**:<br />8004Ed44<br />**数値**:<br />-2147160764|HIP アプリケーションの構成設定 [{0}] が見つかりませんでした。|
> |**名前**:<br />HonorPauseWithoutSLAKPIError<br />**16 進数**:<br />80045000<br />**数値**:<br />-2147201024|SLA は、一時停止を履行し、[はい] に設定されている SLA KPI が使用されている場合のみ再開するように設定できます。|
> |**名前**:<br />HybridSSSExchangeOnlineS2SCertActsExpired<br />**16 進数**:<br />80131500<br />**数値**:<br />-2146233088|Dynamics 365 設置型 + Exchange Online の S2S 認証を使用した証明書が期限切れになりました。|
> |**名前**:<br />HybridSSSExchangeOnlineS2SCertExpired<br />**16 進数**:<br />80131509<br />**数値**:<br />-2146233079|Dynamics 365 設置型 + Exchange Online の S2S 認証を使用した証明書が期限切れになりました。|
> |**名前**:<br />ImportArticleTemplateError<br />**16 進数**:<br />8004800D<br />**数値**:<br />-2147188723|Import Xml で記事テンプレートの解析中にエラーが発生しました|
> |**名前**:<br />ImportAttributeNameError<br />**16 進数**:<br />80048062<br />**数値**:<br />-2147188638|属性の名前が無効です {0}。  カスタム属性名は、有効なカスタマイズの接頭辞で始まる必要があります。 ソリューション コンポーネントの接頭辞は、ソリューションの発行者に対して指定された接頭辞に対応している必要があります。|
> |**名前**:<br />ImportChannelPropertyGroupError<br />**16 進数**:<br />800608F3<br />**数値**:<br />-2147088141|チャネル プロパティ グループをインポート中にエラーが発生しました。|
> |**名前**:<br />ImportComponentDeletedIgnored<br />**16 進数**:<br />8004847c<br />**数値**:<br />-2147187588|この Microsoft Dynamics 365 組織に存在しないため、このコンポーネントを更新できません。|
> |**名前**:<br />ImportConfigNotSpecified<br />**16 進数**:<br />80040322<br />**数値**:<br />-2147220702|インポート構成が指定されていないため、一括インポートを処理することはできません。|
> |**名前**:<br />ImportContractTemplateError<br />**16 進数**:<br />8004800B<br />**数値**:<br />-2147188725|Import Xml で契約テンプレートの解析中にエラーが発生しました|
> |**名前**:<br />ImportConvertRuleError<br />**16 進数**:<br />8004F869<br />**数値**:<br />-2147157911|変換ルールのインポート中にエラーが発生しました。|
> |**名前**:<br />ImportCustomizationsBadZipFileError<br />**16 進数**:<br />80048060<br />**数値**:<br />-2147188640|ソリューション ファイルが無効です。 圧縮ファイルは、そのルートに次のファイルを含んでいる必要があります: solution.xml、customizations.xml、[Content_Types].xml。 Microsoft Dynamics 365 の以前のバージョンからエクスポートされたカスタマイズ ファイルは、サポートされていません。|
> |**名前**:<br />ImportDashboardDeletedError<br />**16 進数**:<br />8004E308<br />**数値**:<br />-2147163384|同じ ID を持つダッシュボードは、システムで削除のマークが付けられています。 システム フォーム エンティティを公開してから、インポートし直してください。|
> |**名前**:<br />ImportDefaultAsPackageError<br />**16 進数**:<br />80048049<br />**数値**:<br />-2147188663|既定のソリューションに対して提供されるパッケージは、マネージド モードにインストールしようとしています。 既定のソリューションは管理できません。 既定のソリューション用の XML で、Managed 値を "false" に戻して、ソリューションをインポートし直してください。|
> |**名前**:<br />ImportDependencySolutionError<br />**16 進数**:<br />80048034<br />**数値**:<br />-2147188684|{0} は、現在インストールされていないソリューションを要求します。 これをインポートする前に、次のソリューションをインポートします。 {1} |
> |**名前**:<br />ImportDuplicateEntity<br />**16 進数**:<br />8004810c<br />**数値**:<br />-2147188468|同じ名前 {0} を持つ別のエンティティが既に対象組織に存在します。|
> |**名前**:<br />ImportEmailTemplateError<br />**16 進数**:<br />8004800C<br />**数値**:<br />-2147188724|Import Xml で電子メール テンプレートの解析中にエラーが発生しました|
> |**名前**:<br />ImportEmailTemplateErrorMissingFile<br />**16 進数**:<br />8004802B<br />**数値**:<br />-2147188693|電子メール テンプレート '{0}' のインポート: インポートする zip ファイルの中に添付ファイル '{1}' がありません。|
> |**名前**:<br />ImportEmailTemplatePersonalError<br />**16 進数**:<br />80048014<br />**数値**:<br />-2147188716|電子メール テンプレートがインポートされませんでした。 テンプレートはターゲット システムの個人用テンプレートです; インポートでは個人用テンプレートを上書きすることはできません。|
> |**名前**:<br />ImportEntityCustomResourcesError<br />**16 進数**:<br />80048002<br />**数値**:<br />-2147188734|インポート ファイルのカスタム リソースは無効です。|
> |**名前**:<br />ImportEntityCustomResourcesNewStringError<br />**16 進数**:<br />80048003<br />**数値**:<br />-2147188733|カスタム リソース内の新しい文字エンティティは無効です。|
> |**名前**:<br />ImportEntityIconError<br />**16 進数**:<br />80048001<br />**数値**:<br />-2147188735|インポート ファイルに無効なアイコンがあります。|
> |**名前**:<br />ImportEntityNameMismatchError<br />**16 進数**:<br />80048008<br />**数値**:<br />-2147188728|入力文字列に渡されたフォーマット パラメーター数が正しくありません|
> |**名前**:<br />ImportEntitySystemUserLiveMismatchError<br />**16 進数**:<br />80048025<br />**数値**:<br />-2147188699|systemuser エンティティはインポートされましたが、このエンティティ用にカスタマイズされたフォームはインポートされませんでした。 Microsoft Dynamics 365の設置型またはホスト バージョンの Systemuser エンティティ フォームは、Microsoft Dynamics 365 Online にインポートできません。|
> |**名前**:<br />ImportEntitySystemUserOnPremiseMismatchError<br />**16 進数**:<br />80048024<br />**数値**:<br />-2147188700|systemuser エンティティはインポートされましたが、このエンティティ用にカスタマイズされたフォームはインポートされませんでした。 Microsoft Dynamics 365 Online の systemuser エンティティ フォームは、設置型またはホスト バージョンの Microsoft Dynamics 365 にインポートできません。|
> |**名前**:<br />ImportExportDeprecatedError<br />**16 進数**:<br />80048045<br />**数値**:<br />-2147188667|このメッセージは現在利用できません。 代替メッセージに関する SDK を参照してください。|
> |**名前**:<br />ImportFieldSecurityProfileAttributesMissingError<br />**16 進数**:<br />80048064<br />**数値**:<br />-2147188636|次のフィールドがシステムにないため、いくつかのフィールド セキュリティのアクセス許可をインポートできませんでした: {0}。|
> |**名前**:<br />ImportFieldSecurityProfileIsSecuredMissingError<br />**16 進数**:<br />80048063<br />**数値**:<br />-2147188637|次のフィールドがセキュリティ保護可能でないため、いくつかのフィールド セキュリティのアクセス許可をインポートできませんでした: {0}。|
> |**名前**:<br />ImportFieldXmlError<br />**16 進数**:<br />80048006<br />**数値**:<br />-2147188730|入力文字列に渡されたフォーマット パラメーター数が正しくありません|
> |**名前**:<br />ImportFileFailed<br />**16 進数**:<br />80050125<br />**数値**:<br />-2147155675|ファイルのインポートと抽出に失敗しました。|
> |**名前**:<br />ImportFileSignatureInvalid<br />**16 進数**:<br />80048065<br />**数値**:<br />-2147188635|インポート ファイルのデジタル署名が無効です。|
> |**名前**:<br />ImportFileTooLargeToUpload<br />**16 進数**:<br />80040375<br />**数値**:<br />-2147220619|インポート ファイルは大きすぎるため、アップロードできません。|
> |**名前**:<br />ImportFormXmlError<br />**16 進数**:<br />80048007<br />**数値**:<br />-2147188729|入力文字列に渡されたフォーマット パラメーター数が正しくありません|
> |**名前**:<br />ImportGenericEntitiesError<br />**16 進数**:<br />80048020<br />**数値**:<br />-2147188704|汎用エンティティのインポート中にエラーが発生しました。|
> |**名前**:<br />ImportGenericError<br />**16 進数**:<br />8004801E<br />**数値**:<br />-2147188706|インポートに失敗しました。 詳細については、関連するエラー メッセージを参照してください。|
> |**名前**:<br />ImportHierarchyRuleDeletedError<br />**16 進数**:<br />8004F9A1<br />**数値**:<br />-2147157599|同じ ID を持つ階層ルールが、このシステムで削除のマークが付けられています。そのため、カスタマイズされたエンティティを公開してから、インポートし直します。|
> |**名前**:<br />ImportHierarchyRuleExistingError<br />**16 進数**:<br />8004F9A2<br />**数値**:<br />-2147157598|既存の階層ルールを再利用することはできません。|
> |**名前**:<br />ImportHierarchyRuleOtcMismatchError<br />**16 進数**:<br />8004F9A3<br />**数値**:<br />-2147157597|同じオブジェクトの種類コードの階層ルールの処理中にエラーが発生しました。(解決できないシステム競合)|
> |**名前**:<br />ImportInvalidFileError<br />**16 進数**:<br />80048000<br />**数値**:<br />-2147188736|無効なインポート マップ ファイルです|
> |**名前**:<br />ImportInvalidXmlError<br />**16 進数**:<br />8004802C<br />**数値**:<br />-2147188692|このソリューション パッケージは無効な XML を含んでいるため、インポートできません。 スキーマ検証エラーの情報に基づいて XML コンテンツを手動で編集し、ファイルを修正するか、ソリューション プロバイダーに問い合わせてください。|
> |**名前**:<br />ImportIsvConfigError<br />**16 進数**:<br />8004800E<br />**数値**:<br />-2147188722|インポート時の IsvConfig 解析中にエラーが発生しました|
> |**名前**:<br />ImportLanguagesIgnoredError<br />**16 進数**:<br />80048026<br />**数値**:<br />-2147188698|以下の言語はこの組織に対して有効にされていないので、それらの言語用に翻訳されたラベルをインポートできませんでした: {0}|
> |**名前**:<br />ImportMailMergeTemplateEntityMissingError<br />**16 進数**:<br />80048480<br />**数値**:<br />-2147187584|差し込み印刷用テンプレート {0} は、このテンプレートに関連付けられた{1}エンティティがターゲット システムにないため、インポートされませんでした。|
> |**名前**:<br />ImportMailMergeTemplateError<br />**16 進数**:<br />80048456<br />**数値**:<br />-2147187626|Import Xml で差し込み印刷テンプレートの解析中にエラーが発生しました|
> |**名前**:<br />ImportMapInUse<br />**16 進数**:<br />80048465<br />**数値**:<br />-2147187611|選択したデータ マップの中に、データのインポートで現在使用されているために削除できないものがあります。|
> |**名前**:<br />ImportMappingsInvalidIdSpecified<br />**16 進数**:<br />80048427<br />**数値**:<br />-2147187673|XML ファイルに複数の無効な ID があります。 指定された ID は、一意の識別子として使用することはできません。|
> |**名前**:<br />ImportMappingsMissingEntityMapError<br />**16 進数**:<br />80048010<br />**数値**:<br />-2147188720|このカスタマイズ ファイルには、ターゲット システムに存在しないエンティティ マップへの参照も含まれます。|
> |**名前**:<br />ImportMappingsSystemMapError<br />**16 進数**:<br />8004800F<br />**数値**:<br />-2147188721|インポートはシステム属性マッピングを作成できません|
> |**名前**:<br />ImportMissingComponent<br />**16 進数**:<br />8004801F<br />**数値**:<br />-2147188705|ターゲット システムに存在しないため、種類 {1} のルート コンポーネント {0}を追加することはできません。|
> |**名前**:<br />ImportMissingDependenciesError<br />**16 進数**:<br />8004801D<br />**数値**:<br />-2147188707|次のソリューションはインポートできません: {0}。 一部の依存関係がありません。|
> |**名前**:<br />ImportMissingRootComponentEntry<br />**16 進数**:<br />8004803A<br />**数値**:<br />-2147188678|種類 {1} のコンポーネント {0} がソリューション ファイルでルート コンポーネントとして宣言されていないため、インポートは失敗しました。 これを修正するには、ソリューションをエクスポートしたときに生成された XML ファイルを使用して再度インポートします。|
> |**名前**:<br />ImportMobileOfflineProfileError<br />**16 進数**:<br />8006099F<br />**数値**:<br />-2147087969|Mobile Offline プロファイルをインポートしているときに、エラーが発生しました。|
> |**名前**:<br />ImportNewPluginTypesError<br />**16 進数**:<br />80048071<br />**数値**:<br />-2147188623|既存のプラグインの種類が削除されました。 プラグイン アセンブリのメジャー バージョンまたはマイナー バージョンを更新してください。|
> |**名前**:<br />ImportNonWellFormedFileError<br />**16 進数**:<br />80048013<br />**数値**:<br />-2147188717|無効なカスタマイズ ファイルです。 このファイルは適切な形式ではありません。|
> |**名前**:<br />ImportNotComplete<br />**16 進数**:<br />80048472<br />**数値**:<br />-2147187598|1 つまたは複数のインポートが完了状態にありません。 インポートされたレコードは完了したジョブからのみ削除されます。 ジョブが完了するまで待ってからもう一度やり直してください。|
> |**名前**:<br />ImportOperationChildFailure<br />**16 進数**:<br />80044334<br />**数値**:<br />-2147204300|1 つまたは複数のインポートの子ジョブが失敗しました。|
> |**名前**:<br />ImportOptionSetAttributeError<br />**16 進数**:<br />80048039<br />**数値**:<br />-2147188679|属性 '{0}' は、存在しないグローバル オプション セット ('{1}') を参照しているのでインポートされませんでした。|
> |**名前**:<br />ImportOptionSetsError<br />**16 進数**:<br />80048030<br />**数値**:<br />-2147188688|OptionSets のインポートでエラーが発生しました。|
> |**名前**:<br />ImportOrgSettingsError<br />**16 進数**:<br />80048019<br />**数値**:<br />-2147188711|インポート時の組織の設定の解析中にエラーが発生しました|
> |**名前**:<br />ImportPluginTypesError<br />**16 進数**:<br />80048012<br />**数値**:<br />-2147188718|プラグインの種類のインポート中にエラーが発生しました。|
> |**名前**:<br />ImportRelationshipRoleMapsError<br />**16 進数**:<br />8004800A<br />**数値**:<br />-2147188726|入力文字列に渡されたフォーマット パラメーター数が正しくありません|
> |**名前**:<br />ImportRelationshipRolesError<br />**16 進数**:<br />80048009<br />**数値**:<br />-2147188727|入力文字列に渡されたフォーマット パラメーター数が正しくありません|
> |**名前**:<br />ImportRelationshipRolesPrivilegeError<br />**16 進数**:<br />8004802F<br />**数値**:<br />-2147188689|{0} をインポートできません。 このコンポーネントをインポートするには、{1} 特権が必要です。|
> |**名前**:<br />ImportReportsError<br />**16 進数**:<br />80048032<br />**数値**:<br />-2147188686|レポートのインポートでエラーが発生しました。|
> |**名前**:<br />ImportRestrictedSolutionError<br />**16 進数**:<br />8004F007<br />**数値**:<br />-2147160057|指定されたソリューション ID は制限されているので、インポートできません。|
> |**名前**:<br />ImportRibbonsError<br />**16 進数**:<br />80048031<br />**数値**:<br />-2147188687|リボンのインポートでエラーが発生しました。|
> |**名前**:<br />ImportRoleError<br />**16 進数**:<br />80048017<br />**数値**:<br />-2147188713|セキュリティ ロールをインポートできません。 指定されたロール ID を持つロールが更新できないか、またはロール名が一意ではありません。|
> |**名前**:<br />ImportRolePermissionError<br />**16 進数**:<br />80048018<br />**数値**:<br />-2147188712|セキュリティ ロールをインポートするのに必要な特権がありません。|
> |**名前**:<br />ImportRoutingRuleError<br />**16 進数**:<br />8004F867<br />**数値**:<br />-2147157913|ルーティング規則セットのインポート中にエラーが発生しました。|
> |**名前**:<br />ImportSavedQueryDeletedError<br />**16 進数**:<br />8004801B<br />**数値**:<br />-2147188709|同じ ID を持つ保存済みクエリは、システムで削除のマークが付けられています。 カスタマイズされたエンティティを公開してから、インポートし直してください。|
> |**名前**:<br />ImportSavedQueryExistingError<br />**16 進数**:<br />80048005<br />**数値**:<br />-2147188731|入力文字列に渡されたフォーマット パラメーター数が正しくありません|
> |**名前**:<br />ImportSavedQueryOtcMismatchError<br />**16 進数**:<br />80048004<br />**数値**:<br />-2147188732|同じオブジェクトの種類コードの保存済みクエリの処理中にエラーが発生しました (解決できないシステム競合)|
> |**名前**:<br />ImportSdkMessagesError<br />**16 進数**:<br />80048016<br />**数値**:<br />-2147188714|SDK メッセージのインポート中にエラーが発生しました。|
> |**名前**:<br />ImportSiteMapError<br />**16 進数**:<br />80048011<br />**数値**:<br />-2147188719|サイト マップのインポート中にエラーが発生しました。|
> |**名前**:<br />ImportSlaError<br />**16 進数**:<br />8004F868<br />**数値**:<br />-2147157912|SLA のインポートでエラーが発生しました。|
> |**名前**:<br />ImportSolutionError<br />**16 進数**:<br />80048033<br />**数値**:<br />-2147188685|ソリューションのインポートでエラーが発生しました。|
> |**名前**:<br />ImportSolutionIsvConfigWarning<br />**16 進数**:<br />80048042<br />**数値**:<br />-2147188670|ISV 構成が上書きされました。|
> |**名前**:<br />ImportSolutionManagedError<br />**16 進数**:<br />80048038<br />**数値**:<br />-2147188680|ソリューション '{0}' はマネージド ソリューションとして既にこのシステムに存在しているので、アップグレードできません。|
> |**名前**:<br />ImportSolutionManagedToUnmanagedMismatch<br />**16 進数**:<br />80048040<br />**数値**:<br />-2147188672|このソリューションはアンマネージド ソリューションとして既にこのシステムにインストールされていますが、指定されたパッケージはソリューションをマネージド モードでインストールしようとしています。 インポートは、モードが一致する場合にのみソリューションを更新できます。 現在のソリューションをアンインストールし、もう一度やり直してください。|
> |**名前**:<br />ImportSolutionOrganizationSettingsWarning<br />**16 進数**:<br />80048044<br />**数値**:<br />-2147188668|組織の設定が上書きされました。|
> |**名前**:<br />ImportSolutionPackageInvalidSku<br />**16 進数**:<br />8004806B<br />**数値**:<br />-2147188629|インポートしようとしているソリューション パッケージは、Microsoft Dynamics 365 Online で作成されたものです。設置型またはホストされたバージョンの Microsoft Dynamics 365 にインポートすることはできません。|
> |**名前**:<br />ImportSolutionPackageInvalidSolutionPackageVersion<br />**16 進数**:<br />80048068<br />**数値**:<br />-2147188632|{0} 以前のパッケージ バージョンのソリューションのみをこの組織にインポートできます。 また、Microsoft Dynamics 365 2011 またはそれ以前からエクスポートされたソリューションをこの組織にインポートすることはできません。|
> |**名前**:<br />ImportSolutionPackageMinimumVersionNeeded<br />**16 進数**:<br />00000001<br />**数値**:<br />1|統合中に問題が発生するかもしれないため、現在削除するのでなく廃止されました。|
> |**名前**:<br />ImportSolutionPackageNeedsUpgrade<br />**16 進数**:<br />80048067<br />**数値**:<br />-2147188633|インポートするソリューション パッケージが Microsoft Dynamics 365 の異なるバージョンで生成されました。 パッケージはインポートの前に変換されます。 パッケージのバージョン: {0} {1}、 システムのバージョン: {2} {3}。|
> |**名前**:<br />ImportSolutionPackageNotValid<br />**16 進数**:<br />80048066<br />**数値**:<br />-2147188634|インポートしようとしているソリューション パッケージは、このシステムにはインポートできない Microsoft Dynamics 365 のバージョンで生成されたものです。 パッケージのバージョン: {0} {1}、 システムのバージョン: {2} {3}。|
> |**名前**:<br />ImportSolutionPackageRequiresOptInAvailable<br />**16 進数**:<br />80048069<br />**数値**:<br />-2147188631|インポートしようとしているソリューション パッケージの一部のコンポーネントはオプトインが必要です。 オプトインが使用できます。管理者に連絡してください。|
> |**名前**:<br />ImportSolutionPackageRequiresOptInNotAvailable<br />**16 進数**:<br />8004806A<br />**数値**:<br />-2147188630|インポートするソリューション パッケージが Microsoft Dynamics 365 がサポートするオプトインの SKU で生成されました。 このシステムにはインポートできません。|
> |**名前**:<br />ImportSolutionSiteMapWarning<br />**16 進数**:<br />80048043<br />**数値**:<br />-2147188669|SiteMap が上書きされました。|
> |**名前**:<br />ImportSolutionUnmanagedToManagedMismatch<br />**16 進数**:<br />80048041<br />**数値**:<br />-2147188671|このソリューションはマネージド ソリューションとして既にこのシステムにインストールされていますが、指定されたパッケージはソリューションをアンマネージド モードでインストールしようとしています。 インポートは、モードが一致する場合にのみソリューションを更新できます。 現在のソリューションをアンインストールし、もう一度やり直してください。|
> |**名前**:<br />ImportSystemSolutionError<br />**16 進数**:<br />80048046<br />**数値**:<br />-2147188666|システム ソリューションはインポートできません。|
> |**名前**:<br />ImportTemplateLanguageIgnored<br />**16 進数**:<br />8004847a<br />**数値**:<br />-2147187590|Microsoft Dynamics 365 組織でその言語が有効でないため、このテンプレートをインポートできません。|
> |**名前**:<br />ImportTemplatePersonalIgnored<br />**16 進数**:<br />8004847b<br />**数値**:<br />-2147187589|Microsoft Dynamics 365 組織で "個人用" として設定されているため、このテンプレートをインポートできません。|
> |**名前**:<br />ImportTranslationMissingSolutionError<br />**16 進数**:<br />80048047<br />**数値**:<br />-2147188665|翻訳のインポート中にエラーが発生しました。 翻訳に関連したソリューションは、このシステムに存在しません。|
> |**名前**:<br />ImportTranslationsBadZipFileError<br />**16 進数**:<br />80048061<br />**数値**:<br />-2147188639|翻訳 ファイルが無効です。 圧縮ファイルは、そのルートに次のファイルを含む必要があります: {0}、[Content_Types].xml。|
> |**名前**:<br />ImportVisualizationDeletedError<br />**16 進数**:<br />8004E013<br />**数値**:<br />-2147164141|ID {0} を持つ保存されたクエリ ビジュアル化は、システムで削除の対象としてマークされています。 最初にカスタマイズされたエンティティを公開してから、インポートし直してください。|
> |**名前**:<br />ImportVisualizationExistingError<br />**16 進数**:<br />8004E014<br />**数値**:<br />-2147164140|ID {0} を持つ保存されたクエリ ビジュアル化は、既にシステムに存在し、新しいユーザー定義エンティティにより再使用はできません。|
> |**名前**:<br />ImportWillExceedCustomEntityQuota<br />**16 進数**:<br />8004b043<br />**数値**:<br />-2147176381|このインポート プロセスは、新しいユーザー定義エンティティ "{0}" をインポートしようとしています。 これは、この組織のカスタム エンティティの制限数を超えています。|
> |**名前**:<br />ImportWorkflowAttributeDependencyError<br />**16 進数**:<br />80048022<br />**数値**:<br />-2147188702|ワークフロー定義をインポートできません。 必須属性依存関係がありません。|
> |**名前**:<br />ImportWorkflowEntityDependencyError<br />**16 進数**:<br />80048023<br />**数値**:<br />-2147188701|ワークフロー定義をインポートできません。 必須エンティティ依存関係がありません。|
> |**名前**:<br />ImportWorkflowError<br />**16 進数**:<br />80048021<br />**数値**:<br />-2147188703|ワークフロー定義をインポートできません。 指定されたワークフロー ID を持つワークフローが更新できないか、またはワークフローの名前が一意ではありません。|
> |**名前**:<br />ImportWorkflowNameConflictError<br />**16 進数**:<br />80048027<br />**数値**:<br />-2147188697|ワークフロー {0} は、ターゲット システムに同じ名前で別の一意の ID を持つワークフローが存在するため、インポートできません。 このワークフローの名前を変更して、再試行します。|
> |**名前**:<br />ImportWorkflowPublishedError<br />**16 進数**:<br />80048028<br />**数値**:<br />-2147188696|ワークフロー {0} ({1}) は、ターゲット システムに同じ一意の ID を持つワークフローが公開されているため、インポートできません。 このワークフローのインポートを再度試みる前に、ターゲット システムでワークフローの公開を取り下げてください。|
> |**名前**:<br />ImportWrongPublisherError<br />**16 進数**:<br />8004801C<br />**数値**:<br />-2147188708|次のマネージド ソリューションはインポートできません: {0}。 発行者名を {1} から {2}に変更することはできません。|
> |**名前**:<br />ImportXsdValidationError<br />**16 進数**:<br />8004801A<br />**数値**:<br />-2147188710|インポート ファイルが無効です。 XSD 検証は次のエラーで失敗しました: '{0}'。 検証が次の場所で失敗しました: '...{1} <<<<<ERROR LOCATION>>>>> {2}...'."|
> |**名前**:<br />InaccessibleSmtpServer<br />**16 進数**:<br />8005E227<br />**数値**:<br />-2147098073|SMTP サーバーにアクセスすることはできません。 SMTP サーバーにアクセスが可能であることを確認してください。|
> |**名前**:<br />InactiveEmailServerProfile<br />**16 進数**:<br />8005E228<br />**数値**:<br />-2147098072|電子メール サーバー プロファイルが無効です。 無効プロファイルの電子メールを処理することはできません。|
> |**名前**:<br />InactiveMailbox<br />**16 進数**:<br />8005E219<br />**数値**:<br />-2147098087|メールボックスは非アクティブ状態です。 メールを送受信できるのはアクティブなメールボックスだけです。|
> |**名前**:<br />InactiveMetricSetOnGoal<br />**16 進数**:<br />8004F686<br />**数値**:<br />-2147158394|非アクティブな指標は、目標で設定することはできません。|
> |**名前**:<br />InactiveRollupQuerySetOnGoal<br />**16 進数**:<br />8004F685<br />**数値**:<br />-2147158395|非アクティブなロールアップ クエリは、目標で設定することはできません。|
> |**名前**:<br />IncidentCannotCancel<br />**16 進数**:<br />8004440e<br />**数値**:<br />-2147204082|このインシデントに対するオープンしている活動があるため、インシデントは取り消すことはできません。|
> |**名前**:<br />IncidentContractDoesNotHaveAllotments<br />**16 進数**:<br />80044403<br />**数値**:<br />-2147204093|この契約はサービス単位が不足しています。 この契約に対してサポート案件を作成できません。|
> |**名前**:<br />IncidentInvalidAllotmentType<br />**16 進数**:<br />8004440b<br />**数値**:<br />-2147204085|契約のサービス単位が無効です。|
> |**名前**:<br />IncidentInvalidContractLineStateForCreate<br />**16 進数**:<br />8004440d<br />**数値**:<br />-2147204083|この契約品目に対してサポート案件を作成できません。この契約品目は取り消されたか期限切れになっています。|
> |**名前**:<br />IncidentInvalidContractStateForCreate<br />**16 進数**:<br />80044400<br />**数値**:<br />-2147204096|契約状態により、この契約に対してサポート案件を作成できません。|
> |**名前**:<br />IncidentIsAlreadyClosedOrCancelled<br />**16 進数**:<br />80044411<br />**数値**:<br />-2147204079|既に [クローズ済み] または [キャンセル済み]|
> |**名前**:<br />IncidentMissingActivityRegardingObject<br />**16 進数**:<br />80044409<br />**数値**:<br />-2147204087|インシデント ID がありません。|
> |**名前**:<br />IncidentMissingContractDetail<br />**16 進数**:<br />80044401<br />**数値**:<br />-2147204095|契約詳細 ID がありません。|
> |**名前**:<br />IncidentNullSpentTimeOrBilled<br />**16 進数**:<br />8004440c<br />**数値**:<br />-2147204084|インシデントに費やされた timespent、または IncidentResolution 活動の IsBilled が NULL です。|
> |**名前**:<br />IncomingDeliveryIsForwardMailbox<br />**16 進数**:<br />8005E223<br />**数値**:<br />-2147098077|メールボックスからメールをポーリングすることはできません。 受信メールの配信方法が [転送用メールボックス] に設定されています。|
> |**名前**:<br />IncomingServerLocationAndSslSetToNo<br />**16 進数**:<br />8005E23E<br />**数値**:<br />-2147098050|HTTPS を使用する受信サーバーの場所を URL で指定しましたが、[受信接続に SSL を使用する] オプションが [いいえ] に設定されています。 オプションを [はい] に設定し、やり直してください。|
> |**名前**:<br />IncomingServerLocationAndSslSetToYes<br />**16 進数**:<br />8005E240<br />**数値**:<br />-2147098048|HTTP を使用する受信サーバーの場所を URL で指定しましたが、[受信接続に SSL を使用する] オプションが [はい] に設定されています。 HTTPS を使用するサーバーの場所を指定し、やり直してください。|
> |**名前**:<br />IncompatibleStepsEncountered<br />**16 進数**:<br />8006088B<br />**数値**:<br />-2147088245|データを変更するプラグインが読み取り専用の SDK メッセージとして登録されているため、EnforceReadOnlyPlugins 設定を有効にできません。 {0}|
> |**名前**:<br />IncompleteTransformationParameterMappingsFound<br />**16 進数**:<br />8004037d<br />**数値**:<br />-2147220611|1 つまたは複数の必須変換パラメーター値は定義済みのマッピングがありません。|
> |**名前**:<br />InconsistentAttributeNameCasing<br />**16 進数**:<br />8004F043<br />**数値**:<br />-2147159997|属性名に不整合な大文字小文字の区別を検出しました。予想される値: {0}、実際の値: {1}。|
> |**名前**:<br />InconsistentProductRelationshipState<br />**16 進数**:<br />8004F996<br />**数値**:<br />-2147157610|製品リレーションシップの他方にある行は使用できません。|
> |**名前**:<br />IncorrectActiveStageEntity<br />**16 進数**:<br />80060462<br />**数値**:<br />-2147089310|'{0}' エンティティにアクティブ ステージはありません。|
> |**名前**:<br />IncorrectAttributeValueType<br />**16 進数**:<br />80044354<br />**数値**:<br />-2147204268|{0} の無効な属性値の種類。 予想: {1}、検出: {2}|
> |**名前**:<br />IncorrectEntitySetName<br />**16 進数**:<br />8006089C<br />**数値**:<br />-2147088228|エンティティ セット名 {0} は、有効なカスタマイズの接頭辞で始まる必要があります。|
> |**名前**:<br />IncorrectSingleFileMultipleEntityMap<br />**16 進数**:<br />80048502<br />**数値**:<br />-2147187454|ImportMap の EntitiesPerFile が複数に設定されている場合、2 つ以上の定義済みエンティティ マッピングが必要です|
> |**名前**:<br />IncreasingDaysWillResetMobileOfflineData<br />**16 進数**:<br />80060991<br />**数値**:<br />-2147087983|モバイル デバイスの再同期および、Mobile offline データをリセットする日数を増やします。|
> |**名前**:<br />IndexOutOfRange<br />**16 進数**:<br />8005E008<br />**数値**:<br />-2147098616|インデックス {0} は {1}の範囲を超えています。 存在する要素数は {2} です。|
> |**名前**:<br />IndexSizeConstraintViolated<br />**16 進数**:<br />80060895<br />**数値**:<br />-2147088235|インデックス サイズがサイズの上限 {0} バイトを超えています。 キーが大きすぎます。 いくつかの列を削除するか、文字列列の文字列を短くしてください。|
> |**名前**:<br />InitializeErrorNoReadOnSource<br />**16 進数**:<br />8004F800<br />**数値**:<br />-2147158016|{0} レコードのいくつかのフィールドで読み取りアクセス権がないため、操作を完了できませんでした。|
> |**名前**:<br />InputParameterFieldIncorrect<br />**16 進数**:<br />80060378<br />**数値**:<br />-2147089544|入力パラメータ “{0}” が、構成された入力パラメータ フィールドと一致しません。 エラーが解決しない場合は、システム管理者に連絡して構成メタデータを確認してください。|
> |**名前**:<br />InsertOptionValueInvalidType<br />**16 進数**:<br />80044320<br />**数値**:<br />-2147204320|候補リスト、および状態属性にのみオプション値を追加できます。|
> |**名前**:<br />InstanceOutsideEffectiveRange<br />**16 進数**:<br />8004E115<br />**数値**:<br />-2147163883|操作を実行できません。 インスタンスは、有効な展開範囲の系列外にあります。|
> |**名前**:<br />InsufficientAccessMode<br />**16 進数**:<br />80044502<br />**数値**:<br />-2147203838|ユーザーには Dynamics 365 組織に対する読み取り / 書き込みアクセス権限がありません。|
> |**名前**:<br />InsufficientAuthTicket<br />**16 進数**:<br />8004A103<br />**数値**:<br />-2147180285|認証のために指定されたチケットがポリシーを満たしていません|
> |**名前**:<br />InsufficientColumnsInSubQuery<br />**16 進数**:<br />8004E022<br />**数値**:<br />-2147164126|サブクエリから利用できない外部クエリには 1 つ以上の列が必須です|
> |**名前**:<br />InsufficientCreatePrivilege<br />**16 進数**:<br />8006110A<br />**数値**:<br />-2147086070|外部パーティには、指定されたパラメーターで新しいレコードを作成する特権がありません。|
> |**名前**:<br />InsufficientPrivilegesSupportUser<br />**16 進数**:<br />80048345<br />**数値**:<br />-2147187899|サポート ユーザーはこの操作を実行するアクセス許可がありません。|
> |**名前**:<br />InsufficientPrivilegeToQueueOwner<br />**16 進数**:<br />80040520<br />**数値**:<br />-2147220192|このキューの所有者には、このキューを操作するための特権がありません。|
> |**名前**:<br />InsufficientRetrievePrivilege<br />**16 進数**:<br />80061109<br />**数値**:<br />-2147086071|外部パーティには、レコードを取得するための特権がありません。|
> |**名前**:<br />InsufficientTransformationParameters<br />**16 進数**:<br />80048506<br />**数値**:<br />-2147187450|変換マッピングを実行するためのパラメーターがありません。|
> |**名前**:<br />InsufficientUpdatePrivilege<br />**16 進数**:<br />8006110B<br />**数値**:<br />-2147086069|外部パーティには、レコードを更新するための特権がありません。|
> |**名前**:<br />IntegerValueOutOfRange<br />**16 進数**:<br />8004432F<br />**数値**:<br />-2147204305|検証エラーが発生しました。 入力した整数が、この属性に対して許可された値の範囲外です。|
> |**名前**:<br />IntegratedAuthenticationIsNotAllowed<br />**16 進数**:<br />80044301<br />**数値**:<br />-2147204351|統合認証は使用できません。|
> |**名前**:<br />InvalidAbsoluteUrlFormat<br />**16 進数**:<br />80048055<br />**数値**:<br />-2147188651|絶対 URL に無効な文字が含まれています。 別の名前を使用してください。 絶対 URL の末尾に、.aspx、.ashx、.asmx、.svc は使用できません。|
> |**名前**:<br />InvalidAccessMaskForTeamTemplate<br />**16 進数**:<br />80048335<br />**数値**:<br />-2147187915|無効なアクセス マスクがチーム テンプレートとして指定されました。|
> |**名前**:<br />InvalidAccessModeTransition<br />**16 進数**:<br />80041d66<br />**数値**:<br />-2147213978|ユーザーが Microsoft Dynamics 365 Online のライセンスを持っていないため、クライアント アクセス ライセンスを変更できません。 アクセス モードを変更するには、先に Microsoft Online Services ポータルで、このユーザーにライセンスを追加する必要があります。|
> |**名前**:<br />InvalidAccessRights<br />**16 進数**:<br />8004020d<br />**数値**:<br />-2147220979|無効なアクセス権です。|
> |**名前**:<br />InvalidAccessRightsPassed<br />**16 進数**:<br />80048347<br />**数値**:<br />-2147187897|無効なアクセス権が渡されました。|
> |**名前**:<br />InvalidActivityMimeAttachmentId<br />**16 進数**:<br />80050005<br />**数値**:<br />-2147155963|activityMimeAttachmentId が無効です。|
> |**名前**:<br />InvalidActivityOwnershipTypeMask<br />**16 進数**:<br />8004F120<br />**数値**:<br />-2147159776|活動として定義されているカスタム エンティティは、ユーザーまたはチームが所有する必要があります。|
> |**名前**:<br />InvalidActivityPartyAddress<br />**16 進数**:<br />80043518<br />**数値**:<br />-2147207912|1 人以上の活動関係者が無効な住所を含んでいます。|
> |**名前**:<br />InvalidActivityType<br />**16 進数**:<br />80040321<br />**数値**:<br />-2147220703|無効オブジェクトの種類は、配布活動に対して指定されました。|
> |**名前**:<br />InvalidActivityTypeForCampaignActivityPropagate<br />**16 進数**:<br />8004030f<br />**数値**:<br />-2147220721|有効な CommunicationActivity を指定する必要があります|
> |**名前**:<br />InvalidActivityTypeForList<br />**16 進数**:<br />80040305<br />**数値**:<br />-2147220731|指定したリストの種類の活動を作成できません。|
> |**名前**:<br />InvalidActivityXml<br />**16 進数**:<br />80043514<br />**数値**:<br />-2147207916|活動構成ファイルの Xml が無効です。|
> |**名前**:<br />InvalidAllotmentsCalc<br />**16 進数**:<br />800404ef<br />**数値**:<br />-2147220241|サービス単位: 残り + 使用済み != 合計|
> |**名前**:<br />InvalidAllotmentsOverage<br />**16 進数**:<br />8004430B<br />**数値**:<br />-2147204341|サービス単位の超過分が無効です。|
> |**名前**:<br />InvalidAllotmentsRemaining<br />**16 進数**:<br />800404f2<br />**数値**:<br />-2147220238|残りのサービス単位数が無効です|
> |**名前**:<br />InvalidAllotmentsTotal<br />**16 進数**:<br />800404f0<br />**数値**:<br />-2147220240|合計サービス単位数が無効です|
> |**名前**:<br />InvalidAllotmentsUsed<br />**16 進数**:<br />800404f1<br />**数値**:<br />-2147220239|使用済みサービス単位数が無効です|
> |**名前**:<br />InvalidAmountFreeResourceLimit<br />**16 進数**:<br />8004B060<br />**数値**:<br />-2147176352|リソースの種類 {0} には、{1}の無料の値が存在しません。|
> |**名前**:<br />InvalidAmountProvided<br />**16 進数**:<br />8004B02D<br />**数値**:<br />-2147176403|サービス コンポーネント {0} は、リソースの種類 {2}を提供 {1} することはできません。|
> |**名前**:<br />InvalidAppModuleClientType<br />**16 進数**:<br />80050126<br />**数値**:<br />-2147155674|渡されたクライアントの種類の値が正しくなく、有効範囲にありません。|
> |**名前**:<br />InvalidAppModuleComponent<br />**16 進数**:<br />80050113<br />**数値**:<br />-2147155693|ID {0} は存在しないか、コンポーネントの種類 “{1}” に対して有効ではありません。|
> |**名前**:<br />InvalidAppModuleComponentType<br />**16 進数**:<br />80050112<br />**数値**:<br />-2147155694|アプリは、コンポーネントの種類 “{0}” を参照できません。|
> |**名前**:<br />InvalidAppModuleEventHandlers<br />**16 進数**:<br />8005012F<br />**数値**:<br />-2147155665|アプリに提供されたイベント ハンドラーは無効です。|
> |**名前**:<br />InvalidAppModuleId<br />**16 進数**:<br />80050116<br />**数値**:<br />-2147155690|アプリの ID が無効、またはアプリへのアクセス権がありません。|
> |**名前**:<br />InvalidAppModuleSiteMap<br />**16 進数**:<br />80050110<br />**数値**:<br />-2147155696|適切に構成されていないため、このアプリ モジュール用のカスタマイズされたサイト マップを使用できませんでした。 この問題を解決するには、フル機能のエクスペリエンスに移動し、カスタマイズされたサイト マップを修復して、インポートし直してください。|
> |**名前**:<br />InvalidAppModuleSiteMapXml<br />**16 進数**:<br />80050109<br />**数値**:<br />-2147155703|アプリ モジュールのサイトマップが無効です。|
> |**名前**:<br />InvalidAppModuleUniqueName<br />**16 進数**:<br />8005011E<br />**数値**:<br />-2147155682|一意の名前が最大長の 40 文字を超えたか、または無効な文字が含まれています。 文字、および数値のみを使用できます。|
> |**名前**:<br />InvalidAppModuleUrl<br />**16 進数**:<br />8005011A<br />**数値**:<br />-2147155686|アプリ URL が一意でないか、形式が無効です。|
> |**名前**:<br />InvalidAppointmentInstance<br />**16 進数**:<br />8004E104<br />**数値**:<br />-2147163900|無効な予定エンティティ インスタンスです。|
> |**名前**:<br />InvalidApproveFromDraftArticle<br />**16 進数**:<br />80048dfd<br />**数値**:<br />-2147185155|下書きの状態にある記事を承認しようとしています。 未承認の状態にある記事のみが承認できます。|
> |**名前**:<br />InvalidApproveFromPublishedArticle<br />**16 進数**:<br />80048dfb<br />**数値**:<br />-2147185157|公開済みの状態にある記事を承認しようとしています。 未承認の状態にある記事のみが承認できます。|
> |**名前**:<br />InvalidArgument<br />**16 進数**:<br />80040203<br />**数値**:<br />-2147220989|無効な引数です。|
> |**名前**:<br />InvalidArticleState<br />**16 進数**:<br />800404fb<br />**数値**:<br />-2147220229|記事の状態が未定義です。|
> |**名前**:<br />InvalidArticleStateTransition<br />**16 進数**:<br />800404fc<br />**数値**:<br />-2147220228|記事の現在の状態により、この記事の状態遷移は無効です|
> |**名前**:<br />InvalidArticleTemplateState<br />**16 進数**:<br />800404fd<br />**数値**:<br />-2147220227|記事テンプレートの状態が未定義です|
> |**名前**:<br />InvalidAssemblyProcessorArchitecture<br />**16 進数**:<br />8004417E<br />**数値**:<br />-2147204738|指定されたプラグイン アセンブリは、サポートされていないターゲット プラットフォームによって作成され、読み込むことはできません。|
> |**名前**:<br />InvalidAssemblySourceType<br />**16 進数**:<br />8004417D<br />**数値**:<br />-2147204739|指定されたプラグイン アセンブリ ソースの種類は、隔離されたプラグイン アセンブリに対してサポートされません。|
> |**名前**:<br />InvalidAssigneeId<br />**16 進数**:<br />80040210<br />**数値**:<br />-2147220976|無効な割り当て先 ID です。|
> |**名前**:<br />InvalidAssociatedSavedQuery<br />**16 進数**:<br />800609AE<br />**数値**:<br />-2147087954|選択した保存済みクエリは、Mobile Offline プロファイル項目の関連エンティティに属していません。|
> |**名前**:<br />InvalidAttachmentsFolder<br />**16 進数**:<br />80048490<br />**数値**:<br />-2147187568|圧縮 (.zip) ファイルをアップロードできません。"Attachments" フォルダーに 1 つ以上のサブフォルダーが含まれています。 サブフォルダーを削除し、もう一度やり直してください。|
> |**名前**:<br />InvalidAttribute<br />**16 進数**:<br />8005E009<br />**数値**:<br />-2147098615|属性 {0} はエンティティ {1} で見つかりません。|
> |**名前**:<br />InvalidAttributeDataType<br />**16 進数**:<br />80044815<br />**数値**:<br />-2147203051|属性データの種類: {0} はこのエンティティーに無効です。|
> |**名前**:<br />InvalidAttributeFieldType<br />**16 進数**:<br />80044816<br />**数値**:<br />-2147203050|属性フィールドの種類: {0} は仮想エンティティに無効です。|
> |**名前**:<br />InvalidAttributeFound<br />**16 進数**:<br />8004E303<br />**数値**:<br />-2147163389|ダッシュボード フォーム XML は、属性: {0} を含めることはできません。|
> |**名前**:<br />InvalidAttributeInXaml<br />**16 進数**:<br />80060412<br />**数値**:<br />-2147089390|XAML で属性 - {0} は無効です|
> |**名前**:<br />InvalidAttributeMap<br />**16 進数**:<br />80046203<br />**数値**:<br />-2147196413|InvalidAttributeMap のエラーが発生しました。|
> |**名前**:<br />InvalidAttributeMapping<br />**16 進数**:<br />80048438<br />**数値**:<br />-2147187656|1 つまたは複数の属性マッピングが無効です。|
> |**名前**:<br />InvalidAttributeQuery<br />**16 進数**:<br />80072527<br />**数値**:<br />-2147015385|AttributeQuery が指定されている場合、属性は要求された EntityMetadata プロパティの一部である必要があります。 要求されたエンティティ プロパティの一覧に property = {0} が必要です。|
> |**名前**:<br />InvalidAuth<br />**16 進数**:<br />80048516<br />**数値**:<br />-2147187434|組織の認証は現在の探索サービス ロールと一致しません。|
> |**名前**:<br />InvalidAuthTicket<br />**16 進数**:<br />8004A100<br />**数値**:<br />-2147180288|認証のために指定されたチケットが検証をパスしませんでした|
> |**名前**:<br />InvalidBaseAttributeError<br />**16 進数**:<br />80044242<br />**数値**:<br />-2147204542|ベース属性が無効です。|
> |**名前**:<br />InvalidBaseUnit<br />**16 進数**:<br />80043b0b<br />**数値**:<br />-2147206389|基本出荷単位はスケジュールに属していません。|
> |**名前**:<br />InvalidBehavior<br />**16 進数**:<br />800608A1<br />**数値**:<br />-2147088223|この属性の [動作] の値は変更できません。|
> |**名前**:<br />InvalidBehaviorSelection<br />**16 進数**:<br />800608A0<br />**数値**:<br />-2147088224|この [日付と時間] フィールドの動作は、"日付のみ" にしか変更できません。|
> |**名前**:<br />InvalidBrowserToConfigureOrganization<br />**16 進数**:<br />8004D255<br />**数値**:<br />-2147167659|組織の構成と互換性のないブラウザー|
> |**名前**:<br />InvalidBusinessProcess<br />**16 進数**:<br />80060389<br />**数値**:<br />-2147089527|無効なビジネス プロセスです。|
> |**名前**:<br />InvalidCaller<br />**16 進数**:<br />80040257<br />**数値**:<br />-2147220905|最初に呼び出し元を設定せずに ExecutionContext をシステム ユーザーに切り替えることはできません。|
> |**名前**:<br />InvalidCascadeLinkType<br />**16 進数**:<br />80048204<br />**数値**:<br />-2147188220|カスケード リンクの種類はカスケード操作に対して無効です。|
> |**名前**:<br />InvalidCategory<br />**16 進数**:<br />8004E009<br />**数値**:<br />-2147164151|カテゴリが無効です。 カテゴリ内のすべてのメジャーは、同じ主グループ化がない、または集計データと非集計データを混在しているかのどちらかです。|
> |**名前**:<br />InvalidCertificate<br />**16 進数**:<br />8005E23A<br />**数値**:<br />-2147098054|指定された証明書は無効です。|
> |**名前**:<br />InvalidChangeProcess<br />**16 進数**:<br />80092002<br />**数値**:<br />-2146885630|無効なプロセス状態リクエストの変更です。 現在のプロセス状態は {0} で、{1} に移行できません。|
> |**名前**:<br />InvalidChannelForCampaignActivityPropagate<br />**16 進数**:<br />80040310<br />**数値**:<br />-2147220720|指定チャネルの種類のキャンペーン活動に対する活動を配布することはできません。|
> |**名前**:<br />InvalidChannelOrigin<br />**16 進数**:<br />80060602<br />**数値**:<br />-2147088894|同じチャネルの権利チャネルの期間は、既に存在します。 異なるチャネルを指定して、やり直してください。|
> |**名前**:<br />InvalidCharactersInField<br />**16 進数**:<br />80040278<br />**数値**:<br />-2147220872|フィールド '{0}' には 1 つ以上の無効な文字が含まれています。|
> |**名前**:<br />InvalidClassIdInReferencePanelSection<br />**16 進数**:<br />80061503<br />**数値**:<br />-2147085053|参照パネル セクションには、サブグリッド、簡易表示フォーム、サポート情報検索、i-frame および HTML Web リソースの各コントロールのみを設定できます。 無効なクラス ID {0}のコントロールが見つかりました。|
> |**名前**:<br />InvalidCollectionName<br />**16 進数**:<br />8006088E<br />**数値**:<br />-2147088242|コレクション名のエンティティは、既に存在します。 一意の名前を指定してください。|
> |**名前**:<br />InvalidColumnMapping<br />**16 進数**:<br />80040377<br />**数値**:<br />-2147220617|ColumnMapping が無効です。 ターゲット属性が存在することを確認します。|
> |**名前**:<br />InvalidColumnNumber<br />**16 進数**:<br />80040336<br />**数値**:<br />-2147220682|データ マップで指定された列番号が存在しません。|
> |**名前**:<br />InvalidCommand<br />**16 進数**:<br />8005E100<br />**数値**:<br />-2147098368|無効なコマンドです。|
> |**名前**:<br />InvalidComplexControlId<br />**16 進数**:<br />8005E103<br />**数値**:<br />-2147098365|複合コントロール ID が無効です。|
> |**名前**:<br />InvalidConnectionString<br />**16 進数**:<br />8004023f<br />**数値**:<br />-2147220929|接続文字列は見つからないか、または無効です。|
> |**名前**:<br />InvalidContractDetailId<br />**16 進数**:<br />800404f6<br />**数値**:<br />-2147220234|契約詳細 ID が無効です|
> |**名前**:<br />InvalidControlClass<br />**16 進数**:<br />8004E307<br />**数値**:<br />-2147163385|ダッシュボード フォーム XML は、クラス ID を持つコントロール要素を含めることはできません: {0}。|
> |**名前**:<br />InvalidConversionRule<br />**16 進数**:<br />800608F6<br />**数値**:<br />-2147088138|指定された ConversionRule {0} は無効です。 有効な ConversionRule を指定してください。|
> |**名前**:<br />InvalidCreateOnProtectedComponent<br />**16 進数**:<br />8004F011<br />**数値**:<br />-2147160047|{0} {1} を作成できません。 {0} が管理されている場合、作成を実行することはできません。|
> |**名前**:<br />InvalidCredentialTypeForNonExchangeIncomingConnection<br />**16 進数**:<br />8005E214<br />**数値**:<br />-2147098092|POP3 電子メール サーバーの種類には、ユーザーまたはキューにより指定された資格情報を使用する場合のみ接続できます。|
> |**名前**:<br />InvalidCrmDateTime<br />**16 進数**:<br />8004E103<br />**数値**:<br />-2147163901|無効な CrmDateTime です。|
> |**名前**:<br />InvalidCrossEntityOperation<br />**16 進数**:<br />80092004<br />**数値**:<br />-2146885628|複数のエンティティにまたがるステージ移行が無効です。 対象エンティティを指定する必要があります。|
> |**名前**:<br />InvalidCrossEntityTargetOperation<br />**16 進数**:<br />80092005<br />**数値**:<br />-2146885627|複数のエンティティにまたがるステージ移行が無効です。 指定された対象は一致している必要があります {0}。|
> |**名前**:<br />InvalidCurrency<br />**16 進数**:<br />80048cfc<br />**数値**:<br />-2147185412|通貨が無効です。|
> |**名前**:<br />InvalidCustomActivityType<br />**16 進数**:<br />8004F125<br />**数値**:<br />-2147159771|活動として定義されているカスタム エンティティは、通信活動タイプである必要があります。|
> |**名前**:<br />InvalidCustomDataDownloadFilters<br />**16 進数**:<br />80060996<br />**数値**:<br />-2147087978|[レコード配布条件] が [他のデータ フィルター] に設定されていないため、カスタム ダウンロード フィルターを設定できません。|
> |**名前**:<br />InvalidCustomer<br />**16 進数**:<br />8004022d<br />**数値**:<br />-2147220947|顧客が無効です。|
> |**名前**:<br />InvalidCustomReportingWizardXml<br />**16 進数**:<br />80040491<br />**数値**:<br />-2147220335|無効なウィザード xml|
> |**名前**:<br />InvalidDataDescription<br />**16 進数**:<br />8004E000<br />**数値**:<br />-2147164160|ビジュアル化のデータ記述が無効です。|
> |**名前**:<br />InvalidDataDownloadFilterBusinessUnit<br />**16 進数**:<br />8005F222<br />**数値**:<br />-2147093982|事業主が所有するエンティティには、次のデータ ダウンロード フィルターのみを使用できます: すべてのレコードまたはダウンロード関連データのみです。|
> |**名前**:<br />InvalidDataDownloadFilterOrganization<br />**16 進数**:<br />8005F223<br />**数値**:<br />-2147093981|組織が所有するエンティティには、次のデータ ダウンロード フィルターのみを使用できます: すべてのレコードまたはダウンロード関連データのみです。|
> |**名前**:<br />InvalidDataFiltersForBUOwnedEntities<br />**16 進数**:<br />80060994<br />**数値**:<br />-2147087980|部署が所有するエンティティに対して、[自分が所有するレコード] や [チームが所有するレコード] を設定することはできません。|
> |**名前**:<br />InvalidDataFiltersForOrgOwnedEntities<br />**16 進数**:<br />80060995<br />**数値**:<br />-2147087979|組織が所有するエンティティに対して、[他のデータ フィルター] を設定することはできません。|
> |**名前**:<br />InvalidDataFiltersForUnownedEntities<br />**16 進数**:<br />80060993<br />**数値**:<br />-2147087981|所有者のないエンティティに対して、[すべてのレコード フィルター] や [他のデータ フィルター] を設定することはできません。|
> |**名前**:<br />InvalidDataFormat<br />**16 進数**:<br />80040356<br />**数値**:<br />-2147220650|ソース データが指定された形式と違います|
> |**名前**:<br />InvalidDataSourceEndPoint<br />**16 進数**:<br />80044826<br />**数値**:<br />-2147203034|無効な URI: クエリ文字列のない完全修飾の URI を指定する必要があります。|
> |**名前**:<br />InvalidDataXml<br />**16 進数**:<br />8005E101<br />**数値**:<br />-2147098367|無効な xml データです。|
> |**名前**:<br />InvalidDateAttribute<br />**16 進数**:<br />80044805<br />**数値**:<br />-2147203067|指定されている日付属性は、ソース エンティティの属性ではありません。|
> |**名前**:<br />InvalidDateTime<br />**16 進数**:<br />80040239<br />**数値**:<br />-2147220935|日付/時刻の形式が無効か、値がサポートされている範囲を超えています。|
> |**名前**:<br />InvalidDateTimeFormat<br />**16 進数**:<br />800608A2<br />**数値**:<br />-2147088222|動作が "日付のみ" である場合、この属性の書式値を "日付と時間" に変更することはできません。|
> |**名前**:<br />InvalidDaysInFebruary<br />**16 進数**:<br />8004E124<br />**数値**:<br />-2147163868|パターン開始日がうるう年である場合にのみ、2 月 29 日が発生します。|
> |**名前**:<br />InvalidDeactivateFormType<br />**16 進数**:<br />8004F660<br />**数値**:<br />-2147158432|{0} フォームを非アクティブ化することはできません。 メイン フォームのみ非アクティブにすることができます。|
> |**名前**:<br />InvalidDeleteModification<br />**16 進数**:<br />80048203<br />**数値**:<br />-2147188221|システム関連付けの削除の伝播動作は、変更することはできません。|
> |**名前**:<br />InvalidDeleteOnProtectedComponent<br />**16 進数**:<br />8004F013<br />**数値**:<br />-2147160045|{0} {1} を削除できません。 {0} が管理されている場合、削除を実行することはできません。|
> |**名前**:<br />InvalidDeleteProcess<br />**16 進数**:<br />80060691<br />**数値**:<br />-2147088751|システムによって生成されたプロセスであるため、このプロセスを削除することはできません。|
> |**名前**:<br />InvalidDependency<br />**16 進数**:<br />8004F036<br />**数値**:<br />-2147160010|{2} コンポーネント {1} (Id={0}) は存在しません。  依存関係として {3} (ID={4}) に関連付けようとして失敗しました。 検索型の依存関係 = {5} がありません。|
> |**名前**:<br />InvalidDependencyComponent<br />**16 進数**:<br />8004F040<br />**数値**:<br />-2147160000|{2} で定義された必要なコンポーネント {1} (ID={0}) はシステムで見つかりませんでした。|
> |**名前**:<br />InvalidDependencyEntity<br />**16 進数**:<br />8004F041<br />**数値**:<br />-2147159999|{2} で定義された必要なコンポーネント {1} (名前 ={0}) はシステムで見つかりませんでした。|
> |**名前**:<br />InvalidDependencyFetchXml<br />**16 進数**:<br />8004F037<br />**数値**:<br />-2147160009|FetchXML ({2}) は無効です。  {1} (ID={0}) の依存関係の計算中の失敗。|
> |**名前**:<br />InvalidDeviceToConfigureOrganization<br />**16 進数**:<br />8004D254<br />**数値**:<br />-2147167660|モバイル デバイスは構成された組織には使用できません|
> |**名前**:<br />InvalidDisplayName<br />**16 進数**:<br />8004700c<br />**数値**:<br />-2147192820|指定した表示名は無効です|
> |**名前**:<br />InvalidDocumentTemplate<br />**16 進数**:<br />800608CB<br />**数値**:<br />-2147088181|ドキュメント テンプレートが無効です。|
> |**名前**:<br />InvalidDomainName<br />**16 進数**:<br />80048015<br />**数値**:<br />-2147188715|このユーザーのドメイン ログオンが無効です。 別のドメイン ログオンを選択して、やり直してください。|
> |**名前**:<br />InvalidDundasPresentationDescription<br />**16 進数**:<br />8004E016<br />**数値**:<br />-2147164138|プレゼンテーションの説明は dundas グラフで無効です。|
> |**名前**:<br />InvalidElementFound<br />**16 進数**:<br />8004E300<br />**数値**:<br />-2147163392|ダッシュボード フォーム XML は、要素: {0} を含めることはできません。|
> |**名前**:<br />InvalidEmail<br />**16 進数**:<br />8004B016<br />**数値**:<br />-2147176426|テンプレートから生成された電子メールが無効です|
> |**名前**:<br />InvalidEmailAddressFormat<br />**16 進数**:<br />80044192<br />**数値**:<br />-2147204718|無効な電子メール アドレス。 詳細については、システム管理者に問い合わせてください。|
> |**名前**:<br />InvalidEmailAddressInMailbox<br />**16 進数**:<br />8005E221<br />**数値**:<br />-2147098079|メールボックスの電子メール アドレスが正しくありません。 メールを処理するために正しい電子メール アドレスを入力してください。|
> |**名前**:<br />InvalidEmailServerLocation<br />**16 進数**:<br />8005E218<br />**数値**:<br />-2147098088|サーバーの場所をが存在しないか、または無効です。 サーバーの場所を修正してください。|
> |**名前**:<br />InvalidEmailTemplate<br />**16 進数**:<br />80040313<br />**数値**:<br />-2147220717|有効なテンプレート ID を指定する必要があります|
> |**名前**:<br />InvalidEntitlementActivate<br />**16 進数**:<br />80060606<br />**数値**:<br />-2147088890|"期限切れ"、"待機中"、または "キャンセル済み" である権利をアクティブ化することはできません。|
> |**名前**:<br />InvalidEntitlementAssociationToCase<br />**16 進数**:<br />80060609<br />**数値**:<br />-2147088887|この権利には利用可能な期間が存在しないため、サポート案件は作成できません。|
> |**名前**:<br />InvalidEntitlementCancel<br />**16 進数**:<br />80060607<br />**数値**:<br />-2147088889|状態が "下書き" または "期限切れ" である権利のキャンセルはできません。|
> |**名前**:<br />InvalidEntitlementChannelTerms<br />**16 進数**:<br />80060605<br />**数値**:<br />-2147088891|権利チャネルで始まる特定のサポート案件の合計時間は、対応する権利の合計時間より長くすることはできません。|
> |**名前**:<br />InvalidEntitlementContacts<br />**16 進数**:<br />80044207<br />**数値**:<br />-2147204601|指定された取引先担当者は、選択された顧客に関連付けられていません。|
> |**名前**:<br />InvalidEntitlementDeactivate<br />**16 進数**:<br />80060608<br />**数値**:<br />-2147088888|"アクティブ" または "待機中" である権利のみ、非アクティブ化できます|
> |**名前**:<br />InvalidEntitlementExpire<br />**16 進数**:<br />80060618<br />**数値**:<br />-2147088872|権利を "期限切れ" 状態に設定することはできません。 アクティブな権利は終了日が過ぎると、自動的に期限切れになります。|
> |**名前**:<br />InvalidEntitlementForSelectedCustomerOrProduct<br />**16 進数**:<br />8004F866<br />**数値**:<br />-2147157914|指定された顧客、取引先担当者、または製品に属するアクティブな権利を選択してから、やり直してください。|
> |**名前**:<br />InvalidEntitlementRenew<br />**16 進数**:<br />80060610<br />**数値**:<br />-2147088880|更新できるのは、期限切れまたはキャンセル済みの権利のみです。|
> |**名前**:<br />InvalidEntitlementStateAssociateToCase<br />**16 進数**:<br />80060611<br />**数値**:<br />-2147088879|サポート案件は、アクティブな権利にのみ関連付けることができます。|
> |**名前**:<br />InvalidEntitlementTotalTerms<br />**16 進数**:<br />800443FF<br />**数値**:<br />-2147204097|権利の合計期間は、対応するどの EntitlementChannels の合計期間よりも少なくできません。|
> |**名前**:<br />InvalidEntity<br />**16 進数**:<br />8005E00C<br />**数値**:<br />-2147098612|エンティティ {0} が見つかりません。|
> |**名前**:<br />InvalidEntityClassException<br />**16 進数**:<br />80040249<br />**数値**:<br />-2147220919|無効なエンティティ クラスです。|
> |**名前**:<br />InvalidEntityForDateAttribute<br />**16 進数**:<br />80044812<br />**数値**:<br />-2147203054|日付属性のエンティティは、ソース エンティティまたは親エンティティです。|
> |**名前**:<br />InvalidEntityForLinkedAttribute<br />**16 進数**:<br />8004F0FD<br />**数値**:<br />-2147159811|リンクされた属性に有効なエンティティではありません。|
> |**名前**:<br />InvalidEntityForRollup<br />**16 進数**:<br />80044813<br />**数値**:<br />-2147203053|エンティティ {0} は、ロールアップに対して無効なエンティティです。|
> |**名前**:<br />InvalidEntityKeyOperation<br />**16 進数**:<br />8006088F<br />**数値**:<br />-2147088241|無効な EntityKey 操作が実行されました : {0}|
> |**名前**:<br />InvalidEntityLogicalName<br />**16 進数**:<br />80072493<br />**数値**:<br />-2147015533|エンティティ名 '{0}' は有効な論理名ではありません。|
> |**名前**:<br />InvalidEntityName<br />**16 進数**:<br />80048416<br />**数値**:<br />-2147187690|レコードの種類は、基本のレコードの種類に対応しませんが、重複データ検出ルールのレコードの種類に対応しています。|
> |**名前**:<br />InvalidEntitySetName<br />**16 進数**:<br />8006089B<br />**数値**:<br />-2147088229|特定のエンティティ セット名 {0} のエンティティは既に存在します。 一意の名前を指定してください。|
> |**名前**:<br />InvalidEntitySpecified<br />**16 進数**:<br />800609B1<br />**数値**:<br />-2147087951|テンプレートでは、エンティティは指定されません。|
> |**名前**:<br />InvalidExchangeRate<br />**16 進数**:<br />80048cfd<br />**数値**:<br />-2147185411|為替レートは無効です。|
> |**名前**:<br />InvalidExportProcessFlowNotActivated<br />**16 進数**:<br />80060376<br />**数値**:<br />-2147089546|ビジネス プロセス “{0}” をエクスポートできませんでした。対応するビジネス プロセス エンティティ “{1}” がソリューションに含まれていません。 これがドラフト状態で新しく作成されたビジネス プロセスである場合は、一度アクティブ化してビジネス プロセス エンティティを生成し、それをソリューションに含めます。 詳細については、「http://support.microsoft.com/kb/4337537」を参照してください。|
> |**名前**:<br />InvalidExternalCollectionName<br />**16 進数**:<br />80046BA7<br />**数値**:<br />-2147193945|指定した外部コレクション名が無効です。|
> |**名前**:<br />InvalidExternalName<br />**16 進数**:<br />80046BC0<br />**数値**:<br />-2147193920|指定した外部名が無効です。|
> |**名前**:<br />InvalidExternalPartyConfiguration<br />**16 進数**:<br />8006110F<br />**数値**:<br />-2147086065|複数の外部パーティ アイテムが要求パラメーターに対して存在します。|
> |**名前**:<br />InvalidExternalPartyOperation<br />**16 進数**:<br />80061111<br />**数値**:<br />-2147086063|外部パーティは許可されていません。|
> |**名前**:<br />InvalidExternalPartyParent<br />**16 進数**:<br />80061110<br />**数値**:<br />-2147086064|外部パーティには、有効な親属性があります。|
> |**名前**:<br />InvalidFeatureType<br />**16 進数**:<br />80044272<br />**数値**:<br />-2147204494|機能の種類が無効です。|
> |**名前**:<br />InvalidFetchCollection<br />**16 進数**:<br />8004E019<br />**数値**:<br />-2147164135|ビジュアル化のフェッチ コレクションが無効です。|
> |**名前**:<br />InvalidFetchXml<br />**16 進数**:<br />80040303<br />**数値**:<br />-2147220733|形式が正しくない FetchXml です。|
> |**名前**:<br />InvalidFileBadCharacters<br />**16 進数**:<br />80040396<br />**数値**:<br />-2147220586|無効な文字が含まれているため、ファイルをアップロードできませんでした|
> |**名前**:<br />InvalidFileType<br />**16 進数**:<br />800608CC<br />**数値**:<br />-2147088180|ファイルの種類が無効です。|
> |**名前**:<br />InvalidFilterCriteriaForVisualization<br />**16 進数**:<br />8004E01E<br />**数値**:<br />-2147164130|指定されたフィルター条件でビジュアル化できませんでした。|
> |**名前**:<br />InvalidFiscalPeriod<br />**16 進数**:<br />80044814<br />**数値**:<br />-2147203052|会計期間 {0} は、組織の会計設定により、会計期間の許容範囲内に入りません。|
> |**名前**:<br />InvalidFlowProcessClientData<br />**16 進数**:<br />80060468<br />**数値**:<br />-2147089304|フロー クライアント データの形式が無効です。 詳細: "{0}"。|
> |**名前**:<br />InvalidFormatForControl<br />**16 進数**:<br />80060875<br />**数値**:<br />-2147088267|コントロールに無効な有効桁数のパラメーターが指定されています {0}。 必要な値が含まれていません|
> |**名前**:<br />InvalidFormatForDataDelimiter<br />**16 進数**:<br />80040355<br />**数値**:<br />-2147220651|データ区切り文字が一致しません: 1 つのデータ区切り文字しか見つかりません。|
> |**名前**:<br />InvalidFormatForUpdateMode<br />**16 進数**:<br />8004F601<br />**数値**:<br />-2147158527|アップロードしたファイルが無効で、レコードの更新に使用できません。|
> |**名前**:<br />InvalidFormatParameters<br />**16 進数**:<br />80047101<br />**数値**:<br />-2147192575|入力文字列に渡されたフォーマット パラメーター数が正しくありません|
> |**名前**:<br />InvalidFormType<br />**16 進数**:<br />8004E306<br />**数値**:<br />-2147163386|フォームの種類はフォーム XML で {0} に設定する必要があります。|
> |**名前**:<br />InvalidFormTypeCalledThroughSdk<br />**16 進数**:<br />80060874<br />**数値**:<br />-2147088268|"作成コマンド呼び出しで無効な Formtype が使用されています|
> |**名前**:<br />InvalidForOfficeGraph<br />**16 進数**:<br />80044231<br />**数値**:<br />-2147204559|1 つまたは両方のエンティティが officegraph に対応していないため、officegraph に使用できません。|
> |**名前**:<br />InvalidGoalAttribute<br />**16 進数**:<br />8004480b<br />**数値**:<br />-2147203061|目標属性が指定された指標の種類に対応しません。|
> |**名前**:<br />InvalidGoalManager<br />**16 進数**:<br />8004F684<br />**数値**:<br />-2147158396|目標のマネージャーは、ユーザーのみであるか、またはチームではありません。|
> |**名前**:<br />InvalidGranularityValue<br />**16 進数**:<br />8004B038<br />**数値**:<br />-2147176392|[細分性] 列の値が正しくありません。 ルール部は等号 (=) で区切られた名前と値のペアである必要があります。 例: FREQ=Minutes;INTERVAL=15|
> |**名前**:<br />InvalidGroupByAlias<br />**16 進数**:<br />8004E00F<br />**数値**:<br />-2147164145|データの説明が無効です。 エイリアスと同じグループは異なる属性として使用することはできません。|
> |**名前**:<br />InvalidGroupByColumn<br />**16 進数**:<br />8004E01D<br />**数値**:<br />-2147164131|属性で許可されていないグループ化。|
> |**名前**:<br />InvalidGuid<br />**16 進数**:<br />80040363<br />**数値**:<br />-2147220637|この行のグローバル一意識別子 (GUID) は無効です|
> |**名前**:<br />InvalidGuidInXaml<br />**16 進数**:<br />80060407<br />**数値**:<br />-2147089401|Xaml での Guid - {0} は無効です|
> |**名前**:<br />InvalidHeaderColumn<br />**16 進数**:<br />80040344<br />**数値**:<br />-2147220668|列見出しにデータ区切り文字の無効な組み合わせが含まれています。|
> |**名前**:<br />InvalidHexColorValue<br />**16 進数**:<br />800608D0<br />**数値**:<br />-2147088176|16 進数の値のみ使用できます。|
> |**名前**:<br />InvalidHierarchicalRelationship<br />**16 進数**:<br />8004701F<br />**数値**:<br />-2147192801|この関係は自己参照ではないため、階層化できません。|
> |**名前**:<br />InvalidHierarchicalRelationshipChange<br />**16 進数**:<br />8004701a<br />**数値**:<br />-2147192806|{0} 階層型の関連付けをカスタマイズできないため、このエンティティの階層を変更できません。|
> |**名前**:<br />InvalidImportFileContent<br />**16 進数**:<br />80040374<br />**数値**:<br />-2147220620|インポートされたファイルの内容は有効ではありません。 テキスト ファイルを選択してください。|
> |**名前**:<br />InvalidImportFileData<br />**16 進数**:<br />80040351<br />**数値**:<br />-2147220655|データの形式が指定された形式と違います|
> |**名前**:<br />InvalidImportFileParseData<br />**16 進数**:<br />80040349<br />**数値**:<br />-2147220663|このファイルのフィールド区切り文字とデータ区切り文字が指定されていません。|
> |**名前**:<br />InvalidImportJobId<br />**16 進数**:<br />80044252<br />**数値**:<br />-2147204526|要求された importjob は存在しません。|
> |**名前**:<br />InvalidImportJobTemplateFile<br />**16 進数**:<br />80044251<br />**数値**:<br />-2147204527|ImportJobTemplate.xml ファイルが無効です。|
> |**名前**:<br />InvalidIncomingDeliveryExpectingEmailConnector<br />**16 進数**:<br />8005E224<br />**数値**:<br />-2147098076|受信メールの配信方法は、電子メール コネクタではありません。 メールを受信するには、受信メールの配信方法を [電子メール コネクタ] に設定する必要があります。|
> |**名前**:<br />InvalidInstanceEntityName<br />**16 進数**:<br />8004E10D<br />**数値**:<br />-2147163891|無効なインスタンス エンティティ名です。|
> |**名前**:<br />InvalidInstanceTypeCode<br />**16 進数**:<br />8004E107<br />**数値**:<br />-2147163897|インスタンスの種類のコードが無効です。|
> |**名前**:<br />InvalidInteractiveUserQuota<br />**16 進数**:<br />8004B049<br />**数値**:<br />-2147176375|対話型 / フル ユーザーの最大値に到達しました。|
> |**名前**:<br />InvalidIntersectEntity<br />**16 進数**:<br />80072540<br />**数値**:<br />-2147015360|多対多の関係を定義する交差エンティティとして、既存の非交差エンティティ {0} を使用できません。|
> |**名前**:<br />InvalidInvitationLiveId<br />**16 進数**:<br />8004D20E<br />**数値**:<br />-2147167730|この電子メール アドレスを持つユーザーは見つかりませんでした。 招待状を受け取ったときと同じ電子メール アドレスを使用して Windows Live ID にサインインしてください。  Windows Live ID がない場合は、その電子メール アドレスを使用して 1 つ作成します。|
> |**名前**:<br />InvalidInvitationToken<br />**16 進数**:<br />8004D20D<br />**数値**:<br />-2147167731|招待状トークン {0} は、正しく書式設定されていません。|
> |**名前**:<br />InvalidIsFirstRowHeaderForUseSystemMap<br />**16 進数**:<br />80040364<br />**数値**:<br />-2147220636|ファイルの最初の行にタイトル行が含まれていません。|
> |**名前**:<br />InvalidIsoCurrencyCode<br />**16 進数**:<br />80048cf2<br />**数値**:<br />-2147185422|無効な ISO 通貨コードです。|
> |**名前**:<br />InvalidKeyQuery<br />**16 進数**:<br />80072529<br />**数値**:<br />-2147015383|KeyQuery が指定された場合、キーは要求された EntityMetadata プロパティの一部である必要があります。 要求されたエンティティ プロパティの一覧に property = {0} が必要です。|
> |**名前**:<br />InvalidKit<br />**16 進数**:<br />80043afd<br />**数値**:<br />-2147206403|この製品はセット製品ではありません。|
> |**名前**:<br />InvalidKitProduct<br />**16 進数**:<br />80043afe<br />**数値**:<br />-2147206402|セット製品をそれ自体に追加することはできません。 別の製品またはセット製品を選択してください。|
> |**名前**:<br />InvalidLanguageCode<br />**16 進数**:<br />80044195<br />**数値**:<br />-2147204715|指定した言語コードは、この組織に対して無効です。|
> |**名前**:<br />InvalidLanguageForCreate<br />**16 進数**:<br />80060750<br />**数値**:<br />-2147088560|ローカライズ可能な属性を持つ行は、現在のユーザーのユーザー インターフェイス (UI) 言語が組織の基本言語に設定されている場合に限り、作成することができます。|
> |**名前**:<br />InvalidLanguageForProcessConfiguration<br />**16 進数**:<br />8005E102<br />**数値**:<br />-2147098366|言語がシステム基本言語と一致しないため、[プロセスの構成] のオプションは使用できません。|
> |**名前**:<br />InvalidLanguageForSolution<br />**16 進数**:<br />80047019<br />**数値**:<br />-2147192807|言語がシステム基本言語と一致しないため、[ソリューション] と [発行者] のオプションは使用できません。|
> |**名前**:<br />InvalidLanguageForUpdate<br />**16 進数**:<br />80060751<br />**数値**:<br />-2147088559|ローカライズ可能な属性は、現在のユーザーのユーザー インターフェイス (UI) 言語が組織の基本言語に設定されている場合に限り、文字列プロパティを使用して更新することができます。 SetLocLabels を使用して次の属性のローカライズ可能な値を更新します: [{0}]|
> |**名前**:<br />InvalidLicenseCannotReadMpcFile<br />**16 進数**:<br />8004D245<br />**数値**:<br />-2147167675|無効なライセンスです。 MPCコードはこのパス {0} を使用して MPC.txt ファイルから読み込むことはできません。|
> |**名前**:<br />InvalidLicenseKey<br />**16 進数**:<br />8004D240<br />**数値**:<br />-2147167680|無効なライセンス キーです ({0})。|
> |**名前**:<br />InvalidLicenseMpcCode<br />**16 進数**:<br />8004D246<br />**数値**:<br />-2147167674|無効なライセンスです。 無効な MPC コードです ({0})。|
> |**名前**:<br />InvalidLicensePid<br />**16 進数**:<br />8004D242<br />**数値**:<br />-2147167678|無効なライセンスです。 無効な PID (製品 ID) です ({0})。|
> |**名前**:<br />InvalidLicensePidGenCannotLoad<br />**16 進数**:<br />8004D243<br />**数値**:<br />-2147167677|無効なライセンスです。 PidGen.dll はこのパスから読み込むことができません {0}|
> |**名前**:<br />InvalidLicensePidGenOtherError<br />**16 進数**:<br />8004D244<br />**数値**:<br />-2147167676|無効なライセンスです。 ライセンス キーで PID (製品 ID) を生成できません。 PidGenエラー コード ({0})。|
> |**名前**:<br />InvalidLocaleIdForKnowledgeArticle<br />**16 進数**:<br />80061400<br />**数値**:<br />-2147085312|ロケール ID {0} を持つ言語が、存在しません|
> |**名前**:<br />InvalidLogoImageId<br />**16 進数**:<br />800608D3<br />**数値**:<br />-2147088173|ロゴ画像の Web リソース ID が無効です。|
> |**名前**:<br />InvalidLogoImageWebResourceType<br />**16 進数**:<br />800608D9<br />**数値**:<br />-2147088167|ロゴ画像に対して無効な Web リソースの種類です。|
> |**名前**:<br />InvalidLookupMapNode<br />**16 進数**:<br />80048481<br />**数値**:<br />-2147187583|提供された検索エンティティは、指定されたターゲット属性に対して有効ではありません。|
> |**名前**:<br />InvalidMailbox<br />**16 進数**:<br />8005E217<br />**数値**:<br />-2147098089|無効な mailboxId が渡されました。 mailboxId を確認してください。|
> |**名前**:<br />InvalidManagedPropertyException<br />**16 進数**:<br />8004F030<br />**数値**:<br />-2147160016|管理プロパティ {0} には作成するための十分な情報が含まれていません。  (アセンブリ、クラス)、または (エンティティ、属性) の入力、またはユーザー定義のために管理プロパティを設定してください。|
> |**名前**:<br />InvalidManifestFilePath<br />**16 進数**:<br />80048533<br />**数値**:<br />-2147187405|指定された場所でマニフェスト ファイルを配置できませんでした|
> |**名前**:<br />InvalidMatchingAttributeError<br />**16 進数**:<br />80044244<br />**数値**:<br />-2147204540|一致する属性が無効です。|
> |**名前**:<br />InvalidMaximumResourceLimit<br />**16 進数**:<br />8004B02B<br />**数値**:<br />-2147176405|リソースの種類 {0} には {1}の上限が存在しません。|
> |**名前**:<br />InvalidMaxLengthForControl <br />**16 進数**:<br />80060879<br />**数値**:<br />-2147088263|コントロール {0} に無効な MaxLength パラメーターが指定されています。MaxLength は {1} ～ {2} の間で設定する必要があります。|
> |**名前**:<br />InvalidMaxValueForControl <br />**16 進数**:<br />8006087B<br />**数値**:<br />-2147088261|コントロール {0} に無効な MaxValue パラメーターが指定されています。MaxValue は {1} ～ {2} の間で設定する必要があります。|
> |**名前**:<br />InvalidMeasureCollection<br />**16 進数**:<br />8004E00A<br />**数値**:<br />-2147164150|メジャー コレクションが無効です。 1 つのメジャー コレクションのすべてのメジャーが、同じグループ group bys を持っているわけではありません。|
> |**名前**:<br />InvalidMetadata<br />**16 進数**:<br />8004023a<br />**数値**:<br />-2147220934|無効なメタデータです。|
> |**名前**:<br />InvalidMetadataSqlOperation<br />**16 進数**:<br />80072343<br />**数値**:<br />-2147015869|現在のメタデータ操作で SQL 例外がスローされました。 詳細については例外を確認してください。|
> |**名前**:<br />InvalidMigrationFileContent<br />**16 進数**:<br />8005F033<br />**数値**:<br />-2147094477|インポートされたファイルの内容は有効ではありません。 テキスト ファイルを選択してください。|
> |**名前**:<br />InvalidMinAndMaxValueForControl <br />**16 進数**:<br />8006087C<br />**数値**:<br />-2147088260|コントロール {0} に無効な MinValue および MaxValue パラメーターが指定されています。MinValue は MaxValue より小さく設定する必要があります。|
> |**名前**:<br />InvalidMinimumResourceLimit<br />**16 進数**:<br />8004B02A<br />**数値**:<br />-2147176406|リソースの種類 {0} には {1}の下限が存在しません。|
> |**名前**:<br />InvalidMinValueForControl <br />**16 進数**:<br />8006087A<br />**数値**:<br />-2147088262|コントロール {0} に無効な MinValue パラメーターが指定されています。MinValue は {1} ～ {2} の間で設定する必要があります。|
> |**名前**:<br />InvalidMobileOfflineFiltersFetchXml<br />**16 進数**:<br />80071113<br />**数値**:<br />-2147020525|XML 形式が一致しません。 XML の正確さを確認します。|
> |**名前**:<br />InvalidMultipleMapping<br />**16 進数**:<br />80048498<br />**数値**:<br />-2147187560|ソース フィールドが、種類が検索/候補リストの 1 つ以上の Dynamics 365 フィールドにマップされています。|
> |**名前**:<br />InvalidMultipleSiteMapReferenceSingleAppModule<br />**16 進数**:<br />80050111<br />**数値**:<br />-2147155695|アプリは複数のサイト マップを持つことができません。|
> |**名前**:<br />InvalidNamePrefix<br />**16 進数**:<br />80044366<br />**数値**:<br />-2147204250|種類 {2} のスキーマ名 {0} が無効か、存在しません。カスタム属性、エンティティ、entitykey、オプション セット、関連付けの名前は、有効なカスタマイズ接頭辞で始まる必要があります。ソリューション コンポーネントの接頭辞は、ソリューションの発行元に対して指定される接頭辞と一致する必要があります。|
> |**名前**:<br />InvalidNetPrice<br />**16 進数**:<br />800404f3<br />**数値**:<br />-2147220237|正価が無効です|
> |**名前**:<br />InvalidNonInteractiveUserQuota<br />**16 進数**:<br />8004B050<br />**数値**:<br />-2147176368|非対話型ユーザーの最大値に到達しました/|
> |**名前**:<br />InvalidNumberGroupFormat<br />**16 進数**:<br />80043700<br />**数値**:<br />-2147207424|NumberGroupFormat に無効な入力文字列があります。 入力文字列には、整数の配列を含める必要があります。 値の配列での各要素は 0 になる最後の要素を除いて、1 ～ 9 であるべきです。|
> |**名前**:<br />InvalidNumberOfCardFormSections<br />**16 進数**:<br />80061505<br />**数値**:<br />-2147085051|カード フォームのセクション数は 4 つにする必要があります。 {0}が見つかりました。|
> |**名前**:<br />InvalidNumberOfPartitions<br />**16 進数**:<br />8004E200<br />**数値**:<br />-2147163648|現在使用中のパーティションに含まれている監査データ、または今後監査データを保存するために作成されたパーティションを削除することはできません。|
> |**名前**:<br />InvalidNumberOfReferencePanelSections<br />**16 進数**:<br />80061504<br />**数値**:<br />-2147085052|MainInteractionCentric フォームに設定できる参照パネル セクションは 1 つだけです。 {0}が見つかりました。|
> |**名前**:<br />InvalidNumberOfSectionsInTab<br />**16 進数**:<br />80060872<br />**数値**:<br />-2147088270|ダイアログのフォーム XML に複数のセクションを含めることはできません。|
> |**名前**:<br />InvalidNumberOfTabsInDialog<br />**16 進数**:<br />80060871<br />**数値**:<br />-2147088271|ダイアログのフォーム XML に複数のタブを含めることはできません。|
> |**名前**:<br />InvalidOAuthToken<br />**16 進数**:<br />80041d50<br />**数値**:<br />-2147214000|OAuth トークンは無効です。|
> |**名前**:<br />InvalidObjectTypes<br />**16 進数**:<br />8004021f<br />**数値**:<br />-2147220961|オブジェクトの種類が無効です。|
> |**名前**:<br />InvalidOccurrenceNumber<br />**16 進数**:<br />8004E125<br />**数値**:<br />-2147163867|系列の有効な終了日は、今日以前にすることはできません。 有効な回数を選択してください。|
> |**名前**:<br />InvalidOfflineOperation<br />**16 進数**:<br />8004410e<br />**数値**:<br />-2147204850|オフラインの場合は、操作が無効です。|
> |**名前**:<br />InvalidOneToManyRelationship<br />**16 進数**:<br />80072500<br />**数値**:<br />-2147015424|EntityRelationshipId '{0}' との OneToMany エンティティの関係に Null の ReferencingEntityRole があります|
> |**名前**:<br />InvalidOneToManyRelationshipForRelatedEntitiesQuery<br />**16 進数**:<br />8004430F<br />**数値**:<br />-2147204337|無効な OneToManyRelationship は RelatedEntitiesQuery に対して指定されました。 参照先エンティティ {0} は主エンティティ {1} と同じでなければなりません|
> |**名前**:<br />InvalidOperandOnLeftHandSide<br />**16 進数**:<br />80072501<br />**数値**:<br />-2147015423|'{0}' 演算子の左側はエンティティのプロパティである必要があります。|
> |**名前**:<br />InvalidOperation<br />**16 進数**:<br />8004023b<br />**数値**:<br />-2147220933|無効な操作が実行されました。|
> |**名前**:<br />InvalidOperationForClosedOrCancelledCampaignActivity<br />**16 進数**:<br />80040314<br />**数値**:<br />-2147220716|クローズした (取り消された) campaignactivity には項目を追加できません。|
> |**名前**:<br />InvalidOperationForDynamicList<br />**16 進数**:<br />8004F701<br />**数値**:<br />-2147158271|この操作は、動的なマーケティング リストに対しては使用できません。|
> |**名前**:<br />InvalidOperationWhenListIsNotActive<br />**16 進数**:<br />8004033a<br />**数値**:<br />-2147220678|リストがアクティブではありません。 この操作を実行できません。|
> |**名前**:<br />InvalidOperationWhenListLocked<br />**16 進数**:<br />80040302<br />**数値**:<br />-2147220734|リストはロックされています。 この操作を実行できません。|
> |**名前**:<br />InvalidOperationWhenPartyIsNotActive<br />**16 進数**:<br />8004033b<br />**数値**:<br />-2147220677|パーティがアクティブではありません。 この操作を実行できません。|
> |**名前**:<br />InvalidOperatorCode<br />**16 進数**:<br />80048415<br />**数値**:<br />-2147187691|演算子が無効であるか、またはサポートされていません。|
> |**名前**:<br />InvalidOperatorCodeError<br />**16 進数**:<br />80044253<br />**数値**:<br />-2147204525|演算子コードが無効です。|
> |**名前**:<br />InvalidOptionSetIdForControl<br />**16 進数**:<br />80060876<br />**数値**:<br />-2147088266|コントロール {0} に無効な OptionSetId が指定されています。OptionSetId は空でないグリッドである必要があります。|
> |**名前**:<br />InvalidOptionSetNameChange<br />**16 進数**:<br />80048409<br />**数値**:<br />-2147187703|OptionSet 名で指定された値 ({2}) が別の既存の OptionSet (id: {3}) によって使用されているため、OptionSet 名 {0}、Id: {1} を更新できません。|
> |**名前**:<br />InvalidOptionSetOperation<br />**16 進数**:<br />80048403<br />**数値**:<br />-2147187709|無効なオプション セット|
> |**名前**:<br />InvalidOptionSetSchemaName<br />**16 進数**:<br />80044345<br />**数値**:<br />-2147204283|指定された名前の OptionSet は既に存在しています。 一意の名前を指定してください。|
> |**名前**:<br />InvalidOrEmptyRelationshipId<br />**16 進数**:<br />80071122<br />**数値**:<br />-2147020510|Mobile プロファイル項目の関連付けの RelationshipId が無効であるか、または空です。|
> |**名前**:<br />InvalidOrganizationFriendlyName<br />**16 進数**:<br />8004D252<br />**数値**:<br />-2147167662|組織のフレンドリ名が無効です ({0})。 理由: ({1})|
> |**名前**:<br />InvalidOrganizationId<br />**16 進数**:<br />80044248<br />**数値**:<br />-2147204536|翻訳ファイル内の組織 ID は、現在の組織 ID と一致しません。|
> |**名前**:<br />InvalidOrganizationSettings<br />**16 進数**:<br />8006110D<br />**数値**:<br />-2147086067|組織の設定は外部パーティに対して正しく構成されていません。|
> |**名前**:<br />InvalidOrganizationUniqueName<br />**16 進数**:<br />8004D251<br />**数値**:<br />-2147167663|組織の一意の名前が無効です ({0})。 理由: ({1})|
> |**名前**:<br />InvalidOrgDBOrgSetting<br />**16 進数**:<br />80048514<br />**数値**:<br />-2147187436|無効な組織の設定が渡されました。 データ型を確認し、適切な値に渡してください。|
> |**名前**:<br />InvalidOrgOwnedCascadeLinkType<br />**16 進数**:<br />80044156<br />**数値**:<br />-2147204778|ユーザー所有のカスケードは、組織が所有するエンティティ関係に対して有効なカスケード リンクの種類ではありません。|
> |**名前**:<br />InvalidOtherDataFilterOptions<br />**16 進数**:<br />8006098D<br />**数値**:<br />-2147087987|[他のデータ フィルター] の [自分のレコードをダウンロードします]、[自分のチームのレコードをダウンロードします]、または [自分の部署のレコードをダウンロードします] からオプションを 1 つ以上選択してください|
> |**名前**:<br />InvalidOutgoingDeliveryExpectingEmailConnector<br />**16 進数**:<br />8005E226<br />**数値**:<br />-2147098074|送信メールの配信方法は、電子メール コネクタではありません。 メールを送信するには、送信メールの配信方法を [電子メール コネクタ] に設定する必要があります。|
> |**名前**:<br />InvalidOwnerID<br />**16 進数**:<br />80040229<br />**数値**:<br />-2147220951|所有者 ID が無効であるか、見つかりません。|
> |**名前**:<br />InvalidOwnershipTypeMask<br />**16 進数**:<br />8004700d<br />**数値**:<br />-2147192819|指定された所有権の種類マスクはこの操作では無効です|
> |**名前**:<br />InvalidPageResponse<br />**16 進数**:<br />8004E00D<br />**数値**:<br />-2147164147|無効なページ応答が生成されました。|
> |**名前**:<br />InvalidParent<br />**16 進数**:<br />80040205<br />**数値**:<br />-2147220987|上位オブジェクトが無効であるか、見つかりません。|
> |**名前**:<br />InvalidParentId<br />**16 進数**:<br />80040206<br />**数値**:<br />-2147220986|親 ID が無効であるか、見つかりません。|
> |**名前**:<br />InvalidPartnerSolutionCustomizationProvider<br />**16 進数**:<br />8004A109<br />**数値**:<br />-2147180279|無効なパートナー ソリューション カスタマイズ プロバイダーの種類|
> |**名前**:<br />InvalidPartyMapping<br />**16 進数**:<br />80043515<br />**数値**:<br />-2147207915|無効なパーティ マッピングです。|
> |**名前**:<br />InvalidPluginAssemblyContent<br />**16 進数**:<br />8004418b<br />**数値**:<br />-2147204725|プラグイン アセンブリに必要な種類が含まれていないか、アセンブリ コンテンツが更新できません。|
> |**名前**:<br />InvalidPluginAssemblyVersion<br />**16 進数**:<br />8004417B<br />**数値**:<br />-2147204741|プラグイン アセンブリ フルネームは一意である必要があります (バージョンのビルド、およびリビジョン番号は無視します)。|
> |**名前**:<br />InvalidPluginRegistrationConfiguration<br />**16 進数**:<br />80044170<br />**数値**:<br />-2147204752|プラグイン アセンブリの登録構成が無効です。|
> |**名前**:<br />InvalidPluginStrongNameRequired<br />**16 進数**:<br />80081114<br />**数値**:<br />-2146954988|プラグイン アセンブリは厳密な名前で署名されていません。|
> |**名前**:<br />InvalidPluginTypeImplementation<br />**16 進数**:<br />8004418c<br />**数値**:<br />-2147204724|プラグインの種類は、以下のクラスからひとつだけ実行する必要があります: Microsoft.Xrm.Sdk.IPlugin、Microsoft.Crm.Sdk.IPlugin、System.Activities.Activity、System.Workflow.ComponentModel.Activity。|
> |**名前**:<br />InvalidPointer<br />**16 進数**:<br />80040218<br />**数値**:<br />-2147220968|オブジェクトは破棄されます。|
> |**名前**:<br />InvalidPrecisionForControl <br />**16 進数**:<br />8006087D<br />**数値**:<br />-2147088259|コントロール {0} に無効な Precision パラメーターが指定されています。Precision は {1} ～ {2} の間で設定する必要があります。|
> |**名前**:<br />InvalidPresentationDescription<br />**16 進数**:<br />8004E002<br />**数値**:<br />-2147164158|プレゼンテーションの説明が無効です。|
> |**名前**:<br />InvalidPreviewModeOperation<br />**16 進数**:<br />8005f219<br />**数値**:<br />-2147093991|この操作はプレビュー モードでは実行できません。|
> |**名前**:<br />InvalidPriceLevelCurrencyForPricingMethod<br />**16 進数**:<br />80048cf9<br />**数値**:<br />-2147185415|価格表の通貨は、価格設定方法の割合に対する製品の通貨に一致する必要があります。|
> |**名前**:<br />InvalidPricePerUnit<br />**16 進数**:<br />80043b10<br />**数値**:<br />-2147206384|出荷単位ごとの価格が無効です。|
> |**名前**:<br />InvalidPrimaryContactBasedOnAccount<br />**16 進数**:<br />8004F864<br />**数値**:<br />-2147157916|指定された取引先担当者は、顧客として選択された取引先企業に属しません。 選択された取引先企業に属している取引先担当者を指定してから、やり直してください。|
> |**名前**:<br />InvalidPrimaryContactBasedOnContact<br />**16 進数**:<br />8004F865<br />**数値**:<br />-2147157915|指定された取引先担当者は、顧客フィールドで指定された取引先担当者に属しません。 取引先担当者フィールドから値を削除するか、選択された顧客に関連付けられた取引先担当者を選択してから、やり直してください。|
> |**名前**:<br />InvalidPrimaryFieldForActivity<br />**16 進数**:<br />8004F127<br />**数値**:<br />-2147159769|活動として定義されているカスタム エンティティには、情報カテゴリ以外に主属性がありません。|
> |**名前**:<br />InvalidPrimaryFieldType<br />**16 進数**:<br />8004700e<br />**数値**:<br />-2147192818|プライマリ UI 属性は文字列型を使用する必要があります。|
> |**名前**:<br />InvalidPrimaryKey<br />**16 進数**:<br />80040266<br />**数値**:<br />-2147220890|無効な主キーです。|
> |**名前**:<br />InvalidPrincipalId<br />**16 進数**:<br />80048348<br />**数値**:<br />-2147187896|渡された Guid は空です。|
> |**名前**:<br />InvalidPrincipalType<br />**16 進数**:<br />80048346<br />**数値**:<br />-2147187898|無効なプリンシパルの種類が渡されました。|
> |**名前**:<br />InvalidPriv<br />**16 進数**:<br />8004024b<br />**数値**:<br />-2147220917|特権の種類が無効です。|
> |**名前**:<br />InvalidPrivilegeDepth<br />**16 進数**:<br />8004140b<br />**数値**:<br />-2147216373|特権の階層が無効です。|
> |**名前**:<br />InvalidProcessControlAttribute<br />**16 進数**:<br />8005E105<br />**数値**:<br />-2147098363|コントロール プロセス定義には、無効な属性が含まれます。|
> |**名前**:<br />InvalidProcessControlEntity<br />**16 進数**:<br />8005E104<br />**数値**:<br />-2147098364|プロセス コントロール定義には、有効なエンティティまたは無効なエンティティの受注が含まれます。|
> |**名前**:<br />InvalidProcessIdOperation<br />**16 進数**:<br />80092001<br />**数値**:<br />-2146885631|無効な操作です。 プロセス ID を修正することはできません。|
> |**名前**:<br />InvalidProcessStateData<br />**16 進数**:<br />80045049<br />**数値**:<br />-2147200951|ProcessState は特定の ProcessSession インスタンスでは有効ではありません。|
> |**名前**:<br />InvalidProduct<br />**16 進数**:<br />80060623<br />**数値**:<br />-2147088861|製品ファミリを追加できません。|
> |**名前**:<br />InvalidPublisherUniqueName<br />**16 進数**:<br />8004F01C<br />**数値**:<br />-2147160036|発行者の uniquename が必要です。|
> |**名前**:<br />InvalidPublishOnProtectedComponent<br />**16 進数**:<br />8004F014<br />**数値**:<br />-2147160044|{0} {1} を公開できません。 {0} が管理されている場合、公開を実行することはできません。|
> |**名前**:<br />InvalidQuantityDecimalCode<br />**16 進数**:<br />80043afc<br />**数値**:<br />-2147206404|数量の 10 進コードが無効です。|
> |**名前**:<br />InvalidQuery<br />**16 進数**:<br />80044183<br />**数値**:<br />-2147204733|この操作に対して指定されたクエリが無効です|
> |**名前**:<br />InvalidQueryForVirtualEntity<br />**16 進数**:<br />80044822<br />**数値**:<br />-2147203038|指定されたクエリは仮想エンティティでサポートされていません。|
> |**名前**:<br />InvalidRecurrenceInterval<br />**16 進数**:<br />8004D2A1<br />**数値**:<br />-2147167583|定期的なアイテムを設定するには、間隔を 1 ～ 365 の間で指定する必要があります。|
> |**名前**:<br />InvalidRecurrenceIntervalForRollupJobs<br />**16 進数**:<br />8004D2A2<br />**数値**:<br />-2147167582|定期的なアイテムを設定するには、間隔を 1 時間以上に指定する必要があります。|
> |**名前**:<br />InvalidRecurrencePattern<br />**16 進数**:<br />8004E100<br />**数値**:<br />-2147163904|定期的なアイテムのパターンが無効です。|
> |**名前**:<br />InvalidRecurrenceRule<br />**16 進数**:<br />80040246<br />**数値**:<br />-2147220922|RecurrencePatternFactory でのエラー。|
> |**名前**:<br />InvalidRecurrenceRuleForBulkDeleteAndDuplicateDetection<br />**16 進数**:<br />8004D2A0<br />**数値**:<br />-2147167584|一括削除および重複データ検出の実行頻度は、日ごとに指定する必要があります。|
> |**名前**:<br />InvalidRegardingObjectTypeCode<br />**16 進数**:<br />80040319<br />**数値**:<br />-2147220711|関連オブジェクトの種類コードは、一括操作に対して無効です。|
> |**名前**:<br />InvalidRegistryKey<br />**16 進数**:<br />8004024c<br />**数値**:<br />-2147220916|指定されたレジストリ キーは無効です。|
> |**名前**:<br />InvalidRelationshipDescription<br />**16 進数**:<br />80047003<br />**数値**:<br />-2147192829|指定された関連付けは作成できません|
> |**名前**:<br />InvalidRelationshipInMOPIAssociation<br />**16 進数**:<br />80060999<br />**数値**:<br />-2147087975|親プロファイル項目で選択されているエンティティにこの関係は存在しません。|
> |**名前**:<br />InvalidRelationshipNameForControl<br />**16 進数**:<br />80060877<br />**数値**:<br />-2147088265|コントロール {0} にリレーションシップ名が指定されていません。[リレーションシップ名] は必須フィールドです。|
> |**名前**:<br />InvalidRelationshipQuery<br />**16 進数**:<br />80072528<br />**数値**:<br />-2147015384|RelationshipQuery が指定されている場合、少なくとも 1 つの関係プロパティーは、要求された EntityMetadata プロパティーの一部である必要があります。要求されたエンティティ プロパティの一覧に、property = {0}、{1}、{2} のうち少なくとも 1 つが必要です。|
> |**名前**:<br />InvalidRelationshipType<br />**16 進数**:<br />8004700f<br />**数値**:<br />-2147192817|指定された関連付けはこの操作では無効です|
> |**名前**:<br />InvalidRelationshipTypeForAccessory<br />**16 進数**:<br />8004F989<br />**数値**:<br />-2147157623|付属品の関係は常に一方向であり、変更できません。|
> |**名前**:<br />InvalidRelationshipTypeForUpSell<br />**16 進数**:<br />8004F988<br />**数値**:<br />-2147157624|アップセルの関係は常に一方向であり、変更できません。|
> |**名前**:<br />InvalidRelativeUrlFormat<br />**16 進数**:<br />80048054<br />**数値**:<br />-2147188652|相対 URL に無効な文字が含まれています。 別の名前を使用してください。 有効な相対 URL 名には、末尾に .aspx、.ashx、.asmx、.svc を使用したり、先頭または末尾にドットを使用したりできません。また、連続するドット、~ " # % & * : < > ? の各文字も使用できません。 / \ { | }。|
> |**名前**:<br />InvalidRequestBody<br />**16 進数**:<br />80072530<br />**数値**:<br />-2147015376|渡されたエンティティ オブジェクトは Null または空にできません。|
> |**名前**:<br />InvalidRequestDataFormat<br />**16 進数**:<br />80044271<br />**数値**:<br />-2147204495|更新した構成には無効なデータが含まれています。|
> |**名前**:<br />InvalidRequestParameter<br />**16 進数**:<br />80044828<br />**数値**:<br />-2147203032|要求パラメーターには名前と値の両方を指定する必要があります。|
> |**名前**:<br />InvalidRequestParameters<br />**16 進数**:<br />8006110E<br />**数値**:<br />-2147086066|要求パラメーターはサーバー外部パーティ要求に対して有効ではありません。|
> |**名前**:<br />InvalidResourceType<br />**16 進数**:<br />8004B029<br />**数値**:<br />-2147176407|要求されたアクションは、リソースの種類 {0}では無効です。|
> |**名前**:<br />InvalidRestore<br />**16 進数**:<br />80040258<br />**数値**:<br />-2147220904|RestoreCaller は SwitchToSystemUser の後に呼び出す必要があります。|
> |**名前**:<br />InvalidRole<br />**16 進数**:<br />8004B012<br />**数値**:<br />-2147176430|このユーザーにロールを割り当てていません|
> |**名前**:<br />InvalidRoleOccurrencesForOneToManyRelationship<br />**16 進数**:<br />8006089A<br />**数値**:<br />-2147088230|1 対多の関係に対し、2 つ以上のエンティティ関係ロールを関連付けすることはできません {0}。|
> |**名前**:<br />InvalidRoleTypeForOneToManyRelationship<br />**16 進数**:<br />80060899<br />**数値**:<br />-2147088231|この顧客間関係ロールの種類は、一対多関連付け {0} に対して有効ではありません。|
> |**名前**:<br />InvalidRollupQueryAttributeSet<br />**16 進数**:<br />8004F683<br />**数値**:<br />-2147158397|ロールアップ クエリは、目標指標で定義されていないロールアップ フィールド に対して設定することはできません。|
> |**名前**:<br />InvalidRollupType<br />**16 進数**:<br />80040234<br />**数値**:<br />-2147220940|ロールアップの種類が無効です。|
> |**名前**:<br />InvalidS2SAuthentication<br />**16 進数**:<br />8005E245<br />**数値**:<br />-2147098043|サーバー間認証は、Microsoft Online Services 環境 (Office 365) を使用して設定された Microsoft Dynamics 365 Online 組織用に作成される、電子メール サーバー プロファイルでのみ使用できます。|
> |**名前**:<br />InvalidSchemaName<br />**16 進数**:<br />8004700b<br />**数値**:<br />-2147192821|指定された名前のエンティティは既に存在しています。 一意の名前を指定してください。|
> |**名前**:<br />InvalidSearchEntities<br />**16 進数**:<br />80060202<br />**数値**:<br />-2147089918|検索 - {0} 有効なエンティティを見つけられませんでした。|
> |**名前**:<br />InvalidSearchEntity<br />**16 進数**:<br />80060201<br />**数値**:<br />-2147089919|検索エンティティ - {0} が無効です。|
> |**名前**:<br />InvalidSearchName<br />**16 進数**:<br />80060204<br />**数値**:<br />-2147089916|検索名 - {0} が無効です。|
> |**名前**:<br />InvalidSeriesId<br />**16 進数**:<br />8004E105<br />**数値**:<br />-2147163899|seriesid が null または無効です。|
> |**名前**:<br />InvalidSeriesIdOriginalStart<br />**16 進数**:<br />8004E109<br />**数値**:<br />-2147163895|seriesid または元の開始日が無効です。|
> |**名前**:<br />InvalidSeriesStatus<br />**16 進数**:<br />8004E10F<br />**数値**:<br />-2147163889|無効な系列の状態です。|
> |**名前**:<br />InvalidSharee<br />**16 進数**:<br />8004020c<br />**数値**:<br />-2147220980|共有 ID が無効です。|
> |**名前**:<br />InvalidSharePointSiteCollectionUrl<br />**16 進数**:<br />80048052<br />**数値**:<br />-2147188654|URL は http または https スキーマに従う必要があります。|
> |**名前**:<br />InvalidSimilarityRuleStateError<br />**16 進数**:<br />80044254<br />**数値**:<br />-2147204524|類似ルールの状態が無効です。|
> |**名前**:<br />InvalidSingletonResults<br />**16 進数**:<br />8004024f<br />**数値**:<br />-2147220913|CRM 内部例外: 単一の取得クエリは、1 つ以上のレコードを返す必要がありません。|
> |**名前**:<br />InvalidSiteRelativeUrlFormat<br />**16 進数**:<br />80048053<br />**数値**:<br />-2147188653|相対 URL に無効な文字が含まれています。 別の名前を使用してください。 有効な相対 URL 名には、末尾に .aspx、.ashx、.asmx、.svc を使用したり、先頭または末尾にドットやスラッシュを使用したりできません。また、連続するドットやスラッシュ、~ " # % & * : < > ? の各文字も使用できません。 \ { | }。|
> |**名前**:<br />InvalidSolutionAwarenessDeclaration<br />**16 進数**:<br />80072000<br />**数値**:<br />-2147016704|更新操作でエンティティをソリューション対応として宣言できません。 エンティティ: {0}|
> |**名前**:<br />InvalidSolutionConfigurationPage<br />**16 進数**:<br />8004701B<br />**数値**:<br />-2147192805|このソリューションに対する指定された構成ページは、無効です。|
> |**名前**:<br />InvalidSolutionUniqueName<br />**16 進数**:<br />8004F002<br />**数値**:<br />-2147160062|ソリューションの一意の名前として指定された文字列に、無効な文字が含まれています。 使用できる文字は、\[A-Z\]、\[a-z\]、\[0-9\]、および \_ のみです。 最初の文字には、\[A-Z\]、\[a-z\]、または \_ のみを使用できます。|
> |**名前**:<br />InvalidSolutionVersion<br />**16 進数**:<br />8004F01E<br />**数値**:<br />-2147160034|無効なソリューション バージョンが指定されました。|
> |**名前**:<br />InvalidSourceAttributeType<br />**16 進数**:<br />80044808<br />**数値**:<br />-2147203064|ソース属性の種類が指定された金額のデータの種類と一致しません。|
> |**名前**:<br />InvalidSourceEntityAttribute<br />**16 進数**:<br />80044806<br />**数値**:<br />-2147203066|属性は {0} エンティティ {1} の属性ではありません。|
> |**名前**:<br />InvalidSourceStateValue<br />**16 進数**:<br />80044810<br />**数値**:<br />-2147203056|エンティティに対して指定されたソースの状態が無効です。|
> |**名前**:<br />InvalidSourceStatusValue<br />**16 進数**:<br />80044811<br />**数値**:<br />-2147203055|エンティティに対して指定されたソースの状態が無効です。|
> |**名前**:<br />InvalidSourceType<br />**16 進数**:<br />80060437<br />**数値**:<br />-2147089353|SourceType {0} は {1} データの種類に対して有効ではありません。|
> |**名前**:<br />InvalidSourceTypeCode<br />**16 進数**:<br />800608EA<br />**数値**:<br />-2147088150|選択したソースの種類に有効なプロパティ バッグを選択してください。|
> |**名前**:<br />InvalidStage<br />**16 進数**:<br />80060452<br />**数値**:<br />-2147089326|検証エラー: 無効なステージ。|
> |**名前**:<br />InvalidStageTransition<br />**16 進数**:<br />80092003<br />**数値**:<br />-2146885629|無効なステージ移行です。 ステージ {0} への移行はプロセスのアクティブ パスにありません。|
> |**名前**:<br />InvalidStageTransitionOnInactiveInstance<br />**16 進数**:<br />80060377<br />**数値**:<br />-2147089545|無効なステージ移行です。 非アクティブなプロセスでステージ移行は許可されません。|
> |**名前**:<br />InvalidState<br />**16 進数**:<br />80040233<br />**数値**:<br />-2147220941|オブジェクトは、この操作を実行するのに有効な状態ではありません。|
> |**名前**:<br />InvalidStateCodeStatusCode<br />**16 進数**:<br />80048408<br />**数値**:<br />-2147187704|状態コードが無効か、または状態コードは有効ですが、指定されたステータス コードの状態コードが無効です。|
> |**名前**:<br />InvalidStateForPublish<br />**16 進数**:<br />8004F90A<br />**数値**:<br />-2147157750|指定された ProductFamily、製品またはバンドルは、そのメッセージを [下書き] 状態または [ActiveDraft] 状態からのみ公開できます|
> |**名前**:<br />InvalidStateTransition<br />**16 進数**:<br />8004F00E<br />**数値**:<br />-2147160050|{0} (Id ={1}) エンティティまたはコンポーネントを無効な状態から移行しようとしました: {2}。|
> |**名前**:<br />InvalidSubmitFromPublishedArticle<br />**16 進数**:<br />80048dfa<br />**数値**:<br />-2147185158|公開済みの状態にある記事を送信しようとしています。 下書き状態にある記事のみ送信できます。|
> |**名前**:<br />InvalidSubmitFromUnapprovedArticle<br />**16 進数**:<br />80048dff<br />**数値**:<br />-2147185153|未承認の状態にある記事を送信しようとしています。 下書き状態にある記事のみ送信できます。|
> |**名前**:<br />InvalidSubstituteProduct<br />**16 進数**:<br />80043aff<br />**数値**:<br />-2147206401|製品に製品自体とのリレーションシップを持たせることはできません。|
> |**名前**:<br />InvalidSyncDirectionValueForUpdate<br />**16 進数**:<br />80060742<br />**数値**:<br />-2147088574|1 つ以上の属性マッピングについて許可された同期方向に基づいて、同期方向は無効です。|
> |**名前**:<br />InvalidTargetEntity<br />**16 進数**:<br />80040369<br />**数値**:<br />-2147220631|指定したターゲット レコードの種類が存在しません。|
> |**名前**:<br />InvalidTargetEntityTypeForControl<br />**16 進数**:<br />80060878<br />**数値**:<br />-2147088264|コントロール {0} に対象エンティティの種類が指定されていません。[対象エンティティ] は必須フィールドです。|
> |**名前**:<br />InvalidTargetFrameworkVersion<br />**16 進数**:<br />8004420b<br />**数値**:<br />-2147204597|プラグイン アセンブリは、サポートされていないバージョンの .NET Framework を対象としています。|
> |**名前**:<br />InvalidTaskFlow<br />**16 進数**:<br />80060392<br />**数値**:<br />-2147089518|タスク フローが無効です。|
> |**名前**:<br />InvalidTemplate<br />**16 進数**:<br />8004B010<br />**数値**:<br />-2147176432|招待状の電子メール テンプレートが無効です。|
> |**名前**:<br />InvalidTemplateContent<br />**16 進数**:<br />800609B2<br />**数値**:<br />-2147087950|テンプレートの内容が無効です。|
> |**名前**:<br />InvalidTemplateId<br />**16 進数**:<br />80050019<br />**数値**:<br />-2147155943|有効なテンプレートではありません。|
> |**名前**:<br />InvalidTenantIDValue<br />**16 進数**:<br />8005E25B<br />**数値**:<br />-2147098021|Exchange Online テナント ID 値が無効です。フィールドの値は GUID の構造の文字列である必要があります。|
> |**名前**:<br />InvalidThemeDeleteOperation<br />**16 進数**:<br />800608D7<br />**数値**:<br />-2147088169|システム テーマまたは既定のテーマを削除することはできません。|
> |**名前**:<br />InvalidThemeId<br />**16 進数**:<br />800608D4<br />**数値**:<br />-2147088172|テーマ ID が無効です。|
> |**名前**:<br />InvalidTimeZoneCode<br />**16 進数**:<br />800608F7<br />**数値**:<br />-2147088137|指定されたタイム ゾーン コード {0} が認識されません。 有効なタイム ゾーンコード値を指定してください。|
> |**名前**:<br />InvalidToken<br />**16 進数**:<br />8004B061<br />**数値**:<br />-2147176351|このトークンは無効です。|
> |**名前**:<br />InvalidTotalDiscount<br />**16 進数**:<br />800404f4<br />**数値**:<br />-2147220236|合計割引が無効です|
> |**名前**:<br />InvalidTotalPrice<br />**16 進数**:<br />800404f5<br />**数値**:<br />-2147220235|合計価格が無効です|
> |**名前**:<br />InvalidTransformationParameter<br />**16 進数**:<br />80040389<br />**数値**:<br />-2147220599|変換のためのパラメーターが見つからないか、無効です。|
> |**名前**:<br />InvalidTransformationParameterDataType<br />**16 進数**:<br />80040380<br />**数値**:<br />-2147220608|変換パラメーターの複数のデータの種類はサポートされていません。|
> |**名前**:<br />InvalidTransformationParameterEmptyCollection<br />**16 進数**:<br />80048511<br />**数値**:<br />-2147187439|変換パラメーター: {0} は無効な入力値の長さ: {1}。 パラメーターの長さを、空のコレクションにすることはできません。|
> |**名前**:<br />InvalidTransformationParameterMapping<br />**16 進数**:<br />80040382<br />**数値**:<br />-2147220606|定義された変換パラメーター マッピングが無効です。 ターゲット属性名が存在することを確認します。|
> |**名前**:<br />InvalidTransformationParameterMappings<br />**16 進数**:<br />8004037c<br />**数値**:<br />-2147220612|1 つ以上の変換パラメーター マッピングが無効、または変換パラメーター Description が一致しません。|
> |**名前**:<br />InvalidTransformationParameterOutsideRange<br />**16 進数**:<br />80048510<br />**数値**:<br />-2147187440|変換パラメーター: {0} は無効な入力値: {1}。 パラメーターは許容範囲外です: {2}。 |
> |**名前**:<br />InvalidTransformationParameterOutsideRangeGeneric<br />**16 進数**:<br />80048512<br />**数値**:<br />-2147187438|1 つまたは複数の入力変換パラメーター値が許容範囲外です: {0}。|
> |**名前**:<br />InvalidTransformationParametersGeneric<br />**16 進数**:<br />80048507<br />**数値**:<br />-2147187449|変換パラメーター: {0} は無効な入力値: {1}。 パラメーターは次の種類である必要があります: {2}。|
> |**名前**:<br />InvalidTransformationParameterString<br />**16 進数**:<br />80048508<br />**数値**:<br />-2147187448|変換パラメーター: {0} は無効な入力値: {1}。 パラメータは、空でない文字列である必要があります。|
> |**名前**:<br />InvalidTransformationParameterZeroToRange<br />**16 進数**:<br />80048509<br />**数値**:<br />-2147187447|変換パラメーター: {0} は無効な入力値: {1}。 パラメーター値は、0 より大きく、パラメータ 1 の長さより小さい必要があります。|
> |**名前**:<br />InvalidTransformationType<br />**16 進数**:<br />8004037a<br />**数値**:<br />-2147220614|指定された変換の種類はサポートされていません。|
> |**名前**:<br />InvalidTranslationsFile<br />**16 進数**:<br />80044249<br />**数値**:<br />-2147204535|翻訳ファイルが無効か、必要なスキーマに準拠していません。|
> |**名前**:<br />InvalidTraversedPath<br />**16 進数**:<br />80092007<br />**数値**:<br />-2146885625|渡ったパスが無効です。|
> |**名前**:<br />InvalidUniqueName<br />**16 進数**:<br />80060386<br />**数値**:<br />-2147089530|アクションの一意の名前が無効です。|
> |**名前**:<br />InvalidUnpublishFromDraftArticle<br />**16 進数**:<br />80048dfc<br />**数値**:<br />-2147185156|下書きの状態にある記事の公開を取り下げようとしています。 公開済みの状態にある記事のみを公開取り下げできます。|
> |**名前**:<br />InvalidUnpublishFromUnapprovedArticle<br />**16 進数**:<br />80048dfe<br />**数値**:<br />-2147185154|未承認の状態にある記事の公開を取り下げようとしています。 公開の状態にある記事のみを公開取り下げできます。|
> |**名前**:<br />InvalidUpdateOnProtectedComponent<br />**16 進数**:<br />8004F012<br />**数値**:<br />-2147160046|{0} {1} を更新できません。 {0} が管理されている場合、更新を実行することはできません。|
> |**名前**:<br />InvalidUrlConsecutiveSlashes<br />**16 進数**:<br />80048056<br />**数値**:<br />-2147188650|URL に許可されていない連続するスラッシュが含まれています。|
> |**名前**:<br />InvalidUrlProtocol<br />**16 進数**:<br />8004E30F<br />**数値**:<br />-2147163377|指定された URL は無効です。|
> |**名前**:<br />InvalidUserAuth<br />**16 進数**:<br />80040204<br />**数値**:<br />-2147220988|ユーザーにこの操作を実行する特権がありません。|
> |**名前**:<br />InvalidUserLicenseCount<br />**16 進数**:<br />8004B027<br />**数値**:<br />-2147176409|オファリング {1} のユーザー ライセンスを購入する {0} ことはできません。|
> |**名前**:<br />InvalidUserName<br />**16 進数**:<br />80048095<br />**数値**:<br />-2147188587|ユーザー名は <name>@<domain> の形式で入力する必要があります。 形式を修正して、やり直してください。|
> |**名前**:<br />InvalidUserQuota<br />**16 進数**:<br />8004B011<br />**数値**:<br />-2147176431|ユーザー数が最大値に達しました|
> |**名前**:<br />InvalidUserToImportExcelOnlineFile<br />**16 進数**:<br />80060807<br />**数値**:<br />-2147088377|このファイルをインポートするためのアクセス許可がありません。 このデータをエクスポートしたユーザーのみ、このファイルをインポートすることができます。|
> |**名前**:<br />InvalidUserToViewExcelOnlineFile<br />**16 進数**:<br />80060806<br />**数値**:<br />-2147088378|このファイルを表示するためのアクセス許可がありません。 このデータをエクスポートしたユーザーのみ、このファイルを表示することができます。|
> |**名前**:<br />InvalidValueForCountryCode<br />**16 進数**:<br />8004B022<br />**数値**:<br />-2147176414|アカウントの国/地域コードは {0} にすることはできません。|
> |**名前**:<br />InvalidValueForCurrency<br />**16 進数**:<br />8004B023<br />**数値**:<br />-2147176413|アカウントの通貨コードは {0} にすることはできません。|
> |**名前**:<br />InvalidValueForDataDelimiter<br />**16 進数**:<br />80040341<br />**数値**:<br />-2147220671|データ区切り文字が無効です。|
> |**名前**:<br />InvalidValueForFieldDelimiter<br />**16 進数**:<br />80040340<br />**数値**:<br />-2147220672|フィールド区切り文字が無効です。|
> |**名前**:<br />InvalidValueForFileType<br />**16 進数**:<br />80040348<br />**数値**:<br />-2147220664|ファイルの種類が無効です。|
> |**名前**:<br />InvalidValueForLocale<br />**16 進数**:<br />8004B024<br />**数値**:<br />-2147176412|アカウントのロケール コードは {0} にすることはできません。|
> |**名前**:<br />InvalidValueProcessEmailAfter<br />**16 進数**:<br />8005E244<br />**数値**:<br />-2147098044|所属組織で許可されている日付よりも前の日付がフィールドに指定されています。 指定された日付以降の日付を入力してからやり直してください。|
> |**名前**:<br />InvalidVersion<br />**16 進数**:<br />8004023c<br />**数値**:<br />-2147220932|ハンドルされないバージョンの不一致があります。|
> |**名前**:<br />InvalidViewReference<br />**16 進数**:<br />800609B3<br />**数値**:<br />-2147087949|ビューが指定されていないか、無効です。|
> |**名前**:<br />InvalidWebResourceForVisualization<br />**16 進数**:<br />8004E017<br />**数値**:<br />-2147164137|{0} というWebリソースの種類では、ビジュアル化がサポートされていません。|
> |**名前**:<br />InvalidWebresourceId<br />**16 進数**:<br />8005012B<br />**数値**:<br />-2147155669|Web リソース ID が無効です。|
> |**名前**:<br />InvalidWebresourceType<br />**16 進数**:<br />8005012D<br />**数値**:<br />-2147155667|アプリのアイコンに提供される Web リソースが無効です。|
> |**名前**:<br />InvalidWebToLeadRedirect<br />**16 進数**:<br />80048476<br />**数値**:<br />-2147187594|redirectto は web2lead リダイレクトに対して無効です。|
> |**名前**:<br />InvalidWelcomePageId<br />**16 進数**:<br />8005012C<br />**数値**:<br />-2147155668|[ようこそ] ページの ID が無効です。|
> |**名前**:<br />InvalidWelcomePageType<br />**16 進数**:<br />8005012E<br />**数値**:<br />-2147155666|アプリの [ようこそ] ページで提供される Web リソースが無効です。|
> |**名前**:<br />InvalidWordDocumentTemplate<br />**16 進数**:<br />800608EF<br />**数値**:<br />-2147088145|ドキュメント テンプレートが無効です。|
> |**名前**:<br />InvalidWordFileType<br />**16 進数**:<br />800608EE<br />**数値**:<br />-2147088146|サポートされていないファイルの種類です。|
> |**名前**:<br />InvalidWordTemplateContent<br />**16 進数**:<br />800608FB<br />**数値**:<br />-2147088133|テンプレートの内容が無効です。|
> |**名前**:<br />InvalidWordXmlFile<br />**16 進数**:<br />80048441<br />**数値**:<br />-2147187647|Microsoft Word XML 形式のファイルのみをアップロードできます。|
> |**名前**:<br />InvalidWorkflowOrWorkflowDoesNotExist<br />**16 進数**:<br />8006040a<br />**数値**:<br />-2147089398|ワークフローが無効、またはワークフローが存在しません。|
> |**名前**:<br />InvalidXaml<br />**16 進数**:<br />80060417<br />**数値**:<br />-2147089385|ワークフローの XAML は NULL か空白です|
> |**名前**:<br />InvalidXml<br />**16 進数**:<br />80040201<br />**数値**:<br />-2147220991|無効な XML.|
> |**名前**:<br />InvalidXmlCollectionNameException<br />**16 進数**:<br />80040247<br />**数値**:<br />-2147220921|無効な Xml のコレクション名です。|
> |**名前**:<br />InvalidXmlEntityNameException<br />**16 進数**:<br />80040248<br />**数値**:<br />-2147220920|無効な Xml のエンティティ名です。|
> |**名前**:<br />InvalidXmlForParameters<br />**16 進数**:<br />80060410<br />**数値**:<br />-2147089392|ControlStep のパラメーター ノードに無効な XML があります。|
> |**名前**:<br />InvalidXmlSSContent<br />**16 進数**:<br />80040350<br />**数値**:<br />-2147220656|無効なエンティティ データが含まれているか、形式が正しくないため、データ ファイルをインポートできません。 ファイルに正しいデータが含まれていること、およびファイルが XML スプレッドシート 2003 形式であることを確認して、もう一度アップロードしてください。|
> |**名前**:<br />InvalidXrmSdkReference<br />**16 進数**:<br />8004419b<br />**数値**:<br />-2147204709|プラグイン アセンブリは、サーバーのバージョンより新しい Microsoft.Xrm.Sdk のバージョンを参照します。|
> |**名前**:<br />InvalidZipFileForImport<br />**16 進数**:<br />80048482<br />**数値**:<br />-2147187582|指定された圧縮 (.zip) ファイルには、インポートできないファイルが含まれます。 .zip ファイルに含めることができるのは、.xlsx、.csv、または .xml ファイルのみです。|
> |**名前**:<br />InvalidZipFileFormat<br />**16 進数**:<br />80048488<br />**数値**:<br />-2147187576|アップロードしようとしているファイルが有効なファイルではありません。 ファイルを確認してから再度お試しください。|
> |**名前**:<br />InvitationBillingAdminUnknown<br />**16 進数**:<br />8004D213<br />**数値**:<br />-2147167725|この組織の請求管理者ではないため、招待状を送信することはできません。  組織の請求管理者に連絡して招待状の送信を依頼するか、または、請求管理者が https://billing.microsoft.com にアクセスして請求管理者を委任してください。 それから招待状を送信することができます。|
> |**名前**:<br />InvitationCannotBeReset<br />**16 進数**:<br />8004D210<br />**数値**:<br />-2147167728|ユーザーの招待状は、リセットされません。|
> |**名前**:<br />InvitationIsAccepted<br />**16 進数**:<br />8004D208<br />**数値**:<br />-2147167736|{0} -- 招待状は既に承諾されています -- トークン ={1} PUID={2} ID={3} 状態 ={4}|
> |**名前**:<br />InvitationIsExpired<br />**16 進数**:<br />8004D207<br />**数値**:<br />-2147167737|{0} -- 招待状は期限が切れています -- トークン ={1} PUID={2} ID={3} 状態 ={4}|
> |**名前**:<br />InvitationIsRejected<br />**16 進数**:<br />8004D209<br />**数値**:<br />-2147167735|{0} -- 招待状は既に新しいユーザーにより拒否されています -- トークン ={1} PUID={2} ID={3} 状態 ={4}|
> |**名前**:<br />InvitationIsRevoked<br />**16 進数**:<br />8004D20A<br />**数値**:<br />-2147167734|{0} -- 招待状は既に組織により失効されています -- トークン ={1} PUID={2} ID={3} 状態 ={4}|
> |**名前**:<br />InvitationNotFound<br />**16 進数**:<br />8004D204<br />**数値**:<br />-2147167740|{0} -- 招待状は見つからないまたは状態が開いていません -- トークン ={1} PUID={2} ID={3} 状態 ={4}|
> |**名前**:<br />InvitationOrganizationNotEnabled<br />**16 進数**:<br />8004D217<br />**数値**:<br />-2147167721|招待状の組織は無効になっています。|
> |**名前**:<br />InvitationSendToSelf<br />**16 進数**:<br />8004D20F<br />**数値**:<br />-2147167729|招待状をユーザーに送信することはできません。|
> |**名前**:<br />InvitationStatusError<br />**16 進数**:<br />8004D20C<br />**数値**:<br />-2147167732|"招待状には状態 {0} があります。"|
> |**名前**:<br />InvitationWrongUserOrgRelation<br />**16 進数**:<br />8004D206<br />**数値**:<br />-2147167738|{0} -- 事前作成されたユーザー組織関係 {1} は間違っています。  認証 {2} は他のユーザーにより既に使用されています|
> |**名前**:<br />InvitedUserAlreadyAdded<br />**16 進数**:<br />8004D205<br />**数値**:<br />-2147167739|{0} -- CRM ユーザー {1} は招待している組織 {3} にではなく、組織 {2} に既に追加されています|
> |**名前**:<br />InvitedUserAlreadyExists<br />**16 進数**:<br />8004D202<br />**数値**:<br />-2147167742|{0} -- 招待されたユーザーは、既に組織内に含まれています -- {1}|
> |**名前**:<br />InvitedUserIsOrganization<br />**16 進数**:<br />8004D203<br />**数値**:<br />-2147167741|{0} -- ユーザー {1} には認証 {2} があり、関係 ID {4} を持つ組織 {3} に既に関連付けられています|
> |**名前**:<br />InvitedUserMultipleTimes<br />**16 進数**:<br />8004D20B<br />**数値**:<br />-2147167733|Dynamics 365 のユーザー {0} は複数回招待されました。|
> |**名前**:<br />InvitingOrganizationNotFound<br />**16 進数**:<br />8004D200<br />**数値**:<br />-2147167744|{0} -- 招待している組織が見つかりません -- {1}|
> |**名前**:<br />InvitingUserNotInOrganization<br />**16 進数**:<br />8004D201<br />**数値**:<br />-2147167743|{0} -- 招待しているユーザーは、招待している組織には含まれていません -- {1}|
> |**名前**:<br />IsKitCannotBeNull<br />**16 進数**:<br />80044158<br />**数値**:<br />-2147204776|属性 iskit は null にはできません。|
> |**名前**:<br />IsNotLiveToSendInvitation<br />**16 進数**:<br />8004B009<br />**数値**:<br />-2147176439|この機能はサポートされていません。Online ソリューションでのみ使用可能です。|
> |**名前**:<br />IsvAborted<br />**16 進数**:<br />80040265<br />**数値**:<br />-2147220891|ISV コードが操作を中止しました。|
> |**名前**:<br />IsvExtensionsPrivilegeNotPresent<br />**16 進数**:<br />80048029<br />**数値**:<br />-2147188695|ISV.Config をインポートするには、ISV 拡張の特権が含まれるセキュリティ ロールに関連付けられたユーザー アカウントを使用する必要があります。|
> |**名前**:<br />IsvUnExpected<br />**16 進数**:<br />80040224<br />**数値**:<br />-2147220956|ISV コードで予期しないエラーが発生しました。|
> |**名前**:<br />JobNameIsEmptyOrNull<br />**16 進数**:<br />80048457<br />**数値**:<br />-2147187625|ジョブ名は、null または空白にすることはできません。|
> |**名前**:<br />KBInvalidCreateAssociation<br />**16 進数**:<br />80060861<br />**数値**:<br />-2147088287|このサポート情報記事は既に {0} にリンクされています。|
> |**名前**:<br />KnowledgeSearchActiveModelsAlreadyExist<br />**16 進数**:<br />80061680<br />**数値**:<br />-2147084672|ソース エンティティ {0} にはアクティブな構成が既に存在します。 ソース エンティティごとに許可されるアクティブな構成は 1 つだけです。|
> |**名前**:<br />LabelIdDoesNotMatchStepId<br />**16 進数**:<br />80060419<br />**数値**:<br />-2147089383|ラベル ID {0} はステップ ID {1}と一致しません。|
> |**名前**:<br />LanguageProvisioningSrsDataConnectorNotInstalled<br />**16 進数**:<br />8004F710<br />**数値**:<br />-2147158256|この組織に対して言語を準備するためには、Microsoft Dynamics 365 Reporting Extensions をインストールする必要があります。|
> |**名前**:<br />LeadAlreadyInClosedState<br />**16 進数**:<br />80040519<br />**数値**:<br />-2147220199|リードは既にクローズしています。|
> |**名前**:<br />LeadAlreadyInOpenState<br />**16 進数**:<br />80040518<br />**数値**:<br />-2147220200|潜在顧客は、既にオープン状態にあります。|
> |**名前**:<br />LegacyXlsxFileNotSupported<br />**16 進数**:<br />800608CF<br />**数値**:<br />-2147088177|レガシ .xlsx ファイルは Excel テンプレートに使用できません。|
> |**名前**:<br />LicenseConfigFileInvalid<br />**16 進数**:<br />8004D250<br />**数値**:<br />-2147167664|提供された構成ファイル {0} には有効な書式設定があります。|
> |**名前**:<br />LicenseNotEnoughToActivate<br />**16 進数**:<br />80042f14<br />**数値**:<br />-2147209452|アクティブ化されたユーザー数に対して、使用可能なライセンスが不足しています。|
> |**名前**:<br />LicenseRegistrationExpired<br />**16 進数**:<br />8004415d<br />**数値**:<br />-2147204771|Microsoft Dynamics 365 の登録期間は終了しました。|
> |**名前**:<br />LicenseTampered<br />**16 進数**:<br />8004415f<br />**数値**:<br />-2147204769|Microsoft Dynamics 365 のこのインストールのライセンスが改ざんされました。 システムは使用できません。 Microsoft 製品サポート サービスにお問い合わせください。|
> |**名前**:<br />LicenseTrialExpired<br />**16 進数**:<br />8004415c<br />**数値**:<br />-2147204772|Microsoft Dynamics 365 試用インストールが期限切れになりました。|
> |**名前**:<br />LicenseUpgradePathNotAllowed<br />**16 進数**:<br />8004D247<br />**数値**:<br />-2147167673|指定されたライセンスの種類は更新できません。|
> |**名前**:<br />LinkedEntitiesAreNotAllowed<br />**16 進数**:<br />80071120<br />**数値**:<br />-2147020512|リンクしているエンティティはフィルターで許可されていません|
> |**名前**:<br />LiveAdminUnknownCommand<br />**16 進数**:<br />8004D239<br />**数値**:<br />-2147167687|不明な管理コマンド {0}|
> |**名前**:<br />LiveAdminUnknownObject<br />**16 進数**:<br />8004D238<br />**数値**:<br />-2147167688|不明な管理ターゲット {0}|
> |**名前**:<br />LivePlatformEmailInvalidBody<br />**16 進数**:<br />8004B524<br />**数値**:<br />-2147175132|"本文" パラメータは空白または null です。|
> |**名前**:<br />LivePlatformEmailInvalidFrom<br />**16 進数**:<br />8004B522<br />**数値**:<br />-2147175134|"差出人" パラメータは空白または null です。|
> |**名前**:<br />LivePlatformEmailInvalidSubject<br />**16 進数**:<br />8004B523<br />**数値**:<br />-2147175133|"件名" パラメータは空白または null です。|
> |**名前**:<br />LivePlatformEmailInvalidTo<br />**16 進数**:<br />8004B521<br />**数値**:<br />-2147175135|"宛先" パラメータは空白または null です。|
> |**名前**:<br />LivePlatformGeneralEmailError<br />**16 進数**:<br />8005B520<br />**数値**:<br />-2147109600|電子メールエラーが発生しました|
> |**名前**:<br />LocalDataSourceAbortError<br />**16 進数**:<br />80072453<br />**数値**:<br />-2147015597|ブラウザ操作が停止しました。 やり直してください。|
> |**名前**:<br />LocalDataSourceDatabaseError<br />**16 進数**:<br />80072455<br />**数値**:<br />-2147015595|ブラウザ データベース エラーのため、ブラウザ操作が失敗しました。 やり直してください。 動作しない場合は、操作が完了するまでデバイスのロックを解除した状態にして同じ操作をもう一度試してください。|
> |**名前**:<br />LocalDataSourceError<br />**16 進数**:<br />80072451<br />**数値**:<br />-2147015599|操作が失敗しました。 やり直してください。|
> |**名前**:<br />LocalDataSourceQuotaExceededError<br />**16 進数**:<br />80072452<br />**数値**:<br />-2147015598|ブラウザー記憶域の割り当てに十分なスペースがないか、ブラウザー記憶域の割り当て上限に達したため操作が失敗しました。ユーザーはブラウザー データベースに追加領域を提供することを拒否しました。|
> |**名前**:<br />LocalDataSourceTimeOutError<br />**16 進数**:<br />80072454<br />**数値**:<br />-2147015596|操作がタイムアウトしました。やり直してください。|
> |**名前**:<br />LockStatusNotValidForDynamicList<br />**16 進数**:<br />8004F703<br />**数値**:<br />-2147158269|動的リストにはロック状態を指定できません。|
> |**名前**:<br />LogoImageNodeDoesNotExist<br />**16 進数**:<br />800608D2<br />**数値**:<br />-2147088174|組織のキャッシュにあるテーマのデータのロゴ画像ノードが存在しません。|
> |**名前**:<br />LongParseRow<br />**16 進数**:<br />80040372<br />**数値**:<br />-2147220622|行が長すぎるため、インポートできません|
> |**名前**:<br />LookupNotFound<br />**16 進数**:<br />80040353<br />**数値**:<br />-2147220653|参照を解決できませんでした|
> |**名前**:<br />LowerVersionUpgrade<br />**16 進数**:<br />80048541<br />**数値**:<br />-2147187391|インポート ソリューションは、更新している既存のソリューションよりも新しいバージョンである必要があります。|
> |**名前**:<br />LowQuantityGreaterThanHighQuantity<br />**16 進数**:<br />80043b01<br />**数値**:<br />-2147206399|下限数量は上限数量未満である必要があります。|
> |**名前**:<br />LowQuantityLessThanZero<br />**16 進数**:<br />80043b00<br />**数値**:<br />-2147206400|下限数量は 0 より大きい必要があります。|
> |**名前**:<br />MailApp_AppointmentFeatureNotEnabled<br />**16 進数**:<br />80061218<br />**数値**:<br />-2147085800|アプリケーションへのアクセスは、この Microsoft Dynamics 365 組織の予定に対して有効になりませんでした。 システム管理者に問い合わせて、予定に対するアクセスを有効にしてください。|
> |**名前**:<br />MailApp_DifferentSecurityZoneError<br />**16 進数**:<br />80061210<br />**数値**:<br />-2147085808|次の URL を信頼済みサイトに追加してみてください: {0} {1} {2}|
> |**名前**:<br />MailApp_EmailAddressMismatch<br />**16 進数**:<br />80061211<br />**数値**:<br />-2147085807|認識できない電子メール アドレスから Outlook 用 CRM アプリにアクセスしようとしている可能性があります。 Dynamics CRM 用に使用している電子メールアドレスでサインアウトおよびサインインします。またはシステム管理者に、電子メール メールボックスの設定をこの電子メール アドレスを反映するよう更新してもらってください。|
> |**名前**:<br />MailApp_FeatureControlBitDisabled<br />**16 進数**:<br />80061204<br />**数値**:<br />-2147085820|アプリケーションへのアクセスは、この Microsoft Dynamics 365 組織に対して有効になりませんでした。 システム管理者に問い合わせて、このアプリに対するアクセスを有効にしてください。|
> |**名前**:<br />MailApp_MailboxNotConfiguredWithServerSideSync<br />**16 進数**:<br />80061202<br />**数値**:<br />-2147085822|電子メール アカウントは受信メールに対してサーバー側同期が設定されていません。|
> |**名前**:<br />MailApp_MailboxNotConfiguredWithServerSideSyncForACT<br />**16 進数**:<br />80061217<br />**数値**:<br />-2147085801|電子メールアカウントは、予定、取引先担当者、およびタスクに対してサーバー側同期で設定されていません。|
> |**名前**:<br />MailApp_MailboxServerSideSyncConfigurationFailure<br />**16 進数**:<br />80061220<br />**数値**:<br />-2147085792|Microsoft Dynamics 365 サーバー側同期が受信メールに対して失敗しました。|
> |**名前**:<br />MailApp_MailboxServerSideSyncConfigurationFailureForACT<br />**16 進数**:<br />80061221<br />**数値**:<br />-2147085791|Microsoft Dynamics 365 サーバー側同期が予定に対して失敗しました。|
> |**名前**:<br />MailApp_MobileBrowserIsNotSupported<br />**16 進数**:<br />80061208<br />**数値**:<br />-2147085816|[Outlook] のモバイル ブラウザー バージョンは現在サポートされていません。 Outlook デスクトップ アプリケーションからやり直してください。|
> |**名前**:<br />MailApp_PermissionsToReadContactRequired<br />**16 進数**:<br />80061219<br />**数値**:<br />-2147085799|ユーザーに十分な特権がないため、受信者が Dynamics 365 に存在するかどうかを確認できません。|
> |**名前**:<br />MailApp_PermissionToUseCrmForOfficeAppsRequired<br />**16 進数**:<br />80061205<br />**数値**:<br />-2147085819|ユーザーにこのアプリにアクセスするアクセス許可がありません。|
> |**名前**:<br />MailApp_ReadWriteAccessRequired<br />**16 進数**:<br />80061203<br />**数値**:<br />-2147085821|ユーザーは Dynamics 365 に対する管理者アクセス権のみがあります|
> |**名前**:<br />MailApp_TrackingIsNotSupported<br />**16 進数**:<br />80061207<br />**数値**:<br />-2147085817|Outlook のこのバージョンは、新しい電子メールの追跡をサポートしていません。|
> |**名前**:<br />MailApp_UnsupportedBrowser<br />**16 進数**:<br />80061201<br />**数値**:<br />-2147085823|ご使用のブラウザーは、現在サポートされていません。|
> |**名前**:<br />MailApp_UnsupportedDevice<br />**16 進数**:<br />80061200<br />**数値**:<br />-2147085824|ご使用のデバイスは、現在サポートされていません。|
> |**名前**:<br />MailApp_UserMailboxInactive<br />**16 進数**:<br />80061216<br />**数値**:<br />-2147085802|ユーザーのメールボックスが非アクティブです|
> |**名前**:<br />MailAppLimitedMode<br />**16 進数**:<br />80061222<br />**数値**:<br />-2147085790|サーバー側の同期が正しく設定されておらず、MailApp を LimitedMode でのみロードできる場合の一般的なエラー|
> |**名前**:<br />MailboxCannotDeleteEmails<br />**16 進数**:<br />8005E233<br />**数値**:<br />-2147098061|[処理後の電子メール削除] オプションを [はい] に設定することはできません。|
> |**名前**:<br />MailboxCannotModifyEmailAddress<br />**16 進数**:<br />8005E208<br />**数値**:<br />-2147098104|ユーザー/キューに関連付けられている場合、メールボックスの電子メール アドレスは更新できません。|
> |**名前**:<br />MailboxCredentialNotSpecified<br />**16 進数**:<br />8005E209<br />**数値**:<br />-2147098103|ユーザー名が指定されていません|
> |**名前**:<br />MailboxTrackingFolderMappingCannotBeUpdated<br />**16 進数**:<br />8006088C<br />**数値**:<br />-2147088244|メールボックス追跡フォルダー マッピングは更新できません。|
> |**名前**:<br />MailboxUnsupportedEmailServerType<br />**16 進数**:<br />8005E247<br />**数値**:<br />-2147098041|予定、取引先担当者、およびタスク用サーバー側同期は、POP3/SMTP 電子メール サーバーではサポートされていません。 サポートされている電子メールの種類を選択するか、予定、連絡先、およびタスクの同期方法を [なし] に変更してください。|
> |**名前**:<br />ManagedBpfDeletionInvalid<br />**16 進数**:<br />80060383<br />**数値**:<br />-2147089533| 業務プロセス フローは管理ソリューションに含まれており、個別に削除できません。 親ソリューションをアンインストールして、業務プロセス フロー内を削除します。|
> |**名前**:<br />ManagedProcessDeletionError<br />**16 進数**:<br />80072457<br />**数値**:<br />-2147015593|プロセスは管理ソリューションに含まれており、個別に削除できません。 親ソリューションをアンインストールして、プロセスを削除します。|
> |**名前**:<br />ManifestParsingFailure<br />**16 進数**:<br />80048534<br />**数値**:<br />-2147187404|OrganizationId を取得する指定されたマニフェスト ファイルを解析できませんでした|
> |**名前**:<br />ManifestXsdValidationError<br />**16 進数**:<br />80160001<br />**数値**:<br />-2146041855|インポート マニフェスト ファイルが無効です。 XSD 検証は次のエラーで失敗しました: '{0}'。"|
> |**名前**:<br />ManyToManyVirtualEntityNotSupported<br />**16 進数**:<br />80044820<br />**数値**:<br />-2147203040|仮想エンティティ間の N:N の関連付けはサポートされません。|
> |**名前**:<br />MappingExistsForTargetAttribute<br />**16 進数**:<br />8004033e<br />**数値**:<br />-2147220674|この属性は複数回マップされます。 重複するマッピングを削除してから、もう一度このデータ マップをインポートしてください。|
> |**名前**:<br />MarsConnectorDisableFailure<br />**16 進数**:<br />80071108<br />**数値**:<br />-2147020536|Mars コネクタの無効化でエラーが発生しました。|
> |**名前**:<br />MarsConnectorEnableFailure<br />**16 進数**:<br />80071107<br />**数値**:<br />-2147020537|Mars コネクタの有効化でエラーが発生しました。|
> |**名前**:<br />MatchingAttributeNameNotNullError<br />**16 進数**:<br />80044243<br />**数値**:<br />-2147204541|一致する属性名は、null の単一エンティティ ルールである必要があります。|
> |**名前**:<br />MaxActiveSLAError<br />**16 進数**:<br />8004F897<br />**数値**:<br />-2147157865|この SLA をアクティブ化できません。組織でアクティブな SLA を持つことができるエンティティの最大数を超えています。|
> |**名前**:<br />MaxActiveSLAKPIError<br />**16 進数**:<br />8004F898<br />**数値**:<br />-2147157864|この SLA をアクティブ化できません。組織でエンティティごとに許可されるアクティブな SLA KPI の最大数を超えています。|
> |**名前**:<br />MaxChildCasesLimitExceeded<br />**16 進数**:<br />8003F454<br />**数値**:<br />-2147224492|親サポート案件は、許可される子サポート案件の最大数を超えることはできません。 詳細については、管理者に問い合わせてください。|
> |**名前**:<br />MaxConditionsMobileOfflineFilters<br />**16 進数**:<br />80071114<br />**数値**:<br />-2147020524|エンティティごとに定義できる Mobile Offline 組織フィルター条件は 3 つのみです。|
> |**名前**:<br />MaximumControlsLimitExceeded<br />**16 進数**:<br />8004E301<br />**数値**:<br />-2147163391|ダッシュボード フォーム XML にはコントロール要素の許容最大数以上が含まれます: {0}。|
> |**名前**:<br />MaximumCountForUpdateModeExceeded<br />**16 進数**:<br />8004F602<br />**数値**:<br />-2147158526|更新操作では、一度に 1 つのファイルのみインポートできます。|
> |**名前**:<br />MaximumNumberHandlersExceeded<br />**16 進数**:<br />80048505<br />**数値**:<br />-2147187451|このソリューションによってフォーム イベント ハンドラーが追加されると、フォーム イベントのイベント ハンドラーの数が最大数を超えます。|
> |**名前**:<br />MaximumNumberOfAttributesForEntityReached<br />**16 進数**:<br />8004841A<br />**数値**:<br />-2147187686|エンティティで許可される属性の最大数に達しました。 属性を作成することができません。|
> |**名前**:<br />MaxLimitForRollupAttribute<br />**16 進数**:<br />8004480a<br />**数値**:<br />-2147203062|指標ごとに指標の詳細を 3 つのみ作成することができます。|
> |**名前**:<br />MaxMatchCodeLengthExceeded<br />**16 進数**:<br />80048429<br />**数値**:<br />-2147187671|マッチコードの長さが最大限度を超える可能性があるため、ルールの条件を作成または更新することはできません。|
> |**名前**:<br />MaxProductsAllowed<br />**16 進数**:<br />80071020<br />**数値**:<br />-2147020768|{0} 以上の製品を作成することはできません。|
> |**名前**:<br />MaxprofileItemFilterConditionsAllowed<br />**16 進数**:<br />80071116<br />**数値**:<br />-2147020522|エンティティごとに定義できる Mobile Offline エンティティのフィルター条件は 6 つのみです。|
> |**名前**:<br />MaxUnzipFolderSizeExceeded<br />**16 進数**:<br />80048499<br />**数値**:<br />-2147187559|選択されている圧縮 (.zip) ファイルは大きすぎるため解凍できません。|
> |**名前**:<br />MeasureDataTypeInvalid<br />**16 進数**:<br />8004E010<br />**数値**:<br />-2147164144|ビジュアル化のデータ記述が無効です。 いずれかの非集計メジャーに関する属性の種類が無効です。 データ記述を修正します。|
> |**名前**:<br />MemberHasAlreadyBeenContacted<br />**16 進数**:<br />8004140e<br />**数値**:<br />-2147216370|このマーケティング リスト メンバーは既にこの連絡を受けているので、このメンバーには連絡しませんでした。|
> |**名前**:<br />MergeActiveQuoteError<br />**16 進数**:<br />80045302<br />**数値**:<br />-2147200254|アクティブな見積もりを持つサブエンティティ上では統合は実行できません。|
> |**名前**:<br />MergeCyclicalParentingError<br />**16 進数**:<br />80045300<br />**数値**:<br />-2147200256|統合は上位の循環を作成できます。|
> |**名前**:<br />MergeDifferentlyParentedWarning<br />**16 進数**:<br />80045316<br />**数値**:<br />-2147200234|統合の警告: サブエンティティは別の上位を持ちます。|
> |**名前**:<br />MergeEntitiesIdenticalError<br />**16 進数**:<br />80045305<br />**数値**:<br />-2147200251|同一のマスターおよびサブエンティティ上では統合は実行できません。|
> |**名前**:<br />MergeEntityNotActiveError<br />**16 進数**:<br />80045304<br />**数値**:<br />-2147200252|非アクティブなエンティティ上では統合は実行できません。|
> |**名前**:<br />MergeLossOfParentingWarning<br />**16 進数**:<br />80045317<br />**数値**:<br />-2147200233|統合の警告: サブエンティティは上位を失った可能性があります|
> |**名前**:<br />MergeSecurityError<br />**16 進数**:<br />80045301<br />**数値**:<br />-2147200255|統合は許可されていません: 呼び出し元に特権またはアクセスがありません。|
> |**名前**:<br />MetadataNoMapping<br />**16 進数**:<br />80040e01<br />**数値**:<br />-2147217919|指定されたエンティティ間のマッピングが存在しません|
> |**名前**:<br />MetadataNotFound<br />**16 進数**:<br />8004024a<br />**数値**:<br />-2147220918|メタデータが見つかりません。|
> |**名前**:<br />MetadataNotSerializable<br />**16 進数**:<br />80040e03<br />**数値**:<br />-2147217917|指定されたメタデータ エンティティはシリアル化に対応していません|
> |**名前**:<br />MetadataRecordNotDeletable<br />**16 進数**:<br />80044250<br />**数値**:<br />-2147204528|削除されているメタデータ レコードはエンド ユーザーによって削除できません|
> |**名前**:<br />MetadataSyncRequired<br />**16 進数**:<br />80072510<br />**数値**:<br />-2147015408|必要なメタデータ同期|
> |**名前**:<br />MetricEntityOrFieldDeleted<br />**16 進数**:<br />8004F687<br />**数値**:<br />-2147158393|目標の指標で参照されているエンティティまたはフィールドが無効です|
> |**名前**:<br />MetricNameAlreadyExists<br />**16 進数**:<br />80044802<br />**数値**:<br />-2147203070|同じ名前の目標指標が既に存在します。 異なる名前を指定して、やり直してください。|
> |**名前**:<br />MinMaxValidationFailed<br />**16 進数**:<br />80061004<br />**数値**:<br />-2147086332|指定できる値の範囲を超えています。|
> |**名前**:<br />MissingBOWFRules<br />**16 進数**:<br />80040329<br />**数値**:<br />-2147220695|ワークフロー ルールに関連する一括操作が見つかりません。|
> |**名前**:<br />MissingBusinessId<br />**16 進数**:<br />8004021a<br />**数値**:<br />-2147220966|事業 ID が見つからないか、無効です。|
> |**名前**:<br />MissingColumn<br />**16 進数**:<br />8004B028<br />**数値**:<br />-2147176408|プロパティ バッグには、{0}のエントリがありません。|
> |**名前**:<br />MissingControlStep<br />**16 進数**:<br />80060385<br />**数値**:<br />-2147089531|必要なコントロールのステップがありません。|
> |**名前**:<br />MissingCrmAuthenticationToken<br />**16 進数**:<br />80044300<br />**数値**:<br />-2147204352|CrmAuthenticationToken がありません。|
> |**名前**:<br />MissingCrmAuthenticationTokenOrganizationName<br />**16 進数**:<br />80044308<br />**数値**:<br />-2147204344|組織名は CrmAuthenticationToken で指定してください。|
> |**名前**:<br />MissingHierarchicalRelationshipForOperator<br />**16 進数**:<br />80047020<br />**数値**:<br />-2147192800|このクエリは階層演算子を使用していますが、{0} エンティティには階層関係がありません。|
> |**名前**:<br />MissingOpportunityId<br />**16 進数**:<br />80043b15<br />**数値**:<br />-2147206379|営業案件 ID が見つからないか、無効です。|
> |**名前**:<br />MissingOrganizationFriendlyName<br />**16 進数**:<br />8004B00A<br />**数値**:<br />-2147176438|組織のフレンドリ名なしで Dynamics 365 をインストールすることはできません。|
> |**名前**:<br />MissingOrganizationUniqueName<br />**16 進数**:<br />8004B00B<br />**数値**:<br />-2147176437|組織の一意の名前なしで Dynamics 365 をインストールすることはできません。|
> |**名前**:<br />MissingOrInvalidRedirectId<br />**16 進数**:<br />80048473<br />**数値**:<br />-2147187597|パートナー リダイレクトの RedirId パラメータが見つかりません。|
> |**名前**:<br />MissingOwner<br />**16 進数**:<br />80040215<br />**数値**:<br />-2147220971|アイテムに所有者がありません。|
> |**名前**:<br />MissingParameter<br />**16 進数**:<br />8004031f<br />**数値**:<br />-2147220705|一括操作には必須パラメーターがありません|
> |**名前**:<br />MissingParameterToMethod<br />**16 進数**:<br />8004B021<br />**数値**:<br />-2147176415|パラメーター {0} が メソッド {1} に指定されていません|
> |**名前**:<br />MissingParameterToStoredProcedure<br />**16 進数**:<br />8004C000<br />**数値**:<br />-2147172352|パラメーターがストアド プロシージャ  {0} に指定されていません。|
> |**名前**:<br />MissingPriceLevelId<br />**16 進数**:<br />80043b12<br />**数値**:<br />-2147206382|価格レベル ID がありません。|
> |**名前**:<br />MissingProductId<br />**16 進数**:<br />80043b11<br />**数値**:<br />-2147206383|製品 ID がありません。|
> |**名前**:<br />MissingQuantity<br />**16 進数**:<br />80081012<br />**数値**:<br />-2146955246|数量がありません。|
> |**名前**:<br />MissingQueryType<br />**16 進数**:<br />80040235<br />**数値**:<br />-2147220939|クエリの種類がありません。|
> |**名前**:<br />MissingRecipient<br />**16 進数**:<br />8004350d<br />**数値**:<br />-2147207923|FAX を送信するには、受信者を指定する必要があります。|
> |**名前**:<br />MissingRequiredAttributes<br />**16 進数**:<br />80061037<br />**数値**:<br />-2147086281|regardingobjectid、データ型、または名前属性が見つからないため、プロパティは作成または更新できませんでした。|
> |**名前**:<br />MissingRequiredComponentAttributes<br />**16 進数**:<br />80072002<br />**数値**:<br />-2147016702|必須属性を Null にできません。 属性: {0}|
> |**名前**:<br />MissingTeamName<br />**16 進数**:<br />80041d0b<br />**数値**:<br />-2147214069|チーム名が想定に反して不足しています。|
> |**名前**:<br />MissingUomId<br />**16 進数**:<br />80043b0d<br />**数値**:<br />-2147206387|ユニット ID がありません。|
> |**名前**:<br />MissingUomScheduleId<br />**16 進数**:<br />80043b0a<br />**数値**:<br />-2147206390|出荷単位スケジュール ID がありません。|
> |**名前**:<br />MissingUserId<br />**16 進数**:<br />8004021b<br />**数値**:<br />-2147220965|ユーザー ID またはチーム ID がありません。|
> |**名前**:<br />MissingWebToLeadRedirect<br />**16 進数**:<br />80048477<br />**数値**:<br />-2147187593|redirectto は web2lead リダイレクトに対して見つかりません。|
> |**名前**:<br />MobileClientLanguageNotSupported<br />**16 進数**:<br />8005F201<br />**数値**:<br />-2147094015|アプリケーションはサーバーでサポートされている言語を見つけることができませんでした。 サポート対象の言語を有効にするため、管理者にお問い合わせください|
> |**名前**:<br />MobileClientNotConfiguredForCurrentUser<br />**16 進数**:<br />8005F20E<br />**数値**:<br />-2147094002|このアクションをやり直してください。 問題が解決しない場合は、ソリューションの {0} を確認するか、{#Brand_CRM} 管理者に問い合わせてください。 それでも解決しない場合には {1}に問い合わせてください。|
> |**名前**:<br />MobileClientVersionNotSupported<br />**16 進数**:<br />8005F202<br />**数値**:<br />-2147094014|モバイル クライアント バージョンはサポートされていません|
> |**名前**:<br />MobileExcelFeatureNotEnabled<br />**16 進数**:<br />800608CA<br />**数値**:<br />-2147088182|Excel へのモバイル エクスポート機能が有効になっていません|
> |**名前**:<br />MobileOfflineDaysSinceRecordLastModifiedZero<br />**16 進数**:<br />80060990<br />**数値**:<br />-2147087984|日数の値が 0 の場合、Mobile offline モードでレコードは使用できません。|
> |**名前**:<br />MobileOfflineProfileItemNameAlreadyExists<br />**16 進数**:<br />800609A8<br />**数値**:<br />-2147087960|この名前の Mobile Offline プロファイル項目は、この Mobile Offline プロファイルに既に存在します。 一意の名前を入力します。|
> |**名前**:<br />MobileOfflineProfileItemNameCanNotBeNullOrEmpty<br />**16 進数**:<br />800609AA<br />**数値**:<br />-2147087958|Mobile offline プロフィールの項目名は null または空にできません。 このプロファイル項目の名前を入力します。|
> |**名前**:<br />MobileOfflineProfileNameAlreadyExists<br />**16 進数**:<br />800609A7<br />**数値**:<br />-2147087961|この名前の Mobile Offline プロファイルは既に存在します。 一意の名前を入力します。|
> |**名前**:<br />MobileOfflineProfileNameCanNotBeNullOrEmpty<br />**16 進数**:<br />800609A9<br />**数値**:<br />-2147087959|Mobile offline プロフィール名は null または空にできません。 このプロファイルの名前を入力します。|
> |**名前**:<br />MobileOfflineRuleEnhancementFeatureNotAvailaible<br />**16 進数**:<br />80071117<br />**数値**:<br />-2147020521|この機能は組織に対して有効になっていません。 詳しい情報についてはシステム管理者にお問い合わせください。|
> |**名前**:<br />MobileServiceError<br />**16 進数**:<br />8004B070<br />**数値**:<br />-2147176336|モバイル サービスと通信する際のエラー|
> |**名前**:<br />ModernFlowProcessesNotEnabled<br />**16 進数**:<br />80060464<br />**数値**:<br />-2147089308|モダン フロー プロセスの作成が有効になっていません。|
> |**名前**:<br />ModernFlowProcessesOnlyAvailableOnline<br />**16 進数**:<br />80060465<br />**数値**:<br />-2147089307|モダン フロー プロセスの作成はオンラインでのみ利用可能です。|
> |**名前**:<br />MoneySizeExceeded<br />**16 進数**:<br />80040317<br />**数値**:<br />-2147220713|指定された値は、金額型のフィールドの最小/最大値を超えています。|
> |**名前**:<br />MOPIAssociationNameCannotBeEmptyOrSpace<br />**16 進数**:<br />80060997<br />**数値**:<br />-2147087977|Mobile Offline プロファイル項目の関連付けの名前は、スペースや空の文字列にすることはできません。|
> |**名前**:<br />MoveBothToPrimary<br />**16 進数**:<br />8004D234<br />**数値**:<br />-2147167692|移動操作は両方のインスタンスを同じサーバー上に入力します:  データベース = {0}  古いプライマリー= {1}  古い予備 = {2}  新しい予備 = {3}|
> |**名前**:<br />MoveBothToSecondary<br />**16 進数**:<br />8004D235<br />**数値**:<br />-2147167691|移動操作は両方のインスタンスを同じサーバー上に入力します:  データベース = {0}  古いプライマリー= {1}  古い予備 = {2}  新しい予備 = {3}|
> |**名前**:<br />MoveOrganizationFailedNotDisabled<br />**16 進数**:<br />8004D236<br />**数値**:<br />-2147167690|組織 {0} が無効ではないので移動操作が失敗しました|
> |**名前**:<br />MultilevelParentChildRelationshipNotAllowed<br />**16 進数**:<br />8003F453<br />**数値**:<br />-2147224493|子サポート案件を既存の子サポート案件に関連付けることはできません。|
> |**名前**:<br />MultipleChartAreasFound<br />**16 進数**:<br />8004E008<br />**数値**:<br />-2147164152|複数のグラフ エリアはサポートされていません。|
> |**名前**:<br />MultipleChildPicklist<br />**16 進数**:<br />80040250<br />**数値**:<br />-2147220912|CRM 内部例外: 複数の childAttribute を持つ候補リストはサポートされていません。|
> |**名前**:<br />MultipleFilesFound<br />**16 進数**:<br />80048439<br />**数値**:<br />-2147187655|添付ファイルの名前が一意ではありません。|
> |**名前**:<br />MultipleFormElementsFound<br />**16 進数**:<br />8004E304<br />**数値**:<br />-2147163388|ダッシュボード フォーム XML は、1 つのフォーム要素のみ含めることができます。|
> |**名前**:<br />MultipleLabelsInUserDashboard<br />**16 進数**:<br />8004E30D<br />**数値**:<br />-2147163379|ユーザー ダッシュボードでは、フォーム要素に最大 1 つのラベルを含めることができます。|
> |**名前**:<br />MultipleMeasureCollectionsFound<br />**16 進数**:<br />8004E01C<br />**数値**:<br />-2147164132|複数のメジャー コレクションはサブカテゴリを含むグラフ、つまり比較グラフはサポートされません。|
> |**名前**:<br />MultipleMeasuresFound<br />**16 進数**:<br />8004E007<br />**数値**:<br />-2147164153|複数のメジャーはサブカテゴリを含むグラフ、つまり比較グラフはサポートされません。|
> |**名前**:<br />MultipleOrganizationsNotAllowed<br />**16 進数**:<br />80041d35<br />**数値**:<br />-2147214027|1 つの組織、および 1 つのルート部署のみ使用できます。|
> |**名前**:<br />MultipleParentReportsFound<br />**16 進数**:<br />80040485<br />**数値**:<br />-2147220347|複数のレポート リンクが見つかりました。 各レポートは、1 つの親のみ持つことができます。|
> |**名前**:<br />MultipleParentsNotSupported<br />**16 進数**:<br />80047007<br />**数値**:<br />-2147192825|エンティティの上位関係は 1 つのみです|
> |**名前**:<br />MultiplePartnerSecurityRoleWithSameInformation<br />**16 進数**:<br />8004A10a<br />**数値**:<br />-2147180278|複数のセキュリティ ロールがパートナーのユーザに対して見つかりました。|
> |**名前**:<br />MultiplePartnerUserWithSameInformation<br />**16 進数**:<br />8004A10b<br />**数値**:<br />-2147180277|同じ情報が含まれる複数のパートナーのユーザーが見つかりました|
> |**名前**:<br />MultipleQueueItemsFound<br />**16 進数**:<br />80040525<br />**数値**:<br />-2147220187|このアイテムは複数のキューに登録されているため、このリストからルーティングすることはできません。 いずれかのキュー内でこのアイテムを選択してから、ルーティング操作をやり直してください。|
> |**名前**:<br />MultipleRecordsFoundByEntityKey<br />**16 進数**:<br />8006089D<br />**数値**:<br />-2147088227|属性 {1} を含むエンティティ キーを持つエンティティ {0} のレコードが複数存在します|
> |**名前**:<br />MultipleRelationshipsNotSupported<br />**16 進数**:<br />80048200<br />**数値**:<br />-2147188224|複数の関連付けはサポートされていません。|
> |**名前**:<br />MultipleRootBusinessUnit<br />**16 進数**:<br />8004A10c<br />**数値**:<br />-2147180276|複数のルート部署が見つかりました。|
> |**名前**:<br />MultipleSitemapsFound<br />**16 進数**:<br />80050120<br />**数値**:<br />-2147155680|1 つのみと予想される {0} 未公開のサイト マップが見つかりました|
> |**名前**:<br />MultipleSubcategoriesFound<br />**16 進数**:<br />8004E006<br />**数値**:<br />-2147164154|ビジュアル化のデータ XML に Group By 句を 2つ以上含めることはできません。|
> |**名前**:<br />MultiValueParameterFound<br />**16 進数**:<br />8005E00A<br />**数値**:<br />-2147098614|Fetch XML パラメーター {0} は、複数の値を取得することはできません。 レポートのパラメーター {0} を、単一のパラメーター値に変更して再試行します。|
> |**名前**:<br />MustContainAtLeastACharInMention<br />**16 進数**:<br />8004F6A4<br />**数値**:<br />-2147158364|表示名には空白以外の文字が 1 つ以上含まれている必要があります。|
> |**名前**:<br />NavigationPropertyAlreadyExists<br />**16 進数**:<br />80072551<br />**数値**:<br />-2147015343|NavigationPropertyName {0} がエンティティ内で一意ではありません|
> |**名前**:<br />NavigationPropertyNameCannotBeTheSameOnBothSidesOfRel<br />**16 進数**:<br />80072550<br />**数値**:<br />-2147015344|自己参照の関連付けの両側でナビゲーション プロパティの名前を同じにできません。 SchemaName - {0}|
> |**名前**:<br />NavPaneNotCustomizable<br />**16 進数**:<br />80044329<br />**数値**:<br />-2147204311|この関係のナビゲーション ウィンドウ プロパティはカスタマイズ可能ではありません|
> |**名前**:<br />NavPaneOrderValueNotAllowed<br />**16 進数**:<br />80044327<br />**数値**:<br />-2147204313|提供されたナビゲーション ウィンドウの順序値は許可されていません|
> |**名前**:<br />NetworkIssue<br />**16 進数**:<br />8005F104<br />**数値**:<br />-2147094268|不明なネットワークの問題、ゲートウェイの問題またはサーバーの問題により、要求が失敗しました。|
> |**名前**:<br />NewStatusHasInvalidState<br />**16 進数**:<br />80044322<br />**数値**:<br />-2147204318|この新しい状態オプションの状態値はこれ以上ありません。|
> |**名前**:<br />NewStatusRequiresAssociatedState<br />**16 進数**:<br />80044321<br />**数値**:<br />-2147204319|新しい状態オプションには、関連した状態値が必要です。|
> |**名前**:<br />NoActiveLocation<br />**16 進数**:<br />80060900<br />**数値**:<br />-2147088128|アクティブな場所が見つかりません。|
> |**名前**:<br />NoAppModuleComponentReferred<br />**16 進数**:<br />8005011B<br />**数値**:<br />-2147155685|コンポーネントが参照されていません|
> |**名前**:<br />NoAttributesForEntityCreate<br />**16 進数**:<br />80047014<br />**数値**:<br />-2147192812|エンティティ アクションに属性はありません。|
> |**名前**:<br />NoConditionRuleCreationNotAllowedForSetValueShowError<br />**16 進数**:<br />80060013<br />**数値**:<br />-2147090413|"エラー メッセージの表示" および "値の設定" の操作は、条件が設定されていない業務ルールでは使用できません。|
> |**名前**:<br />NoConnectionRoleAndObjectTypeCodePairPresent<br />**16 進数**:<br />8004F222<br />**数値**:<br />-2147159518|ConnectionRoleId と AssociatedObjectTypeCode のペアが存在しません。 接続中のエンティティ: ({0},{1}); 接続中のエンティティ レコード: ({2},{3}); Record1ConnectionRoleName: {4}、Record2ConnectionRoleName: {5}。 ConnectionRoleIds : {6}|
> |**名前**:<br />NoConversionRule<br />**16 進数**:<br />800608F5<br />**数値**:<br />-2147088139|ツールを実行するには ConversionRule が必要です。|
> |**名前**:<br />NoDataFilterSelectedForOtherDataFilter<br />**16 進数**:<br />80071138<br />**数値**:<br />-2147020488|プロファイル '{1}' のエンティティ '{0}' にデータ ダウンロード フィルター 'その他のデータ フィルター' が含まれていますが、データ フィルター オプションが選択されていません。 エンティティはデータ フィルター オプションを指定する必要があります。|
> |**名前**:<br />NoDataForVisualization<br />**16 進数**:<br />8004E011<br />**数値**:<br />-2147164143|このビジュアル化を作成するためのデータがありません。|
> |**名前**:<br />NoDefaultValueForOptionSetArgument<br />**16 進数**:<br />80060396<br />**数値**:<br />-2147089514|種類が OptionSet である引数には既定値が設定されている必要があります。|
> |**名前**:<br />NoDefinedRelationshipsForMOPIAssociation<br />**16 進数**:<br />80060998<br />**数値**:<br />-2147087976|プロファイル項目の関連付けエンティティに、定義済みの関係がありません。|
> |**名前**:<br />NoDialNumber<br />**16 進数**:<br />8004350f<br />**数値**:<br />-2147207921|FAX に FAX 番号が指定されていないか、宛先の FAX 番号が指定されていません。|
> |**名前**:<br />NoEntitiesForBulkDelete<br />**16 進数**:<br />80048442<br />**数値**:<br />-2147187646|削除する有効なエンティティがないため、一括削除ウィザードを開けません。|
> |**名前**:<br />NoEntitySpecified<br />**16 進数**:<br />800608FA<br />**数値**:<br />-2147088134|ツールが処理を行うには、少なくとも 1 つのエンティティが必要です。|
> |**名前**:<br />NoFilesSelected<br />**16 進数**:<br />80071021<br />**数値**:<br />-2147020767|コピーするドキュメントが選択されていません。 ドキュメントを選択してからやり直してください。|
> |**名前**:<br />NoHeaderColumnFound<br />**16 進数**:<br />80040368<br />**数値**:<br />-2147220632|列見出しがありません。|
> |**名前**:<br />NoIncidentMergeHavingSameParent<br />**16 進数**:<br />8003F450<br />**数値**:<br />-2147224496|異なる親サポート案件の関連付けを持つ子サポート案件を統合することはできません。|
> |**名前**:<br />NoLabelsAssociatedWithStep<br />**16 進数**:<br />80060408<br />**数値**:<br />-2147089400|{0} には、関連付けられているラベルがありません。|
> |**名前**:<br />NoLanguageProvisioned<br />**16 進数**:<br />80044199<br />**数値**:<br />-2147204711|この組織で使用する言語は準備されていません。|
> |**名前**:<br />NoLicenseInConfigDB<br />**16 進数**:<br />8004D241<br />**数値**:<br />-2147167679|MSCRM_CONFIG データベースにライセンスが存在しません。|
> |**名前**:<br />NoMinimumRequiredPrivilegesForTabletApp<br />**16 進数**:<br />8005F20F<br />**数値**:<br />-2147094001|このサーバーでアプリケーションを読み込むアクセス許可がありません。\n管理者に問い合わせて、アクセス許可を更新してください。|
> |**名前**:<br />NoMoreCustomOptionValuesExist<br />**16 進数**:<br />8004431F<br />**数値**:<br />-2147204321|使用可能なすべてのカスタム オプション値が使用されました。|
> |**名前**:<br />NoncompliantXml<br />**16 進数**:<br />80048425<br />**数値**:<br />-2147187675|入力 XML は、XML スキーマに準拠していません。|
> |**名前**:<br />NonCrmUIInteractiveWorkflowNotSupported<br />**16 進数**:<br />80045044<br />**数値**:<br />-2147200956|Microsoft Dynamics 365 Web アプリケーションの外部で作成されているため、この対話型ワークフローを作成、更新、または公開できません。|
> |**名前**:<br />NonCrmUIWorkflowsNotSupported<br />**16 進数**:<br />80045040<br />**数値**:<br />-2147200960|Microsoft Dynamics 365 Web アプリケーションの外部で作成されているため、このワークフローを作成、更新、または公開できません。 この組織では、この種類のワークフローは使用できません。|
> |**名前**:<br />NonDraftBundleUpdate<br />**16 進数**:<br />80061039<br />**数値**:<br />-2147086279|バンドルが無効な状態の場合は製品の関連付けを更新できません。|
> |**名前**:<br />NonInteractiveUserCannotAccessUI<br />**16 進数**:<br />80044160<br />**数値**:<br />-2147204768|非対話型ユーザーは、 Web ユーザー インターフェイスにアクセスできません。 組織のシステム管理者に問い合わせてください。|
> |**名前**:<br />NonMappableEntity<br />**16 進数**:<br />80046200<br />**数値**:<br />-2147196416|NonMappableEntity エラーが発生しました。|
> |**名前**:<br />NonPrimaryEntityDataDescriptionFound<br />**16 進数**:<br />8004E001<br />**数値**:<br />-2147164159|ビジュアル化のデータ記述が無効です。ビジュアル化のデータ記述は、ビューの主エンティティまたはリンクされたエンティティの属性のみ持つことができます。|
> |**名前**:<br />NoOutputTransformationParameterMappingFound<br />**16 進数**:<br />80040384<br />**数値**:<br />-2147220604|定義された変換パラメーター マッピング出力がありません。 変換マッピングは、少なくとも 1 つの出力変換パラメーター マッピングが必要です。|
> |**名前**:<br />NoPreviewForCustomWebResource<br />**16 進数**:<br />8004E020<br />**数値**:<br />-2147164128|このグラフはカスタムの Web リソースを使用しています。 このグラフをプレビューすることはできません。|
> |**名前**:<br />NoPrivilegeToApplyManualSLA<br />**16 進数**:<br />80055002<br />**数値**:<br />-2147135486|このサポート案件レコードにサービス レベル アグリーメント (SLA) を適用するための適切なアクセス許可がありません。|
> |**名前**:<br />NoPrivilegeToPublishWorkflow<br />**16 進数**:<br />80045016<br />**数値**:<br />-2147201002|ユーザーにはワークフローを公開する十分な特権がありません。|
> |**名前**:<br />NoPrivilegeToWorker<br />**16 進数**:<br />80040521<br />**数値**:<br />-2147220191|非アクティブなキューにアイテムを追加することはできません。 別のキューを選択してから、やり直してください。|
> |**名前**:<br />NoPublishedDuplicateDetectionRules<br />**16 進数**:<br />80048436<br />**数値**:<br />-2147187658|システムに公開済みの重複データ検出ルールはありません。 重複データ検出を実行するには、1 つまたは複数のルールを作成し、公開する必要があります。|
> |**名前**:<br />NoQuickFindFound<br />**16 進数**:<br />80060203<br />**数値**:<br />-2147089917|エンティティ - {0} には、有効な簡易検索クエリの値はありませんでした。|
> |**名前**:<br />NoRollupAttributesDefined<br />**16 進数**:<br />8004F681<br />**数値**:<br />-2147158399|ロールアップの成功には、少なくとも 1 つのロールアップ属性が目標指標に関連付けられている必要があります|
> |**名前**:<br />NoSettingError<br />**16 進数**:<br />8004Ed46<br />**数値**:<br />-2147160762|[configdb] の構成設定 [{0}] が見つかりませんでした。|
> |**名前**:<br />NoSiteMapReferenceInAppModule<br />**16 進数**:<br />8005011C<br />**数値**:<br />-2147155684|アプリ モジュールにサイト マップが含まれていません|
> |**名前**:<br />NotAWellFormedXml<br />**16 進数**:<br />80048426<br />**数値**:<br />-2147187674|入力 XML は適切な形式 XML ではありません。|
> |**名前**:<br />NotEnoughPrivilegesForXamlWorkflows<br />**16 進数**:<br />80045041<br />**数値**:<br />-2147200959|操作を完了するための十分な特権がありません。 展開管理者だけが、 Microsoft Dynamics 365 Web アプリケーションの外部で作成されたワークフローの作成または更新ができます。|
> |**名前**:<br />NoTestEmailAccessPrivilege<br />**16 進数**:<br />8005E232<br />**数値**:<br />-2147098062|テスト アクセスを実行する特権がありません。|
> |**名前**:<br />NotExistArgumentInAction<br />**16 進数**:<br />80060393<br />**数値**:<br />-2147089517|引数 {0} がアクションに存在しません。|
> |**名前**:<br />NotExistBusinessProcess<br />**16 進数**:<br />80060391<br />**数値**:<br />-2147089519|ビジネス プロセスが存在しません。|
> |**名前**:<br />NoTimeZoneCodeForConversionRule<br />**16 進数**:<br />800608F9<br />**数値**:<br />-2147088135|ConversionRule プロパティの値が SpecificTimeZone である場合は、TimeZoneCode プロパティが必要です。|
> |**名前**:<br />NotImplemented<br />**16 進数**:<br />80040219<br />**数値**:<br />-2147220967|要求された機能はまだ実装されていません。|
> |**名前**:<br />NotMobileEnabled<br />**16 進数**:<br />8005F215<br />**数値**:<br />-2147093995|ご使用のタブレットでは、この種類のレコードを表示できません。 システム管理者にお問い合わせください。|
> |**名前**:<br />NotMobileWriteEnabled<br />**16 進数**:<br />8005F21c<br />**数値**:<br />-2147093988|ご使用のデバイスでは、この種類のレコードを作成できません。 システム管理者にお問い合わせください。|
> |**名前**:<br />NotSupported<br />**16 進数**:<br />80040315<br />**数値**:<br />-2147220715|この操作はサポートされていません。|
> |**名前**:<br />NotVerifiedAdmin<br />**16 進数**:<br />8005F106<br />**数値**:<br />-2147094266|このセットアップを完了するには、Yammer の企業アカウントが必要です。 Yammer 管理者アカウントを使用してサインインするか、または Yammer 管理者にサポートを依頼してください。|
> |**名前**:<br />NoUserPrivilege<br />**16 進数**:<br />80154B50<br />**数値**:<br />-2146088112|十分なアクセス許可がありません。|
> |**名前**:<br />NoWritePermission<br />**16 進数**:<br />80071023<br />**数値**:<br />-2147020765|ドキュメントをコピーするための書き込みアクセス許可がありません。|
> |**名前**:<br />NoYammerNetworksFound<br />**16 進数**:<br />8005F108<br />**数値**:<br />-2147094264|Yammer ネットワークに対する権限がありません。 Yammer 管理者アカウントを使用して Yammer のセットアップを再認証、または Yammer 管理者にサポートを依頼してください。|
> |**名前**:<br />NullArticleTemplateFormatXml<br />**16 進数**:<br />800404f8<br />**数値**:<br />-2147220232|記事テンプレート formatxml を NULL にすることはできません。|
> |**名前**:<br />NullArticleTemplateStructureXml<br />**16 進数**:<br />800404f9<br />**数値**:<br />-2147220231|記事テンプレート structurexml を NULL にすることはできません。|
> |**名前**:<br />NullArticleXml<br />**16 進数**:<br />800404f7<br />**数値**:<br />-2147220233|記事の xml を NULL にすることはできません|
> |**名前**:<br />NullDashboardName<br />**16 進数**:<br />8004E305<br />**数値**:<br />-2147163387|ダッシュボードの名前を null にすることはできません。|
> |**名前**:<br />NullKBArticleTemplateId<br />**16 進数**:<br />800404fa<br />**数値**:<br />-2147220230|kbarticletemplateid を NULL にすることはできません|
> |**名前**:<br />NullOrEmptyAttributeInXaml<br />**16 進数**:<br />80060406<br />**数値**:<br />-2147089402|属性 - {1} の {0} を null または空にすることはできません|
> |**名前**:<br />NumberFormatFailed<br />**16 進数**:<br />80040259<br />**数値**:<br />-2147220903|書式設定された数値を生成できませんでした。|
> |**名前**:<br />OAuthTokenNotFound<br />**16 進数**:<br />8005F109<br />**数値**:<br />-2147094263|Yammer OAuth トークンが見つかりません。 関連機能にアクセスする前に、Yammer を構成してください。|
> |**名前**:<br />ObjectAlreadyExists<br />**16 進数**:<br />8004E30A<br />**数値**:<br />-2147163382|ID {0} を持つオブジェクトは既に存在します。 IDを変更し、もう一度やり直してください。|
> |**名前**:<br />ObjectDoesNotExist<br />**16 進数**:<br />80040217<br />**数値**:<br />-2147220969|指定されたオブジェクトは見つかりませんでした。|
> |**名前**:<br />ObjectNotFoundInAD<br />**16 進数**:<br />80041d2a<br />**数値**:<br />-2147214038|オブジェクトは Active Directory に存在していません。|
> |**名前**:<br />ObjectNotRelatedToCampaign<br />**16 進数**:<br />8004030e<br />**数値**:<br />-2147220722|指定されたオブジェクトは上位キャンペーンに関連付けられていません|
> |**名前**:<br />OccurrenceCrossingBoundary<br />**16 進数**:<br />8004E120<br />**数値**:<br />-2147163872|2 つの発生が重複することはできません。|
> |**名前**:<br />OccurrenceSkipsOverBackward<br />**16 進数**:<br />8004E123<br />**数値**:<br />-2147163869|定期的な予定の個別の発生日をスケジュール変更する場合、同じ予定の前回の発生日以前まで早めることはできません。|
> |**名前**:<br />OccurrenceSkipsOverForward<br />**16 進数**:<br />8004E122<br />**数値**:<br />-2147163870|定期的な予定の個別の発生日をスケジュール変更する場合、同じ予定の次回の発生日以降まで遅らせることはできません。|
> |**名前**:<br />OccurrenceTimeSpanTooBig<br />**16 進数**:<br />8004E121<br />**数値**:<br />-2147163871|操作を実行できません。 インスタンスは、有効な展開範囲の系列外にあります。|
> |**名前**:<br />OfferingCategoryAndTokenNull<br />**16 進数**:<br />8004B00C<br />**数値**:<br />-2147176436|サービス カテゴリ、および請求トークンの両方が見つかりません、少なくともどちらか一つが必須です。|
> |**名前**:<br />OfferingIdNotSupported<br />**16 進数**:<br />8004B00D<br />**数値**:<br />-2147176435|このバージョンはサービス ID の検索をサポートしていません。|
> |**名前**:<br />OfficeGraphDisabledError<br />**16 進数**:<br />80044239<br />**数値**:<br />-2147204551|この組織ではドキュメント レコメンデーションが無効になっています。|
> |**名前**:<br />OfficeGraphSiteNotConfigured<br />**16 進数**:<br />80044257<br />**数値**:<br />-2147204521|既定の SharePoint サイトが構成されていません。|
> |**名前**:<br />OfficeGroupsExceptionRetrieveSetting<br />**16 進数**:<br />800610EB<br />**数値**:<br />-2147086101|RetrieveOfficeGroupsSetting で Office グループ例外が発生しました: {0}。|
> |**名前**:<br />OfficeGroupsFeatureNotEnabled<br />**16 進数**:<br />800610EA<br />**数値**:<br />-2147086102|Office グループ機能が有効になっていません。|
> |**名前**:<br />OfficeGroupsInvalidSettingType<br />**16 進数**:<br />800610EC<br />**数値**:<br />-2147086100|Office グループ機能の設定の種類が無効です: {0}。|
> |**名前**:<br />OfficeGroupsNoAuthServersFound<br />**16 進数**:<br />800610EE<br />**数値**:<br />-2147086098|Office グループ機能は認証サーバーを見つけることができませんでした。|
> |**名前**:<br />OfficeGroupsNotSupportedCall<br />**16 進数**:<br />800610ED<br />**数値**:<br />-2147086099|Office グループ機能がサポートされていない電話を試みました。|
> |**名前**:<br />OfflineFilterNestedDateTimeOR<br />**16 進数**:<br />80048450<br />**数値**:<br />-2147187632|OR 句で入れ子になった日時の条件をローカル データ グループで使用することはできません。|
> |**名前**:<br />OfflineFilterParentDownloaded<br />**16 進数**:<br />80048451<br />**数値**:<br />-2147187631|"親レコード ダウンロード済み" 条件はローカル データ グループでは使用できません。|
> |**名前**:<br />OneDriveForBusinessDisabled<br />**16 進数**:<br />80050004<br />**数値**:<br />-2147155964|以下の添付ファイルには、OneDrive for Business が必要です。 組織の OneDrive for Business を有効にするために管理者にお問い合わせください。|
> |**名前**:<br />OneDriveForBusinessLocationNotFound<br />**16 進数**:<br />80050009<br />**数値**:<br />-2147155959|OneDrive for Business のアクティブな場所が見つかりません。|
> |**名前**:<br />OneNoteCreationFailed<br />**16 進数**:<br />80060902<br />**数値**:<br />-2147088126|OneNote の作成に失敗しました。|
> |**名前**:<br />OneNoteLocationDeactivated<br />**16 進数**:<br />80060907<br />**数値**:<br />-2147088121|OneNote の場所のマッピングが非アクティブです。 管理者に問い合わせて、この Dynamics 365 レコードに対応した OneNote の場所レコードをアクティブ化してください。|
> |**名前**:<br />OneNoteLocationNotCreated<br />**16 進数**:<br />80060906<br />**数値**:<br />-2147088122|OneNote の場所が作成されません。|
> |**名前**:<br />OneNoteRenderFailed<br />**16 進数**:<br />80060903<br />**数値**:<br />-2147088125|OneNote の表示に失敗しました。|
> |**名前**:<br />OnlyDisabledOrganizationCanBeDeleted<br />**16 進数**:<br />8004B02F<br />**数値**:<br />-2147176401|有効な組織を削除できません。 組織を削除する前には、その組織を無効にする必要があります。|
> |**名前**:<br />OnlyOneSearchParameterMustBeProvided<br />**16 進数**:<br />80060206<br />**数値**:<br />-2147089914|追加のパラメーター。 EntityGroupName または EntityNames だけを指定してください。両方を指定する必要はありません。|
> |**名前**:<br />OnlyOwnerCanRevoke<br />**16 進数**:<br />80040223<br />**数値**:<br />-2147220957|そのオブジェクトの所有者のアクセスを取り消すことができるのは、オブジェクトの所有者のみです。|
> |**名前**:<br />OnlyOwnerCanSetManagedProperties<br />**16 進数**:<br />8004F031<br />**数値**:<br />-2147160015|コンポーネント {0}: {1} はインポートできません。値 {3} を持つ管理プロパティ {2} が現在の値 {4} と異なっており、インポートされているソリューション発行者が、このコンポーネントをインストールしたソリューション発行者と一致していないためです。|
> |**名前**:<br />OnlyProductCanBeConvertedToKit<br />**16 進数**:<br />80061017<br />**数値**:<br />-2147086313|製品のみをセット製品に変換できます。|
> |**名前**:<br />OnlyStepInPredefinedStagesCanBeModified<br />**16 進数**:<br />80044184<br />**数値**:<br />-2147204732|無効なプラグイン登録ステージです。 ステップを変更できるのは、BeforeMainOperationOutsideTransaction、BeforeMainOperationInsideTransaction、AfterMainOperationInsideTransaction、および AfterMainOperationOutsideTransaction 段階のみです。|
> |**名前**:<br />OnlyStepInServerOnlyCanHaveSecureConfiguration<br />**16 進数**:<br />80044185<br />**数値**:<br />-2147204731|ServerOnly がサポートされる展開を持つ SdkMessageProcessingStep のみセキュリティ保護された構成を設定できます。|
> |**名前**:<br />OnlyStepOutsideTransactionCanCreateCrmService<br />**16 進数**:<br />80044186<br />**数値**:<br />-2147204730|親パイプライン、およびトランザクションの外部のステージでは SdkMessageProcessingStep のみ、デッドロックを防ぐために CrmService を作成することができます。|
> |**名前**:<br />OnlyWorkflowDefinitionOrTemplateCanBePublished<br />**16 進数**:<br />8004500D<br />**数値**:<br />-2147201011|ワークフロー定義、または下書きワークフロー テンプレートのみ公開することができます。|
> |**名前**:<br />OnlyWorkflowDefinitionOrTemplateCanBeUnpublished<br />**16 進数**:<br />8004500E<br />**数値**:<br />-2147201010|ワークフロー定義、またはワークフロー テンプレートのみ非公開にすることができます。|
> |**名前**:<br />OnPremiseRestoreOrganizationManifestFailed<br />**16 進数**:<br />80048532<br />**数値**:<br />-2147187406|マニフェストから組織の configdb 状態を復元できませんでした|
> |**名前**:<br />OpenCrmDBConnection<br />**16 進数**:<br />8004023e<br />**数値**:<br />-2147220930|DB 接続が閉じているべき時に、開いています。|
> |**名前**:<br />OpenDocumentErrorCodeGeneric<br />**16 進数**:<br />8005F20C<br />**数値**:<br />-2147094004|このアクションをやり直してください。 問題が解決しない場合は、ソリューションの {0} を確認するか、{#Brand_CRM} 管理者に問い合わせてください。 それでも解決しない場合には {1}に問い合わせてください。|
> |**名前**:<br />OpenDocumentErrorCodeUnableToFindAnActivity<br />**16 進数**:<br />8005F20A<br />**数値**:<br />-2147094006|このアクションをやり直してください。 問題が解決しない場合は、ソリューションの {0} を確認するか、{#Brand_CRM} 管理者に問い合わせてください。 それでも解決しない場合には {1}に問い合わせてください。|
> |**名前**:<br />OpenDocumentErrorCodeUnableToFindTheDataId<br />**16 進数**:<br />8005F20B<br />**数値**:<br />-2147094005|このアクションをやり直してください。 問題が解決しない場合は、ソリューションの {0} を確認するか、{#Brand_CRM} 管理者に問い合わせてください。 それでも解決しない場合には {1}に問い合わせてください。|
> |**名前**:<br />OpenMailboxException<br />**16 進数**:<br />8005E216<br />**数値**:<br />-2147098090|Exchange 電子メール サーバーのメールボックスを開くときに例外が発生します。|
> |**名前**:<br />OperationCanBeCalledOnlyOnce<br />**16 進数**:<br />80040334<br />**数値**:<br />-2147220684|指定した操作は一度しか実行できません。|
> |**名前**:<br />OperationCanceled<br />**16 進数**:<br />80060912<br />**数値**:<br />-2147088110|更新はユーザーによって取り消されました。|
> |**名前**:<br />OperationFailedTryAgain<br />**16 進数**:<br />80154B53<br />**数値**:<br />-2146088109|現時点では操作を実行できませんでした。 やり直してください。|
> |**名前**:<br />OperationOrganizationNotFullyDisabled<br />**16 進数**:<br />8004D23a<br />**数値**:<br />-2147167686|{1} 操作は組織 {0} が完全に無効にされていないため失敗しました。  FORCE を使用して上書きする|
> |**名前**:<br />OperatorCodeNotPresentError<br />**16 進数**:<br />80044241<br />**数値**:<br />-2147204543|condition xml 内に OperatorCode が存在する必要があります。|
> |**名前**:<br />OperatorsInViewNotSupportedOffline<br />**16 進数**:<br />80071127<br />**数値**:<br />-2147020505|このビューの 1 つ以上のオペレーターはオフラインでサポートされていません。|
> |**名前**:<br />OpportunityAlreadyInOpenState<br />**16 進数**:<br />8004051a<br />**数値**:<br />-2147220198|営業案件は、既にオープン状態にあります。|
> |**名前**:<br />OpportunityCannotBeClosed<br />**16 進数**:<br />80040516<br />**数値**:<br />-2147220202|営業案件をクローズできません。|
> |**名前**:<br />OpportunityCurrencyComparisonNotPossible<br />**16 進数**:<br />80100004<br />**数値**:<br />-2146435068|営業案件を更新できません、通貨の比較を行えませんでした。|
> |**名前**:<br />OpportunityIsAlreadyClosed<br />**16 進数**:<br />80040515<br />**数値**:<br />-2147220203|営業案件は既にクローズされています。|
> |**名前**:<br />OpportunityNotFound<br />**16 進数**:<br />80100006<br />**数値**:<br />-2146435066|営業案件エンティティを更新するために取得できません。|
> |**名前**:<br />OpportunityPreImageNotFound<br />**16 進数**:<br />80100007<br />**数値**:<br />-2146435065|更新前に営業案件のプレイメージが見つかりません。|
> |**名前**:<br />OptimisticConcurrencyNotEnabled<br />**16 進数**:<br />8006088D<br />**数値**:<br />-2147088243|エンティティの種類 {0} に対して、オプティミスティック同時実行は有効になっていません。 オプティミスティック同時実行が有効の場合にのみ ConcurrencyBehavior の IfVersionMatches 値を使用することができます。|
> |**名前**:<br />OptionReorderArrayIncorrectLength<br />**16 進数**:<br />80044324<br />**数値**:<br />-2147204316|指定の並べ替えをしたオプション値の配列は、属性のオプションの数と一致しません。|
> |**名前**:<br />OptionSetValidationFailed<br />**16 進数**:<br />80061005<br />**数値**:<br />-2147086331|指定できる値の範囲を超えています。|
> |**名前**:<br />OptionValuePrefixOutOfRange<br />**16 進数**:<br />80048402<br />**数値**:<br />-2147187710|CustomizationOptionValuePrefix は {0} ～ {1} の数値にする必要があります|
> |**名前**:<br />OrganizationDisabled<br />**16 進数**:<br />8004A104<br />**数値**:<br />-2147180284|Dynamics 365 組織のアクセスは現在無効になっています。  システム管理者にお問い合わせください|
> |**名前**:<br />OrganizationMigrationUnderway<br />**16 進数**:<br />8004B044<br />**数値**:<br />-2147176380|組織の移行はすでに進行中です。|
> |**名前**:<br />OrganizationNotConfigured<br />**16 進数**:<br />8004D253<br />**数値**:<br />-2147167661|組織はまだ構成されていません。|
> |**名前**:<br />OrganizationTakenBySomeoneElse<br />**16 進数**:<br />8004B00F<br />**数値**:<br />-2147176433|組織 {0} は、他の顧客により購入済みです。|
> |**名前**:<br />OrganizationTakenByYou<br />**16 進数**:<br />8004B00E<br />**数値**:<br />-2147176434|組織 {0} は、他のユーザーにより購入済みです。|
> |**名前**:<br />OrganizationUIDeprecated<br />**16 進数**:<br />80044159<br />**数値**:<br />-2147204775|OrganizationUI エンティティは廃止されました。 SystemForm エンティティに置き換えられています。|
> |**名前**:<br />OrgDoesNotExistInDiscoveryService<br />**16 進数**:<br />8004B067<br />**数値**:<br />-2147176345|組織は顧客探索サービスで見つかりませんでした|
> |**名前**:<br />OrgIdNotDetermined<br />**16 進数**:<br />80044353<br />**数値**:<br />-2147204269|エラー。 現在の組織 ID を特定できませんでした|
> |**名前**:<br />OrgsInaccessible<br />**16 進数**:<br />8004D24A<br />**数値**:<br />-2147167670|展開内の 1 つ以上の組織にアクセスできないため、クライアント アクセス ライセンス (CAL) の結果が返されませんでした。|
> |**名前**:<br />OutgoingNotAllowedForForwardMailbox<br />**16 進数**:<br />8005E225<br />**数値**:<br />-2147098075|メールボックスは転送用メールボックスです。 転送用メールボックスはこのメールを送信することはできません。|
> |**名前**:<br />OutgoingServerLocationAndSslSetToNo<br />**16 進数**:<br />8005E23F<br />**数値**:<br />-2147098049|HTTPS を使用する送信サーバーの場所を URL で指定しましたが、[送信接続に SSL を使用する] オプションが [いいえ] に設定されています。 オプションを [はい] に設定し、やり直してください。|
> |**名前**:<br />OutgoingServerLocationAndSslSetToYes<br />**16 進数**:<br />8005E241<br />**数値**:<br />-2147098047|HTTP を使用する送信サーバーの場所を URL で指定しましたが、[送信接続に SSL を使用する] オプションが [はい] に設定されています。 HTTPS を使用するサーバーの場所を指定し、やり直してください。|
> |**名前**:<br />OutgoingSettingsUpdateNotAllowed<br />**16 進数**:<br />8005E238<br />**数値**:<br />-2147098056|"送信接続に同じ設定を使用する" フラグが [True] に設定されるため、異なる送信接続設定は指定できません。|
> |**名前**:<br />OutlookClientConfigActionFailed<br />**16 進数**:<br />80044509<br />**数値**:<br />-2147203831|Dynamics 365 Outlook クライアント構成操作が失敗しました。|
> |**名前**:<br />OutOfScopeSlug<br />**16 進数**:<br />80045050<br />**数値**:<br />-2147200944|次のダイアログ ページを表示する必要のあるデータは見つかりません。 この問題を解決するには、ダイアログの所有者、またはシステム管理者に問い合わせてください。|
> |**名前**:<br />OverlappingInstances<br />**16 進数**:<br />8004E108<br />**数値**:<br />-2147163896|繰り返しの発生が 2 回重複することはできません。|
> |**名前**:<br />OverRetrievalUpperLimitWithoutPagingCookie<br />**16 進数**:<br />8004430A<br />**数値**:<br />-2147204342|ページング Cookie を使用せず要求できるレコードの上限を超えています。 ページング Cookie は、高いページ番号を取得する場合に必要です。|
> |**名前**:<br />OwnerAttributeMissing<br />**16 進数**:<br />8006110C<br />**数値**:<br />-2147086068|所有者属性が要求に存在しません。|
> |**名前**:<br />OwnerMappingExistsWithSourceSystemUserName<br />**16 進数**:<br />80040343<br />**数値**:<br />-2147220669|データ マップには、この所有者のマッピングが既に含まれています。|
> |**名前**:<br />OwnerValueNotMapped<br />**16 進数**:<br />80040361<br />**数値**:<br />-2147220639|所有者の値がマップされていません|
> |**名前**:<br />PageNotFound<br />**16 進数**:<br />8005F21A<br />**数値**:<br />-2147093990|ページが見つかりません。 レコードが存在しないか、リンクが正しくない可能性があります。|
> |**名前**:<br />ParentBusinessDoesNotExist<br />**16 進数**:<br />80041d23<br />**数値**:<br />-2147214045|上位の部署 ID が無効です。|
> |**名前**:<br />ParentCaseNotAllowedAsAChildCase<br />**16 進数**:<br />8003F455<br />**数値**:<br />-2147224491|親サポート案件を子サポート案件として追加することはできません|
> |**名前**:<br />ParentChildMetricIdDiffers<br />**16 進数**:<br />80044905<br />**数値**:<br />-2147202811|下位目標の metricid は上位目標と同じであるべきです。|
> |**名前**:<br />ParentChildPeriodAttributesDiffer<br />**16 進数**:<br />80044906<br />**数値**:<br />-2147202810|下位目標の期間の設定は上位目標と同じであるべきです。|
> |**名前**:<br />ParentHierarchyExistProperty<br />**16 進数**:<br />8004F888<br />**数値**:<br />-2147157880|階層では、ルート ノードを除く各ノードに親が存在する必要があります。|
> |**名前**:<br />ParentReadOnly<br />**16 進数**:<br />80043b09<br />**数値**:<br />-2147206391|親は読み取り専用であり、編集することはできません。|
> |**名前**:<br />ParentRecordAlreadyExists<br />**16 進数**:<br />80048478<br />**数値**:<br />-2147187592|このレコードは既に親レコードを持っているため、追加できません。|
> |**名前**:<br />ParentReportDoesNotReferenceChild<br />**16 進数**:<br />80040486<br />**数値**:<br />-2147220346|指定した上位レポートは現在のレポートを参照していません。 SQL Reporting Services のレポートのみ親レポートを持つことができます。|
> |**名前**:<br />ParentReportLinksToSameNameChild<br />**16 進数**:<br />80040496<br />**数値**:<br />-2147220330|親レポートは同じ名前の別のレポートへすでにリンクしています。|
> |**名前**:<br />ParentReportNotSupported<br />**16 進数**:<br />80040487<br />**数値**:<br />-2147220345|親レポートは指定した種類のレポートではサポートされていません。 SQL Reporting Services のレポートのみ親レポートを持つことができます。|
> |**名前**:<br />ParentUserDoesNotExist<br />**16 進数**:<br />80041d27<br />**数値**:<br />-2147214041|上位ユーザー ID が無効です。|
> |**名前**:<br />ParseMustBeCalledBeforeTransform<br />**16 進数**:<br />80040371<br />**数値**:<br />-2147220623|解析前に変換を呼び出すことはできません。|
> |**名前**:<br />ParsingMetadataNotFound<br />**16 進数**:<br />80040367<br />**数値**:<br />-2147220633|ファイルの解析に必要なデータ (データ区切り文字、フィールド区切り文字、タイトル行など) が見つかりませんでした。|
> |**名前**:<br />PartialExpansionSettingLoadError<br />**16 進数**:<br />8004E102<br />**数値**:<br />-2147163902|構成データベースから部分展開の設定を取得できませんでした。|
> |**名前**:<br />PartialHolidayScheduleCreation<br />**16 進数**:<br />8004F873<br />**数値**:<br />-2147157901|部分的な休日スケジュールは作成できません。|
> |**名前**:<br />ParticipatingEntityDoesNotAppearInTraversedPath<br />**16 進数**:<br />80060441<br />**数値**:<br />-2147089343|業務プロセス コントロールの表示エラー。 参加エンティティは渡ったパスの一部である必要がありますが、エンティティ '{0}' はパス '{1}' に表示されません。 システム管理者にお問い合わせください。|
> |**名前**:<br />ParticipatingQueryEntityMismatch<br />**16 進数**:<br />80044909<br />**数値**:<br />-2147202807|関与クエリの entitytype は、fetchxml で指定されているエンティティと同じであるべきです。|
> |**名前**:<br />PasswordRequiredForImpersonation<br />**16 進数**:<br />8005E24E<br />**数値**:<br />-2147098034|パスワードを入力して保存し直してください|
> |**名前**:<br />PatchMissingBase<br />**16 進数**:<br />80048540<br />**数値**:<br />-2147187392|ソリューション ({1}) 用の修正プログラム ({0}) をインポートできません。このソリューションは存在しません。 操作が取り消されました。|
> |**名前**:<br />PercentageDiscountCannotHaveCurrency<br />**16 進数**:<br />80048cf1<br />**数値**:<br />-2147185423|値引きの種類がパーセンテージの場合、通貨は設定できません。|
> |**名前**:<br />PersonalReportFound<br />**16 進数**:<br />8004E309<br />**数値**:<br />-2147163383|システム ダッシュボードは、個人用レポートを含めることはできません。|
> |**名前**:<br />PickListMappingExistsForTargetValue<br />**16 進数**:<br />8004033f<br />**数値**:<br />-2147220673|このリスト値は複数回マップされます。 重複するマッピングを削除してから、もう一度このデータ マップをインポートしてください。|
> |**名前**:<br />PickListMappingExistsWithSourceValue<br />**16 進数**:<br />80040342<br />**数値**:<br />-2147220670|データ マップには、このリスト値のマッピングが既に含まれています。|
> |**名前**:<br />PicklistValueNotFound<br />**16 進数**:<br />80040393<br />**数値**:<br />-2147220589|ファイルが Microsoft Dynamics 365 に存在しないリスト値を指定しています。|
> |**名前**:<br />PicklistValueNotMapped<br />**16 進数**:<br />80040360<br />**数値**:<br />-2147220640|オプション セット値をマップできないため、レコードを処理できませんでした。|
> |**名前**:<br />PicklistValueNotUnique<br />**16 進数**:<br />80044310<br />**数値**:<br />-2147204336|候補リスト値は既に存在します。  候補リストの値は一意にする必要があります。|
> |**名前**:<br />PicklistValueOutOfRange<br />**16 進数**:<br />8004431A<br />**数値**:<br />-2147204326|候補リスト値の範囲を超えています。|
> |**名前**:<br />PingFailureErrorCode<br />**16 進数**:<br />8005F212<br />**数値**:<br />-2147093998|システムが {#Brand_CRM} サーバーに再接続できませんでした。|
> |**名前**:<br />PluginAssemblyContentSizeExceeded<br />**16 進数**:<br />8004418f<br />**数値**:<br />-2147204721|"アセンブリ コンテンツ サイズ '{0} バイト' は、分離されたプラグイン '{1} バイト' で許可された最大数値を超えています。"|
> |**名前**:<br />PluginAssemblyMustHavePublicKeyToken<br />**16 進数**:<br />8004416c<br />**数値**:<br />-2147204756|公開アセンブリは公開キー トークンが必要です。|
> |**名前**:<br />PluginDoesNotImplementCorrectInterface<br />**16 進数**:<br />8004A200<br />**数値**:<br />-2147180032|指定されたプラグインは、必要なインターフェイス Microsoft.Xrm.Sdk.IPlugin または Microsoft.Crm.Sdk.IPlugin を実装しません。|
> |**名前**:<br />PluginSecureStoreAdalAcquireToken<br />**16 進数**:<br />80091005<br />**数値**:<br />-2146889723|リソースに AcquireToken できません。|
> |**名前**:<br />PluginSecureStoreKeyVaultClient<br />**16 進数**:<br />80091000<br />**数値**:<br />-2146889728|サンドボックス ワーカー プロセス下の KeyVaultClientProvider を初期化できません|
> |**名前**:<br />PluginSecureStoreKeyVaultClientDecrypt<br />**16 進数**:<br />80091003<br />**数値**:<br />-2146889725|Key Vault を使用して暗号化解除できません|
> |**名前**:<br />PluginSecureStoreKeyVaultClientEncrypt<br />**16 進数**:<br />80091004<br />**数値**:<br />-2146889724|Key Vault を使用して暗号化できません|
> |**名前**:<br />PluginSecureStoreKeyVaultClientGetSecret<br />**16 進数**:<br />80091001<br />**数値**:<br />-2146889727|Key VaultからGetSecret できません。|
> |**名前**:<br />PluginSecureStoreKeyVaultClientSetSecret<br />**16 進数**:<br />80091002<br />**数値**:<br />-2146889726|Key Vault に SetSecret できません。|
> |**名前**:<br />PluginSecureStoreKeyVaultServiceCertFormat<br />**16 進数**:<br />8009100D<br />**数値**:<br />-2146889715|証明書は、KeyVault で Base64String として保存されません|
> |**名前**:<br />PluginSecureStoreKeyVaultServiceProviderGetData<br />**16 進数**:<br />8009100C<br />**数値**:<br />-2146889716|Key Vault に AppId / Secrets がありません。|
> |**名前**:<br />PluginSecureStoreLocalConfigStoreGetData<br />**16 進数**:<br />8009100A<br />**数値**:<br />-2146889718|LocalConfigStore からデータを取得できません。|
> |**名前**:<br />PluginSecureStoreLocalConfigStoreSetData<br />**16 進数**:<br />8009100B<br />**数値**:<br />-2146889717|LocalConfigStore にデータを設定できません。|
> |**名前**:<br />PluginSecureStoreNoFullySigned<br />**16 進数**:<br />8009100F<br />**数値**:<br />-2146889713|完全にサインされていないアセンブリ|
> |**名前**:<br />PluginSecureStoreS2SMissing<br />**16 進数**:<br />80091008<br />**数値**:<br />-2146889720|S2S 資格情報が見つかりません。|
> |**名前**:<br />PluginSecureStoreTPSAssemblyNotRegistered<br />**16 進数**:<br />80091007<br />**数値**:<br />-2146889721|アセンブリは TPS に登録されていません|
> |**名前**:<br />PluginSecureStoreTPSClient<br />**16 進数**:<br />80091009<br />**数値**:<br />-2146889719|TPS Client を作成できません|
> |**名前**:<br />PluginSecureStoreTPSKeyVaultUnconfigured<br />**16 進数**:<br />80091006<br />**数値**:<br />-2146889722|KeyVaultURI は TPS のアセンブリに構成されませんでした|
> |**名前**:<br />PluginTypeMustBeUnique<br />**16 進数**:<br />8004417C<br />**数値**:<br />-2147204740|同じアセンブリ上および同じ typename を持つ複数のプラグインの種類は使用できません。|
> |**名前**:<br />Pop3UnexpectedException<br />**16 進数**:<br />8005E215<br />**数値**:<br />-2147098091|POP3 プロトコルを使用する電子メールをポーリングする際に、例外が発生します。|
> |**名前**:<br />PowerBICannotBeSystemDashboard<br />**16 進数**:<br />800608FC<br />**数値**:<br />-2147088132|Power BI ダッシュボードはシステム ダッシュボードではありません。|
> |**名前**:<br />PowerBIDashboardControlLimitation<br />**16 進数**:<br />800608FD<br />**数値**:<br />-2147088131|Power BI ダ ッシュボードは、1 つのコントロールのみ含めることができ、そのコントロールは Power BI コントロールである必要があります。|
> |**名前**:<br />PresentParentAccountAndParentContact<br />**16 進数**:<br />80040508<br />**数値**:<br />-2147220216|取引先担当者の上司、またはそのアカウントを指定できますが、両方指定することはできません。|
> |**名前**:<br />PreviousOperationNotComplete<br />**16 進数**:<br />80048464<br />**数値**:<br />-2147187612|この操作が依存する操作は、正常に完了しませんでした。|
> |**名前**:<br />PriceLevelNameExists<br />**16 進数**:<br />80043b0f<br />**数値**:<br />-2147206385|名前が既に存在します。|
> |**名前**:<br />PriceLevelNoName<br />**16 進数**:<br />80043b0e<br />**数値**:<br />-2147206386|名前を null にすることはできません。|
> |**名前**:<br />PrimaryEntityInvalid<br />**16 進数**:<br />8004501E<br />**数値**:<br />-2147200994|無効な主エンティティです。|
> |**名前**:<br />PrimaryEntityIsNull<br />**16 進数**:<br />80060401<br />**数値**:<br />-2147089407|業務プロセス フロー カテゴリを作成中に、主エンティティを NULL にすることはできません。|
> |**名前**:<br />PrimaryNameAttributeNotFound<br />**16 進数**:<br />80044355<br />**数値**:<br />-2147204267|エンティティ: {0} の PrimaryName 属性が見つかりません|
> |**名前**:<br />PrimaryParticipatingEntityIsNotPresent<br />**16 進数**:<br />80060453<br />**数値**:<br />-2147089325|検証エラー: 主参加エンティティが存在せず、それは各ビジネス プロセスのエンティティ レコードに必要です。|
> |**名前**:<br />PrincipalPrivilegeDenied<br />**16 進数**:<br />80040231<br />**数値**:<br />-2147220943|対象ユーザーまたはチームは必要な特権を持っていません。|
> |**名前**:<br />PrivilegeCreateIsDisabledForOrganization<br />**16 進数**:<br />80040276<br />**数値**:<br />-2147220874|組織の特権の作成が無効です。|
> |**名前**:<br />PrivilegeDenied<br />**16 進数**:<br />80040220<br />**数値**:<br />-2147220960|ユーザーは必要な特権を持っていません。|
> |**名前**:<br />ProcessActionDoesNotExist<br />**16 進数**:<br />80045054<br />**数値**:<br />-2147200940|プロセス アクションが存在しません。|
> |**名前**:<br />ProcessActionIsNotActive<br />**16 進数**:<br />80045053<br />**数値**:<br />-2147200941|アクション ステップで使用するには、プロセス アクションを有効にする必要があります。|
> |**名前**:<br />ProcessActionNameIncorrect<br />**16 進数**:<br />80060379<br />**数値**:<br />-2147089543|プロセス アクション “{0}” が構成された名前: “{1}” と一致しません。 エラーが解決しない場合は、システム管理者に連絡して構成メタデータを確認してください。|
> |**名前**:<br />ProcessActionWithInvalidInputOutputParam<br />**16 進数**:<br />80045058<br />**数値**:<br />-2147200936|プロセス アクションには、サポートされないパラメーターが含まれます。 名前: {0}、種類: {1}、方向: {2}。|
> |**名前**:<br />ProcessActionWithInvalidInputParam<br />**16 進数**:<br />80045057<br />**数値**:<br />-2147200937|プロセス アクションには、アクション ステップでサポートされない入力パラメーターのフィールドが含まれます。 参照先 {0} |
> |**名前**:<br />ProcessActionWithInvalidOutputParam<br />**16 進数**:<br />80045056<br />**数値**:<br />-2147200938|プロセス アクションには、アクション ステップでサポートされない出力パラメーターのフィールドが含まれます。 参照先 {0}。|
> |**名前**:<br />ProcessActionWorkflowNotEnabledForOnDemand<br />**16 進数**:<br />80060380<br />**数値**:<br />-2147089536|アクション ステップでオンデマンド実行を使用可能にするには、プロセス アクションまたはワークフローを有効にする必要があります。|
> |**名前**:<br />ProcessEmptyBranches<br />**16 進数**:<br />80060399<br />**数値**:<br />-2147089511|このプロセスには空の分岐が含まれます。 これらの分岐を定義または削除し、もう一度やり直してください。|
> |**名前**:<br />ProcessIdDoesNotMatchBusinessProcessDefinition<br />**16 進数**:<br />80060460<br />**数値**:<br />-2147089312|検証エラー: プロセス ID がビジネス プロセスの定義と一致しません。|
> |**名前**:<br />ProcessIdIsEmpty<br />**16 進数**:<br />80060459<br />**数値**:<br />-2147089319|検証エラー: プロセス ID を空にできません。|
> |**名前**:<br />ProcessImageFailure<br />**16 進数**:<br />80072553<br />**数値**:<br />-2147015341|画像の処理中にエラーが発生しました。 理由: {0}|
> |**名前**:<br />ProcessNameContainsInvalidCharacters<br />**16 進数**:<br />80060398<br />**数値**:<br />-2147089512|ビジネス プロセス名に無効な文字が含まれています。|
> |**名前**:<br />ProcessNameIsNullOrEmpty<br />**16 進数**:<br />80060418<br />**数値**:<br />-2147089384|業務プロセス フローの名前が NULL または空です。 |
> |**名前**:<br />ProcessStageIdIsEmpty<br />**16 進数**:<br />80060461<br />**数値**:<br />-2147089311|検証エラー: 主ステージ ID を空にできません。|
> |**名前**:<br />ProductCanOnlyBeUpdatedInDraft<br />**16 進数**:<br />8004F995<br />**数値**:<br />-2147157611|製品、製品ファミリ、バンドルは、ドラフト状態でのみ更新できます。|
> |**名前**:<br />ProductCloneFailed<br />**16 進数**:<br />80061006<br />**数値**:<br />-2147086330|廃止された製品ファミリの子レコードを複製することはできません。|
> |**名前**:<br />ProductDoesNotExist<br />**16 進数**:<br />80043b24<br />**数値**:<br />-2147206364|製品は存在しません。|
> |**名前**:<br />ProductFamilyCanCreateDynamicProperty<br />**16 進数**:<br />80081007<br />**数値**:<br />-2146955257|プロパティは製品ファミリに対してのみ作成できます。|
> |**名前**:<br />ProductFamilyRootParentisLocked<br />**16 進数**:<br />8008101F<br />**数値**:<br />-2146955233|製品ファミリ ルートの親レコードが他のプロセスによってロックされています。|
> |**名前**:<br />ProductFromActiveToActiveState<br />**16 進数**:<br />8004F982<br />**数値**:<br />-2147157630|製品はすでにアクティブ状態です。|
> |**名前**:<br />ProductFromActiveToDraftState<br />**16 進数**:<br />8004F912<br />**数値**:<br />-2147157742|公開された製品をドラフト状態に設定することはできません。|
> |**名前**:<br />ProductFromDraftToDraftState<br />**16 進数**:<br />8004F981<br />**数値**:<br />-2147157631|製品はすでに下書き状態です。|
> |**名前**:<br />ProductFromDraftToRetiredState<br />**16 進数**:<br />8004F978<br />**数値**:<br />-2147157640|ドラフト状態の製品を廃止することはできません。|
> |**名前**:<br />ProductFromDraftToRevisedState<br />**16 進数**:<br />8004F913<br />**数値**:<br />-2147157741|ドラフトまたは廃止された製品を変更することはできません。|
> |**名前**:<br />ProductFromRetiredToActiveState<br />**16 進数**:<br />8004F977<br />**数値**:<br />-2147157641|廃止されたプロパティをアクティブ状態に設定することはできません。|
> |**名前**:<br />ProductFromRetiredToDraftState<br />**16 進数**:<br />8004F979<br />**数値**:<br />-2147157639|廃止状態からドラフト状態に製品の状態を移行することはできません。|
> |**名前**:<br />ProductFromRetiredToRetiredState<br />**16 進数**:<br />8004F980<br />**数値**:<br />-2147157632|製品はすでに廃止状態です。|
> |**名前**:<br />ProductHasUnretiredChild<br />**16 進数**:<br />8004F910<br />**数値**:<br />-2147157744|廃止されていない子レコードが 1 つ以上あるために、この製品ファミリは廃止できません。|
> |**名前**:<br />ProductInvalidPriceLevelPercentage<br />**16 進数**:<br />80043b0c<br />**数値**:<br />-2147206388|価格設定率は 0 以上、100,000 未満である必要があります。|
> |**名前**:<br />ProductInvalidQuantityDecimal<br />**16 進数**:<br />80043b07<br />**数値**:<br />-2147206393|数量の小数点以下の桁数が無効です。|
> |**名前**:<br />ProductInvalidUnit<br />**16 進数**:<br />80043b14<br />**数値**:<br />-2147206380|指定した出荷単位はこの製品に対して無効です。|
> |**名前**:<br />ProductKitLoopBeingCreated<br />**16 進数**:<br />80043b23<br />**数値**:<br />-2147206365|セット製品にそれ自体を追加することはできません。|
> |**名前**:<br />ProductKitLoopExists<br />**16 進数**:<br />80043b22<br />**数値**:<br />-2147206366|キットの階層にループが存在します。|
> |**名前**:<br />ProductMaxPropertyLimitExceeded<br />**16 進数**:<br />8008100D<br />**数値**:<br />-2146955251|この製品はプロパティが多すぎるため公開できません。 該当組織の製品には、{0} 個を超えるプロパティを設定できません。|
> |**名前**:<br />ProductMissingUomSheduleId<br />**16 進数**:<br />80043b13<br />**数値**:<br />-2147206381|製品の出荷単位スケジュール ID がありません。|
> |**名前**:<br />ProductNoProductNumber<br />**16 進数**:<br />80043b05<br />**数値**:<br />-2147206395|製品番号を null にすることはできません。|
> |**名前**:<br />ProductNoSubstitutedProductNumber<br />**16 進数**:<br />8004F990<br />**数値**:<br />-2147157616|置換する製品番号を NULL にすることはできません。|
> |**名前**:<br />ProductOrBundleCannotBeAsParent<br />**16 進数**:<br />8004F973<br />**数値**:<br />-2147157645|製品ファミリのみ製品の親になることができます。|
> |**名前**:<br />ProductProductNumberExists<br />**16 進数**:<br />80043b06<br />**数値**:<br />-2147206394|指定した製品 ID が既存のレコードの製品 ID と競合しています。 異なる製品 ID を指定して、やり直してください。|
> |**名前**:<br />ProductRecommendationsFeatureNotEnabled<br />**16 進数**:<br />80061600<br />**数値**:<br />-2147084800|製品推奨機能が有効になっていません。|
> |**名前**:<br />ProfileContainsCircularReference<br />**16 進数**:<br />80071141<br />**数値**:<br />-2147020479|プロファイル '{0}' にデータのダウンロードを妨げる循環参照があります。 循環参照チェーン: {1} を確認して、循環参照の原因であるプロファイル項目の関連付けを削除してください。|
> |**名前**:<br />ProfileContainsRelationshipWithoutEntity<br />**16 進数**:<br />80071142<br />**数値**:<br />-2147020478|プロファイル '{0}' に、{2} に対するプロファイル項目の関連付けを含むプロファイル項目 {1} がありますが、{2} のプロファイル項目は存在しません。 プロフィール項目を含めて公開してください。|
> |**名前**:<br />ProfileCountUserLimitExceeded<br />**16 進数**:<br />80071134<br />**数値**:<br />-2147020492|このプロファイルのユーザーの合計 ('{0}') が、許可された制限 ('{1}') を超えています。 サポートされる制限内にユーザーの総数を制限してください。|
> |**名前**:<br />ProfileRuleActivateDeactivateByNonOwner<br />**16 進数**:<br />80061102<br />**数値**:<br />-2147086078|このプロファイル ルールをアクティブ化または非アクティブ化できるのは所有者だけです。|
> |**名前**:<br />ProfileRuleMissingRuleCriteria<br />**16 進数**:<br />80061100<br />**数値**:<br />-2147086080|ルール アイテムで不足しているルール条件情報を解決しないと、このルールはアクティブ化できません。|
> |**名前**:<br />ProfileRulePublishedByOwner<br />**16 進数**:<br />80061103<br />**数値**:<br />-2147086077|現在のアクティブな規則が非アクティブ化されるまで規則をアクティブ化できません。 アクティブなルールは、ルール所有者によってのみ非アクティブ化することができます。|
> |**名前**:<br />ProfileRuleWorkflowAuthorGenericError<br />**16 進数**:<br />80061101<br />**数値**:<br />-2147086079|ワークフロー作成中にエラーが発生しました。 ワークフロー定義を修正してから、やり直してください。|
> |**名前**:<br />ProvisioningNotCompleted<br />**16 進数**:<br />80091044<br />**数値**:<br />-2146889660|自動取り込みを有効にするには、リレーションシップ インサイトの設定で Cortana Intelligence Customer Insights を設定する必要があります。|
> |**名前**:<br />ProvisionRIAccessNotAllowed<br />**16 進数**:<br />80044270<br />**数値**:<br />-2147204496|組織に対してリレーションシップ インサイトを有効にするには、システム管理者特権が必要です。|
> |**名前**:<br />PublishArticle_TranslationWithMoreThanOneApprovedVersion<br />**16 進数**:<br />80061401<br />**数値**:<br />-2147085311|言語 "{0}" の承認済みバージョンが複数あります。 公開できるバージョンは 1 言語につき 1 つのみです。|
> |**名前**:<br />PublishedWorkflowLimitForSkuReached<br />**16 進数**:<br />80045015<br />**数値**:<br />-2147201003|組織で同時に公開できるワークフローの最大数に到達しているため、このワークフローは公開できません。 (ドラフト ワークフローの数には制限がありません。) 別のワークフローを非公開にしたり、またはライセンスを複数のワークフローをサポートするライセンスにアップグレードすることにより、このワークフローを公開できます。|
> |**名前**:<br />PublishedWorkflowOwnershipChange<br />**16 進数**:<br />8004500C<br />**数値**:<br />-2147201012|公開されているワークフローは、呼び出し元のみに割り当てることができます。|
> |**名前**:<br />PublishWorkflowWhileActingOnBehalfOfAnotherUserError<br />**16 進数**:<br />80045032<br />**数値**:<br />-2147200974|別のユーザーに代わって実行している間はワークフローの公開は許可されていません。|
> |**名前**:<br />PublishWorkflowWhileImpersonatingError<br />**16 進数**:<br />80045039<br />**数値**:<br />-2147200967|別のユーザーに偽装している間はワークフローの公開は許可されていません。|
> |**名前**:<br />QuantityReadonly<br />**16 進数**:<br />80043b18<br />**数値**:<br />-2147206376|標準出荷単位を更新するときに、[数量] フィールドは変更しないでください。|
> |**名前**:<br />QueriesForDifferentEntities<br />**16 進数**:<br />8004D2B0<br />**数値**:<br />-2147167568|内部および外部クエリは、同じエンティティにある必要があります。|
> |**名前**:<br />QueryBuilderAlias_Does_Not_Exist<br />**16 進数**:<br />8004110a<br />**数値**:<br />-2147217142|条件内で特定のエンティティに対する指定されたエイリアスが存在しません。|
> |**名前**:<br />QueryBuilderAliasNotAllowedForNonAggregateOrderBy<br />**16 進数**:<br />80041132<br />**数値**:<br />-2147217102|エイリアスは、非集計クエリの句の受注に対して指定することはできません。 属性を使用します。|
> |**名前**:<br />QueryBuilderAliasRequiredForAggregateOrderBy<br />**16 進数**:<br />80041134<br />**数値**:<br />-2147217100|エイリアスは、集計クエリの句の受注に対して必要です。|
> |**名前**:<br />QueryBuilderAttribute_With_Aggregate<br />**16 進数**:<br />80041107<br />**数値**:<br />-2147217145|属性は、集計操作が指定されている場合返すことはできません。|
> |**名前**:<br />QueryBuilderAttributeCannotBeGroupByAndAggregate<br />**16 進数**:<br />80041137<br />**数値**:<br />-2147217097|属性は、集計またはグループ化のどちらかで、両方ではありません|
> |**名前**:<br />QueryBuilderAttributeNotAllowedForAggregateOrderBy<br />**16 進数**:<br />80041131<br />**数値**:<br />-2147217103|属性は、集計クエリの句の受注に対して指定することはできません。 エイリアスを使用します。|
> |**名前**:<br />QueryBuilderAttributeNotFound<br />**16 進数**:<br />8004111e<br />**数値**:<br />-2147217122|必須属性が指定されていません。|
> |**名前**:<br />QueryBuilderAttributePairMismatch<br />**16 進数**:<br />80041111<br />**数値**:<br />-2147217135|AttributeFrom および AttributeTo は両方とも指定されているか、または両方とも省略されているかのどちらかです。|
> |**名前**:<br />QueryBuilderAttributeRequiredForNonAggregateOrderBy<br />**16 進数**:<br />80041133<br />**数値**:<br />-2147217101|属性は、非集計クエリの句の受注に対して必要です。|
> |**名前**:<br />QueryBuilderBad_Condition<br />**16 進数**:<br />80041106<br />**数値**:<br />-2147217146|フィルター条件または条件が正しくありません。|
> |**名前**:<br />QueryBuilderByAttributeMismatch<br />**16 進数**:<br />8004110f<br />**数値**:<br />-2147217137|QueryByAttribute は、属性の配列のように、同じ要素数を持つ空でない値の配列を指定する必要があります|
> |**名前**:<br />QueryBuilderByAttributeNonEmpty<br />**16 進数**:<br />80041110<br />**数値**:<br />-2147217136|QueryByAttribute は空でない属性の配列を指定する必要があります。|
> |**名前**:<br />QueryBuilderColumnSetVersionMissing<br />**16 進数**:<br />80041113<br />**数値**:<br />-2147217133|指定された列セット バージョンは無効です。|
> |**名前**:<br />QueryBuilderDeserializeEmptyXml<br />**16 進数**:<br />80041124<br />**数値**:<br />-2147217116|Xml 文字列を null にすることはできません。|
> |**名前**:<br />QueryBuilderDeserializeInvalidAggregate<br />**16 進数**:<br />8004111a<br />**数値**:<br />-2147217126|クエリで集計の処理中にエラーが発生しました|
> |**名前**:<br />QueryBuilderDeserializeInvalidDescending<br />**16 進数**:<br />80041119<br />**数値**:<br />-2147217127|降順の属性に有効な値は、'true'、'false'、'1'、および '0' です。|
> |**名前**:<br />QueryBuilderDeserializeInvalidDistinct<br />**16 進数**:<br />80041115<br />**数値**:<br />-2147217131|個別の属性に有効な値は、'true'、'false'、'1'、および '0' です。|
> |**名前**:<br />QueryBuilderDeserializeInvalidGetMinActiveRowVersion<br />**16 進数**:<br />8004111b<br />**数値**:<br />-2147217125|GetMinActiveRowVersion の属性に有効な値は、'true'、'false'、'1'、および '0' です。|
> |**名前**:<br />QueryBuilderDeserializeInvalidGroupBy<br />**16 進数**:<br />8004112E<br />**数値**:<br />-2147217106|グループ化属性に有効な値は、'true'、'false'、'1'、および '0' です。|
> |**名前**:<br />QueryBuilderDeserializeInvalidLinkType<br />**16 進数**:<br />80041117<br />**数値**:<br />-2147217129|リンクの種類の属性に有効な値は、'自然'、'内部'、'in'、'存在'、'matchfirstrowusingcrossapply'、'外部' です。|
> |**名前**:<br />QueryBuilderDeserializeInvalidMapping<br />**16 進数**:<br />80041116<br />**数値**:<br />-2147217130|マッピングに有効な値は、'論理' または '内部' で、それは削除されました。|
> |**名前**:<br />QueryBuilderDeserializeInvalidNode<br />**16 進数**:<br />8004111c<br />**数値**:<br />-2147217124|検出された要素ノードは無効です。|
> |**名前**:<br />QueryBuilderDeserializeInvalidNoLock<br />**16 進数**:<br />80041118<br />**数値**:<br />-2147217128|ロックされていない属性に有効な値は、'true'、'false'、'1'、および '0' です。|
> |**名前**:<br />QueryBuilderDeserializeInvalidUseRawOrderBy<br />**16 進数**:<br />800410fd<br />**数値**:<br />-2147217155|useraworderby の属性に有効な値は、'true'、'false'、'1'、および '0' です。|
> |**名前**:<br />QueryBuilderDeserializeInvalidUtcOffset<br />**16 進数**:<br />8004111d<br />**数値**:<br />-2147217123|utc-offset 属性は、逆シリアル化をサポートしていません。|
> |**名前**:<br />QueryBuilderDeserializeNoDocElemXml<br />**16 進数**:<br />80041125<br />**数値**:<br />-2147217115|ドキュメント要素を null にすることはできません。|
> |**名前**:<br />QueryBuilderDuplicateAlias<br />**16 進数**:<br />80041130<br />**数値**:<br />-2147217104|FetchXML は一意のエイリアスを持っているべきです。|
> |**名前**:<br />QueryBuilderElementNotFound<br />**16 進数**:<br />80041123<br />**数値**:<br />-2147217117|必須要素が指定されていません。|
> |**名前**:<br />QueryBuilderEntitiesDontMatch<br />**16 進数**:<br />80041128<br />**数値**:<br />-2147217112|fetchxml で指定されたエンティティ名は、[エンティティ] または [クエリ式] で指定されたエンティティ名に対応していません。|
> |**名前**:<br />QueryBuilderInvalid_Alias<br />**16 進数**:<br />80041109<br />**数値**:<br />-2147217143|無効な集計操作のエイリアスです。|
> |**名前**:<br />QueryBuilderInvalid_Value<br />**16 進数**:<br />80041108<br />**数値**:<br />-2147217144|種類に指定された値が無効です。|
> |**名前**:<br />QueryBuilderInvalidAggregateAttribute<br />**16 進数**:<br />8004112F<br />**数値**:<br />-2147217105|集計 {0} は、タイプ {1} の属性に対してサポートされていません。|
> |**名前**:<br />QueryBuilderInvalidAttributeValue<br />**16 進数**:<br />80041139<br />**数値**:<br />-2147217095|指定された属性の値が無効です。|
> |**名前**:<br />QueryBuilderInvalidColumnSetVersion<br />**16 進数**:<br />80041112<br />**数値**:<br />-2147217134|指定された列セット バージョンは無効です。|
> |**名前**:<br />QueryBuilderInvalidConditionOperator<br />**16 進数**:<br />80041120<br />**数値**:<br />-2147217120|サポートされていない条件演算子です。|
> |**名前**:<br />QueryBuilderInvalidDateGrouping<br />**16 進数**:<br />80041135<br />**数値**:<br />-2147217099|無効な値は日付グループ化用に特定されました。|
> |**名前**:<br />QueryBuilderInvalidFilterType<br />**16 進数**:<br />80041122<br />**数値**:<br />-2147217118|サポートされていないフィルターの種類です 有効な値は 'and'、または 'or' です。|
> |**名前**:<br />QueryBuilderInvalidJoinOperator<br />**16 進数**:<br />80041121<br />**数値**:<br />-2147217119|サポートされていない結合演算子です。|
> |**名前**:<br />QueryBuilderInvalidLogicalOperator<br />**16 進数**:<br />800410fe<br />**数値**:<br />-2147217154|サポートされていない論理演算子 "{0}" です。  受け付けられる値は ('および'、'または') です。|
> |**名前**:<br />QueryBuilderInvalidOrderType<br />**16 進数**:<br />8004111f<br />**数値**:<br />-2147217121|有効な受注の種類は、このメソッドを呼び出す前の順序で設定する必要があります。|
> |**名前**:<br />QueryBuilderInvalidPagingCookie<br />**16 進数**:<br />8004112A<br />**数値**:<br />-2147217110|ページング Cookieのページ番号が無効です。|
> |**名前**:<br />QueryBuilderInvalidUpdate<br />**16 進数**:<br />80041100<br />**数値**:<br />-2147217152|更新不可能フィールドを更新する試みが実行されました。|
> |**名前**:<br />QueryBuilderLinkNodeForOrderNotFound<br />**16 進数**:<br />80041126<br />**数値**:<br />-2147217114|クエリから EntityExpression への変換に失敗しました。 受注に関するリンク ノードが見つかりませんでした。|
> |**名前**:<br />QueryBuilderMultipleIntersectEntities<br />**16 進数**:<br />8004110e<br />**数値**:<br />-2147217138|指定された 2 つのエンティティ間には、複数の交差するエンティティが存在します。|
> |**名前**:<br />QueryBuilderNoAlias<br />**16 進数**:<br />8004110b<br />**数値**:<br />-2147217141|特定のエンティティに対するエイリアスは条件内で見つかりませんでした。|
> |**名前**:<br />QueryBuilderNoAttribute<br />**16 進数**:<br />80041103<br />**数値**:<br />-2147217149|指定された属性は、このエンティティで存在しません。|
> |**名前**:<br />QueryBuilderNoAttrsDistinctConflict<br />**16 進数**:<br />8004112C<br />**数値**:<br />-2147217108|[no-attrs] タグは、[true] に設定する [Distinct] と組み合わせて使用できません。|
> |**名前**:<br />QueryBuilderNoEntity<br />**16 進数**:<br />80041102<br />**数値**:<br />-2147217150|指定されたエンティティは見つかりませんでした。|
> |**名前**:<br />QueryBuilderNoEntityKey<br />**16 進数**:<br />80041140<br />**数値**:<br />-2147217088|指定された entitykey は見つかりませんでした。|
> |**名前**:<br />QueryBuilderPagingOrderBy<br />**16 進数**:<br />80041129<br />**数値**:<br />-2147217111|列による並べ替えはページング Cookie と一致しません。|
> |**名前**:<br />QueryBuilderReportView_Does_Not_Exist<br />**16 進数**:<br />8004110d<br />**数値**:<br />-2147217139|レポート ビューは、特定のエンティティに存在していません。|
> |**名前**:<br />QueryBuilderSerializationInvalidIsQuickFindFilter<br />**16 進数**:<br />80041138<br />**数値**:<br />-2147217096|isquickfindfields の属性に有効な値は、'true'、'false'、'1'、および '0' です。|
> |**名前**:<br />QueryBuilderSerialzeLinkTopCriteria<br />**16 進数**:<br />80041114<br />**数値**:<br />-2147217132|フェッチは、linkentity からの条件のある句をサポートしていません。|
> |**名前**:<br />QueryBuilderUnexpected<br />**16 進数**:<br />80041101<br />**数値**:<br />-2147217151|予期しないエラーが発生しました。|
> |**名前**:<br />QueryBuilderValue_GreaterThanZero<br />**16 進数**:<br />8004110c<br />**数値**:<br />-2147217140|0 より大きい値は特定する必要があります。|
> |**名前**:<br />QueryContainedSecuredAttributeWithoutAccess<br />**16 進数**:<br />8004F506<br />**数値**:<br />-2147158778|呼び出し元のセキュリティで保護された属性を含むクエリにアクセスできません|
> |**名前**:<br />QueryFilterConditionAttributeNotPresentInExpressionEntity<br />**16 進数**:<br />80071119<br />**数値**:<br />-2147020519|クエリは、Dynamics 365 に存在しないフィールドを参照しています: "{0}"|
> |**名前**:<br />QueryNotValidForStaticList<br />**16 進数**:<br />8004F702<br />**数値**:<br />-2147158270|静的リストにはクエリを指定できません。|
> |**名前**:<br />QueryParameterNotUnique<br />**16 進数**:<br />8005E00B<br />**数値**:<br />-2147098613|クエリ パラメーター {0} はデータ セット内で一度だけ定義する必要があります。|
> |**名前**:<br />QueueIdNotPresent<br />**16 進数**:<br />80040528<br />**数値**:<br />-2147220184|ターゲット キューを入力してください。 [キュー] フィールドに有効な値を指定してから、やり直してください。|
> |**名前**:<br />QueueItemNotPresent<br />**16 進数**:<br />80040529<br />**数値**:<br />-2147220183|このキューに登録するレコードの名前を入力してください。 [キュー] アイテム フィールドに有効な値を指定してから、やり直してください。|
> |**名前**:<br />QueueMailboxUnexpectedDeliveryMethod<br />**16 進数**:<br />8005E210<br />**数値**:<br />-2147098096|キューに関連付けられているメールボックスの配信方法を、Outlook クライアントにすることはできません。|
> |**名前**:<br />QuickCreateDisabledOnEntity<br />**16 進数**:<br />80060911<br />**数値**:<br />-2147088111|{0} エンティティに簡易作成フォームがないか、入れ子になっている簡易作成フォームの数が許可されている最大数を超えました。|
> |**名前**:<br />QuickCreateInvalidEntityName<br />**16 進数**:<br />80060910<br />**数値**:<br />-2147088112|entityLogicalName が無効です。 この値は NULL または空白にすることはできず、組織のエンティティを表す必要があります。|
> |**名前**:<br />QuickFindQueryRecordLimitExceeded<br />**16 進数**:<br />8004E024<br />**数値**:<br />-2147164124|QuickFindQueryRecordLimit が超過しています。 この操作を実行できません。|
> |**名前**:<br />QuickFindSavedQueryAlreadyExists<br />**16 進数**:<br />8004853A<br />**数値**:<br />-2147187398|"1 つの簡易検索保存済みクエリのみが、エンティティで存在できます。 以下の objecttypecode を持つ簡易検索保存済みクエリが既に存在します。{0}"|
> |**名前**:<br />QuickFormNotCustomizableThroughSdk<br />**16 進数**:<br />8004F659<br />**数値**:<br />-2147158439|SDK は、"クイック" 型のフォームの作成をサポートしていません。 このフォームの種類は、内部で使用するためにのみ確保されます。|
> |**名前**:<br />QuoteAndSalesOrderCurrencyNotEqual<br />**16 進数**:<br />80048cee<br />**数値**:<br />-2147185426|レコードの通貨は、価格表の通貨に対応しません。|
> |**名前**:<br />QuoteReviseExistingActiveQuote<br />**16 進数**:<br />80048d00<br />**数値**:<br />-2147185408|見積もりは、同じ見積もり番号を持つ下書きまたはアクティブ状態の別の見積もりが既に存在するため変更できません。|
> |**名前**:<br />ReactivateEntityKeyOnlyForFailedJobs<br />**16 進数**:<br />80060897<br />**数値**:<br />-2147088233|エンティティ キーの再アクティブ化は、失敗したジョブに対してだけサポートされています。|
> |**名前**:<br />ReadIntentIncompatible<br />**16 進数**:<br />80060881<br />**数値**:<br />-2147088255|現在の実行コンテキストのプラグイン実行インテントは親コンテキストと互換性がありません|
> |**名前**:<br />ReadOnlyCreateValidationFailed<br />**16 進数**:<br />80061002<br />**数値**:<br />-2147086334|読み取り専用プロパティにプロパティ インスタンスの値を作成および割り当てることはできません。|
> |**名前**:<br />ReadOnlyUpdateValidationFailed<br />**16 進数**:<br />80061003<br />**数値**:<br />-2147086333|プロパティ インスタンスを読み取り専用プロパティに更新することはできません。|
> |**名前**:<br />ReadOnlyUserNotSupported<br />**16 進数**:<br />80041d40<br />**数値**:<br />-2147214016|読み取り専用アクセス モードはサポートされていません|
> |**名前**:<br />RecalculateNotSupportedOnNonRollupField<br />**16 進数**:<br />80060554<br />**数値**:<br />-2147089068|種類 {1} のフィールド {0} は [再計算] 操作をサポートしていません。 再計算の操作はロールアップ フィールドに対してのみ呼び出せます。|
> |**名前**:<br />RecommendationAzureConnectionCascadeActivateFailed<br />**16 進数**:<br />80061633<br />**数値**:<br />-2147084749|1 つまたは複数のレコメンデーション モデルはアクティブ化できませんでした。 Azure サービス接続とは別に既存の推奨モデルのアクティブ化を試してください。|
> |**名前**:<br />RecommendationAzureConnectionFailed<br />**16 進数**:<br />80061631<br />**数値**:<br />-2147084751|Azure Recommendations サービスに接続できませんでした。 サービス URL と Azure アカウント キーが有効で、サービスのサブスクリプションがアクティブであることを確認してください。|
> |**名前**:<br />RecommendationModelActivateConnectionMustBeActive<br />**16 進数**:<br />80061607<br />**数値**:<br />-2147084793|Azure Machine Learning レコメンデーション サービスの接続は、モデルのアクティブ化の前にアクティブ化する必要があります。 レコメンデーション サービスの接続のライセンス認証を行い、もう一度やり直してください。|
> |**名前**:<br />RecommendationModelActiveVersionInvalidStatus<br />**16 進数**:<br />80061602<br />**数値**:<br />-2147084798|使用されるモデル バージョンは、モデルがアクティブ化される前に、正常に作成される必要があります。|
> |**名前**:<br />RecommendationModelActiveVersionNotSet<br />**16 進数**:<br />80061601<br />**数値**:<br />-2147084799|使用されるモデル バージョンは空になります。 モデルを有効化するには、モデル バージョンを指定してください。|
> |**名前**:<br />RecommendationModelBuildConnectionMustBeActive<br />**16 進数**:<br />80061606<br />**数値**:<br />-2147084794|Azure Machine Learning レコメンデーション サービスの接続は、推奨モデルのビルド前にアクティブ化する必要があります。 レコメンデーション サービスの接続のライセンス認証を行い、もう一度やり直してください。|
> |**名前**:<br />RecommendationModelExpired<br />**16 進数**:<br />80061608<br />**数値**:<br />-2147084792|推奨モデル バージョンは期限切れになりました。 [有効期限] の日付を変更してから、モデルのアクティブ化をやり直してください。|
> |**名前**:<br />RecommendationModelMappingDuplicateRecord<br />**16 進数**:<br />80061610<br />**数値**:<br />-2147084784|エンティティ、マッピングの種類、およびバージョンに対する推奨モデル マッピング値は、一意である必要があります。|
> |**名前**:<br />RecommendationModelMappingReadOnly<br />**16 進数**:<br />80061611<br />**数値**:<br />-2147084783|対応するバスケット エンティティが存在する場合は、推奨事項エンティティは修正できません。|
> |**名前**:<br />RecommendationModelVersionActive<br />**16 進数**:<br />80061620<br />**数値**:<br />-2147084768|RecommendationModel バージョンはモデル上のアクティブ バージョンとして選択されています。削除することはできません。|
> |**名前**:<br />RecommendationModelVersionBuildInProgress<br />**16 進数**:<br />80061621<br />**数値**:<br />-2147084767|モデル ビルドのワークフローが既に処理中です。 現在のワークフローが完了するまで、別のビルド ワークフローを開始することはできません。|
> |**名前**:<br />RecommendationModelVersionDuplicateName<br />**16 進数**:<br />80061622<br />**数値**:<br />-2147084766|同じ名前のモデル バージョンが既に存在します。 異なる名前を指定します。|
> |**名前**:<br />RecommendationsUnavailable<br />**16 進数**:<br />80061605<br />**数値**:<br />-2147084795|Azure Machine Learning の製品推奨機能は、一時的に使用できない状態です。 カタログ レコメンデーションのみ使用できます。|
> |**名前**:<br />RecommendedDocumentsRetrievalFailure<br />**16 進数**:<br />80071015<br />**数値**:<br />-2147020779|ドキュメント ソースからドキュメント サジェスチョンを取得できません。|
> |**名前**:<br />RecommendedDocumentsRetrievalFailureWhenSPSiteNotConfigured<br />**16 進数**:<br />80071028<br />**数値**:<br />-2147020760|ドキュメント ソースからドキュメント サジェスチョンを取得できません。|
> |**名前**:<br />RecordAndOpportunityCurrencyNotEqual<br />**16 進数**:<br />80048cef<br />**数値**:<br />-2147185425|レコードの通貨は、価格表の通貨に対応しません。|
> |**名前**:<br />RecordAndPricelistCurrencyNotEqual<br />**16 進数**:<br />80048cf6<br />**数値**:<br />-2147185418|レコードの通貨は、価格表の通貨に対応しません。|
> |**名前**:<br />RecordCanOnlyBeRevisedFromActiveState<br />**16 進数**:<br />8004F883<br />**数値**:<br />-2147157885|アクティブな製品のみを変更できます。|
> |**名前**:<br />RecordCountExceededForExcelOnlineError<br />**16 進数**:<br />80072456<br />**数値**:<br />-2147015594|必要なレコード数は {0} です。 現在のレコード数は次のとおりです: {1}|
> |**名前**:<br />RecordNotFoundByEntityKey<br />**16 進数**:<br />80060891<br />**数値**:<br />-2147088239|指定されたキー値を持つレコードは、{0} エンティティに存在しません|
> |**名前**:<br />RecordResolutionFailed<br />**16 進数**:<br />8004F603<br />**数値**:<br />-2147158525|元のレコードが Microsoft Dynamics 365 に存在していないため、レコードを更新できませんでした。|
> |**名前**:<br />RecurrenceCalendarTypeNotSupported<br />**16 進数**:<br />8004E116<br />**数値**:<br />-2147163882|カレンダーの種類がサポートされていません。|
> |**名前**:<br />RecurrenceEndDateTooBig<br />**16 進数**:<br />8004E119<br />**数値**:<br />-2147163879|定期的なアイテムのパターンの終了日が無効です。|
> |**名前**:<br />RecurrenceHasNoOccurrence<br />**16 進数**:<br />8004E117<br />**数値**:<br />-2147163881|定期的なアイテムのパターンは発生していません。|
> |**名前**:<br />RecurrenceRuleDeleteFailure<br />**16 進数**:<br />8004E111<br />**数値**:<br />-2147163887|既存のルール マスターに付随されるルールを削除できません。 親エンティティを使用して、ルールを削除します。|
> |**名前**:<br />RecurrenceRuleUpdateFailure<br />**16 進数**:<br />8004E110<br />**数値**:<br />-2147163888|既存のルール マスターに付随されるルールを更新できません。 親エンティティを使用して、ルールを更新します。|
> |**名前**:<br />RecurrenceStartDateTooSmall<br />**16 進数**:<br />8004E118<br />**数値**:<br />-2147163880|定期的なアイテムのパターンの開始日が無効です。|
> |**名前**:<br />RecurringSeriesCompleted<br />**16 進数**:<br />8004E10B<br />**数値**:<br />-2147163893|系列には無効な ExpansionStateCode があります。|
> |**名前**:<br />RecurringSeriesMasterIsLocked<br />**16 進数**:<br />8004E113<br />**数値**:<br />-2147163885|定期的な系列マスター レコードが他のプロセスによってロックされています。|
> |**名前**:<br />RefEntityRelationshipRoleRequired<br />**16 進数**:<br />80048470<br />**数値**:<br />-2147187600|新しい一対多エンティティ関係を作成する際、参照元エンティティのエンティティ関係ロールが必要です。|
> |**名前**:<br />ReferencedEntityHasLogicalPrimaryNameField<br />**16 進数**:<br />8004432E<br />**数値**:<br />-2147204306|このエンティティには論理プライマリ フィールドがあるため、一対多の関連付けの参照先エンティティにすることはできません|
> |**名前**:<br />ReferencedEntityMustHaveLookupView<br />**16 進数**:<br />80044337<br />**数値**:<br />-2147204297|関連付けの参照先エンティティは検索ダイアログ ビューが必要です。|
> |**名前**:<br />ReferencingEntityCannotBeSolutionAware<br />**16 進数**:<br />80044350<br />**数値**:<br />-2147204272|関連付けの参照先エンティティはソリューションのコンポーネントにはできません。|
> |**名前**:<br />ReferencingEntityMustHaveAssociationView<br />**16 進数**:<br />80044338<br />**数値**:<br />-2147204296|関連付けの参照先エンティティは関連ビューが必要です。|
> |**名前**:<br />RefferedSolutionIsDifferent<br />**16 進数**:<br />80050122<br />**数値**:<br />-2147155678|アクティブ ソリューション外で非公開の行が見つかりました: SiteMapId = {0}、SolutionId = {1}|
> |**名前**:<br />ReflexiveEntityParentOrChildDoesNotExist<br />**16 進数**:<br />80040388<br />**数値**:<br />-2147220600|親エンティティまたは子エンティティが存在しません|
> |**名前**:<br />RefRoleNavPaneDisplayOptionRequired<br />**16 進数**:<br />80060898<br />**数値**:<br />-2147088232|NavPaneDisplayOption 属性は、一対多の関連付け {0} の参照ロールに対して必要です。|
> |**名前**:<br />RegardingObjectValuesRetrievalFailure<br />**16 進数**:<br />80071012<br />**数値**:<br />-2147020782|関連するオブジェクト値の取得に失敗しました。|
> |**名前**:<br />RelatedEntityAlreadyExistsInProfile<br />**16 進数**:<br />8005F21e<br />**数値**:<br />-2147093986|このプロファイルに関連エンティティが既に存在します。|
> |**名前**:<br />RelatedEntityDoesNotExistInProfileItem<br />**16 進数**:<br />8006098E<br />**数値**:<br />-2147087986|Mobile Offline プロファイル項目 {2} について、Mobile Offline プロファイル項目の関連付け {1} の関連エンティティ {0} がプロファイル {3} のプロファイル項目に存在しません。|
> |**名前**:<br />RelatedEntityDoesNotExistsInProfile<br />**16 進数**:<br />8005F21f<br />**数値**:<br />-2147093985|関連エンティティは、プロファイル項目に存在しません。|
> |**名前**:<br />RelatedEntityGenericError<br />**16 進数**:<br />8005F220<br />**数値**:<br />-2147093984|プロファイル関連付けの作成中に予期しないエラーが発生しました。 やり直してください。|
> |**名前**:<br />RelatedRecordsFailure<br />**16 進数**:<br />80071013<br />**数値**:<br />-2147020781|関連レコードを取得できませんでした。|
> |**名前**:<br />RelationshipGraphLimitExceeded<br />**16 進数**:<br />80071139<br />**数値**:<br />-2147020487|プロファイル '{0}'で定義されたエンティティに対して 1 つ以上のプロファイル項目の関連付けを指定しました。 関連付け数が {2} で、サポートされている制限の {3} を超えているエンティティ '{1}' を含むプロファイル項目の関連付けを確認してください。|
> |**名前**:<br />RelationshipInsightsFeatureDisableError<br />**16 進数**:<br />80044292<br />**数値**:<br />-2147204462|リレーションシップ インサイト機能を無効にできません|
> |**名前**:<br />RelationshipInsightsFeatureNotEnabledError<br />**16 進数**:<br />80044293<br />**数値**:<br />-2147204461|Relationship Insights 機能が有効になっていないか、RI パッケージがインストールされていません|
> |**名前**:<br />RelationshipIntelligenceSDKInvocationError<br />**16 進数**:<br />80044276<br />**数値**:<br />-2147204490|リレーションシップ インサイト SDK を使用するには Dynamics 365 (online) が必要です。|
> |**名前**:<br />RelationshipIsNotCustomRelationship<br />**16 進数**:<br />8004700a<br />**数値**:<br />-2147192822|指定されたレーションシップは、カスタム リレーションシップではありません|
> |**名前**:<br />RelationshipNameLengthExceedsLimit<br />**16 進数**:<br />8004802A<br />**数値**:<br />-2147188694|識別子の長さは {1} 文字を超えることはできません。 提供された名前: {0} の長さが最大長 {1} 文字を超えています。|
> |**名前**:<br />RelationshipNotCreatedForOfficeGraphError<br />**16 進数**:<br />80044235<br />**数値**:<br />-2147204555|いずれのエンティティでも officegraph が有効になっていないため、この関連付けは作成できません。|
> |**名前**:<br />RelationshipNotUpdatedForOfficeGraphError<br />**16 進数**:<br />80044236<br />**数値**:<br />-2147204554|いずれのエンティティでも officegraph が有効になっていないため、この関連付けを officegraph 向けに更新できません。|
> |**名前**:<br />RelationshipRoleMismatch<br />**16 進数**:<br />80048467<br />**数値**:<br />-2147187609|顧客間関係ロール名 {0} は、{1} または {2}の予期したエンティティ名のいずれかに対応していません。|
> |**名前**:<br />RelationshipRoleNodeNumberInvalid<br />**16 進数**:<br />80048469<br />**数値**:<br />-2147187607|多対多のエンティティ関係を作成する際には、2 つのエンティティ関係ロール ノードが必要です。|
> |**名前**:<br />RelatioshipAlreadyExists<br />**16 進数**:<br />8005F221<br />**数値**:<br />-2147093983|エンティティの選択された関連付はプロファイルにすでに存在します。 |
> |**名前**:<br />ReportDoesNotExist<br />**16 進数**:<br />80040499<br />**数値**:<br />-2147220327|レポートが存在しません。 ReportId:{0}|
> |**名前**:<br />ReportFileTooBig<br />**16 進数**:<br />80048297<br />**数値**:<br />-2147188073|ファイルが大きすぎて、アップロードできません。 ファイルのサイズを小さくして、やり直してください。|
> |**名前**:<br />ReportFileZeroLength<br />**16 進数**:<br />80048296<br />**数値**:<br />-2147188074|空のファイルをアップロードしました。  新しいファイルを選択してからやり直してください。|
> |**名前**:<br />ReportImportCategoryOptionNotFound<br />**16 進数**:<br />8004F028<br />**数値**:<br />-2147160024|レポートのカテゴリ オプションは見つかりませんでした。|
> |**名前**:<br />ReportingServicesReportExpected<br />**16 進数**:<br />80040484<br />**数値**:<br />-2147220348|レポートは、Reporting Services レポートではありません。|
> |**名前**:<br />ReportLocalProcessingError<br />**16 進数**:<br />80048310<br />**数値**:<br />-2147187952|ローカル処理されたレポートの表示中にエラーが発生しました。 ReportId:{0}|
> |**名前**:<br />ReportLoopBeingCreated<br />**16 進数**:<br />80040498<br />**数値**:<br />-2147220328|この上位下位の関連付けを作成すると、レポート階層にループが生成されます。|
> |**名前**:<br />ReportLoopExists<br />**16 進数**:<br />80040497<br />**数値**:<br />-2147220329|レポート階層にループが存在します。|
> |**名前**:<br />ReportMissingDataSourceCredentialsError<br />**16 進数**:<br />80048311<br />**数値**:<br />-2147187951|レポートで使用されるデータ ソースに関して、資格情報が指定されていません。 ReportId:{0}|
> |**名前**:<br />ReportMissingDataSourceError<br />**16 進数**:<br />80048312<br />**数値**:<br />-2147187950|レポートで予期されるデータ ソースが指定されていません。 ReportId:{0}|
> |**名前**:<br />ReportMissingEndpointError<br />**16 進数**:<br />80048313<br />**数値**:<br />-2147187949|ReportViewer コントロールが使用する SOAP エンドポイントにアクセスできませんでした。|
> |**名前**:<br />ReportMissingParameterError<br />**16 進数**:<br />80048314<br />**数値**:<br />-2147187948|レポートにより予期されるパラメーターが指定されていません。 ReportId:{0}|
> |**名前**:<br />ReportMissingReportSourceError<br />**16 進数**:<br />80048315<br />**数値**:<br />-2147187947|レポートのソースが指定されていません。  ReportId:{0}|
> |**名前**:<br />ReportNotAvailable<br />**16 進数**:<br />80048299<br />**数値**:<br />-2147188071|レポートを使用できません|
> |**名前**:<br />ReportParentChildNotCustomizable<br />**16 進数**:<br />8004832f<br />**数値**:<br />-2147187921|レポートは、親レポートまたは子レポートがカスタマイズ可能でないため更新できませんでした。|
> |**名前**:<br />ReportRdlSandboxing<br />**16 進数**:<br />80048293<br />**数値**:<br />-2147188077|レポート サーバーの RDL サンドボックスの制限のため、レポートのアップロードに失敗しました。|
> |**名前**:<br />ReportRenderError<br />**16 進数**:<br />80040494<br />**数値**:<br />-2147220332|レポートのレンダリング中にエラーが発生しました。|
> |**名前**:<br />ReportSecurityError<br />**16 進数**:<br />80048316<br />**数値**:<br />-2147187946|レポートにセキュリティ違反が含まれています。 ReportId:{0}|
> |**名前**:<br />ReportServerInvalidUrl<br />**16 進数**:<br />80048301<br />**数値**:<br />-2147187967|特定の URL からのレポート サーバーに連絡することはできません|
> |**名前**:<br />ReportServerNoPrivilege<br />**16 進数**:<br />80048302<br />**数値**:<br />-2147187966|レポート サーバーを構成するための十分な特権がありません。|
> |**名前**:<br />ReportServerSP2HotFixNotApplied<br />**16 進数**:<br />80048309<br />**数値**:<br />-2147187959|レポート サーバー SP2 ワークグループに役割作成用修正プログラムが適用されていません|
> |**名前**:<br />ReportServerUnknownException<br />**16 進数**:<br />80048300<br />**数値**:<br />-2147187968|レポート サーバーによりスローされた不明な例外|
> |**名前**:<br />ReportServerVersionLow<br />**16 進数**:<br />80048303<br />**数値**:<br />-2147187965|レポート サーバーが最小バージョン要件を満たしていません|
> |**名前**:<br />ReportTypeBlocked<br />**16 進数**:<br />80048295<br />**数値**:<br />-2147188075|レポートは、有効な種類ではありません。  ダウンロードまたはアップロードはできません。|
> |**名前**:<br />ReportUploadDisabled<br />**16 進数**:<br />80048294<br />**数値**:<br />-2147188076|Reporting Services レポートをアップロードすることはできません。 新しいレポートを作成する場合、レポート ウィザードを使用してください。|
> |**名前**:<br />ReportViewerError<br />**16 進数**:<br />8004832c<br />**数値**:<br />-2147187924|レポートのレンダリング中にエラーが発生しました。 ReportId:{0}|
> |**名前**:<br />RequestIsNotAuthenticated<br />**16 進数**:<br />80044302<br />**数値**:<br />-2147204350|要求が認証されていません。|
> |**名前**:<br />RequestLengthTooLarge<br />**16 進数**:<br />8004418a<br />**数値**:<br />-2147204726|要求メッセージが長すぎます。|
> |**名前**:<br />RequiredBundleItemCannotBeUpdated<br />**16 進数**:<br />80081009<br />**数値**:<br />-2146955255|このバンドル品目は、バンドル内の必須の製品であるために、削除できません。|
> |**名前**:<br />RequiredBundleProductCannotBeDeleted<br />**16 進数**:<br />80081008<br />**数値**:<br />-2146955256|この製品レコードは、バンドル内の必須の製品であるために、削除できません。|
> |**名前**:<br />RequiredChildReportHasOtherParent<br />**16 進数**:<br />8004F029<br />**数値**:<br />-2147160023|レポートのカテゴリ オプションは見つかりませんでした。|
> |**名前**:<br />RequiredColumnsNotFoundInImportFile<br />**16 進数**:<br />80040383<br />**数値**:<br />-2147220605|変換に使用された 1 つまたは複数のソース列がソース ファイルに存在しません。|
> |**名前**:<br />RequiredFieldMissing<br />**16 進数**:<br />80040200<br />**数値**:<br />-2147220992|必須フィールドが不足しています。|
> |**名前**:<br />RequiredProcessStepIsNull<br />**16 進数**:<br />8006041a<br />**数値**:<br />-2147089382|次のステージに進むには、必須ステップを完了してください。|
> |**名前**:<br />RequireValidImportMapForUpdate<br />**16 進数**:<br />8004F600<br />**数値**:<br />-2147158528|更新で使用されたインポート マップが正しくないため、更新操作を完了できません。|
> |**名前**:<br />RestrictedSolutionName<br />**16 進数**:<br />8004F022<br />**数値**:<br />-2147160030|ソリューションの一意の名前 '{0}' は、制限されており、内部ソリューションでのみ使用できます。|
> |**名前**:<br />RestrictInheritedRole<br />**16 進数**:<br />80044152<br />**数値**:<br />-2147204782|継承済ロールは修正できません。|
> |**名前**:<br />RetiredProductToBundle<br />**16 進数**:<br />8004F993<br />**数値**:<br />-2147157613|廃止された製品にバンドルを追加することはできません。|
> |**名前**:<br />RetrieveImagePropertiesFail<br />**16 進数**:<br />80072552<br />**数値**:<br />-2147015342|提供されたエンティティ画像のプロパティを取得できません|
> |**名前**:<br />RetrieveOrganizationInfoUnexpectedError<br />**16 進数**:<br />80072301<br />**数値**:<br />-2147015935|組織情報の取得中に予期しないエラーが発生しました。 依存サービスを現時点では利用できない可能性があります。 後で再試行してください。|
> |**名前**:<br />RetrieveRecordOfflineErrorCode<br />**16 進数**:<br />8005F213<br />**数値**:<br />-2147093997|このレコードはオフライン時には利用できません。  再接続してからやり直してください。|
> |**名前**:<br />RetrieveUserLicenseUnexpectedError<br />**16 進数**:<br />80072300<br />**数値**:<br />-2147015936|ユーザー ライセンス情報の取得中に予期しないエラーが発生しました。 依存サービスを現時点では利用できない可能性があります。 後で再試行してください。|
> |**名前**:<br />RetryFailed<br />**16 進数**:<br />8004F045<br />**数値**:<br />-2147159995|{0} 回の再試行後にアクションが失敗しました。 InnerException は次のとおりです: {1}。|
> |**名前**:<br />RibbonImportDependencyMissingEntity<br />**16 進数**:<br />8004F104<br />**数値**:<br />-2147159804|リボン アイテム '{0}' は、エンティティ {1} に依存しています。|
> |**名前**:<br />RibbonImportDependencyMissingRibbonControl<br />**16 進数**:<br />8004F107<br />**数値**:<br />-2147159801|リボン アイテム '{0}' は、リボン コントロール ID='{1}' に依存しています。|
> |**名前**:<br />RibbonImportDependencyMissingRibbonElement<br />**16 進数**:<br />8004F105<br />**数値**:<br />-2147159803|リボン アイテム '{0}' は、<{1} Id="{2}" /> に依存しています。|
> |**名前**:<br />RibbonImportDependencyMissingWebResource<br />**16 進数**:<br />8004F106<br />**数値**:<br />-2147159802|リボン アイテム '{0}' は、Web リソース ID='{1}' に依存しています。|
> |**名前**:<br />RibbonImportDuplicateElementId<br />**16 進数**:<br />8004F10B<br />**数値**:<br />-2147159797|ID: {0} のリボン要素は、同じ ID を持つ既存のリボン要素が既に存在するため、インポートできません。|
> |**名前**:<br />RibbonImportEntityNotSupported<br />**16 進数**:<br />8004F103<br />**数値**:<br />-2147159805|{0} エンティティにはエンティティでサポートされていないリボン定義が含まれているため、ソリューションはインポートできません。 RibbonDiffXml ノードをエンティティ定義から削除し、再びインポートしてください。|
> |**名前**:<br />RibbonImportHidingBasicHomeTab<br />**16 進数**:<br />8004F101<br />**数値**:<br />-2147159807|インポート中のリボンの定義によって、Microsoft Dynamics 365 のホーム タブが削除されます。ホーム タブの定義を含めてください。含めない場合、ホーム タブを表示するアプリケーションの領域内にリボンが表示されなくなります。|
> |**名前**:<br />RibbonImportHidingJewel<br />**16 進数**:<br />8004F10A<br />**数値**:<br />-2147159798|リボンのカスタマイズで <Jewel> ノードを非表示にできません。 このノードを非表示にするリボンのカスタマイズはインポート時にすべて無視され、エクスポートされません。|
> |**名前**:<br />RibbonImportInvalidPrivilegeName<br />**16 進数**:<br />8004F102<br />**数値**:<br />-2147159806|このソリューションの RibbonDiffXml には無効な {0} 特権への参照が含まれています。 有効な特権を参照するように RibbonDiffXml を更新して、インポートをやり直してください。|
> |**名前**:<br />RibbonImportLocationAndIdDoNotMatch<br />**16 進数**:<br />8004F109<br />**数値**:<br />-2147159799|'{2}' が CustomAction の Location 値と一致していないため、CustomAction ID '{0}' で '{1}' を上書きできません。|
> |**名前**:<br />RibbonImportModifyingTopLevelNode<br />**16 進数**:<br />8004F108<br />**数値**:<br />-2147159800|リボンのカスタマイズは、次の最上位レベルのリボン ノードに対して行うことはできません: <Ribbon>、<ContextualGroups>、<Tabs>。|
> |**名前**:<br />RibbonImportRibbonDiffIdInvalidLength<br />**16 進数**:<br />8004F10C<br />**数値**:<br />-2147159796|ID の長さが最大長の 128 文字を超えているため、このリボン要素をインポートできません: {0}|
> |**名前**:<br />RINotProvisioned<br />**16 進数**:<br />80044281<br />**数値**:<br />-2147204479|組織 {0} のリレーションシップ インサイトが有効になっていません。|
> |**名前**:<br />RoleAlreadyExists<br />**16 進数**:<br />80041403<br />**数値**:<br />-2147216381|指定された名前 '{0}' のロールは、部署 {1} およびソリューション ID {3} に既に存在します。 ロール ID: {2}|
> |**名前**:<br />RoleNotEnabledForTabletApp<br />**16 進数**:<br />8005F203<br />**数値**:<br />-2147094013|このアプリを使用する権限がありません。\nシステム管理者に問い合わせて、設定を更新してください。|
> |**名前**:<br />RollupAggregateQueryRecordLimitExceeded<br />**16 進数**:<br />8004E025<br />**数値**:<br />-2147164123|関連レコードの計算の制限 {0} に達したため、計算をオンラインで実行できません。|
> |**名前**:<br />RollupCalculationLimitReached<br />**16 進数**:<br />80060561<br />**数値**:<br />-2147089055|計算の制限に達したため、現在計算を実行できません。 しばらく待ってから、もう一度お試しください。|
> |**名前**:<br />RollupDependentFieldNameAlreadyExists<br />**16 進数**:<br />80060556<br />**数値**:<br />-2147089066|同じ名前の別のフィールドが既に存在するために、ロールアップ フィールドに必要な依存フィールド {0} が作成できません。 ロールアップ フィールドを作成するために代替名を使用してください。|
> |**名前**:<br />RollupFieldAggregateFunctionNotAllowed<br />**16 進数**:<br />80060546<br />**数値**:<br />-2147089082|集計関数 {0} は許可されません。|
> |**名前**:<br />RollupFieldAggregateFunctionNotAllowedForRollupFieldDataType<br />**16 進数**:<br />80060545<br />**数値**:<br />-2147089083|ロールアップ フィールドのデータの種類が {1} である場合、集計関数 {0} は 許可されません。|
> |**名前**:<br />RollupFieldAndAggregateFieldDataTypeFormatMismatch<br />**16 進数**:<br />80060544<br />**数値**:<br />-2147089084|ロールアップ フィールドが形式 {3} のデータの種類 {2} である場合、集計されたフィールドで形式 {1} のデータの種類 {0} は許可されません。|
> |**名前**:<br />RollupFieldDefinitionNotValid<br />**16 進数**:<br />80060553<br />**数値**:<br />-2147089069|ロールアップ フィールド定義が無効なため計算が失敗しました。 システム管理者にお問い合わせください。|
> |**名前**:<br />RollupFieldDependentFieldCannotDeleted<br />**16 進数**:<br />80060541<br />**数値**:<br />-2147089087|ロールアップ フィールド {0} はこのフィールドに依存します。 このフィールドは、対応するロールアップ フィールド {0} を削除することによってのみ削除できます。|
> |**名前**:<br />RollupFieldNoWriteAccess<br />**16 進数**:<br />8004E027<br />**数値**:<br />-2147164121|ユーザーは {0} レコード {1} のロールアップ フィールドを計算する {2} ID への書き込みアクセス許可がありません。|
> |**名前**:<br />RollupFieldsAggregateFieldDataTypeNotAllowedSimilarRollupFieldDataType<br />**16 進数**:<br />8006053d<br />**数値**:<br />-2147089091|ロールアップ フィールドがデータの種類 {1} である場合、データの種類 {0} は集計フィールドに対して許可されません。|
> |**名前**:<br />RollupFieldsAggregateFieldNotBelongToRelatedEntity<br />**16 進数**:<br />80060540<br />**数値**:<br />-2147089088|集計フィールド {0} は、関連エンティティ {1} に属しません。|
> |**名前**:<br />RollupFieldsAggregateFieldNotBelongToSourceEntity<br />**16 進数**:<br />8006053f<br />**数値**:<br />-2147089089|集計フィールド {0} は、ソース エンティティ {1} に属しません。|
> |**名前**:<br />RollupFieldsAggregateFieldNotPartOfEntity<br />**16 進数**:<br />80060537<br />**数値**:<br />-2147089097|集計フィールド {0} は、エンティティ {1} に属しません。|
> |**名前**:<br />RollupFieldsAggregateFunctionTypeMismatch<br />**16 進数**:<br />8006053a<br />**数値**:<br />-2147089094|集計関数が {1} である場合、集計フィールドに対してデータの種類 {0} は許可されません。|
> |**名前**:<br />RollupFieldsAggregateNotDefined<br />**16 進数**:<br />80060536<br />**数値**:<br />-2147089098|ロールアップに対して集計関数と集計フィールドを提供する必要があります。|
> |**名前**:<br />RollupFieldsAggregateOnRollupFieldOrComplexCalcFieldNotAllowed<br />**16 進数**:<br />8006053c<br />**数値**:<br />-2147089092|集計フィールドは、単純なフィールドまたは基本計算フィールドのいずれかであることが必要です。|
> |**名前**:<br />RollupFieldsDataTypeNotValid<br />**16 進数**:<br />8006053e<br />**数値**:<br />-2147089090|データの種類 {0} は、ロールアップ フィールドに対して有効ではありません。|
> |**名前**:<br />RollupFieldsGeneric<br />**16 進数**:<br />8006053b<br />**数値**:<br />-2147089093|ロールアップ フィールドの定義が無効です。|
> |**名前**:<br />RollupFieldSourceFilterFieldNotAllowed<br />**16 進数**:<br />80060548<br />**数値**:<br />-2147089080|ソース エンティティのフィルターは、単純なフィールドまたは基本計算フィールドのいずれかであることが必要です。 ロールアップ フィールド、またはロールアップ フィールドを使用する計算フィールドは使用できません。|
> |**名前**:<br />RollupFieldsSourceEntityNotHierarchical<br />**16 進数**:<br />80060535<br />**数値**:<br />-2147089099|ソース エンティティ {0} 階層が存在しません。|
> |**名前**:<br />RollupFieldsSourceFilterConditionInvalid<br />**16 進数**:<br />80060538<br />**数値**:<br />-2147089096|ソース エンティティ {0} のフィルター条件 {1} が無効です。|
> |**名前**:<br />RollupFieldsTargetEntityNotValid<br />**16 進数**:<br />80060552<br />**数値**:<br />-2147089070|ロールアップでは関連エンティティ {0} は許可されません。|
> |**名前**:<br />RollupFieldsTargetFilterConditionInvalid<br />**16 進数**:<br />80060539<br />**数値**:<br />-2147089095|関連エンティティ {0} のフィルター条件 {1} が無効です。|
> |**名前**:<br />RollupFieldsTargetRelationshipNotPartOfOneToNRelationship<br />**16 進数**:<br />80060534<br />**数値**:<br />-2147089100|ソース エンティティ {1} から関連エンティティ {2} への 1:N の関係 {0} が存在しません。|
> |**名前**:<br />RollupFieldsTargetRelationshipNull<br />**16 進数**:<br />80060533<br />**数値**:<br />-2147089101|関連エンティティは空です。 ロールアップにソース エンティティ階層が使用されない場合には、関連エンティティを提供する必要があります。|
> |**名前**:<br />RollupFieldsTargetSameAsSourceEntity<br />**16 進数**:<br />80060551<br />**数値**:<br />-2147089071|ロールアップ フィールドでは自己参照の 1:N の関連付けは許可されません。|
> |**名前**:<br />RollupFieldsV2FeatureNotEnabled<br />**16 進数**:<br />80060565<br />**数値**:<br />-2147089051|この機能は、製品の現在のバージョンでサポートされていません。|
> |**名前**:<br />RollupFieldTargetFilterFieldNotAllowed<br />**16 進数**:<br />80060549<br />**数値**:<br />-2147089079|ターゲット エンティティのフィルターは、単純なフィールドまたは基本計算フィールドのいずれかであることが必要です。 ロールアップ フィールド、またはロールアップ フィールドを使用する計算フィールドは使用できません。|
> |**名前**:<br />RollupFormulaFieldInvalid<br />**16 進数**:<br />80060560<br />**数値**:<br />-2147089056|計算式フィールドが無効です。|
> |**名前**:<br />RollupInvalidAttributeForFilterCondition<br />**16 進数**:<br />80060564<br />**数値**:<br />-2147089052|属性が {0} の場合はフィルターの条件には許可されていません。|
> |**名前**:<br />RollupOrCalcNotAllowedInWorkflowWaitCondition<br />**16 進数**:<br />80060557<br />**数値**:<br />-2147089065|フィールド {0} は、ロールアップ フィールド、ロールアップ依存フィールド、計算フィールドのいずれかです。 このようなフィールドは、ワークフロー待機状態では許可されません。|
> |**名前**:<br />RollupTargetLinkedEntityCanOnlyUsedForActivityPartyEntities<br />**16 進数**:<br />80060563<br />**数値**:<br />-2147089053|エンティティと関連している対象を使用できるのは、{1} 種類エンティティに対するロールアップに対する {0} エンティティのみです。|
> |**名前**:<br />RollupTargetLinkedEntityOnlySupportedForActivityEntities<br />**16 進数**:<br />80060562<br />**数値**:<br />-2147089054|エンティティと関連している対象は {0} 種類エンティティに対するロールアップのみサポートされています。|
> |**名前**:<br />RollupTargetLinkedRelationshipNotValid<br />**16 進数**:<br />80060566<br />**数値**:<br />-2147089050|対象のリンクされた関連付け {0} 無効です。|
> |**名前**:<br />RootBusinessUnitCannotBeDisabled<br />**16 進数**:<br />80041d63<br />**数値**:<br />-2147213981|ルート部署を無効にすることはできません。|
> |**名前**:<br />RouterIsDisabled<br />**16 進数**:<br />8005E246<br />**数値**:<br />-2147098042|Microsoft Dynamics 365は、電子メールを処理するためサーバー側同期を使用するように構成されています。 このエラーは、一部のクライアントが依然として従来の電子メール ルーターを使用するように構成されているために発生します。 任意のサーバー上でインストールされていた電子メール ルーター クライアント アプリケーションをアンインストールする必要があります。|
> |**名前**:<br />RouteTypeUnsupported<br />**16 進数**:<br />800404e9<br />**数値**:<br />-2147220247|ルーティングの種類がサポートされていません。|
> |**名前**:<br />RoutingNotAllowed<br />**16 進数**:<br />800404e7<br />**数値**:<br />-2147220249|このオブジェクトの種類をルーティングすることはできません。|
> |**名前**:<br />RoutingRuleActivateDeactivateByNonOwner<br />**16 進数**:<br />8004F885<br />**数値**:<br />-2147157883|このルーティング規則セットをアクティブ化または非アクティブ化できるのは所有者だけです。|
> |**名前**:<br />RoutingRuleMissingRuleCriteria<br />**16 進数**:<br />8004F877<br />**数値**:<br />-2147157897|ルール アイテムで不足しているルール条件情報を解決しないと、このルールはアクティブ化できません。|
> |**名前**:<br />RoutingRulePublishedByNonOwner<br />**16 進数**:<br />8004F878<br />**数値**:<br />-2147157896|このルーティング規則セットを公開済みまたは非公開できるのは所有者だけです。|
> |**名前**:<br />RoutingRulePublishedByOwner<br />**16 進数**:<br />8004F876<br />**数値**:<br />-2147157898|現在のアクティブな規則が非アクティブ化されるまで規則をアクティブ化できません。 アクティブなルールは、ルール所有者によってのみ非アクティブ化することができます。|
> |**名前**:<br />RowGuidIsNotValidName<br />**16 進数**:<br />80047001<br />**数値**:<br />-2147192831|rowguid は予約名なので、識別子として使用できません|
> |**名前**:<br />RSCancelBatchError<br />**16 進数**:<br />8004831c<br />**数値**:<br />-2147187940|バッチ操作の取り消し中にエラーが発生しました。|
> |**名前**:<br />RSCreateBatchError<br />**16 進数**:<br />80048320<br />**数値**:<br />-2147187936|バッチ操作の作成中にエラーが発生しました。|
> |**名前**:<br />RSDeleteItemError<br />**16 進数**:<br />80048317<br />**数値**:<br />-2147187945|レポート サーバーからアイテムを削除中にエラーが発生しました。|
> |**名前**:<br />RSExecuteBatchError<br />**16 進数**:<br />8004831d<br />**数値**:<br />-2147187939|バッチ操作の実行中にエラーが発生しました。|
> |**名前**:<br />RSFindItemsError<br />**16 進数**:<br />80048318<br />**数値**:<br />-2147187944|レポート サーバーでアイテムを検索中にエラーが発生しました。|
> |**名前**:<br />RSGetDataSourceContentsError<br />**16 進数**:<br />8004831a<br />**数値**:<br />-2147187942|データ ソース コンテンツの取得中にエラーが発生しました。|
> |**名前**:<br />RSGetItemDataSourcesError<br />**16 進数**:<br />80048321<br />**数値**:<br />-2147187935|現在のデータ ソースのフェッチ中にエラーが発生しました。|
> |**名前**:<br />RSGetItemTypeError<br />**16 進数**:<br />8004832b<br />**数値**:<br />-2147187925|レポートのフェッチ中にエラーが発生しました。|
> |**名前**:<br />RSGetReportHistoryLimitError<br />**16 進数**:<br />8004831e<br />**数値**:<br />-2147187938|レポートで保存されているスナップショット数のフェッチ中にエラーが発生しました。|
> |**名前**:<br />RSGetReportParametersError<br />**16 進数**:<br />80048323<br />**数値**:<br />-2147187933|レポート パラメーターの取得中にエラーが発生しました。|
> |**名前**:<br />RSListExtensionsError<br />**16 進数**:<br />8004831b<br />**数値**:<br />-2147187941|レポート サーバーでインストールされたデータ拡張の一覧をフェッチ中にエラーが発生しました。|
> |**名前**:<br />RSListReportHistoryError<br />**16 進数**:<br />8004831f<br />**数値**:<br />-2147187937|レポート履歴スナップショットのフェッチ中にエラーが発生しました。|
> |**名前**:<br />RSMoveItemError<br />**16 進数**:<br />80048330<br />**数値**:<br />-2147187920|レポート項目 {0} を {1} に移動できません|
> |**名前**:<br />RSReportParameterTypeMismatchError<br />**16 進数**:<br />80048329<br />**数値**:<br />-2147187927|レポートのパラメーターの種類が無効です。|
> |**名前**:<br />RSSetDataSourceContentsError<br />**16 進数**:<br />80048319<br />**数値**:<br />-2147187943|データ ソース コンテンツの設定中にエラーが発生しました。|
> |**名前**:<br />RSSetExecutionOptionsError<br />**16 進数**:<br />80048325<br />**数値**:<br />-2147187931|実行オプションの設定中にエラーが発生しました。|
> |**名前**:<br />RSSetItemDataSourcesError<br />**16 進数**:<br />80048322<br />**数値**:<br />-2147187934|データ ソースの設定中にエラーが発生しました。|
> |**名前**:<br />RSSetPropertiesError<br />**16 進数**:<br />8004832a<br />**数値**:<br />-2147187926|レポートのプロパティ値の設定中にエラーが発生しました。|
> |**名前**:<br />RSSetReportHistoryLimitError<br />**16 進数**:<br />80048327<br />**数値**:<br />-2147187929|レポート履歴スナップショット制限の設定中にエラーが発生しました。|
> |**名前**:<br />RSSetReportHistoryOptionsError<br />**16 進数**:<br />80048326<br />**数値**:<br />-2147187930|レポート履歴スナップショット オプションの設定中にエラーが発生しました。|
> |**名前**:<br />RSSetReportParametersError<br />**16 進数**:<br />80048324<br />**数値**:<br />-2147187932|レポート パラメーターの設定中にエラーが発生しました。|
> |**名前**:<br />RSUpdateReportExecutionSnapshotError<br />**16 進数**:<br />80048328<br />**数値**:<br />-2147187928|レポートのスナップショットの取得中にエラーが発生しました。|
> |**名前**:<br />RuleActivationNotAllowedWithDeletedStages<br />**16 進数**:<br />80060014<br />**数値**:<br />-2147090412|削除されたステージまたはステージ カテゴリを含むために、このルールをアクティブ化できません。 ルールを修正してからやり直してください。|
> |**名前**:<br />RuleAlreadyExistsWithSameQueueAndChannel<br />**16 進数**:<br />8004F884<br />**数値**:<br />-2147157884|指定したチャネルおよびキューには、レコード作成ルールが既に存在します。 もう 1 つ作成することはできません。|
> |**名前**:<br />RuleAlreadyInactiveState<br />**16 進数**:<br />8004F852<br />**数値**:<br />-2147157934|このルーティング規則は既にアクティブ状態になっています。|
> |**名前**:<br />RuleAlreadyInDraftState<br />**16 進数**:<br />8004F853<br />**数値**:<br />-2147157933|下書きのルーティング規則を非アクティブ化することはできません。|
> |**名前**:<br />RuleAlreadyPublishing<br />**16 進数**:<br />80048434<br />**数値**:<br />-2147187660|選択した重複データ検出ルールは、既に公開処理中です。|
> |**名前**:<br />RuleCreationNotAllowedForCyclicReferences<br />**16 進数**:<br />80060012<br />**数値**:<br />-2147090414|循環参照を含むために、このルールを作成できません。 ルールを修正してからやり直してください。|
> |**名前**:<br />RuleNotFound<br />**16 進数**:<br />80048433<br />**数値**:<br />-2147187661|条件に一致するルールは見つかりませんでした。|
> |**名前**:<br />RuleNotSupportedForEditor<br />**16 進数**:<br />80060007<br />**数値**:<br />-2147090425|現在のルール定義は業務ルール エディターで編集することはできません。|
> |**名前**:<br />RulesInInconsistentStateFound<br />**16 進数**:<br />80048423<br />**数値**:<br />-2147187677|1 つまたは複数のルールは、現在公開処理中のため、または非公開にできない状態にあるために非公開にすることができません。|
> |**名前**:<br />RuntimeRibbonXmlValidation<br />**16 進数**:<br />8004F671<br />**数値**:<br />-2147158415|このページのタブの、カスタマイズされた最新のリボンを生成できません。 リボンのすぐに使用できるバージョンが、代わりに表示されます。|
> |**名前**:<br />S2SAccessTokenCannotBeAcquired<br />**16 進数**:<br />8005E243<br />**数値**:<br />-2147098045|承認サーバーから S2S アクセス トークンを取得するのに失敗しました。|
> |**名前**:<br />S2SNotConfigured<br />**16 進数**:<br />80044259<br />**数値**:<br />-2147204519|Office Graph の統合は、サーバー ベースの SharePoint 統合に依存します。 この機能を使用するには、サーバーベースの統合を有効にして、少なくとも 1 つのアクティブな SharePoint サイトがあることを確認してください。|
> |**名前**:<br />SalesOrderAndInvoiceCurrencyNotEqual<br />**16 進数**:<br />80048ced<br />**数値**:<br />-2147185427|レコードの通貨は、価格表の通貨に対応しません。|
> |**名前**:<br />SalesPeopleDuplicateCalendarNotAllowed<br />**16 進数**:<br />80043803<br />**数値**:<br />-2147207165|この営業担当者/年に対する会計カレンダーは既に存在しています|
> |**名前**:<br />SalesPeopleEmptyEffectiveDate<br />**16 進数**:<br />80043801<br />**数値**:<br />-2147207167|会計カレンダーの有効日は空にすることはできません|
> |**名前**:<br />SalesPeopleEmptySalesPerson<br />**16 進数**:<br />80043800<br />**数値**:<br />-2147207168|上位の営業担当者は空にすることはできません。|
> |**名前**:<br />SalesPeopleManagerNotAllowed<br />**16 進数**:<br />80043805<br />**数値**:<br />-2147207163|担当地域マネージャーが他の担当地域に属することはできません|
> |**名前**:<br />SandboxClientPluginTimeout<br />**16 進数**:<br />80044171<br />**数値**:<br />-2147204751|サンドボックス クライアントで操作がタイムアウトしたため、プラグイン実行に失敗しました。|
> |**名前**:<br />SandboxHostNotAvailable<br />**16 進数**:<br />8004418e<br />**数値**:<br />-2147204722|サンドボックス ホストが現在利用できないため、プラグイン実行に失敗しました。 構成されているサンドボックス サーバーが存在し、実行していることを確認してください。|
> |**名前**:<br />SandboxHostPluginTimeout<br />**16 進数**:<br />80044172<br />**数値**:<br />-2147204750|サンドボックス ホストで操作がタイムアウトしたため、プラグイン実行に失敗しました。|
> |**名前**:<br />SandboxPluginDisabled<br />**16 進数**:<br />80081115<br />**数値**:<br />-2146954987|サンドボックス プラグインの実行が無効です。|
> |**名前**:<br />SandboxSdkListenerStartFailed<br />**16 進数**:<br />80044174<br />**数値**:<br />-2147204748|サンドボックス クライアントで初期化中にエラーが発生したため、プラグイン実行に失敗しました。|
> |**名前**:<br />SandboxWorkerNotAvailable<br />**16 進数**:<br />8004418d<br />**数値**:<br />-2147204723|サンドボックス ワーカー プロセスが現在利用できないため、プラグイン実行に失敗しました。 やり直してください。|
> |**名前**:<br />SandboxWorkerPluginExecuteTimeout<br />**16 進数**:<br />80081111<br />**数値**:<br />-2146954991|2 分 20 秒の制限以内に {0} プラグインからの反応を受け取りませんでした。|
> |**名前**:<br />SandboxWorkerPluginTimeout<br />**16 進数**:<br />80044173<br />**数値**:<br />-2147204749|サンドボックス ワーカーで操作がタイムアウトしたため、プラグイン実行に失敗しました。|
> |**名前**:<br />SandboxWorkerThrottleLimit<br />**16 進数**:<br />80081116<br />**数値**:<br />-2146954986|プラグイン ビジネス ロジックに割り当てられた最大プロセス数を超えました。 この環境のプラグインで致命的なエラーが過去 {1} 分間に {0} 回発生しました。 各エラーを回復するには追加のプロセスが必要です。 プラグインのプロセスがリサイクルされています。 この期間中、この環境のすべてのプラグインは失敗します。 詳細: https://go.microsoft.com/fwlink/?linkid=2038718 |
> |**名前**:<br />SaveAsDraftAppointmentNotAllowed<br />**16 進数**:<br />8004026b<br />**数値**:<br />-2147220885|AllowSaveAsDraftAppointment が無効に設定されます。|
> |**名前**:<br />SaveDataFileErrorOutOfSpace<br />**16 進数**:<br />8005F209<br />**数値**:<br />-2147094007|このアクションをやり直してください。 問題が解決しない場合は、ソリューションの {0} を確認するか、{#Brand_CRM} 管理者に問い合わせてください。 それでも解決しない場合には {1}に問い合わせてください。|
> |**名前**:<br />SavedQueryIsNotCustomizable<br />**16 進数**:<br />80047017<br />**数値**:<br />-2147192809|指定されたビューがカスタマイズ可能ではありません。|
> |**名前**:<br />SavedQueryValidationError<br />**16 進数**:<br />800609A0<br />**数値**:<br />-2147087968|プロファイル {0} を公開できません。プロファイル項目 {1} の保存済みクエリ {3} に、このプロファイルの一部ではないエンティティ {2} があります。|
> |**名前**:<br />SavePending<br />**16 進数**:<br />80060913<br />**数値**:<br />-2147088109|保存操作はすでにバックグラウンドで実行されています。|
> |**名前**:<br />SaveRecordBeforeAddingBundle<br />**16 進数**:<br />8004F983<br />**数値**:<br />-2147157629|価格表を選択した後、オプション製品のバンドルを追加する前に、レコードを保存しておく必要があります。|
> |**名前**:<br />ScaleGroupDisabled<br />**16 進数**:<br />8004A107<br />**数値**:<br />-2147180281|指定した scalegroup は無効になっています。 この scalegroup で組織にアクセスするのは許可されていません。|
> |**名前**:<br />SchedulingFailedForBookingValidation<br />**16 進数**:<br />80060915<br />**数値**:<br />-2147088107|予約検証により、予約またはスケジュール変更の機能が失敗しました。|
> |**名前**:<br />SchedulingFailedForInvalidData<br />**16 進数**:<br />80060914<br />**数値**:<br />-2147088108|無効なデータにより、予約またはスケジュール変更の機能が失敗しました。|
> |**名前**:<br />SchemaNameContainsNonAlphaNumericCharacters<br />**16 進数**:<br />80044364<br />**数値**:<br />-2147204252|種類 {2} の識別子 {0} で使用できるのは英数字とアンダースコア (_) のみです。|
> |**名前**:<br />SchemaNameisNotUnique<br />**16 進数**:<br />80044363<br />**数値**:<br />-2147204253|種類 {1} のスキーマ名 {0} は一意ではありません。 同じ名前の {0} が既に存在します。|
> |**名前**:<br />SchemaNameLengthExceedsLimit<br />**16 進数**:<br />80044367<br />**数値**:<br />-2147204249|識別子の長さは {1} 文字を超えることはできません。 種類 {2} に提供されたスキーマ名 {0} の長さが、最大長 {1} 文字を超えています。|
> |**名前**:<br />SchemaNameMatchesExistingIdentifier<br />**16 進数**:<br />80044361<br />**数値**:<br />-2147204255|識別子は既存のオブジェクト名と一致できません。 同じ名前 {0} を持つ種類 {1} のオブジェクトが既に存在します。|
> |**名前**:<br />SchemaNameMatchesReservedSqlKeywords<br />**16 進数**:<br />80044362<br />**数値**:<br />-2147204254|識別子は予約済み SQL キーワードと一致できません。 種類 {1} の提供された名前: {0} がキーワード: {2} に一致します。|
> |**名前**:<br />SchemaNameNotStartwithLetter<br />**16 進数**:<br />80044365<br />**数値**:<br />-2147204251|識別子は文字から始める必要があります。 種類 {2} のスキーマ名 {0} が文字から始まっていません。|
> |**名前**:<br />ScopeNotSetToGlobal<br />**16 進数**:<br />80060403<br />**数値**:<br />-2147089405|スコープは、ビジネス プロセス フローのカテゴリの作成時に [グローバル] に設定されている必要があります|
> |**名前**:<br />SdkCorrelationTokenDepthTooHigh<br />**16 進数**:<br />80044182<br />**数値**:<br />-2147204734|このワークフロー ジョブは、それを開始したワークフローに無限ループが含まれているため、取り消されました。 ワークフロー ロジックツールを修正して、もう一度やり直してください。 ワークフロー ロジックに関する詳細ついては、[ヘルプ] を参照してください。|
> |**名前**:<br />SdkCustomProcessingStepIsNotAllowed<br />**16 進数**:<br />80044187<br />**数値**:<br />-2147204729|カスタム SdkMessageProcessingStep は、指定されたメッセージおよびエンティティで許可されていません。|
> |**名前**:<br />SdkEntityDoesNotSupportMessage<br />**16 進数**:<br />80040800<br />**数値**:<br />-2147219456|呼び出されているメソッドは、指定されたエンティティの種類をサポートしません。|
> |**名前**:<br />SdkEntityOfflineQueuePlaybackIsNotAllowed<br />**16 進数**:<br />80044188<br />**数値**:<br />-2147204728|エンティティ '{0}' はオフライン キューの再生で許可されていません。|
> |**名前**:<br />SdkInvalidMessagePropertyName<br />**16 進数**:<br />8004416b<br />**数値**:<br />-2147204757|Message のプロパティ名は '{0}' Message 上では有効ではありません {1}。|
> |**名前**:<br />SdkMessageDoesNotSupportImageRegistration<br />**16 進数**:<br />80044189<br />**数値**:<br />-2147204727|Message '{0}' は画像の登録をサポートしていません。|
> |**名前**:<br />SdkMessageDoesNotSupportPostImageRegistration<br />**16 進数**:<br />8004416e<br />**数値**:<br />-2147204754|PreEvent ステップの登録はポスト イメージをサポートしていません。|
> |**名前**:<br />SdkMessageInvalidImageTypeRegistration<br />**16 進数**:<br />8004416d<br />**数値**:<br />-2147204755|Message {0} はこの画像の種類をサポートしていません。|
> |**名前**:<br />SdkMessageNotImplemented<br />**16 進数**:<br />80044824<br />**数値**:<br />-2147203036|SDK メッセージが実装されていません。|
> |**名前**:<br />SdkMessageNotSupportedOnClient<br />**16 進数**:<br />80044181<br />**数値**:<br />-2147204735|要求されたメッセージは、クライアントではサポートされません。|
> |**名前**:<br />SdkMessageNotSupportedOnServer<br />**16 進数**:<br />80044180<br />**数値**:<br />-2147204736|要求されたメッセージは、サーバーではサポートされません。|
> |**名前**:<br />SdkMessagesDeprecatedError<br />**16 進数**:<br />8004F903<br />**数値**:<br />-2147157757|このメッセージは現在利用できません。 代替メッセージに関する SDK を参照してください。|
> |**名前**:<br />SdkNotEnoughPrivilegeToSetCallerOriginToken<br />**16 進数**:<br />80044309<br />**数値**:<br />-2147204343|呼び出し元には、指定した値に CallerOriginToken を設定するための権限がありません。|
> |**名前**:<br />SearchTextLenExceeded<br />**16 進数**:<br />800401ff<br />**数値**:<br />-2147220993|検索文字列が長すぎます。|
> |**名前**:<br />SelectedFileNotFound<br />**16 進数**:<br />80071025<br />**数値**:<br />-2147020763|ドキュメントをコピーできません。 ソース ファイルは存在しません。|
> |**名前**:<br />SeriesMeasureCollectionMismatch<br />**16 進数**:<br />8004E003<br />**数値**:<br />-2147164157|グラフ エリアの系列の数は、カテゴリのメジャー コレクションの数に等しくする必要があります。|
> |**名前**:<br />ServerLocationAndSSLSetToYes<br />**16 進数**:<br />8005E255<br />**数値**:<br />-2147098027|サーバーの場所に指定された URL では HTTP が使用されていますが、Exchange Online に対しては Secure Sockets Layer(SSL) が必要です。|
> |**名前**:<br />ServerLocationIsEmpty<br />**16 進数**:<br />8005E250<br />**数値**:<br />-2147098032|サーバーの場所 フィールドは空にできません|
> |**名前**:<br />ServiceAccountMailboxesCountIsGreaterThanOne<br />**16 進数**:<br />8005E24A<br />**数値**:<br />-2147098038|より多くのサービス アカウント メールボックスが電子メール サーバー プロファイルに関連付けられています。|
> |**名前**:<br />ServiceAccountMailboxesCountIsZero<br />**16 進数**:<br />8005E249<br />**数値**:<br />-2147098039|電子メール サーバー プロファイルに関連付けられてるサービス アカウント メールボックスはありません。|
> |**名前**:<br />ServiceBusEndpointNotConfigured<br />**16 進数**:<br />80081112<br />**数値**:<br />-2146954990|メッセージを送信する前に、必要な資格情報の構成を完了している必要があります。|
> |**名前**:<br />ServiceBusExtendedTokenFailed<br />**16 進数**:<br />80044178<br />**数値**:<br />-2147204744|サービス バスの送信の追加トークンが取得できませんでした。|
> |**名前**:<br />ServiceBusIssuerCertificateError<br />**16 進数**:<br />80044177<br />**数値**:<br />-2147204745|サービス統合発行者証明書エラー。|
> |**名前**:<br />ServiceBusIssuerNotFound<br />**16 進数**:<br />80044176<br />**数値**:<br />-2147204746|サービス統合発行者の情報が見つかりませんでした。|
> |**名前**:<br />ServiceBusMaxSizeExceeded<br />**16 進数**:<br />80050208<br />**数値**:<br />-2147155448|要求ペイロードが最大許容サイズを超えたため、サービス バス呼び出しが失敗しました。 要求のサイズを小さくしてから再試行してください。|
> |**名前**:<br />ServiceBusPostDisabled<br />**16 進数**:<br />8004417A<br />**数値**:<br />-2147204742|サービス バスの投稿は組織では無効です。|
> |**名前**:<br />ServiceBusPostFailed<br />**16 進数**:<br />80044175<br />**数値**:<br />-2147204747|サービス バス ポストに失敗しました。|
> |**名前**:<br />ServiceBusPostPostponed<br />**16 進数**:<br />80044179<br />**数値**:<br />-2147204743|サービス バスの投稿は延期されています。|
> |**名前**:<br />ServiceEndpointAcsAuthNotSupported<br />**16 進数**:<br />80050209<br />**数値**:<br />-2147155447|ACS 認証の種類のサービス エンドポイント はサポートされなくなりました。 サポートされている認証の種類を使用するようにエンドポイント構成を変更してください|
> |**名前**:<br />ServiceInstantiationFailed<br />**16 進数**:<br />80040244<br />**数値**:<br />-2147220924|エンティティのインスタンス化に失敗しました。|
> |**名前**:<br />SessionTokenUnavailable<br />**16 進数**:<br />80040253<br />**数値**:<br />-2147220909|トランザクションが存在する場合を除いて、セッション トークンは使用できません。|
> |**名前**:<br />SetActiveNotSupportedOnNewRecords<br />**16 進数**:<br />80060374<br />**数値**:<br />-2147089548|新しいレコードに対して SetActiveProcess はサポートされていません。|
> |**名前**:<br />SharePointAbsoluteAndRelativeUrlEmpty<br />**16 進数**:<br />80048149<br />**数値**:<br />-2147188407|絶対 URL も相対 URL も NULL にできません。|
> |**名前**:<br />SharePointAuthenticationFailure<br />**16 進数**:<br />800608B3<br />**数値**:<br />-2147088205|Microsoft Dynamics 365 は、このユーザー {0} を認証できません。 このユーザーについての情報が正しいことを確認して、もう一度やり直してください。|
> |**名前**:<br />SharePointAuthorizationFailure<br />**16 進数**:<br />800608B4<br />**数値**:<br />-2147088204|Microsoft Dynamics 365 は、このユーザー {0} を承認できません。 このユーザーについての情報が正しいことを確認して、もう一度やり直してください。|
> |**名前**:<br />SharePointCertificateExpired<br />**16 進数**:<br />800608B1<br />**数値**:<br />-2147088207|SharePoint 検証に使用する証明書が期限切れになりました|
> |**名前**:<br />SharePointConnectionFailure<br />**16 進数**:<br />800608B5<br />**数値**:<br />-2147088203|Microsoft Dynamics 365 は、このユーザー {0} を SharePoint に接続できません。 このユーザーについての情報が正しく、SharePoint に存在していることを確認して、もう一度やり直してください。|
> |**名前**:<br />SharePointCrmDomainValidator<br />**16 進数**:<br />8004F302<br />**数値**:<br />-2147159294|SharePoint と Microsoft Dynamics 365 Server は異なるドメインにあります。 2 つのドメイン間の信頼関係を確認してください。|
> |**名前**:<br />SharePointCrmGridIsInstalledValidator<br />**16 進数**:<br />8004F309<br />**数値**:<br />-2147159287|Microsoft Dynamics 365 グリッド コンポーネントを SharePoint Server にインストールする必要があります。 このコンポーネントは、SharePoint 統合が正しく機能するために必要です。|
> |**名前**:<br />SharePointErrorAbsoluteUrlClipped<br />**16 進数**:<br />8004F314<br />**数値**:<br />-2147159276|URL が最大の長さである 256 文字を超えています。 より短い名前をサイトおよびフォルダに使用してから、もう一度やり直してください。|
> |**名前**:<br />SharePointErrorRetrieveAbsoluteUrl<br />**16 進数**:<br />8004F310<br />**数値**:<br />-2147159280|SharePoint オブジェクトの絶対 URL およびサイト コレクション URL を取得するときに、エラーが発生しました。|
> |**名前**:<br />SharePointInvalidEntityForValidation<br />**16 進数**:<br />8004F311<br />**数値**:<br />-2147159279|エンティティは、SharePoint URL 検証をサポートしていません。|
> |**名前**:<br />SharePointRealmMismatch<br />**16 進数**:<br />800608B2<br />**数値**:<br />-2147088206|入力された SharePoint 領域 ID は登録された SharePoint 側の領域と一致しません。|
> |**名前**:<br />SharePointRecordWithDuplicateUrl<br />**16 進数**:<br />80048057<br />**数値**:<br />-2147188649|既に同じ URL を使用しているレコードがあります。|
> |**名前**:<br />SharePointRoleProvisionJobAlreadyExists<br />**16 進数**:<br />8004F0FA<br />**数値**:<br />-2147159814|指定したセキュリティ ロールを準備するシステム ジョブが保留になっています。 セキュリティ ロール レコードに対して、このシステム ジョブを開始する前に加えられたどんな変更も、このシステム ジョブに適用されます。|
> |**名前**:<br />SharePointS2SIsDisabled<br />**16 進数**:<br />80071017<br />**数値**:<br />-2147020777|SharePoint サーバーベースの SharePoint 統合が有効になっていません。|
> |**名前**:<br />SharePointServerDiscoveryValidator<br />**16 進数**:<br />8004F303<br />**数値**:<br />-2147159293|URL が正しくないか、サイトが実行されていません。|
> |**名前**:<br />SharePointServerLanguageValidator<br />**16 進数**:<br />8004F308<br />**数値**:<br />-2147159288|Microsoft Dynamics 365 と Microsoft Office SharePoint サーバーの基本言語が異なっています。|
> |**名前**:<br />SharePointServerVersionValidator<br />**16 進数**:<br />8004F304<br />**数値**:<br />-2147159292|SharePoint サイト コレクションは、サポートされているバージョンの Microsoft Office SharePoint サーバーまたは Microsoft Windows SharePoint サービスを実行している必要があります。 実装ガイドを参照してください。|
> |**名前**:<br />SharePointSiteCollectionIsAccessibleValidator<br />**16 進数**:<br />8004F305<br />**数値**:<br />-2147159291|URL が正しくないか、サイトが実行されていません。|
> |**名前**:<br />SharePointSiteCreationFailure<br />**16 進数**:<br />8004F0F8<br />**数値**:<br />-2147159816|SharePoint のサイト {0} を作成できませんでした。|
> |**名前**:<br />SharePointSiteNotConfigured<br />**16 進数**:<br />80071014<br />**数値**:<br />-2147020780|SharePointSite が構成されていません。構成する必要があります。|
> |**名前**:<br />SharePointSiteNotPresentInSharePoint<br />**16 進数**:<br />8004F0F3<br />**数値**:<br />-2147159821|サイト {0} が SharePoint に存在しません。|
> |**名前**:<br />SharePointSitePermissionsValidator<br />**16 進数**:<br />8004F307<br />**数値**:<br />-2147159289|現在のユーザーには適切な特権がありません。 SharePoint サイトで SharePoint サイト管理者である必要があります。|
> |**名前**:<br />SharePointSiteWideProvisioningJobFailed<br />**16 進数**:<br />8004F0FB<br />**数値**:<br />-2147159813|SharePoint のプロビジョニング ジョブが失敗しました。|
> |**名前**:<br />SharePointTeamProvisionJobAlreadyExists<br />**16 進数**:<br />8004F0F9<br />**数値**:<br />-2147159815|指定したセキュリティ ロールを準備するチームが保留になっています。 チーム レコードに対して、このシステム ジョブを開始する前に加えられたどんな変更も、このシステム ジョブに適用されます。|
> |**名前**:<br />SharePointUnableToAclSite<br />**16 進数**:<br />8004F0F6<br />**数値**:<br />-2147159818|SharePoint の ACL サイト {0} にアクセスできません。|
> |**名前**:<br />SharePointUnableToAclSiteWithPrivilege<br />**16 進数**:<br />8004F0F5<br />**数値**:<br />-2147159819|SharePoint の ACL サイト {0} に特権 {1} でアクセスできません。|
> |**名前**:<br />SharePointUnableToAddUserToGroup<br />**16 進数**:<br />8004F0F1<br />**数値**:<br />-2147159823|Microsoft Dynamics 365 は SharePoint でグループ {1} にこのユーザー {0} を追加できません。 このユーザーとグループについての情報が正しく、SharePoint にそのグループが存在していることを確認して、もう一度やり直してください。|
> |**名前**:<br />SharePointUnableToCreateSiteGroup<br />**16 進数**:<br />8004F0F7<br />**数値**:<br />-2147159817|SharePoint でサイト グループ {0} を作成できません。|
> |**名前**:<br />SharePointUnableToRemoveUserFromGroup<br />**16 進数**:<br />8004F0F2<br />**数値**:<br />-2147159822|SharePoint のグループ {1} からユーザー {0} を削除できません。|
> |**名前**:<br />SharePointUnableToRetrieveGroup<br />**16 進数**:<br />8004F0F4<br />**数値**:<br />-2147159820|SharePoint からグループ {0} を取得できません。|
> |**名前**:<br />SharePointUrlHostValidator<br />**16 進数**:<br />8004F301<br />**数値**:<br />-2147159295|URL を IP に解決できません。|
> |**名前**:<br />SharePointUrlIsRootWebValidator<br />**16 進数**:<br />8004F306<br />**数値**:<br />-2147159290|無効な URL です。 URL は有効なサイト コレクションである必要があり、サブサイトを含めることはできません。 URL は http://SharePointServer/sites/CrmSite などの、有効な形式である必要があります。|
> |**名前**:<br />SharePointVersionUnsupported<br />**16 進数**:<br />800608B6<br />**数値**:<br />-2147088202|Sharepoint バージョンがサポートされていないため、Microsoft Dynamics 365 は Sharepoint に接続できません。 正しいバージョンをインストールし、もう一度実行してください。 |
> |**名前**:<br />SimilarityRuleDisabled<br />**16 進数**:<br />80071016<br />**数値**:<br />-2147020778|このエンティティでアクティブな類似ルールはありません。|
> |**名前**:<br />SimilarityRuleFCBOff<br />**16 進数**:<br />80071018<br />**数値**:<br />-2147020776|類似ルールが有効になっていません。|
> |**名前**:<br />SingletonMappingFoundForArrayParameter<br />**16 進数**:<br />8004037e<br />**数値**:<br />-2147220610|単一の変換パラメーター マッピングは、配列パラメーター用に定義されます。|
> |**名前**:<br />SiteMapMissing<br />**16 進数**:<br />80050016<br />**数値**:<br />-2147155946|これらのレコードに対するアクセス許可がないか、サイト マップに問題がある可能性があります。 システム管理者にお問い合わせください。管理者であれば、ソリューション ページに移動して別のソリューションをインポートできます。|
> |**名前**:<br />SiteMapXsdValidationError<br />**16 進数**:<br />8004F401<br />**数値**:<br />-2147159039|サイトマップ XML は XSD 検証で次のエラーで失敗しました: '{0}' ライン {1} ポジション {2}。|
> |**名前**:<br />SkipValidDateTimeBehavior<br />**16 進数**:<br />800608A3<br />**数値**:<br />-2147088221|このフィールドの動作値は無視されました。 システム カスタマイザーは、このフィールドの動作値を直接構成する必要があります。|
> |**名前**:<br />SlaActivateDeactivateByNonOwner<br />**16 進数**:<br />8004F872<br />**数値**:<br />-2147157902|この SLA をアクティブ化または非アクティブ化できるのは所有者だけです。|
> |**名前**:<br />SlaAlreadyInactiveState<br />**16 進数**:<br />8004F861<br />**数値**:<br />-2147157919|このレコードは既にアクティブなため、アクティブ化することはできません。|
> |**名前**:<br />SlaAlreadyInDraftState <br />**16 進数**:<br />8004F862<br />**数値**:<br />-2147157918|このレコードは下書き状態のため、非アクティブ化できません。|
> |**名前**:<br />SlaNotEnabledEntity<br />**16 進数**:<br />80055003<br />**数値**:<br />-2147135485|SLA はこのエンティティでは有効ではありません。|
> |**名前**:<br />SlaPermissionToPerformAction<br />**16 進数**:<br />8004F875<br />**数値**:<br />-2147157899|SLA およびプロセスに対してこの操作を実行するために必要なアクセス許可がありません。|
> |**名前**:<br />SnapshotReportNotReady<br />**16 進数**:<br />80040489<br />**数値**:<br />-2147220343|指定されたレポートは、表示できる状態になっていません。 レポートがまだ作成中か、レポート スナップショットが使用できません。 ReportId:{0}|
> |**名前**:<br />SocialCareDisabledError<br />**16 進数**:<br />80060621<br />**数値**:<br />-2147088863|Dynamics 365 組織との通信に問題があります。 組織は利用できない、または機能が設定されており、ソーシャル データを受信できないようになっています。 後でもう一度試してみてください。 問題が解決しない場合は、Microsoft Dynamics 365 管理者に問い合わせてください。|
> |**名前**:<br />SolutionConcurrencyFailure<br />**16 進数**:<br />80071151<br />**数値**:<br />-2147020463|ソリューションのインストールまたは削除が失敗しました。別のソリューションのインストールまたは削除が同時に行われていることが原因です。 後でやり直してください。|
> |**名前**:<br />SolutionConfigurationPageMustBeHtmlWebResource<br />**16 進数**:<br />8004701C<br />**数値**:<br />-2147192804|ソリューション構成ページは、対応するソリューション内に存在する必要があります。|
> |**名前**:<br />SolutionImportCauseTimeout<br />**16 進数**:<br />80048543<br />**数値**:<br />-2147187389|操作がタイムアウトしました。考えられる原因はソリューションが現在この環境にインポートされているからです。 ソリューションのインポートが完了した後にもう一度やり直してください。 可能な場合はソリューションを作業時間外にインポートする必要があります。|
> |**名前**:<br />SolutionRestrictedAttributes<br />**16 進数**:<br />80072003<br />**数値**:<br />-2147016701|ソリューション対応列がすでにあるため、コンポーネントを作成できません。 エンティティ: {0}、既存の属性: {1}|
> |**名前**:<br />SolutionUniqueNameViolation<br />**16 進数**:<br />8004F023<br />**数値**:<br />-2147160029|ソリューションの一意の名前 '{0}' は既に使用されており、再び使用することはできません。|
> |**名前**:<br />SolutionUpgradeFailed<br />**16 進数**:<br />8004F046<br />**数値**:<br />-2147159994|保留としてインポートした後、ソリューションのアップグレード操作が失敗しました。 InnerException は次のとおりです: {1}。|
> |**名前**:<br />SolutionUpgradeNotAvailable<br />**16 進数**:<br />8004853B<br />**数値**:<br />-2147187397|" {0} ソリューションには、適用できるアップグレードがありません。"|
> |**名前**:<br />SolutionUpgradeWrongSolutionSelected<br />**16 進数**:<br />8004853C<br />**数値**:<br />-2147187396|"このアクションを使用するには、最初に古いソリューションを選択してからやり直してください。"|
> |**名前**:<br />SourceAttributeHeaderTooBig<br />**16 進数**:<br />80044340<br />**数値**:<br />-2147204288|列見出しは 160 文字以内にする必要があります。 列見出しを修正し、データ移行マネージャを再度実行します。|
> |**名前**:<br />SourceEntityMappedToMultipleTargets<br />**16 進数**:<br />8004033d<br />**数値**:<br />-2147220675|このソース エンティティは複数の Microsoft Dynamics 365 エンティティにマッピングされています。 重複するマッピングを削除してから、もう一度このデータ マップをインポートしてください。|
> |**名前**:<br />SPAccountNameFetchFailure<br />**16 進数**:<br />8006072A<br />**数値**:<br />-2147088598|SharePoint から取引先企業名をフェッチ中に例外が発生しました。|
> |**名前**:<br />SPAllFilesErrorScenario<br />**16 進数**:<br />80060760<br />**数値**:<br />-2147088544|SharePointDocument のすべてのファイル ビューの 1 つまたは複数のサイトが失敗しました。|
> |**名前**:<br />SPBadLockInFileCollectionErrorCode<br />**16 進数**:<br />8006070A<br />**数値**:<br />-2147088630|コレクション内のファイルのロックが適切ではありません |
> |**名前**:<br />SPCertificationError<br />**16 進数**:<br />80060767<br />**数値**:<br />-2147088537|S2STokenIssuer の証明書が見つかりません。|
> |**名前**:<br />SPConnectionFailure<br />**16 進数**:<br />80060761<br />**数値**:<br />-2147088543|SharePointSite に接続できませんでした。|
> |**名前**:<br />SPCurrentDocumentLocationDisabledErrorCode<br />**16 進数**:<br />80060720<br />**数値**:<br />-2147088608|現在のドキュメントの場所は、管理者により無効になっています|
> |**名前**:<br />SPCurrentFolderAlreadyExistErrorCode<br />**16 進数**:<br />80060721<br />**数値**:<br />-2147088607|レコードはすでに db に存在します|
> |**名前**:<br />SPDataValidationFiledOnFieldAndListErrorCode<br />**16 進数**:<br />80060713<br />**数値**:<br />-2147088621|フィールドおよびリストでデータ検証に失敗しました|
> |**名前**:<br />SPDataValidationFiledOnFieldErrorCode<br />**16 進数**:<br />80060711<br />**数値**:<br />-2147088623|フィールドでデータ検証に失敗しました|
> |**名前**:<br />SPDataValidationFiledOnListErrorCode<br />**16 進数**:<br />80060712<br />**数値**:<br />-2147088622|リストでデータ検証に失敗しました|
> |**名前**:<br />SPDefaultSiteNotPresent<br />**16 進数**:<br />80060739<br />**数値**:<br />-2147088583|OneDrive のアクティブ化には既定の SharePoint サイトが必要です。|
> |**名前**:<br />SPDocumentMappingFailure<br />**16 進数**:<br />80060734<br />**数値**:<br />-2147088588|ドキュメントの場所にはドキュメントをマップできません。|
> |**名前**:<br />SPDuplicateValuesFoundErrorCode<br />**16 進数**:<br />80060708<br />**数値**:<br />-2147088632|リスト内の 1 つまたは複数のフィールドで重複する値が見つかったため、リスト アイテムを更新できませんでした|
> |**名前**:<br />SpecifyIncomingPassword<br />**16 進数**:<br />8005E253<br />**数値**:<br />-2147098029|受信接続のパスワードを指定してください|
> |**名前**:<br />SpecifyInComingPort<br />**16 進数**:<br />8005E24F<br />**数値**:<br />-2147098033|受信ポートを指定して保存し直してください|
> |**名前**:<br />SpecifyIncomingServerLocation<br />**16 進数**:<br />8005E24B<br />**数値**:<br />-2147098037|受信サーバーの場所を表す URL を指定します|
> |**名前**:<br />SpecifyIncomingUserName<br />**16 進数**:<br />8005E251<br />**数値**:<br />-2147098031|受信接続のユーザー名を指定してください|
> |**名前**:<br />SpecifyOutgoingPassword<br />**16 進数**:<br />8005E254<br />**数値**:<br />-2147098028|送信接続のパスワードを指定してください|
> |**名前**:<br />SpecifyOutgoingPort<br />**16 進数**:<br />8005E256<br />**数値**:<br />-2147098026|送信ポートを指定して保存し直してください|
> |**名前**:<br />SpecifyOutgoingServerLocation<br />**16 進数**:<br />8005E24C<br />**数値**:<br />-2147098036|送信サーバーの場所を表す URL を指定します|
> |**名前**:<br />SpecifyOutgoingUserName<br />**16 進数**:<br />8005E252<br />**数値**:<br />-2147098030|送信接続のユーザー名を指定してください|
> |**名前**:<br />SPExclusiveLockOnFileErrorCode<br />**16 進数**:<br />80060705<br />**数値**:<br />-2147088635|ファイルの排他ロックです|
> |**名前**:<br />SPFileAlreadyCheckedOutErrorCode<br />**16 進数**:<br />80060702<br />**数値**:<br />-2147088638|ファイルは既にチェックアウトされています|
> |**名前**:<br />SPFileCheckedOutInvalidArgsErrorCode<br />**16 進数**:<br />80060703<br />**数値**:<br />-2147088637|チェックアウトの引数が無効です|
> |**名前**:<br />SPFileContentNullErrorCode<br />**16 進数**:<br />8006070D<br />**数値**:<br />-2147088627|ファイルの作成情報の内容は、null にしないでください|
> |**名前**:<br />SPFileIsCheckedOutByOtherUser<br />**16 進数**:<br />80060728<br />**数値**:<br />-2147088600|ファイルは、現在のユーザー以外のユーザーにチェックアウトされています|
> |**名前**:<br />SPFileIsReadOnlyErrorCode<br />**16 進数**:<br />8006070F<br />**数値**:<br />-2147088625|フィールドが読み取り専用|
> |**名前**:<br />SPFileNameModifiedErrorCode<br />**16 進数**:<br />80060729<br />**数値**:<br />-2147088599|フォルダーが見つかりません。 このドキュメントの場所として SharePoint で自動生成されたフォルダー名を変更した場合は、名前を変更したフォルダーに合わせて、Dynamics 365 でフォルダー名を変更する必要があります。 これを行うには、[場所の変更] をクリックし、一致する名前を [フォルダー名] フィールドに入力してください。|
> |**名前**:<br />SPFileNotCheckedOutErrorCode<br />**16 進数**:<br />80060700<br />**数値**:<br />-2147088640|ファイルはチェックアウトされていません|
> |**名前**:<br />SPFileNotFoundErrorCode<br />**16 進数**:<br />80060706<br />**数値**:<br />-2147088634|ファイルが見つかりません|
> |**名前**:<br />SPFileNotLockedErrorCode<br />**16 進数**:<br />80060707<br />**数値**:<br />-2147088633|コレクション内のファイルがロックされていません|
> |**名前**:<br />SPFileSizeMismatchErrorCode<br />**16 進数**:<br />8006070E<br />**数値**:<br />-2147088626|書き込まれたドキュメント ストリームのサイズと入力ドキュメント ストリームのサイズが一致しません|
> |**名前**:<br />SPFileTooLargeOrInfectedErrorCode<br />**16 進数**:<br />80060709<br />**数値**:<br />-2147088631|ウイルス チェックにより、ファイルがウイルスに感染しているか、ファイルが大きすぎることが示されています|
> |**名前**:<br />SPFolderCreationFailure<br />**16 進数**:<br />8004F0F0<br />**数値**:<br />-2147159824|この名前でフォルダを作成できません|
> |**名前**:<br />SPFolderNotFoundErrorCode<br />**16 進数**:<br />8006071B<br />**数値**:<br />-2147088613|フォルダーは見つかりませんでした|
> |**名前**:<br />SPFolderRenameFailure<br />**16 進数**:<br />8006072C<br />**数値**:<br />-2147088596|SharePoint のドキュメント プロパティの編集中に例外が発生しました。|
> |**名前**:<br />SPGenericErrorCode<br />**16 進数**:<br />80060719<br />**数値**:<br />-2147088615|SharePoint でこの操作を実行中にエラーが発生しました|
> |**名前**:<br />SPIllegalCharactersInFileNameErrorCode<br />**16 進数**:<br />8006071F<br />**数値**:<br />-2147088609|ファイル名に無効な文字|
> |**名前**:<br />SPIllegalFileTypeErrorCode<br />**16 進数**:<br />8006071D<br />**数値**:<br />-2147088611|無効なファイルの種類|
> |**名前**:<br />SPInstanceOfRecurringEventErrorCode<br />**16 進数**:<br />80060716<br />**数値**:<br />-2147088618|リスト アイテムは、繰り返しの例外でない定期的なイベントのインスタンスであり、親ワークフローがごみ箱にあるか、親リストがドキュメント ライブラリにあるワークフロー タスクです|
> |**名前**:<br />SPIntermittentError<br />**16 進数**:<br />80060764<br />**数値**:<br />-2147088540|断続的にエラーが発生しました。 グリッドを最新の情報に更新して、やり直してください。|
> |**名前**:<br />SPInvalidDocumentLocation<br />**16 進数**:<br />80060762<br />**数値**:<br />-2147088542|Sharepoint ドキュメントの場所の種類が無効です|
> |**名前**:<br />SPInvalidFieldValueErrorCode<br />**16 進数**:<br />8006071E<br />**数値**:<br />-2147088610|無効なフィールド値|
> |**名前**:<br />SPInvalidLookupValuesErrorCode<br />**16 進数**:<br />8006070B<br />**数値**:<br />-2147088629|リスト内の 1 つまたは複数のフィールドで無効な検索値が見つかったため、リスト アイテムを更新できませんでした|
> |**名前**:<br />SPInvalidSavedQueryErrorCode<br />**16 進数**:<br />80060718<br />**数値**:<br />-2147088616|SharePoint でこの操作を実行中にエラーが発生しました|
> |**名前**:<br />SPInvalidSubSite<br />**16 進数**:<br />80060763<br />**数値**:<br />-2147088541|サブサイト URL の形式が正しくありません|
> |**名前**:<br />SPItemNotExistErrorCode<br />**16 進数**:<br />80060717<br />**数値**:<br />-2147088617|リスト アイテムが存在しません。|
> |**名前**:<br />SPMalFormedRelativeUrl<br />**16 進数**:<br />80060766<br />**数値**:<br />-2147088538|相対 URL の先頭または末尾にスペースを含めないでください。|
> |**名前**:<br />SPModifiedOnServerErrorCode<br />**16 進数**:<br />80060710<br />**数値**:<br />-2147088624|リスト アイテムがサーバー上で変更されたため、変更をコミットできません|
> |**名前**:<br />SPMultipleOdbSitesError<br />**16 進数**:<br />8006072D<br />**数値**:<br />-2147088595|OneDrive が有効な複数のサービス拠点は許可されていません。|
> |**名前**:<br />SPNoActiveDocumentLocationErrorCode<br />**16 進数**:<br />8006071C<br />**数値**:<br />-2147088612|アクティブなドキュメントの場所がありません|
> |**名前**:<br />SPNotAdminError<br />**16 進数**:<br />80060765<br />**数値**:<br />-2147088539|テナント管理者である CRM 管理者だけが、作成操作を実行できます|
> |**名前**:<br />SPNotEnabledError<br />**16 進数**:<br />8006073A<br />**数値**:<br />-2147088582|SharePoint 統合がエンティティで有効になっていません|
> |**名前**:<br />SPNotEnabledForEntity<br />**16 進数**:<br />8006073B<br />**数値**:<br />-2147088581|SharePoint I統合および Microsoft Teams 統合がエンティティで有効になっていません|
> |**名前**:<br />SPNullFileUrlErrorCode<br />**16 進数**:<br />8006070C<br />**数値**:<br />-2147088628|ファイルの作成情報の URL は、null または無効にしないでください|
> |**名前**:<br />SPNullRegardingObjectErrorCode<br />**16 進数**:<br />80060723<br />**数値**:<br />-2147088605|関連するオブジェクトは null です|
> |**名前**:<br />SPOdbDisabledError<br />**16 進数**:<br />8006072E<br />**数値**:<br />-2147088594|ODB サイトを作成するために ODB(One Drive for Business) 機能を有効にしてください。|
> |**名前**:<br />SPOdbDuplicateLocationError<br />**16 進数**:<br />80060735<br />**数値**:<br />-2147088587|複数の ODB (OneDrive for Business) の場所は許可されていません。|
> |**名前**:<br />SPOdbUpdateDeleteError<br />**16 進数**:<br />8006072F<br />**数値**:<br />-2147088593|ODB (One Drive for Business) サイトを更新、または削除できません。|
> |**名前**:<br />SPOdbUpdateDeleteLocationError<br />**16 進数**:<br />80060736<br />**数値**:<br />-2147088586|ODB タイプ (OneDrive for Business) の SharePoint のドキュメントの場所を更新、または削除できません。|
> |**名前**:<br />SPOperationNotSupportedErrorCode<br />**16 進数**:<br />80060715<br />**数値**:<br />-2147088619|リストはこの操作をサポートしていません|
> |**名前**:<br />SPOperatorNotSupportedErrorCode<br />**16 進数**:<br />80060724<br />**数値**:<br />-2147088604|{0} は選択したオペレーターをサポートしていません|
> |**名前**:<br />SPPersonalSiteNotFound<br />**16 進数**:<br />8006072B<br />**数値**:<br />-2147088597|ユーザーの個人用のサイトは見つかりませんでした。|
> |**名前**:<br />SPRequiredColCheckInErrorCode<br />**16 進数**:<br />80060725<br />**数値**:<br />-2147088603|SharePoint では一部の列が必須であるため、ドキュメントのチェックイン時に例外が発生しました|
> |**名前**:<br />SPSearchOneDriveNotCreated<br />**16 進数**:<br />80060737<br />**数値**:<br />-2147088585|OneDrive の場所がまだ作成されていません。 検索する前に場所を作成してください。|
> |**名前**:<br />SPSharedLockOnFileErrorCode<br />**16 進数**:<br />80060704<br />**数値**:<br />-2147088636|ファイルの共有ロックです|
> |**名前**:<br />SPSiteNotFoundErrorCode<br />**16 進数**:<br />8006071A<br />**数値**:<br />-2147088614|サービス拠点が見つかりません|
> |**名前**:<br />SPSiteProtocolError<br />**16 進数**:<br />80060738<br />**数値**:<br />-2147088584|SharePoint のアクセス中にプロトコル エラーが発生しました。|
> |**名前**:<br />SPThrottlingLimitExceededErrorCode<br />**16 進数**:<br />80060714<br />**数値**:<br />-2147088620|操作によって調整の制限を超えています|
> |**名前**:<br />SPUnauthorizedAccessErrorCode<br />**16 進数**:<br />80060701<br />**数値**:<br />-2147088639|現在のユーザーには十分な特権がありません|
> |**名前**:<br />SPUploadFailure<br />**16 進数**:<br />80060740<br />**数値**:<br />-2147088576|未知の理由により、SharePoint でアップロードに失敗しました。 ファイルが大きすぎる可能性があります。|
> |**名前**:<br />SqlArithmeticOverflowError<br />**16 進数**:<br />80041136<br />**数値**:<br />-2147217098|SQL 算術のオーバーフロー エラーが発生しました|
> |**名前**:<br />SqlEncryption<br />**16 進数**:<br />80048518<br />**数値**:<br />-2147187432|データ暗号化にエラーがありました。|
> |**名前**:<br />SqlEncryptionCannotOpenSymmetricKeyBecauseDatabaseMasterKeyDoesNotExistOrIsNotOpened<br />**16 進数**:<br />8004851A<br />**数値**:<br />-2147187430|データベース マスター キーがデータベースに存在しないまたは開かないため、対称キーを開くことはできません。|
> |**名前**:<br />SqlEncryptionCertificateDoesNotExist<br />**16 進数**:<br />8004851D<br />**数値**:<br />-2147187427|名前 ='{0}' を持つ証明書は、データベースに存在しません。|
> |**名前**:<br />SqlEncryptionChangeEncryptionKeyExceededQuotaForTheInterval<br />**16 進数**:<br />80048529<br />**数値**:<br />-2147187415|'変更' 暗号化キーは過去 {1} 分間に既に {0} 回実行されています。 数分待ってから、もう一度お試しください。|
> |**名前**:<br />SqlEncryptionCreateCertificateError<br />**16 進数**:<br />8004851E<br />**数値**:<br />-2147187426|既に存在するため、名前 ='{0}' の証明書は作成できません。|
> |**名前**:<br />SqlEncryptionCreateDatabaseMasterKeyError<br />**16 進数**:<br />8004851B<br />**数値**:<br />-2147187429|既に存在するため、データベース マスター キーを作成することはできません。|
> |**名前**:<br />SqlEncryptionCreateSymmetricKeyError<br />**16 進数**:<br />80048521<br />**数値**:<br />-2147187423|既に存在するため、名前 ='{0}' の対称キーは作成できません。|
> |**名前**:<br />SqlEncryptionDatabaseMasterKeyDoesNotExist<br />**16 進数**:<br />80048519<br />**数値**:<br />-2147187431|データベース マスター キーがデータベースに存在しません。|
> |**名前**:<br />SqlEncryptionDeleteCertificateError<br />**16 進数**:<br />8004851F<br />**数値**:<br />-2147187425|存在していない名前 ='{0}' の証明書は削除できません。|
> |**名前**:<br />SqlEncryptionDeleteDatabaseMasterKeyError<br />**16 進数**:<br />8004851C<br />**数値**:<br />-2147187428|存在していないデータベース マスター キーを削除できません。|
> |**名前**:<br />SqlEncryptionDeleteEncryptionKeyError<br />**16 進数**:<br />80048526<br />**数値**:<br />-2147187418|暗号化キーは削除できません。|
> |**名前**:<br />SqlEncryptionDeleteSymmetricKeyError<br />**16 進数**:<br />80048522<br />**数値**:<br />-2147187422|存在していない名前 ='{0}' の対称キーは削除できません。|
> |**名前**:<br />SqlEncryptionEncryptionDecryptionTestError<br />**16 進数**:<br />80048523<br />**数値**:<br />-2147187421|データの暗号化および暗号化解除のテスト中にエラーが発生しました。|
> |**名前**:<br />SqlEncryptionEncryptionKeyValidationError<br />**16 進数**:<br />80048528<br />**数値**:<br />-2147187416|新しい暗号化キーは強力な暗号化キーの要件を満たしていません。 キーは 10 ～ 100 文字にし、数字、文字、記号 (または特殊文字) をそれぞれ少なくとも 1 つ使用する必要があります。 {0}|
> |**名前**:<br />SqlEncryptionIsActiveCannotRestoreEncryptionKey<br />**16 進数**:<br />80048525<br />**数値**:<br />-2147187419|暗号化キーが既に設定され動作しているため、暗号化キーのアクティブ化は実行できません。 暗号化キーの '変更' を代わりに使用します。|
> |**名前**:<br />SqlEncryptionIsInactiveCannotChangeEncryptionKey<br />**16 進数**:<br />80048527<br />**数値**:<br />-2147187417|暗号化キーがまだ設定されず動作していないため、暗号化キーの変更は実行できません。 最初に現在の暗号化キーを修正するよう設定する代わりに 'アクティブ化' 暗号化キーを使用します。それから新しい暗号化キーを使用してデータを再暗号化する場合は、 '変更' 暗号を使用します。|
> |**名前**:<br />SqlEncryptionKeyCannotDecryptExistingData<br />**16 進数**:<br />80048524<br />**数値**:<br />-2147187420|現在の暗号化キーを使用して、暗号化されたデータ (エンティティ ='{0}'、属性 ='{1}') を暗号化解除することはできません。 暗号化キーの「アクティブ化」を使用して、正しい暗号化キーを設定してください。|
> |**名前**:<br />SqlEncryptionRestoreEncryptionKeyCannotDecryptExistingData<br />**16 進数**:<br />8004852B<br />**数値**:<br />-2147187413|暗号化キーがデータの暗号化に使用された最初の暗号化キーと一致しないため、アクティブ化を実行できません。|
> |**名前**:<br />SqlEncryptionSetEncryptionKeyIsAlreadyRunningCannotRunItInParallel<br />**16 進数**:<br />8004852A<br />**数値**:<br />-2147187414|現在、暗号化キーを「変更」または「アクティブ化」する要求を実行中です。 しばらく待ってから別の要求を行ってください。|
> |**名前**:<br />SqlEncryptionSymmetricKeyCannotOpenBecauseWrongPassword<br />**16 進数**:<br />80048530<br />**数値**:<br />-2147187408|パスワードが間違っているため、暗号対称キーを開くことはできません。|
> |**名前**:<br />SqlEncryptionSymmetricKeyDoesNotExist<br />**16 進数**:<br />80048520<br />**数値**:<br />-2147187424|名前 ='{0}' を持つ対称キーは、データベースに存在しません。|
> |**名前**:<br />SqlEncryptionSymmetricKeyDoesNotExistOrNoPermission<br />**16 進数**:<br />8004852F<br />**数値**:<br />-2147187409|データベースに存在しないまたはユーザーにアクセス許可がないため、暗号対称キーを開くことはできません。|
> |**名前**:<br />SqlEncryptionSymmetricKeyPasswordDoesNotExistInConfigDB<br />**16 進数**:<br />8004852E<br />**数値**:<br />-2147187410|暗号対称キーのパスワードは Config DB に存在しません。|
> |**名前**:<br />SqlEncryptionSymmetricKeySourceDoesNotExistInConfigDB<br />**16 進数**:<br />8004852D<br />**数値**:<br />-2147187411|暗号対称キーのソースは Config DB に存在しません。|
> |**名前**:<br />SqlErrorInStoredProcedure<br />**16 進数**:<br />8004C001<br />**数値**:<br />-2147172351|SQL エラー {0} がストアド プロシージャ {1} で発生しました|
> |**名前**:<br />SqlMaxRecursionExceeded<br />**16 進数**:<br />80044157<br />**数値**:<br />-2147204777|説明文の完了前に、最大再帰に達しました。|
> |**名前**:<br />SrsDataConnectorNotInstalled<br />**16 進数**:<br />80040492<br />**数値**:<br />-2147220334|MSCRM Data Connector はインストールされていません。|
> |**名前**:<br />SrsDataConnectorNotInstalledUpload<br />**16 進数**:<br />80048292<br />**数値**:<br />-2147188078|レポートの必須コンポーネントである Dynamics 365 Reporting Extensions が、Microsoft SQL Server Reporting Services を実行しているサーバーにインストールされていないため、このレポートをアップロードできません。|
> |**名前**:<br />SSM_MaxPCI_Exceeded<br />**16 進数**:<br />80072570<br />**数値**:<br />-2147015312|セッションを更新するには、もう一度ログインしてください。|
> |**名前**:<br />SSM_RefreshToken_Failed<br />**16 進数**:<br />80072571<br />**数値**:<br />-2147015311|ログイン セッションを更新できませんでした。|
> |**名前**:<br />StageEntityIsNull<br />**16 進数**:<br />80060451<br />**数値**:<br />-2147089327|検証エラー: ステージ エンティティを Null にできません。|
> |**名前**:<br />StageIdIsEmpty<br />**16 進数**:<br />80060454<br />**数値**:<br />-2147089324|検証エラー: ステージ ID を空にできません。|
> |**名前**:<br />StageIdIsNotPresentInBusinessProcess<br />**16 進数**:<br />80060450<br />**数値**:<br />-2147089328|検証エラー: ステージ ID ‘{0}’ がビジネス プロセスに存在しません。 システム管理者にお問い合わせください。|
> |**名前**:<br />StageIdIsNotValid<br />**16 進数**:<br />80060458<br />**数値**:<br />-2147089320|検証エラー: ステージ ID がビジネス プロセスに対して無効です。|
> |**名前**:<br />StateTransitionActivateNewStatus<br />**16 進数**:<br />8004F857<br />**数値**:<br />-2147157929|状態の移行ルール上、このレコードはアクティブ化できません。システム管理者に問い合わせてください。|
> |**名前**:<br />StateTransitionActiveToCanceled<br />**16 進数**:<br />8004F855<br />**数値**:<br />-2147157931|状態の移行ルールにより、現在の状態のサポート案件を取り消すことはできません。サポート案件の状態を変更してから取り消すか、システム管理者に問い合わせてください。|
> |**名前**:<br />StateTransitionActiveToResolve<br />**16 進数**:<br />8004F854<br />**数値**:<br />-2147157932|状態の移行ルールにより、現在の状態のサポート案件を解決することができません。サポート案件の状態を変更してから解決するか、システム管理者に問い合わせてください。|
> |**名前**:<br />StateTransitionDeactivateNewStatus<br />**16 進数**:<br />8004F858<br />**数値**:<br />-2147157928|状態の移行ルール上、このレコードは非アクティブ化できません。システム管理者に問い合わせてください。|
> |**名前**:<br />StateTransitionResolvedOrCanceledToActive<br />**16 進数**:<br />8004F856<br />**数値**:<br />-2147157930|状態の移行ルールのため、現在の状態からサポート案件をアクティブ化することはできません。システム管理者に問い合わせてください。|
> |**名前**:<br />StepAutomaticallyDisabled<br />**16 進数**:<br />80045043<br />**数値**:<br />-2147200957|元の sdkmessageprocessingstep は無効になり、置き換えられました。|
> |**名前**:<br />StepCountInXamlExceedsMaxAllowed<br />**16 進数**:<br />80060414<br />**数値**:<br />-2147089388|Xamlに {0} {1} があります。 許可された最大値は {2} です。|
> |**名前**:<br />StepDoesNotHaveAnyChildInXaml<br />**16 進数**:<br />80060416<br />**数値**:<br />-2147089386|{0} には、子として少なくとも 1 つの {1} もありません。|
> |**名前**:<br />StepNotSupportedForClientBusinessRule<br />**16 進数**:<br />80060000<br />**数値**:<br />-2147090432|ステップ {0} は、クライアント側の業務ルールでサポートされていません。|
> |**名前**:<br />StepStepDoesNotHaveAnyControlStepAsItsChildren<br />**16 進数**:<br />80060409<br />**数値**:<br />-2147089399|StepStep に子供としての ControlStep はありません。|
> |**名前**:<br />StoredProcedureContext<br />**16 進数**:<br />8004C002<br />**数値**:<br />-2147172350|{1}:{2} での Dynamics 365 エラー {0}|
> |**名前**:<br />StringAttributeIndexError<br />**16 進数**:<br />8004D292<br />**数値**:<br />-2147167598|選択されたエンティティの属性の 1 つはデータベース インデックスの一部なので、900 バイトより大きくすることはできません。|
> |**名前**:<br />StringLengthTooLong<br />**16 進数**:<br />80044331<br />**数値**:<br />-2147204303|検証エラーが発生しました。 提供された文字列値が長すぎます。|
> |**名前**:<br />SubcomponentDoesNotExist<br />**16 進数**:<br />80048537<br />**数値**:<br />-2147187401|サブコンポーネント {0} の種類 {1} が組織内で見つかりませんでした。SolutionComponents に追加することはできません。|
> |**名前**:<br />SubcomponentMissingARoot<br />**16 進数**:<br />80048536<br />**数値**:<br />-2147187402|ルート コンポーネント {1} が存在しないため、サブコンポーネント {0} はソリューションに追加できません。|
> |**名前**:<br />SubjectDoesNotExist<br />**16 進数**:<br />80043e02<br />**数値**:<br />-2147205630|件名が存在しません。|
> |**名前**:<br />SubjectLoopBeingCreated<br />**16 進数**:<br />80043e01<br />**数値**:<br />-2147205631|この上位下位の関連付けを作成すると、情報カテゴリ階層にループが生成されます。|
> |**名前**:<br />SubjectLoopExists<br />**16 進数**:<br />80043e00<br />**数値**:<br />-2147205632|情報カテゴリ階層にループが存在します。|
> |**名前**:<br />SubReportDoesNotExist<br />**16 進数**:<br />80040493<br />**数値**:<br />-2147220333|サブレポートが存在しません。 ReportId:{0}|
> |**名前**:<br />SubscriptionGone<br />**16 進数**:<br />80072513<br />**数値**:<br />-2147015405|サブスクリプション期限が切れました|
> |**名前**:<br />SupportLogOnExpired<br />**16 進数**:<br />8004A108<br />**数値**:<br />-2147180280|サポート ログインは期限切れです|
> |**名前**:<br />SupportUserCannotBeCreateNorUpdated<br />**16 進数**:<br />80041d41<br />**数値**:<br />-2147214015|サポート ユーザーは更新できません|
> |**名前**:<br />SyncAttributeMappingCannotBeUpdated<br />**16 進数**:<br />80060741<br />**数値**:<br />-2147088575|同期属性マッピングを更新できません。|
> |**名前**:<br />SyncToMsdeFailure<br />**16 進数**:<br />80048407<br />**数値**:<br />-2147187705|オフライン モードの MSDE データベースの開始または接続を行えませんでした。|
> |**名前**:<br />SystemAttributeMap<br />**16 進数**:<br />80046205<br />**数値**:<br />-2147196411|SystemAttributeMap のエラーが発生しました|
> |**名前**:<br />SystemEntityMap<br />**16 進数**:<br />80046202<br />**数値**:<br />-2147196414|SystemEntityMap のエラーが発生しました|
> |**名前**:<br />SystemFormCopyUnmatchedEntity<br />**16 進数**:<br />8004F656<br />**数値**:<br />-2147158442|Target と SourceId のエンティティが一致する必要があります。|
> |**名前**:<br />SystemFormCopyUnmatchedFormType<br />**16 進数**:<br />8004F657<br />**数値**:<br />-2147158441|SourceId のフォームの種類が Target エンティティに対して有効ではありません。|
> |**名前**:<br />SystemFormCreateWithExistingLabel<br />**16 進数**:<br />8004F658<br />**数値**:<br />-2147158440|ラベル '{0}'、ID: '{1}' が既に存在します。 一意のラベル ID 値を指定してください。|
> |**名前**:<br />SystemFormImportMissingRoles<br />**16 進数**:<br />8004F655<br />**数値**:<br />-2147158443|インポートしているアンマネージド ソリューションには、ターゲット システムにはないセキュリティ ロールを参照する表示条件 XML 属性が含まれています。 これらのセキュリティ ロールに言及するどんな displaycondition 属性も削除されます。|
> |**名前**:<br />SystemUserDisabled<br />**16 進数**:<br />8004A112<br />**数値**:<br />-2147180270|システム ユーザーが無効にされたため、チケットが期限切れになりました。|
> |**名前**:<br />TamperedAuthTicket<br />**16 進数**:<br />8004A105<br />**数値**:<br />-2147180283|認証のために指定されたチケットが改ざん、または無効化されています。|
> |**名前**:<br />TargetAttributeInvalidForIgnore<br />**16 進数**:<br />80048500<br />**数値**:<br />-2147187456|ProcessCode を無視する場合は、ターゲット属性は空である必要があります。|
> |**名前**:<br />TargetAttributeInvalidForMap<br />**16 進数**:<br />80040394<br />**数値**:<br />-2147220588|この属性はマッピングには無効です。|
> |**名前**:<br />TargetAttributeNotFound<br />**16 進数**:<br />80040392<br />**数値**:<br />-2147220590|ファイルが Microsoft Dynamics 365 に存在しない属性を指定しています。|
> |**名前**:<br />TargetEntityInvalidForMap<br />**16 進数**:<br />80040395<br />**数値**:<br />-2147220587|データ移行には無効なエンティティがファイルで指定されています。|
> |**名前**:<br />TargetEntityNotFound<br />**16 進数**:<br />80040391<br />**数値**:<br />-2147220591|ファイルが Microsoft Dynamics 365 に存在しないエンティティを指定しています。|
> |**名前**:<br />TargetEntityNotMapped<br />**16 進数**:<br />80048460<br />**数値**:<br />-2147187616|対象エンティティ名がソースに対して定義されていません:{0} ファイル。|
> |**名前**:<br />TargetUserInsufficientPrivileges<br />**16 進数**:<br />80048342<br />**数値**:<br />-2147187902|ユーザーに "{0}" 特権がないため、そのユーザーをチームに追加できません。|
> |**名前**:<br />TaskFlowEmptyName<br />**16 進数**:<br />80061712<br />**数値**:<br />-2147084526|名前フィールドは空にできません。 名前を入力してください。|
> |**名前**:<br />TaskFlowEntityAttributeIsNotValid<br />**16 進数**:<br />80061717<br />**数値**:<br />-2147084521|無効な属性の種類: {0}。{1}。|
> |**名前**:<br />TaskFlowEntityRelationshipIsNotValid<br />**16 進数**:<br />80061716<br />**数値**:<br />-2147084522|無効な関係の種類: {0}。|
> |**名前**:<br />TaskFlowFormXmlNotFound<br />**16 進数**:<br />80061713<br />**数値**:<br />-2147084525|タスク フロー {1} のシステム フォーム {0} が見つかりませんでした。|
> |**名前**:<br />TaskFlowInvalidCharactersInName<br />**16 進数**:<br />80061711<br />**数値**:<br />-2147084527|名前フィールドには英数字のみを使用できます。|
> |**名前**:<br />TaskFlowMaxNumberControls<br />**16 進数**:<br />80061719<br />**数値**:<br />-2147084519|タスク フローが、許可されている最大コントロール数 ({0}) を越えました。 続行するには、一部のコントロールを削除する必要があります。|
> |**名前**:<br />TaskFlowMaxNumberPages<br />**16 進数**:<br />80061718<br />**数値**:<br />-2147084520|タスク フローが、許可されている最大ページ数 ({0}) を越えました。 続行するには、一部のページを削除する必要があります。|
> |**名前**:<br />TaskFlowNameIsNotUnique<br />**16 進数**:<br />80061710<br />**数値**:<br />-2147084528|指定された名前のタスク フローは、既に存在しています。  一意の名前を指定してください。|
> |**名前**:<br />TaskFlowNotFound<br />**16 進数**:<br />80061720<br />**数値**:<br />-2147084512|起動しようとするタスク フローは、このデバイスでは使用できません。 そのフローへのアクセス許可がないか、所属している組織ではそのフローを使用できない可能性があります。 システム管理者にお問い合わせください。|
> |**名前**:<br />TaskFlowNotValid<br />**16 進数**:<br />8006172F<br />**数値**:<br />-2147084497|タスク フローの定義が無効です。|
> |**名前**:<br />TaskFlowPageMissingFormXmlTab<br />**16 進数**:<br />80061714<br />**数値**:<br />-2147084524|タスク フロー {1} ステップ {2}のページ {0} が見つかりませんでした。|
> |**名前**:<br />TaskFlowUnsupportedEntities<br />**16 進数**:<br />80061715<br />**数値**:<br />-2147084523|次のエンティティは、タスク フローに対応していません: {0}。|
> |**名前**:<br />TeamAdministratorMissedPrivilege<br />**16 進数**:<br />80041d0a<br />**数値**:<br />-2147214070|チーム管理者は、チームに対する読み取り特権を持っていません。|
> |**名前**:<br />TeamInWrongBusiness<br />**16 進数**:<br />8004140d<br />**数値**:<br />-2147216371|id = {0} のチームは、roleId = {2} および roleBusinessUnit = {3} のロールとは異なる部署 = {1} に属しています。|
> |**名前**:<br />TeamNameTooLong<br />**16 進数**:<br />80048305<br />**数値**:<br />-2147187963|指定されたチームに対する名前は長すぎます。|
> |**名前**:<br />TeamNotAssignedRoles<br />**16 進数**:<br />80042f0a<br />**数値**:<br />-2147209462|チームにロールが割り当てられていません。|
> |**名前**:<br />TemplateNotAllowedForInternetMarketing<br />**16 進数**:<br />80048475<br />**数値**:<br />-2147187595|インターネット マーケティング キャンペーン活動のテンプレートを作成することは許可されていません|
> |**名前**:<br />TemplateTypeNotSupportedForUnsubscribeAcknowledgement<br />**16 進数**:<br />80040324<br />**数値**:<br />-2147220700|このテンプレートの種類は、登録解除の受信確認をサポートしていません。|
> |**名前**:<br />TenantIDIsEmpty<br />**16 進数**:<br />8005E25A<br />**数値**:<br />-2147098022|Exchange Online テナント ID フィールドは空にできません。|
> |**名前**:<br />TenantIDValueChanged<br />**16 進数**:<br />8005E25C<br />**数値**:<br />-2147098020|Exchange 用に検出された tenantId は、保存したものとは異なります。|
> |**名前**:<br />TestEmailConfigurationScheduledInProgress<br />**16 進数**:<br />8005E248<br />**数値**:<br />-2147098040|テスト電子メール アクセス構成のスケジュールが進行中です。 テストの完了後に保存してください。|
> |**名前**:<br />TextAnalyticsAPIActiveConfigurationDoesNotExist<br />**16 進数**:<br />80061690<br />**数値**:<br />-2147084656|エンティティのアクティブな構成が存在しません。|
> |**名前**:<br />TextAnalyticsAPIActiveSimilarityConfigurationDoesNotExist<br />**16 進数**:<br />80061695<br />**数値**:<br />-2147084651|アクティブな類似ルールは存在しません。 システム管理者は類似ルール構成を設定する必要があります。|
> |**名前**:<br />TextAnalyticsAPIAllowedOnlyForEnglishLanguage<br />**16 進数**:<br />80061691<br />**数値**:<br />-2147084655|テキスト分析機能は、基本言語が英語の組織で利用可能です。|
> |**名前**:<br />TextAnalyticsAPIAzureUnableToConnectWithBuild<br />**16 進数**:<br />80061692<br />**数値**:<br />-2147084654|Dynamics 365 は Azure Text Analytics サービスに接続するのに失敗しました。 サービス URI とアカウント キーが有効で、Azure サブスクリプションがアクティブであることを確認してください。|
> |**名前**:<br />TextAnalyticsAzureConnectionCascadeActivateFailed<br />**16 進数**:<br />80061634<br />**数値**:<br />-2147084748|1 つまたは複数のテキスト分析モデルはアクティブ化できませんでした。 Azure サービス接続とは別に既存のテキスト分析モデルのアクティブ化を試してください。|
> |**名前**:<br />TextAnalyticsAzureConnectionFailed<br />**16 進数**:<br />80061650<br />**数値**:<br />-2147084720|Text Analytics API へ接続できません。|
> |**名前**:<br />TextAnalyticsAzureSchedulerError<br />**16 進数**:<br />80061693<br />**数値**:<br />-2147084653|Dynamics 365 は Azure Text Analytics サービスに接続するのに失敗しました。 もう一度試してみても問題が解決しない場合は、システム管理者に問い合わせてください。|
> |**名前**:<br />TextAnalyticsAzureTestConnectionFailed<br />**16 進数**:<br />80061632<br />**数値**:<br />-2147084750|Azure Text Analytics サービスに接続できませんでした。 サービス URL と Azure アカウント キーが有効で、サービスのサブスクリプションがアクティブであることを確認してください。|
> |**名前**:<br />TextAnalyticsAzureUnableToConnectWithBuild<br />**16 進数**:<br />80061655<br />**数値**:<br />-2147084715|Dynamics 365 は Azure Text Analytics サービスに接続するのに失敗しました。 サービス URI とアカウント キーが有効で、Azure サブスクリプションがアクティブであることを確認してください。|
> |**名前**:<br />TextAnalyticsFeatureNotEnabled<br />**16 進数**:<br />80061652<br />**数値**:<br />-2147084718|Azure テキスト分析機能はアクティブ化されていません。 システム管理者はこの機能をアクティブ化し、必要な構成を設定する必要があります。|
> |**名前**:<br />TextAnalyticsMappingUsedForActiveConfiguration<br />**16 進数**:<br />80061667<br />**数値**:<br />-2147084697|このテキスト分析エンティティ マッピングは、アクティブな構成に使用されています。 アクティブな構成で使用されている間は、修正または削除できません。|
> |**名前**:<br />TextAnalyticsMaxLimitForTopicModelReached<br />**16 進数**:<br />80061694<br />**数値**:<br />-2147084652|組織で許可されているトピック モデルの最大数に達しました。|
> |**名前**:<br />TextAnalyticsModelActivateConnectionMustBeActive<br />**16 進数**:<br />80061657<br />**数値**:<br />-2147084713|Azure Machine Learning テキスト分析サービスの接続は、モデルのアクティブ化の前にアクティブ化する必要があります。 テキスト分析 サービスの接続のライセンス認証を行い、もう一度やり直してください。|
> |**名前**:<br />ThemeIdOrUpdateTimestampIsNull<br />**16 進数**:<br />800608D1<br />**数値**:<br />-2147088175|テーマ ID または更新タイムスタンプ値がテーマのデータに存在しません。|
> |**名前**:<br />調整<br />**16 進数**:<br />8005F103<br />**数値**:<br />-2147094269|リクエストが多すぎます。|
> |**名前**:<br />ThrottlingBurstRequestLimitExceededError<br />**16 進数**:<br />80072322<br />**数値**:<br />-2147015902|{1} 秒の時間枠で要求の数が制限値 {0} を超えています。|
> |**名前**:<br />ThrottlingConcurrencyLimitExceededError<br />**16 進数**:<br />80072326<br />**数値**:<br />-2147015898|同時実行要求の数が制限値 {0} を超えています。|
> |**名前**:<br />ThrottlingTimeExceededError<br />**16 進数**:<br />80072321<br />**数値**:<br />-2147015903|受信した要求の合計実行時間が {1} 秒の時間枠にわたって {0} ミリ秒の制限を超えました。 同時要求の数を減らすか、要求の期間を短くして後で再試行してください。|
> |**名前**:<br />TooManyBytesInInputStream<br />**16 進数**:<br />8004F901<br />**数値**:<br />-2147157759|読み取られるストリームのバイトが多すぎます。|
> |**名前**:<br />TooManyCalculatedFieldsInQuery<br />**16 進数**:<br />80060429<br />**数値**:<br />-2147089367|クエリの計算フィールド数が最大制限値 {0} を超えました。|
> |**名前**:<br />TooManyConditionParametersInQuery<br />**16 進数**:<br />8004430E<br />**数値**:<br />-2147204338|条件のパラメーター数が上限を超えました。|
> |**名前**:<br />TooManyConditionsInQuery<br />**16 進数**:<br />8004430C<br />**数値**:<br />-2147204340|クエリの条件数が最大制限値を超えました。|
> |**名前**:<br />TooManyEntitiesEnabledForAutoCreatedAccessTeams<br />**16 進数**:<br />80048332<br />**数値**:<br />-2147187918|自動作成のアクセス チームに対して有効になっているエンティティが多すぎます。|
> |**名前**:<br />TooManyLinkEntitiesInQuery<br />**16 進数**:<br />8004430D<br />**数値**:<br />-2147204339|クエリのリンク エンティティが最大制限値を超えました。|
> |**名前**:<br />TooManyMultiSelectConditionParametersInQuery<br />**16 進数**:<br />80050223<br />**数値**:<br />-2147155421|クエリの複数選択条件パラメーターの数が最大制限: {0} を超えました。|
> |**名前**:<br />TooManyPicklistValues<br />**16 進数**:<br />80048492<br />**数値**:<br />-2147187566|個別候補リスト値が最大制限値を超えました。|
> |**名前**:<br />TooManyRecipients<br />**16 進数**:<br />8004350e<br />**数値**:<br />-2147207922|複数の受信者への送信はサポートされていません。|
> |**名前**:<br />TooManySelectionsForAttributeType<br />**16 進数**:<br />80050222<br />**数値**:<br />-2147155422|MultiSelectPicklist 属性の種類の選択数が上限: {0} を超えました。|
> |**名前**:<br />TooManyTeamTemplatesForEntityAccessTeams<br />**16 進数**:<br />80048333<br />**数値**:<br />-2147187917|現在のチーム数: {0} が、ObjectTypeCode {2} のエンティティのチーム制限: {1} を超えています|
> |**名前**:<br />TopicModelActivateWithInvalidConfiguration<br />**16 進数**:<br />80061656<br />**数値**:<br />-2147084714|ビルドに使用する構成が無効です。 トピック分析に使用する構成にはトピックの判定フィールドが必須です。|
> |**名前**:<br />TopicModelConfigurationAssociatedModelAlreadyActive<br />**16 進数**:<br />80061670<br />**数値**:<br />-2147084688|トピック モデル構成がアクティブなトピック モデルに関連付けられているため、更新または削除できません。|
> |**名前**:<br />TopicModelConfigurationUsedEmpty<br />**16 進数**:<br />80061653<br />**数値**:<br />-2147084717|アクティブ化には、ビルド構成の指定が必要です。 アクティブ化の前にビルドに使用する構成を指定してください。|
> |**名前**:<br />TopicModelScheduleBuildSettingsEmpty<br />**16 進数**:<br />80061651<br />**数値**:<br />-2147084719|アクティブ化には、ビルド スケジュールの設定が必要です。 アクティブ化の前にビルドのスケジュール設定を指定してください。|
> |**名前**:<br />TopicModelTestWithoutConfiguration<br />**16 進数**:<br />80061654<br />**数値**:<br />-2147084716|ビルドに使用する構成を指定してください。|
> |**名前**:<br />TraceMessageConstructionError<br />**16 進数**:<br />8004F900<br />**数値**:<br />-2147157760|トレース レコードに無効なトレース コードがあるか、トレース パラメーターの数が不足しています。|
> |**名前**:<br />TransactionAborted<br />**16 進数**:<br />80040255<br />**数値**:<br />-2147220907|トランザクションは中止されました。|
> |**名前**:<br />TransactionNotCommited<br />**16 進数**:<br />80040252<br />**数値**:<br />-2147220910|トランザクションはコミットされません。|
> |**名前**:<br />TransactionNotStarted<br />**16 進数**:<br />80040251<br />**数値**:<br />-2147220911|トランザクションが開始されません。|
> |**名前**:<br />TransactionNotSupported<br />**16 進数**:<br />8005E007<br />**数値**:<br />-2147098617|実行しようとしている操作では、トランザクションはサポートされません。|
> |**名前**:<br />TransformationResumeNotSupported<br />**16 進数**:<br />80048463<br />**数値**:<br />-2147187613|インポートの変換ジョブの再開/再試行はサポートされていません。|
> |**名前**:<br />TransformMustBeCalledBeforeImport<br />**16 進数**:<br />80040335<br />**数値**:<br />-2147220683|変換前にインポートを呼び出すことはできません。|
> |**名前**:<br />TranslateArticle_OnlyPrimaryArticlesCanBeTranslated<br />**16 進数**:<br />80061402<br />**数値**:<br />-2147085310|この記事は、元の記事の翻訳版です。 再び変換することはできません。 別の翻訳が必要な場合は、これよりむしろ元の記事から始めてください。|
> |**名前**:<br />TranslateArticle_TranslationCanNotBeCreatedForTheSameLanguage<br />**16 進数**:<br />80061403<br />**数値**:<br />-2147085309|この記事のバージョンには、この言語の翻訳版が既に存在しています|
> |**名前**:<br />TrendingDocumentsDataRetrievalFailure<br />**16 進数**:<br />80044234<br />**数値**:<br />-2147204556|Trending Documents を表示できません。 後でもう一度試してみてください。|
> |**名前**:<br />TrendingDocumentsIntegrationDisabledError<br />**16 進数**:<br />80044233<br />**数値**:<br />-2147204557|Trending Documents はユーザーの Microsoft Dynamics 365 アカウントで無効になっています。|
> |**名前**:<br />TrendingDocumentsIntegrationTurnedOffError<br />**16 進数**:<br />80044255<br />**数値**:<br />-2147204523|Trending Documents が無効になっています。 システム管理者に連絡して、[システムの設定] でこの機能をオンにしてもらってください。|
> |**名前**:<br />TrendingDocumentsOfflineModeError<br />**16 進数**:<br />80044258<br />**数値**:<br />-2147204520|Trending Documents は、オフライン モードでは使用できません。|
> |**名前**:<br />TrendingDocumentsOnpremiseDeploymentError<br />**16 進数**:<br />80044232<br />**数値**:<br />-2147204558|Trending Documents ダッシュボード コンポーネントは会社の Microsoft Office サービスによってサポートされていません。|
> |**名前**:<br />TriggerFlowFailure<br />**16 進数**:<br />80050261<br />**数値**:<br />-2147155359|このフローを実行しようとしたときにエラーが発生しました。|
> |**名前**:<br />TypeNotSetToDefinition<br />**16 進数**:<br />80060402<br />**数値**:<br />-2147089406|種類は、ビジネス プロセス フローのカテゴリの作成時に [Definition] に設定されている必要があります|
> |**名前**:<br />UIDataGenerationFailed<br />**16 進数**:<br />80045037<br />**数値**:<br />-2147200969|XAML から UIData を生成中にエラーが発生しました。|
> |**名前**:<br />UIDataMissingInWorkflow<br />**16 進数**:<br />80048471<br />**数値**:<br />-2147187599|ワークフローに UIData が含まれていません。|
> |**名前**:<br />UIScriptIdentifierDuplicate<br />**16 進数**:<br />8004F217<br />**数値**:<br />-2147159529|同じ名前の変数または入力引数が既に存在しています。 異なる名前を選択して、やり直してください。|
> |**名前**:<br />UIScriptIdentifierInvalid<br />**16 進数**:<br />8004F218<br />**数値**:<br />-2147159528|変数または入力引数の名前が無効です。 名前には'_'、数字およびアルファベット文字のみ使用できます。 異なる名前を選択して、やり直してください。|
> |**名前**:<br />UIScriptIdentifierInvalidLength<br />**16 進数**:<br />8004F219<br />**数値**:<br />-2147159527|変数または入力引数の名前が長すぎます。 小さな名前を選択して、やり直してください。|
> |**名前**:<br />UnableToActivateQuoteNotInDraft<br />**16 進数**:<br />80100003<br />**数値**:<br />-2146435069|見積もりは、ドラフト状態でないためアクティブ化できません。|
> |**名前**:<br />UnableToLoadCustomActivity<br />**16 進数**:<br />8004505A<br />**数値**:<br />-2147200934|カスタム活動を読み込めません。|
> |**名前**:<br />UnableToLoadPluginAssembly<br />**16 進数**:<br />80044191<br />**数値**:<br />-2147204719|プラグイン アセンブリを読み込めません。|
> |**名前**:<br />UnableToLoadPluginType<br />**16 進数**:<br />80044190<br />**数値**:<br />-2147204720|プラグインの種類を読み込めません。|
> |**名前**:<br />UnableToLoadTransformationAssembly<br />**16 進数**:<br />80040378<br />**数値**:<br />-2147220616|変換アセンブリを読み込めません。|
> |**名前**:<br />UnableToLoadTransformationType<br />**16 進数**:<br />80040379<br />**数値**:<br />-2147220615|変換の種類を読み込めません。|
> |**名前**:<br />UnableToLogOnUserFromUserNameAndPassword<br />**16 進数**:<br />80044311<br />**数値**:<br />-2147204335|指定したユーザー名とパスワードは、ログオンできません。|
> |**名前**:<br />UnableToSendEmail<br />**16 進数**:<br />8004B015<br />**数値**:<br />-2147176427|招待の送信で、一部内部エラーが発生しました。後でやり直してください。|
> |**名前**:<br />UnapprovedMailbox<br />**16 進数**:<br />8005E220<br />**数値**:<br />-2147098080|メールボックスは承認済みの状態ではありません。 メールを送受信できるのは承認されたメールボックスだけです。|
> |**名前**:<br />UnauthorizedAccess<br />**16 進数**:<br />80040277<br />**数値**:<br />-2147220873|許可されていない操作を実行しようとしました。|
> |**名前**:<br />UnExpected<br />**16 進数**:<br />80040216<br />**数値**:<br />-2147220970|予期しないエラーが発生しました。|
> |**名前**:<br />UnexpectedErrorInMailMerge<br />**16 進数**:<br />80040330<br />**数値**:<br />-2147220688|差し込み印刷中に予期しないエラーが発生しました。|
> |**名前**:<br />UnexpectedNullReferenceError<br />**16 進数**:<br />8004F044<br />**数値**:<br />-2147159996|予期しない Null 参照エラー: {0}。|
> |**名前**:<br />UnexpectedRightOperandCount<br />**16 進数**:<br />80060006<br />**数値**:<br />-2147090426|式の右側オペランドの配列は予期しない no を含みます。 演算子。|
> |**名前**:<br />UnitDoesNotExist<br />**16 進数**:<br />80043b1b<br />**数値**:<br />-2147206373|出荷単位が存在しません。|
> |**名前**:<br />UnitLoopBeingCreated<br />**16 進数**:<br />80043b1a<br />**数値**:<br />-2147206374|この基本出荷単位を使用すると出荷単位階層にループが作成されます。|
> |**名前**:<br />UnitLoopExists<br />**16 進数**:<br />80043b19<br />**数値**:<br />-2147206375|出荷単位階層にループが存在します。|
> |**名前**:<br />UnitNoName<br />**16 進数**:<br />80043b26<br />**数値**:<br />-2147206362|出荷単位名を null にすることはできません。|
> |**名前**:<br />UnitNotInSchedule<br />**16 進数**:<br />80043b16<br />**数値**:<br />-2147206378|指定された出荷単位スケジュールに出荷単位が存在しません。|
> |**名前**:<br />UnknownInvalidTransformationParameterGeneric<br />**16 進数**:<br />80048513<br />**数値**:<br />-2147187437|1 つまたは複数の入力変換パラメーター値が無効です: {0}。|
> |**名前**:<br />unManagedchildentityisnotchild<br />**16 進数**:<br />800404e6<br />**数値**:<br />-2147220250|入力した子エンティティは、子ではありません。|
> |**名前**:<br />unManagedcihldofconditionforoffilefilters<br />**16 進数**:<br />800404a9<br />**数値**:<br />-2147220311|子の条件はオフライン フィルターでのみ許可されています。|
> |**名前**:<br />UnmanagedComponentParentsManagedComponent<br />**16 進数**:<br />8004803B<br />**数値**:<br />-2147188677|アンマネージド コンポーネントがマネージド コンポーネントの親である場合、{0} 依存関係レコードが見つかりました。 最初レコード (dependentcomponentobjectid = {1}、種類 = {2}、requiredcomponentobjectid = {3}、種類 = {4}、ソリューション = {5})。|
> |**名前**:<br />unManagedemptyprocessliteralcondition<br />**16 進数**:<br />800404b0<br />**数値**:<br />-2147220304|ProcessLiteralCondition に指定したデータはありません。|
> |**名前**:<br />unManagedentityisnotintersect<br />**16 進数**:<br />800404aa<br />**数値**:<br />-2147220310|エンティティは、交差するエンティティではありません。|
> |**名前**:<br />unManagederroraddingfiltertoqueryplan<br />**16 進数**:<br />800404ca<br />**数値**:<br />-2147220278|クエリ計画にフィルターを追加中にエラーが発生しました。|
> |**名前**:<br />unManagederrorprocessingfilternodes<br />**16 進数**:<br />800404c4<br />**数値**:<br />-2147220284|フィルター ノードの処理中に予期しないエラーが発生しました。|
> |**名前**:<br />unManagedfieldnotvalidatedbyplatform<br />**16 進数**:<br />800404ae<br />**数値**:<br />-2147220306|フィールドはプラットフォームによって検証されませんでした。|
> |**名前**:<br />unManagedfilterindexoutofrange<br />**16 進数**:<br />800404ab<br />**数値**:<br />-2147220309|フィルター インデックスの範囲を超えています。|
> |**名前**:<br />unManagedIdsAccessDenied<br />**16 進数**:<br />80048306<br />**数値**:<br />-2147187962|Microsoft Dynamics 365 オブジェクトまたは、要求された操作を実行するための十分な特権がありません。|
> |**名前**:<br />unManagedidsaccounthaschildopportunities<br />**16 進数**:<br />80040511<br />**数値**:<br />-2147220207|取引先企業に下位の営業案件が存在しています。|
> |**名前**:<br />unManagedidsactivitydurationdoesnotmatch<br />**16 進数**:<br />8004350a<br />**数値**:<br />-2147207926|活動期間は、開始時刻、終了時間と一致しません|
> |**名前**:<br />unManagedidsactivityinvalidduration<br />**16 進数**:<br />80043509<br />**数値**:<br />-2147207927|無効な活動期間|
> |**名前**:<br />unManagedidsactivityinvalidobjecttype<br />**16 進数**:<br />80043503<br />**数値**:<br />-2147207933|活動の関連オブジェクトの種類が無効です。|
> |**名前**:<br />unManagedidsactivityinvalidpartyobjecttype<br />**16 進数**:<br />80043505<br />**数値**:<br />-2147207931|活動関係者オブジェクトの種類が無効です。|
> |**名前**:<br />unManagedidsactivityinvalidregardingobject<br />**16 進数**:<br />80043507<br />**数値**:<br />-2147207929|オブジェクトに関する無効な活動は、存在しない可能性があります|
> |**名前**:<br />unManagedidsactivityinvalidstate<br />**16 進数**:<br />80043500<br />**数値**:<br />-2147207936|無効な活動の状態|
> |**名前**:<br />unManagedidsactivityinvalidtimeformat<br />**16 進数**:<br />80043508<br />**数値**:<br />-2147207928|無効な活動時間、小切手の形式|
> |**名前**:<br />unManagedidsactivityinvalidtype<br />**16 進数**:<br />80043501<br />**数値**:<br />-2147207935|活動の種類のコードが無効です|
> |**名前**:<br />unManagedidsactivitynotroutable<br />**16 進数**:<br />8004350b<br />**数値**:<br />-2147207925|この種類の活動はルーティングできません|
> |**名前**:<br />unManagedidsactivityobjectidortypemissing<br />**16 進数**:<br />80043502<br />**数値**:<br />-2147207934|活動の関連オブジェクトの ID または種類がありません。|
> |**名前**:<br />unManagedidsactivitypartyobjectidortypemissing<br />**16 進数**:<br />80043504<br />**数値**:<br />-2147207932|活動関係者オブジェクトの ID または種類がありません。|
> |**名前**:<br />unManagedidsanonymousenabled<br />**16 進数**:<br />80040226<br />**数値**:<br />-2147220954|ログインしたユーザーが、Active Directory で見つかりませんでした。|
> |**名前**:<br />unManagedidsarticletemplatecontainsarticles<br />**16 進数**:<br />80043e05<br />**数値**:<br />-2147205627|サポート情報記事が記事テンプレートを使用しているため、記事テンプレートを変更することはできません。|
> |**名前**:<br />unManagedidsarticletemplateisnotactive<br />**16 進数**:<br />80043e07<br />**数値**:<br />-2147205625|非アクティブなサポート技術情報の記事のテンプレートです。|
> |**名前**:<br />unManagedidsattachmentcannotcreatetempfile<br />**16 進数**:<br />80044a05<br />**数値**:<br />-2147202555|一時添付ファイルを作成することはできません。|
> |**名前**:<br />unManagedidsattachmentcannotgetfilesize<br />**16 進数**:<br />80044a01<br />**数値**:<br />-2147202559|一時添付ファイルのサイズを取得することはできません。|
> |**名前**:<br />unManagedidsattachmentcannotopentempfile<br />**16 進数**:<br />80044a00<br />**数値**:<br />-2147202560|一時添付ファイルを開くことはできません。|
> |**名前**:<br />unManagedidsattachmentcannotreadtempfile<br />**16 進数**:<br />80044a03<br />**数値**:<br />-2147202557|一時添付ファイルを読み込むことはできません。|
> |**名前**:<br />unManagedidsattachmentcannottruncatetempfile<br />**16 進数**:<br />80044a07<br />**数値**:<br />-2147202553|一時添付ファイルを切り詰めることはできません。|
> |**名前**:<br />unManagedidsattachmentcannotunmaptempfile<br />**16 進数**:<br />80044a06<br />**数値**:<br />-2147202554|一時添付ファイルをアンマップすることはできません。|
> |**名前**:<br />unManagedidsattachmentinvalidfilesize<br />**16 進数**:<br />80044a02<br />**数値**:<br />-2147202558|添付ファイルのサイズが大きすぎます。|
> |**名前**:<br />unManagedidsattachmentisempty<br />**16 進数**:<br />80044a04<br />**数値**:<br />-2147202556|添付ファイルが空です。|
> |**名前**:<br />unManagedidsbizmgmtbusinessparentdiffmerchant<br />**16 進数**:<br />80041d04<br />**数値**:<br />-2147214076|事業は上位の部署として同じマーチャントにありません。|
> |**名前**:<br />unManagedidsbizmgmtcallernotinpartnerbusiness<br />**16 進数**:<br />80041d14<br />**数値**:<br />-2147214060|呼び出し元はパートナー事業からではありません。|
> |**名前**:<br />unManagedidsbizmgmtcallernotinprimarybusiness<br />**16 進数**:<br />80041d12<br />**数値**:<br />-2147214062|呼び出し元は主事業からではありません。|
> |**名前**:<br />unManagedidsbizmgmtcannotaddlocaluser<br />**16 進数**:<br />80041d32<br />**数値**:<br />-2147214030|ローカル ユーザーは Dynamics 365 には追加できません。|
> |**名前**:<br />unManagedidsbizmgmtcannotdeletebusiness<br />**16 進数**:<br />80041d18<br />**数値**:<br />-2147214056|これは従属部署です。 この従属部署を削除するには IBizMerchant::Delete を使用します。|
> |**名前**:<br />unManagedidsbizmgmtcannotdeleteprovision<br />**16 進数**:<br />80041d19<br />**数値**:<br />-2147214055|これはプロビジョニング済みのルート部署です。 このルート部署を削除するには IBizProvision::Delete を使用します。|
> |**名前**:<br />unManagedidsbizmgmtcannotdisablebusiness<br />**16 進数**:<br />80041d1a<br />**数値**:<br />-2147214054|この部署を無効にすることはできません。|
> |**名前**:<br />unManagedidsbizmgmtcannotdisableprovision<br />**16 進数**:<br />80041d1b<br />**数値**:<br />-2147214053|これはプロビジョニング済みのルート部署です。 このルート部署を無効にするには IBizProvision::Disable を使用します。|
> |**名前**:<br />unManagedidsbizmgmtcannotenablebusiness<br />**16 進数**:<br />80041d1c<br />**数値**:<br />-2147214052|これは従属部署です。 この従属部署を有効にするには IBizMerchant::Enable を使用します。|
> |**名前**:<br />unManagedidsbizmgmtcannotenableprovision<br />**16 進数**:<br />80041d1d<br />**数値**:<br />-2147214051|これはプロビジョニング済みのルート部署です。 このルート部署を有効にするには IBizProvision::Enable を使用します。|
> |**名前**:<br />unManagedidsbizmgmtcannotmovedefaultuser<br />**16 進数**:<br />80041d05<br />**数値**:<br />-2147214075|unManagedidsbizmgmtcannotmovedefaultuser|
> |**名前**:<br />unManagedidsbizmgmtcannotreadaccountcontrol<br />**16 進数**:<br />80041d2d<br />**数値**:<br />-2147214035|指定された Active Directory ユーザーには十分なアクセス許可がありません。 システム管理者にお問い合わせください。|
> |**名前**:<br />unManagedidsbizmgmtcannotremovepartnershipdefaultuser<br />**16 進数**:<br />80041d17<br />**数値**:<br />-2147214057|パートナーシップの既定のユーザーを削除できません。|
> |**名前**:<br />unManagedidsbizmgmtcantchangeorgname<br />**16 進数**:<br />80041d36<br />**数値**:<br />-2147214026|組織名を変更できません。|
> |**名前**:<br />unManagedidsbizmgmtdefaultusernotinbusiness<br />**16 進数**:<br />80041d03<br />**数値**:<br />-2147214077|事業内に既定のユーザーがありません。|
> |**名前**:<br />unManagedidsbizmgmtdefaultusernotinpartnerbusiness<br />**16 進数**:<br />80041d15<br />**数値**:<br />-2147214059|パートナー事業の中に既定のユーザーがありません。|
> |**名前**:<br />unManagedidsbizmgmtdefaultusernotinprimarybusiness<br />**16 進数**:<br />80041d13<br />**数値**:<br />-2147214061|主事業の中に既定のユーザーがありません。|
> |**名前**:<br />unManagedidsbizmgmtmissbusinessname<br />**16 進数**:<br />80041d00<br />**数値**:<br />-2147214080|事業名が予期せず見つかりませんでした。|
> |**名前**:<br />unManagedidsbizmgmtmissparentbusiness<br />**16 進数**:<br />80041d02<br />**数値**:<br />-2147214078|上位の部署が予期せず見つかりませんでした。|
> |**名前**:<br />unManagedidsbizmgmtmisspartnerbusiness<br />**16 進数**:<br />80041d0f<br />**数値**:<br />-2147214065|パートナー事業間のパートナーシップが予期せず見つかりませんでした。|
> |**名前**:<br />unManagedidsbizmgmtmissprimarybusiness<br />**16 進数**:<br />80041d0e<br />**数値**:<br />-2147214066|主事業のパートナーシップが予期せず見つかりませんでした。|
> |**名前**:<br />unManagedidsbizmgmtmissuserdomainname<br />**16 進数**:<br />80041d01<br />**数値**:<br />-2147214079|ユーザーのドメイン名が想定に反して不足しています。|
> |**名前**:<br />unManagedidsbizmgmtnoparentbusiness<br />**16 進数**:<br />80041d29<br />**数値**:<br />-2147214039|指定されたビジネスには、上位の部署はありません。|
> |**名前**:<br />unManagedidsbizmgmtpartnershipalreadyexists<br />**16 進数**:<br />80041d11<br />**数値**:<br />-2147214063|指定した主事業およびパートナー事業間のパートナーシップが、既に存在します。|
> |**名前**:<br />unManagedidsbizmgmtpartnershipnotinpendingstatus<br />**16 進数**:<br />80041d16<br />**数値**:<br />-2147214058|パートナーシップが許可されるか、または却下されました。|
> |**名前**:<br />unManagedidsbizmgmtprimarysameaspartner<br />**16 進数**:<br />80041d10<br />**数値**:<br />-2147214064|主事業とパートナー事業は同じです。|
> |**名前**:<br />unManagedidsbizmgmtusercannotbeownparent<br />**16 進数**:<br />80041d06<br />**数値**:<br />-2147214074|上位ユーザーをユーザーに指定することはできません。|
> |**名前**:<br />unManagedidsbizmgmtuserdoesnothaveparent<br />**16 進数**:<br />80041d1e<br />**数値**:<br />-2147214050|このユーザーに上位ユーザーはありません。|
> |**名前**:<br />unManagedidsbizmgmtusersettingsnotcreated<br />**16 進数**:<br />80041d2b<br />**数値**:<br />-2147214037|指定したユーザー設定がまだ作成されていません。|
> |**名前**:<br />unManagedidscalendarinvalidcalendar<br />**16 進数**:<br />80044d00<br />**数値**:<br />-2147201792|カレンダーが無効です。|
> |**名前**:<br />unManagedidscalendarruledoesnotexist<br />**16 進数**:<br />80045100<br />**数値**:<br />-2147200768|カレンダー ルールは存在しません。|
> |**名前**:<br />unManagedidsCalloutException<br />**16 進数**:<br />80045f05<br />**数値**:<br />-2147197179|コールアウト コードは例外をスローします。|
> |**名前**:<br />unManagedidscalloutinvalidconfig<br />**16 進数**:<br />80045f03<br />**数値**:<br />-2147197181|無効なコールアウト構成|
> |**名前**:<br />unManagedidscalloutinvalidevent<br />**16 進数**:<br />80045f04<br />**数値**:<br />-2147197180|無効なコールアウト イベント|
> |**名前**:<br />unManagedidscalloutisvabort<br />**16 進数**:<br />80045f01<br />**数値**:<br />-2147197183|コールアウト ISV コードが操作を中止しました|
> |**名前**:<br />unManagedidscalloutisvexception<br />**16 進数**:<br />80045f00<br />**数値**:<br />-2147197184|コールアウト ISV コードは例外をスローします。|
> |**名前**:<br />unManagedidscalloutisvstop<br />**16 進数**:<br />80045f02<br />**数値**:<br />-2147197182|コールアウト ISV コードが操作を中止しました|
> |**名前**:<br />unManagedidscannotassigntobusiness<br />**16 進数**:<br />80040221<br />**数値**:<br />-2147220959|マーチャントにオブジェクトを割り当てることはできません。|
> |**名前**:<br />unManagedidscannotdeactivatepricelevel<br />**16 進数**:<br />80043b04<br />**数値**:<br />-2147206396|取引先企業、取引先担当者または製品の既定の価格レベルであるため、価格レベルは非アクティブ化することはできません。|
> |**名前**:<br />unManagedidscannotdefaultprivateview<br />**16 進数**:<br />80040238<br />**数値**:<br />-2147220936|個人用ビューを既定にすることはできません。|
> |**名前**:<br />unManagedidscannotgrantorrevokeaccesstobusiness<br />**16 進数**:<br />8004021e<br />**数値**:<br />-2147220962|マーチャントへのアクセス権を付与する、またはアクセス権を取り消すことはできません。|
> |**名前**:<br />unManagedidscantdisable<br />**16 進数**:<br />80044154<br />**数値**:<br />-2147204780|コンテキストの下でワークフロー ルールが実行されているため、ユーザーを無効にすることができません。|
> |**名前**:<br />unManagedidscascadeemptylinkerror<br />**16 進数**:<br />80045602<br />**数値**:<br />-2147199486|関連リンクが空です|
> |**名前**:<br />unManagedidscascadeinconsistencyerror<br />**16 進数**:<br />80045600<br />**数値**:<br />-2147199488|カスケード マップ情報は一貫していません。|
> |**名前**:<br />unManagedidscascadeundefinedrelationerror<br />**16 進数**:<br />80045601<br />**数値**:<br />-2147199487|関連付けの種類はサポートされていません。|
> |**名前**:<br />unManagedidscascadeunexpectederror<br />**16 進数**:<br />80045603<br />**数値**:<br />-2147199485|伝播操作で予期しないエラーが発生しました|
> |**名前**:<br />unManagedidscommunicationsbadsender<br />**16 進数**:<br />80040b01<br />**数値**:<br />-2147218687|複数の送信者が指定されました|
> |**名前**:<br />unManagedidscommunicationsnoparticipationmask<br />**16 進数**:<br />80040b06<br />**数値**:<br />-2147218682|参加の種類が活動から見つかりません。|
> |**名前**:<br />unManagedidscommunicationsnopartyaddress<br />**16 進数**:<br />80040b00<br />**数値**:<br />-2147218688|オブジェクトのアドレスがパーティで見つからない、またはパーティが電子メール無効としてマークされています。|
> |**名前**:<br />unManagedidscommunicationsnorecipients<br />**16 進数**:<br />80040b05<br />**数値**:<br />-2147218683|組織内の少なくとも 1 つのシステム ユーザーまたはキューが受信者である必要があります|
> |**名前**:<br />unManagedidscommunicationsnosender<br />**16 進数**:<br />80040b02<br />**数値**:<br />-2147218686|電子メール アドレスが指定されておらず、また呼び出し元ユーザーに電子メール アドレスが設定されていません。|
> |**名前**:<br />unManagedidscommunicationsnosenderaddress<br />**16 進数**:<br />80040b08<br />**数値**:<br />-2147218680|送信者には関係者レコードの電子メール アドレスがありません|
> |**名前**:<br />unManagedidscommunicationstemplateinvalidtemplate<br />**16 進数**:<br />80040b07<br />**数値**:<br />-2147218681|テンプレートの本文が無効です。|
> |**名前**:<br />unManagedidscontacthaschildopportunities<br />**16 進数**:<br />80040512<br />**数値**:<br />-2147220206|取引先担当者に下位の営業案件が存在しています。|
> |**名前**:<br />unManagedidscontractaccountmissing<br />**16 進数**:<br />80043201<br />**数値**:<br />-2147208703|取引先企業は、契約を保存する必要があります。|
> |**名前**:<br />unManagedidscontractdoesnotexist<br />**16 進数**:<br />80043207<br />**数値**:<br />-2147208697|契約が存在しません。|
> |**名前**:<br />unManagedidscontractinvalidowner<br />**16 進数**:<br />80043212<br />**数値**:<br />-2147208686|契約の所有者は無効です。|
> |**名前**:<br />unManagedidscontractinvalidstartdateforrenewedcontract<br />**16 進数**:<br />80043217<br />**数値**:<br />-2147208681|更新した契約の開始日を、元の契約の終了日以前にすることはできません。|
> |**名前**:<br />unManagedidscontractinvalidtotalallotments<br />**16 進数**:<br />80043214<br />**数値**:<br />-2147208684|合計サービス単位数が無効です。|
> |**名前**:<br />unManagedidscontractlineitemdoesnotexist<br />**16 進数**:<br />80043208<br />**数値**:<br />-2147208696|契約品目が存在しません。|
> |**名前**:<br />unManagedidscontractopencasesexist<br />**16 進数**:<br />8004320a<br />**数値**:<br />-2147208694|この契約品目に対してオープンしているサポート案件があります。|
> |**名前**:<br />unManagedidscontracttemplateabbreviationexists<br />**16 進数**:<br />80043216<br />**数値**:<br />-2147208682|略名の値は既に存在します。|
> |**名前**:<br />unManagedidscontractunexpected<br />**16 進数**:<br />80043200<br />**数値**:<br />-2147208704|契約で予期しないエラーが発生しました。|
> |**名前**:<br />unManagedidscpbadpassword<br />**16 進数**:<br />80042901<br />**数値**:<br />-2147211007|指定した顧客のポータルユーザー用のパスワードが正しくありません。|
> |**名前**:<br />unManagedidscpdecryptfailed<br />**16 進数**:<br />80042903<br />**数値**:<br />-2147211005|パスワードの復号化に失敗しました。|
> |**名前**:<br />unManagedidscpencryptfailed<br />**16 進数**:<br />80042902<br />**数値**:<br />-2147211006|入力したパスワードの暗号化に失敗しました。|
> |**名前**:<br />unManagedidscpuserdoesnotexist<br />**16 進数**:<br />80042900<br />**数値**:<br />-2147211008|顧客ポータル ユーザーが存在しません、またはパスワードが正しくありません。|
> |**名前**:<br />unManagedidscustomentityalreadyinitialized<br />**16 進数**:<br />80045901<br />**数値**:<br />-2147198719|既にこのスレッドで初期化されているユーザー定義エンティティ インターフェイス。|
> |**名前**:<br />unManagedidscustomentityambiguousrelationship<br />**16 進数**:<br />8004590d<br />**数値**:<br />-2147198707|要求したエンティティ間に複数の関連付けが存在します。|
> |**名前**:<br />unManagedidscustomentityexistingloop<br />**16 進数**:<br />80045907<br />**数値**:<br />-2147198713|データベースに既存のループがあります。|
> |**名前**:<br />unManagedidscustomentityinvalidchild<br />**16 進数**:<br />80045909<br />**数値**:<br />-2147198711|渡された指定の子エンティティは有効ではありません。|
> |**名前**:<br />unManagedidscustomentityinvalidownership<br />**16 進数**:<br />80045903<br />**数値**:<br />-2147198717|ユーザー定義エンティティの所有権の種類マスクが正しく設定されていません。|
> |**名前**:<br />unManagedidscustomentityinvalidparent<br />**16 進数**:<br />8004590a<br />**数値**:<br />-2147198710|渡された指定の親エンティティは有効ではありません。|
> |**名前**:<br />unManagedidscustomentitynameviolation<br />**16 進数**:<br />80045900<br />**数値**:<br />-2147198720|指定されたエンティティが見つかりましたが、ユーザー定義エンティティではありません。|
> |**名前**:<br />unManagedidscustomentitynorelationship<br />**16 進数**:<br />8004590c<br />**数値**:<br />-2147198708|要求したエンティティ間に関連付けが存在しません。|
> |**名前**:<br />unManagedidscustomentitynotinitialized<br />**16 進数**:<br />80045902<br />**数値**:<br />-2147198718|ユーザー定義エンティティ インターフェイスが正しく初期化されませんでした。|
> |**名前**:<br />unManagedidscustomentityparentchildidentical<br />**16 進数**:<br />8004590b<br />**数値**:<br />-2147198709|指定された親と子のエンティティが同じです。|
> |**名前**:<br />unManagedidscustomentitystackoverflow<br />**16 進数**:<br />80045905<br />**数値**:<br />-2147198715|ユーザー定義エンティティ MD スタックのオーバーフロー。|
> |**名前**:<br />unManagedidscustomentitystackunderflow<br />**16 進数**:<br />80045906<br />**数値**:<br />-2147198714|ユーザー定義エンティティ MD スタックのアンダーフロー。|
> |**名前**:<br />unManagedidscustomentitytlsfailure<br />**16 進数**:<br />80045904<br />**数値**:<br />-2147198716|初期化されていないユーザー定義エンティティ MD TLS。|
> |**名前**:<br />unManagedidscustomentitywouldcreateloop<br />**16 進数**:<br />80045908<br />**数値**:<br />-2147198712|この関連付けにより、データベースにループが作成されます。|
> |**名前**:<br />unManagedidscustomeraddresstypeinvalid<br />**16 進数**:<br />80040514<br />**数値**:<br />-2147220204|無効な顧客住所の種類です。|
> |**名前**:<br />unManagedidscustomizationtransformationnotsupported<br />**16 進数**:<br />80044700<br />**数値**:<br />-2147203328|このオブジェクトに対して変換はサポートされていません。|
> |**名前**:<br />unManagedidsdataaccessunexpected<br />**16 進数**:<br />80042300<br />**数値**:<br />-2147212544|予期しないデータ アクセスのエラーです。  DB 接続が正常に開いていないかもしれません。|
> |**名前**:<br />unManagedidsdataoutofrange<br />**16 進数**:<br />8004022c<br />**数値**:<br />-2147220948|範囲外のデータ|
> |**名前**:<br />unManagedidsevalaborted<br />**16 進数**:<br />80042c03<br />**数値**:<br />-2147210237|評価が中止されました。|
> |**名前**:<br />unManagedidsevalallaborted<br />**16 進数**:<br />80042c02<br />**数値**:<br />-2147210238|評価が中止され、以降の処理を停止します。|
> |**名前**:<br />unManagedidsevalallcompleted<br />**16 進数**:<br />80042c0c<br />**数値**:<br />-2147210228|評価が完了し、以降の処理を停止します。|
> |**名前**:<br />unManagedidsevalassignshouldhave4parameters<br />**16 進数**:<br />80042c01<br />**数値**:<br />-2147210239|割り当て操作には 4 つのパラメーターが必要です。|
> |**名前**:<br />unManagedidsevalchangetypeerror<br />**16 進数**:<br />80042c0d<br />**数値**:<br />-2147210227|タイプ エラーを変更します。|
> |**名前**:<br />unManagedidsevalcompleted<br />**16 進数**:<br />80042c04<br />**数値**:<br />-2147210236|評価が完了しました。|
> |**名前**:<br />unManagedidsevalcreateshouldhave2parameters<br />**16 進数**:<br />80042c3c<br />**数値**:<br />-2147210180|作成操作には 2 つのパラメーターが必要です。|
> |**名前**:<br />unManagedidsevalerrorabsparameter<br />**16 進数**:<br />80042c2c<br />**数値**:<br />-2147210196|WFPM_ABS パラメーターを評価中にエラーが発生しました。|
> |**名前**:<br />unManagedidsevalerroractivityattachment<br />**16 進数**:<br />80042c18<br />**数値**:<br />-2147210216|操作活動の添付ファイルでのエラー。|
> |**名前**:<br />unManagedidsevalerroraddparameter<br />**16 進数**:<br />80042c0f<br />**数値**:<br />-2147210225|WFPM_ADD パラメーターを評価中にエラーが発生しました。|
> |**名前**:<br />unManagedidsevalerrorappendtoactivityparty<br />**16 進数**:<br />80042c3f<br />**数値**:<br />-2147210177|unManagedidsevalerrorappendtoactivityparty|
> |**名前**:<br />unManagedidsevalerrorassign<br />**16 進数**:<br />80042c22<br />**数値**:<br />-2147210206|割り当て操作でのエラー。|
> |**名前**:<br />unManagedidsevalerrorbeginwithparameter<br />**16 進数**:<br />80042c38<br />**数値**:<br />-2147210184|WFPM_BEGIN_WITH パラメーターを評価中にエラーが発生しました。|
> |**名前**:<br />unManagedidsevalerrorbetweenparameter<br />**16 進数**:<br />80042c33<br />**数値**:<br />-2147210189|WFPM_BETWEEN パラメーターを評価中にエラーが発生しました。|
> |**名前**:<br />unManagedidsevalerrorcontainparameter<br />**16 進数**:<br />80042c3a<br />**数値**:<br />-2147210182|WFPM_CONTAIN パラメーターを評価中にエラーが発生しました。|
> |**名前**:<br />unManagedidsevalerrorcreate<br />**16 進数**:<br />80042c3b<br />**数値**:<br />-2147210181|更新の作成でのエラー。|
> |**名前**:<br />unManagedidsevalerrorcreateactivity<br />**16 進数**:<br />80042c17<br />**数値**:<br />-2147210217|活動作成の操作でのエラー。|
> |**名前**:<br />unManagedidsevalerrorcreateincident<br />**16 進数**:<br />80042c1d<br />**数値**:<br />-2147210211|インシデント作成の操作でのエラー。|
> |**名前**:<br />unManagedidsevalerrorcreatenote<br />**16 進数**:<br />80042c1b<br />**数値**:<br />-2147210213|メモ作成の操作でのエラー。|
> |**名前**:<br />unManagedidsevalerrordividedbyzero<br />**16 進数**:<br />80042c16<br />**数値**:<br />-2147210218|ゼロで割ります。|
> |**名前**:<br />unManagedidsevalerrordivisionparameter<br />**16 進数**:<br />80042c13<br />**数値**:<br />-2147210221|WFPM_DIVISION パラメーターを評価中にエラーが発生しました。|
> |**名前**:<br />unManagedidsevalerrordivisionparameters<br />**16 進数**:<br />80042c12<br />**数値**:<br />-2147210222|事業部パラメーターは サブパラメーターを 2 つのみ設定できます。|
> |**名前**:<br />unManagedidsevalerroremailtemplate<br />**16 進数**:<br />80042c21<br />**数値**:<br />-2147210207|電子メール テンプレートの操作でのエラー。|
> |**名前**:<br />unManagedidsevalerrorendwithparameter<br />**16 進数**:<br />80042c39<br />**数値**:<br />-2147210183|WFPM_END_WITH パラメーターを評価中にエラーが発生しました。|
> |**名前**:<br />unManagedidsevalerroreqparameter<br />**16 進数**:<br />80042c31<br />**数値**:<br />-2147210191|WFPM_EQ パラメーターを評価中にエラーが発生しました。|
> |**名前**:<br />unManagedidsevalerrorexec<br />**16 進数**:<br />80042c27<br />**数値**:<br />-2147210201|操作 exec でのエラー。|
> |**名前**:<br />unManagedidsevalerrorformatbooleanparameter<br />**16 進数**:<br />80042c45<br />**数値**:<br />-2147210171|WFPM_FORMAT_BOOLEAN パラメーターを評価する際に発生するエラー。|
> |**名前**:<br />unManagedidsevalerrorformatdatetimeparameter<br />**16 進数**:<br />80042c44<br />**数値**:<br />-2147210172|WFPM_FORMAT_DATETIME パラメーターを評価する際に発生するエラー。|
> |**名前**:<br />unManagedidsevalerrorformatdecimalparameter<br />**16 進数**:<br />80042c4a<br />**数値**:<br />-2147210166|WFPM_FORMAT_DECIMAL パラメーターを評価する際に発生するエラー。|
> |**名前**:<br />unManagedidsevalerrorformatintegerparameter<br />**16 進数**:<br />80042c49<br />**数値**:<br />-2147210167|WFPM_FORMAT_INTEGER パラメーターを評価する際に発生するエラー。|
> |**名前**:<br />unManagedidsevalerrorformatlookupparameter<br />**16 進数**:<br />80042c4c<br />**数値**:<br />-2147210164|WFPM_FORMAT_LOOKUP パラメーターを評価する際に発生するエラー。|
> |**名前**:<br />unManagedidsevalerrorformatpicklistparameter<br />**16 進数**:<br />80042c46<br />**数値**:<br />-2147210170|WFPM_FORMAT_PICKLIST パラメーターを評価する際に発生するエラー。|
> |**名前**:<br />unManagedidsevalerrorformattimezonecodeparameter<br />**16 進数**:<br />80042c4b<br />**数値**:<br />-2147210165|unManagedidsevalerrorformattimezonecodeparameter|
> |**名前**:<br />unManagedidsevalerrorgeqparameter<br />**16 進数**:<br />80042c2e<br />**数値**:<br />-2147210194|WFPM_GEQ パラメーターを評価中にエラーが発生しました。|
> |**名前**:<br />unManagedidsevalerrorgtparameter<br />**16 進数**:<br />80042c2d<br />**数値**:<br />-2147210195|WFPM_GT パラメーターを評価中にエラーが発生しました。|
> |**名前**:<br />unManagedidsevalerrorhalt<br />**16 進数**:<br />80042c28<br />**数値**:<br />-2147210200|操作 halt でのエラー。|
> |**名前**:<br />unManagedidsevalerrorhandleactivity<br />**16 進数**:<br />80042c19<br />**数値**:<br />-2147210215|処理活動の操作でのエラー。|
> |**名前**:<br />unManagedidsevalerrorhandleincident<br />**16 進数**:<br />80042c1e<br />**数値**:<br />-2147210210|処理インシデントの操作でのエラー。|
> |**名前**:<br />unManagedidsevalerrorincidentqueue<br />**16 進数**:<br />80042c29<br />**数値**:<br />-2147210199|INCIDENT_QUEUE を評価できませんでした。|
> |**名前**:<br />unManagedidsevalerrorinlistparameter<br />**16 進数**:<br />80042c42<br />**数値**:<br />-2147210174|unManagedidsevalerrorinlistparameter|
> |**名前**:<br />unManagedidsevalerrorinparameter<br />**16 進数**:<br />80042c34<br />**数値**:<br />-2147210188|WFPM_IN パラメーターを評価中にエラーが発生しました。|
> |**名前**:<br />unManagedidsevalerrorinvalidparameter<br />**16 進数**:<br />80042c2b<br />**数値**:<br />-2147210197|無効なパラメーターです。|
> |**名前**:<br />unManagedidsevalerrorinvalidrecipient<br />**16 進数**:<br />80042c35<br />**数値**:<br />-2147210187|無効な電子メール受信者です。|
> |**名前**:<br />unManagedidsevalerrorisnulllistparameter<br />**16 進数**:<br />80042c43<br />**数値**:<br />-2147210173|unManagedidsevalerrorisnulllistparameter|
> |**名前**:<br />unManagedidsevalerrorleqparameter<br />**16 進数**:<br />80042c30<br />**数値**:<br />-2147210192|WFPM_LEQ パラメーターを評価中にエラーが発生しました。|
> |**名前**:<br />unManagedidsevalerrorltparameter<br />**16 進数**:<br />80042c2f<br />**数値**:<br />-2147210193|WFPM_LT パラメーターを評価中にエラーが発生しました。|
> |**名前**:<br />unManagedidsevalerrormodulusparameter<br />**16 進数**:<br />80042c15<br />**数値**:<br />-2147210219|WFPM_MODULUR パラメーターを評価中にエラーが発生しました。|
> |**名前**:<br />unManagedidsevalerrormodulusparameters<br />**16 進数**:<br />80042c14<br />**数値**:<br />-2147210220|モジュール パラメーターは サブパラメーターを 2 つのみ設定できます。|
> |**名前**:<br />unManagedidsevalerrormultiplicationparameter<br />**16 進数**:<br />80042c11<br />**数値**:<br />-2147210223|WFPM_MULTIPLICATION パラメーターを評価中にエラーが発生しました。|
> |**名前**:<br />unManagedidsevalerrorneqparameter<br />**16 進数**:<br />80042c32<br />**数値**:<br />-2147210190|WFPM_NEQ パラメーターを評価中にエラーが発生しました。|
> |**名前**:<br />unManagedidsevalerrornoteattachment<br />**16 進数**:<br />80042c1c<br />**数値**:<br />-2147210212|メモ添付ファイルの操作でのエラー。|
> |**名前**:<br />unManagedidsevalerrorobjecttype<br />**16 進数**:<br />80042c48<br />**数値**:<br />-2147210168|WFPM_GetObjectType パラメーターを評価する際に発生するエラー。|
> |**名前**:<br />unManagedidsevalerrorposturl<br />**16 進数**:<br />80042c26<br />**数値**:<br />-2147210202|URL への送信操作でのエラー。|
> |**名前**:<br />unManagedidsevalerrorqueueidparameter<br />**16 進数**:<br />80042c47<br />**数値**:<br />-2147210169|unManagedidsevalerrorqueueidparameter|
> |**名前**:<br />unManagedidsevalerrorremovefromactivityparty<br />**16 進数**:<br />80042c40<br />**数値**:<br />-2147210176|unManagedidsevalerrorremovefromactivityparty|
> |**名前**:<br />unManagedidsevalerrorroute<br />**16 進数**:<br />80042c24<br />**数値**:<br />-2147210204|ルートの操作でのエラー。|
> |**名前**:<br />unManagedidsevalerrorsendemail<br />**16 進数**:<br />80042c20<br />**数値**:<br />-2147210208|電子メール送信の操作でのエラー。|
> |**名前**:<br />unManagedidsevalerrorsetactivityparty<br />**16 進数**:<br />80042c41<br />**数値**:<br />-2147210175|unManagedidsevalerrorsetactivityparty|
> |**名前**:<br />unManagedidsevalerrorsetstate<br />**16 進数**:<br />80042c25<br />**数値**:<br />-2147210203|状態設定の操作でのエラー。|
> |**名前**:<br />unManagedidsevalerrorstrlenparameter<br />**16 進数**:<br />80042c37<br />**数値**:<br />-2147210185|WFPM_STRLEN パラメーターを評価中にエラーが発生しました。|
> |**名前**:<br />unManagedidsevalerrorsubstrparameter<br />**16 進数**:<br />80042c36<br />**数値**:<br />-2147210186|WFPM_SUBSTR パラメーターを評価中にエラーが発生しました。|
> |**名前**:<br />unManagedidsevalerrorsubtractionparameter<br />**16 進数**:<br />80042c10<br />**数値**:<br />-2147210224|WFPM_SUBTRACTION パラメーターを評価中にエラーが発生しました。|
> |**名前**:<br />unManagedidsevalerrorunhandleactivity<br />**16 進数**:<br />80042c1a<br />**数値**:<br />-2147210214|非処理活動の操作でのエラー。|
> |**名前**:<br />unManagedidsevalerrorunhandleincident<br />**16 進数**:<br />80042c1f<br />**数値**:<br />-2147210209|非処理インシデントの操作でのエラー。|
> |**名前**:<br />unManagedidsevalerrorupdate<br />**16 進数**:<br />80042c23<br />**数値**:<br />-2147210205|更新操作でのエラー。|
> |**名前**:<br />unManagedidsevalgenericerror<br />**16 進数**:<br />80042c2a<br />**数値**:<br />-2147210198|評価エラー。|
> |**名前**:<br />unManagedidsevalmetabaseattributenotfound<br />**16 進数**:<br />80042c08<br />**数値**:<br />-2147210232|指定したメタベース属性が存在しません。|
> |**名前**:<br />unManagedidsevalmetabaseattributenotmatchquery<br />**16 進数**:<br />80042c0b<br />**数値**:<br />-2147210229|指定された refattributeid は WFPM_SELECT パラメーターのクエリではありません。|
> |**名前**:<br />unManagedidsevalmetabaseentitycompoundkeys<br />**16 進数**:<br />80042c07<br />**数値**:<br />-2147210233|指定したメタベース オブジェクトに複合キーがあります。 複合キー エンティティはまだサポートされていません。|
> |**名前**:<br />unManagedidsevalmetabaseentitynotmatchquery<br />**16 進数**:<br />80042c0a<br />**数値**:<br />-2147210230|指定された refentityid は WFPM_SELECT パラメーターのクエリではありません。|
> |**名前**:<br />unManagedidsevalmissselectquery<br />**16 進数**:<br />80042c0e<br />**数値**:<br />-2147210226|選択したパラメーターにクエリのサブパラメーターがありません。|
> |**名前**:<br />unManagedidsevalobjectnotfound<br />**16 進数**:<br />80042c05<br />**数値**:<br />-2147210235|必要なオブジェクトは存在しません。|
> |**名前**:<br />unManagedidsevalpropertyisnull<br />**16 進数**:<br />80042c09<br />**数値**:<br />-2147210231|オブジェクトの必須プロパティは設定されませんでした。|
> |**名前**:<br />unManagedidsevalpropertynotfound<br />**16 進数**:<br />80042c06<br />**数値**:<br />-2147210234|オブジェクトの必須プロパティは見つかりませんでした。|
> |**名前**:<br />unManagedidsevaltimererrorcalculatescheduletime<br />**16 進数**:<br />80042c3e<br />**数値**:<br />-2147210178|タイマー アクションのスケジュール期間の計算に失敗しました。|
> |**名前**:<br />unManagedidsevaltimerinvalidparameternumber<br />**16 進数**:<br />80042c3d<br />**数値**:<br />-2147210179|タイマー アクションのパラメーターが無効です。|
> |**名前**:<br />unManagedidsevalupdateshouldhave3parameters<br />**16 進数**:<br />80042c00<br />**数値**:<br />-2147210240|更新操作には 3 つのパラメーターが必要です。|
> |**名前**:<br />unManagedidsfailureinittoken<br />**16 進数**:<br />8004020f<br />**数値**:<br />-2147220977|ユーザー トークンの取得に失敗しました。|
> |**名前**:<br />unManagedidsfetchbetweentext<br />**16 進数**:<br />80044153<br />**数値**:<br />-2147204781|"between"、"not-between"、"in"、"not-in" 演算子は、種類が text または ntext の属性に対して使用できません。|
> |**名前**:<br />unManagedidsfulltextoperationfailed<br />**16 進数**:<br />80043e06<br />**数値**:<br />-2147205626|フルテキスト操作に失敗しました。|
> |**名前**:<br />unManagedidsincidentassociatedactivitycorrupted<br />**16 進数**:<br />80044405<br />**数値**:<br />-2147204091|このサポート案件に関連付けられている活動は破損しています。|
> |**名前**:<br />unManagedidsincidentcannotclose<br />**16 進数**:<br />8004440a<br />**数値**:<br />-2147204086|このインシデントに対するオープンしている活動があるため、インシデントはクローズできません。|
> |**名前**:<br />unManagedidsincidentcontractdetaildoesnotmatchcontract<br />**16 進数**:<br />80044402<br />**数値**:<br />-2147204094|この契約品目は指定した契約にありません。|
> |**名前**:<br />unManagedidsincidentinvalidactivitytypecode<br />**16 進数**:<br />80044406<br />**数値**:<br />-2147204090|activitytypecode が間違っています。|
> |**名前**:<br />unManagedidsincidentinvalidstate<br />**16 進数**:<br />80044404<br />**数値**:<br />-2147204092|インシデントの状態が無効です。|
> |**名前**:<br />unManagedidsincidentmissingactivityobjecttype<br />**16 進数**:<br />80044408<br />**数値**:<br />-2147204088|オブジェクトの種類コードが指定されていません。|
> |**名前**:<br />unManagedidsincidentnullactivitytypecode<br />**16 進数**:<br />80044407<br />**数値**:<br />-2147204089|activitytypecode を NULL にすることはできません。|
> |**名前**:<br />unManagedidsincidentparentaccountandparentcontactnotpresent<br />**16 進数**:<br />80044410<br />**数値**:<br />-2147204080|上位の取引先担当者または取引先企業を指定する必要があります。|
> |**名前**:<br />unManagedidsincidentparentaccountandparentcontactpresent<br />**16 進数**:<br />8004440f<br />**数値**:<br />-2147204081|取引先担当者の上司またはアカウントを指定できますが、両方指定することはできません。|
> |**名前**:<br />unManagedidsinvalidassociation<br />**16 進数**:<br />80040211<br />**数値**:<br />-2147220975|無効な関連付けです。|
> |**名前**:<br />unManagedidsinvalidbusinessid<br />**16 進数**:<br />80040209<br />**数値**:<br />-2147220983|無効な事業 ID です。|
> |**名前**:<br />unManagedidsinvaliditemid<br />**16 進数**:<br />8004020b<br />**数値**:<br />-2147220981|無効なアイテム ID です。|
> |**名前**:<br />unManagedidsinvalidorgid<br />**16 進数**:<br />8004020a<br />**数値**:<br />-2147220982|無効な組織 ID です。|
> |**名前**:<br />unManagedidsinvalidowninguser<br />**16 進数**:<br />80040212<br />**数値**:<br />-2147220974|アイテムに所有ユーザーがありません。|
> |**名前**:<br />unManagedidsinvalidteamid<br />**16 進数**:<br />80040208<br />**数値**:<br />-2147220984|無効なチーム ID です。|
> |**名前**:<br />unManagedidsinvaliduserid<br />**16 進数**:<br />80040207<br />**数値**:<br />-2147220985|ユーザー ID が無効か、見つかりません。|
> |**名前**:<br />unManagedidsinvaliduseridorbusinessidorusersbusinessinvalid<br />**16 進数**:<br />8004021d<br />**数値**:<br />-2147220963|次のいずれかが発生しました: 無効なユーザー ID、無効な事業 ID または事業に所属していないユーザー。|
> |**名前**:<br />unManagedidsinvalidvisibility<br />**16 進数**:<br />8004020e<br />**数値**:<br />-2147220978|表示状態が無効です|
> |**名前**:<br />unManagedidsinvalidvisibilitymodificationaccess<br />**16 進数**:<br />80040213<br />**数値**:<br />-2147220973|ユーザーにはこのアイテムの表示を変更するアクセス権がありません。|
> |**名前**:<br />unManagedidsinvoicecloseapideprecated<br />**16 進数**:<br />80043b25<br />**数値**:<br />-2147206363|請求書クローズ API は廃止です。 支払いおよびキャンセル API に置き換えられています。|
> |**名前**:<br />unManagedidsjournalinginvalideventtype<br />**16 進数**:<br />80040803<br />**数値**:<br />-2147219453|イベントの種類が無効です。|
> |**名前**:<br />unManagedidsjournalingmissingaccountid<br />**16 進数**:<br />80040806<br />**数値**:<br />-2147219450|取引先企業 ID がありません。|
> |**名前**:<br />unManagedidsjournalingmissingcontactid<br />**16 進数**:<br />80040808<br />**数値**:<br />-2147219448|取引先担当者 ID がありません。|
> |**名前**:<br />unManagedidsjournalingmissingeventdirection<br />**16 進数**:<br />80040802<br />**数値**:<br />-2147219454|イベント通信方向コードがありません。|
> |**名前**:<br />unManagedidsjournalingmissingeventtype<br />**16 進数**:<br />80040804<br />**数値**:<br />-2147219452|イベントの種類がありません。|
> |**名前**:<br />unManagedidsjournalingmissingincidentid<br />**16 進数**:<br />80040809<br />**数値**:<br />-2147219447|インシデント ID が失われています。|
> |**名前**:<br />unManagedidsjournalingmissingleadid<br />**16 進数**:<br />80040805<br />**数値**:<br />-2147219451|リード ID がありません。|
> |**名前**:<br />unManagedidsjournalingmissingopportunityid<br />**16 進数**:<br />80040807<br />**数値**:<br />-2147219449|営業案件 ID がありません|
> |**名前**:<br />unManagedidsjournalingunsupportedobjecttype<br />**16 進数**:<br />80040801<br />**数値**:<br />-2147219455|操作中にサポートされていないオブジェクトの種類が渡されました。|
> |**名前**:<br />unManagedidsleaddoesnotexist<br />**16 進数**:<br />80040501<br />**数値**:<br />-2147220223|リードが存在しません。|
> |**名前**:<br />unManagedidsleadnoparent<br />**16 進数**:<br />8004050b<br />**数値**:<br />-2147220213|潜在顧客には上位がありません。|
> |**名前**:<br />unManagedidsleadnotassigned<br />**16 進数**:<br />8004050c<br />**数値**:<br />-2147220212|そのリードは割り当てられていません。|
> |**名前**:<br />unManagedidsleadnotassignedtocaller<br />**16 進数**:<br />80040513<br />**数値**:<br />-2147220205|潜在顧客は承認用に呼び出し元に割り当てられていません。|
> |**名前**:<br />unManagedidsleadoneaccount<br />**16 進数**:<br />80040510<br />**数値**:<br />-2147220208|潜在顧客と関連付けることのできる取引先企業は 1 つだけです。|
> |**名前**:<br />unManagedidsleadusercannotreject<br />**16 進数**:<br />8004050d<br />**数値**:<br />-2147220211|ユーザーに潜在顧客を拒否する特権がないため、潜在顧客を承認に割り当てることはできません。|
> |**名前**:<br />unManagedidsmergedifferentbizorgerror<br />**16 進数**:<br />80045303<br />**数値**:<br />-2147200253|別のビジネス エンティティからのエンティティ上では統合は実行できません。|
> |**名前**:<br />unManagedidsmetadatanoentity<br />**16 進数**:<br />80040e00<br />**数値**:<br />-2147217920|指定されたエンティティは存在しません|
> |**名前**:<br />unManagedidsmetadatanorelationship<br />**16 進数**:<br />80040e02<br />**数値**:<br />-2147217918|関連付けが存在しません|
> |**名前**:<br />unManagedidsnorelationship<br />**16 進数**:<br />80040236<br />**数値**:<br />-2147220938|指定されたオブジェクトの間に関連付けは存在しません。|
> |**名前**:<br />unManagedidsnotesalreadyattached<br />**16 進数**:<br />80041701<br />**数値**:<br />-2147215615|指定されたメモは既にオブジェクトに添付されています。|
> |**名前**:<br />unManagedidsnotesloopbeingcreated<br />**16 進数**:<br />80041703<br />**数値**:<br />-2147215613|この上位下位の関連付けを作成すると、注釈階層にループが生成されます。|
> |**名前**:<br />unManagedidsnotesloopexists<br />**16 進数**:<br />80041702<br />**数値**:<br />-2147215614|注釈階層にループが存在します。|
> |**名前**:<br />unManagedidsnotesnoattachment<br />**16 進数**:<br />80041704<br />**数値**:<br />-2147215612|指定されたメモには添付ファイルはありません。|
> |**名前**:<br />unManagedidsnotesnotedoesnotexist<br />**16 進数**:<br />80041700<br />**数値**:<br />-2147215616|指定されたメモは存在しません。|
> |**名前**:<br />unManagedidsopportunitydoesnotexist<br />**16 進数**:<br />80040500<br />**数値**:<br />-2147220224|営業案件が存在しません。|
> |**名前**:<br />unManagedidsopportunityinvalidparent<br />**16 進数**:<br />80040504<br />**数値**:<br />-2147220220|上位営業案件は、取引先企業または取引先担当者でなければなりません。|
> |**名前**:<br />unManagedidsopportunitymissingparent<br />**16 進数**:<br />80040505<br />**数値**:<br />-2147220219|上位営業案件がありません。|
> |**名前**:<br />unManagedidsopportunityoneaccount<br />**16 進数**:<br />8004050e<br />**数値**:<br />-2147220210|営業案件と関連付けることのできる取引先企業は 1 つだけです。|
> |**名前**:<br />unManagedidsopportunityorphan<br />**16 進数**:<br />8004050f<br />**数値**:<br />-2147220209|この関連付けを削除すると、営業案件の親が失われます。|
> |**名前**:<br />unManagedidsoutofmemory<br />**16 進数**:<br />80040222<br />**数値**:<br />-2147220958|メモリ不足です。|
> |**名前**:<br />unManagedidsownernotenabled<br />**16 進数**:<br />8004022b<br />**数値**:<br />-2147220949|指定された所有者が無効にされました。|
> |**名前**:<br />unManagedidspresentuseridandteamid<br />**16 進数**:<br />8004021c<br />**数値**:<br />-2147220964|ユーザー ID およびチーム ID の両方が存在します。 1 つのみが存在する必要があります。|
> |**名前**:<br />unManagedidspropbagattributealreadyset<br />**16 進数**:<br />8004203f<br />**数値**:<br />-2147213249|渡された属性の 1 つが既に設定されています|
> |**名前**:<br />unManagedidspropbagattributenotnullable<br />**16 進数**:<br />8004203e<br />**数値**:<br />-2147213250|渡された属性の 1 つを NULL にすることはできません。|
> |**名前**:<br />unManagedidspropbagcolloutofrange<br />**16 進数**:<br />8004201e<br />**数値**:<br />-2147213282|コレクションのバッグ インデックスは範囲外です。|
> |**名前**:<br />unManagedidspropbagnointerface<br />**16 進数**:<br />80042001<br />**数値**:<br />-2147213311|プロパティ バッグ インターフェイスが見つかりませんでした。|
> |**名前**:<br />unManagedidspropbagnullproperty<br />**16 進数**:<br />80042002<br />**数値**:<br />-2147213310|プロパティ バッグの中で、指定されたプロパティは null でした。|
> |**名前**:<br />unManagedidspropbagpropertynotfound<br />**16 進数**:<br />80042000<br />**数値**:<br />-2147213312|プロパティ バッグの中に、指定されたプロパティが見つかりませんでした。|
> |**名前**:<br />unManagedidsqueuemissingbusinessunitid<br />**16 進数**:<br />80043e03<br />**数値**:<br />-2147205629|businessunitid がありません。|
> |**名前**:<br />unManagedidsqueueorganizationidnotmatch<br />**16 進数**:<br />80043e04<br />**数値**:<br />-2147205628|呼び出し元の組織 ID は businessunit の 組織 ID に対応しません。|
> |**名前**:<br />unManagedidsrcsyncfilternoaccess<br />**16 進数**:<br />8004410f<br />**数値**:<br />-2147204849|オフラインにできません: 必要なエンティティのアクセス権がありません。|
> |**名前**:<br />unManagedidsrcsyncinvalidfiltererror<br />**16 進数**:<br />8004410d<br />**数値**:<br />-2147204851|無効なフィルターが指定されました。|
> |**名前**:<br />unManagedidsrcsyncinvalidsubscription<br />**16 進数**:<br />80044109<br />**数値**:<br />-2147204855|指定したサブスクリプションは存在しません。|
> |**名前**:<br />unManagedidsrcsyncinvalidsynctime<br />**16 進数**:<br />80044100<br />**数値**:<br />-2147204864|指定された同期時刻は無効です。  同期時間は、前回の同期で返された時間よりも早くすることはできません。サブスクリプションを再初期化してください。|
> |**名前**:<br />unManagedidsrcsyncmethodnone<br />**16 進数**:<br />80044114<br />**数値**:<br />-2147204844|同期方法が [なし] に設定されているため、このコンピューターでは同期タスクを実行できません。|
> |**名前**:<br />unManagedidsrcsyncmsxmlfailed<br />**16 進数**:<br />80044101<br />**数値**:<br />-2147204863|unManagedidsrcsyncmsxmlfailed|
> |**名前**:<br />unManagedidsrcsyncnoclient<br />**16 進数**:<br />80044113<br />**数値**:<br />-2147204845|クライアントが存在しません。|
> |**名前**:<br />unManagedidsrcsyncnoprimary<br />**16 進数**:<br />80044112<br />**数値**:<br />-2147204846|主なクライアントが存在しません。|
> |**名前**:<br />unManagedidsrcsyncnotprimary<br />**16 進数**:<br />80044111<br />**数値**:<br />-2147204847|同期できません: プライマリ OutlookSync クライアントではありません。|
> |**名前**:<br />unManagedidsrcsyncsoapconnfailed<br />**16 進数**:<br />80044103<br />**数値**:<br />-2147204861|unManagedidsrcsyncsoapconnfailed|
> |**名前**:<br />unManagedidsrcsyncsoapfaulterror<br />**16 進数**:<br />80044106<br />**数値**:<br />-2147204858|unManagedidsrcsyncsoapfaulterror|
> |**名前**:<br />unManagedidsrcsyncsoapgenfailed<br />**16 進数**:<br />80044102<br />**数値**:<br />-2147204862|unManagedidsrcsyncsoapgenfailed|
> |**名前**:<br />unManagedidsrcsyncsoapparseerror<br />**16 進数**:<br />80044108<br />**数値**:<br />-2147204856|unManagedidsrcsyncsoapparseerror|
> |**名前**:<br />unManagedidsrcsyncsoapreaderror<br />**16 進数**:<br />80044107<br />**数値**:<br />-2147204857|unManagedidsrcsyncsoapreaderror|
> |**名前**:<br />unManagedidsrcsyncsoapsendfailed<br />**16 進数**:<br />80044104<br />**数値**:<br />-2147204860|unManagedidsrcsyncsoapsendfailed|
> |**名前**:<br />unManagedidsrcsyncsoapservererror<br />**16 進数**:<br />80044105<br />**数値**:<br />-2147204859|unManagedidsrcsyncsoapservererror|
> |**名前**:<br />unManagedidsrcsyncsqlgenericerror<br />**16 進数**:<br />80044110<br />**数値**:<br />-2147204848|unManagedidsrcsyncsqlgenericerror|
> |**名前**:<br />unManagedidsrcsyncsqlpausederror<br />**16 進数**:<br />8004410c<br />**数値**:<br />-2147204852|unManagedidsrcsyncsqlpausederror|
> |**名前**:<br />unManagedidsrcsyncsqlstoppederror<br />**16 進数**:<br />8004410b<br />**数値**:<br />-2147204853|unManagedidsrcsyncsqlstoppederror|
> |**名前**:<br />unManagedidsrcsyncsubscriptionowner<br />**16 進数**:<br />8004410a<br />**数値**:<br />-2147204854|呼び出し元 ID がサブスクリプションの所有者 ID と一致しません。サブスクリプションに対する操作を実行できるのは、サブスクリプションの所有者のみです。|
> |**名前**:<br />unManagedidsrolesdeletenonparentrole<br />**16 進数**:<br />8004140c<br />**数値**:<br />-2147216372|上位の部署から継承されたロールは削除できません。|
> |**名前**:<br />unManagedidsrolesinvalidroledata<br />**16 進数**:<br />80041400<br />**数値**:<br />-2147216384|ロール データが無効です。|
> |**名前**:<br />unManagedidsrolesinvalidroleid<br />**16 進数**:<br />80041401<br />**数値**:<br />-2147216383|無効なロール ID です。|
> |**名前**:<br />unManagedidsrolesinvalidrolename<br />**16 進数**:<br />8004140a<br />**数値**:<br />-2147216374|ロール名が無効です。|
> |**名前**:<br />unManagedidsrolesinvalidtemplateid<br />**16 進数**:<br />80041404<br />**数値**:<br />-2147216380|無効なロール テンプレート ID です。|
> |**名前**:<br />unManagedidsrolesmissbusinessid<br />**16 進数**:<br />80041406<br />**数値**:<br />-2147216378|ロールの部署 ID が予期せず見つかりませんでした。|
> |**名前**:<br />unManagedidsrolesmissprivid<br />**16 進数**:<br />80041408<br />**数値**:<br />-2147216376|特権 ID が予期せず見つかりませんでした。|
> |**名前**:<br />unManagedidsrolesmissroleid<br />**16 進数**:<br />80041405<br />**数値**:<br />-2147216379|ロール ID が予期せず見つかりませんでした。|
> |**名前**:<br />unManagedidsrolesmissrolename<br />**16 進数**:<br />80041407<br />**数値**:<br />-2147216377|ロール名が想定に反して不足しています。|
> |**名前**:<br />unManagedidsrolesroledoesnotexist<br />**16 進数**:<br />80041402<br />**数値**:<br />-2147216382|指定されたロールは存在しません。|
> |**名前**:<br />unManagedidsrspropbagdbinfoalreadyset<br />**16 進数**:<br />8004203d<br />**数値**:<br />-2147213251|レコード セット プロパティ バッグのDBの情報は既に設定されています。|
> |**名前**:<br />unManagedidsrspropbagdbinfonotset<br />**16 進数**:<br />8004203c<br />**数値**:<br />-2147213252|レコード セット プロパティ バッグのDBの情報は設定されませんでした。|
> |**名前**:<br />unManagedidssalespeopleduplicatecalendarfound<br />**16 進数**:<br />80043802<br />**数値**:<br />-2147207166|この営業担当者/年に対する重複会計カレンダーが見つかりました|
> |**名前**:<br />unManagedidssalespeopleinvalidfiscalcalendartype<br />**16 進数**:<br />80043808<br />**数値**:<br />-2147207160|無効な会計カレンダーの種類|
> |**名前**:<br />unManagedidssalespeopleinvalidfiscalperiodindex<br />**16 進数**:<br />80043807<br />**数値**:<br />-2147207161|無効な会計期間インデックス|
> |**名前**:<br />unManagedidssalespeopleinvalidterritoryobjecttype<br />**16 進数**:<br />80043804<br />**数値**:<br />-2147207164|担当地域はこの種類のオブジェクトからは取得できません|
> |**名前**:<br />unManagedidssqlerror<br />**16 進数**:<br />80044150<br />**数値**:<br />-2147204784|一般的な SQL エラー。|
> |**名前**:<br />unManagedidssqltimeouterror<br />**16 進数**:<br />80044151<br />**数値**:<br />-2147204783|SQL がタイムアウトしました。|
> |**名前**:<br />unManagedidsstatedoesnotexist<br />**16 進数**:<br />80043af9<br />**数値**:<br />-2147206407|状態はこのオブジェクトに対して無効です。|
> |**名前**:<br />unManagedidsusernotenabled<br />**16 進数**:<br />80040225<br />**数値**:<br />-2147220955|指定されたユーザーは無効であるか、または任意の部署のメンバーではありません。|
> |**名前**:<br />unManagedidsviewisnotsharable<br />**16 進数**:<br />80040232<br />**数値**:<br />-2147220942|ビューを共有できません。|
> |**名前**:<br />unManagedidsxmlinvalidcollectionname<br />**16 進数**:<br />80041a03<br />**数値**:<br />-2147214845|指定されたコレクション名が正しくありません|
> |**名前**:<br />unManagedidsxmlinvalidcreate<br />**16 進数**:<br />80041a01<br />**数値**:<br />-2147214847|作成に無効なフィールドが指定されました|
> |**名前**:<br />unManagedidsxmlinvalidentityattributes<br />**16 進数**:<br />80041a06<br />**数値**:<br />-2147214842|無効な属性|
> |**名前**:<br />unManagedidsxmlinvalidentityname<br />**16 進数**:<br />80041a00<br />**数値**:<br />-2147214848|指定されたエンティティ名が正しくありません|
> |**名前**:<br />unManagedidsxmlinvalidfield<br />**16 進数**:<br />80041a07<br />**数値**:<br />-2147214841|無効な値はフィールドに渡されました|
> |**名前**:<br />unManagedidsxmlinvalidread<br />**16 進数**:<br />80041a08<br />**数値**:<br />-2147214840|読み込みに無効なフィールドが指定されました|
> |**名前**:<br />unManagedidsxmlinvalidupdate<br />**16 進数**:<br />80041a02<br />**数値**:<br />-2147214846|更新に無効なフィールドが指定されました|
> |**名前**:<br />unManagedidsxmlparseerror<br />**16 進数**:<br />80041a04<br />**数値**:<br />-2147214844|XML で解析エラーが検出されました|
> |**名前**:<br />unManagedidsxmlunexpected<br />**16 進数**:<br />80041a05<br />**数値**:<br />-2147214843|予期しないエラーが発生しました|
> |**名前**:<br />unManagedinvalddbtimefield<br />**16 進数**:<br />800404d9<br />**数値**:<br />-2147220263|プラットフォームは dbtime フィールドを処理することはできません。|
> |**名前**:<br />unManagedinvalidargumentsforcondition<br />**16 進数**:<br />800404b7<br />**数値**:<br />-2147220297|引数の無効な値は条件に指定されました。|
> |**名前**:<br />unManagedinvalidbinaryfield<br />**16 進数**:<br />800404dc<br />**数値**:<br />-2147220260|プラットフォームはバイナリ フィールドを処理することはできません。|
> |**名前**:<br />unManagedinvalidbusinessunitid<br />**16 進数**:<br />800404a7<br />**数値**:<br />-2147220313|businessunitid が見つからないか、無効です。|
> |**名前**:<br />unManagedinvalidcharacterdataforaggregate<br />**16 進数**:<br />800404de<br />**数値**:<br />-2147220258|文字データは、集計をクリアする場合、無効になります。|
> |**名前**:<br />unManagedinvalidcountvalue<br />**16 進数**:<br />800404c1<br />**数値**:<br />-2147220287|カウント値が無効か、見つかりません。|
> |**名前**:<br />unManagedinvaliddbdatefield<br />**16 進数**:<br />800404da<br />**数値**:<br />-2147220262|プラットフォームは dbdate フィールドを処理することはできません。|
> |**名前**:<br />unManagedinvaliddynamicparameteraccessor<br />**16 進数**:<br />800404d5<br />**数値**:<br />-2147220267|SetParam が DynamicParameterAccessor パラメーターの処理に失敗しました。|
> |**名前**:<br />unManagedinvalidequalityoperand<br />**16 進数**:<br />800404ac<br />**数値**:<br />-2147220308|等価演算子には、QB_LITERAL のみサポートされます。|
> |**名前**:<br />unManagedinvalidescapedxml<br />**16 進数**:<br />800404a1<br />**数値**:<br />-2147220319|予想通りではないエスケープされた xml サイズ。|
> |**名前**:<br />unManagedinvalidfieldtype<br />**16 進数**:<br />800404d8<br />**数値**:<br />-2147220264|プラットフォームは、特定のフィールドの種類を処理することはできません。|
> |**名前**:<br />unManagedinvalidlinkobjects<br />**16 進数**:<br />800404ba<br />**数値**:<br />-2147220294|無効なリンク エンティティ、属性へのリンク、または属性からのリンクです。|
> |**名前**:<br />unManagedinvalidoperator<br />**16 進数**:<br />800404c7<br />**数値**:<br />-2147220281|指定された演算子が無効です。|
> |**名前**:<br />unManagedinvalidorganizationid<br />**16 進数**:<br />800404be<br />**数値**:<br />-2147220290|OrganizationId が見つからないか、無効です。|
> |**名前**:<br />unManagedinvalidowningbusinessunit<br />**16 進数**:<br />800404a8<br />**数値**:<br />-2147220312|owningbusinessunit が見つからないか、無効です。|
> |**名前**:<br />unManagedinvalidowningbusinessunitorbusinessunitid<br />**16 進数**:<br />800404bc<br />**数値**:<br />-2147220292|owningbusinessunit または businessunitid が見つからないか、無効です。|
> |**名前**:<br />unManagedinvalidowninguser<br />**16 進数**:<br />800404bd<br />**数値**:<br />-2147220291|owninguser が見つからないか、無効です。|
> |**名前**:<br />unManagedinvalidpagevalue<br />**16 進数**:<br />800404c2<br />**数値**:<br />-2147220286|ページの値が無効か、見つかりません。|
> |**名前**:<br />unManagedinvalidparametertypeforparameterizedquery<br />**16 進数**:<br />800404d6<br />**数値**:<br />-2147220266|パラメーター化したクエリは、指定されたパラメータの種類をサポートしていません。|
> |**名前**:<br />unManagedinvalidprincipal<br />**16 進数**:<br />8004049e<br />**数値**:<br />-2147220322|プリンシパル ID が見つからないか、無効です。|
> |**名前**:<br />unManagedinvalidprivilegeedepth<br />**16 進数**:<br />800404bb<br />**数値**:<br />-2147220293|ユーザーの特権の階層が無効です。|
> |**名前**:<br />unManagedinvalidprivilegeid<br />**16 進数**:<br />800404ce<br />**数値**:<br />-2147220274|特権 ID が無効である、または見つかりません。|
> |**名前**:<br />unManagedinvalidprivilegeusergroup<br />**16 進数**:<br />800404cd<br />**数値**:<br />-2147220275|特権ユーザー グループ ID が無効かまたは見つかりません。|
> |**名前**:<br />unManagedinvalidprocesschildofcondition<br />**16 進数**:<br />800404b4<br />**数値**:<br />-2147220300|ProcessChildOfCondition は条件 non-child-of で呼ばれます。|
> |**名前**:<br />unManagedinvalidprocessliternalcondition<br />**16 進数**:<br />800404b1<br />**数値**:<br />-2147220303|ProcessLiteralCondition はロールアップ クエリで使用した場合のみ有効です。|
> |**名前**:<br />unManagedinvalidsecurityprincipal<br />**16 進数**:<br />800404d2<br />**数値**:<br />-2147220270|セキュリティ プリンシパルが無効または見つかりません。|
> |**名前**:<br />unManagedinvalidstreamfield<br />**16 進数**:<br />800404d7<br />**数値**:<br />-2147220265|プラットフォームはストリーム フィールドを処理することはできません。|
> |**名前**:<br />unManagedinvalidtlsmananger<br />**16 進数**:<br />800404a2<br />**数値**:<br />-2147220318|TLS マネージャーを取得できませんでした。|
> |**名前**:<br />unManagedinvalidtrxcountforcommit<br />**16 進数**:<br />800404e2<br />**数値**:<br />-2147220254|コミットするには、トランザクション数を 1 にする必要があります。|
> |**名前**:<br />unManagedinvalidtrxcountforrollback<br />**16 進数**:<br />800404e1<br />**数値**:<br />-2147220255|ロールバックするには、トランザクション数を 1 にする必要があります。|
> |**名前**:<br />unManagedinvalidvaluettagoutsideconditiontag<br />**16 進数**:<br />800404bf<br />**数値**:<br />-2147220289|無効な値のタグは、condition タグの外部で検出されました。|
> |**名前**:<br />unManagedinvalidversionvalue<br />**16 進数**:<br />800404c0<br />**数値**:<br />-2147220288|バージョン値が無効か、見つかりません。|
> |**名前**:<br />unManagedinvaludidispatchfield<br />**16 進数**:<br />800404db<br />**数値**:<br />-2147220261|プラットフォームは idispatch フィールドを処理することはできません。|
> |**名前**:<br />unManagedmissingaddressentity<br />**16 進数**:<br />800404cb<br />**数値**:<br />-2147220277|住所エンティティが見つかりませんでした。|
> |**名前**:<br />unManagedmissingattributefortag<br />**16 進数**:<br />800404c5<br />**数値**:<br />-2147220283|必要な属性は、特定のタグに対して見つかりませんでした。|
> |**名前**:<br />unManagedmissingdataaccess<br />**16 進数**:<br />800404df<br />**数値**:<br />-2147220257|データ アクセスを ExecutionContext から取得できませんでした。|
> |**名前**:<br />unManagedmissingfilterattribute<br />**16 進数**:<br />800404ad<br />**数値**:<br />-2147220307|フィルターの属性がありません。|
> |**名前**:<br />unManagedmissinglinkentity<br />**16 進数**:<br />800404b2<br />**数値**:<br />-2147220302|リンク エンティティの検索中の予期しないエラーです。|
> |**名前**:<br />unManagedMissingObjectType<br />**16 進数**:<br />80042003<br />**数値**:<br />-2147213309|一つの属性に対してオブジェクトの種類を指定してください。|
> |**名前**:<br />unManagedmissingparentattributeonentity<br />**16 進数**:<br />800404b5<br />**数値**:<br />-2147220299|上位属性は、必要なエンティティで見つかりませんでした。|
> |**名前**:<br />unManagedmissingparententity<br />**16 進数**:<br />800404e5<br />**数値**:<br />-2147220251|親エンティティが見つかりませんでした。|
> |**名前**:<br />unManagedmissingpreviousownertype<br />**16 進数**:<br />800404d0<br />**数値**:<br />-2147220272|以前の所有者の種類を判断できません。|
> |**名前**:<br />unManagedmissingreferencesfromrelationship<br />**16 進数**:<br />800404c9<br />**数値**:<br />-2147220279|エンティティの ReferencesFrom コレクションの関連付けにアクセスできません。|
> |**名前**:<br />unManagedmissingreferencingattribute<br />**16 進数**:<br />800404c8<br />**数値**:<br />-2147220280|関連付けの ReferencingAttribute が見つからないかまたは無効です。|
> |**名前**:<br />unManagedmorethanonesortattribute<br />**16 進数**:<br />800404a6<br />**数値**:<br />-2147220314|複数の並べ替え属性が定義されています。|
> |**名前**:<br />unManagedObjectTypeUnexpected<br />**16 進数**:<br />80042004<br />**数値**:<br />-2147213308|許可されていない一つの属性に対してオブジェクトの種類が指定されています。|
> |**名前**:<br />unManagedparentattributenotfound<br />**16 進数**:<br />800404a4<br />**数値**:<br />-2147220316|上位属性は、下位属性で見つかりませんでした。|
> |**名前**:<br />unManagedpartylistattributenotsupported<br />**16 進数**:<br />800404b8<br />**数値**:<br />-2147220296|種類 partylist の属性はサポートされていません。|
> |**名前**:<br />unManagedpendingtrxexists<br />**16 進数**:<br />800404e3<br />**数値**:<br />-2147220253|保留中のトランザクションがに既に存在します。|
> |**名前**:<br />unManagedproxycreationfailed<br />**16 進数**:<br />8004049f<br />**数値**:<br />-2147220321|マネージド プロキシのインスタンスは作成できません。|
> |**名前**:<br />unManagedtrxinterophandlerset<br />**16 進数**:<br />800404dd<br />**数値**:<br />-2147220259|TrxInteropHandler がすでに設定されています。|
> |**名前**:<br />unManagedunablegetexecutioncontext<br />**16 進数**:<br />800404e4<br />**数値**:<br />-2147220252|実行コンテキスト (TLS) を取得できませんでした。|
> |**名前**:<br />unManagedunablegetsessiontoken<br />**16 進数**:<br />800404d3<br />**数値**:<br />-2147220269|セッション トークンを取得できません。|
> |**名前**:<br />unManagedunablegetsessiontokennotrx<br />**16 進数**:<br />800404d4<br />**数値**:<br />-2147220268|保留中のトランザクションがないため、セッション トークンを取得できません。|
> |**名前**:<br />unManagedunableswitchusercontext<br />**16 進数**:<br />800404e0<br />**数値**:<br />-2147220256|異なるユーザー コンテキストに設定することはできません。|
> |**名前**:<br />unManagedunabletoaccessqueryplan<br />**16 進数**:<br />800404a5<br />**数値**:<br />-2147220315|計画クエリにアクセスできません。|
> |**名前**:<br />unManagedunabletoaccessqueryplanfilter<br />**16 進数**:<br />800404c6<br />**数値**:<br />-2147220282|計画クエリのフィルターにアクセスできません。|
> |**名前**:<br />unManagedunabletolocateconditionfilter<br />**16 進数**:<br />800404c3<br />**数値**:<br />-2147220285|条件のフィルターを検索中の予期しないエラーです。|
> |**名前**:<br />unManagedunabletoretrieveprivileges<br />**16 進数**:<br />800404a0<br />**数値**:<br />-2147220320|特権を取得できませんでした。|
> |**名前**:<br />unManagedunexpectedpropertytype<br />**16 進数**:<br />800404cc<br />**数値**:<br />-2147220276|予期しないプロパティの種類です。|
> |**名前**:<br />unManagedunexpectedrimarykey<br />**16 進数**:<br />800404b3<br />**数値**:<br />-2147220301|主キーが想定される属性通りにありません。|
> |**名前**:<br />unManagedunknownaggregateoperation<br />**16 進数**:<br />800404b6<br />**数値**:<br />-2147220298|不明な集計操作が指定されました。|
> |**名前**:<br />unManagedunusablevariantdata<br />**16 進数**:<br />800404af<br />**数値**:<br />-2147220305|指定されたバリアントに使用不能な形式のデータが含まれています。|
> |**名前**:<br />UnmappedTransformationOutputDataFound<br />**16 進数**:<br />80040381<br />**数値**:<br />-2147220607|1 つまたは複数の出力はターゲット フィールドにマップされていない変換によって返されました。|
> |**名前**:<br />UnpopulatedPrimaryKey<br />**16 進数**:<br />8004023d<br />**数値**:<br />-2147220931|オフライン モードにあるリッチ クライアントのプラットフォームを呼び出すために、主キーを事前設定する必要があります。|
> |**名前**:<br />UnrelatedConnectionRoles<br />**16 進数**:<br />80048216<br />**数値**:<br />-2147188202|つながりロールは、関連付けがありません。|
> |**名前**:<br />UnrestrictedIFrameInUserDashboard<br />**16 進数**:<br />8004E30C<br />**数値**:<br />-2147163380|ユーザー ダッシュボード フォーム XML にはセキュリティ = false がありません。|
> |**名前**:<br />UnspecifiedActivityXmlForCampaignActivityPropagate<br />**16 進数**:<br />80040318<br />**数値**:<br />-2147220712|CampaignActivity 実行/配布に対して Activity XML を指定する必要があります。|
> |**名前**:<br />UnsupportedActionType<br />**16 進数**:<br />80060390<br />**数値**:<br />-2147089520|コントロールのステップがありません。|
> |**名前**:<br />UnsupportedArgumentsMarkedRequired<br />**16 進数**:<br />80060394<br />**数値**:<br />-2147089516|サポートされない引数を必須としてマークしないでください。|
> |**名前**:<br />UnsupportedAttributeForEditor<br />**16 進数**:<br />80060010<br />**数値**:<br />-2147090416|サポートされていない属性がルールに含まれています。|
> |**名前**:<br />UnsupportedAttributeInInProfileItemEntityFilters<br />**16 進数**:<br />80071123<br />**数値**:<br />-2147020509|属性 {0} は、フィルター クエリ オプションではサポートされません。|
> |**名前**:<br />UnsupportedAttributeOrOperatorMobileOfflineFilters<br />**16 進数**:<br />80071115<br />**数値**:<br />-2147020523|属性または演算子 "{0}" は、Mobile Offline 組織フィルター用にサポートされていません。|
> |**名前**:<br />UnsupportedAttributeType<br />**16 進数**:<br />8005E00D<br />**数値**:<br />-2147098611|属性の種類 {0} はサポートされていません。 属性 {1} をクエリから削除し、やり直してください。|
> |**名前**:<br />UnsupportedComponentOperation<br />**16 進数**:<br />8004F010<br />**数値**:<br />-2147160048|{0} はサポートされた操作として認識されていません。|
> |**名前**:<br />UnsupportedCudOperationForDynamicProperties<br />**16 進数**:<br />80061019<br />**数値**:<br />-2147086311|セット製品のプロパティを作成することはできません。|
> |**名前**:<br />UnsupportedDashboardInEditor<br />**16 進数**:<br />8004E30E<br />**数値**:<br />-2147163378|ダッシュボードを開くことができません。|
> |**名前**:<br />UnsupportedEmailServer<br />**16 進数**:<br />8005E242<br />**数値**:<br />-2147098046|電子メール サーバーがサポートされていません。|
> |**名前**:<br />UnsupportedImportComponent<br />**16 進数**:<br />80061302<br />**数値**:<br />-2147085566|申し訳ありません、インポートが失敗しました。{0} コンポーネントはインポートとエクスポートの対象としてサポートされていません。|
> |**名前**:<br />UnsupportedListMemberType<br />**16 進数**:<br />80040301<br />**数値**:<br />-2147220735|サポートされていないリスト メンバーの種類です。|
> |**名前**:<br />UnsupportedOperatorForAttributeInProfileItemEntityFilters<br />**16 進数**:<br />80071121<br />**数値**:<br />-2147020511|演算子 {0} は、フィルター クエリ オプションの属性 {1} ではサポートされません。|
> |**名前**:<br />UnsupportedParameter<br />**16 進数**:<br />80040320<br />**数値**:<br />-2147220704|指定されたパラメーターは、一括操作ではサポートされていません|
> |**名前**:<br />UnsupportedProcessCode<br />**16 進数**:<br />80040385<br />**数値**:<br />-2147220603|プロセス コードは、このエンティティではサポートされていません。|
> |**名前**:<br />UnsupportedSdkMessageForBundles<br />**16 進数**:<br />80061025<br />**数値**:<br />-2147086299|このメッセージは、種類がバンドルである製品ではサポートされません。|
> |**名前**:<br />UnsupportedStepForBusinessRuleEditor<br />**16 進数**:<br />80060009<br />**数値**:<br />-2147090423|エディターでサポートされていないステップがルールに含まれています。|
> |**名前**:<br />UnsupportedZipFileForImport<br />**16 進数**:<br />80048495<br />**数値**:<br />-2147187563|圧縮 (.zip) ファイルまたは .cab ファイルをアップロードできませんでした。ファイルが壊れているか、インポートできる有効なファイルが含まれていません。|
> |**名前**:<br />UnzipProcessCountLimitReached<br />**16 進数**:<br />80048494<br />**数値**:<br />-2147187564|新しいプロセスを解凍し始めることはできません。|
> |**名前**:<br />UnzipTimeout<br />**16 進数**:<br />80048496<br />**数値**:<br />-2147187562|インポート用にアップロードされた zip ファイルを解凍中にタイムアウトが発生しました。|
> |**名前**:<br />UpdateAttributeMap<br />**16 進数**:<br />80046204<br />**数値**:<br />-2147196412|UpdateAttributeMap のエラーが発生しました|
> |**名前**:<br />UpdateEntityMap<br />**16 進数**:<br />80046201<br />**数値**:<br />-2147196415|UpdateEntityMap のエラーが発生しました|
> |**名前**:<br />UpdateNonCustomReportFromTemplate<br />**16 進数**:<br />80040490<br />**数値**:<br />-2147220336|レポートがテンプレートから作成されなかった場合、テンプレートからのレポートを更新できません|
> |**名前**:<br />UpdatePublishedWorkflowDefinition<br />**16 進数**:<br />80045002<br />**数値**:<br />-2147201022|公開されたワークフローの定義を更新できません。|
> |**名前**:<br />UpdatePublishedWorkflowDefinitionWorkflowDependency<br />**16 進数**:<br />80045008<br />**数値**:<br />-2147201016|公開されたワークフロー定義に対する、ワークフローの依存関係を更新することはできません。|
> |**名前**:<br />UpdatePublishedWorkflowTemplate<br />**16 進数**:<br />8004501B<br />**数値**:<br />-2147200997|公開されたワークフロー テンプレートを更新できません。|
> |**名前**:<br />UpdateRecurrenceRuleFailed<br />**16 進数**:<br />8004E114<br />**数値**:<br />-2147163884|定期的なアイテムのルールを更新できませんでした。 対応する定期的なアイテムのルールが見つかりません。|
> |**名前**:<br />UpdateRIOrganizationDataAccessNotAllowed<br />**16 進数**:<br />80044273<br />**数値**:<br />-2147204493|この機能の構成は、システム管理者だけが更新できます。|
> |**名前**:<br />UpdateWorkflowActivation<br />**16 進数**:<br />80045003<br />**数値**:<br />-2147201021|ワークフローのアクティブ化は更新できません。|
> |**名前**:<br />UpdateWorkflowActivationWorkflowDependency<br />**16 進数**:<br />80045007<br />**数値**:<br />-2147201017|ワークフロー アクティベーションに関連付けられている、ワークフローの依存関係を更新することはできません。|
> |**名前**:<br />UserAlreadyExists<br />**16 進数**:<br />80041d2c<br />**数値**:<br />-2147214036|指定された Active Directoryユーザーが、Dynamics 365 ユーザーとして既に存在します。|
> |**名前**:<br />UserCancelledMailMerge<br />**16 進数**:<br />8004032f<br />**数値**:<br />-2147220689|差し込み印刷操作はユーザーによって取り消されました。|
> |**名前**:<br />UserCannotEnableWithoutLicense<br />**16 進数**:<br />8004D24C<br />**数値**:<br />-2147167668|ライセンスを付与されていないユーザーを有効にすることはできません|
> |**名前**:<br />UserDataNotFound<br />**16 進数**:<br />8004D211<br />**数値**:<br />-2147167727|ユーザー データが見つかりませんでした。|
> |**名前**:<br />UserDoesNotHaveAccessToTheTenant<br />**16 進数**:<br />80044507<br />**数値**:<br />-2147203833|ユーザーにはテナントへのアクセス権がありません。|
> |**名前**:<br />UserDoesNotHaveAdminOnlyModePermissions<br />**16 進数**:<br />8004A113<br />**数値**:<br />-2147180269|管理者専用モードのとき、ユーザーには組織にアクセスするのに必要な特権 (またはロール メンバーシップ) がありません。|
> |**名前**:<br />UserDoesNotHavePrivilegesToRunTheTool<br />**16 進数**:<br />800608F8<br />**数値**:<br />-2147088136|この要求を実行するには、システム管理者であることが必要です。|
> |**名前**:<br />UserDoesNotHaveSendAsAllowed<br />**16 進数**:<br />8004480d<br />**数値**:<br />-2147203059|ユーザーには "として送信" 特権がありません|
> |**名前**:<br />UserDoesNotHaveSendAsForQueue<br />**16 進数**:<br />8004480f<br />**数値**:<br />-2147203057|指定されたキューとして電子メールを送信するための十分な特権がありません。 迅速なサポートが必要な場合、システム管理者に支援を依頼してください。|
> |**名前**:<br />UserIdOrQueueNotSet<br />**16 進数**:<br />800404e8<br />**数値**:<br />-2147220248|プライマリ ユーザー ID、または宛先キューの種類コードが設定されていません。|
> |**名前**:<br />UserInviteDisabled<br />**16 進数**:<br />8004D216<br />**数値**:<br />-2147167722|ユーザー招待が無効にされているため招待状は送信できません。|
> |**名前**:<br />UserInWrongBusiness<br />**16 進数**:<br />80041409<br />**数値**:<br />-2147216375|id = {0} のユーザーは、roleId = {2} および rolebusinessUnit = {3} のロールとは異なる部署 = {1} に属しています。|
> |**名前**:<br />UserIsNotSystemAdminInOrganization<br />**16 進数**:<br />8004B069<br />**数値**:<br />-2147176343|現在のユーザーは、顧客の組織でのシステム管理者ではありません|
> |**名前**:<br />UserLoopBeingCreated<br />**16 進数**:<br />80041d25<br />**数値**:<br />-2147214043|選択したユーザーをこのユーザーの上司に設定できません。選択したユーザーは既に上司に設定されているか、ユーザーの直接の管理階層に存在します。  管理者になるよう他のユーザーを選択するか、またはレコードを更新しないでください。|
> |**名前**:<br />UserLoopExists<br />**16 進数**:<br />80041d24<br />**数値**:<br />-2147214044|このユーザーの上司を設定できません。管理階層の既存の関係により、循環リレーションシップが発生しています。  これは通常、Microsoft Dynamics 365 データベースの手動編集によって起こります。 これを修正するには、データベースの階層を変更し、循環リレーションシップを解消する必要があります。|
> |**名前**:<br />UserNameRequiredForImpersonation<br />**16 進数**:<br />8005E24D<br />**数値**:<br />-2147098035|ユーザー名を入力して保存し直してください|
> |**名前**:<br />UserNeverLoggedIntoYammer<br />**16 進数**:<br />8005F111<br />**数値**:<br />-2147094255|他のユーザーをフォローするには、Yammer にログインする必要があります。 Yammer アカウントにログインし、やり直してください。|
> |**名前**:<br />UserNotAssignedLicense<br />**16 進数**:<br />8004D24B<br />**数値**:<br />-2147167669|ユーザーにライセンスが割り当てられていません|
> |**名前**:<br />UserNotAssignedRoles<br />**16 進数**:<br />80042f09<br />**数値**:<br />-2147209463|ユーザーにロールが割り当てられていません。|
> |**名前**:<br />UserNotInParentHierarchy<br />**16 進数**:<br />80041d07<br />**数値**:<br />-2147214073|ユーザーは、上位ユーザーの事業階層にはありません。|
> |**名前**:<br />UserNotMemberOfOrg<br />**16 進数**:<br />80072560<br />**数値**:<br />-2147015328|ユーザーが組織のメンバーではありません。|
> |**名前**:<br />UserSettingsInvalidAdvancedFindStartupMode<br />**16 進数**:<br />80041d34<br />**数値**:<br />-2147214028|無効な高度検索スタートアップ モードです。|
> |**名前**:<br />UserSettingsInvalidSearchExperienceValue<br />**16 進数**:<br />80041d53<br />**数値**:<br />-2147213997|無効な検索エクスペリエンス値です。|
> |**名前**:<br />UserSettingsOverMaxPagingLimit<br />**16 進数**:<br />80044305<br />**数値**:<br />-2147204347|ページ制限が構成値の最大値を超えています。|
> |**名前**:<br />UserTimeConvertException<br />**16 進数**:<br />80040241<br />**数値**:<br />-2147220927|ユーザーのタイム ゾーン情報を変換できませんでした。|
> |**名前**:<br />UserTimeZoneException<br />**16 進数**:<br />80040240<br />**数値**:<br />-2147220928|ユーザーのタイム ゾーン情報を取得できませんでした。|
> |**名前**:<br />UserViewsOrVisualizationsFound<br />**16 進数**:<br />8004E302<br />**数値**:<br />-2147163390|システム ダッシュボードには、ユーザー ビューとビジュアル化のどちらも含めることができません。|
> |**名前**:<br />ValidateNotSupported<br />**16 進数**:<br />8004E10A<br />**数値**:<br />-2147163894|定期的な予定マスターの検証メソッドはサポートされていません。|
> |**名前**:<br />ValidationContextIsNull<br />**16 進数**:<br />80060442<br />**数値**:<br />-2147089342|ビジネス プロセスの作成または更新時のエラー: 検証コンテキストは Null にできません。|
> |**名前**:<br />ValidationFailedForDynamicProperty<br />**16 進数**:<br />80061021<br />**数値**:<br />-2147086303|{0} プロパティの保存中にエラーが発生しました。|
> |**名前**:<br />ValidDateTimeBehaviorExportAsWarning<br />**16 進数**:<br />800608A5<br />**数値**:<br />-2147088219|[日付のみ] と [タイム ゾーン非依存] の動作は以前のバージョンの Dynamics 365 では機能しないため、{0} フィールドはユーザー ローカルの日付と時間になります。|
> |**名前**:<br />ValidDateTimeBehaviorWarning<br />**16 進数**:<br />800608A4<br />**数値**:<br />-2147088220|このフィールドの動作が変更されました。 このフィールドのすべての依存関係 (業務ルール、ワークフロー、計算フィールド、ロールアップ フィールドなど) を調べて、問題が発生しないことを確認する必要があります。 属性: {0}|
> |**名前**:<br />ValidOnlyForDynamicsOnline<br />**16 進数**:<br />80072302<br />**数値**:<br />-2147015934|この API は Dynamics 365 オンラインに対してのみ有効です。|
> |**名前**:<br />ValueMissingInOptionOrderArray<br />**16 進数**:<br />80044325<br />**数値**:<br />-2147204315|オプションの配列に値がありません。|
> |**名前**:<br />ValueParsingError<br />**16 進数**:<br />8004B037<br />**数値**:<br />-2147176393|値 {2} を持つ種類 {1} のパラメーター {0} の解析エラー|
> |**名前**:<br />VersionedRowNotFoundInTempDB<br />**16 進数**:<br />80048542<br />**数値**:<br />-2147187390|必要なバージョンの行が TempDB に見つかりません; TempDB の空き容量が不足している可能性があります; しばらくしてから再試行してください。|
> |**名前**:<br />VersionMismatch<br />**16 進数**:<br />8004B020<br />**数値**:<br />-2147176416|サポートされていないバージョン - これは {0} バージョン {1} ですが、バージョン {2} が要求されています。|
> |**名前**:<br />VeryLargeFileInZipImport<br />**16 進数**:<br />80048491<br />**数値**:<br />-2147187567|インポートしようとしている圧縮 (.zip) ファイルまたは .cab ファイル内の 1 つのファイルがサイズ制限を超えています。|
> |**名前**:<br />ViewConditionTypeNotSupportedOffline<br />**16 進数**:<br />80071130<br />**数値**:<br />-2147020496|条件 {0} がサポートされていません。|
> |**名前**:<br />ViewForDuplicateDetectionNotDefined<br />**16 進数**:<br />80048838<br />**数値**:<br />-2147186632|エンティティの重複する表示の必須ビューが定義されていません。|
> |**名前**:<br />ViewNotAvailableForMobileOffline<br />**16 進数**:<br />8005F21b<br />**数値**:<br />-2147093989|現在、ビューはオフラインでは使用できません。 ビューの切り替えをするか、管理者にお問い合わせください|
> |**名前**:<br />ViewNotAvailableOnMobile<br />**16 進数**:<br />80071126<br />**数値**:<br />-2147020506|このビューはモバイルで使用できません。|
> |**名前**:<br />ViewNotSupportedInCalendarModeOffline<br />**16 進数**:<br />80071128<br />**数値**:<br />-2147020504|このビューは、グリッド モード オフラインでのみサポートされています。 オフラインのカレンダー モードはサポートされていません。|
> |**名前**:<br />VirtualEntitiesNotSupported<br />**16 進数**:<br />80073020<br />**数値**:<br />-2147012576|仮想エンティティはサポートされていません。|
> |**名前**:<br />VirtualEntityFailure<br />**16 進数**:<br />80050263<br />**数値**:<br />-2147155357|仮想エンティティ操作に失敗しました。|
> |**名前**:<br />VirtualEntityFCBOFF<br />**16 進数**:<br />80081113<br />**数値**:<br />-2146954989|仮想エンティティの機能ビットが有効になっていません。|
> |**名前**:<br />VirtualEntityNotSupportedInMobileOffline<br />**16 進数**:<br />80044821<br />**数値**:<br />-2147203039|エンティティ {0} は、Mobile offline では使用できない仮想エンティティです。|
> |**名前**:<br />VisualizationModuleNotFound<br />**16 進数**:<br />8004E012<br />**数値**:<br />-2147164142|指定された名前のビジュアル化モジュールはありません。|
> |**名前**:<br />VisualizationOtcNotFoundError<br />**16 進数**:<br />8004E015<br />**数値**:<br />-2147164139|ビジュアル化のオブジェクトの種類コードが指定されていません。|
> |**名前**:<br />VisualizationRenderingError<br />**16 進数**:<br />8004E00E<br />**数値**:<br />-2147164146|グラフのレンダリング中にエラーが発生しました|
> |**名前**:<br />WebhooksHttpRequestTimedOut<br />**16 進数**:<br />80050202<br />**数値**:<br />-2147155454|HTTP 要求がクライアント側でタイムアウトしたため、Webhook 呼び出しに失敗しました。 webhook 要求ハンドラを確認してください。|
> |**名前**:<br />WebhooksInvalidHttpHeaders<br />**16 進数**:<br />80050203<br />**数値**:<br />-2147155453|authValue に無効な http ヘッダーがあるため、Webhook 呼び出しに失敗しました。 authValue 形式、ヘッダー名、値が、サービス エンドポイント エンティティに対して有効か確認してください。|
> |**名前**:<br />WebhooksInvalidHttpQueryParams<br />**16 進数**:<br />80050204<br />**数値**:<br />-2147155452|authValue に無効な http クエリ パラメーターがあるため、Webhook 呼び出しに失敗しました。 authValue 形式、クエリ パラメーター名、値が、サービス エンドポイント エンティティに対して有効か確認してください。|
> |**名前**:<br />WebhooksMaxSizeExceeded<br />**16 進数**:<br />80050207<br />**数値**:<br />-2147155449|http 要求ペイロードが最大許容サイズを超えたため、Webhook 呼び出しに失敗しました。 要求のサイズを小さくしてから再試行してください。|
> |**名前**:<br />WebhooksNonSuccessHttpResponse<br />**16 進数**:<br />80050201<br />**数値**:<br />-2147155455|http 要求が成功ではない httpStatus コードを受信したため、Webhook 呼び出しに失敗しました。 webhook 要求ハンドラを確認してください。|
> |**名前**:<br />WebhooksPostDisabled<br />**16 進数**:<br />80050206<br />**数値**:<br />-2147155450|Webhook の投稿は組織に対して無効です。|
> |**名前**:<br />WebhooksPostRequestFailed<br />**16 進数**:<br />80050205<br />**数値**:<br />-2147155451|Webhook 呼び出しが http ポスト中に失敗しました。 詳細については例外を確認してください。|
> |**名前**:<br />WebResourceContentSizeExceeded<br />**16 進数**:<br />8004F114<br />**数値**:<br />-2147159788|Web リソースのコンテンツ サイズが大きすぎます。|
> |**名前**:<br />WebResourceDuplicateName<br />**16 進数**:<br />8004F115<br />**数値**:<br />-2147159787|同じ名前の Web リソースが既に存在します。 別の名前を使用してください。|
> |**名前**:<br />WebResourceEmptyName<br />**16 進数**:<br />8004F116<br />**数値**:<br />-2147159786|Web リソース名は NULL または空にすることはできません。|
> |**名前**:<br />WebResourceEmptySilverlightVersion<br />**16 進数**:<br />8004F112<br />**数値**:<br />-2147159790|Silverlight Web リソースに対して Silverlight のバージョンを空にすることはできません。|
> |**名前**:<br />WebResourceImportError<br />**16 進数**:<br />8004F11B<br />**数値**:<br />-2147159781|Web リソースのインポート中にエラーが発生しました。 このソリューションをインポートし直してください。 詳細については、Microsoft Dynamics 365 テクニカル サポートにお問い合わせください。|
> |**名前**:<br />WebResourceImportMissingFile<br />**16 進数**:<br />8004F11A<br />**数値**:<br />-2147159782|この Web リソース用のファイルはソリューション ファイルに存在しません。|
> |**名前**:<br />WebResourceInvalidSilverlightVersion<br />**16 進数**:<br />8004F113<br />**数値**:<br />-2147159789|Silverlight のバージョンは、xx.xx[.xx.xx] の形式で指定してください。|
> |**名前**:<br />WebResourceInvalidType<br />**16 進数**:<br />8004F111<br />**数値**:<br />-2147159791|無効な Web リソースの種類が指定されました。|
> |**名前**:<br />WebResourceNameInvalidCharacters<br />**16 進数**:<br />8004F117<br />**数値**:<br />-2147159785|Web リソース名には、文字、数字、ピリオド、および連続していないスラッシュのみを含めることができます。|
> |**名前**:<br />WebResourceNameInvalidFileExtension<br />**16 進数**:<br />8004F119<br />**数値**:<br />-2147159783|Web リソースには次の拡張子は使用できません: .aspx、.ascx、.asmx、または .ashx。|
> |**名前**:<br />WebResourceNameInvalidPrefix<br />**16 進数**:<br />8004F118<br />**数値**:<br />-2147159784|Web リソース名に有効な接頭辞が含まれていません。|
> |**名前**:<br />WopiApplicationUrl<br />**16 進数**:<br />80060802<br />**数値**:<br />-2147088382|WOPI アプリケーション URL から情報を取得中にエラーが発生しました。|
> |**名前**:<br />WopiDiscoveryFailed<br />**16 進数**:<br />80060800<br />**数値**:<br />-2147088384|WOPI 検索 XML を取得する要求が失敗しました。|
> |**名前**:<br />WopiMaxFileSizeExceeded<br />**16 進数**:<br />80060803<br />**数値**:<br />-2147088381|{0} ファイルは {1} のサイズの上限を超えています。|
> |**名前**:<br />WordTemplateFeatureNotEnabled<br />**16 進数**:<br />800608DB<br />**数値**:<br />-2147088165|Word ドキュメント テンプレート機能が有効になっていません。|
> |**名前**:<br />WorkflowActivityNotSupported<br />**16 進数**:<br />80045045<br />**数値**:<br />-2147200955|サポートされていないワークフロー ステップを参照しているため、このワークフローを作成、更新、または公開できません。|
> |**名前**:<br />WorkflowAutomaticallyDeactivated<br />**16 進数**:<br />80045042<br />**数値**:<br />-2147200958|元のワークフロー定義は非アクティブ化され、置き換えられました。|
> |**名前**:<br />WorkflowCompileFailure<br />**16 進数**:<br />80045001<br />**数値**:<br />-2147201023|ワークフローのコンパイル中にエラーが発生しました。|
> |**名前**:<br />WorkflowConditionIncorrectBinaryOperatorFormation<br />**16 進数**:<br />80045011<br />**数値**:<br />-2147201007|バイナリ演算子の構成が正しくありません。|
> |**名前**:<br />WorkflowConditionIncorrectUnaryOperatorFormation<br />**16 進数**:<br />80045010<br />**数値**:<br />-2147201008|単項演算子の構成が正しくありません。|
> |**名前**:<br />WorkflowConditionOperatorNotSupported<br />**16 進数**:<br />80045012<br />**数値**:<br />-2147201006|指定した種類でサポートされていない条件演算子。|
> |**名前**:<br />WorkflowConditionTypeNotSupport<br />**16 進数**:<br />80045013<br />**数値**:<br />-2147201005|条件に指定された種類が無効です。|
> |**名前**:<br />WorkflowDoesNotExist<br />**16 進数**:<br />8006040b<br />**数値**:<br />-2147089397|ワークフローが存在しません。|
> |**名前**:<br />WorkflowExpressionOperatorNotSupported<br />**16 進数**:<br />8004502E<br />**数値**:<br />-2147200978|指定した種類でサポートされていない表現演算子。|
> |**名前**:<br />WorkflowIdIsNull<br />**16 進数**:<br />80060400<br />**数値**:<br />-2147089408|業務プロセス フロー カテゴリを作成中に、ワークフロー ID を NULL にすることはできません|
> |**名前**:<br />WorkflowIsNotActive<br />**16 進数**:<br />80045055<br />**数値**:<br />-2147200939|アクション ステップでワークフローを使用するには、ワークフローがアクティブである必要があります。|
> |**名前**:<br />WorkflowIsNotOnDemand<br />**16 進数**:<br />80045059<br />**数値**:<br />-2147200935|ワークフローはオンデマンドとしてマークされている必要があります。|
> |**名前**:<br />WorkflowPublishedByNonOwner<br />**16 進数**:<br />8004500B<br />**数値**:<br />-2147201013|このワークフローを公開または非公開にできるのは所有者だけです。|
> |**名前**:<br />WorkflowPublishNoActivationParameters<br />**16 進数**:<br />80045018<br />**数値**:<br />-2147201000|自動ワークフローは、アクティブ化パラメーターが指定されていない場合は公開できません。|
> |**名前**:<br />WorkflowReferencesInvalidActivity<br />**16 進数**:<br />80045038<br />**数値**:<br />-2147200968|ワークフロー定義には、無効なカスタム活動を参照するステップが含まれています。 無効な参照を削除し、やり直してください。|
> |**名前**:<br />WorkflowSystemPaused<br />**16 進数**:<br />80045017<br />**数値**:<br />-2147201001|ワークフローはシステムにより停止される必要があります。|
> |**名前**:<br />WorkflowValidationFailure<br />**16 進数**:<br />80045014<br />**数値**:<br />-2147201004|指定されたワークフローで検証に失敗しました。|
> |**名前**:<br />WrongNumberOfBooleanOptions<br />**16 進数**:<br />8004431B<br />**数値**:<br />-2147204325|ブール値の属性には、2 つのオプションの値が必要です。|
> |**名前**:<br />XamlNotFound<br />**16 進数**:<br />80154B4F<br />**数値**:<br />-2146088113|この機能は、オフライン モードでは使用できません。|
> |**名前**:<br />XlsxExportGeneratingExcelFailed<br />**16 進数**:<br />800608C7<br />**数値**:<br />-2147088185|Excel を生成できませんでした。|
> |**名前**:<br />XlsxImportColumnHeadersInvalid<br />**16 進数**:<br />800608C6<br />**数値**:<br />-2147088186|無効な列です。|
> |**名前**:<br />XlsxImportExcelFailed<br />**16 進数**:<br />800608C8<br />**数値**:<br />-2147088184|データのインポートに失敗しました。|
> |**名前**:<br />XlsxImportHiddenColumnAbsent<br />**16 進数**:<br />800608C4<br />**数値**:<br />-2147088188|必要な列がありません。|
> |**名前**:<br />XlsxImportInvalidColumnCount<br />**16 進数**:<br />800608C5<br />**数値**:<br />-2147088187|列の不一致。|
> |**名前**:<br />XlsxImportInvalidExcelDocument<br />**16 進数**:<br />800608C2<br />**数値**:<br />-2147088190|無効なインポート用ファイル。|
> |**名前**:<br />XlsxImportInvalidFileData<br />**16 進数**:<br />800608C3<br />**数値**:<br />-2147088189|インポート ファイルに無効な形式があります。|
> |**名前**:<br />YammerAuthTimedOut<br />**16 進数**:<br />8005F107<br />**数値**:<br />-2147094265|Yammer の認証の実行に時間がかかりすぎています。 やり直してください。|
> |**名前**:<br />YValuesPerPointMeasureMismatch<br />**16 進数**:<br />8004E004<br />**数値**:<br />-2147164156|系列の YValuesPerPoint の数は、カテゴリのメジャー コレクションのメジャーの数に等しくしてください。|
> |**名前**:<br />ZeroEmailReceived<br />**16 進数**:<br />8005E231<br />**数値**:<br />-2147098063|メールボックスに使用できる電子メールがないか、または取得できませんでした。|
> |**名前**:<br />ZipFileHasMixOfCsvAndXmlFiles<br />**16 進数**:<br />80048485<br />**数値**:<br />-2147187579|アップロードしようとしている圧縮 (.zip) ファイルに、複数の種類のファイルが含まれています。 ファイルには Excel (.xlsx) ファイル、コンマ区切り (.csv) ファイル、または XML スプレッドシート 2003 (.xml) ファイルのいずれかを含めることができますが、ファイルの種類を組み合わせて含めることはできません。|
> |**名前**:<br />ZipInsideZip<br />**16 進数**:<br />80048489<br />**数値**:<br />-2147187575|アップロードしようとしている圧縮 (.zip) ファイルに、別の .zip ファイルが含まれています。|

### <a name="see-also"></a>関連項目

[コードで例外を処理する](handle-exceptions-code.md)