---
title: Common Data Service とは何か？ | Microsoft Docs
description: Common Data Service、エンティティ、サーバーサイド ロジック、セキュリティ、開発者向け機能の概要。
author: clwesene
manager: kvivek
ms.service: powerapps
ms.topic: overview
ms.component: cds
ms.date: 06/21/2019
ms.reviewer: matp
ms.author: matp
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="what-is-common-data-service"></a>Common Data Service とは何か？
Common Data Service を使用することで、ビジネス アプリケーションで使用されるデータを安全に保存、管理することできます。 Common Data Service 内のデータは、一連のエンティティ内に格納されています。 *エンティティ*はデータベース内にデータを格納する方法と同様に、データの格納に使用される一連のレコードです。 Common Data Service には一般的なシナリオをカバーする標準エンティティの基本セットが含まれていますが、組織固有のカスタム エンティティを作成し、Power Queryを使用したデータ取り込みを行うことも可能です。 アプリ作成者はこのデータを使用して機能豊富なアプリケーションを作成するために PowerApps を使用できます。

![ビジネス アプリケーション プラットフォームの概要を示すスクリーンショット。](./media/data-platform-cds-intro/platform.png "プラットフォームの概要")

Common Data Serviceを使用するプランの購入については、 [価格情報](../../administrator/pricing-billing-skus.md)を参照してください。

## <a name="why-use-common-data-service"></a>なぜ Common Data Serviceを使うのか?
Common Data Service 内の標準エンティティおよびカスタム エンティティは、ご利用のデータに対する安全なクラウドベースのストレージ オプションを提供します。 エンティティを使用すると、アプリ内で使用するための組織のデータのビジネス重視の定義を作成できます。 エンティティが最善の選択肢であるかどうか分からない場合は、次の点を考慮してください。

* **簡単に管理できます** &ndash; メタデータとデータの両方がクラウドに格納されます。 それらがどのように格納されているかの詳細について気にする必要はありません。
* **セキュリティ保護を簡単にできます** &ndash; データが安全に保存されるため、ユーザーはアクセスを許可した場合にのみデータを見ることができます。 ロール ベースのセキュリティでは、組織内のさまざまなユーザーのエンティティへのアクセスを制御できます。
* **Dynamics 365 データにアクセスする** &ndash; また、Dynamics 365アプリケーションのデータは  Common Data Service に保存されるため、Dynamics 365 のデータを活用したアプリケーションの迅速な構築や、PowerAppsを使用したアプリケーションの拡張が可能になります。
* **豊富なメタデータ** &ndash; データの種類と関連付けは、PowerApps 内で直接利用されます。
* **ロジックおよび検証** &ndash; 計算フィールド、業務ルール、ワークフロー、およびビジネス プロセス フローを定義して、データ品質を保証し、業務プロセスを推進します。
* **プロダクティビティ ツール** &ndash; エンティティは Microsoft Excel のアドイン内で使用可能となり、生産性を向上させ、データへのアクセス性を確保します。

## <a name="dynamics-365-and-the-common-data-service"></a>Dynamics 365 と Common Data Service

Dynamics 365 for Sales、サービス、Talent などのDynamics 365 アプリケーションにおいては、アプリケーションで使用するデータの格納と保護には Common Data Service を使用しています。 これにより PowerAppsと Common Data Service を使って、すでに Dynamics 365 で使用されているコア ビジネスデータに直接アプリケーションを構築することができます。

* **Dynamics 365 データに対するアプリケーションの構築** &ndash; PowerApps 内のビジネス データに対して、または Pro Developer SDK を使用して、アプリケーションを迅速に構築します。
* **再利用可能なビジネス ロジックとルールの管理** &ndash; ご利用のPowerApps にDynamics 365エンティティですでに定義されているビジネス ルールとロジックが適用されます。これによってユーザーがどのようにデータにアクセスしているか、どのアプリを使っているかを問わずデータの一貫性が保証されます。
* **Dynamics 365とPowerApps 全体で再利用可能なスキル** &ndash; これまで PowerApps や Dynamics 365 のスキルを持っていたユーザーは、新たな Common Data Service プラットフォームでそのスキルを活用できます。 エンティティ、フォーム、チャートなどの作成は、アプリケーション全体で共通になりました。

    > [!NOTE]
    > 現在 Dynamics 365 for Finance and Operations を使用するには、Data Integrator の構成を使用して、Finance and Operations からのビジネス データを Common Data Service 内で使用可能にする必要があります。

## <a name="integrating-data-into-the-common-data-service"></a>データを Common Data Serviceに統合する

アプリケーションの構築には、通常、複数のソースからのデータが含まれますが、これはアプリケーション レベルで行われることもあります。このデータを共通のストアに統合することで、アプリケーション構築の経験が簡単になり、データを維持して操作するための単一のロジック セットが可能になる場合もあります。 Common Data Service を使用すると、複数のソースから単一のストアにデータを統合し、Dynamics 365アプリケーションからすでに入手可能なデータとともに PowerApps、 Power Automate 、 Power BI で使用できるようになります。

* **他システムとの統合をスケジュールする** &ndash; 他のアプリケーションに保存されているデータは定期的に Common Data Service と同期することが可能であり、PowerApps 内の他のアプリケーションのデータを活用することができます。
* **PowerQueryを使用したデータの変換とインポート** &ndash; Common Data Serviceへのインポートする際のデータ変換は、Excel と Power BIにて共通のツールである多くのオンライン データソースから、PowerQueryを使って行うことができます。
* **データの一括インポート** &ndash; ExcelおよびCSVファイルの簡単なインポート/エクスポートは、データの Common Data Serviceへの1回限りのインポート、または不定期のインポートに使用できます。

Common Data Serviceへのデータの統合についての詳細にていては、 [Power Queryを使用して Common Data Service のエンティティにデータを追加する](data-platform-cds-newentity-pq.md) を参照してください。

## <a name="interacting-with-entities"></a>エンティティとのやりとり
アプリケーションを開発する場合は、標準エンティティ、ユーザー定義エンティティ、または両方を使用できます。 Common Data Service は、既定で標準エンティティを提供します。 組織内の最も一般的な概念やシナリオを取得するよう、推奨事項に従って設計されています。

![エンティティのリストを表示するスクリーンショット。](./media/data-platform-cds-intro/entitylist.png "エンティティ リスト")

エンティティのリストの全一覧については、[エンティティ参照](https://docs.microsoft.com/powerapps/developer/common-data-service/reference/about-entity-reference) を参照してください。

組織に固有の情報を格納する 1 つ以上のカスタム エンティティを作成して、標準エンティティの機能を拡張できます。 詳細については、[カスタム エンティティの作成方法](create-custom-entity.md) を参照してください。

## <a name="logic-and-validation"></a>ロジックおよび検証
Common Data Service 内のエンティティは、豊富なサーバーサイドのロジックと検証を活用してデータ品質を保証し、エンティティ内でデータを作成し、使用する各アプリケーションにて繰り返し使用されるコードを削減できます。

* **業務ルール**は、複数のフィールドとエンティティ間でデータを検証し、データの作成に使用されたアプリケーションに関係なく、警告メッセージとエラー メッセージを表示します。 詳細については、[業務ルールの作成](./data-platform-create-business-rule.md) を参照してください。
* **業務プロセス フロー**は、ユーザーがデータを統一して入力し、毎回同じ手順に従うようにします。 業務プロセス フローでは、現在モデル駆動型アプリでのみサポートされています。 詳細については、[業務プロセス フローの概要](/dynamics365/customer-engagement/customize/business-process-flows-overview) を参照してください。
* **ワークフロー**は、ユーザー対話を使用しないビジネス プロセスを可能にします。 詳細については、[ワークフローの概要](/dynamics365/customer-engagement/customize/workflow-processes)の説明を参照してください。
* **コードによるビジネス ロジック**は、高度な開発者シナリオをサポートし、アプリケーションをコードを通じて直接拡張します。 詳細については、[コードによるビジネスロジックの適用](../../developer/common-data-service/apply-business-logic-with-code.md) を参照してください。

## <a name="security"></a>セキュリティ
Common Data Service は、効率的なデータ アクセスと協業を活性化しつつも、データの整合性とプライバシーを保護するための豊富なセキュリティ モデルを備えています。 ビジネス ユニット、役割にもとづくセキュリティ、レコード にもとづくセキュリティ、フィールドにもとづくセキュリティを組み合せて、 Common Data Service 環境にてユーザーが保有する情報への包括的なアクセスを定義することができます。 詳細情報については次を参照してください: [ Common Data Serviceのセキュリティ](/power-platform/admin/wp-security) 

## <a name="developer-capabilities"></a>開発者機能
[PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) ポータルで利用可能な機能に加えて、 Common Data Service は開発者がメタデータとデータにアクセスしてエンティティとビジネスロジックをプログラムし、データとやり取りするために使用できる機能を実装しています。 詳細については、 [Common Data Service 開発者向けの概要](../../developer/common-data-service/overview.md)をご覧ください。

## <a name="next-steps"></a>次のステップ
Common Data Serviceを使用して作業を開始するには:
- [ Common Data Service のデータベースを使用してキャンバス アプリケーションを作成する](../canvas-apps/data-platform-create-app-scratch.md)
- [カスタム エンティティを作成する](create-custom-entity.md) [エンティティを使用するキャンバス アプリケーションを作成する](../canvas-apps/data-platform-create-app.md)
- Common Data Service上に構築された[モデル駆動アプリを作成する](/powerapps/maker/model-driven-apps/build-first-model-driven-app)
- [Power Queryを使用](./data-platform-cds-newentity-pq.md) してオンラインまたはオンプレミスのデータソースに接続し、データを直接 Common Data Serviceにインポートする。

## <a name="privacy-notice"></a>プライバシーに関する声明
Microsoft PowerApps の Common Data モデルを使用することで、Microsoft はカスタム エンティティとフィールド名称を収集し、診断システムに保管します。 この情報を使って、お客様の共通データ モデルを改善します。 アプリケーション作成者が作成するエンティティ名称とフィールド名称は、 Microsoft PowerApps コミュニティに通底するシナリオの理解に役立ち、組織に関連するスキーマなど、サービスの標準的なエンティティ カバレッジのギャップを確認する際に役立てられます。 これらのエンティティに関連付けられたデータベース テーブル内のデータは、Microsoft によりアクセスまたは使用されず、データベースがプロビジョニングされた地域の外部にレプリケーションされません。 しかし、カスタム エンティティおよびフィールド名は、地域間でレプリケーションされ、データ保持ポリシーに基づいて削除される可能性がある点に注意してください。 マイクロソフトは、[セキュリティ センター](https://www.microsoft.com/trustcenter/Privacy/default.aspx) で詳しく説明されているとおりにプライバシー保護に努めています。
