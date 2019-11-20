埋め込みインテリジェンスの機能であるリレーションシップ分析を有効にすると、ユーザーを特定できる情報を含む [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 顧客データが、Azure で実行されるサービスである [!INCLUDE[pn_customerinsight_full](pn-customer-insights-full.md)] に送信され、保存されます。その目的は、[!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] ユーザーと顧客の間のリレーションシップ KPI を計算することです。 また、データは一時的に [!INCLUDE[pn_azure_service_fabric](pn-azure-service-fabric.md)] に保存され、リレーションシップの正常性の状態と傾向などの追加出力のために処理されます。その情報は [!INCLUDE[pn_customerinsight_short](pn-customer-insights-short.md)] に返され、その後 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] に返されます。  
  
 管理者は、リレーションシップ分析機能を [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)] 組織にソリューションとしてインストールすることで、この機能を有効にできます。 また、管理者はその後、[!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)] 組織からソリューションをアンインストールすることで、機能を無効にできます。  
  
 [!INCLUDE[pn_Exchange](pn-exchange.md)] データをデータ ソースとして有効にすると、[!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 顧客データ (エンドユーザーを特定できる情報を含む) が [!INCLUDE[pn_customerinsight_full](pn-customer-insights-full.md)] から [!INCLUDE[pn_Exchange_Online](pn-exchange-online.md)] に送信されます。その目的は追加データを収集することで、収集されたデータは KPI の計算や他の分析の作成に使用されます。  この機能を完全に有効にするには、[!INCLUDE[pn_Office_365](pn-office-365.md)][!INCLUDE[pn_Exchange](pn-exchange.md)] 管理者にも、[!INCLUDE[pn_Exchange](pn-exchange.md)] アプリケーションで別個の同意文に同意してもらう必要があります。  両方の管理者が、それぞれの製品で同意した後、[!INCLUDE[pn_Exchange](pn-exchange.md)] は電子メールと会議のメタデータを生成します。そのメタデータは [!INCLUDE[pn_customerinsight_full](pn-customer-insights-full.md)] に保存され、KPI 計算の改善に使用されます。また、[!INCLUDE[pn_customerinsight_full](pn-customer-insights-full.md)] 管理者によってその他の分析が定義されている場合は、その改善にも使用されます。 リレーションシップ分析の構成で [!INCLUDE[pn_Exchange](pn-exchange.md)] データをデータ ソースとして無効にしても、[!INCLUDE[pn_Exchange](pn-exchange.md)] データは [!INCLUDE[pn_customerinsight_full](pn-customer-insights-full.md)] から削除されません。  [!INCLUDE[pn_customerinsight_full](pn-customer-insights-full.md)] での [!INCLUDE[pn_Exchange](pn-exchange.md)] データの削除は、[!INCLUDE[pn_customerinsight_full](pn-customer-insights-full.md)] から直接削除することによってのみ実行できます。  
  
 リレーションシップ分析に関連する [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] コンポーネントとサービスについては、以下のセクションで説明します。  
  
 [!INCLUDE[cc_privacy_note_azure_trust_center](cc-privacy-note-azure-trust-center.md)]  
  
 **[!INCLUDE[pn_customerinsight_full](pn-customer-insights-full.md)]**  
  
 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] で実行されるサービスである [!INCLUDE[pn_customerinsight_short](pn-customer-insights-short.md)] は、[!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] データ (顧客に関する、個人を特定できる情報を含む) を保存します。その目的は、リレーションシップ分析機能の出力を計算することです。 [!INCLUDE[pn_customerinsight_short](pn-customer-insights-short.md)] のプレビューには、[プレビュー機能の追加使用条件](https://go.microsoft.com/fwlink/p/?LinkId=511446)が適用されます。  
  
 [Customer Insights のプレビューの詳細については、こちらを参照してください](https://azure.microsoft.com/services/customer-insights/)。  
  
 [Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/)  
  
 [!INCLUDE[pn_azure_service_fabric](pn-azure-service-fabric.md)] は、リレーションシップ分析機能の出力を計算することを目的に、[!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] データ (顧客に関する、個人を特定できる情報を含む) を保存するために使用されます。