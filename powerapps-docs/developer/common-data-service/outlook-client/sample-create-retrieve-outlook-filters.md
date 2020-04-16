---
title: 'Beispiel: Outlook-Filter erstellen und abrufen (Common Data Service) | Microsoft-Dokumentation'
description: Dieses Beispiel veranschaulicht, wie Filter für Microsoft Dynamics 365 for Outlook abgerufen werden
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: pehecke
ms.service: powerapps
ms.topic: article
author: sriharibs
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 22fb005832149316eb8c967b425f6058d7e1bcf9
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155386"
---
# <a name="sample-create-and-retrieve-outlook-filters"></a>Beispiel: Outlook-Filter erstellen und abrufen

Dieser Beispielcode ist für Common Data Service. Um das Beispiel herunterladen, gehen Sie zu [Beispiel: Erstellen und abrufen von Outlook-Filtern](/dynamics365/customer-engagement/developer/outlook-client/sample-create-retrieve-outlook-filters).

## <a name="prerequisites"></a>Voraussetzungen

Um das Beispielprojekt herunterzuladen und die NuGet-Pakete wiederherzustellen, die im Beispielprojekt verwendet werden, ist eine Internetverbindung erforderlich.

## <a name="demonstrates"></a>Demonstriert  

 Dieses Beispiel veranschaulicht, wie Filter für Microsoft Dynamics 365 for Outlook abgerufen werden.  
  
## <a name="example"></a>Beispiel  

```csharp
// Create and Retrieve Offline Filter
// In your Outlook client, this will appear in the System Filters tab
// under File | CRM | Synchronize | Outlook Filters.
Console.Write("Creating offline filter");
String contactName = String.Format("offlineFilteredContact {0}",
    DateTime.Now.ToLongTimeString());
String fetchXml = String.Format("<fetch version=\"1.0\" output-format=\"xml-platform\" mapping=\"logical\"><entity name=\"contact\"><attribute name=\"contactid\" /><filter type=\"and\">" +
    "<condition attribute=\"ownerid\" operator=\"eq-userid\" /><condition attribute=\"description\" operator=\"eq\" value=\"{0}\" />" +
    "<condition attribute=\"statecode\" operator=\"eq\" value=\"0\" /></filter></entity></fetch>", contactName);
SavedQuery filter = new SavedQuery();
filter.FetchXml = fetchXml;
filter.IsQuickFindQuery = false;
filter.QueryType = SavedQueryQueryType.OfflineFilters;
filter.ReturnedTypeCode = Contact.EntityLogicalName;
filter.Name = "ReadOnlyFilter_" + contactName;
filter.Description = "Sample offline filter for Contact entity";
_offlineFilter = _serviceProxy.Create(filter);

Console.WriteLine(" and retrieving offline filter");
SavedQuery result = (SavedQuery)_serviceProxy.Retrieve(
    SavedQuery.EntityLogicalName,
    _offlineFilter,
    new ColumnSet("name", "description"));
Console.WriteLine("Name: {0}", result.Name);
Console.WriteLine("Description: {0}", result.Description);
Console.WriteLine();

// Create and Retrieve Offline Template
// In your Outlook client, this will appear in the User Filters tab
// under File | CRM | Synchronize | Outlook Filters.
Console.Write("Creating offline template");
String accountName = String.Format("offlineFilteredAccount {0}",
    DateTime.Now.ToLongTimeString());
fetchXml = String.Format("<fetch version=\"1.0\" output-format=\"xml-platform\" mapping=\"logical\"><entity name=\"account\"><attribute name=\"accountid\" /><filter type=\"and\">" +
    "<condition attribute=\"ownerid\" operator=\"eq-userid\" /><condition attribute=\"name\" operator=\"eq\" value=\"{0}\" />" +
    "<condition attribute=\"statecode\" operator=\"eq\" value=\"0\" /></filter></entity></fetch>", accountName);
SavedQuery template = new SavedQuery();
template.FetchXml = fetchXml;
template.IsQuickFindQuery = false;
template.QueryType = SavedQueryQueryType.OfflineTemplate;
template.ReturnedTypeCode = Account.EntityLogicalName;
template.Name = "ReadOnlyFilter_" + accountName;
template.Description = "Sample offline template for Account entity";
_offlineTemplate = _serviceProxy.Create(template);

Console.WriteLine(" and retrieving offline template");
result = (SavedQuery)_serviceProxy.Retrieve(
    SavedQuery.EntityLogicalName,
    _offlineTemplate,
    new ColumnSet("name", "description"));
Console.WriteLine("Name: {0}", result.Name);
Console.WriteLine("Description: {0}", result.Description);
Console.WriteLine();
```
  
### <a name="see-also"></a>Siehe auch  

[Erweitern von Dynamics 365 for Outlook](extend-dynamics-365-outlook.md)<br />
[Beispiel: Verwendung von Outlook-Methoden](sample-outlook-methods.md)<br />
[Offline- und Outlook-Filter und -Vorlagen](offline-outlook-filters-templates.md)<br />
[SavedQuery-Entitätsreferenz](../reference/entities/savedquery.md) 
<xref:Microsoft.Xrm.Sdk.IOrganizationService>