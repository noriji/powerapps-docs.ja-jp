データ エクスポート サービスを使用すると、[!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)] 内からデータ エクスポート プロファイルをアクティブ化するときに、プロファイルに追加されたエンティティのデータが [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] に送信されます。 最初の同期には、エクスポート プロファイルに追加されたエンティティに関連付けられているすべてのデータが含まれますが、以降の同期には、データ エクスポート サービスに継続的に送信される新しく加えられた変更のみが含まれます。 データ エクスポート サービスに送信されたデータは一時的に [!INCLUDE[pn_azure_service_bus](pn_azure_service_bus.md)] と [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Storage に保存されて [!INCLUDE[pn_azure_service_fabric](pn_azure_service_fabric.md)] で処理され、最終的に [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] サブスクリプションで指定されている送信先のデータベースに同期 (挿入、更新、または削除) されます。 データが同期されると、そのデータは [!INCLUDE[pn_azure_service_bus](pn_azure_service_bus.md)] と [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Storage から削除されます。 データ同期中にエラーが発生すると、エンティティの種類、レコード ID、および同期タイムスタンプに対応する最小データが [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Storage に保存され、更新されなかった一覧のレコードがダウンロードできるようになります。  
  
 管理者は任意のタイミングでデータ エクスポート プロファイルを非アクティブ化し、データ同期を停止できます。 さらに、管理者はエクスポート プロファイルを削除してエラーが発生したレコードのログを削除し、データ エクスポート サービス ソリューションをアンインストールしてデータ エクスポート サービスの使用を停止できます。  
  
 データ同期は [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)] とデータ エクスポート サービスの間で安全な方法で継続的に発生します。 データが [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)] とデータ エクスポート サービスの間で継続的に交換される際には暗号化されます。  
  
 データ エクスポート サービスに関連する Azure コンポーネントとサービスについては、以下のセクションで説明します。  
  
 [!INCLUDE[cc_privacy_note_azure_trust_center](cc_privacy_note_azure_trust_center.md)]  
  
 [Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/)  
  
 [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)] から受け取ったレコード同期通知を処理するための API および [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] コンピューティング VM を提供します。受け取ったレコード同期通知を処理して送信先データベースのレコード データを挿入、更新、または削除します。 [!INCLUDE[pn_azure_service_fabric](pn_azure_service_fabric.md)] ランタイムで管理される仮想マシンに展開されたマイクロサービスは、データ同期に関連するすべてのコンピューティング サービスを処理します。  
  
 [Azure Service Bus](https://azure.microsoft.com/services/service-bus/)  
  
 これは、[!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)] が [!INCLUDE[pn_azure_service_fabric](pn_azure_service_fabric.md)] のコンピューティング ノードで処理される同期通知メッセージを挿入する、メッセージ バスを提供します。 各メッセージに、組織 ID やレコードなど、同期するデータの情報が保存されます。 Azure Service Bus のデータは、保管時に暗号化はされませんが、データ エクスポート サービスによるアクセスのみが可能です。  
  
 [Azure Blob Storage](https://azure.microsoft.com/services/storage/)  
  
 レコード同期通知データが大きすぎてメッセージに格納できない、または同期通知の処理で一時エラーが発生した場合、データは一時的に [!INCLUDE[pn_azure_blob_storage](pn_azure_blob_storage.md)] に保存されます。 これらの BLOB は、対称および非対称暗号化のサポート、[!INCLUDE[pn_azure_key_vault](pn-azure-key-vault.md)] との統合といった機能を備えた、[!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Storage SDK の最新機能を利用して暗号化されます。  
  
 [Azure SQL](https://azure.microsoft.com/services/sql-database/)  
  
 [!INCLUDE[pn_Azure_SQL_Database_long](pn-azure-sql-database-long.md)] はデータ エクスポート プロファイルの構成とデータ同期の指標を保存します。