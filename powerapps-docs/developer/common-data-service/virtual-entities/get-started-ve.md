---
title: Erste Schritte mit virtuellen Entitäten (Common Data Service) | Microsoft Docs
description: Virtuelle Entitäten ermöglichen die Integration von Daten, die sich auf externen Systemen befinden, indem nahtlos diese Entitäten in Common Data Service repräsentiert werden, ohne Replikation von Daten und oft ohne benutzerdefinierte Codierung.
ms.date: 10/31/2018
ms.service: powerapps
ms.topic: get-started-article
applies_to:
- Dynamics 365 (online)
ms.assetid: 14c5fbbc-98db-4e49-b245-2c84c1cd11cd
author: mayadumesh
ms.author: jdaly
manager: amyla
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: d64aa3a4802917f0ed03dec5c22cafaffcd5ce5f
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "2753702"
---
# <a name="get-started-with-virtual-entities"></a> Erste Schritte mit virtuellen Entitäten

Virtuelle Entitäten ermöglichen die Integration von Daten, die sich auf externen Systemen befinden, indem nahtlos diese Entitäten in Common Data Service repräsentiert werden, ohne Replikation von Daten und oft ohne benutzerdefinierte Codierung. Die ursprüngliche Implementierung dieser Funktion bietet nur schreibgeschützte Unterstützung dieser Entitäten und besitzt eine Reihe weiterer Einschränkungen, die im Abschnitt [Beschränkungen der virtuellen Entitäten](#limitations-of-virtual-entities) weiter unten beschrieben sind. Außer diesen Beschränkungen verhalten sich virtuelle Entitäten identisch wie andere benutzerdefinierte Entitäten. 

Virtuelle Entitäten ersetzen frühere clientseitige und serverseitige Vorgehensweisen zur Integrierung externer Daten, die benutzerdefinierten Code erforderten und litten an zahlreichen Beschränkungen, einschließlich unvollkommener Integration, Datenverdopplung, umfangreiche Beanspruchung von Entwicklungsressourcen.  Außerdem vereinfacht für Administratoren und Systemanpasser die Verwendung virtueller Entitäten Verwaltung und Konfiguration.

> [!NOTE]
> In diesem Abschnitt werden die Auswirkungen von virtuellen Entitäten für Entwickler beschrieben. Weitere Informationen zum Verwalten der virtuellen Entitäten auf der Benutzeroberfläche, siehe [Erstellen und Bearbeiten virtueller Entitäten, die Daten von externen Datenquellen enthalten](../../../maker/common-data-service/create-edit-virtual-entities.md).

## <a name="virtual-entities-data-providers-and-data-sources"></a>Virtuelle Entitäten, Datenanbieter und Datenquellen

Eine virtuelle Entität ist eine Definition einer Entität in den Common Data Service-Plattformmetadaten ohne zugeordnete Tabellen für die physikalischen Entitätsinstanzen, die in der Common Data Service-Datenbank erstellt werden. Stattdessen wird während der Laufzeit, wenn eine Entitätsinstanz erforderlich ist, deren Status vom zugeordneten externen System erhalten. Jeder virtuelle Entitätstyp wird einem *virtuellenEntitätsdatenanbieter* einige Konfigurationsinformationen von einer *virtuellen Entitätsdatenquelle* zugeordnet. 

<!-- TODO:
A data provider is a particular type of Common Data Service plug-in, which is registered against CRUD events that occur in the platform. This initial release only supports READ operations. More information: [Write a plug-in](../write-plugin.md) -->

Die folgenden Datenanbieter werden mit Common Data Service geliefert:
- Ein [OData v4](https://www.odata.org/documentation/) Anbieter ist mit dem Service enthalten und wird standardmäßig installiert.
- Ein [Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db) (füher *Microsoft Document DB*)-Anbieter ist verfügbar von [AppSource](https://appsource.microsoft.com).

Zusätzliche Anbieter werden von Microsoft, seinen Partnern oder anderen Drittanbietern bereitgestellt. Wenn ein Datenanbieter nicht für die externe Datenquelle gefunden werden, können Sie einen *benutzerdefinierten virtuellen Entitätsdatenanbieter* entwickeln, weitere Information, siehe [Virtuelle Entitätsdatenanbieter](custom-ve-data-providers.md).

## <a name="virtual-entity-creation-and-mapping"></a>Virtuelle Entitätserstellung und -Zuordnung

Das Definieren einer virtuellen Entität ist anfänglich das Gleiche wie eine benutzerdefinierte Entität zu definieren: Sie können der Entität Attribute und Beziehungen für den neuen virtuellen Entitätstyp anfügen. Darüber hinaus jedoch schließen Sie die virtuelle Entität an einen Datenanbieter, um Datenabruf zu verwalten. Der Typ der benutzerdefinierten Entität und die Felder müssen den erforderlichen Daten in der externen Datenquelle zugeordnet werden.  Beispielsweise könnte eine virtuelle Entität als Zeile in einer externen relationalen Datenbank repräsentiert werden, und jedes der Felder könnte einer Spalte in dieser Zeile entsprechen.  (Beachten Sie, dass diese externen Datennamen sich oft von den entsprechenden virtuellen Entitätsnamen unterscheiden) Eine spezifische, erforderliche Zuordnung ist für das ID-Feld Entität erforderlich: der Datenanbieter muss diese GUID bereitstellen können und ihn einem externen Datensatz zuordnen, der diese Entitätsinstanz darstellt. Die direktste Möglichkeit, dies zu erreichen ist die Verwendung von GUIDs als Primärschlüssel in der externen Datenquelle.  

In diesem Beispiel würde eine entsprechende virtuelle Entitätsdatenquelle auch bereitgestellt, um Benutzer- und -Verbindungsinformationen für die externe Datenbank bereitzustellen.

## <a name="limitations-of-virtual-entities"></a>Beschränkungen der virtuellen Entitäten

In dieser Version gibt es einige Beschränkungen der virtuellen Entitäten, die Sie kennen müssen beim Auswerten, ob Sie virtuelle Entitäten mit den externen Daten verwenden können.
- Die Daten sind schreibgeschützt. Diese virtuelle Entitätsfunktion unterstützt nicht das Veröffentlichen von Änderungen, die am externen Common Data Service-System vorgenommen werden.
- Nur Entitäten im Besitz der Organisation werden unterstützt. Die Sicherheitsfilterung, die auf Entitäten im Besitz von Benutzern angewendet wird, wird nicht unterstützt. Zugriff den virtuellen Entitätsdaten kann abgeschaltet werden für einzelne Benutzer auf Grundlage ihrer Sicherheitsrolle. Sicherheit auf Feldebene wird nicht unterstützt.
- Es muss möglich sein, die externen Daten als Common Data Service-Entität zu modellieren. Das bedeutet Folgendes:
    - Alle Entitäten in der externen Datenquelle müssen einen GUID-Primärschlüssel zugeordneten haben.  
    - Alle Entitätsattribute müssen als Common Data Service-Attribute dargestellt werden. Sie können einfache Typen verwenden, die Text, Zahlen, Optionsätze, Daten, Bilder und Suchen repräsentieren. 
    - Sie müssen in der Lage sein sollen, alle Entitätsbeziehungen in Common Data Service zu modellieren.
    - Ein Attribut für eine virtuelle Entität kann nicht Rollup oder berechnet werden.  Alle gewünschten Berechnungen müssen auf der externen Seite ausgeführt werden, möglichst im oder geleitet vom Datenanbieter.
    - Obwohl Sie virtuelle Entitätsspalten als Suche in einem Raster oder anderen Benutzeroberflächenansichten hinzufügen können, können Sie nicht anhand dieser virtuelle Entitätssuchenspalte filtern oder sortieren.
- Überwachung und Änderungsnachverfolgung wird nicht unterstützt.  Diese Felder können im externen Datenspeicher implementiert werden.
- Entitäten können nicht für virtuelle Warteschlangen aktiviert werden.
- Offlinezwischenspeichern von Werten wird für virtuelle Entitäten nicht unterstützt.
- Eine virtuelle Entität kann nicht eine Aktivität repräsentieren und unterstützt nicht Geschäftsprozessflüsse.
- Sobald erstellt, kann eine virtuelle Entität nicht geändert werden, um eine (nicht-virtuelle) Standard-Entität zu werden.  Das Umgekehrt auch der Fall: eine Standardentität kann nicht in eine virtuelle Entität konvertiert werden.

Weitere Informationen dazu, wie diese in Beschränkungen sich in der Common Data Service API auswirken, siehe [API-Aspekte von virtuellen Entitäten](api-considerations-ve.md). 

### <a name="see-also"></a>Siehe auch

[API-Rücksichten auf virtuelle Entitäten](api-considerations-ve.md)<br />
[Benutzerdefinierte virtuelle Entitätsdatenanbieter](custom-ve-data-providers.md)<br />
[Beispiel: Generisches virtuelles Entitätsdatenanbieter-Plug-In](sample-generic-ve-plugin.md)
