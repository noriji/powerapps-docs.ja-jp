---
title: PreOperation RetrieveMultiple を使用したフィルター処理した場合に、すべての種類のクエリを実行する | MicrosoftDocs
description: すべてのアプリケーションの、最適なパフォーマンスと一貫した結果を得るには、RetrieveMultiple の PreOperation に登録されたプラグインを使用できるすべての種類のクエリに対してフィルター処理を実行する必要があります
services: ''
suite: powerapps
documentationcenter: na
author: JimDaly
manager: ryjones
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 09/23/2019
ms.author: jdaly
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="implement-all-types-of-queries-when-filtering-results-using-preoperation-retrievemultiple"></a>PreOperation RetrieveMultiple を使用したフィルター処理した場合に、すべての種類のクエリを実行する

**カテゴリ**: 設計、パフォーマンス、セキュリティ、サポート性

**影響の可能性**: 中程度

<a name='symptoms'></a>

## <a name="symptoms"></a>現象

別のアプリケーションからの RetrieveMultiple の呼び出しは異なる結果を表示します。

- 例: レガシ アプリケーションの同じビューには、新しいアプリケーションでの異なる結果が表示されます。

<a name='guidance'></a>

## <a name="guidance"></a>ガイダンス

> [!NOTE]
> `Retrieve` メッセージと `RetrieveMultiple` メッセージは　最もよく使用されるメッセージです。 これらのメッセージのプラグインは、システムのパフォーマンスが影響を受ける可能性があります。 通常、要件が他の方法でも達成することができる場合は、これらのメッセージのプラグインを使用しないようにする必要があります。 詳細: [Retrieve メッセージと RetrieveMultiple メッセージ用のプラグインの登録を制限する](limit-registration-plugins-retrieve-retrievemultiple.md)

`RetrieveMultiple` メッセージに登録されたプラグインは、通常、エンティティのクエリで返された結果をフィルターするためのものです。 `PostOperation` ステージまたは `PreOperation` ステージのいずれかに登録されたプラグインを使用してこれをおこなう 2 つの戦略があります。

### <a name="postoperation-filtering"></a>PostOperation フィルター処理

`PostOperation` ステージでは、<xref:Microsoft.Xrm.Sdk.IExecutionContext.OutputParameters>`BusinessEntityCollection`<xref:Microsoft.Xrm.Sdk.EntityCollection.Entities> プロパティから返されるレコードを評価し、返すべきではないエンティティを削除します。

この方法は、結果の各ページで返されるレコードの想定数を潜在的に変更し、データがアプリケーションで表示される際に一貫していないエクスペリエンスへとつながる可能性があります。

### <a name="preoperation-filtering"></a>PostOperation フィルター処理

`PreOperation` ステージで、<xref:Microsoft.Xrm.Sdk.IExecutionContext.InputParameters>  <xref:Microsoft.Xrm.Sdk.Messages.RetrieveMultipleRequest.Query> プロパティを評価し、実行前に何が返されるかをフィルター処理するクエリを調整します。

この方法を使用する場合は、異なる種類のクエリに対して適切なフィルター処理を実行する必要があります。最も重要なクエリは <xref:Microsoft.Xrm.Sdk.Query.FetchExpression> と<xref:Microsoft.Xrm.Sdk.Query.QueryExpression>です。 これらのうち一つのみを実行した場合は、その他の種類のクエリを使用する異なるアプリケーションには変更は適用されません。

`QueryExpressionToFetchXml` メッセージと `FetchXmlToQueryExpression` メッセージはある種類のクエリから他へと変換する機能がありますが、`RetrieveMultiple` 内にその他の呼び出しを含めることのパフォーマンスへの影響から、このコンテキストでこれらのメッセージを使用しないことをお勧めします。 むしろ、両方で同等のロジックを使用してフィルター処理を実行してください。 

`RetrieveMultiple`: <xref:Microsoft.Xrm.Sdk.Query.QueryByAttribute> で使用できる 3 番目の種類のクエリもあります。 この種類のクエリは、複雑なフィルター処理はおこなわず、プラグイン内にさらに複雑なフィルター処理を行うロジックを含めることはできません。 幸い、このクエリは頻繁には使用されません。 加えるフィルター処理の必要性によって、<xref:Microsoft.Xrm.Sdk.InvalidPluginExecutionException> をスローすることでこの種類のクエリを拒否することを選択することもできます。

## <a name="example"></a>例

推奨される戦略例については、[サンプル: PreOperation ステージでクエリを変更する](../../org-service/samples/modify-query-preoperation-stage.md) を参照してください。

## <a name="problematic-patterns"></a>問題となるパターン

<xref:Microsoft.Xrm.Sdk.Query.FetchExpression> または <xref:Microsoft.Xrm.Sdk.Query.QueryExpression> のいずれかのアプリケーションによって使用されているクエリの一つの種類のみを使用する、特定アプリケーションから返されるレコードを変更するようにプラグインが書かれている場合、結果がその他のアプリケーションで一貫しないことがある、またはアプリケーションが使用されているクエリの種類を変更する場合。 プラグインは、アプリケーションにかかわらず同じ結果を達成するように書かれている必要があります。

<a name='additional'></a>

## <a name="additional-information"></a>追加情報

Web API を使用する場合、クエリが  [ あらかじめ定義されたクエリの取得と実行](../../webapi/retrieve-and-execute-predefined-queries.md) で説明されている FetchXml を使用しない限り、コレクションでの GET 要求は、 <xref:Microsoft.Xrm.Sdk.Query.QueryExpression> に変換されます。 この場合の、クエリは <xref:Microsoft.Xrm.Sdk.Query.FetchExpression> を使用します。

モデル駆動型アプリのレガシ Web クライアントは、統一インターフェイスと置き換えられます。 統一インターフェイスは、[SavedQuery.FetchXml](../../reference/entities/savedquery.md#BKMK_FetchXml) または [UserQuery.FetchXml](../../reference/entities/userquery.md#BKMK_FetchXml) で定義された FetchXml を使用します。 より良いパフォーマンスを得るために、統一インターフェイスは、クエリをレガシ Web クライアントがおこなったようにこれらのクエリを実行する前に、FetchXml データを <xref:Microsoft.Xrm.Sdk.Query.QueryExpression> に変換しません。 したがって、<xref:Microsoft.Xrm.Sdk.Query.QueryExpression> を使用したレガシ Web クライアントのプラグイン コードで修正されたクエリは、プラグイン コードが同じロジックを <xref:Microsoft.Xrm.Sdk.Query.FetchExpression> クエリに対して適用するように書かれていない限り、ビューをサポートするクエリは、<xref:Microsoft.Xrm.Sdk.Query.FetchExpression> を使用して渡されているため、同じ変更には適用されません。 

<a name='seealso'></a>

### <a name="see-also"></a>関連項目

[サンプル: PreOperation ステージでクエリを変更する](../../org-service/samples/modify-query-preoperation-stage.md)<br />
[組織サービスを使用したクエリ データ](../../org-service/entity-operations-query-data.md)<br />
[FetchXML の使用によるクエリの作成](../../use-fetchxml-construct-query.md)<br />
[QueryExpression でクエリを作成する](../../org-service/build-queries-with-queryexpression.md)<br />
[retrieve および RetrieveMultiple メッセージ用のプラグインの登録を制限する](limit-registration-plugins-retrieve-retrievemultiple.md)<br />
[統一インターフェイスのコミュニティ](https://community.dynamics.com/365/unified-interface/)