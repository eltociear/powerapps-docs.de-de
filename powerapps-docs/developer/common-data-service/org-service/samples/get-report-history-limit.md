---
title: 'Beispiel: Berichtsverlaufsgrenzenwerte (Common Data Service) abrufen | Microsoft Docs'
description: In diesem Beispiel wird gezeigt, wie Sie Berichtsverlaufsgrenzen abrufen.
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
ms.openlocfilehash: 80dc150533914c64983aa6ec4450fde23dbb6b0a
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155758"
---
# <a name="get-report-history-limits"></a>Abrufen des Berichtsverlaufsgrenzen für den Bericht

Dieses Beispiel zeigt, wie man mit Hilfe der Meldung [GetReportHistoryLimitRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.getreporthistorylimitrequest?view=dynamics-general-ce-9) die Grenzen der Berichtshistorie erhält. Sie können das Beispiel von [hier](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/GetReportHistoryLimit) herunterladen.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Funktionsweise:

Die `GetReportHistoryLimitRequest`-Nachricht soll in einem Szenario verwendet werden, in dem sie Daten enthält, die zum Abrufen der Historiengrenze für einen Bericht benötigt werden.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

Prüft auf aktuelle Version der Organisation.

### <a name="demonstrate"></a>Demonstrieren

1. Die `QueryByAttribute`-Methode fragt nach einem bestehenden Bericht ab.
2. Die `GetReportHistoryLimitRequest`-Methode erhält die Daten zur Historiengrenze.

### <a name="clean-up"></a>Bereinigung

Für diese Beispiel ist keine Bereinigung erforderlich.
