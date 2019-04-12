---
title: 'Beispiel: Rollup für Zieldaten für eine Buchhaltungsperiode für die Streckungszielanzahl (Common Data Service) | Microsoft Docs'
description: Dieses Beispiel veranschaulicht das Rollup von Zieldaten für eine Buchhaltungsperiode für die Streckungszielanzahl.
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
# <a name="sample-rollup-goal-data-for-a-fiscal-period-against-the-stretch-target-count"></a>Beispiel: Rollup für Zieldaten für eine Buchhaltungsperiode für die Streckungszielanzahl

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-rollup-goal-data-fiscal-period-stretch-target-count -->

Dieses Beispiel zeigt, wie ein Rollup der Zieldaten für eine Buchhaltungsperiode für die Streckungszielanzahl zum Darstellen einiger abgeschlossener Telefonanrufe durchgeführt wird. Sie können das Beispiel [hier](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/GoalDataForFiscalYear) herunterladen.

Dieses Beispiel benötigt weitere Benutzer, die nicht in Ihrem System sind. Erstellen Sie die drei erforderliche Benutzer manuell**wie dargestellt** in **Office 365**. Ersetzen Sie `yourorg` durch den Namen Ihrer Organisation.

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

Dieses Beispiel zeigt, wie ein Rollup der Zieldaten für eine Buchhaltungsperiode zum Darstellen einiger abgeschlossener Telefonanrufe durchgeführt wird.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

1. Tests für die Version der Organisation.
2. Ruft den Vertriebsmanager und 2 Vertriebsmitarbeiter ab, die manuell in **Office 365** erstellt werden.
3. Erstellt einen `PhoneCall`-Datensatz und den unterstützenden Firmendatensatz für das Beispiel.
4. Erstellt ActivityPartys für das Feld **Von** von Telefonanrufen.
5. Erstellt einen offenen Telefonanruf.
6. Schließt den ersten Telefonanruf und erstellt einen zweiten.
7. Schließt den zweiten Telefonanruf.

### <a name="demonstrate"></a>Demonstrieren

1. Erstellt die Metrik und legt den Metriktyp auf **Anzahl** fest und aktiviert die Streckungsnachverfolgung.
2. Erstellt ein Rollupfeld, das auf abgeschlossene (empfangene) Telefonanrufe ausgerichtet ist.
3. `GoalRollupQuery` erstellt die Zielrollupabfragen zum Lokalisieren der ein- und ausgehenden abgeschlossenen Telefonanrufe. 
4. Erstellt drei Ziele, ein übergeordnetes Ziel und zwei untergeordnete Ziele.
5. `RecalculateRequest` berechnet den Rollup für Ziele. 

### <a name="clean-up"></a>Bereinigung

1. Zeigt eine Option an, um die Beispieldaten zu löschen, die in [Einrichtung](#setup)erstellt wurden.

    Das Löschen ist optional, falls Sie die Entitäten und Daten durchsuchen möchten, die durch das Beispiel erstellt wurden. Sie können die Datensätze manuell löschen, um das gleiche Ergebnis zu erzielen.
