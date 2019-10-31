---
title: TypeScript を使用したコード コンポーネントの実装 | MicrosoftDocs
description: TypeScript を使用してコード コンポーネントを実装する方法
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.topic: index-page
ms.assetid: 18e88d702-3349-4022-a7d8-a9adf52cd34f
ms.author: nabuthuk
author: Nkrb
---

# <a name="implement-components-using-typescript"></a>TypeScript を使ってコンポーネントを実装する

このチュートリアルでは、Typescript で新しいコード コンポーネントを作成する手順を説明します。 サンプル コンポーネントは、ユーザーがフィールドに値を入力する代わりに、ビジュアル スライダーを使用して数値を入力できる線形入力コンポーネントです。 

## <a name="creating-a-new-component-project"></a>新しいコンポーネント プロジェクトを作成する

新しいプロジェクトを作成するには:

1. **VS 2017 のコマンド プロンプトの作成** ウィンドウを開きます。
1. コマンドを使用してプロジェクトの新規フォルダを作成する 
    ```CLI
    mkdir LinearComponent
    ```

1. `cd LinearComponent` コマンドを使用して、新規ディレクトリに移動します。 
   
1. 以下のコマンドを実行し、基本パラメータを渡す新しいコンポーネントプロジェクトを作成します。

   ```CLI
    pac pcf init --namespace SampleNamespace --name TSLinearInputComponent --template field
    ``` 

1. `npm install` コマンドを使用して、プロジェクトのビルド ツールをインストールします。 
2. 任意の開発者環境でプロジェクト フォルダー `C:\Users\<your name>\Documents\<My_PCF_Component` ) を開き、コード コンポーネントの開発を始めます。 最も簡単に始めるには、`C:\Users\<your name>\Documents\<My_PCF_Component>` ディレクトリに入ったら、コマンド プロンプトから `code .` を実行する方法です。 このコマンドは、**Visual Studio コード**にあるコンポーネント プロジェクトを開きます。

## <a name="implementing-manifest"></a>マニフェストの実装

マニフェストは、コード コンポーネントのメタデータを含む XML ファイルです。 また、コード コンポーネントの動作も定義します。 このチュートリアルでは、`<Your component Name>` サブフォルダーでマニフェスト ファイルが作成されます。 Visual Studio コードで `ControlManifest.Input.xml` ファイルを開くと、ファイル マニフェストの一部のプロパティが既に定義済みであることがわかります。 以下に示すように、これらのあらかじめ定義されたマニフェスト ファイルに変更を加えます。

1. [コントロール](manifest-schema-reference/control.md) ノードは、コード コンポーネントの名前空間、バージョン、および表示名を定義します。 次に、以下に示すように、[コントロール](manifest-schema-reference/control.md)ノードの各プロパティを定義します。

   - **名前空間**: コード コンポーネントの名前空間。 
   - **コンストラクター**: コード コンポーネントのコンストラクター。
   - **バージョン**: コンポーネントのバージョン。 コンポーネントを更新すると、ランタイムで変更を表示するにはバージョンを更新する必要があります。
   - **display-name-key**: UI で表示するコード コンポーネントの名前。
   - **description-name-key**: UI に表示されるコード コンポーネントの説明。
   - **control-type**: コード コンポーネントの種類。 コード コンポーネントの *標準*タイプのみサポートされています。

     ```XML
      <?xml version="1.0" encoding="utf-8" ?>
      <manifest>
      <control namespace="SampleNameSpace" constructor="TSLinearInputComponent" version="1.0.0" display-name-key="Linear Input Component" description-key="Allows you to enter the numeric values using the visual slider." control-type="standard">
     ```

2. [プロパティ](manifest-schema-reference/property.md) ノードは、フィールドのデータ型の定義など、コード コンポーネントのプロパティを定義します。 プロパティ ノードは、コントロール要素の下の子要素として指定されます。 [プロパティ](manifest-schema-reference/property.md) ノードを下記に示す通り定義します。

   - **名前**: プロパティの名前。
   - **display-name-key**: UI に表示されるプロパティの表示名。
   - **description-name-key**: UI に表示されるプロパティの説明。 
   - **of-type-group**: [of-type-group](manifest-schema-reference/type-group.md) は、2 つ以上のデータ フィールドが必要な場合に使用されます。 [of-type-group](manifest-schema-reference/type-group.md) 要素をマニフェストの `property` 要素の兄弟として追加します。 `of-type-group` はコンポーネント値を指定し、整数、通貨、浮動小数点、または 10 進数値を含めることができます。
   - **使用**: *バインド*と*入力*の 2 つのプロパティがあります。 バインドされたプロパティは、フィールドの値にのみバインドされたものです。 入力プロパティはフィールドにバインドされたか、静的な値を有効にするものです。
   - **必須**: プロパティが必要かどうかを定義します。

     ```XML
      <property name="sliderValue" display-name-key="sliderValue_Display_Key" description-key="sliderValue_Desc_Key" of-type-group="numbers" usage="bound" required="true" />
      ```
3. [リソース](manifest-schema-reference/resources.md)ノードは、コード コンポーネントのビジュアル化を定義します。 コード コンポーネントを構成するすべてのリソースが含まれています。 [コード](manifest-schema-reference/code.md)は、リソース要素の下の子要素として指定されます。 [リソース](manifest-schema-reference/resources.md)を下記に示す通り定義します。

   - **コード**: すべてのリソース ファイルが設置されるファイル パスを参照します。
 
      ```XML
      <resources>
        <code path="index.ts" order="1" />
        <css path="css/TS_LinearInputComponent.css" order="1" />
        </resources>
        ```
      マニフェスト ファイル全体は、次のように表示されます。 

     ```XML
      <?xml version="1.0" encoding="utf-8" ?>
      <manifest>
      <control namespace="SampleNamespace" constructor="TSLinearInputComponent" version="1.0.0" display-name-key="Linear Input Component" description-key="Allows you to enter the numeric values using the visual slider." control-type="standard">
        <type-group name="numbers">
          <type>Whole.None</type>
          <type>Currency</type>
          <type>FP</type>
          <type>Decimal</type>
         </type-group>
        <property name="sliderValue" display-name-key="sliderValue_Display_Key" description-key="sliderValue_Desc_Key" of-type-group="numbers" usage="bound" required="true" />
       <resources>
         <code path="index.ts" order="1" />
         <css path="css/TS_LinearInputComponent.css" order="1" />
       </resources>
      </control>
     </manifest>
     ```

4. `ControlManifest.Input.xml` ファイルに加えた変更を保存します。
5. 次に、 `TSLinearInputComponent` フォルダー内に新しいフォルダーを作成し、 **css** という名前を付けます。
6. CSS ファイルを[コード コンポーネントにスタイルを追加する](#adding-style-to-the-code-component)に作成します。
7. コマンド `npm run build` を使用してコンポーネント プロジェクトをビルドします
8. このビルドは、`TSLinearInputComponent/generated` フォルダーにある更新された Typescript 型宣言ファイルを生成します。

## <a name="implementing-component-logic"></a>コンポーネント ロジックの実装

マニフェスト ファイルを実行した後の次の手順は、TypeScript を使用してマニフェスト ファイルをコンポーネントのロジックに実装することです。 コンポーネントのロジックは、`index.ts` ファイル内で実装する必要があります。 `index.ts` ファイルを Visual Studio コード内で開く場合、4 つの重要なクラスがあらかじめ定義されていることがわかります。 次に、コード コンポーネントのロジックを実装します。 

1. 任意のコードエディタで `index.ts` ファイルを開きます。
2. 次のコードで `TSLinearInputComponent` クラスを更新します。

```TypeScript
import { IInputs, IOutputs } from "./generated/ManifestTypes";
export class TSLinearInputComponent
  implements ComponentFramework.StandardControl<IInputs, IOutputs> {
  // Value of the field is stored and used inside the component
  private _value: number;
  // PowerApps component framework delegate which will be assigned to this object which would be called whenever any update happens.
  private _notifyOutputChanged: () => void;
  // label element created as part of this component
  private labelElement: HTMLLabelElement;
  // input element that is used to create the range slider
  private inputElement: HTMLInputElement;
  // Reference to the component container HTMLDivElement
  // This element contains all elements of our code component example
  private _container: HTMLDivElement;
  // Reference to PowerApps component framework Context object
  private _context: ComponentFramework.Context<IInputs>;
  // Event Handler 'refreshData' reference
  private _refreshData: EventListenerOrEventListenerObject;

  constructor() {}

  public init(
    context: ComponentFramework.Context<IInputs>,
    notifyOutputChanged: () => void,
    state: ComponentFramework.Dictionary,
    container: HTMLDivElement
  ) {
    this._context = context;
    this._container = document.createElement("div");
    this._notifyOutputChanged = notifyOutputChanged;
    this._refreshData = this.refreshData.bind(this);
    // creating HTML elements for the input type range and binding it to the function which refreshes the component data
    this.inputElement = document.createElement("input");
    this.inputElement.setAttribute("type", "range");
    this.inputElement.addEventListener("input", this._refreshData);
    //setting the max and min values for the component.
    this.inputElement.setAttribute("min", "1");
    this.inputElement.setAttribute("max", "1000");
    this.inputElement.setAttribute("class", "linearslider");
    this.inputElement.setAttribute("id", "linearrangeinput");
    // creating a HTML label element that shows the value that is set on the linear range component
    this.labelElement = document.createElement("label");
    this.labelElement.setAttribute("class", "TS_LinearRangeLabel");
    this.labelElement.setAttribute("id", "lrclabel");
    // retrieving the latest value from the component and setting it to the HTMl elements.
    this._value = context.parameters.sliderValue.raw
      ? context.parameters.sliderValue.raw
      : 0;
    this.inputElement.setAttribute(
      "value",
      context.parameters.sliderValue.formatted
        ? context.parameters.sliderValue.formatted
        : "0"
    );
    this.labelElement.innerHTML = context.parameters.sliderValue.formatted
      ? context.parameters.sliderValue.formatted
      : "0";
    // appending the HTML elements to the component's HTML container element.
    this._container.appendChild(this.inputElement);
    this._container.appendChild(this.labelElement);
    container.appendChild(this._container);
  }

  /**
   * Updates the values to the internal value variable we are storing and also updates the html label that displays the value
   * @param context : The "Input Properties" containing the parameters, component metadata and interface functions
   */

  public refreshData(evt: Event): void {
    this._value = (this.inputElement.value as any) as number;
    this.labelElement.innerHTML = this.inputElement.value;
    this._notifyOutputChanged();
  }

  public updateView(context: ComponentFramework.Context<IInputs>): void {
    // storing the latest context from the control.
    this._value = context.parameters.sliderValue.raw
      ? context.parameters.sliderValue.raw
      : 0;
    this._context = context;
    this.inputElement.setAttribute(
      "value",
      context.parameters.sliderValue.formatted
        ? context.parameters.sliderValue.formatted
        : ""
    );
    this.labelElement.innerHTML = context.parameters.sliderValue.formatted
      ? context.parameters.sliderValue.formatted
      : "";
  }

  public getOutputs(): IOutputs {
    return {
      sliderValue: this._value
    };
  }

  public destroy() {
    this.inputElement.removeEventListener("input", this._refreshData);
  }
}

```

3. コマンド `npm run build` を使用してコントロール プロジェクトを再構築します。 
 
4. コンポーネントは `out/controls/TSLinearInputComponent` フォルダにコンパイルされます。 構築アーティファクトには以下が含まれます:

   - bundle.js – バンドルされたコンポーネントのソースコード 
   - ControlManifest.xml – Common Data Service にアップロードされるコンポーネント マニフェスト ファイル。

## <a name="adding-style-to-the-code-component"></a>コード コンポーネントにスタイルを追加する

開発者およびアプリ作成者は、CSS を使用してコード コンポーネントを表するためのスタイルを定義できます。 CSS は、スタイル、、色、レイアウトやフォントを含む、コード コンポーネントのプレゼンテーションを開発者が説明できるようにします。 線形入力コンポーネントの [init](reference/control/init.md) メソッドは、入力の要素を作成し、クラス属性を `linearslider` に設定します。 `linearslider` クラスのスタイルは別に `CSS` ファイルで定義されます。 `CSS` ファイルのような追加のコンポーネント リソースをコード コンポーネントに含め、さらにカスタマイズをサポートすることができます。

1. `TSLinearInputComponent` フォルダの下に新しい `css` サブフォルダを作成します。 
2. `css` サブ フォルダの中に新しい `TS_LinearInputComponent.css` ファイルを作成します。 
3. 以下のスタイル コンテンツを `TS_LinearInputComponent.css` ファイルに追加します

    ```CSS
    .SampleNamespace\.TSLinearInputComponent input[type=range].linearslider {
      margin: 1px 0;
      background: transparent;
      -webkit-appearance: none;
      width: 100%;
      padding: 0;
      height: 24px;
      -webkit-tap-highlight-color: transparent
    }

    .SampleNamespace\.TSLinearInputComponent input[type=range].linearslider:focus {
      outline: none;
    }

    .SampleNamespace\.TSLinearInputComponent input[type=range].linearslider::-webkit-slider-runnable-track {
      background: #666;
      height: 2px;
      cursor: pointer
    }

    .SampleNamespace\.TSLinearInputComponent input[type=range].linearslider::-webkit-slider-thumb {
      background: #666;
      border: 0 solid #f00;
      height: 24px;
      width: 10px;
      border-radius: 48px;
      cursor: pointer;
      opacity: 1;
      -webkit-appearance: none;
      margin-top: -12px
    }

    .SampleNamespace\.TSLinearInputComponent input[type=range].linearslider::-moz-range-track {
      background: #666;
      height: 2px;
      cursor: pointer
    }

    .SampleNamespace\.TSLinearInputComponent input[type=range].linearslider::-moz-range-thumb {
      background: #666;
      border: 0 solid #f00;
      height: 24px;
      width: 10px;
      border-radius: 48px;
      cursor: pointer;
      opacity: 1;
      -webkit-appearance: none;
      margin-top: -12px
    }

    .SampleNamespace\.TSLinearInputComponent input[type=range].linearslider::-ms-track {
      background: #666;
      height: 2px;
      cursor: pointer
    }

    .SampleNamespace\.TSLinearInputComponent input[type=range].linearslider::-ms-thumb {
      background: #666;
      border: 0 solid #f00;
      height: 24px;
      width: 10px;
      border-radius: 48px;
      cursor: pointer;
      opacity: 1;
      -webkit-appearance: none;
    }
    ```

5. `TS_LinearInputComponent.css` ファイルを保存します。
6. `ControlManifest.Input.xml` ファイルを編集して、 `CSS` リソース ファイルをリソース要素内に追加します。
 
    ```XML
    <resources> 
      <code path="index.ts" order="1"/> 
      <css path="css/TS_LinearInputComponent.css" order="1"/> 
    </resources> 
     ```
7. コマンド  を使ってコントロール プロジェクトを再構築します。 
   ```CLI
   npm run build
   ```
8. **./out/controls/TSLinearInputComponent** にあるビルド出力を調査して、**TS_LinearInputComponent.css** ファイルがコンパイル済みビルド生成物に含まれていることを確認します。 

## <a name="debugging-your-code-component"></a>コード コンポーネントのデバッグ

コード コンポーネント ロジックの実装が完了したら、次のコマンドを実行してデバッグ処理を開始します。 詳細: [コード コンポーネントのデバッグ](debugging-custom-controls.md)

```CLI
npm start
```

## <a name="packaging-your-code-components"></a>コード コンポーネントのパッケージ化

[ソリューション](https://docs.microsoft.com/dynamics365/customer-engagement/customize/solutions-overview) ファイルを作成してインポートするには、次の手順に従います。

1. **LinearComponent** フォルダー内の新しい フォルダー **ソリューション** 作成し、フォルダーに移動します。 
2. コマンドを使用して、**LinearComponent** フォルダに新しいソリューション プロジェクトを作成します。
 
    ```CLI
     pac solution init --publisher-name developer --publisher-prefix dev 
    ```

   > [!NOTE]
   > [publisher-name](https://docs.microsoft.com/powerapps/developer/common-data-service/reference/entities/publisher) と [publisher-prefix](https://docs.microsoft.com/powerapps/maker/common-data-service/change-solution-publisher-prefix) の値は環境に特化したものである必要があります。
 
3. 新しいソリューション プロジェクトを作成したら、その作成したコンポーネントが配置される場所を参照する必要があります。 コマンドを使用して参照を追加できます。

    ```CLI
     pac solution add-reference --path c:\users\LinearComponent
    ```

4. ソリューションプロジェクトから zip ファイルを生成するには、ソリューション プロジェクトのディレクトリ内に `cd` が必要で、以下のコマンドを使用してプロジェクトを構築する必要があります。 

    ```CLI
     msbuild /t:restore
    ```

5. 次の msbuild コマンドを再度実行します。
    ```CLI
     msbuild
    ```

    > [!NOTE]
    > **NuGet ターゲットおよび構成タスク** を確認してください。 有効にするには、次の手順を行います。
    > - **Visual Studio インストーラー** 開きます。
    > - VS 2017 の場合は、 **変更** をクリックします。
    > - **個別のコンポーネン** をクリックします。
    > - **コード ツール** の **NuGetターゲットとビルド タスク** を参照してください。

6. 生成されたソリューションの zip ファイルは `Solution\bin\debug` フォルダーにあります。
7. [zip ファイルの準備ができたら、ソリューションをCommon Data Service](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/customize/import-update-upgrade-solution) に Web ポータルを使用して手動でインポートする、または[組織に対する認証](import-custom-controls.md#authenticating-to-your-organization)と[デプロイ](import-custom-controls.md#deploying-code-components)セクションを参照して、PowerApps CLI コマンドを使用してインポートします。

## <a name="adding-code-components-in-model-driven-apps"></a>モデル駆動型のアプリのコード コンポーネントの追加

線形入力コンポーネントのようなコード コンポーネントを追加するには、トピック[エンティティおよびフィールドにコンポーネントを追加する](add-custom-controls-to-a-field-or-entity.md)で説明されている手順に従います。

## <a name="adding-code-components-to-a-canvas-app"></a>キャンバス アプリにコード コンポーネントを追加する

コード コンポーネントをキャンバス アプリに追加するには、このトピック[コード コンポーネントをキャンバス アプリに追加する](component-framework-for-canvas-apps.md#add-components-to-a-canvas-app)で説明されている手順を実行します。

### <a name="see-also"></a>関連項目

[サンプル コンポーネントをダウンロード](https://go.microsoft.com/fwlink/?linkid=2088525)<br/>
[既存の PowerApps Component Framework のコントロールを更新する](updating-existing-controls.md)<br/>
[PowerApps Component Framework API の参照](reference/index.md)<br/>
[PowerApps Component Framework の概要](overview.md)
