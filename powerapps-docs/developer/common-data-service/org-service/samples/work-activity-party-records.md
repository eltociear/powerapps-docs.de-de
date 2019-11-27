---
title: 'Beispiel: Arbeiten mit Aktivitätsparteidatensätzen (Common Data Service) | Microsoft-Dokumentation'
description: In diesem Beispiel wird das Arbeiten mit Aktivitätsparteidatensätzen dargestellt.
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
ms.openlocfilehash: ce1824020e8ca09380d34d871b4222f132837e87
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748696"
---
# <a name="sample-work-with-activity-party-records"></a>Beispiel: Arbeiten mit Aktivitätsparteidatensätzen

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-work-activity-party-records -->

Dieser Beispielcode zeigt, wie mit Aktivitätsparteidatensätzen gearbeitet wird. Sie können das Beispiel von [hier](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/ActivityPartyRecords) herunterladen.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Funktionsweise:

In diesem Beispiel werden einige Beispieldaten erstellt, um mit Aktivitätspartei-Datensätzen zu arbeiten. 

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

1. Prüft auf aktuelle Version der Organisation.
1. Erstellt drei Kontaktdatensätze, die für dieses Beispiel erforderlich sind.


### <a name="demonstrate"></a>Demonstrieren

1. Ruft die Kontaktdatensätze ab, die im [Setup](#setup) erstellt werden. 
2. Erstellt die Aktivitätsparteidatensätze für jeden Kontakt.
3. Erstellt auch die Briefaktivität und legt die Felder **Von** und **Bis** auf die entsprechenden Aktivitätspartei-Entitäten fest.

### <a name="clean-up"></a>Bereinigung

1. Zeigt eine Option an, um die Datensätze zu löschen, die in [Einrichtung](#setup)erstellt wurden.

    Das Löschen ist optional, falls Sie die Entitäten und Daten durchsuchen möchten, die durch das Beispiel erstellt wurden. Sie können die Datensätze manuell löschen, um das gleiche Ergebnis zu erzielen.
