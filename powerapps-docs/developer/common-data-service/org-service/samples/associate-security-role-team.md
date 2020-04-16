---
title: " Sicherheitsrolle einem Team zuweisen (Common Data Service) | Microsoft-Dokumentation"
description: 'Dieses Beispiel zeigt, wie eine Sicherheitsrolle einem Team zugewiesen wird '
ms.custom: ''
ms.date: 12/20/2019
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
ms.openlocfilehash: 6ea2984f5fd8ad276581307edf3ff76ca1abeef8
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155950"
---
# <a name="sample-associate-security-role-to-a-team"></a>Beispiel: Zuordnen einer Sicherheitsrolle zu einem Team 

Dieses Beispiel zeigt, wie einem Team mithilfe der Meldung [AssignRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.assignrequest?view=dynamics-general-ce-9) eine Sicherheitsrolle zugewiesen wird. Beachten Sie, dass dieses Beispiel nicht berücksichtigt, dass einem Team oder einem Benutzer nur von deren Unternehmenseinheit eine Rolle zugewiesen werden kann. Die Rolle, die zugewiesen werden soll, ist die erste in der Sammlung, die von der Methode RetrieveMultiple zurückgegeben wird. Wenn dieser Datensatz aus einer Unternehmenseinheit stammt, die nicht zu dem anfordernden Team gehört, schlägt die Zuweisung fehl.

Sie können das Beispiel [hier](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/AssociateSecurityRoleToTeam) herunterladen.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Funktionsweise:

Die Meldung [AssignRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.assignrequest?view=dynamics-general-ce-9) soll in einem Szenario verwendet werden, in dem sie Daten enthält, die erforderlich sind, um den angegebenen Datensatz einem neuen Besitzer (Benutzer oder Team) zuzuweisen, indem das OwnerId-Attribut des Datensatzes geändert wird.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

1. Prüft auf aktuelle Version der Organisation.
2. Die `CreateRequiredRecords`-Methode erstellt die erforderlichen Datensätze für das Beispiel.

### <a name="demonstrate"></a>Demonstrieren

1. Die `query` Methode ruft eine Rolle von Common Data Service ab.
2. Die Meldung `Associate` weist die Rolle einem Team zu.

### <a name="clean-up"></a>Bereinigung

Zeigt eine Option an, um die Beispieldaten zu löschen, die in [Einrichtung](#setup)erstellt wurden. Das Löschen ist optional, falls Sie die Entitäten und Daten durchsuchen möchten, die durch das Beispiel erstellt wurden. Sie können die Datensätze manuell löschen, um das gleiche Ergebnis zu erzielen.
