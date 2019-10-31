---
title: カスタム クエリストリング パラメーターが許可されるフォームの構成 (モデル駆動型アプリ) | Microsoft Docs
description: カスタム クエリ パラメーターが許可されるフォームの構成について説明します。 アプリケーション内で新しいレコードを作成するときは、これらのパラメーターを使用して既定値を設定します。
keywords: ''
ms.date: 10/31/2018
ms.service: powerapps
ms.custom:
  - ''
ms.topic: article
ms.assetid: 89287d32-0d16-8f7d-e0b6-8cc208212cff
author: JimDaly
ms.author: jdaly
manager: shilpas
ms.reviewer: null
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---

# <a name="configure-a-form-to-accept-custom-querystring-parameters"></a>カスタム クエリストリング パラメーターが許可されるフォームの構成

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/configure-form-accept-custom-querystring-parameters -->

クエリ文字列で Web ページに値を渡せることにはセキュリティ上の懸念があります。 モデル駆動アプリは、クエリ文字列として渡されたパラメータを、予想されるパラメータ名とデータ型のリストと常に突き合わせを行う、最良の実践モデルが適用されています。  
  
 モデル駆動アプリは、既定でクエリ文字列の所定のパラメーター セットをフォームに渡すことを許可します。 アプリケーション内で新しいレコードを作成するときは、これらのパラメーターを使用して既定値を設定します。 各パラメーターでは、属性の論理名への参照を含む標準の命名規則を使用する必要があります。 詳細については、「[フォームに渡すパラメーターを使用してフィールド値を設定する](set-field-values-using-parameters-passed-form.md)」を参照してください。  
  
 アプリケーションでカスタム クエリの文字列パラメーターをエンティティ フォームに渡すことがあります。 このトピックでは、特定のエンティティ フォームで受け付けられる特定のパラメーターの名前およびデータ型のセットを定義する方法を説明します。  
  
## <a name="define-allowed-query-string-parameters"></a>許可されるクエリ文字列パラメーターの定義  
 フォームに受け付けられるクエリ文字列パラメーターを指定する方法は 2 つあります。  
  
-   フォーム プロパティの編集  
  
-   フォーム XML の編集  
  
### <a name="edit-form-properties"></a>フォーム プロパティの編集  
 エンティティ フォームを編集するとき、**フォーム**グループの**ホーム**タブで、**フォームのプロパティ**をクリックします。 **フォームのプロパティ**ダイアログ ボックスで、**パラメーター**タブを選択します。  
  
 このタブで、フォームが許可する名前とデータ型を変更します。  
  
### <a name="edit-formxml"></a>FormXml の編集  
 エクスポートしたソリューション ファイル customizations.xml 内で、フッター要素の直後に `<formparameters>` 要素を追加します。 この `<formparameters>` 要素に `<querystringparameter>` 要素を追加して、許可するパラメーターを指定します。  
  
 以下に、`querystringparameter` 要素の属性である `name` と `type` を説明します。  
  
- **name**。 個々の名前属性に少なくとも 1 つの下線 ('\_') を含める必要があります。ただし、クエリ文字列のパラメーター名を下線で開始することはできません。 名前の先頭に "crm\_" を付けることもできません。 命名規則のとおり、ソリューション発行者のカスタマイズ接頭辞を使用することを強くお勧めします。 たとえば、"myISV_contact_specialvalue" は `querystringparameter` の name 属性として有効です。  
  
    > [!IMPORTANT]
    >  `querystringparameter` 要素名が一意でない場合、データ型の異なる別のパラメーター定義で上書きされることがあります。  
  
- **Type**。 データ型の値をパラメーター値と一致させてください。そうすれば、無効な値がパラメーターで渡されることはなくなります。 以下は、有効なデータ型です。  
  
    -   Boolean  
  
    -   日時  
  
    -   Double  
  
    -   EntityType  
  
    -   Integer  
  
    -   Long  
  
    -   PositiveInteger  
  
        > [!NOTE]
        >  PositiveInteger (有効な値の範囲に "0" を含む)  
  
    -   SafeString  
  
    -   UniqueId  
  
    -   UnsignedInt  
  
### <a name="see-also"></a>関連項目  
 [フォームに渡すパラメーターを使用してフィールド値を設定する](set-field-values-using-parameters-passed-form.md)   
 [URL を使用してフォームおよびビューを開く](open-forms-views-dialogs-reports-url.md)
