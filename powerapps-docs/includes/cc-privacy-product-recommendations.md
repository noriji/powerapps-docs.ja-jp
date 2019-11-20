製品レコメンデーション機能を有効にすることで、[!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)] 内からレコメンデーション モデルを作成するときに、構成されたバスケット データ エンティティとそのフィルターに基づくトランザクションの履歴データが [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] に送信されて [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] で処理され、一時的に [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Storage に保存され、最終的に Azure Recommendations API に送信されて機械学習モデルが構築されます。 モデルが Azure Recommendations API で作成されると、データが [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Storage から削除されます。 ID (アカウント ID、製品 ID、トランザクション ID) のみが [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] に送信されてレコメンデーション モデルが構築されます。

管理者は、[!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)] 組織の**設定** &gt; **管理** &gt; **システムの設定** &gt; **プレビュー**タブで製品レコメンデーション機能を有効にできます。 データは、レコメンデーション モデルが構築されているときにのみ Azure Recommendations API に送信されます。 システム管理者には既存のモデルを削除するオプションがないため、Azure Recommendations API で共有されたデータを削除できません。 また、システム管理者は将来にわたってレコメンデーション モデルが削除されないように、Azure Recommendations API への接続を削除できます。

製品レコメンデーション機能に関連する [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] のコンポーネントとサービスについては、次のセクションで説明します。

[!INCLUDE[cc_privacy_note_azure_trust_center](cc-privacy-note-azure-trust-center.md)]

[Azure Logic Apps](https://azure.microsoft.com/services/app-service/logic/)

製品カタログとトランザクション データを Recommendations API と同期してレコメンデーション モデル バージョンを構築する、調整されたデータ パイプラインを提供します。 このパイプラインは、Dynamics 365 組織と Recommendations API の間の通信のために、複数の API アプリでマルチテナント型のサービスとして実行されます。 Logic Apps は、モデル バージョン ID や [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 組織の URL など、[!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] から最小のコンテキストでトリガーされます。 

[Azure API Apps](https://azure.microsoft.com/services/app-service/api/)

これらの Web アプリケーションによってトリガーされる Web ジョブは、[!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 組織からデータを読み込み、Recommendations API にデータを送信してレコメンデーション モデルを構築します。 3 つの API アプリと対応する Web ジョブがあります。1 つは製品データを読み取り、1 つはトランザクション データを読み取り、1 つはレコメンデーション モデルを構築します。 API アプリは Web ジョブを使用してバックグラウンドで実際のデータ処理を実行し、データ出力を [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob Storage に書き込みます。 データは [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob Storage に一時的に保存されます。 最終的にモデルが作成されると、データは [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Storage から削除されます。

[Azure Table](https://azure.microsoft.com/services/storage/tables/)

[!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Table は、API アプリと Web ジョブの間で、モデル バージョンと組織のコンテキストの通信に使用されます。

[Azure Blob Storage](https://azure.microsoft.com/services/storage/) 

データは Web ジョブにより [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob Storage に一時的に保存され、Logic App パイプラインの実行が完了した時点で削除されます。

[Azure Recommendations API](https://www.microsoft.com/cognitive-services/recommendations-api) Azure Recommendations API は製品 ID、トランザクション ID、アカウント ID などの最小限のデータと共に送信され、レコメンデーション モデルを構築します。 データは対応するモデル バージョンが存在するまで Recommendations API で保存されます。
