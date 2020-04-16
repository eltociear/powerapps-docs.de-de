---
title: " Erstellen, Abrufen, Aktualisieren und Löschen von Dashboards (Common Data Service) | Microsoft-Dokumentation"
description: Dieses Beispiel zeigt, wie im Besitz eines Benutzers befindliche Dashboards erstellt, abgerufen, aktualisiert und gelöscht werden.
ms.custom: ''
ms.date: 12/20/2019
ms.reviewer: pehecke
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
ms.openlocfilehash: 591934479a2b1bc810907973767e9a3083e7f107
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155862"
---
# <a name="create-retrieve-update-and-delete-a-chart"></a>Erstellen, Abrufen, Aktualisieren und Löschen eines Diagramms

Dieses Beispiel zeigt, wie Sie anhand der folgenden Methoden eine im Besitz eines Benutzers befindliches Dashboard erstellen, abrufen, aktualisieren und löschen:

- [IOrganizationService.Create](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.iorganizationservice.create?view=dynamics-general-ce-9)
- [IOrganizationService.Retrieve](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.iorganizationservice.retrieve?view=dynamics-general-ce-9)
- [IOrganizationService.Update](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.iorganizationservice.update?view=dynamics-general-ce-9)
- [IOrganizationService.Delete](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.iorganizationservice.delete?view=dynamics-general-ce-9)

Sie können das Beispiel von [hier](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/CRUDOperationsDashboard) herunterladen.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Funktionsweise:

Die `IOrganizationService`-Methoden soll in einem Szenario verwendet werden, das Daten enthält, die programmgesteuerten Zugriff auf die Metadaten und Daten einer Organisation bereitstellen.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

Prüft auf aktuelle Version der Organisation.

### <a name="demonstrate"></a>Demonstrieren

1. Die `mySavedQuery`-Methode erfasst die standardmäßige öffentliche Ansicht für Verkaufschancen. 
2. Die `visualizationQuery`-Methode ruft die Visualisierungen aus dem System ab. In diesem Beispiel wird davon ausgegangen, dass Sie die **Besten Möglichkeiten** haben. 
3. Die `dashboard`-Methode legt das Dashboard fest und gibt die FormXml an.
4. Die `chartPicker`-Methode aktiviert die Diagrammauswahl im Diagramm.

### <a name="clean-up"></a>Bereinigung

Zeigt eine Option an, um die Datensätze zu löschen, die in der [Einrichtung](#setup)erstellt wurden. Das Löschen ist optional, falls Sie die Entitäten und Daten durchsuchen möchten, die durch das Beispiel erstellt wurden. Sie können die Datensätze manuell löschen, um das gleiche Ergebnis zu erzielen.