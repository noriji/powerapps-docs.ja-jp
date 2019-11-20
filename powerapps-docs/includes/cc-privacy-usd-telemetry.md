[!INCLUDE[pn_unified_service_desk](pn-unified-service-desk.md)] の品質向上プログラム機能は、クライアントがインストールされたコンピューターから [!INCLUDE[pn_unified_service_desk](pn-unified-service-desk.md)] の使用状況に関する情報 (オペレーティング システムの詳細、ブラウザーの詳細、[!INCLUDE[pn_unified_service_desk](../includes/pn-unified-service-desk.md)] アプリケーション固有の情報、[!INCLUDE[pn_unified_service_desk](pn-unified-service-desk.md)] バージョンなど) を送信します。 [!INCLUDE[pn_unified_service_desk](pn-unified-service-desk.md)] は、組織のインサイトへの安全な接続を経由して、[!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Table Storage に保存された情報を [!INCLUDE[cc_Microsoft](cc-microsoft.md)] に送信します。
  
> [!NOTE]
>  組織のインサイトにより、[!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)]のシステム管理者は組織の利用状況の概要を知ることができます。 システム管理者は最もアクティブなユーザー、開始中の SDK 要求の数、SDK ユーザーによるビュー数を表示できます。
  
 Unified Service Desk の品質向上プログラム機能に関連する [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] コンポーネントとサービスを以下に示します。  
  
> [!NOTE]
>  その他の [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] サービス内容については、[Microsoft Azure セキュリティ センター](https://azure.microsoft.com/support/trust-center/)を参照してください。  
  
 [Cloud Services](https://azure.microsoft.com/services/cloud-services/) OrgInsights データの REST API (Web ロール)  
  
 この Web ロールは組織のインサイトにデータを表示するグラフから要求を受け取ります。 API は [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] テーブルから集計データを読み取り、そのデータを返します。  
  
 [Azure Blob Storage](https://azure.microsoft.com/services/storage/blobs/)  
  
 [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)] 組織の未加工の利用統計情報が (あらゆる規模のグループ コンピューターで実行される) 監視エージェントによって収集され、ボンド形式 (バイナリ形式) で [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob Storage にアップロードされます。  
  
 [Azure Table Storage](https://azure.microsoft.com/services/storage/tables/)  
  
 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob Storage 内の未加工のテレメトリ データは集計されて Azure Table Storage に保存され、Cloud Service はそこからデータを読み取ります。  
  
 [Azure Active Directory](https://azure.microsoft.com/services/active-directory/)  
  
 組織のインサイトは [!INCLUDE[pn_azure_active_directory](pn-azure-active-directory.md)] サービスを使用して Web サービスを認証します。  
  
 [Azure Service Bus](https://azure.microsoft.com/services/service-bus/)  
  
 監視エージェントは、データを [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob Storage にアップロードするたびにメッセージを作成し、キューに追加します。 これらのメッセージを CMA パイプが取得し、アップロードされたデータを集計します。