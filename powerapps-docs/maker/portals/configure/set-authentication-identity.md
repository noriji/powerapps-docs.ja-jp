---
title: ポータルの認証 id を設定する |MicrosoftDocs
description: ポータルの認証 id を設定する手順。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/18/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 3904de43a8e27ca555545cccdf23532970b02edd
ms.sourcegitcommit: 57b968b542fc43737330596d840d938f566e582a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2019
ms.locfileid: "72978142"
---
# <a name="set-authentication-identity-for-a-portal"></a>ポータルの認証 id を設定する

ポータルには、 [ASP.NET Identity](http://www.asp.net/identity) API 上に構築された認証機能が用意されています。 ASP.NET Identity は[OWIN](http://www.asp.net/aspnet/overview/owin-and-katana) framework 上に構築されています。これは、認証システムの重要なコンポーネントでもあります。 提供されるサービスは次のとおりです。

- ローカル (ユーザー名/パスワード) のユーザーサインイン
- サードパーティの id プロバイダーを使用した外部 (ソーシャルプロバイダー) のユーザーサインイン
- 2要素認証と電子メール
- 電子メールアドレスの確認
- パスワードの回復
- 生成前 contact レコードを登録するための招待コードのサインアップ

> [!NOTE]
> 現在、連絡先エンティティのポータルの連絡先フォームの **[携帯電話の確認]** フィールドには目的がありません。 このフィールドは、Adxstudio ポータルからアップグレードする場合にのみ使用する必要があります。

## <a name="requirements"></a>要件

ポータルには次が必要です。

- ポータルベース
- [!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)] Id
- [!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)] Id ワークフローソリューションパッケージ

## <a name="authentication-overview"></a>認証の概要

ポータルの訪問者を返すには、ローカルユーザーの資格情報または外部の id プロバイダーアカウントを使用して認証を行うことができます。 新しい訪問者は、ユーザー名とパスワードを入力するか、外部プロバイダーにサインインすることによって、新しいユーザーアカウントを登録できます。 招待コードを送信する訪問者 (ポータル管理者) は、新しいユーザーアカウントにサインアップするプロセスでコードを利用するオプションを使用できます。

**関連サイトの設定:**

- `Authentication/Registration/Enabled`
- `Authentication/Registration/LocalLoginEnabled`
- `Authentication/Registration/ExternalLoginEnabled`
- `Authentication/Registration/OpenRegistrationEnabled`
- `Authentication/Registration/InvitationEnabled`
- `Authentication/Registration/RememberMeEnabled`
- `Authentication/Registration/ResetPasswordEnabled`

### <a name="sign-in-by-using-a-local-identity-or-external-identity"></a>ローカル id または外部 id を使用してサインインする

![ローカルアカウントを使用してサインインする](../media/sign-in-local-account.png "ローカルアカウントを使用してサインインする")  

### <a name="sign-up-by-using-a-local-identity-or-external-identity"></a>ローカル id または外部 id を使用してサインアップする

![新しいローカルアカウントに登録する](../media/register-new-local-account.png "新しいローカルアカウントに登録する")  

### <a name="redeem-an-invitation-code-manually"></a>招待コードを手動で利用する

![招待コードを使用してサインアップする](../media/sign-up-invitation-code.png "招待コードを使用してサインアップする")  

## <a name="forgot-password-or-password-reset"></a>パスワードまたはパスワードのリセットを忘れた場合 

パスワードリセットを必要とする訪問者 (以前にユーザープロファイルで電子メールアドレスを指定したもの) を返すと、パスワードリセットトークンを電子メールアカウントに送信するように要求できます。 リセットトークンを使用すると、その所有者は新しいパスワードを選択できます。 または、トークンを破棄して、ユーザーの元のパスワードを変更せずに残しておくこともできます。

**関連サイトの設定:**

- `Authentication/Registration/ResetPasswordEnabled`
- `Authentication/Registration/ResetPasswordRequiresConfirmedEmail`

**関連プロセス:** 連絡先にパスワードリセットを送信する

1.  必要に応じて、ワークフローの電子メールをカスタマイズします。
2.  電子メールを送信してプロセスを呼び出します。
3.  訪問者に電子メールを確認するように求められます。
4.  ビジターは、指示に従ってパスワードリセットの電子メールを受信します。
5.  ビジターがリセットフォームに戻ります。
6.  パスワードのリセットが完了しました。

## <a name="redeem-an-invitation"></a>招待を引き換える

招待コードを適用すると、登録訪問者は、その訪問者専用に事前に準備された既存の連絡先レコードに関連付けることができます。 通常、招待コードは電子メールで送信されますが、一般的なコード送信フォームを使用して、他のチャネルでコードを送信することもできます。 有効な招待コードが送信されると、通常のユーザー登録 (サインアップ) プロセスが実行され、新しいユーザーアカウントが設定されます。

**関連サイトの設定:**

`Authentication/Registration/InvitationEnabled`

**関連プロセス:** 招待状の送信

このワークフローによって送信される電子メールは、ポータルの [使用の招待] ページの URL を使用してカスタマイズする必要があります。 http://portal.contoso.com/register/?returnurl=%2f&invitation={Invitation コード (招待)}

1. 新しい連絡先の招待を作成します。

    ![新しい連絡先の招待を作成する](../media/create-invitation.png "新しい連絡先の招待を作成する")  

2. 新しい招待をカスタマイズして保存します。

    ![新しい招待をカスタマイズする](../media/customize-new-invitation.png "新しい招待をカスタマイズする")  

3. プロセス: 招待状の送信
4. 招待メールをカスタマイズします。
5. 招待メールによって、引き換えページが開きます。
6. ユーザーは、送信された招待コードを使用してサインアップします。

    ![招待コードを使用してサインアップする](../media/sign-up-invitation-code.png "招待コードを使用してサインアップする")  

## <a name="manage-user-accounts-through-profile-pages"></a>プロファイルページを使用してユーザーアカウントを管理する

認証されたユーザーは、プロファイルページの**セキュリティ**ナビゲーションバーを使用してユーザーアカウントを管理します。 ユーザーは、ユーザー登録時に選択した単一のローカルアカウントまたは単一の外部アカウントに限定されません。 外部アカウントを持っているユーザーは、ユーザー名とパスワードを適用してローカルアカウントを作成することができます。 ローカルアカウントを使用して開始したユーザーは、複数の外部 id を自分のアカウントに関連付けることができます。 [プロファイル] ページでは、電子メールアカウントに確認の電子メールを送信するように要求することによって、電子メールアドレスを確認するようにユーザーに通知することもできます。

**関連サイトの設定:**

- `Authentication/Registration/LocalLoginEnabled`
- `Authentication/Registration/ExternalLoginEnabled`
- `Authentication/Registration/TwoFactorEnabled`

## <a name="set-or-change-a-password"></a>パスワードを設定または変更する

既存のローカルアカウントを持つユーザーは、元のパスワードを指定することによって新しいパスワードを適用できます。 ローカルアカウントを持っていないユーザーは、ユーザー名とパスワードを選択して、新しいローカルアカウントを設定できます。 ユーザー名は、設定後に変更することはできません。

**関連サイトの設定:**

`Authentication/Registration/LocalLoginEnabled`

**関連プロセス:**
- ユーザー名とパスワードを作成します。
- 既存のパスワードを変更します。

## <a name="confirm-an-email-address"></a>電子メールアドレスの確認

電子メールアドレスを変更する (または初めて設定する) と、そのアドレスが未確認の状態になります。 ユーザーは、新しい電子メールアドレスに電子メールを送信するように要求できます。電子メールには、電子メールの確認プロセスを完了するための指示が記載されています。

**関連プロセス:** 連絡先に電子メールの確認を送信する

1. 必要に応じて、ワークフローの電子メールをカスタマイズします。 
2. ユーザーが、未確認の状態にある新しい電子メールを送信した。
3. ユーザーは、確認のために電子メールを確認します。
4. プロセス: 連絡先に電子メールの確認を送信する
5. 確認の電子メールをカスタマイズします。
6. 確認プロセスを完了するために、ユーザーが確認リンクをクリックします。

> [!NOTE]
> 確認メールが連絡先のプライマリ電子メール (emailaddress1) にのみ送信されるため、連絡先の電子メールアドレスが指定されていることを確認します。 確認の電子メールは、連絡先レコードのセカンダリメール (emailaddress2) または連絡用メール (emailaddress3) に送信されません。

## <a name="enable-two-factor-authentication"></a>2要素認証を有効にする

2要素認証機能では、標準のローカルまたは外部アカウントのサインインに加えて、確認済みの電子メールの所有権を要求することで、ユーザーアカウントのセキュリティが向上します。 2要素認証が有効になっているアカウントにサインインしようとすると、アカウントに関連付けられている確認済みの電子メールにセキュリティコードが送信されます。 サインインプロセスを完了するには、セキュリティコードを送信する必要があります。 ユーザーは、正常に検証に合格したブラウザーを記憶することを選択できます。これにより、同じブラウザーからの以降のサインインにセキュリティコードが不要になります。 各ユーザーアカウントは、この機能を個別に有効にし、確認済みの電子メールを要求します。

> [!WARNING]
> 従来の機能を有効にするために**認証/登録/MobilePhoneEnabled**サイト設定を作成して有効にすると、エラーが発生します。 このサイト設定は、ポータルではサポートされていないため、既定では提供されていません。

**関連サイトの設定:**

- `Authentication/Registration/TwoFactorEnabled`
- `Authentication/Registration/RememberBrowserEnabled`

**関連プロセス:** 連絡先に電子メールの2要素コードを送信する

1. 2要素認証を有効にします。
2. セキュリティコードを電子メールで受け取ることを選択します。
3. セキュリティコードが記載されている電子メールを待ちます。
4. プロセス: 連絡先に電子メールを2つ送信します。
5. 2要素認証は無効にすることができます。

## <a name="manage-external-accounts"></a>外部アカウントの管理

認証されたユーザーは、構成済みの各 id プロバイダーから1つずつ、複数の外部 id をそのユーザーアカウントに接続 (登録) できます。 Id が接続されると、ユーザーは接続された id のいずれかを使用してサインインすることを選択できます。 1つの外部またはローカルの id が残っている限り、既存の id を切断することもできます。

**関連サイトの設定:**

- `Authentication/Registration/ExternalLoginEnabled`

**外部 Id プロバイダーのサイト設定**

1.  ユーザーアカウントに接続するプロバイダーを選択します。

    ![外部アカウントの管理](../media/manage-external-accounts.png "外部アカウントの管理")  

2.  接続するプロバイダーを使用してサインインします。

プロバイダーが接続されました。 プロバイダーを切断することもできます。

## <a name="enable-aspnet-identity-authentication"></a>ASP.NET identity 認証を有効にする

以下では、さまざまな認証機能および動作を有効または無効にするための設定について説明します。


|                        サイト設定名                        |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
|-----------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|          Authentication/Registration/LocalLoginEnabled          |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     ユーザー名 (または電子メール) とパスワードに基づいてローカルアカウントのサインインを有効または無効にします。 既定値: false                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|          認証/登録/LocalLoginByEmail          |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               ユーザー名フィールドの代わりに [電子メールアドレス] フィールドを使用して、ローカルアカウントのサインインを有効または無効にします。 既定値: false                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
|        認証/登録/ExternalLoginEnabled         |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  外部アカウントのサインインと登録を有効または無効にします。 既定値: true                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|          認証/登録/RememberMeEnabled          |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          [記憶] を選択またはクリアしますか?ローカルサインインのチェックボックスをオンにして、web ブラウザーが閉じている場合でも認証されたセッションを保持できるようにします。 既定値: true                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|          認証/登録/TwoFactorEnabled           |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        ユーザーが2要素認証を有効にするオプションを有効または無効にします。 確認済みの電子メールアドレスを持つユーザーは、2要素認証のセキュリティを強化することができます。 既定値: false                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
|       Authentication/Registration/RememberBrowserEnabled        |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                記憶ブラウザーを選択またはクリアしますか?2要素検証 (電子メールコード) のチェックボックスをオンにして、現在のブラウザーの2要素目の検証を保持します。 ユーザーは、同じブラウザーが使用されている限り、後続のサインインに対して2要素目の検証を渡す必要はありません。 既定値: true                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
|        Authentication/Registration/ResetPasswordEnabled         |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         パスワードリセット機能を有効または無効にします。 既定値: true                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| 認証/登録/ResetPasswordRequiresConfirmedEmail |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               確認済みの電子メールアドレスに対してのみ、パスワードのリセットを有効または無効にします。 有効にした場合、未確認の電子メールアドレスを使用してパスワードリセットの手順を送信することはできません。 既定値: false                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
|   Authentication/Registration/Triggerlockouton失敗パスワード    |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          失敗したパスワード試行の記録を有効または無効にします。 無効にした場合、ユーザーアカウントはロックアウトされません。既定値: true                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|             認証/登録/IsDemoMode              |                                                                                                                                                                                                                                                                                                                                                                                                                                                                          開発環境またはデモンストレーション環境でのみ使用するデモモードフラグを有効または無効にします。 運用環境ではこの設定を有効にしないでください。 デモモードでは、web ブラウザーが web アプリケーションサーバーに対してローカルで実行されている必要もあります。 デモモードを有効にすると、パスワードリセットコードと2番目の要素コードがユーザーに表示され、すばやくアクセスできるようになります。 既定値: false                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|    認証/登録/LoginButtonAuthenticationType    | ポータルで1つの外部 id プロバイダー (すべての認証を処理するため) のみが必要な場合は、ヘッダーナビゲーションバーの **サインイン** ボタンを使用して、外部 id プロバイダーのサインインページに直接リンクすることができます (代わりに、中間にリンクします)。ローカルサインインフォームおよび id プロバイダーの選択 ページ)。 このアクションに対して選択できる id プロバイダーは1つだけです。 プロバイダーの[AuthenticationType](https://msdn.microsoft.com/library/microsoft.owin.security.authenticationoptions.authenticationtype.aspx)値を指定します。<br>OpenIdConnect を使用したシングルサインオン構成 (Azure Active Directory B2C の使用など) の場合、ユーザーは権限を提供する必要があります。<br>OAuth2 ベースのプロバイダーの場合、許容される値は `Facebook, Google, Yahoo, [!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)], LinkedIn, Yammer,` または `Twitter`<br>WS-FEDERATION ベースのプロバイダーの場合は、`Authentication/WsFederation/ADFS/AuthenticationType` と `Authentication/WsFederation/[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]/\[provider\]/AuthenticationType` のサイト設定に指定された値を使用します。 例: http://adfs.contoso.com/adfs/services/trust 、Facebook-0123456789、Google、Yahoo!、uri:[!INCLUDE[pn-ms-windows-short](../../../includes/pn-ms-windows-short.md)] LiveID。 |
|                                                                 |                                                                                                                                                                                                                                                                                                  |

## <a name="enable-or-disable-user-registration"></a>ユーザー登録を有効または無効にする

次に、ユーザー登録 (サインアップ) オプションを有効または無効にするための設定について説明します。

| サイト設定名                                   | Description                                                                                                                                                                             |
|-----------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 認証/登録/有効化                 | すべての形式のユーザー登録を有効または無効にします。 このセクションの他の設定を有効にするには、登録を有効にする必要があります。 既定値: true                                   |
| 認証/登録/OpenRegistrationEnabled | 新しいローカルユーザーを作成するためのサインアップ登録フォームを有効または無効にします。 サインアップフォームを使用すると、ポータルに対する匿名の訪問者は、新しいユーザーアカウントを作成できます。 既定値: true |
| 認証/登録/InvitationEnabled       | 招待コードを所有しているユーザーを登録するための招待コードの引き換えフォームを有効または無効にします。 既定値: true                                                               |
|認証/登録/CaptchaEnabled|ユーザー登録ページで captcha を有効または無効にします。 既定値: false<br>**注**: 既定では、このサイト設定を使用できない場合があります。 Captcha を有効にするには、サイト設定を作成し、その値を true に設定する必要があります。 |
||

> [!NOTE]
> ユーザーのプライマリ電子メール (emailaddress1) を使用して登録が行われるため、ユーザーのプライマリ電子メールアドレスが指定されていることを確認します。 連絡先レコードのセカンダリメール (emailaddress2) または連絡用電子メールアドレス (emailaddress3) を使用してユーザーを登録することはできません。

## <a name="user-credential-validation"></a>ユーザー資格情報の検証

ここでは、ユーザー名とパスワードの検証パラメーターを調整するための設定について説明します。 検証は、ユーザーが新しいローカルアカウントにサインアップしたとき、またはパスワードを変更したときに発生します。

| サイト設定名                                                       | Description                                                                                                                                                                                         |
|-------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Authentication/UserManager/PasswordValidator/EnforcePasswordPolicy      | パスワードに次の3つのカテゴリの文字が含まれているかどうか。<br><ul><li>ヨーロッパ言語の大文字 (A ~ Z、分音記号、ギリシャ語、キリル文字)</li><li>ヨーロッパ言語の小文字 (a ~ z、シャープ-s、分音記号、ギリシャ語、キリル文字)</li><li>10進数 (0 ~ 9)</li><li>英数字以外の文字 (特殊文字) (例、!、$、\#、%)</li></ul>既定値は true です。 詳細については、「[パスワードポリシー](https://technet.microsoft.com/library/hh994562(v=ws.10).aspx)」を参照してください。                                                                                                           |  
| Authentication/UserManager/Usermanager/AllowOnlyAlphanumericUserNames | ユーザー名に英数字のみを許可するかどうかを指定します。 既定値は false です。 詳細については[、「Uservalidator < tuser、TKey >」を参照してください。AllowOnlyAlphanumericUserNames](https://msdn.microsoft.com/library/dn613211.aspx)。                                                          |  
| Authentication/UserManager/Usermanager/RequireUniqueEmail             | ユーザーの検証に一意の電子メールアドレスが必要かどうか。 既定値は true です。 詳細については[、「Uservalidator < tuser、TKey >」を参照してください。RequireUniqueEmail](https://msdn.microsoft.com/library/dn613213.aspx)。                                                                   |  
| Authentication/UserManager/PasswordValidator/RequiredLength             | 最低限必要なパスワードの長さ。 既定値: 8。 詳細については、「 [Passwordvalidator. RequiredLength](https://msdn.microsoft.com/library/microsoft.aspnet.identity.passwordvalidator.requiredlength.aspx)」を参照してください。                                       |  
| Authentication/UserManager/PasswordValidator/RequireNonLetterOrDigit    | パスワードに英字以外の文字または数字を含める必要があるかどうか。 既定値は false です。 詳細については、「 [Passwordvalidator](https://msdn.microsoft.com/library/microsoft.aspnet.identity.passwordvalidator.requirenonletterordigit.aspx)」を参照してください。 |  
| Authentication/UserManager/PasswordValidator/RequireDigit               | パスワードに数字 (0 ~ 9) が必要かどうか。 既定値は false です。 詳細については、「 [Passwordvalidator. RequireDigit](https://msdn.microsoft.com/library/microsoft.aspnet.identity.passwordvalidator.requiredigit.aspx)」を参照してください。                |  
| Authentication/UserManager/PasswordValidator/RequireLowercase 文字           | パスワードに小文字 (a から z まで) が必要かどうか。 既定値は false です。 詳細については、「 [Passwordvalidator. RequireLowercase 文字](https://msdn.microsoft.com/library/microsoft.aspnet.identity.passwordvalidator.requirelowercase.aspx)」を参照してください。        |  
| Authentication/UserManager/PasswordValidator/RequireUppercase           | パスワードに大文字 (A から Z まで) が必要かどうか。 既定値は false です。 詳細については、「 [Passwordvalidator. RequireUppercase 文字](https://msdn.microsoft.com/library/microsoft.aspnet.identity.passwordvalidator.requireuppercase.aspx)」を参照してください。       | 
|| 

## <a name="user-account-lockout-settings"></a>ユーザーアカウントのロックアウトの設定

次に、アカウントが認証からロックされる方法とタイミングを定義する設定について説明します。 短時間に特定の数の失敗したパスワード試行が検出されると、そのユーザーアカウントは一定期間ロックされます。 使用すると、ロックアウト期間が経過した後に再試行できます。

| サイト設定名                                               | Description                                                                                                                                                                                                                                     |
|-----------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Authentication/UserManager/Userlockoutenabled(デフォルト)          | ユーザーの作成時にユーザーロックアウトが有効かどうかを示します。 既定値は true です。 詳細については[、「Usermanager < TUser, TKey >」を参照してください。UserLockoutEnabledByDefault デフォルト](https://msdn.microsoft.com/library/dn613214.aspx)です。                                                                                                  |  
| Authentication/UserManager/DefaultAccountLockoutTimeSpan        | Authentication/UserManager/MaxFailedAccessAttemptsBeforeLockout に達した後にユーザーがロックアウトされる既定の時間。 既定値は 24:00:00 (1 日) です。 詳細については[、「Usermanager < TUser, TKey >」を参照してください。DefaultAccountLockoutTimeSpan](https://msdn.microsoft.com/library/dn613201.aspx)。                 |  
| Authentication/UserManager/MaxFailedAccessAttemptsBeforeLockout | ユーザーがロックアウトされるまでに許可されるアクセス試行の最大数 (ロックアウトが有効になっている場合)。 既定値は5です。 詳細については[、「Usermanager < TUser, TKey >」を参照してください。MaxFailedAccessAttemptsBeforeLockout](https://msdn.microsoft.com/library/dn613202.aspx)。                                                                        |  
| Authentication/ApplicationCookie/ExpireTimeSpan                 | クッキー認証セッションの有効期間の既定値。 既定値は 24:00:00 (1 日) です。 詳細については、「 [Cookieauthenticationoptions. ExpireTimeSpan](https://msdn.microsoft.com/library/microsoft.owin.security.cookies.cookieauthenticationoptions.expiretimespan(v=vs.113).aspx)」を参照してください。 |
||  

## <a name="cookie-authentication-site-settings"></a>Cookie 認証のサイト設定

既定の認証 cookie の動作を変更するための設定。 [Cookieauthenticationoptions](https://msdn.microsoft.com/library/microsoft.owin.security.cookies.cookieauthenticationoptions.aspx)クラスによって定義されます。

| サイト設定名   | Description       |
|----------------------|------------------------------------------------|
| Authentication/ApplicationCookie/AuthenticationType                      | アプリケーション認証クッキーの型。 既定値: ApplicationCookie。 詳細については、「 [Authenticationoptions:: AuthenticationType](https://msdn.microsoft.com/library/dn300391.aspx)」を参照してください。  |
| Authentication/ApplicationCookie/CookieName                              | Id を保持するために使用されるクッキー名を決定します。 既定値はです。AspNet. Cookie。 詳細については、「 [Cookieauthenticationoptions:: CookieName](https://msdn.microsoft.com/library/dn385537.aspx)」を参照してください。  |
| Authentication/ApplicationCookie/CookieDomain                            | クッキーの作成に使用されるドメインを決定します。 詳細については、「 [Cookieauthenticationoptions:: CookieDomain](https://msdn.microsoft.com/library/dn385536.aspx)」を参照してください。  |
| Authentication/ApplicationCookie/CookiePath                              | クッキーの作成に使用するパスを決定します。 既定値は/です。 詳細については、「 [Cookieauthenticationoptions:: CookiePath](https://msdn.microsoft.com/library/dn385539.aspx)」を参照してください。 |
| Authentication/ApplicationCookie/CookieHttpOnly                          | ブラウザーがクライアント側の javascript による cookie へのアクセスを許可する必要があるかどうかを判断します。 既定値は true です。 詳細については、「 [Cookieauthenticationoptions:: Cookieauthenticationoptions](https://msdn.microsoft.com/library/dn385540.aspx)」を参照してください。                     |
| Authentication/ApplicationCookie/CookieSecure                            | クッキーを HTTPS 要求でのみ送信するかどうかを決定します。 既定値: SameAsRequest。 詳細については、「 [Cookieauthenticationoptions:: CookieSecure](https://msdn.microsoft.com/library/dn385538.aspx)」を参照してください。  |
| Authentication/ApplicationCookie/ExpireTimeSpan                          | アプリケーションクッキーが作成された時点から有効な状態を維持する時間を制御します。 既定値:14 日。 詳細については、「 [Cookieauthenticationoptions:: ExpireTimeSpan](https://msdn.microsoft.com/library/microsoft.owin.security.cookies.cookieauthenticationoptions.expiretimespan(v=vs.113).aspx)」を参照してください。  |
| Authentication/ApplicationCookie/SlidingExpiration                       | SlidingExpiration は true に設定されています。これにより、ミドルウェアは、有効期限期間の半分を超える要求を処理するたびに新しい有効期限で新しいクッキーを再発行するように指示します。 既定値は true です。 詳細については、「 [Cookieauthenticationoptions:: SlidingExpiration](https://msdn.microsoft.com/library/dn385548.aspx)」を参照してください。 |
| Authentication/ApplicationCookie/LoginPath                               | LoginPath プロパティは、送信401の承認されていないステータスコードを指定されたログインパスに302リダイレクトするように変更する必要があることをミドルウェアに通知します。 既定値: ~/signin. 詳細については、「 [Cookieauthenticationoptions:: LoginPath](https://msdn.microsoft.com/library/dn385541.aspx)」を参照してください。                                            |
| Authentication/ApplicationCookie/LogoutPath                              | LogoutPath がミドルウェアに指定されている場合、そのパスに対する要求は、ReturnUrlParameter に基づいてリダイレクトされます。 詳細については、「 [Cookieauthenticationoptions:: LogoutPath](https://msdn.microsoft.com/library/dn385545.aspx)」を参照してください。               |
| Authentication/ApplicationCookie/ReturnUrlParameter                      | ReturnUrlParameter は、401の承認されていない状態コードがログインパスに302リダイレクトに変更されたときにミドルウェアによって追加されるクエリ文字列パラメーターの名前を決定します。 詳細については、「 [Cookieauthenticationoptions:: ReturnUrlParameter](https://msdn.microsoft.com/library/dn385546.aspx)」を参照してください。                           |
| Authentication/ApplicationCookie/SecurityStampValidator/ValidateInterval | セキュリティスタンプ検証の間隔。 既定値は30分です。 詳細については、「 [SecurityStampValidator:: OnValidateIdentity](https://msdn.microsoft.com/library/microsoft.aspnet.identity.owin.securitystampvalidator.onvalidateidentity.aspx)」を参照してください。                    |
| Authentication/TwoFactorCookie/AuthenticationType                        | 2要素認証 cookie の型。 既定値: TwoFactorCookie。 詳細については、「 [Authenticationoptions:: AuthenticationType](https://msdn.microsoft.com/library/dn300391.aspx)」を参照してください。            |
| Authentication/TwoFactorCookie/ExpireTimeSpan                            | 2要素クッキーが作成された時点から有効な状態を維持する時間を制御します。 既定値は5分です。 詳細については、「 [Cookieauthenticationoptions:: ExpireTimeSpan](https://msdn.microsoft.com/library/dn385543.aspx)」を参照してください。     |
|||

### <a name="see-also"></a>関連項目

[ポータル認証を構成する](configure-portal-authentication.md)  
[ポータルの OAuth2 プロバイダーの設定](configure-oauth2-settings.md)  
[ポータルの Open ID Connect プロバイダー設定](configure-openid-settings.md)  
[ポータルの WS-FEDERATION プロバイダーの設定](configure-ws-federation-settings.md)  
[ポータルの SAML 2.0 プロバイダー設定](configure-saml2-settings.md)  
