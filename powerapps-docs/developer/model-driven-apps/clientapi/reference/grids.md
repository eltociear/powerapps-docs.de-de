---
title: Raster und Unterraster in modellgesteuerten Apps für Dynamics 365 | MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 9d35c036-637f-4580-8ba0-027a44c0fdee
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="grids-and-subgrids-in-model-driven-apps-client-api-reference"></a>Raster und Unterraster in modellgestützten Apps (Client-API-Referenz)



Raster zeigen Daten in einem tabellarischen Format in modellgesteuerten Apps. Raster können das gesamte Formular einschließen oder eines der Elemente in einem Formular sein; die letzteren werden als *Unterraster* bezeichnet.

## <a name="types-of-grids"></a>Rastertypen

Es gibt zwei Typen von Rastern in modellgesteuerten Apps:
- **Schreibgeschützte Raster**: Daten anzeigen in einen tabellarischen Format. Um die Daten zu bearbeiten, die in einem schreibgeschützten Raster angezeigt werden, müssen Sie auf den Datensatztyp klicken im Raster, um das Formular zu öffnen, bearbeiten die Daten zu synchronisieren und speichern.
-  **Bearbeitbare Raster**: Neben dem Anzeigen von Daten im Tabellenformat bietet es umfangreiche Inline-Bearbeitungsfunktionen auf Internet- und mobilen Client einschließlich der Möglichkeit, Daten innerhalb der gleichen Rasters zu gruppieren, zu sortieren und zu filtern, um nicht zwischen Datensätzen oder Ansichten zu wechseln. Das bearbeitbare Raster ist ein benutzerdefiniertes Steuerelement und wird im Hauptraster, in den Formularrastern und im Unterraster im Webclient und in Dashboards und im Formularraster auf dem mobilen Clients unterstützt. Obwohl das bearbeitbare Unterrastersteuerelement Bearbeitungsfunktion enthält, sind die schreibgeschützten Rastermetadaten und die Sicherheitsebenen-Einstellungen zentral.

<a name="bkmk_gridcontext"></a>
## <a name="getting-the-grid-context"></a>Abrufen des Rasterkontexts

Rasterkontext ist die Raster- oder Unterrasterinstanz in einem Formular, mit dem Sie Ihren Code ausführen. Weitere Informationen zum Abrufen eines Rasterkontexts, um Ihren JavaScript-Code auszuführen, finden Sie unter [Client API-Rasterkontext](../clientapi-grid-context.md)

## <a name="events"></a>Ereignisse

|Name|Beschreibung|Anwendbar für|
|--|--|--|
|[Unterraster-OnLoad-Ereignis](events/subgrid-onload.md)|Tritt auf, wenn das Unterraster aktualisiert wird. Dies gilt auch dann, wenn Benutzer Werte im Unterraster sortieren, indem sie auf die Spaltenüberschriften klicken.|Schreibgeschütztes Raster|
|[Raster OnChange](events/grid-onchange.md)|Tritt auf, wenn ein Wert an einem Computerarbeitsplatz im bearbeitbaren Raster geändert wurde und die Zelle den Fokus verliert.|Bearbeitbares Raster|
|[Raster OnRecordSelect](events/grid-onrecordselect.md)|Tritt auf, wenn eine einzelne Zeile (Datensatz) im bearbeitbaren Raster ausgewählt ist.|Bearbeitbares Raster|
|[Raster OnSave](events/grid-onsave.md)|Vor dem Versenden der aktualisierten Informationen zum Server tritt es auf und bei einer der folgenden Aktionen: Es gibt eine Änderung in der Datensatz-Auswahl, der Benutzer löst einen Speichervorgang explizit mithilfe der bearbeitbaren Speichern-Schaltfläche des Rasters aus, oder der Benutzer wendet eine Sortierung, einen Filters, eine Gruppe, eine Paginierung oder einen Navigationsvorgang auf das bearbeitbaren Raster an, wenn keine ausstehende Änderungen vorhanden ist.|Bearbeitbares Raster|

>[!NOTE]
>Sie können sich registrieren für die **OnChange**, **OnRecordSelect** und **OnSave**-Ereignisse mithilfe der **Ereignisse**-Registerkarte der modellgesteuerten Apps-Seite, die verwendet wird, um bearbeitbare Raster für eine Entität oder ein schreibgeschütztes Raster zu aktivieren.

## <a name="methods"></a>Methoden

|Name|Beschreibung|Verfügbar für|
|--|--|--|
|[GridControl](grids/gridcontrol.md)|Stellt Methoden zur Arbeit mit dem Raster oder dem Unterrastersteuerelement bereit.|Bearbeitbare und schreibgeschützte Raster|
|[Raster](grids/grid.md)|Stellt Methoden bereit, um auf Informationen über Daten im Raster zuzugreifen.|Bearbeitbare und schreibgeschützte Raster|
|[GridRow](grids/gridrow.md)|Stellt Methoden bereit, um mit Zeilen oder ausgewählten Zeilen im Raster zu arbeiten.|Bearbeitbare und schreibgeschützte Raster|
|[GridRowData](grids/gridrowdata.md)|Stellt Methoden bereit, um mit Zeilen oder ausgewählten Zeilen im Raster zu arbeiten.|Bearbeitbare und schreibgeschützte Raster|
|[GridEntity](grids/gridentity.md)|Stellt Methoden für den Zugriff auf Daten zu den spezifischen Datensätzen in den Zeilen bereit.|Bearbeitbare und schreibgeschützte Raster|
|[GridAttribute](grids/gridattribute.md)|Stellt Methoden bereit, um auf die Daten in der Zelle eines bearbeitbaren Rasters zuzugreifen.|Bearbeitbares Raster|
|[GridCell](grids/gridcell.md)|Stellt Methoden bereit, um auf die Daten zuzugreifen, die mit Steuerelementen in einem Formular zusammenhängen, das einem Attribut in einem bearbeitbaren Raster zugeordnet ist.|Bearbeitbares Raster|
|[ViewSelector](grids/viewselector.md)|Stellt Methoden bereit, um Informationen zur Ansichtsauswahl des Unterrastersteuerelements abzurufen oder festzulegen.|Schreibgeschütztes Raster|


### <a name="related-topics"></a>Verwandte Themen

[Rasterkontext der Client-API](../clientapi-grid-context.md)

[Bearbeitbare Raster verwenden](../../use-editable-grids.md)

[Client-API-Referenz für modellgesteuerte Apps](../reference.md)

[Modell-angetriebene Apps Entwickler-Übersicht](../../overview.md)

