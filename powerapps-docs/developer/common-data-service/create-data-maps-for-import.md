---
title: Datenzuordnungen für den Import erstellen (Common Data Service für Apps) | Microsoft Docs
description: Datenzuordnungen sind für Datenimport erforderlich und enthalten Zuordnungen zwischen den Daten in der Quelldatei und die entsprechenden Entitätsattributen.
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
# <a name="create-data-maps-for-import"></a>Erstellen von Datenzuordnungen für den Import

Um Daten in den Common Data Service for Apps zu importieren, müssen Sie die entsprechenden Datenzuordnungen bereitstellen.  
  
 Sie können Beispiele der Datenzuordnungen aus [Microsoft-Downloads: DataImportMaps.zip](http://download.microsoft.com/download/D/5/F/D5F73E15-439B-4EBC-BFFB-C6837B146C76/DataImportMaps.zip) herunterladen.
  
 Mit Hilfe von Datenzuordnungen können Sie die in der Quelldatei enthaltenen Daten auf die Entitäts-Attribute des CDS for Apps abbilden. Sie müssen jede Spalte in der Quelldatei einem entsprechenden Attribut zuordnen. Die Daten in den nicht zugeordneten Spalten werden während des Vorgangs des Datenimports nicht importiert.  
  
 Die Datenzuordnung wird durch die Importzuordnungsentität (Datenzuordnung) dargestellt. Sie können eine neue Zuordnung erstellen, indem Sie die <xref:Microsoft.Xrm.Sdk.Messages.CreateRequest>-Meldung verwenden, oder eine bestehende Zuordnung aktualisieren, indem Sie <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Update*>-Methode anwenden. Methode. Die Zuordnung besitzt einen eindeutigen Namen, der im Attribut `ImportMap.Name` enthalten ist. Sie können den Namen der Importquelle angeben, für die diese Datenzuordnung erstellt wird, indem Sie das Attribut `ImportMap.Source` verwenden.  
  
<a name="BKMK_Column"></a>   
## <a name="column-list-value-and-lookup-mappings"></a>Spalte, Listenwert und Suchzuordnungen  
 Um eine Spalte, einen Listenwert oder einen Suchwert in der Quelldatei auf ein CDS for Apps-Attribut abzubilden, verwenden Sie die folgenden Zuordnungen:  
  
 **Spaltenzuordnung**  
  
 Ordnet eine Spalte in einer Quelldatei einem CDS for Apps-Entitätsattribut zu. Für Spaltenzuordnungen können Sie die Spaltenzuordnungsentität (`ColumnMapping`) verwenden. Sie können 1:1-Beziehungen (eins-zu-eins) oder 1:n-Beziehungen (eins-zu-vielen) zwischen Quell- und Zielattributen verwenden. Beispielsweise können Sie die Adressinformationen einer Firma sowohl der Rechnungs- als auch der Lieferadresse in einer Bestellung zuordnen.  
  
 **Listenwertzuordnung**  
  
 Ordnet einen Listenwert in einer Quelldatei einem CDS for Apps-Attribut des Typs <xref:Microsoft.Xrm.Sdk.OptionSetValue> zu. Bei der Zuordnung von Listenwerten können Sie die Auswahllistenzuordnungsentität (`PicklistMapping`) verwenden.  
  
 Ist ein in der Quelldateispalte angegebener Wert einen Listenwert wie OptionSetValue, Status, Zustand und Boolesche, müssen Sie neben der Spaltenzuordnung auch eine Listenwertzuordnung. Ordnen Sie beispielsweise die Listenwerte "Rechnung" sowie "Versand" in der Quelldatei den Rechnungs- und Versandwerten des Typs <xref:Microsoft.Xrm.Sdk.OptionSetValue> zu.  
  
 **Suchzuordnung**  
  
 Ordnet einen Suchwert in einer Quelldatei einem CDS for Apps-Attribut des Typs <xref:Microsoft.Xrm.Sdk.EntityReference> zu. Für Suchzuordnungen können Sie die Suchzuordnungsentität (`LookupMapping`) verwenden.  
  
 Wenn der in der Quelldatei angegebene Wert auf eine Entität verweist, müssen Sie für diesen Wert eine Suchzuordnung bereitstellen. Verwenden Sie das `LookupMapping.LookupSourceCode` Attribut , um anzugeben, ob die referenzierte Entität in der Quelldatei oder innerhalb von CDS for Apps gesucht werden soll. Wenn Sie Typen mit früherer Bindung verwenden, können Sie die `LookupSourceType`-Enumeration verwenden, um die Statuswerte festzulegen. Um in der Quelldatei zu suchen, verwenden Sie den `LookupSourceType.Source`-Wert. Um innerhalb von CDS for Apps zu suchen, verwenden Sie den `LookupSourceType.System`-Wert. Eine Liste der LookupSourceCode-Werte finden Sie in den Werten der Auswahlliste für diese Entität. Zum Anzeigen der Entitätsmetadaten für Ihre Organisation installieren Sie die Metadatenbrowserlösung, die in [Durchsuchen der Metadaten für Ihre Organisation](/dynamics365/customer-engagement/developer/browse-your-metadata) beschrieben ist. Sie können die Referenzdokumentation für Entitäten auch in der [Entitätsreferenz](reference/about-entity-reference.md) durchsuchen.  Sie können mehrere Suchzuordnungen bereitstellen. Der asynchrone Transformationsauftrag verarbeitet alle verfügbaren Zuordnungen. Er findet die Datensätze, auf die verwiesen wird, und aktualisiert die Analysetabelle mit den eindeutigen Kennungen der Datensätze. Weitere Informationen finden Sie unter [Datenimport ausführen](run-data-import.md).  
  
<a name="BKMK_Owner"></a>   
## <a name="owner-mapping"></a>Besitzerzuordnung  
 Verwenden Sie die Besitzerzuordnung, um einen in der Quelldatei angegebenen Benutzer einem Benutzer in CDS for Apps zuzuordnen. Für Protokollinformation können Sie den CDS for Apps-Benutzeranmeldenamen verwenden. Für Besitzerzuordnungen können Sie die Besitzerzuordnungsentität (`OwnerMapping`) verwenden.  
  
<a name="BKMK_Notes"></a>   
## <a name="notes-and-attachments"></a>Notizen und Anlagen  
 Zuordnung für Notizen und Anlagen werden im Vergleich zu anderen Entitäten jedoch unterschiedlich behandelt. Notizen und Anlagen werden verwendet, um zusätzliche Informationen an einen Datensatz in CDS for Apps anzufügen. Notizen werden Text als gespeichert, Anlagen dagegen als Dateien in der CDS for Apps- Datenbank.  
  
 Um eine Notiz in CDS for Apps zu erstellen, setzen Sie den Wert des Attribut `Annotation.IsDocument` in der Anmerkung (Notiz)-Entität auf `false`. Um eine Anlage zu erstellen, Setzen Sie `IsDocument` auf `true`.  
  
 Verwenden Sie die folgenden Einstellungen für die Zuordnung von Notizen und Anlagen:  
  
- Setzen Sie das Attribut `ColumnMapping.SourceAttributeName` auf den Wert "`true`" oder "`false`": Der Wert "`true`" zeigt eine Anlage an. Der Wert "`false`" zeigt eine Notiz an.  
  
- Setzen Sie das Attribut `ColumnMapping.TargetAttributeName` auf den Wert `IsDocument`.  
  
- Setzen Sie das Attribut `ColumnMapping.ProcessCode` auf den `ImportProcessCode.Internal`-Wert der `ImportProcessCode`-Enumeration, wenn Sie Typen mit früher Bindung verwenden. Eine Liste der ProcessCode-Werte finden Sie in den Werten der Auswahlliste für diese Entität.  
  
  Wenn die Quelldaten eine Notiz darstellen, ordnen Sie auf den Text der Notiz dem `Annotation.NoteText`-Attribut zu. Wenn Sie mit Salesforce-Dateien arbeiten, werden diese normalerweise mit eindeutigen Kennnummern auf der Festplatte gespeichert. Zum eine Anlage zu importieren, müssen Sie eine in der Quelldatei enthaltene Dateikennnummer dem Attribut `Annotation.DocumentBody` zuordnen. Das Attribut `DocumentBody` speichert den Inhalt der Anlage.  
  
  Der Auftrag zum asynchronen Import überprüft die Zuordnungen, deren Quellattributnamen auf die Werte "`true`" und "`false`" gesetzt wurden, auf vorhandene Notizen und Anlagen. Wird eine Anlagenzuordnung gefunden, werden die angegebenen Dateien auf der Festplatte gesucht und der Dateiinhalt als Anlage in CDS for Apps hochgeladen. Wenn eine Datei nicht gefunden wird, wird eine Fehlermeldung zurückgegeben.  
  
  Wenn Sie die Zuordnung für eine Anmerkungsentität (Notiz) nicht bereitstellen, generiert der Importauftrag eine Standardzuordnung für die Notiz.  
  
> [!NOTE]
> Die maximale Größe für Dateien, die hochgeladen werden können, wird durch die **Organization.MaxUploadFileSize**-Eigenschaft bestimmt. Diese Eigenschaft wird in der CDS for Apps-Anwendung auf der Registerkarte **E-Mail** in den **Systemeinstellungen** festgelegt. Mit dieser Einstellung wird die Größe von Dateien begrenzt, die an E-Mail-Nachrichten, Notizen und Webressourcen angefügt werden können. Die Standardeinstellung ist 5 MB.  Allerdings darf die Dateigröße einer Anlage die maximale Größe für HTTP-Anforderung nicht überschreiten (Standard sind 16 MB). Damit die Änderung wirksam wird, setzen Sie die Internet-Informationsdienste zurück. Klicken Sie hierzu auf **Start**, klicken Sie auf **Ausführen**, geben Sie `iisreset` ein, und klicken Sie dann auf **OK**.  
  
<a name="BKMK_ImportExport"></a>   
## <a name="import-and-export-data-maps"></a>Import und Export von Datenzuordnungen  
 Sie können eine vorhandene Datenzuordnung in eine XML-Datei exportieren und XML-Datenzuordnungen in CDS for Apps importieren. Wenn Sie eine Datenzuordnung aus CDS for Apps exportieren möchten, verwenden Sie die <xref:Microsoft.Crm.Sdk.Messages.ExportMappingsImportMapRequest>-Nachricht . Um XML-Datenzuordnungen zu importieren und in CDS for Apps eine Datenzuordnung zu erstellen, können Sie die Nachricht <xref:Microsoft.Crm.Sdk.Messages.ImportMappingsImportMapRequest> verwenden.  
  
### <a name="see-also"></a>Siehe auch

[Importieren von Daten](import-data.md)<br />
[Vorbereiten einer Quelldatei für den Import](prepare-source-files-import.md)<br />
[Hinzufügen von Transformationszuordnungen für den Import](add-transformation-mappings-import.md)<br />
[Konfiguration des Datenimports](configure-data-import.md)<br />
[Ausführen des Datenimports](run-data-import.md)<br />
[Datenimportentitäten](data-import-entities.md)<br />
[Beispiel: Exportieren und Importieren einer Datenzuordnung](org-service/samples/export-import-data-map.md)<br />
[Beispiel: Importieren von Daten mithilfe der komplexen Datenzuordnung](org-service/samples/import-data-complex-data-map.md)<br />