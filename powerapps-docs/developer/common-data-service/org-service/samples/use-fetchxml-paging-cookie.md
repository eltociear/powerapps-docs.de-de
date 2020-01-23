---
title: 'Beispiel: Verwendung von FetchXML mit einem Auslagerungscookie (Common Data Service) | Microsoft-Dokumentation'
description: Dieses Beispiel zeigt, wie das Auslagerungscookie in FetchXML verwendet wird
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
ms.openlocfilehash: 7325fc94f4a73616dbd679ba0800879dc7c6ea2f
ms.sourcegitcommit: 5ec7c7f04fe41896dec966706a3b3d295648726f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/06/2020
ms.locfileid: "2934078"
---
# <a name="sample-use-fetchxml-with-a-paging-cookie"></a>Beispiel: Verwenden von FetchXML mit einem Auslagerungscookie

<!-- This could be greatly simplified IMHO 
https://docs.microsoft.com/dynamics365/customer-engagement/developer/org-service/sample-use-fetchxml-paging-cookie
-->
Dieses Beispiel zeigt, wie Sie einen Auslagerungscookie in einer FetchXML-Abfrage verwenden, um aufeinander folgende Seiten von Abfrageergebnissen abzurufen. Es verwendet die [IOrganizationService. RetrieveMultiple](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.iorganizationservice.retrievemultiple?view=dynamics-general-ce-9)-Methode. Sie können das Beispiel [hier](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/UseFetchXMLWithPaging) herunterladen.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Funktionsweise:

Die `IOrganizationService.Retrieve`-Methode ist dazu vorgesehen, in einem Szenario verwendet zu werden, in dem sie Daten enthält, die alle Datensätze abrufen.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

1. Prüft auf aktuelle Version der Organisation.
1. Die `Account`-Methode erstellt einen übergeordneten Firmendatensatz und auch 10 untergeordnete Firmendatensätze.

### <a name="demonstrate"></a>Demonstrieren

`fetchXml` erstellt die FetchXML-Zeichenfolge für das Abrufen aller untergeordneten Firmen in eine übergeordnete Firma. Diese Fetch-Abfrage verwendet 1 Platzhalter, um die ID der übergeordneten Firma für das Herausfiltern erforderlicher Firmen anzugeben.

### <a name="clean-up"></a>Bereinigung

Zeigt eine Option zum Löschen aller im Beispiel erstellten Daten an. Das Löschen ist optional, falls Sie die Daten überprüfen möchten, die durch das Beispiel erstellt wurden. Sie können die Daten manuell löschen, um das gleiche Ergebnis zu erzielen.

