---
title: 'Web バーコード-スキャナーコントロール: リファレンス |Microsoft Docs'
description: プロパティと例を含む、バーコードスキャナーコントロールに関する情報
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
ms.openlocfilehash: e80f34917bba942f85e141c382cf3b1caa5e6d44
ms.sourcegitcommit: 8e42a5996799d9831f8c5a52b0b051a6088d9ce7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/06/2019
ms.locfileid: "73650751"
---
# <a name="web-barcode-scanner-control-experimental-in-powerapps"></a>Web バーコード-PowerApps でのスキャナーコントロール (試験段階)

従来のバーコードスキャンコントロール。 web ブラウザーでのコードのスキャンに便利な場合があります。

## <a name="description"></a>Description

コントロールは、ユーザーがすべてのデバイスでバーコードをスキャンできるように、アプリにカメラフィードを表示します。 パフォーマンスが低下しているため、コントロールは廃止されています。また、モバイル **[バーコードスキャナー](control-new-barcode-scanner.md)** コントロールは、このコントロールを置き換えます。

## <a name="key-properties"></a>主要なプロパティ

**barcode scanner** – 複数のバーコード スキャナーを備えるデバイスで、アプリが使うバーコード スキャナーの数値 ID です。

## <a name="additional-properties"></a>その他のプロパティ

**[AccessibleLabel](properties-accessibility.md)** – スクリーン リーダー用のラベルです。

**[BorderColor](properties-color-border.md)** – コントロールの境界線の色です。

**[BorderStyle](properties-color-border.md)** – コントロールの境界線を **Solid** (実線)、**Dashed** (破線)、**Dotted** (点線)、**None** (なし) のいずれに指定します。

**[BorderThickness](properties-color-border.md)** – コントロールの境界線の太さです。

**[DisplayMode](properties-core.md)** – コントロールで、ユーザー入力を許可するか (**Edit**)、データの表示のみを許可するか (**View**)、許可しないか (**Disabled**) を設定します。

**[Height](properties-size-location.md)** – コントロールの上端と下端の距離です。

**ShowLiveBarcodeDetection** – バーコード検出の状態を示す視覚的な手がかりが表示されるかどうかを示します。 黄色の四角形は、検査されている領域を表します。 四角形内の緑色の線は、バーコードの識別に成功したことを示します。

**Stream** – **StreamRate** プロパティに基づいて自動的に更新された画像です。

**StreamRate** – **Stream** プロパティの画像を更新する頻度です (ミリ秒単位)。  この値の範囲は、100 (0.1 秒) から 3,600,000 (1 時間) です。

**Text** – スキャナーによって最後に識別されたバーコードの値。

**[Tooltip](properties-core.md)** – ポインターをコントロールに合わせたときに表示される説明テキストです。

**[Visible](properties-core.md)** – コントロールを表示するか非表示にするかを指定します。

**[Width](properties-size-location.md)** – コントロールの左端と右端の間の距離です。

**[X](properties-size-location.md)** – コントロールの左端とその親コンテナー (親コンテナーがない場合は画面) の左端間の距離です。

**[Y](properties-size-location.md)** – コントロールの上端とその親コンテナー (親コンテナーがない場合は画面) の上端間の距離です。

## <a name="related-functions"></a>関連する関数

[**Patch**( *DataSource*, *BaseRecord*, *ChangeRecord* )](../functions/function-patch.md)

## <a name="example"></a>例

### <a name="add-photos-to-an-image-gallery-control"></a>イメージ ギャラリー コントロールに写真を追加する

1. **バーコード スキャナー** コントロールを追加し、名前を **Mybarcode scanner** に設定します

    [コントロールの追加、命名、構成についてはこちらをご覧ください](../add-configure-controls.md)。

1. **ラベル**コントロールを追加し、その出力をバーコードスキャナーの**Text**プロパティに設定します。

1. **Barcodetype**プロパティで設定されている種類のバーコードをスキャンします。

    ラベルには、スキャンされたバーコードが表示されます。

## <a name="accessibility-guidelines"></a>アクセシビリティ ガイドライン

### <a name="video-alternatives"></a>ビデオの代替手段

* **[Text](properties-core.md)** をバーコード スキャナーの **Text** に設定した **[ラベル](control-text-box.md)** を追加することを検討してください。 バーコード スキャナーは識別されたバーコード値を表示しないので、上記のようにすると、視覚障碍を持つユーザーだけでなく、誰でもスキャナーにアクセスできるようになります。

### <a name="screen-reader-support"></a>スクリーン リーダーのサポート

* **[AccessibleLabel](properties-accessibility.md)** が存在する必要があります。

    > [!NOTE]
  > 新しいバーコードが検出されると、スクリーンリーダーによってアナウンスされます。 値は発表されません。 バーコードが表示されている限り、スクリーンリーダーは、同じバーコードがまだ識別されていることを5秒ごとにユーザーに通知します。
