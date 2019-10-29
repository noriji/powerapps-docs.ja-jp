---
title: TypeScript を使用したコードコンポーネントの実装 |MicrosoftDocs
description: TypeScript を使用してコードコンポーネントを実装する方法
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.topic: index-page
ms.assetid: 18e88d702-3349-4022-a7d8-a9adf52cd34f
ms.author: nabuthuk
author: Nkrb
ms.openlocfilehash: 669bf03d7869d6fd625288a65a305a3a458cfde4
ms.sourcegitcommit: 7c1e70e94d75140955518349e6f9130ce3fd094e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/29/2019
ms.locfileid: "73025752"
---
# <a name="implement-components-using-typescript"></a>TypeScript を使用してコンポーネントを実装する

このトピックでは、PowerApps CLI を使用して TypeScript で新しいコードコンポーネントを作成する手順について説明します。 このチュートリアルでは、ユーザーがフィールドに値を入力する代わりに、視覚スライダーを使用して数値を変更できるようにするサンプルの線形コードコンポーネントを作成します。 

コードコンポーネントをビルドするために必要な成果物は次のとおりです。

1. [新しいコンポーネントプロジェクトを作成する](#creating-a-new-component-project)
2. [実装 (マニフェストを)](#implementing-manifest)
3. [TypeScript を使用してコンポーネントロジックを実装する](#implementing-component-logic)
4. [コードコンポーネントにスタイルを追加する](#adding-style-to-the-code-component)
5. [パッケージ化 (コードコンポーネントを)](#packaging-your-code-components)

## <a name="creating-a-new-component-project"></a>新しいコンポーネントプロジェクトの作成

新しいプロジェクトを作成するには:

1. **VS 2017 ウィンドウの開発者コマンドプロンプト**を開きます。
1. 次のコマンドを使用して、プロジェクト用の新しいフォルダーを作成します。 
    ```CLI
    mkdir LinearComponent
    ```

1. コマンド `cd LinearComponent`を使用して、コンポーネントフォルダーにアクセスします。 
   
1. コマンドを使用して基本パラメーターを渡すことによって、新しいコンポーネントプロジェクトを作成します。

   ```CLI
    pac pcf init --namespace SampleNamespace --name TSLinearInputComponent --template field
    ``` 

1. コマンド `npm install` を使用して、プロジェクトビルドツールをインストールします。 
1. プロジェクトフォルダーを任意の開発者環境で開き、コードコンポーネントの開発を開始します。 `C:\Users\<your name>\Documents\<My_code_Component>` します。 最も簡単に開始するには、`C:\Users\<your name>\Documents\<My_code_Component>` ディレクトリにあるコマンドプロンプトから `code .` を実行します。 このコマンドにより、コンポーネントプロジェクトが Visual Studio Code で開きます。

## <a name="implementing-manifest"></a>実装 (マニフェストを)

マニフェストは、コードコンポーネントのメタデータを含む XML ファイルです。 また、コードコンポーネントの動作も定義します。 このチュートリアルでは、このマニフェストファイルを `<Your component Name>` サブフォルダーの下に作成します。 Visual Studio Code で `ControlManifest.Input.xml` ファイルを開くと、マニフェストファイルがいくつかのプロパティで事前に定義されていることがわかります。 詳細については、「 [Manifest](manifest-schema-reference/manifest.md)」を参照してください。

次に示すように、定義済みのマニフェストファイルに変更を加えます。

1. [コントロール](manifest-schema-reference/control.md)ノードは、コードコンポーネントの名前空間、バージョン、および表示名を定義します。 ここで、次に示すように、[コントロール](manifest-schema-reference/control.md)ノードの各プロパティを定義します。

   - **名前空間**: コードコンポーネントの名前空間。 
   - **コンストラクター**: コードコンポーネントのコンストラクター。
   - **バージョン**: コンポーネントのバージョン。 コンポーネントを更新するたびに、ランタイムの最新の変更を表示するにはバージョンを更新する必要があります。
   - **表示名-キー**: UI に表示されるコードコンポーネントの名前。
   - **description-name-key**: UI に表示されるコードコンポーネントの説明。
   - **コントロールの種類**: コードコンポーネントの型。 サポートされているのは、*標準*型のコードコンポーネントのみです。

     ```XML
      <?xml version="1.0" encoding="utf-8" ?>
      <manifest>
      <control namespace="SampleNameSpace" constructor="TSLinearInputComponent" version="1.0.0" display-name-key="Linear Input Component" description-key="Allows you to enter the numeric values using the visual slider." control-type="standard">
     ```

2. [プロパティ](manifest-schema-reference/property.md)ノードは、フィールドのデータ型の定義など、コードコンポーネントのプロパティを定義します。 プロパティノードは、`control` 要素の下に子要素として指定されます。 次に示すように、[プロパティ](manifest-schema-reference/property.md)ノードを定義します。

   - **name**: プロパティの名前。
   - **表示名-キー**: UI に表示されるプロパティの表示名。
   - **description-name-key**: UI に表示されるプロパティの説明。 
   - **-type-group**: 3 つ以上のデータ型フィールドを使用する場合は、 [-type-group](manifest-schema-reference/type-group.md)を使用します。 マニフェスト内の `property` 要素に、 [-type-group](manifest-schema-reference/type-group.md)要素を兄弟として追加します。 `of-type-group` には、コンポーネントの値を指定し、整数、通貨、浮動小数点、または10進値を含めることができます。
   - **使用法**:*バインド*と*入力*の2つのプロパティがあります。 バインドされたプロパティは、フィールドの値にのみバインドされます。 入力プロパティは、フィールドにバインドされているか、静的な値が許可されています。
   - **必須**: プロパティが必須かどうかを定義します。

     ```XML
      <property name="sliderValue" display-name-key="sliderValue_Display_Key" description-key="sliderValue_Desc_Key" of-type-group="numbers" usage="bound" required="true" />
      ```
3. [Resources](manifest-schema-reference/resources.md)ノードでは、コードコンポーネントの視覚化を定義します。 これには、コードコンポーネントの視覚化とスタイル設定を構築するすべてのリソースが含まれます。 [コード](manifest-schema-reference/code.md)は resources 要素の下に子要素として指定されます。 次に示すように、[リソース](manifest-schema-reference/resources.md)を定義します。

   - **code**: すべてのリソースファイルが配置されているパスを参照します。
 
      ```XML
      <resources>
        <code path="index.ts" order="1" />
        <css path="css/TS_LinearInputComponent.css" order="1" />
        </resources>
        ```
      マニフェストファイル全体は次のようになります。 

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

4. 変更内容を `ControlManifest.Input.xml` ファイルに保存します。
5. ここで、`TSLinearInputComponent` フォルダー内に新しいフォルダーを作成し、 **css**という名前を付けます。
6. CSS ファイルを作成し[て、コードコンポーネントにスタイルを追加](#adding-style-to-the-code-component)します。
7. コマンド `npm run build` を使用して、コンポーネントプロジェクトをビルドします。
8. ビルドによって、更新された TypeScript 型宣言ファイルが `TSLinearInputComponent/generated` フォルダーに生成されます。

## <a name="implementing-component-logic"></a>実装 (コンポーネントロジックを)

マニフェストファイルを実装した後の次の手順では、TypeScript を使用してコンポーネントロジックを実装します。 コンポーネントロジックは `index.ts` ファイル内に実装する必要があります。 Visual Studio Code で `index.ts` ファイルを開くと、4つの必須クラスが事前に定義されていることがわかります。 では、コードコンポーネントのロジックを実装してみましょう。 

1. 任意のコードエディターで `index.ts` ファイルを開きます。
2. 次のコードを使用して、`TSLinearInputComponent` クラスを更新します。

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
  // reference to the component container HTMLDivElement
  // This element contains all elements of our code component example
  private _container: HTMLDivElement;
  // reference to PowerApps component framework Context object
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
    // retrieving the latest value from the component and setting it to the HTML elements.
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

3. コマンド `npm run build` を使用して、プロジェクトをリビルドします。 
 
4. コンポーネントは、`out/controls/TSLinearInputComponent` フォルダーにコンパイルされます。 ビルド成果物には次のものが含まれます。

   - node.js –バンドルコンポーネントのソースコード。 
   - ControlManifest .xml – Common Data Service 組織にアップロードされる実際のコンポーネントマニフェストファイルです。

## <a name="adding-style-to-the-code-component"></a>コードコンポーネントへのスタイルの追加

開発者やアプリメーカーは、CSS を使用してコードコンポーネントを視覚的に表現するスタイルを定義できます。 CSS を使用すると、開発者はスタイル、色、レイアウト、フォントなどのコードコンポーネントの表現を記述できます。 線形入力コンポーネントの[init](reference/control/init.md)メソッドは、入力要素を作成し、class 属性を `linearslider` に設定します。 `linearslider` クラスのスタイルは、別の `CSS` ファイルで定義されています。 その他のカスタマイズをサポートするために、コードコンポーネントには `CSS` ファイルなどの追加コンポーネントリソースを含めることができます。

1. `TSLinearInputComponent` フォルダーの下に新しい `css` サブフォルダーを作成します。 
2. `css` サブフォルダー内に新しい `TS_LinearInputComponent.css` ファイルを作成します。 
3. 次のスタイルコンテンツを `TS_LinearInputComponent.css` ファイルに追加します。

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
6. `ControlManifest.Input.xml` ファイルを編集して、resources 要素内に `CSS` リソースファイルを含めます。
 
    ```XML
    <resources> 
      <code path="index.ts" order="1"/> 
      <css path="css/TS_LinearInputComponent.css" order="1"/> 
    </resources> 
     ```
7. 次のコマンドを使用して、プロジェクトをリビルドします。 
   ```CLI
   npm run build
   ```
8. **/Out/controls/TSLinearInputComponent**の下のビルド出力を調べ、 **TS_LinearInputComponent**ファイルがコンパイル済みのビルド成果物に含まれていることを確認します。 

## <a name="debugging-your-code-component"></a>コードコンポーネントのデバッグ

コードコンポーネントロジックの実装が完了したら、次のコマンドを実行してデバッグプロセスを開始します。 詳細情報:[デバッグコードコンポーネント](debugging-custom-controls.md)

```CLI
npm start
```

## <a name="packaging-your-code-components"></a>コードコンポーネントのパッケージ化

[ソリューション](https://docs.microsoft.com/powerapps/maker/common-data-service/solutions-overview)ファイルを作成してインポートするには、次の手順に従います。

1. **LinearComponent**フォルダー内に新しいフォルダー**ソリューション**を作成し、フォルダーに移動します。 
2. 次のコマンドを使用して、 **LinearComponent**フォルダーに新しいソリューションプロジェクトを作成します。
 
    ```CLI
     pac solution init --publisher-name developer --publisher-prefix dev 
    ```

   > [!NOTE]
   > [発行者名](https://docs.microsoft.com/powerapps/developer/common-data-service/reference/entities/publisher)と[発行者のプレフィックス](https://docs.microsoft.com/powerapps/maker/common-data-service/change-solution-publisher-prefix)値は、環境によって一意である必要があります。
 
3. 新しいソリューションプロジェクトが作成されたら、作成したコンポーネントが配置されている場所を参照する必要があります。 次のコマンドを使用して、参照を追加できます。

    ```CLI
     pac solution add-reference --path c:\users\LinearComponent
    ```

4. ソリューションプロジェクトから zip ファイルを生成するには、ソリューションプロジェクトディレクトリに `cd` し、次のコマンドを使用してプロジェクトをビルドする必要があります。 

    ```CLI
     msbuild /t:restore
    ```

5. ここでも、次のコマンドを実行して msbuild を実行します。
    ```CLI
     msbuild
    ```

    > [!NOTE]
    > **ビルドタスク & NuGet ターゲット**がオンになっていることを確認します。 有効にするには:
    > - **Visual Studio インストーラー**を開きます。
    > - Visual Studio 2017 の場合は、 **[変更]** を選択します。
    > - **個々のコンポーネント**を選択します。
    > - **[コードツール]** で、 **[NuGet ターゲット & ビルドタスク]** をオンにします。

6. 生成されたソリューション zip ファイルは、`Solution\bin\debug` フォルダーにあります。
7. Zip ファイルの準備ができたら、web ポータルを使用して[ソリューションを Common Data Service に](https://docs.microsoft.com/powerapps/maker/common-data-service/import-update-export-solutions)手動でインポートします。また、PowerApps CLI コマンドを使用してインポートするには、「[組織への認証](import-custom-controls.md#authenticating-to-your-organization)」と「[デプロイ](import-custom-controls.md#deploying-code-components)」セクションを参照してください。

## <a name="adding-code-components-in-model-driven-apps"></a>モデル駆動型アプリでのコードコンポーネントの追加

線形入力コンポーネントのようなコードコンポーネントを追加するには、「[フィールドとエンティティへのコンポーネントの追加](add-custom-controls-to-a-field-or-entity.md)」に記載されている手順に従います。

## <a name="adding-code-components-to-a-canvas-app"></a>キャンバスアプリへのコードコンポーネントの追加

キャンバスアプリにコードコンポーネントを追加するには、「[キャンバスアプリへのコードコンポーネントの追加](component-framework-for-canvas-apps.md#add-components-to-a-canvas-app)」の手順に従います。

### <a name="see-also"></a>関連項目

[サンプルコンポーネントのダウンロード](https://go.microsoft.com/fwlink/?linkid=2088525)<br/>
[既存の PowerApps コンポーネントフレームワークコンポーネントの更新](updating-existing-controls.md)<br/>
[PowerApps コンポーネントフレームワーク API リファレンス](reference/index.md)<br/>
[PowerApps コンポーネントフレームワークの概要](overview.md)
