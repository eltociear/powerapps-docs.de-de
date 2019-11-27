---
title: Zeitzonenentitäten (Common Data Service) | Microsoft-Dokumentation
description: Die Zeitzonenentitäten enthalten Zeitzoneninformationen, wie unterstützte Zeitzone, Zeitzonencode, die lokalisierte Zeitzone, und speichern Informationen dazu, wie Uhrzeit berechnet werden.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
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
ms.openlocfilehash: edff87a40b10e99024df4e85d4d46a073a79f6d8
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748522"
---
# <a name="time-zone-entities"></a>Zeitzonenentitäten

Die *Zeitzonenentitäten*-Entitäten können verwendet werden, wenn Sie Code schreiben, der in mehreren Zeitzonen funktioniert. Die folgenden drei schreibgeschützten Entitäten in Common Data Service enthalten Zeitzoneninformationen:  
  
- Die *Zeitzonendefinitionsentität* speichert grundlegende Informationen über sämtliche unterstützte Zeitzone, einschließlich des Zeitzonencodes und des standardmäßigen Zeitzonennamens.  
  
- In der Entität *Lokalisierter Name der Zeitzone* werden die lokalisierten Zeitzonennamen gespeichert.  
  
- Die *Zeitzonenregel*-Entität enthält Informationen dazu, wie Zeiten berechnet werden.  
  
  In der folgenden Tabelle werden die Nachrichten aufgeführt, die mit Zeitzonen verknüpft sind, sich aber auf keine bestimmte Entität beziehen.  
  
|Meldung|Beschreibung|  
|-------------|-----------------|  
|<xref:Microsoft.Crm.Sdk.Messages.GetTimeZoneCodeByLocalizedNameRequest>|Ruft die Zonendefinitionen für bestimmte Gebietsschemas ab und gibt nur das Anzeigenamenattribut zurück.|  
|<xref:Microsoft.Crm.Sdk.Messages.LocalTimeFromUtcTimeRequest>|Ruft die lokale Zeit für die angegebene UTC-Zeit ab.|  
|<xref:Microsoft.Crm.Sdk.Messages.UtcTimeFromLocalTimeRequest>|Ruft die UTC-Zeit für die angegebene lokale Zeit ab.|  
  
### <a name="see-also"></a>Siehe auch  
 [Unternehmensmanagement-Entitäten](/dynamics365/customer-engagement/developer/business-management-entities)   
 [Beispiel: Abrufen von Zeitzoneninformationen](org-service/samples/retrieve-time-zone-information.md)   
 [timezonedefinition EntityType](reference/entities/timezonedefinition.md)   
 [timezonelocalizedname EntityType](reference/entities/timezonelocalizedname.md)   
 [timezonerule EntityType](reference/entities/timezonerule.md)   
 [Beispiel: Abrufen von Zeitzoneninformationen](org-service/samples/retrieve-time-zone-information.md)   
 [Entität der Transaktionswährung (Währung)](transaction-currency-currency-entity.md)
