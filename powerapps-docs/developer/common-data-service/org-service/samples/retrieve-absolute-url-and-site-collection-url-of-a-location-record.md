---
title: 'Beispiel: Abruf der absoluten URL und der Websitesammlungs-URL (Common Data Service) | Microsoft-Dokumentation'
description: Dieses Beispiel zeigt, wie die absolute URL und die Websitesammlungs-URL eines SharePoint-Ortes abgerufen werden.
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
ms.openlocfilehash: 73d4c419a41d0f152b5a8c08fc646c8774a4403e
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155654"
---
# <a name="sample-retrieve-absolute-url-and-site-collection-url-of-a-location-record"></a>Beispiel: Abruf der absoluten URL und der Websitesammlungs-URL eines Ortsdatensatzes

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/integration-dev/sample-retrieve-absolute-url-and-site-collection-url-of-a-location-record -->

Dieses Beispiel zeigt, wie die absolute URL und die Websitesammlungs-URL eines SharePoint-Server-Ortdatensatzes mit der Nachricht [RetrieveAbsoluteAndSiteCollectionUrlRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.retrieveabsoluteandsitecollectionurlrequest?view=dynamics-general-ce-9) abgerufen werden.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Funktionsweise:

Die Nachricht `RetrieveAbsoluteAndSiteCollectionUrlRequest` ist in einem Szenario zu verwenden, das die Daten enthält, die für den Abruf der absoluten URL und der Websitesammlungs-URL für einen SharePoint-Ortsdatensatz benötigt werden.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

1. Prüft auf aktuelle Version der Organisation. 
1. Die Methode `CreateRequireRecords` erstellt Entitätsdatensätze, die von dem Beispiel verwendet werden.

### <a name="demonstrate"></a>Demonstrieren

`RetrieveAbsoluteAndSiteCollectionUrlRequest` wird verwendet, um die absolute URL und Websitesammlungs-URL des SharePoint-Datensatzes abzurufen.

### <a name="clean-up"></a>Bereinigung

Zeigt eine Option an, um die Datensätze zu löschen, die in der [Einrichtung](#setup)erstellt wurden. Das Löschen ist optional, falls Sie die Entitäten und Daten durchsuchen möchten, die durch das Beispiel erstellt wurden. Sie können die Datensätze manuell löschen, um das gleiche Ergebnis zu erzielen.
