---
title: プッシュ通知を送信する | Microsoft Docs
description: PowerApps でネイティブのプッシュ通知をアプリに送信する方法を説明します。
author: kavishi
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 08/08/2017
ms.author: kaagar
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 4a72fc689fa9b4d7d84f554745e5a04ee2812b70
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2019
ms.locfileid: "73541144"
---
# <a name="send-a-push-notification-in-powerapps"></a>PowerApps でプッシュ通知を送信する
プッシュ通知は、主にアプリのユーザーに注意を促したり、ユーザーが重要なタスクを優先したりできるようにするため、コンシューマー向けおよびビジネス向けのシナリオにおいてモバイル アプリで使用されます。 PowerApps では PowerApps Notification コネクタを使用して通知を送信できます。 PowerApps で作成したすべてのアプリに、ネイティブのプッシュ通知を送信できます。 通知の種類は今後追加される予定です。

![プッシュ通知の外観の例](./media/add-notifications/pic1-notification-screenshot.png)

次のような場合に、アプリにプッシュ通知を追加します。

* ユーザーがすぐに情報を知る必要がある。
* 事前に読み込まれたコンテキストで、アプリを使用してユーザーが重要なタスクを完了する必要がある。
* 一定の間隔でユーザーに注意を促す必要がある、またはユーザーが特定のコンテキストでアプリを起動する必要がある。

> [!NOTE]
> プッシュ通知を受信するには、各ユーザーが PowerApps Mobile でアプリを一度開いているか、[Dynamics 365](https://home.dynamics.com/) の AppSource からアプリを取得している必要があります。

## <a name="before-you-start"></a>開始する前に
**[共同作成者]** のアクセス許可を持つアプリで、PowerApps Notification の接続を追加します。 まだアプリを持っていない場合は、すぐに[テンプレートから作成](get-started-test-drive.md)できます。既定では、必要なアクセス許可が与えられます。 そのチュートリアルとこのページでは、ケース管理のテンプレートに基づいたアプリを使用します。

## <a name="send-a-notification-from-a-flow"></a>フローから通知を送信する
> [!NOTE]
> フローからプッシュ通知をトリガーする場合、現在一度に通知を送信できるのは 1 ユーザーまたは 1 セキュリティ グループのみです。

1. [Microsoft Flow](https://flow.microsoft.com) で、プッシュ通知が送信されるタイミングを指定するトリガーを作成します。

    たとえば、Common Data Service の **[Case]** エンティティにレコードが追加されたときに通知を送信するとします。

    ![Common Data Service のトリガーによるフローの作成のスクリーンショット](./media/add-notifications/pic4-step1-flowupdated.png)
2. **PowerApps Notification** コネクタを使用してフローのアクションを作成し、通知を送信するアプリの **[アプリ ID]** を入力します。

    自分のシナリオが反映されるように、接続の名前を変更することもできます。

    ![プッシュ通知を受信する PowerApps への接続の作成のスクリーン ショット](./media/add-notifications/pic5-step2-create-connection.jpg)
3. (省略可能) アプリの起動時 (ユーザーによるプッシュ通知のタップ後) にアプリにパラメーターを渡します。

    この例では、選択した連絡先の **[Case ID]** と **[Initial Owner]** フィールドを渡します。

    ![プッシュ通知に省略可能なパラメーターを渡しているスクリーン ショット](./media/add-notifications/pic6-step3-configure-notif.jpg)

## <a name="send-a-notification-from-an-app"></a>アプリから通知を送信する
プッシュ通知は別のアプリにも、同じアプリにも送信できます。

1. [PowerApps](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) で、プッシュ通知を送信するアプリに移動します。
2. **[詳細]** タブで、そのアプリの **[アプリ ID]** をコピーします。

    ![アプリ ID を取得する](./media/add-notifications/grab-id.png)
3. **[接続]** タブに進み、PowerApps Notification コネクタへの接続を作成し、前の手順のアプリ ID に貼り付けます。

    ![接続の作成](./media/add-notifications/create-connection.png)
4. トリガー アプリへの接続を追加します。

    この例では、トリガー アプリと同じアプリを使用します。 ケースを再割り当てするユーザーは、新しいケース所有者にもプッシュ通知を送信します。

    ![接続の追加](./media/add-notifications/add-connection.png)
5. プッシュ通知の接続から、 **[SendPushNotification]** メソッドを呼び出します。

    この例では、フォームの **OnSuccess** プロパティを使用してこの通知をトリガーします。

    ![PowerApps の数式](./media/add-notifications/powerapps-function.png)

## <a name="load-a-specific-page-and-context-when-a-user-taps-the-notification"></a>ユーザーが通知をタップしたときに、特定のページとコンテキストを読み込む
### <a name="pass-parameters"></a>パラメーターを渡す
プッシュ通知で、アプリに特定のパラメーターを渡すことができます。 たとえば、 **[CaseID]** の値を読み取るには、 *[Param("CaseID")]* を使用します。 このパラメーターをすばやく識別するには、**ラベル** コントロールをアプリに追加します。 そのコントロールの **Text** プロパティを **Param("CaseID")** に設定します。 ユーザーが **[すべてのアプリ]** 一覧からアプリを開いた場合、値は空です。 ユーザーがデバイス上の別の場所からアプリを開いた場合、値には **[CaseID]** の値が入力されます。

### <a name="set-the-start-page"></a>スタート ページを設定する
アプリの起動時に、たとえば **[Case details]\(ケースの詳細\)** のページが開くように、アプリを設定することができます。

1. **タイマー** コントロールを追加し、その **OnTimerEnd** プロパティを次の数式に設定します。
   <br>**Navigate(EditCase, ScreenTransition.None)**
2. (省略可能) **Visible** プロパティを **false** に設定して、**タイマー** コントロールを非表示にします。
3. 画面の **OnVisible** プロパティを **Timer.Start()** に設定します。

> [!TIP]
> 次のように、アプリで一意の通知用のスタート ページを作成することをお勧めします。
> 
> 1. アプリがまだ開いていない空のページを作成し、**テキスト入力**コントロールを追加して、その **timer.Duration** の値を設定します。
> 2. アプリを作成するときは、タイマーの値を 0 以外に設定します。 アプリを公開する準備ができたら、タイマーがすぐにトリガーされるように、値を **0** に設定します。

## <a name="syntax"></a>構文

| 名前 | Description |
| --- | --- |
| SendPushNotification |通知の接続設定に指定されたアプリに、プッシュ通知を送信します。 |

### <a name="parameters"></a>パラメーター

| 名前 | 種類 | Description |
| --- | --- | --- |
| recipients |文字列配列、必須 |以下の一覧: <ul> <li>ユーザーまたはセキュリティ グループの電子メール アドレス</li> <li>Azure Active Directory のユーザーまたはセキュリティ グループのオブジェクト ID</li></ul> |
| message |文字列、必須 |プッシュ通知のメッセージの本文。 |
| openApp |ブール値、省略可能 |ユーザーがプッシュ通知をタップしたときにアプリを開くかどうか。 |
| params |パラメーター、省略可能 |通知に渡すキーと値のパラメーター。 特定のページを開き、特定の状態を読み込むように、アプリでさらに処理することができます。 |

### <a name="sample-formulas"></a>サンプルの数式
基本の通知を送信します。

```powerapps-dot
PowerAppsNotification.SendPushNotification(
    {
        recipients: ["f60ccf6f-7579-4f92-967c-2920473c966b", "72f988bf-86f1-41af-91ab-2d7cd011db47"],
        message: "A new case was assigned to you."
    }
)
```

アプリを開き、特定のパラメーターを渡す通知を送信します。

```powerapps-dot
PowerAppsNotification.SendPushNotification(
    {
        recipients: ["email1@contoso.com", "email2@contoso.com"],
        message: "message in the notif toast",
        params: Table({key:"notificationKey", value:"The value for notificationKey"}),
        openApp: true
    }
)
```

## <a name="known-limitations"></a>既知の制限
* 現時点では、通知は Windows Phone の PowerApps Mobile に表示されません。
* 現時点では、Web ブラウザーでのみアプリを実行するユーザーにはプッシュ通知を提供していません。
* 通知には、特定のアプリ アイコンの代わりに汎用的な PowerApps アイコンが表示されます。
* Microsoft Flow を使用する場合、一度に 1 人の受信者にしかプッシュ通知を送信できせん。

参照情報については、[PowerApps 通知の参照](https://docs.microsoft.com/connectors/powerappsnotification/)に関するページを参照してください。

