---
title: Datenimport konfigurieren (Common Data Service für Apps) | Microsoft Docs
description: 'Die Konfigurationsinformationen, die zum Importieren von Daten erforderlich sind, sind in der Datenimportentität und der Importquelldateientität enthalten.'
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
# <a name="configure-data-import"></a>Konfiguration des Datenimports

<!-- 
Was Mike Carter's

https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/configure-data-import 

Child topic of 
powerapps-docs/developer/common-data-service/import-data.md
-->

Die Konfigurationsinformationen, die zum Importieren von Daten erforderlich sind, sind in der Datenimport (`Import`)-Entität und der Importquelldatei (`ImportFile`)-Entität enthalten.  
  
 Gehen Sie zum Konfigurieren des Datenimports:  
  
- Verwenden Sie das Attribut `Import.ModeCode`, um anzugeben, ob Daten während des Imports erstellt oder aktualisiert werden sollen. Bei Nutzung von Typen mit früher Bindung können Sie die `ImportModeCode`-Enumeration verwenden. Eine Liste der ModeCode-Werte finden Sie in den Werten der Auswahlliste für diese Entität. Zum Anzeigen der Entitätsmetadaten für Ihre Organisation installieren Sie die Metadatenbrowserlösung, die in [Durchsuchen der Metadaten für Ihre Organisation](/dynamics365/customer-engagement/developer/browse-your-metadata) beschrieben ist. Sie können die Referenzdokumentation für Entitäten auch in der [Entitätsreferenz](/dynamics365/customer-engagement/developer/about-entity-reference) durchsuchen.  
  
- Verwenden Sie das Attribut `ImportFile.FileTypeCode`, um den Typ der Importdatei festzulegen. Bei Nutzung von Typen mit früher Bindung können Sie die `ImportFileType`-Enumeration verwenden. Eine Liste der FileTypeCode-Werte finden Sie in den Werten der Auswahlliste für diese Entität.  
  
- Verwenden Sie das `ImportFile.DataDelimiterCode`-Attribut, um das aus einem Zeichen bestehende Datentrennzeichen in der Importdatei anzugeben. Bei Nutzung von Typen mit früher Bindung können Sie die `ImportDataDelimiter`-Enumeration verwenden. Eine Liste der ImportDataDelimiter-Werte finden Sie in den Werten der Auswahlliste für diese Entität.  
  
- Verwenden Sie das `ImportFile.FieldDelimiterCode`-Attribut, um das aus einem Zeichen bestehende Feldtrennzeichen in der Importdatei anzugeben. Bei Nutzung von Typen mit früher Bindung können Sie die `ImportFieldDelimiter`-Enumeration verwenden. Eine Liste der FieldDelimiterCode-Werte finden Sie in den Werten der Auswahlliste für diese Entität.  
  
- Setzen Sie `ImportFile.IsFirstRowHeader` auf `true`, um anzugeben, dass die erste Zeile in der Quelldatei Spaltenüberschriften enthält, oder auf  `false`, um anzugeben, dass die erste Zeile tatsächliche Daten enthält. Bei `false` werden Standard-Spaltenüberschriften generiert.  
  
- Setzen Sie `ImportFile.ImportId` auf die ID des Imports (Datenimport), mit dem die Importdatei verbunden ist.  
  
- Setzen Sie `ImportFile.ImportMapId` auf die ID der zugehörigen Importzuordnung (Datenzuordnung).  
  
- Setzen Sie `ImportFile.EnableDuplicateDetection` auf `true`, um die Duplikaterkennung während des Datenimports zu aktivieren.  
  
- Lesen Sie den Inhalt der Quelldatei in den `ImportFile.Content` ein.  
  
> [!IMPORTANT]
>  Es ist nicht empfohlen, Datensätze durch den programmgesteuerten Import von Daten zu aktualisieren. Verwenden Sie für die Aktualisierung die Datenexport- und Importfunktionen der CDS for Apps-Webanwendung. Verwenden Sie **Exportieren zu Excel**, um Datensätze in eine XML-Spreadsheet 2003 (.xml) Datei zu exportieren. Dies ist der einzige gültige Quelldateityp für den Updatemodus. Der Rückimport der Daten aus der XML Spreadsheet 2003 (.xml)-Datei garantiert die Datenintegrität in CDs for Apps. Verwenden Sie zum Import aktualisierter Daten den CDS for Apps-Datenimport-Assistenten. Weitere Informationen zum Datenimport-Assistenten finden Sie in der Hilfe zu CDs for Apps.  
 
### <a name="see-also"></a>Siehe auch

[Importieren von Daten](import-data.md)<br />
[Blogbeitrag: Wie Anhänge automatisch importiert werden](http://blogs.msdn.com/b/crm/archive/2012/08/06/how-to-import-attachments-programmatically.aspx)<br />
[Vorbereiten einer Quelldatei für den Import](prepare-source-files-import.md)<br />
[Erstellen von Datenzuordnungen für den Import](create-data-maps-for-import.md)<br />
[Hinzufügen von Transformationszuordnungen für den Import](add-transformation-mappings-import.md)<br />
[Ausführen des Datenimports](run-data-import.md)<br />
[Datenimportentitäten](data-import-entities.md)<br />
[Beispiel: Exportieren und Importieren einer Datenzuordnung](org-service/samples/export-import-data-map.md)<br />
[Beispiel: Importieren von Daten mithilfe der komplexen Datenzuordnung](org-service/samples/import-data-complex-data-map.md)<br />