---
title: 'オーディオとビデオのコントロール: リファレンス | Microsoft Docs'
description: プロパティや例など、オーディオとビデオのコントロールに関する情報です
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
ms.openlocfilehash: 3b8c5ea5ee2784bc1ab97d6943045cee8da6a52f
ms.sourcegitcommit: 8e42a5996799d9831f8c5a52b0b051a6088d9ce7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/06/2019
ms.locfileid: "73650783"
---
# <a name="audio-and-video-controls-in-powerapps"></a>PowerApps でのオーディオとビデオのコントロール
オーディオ ファイル、ビデオ ファイル、または YouTube のビデオを再生するコントロールです。

## <a name="description"></a>Description
**オーディオ** コントロールは、ファイルのサウンド クリップ、 **[マイク](control-microphone.md)** コントロールからの録音、またはビデオ ファイルのオーディオ トラックを再生します。

**ビデオ** コントロールは、ファイルから、または YouTube や Azure Media Services から、ビデオ クリップを再生します。  必要であれば、クローズド キャプションを表示するように指定できます。

## <a name="key-properties"></a>主要なプロパティ
**Loop** – オーディオまたはビデオ クリップを、再生終了と同時に先頭から自動的に再開するかどうかを指定します。

**Media** – オーディオまたはビデオ コントロールが再生するクリップの ID です。

**ShowControls** – オーディオ プレイヤーまたはビデオ プレイヤーに再生ボタンと音量スライダーなどを表示するかどうか、およびペン コントロールに描画、削除、クリアなどのアイコンを表示するかどうかを指定します。

## <a name="additional-properties"></a>その他のプロパティ
**[AccessibleLabel](properties-accessibility.md)** – スクリーン リーダー用のラベルです。 ビデオまたはオーディオ クリップのタイトルにする必要があります。

**AutoPause** – ユーザーが別の画面に移動した場合、オーディオまたはビデオ クリップを自動的に一時停止するかどうかを指定します。

**AutoStart** – ユーザーがオーディオまたはビデオ コントロールを含む画面に移動したときに、自動的にクリップの再生を開始するかどうかを指定します。

**[BorderColor](properties-color-border.md)** – コントロールの境界線の色です。

**[BorderStyle](properties-color-border.md)** – コントロールの境界線を **Solid** (実線)、**Dashed** (破線)、**Dotted** (点線)、**None** (なし) のいずれに指定します。

**[BorderThickness](properties-color-border.md)** – コントロールの境界線の太さです。

**ClosedCaptionsUrl** – ビデオ コントロールのみ。  WebVTT 形式のクローズド キャプションのファイルの URL です。  ビデオの URL と キャプションの URL は、どちらも HTTPS である必要があります。 ビデオとキャプションの両方のファイルをホストするサーバーでは、CORS が有効になっている必要があります。

**[DisplayMode](properties-core.md)** – コントロールで、ユーザー入力を許可するか (**Edit**)、データの表示のみを許可するか (**View**)、許可しないか (**Disabled**) を設定します。

**[Fill](properties-color-border.md)** – コントロールの背景色です。

**[FocusedBorderColor](properties-color-border.md)** – コントロールにフォーカスがあるときのコントロールの境界線の色です。

**[FocusedBorderThickness](properties-color-border.md)** – コントロールにフォーカスがあるときのコントロールの境界線の太さです。

**[Height](properties-size-location.md)** – コントロールの上端と下端の距離です。

**[Image](properties-visual.md)** – イメージ、オーディオ、マイクの各コントロールに表示される画像の名前です。

**[ImagePosition](properties-visual.md)** – 画面またはコントロールのサイズが画像と異なる場合の、画面またはコントロール内の画像の位置です (**Fill** (フィル)、**Fit** (サイズに合わせる)、**Stretch** (伸ばす)、**Tile** (タイル表示)、または **Center** (中央に表示))。

**OnEnd** – オーディオまたはビデオ クリップの再生が終了したときの、アプリの応答方法です。

**OnPause** – オーディオまたはビデオ コントロールが再生しているクリップをユーザーが一時停止したときの、アプリの応答方法です。

**OnStart** – ユーザーがマイク コントロールで録音を開始したときの、アプリの応答方法です。

**Paused** – メディア再生コントロールが現在一時停止している場合は *true*、それ以外の場合は *false* です。

**[Reset](properties-core.md)** – コントロールを既定値に戻すかどうかを指定します。

**Start** – オーディオまたはビデオ クリップを再生するかどうかを指定します。

**StartTime** – クリップの再生が開始するとき、オーディオまたはビデオ クリップの開始後の時刻です。

**Time** – メディア コントロールの現在位置です。

**[TabIndex](properties-accessibility.md)** – 他のコントロールに関連するキーボード ナビゲーションの順序です。

**[Tooltip](properties-core.md)** – ポインターをコントロールに合わせたときに表示される説明テキストです。

**[Visible](properties-core.md)** – コントロールを表示するか非表示にするかを指定します。

**[Width](properties-size-location.md)** – コントロールの左端と右端の間の距離です。

**[X](properties-size-location.md)** – コントロールの左端とその親コンテナー (親コンテナーがない場合は画面) の左端間の距離です。

**[Y](properties-size-location.md)** – コントロールの上端とその親コンテナー (親コンテナーがない場合は画面) の上端間の距離です。

## <a name="related-functions"></a>関連する関数
[**First**( *TableName* )](../functions/function-first-last.md)

## <a name="examples"></a>例
### <a name="play-an-audio-or-video-file"></a>オーディオまたはビデオ ファイルを再生する
1. **[ファイル]** メニューの **[メディア]** をクリックまたはタップし、 **[ビデオ]** または **[オーディオ]** をクリックまたはタップしてから、 **[参照]** をクリックまたはタップします。
2. 再生するファイルを探してクリックまたはタップし、 **[開く]** をクリックまたはタップします。
3. Esc キーを押して既定のワークスペースに戻り、**オーディオ**または**ビデオ** コントロールを追加して、**Media** プロパティを追加したファイルに設定します。

    [コントロールの追加および構成](../add-configure-controls.md)についてはこちらをご覧ください。
4. F5 キーを押し、追加したコントロールの再生ボタンをクリックまたはタップして、クリップを再生します。

    > [!TIP]
   > **ビデオ** コントロールの再生ボタンは、コントロールをポイントすると表示されます。
5. Esc キーを押して既定のワークスペースに戻ります。

### <a name="play-a-youtube-video"></a>YouTube のビデオを再生する
1. **ビデオ** コントロールを追加し、**Media** プロパティに、YouTube のビデオの URL を二重引用符で囲んで設定します。
2. F5 キーを押し、**ビデオ** コントロールの再生ボタンをクリックまたはタップして、クリップを再生します。
3. Esc キーを押して既定のワークスペースに戻ります。

### <a name="play-a-video-from-azure-media-services"></a>Azure Media Services からビデオを再生する
1. AMS でビデオが公開された後、マニフェストの URL をコピーします。 まだ行っていない場合は、サービスのストリーミング エンドポイントを開始します。
1. **ビデオ** コントロールを追加し、**Media** プロパティに、AMS のビデオの URL を二重引用符で囲んで設定します。
2. F5 キーを押し、**ビデオ** コントロールの再生ボタンをクリックまたはタップして、クリップを再生します。
3. Esc キーを押して既定のワークスペースに戻ります。


## <a name="accessibility-guidelines"></a>アクセシビリティ ガイドライン
### <a name="audio-and-video-alternatives"></a>オーディオおよびビデオの代替手段
* ユーザーが自分のペースでマルチメディアを視聴できるように、**ShowControls** を true にする必要があります。 これにより、ユーザーはビデオ プレーヤーでクローズド キャプションや全画面モードを切り替えることもできます。
* クローズド キャプションがビデオに対して提供されている必要があります。
  *  YouTube ビデオの場合は、YouTube から提供されている作成ツールを使ってキャプションを追加します。
  *  その他のビデオの場合は、WebVTT 形式でキャプションを作成し、アップロードして、**ClosedCaptionsUrl** に URL の場所を設定します。 いくつかの制限があります。 ビデオとキャプションをホストしているサーバーは、CORS が有効であり、HTTPS プロトコルでそれらを提供している必要があります。 Internet Explorer ではキャプションは機能しません。
* 次のいずれかの方法を使用して、オーディオまたはビデオのトランスクリプトを提供することを検討してください。
  1. **[ラベル](control-text-box.md)** にテキストを挿入し、マルチメディア プレーヤーの隣に配置します。 必要に応じて、テキストの表示を切り替える **[ボタン](control-button.md)** を作成します。
  2. 別の画面にテキストを配置します。 その画面に移動する **[ボタン](control-button.md)** を作成し、マルチメディア プレーヤーの隣にボタンを配置します。
  3. 説明が短い場合は、 **[AccessibleLabel](properties-accessibility.md)** に格納できます。

### <a name="color-contrast"></a>色のコントラスト
以下の間には適切な色のコントラストが必要です。
* **[FocusedBorderColor](properties-color-border.md)** と外側の色
* **[Image](properties-visual.md)** とマルチメディア プレーヤーのコントロール (該当する場合)
* **[Fill](properties-color-border.md)** とマルチメディア プレーヤーのコントロール (背景色を表示する場合)

ビデオ コンテンツに色のコントラストの問題がある場合は、クローズド キャプションまたはトランスクリプトを提供します。

### <a name="screen-reader-support"></a>スクリーン リーダーのサポート
* **[AccessibleLabel](properties-accessibility.md)** が存在する必要があります。

### <a name="keyboard-support"></a>キーボードのサポート
* **[TabIndex](properties-accessibility.md)** を 0 以上にして、キーボード ユーザーがそこに移動できるようにする必要があります。
* フォーカス インジケーターは明確に表示する必要があります。 これを実現するには **[FocusedBorderColor](properties-color-border.md)** と **[FocusedBorderThickness](properties-color-border.md)** を使用します。
* **AutoStart** は、キーボード ユーザーが再生をすばやく停止するのが難しい場合があるので、false にする必要があります。
