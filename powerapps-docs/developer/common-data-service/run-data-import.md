---
title: Datenimport ausführen (Common Data Service) | Microsoft Docs
description: 'Dateneinfuhr wird direkt auf dem Dynamics 365 Server ausgeführt und erfordert drei asynchrone Aufträge für das Analysieren, zuordnungsgeführte Transformation und Hochladen.'
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
# <a name="run-data-import"></a>Ausführen des Datenimports

Der Datenimport wird direkt auf dem Common Data Service-Server ausgeführt. Richten Sie zum Ausführen des Datenimports asynchrone Aufträge ein, die im Hintergrund ausgeführt werden und Folgendes in der angegebenen Reihenfolge ausführen:  
  
- Analysieren Sie Quelldaten, die in der Importdatei enthalten sind.  
  
- Formen Sie analysierte Daten mithilfe der Datenzuordnung um.  
  
- Laden Sie transformierte Daten in den Common Data Service hoch.  
  
  Alle Common Data Service-Benutzer mit entsprechenden Rechten können den Datenimport ausführen.  
  
<a name="parse"></a>   
## <a name="parse-source-data"></a>Analysieren von Quelldaten  
 Das Analysieren von Quelldaten enthält das Analysieren aller Importdateien mit einem bestimmten Import (Datenimport).  
  
 Analysierte Daten werden in den temporären Analysetabellen gespeichert, die für jede importierte Datei erstellt werden. Der Name der Analysetabelle wird im `ImportFile.ParsedTableName`-Attribut gespeichert. Die Spaltenüberschriften der Quelldatei werden im Attribut `ImportFile.HeaderRow` angegeben. Wenn die Quelldatei keine erste Zeile mit Spaltenüberschriften enthält, gibt dieses Attribut die vom System generierten Standardspaltenüberschriften an.  
  
 Speichern Sie analysierte Daten in der Analysetabelle mithilfe der <xref:Microsoft.Crm.Sdk.Messages.ParseImportRequest>-Nachricht. Rufen Sie Daten aus der Analysetabelle ab, indem Sie die Nachrichten <xref:Microsoft.Crm.Sdk.Messages.GetDistinctValuesImportFileRequest> und <xref:Microsoft.Crm.Sdk.Messages.RetrieveParsedDataImportFileRequest> verwenden.  
  
 In der folgenden Tabelle werden die Nachrichten aufgelistet, die Sie verwenden können, um die Importdateien zu analysieren die analysierten Daten aus den Analysetabellen abzurufen.  
  
|Meldung|Beschreibung|  
|-------------|-----------------|  
|<xref:Microsoft.Crm.Sdk.Messages.ParseImportRequest>|Gibt einen asynchronen Auftrag ein, der alle Importdateien analysiert, die dem angegebenen Import (datenimport) zugeordnet sind. Übergeb Sie die ID des zugehörigen Imports (Datenimport) in die Eigenschaft <xref:Microsoft.Crm.Sdk.Messages.ParseImportRequest.ImportId> dieser Anforderung. Die ID des asynchronen Auftrags, der im Hintergrund ausgeführt wird und das Analysieren von Daten durchführt, die in der <xref:Microsoft.Crm.Sdk.Messages.ParseImportResponse.AsyncOperationId>-Eigenschaft der Nachrichtenantwort zurückgegeben werden.|  
|<xref:Microsoft.Crm.Sdk.Messages.GetDistinctValuesImportFileRequest>|Gibt eindeutige Werte für eine Spalte in der Quelldatei zurück, die Listenwerte enthält. Übergeben Sie die ID der zugehörigen Importdatei in die Eigenschaft <xref:Microsoft.Crm.Sdk.Messages.GetHeaderColumnsImportFileRequest.ImportFileId> dieser Anforderung. Die eindeutigen Werte werden in einem Zeichenfolgenarray in der <xref:Microsoft.Crm.Sdk.Messages.GetDistinctValuesImportFileResponse.Values>-Eigenschaft der Nachrichtenantwort zurückgegeben. Verwenden Sie diese Meldung nur, nachdem Sie eine Analysetabelle erstellt haben, indem Sie die <xref:Microsoft.Crm.Sdk.Messages.ParseImportRequest>-Nachricht verwenden. **Wichtig:** Verwenden Sie diese Meldung nicht, nachdem Sie die Nachricht <xref:Microsoft.Crm.Sdk.Messages.ImportRecordsImportRequest> verwenden. Sie können nicht auf die Analysetabelle zugreifen, nachdem der Importauftrag, der durch die <xref:Microsoft.Crm.Sdk.Messages.ImportRecordsImportRequest>-Nachricht gesendet wurde, abgeschlossen wurde.|  
|<xref:Microsoft.Crm.Sdk.Messages.RetrieveParsedDataImportFileRequest>|Ruft die Daten aus der Analysetabelle ab. Übergeben Sie die ID der zugehörigen Importdatei in die Eigenschaft <xref:Microsoft.Crm.Sdk.Messages.RetrieveParsedDataImportFileRequest.ImportFileId> dieser Anforderung. Die analysierten Daten werden in einem zweidimensionalen Zeichenfolgenarray in der <xref:Microsoft.Crm.Sdk.Messages.RetrieveParsedDataImportFileResponse.Values>-Eigenschaft der Nachrichtenantwort zurückgegeben. Die Daten werden mit derselben Spaltenreihenfolge wie die Spaltenreihenfolge in der Quelldatei zurückgegeben. Verwenden Sie diese Meldung nur, nachdem Sie eine Analysetabelle erstellt haben, indem Sie die <xref:Microsoft.Crm.Sdk.Messages.ParseImportRequest>-Nachricht verwenden. **Wichtig:** Verwenden Sie diese Meldung nicht, nachdem Sie die Nachricht <xref:Microsoft.Crm.Sdk.Messages.ImportRecordsImportRequest> verwenden. Sie können nicht auf die Analysetabelle zugreifen, nachdem der Importauftrag, der durch die `ImportRecordsMessage`-Nachricht gesendet wurde, abgeschlossen wurde.|  
  
<a name="transform"></a>   
## <a name="transform-parsed-data"></a>Transformieren analysierter Daten  
 Während der Transformation ändern Sie analysierte Daten, indem Sie alle verfügbaren Datenzuordnungen und Transformationen übernehmen, die einem bestimmten Import (Datenimport) in die Daten zugeordnet sind.  
  
 Verwenden Sie die <xref:Microsoft.Crm.Sdk.Messages.TransformImportRequest>-Nachricht, um einen asynchronen Auftrag zu senden und die analysierten Daten zu transformieren. Übergeben Sie einen eindeutigen Bezeichner des zugeordneten Imports (Datenimport) im `Import.ImportId`-Attribut der Anforderung. Ein eindeutiger Bezeichner des asynchronen Auftrags, der im Hintergrund ausgeführt wird und die Transformation durchführt, wird in der <xref:Microsoft.Crm.Sdk.Messages.TransformImportResponse.AsyncOperationId>-Eigenschaft der Nachrichtenantwort zurückgegeben.  
  
<a name="upload"></a>   
## <a name="upload-transformed-data-to-the-target-server"></a>Hochladen transformierter Daten auf den Zielserver  
 Nachdem Sie die Transformation erfolgreich abgeschlossen haben, können die Daten auf den Common Data Service-Server hochgeladen werden.  
  
 Verwenden Sie die Message <xref:Microsoft.Crm.Sdk.Messages.ImportRecordsImportRequest>, um einen asynchronen Auftrag zu senden und die transformierten Daten in Common Data Service hochzuladen. Der eindeutige Bezeichner des zugeordneten Imports (Datenimport) muss in der <xref:Microsoft.Crm.Sdk.Messages.ImportRecordsImportRequest.ImportId>-Eigenschaft der Anforderung angegeben werden. Ein eindeutiger Bezeichner des asynchronen Auftrags, der im Hintergrund ausgeführt wird und die Daten in Common Data Service hochlädt, wird in der <xref:Microsoft.Crm.Sdk.Messages.ImportRecordsImportResponse.AsyncOperationId>-Eigenschaft der Message-Antwort zurückgegeben. Alle Importdateien, die dem angegebenen Import (Datenimport) zugeordnet sind, werden importiert.  
  
 Jeder Importauftrag besitzt eine eigene Sequenznummer, die im `ImportSequenceNumber`-Attribut der erstellten Datensätze gespeichert ist. Das `Organization.CurrentImportSequenceNumber`-Attribut enthält eine eindeutige Sequenznummer des letzten Importauftrags, der im System lief. Sie können diese eindeutigen Sequenznummern verwenden, um Datensätze nachzuverfolgen, die zu einem Importauftrag gehören.  
  
<a name="log"></a>   
## <a name="log-failures"></a>Protokollfehler  
 Ein Fehler beim Importieren eines Datensatzes kann während der Analyse, der Transformation oder des Hochladens von Daten auftreten. Die Fehlerursachen und andere ausführliche Informationen zu den nicht importierten Datensätzen werden in der Importprotokollentität (ImportLog) aufgezeichnet.  
  
 Um festzustellen, wie viele Datensätze nicht importiert werden konnten, rufen Sie das `ImportFile.FailureCount`-Attribut des Datensatzes ab. Um zu überprüfen, wie viele Datensätze beim Importieren teilweise fehlgeschlagen sind, rufen Sie das `ImportData.HasError`-Attribut ab. Wenn das `HasError`-Attribut `true` ist, ist ein Teilfehler aufgetreten, wenn es `false` ist, wurde der Datensatz erfolgreich importiert.  
  
<a name="import_audit"></a>   
## <a name="import-auditing-data"></a>Importieren von Überwachungsdaten  
 Die Common Data Service-Entitäten haben vier Standardattribute, die verwendet werden, um nachzuverfolgen, an welchem Datum und zu welcher Uhrzeit ein Datensatz erstellt und zuletzt geändert wurde. Außerdem wird die Person nachverfolgt, die den Datensatz erstellt und geändert hat:  
  
 Das Attribut `createdon` gibt das Datum und die Uhrzeit an, an dem bzw. zu der der Datensatz erstellt wurde. Um Daten in das `createdon`-Attribut zu importieren, ordnen Sie die Quellspalte, die diese Daten enthält, dem `overriddencreatedon`-Attribut zu. Während des Imports wird das `createdon`-Attribut des Datensatzes mit dem Wert aktualisiert, der dem `overriddencreatedon`-Attribut zugeordnet ist, und das `overriddencreatedon`-Attribut wird auf das Datum und die Uhrzeit festgelegt, an dem bzw. zu der die Daten importiert wurden. Wenn dem `overriddencreatedon`-Attribut kein Quellcode zugeordnet ist, wird das `createdon`-Attribut auf das Datum und die Uhrzeit festgelegt, an dem bzw. zu der die Daten importiert werden. Das `overriddencreatedon`-Attribut ist auf keinen Wert festgelegt.  
  
> [!NOTE]
>  Wenn Sie den Wert im `createdon`-Attribut beim Importieren überschreiben möchten, benötigen Sie das `prvOverrideCreatedOnCreatedBy`-Recht. Beachten Sie, das der Name des Rechts besagt, dass Sie das `createdby`-Attribut auch während des Imports überschreiben können. Allerdings wird diese Funktion derzeit nicht unterstützt.  
  
 Sie können keine Daten in die Attribute `modifiedon`, `createdby` und `modifiedby` importieren. Wenn Sie Information dazu speichern müssen, wer den Datensatz erstellt und geändert hat und wann die Daten geändert wurden, können Sie in Common Data Service benutzerdefinierte Attribute erstellen und die Quellspalten den neuen benutzerdefinierten Attributen zuordnen.  
  
### <a name="see-also"></a>Siehe auch

[Importieren von Daten](import-data.md)<br />
[Vorbereiten einer Quelldatei für den Import](prepare-source-files-import.md)<br />
[Erstellen von Datenzuordnungen für den Import](create-data-maps-for-import.md)<br />
[Hinzufügen von Transformationszuordnungen für den Import](add-transformation-mappings-import.md)<br />
[Konfiguration des Datenimports](configure-data-import.md)<br />
[Datenimportentitäten](data-import-entities.md)<br />
[Beispiel: Exportieren und Importieren einer Datenzuordnung](org-service/samples/export-import-data-map.md)<br />
[Beispiel: Importieren von Daten mithilfe der komplexen Datenzuordnung](org-service/samples/import-data-complex-data-map.md)<br />
[Blogbeitrag: Wie Anhänge automatisch importiert werden](http://blogs.msdn.com/b/crm/archive/2012/08/06/how-to-import-attachments-programmatically.aspx) 