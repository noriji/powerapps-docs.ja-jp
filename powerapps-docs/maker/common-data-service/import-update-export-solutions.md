---
title: ソリューションのインポート、更新およびエクスポート| MicrosoftDocs
description: PowerApps でソリューションのインポート、更新およびエクスポートする方法について
ms.custom: ''
ms.date: 09/30/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
author: Mattp123
ms.assetid: 56363ea3-ea76-4311-9b7a-b71675e446fb
caps.latest.revision: 57
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="import-update-and-export-solutions"></a>ソリューションのインポート、更新およびエクスポート 

 次の手順に従って手動でソリューションをインポートできます。 信頼できるソースから取得したソリューションだけをインポートしてください。 カスタマイズには、外部ソースにデータを送信できるコードが含まれている場合があります。   
  
1.  左のナビゲーション ウィンドウから、**ソリューション**を選択します。  
  
2.  ソリューションの一覧メニューで、**インポート**を選択します。  

    > [!div class="mx-imgBorder"]  
    > ![インポート ソリューション](media/solution-import.png "インポート ソリューション") 
  
3.  **ソリューションのインポート** ダイアログの、**ソリューション パッケージの選択**のステップにおいて、**ファイルの選択**を選択し、インポートするソリューションが含まれている圧縮 (.zip または .cab) ファイルを参照します。 
  
4.  **次へ**を選択します。  
  
5.  ソリューションに関する情報を表示します。 **インポート**を選択します。  
  
6. インポートが完了するまで、数分待つ必要がある場合があります。 結果を表示し、**閉じる**を選択します。  
  
 公開が必要な変更をインポートした場合、それらを使用可能にする前に、カスタマイズを公開する必要があります。 
  
 インポートが正常に完了しない場合、キャプチャされたエラーまたは警告のレポートが表示されます。 インポートが失敗した原因に関する詳細をキャプチャするために、**ログ ファイルのダウンロード**を選択します。 インポートの失敗の最も一般的な原因は、ソリューションに必要なコンポーネントが含まれていなかったことです。  
  
 ログ ファイルをダウンロードするとき、Office Excel を使用して XML ファイルを開き、内容を表示します。  
  
> [!NOTE]
>  アクティブなルーティング規則セットを編集することはできません。 したがって、同じ ID のルールが既に存在する環境にアクティブなルーティング規則セットを組み込むソリューションをインポートする場合、インポートは失敗します。 詳細情報: [サポート案件を自動的にルーティングするルールを作成する](https://docs.microsoft.com/dynamics365/customer-engagement/customer-service/create-rules-automatically-route-cases)  
  
<a name="BKMK_UpdateSolutions"></a>   

## <a name="update-solutions"></a>ソリューションの更新  
 既存の管理ソリューションに更新をインストールする場合があります。 手順は、各種オプションを取得することを除けば、新しく管理ソリューションをインストールする場合と同じです。 他から取得したソリューションを更新している場合は、どのオプションを選択する必要があるかについてソリューション発行者からのガイダンスが必要です。  
  
1.  左のナビゲーション ウィンドウから、**ソリューション**を選択します。
  
2.  ソリューションの一覧メニューで、**インポート**を選択します。  
  
3.  **ソリューションのインポート** ダイアログの、**ソリューション パッケージの選択**のステップにおいて、**ファイルの選択**を選択し、更新するソリューションが含まれている圧縮 (.zip または .cab) ファイルを参照します。

4.  **次へ**を選択します。  
  
5.  ソリューションに関する情報を表示し、**次へ**を選択します。 このページには、**このソリューション パッケージには、インストール済のソリューションの更新が含まれています**という黄色バーが表示されます。  
  
6.  次のオプションがあります。  
  
    - **カスタマイズを維持 (推奨)**  
  
         このオプションを選択すると、コンポーネント上で実行されたアンマネージドなカスタマイズが維持されますが、このソリューションに含まれる更新プログラムの一部が適用されない可能性があります。  
  
    - **カスタマイズを上書き**  
  
         このオプションを選択すると、このソリューションに含まれるコンポーネントに対してこれまでに実行されたアンマネージド ソリューションをすべて上書きします。 このソリューションに含まれるすべて更新が有効になります。  
  
     適切なオプションを選択し、**次へ**を選択します。  
  
7.  インポートが完了するまで、数分待つ必要がある場合があります。 結果を表示し、**閉じる**を選択します。  
  
 公開が必要な変更をインポートした場合、それらを使用可能にする前に、カスタマイズを公開する必要があります。 
  
 ソリューション発行者により、既存のアンマネージド カスタマイズをエクスポートし、オプションを使用して管理ソリューションを更新しカスタマイズを上書きし、それからアンマネージド カスタマイズを再インポートするように指示される場合があります。 これにより、カスタマイズを保持したまま、期待している変更が適用されます。  
  
<a name="BKMK_ExportSolutions"></a>   

## <a name="export-solutions"></a>エクスポート ソリューション  
 カスタマイズを使用またはエクスポートするには、アンマネージド ソリューションを作成することをお勧めします。 その後、カスタマイズを定期的にエクスポートすることで、万一のためのバックアップを持つことができます。 管理ソリューションはエクスポートできません。 PowerApps からソリューションをエクスポートするか、またはクラシック エクスペリエンスを使用してエクスポートすることができます。 
 
> [!IMPORTANT]
> 既定のソリューションのエクスポートはサポートされていません。 

### <a name="export-from-powerapps"></a>PowerApps からのエクスポート
  
1.  左のナビゲーション ウィンドウから、**ソリューション**を選択します。   
  
2.  一覧でエクスポートするソリューションを選択し、**エクスポート**を選択します。 

3.  **アンマネージド**または**マネージド**のパッケージ タイプを選択します。 エクスポートを開始するのに、数分間かかる場合があります。 終了後、エクスポートされた zip ファイルは、Web ブラウザーで指定されたダウンロード フォルダーで使用可能になります。

    > [!div class="mx-imgBorder"]  
    > ![エクスポート ソリューション](media/solution-export.png "エクスポート ソリューション") 

### <a name="export-from-the-classic-experience"></a>クラシック エクスペリエンスからのエクスポート

1.  左側のナビゲーションから**ソリューション**を選択し、それから**クラシックに切り替え**を選択します。 
  
2.  一覧でエクスポートするソリューションを選択し、**エクスポート**を選択します。 
  
3.  **カスタマイズの公開**の手順で、公開済のカスタマイズのみがエクスポートされること、また**次へ**を選択する前に**すべてのカスタマイズの公開**という選択肢があるということが忠告されます。  
  
4.  ソリューションに不足している必須コンポーネントがある場合、**不足している必須コンポーネント**の手順が表示されます。 アンマネージド ソリューションとしてこれを元の環境にインポートする場合は、この警告を無視できます。 それ以外は、ダイアログの指示に従い、エクスポートをキャンセルし、必要なコンポーネントを追加します。  
  
5.  **システム設定のエクスポート (詳細)** の手順で、ソリューションに含める特定のシステム設定を選択できます。 ソリューションがシステム設定のグループのいずれかに基づく場合、それら選択し、**次へ**を選択します。  
  
     各オプションに含まれる設定の詳細については、下の**ソリューション エクスポートのオプションの設定**を参照してください。  
  
6.  **パッケージの種類**手順で、ソリューションを**アンマネージド**または**管理**のいずれとしてエクスポートするか選択する必要があります。  
  
7.  次の手順では、特定バージョンのターゲット ソリューションを選択することができます。 このオプションは、通常、以前のバージョンと互換性のあるソリューションをエクスポートしたい ISV によって使用されます。 このソリューションを、現在使用している環境のバージョンと同じバージョンにアップグレードされていない環境にインポートする場合を除き、既定値を受け入れます。   
  
8.  **エクスポート**を選択して、ソリューション ファイルをダウンロードします。  
  
 ファイルをダウンロードする処理は、Web ブラウザーによって異なります。  

<a name="BKMK_SettingsOptionsOnSolutionExport"></a>  
 
## <a name="settings-options-for-solution-export"></a>ソリューション エクスポートのオプションの設定  
 PowerApps からソリューションをエクスポートする場合は、このセクションを無視してください。 次の表には、クラシック エクスペリエンスからソリューションをエクスポートするときに使用できるオプションが示されます。  
  
|グループ|設定|説明|  
|-----------|-------------|-----------------|  
|自動付番|キャンペーンの接頭辞|キャンペーンの付番に使用する接頭辞です。|  
|サポート案件の接頭辞|アプリ全体ですべてのサポート案件に使用する接頭辞です。|  
|契約の接頭辞|アプリ全体ですべての契約に使用する接頭辞です。|  
|請求書の接頭辞|アプリ全体ですべての請求書番号に使用する接頭辞です。|  
|記事の接頭辞|アプリですべての記事に使用する接頭辞です。|  
|受注の接頭辞|アプリ全体ですべての受注に使用する接頭辞です。|  
|一意の文字列の長さ|請求書番号、見積もり番号、受注番号に追加する文字数です。|  
|カレンダー|カレンダーの種類|システムのカレンダーの種類。 既定ではグレゴリオ米国暦に設定します|  
|日付の表示形式コード|Common Data Service 全体で表示される日付の表示方法に関する情報|  
|日付の区切り記号|アプリ全体で、日付の月、日、年の区切りとして使用される文字です。|  
|最長の予定期間|設定可能な予定期間の最大日数です。|  
|週番号の表示|アプリ全体で、カレンダーに週番号を表示するかどうかを指定する情報です。|  
|時間の表示形式コード|アプリ全体での時間の表示方法を指定する情報です。|  
|週の開始曜日コード|アプリ全体で指定された週の最初の曜日です。|  
|カスタマイズ|アプリケーション モードが有効|アドレス バー、ツール バー、およびメニュー バーのないブラウザー ウィンドウでのアプリの読み込みが有効かどうかを示します。|  
|電子メールの追跡|未解決アドレスの電子メール送信を許可|ユーザーが未解決の関係者に電子メールを送信できるかどうか示します (関係者は電子メール アドレスを持っている必要があります)。|  
|内部電子メールを無視|アプリ ユーザーまたはキューから送信された受信メールを追跡するかどうかを示します。|  
|最大の追跡番号|リサイクルする前の最大追跡番号です。|  
|セキュリティで保護されたフレームを電子メール用に表示|security='restricted' 属性セットで IFRAME の Web フォームの電子メール本文を表示するようフラグできます。 これは追加のセキュリティで、資格情報のプロンプトが発生することがあります。|  
|追跡プレフィックス|追跡トークンの接頭辞の履歴リストです。|  
|追跡トークンの基準番号|別の展開に所属するユーザーに対して個別の追跡トークン ID を提供する場合に使用する基準番号です。|  
|追跡トークンの桁数|追跡トークン ID の表示桁数です。|  
|全般|添付ファイルのブロック|危険であると考えられる特定の添付ファイルの種類のアップロードまたはダウンロードを禁止します。|  
|通貨の表示形式コード|アプリ全体での通貨記号の配置方法に関する情報です。|  
|通貨記号|通貨記号|  
|氏名の表示順序|アプリ全体で表示される名前の表示順序です。|  
|プレゼンス有効|IM プレゼンスが有効かどうかを示す情報です。|  
|負の形式|アプリ全体での負の数値の表示方法を指定する情報です。|  
|数値の表示形式|アプリ全体での数字の表示方法を指定する情報です。|  
|小数以下の精度の設定値|価格に使用できる小数点以下の桁数です。|  
|割り当て時に以前の所有者への共有を設定|譲受人について、以前の所有者に共有を設定するかどうかを指定する情報です。|  
|マーケティング|自動反応作成を許可|自動反応作成を許可するかどうかを示します|  
|購読の自動取り消しを許可|購読の自動取り消しを許可するかどうかを示します。|  
|購読の自動取り消しの受信確認を許可|購読の自動取り消しの受信確認電子メールの送信を許可するかどうかを示します。|  
|マーケティング電子メールの実行を許可|マーケティング電子メールの実行を許可するかどうかを示します。|  
| Outlook 同期|アドレス帳の同期を許可|Microsoft Office Outlookでバックグラウンドでのアドレス帳同期を許可するかどうかを示します。|  
|スケジュールされたオフライン同期を許可|Outlook でバックグラウンドでのオフライン同期を許可するかどうかを示します。|  
|スケジュールされた同期を許可|Outlook とのスケジュールされた同期を許可するかどうかを示します。|  
|電子メール送信のポーリング間隔|Outlook で電子メールの送信に使用する通常のポーリング間隔です。|  
|最小のアドレス同期頻度|Outlook でアドレス帳同期に使用する通常のポーリング間隔です。|  
|最小のオフライン同期頻度|Outlook でバックグランドでのオフライン同期に使用する通常のポーリング間隔です。|  
|最小の同期頻度|スケジュールされた Outlook 同期の最小許容間隔です。|  
|自動タグ付けの最大サイクル数|新しい電子メールの受信時に電子メールの自動タグ付けに対して実行されるアグレッシブ ポーリング サイクルの最大数です。|  
|自動タグ付けの間隔|Outlook で電子メールの自動タグ付けに使用される通常のポーリング間隔です。|  
|ISV 構成|サービス カレンダーの外観の構成|サービス カレンダーの表示上のスタイルを定義できます。

詳細情報: [サービス カレンダーの外観の構成](https://docs.microsoft.com/dynamics365/customer-engagement/developer/customize-dev/service-calendar-appearance-configuration)|

  
## <a name="next-steps"></a>次のステップ

[ソリューションと修正プログラムの配布](use-segmented-solutions-patches-simplify-updates.md)
