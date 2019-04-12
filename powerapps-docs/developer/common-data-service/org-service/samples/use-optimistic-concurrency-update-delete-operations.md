---
title: 'Beispiel: Nutzung der optimistischen Parallelität mit Aktualisierungs- und Löschaktivitäten (Common Data Service) | Microsoft Docs'
description: Dieses Beispiel zeigt die Nutzung der optimistischen Parallelität mit Aktualisierungs- und Löschaktivitäten.
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
# <a name="sample-use-optimistic-concurrency-with-update-and-delete-operations"></a>Beispiel: Nutzung der optimistischen Parallelität mit Aktualisierungs- und Löschaktivitäten

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/org-service/sample-use-optimistic-concurrency-update-delete-operations -->

Dieses Beispiel zeigt die Nutzung der optimistischen Parallelität mit Aktualisierungs- und Löschaktivitäten. Sie können das Beispiel [hier](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/OptimisticConcurrency) herunterladen.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]


## <a name="what-this-sample-does"></a>Funktionsweise:

Die `UpdateRequest`-Klasse ist dazu vorgesehen, in einem Szenario verwendet zu werden, in dem sie die Daten enthält, die zur Aktualisierung eines vorhandenen Datensatzes benötigt werden.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

1. Prüft auf aktuelle Version der Organisation.
1. Die `Account`-Methode erstellt einen Firmendatensatz.

### <a name="demonstrate"></a>Demonstrieren

1. Ruft die Firmendatensätze ab, die im [Setup](#setup) erstellt werden.
1. Aktualisiert den Firmendatensatz, indem das `creditlimit`-Attribut erhöht wird.
1. Die `UpdateRequest`-Methode legt das Verhalten der Parallelität der Anfrage fest, um nach einer Übereinstimmung mit den Zeilenversionen zu suchen.

### <a name="clean-up"></a>Bereinigung

1. Zeigt eine Option zum Löschen aller im Beispiel erstellten Daten an.

Das Löschen ist optional, falls Sie die Daten überprüfen möchten, die durch das Beispiel erstellt wurden. Sie können die Daten manuell löschen, um das gleiche Ergebnis zu erzielen.
