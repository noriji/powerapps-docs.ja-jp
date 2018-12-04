---
title: マルチ テナント型サーバー間認証を使用する (アプリ用 Common Data Service) | Microsoft Docs
description: アプリ用 Common Data Service でサーバー間認証のためにアプリケーション ユーザーを構成する方法について説明します。
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: paulliew
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="use-multi-tenant-server-to-server-authentication"></a>マルチ テナント型でのサーバー間認証の使用

これはもっとも一般的なシナリオであり、Microsoft AppSource で配布されるアプリでも使用されます。しかし Microsoft AppSource でアプリケーションを一覧表示せずにマルチテナント型を使用することもできます。  
  
アプリ用 CDS の組織は、それぞれが Azure Active Directory のテナントに関連付けられます。 Web アプリケーションまたはサービスには、独自の Azure AD テナントが登録されます。  
  
このシナリオではすべてのアプリ用 CDS テナントはアプリケーションがデータにアクセスする承認を付与した後、マルチテナント型アプリケーションを潜在的に使用できます。  
  
<a name="bkmk_Requirements"></a>   

## <a name="requirements"></a>要件  

 サーバー間の (S2S) 認証を使用するマルチテナント型アプリケーション テストを作成してテストするには次のものが必要です:  
  
- アプリケーションまたはサービスの公開に使用する Azure AD テナント。  
  
- 2 つのアプリ用 CDS サブスクリプション  
  
  -   1 つは、アプリケーションまたはサービスの公開に使用する Azure AD テナントに関連付けられている必要があります。  
  
  -   もう 1 つは、サブスクライバーがアプリケーションにアクセスする方法をテストするための試用版サブスクリプションです。  
  
<a name="bkmk_DevelopAndTest"></a>  
 
## <a name="overview-develop-and-test-your-application"></a>概要: アプリケーションの開発とテスト  

 作成するアプリケーションは、アプリケーションを公開する時に使用する Azure AD テナントを登録する必要があります。  
  
 高いレベルでは、プロセスは次のように構成されます:  
  
1. Azure AD テナントに登録されたマルチテナント型 Web アプリケーションを作成します。  
  
2. アプリ用 CDS テナントで登録されたアプリケーションに関連付けられるアプリケーション ユーザーを作成します。  
  
3. ユーザー定義のセキュリティ ロールを作成し、アプリ用 CDS テナントでアプリケーション ユーザーに割り当てます  
  
4. アプリ用 CDS テナントを使用してアプリケーションをテストします  
  
5. 個別のアプリ用 CDS テナントを使用してアプリケーションをテストします  
  
   このプロセスの完全な例については、「[チュートリアル: マルチ テナント型のサーバー間認証の使用](/dynamics365/customer-engagement/developer/walkthrough-multi-tenant-server-server-authentication)」を参照してください。  
  
<a name="bkmk_CreateAMultitenantWebApp"></a>
   
## <a name="create-a-multi-tenant-web-application-registered-with-your-azure-ad-tenant"></a>Azure AD テナントに登録されたマルチテナント型 Web アプリケーションを作成します 
 
 Azure AD を認証プロバイダーとして使用するマルチテナント型 Web アプリケーションまたはサービスを作成します。  
  
 これをどうやって行うのかは、このトピックの焦点ではありません。 これにアプローチして、要件や好みに合った選択をすることができるいくつかの方法があります。 詳細とサンプルについては、次のリンクを参照してください:  
  
- [Azure AD &amp; OpenID Connect を使用してマルチテナント型 SaaS Web アプリケーションを構築する](https://azure.microsoft.com/en-us/documentation/samples/active-directory-dotnet-webapp-multitenant-openidconnect/)  
  
- [Azure AD を使用して、Web API を呼び出すマルチテナント型 SaaS Web アプリケーションを構築します](https://azure.microsoft.com/en-us/documentation/samples/active-directory-webapp-webapi-multitenant-openidconnect-aspnetcore/)  
  
  Azure AD には、アプリケーションを登録するために次の値が必要です:  
  
|値|説明|  
|-----------|-----------------|  
|**アプリケーション ID URI**|アプリケーションの識別子です。 この値は認証中に Azure AD へ送信され、発信者がトークンを要求するアプリケーションを示します。 さらに、この値はトークンに含まれ、対象のターゲットであることがアプリケーションに認識されます。|  
|**返信 URL およびリダイレクト URI**|Web API または Web アプリケーションの場合、返信 URL は、認証が成功した場合、Azure AD がトークンを含む認証応答を送信する場所です。|  
|**クライアント ID**|アプリケーションの ID は、アプリケーションが登録されるときに Azure AD によって生成されます。 認証コードまたはトークンを要求した場合、認証中にクライアント ID とキーが Azure AD へ送信されます。|  
|**キー**|Azure AD に認証し、Web API を呼び出すときにクライアント ID と共に送信されるキー。|  
  
 アプリケーションが登録されると、登録されたアプリケーションの一意識別子である **Azure Active Directory オブジェクト ID** が割り当てられます。  
  
 Visual Studio を使用して新規に ASP.NET MVC アプリケーションを作成する場合、アプリケーションがマルチテナント機能をサポートするように指定するオプションがあります。 MVC アプリケーション用テンプレートには、どのような種類の認証が行われるかを指定するオプションがあります。 プロジェクトの作成時にプロジェクトのプロパティを設定することで、認証方法を選択するオプションがあります。 次の図で使用できるオプションを表示します:  
  
 ![ASP.NET MVC 変更認証ダイアログ](media/mvc-change-authentication-dialog.png "ASP.NET MVC 変更認証ダイアログ")  
  
 これらのオプションを使用してプロジェクトを構成すると、このシナリオをサポートする基本的なアプリケーションの [OWIN] ミドルウェアおよびスキャフォールディングを使用するよう構成されます。 いくつか基本的な変更を加えればアプリ用 CDS で動作するように調整することができます。 これは、「[チュートリアル: マルチ テナント型のサーバー間認証の使用](/dynamics365/customer-engagement/developer/walkthrough-multi-tenant-server-server-authentication)」で示されているアプローチです。  
  
 開発用アプリケーションを作成して登録するプロセスについては、[`http://localhost`] を **URL にサインオン**と**返答 URL** 値として使用し、公開前にアプリケーションをローカルでテストしてデバッグすることができます。 アプリの公開前にこれらの値を変更する必要があります。  
  
 アプリを登録する場合、`ClientSecret` としても呼ばれるキーを生成する必要があります。 これらのキーは 1 年、または 2 年間構成することができます。 アプリケーションのホストは、この値をパスワードのように扱う必要があり、期限が切れる前にキーの更新を管理する責任があります。 [Key Vault] を使用することができます。 詳細: [https://azure.microsoft.com/en-us/services/key-vault/](https://azure.microsoft.com/en-us/services/key-vault/)  
  
<a name="bkmk_GrantApplicationRights"></a>
   
## <a name="grant-your-application-rights-to-access-cds-for-apps-data"></a>アプリ用 CDS のデータにアクセスする権限を付与します
  
 このためアプリ用 CDS のインスタンスは Azure AD テナントに関連付けられている必要があります。 Azure AD テナントが アプリ用 CDS テナントに関連付けられていない場合、次の手順を実行することはできません。  
  
1. [https://portal.azure.com](https://portal.azure.com) に移動して **Azure Active Directory** を選択します。  
  
2. **アプリ登録** をクリックして Visual Studio を使用して作成したアプリケーションを検索します。  
  
3. アプリ用 CDS のデータにアクセスする特権をアプリケーションに与える必要があります。 **API アクセス**領域で**必要なアクセス許可**をクリックします。 **Windows Azure Active Directory** に対するアクセス許可が既にあることを確認する必要があります。  
  
4. **追加**をクリックし、次に **API の選択**をクリックします。 一覧で、**Dynamics 365** を選択し、**選択**ボタンをクリックします。  
  
5. **アクセス許可の選択**で、**組織のユーザーとして Dynamics 365 にアクセスする**を選択します。 次に、**選択**ボタンをクリックします。  
  
6. これらのアクセス許可を追加するには、**完了**をクリックします。 完了したらアクセス許可が適用されていることを確認する必要があります。  
  
   ![Dynamics 365 の許可をアプリケーションに与える](media/grant-crm-permissions-to-application.png "Dynamics 365 の許可をアプリケーションに与える")  
  
<a name="bkmk_CreateAppUser"></a>
   
## <a name="create-an-application-user--associated-with-the-registered-application--in-cds-for-apps"></a>アプリ用 CDS で登録されたアプリケーションに関連付けられるアプリケーション ユーザーを作成します  
 アプリケーションのサブスクライバーの 1 つである アプリ用 CDS のデータにアクセスする場合、サブスクライバーの アプリ用 CDS 組織にアプリケーション ユーザーが必要になります。 あらゆるアプリ用 CDS ユーザーと同様に、このアプリケーション ユーザーはユーザーがアクセスできるデータを定義する少なくとも 1 つのセキュリティロールに関連付けられている必要があります。  
  
 [SystemUser エンティティ](reference/entities/systemuser.md)には、このデータを保存する 3 つの新しい属性があります。  
  
|スキーマ名|表示名|種類​​|内容|  
|-----------------|------------------|----------|-----------------|  
|[ApplicationId](reference/entities/systemuser.md#BKMK_ApplicationId)|**アプリケーション ID**|UniqueidentifierType|アプリケーションの識別子。 これは、別のアプリケーションのデータにアクセスするために使用されます。|  
|[ApplicationIdUri](reference/entities/systemuser.md#BKMK_ApplicationIdUri)|**アプリケーション ID の URI**|StringType|外部アプリケーションの一意の論理識別子として使用される URI。 これは、アプリケーションを検証するのに使用できます|  
|[AzureActiveDirectoryObjectId](reference/entities/systemuser.md#BKMK_AzureActiveDirectoryObjectId)|**Azure AD オブジェクト ID**|UniqueidentifierType|アプリケーション ディレクトリのオブジェクト ID です。|  
  
 この `systemuser``AzureActiveDirectoryObjectId` プロパティ値は、登録済みアプリケーションの Azure Active Directory オブジェクト ID の参照である必要があります。 この参照はアプリケーション ユーザーが `ApplicationId` の値に基づいて作成されるときアプリ用 CDS に設定されます。  
  
> [!NOTE]
>  独自の アプリ用 CDS テナントとそれに関連付けられた Azure AD テナントを使用して最初にアプリケーションを開発する場合、登録済みアプリケーションが既に Azure AD テナントの一部であるためアプリケーション ユーザーを容易に作成できます。  
> 
>  ただし、テストのために別の組織でアプリケーション ユーザを作成するため、またはユーザがアプリケーションを使用するたびに、まずアプリケーションの同意を取得する必要があるため、プロセスのステップが異なります。 詳細については、「[個別の Dynamics 365 テナントを使用してアプリケーションをテストする](#bkmk_TestUsingSeparateTenant)」を参照してください。  
  
<a name="bkmk_CreateSecurityRole"></a>  
 
### <a name="create-a-security-role-for-the-application-user"></a>アプリケーション ユーザーによるセキュリティ ロールを作成します  

 次の手順でアプリ用 CDS のアプリケーション ユーザーを作成します。 このユーザーの特権とアクセス権は、設定したカスタム セキュリティ ロールで定義されます。 アプリケーションでユーザーを作成する前に、カスタム セキュリティ ロールを作成してユーザーを関連付けることができます。 詳細: [セキュリティ ロールの作成または編集](https://technet.microsoft.com/library/dn531130.aspx)  
  
> [!NOTE]
>  アプリケーション ユーザーはアプリ用 CDS における既定のセキュリティ ロールの 1 つと関連付けることができません。 アプリケーション ユーザーに関連付ける、ユーザー定義のセキュリティ ロールを作成する必要があります。  
  
<a name="bkmk_ManuallyCreateUser"></a>   

### <a name="manually-create-a-cds-for-apps-application-user"></a>アプリ用 CDS のアプリケーション ユーザーを手動で作成します  

 このユーザーを作成する手順は、ライセンスを受けたユーザーを作成する手順とは異なります。 次の手順を実行します。  
  
1. **設定** > **セキュリティ** > **ユーザー**の順に移動します  
  
2. ビュー ドロップダウンで、**アプリケーション ユーザー**を選択します。  
  
3. **新規**をクリックします。 次に**アプリケーション ユーザー**フォームを使用していることを確認します。  
  
    フォームの**アプリケーション ID**、**Application ID URI** および **Azure AD オブジェクト ID** フィールドが表示されない場合は、リストから**アプリケーションのユーザー**フォームを選択する必要があります:  
  
   ![アプリケーション ユーザー フォームの選択](media/select-application-user-form.PNG "アプリケーション ユーザー フォームの選択")  
  
4. フィールドに適切な値を追加します:  
  
   |フィールド|Value|  
   |-----------|-----------|  
   |**アプリケーション ID**|Azure AD に登録されたアプリケーションのアプリケーション ID 値。|  
   |**氏名**|アプリケーションの名前。|  
   |**電子メール 1**|サブスクライバーが連絡するときに使用する電子メール アドレス。|  
  
    **ユーザー名**、**アプリケーション ID URI** および **Azure AD オブジェクト ID** はロックされているため、これらのフィールドの値を設定することはできません。  
  
    このユーザーを作成するときのこれらのフィールド値は、ユーザーを保存するときの**アプリケーション ID** 値に基づいて Azure AD から取得されます。  
  
5. アプリケーション ユーザーを「[アプリケーション ユーザーによるセキュリティ ロールを作成する](#bkmk_CreateSecurityRole)」で作成されたカスタム セキュリティ ロールに関連付けます。 詳細情報: [Dynamics 365 (オンライン) でのユーザーの作成およびセキュリティ ロールの割り当て](/dynamics365/customer-engagement/admin/create-users-assign-online-security-roles)  
  
<a name="bkmk_TestUsingYourTenant"></a>  
 
## <a name="test-your-application-using-your-cds-for-apps-tenant"></a>アプリ用 CDS テナントを使用してアプリケーションをテストします 
 
 アプリケーションが Azure AD テナントに登録されていて、なおかつ開発組織のアプリケーション ユーザーが既に構成されているため、独自の アプリ用 CDS テナントに対してアプリケーションを開発し続けることができます。 ただし、これは、マルチテナント機能の有効なテストではありません。 個別のアプリ用 CDS テナントでアプリケーションをテストする必要があります。  
  
<a name="bkmk_TestUsingSeparateTenant"></a>   

## <a name="test-your-application-using-a-separate-cds-for-apps-tenant"></a>個別のアプリ用 CDS テナントを使用してアプリケーションをテストします  

 個別のアプリ用 CDS テナントでアプリケーションをテストする前に、Azure AD テナントの管理者はアプリケーションの承認を取得する必要があります。 管理者は、ブラウザーを使用してアプリケーションに移動し同意を取得します。 初めてアプリケーションにアクセスすると、このようなダイアログが表示されます:  
  
 ![Dynamics 365 データにアクセスする同意を与える](media/grant-consent-to-access-crm-data.PNG "Dynamics 365 データにアクセスする同意を与える")  
  
 同意を取得すると、登録されたアプリケーションは、Azure AD エンタープライズ アプリケーション リストに追加され、Azure AD テナントのユーザーが使用できるようになります。  
  
 管理者が承認を取得した後でのみ、サブスクライバーのアプリ用 CDS テナントでアプリケーション ユーザーを作成することができます。 「[Dynamics 365 アプリケーション ユーザーを手動で作成する](#bkmk_ManuallyCreateUser)」に記載された手順を使用してアプリケーション ユーザーを手動で作成することができます。  
  
 初期テストの場合は、これらのステップを手動で実行する必要があります。 サブスクライバーがアプリケーションまたはサービスを利用する準備ができたときに、より効率的なステップを使用します。 これについては、次のセクションで説明します。  
  
<a name="bkmk_PrepareMethodToDeployAppUser"></a>
   
## <a name="prepare-a-method-to-deploy-the-application-user"></a>アプリケーション ユーザーを展開するメソッドを準備します  

 サブスクライバーがアプリケーションまたはサービスの承認を取得した後、アプリ用 CDS 組織にアプリケーション ユーザーとその他の必須コンポーネントを追加するための簡単で信頼できる方法が必要になります。  
  
 アプリケーションに必要な特権を定義し、アプリケーション ユーザーがそのカスタム セキュリティ ロールに関連付けられていることを確認するカスタムセキュリティロールを含める必要があります。 カスタム セキュリティ ロールをソリューションに含めることができるため、カスタム セキュリティ ロールの定義とアプリケーションに必要なその他のソリューション コンポーネントを含む管理 ソリューションを準備する必要があります。  
  
 カスタム セキュリティ ロールの作成の詳細については、参照してください  
  
- [セキュリティ ロールの作成または編集](/dynamics365/customer-engagement/admin/create-edit-security-role)  
- [セキュリティ ロールのコピー](/dynamics365/customer-engagement/admin/copy-security-role)  
- [ソリューション コンポーネントの追加](/dynamics365/customer-engagement/customize/create-solution.md#add-solution-components)
  
  アプリ用 CDS のソリューション作成に関する詳細は次のトピックを参照してください:
  
- [カスタマイズでのソリューションの使用](../../maker/common-data-service/use-solutions-for-your-customizations.md)  
- [ソリューションを使用した拡張機能のパッケージ化および配布](/dynamics365/customer-engagement/developer/package-distribute-extensions-use-solutions)  
  
  ただし、アプリケーション ユーザーをソリューションに含めることはできないため、このアプリケーション ユーザーを作成しカスタム セキュリティ ロールを関連付ける方法を提供する必要があります。  
  
  Web サービスを使用して独自のプログラムを作成したりサブスクライバーにプログラムを実行させるなど、これを達成するにはいくつかの方法があります。  
  
  Dynamics 365 の Package Deployerは、ソリューションおよびデータを別の アプリ用 CDS 組織へ自動的に転送するパッケージを準備するのに使用できるアプリケーションです。 詳細: [Dynamics 365 Package Deployer 用のパッケージを作成する](/dynamics365/customer-engagement/developer/create-packages-package-deployer)  
  
### <a name="see-also"></a>関連項目  
 [チュートリアル: マルチ テナント型のサーバー間認証の使用](/dynamics365/customer-engagement/developer/walkthrough-multi-tenant-server-server-authentication)   
 [単一テナント型のサーバー間認証の使用](use-single-tenant-server-server-authentication.md)   
 [サーバー間 (S2S) の認証を使用して Web アプリケーションを作成する](build-web-applications-server-server-s2s-authentication.md)   
 [Dynamics 365 への接続](/dynamics365/customer-engagement/developer/connect-customer-engagement)