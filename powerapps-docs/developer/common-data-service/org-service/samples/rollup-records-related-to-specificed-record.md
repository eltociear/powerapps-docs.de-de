---
title: " Mit einem bestimmten Datensatz verknüpfte Datensätze zusammenfassen (Common Data Service) | Microsoft Docs"
description: In diesem Beispiel wird gezeigt, wie Datensätze, die sich auf einen bestimmten Datensatz beziehen, zusammengefasst werden.
ms.custom: ''
ms.date: 12/20/2019
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
ms.openlocfilehash: ebdaaa74f406a1f640f8d26494a72fa1e5ed31e1
ms.sourcegitcommit: 5ec7c7f04fe41896dec966706a3b3d295648726f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/06/2020
ms.locfileid: "2934556"
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
