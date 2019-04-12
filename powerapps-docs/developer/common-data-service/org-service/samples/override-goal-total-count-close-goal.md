---
title: 'Beispiel: Überschreiben der Zielgesamtanzahl und Schließen des Ziels (Common Data Service) | Microsoft Docs'
description: 'Dieses Beispiel zeigt, wie Sie die Zielgesamtanzahl überschreiben und das Ziel schließen.'
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
# <a name="sample-override-goal-total-count-and-close-the-goal"></a>Beispiel: Überschreiben einer Zielgesamtanzahl und Schließen des Ziels

Dieses Beispiel zeigt, wie Sie die Zielgesamtanzahl überschreiben und das Ziel schließen. Sie können das Beispiel [hier](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/OverrideGoalTotal) herunterladen.

Dieses Beispiel benötigt weitere Benutzer, die nicht in Ihrem System sind. Erstellen Sie den erforderlichen Benutzer manuell **wie besehen** in **Office 365**. Ersetzen Sie `yourorg` durch den `OrgName` Ihrer Organisation.

**Vorname**: Samantha<br/>
**Nachname**: Smith<br/>
**Sicherheitsrolle**: Marketing Manager<br/>
**Benutzername**: ssmith@yourorg.onmicrosoft.com<br/>

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Funktionsweise:


Dieses Beispiel zeigt, wie Sie die Zielgesamtanzahl überschreiben und das Ziel schließen.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

1. Tests für die Version der Organisation.
2. Ruft den Vertriebsmanager ab, der manuell in **Office 365** erstellt wurde.
3. Erstellt einen `PhoneCall`-Datensatz und den unterstützenden Firmendatensatz für das Beispiel.
4. Erstellt ActivityPartys für das "Von"-Feld von Telefonanrufen.
5. Erstellt einen offenen Telefonanruf.
6. Schließt den ersten Telefonanruf und erstellt einen zweiten.
7. Schließt den zweiten Telefonanruf.

### <a name="demonstrate"></a>Demonstrieren

1. Erstellt Metrik und legt den Metriktyp auf `count` und `IsAmount` auf "false" fest.
2. `RollupFields` erstellt ein Rollupfeld, das auf abgeschlossene (empfangene) Telefonanrufe ausgerichtet ist.
3. `GoalRollupQuery` erstellt die Zielrollupabfragen zum Lokalisieren der ein- und ausgehenden abgeschlossenen Telefonanrufe. 
4. Erstellt ein Ziel, um die offenen eingehenden Telefonanrufe nachzuverfolgen.
5. `RecalculateRequest` berechnet den Rollup für Ziele. 
6. Überschreibt die tatsächlichen und in Verarbeitung befindlichen Werte für das Ziel.
7. `goal.IsOverridden =true` verhindert, dass die Rollup-Werte während der nächsten Neuberechnung überschrieben werden.

### <a name="clean-up"></a>Bereinigung

1. Zeigt eine Option an, um die Beispieldaten zu löschen, die in [Einrichtung](#setup)erstellt wurden.

    Das Löschen ist optional, falls Sie die Entitäten und Daten durchsuchen möchten, die durch das Beispiel erstellt wurden. Sie können die Datensätze manuell löschen, um das gleiche Ergebnis zu erzielen.
