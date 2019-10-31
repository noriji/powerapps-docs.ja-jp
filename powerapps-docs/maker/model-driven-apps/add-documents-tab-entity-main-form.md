---
title: エンティティのメイン フォームにドキュメント タブを追加する | MicrosoftDocs
description: エンティティのメインフォームにドキュメント タブを追加する方法を説明します
s.custom: null
ms.date: 09/05/2019
ms.reviewer: null
ms.service: crm-online
ms.suite: null
ms.tgt_pltfrm: null
ms.topic: article
author: Mattp123
ms.assetid: null
caps.latest.revision: null
ms.author: matp
manager: kvivek
search.audienceType:
  - customizer
search.app:
  - D365CE
---
# <a name="add-the-sharepoint-documents-tab-to-the-main-form-for-an-entity"></a>エンティティのメイン フォームに SharePoint ドキュメント タブを追加する
[!INCLUDE [cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

エンティティのメイン フォームにタブを追加して SharePoint ドキュメントを表示すると、ユーザーはモデル駆動型アプリで利用できる SharePoint 統合機能を見つけて使用できます。 

![ドキュメント ファイル タブ](media/document-files-tab.png)

> [!IMPORTANT]
> この機能を使用するには、ドキュメント管理を有効にする必要があります。 詳細: [SharePoint を使用してドキュメントを管理する](/dynamics365/customer-engagement/admin/manage-documents-using-sharepoint)

## <a name="add-the-documents-tab-in-the-formxml"></a>FormXML にドキュメント タブを追加する 
1.  新しいソリューションの作成 PowerApps にサインインして **ソリューション** に移動し、**新しいソリューション** に移動して必須の情報とオプション情報を入力します。 詳細: [ソリューションの作成](../common-data-service/create-solution.md)
2. メイン フォームのドキュメント タブを追加するソリューションに、エンティティを追加します。 すべての標準エンティティとカスタム エンティティをサポートしています。 詳細: [既存のコンポーネントをソリューションに追加する](/powerapps/maker/common-data-service/use-solution-explorer#add-an-existing-component-to-a-solution)
3. 取引先企業エンティティのメイン フォームなど、エンティティのフォームをソリューションに含めます。 エンティティの隣の **...** を選択して **編集** を選択します。 **フォーム** タブを選択します。必要なフォームが見つからない場合は、追加します。   

4. メイン フォームに 1 列のタブを追加します。 これを行うにはフォーム デザイナーでフォーム キャンバス上の領域を選択し、**コンポーネントを追加** を選択してから **1 列のタブ** を選択します。  
   ![1 列のタブを挿入](media/insert-one-column-tab.png)

5. フォーム デザイナーで、フォーム デザイナー キャンバスの **新しいタブ** を選択し、**フィールドを追加** を選択して、左側のウィンドウから *住所 1: 市区町村* などのフィールドを追加します。 タブには任意のテキストや数値のフィールドを使用できます。![タブにフィールドを追加します](media/add-field-to-tab.png)
6. タブ ラベルの名前を変更します。 これを行うには **新しいタブ** を選択し、右側のプロパティ ウィンドウで **新しいタブ** を *ファイル* のようにわかりやすいものに置き換えます。
7. **保存** を選択し、**公開** を選択してフォーム デザイナーを閉じます。 
8. PowerApps 作成者のホームページから **ソリューション** を選択し、ソリューションを選択して **エクスポート** を選択し、ソリューションをアンマネージド ソリューションとしてエクスポートします。 詳細: [ソリューションのエクスポート](../common-data-service/import-update-export-solutions.md#export-solutions) 
9. ソリューションを抽出し、XML やテキスト エディターで customization.xml ファイルを開きます。 
10. customization.xml で **label description="Files"** (または前のステップでタブ ラベルに付けた名前) を検索します。
11. **control id="address1_city"** などのコントロール id="*フィールド名*" 要素までスクロールし、このトピックの要素全体を [XML サンプル](#xml-sample-for-adding-the-documents-tab-to-a-form) に置き換えます。 

    > [!div class="mx-imgBorder"] 
    > ![](media/form-xml.png "XML サンプル挿入ポイント")

12. XML サンプルにこれらの変更を加えます。 
    
     a. **RelationshipName** 要素を見つけて *entityLogicalName*_SharePointDocument として表示されるスキーマ名に置き換えます。 たとえば、取引先企業エンティティの場合、関係のスキーマ名は Account_SharePointDocument で、これはこのトピックの XML サンプルのスキーマ名です。 別のエンティティの名前を見つけるには **設定** > **カスタマイズ** > **システムのカスタマイズ** > **エンティティ** > エンティティを選択 > **1:N Relationships** を選択、に順に移動します。 **SharePointDocument** の種類の **関連エンティティ** を見つけます。 

      ![取引先企業の関連付けの SharePoint ドキュメント](media/account-sharepointdocument.png)

     b. グローバル一意識別子 (GUID) を作成し、前の手順で貼り付けた **コントロール** 要素にある既存の **uniqueid** GUID を中括弧 {} を保持しながら置き換えます。  
       ![コントロール要素の一意 ID](media/control-unique-id.png) c。 customizations.xml への変更を保存します。 
13. solution.xml ファイルを開いて **バージョン** 要素の値を増やします。 たとえば、*1.1.0.0* から *1.2.0.0* に変更します。 
14. すべてのソリューション ファイルを圧縮 (zip 形式) フォルダにパッケージ化して、環境にインポートします。 以前のソリューションを削除する必要があるというエラーが表示された場合は、指示に従います。 詳細: [ソリューションのインポート、更新、アップグレード](../common-data-service/import-update-export-solutions.md) 

## <a name="xml-sample-for-adding-the-documents-tab-to-a-form"></a>フォームにドキュメント タブを追加する XML サンプル
```xml
  <control id="DocumentSubGrid" classid="{E7A81278-8635-4d9e-8D4D-59480B391C5B}" indicationOfSubgrid="true" uniqueid="{9cd66b5c-8b7a-6433-c5a5-46a7245dd534}"> 
    <parameters> 
      <ViewId>{0016F9F3-41CC-4276-9D11-04308D15858D}</ViewId> 
      <IsUserView>false</IsUserView>         
      <RelationshipName>Account_SharepointDocument</RelationshipName>
      <TargetEntityType>sharepointdocument</TargetEntityType> 
      <AutoExpand>Fixed</AutoExpand> 
      <EnableQuickFind>false</EnableQuickFind> 
      <EnableViewPicker>true</EnableViewPicker> 
      <ViewIds /> 
      <EnableJumpBar>false</EnableJumpBar> 
      <ChartGridMode>Grid</ChartGridMode> 
      <VisualizationId /> 
      <IsUserChart>false</IsUserChart> 
      <EnableChartPicker>false</EnableChartPicker> 
      <RecordsPerPage>10</RecordsPerPage> 
      <HeaderColorCode>#F3F3F3</HeaderColorCode> 
    </parameters> 
  </control> 
```

### <a name="see-also"></a>関連項目
[SharePoint を使用してドキュメントを管理する](/dynamics365/customer-engagement/admin/manage-documents-using-sharepoint)