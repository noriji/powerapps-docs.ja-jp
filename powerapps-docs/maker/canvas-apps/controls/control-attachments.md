---
title: 'Attachments コントロール: リファレンス | Microsoft Docs'
description: 各種プロパティとサンプルを含む Attachments コントロールに関する情報
author: chmoncay
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.date: 04/23/2018
ms.author: chmoncay
ms.reviewer: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 5279f9368cdd832e84fba13faf8643cd7392d70b
ms.sourcegitcommit: 8e42a5996799d9831f8c5a52b0b051a6088d9ce7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/06/2019
ms.locfileid: "73650802"
---
# <a name="attachments-control-in-powerapps"></a>PowerApps の Attachments コントロール
ユーザーがデバイスにファイルをダウンロードしたり、SharePoint リストまたは Common Data Service エンティティからファイルをアップロードしたり削除したりできるようにするコントロール。

## <a name="limitations"></a>事項
添付ファイル コントロールには、次の制限があります。
1. 添付ファイルは、SharePoint リストおよび Common Data Service エンティティでサポートされています。

1. アップロードおよび削除機能は、フォーム内でのみ動作します。 添付コントロールは、編集モードのときは無効になり、フォーム内では表示されません。 ファイルの追加と削除を保存するには、アプリユーザーがフォームを保存する必要があります。 この制限のため、添付ファイルコントロールは **[挿入]** タブからは使用できませんが、SharePoint または Common Data Service フォームで添付ファイルフォームフィールドが有効になっている場合はフォームに表示されます。

1. ファイルをアップロードできるのは、10 MB 以下の場合だけです。  

## <a name="description"></a>Description
**添付**ファイルコントロールを使用すると、SharePoint リストまたは Common Data Service エンティティからファイルを開いたり、追加したり、削除したりできます。

## <a name="key-properties"></a>主要なプロパティ
**[Items](properties-core.md)** – ダウンロードできるファイルを記述するソースです。

**MaxAttachments** - コントロールが受け入れるファイルの最大数です。

**MaxAttachmentSize** – 新しい添付ファイルごとに許容される最大ファイル サイズ (MB) です。  現在、10 MB の制限があります。

**OnAttach** – ユーザーが新しい添付ファイルを追加したときのアプリの応答です。

**OnRemove** – ユーザーが既存の添付ファイルを削除したときのアプリの応答です。

**[OnSelect](properties-core.md)** – ユーザーが添付ファイルをクリックしたときのアプリの応答です。

## <a name="additional-properties"></a>その他のプロパティ
**[AccessibleLabel](properties-accessibility.md)** – スクリーン リーダー用のラベルです。 添付ファイルの目的を説明する必要があります。

**AddAttachmentText** – 新しい添付ファイルを追加するために使用するリンクのラベル テキストです。

**[BorderColor](properties-color-border.md)** – コントロールの境界線の色です。

**[BorderStyle](properties-color-border.md)** – コントロールの境界線を **Solid** (実線)、**Dashed** (破線)、**Dotted** (点線)、**None** (なし) のいずれに指定します。

**[BorderThickness](properties-color-border.md)** – コントロールの境界線の太さです。

**[DisplayMode](properties-core.md)** – コントロールで、ファイルの追加と削除を許可するか (**Edit**)、データの表示のみを許可するか (**View**)、許可しないか (**Disabled**) を設定します。

**[FocusedBorderColor](properties-color-border.md)** – コントロールにフォーカスがあるときのコントロールの境界線の色です。

**[FocusedBorderThickness](properties-color-border.md)** – コントロールにフォーカスがあるときのコントロールの境界線の太さです。

**[Height](properties-size-location.md)** – コントロールの上端と下端の距離です。

**MaxAttachmentsText** – コントロールに許容される最大数のファイルが含まれている場合に "ファイルの添付" リンクと置き換えられるテキストです。

**NoAttachmentsText** – 添付されているファイルが存在しないときにユーザーに表示する情報テキストです。

**[TabIndex](properties-accessibility.md)** – 他のコントロールに関連するキーボード ナビゲーションの順序です。

**[Visible](properties-core.md)** – コントロールを表示するか非表示にするかです。

**[Width](properties-size-location.md)** – コントロールの左端と右端の間の距離です。

**[X](properties-size-location.md)** – コントロールの左端とその親コンテナー (親コンテナーがない場合は画面) の左端間の距離です。

**[Y](properties-size-location.md)** – コントロールの上端とその親コンテナー (親コンテナーがない場合は画面) の上端間の距離です。


## <a name="example"></a>例
1. データ ソースとして SharePoint リストを使用してデータからアプリを作成します。 または、アプリにフォームを追加し、そのデータ ソースとして SharePoint リストを設定します。

2. 左側にあるツリー ビュー内の **Form** コントロールを選択します。

3. 右側の [オプション] パネルの [プロパティ] タブで **[データ]** をクリックします。

4. **[フィールド]** の下で、 **[添付ファイル]** フィールドを有効にします。

    SharePoint リストに関連付けられている添付ファイル フィールドが、フォームに表示されます。

[コントロールを追加して構成する方法について学習してください].(../add-configure-controls.md)。


## <a name="accessibility-guidelines"></a>アクセシビリティ ガイドライン
### <a name="color-contrast"></a>色のコントラスト
以下の間には適切な色のコントラストが必要です。
* **ItemColor** と **ItemFill**
* **ItemHoverColor** と **ItemHoverFill**
* **ItemPressedColor** と **ItemPressedFill**
* **AddedItemColor** と **AddedItemFill**
* **RemovedItemColor** と **RemovedItemFill**
* **ItemErrorColor** と **ItemErrorFill**
* **AddAttachmentColor** と **Fill**
* **MaxAttachmentsColor** と **Fill**
* **NoAttachmentsColor** と **Fill**

これは、[標準の色のコントラスト要件](../accessible-apps-color.md)に追加されるものです。

### <a name="screen-reader-support"></a>スクリーン リーダーのサポート
次のプロパティが存在する必要があります。
* **[AccessibleLabel](properties-accessibility.md)**
* **AddAttachmentsText**
* **MaxAttachmentsText**
* **NoAttachmentsText**

### <a name="keyboard-support"></a>キーボードのサポート
* **[TabIndex](properties-accessibility.md)** を 0 以上にして、キーボード ユーザーがそこに移動できるようにする必要があります。
* フォーカス インジケーターは明確に表示する必要があります。 これを実現するには **[FocusedBorderColor](properties-color-border.md)** と **[FocusedBorderThickness](properties-color-border.md)** を使用します。
