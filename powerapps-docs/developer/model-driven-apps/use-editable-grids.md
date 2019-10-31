---
title: モデル駆動型アプリで編集可能グリッドを使用する | Microsoft Docs
description: 編集可能グリッドは Web およびモバイル クライアント (Dynamics 365 for phones および Dynamics 365 for tablets) 上で、インライン編集機能を提供するカスタム コントロールです。これは同じグリッド内でデータをグループ化、並べ替えおよびフィルタする機能を含み、レコードやビューを切り替える必要がありません。
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: jdaly
manager: shilpas
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="use-editable-grids"></a>編集可能グリッドの使用

編集可能グリッドは Web およびモバイル クライアント (Dynamics 365 for phones および Dynamics 365 for tablets) 上で、インライン編集機能を提供するカスタム コントロールです。これは同じグリッド内でデータをグループ化、並べ替えおよびフィルタする機能を含み、レコードやビューを切り替える必要がありません。 編集可能グリッド コントロールは、Web クライアントおよびダッシュボードのフォームでのメイン グリッドやサブグリッド、およびモバイル クライアントでのフォーム グリッドでサポートされます。 編集可能グリッド コントロールでは編集機能を提供しますが、読み取り専用グリッド メターデータおよびフィールドレベルのセキュリティ設定に従います。 編集可能グリッドは、業務ルールおよびフォーム スクリプトもサポートするので、組織の要件に従ってカスタム ビジネス ロジックを適用することができます。  

> [!NOTE] 
> 従来のフォーム (Dynamics CRM 2016 より前のバージョン) を使用している場合、サブグリッドで編集可能なグリッドを有効にした場合、編集可能なサブグリッドが表示されません。 システム管理者は、必要に応じてシステム設定で従来のフォームをオフにできます。 

<a name="Enable"></a>   
## <a name="enable-editable-grids"></a>編集可能グリッドの有効化  
 編集可能グリッドを有効にして、エンティティ レベルでメイン グリッドで使用したり、またはフォーム レベルで編集可能グリッドと読み取り専用サブグリッド (関連グリッド) を置き換えることができます。  
  
 モデル駆動型アプリのカスタマイズ ツールを使用して、エンティティに対して編集可能グリッド コントロールを有効にすることができます (**設定** > **カスタマイズ**  > **システムのカスタマイズ** > **エンティティ** > *[Entity_Name]* > **コントロール**タブ。  
  
 フォームでグリッドに対して編集可能グリッドを有効にするには、フォーム エディターを開いて、編集可能グリッドに置き換えたい読み取り専用グリッドをダブルクリックしてから、**コントロール**タブで編集可能グリッドを追加または有効にします。  
  
 編集不可能なグリッドをメイン グリッドと関連グリッドに、必要に応じていつでも戻すことができます。 さらに実行時に、ユーザーは、編集可能なグリッドと読み取り専用グリッドを切り替えることができます。  
  
 詳細: [編集可能グリッドのカスタム コントロールを使用して、モデル駆動型アプリのグリッド (リスト) を編集可能にする](../../maker/model-driven-apps/make-grids-lists-editable-custom-control.md)  
  
<a name="FormScripting"></a>   
## <a name="form-scripting-support"></a>フォーム スクリプトのサポート  
 編集可能グリッドでは、クライアント側のイベントと、ビジネス ニーズに応じてカスタム クライアント拡張の作成に使用できるメソッドがサポートされています。 詳細: [モデル駆動型アプリ (クライアント API リファレンス) におけるグリッドおよびサブグリッド](clientapi/reference/grids.md)
  
<a name="EntitiesSupported"></a>   
## <a name="entities-and-views-supported-by-editable-grid"></a>編集可能グリッドでサポートされているエンティティとビュー  
 編集可能グリッドの使用がサポートされていないエンティティおよびビューもあります。  
  
 Web クライアントで、エンティティは次のすべての条件が成り立つ場合に編集可能グリッドをサポートします。  
  
- エンティティはカスタマイズ可能である (IsCustomizable = true)  
  
- エンティティが更新されている (IsAIRUpdated = true) またはユーザー定義エンティティである (IsCustomEntity = true)  
  
- エンティティは、子エンティティではない (IsChildEntity = false)  
  
  モバイル クライアントにおいてモバイル クライアントのサイトマップに表示できる場合、エンティティは編集可能グリッドをサポートします。  
  
  編集可能グリッドをサポートするエンティティの詳細については、 [編集可能グリッドのカスタム コントロールを使用して、モデル駆動型アプリのグリッド (リスト) を編集可能にする](../../maker/model-driven-apps/make-grids-lists-editable-custom-control.md)の **サポートされている標準のエンティティ** セクションを参照してください 
   
  編集可能グリッドでは、ロールアップ関連ビューはサポートされません (**ロールアップ タイプ** = `Related`)。  
  
  編集可能なコントロールのエンティティ サポート情報を表示するために、次のサンプル コードを使用して Excel を XML テーブルとして開くことができる XML ファイルを生成します。 Excel はスキーマを自動的に判断して次に示す列に情報を表示します。  
  
- `LogicalName`: エンティティの論理名。  
  
- `DisplayName`: エンティティの表示名。  
  
- `CanEnableEditableGridWeb`: 編集可能グリッドは Web クライアントでエンティティがサポートされているかどうかの状態 ("True" または "False") を表示します。  
  
- `CanEnableEditableGridMobile`: 編集可能グリッドは モバイル クライアントでエンティティがサポートされているかどうかの状態 ("True" または "False") を表示します。 (Dynamics 365 for phones および Dynamics 365 for tablets)。  
  
```csharp  
using System;  
using System.Linq;  
using System.Xml.Linq;  
using System.ServiceModel;  
using System.ServiceModel.Description;  
using System.Collections.Generic;  
using System.Xml.Serialization;  
using System.Xml;  
using System.IO;  
  
// These namespaces are found in the Microsoft.Xrm.Sdk.dll assembly  
// found in the SDK\bin folder.  
using Microsoft.Xrm.Sdk;  
using Microsoft.Xrm.Sdk.Query;  
using Microsoft.Xrm.Sdk.Metadata;  
using Microsoft.Xrm.Sdk.Client;  
using Microsoft.Xrm.Sdk.Messages;  
  
// This namespace is found in Microsoft.Crm.Sdk.Proxy.dll assembly  
// found in the SDK\bin folder.  
using Microsoft.Crm.Sdk.Messages;  
  
namespace Microsoft.Crm.Sdk.Samples  
{  
    /// <summary>  
    /// This sample generates an XML table to display the entity-support information for   
    ///  editable controls.  
    /// </summary>  
    public class DumpEditableGridEntityInfo  
    {  
        #region Class Level Members  
  
        /// <summary>  
        /// Stores the organization service proxy.  
        /// </summary>  
        OrganizationServiceProxy _serviceProxy;  
  
        // Create storage for new attributes being created  
        public List<AttributeMetadata> addedAttributes;  
  
        // Specify which language code to use in the sample. If you are using a language  
        // other than US English, you will need to modify this value accordingly.  
        // See https://msdn.microsoft.com/library/0h88fahh.aspx  
        public const int _languageCode = 1033;  
  
        // Define the IDs/variables needed for this sample.  
        public int _insertedStatusValue;  
  
        #endregion Class Level Members  
  
        #region How To Sample Code  
        /// <summary>  
        /// </summary>  
        /// <param name="serverConfig">Contains server connection information.</param>  
        /// <param name="promptForDelete">When True, the user will be prompted to delete all  
        /// created entities.</param>  
        public void Run(ServerConnection.Configuration serverConfig, bool promptForDelete)  
        {  
            try  
            {  
  
                // Connect to the Organization service.   
                // The using statement assures that the service proxy will be properly disposed.  
                using (_serviceProxy = new OrganizationServiceProxy(serverConfig.OrganizationUri, serverConfig.HomeRealmUri, serverConfig.Credentials, serverConfig.DeviceCredentials))  
                {  
                    // This statement is required to enable early-bound type support.  
                    _serviceProxy.EnableProxyTypes();  
  
                    //<snippetDumpEditableGridEntityInfo1>  
                    RetrieveAllEntitiesRequest request = new RetrieveAllEntitiesRequest()  
                    {  
                        EntityFilters = EntityFilters.Entity,  
                        RetrieveAsIfPublished = true  
                    };  
  
                    // Retrieve the MetaData.  
                    RetrieveAllEntitiesResponse response = (RetrieveAllEntitiesResponse)_serviceProxy.Execute(request);  
  
                    // Create an instance of StreamWriter to write text to a file.  
                    // The using statement also closes the StreamWriter.  
                    // To view this file, right click the file and choose open with Excel.   
                    // Excel will figure out the schema and display the information in columns.  
  
                    String filename = String.Concat("EditableGridEntityInfo.xml");  
                    using (StreamWriter sw = new StreamWriter(filename))  
                    {  
                        // Create Xml Writer.  
                        XmlTextWriter metadataWriter = new XmlTextWriter(sw);  
  
                        // Start Xml File.  
                        metadataWriter.WriteStartDocument();  
  
                        // Metadata Xml Node.  
                        metadataWriter.WriteStartElement("Metadata");  
  
                        foreach (EntityMetadata currentEntity in response.EntityMetadata)  
                        {  
                            // Start Entity Node  
                            metadataWriter.WriteStartElement("Entity");  
  
                            bool canBeDisplayedInSitemap = currentEntity.IsCustomizable.Value;  
  
                            if (canBeDisplayedInSitemap)  
                            {  
                                metadataWriter.WriteElementString("LogicalName", currentEntity.LogicalName);  
                                metadataWriter.WriteElementString("DisplayName", currentEntity.DisplayName.UserLocalizedLabel?.Label);  
                                metadataWriter.WriteElementString("CanEnableEditableGridWeb", (!(bool)currentEntity.IsChildEntity && ((bool)currentEntity.IsAIRUpdated || (bool)currentEntity.IsCustomEntity)).ToString());  
                                metadataWriter.WriteElementString("CanEnableEditableGridMobile", (currentEntity.IsVisibleInMobileClient.Value || currentEntity.IsVisibleInMobileClient.CanBeChanged).ToString());  
                            }  
  
                            // Write the Entity's Information.  
  
                            //End Entity Node  
                            metadataWriter.WriteEndElement();  
                        }  
  
                        // End Metadata Xml Node  
                        metadataWriter.WriteEndElement();  
                        metadataWriter.WriteEndDocument();  
  
                        // Close xml writer.  
                        metadataWriter.Close();  
                        Console.WriteLine("Dumped information in the EditableGridEntityInfo.xml file");  
                    }  
                }  
            }  
  
            // Catch any service fault exceptions that Microsoft Dynamics CRM throws.  
            catch (FaultException<Microsoft.Xrm.Sdk.OrganizationServiceFault>)  
            {  
                // You can handle an exception here or pass it back to the calling method.  
                throw;  
            }  
        }  
        #endregion How To Sample Code  
  
        #region Main  
        /// <summary>  
        /// Standard Main() method used by most SDK samples.  
        /// </summary>  
        /// <param name="args"></param>  
        static public void Main(string[] args)  
        {  
            try  
            {  
                // Obtain the target organization's Web address and client logon   
                // credentials from the user.  
                ServerConnection serverConnect = new ServerConnection();  
                ServerConnection.Configuration config = serverConnect.GetServerConfiguration();  
                DumpEditableGridEntityInfo app = new DumpEditableGridEntityInfo();  
                app.Run(config, false);                  
            }  
            catch (FaultException<Microsoft.Xrm.Sdk.OrganizationServiceFault> ex)  
            {  
                Console.WriteLine("The application terminated with an error.");  
                Console.WriteLine("Timestamp: {0}", ex.Detail.Timestamp);  
                Console.WriteLine("Code: {0}", ex.Detail.ErrorCode);  
                Console.WriteLine("Message: {0}", ex.Detail.Message);  
                Console.WriteLine("Plugin Trace: {0}", ex.Detail.TraceText);  
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
  
                    FaultException<Microsoft.Xrm.Sdk.OrganizationServiceFault> fe  
                        = ex.InnerException  
                        as FaultException<Microsoft.Xrm.Sdk.OrganizationServiceFault>;  
                    if (fe != null)  
                    {  
                        Console.WriteLine("Timestamp: {0}", fe.Detail.Timestamp);  
                        Console.WriteLine("Code: {0}", fe.Detail.ErrorCode);  
                        Console.WriteLine("Message: {0}", fe.Detail.Message);  
                        Console.WriteLine("Plugin Trace: {0}", fe.Detail.TraceText);  
                        Console.WriteLine("Inner Fault: {0}",  
                            null == fe.Detail.InnerFault ? "No Inner Fault" : "Has Inner Fault");  
                    }  
                }  
            }  
            // Additional exceptions to catch: SecurityTokenValidationException, ExpiredSecurityTokenException,  
            // SecurityAccessDeniedException, MessageSecurityException, and SecurityNegotiationException.  
  
            finally  
            {  
  
                Console.WriteLine("Press <Enter> to exit.");  
                Console.ReadLine();  
            }  
  
        }  
        #endregion Main  
  
    }  
}  
```  
  
### <a name="see-also"></a>関連項目  
 [モデル駆動型アプリにおけるグリッドおよびサブグリッド (クライアント API リファレンス)](clientapi/reference/grids.md)   
 [編集可能グリッドのカスタム コントロールを使用して、モデル駆動型アプリのグリッド (リスト) を編集可能にする](../../maker/model-driven-apps/make-grids-lists-editable-custom-control.md)
