---
title: 'Beispiel: Abrufen von E-Mail-Anlagen für eine E-Mail-Vorlage (Common Data Service) | Microsoft-Dokumentation'
description: Dieses Beispiel zeigt, wie E-Mail-Anlagen, die einer E-Mail-Vorlage zugeordnet sind, abgerufen werden.
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
ms.openlocfilehash: 9c7ffaa212de51d019794282b12e43bfb0f7388a
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748724"
---
# <a name="sample-retrieve-email-attachments-for-an-email-template"></a>Beispiel: Abrufen von E-Mail-Anlagen für eine E-Mail-Vorlage

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-retrieve-email-attachments-email-template -->

Dieses Beispiel zeigt, wie E-Mail-Anlagen, die einer E-Mail-Vorlage zugeordnet sind, mithilfe der Methode [IOrganizationService.RetrieveMultiple](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.iorganizationservice.retrievemultiple?view=dynamics-general-ce-9) abgerufen werden können. Sie können das Beispiel [hier](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/RetrieveEmailAttach) herunterladen.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Funktionsweise:

Die Methode `IOrganizationService.RetrieveMultiple` ist dazu vorgesehen, in einem Szenario verwendet zu werden, in dem sie eine Sammlung von Datensätzen abruft.


## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

1. Prüft auf aktuelle Version der Organisation.
2. Erstellt eine Beispiele-E-Mail-Vorlage mit der `Template`-Methode.

### <a name="demonstrate"></a>Demonstrieren

1. `QueryExpression` ruft alle Anlagen ab.

### <a name="clean-up"></a>Bereinigung

1. Zeigt eine Option an, um Beispieldaten zu löschen, die in [Einrichtung](#setup)erstellt wurden.

    Das Löschen ist optional, falls Sie die Entitäten und Daten durchsuchen möchten, die durch das Beispiel erstellt wurden. Sie können die Datensätze manuell löschen, um das gleiche Ergebnis zu erzielen.
