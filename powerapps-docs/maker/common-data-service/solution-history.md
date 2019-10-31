---
title: ソリューションの履歴の表示 | MicrosoftDocs
description: ソリューションの履歴の表示方法に関する説明 | MicrosoftDocs
keywords: null
ms.date: 05/19/2019
ms.service: powerapps
ms.custom: null
ms.topic: article
ms.assetid: null
author: Mattp123
ms.author: matp
manager: kvivek
ms.reviewer: null
ms.suite: null
ms.tgt_pltfrm: null
caps.latest.revision: null
topic-status: Drafting
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="view-the-history-of-a-solution"></a>ソリューションの履歴の表示
モデル駆動型アプリケーション **ソリューション** 領域からソリューションの操作の詳細を表示できます。 操作は、ソリューションのインポート、エクスポート、または削除のいずれかです。 ソリューションの履歴はソリューション バージョン、ソリューション発行者、操作などの一部の情報を、操作の開始時刻と終了時刻、および操作の状態の表示されます。

> [!div class="mx-imgBorder"] 
> ![](media/solutions-history-custom-view.png "ソリューション履歴表示")

## <a name="view-solution-history"></a>ソリューション履歴表示
1. **設定**を選択して、その後**ソリューション履歴**を選択します。

     > [!div class="mx-imgBorder"] 
     > ![](media/solution-history-sitemap.png "ソリューション履歴エリア")

     > [!NOTE]
     > PowerApps 統一インターフェイスのモデル駆動型アプリから、**設定** 領域を取得するには、アプリのツールバーにある **設定** ![設定](../model-driven-apps/media/powerapps-gear.png) を選択してから、**詳細設定** を選択します。 

2. 既定では、**カスタム ソリューションの履歴** ビューが表示されます。 次のビューは、 **ソリューション履歴** 領域で利用できます。 
- **すべてのソリューション履歴**。 内部システムとカスタムソリューション両方のソリューション履歴の表示。 
- **カスタム ソリューション履歴**。 カスタム ソリューションだけのソリューション履歴が表示されます。 
- **内部ソリューション履歴**。 内部システムのみのソリューション履歴の表示。 

各ソリューションの履歴記録は読み取り専用であり、次のプロパティが含まれます: 
- **開始時間**。 操作が開始した時間。 
- **終了時刻**: 操作が終了した時間。 
- **ソリューションのバージョン**。 このソリューションのバージョンです。 
- **発行者名**。 操作が関連付けられている発行者の名前を入力します。 詳細: [ソリューション発行者の接頭辞を変更する](change-solution-publisher-prefix.md)  
- **操作**。 インポート、エクスポート、または削除のような操作です。 詳細: [ソリューションのインポート、更新およびエクスポート](import-update-export-solutions.md)
- **サブ操作**: 既存のソリューションへの新しいソリューションのインポートまたは更新などの操作の種類を示します。 
- **状態**:  **完了済み** または **未完了**など操作の状態。 
- **結果**。  **成功** または **失敗** など、操作の結果。 
-  **エラー コード**: 操作で返されるエラー コード。 エラー コード 0 は、操作が正常に終了したことを意味します。 

### <a name="view-solution-operation-error-details"></a>ソリューションの操作エラーの詳細表示 
ソリューション操作に失敗が含まれている場合は、追加のエラーの詳細を記載したページを表示することを選択できます。 

> [!div class="mx-imgBorder"] 
> ![](media/solution-history-with-failure.png " 操作エラー込のソリューション履歴")

操作エラーの根本原因の診断に役立つ可能性がある **例外メッセージ** を含む情報が含まれる詳細ページ。 ソリューション依存エラーを含む一部のエラーは、問題の診断を簡単におこなうための **ソリューション階層** へのリンクも含まれることがあります。 **活動ID** は、Microsoft カスタマ サポートに問い合わせる必要があるケースに有用です。 

> [!div class="mx-imgBorder"] 
> ![](media/solution-history-error-details.png "ソリューションの操作エラーの詳細表示")

### <a name="see-also"></a>関連項目
[ソリューションの階層の表示](solution-layers.md)  <br />
[ソリューションの概要](solutions-overview.md) 


