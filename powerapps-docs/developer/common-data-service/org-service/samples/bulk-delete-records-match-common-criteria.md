---
title: 'Beispiel: Massenlöschung von Datensätzen in großen Mengen, die gemeinsamen Kriterien entsprechen (Common Data Service) | Microsoft-Dokumentation'
description: Dieses Beispiel zeigt das Massenlöschen von Datensätzen, die allgemeinen Kriterien entsprechen.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 45e3413a37887a5a2ee826f7ff6150edec73186a
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748385"
---
# <a name="sample-bulk-delete-records-that-match-common-criteria"></a>Beispiel: Massenlöschen von Datensätzen, die allgemeinen Kriterien entsprechen

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-bulk-delete-records-match-common-criteria -->

Dieses Beispiel zeigt das Massenlöschen von Datensätzen, die allgemeinen Kriterien entsprechen. Sie können das Beispiel von [hier](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/BulkDeleteMatchCriteria) herunterladen.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Funktionsweise:

Die `BulkDeleteRequest`-Message ist für die Verwendung in einem Szenario vorgesehen, in dem sie Daten enthält, die für die Erstellung des Massenlöschungsanfrage erforderlich sind.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

1. Prüft auf aktuelle Version der Organisation.
2. Einen Beispiel-Firmendatensatz erstellen.
3. Abfrage, ob einem Systembenutzer eine E-Mail gesendet werden soll, nachdem der Vorgang zum Löschen von Massenanfragen abgeschlossen ist.
3. Die `BulkDeleteRequest` erstellt den Massenlöschungsprozess und setzt die Eigenschaften der Anforderung.
4. Die `InspectBulkDeleteOperation`-Methode prüft und zeigt die Informationen über die erstellte `BulkDeleteOperation` an.
5. Die `RetrieveBulkDeleteOperation`-Methode ruft die `BulkDeleteOperation` ab.

### <a name="demonstrate"></a>Demonstrieren

1. Überprüft, ob Standard-E-mail-Vorlagen vorhanden sind.
1. Die `PerformBulkDelete`-Methode führt den Haupt-Löschvorgang durch.

### <a name="clean-up"></a>Bereinigung

1. Zeigt eine Option an, um Beispieldaten zu löschen, die in [Einrichtung](#setup)erstellt wurden.

    Das Löschen ist optional, falls Sie die Entitäten und Daten durchsuchen möchten, die durch das Beispiel erstellt wurden. Sie können die Datensätze manuell löschen, um das gleiche Ergebnis zu erzielen.
