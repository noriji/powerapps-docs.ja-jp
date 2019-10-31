---
title: 電子メール活動エンティティ (Common Data Service) | Microsoft Docs
description: Dynamics 365 の電子メール活動を使用すると、顧客との電子メール通信を追跡および管理することができます。
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: mayadumesh
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="email-activity-entities"></a>電子メール活動エンティティ

電子メール活動を使用すると、顧客との電子メール通信を追跡および管理できます。 Common Data Service には、Common Data Service との間の電子メールのルーティングを管理する電子メール ルーター ソフトウェアが含まれています。 電子メール活動は、電子メール プロトコルを使用して配信されます。 電子メール ルーターは、Exchange Web サービス、POP3、および SMTP の電子メール プロトコルをサポートしています。 電子メール ルーターに加え、電子メール活動は Dynamics 365 for Outlook を使用して配信することもできます。  
  
<a name="Actions"></a>   

## <a name="actions-on-an-email-activity"></a>電子メール活動のアクション  
 Common Data Service Web サービスでは、電子メール活動の以下のアクションを実行できます。  
  
- 電子メール活動を作成、取得、更新、削除する。  
  
- 電子メール メッセージを送信する。または電子メール テンプレート (`Template`) を使用して電子メール メッセージを送信する。 電子メール テンプレートの詳細については、[テンプレート エンティティ](/reference/entities/template.md) を参照してください。  
  
- (`ActivityMimeAttachment`) 属性を使用して電子メールにファイルを添付する。  
  
- 大量の電子メールを一括で送信する。  
  
- 着信した電子メール メッセージが Microsoft Exchange Server からユーザーまたはキューへ配信されるようにする、または発信するメッセージがユーザーまたはキューから Microsoft Exchange Server へ送信されるようにする。 キューに対して着信の電子メール メッセージを構成する方法については、[受信メッセージ用電子メールを構成する](/dynamics365/customer-engagement/developer/configure-email-incoming-messages) を参照してください。  
  
   `Organization.RequireApprovalForuserEmail` と `Organization.RequireApprovalForQueueEmail` (承認されたユーザー/キューに関してだけ電子メールを処理する) 組織属性が **true** (1) に設定されている場合、電子メール メッセージはユーザー/キューの既定電子メール アドレスが承認されている場合に限ってユーザー/キューから配信または送信されます。 `SystemUser.EmailRouterAccessApproval` と `Queue.EmailRouterAccessApproval` 属性は、それぞれユーザーとキューの既定電子メール アドレスのステータスを示し、値を 1 に設定する必要があります。 それ以外の場合は、受信メッセージと送信メッセージがブロックされます。 まだ承認状態でない場合、現在使用しているユーザー アカウントに **prvApproveRejectEmailAddress** 権限が割り当てられていれば、ユーザーまたはキュー レコードを更新してこの属性値を変更できます。
  
> [!NOTE]
>  Common Data Service では、`Email.StatusCode` 属性を **null** にできません。  
  
<a name="BulkE-Mail"></a>   

## <a name="bulk-email"></a>電子メール広告  
 Common Data Service は、電子メールの一括処理要求を通じて大きな受信者リストに電子メールを送信する機能をサポートしています。 電子メールの一括処理要求が Common Data Service に送られると、非同期サービス キュー内に非同期処理が作成され、それがバックグラウンド プロセスを使用してそのすべての電子メール メッセージを送信します。 これでシステム パフォーマンスが向上します。  
  
 電子メール メッセージの一括送信には <xref:Microsoft.Crm.Sdk.Messages.SendBulkMailRequest> メッセージと <xref:Microsoft.Crm.Sdk.Messages.BackgroundSendEmailRequest> メッセージが使用されます。 電子メールの一括送信のシーケンスは次のとおりです。  
  
1. `SendBulkMail` 要求を実行します。 この要求は、対象となる電子メールの受信者を選択するクエリと、個々の電子メールを作成するための電子メール テンプレートで構成されます。  
  
2. 非同期サービスが受信者ごとに電子メール活動を作成します。  
  
3. 非同期サービスが各電子メール メッセージを送信します。 これらの電子メール メッセージの送信状態は "保留中" とされます。  
  
4. 電子メール ルーター、Dynamics 365 for Outlook、またはサードパーティの電子メール送信コンポーネントが Common Data Service にポーリングを行い、保留中の電子メール メッセージがないかどうかを調べます。保留中の電子メール メッセージが見つかった場合は、`BackgroundSendEmail` 要求を使用して電子メール メッセージをダウンロードします。  
  
5. `BackgroundSendEmail` 要求によって、保留中の電子メール メッセージが存在するかどうかがチェックされ、<xref:Microsoft.Crm.Sdk.Messages.BackgroundSendEmailRequest> メッセージの呼び出し元に電子メールがダウンロードされます。呼び出し元が複数の場合はダウンロードが同時に行われます。  
  
6. <xref:Microsoft.Crm.Sdk.Messages.BackgroundSendEmailRequest> メッセージの発信者は、ダウンロードされた電子メール メッセージを受け取り、送信します。  
  
<a name="E-MailAttachments"></a>   
## <a name="email-attachments"></a>電子メールの添付ファイル  
 電子メール添付ファイルとは、電子メール メッセージまたは電子メール テンプレートに添付できるファイルです。 Office Outlook ドキュメント、Office Excel スプレッドシート、CAD ファイル、PDF ファイルなど、標準形式の任意のコンピューター ファイルを添付ファイルとすることができます。 複数のファイルを電子メール添付ファイルとして電子メールまたは電子メール テンプレートに添付できます。 アップロードできる最大ファイル サイズは、**Organization.MaxUploadFileSize** プロパティによって決まります。 このプロパティは、Dynamics 365 アプリケーションの**システム設定**の**電子メール**タブで設定します。 この設定で電子メール メッセージ、メモ、および Web リソースに添付できるファイルのサイズを制限します。 既定の設定は 5 MB です。 
  
 電子メール添付ファイルを電子メール メッセージまたはテンプレートに添付するには、活動 MIME 添付ファイルを作成または更新するときに、`ActivityMimeAttachment.ObjectId` 属性と `ActivityMimeAttachment.ObjectTypeCode` 属性を使用します。  
  
 次のコード サンプルは、電子メール添付ファイルを電子メールに添付する方法を示しています。  
  
```csharp  
ActivityMimeAttachment _sampleAttachment = new ActivityMimeAttachment{  
    ObjectId = new EntityReference(Email.EntityLogicalName, _emailId),  
    ObjectTypeCode = Email.EntityLogicalName,  
    Subject = "Sample Attachment”,  
    Body = System.Convert.ToBase64String(new ASCIIEncoding().GetBytes("Example Attachment")),  
    FileName = "ExampleAttachment.txt"};  
```  
  
 同様に、電子メール添付ファイルを電子メールの代わりにテンプレートに添付するには、上記のコードに示されているように `ActivityMimeAttachment.ObjectId` 属性と `ActivityMimeAttachment.ObjectTypeCode` 属性の値を次のように置き換えます。  
  
```csharp  
ObjectId = new EntityReference(Template.EntityLogicalName, _templateId), ObjectTypeCode = Template.EntityLogicalName,  
```  
  
 電子メール アタッチメントを作成する方法の完全なサンプル コードは、[サンプル: 電子メールの添付ファイルの作成、取得、更新、および削除](/dynamics365/customer-engagement/developer/sample-create-retrieve-update-delete-email-attachment) を参照してください。  
  
### <a name="reusing-email-attachments"></a>電子メール添付ファイルの再利用  
 電子メール添付ファイル レコードを作成すると、添付ファイルはファイル BLOB として保存されます。 ファイル BLOB は、電子メール添付ファイル レコードの `ActivityMimeAttachment.AttachmentId` 属性によって一意に識別されます。 したがって、他の電子メール レコードや電子メール テンプレート レコードで添付ファイルを再利用できるため、データベースに同じファイルのコピーを複数保持する必要はありません。  
  
 既存の添付ファイルを再利用するには  
  
1.  再利用する添付ファイルを含む `ActivityMimeAttachment` レコードを取得します。次にコード例を示します。  
  
    ```csharp  
    ActivityMimeAttachment retrievedAttachment = (ActivityMimeAttachment)_serviceProxy.Retrieve(ActivityMimeAttachment.EntityLogicalName, _emailAttachmentId, new ColumnSet(true));  
    ```  
  
2.  新しい電子メール添付ファイル レコードを作成し、必要な電子メールまたは電子メール テンプレート レコードと関連付けて、取得した `ActivityMimeAttachment` レコードの添付ファイルを参照するように設定します。次にコード例を示します。  
  
    ```csharp  
    ActivityMimeAttachment _reuseAttachment = new ActivityMimeAttachment{  
        ObjectId = new EntityReference(Email.EntityLogicalName, _emailId),  
        ObjectTypeCode = Email.EntityLogicalName,  
        Subject = "Sample Attachment”,  
        AttachmentId = retrievedAttachment.AttachmentId};  
    ```  
  
     既存の添付ファイルを再利用するので、電子メール添付ファイル レコードを作成して電子メールまたは電子メール テンプレートに関連付けるときに、`ActivityMimeAttachment.Body` 属性と `ActivityMimeAttachment.FileName` 属性の値を指定する必要はありません。  
  
### <a name="see-also"></a>関連項目  
 [活動エンティティ](activity-entities.md)   
 [活動エンティティのサンプル コード](/dynamics365/customer-engagement/developer/sample-code-activity-entities)   
 [電子メール エンティティ](/reference/entities/email.md)   
 [ActivityMimeAttachment エンティティ](/reference/entities/activitymimeattachment.md)
