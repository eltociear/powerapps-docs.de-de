---
title: 'Beispiel: Abrufen gültiger Statusübergänge (Common Data Service) | Microsoft-Dokumentation'
description: In diesem Beispiel wird gezeigt, wie gültige Statusübergänge abgerufen werden.
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
ms.openlocfilehash: e6eb7b939430b2f21f961bfd85b0d3b6179eb3d7
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155602"
---
# <a name="sample-retrieve-valid-status-transitions"></a>Beispiel: Abrufen gültiger Statusübergänge

Dieses Beispiel zeigt, wie gültige Statusübergänge unabhängig davon abrufen werden können, ob benutzerdefinierte Statusübergänge für die Entität definiert wurden. Sie können das Beispiel [hier](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/RetrieveValidTransitions) herunterladen.
 
## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]


## <a name="what-this-sample-does"></a>Funktionsweise:

Die Methode `GetValidStatusOptions` ist zur Verwendung in einem Szenario bestimmt, in dem sie Daten enthält, die gültige Statusoptionsübergänge zurückgeben, unabhängig davon, ob Statusübergänge für die Entität aktiviert sind.
## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

1. Prüft auf aktuelle Version der Organisation.
1. Die Methode `MetadataFilterExpression` prüft auf die Entitäten-Metadaten.

### <a name="demonstrate"></a>Demonstrieren

1. Die Methode `MetadataFilterExpression` ruft die Statusoptionen für die Entität `Incident` ab.
1. Die Methode `RetrieveMetadataChangeRequest` ruft die Metadaten ab.
1. Die Methdoe `GetValidStatusOptions` fordert die gültigen Statusübergänge für jede Statusoption an.

### <a name="clean-up"></a>Bereinigung

Dieses Beispiel erstellt keine Datensätze. Keine Bereinigung erforderlich.
