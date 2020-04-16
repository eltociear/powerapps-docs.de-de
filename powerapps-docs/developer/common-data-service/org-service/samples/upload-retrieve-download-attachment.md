---
title: 'Beispiel: Hochladen, Abrufen und Herunterladen einer Anlage (Common Data Service) | Microsoft-Dokumentation'
description: Dieses Beispiel veranschaulicht, wie Sie eine Anlage hochladen, abrufen und herunterladen.
ms.custom: ''
ms.date: 10/31/2018
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
ms.openlocfilehash: c147acf6cef89eec26af7cd86740b47fc74cee75
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155542"
---
# <a name="sample-upload-retrieve-and-download-an-attachment"></a>Beispiel: Hochladen, Abrufen und Herunterladen einer Anlage

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-upload-retrieve-download-attachment -->

Das Beispiel veranschaulicht, wie Sie eine Anlage für eine Anmerkung mithilfe der [IOrganizationService.Create](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.iorganizationservice.create?view=dynamics-general-ce-9)- und [IOrganizationService.Retrieve](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.iorganizationservice.retrieve?view=dynamics-general-ce-9)-Methoden. Sie können das Beispiel [hier](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/URDAttachement) herunterladen.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]


## <a name="what-this-sample-does"></a>Funktionsweise:

Die `IOrganizationService`-Methoden soll in einem Szenario verwendet werden, wo sie programmgesteuerten Zugriff auf die Metadaten und Daten einer Organisation bereitstellt.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

Prüft auf aktuelle Version der Organisation.

### <a name="demonstrate"></a>Demonstrieren

1. Die `Annotation`-Methode instanziiert ein Anmerkungsobjekt.
1. Die `IOrganizationService`-Methode erstellt und lädt das Anmerkungsobjekt hoch.

### <a name="clean-up"></a>Bereinigung

Zeigt eine Option zum Löschen aller im Beispiel erstellten Daten an. Das Löschen ist optional, falls Sie die Daten überprüfen möchten, die durch das Beispiel erstellt wurden. Sie können die Daten manuell löschen, um das gleiche Ergebnis zu erzielen.
