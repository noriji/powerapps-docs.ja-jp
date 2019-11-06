---
title: 'カメラ コントロール: リファレンス | Microsoft Docs'
description: 各種プロパティとサンプルを含むカメラ コントロールに関する情報
author: chmoncay
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.date: 10/25/2016
ms.author: chmoncay
ms.reviewer: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 14f802a899171dce052c8975f9fc63b07e448afc
ms.sourcegitcommit: 8e42a5996799d9831f8c5a52b0b051a6088d9ce7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/06/2019
ms.locfileid: "73650718"
---
# <a name="camera-control-in-powerapps"></a>PowerApps のカメラ コントロール
ユーザーがデバイスのカメラを使って写真を撮影するために使用できるコントロールです。

## <a name="description"></a>Description
このコントロールを追加した場合、ユーザーは、アプリを実行している任意の場所から 1 枚以上の写真でデータ ソースを更新できます。

## <a name="key-properties"></a>主要なプロパティ
**Camera** – 複数のカメラを備えたデバイスでの、アプリが使用するカメラの数値 ID です。

## <a name="additional-properties"></a>その他のプロパティ
**[AccessibleLabel](properties-accessibility.md)** – スクリーン リーダー用のラベルです。 写真撮影の目的を説明する必要があります。

**[BorderColor](properties-color-border.md)** – コントロールの境界線の色です。

**[BorderStyle](properties-color-border.md)** – コントロールの境界線を **Solid** (実線)、**Dashed** (破線)、**Dotted** (点線)、**None** (なし) のいずれに指定します。

**[BorderThickness](properties-color-border.md)** – コントロールの境界線の太さです。

**Brightness** – ユーザーが画像で認識する可能性のある光の量を指定します。

**Contrast** – ユーザーが画像内の似た色をどれだけ容易に区別できるかを指定します。

**[DisplayMode](properties-core.md)** – コントロールで、ユーザー入力を許可するか (**Edit**)、データの表示のみを許可するか (**View**)、許可しないか (**Disabled**) を設定します。

**[FocusedBorderColor](properties-color-border.md)** – コントロールにフォーカスがあるときのコントロールの境界線の色です。

**[FocusedBorderThickness](properties-color-border.md)** – コントロールにフォーカスがあるときのコントロールの境界線の太さです。

**[Height](properties-size-location.md)** – コントロールの上端と下端の距離です。

**[OnSelect](properties-core.md)** – ユーザーがコントロールをタップまたはクリックした場合のアプリの反応を指定します。

**OnStream** – **Stream** プロパティが更新された場合のアプリの反応を指定します。

**Photo** – ユーザーが写真を撮影すると取得される画像です。

**Stream** – **StreamRate** プロパティに基づいて自動的に更新された画像です。

**StreamRate** – **Stream** プロパティの画像を更新する頻度です (ミリ秒単位)。  この値の範囲は、100 (0.1 秒) から 3,600,000 (1 時間) です。

**[TabIndex](properties-accessibility.md)** – 他のコントロールに関連するキーボード ナビゲーションの順序です。

**[Tooltip](properties-core.md)** – ポインターをコントロールに合わせたときに表示される説明テキストです。

**[Visible](properties-core.md)** – コントロールを表示するか非表示にするかを指定します。

**[Width](properties-size-location.md)** – コントロールの左端と右端の間の距離です。

**[X](properties-size-location.md)** – コントロールの左端とその親コンテナー (親コンテナーがない場合は画面) の左端間の距離です。

**[Y](properties-size-location.md)** – コントロールの上端とその親コンテナー (親コンテナーがない場合は画面) の上端間の距離です。

## <a name="related-functions"></a>関連する関数
[**Patch**( *DataSource*, *BaseRecord*, *ChangeRecord* )](../functions/function-patch.md)

## <a name="example"></a>例
### <a name="add-photos-to-an-image-gallery-control"></a>イメージ ギャラリー コントロールに写真を追加する
1. **Camera** コントロールを追加して **MyCamera** という名前を付け、その **[OnSelect](properties-core.md)** プロパティを次の数式に設定します。<br>
   **Collect(MyPix, MyCamera.Photo)**

    [コントロールの追加、命名、構成についてはこちらをご覧ください](../add-configure-controls.md)。

    **[Collect](../functions/function-clear-collect-clearcollect.md)** 関数または[その他の関数](../formula-reference.md)については各関連記事を参照してください。
2. F5 キーを押した後、**MyCamera** をクリックまたはタップして写真を撮影します。
3. **[垂直ギャラリー](control-gallery.md)** コントロールを追加してから、その **[イメージ](control-image.md)** コントロール、テンプレート、さらに **画像ギャラリー** コントロール自体のサイズを画面内に収まるように変更します。
4. **画像ギャラリー** コントロールの **[Items](properties-core.md)** プロパティを以下に設定します。<br>**MyPix**
5. ギャラリーで、**画像**コントロールの **[Image](properties-visual.md)** プロパティを次の式に設定します。<br>
   **ThisItem.Url**

    撮影した写真が**イメージ ギャラリー** コントロールに表示されます。
6. 必要な枚数の写真を撮影してから、Esc キーを押して既定のワークスペースに戻ります。
7. (省略可能) **イメージ ギャラリー** コントロール内の**イメージ** コントロールの **OnSelect** プロパティを **Remove(MyPix, ThisItem)** に設定し、F5 キーを押して、写真をクリックまたはタップして削除します。

**[SaveData](../functions/function-savedata-loaddata.md)** 関数を使用して写真をローカルに保存するか、 **[Patch](../functions/function-patch.md)** 関数を使用してデータ ソースを更新します。


## <a name="accessibility-guidelines"></a>アクセシビリティ ガイドライン
カメラのフィードを表示するだけでなく、カメラ コントロール全体も写真を撮るボタンとして機能します。 そのため、ボタンと同様のアクセシビリティの考慮事項があります。

### <a name="video-alternatives"></a>ビデオの代替手段
* 視覚障碍があるユーザー向けに、代替形式の入力を追加することを検討してください。 たとえば、 **[[画像の追加]](control-add-picture.md)** があると、ユーザーはデバイスから画像をアップロードできます。

### <a name="color-contrast"></a>色のコントラスト
以下の間には適切な色のコントラストが必要です。
* **[FocusedBorderColor](properties-color-border.md)** と外側の色

### <a name="screen-reader-support"></a>スクリーン リーダーのサポート
* **[AccessibleLabel](properties-accessibility.md)** が存在する必要があります。

### <a name="keyboard-support"></a>キーボードのサポート
* **[TabIndex](properties-accessibility.md)** を 0 以上にして、キーボード ユーザーがそこに移動できるようにする必要があります。
* フォーカス インジケーターは明確に表示する必要があります。 これを実現するには **[FocusedBorderColor](properties-color-border.md)** と **[FocusedBorderThickness](properties-color-border.md)** を使用します。
