---
title: 'Beispiel: Bereinigung des Verlaufs für eine Warteschlange (Common Data Service) | Microsoft Docs'
description: 'In diesem Beispiel wird gezeigt, wie Sie einen Verlauf für eine Warteschlange bereinigen'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: brandonsimons
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="sample-clean-up-history-for-a-queue"></a>Beispiel: Bereinigung des Verlaufs für eine Warteschlange

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-clean-up-history-queue-early-bound -->

 Dieses Beispiel zeigt, wie Sie den Verlauf für die Warteschlange bereinigen können, indem Sie [RemoveFromQueueRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.removefromqueuerequest?view=dynamics-general-ce-9) mit inaktiven Elementen verwenden. Es werden beendete Telefonanrufe in der Warteschlange gefunden und die zugeordneten Warteschlangenelemente werden entfernt. Sie können das Beispiel von [hier](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/CleanHistoryQueue) herunterladen.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Funktionsweise:

Die `RemoveFromQueueRequest`-Nachricht ist für die Verwendung in einem Szenario vorgesehen, um den Warteschlangenverlauf mit inaktiven Elementen zu bereinigen.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

1. Prüft auf aktuelle Version der Organisation.
2. Erstellt eine Warteschlangeninstanz und legt deren Eigenschaftswerte fest.
3. Erstellt eine Telefonanrufaktivitätsinstanz sowie queueitems-Instanz und initialisiert und deren Eigenschaften.
4. Markiert den Telefonanruf als abgeschlossen. 

### <a name="demonstrate"></a>Demonstrieren

1. Ruft queueitem mit inaktiven Telefonanrufen aus einer Warteschlange über die Message [RemoveFromQueueRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.removefromqueuerequest?view=dynamics-general-ce-9) ab.

### <a name="clean-up"></a>Bereinigung

1. Zeigt eine Option an, um die Datensätze zu löschen, die in [Einrichtung](#setup)erstellt wurden.

    Das Löschen ist optional, falls Sie die Entitäten und Daten durchsuchen möchten, die durch das Beispiel erstellt wurden. Sie können die Datensätze manuell löschen, um das gleiche Ergebnis zu erzielen.
