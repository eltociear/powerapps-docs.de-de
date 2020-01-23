---
title: " Initialisieren eines Datensatzes aus einem bestehenden Datensatz (Common Data Service) | Microsoft-Dokumentation"
description: In diesem Beispiel wird gezeigt, wie aus einem vorhandenen Datensatz ein neuer Datensatz erstellt wird.
ms.custom: ''
ms.date: 12/20/2019
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
ms.openlocfilehash: dbc1e734459ccfdd1a541e850d9c798f45297eee
ms.sourcegitcommit: 5ec7c7f04fe41896dec966706a3b3d295648726f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/06/2020
ms.locfileid: "2934558"
---
# <a name="initailize-a-record-from-existing-record"></a>Initialisieren eines Datensatzes aus einem vorhandenen Datensatz

Dieses Beispiel zeigt, wie Sie die Nachricht [IOrganizationService.InitializeFromRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.initializefromrequest?view=dynamics-general-ce-9) verwenden, um neue Datensätze aus einem vorhandenen Datensatz zu erstellen. Sie können das Beispiel von [hier](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/InitializeRecordFromExisting) herunterladen.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Funktionsweise:

Die Nachricht `IOrganizationService.InitializeFromRequest` ist für die Verwendung in einem Szenario vorgesehen, in dem sie die Daten enthält, die benötigt werden, um einen neuen Datensatz aus einem vorhandenen Datensatz zu initialisieren.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

1. Prüft auf aktuelle Version der Organisation.
2. Die Methode `CreateRequiredRecords` erstellt Entitätsdatensätze, die für dieses Beispiel benötigt werden.


### <a name="demonstrate"></a>Demonstrieren

1. Die `InitializeFromRequest`-Methode erstellt die Anforderung und legt Eigenschaften für das Anforderungsobjekt fest. 
2. Die `InitializeFromResponse`-Methode führt die Anforderung aus.


### <a name="clean-up"></a>Bereinigung

Zeigt eine Option an, um Beispieldaten zu löschen, die in [Einrichtung](#setup)erstellt wurden. Das Löschen ist optional, falls Sie die Entitäten und Daten durchsuchen möchten, die durch das Beispiel erstellt wurden. Sie können die Datensätze manuell löschen, um das gleiche Ergebnis zu erzielen.

