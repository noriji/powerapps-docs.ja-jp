---
title: キャンバスアプリの電子メール画面テンプレートのリファレンス |Microsoft Docs
description: PowerApps でキャンバスアプリの電子メール画面テンプレートがどのように機能するかについて詳しく説明します。
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 12/31/2018
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 7663668b77c6f8186ef54c3182230fa843f86577
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/07/2019
ms.locfileid: "71995699"
---
# <a name="reference-information-about-the-email-screen-template-for-canvas-apps"></a>キャンバスアプリの電子メール画面テンプレートに関するリファレンス情報

PowerApps のキャンバスアプリの場合、電子メール画面テンプレートの各重要なコントロールが画面の既定の機能全体にどのように影響するかを理解します。 この詳細では、動作の数式と、コントロールがユーザー入力にどのように応答するかを決定するその他のプロパティの値を示します。 この画面の既定の機能の概要については、[電子メール画面の概要](email-screen-overview.md)に関するページを参照してください。

ここでは、いくつかの重要なコントロールについて説明し、これらのコントロールのさまざまなプロパティ ( **Items**や**onselect**など) が設定される式または数式について説明します。

* [テキスト検索ボックス](#text-search-box)
* [[追加] アイコン](#add-icon)
* [People 閲覧ギャラリー](#people-browse-gallery)
* [電子メール people ギャラリー](#email-people-gallery) (+ 子コントロール)
* [メールアイコン](#mail-icon)

## <a name="prerequisite"></a>前提条件

[PowerApps でアプリを作成](../data-platform-create-app-scratch.md)するときに、画面やその他のコントロールを追加および構成する方法について理解します。

## <a name="text-search-box"></a>テキスト検索ボックス

   ![Texttexttextコントロール](media/email-screen/email-search-box.png)

画面内の他のいくつかのコントロールは、**テキスト検索ボックス**コントロールに依存しています。

* ユーザーがテキストの入力を開始すると、 **PeopleBrowseGallery**が表示されます。
* ユーザーが有効な電子メールアドレスを入力すると、 **Addicon**が表示されます。
* ユーザーが**PeopleBrowseGallery**内で人物を選択すると、検索内容がリセットされます。

## <a name="add-icon"></a>[追加] アイコン

   ![AddIcon コントロール](media/email-screen/email-add-icon.png)

[**アイコンの追加]** コントロールを使用すると、アプリユーザーは、組織内に存在しないユーザーを、構成されている電子メールの受信者の一覧に追加できます。

* プロパティ: **Visible**<br>
    値: ユーザーが検索ボックスに有効な電子メールアドレスを入力した場合にのみ、コントロールを表示するロジック:

    ```powerapps-dot
    !IsBlank( TextSearchBox.Text ) &&
        IsMatch( TextSearchBox.Text, Match.Email ) &&
        Not( Trim( TextSearchBox.Text ) in MyPeople.UserPrincipalName )
    ```
  行ごとに、前のコードブロックは、次の場合にのみ、[**アイコンの追加]** コントロールが表示されることを示しています。

    * **Texttexttextに**はテキストが含まれます。
    * **Texttextの**テキストは、有効な電子メールアドレスです。
    * **Textsearchbox**コレクション内のテキストは、既に存在しません。

* プロパティ: **Onselect**<br>
    値: これを選択すると、 **MyPeople**コレクションに有効な電子メールアドレスが追加されます。 このコレクションは、画面で受信者の一覧として使用されます。

    ```powerapps-dot
    Collect( MyPeople,
        { 
            DisplayName: TextSearchBox.Text, 
            UserPrincipalName: TextSearchBox.Text, 
            Mail: TextSearchBox.Text
        }
    );
    Reset( TextSearchBox )
    ```
  
  このコードブロックは、 **MyPeople**コレクションに行を追加し、 **texttexttextの**テキストを3つのフィールドに設定します。 この3つのフィールドは**DisplayName**、 **UserPrincipalName**、および**Mail**です。 次に、 **texttexttextの**内容をリセットします。

## <a name="people-browse-gallery"></a>People 閲覧ギャラリー

   ![PeopleBrowseGallery コントロール](media/email-screen/email-browse-gall.png)

* プロパティ: **Items**<br>
    Value: **texttextcontrol**に入力された検索テキストの上位15件の検索結果。
    
    ```powerapps-dot
    If( !IsBlank( Trim(TextSearchBox.Text ) ), 
        'Office365Users'.SearchUser( {searchTerm: Trim( TextSearchBox.Text ), top: 15} )
    )
    ```

  このギャラリーの項目は、 [Office365 ユーザー](https://docs.microsoft.com/connectors/office365users/#searchuser)操作の検索結果によって設定されます。 操作は `Trim(TextSearchBox)` 内のテキストを検索語として受け取り、その検索に基づいて上位15件の結果を返します。
  
  空白を検索するユーザーが無効なため、 **texttexttextが**`Trim()` 関数でラップされています。 `Office365Users.SearchUser` 操作は `If(!IsBlank(Trim(TextSearchBox.Text)) ... )` 関数でラップされます。これは、検索ボックスにユーザーが入力したテキストが含まれている場合にのみ操作が実行されることを意味します。 これにより、パフォーマンスが向上します。 

### <a name="people-browse-gallery-title-control"></a>People 閲覧ギャラリーのタイトルコントロール

   ![PeopleBrowseGallery Title コントロール](media/email-screen/email-browse-gall-title.png)

* プロパティ:**テキスト**<br>
    値: `ThisItem.DisplayName`

  Office 365 プロファイルからのユーザーの表示名を表示します。

* プロパティ: **Onselect**<br>
    値: ユーザーをアプリレベルのコレクションに追加するコードを入力し、ユーザーを選択します。

    ```powerapps-dot
    Concurrent(
        Set( _selectedUser, ThisItem ),
        Reset( TextSearchBox ),
        If( Not( ThisItem.UserPrincipalName in MyPeople.UserPrincipalName ), 
            Collect( MyPeople, ThisItem )
        )
    )
    ```
このコントロールを選択すると、次の3つの処理が同時に実行される

   * 選択した項目に **_selectedUser**変数を設定します。
   * **Texttexttextの**検索語句をリセットします。
   * 選択した項目を**MyPeople**コレクションに追加します。このコレクションは、電子メール画面が受信者のセットとして使用する、選択されたすべてのユーザーのコレクションです。

## <a name="email-people-gallery"></a>電子メールの people ギャラリー

   ![EmailPeopleGallery コントロール](media/email-screen/email-people-gall.png)

* プロパティ: **Items**<br>
    値: `MyPeople`

  これは、 **PeopleBrowseGallery Title**コントロールを選択することによって、に初期化または追加された人間のコレクションです。

* プロパティ:**高さ**<br>
    値: ギャラリー内の現在の項目数に基づいて、高さを設定するロジック:

    ```powerapps-dot
    Min( 
        ( EmailPeopleGallery.TemplateHeight + EmailPeopleGallery.TemplatePadding * 2) *
            RoundUp(CountRows(EmailPeopleGallery.AllItems) / 2, 0 ),
        304
    )
    ```

  このギャラリーの高さは、ギャラリー内の項目の数に合わせて調整されます。最大の高さは304です。
  
  **EmailPeopleGallery**の1行の高さの合計として `TemplateHeight + TemplatePadding * 2` を取得し、行の数で乗算します。 `WrapCount = 2`のため、true 行の数は `RoundUp(CountRows(EmailPeopleGallery.AllItems) / 2, 0)`ます。

* プロパティ: **Showscrollbar**<br>
    値: `EmailPeopleGallery.Height >= 304`
  
  ギャラリーの高さが304に達すると、スクロールバーが表示されます。

### <a name="email-people-gallery-title-control"></a>電子メール people ギャラリーのタイトルコントロール

   ![EmailPeopleGallery Title コントロール](media/email-screen/email-people-gall-text.png)

* プロパティ: **Onselect**<br>
    値: `Set(_selectedUser, ThisItem)`

  **EmailPeopleGallery**で選択した項目に **_selectedUser**変数を設定します。

### <a name="email-people-gallery-iconremove-control"></a>電子メール people ギャラリーアイコンの削除コントロール

   ![MonthDayGallery Title コントロール](media/email-screen/email-people-gall-delete.png)

* プロパティ: **Onselect**<br>
    値: `Remove( MyPeople, LookUp( MyPeople, UserPrincipalName = ThisItem.UserPrincipalName ) )`

  **MyPeople**コレクション内のレコードを検索します。 **userprincipalname**は選択された項目の**userprincipalname**と一致し、そのレコードをコレクションから削除します。

## <a name="mail-icon"></a>メールアイコン

* プロパティ: **Onselect**<br>
    値: ユーザーの電子メールメッセージを送信するロジック:

    ```powerapps-dot
    Set( _emailRecipientString, Concat( MyPeople, Mail & ";" ) );
    'Office365'.SendEmail( _emailRecipientString, 
        TextEmailSubject.Text,  
        TextEmailMessage.Text, 
        { Importance:"Normal" }
    );
    Reset( TextEmailSubject );
    Reset( TextEmailMessage );
    Clear( MyPeople )
    ```

  電子メールメッセージを送信するには、セミコロンで区切られた電子メールアドレスを指定する必要があります。 前のコードでは、次のようになります。
  1. コードの1行目では、 **MyPeople**コレクション内のすべての行から**メール**フィールドを取得し、それらをセミコロンで区切られた1つの電子メールアドレスの文字列に連結し、 **_emailRecipientString**変数をその文字列値に設定します。

  1. 次に、 [SendEmail](https://docs.microsoft.com/connectors/office365/#sendemail)操作を使用して、受信者に電子メールを送信します。
    操作には、 **To**、 **Subject**、 **Body**という3つの必須パラメーターと、1つの省略可能なパラメーター--**重要度**があります。 上記のコードで**は、これら**は **_emailRecipientString**、テキストです。テキスト、テキスト、**メッセージ**。Text および**Normal**。
  1. 最後に、テキストコントロール**とテキスト** **メッセージ**のコントロールをリセットし、 **MyPeople**コレクションをクリアします。

* プロパティ: **DisplayMode**<br>
    値 `If( Len( Trim( TextEmailSubject.Text ) ) > 0 && !IsEmpty( MyPeople ), DisplayMode.Edit, DisplayMode.Disabled )`: 電子メールを送信する場合、電子メールの件名行にはテキストが含まれている必要があり、受信者 (**MyPeople**) コレクションを空にすることはできません。

## <a name="next-steps"></a>次の手順

* [この画面の詳細情報](./email-screen-overview.md)
* [PowerApps での Office 365 Outlook コネクタについての詳細情報](../connections/connection-office365-outlook.md)
* [PowerApps での Office 365 Users コネクタについての詳細情報](../connections/connection-office365-users.md)
