---
title: 'Beispiel: Konvertieren eines Termins in eine Terminserie (Common Data Service) | Microsoft-Dokumentation'
description: Dieses Beispiel zeigt, wie Sie einen Termin in eine wiederkehrende Terminserie umwandeln können.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 4125ffa1bf8d5c21646265fc2020484916af291f
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748384"
---
# <a name="sample-convert-an-appointment-to-a-recurring-appointment"></a>Beispiel: Konvertieren eines Termins in eine Terminserie

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-convert-appointment-recurring-appointment -->

Dieses Beispiel zeigt, wie Sie einen Termin in eine wiederkehrende Terminserie umwandeln können, indem Sie die Meldung [AddRecurrenceRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.addrecurrencerequest?view=dynamics-general-ce-9) verwenden. Sie können das Beispiel [hier](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/ConvertToRecurring) herunterladen.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Funktionsweise:

Die `AddRecurrenceRequest`-Nachricht ist für die Verwendung in einem Szenario vorgesehen, in dem sie die Daten enthält, die erforderlich sind, um Serieninformationen zu einem bestehenden Termin hinzuzufügen.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

1. Prüft auf aktuelle Version der Organisation.
1. Erstellt einen Beispieltermin, der später in einen Serientermin konvertiert wird.

### <a name="demonstrate"></a>Demonstrieren

1. Gibt die Serieninformationen an, die dem im [Setup](#setup) erstellten Termin hinzugefügt werden müssen.
2. Definiert die anonymen Typen, die die möglichen wiederkehrenden Serienmusterwerte und mögliche Werte für Tage definieren.
3. Definiert die anonymen Typen, die die möglichen wiederkehrenden Serienmuster und Typen definieren.
4. Das `RecurringAppointmentMaster` gibt die Serieninformationen an. 
5. Die `AddRecurrence` Meldung wandelt den erstellten Termin in einen wiederkehrenden Termin um.

### <a name="clean-up"></a>Bereinigung

1. Zeigt eine Option an, um die Beispieldaten zu löschen, die in [Einrichtung](#setup)erstellt wurden. 

    Das Löschen ist optional, falls Sie die Entitäten und Daten durchsuchen möchten, die durch das Beispiel erstellt wurden. Sie können die Beispieldaten manuell löschen, um das gleiche Ergebnis zu erzielen.
