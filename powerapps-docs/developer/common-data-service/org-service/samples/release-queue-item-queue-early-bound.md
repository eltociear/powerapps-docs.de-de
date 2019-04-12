---
title: 'Beispiel: Freigeben eines Warteschlangenelements zur Warteschlange (Common Data Service) | Microsoft Docs'
description: 'Dieses Beispiel veranschaulicht, wie die Message ReleaseToQueueRequest verwendet wird.'
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

1. Die Message `ReleaseToQueueRequest` entfernt Mitarbeiter vom Warteschlangenelement, um ein in der Warteschlange stehendes Objekt aus der Warteschlange des Mitarbeiters freizugeben.

### <a name="clean-up"></a>Bereinigung

1. Zeigt eine Option an, um die Beispieldaten zu löschen, die in [Einrichtung](#setup)erstellt wurden.

    Das Löschen ist optional, falls Sie die Entitäten und Daten durchsuchen möchten, die durch das Beispiel erstellt wurden. Sie können die Datensätze manuell löschen, um das gleiche Ergebnis zu erzielen.
