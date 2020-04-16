---
title: 'Beispiel: Erstellen einer benutzerdefinierten Aktivität (Common Data Service) | Microsoft-Dokumentation'
description: Dieses Beispiel zeigt, wie eine benutzerdefinierte benutzerdefinierten Aktivität erstellet wird.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: pehecke
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 08d369bbb7aa835bcd9cabc28f04dc3a23e2938e
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155882"
---
# <a name="sample-create-a-custom-activity"></a>Beispiel: Erstellen einer benutzerdefinierten Aktivität

Dieses Beispiel zeigt, wie man eine benutzerdefinierte Aktivität mit [CreateEntityRequest](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.messages.createentityrequest?view=dynamics-general-ce-9) und [CreateAttributeRequest](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.messages.createattributerequest?view=dynamics-general-ce-9) erstellt. Sie können das Beispiel von [hier](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/CustomActivity) herunterladen. 

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Funktionsweise:

Die Nachricht `CreateEntityRequest` und die Nachricht `CreateAttributeRequest` sind für die Verwendung in einem Szenario zum Erstellen einer benutzerdefinierten Aktivität vorgesehen.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

Prüft auf aktuelle Version der aktuellen Organisation.

### <a name="demonstrate"></a>Demonstrieren

1. Erstellt die benutzerdefinierte Aktivitätsentität mit der Meldung `CreateEntityRequest`.
2. Veröffentlicht der erstellte benutzerdefinierte Aktivitätsentität.
3. Erstellt einige Attribute für die benutzerdefinierte Aktivitätsentität mit der Nachricht `CreateAttributeRequest`.

### <a name="clean-up"></a>Bereinigung

Zeigt eine Option an, um die Datensätze in [Einrichtung](#setup) zu löschen. Das Löschen ist optional, falls Sie die Entitäten und Daten durchsuchen möchten, die durch das Beispiel erstellt wurden. Sie können die Datensätze manuell löschen, um das gleiche Ergebnis zu erzielen.
