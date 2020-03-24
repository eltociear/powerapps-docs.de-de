---
title: API Grenzwerte, Übersicht (Common Data Service) | MicrosoftDocs
description: Verstehen Sie die Begrenzungen für Common Data Service API-Anforderungen.
ms.custom: ''
ms.date: 03/05/2020
ms.reviewer: kvivek
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: jdaly
manager: ryjones
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 69e55b7b917a95158caa13322be21471bd43df3a
ms.sourcegitcommit: 629e47c769172e312ae07cb29e66fba8b4f03efc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "3109105"
---
# <a name="common-data-service-api-limits-overview"></a>Common Data Service Übersicht über API-Grenzwerte

Common Data Service API-Grenzwerte tragen dazu bei, Service Level, Verfügbarkeit und Qualität sicherzustellen. Common Data Service API-Grenzwerte sind Teil der Power Platform Grenzwertanforderungen und Zuteilungen. Diese Thema führt Grenzwerte speziell ein für Common Data Service anwendbar für modellbasierte Apps in Dynamics 365 (z. B. Dynamics 365 Sales und Dynamics 365 Customer Service), Power Apps, und Power Automate verbindet mit Common Data Service/ modellbasierte Apps in Dynamics 365. 

Informationen zu Grenzwerten für alle Bereiche innerhalb von Power Platform finden Sie unter [Power Platform Grenzwerte und Zuteilungen anfordern](/power-platform/admin/api-request-limits-allocations).

Es gibt zwei Kategorien von Grenzwerte, die für Common Data Service gelten: *Berechtigung* und *Serviceschutz* Grenzwerte.

## <a name="entitlement-limits"></a>Berechtigungs-Grenzwerte

Diese Grenzwerte geben die Anzahl der Anforderungen an, zu denen Benutzer täglich berechtigt sind. Der zugewiesene Grenzwert hängt von der Art der Lizenz ab, die jedem Benutzer zugewiesen wurde.

Wenn ein Benutzer seine Anforderungsberechtigung überschreitet, würde der Administrator benachrichtigt und könnte Power Apps zuweisen und Power Automate Kapazität für diesen Benutzer anfordern. Benutzer werden zu diesem Zeitpunkt nicht daran gehindert, Apps für gelegentliche und angemessene Überschreitungen zu verwenden.

Für Common Data Service umfassen API-Anforderungen alle Datenoperationen, die mit Entitätsdatensätzen interagieren, in denen Datensätze erstellt, abgerufen, aktualisiert oder gelöscht werden (CRUD). Sonderoperationen wie *freigeben* und *zuweisen* sind enthalten, da sie als Updates gelten. Diese Anforderungen können von einem beliebigen Client oder einer beliebigen Anwendung stammen und einen beliebigen Endpunkt verwenden. Hierzu zählen unter anderem Vorgänge, die von Plug-Ins ausgeführt werden, asynchrone Workflows, benutzerdefinierte Steuerelemente und $batch-Vorgänge (ExecuteMultiple). Es gibt eine kleine Reihe von systeminternen Vorgängen, die ausgeschlossen sind, wie Anmelde-, Abmelde- und Systemmetadatenvorgänge.

> [!IMPORTANT]
> Power Platform API-Anforderungszuordnungen umfassen die Verwendung von Power Automate, AI Builder und Connector-APIs. Alle Anfragen über einen Connector, die zu einer Common Data Service Anfrage führen, steht als 1 in der Power Platform Anfrage.

Einzelheiten zu diesen Berechtigungsgrenzen finden Sie unter [Microsoft Power Platform Zuweisungsanforderungen basierend auf Lizenzen](/power-platform/admin/api-request-limits-allocations#microsoft-power-platform-requests-allocations-based-on-licenses).

Informationen zum Anzeigen und Zuweisen von Kapazitätserweiterungen finden Sie unter [Kapazitätserweiterungen](/power-platform/admin/capacity-add-on).

Informationen zum Kauf einzelner Kapazitätserweiterungen finden Sie unter [Power Apps und Power Automate Lizenzierungshandbuch](https://go.microsoft.com/fwlink/?linkid=2085130). 
<!-- There should be some help about purchasing these through the Portal -->


## <a name="service-protection-limits"></a>Grenzwerte für den Serviceschutz

Um eine konsistente Verfügbarkeit und Leistung für alle zu gewährleisten, wenden wir einige Einschränkungen für die Verwendung von APIs mit Common Data Service anwenden. Der Serviceschutz API Grenzwert stellt sicher, dass Benutzer, die Anwendungen ausführen, sich nicht aufgrund vorhandener Ressourceneinschränkungen gegenseitig stören. Die Grenzwerte haben keine Auswirkungen auf normale Plattformbenutzer. Nur Anwendungen, die eine sehr große Anzahl an API-Anforderungen ausführen, sind möglicherweise betroffen. Der Grenzwert bietet einen gewissen Schutz vor dem unwillkürlichen und unerwarteten Anstieg des Anforderungsvolumens, das die Verfügbarkeit und Leistungsfähigkeit der Common Data Service Plattform gefährdet.

Wir begrenzen die Anzahl der gleichzeitigen Verbindungen pro Benutzerkonto, die Anzahl der API-Anforderungen pro Verbindung und die Ausführungszeit, die für jede Verbindung verwendet werden kann. Diese werden innerhalb eines fünfminütigen Schiebefensters ausgewertet. Wenn einer dieser Grenzwerte überschritten wird, gibt die Plattform eine Ausnahme zurück.

> [!NOTE]
> Die Schutzbegrenzungen für den Dienst gelten für alle externen Web-Service-Anfragen, nicht nur für die CRUD-Operationen an Entitäten, die auf die Berechtigungsbegrenzungen angerechnet werden.
> 
> API-Beschränkungen für den Dienstschutz werden nicht auf API-Aufrufe innerhalb von Workflows, benutzerdefinierte Workflow-Aktivitäten oder Plugin-Code angewendet. Diese Operationen werden intern aufgerufen.

Da Serviceschutzbeschränkungen normalerweise nur von Anwendungen angewendet werden, die eine große Anzahl von Datenvorgängen ausführen, wird empfohlen, dass Entwickler, die diese Anwendungen erstellen, nach einem bestimmten Zeitraum Muster anwenden, um Vorgänge erneut zu versuchen, wenn diese Ausnahmen zurückgegeben werden. Auf diese Weise kann die Anwendung auf vom Dienst gesendete Ausnahmen reagieren, die Gesamtzahl der Anforderungen verringern und den höchstmöglichen Durchsatz erzielen.

Informationen zu den spezifischen Fehlern, die zurückgegeben werden können, und darüber, wie Entwickler Muster anwenden können, um auf diese Fehler zu reagieren, finden Sie unter [Serviceschutz API-Beschränkungen](../../developer/common-data-service/api-limits.md).


### <a name="see-also"></a>Siehe auch

[Verwalten Power Platform / Lizenzierung und Lizenzverwaltung / Anforderungsgrenzen und -zuordnungen](/power-platform/admin/api-request-limits-allocations)<br />
[Entwickler / Arbeiten mit Daten mithilfe von Code / Serviceschutz API-Grenzwerte](../../developer/common-data-service/api-limits.md)

