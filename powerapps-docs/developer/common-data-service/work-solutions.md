---
title: ソリューションに関する作業 (Common Data Service) | MicrosoftDocs
description: ''
keywords: ''
ms.date: 10/31/2018
ms.service: powerapps
ms.custom:
  - ''
ms.topic: article
ms.assetid: 33c9da5b-27dd-d82d-1eb1-7b3b69b6032b
author: shmcarth
ms.author: jdaly
manager: ryjones
ms.reviewer: null
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---

# <a name="work-with-solutions"></a>ソリューションに関する作業

このトピックでは、「[サンプル: ソリューションに関する作業](org-service/samples/work-solutions.md)」および「[サンプル: ソリューションの依存関係の検出](org-service/samples/detect-solution-dependencies.md)」に含まれている具体的なプログラミング作業について説明します。  
  
<a name="BKMK_CreatePublisher"></a>

## <a name="create-a-publisher"></a>発行元の作成

 すべてのソリューションには、[Publisher エンティティ](reference/entities/publisher.md)で表される発行元が必要です。 ソリューションは、`Microsoft Corporation` 発行元を使用することはできませんが、組織の `Default` 発行元または新しい発行元は使用できます。  
  
 発行元には次の情報が必要です。  
  
- カスタマイズの接頭辞  
  
- 一意の名前  
  
- フレンドリ名  
  
  以下のサンプルでは、最初に発行元を定義した後、一意の名前に基づいて発行元が既に存在するかどうかを確認します。 既に存在する場合は、カスタマイズの接頭辞が変更されている可能性があるので、現在のカスタマイズの接頭辞を探して取得します。 `PublisherId` を取得することで、発行元のレコードを削除することもできます。 発行者が見つからない場合は、<xref:Microsoft.Xrm.Sdk.IOrganizationService> を使用して新しい発行者が作成されます。 <xref:Microsoft.Xrm.Sdk.IOrganizationService.Create*> メソッド 

 ```csharp
//Define a new publisher
Publisher _crmSdkPublisher = new Publisher
{
    UniqueName = "sdksamples",
    FriendlyName = "Microsoft CRM SDK Samples",
    SupportingWebsiteUrl = "https://msdn.microsoft.com/dynamics/crm/default.aspx",
    CustomizationPrefix = "sample",
    EMailAddress = "someone@microsoft.com",
    Description = "This publisher was created with samples from the Microsoft Dynamics CRM SDK"
};
//Does publisher already exist?
QueryExpression querySDKSamplePublisher = new QueryExpression
{
    EntityName = Publisher.EntityLogicalName,
    ColumnSet = new ColumnSet("publisherid", "customizationprefix"),
    Criteria = new FilterExpression()
};

querySDKSamplePublisher.Criteria.AddCondition("uniquename", ConditionOperator.Equal, _crmSdkPublisher.UniqueName);
EntityCollection querySDKSamplePublisherResults = _serviceProxy.RetrieveMultiple(querySDKSamplePublisher);
Publisher SDKSamplePublisherResults = null;
//If it already exists, use it
if (querySDKSamplePublisherResults.Entities.Count > 0)
{
    SDKSamplePublisherResults = (Publisher)querySDKSamplePublisherResults.Entities[0];
    _crmSdkPublisherId = (Guid)SDKSamplePublisherResults.PublisherId;
    _customizationPrefix = SDKSamplePublisherResults.CustomizationPrefix;
}
//If it doesn't exist, create it
if (SDKSamplePublisherResults == null)
{
    _crmSdkPublisherId = _serviceProxy.Create(_crmSdkPublisher);
    Console.WriteLine(String.Format("Created publisher: {0}.", _crmSdkPublisher.FriendlyName));
    _customizationPrefix = _crmSdkPublisher.CustomizationPrefix;
}
``` 
  
<a name="BKMK_RetrieveDefaultPublisher"></a>
   
## <a name="retrieve-the-default-publisher"></a>既定の発行元の取得  

このサンプルは既定の発行者を取得する方法を示します。 既定の発行元の不変 GUID 値は `d21aab71-79e7-11dd-8874-00188b01e34f` です。  

```csharp
// Retrieve the Default Publisher

//The default publisher has a constant GUID value;
Guid DefaultPublisherId = new Guid("{d21aab71-79e7-11dd-8874-00188b01e34f}");

Publisher DefaultPublisher = (Publisher)_serviceProxy.Retrieve(Publisher.EntityLogicalName, DefaultPublisherId, new ColumnSet(new string[] {"friendlyname" }));

EntityReference DefaultPublisherReference = new EntityReference
{
    Id = DefaultPublisher.Id,
    LogicalName = Publisher.EntityLogicalName,
    Name = DefaultPublisher.FriendlyName
};
Console.WriteLine("Retrieved the {0}.", DefaultPublisherReference.Name);
```
  
<a name="BKMK_CreateASolution"></a>
 
## <a name="create-a-solution"></a>ソリューションの作成

 以下のサンプルでは、「[発行元の作成](work-solutions.md#BKMK_CreatePublisher)」で作成された SDK サンプル発行者を使用してアンマネージド ソリューションを作成する方法を示します。  
  
 ソリューションには次の情報が必要です。  
  
- 発行元  
  
- フレンドリ名  
  
- 一意の名前  
  
- バージョン番号  
  
  変数 `_crmSdkPublisherId` は、`publisherid` の値を表す GUID 値です。  
  
  このサンプルでは、一意の名前を基にして組織内にソリューションが既に存在するかどうかを調べます。 ソリューションが存在しない場合は作成します。 ソリューションを削除できるように、`SolutionId` の値を取得します。  
  
 ```csharp
  // Create a Solution
//Define a solution
Solution solution = new Solution
{
    UniqueName = "samplesolution",
    FriendlyName = "Sample Solution",
    PublisherId = new EntityReference(Publisher.EntityLogicalName, _crmSdkPublisherId),
    Description = "This solution was created by the WorkWithSolutions sample code in the Microsoft Dynamics CRM SDK samples.",
    Version = "1.0"
};

//Check whether it already exists
QueryExpression queryCheckForSampleSolution = new QueryExpression
{
    EntityName = Solution.EntityLogicalName,
    ColumnSet = new ColumnSet(),
    Criteria = new FilterExpression()
};
queryCheckForSampleSolution.Criteria.AddCondition("uniquename", ConditionOperator.Equal, solution.UniqueName);

//Create the solution if it does not already exist.
EntityCollection querySampleSolutionResults = _serviceProxy.RetrieveMultiple(queryCheckForSampleSolution);
Solution SampleSolutionResults = null;
if (querySampleSolutionResults.Entities.Count > 0)
{
    SampleSolutionResults = (Solution)querySampleSolutionResults.Entities[0];
    _solutionsSampleSolutionId = (Guid)SampleSolutionResults.SolutionId;
}
if (SampleSolutionResults == null)
{
    _solutionsSampleSolutionId = _serviceProxy.Create(solution);
}
  ```
  
<a name="BKMK_RetrieveASolution"></a> 
  
## <a name="retrieve-a-solution"></a>ソリューションの取得  

特定のソリューションを取得するには、ソリューションの `UniqueName` を使用します。 各組織には既定のソリューションがあり、その不変 GUID 値は `FD140AAF-4DF4-11DD-BD17-0019B9312238` です。  
  
このサンプルでは、一意の名前 ”samplesolution” のソリューション用にデータを取得する方法を示します。 この名前のソリューションは、「[ソリューションの作成](work-solutions.md#BKMK_CreateASolution)」で作成されます。  
  
 ```csharp
 // Retrieve a solution
String solutionUniqueName = "samplesolution";
QueryExpression querySampleSolution = new QueryExpression
{
    EntityName = Solution.EntityLogicalName,
    ColumnSet = new ColumnSet(new string[] { "publisherid", "installedon", "version", "versionnumber", "friendlyname" }),
    Criteria = new FilterExpression()
};

querySampleSolution.Criteria.AddCondition("uniquename", ConditionOperator.Equal, solutionUniqueName);
Solution SampleSolution = (Solution)_serviceProxy.RetrieveMultiple(querySampleSolution).Entities[0];
 ``` 
  
<a name="BKMK_AddANewSolutionComponent"></a> 
  
## <a name="add-a-new-solution-component"></a>新しいソリューション コンポーネントの追加 
 
このサンプルでは、特定のソリューションに関連付けられたソリューション コンポーネントの作成方法を示します。 ソリューション コンポーネントを作成したときに、特定のソリューションと関連付けないと、コンポーネントは既定のソリューションだけに追加され、手動でコンポーネントをソリューションに追加するか、または「[既存のソリューション コンポーネントの追加](work-solutions.md#BKMK_AddExistingSolutionComponent)」で示されているコードを使用する必要が生じます。  
  
 このコードでは、新しいグローバル オプション セットを作成し、一意の名前が `_primarySolutionName` であるソリューションに追加します。  
  
 ```csharp
 OptionSetMetadata optionSetMetadata = new OptionSetMetadata()
{
    Name = _globalOptionSetName,
    DisplayName = new Label("Example Option Set", _languageCode),
    IsGlobal = true,
    OptionSetType = OptionSetType.Picklist,
    Options =
{
    new OptionMetadata(new Label("Option 1", _languageCode), 1),
    new OptionMetadata(new Label("Option 2", _languageCode), 2)
}
};
CreateOptionSetRequest createOptionSetRequest = new CreateOptionSetRequest
{
    OptionSet = optionSetMetadata                
};

createOptionSetRequest.SolutionUniqueName = _primarySolutionName;
_serviceProxy.Execute(createOptionSetRequest);
 ```  
  
<a name="BKMK_AddExistingSolutionComponent"></a>  
 
## <a name="add-an-existing-solution-component"></a>既存のソリューション コンポーネントの追加  

このサンプルは、ソリューションに既存のソリューション コンポーネントを追加する方法を示します。  
  
次のコードでは、<xref:Microsoft.Crm.Sdk.Messages.AddSolutionComponentRequest> を使用して、`Account` エンティティをアンマネージド ソリューションにソリューション コンポーネントとして追加します。  
  
 ```csharp
 // Add an existing Solution Component
//Add the Account entity to the solution
RetrieveEntityRequest retrieveForAddAccountRequest = new RetrieveEntityRequest()
{
    LogicalName = Account.EntityLogicalName
};
RetrieveEntityResponse retrieveForAddAccountResponse = (RetrieveEntityResponse)_serviceProxy.Execute(retrieveForAddAccountRequest);
AddSolutionComponentRequest addReq = new AddSolutionComponentRequest()
{
    ComponentType = (int)componenttype.Entity,
    ComponentId = (Guid)retrieveForAddAccountResponse.EntityMetadata.MetadataId,
    SolutionUniqueName = solution.UniqueName
};
_serviceProxy.Execute(addReq);
``` 
  
<a name="BKMK_RemoveSolutionComponent"></a>  
 
## <a name="remove-a-solution-component"></a>ソリューション コンポーネントの削除  

このサンプルは、アンマネージド ソリューションからソリューション コンポーネントを削除する方法を示します。 次のコードでは、<xref:Microsoft.Crm.Sdk.Messages.RemoveSolutionComponentRequest> を使用して、エンティティ ソリューション コンポーネントをアンマネージド ソリューションから削除します。 `solution.UniqueName` は、「[ソリューションの作成](work-solutions.md#BKMK_CreateASolution)」で作成したソリューションを参照します。  
  
 ```csharp
 // Remove a Solution Component
//Remove the Account entity from the solution
RetrieveEntityRequest retrieveForRemoveAccountRequest = new RetrieveEntityRequest()
{
    LogicalName = Account.EntityLogicalName
};
RetrieveEntityResponse retrieveForRemoveAccountResponse = (RetrieveEntityResponse)_serviceProxy.Execute(retrieveForRemoveAccountRequest);

RemoveSolutionComponentRequest removeReq = new RemoveSolutionComponentRequest()
{
    ComponentId = (Guid)retrieveForRemoveAccountResponse.EntityMetadata.MetadataId,
    ComponentType = (int)componenttype.Entity,
    SolutionUniqueName = solution.UniqueName
};
_serviceProxy.Execute(removeReq);
```
  
<a name="BKMK_ExportPackageSolution"></a>
   
## <a name="export-or-package-a-solution"></a>ソリューションのエクスポートまたはパッケージ化  

このサンプルでは、アンマネージド ソリューションのエクスポートまたはパッケージの方法を示します。 このコードでは、<xref:Microsoft.Crm.Sdk.Messages.ExportSolutionRequest> を使用して、アンマネージド ソリューションを表す圧縮されたファイルをエクスポートします。 マネージド ソリューションを作成するためのオプションは、<xref:Microsoft.Crm.Sdk.Messages.ExportSolutionRequest.Managed> プロパティを使用して設定します。 このサンプルでは、*samplesolution.zip* という名前のファイルを `c:\temp\` フォルダーに保存します。  
  
```csharp
// Export or package a solution
//Export an a solution

ExportSolutionRequest exportSolutionRequest = new ExportSolutionRequest();
exportSolutionRequest.Managed = false;
exportSolutionRequest.SolutionName = solution.UniqueName;

ExportSolutionResponse exportSolutionResponse = (ExportSolutionResponse)_serviceProxy.Execute(exportSolutionRequest);

byte[] exportXml = exportSolutionResponse.ExportSolutionFile;
string filename = solution.UniqueName + ".zip";
File.WriteAllBytes(outputDir + filename, exportXml);

Console.WriteLine("Solution exported to {0}.", outputDir + filename);
``` 

<a name="BKMK_InstallUpgradeSolution"></a>  
 
## <a name="install-or-upgrade-a-solution"></a>ソリューションのインストールまたはアップグレード  

このサンプルは、<xref:Microsoft.Crm.Sdk.Messages.ImportSolutionRequest> メッセージを使用してソリューションインストールまたはアップグレードするする方法を説明します。  
  
`ImportJob` エンティティを使用すると、成功したインポートについてのデータを取得できます。  
  
以下のサンプルは、成功したかどうかを追跡せずにソリューションをインポートする方法を示します。  
  
 ```csharp
 // Install or Upgrade a Solution                  

byte[] fileBytes = File.ReadAllBytes(ManagedSolutionLocation);

ImportSolutionRequest impSolReq = new ImportSolutionRequest()
{
    CustomizationFile = fileBytes
};

_serviceProxy.Execute(impSolReq);

Console.WriteLine("Imported Solution from {0}", ManagedSolutionLocation);
 ```  
  
### <a name="tracking-import-success"></a>インポートの成功の追跡

 `ImportSolutionRequest` に対して <xref:Microsoft.Crm.Sdk.Messages.ImportSolutionRequest.ImportJobId> を指定すると、その値を使用してインポートの状態を `ImportJob` エンティティにクエリできます。  
  
 `ImportJobId` を使用すると、<xref:Microsoft.Crm.Sdk.Messages.RetrieveFormattedImportJobResultsRequest> メッセージを使用してインポート ログ ファイルをダウンロードすることもできます。  
  
#### <a name="retrieving-import-job-data"></a>インポート ジョブ データの取得

 以下のサンプルは、インポート ジョブ レコードおよび `ImportJob.Data` 属性の内容を取得する方法を示します。  
  
```csharp
// Monitor import success
byte[] fileBytesWithMonitoring = File.ReadAllBytes(ManagedSolutionLocation);

ImportSolutionRequest impSolReqWithMonitoring = new ImportSolutionRequest()
{
    CustomizationFile = fileBytes,
    ImportJobId = Guid.NewGuid()
};

_serviceProxy.Execute(impSolReqWithMonitoring);
Console.WriteLine("Imported Solution with Monitoring from {0}", ManagedSolutionLocation);

ImportJob job = (ImportJob)_serviceProxy.Retrieve(ImportJob.EntityLogicalName, impSolReqWithMonitoring.ImportJobId, new ColumnSet(new System.String[] { "data", "solutionname" }));


System.Xml.XmlDocument doc = new System.Xml.XmlDocument();
doc.LoadXml(job.Data);

String ImportedSolutionName = doc.SelectSingleNode("//solutionManifest/UniqueName").InnerText;
String SolutionImportResult = doc.SelectSingleNode("//solutionManifest/result/@result").Value;

Console.WriteLine("Report from the ImportJob data");
Console.WriteLine("Solution Unique name: {0}", ImportedSolutionName);
Console.WriteLine("Solution Import Result: {0}", SolutionImportResult);
Console.WriteLine("");

// This code displays the results for Global Option sets installed as part of a solution.

System.Xml.XmlNodeList optionSets = doc.SelectNodes("//optionSets/optionSet");
foreach (System.Xml.XmlNode node in optionSets)
{
    string OptionSetName = node.Attributes["LocalizedName"].Value;
    string result = node.FirstChild.Attributes["result"].Value;

    if (result == "success")
    {
        Console.WriteLine("{0} result: {1}",OptionSetName, result);
    }
    else
    {
        string errorCode = node.FirstChild.Attributes["errorcode"].Value;
        string errorText = node.FirstChild.Attributes["errortext"].Value;

        Console.WriteLine("{0} result: {1} Code: {2} Description: {3}",OptionSetName, result, errorCode, errorText);
    }
}
```   
  
`Data` プロパティの内容は XML ファイルを表す文字列です。 このサンプルのコードを使用して取得されるもののサンプルを次に示します。 このマネージド ソリューションには、`sample_tempsampleglobaloptionsetname` という名前のグローバル オプション セットが 1 つ含まれていました。  
  
```xml  
<importexportxml start="634224017519682730"  
                 stop="634224017609764033"  
                 progress="80"  
                 processed="true">  
 <solutionManifests>  
  <solutionManifest languagecode="1033"  
                    id="samplesolutionforImport"  
                    LocalizedName="Sample Solution for Import"  
                    processed="true">  
   <UniqueName>samplesolutionforImport</UniqueName>  
   <LocalizedNames>  
    <LocalizedName description="Sample Solution for Import"  
                   languagecode="1033" />  
   </LocalizedNames>  
   <Descriptions>  
    <Description description="This solution was created by the WorkWithSolutions sample code in the Microsoft CRM SDK samples."  
                 languagecode="1033" />  
   </Descriptions>  
   <Version>1.0</Version>  
   <Managed>1</Managed>  
   <Publisher>  
    <UniqueName>sdksamples</UniqueName>  
    <LocalizedNames>  
     <LocalizedName description="Microsoft CRM SDK Samples"  
                    languagecode="1033" />  
    </LocalizedNames>  
    <Descriptions>  
     <Description description="This publisher was created with samples from the Microsoft CRM SDK"  
                  languagecode="1033" />  
    </Descriptions>  
    <EMailAddress>someone@microsoft.com</EMailAddress>  
    <SupportingWebsiteUrl>https://msdn.microsoft.com/dynamics/crm/default.aspx</SupportingWebsiteUrl>  
    <Addresses>  
     <Address>  
      <City />  
      <Country />  
      <Line1 />  
      <Line2 />  
      <PostalCode />  
      <StateOrProvince />  
      <Telephone1 />  
     </Address>  
    </Addresses>  
   </Publisher>  
   <results />  
   <result result="success"  
           errorcode="0"  
           errortext=""  
           datetime="20:49:12.08"  
           datetimeticks="634224269520845122" />  
  </solutionManifest>  
 </solutionManifests>  
 <upgradeSolutionPackageInformation>  
  <upgradeRequired>0</upgradeRequired>  
  <upgradeValid>1</upgradeValid>  
  <fileVersion>5.0.9669.0</fileVersion>  
  <currentVersion>5.0.9669.0</currentVersion>  
  <fileSku>OnPremise</fileSku>  
  <currentSku>OnPremise</currentSku>  
 </upgradeSolutionPackageInformation>  
 <entities />  
 <nodes />  
 <settings />  
 <dashboards />  
 <securityroles />  
 <workflows />  
 <templates />  
 <optionSets>  
  <optionSet id="sample_tempsampleglobaloptionsetname"  
             LocalizedName="Example Option Set"  
             Description=""  
             processed="true">  
   <result result="success"  
           errorcode="0"  
           errortext=""  
           datetime="20:49:16.10"  
           datetimeticks="634224269561025400" />  
  </optionSet>  
 </optionSets>  
 <ConnectionRoles />  
 <SolutionPluginAssemblies />  
 <SdkMessageProcessingSteps />  
 <ServiceEndpoints />  
 <webResources />  
 <reports />  
 <FieldSecurityProfiles />  
 <languages>  
  <language>  
   <result result="success"  
           errorcode="0"  
           errortext=""  
           datetime="20:49:12.00"  
           datetimeticks="634224269520092986" />  
  </language>  
 </languages>  
 <entitySubhandlers />  
 <publishes>  
  <publish processed="false" />  
 </publishes>  
 <rootComponents>  
  <rootComponent processed="true">  
   <result result="success"  
           errorcode="0"  
           errortext=""  
           datetime="20:49:20.83"  
           datetimeticks="634224269608387238" />  
  </rootComponent>  
 </rootComponents>  
 <dependencies>  
  <dependency processed="true">  
   <result result="success"  
           errorcode="0"  
           errortext=""  
           datetime="20:49:20.97"  
           datetimeticks="634224269609715208" />  
  </dependency>  
 </dependencies>  
</importexportxml>  
```  
  
<a name="BKMK_DeleteSolution"></a>

## <a name="delete-a-solution"></a>ソリューションの削除

 このサンプルはソリューションを削除する方法を示します。次のサンプルは、ソリューション `uniquename` を使用してソリューションを取得し、結果から `solutionid` を抽出します。 `solutionid` を <xref:Microsoft.Xrm.Sdk.IOrganizationService> で使用します。 <xref:Microsoft.Xrm.Sdk.IOrganizationService.Delete*> メソッド。  
  
```csharp
// Delete a solution

QueryExpression queryImportedSolution = new QueryExpression
{
    EntityName = Solution.EntityLogicalName,
    ColumnSet = new ColumnSet(new string[] { "solutionid", "friendlyname" }),
    Criteria = new FilterExpression()
};


queryImportedSolution.Criteria.AddCondition("uniquename", ConditionOperator.Equal, ImportedSolutionName);

Solution ImportedSolution = (Solution)_serviceProxy.RetrieveMultiple(queryImportedSolution).Entities[0];

_serviceProxy.Delete(Solution.EntityLogicalName, (Guid)ImportedSolution.SolutionId);

Console.WriteLine("Deleted the {0} solution.", ImportedSolution.FriendlyName);
```  
  
<a name="BKMK_DetectSolutionDependencies"></a>

## <a name="detect-solution-dependencies"></a>ソリューションの依存関係の検出

 このサンプルは、ソリューション コンポーネント間の依存関係を示すレポートを作成する方法を示します。  
  
 このコードでは次のことを行います。  
  
- ソリューションのすべてのコンポーネントを取得します。  
  
- 各コンポーネントのすべての依存関係を取得します。  
  
- 検出された各依存関係について、依存関係を説明するレポートを表示します。  
  
```csharp
// Grab all Solution Components for a solution.
QueryByAttribute componentQuery = new QueryByAttribute
{
    EntityName = SolutionComponent.EntityLogicalName,
    ColumnSet = new ColumnSet("componenttype", "objectid", "solutioncomponentid", "solutionid"),
    Attributes = { "solutionid" },

    // In your code, this value would probably come from another query.
    Values = { _primarySolutionId }
};

IEnumerable<SolutionComponent> allComponents =
    _serviceProxy.RetrieveMultiple(componentQuery).Entities.Cast<SolutionComponent>();

foreach (SolutionComponent component in allComponents)
{
    // For each solution component, retrieve all dependencies for the component.
    RetrieveDependentComponentsRequest dependentComponentsRequest =
        new RetrieveDependentComponentsRequest
        {
            ComponentType = component.ComponentType.Value,
            ObjectId = component.ObjectId.Value
        };
    RetrieveDependentComponentsResponse dependentComponentsResponse =
        (RetrieveDependentComponentsResponse)_serviceProxy.Execute(dependentComponentsRequest);

    // If there are no dependent components, we can ignore this component.
    if (dependentComponentsResponse.EntityCollection.Entities.Any() == false)
        continue;

    // If there are dependencies upon this solution component, and the solution
    // itself is managed, then you will be unable to delete the solution.
    Console.WriteLine("Found {0} dependencies for Component {1} of type {2}",
        dependentComponentsResponse.EntityCollection.Entities.Count,
        component.ObjectId.Value,
        component.ComponentType.Value
        );
    //A more complete report requires more code
    foreach (Dependency d in dependentComponentsResponse.EntityCollection.Entities)
    {
        DependencyReport(d);
    }
}
``` 
  
  `DependencyReport` メソッドについては次のコード サンプルで示します。  
  
### <a name="dependency-report"></a>依存関係レポート

 `DependencyReport` メソッドは、依存関係で見つかった情報を基にして、よりわかりやすいメッセージを提供します。  
  
> [!NOTE]
>  このサンプルでは、メソッドは部分的にのみ実装されています。 属性およびオプション セット ソリューション コンポーネントについてのみメッセージを表示できます。  
  
```csharp
/// <summary>
   /// Shows how to get a more friendly message based on information within the dependency
   /// <param name="dependency">A Dependency returned from the RetrieveDependentComponents message</param>
   /// </summary> 
public void DependencyReport(Dependency dependency)
   {
 //These strings represent parameters for the message.
    String dependentComponentName = "";
    String dependentComponentTypeName = "";
    String dependentComponentSolutionName = "";
    String requiredComponentName = "";
    String requiredComponentTypeName = "";
    String requiredComponentSolutionName = "";

 //The ComponentType global Option Set contains options for each possible component.
    RetrieveOptionSetRequest componentTypeRequest = new RetrieveOptionSetRequest
    {
     Name = "componenttype"
    };

    RetrieveOptionSetResponse componentTypeResponse = (RetrieveOptionSetResponse)_serviceProxy.Execute(componentTypeRequest);
    OptionSetMetadata componentTypeOptionSet = (OptionSetMetadata)componentTypeResponse.OptionSetMetadata;
 // Match the Component type with the option value and get the label value of the option.
    foreach (OptionMetadata opt in componentTypeOptionSet.Options)
    {
     if (dependency.DependentComponentType.Value == opt.Value)
     {
      dependentComponentTypeName = opt.Label.UserLocalizedLabel.Label;
     }
     if (dependency.RequiredComponentType.Value == opt.Value)
     {
      requiredComponentTypeName = opt.Label.UserLocalizedLabel.Label;
     }
    }
 //The name or display name of the compoent is retrieved in different ways depending on the component type
    dependentComponentName = getComponentName(dependency.DependentComponentType.Value, (Guid)dependency.DependentComponentObjectId);
    requiredComponentName = getComponentName(dependency.RequiredComponentType.Value, (Guid)dependency.RequiredComponentObjectId);

 // Retrieve the friendly name for the dependent solution.
    Solution dependentSolution = (Solution)_serviceProxy.Retrieve
     (
      Solution.EntityLogicalName,
      (Guid)dependency.DependentComponentBaseSolutionId,
      new ColumnSet("friendlyname")
     );
    dependentComponentSolutionName = dependentSolution.FriendlyName;
    
 // Retrieve the friendly name for the required solution.
    Solution requiredSolution = (Solution)_serviceProxy.Retrieve
      (
       Solution.EntityLogicalName,
       (Guid)dependency.RequiredComponentBaseSolutionId,
       new ColumnSet("friendlyname")
      );
    requiredComponentSolutionName = requiredSolution.FriendlyName;

 //Display the message
     Console.WriteLine("The {0} {1} in the {2} depends on the {3} {4} in the {5} solution.",
     dependentComponentName,
     dependentComponentTypeName,
     dependentComponentSolutionName,
     requiredComponentName,
     requiredComponentTypeName,
     requiredComponentSolutionName);
   }
```
  
### <a name="detect-whether-a-solution-component-may-be-delete"></a>ソリューション コンポーネントが削除されるかどうかの検出

 <xref:Microsoft.Crm.Sdk.Messages.RetrieveDependenciesForDeleteRequest> メッセージを使用して、特定のソリューション コンポーネントが削除されるのを防ぐ他のソリューション コンポーネントを識別します。 次のコード サンプルは、既知のグローバル オプションセットを使用して属性を検索します。 グローバル オプションセットを使用する属性は、グローバル オプションセットが削除されることを防ぎます。  
  
```csharp
// Use the RetrieveOptionSetRequest message to retrieve  
// a global option set by it's name.
RetrieveOptionSetRequest retrieveOptionSetRequest =
    new RetrieveOptionSetRequest
    {
     Name = _globalOptionSetName
    };

// Execute the request.
RetrieveOptionSetResponse retrieveOptionSetResponse =
    (RetrieveOptionSetResponse)_serviceProxy.Execute(
    retrieveOptionSetRequest);
_globalOptionSetId = retrieveOptionSetResponse.OptionSetMetadata.MetadataId;
if (_globalOptionSetId != null)
{ 
 //Use the global OptionSet MetadataId with the appropriate componenttype
 // to call RetrieveDependenciesForDeleteRequest
 RetrieveDependenciesForDeleteRequest retrieveDependenciesForDeleteRequest = new RetrieveDependenciesForDeleteRequest 
{ 
 ComponentType = (int)componenttype.OptionSet,
 ObjectId = (Guid)_globalOptionSetId
};

 RetrieveDependenciesForDeleteResponse retrieveDependenciesForDeleteResponse =
  (RetrieveDependenciesForDeleteResponse)_serviceProxy.Execute(retrieveDependenciesForDeleteRequest);
 Console.WriteLine("");
 foreach (Dependency d in retrieveDependenciesForDeleteResponse.EntityCollection.Entities)
 {

  if (d.DependentComponentType.Value == 2)//Just testing for Attributes
  {
   String attributeLabel = "";
   RetrieveAttributeRequest retrieveAttributeRequest = new RetrieveAttributeRequest
   {
    MetadataId = (Guid)d.DependentComponentObjectId
   };
   RetrieveAttributeResponse retrieveAttributeResponse = (RetrieveAttributeResponse)_serviceProxy.Execute(retrieveAttributeRequest);

   AttributeMetadata attmet = retrieveAttributeResponse.AttributeMetadata;

   attributeLabel = attmet.DisplayName.UserLocalizedLabel.Label;
  
    Console.WriteLine("An {0} named {1} will prevent deleting the {2} global option set.", 
   (componenttype)d.DependentComponentType.Value, 
   attributeLabel, 
   _globalOptionSetName);
  }
 }                 
}
``` 

### <a name="see-also"></a>関連項目

 [Dynamics 365 ソリューションを使用した拡張機能のパッケージ化および配布](/dynamics365/customer-engagement/developer/package-distribute-extensions-use-solutions)   
 [ソリューションの概要](introduction-solutions.md)   
 [ソリューション開発の計画](/dynamics365/customer-engagement/developer/plan-solution-development)   
 [ソリューション コンポーネントの依存関係の追跡](dependency-tracking-solution-components.md)   
 [アンマネージド ソリューションの作成、エクスポート、またはインポート](create-export-import-unmanaged-solution.md)   
 [マネージド ソリューションの作成、インストール、および更新](create-install-update-managed-solution.md)   
 [ソリューションのアンインストールまたは削除](uninstall-delete-solution.md)   
 [ソリューション エンティティ](/dynamics365/customer-engagement/developer/solution-entities)   
 [サンプル: ソリューションに関する作業](org-service/samples/work-solutions.md) [サンプル: ソリューションの依存関係の検出](/dynamics365/customer-engagement/developer/sample-detect-solution-dependencies)
