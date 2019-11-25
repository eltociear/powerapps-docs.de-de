---
title: 'Beispiel: Erstellen einer benutzerdefinierten Aktivität (Common Data Service) | Microsoft-Dokumentation'
description: Dieses Beispiel zeigt, wie eine benutzerdefinierte benutzerdefinierten Aktivität erstellet wird.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
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
ms.openlocfilehash: fa71b952ee6612f01ca0b9f8936eaf2f67a7e1b1
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748380"
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

1. Prüft auf aktuelle Version der aktuellen Organisation.

### <a name="demonstrate"></a>Demonstrieren

1. Erstellt die benutzerdefinierte Aktivitätsentität mit der Meldung `CreateEntityRequest`.
2. Veröffentlicht der erstellte benutzerdefinierte Aktivitätsentität.
3. Erstellt einige Attribute für die benutzerdefinierte Aktivitätsentität mit der Nachricht `CreateAttributeRequest`.

### <a name="clean-up"></a>Bereinigung

1. Zeigt eine Option an, um die Datensätze in [Einrichtung](#setup) zu löschen.

    Das Löschen ist optional, falls Sie die Entitäten und Daten durchsuchen möchten, die durch das Beispiel erstellt wurden. Sie können die Datensätze manuell löschen, um das gleiche Ergebnis zu erzielen.
