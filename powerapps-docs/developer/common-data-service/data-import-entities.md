---
title: Datenimportentitäten (Common Data Service) | Microsoft-Dokumentation
description: Listet die Datenimportentitäten für die Erstellung von Datenzuordnungen auf, die für Konfiguration und Ausführung von Datenimporten und die Protokollierung von Fehlerinformationen verwendet werden.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: pehecke
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
ms.openlocfilehash: 6413ec48edc17310cd312e82acae435b2af9ffd4
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3156282"
---
# <a name="data-import-entities"></a>Datenimportentitäten

Die Common Data Service-Datenimportentitäten werden für die Erstellung von Datenzuordnungen, die Konfiguration und AUsführung von Datenimporten und die Protokollierung von Fehlerinformationen verwendet.  

 Die folgende Tabelle enthält die Entitäten, die verwendet werden, um Importvorgänge zu konfigurieren und auszuführen, sowie um Fehler zu protokollieren.  

|Anzeigename der Entität|Beschreibung|  
|----------------------------------|-----------------|  
|Import (Datenimport)|Status- und Besitzinformationen für den Importauftrag.|  
|importfile (Importquelldatei)|Logische Quelldatei.|  
|importlog (Importprotokoll)|Fehlergrund und andere Detailinformationen für Datensätze, die nicht importiert werden konnten.|  

 Die folgende Tabelle enthält die Datenentitäten, die für die Erstellung von Datenzuordnungen verwendet werden.  


|                    Anzeigename der Entität                     |                                                                                                                      Beschreibung                                                                                                                       |
|-------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                       importmap (Datenzuordnung)                        |                                                                                                           Die Datenzuordnung, die für den Import verwendet wird.                                                                                                            |
|                  columnmapping (Spaltenzuordnung)                   |                                                           Zuordnung zwischen einer Spalte in der Quelldatei und einem Zielattribut in Common Data Service.                                                           |
|                  lookupmapping (Suchzuordnung)                   |       Zuordnung zwischen einer Spalte in der Quelldatei oder einer Ausgabe einer komplexen Transformation und einem Zielattribut vom Typ <xref:Microsoft.Xrm.Sdk.EntityReference>. Dies wird in Verbindung mit Spaltenzuordnung oder komplexer Transformationszuordnung verwendet.        |
|                   ownermapping (Besitzerzuordnung)                    |                                                             Zuordnung zwischen einem in der Quelldatei angegebenen Benutzer und einem Benutzer in Common Data Service.                                                             |
|                picklistmapping (Auswahllistenzuordnung)                 | Zuordnung zwischen einer Spalte in der Quelldatei und einem Zielattribut vom Typ <xref:Microsoft.Xrm.Sdk.OptionSetValue>, Boolescher Wert, Zustand oder Status in Common Data Service. In Verbindung mit Spaltenzuordnung verwendet. |
|          transformationmapping (Transformationszuordnung)           |                                                                                                            Komplexe Transformationszuordnung.                                                                                                             |
| transformationparametermapping (Transformationsparameterzuordnung) |                                                                                           Parameterzuordnung, die in der komplexen Transformationszuordnung verwendet wird.                                                                                            |

### <a name="see-also"></a>Siehe auch  
 [Import von Daten in Dynamics 365](import-data.md)   
 [Importentität](reference/entities/import.md)   
 [ImportFile-Entität](reference/entities/importfile.md)   
 [ImportLog-Entität](reference/entities/importlog.md)   
 [ImportMap-Entität](reference/entities/importmap.md)   
 <!-- jdaly These links will have content when we re-gen docs after bug 689487 is checked in. START -->
 [ColumnMapping-Entität](reference/entities/columnmapping.md)   
 [LookupMapping-Entität](reference/entities/lookupmapping.md)   
 [OwnerMapping-Entität](reference/entities/ownermapping.md)   
 [PicklistMapping-Entität](reference/entities/picklistmapping.md)   
 [TransformationMapping-Entität](reference/entities/transformationmapping.md)    
 [TransformationParameterMapping-Entität](reference/entities/transformationparametermapping.md)   
 <!-- jdaly These links will have content  when we re-gen docs after bug 689487 is checked in. END -->
 [Beispiel: Exportieren und Importieren einer Datenzuordnung](/dynamics365/customer-engagement/developer/sample-export-import-data-map)   
 [Erstellen von Datenzuordnungen für den Import](create-data-maps-for-import.md)<br />
 [Hinzufügen von Transformationszuordnungen für den Import](add-transformation-mappings-import.md)<br />
 [Konfiguration des Datenimports](configure-data-import.md)<br />
 [Ausführen des Datenimports](run-data-import.md)<br />
 [Beispiel: Exportieren und Importieren einer Datenzuordnung](/dynamics365/customer-engagement/developer/org-service/samples/export-import-data-map)<br />
 [Beispiel: Importieren von Daten mithilfe der komplexen Datenzuordnung](/dynamics365/customer-engagement/developer/org-service/samples/import-data-complex-data-map)<br />