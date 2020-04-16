---
title: " Abrufen von Diagrammen, die an eine Entität angehängt sind (Common Data Service) | Microsoft-Dokumentation"
description: 'In diesem Beispiel wird gezeigt, wie an eine Entität angehängte Diagramme abgerufen werden '
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
ms.openlocfilehash: 4567549633ddadb46add977ea26e6b45a69e2538
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155646"
---
# <a name="retrieve-all-charts-attached-to-an-entity"></a>Abrufen aller Diagramme die einer Entität angefügt wurden

Dieses Beispiel zeigt, wie alle Visualisierungen im Besitz der Organisation, die mithilfe der Methode [IOrganizationService.RetrieveMultiple](https://docs.microsoft.com//dotnet/api/microsoft.xrm.sdk.iorganizationservice.retrievemultiple?view=dynamics-general-ce-9) an eine Entität angefügt wurden, abgerufen werden können.

Sie können das Beispiel von [hier](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/RetrieveChartsAttachedToEntity) herunterladen.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]


## <a name="what-this-sample-does"></a>Funktionsweise:

Die `IOrganizationService`-Methoden soll in einem Szenario verwendet werden, das Daten enthält, die programmgesteuerten Zugriff auf die Metadaten und Daten einer Organisation bereitstellen.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

Prüft auf aktuelle Version der Organisation.

### <a name="demonstrate"></a>Demonstrieren

Mit der `newSavedQuery` Methode können Sie alle Visualisierungen im Besitz der Organisation, die an eine Entität angefügt sind, abfragen und abrufen.


### <a name="clean-up"></a>Bereinigung

Dieses Beispiel erstellt keine Datensätze. Keine Bereinigung erforderlich
