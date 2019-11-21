---
title: Power BI 用の PowerApps カスタム ビジュアル | Microsoft Docs
description: 同じデータ ソースを使用し、Power BI の他のレポート項目と同様にフィルタリングできるキャンバス アプリの埋め込みに関する手順と制限
author: chmoncay
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 11/20/2019
ms.author: chmoncay
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 422cbc151b6ee5c4adfd295800bf9747519132cf
ms.sourcegitcommit: 6c91c6dae20437f263e4eb827c6b938d6aa1b6a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2019
ms.locfileid: "74262109"
---
# <a name="powerapps-custom-visual-for-power-bi"></a>Power BI 用の PowerApps カスタム ビジュアル

Power BI を利用すると、データの洞察と適切な意思決定を行うことができ、同時に PowerApps を使用して、すべてのユーザーが、ビジネス データに接続するアプリを構築して使用することができます。 PowerApps カスタム ビジュアルを使用すると、状況に応じたデータをキャンバス アプリに渡すことができます。キャンバス アプリは、レポートを変更するとリアルタイムで更新されます。 これで、アプリ ユーザーは、ビジネスの動向を把握し、Power BI レポートとダッシュ ボードから直接アクションを実行できます。

## <a name="using-the-powerapps-custom-visual"></a>PowerApps のカスタム ビジュアルを使用する

PowerApps カスタム ビジュアルを Power BI レポートで使用するための手順を見てみましょう。

1. [AppSource](https://appsource.microsoft.com/product/power-bi-visuals/WA104381378?tab=Overview) からカスタム ビジュアルを取得したり、Power BI サービスに直接インポートしたりします。

    ![Marketplace のカスタム ビジュアル](./media/powerapps-custom-visual/powerapps-store.png) 

2. PowerApps ビジュアルをレポートに追加し、それに関連付けられているデータ フィールドを設定します。

    ![レポート データの選択](./media/powerapps-custom-visual/add-visual-set-data.png)

    既存のアプリを選択するか、またはアプリを作成できますが、レポートは Power BI サービスに発行し、Microsoft Edge または Google Chrome で開く必要があります。

3.  アプリを作成する場合は、それを作成する環境を選択できます。

    ![新規または既存のアプリ](./media/powerapps-custom-visual/create-new-or-choose-app.png)

    既存のアプリを使用する場合は、ビジュアルによって PowerApps でアプリを開くように求められます。 ビジュアルは、Power BI が PowerApps にデータを送信できるように、アプリで必要なコンポーネントが設定されます。

    新しいアプリを作成する場合、PowerApps は既にセットアップされている必要なコンポーネントで簡単なアプリを作成します。

    ![新しいアプリ](./media/powerapps-custom-visual/new-app.png)

4. 現在、PowerApps Studio では、手順 2. で設定するデータ フィールドを使用できます。 `PowerBIIntegration` オブジェクトは他の PowerApps 読み取り専用データ ソースまたはコレクションと同様に動作します。 オブジェクトを使用して、すべてのコントロールに入力できるほか、他のデータ ソースを結合したりフィルタリングしたりすることができます。

    ![ユーザー定義式](./media/powerapps-custom-visual/custom-formula.png)

    この数式は、顧客のデータ ソースと Power BI のデータを結合します。`LookUp(Customer,Customer_x0020_Name=First(PowerBIIntegration.Data).Customer_Name)`

   Power BI レポートと起動された PowerApps Studio のインスタンスは、ライブ データの接続を共有します。 これらは、どちらも開かれていますが、レポートのデータをフィルタリングまたは変更し、更新されたデータが PowerApps Studio でアプリにすぐに反映されるようにすることができます

5. アプリの構築または変更を完了した後で、PowerApps でアプリを保存および公開し、Power BI レポートにアプリを表示します。

6. 変更が完了したら、PowerApps アプリをレポートのユーザーと共有していることを確認し、レポートを保存します。

7. これで、ユーザー アクションを実行してデータから洞察を得ることができるレポートが作成されました。

    ![レポートの操作](./media/powerapps-custom-visual/working-report.gif)

    アプリを変更する必要がある場合は、編集モードでレポートを開き、PowerApps ビジュアルの **[その他のオプション]** ( **. . .** ) をクリックまたはタップし、 **[編集]** を選択します。

    ![アプリの編集](./media/powerapps-custom-visual/edit-app.png)

## <a name="limitations-of-the-powerapps-custom-visual"></a>PowerApps のカスタム ビジュアルの制限

PowerApps のカスタムビジュアルには、次の制限事項が適用されます。

- ビジュアルに関連付けられているデータ フィールドを変更する場合、省略記号 (...) を選択し、 **[編集]** を選択して Power BI サービス内でアプリを編集する必要があります。 それ以外の場合、PowerApps に変更が反映されず、アプリは予期しない方法で動作します。
- PowerApps のカスタムビジュアルでは、Power BI Desktop 内から Power BI レポートと Power BI データソースの更新をトリガーすることはできません。 アプリケーションからレポートと同じデータソースにデータを書き戻す場合、変更内容はすぐに Power BI Desktop に反映されません。 変更は、次回のスケジュールされた更新で反映されます。
- PowerApps のカスタム ビジュアルでは、データをフィルター処理したり、データをレポートに送信したりできません。
- レポートとは別に PowerApps アプリを共有する必要があります。 [PowerApps でのアプリの共有](share-app.md)の詳細を参照してください。
- Power BI Report Server と Power BI 用のモバイルアプリは、PowerApps のカスタムビジュアルをサポートしていません。
- PowerBIIntegration. Refresh () 関数を使用する場合は、 [directquery](https://docs.microsoft.com/power-bi/desktop-directquery-data-sources)をサポートするソースを使用する必要があり、データ接続は directquery メソッドを使用して作成する必要があります。
- Power BI Desktop の PowerApps は、編集中ではなく、アプリを作成するときに PowerApps Studio するデータを提供します。 Power BI Web を使用して、アプリの編集中にデータをプレビューします。

> [!NOTE]
> 最初にレポートを Power BI サービスに発行してから、アプリを作成または変更することをお勧めします。

## <a name="browser-support"></a>ブラウザーサポート

次の表に、PowerApps のカスタムビジュアルの表示、作成、および変更アクションのブラウザーのサポートを示します。 サポートされているブラウザーとアクションは、チェックマーク (&check;) によって識別されます。

|ブラウザー|モード|生成|更新
|-|-|-|-
|Microsoft Edge|&check;|&check;|&check;
|Internet Explorer 11|&check;
|Google Chrome|&check;|&check;|&check;
|Safari \*|&check;
|Mozilla Firefox
|その他すべてのブラウザー

Safari で \*、サイト間の追跡を有効にする必要があります ( **[ユーザー設定]**  >  **[プライバシー]** をオンにし、 **[クロスサイトトラッキングを防止]** する をオフにする)。

## <a name="accessibility-support"></a>ユーザー補助機能のサポート

キーボードを使用して PowerApps ビジュアル内を移動するには、次の手順を実行します。

1. 目的の PowerApps ビジュアルの Power BI レポートでフォーカスを選択します。
2. ビジュアルが強調表示されるまで、キーボードの**Tab**キーを使用します。
3. キーボードの**Ctrl + Right**キーを使用してビジュアルを入力します。
3. ビジュアルの必要なコンポーネントが選択されるまで、キーボードの**Tab**キーを使用します。

詳細については、 [Power BI アクセシビリティのドキュメント]( https://docs.microsoft.com/power-bi/desktop-accessibility)を参照してください。


## <a name="next-steps"></a>次の手順

* 単純な[ステップ バイ ステップ チュートリアル](embed-powerapps-powerbi.md)を実行する。
* [ビデオ](https://aka.ms/powerappscustomvisualvideo)をご覧ください。
