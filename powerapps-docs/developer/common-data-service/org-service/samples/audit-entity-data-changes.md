---
title: 'Beispiel: Überwachungsentitäts-Datenenänderungen (Common Data Service) | Microsoft-Dokumente'
description: Dieses Beispiel zeigt, wie Sie Entitätsdatenenänderungen überwachen.
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
ms.openlocfilehash: 907ac09f9cd530c26c2e577351736d52f005a65a
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155926"
---
# <a name="sample-audit-entity-data-changes"></a>Beispiel: Überwachung von Entitätsdatenänderungen

Dieses Beispiel zeigt, wie Sie die Überwachung für eine Entität und ihre Attribute aktivieren und deaktivieren, die Datenänderungshistorie der überwachten Entität abrufen und die Überwachungsdatensätze löschen können. Sie können das Beispiel von [hier](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/AuditEntityData) herunterladen.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Funktionsweise:

Die `RetrieveRecordChangeHistoryRequest`-Message ist für die Verwendung in einem Szenario vorgesehen, in dem sie Daten enthält, die zum Abrufen der Überwachungshistorie einer Entität erforderlich sind.


## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

1. Prüft auf aktuelle Version der Organisation.
2. Erstellt eine Beispiel-Firmenentität.

### <a name="demonstrate"></a>Demonstrieren

1. Ermittelt die ID der Organisation aus dem Systembenutzerdatensatz.
2. Aktivieren der Überwachung in der Organisations- und auch in der Beispiel-Firmenentität.
3. Die `RetrieveRecordChangeHistoryRequest` ruft den Überwachungsverlauf für die Firmenentität ab und zeigt das Ergebnis an.

### <a name="clean-up"></a>Bereinigung

Zeigt eine Option an, um Beispieldaten zu löschen, die in [Einrichtung](#setup)erstellt wurden. Das Löschen ist optional, falls Sie die Entitäten und Daten durchsuchen möchten, die durch das Beispiel erstellt wurden. Sie können die Datensätze manuell löschen, um das gleiche Ergebnis zu erzielen.
