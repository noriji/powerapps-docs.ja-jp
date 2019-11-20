テキスト分析機能を有効にすると、[!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Cognitive Services Text Analytics API を活用する [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 内の依存機能が有効になり、高度なインサイトを提供します。 依存機能は次のとおりです。  
  
-   サポート情報のサジェスチョン  
  
-   サポート案件のトピック分析  
  
-   類似サポート案件のサジェスチョン  
  
 管理者は、[!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)] 組織の**設定** > **管理** > **システムの設定** > **プレビュー**タブでテキスト分析機能を有効にできます。  
  
 テキスト分析機能を有効にすることで、[!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)] 内からテキスト分析ベースのサポート情報のサジェスチョンを設定するときに、サポート案件と関連するエンティティのデータが [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Text Analytics API に送信され、キーワードやフレーズが抽出されます。 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Text Analytics API ではデータは保存されません。 サポート情報記事構成で構成されているフィールドのみが [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Text Analytics API に送信されて用語が抽出されます。 管理者またはカスタマイザーには、サポート情報記事構成を非アクティブ化するオプションがないため、[!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Text Analytics API の API の呼び出しを停止できません。 また、カスタマイザーはサポート案件エンティティ フォーム構成でフィールドベースのサジェスチョンに戻すことで、テキスト分析ベースのサジェスチョンの使用を停止できます。  
  
 テキスト分析機能を有効にすることで、[!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)] 内からサポート案件のトピック分析を設定するときに、サポート案件と関連するエンティティのデータが [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Text Analytics API に送信され、トピックが判定されます。 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Text Analytics API ではデータは保存されません。 トピック モデル構成で構成されているフィールドのみが [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Text Analytics API に送信されてトピックが抽出されます。 管理者またはカスタマイザーには、トピック モデルを非アクティブ化するオプションがないため、[!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Text Analytics API の呼び出しを停止できません。  
  
 テキスト分析機能を有効にすることで、[!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)] 内から類似サポート案件のサジェスチョンを設定するときに、類似ルールで [詳細なテキスト分析] オプションを有効にすると、サポート案件と関連するエンティティのデータが [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Text Analytics API に送信され、キーワードとフレーズが抽出されます。 類似ルールで構成されているテキスト フィールドのみが [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Text Analytics API に送信されます。 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Text Analytics API ではデータは保存されません。 管理者またはカスタマイザーには、類似ルールを非アクティブ化するオプションがないため、[!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Text Analytics API の呼び出しを停止できません。  
  
 テキスト分析ベースの機能に関連する [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] のコンポーネントとサービスについては、以下のセクションで説明します。  
  
 [!INCLUDE[cc_privacy_note_azure_trust_center](cc-privacy-note-azure-trust-center.md)]  
  
 [Azure API App](https://azure.microsoft.com/services/app-service/api/)  
  
 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] API App によってトリガーされる Web ジョブは、[!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 組織からデータを読み取り、データを Text Analysis API に送信してトピックを分析します。 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] API App は Web ジョブを使用してバックグラウンドで実際のデータ処理を実行し、データ出力を [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob Storage に書き込みます。 データは [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob Storage に一時的に保存されます。 最終的にトピックが判定されると、データは [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Storage から削除されます。  
  
 [Azure Scheduler](https://azure.microsoft.com/services/storage/)  
  
 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Scheduler は、スケジュールに基づいて Web ジョブをトリガーし、トピックの分析を実行します。 Scheduler とはトピック モデルの構築スケジュールのみが共有されます。  
  
 [Azure Table](https://azure.microsoft.com/services/storage/)  
  
 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Table は、[!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] API App と Web ジョブの間で、モデル バージョンと組織のコンテキストの通信に使用されます。  
  
 [Azure Blob Storage](https://azure.microsoft.com/services/storage/)  
  
 Web ジョブはデータを [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob Storage に一時的に保存し、Logic App パイプラインの実行が完了した時点で削除します。  
  
 [Azure Text Analytics API](https://www.microsoft.com/cognitive-services/text-analytics-api)  
  
 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Text Analytics API には、サポート情報検索のアクティブなフィールドで構成されているフィールドのほか、トピック モデル構成または類似ルール構成に基づいてデータが送信されます。 たとえば、タイトルや説明などのサポート案件エンティティのフィールドや、関連するメモやアクティビティの説明フィールドは、サポート情報検索フィールド構成で構成されます。  
  
 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 関連性検索  
  
 管理者によって有効になっている場合は、関連性検索を使用してサポート案件の類似レコードを検索できます。 類似ルールで使用されるテキスト一致フィールドや完全一致フィールドは、Relevance Search API の呼び出しに使用されます。 データ処理の詳細については、[!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 関連性検索の技術情報を参照してください。