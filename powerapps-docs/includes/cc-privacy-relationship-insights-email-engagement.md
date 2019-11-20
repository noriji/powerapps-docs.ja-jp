埋め込みインテリジェンス機能である電子メール エンゲージメントを有効にすると、**フォロー**対象に設定されている電子メールが [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] から送信されたときに、受信者による電子メールでのやり取りについての情報が収集され、[!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] に保存されます。その目的は、受信者の活動を表す KPI と "フォロー対象" の電子メールでのやり取りを分析することです。  
  
 電子メール エンゲージメントは、システム管理者が埋め込みインテリジェンスの**電子メール エンゲージメント**タブでその機能を設定することにより、有効になります。 管理者は、**インテリジェンスの構成**ノードの**設定**で、組織の電子メール エンゲージメントを後から無効にすることができます。  
  
 この機能を無効にすると、[!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] から送信された電子メールは、ユーザー インターフェイスまたはプログラムのどちらの方法を使ってもフォローできません。 また、**フォロー**対象に設定された電子メールが送信されても、受信者のやり取りのデータは収集されません。 以前に収集されたデータは [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] に保存されており、この機能を組織で再度有効にした場合は、そのデータを利用できます。 データは、お客様と Microsoft のサブスクリプション契約が終了した後、90 日間保持されます。 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] ユーザーが、取引先担当者ごと、またはリードごとに埋め込みインテリジェンス - 電子メール エンゲージメント機能を無効にすることもできます。そのためには、**優先する連絡方法**で**電子メールのフォロー**の設定を変更します。  
  
 電子メール エンゲージメント機能に関連する [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] コンポーネントとサービスについて次に説明します。  
  
 [!INCLUDE[cc_privacy_note_azure_trust_center](cc-privacy-note-azure-trust-center.md)]  
  
 **[!INCLUDE[pn_azure_storage_account](pn-azure-storage-account.md)]**  
  
 電子メール エンゲージメント機能では、[!INCLUDE[pn_azure_storage_account](pn-azure-storage-account.md)] を使用して電子メールのやり取りの BLOB が一時的に保存されます。