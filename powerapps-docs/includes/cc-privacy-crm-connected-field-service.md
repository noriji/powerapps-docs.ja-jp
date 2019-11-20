[!INCLUDE[pn_connected_field_service_msdyn365](pn-connected-field-service-msdyn365.md)] をインストールすることにより、[!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] サブスクリプション情報を入力すると必要な [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] リソース (以下を参照) が展開され、[!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)] インスタンスから [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] にデータ (コマンドや登録情報など) が送信されて、IoT に対応したシナリオが有効になります。このシナリオでは、デバイスを登録し、登録したデバイスに対してコマンドの送受信を行うことができます。 管理者は Connected Field Service をアンインストールしてその機能を削除した後、[!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] ポータルに移動して、不要になった関連 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] サービスを管理できます。  
  
 Connected Field Service 機能に関連する [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] のコンポーネントとサービスについては、以下のセクションで説明します。  
  
 [!INCLUDE[cc_privacy_note_azure_trust_center](cc-privacy-note-azure-trust-center.md)]  
  
 [Service Bus キュー](https://azure.microsoft.com/documentation/articles/service-bus-dotnet-get-started-with-queues/)  
  
 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] と [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] の間でやり取りされる、受信と送信の両方のメッセージ (コマンド) にキューを提供します。 IoT 通知が [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] に送信されるか、[!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] から IoT Hub にコマンドが送信されると、その通知やコマンドはここでキューに入れられます。  
  
 [Logic Apps](https://azure.microsoft.com/services/logic-apps/)  
  
 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] コネクタとキュー コネクタを使用するオーケストレーション サービスを提供します。 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] コネクタは [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 固有のエンティティを作成するために使用され、キュー コネクタはキューをポーリングするために使用されます。  
  
 [Stream Analytics](https://azure.microsoft.com/services/stream-analytics/)  
  
 データから深い洞察を得るために役立つ、完全に管理されたリアルタイム イベント処理エンジンを提供します。 Stream Analytics を使うと、デバイス、センサー、Web サイト、ソーシャル メディア、アプリケーション、インフラストラクチャ システムなどからのデータ ストリーミングに対して、リアルタイムの分析処理を簡単にセットアップできます。 一部の IoT 通知を [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] に送信するためのフィルターとして機能します。  
  
 [IoT Hub](https://azure.microsoft.com/services/iot-hub/)  
  
 Connected Field Services は IoT Hub を使用して、登録されたデバイスや資産の状態を管理します。 さらに、IoT Hub は接続されたデバイスにコマンドや通知を送信し、受領確認によってメッセージの配信を追跡します。 断続的に接続されるデバイスに対応するため、送信されるデバイス メッセージには永続性があります。  
  
 **シミュレーター**  
  
 IoT Hub にコマンドを送信または IoT Hub からコマンドを受信するデバイスをエミュレートするためのテスト Web アプリです。  
  
 [Azure SQL Database](https://azure.microsoft.com/services/sql-database/)  
  
 Connected Field Service は SQL [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] を使用して、後で PowerBI が [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] にデバイスの状態を表示するために使用するデバイスのハートビート メッセージを保存します。  
  
 [Azure Blob Storage](https://azure.microsoft.com/services/storage/)  
  
 Stream Analytics で使用されるクエリは、[!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob Storage に保存されます。