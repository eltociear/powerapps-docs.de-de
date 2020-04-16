---
title: Optionssätze anpassen (Common Data Service) | Microsoft-Dokumentation
description: Beschreibt, wie mit globalen und lokale Optionssätzen im Code gearbeitet wird.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: pehecke
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 3b2d6bc193fb5e001d3fd2813d8da3956b0b3a53
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3156014"
---
# <a name="customize-option-sets"></a>Optionssätze anpassen

Normalerweise können Sie mithilfe von *globalen* Optionssätzen Felder festlegen, sodass andere Felder denselben Satz von Optionen nutzen können, die an einem Ort verwaltet werden. Anders als *lokale* Optionssätze, die nur für ein bestimmtes Attribut definiert werden, können Sie Globale Optionssätze wiederverwenden. Sie können auch in Anforderungsparametern auf eine ähnliche Weise wie eine Enumeration verwendet werden.  
  
Beim Definieren eines globalen Optionssatzes mithilfe von <xref:Microsoft.Xrm.Sdk.Messages.CreateOptionSetRequest> wird empfohlen, das System einen Wert zuweisen zu lassen. Dazu übergeben Sie einen **null** -Wert, wenn Sie die neue `OptionMetadata`-Instanz erstellen. Wenn Sie eine Option definieren, enthält sie ein für den Kontext des Herausgebers spezifisches Optionswertpräfix, festgelegt für die Lösung, in der der Optionssatz erstellt wird. Dieses Präfix hilft, die Möglichkeit der Erstellung von doppelten Optionssätzen für eine verwaltete Lösung zu verringern, sowie in allen Optionssätzen, die in Organisationen definiert werden, in denen die verwaltete Lösung installiert ist. Weitere Informationen finden Sie unter [Zusammenführung von Optionssatz-Optionen](../../../maker/common-data-service/how-managed-solutions-merged.md).  

Sie können das Beispiel von [hier](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/WorkWithOptionSets) herunterladen.

## <a name="messages-request-classes"></a>Nachrichtenanforderungsklassen  

Verwenden Sie die folgenden Nachrichtenanforderungsklassen für das Arbeiten mit globalen Optionssätzen

- <xref:Microsoft.Xrm.Sdk.Messages.CreateOptionSetRequest>
- <xref:Microsoft.Xrm.Sdk.Messages.DeleteOptionSetRequest>
- <xref:Microsoft.Xrm.Sdk.Messages.RetrieveAllOptionSetsRequest>
- <xref:Microsoft.Xrm.Sdk.Messages.RetrieveOptionSetRequest>  
- <xref:Microsoft.Xrm.Sdk.Messages.UpdateOptionSetRequest> 

Verwenden Sie die folgenden Nachrichtenanforderungsklassen für globale und lokale Optionssätze.

- <xref:Microsoft.Xrm.Sdk.Messages.DeleteOptionValueRequest>
- <xref:Microsoft.Xrm.Sdk.Messages.InsertOptionValueRequest>
- <xref:Microsoft.Xrm.Sdk.Messages.InsertStatusValueRequest>
- <xref:Microsoft.Xrm.Sdk.Messages.OrderOptionRequest>
- <xref:Microsoft.Xrm.Sdk.Messages.UpdateOptionValueRequest>
- <xref:Microsoft.Xrm.Sdk.Messages.UpdateStateValueRequest>  

<a name="BKMK_RetrieveAGlobalOptionSet"></a>

## <a name="retrieve-a-global-option-set"></a>Abrufen eines globalen Optionssatzes  

 Das folgende Beispiel zeigt, wie ein globaler Optionssatz nach Name mithilfe der Meldung <xref:Microsoft.Xrm.Sdk.Messages.RetrieveOptionSetRequest> abgerufen wird.  
  

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
    (RetrieveOptionSetResponse)svc.Execute(
    retrieveOptionSetRequest);

Console.WriteLine("Retrieved {0}.",
    retrieveOptionSetRequest.Name);

// Access the retrieved OptionSetMetadata.
OptionSetMetadata retrievedOptionSetMetadata =
    (OptionSetMetadata)retrieveOptionSetResponse.OptionSetMetadata;

// Get the current options list for the retrieved attribute.
OptionMetadata[] optionList =
    retrievedOptionSetMetadata.Options.ToArray();
```

  
<a name="BKMK_CreateGlobalOptionSet"></a>  
 
## <a name="create-a-global-option-set"></a>Erstellen eines globalen Optionssatzes
  
Verwenden Sie die Meldung <xref:Microsoft.Xrm.Sdk.Messages.CreateOptionSetRequest>, um einen neuen globalen Optionssatz zu erstellen. Legen Sie die Eigenschaft <xref:Microsoft.Xrm.Sdk.Metadata.OptionSetMetadataBase.IsGlobal> auf `true` fest, um anzugeben, dass der Optionssatz global ist. Das folgende Codebeispiel erstellt einen globalen Optionssatz mit dem Namen "Beispiel-Optionssatz":  
  
```csharp
// Define the request object and pass to the service.
CreateOptionSetRequest createOptionSetRequest = new CreateOptionSetRequest
{
    // Create a global option set (OptionSetMetadata).
    OptionSet = new OptionSetMetadata
    {
        Name = _globalOptionSetName,
        DisplayName = new Label("Example Option Set", _languageCode),
        IsGlobal = true,
        OptionSetType = OptionSetType.Picklist,
        Options = 
    {
        new OptionMetadata(new Label("Open", _languageCode), null),
        new OptionMetadata(new Label("Suspended", _languageCode), null),
        new OptionMetadata(new Label("Cancelled", _languageCode), null),
        new OptionMetadata(new Label("Closed", _languageCode), null)
    }
    }
};

// Execute the request.
CreateOptionSetResponse optionsResp =
    (CreateOptionSetResponse)svc.Execute(createOptionSetRequest);
```

  
<a name="BKMK_CreatePicklistWithGlobalOptionSet"></a>  
 
## <a name="create-a-picklist-that-uses-a-global-option-set"></a>Erstellen einer Auswahlliste, die einen globalen Optionssatz verwendet  

 Das folgende Beispiel zeigt, wie ein Auswahllistenattribut erstellt wird, das einen globalen Optionssatz verwendet, indem <xref:Microsoft.Xrm.Sdk.Messages.CreateAttributeRequest> verwendet wird:  
  

```csharp
// Create a Picklist linked to the option set.
// Specify which entity will own the picklist, and create it.
CreateAttributeRequest createRequest = new CreateAttributeRequest
{
    EntityName = Contact.EntityLogicalName,
    Attribute = new PicklistAttributeMetadata
    {
        SchemaName = "sample_examplepicklist",
        LogicalName = "sample_examplepicklist",
        DisplayName = new Label("Example Picklist", _languageCode),
        RequiredLevel = new AttributeRequiredLevelManagedProperty(AttributeRequiredLevel.None),

        // In order to relate the picklist to the global option set, be sure
        // to specify the two attributes below appropriately.
        // Failing to do so will lead to errors.
        OptionSet = new OptionSetMetadata
        {
            IsGlobal = true,
            Name = _globalOptionSetName
        }
    }
};

svc.Execute(createRequest);
```

  
<a name="BKMK_UpdateGlobalOptionSet"></a>

## <a name="update-a-global-option-set"></a>Aktualisieren eines globalen Optionssatzes 

Das folgende Beispiel zeigt, wie die Beschriftung für einen globalen Optionssatz aktualisiert wird, indem <xref:Microsoft.Xrm.Sdk.Messages.UpdateOptionSetRequest> verwendet wird.  
  

```csharp
// Use UpdateOptionSetRequest to update the basic information of an option
// set. Updating option set values requires different messages (see below).
UpdateOptionSetRequest updateOptionSetRequest = new UpdateOptionSetRequest
{
    OptionSet = new OptionSetMetadata
    {
        DisplayName = new Label("Updated Option Set", _languageCode),
        Name = _globalOptionSetName,
        IsGlobal = true
    }
};

svc.Execute(updateOptionSetRequest);

//Publish the OptionSet
PublishXmlRequest pxReq1 = new PublishXmlRequest { ParameterXml = String.Format("<importexportxml><optionsets><optionset>{0}</optionset></optionsets></importexportxml>", _globalOptionSetName) };
svc.Execute(pxReq1);
```

  
<a name="BKMK_OrderingOptions"></a> 
  
## <a name="ordering-options"></a>Reihenfolgeoptionen  

Das folgende Beispiel zeigt, wie die Optionen in einem globalen Optionssatz mithilfe von <xref:Microsoft.Xrm.Sdk.Messages.OrderOptionRequest> geordnet werden können.  
  

```csharp
// Change the order of the original option's list.
// Use the OrderBy (OrderByDescending) linq function to sort options in  
// ascending (descending) order according to label text.
// For ascending order use this:
var updateOptionList =
    optionList.OrderBy(x => x.Label.LocalizedLabels[0].Label).ToList();

// For descending order use this:
// var updateOptionList =
//      optionList.OrderByDescending(
//      x => x.Label.LocalizedLabels[0].Label).ToList();

// Create the request.
OrderOptionRequest orderOptionRequest = new OrderOptionRequest
{
    // Set the properties for the request.
    OptionSetName = _globalOptionSetName,
    // Set the changed order using Select linq function 
    // to get only values in an array from the changed option list.
    Values = updateOptionList.Select(x => x.Value.Value).ToArray()
};

// Execute the request
svc.Execute(orderOptionRequest);

//Publish the OptionSet
PublishXmlRequest pxReq4 = new PublishXmlRequest { 
ParameterXml = String.Format("<importexportxml><optionsets><optionset>{0}</optionset></optionsets></importexportxml>", _globalOptionSetName) 
};
svc.Execute(pxReq4);
```

  
<a name="BKMK_RetrieveAllGlobalOptionSets"></a>  
 
## <a name="retrieve-all-global-option-sets"></a>Abrufen aller globalen Optionssätze  

Das folgende Beispiel zeigt, wie alle globalen Optionssätze mithilfe von <xref:Microsoft.Xrm.Sdk.Messages.RetrieveAllOptionSetsRequest> abgerufen werden.  
  

```csharp
// Use RetrieveAllOptionSetsRequest to retrieve all global option sets.
// Create the request.
RetrieveAllOptionSetsRequest retrieveAllOptionSetsRequest =
    new RetrieveAllOptionSetsRequest();

// Execute the request
RetrieveAllOptionSetsResponse retrieveAllOptionSetsResponse =
    (RetrieveAllOptionSetsResponse)svc.Execute(
    retrieveAllOptionSetsRequest);

// Now you can use RetrieveAllOptionSetsResponse.OptionSetMetadata property to 
// work with all retrieved option sets.
if (retrieveAllOptionSetsResponse.OptionSetMetadata.Count() > 0)
{
    Console.WriteLine("All the global option sets retrieved as below:");
    int count = 1;
    foreach (OptionSetMetadataBase optionSetMetadata in
        retrieveAllOptionSetsResponse.OptionSetMetadata)
    {
        Console.WriteLine("{0} {1}", count++,
            (optionSetMetadata.DisplayName.LocalizedLabels.Count >0)? optionSetMetadata.DisplayName.LocalizedLabels[0].Label : String.Empty);
    }
}
```

  
<a name="BKMK_DeleteAGlobalOptionSet"></a>

## <a name="delete-a-global-option-set"></a>Löschen eines globalen Optionssatzes

 Das folgende Beispiel zeigt, wie Sie mithilfe der `RetrieveDependentComponents`-Message (<xref href="Microsoft.Dynamics.CRM.RetrieveDependentComponents?text=RetrieveDependentComponents Function" /> oder <xref:Microsoft.Crm.Sdk.Messages.RetrieveDependentComponentsRequest>) überprüfen, ob ein globaler Optionssatz von einer anderen Lösungskomponente verwendet wird, und wie Sie ihn mithilfe der `DeleteOptionSet` Message (Für Organisation-Service, verwenden Sie <xref:Microsoft.Xrm.Sdk.Messages.DeleteOptionSetRequest>) löschen können:  
  

```csharp
// Create the request to see which components have a dependency on the
// global option set.
RetrieveDependentComponentsRequest dependencyRequest =
    new RetrieveDependentComponentsRequest
    {
        ObjectId = _optionSetId,
        ComponentType = (int)componenttype.OptionSet
    };

RetrieveDependentComponentsResponse dependencyResponse =
    (RetrieveDependentComponentsResponse)svc.Execute(
    dependencyRequest);

// Here you would check the dependencyResponse.EntityCollection property
// and act as appropriate. However, we know there is exactly one 
// dependency so this example deals with it directly and deletes 
// the previously created attribute.
DeleteAttributeRequest deleteAttributeRequest =
    new DeleteAttributeRequest
{
    EntityLogicalName = Contact.EntityLogicalName,
    LogicalName = "sample_examplepicklist"
};

svc.Execute(deleteAttributeRequest);

Console.WriteLine("Referring attribute deleted.");
  
// Finally, delete the global option set. Attempting this before deleting
// the picklist above will result in an exception being thrown.
DeleteOptionSetRequest deleteRequest = new DeleteOptionSetRequest
{
    Name = _globalOptionSetName
};

svc.Execute(deleteRequest);
```

  
### <a name="see-also"></a>Siehe auch

[Erstellen und Aktualisieren von Optionssätzen mit der Web-API](../webapi/create-update-optionsets.md)