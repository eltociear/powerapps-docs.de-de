---
title: Benutzerzugriff überwachen (Common Data Service) | Microsoft Docs
description: 'Unterstützung für die Funktion zur Überwachung von Benutzerzugriffen einschließlich Benutzeidentifizierung, Zugriffsgeschwindigkeit und Clienttyp.'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: paulliew
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="audit-user-access"></a>Benutzerzugriff überwachen

Common Data Service unterstützt die Möglichkeit, den Benutzerzugriff zu überwachen. Zu den erfassten Informationen gehört, wann der Benutzer erstmals auf Common Data Service zugegriffen hat, und ob der Zugriff aus der Webanwendung von Common Data Service, Dynamics 365 for Outlook oder aus SDK-Anrufen bei den Webdiensten erfolgte.  
  
## <a name="enable-user-access-auditing"></a>Überwachung des Benutzerzugriffs aktivieren  
 Überwachung des Benutzerzugriffs wird auf Organisationsebene aktiviert. Um Benutzerzugriffüberwachung zu aktivieren oder zu deaktivieren, müssen Sie den Datensatz der Zielorganisation abrufen und den `Organization.IsUserAccessAuditEnabled`-Attributwert für die Organisation aktualisieren. Globale Überwachung in der Organisation muss auch aktiviert werden, indem Sie das `Organization.IsAuditEnabled`-Attribut auf `true` im Organisationsdatensatz setzen. Um den Ursprung des Benutzerzugriffs zu überwachen, beispielsweise: Webanwendung, Dynamics 365 for Outlook oder SDK, müssen Sie die Überwachung auf den Entitäten aktivieren, auf die zugegriffen wird.  
  
 Die Häufigkeit der Überwachung das Benutzerzugriffs kann mithilfe des `Organization.UserAccessAuditingInterval`-Attributs gelesen oder festgelegt werden. Das Standardattribut 4 gibt an, dass der Benutzerzugriff einmal alle 4 Stunden überwacht wird.  
  
 Weitere Informationen zum Aktivieren der Überwachung für eine Organisation oder eine Entität finden Sie unter [Konfigurieren von Entitäten und Attributen für Überwachung](configure-entities-attributes-auditing.md).  
  
## <a name="filter-on-user-access-events"></a>Filtern auf Benutzerzugriffereignissen  
 Um nach Prüfprotokollen zu suchen, die sich auf Benutzerzugriff beziehen, sollte Ihr Code `Audit`-Datensätzen einer Organisation abrufen und nach dem Wert in Datei `Audit.Action` filtern. Eine Aufzählung namens `AuditAction` wird bereitgestellt, um unterstützte Überwachungsaktionen zu identifizieren. Die Aktionen, die mit den Benutzerzugriff zusammenhängen, werden in der folgenden Liste angezeigt.  
  
-   `AuditAction.UserAccessviaWeb`  
  
-   `AuditAction.UserAccessviaWebServices`  
  
-   `AuditAction.UserAccessAuditStarted`  
  
-   `AuditAction.UserAccessAuditStopped`  
  
 `UserAccessviaWeb` gibt den Zugriff auf die Common Data Service-Webanwendung oder Dynamics 365 for Outlook an. `UserAccessviaWebServices` gibt eine Webdienstanforderung des SDK an. Die `AuditAction`-Aufzählung ist für Ihren Code verfügbar, wenn Sie `OptionSets.cs` oder `OptionSets.vb` im Projekt der Anwendung einschließen.  
  
### <a name="see-also"></a>Siehe auch  
 [Überwachung von Änderungen in Dynamics 365](/dynamics365/customer-engagement/developer/audit-entity-data-changes)   
 [Konfigurieren von Entitäten und Attributen für die Überwachung](/dynamics365/customer-engagement/developer/configure-entities-attributes-auditing)     
 [Beispiel: Überwachung von Entitätsdatenänderungen](/dynamics365/customer-engagement/developer/sample-audit-entity-data-changes)   
 [Beispiel: Überwachung von Benutzerzugriffen](/dynamics365/customer-engagement/developer/sample-audit-user-access)
