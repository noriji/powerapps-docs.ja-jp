---
title: Visual Studio および.NET Framework (Common Data Service) | Microsoft Docs
description: マネージド コードの開発ツールと要件について説明します。
ms.custom: ''
ms.date: 07/03/2019
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
# <a name="visual-studio-and-the-net-framework"></a>Visual Studio および .NET Framework

Common Data Service の .NET SDK アセンブリは、.NET Framework 4.6.2 に構築されています。 

Visual Studio を使用して、.NET Framework 4.6.2 以降を使用したマネージ コード アプリケーションを構築できます。 

プラグインおよびカスタム ワークフロー アセンブリは、.NET Framework 4.6.2を使用する必要があります。 エラーが発生後に 4.6.2 以降に導入された機能を使用する場合、アセンブリが後のバージョンを構築して使用するため一般的には機能します。

> [!IMPORTANT]
> ユーザー定義のクライアント アプリケーションを作成するには、Microsoft .NET フレームワーク 4.6.2 またはそれ以降を使用します。
> Transport Level Security (TLS) 1.2 またはそれより優れたセキュリティを使用するアプリのみが Common Data Service への接続を許可されます。 TLS 1.2 は .NET Framework 4.5.2 で使用される既定のプロトコルではありませんが、.NET Framework 4.6.2 内にあります。 
> 
> 詳細: <https://<blogs.msdn.microsoft.com/crm/2017/09/28/updates-coming-to-dynamics-365-customer-engagement-connection-security/>
> 
> [!TIP]
> 開発用コンピューターに .NET Framework 4.6.2 をインストールする場合、ランタイムだけでなく開発者パックのインストールを実行してください。 これにより、4.6.2 フレームワークを、Visual Studio の**新しいプロジェクト**ダイアログ ボックスおよびプロジェクトのプロパティのターゲット フレームワーク ドロップダウン メニューで選択できるようになります。  

開発に Visual Studio コミュニティ エディションを使用できます。 ただし、エクスプレス版では拡張機能の使用に対応していないため、そのバージョンの Visual Studioに実用的な拡張機能をインストールすることはできません。

詳細: [サポートされる .NET Framework のバージョン](/dynamics365/customer-engagement/developer/supported-extensions#SupportNET)

サポートされる開発およびサポートされていない開発に関する声明の全文については、「[Dynamics 365 でサポートされる拡張](/dynamics365/customer-engagement/developer/supported-extensions#SupportNET)」を参照してください。

## <a name="see-also"></a>関連項目

 [開発者ツール](/dynamics365/customer-engagement/developer/developer-tools)
