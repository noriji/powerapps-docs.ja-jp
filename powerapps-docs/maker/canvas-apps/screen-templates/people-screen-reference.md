---
title: People screen のテンプレートリファレンス |Microsoft Docs
description: PowerApps でキャンバスアプリの people screen テンプレートがどのように機能するかについて詳しく説明します。
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 1/2/2019
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 0a1626583300e6fe696415a91de68ff08596f081
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/07/2019
ms.locfileid: "71989379"
---
# <a name="reference-information-about-the-people-screen-template-for-canvas-apps"></a>Canvas apps の people screen テンプレートに関するリファレンス情報

PowerApps のキャンバスアプリの場合、people 画面テンプレートの各重要なコントロールが画面の既定の機能全体にどのように影響するかを理解します。 この詳細では、動作の数式と、コントロールがユーザー入力にどのように応答するかを決定するその他のプロパティの値を示します。 この画面の既定の機能の概要については、「 [people screen の概要](people-screen-overview.md)」を参照してください。

ここでは、いくつかの重要なコントロールについて説明し、これらのコントロールのさまざまなプロパティ ( **Items**や**onselect**など) が設定される式または数式について説明します。

* [テキスト検索ボックス](#text-search-box)
* [ユーザー参照ギャラリー](#user-browse-gallery) (+ 子コントロール)
* [自分が追加したギャラリー](#people-added-gallery) (+ 子コントロール)

## <a name="prerequisite"></a>前提条件

[PowerApps でアプリを作成](../data-platform-create-app-scratch.md)するときに、画面やその他のコントロールを追加および構成する方法について理解します。

## <a name="text-search-box"></a>テキスト検索ボックス

![Texttexttextコントロール](media/people-screen/people-search-box.png)

他のいくつかのコントロールが相互作用しているか、テキスト検索ボックスに依存しています。

* ユーザーがテキストの入力を開始すると、 **UserBrowseGallery**が表示されます。
* ユーザーが**UserBrowseGallery**内で人物を選択すると、検索内容がリセットされます。

## <a name="user-browse-gallery"></a>ユーザー-ギャラリーの参照

![UserBrowseGallery コントロール](media/people-screen/people-browse-gall.png)

* プロパティ: **Items**<br>
    値: ユーザーが入力を開始したときにユーザーを検索するロジック:
    
    ```powerapps-dot
    If( !IsBlank( Trim( TextSearchBox.Text ) ), 
        'Office365Users'.SearchUser(
            {
                searchTerm: Trim( TextSearchBox.Text ), 
                top: 15
            }
        )
    )
    ```
    
このギャラリーの項目は、 [Office365 ユーザー](https://docs.microsoft.com/connectors/office365users/#searchuser)操作の検索結果によって設定されます。 操作は `Trim(TextSearchBox)` 内のテキストを検索語として受け取り、その検索に基づいて上位15件の結果を返します。 空白を検索するユーザーが無効なため、 **texttexttextが**`Trim()` 関数でラップされています。

`Office365Users.SearchUser` 操作は、検索ボックスにユーザーが入力したテキストが含まれている場合にのみ操作を呼び出す必要があるため、`If(!IsBlank(Trim(TextSearchBox.Text)) ... )` 関数でラップされます。 これにより、パフォーマンスが向上します。

### <a name="userbrowsegallery-title-control"></a>UserBrowseGallery Title コントロール

![UserBrowseGallery Title コントロール](media/people-screen/people-browse-gall-title.png)

* プロパティ:**テキスト**<br>値: `ThisItem.DisplayName`

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

   * 選択した項目に **\_selectedUser**変数を設定します。
   * **Texttexttextの**検索語句をリセットします。
   * 選択した項目を**MyPeople**コレクションに追加します。このコレクションは、アプリユーザーが選択したすべてのユーザーのコレクションです。

### <a name="userbrowsegallery-profileimage-control"></a>UserBrowseGallery ProfileImage コントロール

![UserBrowseGallery ProfileImage コントロール](media/people-screen/people-browse-gall-image.png)

* プロパティ: **Image**<br>
    値: ユーザーのプロファイル写真を取得するためのロジック。

    ```powerapps-dot
    If( !IsBlank( ThisItem.Id ) && 
            'Office365Users'.UserPhotoMetadata( ThisItem.Id ).HasPhoto,
        'Office365Users'.UserPhoto( ThisItem.Id )
    )
    ```

**イメージ**コントロールは、 [Office365Users](https://docs.microsoft.com/connectors/office365users/#get-user-photo--v1-)操作を使用してユーザーのイメージを取得します。 ただし、この作業を行う前に、次の2つのことを確認します。
  
   * ID フィールドが空であるか、空でないかを示します。 これにより、ギャラリーに検索結果が設定される前に、**イメージ**コントロールがユーザーの写真を取得しようとするのを防ぐことができます。
   * ユーザーが写真を持っているかどうか ( [Office365Users メタデータ](https://docs.microsoft.com/connectors/office365users/#get-user-photo-metadata)操作を含む)。 これにより、ユーザーがプロファイル画像を持っていない場合に、`Office365Users.UserPhoto` の参照から例外が返されるのを防ぐことができます。

画像が取得されない場合、**イメージ**コントロールは空白になり、代わりに**iconuser**コントロールが表示されることに注意してください。

## <a name="people-added-gallery"></a>People が追加されたギャラリー

![PeopleAddedGallery コントロール](media/people-screen/people-people-gall.png)

* プロパティ: **Items**<br>
    値: `MyPeople`

これは、 **UserBrowseGallery Title**コントロールを選択することによって、に初期化または追加された人間のコレクションです。

### <a name="peopleaddedgallery-title-control"></a>PeopleAddedGallery Title コントロール

![PeopleAddedGallery Title コントロール](media/people-screen/people-people-gall-title.png)

* プロパティ: **Onselect**<br>
    値: `Set( _selectedUser, ThisItem )`

**EmailPeopleGallery**で選択した項目に **_selectedUser**変数を設定します。

### <a name="peopleaddedgallery-iconremove-control"></a>PeopleAddedGallery iconRemove コントロール

![PeopleAddedGallery iconRemove コントロール](media/people-screen/people-people-gall-delete.png)

* プロパティ: **Onselect**<br>
    値: `Remove( MyPeople, LookUp( MyPeople, UserPrincipalName = ThisItem.UserPrincipalName ) )`

**MyPeople**コレクション内のレコードを検索します。 **userprincipalname**は選択された項目の**userprincipalname**と一致し、そのレコードをコレクションから削除します。

## <a name="next-steps"></a>次の手順

* [この画面の詳細について](./people-screen-overview.md)は、こちらをご覧ください。
* [Office 365 Outlook コネクタの詳細については、こちらを参照して](../connections/connection-office365-outlook.md)ください。
* [Office 365 Users コネクタの詳細については、こちらを参照して](../connections/connection-office365-users.md)ください。
