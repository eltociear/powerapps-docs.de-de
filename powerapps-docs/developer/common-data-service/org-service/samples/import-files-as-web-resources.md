---
title: 'Beispiel: Dateien als Webressourcen importieren (Common Data Service) | Microsoft-Dokumentation'
description: In diesem Beispiel wird gezeigt, wie Dateien als Webressourcen importiert werden
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
ms.openlocfilehash: c4f17c771242505941780b16c53ad3defd763c08
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155750"
---
# <a name="sample-import-files-as-web-resources"></a>Beispiel: Importieren von Dateien als Webressourcen 

In diesem Beispiel wird gezeigt, wie Dateien als Webressourcen importiert werden. Sie können das Beispiel von [hier](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/ImportWebResources) herunterladen.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Funktionsweise:

In diesem Beispiel wird gezeigt, wie der optionale `SolutionUniqueName`-Parameter verwendet wird, um eine Webressource einer bestimmten Lösung zuzuordnen, wenn sie erstellt wird.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

1. Prüft auf aktuelle Version der Organisation.
2. Die `CreateRequiredRecords`-Klasse erstellt einen Herausgeber und eine Lösung, die für das Beispiel erforderlich ist, wenn die Webressourcen hinzugefügt werden.


### <a name="demonstrate"></a>Demonstrieren

1. Die `XDocument`-Methode liest die beschreibenden Daten aus den XML-Dateien. 
1. Die `WebResource` wird zum Festlegen der Webressourceneigenschaften verwendet.
1. Die `CreateRequest`-Methode wird verwendet, um optionale Parameter hinzuzufügen.

### <a name="clean-up"></a>Bereinigung

Zeigt eine Option an, um Beispieldaten zu löschen, die in [Einrichtung](#setup)erstellt wurden. Das Löschen ist optional, falls Sie die Entitäten und Daten durchsuchen möchten, die durch das Beispiel erstellt wurden. Sie können die Datensätze manuell löschen, um das gleiche Ergebnis zu erzielen.

