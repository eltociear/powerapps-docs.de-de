---
title: 'Beispiel: Verwenden von Lösungen (Common Data Service) | Microsoft-Dokumentation'
description: In diesem Beispiel wird das Arbeiten mit Lösungen dargestellt
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: pehecke
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
ms.openlocfilehash: 6a85a4643b5cc15f2c258893e538de96ef95231b
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155490"
---
# <a name="sample-work-with-solutions"></a>Beispiel: Verwenden von Lösungen

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-work-solutions -->

Dieses Beispiel veranschaulicht die Ausführung der folgenden Aktionen mithilfe von Lösungen:

- Erstellen eines Herausgebers.
- Abrufen des Standardherausgebers.
- Erstellen einer Lösung.
- Abrufen einer Lösung.
- Hinzufügen einer vorhandenen Lösungskomponente.
- Entfernen einer Lösungskomponente.
- Exportieren oder Packen einer Lösung.
- Installieren oder Aktualisieren einer Lösung.
- Löschen einer Lösung.

Sie können das Beispiel von [hier](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/WorkwithSolutions) herunterladen.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Funktionsweise:

In diesem Beispiel wird das Arbeiten mit Lösungen dargestellt. Dieses Beispiel befasst sich damit, wie ein Herausgeber erstellt wird, eine Lösung erstellt wird, eine Lösung exportiert und importiert wird sowie auch wie die Lösung gelöscht wird.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

1. Prüft auf aktuelle Version der Organisation.
1. Die `Publisher`-Methode definiert einen neuen Herausgeber. 
1. Die `Solution`-Methode erstellt eine neue Lösung.
1. Die `OptionSetMetadata`-Methode fügt eine Lösungskomponente hinzu.
1. Die `ExportSolutionRequest`-Methode exportiert die erstellte Lösung im [Setup](#setup).
1. Die `DeleteSolutionRequest`-Methode löscht die Lösung und die Komponenten.

### <a name="demonstrate"></a>Demonstrieren

1. Die `querySDKSamplePublisher`-Methode überprüft, ob der Herausgeber bereits im System vorhanden ist.
1. Die `querySampleSolutionResults`-Methode überprüft, ob die Lösung bereits im System vorhanden ist.
1. Die `ExportSolutionRequest`-Methode exportiert die Lösung.
1. Die `ImportSolutionRequest`-Methode importiert die Lösung.

### <a name="clean-up"></a>Bereinigung

Zeigt eine Option zum Löschen aller im Beispiel erstellten Daten an. Das Löschen ist optional, falls Sie die Daten überprüfen möchten, die durch das Beispiel erstellt wurden. Sie können die Daten manuell löschen, um das gleiche Ergebnis zu erzielen.
