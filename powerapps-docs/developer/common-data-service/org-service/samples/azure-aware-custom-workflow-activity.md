---
title: Azure 対応のカスタム ワークフロー活動 (Common Data Service) | Microsoft Docs
description: このサンプルでは、現在の Common Data Service 操作からデータ コンテキストを取得して Azure Service Bus にポストします。
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
# <a name="sample-azure-aware-custom-workflow-activity"></a>サンプル: Azure 対応のユーザー定義ワークフロー活動

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-azure-aware-custom-workflow-activity -->

このサンプルは、現在の操作からデータ コンテキストを取得し、Azure Service Bus に投稿します。サンプルは [こちら](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/Azurecustomworkflowactivity) からダウンロードできます。

## <a name="requirements"></a>要件

このカスタム ワークフロー活動のサンプルを登録して実行する前に、Common Data Service と Azure の接続を構成する必要があります。 詳細: [Common Data Service と Microsoft Azure の統合を構成する](../../configure-azure-integration.md)。

コードには `Input id` 引数が必要です。 この活動をワークフローに追加する場合は、Azure サービス エンドポイントの GUID を指定する必要があります。

このユーザー定義のワークフロー活動を Common Data Service に登録する場合は、サンドボックス (部分信頼) で登録する必要があります。

## <a name="how-to-run-samples"></a>サンプルを実行する方法

1. [サンプル](https://github.com/Microsoft/PowerApps-Samples) リポジトリをダウンロードまたは複製して、ローカル コピーを用意します。
2. ワークフロー活動を登録します。

## <a name="what-this-sample-does"></a>このサンプルの概要

このサンプルは、現在の Common Data Service 操作から Azure サービス バスにデータ コンテキストをポストできるカスタム ワークフロー活動の作成方法を示しています。 データ コンテキストを投稿するには、<xref:Microsoft.Xrm.Sdk.IServiceEndpointNotificationService.Execute(Microsoft.Xrm.Sdk.EntityReference,Microsoft.Xrm.Sdk.IExecutionContext)> メソッドを使用します。
