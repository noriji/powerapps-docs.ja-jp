---
title: 環境に応じた作業 | Microsoft Docs
description: 環境を切り替えて、ページ上の内容がどのように変わるかを理解しましょう。
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/14/2016
ms.author: litran
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 9cff6054c9c238aeceaff63b5f178f5db3b16727
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2019
ms.locfileid: "73542326"
---
# <a name="working-with-environments-and-microsoft-powerapps"></a>Microsoft PowerApps で環境を使用する
PowerApps では、異なる環境での作業が可能で、それらを簡単に切り替えることができます。 環境の概要については、[環境の概要](../../administrator/environments-overview.md) を参照してください。なぜ複数環境を使うのか、どのように環境の作成と管理を行えばよいか、を詳しく説明しています。 この記事では、環境に関する次のトピックを取り上げます。

- 環境を powerapps.com に切り替える方法
- 適切な環境でアプリを作成する方法
- 適切な環境でアプリを表示する方法

## <a name="switch-the-environment"></a>環境を切り替える
サインアップして最初に PowerApps にサインインすると、既定の環境で開かれます。これは、ページの右上隅で確認できます。

> [!div class="mx-imgBorder"]
> 既定の環境](./media/working-with-environments/env-dropdown.png) の ![

組織内のすべてのユーザーが既定の環境にアクセスできます。 この環境でアプリを作成し、他のユーザーとアプリを共有できます。 また、他の環境を[作成する](../../administrator/environments-administration.md)かどうかに関係なく、他の環境にアクセスすることもできます。 環境を切り替えるには、右上隅にある [環境] の一覧を開き、別の環境を選択します。 この例は、 **Microsoft**から**MyOwnEnv**への切り替えを示しています。

> [!div class="mx-imgBorder"]
> ![スイッチ環境](./media/working-with-environments/switch-environment.png)

環境を切り替えた後、新しい環境には、その環境でアクセスできるすべてのアプリが表示されます。

## <a name="create-apps-in-the-right-environment"></a>適切な環境でアプリを作成する
ご自分で作成する環境、またはアクセス権が付与されている環境でアプリを作成することができます。 ただし、独自の環境を作成するには、[具体的なプラン](../../administrator/pricing-billing-skus.md)が必要です。 アプリを作成する前に、必ず **アプリに使用する正しい環境を選択しているかどうか確認**します。 そうしないと、環境間でのアプリの移行処理が必要になります。

適切な環境でアプリを作成するには、次のようにします。

1. [PowerApps にサインインします](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)。

1. 前のセクションで説明したように、アプリを作成する環境を選択します。

1. 左端近くにある **[アプリ]** を選択し、 **[アプリの作成]** を選択します。

## <a name="view-apps-in-the-right-environment"></a>適切な環境でアプリを作成する
[powerapps.com](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) と PowerApps Studio のどちらで作業しているかに関係なく、アプリや接続などの一覧は常に、ドロップダウン リストで選択されている環境に基づいてフィルター表示されます。 探しているアプリが表示されない場合は、適切な環境が選択されているかどうかを必ず確認してください。

環境の詳細については、 [この概要](../../administrator/environments-overview.md)を参照してください。
