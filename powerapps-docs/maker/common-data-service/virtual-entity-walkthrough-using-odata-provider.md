---
title: Common Data Service で OData データ プロバイダーを使用した仮想エンティティ チュートリアル | MicrosoftDocs
description: 仮想エンティティで OData v4 データ プロバイダーを使用する方法について学習
ms.custom: ''
ms.date: 06/04/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
ms.assetid: null
caps.latest.revision: 11
author: Mattp123
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="virtual-entity-walkthrough-using-the-odata-v4-data-provider"></a>OData v4 データ プロバイダーを使用してエンティティ チュートリアルを仮想

モデル駆動型アプリ内で、外部データ ソースからのチケット情報にアクセスするとします。 この単純なチュートリアルでは、実行時にチケット データを OData Web サービスから取得する、外部スキーマにマップされたフィールドを持つ仮想エンティティをモデル化します。

## <a name="data-source-details"></a>データ ソースの詳細

このチュートリアルで使用されるデータ ソースには OData v4 Web サービスがあるため、ユーザーの環境に含まれる OData v4 データ プロバイダーを使用することができます。

Web サービス URL: `http://contosowebservice.azurewebsites.net/odata/` 

> [!IMPORTANT]
> このチュートリアルで使用する Web サービス URL は、機能しているWeb サービスではありません。

このチュートリアルでは、以下の 3 つのフィールドを含む単一の仮想エンティティが必要です。

|外部のフィールド名 |外部データの種類 |仮想エンティティ データの種類 |目的 |
|---------|---------|---------|---------|
|チケット ID |`Edm.Guid` |主キー |エンティティの主キー |
|タイトル  |`Edm.String` |1 行テキスト |チケットのタイトル |
|重要度 |`Edm.Int32`| 整数 |チケットの重要度を示す 0-4 の数値 |

外部データ ソース チケット エンティティの OData メタデータ:

```xml
<EntityType Name="Ticket">
  <Key>
    <PropertyRef Name="TicketID" />
  </Key>
  <Property Name="TicketID" Nullable="false" Type="Edm.Guid" />
  <Property Name="Title" Type="Edm.String" />
  <Property Name="Severity" Nullable="false" Type="Edm.Int32" />
</EntityType>
```

## <a name="create-the-data-source"></a>データ ソースを作成

OASIS オープン データ プロトコル (OData) のサンプル Web サービスを使用する OData v4 データ プロバイダーに、データソースを作成します。

1. **設定** > **管理** > **仮想エンティティのデータ ソース**の順に移動します。
1. **新規**を選び、**OData v4 データ プロバイダー**を選択し、**OK** を選択します。
1. 以下の情報を入力または選択します。

    |フィールド|Value|
    |--|--|
    |**名前**|Contoso サンプル データ ソース|
    |**URL**|`http://contosowebservice.azurewebsites.net/odata` |
    |**タイムアウト**|30|
    |**インライン カウントの取得**|はい|

他のフィールドを現状のまま残し、**保存 & 閉じる**を選択します。

> [!TIP]
> 独自の Web サービスを使用する場合は、URL が Webブラウザーに貼り付けることで有効であることを確認します。 

## <a name="open-solution-explorer"></a>ソリューション エクスプローラーを開きます

作成するユーザー定義エンティティの名前の一部はカスタマイズの接頭辞です。 これは、作業中のソリューションの発行者に基づいて設定されます。 カスタマイズの接頭辞に注意を払う場合は、カスタマイズの接頭辞がこのエンティティに対して必要な接頭辞であるアンマネージド ソリューションで作業するようにします。 詳細: [ソリューション発行者の接頭辞を変更する](change-solution-publisher-prefix.md) 

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]


## <a name="create-the-virtual-entity"></a>仮想エンティティを作成

1. ソリューション エクスプローラーの左側のナビゲーション ウィンドウで、**エンティティ**を選び、メイン ウィンドウから**新規**選択します。
2. **エンティティ: 新規**フォームで、**仮想エンティティ**オプションを選び、以下の情報を入力します。 

    |フィールド|Value|
    |--|--|
    |**データ ソース**|Contoso サンプル データ ソース|
    |**表示名**|チケット|
    |**複数名**|チケット|
    |**名前**|new_ticket|
    |**外部名**|チケット|
    |**外部コレクション名**|チケット|
    |**メモ (添付ファイルを含む)**|選択済み|
    |**活動**|選択済み|

1. **このエンティティが表示される領域**の横で、**サービス**を選択してから、**保存**を選択します (エンティティ フォームを閉じないでください)。
    ![チケット エンティティの定義](media/ticket-entity.png)

## <a name="create-the-fields-for-the-virtual-entity"></a>仮想エンティティのフィールドを作成

**エンティティ: チケット**ページの左のナビゲーション ウィンドウで、**フィールド**を選択します。 このチュートリアルの一部として、2 つの既存のフィールドを編集し、3 番目のフィールドを追加します。

> [!IMPORTANT]
> 外部名は大文字と小文字が区別されます。 正しい名前を使用しているか Web サービス メタデータを参照してください。
> false の Nullable 値は、属性が必要なことを示します。 主キー フィールドは常にシステムが必要であることに注意してください。

1. **new_ticketid** フィールドを開き、次に表示される値の属性を変更します。**外部名**: TicketID  ![TicketID フィールド](media/ticketid-field.png)
1. **保存して閉じる**を選択します。
1. **新しい名前**フィールドを開き、次に表示される値をもつ属性を変更します。
    - **表示名**: タイトル
    - **外部名**: タイトル ![Title フィールド](media/title-field.png)
1. **保存して閉じる**を選択します。
1. **新規**を選び、**フィールド: チケットの新規**ページで以下の情報を入力します。

    |フィールド|Value|
    |--|--|
    |**表示名**|重要度|
    |**名前**|new_severity|
    |**外部名**|重要度|
    |**フィールド要件**|必須項目|
    |**データの種類**|整数|
    |**最小値**|0|
    |**最大値**|4|

  ![重要度フィールド](media/severity-field.png)
1. **保存して閉じる**を選択します。

## <a name="add-the-fields-to-the-main-form"></a>主フォームにフィールドを追加

1. チケット エンティティ ウィンドウで、**フォーム**を選択します。
1. メイン フォームを開き、**タイトル**フィールド下**概要**セクションの フォーム上の右側のウィンドウから**重要度**フィールドをドラッグおよびドロップします。 
    ![メイン フォームに追加される重要度フィールド](media/drop-severity-field.png)
1. チケット エンティティ ウィンドウで、**保存および閉じる**を選択します。

## <a name="configure-the-default-view"></a>既定のビューを構成

1. ソリューション エクスプローラーの左側のウィンドウの、**チケット エンティティ**の下で、**ビュー**を選択します。
1. **すべてのチケット**ビューを開きます。
1. **タスク**ウィンドウで、**検索列の追加**を選択します。
    ![ビュー列の追加](media/addcolumns.png)
1. **重要度**を選び、**OK** を選択します。
1. **ビュー: すべてのチケット**ウィンドウで、**保存して閉じる**を選択します。
1. ソリューション エクスプローラー ウィンドウで、**すべてのカスタマイズの公開**を選択します。
    ![すべてのカスタマイズの公開](media/publishall.png)
1. すべてのカスタマイズの公開後、ソルーション エクスプローラー ウィンドウを閉じます。

## <a name="view-the-virtual-entity-in-action-with-dynamics-365"></a>Dynamics 365 のアクションで仮想エンティティを表示

1. **サービス** > **拡張** > **チケット**へ移動します。
    
    ![チケット領域](media/ticket-area.png)

    **すべてのチケット**ビューが表示されます。 **サービス**領域からでエンティティを参照するには、ブラウザーを更新する必要がある場合があることに注意してください。

    ![すべての通知を表示](media/all-tickets-view.png)
1. 特定のレコードの**タイトル**および**重要度**フィールドを含むフォームを表示するために**チケット**レコードを開きます。
    ![チケット レコード](media/ticket-record.png)

### <a name="see-also"></a>関連項目

[OData v4 データ プロバイダーの構成、要件、ベスト プラクティス](virtual-entity-odata-provider-requirements.md)<br />
[外部データ ソースからのデータを格納する仮想エンティティの作成および編集](create-edit-virtual-entities.md)
