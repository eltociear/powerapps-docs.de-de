---
title: 'Beispiel: Verwenden der Duplikaterkennung für die Erstellung und Aktualisierung von Datensätzen (Common Data Service) | Microsoft-Dokumentation'
description: Dieses Beispiel zeigt, wie Sie die Duplikaterkennung für die Erstellung und Aktualisierung von Entitätsdatensätzen aufrufen.
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
ms.openlocfilehash: 3a2d39ee12b098698115c77ee78a6ae71107f755
ms.sourcegitcommit: 303d5aed44f2bbb406cabeb6b9c8474d738d9114
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "3005047"
---
# <a name="sample-use-duplicate-detection-when-creating-and-updating-records"></a>Beispiel: Verwenden der Duplikaterkennung für die Erstellung und Aktualisierung von Datensätzen

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/org-service/sample-use-duplicate-detection-when-creating-and-updating-records -->
 Dieses Beispiel zeigt, wie Sie die Duplikaterkennung für die Erstellung und Aktualisierung von Entitätsdatensätzen aufrufen. Sie können das Beispiel [hier](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/UseDuplicatedetectionforCRUD) herunterladen.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]


## <a name="what-this-sample-does"></a>Funktionsweise:

Die `DuplicateRule`-Methode ist dazu vorgesehen, in einem Szenario verwendet zu werden, in dem sie Daten enthält, die zur Erstellung einer Duplikaterkennungsregel benötigt werden.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

1. Prüft auf aktuelle Version der Organisation.
1. Die `Account`-Methode erstellt einen Firmendatensatz. 
1. Die `DuplicateRule`-Methode erstellt eine Duplikaterkennungsregel.
1. Die `DuplicateRuleCondition`-Methode erstellt Bedingungen einer Duplikaterkennungsregel.
1. Die `PublishDuplicateRuleRequest`-Methode veröffentlicht die Duplikaterkennungsregel, die früher erstellt wurde. Sie müssen warten, bis der Veröffentlichungsvorgang abgeschlossen ist. Daher fragen wir weiterhin den Status der Regel ab, bis sie `Published` wird.

### <a name="demonstrate"></a>Demonstrieren
1. Die `Account`-Methode erstellt einen Firmendatensatz. 
1. Die `CreateRequest`-Methode erzeugt eine Operation durch Unterdrückung der Dublettenerkennung.
1. Die `UpdateRequest`-Methode aktualisiert den abgerufenen Firmendatensatz mit der neuen Kontonummer.

### <a name="clean-up"></a>Bereinigung

Zeigt eine Option zum Löschen aller im Beispiel erstellten Daten an. Das Löschen ist optional, falls Sie die Daten überprüfen möchten, die durch das Beispiel erstellt wurden. Sie können die Daten manuell löschen, um das gleiche Ergebnis zu erzielen.
