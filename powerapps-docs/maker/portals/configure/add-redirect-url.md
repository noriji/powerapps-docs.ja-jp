---
title: ポータルで新しい URL にリダイレクトする |MicrosoftDocs
description: リダイレクト URL を作成して、サイト内の別のページにユーザーをリダイレクトする方法について説明します。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 63cec47042cee4c29e225f33f1678261da3a01ca
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2019
ms.locfileid: "73553419"
---
# <a name="add-a-redirect-url-to-a-new-url-on-a-portal"></a>ポータルでの新しい URL へのリダイレクト URL の追加

多くの場合、サイトの深いページにリダイレクトする単純な URL を使用したり、サイトで従来の URL を使用してサイト内の新しい URL に自動的にリダイレクトしたりすることができます。 ページリダイレクトを使用すると、コンテンツ作成者は、要求されたときに、特定の web ページまたは web ファイルに対して永続的または一時的にリダイレクトされる URL を指定できます。 これらのリダイレクト Url はページコンテンツとは別に管理されるため、web 階層に直接適合する必要はありません。

## <a name="create-a-redirect"></a>リダイレクトの作成

1. [ポータル管理アプリ](configure-portal.md)を開きます。

2. **ポータル** > **Web サイト** > **リダイレクト**にアクセスします。

3. **[新規]** を選択します。

4. 以下の説明に従って、リダイレクト情報を入力します。

| 名前        | Description                                                                                                                                  |
|-------------|----------------------------------------------------------------------------------------------------------------------------------------------|
| 名前        | リダイレクトのフレンドリ名。 (何でもかまいません。 簡単に識別できるようにします)。                                                              |
| 用     | リダイレクトが関連付けられている web サイト。 (ユーザーがリダイレクトされるサイト)。                                                         |
| 受信 URL | リダイレクトされる URL の一部。 (ユーザーがリダイレクトされるページ)。                                                            |
| 状態コード | 次のいずれか: **302 (一時的なリダイレクト)** : 一時的なリダイレクトステータスを返します。 これが既定値です。                                               -   **301 (永続的リダイレクト)** : 永続的なリダイレクトステータスを返します。これは、リソースが完全に移動したことを示します。                          |
| 先         | リダイレクト先のターゲット外部 URL。 (前に指定した web サイトの外部のリンクにユーザーがリダイレクトされている場合は、これを使用します。)                            |
| Web ページ    | リダイレクト先となるターゲットの内部 web ページ。 (前に指定した web サイトの内部ページにユーザーがリダイレクトされている場合に使用します。) |
| サイトマーカー | リダイレクト先の内部サイトマーカー。                                                                                           |

4. 必須フィールドを入力し、URL、Web ページ、またはサイトマーカーのフィールドの少なくとも1つの値を指定したら、 **[保存]** を選択します。

    ![顧客調査をリダイレクトする](../media/redirect-customer-survey.png "顧客調査をリダイレクトする")  

## <a name="use-the-redirect"></a>リダイレクトを使用する

受信 URL が要求されると、ブラウザーは、一致するリダイレクトエントリのターゲット web ページの URL にリダイレクトされます。

たとえば、ターゲット web ページが [カスタマーサポートの調査] ページに設定されている場合は、次のように要求されます。

https://customerportal.contoso.com/cs-survey

ブラウザーは次の URL を要求します。

https://customerportal.contoso.com/surveys/customer-service-survey/
