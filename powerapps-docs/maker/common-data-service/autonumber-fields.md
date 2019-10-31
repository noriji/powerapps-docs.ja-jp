---
title: Common Data Service のオートナンバー フィールド | MicrosoftDocs
description: 自動付番フィールドを作成、管理、そして使用する方法を説明します
keywords: ''
ms.date: 02/26/2019
ms.service: powerapps
ms.custom: null
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
author: daemelia
ms.assetid: null
ms.author: daemelia
manager: kvivek
ms.reviewer: Mattp123
ms.suite: null
ms.tgt_pltfrm: null
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="autonumber-fields"></a>自動付番フィールド

自動付番フィールドは、作成されるたびに自動的に英数字文字列を生成するフィールドです。 作成者はこれらのフィールドのフォーマットを好みに合わせてカスタマイズし、そして実行時に自動的に入力される一致する値の生成をシステムに頼ることができます。

自動付番フィールドは正式にはその上に追加機能を構築したテキスト フィールドですが、[PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) は **自動付番** を **テキスト** カテゴリの下に個別のデータ型として単純に公開することでこの概念を単純化しています。 [クラシック ソリューション エクスプローラー](use-solution-explorer.md#classic-solution-explorer) が自動付番フィールドの作成または管理をサポートしていないことに注意する必要があります。

自動付番フィールドを作成するには、[フィールドの作成](create-edit-field-portal.md#create-a-field) まで同じ手順に従って、**データの種類** ドロップダウン リスト ボックスから単純に **自動付番** を選択します。 

フィールドを開いて **データの種類** ドロップダウン リスト ボックスから **自動付番** を選択して、既存のテキストフィールドの自動付番機能を有効にすることもできます。 同様に、このフィールドを開いて **データの種類** ドロップダウン リスト ボックスで異なるオプションを選択することで、いつでも自動付番機能を無効にもできます。

> [!NOTE]
>自動付番の値は、レコードの開始時にデータベースによって事前に選択されます。 レコードを開始してからキャンセルした場合、割り当てられた番号は使用されません。 この間に次の連続番号を持つ別のレコードが完了した場合は、レコードの自動付番にギャップが生じます。

## <a name="autonumber-types"></a>自動付番の種類

自動付番フィールドの作成を簡単にするために、最も一般的なシナリオで役立つ定義済みの既定の自動付番の種類がいくつかあります。 

### <a name="string-prefixed-number"></a>接頭辞に番号がついた文字列

最も一般的な自動付番の形式は、接頭辞に番号がついた単純な文字列です。 この種類が選択された場合、自動付番はオプションで固定の接頭辞文字列とともに、自動で増加する番号で構成されます。 たとえば、*Contoso-1000*、*Contoso-1001*、*Contoso-1002* など、接頭辞番号の文字列に *Contoso* という接頭辞がついたレコードを生成します。

### <a name="date-prefixed-number"></a>接頭辞に日付がついた番号

一般的なもうひとつの自動付番の形式は、接頭辞に日付がついた番号です。 この種類が選択された場合、自動付番は書式設定された日付の接頭辞とともに、自動で増加する番号で構成されます。 レコードの日付部分は、レコードが作成された現在の日時を UTC 時間で反映します。 選択可能なさまざまな日付の形式がいくつも提供されます。
たとえば、現在の日付と選択した形式によって *2019-26-02-1000*、*2019-27-02-1000*、*2019-28-02-1000* など、日付の接頭辞番号がレコードを生成します。

### <a name="custom"></a>ユーザー定義

特定のユースケースのより高度な作成者には、自動付番フィールドを希望の形式に完全にカスタマイズするオプションを提供します。 その形式は、文字列定数、自動的に増加する番号、書式設定された日付、またはランダムな英数字の連続で構成されます。
カスタム フォーマットを定義する方法の詳細は、[自動付番書式のオプション](https://docs.microsoft.com/dynamics365/customer-engagement/developer/create-auto-number-attributes#autonumberformat-options) を参照してください。

## <a name="seed-values"></a>シード値

自動付番フィールドのシード値は、形式の番号部分に使用される開始番号です。 たとえば、自動付番フィールドに *Contoso-1000*、*Contoso-1001*、*Contoso-1002* などのレコードを生成する場合、番号シーケンスの開始値であるため目的のシード値は 1000 です。 自動付番フィールドの既定のシード値は 1000 ですが、必要ならカスタム シード値を設定することもできます。 


> [!IMPORTANT]
> シードを設定すると、現在の環境で指定された属性の現在の数値のみが変更されます。 異なる環境にインポートされるとき、シード値はソリューションに含まれません。 

## <a name="create-an-autonumber-field"></a>自動付番フィールドの作成
  
1.  [PowerApps ポータル](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) にサインインします。
  
2.  左のウィンドウで **データ** を展開して **エンティティ** を選択します。
  
3.  自動付番フィールドを追加するエンティティを選択して、そして **フィールド** タブを選択します。
  
4.  ツールバーで、フィールドを **追加** を選択します。  
  
5.  右のウィンドウで **表示名** を入力して **データの種類** に **自動付番** を選択します。

    > [!div class="mx-imgBorder"] 
    > ![](media/create-autonumber-field.png "自動付番フィールドの作成")
  
6. 必要に応じてオプション フィールドを設定します。 詳細: [フィールドの作成と編集](create-edit-field-portal.md#create-a-field)

7. 自動付番の種類を選択するか、既定の **接頭辞に番号がついた文字列** オプションを保持します。

8. シード値をカスタマイズするか、または **1000** の既定値を保持します。

9. **完了**を選択します。

## <a name="see-also"></a>関連項目
 [PowerApps ポータルを使用して Common Data Service のフィールドの作成、編集を行います](create-edit-field-portal.md)
