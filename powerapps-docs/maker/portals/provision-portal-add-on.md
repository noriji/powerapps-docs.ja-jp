---
title: 以前のポータルアドオンを使用してポータルをプロビジョニングする |MicrosoftDocs
description: 以前のポータルアドオンを使用してポータルをプロビジョニングする方法について説明します。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 6572a92a46fa308eab6cb46b813a572605327197
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2019
ms.locfileid: "73550981"
---
# <a name="provision-a-portal-using-the-older-portal-add-on"></a>以前のポータルアドオンを使用してポータルをプロビジョニングする

古いポータルアドオンを購入し、アドオンを使用してポータルをプロビジョニングする場合は、 **Dynamics 365 管理センター**のページにアクセスしてポータルをプロビジョニングする必要があります。

> [!NOTE]
> ポータルをプロビジョニングするには、ポータルで選択した Common Data Service 環境の [システム管理者] または [システムカスタマイザー] のいずれかのロールが割り当てられている必要があります。 Azure AD でアプリケーションを作成および登録するために[必要なアクセス許可](https://docs.microsoft.com/azure/active-directory/develop/howto-create-service-principal-portal#required-permissions)も必要です。 必要なアクセス許可がない場合は、全体管理者に連絡してアクセス許可を更新するか、全体管理者にポータルのプロビジョニングを依頼してください。

ポータルをプロビジョニングするには:

1.  **Dynamics 365 管理センター**のページにアクセスし、 **[アプリケーション]** タブを選択します。

2.  **ポータルアドオン** というタイトルのアプリケーション行を選択し、管理 を選択し**ます。**

3.  **[全般設定**] セクションで、ポータルの**名前**を入力します。 **名前**はポータルを識別するのに役立ち、後で変更できます。

4.  **Type**フィールドは、ポータルサブスクリプション (試用版または運用環境) の種類を表します。 これはシステムフィールドなので、ユーザーが変更することはできません。 値は、試用版サブスクリプションと有料サブスクリプションのどちらであるかに基づいて変化します。

5. 必要に応じて、 **[ポータル開発の状態]** ドロップダウンリストで、ポータルの次のいずれかの開発状態を選択します。

    - プロトタイプ
    - モーター
    - Test
    - UAT
    - 居住

    > [!NOTE]
    > - 既存のプロビジョニング済みポータルの場合、このドロップダウンリストはポータルの **[詳細]** タブで利用でき、既定では状態は選択されていません。
    > - このドロップダウンリストは、種類が [運用] のポータルに対してのみ使用できます。
    > - このフィールドは、このポータルの使用パターンを理解するために Microsoft によって使用され、どの機能にも影響しません。 開発ライフサイクルに別の名前を使用する場合は、目的に近いものを選択してください。 ポータルがプロビジョニングされると、後でこの設定を変更できます。

5.  **[ポータルの URL]** フィールドに、ポータルに使用するサブドメイン名を入力します。 使用できるのは英数字またはハイフン (-) のみです。その他の文字は使用できません。

    > [!NOTE]
    > - ポータルのプロビジョニング後にポータルの URL を変更する方法については、「[ポータルのベース url を変更](admin/change-base-url.md)する」を参照してください。
    > - ポータルをカスタムドメインにリンクするには、「[ポータルをカスタムドメインにリンク](admin/add-custom-domain.md)する」を参照してください。

6.  **[Dynamics 365 インスタンス]** ドロップダウンリストで、ポータルのリンク先となるインスタンスを選択します。 これには、選択したインスタンスでシステム管理者またはシステムカスタマイザーの役割が必要です。

7.  **[ポータルの言語の選択**] ドロップダウンリストで、ポータルの既定の言語を選択します。 使用できる言語は、インスタンスにインストールされている言語によって異なります。 

    > [!NOTE]
    > サンプルデータは1つの言語でのみ提供されるため、既定の言語を選択すると、サンプルデータの変換方法も決定されます。 アラビア語およびヘブライ語はサポートされていないため、一覧に表示されません。

8. **[ポータル管理者の選択**] ドロップダウンリストで、ポータルの構成、カスタマイズ、および管理を行うユーザーを選択します。 組織内のシステム管理者の役割を持つすべてのユーザーが、オプションとして表示されます。 

9. **[ポータルユーザー]** セクションで、新しいポータルにアクセスする対象ユーザーの種類を選択します。 これにより、提供されるポータルのオプションが決まります。 次のいずれかを選択できます。

    -   Partner    
        -   カスタマーセルフサービスポータル
        -   カスタムポータル
        -   パートナーポータル
        -   パートナープロジェクトサービス (オプション、インストールされているソリューションが必要)
        -   パートナーフィールドサービス (オプション、インストールされているソリューションが必要)
        -   コミュニティポータル

    -   Customer
        -   カスタマーセルフサービスポータル
        -   カスタムポータル
        -   コミュニティポータル

    -   Employee
        -   従業員セルフサービスポータル

10. **[デプロイするポータルの選択**] セクションで、作成するポータルの種類を選択します。 表示されるオプションは、選択した対象ユーザーによって異なります。

    > [!div class="mx-imgBorder"]
    > ![ポータルの設定を構成する](media/configure-settings-portal.png "ポータルの設定を構成する")  

11. **[送信]** を選択し、サービス利用規約に同意します。
    > [!div class="mx-imgBorder"]
    > ![サービス利用規約](media/terms-of-service.png "サービス利用規約")  

サービス利用規約に同意すると、ポータルでプロビジョニングが開始されます。 通常、プロビジョニングには30分かかりますが、システムの負荷によっては数時間かかることがあります。 [アプリケーション] タブのポータルの*名前*は、プロビジョニング中の*名前*に変わります。 ポータルの管理ページに戻り、プロビジョニングが成功したかどうかを確認します。

ポータルがプロビジョニングされると、**ポータルの詳細**ページが表示され、必要な詳細情報が表示されます。

> [!div class="mx-imgBorder"]
> ![ポータルの詳細](media/portal-details-prov.png "ポータルの詳細") 


> [!Note]
> ポータルユーザーが Azure AD 資格情報を使用して初めてポータルにサインインすると、ユーザーまたはポータルの種類に関係なく、すべてのユーザーに同意ページが表示されます。

次の表は、各ポータルオプションに関連する機能をまとめたものです。

| 機能                                | 顧客セルフサービスポータル | パートナーポータル | 従業員セルフサービスポータル | コミュニティポータル | カスタムポータル |
|----------------------------------------|------------------------------|----------------|------------------------------|------------------|---------------|
| 国際対応                            | •                            | •              | •                            | •                | •             |
| 複数言語のサポート                 | •                            | •              | •                            | •                | •             |
| ポータルの管理                  | •                            | •              | •                            | •                | •             |
| カスタマイズと拡張性        | •                            | •              | •                            | •                | •             |
| テーマ                                | •                            | •              | •                            | •                | •             |
| コンテンツ管理                     | •                            |                | •                            | •                |               |
| ナレッジ管理                   | •                            | •              | •                            | •                |               |
| サポート/ケース管理                | •                            |                | •                            | •                |               |
| フォーラム                                 | •                            |                | •                            | •                |               |
| ファセット検索                         | •                            |                | •                            |                  |               |
| プロファイルの管理                     | •                            |                | •                            |                  |               |
| フォーラムスレッドの購読              | •                            |                | •                            |                  |               |
| Comments                               | •                            |                | •                            | •                |               |
| [!INCLUDE[pn-azure-shortest](../../includes/pn-azure-shortest.md)] AD 認証                |                              |                | •                            |                  |               |
| よい                                  |                              |                |                              | •                |               |
| Blog                                  |                              |                |                              | •                |               |
| Project Service Automation の統合 |                              | •              |                              |                  |               |
| フィールドサービスの統合              |                              | •              |                              |                  |               |
| パートナーのオンボード                     |                              | •              |                              |                  |               |
| ポータルベース                            |  •                           | •              |  •                           | •                | •             |
| ポータルのワークフロー                       |  •                           | •              |  •                           | •                | •             |
| Web 通知                      |  •                           | •              |  •                           | •                | •             |
| [!INCLUDE[cc-microsoft](../../includes/cc-microsoft.md)] Id                     |     •                         |  •              |     •                         |   •               | •             |
| Id ワークフロー                     | •                            |  •             |     •                         |   •               | •             |
| Web フォーム                              |  •                            | •               |    •                          | •                 | •             |
| 皆様                               |   •                           |  •              |  •                            | •                 | •             |
||

## <a name="troubleshoot-provisioning"></a>プロビジョニングのトラブルシューティング

パッケージのインストールプロセスまたは URL の作成プロセスでエラーが発生することがあります。このような場合は、プロセスを再起動できます。

名前の変更を構成するときに*名前*を変更できなかっ*た場合は*、プロビジョニングプロセスを再起動する必要があります。

1. **[アプリケーション]** ページにアクセスして、ポータルを選択します。
2. **[管理]** というラベルの青い鉛筆ボタンを選択します。
3. 次のいずれかのオプションを選択します。

   - **プロビジョニングの再開**: 以前に定義された構成を使用してインストールプロセスを再起動します。

   - **値の変更とプロビジョニングの再開**: プロビジョニングプロセスを再起動する前に、一部の値を変更できます。

パッケージのインストールが失敗した場合、問題なくポータル管理者のページが開きますが、実際のポータル URL に移動すると、メッセージが設定されます。 確認するには:

1. **Dynamics 365 管理センター**ページの [ソリューションの管理] ページにアクセスして、パッケージの状態が [**インストールに失敗しまし**た] になっていることを確認します。 

2. パッケージの状態が **インストール失敗** の場合は、ソリューション ページからインストールを再試行してください。 また、システム管理者が既定の言語を使用してソリューションをインストールしていることを必ず確認してください Common Data Service は、ポータルをインストールする言語に設定します。

> [!NOTE]
> 一部のソリューションにはインストールの前提条件があるため、前提条件が満たされていない場合、インストールは失敗します。 たとえば、パートナーポータルのパートナーフィールドサービスをインストールするには、パートナーポータルとフィールドサービスソリューションが既にインストールされている必要があります。 最初に Partner Field サービスをインストールしようとすると、インストールは失敗し、エラーメッセージが表示されます。
