---
title: Überwachungsbenutzerzugriff (Common Data Service) | Microsoft-Dokumente
description: Unterstützung für die Funktion zur Überwachung von Benutzerzugriffen einschließlich Benutzeidentifizierung, Zugriffsgeschwindigkeit und Clienttyp.
ms.custom: ''
ms.date: 01/27/2019
ms.reviewer: pehecke
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
ms.openlocfilehash: 5bc524f4cfbd4d5623894b4de4607d7b3ff96bf5
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3156462"
---
# <a name="audit-user-access"></a>Benutzerzugriff überwachen

Common Data Service unterstützen die Möglichkeit, den Benutzerzugriff zu überwachen. Zu den erfassten Informationen gehört, wann der Benutzer erstmals auf Common Data Service zugegriffen hat, und ob der Zugriff aus der Webanwendung von Common Data Service, Dynamics 365 for Outlook oder aus SDK-Anrufen bei den Webdiensten erfolgte.  
  
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
  
 `UserAccessviaWeb` gibt den Zugriff über die Common Data Service-Webanwendung oder Dynamics 365 for Outlook an. `UserAccessviaWebServices` gibt eine Webdienstanforderung des SDK an. Die `AuditAction` Aufzählung ist für Ihren Code verfügbar, wenn Sie `OptionSets.cs` in Ihrer Projektanwendung einschließen.  
  
### <a name="see-also"></a>Siehe auch  
 [Datenänderungen überwachen](/powerapps/developer/common-data-service/auditing-overview)   
 [Konfigurieren von Entitäten und Attributen für die Überwachung](/powerapps/developer/common-data-service/configure-entities-attributes-auditing)     
 [Beispiel: Überwachung von Entitätsdatenänderungen](/powerapps/developer/common-data-service/org-service/samples/audit-entity-data-changes)   
 [Beispiel: Überwachung von Benutzerzugriffen](/powerapps/developer/common-data-service/org-service/samples/audit-user-access)
