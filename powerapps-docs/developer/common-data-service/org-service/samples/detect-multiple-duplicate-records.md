---
title: 'Beispiel: Erkennen von Mehrfachduplikat-Datensätzen (Common Data Service for Apps) | Microsoft Docs'
description: 'Dieses Beispiel veranschaulicht, wie mehrere doppelte Datensätze für einen angegebenen Entitätstyp erkannt und protokolliert werden können.'
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
# <a name="sample-detect-multiple-duplicate-records"></a>Beispiel: Erkennen von mehreren doppelten Datensätzen

Dieses Beispiel veranschaulicht, wie mehrere doppelte Datensätze für einen angegebenen Entitätstyp erkannt und protokolliert werden können.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Funktionsweise:

Die Meldung `BulkDetectDuplicatesRequest` ist für die Verwendung in einem Szenario vorgesehen, das Daten enthält, die für die Übermittlung eines asynchronen Systemauftrags erforderlich sind, der mehrere doppelte Datensätze erkennt und protokolliert. Sie können das Beispiel von [hier](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/DetectMultipleDuplicateRecords) herunterladen.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

1. Prüft auf aktuelle Version der Organisation.
1. Die `CreateRequiredRecords`-Klasse erstellt einige Duplikatentitätsdatensätze für dieses Beispiel.
1. Die `DuplicateRule`-Methode erstellt eine Duplikaterkennungsregel.
1. Die `DuplicateRuleCondition`-Methode erstellt eine -Regelbedingung zum Erkennen von Duplikatsdatensätzen.
1. Die `PublishDuplicateRuleRequest`-Methode veröffentlicht die Duplikaterkennungsregel.
1. Die `PublishDuplicateRuleRequest` wird zurückgegeben, bevor die Veröffentlichung abgeschlossen ist, daher rufen wir den Zustand des asynchronen Auftrags so lange ab, bis er `Completed` ist.

### <a name="demonstrate"></a>Demonstrieren

1. Die `BulkDetectDuplicatesRequest`-Methode erstellt das BulkDetectDuplicatesRequest-Objekt.

### <a name="clean-up"></a>Bereinigung

1. Zeigt eine Option an, um die Datensätze zu löschen, die in der [Einrichtung](#setup)erstellt wurden.

    Das Löschen ist optional, falls Sie die Entitäten und Daten durchsuchen möchten, die durch das Beispiel erstellt wurden. Sie können die Datensätze manuell löschen, um das gleiche Ergebnis zu erzielen.

