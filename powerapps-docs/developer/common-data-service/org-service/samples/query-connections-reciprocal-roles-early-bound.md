---
title: 'Beispiel: Abfragen von Verbindungen durch reziproke Rollen (Common Data Service) | Microsoft-Dokumentation'
description: Dieses Beispiel veranschaulicht, wie Verbindungsrollen durch rezproke Rollen abgefragt werden.
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
ms.openlocfilehash: 86cd5b567d6db0ede136530a51511beb8febb07e
ms.sourcegitcommit: 3bf59896a98e5f01289a2489e185f27518aeaec3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/15/2020
ms.locfileid: "2956185"
---
# <a name="sample-query-connections-by-reciprocal-roles-early-bound"></a>Beispiel: Abfragen von Verbindungen durch reziproke Rollen (frühe Bindung)

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-query-connections-reciprocal-roles-early-bound -->

Dieses Beispiel zeigt, wie entsprechende Rollen erstellt werden und dann eine entsprechende Rolle für eine bestimmte Rolle gefunden wird. Sie können das Beispiel [hier](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/QueryByReciprocalRole) herunterladen.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Funktionsweise:

Dieses Beispiel zeigt, wie entsprechende Rollen erstellt werden und dann eine entsprechende Rolle für eine bestimmte Rolle gefunden wird.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

1. Prüft auf aktuelle Version der Organisation.
2. Definiert einige anonyme Typen, um den Bereich der möglichen Werte für die Verbindungseigenschaften festzulegen.
3. `ConnectionRole` erstellt die primäre Instanz der Verbindungsrolle.
4. `ConnectionRoleObjectTypeCode` erstellt eine Verbindungsrollen-Objekttypcode-Datensatz für die Account- und Kontakt-Entität.
5. `AssociateRequest` ordnet die Verbindungsrollen zu.

### <a name="demonstrate"></a>Demonstrieren

`QueryExpression` ruft alle Verbindungsrollen ab, für die diese Rolle als reziprokale Rolle aufgelistet ist.

### <a name="clean-up"></a>Bereinigung

Zeigt eine Option an, um die Datensätze in [Einrichtung](#setup) zu löschen. Das Löschen ist optional, falls Sie die Entitäten und Daten durchsuchen möchten, die durch das Beispiel erstellt wurden. Sie können die Datensätze manuell löschen, um das gleiche Ergebnis zu erzielen.
