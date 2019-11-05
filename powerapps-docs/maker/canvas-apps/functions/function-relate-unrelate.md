---
title: 関連付けと非関連付け関数 |Microsoft Docs
description: 構文と例を含む PowerApps の関連付け関数と関連付け解除関数の参照情報
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 01/22/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: ca0b81cb1150fb744251b3dfca30c9b6ed8f90a5
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2019
ms.locfileid: "73537103"
---
# <a name="relate-and-unrelate-functions-in-powerapps"></a>PowerApps の関連付け関数と関連付け解除関数

一対多または多対多のリレーションシップを通じて、2つのエンティティのレコードを関連付けると、関連付けを解除します。

## <a name="description"></a>Description

**関連付け**関数は、Common Data Service で一対多または多対多のリレーションシップを介して2つのレコードをリンクします。 **Unrelate**関数はプロセスを反転し、リンクを削除します。

一対多のリレーションシップの場合、多くのエンティティには、1つのエンティティのレコードを指す外部キーフィールドがあります。 **関連付け**このフィールドは、1つのエンティティの特定のレコードをポイントするように設定されますが、[**関連付け**解除] を指定すると、このフィールドは*空白*に設定されます。 **関連付け**が呼び出されたときにフィールドが既に設定されている場合、新しいリンクを優先するため、既存のリンクは失われます。 このフィールドは、 [**Patch**](function-patch.md)関数または **[Edit form](../controls/control-form-detail.md)** コントロールを使用して設定することもできます。**関連付け**関数を使用する必要はありません。

多対多リレーションシップの場合、レコードをリンクするシステムは非表示の結合テーブルを保持します。 この結合テーブルに直接アクセスすることはできません。一対多のプロジェクションを通じてのみ読み取り可能で、**関連付け**関数と**unrelate**関数を使用して設定できます。 関連エンティティに外部キーがありません。

最初の引数で指定したエンティティのデータは、変更を反映して更新されますが、2番目の引数で指定したエンティティのデータは更新されません。 操作の結果を表示するには、そのデータを **[Refresh](function-refresh.md)** 関数で手動で更新する必要があります。

これらの関数は、レコードを作成したり削除したりすることはありません。 既に存在する2つのレコードのみを関連付けるか、関連付けを解除します。

これらの関数は、動作の[数式](../working-with-formulas-in-depth.md)でのみ使用できます。

> [!NOTE]
> これらの関数はプレビュー機能に含まれており、その動作は、**リレーショナルデータ、オプションセット、およびその他の cd**機能の新機能が有効になっている場合にのみ使用できます。 これは、新しいアプリで既定で有効になるアプリレベルの設定です。 この機能スイッチを見つけるには、 **[ファイル]** メニューの **[アプリの設定]** を選択し、 **[詳細設定]** を選択します。 お客様のフィードバックは弊社にとって非常に重要です。ご意見を [PowerApps コミュニティ フォーラム](https://powerusers.microsoft.com/t5/Expressions-and-Formulas/bd-p/How-To)にお寄せください。

## <a name="syntax"></a>構文

**関連付け**( *Entity1RelatedTable*、 *Entity2Record* )

* *Entity1RelatedTable* -必須。 *Entity1*のレコードの場合、 *Entity2*のテーブルは、一対多または多対多のリレーションシップによって関連付けられています。
* *Entity2Record* -必須。 リレーションシップに追加する*Entity2*レコード。

**関連付け**解除 ( *Entity1RelatedTable*、 *Entity2Record* )

* *Entity1RelatedTable* -必須。 *Entity1*のレコードの場合、 *Entity2*のテーブルは、一対多または多対多のリレーションシップによって関連付けられています。
* *Entity2Record* -必須。 リレーションシップから削除する*Entity2*レコード。

## <a name="examples"></a>例

[PowerApps ポータルのエンティティビューアー](../../common-data-service/create-edit-entities-portal.md)に表示される次のようなリレーションシップを持つ**Products**エンティティを考えてみましょう。

| リレーションシップの表示名 | 関連エンティティ | リレーションシップの種類 |
| --- | --- |
| 製品の予約 | 引当 | 1対多 |
| 製品 &harr; 連絡先 | お問い合わせ | 多対多 |

**製品**と**予約**は、一対多のリレーションシップによって関連付けられています。  **予約**エンティティの最初のレコードを**Products**エンティティの最初のレコードと関連付けるには、次のようにします。

`Relate( First( Products ).Reservations, First( Reservations ) )`

これらのレコード間のリレーションシップを削除するには、次の手順を実行します。

`Unrelate( First( Products ).Reservations, First( Reservations ) )`

レコードを作成または削除しても、レコード間のリレーションシップのみが変更されました。

**製品**と**連絡先**は、多対多のリレーションシップによって関連付けられています。  **Contacts**エンティティの最初のレコードを**Products**エンティティの最初のレコードと関連付けるには、次のようにします。

`Relate( First( Products ).Contacts, First( Contacts ) )`

多対多リレーションシップは対称であるため、逆方向にもこれを行うことができます。

`Relate( First( Contacts ).Products, First( Products ) )`

これらのレコード間のリレーションシップを削除するには、次の手順を実行します。

`Unrelate( First( Products ).Contacts, First( Contacts ) )`

もしくは

`Unrelate( First( Contacts ).Products, First( Products ) )`

この後の手順では、これらのエンティティに対してこれらの操作を行います。これらの操作は、関連するレコードを選択するために、**ギャラリー**コントロールと**コンボボックス**コントロールを持つアプリを使用します。

これらの例は、環境にインストールされているサンプルデータによって異なります。 [サンプルデータを含む試用環境を作成](../../model-driven-apps/overview-model-driven-samples.md#get-sample-apps)するか、[既存の環境にサンプルデータを追加](../../model-driven-apps/overview-model-driven-samples.md#install-or-uninstall-sample-data)します。

### <a name="one-to-many"></a>1対多

#### <a name="relate-function"></a>**関連付け**関数

まず、製品に関連付けられている予約を表示および再割り当てする単純なアプリを作成します。

1. [タブレットアプリを空白から](../data-platform-create-app-scratch.md)作成します。

1. **[ビュー]** タブで **[データソース]** を選択します。

1. **データ** ウィンドウで、**データ > ソースの追加** を選択し**Common Data Service** > **Products** > **Connect** を選択します。  

    Products エンティティは、上記で読み込まれたサンプルデータの一部です。

     ![Products エンティティをデータソースとして追加する](media/function-relate-unrelate/products-connect.png)

1. **[挿入]** タブで、空の垂直 **[ギャラリー](../controls/control-gallery.md)** コントロールを追加します。

1. 追加したコントロールに**gallery1.selected**という名前が付けられていることを確認し、画面の左側に収まるように移動してサイズを変更します。

1. **[プロパティ]** タブで、 **gallery1.selected**の**Items**プロパティを**Products**に設定し、その**レイアウト**を [**画像] と [タイトル**] に設定します。

    ![製品ギャラリーの構成](media/function-relate-unrelate/products-gallery.png)

1. **Gallery1.selected**で、 **Label**コントロールの名前が**Title1**であることを確認し、その**Text**プロパティを**ThisItem.Name**に設定します。

    ![Gallery1.selected でラベルを構成する](media/function-relate-unrelate/products-title.png)

1. 次の項目が**gallery1.selected**に挿入されないようにするには、画面を選択します。  2番目の空の垂直方向の**ギャラリー**コントロールを追加し、**読み込む gallery2**という名前であることを確認します。

    **読み込む gallery2**は、ユーザーが**gallery1.selected**で選択した製品の予約を表示します。

1. **読み込む gallery2**を移動し、サイズを変更して、画面の右上のクアドラントを塗りつぶします。

1. optional次の図に示すように、**読み込む gallery2**の上に青い**ラベル**コントロールを追加します。

1. 数式バーで、**読み込む gallery2**の**Items**プロパティを**gallery1.selected**に設定します。

    ![読み込む gallery2 項目の構成](media/function-relate-unrelate/reservations-gallery.png)

1. [プロパティ] ペインで、**読み込む gallery2**の **[レイアウト]** を **[タイトル]** に設定します。

    ![読み込む gallery2 レイアウトを構成する](media/function-relate-unrelate/reservations-gallery-right.png)

1. **読み込む gallery2**で、 **[コンボボックス](../controls/control-combo-box.md)** コントロールを追加し、 **ComboBox1**という名前であることを確認します。次に、**読み込む gallery2**内の他のコントロールがブロックされないように、そのコントロールの移動とサイズ変更を行います。

1. **[プロパティ]** タブで、 **ComboBox1**の**Items**プロパティを**Products**に設定します。

    ![Items プロパティを Products に設定する](media/function-relate-unrelate/reservations-combo-right.png)

1. **[プロパティ]** タブで下にスクロールし、[ **ComboBox1**の**複数選択を許可**する] プロパティを **[オフ]** に設定します。

    ![複数選択を許可するように設定する](media/function-relate-unrelate/reservations-singleselect-right.png)

1. 数式バーで、 **ComboBox1**の**DefaultSelectedItems**プロパティを「the **Product 予約」** に設定します。

    ![ReserveCombo の DefaultSelectedItems を設定します。](media/function-relate-unrelate/reservations-combo.png)

1. **読み込む gallery2**で、 **NextArrow2**の**onselect**プロパティを次の数式に設定します。

    ```powerapps-dot
    Relate( ComboBox1.Selected.Reservations, ThisItem )
    ```

    ユーザーがこのアイコンを選択すると、 **ComboBox1**でユーザーが選択した製品に対する現在の予約が変更されます。

    ![NextArrow2 を構成する](media/function-relate-unrelate/reservations-relate.png)

1. F5 キーを押して、プレビューモードでアプリをテストします。

このアプリでは、ユーザーは1つの製品から別の製品に予約を移動できます。 1つの製品の予約の場合、ユーザーは**ComboBox1**で別の製品を選択し、 **[NextArrow2]** を選択してその予約を変更できます。

![一対多のアプリでの関連付け関数のデモンストレーション](media/function-relate-unrelate/reservations-reassign.gif)

#### <a name="unrelate-function"></a>**Unrelate**関数

この時点で、リレーションシップを1つのレコードから別のレコードに移動することはできますが、リレーションシップを完全に削除することはできません。 **Unrelate**関数を使用すると、任意の製品から予約レコードを切断できます。

1. **[ビュー]** タブで **[データソース]** を選択します。

1. **[データ]** ウィンドウで、 **[データソースの追加]** を選択して**Common Data Service** > **予約** > **接続** > します。

1. **読み込む gallery2**で、 **NextArrow2**の**onselect**式を次の数式に設定します。

    ```powerapps-dot
    If( IsBlank( ComboBox1.Selected ),
        Unrelate( Gallery1.Selected.Reservations, ThisItem ),
        Relate( ComboBox1.Selected.Reservations, ThisItem )
    );
    Refresh( Reservations )
    ```
    ![右側の設定アイコン](media/function-relate-unrelate/reservations-relate-unrelate.png)

1. **読み込む gallery2**を選択し、Ctrl + C キーを押してクリップボードにコピーします。

1. Ctrl キーを押しながら V キーを押して、**読み込む gallery2**の複製を同じ画面に貼り付け、画面の右下のクアドラントに移動します。

1. optional**読み込む gallery2**の上にラベルを追加した場合は、そのラベルに対して前の2つの手順を繰り返します。

1. **読み込む gallery2**の複製に**Gallery2_1**という名前が付けられていることを確認し、その**Items**プロパティを次の数式に設定します。

    ```powerapps-dot
    Filter( Reservations, IsBlank( 'Product Reservation' ) )
    ```

    委任の警告が表示されますが、この例では少量のデータには関係ありません。

    ![Gallery2_1 の Items プロパティを設定します。](media/function-relate-unrelate/reservations-lost.png)

これらの変更により、ユーザーが製品を予約していない場合は、 **ComboBox1**で連絡先の選択を解除できます。 製品を予約していない連絡先は**Gallery2_1**に表示され、ユーザーは各連絡先を製品に割り当てることができます。

   ![一対多のアプリで関連関数と非関連付け関数をデモンストレーションする](media/function-relate-unrelate/reservations-lostandfound.gif)

### <a name="many-to-many"></a>多対多

#### <a name="create-a-many-to-many-relationship"></a>多対多リレーションシップを作成する

サンプルデータには多対多リレーションシップは含まれていませんが、Products エンティティと contact エンティティの間に1つ作成されます。 ユーザーは、各製品を複数の連絡先に関連付けることができ、各連絡先を複数の製品に関連付けることができます。

1. [このページ](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)の左側のナビゲーションバーで **[データ]** を選択し、 **[エンティティ]** を選択します。

    ![エンティティの一覧を開く](media/function-relate-unrelate/entity-list.png)

1. エンティティフィルターをすべてのエンティティを含めるように変更します。

    既定では、サンプルエンティティは表示されません。

    ![エンティティフィルターの削除](media/function-relate-unrelate/entity-all.png)

1. 下へスクロールし、 **Product**エンティティを開いて、 **[リレーションシップ]** を選択します。

    ![Product エンティティの [リレーションシップ] タブ](media/function-relate-unrelate/entity-relationships.png)

1. [**多対多** > **リレーションシップの追加**] を選択します。

    ![多対多リレーションシップの追加](media/function-relate-unrelate/entity-manytomany.png)

1. リレーションシップの**Contact**エンティティを選択します。

    ![Contact エンティティを選択します](media/function-relate-unrelate/entity-contact.png)

1. **[完了]** を選択して**エンティティを保存** > ます。

    ![Products エンティティのリレーションシップの一覧](media/function-relate-unrelate/entity-done.png)

#### <a name="relate-and-unrelate-contacts-with-one-or-more-products"></a>連絡先を1つ以上の製品と関連付ける/関連付け解除する

このトピックで既に作成したものと似た別のアプリを作成しますが、新しいアプリは多対多の関係を提供します。 各連絡先は、1つだけではなく、複数の製品を予約できます。

1. タブレット用の空のアプリで、このトピックの[最初の手順](#one-to-many)として**gallery1.selected**を作成します。

1. 別の空の垂直**ギャラリー**コントロールを追加し、**読み込む gallery2**という名前であることを確認してから、画面の右上隅に移動します。

    このトピックの後半で、**読み込む gallery2**の下に**コンボボックス**コントロールを追加します。

1. 数式バーで、**読み込む gallery2**の**Items**プロパティを**gallery1.selected**に設定します。

    ![ContactsGallery を構成する](media/function-relate-unrelate/contacts-gallery.png)

1. **[プロパティ]** タブで、 **[レイアウト]** を **[画像とタイトル]** に設定します。

    ![ContactsGallery を構成する](media/function-relate-unrelate/contacts-gallery-right.png)

1. **読み込む gallery2**で、 **Label**コントロールの名前が**Title2**になっていることを確認し、その**Text**プロパティを次の項目に設定し**ます。 ' Full Name '** .

    この手順を完了して連絡先を製品に割り当てるまで、そのコントロールにテキストは表示されません。

    ![連絡先名の表示](media/function-relate-unrelate/contacts-title.png)

1. **NextArrow2**を削除し、**キャンセル**アイコンを挿入して、 **icon1**という名前であることを確認します。

1. **キャンセル**アイコンの**onselect**プロパティを次の数式に設定します。 

    ```powerapps-dot
    Unrelate( Gallery1.Selected.Contacts, ThisItem )
    ```

    ![[キャンセル] アイコンの構成](media/function-relate-unrelate/contacts-unrelate.png)

1. **[ビュー]** タブで **[データソース]** を選択します。

1. **[データ]** ウィンドウで、 **[データソースの追加]** を選択して > **連絡先** > **接続** **Common Data Service** > します。

1. **読み込む gallery2**の下で、**コンボボックス**コントロールを追加し、 **ComboBox1**という名前であることを確認して、その**Items**プロパティを**Contacts**に設定します。

    ![コンボボックス項目のプロパティを構成する](media/function-relate-unrelate/contacts-combo.png)

1. **[プロパティ]** タブで、 **[複数選択を許可]** する を **[オフ]** に設定します。

    ![コンボボックスレイアウトプロパティの構成](media/function-relate-unrelate/contacts-combo-right.png)

1. **[追加]** アイコンを挿入し、その**onselect**プロパティを次の数式に設定します。 

    ```powerapps-dot
    Relate( Gallery1.Selected.Contacts, ComboBox1.Selected )
    ```

    ![[追加の構成] アイコン](media/function-relate-unrelate/contacts-relate.png)

このアプリでは、ユーザーは、連絡先のセットを各製品に自由に関連付けたり、関連付けを解除したりすることができるようになりました。

- 製品に連絡先を追加するには、画面の下部にあるコンボボックスで連絡先を選択し、 **[追加]** アイコンを選択します。
- 製品から連絡先を削除するには、その連絡先の **[キャンセル**] アイコンを選択します。

    一対多の関係とは異なり、多対多のリレーションシップでは、ユーザーは同じ連絡先を複数の製品に関連付けることができます。

![多対多アプリでの関連関数と非関連付け関数のデモンストレーション](media/function-relate-unrelate/contacts-relate-unrelate.gif)

#### <a name="in-reverse-relate-and-unrelate-products-with-multiple-contacts"></a>逆: 製品と複数の連絡先の関連付けと関連付け解除

多対多リレーションシップは対称です。 この例を拡張して、連絡先に製品を追加し、2つの画面間を切り替えて、いずれかの方向からのリレーションシップの表示方法を示すことができます。

1. **Screen1**の**Onvisible**プロパティを**Refresh (Products)** に設定します。

    一対多または多対多のリレーションシップを更新すると、**関連付け**または**関連付け**解除の呼び出しの最初の引数エンティティのデータのみが更新されます。 このアプリの画面間を反転させる場合は、2番目のを手動で更新する必要があります。

    ![OnVisible プロパティを Refresh 関数に設定します](media/function-relate-unrelate/contacts-refresh.png)

1. **Screen1**が重複しています。

    複製は**Screen1_1**という名前になり、連絡先側からの関係を調べるための基礎となります。

    ![画面を複製する](media/function-relate-unrelate/contacts-duplicate.png)

1. 反転ビューを作成するには、 **Screen1_1**のコントロールに対して次の式を変更します。

    - Screen1_1 = `Refresh( Contacts )`
    - Gallery1_1 = `Contacts`
    - Title1_1 = `ThisItem.'Full Name'`
    - Label1_1 = `"Selected Contact Products"`
    - Gallery2_1 = `Gallery1_1.Selected.Products`
    - Title2_1 = `ThisItem.Name`
    - Icon1_1 = `Unrelate( Gallery1_1.Selected.Products, ThisItem )`
    - ComboBox1_1 = `Products`
    - Icon2_1 = `Relate( Gallery1_1.Selected.Products, ComboBox1_1.Selected )`

    結果は前の画面とよく似ていますが、**連絡先**側からの関係にあります。

    ![連絡先で始まる多対多リレーションシップを表示する](media/function-relate-unrelate/reverse-screen.png)

1. 矢印を**上下**に挿入し、 **Onselect**プロパティを**Navigate (Screen1, None)** に設定します。  数式で**Navigate (Screen1_1, None)** を使用して、 **Screen1**で同じ操作を行います。

    ![画面間のナビゲーションを追加する](media/function-relate-unrelate/reverse-navigate.png)

この新しい画面では、ユーザーは製品に連絡先を追加し、連絡先のビューに切り替えて、関連付けられている製品を確認できます。 リレーションシップは対称であり、2つの画面間で共有されます。

![両側からの多対多リレーションシップのデモンストレーション](media/function-relate-unrelate/contacts-reverse.gif)
