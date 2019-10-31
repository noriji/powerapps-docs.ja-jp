---
title: Common Data Service アプリ作成の実践 | MicrosoftDocs
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
ms.assetid: e9810433-224b-4bde-851a-e581cf5fb8a4
caps.latest.revision: 21
author: Mattp123
ms.author: matp
manager: kvivek
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---

# <a name="common-data-service-supported-and-unsupported-app-building-practices"></a>Common Data Service のサポートしているアプリとサポートしていないアプリの作成の実践

<!--
The way your organization works is unique. Some organizations have well-defined business processes that they apply using PowerApps apps. Others aren’t happy with their current business processes and use PowerApps to apply new data and processes to their business. Whatever situation you find yourself in, you’ll find a lot of customization capabilities in PowerApps so that it can work for your organization.  
  
 Of course you’re eager to get started, but please take a few minutes to read the content in this section. This will introduce you to important terms, give you some background about why things are done a certain way, and help you avoid potential problems in the future.  

## What is metadata and why should you care?  
 In the past, you may have customized business applications by editing the source code. This created complications because each organization had unique changes and it was very difficult, or extremely expensive, to upgrade. Then application developers started exposing application programming interfaces (APIs) so that other developers could interact with the application and add their own logic without touching the source code. This was moderately better because it means developers can extend the application without changing it. But it still requires a developer to write code.  -->
  
 現代のビジネス アプリケーションは、メタデータ駆動のアーキテクチャを使用しているため、コードを記述せずにアプリケーションを作成できます。 メタデータは "データについてのデータ" を意味しており、 Common Data Service に格納されているデータの構造を定義します。 このメタデータによって、アプリケーションはデータ構造への変化を理解し、これによりアプリケーションはデータ構造変更に適用できるようになります。 メタデータは既知のため、メタデータに関連付けられている追加機能を含むことができます。  

エンティティ、ビュー、フィールド、グラフおよびダッシュボードなどの Common Data Service コンポーネントを変更して、思い通りに動作するアプリを構築することを、 *カスタマイズ* と呼びます。  
 
PowerApps のツールを使用してアプリを構築しカスタマイズすると、メタデータに依存する機能で使用されるメタデータやデータが追加または更新されます。 アプリの作成に使用するデータの種類は既知なので、このデータを考慮に入れてアプリを中断することなく新機能を Common Data Service 環境 に追加できます。 <!-- This way you should always be able to apply an update rollup or upgrade to the latest version and enjoy the best new features.  -->

<!--  
> **Customize or Configure?**   
> Most people say they want to customize the application, so we use the word “customize” to describe changing the system to make it work the way you want. Some people prefer to use the word “configure” because it suggests that no code was required to make changes. Call it whatever you like, we just want to make it clear that you don’t need to be a developer to customize or create PowerApps apps.  -->
  
PowerApps アプリを構築してカスタマイズするために、開発者である必要はありません。 しかし、 PowerApps は、開発者がコードを記述できるように一連の Web サービスと API を提供します。 コードがサポートされているメソッドを使用して記述されると、 Common Data Service 環境をアップグレードすると、そのコードは引き続き機能します。  
  
<a name="BKMK_SupportedCust"></a>   
## <a name="what-kinds-of-customizations-are-supported"></a>どのようなカスタマイズがサポートされますか。  
 使用可能な PowerApps ツールを使用して、ほとんどのアプリの構築とカスタマイズを行うことができます。 カスタマイズ ツールがニーズに合わない場合、サード パーティが提供するソリューションをインストールするか、開発者を雇ってアプリをコーディングすることができます。 コードを必要とするソリューションに投資する必要がある場合は、そのコードはサポートされている API のみを使用して記述されていることを確認してください。 これは、アプリと取得したソリューションの両方に対する投資を保護する助けになります。  
  
 PowerApps アプリを拡張する開発者は、 [こちら](/powerapps/developer/common-data-service/best-practices/) に記載されているルールとベスト プラクティスに従う責任があります。 Microsoft は、SDK に文書化されている API とプラクティスのみをサポートします。 問題の解決方法がインターネットで見つかったとしても、SDK で文書化されている API を活用していない場合、その方法は Microsoft によってサポートされません。 開発者に変更を適用してもらう前に、サポートされているメソッドを使用していることを確認してください。  
  
 開発者が SDK に記載されている API とベスト プラクティスを使用する場合、Microsoft は Common Data Service への変更点が既存のカスタマイズを壊す可能性があるかどうかをテストいたします。 目的は、 Common Data Service の新しいバージョンまたは更新がリリースされても、サポートされているメソッドを使用して記述したコード カスタマイズが引き続き機能することです。 開発者が毎回コードを変更しなくても、改良された機能を持つ新しいバージョンにアップグレードできるため、大変便利です。  
  
 Common Data Service の新しいバージョンの変更がサポートされているカスタマイズを壊すことが検出された場合は、影響の内容とコード修正のためのコードの変更方法を文書化します。  
  
<a name="BKMK_Unsupported"></a>   
## <a name="what-kinds-of-customizations-arent-supported"></a>サポートされないカスタマイズ  
 特定の API およびプログラミングのプラクティスが Microsoft によってサポートされていないからと言って、機能しないというわけではありません。 <!--  “Unsupported by Microsoft” means exactly what it says: you can’t get support about these APIs or programming practices from Microsoft. We don’t test them and we don’t know if something we change will break them. We can’t predict what will happen if someone changes code in our application.  -->  サポートされていない API およびプログラミング プラクティスを使用する開発者が、コードをサポートする責任を負います。 機能するかどうか開発者がコードをテストする必要があります。  
  
 Common Data Service 環境でサポートされていないカスタマイズを使用することを選択した場合、 Microsoft テクニカル サポートに問い合わせる前に、実施したことを記載し、そのカスタマイズの削除方法を確認しておく必要があります。 サポートされていないカスタマイズでヘルプを必要とする場合は、カスタマイズを準備または開発した開発者に問い合わせてください。  
  
<a name="BKMK_CommonUnsupportedCustomizations"></a>   
### <a name="common-unsupported-customization-practices"></a>サポートされていないカスタマイズの共通のプラクティス  
 サポートされないカスタマイズの一般的なプラクティスの一覧を次に示します。 これは完全な一覧ではありません。 詳細: [Dynamics 365 でサポートされている拡張機能。サポートされていないカスタマイズ](https://docs.microsoft.com/dynamics365/customer-engagement/developer/supported-extensions#Unsupported)。 
 
**JavaScript を使用して Web アプリケーションのドキュメント オブジェクト モデル (DOM) の要素と対話する**  
 アプリケーションの任意の場所で使用される JavaScript ライブラリは、文書化されている API とのみ対話します。 JavaScript の開発者がアプリケーションで作業する際、特定名を使用し DOM 要素に頻繁にアクセスします。 PowerApps アプリは Web アプリケーションであるため、これらのテクノロジは機能しますが、参照する要素名がいつでも変更されてしまうため、アップグレード中に破壊する可能性があります。 Microsoft には、アプリケーションで必要な変更を加える権利があります。つまり、ページの構成方法が変わることを意味します。 ページの現在の構造に基づく変更を追加する場合、アプリケーションのアップグレードのたびにこれらのスクリプトのユーザー定義コードをテストおよび時には変更することに投資する必要があります。  
  
 jQuery は JavaScript の開発者によって使用される非常に一般的なライブラリです。 jQuery を使用する利点の多くは、開発者が DOM 要素を作成してアクセスするための能力を簡素化することです。これは Common Data Service アプリケーション ページではサポートしていません。 開発者が HTML Web リソースを使用するカスタム ユーザー インターフェイスを作成するときは jQuery が推奨されますが、PowerApps アプリケーション ページ内では、サポートされる API は jQuery の使用を必要としません。  
  
 **JavaScript を使用する文書化されていない内部オブジェクトまたはメソッドを使用する**  
Common Data Service は、ページ内で多数の JavaScript オブジェクトを使用します。 JavaScript の開発者はページをデバッグしてそれらのオブジェクトを検出し、これらのオブジェクトにアクセスし再利用できます。 Microsoft は、削除またはメソッド名の変更など、これらのオブジェクトに対する必要な変更を加える権利を有します。 スクリプトがそれらのオブジェクトを参照している場合は、オブジェクトが見つからない場合、スクリプトは停止します。  <a name="BKMK_Metadata"></a>   
 
<a name="BKMK_CombineCustomizations"></a>   
## <a name="combine-customization-capabilities"></a>カスタマイズ機能の結合  
 これらのセクションにあるトピックは、個々のカスタマイズ機能をかなり詳細に説明します。 しかし、自身の業務要件を満たすためのソリューションは、機能のいずれかを、1 つ以上の他の機能と共に頻繁に使用することを心に留めておくことが重要です。  
  
<a name="BKMK_ChooseTheRightCustomization"></a>   
### <a name="choose-the-right-customization-capability-for-the-job"></a>ジョブに適切なカスタマイズ機能の選択  
 PowerApps で使用可能なすべてのカスタマイズ機能では、これらの機能の 1 つを理解すること、またすべての問題を解決するためにそれらの機能を使用することが容易です。 解決を望んでいる業務上の問題を評価するとき、達成する最終結果について検討してから、それにどのような方法で到達するかを逆算します。  
 
<a name="BKMK_changesinperformance"></a>   
## <a name="changes-that-affect-common-data-service-environment-performance"></a>Common Data Service 環境パフォーマンスに影響する変更  
 メタデータの変更を伴うソリューションのインポートとカスタマイズの適用は、 Common Data Service 環境パフォーマンスに影響を与える可能性があります。 正常なシステム操作を妨げる可能性のあるアクションには、以下のものが含まれます。  
  
-   エンティティの追加、削除、または変更、代替キー、属性、あるいは関連付け。   
-   ソリューションのインポート
  
-   カスタマイズを公開しています 
  
運用システムにこれらの変更を加える場合は、ユーザーへの影響が最小限に留まるように変更の操作をスケジューリングすることを推奨します。   
  
  
## <a name="next-steps"></a>次の手順  
[PowerApps におけるモデル駆動型アプリとは?](../../maker/model-driven-apps/model-driven-app-overview.md)

