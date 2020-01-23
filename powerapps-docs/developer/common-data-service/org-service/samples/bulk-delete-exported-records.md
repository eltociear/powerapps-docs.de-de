---
title: 'Beispiel: Massenlöschung exportierter Datensätze (Common Data Service) | Microsoft-Dokumentation'
description: In diesem Beispiel wird gezeigt, wie Sie eine Massenlöschung von Datensätzen ausführen
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
ms.openlocfilehash: 8b690bb3a7a27c278c9354073f5e4140dfe33b4d
ms.sourcegitcommit: 5ec7c7f04fe41896dec966706a3b3d295648726f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/06/2020
ms.locfileid: "2934410"
---
# <a name="sample-bulk-delete-exported-records"></a>Beispiel: Massenlöschung exportierter Datensätze

Dieses Beispiel zeigt, wie eine Massenlöschung von Datensätzen durchgeführt wird, die zuvor aus Common Data Service exportiert wurden, indem die Option **Exportieren nach Excel** verwendet wurde. Sie können das Beispiel [hier](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/BulkDeleteExported) herunterladen.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Funktionsweise:

Die `BulkDeleteRequest`-Message ist für die Verwendung in einem Szenario vorgesehen, in dem sie Daten enthält, die für die Erstellung des Massenlöschungsanfrage erforderlich sind.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

1. Prüft auf aktuelle Version der Organisation.
2. Abfrage, ob ein Systembenutzer eine E-Mail senden soll, nachdem der Vorgang zum Löschen von Massenanfragen abgeschlossen ist.
3. Die `BulkDeleteRequest` erstellt den Massenlöschungsprozess und setzt die Eigenschaften der Anforderung.
4. Die `CheckSuccess`-Methode fragt den `BulkDeleteOperation` ab, bis er abgeschlossen ist oder bis die angegebene Zeit abgelaufen ist. Anschließend wird überprüft, ob der Vorgang abgeschlossen ist.

### <a name="demonstrate"></a>Demonstrieren

Die `PerformBulkDeleteBackup`-Methode führt den Hauptlöschvorgang bei inaktiven Verkaufschancen und Aktivitäten durch, um sie aus dem System zu entfernen.

### <a name="clean-up"></a>Bereinigung

Zeigt eine Option an, um Beispieldaten zu löschen, die in [Einrichtung](#setup)erstellt wurden. Das Löschen ist optional, falls Sie die Entitäten und Daten durchsuchen möchten, die durch das Beispiel erstellt wurden. Sie können die Datensätze manuell löschen, um das gleiche Ergebnis zu erzielen.
