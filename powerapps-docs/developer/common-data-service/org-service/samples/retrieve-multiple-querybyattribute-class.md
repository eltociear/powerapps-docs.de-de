---
title: 'Beispiel: Abrufen von Vielfachen mit der QueryByAttribute-Klasse (Common Data Service) | Microsoft-Dokumentation'
description: In diesem Beispiel wird gezeigt, wie die QueryByAttribute-Klasse verwendet wird
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
ms.openlocfilehash: 4b545431853a3f6ca66ce5906f6d6ff69edde1db
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748719"
---
# <a name="sample-retrieve-multiple-with-the-querybyattribute-class"></a>Beispiel: Abruf von Vielfachen mit der QueryByAttribute-Klasse

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/org-service/sample-retrieve-multiple-querybyattribute-class -->

In diesem Beispiel wird gezeigt, wie [QueryByAttribute](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.query.querybyattribute?view=dynamics-general-ce-9) in der Methode [RetrieveMultiple](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.iorganizationservice.retrievemultiple?view=dynamics-general-ce-9) verwendet wird. Sie können das Beispiel [hier](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/RetrieveMultipleQueryByAttribute) herunterladen.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]


## <a name="what-this-sample-does"></a>Funktionsweise:

Diese `QueryByAttribute`-Klasse ist zur Verwendung in einem Szenario bestimmt, in dem sie eine Abfrage enthält, die aus ein Satz von Attribut- und Wertpaaren ausgedrückt wird.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

1. Prüft auf aktuelle Version der Organisation.
1. Die `Account`-Methode erstellt 2 Account-Datensätze.

### <a name="demonstrate"></a>Demonstrieren

1. Die Methode `QueryByAttribute` erstellt eine Abfrage mit QueryByAttribute.

### <a name="clean-up"></a>Bereinigung

1. Zeigt eine Option zum Löschen aller im Beispiel erstellten Daten an.

Das Löschen ist optional, falls Sie die Daten überprüfen möchten, die durch das Beispiel erstellt wurden. Sie können die Daten manuell löschen, um das gleiche Ergebnis zu erzielen.
