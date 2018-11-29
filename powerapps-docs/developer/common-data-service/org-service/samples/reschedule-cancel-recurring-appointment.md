---
title: 'Beispiel: Erneutes Planen und Stornieren eines Serientermins (Common Data Service for Apps) | Microsoft Docs'
description: 'Dieses Beispiel zeigt, wie ein Serientermin geplant und storniert wird.'
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
# <a name="sample-reschedule-and-cancel-a-recurring-appointment"></a>Beispiel: Erneutes Planen und Stornieren eines Serientermins

<!-- https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/sample-reschedule-cancel-recurring-appointment -->

Dieses Beispiel zeigt, wie Termininstanzen in der Serie eines sich wiederholenden Termins mithilfe der Message [RescheduleRequest](https://docs.microsoft.com/en-us/dotnet/api/microsoft.crm.sdk.messages.reschedulerequest?view=dynamics-general-ce-9) neu geplant und storniert werden. Sie können das Beispiel [hier](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/RecurringAppointment) herunterladen.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Funktionsweise:

Die `RescheduleRequest`-Message ist für die Verwendung in einem Szenario vorgesehen, in dem sie die Daten enthält, die erforderlich sind, um einen Termin, eine Terminserie oder einen Wartungstermin (Serviceaktivität) neu zu planen.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

1. Prüft auf aktuelle Version der Organisation. 
2. Definiert einen anonymen Typ zum Definieren der möglichen Serienmusterwerte und möglichen Werte für die Wochentage.
3. Definiert einen anonymen Typ, um die möglichen Werte für wiederkehrende Regelmuster und Endwerte zu definieren.
4. Die Methode `RecurringAppointmentMaster` erstellt einen neuen Serientermin.

### <a name="demonstrate"></a>Demonstrieren

1. Die Message `QueryExpression` fragt die einzelne Termininstanz ab, die auf das heutige Datum oder 10 Tage danach fällt. Im Allgemeinen ist dies die zweite Instanz in der Serienterminserie.
3. Die Message `RescheduleRequest` aktualisiert wird das Zeitplanstart- und enddatum eines Termins.
4. Die Message `SetStateRequest` bricht die letzte Instanz des Termins ab. Der Status dieser Termininstanz wird auf `canceled` eingestellt. Sie können diese Termininstanz in der Ansicht `All Activities` anzeigen.

### <a name="clean-up"></a>Bereinigung

1. Zeigt eine Option an, um die Beispieldaten zu löschen, die in [Einrichtung](#setup)erstellt wurden.
    Das Löschen ist optional, falls Sie die Entitäten und Daten durchsuchen möchten, die durch das Beispiel erstellt wurden. Sie können die Datensätze manuell löschen, um das gleiche Ergebnis zu erzielen.
