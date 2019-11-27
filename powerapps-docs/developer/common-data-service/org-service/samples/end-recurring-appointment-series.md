---
title: 'Beispiel: Beenden einer Terminserie (Common Data Service) | Microsoft-Dokumentation'
description: Dieses Beispiel zeigt, wie Sie eine wiederkehrende Terminserie beenden
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
ms.openlocfilehash: 3d2bdec0f2975efd6433ad492bf86ae65dbc28b3
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748747"
---
# <a name="sample-end-a-recurring-appointment-series"></a>Beispiel: Erstellen einer Terminserie

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-end-recurring-appointment-series -->

Das folgende Beispiel zeigt, wie eine wiederkehrende Terminserie mithilfe der [DeleteOpenInstancesRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.deleteopeninstancesrequest?view=dynamics-general-ce-9)-Message abgeschlossen wird. Sie können das Beispiel herunterladen von [hier](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/EndRecurringAppointment).

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Funktionsweise:

Die `DeleteOpenInstanceRequest` Message dient dazu, in einem Szenario verwendet zu werden, in den die Daten, die erforderlich ist, um Instanzen eines wiederkehrenden Terminserienmaster zu löschen, der den Status enthält `Open`.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

1. Prüft auf aktuelle Version der Organisation.
2. Definiert den anonymen Type, die die wiederkehrenden Serienmusterwerte, mögliche Werte für Tage und wiederkehrende Regelmuster und Endwerte definieren.
3. Erstellt einen neuen Serientermin, der zum Beispiel erforderlich ist.

### <a name="demonstrate"></a>Demonstrieren

1. Die `RecurringAppointmentMaster` Message ruft eine wiederkehrende Terminserie ab, die in der [Einrichtung](#setup) erstellt wird.
2. Die `DeleteOpenInstanceRequest` Messge endet mit der wiederkehrenden Terminserie mit dem letzten auftretenden Instanzdatum. Enddatum der Serie.

### <a name="clean-up"></a>Bereinigung

1. Zeigt eine Option an, um die Beispieldaten zu löschen, die in [Einrichtung](#setup)erstellt wurden.

    Das Löschen ist optional, falls Sie die Entitäten und Daten durchsuchen möchten, die durch das Beispiel erstellt wurden. Sie können die Datensätze manuell löschen, um das gleiche Ergebnis zu erzielen.
