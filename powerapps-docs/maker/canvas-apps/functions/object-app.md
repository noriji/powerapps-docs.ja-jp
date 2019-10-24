---
title: アプリオブジェクト |Microsoft Docs
description: 構文と例を含む PowerApps の App オブジェクトの参照情報
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 05/29/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: b0ab20ce5e0700337bb059644c458a2665d20f1e
ms.sourcegitcommit: 57b968b542fc43737330596d840d938f566e582a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2019
ms.locfileid: "71983581"
---
# <a name="app-object-in-powerapps"></a>PowerApps のアプリオブジェクト

現在実行中のアプリに関する情報を提供し、アプリの動作を制御します。

## <a name="description"></a>Description

コントロールと同様に、 **App**オブジェクトには、表示されている画面を識別するプロパティが用意されています。また、変更内容を保存するようにユーザーに要求することもできます。 すべてのアプリには**アプリ**オブジェクトがあります。

**アプリ**オブジェクトの一部のプロパティの数式を作成できます。 **ツリービュー**ペインの上部で、他のコントロールまたは画面と同じように、**アプリ**オブジェクトを選択します。 オブジェクトのプロパティの1つを表示して編集するには、数式バーの左側にあるドロップダウンリストから選択します。

> [!div class="mx-imgBorder"]
> ツリービューペインで ![The アプリオブジェクト ](media/object-app/appobject.png)

## <a name="activescreen-property"></a>ActiveScreen プロパティ

**Activescreen**プロパティは、表示されている画面を識別します。

このプロパティは、画面オブジェクトを返します。このオブジェクトを使用して、画面のプロパティを参照したり、別の画面と比較して、どの画面が表示されているかを判断したりすることができます。 また、式**App.ActiveScreen.Name**を使用して、表示されている画面の名前を取得することもできます。

表示されている画面を変更するには、 **[Back](function-navigate.md)** または **[Navigate](function-navigate.md)** 関数を使用します。

## <a name="onstart-property"></a>OnStart プロパティ

**OnStart**プロパティは、ユーザーがアプリを起動したときに実行されます。 アプリの製造元は、多くの場合、このプロパティを使用して次のタスクを実行します。

- **[Collect](function-clear-collect-clearcollect.md)** 関数を使用して、データをコレクションに取得してキャッシュします。
- **[Set](function-set.md)** 関数を使用してグローバル変数を設定します。
- **[Navigate](function-navigate.md)** 関数を使用して最初の画面に移動します。

この数式は、最初の画面が表示される前に評価されます。 画面が読み込まれていないため、 **[Updatecontext](function-updatecontext.md)** 関数でコンテキスト変数を設定することはできません。 ただし、 **Navigate**関数でコンテキスト変数を渡すことはできます。

**Onstart**プロパティを変更した後、**ツリービュー**ペインで**アプリ**オブジェクトをポイントし、表示される省略記号 (...) を選択して、 **[実行 onstart]** を選択してテストします。 アプリが初めて読み込まれるときとは異なり、既存のコレクションと変数は既に設定されています。 空のコレクションから始めるには、 **collect**関数ではなく、 **[clearcollect](function-clear-collect-clearcollect.md)** 関数を使用します。

> [!div class="mx-imgBorder"]
> 実行 OnStart ](media/object-app/appobject-runonstart.png) の ![App 項目のショートカットメニュー

## <a name="confirmexit-properties"></a>ConfirmExit プロパティ

未保存の変更が失われないようにしたいと考えています。 **Confirmexit**および**confirmexitmessage**プロパティを使用して、アプリを閉じる前にユーザーに警告します。

> [!NOTE]
> **Confirmexit**は、Power BI や SharePoint など、に埋め込まれているアプリでは機能しません。

> [!NOTE]
> 現時点では、**遅延読み込み**のプレビュー機能が有効になっている場合 (新しいアプリでは既定)、これらのプロパティは最初の画面でのみコントロールを参照できます。 参照が行われた場合、PowerApps Studio にエラーは表示されませんが、結果として発行されるアプリは PowerApps Mobile またはブラウザーで開かれません。 この制限を引き上げるために積極的に取り組んでいます。 それまでの間は、[**ファイル** > **アプリの設定**]  >  **[詳細設定]** ( **[プレビュー機能]** の下) で**遅延読み込み**をオフにすることができます。

### <a name="confirmexit"></a>ConfirmExit

**Confirmexit**はブール型のプロパティです。 *true*の場合、アプリを閉じる前に確認ダイアログボックスが開きます。 既定では、このプロパティは*false*であり、ダイアログボックスは表示されません。

このプロパティを使用すると、ユーザーが変更を行っても保存されていない場合に、確認ダイアログボックスが表示されます。 変数およびコントロールのプロパティを確認できる数式を使用します (たとえば、 [**Edit form**](../controls/control-form-detail.md)コントロールの**未保存**のプロパティ)。

次の例のように、データが失われる可能性がある場合は、確認のダイアログボックスが表示されます。

- [**Exit**](function-exit.md)関数を実行しています。
- アプリがブラウザーで実行されている場合:
  - ブラウザーを閉じるか、アプリが実行されているブラウザータブを閉じます。
  - ブラウザーの [戻る] ボタンを選択します。
- アプリが PowerApps Mobile (iOS または Android) で実行されている場合:
  - [**Launch**](function-param.md)関数を実行しています。<br>**起動**関数は、データが失われないように別のタブが開いているため、ブラウザーでダイアログボックスをトリガーしません。
  - PowerApps Mobile で別のアプリに切り替えるためのスワイプ。
  - Android デバイスで [戻る] ボタンを選択します。

確認ダイアログボックスの正確な外観は、デバイスと PowerApps のバージョンによって異なります。

[確認] ダイアログボックスは PowerApps Studio に表示されません。

### <a name="confirmexitmessage"></a>ConfirmExitMessage

既定では、[確認] ダイアログボックスに、 **"保存されていない変更がある可能性があります"** などの一般的なメッセージが表示されます。 ユーザーの言語。

確認ダイアログボックスにカスタムメッセージを提供するには、 **Confirmexitmessage**を使用します。 このプロパティが*空白*の場合は、既定値が使用されます。 カスタムメッセージは、確認ダイアログボックス内に収まるように、必要に応じて切り捨てられます。そのため、メッセージは最大数行に保持されます。

ブラウザーでは、ブラウザーからの一般的なメッセージと共に、確認のダイアログボックスが表示される場合があります。

### <a name="example"></a>例

1. **Accountform**と**contactform**の2つのフォームコントロールを含むアプリを作成します。

1. **アプリ**オブジェクトの**confirmexit**プロパティを次の式に設定します。

    ```powerapps-dot
    AccountForm.Unsaved Or ContactForm.Unsaved
    ```

    このダイアログボックスは、ユーザーがいずれかの形式でデータを変更し、変更を保存せずにアプリを終了しようとした場合に表示されます。

    > [!div class="mx-imgBorder"]
    > [![Generic の確認] ダイアログボックス ](media/object-app/confirm-native.png)

1. **アプリ**オブジェクトの**confirmexitmessage**プロパティを次の数式に設定します。

    ```powerapps-dot
    If( AccountsForm.Unsaved,
        "Accounts form has unsaved changes.",
        "Contacts form has unsaved changes."
    )
    ```

    このダイアログボックスは、ユーザーがアカウントフォームのデータを変更し、変更を保存せずにアプリを終了しようとした場合に表示されます。

    > [!div class="mx-imgBorder"]
    > ![Form 固有の確認 ダイアログボックス ](media/object-app/confirm-native-custom.png)
