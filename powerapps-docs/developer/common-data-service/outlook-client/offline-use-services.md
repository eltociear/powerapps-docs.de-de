---
title: Offline-Nutzung von Dynamics 365-Services (Common Data Service für Apps) | Microsoft Docs
description: 'Lernen Sie, wie die verschiedenen Dynamics 365-Dienste offline verwendet werden können. Es gibt einige Meldungen, die im Offlinemodus unterstützt werden. Sie können auch feststellen, ob eine IOrganizationService-Nachricht offline arbeitet, indem Sie das SdkMessage.Availability-Attribut für die gewünschte Nachricht überprüfen.'
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

# <a name="offline-use-of-services"></a>Offline-Verwendung von Services

Dynamics 365 for Microsoft Office Outlook mit Offlinezugriff ermöglicht Ihnen, auch dann weiterzuarbeiten, wenn die Verbindung zum Server getrennt wurde.  
  
 Zudem können Sie mit der Ereignis- und die Plug-In-Infrastruktur Entwicklungsinvestitionen über Lösungen veranschaulichen, indem Sie das gleiche APIs und Programmiermodell verwenden. Die <xref:Microsoft.Xrm.Sdk.IOrganizationService>-Methoden und die Common Data Service für Apps-OData-Servicemethoden funktionieren im Online- und Offlinemodus. Wenn Sie im Offlinemodus eine Methode wie `Create` oder `Update` verwenden, werden die Daten lokal gespeichert. Wenn der Benutzer dann eine Verbindung mit dem Server herstellt, werden die Aktionen an den Server übermittelt.  
  
 Weitere Informationen darüber, ob eine Nachricht im Offlinemodus unterstützt wird, finden Sie unter <xref:Microsoft.Crm.Sdk.Messages>. Sie können auch feststellen, ob eine Nachricht <xref:Microsoft.Xrm.Sdk.IOrganizationService> offline arbeitet, indem Sie das `SdkMessage.Availability` Attribut für die gewünschte Nachricht überprüfen. Wenn die Meldung für mehrere Entitätstypen funktioniert, müssen Sie auch das `SdkMessageFilter.Availability` Attribut überprüfen, um festzustellen, ob die Meldung für die Entität, die Sie verwenden möchten, im Offlinemodus verfügbar ist. Beispielsweise ist die `Create` Nachricht im Offlinemodus verfügbar aber nicht für die Warteschlange, den Benutzer oder die Websiteentitäten.  
  
 Die Ablaufverfolgung kann in Dynamics 365 for Microsoft Office Outlook mit Offlinezugriff für das Debuggen aktiviert werden. Weitere Informationen zu den Ereignisanzeige- und Plattformablaufverfolgung, finden Sie unter [Überwachung und Problembehandlung in Dynamics 365](https://technet.microsoft.com/library/hh699694.aspx).  
  
### <a name="see-also"></a>Siehe auch  
 [Erweitern von Dynamics 365 Customer Engagement auf dem Server](/dynamics365/customer-engagement/developer/extend-dynamics-365-server)   
 [Fehler- und Problembehandlung](/dynamics365/customer-engagement/developer/org-service/troubleshooting-error-handling)   
 <xref:Microsoft.Xrm.Sdk.IOrganizationService>   
 [Organisationsdienstmethoden](/dynamics365/customer-engagement/developer/org-service/organization-service-methods)   
 <xref:Microsoft.Xrm.Sdk.IOrganizationService.Create*>   
 <xref:Microsoft.Xrm.Sdk.IOrganizationService.Update*>