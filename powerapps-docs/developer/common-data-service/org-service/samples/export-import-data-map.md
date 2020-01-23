---
title: 'Beispiel: Exportieren und Importieren einer Datenzuordnung (Common Data Service) | Microsoft-Dokumentation'
description: Dieses Beispiel veranschaulicht, wie Sie eine Datenzuordnung erstellen und diese exportieren
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: samples
author: mayadumesh
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: c87fb5601d01eaffb832c2b9b9452a3925ac2097
ms.sourcegitcommit: 5ec7c7f04fe41896dec966706a3b3d295648726f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/06/2020
ms.locfileid: "2934290"
---
# <a name="sample-export-and-import-a-data-map"></a>Beispiel: Exportieren und Importieren einer Datenzuordnung

Dieses Beispiel zeigt, wie Sie eine Importzuordnung (Datenzuordnung) in Common Data Service erstellen, diese als XML-formatierte Daten exportieren, geänderte Zuordnungen importieren und eine neue Importzuordnung in Common Data Service basierend auf den importierten Zuordnungen erstellen. Sie können das Beispiel herunterladen von [hier](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/ExportImportDataMap).

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Funktionsweise:

Die `BulkDeleteRequest`-Message ist für die Verwendung in einem Szenario vorgesehen, in dem sie Daten enthält, die für die Erstellung des Massenlöschungsanfrage erforderlich sind.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

1. Prüft auf aktuelle Version der Organisation. 
2. Die `CreateImportMapping` Methode erstellt den Importzuordnungsdatensatz.
3. Die `RetrieveMappingXML` Methode exportiert die Zuordnung, die erstellt werden.
4. Die `ChangeMappingName`-Methode veranlasst, dass XML das Namensattribut ändert.

### <a name="clean-up"></a>Bereinigung

Zeigt eine Option an, um Beispieldaten zu löschen, die in [Einrichtung](#setup)erstellt wurden. Das Löschen ist optional, falls Sie die Entitäten und Daten durchsuchen möchten, die durch das Beispiel erstellt wurden. Sie können die Datensätze manuell löschen, um das gleiche Ergebnis zu erzielen.


### <a name="see-also"></a>Siehe auch

[Importieren von Daten](../../import-data.md)<br />
[Vorbereiten einer Quelldatei für den Import](../../prepare-source-files-import.md)<br />
[Erstellen von Datenzuordnungen für den Import](../../create-data-maps-for-import.md)<br />
[Hinzufügen von Transformationszuordnungen für den Import](../../add-transformation-mappings-import.md)<br />
[Konfiguration des Datenimports](../../configure-data-import.md)<br />
[Ausführen des Datenimports](../../run-data-import.md)<br />
[Datenimportentitäten](../../data-import-entities.md)<br />
[Beispiel: Importieren von Daten mithilfe der komplexen Datenzuordnung](import-data-complex-data-map.md)<br />
