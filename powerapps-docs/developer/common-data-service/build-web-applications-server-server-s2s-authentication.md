---
title: サーバー間 (S2S) の認証を使用して Web アプリケーションを作成する (Common Data Service) | Microsoft Docs
description: サーバー間 (S2S) の認証を使用して、 Common Data Service と Web アプリケーションおよびサービスと安全かつシームレスに通信します。 S2S 認証は Microsoft AppSource に登録されたアプリがサブスクライバーの Common Data Service のデータにアクセスする一般的な方法です。
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
# <a name="build-web-applications-using-server-to-server-s2s-authentication"></a>サーバー間 (S2S) の認証を使用して Web アプリケーションを作成する

サーバー間 (S2S) の認証を使用して、 Common Data Service と Web アプリケーションおよびサービスと安全かつシームレスに通信します。 S2S 認証は Microsoft AppSource に登録されたアプリがサブスクライバーの Common Data Service のデータにアクセスする一般的な方法です。  

S2S 認証は、Common Data Service 環境に接続する時に、有料の PowerApps ユーザー ライセンスを使用する必要がないことを意味します。 S2S 認証と共に使用する特殊 *アプリケーション ユーザー* アカウントのライセンス料金はありません。 ただし、[アプリケーション ユーザーの要求数の制限](https://docs.microsoft.com/power-platform/admin/api-request-limits-allocations#non-licensed-usersapplication-users) のアカウントを呼び出すことができます。 S2S 認証でライセンスを付与されていない特殊アプリケーション ユーザー アカウントが作成され、そこには Azure Active Directory (Azure AD) に登録されているアプリケーションの情報が含まれます。 ユーザーの資格情報ではなく、アプリケーション ユーザー レコードに保存されている Azure AD オブジェクト ID 値によって識別されるサービス プリンシパルに基づいてアプリケーションは認証されます。 アプリケーション ユーザーは、アプリケーションが実行できるデータおよび操作の種類を制御するカスタム セキュリティ ロールに関連付けられます。  

 S2S を使用してアプリケーションまたはサービスによって実行するすべての操作は、ユーザーのアプリケーションにアクセスしているユーザーとしてではなく、ユーザーが提供するアプリケーションのユーザーとして実行されます。 ユーザーのアプリケーションと対話しているユーザーなど、特定のユーザーに代わってデータ操作をアプリケーションが実行することを希望する場合、アプリケーション サービス プリンシパルに適用するユーザー定義のセキュリティ ロールが必要な特権を持っている場合に、偽装を適用できます。 詳細情報: [もう一方のユーザーの偽装](impersonate-another-user.md)  

 S2S 認証を使用する Web アプリケーションまたはサービスはアクセス権を持っているデータへのアクセスを制御します。 これは通常、OpenID 接続プロバイダーを使用して行われます。 詳細については、「<http://openid.net/connect/>」を参照してください。  

## <a name="server-to-server-authentication-scenarios"></a>サーバー間の認証シナリオ  
 S2S 認証が適用できる 2 つのシナリオがあります。  


|   シナリオ    |   説明  |
|---------------|---------------|
| マルチテナント  | これは最も一般的なシナリオで、 Microsoft AppSource を使用して配布されたアプリケーションに対して使用されるものです。<br /><br /> 各 Common Data Service テナントは、Azure AD テナントに関連付けられます。 Web アプリケーションまたはサービスは、独自の Azure AD テナントで登録されます。<br /><br /> このシナリオでは、アプリケーションがテナントのデータにアクセスする許可を取得した後に、すべての Common Data Service テナントはマルチテナント型アプリケーションを潜在的に使用できます。                                                           |
| 単一テナント | このシナリオは通常、独自のテナントのアプリを開発し、それをその他の [Common Data Service 環境 へ配布する意図のない Common Data Service 環境に対して適用されます。<br /><br /> エンタープライズは、テナントのすべての Common Data Service 環境に接続する Web アプリケーションまたはサービスを作成できます。<br /><br /> このシナリオでは、Web アプリケーションやサービスが、同じ Azure AD テナント情報を使用して Common Data Service 環境のみに接続することができます。 |

 両方のシナリオに共通要素がありますが、異なる要素もあります。 マルチテナント型は最も共通なシナリオであるため、 [マルチテナント型サーバー間認証を使用](use-multi-tenant-server-server-authentication.md) コンテンツでは、このシナリオで S2S を使用する方法が説明され、単一テナントの構成のオプションが異なる場合に関するメモが追加されています。 

[マルチテナント型サーバー間認証を使用](use-single-tenant-server-server-authentication.md) では、このシナリオの概要が説明され、マルチテナント型 S2S 認証のコンテンツで説明されている手順が参照されています。  

### <a name="see-also"></a>関連項目  
  
[マルチ テナント型でのサーバー間認証の使用](use-multi-tenant-server-server-authentication.md)<br/> 
[単一テナント型のサーバー間認証を使用する](use-single-tenant-server-server-authentication.md)   
