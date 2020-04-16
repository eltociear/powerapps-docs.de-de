---
title: " Erstellen und Aktualisieren einer E-Mail-fähigen Entität (Common Data Service) | Microsoft-Dokumentation"
description: Dieses Beispiel zeigt, wie Sie eine per E-Mail versendbare Entität erstellen und aktualisieren.
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
ms.openlocfilehash: 26150d445c129658b91c51810c99e74ff56e5f64
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155854"
---
# <a name="create-an-email-entity"></a>Eine E-Mail-Entität erstellen

Dieses Beipiel zeigt, wie Sie eine Entität mithilfe der Nachricht [CreateEntityRequest](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.messages.createentityrequest?view=dynamics-general-ce-9) erstellen.

Sie können das Beispiel von [hier](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/CreateUpdateEmailableEntity) herunterladen.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Funktionsweise:

Die Nachricht `CreateEntityRequest` soll in einem Szenario verwendet werden, in dem sie die Daten enthält, die zum Erstellen einer benutzerdefinierten Entität und optional zu deren Hinzufügen zu einer angegebenen nicht verwalteten Lösung erforderlich sind.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

Prüft auf aktuelle Version der Organisation.

### <a name="demonstrate"></a>Demonstrieren

1. Die `Entity`-Methode erstellt die benutzerdefinierte Entität. Definieren Sie die Entität, um ihren E-Mail-Versand zu aktivieren. Dazu muss `IsActivityParty` auf „true“ festegelegt werden.
2. Die Methode `StringAttributeMetadata` wird verwendet, um das primäre Attribut der Entität zu definieren, das in den ActivityParty-Anzeigen verwendet wird. Stellen Sie sicher, dass Sie beschreibende Attribute auswählen.
3. Die `PublishRequest`-Methode veröffentlicht alle Anpassungen.
4. Die `CreateFirstEmailAttributeRequest`-Methode erstellt ein E-Mail-Attribut, um E-Mails von der Entität zu erstellen.

### <a name="clean-up"></a>Bereinigung

Zeigt eine Option an, um die Datensätze zu löschen, die in der [Einrichtung](#setup)erstellt wurden. Das Löschen ist optional, falls Sie die Entitäten und Daten durchsuchen möchten, die durch das Beispiel erstellt wurden. Sie können die Datensätze manuell löschen, um das gleiche Ergebnis zu erzielen.

