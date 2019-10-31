---
title: リアクト フェイスパイル コンポーネント| Microsoft Docs
description: リアクトを使用したフェイスパイル コンポーネントの実装
ms.custom: ''
author: ghurlman
manager: kvivek
ms.date: 06/19/2019
ms.service: powerapps
ms.topic: article
ms.author: grhurl
ms.reviewer: nkrb
---

# <a name="implementing-the-facepile-component"></a>フェイスパイル コンポーネントの実装

このサンプルは、PowerApps component framework を利用してコンポーネントを作成するリアクトの使用方法を示します。  フェイスパイル サンプルコンポーネントは、リアクトと Office UI Fabric リアクト コンポーネントに基づいて実装されます。 このコードは、言及したサードパーティ製ライブラリのベスト プラクティスを明らかにしない場合があります。

> [!div class="mx-imgBorder"]
> ![リアクト フェイスパイル](../media/react-facepile.png "リアクト フェイスパイル")

## <a name="available-for"></a>以下に使用できます 

モデル駆動型アプリとキャンバス アプリ (実験的プレビュー) 


> [!IMPORTANT]
> PowerApps ホスト アプリケーションは、リアクト上で機能しますが、バンドルするリアクトのバージョンはホストバージョンとは通信せず、そのバージョンにも依存しません。 リアクトの新規コピー (または自分のコンポーネントでバンドルしたサードパーティ ライブラリ) は、そのコントロールのすべてのインスタンスのホストページに読み込まれます。そのため、コンポーネントを追加する際に、どの程度の大きさのページを作成するかに注意してください。 この問題に対するソリューションは将来のリリースに含まれます。

## <a name="manifest"></a>マニフェスト

```XML
<?xml version="1.0" encoding="utf-8" ?>
<manifest>
  <control namespace="SampleControls" constructor="ReactStandardControl" version="0.0.1" display-name-key="ReactStandardControl_Display_Key" description-key="ReactStandardControl_Desc_Key" control-type="standard">
    <!-- property node identifies a specific, configurable piece of data that the control expects from CDS -->
    <property name="numberOfFaces" display-name-key="numberOfFaces" description-key="numberOfFaces" of-type="Whole.None" usage="bound" required="false" />
    <resources>
      <css path="css/ReactStandardControl.css" order="1" />
      <code path="index.ts" order="2"/>
    </resources>
  </control>
</manifest>
```

## <a name="overview"></a>概要

このサンプルは、サードパーティ製ライブラリに依存関係を追加する方法の例を示し、リアクトのために Office UI Fabric コンポーネントを活用する方法と PowerApps component framework とリアクト状態モデル間で双方向のデータ バインディングを実行する方法を紹介します。

コンポーネントサンプルは 3 つの Office UI Fabric コンポーネントから構成されます: フェイスパイル、スライダー、チェックボックスとドロップダウンメニューです。 スライダーを移動すると、フェイスパイルのフェイスの数が変わります。 チェックボックス コンポーネントは、フェイスのフェードインやアウト、あるいは単に表示や非表示をコントロールし、ドロップダウンリストのオプションはフェイスのサイズをコントロールします。 値が設定されていない場合、フェイス番号は 3 に既定で設定されます。

- コンポーネントが読み込まれると、スライダーはバインド属性値に設定されます。 `context.parameters.[property_name].attributes` プロパティは関連するメタデータを含みます。
- イベント ハンドラーは、リアクト コンポーネントのプロップ内を通過されます。これにより、リアクト コンポーネントは値が変更されたホスト PowerApps component framework コントロールを通知できます。 イベント ハンドラーは、 **notifyOutputEvents** メソッドへの呼び出しが必要かどうかを判断します。
- スライダーをスライドさせると、リアクトはバインド値を更新し、イベントハンドラーに応答しますバインド値を更新して、渡されたイベントハンドラーを呼び出します。 このハンドラー内では、呼び出しが **notifyOutputEvents** メソッドに実行されると、コントロールの [getOutputs](../reference/control/getoutputs.md) メソッドが非同期的に呼び出され、 PowerApps component framework に流れます。 
- フレームワーク ホストはバインド属性値を更新し、更新された値は [updateView](../reference/control/updateview.md) メソッドをトリガーするコンポーネントへと流れます。 その後コントロールは新しい値を持つリアクト コンポーネントを再表示します。


## <a name="code"></a>Code

```TypeScript
import { IInputs, IOutputs } from "./generated/ManifestTypes";
import * as React from "react";
import * as ReactDOM from "react-dom";
import { FacepileBasicExample, IFacepileBasicExampleProps } from "./Facepile";

export class ReactStandardControl
  implements ComponentFramework.StandardControl<IInputs, IOutputs> {
  // Reference to the notifyOutputChanged method
  private notifyOutputChanged: () => void;
  // Reference to the container div
  private theContainer: HTMLDivElement;
  // Reference to the React props, prepopulated with a bound event handler
  private props: IFacepileBasicExampleProps = {
    numberFacesChanged: this.numberFacesChanged.bind(this)
  };

  /**
   * Empty constructor.
   */
  constructor() {}

  /**
   * Used to initialize the control instance. Controls can kick off remote server calls and other initialization actions here.
   * Data-set values are not initialized here, use updateView.
   * @param context The entire property bag available to control via Context Object; It contains values as set up by the customizer mapped to property names defined in the manifest, as well as utility functions.
   * @param notifyOutputChanged A callback method to alert the framework that the control has new outputs ready to be retrieved asynchronously.
   * @param state A piece of data that persists in one session for a single user. Can be set at any point in a controls life cycle by calling 'setControlState' in the Mode interface.
   * @param container If a control is marked control-type='starndard', it will receive an empty div element within which it can render its content.
   */
  public init(
    context: ComponentFramework.Context<IInputs>,
    notifyOutputChanged: () => void,
    state: ComponentFramework.Dictionary,
    container: HTMLDivElement
  ) {
    this.notifyOutputChanged = notifyOutputChanged;
    this.props.numberOfFaces = context.parameters.numberOfFaces.raw || 3;
    this.theContainer = container;
  }

  /**
   * Called when any value in the property bag has changed. This includes field values, data-sets, global values such as container height and width, offline status, control metadata values such as label, visible, etc.
   * @param context The entire property bag available to control via Context Object; It contains values as set up by the customizer mapped to names defined in the manifest, as well as utility functions
   */
  public updateView(context: ComponentFramework.Context<IInputs>): void {
    if (context.updatedProperties.includes("numberOfFaces"))
      this.props.numberOfFaces = context.parameters.numberOfFaces.raw || 3;

    // Render the React component into the div container
    ReactDOM.render(
      // Create the React component
      React.createElement(
        FacepileBasicExample, // the class type of the React component found in Facepile.tsx
        this.props
      ),
      this.theContainer
    );
  }

  /**
   * Called by the React component when it detects a change in the number of faces shown
   * @param newValue The newly detected number of faces
   */
  private numberFacesChanged(newValue: number) {
    // only update if the number of faces has truly changed
    if (this.props.numberOfFaces !== newValue) {
      this.props.numberOfFaces = newValue;
      this.notifyOutputChanged();
    }
  }

  /**
   * It is called by the framework prior to a control receiving new data.
   * @returns an object based on nomenclature defined in manifest, expecting object[s] for property marked as “bound” or “output”
   */
  public getOutputs(): IOutputs {
    return {
      numberOfFaces: this.props.numberOfFaces
    };
  }

  /**
   * Called when the control is to be removed from the DOM tree. Controls should use this call for cleanup.
   * i.e. cancelling any pending remote calls, removing listeners, etc.
   */
  public destroy(): void {
    ReactDOM.unmountComponentAtNode(this.theContainer);
  }
}

```

### <a name="facepiletsx"></a>Facepile.tsx

```TSX
import * as React from "react";
import { Checkbox } from "office-ui-fabric-react/lib/Checkbox";
import { Dropdown, IDropdownOption } from "office-ui-fabric-react/lib/Dropdown";
import { Facepile, IFacepilePersona, IFacepileProps, OverflowButtonType } from "office-ui-fabric-react/lib/Facepile";
import { PersonaSize } from "office-ui-fabric-react/lib/Persona";
import { Slider } from "office-ui-fabric-react/lib/Slider";
import { facepilePersonas } from "./FacepileExampleData";
import { setIconOptions } from "office-ui-fabric-react/lib/Styling";

// Suppress office UI fabric icon warnings.
setIconOptions({
  disableWarnings: true,
});

export interface IFacepileBasicExampleProps {
  numberOfFaces?: number;
  numberFacesChanged?: (newValue: number) => void;
}

export interface IFacepileBasicExampleState extends React.ComponentState, IFacepileBasicExampleProps {
  personaSize: PersonaSize;
  imagesFadeIn: boolean;
}

export class FacepileBasicExample extends React.Component<IFacepileBasicExampleProps, IFacepileBasicExampleState> {
  constructor(props: IFacepileBasicExampleProps) {
    super(props);

    this.state = {
      numberOfFaces: props.numberOfFaces || 3,
      imagesFadeIn: true,
      personaSize: PersonaSize.size32
    };
  }

  public componentWillReceiveProps(newProps: IFacepileBasicExampleProps): void {
    this.setState(newProps);
  }

  public render(): JSX.Element {
    const { numberOfFaces, personaSize } = this.state;
    const facepileProps: IFacepileProps = {
      personaSize,
      personas: facepilePersonas,
      overflowButtonType: OverflowButtonType.descriptive,
      maxDisplayablePersonas: this.state.numberOfFaces,
      getPersonaProps: (persona: IFacepilePersona) => {
        return {
          imageShouldFadeIn: this.state.imagesFadeIn,
        };
      },
      ariaDescription: "To move through the items use left and right arrow keys.",
    };

    return (
      <div className={"msFacepileExample"}>
        <Facepile {...facepileProps} />
        <div className={"control"}>
          <Slider
            label="Number of Personas:"
            min={1}
            max={5}
            step={1}
            showValue={true}
            value={numberOfFaces}
            onChange={this.onChangePersonaNumber}
          />
          <Dropdown
            label="Persona Size:"
            selectedKey={this.state.personaSize}
            options={[
              { key: PersonaSize.size16, text: "16px" },
              { key: PersonaSize.size24, text: "24px" },
              { key: PersonaSize.size28, text: "28px" },
              { key: PersonaSize.size32, text: "32px" },
              { key: PersonaSize.size40, text: "40px" },
            ]}
            onChange={this.onChangePersonaSize}
          />
          <Checkbox
            className={"exampleCheckbox"}
            label="Fade In"
            checked={this.state.imagesFadeIn}
            onChange={this.onChangeFadeIn}
          />
        </div>
      </div>
    );
  }

  private onChangeFadeIn = (
    ev: React.FormEvent<HTMLElement | HTMLInputElement> | undefined,
    checked?: boolean
  ): void => {
    this.setState(
      (prevState: IFacepileBasicExampleState): IFacepileBasicExampleState => {
        prevState.imagesFadeIn = checked!;
        return prevState;
      }
    );
  };

  private onChangePersonaNumber = (value: number): void => {
    this.setState(
      (prevState: IFacepileBasicExampleState): IFacepileBasicExampleState => {
        prevState.numberOfFaces = value;
        return prevState;
      }
    );
    if (this.props.numberFacesChanged) {
      this.props.numberFacesChanged(value);
    }
  };

  private onChangePersonaSize = (event: React.FormEvent<HTMLDivElement>, value?: IDropdownOption): void => {
    this.setState(
      (prevState: IFacepileBasicExampleState): IFacepileBasicExampleState => {
        prevState.personaSize = value ? (value.key as PersonaSize) : PersonaSize.size32;
        return prevState;
      }
    );
  };
}
```

### <a name="facepileexampledatats"></a>FacepileExampleData.ts

```TypeScript
import * as React from 'react';
import { IFacepilePersona } from 'office-ui-fabric-react/lib/Facepile';
import { PersonaInitialsColor } from 'office-ui-fabric-react/lib/Persona';
import { TestImages } from './TestImages';

export const facepilePersonas: IFacepilePersona[] = [
  {
    imageUrl: TestImages.personaFemale,
    personaName: 'Annie Lindqvist',
    data: '50%'
  },
  {
    imageUrl: TestImages.personaMale,
    personaName: 'Aaron Reid',
    data: '$1,000'
  },
  {
    personaName: 'Alex Lundberg',
    data: '75%',
    onClick: (ev?: React.MouseEvent<HTMLElement>, persona?: IFacepilePersona) => {
      if (persona)
        alert('You clicked on ' + persona.personaName + '. Extra data: ' + persona.data);
    }
  },
  {
    personaName: 'Roko Kolar',
    data: '4 hrs'
  },
  {
    imageInitials: 'CB',
    personaName: 'Christian Bergqvist',
    initialsColor: PersonaInitialsColor.green,
    data: '25%'
  },
  {
    imageUrl: TestImages.personaFemale,
    imageInitials: 'VL',
    personaName: 'Valentina Lovric',
    initialsColor: PersonaInitialsColor.lightBlue,
    data: 'Emp1234',
    onClick: (ev?: React.MouseEvent<HTMLElement>, persona?: IFacepilePersona) => {
      if (persona)
        alert('You clicked on ' + persona.personaName + '. Extra data: ' + persona.data);
    }
  },
  {
    imageUrl: TestImages.personaMale,
    imageInitials: 'MS',
    personaName: 'Maor Sharett',
    initialsColor: PersonaInitialsColor.lightGreen
  },
  {
    imageUrl: TestImages.personaFemale,
    imageInitials: 'PV',
    personaName: 'Annie Lindqvist2',
    initialsColor: PersonaInitialsColor.lightPink
  },
  {
    imageUrl: TestImages.personaMale,
    imageInitials: 'AR',
    personaName: 'Aaron Reid2',
    initialsColor: PersonaInitialsColor.magenta,
    data: 'Emp1234',
    onClick: (ev?: React.MouseEvent<HTMLElement>, persona?: IFacepilePersona) => {
      if (persona)
        alert('You clicked on ' + persona.personaName + '. Extra data: ' + persona.data);
    }
  },
  {
    imageUrl: TestImages.personaMale,
    imageInitials: 'AL',
    personaName: 'Alex Lundberg2',
    initialsColor: PersonaInitialsColor.orange
  }

  // Trimmed for display; full file in the downloadable sample code
```

### <a name="testimagests"></a>TestImages.ts

```TypeScript
const baseProductionCdnUrl = 'https://static2.sharepointonline.com/files/fabric/office-ui-fabric-react-assets/';

export const TestImages = {
  choiceGroupBarUnselected: baseProductionCdnUrl + 'choicegroup-bar-unselected.png',
  choiceGroupBarSelected: baseProductionCdnUrl + 'choicegroup-bar-selected.png',
  choiceGroupPieUnselected: baseProductionCdnUrl + 'choicegroup-pie-unselected.png',
  choiceGroupPieSelected: baseProductionCdnUrl + 'choicegroup-pie-selected.png',
  documentPreview: baseProductionCdnUrl + 'document-preview.png',
  documentPreviewTwo: baseProductionCdnUrl + 'document-preview2.png',
  documentPreviewThree: baseProductionCdnUrl + 'document-preview3.png',
  iconOne: baseProductionCdnUrl + 'icon-one.png',
  iconPpt: baseProductionCdnUrl + 'icon-ppt.png',
  personaFemale: baseProductionCdnUrl + 'persona-female.png',
  personaMale: baseProductionCdnUrl + 'persona-male.png'
};
```

## <a name="resources"></a>リソース

### <a name="cssreactstandardcontrolcss"></a>css/ReactStandardControl.css

```css
.msFacepileExample {
  max-width: 300px;
}

.msFacepileExample .control {
  padding-top: 20px;
}

.msFacepileExample .ms-Dropdown-container,
.msFacepileExample .ms-Slider {
  margin: 10px 0 10px 0;
}

.msFacepileExample .ms-Dropdown-container .ms-Label {
  padding-top: 0;
}

.msFacepileExample .ms-Checkbox {
  padding-top: 15px;
}

.exampleCheckbox {
  margin: 10px 0;
}

.exampleLabel {
  margin: 10px 0;
}
```

### <a name="related-topics"></a>関連トピック

[PowerApps Component Framework のマニフェスト スキーマの参照](../manifest-schema-reference/index.md)<br />
[PowerApps Component Framework API の参照](../reference/index.md)<br />
[PowerApps Component Framework の概要](../overview.md)
