---
title: Aktivitätsentitäten (Common Data Service) | Microsoft-Dokumentation
description: In Dynamics 365 (online) sind Aktivitäten Aufgaben, die Sie oder Ihre Teams ausführen, wenn sie mit Kunden in Kontakt treten, z. B. über Briefe oder Telefonanrufe.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: pehecke
ms.service: powerapps
ms.topic: article
author: mayadumesh
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 6affff8692c279865b0f97a896be257f24c25be7
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3156502"
---
# <a name="activity-entities"></a>Aktivitätsentitäten

In Common Data Service sind Aktivitäten Aufgaben, die Sie oder Ihre Teams ausführen, wenn sie mit Kunden in Kontakt treten, z. B. über Briefe oder Telefonanrufe. Sie können Aktivitäten für sich selbst erstellen, können sie aber auch einer anderen Person zuweisen oder sie für andere Benutzer oder Teams freigeben. Eine Aktivität ist eine Aktion, die in einen Kalender eingetragen werden kann und Zeitdimensionen hat (Startzeit, Endzeit, Fälligkeitsdatum und Dauer), um leichter zu ermitteln, wann die Aktion geschehen ist oder wird. Aktivitäten enthalten auch grundlegende Eigenschaften die bestimmen helfen, welche Aktion die Aktivität repräsentiert, etwa Betreff und Beschreibung. Ein Aktivitätsstatus kann geöffnet, storniert oder abgeschlossen werden. Der abgeschlossene Status einer Aktivität hat verschiedene verknüpfte Substatuswerte, die klären, in welcher Weise die Aktivität abgeschlossen wurde.  
  
 Aktivitäten beziehen einen oder mehrere Teilnehmer, die in Common Data Service als Aktivitätsparteien bezeichnet werden. Bei einer Besprechungsaktivität sind die Teilnehmer die Kontakte oder Benutzer, welche an der Besprechung teilnehmen. Bei einer Telefonanruf- oder Faxaktivität sind die Seiten der Anrufer und die Person, die angerufen wird. Das folgende Diagramm zeigt die Entitätsbeziehungen für Aktivitäten.  
  
 ![Aktivitätsdiagramm](media/entity-model-activity.gif "Aktivitätsdiagramm")  
  
 Um den Kommunikationsbedarf moderner Unternehmen zu unterstützen, wie z. B. Instant Messaging und SMS, können Sie in Common Data Service benutzerdefinierte Aktivitäten erstellen.  
  
 **Weitere Aktivitätsentitäten**  
  
-   Mit Planungsaktivitäten können Sie Ihre Dienste und Ressourcen planen und folglich Arbeitspläne definieren. Die Planungsaktivitätsentitäten sind `Appointment`, `ServiceAppointment` und `RecurringAppointmentMaster`. Weitere Informationen finden Sie unter [Zeitplan- und Termin-Entitäten](/dynamics365/customer-engagement/developer/schedule-appointment-entities).  
  
-   Die Marketingaktivität, `CampaignResponse`, ermöglicht Ihnen, Antworten von Kunden für eine Marketingkampagne zu erfassen, während die `CampaignActivity`-Entität einen Schritt in einer Kampagne darstellt. Weitere Informationen finden Sie unter [Kampagnenentitäten](/dynamics365/customer-engagement/developer/campaign-entities).  
  
-   Die Vertriebsmitarbeiterautomatisierungs-Entitätsaktivitäten `OpportunityClose`, `OrderClose` und `QuoteClose` dienen der Erfassung von Informationen zu jedem dieser Ereignisse. Weitere Informationen finden Sie unter [Vertriebsentitäten (Lead, Verkaufschance, Mitbewerber, Angebot, Auftrag, Rechnung)](/dynamics365/customer-engagement/developer/sales-entities-lead-opportunity-competitor-quote-order-invoice).  
  
-   Die Kundenservice-Entitätsaktivität `IncidentResolution` dient der Erfassung von Informationen zu einem Anfrageabschluss. Weitere Informationen finden Sie unter [Zwischenfall (Fallstudien)-Entitäten](/dynamics365/customer-engagement/developer/incident-case-entities).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Benutzerdefinierte Aktivitäten in Dynamics 365](custom-activities.md)  
  
 [Activity Pointer (Aktivität) Entität](activitypointer-activity-entity.md)  
  
 [Activity Party-Entität](activityparty-entity.md)  
  
 [Aktivitätsentitäten wie Aufgabe, Fax, Telefonanruf und Brief](task-fax-phone-call-letter-activity-entities.md)  
  
 [E-Mail-Aktivitätsentitäten](email-activity-entities.md)  
  
 [Beispielcode für Aktivitätsentitäten](/dynamics365/customer-engagement/developer/sample-code-activity-entities)  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
   
 [Serverseitige Synchronisierungsentitäten](server-side-synchronization-entities.md)  
  
 [Anpassen von Entitätsmetadaten](customize-entity-metadata.md)
