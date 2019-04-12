---
title: Vorbereiten einer Quelldatei für den Import (Common Data Service) | Microsoft Docs
description: 'Datenimport unterstützt Quellendateien, die als durch Trennzeichen getrennten Datei (CSV-Datei), Textdateien oder 2003 (XML-Dateien) Textdateien formatiert sind.'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: mayadumesh
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="prepare-source-files-for-import"></a>Vorbereiten einer Quelldatei für den Import

Bevor Sie Daten in Common Data Service importieren können, müssen Sie die Quelldatendateien erstellen.  
  
Die Datenquellendateien, die Sie in einem Import verwenden, müssen als durch Trennzeichen getrennten Datei (CSV-Datei), Textdateien oder 2003 (XML-Dateien) Textdateien formatiert werden. Die Verwendung von Quelldateien ermöglicht es, Daten zwischen Datenbanksystemen, die unterschiedliche Formate verwenden, in Common Data Service zu übertragen.  
  
Eine Quelldatei enthält unter Umständen Daten für einen Entitätstyp oder mehrere Entitätstypen wie Firmen und Kontakte. Für mehrere Quelldateien, die Daten mehrerer Entitätsdaten enthalten, müssen Sie eine Zuordnung verfügbar machen, die das Tag `<EntitiesPerFile>` enthält. Legen Sie den Wert dieses Tags auf "Mehrere", um anzuzeigen, dass es in der Quelldatei mehr als einen Entitätstyp gibt. Fügen Sie das `Dedupe = “Eliminate”` Attribut `<EntityMap>` dem Tag hinzu. Dies gewährleistet, dass für den Fall, dass die Datei für den den Entitätstyp doppelte Zeilen enthält, nur eine einzelne Linie verwendet wir, um Suchfehler zu minimieren.  
  
Sie können ein Beispiel einer Datenzuordnung mit mehreren von Entitätstypen herunterladen. [Microsoft-Downloads: DataImportMaps.zip](http://download.microsoft.com/download/D/5/F/D5F73E15-439B-4EBC-BFFB-C6837B146C76/DataImportMaps.zip) Sehen Sie sich die `MapForSalesForceContactAccount.xml`-Datei an.  
  
 Die Feldwerte in der Quelldatei können durch Kommas, Tabulatoren oder andere Zeichen, die in den `ImportFile.FieldDelimiterCode`, Attributen definiert sind, getrennt werden.  
  
> [!NOTE]
>  Verwenden Sie keine nicht druckbaren Zeichen, **null** (\0) oder break (\b) als Trennzeichen für Feldwerte.  
  
 Die erste Zeile der Quelldatei sollte keine Spaltenüberschriften enthalten. Wenn Sie keine Spaltenbeschriftungen verwenden, nehmen Sie das `ImportFile.IsFirstRowHeader` Attribut, um anzugeben, dass die erste Zeile tatsächliche Daten enthält. In diesem Fall werden automatisch standardmäßige Spaltenüberschriften mit den Namen, Col1, Col2 etc. erstellt.  

### <a name="see-also"></a>Siehe auch

[Importieren von Daten](import-data.md)<br />
[Erstellen von Datenzuordnungen für den Import](create-data-maps-for-import.md)<br />
[Hinzufügen von Transformationszuordnungen für den Import](add-transformation-mappings-import.md)<br />
[Konfiguration des Datenimports](configure-data-import.md)<br />
[Ausführen des Datenimports](run-data-import.md)<br />
[Datenimportentitäten](data-import-entities.md)<br />
[Beispiel: Exportieren und Importieren einer Datenzuordnung](org-service/samples/export-import-data-map.md)<br />
[Beispiel: Importieren von Daten mithilfe der komplexen Datenzuordnung](org-service/samples/import-data-complex-data-map.md)<br />