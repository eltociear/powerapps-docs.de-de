---
title: 'Beispiel: Synchronisieren Sie Daten mit externen Systemen mithilfe des Änderungsnachverfolgungssystems (Common Data Service) | Microsoft-Dokumentation'
description: Dieses Beispiel zeigt, wie Änderungen aus einer Entität abgerufen werden und Daten mit externen Systemen synchronisiert werden.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: samples
author: JimDaly
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: c6b855102f595460fd2324e94fff56a9ccd949d7
ms.sourcegitcommit: 5ec7c7f04fe41896dec966706a3b3d295648726f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/06/2020
ms.locfileid: "2934146"
---
# <a name="sample-synchronize-data-with-external-systems-using-change-tracking"></a>Beispiel: Synchronisieren von Daten mit externen Systemen mithilfe der Änderungsnachverfolgung

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-synchronize-data-external-systems-using-change-tracking -->

Dieser Beispielcode zeigt, wie Änderungen aus einer Entität abgerufen werden und Daten mithilfe der `RetrieveEntityChanges`-Nachricht mit den [RetrieveEntityChangesRequest](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.messages.retrieveentitychangesrequest) und [RetrieveEntityChangesResponse](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.messages.retrieveentitychangesresponse)- Klassen mit externen Systemen synchronisiert werden. Sie können das Beispiel von [hier](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/Changetracking) herunterladen.

Weitere Informationen zur Funktion, die dieses Beispiel veranschaulicht, siehe [Synchronisieren von Daten mit externen Systemen mithilfe der Änderungsnachverfolgung](https://docs.microsoft.com/powerapps/developer/common-data-service/use-change-tracking-synchronize-data-external-systems).
<!-- The link above won't work until the topic is published -->

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Funktionsweise:

Die `RetrieveEntityChanges`-Nachricht soll in einem Szenario verwendet werden, in dem Daten aus einem externen System synchronisiert werden, und die Funktion zur Änderungsnachverfolgung kann verwendet werden, um Datenänderungen zu ermitteln und auszugleichen.

Ohne dass ein separates System erforderlich ist, um dieses Szenario zu replizieren, simuliert dieses Beispiel das Szenario, indem zwei Anfragen ausgeführt werden. Zwischen den Anforderungen werden einige Daten geändert, sodass die zweite Anforderung Daten zurückgibt, zu den Änderungen im Laufe der Zeit.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

1. Importieren einer verwalteten Lösung (ChangeTrackingSample_1_0_0_0_managed.zip) die eine Entität `sample_book` erstellt, die einen Alternativschlüssel namens `sample_bookcode` hat. Stellen Sie sicher, dass die Indizes, um den Alternativschlüssels zu unterstützen, aktiv sind
1. 10 anfängliche sample_book-Entitätsdatensätze werden erstellt, sodass diese Änderungen an diesen Entitäten nachverfolgt werden können.

### <a name="demonstrate"></a>Demonstrieren

1. Führen Sie die anfängliche Abfrage durch und zwischenspeichern Sie die Ergebnisse, einschließlich der `DataToken`
1. Aktualisieren Sie die Datensätze, die in [Setup](#setup) erstellt wurden
1. Führen Sie eine zweite Abfrage aus, diesmal durch den `DataVersion` mit dem `DataToken`-Wert, der aus der ursprünglichen Abfrage abgerufen wurde.
1. Zeigen Sie die Entitätsänderungen an, die durch die zweite Abfrage zurückgegeben wurden

### <a name="clean-up"></a>Bereinigung

Zeigen Sie eine Option an, um die verwaltete Lösung löschen, die in [Setup](#setup) importiert wird, die die `sample_book`-Entität und alle Daten entfernt, die im Beispiel erstellt werden. Das Löschen ist optional, falls Sie die Entitäten und Daten durchsuchen möchten, die durch das Beispiel erstellt wurden. Sie können `ChangeTrackingSample` manuell löschen, um das gleiche Ergebnis zu erzielen.
