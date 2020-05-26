---
title: 'Beispiel: Exportieren von Menübanddefinitionen (modellgestützte Apps) | Microsoft Docs'
description: Dieses Beispiel veranschaulicht das Exportieren von Menübanddefinitionen. Es wird die RetrieveApplicationRibbonRequest und RetrieveEntityRibbonRequest Nachrichten verwendet.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: KumarVivek
ms.author: kvivek
manager: shilpas
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: a08a64d2e74298093e7c3b260b00f82d0b5aa51a
ms.sourcegitcommit: 6c73e316f866af6a34619f95a5ac64ad1664b48a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/01/2020
ms.locfileid: "3326424"
---
# <a name="sample-export-ribbon-definitions"></a>Beispiel: Exportieren von Menübanddefinitionen

Dieses Beispiel zeigt, wie man Multifunktionsleistendefinitionen exportiert. Es verwendet die Meldungen [RetrieveApplicationRibbonRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.retrieveapplicationribbonrequest?view=dynamics-general-ce-9) und [RetrieveEntityRibbonRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.retrieveentityribbonrequest?view=dynamics-general-ce-9). Sie können das Beispiel von [hier](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/ExportRibbonDefinitions) herunterladen.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../common-data-service/includes/cc-how-to-run-samples.md)]

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

  
### <a name="see-also"></a>Siehe auch  
 [Befehle und das Menüband anpassen](customize-commands-ribbon.md)   
 [Parameter mit dem Menüband an eine URL übergeben](pass-parameters-url-by-using-ribbon.md)   
 [Menübandkernschema](ribbon-core-schema.md) [Menübandtypenschema](ribbon-types-schema.md) [Menüband-WSS-Schema](ribbon-wss-schema.md) <xref:Microsoft.Crm.Sdk.Messages.RetrieveApplicationRibbonRequest>   
 <xref:Microsoft.Crm.Sdk.Messages.RetrieveEntityRibbonRequest>
