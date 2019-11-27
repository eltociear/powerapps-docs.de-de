---
title: Einfügen, Aktualisieren, Löschen und Anordnen von globalen Optionssatzoptionen (Common Data Service) | Microsoft-Dokumentation
description: Die Codebeispiele zeigen, wie Option im globalen Optionssatz eingefügt, aktualisiert, gelöscht und angeordnet werden.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
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
ms.openlocfilehash: ac224afc2497d5c7600c95a37f61d5b72c8eb461
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748538"
---
# <a name="insert-update-delete-and-order-global-option-set-options"></a>Einfügen, Aktualisieren, Löschen und Anordnen von globalen Optionssatzoptionen

<!-- 

https://docs.microsoft.com/dynamics365/customer-engagement/developer/org-service/insert-update-delete-order-global-option-set-options 

-->

Die Codebeispiele zeigen, wie der globale Optionssatz eingefügt, aktualisiert, gelöscht und angeordnet werden kann.  
  
<a name="BKMK_InsertNewOption"></a>   
## <a name="insert-a-new-option"></a>Einfügen einer neuen Option  
 Das folgende Beispiel zeigt das Einfügen einer neuen Option zu einem globalen Optionssatz mit <xref:Microsoft.Xrm.Sdk.Messages.InsertOptionValueRequest>.  
  
```csharp
// Use InsertOptionValueRequest to insert a new option into a 
// global option set.
InsertOptionValueRequest insertOptionValueRequest =
    new InsertOptionValueRequest
    {
        OptionSetName = _globalOptionSetName,
        Label = new Label("New Picklist Label", _languageCode)
    };

// Execute the request and store the newly inserted option value 
// for cleanup, used in the later part of this sample.
_insertedOptionValue = ((InsertOptionValueResponse)_serviceProxy.Execute(
    insertOptionValueRequest)).NewOptionValue;

//Publish the OptionSet
PublishXmlRequest pxReq2 = new PublishXmlRequest { ParameterXml = String.Format("<importexportxml><optionsets><optionset>{0}</optionset></optionsets></importexportxml>", _globalOptionSetName) };
_serviceProxy.Execute(pxReq2);
```


  
<a name="BKMK_UpdateAnOption"></a>   
## <a name="update-an-option"></a>Aktualisieren einer Option  
 Das folgende Beispiel zeigt das Aktualisieren einer Option in einem globalen Optionssatz mit <xref:Microsoft.Xrm.Sdk.Messages.UpdateOptionValueRequest>.  
  
```csharp
// In order to change labels on option set values (or delete) option set
// values, you must use UpdateOptionValueRequest 
// (or DeleteOptionValueRequest).
UpdateOptionValueRequest updateOptionValueRequest =
    new UpdateOptionValueRequest
    {
        OptionSetName = _globalOptionSetName,
        // Update the second option value.
        Value = optionList[1].Value.Value,
        Label = new Label("Updated Option 1", _languageCode)
    };

_serviceProxy.Execute(updateOptionValueRequest);

//Publish the OptionSet
PublishXmlRequest pxReq3 = new PublishXmlRequest { ParameterXml = String.Format("<importexportxml><optionsets><optionset>{0}</optionset></optionsets></importexportxml>", _globalOptionSetName) };
_serviceProxy.Execute(pxReq3);
```
  
<a name="BKMK_DeleteAnOption"></a>   
## <a name="delete-an-option"></a>Löschen einer Option  
 Das folgende Beispiel zeigt das Löschen einer Option in einem globalen Optionssatz mit <xref:Microsoft.Xrm.Sdk.Messages.DeleteOptionValueRequest>.  
  
```csharp
// Use the DeleteOptionValueRequest message 
// to remove the newly inserted label.
DeleteOptionValueRequest deleteOptionValueRequest =
    new DeleteOptionValueRequest
{
    OptionSetName = _globalOptionSetName,
    Value = _insertedOptionValue
};

// Execute the request.
_serviceProxy.Execute(deleteOptionValueRequest);
```  
  
<a name="BKMK_OrderOptions"></a>   
## <a name="order-options"></a>Anordnen von Optionen  
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
_serviceProxy.Execute(orderOptionRequest);

//Publish the OptionSet
PublishXmlRequest pxReq4 = new PublishXmlRequest { ParameterXml = String.Format("<importexportxml><optionsets><optionset>{0}</optionset></optionsets></importexportxml>", _globalOptionSetName) };
_serviceProxy.Execute(pxReq4);
``` 
