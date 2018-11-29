---
title: Grid OnSave Ereignis (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 89123cde-7c66-4c7d-94e4-e287285019f8
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="grid-onsave-event-client-api-reference"></a>OnSave-Rasterereignis (Client-API-Referenz)



Das `OnSave`-Ereignis tritt auf, bevor die aktualisierten Informationen an den Server gesendet werden und wenn einer der folgenden Aktionen erfolgt: 
- Es gibt eine Änderung in der Datensatz-Auswahl.
- Der Benutzer startet explizit einen Speichervorgang mithilfe der Schaltfläche "Speichern" im bearbeitbaren Raster.
- Der Benutzer wendet den Sortierungs-, Gruppen-, Paginierungs- oder Navigationsvorgang im bearbeitbaren Raster an, wenn es ausstehende Änderungen gibt.

Wichtige zu beachtende Punkte für das `OnSave`-Ereignis: 
- Wenn ein Benutzer mehrere Spalten desselben Datensatzes nacheinander bearbeitet, wird das OnSave-Ereignis nur einmal aufgerufen, um optimale Leistungs- und Formkompatibilität zu gewährleisten.
- Bearbeitbare Raster und das übergeordnete Formular haben separate Speicherschaltflächen. Beim Klicken auf die eine Speicherschaltfläche werden keine Änderungen in der anderen gespeichert.
- Bearbeitbare Raster speichern keine ausstehenden Änderungen, wenn Navigationsvorgänge außerhalb des Kontexts ausgeführt werden. Wenn das Steuerelement nicht gespeicherten Daten enthält, können die Daten möglicherweise verloren gehen. Daher löst das `OnSave`-Ereignis nichts aus. Beispielsweise kann dies vorkommen, wenn Sie zu einem anderen Datensatz navigieren und eine Formularsuchfeld verwenden oder über das Menüband gehen.
- Das Drücken der Schaltfläche "Aktualisieren " im bearbeitbaren Raster, kann alle ausstehenden Änderungen verwerfen, und das `OnSave`-Ereignis wird nicht ausgelöst.
- Bearbeitbare Rastersteuerelemente implementieren keinen Zeitgeber mit automatischer Speicherung.
Bearbeitbares Raster unterdrücken Duplikaterkennungsregeln.

### <a name="related-topic"></a>Verwandtes Thema
[OnSave-Formularereignis](form-onsave.md)



