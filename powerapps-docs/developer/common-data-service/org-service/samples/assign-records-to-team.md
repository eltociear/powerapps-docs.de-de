---
title: " Zuweisen eines Datensatzes zu einem Team (Common Data Service) | Microsoft-Dokumentation"
description: Dieses Beispiel zeigt, wie Datensätze einem Team zugewiesen werden.
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
ms.openlocfilehash: a2e1bea56c0fa13a3a0d1d5c1bf7c2e55caf791f
ms.sourcegitcommit: 5ec7c7f04fe41896dec966706a3b3d295648726f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/06/2020
ms.locfileid: "2934562"
---
# <a name="assign-a-record-to-a-team"></a>Zuweisen eines Datensatzes an einem Team

Dieses Beispiel zeigt, wie einem Team mithilfe der Meldung [AssignRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.assignrequest?view=dynamics-general-ce-9) ein Datensatz zugewiesen wird.

Sie können das Beispiel von [hier](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/AssignRecordToTeam) herunterladen.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]
## <a name="what-this-sample-does"></a>Funktionsweise:

Die [AssignRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.assignrequest?view=dynamics-general-ce-9)-Meldung soll in einem Szenario verwendet werden, in dem sie die Daten enthält, die erforderlich sind, um den angegebenen Datensatz einem neuen Besitzer(Benutzer oder Team) zuzuweisen, indem das OwnerId-Attribut des Datensatzes geändert wird.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichtung

1. Prüft auf die aktuelle Version der Organisation. 
1. Erstellt die für dieses Beispiel erforderlichen Daten.

### <a name="demonstrate"></a>Demonstrieren

Die Meldung `AssignRequest` weist den für das Beispiel erstellten Firmendatensatz einem Team zu. 

### <a name="clean-up"></a>Bereinigung

Zeigt eine Option zum Löschen aller im Beispiel erstellten Daten an. Das Löschen ist optional, falls Sie die Daten überprüfen möchten, die durch das Beispiel erstellt wurden. Sie können die Daten manuell löschen, um das gleiche Ergebnis zu erzielen.