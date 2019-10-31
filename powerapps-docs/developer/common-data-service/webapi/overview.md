---
title: Common Data Service Web API を使用する (Common Data Service)| Microsoft Docs
description: Common Data Service Web API は OData v4 を実装し、各種のプログラミング言語、プラットフォーム、およびデバイスで使用できる開発環境を提供します。
ms.custom: ''
ms.date: 04/22/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: 15c4039e-a3ca-4116-ba1d-3ac88cba3ae1
caps.latest.revision: 15
author: brandonsimons
ms.author: susikka
ms.reviewer: susikka
manager: shujoshi
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="use-the-common-data-service-web-api"></a>Common Data Service Web API の使用

Web API は、Common Data Service でデータとメタデータを連携するために使用できる 2 つの Web サービスのひとつです。 もう一方は[組織サービス](../org-service/overview.md)です。

Common Data Service は、各種のプログラミング言語、プラットフォーム、およびデバイスで使用できる開発作業を提供します。 Web API は、多様なデータ ソースに対して RESTful API を構築して使用するための OASIS 標準規格 OData (オープン データ プロトコル)、バージョン 4.0 を実装します。 このプロトコルの詳細については、[http://www.odata.org/](http://www.odata.org/) を参照してください。 この標準規格の詳細については、[https://www.oasis-open.org/standards#odatav4.0](https://www.oasis-open.org/standards#odatav4.0) を参照してください。 


Web API はオープン スタンダードに基づいて構築されるので、特定の開発者環境用のアセンブリを提供しません。 特定の操作に対する HTTP 要求を作成でき、サードパーティのライブラリを使用して必要な任意の言語またはプラットフォームに対応するクラスを生成することができます。 OData バージョン 4.0 をサポートするライブラリ一覧については、[http://www.odata.org/libraries/](http://www.odata.org/libraries/) を参照してください。  

## <a name="web-api-and-the-organization-service"></a>Web API および組織サービス

組織サービスがプラットフォームを定義するものであると認識することは有益です。 Web API は RESTful プログラミング エクスペリエンスを提供しますが、最終的にはすべてのデータ操作は、基盤となる組織サービスを実行します。 組織サービスのサポートされる操作はメッセージとして定義されます。 各メッセージには名前があります。 これらの名前は、どの登録された拡張を開始するかを評価するため、イベント フレームワークで使用されるイベントに結び付けられています。 詳細: [イベント フレームワーク](../event-framework.md)

Web API により組織サービスと同じ操作が可能になりますが、RESTful 形式で提供されます。 OData v4 は*関数*または*アクション*により、名前付き操作を提供します。 組織サービスで使用可能なメッセージの多くは、対応する名前付き関数またはアクションとして公開されています。 CRUD 操作に対応するこれらのメッセージは、RESTful サービスとして GET、POST、PATCH、および DELETE HTTP メソッドを使用した実装があるため、Web API では使用できませんが、プラットフォーム内では、対応する操作が .NET Framework アセンブリを使用して実行される場合、*取得*、 *作成*、*更新*、および*削除*メッセージはそのまま呼び出されます。

  
### <a name="related-sections"></a>関連セクション

[コードを使用したデータに関する作業](../work-with-data-cds.md)<br />
[OData - REST への最善の方法](http://www.odata.org/)<br />
[OData バージョン 4.0 パート 1: Protocol Plus Errata 02](http://docs.oasis-open.org/odata/odata/v4.0/odata-v4.0-part1-protocol.html)<br />
[OData バージョン 4.0 パート 2: URL Conventions Plus Errata 02](http://docs.oasis-open.org/odata/odata/v4.0/odata-v4.0-part2-url-conventions.html)<br />
[OData バージョン 4.0 パート 3: Common Schema Definition Language (CSDL) Plus Errata 02](http://docs.oasis-open.org/odata/odata/v4.0/odata-v4.0-part3-csdl.html)
