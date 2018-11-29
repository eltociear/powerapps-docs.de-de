---
title: 'Beispiel: Abruf von Vielfachen mit der QueryExpression (Common Data Service for Apps) | Microsoft Docs'
description: 'In diesem Beispiel wird gezeigt, wie Sie mehrere Entitäten mit QueryExpression abrufen.'
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
# <a name="sample-retrieve-multiple-with-the-queryexpression-class"></a>Beispiel: Rufen Sie mit der QueryExpressions-Klasse Vielfaches ab

<!-- Re-title? This is really about retrieving  related records 
https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/org-service/sample-retrieve-multiple-queryexpression-class
-->
Dieses Beispiel zeigt, wie Sie mehrere Entitäten mit der Methode [IOrganizationService.RetrieveMultiple(QueryBase)](https://docs.microsoft.com/en-us/dotnet/api/microsoft.xrm.sdk.iorganizationservice.retrievemultiple?view=dynamics-general-ce-9#Microsoft_Xrm_Sdk_IOrganizationService_RetrieveMultiple_Microsoft_Xrm_Sdk_Query_QueryBase_) mit [QueryExpression](https://docs.microsoft.com/en-us/dotnet/api/microsoft.xrm.sdk.query.queryexpression?view=dynamics-general-ce-9) und den verknüpften Entitätsspalten abrufen. Sie können das Beispiel [hier](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/RetrieveMultipleByQueryExpression) herunterladen.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]


## <a name="what-this-sample-does"></a>Funktionsweise:

Die Klasse `QueryExpression` ist für die Verwendung in einem Szenario vorgesehen, in der es eine komplexe Abfrage enthält, die in einer Hierarchie von Ausdrücken formuliert ist.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

1. Prüft auf aktuelle Version der Organisation.

### <a name="demonstrate"></a>Demonstrieren
1. Erstellt mehrere Accounts mit primären Kontakten.
1. Diese `QueryExpression`-Klasse erstellt einen Abfrageausdruck, der den Linkentitätsalias und Spalten der Linkentität angibt, die zurückgegeben werden sollen.
### <a name="clean-up"></a>Bereinigung

1. Keine Bereinigung erforderlich.
