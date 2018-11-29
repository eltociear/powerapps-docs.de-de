---
title: 'Beispiel: Speichern von Entitätsmetadaten in einer Datei (Common Data Service für Apps) | Microsoft Docs'
description: 'BeispieldatenDieses Beispiel zeigt, wie alle Entitätsmetadaten in einer XML-Datei ausgeschrieben werden.'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: samples
author: brandonsimons
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="sample-dump-entity-metadata-to-a-file"></a>Beispiel: Speichern von Entitätsmetadaten in einer Datei

Dieses Beispiel zeigt, wie alle Entitätsmetadaten in eine `XML` ausgeschrieben werden. Es wird die [RetrieveAllEntitiesRequest](https://docs.microsoft.com/en-us/dotnet/api/microsoft.xrm.sdk.messages.retrieveallentitiesrequest?view=dynamics-general-ce-9)-Nachricht verwendet.

Das folgende Bespiel erstellt eine neue Datei unter `\Entities\bin\Debug\EntityInfo.xml`. Diese Datei können Sie in Office Excel öffnen, um einen tabellarischen Bericht anzuzeigen. Möglicherweise benötigen Sie diese Informationen, um den Entitätstypcode für eine benutzerdefinierte Entität zur Verwendung in Berichten zu ermitteln. Sie können das Beispiel von [hier](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/DumpEntityMetadata) herunterladen.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Funktionsweise:

Die `RetrieveAllEntitiesRequest`-Message ist für die Verwendung in einem Szenario vorgesehen, in dem sie Daten enthält, die zum Abrufen der Metadateninformationen aller Entitäten erforderlich sind.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

1. Prüft auf aktuelle Version der Organisation.


### <a name="demonstrate"></a>Demonstrieren

1. Ruft die `RetrieveAllEntitiesRequest` Methode zum Abrufen der Metadaten ab. 
1. Der `StreamWriter` erstellt einer Instanz von StreamWriter, um Text in eine Datei zu schreiben.

### <a name="clean-up"></a>Bereinigung

1. Dieses Beispiel erstellt keine Datensätze. Keine Bereinigung erforderlich


