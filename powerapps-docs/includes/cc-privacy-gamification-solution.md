[!INCLUDE[pn_gamification](pn-gamification.md)] ソリューションをインストールして有効化すると、有効化を行ったユーザーのアカウント識別情報 (名、姓、電子メール アドレスなど) が [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] に保存され、[!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] サービスに対する認証に使用されます (このサービスは [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] でホストされます)。 これは、[!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] サービス内で管理者によって有効化されたすべてのユーザーに当てはまります。 [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] ソリューションは、管理者によって構成された主要業績評価指標 (KPI) データを [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] サービスに送信し、そのデータが [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] の構造化ストレージと BLOB ストレージに保存されます。  各ユーザーのアバター、カスタム アワード、会社ロゴは [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] に保存されますが、この情報は [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)] に返されません。  
  
管理者と承認されたユーザーは、電話、営業案件、予約済み売上などの [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)] データを利用して、ゲームで使用する KPI を構成できます。 [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] サービスから [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)] に呼び出しが行われることはなく、KPI が使用されているゲームなどのデータに対する応答のみが行われます (その応答は [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)] に送り返されます)。  
  
管理者は [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] TV ストリームを公開できるようにすることもできます。 ゲーム マネージャーが [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] TV ストリームを設定して公開ストリーミングを有効化すると、ストリームのリンクを知っていればだれでも、インターネットに接続してその TV ストリームを視聴できるようになります。  
  
管理者は後からこのソリューションを [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)] 組織からアンインストールすることで、[!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] 機能を削除できます。  
  
[!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] に関係する [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] のコンポーネントとサービスの詳細については、以下のセクションを参照してください。  
  
[!INCLUDE[cc_privacy_note_azure_trust_center](cc-privacy-note-azure-trust-center.md)]  
  
[Cloud Services](https://azure.microsoft.com/services/cloud-services/)  
  
 **デザイナー サービス (Web ロール)**  
  
[!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)] 組織とマルチテナント型 [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] の [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] コンポーネント間の通信のために複数の Web サービスを提供します。 たとえば、Gamification の詳細を [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] SQL Storage に保存します。  ゲームの計算結果は [!INCLUDE[pn_azure_service_bus](pn-azure-service-bus.md)] キューから取得され、スコアを記録して表示できるように返されます。  顧客とユーザーがアップロードした画像は [!INCLUDE[pn_azure_blob_storage](pn-azure-blob-storage.md)] に保存されます。 すべてのリクエストは [!INCLUDE[pn_azure_active_directory](pn-azure-active-directory.md)] に対して認証されます。  
  
[Azure Key Vault](https://azure.microsoft.com/services/key-vault/)  
  
すべてのサービスの構成データは、[!INCLUDE[pn_azure_key_vault](pn-azure-key-vault.md)] に保存されます。  
  
[Azure SQL Database](https://azure.microsoft.com/services/sql-database/)  
  
[!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] は SQL [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] を使用して次の情報を保存します。  
  
- KPI データ  
  
- ゲームの計算結果  
  
- 組織 (テナント) データ  
  
[Azure Blob Storage](https://azure.microsoft.com/services/storage/)  
  
アバターや会社ロゴ、顧客がアップロードしたその他の画像は、[!INCLUDE[pn_azure_blob_storage](pn-azure-blob-storage.md)] に保存されます。  
  
[Azure Content Delivery Network (CDN)](https://azure.microsoft.com/services/cdn/)  
  
[!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] は、[!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] コンテンツ配信ネットワークを使用して、画像 (顧客ロゴなどのアップロードされた画像を含む)、[!INCLUDE[pn_JavaScript](pn-javascript.md)]、CSS などの静的コンテンツをランタイムに提供します。  
  
[Azure Active Directory](https://azure.microsoft.com/services/active-directory/)  
  
[!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] は、[!INCLUDE[pn_azure_active_directory](pn-azure-active-directory.md)] を使用してユーザーを認証し、プラットフォームの利用資格があるかどうかを決定します。