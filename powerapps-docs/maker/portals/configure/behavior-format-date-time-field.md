---
title: Common Data Service | の日付と時刻のフィールドの動作と形式MicrosoftDocs
description: ポータルで使用される日付と時刻のフィールドの動作と形式。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 785b5fa7def4a5b8e4964e888567d64643405708
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2019
ms.locfileid: "73553327"
---
# <a name="behavior-and-format-of-the-date-and-time-field"></a>日付と時刻フィールドの動作と形式

Common Data Service では、日付と時刻のデータ型は、多くのシステムエンティティフィールドで使用されます。 たとえば、マーケティングキャンペーンでアカウントが最後に使用された日時を表示したり、ケースがエスカレートされた日付と時刻を表示したりすることができます。 また、日付と時刻のフィールドを含むカスタムエンティティを作成することもできます。 フィールドが表す内容に応じて、次のいずれかのフィールド動作をポータルフォームとグリッドに対して選択できます。 
- **ユーザーローカル**: フィールド値は、ユーザーの現地時刻に表示され、現在のポータルの言語/ロケールに従って書式設定されます。 値は Common Data Service に UTC タイムゾーン形式で格納されます。 別のタイムゾーンに Common Data Service (または別のポータルユーザー) のユーザーがその値を表示すると、その値が独自のタイムゾーンに変換されていることがわかります。
- **日付のみ**: フィールド値には日付のみが含まれ、タイムゾーンの変換なしで表示されます。 値の時刻部分は常に 12:00 AM です。 1人のユーザーが入力した値は、異なるタイムゾーンの他のユーザーによって同じように表示されます (たとえば、誕生日)。
  
  > [!Note]
  > このフィールドの動作は、保存後に変更することはできません。
  
- **タイムゾーンに依存しない**: フィールド値には日付と時刻が含まれ、タイムゾーンの変換なしで表示されます。 1人のユーザーが入力した値は、異なるタイムゾーンの他のユーザーによっても表示されます。
  
  > [!Note]
  > このフィールドの動作は、保存後に変更することはできません。

次のサイト設定を作成して、ポータルで使用する既定の日付/時刻形式を上書きすることもできます。
- DateTime/DateFormat: ポータルで使用される日付形式。 
- DateTime/TimeFormat: ポータルで使用される時刻形式。 
- DateTime/DateTimeFormat: ポータルで使用される完全な日付と時刻の形式。

既定では、ポータルは、web サイトの言語設定で指定された標準の日付/時刻形式を使用します。
許容される日付/時刻形式は[ここで](https://docs.microsoft.com/dotnet/standard/base-types/custom-date-and-time-format-strings)指定します。
