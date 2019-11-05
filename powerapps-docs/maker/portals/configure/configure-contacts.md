---
title: ポータルで使用する連絡先を構成する |MicrosoftDocs
description: ポータルで使用する連絡先を追加して構成する手順。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 4a8c70304385007c132f2c13ec0ddca4b68e2231
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2019
ms.locfileid: "73553189"
---
# <a name="configure-a-contact-for-use-on-a-portal"></a>ポータルで使用する連絡先を構成する

連絡先の基本情報を入力した後 (または、ユーザーがポータルでサインアップフォームに入力した場合)、ポータルの連絡先フォームの [web 認証] タブにアクセスし、ローカル認証を使用して連絡先を構成します。 フェデレーション認証オプションの詳細については、「[ポータルの認証 id を設定](set-authentication-identity.md)する」を参照してください。 ローカル認証を使用してポータルの連絡先を構成するには、次の手順に従います。  

1.  **ユーザー名**を入力します。
2.  コマンド リボンで、**その他のコマンド** &gt; **パスワードの変更** に移動します。

パスワードの変更ワークフローを完了すると、必要なフィールドが自動的に構成されます。 これを完了すると、お客様のポータル用に連絡先が構成されます。

## <a name="change-password-for-a-contact-from-portal-management-app"></a>ポータル管理アプリから連絡先のパスワードを変更する

1.  [ポータル管理アプリ](configure-portal.md)を開きます。

2.  [**ポータル** > **連絡先**] に移動し、パスワードを変更する連絡先を開きます。
    または、[[共有](../manage-existing-portals.md#share)] ウィンドウから **[連絡先]** ページを開くこともできます。 

3.  上部にあるツールバーの **[タスクフロー]** を選択します。

    > [!div class="mx-imgBorder"]
    > ![タスクフローアイコン](../media/task-flow.png "タスクフローアイコン")

4.  **ポータルの連絡先**タスクフローの [パスワードの変更] を選択します。

5.  **[ポータル連絡先のパスワードの変更]** ウィンドウで、パスワードを変更する連絡先を選択または作成し、 **[次へ]** を選択します。

    > [!div class="mx-imgBorder"]
    > ![パスワードを変更する連絡先を選択してください](../media/change-password-select-contact.png "パスワードを変更する連絡先を選択してください")

6.  **[新しいパスワード]** フィールドに新しいパスワードを入力し、 **[次へ]** を選択します。

    > [!div class="mx-imgBorder"]
    > ![連絡先の新しいパスワードを入力してください](../media/change-password-new-password.png "連絡先の新しいパスワードを入力してください")

    パスワードを入力せずに **[次へ]** を選択した場合は、選択した連絡先のパスワードを削除するかどうかを確認するメッセージが表示されます。

    > [!div class="mx-imgBorder"]
    > ![連絡先のパスワードを削除します。](../media/change-password-remove-password.png "連絡先のパスワードを削除します。")

7.  変更を行った後、 **[完了]** を選択します。


### <a name="see-also"></a>関連項目
[ポータルに連絡先を招待する](invite-contacts.md)  
[ポータルの認証 id を設定する](set-authentication-identity.md)  