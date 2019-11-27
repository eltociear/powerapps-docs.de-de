---
title: 'Beispiel: Erstellen einer reziproken Verbindungsrolle (Common Data Service) | Microsoft-Dokumentation'
description: Dieses Beispiel veranschaulicht, wie eine reziproke Verbindungsrolle erstellt wird.
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
ms.openlocfilehash: e61ee0a712ec8844776bc14231ef18ec82092e07
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748378"
---
# <a name="sample-create-a-reciprocal-connection-role"></a>Beispiel: Eine reziproke Verbindungsrolle erstellen

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-create-reciprocal-connection-role-early-bound -->

Dieses Beispiel veranschaulicht, wie gegenseitige Verbindungsrollen erstellt werden. Es erstellt eine Verbindungsrolle für eine neue Firma sowie eine Verbindungsrolle für einen Kontakt und dann wird die Behandlung reziprok, indem sie einander zugeordnet werden. Sie können das Beispiel von [hier](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/ReciprocalConnection
) herunterladen.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Funktionsweise:

Die `ConnectionRole`- und `ConnectionRoleObjectTypeCode`-Nachrichten sind für die Verwendung in einem Szenario vorgesehen, in dem sie Daten enthalten, die zum Anlegen einer neuen Verbindungsrolle und eines neuen Objekttyps für Verbindungsrollen erforderlich sind.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

1. Prüft auf aktuelle Version der Organisation.
2. Die `ConnectionRole` Nachricht erstellt die Verbindungsrollen, die Sie für das Beispiel benötigen.
3. Die `ConnectionRoleObjectTypeCode` Message erstellt Verbindungsrollen-Objekttyp-Datensatz für Firma.
4. Die `AssociateRequest`-Message ordnet die Verbindungsrollen einander zu.

### <a name="demonstrate"></a>Demonstrieren

1. Führen Sie die anfängliche Abfrage durch und zwischenspeichern Sie die Ergebnisse, einschließlich der `DataToken`
1. Aktualisieren Sie die Datensätze, die in [Setup](#setup) erstellt wurden
1. Führen Sie eine zweite Abfrage aus, diesmal durch den `DataVersion` mit dem `DataToken`-Wert, der aus der ursprünglichen Abfrage abgerufen wurde.
1. Zeigen Sie die Entitätsänderungen an, die durch die zweite Abfrage zurückgegeben wurden

### <a name="clean-up"></a>Bereinigung

1. Zeigt eine Option an, um Beispieldaten zu löschen, die in [Einrichtung](#setup)erstellt wurden.

    Das Löschen ist optional, falls Sie die Entitäten und Daten durchsuchen möchten, die durch das Beispiel erstellt wurden. Sie können die Datensätze manuell löschen, um das gleiche Ergebnis zu erzielen.
