---
title: Common Data Service 組織サービスの使用 (Common Data Service) | Microsoft Docs
description: アプリ用 Common Data Service 組織サービスを使用したデータおよびメタデータの操作方法を説明します。
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: brandonsimons
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---

# <a name="use-the-common-data-service-organization-service"></a>Common Data Service 組織サービスの使用

組織サービスは、Common Data Service でデータとメタデータを連携するために使用できる 2 つの Web サービスのひとつです。 もう一方は [Web API](../webapi/overview.md)です。

組織サービスは .NET Framework での使用に最適化されており、[Microsoft.CrmSdk.CoreAssemblies](https://www.nuget.org/packages/Microsoft.CrmSdk.CoreAssemblies/) NuGet パッケージの SDK アセンブリがこのサービスを使用するデータおよびメタデータの処理に必要な <xref:Microsoft.Xrm.Sdk.IOrganizationService> インターフェイス用のクラスを提供します。 

プラグインおよびワークフロー拡張などの拡張機能のいくつかは .NET Framework およびこれらのアセンブリで定義されたクラスに依存するため、組織サービスはこれらのメソッドを使用して Common Data Service を拡張する唯一の手段です。

## <a name="organization-service-assemblies"></a>組織サービスのアセンブリ

組織サービスがプラットフォームを定義するものであると認識することは有益です。 組織サービスのサポートされる操作はメッセージとして定義されます。 各メッセージには名前があります。 これらのメッセージは、イベント フレームワークにより送信されるイベントに対応しています。 詳細: [イベント フレームワーク](../event-framework.md)

組織サービス用の .NET アセンブリでは、SOAP エンドポイントを現在使用しています。 アセンブリは <xref:Microsoft.Xrm.Sdk.IOrganizationService> インターフェイスに基づいて基盤となるプラットフォーム サービスを厳密に模倣するよう設計されています。 ただし、同じコンポーネントではありませんので、混同しないでください。 

組織サービス用 SOAP エンドポイントは 2011 年に導入されましたが、廃止されることを発表しました。 これは、削除されるまで引き続き機能し、サポートされることを意味します。 また、.NET SDK アセンブリを更新し、SOAP エンドポイントが削除された後も機能し続けるようにすることも発表しました。 これは、SOAP エンドポイントが削除される前に更新された SDK アセンブリが使用可能になり、開発者は、将来のいずれかの時点で新しいアセンブリを使用するためにコードを更新する必要があることを意味します。

## <a name="using-the-organization-service-without-assemblies"></a>アセンブリなしの組織サービスの使用

たとえば、サービスにより公開された WSDL を使用して Web サービス プロキシを作成するなど、開発者が .NET SDK アセンブリを使用せずに組織サービスの SOAP エンドポイントを使用することは可能ですが、Web API の RESTful の性質により、優れた代替策になります。
