---
title: 自動付番の属性を作成する (Common Data Service) | Microsoft Docs
description: 新しいAutoNumberFormatプロパティを使用することを除いては、StringAttributeMetadataクラスを使用して文字列属性を作成する方法と同じ方法で、自動付番の属性の作成する方法について説明します。 プレースホルダーを構成することにより、シーケンス番号およびランダム文字列を含むパターンを定義するために、AutoNumberFormatプロパティを使用します。これにより生成される値の長さと種類を表示します。
keywords: 自動付番の属性
ms.custom: ''
ms.date: 07/24/2019
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: nhelgren
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="create-auto-number-attributes"></a>自動付番の属性を作成

Common Data Service では、エンティティに対して自動付番の特性を付与することができます。 現在は、プログラムで属性を追加することができます。 この種類の属性を追加するユーザー インターフェイスはありません。 このトピックでは、プログラムで自動付番の属性を作成してシーケンシャル要素のシード値を設定する方法を説明します。 また、後からシードをリセットする必要がある場合はいつでも、次のレコードにシーケンス番号を設定する方法についてのトピックを表示します。
> [!NOTE]
>シードの設定は任意です。 リシードする必要がない場合、シードを呼び出す必要はありません。


新しい **AutoNumberFormat** プロパティを使用することを除いては、 **StringAttributeMetadata** クラスを使用して文字列属性を作成する方法と同じ方法で、自動付番の属性の作成することができます。 プレースホルダーを構成することにより、シーケンス番号およびランダム文字列を含むパターンを定義するために、 **AutoNumberFormat** プロパティを使用します。これにより生成される値の長さと種類を表示します。 特に、オフラインのクライアントが自動付番を作成しようとしている場合、ランダム文字列は重複または競合を回避するのに役立ちます。

自動付番の属性を作成する場合、 **StringAttributeMetadata.FormatName** プロパティまたは **StringAttributeMetadata.Format** プロパティ値はテキストである必要があります。 これらは既定値であるため、通常、このプロパティは設定されません。 電子メール、電話、TextArea、URLまたはその他の [既存のフォーム](https://msdn.microsoft.com/library/microsoft.xrm.sdk.metadata.stringformatname.aspx)などの、その他の特殊なタイプの任意のフォーマットフォームを使用して自動付番の属性を作成することはできません。

シーケンシャル セグメントは SQL で生成されるため、一意性は SQL で保証されます。

> [!NOTE]
>自動付番フォーマットとして、既存のフォームのテキスト属性を変更できます。

フォームにフィールドとして自動付番の属性を追加する場合、自動付番の属性フィールドがフォーム上で読み取り専用に動作し、エンドユーザーがフィールドを編集することはできません。 値は、エンティティを保存した後にのみ設定されます。 ビュー、グリッドなどの任意の他のフィールド値として自動付番の属性を扱うことできます。

### <a name="examples"></a>例
次の例には、新しい自動付番の属性の作成方法と、 **WID-00001-AB7LSFG-20170913070240**のような値がある **新しい\_ウィジェット** という名前のユーザー定義エンティティの、 **新しい\_シリアル番号** という名前の新しい自動付番の属性を作成する方法を示します。
SDKアセンブリ **CreateAttributeRequest** および **StringAttributeMetadata** クラスの組織サービスの使用:

```csharp
CreateAttributeRequest widgetSerialNumberAttributeRequest = new CreateAttributeRequest
            {
                EntityName = "newWidget",
                Attribute = new StringAttributeMetadata
                {
                    //Define the format of the attribute
                    AutoNumberFormat = "WID-{SEQNUM:5}-{RANDSTRING:6}-{DATETIMEUTC:yyyyMMddhhmmss}",
                    LogicalName = "new_serialnumber",
                    SchemaName = "new_SerialNumber",
                    RequiredLevel = new AttributeRequiredLevelManagedProperty(AttributeRequiredLevel.None),
                    MaxLength = 100, // The MaxLength defined for the string attribute must be greater than the length of the AutoNumberFormat value, that is, it should be able to fit in the generated value.
                    DisplayName = new Label("Serial Number", 1033),
                    Description = new Label("Serial Number of the widget.", 1033)
                }
            };
            _serviceProxy.Execute(widgetSerialNumberAttributeRequest);
```

## <a name="use-web-api"></a>Web APIを使用

Web API を使用してエンティティ定義を作成および更新できます。

詳細については、 [Web API を使用してエンティティ定義を作成および更新 > 属性を作成](https://msdn.microsoft.com/library/mt593078.aspx#Anchor_3) を参照してください。

#### <a name="request"></a>要求
```http
POST [Organization URI]/api/data/v9.0/EntityDefinitions(LogicalName='new_widget')/Attributes HTTP/1.1
Accept: application/json
Content-Type: application/json; charset=utf-8
OData-MaxVersion: 4.0
OData-Version: 4.0

{
 "AttributeType": "String",
 "AttributeTypeName": {
  "Value": "StringType"
 },
 "Description": {
  "@odata.type": "Microsoft.Dynamics.CRM.Label",
  "LocalizedLabels": [
   {
    "@odata.type": "Microsoft.Dynamics.CRM.LocalizedLabel",
    "Label": "Serial Number of the widget.",
    "LanguageCode": 1033
   }
  ]
 },
 "DisplayName": {
  "@odata.type": "Microsoft.Dynamics.CRM.Label",
  "LocalizedLabels": [
   {
    "@odata.type": "Microsoft.Dynamics.CRM.LocalizedLabel",
    "Label": "Serial Number",
    "LanguageCode": 1033
   }
  ]
 },
 "RequiredLevel": {
  "Value": "None",
  "CanBeChanged": true,
  "ManagedPropertyLogicalName": "canmodifyrequirementlevelsettings"
 },
 "SchemaName": "new_SerialNumber",
 "AutoNumberFormat": "WID-{SEQNUM:5}-{RANDSTRING:6}-{DATETIMEUTC:yyyyMMddhhmmss}",
 "@odata.type": "Microsoft.Dynamics.CRM.StringAttributeMetadata",
 "FormatName": {
  "Value": "Text"
 },
 "MaxLength": 100
}
```

#### <a name="response"></a>応答

```http
HTTP/1.1 204 No Content
OData-Version: 4.0
OData-EntityId: [Organization URI]/api/data/v9.0/EntityDefinitions(402fa40f-287c-e511-80d2-00155d2a68d2)/Attributes(f01bef16-287c-e511-80d2-00155d2a68d2)
```
> [!NOTE]
>自動付番の値は、レコードの開始時にデータベースによって事前に選択されます。 レコードを開始してからキャンセルした場合、割り当てられた番号は使用されません。 この間に次の連続番号を持つ別のレコードが完了した場合は、レコードの自動付番にギャップが生じます。

## <a name="autonumberformat-options"></a>AutoNumberFormatオプション

これらの例は、異なる結果を取得するための **AutoNumberFormat** プロパティの設定方法を示します:

|**AutoNumberFormat値**|**例値**|
|:----------|:----------|
|`CAR-{SEQNUM:3}-{RANDSTRING:6}`|`CAR-123-AB7LSF`|
|`CNR-{RANDSTRING:4}-{SEQNUM:4}`|`CNR-WXYZ-1000`|
|`{SEQNUM:6}-#-{RANDSTRING:3}`  |`123456-#-R3V`|
|`KA-{SEQNUM:4}`                |`KA-0001`|
|`{SEQNUM:10}`                  |`1234567890`|
|`QUO-{SEQNUM:3}#{RANDSTRING:3}#{RANDSTRING:5}`|      `QUO-123#ABC#PQ2ST`|
|`QUO-{SEQNUM:7}{RANDSTRING:5}` |`QUO-0001000P9G3R`|
|`CAS-{SEQNUM:6}-{RANDSTRING:6}-{DATETIMEUTC:yyyyMMddhhmmss}`|`CAS-002000-S1P0H0-20170913091544`|
|`CAS-{SEQNUM:6}-{DATETIMEUTC:yyyyMMddhh}-{RANDSTRING:6}`|`CAS-002002-2017091309-HTZOUR`|
|`CAS-{SEQNUM:6}-{DATETIMEUTC:yyyyMM}-{RANDSTRING:6}-{DATETIMEUTC:hhmmss}`|`CAS-002000-201709-Z8M2Z6-110901`|

ランダム文字列のプレースホルダーは任意です。一つ以上のランダム文字列のプレースホルダーを含めることができます。 [標準日および時刻フォーマットの文字列](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings)からプレースホルダーを決定するために任意のフォーム値を使用します 。

### <a name="string-length"></a>文字列の長さ

次の表は、ランダムおよびシーケンスプレースホルダーの文字列の長さの値を示します。

<table>
  <tr>
    <th>Placeholder</th>
    <th>文字列の長さ</th>
    <th>シナリオを出力</th>
  </tr>
  <tr>
    <td><code>{RANDSTRING:MIN_LENGTH}</code></td>
    <td><b>MIN_LENGTH</b> の値は1 ~ 6の間です。</td>
     <td>エンティティを保存する際に、値が1 ~ 6の間の場合、自動付番の属性は定義された長さの任意の文字列を生成します。 7または7を超える場合に <b>MIN_LENGTH</b> 値を使用すると、｢無効な引数｣エラーが発生します。</td>
  </tr>
  <tr>
    <td><code>{SEQNUM:MIN_LENGTH}</code></td>
    <td><b>MIN_LENGTH</b> の最小値は1です。 数は、最小長を超えて増加し続けます。</td>
    <td>エンティティを保存する際に、 <b>MIN_LENGTH</b>の数値がより大きい場合に、自動付番の属性は良好に動作し、かつ良好に動作し続けます。</td></table>

シーケンス値のプレースホルダーの場合、 **MIN_LENGTH** が最小長です。 2になるように値を設定する場合、初期値は01で、100番目のエンティティ値は100です。 数は、最小長を超えて増加し続けます。 シーケンス値の長さの設定する際は、初期値に追加の0を追加することにより、自動生成された値に対して一定の長さを確立します。 絶対値は制限されません。 ランダム値のプレースホルダーは常に同じ長さです。

シーケンス値が割り当てられた最小長より大きくなるため、 **StringAttributeMetadata.MaxLength** プロパティを調整してフォーマットされた値の長さに合わせる必要はありません。 値が **MaxLength** 値を超える場合、これを行う際に小さい値となり、将来エラーを生じさせる可能性があります。 シーケンス値の現実的な範囲に対して十分な余裕を残しているか確認します。

> [!NOTE]
> 属性を作成する際、プレースホルダー値の検証は行われません。 エラーは、誤って設定されている **AutoNumberFormat** 値を使用するエンティティ インスタンスを保存しようとするときにのみ表示されます。
> たとえば、ランダム文字列の長さを6以上指定した場合、最初に新しい自動付番属性を含むエンティティを保存する際に、新しいエンティティ インスタンスを作成する最初のユーザーは**引数が無効**エラーが表示されます。

## <a name="update-auto-number-attributes"></a>自動付番の属性を更新

正しくない構成で自動付番の属性を作成するか、または既存の自動付番の属性を変更したい場合、 **AutoNumberFormat** 属性値を更新できます。

次のコード スニペットは、自動付番の属性を取得、変更、および更新するにはどうしたらよいかを説明します。

既存の属性の自動付番を変更するには、 **RetrieveAttributeRequest** クラスを使用して、属性を取得する必要があります。

```csharp
// Create the retrieve request
RetrieveAttributeRequest attributeRequest = new RetrieveAttributeRequest
            {
                EntityLogicalName = entityName.ToLower(),
                LogicalName = "new_serialnumber",
                RetrieveAsIfPublished = true
            };
// Retrieve attribute response
RetrieveAttributeResponse attributeResponse = (RetrieveAttributeResponse)_serviceProxy.Execute(attributeRequest);
```

自動付番の属性を取得した後、属性を変更し、更新する必要があります。

```csharp            
//Modify the retrieved auto-number attribute
AttributeMetadata retrievedAttributeMetadata = attributeResponse.AttributeMetadata;
retrievedAttributeMetadata.AutoNumberFormat = "CAR-{RANDSTRING:5}{SEQNUM:6}"; //Modify the existing attribute by writing the format as per your requirement 

// Update the auto-number attribute            
UpdateAttributeRequest updateRequest = new UpdateAttributeRequest
                        {
                            Attribute = retrievedAttributeMetadata,
                            EntityName = "newWidget",
                        };
// Execute the request
_serviceProxy.Execute(updateRequest);
```

## <a name="set-a-seed-value"></a>シード値の設定

既定では、1000 ですべての自動付番のシーケンス値を開始し、長さに応じて、プレフィックスとして0を使用します。 このように、値の長さは常に同じです。 初期値を変更したい場合、以下のAPIを使用して最初のシード値を変更し、シーケンスセグメントに使用される次の数を設定する必要があります。

たとえば、シーケンス番号の長さが5の場合、既定値の00001ではなく10000の初期値から開始することができます。 自動付番の属性を作成した後に異なる開始値を選択したい場合、 **SetAutoNumberSeed** メッセージを使用します。 Web APIを使用する際に、SDKアセンブリと **SetAutoNumberSeed** アクションを使用する場合は、 **SetAutoNumberSeedRequest** クラスを使用します。

**AutoNumberSeed** メッセージには以下のパラメーターがあります:


|**名前**|**種類**|**説明**|
|:----------|:----------|:----------|
|EntityName|文字列|シードに設定したい属性を含むエンティティの論理名。|
|AttributeName|文字列|シードに設定したい属性の論理名。|
|Value|int|属性の次の自動付番の値。|

> [!NOTE]
> シードを設定すると、現在の環境で指定された属性の**現在の数値**のみが変更されます。 属性の一般的な**開始値**は示しません。 異なる環境にインストールされるとき、シード値はソリューションに含まれません。 開始番号をソリューションのインポート後に設定するには、ターゲット環境内の **SetAutoNumberSeed** メッセージを使用します。

### <a name="examples"></a>例
次のサンプルは、 **新しい\_ウィジェット**という名前のユーザー定義エンティティの、 **新しい\_シリアル番号** という名前の自動付番の属性に10000のシードを設定します。

SDKアセンブリ **SetAutoNumberSeedRequest** クラスで組織サービスを使用します:
```csharp
//Define the seed 
SetAutoNumberSeedRequest req = new SetAutoNumberSeedRequest();
req.EntityName = "newWidget";
req.AttributeName = "newSerialnumber";
req.Value = 10000;
_serviceProxy.Execute(req);
```
Web API **SetAutoNumberSeed** アクションを使用します。

詳細: [Web APIアクションを使用> アンバインドされたアクション](https://msdn.microsoft.com/library/mt607600.aspx#bkmk_unboundActions)

#### <a name="request"></a>要求

```http
POST [Organization URI]/api/data/v9.0/SetAutoNumberSeed HTTP/1.1
Accept: application/json
Content-Type: application/json; charset=utf-8
OData-MaxVersion: 4.0
OData-Version: 4.0

{
 "EntityName": "new_Widget",
 "AttributeName": "new_Serialnumber",
 "Value": 10000
} 
```

#### <a name="response"></a>応答

```json
HTTP/1.1 204 No Content
OData-Version: 4.0
```
## <a name="community-tools"></a>コミュニティ ツール

### <a name="auto-number-manager"></a>自動付番マネージャ

XrmToolBox の **[自動付番マネージャ](https://www.xrmtoolbox.com/plugins/Rappen.XrmToolBox.AutoNumManager/)** は Common Data Service のコミュニティ駆動型ツールで、新規または既存の特性に対して自動付番のフォーマットの設定、更新、削除を行うUIを提供します。
自動付番マネージャの詳細については、コミュニティ開発ツールの[開発者ツール](developer-tools.md)のトピックおよび [anm.xrmtoolbox.com](http://anm.xrmtoolbox.com) を参照してください。

> [!NOTE]
> コミュニティ ツールは Common Data Service の製品ではなく、コミュニティ ツールに対するサポートは提供しません。 このツールに関するご質問は、その発行元にお問い合わせください。 詳細: [XrmToolBox](https://www.xrmtoolbox.com)。 


### <a name="see-also"></a>関連項目
[Dynamics 365 のメタデータ モデルおよびデータ モデル](/dynamics365/customer-engagement/developer/metadata-data-models)  
[エンティティ メタデータのカスタマイズ](customize-entity-metadata.md) 
