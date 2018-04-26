---
title: ルックアップ フィールド経由でのエンティティのリレーションシップのクイック スタート | Microsoft Docs
description: ルックアップ フィールドを使ってエンティティ間のリレーションシップを作成するクイック スタートです。
documentationcenter: na
author: clwesene
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: cds
ms.date: 3/21/2018
ms.author: clwesene
ms.openlocfilehash: a607058d1e26f37a4bffa054d9dc148be8b6b011
ms.sourcegitcommit: 8bd4c700969d0fd42950581e03fd5ccbb5273584
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="quickstart-create-a-relationship"></a>クイック スタート: リレーションシップを作成する
エンティティのデータに、別のエンティティのデータとの関連性があることは少なくありません。 たとえば、**Teachers** エンティティと **Class** エンティティがあり、**Class** エンティティには担当教師を示すために **Teachers** エンティティへのルックアップ リレーションシップがあるような場合です。 ルックアップ フィールドを使うと、**Teachers** エンティティからのデータを表示できます。 これは、一般にルックアップ フィールドと呼ばれます。

## <a name="define-a-relationship"></a>リレーションシップの定義
2 つのエンティティ間 (または同じエンティティ間) で作成できるリレーションシップには、いくつかの種類があります。 1 つのエンティティは、複数のエンティティとのリレーションシップを持つことができます。また、1 つのエンティティが、別のエンティティに対して複数のリレーションシップを持つこともできます。 以下に、いくつかの一般的なリレーションシップの種類を示します。


* **多対一** - このタイプのリレーションシップでは、エンティティ A の各レコードは、エンティティ B の複数のレコードと対応関係を持つことができます。一方、エンティティ B の各レコードは、エンティティ A の 1 件のレコードに対してしか対応関係を持つことができません。たとえば、クラスに教室が 1 つしかないような場合です。 これは最も一般的なリレーションシップの種類であり、フィールド リストでは**ルックアップ フィールド**として表示されます。
* **一対多** - このタイプのリレーションシップでは、エンティティ B の各レコードは、エンティティ A の複数のレコードと対応関係を持つことができます。一方、エンティティ A の各レコードは、エンティティ B の 1 件のレコードに対してしか対応関係を持つことができません。たとえば、1 人の教師が多数のクラスを教えているような場合です。
* **多対多** - このタイプのリレーションシップでは、エンティティ A の各レコードが、エンティティ B の複数のレコードと対応関係を持つことができます (その逆も同様)。 たとえば、1 人の学生が多数のクラスに出席し、各クラスに複数の学生がいるような場合です。

## <a name="add-a-lookup-field-many-to-one-relationship"></a>ルックアップ フィールドを追加する (多対一のリレーションシップ)

エンティティにルックアップ リレーションシップを追加するには、**[リレーションシップ]** タブでリレーションシップを作成し、リレーションシップを作成するエンティティを指定します。

1. [powerapps.com](https://web.powerapps.com) で、**[データ]** セクションを展開し、左側のナビゲーション ウィンドウで **[エンティティ]** をクリックまたはタップします。

    ![エンティティの詳細](./media/data-platform-cds-create-entity/entitylist.png "エンティティの一覧")

2. 既存のエンティティまたは [[新しいエンティティを作成する]](data-platform-create-entity.md) を、タップまたはクリックします。

3. **[リレーションシップ]** をクリックします。

4. **[リレーションシップの追加]** をクリックします。新しいパネルが開き、リレーションシップを作成するエンティティを選ぶことができます。 **[関連エンティティ]** ドロップダウンからエンティティを選びます。

    ![多対一のリレーションシップ](./media/data-platform-cds-newrelationship/manytoone-1.png "多対一のリレーションシップ")

5. エンティティを選ぶと、プライマリ エンティティにルックアップ フィールドが表示されます。既定ではエンティティ名 (この例では Classroom) ですが、必要に応じて変更できます。

    ![多対一のリレーションシップ](./media/data-platform-cds-newrelationship/manytoone-2.png "多対一のリレーションシップ")

6. **[完了]** をクリックしてエンティティにリレーションシップを追加してから、**[エンティティの保存]** をクリックします。

    ![多対一のリレーションシップ](./media/data-platform-cds-newrelationship/manytoone-3.png "多対一のリレーションシップ")

## <a name="add-a-one-to-many-relationship"></a>一対多のリレーションシップを追加する

一対多のリレーションシップを追加するには、**[リレーションシップ]** タブでリレーションシップを作成し、リレーションシップを作成するエンティティを指定します。

1. [powerapps.com](https://web.powerapps.com) で、**[データ]** セクションを展開し、左側のナビゲーション ウィンドウで **[エンティティ]** をクリックまたはタップします。

    ![エンティティの詳細](./media/data-platform-cds-create-entity/entitylist.png "エンティティの一覧")

2. 既存のエンティティまたは [[新しいエンティティを作成する]](data-platform-create-entity.md) を、タップまたはクリックします。

3. **[リレーションシップ]** をクリックします。

4. **[リレーションシップの追加]** の右側にある下向き矢印をクリックすると、両方の種類のリレーションシップの選択肢が表示されます。 **[一対多]** をクリックします。新しいパネルが開き、リレーションシップを作成するエンティティを選ぶことができます。 **[関連エンティティ]** ドロップダウンからエンティティを選びます。

    ![一対多のリレーションシップ](./media/data-platform-cds-newrelationship/onetomany-1.png "一対多のリレーションシップ")

5. エンティティを選ぶと、プライマリ エンティティにルックアップ フィールドが表示されます。既定ではエンティティ名 (この例では Class) ですが、必要に応じて変更できます。

    > [!NOTE]
    > 一対多のリレーションシップでは、ルックアップ フィールドは、現在選択されているエンティティではなく、関連するエンティティに作成されます。 現在のエンティティにルックアップが必要な場合は、多対一リレーションシップを作成してください。

    ![一対多のリレーションシップ](./media/data-platform-cds-newrelationship/onetomany-2.png "一対多のリレーションシップ")

6. **[完了]** をクリックしてエンティティにリレーションシップを追加してから、**[エンティティの保存]** をクリックします。

    ![一対多のリレーションシップ](./media/data-platform-cds-newrelationship/onetomany-3.png "一対多のリレーションシップ")

## <a name="add-a-many-to-many-relationship"></a>多対多のリレーションシップを追加する

現在、多対多のリレーションシップは [詳細] メニューからのみ使用できます。 PowerApps のホーム ページで、左側のメニューから [詳細] をクリックします。 リレーションシップの作成方法について詳しくは、「[N:N (多対多) の関連付けを作成する](/dynamics365/customer-engagement/customize/create-and-edit-nn-many-to-many-relationships)」をご覧ください。

## <a name="use-a-lookup-field-in-an-app"></a>アプリでのルックアップ フィールドの使用
ルックアップ フィールドを含むエンティティから[自動的にアプリを作成](../canvas-apps/data-platform-create-app.md)した場合、そのエンティティは**ドロップダウン** コントロールとして表示され、エンティティの**プライマリ名** フィールドからのデータを含みます。

## <a name="next-steps"></a>次の手順
* [Common Data Service データベースを使用してアプリを生成する](../canvas-apps/data-platform-create-app.md)
* [Common Data Service データベースを使用してアプリを最初から作成する](../canvas-apps/data-platform-create-app-scratch.md)
