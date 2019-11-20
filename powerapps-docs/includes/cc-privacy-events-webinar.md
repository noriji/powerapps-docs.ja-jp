イベント管理の利用条件に同意すると、ウェビナー統合機能がアクティブ化されます。 ウェビナー統合機能は、パートナー ウェビナー プロバイダーを活用してイベントまたはセッションをウェビナーとして実施する機能です。 ウェビナー プロバイダーのサービスを利用するには、プロバイダーに登録したアカウントが必要です。 現時点で、最初から提供されているパートナーのウェビナー プロバイダー サービスは ON24 だけです。 ウェビナー統合機能の使用時、ウェビナーの提供と実行に不可欠なデータは [!INCLUDE[pn-azure-service-fabric](../includes/pn-azure-service-fabric.md)] で処理され、保存された後、ON24 に送信されます。 このようなデータには、ウェビナー参加者の登録データ (名前、電子メール、会社名など) が含まれます。 また、ON24 はウェビナー閲覧時間などのウェビナー指標を [!INCLUDE[pn-azure-service-fabric](../includes/pn-azure-service-fabric.md)] 経由で [!INCLUDE[pn-microsoftcrm](../includes/pn-microsoftcrm.md)] に送信します。

イベント管理ソリューションのその他の機能を使用するために、ウェビナー機能をアクティブ化する必要はありません。 管理者は、ウェビナー構成で資格情報を削除することによって、ウェビナー統合機能をオフにすることができます。

ウェビナー統合機能によって使用される [!INCLUDE[pn-windows-azure](../includes/pn-windows-azure.md)] のコンポーネントとサービスは、次のとおりです。

- [!INCLUDE[pn_azure_key_vault](../includes/pn_azure_key_vault.md)] ([!INCLUDE[proc-more-information](../includes/proc-more-information.md)] [Azure Key Vault とは](https://docs.microsoft.com/azure/key-vault/key-vault-whatis))
  - お客様の ON24 アカウント資格情報の暗号化/暗号化解除のための暗号化キーを提供
- [!INCLUDE[pn-azure-service-fabric](../includes/pn-azure-service-fabric.md)] ([!INCLUDE[proc-more-information](../includes/proc-more-information.md)] [Azure Service Fabric の概要](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview))
  - 登録データとウェビナー アカウントの資格情報を処理して ON24 に送信
  - On24 から [!INCLUDE[pn-microsoftcrm](../includes/pn-microsoftcrm.md)] にウェビナー指標を取得 - 顧客の ON24 アカウント資格情報を保存 (カスタム暗号化)