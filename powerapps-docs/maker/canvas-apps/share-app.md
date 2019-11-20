---
title: キャンバス アプリを共有する | Microsoft Docs
description: キャンバス アプリを実行または修正するためのアクセス許可を他のユーザーに付与することで、キャンバス アプリを共有します。
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 08/09/2019
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 2fdf5577f907e2beb7ead5eef3c4d7b06aeaa9c5
ms.sourcegitcommit: 01fefd7a06bf5d6509acd0bb54ea6479208cbbc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/19/2019
ms.locfileid: "74177860"
---
# <a name="share-a-canvas-app-in-powerapps"></a>PowerApps でのキャンバス アプリの共有

ビジネス ニーズに対応するキャンバス アプリをビルドした後、アプリを実行できる組織内のユーザー、およびアプリを変更したり、再度共有したりすることもできるユーザーを指定します。 各ユーザーを名前で指定するか、Azure Active Directory のセキュリティ グループを指定します。 すべてのユーザーがアプリから恩恵を受ける場合、組織全体がアプリを実行できるように指定します。

> [!IMPORTANT]
> For a shared app to function as you expect, you must also manage permissions for the data source or sources on which the app is based, such as [Common Data Service](#common-data-service) or [Excel](share-app-data.md). アプリが依存する[その他のリソース](share-app-resources.md) (フロー、ゲートウェイ、接続など) を共有する必要がある場合もあります。

## <a name="prerequisites"></a>前提条件

アプリを共有するには、そのアプリを (ローカルではなく) クラウドに保存して、アプリを発行する必要があります。

- ユーザーがアプリで行う内容を理解し、リストで簡単に見つけられるように、アプリにわかりやすい名前と明確な説明を追加します。 PowerApps Studio の **[ファイル]** メニューで、 **[アプリの設定]** を選択し、説明を入力するか貼り付けます。

- 変更を加えるたびに、他のユーザーがそれらの変更を表示する必要がある場合は、再度アプリを保存および発行する必要があります。

## <a name="share-an-app"></a>アプリを共有する

1. PowerApps に[サインイン](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)し、左端近くにある **[アプリ]** を選びます。

    ![アプリの一覧を表示する](./media/share-app/file-apps.png)

1. Select the app that you want to share by selecting its icon.

    ![Select an app](./media/share-app/select-app.png)

1. In the banner, select **Share**.

    ![共有画面を開く](./media/share-app/banner-share.png)

1. Specify by name or alias the users or security groups in Azure Active Directory with which you want to share the app.

    - To allow your entire organization to run the app (but not modify or share it), type **Everyone** in the sharing panel.
    - You can share an app with a list of aliases, friendly names, or a combination of those (for example, **Jane Doe &lt;jane.doe@contoso.com** ) if the items are separated by semi-colons. If more than one person has the same name but different aliases, the first person found will be added to the list. A tooltip appears if a name or alias already has permission or can't be resolved. 

    ![Specify users and co-owners](./media/share-app/share-everyone.png)

    > [!NOTE]
    > You can't share an app with a distribution group in your organization or with a group outside your organization.

1. If you want to allow those with whom you're sharing the app to edit and share it (in addition to running it), select the **Co-owner** check box.

    You can't grant **Co-owner** permission to a security group if you [created the app from within a solution](add-app-solution.md).

    > [!NOTE]
    > Regardless of permissions, no two people can edit an app at the same time. If one person opens the app for editing, other people can run it but not edit it.

1. If your app connects to data for which users need access permissions, specify them.

    For example, your app might connect to an entity in a Common Data Service database. When you share such an app, the sharing panel prompts you to manage security for that entity.

    > [!div class="mx-imgBorder"]
    > ![Assign a security role](media/share-app/cds-assign-security-role.png)

    For more information about managing security for an entity, see [Manage entity permissions](share-app.md#manage-entity-permissions) later in this topic.

1. If you want to help people find your app, select the **Send an email invitation to new users** check box.

1. At the bottom of the share panel, select **Share**.

    Everyone with whom you shared the app can run it in PowerApps Mobile on a mobile device or in AppSource on [Dynamics 365](https://home.dynamics.com) in a browser. Co-owners can edit and share the app in [PowerApps](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).

    If you sent an email invitation, everyone with whom you shared the app can run it by selecting a link in the invitation.

    - If a user selects the link on a mobile device, the app opens in PowerApps Mobile.
    - If a user selects the link on a desktop computer, the app opens in a browser.

    Co-owners who receive an invitation get another link that opens the app for editing in PowerApps Studio.

You can change permissions for a user or a security group by selecting their name and then performing either of these steps:

- To allow co-owners to run the app but no longer edit or share it, clear the **Co-owner** check box.
- To stop sharing the app with that user or group, select the Remove (x) icon.

## <a name="security-group-considerations"></a>セキュリティ グループに関する考慮事項

- セキュリティ グループでアプリを共有すると、そのグループの既存のメンバーとグループに参加するユーザーは、そのグループに指定したアクセス許可が付与されます。 アクセス権がある別のグループに属しているか、個人としてアクセス許可を付与しない限り、グループから脱退する任意のユーザーはそのアクセス許可を失います。

- セキュリティ グループのすべてのメンバーは、アプリに関して、グループ全体と同じアクセス許可を持ちます。 ただし、そのグループの 1 人以上のメンバーに対してより多くのアクセス許可を指定することで、メンバーのアクセス許可を増やすことができます。 For example, you can give Security Group A permission to run an app, but you can also give User B, who belongs to that group, **Co-owner** permission. セキュリティ グループのすべてのメンバーはアプリを実行できますが、ユーザー B だけは編集することができます。 If you give Security Group A **Co-owner** permission and User B permission to run the app, that user can still edit the app.

## <a name="manage-entity-permissions"></a>エンティティのアクセス許可を管理する

### <a name="common-data-service"></a>Common Data Service

If you create an app based on Common Data Service, you must also ensure that the users with whom you share the app have the appropriate permissions for the entity or entities on which the app relies. Specifically, those users must belong to a security role that can perform tasks such as creating, reading, writing, and deleting relevant records. In many cases, you'll want to create one or more custom security roles with the exact permissions that users need to run the app. You can then assign a role to each user as appropriate.

> [!NOTE]
> As of this writing, you can assign security roles to individual users and security groups in Azure Active Directory but not to Office groups.

#### <a name="prerequisite"></a>前提条件

To assign a role, you must have **System administrator** permissions for a Common Data Service database.

#### <a name="assign-a-security-group-in-azure-ad-to-a-role"></a>Assign a security group in Azure AD to a role

1. In the sharing panel, select **Assign a security role** under **Data permissions**.

1. Select the role or roles in Common Data Service that you want to assign to the user or the security group in Azure AD with which you want to share the app.
     > [!div class="mx-imgBorder"] 
     > ![Security role list](media/share-app/cds-assign-security-role-list.png "Security role list")

### <a name="common-data-service-previous-version"></a>Common Data Service (以前のバージョン)

When you share an app that's based on an older version of Common Data Service, you must share the runtime permission to the service separately. If you don’t have permission to do this, see your environment administrator.

## <a name="share-with-guests"></a>Share with guests
 
PowerApps canvas apps can be shared with guest users of an Azure Active Directory tenant. This enables inviting external business partners, contractors, and third parties to run your company’s canvas apps. 

> [!NOTE]
> Guests may only be assigned the **User** role, and not the **Co-owner** role, for apps shared with them.

### <a name="prerequisites"></a>前提条件
- In Azure Active Directory (Azure AD), enable B2B external collaboration for the tenant. More information: [Enable B2B external collaboration and manage who can invite guests](/azure/active-directory/b2b/delegate-invitations)
    - Enable B2B external collaboration is on by default. However, the settings can be changed by a tenant admin.  For more information about Azure AD B2B, see [What is guest user access in Azure AD B2B?](/azure/active-directory/b2b/what-is-b2b)  
- Access to an account that can add guest users to an Azure AD tenant. Admins and users with the Guest Inviter role can add guests to a tenant.   
- The guest user must have a license with Power Apps use rights that matches the capability of the app assigned through one of the following tenants:
    - The tenant hosting the app being shared.
    - The home tenant of the guest user.

### <a name="steps-to-grant-guest-access"></a>Steps to grant guest access
1. Select **New guest user** to add guest users in Azure AD. More information: [Quickstart: Add a new guest user in Azure AD](/azure/active-directory/b2b/b2b-quickstart-add-guest-users-portal).
    > [!div class="mx-imgBorder"] 
    > ![Add guest in Azure AD](media/share-app/guest_access_doc_1.png "Add guest in Azure AD")
2. If the guest user doesn't already have a license in their home tenant, assign a license to the guest user.
   - To assign guest users from admin.microsoft.com, see [Assign licenses to one user](/office365/admin/subscriptions-and-billing/assign-licenses-to-users).
   - To assign guest users from portal.azure.com, see [Assign or remove licenses](/azure/active-directory/fundamentals/license-users-groups).
 
   > [!IMPORTANT]
   > You may need to disable the Microsoft 365 admin center preview to assign a license to a guest. 

3. Share the canvas app. 
    1. Sign in to https://make.powerapps.com  
    2. Go to **Apps**, select a canvas app, and then on the command bar select **Share**. 
    3. Enter an email address for a guest user from an Azure AD tenant. More information: [What is guest user access in Azure AD B2B?](/azure/active-directory/b2b/what-is-b2b)
          > [!div class="mx-imgBorder"] 
          > ![Share with guest](media/share-app/guest_access_doc_2.png "Share with guest")
 
After you share an app for guest access, guests can discover and access apps shared with them from the email sent to them as part of sharing.

> [!div class="mx-imgBorder"]  
> ![Guests receive app share email](media/share-app/guest_access_doc_4.png "Guests receive app share email")

### <a name="frequently-asked-questions"></a>よく寄せられる質問

#### <a name="whats-the-difference-between-canvas-app-guest-access-and-powerapps-portals"></a>What’s the difference between canvas app guest access and PowerApps Portals? 
Canvas apps enable building an app, tailored to digitizing a business processes, without writing code in a traditional programming language such as C#. Guest access for canvas apps enables teams of individuals made up of different organizations participating in a common business process to access the same app resources that may be integrated with a wide variety of Microsoft and third-party sources. More information: [Overview of canvas-app connectors for PowerApps](/powerapps/maker/canvas-apps/connections-list).

[PowerApps Portals](/powerapps/maker/portals/overview) provide the ability to build low-code, responsive websites that allow external users to interact with the data stored in Common Data Service. It allows organizations to create websites that can be shared with users external to their organization either anonymously or through the login provider of their choice, such as LinkedIn, Microsoft Account, or other commercial login providers. 

The following table outlines a few core capability differences between PowerApps Portals and canvas apps.  

| | インターフェイス | 認証 | Accessible data sources |
|------|--------|----------|-------------------|
| PowerApps Portals | Browser only experience | Allows anonymous and authenticated access | Common Data Service |
| キャンバス アプリ | Browser and mobile apps | Requires authentication via Azure AD | Any ~150 out-of-box connectors and any custom connector  |
||

#### <a name="can-guests-access-customized-forms-in-sharepoint"></a>Can guests access customized forms in SharePoint?
はい。 Any user that can access a SharePoint list with a customized form can create and edit items in the list, using the form, without any Power Apps license.

#### <a name="can-guests-access-apps-embedded-in-sharepoint"></a>Can guests access apps embedded in SharePoint? 
はい。 Though, access to canvas standalone apps require a license with Power Apps use rights that matches the capability of the app, including apps that are embedded. When embedding a canvas app in SharePoint via the Microsoft PowerApps embed control, enter the app id. To do this, enter the app ID in the **App web link or ID** box. 

> [!div class="mx-imgBorder"]  
> ![Embed canvas app in SharePoint for guests](media/share-app/guest_access_doc_5.PNG "Embed canvas app in SharePoint for guests")

When embedding a canvas app in SharePoint via the iFrame HTML tag, reference the app using the full web URL. To find the URL, go to https://make.powerapps.com, select an app, select the **Details** tab, and the URL is displayed under **Web link**.

> [!div class="mx-imgBorder"]  
> ![Canvas app details](media/share-app/guest_access_doc_6.PNG "Canvas app details")

#### <a name="how-come-guests-can-launch-the-app-shared-with-them-but-connections-fail-to-be-created"></a>How come guests can launch the app shared with them but connections fail to be created?
As with non-guests, the underlying data source(s) accessed by the app must also be made accessible to the guest.

#### <a name="what-license-must-be-assigned-to-my-guest-so-they-can-run-an-app-shared-with-them"></a>What license must be assigned to my guest so they can run an app shared with them?
The same license that’s required for non-guests to run an app. For instance, if the app uses premium connecters then a PowerApps Per App Plan or a PowerApps Per User Plan must be assigned to the guest.  

|                                 | SharePoint customized form | Standalone canvas app using non-premium connectors | Standalone canvas app using premium connectors | Model driven app |
|---------------------------------|----------------------------|----------------------------------------------------|------------------------------------------------|------------------|
| SharePoint user (no PA license) | x                          |                                                    |                                                |                  |
| Power Apps Included w/ Office    | x                          | x                                                  |                                                |                  |
| Power Apps Per App Plan          | x                          | x                                                  | x                                              | x                |
| Power Apps Per User Plan         | x                          | x                                                  | x                                              | x                |


#### <a name="in-powerapps-mobile-how-does-a-guest-see-apps-for-their-home-tenant"></a>In PowerApps Mobile, how does a guest see apps for their home tenant?
Any user that has accessed an canvas app, on their mobile device, that’s published in an Azure AD tenant that isn’t their home tenant must sign-out of PowerApps and sign back in to PowerApps Mobile.  

#### <a name="must-a-guest-accept-the-azure-ad-guest-invitation-prior-to-sharing-an-app-with-the-guest"></a>Must a guest accept the Azure AD guest invitation prior to sharing an app with the guest?
いいえ。 If a guest launches an app shared with them prior to accepting a guest invitation the guest will be prompted to accept the invitation as part of the sign-in experience while launching the app.  

#### <a name="what-azure-ad-tenant-are-connections-for-a-guest-user-created-in"></a>What Azure AD tenant are connections for a guest user created in?
Connections for an app are always made in the context of the Azure AD tenant the app is associated. For instance, if an app is created in the Contoso tenant then connections made for Contoso internal and guest users are made in the context of the Contoso tenant.

#### <a name="can-guests-use-microsoft-graph-via-microsoft-security-graph-connector-or-a-custom-connector-using-microsoft-graph-apis"></a>Can guests use Microsoft Graph via Microsoft Security Graph connector or a custom connector using Microsoft Graph APIs?
No, Azure AD guests can't query Microsoft Graph to retrieve information for a tenant in which they’re a guest.

#### <a name="what-intune-policies-apply-to-guests-using-my-powerapps"></a>What InTune policies apply to guests using my PowerApps?
InTune only applies policies of a user’s home tenant. For instance, if Alice@Contoso.com shares an app with Vikram@Fabrikam.com, InTune continues to apply Fabrikam.com policies on Virkam’s device regardless of the PowerApps he runs.

#### <a name="what-connectors-support-guest-access"></a>What connectors support guest access?
All connectors that do not perform Azure AD authentication of any type supports guest access. The following table enumerates all connectors that perform Azure AD authentication and which connectors currently support guest access. Many of these will be updated leading up to general availability.

| **Connector**                                     | **Supports guest access**                                              |
|---------------------------------------------------|------------------------------------------------------------------------|
| 10to8 Appointment Scheduling                      | いいえ                                                                     |
| Adobe Creative Cloud                              | いいえ                                                                     |
| Adobe Sign                                        | いいえ                                                                     |
| Asana                                             | いいえ                                                                     |
| AtBot Admin                                       | いいえ                                                                     |
| AtBot Logic                                       | いいえ                                                                     |
| Azure AD                                          | はい                                                                    |
| Azure Automation                                  | はい                                                                    |
| Azure Container Instance                          | はい                                                                    |
| Azure Data Factory                                | はい                                                                    |
| Azure Data Lake                                   | はい                                                                    |
| Azure DevOps                                      | いいえ                                                                     |
| Azure Event Grid                                  | いいえ                                                                     |
| Azure IoT Central                                 | はい                                                                    |
| Azure Key Vault                                   | いいえ                                                                     |
| Azure Kusto                                       | はい                                                                    |
| Azure Log Analytics                               | はい                                                                    |
| Azure Resource Manager                            | はい                                                                    |
| Basecamp 2                                        | いいえ                                                                     |
| Bitbucket                                         | いいえ                                                                     |
| Bitly                                             | いいえ                                                                     |
| bttn                                              | いいえ                                                                     |
| Buffer                                            | いいえ                                                                     |
| Business Central                                  | いいえ                                                                     |
| CandidateZip                                      | いいえ                                                                     |
| Capsule CRM                                       | いいえ                                                                     |
| Cloud PKI Management                              | いいえ                                                                     |
| Cognito Forms                                     | いいえ                                                                     |
| Common Data Service                               | いいえ                                                                     |
| Common Data Service (Legacy)                      | いいえ                                                                     |
| D&B Optimizer                                     | いいえ                                                                     |
| Derdack SIGNL4                                    | いいえ                                                                     |
| Disqus                                            | いいえ                                                                     |
| Document Merge                                    | いいえ                                                                     |
| Dynamics 365                                      | いいえ                                                                     |
| Dynamics 365 AI for Sales                         | はい                                                                    |
| Dynamics 365 for Fin & Ops                        | いいえ                                                                     |
| Enadoc                                            | いいえ                                                                     |
| Eventbrite                                        | いいえ                                                                     |
| Excel Online (Business)                           | いいえ                                                                     |
| Excel Online (OneDrive)                           | いいえ                                                                     |
| Expiration Reminder                               | いいえ                                                                     |
| FreshBooks                                        | いいえ                                                                     |
| GoToMeeting                                       | いいえ                                                                     |
| GoToTraining                                      | いいえ                                                                     |
| GoToWebinar                                       | いいえ                                                                     |
| Harvest                                           | いいえ                                                                     |
| HTTP with Azure AD                                | いいえ                                                                     |
| Infusionsoft                                      | いいえ                                                                     |
| Inoreader                                         | いいえ                                                                     |
| Intercom                                          | いいえ                                                                     |
| JotForm                                           | いいえ                                                                     |
| kintone                                           | いいえ                                                                     |
| LinkedIn                                          | いいえ                                                                     |
| Marketing Content Hub                             | いいえ                                                                     |
| M                                            | いいえ                                                                     |
| Metatask                                          | いいえ                                                                     |
| Microsoft Forms                                   | いいえ                                                                     |
| Microsoft Forms Pro                               | いいえ                                                                     |
| Microsoft Graph Security                          | いいえ                                                                     |
| Microsoft Kaizala                                 | いいえ                                                                     |
| Microsoft School Data Sync                        | いいえ                                                                     |
| Microsoft StaffHub                                | いいえ                                                                     |
| Microsoft Teams                                   | はい                                                                    |
| Microsoft To-Do (Business)                        | いいえ                                                                     |
| Muhimbi PDF                                       | いいえ                                                                     |
| NetDocuments                                      | いいえ                                                                     |
| Office 365 グループ                                 | はい                                                                    |
| Office 365 Outlook                                | いいえ                                                                     |
| Office 365 Users                                  | はい                                                                    |
| Office 365 ビデオ                                  | いいえ                                                                     |
| OneDrive                                          | いいえ                                                                     |
| OneDrive for Business                             | いいえ                                                                     |
| OneNote (ビジネス)                                | いいえ                                                                     |
| Outlook Customer Manager                          | いいえ                                                                     |
| Outlook Tasks                                     | はい                                                                    |
| Outlook.com                                       | いいえ                                                                     |
| Paylocity                                         | いいえ                                                                     |
| Planner                                           | いいえ                                                                     |
| Plumsail Forms                                    | いいえ                                                                     |
| Power BI                                          | はい                                                                    |
| Project Online                                    | いいえ                                                                     |
| ProjectWise Design Integration                    | いいえ                                                                     |
| Projectwise Share                                 | いいえ                                                                     |
| SharePoint                                        | はい                                                                    |
| SignNow                                           | いいえ                                                                     |
| Skype for Business Online                         | いいえ                                                                     |
| Soft1                                             | いいえ                                                                     |
| Stormboard                                        | いいえ                                                                     |
| Survey123                                         | いいえ                                                                     |
| SurveyMonkey                                      | いいえ                                                                     |
| Toodledo                                          | いいえ                                                                     |
| Typeform                                          | いいえ                                                                     |
| Vimeo                                             | いいえ                                                                     |
| Webex Teams                                       | いいえ                                                                     |
| Windows Defender Advanced Threat Protection (ATP) | いいえ                                                                     |
| Word Online (Business)                            | いいえ                                                                     |
