---
title: 'Beispiel: Abfrageverbindungsrollen mithilfe von Entitätstypcode (Common Data Service) | Microsoft-Dokumentation'
description: Dieses Beispiel zeigt, wie man eine Verbindungsro
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
ms.openlocfilehash: 25432f43350b6c32dc31a87f913233c3e71bd427
ms.sourcegitcommit: 3bf59896a98e5f01289a2489e185f27518aeaec3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/15/2020
ms.locfileid: "2956189"
---
# <a name="sample-query-connection-roles-by-entity-type-code-early-bound"></a>Beispiel: Abfragenverbindungsrollen mithilfe von Entitätstypcode (frühe Bindung)

Dieses Beispiel zeigt, wie Sie eine Abfrage verwenden können, um eine Verbindungsrolle für eine Firmenentität zu suchen, indem Sie einen Entitätstypcode angeben. Sie können das Beispiel [hier](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/QueryRoleByEntityType) herunterladen.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Funktionsweise:

Dieses Beispiel zeigt, wie Sie eine Abfrage verwenden können, um eine Verbindungsrolle für eine Firmenentität zu suchen, indem Sie einen Entitätstypcode angeben.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

Prüft auf aktuelle Version der Organisation.

### <a name="demonstrate"></a>Demonstrieren

1. Definiert einige anonyme Typen, um den Bereich der möglichen Werte für die Verbindungseigenschaften festzulegen.
2. `ConnectionRole` erstellt eine Verbindungsrolle.
3. `QueryExpression` fragt alle Verbindungsrollen ab.
4. `ConnectionRoleObjectTypeCode` erstellt eine Verbindungsrollen-Objekttypcode-Datensatz für die Account-Entität. 

### <a name="clean-up"></a>Bereinigung

Zeigt eine Option an, um die Datensätze in [Einrichtung](#setup) zu löschen. Das Löschen ist optional, falls Sie die Entitäten und Daten durchsuchen möchten, die durch das Beispiel erstellt wurden. Sie können die Datensätze manuell löschen, um das gleiche Ergebnis zu erzielen.
