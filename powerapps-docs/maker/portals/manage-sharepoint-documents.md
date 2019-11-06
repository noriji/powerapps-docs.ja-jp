---
title: ポータルで SharePoint ドキュメントを管理する |MicrosoftDocs
description: ポータルで SharePoint ドキュメントを管理する方法について説明します。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: f94dee983d5d2d9cedf417f2843a2c10c46b82c1
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2019
ms.locfileid: "73543326"
---
# <a name="manage-sharepoint-documents"></a>SharePoint ドキュメントの管理

Common Data Service は、Common Data Service 内から [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] のドキュメント管理機能を使用できるようにする [!INCLUDE[pn-microsoft-sharepoint-online](../../includes/pn-microsoft-sharepoint-online.md)] との統合をサポートしています。 PowerApps ポータルでは、ポータルでのエンティティフォームまたは web フォームに対する [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] との間でのドキュメントのアップロードと表示がサポートされるようになりました。 これにより、ポータルユーザーはポータルからドキュメントを表示、ダウンロード、追加、および削除できます。 ポータルユーザーは、サブフォルダーを作成してドキュメントを整理することもできます。

> [!NOTE]
> - ドキュメント管理は、[!INCLUDE[pn-microsoft-sharepoint-online](../../includes/pn-microsoft-sharepoint-online.md)]でのみ機能します。
> - ドキュメント管理は、サーバーベースの統合でサポートされています。

Common Data Service 内から [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] のドキュメント管理機能を使用するには、次の操作を行う必要があります。

1.  [Dynamics 365 でモデル駆動型アプリのドキュメント管理機能を有効にする](#step-1-enable-document-management-functionality-in-model-driven-apps-in-dynamics-365)

2.  [PowerApps ポータル管理センターから SharePoint 統合をセットアップする](#step-2-set-up-sharepoint-integration-from-powerapps-portals-admin-center)

3.  [エンティティのドキュメント管理を有効にする](#step-3-enable-document-management-for-entities)

4.  [PowerApps ドキュメントで適切なフォームを構成する](#step-4-configure-the-appropriate-form-to-display-documents)

5.  [適切なエンティティアクセス許可を作成し、適切な web ロールに割り当てます。](#step-5-create-appropriate-entity-permission-and-assign-it-to-the-appropriate-web-role)

## <a name="step-1-enable-document-management-functionality-in-model-driven-apps-in-dynamics-365"></a>手順 1: Dynamics 365 でモデル駆動型アプリのドキュメント管理機能を有効にする

サーバーベースの [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 統合を使用して、Dynamics 365 のモデル駆動型アプリでドキュメント管理機能を有効にする必要があります。 サーバーベースの [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 統合により、Dynamics 365 および [!INCLUDE[pn-microsoft-sharepoint-online](../../includes/pn-microsoft-sharepoint-online.md)] のモデル駆動型アプリは、サーバー間接続を実行できます。 既定の [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] サイトレコードは、ポータルで使用されます。 Dynamics 365 でモデル駆動型アプリのドキュメント管理機能を有効にする方法については、「 [dynamics 365 でモデル駆動型アプリを設定して SharePoint Online を使用する](https://docs.microsoft.com/power-platform/admin/set-up-dynamics-365-online-to-use-sharepoint-online)」を参照してください。

## <a name="step-2-set-up-sharepoint-integration-from-powerapps-portals-admin-center"></a>手順 2: PowerApps ポータル管理センターから SharePoint 統合をセットアップする

[!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)]のドキュメント管理機能を使用するには、PowerApps ポータル管理センターから [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 統合を有効にする必要があります。

> [!NOTE]
> この操作を実行するには、全体管理者である必要があります。

1. [PowerApps ポータル管理センター](admin/admin-overview.md)を開きます。

2.  **[!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 統合を有効に**する >  **[!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 統合のセットアップ**に関するページを参照してください。

    > [!div class=mx-imgBorder]
    > ![SharePoint 統合を有効にする](media/enable-sharepoint-integration.png "SharePoint 統合を有効にする")

3.  確認ウィンドウで **[有効化]** を選択します。 これにより、ポータルは [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)]と通信できるようになります。 [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 統合が有効になっている間、ポータルは再起動され、数分間利用できなくなります。 [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 統合が有効になっていると、メッセージが表示されます。

[!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 統合を有効にすると、次の操作が可能になります。

- **[!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 統合を無効**にする: ポータルとの [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 統合を無効にすることができます。 [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 統合が無効になっている間は、ポータルが再起動され、数分間利用できなくなります。 [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 統合が無効になると、メッセージが表示されます。

    > [!div class=mx-imgBorder]
    > ![SharePoint 統合を無効にする](media/disable-sharepoint-integration.png "SharePoint 統合を無効にする")

[!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 統合を有効または無効にすると、ポータルの [!INCLUDE[pn-azure-active-directory](../../includes/pn-azure-active-directory.md)] ([!INCLUDE[pn-azure-shortest](../../includes/pn-azure-shortest.md)] AD) アプリケーションが更新され、必要な [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] アクセス許可がそれぞれ追加または削除されます。 また、[!INCLUDE[pn-azure-shortest](../../includes/pn-azure-shortest.md)] AD アプリケーションで行われる変更の同意を得るためにもリダイレクトされます。 

> [!div class=mx-imgBorder]
> ![SharePoint 統合を無効にする](media/sharepoint-integration-consent.png "SharePoint 統合を無効にする")

同意しない場合:

- [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] の統合を有効または無効にすることは完了せず、エラーメッセージが表示されます。

- ポータルですぐに使用 [!INCLUDE[pn-azure-shortest](../../includes/pn-azure-shortest.md)] AD ログインが機能しません。 


## <a name="step-3-enable-document-management-for-entities"></a>手順 3: エンティティのドキュメント管理を有効にする
エンティティのドキュメント管理を有効にして、エンティティレコードに関連するドキュメントを [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)]に格納する必要があります。 エンティティのドキュメント管理を有効にする方法については、「[特定のエンティティに対する SharePoint ドキュメント管理の有効化](https://docs.microsoft.com/dynamics365/customer-engagement/admin/enable-sharepoint-document-management-specific-entities)」を参照してください。

## <a name="step-4-configure-the-appropriate-form-to-display-documents"></a>手順 4: ドキュメントを表示するための適切なフォームを構成する

### <a name="powerapps-customization"></a>PowerApps のカスタマイズ

ドキュメント管理機能を使用するフォームを特定します。 モデル駆動型アプリフォームエディターを使用してフォームを編集し、サブグリッドを追加する必要があります。 サブグリッドによってフォームにセクションが追加され、ポータル内からドキュメントを操作できるようになります。 この機能を使用するには、サブグリッドで次のプロパティを設定する必要があります。

- **[データソース]** で、 **[エンティティ]** ボックスの一覧から **[ドキュメントの場所]** を選択します。

- **[データソース]** で、 **[既定のビュー]** の一覧から **[アクティブなドキュメントの場所]** を選択します。

要件に従って、名前とラベルを指定できます。 サブグリッドを追加して構成したら、フォームを保存してパブリッシュします。

> [!NOTE]
> フォームを編集するエンティティに対してドキュメント管理を有効にする必要があります。 詳細情報:[エンティティのドキュメント管理を有効にする](#step-3-enable-document-management-for-entities)

### <a name="powerapps-portals-configuration"></a>PowerApps ポータルの構成

エンティティフォームまたは web フォームに必要な標準の構成とは別に、ドキュメント管理を有効にするには、次のプロパティを設定する必要があります。

- [**エンティティ名**と**フォーム名**]: 前の手順でカスタマイズしたエンティティとフォーム名をそれぞれ入力します。

- フォームの [**エンティティのアクセス許可を有効**にする] チェックボックスをオンにして、ユーザーがドキュメントを閲覧できるようにします。

- ドキュメントのアップロードを許可するには、**モード**を **[編集]** に設定します。

> [!NOTE]
> ドキュメントのアップロードには、親エンティティレコードが存在する必要があります。 モードを挿入に設定すると、フォームが送信されるまで親エンティティレコードが作成されないため、ドキュメントのアップロードは機能しません。

## <a name="step-5-create-appropriate-entity-permission-and-assign-it-to-the-appropriate-web-role"></a>手順 5: 適切なエンティティアクセス許可を作成し、適切な web ロールに割り当てる

ドキュメントを表示およびアップロードするために必要なアクセス権を確立するには、2つのエンティティアクセス許可レコードが必要です。

- エンティティまたは web フォームのエンティティに対するアクセス許可: 
    - エンティティフォームまたは以前に構成した web フォームのエンティティとして**エンティティ名**を指定する**エンティティアクセス許可**レコードを作成します。 
    - フォームの目的の動作に適した**スコープ**とスコープの関係を選択します。 
    - ドキュメントへの読み取りアクセスを許可するには、**読み取り**と**追加の**特権を有効にし、必要に応じて、ドキュメントのアップロードを許可する**書き込み**特権を有効にします。 ここでは、次の手順によって設定されるため、ここでは**Child Entity Permissions**セクションを無視します。
- **親スコープ**が前のアクセス許可レコードを参照する**ドキュメントの場所**に対するアクセス許可: 
    - エンティティ**名**を**ドキュメントの場所**エンティティとして指定し、**スコープ**が**親**に設定されたエンティティ**アクセス許可**レコードを作成します。 
    - 前の手順で作成したエンティティアクセス許可レコードに対する [親エンティティ] アクセス許可を選択します。 
    - 特権 
        - ドキュメントへの読み取りアクセスを許可するための最小限の特権は、**読み取り**、**作成**、および**追加**です。 
        - ドキュメントのアップロードアクセスに対する**書き込み**特権を含めます。 
        - ドキュメントの削除を許可するには、 **Delete**を含めます。

> [!NOTE]
> ドキュメントの**場所**エンティティに対する対応する子エンティティのアクセス許可は、ドキュメントを表示する必要があるエンティティまたは web フォームのエンティティに存在する親エンティティのアクセス許可レコードのインスタンスごとに作成する必要があります。

## <a name="configure-file-upload-size"></a>ファイルのアップロードサイズを構成する

既定では、ファイルサイズは 10 MB に設定されています。 ただし、`SharePoint/MaxUploadSize`のサイト設定を使用して、ファイルサイズを最大 50 MB に構成できます。

## <a name="sample-configuration-to-enable-document-management-on-the-case-entity-form"></a>ケースエンティティフォームでドキュメント管理を有効にするためのサンプル構成

次の例では、前提条件として Dynamics 365 Customer Service アプリケーションを必要とするケースエンティティを使用した構成を示します。 このサンプルでは、ケースエンティティを使用しますが、上記の手順を説明するだけで、他のカスタムエンティティや、SharePoint でのドキュメントの管理をサポートする任意の Common Data Service エンティティに従うことができます。 

1.  [手順 1](#step-1-enable-document-management-functionality-in-model-driven-apps-in-dynamics-365) . で説明されている手順に従って、Dynamics 365 および [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)] 統合のモデル駆動型アプリのサーバーベースの構成が完了していることを確認します。

2.  [手順 2](#step-2-set-up-sharepoint-integration-from-powerapps-portals-admin-center) . の指示に従って、ポータルに [!INCLUDE[pn-sharepoint-short](../../includes/pn-sharepoint-short.md)]と統合するためのアクセス許可があることを確認します。 

3.  [手順 3](#step-3-enable-document-management-for-entities) . の指示に従って、ケースエンティティのドキュメント管理が有効になっていることを確認します。

4.  [手順 4.](#step-4-configure-the-appropriate-form-to-display-documents)の指示に従って、次の構成を行います。

    - Dynamics 365 カスタマイズでのモデル駆動型アプリ

        a. **設定** > **カスタマイズ** > **カスタマイズしてシステムをカスタマイズ**します。 

        b. 既定の**ソリューション**では、**ケース**エンティティ >**フォーム**にアクセスします。 
    
        c. フォームエディターで**Web-Edit ケース**を開きます。

         > [!div class=mx-imgBorder]
         > ![Web 編集ケースフォーム](media/web-edit-case-form.png "Web 編集ケースフォーム")
    
        d. フォームの **[作成日]** フィールドを選択し、 **[挿入]** タブで **[サブグリッド]** を選択します。

         > [!div class=mx-imgBorder]
         > ![Web 編集のケースフォームにサブグリッドを追加する](media/add-sub-grid.png "Web 編集のケースフォームにサブグリッドを追加する")
    
        e. **[プロパティの設定]** ダイアログボックスで、次のプロパティを設定し、[ **OK]** を選択します。

         - **名前**(任意の名前を指定できます): casedocuments 
    
         - **ラベル**(任意のラベル名を指定できます): Case ドキュメント 
      
         - **エンティティ**: ドキュメントの場所 
    
         - **既定のビュー**: アクティブなドキュメントの場所

         > [!div class=mx-imgBorder]
         > ![サブグリッドのプロパティ](media/sub-grid-properties.png "サブグリッドのプロパティ")

        f. フォームエディターで、 **[保存]** を選択し、 **[発行]** を選択します。

    - PowerApps ポータルの構成

        a. **ポータル** > **エンティティフォーム**にアクセスします。
    
        b. **カスタマーサービスを**検索して開きます。ケースエンティティフォームを編集します。
    
        c. を確認し、次のプロパティが設定されていることを確認します。
    
         - **エンティティ名**: Case (インシデント)
    
         - **フォーム名**: Web –ケースの編集
    
         - **モード**: 編集
    
         - **エンティティアクセス許可**: 有効
    
         > [!div class=mx-imgBorder]
         > ![カスタマーサービス-ケースフォームの編集](media/customer-service-edit-case-form.png "カスタマーサービス-ケースフォームの編集")
    
        d. フォームに変更を加えた場合は、 **[保存]** を選択します。

5. [手順 5](#step-5-create-appropriate-entity-permission-and-assign-it-to-the-appropriate-web-role
)に従って、エンティティのアクセス許可がユーザーに付与されていることを確認します。

   1. ユーザーに関連付けられている**Web ロール**レコードにアクセスします。 このサンプルでは、ユーザーが管理者 web ロールを持っていることを前提としています。

   2. **顧客サービスの名前 (contact が customer の場合)** によって、エンティティアクセス許可レコードが存在することを確認します。 

      > [!NOTE]
      > Web ロールにこのエンティティのアクセス許可が追加されていることを確認します。 ユーザーが既に管理者である場合は、上記のエンティティのアクセス許可を明示的に割り当てる必要はありません。

   3. 新しいエンティティアクセス許可を作成し、次の詳細を入力して、 **[保存]** を選択します。

    - **名前**(任意の名前を指定できます): カスタマーサービス関連のドキュメント

    - **エンティティ名**: ドキュメントの場所
        
    - **スコープ**: 親
        
    - **親エンティティのアクセス許可**: カスタマーサービス-contact が Customer の場合
        
    - **親リレーションシップ**: incident_SharePointDocumentLocations
        
    - **特権**: 読み取り、作成、追加、書き込み、削除

      > [!div class=mx-imgBorder]
      > ![Customer Service エンティティアクセス許可](media/customer-service-entity-permission.png "Customer Service エンティティアクセス許可")
  
   4. ポータルにサインインして、ドキュメント管理がケースエンティティに対して有効になっていることを確認します。

      a. **サポート**ページにアクセスします。

      > [!div class=mx-imgBorder]
      > ![ポータルのサポートページ](media/portal-support-page.png "ポータルのサポートページ")

      b. 一覧から既存のケースレコードをクリックします。 ページの**ケースドキュメント**セクションにアクセスし、ドキュメントリストが追加されていることを確認します。

      > [!div class=mx-imgBorder]
      > ![ケースドキュメント](media/case-document.png "ケースドキュメント")

