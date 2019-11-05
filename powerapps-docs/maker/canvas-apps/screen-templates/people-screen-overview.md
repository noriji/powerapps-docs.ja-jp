---
title: People 画面テンプレート |Microsoft Docs
description: キャンバスアプリのユーザー画面テンプレートのしくみと、独自のユースケースに合わせて画面を拡張する方法について説明します
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
ms.openlocfilehash: e4c688232e275cee1e285b22dd4885ea2126e7ad
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2019
ms.locfileid: "73541374"
---
# <a name="overview-of-the-people-screen-template-for-canvas-apps"></a>キャンバスアプリの people 画面テンプレートの概要

キャンバスアプリで、ユーザーが組織内のユーザーを検索できるようにする people 画面を追加します。 ユーザーは、コレクションに対してユーザーの検索、選択、および追加を行うことができます。 検索結果ギャラリーに表示されるデータの種類を変更したり、ユーザーの選択を使用して電子メールを送信したり、その他のカスタマイズを行ったりすることができます。

また、[電子メール](email-screen-overview.md)、ユーザーの[予定表](calendar-screen-overview.md)、会議に招待するユーザーの[利用](meeting-screen-overview.md)可能性など、Office 365 のさまざまなデータを表示するテンプレートベースの他の画面を追加することもできます。

この概要では、次のことについて説明します。
> [!div class="checklist"]
> * 既定の people 画面を使用する方法。
> * 画面を変更する方法。
> * 画面をアプリに統合する方法。

この画面の既定の機能の詳細については、「 [people screen reference](people-screen-reference.md)」を参照してください。

## <a name="prerequisite"></a>前提条件

[PowerApps でアプリを作成](../data-platform-create-app-scratch.md)するときに、画面やその他のコントロールを追加および構成する方法について理解します。

## <a name="default-functionality"></a>既定の機能

テンプレートから people 画面を追加するには、次のようにします。

1. PowerApps に[サインイン](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)し、PowerApps Studio でアプリを作成するか、既存のアプリを開きます。

    このトピックでは phone アプリについて説明しますが、同じ概念がタブレットアプリにも当てはまります。

1. リボンの **[ホーム]** タブで、[**新しい画面** > **People**] を選択します。

    既定では、画面は次のようになります。

    ![最初の people 画面の状態](media/people-screen/people-screen-empty.png)

1. ユーザーの検索を開始するには、上部にあるテキスト入力ボックスを選択し、同僚の名前の入力を開始します。 検索結果は、テキスト入力ボックスの下に表示されます。

    ![people 画面の検索状態](media/people-screen/people-browse-gall-full.png)

1. 検索結果から個人を選択すると、 **MyPeople**コレクションに追加されます。 検索バーの入力値がリセットされ、選択したユーザーのコレクションが表示されます。

    ![people 画面コレクションの結果](media/people-screen/people-people-gall-full.png)

## <a name="modify-the-screen"></a>画面を変更する

この画面の既定の機能を変更するには、[ユーザーごとに異なるデータを表示](people-screen-overview.md#show-different-data-for-people)します。

画面をさらに変更する場合は、ガイドとして[people screen リファレンス](./people-screen-reference.md)を使用します。

### <a name="show-different-data-for-people"></a>他のデータを表示する

この画面では、 [Office365Users](https://docs.microsoft.com/connectors/office365users/#searchuser)操作を使用して、組織内のユーザーを検索します。**UserBrowseGallery**コントロールに表示される内容を超えて、各イベントの追加フィールドを提供します。 ギャラリーでのフィールドの追加または変更は、単純なプロセスです。

1. **UserBrowseGallery**で、変更するラベルを選択します (または追加して選択したままにします)。

1. **テキスト**プロパティを選択した状態で、数式バーの内容を `ThisItem.` に置き換えます。

    IntelliSense では、選択できるフィールドの一覧が表示されます。

1. 目的のフィールドを選択します。

    **Text**プロパティを `ThisItem.{FieldSelection}`に更新する必要があります。

## <a name="integrate-the-screen-into-an-app"></a>画面をアプリに統合する

People 画面は独自の機能を備えた強力なコントロールですが、通常は、より大規模で多目的なアプリの一部として最適に動作します。 この画面は、キャッシュされた[ユーザーのリストを使用](people-screen-overview.md#use-your-cached-list-of-people)するなど、さまざまな方法で大規模なアプリに統合できます。

### <a name="use-your-cached-list-of-people"></a>キャッシュされたユーザーの一覧を使用する

People 画面では、 **MyPeople**コレクションでのユーザーの選択がキャッシュされます。 ビジネスシナリオでユーザー検索を呼び出す場合は、このコレクションの使用方法を把握しておく必要があります。 ここでは、この画面を基本的な電子メール画面に接続し、 **MyPeople**コレクション内のユーザーに電子メールを送信する方法について説明します。 また、[電子メール画面](./email-screen-overview.md)のしくみについての洞察も得られます。

1. Office 365 Outlook データソースをアプリに追加するには、 **[表示]** タブを選択し、 **[データソース > ** **追加**] を選択して、office 365 outlook コネクタを探します。 **[新しい接続]** を選択して検索することが必要になる場合があります。
1. People 画面を挿入した後、新しい空の画面を挿入します。 この画面で、戻る矢印アイコン、2つのテキスト入力ボックス、および [送信] アイコンを追加します。
1. 画面の名前を**Emailscreen**に、戻る矢印のアイコンを**backicon**に、1つのテキスト入力ボックスを**subjectline**に、もう1つは**Messagebody**に、送信アイコンを**sendicon**に変更します。
1. **Backicon**の**onselect**プロパティを `Back()`に設定します。
1. **Sendicon**の**onselect**プロパティを次の数式に設定します。

    ```powerapps-dot
    Office365.SendEmail( 
        Concat( MyPeople, UserPrincipalName & ";" ), 
        SubjectLine.Text, 
        MessageBody.Text 
    )
    ```
    
    ここでは、Outlook コネクタを使用して電子メールを送信しています。 この `Concat(MyPeople, UserPrincipalName & ";")`、受信者の一覧として渡します。 この数式は、 **MyPeople**コレクション内のすべての電子メールアドレスを、セミコロンで区切られた1つの文字列に連結します。 これは、お気に入りの電子メールクライアントの "宛先" 行に、セミコロンで区切られた電子メールアドレスの文字列を記述することとは異なります。
    * メッセージの件名として `SubjectLine.Text` を渡し、メッセージの本文として `MessageBody.Text` します。
1. [People] 画面の右上隅に、**メール**アイコンが挿入されます。
   アイコンの色を任意のものに変更します。
1. **Sendicon**の**onselect**プロパティを `Navigate( EmailScreen, None )`に設定します。

    これで、ユーザーを選択し、電子メールメッセージを作成して送信する、2画面のアプリが作成されました。 テストは自由に行うことができますが、アプリから**MyPeople**コレクションに追加したすべてのユーザーに電子メールが送信されるため、注意してください。

## <a name="next-steps"></a>次の手順

* [この画面のリファレンスドキュメントを表示](./people-screen-reference.md)します。
* [Office 365 Outlook コネクタの詳細については、こちらを参照して](../connections/connection-office365-outlook.md)ください。
* [Office 365 Users コネクタの詳細については、こちらを参照して](../connections/connection-office365-users.md)ください。
