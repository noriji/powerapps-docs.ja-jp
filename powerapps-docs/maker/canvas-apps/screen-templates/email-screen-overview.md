---
title: 電子メール-画面テンプレート |Microsoft Docs
description: キャンバスアプリの電子メール画面テンプレートがどのように機能するかを理解し、独自のユースケースに合わせて画面を拡張する
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 12/29/2018
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: b6f977154a350c6ca4b0b630cb4a4050e6d015c8
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2019
ms.locfileid: "73541489"
---
# <a name="overview-of-the-email-screen-template-for-canvas-apps"></a>キャンバスアプリの電子メール画面テンプレートの概要

Canvas アプリで、ユーザーが Office 365 Outlook アカウントから電子メールを送信できるようにする電子メール画面を追加します。 ユーザーは、組織で受信者を検索したり、外部の電子メールアドレスを追加したりすることができます。 画像添付ファイルのサポートを追加したり、検索ギャラリーに表示されるユーザーデータを変更したり、その他のカスタマイズを行ったりすることができます。

また、ユーザーの[予定表](calendar-screen-overview.md)、[組織内のユーザー、](people-screen-overview.md)会議に招待するユーザーの[利用](meeting-screen-overview.md)可能性など、Office 365 のさまざまなデータを表示するテンプレートベースの他の画面を追加することもできます。

この概要では、次のことについて説明します。
> [!div class="checklist"]
> * 既定の電子メール画面を使用する方法。
> * 変更方法。
> * アプリに統合する方法。

この画面の既定の機能の詳細については、[電子メール画面のリファレンス](email-screen-reference.md)を参照してください。

## <a name="prerequisite"></a>前提条件

[PowerApps でアプリを作成](../data-platform-create-app-scratch.md)するときに、画面やその他のコントロールを追加および構成する方法について理解します。

## <a name="default-functionality"></a>既定の機能

テンプレートから電子メール画面を追加するには、次のようにします。

1. PowerApps に[サインイン](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)し、PowerApps Studio でアプリを作成するか、既存のアプリを開きます。

    このトピックでは phone アプリについて説明しますが、同じ概念がタブレットアプリにも当てはまります。

1. リボンの **[ホーム]** タブで、[**新しい画面** > **電子メール**] を選択します。

    既定では、画面は次のようになります。

    ![電子メール画面](media/email-screen/email-screen-full.png)

役に立つ注意事項がいくつかあります。

* 組織内のユーザーを検索するには、"To" の下のテキスト入力ボックスに名前を入力します。
* 検索時には、上位15件の結果のみが返されます。
* 組織外の電子メールの受信者の電子メールアドレスを追加するには、完全な有効な電子メールアドレスを入力し、右側に表示される [+] アイコンを選択します。
* 少なくとも1人を受信者として追加し、件名を入力して電子メールを送信する必要があります。
* 電子メールを送信した後は、件名行とメッセージ本文の内容、および受信者リストはすべて消去されます。

## <a name="modify-the-screen"></a>画面を変更する

この画面の既定の機能は、いくつかの一般的な方法で変更できます。

* [イメージ添付ファイルのサポートの追加](email-screen-overview.md#add-image-attachment-support)
* [他のデータを表示する](email-screen-overview.md#show-different-data-for-people)

画面をさらに変更する場合は、[電子メールの画面参照](./email-screen-reference.md)をガイドとして使用します。

> [!IMPORTANT]
> 次の手順では、アプリに電子メール画面を1つだけ追加したことを前提としています。 複数のコントロールを追加した場合、制御名 ( **iconMail1**など) は異なる数値で終了し、それに応じて数式を調整する必要があります。

### <a name="add-image-attachment-support"></a>イメージ添付ファイルのサポートの追加

これにより、ユーザーは電子メールを添付ファイルとして1つの画像を送信できます。

1. **[挿入]** タブで **[メディア]** を選択し、 **[画像の追加]** を選択します。
1. 新しいコントロールの**Y**プロパティを次の式に設定します。

    `TextEmailMessage1.Y + TextEmailMessage1.Height + 20`
    
1. **Addmediawithimage**コントロールが挿入された状態で、その高さを210未満に設定します。
1. コントロールツリービューで、[ **Addmediawithimage** >  **...** ] を選択し、 **[並べ替え]**  >  **[戻る]**  > ます。
   これにより、コントロールが**PeopleBrowseGallery**コントロールの前に置かれるのを防ぐことができます。
1. **EmailPeopleGallery**の**Height**プロパティを次の数式に変更します。

    ```powerapps-dot
    Min( 
        ( EmailPeopleGallery1.TemplateHeight + EmailPeopleGallery1.TemplatePadding * 2 ) *
            RoundUp( CountRows( EmailPeopleGallery1.AllItems ) / 2, 0 ), 
        304
    )
    ```

1. **EmailPeopleGallery**の**showscrollbar**プロパティを次の式に設定します。

    ```EmailPeopleGallery1.Height >= 304```
    
    これにより、最大の高さが**Addmediawithimage**コントロールをページからプッシュするのを防ぐことができます。
    
1. **Iconmail**コントロールの**onselect**プロパティを次の数式に変更します。

    ```powerapps-dot
    Set( _emailRecipientString, Concat(MyPeople, Mail & ";") );
    If( IsBlank( UploadedImage1 ),
        'Office365'.SendEmail( _emailRecipientString, 
            TextEmailSubject1.Text, 
            TextEmailMessage1.Text, 
            { Importance: "Normal" }
        ),
        'Office365'.SendEmail( _emailRecipientString, 
            TextEmailSubject1.Text, 
            TextEmailMessage1.Text, 
            {
                Importance: "Normal",
                Attachments: Table(
                    {
                        Name: "Image.jpg", 
                        ContentBytes: UploadedImage1.Image
                    }
                )
            }
        )
    );
    Reset( TextEmailSubject1 );
    Reset( TextEmailMessage1 );
    Reset( AddMediaButton1 );
    Clear( MyPeople )
    ```
    
    この数式は、アップロードされたイメージを確認します。 存在しない場合は、以前と同じ `Office365.SendEmail` 操作が使用されます。 画像がある場合は、添付ファイルテーブルに添付ファイルとして追加されます。
    電子メールの送信後、アップロードされたイメージを削除するために、 **AddMediaButton**で追加の**リセット**操作が実行されます。
> [!NOTE]
> 複数の添付ファイルを電子メールに追加するには、添付ファイルテーブルにレコードを追加します。

### <a name="show-different-data-for-people"></a>他のデータを表示する

この画面では、 [Office365Users](https://docs.microsoft.com/connectors/office365users/#searchuser)操作を使用して、組織内のユーザーを検索します。**PeopleBrowseGallery**コントロールに表示される内容を超えて、各イベントの追加フィールドを提供します。 ギャラリーでのフィールドの追加または変更は簡単です。

1. **PeopleBrowseGallery**コントロールで、変更するラベルを選択します (または追加して、選択したままにします)。

1. **テキスト**プロパティを選択した状態で、数式バーの内容を `ThisItem.` に置き換えます。

    IntelliSense では、選択できるフィールドの一覧が表示されます。

1. 目的のフィールドを選択します。

    **Text**プロパティが `ThisItem.{FieldSelection}`に更新されます。

## <a name="integrate-the-screen-into-an-app"></a>画面をアプリに統合する

電子メール画面は独自の機能を備えた強力なコントロールですが、通常は大規模で汎用性の高いアプリの一部として最適に動作します。 この画面を大きなアプリに統合するには、[カレンダー画面へのリンク](email-screen-overview.md#linking-to-the-calendar-screen)など、さまざまな方法があります。

### <a name="linking-to-the-calendar-screen"></a>予定表画面へのリンク

「 [Calendar screen の概要](./calendar-screen-overview.md#show-event-attendees)」の「イベントの参加者を表示」セクションで説明されている手順に従います。最後の手順では、 **Navigate**関数を設定して、電子メール画面を開きます。 これらの手順を完了すると、 **MyPeople**コレクションに値が設定され、ユーザーは選択したイベントに参加しているユーザーに電子メールを送信できるようになります。

> [!NOTE]
> この電子メールを送信すると、Outlook の実際のイベントから別の電子メールが送信されます。

## <a name="next-steps"></a>次の手順

* [この画面のリファレンスドキュメントを表示](./email-screen-reference.md)します。
* [Office 365 ユーザーコネクタの詳細については、PowerApps を参照して](../connections/connection-office365-users.md)ください。
* [PowerApps で使用可能なすべての接続を表示](../connections-list.md)します。