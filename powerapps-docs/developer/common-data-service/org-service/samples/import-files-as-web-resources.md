---
title: 'Beispiel: Dateien als Webressourcen importieren (Common Data Service) | Microsoft-Dokumentation'
description: In diesem Beispiel wird gezeigt, wie Dateien als Webressourcen importiert werden
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
ms.openlocfilehash: d73d2d7fa70998ceedc2cf9f833201a92c32c7e4
ms.sourcegitcommit: 5ec7c7f04fe41896dec966706a3b3d295648726f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/06/2020
ms.locfileid: "2934559"
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

