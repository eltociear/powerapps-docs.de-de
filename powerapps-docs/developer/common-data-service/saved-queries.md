---
title: Gespeicherte Abfragen (Common Data Service) | Microsoft-Dokumentation
description: Hier erfahren Sie, wie gespeicherte Abfragen die Suchumgebung in Common Data Service erweitern.
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
ms.openlocfilehash: c466cb19fcc1b350fda1b85a05c24c2231d14815
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748653"
---
# <a name="saved-queries"></a>Gespeicherte Abfragen

Gespeicherte Abfragen sind Geschäftsentitäten, die die Parameter und Kriterien einer Common Data Service-Umgebungssuche definieren. Gespeicherte Abfragen unterstützen Suchen über mehrere Entitäten. Es gibt zwei Entitäten, die für Abfragen der Common Data Service-Umgebung verfügbar sind.  
  
- Eine *Benutzerabfrage*, die in der Anwendung als gespeicherte Ansicht bezeichnet wird, befindet sich im Besitz eines einzelnen Benutzers, kann anderen Benutzern zugewiesen und für andere Benutzer freigegeben werden und kann von anderen Benutzern abhängig von den Zugriffsrechten der Abfrage angezeigt werden. Dies ist für häufig verwendete Abfragen, die sich über mehrere Entitätstypen erstrecken, und Abfragen, die eine Aggregation ausführen, geeignet. Weitere Informationen: [UserQuery-Entität](reference/entities/userquery.md) 

- Eine *gespeicherte Abfrage*, die in der Anwendung als Ansicht bezeichnet wird, ist im Besitz einer Organisation und wird dadurch für alle Benutzer in der Organisation sichtbar. Gespeicherte Abfragen (Ansichten) werden für beide Ansichten verwendet, die für eine Entität sowie für Filter und Vorlangen für Dynamics 365 for Outlook definiert werden. Weitere Informationen: [SavedQuery-Entität](reference/entities/savedquery.md) 
  
 Eine Abfrage in der Form einer FetchXML-Anweisung wird konstruiert und dann dem `UserQuery.FetchXml`-Attribut zugewiesen. Diese Abfrage kann ausgeführt werden, indem Sie die Nachricht <xref:Microsoft.Crm.Sdk.Messages.ExecuteByIdUserQueryRequest> verwenden.  
  
 Sie können die Benutzerabfrage im Bereich **Erweiterte Suche** der modellgestützten App sowie auch in der Dropdown-Liste **Ansicht** für eine Entität anzeigen.  Sie können den Wert des Attributs `UserQuery.FetchXml` mithilfe der Schaltfläche **FetchXML herunterladen** im Dialogfeld **Erweiterte Suche** exportieren.  
  
## <a name="use-web-api-to-execute-saved-queries"></a>Verwenden der Web-API zum Ausführen gespeicherter Abfragen

Informationen zum Ausführen der Benutzerabfrage und gespeicherten Abfrage mithilfe der Web-API finden Sie unter [Abrufen und Ausführen von vordefinierten Abfragen](webapi/retrieve-and-execute-predefined-queries.md).

## <a name="use-organization-service-to-execute-saved-queries"></a>Verwenden Sie den Organisationsservice, um gespeicherte Abfragen auszuführen

Sie können die Messages <xref:Microsoft.Crm.Sdk.Messages.ExecuteByIdUserQueryRequest> und <xref:Microsoft.Crm.Sdk.Messages.ExecuteByIdSavedQueryRequest> verwenden, um die Benutzerabfrage bzw. die gespeicherte Abfrage auszuführen.
