---
title: 'Beispiel: Überwachungsentitäts-Datenenänderungen (Common Data Service) | Microsoft-Dokumente'
description: Dieses Beispiel zeigt, wie Sie Entitätsdatenenänderungen überwachen.
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
ms.openlocfilehash: f6d70ce43942b9012f512fcbce931a616964abb8
ms.sourcegitcommit: 5ec7c7f04fe41896dec966706a3b3d295648726f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/06/2020
ms.locfileid: "2934422"
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
