---
title: フォームに渡すパラメーターを使用してフィールド値を設定する (モデル駆動型アプリ) | Microsoft Docs
description: ユーザーによって作成される新規のレコードの既定値を設定するには、そのフォームを開くために使われる URL 内に属性値を指定します。
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: KumarVivek
ms.author: kvivek
manager: shilpas
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="set-field-values-using-parameters-passed-to-a-form"></a>フォームに渡すパラメーターを使用してフィールド値を設定する

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/set-field-values-using-parameters-passed-form -->

ユーザーによって作成される新規のレコードの既定値を設定するには、そのフォームを開くために使われる URL 内に属性値を指定します。 既定で、これらの値はフォーム内に設定されますが、ユーザーがレコードを保存する前に変更することもできます。  
  
<a name="BKMK_PassingParameters"></a>   
## <a name="pass-parameters-to-set-field-record-values"></a>レコードのフィールド値を設定するパラメーターの受け渡し  
  
> [!NOTE]
>  `Xrm.Navigation.`[openForm](clientapi/reference/Xrm-Navigation/openForm.md) 関数を使用して、フォームにパラメーター値を渡してフィールドの値を設定できます。 例については、「[例: Xrm.Navigation.openForm で新しいウィンドウを開く](set-field-values-using-parameters-passed-form.md#BKMK_ExampleXrmNavigationOpentForm)」を参照してください。  
  
 URL アドレスを使用して新しいフォームを開くとき、フィールドの値を設定する引数を `extraqs` パラメーターに含めることができます。 次の要件を満たす必要があります。  
  
- `extraqs` パラメーターで受け渡すパラメーターをエンコードすること。 パラメーターのエンコードには [encodeURIComponent](https://msdn.microsoft.com/library/aeh9cef7\(VS.85\).aspx) を使用します。  
  
- クエリ文字列の引数の名前を該当するエンティティの属性の名前と一致させること。あるいは、それらの名前に属性の名前が含まれるようにすること。  
  
- 有効な値を引き渡すこと。  
  
- 値にスクリプトは使用できない。  
  
  無効なパラメーターまたは値を引き渡そうとするとエラーが発生します。  
  
- ブール値フィールドでは、`0` か `1` の整数値、または `true` か `false` のテキスト値を使用すること。  
  
- DateTime フィールドでは、日付のテキスト値を使用すること。  
  
<a name="BKMK_ExampleSetValueStringFields"></a>   

## <a name="example-set-the-value-for-string-fields"></a>例: 文字列フィールドの値を設定する  
 次のサンプルでは、新規の取引先企業レコードの**名前**フィールドに値 "New Account" を設定します。  
  
 `extraqs` パラメーターのエンコード前の値は "name=New Account" です。  
  
```  
/main.aspx?etn=account&extraqs=name%3DNew%20Account&pagetype=entityrecord  
```  
  
<a name="BKMK_SetLookupFieldValues"></a>   

## <a name="set-values-for-lookup-fields"></a>検索フィールドの値の設定  
 次の表に、5 種類の検索フィールドを示します。 検索フィールドの使用例については、「[例: 検索フィールドの値を設定する](set-field-values-using-parameters-passed-form.md#BKMK_setValueLookupfields)」および「[例: Xrm.Navigation.openForm で新しいウィンドウを開く](set-field-values-using-parameters-passed-form.md#BKMK_ExampleXrmNavigationOpentForm)」を参照してください。  
  
|検索の種類|内容|  
|-----------------|-----------------|  
|簡易検索|1 種類のエンティティに対する 1 つの参照を使用できます。|  
|顧客の検索|取引先企業または取引先担当者のレコードに対する単一の参照を使用できます。|  
|所有者の検索|チームまたはシステム ユーザーのレコードに対する単一の参照を使用できます。|  
|関係者リストの検索|複数のエンティティに対する複数の参照を使用できます。|  
|関連の検索|複数のエンティティに対する単一の参照を使用できます。|  
  
 クエリ文字列引数を使用してフォームに対する検索の値を設定するときは、次のガイドラインが適用されます。  
  
-   簡易検索の場合、検索に表示する値とテキストを設定する必要があります。 テキストの値を設定するときは、属性の名前を末尾に使用します。  
  
     その他の引数を使用しないでください。  
  
-   顧客および所有者の検索の場合、値と名前を設定する必要があります。設定方法は簡易検索の場合と同じです。 また、エンティティの種類を指定するときは、種類を表す値を末尾に使用する必要があります。 種類として使用できる値は、account、contact、systemuser、および team です。  
  
-   関係者リストまたは関連の検索には値を設定できません。  
  
<a name="BKMK_setValueLookupfields"></a>   

## <a name="example-set-the-value-for-lookup-fields"></a>例: 検索フィールドの値を設定する  
 検索フィールドの値を設定するには、データ値と名前値を使用し、顧客または所有者の検索の場合にのみ、各フィールドの種類値を指定します。 次のサンプルは "Mark Folkerts" という名前のユーザーに所有者フィールドを設定します。  
  
 `extraqs` パラメーターのエンコード前の値は "**ownerid**={B8C6E040-656E-DF11-B414-00155DB1891A}&**owneridname**=Mark Folkerts&**owneridtype**=systemuser" です。  
  
```  
/main.aspx?etn=lead&pagetype=entityrecord&extraqs=ownerid%3D%7bB8C6E040-656E-DF11-B414-00155DB1891A%7d%26owneridname%3DMark%20Folkerts%26owneridtype%3Dsystemuser  
```  
  
 次のサンプルでは、取引先責任者フィールドを “Yvonne McKay (sample)” という名前のユーザーに設定します。`extraqs` パラメーターのエンコード前の値は “**primarycontactid**={43b58571-eefa-e311-80c1-00155d2a68c4}&**primarycontactidname**=Yvonne McKay (sample)” です。  
  
```  
/main.aspx?etn=account&pagetype=entityrecord&extraqs=primarycontactid%3D%7B43b58571-eefa-e311-80c1-00155d2a68c4%7D%26primarycontactidname%3DYvonne%20McKay%20(sample)  
```  
  
> [!NOTE]
>  このような簡易検索の場合、種類の値を設定する必要はありません。  
  
<a name="BKMK_SetValueDateFields"></a>   

## <a name="example-set-the-value-for-date-fields"></a>例: 日付フィールドの値を設定する  
 次の例では、新しい営業案件の**予測クローズ日**フィールドを 2011 年 1 月 31 日に設定します。 `extraqs` パラメーターのエンコード前の値は "estimatedclosedate=01/31/11" です。  
  
```  
/main.aspx?etn=opportunity&extraqs=estimatedclosedate%3D01%2F31%2F11&pagetype=entityrecord  
```  
  
<a name="BKMK_SampleSEtValueOptionSetFields"></a>   

## <a name="example-set-the-value-for-option-set-fields"></a>例: オプション セット フィールドの値を設定する  
 **オプション セット**フィールドの値を設定するには、オプションに整数値を設定します。 次の例では、新しい取引先担当者レコードの値の**ロール**フィールドの値を "意思決定者" に設定します。  
  
 `extraqs` パラメーターのエンコード前の値は "accountrolecode=1" です。  
  
```  
/main.aspx?etn=contact&extraqs=accountrolecode%3D1&pagetype=entityrecord  
``` 

<a name="BKMK_SampleSEtValueMultiSelectOptionSetFields"></a> 
  
## <a name="example-set-the-value-for-multi-select-option-set-fields"></a>例: 複数選択オプション セット フィールドの値の設定

**複数選択オプション セット**フィールドの値を設定するには、フォームを開くために使用される URL にオプションの整数値を指定します。 たとえば、**Hobbies** フィールドのオプションを設定する場合、extraqs パラメーターのエンコード前の値は "hobbies=[1,3,4]" です。   

```  
/main.aspx?etn=contact&extraqs=hobbies%3D%5B1%2C3%2C4%5D&pagetype=entityrecord   
``` 
  
<a name="BKMK_ExampleXrmNavigationOpentForm"></a>   

## <a name="example-use-xrmnavigationopenform-to-open-a-new-window"></a>例: Xrm.Navigation.openForm で新しいウィンドウを開く  
 次の例では、いくつかのフィールドの既定値を設定します。これを見ると、`Xrm.Navigation`.[openForm](clientapi/reference/Xrm-Navigation/openForm.md) 関数の使用方法がわかります。 この例は、`window.open` メソッドを使用した前の例と同じです。  
  
```Javascript  
function OpenNewContact() {  
 var parameters = {};  
 //Set the Parent Customer field value to “Contoso”.  
 parameters["parentcustomerid"] = "2878282E-94D6-E111-9B1D-00155D9D700B";  
 parameters["parentcustomeridname"] = "Contoso";  
 parameters["parentcustomeridtype"] = "account";  
 //Set the Address Type to “Primary”.  
 parameters["address1_addresstypecode"] = "3";  
 //Set text in the Description field.  
 parameters["description"] = "Default values for this record were set programmatically.";  
 //Set Do not allow E-mails to "Do Not Allow".  
 parameters["donotemail"] = "1";  
  
 // Define the entity name to open the form  
 var entityFormOptions = {};
 entityFormOptions["entityName"] = "contact";

// Open the form
 Xrm.Navigation.openForm(entityFormOptions, parameters).then(
    function (success) {
        console.log(success);
    },
    function (error) {
        console.log(error);
    });  
}  
```  
  
<a name="BKMK_ExampleWindowOpen"></a>   

## <a name="example-use-windowopen-to-open-a-new-window"></a>例: window.open で新しいウィンドウを開く  
 次のサンプルでは、いくつかのフィールドの既定値を設定します。これを見ると、[encodeURIComponent](https://msdn.microsoft.com/library/aeh9cef7\(VS.85\).aspx) で `extraqs` パラメーターの値をエンコードする方法がわかります。 [window.open](https://msdn.microsoft.com/library/ms536651\(VS.85\).aspx) メソッドでは、開くウィンドウの機能を制御できます。  
  
```Javascript  
function OpenNewContact() {  
    //Set the Parent Customer field value to “Contoso”.  
    var extraqs = "parentcustomerid={F01F3F6D-896E-DF11-B414-00155DB1891A}";  
    extraqs += "&parentcustomeridname=Contoso";  
    extraqs += "&parentcustomeridtype=account";  
    //Set the Address Type to “Primary”.  
    extraqs += "&address1_addresstypecode=3";  
    //Set text in the Description field.  
    extraqs += "&description=Default values for this record were set programatically.";  
    //Set Do not allow E-mails to "Do Not Allow".  
    extraqs += "&donotemail=1";  
    //Set features for how the window will appear.  
    var features = "location=no,menubar=no,status=no,toolbar=no";  
    // Open the window.  
    window.open("/main.aspx?etn=contact&pagetype=entityrecord&extraqs=" +  
     encodeURIComponent(extraqs), "_blank", features, false);  
}  
```  
  
### <a name="see-also"></a>関連項目  

 [URL を使用してフォームおよびビューを開く](open-forms-views-dialogs-reports-url.md)   
 [openForm](clientapi/reference/Xrm-Navigation/openForm.md)  
 [カスタム クエリストリング パラメーターが許可されるフォームの構成](configure-form-accept-custom-querystring-parameters.md)
