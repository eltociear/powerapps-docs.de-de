---
title: 'Beispiel: Entität-Beziehungen anlegen und abrufen (Common Data Service) | Microsoft Docs'
description: Dieses Beispiel zeigt, wie Entitätsbeziehungen erstellt und abgerufen werden.
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
ms.openlocfilehash: fab6347b512d0048c5e666c551a99c43c99915df
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155981"
---
# <a name="create-and-retrieve-entity-relationships"></a>Erstellen und Abrufen von Entitätsbeziehungen

Dieses Beispiel zeigt, wie Entitätsbeziehungen erstellt und abgerufen werden. Die folgenden Methoden werden verwendet, um die Beziehungen zu erstellen und abzurufen:

- [CreateOneToManyRequest](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.messages.createonetomanyrequest?view=dynamics-general-ce-9)
- [CreateManyToManyRequest](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.messages.createmanytomanyrequest?view=dynamics-general-ce-9)
- [CanBeReferencedRequest](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.messages.canbereferencedrequest?view=dynamics-general-ce-9)
- [CanBeReferencingRequest](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.messages.canbereferencingrequest?view=dynamics-general-ce-9)
- [CanManyToManyRequest](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.messages.canmanytomanyrequest?view=dynamics-general-ce-9)
- [RetrieveRelationshipRequest](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.messages.retrieverelationshiprequest?view=dynamics-general-ce-9)

Sie können das Beispiel von [hier](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/CreateRetrieveEntityRelationships) herunterladen.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Funktionsweise:

Die `CreateOneToManyRequest`, `CreateManyToManyRequest`, `CanManyToManyRequest`,`CreateOneToManyRequest`, `CanBeReferencedRequest`, `CanBeReferencingRequest` und `RetrieveRelationshipRequest` Nachrichten sind für die Verwendung in einem Szenario vorgesehen, in dem sie Daten enthalten, die für das Gewähren, Ändern und Widerrufen des Zugriffs erforderlich sind.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

Prüft auf aktuelle Version der Organisation.

### <a name="demonstrate"></a>Demonstrieren

1. Die `CreateOneToManyRequest` Methode erstellt eine neue Eins-zu-Viele-Beziehung (1:N). 
2. Die `CreateManyToManyRequest` Methode erstellt eine neue Viele-zu-Viele-Beziehung (N:N).
3. Die `EligibleCreateManyToManyRelationship` Methode überprüft, ob Entitäten an der N:N-Beziehung teilnehmen können.
4. Die `RetrieveRelationshipRequest` Methode ruft die beiden Entitätsbeziehungen ab, die zuvor erstellt werden.


### <a name="clean-up"></a>Bereinigung

Zeigt eine Option an, um die Datensätze zu löschen, die in der [Einrichtung](#setup)erstellt wurden. Das Löschen ist optional, falls Sie die Entitäten und Daten durchsuchen möchten, die durch das Beispiel erstellt wurden. Sie können die Datensätze manuell löschen, um das gleiche Ergebnis zu erzielen.
