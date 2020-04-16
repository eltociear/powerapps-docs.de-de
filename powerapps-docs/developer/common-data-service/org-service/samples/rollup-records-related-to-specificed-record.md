---
title: " Mit einem bestimmten Datensatz verknüpfte Datensätze zusammenfassen (Common Data Service) | Microsoft Docs"
description: In diesem Beispiel wird gezeigt, wie Datensätze, die sich auf einen bestimmten Datensatz beziehen, zusammengefasst werden.
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
ms.openlocfilehash: 7756f3b180e57277a6350eca261898ecec264032
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155594"
---
# <a name="rollup-records-related-to-a-specific-record"></a>Mit einem bestimmten Datensatz verknüpfte Datensätze zusammenfassen

Dieses Beispiel zeigt, wie Sie ein Rollup der Verkaufschancen nach ihrer übergeordneten Firma durchführen. Sie können das Beispiel von [hier](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/RollupSpecificRecords) herunterladen.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Funktionsweise:

Die `RollupRequest` Meldung ist dazu vorgesehen, in einem Szenario verwendet zu werden, in dem sie Daten enthält, um eine Rollup-Anfrage zu erstellen.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichtung

1. Prüft auf aktuelle Version der Organisation.
2. Erstellt Beispielkonten- und Verkaufschancen-Datensätze.

### <a name="demonstrate"></a>Demonstrieren

1. Das `QueryExpression` fragt die Verkaufschancen nach übergeordnete Firma ab.
2. Das `RollupRequest` erstellt die Rollup-Anfrage.

### <a name="clean-up"></a>Bereinigung

Zeigt eine Option an, um die Datensätze in [Einrichtung](#setup) zu löschen. Das Löschen ist optional, falls Sie die Entitäten und Daten durchsuchen möchten, die durch das Beispiel erstellt wurden. Sie können die Datensätze manuell löschen, um das gleiche Ergebnis zu erzielen.
