---
title: キャンバスアプリに依存するドロップダウンリストを作成する |Microsoft Docs
description: PowerApps で、キャンバスアプリ内の別のドロップダウンリストをフィルター処理するドロップダウンリストを作成します。
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 04/04/2019
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 57abde44541a2a1e40e3a8ffc55a89e37a8c6478
ms.sourcegitcommit: 7c1e70e94d75140955518349e6f9130ce3fd094e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/29/2019
ms.locfileid: "71985744"
---
# <a name="create-dependent-drop-down-lists-in-a-canvas-app"></a>キャンバスアプリに依存するドロップダウンリストを作成する

依存 (またはカスケード) のドロップダウンリストを作成する場合、ユーザーは一覧でオプションを選択して、別の一覧のオプションをフィルター処理します。 多くの組織は、ユーザーがフォームに効率的に入力できるように、依存リストを作成します。 たとえば、ユーザーが市区町村の一覧をフィルター処理する国または地域を選択したり、ユーザーがカテゴリを選択してそのカテゴリのコードのみを表示したりすることがあります。

ベストプラクティスとして、ユーザーがアプリを使用して更新するデータソースとは別の "親" リストと "子" リスト (国、地域、都市など) の値のデータソースを作成します。 この方法を使用すると、複数のアプリで同じ親データと子データを使用でき、そのデータを使用するアプリやアプリを再発行しなくても、そのデータを更新できます。 コレクションまたは静的データを使用しても同じ結果を得ることができますが、エンタープライズシナリオでは推奨されません。

このトピックのシナリオでは、ストアの従業員がフォームを使用して**インシデント**の一覧に問題を送信します。 従業員は、インシデントが発生した店舗の場所だけでなく、その場所にある部門も指定します。 すべての場所で同じ部門が使用されているわけではないので、**場所**の一覧では、従業員がその部署を持っていない場所に部署を指定することはできません。

このトピックでは、データソースとして Microsoft SharePoint リストを使用しますが、すべての表形式データソースは同じように動作します。

## <a name="create-data-sources"></a>データソースの作成

[**場所] 一覧には**、各場所の部門が表示されます。

| Location | Department |
|----------------|------------------|
| Eganville      | ケーキ屋さん           |
| Eganville      | 家             |
| Eganville      | ビール          |
| Renfrew        | ケーキ屋さん           |
| Renfrew        | 家             |
| Renfrew        | ビール          |
| Renfrew        | 薬         |
| Renfrew        | フローラル           |
| Pembroke       | ケーキ屋さん           |
| Pembroke       | 家             |
| Pembroke       | ビール          |
| Pembroke       | フローラル           |

インシデント**の一覧に**は、各インシデントに関する連絡先情報と情報が表示されます。 日付列を**日付**列として作成しますが、他の列を**1 行のテキスト**列として作成して、構成を簡素化し、Microsoft PowerApps で[委任](./delegation-overview.md)の警告を回避します。

| 名 | 姓 | 電話番号     | Location | Department | Description       | Date      |
|------------|-----------|------------------|----------------|------------|-------------------------|-----------|
| Tonya       | Cortez, p.   | (206) 555-1022 | Eganville      | ビール    | 問題が発生しました...   | 2/12/2019 |
| Moses     | Laflamme     | (425) 555-1044 | Renfrew        | フローラル     | 問題が発生しました... | 2/13/2019 |

既定では、カスタム SharePoint リストには、名前を変更したり削除したりすることができない**タイトル**列が含まれています。また、リストに項目を保存する前に、データを含める必要があります。 データを必要としないように列を構成するには、次のようにします。

1. 右上隅にある歯車アイコンを選択し、 **[リストの設定]** を選択します。
1. **[設定]** ページで、列の一覧の **[タイトル]** を選択します。
1. **[この列に情報が含まれていることを要求]** する で **[いいえ]** を選択します。

この変更を行った後は、 **Title**列を無視することも、他の列が少なくとも1つ表示されている場合は既定のビューから[削除](https://support.office.com/article/edit-a-list-column-in-sharepoint-online-77130c2e-76d1-4f80-af8b-4c6f47b264b8)することもできます。

## <a name="open-the-form"></a>フォームを開く

1. **インシデント**の一覧を開き、[ **PowerApps**  > **フォームのカスタマイズ**] を選択します。

    > [!div class="mx-imgBorder"]
    > ![インシデントの一覧を開き、[PowerApps > フォームのカスタマイズ] を選択します。](./media/dependent-drop-down-lists/open-form.png "インシデントの一覧を開き、[PowerApps > フォームのカスタマイズ] を選択します。")

    [ブラウザー] タブが開き、PowerApps Studio に既定のフォームが表示されます。

1. optional **[フィールド]** ウィンドウで、 **[タイトル]** フィールドの上にマウスポインターを移動し、表示される省略記号 (...) を選択して、 **[削除]** を選択します。

    **[フィールド]** ウィンドウを閉じた場合は、左側のナビゲーションバーで **[SharePointForm1]** を選択し、右側のウィンドウの **[プロパティ]** タブで **[フィールドの編集]** を選択すると、もう一度開くことができます。

1. optional前の手順を繰り返して、**添付ファイル**フィールドをフォームから削除します。

    フォームには、追加したフィールドだけが表示されます。

    > [!div class="mx-imgBorder"]
    > タイトルと添付ファイルのフィールドのない ![フォーム](./media/dependent-drop-down-lists/default-form.png)

## <a name="replace-the-controls"></a>コントロールを置き換える

1. **[フィールド]** ウィンドウで、 **[場所]** の横にある矢印を選択します。

    **[フィールド]** ウィンドウを閉じた場合は、左側のナビゲーションバーで **[SharePointForm1]** を選択し、右側のウィンドウの **[プロパティ]** タブで **[フィールドの編集]** を選択すると、もう一度開くことができます。

1. **[コントロールの種類]** の一覧を開き、 **[許可さ]** れた値 を選択します。

    > [!div class="mx-imgBorder"]
    > 許可される値の ![](./media/dependent-drop-down-lists/change-control.png)

    入力メカニズムが**ドロップダウン**コントロールに変わります。

1. **Department**カードに対しても同じ手順を繰り返します。

## <a name="add-the-locations-list"></a>場所の一覧を追加する

1. [データ**ソースの追加** **]  >  [データソース**の  > **表示**] を選択します。

1. SharePoint 接続を選択または作成し、 **[場所]** ボックスの一覧を含むサイトを指定します。

1. この一覧のチェックボックスをオンにし、 **[接続]** を選択します。

    > [!div class="mx-imgBorder"]
    > ![データペイン](./media/dependent-drop-down-lists/select-list.png)

    接続の一覧には、フォームの基になっている**インシデント**の一覧と、フォーム内の場所と部署を識別する**場所**の一覧が表示されます。

    > [!div class="mx-imgBorder"]
    > SharePoint データソースの ![](./media/dependent-drop-down-lists/data-sources.png)

## <a name="unlock-the-cards"></a>カードのロックを解除する

1. **Location**カードを選択し、右側のウィンドウで **詳細設定** タブを選択し、ロック解除 を選択して**プロパティを変更**します。

1. **Department**カードに対して前の手順を繰り返します。

## <a name="rename-the-controls"></a>コントロールの名前を変更する

コントロールの名前を変更すると、それらをより簡単に識別できるようになります。また、例の方が簡単になります。 その他のベストプラクティスについては、[コーディング標準とガイドラインに関するホワイトペーパー](https://aka.ms/powerappscanvasguidelines)を参照してください。

1. **[場所]** カードで、**ドロップダウン**コントロールを選択します。

1. 右側のウィンドウの上部にある **[Ddlocation]** を入力または貼り付けて、選択したコントロールの名前を変更します。

    > [!div class="mx-imgBorder"]
    > コントロールの名前を変更 ![](./media/dependent-drop-down-lists/rename-control.png)

1. **Department**カードの前の2つの手順を繰り返して、**ドロップダウン**コントロールの名前を**dddepartment**に変更します。

## <a name="configure-the-locations"></a>場所を構成する

1. **Ddlocation**の**Items**プロパティを次の数式に設定します。

    `Distinct(Locations, Location)`

1. optionalAlt キーを押したまま、 **Ddlocation**を開き、一覧に3つの場所が表示されていることを確認します。

## <a name="configure-the-departments"></a>部門を構成する

1. **Dddepartment** を選択し、右側のウィンドウの **プロパティ** タブで、依存先 を選択し**ます。**

1. **[親コントロール]** で、 **[ddlocation]** が上部の一覧に表示され、**結果**が下の一覧に表示されていることを確認します。

    > [!NOTE]
    > 文字列を一致させたくないが、実際のデータ行の ID では、 **[結果]** ではなく **[id]** を選択します。

1. **[一致するフィールド]** で、上部の一覧から [**場所] を選択し**、下部の一覧から **[場所]** を選択し、 **[適用]** を選択します。

    > [!div class="mx-imgBorder"]
    > ![はリンク](./media/dependent-drop-down-lists/depends-on.png) に依存します

    **Dddepartment**の**Items**プロパティは、次の数式に設定されます。

    `Filter(Locations, Location = ddLocation.Selected.Result)`

    この数式は、ユーザーが**Dddepartment**で選択した内容に基づいて、 **dddepartment**内の項目をフィルター処理します。 このような構成では、SharePoint の**場所**の一覧によって指定されているように、部署の "子" リストに "親" の場所のデータが反映されます。

1. 右側のウィンドウの **[プロパティ]** タブで、 **[値]** の横にある一覧を開き、 **[Department]** を選択します。

    この手順では、SharePoint の **[場所]** ボックスの一覧の **[部門]** 列に表示されるテキストをオプションに設定します。

    > [!div class="mx-imgBorder"]
    > ![Department 値](./media/dependent-drop-down-lists/dept-value.png)

## <a name="test-the-form"></a>フォームをテストする

Alt キーを押したまま、場所の一覧を開き、1つを選択して、部門の一覧を開き、1つを選択します。

場所と部門の一覧には、SharePoint の **[場所]** リストの情報が反映されています。

> [!div class="mx-imgBorder"]
> ![の場所の一覧を開いて、選択内容を Renfrew から Pembroke に変更し、部門の一覧を開き](./media/dependent-drop-down-lists/dropdowns.gif)

## <a name="save-and-open-the-form-optional"></a>フォームを保存して開きます (省略可能)。

1. **ファイル** メニューを開き、Sharepoint に**発行** ** >  sharepoint に発行**を選択して **保存** >  ます。

1. 左上隅で、戻る矢印を選択し、 **[SharePoint に戻る]** を選択します。

1. コマンド バーで **[新規]** を選択し、カスタマイズしたフォームを開きます。

## <a name="faq"></a>FAQ

**データがまったく表示されない: ソースがすべて空白であるか、データが間違っています。**
次のいずれかの方法で、コントロールに適切なフィールドが表示されているかどうかを確認します。

- ドロップダウンリストを選択し、右側のペインの **[プロパティ]** タブで **[値]** プロパティを選択します。

    > [!div class="mx-imgBorder"]
    > ![ドロップダウン](./media/dependent-drop-down-lists/drop-down-display-field.png) の変更

- コンボボックスを選択し、プライマリテキストが表示するフィールドであることを確認します。

    > [!div class="mx-imgBorder"]
    > コンボボックス](./media/dependent-drop-down-lists/combo-box-display-field.png) を変更 ![

**[マイ子] ドロップダウンリストに重複する項目が含まれています。**
この現象は、SharePoint で**参照**列を使用しているか、PowerApps で**choice**関数が使用されていることが原因である可能性があります。 重複を削除するには、適切にデータを返すように**個別**の関数をラップします。 詳細については、「 [Distinct 関数](functions/function-distinct.md)」を参照してください。

## <a name="known-limitations"></a>既知の制限

この構成は、**ドロップダウン**コントロールと、一度に1つの選択を可能にする**コンボボックス**コントロールと**リストボックス**コントロールで使用できます。 複数の選択が許可されている場合、これらのコントロールのいずれに対しても、**依存**関係を使用することはできません。 Common Data Service のオプションセットを使用する場合、この方法は推奨されません。

**依存**関係は、静的データまたはコレクションをサポートしていません。 これらのソースで依存するドロップダウンリストを構成するには、数式バーで式を直接編集します。 さらに、PowerApps では、一致するデータテーブルを使用せずに、SharePoint で2つの選択肢フィールドを使用することはできません。また、この UI 内で**一致するフィールド**を定義することもできません。
