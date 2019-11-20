Dynamics 365 のお客様の声機能を有効にすると、Dynamics 365 内から調査を公開するときに、調査の定義が Azure に送信され、Azure Storage に保存されます。 回答者が (電子メールで送信された調査の招待状のリンクを開くことで) 調査を送信すると、調査の回答は Azure Service Bus に一時的に保存されてから、Dynamics 365 で取得されて保存されます。 Dynamics 365 に保存された後、回答は Azure から削除されます。  
  
 回答者に調査を実施する際に、顧客名、製品名、サポート案件番号などの Dynamics 365 データが調査 (質問と回答などの調査要素の中) に含まれる場合がある点に注意してください。 調査招待状リンクが生成されると、この Dynamics 365 データは Dynamics 365 から Azure SQL Database に送信され、調査招待状リンク内で使用されている ID の代わりに保存されます。 この ID は、調査招待状のリンクを使って調査が開かれた後、調査内に Dynamics 365 データを表示するために使用されます。 回答者に電子メールで送信された調査リンク内の ID は、回答者の電子メール システムに保存されます。  
  
 管理者は、Dynamics 365 のお客様の声機能を Dynamics 365 組織にソリューションとしてインストールすることで、この機能を有効にできます。 また、管理者はその後、Dynamics 365 組織からソリューションをアンインストールすることで、機能を無効にできます。  
  
 Dynamics 365 のお客様の声機能に関連する Azure コンポーネントとサービスについては、以下のセクションで説明します。  
  
 メモ: その他の Azure サービス内容については Microsoft Azure セキュリティ センター ([https://azure.microsoft.com/support/trust-center/](https://azure.microsoft.com/support/trust-center/)) を参照してください。  
  
 **Cloud Services** ([https://azure.microsoft.com/services/cloud-services/](https://azure.microsoft.com/services/cloud-services/))  
  
 **デザイナー サービス (Web ロール)**  
  
 Dynamics 365 組織とマルチテナント型 "Dynamics 365 のお客様の声" の Azure コンポーネント間の通信のために複数の Web サービスを提供します。  たとえば、調査を公開して Azure Blob Storage に保存します。  調査回答は Azure Service Bus キューから取得され、Dynamics 365 組織で保存できるように返されます。  すべてのリクエストは Azure Active Directory に対して認証されます。  
  
 **調査ランタイム (Web ロール)**  
  
 これは、回答者への調査を扱う Web アプリケーションです。  送信された調査回答は、Azure Service Bus キューに一時的に保存されてから、Dynamics 365 非同期サービスによって処理されて取得されます。  
  
 **応答プロセッサ (ワーカー ロール)**  
  
 このワーカー ロールは、完了した調査の生データを、Dynamics 365 で作成できる有効な調査回答になるように処理します。  
  
 **プッシュ プロセッサ (ワーカー ロール)**   このワーカー ロールは、有効な調査回答を処理し、Dynamics 365 のエンティティ レコードとして更新します。 
 
 **Azure Key Vault** ([https://azure.microsoft.com/services/key-vault/](https://azure.microsoft.com/services/key-vault/))  
  
 すべてのクラウド サービスの構成データは Azure Key Vault に保存されます。  組織とテナントのデータは SQL Azure に保存されます。  
  
 **Azure SQL Database** ([https://azure.microsoft.com/services/sql-database/](https://azure.microsoft.com/services/sql-database/))  
  
 Dynamics 365 のお客様の声では、SQL Azure を使用して次のデータを保存します。  
  
-   パイプ指定されたデータ  
  
-   調査メタデータ  
  
-   組織 (テナント) データ  
  
 **Azure Blob Storage** ([https://azure.microsoft.com/services/storage/](https://azure.microsoft.com/services/storage/))  
  
 調査の定義および一部完了した (保存された) 応答は、Azure Blob Storage に保存されます。  
  
 **Azure Content Delivery Network (CDN)** ([https://azure.microsoft.com/services/cdn/](https://azure.microsoft.com/services/cdn/))  
  
 Dynamics 365 のお客様の声ソリューションは、Azure Content Delivery Network を使って画像 (顧客のロゴなどのアップロードされた画像を含む)、JavaScript、CSS などの静的コンテンツを調査ランタイムに送ります。  
  
 **Azure Active Directory** ([https://azure.microsoft.com/services/active-directory/](https://azure.microsoft.com/services/active-directory/))  
  
 Dynamics 365 のお客様の声ソリューションは、Azure Active Directory サービスを使って Web サービスを認証します。  
  
 **Azure Service Bus** ([https://azure.microsoft.com/services/service-bus/](https://azure.microsoft.com/services/service-bus/))  
  
 調査が表示または送信されるときに作成されるメッセージは、Azure ワーカー ロールが調査回答を組織の Dynamics 365 インスタンスにプッシュし、Dynamics 365 エンティティ レコードとして保持されるまで、組織 (テナント) の Azure Service Bus キューに一時的に保存されます。
