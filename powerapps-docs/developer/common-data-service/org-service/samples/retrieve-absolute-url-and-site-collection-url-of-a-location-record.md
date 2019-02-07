---
title: 'Beispiel: Abruf der absoluten URL und der Websitesammlungs-URL (Common Data Service for Apps) | Microsoft Docs'
description: 'Dieses Beispiel zeigt, wie die absolute URL und die Websitesammlungs-URL eines SharePoint-Ortes abgerufen werden.'
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
# <a name="sample-retrieve-absolute-url-and-site-collection-url-of-a-location-record"></a>Beispiel: Abruf der absoluten URL und der Websitesammlungs-URL eines Ortsdatensatzes

<!-- https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/integration-dev/sample-retrieve-absolute-url-and-site-collection-url-of-a-location-record -->

Dieses Beispiel zeigt, wie die absolute URL und die Websitesammlungs-URL eines SharePoint-Server-Ortdatensatzes mit der Message [RetrieveAbsoluteAndSiteCollectionUrlRequest](https://docs.microsoft.com/en-us/dotnet/api/microsoft.crm.sdk.messages.retrieveabsoluteandsitecollectionurlrequest?view=dynamics-general-ce-9) abgerufen werden.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Funktionsweise:

Die Message `RetrieveAbsoluteAndSiteCollectionUrlRequest` ist in einem Szenario zu verwenden, das die Daten enthält, die für den Abruf der absoluten URL und der Websitesammlungs-URL für einen SharePoint-Ortsdatensatz benötigt werden.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

1. Prüft auf aktuelle Version der Organisation. 
1. Die Methode `CreateRequireRecords` erstellt Entitätsdatensätze, die von dem Beispiel verwendet werden.

### <a name="demonstrate"></a>Demonstrieren

1. `RetrieveAbsoluteAndSiteCollectionUrlRequest` wird verwendet, um die absolute URL und Websitesammlungs-URL des SharePoint-Datensatzes abzurufen.

### <a name="clean-up"></a>Bereinigung

1. Zeigt eine Option an, um die Datensätze zu löschen, die in der [Einrichtung](#setup)erstellt wurden.

    Das Löschen ist optional, falls Sie die Entitäten und Daten durchsuchen möchten, die durch das Beispiel erstellt wurden. Sie können die Datensätze manuell löschen, um das gleiche Ergebnis zu erzielen.