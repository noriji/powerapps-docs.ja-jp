---
title: ミーティング画面のテンプレート |Microsoft Docs
description: キャンバスアプリのミーティング画面テンプレートがどのように機能するかを理解し、独自のユースケースに合わせて画面を拡張する
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 12/30/2018
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 2b300b0d90803ae08aaf262dde5642f4d448c05f
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2019
ms.locfileid: "73541433"
---
# <a name="overview-of-the-meeting-screen-template-for-canvas-apps"></a>キャンバスアプリのミーティング画面テンプレートの概要

キャンバスアプリで、ユーザーが Office 365 Outlook アカウントから会議出席依頼を作成して送信できるようにする会議画面を追加します。 ユーザーは、組織内の出席者を検索したり、外部の電子メールアドレスを追加したりできます。 テナントに Outlook に会議室が組み込まれている場合は、ユーザーが場所を選択することもできます。

また、[電子メール](email-screen-overview.md) [、組織内のユーザー、](people-screen-overview.md)ユーザーの[予定表](calendar-screen-overview.md)など、Office 365 のさまざまなデータを表示するテンプレートベースの他の画面を追加することもできます。

この概要では、画面の高レベルの機能について説明します。

この画面の既定の機能の詳細については、[ミーティング画面のリファレンス](meeting-screen-reference.md)を参照してください。

## <a name="prerequisite"></a>前提条件

[PowerApps でアプリを作成](../data-platform-create-app-scratch.md)するときに、画面やその他のコントロールを追加および構成する方法について理解します。

## <a name="default-functionality"></a>既定の機能

テンプレートからミーティング画面を追加するには、次のようにします。

1. PowerApps に[サインイン](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)し、PowerApps Studio でアプリを作成するか、既存のアプリを開きます。

    このトピックでは phone アプリについて説明しますが、同じ概念がタブレットアプリにも当てはまります。

1. リボンの **[ホーム]** タブで、[**新しい画面** > **会議**] を選択します。

  入力すると、ミーティング画面の両方のタブが次のようになります。

  ![ミーティング画面、両方のタブ](media/meeting-screen/meeting-screen-full-both.png)

役に立つ注意事項がいくつかあります。

* 会議画面では、アプリユーザーは Outlook で会議を作成できます。
  ユーザーは、出席者を検索して追加したり、必要に応じて会議室を会議に追加したりすることができます。
* 組織内のユーザーを検索するには、[出席者] の下のテキスト入力ボックスで、名前の入力を開始します。
* ユーザーを検索すると、上位15件の結果のみが返されます。
* 組織外の出席者の電子メールアドレスを追加するには、完全な有効な電子メールアドレスを入力し、電子メールアドレスの右側に表示される [+] アイコンを選択します。
* 会議を作成するには、少なくとも1人を出席者として追加し、件名を入力して、 **[スケジュール]** タブで会議の時刻を選択する必要があります。
* 会議出席依頼を送信すると、その会議のすべての情報がクリアされます。
* 送信アイコン (右上隅) の**Onselect**ステートメントには、次の式が含まれています。
    ```powerapps-dot
    Set( _myCalendarName, 
        LookUp( 'Office365'.CalendarGetTables().value, DisplayName = "Calendar" ).Name 
    );
    ```
* "Calendar" はほとんどの Office ユーザーの予定表の既定の表示名ですが、組織によって異なる場合があります。 その場合は、"Calendar" を組織の適切な用語に変更できます。
* 過去に発生した会議のスケジュールを設定しようとした場合、または会議に20人を超える人を追加しようとした場合に、エラーが表示されます。

## <a name="next-steps"></a>次の手順

* [この画面のリファレンスドキュメントを表示](./meeting-screen-reference.md)します。
* [Office 365 Outlook コネクタの詳細については、こちらを参照して](../connections/connection-office365-outlook.md)ください。
* [Office 365 Users コネクタの詳細については、こちらを参照して](../connections/connection-office365-users.md)ください。
