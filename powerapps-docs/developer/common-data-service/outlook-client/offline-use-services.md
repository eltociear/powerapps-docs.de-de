---
title: Offline-Nutzung von Diensten (Common Data Service) | Microsoft Docs
description: Erfahren Sie, wie Sie verschiedene Dienste offline nutzen können. Es gibt einige Meldungen, die im Offlinemodus unterstützt werden. Sie können auch feststellen, ob eine IOrganizationService-Nachricht offline arbeitet, indem Sie das SdkMessage.Availability-Attribut für die gewünschte Nachricht überprüfen.
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
ms.openlocfilehash: 8a75ec933ad347bc90ea6710959178710733128a
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155390"
---
# <a name="offline-use-of-services"></a>Offline-Verwendung von Services

Mit Dynamics 365 for Outlook mit Offline Access können Sie Ihre Arbeit fortsetzen, wenn Sie vom Server getrennt sind.  
  
 Zudem können Sie mit der Ereignis- und die Plug-In-Infrastruktur Entwicklungsinvestitionen über Lösungen veranschaulichen, indem Sie das gleiche APIs und Programmiermodell verwenden. Die <xref:Microsoft.Xrm.Sdk.IOrganizationService>-Methoden und die Common Data Service OData Servicemethoden funktionieren im Online- und Offlinemodus. Wenn Sie im Offlinemodus eine Methode wie `Create` oder `Update` verwenden, werden die Daten lokal gespeichert. Wenn der Benutzer dann eine Verbindung mit dem Server herstellt, werden die Aktionen an den Server übermittelt.  
  
 Weitere Informationen darüber, ob eine Nachricht im Offlinemodus unterstützt wird, finden Sie unter <xref:Microsoft.Crm.Sdk.Messages>. Sie können auch feststellen, ob eine Nachricht <xref:Microsoft.Xrm.Sdk.IOrganizationService> offline arbeitet, indem Sie das `SdkMessage.Availability` Attribut für die gewünschte Nachricht überprüfen. Wenn die Meldung für mehrere Entitätstypen funktioniert, müssen Sie auch das `SdkMessageFilter.Availability` Attribut überprüfen, um festzustellen, ob die Meldung für die Entität, die Sie verwenden möchten, im Offlinemodus verfügbar ist. Beispielsweise ist die `Create` Nachricht im Offlinemodus verfügbar aber nicht für die Warteschlange, den Benutzer oder die Websiteentitäten.  
  
 Das Tracing kann auf der Dynamics 365 for Microsoft Office Outlook mit Offline Access für das Debugging aktiviert werden. Weitere Informationen zu den Ereignisanzeige- und Plattformablaufverfolgung, finden Sie unter [Überwachung und Problembehandlung in Dynamics 365](https://technet.microsoft.com/library/hh699694.aspx).  
  
### <a name="see-also"></a>Siehe auch  
 
 <xref:Microsoft.Xrm.Sdk.IOrganizationService>   
 [Organisationsdienstmethoden](/dynamics365/customer-engagement/developer/org-service/organization-service-methods)   
 <xref:Microsoft.Xrm.Sdk.IOrganizationService.Create*>   
 <xref:Microsoft.Xrm.Sdk.IOrganizationService.Update*>