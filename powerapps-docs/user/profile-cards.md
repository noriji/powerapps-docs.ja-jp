---
title: 連絡先またはユーザーのプロファイルカードを表示する |MicrosoftDocs
ms.custom: ''
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 10/03/2019
ms.author: mduelae
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 276c7d3cbf95947306fab768da8af3c4c66b33e0
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2019
ms.locfileid: "73543370"
---
# <a name="view-the-profile-card-for-a-contact-or-user"></a>連絡先またはユーザーのプロファイルカードを表示する

プロファイルカードを使用して、連絡先またはユーザーに関する簡単な情報を取得します。 Dynamics 365 Sales や Dynamics 365 カスタマサービスなど、Dynamics 365 のモデル駆動型アプリで連絡先またはユーザーフィールドを選択すると、それらに関連する情報がプロファイルカードに表示されます。 プロファイルカードの詳細については、「 [Office 365 のプロファイルカード](https://support.office.com/article/Profile-cards-in-Office-365-e80f931f-5fc4-4a59-ba6e-c1e35a85b501)」を参照してください。

> [!NOTE]
>  - プロファイルカードは、 **Contact**および**User**エンティティで使用できます。 詳細については、「[プロファイルカードを有効にする (管理者向け)](https://docs.microsoft.com/dynamics365/customer-engagement/admin/enable-profile-card)」を参照してください。
>  - Azure Active Directory で Office Delve サービスに対して多要素認証が有効になっている場合、Common Data Service のプロファイルカードは表示されません。

## <a name="view-a-contacts-profile"></a>連絡先のプロファイルを表示する

1.  **[アクティビティ]** に移動します。
2.  既存のアクティビティを選択するか、新しいアクティビティを作成します。
3.  連絡先レコードがある場合は、 **[呼び出し]** フィールドの上にマウスポインターを移動します。 

連絡先の画像、名前、タイトル、およびアカウントを含む連絡先の詳細を表示できます。

4. 詳細を表示するには、 **[さらに表示]** を選択して連絡先のプロファイルを展開します。
 
    > [!div class="mx-imgBorder"] 
    > ![連絡先プロファイルカードの詳細を展開する](media/profile1.png "連絡先プロファイルカードの詳細を展開する")
   
 ## <a name="view-a-users-profile"></a>ユーザーのプロファイルを表示する
 
1.  **[アカウント]** にアクセスします。
2.  アカウントレコードを選択します。
3.  ユーザーレコードがある場合は、[所有者] フィールドにマウスポインターを移動します。 ユーザーインラインの詳細を表示できます。
4.  ユーザーとの電子メールや共有ファイルなどの詳細を表示するには、 **[詳細を表示]** を選択して連絡先のプロファイルを展開します。
 
    > [!div class="mx-imgBorder"] 
    > ![ユーザープロファイルカードの詳細を展開する](media/profile2.png "ユーザープロファイルカードの詳細を展開する")


 ## <a name="faqs"></a>ら
 
### <a name="where-can-i-see-profile-cards-in-dynamics-365"></a>Dynamics 365 のプロファイルカードはどこで確認できますか。
プロファイルカードは、連絡先レコードとユーザーレコードで見ることができます。 参照されている場合にのみ表示できます。

### <a name="where-is-information-shown-in-the-profile-card-coming-from"></a>プロファイルカードに表示される情報はどこにありますか。
連絡先プロファイルカードに表示される情報は、(Microsoft Exchange ではなく) Common Data Service からフェッチされます。 これは、連絡先の詳細が Dynamics 365 から送信されることを意味します。

ユーザープロファイルカードに表示される情報は、Office 365 (Azure Active Directory) から取得されます。 詳細については、「 [Office 365 のプロファイルカード (管理者セクション)](https://support.office.com/article/Profile-cards-in-Office-365-e80f931f-5fc4-4a59-ba6e-c1e35a85b501)」を参照してください。

### <a name="how-can-i-customize-the-fields-shown-on-the-profile-card"></a>プロファイルカードに表示されるフィールドをカスタマイズする方法はありますか
現時点では、プロファイルカードに表示されるフィールドの一覧は、カスタマイズ用に開いていません。

### <a name="why-is-the-start-chat-option-on-the-profile-card-disabled-greyed-out"></a>プロファイルカードの **[チャットの開始]** オプションが無効になっているのはなぜですか (グレー表示)
**[チャットの開始]** と プロファイル カードの **[電子メールの送信]** オプションを使用すると、既定のインスタントメッセージと電子メールアプリが開きます。 **[チャットの開始]** オプションは、自分と同じ Azure Active Directory 環境で、またはフェデレーション連絡先として接続しようとしている人がいる場合に有効になります。


  
