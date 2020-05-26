---
title: Erweitern von Dynamics 365 for Outlook (Common Data Service) | Microsoft-Dokumentation
description: Dynamics 365 for Outlook ermöglicht Benutzern, mit den Daten zu interagieren, während sie offline und nicht mit dem Server verbunden sind. Common Data Service umfasst Features, die es Ihnen ermöglichen, Ihre Lösungen auch auf Offline-Szenarien auszuweiten, indem Sie die Webdienste offline von Ihrem benutzerdefinierten Code abrufen. Darüber hinaus bietet die Sdk-Assembly programmgesteuerten Support für grundlegende Outlook-Aktionen wie Synchronisierung, Wechsel in den Offline- oder Onlinemodus und Dynamics 365 for Outlook Statusüberprüfung. Offline-Programmierung verwendet den ASP.NET Entwicklungsserver.
ms.custom: ''
ms.date: 04/07/2020
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
ms.openlocfilehash: 8c8fc40f7a02d6b636b29758cd0964084b8e9333
ms.sourcegitcommit: 6acc6ac7cc1749e9681d5e55c96613033835d294
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "3238262"
---
# <a name="extend-dynamics-365-for-outlook"></a>Dynamics 365 for Outlook erweitern

> [!IMPORTANT]
> Ab März 2020 ist die Vorgängerversion von Dynamics 365 for Outlook (auch als Outlook COM-Add-In bezeichnet) veraltet. Kunden müssen vor dem 1. Oktober 2020 zur modernen [Dynamics 365 App for Outlook](https://docs.microsoft.com/dynamics365/outlook-app/overview) übergehen. Microsoft wird weiterhin Support, Sicherheit und andere wichtige Updates für das Outlook COM-Add-In bis zum 1. Oktober 2020 bereitstellen.
> 
> Weitere Informationen und Schritte für einen reibungslosen Übergang finden Sie unter [Dynamics 365 for Outlook (COM-Add-In) Playbook](https://aka.ms/OutlookCOMPlaybook).

Dynamics 365 for Outlook ermöglicht Benutzern, mit den Daten zu interagieren, während sie offline und nicht mit dem Server verbunden sind. Common Data Service umfasst Features, die es Ihnen ermöglichen, Ihre Lösungen auch auf Offline-Szenarien auszuweiten, indem Sie die Webdienste offline von Ihrem benutzerdefinierten Code abrufen. Darüber hinaus bietet die <xref:Microsoft.Crm.Outlook.Sdk>-Assembly programmgesteuerten Support für grundlegende Outlook-Aktionen wie Synchronisierung, Wechsel in den Offline- oder Onlinemodus und Dynamics 365 for Outlook-Statusüberprüfung. Offline-Programmierung verwendet den ASP.NET Entwicklungsserver.  
  
 Dynamics 365 enthält Funktionen, die es Administratoren ermöglichen, Filter für die Benutzer anzupassen und zu verwalten. Filtervorlagen stellen den Ausgangspunkt für die Entitätssynchronisierung in Dynamics 365 for Outlook dar. Filter, die bestimmen, welche Entitätssammlungen mit Outlook und mir Microsoft SQL Server 2008 Express Edition für offline-aktivierte Dynamics 365-Lösungen synchronisiert werden.  
  
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
  

