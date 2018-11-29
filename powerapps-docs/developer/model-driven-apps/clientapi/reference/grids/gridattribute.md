---
title: GridAttribute (Client-API-Referenz) in modellgestützten Apps | MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 8139c622-e4d9-478f-9510-414d140e5556
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="gridattribute-client-api-reference"></a>GridAttribute (Client-API-Referenz)



GridAttribute wird nur für bearbeitbare Raster unterstützt.

GridAttribute vertritt die Daten in der Zelle eines bearbeitbaren Rasters und umfasst einen Verweis auf alle gewünschten Zellen, die dem Attribut zugeordnet werden. Soehe [Sammlungen (Client-API-Referenz)](../collections.md) für Informationen zu Methoden zum Zugreifen auf Daten in einer Sammlung.

GridAttribute unterstützt auch die **Steuerelemente**-Sammlung für Attribute einer ausgewählten Rasterzeile, die Methoden bereitstellen, um mit einer Sammlung Zellen von Zellen zu arbeiten, die einem Attribut zugewiesen sind. Jede Zelle ([GridCell](gridcell.md)) einer ausgewählten Rasterzeile ist ein vergleichbares Steuerelement in einem Formular, das mit einem Attribut in einem bearbeitbaren Raster zusammenhängt. Soehe [Sammlungen (Client-API-Referenz)](../collections.md) für Informationen zu Methoden zum Zugreifen auf Daten in einer Sammlung.

>[!TIP]
>Aus Leistungsgründen ist eine Zeile (Datensatz) in einem bearbeitbaren Raster nicht bearbeitet, bis der Datensatz ausgewählt ist. Benutzer müssen einen einzelnen Datensatz in einem Raster auswählen, um ihn zu bearbeiten. Sobald ein Datensatz in einen bearbeitbaren Raster ausgewählt ist, wertet Dynamics 365 intern eine Reihe von Punkten aus, einschließlich Benutzerzugriff zum Datensatz, ob der Datensatz aktiv ist und die Feldüberprüfungen, um sicherzustellen, dass die Datensicherheit und Gültigkeit berücksichtigt werden, wenn Sie die Daten bearbeiten. Sie können das [OnRecordSelect](../events/grid-onrecordselect.md) Ereignis mit der [getFormContext](../executioncontext/getFormContext.md)-Methode verwenden, um auf Datensätze im Raster zuzugreifen, die einen bearbeitbaren Status aufweisen.

## <a name="methods"></a>Methoden

GridAttribute unterstützt die folgenden Arten für Attribute einer ausgewählten Rasterzeile.

|Name|Beschreibung|
|--|--|
|[getName](../attributes/getName.md)|Gibt den logischen Name des Attributs der ausgewählten Rasterzeile zurück.|
|[getRequiredLevel](../attributes/getRequiredLevel.md)| Gibt einen Zeichenfolgenwert zurück, der angibt, ob ein Wert für das Attribut erforderlich oder empfohlen ist.|
|[setRequiredLevel](../attributes/setRequiredLevel.md)| Legt fest, ob Daten für das Attribut einer ausgewählten Rasterzeile erforderlich oder empfohlen sind, bevor der Datensatz gespeichert werden kann.|
|[getValue](../attributes/getValue.md)| Ruft den Datenwert für ein Attribut ab.|
|[setValue](../attributes/setValue.md)| Legt den Datenwert für ein Attribut fest.|

>[!NOTE]
>Wenn Sie eine Zeile in einem bearbeitbaren Raster auszuwählen, verwenden Sie [Grid](grid.md).[getSelectedRows](grid/getSelectedRows.md)

### <a name="related-topics"></a>Verwandte Themen

[GridCell](gridcell.md)

[Raster und Unterraster in modellgestützten Apps](../grids.md)

[Steuerelementsammlung](../attributes/controls-collection.md)


