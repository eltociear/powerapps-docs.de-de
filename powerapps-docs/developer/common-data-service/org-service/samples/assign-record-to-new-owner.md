---
title: " Zuweisen eines Datensatzes an einen neuen (Common Data Service) | Microsoft Docs"
description: In diesem Beispiel wird gezeigt, wie Datensätze einem neuen Besitzer zugewiesen werden.
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
ms.openlocfilehash: 0e6df124f8fcd9baf4658263bc65d510af3ac003
ms.sourcegitcommit: 3bf59896a98e5f01289a2489e185f27518aeaec3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/15/2020
ms.locfileid: "2956327"
---
# <a name="assign-a-record-to-a-new-owner"></a>Einen Datensatz einem neuen Besitzer zuweisen

Dieses Beispiel zeigt, wie ein Konto einem anderen Benutzer mithilfe der Message [IOrganizationService.Update](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.iorganizationservice.update?view=dynamics-general-ce-9) zugewiesen wird.

Dieses Beispiel verwendet die `IOrganization.Update`-Methode und nicht die [AssignRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.assignrequest?view=dynamics-general-ce-9), weil es einen Aufwand gibt, spezialisierte Nachrichten zu entfernen. Mehr Informationen: [Durchführen von spezialisierten Operationen mit update](https://docs.microsoft.com/powerapps/developer/common-data-service/special-update-operation-behavior)

Sie können das Beispiel von [hier](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/AssignRecordToNewOwner) herunterladen.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Funktionsweise:

Die Nachricht [IOrganizationService.Update](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.iorganizationservice.update?view=dynamics-general-ce-9) ist für ein Szenario gedacht, in dem sie die Daten enthält, die zur Aktualisierung eines bestehenden Datensatzes benötigt werden.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichtung

1. Prüft auf aktuelle Version der Organisation. 
1. Erstellt die für dieses Beispiel erforderlichen Daten.

### <a name="demonstrate"></a>Demonstrieren

1. Die `Retrieve`-Methode ruft die in der Einrichtung (#setup) erstellten Kontodatensätze ab.
1. Die `Update`-Nachricht aktualisiert das `ownerid`-Attribut für den Benutzer, dem der Datensatz gehören soll. 

### <a name="clean-up"></a>Bereinigung

Zeigt eine Option zum Löschen aller im Beispiel erstellten Daten an. Das Löschen ist optional, falls Sie die Daten überprüfen möchten, die durch das Beispiel erstellt wurden. Sie können die Daten manuell löschen, um das gleiche Ergebnis zu erzielen.