---
title: Download、Launch、および Param 関数 | Microsoft Docs
description: キャンバスアプリの Download、Launch、および Param 関数の構文と例を含む参照情報
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 11/07/2015
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 15bef0fc30c2efe90647d9f190cf8917de11a109
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2019
ms.locfileid: "73536935"
---
# <a name="download-launch-and-param-functions-in-canvas-apps"></a>キャンバスアプリでの Download、Launch、および Param 関数
パラメーターを使用して、Web ページまたはアプリをダウンロードまたは起動します。  

## <a name="description"></a>Description
**Download** 関数は、Web からローカル デバイスにファイルをダウンロードします。 ユーザーは、ファイルを保存する場所の入力を求められます。  **Download** は、ファイルが格納されているローカルの場所を文字列として返します。  

**Launch** 関数は、Web ページまたはアプリを起動します。  この関数では、必要に応じて、アプリにパラメーターを渡すことができます。

Internet Explorer と Microsoft Edge では、**起動**機能によって web サイトまたはアプリが開かれるのは、そのセキュリティ設定が、その機能を含むアプリの設定と同じかそれよりも大きい場合のみです。 たとえば、**信頼済みサイト**のセキュリティゾーンで実行されるアプリに**Launch**関数を追加する場合、その機能を開く web サイトまたはアプリが、**信頼済みサイト**または**ローカルイントラネット**ゾーンにあることを確認します ( **制限付きサイト**)。 詳細情報: [Internet Explorer 11 のセキュリティとプライバシーの設定を変更](https://support.microsoft.com/help/17479/windows-internet-explorer-11-change-security-privacy-settings)します。  

**Param** 関数は、アプリに渡されたパラメーターをアプリの起動時に取得します。 名前付きパラメーターが渡されていなかった場合、**Param** は "*空白*" を返します。

## <a name="syntax"></a>構文
**Download**( *Address* )

* *Address* - 必須。  ダウンロードする Web リソースのアドレス。

**Launch**( *Address* [, *ParameterName1*, *ParameterValue1*, ... ] )

* *Address* - 必須。  起動する Web ページのアドレスまたはアプリの ID。
* *ParameterName(s)* - 省略可能。  パラメーター名。
* *ParameterValue(s)* - 省略可能。  アプリまたは Web ページに渡す、対応するパラメーター値。

**Param**( *ParameterName* )

* *ParameterName* - 必須。  アプリに渡されるパラメーターの名前。

