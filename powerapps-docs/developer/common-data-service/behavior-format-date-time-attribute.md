---
title: 日時属性の動作と形式 (Common Data Service) | Microsoft Docs
description: DateTimeAttributeMetadata クラスを、Common Data Service のタイプ DateTime の属性を定義および管理するのに使用します。
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: mayadumesh
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="behavior-and-format-of-the-date-and-time-attribute"></a>日時属性の動作と形式

世界中にユーザーと事務所がある場合、複数のタイム ゾーンで日付と時刻の値を適切に表現することが重要です。 `DateTimeAttributeMetadata` (<xref href="Microsoft.Dynamics.CRM.DateTimeAttributeMetadata?text=DateTimeAttributeMetadata EntityType" /> または <xref:Microsoft.Xrm.Sdk.Metadata.DateTimeAttributeMetadata> クラス) は、Common Data Service で型 `DateTime` の属性を定義および管理するために使用されます。 `DateTimeBehavior` プロパティを使用して(組織サービスについては、 <xref:Microsoft.Xrm.Sdk.Metadata.DateTimeAttributeMetadata>.<xref:Microsoft.Xrm.Sdk.Metadata.DateTimeAttributeMetadata.DateTimeBehavior>を参照してください)、日付と時刻の値をタイムゾーン情報を付けて格納するか、付けないで格納するかを定義し、 `DateTimeAttributeMetadata.Format` プロパティを使用してこれらの属性の表示形式を指定します。  

  
 また、 Common Data Service のカスタマイズ領域を使用して、日時属性の動作と形式を定義します。 詳細: [日時フィールドの動作と形式](/dynamics365/customer-engagement/customize/behavior-format-date-time-field)。  
  
> [!NOTE]
>  Common Data Service では、すべての日付と時刻の属性は 1753 年 1 月 1 日午前 12:00 以降の日付をサポートします。  
  
<a name="SpecifyBehavior"></a>   

## <a name="specify-the-behavior-of-a-date-and-time-attribute"></a>日時属性の動作の指定

 `DateTimeBehavior` (<xref href="Microsoft.Dynamics.CRM.DateTimeBehavior?text=DateTimeBehavior ComplexType" /> または <xref:Microsoft.Xrm.Sdk.Metadata.DateTimeBehavior> クラス) を使用して、 <xref href="Microsoft.Dynamics.CRM.DateTimeAttributeMetadata?text=DateTimeAttributeMetadata EntityType" />.DateTimeBehavior プロパティの値を指定することができます。 `DateTimeBehavior` には次のメンバーが含まれます。各メンバーは、メンバー名と同じ値の文字列を返します:  
  
|メンバーの名前および値|内容|  
|---------------------------|-----------------|  
|`UserLocal`|-   日時値を UTC 値としてシステムに格納します。<br />-   取得操作によって UTC 値が返されます。<br />-   更新操作は UTC 値を現在のユーザーのタイム ゾーン値に変換し、更新に対して指定された値の種類 ([DateTimeKind](https://msdn.microsoft.com/library/shx7s921.aspx)) 基づいて、更新された値をそのまま、あるいは同等の UTC 値として格納します。 指定された値の種類が UTC の場合は、そのまま格納されます。 そうでない場合は、UTC 相当値が格納されます。<br />-   書式設定された値を取得すると、UTC から、ユーザーのタイム ゾーンとロケールの設定に基づいて、ユーザーの現在のタイム ゾーンを変換されます。<br />-   Web API の場合、属性は DateTimeOffset として公開されます。<br />-   この動作は、`CreatedOn` および `ModifiedOn` のようなシステム属性に対して使用され、変更することはできません。 日時値をタイム ゾーン情報を付けて格納するユーザー定義属性の動作に対して、これを使用します。|  
|`DateOnly`|-   実際値の日付の値を、時刻値 12:00 AM (00:00:00) で、システムに格納します。<br />-   取得と更新操作の場合は、タイム ゾーンの変換は行われず、時刻値はつねに 12 AM (00:00:00) となります。<br />-   書式設定された値を取得すると、タイム ゾーンの変換なしで、日付値が表示されます。<br />-   Web API の場合、属性は DateTimeOffset として公開されます。<br />-   この動作は、時刻情報が必要とされない生年月日や記念日を格納する、ユーザー定義属性に対して使用します。|  
|`TimeZoneIndependent`|-   ユーザーのタイムゾーンに関係なく、実際の日時値をシステムに格納します。<br />-   取得および更新操作の場合、タイム ゾーンの変換は行われません、実際の日付と時刻の値が返されて、ユーザーのタイム ゾーンに関係なく、システム内でそれぞれ更新されます。<br />-   書式設定された値を取得すると、現在のユーザーのタイム ゾーンとロケールの設定で指定された形式に基づいて、日付と時刻の値が (タイム ゾーンの変換なしで) 表示されます。<br />-   Web API の場合、属性は DateTimeOffset として公開されます。<br />-   この動作は、ホテルのチェックインおよびチェック アウトの時間などの情報を格納する属性に対して使用されます。|  
  
 次のサンプル コードは、新しい日時属性の `UserLocal` 動作の設定方法を示しています。  
  
 ```csharp
// Create a date time attribute for the Account entity
// with the UserLocal behavior
dtAttribute = new DateTimeAttributeMetadata
{                             
    SchemaName = "new_SampleDateTimeAttribute",
    DisplayName = new Label("Sample Date Time Attribute", _languageCode),
    RequiredLevel = new AttributeRequiredLevelManagedProperty(AttributeRequiredLevel.None),                
    Description = new Label("Created by SDK Sample", _languageCode),                
    DateTimeBehavior = DateTimeBehavior.UserLocal,
    Format = DateTimeFormat.DateAndTime,
    ImeMode = ImeMode.Disabled
};

CreateAttributeRequest createAttributeRequest = new CreateAttributeRequest
{
    EntityName = Account.EntityLogicalName,
    Attribute = dtAttribute
};
_serviceProxy.Execute(createAttributeRequest);
Console.WriteLine("Created attribute '{0}' with UserLocal behavior\nfor the Account entity.\n", 
                            dtAttribute.SchemaName);
```
  
 このサンプル コードでは、文字列値 `DateTimeBehavior = "UserLocal"` を直接指定することによって、 `DateTimeBehavior` プロパティの値を設定することもできます。  
  
 日時属性の作成時に、動作を指定しない場合、既定で、属性は `UserLocal` 動作で作成されます。 完全なコード サンプルは、 [サンプル: 日時の値の変換](/dynamics365/customer-engagement/developer/org-service/sample-convert-date-time-behavior)を参照してください。  
  
> [!IMPORTANT]
>  -   動作を `DateOnly` または `TimeZoneIndependent` に設定した状態で、日時属性を作成すると、属性の動作は変更できません。 詳細: [DateTime 属性の動作の変更](behavior-format-date-time-attribute.md#ChangeBehavior)  
> -   動作が `DateOnly` または `TimeZoneIndependent` の日時属性は、 Dynamics 365 for Outlook の以前のバージョンでオフライン モードで編集すると、 `UserLocal` 動作を使用しているかのように処理されます。 これは、このクライアントが新しい動作を認識せず、その動作を `UserLocal` と区別して処理しないことによります。 日時属性はアップグレードで新しい動作に変換されません。したがって、ベスト プラクティスは、カスタマイザーが新しい動作のいずれかを採用する前に、すべての Common Data Service クライアントを最新のリリースにアップグレードすることです。 オンライン時には、フィールドのデータを新しい行動で編集しても問題なく動作します。  
  
<a name="SpecifyFormat"></a>   

## <a name="specify-format-of-the-date-and-time-attribute"></a>日時属性の形式の指定  

 `Format` プロパティを使用して、属性がシステムにどのように保存されているかに関係なく、属性の日付/時刻の表示形式を指定します。 `DateTimeFormat` 列挙体(<xref href="Microsoft.Dynamics.CRM.DateTimeFormat?text=DateTimeFormat EnumType" /> or <xref:Microsoft.Xrm.Sdk.Metadata.DateTimeFormat> 列挙体)を使用して、 `DateAndTime` または `DateOnly` のいずれかの表示形式を指定できます。  
  
 `DateTimeAttributeMetadata.DateTimeBehavior` プロパティが `DateOnly` に設定されている場合、 `DateTimeAttributeMetadata.Format` プロパティの値を `DateAndTime` に設定または変更することはできません。  
  
<a name="UnsupportedQueryOperators"></a>   

## <a name="date-and-time-query-operators-not-supported-for-dateonly-behavior"></a>[日付のみ] の動作でサポートされない日付および時刻のクエリ演算子  

 時刻関連のクエリ演算子は、 `DateOnly` 動作に対してはサポートされません。 ここに表示されている時間固有のクエリ演算子を除いて、すべてのクエリ演算子がサポートされます。  
  
-   が X 分よりも古い  
  
-   が X 時間よりも古い  
  
-   過去 X 時間  
  
-   今後 X 時間  
  
 詳細: [FetchXML の日時クエリ演算子](/dynamics365/customer-engagement/developer/org-service/fiscal-date-older-datetime-query-operators-fetchxml)  
  
<a name="ChangeBehavior"></a>
   
## <a name="change-the-behavior-of-a-date-and-time-attribute"></a>日時属性の動作の変更  

 Common Data Service インスタンスでシステム カスタマイザー ロールを所有していて、日時属性の `DateTimeAttributeMetadata.CanChangeDateTimeBehavior` の管理プロパティが `True` に設定されている場合、日時属性を更新してその動作を変更できます。  
  
> [!CAUTION]
>  日時属性の動作を変更するには、その前に、業務ルール、ワークフロー、計算フィールド、またはロールアップ属性などの属性のすべての依存性を検討して、動作の変更によって問題が発生しないことを確認する必要があります。 システム カスタマイザは、 `DateTimeAttributeMetadata.CanChangeDateTimeBehavior` マネージド プロパティを使用して、既存の日時属性の動作の変更を制限できます。  
>   
>  少なくとも、日時属性の動作を変更した後、変更した日時属性に依存する、業務ルール、ワークフロー、計算属性、およびロールアップ属性の各レコードを開いて、情報を確認し、そのレコードを保存して、最新の属性の動作と値が使用されることを確認する必要があります。  
>   
>  計算属性またはロールアップ属性の日時動作の変更後、計算フィールドまたはロールアップ フィールドの定義エディターを開いて、そのフィールド定義を保存して、動作の変更後、それらの属性が引き続き有効であることを確認します。 システム カスタマイザは、 Common Data Service のカスタマイズ領域の**フィールドの種類**の横にある**編集**をクリックして、計算属性またはロールアップ属性に対するフィールド定義エディターを開くことができます。 詳細: [計算フィールドの定義](/dynamics365/customer-engagement/customize/define-calculated-fields) および [ロールアップ フィールドの定義](/dynamics365/customer-engagement/developer/customize/define-rollup-fields)  
  
-   標準のエンティティとユーザー定義エンティティの `CreatedOn` および `ModifiedOn` 属性の動作は、既定では、 `UserLocal` に設定され、 `DateTimeAttributeMetadata.CanChangeDateTimeBehavior` 管理プロパティは `False` に設定されます。このことは、これらの属性の動作は変更できないことを意味します。 ユーザー定義エンティティのこれらの属性の `DateTimeAttributeMetadata.CanChangeDateTimeBehavior` 管理プロパティの値を変更することはできますが、属性の動作は変更できません。  
  
-   新しいユーザー定義の日時属性の場合は、 `DateTimeAttributeMetadata.CanChangeDateTimeBehavior` 管理プロパティが `True` に設定されています。 このことは、ユーザー定義の日時属性の動作を、 `UserLocal` から `DateOnly` または `TimeZoneIndependent` のいずれかに変更できることを意味しています。他の動作の移行は使用できません。  
  
     Common Data Service 組織の一部であるユーザー定義の日時属性の場合は、その属性または親エンティティがカスタマイズ可能でなければ `DateTimeAttributeMetadata.CanChangeDateTimeBehavior` 管理プロパティは `True` に設定されます。  
  
    > [!NOTE]
    >  属性の `DateTimeAttributeMetadata.DateTimeBehavior` プロパティを `UserLocal` から `DateOnly` に更新するときは、`DateTimeAttributeMetadata.Format` プロパティもかならず `DateAndTime` から `DateOnly` に変更してください。 そうしなければ、例外が発生します。  
  
-   Common Data Service の次の標準の日時属性は、既定では、`DateOnly` に設定され、これらの属性の `DateTimeAttributeMetadata.CanChangeDateTimeBehavior` 管理プロパティは `False` に設定されます。このことは、これらの属性の動作は変更できないことを意味します。  
  
    |日付と時間の属性です。|上位エンティティ|  
    |-----------------------------|-------------------|  
    |anniversary|取引先担当者|  
    |birthdate|取引先担当者|  
    |duedate|請求書|  
    |estimatedclosedate|リード|  
    |actualclosedate|営業案件|  
    |estimatedclosedate|営業案件|  
    |finaldecisiondate|営業案件|  
    |validfromdate|製品|  
    |validtodate|製品|  
    |closedon|見積もり|  
    |expireson|見積もり|  
  
     これらの属性の動作を `UserLocal` に、`DateTimeAttributeMetadata.CanChangeDateTimeBehavior` 管理プロパティを `True` に設定し、 これらの属性の動作を `DateOnly` のみに変更できます。 他の動作の移行は使用できません。  
  
 属性の動作の更新後、変更が有効になるには、そのカスタマイズを公開する必要があります。 日時属性の動作を更新することによって、属性の動作の変更 *後* に入力または更新されたすべての値が、新しい動作でシステムに格納されるようになります。 これは、データベースにすでに格納されている値には影響を与えず、それらは引き続き UTC 値として保存されます。 ただし、既存の値を SDK を使用して取得したり、UI でそれを表示するときは、既存の値はその属性の新しい動作にしたがって表示されます。 たとえば、取引先企業エンティティに関するユーザー定義の属性の動作を、 `UserLocal` から `DateOnly` に変更し、SDK を使用して既存の取引先企業レコードを取り出した場合、日付と時刻は、 \<Date> の後に 12 AM (00:00:00) が続く形式で表示されます。 同様に、 `UserLocal` から `TimeZoneIndependent` への動作の変更の場合、データベースにある実際の値は、タイム ゾーンの変換なしに、そのまま表示されます。  
  
 次のサンプル コードは、新しい日時属性動作の更新方法を示しています。  
  
```csharp
// Retrieve the attribute to update its behavior and format
RetrieveAttributeRequest attributeRequest = new RetrieveAttributeRequest
{
    EntityLogicalName = Account.EntityLogicalName,
    LogicalName = "new_sampledatetimeattribute",
    RetrieveAsIfPublished = false
};
// Execute the request
RetrieveAttributeResponse attributeResponse =
                (RetrieveAttributeResponse)_serviceProxy.Execute(attributeRequest);

Console.WriteLine("Retrieved the attribute '{0}'.",
                attributeResponse.AttributeMetadata.SchemaName);

// Modify the values of the retrieved attribute
DateTimeAttributeMetadata retrievedAttributeMetadata =
                (DateTimeAttributeMetadata)attributeResponse.AttributeMetadata;
retrievedAttributeMetadata.DateTimeBehavior = DateTimeBehavior.DateOnly;
retrievedAttributeMetadata.Format = DateTimeFormat.DateOnly;

// Update the attribute with the modified value
UpdateAttributeRequest updateRequest = new UpdateAttributeRequest
{
    Attribute = retrievedAttributeMetadata,
    EntityName = Account.EntityLogicalName,
    MergeLabels = false
};
_serviceProxy.Execute(updateRequest);
Console.WriteLine("Updated the behavior and format of '{0}' to DateOnly.",
    retrievedAttributeMetadata.SchemaName);

// Publish customizations to the account entity
PublishXmlRequest pxReq = new PublishXmlRequest
{
    ParameterXml = String.Format("<importexportxml><entities><entity>account</entity></entities></importexportxml>")
};
_serviceProxy.Execute(pxReq);
Console.WriteLine("Published customizations to the Account entity.\n");
 
``` 
  
 完全なコード サンプルは、 [サンプル: 日時の値の変換](/dynamics365/customer-engagement/developer/org-service/sample-convert-date-time-behavior)を参照してください。  
  
<a name="Convert"></a>   
## <a name="convert-behavior-of-existing-date-and-time-values-in-the-database"></a>データベース内の既存の日時値の動作の変換 

 日時属性を更新して、属性の動作を `UserLocal` から `DateOnly` または `TimeZoneIndependent` に変更する場合、データベース内の既存の属性値は自動的に変換されません。 この属性の変更は、その属性の変更 *後* に、属性に入力または属性内で更新された値にのみ影響します。 システム内の既存の日付および時刻の値は引き続き UTC 形式であり、前のセクションで説明したとおりに、SDK を使用してまたは UI で取得されたときに、新しい動作にしたがって Common Data Service によって表示されます。 `UserLocal` から `DateOnly` に行動が変更された属性の場合、 `ConvertDateAndTimeBehavior` メッセージを使用して、データベース内の既存の UTC 値を適切な `DateOnly` 値に変換して、データのアノマリを回避することができます。  
  
 このメッセージを使用すると、UTC から DateOnly への値の変換に使用するタイム ゾーンを選択するための変換ルール (組織サービスと連携する場合、 <xref:Microsoft.Xrm.Sdk.Messages.ConvertDateAndTimeBehaviorRequest.ConversionRule>を参照してください) を指定できます。 次のいずれかの変換ルールを指定できます。  
  
-   `SpecificTimeZone`: 指定された Common Data Service タイム ゾーンに従い、UTC 値を DateOnly 値に変換します。 この場合、 <xref:Microsoft.Xrm.Sdk.Messages.ConvertDateAndTimeBehaviorRequest.TimeZoneCode> パラメーターの値を指定する必要もあります。  
  
-   `CreatedByTimeZone`: UTC 値を、レコードを作成したユーザーの UI に表示される DateOnly 値に変換します。  
  
-   `OwnerTimeZone`: UTC値を、レコードを所有するユーザーの UI に表示するDateOnly値に変換します。  
  
-   `LastUpdatedByTimeZone`: UTC 値を、レコードを最後に更新したユーザーの UI に表示する DateOnly 値に変換します。  
  
 <xref:Microsoft.Xrm.Sdk.DateTimeBehaviorConversionRule> クラスの 4 つのメンバーのいずれかを使用して、 <xref:Microsoft.Xrm.Sdk.Messages.ConvertDateAndTimeBehaviorRequest.ConversionRule> パラメーターの有効な値を指定できます。  
  
> [!NOTE]
>  <xref:Microsoft.Xrm.Sdk.Messages.ConvertDateAndTimeBehaviorRequest> メッセージを実行するには、 Common Data Service インスタンスのシステム管理者ロールが必要です。  
  
 `ConvertDateAndTimeBehavior` (組織サービスと連携する場合、 <xref:Microsoft.Xrm.Sdk.Messages.ConvertDateAndTimeBehaviorRequest> メッセージを参照してください)を実行するとき、システム ジョブ (非同期処理) が作成されて、変換要求が実行されます。 メッセージ応答の `ConvertDateAndTimeBehaviorResponse.JobId` 属性には、変換の結果として作成されたシステム ジョブの ID が表示されます。 システム ジョブが完了したら、ジョブの詳細 (`AsyncOperation.Message`) をチェックして、変換の詳細またはエラーを必要に応じて表示します。  
  
> [!NOTE]
>  複数の属性の変換を 1 つの変換ジョブにまとめて、1 つのジョブを一度に実行することを推奨します。これにより、変換時に競合がなくなり、また最適なシステム パフォーマンスが得られます。  
  
 `ConvertDateAndTimeBehavior` メッセージを使用する際に、以下のいくつかの考慮を必要とする重要な点があります。  
  
-   ソリューションのインポート、または属性や上位エンティティの削除などのメッセージの実行中は、 Common Data Service 内のソリューションの大きな変更は避ける必要があります。 これを行うと、予期しない動作が発生することがあります。ただし、データの損失は発生しません。  
  
-   メッセージの実行結果としてシステムで行われる更新では、ワークフローとプラグインは実行されません。  
  
-   メッセージの実行結果としてシステムで行われる更新では、属性の "最終修正日" の値は変更されませんが、更新の監査が行われて、管理者が属性の変換の時刻および元の値と変更後の値を確認するのを支援します。  
  
 次のサンプル コードは、 メッセージの使用方法を示しています。  
  
```csharp
ConvertDateAndTimeBehaviorRequest request = new ConvertDateAndTimeBehaviorRequest()
{
    Attributes = new EntityAttributeCollection() 
            { 
                new KeyValuePair<string, StringCollection>("account", new StringCollection() 
                { "new_sampledatetimeattribute" }) 
            },
    ConversionRule = DateTimeBehaviorConversionRule.SpecificTimeZone.Value,
    TimeZoneCode = 190, // Time zone code for India Standard Time (IST) in CRM
    AutoConvert = false // Conversion must be done using ConversionRule
};

// Execute the request
ConvertDateAndTimeBehaviorResponse response = (ConvertDateAndTimeBehaviorResponse)_serviceProxy.Execute(request);

```
  
 完全なコード サンプルは、 [サンプル: 日時の値の変換](/dynamics365/customer-engagement/developer/org-service/sample-convert-date-time-behavior)を参照してください。  
  
### <a name="see-also"></a>関連項目  
 [サンプル: 日時の値の変換](/dynamics365/customer-engagement/developer/org-service/sample-convert-date-time-behavior.md)   
 [日時フィールドの動作と形式](/dynamics365/customer-engagement/developer/customize/behavior-format-date-time-field)   
 [エンティティ属性メタデータのカスタマイズ](/dynamics365/customer-engagement/developer/customize-entity-attribute-metadata)          
 <xref:Microsoft.Xrm.Sdk.Messages.ConvertDateAndTimeBehaviorRequest>      
 <xref:Microsoft.Xrm.Sdk.Metadata.DateTimeAttributeMetadata> 