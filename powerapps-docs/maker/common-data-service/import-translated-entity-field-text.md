---
title: PowerApps を使って翻訳済みエンティティおよびフィールド テキストをインポートする | MicrosoftDocs
description: 翻訳済みエンティティおよびフィールド テキストのインポート方法について説明する
ms.custom: ''
ms.date: 06/19/2018
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
ms.assetid: 3d77d149-819b-45e6-8e70-1fbe54d5c153
caps.latest.revision: 19
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="import-translated-entity-and-field-text-back-into-an-app"></a>翻訳済みエンティティおよびフィールド テキストをアプリにインポートし直す

フィールドのラベルやドロップダウン リストの値などのエンティティまたはフィールドのテキストをカスタマイズした場合、自分の環境とは異なる基本言語バージョンを使用している組織内のユーザーに対して、カスタマイズしたテキストをユーザーごとの言語で提供することができます。 そのためには、組織で使用する言語に翻訳できるように、すべてのカスタマイズのテキスト文字列をエクスポートします。  
  
 翻訳後、ユーザーが変更を利用できるようにするには、環境に翻訳済みのテキスト文字列をインポートする必要があります。  
  
> [!IMPORTANT]
> - インポートするファイルは、ルートに CrmTranslations.xml と [Content_Types].xml ファイルを含む圧縮ファイルである必要があります。  
> - 500文字を超える長さの翻訳済みテキストをインポートすることはできません。 翻訳ファイル内の任意のアイテムが 500 文字を超える長さの場合、インポート プロセスは失敗します。 インポート プロセスが失敗した場合は、失敗の原因となったファイル中の行を確認し、文字数を減らしてから再度インポートを試みてください。 翻訳済みのテキストのインポートが終了したら、カスタマイズを再公開する必要があることにも注意してください。  
  
1. [ソリューション エクスプローラー](../model-driven-apps/advanced-navigation.md#solution-explorer)を開きます。  
  
2. ソリューション エクスプローラーの操作ツール バーで、**翻訳のインポート**を選択します。  
3.  **翻訳されたテキストのインポート**ダイアログ ボックスで、翻訳済みのテキストを含むファイルを指定してから、**インポート**を選択します。  
  
4.  インポートが完了したら、**閉じる**を選択します。  
  
> [!NOTE]
>  カスタマイズを公開すると、標準システム操作を干渉する可能性があります。 ユーザーへの影響が最小限に留まるように公開をスケジュールすることを推奨します。  

## <a name="community-tools"></a>コミュニティ ツール

[Easy Translator](https://www.xrmtoolbox.com/plugins/MsCrmTools.Translator/) は PowerApps 向けに XrmToolbox コミュニティが開発したツールです。 Easy Translator を使用して、翻訳をコンテキスト情報と共にエクスポートおよびインポートします。 

> [!NOTE]
> このコミュニティ ツールは Microsoft ではサポートされていません。 このツールに関するご質問は、その発行元にお問い合わせください。 詳細: [XrmToolBox](https://www.xrmtoolbox.com)。

## <a name="next-steps"></a>次のステップ  
 [カスタマイズされたエンティティとフィールド テキストの翻訳用のエクスポート](export-customized-entity-field-text-translation.md)
