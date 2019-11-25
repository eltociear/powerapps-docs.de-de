---
title: Daten importieren (Common Data Service) | Microsoft-Dokumentation
description: Wenn Sie Daten in Common Data Service importieren möchten, können Sie die *Datenimport*-Funktion verwenden. Mithilfe von Datenimport können Sie Daten aus verschiedenen CRM-Systemen und Datenquellen in Common Data Service hochladen
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
ms.openlocfilehash: 562072c6d63b0abfeaa6c9f44f9cccfc5fdc960c
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748281"
---
# <a name="import-data"></a>Daten importieren

<!--
Was Mike Carter


https://docs.microsoft.com/dynamics365/customer-engagement/developer/import-data



This should be the generic high-level content to support either web api or org service

Should there be a separate topic for organization service and Web API?
All these functions & actions exist:

RetrieveParsedDataImportFile Function
https://docs.microsoft.com/dynamics365/customer-engagement/web-api/retrieveparseddataimportfile?view=dynamics-ce-odata-9
GetDistinctValuesImportFile Function
https://docs.microsoft.com/dynamics365/customer-engagement/web-api/getdistinctvaluesimportfile?view=dynamics-ce-odata-9
ParseImport Function
https://docs.microsoft.com/dynamics365/customer-engagement/web-api/parseimport?view=dynamics-ce-odata-9
TransformImport Action
https://docs.microsoft.com/dynamics365/customer-engagement/web-api/transformimport?view=dynamics-ce-odata-9
ImportRecordsImport Action
https://docs.microsoft.com/dynamics365/customer-engagement/web-api/importrecordsimport?view=dynamics-ce-odata-9
ExportMappingsImportMap Action
https://docs.microsoft.com/dynamics365/customer-engagement/web-api/exportmappingsimportmap?view=dynamics-ce-odata-9
ImportMappingsImportMap Action
https://docs.microsoft.com/dynamics365/customer-engagement/web-api/importmappingsimportmap?view=dynamics-ce-odata-9

Or should the core general content simply include both?

-->
Wenn Sie Daten in Common Data Service importieren möchten, können Sie die *Datenimport*-Funktion verwenden. Mithilfe von Datenimport können Sie Daten aus verschiedenen CRM-Systemen und Datenquellen in Common Data Service hochladen. Sie können Daten in Standard- und benutzerdefinierte Attribute der meisten Geschäfts- und benutzerdefinierten Entitäten importieren. Sie können auch zugehörige Daten, wie etwa Notizen und Anlagen, hinzufügen.  
  
Common Data Service beinhaltet ein Webanwendungstool mit dem Namen Datenimport-Assistent. Sie können dieses Tool verwenden, um Datensätze aus einer oder mehr Dateien mit durch Komma getrennten Werten (.csv), XML-Kalkulationstabellen 2003 (.xml) oder aus Textdateien zu importieren.  
  
 Weitere Informationen zum Datenimport-Assistenten finden Sie in der Hilfe zu Common Data Service.  
  
 Die Common Data Service-Webdienste bieten die folgenden zusätzlichen Funktionen, die im Datenimport-Assistenten nicht verfügbar sind:  
  
- Erstellen Sie Datenzuordnungen, die komplexe Transformationszuordnungen, wie Verkettungen, Teilungen und Ersetzungen, einschließen.  
  
- Definieren Sie benutzerdefinierte Transformationszuordnungen.  
  
- Zeigen Sie Quelldaten an, die innerhalb der temporären Analysetabellen gespeichert sind.  
  
- Greifen Sie auf Fehlerprotokolle zu, um benutzerdefinierte Fehlerberichterstattungstools mit verbesserten Fehlerprotokollierungsansichten zu erstellen.  
  
- Führen Sie den Datenimport aus, indem Sie Befehlszeilenskripts verwenden.  
  
- Fügen Sie `LookupMap`XML-Tags in der Datenzuordnung hinzu, um anzugeben, dass die Datensuche initiiert und in einer Quelldatei ausgeführt wird, die bei dem Import verwendet wird.  
  
- Fügen Sie benutzerdefinierte `OwnerMetadata`XML-Tags in der Datenzuordnung hinzu, sodass die Benutzerdatensätze in der Quelldatei den Datensätzen des Benutzers (Systembenutzer) in Common Data Service entsprechen.  
  
- Verwenden Sie optionale Überprüfungen.  
  
  > [!NOTE]
  >  Die Überprüfung ist im Datenimport-Assistent nicht optional.  
  
  Um den Datenimport zu implementieren, führen Sie in der Regel folgende Schritte aus:  
  
- Erstellen Sie eine Datei mit durch Komma getrennten Werten (CSV), eine XML-Kalkulationstabelle 2003 (XMLSS) oder eine Textquelldatei.  
  
- Erstellen Sie eine Datenzuordnung bzw. verwenden Sie eine vorhandene Datenzuordnung.  
  
- Ordnen Sie eine Importdatei einer Datenzuordnung zu.  
  
- Laden Sie den Inhalt einer Quelldatei in die zugeordnete Importdatei.  
  
- Analysieren Sie die Importdatei.  
  
- Transformieren Sie die analysierten Daten.  
  
- Laden Sie die transformierten Daten in den Common Data Service-Zielserver hoch.  
  
  Sie können Daten aus einer oder mehreren Quelldateien importieren. Eine Quelldatei kann Daten für einen oder mehrere Entitätstypen enthalten.  
  
  Transformation Analyse und Hochladen der Daten erfolgt durch die asynchronen Aufträge, die im Hintergrund ausgeführt werden.  
  
> [!NOTE]
>  Standardmäßig werden alle benutzerdefinierten Entitäten für den Import aktiviert. Um festzustellen, ob eine Geschäftsentität für den Import aktiviert ist, zeigen Sie die Entitätsmetadaten für die gewünschte Entität an. Wenn eine Entität für den Import aktiviert ist, ist die Entitätsmetadateneigenschaft `IsImportable` auf `true` festgelegt. Der Wert dieser Eigenschaft kann für die Standardgeschäftsentitäten nicht geändert werden. <!--[!INCLUDE[metadata_browser](../includes/metadata-browser.md)]-->  


### <a name="see-also"></a>Siehe auch

[Vorbereiten einer Quelldatei für den Import](prepare-source-files-import.md)<br />
[Erstellen von Datenzuordnungen für den Import](create-data-maps-for-import.md)<br />
[Hinzufügen von Transformationszuordnungen für den Import](add-transformation-mappings-import.md)<br />
[Konfiguration des Datenimports](configure-data-import.md)<br />
[Ausführen des Datenimports](run-data-import.md)<br />
[Datenimportentitäten](data-import-entities.md)<br />
[Beispiel: Exportieren und Importieren einer Datenzuordnung](org-service/samples/export-import-data-map.md)<br />
[Beispiel: Importieren von Daten mithilfe der komplexen Datenzuordnung](org-service/samples/import-data-complex-data-map.md)<br />
