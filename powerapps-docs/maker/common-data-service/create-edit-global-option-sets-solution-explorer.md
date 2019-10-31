---
title: ソリューション エクスプローラーを使用して、 Common Data Service にグローバル オプション セットを作成、編集する | MicrosoftDocs
ms.custom: ''
ms.date: 05/26/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - PowerApps
ms.author: matp
manager: kvivek
author: Mattp123
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="create-and-edit-global-option-sets-for-common-data-service-using-solution-explorer"></a>ソリューション エクスプローラーを使用して、 Common Data Service にグローバル オプション セットを作成、編集する

ソリューション エクスプローラーは Common Data Service のグローバル オプション セットの作成および編集を行う方法を提供します。

[PowerApps ポータル](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) ではほとんどの一般的なオプションを構成することができますが、ソリューション エクスプローラーを使用して設定する必要があるオプションもあります。 <br />詳細: 
- [Common Data Service のグローバル オプション セットの作成および編集](create-edit-global-option-sets.md)
- [オプション セットの作成](custom-picklists.md)

## <a name="open-solution-explorer"></a>ソリューション エクスプローラーを開きます

作成するグローバル オプション セットの名前の一部はカスタマイズの接頭辞です。 これは、作業中のソリューションの発行者に基づいて設定されます。 カスタマイズの接頭辞に注意を払う場合は、カスタマイズの接頭辞がこのグローバル オプション セットに対して必要な接頭辞であるアンマネージド ソリューションで作業するようにします。 詳細: [ソリューション発行者の接頭辞を変更する](change-solution-publisher-prefix.md) 

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

## <a name="view-global-option-sets"></a>グローバル オプション セットを表示

ソリューション エクスプローラーを開いた状態で、**コンポーネント**下の**オプション セット**を選択します。

![グローバル オプション セットを表示](media/view-global-option-sets-solution-explorer.png)

> [!NOTE]
> 一部のシステム グローバル オプション セットはカスタマイズできません。 これらのオプションは更新や新しいバージョンにより変更がされるため、ご利用に当たっての要件と Common Data Service の値の使用方法が一致していることが定かでない場合は、これをご利用にならないことを推奨します。

## <a name="create-a-global-option-set"></a>グローバル オプション セットの作成

> [!NOTE]
> カスタム フィールド内で使用する前に、グローバル オプション セットを作成する必要はありません。 新しいオプション セット フィールドを作成する場合、新しいグローバル オプション セットを作成するか、または既存のものを使用するか選ぶことができます。 [オプション セット フィールド オプション](create-edit-field-solution-explorer.md#option-set-field-options) を参照

グローバル オプション セットが表示されているとき、グローバル オプション セットを定義するには**新しい**をクリックしフォームを開きます。

![グローバル オプション セットの作成](media/create-global-option-set-solution-explorer.png)

使用する新しいフィールドを定義するとき、このグローバル オプション セットを選ぶシステム管理者またはカスタマイザー ロールを持つユーザーに表示される**表示名**を入力してください。 この名前はアプリケーションを使用しているユーザーに対して表示されません。

**名前**フィールドは、入力した**表示名**に基づいて生成されます。 作業中ソリューションのコンテキストで、ソリューション発行者のカスタマイズの接頭辞が含まれます。 保存する前に、**名前**フィールド値の生成された一部を変更できます。

グローバル オプション セットの**説明**を入力します。 

> [!TIP]
> このグローバル オプション セットの目的を記述するには、**説明**を使用します。 この値は、アプリケーションのユーザーに対してではなく、特定のグローバル オプション セットが作成された理由を知りたいシステム管理者またはカスタマイザー ロールを持つ他のユーザーに表示されます。

### <a name="configure-options"></a>オプションの構成

[!INCLUDE [cc_configure-option-set-options-solution-explorer](../../includes/cc_configure-option-set-options-solution-explorer.md)]

## <a name="edit-a-global-option-set"></a>グローバル オプション セットの編集

グローバル オプション セットが表示されているとき、編集するパネルを開くよう編集したいオプション セットを選択します。

オプションに割り当てられた**名前**フィールドの値または件数の**値**の変更を除いて、グローバル オプション セットを作成するときにできることは何でも可能です。

[!INCLUDE [cc_remove-option-warning](../../includes/cc_remove-option-warning.md)]

## <a name="delete-a-global-option-set"></a>グローバル オプション セットの削除

グローバル オプション セットを削除するには、リストを表示して次を選択します ![削除コマンド](media/delete.gif) コマンド バーのコマンドにあります。

> [!IMPORTANT]
> グローバル オプション セットをフィールドで使用している場合は、そのフィールドが削除されるまで、削除できません。
  
### <a name="see-also"></a>関連項目
 
[Common Data Service のグローバル オプション セットの作成および編集](create-edit-global-option-sets.md)<br />
[オプション セットの作成](custom-picklists.md)<br />
[フィールドの作成および編集](create-edit-fields.md)<br />
[開発者ドキュメント: グローバル オプション セットのカスタマイズ](/dynamics365/customer-engagement/developer/org-service/customize-global-option-sets)
