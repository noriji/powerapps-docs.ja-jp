関連性検索機能を有効にすると、[!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)] インスタンスの参加するエンティティおよび属性のデータの同期が開始し、[!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Search インデックスに保存されます。  
  
 関連性検索は既定では有効になっていません。 システム管理者は [!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)] インスタンス内の機能を有効にする必要があります。 関連性検索機能を有効にすると、システム管理者とシステム カスタマイザーは [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 検索インデックスに同期されるデータを完全に制御できます。  
  
 システム カスタマイザーは**カスタマイズ ツール**の**関連性検索の構成**ダイアログ ボックスを使用して検索を有効にするエンティティを指定し、有効にしたエンティティの [ビューの簡易検索] を構成して検索可能にする属性を選択することができます。 データの変更は、[!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)] と [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] の検索の間で、セキュリティで保護された接続により継続的に同期されます。  構成データは暗号化され、必要なシークレットは [!INCLUDE[pn_azure_key_vault](pn-azure-key-vault.md)] に保存されます。  
  
 関連性検索機能に関連する Azure コンポーネントとサービスについては、以下のセクションで説明します。  
  
 [!INCLUDE[cc_privacy_note_azure_trust_center](cc_privacy_note_azure_trust_center.md)]  
  
 [Azure Search サービス](https://azure.microsoft.com/services/search/)  
  
 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Search インデックスを使用すると、高品質の検索結果をすばやく得ることができます。  [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Search は [!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)] にパワフルで高度な次世代の検索機能を付加します。  この機能は [!INCLUDE[pn_Windows_Azure](pn-windows-azure.md)] で提供されている、[!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)] とは独立した専用検索サービスです。 まったく新しい [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]​ 検索インデックスは、暗号化されて保存されます。  2018 年 1 月 24 日より前にオプトアウトした場合は、関連性検索をオプトアウトし、1 時間待ってから、もう一度関連性検索を選択することによって、データのインデックスを再作成する必要があります。  
  
 [Azure SQL Database](https://azure.microsoft.com/services/sql-database/)  
  
 関連性検索は [!INCLUDE[pn_Azure_SQL_Database_long](pn-azure-sql-database-long.md)] を使用して以下の情報を保存します。  
  
-   組織に関連する構成データと対応するインデックス  
  
-   検索サービスに関連するメタデータとインデックス  
  
-   変更を同期する場合のシステム メタデータとデータへのポインター  
  
-   強化された行レベルのセキュリティを有効にする認証データ  
  
[Azure Event Hubs](https://azure.microsoft.com/services/event-hubs/)  
  
[!INCLUDE[pn_azure_event_hubs](pn-azure-event-hubs.md)] は、[!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)] と [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] の間でメッセージを交換し、同期プロセスで管理される作業アイテムを管理するために使用されます。 各メッセージに、組織 ID やエンティティ名など、データの同期に使用される情報が保存されます。  
  
[Azure Service Fabric Cluster](https://azure.microsoft.com/services/service-fabric/)  
  
データの処理とインデックス作成は、Service Fabric ランタイムを通じて管理される仮想マシンに展開されたマイクロサービスによって処理されます。 検索 API とデータ同期プロセスも Service Fabric Cluster にホストされます。  
  
Service Fabric は、ミッション クリティカルなクラウド サービスを提供してきた Microsoft の長年の経験に基づいて誕生し、既に 5 年以上の実績があります。 Service Fabric は、[!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] のコア インフラストラクチャを実行するための基盤テクノロジであり、[!INCLUDE[pn_skype_for_business](pn-skype-for-business.md)]、[!INCLUDE[pn_intune](pn-intune.md)]、[!INCLUDE[pn_azure_event_hubs](pn-azure-event-hubs.md)]、[!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Data Factory、[!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] DocumentDB、[!INCLUDE[pn_Azure_SQL_Database_long](pn-azure-sql-database-long.md)]、[!INCLUDE[pn_cortana](pn-cortana.md)] などのサービスに使用されていて、1 秒あたり 5 億件以上の評価を処理するように拡張できます。  
  
[Azure Virtual Machine Scale Sets](https://azure.microsoft.com/services/virtual-machine-scale-sets/)  
  
[!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Virtual Machine Scale Sets はエラスティックでハイパー スケールアウト ワークロードをサポートするように設計されています。 [!INCLUDE[pn_azure_service_fabric](pn_azure_service_fabric.md)] クラスターは仮想マシンのスケール セットで実行されます。 データを処理し、インデックスを作成するマイクロサービスはスケール セットにホストされ、Service Fabric ランタイムで管理されます。  
  
[Azure Key Vault](https://azure.microsoft.com/services/key-vault/)  
  
[!INCLUDE[pn_azure_key_vault](pn-azure-key-vault.md)]は、検索プロセスで使用される証明書、キーおよびその他のシークレットを安全に管理するために使用されます。  
  
[Azure Storage (Blob Storage)](https://azure.microsoft.com/services/storage/blobs/?b=16.38)  
  
顧客データの変更を最大 2 日間 [!INCLUDE[pn_azure_blob_storage](pn_azure_blob_storage.md)] に保存します。  これらの BLOB は、対称および非対称暗号化のサポート、[!INCLUDE[pn_azure_key_vault](pn-azure-key-vault.md)] との統合といった機能を備えた、[!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Storage SDK の最新機能を利用して暗号化されます。 [!INCLUDE[pn_crm_8_2_0_online_subsequent](pn-crm-8-2-0-online-subsequent.md)] では、電子メール メッセージや予定のメモと添付ファイルも Blob Storage に同期されます。  
  
[Azure Active Directory サービス](https://azure.microsoft.com/services/active-directory/)  
  
[!INCLUDE[pn_azure_active_directory](pn-azure-active-directory.md)] を使用して [!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)] と [!INCLUDE[pn_Windows_Azure](pn-windows-azure.md)] サービス間の認証を行います。  
  
[Azure Load Balancer](https://azure.microsoft.com/services/load-balancer/)  
  
[!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Load Balancer は、ロード バランサー セットで定義されているクラウド サービスや仮想マシンの正常なサービス インスタンス間で着信トラフィックを分散します。 関連性検索はこれを使用して、展開に含まれるエンドポイントの負荷分散を行います。  
  
[Azure Virtual Network](https://azure.microsoft.com/documentation/articles/virtual-networks-overview/)  
  
1 つ以上のサブネットで実行されている Service Fabric クラスター上の仮想マシンは、[!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Virtual Network によって接続されます。 セキュリティ ポリシー、DNS 設定、ルート テーブル、および IP アドレスはこの仮想ネットワークで完全に制御されます。 ネットワーク セキュリティ グループはこの仮想ネットワークにセキュリティ規則を適用するために使用されます。 これらの規則は仮想ネットワーク内の仮想マシンへのネットワーク トラフィックを許可または拒否します。