---
title: カスタム仮想エンティティ データ プロバイダ (Common Data Service) | Microsoft Docs
description: Common Data Service Data SDK の使用により、.NET Developers には、既存のデータ プロバイダーがサポートしていない外部データ ソースの種類を統合するために役立つ、カスタム仮想エンティティ データ プロバイダーを作成するオプションがあります。
ms.date: 09/05/2019
ms.service: powerapps
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: d329dade-16c5-46e9-8dec-4b8efb996d22
author: mayadumesh
ms.author: jdaly
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---

# <a name="custom-virtual-entity-data-providers"></a>カスタム仮想エンティティ データ プロバイダー

Common Data Service Data SDK の使用により、.NET Developers には、既存のデータ プロバイダーがサポートしていない外部データ ソースの種類を統合するために役立つ、カスタム仮想エンティティ データ プロバイダーを作成するオプションがあります。 各データ プロバイダーは、サポートされる CRUD 操作を実装する一連の再利用可能な Common Data Service プラグインで構成されます。 (初期リリースは **Retrieve** および **RetrieveMultiple** 読み取り命令に制限されます。) このセクションには、データ プロバイダー、およびコード例を含むカスタム プロバイダーを開発するためのアプローチに関する基本情報が用意されています。

> [!NOTE]
> カスタム データ ソース プロバイダー作成の代替策として、既存のデータ データ プロバイダー対するデータ ソースの調整を検討する必要があります。 たとえば、外部データ ソースに対して OData v4 インターフェイスを作成する場合、用意された標準 OData v4 データ プロバイダーを使用して直接アクセスすることができます。 この REST インターフェイスを追加するメカニズムは、基盤となるデータ サービス テクノロジにより異なります。たとえば、[WCF Data Services 4.5](https://docs.microsoft.com/dotnet/framework/data/wcf/) を参照してください。 OData は広範囲に及ぶ専用ツールおよび互換性技術を持ち、業界からの広い支持を得ています。


## <a name="prerequisites"></a>前提条件

カスタム データ プロバイダーには、作成および管理のための実質的開発リソースが必要です。 次の領域の基本的な知識が必要です。

- 外部データ ソース スキーマおよび関連するデータ アクセスの技術。  このドメインに関する知識は、外部データ ソースの種類特有です。
- Common Data Service メタデータ スキーマ: 詳細: [コードを使用してメタデータを扱う](../metadata-services.md)。
- Common Data Service イベント フレームワーク: 詳細: [イベント フレームワーク](../event-framework.md)。 
- Common Data Service プラグイン アーキテクチャと開発: 詳細: [ビジネス プロセスを拡張するためのプラグインの使用](../plug-ins.md)。

`Microsoft.Xrm.Sdk.Data.dll` アセンブリは NuGet パッケージとして次から入手可能です: [Microsoft.CrmSdk.Data](https://www.nuget.org/packages/Microsoft.CrmSdk.Data/)

## <a name="categories-of-providers"></a>プロバイダのカテゴリ

仮想データ SDK アセンブリを使用して作成することができるデータ プロバイダーには、汎用または対象の 2 つの全般カテゴリがあります。 以下の表はこれらのアプローチを説明し、そのアプローチに最適なデータ プロバイダー開発モデルを照合します。

|**カテゴリ**|**Dev モデル**|**説明**|
|------------|-------------|---------------|
|汎用|「地金」プロバイダ|このプロバイダーは、関連要求に対する FetchXML クエリ式を外部データ ソースに柔軟に変換して、結果のエンティティ インスタンスを返すことができます。 このようなプロバイダーは、このデータ ソースの種類のすべてのインスタンスで再使用することができます。 このアプローチは最も一般的ですが、開発はより複雑になります。  データ ソースのスキーマを変更する場合、影響を受ける仮想エンティティは再マッピングのみが必要です。|
|対象|既知のスキーマの LINQ プロバイダー|このようなプロバイダーは、関連する LINQ コールに対するクエリのみを、既知の、既存データ ソースのインスタンスに変換します。 [LINQ 照会に対してデータ ソースを有効にする](/dotnet/csharp/programming-guide/concepts/linq/enabling-a-data-source-for-linq-querying1) のトピックスで説明されているように、データ ソースは LINQ プロバイダーである必要があります。 このアプローチは特定のデータ ソースのインスタンスに制限されますが、コーディングの必要が少なくなります。 データ ソースのスキーマを変更する場合、プロバイダーを更新および再作成する必要があります。|

汎用プロバイダの例として、標準 Odata v4 データプロバイダと、 Cosmos DB データプロバイダ が挙げられます。

## <a name="steps-to-use-a-custom-data-provider"></a>カスタム データ プロバイダーを使用する手順

Common Data Service アプリケーションにインポートすることができる仮想エンティティ データ プロバイダー ソリューションを作成するために必要な、いくつかの手順があります。

1. カスタム データ プロバイダー プラグイン DLL (または一連の DLL) を開発します。
2. プラグイン登録ツール (PRT) を使用して、Common Data Service サービスを持つカスタム データ プロバイダーを登録します。
3. データ プロバイダー ソリューションを作成します。
4. データの種類または特定のインスタンスを反映するデータ ソース エンティティをカスタマイズします。
5. カスタム データ プロバイダー ソリューションをエクスポートします。


### <a name="plug-in-development"></a>プラグインの開発

このリリースのバーチャル エンティティは読み取り専用であるため、**取得**および **RetrieveMultiple** イベントに登録されたプラグインの形式でデータ プロバイダーを記述します。 各イベントには、戻すデータの種類を説明する実行コンテキスト内の情報が含まれます。 

|**イベント**|**実行コンテキスト**|
|---------|---------------------|
|**取得**|取得するエンティティと共に、含める属性および関連エンティティについて説明します。|
|**RetrieveMultiple**|クエリを定義する <xref:Microsoft.Xrm.Sdk.Query.QueryExpression> オブジェクトを含めます。 フレームワークには、クエリ式ツリーの異なる部分を参照するように設計された **QueryExpressionVisitor** クラスが含まれます。|

両方のイベントで、以下の内容が必要です。

1. 実行コンテキスト内のそれぞれの情報を、外部データ ソースに対して機能するクエリに変換します。
2. データを外部システムから取得します。
3. **取得**の場合、<xref:Microsoft.Xrm.Sdk.Entity> にデータを変換します。それ以外の場合、**RetrieveMultiple** は、<xref:Microsoft.Xrm.Sdk.EntityCollection> に変換します。 この結果は、 Common Data Service プラットフォームを介してクエリを実行するユーザに返されます。 

<xref:Microsoft.Xrm.Sdk.Data> 名前空間のクラスは、 Common Data Service クエリ情報を実行コンテキストから外部データソースに適した形式のクエリにマッピングするための、フレームワークを提供します。 このフレームワークは、データを Common Data Service プラットフォームにて想定された適切な <xref:Microsoft.Xrm.Sdk.Entity> 型または <xref:Microsoft.Xrm.Sdk.EntityCollection> 型に変換する際に役立ちます。 

#### <a name="data-provider-exceptions"></a>データ プロバイダーの例外

何らかの理由で期待した結果をコードが実現できない場合、適切なエラーをスローする必要があります。 <xref:Microsoft.Xrm.Sdk.Data.Exceptions> 名前空間には、この目的のために使用できる、 <xref:Microsoft.Xrm.Sdk.SdkExceptionBase> から派生した次の例外クラスが含まれます。  

|**例外クラス**|**説明**|
|---------------|-----------|
|<xref:Microsoft.Xrm.Sdk.Data.Exceptions.AuthenticationException>|エラーは外部データ ソース サービスに対するセキュリティ認証中に発生します。たとえば、外部データ サービスから受け取る HTTP ステータス 401 です。 通常、現在のユーザーが適切な特権を持たない場合、または関連付けられた **EntityDataSource** の接続情報が不正確であるために発生します。|
|<xref:Microsoft.Xrm.Sdk.Data.Exceptions.EndpointException>|データ ソース エンティティ内のエンドポイント構成が無効、またはエンドポイントが存在しません。|
|<xref:Microsoft.Xrm.Sdk.Data.Exceptions.GenericDataAccessException>|一般的なデータ 悪性 エラーで、エラーがより具体的な例外に対してマッピングされない時に使用します。|
|<xref:Microsoft.Xrm.Sdk.Data.Exceptions.InvalidMetadataException>| |
|<xref:Microsoft.Xrm.Sdk.Data.Exceptions.InvalidQueryException>|指定されたクエリが無効です。たとえば無効な句の組み合わせ、またはサポートされていない比較演算子です。|
|<xref:Microsoft.Xrm.Sdk.Data.Exceptions.ObjectNotFoundException>|外部データ ソースで指定されたレコードが存在しません。|
|<xref:Microsoft.Xrm.Sdk.Data.Exceptions.TimeoutException>|許容時間内に外部オペレーションが完了しませんでした。たとえば、外部データ サービスからの HTTP ステータス 408 の結果です。|


### <a name="plug-in-registration"></a>プラグイン登録

通常のプラグインと違い、 各イベントのアセンブリとプラグインの登録には Plugin Registration Tool (PRT) のみが必要をなります。 特定のステップは登録しません。 プラグインは、通常のプラグイン ステップでは利用可能でないオペレーションのコア トランザクション ステージである、ステージ 30 で実行します。 ステップを登録する代わりに、次のエンティティを使用して、データ プロバイダーを構成します。 


|**エンティティ**|**説明**|
|-----|-----|
|[EntityDataProvider](../reference/entities/entitydataprovider.md)|各イベントで使用するプラグインおよびデータ ソースの論理名を定義します。|
|[EntityDataSource](../reference/entities/entitydatasource.md)|認証に必要な秘密情報を含め、外部データ ソースに必要なエンティティ コンテキストと接続情報を提供します。|

仮想エンティティのメタデータが構成されると、プラグインは PRT を使用して登録されて、正確な構成データが **EntityDataProvider** および **EntityDataSource** エンティティのにセットされ、仮想エンティティは要求に対する応答を開始します。

### <a name="debugging-plug-ins"></a>プラグインのデバッグ

カスタム仮想エンティティ プロバイダーは、プラグインの種類です。 これらのトピックの情報を使用して、カスタム仮想エンティティ プロバイダーのためのプラグインをデバッグします: [プラグインのデバッグ](../debug-plug-in.md) と [チュートリアル: プラグインのデバッグ](../tutorial-debug-plug-in.md)。


### <a name="see-also"></a>関連項目

[仮想エンティティに関する入門情報](get-started-ve.md)<br />
[仮想エンティティの API に関する考慮事項](api-considerations-ve.md)<br />
[サンプル: 汎用仮想エンティティ データ プロバイダー プラグイン](sample-generic-ve-plugin.md)

 