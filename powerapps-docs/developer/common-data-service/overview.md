---
title: Common Data Service 開発者ガイド | Microsoft Docs
description: 開発者が Common Data Service を使って値を追加する方法を説明します。
author: JimDaly
manager: annbe
ms.service: powerapps
ms.topic: article
ms.date: 03/27/2019
ms.author: jdaly
ms.reviewer: kvivek
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---

# <a name="common-data-service-developer-guide"></a>Common Data Service 開発者ガイド

PowerApps では、ユーザー、企業、独立系ソフトウェア ベンダー (ISV)、およびシステム インテグレーター (SI) に、基幹業務アプリを構築するための強力なプラットフォームを提供します。 サーバー側のロジック (プラグインとワークフロー)、業務プロセス フロー、高度なセキュリティ モデル、そして開発者がアプリを構築する拡張可能なプラットフォームなど、**Common Data Service** は、PowerApps の基盤となるデータ プラットフォームです。 

Common Data Service を使用したアプリを作成するのに開発者がどのように貢献できるか多数の側面があります。 データ ソースとして Common Data Service を使用するコードでアプリケーションが構築できる一方、多くのプロジェクトでは、[モデル駆動型アプリ](/powerapps/maker/model-driven-apps/model-driven-app-overview) または [キャンバス アプリ](/powerapps/maker/canvas-apps/getting-started) を使用してユーザーのエクスペリエンスを生成します。 

## <a name="working-with-model-driven-apps"></a>モデル駆動型アプリに関する作業

駆動型モデルのアプリは Common Data Service でビルドされ、 Common Data Service 環境にのみ接続できます。 モデル駆動型アプリを定義するすべてのデータは Common Data Service に格納されます。

モデル駆動型アプリは、[ソリューション](introduction-solutions.md) を使用して Common Data Service に使用されるカスタマイズと拡張の配布方法を共有します。

モデル駆動型アプリには開発者がコードを記述して拡張するための多くのポイントもあります。 開発者がモデル駆動型アプリでできることについては [モデル駆動型アプリ開発者ガイド](../model-driven-apps/overview.md) を参照してください。

モデル駆動型のアプリケーションの一例が、[Dynamics 365 Field Service](https://docs.microsoft.com/dynamics365/field-service/overview)、[Dynamics 365 Customer Service](https://docs.microsoft.com/dynamics365/customer-service/help-hub)[Dynamics 365 Marketing](https://docs.microsoft.com/dynamics365/marketing/help-hub) で閲覧できます。

## <a name="understand-when-to-write-code"></a>コードを記述する場合について

Common Data Service は、ユーザーがコードを記述することなく、カスタム ビジネス ロジックを構成できるように多くの機能を含んでいます。開発者が貢献する最も一般的なシナリオは、既存の機能が要件に合わせて必要な機能を提供していない場所にスペースを埋め込むことです。 しかし、Common Data Service は、開発者がコードを使用して共通の機能を拡張するために、多くのポイントを提供します。

開発者がプロジェクトに貢献するためには、コードを記述せずに何ができるかを理解することが重要です。 これらの機能についてよく理解する必要があります。 詳細: [Common Data Service とは](../../maker/common-data-service/data-platform-intro.md) 

## <a name="content-for-on-premises-deployments"></a>設置型展開の内容

Common Data Service リリースは、オンプレミス展開では使用できません。 このガイドの内容は、設置型またはインターネット経由の展開 (IFD) のオプションに関する情報は含まれていません。 これらのオプションの関連情報については、[Dynamics 365 Customer Engagement (on-premises) 開発者ガイド](/dynamics365/customer-engagement/on-premises/developer/overview) を参照してください。

> [!div class="nextstepaction"]
> [はじめに](get-started-cds-developers.md)

### <a name="see-also"></a>関連項目

[PowerApps for Developers](/powerapps/#pivot=home&panel=developer)<br/>
[モデル駆動型アプリの開発者ガイド](../model-driven-apps/overview.md)
