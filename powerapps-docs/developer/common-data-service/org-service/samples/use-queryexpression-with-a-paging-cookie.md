---
title: 'Beispiel: Verwendung von QueryExpresion mit einem Auslagerungscookie (Common Data Service) | Microsoft-Dokumentation'
description: Dieses Beispiel zeigt, wie das Auslagerungscookie in einer QueryExpresion verwendet wird
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
ms.openlocfilehash: 4e130a5c03567771f38a201ada5ef4e7457bb724
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155522"
---
# <a name="sample-use-queryexpression-with-a-paging-cookie"></a>Beispiel: Verwenden von QueryExpression mit einem Auslagerungscookie

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/org-service/sample-use-queryexpression-with-a-paging-cookie -->

Dieses Beispiel zeigt, wie Sie einen Auslagerungscookie in einer QueryExpression-Abfrage verwenden, um aufeinander folgende Seiten von Abfrageergebnissen abzurufen. Es verwendet die [IOrganizationService.RetrieveMultiple](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.iorganizationservice.retrievemultiple?view=dynamics-general-ce-9)-Methode. Sie können das Beispiel [hier](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/UseQueryExpressionwithPaging) herunterladen.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Funktionsweise:

Die `IOrganizationService.RetreiveMultiple`-Methode ist dazu vorgesehen, in einem Szenario verwendet zu werden, in dem sie eine Sammlung von Datensätzen abruft.
## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

1. Prüft auf aktuelle Version der Organisation.
1. Die `Account`-Methode erstellt einen übergeordneten Firmendatensatz und 10 untergeordnete Firmendatensätze.

### <a name="demonstrate"></a>Demonstrieren

1. `ConditionExpress` definiert den Bedingungsausdruck für das Abrufen von Datensätzen.
1. Die `OrderExpression`-Methode definiert den Auftragsausdruck zum Abrufen von Datensätzen.

### <a name="clean-up"></a>Bereinigung

Zeigt eine Option zum Löschen aller im Beispiel erstellten Daten an. Das Löschen ist optional, falls Sie die Daten überprüfen möchten, die durch das Beispiel erstellt wurden. Sie können die Daten manuell löschen, um das gleiche Ergebnis zu erzielen.
