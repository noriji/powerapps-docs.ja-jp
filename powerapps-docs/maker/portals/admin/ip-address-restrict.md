---
title: IP アドレス | を使用してポータルへのアクセスを制限するMicrosoftDocs
description: IP アドレスによってポータルアクセスを制限する手順。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: da8e6ac6d4e86a12ba196393073706c3705e4a92
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2019
ms.locfileid: "73543015"
---
# <a name="restrict-portal-access-by-ip-address"></a>ポータルアクセスを IP アドレスで制限する

ポータルは、任意のコンピューターのすべてのユーザーによってプロビジョニングされ、アクセスできる場合にパブリックになります。 これで、IP アドレスの一覧からポータルへのアクセスを制限できるようになりました。 たとえば、政府組織は、自社の企業ネットワーク内にのみコンテンツを公開したい場合があります。 商用組織では、データの漏洩を防ぐために、ポータルを公開したときにのみポータルを表示し、開発中には表示しないようにすることができます。

ポータルへの要求が任意のユーザーから生成されると、その IP アドレスが許可リストに対して評価されます。 IP アドレスが一覧に表示されていない場合、ポータルには HTTP 403 ステータスコードを含む web ページが表示されます。

IP アドレスを追加または削除するには、次のいずれかのロールが割り当てられている必要があります。
- Office 365 全体管理者 
- サービス管理者。 詳細情報:[サービス管理者ロールを使用してテナントを管理する](https://technet.microsoft.com/library/mt793847.aspx)  
- ポータル用に選択された Common Data Service 環境のシステム管理者

## <a name="add-an-ip-address"></a>IP アドレスを追加する

Ip アドレスまたは一連の IP アドレスからポータルにアクセスできるようにするには、IP アドレスを一覧に追加します。 これにより、追加された IP アドレスの一覧からのみポータルにアクセスできるようになります。 IP アドレスを追加しない場合、ポータルにはすべての IP アドレスからアクセスできるようになります。

制限リストに IP アドレスを追加すると、指定した IP アドレスのみにポータルにアクセスできるようになります。 他の IP アドレスからポータルにアクセスしようとすると、アクセスが拒否され、HTTP 403 状態コードを含む web ページが表示されます。 この web ページの内容は静的であり、変更することはできません。

> [!div class=mx-imgBorder]
> ![HTML 403 エラー](../media/ip-address-page-error.png "HTML 403 エラー")  

> [!NOTE]
> ポータルからアクセスできるパブリック IP アドレスを指定する必要があります。 ポータルでプライベート IP アドレスにアクセスすることはできません。

1.  [PowerApps ポータル管理センター](admin-overview.md)を開きます。

2.  **IP アドレス制限の設定**に関するページを参照してください。 IP アドレスとその種類の一覧が表示されます。

    > [!div class=mx-imgBorder]
    > ![IP アドレスの制限を設定する](../media/set-up-ip-address-restrict.png "IP アドレス制限を設定する")

3.  IP アドレス制限の設定 ページで、**新規追加** を選択します。

4.  [IP アドレスの追加] ウィンドウで、次の値を入力します。

    - **Ip アドレスの種類の選択**: ip アドレスが IPv4 と IPv6 のどちらであるかを選択します。

    - **Ip アドレスを cidr 表記で指定する**: ip アドレスを cidr 表記で指定します。 詳細情報:[クラスレスドメイン間ルーティング](https://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing)

      > [!div class=mx-imgBorder]
      > ![IP アドレスを追加する](../media/add-ip-address.png "IP アドレスを追加する")    

5.  **[構成]** を選択します。

## <a name="remove-an-ip-address"></a>IP アドレスを削除する

以前に許可されていた IP アドレスからポータルへのアクセスを削除するには、一覧から IP アドレスを削除します。 すべての IP アドレスを削除すると、ポータルにすべての IP アドレスからアクセスできるようになります。

1.  [PowerApps ポータル管理センター](admin-overview.md)を開きます。

2.  **IP アドレス制限の設定**に関するページを参照してください。 IP アドレスとその種類の一覧が表示されます。

    > [!div class=mx-imgBorder]
    > ![IP アドレスの制限を設定する](../media/set-up-ip-address-restrict.png "IP アドレス制限を設定する")

3.  削除する IP アドレスの横にある [ **ip アドレス (x) を削除**する] を選択します。

4.  確認メッセージで **[削除]** を選択します。

