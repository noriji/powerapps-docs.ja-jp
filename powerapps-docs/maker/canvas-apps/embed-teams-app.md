---
title: Teams に PowerApps アプリを埋め込む |Microsoft Docs
description: PowerApps で作成したアプリを Microsoft Teams に埋め込み、共有することができます。
author: jimholtz
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 09/09/2019
ms.author: jimholtz
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: ba08437dc144fc81aa9748163b1005222735cb69
ms.sourcegitcommit: a560630f5ee83629a7236ae774fc0c8195b95efa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2019
ms.locfileid: "70842243"
---
# <a name="embed-a-powerapps-app-in-teams"></a>チームへの PowerApps アプリの埋め込み 

作成した PowerApps は、Microsoft Teams に直接埋め込むことによって共有できます。 完了すると、ユーザーは [ **+** ] を選択して、チーム内**のチームチャネル**または会話にアプリを追加できます。 アプリは、**チームのタブ**の下にタイルとして表示されます。 

管理者はアプリをアップロードして、テナント内の**すべて**のチームに対して [**すべてのタブ] セクション**に表示されるようにすることができます。 「 [Microsoft Teams でのアプリの共有」を](https://docs.microsoft.com/en-us/power-platform/admin/embed-app-teams)参照してください。

> [!NOTE]
> Team カスタムアプリポリシーは、カスタムアプリのアップロードを許可するように設定する必要があります。 アプリをチームに埋め込むことができない場合は、管理者に連絡して、[カスタムアプリ設定](https://docs.microsoft.com/MicrosoftTeams/teams-custom-app-policies-and-settings#custom-app-policy-and-settings)がセットアップされているかどうかを確認してください。 

## <a name="prerequisites"></a>前提条件

- [PowerApps ライセンスを持っている](https://docs.microsoft.com/power-platform/admin/pricing-billing-skus)
- キャンバスアプリを作成しました

## <a name="locate-your-powerapps-guid"></a>PowerApp の GUID を見つける

後の手順で使用する PowerApp の GUID を見つけてメモします。

1. [@No__t_1](https://web.powerapps.com)にサインインし、メニューの **[アプリ]** を選択します。

   > [!div class="mx-imgBorder"] 
   > ![アプリの一覧を表示する](./media/embed-teams-app/file-apps2.png "アプリの一覧を表示する")

2. チームで共有するアプリの **[その他のコマンド]** (...) を選択し、 **[詳細]** を選択します。

   > [!div class="mx-imgBorder"] 
   > ![アプリの詳細](./media/embed-teams-app/app-details.png "アプリの詳細")


3. 後で使用するために**アプリ ID**を記録します。

   > [!div class="mx-imgBorder"] 
   > ![アプリの詳細](./media/embed-teams-app/app-details2.png "アプリの詳細")

## <a name="install-app-studio"></a>App Studio のインストール

App Studio が既にインストールされている場合は、これらの手順を省略できます。 

1. チームで、[チーム] メニュー (![アプリアイコン](./media/embed-teams-app/apps-icon.png "アプリアイコン")) の左下にある **[アプリ]** を選択します。

2. 検索ボックスで "App Studio" を検索し、それを選択します。

   > [!div class="mx-imgBorder"] 
   > ![App Studio](./media/embed-teams-app/store-app-studio.png "App Studio")

3. **[インストール]** を選択します。 

   > [!div class="mx-imgBorder"] 
   > ![App Studio のインストール](./media/embed-teams-app/install-app-studio.png "App Studio のインストール")

4. アプリ機能に対して **[開く]** を選択します。

   > [!div class="mx-imgBorder"] 
   > ![App Studio を開く](./media/embed-teams-app/open-app-studio.png "App Studio を開く")

## <a name="create-a-teams-app-for-your-powerapp"></a>PowerApp 用の Teams アプリを作成する

1. Teams で、App Studio を開きます。

   > [!div class="mx-imgBorder"] 
   > ![App Studio を開く](./media/embed-teams-app/open-app-studio2.png "App Studio を開く")

2. **マニフェストエディター** タブを選択し、ようこそ の下にある **新しいアプリの作成** を選択します。

   > [!div class="mx-imgBorder"] 
   > ![新しいアプリの作成](./media/embed-teams-app/create-new-app.png "新しいアプリの作成")

3. アプリの**詳細**ページで、アプリに関する情報を入力します。  アプリ ID GUID については、上記で記録した PowerApp のアプリ ID GUID を使用する必要があります。  これにより、特定の PowerApp に対する Teams アプリの重複が回避されます。
 
   > [!div class="mx-imgBorder"] 
   > ![情報の入力](./media/embed-teams-app/fill-in-info-about-app.png "情報の入力")

   |フィールド  |説明  |
   |---------|---------|
   |**アプリ名** |    |
   |短い名前     | 必須。 アプリの短い表示名。 30文字の制限。        |
   |長い名前     | アプリの完全名。完全なアプリ名が30文字を超える場合に使用されます。       | 
   |**番号**     |         |
   |アプリ ID     | 必須。 Microsoft が生成したこのアプリの一意の識別子。        |
   |パッケージ名     | 必須。 このアプリの一意の識別子。 逆引きドメイン表記を使用することをお勧めします。たとえば、「.com」のようにします.<AppName>。       |
   |バージョン     | 必須。 特定のアプリのバージョン。 マニフェストの内容を更新する場合は、バージョンもインクリメントする必要があります。     |
   |**摘要**    |     |
   | 簡単な説明    | 必須。 領域が制限されている場合に使用される、アプリのエクスペリエンスに関する簡単な説明。 80文字の制限。   |
   | 長い説明    | 必須。 アプリの完全な説明。     |
   | **開発者向け情報**    |     |
   | 名前    | 必須。 会社または開発者の表示名。     |
   | 用    | 必須。 Powerapps.com を使用したアプリの web サイトへの https://URL。 だれかがアプリをインストールすると、"アプリについて" というページが表示されます。 Powerapps.com 上のアプリの web バージョンにリンクする必要があります。   |
   | **アプリの Url**    | これらのリンクは、web サイトの URL と共に **[バージョン情報]** ページに表示されます。     |
   | プライバシーに関する声明    | 必須。 開発者のプライバシーポリシーへの https://URL。 [例](https://go.microsoft.com/fwlink/p/?LinkID=698505)。   |
   | 利用規約    | 必須。 開発者の使用条件への https://URL。  [例](https://go.microsoft.com/fwlink/p/?LinkID=698507)。  |
   | **戦略**    |     |
   | 全色    | Full color 192x192 PNG アイコンへの相対ファイルパス。    |
   | 透明なアウトライン    |透過的な32x32 の PNG アウトラインアイコンへの相対ファイルパス。     |
   | アクセントカラー    | アウトラインアイコンの背景としておよびと組み合わせて使用する色。     |

詳細については、「[マニフェストエディター](https://docs.microsoft.com/microsoftteams/platform/get-started/get-started-app-studio#manifest-editor)と[マニフェストスキーマ](https://docs.microsoft.com/microsoftteams/platform/resources/schema/manifest-schema)」を参照してください。

4. [ブランド] セクションまで下にスクロールし、アプリに必要なロゴとアクセントカラーを追加します。  これらは、チームでアプリに対して表示されるロゴです。 

   > [!div class="mx-imgBorder"] 
   > ![ブランド化とタブ](./media/embed-teams-app/branding-tabs.png "ブランド化とタブ")

5. **[機能]** で、 **[タブ]** を選択します。

6. [**チーム] タブ**で **[追加]** を選択します。

   > [!div class="mx-imgBorder"] 
   > ![チームタブの追加](./media/embed-teams-app/team-tab-add.png "チームタブの追加")

7. 次の形式を使用して、"Configuration URL" 入力フィールドにアプリの構成 URL を追加します。 `https://apps.powerapps.com/teams/settings/<PowerApp ID>`

   @No__t_0 を、上で記録したアプリ ID GUID に置き換えます。

   アプリを表示する[スコープ](https://docs.microsoft.com/microsoftteams/platform/concepts/tabs/tabs-overview#tab-scope)を選択します。 **[更新プログラムの構成]** チェックボックスがオンになっていることを確認し、 **[保存]** を選択します。

   > [!div class="mx-imgBorder"] 
   > ![構成 URL](./media/embed-teams-app/configuration-url.png "構成 URL")

8. **[完了]** で、 **[有効なドメイン]** を選択します。 **Apps.powerapps.com**と**apps.preview.powerapps.com**を Teams アプリケーションの有効なドメインとして追加します。

   > [!div class="mx-imgBorder"] 
   > ![有効なドメインの追加](./media/embed-teams-app/add-valid-domains.png "有効なドメインの追加")

9. **[完了]** で、 **[テストおよび配布]** を選択します。 **[インストール]** で、 **[インストール]** を選択します。

   > [!div class="mx-imgBorder"] 
   > ![インストールの選択](./media/embed-teams-app/test-distribute-app.png "インストールの選択")

10. アプリをインストールするチームを選択し、 **[インストール]** を選択します。

    > [!div class="mx-imgBorder"] 
    > ![チームインストールに追加](./media/embed-teams-app/new-app-add-to-team.png "チームインストールに追加")
11. そのアプリのインスタンスをチャネルに追加する場合は、アプリを使用するチャネルを選択し、 **[セットアップ]** を選択します。

    > [!div class="mx-imgBorder"] 
    > ![セットアップの選択](./media/embed-teams-app/app-now-available.png "セットアップの選択")

12. **[保存]** を選択します。

## <a name="add-the-app-as-a-tab"></a>アプリをタブとして追加する

チャネルまたはメッセージ交換にアプリをタブとして追加するには、[ **+** ] を選択し、**チームの [タブ**] でアプリを選択します。 

> [!div class="mx-imgBorder"] 
> ![[アプリをタブとして追加]](./media/embed-teams-app/add-app-as-tab.png "[アプリをタブとして追加]")

これで、アプリがタブとして表示されるようになります。

> [!div class="mx-imgBorder"] 
> ![[アプリとしてのアプリ]](./media/embed-teams-app/app-as-tab.png "[アプリとしてのアプリ]")

### <a name="see-also"></a>関連項目
[Microsoft Teams へようこそ](https://docs.microsoft.com/MicrosoftTeams/teams-overview)<br />
[For 管理者:Microsoft Teams にアプリを埋め込む ](https://docs.microsoft.com/power-platform/admin/share-app-teams)
