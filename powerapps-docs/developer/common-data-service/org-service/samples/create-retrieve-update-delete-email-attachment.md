---
title: 'Beispiel: CRUD-E-Mail-Anlagen <Topic Title> (Common Data Service) | Microsoft-Dokumentation'
description: In diesem Beispiel wird gezeigt, wie CRUD-Vorgänge auf E-Mail- Anhänge ausführt werden
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
ms.openlocfilehash: 0b5c0105ac67603826ffa1b6402d10cda2cc845f
ms.sourcegitcommit: 5ec7c7f04fe41896dec966706a3b3d295648726f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/06/2020
ms.locfileid: "2934352"
---
# <a name="sample-create-retrieve-update-and-delete-an-email-attachment"></a>Beispiel: Erstellen, abrufen, aktualisieren und löschen einer E-Mail-Anlage

Dieses Beispiel zeigt, wie Sie anhand dieser Methoden eine E-Mail-Anlage erstellen, abrufen, aktualisieren und löschen:

- [IOrganizationService.Create](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.iorganizationservice.create?view=dynamics-general-ce-9)
- [IOrganizationService.Retrieve](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.iorganizationservice.retrieve?view=dynamics-general-ce-9)
- [IOrganizationService.Update](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.iorganizationservice.update?view=dynamics-general-ce-9)
- [IOrganizationService.Delete](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.iorganizationservice.delete?view=dynamics-general-ce-9)

Sie können das Beispiel von [hier](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/CRUDEmailAttachements) herunterladen.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Funktionsweise:

Die `IOrganizationService`-Nachricht soll in einem Szenario verwendet werden, das programmgesteuerten Zugriff auf die Metadaten und Daten einer Organisation bereitstellt.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

1. Prüft auf aktuelle Version der Organisation.
1. Die `Email`-Methode erzeugt die für das Beispiel erforderliche E-Mail-Aktivität.

### <a name="demonstrate"></a>Demonstrieren

1. Die `ActivityMimeAttachment`-Methode erstellt drei E-Mail-Anlagen. 
1. Die `Retrieve`-Methode ruft eine Anlage einschließlich deren ID, Betreff, Dateinamen und Text aus.
1. Die `Update`-Methode aktualisiert den Dateinamen der vorhandenen Anlage.


### <a name="clean-up"></a>Bereinigung

Zeigt eine Option an, um die Datensätze zu löschen, die in der [Einrichtung](#setup)erstellt wurden. Das Löschen ist optional, falls Sie die Entitäten und Daten durchsuchen möchten, die durch das Beispiel erstellt wurden. Sie können die Datensätze manuell löschen, um das gleiche Ergebnis zu erzielen.


