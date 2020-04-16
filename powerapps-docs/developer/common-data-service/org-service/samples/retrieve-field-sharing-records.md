---
title: 'Beispiel: Abrufen von Feldfreigabedatensätzen (Common Data Service) | Microsoft-Dokumentation'
description: Dieses Beispiel zeigt, wie die Feldfreigabedatensätze für eine Entität abgerufen werden können.
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
ms.openlocfilehash: 5b8f151fddc3561654d62ef4d415c6401f7d5ff1
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155630"
---
# <a name="sample-retrieve-field-sharing-records"></a>Beispiel: Abrufen von Feldfreigabedatensätzen

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-retrieve-field-sharing-records -->

Dieses Beispiel veranschaulicht, wie die `PrincipalObjectAttributeAccess` (Feldfreigabe)-Datensätze für eine Entität abgerufen werden. Sie können das Beispiel von [hier](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/RetrieveFieldSharing) herunterladen.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Funktionsweise:

Die Message `PrincipleObjectAttributeAccess` ist dazu vorgesehen, in einem Szenario verwendet zu werden, in dem sie die Feld-Sharing-Datensätze für eine Entität abruft.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

1. Prüft auf aktuelle Version der Organisation.
2. Die Methode `CreateAttributeRequest` erstellt die für das Beispiel erforderlichen benutzerdefinierten Felder.

### <a name="demonstrate"></a>Demonstrieren

1. `WhoAMIRequest` ruft die aktuellen Benutzerinformationen ab.
2. Die Message `RetrieveUserPrivilegesRequest` überprüft, ob der aktuelle Benutzer über `prvReadPOAA` verfügt.
3. `PrincipalObjectAttributeAccess` erstellt POAA-Entität für die benutzerdefinierten Felder, die in Setup (#setup) erstellt werden.
4. Rufen Sie mithilfe von `QueryExpression` vom Benutzer freigegebene Attributberechtigungen ab.

### <a name="clean-up"></a>Bereinigung

Zeigt eine Option an, um Beispieldaten zu löschen, die in [Einrichtung](#setup)erstellt wurden. Das Löschen ist optional, falls Sie die Entitäten und Daten durchsuchen möchten, die durch das Beispiel erstellt wurden. Sie können die Datensätze manuell löschen, um das gleiche Ergebnis zu erzielen.
