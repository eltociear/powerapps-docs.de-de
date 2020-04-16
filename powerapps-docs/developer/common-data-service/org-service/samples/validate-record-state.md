---
title: " Überprüfen und Festlegen des Aufzeichnungsstatus (Common Data Service) | Microsoft Docs"
description: Dieses Beispiel zeigt, wie Sie eine Zustandsänderung einer Entität sowie den Status einer Entität validieren müssen.
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
ms.openlocfilehash: 7dc4321cba939a0882e753cdd7741d923b7b2ae4
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155502"
---
# <a name="validate-record-state-and-set-the-state-of-record"></a>Validieren Sie den Datensatzstatus und legen Sie den Status des Datensatzes fest

Dieses Beispiel zeigt, wie Sie eine Zustandsänderung einer Entität sowie den Status einer Entität validieren müssen. Sie können das Beispiel von [hier](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/ValidateandExecuteSavedQuery) herunterladen.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Funktionsweise:

Die `IsValidStateTransitionRequest` Meldung ist für die Verwendung in einem Szenario vorgesehen, in dem sie Daten enthält, die für die Erstellung des Massenlöschungsanfrage erforderlich sind.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

1. Prüft auf aktuelle Version der Organisation.
2. Die Methode `CreateRequiredRecords` erstellt Entitätsdatensätze, die für dieses Beispiel benötigt werden.

### <a name="demonstrate"></a>Demonstrieren

1. Die `EntityReference` Methode erstellt eine EntityReference, um offenen Fall darzustellen. 
2. Die `IsValidStateTransitionRequest` Methode setzt die Übergangsanforderung auf einen offenen Fall.
3. Die `checkState.NewState` prüft, ob ein neuer Status von gelösten und ein neuer Status von gelöstem Problem gültig sind.
4. Die `IsValidStateTransitionResponse` Methode führt die Anforderung aus.

### <a name="clean-up"></a>Bereinigung

Zeigt eine Option an, um Beispieldaten zu löschen, die in [Einrichtung](#setup)erstellt wurden. Das Löschen ist optional, falls Sie die Entitäten und Daten durchsuchen möchten, die durch das Beispiel erstellt wurden. Sie können die Datensätze manuell löschen, um das gleiche Ergebnis zu erzielen.

