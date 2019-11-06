---
title: ポータルでコンテンツスニペットを使用してコンテンツをカスタマイズする |MicrosoftDocs
description: コンテンツスニペットを使用してコンテンツをカスタマイズする方法について説明します。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 362bbe27850e8e72d7af4b2fb32b42796334d579
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2019
ms.locfileid: "73552821"
---
# <a name="customize-content-by-using-content-snippets"></a>コンテンツスニペットを使用してコンテンツをカスタマイズする

コンテンツスニペットは、編集可能なコンテンツの小さなまとまりであり、ページテンプレートに開発者が配置できます。これにより、カスタマイズ可能なコンテンツを使用して、ページのレイアウトの任意の部分を簡単に設定できるようになります。 Web 向けポータル上でスニペットのコンテンツをレンダリングするスニペットコントロールは、開発者によってページテンプレートに配置されます。

## <a name="edit-snippets"></a>スニペットの編集

スニペットは、ポータル管理アプリを使用して編集できます。 スニペットの主な威力は、(ページのメインコピー以外の) コンテンツを抽象化して個別に編集できることです。これにより、実質的には、サイトのすべての静的コンテンツを完全にコンテンツを管理および編集できるようになります。

1. [ポータル管理アプリ](configure-portal.md)を開きます。

2.  **ポータル** > **コンテンツスニペット**にアクセスします。

3.  新しいスニペットを作成するには、[**新規**作成] を選択します。

4.  既存のスニペットを編集するには、グリッド内の既存の**コンテンツスニペット**を選択します。

次のフィールドの値を入力します。

| 名前    | Description                                                                                                   |
|---------|---------------------------------------------------------------------------------------------------------------|
| 名前    | 開発者はこの名前を使用して、スニペットの値をポータルのコード内のページテンプレートに配置できます。 |
| 用 | スニペットに関連付けられている web サイト。                                                              |
| Value   | ポータルに表示されるスニペットのコンテンツ。 これには、プレーンテキストまたは HTML マークアップを含めることができます。         |


