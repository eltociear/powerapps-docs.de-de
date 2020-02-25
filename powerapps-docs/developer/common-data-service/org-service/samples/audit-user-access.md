---
title: 'Beispiel: Überwachungsbenutzerzugriff (Common Data Service) | Microsoft-Dokumente'
description: Dieses Beispiel zeigt, wie Sie den Benutzerzugriff überwachen können.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 5e2f07225b842821a32ad6818842c8e08f1ab198
ms.sourcegitcommit: 3bf59896a98e5f01289a2489e185f27518aeaec3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/15/2020
ms.locfileid: "2956225"
---
# <a name="sample-audit-user-access"></a>Beispiel: Überwachung von Benutzerzugriffen

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-audit-user-access -->

Dieser Beispielcode zeigt, wie Sie den Benutzerzugriff überwachen können. Sie können das Beispiel von [hier](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/AuditUserAccess) herunterladen.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Funktionsweise:

Dieses Beispiel aktiviert zunächst die Überwachung des Benutzerzugriffs für die Organisation des angemeldeten Benutzers. Danach wird eine Firmenentität erstellt und so geändert, dass Überwachungsdatensätze generiert werden.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

1. Prüft auf aktuelle Version der Organisation.
1. Erstellt eine neue Firmenentität und aktiviert die Überwachung der neuen Firmenentität.

### <a name="demonstrate"></a>Demonstrieren

1. Ruft die ID der Organisation aus dem Systembenutzersatz ab und ruft den Organisationsdatensatz ab.
2. Aktiviert die Überwachung der Organisation, inklusive der Überwachung des Benutzerzugriffs.
3. Stellt eine Aktualisierungsanforderung an die Accountentität, die durch die Überwachung nachverfolgt werden soll.
4. setzen Sie die Organisations- und Kontoüberprüfungsflags wieder auf alte Werte und rufen Sie sie ab, wenn sie tatsächlich geändert wurden.

### <a name="clean-up"></a>Bereinigung

Zeigt eine Option an, um die Datensätze zu löschen, die in [Einrichtung](#setup)erstellt wurden. Das Löschen ist optional, falls Sie die Entitäten und Daten durchsuchen möchten, die durch das Beispiel erstellt wurden. Sie können die Datensätze manuell löschen, um das gleiche Ergebnis zu erzielen.
