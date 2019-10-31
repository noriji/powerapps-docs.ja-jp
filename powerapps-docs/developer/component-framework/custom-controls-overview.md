---
title: コード コンポーネントとは? | MicrosoftDocs
description: PowerApps Component Framework を使用してコード コンポーネントを作成し、フォーム、ビュー、ダッシュボードでデータを表示して作業する高度なユーザー エクスペリエンスを提供します。
manager: kvivek
ms.date: 09/05/2019
ms.service: powerapps
ms.topic: article
ms.assetid: 135481cd-4583-4e49-8f58-02f32a9b054a
ms.author: nabuthuk
author: Nkrb
---

# <a name="what-are-code-components"></a>コード コンポーネントとは

コード コンポーネントはソリューション コンポーネントの一種です。つまり、コード コンポーネントをソリューション ファイルに含めて異なる環境にインストールできます。 詳細: [ソリューションを使用した拡張機能のパッケージ化および配布](https://docs.microsoft.com/dynamics365/customer-engagement/developer/package-distribute-extensions-use-solutions).

コード コンポーネントをソリューションに含めて追加し、そして Common Data Service にインポートします。 Common Data Service に組み込まれたら、システム管理者およびシステム カスタマイザーは、フィールド、サブグリッド、ビュー、ダッシュボード サブグリッドで構成し、既定のコンポーネントの代わりに使用できます。 キャンバス アプリでこれたのコード コンポーネントも追加できます。 

コード コンポーネントは 3 つの要素で構成されています:

1. [マニフェスト](#manifest)
2. [コンポーネント実装ライブラリ](#component-implementation-library)
3. [リソース](#resources)

## <a name="manifest"></a>マニフェスト

マニフェストはコンポーネントを定義するメタデータ ファイルです。 それは次を記述する XML 文書です:

- コンポーネントの名前
- 構成が可能なデータの種類、フィールドまたはデータセット。
- コンポーネントが追加されたときにアプリケーションで構成できる任意のプロパティ。
- コンポーネントが必要とするリソース ファイルの一覧。 
- 必要なコンポーネント インタフェースを適用するオブジェクトを返すコンポーネント実装ライブラリの TypeScript 関数名。

ユーザーがコード コンポーネントを設定したときに、マニフェスト ファイルのデータは利用可能なコンポーネントを除外して、コンテキストに有効なコンポーネントのみ構成に使用できるようにします。 コンポーネントのマニフェストで定義されたプロパティは、ユーザーがコンポーネントの設定時に値を指定できるよう構成フィールドとして表示されます。 これらのプロパティ値は、実行時にコンポーネントで利用可能になります。 詳細: [マニフェスト ファイルの参照](manifest-schema-reference/index.md)

## <a name="component-implementation-library"></a>コンポーネント実装ライブラリ

PowerApps component framework を使用してコード コンポーネントを開発する場合は、コンポーネント ライブラリの実装は重要なステップのひとつです。 開発者は TypeScript を使用してコンポーネント ライブラリを実装できます。 各コード コンポーネントは、コード コンポーネント インタフェースに記述されたメソッドを実装したオブジェクトを返すことができる、関数の定義を含むライブラリが必要です 

オブジェクトは次のメソッドを実装します:

- [init](reference/control/init.md) (必須)
- [updateView](reference/control/updateview.md) (必須)
- [getOutputs](reference/control/getoutputs.md) (オプション)
- [destroy](reference/control/destroy.md) (必須)

これらのメソッドはコード コンポーネントのライフサイクルを制御します。

### <a name="page-load"></a>ページの読み込み

ページを読み込む時に、アプリケーションは作業するオブジェクトを必要とします。 マニフェスト ファイルからのデータを使用して、コードは呼び出しによってオブジェクトを取得します

```js
var obj =  new <"namespace on manifest">.<"constructor on manifest">();
```

マニフェストの名前空間とコンストラクターの値がそれぞれ `SampleNameSpace` と `LinearInputComponent` である場合、オブジェクトをインスタンス化するコードはこれになります:

```js
var controlObj = new SampleNameSpace.LinearInputComponent();
```

ページの準備ができたら、一連のパラメーターとともに [init](reference/control/init.md) メソッドを呼び出してコンポーネントを初期化します。

```js
controlObj.init(context,notifyOutputChanged,state,container);
```

|パラメーター|説明|
|---|---|
|コンテキスト| コンポーネントの構成方法に関するすべての情報と、 [PowerApps Component Framework API](reference/index.md) とともにコンポーネント内で使用できるすべてのパラメータを含みます。 たとえば、`context.parameters.<"property name from manifest">` を入力プロパティへのアクセスに使用できます。|
|notifyOutputChanged |コード コンポーネントに非同期に取得可能な新しい出力があるとフレームワークに警告します。|
|状態|コンポーネントがすでに [setControlState](reference/mode/setcontrolstate.md) メソッドを使用して、以前に明示的に保存した場合は、現在のセッションで以前読み込まれたページのコンポーネント データが含まれます。|
|コンテナ|開発者とアプリ メーカーが、コンポーネントを定義する UI の HTML 要素を追加することができるHTML div 要素。|

### <a name="user-changes-data"></a>ユーザーがデータを変更する

ページがロードされると、ユーザーがデータを変更するためにコンポーネントを操作するまで、コンポーネントはデータを表示します。 これが発生すると、好きなように管理できますが、 [init](reference/control/init.md) メソッドで *notifyOutputChanged* パラメータとして渡されるメソッドを呼び出す必要があります。 このメソッドを使用すると、プラットフォームは、 [getOutputs](reference/control/getoutputs.md) メソッドを呼び出すことで応答します。 [getOutputs](reference/control/getoutputs.md) メソッドでは、ユーザーが行った変更を含む値が返されます。 フィールド コンポーネントの場合、通常これはコンポーネントの新しい値になります。

### <a name="app-changes-data"></a>アプリがデータを変更する

プラットフォームがデータを変更すると、コンポーネントの [updateView](reference/control/updateview.md) メソッドを呼び出し、新しいコンテキスト オブジェクトをパラメータとして渡します。 このメソッドを実装し、コンポーネントに表示された値を更新する必要があります。

### <a name="page-close"></a>ページを閉じる

ユーザーがページから離れると、コード コンポーネントがスコープを失い、オブジェクトのそのページに割り当てられたすべてのメモリが消去されます。 ただし、ブラウザの実装メカニズムに基づくいくつかのメソッドは、消去されずにメモリを消費し続ける可能性があります。 通常、これらはイベント ハンドラーです。 ユーザーがこの情報を保存する必要がある場合は、同じセッション内で次回、情報が渡されるように [setControlState](reference/mode/setcontrolstate.md) メソッドを実装する必要があります。

開発者は、イベント ハンドラーの削除など、クリーンアップ コードを削除するためにページがクローズするときに呼び出されるを [破棄](reference/control/destroy.md) メソッドを実行する必要があります。

## <a name="resources"></a>リソース

各コード コンポーネントは視覚化を構築するためのリソース ファイルが必要です。 マニフェストでリソース ファイルを定義できます。 マニフェスト ファイルのリソース ノードは、コンポーネントが視覚化を実装するために必要なリソースを参照します。 詳細: [リソース](manifest-schema-reference/resources.md)

### <a name="related-topics"></a>関連トピック

[コード コンポーネントの作成](create-custom-controls-using-pcf.md)
