---
title: ポータルでカスタム JavaScript を使用する |MicrosoftDocs
description: ポータルでカスタム JavaScript をフォームに追加する手順
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 42e31fc2ecb18d4f26327f8ccbeabe034d7a1700
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2019
ms.locfileid: "73553649"
---
# <a name="add-custom-javascript"></a>カスタム JavaScript の追加

Web フォームステップレコードには、**カスタム javascript**という名前のフィールドが含まれています。このフィールドを使用すると、フォームのビジュアル表示または機能を拡張または変更するための javascript コードを格納できます。

JavaScript のカスタムブロックは、フォームの終了タグ要素の直前にページの下部に追加されます。

## <a name="form-fields"></a>フォームフィールド

エンティティフィールドの HTML 入力 ID は、属性の論理名に設定されます。 これにより、 [jQuery](https://jquery.com/)を使用して、フィールドの選択、値の設定、またはその他のクライアント側の操作を簡単に行うことができます。  

```JavaScript
$(document).ready(function() {
   $("#address1_stateorprovince").val("Saskatchewan");
});
```

## <a name="additional-client-side-field-validation"></a>追加のクライアント側フィールドの検証
場合によっては、フォームのフィールドの検証のカスタマイズが必要になることがあります。 次の例は、カスタム検証を追加する方法を示しています。 この例では、優先する contact メソッドの他のフィールドが Email に設定されている場合にのみ、電子メールを指定するようユーザーに強制します。

> [!NOTE]
> クライアント側のフィールドの検証は、サブグリッドではサポートされていません。

```JavaScript
if (window.jQuery) {
   (function ($) {
      $(document).ready(function () {
         if (typeof (Page_Validators) == 'undefined') return;
         // Create new validator
         var newValidator = document.createElement('span');
         newValidator.style.display = "none";
         newValidator.id = "emailaddress1Validator";
         newValidator.controltovalidate = "emailaddress1";
         newValidator.errormessage = "<a href='#emailaddress1_label'>Email is a required field.</a>";
         newValidator.validationGroup = ""; // Set this if you have set ValidationGroup on the form
         newValidator.initialvalue = "";
         newValidator.evaluationfunction = function () {
            var contactMethod = $("#preferredcontactmethodcode").val();
            if (contactMethod != 2) return true; // check if contact method is not 'Email'.
            // only require email address if preferred contact method is email.
            var value = $("#emailaddress1").val();
            if (value == null || value == "") {
            return false;
            } else {
               return true;
            }
         };
 
         // Add the new validator to the page validators array:
         Page_Validators.push(newValidator);
 
         // Wire-up the click event handler of the validation summary link
         $("a[href='#emailaddress1_label']").on("click", function () { scrollToAndFocus('emailaddress1_label','emailaddress1'); });
      });
   }(window.jQuery));
}
```

## <a name="general-validation"></a>一般的な検証

[**次**の/の**送信**] ボタンをクリックすると、 **webformclientvalidate**という名前の関数が実行されます。 このメソッドを拡張して、カスタム検証ロジックを追加できます。

```JavaScript
if (window.jQuery) {
   (function ($) {
      if (typeof (webFormClientValidate) != 'undefined') {
         var originalValidationFunction = webFormClientValidate;
         if (originalValidationFunction && typeof (originalValidationFunction) == "function") {
            webFormClientValidate = function() {
               originalValidationFunction.apply(this, arguments);
               // do your custom validation here
               // return false; // to prevent the form submit you need to return false
               // end custom validation.
               return true;
            };
         }
      }
   }(window.jQuery));
}
```
### <a name="see-also"></a>関連項目

[ポータルの構成](configure-portal.md)  
[エンティティフォームの定義](entity-forms.md)  
[ポータルの Web フォームの手順](web-form-steps.md)  
[フォームの読み込み/読み込みタブのステップの種類](load-form-step.md)  
[リダイレクトステップの種類](add-redirect-step.md)  
[条件付きステップの種類](add-conditional-step.md)
