---
title: " Entitätsberechtigungen in einer Datei sichern (Common Data Service) | Microsoft-Dokumentation"
description: In diesem Beispiel wird gezeigt, wie Entitätsberechtigungen in einer Datei gesichert werden.
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
ms.openlocfilehash: 645977524a8d90bf4c241aba672a311da044419b
ms.sourcegitcommit: 5ec7c7f04fe41896dec966706a3b3d295648726f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/06/2020
ms.locfileid: "2934326"
---
# <a name="dump-entity-privileges-information-to-a-file"></a>Entitätsberechtigungsinformationen in einer Datei sichern

Dieses Beispiel zeigt, wie alle Attributmetadaten in eine `XML`-Datei ausgeschrieben werden. Es wird die [RetrieveAllEntitiesRequest](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.messages.retrieveallentitiesrequest?view=dynamics-general-ce-9)-Nachricht verwendet. Sie können das Beispiel von [hier](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/DumpEntityPriviliges) herunterladen.

Das folgende Bespiel erstellt eine neue Datei unter `\DumpEntityPriviliges\bin\Debug\EntityPrivileges.xml`. Diese Datei können Sie in **Office Excel** öffnen, um einen tabellarischen Bericht anzuzeigen. 

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Funktionsweise:

Die `RetrieveAllEntitiesRequest`-Nachricht ist für die Verwendung in einem Szenario vorgesehen, das Daten enthält, die zum Abrufen von Metadateninformationen über alle Entitäten erforderlich sind.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

Prüft auf aktuelle Version der Organisation.

### <a name="demonstrate"></a>Demonstrieren

1. Ruft die `RetrieveAllEntitiesRequest` Methode zum Abrufen der Metadaten ab. 
1. Der `StreamWriter` erstellt einer Instanz von StreamWriter, um Text in eine Datei zu schreiben.

### <a name="clean-up"></a>Bereinigung

Dieses Beispiel erstellt keine Datensätze. Keine Bereinigung erforderlich