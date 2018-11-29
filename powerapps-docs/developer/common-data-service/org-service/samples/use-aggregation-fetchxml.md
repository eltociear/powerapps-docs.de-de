---
title: 'Beispiel: Verwendung von Aggregation in FetchXML (Common Data Service für Apps) | Microsoft Docs'
description: 'Dieses Beispiel zeigt, wie aggregierte Datensatzdaten mithilfe von FetchXMLs abgerufen werden.'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: samples
author: brandonsimons
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="sample-use-aggregation-in-fetchxml"></a>Beispiel: Verwendung von Aggregation in FetchXML

<!-- https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/org-service/sample-use-aggregation-fetchxml -->

Dieses Beispiel zeigt, wie aggregierte Datensatzdaten mithilfe von FetchXMLs abgerufen werden.

## <a name="what-this-sample-does"></a>Funktionsweise:

Die `FetchXML`-Abfrage soll in einem Szenario verwendet werden, in der sie in Abfragen erstellt, um die Daten abzurufen.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

1. Prüft auf aktuelle Version der Organisation.
1. Diese `CreateRequiredRecords`-Klasse erstellt 3 Verkaufschancendatensätze und Firmendatensätze.

### <a name="demonstrate"></a>Demonstrieren

1. `estimatedvalue_avg` ruft den Durchschnitt des geschätzten Werts für alle Verkaufschancen ab. Die `EntityCollection`-Methode gibt die Ergebnisse der `RetrieveMultiple`-Abfrage zurück.
1. `opportunity_count` ruft die Anzahl aller Verkaufschancen ab.
1. `estimatedvalue_max` ruft den maximal geschätzten Wert aller Verkaufschancen ab.
1. `estimatedvalue_min` ruft den minimal geschätzten Wert aller Verkaufschancen ab.
1. `estimatedvalue_sum` ruft die Summe des geschätzten Werts für alle Verkaufschancen ab.
1. `estimatedvalue_avg2` ruft mehrere Gesamtwerte in einer einzelnen Abfrage ab.
1. `groupby1` ruft eine Liste der Benutzer mit der Anzahl aller Verkaufschancen, die sie besitzen, mithilfe von GroupBy ab.
1. `byyear` ruft die Gesamtinformationen zu allen Verkaufschancen, die gewonnen wurden, nach Jahren ab.
1. `byquarter` ruft die Gesamtinformationen zu den Verkaufschancen, die gewonnen wurden, nach Quartalen ab.
1. `bymonth` ruft die Gesamtinformationen zu den Verkaufschancen, die gewonnen wurden, nach Monaten ab.
1. `byweek` ruft die Gesamtinformationen zu den Verkaufschancen, die gewonnen wurden, nach Wochen ab.
1. `byday` ruft die Gesamtinformationen zu den Verkaufschancen, die gewonnen wurden, nach Tagen ab.
1. `byyrqtr` ruft die Gesamtinformationen zu den Verkaufschancen, die gewonnen wurden, nach Jahren und Quartalen ab.
1. `byyrqtr2` gibt die Ergebnisreihenfolge an. 


### <a name="clean-up"></a>Bereinigung

1. Zeigt eine Option zum Löschen aller im Beispiel erstellten Daten an.

Das Löschen ist optional, falls Sie die Daten überprüfen möchten, die durch das Beispiel erstellt wurden. Sie können die Daten manuell löschen, um das gleiche Ergebnis zu erzielen.
