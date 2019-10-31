---
title: Power BI レポートをモデル駆動型システム フォームに埋め込む | MicrosoftDocs
ms.custom: ''
ms.date: 03/05/2019
ms.reviewer: matp
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - PowerApps
ms.assetid: 99c795e0-9165-4112-85b1-6b5e1a4aa5ec
caps.latest.revision: 1
author: prsi-msft
ms.author: prsi
manager: kvivek
tags:
  - Links to topic not migrated
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="embed-a-power-bi-report-in-a-model-driven-system-form"></a>Power BI レポートをモデル駆動型システム フォームに埋め込む
PowerApps モデル駆動型アプリで Power BI レポートを使用して、システム フォームに豊富なレポート作成と分析を導入して、ユーザーがより多くを達成するよう強化します。 これでシステム間でデータを集約できるようになり、単一レコードのコンテキストに合わせて調整します。
 
## <a name="prerequisites"></a>前提条件
Power BI コンテンツの埋め込みはオプション機能で、すべての環境において既定で無効になっています。 Power BI コンテンツを埋め込む前に、それを有効にする必要があります。 詳細: [組織で Power BI ビジュアル化を有効にする](https://docs.microsoft.com/dynamics365/customer-engagement/admin/use-power-bi?#enable--visualizations-in-the-organization)。

この機能は、ソリューションをエクスポートし、それを修正して XML スニペットを追加し、そして元の環境にインポートする必要があります。 管理ソリューションのみを介して、ターゲット環境に変更を必ずインポートしてください。 既存の管理ソリューションに更新プログラムをインストールするガイダンスは [ソリューションのインポート、更新およびエクスポート](https://docs.microsoft.com/powerapps/maker/common-data-service/import-update-export-solutions) を参照してください。

## <a name="embed-without-contextual-filtering"></a>コンテキストのフィルター処理なしで埋め込む
埋め込むだけで Power BI レポートとタイルを使用でき、まったく同じレポートを取得できます。 これには、現在のモデル駆動型フォームにそれらをコンテキスト化することを含まれず、そのためエンティティのすべてのレコードで同じレポートまたはタイルを取得します。 たとえば、次のレポートは一度にすべての取引先企業の地理的位置を示しており、要約情報を表示するのに役立ちます。

> [!div class="mx-imgBorder"] 
> ![](media/embed-powerbi/embed-powerbi-report-in-system-form-unfiltered.png "Embed-powerbi-report-in-system-form-unfiltered")

フォーム XML の `<sections>` ブロック内に次のコード スニペットを追加することで、 Power BI レポートとタイルをホストするセクションをシステム フォームに埋め込むことが可能です。 その後、対象の環境でソリューションをインポートします。 

```xml
<section id="{d411658c-7450-e1e3-bc80-07021a04bcc2}" locklevel="0" showlabel="true" IsUserDefined="0" name="tab_4_section_1" labelwidth="115" columns="1" layout="varwidth" showbar="false">
    <labels>
        <label languagecode="1033" description="Unfiltered Power BI embedding demo"/>
    </labels>
    <rows>
        <row>
            <cell id="{7d18b61c-c588-136c-aee7-03e5e74a09a1}" showlabel="true" rowspan="20" colspan="1" auto="false">
                <labels>
                    <label languagecode="1033" description="Accounts (Parent Account)"/>
                </labels>
                <control id="unfilteredreport" classid="{8C54228C-1B25-4909-A12A-F2B968BB0D62}">
                    <parameters>
                        <PowerBIGroupId>00000000-0000-0000-0000-000000000000</PowerBIGroupId>
                        <PowerBIReportId>544c4162-6773-4944-900c-abfd075f6081</PowerBIReportId>
                        <TileUrl>https://xyz.powerbi.com/reportEmbed?reportId=544c4162-6773-4944-900c-abfd075f6081</TileUrl>
                    </parameters>
                </control>
            </cell>
        </row>
        <row/>
    </rows>
</section>
```
> [!IMPORTANT]
> XML のサンプルに示すように、コントロール `classid="{8C54228C-1B25-4909-A12A-F2B968BB0D62}"` を必ず使用してください。

 次の表では、前の例のプロパティについて説明します。

|                                                 プロパティ                                                  |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      説明                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|-----------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                         **PowerBIGroupId**                          |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  Power BI ワークスペースの ID。ユーザーの既定のワークスペースは常に 00000000-0000-0000-0000-000000000000 です。 URL を見ることで、任意のワークスペースの ID を確認できます。 たとえば、https://xyz.powerbi.com/groups/0ddbe381-256d-44bc-93de-34e47f3d9ab4/ などとします。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|                               **PowerBIReportId**                                |                             Power BI レポートの ID。これを埋め込む必要があるレポートと置き換えます。 URL をみることで、任意のレポートの ID を確認できます。 たとえば、https://xyz.powerbi.com/groups/me/reports/544c4162-6773-4944-900c-abfd075f6081 などとします。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|                                       **TileUrl**                                       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        埋め込む必要がある Power BI レポートまたはのタイルの URL。 正しい Power BI インスタンス名 (msit.powerbi.com を独自に置き換えてください) とレポート ID (reportId = 544c4162-6773-4944-900c-abfd075f6081 を独自に置き換えてください) を必ず使用してください。 たとえば、https://xyz.powerbi.com/reportEmbed?reportId=544c4162-6773-4944-900c-abfd075f6081 などとします。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |

## <a name="embed-with-contextual-filtering"></a>コンテキストのフィルター処理で埋め込む
現在のレコードの属性に基づいてレポートやタイルをフィルター処理するために、現在のモデル駆動型フォームにコンテキスト フィルターを適用すると、 Power BI のレポートとタイルをより意味あるものにできます。 例えば、次のレポートはアカウント名を使用して Power BI レポートをフィルター処理し、アカウントの地理的位置を表示します。 これにより、単一のレポートでエンティティのすべてのレコードに対するコンテキスト化された情報を表示できます。

> [!div class="mx-imgBorder"] 
> ![](media/embed-powerbi/embed-powerbi-report-in-system-form-filtered.png "Embed-powerbi-report-in-system-form-filtered")

ここで示すように、フィルター処理は `<parameter>` ブロックに `<PowerBIFilter>` 要素を加えることで実行されます。 フォームのエンティティの任意の属性を使用してフィルター式を作成できます。 詳細: [フィルターの作成](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Filters#contructingfilters) で独自のフィルターを作成する方法を説明します。
    
```xml
<control id="filteredreport" classid="{8C54228C-1B25-4909-A12A-F2B968BB0D62}">
    <parameters>
        <PowerBIGroupId>00000000-0000-0000-0000-000000000000</PowerBIGroupId>
        <PowerBIReportId>544c4162-6773-4944-900c-abfd075f6081</PowerBIReportId>
        <TileUrl>https://xyz.powerbi.com/reportEmbed?reportId=544c4162-6773-4944-900c-abfd075f6081</TileUrl>
        <PowerBIFilter>{"Filter": "[{\"$schema\":\"basic\",\"target\":{\"table\":\"My Active Accounts\",\"column\":\"Account Name\"},\"operator\":\"In\",\"values\":[$a],\"filterType\":1}]", "Alias": {"$a": "name"}}</PowerBIFilter>
    </parameters>
</control>
```

これはフィルター処理されていないレポートの埋め込みと同じコントロールを使用することに注意し、それゆえコントロール クラス ID は変更されないままです。 

次の表では、前の例の任意の追加プロパティについて説明します。

|                                                 プロパティ                                                  |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      説明                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|-----------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                         **PowerBIFilter**                          |        フォーム属性をパラメーターとして渡すことによって Power BI レポートをコンテキスト化するフィルター式。 より読みやすくするために、フィルターはここで示すように作成されています。    |

    {
            "Filter": "[{
                    \"$schema\":\"basic\",
                    \"target\":{
                            \"table\":\"My Active Accounts\",
                            \"column\":\"Account Name\"
                    },
                    \"operator\":\"In\",
                    \"values\":[$a, $b],
                    \"filterType\":1
            }]",
            "Alias": {
                    "$a": "firstname",
                    "$b":"lastname"
            }
    }

前の式の対象部分はフィルタを適用するテーブルと列を識別します。 オペレーターはロジックを識別し、値は PowerApps モデル駆動型アプリから渡されたデータを識別します。 汎用な方法でパラメータ化するために、値はエイリアスによって作成されます。 前の式では、取引先企業の **名** と **姓** が渡され、どちらも Power BI レポートの **取引先企業名** 列で検索されます。 **名** と **姓** はここで渡される取引先企業エンティティの属性の一意の名前であることに注意してください。 

[フィルターの作成](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Filters#contructingfilters) の例を見て $schema と filterType に適切な値を指定することにより、もっと複雑なフィルター式を作成できます。 JSON が正しく生成されるように、フィルター部分で *\"* を使用して各リテラルを確実にエスケープしてください。

## <a name="known-issues-and-limitations"></a>既知の問題と制限
1. この統合はサポートされている Web ブラウザおよびモバイル デバイス上の、統一インターフェイスのクライアントでのみ利用可能です。
2.  PowerApps フォーム デザイナーでこのフォームを開いても、コントロールが意味のある方法では表示されません。 これはコントロールがフォーム デザイナーの外部でカスタマイズされているためです。
3. ユーザーは PowerApps のユーザー名とパスワードで自動的に Power BI に認証されます。 資格情報が一致する Power BI アカウントが存在しない場合は、ここに示すようなサインイン プロンプトが表示されます。 

   > [!div class="mx-imgBorder"] 
   > ![](media/embed-powerbi/embed-powerbi-report-in-system-form-auth-1.png "Embed-powerbi-report-in-system-form-auth-1")

4. 誤ったアカウントを使用して Power BI にログインした場合はデータが表示されません。 正しい資格情報でサインインするには、サインアウトして、もう一度サインインしてください。

   > [!div class="mx-imgBorder"] 
   > ![](media/embed-powerbi/embed-powerbi-report-in-system-form-auth-2.png "Embed-powerbi-report-in-system-form-auth-2")

   > [!div class="mx-imgBorder"] 
   > ![](media/embed-powerbi/embed-powerbi-report-in-system-form-auth-3.png "Embed-powerbi-report-in-system-form-auth-3")

5. PowerApps 内部で示されるレポート データのビューは Power BI のものと同じであり、PowerAppsのセキュリティ ロールと権限は表示されるデータに影響しません。 したがって、データは Power BI データセットの作成者が見るものと基本的に同じです。 PowerApps のセキュリティ ロールとチームと同様のデータ アクセス制限を適用するには、[Power BI を使った行レベルセキュリティ (RLS)](https://docs.microsoft.com/power-bi/service-admin-rls) を使用します。
6. ソリューションをインポートしてカスタマイズを公開した後でフォームに Power BI レポートが表示されない場合、モデル駆動型フォーム エディターで開いて保存するとフォーム JSON が再生成されます。


### <a name="see-also"></a>関連項目

[PowerApps モデル駆動型個人用ダッシュボードに Power BI ダッシュボードを埋め込む](https://docs.microsoft.com/dynamics365/customer-engagement/basics/add-edit-power-bi-visualizations-dashboard)

[Dynamics 365 アプリで Power BI を使用する](https://docs.microsoft.com/dynamics365/customer-engagement/admin/use-power-bi)

[ソリューションのインポート、更新およびエクスポート](../common-data-service/import-update-export-solutions.md)
