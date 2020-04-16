---
title: 'Beispiel: Freigabe eines Warteschlangenelements für die Warteschlange mit (Common Data Service) | Microsoft-Dokumentation'
description: Dieses Beispiel veranschaulicht, wie die Message ReleaseToQueueRequest verwendet wird.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: pehecke
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
ms.openlocfilehash: 8a90f3c93ccf70e5a296ab01fce596947e933d78
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155674"
---
# <a name="sample-release-a-queue-item-to-the-queue"></a>Beispiel: Freigabe eines Warteschlangenelements zur Warteschlange

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-release-queue-item-queue-early-bound
Couldn't each of the operations in this series of samples be added to just one sample?
 -->
Dieses Beispiel zeigt, wie Sie [ReleaseToQueueRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.releasetoqueuerequest?view=dynamics-general-ce-9) verwenden können, um die Zuordnung eines Benutzers zu einem Warteschlangenelement, an dem er gearbeitet hat, aufzuheben und das Warteschlangenelement wieder für die Warteschlange freizugeben. Sie können das Beispiel [hier](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/ReleaseQueueItems) herunterladen.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Funktionsweise:

Die Message `ReleaseToQueueRequest` soll in einem Szenario verwendet werden, in dem sie Daten enthält, die erforderlich sind, um ein Warteschlangenelement wieder einem Warteschlangeeigentümer zuzuweisen, sodass andere Benutzer auf sie zugreifen können.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

1. Prüft auf aktuelle Version der Organisation.
2. Die Message `Queue` erstellt eine neue Warteschlange und speichert ihre zurückgegebenen GUIDs in einer Variablen.
3. Die Message `QueueItem` erstellt eine neue Instanz eines Warteschlangenelements und initialisiert dessen Eigenschaften.
4. `WhoAMIRequest` ruft die aktuellen Benutzerinformationen ab.

### <a name="demonstrate"></a>Demonstrieren

Die Message `ReleaseToQueueRequest` entfernt Mitarbeiter vom Warteschlangenelement, um ein in der Warteschlange stehendes Objekt aus der Warteschlange des Mitarbeiters freizugeben.

### <a name="clean-up"></a>Bereinigung

Zeigt eine Option an, um die Beispieldaten zu löschen, die in [Einrichtung](#setup)erstellt wurden. Das Löschen ist optional, falls Sie die Entitäten und Daten durchsuchen möchten, die durch das Beispiel erstellt wurden. Sie können die Datensätze manuell löschen, um das gleiche Ergebnis zu erzielen.
