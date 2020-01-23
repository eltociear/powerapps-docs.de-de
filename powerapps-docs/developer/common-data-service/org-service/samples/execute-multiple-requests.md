---
title: 'Beispiel: Ausführen mehrere Anfragen (Common Data Service) | Microsoft-Dokumentation'
description: Dieses Beispiel zeigt, wie Sie mehrere Organisationsnachrichtenanforderungen mithilfe eines einzelnen Webdienst-Methodenaufrufs ausführen und als Parameter übergeben.
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
ms.openlocfilehash: 6f9617f1320de9f9e1ad3d0dc807e76797d98623
ms.sourcegitcommit: 5ec7c7f04fe41896dec966706a3b3d295648726f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/06/2020
ms.locfileid: "2934294"
---
# <a name="sample-execute-multiple-requests"></a>Beispiel: Ausführen mehrerer Anforderungen

Dieses Beispiel zeigt, wie Sie mehrere Organisationsnachrichtenanforderungen mithilfe eines einzelnen Webdienst-Methodenaufrufs ausführen und als [ExecuteMultipleRequest](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.messages.executemultiplerequest?view=dynamics-general-ce-9) als Parameter übergeben. Das Reduzieren der Anzahl der Nachrichtenanforderungen, die über das Netzwerk gesendet werden müssen, führt zu einer höheren Nachrichtenverarbeitungsleistung.

Sie können das Beispiel herunterladen von [hier](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/ExecutemultipleRequests).

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Funktionsweise:

Die `ExecuteMultipleRequest` Message wird in einem Szenario verwendet werden, in der sie Daten enthält, die erforderlich ist, um mindestens eine Nachrichtenanforderungen als einem Batchbetrieb auszuführen und optional einer Sammlung Ergebnisse zurückgegeben werden.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

1. Prüft auf aktuelle Version der Organisation.

### <a name="demonstrate"></a>Demonstrieren

1. Die `ExecuteMultipleRequest` Methode erstellt das `ExecuteMultipleRequest`-Objekt.
1. Die `ExecutingMultipleSettings` Methode weist Einstellungen zu, die Ausführungsverhalten definiert: auf Fehler fortgahren, Rückantworten.
1. Die `OrganizationRequestCollection` Methode erstellt eine leere Organisationsanforderungssammlung.
1. Die `CreateRequest` Methode ist für jede Entität in Anforderungssammlung hinzugefügt.
1. Diese `GetCollectionOdEntitiesToUpdate`-Klasse aktualisiert die Entitäten, die zuvor erstellt werden.


### <a name="clean-up"></a>Bereinigung

Zeigt eine Option an, um die Datensätze zu löschen, die in der [Einrichtung](#setup)erstellt wurden. Das Löschen ist optional, falls Sie die Entitäten und Daten durchsuchen möchten, die durch das Beispiel erstellt wurden. Sie können die Datensätze manuell löschen, um das gleiche Ergebnis zu erzielen.
