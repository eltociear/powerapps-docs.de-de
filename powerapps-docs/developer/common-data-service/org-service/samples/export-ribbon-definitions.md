---
title: 'Beispiel: Exportieren von Menübanddefinitionen (Common Data Service) | Microsoft Docs'
description: Dieses Beispiel veranschaulicht das Exportieren von Menübanddefinitionen
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: pehecke
ms.service: powerapps
ms.topic: samples
author: mayadumesh
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 009b9a644ac4ae010d4e5e74facc4cdef99a6cc7
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155766"
---
# <a name="export-ribbon-definitions"></a>Exportieren von Menübanddefinitionen

Dieses Beispiel zeigt, wie man Multifunktionsleistendefinitionen exportiert. Es verwendet die Meldungen [RetrieveApplicationRibbonRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.retrieveapplicationribbonrequest?view=dynamics-general-ce-9) und [RetrieveEntityRibbonRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.retrieveentityribbonrequest?view=dynamics-general-ce-9). Sie können das Beispiel von [hier](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/ExportRibbonDefinitions) herunterladen.


## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Funktionsweise:

Die `RetrieveApplicationRibbonRequest`-Nachricht soll in einem Szenario verwendet werden, in dem sie Daten enthält, die zum Abrufen der Daten benötigt werden, die den Inhalt und das Verhalten des Anwendungs-Band definieren. Die `RetrieveEntityRibbonRequest`-Nachricht ist für ein Szenario gedacht, in dem sie Daten enthält, die zum Abrufen von Banddefinitionen für eine Entität benötigt werden.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

Prüft auf aktuelle Version der Organisation.

### <a name="demonstrate"></a>Demonstrieren

1. Die `RetrieveApplicationRibbonRequest`-Methode ruft das Anwendungs-Band ab.
2. Die `RetrieveEntityRibbonRequest`-Methode ruft die System-Entitäts-Menübänder ab

### <a name="clean-up"></a>Bereinigung

Für dieses Beispiel ist keine Bereinigung erforderlich
