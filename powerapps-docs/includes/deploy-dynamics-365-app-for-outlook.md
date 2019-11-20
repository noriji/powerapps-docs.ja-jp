---
title: Dynamics 365 App for Outlook の展開 | MicrosoftDocs
ms.custom: ''
ms.date: 2017-04-20
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
- Dynamics 365 (online)
ms.assetid: 09736e14-e744-48ca-a755-1b05bb55340e
caps.latest.revision: 39
author: jimholtz
ms.author: jimholtz
manager: brycho
ms.openlocfilehash: 2df69eb2823726116ca08e893acf384afffdd957
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2019
ms.locfileid: "2754128"
---
# <a name="deploy-dynamics-365-app-for-outlook"></a>Dynamics 365 App for Outlook の展開
[!INCLUDE[pn_ms_dyn_crm_app_for_outlook](../includes/pn-ms-dyn-crm-app-for-outlook.md)] を使用すると、デスクトップ、Web、またはタブレット PC で [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] を使っているときに、[!INCLUDE[pn_microsoftcrm](../includes/pn-microsoftcrm.md)] の機能を活用できます。 たとえば、電子メールや予定の受信者に関する情報を表示したり、[!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] の電子メールや予定を [!INCLUDE[pn_microsoftcrm](../includes/pn-microsoftcrm.md)] のレコード (営業案件、取引先企業、サポート案件など) にリンクしたりできます。 [!INCLUDE[pn_ms_dyn_crm_app_for_outlook](../includes/pn-ms-dyn-crm-app-for-outlook.md)] の詳細については、[Dynamics 365 App for Outlook のユーザー ガイド](https://go.microsoft.com/fwlink/p/?LinkID=613099) を参照してください。  
  
> [!IMPORTANT]
>  [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] は、[!INCLUDE[pn_crm_for_outlook_short](../includes/pn-crm-for-outlook-short.md)] と同じものではありません。 [!INCLUDE[pn_crm_8_2_0_both](../includes/pn-crm-8-2-0-both.md)] では、[!INCLUDE[cc_server_side_synch](../includes/cc-server-side-synch.md)] と [!INCLUDE[pn_ms_dyn_crm_app_for_outlook](../includes/pn-ms-dyn-crm-app-for-outlook.md)] を組み合わせることが、[!INCLUDE[pn_microsoftcrm](../includes/pn-microsoftcrm.md)] と [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] を統合するための推奨される方法です。 **[!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] と [!INCLUDE[pn_crm_for_outlook_short](../includes/pn-crm-for-outlook-short.md)] が同一のユーザーによって共に使用されている場合、活動の追跡はサポートされません。** [!INCLUDE[pn_crm_for_outlook_short](../includes/pn-crm-for-outlook-short.md)] アドインの詳細については、[Dynamics 365 for Outlook のユーザー ガイド](https://go.microsoft.com/fwlink/p/?LinkID=524751) を参照してください。  
>   
>  [委任されたユーザー](https://support.office.com/article/Allow-someone-else-to-manage-your-mail-and-calendar-9684B670-7588-4EEA-8717-9E5799047540) は、[!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] を使用して電子メールを追跡することはできません。 委任されたユーザーには、[フォルダー レベルの追跡、または自動追跡](https://www.microsoft.com/dynamics/crm-customer-center/overview-of-tracking-records-in-dynamics-365-for-outlook.aspx) の使用をお勧めします。  
  
<a name="BKMK_Compare"></a>   
## <a name="comparing-dynamics-365-app-for-outlook-with-dynamics-365-for-outlook"></a>Dynamics 365 App for Outlook と Dynamics 365 for Outlook の比較  
 次の表は、[!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] 機能を [!INCLUDE[pn_crm_8_2_0_both](../includes/pn-crm-8-2-0-both.md)] の時点での [!INCLUDE[pn_crm_for_outlook_short](../includes/pn-crm-for-outlook-short.md)] ([!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] クライアントまたはアドインとも呼ばれる) と比較したものです。  
  
||||  
|-|-|-|  
|**機能**|**[!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)]**|**[!INCLUDE[pn_crm_for_outlook_short](../includes/pn-crm-for-outlook-short.md)]**|  
|電子メールの追跡および関連の設定|はい|はい|  
|予定の追跡および関連の設定|はい|はい|  
|取引先担当者の追跡および関連の設定|はい|はい|  
|タスクの追跡および関連の設定|いいえ|はい|  
|ワンクリックによる関連の設定|はい|いいえ|  
|受信者の概要の表示|はい|いいえ|  
|電子メール/予定の関連レコード概要の表示|はい|いいえ|  
|[!INCLUDE[pn_outlook_web_app](../includes/pn-outlook-web-app.md)] での作業|はい|いいえ|  
|[!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] デスクトップでの作業|はい|はい|  
|Mac 向け [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] での作業|はい|いいえ|  
|電話での作業|はい|いいえ|  
|[!INCLUDE[pn_microsoftcrm](../includes/pn-microsoftcrm.md)] レコードを直接開き作成する|はい|はい|  
|カスタム フォームおよびビジネス ロジックを適用する|はい|はい|  
|オフライン作業|いいえ|はい|  
|電子メール テンプレートの適用|はい|はい|  
|営業資料の適用|はい|はい|  
|サポート情報記事の適用|はい|はい|  
|送信後の電子メールを監視する機能|はい|いいえ|  
|ビューの並び替え、フィルター、グループ、分類|いいえ|はい|  
|Word の差し込み印刷文書の作成|いいえ|はい|  
|フィールド同期のコントロール|いいえ|はい|  
  
<a name="BKMK_Requirements"></a>   
## <a name="requirements"></a>要件  
 [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] を使用するには、以下が必要です。  
  
-   [!INCLUDE[pn_crm_online_2016_update](../includes/pn-crm-online-2016-update.md)] または [!INCLUDE[pn_crm_8_2_0_both](../includes/pn-crm-8-2-0-both.md)]  
  
-   サーバー側同期による受信メールの同期。 [!INCLUDE[proc_more_information](../includes/proc-more-information.md)][電子メール、予定、取引先担当者、およびタスクのサーバー側同期の設定](../Topic/Set%20up%20server-side%20synchronization%20of%20email,%20appointments,%20contacts,%20and%20tasks.md)  
  
-   以下で説明されている必要な特権  
  
> [!NOTE]
>  [!INCLUDE[pn_dyn_365](../includes/pn-dyn-365.md)] 機能のサポートされている構成と要件が、ドキュメント全体で表示されます。 ドキュメントに文書化されていない特定の構成は、サポートされていないと見なされます。  
  
### <a name="required-privileges"></a>必要な特権  
 [!INCLUDE[pn_microsoftcrm](../includes/pn-microsoftcrm.md)] で [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] にアクセスするには、**Dynamics 365 App for Outlook** 特権が必要です。 ユーザーにこの特権がない場合、次のエラー メッセージが表示されます。  
  
> "このアプリを使用する権限がありません。 システム管理者に問い合わせて、設定を更新してください。"  
  
 ユーザーにはさらに、以下のエンティティに対する読み取り/書き込み特権が必要です。  
  
 [事業部管理] タブ:  
  
-   **メールボックス**  
  
 [カスタマイズ] タブ:  
  
-   **エンティティ**  
  
-   **フィールド**  
  
-   **リレーションシップ**  
  
-   **システム アプリケーション メタデータ**  
  
-   **システム フォーム**  
  
-   **ユーザー アプリケーション メタデータ**  
  
-   **ビュー**  
  
##### <a name="set-the-privileges-for-a-security-role"></a>セキュリティ ロール用の特権の設定  
  
1.  [!INCLUDE[proc_settings_security](../includes/proc-settings-security.md)]  
  
2.  **セキュリティ ロール**をクリックします。  
  
3.  セキュリティ ロールを選択してから、**事業部管理**タブをクリックします。  
  
4.  **エンティティ**セクションで、**メールボックス**特権設定を確認します。 セキュリティ ロールには、ユーザーまたはそれ以上の設定が必要です。  
  
5.  **プライバシーの関連の特権** セクションで、**Dynamics 365 App for Outlook の使用**が**組織**に設定されていることを確認します。 設定されていない場合は、**Dynamics 365 App for Outlook の使用**をクリックします。  
  
### <a name="supported-configurations-with-microsoft-exchange"></a>Microsoft Exchange でサポートされている構成  
 [!INCLUDE[pn_crm_8_2_0_both](../includes/pn-crm-8-2-0-both.md)] については、ハイブリッド構成を含め、[!INCLUDE[pn_crm_online_shortest](../includes/pn-crm-online-shortest.md)] や [!INCLUDE[pn_crm_op_edition](../includes/pn-crm-op-edition.md)]、または [!INCLUDE[pn_Exchange_Online](../includes/pn-exchange-online.md)] や [!INCLUDE[pn_Exchange_Server_short](../includes/pn-exchange-server-short.md)] (on-premises) のすべての組み合わせでアプリを使用できます。 これは次のいずれの構成でも [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] を使用できることを意味します。  
  
|||  
|-|-|  
|[!INCLUDE[pn_crm_online_shortest](../includes/pn-crm-online-shortest.md)]|[!INCLUDE[pn_Exchange_Online](../includes/pn-exchange-online.md)]|  
|[!INCLUDE[pn_crm_online_shortest](../includes/pn-crm-online-shortest.md)]|[!INCLUDE[pn_Exchange_Server_short](../includes/pn-exchange-server-short.md)] (設置型)|  
|[!INCLUDE[pn_crm_op_edition](../includes/pn-crm-op-edition.md)]|[!INCLUDE[pn_Exchange_Server_short](../includes/pn-exchange-server-short.md)] (設置型)|  
|[!INCLUDE[pn_crm_op_edition](../includes/pn-crm-op-edition.md)]|[!INCLUDE[pn_Exchange_Online](../includes/pn-exchange-online.md)]|  
  
> [!NOTE]
>  [!INCLUDE[pn_crm_op_edition](../includes/pn-crm-op-edition.md)] を利用する場合、次の方法で IFD 認証を使用して認証する必要があります。  
  
### <a name="supported-browsers-for-outlook-on-the-web"></a>Outlook on the web 用にサポートされているブラウザー  
 以下のブラウザー上で [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] を [!INCLUDE[pn_outlook_web_app](../includes/pn-outlook-web-app.md)] と共に使用できます。  
  
-   [!INCLUDE[pn_IE_10](../includes/pn-ie-10.md)]、[!INCLUDE[pn_ie_11](../includes/pn-ie-11.md)]、または [!INCLUDE[pn_microsoft_edge](../includes/pn-microsoft-edge.md)]  
  
     以下の構成がサポートされています。  
  
    -   **インターネット** セキュリティ ゾーンで保護モードが有効になっている。 IE 10 または 11 で保護モードを有効にするには、**ツール** > **インターネット オプション** > **セキュリティ タブ** > **インターネット**に移動します。  
  
    -   **ローカル イントラネット** セキュリティ ゾーンで保護モードが有効になっている。 IE 10 または 11 で保護モードを有効にするには、**ツール** > **インターネット オプション** > **セキュリティ タブ** > **ローカル インターネット**に移動します。  
  
    -   [!INCLUDE[pn_dyn_365](../includes/pn-dyn-365.md)] の URL が、**ローカル イントラネット** セキュリティ ゾーンの信頼済みサイトの一覧に含まれている。 IE 10 または 11 では、**ツール** > **インターネット オプション** > **セキュリティ タブ** > **ローカル イントラネット** > **サイト** > **詳細設定**に移動します。  
  
-   [!INCLUDE[pn_ms_Windows_short](../includes/pn-ms-windows-short.md)] での [!INCLUDE[tn_Google_Chrome](../includes/tn-google-chrome.md)] (最新バージョン)  
  
-   [!INCLUDE[pn_ms_Windows_short](../includes/pn-ms-windows-short.md)] での [!INCLUDE[tn_Firefox](../includes/tn-firefox.md)] (最新バージョン)  
  
-   Mac または OSX での [!INCLUDE[tn_apple](../includes/tn-apple.md)] [!INCLUDE[tn_Safari](../includes/tn-safari.md)] (バージョン 9 またはバージョン 10)  
  
### <a name="supported-operating-systems-for-outlook-on-the-desktop"></a>デスクトップ版 Outlook 用にサポートされているオペレーティング システム  
 デスクトップ用 [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] の次のバージョンで [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] を使用できます。  
  
-   [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] 2013 および [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] 2016。  
  
-   Mac 用 [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)]*。  
  
     *[!INCLUDE[pn_Exchange_Server_short](../includes/pn-exchange-server-short.md)] バージョン 15.0.847.32 またはそれ以降が必要です。  
  
### <a name="supported-mobile-devices"></a>サポートされるモバイル デバイス  
 次のいずれかの電話およびオペレーティング システムのモバイル ブラウザーで、[!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] を [!INCLUDE[pn_outlook_web_app](../includes/pn-outlook-web-app.md)] と共に使用できます。  
  
-   iOS バージョン 8、9、または 10 を実行している [!INCLUDE[tn_apple](../includes/tn-apple.md)]​ [!INCLUDE[tn_iphone](../includes/tn-iphone.md)] デバイス。  
  
-   [!INCLUDE[tn_android](../includes/tn-android.md)] 4.4 (KitKat) または 5.0 (Lollipop)、6 (Marshmallow)、または 7 (Nougat) を実行している [!INCLUDE[tn_android](../includes/tn-android.md)] 電話。  
  
-   [!INCLUDE[pn_windows_8_1](../includes/pn-windows-8-1.md)] または [!INCLUDE[pn_windows_10](../includes/pn-windows-10.md)] を実行している [!INCLUDE[pn_windows_phone](../includes/pn-windows-phone.md)] デバイス。  
  
### <a name="supported-clients-per-feature"></a>機能ごとにサポートされているクライアント  
 サポートされる [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] 機能は、実行しているクライアントによって異なります。 次の表は、[!INCLUDE[pn_crm_shortest](../includes/pn-crm-shortest.md)] と [!INCLUDE[pn_Exchange](../includes/pn-exchange.md)] の各クライアント/構成に対してサポートされている機能をまとめたものです。  
  
 ![Dynamics 365 App for Outlook の機能ごとにサポートされているクライアント](media/clients-supported-for-each-dynamics-365-app-for-outlook-feature.png "Dynamics 365 App for Outlook の機能ごとにサポートされているクライアント")  
  
 (1)  [!INCLUDE[pn_outlook_web_app](../includes/pn-outlook-web-app.md)] は [!INCLUDE[pn_IE_10](../includes/pn-ie-10.md)]、[!INCLUDE[pn_ie_11](../includes/pn-ie-11.md)]、[!INCLUDE[pn_microsoft_edge](../includes/pn-microsoft-edge.md)]、[!INCLUDE[tn_Safari](../includes/tn-safari.md)] 9、[!INCLUDE[tn_Safari](../includes/tn-safari.md)] 10、[!INCLUDE[tn_Firefox](../includes/tn-firefox.md)]、および [!INCLUDE[tn_chrome](../includes/tn-chrome.md)] をサポートします。  
  
 (2)  Mobile [!INCLUDE[pn_outlook_web_app](../includes/pn-outlook-web-app.md)] は、[!INCLUDE[pn_windows_8_1](../includes/pn-windows-8-1.md)]、[!INCLUDE[pn_windows_10](../includes/pn-windows-10.md)]、[!INCLUDE[tn_ios](../includes/tn-ios.md)] 8、[!INCLUDE[tn_ios](../includes/tn-ios.md)] 9、[!INCLUDE[tn_ios](../includes/tn-ios.md)] 10、[!INCLUDE[tn_android](../includes/tn-android.md)] KitKat (4.4)、[!INCLUDE[tn_android](../includes/tn-android.md)] Lollipop、[!INCLUDE[tn_android](../includes/tn-android.md)] Marshmallow と [!INCLUDE[tn_android](../includes/tn-android.md)] Nougat をサポートしています。  
  
 (3)  作成モードでの電子メールの追跡および予定の追跡には、[!INCLUDE[pn_Exchange_Server_short](../includes/pn-exchange-server-short.md)] 2013 CU14 または [!INCLUDE[pn_Exchange_Server_short](../includes/pn-exchange-server-short.md)] 2016 が必要です。  
  
 (4)  取引先担当者の追跡は、[!INCLUDE[pn_Exchange_Server_short](../includes/pn-exchange-server-short.md)] 2016 CU3 および [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] 2016 16.0.6741.1000 以降のみでサポートされています。  
  
 (5)  電子メール テンプレート、ナレッジ マネージメント記事、および営業資料は Mobile [!INCLUDE[pn_outlook_web_app](../includes/pn-outlook-web-app.md)] でサポートされていません。  
  
 (6)  [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] 2016 16.0.7426.1049 以降でのみサポートされています。  
  
 (7)  16.0.6741.1000 以降でのみサポートされています。  
  
> [!NOTE]
>  タブレット PC は現時点 (2017 年) ではサポートされていません。  
  
 [サポートされているクライアントに関する詳細をこのブログで読む: Dynamics 365 App for Outlook のサポート マトリックス](https://blogs.msdn.microsoft.com/crm/2016/12/13/dynamics-365-app-for-outlook-support-matrix/)  
  
### <a name="supported-servers"></a>サポートされているサーバー  
 [Office アドインを使用するためのサーバー要件](https://dev.office.com/docs/add-ins/overview/requirements-for-running-office-add-ins) は [!INCLUDE[pn_Exchange_Server_2013_short](../includes/pn-exchange-server-2013-short.md)]、[!INCLUDE[pn_exchange_server_2016_short](../includes/pn-exchange-server-2016-short.md)]、または [!INCLUDE[pn_Exchange_Online](../includes/pn-exchange-online.md)] です。  
  
### <a name="supported-languages"></a>サポートされている言語  
 [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] は、以下の言語をサポートしています。  
  
||||  
|-|-|-|  
|ブルガリア語 (ブルガリア) - 1026|ヒンディー語 (インド) - 1081|ポルトガル語 (ポルトガル) - 2070|  
|中国語 (中華人民共和国) - 2052|ハンガリー語 - 1038|ルーマニア語 - 1048|  
|中国語 (台湾) - 1028|インドネシア語 - 1057|ロシア語 - 1049|  
|クロアチア語 (クロアチア) - 1050|イタリア語 - 1040|セルビア語 - 2074|  
|チェコ語 (チョコ共和国) - 1029|日本語 - 1041|スロバキア語 - 1051|  
|デンマーク語 - 1030|カザフ語 - 1087|スロベニア語 - 1060|  
|オランダ語 - 1043|韓国語 - 1042|スペイン語 - 3082|  
|英語 - 1033|ラトビア語 - 1062|スウェーデン語 - 1053|  
|エストニア語 - 1061|リトアニア語 - 1063|タイ語 - 1054|  
|フィンランド語 - 1035|マレーシア語 - 1086|トルコ語 - 1055|  
|フランス語 - 1036|ノルウェー語 - 1044|ウクライナ語 - 1058|  
|ドイツ語 - 1031|ポーランド語 - 1045|ベトナム語 - 1066|  
|ギリシャ語 - 1032|ポルトガル語 (ブラジル) - 1046||  
  
<a name="BKMK_Deploy"></a>   
## <a name="deploy-dynamics-365-app-for-outlook"></a>Dynamics 365 App for Outlook の展開  
 [!INCLUDE[cc_server_side_synch](../includes/cc-server-side-synch.md)] のセットアップと必要な特権の設定後、[!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] を一部または全部のユーザーにプッシュするか、ユーザーが必要に応じて自分でインストールするようにすることができます。  
  
> [!NOTE]
>  [!INCLUDE[pn_dyn_365_op](../includes/pn-dyn-365-op.md)] を使用している場合は、次のセクションを参照してください: [Dynamics 365 (設置型) ユーザーへの展開方法](#BKMK_DeployOnprem)  
  
#### <a name="to-push-the-app-to-users"></a>アプリをユーザーにプッシュする方法  
  
1.  **設定** >  **Dynamics 365 App for Outlook** に移動します。  
  
2.  **Dynamics 365 App for Outlook の使用の開始**画面の**利用資格があるユーザー用に追加**で (2 回目以降にこの画面を開く場合は、**設定**をクリックすることが必要な場合があります)、ユーザーが自動的にアプリを取得できるようにするには、**自動的に [!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] にアプリを追加する**チェック ボックスをオンにします。 ユーザーに必要な特権があり、電子メールが [!INCLUDE[cc_server_side_synch](../includes/cc-server-side-synch.md)] により同期されている場合、アプリをユーザーにプッシュするためにそれ以上必要な操作はありません。 たとえば、営業担当者ロールに必要な特権を追加してから、新しいユーザーにこのロールを割り当てると、アプリは自動的に取得されます。  
  
3.  次のいずれかを実行します。  
  
    -   すべての利用資格を持つユーザーにアプリをプッシュするには、**利用資格があるすべてのユーザー用のアプリの追加**をクリックします。  
  
    -   特定のユーザーにアプリをプッシュするには、一覧でユーザーを選択してから、**Outlook へのアプリの追加**をクリックします。  
  
    > [!TIP]
    >  一覧でユーザーが保留中またはまだ追加されていないことが示されている場合、ユーザーの横にある**詳細**リンクをクリックすると、状態に関する詳細を確認できます。  
  
4.  終了したら**保存**をクリックします。  
  
#### <a name="to-have-users-install-the-app-themselves"></a>ユーザーが自分でアプリをインストールする方法  
  
1.  ユーザーは**設定**ボタン ![設定ボタン](media/mp-ua-r16-settings.png "設定ボタン") をクリックしてから、**Dynamics 365 用アプリ**をクリックします。  
  
2.  **Dynamics 365 用アプリ**画面の **[!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)]** で、ユーザーは **[!INCLUDE[pn_Outlook_short](../includes/pn-outlook-short.md)] へのアプリの追加**をクリックします。  
  
> [!NOTE]
>  ユーザーは必要に応じて、アドイン自体を自分で無効にすることや削除することもできます。 詳細については、[Dynamics 365 App for Outlook のユーザー ガイド](https://go.microsoft.com/fwlink/p/?LinkID=613099) を参照してください。  
  
<a name="BKMK_DeployOnprem"></a>   
## <a name="to-deploy-to-dynamics-365-on-premises-users"></a>Dynamics 365 (設置型) ユーザーへの展開方法  
 Dynamics 365 (on-premises) を使用している場合は次の手順に従います。  
  
-   Dynamics 365 Server をインターネットに接続する展開用に構成します。 「[Microsoft Dynamics 365 の IFD を構成する](https://technet.microsoft.com/library/dn609803.aspx)」を参照してください。  
  
-   Exchange on-premises に接続する場合は、OAuth プロバイダーを構成してクライアント アプリを登録します。 「[OAuth を使用する Dynamics 365 アプリケーション用に Windows Server 2012 R2 を設定する](https://technet.microsoft.com/library/hh699726.aspx)」を参照してください。  
  
<a name="BKMK_Troubleshoot"></a>   
## <a name="troubleshooting-installation-problems"></a>インストールに関する問題のトラブルシューティング  
 [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] のインストールに関する問題がある場合、[!INCLUDE[pn_Exchange](../includes/pn-exchange.md)] メールボックスが現在別の [!INCLUDE[pn_crm_shortest](../includes/pn-crm-shortest.md)] 組織にリンクされていることが原因である可能性があります。 1 つの [!INCLUDE[pn_Exchange](../includes/pn-exchange.md)] メールボックス (電子メール アドレス) は、1 つの組織とのみ、予定、連絡先、タスクを同期できます。また、その組織に属するユーザーは、予定、連絡先、タスクを 1 つの [!INCLUDE[pn_Exchange](../includes/pn-exchange.md)] メールボックスとのみ同期できます。  プライマリ同期組織を変更したい場合には、[!INCLUDE[pn_Exchange](../includes/pn-exchange.md)] に保存されている設定を上書きできます。 詳細については、[このサポート技術情報の記事](https://support.microsoft.com/en-gb/help/3211627/incomingemailrejected-error-when-attempting-to-install-dynamics-365-app-for-outlook) を参照してください。  
  
<a name="BKMK_Explore"></a>   
## <a name="explore-the-users-guide-and-train-your-users"></a>ユーザー ガイドの説明とユーザーのトレーニング  
 [!INCLUDE[pn_crm_app_for_outlook_short](../includes/pn-crm-app-for-outlook-short.md)] の使用方法については、[Dynamics 365 App for Outlook のユーザー ガイド](https://go.microsoft.com/fwlink/p/?LinkID=613099)を参照してください。  
  
 ![Dynamics 365 App for Outlook ユーザー ガイドのページ](media/dynamics-365-app-for-outlook-user-s-guide-page.png "Dynamics 365 App for Outlook ユーザー ガイドのページ")  
  
## <a name="see-also"></a>関連項目  
 [Dynamics 365 App for Outlook のユーザー ガイド](https://go.microsoft.com/fwlink/p/?LinkID=613099)   
 [サポートされているクライアントに関する詳細をこのブログで読む: Dynamics 365 App for Outlook のサポート マトリックス](https://blogs.msdn.microsoft.com/crm/2016/12/13/dynamics-365-app-for-outlook-support-matrix/)   
 [電子メール、予定、取引先担当者、およびタスクのサーバー側同期の設定](../Topic/Set%20up%20server-side%20synchronization%20of%20email,%20appointments,%20contacts,%20and%20tasks.md)   
 [ユーザー、ライセンス、セキュリティ ロールの追加](https://msdn.microsoft.com/23612155-f92d-4871-a109-186419d5c19d)   
 [相互運用の機能を Microsoft Dynamics 365 (online) に追加する](../DocSets/CRMIGv9_Admin/Toc/Add%20interoperation%20features%20to%20Microsoft%20Dynamics%20365%20\(online\).md)