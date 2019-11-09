---
title: InfoPath フォームをキャンバス アプリに作り替える | Microsoft Docs
description: 一般的なシナリオに関する情報、およびキャンバス アプリでのこれらの項目の作成方法を使用して、InfoPath フォームの PowerApps への作り替えを開始します。
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: article
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 04/05/2018
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 505ddf8bee3108b91ef8e4ca4683ce5fe44172e8
ms.sourcegitcommit: 0f0b26122be28d674af0833247b491e9367c4932
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2019
ms.locfileid: "73899273"
---
# <a name="transform-your-infopath-form-to-powerapps"></a>InfoPath フォームを PowerApps に作り替える

InfoPath で作成したものをさらに堅牢なプラットフォームで提供する方法について説明します。

## <a name="key-advantages-of-powerapps-over-infopath"></a>PowerApps が InfoPath より優れている点

InfoPath のほとんどのパワー ユーザーと同様に、ご自分でも固有のスキル セットを使って優れたフォームを作成しています。 自分で作成したフォームに非常に満足している一方で、その限界もわかっています。&quot;古くさい&quot; 感じ、モバイル デバイスの最適なエクスペリエンスとはいえないこと、将来の見通しの不確実さ、そしてコードを記述せずに他のサービスに接続しようとするといつでも引っ掛かってしまうこと、などです。

PowerApps チームには、こうした意見やその他の多くの課題が寄せられています。 チームは、よりよいエクスペリエンスを組み込み、ユーザーの既存のビジネス スキルと技術を活用してユーザーがキャンバス アプリを作成できるように努力しています。 PowerApps を使用することで、コードを記述することなく、適切なビジネス ソリューションを速やかにビルドして展開することができます。

**PowerApps が可能にするパワフルな未来**  
PowerApps はサービスとしてのソフトウェア (SaaS) プラットフォームであり、高機能のアプリを短期間で開発し、追加作業なしで Web、SharePoint、Dynamics 365、Teams、Power BI、モバイル デバイスに展開できるように設計されています。 公開されているアプリへの URL を伝えるだけで簡単に展開できるので、更新も簡単に行うことができます。

**アプリの共有**  
アプリを構築して、それを iOS や Android デバイスに公開しようとしたことがあればわかるはずですが、 面倒です。 第 2 のアプリを展開したり、既存のアプリを更新したりする場合、ユーザーは、はるかに多くの手順を実行する必要があります。 PowerApps ではそのようなことはありません。 ユーザーは自分のデバイスに PowerApps Mobile をインストールし、サインインします。 これでユーザーは共有されているすべての高機能アプリを利用できるようになります。 その後は、これらのアプリを更新したり新しいアプリをユーザーにプッシュしたりすると、ユーザーのデバイスにこれらのアプリが表示されるようになります。 デバイス管理の苦労がないモバイル アプリは、ビジネスにとって大きなメリットです。

**モバイルについて**  
PowerApps では、ユーザーのモバイル デバイスの機能を活用することができます。 アクセラレータ、カメラ、コンパス、接続情報、位置信号などのすべてにアプリ内からアクセスできます。 これにより、アプリ構築のあらゆる可能性を活用できます。 もちろん、PowerApps ではタッチ機能が自動的に有効になり、アプリ構築時に余分なコーディングは必要ありません。

**既成の枠を破る**  
InfoPath では、通常、1 つのソースからのデータを使用します。 ただし、別のソース (別のサイト コレクションの SharePoint リストなど) を更新したり、外部サービスに接続したりする場合には、注意が必要です。 コード ビハインドなどの概念に悩まされることになります。 PowerApps は、複数のデータ ソースとサービス接続を 1 つのアプリで使用できるように設計されています。 現在、 [200 以上のコネクタ](connections-list.md#all-standard-connectors)では、オンプレミスとクラウドのデータの組み合わせがサポートされています。たとえば、Microsoft Office 365 や、Power オートメーションや Dynamics 365 などの Azure サービスが含まれます。 Dropbox、Google、Salesforce、Slack などの人気のあるターゲットを含む多数のサード パーティ サービスに接続することもできます。

元のデータがあった場所だけでなく、ユーザーが必要とする場所を含むようにソリューションを拡張できます。

## <a name="powerapps-and-sharepoint-even-better-together"></a>PowerApps と SharePoint: 相乗効果

PowerApps は、SharePoint のエクスペリエンスを 2 つの方法で向上させる優れたツールです。 SharePoint リスト用のフォームをカスタマイズしたり、SharePoint データを操作するためのスタンドアロン アプリを作成したりできます。

**[Customizing a SharePoint form]\(SharePoint フォームのカスタマイズ\)** は、ユーザーが日常の作業に使っているリストの項目を追加、表示、または編集する方法をカスタマイズしたい場合に最適です。 **[Customize Forms]\(フォームのカスタマイズ\)** をクリックすると、コンテキストに基づいてモード (新規/編集/表示) を変更する単一画面の &quot;フォーム アプリ&quot; が作成されます。 これらのアプリは SharePoint によって管理されます。そのアクセス許可は、編集/表示のためのリストのアクセス許可と同じです。

**SharePoint から PowerApps キャンバス アプリを作成する**と、モバイル デバイスでアプリを単独で実行することができます。 アプリを SharePoint ページに埋め込むこともできます。 これをクリックすると、3 画面のアプリ (参照リスト、詳細の表示、および項目の作成/更新) が作成されます。 これらのアプリのアクセス許可/共有モデルは、SharePoint には関連付けられておらず、PowerApps から管理されます。

2 つのオプションの違いを理解したので、次のセクションではそれぞれの使い方の概要を説明します。

## <a name="sharepoint-forms"></a>SharePoint フォーム

PowerApps チームと SharePoint チームは協力して、SharePoint で使用するためのカスタマイズ ストーリーを作成しています。 ほとんどの InfoPath 開発者は、SharePoint と対話するために InfoPath を学習します。 SharePoint はすばらしいものですが、既定のフォームは少し平凡であり、InfoPath なしではカスタマイズやビジネス ロジックに対応していません。 しかし、それももう昔の話です。

PowerApps を使えば、ネイティブ機能としてリスト フォームをカスタマイズできます。 それにより、PowerApps のすべての機能を利用できます。 次のスクリーンショットは、Power BI レポートが埋め込まれた PowerApps フォームの例です。 ソリューション全体は、15 分もかからずに作成できました。

![SharePoint の統合](./media/transform-infopath/sharepoint-integration.png)

PowerApps のもう 1 つの重要な機能は、同じフォームから別の SharePoint サイト コレクションまたは別の環境に簡単に接続できることです。 たとえば、SharePoint Online のデータと SharePoint オンプレミス環境のデータを同時に表示して更新する 1 つのフォームを作成したいことはありませんか。 大丈夫。 [オンプレミスデータゲートウェイ](gateway-management.md)をインストールすると、数分で起動し、PowerApps、Power BI、電源自動化、Azure Logic Apps オンプレミスデータとの接続が開始されます。 ファイアウォール規則を変更する必要はありません。 このアプリを Power の自動化に接続することで、さらに一歩進めていくことができます。

## <a name="a-standalone-sharepoint-app"></a>スタンドアロン SharePoint アプリ

リスト フォームのエクスペリエンスを更新するだけではなく、完全に構築したい場合は、SharePoint データに基づくスタンドアロン アプリでこの手法を使います。 これは初めて作るものとしても適しており、PowerApps キャンバスのしくみを学習し、さまざまなデータ ソースから将来のアプリの開発を始めることができます。

開始するには、次の手順に従います。

1. アプリの構築元となる SharePoint リストを開きます。
1. メニュー バーで **[PowerApps]** を選択し、 **[アプリの作成]** を選択します。
1. 名前を指定し、 **[作成]** を選択します。

PowerApps によってアプリが作成され、それをカスタマイズすることができます。

最初のアプリ用に、異なる型のフィールドを 2 つだけ含むシンプルなカスタム リストを使って開始します。 これにより、苦労することなく強固な基盤を築くことができます。 心配しないでください。すぐに習熟して複雑なアプリを作成できるようになります。 この最初のアプリを作成する手順については、こちらの[ドキュメント](app-from-sharepoint.md#generate-an-app-from-within-sharepoint-online)またはコミュニティのこちらの[ビデオ](https://youtu.be/BnYe_7fpZRM)をご覧ください。 次の例では、InfoPath の一般的なタスクと PowerApps でのその方法を示します。 これらの各タスクではシンプルな SharePoint リスト アプリを作成します。

## <a name="how-do-you-do-that-with-powerapps"></a>PowerApps での方法

基本的な概念を理解したので、次に進みます。 最初のアプリが身についたので、このセクションでは InfoPath の一般的な概念を PowerApps に適用します。

**値に基づいてフィールドを非表示/表示/ロックする**  
成功したフォームの多くは、たとえば値またはアクションに基づいてフィールドの状態を変更するといった、強力なビジネス ロジックを適用しています。 PowerApps では、コントロールの **DisplayMode** プロパティを **Edit** または **View** に設定して、ユーザーがフィールドを変更できるかどうかを指定できます。 簡単な **If** 式を使用して、条件付きでこれを行うこともできます。 最初に、編集するカードを選んでから、ロック アイコンを選択します。 この手順によりカードをロック解除して、値が変更できるようになります。

![データ カードの非表示/表示/ロック](./media/transform-infopath/hide-show-lock.png)

右側のウィンドウで、 **[DisplayMode]** プロパティまでスクロールして編集できるようにします。

![If-Else ステートメント式](./media/transform-infopath/if-else-statement.png)

この例では **If** 式を使います。

```If(ThisItem.Color = "Blue", DisplayMode.View, DisplayMode.Edit)```

この数式は、現在の項目の **Color** フィールドが **Blue** の場合は **Animal** フィールドを読み取り専用にし、 それ例外の場合はフィールドを編集可能にします。

カードを読み取り専用にするのではなく、非表示にするには、同様の関数を **DisplayMode** のすぐ上の **Visible** プロパティに挿入します。

また、ユーザーのメール アドレスが承認者のメール アドレスと一致する場合にのみ承認ボタンが表示されるようにすることもできます (ヒント: **User () を使用します。** 現在のユーザーの電子メールアドレスにアクセスするための電子メール。)そのため、承認者の電子メールアドレスを**ストアに格納**し、ボタンの**Visible**プロパティを次の数式に設定します。

```If( YourDataCard.Text = User().Email, true, false )```

**条件付き書式**  
上でフィールドを非表示にしたのと同様の方法で、ユーザーへのフィードバックを表示できます。 入力された値が有効範囲外の場合はテキストを赤で強調表示したり、ユーザーがファイルをアップロードした後にアップロード ボタンのテキストと色を変更します。 どちらも **Color** や **Visible** などのプロパティで **If** などの関数を使って行うことができます。

たとえば、**If** 関数と [IsMatch](functions/function-ismatch.md) 関数を組み合わせて使って、ユーザーが入力ボックスに正しい書式のメール アドレスを入力しなかった場合、メール アドレス フィールドのテキストの色を赤に変更できます。 これを行うには、**TextInput1** (ユーザーがメール アドレスを入力する場所) の **Color** の値を次の数式に設定します。

```If( IsMatch(TextInput1.Text, Email), Black, Red )```

**IsMatch** は、メールなどの多種多様な定義済みパターンをサポートしている他、ユーザーが独自にパターンを作成することもできます。 条件付き書式については、こちらの[コミュニティ ビデオ](https://powerusers.microsoft.com/t5/Video-Webinar-Gallery/PowerApps-Conditional-Formatting-and-Popups/m-p/84962)をご覧ください。

**ロール ベースのセキュリティの実装**  
最初に検討する関数は [DataSourceInfo](functions/function-datasourceinfo.md) です。 データ ソースから戻る情報は異なりますが、多くの場合、この数式を使って、ユーザーにデータを編集するアクセス権があるかどうかを確認できます (*YourDataSource* はご自分のデータ ソースの名前に置き換えます)。

```DataSourceInfo( YourDataSource, DataSourceInfo.EditPermission )```

これにより、ユーザーが編集アクセス権限を持っている場合にのみ、フォームやボタンを表示できます。 関数で照会できる情報の完全な一覧については、[DataSourceInfo](functions/function-datasourceinfo.md) のドキュメントをご覧ください。

Active Directory グループを使ってアプリ内のボタンやフォームへのアクセスを管理する場合は、さらに詳しく知る必要があります。 これを行うには、PowerApps の柔軟性を利用し、Microsoft Graph API を使って独自のコネクタを作成します。 困難に思える場合は、この[ブログ記事](https://powerapps.microsoft.com/blog/implementing-role-based-permission/)のステップ バイ ステップ ガイダンスに従うことができます。

**アプリからのメールの送信**  
PowerApps からメール メッセージを送信する方法はたくさんありますが、最も簡単な方法は、Office 365 Outlook コネクタを使うことです。 このコネクタを使用すると、アプリからユーザーとしてメッセージを送信できます。 メール メッセージを受け取ったり、メールボックスの他のタスクを実行したりすることもできます。 メールの送信については、[ドキュメント](connections/connection-office365-outlook.md)またはこちらのコミュニティ [ビデオ](https://powerusers.microsoft.com/t5/Video-Webinar-Gallery/Send-an-email-from-PowerApps/m-p/74349)をご覧ください。

Power オートメーションを使用して、作成したフローにアプリを接続することで、より複雑なメッセージ (たとえば、SharePoint 承認ワークフローの一部として) を送信できます。 アプリを Power の自動化に接続すると、PowerApps のように、外部のデータとサービスに非常によく接続されているワークフローエンジンを最大限に活用できるようになります。 PowerApps と Power の自動化を接続する方法の詳細については、こちらの[ドキュメント](using-logic-flows.md)を参照してください。

まだ探しているメール オプションが見つからない場合は、Benchmark Email、Gmail、MailChimp、Outlook.com、SendGrid、SMTP などに対する PowerApps コネクタも利用できます。 接続性は PowerApps の長所です。

**ワークフロー**  
ワークフロー エンジンに触れずにビジネス アプリやビジネス ロジックについて説明するのは容易ではありません。 よいニュースは、PowerApps チームは別のワークフロー エンジンを提供するようなことはしていません。 代わりに、パワー自動化サービスへの堅牢なコネクタが提供されます。 使いやすいワークフロー エンジンを通して [200 以上のさまざまなサービス](https://flow.microsoft.com/connectors/)を使ってプロセスとタスクを自動化できます。 PowerApps と Power の自動化を接続する方法の詳細については、こちらの[ドキュメント](using-logic-flows.md)を参照してください。

**PowerApps での変数**  
ソリューションを作成するときは、変数を含める必要があると考えるのが自然です。 PowerApps には数種類の変数が用意されていますが、必要なときにのみ使います。 データを取得し、変数に格納して、その変数を参照することを考えるのではなく、データを直接参照することを考えてください。 Excel と比較すると、このモデルをより深く理解することができます。 Excel では、Total は変数ではなく他のフィールドの合計です。 したがって、シートの他の場所でその値を使う場合は、合計を計算したセルを指定します。 これらはすべて[ドキュメント](working-with-variables.md)で詳しく説明されています。 別の思考プロセスを受け入れてください。

それでも変数が必要な場合 (いろいろなケースがあります)、これは異なるオプションを理解する役に立ちます。 PowerApps では変数を定義する必要がないことに留意してください。 関数を使って名前と格納する値を指定するだけで、変数が作成されます。 **[表示]** タブ**で変数を選択する**と、作成した変数を表示できます。変数はメモリに保持され、アプリを閉じるとその値は失われます。 次の種類の変数を作成できます。

- グローバル変数は最も一般的なものです。 [Set](functions/function-set.md) 関数を使ってグローバル変数の値を指定すると、その変数がアプリ全体で使用できるようになります。

    ```Set( YourVariable, YourValue )```

    アプリ全体で、名前を使って *YourVariable* を参照できます。

- コンテキスト変数は、それが定義されている画面でのみ使用できます。 画面を終了するとそれらはリセットされます。 コンテキスト変数は、たとえば、前の画面から渡された情報を格納したり、フォームが送信されたかどうかを追跡したりするためによく使われます。 コンテキスト変数を設定するには、この例のように、[UpdateContext](functions/function-updatecontext.md) 関数を使用します。

    ```UpdateContext( { Submitted: "true" } )```

    この例では、**Submitted** という名前の変数の値を **true** に設定します。 送信ボタンの **OnSelect** プロパティにこの数式を追加して、情報が送信されたことを追跡し、すべてのフィールドを読み取り専用に変更することができます。

- コレクションには、個別に更新可能な情報のテーブルが格納されます。 たとえば、ユーザーが送信するさまざまな SharePoint 項目にタグを付けるショッピング カートを作成するには、[Collect](functions/function-clear-collect-clearcollect.md) を使用します。 概念の仕組みについては、コミュニティの[ビデオ](https://powerusers.microsoft.com/t5/Video-Webinar-Gallery/Learn-about-PowerApps-Collections/m-p/89180)をご覧ください。

**カスケード ドロップダウン**  
カスケード ドロップダウンは、たとえば、前のドロップダウンで選択された値に基づいて、次のドロップダウンに表示される項目をフィルター処理できるため、非常に便利です。 PowerApps では、アプリで 2 つのデータ ソースを使って作成されることがよくあります。 最初のデータ ソースのデータを表示または更新し、2 番目のデータ ソースにカスケード効果を作成するための値を格納します。 2 番目のデータ ソースと選択オプションの例を次の図に示します。

![カスケード ドロップダウン](./media/transform-infopath/cascading-dropdowns.png)

この例では、**ddSelectType** という名前のドロップダウンを追加し、その **Items** プロパティを次の式に設定できます。

```Distinct( Impacts, Title )```

ドロップダウンには、Cost、Program Impact、Schedule のみが表示されます。 次に、2 番目のドロップダウンを追加して、その **Items** プロパティを次の式に設定できます。

```Filter( Impacts, ddSelectType.Selected.Value in SCategory )```

このようにしてカスケード ドロップダウンを作成できます。 詳細については、PowerApps チームの投稿「[SharePoint: Cascading Dropdowns in 4 Easy Steps!](https://powerusers.microsoft.com/t5/PowerApps-Community-Blog/SharePoint-Cascading-Dropdowns-in-4-Easy-Steps/ba-p/16248)」(SharePoint: 4 つの簡単な手順でドロップダウン カスケードを作成する)、 またはこの[コミュニティ ビデオ](https://powerusers.microsoft.com/t5/Video-Webinar-Gallery/PowerApps-Cascading-Dropdown/m-p/92813)をご覧ください。 心配しなくても SharePoint なしで簡単に行うことができます。

**1 つのスーパー アプリを作成しない**  
PowerApps では、アプリから別のアプリを呼び出すことができます。 そのため、大規模な InfoPath フォームを 1 つ作成する代わりに、相互に呼び出すアプリのグループを作成したり、データを受け渡すことで、開発をよりシンプルにできます。

## <a name="next-steps"></a>次の手順

以上で PowerApps アプリを作成する準備ができました。 続けて、以下の役に立つリンクをご覧ください。これには PowerApps コミュニティ サイトへのリンクなどが含まれます。 コミュニティを利用すれば、自分だけで行うよりスキルを速く高めることができます。

[**数式のリファレンス**](formula-reference.md) - 既定の関数をいくつか見るだけでも、刺激を受けるのによい方法です。

[**PowerApps コミュニティ**](https://powerusers.microsoft.com/t5/PowerApps-Community/ct-p/PowerApps1) - 例を参照し、他のユーザーと情報交換し、質問して回答を受け取り、PowerApps コミュニティの拡大に手を貸してください。
