---
title: Common Data Service のグローバル オプション設定 (入力候補) を作成、編集する | MicrosoftDocs
ms.custom: ''
ms.date: 05/26/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - PowerApps
ms.assetid: f06b8941-8dca-4601-b965-341cfb6fc3b2
caps.latest.revision: 11
ms.author: matp
manager: kvivek
author: Mattp123
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="create-and-edit-global-option-sets-overview"></a>グローバル オプション セットの概要を作成および編集 

オプション セット (候補リスト) はエンティティに含めることができるフィールドの種類です。 オプション セットは一連のオプションを定義します。 オプション セットはフォームに表示されるとき、ドロップダウン リスト コントロールを使用します。 **高度な検索**で表示する場合は、*候補リスト コントロール*を使用します。 オプション セットは、開発者には候補リストと呼ばれることがあります。  
  
オプション セットを定義して、そのオプション セット内 (ローカル) で定義されている一連オプションを使用するか、ほかのオプション セット フィールドで使用できる他のネットワーク (グローバル) で定義されているオプション セットを使用できます。 

グローバル オプション セットは、複数のフィールドに適用できる標準的な一連カテゴリがある場合に便利です。 同じ値の 2 つの異なるオプション セットを維持するのは困難です。それらのオプション セットが同期されていないと、特に 1 対多エンティティ関係のエンティティ フィールドでマッピングしているときにエラーが発生します。 詳細: [エンティティのフィールドのマッピング](map-entity-fields.md)

> [!NOTE]
> すべてのオプション セットをグローバル オプション セットとして定義した場合、グローバル オプション セットの一覧が大きくなり、管理しくくなることがあります。 オプションのセットが 1 か所でのみ使用されることがわかっている場合は、ローカル オプション セットを使用します。

グローバル オプション セットを作成または編集に使用できる 2 人のデザイナーがいます。

|デザイナー| 説明|
|--|--|
|[PowerApps ポータル](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)|簡単な優れたエクスペリエンスを提供しますが、一部の特殊な設定は使用できません。<br />詳細: [オプション セットの作成](custom-picklists.md) |
|ソリューション エクスプローラー|簡単ではありませんが、一般的な要件が少ない割に柔軟性が高くなっています。 <br />詳細: [ソリューション エクスプローラーを使用して、 Common Data Service のグローバル オプション セットを作成、編集する](create-edit-global-option-sets-solution-explorer.md) |

> [!NOTE]
> 以下を使用して、環境にグローバル オプション セットを作成することもできます。
> - グローバル オプション セットの定義を含むソリューションをインポートします。
> - 開発者はプログラムを記述して作成することもできます。 <br />詳細: [開発者ドキュメント: グローバル オプション セットのカスタマイズ](/dynamics365/customer-engagement/developer/org-service/customize-global-option-sets) を参照してください。

このトピックの情報は、使用できるデザイナーの選択に役立ちます。 

グローバル オプション セットで作業をするには、 [PowerApps ポータル](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) を使用する必要があります。ただし、以下のいずれかの要件に対処する必要がある場合を除きます。

- オプションの色の割り当て
- オプションの順序を変更
- Common Data Service の既定のソリューション以外のソリューションにグローバル オプション セットを作成する。
- 管理プロパティの設定
- 仮想エンティティに使用するプロパティの設定
- 依存関係を表示

## <a name="see-also"></a>関連項目

[オプション セットの作成](custom-picklists.md)<br />
[ソリューション エクスプローラーを使用して、 Common Data Service にグローバル オプション セットを作成、編集する](create-edit-global-option-sets-solution-explorer.md)<br />
[開発者ドキュメント: グローバル オプション セットのカスタマイズ](/dynamics365/customer-engagement/developer/org-service/customize-global-option-sets)
  

 
