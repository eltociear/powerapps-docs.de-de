---
title: 'Beispiel: Mehrere Anforderungen in einer Transaktion (Common Data Service) ausführen | Microsoft Docs'
description: Dieses Beispiel zeigt, wie mehrere Anforderungen in der Transaktion ausgeführt werden.
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
ms.openlocfilehash: a02a88b5939a1997df01f8f2344ee6cdd85ecb04
ms.sourcegitcommit: 3bf59896a98e5f01289a2489e185f27518aeaec3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/15/2020
ms.locfileid: "2956323"
---
# <a name="sample-execute-multiple-requests-in-transaction"></a>Beispiel: Mehrere Anforderungen in einer Transaktion ausführen

Dieses Beispiel zeigt, wie ein einzelnen Internet-Methodeninternetaufruf verwendet wird, um alle Nachrichtenanforderungen in der Sammlung als Teil einer einzelnen Datenbanktransaktion auszuführen. Es ist eine allgemeine Anforderung in Geschäftsanwendungen, Änderungen mehrerer Datensätze im System zu koordinieren, sodass entweder alle Datenänderungen erfolgreich sind oder keine. Unter Datenbankbedingungen ist dies bekannt als Ausführung von mehreren Vorgängen in einer einzelnen Transaktion mit der Möglichkeit eines Rollbacks aller Datenänderungen, falls einer der Vorgänge nicht erfolgreich ist.

Sie können mehrere Organisationsserviceanforderungen in einer einzelnen Datenbanktransaktion mit der [ExecuteTransactionRequest](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.messages.executetransactionrequest?view=dynamics-general-ce-9)-Message-Anforderung ausführen. 

Sie können das Beispiel von [hier](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/ExecuteMultipleInTransaction) herunterladen.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Funktionsweise:

Die `ExecuteTransactionRequest` Nachricht wird in einem Szenario verwendet werden, in der sie Daten enthält, die erforderlich ist, um mindestens eine Nachrichtenanforderungen in einer einzelnen Datenbanktransaktion auszuführen und optional einer Sammlung Ergebnisse zurückgegeben werden.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

Prüft auf aktuelle Version der Organisation.

### <a name="demonstrate"></a>Demonstrieren

1. Die `ExecuteTransactionRequest` Methode erstellt das `ExecuteTransactionRequest`-Objekt.
2. Die `OrganizationRequestCollection` Methode erstellt eine leere Organisationsanforderungssammlung.
3. Die `CreateRequest` Methode ist für jede Entität in Anforderungssammlung hinzugefügt.

### <a name="clean-up"></a>Bereinigung

Zeigt eine Option an, um die Datensätze zu löschen, die in der [Einrichtung](#setup)erstellt wurden. Das Löschen ist optional, falls Sie die Entitäten und Daten durchsuchen möchten, die durch das Beispiel erstellt wurden. Sie können die Datensätze manuell löschen, um das gleiche Ergebnis zu erzielen.
