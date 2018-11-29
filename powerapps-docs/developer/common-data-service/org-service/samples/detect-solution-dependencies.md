---
title: 'Beispiel: Erkennen von Lösungsabhängigkeiten (Common Data Service for Apps) | Microsoft Docs'
description: 'Dieses Beispiel zeigt, wie man Abhängigkeiten von Lösungen erkennt.'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: samples
author: shmcarth
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="sample-detect-solution-dependencies"></a>Beispiel: Erkennen von Lösungsabhängigkeiten

Dieses Beispiel zeigt, wie man Abhängigkeiten erkennt, bevor man eine Lösungskomponente löscht.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Funktionsweise:

Die `RetrieveDependentComponentsRequest`, `RetrieveDependenciesForDeleteRequest` Nachrichten sind für die Verwendung in einem Szenario vorgesehen, in dem sie Daten zur Erkennung von Lösungsabhängigkeiten enthalten. Sie können das Beispiel [hier](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/SolutionDependencies) herunterladen.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

1. Prüft auf aktuelle Version der Organisation.
1. Die `Publisher`-Methode erstellt den Beispielherausgeber, der `own` die beiden Lösungen erstellt.
1. Die `Solution`-Methode erzeugt die Primärlösung.
1. Der `OptionSetMetadata` erstellt den globalen Optionssatz und ordnet ihn der Lösung zu.
1. Die `ExportSolutionRequest` exportiert die Lösung als verwaltet, so dass wir sie später importieren können.
1. Die `DeleteOptionSetRequest` löscht die zuvor erstellte Option, so dass sie unter der verwalteten Lösung importiert werden kann.
1. Die `ImportSolutionRequest` importiert die Lösung erneut als verwaltet.

### <a name="demonstrate"></a>Demonstrieren

1. Das `QueryByAttribute` fragt alle Lösungskomponenten nach einer Lösung ab.
1. Die `RetrieveDependentComponentsRequest` ruft alle Abhängigkeiten für die Komponente ab. Wenn es keine Abhängigkeiten gibt, können wir diese Komponente ignorieren. Wenn Abhängigkeiten von dieser Lösungskomponente bestehen und die Lösung selbst verwaltet wird, können Sie die Lösung nicht löschen.
### <a name="clean-up"></a>Bereinigung

1. Zeigt eine Option an, um die Lösungen zu löschen, die in [Einrichtung](#setup)erstellt wurden.

    Das Löschen ist optional, falls Sie die Entitäten und Daten durchsuchen möchten, die durch das Beispiel erstellt wurden. Sie können die Datensätze manuell löschen, um das gleiche Ergebnis zu erzielen.
