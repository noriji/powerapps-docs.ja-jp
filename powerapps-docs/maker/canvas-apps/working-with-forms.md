---
title: キャンバス アプリのフォームについて | Microsoft Docs
description: PowerApps でキャンバス アプリにフォームを追加して、データ ソースから情報を収集して表示できるようにします。
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 04/27/2016
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 476964166a57bea23469baf0c1e7497be10ab73f
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2019
ms.locfileid: "73541662"
---
# <a name="understand-canvas-app-forms-in-microsoft-powerapps"></a>Microsoft PowerApps のキャンバス アプリ フォームについて

ユーザーがレコードの閲覧、そのレコードの詳細の表示、レコードの編集または作成を実行できるように 3 種類のコントロールをキャンバス アプリに追加します。

| アクティビティ | コントロール | Description |
| --- | --- | --- |
| **レコードを閲覧する** |**[ギャラリー](controls/control-gallery.md)** コントロール |データ ソースのレコードをフィルター処理、並べ替え、検索、スクロールして、特定のレコードを選択します。 小さな画面上でも、各レコードからごく少数のフィールドを表示して、一度に複数のレコードを表示します。 |
| **レコードの詳細を表示する** |**[表示フォーム](controls/control-form-detail.md)** コントロール |単一のレコードの場合、そのレコードの複数またはすべてのフィールドが表示されます。 |
| **レコードを編集または作成する** |**[編集フォーム](controls/control-form-detail.md)** コントロール |1 つのレコードの 1 つ以上のフィールドを更新 (または既定値で始まるレコードを作成) し、これらの変更を基になるデータ ソースに保存します。 |

各コントロールを区別しやすくするために、個別の画面に配置します。

![3 つの画面でのレコードの閲覧、表示、編集](./media/working-with-forms/three-screens.png)

このトピックで説明するように、これらのコントロールを数式と組み合わせて、全体的なユーザー エクスペリエンスを作成します。

## <a name="prerequisites"></a>前提条件

* PowerApps に[サインアップ](../signup-for-powerapps.md)し、サインアップに使用したのと同じ資格情報を入力して[サインイン](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)します。
* PowerApps で[コントロールを構成する](add-configure-controls.md)方法について確認します。

## <a name="explore-a-generated-app"></a>生成されたアプリの詳細
PowerApps では、指定したデータ ソースに基づいて自動的にアプリを生成することができます。 各アプリには、先ほど説明したコントロールとそれらを接続する数式を使用した 3 つの画面があります。 これらのアプリは、"そのまま" 実行することも、具体的な目標に合わせてカスタマイズすることもできます。また、アプリのしくみを調べて、自分のアプリに当てはまる有用な概念を習得することもできます。 以降のセクションでは、生成されたアプリを動作させる画面、コントロール、数式について確認します。  

### <a name="browse-screen"></a>ブラウズ画面
![閲覧画面のコントロール](./media/working-with-forms/afd-browse-screen-basic.png)

この画面では、次の重要な数式が使用されます。

| コントロール | サポートされている動作 | 数式 |
| --- | --- | --- |
| **BrowseGallery1** |**Assets** データ ソースからレコードを表示します。 |ギャラリーの **[Items](controls/properties-core.md)** プロパティは、**Assets** データ ソースに基づく数式に設定されています。 |
| **ImageNewItem1** |**編集および作成**画面を表示します。画面の各フィールドは既定値に設定されているため、ユーザーは簡単にレコードを作成できます。 |イメージの **[OnSelect](controls/properties-core.md)** プロパティは、次の数式に設定されています。<br> **NewForm( EditForm1 );<br>Navigate( EditScreen1, None )** |
| **NextArrow1** (ギャラリー内) |現在選択されているレコードの多くまたはすべてのフィールドを表示するための**詳細**画面を表示します。 |矢印の **[OnSelect](controls/properties-core.md)** プロパティは、次の数式に設定されています。<br>**Navigate( DetailScreen1, None )** |

この画面の主要コントロール **BrowseGallery1** は、画面の領域の大半を占めています。 ユーザーは、ギャラリーをスクロールして特定のレコードを見つけ、さらにフィールドを表示したり更新したりできます。

データ ソースのレコードをギャラリーに表示するように、ギャラリーの **[Items](controls/properties-core.md)** プロパティを設定します。 たとえば、このプロパティを **Assets** に設定すると、その名前のデータ ソースのレコードが表示されます。

> [!NOTE]
> 生成されたアプリでは、ユーザーがレコードの並べ替えと検索を実行できるように、 **[Items](controls/properties-core.md)** が既定でかなり複雑な数式に設定されています。 この数式の作成方法についてはこのトピックの後半で説明しますが、この時点では単純なバージョンで十分です。

ユーザーは、表示または編集するレコードを探す代わりに、ギャラリーの上部にある "+" 記号を選択してレコードを作成することができます。 この効果を作成するには、 **[イメージ](controls/control-image.md)** コントロールを追加し、その中に "+" 記号を表示して、その **[OnSelect](controls/properties-core.md)** プロパティを次の数式に設定します。
<br>**NewForm( EditForm1 ); Navigate( EditScreen1, None )**

この数式により、**編集および作成**画面が開きます。この画面には、**EditForm1** という名前の **[編集フォーム](controls/control-form-detail.md)** コントロールが用意されています。 また、そのフォームは **New** モードに切り替わります。このモードでは、ユーザーが最初からレコードを簡単に作成できるように、フォームにはデータ ソースからの既定値が表示されます。

**BrowseGallery1** に表示される任意のコントロールを調べるには、そのギャラリーの最初のセクションでそのコントロールを選択します。最初のセクションは、その他すべてのセクションのテンプレートとして機能します。 たとえば、左端の中央にある **[ラベル](controls/control-text-box.md)** コントロールを選択します。

![閲覧画面のコントロール](./media/working-with-forms/afd-browse-gallery-controls.png)

この例では、コントロールの **[Text](controls/properties-core.md)** プロパティが **ThisItem.AssignedTo** に設定されています。これは **Assets** データ ソースのフィールドです。 ギャラリー内の他の 3 つの **[ラベル](controls/control-text-box.md)** コントロールの **[Text](controls/properties-core.md)** プロパティは類似の数式に設定され、各コントロールにはデータ ソースの異なるフィールドが表示されます。  

**[図形](controls/control-shapes-icons.md)** コントロール (矢印) を選択し、その **[OnSelect](controls/properties-core.md)** プロパティが次の数式に設定されていることを確認します。
<br>**Navigate( DetailScreen1, None )**

ユーザーは、**BrowseGallery1** でレコードを見つけると、そのレコードの矢印を選択して、その詳細情報を **DetailScreen1** に表示することができます。 ユーザーが矢印を選択することで、**BrowseGallery1** の **Selected** プロパティの値が変更されます。 このアプリでは、そのプロパティによって、**DetailScreen1** だけでなく、**編集および作成**画面 (ユーザーがレコードを更新することにした場合) にも表示されるレコードが決まります。

### <a name="detail-screen"></a>詳細画面
![詳細画面のコントロール](./media/working-with-forms/afd-detail-screen-basic.png)

この画面では、次の重要な数式が使用されます。

| コントロール | サポートされている動作 | 数式 |
| --- | --- | --- |
| **DetailForm1** |**Assets** データ ソースのレコードを表示します。 |**[DataSource](controls/control-form-detail.md)** プロパティを **Assets** に設定します。 |
| **DetailForm1** |表示するレコードを決定します。 生成されたアプリでは、ユーザーがギャラリーで選択したレコードが表示されます。 |このコントロールの **[Item](controls/control-form-detail.md)** プロパティを次の値に設定します。<br>**BrowseGallery1.Selected** |
| **[カード](controls/control-card.md)** コントロール |**[表示フォーム](controls/control-form-detail.md)** コントロールに、レコードの 1 つのフィールドを表示します。 |**[DataField](controls/control-card.md)** プロパティをフィールドの名前に設定します。フィールド名は二重引用符で囲みます (例: **"Name"** )。 |
| **ImageBackArrow1** |ユーザーがこのコントロールを選択したときに、**BrowseScreen1** を開きます。 |**[OnSelect](controls/properties-core.md)** プロパティを次の数式に設定します。<br>**Back()** |
| **ImageDelete1** |ユーザーがこのコントロールを選択したときに、レコードを削除します。 |**[OnSelect](controls/properties-core.md)** プロパティを次の数式に設定します。<br>**Remove( Assets, BrowseGallery1.Selected )** |
| **ImageEdit1** |ユーザーがこのコントロールを選択したときに、**編集および作成**画面で現在のレコードを開きます。 |**[OnSelect](controls/properties-core.md)** プロパティを次の数式に設定します。<br>**Navigate( EditScreen1, None )** |

画面の上部には、3 つの画像が **DetailForm1** の外部に配置されています。これらの画像は、アプリの 3 つの画面間の調整を行うボタンとして機能します。

この画面の大部分を占める **DetailForm1** には、ユーザーがギャラリーで選択したレコードが表示されます (フォームの **[Item](controls/control-form-detail.md)** プロパティが **BrowseGallery1.Selected** に設定されているため)。 フォームの **[DataSource](controls/control-form-detail.md)** プロパティは、各フィールドのわかりやすい表示名など、データ ソースに関するメタデータも提供します。

**DetailForm1** には、複数の **[カード](controls/control-card.md)** コントロールが含まれています。 **[カード](controls/control-card.md)** コントロール自体、またはそれに含まれているコントロールを選択して、追加の情報を探すことができます。

![作成環境で選択された詳細カードとカード コントロール](./media/working-with-forms/afd-detail-card-controls.png)

**[カード](controls/control-card.md)** コントロールの **[DataField](controls/control-card.md)** プロパティにより、カードに表示されるフィールドが決まります。 この場合、そのプロパティは **AssetID** に設定されています。 このカードには、 **[Text](controls/properties-core.md)** プロパティが **Parent.Default** に設定されている **[ラベル](controls/control-text-box.md)** コントロールが含まれています。 このコントロールには、カードの **Default** 値が表示されます。この値は、 **[DataField](controls/control-card.md)** プロパティで設定されます。

生成されたアプリでは、 **[カード](controls/control-card.md)** コントロールが既定でロックされています。 カードがロックされていると、 **[DataField](controls/control-card.md)** などの一部のプロパティを変更できず、それらのプロパティで数式バーを使用できません。 この制限は、生成されたアプリの基本機能がカスタマイズによって損なわれないようにするのに役立ちます。 ただし、カードとそのコントロールの一部のプロパティは、右側のウィンドウで変更することができます。

![[オプション] ウィンドウを開いた状態の詳細画面](./media/working-with-forms/detail-screen-new.png)

右側のウィンドウで、表示するフィールドと、各フィールドに表示するコントロールの種類を選択できます。

### <a name="editcreate-screen"></a>編集/作成画面
![編集画面のコントロール](./media/working-with-forms/afd-edit-screen-basic.png)

この画面では、次の重要な数式が使用されます。

| コントロール | サポートされている動作 | 数式 |
| --- | --- | --- |
| **EditForm1** |**Assets** データ ソースのレコードを表示します。 |**[DataSource](controls/control-form-detail.md)** プロパティを **Assets** に設定します。 |
| **EditForm1** |表示するレコードを決定します。 生成されたアプリでは、ユーザーが **BrowseScreen1** で選択したレコードが表示されます。 |**[Item](controls/control-form-detail.md)** プロパティを次の値に設定します。<br>**BrowseGallery1.Selected** |
| **[カード](controls/control-card.md)** コントロール |**[編集フォーム](controls/control-form-detail.md)** コントロール内に、ユーザーがレコードの 1 つ以上のフィールドを編集できるようにコントロールを指定します。 |**[DataField](controls/control-card.md)** プロパティをフィールドの名前に設定します。フィールド名は二重引用符で囲みます (例: **"Name"** )。 |
| **ImageCancel1** |ユーザーがこのコントロールを選択したときに、進行中のすべての変更を破棄し、**詳細**画面を開きます。 |**[OnSelect](controls/properties-core.md)** プロパティを次の数式に設定します。<br>**ResetForm( EditForm1 ); Back()** |
| **ImageAccept1** |ユーザーがこのコントロールを選択したときに、データ ソースに変更を送信します。 |**[OnSelect](controls/properties-core.md)** プロパティを次の数式に設定します。<br>**SubmitForm( EditForm1 )** |
| **EditForm1** |変更が受け入れられた場合に、前の画面に戻ります。 |**[OnSuccess](controls/control-form-detail.md)** プロパティを次の数式に設定します。<br>**Back()** |
| **EditForm1** |変更が受け入れられない場合に、ユーザーが問題を修正して再送信を試みることができるように、現在の画面に留まります。 |**[OnFailure](controls/control-form-detail.md)** プロパティを空のままにします。 |
| **LblFormError1** |変更が受け入れられない場合、エラー メッセージを表示します。 |**[Text](controls/properties-core.md)** プロパティを次の値に設定します。<br>**EditForm1.Error** |

**詳細**画面と同様に、**編集および作成**画面の大部分は、**EditForm1** という名前のフォーム コントロールで占められています。 さらに、**EditForm1** の **[Item](controls/control-form-detail.md)** プロパティは **BrowseGallery1.Selected** に設定されているため、ユーザーが **BrowseScreen1** で選択したレコードがフォームに表示されます。 **詳細**画面では、各フィールドが読み取り専用として表示されるのに対し、**EditForm1** では、ユーザーがコントロールを使用して 1 つ以上のフィールドの値を更新できます。 また、 **[DataSource](controls/control-form-detail.md)** プロパティを使用して、各フィールドのわかりやすい表示名や変更の保存場所など、このデータ ソースに関するメタデータにアクセスします。

ユーザーが "X" アイコンを選択して更新を取り消すと、 **[ResetForm](functions/function-form.md)** 関数によって未保存の変更が破棄され、 **[Back](functions/function-navigate.md)** 関数によって**詳細**画面が開かれます。 ユーザーが **BrowseScreen1** で別のレコードを選択するまで、**詳細**画面と**編集および作成**画面の両方に同じレコードが表示されます。 そのレコードのフィールドは、直前に保存された値に設定されたままになります。ユーザーが変更後に破棄した値ではありません。

ユーザーがフォームで 1 つ以上の値を変更した後で "チェックマーク" アイコンを選択すると、 **[SubmitForm](functions/function-form.md)** 関数によってユーザーの変更がデータ ソースに送信されます。

* 変更が正常に保存されると、フォームの **[OnSuccess](controls/control-form-detail.md)** の数式が実行され、**Back()** 関数によって詳細画面が開き、更新されたレコードが表示されます。
* 変更が正常に保存されなかった場合、フォームの **[OnFailure](controls/control-form-detail.md)** の数式が実行されますが、"*空白*" のため、何も変更されません。 **編集および作成**画面は開いたままになるため、ユーザーは変更を取り消すか、エラーを修正することができます。 **LblFormError1** は、フォームの **Error** プロパティに設定されている、ユーザー向けのエラー メッセージを表示します。

**[表示フォーム](controls/control-form-detail.md)** コントロールと同様、 **[編集フォーム](controls/control-form-detail.md)** コントロールには **[カード](controls/control-card.md)** コントロールが含まれています。これには、レコードのさまざまなフィールドを表示する他のコントロールが含まれています。

![作成環境で選択された編集カードとカード コントロール](./media/working-with-forms/afd-edit-card-controls.png)

前の画像で選択されているカードには、**AssetID** フィールドが表示されていて、ユーザーがそのフィールドの値を編集できるように **[テキスト入力](controls/control-text-input.md)** コントロールが含まれています (これに対して、詳細画面では、読み取り専用の **[ラベル](controls/control-text-box.md)** コントロールに同じフィールドが表示されます)。 **[テキスト入力](controls/control-text-input.md)** コントロールには **[既定](controls/properties-core.md)** のプロパティがあり、これは**Parent. default**に設定されています。 ユーザーがレコードを編集ではなく作成していた場合、そのコントロールには初期値が表示されます。ユーザーは、新しいレコード用にこの値を変更できます。

右側のウィンドウでは、各カードの表示と非表示を切り替えたり、カードを並べ替えたりできるほか、さまざまな種類のコントロールにフィールドを表示するように構成することもできます。

![[オプション] ウィンドウを開いた状態の編集画面](./media/working-with-forms/edit-screen.png)

## <a name="build-an-app-from-scratch"></a>アプリをゼロから作成
PowerApps でアプリが生成されるしくみを理解すると、このトピックの前半で説明したのと同じ構成要素と数式を使用するアプリを自分で作成できます。

## <a name="identify-test-data"></a>テスト データの識別
このトピックを最大限に活用するために、実験に使用できるデータ ソースから見ていきましょう。 このデータ ソースには、心配なしに読み取りおよび更新できるテスト データが含まれている必要があります。

> [!NOTE]
> データ ソースに列名がスペースの列を含む SharePoint リストまたは Excel テーブルを使用する場合、PowerApps はスペースを **"\_x0020\_"** に置き換えます。 たとえば、SharePoint または Excel の **"Column Name"** は、PowerApps のデータ レイアウトに表示されるときや数式で使用されるときは **"Column_x0020_Name"** と表示されます。

このトピックの残りの部分に忠実に従うために、次のデータを含む、"Ice Cream" という名前の SharePoint リストを作成します。

![Ice Cream SharePoint リスト](./media/working-with-forms/sharepointlist-icecream.png)

* スマートフォン向けに、アプリをゼロから作成し、[それをデータ ソースに接続](add-data-connection.md)します。
  
    > [!NOTE]
  > タブレット アプリはどれもよく似ていますが、余分な画面スペースを最大限に活用するために、別の[画面レイアウト](#screen-design)が必要になる場合があります。
  
    このトピックの残りの部分の例は、**Ice Cream** という名前のデータ ソースに基づいています。

## <a name="browse-records"></a>レコードの閲覧
閲覧画面上のギャラリーでレコードを見つけてすばやく情報を入手します。

1. **垂直**ギャラリーを追加して、レイアウトを**タイトル**のみ変更します。
   
    ![Ice Cream データ ソースに接続されているギャラリー](./media/working-with-forms/new-gallery.png)
2. ギャラリーの **[Items](controls/properties-core.md)** プロパティを **Ice Cream** に設定します。
3. ギャラリーの最初のラベルの **[Text](controls/properties-core.md)** プロパティを、他のものに設定されている場合は、**ThisItem.Title** に設定します。
   
    これで、ラベルに各レコードの **Title** フィールドの値が表示されます。
   
    ![Ice Cream データ ソースに接続されているギャラリー](./media/working-with-forms/new-gallery-2.png)
4. ギャラリーのサイズを画面いっぱいになるように変更し、 **[TemplateSize](controls/control-gallery.md)** プロパティを **60** に設定します。
   
    画面には、この例のように、データ ソースのすべてのレコードが表示されます。
   
    ![Ice Cream データ ソースに接続されているギャラリー](./media/working-with-forms/new-gallery-icecream.png)

## <a name="view-details"></a>詳細の表示
ギャラリーに必要な情報が表示されていない場合は、レコードの矢印を選択して詳細画面を開きます。 この画面の **[表示フォーム](controls/control-form-detail.md)** コントロールには、選択したレコードのさらに多く (おそらくすべて) のフィールドが表示されます。

**[表示フォーム](controls/control-form-detail.md)** コントロールでは、次の 2 つのプロパティを使用してレコードを表示します。

* **[DataSource](controls/control-form-detail.md)** プロパティ。  レコードを保持するデータ ソースの名前。 このプロパティにより、右側のパネルにフィールドが設定され、各フィールドの表示名とデータ型 (文字列、数値、日付など) が決まります。  
* **[Item](controls/control-form-detail.md)** プロパティ。  表示するレコード。  このプロパティは、多くの場合、 **[ギャラリー](controls/control-gallery.md)** コントロールの **Selected** プロパティに関連付けられています。そのため、ユーザーは、 **[ギャラリー](controls/control-gallery.md)** コントロールでレコードを選択した後、そのレコードの詳細を確認することができます。

**[DataSource](controls/control-form-detail.md)** プロパティが設定されていると、右側のウィンドウでフィールドを追加および削除したり、フィールドの表示方法を変更したりできます。

この画面では、ユーザーは意図的にも偶発的にもレコードの値を変更できません。 **[表示フォーム](controls/control-form-detail.md)** コントロールは読み取り専用のコントロールのため、レコードが変更されることはありません。

**[表示フォーム](controls/control-form-detail.md)** コントロールを追加するには:

1. 画面を追加し、 **[表示フォーム](controls/control-form-detail.md)** コントロールを追加します。
2. フォーム コントロールの **[DataSource](controls/control-form-detail.md)** プロパティを **'Ice Cream'** に設定します。

右側のウィンドウで、画面に表示するフィールドと、各フィールドに表示するカードの種類を選択できます。 右側のウィンドウで変更を加えると、各 **[カード](controls/control-card.md)** コントロールの **[DataField](controls/control-card.md)** プロパティは、ユーザーが操作するフィールドに設定されます。 画面は次の例のようになります。

![Ice Cream データ ソースの表示フォーム](./media/working-with-forms/ice-cream-new.png)

最後に、特定のレコードの詳細が表示されるように、 **[表示フォーム](controls/control-form-detail.md)** コントロールを **[ギャラリー](controls/control-gallery.md)** コントロールに接続します。  **[Item](controls/control-form-detail.md)** プロパティの設定が完了すると、すぐにギャラリーの最初のレコードがフォームに表示されます。

* **[表示フォーム](controls/control-form-detail.md)** コントロールの **[Item](controls/control-form-detail.md)** プロパティを **Gallery1.Selected** に設定します。
   
    選択した項目の詳細がフォームに表示されます。
   
    ![ギャラリー コントロールに接続された、Ice Cream データ ソースの表示フォーム](./media/working-with-forms/view-form-select-coconut.png)

成功しました。  次は、ナビゲーションです。これは、ユーザーがギャラリー画面から詳細画面、詳細画面からギャラリー画面を開く方法です。

* 画面に **[ボタン](controls/control-button.md)** コントロールを追加し、 **[Back](functions/function-navigate.md)** と表示されるように **[Text](controls/properties-core.md)** プロパティを設定して、 **[OnSelect](controls/properties-core.md)** プロパティを **Back()** に設定します。
   
    この数式により、ユーザーは、詳細の表示を終了したときにギャラリーに戻ります。

    ![[Back] ボタンが追加された Ice Cream データ ソースの表示フォーム](./media/working-with-forms/viewform-icecream-back.png)

ここで、 **[ギャラリー](controls/control-gallery.md)** コントロールに戻り、詳細画面にいくつかのナビゲーションを追加します。

1. **[ギャラリー](controls/control-gallery.md)** コントロールをホストしている最初の画面に切り替え、ギャラリーの最初の項目の矢印を選択します。

2. 図形の **[OnSelect](controls/properties-core.md)** プロパティを次の数式に設定します。
   <br>**Navigate( Screen2, None )**
   
    ![[Back] ボタンが追加された Ice Cream データ ソースの表示フォーム](./media/working-with-forms/gallery-icecream-nav-new.png)

3. F5 キーを押し、ギャラリーの矢印を選択して項目の詳細を表示します。

4. **[[Back]](functions/function-navigate.md)** ボタンを選択して製品ギャラリーに戻り、Esc キーを押します。

## <a name="editing-details"></a>詳細の編集
最後の重要な作業として、ユーザーが **[編集フォーム](controls/control-form-detail.md)** コントロールで完成させた、レコードの内容を変更します。

**[編集フォーム](controls/control-form-detail.md)** コントロールでは、2 つのプロパティを使用してレコードを表示および編集します。

* **[DataSource](controls/control-form-detail.md)** プロパティ。  レコードを保持するデータ ソースの名前。  **[表示フォーム](controls/control-form-detail.md)** コントロールと同様、このプロパティにより、右側のパネルにフィールドが設定され、各フィールドの表示名とデータ型 (文字列、数値、日付など) が決まります。 また、各フィールドの値を基になるデータ ソースに送信する前にその値が有効かどうかが判定されます。
* **[Item](controls/control-form-detail.md)** プロパティ。  編集するレコード。多くの場合、これは、 **[ギャラリー](controls/control-gallery.md)** コントロールの **Selected** プロパティに関連付けられています。 こうすることで、 **[ギャラリー](controls/control-gallery.md)** コントロールでレコードを選択すると、そのレコードを詳細画面では表示し、**編集および作成**画面では編集することができます。

**[編集フォーム](controls/control-form-detail.md)** コントロールを追加するには:

1. 画面を追加し、 **[編集フォーム](controls/control-form-detail.md)** コントロールを追加して、フォームの **[DataSource](controls/control-form-detail.md)** プロパティを **'Ice Cream'** に設定します。
2. **[Item](controls/control-form-detail.md)** プロパティを **Gallery1.Selected** に設定します。

これで、画面に表示するフィールドを選択できるようになりました。 各フィールドに表示するカードの種類を選択することもできます。 右側のウィンドウで変更を加えると、各 **[カード](controls/control-card.md)** コントロールの **[DataField](controls/control-card.md)** プロパティは、ユーザーが操作するフィールドに設定されます。  画面は次の例のようになります。

![Ice Cream データ ソースの表示フォーム](./media/working-with-forms/icecream-edit.png)

これらの 2 つのプロパティは、 **[表示フォーム](controls/control-form-detail.md)** コントロールのプロパティと同じです。  これだけでレコードの詳細を表示することができます。  

変更をデータ ソースに書き戻すために、 **[SubmitForm](functions/function-form.md)** 関数を指定して **[編集フォーム](controls/control-form-detail.md)** コントロールを先に進めることができます。 この機能をボタンまたはイメージ コントロールと共に使用して、ユーザーの変更を保存します。

* **[ボタン](controls/control-button.md)** コントロールを追加して、**Save** と表示されるように **[Text](controls/properties-core.md)** プロパティを設定し、 **[OnSelect](controls/properties-core.md)** プロパティに次の数式を設定します。<br>
  **SubmitForm( Form1 )**

![Ice Cream データ ソースの編集フォーム](./media/working-with-forms/edit-icecream-save.png)

この画面でナビゲーションを追加するには:

1. **[ボタン](controls/control-button.md)** コントロールをもう 1 つ追加して、**Cancel** と表示されるように **[Text](controls/properties-core.md)** プロパティを設定し、 **[OnSelect](controls/properties-core.md)** プロパティを次の数式に設定します。 <br>**ResetForm( Form1 ); Back()**
   
    この数式は、未保存の編集をすべて破棄し、前の画面を開きます。
   
    ![Ice Cream データ ソースの表示フォーム](./media/working-with-forms/edit-icecream-cancel.png)
2. フォームの **[OnSuccess](controls/control-form-detail.md)** プロパティを **Back()** に設定します。
   
    更新が正常に保存されると、前の画面 (この場合は詳細画面) が自動的に開きます。
   
    !["OnSuccess" 規則が追加された編集フォーム](./media/working-with-forms/edit-icecream-onsuccess.png)
3. **表示**画面でボタンを追加して、**Edit** と表示されるように **[Text](controls/properties-core.md)** プロパティを設定し、 **[OnSelect](controls/properties-core.md)** プロパティを次の数式に設定します。<br> **Navigate( Screen3, None )**
   
    ![[Edit] ボタンが追加された表示フォーム](./media/working-with-forms/viewform-icecream-edit.png)

これで、データを表示および入力するための 3 つの画面を備えた基本的なアプリを作成できました。  アプリを試してみるには、ギャラリー画面を表示し、F5 キーを押します (または、画面の左上隅にある次へ進む矢印の "プレビュー" ボタンを選択します)。 ピンク色の円は、各ステップでユーザーがクリックまたはタップする画面上の場所を示します。

![Ice Cream アプリを試す](./media/working-with-forms/try-icecream.png)

## <a name="create-a-record"></a>レコードの作成
ユーザーは、レコードの更新と作成の両方で、同じ**編集**フォームを操作します。 ユーザーがレコードを作成する場合は、 **[NewForm](functions/function-form.md)** 関数によってフォームが **New** モードに切り替わります。

フォームが **New** モードの場合、各フィールドの値はデータ ソースの既定値に設定されます。 フォームの **[Item](controls/control-form-detail.md)** プロパティに指定されたレコードは無視されます。  

ユーザーが新しいレコードを保存できる状態になると、 **[SubmitForm](functions/function-form.md)** が実行されます。 フォームは、正常に送信されると **EditMode** に戻ります。  

最初の画面で、 **[New]** ボタンを追加します。

1. ギャラリーを含む画面で、 **[ボタン](controls/control-button.md)** コントロールを追加します。
2. ボタンの **[Text](controls/properties-core.md)** プロパティを **New** に設定し、 **[OnSelect](controls/properties-core.md)** プロパティを次の数式に設定します。<br>
   **NewForm( Form1 ); Navigate( Screen3, None )**
   
    この数式により、**Screen3** 上の **[編集フォーム](controls/control-form-detail.md)** コントロールが **New** モードに切り替わり、ユーザーが入力できる画面が開きます。

![[Edit] ボタンが追加された表示フォーム](./media/working-with-forms/gallery-icecream-new.png)

編集および作成画面が開いた時点では、フォームは空で、ユーザーが項目を追加できます。 ユーザーが **[Save]** ボタンを選択すると、 **[SubmitForm](functions/function-form.md)** 関数によって、レコードが更新されるのではなく作成されます。 ユーザーが **[Cancel]** ボタンを選択すると、 **[ResetForm](functions/function-form.md)** 関数によってフォームが **Edit** モードに切り替わり、 **[Back](functions/function-navigate.md)** 関数によってギャラリーを閲覧するための画面が開かれます。

## <a name="delete-a-record"></a>レコードの削除
1. **表示**画面で、ボタンを追加して、**Delete** と表示されるように **[Text](controls/properties-core.md)** プロパティを設定します。
2. ボタンの **[OnSelect](controls/properties-core.md)** プロパティを次の数式に設定します。
   <br>**Remove( 'Ice Cream', Gallery1.Selected ); Back()**
   
    ![[Edit] ボタンが追加された表示フォーム](./media/working-with-forms/viewform-icecream-remove.png)

## <a name="handling-errors"></a>エラーの処理
このアプリでは、フィールドの値が無効な場合、必須のフィールドが空の場合、ネットワークから切断された場合など、その他多くの問題が発生した場合にエラーが発生します。  

何らかの理由で **[SubmitForm](functions/function-form.md)** が失敗すると、 **[編集フォーム](controls/control-form-detail.md)** コントロールの **Error** プロパティには、ユーザーに表示されるエラー メッセージが格納されます。 この情報により、ユーザーは問題を修正して変更を再送信できるようになります。または、更新を取り消すこともできます。

1. 編集および作成画面で、 **[ラベル](controls/control-text-box.md)** コントロールを追加し、それを **[Save]** ボタンのすぐ下に移動します。 ユーザーがこのコントロールを選択して変更を保存すると、エラーがわかりやすくなります。

2. **[ラベル](controls/control-text-box.md)** コントロールの **[Text](controls/properties-core.md)** プロパティを **Form1.Error** が表示されるように設定します。

    ![[Edit] ボタンが追加された表示フォーム](./media/working-with-forms/edit-icecream-error.png)

PowerApps によってデータから生成されるアプリでは、このコントロールの **[AutoHeight](controls/control-text-box.md)** プロパティが *true* に設定されているため、エラーが発生しなければ領域が使用されません。 **[編集フォーム](controls/control-form-detail.md)** コントロールの **[Height](controls/properties-size-location.md)** プロパティと **[Y](controls/properties-size-location.md)** プロパティも、エラーが発生したときに拡張されるこのコントロールに合わせて動的に調整されます。 詳細については、既存のデータからアプリを生成し、これらのプロパティを調べてください。 エラー用のテキスト ボックス コントロールは、エラーが発生していないときは非常に短くなっています。このコントロールを選択するには、( **[表示]** タブにある) **[詳細]** ビューを開く必要がある場合もあります。

![データから生成されたアプリ (エラーのテキスト コントロールが選択された編集フォーム)](./media/working-with-forms/edit-assets-error1.png)

![データから生成されたアプリ (コントロールが選択された編集フォーム)](./media/working-with-forms/edit-assets-error2.png)

## <a name="refresh-data"></a>データの更新
データ ソースはユーザーがアプリを開くたびに更新されますが、ユーザーはアプリを閉じなくてもギャラリーのレコードを更新したい場合があります。 **[Refresh]** ボタンを追加し、ユーザーがそのボタンを選択して手動でデータを更新できるようにします。

1. **[ギャラリー](controls/control-gallery.md)** コントロールが配置された画面で、 **[ボタン](controls/control-button.md)** コントロールを追加し、**Refresh** と表示されるように **[Text](controls/properties-core.md)** プロパティを設定します。

2. このコントロールの **[OnSelect](controls/properties-core.md)** プロパティを次の数式に設定します。<br> **Refresh( 'Ice Cream' )**

    ![データ ソースの更新](./media/working-with-forms/browse-icecream-refresh.png)

## <a name="search-and-sort-the-gallery"></a>ギャラリーの検索と並べ替え
PowerApps によってデータから生成されたアプリでは、閲覧画面の上部にある 2 つのコントロールを無視してきました。 ユーザーは、これらのコントロールを使用すると、1 つ以上のレコードの検索、レコードの一覧の並べ替え (昇順または降順)、またはその両方を実行できます。

![閲覧画面でのコントロールの並べ替えと検索](./media/working-with-forms/afd-browse-search-sort.png)

ユーザーが並べ替えボタンを選択すると、ギャラリーの並べ替え順序が逆になります。 この動作を作成するには、"*コンテキスト変数*" を使用して、ギャラリーの並べ替え方向を追跡します。 ユーザーがボタンを選択すると、変数が更新され、方向が逆になります。 並べ替えボタンの **[OnSelect](controls/properties-core.md)** プロパティは、**UpdateContext( {SortDescending1: !SortDescending1} )** という数式に設定されています。

**[UpdateContext](functions/function-updatecontext.md)** 関数は、**SortDescending1** コンテキスト変数がまだ存在しない場合に作成します。 この関数は、変数の値を読み取り、 **!** 演算子を使用してその反対の論理値に設定します 。 値が *true* の場合は *false* になります。 値が *false* の場合は *true* になります。

**[ギャラリー](controls/control-gallery.md)** コントロールの **[Items](controls/properties-core.md)** プロパティの数式では、このコンテキスト変数を **TextSearchBox1** コントロールのテキストと共に使用します。

```powerapps-dot
Sort( 
    If( IsBlank(TextSearchBox1.Text),
        Assets,
        Filter( Assets, TextSearchBox1.Text in Text(ApproverEmail) ) 
    ),
    ApproverEmail,
    If(SortDescending1, Descending, Ascending) 
)
```

ここで、詳しく見ていきましょう。

* 外側には **[Sort](functions/function-sort.md)** 関数があります。この関数は、テーブル、並べ替えに使用するフィールド、並べ替えの方向という 3 つの引数を受け取ります。  
  
  * 並べ替え方向は、ユーザーが **ImageSortUpDown1** コントロールを選択するたびに切り替わるコンテキスト変数から取得されます。 *true*/*false* 値は、定数の **Descending** と **Ascending** に変換されます。
  * 並べ替えに使用するフィールドは、**ApproverEmail** に固定されています。 ギャラリーに表示するフィールドを変更する場合は、この引数も変更する必要があります。
* 内側には **[Filter](functions/function-filter-lookup.md)** 関数があります。この関数は、引数としてのテーブルと、レコードごとに評価する数式を受け取ります。
  
  * テーブルは、未加工の **Assets** データ ソースで、これがフィルター処理または並べ替えの前の開始点となります。
  * この式では、**ApproverEmail** フィールド内の **TextSearchBox1** の文字列のインスタンスを検索します。  繰り返しになりますが、ギャラリーに表示するフィールドを変更する場合は、この引数も更新する必要があります。
  * **TextSearchBox1** が空の場合は、すべてのレコードを表示することを意味します。この場合、 **[Filter](functions/function-filter-lookup.md)** 関数はバイパスされます。

これは単なる一例です。 **[Filter](functions/function-filter-lookup.md)** 、 **[Sort](functions/function-sort.md)** などの関数や演算子を組み合わせることで、アプリのニーズに応じて **[Items](controls/properties-core.md)** プロパティの数式を独自に作成できます。    

## <a name="screen-design"></a>画面の設計
ここまで、複数の画面にコントロールを分散する他の方法については説明してきませんでした。 それは、多くの選択肢があり、最適な選択肢はアプリの特定のニーズによって決まるためです。

スマートフォンの画面はサイズが限られているため、閲覧、表示、編集/作成の各操作を別々の画面で行うことが必要になる場合があります。 このトピックでは、 **[Navigate](functions/function-navigate.md)** 関数と **[Back](functions/function-navigate.md)** 関数を使用して各画面を開きます。  

タブレットでは、閲覧、表示、編集/作成の各操作を 2 つの画面、または場合によっては 1 つの画面で実行できます。 後者の場合、 **[Navigate](functions/function-navigate.md)** 関数も **[Back](functions/function-navigate.md)** 関数も必要ありません。

ユーザーが同じ画面で操作している場合、ユーザーが **[ギャラリー](controls/control-gallery.md)** で選択した内容を変更できず、 **[編集フォーム](controls/control-form-detail.md)** コントロールの編集内容を失う可能性があることに注意する必要があります。  レコードに対する変更がまだ保存されていないときにユーザーが別のレコードを選択できないようにするには、ギャラリーの **[Disabled](controls/properties-core.md)** プロパティを次の数式に設定します。<br>
**EditForm.Unsaved**

