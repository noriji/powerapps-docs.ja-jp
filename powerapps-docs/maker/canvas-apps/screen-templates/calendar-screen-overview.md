---
title: カレンダー-画面テンプレート |Microsoft Docs
description: キャンバスアプリのカレンダー画面テンプレートがどのように機能するかを理解し、画面を変更し、アプリの一部として拡張します。
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 12/28/2018
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 9ca7e5f14508a2dcd70967e77b29989819bfe7ba
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2019
ms.locfileid: "73541595"
---
# <a name="overview-of-the-calendar-screen-template-for-canvas-apps"></a>キャンバスアプリのカレンダー画面テンプレートの概要

Canvas アプリで、Office 365 Outlook アカウントからの今後のイベントを表示する予定表画面を追加します。 ユーザーはカレンダーから日付を選択し、その日のイベントの一覧をスクロールすることができます。 一覧に表示される詳細を変更したり、各イベントの詳細を表示する2番目の画面を追加したり、各イベントの出席者のリストを表示したり、その他のカスタマイズを行ったりすることができます。

また、[電子メール](email-screen-overview.md)、組織内の[ユーザー](people-screen-overview.md) 、会議に招待するユーザーの[利用](meeting-screen-overview.md)可能性など、Office 365 のさまざまなデータを表示するテンプレートベースの他の画面を追加することもできます。

この概要では、次のことについて説明します。
> [!div class="checklist"]
> * 既定のカレンダー画面を使用する方法について説明します。
> * 変更方法。
> * アプリに統合する方法。

この画面の既定の機能の詳細については、「[カレンダー画面リファレンス](calendar-screen-reference.md)」を参照してください。

## <a name="prerequisite"></a>前提条件

[PowerApps でアプリを作成](../data-platform-create-app-scratch.md)するときに、画面やその他のコントロールを追加および構成する方法について理解します。

## <a name="default-functionality"></a>既定の機能

テンプレートから予定表画面を追加するには、次のようにします。

1. PowerApps に[サインイン](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)し、PowerApps Studio でアプリを作成するか、既存のアプリを開きます。

    このトピックでは phone アプリについて説明しますが、同じ概念がタブレットアプリにも当てはまります。

1. リボンの **[ホーム]** タブで、[**新しい画面** > **カレンダー**] を選択します。

    既定では、画面は次のようになります。

    ![予定表画面](media/calendar-screen/calendar-initial.png)

1. データを表示するには、画面の上部付近のドロップダウンリストでオプションを選択します。

    ![読み込みが完了した後の予定表画面](./media/calendar-screen/calendar-screen.png)

役に立つ注意事項がいくつかあります。

* 今日の日付が既定で選択されています。右上隅のカレンダーアイコンを選択すると、簡単に戻ることができます。
* 別の日付を選択すると、円が囲まれ、明るい四角形 (既定のテーマが適用されている場合は青色) が今日の日付を囲むようになります。
* 特定の日付に対して少なくとも1つのイベントがスケジュールされている場合は、カレンダーのその日付の下に小さな色付きの円が表示されます。
* 1つ以上のイベントがスケジュールされている日付を選択すると、そのイベントはカレンダーの下の一覧に表示されます。

## <a name="modify-the-screen"></a>画面を変更する

この画面の既定の機能は、いくつかの一般的な方法で変更できます。

* [カレンダーを指定](calendar-screen-overview.md#specify-the-calendar)します。
* [イベントに関するさまざまな詳細を表示](calendar-screen-overview.md#show-different-details-about-an-event)します。
* [非ブロッキングイベントを非表示](calendar-screen-overview.md#hide-nonblocking-events)にします。

画面をさらに変更する場合は、ガイドとして[カレンダー画面参照](./calendar-screen-reference.md)を使用します。

### <a name="specify-the-calendar"></a>カレンダーの指定

ユーザーに表示する予定のカレンダーが既にわかっている場合は、アプリを発行する前にそのカレンダーを指定することで、画面を簡略化できます。 この変更により、カレンダーのドロップダウンリストが不要になるため、削除することができます。

1. アプリの既定の画面の **[OnStart](../controls/control-screen.md)** プロパティを次の数式に設定します。

    ```powerapps-dot
    Set( _userDomain, Right( User().Email, Len( User().Email ) - Find( "@", User().Email ) ) );
    Set( _dateSelected, Today() );
    Set( _firstDayOfMonth, DateAdd( Today(), 1 - Day( Today() ), Days ) );
    Set( _firstDayInView, 
        DateAdd( _firstDayOfMonth, -( Weekday( _firstDayOfMonth) - 2 + 1 ), Days )
    );
    Set( _lastDayOfMonth, DateAdd( DateAdd( _firstDayOfMonth, 1, Months ), -1, Days ) );
    Set( _calendarVisible, false );
    Set( _myCalendar, 
        LookUp( Office365.CalendarGetTables().value, DisplayName = "{YourCalendarNameHere}" )
    );
    Set( _minDate, 
        DateAdd( _firstDayOfMonth, -( Weekday(_firstDayOfMonth) - 2 + 1 ), Days )
    );
    Set( _maxDate, 
        DateAdd(
            DateAdd( _firstDayOfMonth, -( Weekday(_firstDayOfMonth) - 2 + 1 ), Days ),
            40, 
            Days 
        )
    );
    ClearCollect( MyCalendarEvents, 
        Office365.GetEventsCalendarViewV2( _myCalendar.Name, 
            Text( _minDate, UTC ), 
            Text( _maxDate, UTC ) 
        ).value
    );
    Set( _calendarVisible, true )
    ```

    > [!NOTE]
    > この数式は、カレンダーを選択するためのドロップダウンリストの**Onselect**プロパティの既定値から若干編集されています。 このコントロールの詳細については、[カレンダー画面リファレンス](./calendar-screen-reference.md#calendar-drop-down)のセクションを参照してください。

1. 中かっこを含む `{YourCalendarNameHere}`を、表示する予定のカレンダーの名前 (たとえば**calendar**) に置き換えます。

    > [!IMPORTANT]
    > 次の手順では、アプリに予定表の画面を1つだけ追加したことを前提としています。 複数のコントロールを追加した場合、制御名 ( **iconCalendar1**など) は異なる数値で終了し、それに応じて数式を調整する必要があります。

1. **IconCalendar1**コントロールの**Y**プロパティを次の式に設定します。

    `RectQuickActionBar1.Height + 20`

1. **LblMonthSelected1**コントロールの**Y**プロパティを次の式に設定します。

    `iconCalendar1.Y + iconCalendar1.Height + 20`

1. **LblNoEvents1**コントロールの**Text**プロパティを次の値に設定します。

    `"No events scheduled"`

1. **LblNoEvents1**の**Visible**プロパティを次の数式に設定します。

    `CountRows(CalendarEventsGallery1.AllItems) = 0 && _calendarVisible`

1. 次のコントロールを削除します。

    - **dropdownCalendarSelection1**
    - **LblEmptyState1**
    - **iconEmptyState1**

1. カレンダー画面が既定の画面でない場合は、アプリをテストできるように、既定の画面から予定表画面に移動するボタンを追加します。

    たとえば、空白から作成したアプリに予定表画面を追加した場合は、 **Screen2**に移動するボタンを**Screen1**に追加します。

1. アプリを保存し、ブラウザーまたはモバイルデバイスでテストします。

### <a name="show-different-details-about-an-event"></a>イベントに関するさまざまな詳細を表示する

既定では、 **CalendarEventsGallery**という名前のカレンダーの下にあるギャラリーには、開始時刻、期間、件名、および各イベントの場所が表示されます。 [Office 365 コネクタ](https://docs.microsoft.com/connectors/office365/#calendareventclientreceive)がサポートしているフィールド (オーガナイザーなど) を表示するようにギャラリーを構成できます。

1. **CalendarEventsGallery**で、新規または既存のラベルの**Text**プロパティを `ThisItem` の後にピリオドを付けて設定します。

    IntelliSense では、選択できるフィールドが一覧表示されます。

1. 目的のフィールドを選択します。

    ラベルには、指定した情報の種類が表示されます。

### <a name="hide-nonblocking-events"></a>非ブロッキングイベントの非表示

多くのオフィスでは、チームメンバーが会議出席依頼を送信し、オフィスから離れたときに互いに通知します。 すべてのユーザーのスケジュールをブロックしないようにするために、要求を送信するユーザーはその可用性を**無料**に設定します。 これらのイベントは、いくつかのプロパティを更新することで、カレンダーとギャラリーから非表示にすることができます。

1. **CalendarEventsGallery**の**Items**プロパティを次の数式に設定します。

    ```powerapps-dot
    SortByColumns(
        Filter(
            MyCalendarEvents,
            Text( Start, DateTimeFormat.ShortDate ) = 
                Text( _dateSelected, DateTimeFormat.ShortDate ),
            ShowAs <> "Free"
        ),
        "Start"
    )
    ```

    この数式では、**フィルター**関数は、選択されたイベント以外の日付に対してスケジュールされているイベントだけでなく、Availability が**Free**に設定されているイベントも非表示にします。

1. カレンダーで、**円**コントロールの**Visible**プロパティを次の数式に設定します。

    ```powerapps-dot
    CountRows(
        Filter(
            MyCalendarEvents,
            DateValue( Text(Start) ) = DateAdd( _firstDayInView, ThisItem.Value, Days ),
            ShowAs <> "Free"
        )
    ) > 0 && !Subcircle1.Visible && Title2.Visible
    ```
    この数式には、前の数式と同じフィルターが含まれています。 そのため、選択した日付に1つ以上のイベントがあり、その可用性が**Free**に設定されていない場合にのみ、イベントインジケーターの円が日付の下に表示されます。

## <a name="integrate-the-screen-into-an-app"></a>画面をアプリに統合する

Calendar screen は独自の機能を備えた強力なコントロールですが、通常は大規模で汎用性の高いアプリの一部として最適に動作します。 この画面を大きなアプリに統合するには、次のオプションを追加するなど、さまざまな方法があります。

* [イベントの詳細を表示](calendar-screen-overview.md#view-event-details)します。
* [イベントの出席者を表示](calendar-screen-overview.md#show-event-attendees)します。

### <a name="view-event-details"></a>イベントの詳細の表示

ユーザーが**CalendarEventsGallery**でイベントを選択した場合、そのイベントに関する詳細情報を表示する別の画面を開くことができます。

> [!NOTE]
> この手順では、動的なコンテンツを含むギャラリーにイベントの詳細が表示されますが、他の方法を使用して同様の結果を得ることができます。 たとえば、代わりに一連のラベルを使用して、より多くのデザインコントロールを取得できます。

1. 空の柔軟な高さのギャラリーを含む**Eventheight screen**という名前の空の画面を追加し、予定表画面に戻るボタンを追加します。

1. 柔軟な高さのギャラリーで、**ラベル**コントロールと**HTML テキスト**コントロールを追加し、両方の**autoheight**プロパティを**true**に設定します。

    > [!NOTE]
    > PowerApps は、各イベントのメッセージ本文を HTML テキストとして取得するため、そのコンテンツを**html テキスト**コントロールに表示する必要があります。

1. **HTML テキスト**コントロールの**Y**プロパティを次の式に設定します。

    `Label1.Y + Label1.Height + 20`

1. 必要に応じて、スタイルのニーズに合わせて追加のプロパティを調整します。

    たとえば、 **HTML テキスト**コントロールの下に区切り線を追加することができます。

1. 柔軟な高さのギャラリーの**Items**プロパティを次の数式に設定します。

    ```powerapps-dot
    Table(
        { Title: "Subject", Value: _selectedCalendarEvent.Subject },
        { 
            Title: "Time", 
            Value: _selectedCalendarEvent.Start & " - " & _selectedCalendarEvent.End 
        },
        { Title: "Body", Value: _selectedCalendarEvent.Body }
    )
    ```

    この数式は、 **_selectedCalendarEvent**のフィールド値に設定された動的データのギャラリーを作成します。これは、ユーザーが**CalendarEventsGallery**コントロールでイベントを選択するたびに設定されます。 このギャラリーを拡張して、さらに多くのフィールドを含めることができます。ただし、このセットには適切な開始点が用意されています。

1. ギャラリー項目を配置した状態で、 **Label**コントロールの**Text**プロパティを `ThisItem.Title`に設定し、 **HTML テキスト**コントロールの**HtmlText**プロパティを `ThisItem.Value`に設定します。

1. **CalendarEventsGallery**で、 **Title**コントロールの**onselect**プロパティを次の数式に設定します。

    ```powerapps-dot
    Set( _selectedCalendarEvent, ThisItem );
    Navigate( EventDetailsScreen, None )
    ```

    > [!Note]
    > 代わりに、 **_selectedCalendarEvent**変数を使用する代わりに、 **CalendarEventsGallery**を使用することもできます。オフ.

### <a name="show-event-attendees"></a>イベント出席者を表示する

`Office365.GetEventsCalendarViewV2` 操作は、セミコロンで区切られた必須出席者とオプションの出席者のセットを含む、各イベントのさまざまなフィールドを取得します。 この手順では、各参加者のセットを解析し、組織内の参加者を特定して、そのユーザーの Office 365 プロファイルを取得します。

1. アプリに Office 365 Users コネクタが含まれていない場合は、[それを追加](../add-data-connection.md)します。

1. 会議出席者の Office 365 プロファイルを取得するには、 **CalendarEventsGallery**の **[タイトル]** コントロールの**onselect**プロパティを次の数式に設定します。

    ```powerapps-dot
    Set( _selectedCalendarEvent, ThisItem );
    ClearCollect( AttendeeEmailsTemp,
        Filter(
            Split( ThisItem.RequiredAttendees & ThisItem.OptionalAttendees, ";" ),
            !IsBlank( Result )
        )
    );
    ClearCollect( AttendeeEmails,
        AddColumns( AttendeeEmailsTemp, 
            "InOrg",
            Upper( _userDomain ) = Upper( Right( Result, Len( Result ) - Find( "@", Result ) ) )
        )
    );
    ClearCollect( MyPeople,
        ForAll( AttendeeEmails, If( InOrg, Office365Users.UserProfile( Result ) ) ) 
    );
    Collect( MyPeople,
        ForAll( AttendeeEmails,
            If( !InOrg, 
                { DisplayName: Result, Id: "", JobTitle: "", UserPrincipalName: Result }
            )
        )
    )
    ```

この一覧では、各**Clearcollect**操作の動作について説明します。

- ClearCollect (AttendeeEmailsTemp)
    ```powerapps-dot
    ClearCollect( AttendeeEmailsTemp,
        Filter(
            Split( ThisItem.RequiredAttendees & ThisItem.OptionalAttendees, ";" ), 
            !IsBlank( Result)
        )
    );
    ```

    この数式では、必須出席者と省略可能な出席者を1つの文字列に連結し、その文字列をセミコロンで個々のアドレスに分割します。 次に、そのセットの空白の値をフィルターで除外し、他の値を**AttendeeEmailsTemp**という名前のコレクションに追加します。

- ClearCollect (AttendeeEmails)
    ```powerapps-dot
    ClearCollect( AttendeeEmails,
        AddColumns( AttendeeEmailsTemp, 
            "InOrg",
            Upper( _userDomain ) = Upper( Right( Result, Len(Result) - Find("@", Result) ) )
        )
    );
    ```
    この数式は、参加者が組織内にあるかどうかを大まかに判断します。 **Userdomain**の定義は、アプリを実行しているユーザーの電子メールアドレスのドメイン URL にすぎません。 この行では、 **AttendeeEmailsTemp**コレクションに**inorg**という名前の追加の true/false 列が作成されます。 この列には、 **Userdomain**が、その特定の行の**AttendeeEmailsTemp**の電子メールアドレスのドメイン URL と等しい場合に**true**が格納されます。

    この方法は常に正確ではありませんが、かなり近いものになります。 たとえば、組織内の特定の参加者は Jane@OnContoso.comのような電子メールアドレスを持つことがありますが、 **Userdomain**は Contoso.com です。 アプリのユーザーと加藤さんは同じ会社で仕事をしているかもしれませんが、電子メールアドレスに多少の違いがあります。 次のような場合は、次の式を使用することをお勧めします。

    `Upper(_userDomain) in Upper(Right(Result, Len(Result) - Find("@", Result)))`

    ただし、この数式は、Jane@NotTheContosoCompany.com のような電子メールアドレスと Contoso.com のような**Userdomain**を照合し、それらのユーザーが同じ会社で作業しないようにします。

- ClearCollect (MyPeople)

    ```powerapps-dot
    ClearCollect( MyPeople,
        ForAll( AttendeeEmails, 
            If( InOrg, 
                Office365Users.UserProfile( Result )
            )
        )
    );
    Collect( MyPeople,
        ForAll( AttendeeEmails,
            If( !InOrg, 
                { 
                    DisplayName: Result, 
                    Id: "", 
                    JobTitle: "", 
                    UserPrincipalName: Result
                }
            )
        )
    );
    ```
    Office 365 のプロファイルを取得するには、 [Office365Users](https://docs.microsoft.com/connectors/office365users/#userprofile)または[Office365Users](https://docs.microsoft.com/connectors/office365users/#userprofile)操作を使用する必要があります。 これらの操作では、まず、ユーザーの組織内にある出席者のすべての Office 365 プロファイルが収集されます。その後、操作によって、組織の外部から参加者のためのいくつかのフィールドが追加されます。 これらの2つの項目を個別の操作に分割したのは、 **ForAll**ループが順序を保証していないためです。 そのため、 **ForAll**は最初に組織の外部から出席者を回収することがあります。 この場合、 **MyPeople**のスキーマには**DisplayName**、 **Id**、 **jobtitle**、および**UserPrincipalName**だけが含まれます。 ただし、UserProfile 操作は、これよりもはるかに豊富なデータを取得します。 そのため、 **MyPeople**コレクションでは、他のプロファイルの前に Office 365 プロファイルを追加するように強制します。

    > [!NOTE]
    > **Clearcollect**関数を1つだけ使用して同じ結果を得ることができます。

    ```powerapps-dot
    ClearCollect( MyPeople, 
        ForAll(
            AddColumns(
                Filter(
                    Split(
                        ThisItem.RequiredAttendees & ThisItem.OptionalAttendees, 
                        ";"
                    ), 
                    !IsBlank( Result )
                ), 
                "InOrg", _userDomain = Right( Result, Len( Result ) - Find( "@", Result ) )
            ), 
            If( InOrg, 
                Office365Users.UserProfile( Result ), 
                { 
                    DisplayName: Result, 
                    Id: "", 
                    JobTitle: "", 
                    UserPrincipalName: Result, 
                    Department: "", 
                    OfficeLocation: "", 
                    TelephoneNumber: ""
                }
            )
        )
    )
    ```

この演習を完了するには:

1. **Items**プロパティが**MyPeople**に設定されているギャラリーを含む画面を追加します。

1. **CalendarEventsGallery**の**タイトル**コントロールの**onselect**プロパティで、前の手順で作成した画面に**Navigate**関数を追加します。

## <a name="next-steps"></a>次の手順

* [この画面のリファレンスドキュメントを表示](calendar-screen-reference.md)します。
* [Office 365 Outlook コネクタの詳細については、こちらを参照して](../connections/connection-office365-outlook.md)ください。
* [Office 365 Users コネクタの詳細については、こちらを参照して](../connections/connection-office365-users.md)ください。
