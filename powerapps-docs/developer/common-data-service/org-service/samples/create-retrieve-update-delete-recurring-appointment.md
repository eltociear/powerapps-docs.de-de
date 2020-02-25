---
title: 'Beispiel: Buchen einer CRUD-Terminserie (Common Data Service) | Microsoft-Dokumentation'
description: In diesem Beispiel wird gezeigt, wie CRUD-Vorgänge auf wiederkehrende Termine ausführt werden
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
ms.openlocfilehash: 08789d9be9b093428733ab13424a75e307504bdd
ms.sourcegitcommit: 303d5aed44f2bbb406cabeb6b9c8474d738d9114
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "3005057"
---
# <a name="sample-create-retrieve-update-and-delete-a-recurring-appointment"></a>Beispiel: Einen wiederkehrenden Termin erstellen, abbrufen, aktualisieren und löschen

Dieses Beispiel zeigt, wie ein Serie wiederkehrender Termine erstellt, abgerufen, aktualisiert und gelöscht werden kann. Das Beispiel verwendet die folgenden allgemeinen Methoden:

- [IOrganizationService.Create](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.iorganizationservice.create?view=dynamics-general-ce-9)
- [IOrganizationService.Retrieve](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.iorganizationservice.retrieve?view=dynamics-general-ce-9)
- [IOrganizationService.Update](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.iorganizationservice.update?view=dynamics-general-ce-9)
- [IOrganizationService.Delete](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.iorganizationservice.delete?view=dynamics-general-ce-9)

Sie können das Beispiel von [hier](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/CRUDRecurringAppointment) herunterladen.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Funktionsweise:

Die `IOrganizationService`-Methoden soll in einem Szenario verwendet werden, das Daten enthält, die programmgesteuerten Zugriff auf die Metadaten und Daten einer Organisation bereitstellen.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

Prüft auf aktuelle Version der Organisation.

### <a name="demonstrate"></a>Demonstrieren

1. Definierne Sie anonyme Typen , um die möglichen Werte für Wiederholungsmuster, mögliche Werte für Wochentage und mögliche Werte für den Serienregel-Muster-Endtyp zu definieren. 
1. Die `RecurringAppointmentMaster`-Methode erstellt einen Serientermin.
1. Die `QueryExpression`-Methode ruft den neu erstellten Serientermin ab.
1. Die `Update` Methode aktualisiert das Thema, die Anzahl der Vorkommnisse auf 5, das Terminintervall auf 2 für den abgerufenen wiederkehrenden Termin.


### <a name="clean-up"></a>Bereinigung

Zeigt eine Option an, um die Datensätze zu löschen, die in der [Einrichtung](#setup)erstellt wurden. Das Löschen ist optional, falls Sie die Entitäten und Daten durchsuchen möchten, die durch das Beispiel erstellt wurden. Sie können die Datensätze manuell löschen, um das gleiche Ergebnis zu erzielen.


