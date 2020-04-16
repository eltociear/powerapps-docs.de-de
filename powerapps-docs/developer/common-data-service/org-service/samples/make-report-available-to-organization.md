---
title: 'Beispiel: Einen Bericht für die Organisation verfügbar oder nicht verfügbar machen (Common Data Service) | Microsoft Docs'
description: Dieses Beispiel zeigt, wie Sie einen Bericht für die Organisation verfügbar machen bzw. wie Sie die Verfügbarkeit aufheben.
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
ms.openlocfilehash: 7c248c4393bd2872b3fba32977b47ebd32b15c17
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155726"
---
# <a name="make-a-report-available-or-unavailable-to-organization"></a>Stellen Sie der Organisation einen Bericht zur Verfügung oder nicht zur Verfügung

Dieses Beispiel zeigt, wie Sie einen Bericht für die Organisation verfügbar machen bzw. wie Sie die Verfügbarkeit aufheben. Sie können das Beispiel von [hier](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/MakeReportAvailableToOrganization) herunterladen.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das oben beschriebene Beispiel zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

1. Prüft auf aktuelle Version der Organisation.
2. Die Methode `CreateRequiredRecords` erstellt Entitätsdatensätze, die für dieses Beispiel benötigt werden.

### <a name="demonstrate"></a>Demonstrieren

1. Die `service.Retrieve`-Methode ruft einen vorhandenen persönlichen Bericht ab.
2. Setzen Sie den Parameter `IsPersonal` auf "falsch".
3. Die `service.Update`-Methode stellt den Bericht für die Organisation zur Verfügung.
4. Setzen Sie den Parameter `IsPersonal` auf wahr. Dadurch steht der Bericht für die Organisation nicht zur Verfügung.

### <a name="clean-up"></a>Bereinigung

Zeigt eine Option an, um Beispieldaten zu löschen, die in [Einrichtung](#setup)erstellt wurden. Das Löschen ist optional, falls Sie die Entitäten und Daten durchsuchen möchten, die durch das Beispiel erstellt wurden. Sie können die Datensätze manuell löschen, um das gleiche Ergebnis zu erzielen.
