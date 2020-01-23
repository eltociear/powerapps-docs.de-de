---
title: 'Beispiel: Abfragen der Arbeitszeit eines Benutzers (Common Data Service) | Microsoft-Dokumentation'
description: Dieses Beispiel zeigt, wie Sie die Arbeitszeit eines Benutzers abrufen.
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
ms.openlocfilehash: 5d2426d63e7c8444c22ea0103979ed8a2812724e
ms.sourcegitcommit: 5ec7c7f04fe41896dec966706a3b3d295648726f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/06/2020
ms.locfileid: "2934246"
---
# <a name="sample-query-the-working-hours-of-a-user"></a>Beispiel: Abfragen der Arbeitszeit eines Benutzers

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-query-working-hours-user -->

Dieses Beispiel zeigt, wie Sie die Arbeitszeit eines Benutzers mithilfe der Message [QueryScheduleRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.queryschedulerequest?view=dynamics-general-ce-9) abrufen. Sie können das Beispiel [hier](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/QueryWorkingHours
) herunterladen.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Funktionsweise:

Die Message `QueryScheduleRequest` soll in einem Szenario verwendet werden, in dem sie die Daten enthält, die erforderlich sind, um die angegegebene Ressource für einen verfügbaren Zeitblock zu durchsuchen, der den angegebenen Parametern entspricht.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

Prüft auf aktuelle Version der Organisation.

### <a name="demonstrate"></a>Demonstrieren

1. Die Message `WhoAMIRequest` fordert die aktuellen Benutzerinformationen an.
2. Die Message `QueryScheduleRequest` Nachricht ruft die Arbeitszeit des aktuellen Benutzers ab.

### <a name="clean-up"></a>Bereinigung

Zeigt eine Option an, um die Beispieldaten zu löschen, die in [Einrichtung](#setup)erstellt wurden. Das Löschen ist optional, falls Sie die Entitäten und Daten durchsuchen möchten, die durch das Beispiel erstellt wurden. Sie können die Datensätze manuell löschen, um das gleiche Ergebnis zu erzielen.
