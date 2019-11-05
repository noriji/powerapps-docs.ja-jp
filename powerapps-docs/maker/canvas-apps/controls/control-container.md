---
title: 'コンテナーコントロール: reference |Microsoft Docs'
description: プロパティと例を含むコンテナーコントロールに関する情報
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.component: canvas
ms.date: 9/20/2019
ms.author: emcoope
ms.reviewer: tapanm-msft
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 8456e82cfd2680fcbb722c8b4b2b5b32ef73dbde
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2019
ms.locfileid: "73540291"
---
# <a name="container-control-in-powerapps-experimental"></a>PowerApps のコンテナーコントロール (試験段階)
階層を作成する機能を提供します。

> [!IMPORTANT]
> これは試験的な機能です。 試験的な機能は大幅に変更されたり、いつでもまったく表示されなくなったりする可能性があります。
> 詳細については、「 [PowerApps の実験的およびプレビュー機能に](https://docs.microsoft.com/powerapps/maker/canvas-apps/working-with-experimental-preview)ついて」を参照してください。

## <a name="description"></a>Description
 コンテナーは、一連のコントロールを保持し、独自のプロパティを持つことができます。 

空のコンテナーを挿入してから、コントロールを追加し、サイズを変更し、移動し、非表示にし、その他の変更を加えることによって、コンテナーをカスタマイズすることができます。 また、さまざまなコントロールから開始し、それらを選択してコンテナーに追加することもできます。これを行うには、ツリービューのコンテキストメニューを使用するか、キャンバスを右クリックします。 

## <a name="properties"></a>プロパティ
**[BorderColor](properties-color-border.md)** – コントロールの境界線の色です。

**[BorderStyle](properties-color-border.md)** – コントロールの境界線を **Solid** (実線)、**Dashed** (破線)、**Dotted** (点線)、**None** (なし) のいずれに指定します。

**[BorderThickness](properties-color-border.md)** – コントロールの境界線の太さです。

**[Fill](properties-color-border.md)** – コントロールの背景色です。

**[Height](properties-size-location.md)** – コントロールの上端と下端の距離です。

**[Width](properties-size-location.md)** – コントロールの左端と右端の間の距離です。

**[Visible](properties-core.md)** – コントロールを表示するか非表示にするかを指定します。

**[X](properties-size-location.md)** – コントロールの左端とその親コンテナー (親コンテナーがない場合は画面) の左端間の距離です。 

**[Y](properties-size-location.md)** – コントロールの上端とその親コンテナー (親コンテナーがない場合は画面) の上端間の距離です。 


## <a name="known-limitations"></a>既知の制限

コンテナーは、キャンバスコンポーネントまたはフォーム内では使用できません。 

## <a name="frequently-asked-questions"></a>よく寄せられる質問

**コンテナーとグループの違いは何ですか。**
作成グループは、コントロールを移動したり、グループ内のコントロールの同様のプロパティを一括編集したりするために使用される軽量の概念です。 作成グループは、アプリのレイアウトには影響しません。 

このコンテナーコントロールは、事前試験段階で、強化されたグループとして名前が変更された作成グループの代替として出荷されました。 簡易作成グループと、追加のプロパティを持つ strutured container コントロールの両方に値があるため、コンテナーコントロールに名前が変更されました。 

