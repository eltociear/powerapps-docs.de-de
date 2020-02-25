---
title: " Zwei Datensätze zusammenführen (Common Data Service) | Microsoft Docs"
description: Dieses Beispiel zeigt, wie zwei Datensätze zusammengeführt werden.
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
ms.openlocfilehash: d354f49535b8afe0bcc7a246879bbd25c2ad7bc6
ms.sourcegitcommit: 3bf59896a98e5f01289a2489e185f27518aeaec3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/15/2020
ms.locfileid: "2956193"
---
# <a name="merge-two-record"></a>Zusammenführen von zwei Datensätzen

Dieses Beispiel zeigt, wie zwei Datensätze zusammengeführt werden. Sie können das Beispiel von [hier](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/MergeTwoRecords) herunterladen.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Funktionsweise:

Die Nachricht `MergeRequest` ist für die Verwendung in einem Szenario vorgesehen, in dem sie Daten enthält, die benötigt werden, um die Informationen von zwei Entitätsdatensätze vom gleichen Beispiel zusammenzuführen.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

1. Prüft auf aktuelle Version der Organisation.
2. Die Methode `CreateRequiredRecords` erstellt Entitätsdatensätze, die für dieses Beispiel benötigt werden.

### <a name="demonstrate"></a>Demonstrieren

1. Die `MergeRequest` Methode erstellt die Überprüfungsanforderung. 
2. Die `Account` Meldung erstellt ein anderes Konto, um neue Daten zu speichern, die mit der Entität zusammengeführt werden sollen.


### <a name="clean-up"></a>Bereinigung

Zeigt eine Option an, um Beispieldaten zu löschen, die in [Einrichtung](#setup)erstellt wurden. Das Löschen ist optional, falls Sie die Entitäten und Daten durchsuchen möchten, die durch das Beispiel erstellt wurden. Sie können die Datensätze manuell löschen, um das gleiche Ergebnis zu erzielen.

