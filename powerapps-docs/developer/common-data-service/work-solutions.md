---
title: Verwenden von Lösungen (Common Data Service) | MicrosoftDocs
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

# <a name="work-with-solutions"></a>Mit Lösungen arbeiten

In diesem Thema werden die bestimmten Programmieraufgaben dargestellt, die in [Beispiel: Verwenden von Lösungen](org-service/samples/work-solutions.md) und [Beispiel: Erkennen von Lösungsabhängigkeiten](org-service/samples/detect-solution-dependencies.md) enthalten sind.  
  
<a name="BKMK_CreatePublisher"></a>

## <a name="create-a-publisher"></a>Erstellen eines Herausgebers

 Jede Lösung erfordert einen Herausgeber, repräsentiert durch die [Publisher-Entität](reference/entities/publisher.md). Eine Lösung kann den Herausgeber `Microsoft Corporation` nicht verwenden sie kann aber den Herausgeber `Default` für die Organisation oder einen neuen Herausgeber verwenden  
  
 Ein Herausgeber erfordert Folgendes:  
  
- Ein Anpassungspräfix  
  
- Einen eindeutigen Namen  
  
- Einen Anzeigenamen  
  
  Das folgende Bespiel definiert zunächst einen Herausgeber und prüft dann aufgrund des eindeutigen Namens, ob dieser Herausgeber bereits vorhanden ist. Falls er bereits vorhanden ist, wurde möglicherweise das Anpassungspräfix geändert, dieses Beispiel versucht also, das aktuelle Anpassungspräfix zu erfassen. Die `PublisherId` wird ebenfalls erfasst, so dass der Herausgeberdatensatz gelöscht werden kann. Wenn der Herausgeber nicht gefunden wird, wird ein neuer Herausgeber mit der <xref:Microsoft.Xrm.Sdk.IOrganizationService>-Methode erstellt. <xref:Microsoft.Xrm.Sdk.IOrganizationService.Create*> Methode 

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
## <a name="retrieve-the-default-publisher"></a>Abrufen des Standardherausgebers  
 Dieses Beispiel zeigt, wie der Standardherausgeber abgerufen wird. Der Standardherausgeber hat einen konstanten GUID-Wert: `d21aab71-79e7-11dd-8874-00188b01e34f`.  
  
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
 
## <a name="create-a-solution"></a>Erstellen einer Lösung

 Das folgende Beispiel zeigt, wie Sie eine nicht verwaltete Lösung mithilfe des in [Erstellen eines Herausgebers](work-solutions.md#BKMK_CreatePublisher) erstellten SDK-Beispielherausgebers erstellen.  
  
 Eine Lösung erfordert Folgendes:  
  
- Einen Herausgeber  
  
- Einen Anzeigenamen  
  
- Einen eindeutigen Namen  
  
- Eine Versionsnummer  
  
  Die Variable `_crmSdkPublisherId` ist ein GUID-Wert, der den `publisherid`-Wert repräsentiert.  
  
  Dieses Beispiel überprüft anhand des eindeutigen Namens, ob die Lösung in der Organisation bereits vorhanden ist. Wenn dies nicht der Fall ist, wird sie erstellt. Der `SolutionId`-Wert wird erfasst, so dass die Lösung gelöscht werden kann.  
  
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
## <a name="retrieve-a-solution"></a>Abrufen einer Lösung  
 Um eine bestimmte Lösung abzurufen, können Sie den `UniqueName` der Lösung verwenden. Jede Organisation hat eine Standardlösung mit einem konstanten GUID-Wert: `FD140AAF-4DF4-11DD-BD17-0019B9312238`.  
  
 Dieses Beispiel zeigt, wie Daten für eine Lösung mit dem eindeutigen Namen "samplesolution" abgerufen werden. Eine Lösung mit diesem Namen wird unter [Erstellen einer Lösung](work-solutions.md#BKMK_CreateASolution) erstellt.  
  
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
## <a name="add-a-new-solution-component"></a>Hinzufügen einer neuen Lösungskomponente  
 Dieses Beispiel zeigt, wie eine Lösungskomponente erstellt wird, die mit einer bestimmten Lösung verbunden ist. Wenn Sie die Lösungskomponente nicht mit einer bestimmten Lösung verbinden, wenn sie erstellt wird, wird sie nur der Standardlösung hinzugefügt, und Sie müssen sie manuell einer Lösung hinzufügen, wobei Sie den Code verwenden, der in [Eine vorhandene Lösungskomponente](work-solutions.md#BKMK_AddExistingSolutionComponent) enthalten ist.  
  
 Dieser Code erstellt einen neuen globalen Optionssatz und fügt ihn der Lösung mit dem eindeutigen Namen `_primarySolutionName` hinzu.  
  
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
## <a name="add-an-existing-solution-component"></a>Hinzufügen einer vorhandenen Lösungskomponente  
 Dieses Beispiel zeigt, wie einer Lösungskomponente eine vorhandene Lösung hinzugefügt wird.  
  
 Der folgende Code verwendet die <xref:Microsoft.Crm.Sdk.Messages.AddSolutionComponentRequest> zum Hinzufügen der `Account`-Entität als  Lösungskomponente zu einer nicht verwalteten Lösung.  
  
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
## <a name="remove-a-solution-component"></a>Entfernen einer Lösungskomponente  
 Dieses Beispiel zeigt, wie eine Lösungskomponente von einer nicht verwalteten Lösung entfernt wird. Der folgende Code verwendet die <xref:Microsoft.Crm.Sdk.Messages.RemoveSolutionComponentRequest> zum Entfernen einer Entitätslösungskomponente von einer nicht verwalteten Lösung. `solution.UniqueName` verweist auf die Lösung, die in [Erstellen einer Lösung](work-solutions.md#BKMK_CreateASolution) erstellt wird.  
  
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
## <a name="export-or-package-a-solution"></a>Exportieren oder Packen einer Lösung  
 Dieses Beispiel zeigt, wie eine nicht verwaltete Lösung exportiert oder eine verwaltete Lösung gepackt wird. Der Code verwendet <xref:Microsoft.Crm.Sdk.Messages.ExportSolutionRequest>, um eine komprimierte Datei zu exportieren, die eine nicht verwalte Lösung repräsentiert. Die Option zur Erstellung einer verwalteten Lösung wird mit der <xref:Microsoft.Crm.Sdk.Messages.ExportSolutionRequest.Managed>-Eigenschaft festgelegt. In diesem Beispiel wird eine Datei mit dem Namen samplesolution.zip im `c:\temp\`-Ordner gespeichert.  
  
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
## <a name="install-or-upgrade-a-solution"></a>Installieren oder Aktualisieren einer Lösung  
 Dieses Beispiel veranschaulicht, wie Sie mithilfe der Meldung <xref:Microsoft.Crm.Sdk.Messages.ImportSolutionRequest> eine Lösung installieren oder aktualisieren.  
  
 Mit der `ImportJob`-Entität können Sie Daten zum Erfolg des Imports erfassen.  
  
 Das folgende Beispiel zeigt, wie Sie eine Lösung importieren, ohne den Erfolg nachzuverfolgen.  
  
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
  
### <a name="tracking-import-success"></a>Nachverfolgen des Importerfolgs
 Wenn Sie eine <xref:Microsoft.Crm.Sdk.Messages.ImportSolutionRequest.ImportJobId> für die  `ImportSolutionRequest` angegeben haben, können Sie diesen Wert verwenden, um `ImportJob` nach dem Status des Imports abzufragen.  
  
 Die `ImportJobId` kann auch für den Download einer Importprotokolldatei mit der <xref:Microsoft.Crm.Sdk.Messages.RetrieveFormattedImportJobResultsRequest>-Meldung verwendet werden.  
  
#### <a name="retrieving-import-job-data"></a>Abrufen von Importauftragsdaten

 Das folgende Beispiel zeigt, wie Sie den Datensatz für den Importauftrag und den Inhalt des `ImportJob.Data`-Attributs abrufen.  
  
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
  
 Der Inhalt der Eigenschaft `Data` eine Zeichenfolge, die eine XML-Datei repräsentiert. Im Folgenden finden Sie ein Beispiel, das mithilfe des Codes in diesem Beispiel erfasst wurde. Diese verwaltete Lösung enthielt einen einzelnen globalen Optionssatz mit dem Namen `sample_tempsampleglobaloptionsetname`.  
  
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

## <a name="delete-a-solution"></a>Löschen einer Lösung

 Dieses Beispiel zeigt, wie Sie eine Lösung löschen. Das folgende Beispiel zeigt, wie Sie eine Lösung mit der Lösung `uniquename` abrufen und dann die  `solutionid` aus den Ergebnissen extrahieren. Verwenden Sie die `solutionid` mit der <xref:Microsoft.Xrm.Sdk.IOrganizationService>-Methode. <xref:Microsoft.Xrm.Sdk.IOrganizationService.Delete*>-Methode.  
  
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

## <a name="detect-solution-dependencies"></a>Erkennen von Lösungsabhängigkeiten

 Dieses Beispiel zeigt, wie Sie einen Bericht erstellen, der die Abhängigkeiten zwischen Lösungskomponenten zeigt.  
  
 Dieser Code leistet Folgendes:  
  
- Abrufen aller Komponenten für eine Lösung.  
  
- Abrufen aller Abhängigkeiten für jede Komponente.  
  
- Für jede gefundene Abhängigkeit wird ein bericht angezeigt, der die Abhängigkeit beschreibt.  
  
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
  
  Die `DependencyReport`-Methode befindet sich im folgenden Codebeispiel.  
  
### <a name="dependency-report"></a>Abhängigkeitsbericht

 Die Methode `DependencyReport` bietet eine benutzerfreundlichere Nachricht, basierend auf den Informationen, die innerhalb der Abhängigkeit gefunden werden.  
  
> [!NOTE]
>  In diesem Beispiel wird die Methode nur teilweise implementiert. Sie kann Nachrichten nur für Attribut- und Optionssatzlösungskomponenten anzeigen.  
  
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
  
### <a name="detect-whether-a-solution-component-may-be-delete"></a>Erkennen, ob eine Lösungskomponente möglicherweise löscht

 Verwenden Sie die <xref:Microsoft.Crm.Sdk.Messages.RetrieveDependenciesForDeleteRequest>-Meldung, um andere Lösungskomponenten zu identifizieren, die die Löschung einer bestimmten Lösungskomponente verhindern können. Das folgende Codebeispiel sucht nach Attributen, die einen bekannten globalen Optionssatz verwenden. Jedes Attribut, das den globalen Optionssatz verwendet, verhindert das Löschen des globalen Optionssatzes.  
  
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

### <a name="see-also"></a>Siehe auch

 [Packen und Verteilen von Erweiterungen mithilfe von Dynamics 365-Lösungen](/dynamics365/customer-engagement/developer/package-distribute-extensions-use-solutions)   
 [Einführung zu Lösungen](introduction-solutions.md)   
 [Planen einer Lösungsentwicklung](/dynamics365/customer-engagement/developer/plan-solution-development)   
 [Abhängigkeitsnachverfolgung für Lösungskomponenten](dependency-tracking-solution-components.md)   
 [Erstellen, Exportieren oder Importieren einer nicht verwalteten Lösung](create-export-import-unmanaged-solution.md)   
 [Eine verwaltete Lösung erstellen, installieren und aktualisieren](create-install-update-managed-solution.md)   
 [Deinstallieren oder Löschen einer Lösung](uninstall-delete-solution.md)   
 [Lösungsentitäten](/dynamics365/customer-engagement/developer/solution-entities)   
 [Beispiel: Mit Lösungen arbeiten](org-service/samples/work-solutions.md) [Beispiel: Lösungsabhängigkeiten erkennen](/dynamics365/customer-engagement/developer/sample-detect-solution-dependencies)
