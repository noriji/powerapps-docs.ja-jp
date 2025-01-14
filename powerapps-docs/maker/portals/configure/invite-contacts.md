---
title: ポータルに連絡先を招待する |MicrosoftDocs
description: ポータルで招待を作成して構成する方法について説明します。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 631f17d9764fbfc209fd193ddabe4882f8ad8042
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2019
ms.locfileid: "73552223"
---
# <a name="invite-contacts-to-your-portals"></a>ポータルに連絡先を招待する

ポータルの招待機能を使用して、Common Data Service で作成された自動電子メールを通じて、ポータルに連絡先を招待します。 招待した相手は、自分で完全にカスタマイズできる電子メールを、ポータルへのリンクと招待コードと共に受信します。 このコードを使用して、ユーザーが構成した特別なアクセス権を取得できます。 この機能を使用すると、次のことが可能になります。

- 1つまたは複数の招待を送信する
-   必要に応じて有効期限を指定します
-   必要に応じて、招待元としてユーザーまたはポータルの連絡先を指定します
-   招待の利用時に招待された連絡先を自動的にアカウントに割り当てる
-   招待の引き換え時に自動的にワークフローを実行する
-   招待された連絡先を、利用時に Web ロールに自動的に割り当てる

招待の引き換えは、さまざまな認証オプションを使用して実現できます。 ポータル認証に関するドキュメントについては、「[ポータルの認証 id を設定](set-authentication-identity.md)し、ポータルのバージョンと構成に適したモデルを選択する」を参照してください。 ユーザーは、利用時に管理者によって提供された設定を採用します。 招待と連絡先に対して [招待の引き換え] 活動が作成されます。

招待は、**送信招待**ワークフローを使用して送信されます。 既定では、ワークフローは、汎用メッセージを含む電子メールを作成し、招待された連絡先のプライマリ電子メールアドレスに送信します。 **送信招待**ワークフローには、ポータルの特定のメッセージを含むように編集する必要がある電子メールテンプレートと、ポータルの [招待の利用 **] ページ**への適切なハイパーリンクが含まれています。

**送信招待**ワークフロー電子メールテンプレートを編集するには、それを見つけて非アクティブ化します。 非アクティブ化した後、電子メールテンプレートを編集して必要なメッセージを送信し、ポータルの [招待の取得 **] ページ**へのリンクを提供します。

> [!NOTE]
> 招待は、連絡先のプライマリ電子メール (emailaddress1) にのみ送信されます。 招待は、連絡先レコードのセカンダリメール (emailaddress2) または連絡用メール (emailaddress3) に送信されません。

## <a name="create-invitations-from-portal-management-app"></a>ポータル管理アプリから招待を作成する

1.  [ポータル管理アプリ](configure-portal.md)を開きます。

2.  [**ポータル** > **連絡先**] にアクセスします。
    または、[[共有](../manage-existing-portals.md#share)] ウィンドウから **[連絡先]** ページを開くこともできます。 

3.  連絡先を選択するか、招待する連絡先レコードを開きます。

4.  コマンドバーで [招待の**作成**] を選択します。

5.  **[招待]** ページで、フィールドに適切な値を入力します。 詳細情報:[招待属性](#invitation-attributes)

6.  **[保存]** を選択します。

7.  コマンドバーで、[**フロー** > **送信の招待**] を選択します。

    > [!div class="mx-imgBorder"]
    > ![招待の送信ワークフロー](../media/send-invitation-portal-app.png "招待の送信ワークフロー")

8.  確認ウィンドウで、[ **OK]** を選択します。 招待は、選択した連絡先に送信されます。

    > [!div class="mx-imgBorder"]
    > ![招待状の送信の確認](../media/confirm-invitation-portal-app.png "招待状の送信の確認")

### <a name="send-multiple-invitations"></a>複数の招待を送信する

連絡先の招待を作成し、一度にすべての招待を送信することができます。

1.  必要な連絡先の招待を作成し、**ポータル** > **招待**にアクセスします。

2.  作成した招待を選択します。

3.  コマンドバーで、[**フロー** > **送信の招待**] を選択します。

    > [!div class="mx-imgBorder"]
    > ![招待の送信ワークフロー](../media/send-invitation-portal-app.png "招待の送信ワークフロー")

4.  確認ウィンドウで、[ **OK]** を選択します。 招待は、選択した連絡先に送信されます。

    > [!div class="mx-imgBorder"]
    > ![複数の招待の送信の確認](../media/confirm-multiple-invites-portal-app.png "複数の招待の送信の確認")

## <a name="invitation-attributes"></a>招待属性

次の表では、**招待**ページの属性について説明します。


|  名前    |    Description    |
|-------|------------|
|                 名前                  |                                                                                                      招待を認識するのに役立つわかりやすい名前。                                                                                                      |
|                 種類                  |                                             **1 つ**または**複数のグループ**。 1つの連絡先に招待できるのは1つの連絡先だけで、1回の引き換えのみが許可されます。 グループでは、複数の連絡先と複数の引き換えを招待できます。                                              |
|             所有者/送信者              | 招待状が送信されたときに電子メールの送信者になるユーザー。 作成した電子メールに [差出人] フィールドのユーザーが既に含まれている場合は、**送信招待**ワークフローでこれを上書きできます。 |
|            招待コード            |                                                                 招待状が知られるのは、招待状の一意のコードです。 これは、新しい招待を作成するときに自動的に生成されます。                                                                  |
|              有効期限日              |                                                                                     招待が引き換えに無効になる日時を表す日付。 省略可能。                                                                                     |
|                招待元                |                                                                                               連絡先が招待の送信者である場合に使用できます。 省略可能。                                                                                                |
|          招待した連絡先           |                                                                                                             ポータルに招待される連絡先です。                                                                                                              |
|           アカウントに割り当て           |                                                                        招待を引き換えるときに、取引先の連絡先の親顧客として関連付けるアカウントレコード。 省略可能。                                                                        |
| 連絡先の引き換えにワークフローを実行する |                                                         招待が引き換えされたときに実行されるワークフロープロセス。 ワークフローには、プライマリエンティティとして引き換え連絡先が渡されます。 省略可能。                                                          |
|          Web ロールへの割り当て          |                                                                               招待の引き換え時に、対応する連絡先に関連付けられる一連の web ロール。 省略可能。                                                                                |
|          引き換え済み連絡先          |                                                                                                   招待状の引き換えに成功した連絡先。                                                                                                   |
|      許可される最大引き換え      |                                                                                   招待を引き換えることができる回数。 グループの種類の招待でのみ使用できます。                                                                                   |
|                                       |                                                                                                                                                                                                                                                                    |

### <a name="see-also"></a>関連項目

[ポータルで使用する連絡先を構成する](configure-contacts.md)  
[ポータルの認証 id を設定する](set-authentication-identity.md)  
