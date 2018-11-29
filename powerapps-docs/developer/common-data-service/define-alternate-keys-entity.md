---
title: Arbeiten mit alternativen Schlüsseln (Common Data Service for Apps) | Microsoft Docs
description: 'Das Thema erläutert, wie Sie Alternativschlüssel für eine Entität erstellen. Sie können Alternativschlüssel programmgesteuert erstellen oder mithilfe der Anpassungstools.'
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
# <a name="work-with-alternate-keys"></a>Arbeiten mit Alternativschlüsseln

Alle Common Data Service for Apps-Datensätze haben eindeutige Bezeichner, die als GUIDs definiert sind. Diese sind der Primärschlüssel für jede Entität. Wenn Sie mit einem externen Datenspeicher integrieren müssen, können Sie möglicherweise eine Spalte zu externen Datenbanktabellen hinzufügen, sodass ein Verweis zum eindeutigen Bezeichner in CDS for Apps vorhanden ist. Dies ermöglicht einen lokalen Verweis für einen Link zu dem CDS for Apps-Datensatz. Manchmal können Sie jedoch die externe Datenbank nicht ändern. Mit Alternativschlüsseln können Sie jetzt ein Attribut in einer CDS for Apps-Entität definieren, um einem eindeutigen Bezeichner (oder einer eindeutigen Kombination von Spalten), der vom externen Datenspeicher verwendet wird, zu entsprechen. Sie können diesen Alternativschlüssel anstelle des Primärschlüssels verwenden, um einen Datensatz in CDS for Apps eindeutig zu identifizieren. Sie müssen in der Lage sein, zu definieren, welche Attribute eine eindeutige Identität für Ihre Datensätze darstellen. Nachdem Sie die Attribute ermittelt haben, die für die Entität eindeutig sind, können sie als Alternativschlüssel über die Anpassungs-Benutzeroberfläche oder im Code deklariert werden. Dieses Thema enthält Informationen zum Festlegen von Alternativschlüsseln im Datenmodell.  

<a name="BKMK_Declare"></a>

## <a name="create-alternate-keys"></a>Erstellen Sie Alternativschlüssel  

Sie können Alternativschlüssel programmgesteuert erstellen oder mithilfe der Anpassungstools. Weitere Informationen zur Verwendung der Anpassungstools finden Sie unter [Definieren von Alternativschlüsseln für den Verweis auf CRM-Datensätze](https://technet.microsoft.com/library/29e53691-0b18-4fde-a1d0-7490aa227898.aspx).  

Um Alternativschlüssel programmgesteuert zu definieren, müssen Sie zunächst ein Objekt des Typs <xref:Microsoft.Xrm.Sdk.Metadata.EntityKeyMetadata> erstellen (oder <xref href="Microsoft.Dynamics.CRM.EntityKeyMetadata?text=EntityKeyMetadata EntityType" />, wenn Sie mit Web-API arbeiten). Diese Klasse enthält die Schlüsselattribute. Sobald die Schlüsselattribute festgelegt sind, können Sie `CreateEntityKey` verwenden, um die Schlüssel für eine Entität erstellen. Diese Nachricht nimmt die gesamten `EntityKeyMetadata`-Werte entgegen und erstellt den Schlüssel.  

Sie sollten folgende Einschränkungen berücksichtigen, wenn Alternativschlüssel erstellt werden:  

- **Gültige Attribute in Schlüsseldefinitionen**  

   Nur Attribute der folgenden Typen können in den Alternativschlüsseldefinitionen hinzugefügt werden:  


  |      Attributtyp      |    Anzeigename     |
  |--------------------------|---------------------|
  | DecimalAttributeMetadata |   Dezimalzahl    |
  | IntegerAttributeMetadata |    Ganze Zahl     |
  | StringAttributeMetadata  | Einzelne Textzeile |


- **Gültige Schlüsselgröße**  

   Wenn ein Schlüssel erstellt wurde, überprüft das System, ob dieser Schlüssel von der Plattform unterstützt werden kann, u. a. auch, ob die Gesamtschlüsselgröße nicht gegen die SQL-basierten Indexeinschränkungen verstößt, zum Beispiel 900 Bytes pro Schlüssel und 16 Spalten pro Schlüssel. Wenn die Schlüsselgröße die Einschränkungen nicht erfüllt, wird eine Fehlermeldung angezeigt.  

- **Maximale Anzahl an Alternativschlüsseldefinitionen für eine Entität**  

   Es gibt ein Maximum von 5 Alternativschlüsseldefinitionen für eine Entität in einer CDS for Apps-Instanz.  

- **Unicode-Zeichen im Schlüsselwert**

  Wenn die Daten innerhalb eines Felds, das in einem Alternativschlüssel verwendet wird, eines der folgenden Zeichen enthält `<`,`>`,`*`,`%`,`&`,`:`,`\\` funktionieren Patarbeiten, und patch- oder upsert-Aktionen nicht.  Wenn Sie nur Eindeutigkeit benötigen, reicht dieser Ansatz aus, wenn Sie jedoch diese Schlüssel im Rahmen der Datenintegration benötigen, sollten Sie den Schlüssel besser in Feldern ohne Daten mit diesen Zeichen erstellen.

<a name="BKMK_crud"></a>   

## <a name="retrieve-and-delete-alternate-keys"></a>Abrufen und Löschen von Alternativschlüsseln  

Wenn Sie Alternativschlüssel abrufen oder löschen müssen, können Sie die Anpassungs-Benutzeroberfläche dazu verwenden, dies ohne Code zu schreiben zu erledigen. Dennoch bietet das SDK die folgenden beiden Nachrichten, um Alternativschlüssel programmgesteuert abzurufen und zu löschen.  

|Meldungsanforderungsklasse|Beschreibung|  
|---------------------------|-----------------|  
|<xref:Microsoft.Xrm.Sdk.Messages.RetrieveEntityKeyRequest>|Ruft den angegebenen Alternativschlüssel ab.|  
|<xref:Microsoft.Xrm.Sdk.Messages.DeleteEntityKeyRequest>|Löscht den angegebenen Alternativschlüssel.|  

Um alle Schlüssel für eine Entität abzurufen, verwenden Sie die neue <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.Keys>-Eigenschaft der `EntityMetadata` (<xref href="Microsoft.Dynamics.CRM.EntityMetadata?text=EntityMetadata EntityType" /> oder <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata>-Klasse). Ruft ein Array von Schlüsseln für eine Entität ab.  

<a name="BKMK_index"></a>   

## <a name="monitor-index-creation-for-alternate-keys"></a>Überwachen der Indexerstellung für Alternativschlüssel  

Alternativschlüssel nutzen Datenbankindizes um eine Eindeutigkeit zu gewährleisten und die Suchenleistung und zu optimieren. Wenn es viele vorhandener Datensätze in einer Tabelle gibt, dann kann die Indexerstellung lange dauern. Sie können das Reaktionsvermögen der Anpassungs-Benutzeroberfläche und den Lösungsimporte optimieren, indem Sie die Indexerstellung als Hintergrundprozess ausführen. Die `EntityKeyMetadata.AsyncJob`-Eigenschaft (<xref href="Microsoft.Dynamics.CRM.EntityKeyMetadata?text=EntityKeyMetadata EntityType" /> oder <xref:Microsoft.Xrm.Sdk.Metadata.EntityKeyMetadata>) bezieht sich auf den asynchronen Auftrag, der die Indexerstellung vornimmt. Die Eigenschaft `EntityKeyMetadata.EntityKeyIndexStatus` gibt den Status des Schlüssels als seinen Indexerstellungs-Auftragsstatus an. Der Status kann einer der folgenden sein:  

- Ausstehend  
- In Bearbeitung  
- Aktiv  
- Fehler  

Wenn ein Alternativschlüssel mithilfe der API erstellt wird, können Sie, wenn bei der Indexerstellung ein Fehler auftritt, Details über die Ursache des Fehlers einsehen, die Probleme beheben und die Schlüsselanforderung erneut aktivieren mithilfe der `ReactivateEntityKey` (<xref href="Microsoft.Dynamics.CRM.ReactivateEntityKey?text=ReactivateEntityKey Action" /> oder <xref:Microsoft.Xrm.Sdk.Messages.ReactivateEntityKeyRequest>-Meldung).  

Wenn der Alternativschlüssel gelöscht wird, während ein Indexerstellungsauftrag noch ausstehend oder in Verarbeitung ist, wird der Auftrag abgebrochen und der Index gelöscht.  

### <a name="see-also"></a>Siehe auch  
 [Verwenden von Alternativschlüsseln](use-alternate-key-create-record.md)<br />
 [Synchronisieren von Daten mit externen Systemen mithilfe der Änderungsnachverfolgung](use-change-tracking-synchronize-data-external-systems.md)<br />
 [Einen Datensatz mit Upsert einfügen oder aktualisieren](use-upsert-insert-update-record.md) [Definieren von Alternativschlüsseln für den Verweis auf Datensätze](../../maker/common-data-service/define-alternate-keys-reference-records.md)