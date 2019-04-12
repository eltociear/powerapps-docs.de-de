---
title: Erweitern Sie Dynamics 365 for Outlook (Common Data Service) | Microsoft Docs
description: 'Dynamics 365 für Outlook ermöglicht Benutzern, mit den Daten zu interagieren, während sie offline und nicht mit dem Server verbunden sind. Common Data Service umfasst Features, die es Ihnen ermöglichen, Ihre Lösungen auch auf Offline-Szenarien auszuweiten, indem Sie die Webdienste offline von Ihrem benutzerdefinierten Code abrufen. Darüber hinaus bietet die Sdk-Assembly programmgesteuerten Support für grundlegende Outlook-Aktionen wie Synchronisierung, Wechsel in den Offline- oder Onlinemodus und Dynamics 365 for Outlook-Statusüberprüfung. Offline-Programmierung verwendet den ASP.NET-Entwicklungsserver.'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
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
---
<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/extend-customer-engagement-outlook 

This topic should be in powerapps-docs/developer/common-data-service/outlook-client/
-->

# <a name="extend-dynamics-365-for-outlook"></a>Erweitern von Dynamics 365 für Outlook

> [!IMPORTANT]
> Wir haben ein überwältigendes Kundenfeedback erhalten und möchten unsere Kunden weiterhin bestmöglich unterstützen. Daher haben wir am 29.1.2018 die Entscheidung getroffen, **Dynamics 365 for Outlook** (Outlook-Add-In) nicht als veraltet einzustufen. Weitere Informationen hierzu erhalten Sie in [diesem Blogbeitrag](https://blogs.msdn.microsoft.com/crm/2018/01/29/continued-support-for-outlook-add-in-dynamics-365-for-outlook/).

Microsoft Dynamics 365 for Outlook ermöglicht Benutzern, mit den Daten zu interagieren, während sie offline und nicht mit dem Server verbunden sind. Common Data Service umfasst Features, die es Ihnen ermöglichen, Ihre Lösungen auch auf Offline-Szenarien auszuweiten, indem Sie die Webdienste offline von Ihrem benutzerdefinierten Code abrufen. Darüber hinaus bietet die <xref:Microsoft.Crm.Outlook.Sdk>Assembly programmgesteuerten Support für grundlegende Outlook-Aktionen wie Synchronisierung, Wechsel in den Offline- oder Onlinemodus und Dynamics 365 for Outlook-Statusüberprüfung. Offline-Programmierung verwendet den ASP.NET-Entwicklungsserver.  
  
 Dynamics 365 enthält Funktionen, die es Administratoren ermöglichen, Filter für die Benutzer anzupassen und zu verwalten. Filtervorlagen stellen den Ausgangspunkt für die Entitätssynchronisierung in  Dynamics 365 for Outlook dar. Filter, die bestimmen, welche Entitätssammlungen mit Outlook und mir Microsoft SQL Server 2008 Express Edition für offline-aktivierte Dynamics 365-Lösungen synchronisiert werden.  
  
## <a name="in-this-section"></a>In diesem Abschnitt

[Offline- und Outlook-Filter und -Vorlagen](offline-outlook-filters-templates.md)<br />  
[Beispiel: Outlook-Filter erstellen und abrufen](sample-create-retrieve-outlook-filters.md)<br />  
[Beispiel: Verwendung von Outlook-Methoden](sample-outlook-methods.md)<br />
  
## <a name="related-sections"></a>Verwandte Abschnitte

<!-- TODO:
[Extend Dynamics 365](extend-dynamics-365-server.md)<br />
[Supported Extensions for Dynamics 365](supported-extensions.md)<br />
[The Metadata and Data Models in Dynamics 365](metadata-data-models.md)<br />
[Extend Dynamics 365 on the server](extend-dynamics-365-server.md)<br />
[Extend Dynamics 365 on the client](extend-client.md)<br />
[Customize Dynamics 365 applications](customize-dev/customize-applications.md)<br />
[Package and distribute extensions using solutions](package-distribute-extensions-use-solutions.md)<br />
[Integrate Dynamics 365 with SharePoint](integration-dev/integrate-sharepoint.md)<br />
 -->
<xref href="Microsoft.Dynamics.CRM.savedquery?text=savedquery EntityType" /><br />
[SavedQuery-Entität](../reference/entities/savedquery.md)<br />
  

