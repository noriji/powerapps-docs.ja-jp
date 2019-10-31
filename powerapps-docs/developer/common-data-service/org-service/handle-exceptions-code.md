---
title: コードで例外を処理する (Common Data Service) | Microsoft Docs
description: この記事では、 Common Data Service web サービス メソッド呼び出しで返される例外について説明します。 この記事のサンプルでは、アプリケーション デザインで処理する必要がある一般的なフォールトと例外を重点的に示しています。
ms.custom: ''
ms.date: 06/17/2019
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: brandonsimons
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="handle-exceptions-in-your-code"></a>コードで例外を処理する

Common Data Service Web サービスのメソッド呼び出しで返される例外がいくつかあります。 これらの例外をキャッチし、適切に処理するようにアプリケーションを設計する必要があります。 SDK .NET アセンブリでは、すべての Web サービス メソッド呼び出しで、Windows Communication Foundation テクノロジを基盤とするサーバーへの通信チャネルを使用します。 WCF の用語では、このチャネルから返される例外を *フォールト* と呼びます。  

<a name="BKMK_Common"></a>   

## <a name="common-exceptions-and-faults"></a>一般的な例外とフォールト  

次のコードは、ほとんどの Common Data Service Web サービス サンプルで使用されるものです。 アプリケーション デザインで処理する必要がある一般的なフォールトと例外を重点的に示しています。  
  
```csharp
catch (FaultException<Microsoft.Xrm.Sdk.OrganizationServiceFault> ex)
{
    Console.WriteLine("The application terminated with an error.");
    Console.WriteLine("Timestamp: {0}", ex.Detail.Timestamp);
    Console.WriteLine("Code: {0}", ex.Detail.ErrorCode);
    Console.WriteLine("Message: {0}", ex.Detail.Message);
    Console.WriteLine("Inner Fault: {0}",
        null == ex.Detail.InnerFault ? "No Inner Fault" : "Has Inner Fault");
}
catch (System.TimeoutException ex)
{
    Console.WriteLine("The application terminated with an error.");
    Console.WriteLine("Message: {0}", ex.Message);
    Console.WriteLine("Stack Trace: {0}", ex.StackTrace);
    Console.WriteLine("Inner Fault: {0}",
        null == ex.InnerException.Message ? "No Inner Fault" : ex.InnerException.Message);
}
catch (System.Exception ex)
{
    Console.WriteLine("The application terminated with an error.");
    Console.WriteLine(ex.Message);

    // Display the details of the inner exception.
    if (ex.InnerException != null)
    {
        Console.WriteLine(ex.InnerException.Message);

        FaultException<Microsoft.Xrm.Sdk.OrganizationServiceFault> fe = ex.InnerException
            as FaultException<Microsoft.Xrm.Sdk.OrganizationServiceFault>;
        if (fe != null)
        {
            Console.WriteLine("Timestamp: {0}", fe.Detail.Timestamp);
            Console.WriteLine("Code: {0}", fe.Detail.ErrorCode);
            Console.WriteLine("Message: {0}", fe.Detail.Message);
            Console.WriteLine("Trace: {0}", fe.Detail.TraceText);
            Console.WriteLine("Inner Fault: {0}",
                null == fe.Detail.InnerFault ? "No Inner Fault" : "Has Inner Fault");
        }
    }
}
```
  
> [!NOTE]
>  検出 Web サービスにアクセスしている場合は、以前に示した <xref:Microsoft.Xrm.Sdk.DiscoveryServiceFault> フォールトではなく <xref:Microsoft.Xrm.Sdk.OrganizationServiceFault> をコードでキャッチする必要があります。  
  
これらの例外とフォールトに加えて、次の例外もコードで処理する必要があります。  
  
- [SecurityTokenValidationException](/dotnet/api/system.identitymodel.tokens.securitytokenvalidationexception)  
- [ExpiredSecurityTokenException](/dotnet/api/system.servicemodel.security.expiredsecuritytokenexception)  
- [SecurityAccessDeniedException](/dotnet/api/system.servicemodel.security.securityaccessdeniedexception)  
- [MessageSecurityException](/dotnet/api/system.servicemodel.security.messagesecurityexception)  
- [SecurityNegotiationException](/dotnet/api/system.servicemodel.security.securitynegotiationexception)  
  
Common Data Service に接続するときに、Microsoft アカウント が有効であり、アカウントが Common Data Service 組織に関連付けられていない場合、 `SecurityAccessDeniedException` 例外がスローされることがあります。 Microsoft アカウントが無効か、認証に失敗する場合、`MessageSecurityException` がスローされることがあります。  
  
<a name="BKMK_BusinessRuleErrors"></a>

## <a name="custom-errors-from-business-rules"></a>業務ルールからのカスタム エラー
 
Common Data Serviceでは、 カスタマイザーはサーバーで評価される業務ルールを作成します。 カスタマイザーは、ビジネス ルール条件のセットに基づいてエラーメッセージをスローする可能性があります。 開発者は、コードで処理するにしっかりとしたエラーを含め、これらの例外を取得して処理するようにする必要があります。  
  
次の例は、これらのエラーの 1 つが業務ルールから返される際に生成されるトレース ログを示しています。業務ルールの名前は**エラーを返すエンティティ スコープの業務ルールの名前**で、エラーメッセージは**ユーザー定義のエラー メッセージ**です。  
  
```csharp
Unhandled Exception: System.ServiceModel.FaultException`1[[Microsoft.Xrm.Sdk.OrganizationServiceFault, Microsoft.Xrm.Sdk, Version=7.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35]]: custom error messageDetail:   
<OrganizationServiceFault xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.microsoft.com/xrm/2011/Contracts">  
  <ErrorCode>-2147220891</ErrorCode>  
  <ErrorDetails xmlns:d2p1="http://schemas.datacontract.org/2004/07/System.Collections.Generic">  
    <KeyValuePairOfstringanyType>  
      <d2p1:key>OperationStatus</d2p1:key>  
      <d2p1:value xmlns:d4p1="http://www.w3.org/2001/XMLSchema" i:type="d4p1:string">0</d2p1:value>  
    </KeyValuePairOfstringanyType>  
    <KeyValuePairOfstringanyType>  
      <d2p1:key>SubErrorCode</d2p1:key>  
      <d2p1:value xmlns:d4p1="http://www.w3.org/2001/XMLSchema" i:type="d4p1:string">-2146233088</d2p1:value>  
    </KeyValuePairOfstringanyType>  
  </ErrorDetails>  
  <Message>custom error message</Message>  
  <Timestamp>2014-09-04T17:43:16.8197965Z</Timestamp>  
  <InnerFault i:nil="true" />  
  <TraceText>  
  
[Microsoft.Crm.ObjectModel: Microsoft.Crm.ObjectModel.SyncWorkflowExecutionPlugin]  
[cf6a25a9-5a34-e411-80b9-00155dd8c20f: ]  
Starting sync workflow 'Name of Entity Scope Business Rule returning Error', Id: c76a25a9-5a34-e411-80b9-00155dd8c20f  
Entering ConditionStep1_step:   
Entering SetMessage_step:   
Sync workflow 'Name of Entity Scope Business Rule returning Error' terminated with error 'custom error message'  
  
</TraceText>  
</OrganizationServiceFault>  
```  
  
詳細: [エンティティに対する業務ルールの作成](../../../maker/common-data-service/data-platform-create-business-rule.md)  
  
<a name="BKMK_AdditionalInfo"></a>

## <a name="additional-information-about-exceptions"></a>例外に関する追加情報

ユーザーが表示するアクセス許可がない機密情報を含む uncaught の例外がスローされると、例外の機密情報はユーザーから隠され、参照番号が表示されます。 この参照番号は、関連するサーバー イベント ログのエントリとサーバー トレースのエントリを参照します。 システム管理者はこれらのエントリを検索して、例外に関する情報を参照できます。  
  
### <a name="see-also"></a>関連項目  

 [Web サービス エラー コード](web-service-error-codes.md)   
 [プラグインでの例外の処理](../handle-exceptions.md)   
 [.NET Framework デベロッパー センター](https://docs.microsoft.com/dotnet/framework/development-guide)