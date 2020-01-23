---
title: 'Beispiel: Einen Datensatz mit Upsert einfügen oder aktualisieren (Common Data Service) | Microsoft-Dokumentation'
description: Dieses Beispiel zeigt, wie Datensätze mithilfe der Message Upsert eingefügt oder aktualisiert werden.
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
ms.openlocfilehash: e1157acd76f9f6cb83286e3b5066be52b7545256
ms.sourcegitcommit: 5ec7c7f04fe41896dec966706a3b3d295648726f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/06/2020
ms.locfileid: "2934278"
---
# <a name="sample-insert-or-update-a-record-using-upsert"></a>Beispiel: Einen Datensatz mit Upsert einfügen oder aktualisieren

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-insert-update-record-upsert -->

Dieser Beispielcode zeigt, wie Datensätze mithilfe der Message Upsert eingefügt oder aktualisiert werden [UpsertRequest](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.messages.upsertrequest?view=dynamics-general-ce-9). Sie können das Beispiel herunterladen von [hier](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/InsertRecordUsingUpsert).

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Funktionsweise:

Die `UpsertRequest`-Message ist dazu vorgesehen, in einem Szenario verwendet zu werden, in dem sie die Daten enthält, die zur Aktualisierung eines vorhandenen Datensatzes benötigt werden.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

1. Prüft die aktuelle Version der Organisation.
1. Importieren einer verwalteten Lösung UpsertSample_1_0_0_0_managed.zip () die eine Entität erstellen, `sample_product` die einen Alternativschlüssel namens `sample_productcode` hat. Stellen Sie sicher, dass die Indizes, um den Alternativschlüssels zu unterstützen aktiv sind.

### <a name="demonstrate"></a>Demonstrieren

1. Die `ProcessUpsert` Methode verarbeite Daten in `newsampleproduct.xml`, um neue Produkte darzustellen  und 13 neue Datensätze zu erstellen.
1. Beim zweiten Aufrufen der `ProcessUpsert`-Methode erfolgt die Verarbeitung von Daten in der `updatedsampleproduct.xml`-Datei, um Aktualisierungen der zuvor erstellten Produkte darzustellen. 
1. Die `UpsertRequest`-Methode erstellt 6 aktualisierte Firmendatensätze. 

### <a name="clean-up"></a>Bereinigung

Zeigt eine Option an, um verwaltete Lösungen zu löschen, die in [Einrichtung](#setup)erstellt wurden. Das Löschen ist optional, falls Sie die Entitäten und Daten durchsuchen möchten, die durch das Beispiel erstellt wurden. Sie können die Datensätze manuell löschen, um das gleiche Ergebnis zu erzielen.
