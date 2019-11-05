---
title: キャンバス アプリ コントロールを追加および構成する | Microsoft Docs
description: ツールバー、[プロパティ] タブ、数式バーなどからキャンバス アプリ コントロールを直接追加および構成するための詳細な手順です。
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 01/25/2019
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 29fcc240bdf0dbe926acb702c26d535fb4536c16
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2019
ms.locfileid: "73537133"
---
# <a name="add-and-configure-a-canvas-app-control-in-powerapps"></a>PowerApps でキャンバス アプリ コントロールを追加および構成する

キャンバス アプリへのさまざまな UI 要素の追加や、要素の外観と動作の構成を、ツールバー、 **[プロパティ]** タブ、数式バーなどから直接行います。 これらの UI 要素はコントロールと呼ばれ、構成する内容はプロパティと呼ばれます。

## <a name="prerequisites"></a>前提条件

1. PowerApps ライセンスをまだお持ちでない場合は、[サインアップ](../signup-for-powerapps.md)して[サインイン](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)します。
1. **[独自のアプリを作成する]** で、[**キャンバスアプリ] を空白から**ポイントし、 **[このアプリを作成]** する を選択します。
1. イントロツアーを実行するように求められたら、 **[次]** へ を選択して、PowerApps インターフェイスの主要な領域について理解を深めます (または **[スキップ]** を選択します)。

    後でツアーを実行するには、画面の右上隅にある疑問符アイコンを選択し、[**入門ツアーを実行**する] を選択します。

## <a name="add-and-select-a-control"></a>コントロールを追加して選択する

**[挿入]** タブで、次のいずれかの手順を実行します。

- これらの種類のコントロールのいずれかを追加するには、 **[ラベル]** または **[ボタン]** を選択します。
- コントロールのカテゴリを選択し、追加するコントロールの種類を選択します。

たとえば、 **[新しい画面]** を選択し、 **[空白]** を選択して、アプリに空の画面を追加します。 (画面は、他の種類のコントロールを含めることができるコントロールの一種です)。

![画面の追加](./media/add-configure-controls/add-screen.png)

新しい画面は**Screen2**という名前で、左側のナビゲーションウィンドウに表示されます。 このペインには、各コントロールを簡単に見つけて選択できるように、アプリ内のコントロールの階層リストが表示されます。

![リスト内の Screen2](./media/add-configure-controls/list-screen2.png)

この一覧の動作を説明するには、 **[挿入]** タブで **[ラベル]** を選択します。新しいコントロールは、 **[Screen2]** の下の [階層] の一覧に表示されます。

![リスト内の Screen2](./media/add-configure-controls/add-label.png)

画面では、既定では、6つのハンドルを持つボックスがラベルを囲みます。 この種類のボックスは、どのコントロールが選択されているかを囲みます。 クリックまたはタップして画面を選択した場合 (ただし、ラベルの外側)、このボックスはラベルから消えます。 もう一度ラベルを選択するには、その中をクリックまたはタップします。または、コントロールの階層の一覧でその名前をクリックまたはタップできます。

> [!IMPORTANT]
> コントロールを構成する前に、必ずコントロールを選択する必要があります。

## <a name="rename-a-control"></a>コントロールの名前を変更する

コントロールの階層リストで、名前を変更するコントロールの上にマウスポインターを移動し、表示される省略記号ボタンをクリックして、 **[名前の変更]** を選択します。 アプリを簡単にビルドできるように、わかりやすい一意の名前を入力できます。

![コントロール名の変更](./media/add-configure-controls/rename-control.png)

## <a name="delete-a-control"></a>コントロールを削除する

コントロールの階層リストで、削除するコントロールの上にマウスポインターを移動し、表示される省略記号ボタンをクリックして、 **[削除]** を選択します。 画面ではないコントロールを削除するには、キャンバス上のコントロールを選択し、Del キーを押します。

![コントロールの削除](./media/add-configure-controls/delete-control.png)

## <a name="reorder-screens"></a>画面の順序を変更する

コントロールの階層リストで、上または下に移動する画面の上にマウスポインターを移動し、表示される省略記号ボタンを選択して **[上へ移動]** または **[下へ移動]** を選択します。

![画面の順序変更](./media/add-configure-controls/reorder-screen.png)

> [!NOTE]
> アプリを開くと、通常、コントロールの階層リストの上部にある画面が最初に表示されます。 ただし、 **[OnStart](controls/control-screen.md)** プロパティを **[Navigate](functions/function-navigate.md)** 関数を含む数式に設定して、別の画面を指定することもできます。

## <a name="move-and-resize-a-control"></a>コントロールの移動とサイズ変更

コントロールを移動するには、コントロールを選択し、中心にマウスポインターを合わせて4方向矢印を表示します。次に、コントロールを別の場所にドラッグします。

![コントロールの移動](./media/add-configure-controls/move-control.png)

コントロールのサイズを変更するには、コントロールを選択し、[選択] ボックスのハンドルをポイントします。2方向矢印が表示されます。その後、ハンドルをドラッグします。

![コントロールの移動](./media/add-configure-controls/resize-control.png)

> [!NOTE]
> このトピックでは、後で説明するように、数式バーの **[X](controls/properties-size-location.md)** 、 **[Y](controls/properties-size-location.md)** 、 **[Height](controls/properties-size-location.md)** 、 **[Width](controls/properties-size-location.md)** プロパティの任意の組み合わせを変更して、コントロールの移動とサイズ変更を行うこともできます。

## <a name="change-the-text-of-a-label-or-a-button"></a>ラベルまたはボタンのテキストを変更する

ラベルまたはボタンを選択し、コントロールに表示されるテキストをダブルクリックして、目的のテキストを入力します。

![テキストの変更](./media/add-configure-controls/change-text.png)

> [!NOTE]
> このトピックで後述するように、数式バーで **[text](controls/properties-core.md)** プロパティを変更して、このテキストを変更することもできます。

## <a name="configure-a-control-from-the-toolbar"></a>ツールバーからコントロールを構成する

ツールバーからコントロールを構成することにより、コントロールを直接構成する場合よりも幅広いオプションを指定できます。

たとえば、ラベルを選択し、 **[ホーム]** タブを選択して、ラベル内のテキストのフォントを変更することができます。

![フォントの変更](./media/add-configure-controls/change-font.png)

## <a name="configure-a-control-from-the-properties-tab"></a>[プロパティ] タブでコントロールを構成する

**[プロパティ]** タブを使用すると、ツールバーからコントロールを構成する場合よりも幅広いオプションを指定できます。

たとえば、コントロールを選択し、 **Visible**プロパティを変更することによって、コントロールの表示と非表示を切り替えることができます。

![可視性の設定](./media/add-configure-controls/set-visibility.png)

## <a name="configure-a-control-in-the-formula-bar"></a>数式バーでコントロールを構成する

コントロールを直接構成するのではなく、ツールバーまたは **[プロパティ]** タブで、プロパティの一覧でプロパティを選択し、数式バーで値を指定することで、コントロールを構成できます。 この方法により、プロパティをアルファベット順に検索したり、より多くの種類の値を指定したりできます。

たとえば、ラベルを選択し、次の方法で構成できます。

- プロパティ の一覧で  **X** または **Y** を選択し、数式バーに別の数値を指定して移動します。

    ![X プロパティの設定](./media/add-configure-controls/x-property.png)

- プロパティの一覧で **[高さ]** または **[幅]** を選択し、数式バーに別の数値を指定して、サイズを変更します。

    ![Height プロパティの設定](./media/add-configure-controls/height-property.png)

- そのテキストを変更するには、[プロパティ] の一覧で**テキスト**を選択し、数式バーでリテラル文字列、式、または数式の任意の組み合わせを指定します。

    - リテラル文字列は引用符で囲まれ、入力したとおりに表示されます。 **"Hello, world"** はリテラル文字列です。

        ![Text プロパティをリテラル文字列に設定する](./media/add-configure-controls/literal-string.png)

    - 式は関数を含まず、多くの場合、別のコントロールのプロパティに基づいています。 **Screen1**は、 **Screen1**の高さを示す式です。

        ![Text プロパティを式に設定する](./media/add-configure-controls/expression.png)

    - 数式には、1つまたは複数の関数が含まれます。 **Now**関数は、ローカルタイムゾーンの現在の日付と時刻を返します。 **Text**関数は、日付、時刻、通貨などの値を書式設定します。

        ![Text プロパティを数式に設定します。](./media/add-configure-controls/formula.png)

        通常、数式はこの例よりもはるかに複雑であるため、データの更新、並べ替え、フィルター処理、およびその他の操作を行うことができます。 詳細については、「[数式のリファレンス](formula-reference.md)」を参照してください。

## <a name="next-steps"></a>次の手順

- [画面](add-screen-context-variables.md)、[リスト](add-list-box-drop-down-list-radio-button.md)、[ギャラリー](add-gallery.md)、[フォーム](add-form.md)、[グラフ](use-line-pie-bar-chart.md)などの一般的なコントロールを構成する手順について説明します。
- コントロール[参照](reference-properties.md)の各種類のコントロールに関する参照情報を検索します。
