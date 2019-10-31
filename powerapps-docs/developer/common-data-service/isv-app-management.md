---
title: Power Platform ISV Studio の概要 | Microsoft Docs
description: ISV Studio ポータルを使用したアプリケーションの管理とサポートについて説明します。
services: ''
suite: powerapps
documentationcenter: na
author: phecke
manager: kvivek
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.reviewer: pehecke
ms.workload: na
ms.date: 07/11/2019
ms.author: prkoduku
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---

# <a name="introduction-to-isv-studio-for-the-power-platform"></a>Power Platform ISV Studio の概要

[!INCLUDE [cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

ISV Studioは、独立系ソフトウェアベンダー(ISV)がアプリケーションを監視および管理するにあたって信頼のおける Power Platform になるように設計されています。 ISV Studioは、ISVが顧客に配布しているすべてのアプリケーションの統合されたクロステナント ビューを提供します。

> [!IMPORTANT]
>
> - ISV Studio はプレビューの機能です。
> - [!INCLUDE[cc_preview_features_definition](../../includes/cc-preview-features-definition.md)]

ISV Studioは、 [AppSource](https://appsource.microsoft.com/)で公開、導入された Common Data Service 上に構築されたアプリケーションに対応しています。 AppSourceを介して展開されていないサイドロードされたソリューションでは、テレメトリは提供されません。

このアプリケーションは現在、PowerApps などの Common Data Service、ならびに Dynamics 365 for Sales、Marketing、Service、および Talent で利用可能です。

エンド ユーザーが AppSource からアプリケーションをインストールすると、連絡先、使用率、トランザクション情報がアプリケーションプロバイダーと共有される可能性があることに対する確認を求める、同意ダイアログが表示されます。 この情報は、プロバイダが課金やその他のトランザクション処理をサポートし、ISVがISV Studioから遠隔的にデータを計測して学習する目的で使用されます。

顧客は、データをプロバイダと共有しない要求をすることができます。その場合、Microsoft は ISV Studio内の特定のテナントのすべてのデータを削除します。

ISV Studio の共有プレビューにアクセスするには、ブラウザで [https://aka.ms/ISVStudio](https://aka.ms/ISVStudio/)に移動します

## <a name="pre-requisites"></a>前提条件

1. ISVは、 [AppSource](https://appsource.microsoft.com/)で公開された1つまたは複数のサポート対象アプリケーションを持つ、Microsoft登録パートナーの組織 [ISV] と関連付けられている必要があります。 サポートされているアプリには、PowerApps と Dynamics 365 Sales や Dynamics 365 Customer Service などの Dynamics 365 のモデル駆動型アプリがあります。

2. ISVは [Azure Active Directory](https://azure.microsoft.com/services/active-directory/) (AAD) アカウントを持っている必要があり、そのアカウントは ISV の クラウド パートナー ポータル(CPP) で、アプリのコントリビューターまたはオーナーとして設定されている必要があります。

ISV Studio にアクセスできるユーザを追加する場合は、CPPにて アプリ コントリビュータとして追加することができます。  手順については、[クラウド パートナー ポータルでのユーザー管理](https://docs.microsoft.com/en-us/azure/marketplace/cloud-partner-portal-orig/cloud-partner-portal-manage-users)で確認することができます。

ISV Studioの機能については、以下の「アプリ」と「テナント」ページのトピックを参照してください。

フィードバックや質問については [ISVFeedback@microsoft.com](mailto:ISVFeedback@microsoft.com) に電子メールを送信してください。 お客様からのフィードバックは、今後の運用体制を形成する上で重要となります。

## <a name="in-this-section"></a>このセクションでは、以下について説明します。

[ホーム ページ](isv-app-management-homepage.md)  
[アプリ ページ](isv-app-management-apppage.md)  
[テナント ページ](isv-app-management-tenantpage.md)

### <a name="see-also"></a>関連項目

[ソリューションの概要](introduction-solutions.md)  
[AppSourceでアプリを公開する](publish-app-appsource.md)
