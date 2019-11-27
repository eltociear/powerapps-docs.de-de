---
title: 'Beispiel: Warteschlangenelement zum Bearbeiten angeben (Common Data Service) | Microsoft-Dokumentation'
description: Dieses Beispiel zeigt, wie Sie einen Benutzer angeben, der ein Warteschlangenelement bearbeitet
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
ms.openlocfilehash: 9f2c10cbe8dbbff691179977913b42c01588235b
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748711"
---
# <a name="sample-specify-a-queue-item-to-work-on"></a>Beispiel: Ein zu bearbeitendes Warteschlangenelement angeben

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-specify-queue-item-work-early-bound -->

Dieses Beispiel zeigt, wie Sie [PickFromQueueRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.pickfromqueuerequest?view=dynamics-general-ce-9) verwenden, um einen Benutzer anzugeben, der ein Warteschlangenelement bearbeitet. Sie können das Beispiel von [hier](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/SpecifyQueueItem) herunterladen.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Funktionsweise:

Die `PickFromQueueRequest`-Nachricht soll in einem Szenario verwendet werden, in dem sie Daten enthält, die erforderlich sind, um ein Warteschlangenelement einem Benutzer zuzuweisen und optional das Warteschlangenelement aus der Warteschlange zu entfernen.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

1. Prüft auf aktuelle Version der Organisation.
2. Die `Queue`-Methode erstellt eine private Warteschlangeninstanz und legt die Eigenschaftswerte fest.
3. Die `QueueItem`-Methode erstellt eine neue Instanz des Warteschlangenelements und initialisiert dessen Eigenschaften.

### <a name="demonstrate"></a>Demonstrieren

1. Die `WhoAmIRequest`-Methode ruft die aktuellen Benutzerinformationen ab.
1. Die `PickFromQueueRequest`-Methode erstellt eine Instanz eines vorhandenen Warteschlangenelements, um den Benutzer anzugeben, der daran arbeitet.


### <a name="clean-up"></a>Bereinigung

1. Zeigt eine Option an, um Beispieldaten zu löschen, die in [Einrichtung](#setup)erstellt wurden.

    Das Löschen ist optional, falls Sie die Entitäten und Daten durchsuchen möchten, die durch das Beispiel erstellt wurden. Sie können die Datensätze manuell löschen, um das gleiche Ergebnis zu erzielen.
