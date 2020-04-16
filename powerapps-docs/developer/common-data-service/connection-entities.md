---
title: Verwenden Sie Verbindungen, um Datensätze miteinander zu verknüpfen (Common Data Service) | Microsoft-Dokumentation
description: Verbindungsentitaten hilfen Ihnen, die Abfrageverbindungen zu aktivieren und zu erstellen.
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
ms.openlocfilehash: 3365407b4ed719f1b9f6c8eef2a73c81bd0a8b43
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3156354"
---
# <a name="use-connections-to-link-records-to-each-other"></a>Verwenden Sie Verbindungen, um Datensätze miteinander zu verknüpfen

Die *Verbindungen* bieten eine flexible Möglichkeit, um die Beziehungen zwischen zwei Entitätsdatensätzen Common Data Service zu verbinden und zu beschreiben. Sie hilft Ihnen, Teamwork, Zusammenarbeit und die effektive Verwaltung des Unternehmens und der Vertriebsprozesse zu fördern. Mit Verbindungen können Sie problemlos Benutzer, Kontakte, Angebote, Vertriebsaufträge und viele andere Entitätsdatensätze einander zuordnen. Den Datensätzen in der Zuordnung können bestimmte Rollen zugewiesen werden, mit denen der Zweck der Beziehung definiert werden kann.  
  
 Verbindungen bieten die folgenden Funktionen:  
  
- Eine einfache und flexible Möglichkeit, um eine Verbindung zwischen zwei Datensätzen der meisten Common Data Service-Entitätstypen zu erstellen. Alle anpassbaren Geschäfts- und benutzerdefinierten Entitäten können für Verbindungen aktiviert werden.  
  
- Eine Option zum Hinzufügen von nützlichen Informationen, wie eine Beschreibung der Verbindung und der Dauer.  
  
- Die Möglichkeit, Verbindungsrollen zu erstellen, die die Beziehung zwischen zwei Datensätzen beschreiben, z. B. die Beziehung zwischen einem Doktor und einem Patienten oder einem Manager und einem Mitarbeiter.  
  
- Eine schnelle Möglichkeit, um mehrere Verbindungen und Rollen für einen bestimmten Datensatz zu erstellen. Beispielsweise kann ein Kontakt viele Beziehungen mit anderen Kontakten, Firmen oder Verträgen haben. In jeder Beziehung kann ein Kontakt eine andere Rolle spielen.  
  
- Informationen zum Erstellen von Abfragen und Diagrammen. Sie können nach allen Verbindungen und Verbindungsrollen für einen bestimmten Datensatz suchen und Grafiken und Diagramme für die visuelle Darstellung von Verbindungen erstellen.  
  
- Unterstützung für Workflows und die Überprüfung zur Automatisierung und Verbesserung der Geschäftsprozesse.  
  
## <a name="enabling-and-creating-connections"></a>Aktivieren und Erstellen von Verbindungen  
 Sie können eine beliebige benutzerdefinierte oder anpassbare Entität für die Verbindung erstellen, indem Sie die Entitätsmetadaten aktualisieren. Verwenden Sie die Meldung <xref:Microsoft.Xrm.Sdk.Messages.UpdateEntityRequest>, um die Eigenschaft <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.IsConnectionsEnabled> auf `true` festzulegen.  
  
 Wenn Sie eine Verbindung zwischen zwei Datensätzen erstellen möchten, verwenden Sie die `Connection`-Entität. Sie müssen einen Datensatz angeben, aus dem Sie eine Verbindung (Quelle) und einem Datensatz erstellen, zu dem Sie eine Verbindung herstellen (Ziel). Verwenden Sie das Attribut `Connection.Record1Id`, um den Quellentitätsdatensatz und das `Connection.Record2Id`-Attribut anzugeben, um den Zielentitätsdatensatz anzugeben. Optional können Sie die Dauer der Verbindung und der Beschreibung angeben. Um die Beziehung zwischen den Teilnehmern in der Verbindung zu beschreiben, verwenden Sie Verbindungsrollen. Um die Verbindungsrollen anzugeben, verwenden Sie das `Connection.Record1RoleId`- und das `Connection.Record2RoleId`-Attribut.  
  
## <a name="querying-connections"></a>Abfragen von Verbindungen  
 Bei Abfragen von Verbindungen erhalten Sie wertvolle Daten, die Sie verwenden können, um Berichte, Grafiken oder Diagramme zu erstellen. Sie können Verbindungen über einen Datensatz, über einen Entitätstyp (Entitätstypcode), über eine bestimmte Rolle oder über andere Kriterien abfragen. Nachfolgend finden Sie Beispiele dafür, wie Sie Verbindungen abfragen können:  
  
 Über einen Entitätsdatensatz:  
  
- Zeigen Sie alle Verbindungen für Firma A. an.  
  
- Zeigen Sie alle Rollen für Firma A. an.  
  
  Über einen Entitätstyp (unter Verwendung von Entitätstypcodes):  
  
- Zeigen Sie alle Rollen für die Mitbewerberentität an.  
  
- Suchen Sie die Gesamtanzahl an Rollen für die Firmenentität.  
  
  Über eine Rolle:  
  
- Suchen Sie alle Verbindungen, in denen Firma A ein "Anbieter" ist.  
  
- Suchen Sie alle Verkaufschancen über 20.000 $ein, in denen Kontakt B ein "Vertriebsmitarbeiter" ist.  
  
- Suchen Sie alle entsprechenden Rollen für eine "Doktorrolle", wie "Patient", "Krankenschwester" oder "Assistenzarzt".  
  
- Suchen Sie alle Kontakte, die die Rolle "Freund" haben.  
  
> [!IMPORTANT]
>  Wenn Sie einen Verbindungsentitätsdatensatz erstellen, werden zwei Datensätze in der Datenbank erstellt. Der erste Datensatz stellt eine Quelle zur Zielverbindung dar, und der zweite Datensatz stellt ein Ziel zu einer Quellverbindung dar. Dadurch wird sichergestellt, dass eine Abfrage alle Verbindungen sucht, an denen der Datensatz teilnimmt, unabhängig davon, ob der Datensatz ein Quelldatensatz oder ein Zieldatensatz in der Verbindung ist.  
  
### <a name="see-also"></a>Siehe auch  
 [Beschreiben einer Beziehung zwischen den Entitäten mit Verbindungsrollen](describe-relationship-entities-connection-roles.md)   
 [Verbindungsentität](/reference/entities/connection.md)   
 [Verbindungsentität](/reference/entities/connectionrole.md)   
 [Beispielcode für Verbindungsentitäten](/dynamics365/customer-engagement/developer/sample-code-connection-entities)   
 [Unternehmensmanagement-Entitäten](/dynamics365/customer-engagement/developer/business-management-entities)   
 [Anzeigen und Analysieren von Daten mit Visualisierungen und Dashboards in Dynamics 365](/dynamics365/customer-engagement/developer/customize-dev/customize-visualizations-dashboards)   
 [Geschäftskalender- und Gebietsentitäten](/dynamics365/customer-engagement/developer/fiscal-calendar-and-territory-entities)