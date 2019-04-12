---
title: 'Beispiel: Benutzerzugriff überwachen (Common Data Service) | Microsoft Docs'
description: 'Dieses Beispiel zeigt, wie Sie den Benutzerzugriff überwachen können.'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: brandonsimons
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
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

1. Ermittelt die ID der Organisation aus dem Systembenutzerdatensatz und ruft den Unternehmensdatensatz ab.
2. Aktiviert die Überwachung der Organisation, inklusive der Überwachung des Benutzerzugriffs.
3. Stellt eine Aktualisierungsanforderung an die Accountentität, die durch die Überwachung nachverfolgt werden soll.
4. setzen Sie die Organisations- und Kontoüberprüfungsflags wieder auf alte Werte und rufen Sie sie ab, wenn sie tatsächlich geändert wurden.

### <a name="clean-up"></a>Bereinigung

1. Zeigt eine Option an, um die Datensätze zu löschen, die in [Einrichtung](#setup)erstellt wurden. 

    Das Löschen ist optional, falls Sie die Entitäten und Daten durchsuchen möchten, die durch das Beispiel erstellt wurden. Sie können die Datensätze manuell löschen, um das gleiche Ergebnis zu erzielen.
