---
title: " Speichern eines globalen Optionssatzes in einer Datei (Common Data Service) | Microsoft Docs"
description: Dieses Beispiel zeigt, wie ein globaler Optionssatz in einer Datei gespeichert wird.
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
ms.openlocfilehash: 17940374791955a43cc27a030bc14c9d9abc2e73
ms.sourcegitcommit: 3bf59896a98e5f01289a2489e185f27518aeaec3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/15/2020
ms.locfileid: "2956324"
---
# <a name="dump-global-option-information-to-a-file"></a>Speichern eines globalen Optionssatzes in einer Datei

Dieses Beispiel zeigt, wie alle globalen Optionssätze-Metadaten in einer `XML` Datei ausgeschrieben werden. Es wird die [RetrieveAllOptionSetsRequest](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.messages.retrievealloptionsetsrequest?view=dynamics-general-ce-9)-Nachricht verwendet. Sie können das Beispiel von [hier](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/DumpGlobalOptionSetInfo) herunterladen.

Das folgende Bespiel erstellt eine neue Datei unter `\DumpGlobalOptionSetInfo\bin\Debug\AllOptionSetValues.xml`. Diese Datei können Sie in **Office Excel** öffnen, um einen tabellarischen Bericht anzuzeigen. 

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Funktionsweise:

Die `RetrieveAllOptionSetsRequest` Nachricht ist für die Verwendung in einem Szenario vorgesehen, in dem sie Daten enthält, die zum Abrufen aller Metadateninformationen über globale Metadatenoptionssätze erforderlich sind.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

Prüft auf aktuelle Version der Organisation.

### <a name="demonstrate"></a>Demonstrieren

1. Ruft die `RetrieveAllOptionSetsRequest` Methode zum Abrufen der Metadaten ab. 
1. Der `StreamWriter` erstellt einer Instanz von StreamWriter, um Text in eine Datei zu schreiben.

### <a name="clean-up"></a>Bereinigung

Dieses Beispiel erstellt keine Datensätze. Keine Bereinigung erforderlich