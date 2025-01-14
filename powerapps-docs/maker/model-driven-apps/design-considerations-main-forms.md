---
title: PowerApps でのモデル駆動型アプリのメイン フォームに関する設計上の考慮事項 | MicrosoftDocs
description: メイン フォームの設計方法を説明します
ms.custom: ''
ms.date: 06/27/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
author: Mattp123
ms.assetid: a83872f4-9e36-413b-8561-41a1e5ffe5dd
caps.latest.revision: 17
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="design-considerations-for-model-driven-app-main-forms"></a>モデル駆動型アプリのメイン フォームの設計に関する考慮事項

メイン フォームは、ユーザーデータを表示したりデータとやり取りする、主たるユーザー インターフェイスです。 メイン フォームは、広い範囲のオプションを提供し、モデル駆動型アプリが使用できます。例外は Dynamics 365 for phones です。  
  
 メイン フォームの主要な設計の目的の 1 つは、1 回設計し、それをすべての場所に導入することです。 モデル駆動型アプリ用に設計した同じメイン フォームが、 Dynamics 365 for Outlook とタブレット PC 用 Dynamics 365でも使用されます。 この方法の利点は、複数のフォームに変更を統合する必要がないことです。 ただし、これらのフォームの設計で考慮する必要のある、いくつか重要な要因があります。  
  
<a name="BKMK_CustomFormsForGroups"></a>   

## <a name="custom-forms-for-different-groups"></a>さまざまなグループのユーザー定義フォーム  
 複数のメイン フォームを作成し、各フォームに異なるセキュリティ ロールを割り当てることができるため、組織内のさまざまなグループを、それぞれのグループのアプリケーションの使い方を最適化するフォームを使用して、表現することができます。 各グループが選択するフォームが異なるように、各グループに異なるオプションを与えることもできます。 詳細情報: [フォームへのアクセスを制御する](control-access-forms.md)  
  
 管理者と意思決定者は、重要なデータのポイントをすぐ参照できるように最適化されたフォームをたぶん必要としているでしょう。 彼らは一覧よりもグラフに表示されることを好み、大量のデータ入力はできないかもしれません。  
  
 顧客と直接対話する者は、最も頻繁に実行するタスクに合ったフォームを必要とするかもしれません。 彼らは最も効率のよいデータの入力を可能にするフォームを必要としているかもしれません。  
  
 組織内の人が何を要求し、必要としているかを見つけ出す必要があります。 しばしば、これは、入力を収集し、さまざまなことを試し、ユーザーが使用できるフォームを作成する、繰り返しのプロセスとなります。 使用できるさまざまなツールがあり、フォーム内ですべてを行う必要がないことに留意してください。 業務ルール、ワークフロー プロセス、ダイアログ、および業務プロセス フローを、組織に有効なソリューションを提供するフォームと組み合わせて使用します。  
  
 フォームの管理に費やされる時間とこれとのバランスをとる必要があります。 フォームの作成と編集は比較に簡単ですが、より詳細なフォームを作成するときは、さらなるフォームの管理が必要となります。  
  
<a name="BKMK_PresentationDifferences"></a>   
## <a name="presentation-differences"></a>表現の違い  
 複数のフォームのそれぞれの表現を管理する必要はありませんが、表現の違いがどのようにメイン フォームで説明できるかを検討する必要があります。 [メイン フォームの表示](main-form-presentations.md) では、メイン フォームで表現できる様々なさまざまな方法を説明しています。 考慮する内容は主に次のとおりです。  
  
- Dynamics 365 for tablets は、イメージ、HTML、または Silverlight Web リソースのフォームへの追加をサポートしていません。  
  
-   Dynamics 365 for tablets フォームのレイアウトは、メイン フォームに基づいて自動生成されます。 Dynamics 365 for tablets フォームに特殊なフォーム エディターはありません。 フォームの表現が両方のクライアントに対しても有効であることを確認する必要があります。  
  
-   DOM 要素とやり取りするサポートされていないスクリプトが Web アプリケーションに見つかった場合、同じ DOM 要素は使用できないので、そのスクリプトは Dynamics 365 for tablets のフォームでは機能しません。  
  
- Dynamics 365 for Outlook 閲覧ウィンドウのフォームではスクリプトは使用できません。 フォーム要素の表示は既定の設定によって決まり、スクリプトを使用して実行時に変更することはできません。  
  
<a name="BKMK_FormPerformance"></a>   
## <a name="form-performance"></a>フォームのパフォーマンス  
 読み込みが遅く、すばやく応答しないフォームは、生産性とユーザーのアプリの採用に影響を与えます。 [フォームのパフォーマンスの最適化](optimize-form-performance.md) には、カスタマイズがフォームのパフォーマンスに悪影響しないように、フォームの設計時に考慮する必要のある多くの推奨事項があります。  
  
### <a name="next-steps"></a>次のステップ 
 [フォームの作成および設計](create-design-forms.md)    
 [簡易作成フォームの作成および編集](create-edit-quick-create-forms.md)   

 
