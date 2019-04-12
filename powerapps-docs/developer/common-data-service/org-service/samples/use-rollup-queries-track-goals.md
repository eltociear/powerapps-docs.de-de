---
title: 'Beispiel: Benutzer-Rollupabfragen zur Nachverfolgung von Zielen (Common Data Service) | Microsoft Docs'
description: In diesem Beispiel wird die Verwendung von Rollupabfragen zur Nachverfolgung von Zielen dargestellt
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
# <a name="sample-use-rollup-queries-to-track-goals"></a>Beispiel: Verwendung von Rollupabfragen zur Nachverfolgung von Zielen

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-use-rollup-queries-track-goals -->

In diesem Beispiel wird die Verwendung von Rollupabfragen zur Nachverfolgung von Zielen dargestellt. Sie können das Beispiel [hier](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/QueriesTrackGoals) herunterladen.

Dieses Beispiel benötigt weitere drei Benutzer, die nicht in Ihrem System sind. Erstellen Sie die drei erforderliche Benutzer manuell**wie dargestellt** in **Office 365**. Ersetzen Sie `yourorg` durch den Namen Ihrer Organisation.

**Vorname**: Nancy<br/>
**Nachname**: Anderson<br/>
**Sicherheitsrolle**: Vertriebsmitarbeiter<br/>
**Benutzername**: nanderson@yourorg.onmicrosoft.com<br/>

**Vorname**: David<br/>
**Nachname**: Bristol<br/>
**Sicherheitsrolle**: Vertriebsmitarbeiter<br/>
**Benutzername**: dbristol@yourorg.onmicrosoft.com<br/>

**Vorname**: Kevin<br/>
**Nachname**: Cook<br/>
**Sicherheitsrolle**: Vertriebsmanager<br/>
**Benutzername**: kcook@yourorg.onmicrosoft.com<br/>

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Funktionsweise:

In diesem Beispiel wird die Verwendung von Rollupabfragen zur Nachverfolgung von Zielen dargestellt.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

1. Prüft auf aktuelle Version der Organisation.
2. Ruft den Vertriebsmanager und 2 Vertriebsmitarbeiter ab, die manuell in **Office 365** erstellt werden.
3. Erstellt Datensätze, um `SalesOrder`-Datensätze zu unterstützen.
4. Erstellt eine neue Einheitengruppe für das Beispiel.
5. Ruft die Standardeinheits-ID ab, die automatisch erstellt wird, wenn wir eine neue Einheitengruppe erstellt haben.
6. `Product` erstellt einige Produkte, die für das Beispiel erforderlich sind.
7. `PriceLevel` erstellt eine neue Preisliste.
8. `ProductPriceLevel` erstellt ein Preislistenelement für das erste Produkt und wendet den Mengenrabatt an.
9. Erstellt einen Firmendatensatz für die potenzielle Kunden-ID des Vertriebsauftrags. 
10. `SalesOrderDetails` fügt das Produkt zum Auftrag hinzu. Dabei wird der Preis mit einem negativen Wert überschrieben.

### <a name="demonstrate"></a>Demonstrieren

1. Erstellt Metrik und legt den Metriktyp auf `Amount` und den Betragsdatentyp auf `Money` fest.
2. `RollupField` erstellt ein Rollupfeld, das auf die tatsächlichen Summen abzielt.
3. `GoalRollupQuery` erstellt die Ziel-Rollupabfragen, wobei sich die Vertriebsaufträge im Gebiet des ersten Vertriebsmitarbeiters (Postleitzahl: 60661) und mit einem Wert von mehr als 1000 $. 
4. Erstellt zwei Ziele, ein übergeordnetes Ziel und ein untergeordnetes Ziel.
5. `RecalculateRequest` berechnet den Rollup für Ziele. 

### <a name="clean-up"></a>Bereinigung

1. Zeigt eine Option an, um die Beispieldaten zu löschen, die in [Einrichtung](#setup)erstellt wurden.

    Das Löschen ist optional, falls Sie die Entitäten und Daten durchsuchen möchten, die durch das Beispiel erstellt wurden. Sie können die Datensätze manuell löschen, um das gleiche Ergebnis zu erzielen.
