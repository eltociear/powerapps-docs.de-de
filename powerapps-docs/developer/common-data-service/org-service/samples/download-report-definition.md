---
title: " Berichtsdefinition herunterladen (Common Data Service) | Microsoft Docs"
description: In diesem Beispiel wird gezeigt, wie die Berichtsdefinition heruntergeladen wird
ms.custom: ''
ms.date: 12/20/2019
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
ms.openlocfilehash: 6498fd0db4a65c5664cff8c4ffc03f1ff477fc78
ms.sourcegitcommit: cb533c30252240dc298594e74e3189d7290a4bd7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/04/2020
ms.locfileid: "3020094"
---
# <a name="download-report-definition"></a>Berichtsdefinition herunterladen

Dieses Beispiel zeigt, wie eine Berichtsdefinitionsdatei (.rdl) mit Hilfe der Nachricht [DownloadReportDefinitionRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.downloadreportdefinitionrequest?view=dynamics-general-ce-9) heruntergeladen werden kann. Sie können das Beispiel von [hier](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/DownloadReportDefinition) herunterladen.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Funktionsweise:

Die `DownloadReportDefinitionRequest`-Nachricht soll in einem Szenario verwendet werden, in dem sie die Daten enthält, die zum Herunterladen einer Berichtsdefinition benötigt werden.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

Prüft auf aktuelle Version der Organisation.

### <a name="demonstrate"></a>Demonstrieren

1. Die `QueryByAttribute`-Methode fragt nach einem bestehenden Bericht ab.
2. Mit der `DownloadReportDefinitionRequest`-Methode wird die Berichtsdefinition heruntergeladen.

### <a name="clean-up"></a>Bereinigung

Zeigt eine Option an, um Beispieldaten zu löschen, die in [Einrichtung](#setup)erstellt wurden. Das Löschen ist optional, falls Sie die Entitäten und Daten durchsuchen möchten, die durch das Beispiel erstellt wurden. Sie können die Datensätze manuell löschen, um das gleiche Ergebnis zu erzielen.