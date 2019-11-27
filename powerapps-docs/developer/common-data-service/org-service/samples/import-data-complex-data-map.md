---
title: 'Beispiel: Importieren von Daten mithilfe der komplexen Datenzuordnung (Common Data Service) | Microsoft-Dokumentation'
description: Dieses Beispiel zeigt, wie neue Datensätze mithilfe des Datenimports erstellt werden.
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
ms.openlocfilehash: bb2583ce166564dd2ed8bad515bc2ab46409559e
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748744"
---
# <a name="sample-import-data-using-complex-data-map"></a>Beispiel: Importieren von Daten mithilfe der komplexen Datenzuordnung

Dieses Beispiel zeigt, wie neue Datensätze mithilfe des Datenimports erstellt werden. In diesem Beispiel wird eine komplexe Datenzuordnung verwendet. Sie können das Beispiel herunterladen von [hier](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/ImportComplexDataMap).

>[!NOTE]
> Die Quelldaten für dieses Beispiel sind in der folgenden Datei enthalten: `ImportComplexDataMap\import accounts.csv`

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das oben beschriebene Beispiel zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

1. Prüft auf aktuelle Version der Organisation.
1. Die `ImportMap` Methode erstellt eine Importzuordnung.
1. Die `ColumnMapping` Methode erstellt eine Spaltenzuordnung für das Typfeld `text`.
1. Die `EntityReference` Methode verknüpft die Spaltenzuordnung mit der Datenzuordnung.
1. Die `LookUpMapping` Methode erstellt eine Suchzuordnung der übergeordneten Firma.
1. Die `ImportFile` Methode erstellt eine Importdatei.
1. Die `GetHeaderColumnsImportFileRequest` Methode ruft die Kopfzeilenspalten ab, die in der Importdatei verwendet werden.
1. Die `ParseImportRequest` Methode analysiert die Importdatei. 
1. Die `RetrievedParsedDataImportFileRequest` Methode ruft die Daten aus der Analysetabelle ab.
1. Die `TransformImportRequest` Methode transformiert der Import.


### <a name="clean-up"></a>Bereinigung

1. Zeigt eine Option an, um die Datensätze zu löschen, die in der [Einrichtung](#setup)erstellt wurden.

    Das Löschen ist optional, falls Sie die Entitäten und Daten durchsuchen möchten, die durch das Beispiel erstellt wurden. Sie können die Datensätze manuell löschen, um das gleiche Ergebnis zu erzielen.


### <a name="see-also"></a>Siehe auch

[Importieren von Daten](../../import-data.md)<br />
[Vorbereiten einer Quelldatei für den Import](../../prepare-source-files-import.md)<br />
[Erstellen von Datenzuordnungen für den Import](../../create-data-maps-for-import.md)<br />
[Hinzufügen von Transformationszuordnungen für den Import](../../add-transformation-mappings-import.md)<br />
[Konfiguration des Datenimports](../../configure-data-import.md)<br />
[Ausführen des Datenimports](../../run-data-import.md)<br />
[Datenimportentitäten](../../data-import-entities.md)<br />
[Beispiel: Exportieren und Importieren einer Datenzuordnung](export-import-data-map.md)<br />
