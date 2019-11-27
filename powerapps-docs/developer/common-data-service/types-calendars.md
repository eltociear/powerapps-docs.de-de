---
title: Kalendertypen (Common Data Service) | Microsoft-Dokumentation
description: ''
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
ms.openlocfilehash: e5f0465a51114a7fc3fd2eecd33a243a5af74cae
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748631"
---
# <a name="types-of-calendars"></a>Kalendertypen

Die Kalenderentität wurde geändert, um zusätzliche Kalendertypen in Common Data Service zu unterstützen.  
  
## <a name="calendar-type"></a>Kalendertyp  
 Das `Type`-Auswahllistenattribut enthält die folgenden Optionen:  
  
|Wert|Etikett|Beschreibung|  
|-----------|-----------|-----------------|  
|0|Standard|Alle Kalender, die nicht Kundenservicekalender, Feiertagskalender oder interne Kalender sind.|  
|1|Kundenservice|Servicekalender für Kundenservice.|  
|2|Feiertagszeitplan|Feiertagskalender für Kundenservice.|  
|-1|Interner Kalendertyp|Interne Kalender werden von anderen Kalendern verwendet, um ein Diagramm mit den Zeitfenstern zu erstellen, die für Kundenservice oder die Ausführung der Serviceplanung verfügbar sind.|  
  
### <a name="customer-service-calendars"></a>Kundenservicekalender  
 Kundenservicekalender sind vorhanden, um die Leistung für Vereinbarungen zum Servicelevel (SLAs) zu berechnen. SLAs beruhen häufig auf Schlüsselleistungsindikatoren (KPIs) basierend auf Zeit, z. B. Dauer für die erste Antwort oder Zeitlimit vor der Eskalation. Wenn diese Zeitlimits auf Zeiträume beschränkt sind, in denen Kundenservicevorgänge verfügbar sind, müssen die Berechnungen zum Erzwingen dieser Vereinbarungen Daten aus dem Kundenservicekalender enthalten.  
  
 Kundenservicekalender definieren reguläre Wochenpläne. Ereignisse, die nicht in diese regelmäßigen Zeitpläne fallen, sind meistens Feiertage. Ein Kundenservicekalender kann einem Feiertagskalender zugeordnet werden, um eine vollständige Beschreibung der Zeiten bereitzustellen, in denen Kundenservices verfügbar sind.  
  
### <a name="service-scheduling-calendars"></a>Serviceplanungskalender  
 Die Serviceplanung verwendet den Standardkalendertyp. Betriebsferienkalender können für Service- und Ressourcenentitäten definiert und freigegeben werden. Das Planungsmodul stellt sicher, dass alle entsprechenden Kalenderregeln für eine Terminanforderung berücksichtigt werden.  
  
 Zusätzlich zu den Frei-/Gebucht-Zeiten können Sie den Einschränkungen für den Aufwand (erforderlich/verfügbar) für die `CalendarRule`-Entität definieren. Diese Einschränkungen werden als Aufwand definiert, der aus einer Ressource zum Ausführen, Liefern oder Wiederholen eines bestimmten Service zu gegebener Zeit verfügbar ist. Entsprechend definiert jeder Service den Aufwand, der vom geforderten Pool von Ressourcen zum Abschließen einer Serviceeinheit für die angegebene Dauer erforderlich ist. Das Planungsmodul berechnet automatisch die entsprechenden Zeitblöcke für einen Termin, wenn der Gesamtaufwand, der für einen bestimmten Service erforderlich ist, kleiner oder gleich ist wie der gesamten verfügbare Aufwand für alle erforderlichen Ressourcen.  
  
### <a name="see-also"></a>Siehe auch  
 [Kalenderentitäten](calendar-entities.md)   
 [Kalenderentität](reference/entities/calendar.md)   
 <xref:Microsoft.Dynamics.CRM.calendarrule>