[!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] を有効にすると、一部のマーケティング プロセスを実行するために [!INCLUDE[pn-microsoftcrm](../includes/pn-microsoftcrm.md)] から特定の [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] サービスへのデータのフローを許可することに同意したものと見なされます。 これらのサービスは、まとめて "[!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)] サービス" と呼ばれます。

顧客体験を実行するには、[!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] から顧客体験、電子メール、送信フォーム、マーケティング ページの定義を、[!INCLUDE[pn_azure_service_fabric](../includes/pn_azure_service_fabric.md)] で実行しているこれらの [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)] サービスに送る必要があります。 マーケティング ページはさらに、[!INCLUDE[pn-microsoftcrm](../includes/pn-microsoftcrm.md)] のポータル機能の顧客独自のインスタンスに送信されます。

送信されるメールを個人設定するため、[!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] は [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] との間の双方向のデータ フローを有効にする必要があります。 [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] サービスについて詳しくは、以下をご覧ください。 [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] へのデータ フローには、[!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] への取引先担当者と取引先企業の同期が含まれます。 [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)] サービスは、このデータを使って電子メールの内容を個人設定します。 含まれるデータは、電子メールの定義のみに依存します。

リード スコア モデルとマーケティング セグメントを再計算するため、[!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] は、リード スコア モデルの定義とセグメントの定義を [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] に送信し、[!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] でのプロファイルと対話をこれらの計算に利用する必要があります。

[!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)] サービスによってキャプチャされたメールとインターネットでの対話へのインサイトを提供するため、収集されたデータが、[!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)] サービスから [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] と [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] の両方に送られます。

さらに、[!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] のイベント管理統合が有効になっている場合、[!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] は、[!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] ([!INCLUDE[pn-crm-online-shortest](../includes/pn-crm-online-shortest.md)] 用コネクタを介して直接) およびイベント登録とチェックイン ([!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)] サービスを介して対話として) に対して、イベントを同期しています。

[!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] に関するデータ フローは次のとおりです。
- [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] から [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] へのエンティティ データ。[!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] の通常の受信コネクタを使用し、目的は電子メールの個人設定、リード スコアリング、セグメント化のためのコンテンツを提供することです (主として取引先担当者と取引先企業、最終的にはリードとイベントも)
- [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] から [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] への [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)] サービスを介したエンティティ データ。目的は、対話とインサイトのための識別子を提供することです (顧客体験、マーケティング電子メール、マーケティング ページ)
- [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)] サービスから [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] への対話 (メール追跡、Web サイト追跡、顧客体験の進行)
- [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] から [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] への [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)] サービスを介した対話 (イベント登録とチェックイン)
- [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] から [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] への [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)] サービスを介した[!INCLUDE[pn-insights](../includes/pn-insights.md)] (対話と KPI) (主として、顧客体験、メール送信の進行状況、リード スコアリングの結果)
- [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] から直接 [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] のフォーム内の専用 UI 要素およびサンドボックス化された UI 要素への [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] アプリ (セグメント化およびウィジェット)

### <a name="marketing-services"></a>マーケティング サービス

[!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] では以下の [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] サービスが使用されます。

- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] Data Lake Store
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] Data Lake Analytics
- [!INCLUDE[pn-azure-key-vault](../includes/pn-azure-key-vault.md)]
- [!INCLUDE[pn_azure_service_fabric](../includes/pn_azure_service_fabric.md)]
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] DocumentDb
- [!INCLUDE[pn-microsoft-azure-active-directory](../includes/pn-microsoft-azure-active-directory.md)]
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] Storage

> [!NOTE]
> その他の [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] サービス オファリングの詳細については、「[!INCLUDE[cc_privacy_note_azure_trust_center](../includes/cc_privacy_note_azure_trust_center.md)]」(<https://azure.microsoft.com/support/trust-center/>) を参照してください。

### [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)]

[!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] を使うと、詳細な処理のための [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] への顧客データの転送がアクティブになります。 [!INCLUDE[pn-microsoftcrm](../includes/pn-microsoftcrm.md)] のための [!INCLUDE[pn-customer-insights-short](../includes/pn-customer-insights-short.md)] の使用では、プライバシーに関する特定の法律への準拠が必要になる場合があります。 質問がある場合は、組織内の適切な担当者に問い合わせてください。

現在、[!INCLUDE[pn-customer-insights-short](../includes/pn-customer-insights-short.md)] はパブリック プレビュー段階にあり、[!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] または Common Data Service と同レベルのプライバシーとセキュリティは提供されません。 [!INCLUDE[pn-customer-insights-short](../includes/pn-customer-insights-short.md)] は、[!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] サービスにネイティブに基づいており、該当する各 [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] サービスのコンプライアンスとセキュリティ標準が適用されます。 詳細については、[!INCLUDE[cc-microsoft](../includes/cc-microsoft.md)] セキュリティ センターを参照してください: [https://azure.microsoft.com/support/trust-center/](https://azure.microsoft.com/support/trust-center/)

[!INCLUDE[pn-customer-insights-short](../includes/pn-customer-insights-short.md)] では以下の [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] サービスが使用されます。

- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] Data Lake Store
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] Data Lake Analytics
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] HDInsight (Spark、Phoenix、HBase)
- [!INCLUDE[pn-ms-azure-sql-database](../includes/pn-ms-azure-sql-database.md)]
- [!INCLUDE[pn-azure-key-vault](../includes/pn-azure-key-vault.md)]
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] シークレット ストア
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] イベント ハブ
- [!INCLUDE[pn-azure-stream-analytics](../includes/pn-azure-stream-analytics.md)]
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] Redis Cache
- [!INCLUDE[pn_azure_service_fabric](../includes/pn_azure_service_fabric.md)]
- [!INCLUDE[pn-microsoft-azure-active-directory](../includes/pn-microsoft-azure-active-directory.md)]
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] Monitoring
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] メトリックス
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] Websites
- [!INCLUDE[pn_azure_service_bus](../includes/pn_azure_service_bus.md)]
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] Storage
