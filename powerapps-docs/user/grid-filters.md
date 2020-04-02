---
title: Filtern von Daten in Rastern | Microsoft-Dokumentation
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 03/31/2020
ms.author: mkaur
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 54ddcf717b26859e71ed1339caa533fa9c6bcbb8
ms.sourcegitcommit: f5d15c973b2a129a0cc29a74cf8eaf6b24fbf36d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/01/2020
ms.locfileid: "80516662"
---
# <a name="use-grid-filters"></a>Verwenden von Rasterfiltern 

Raster in der einheitlichen Oberfläche wurden verbessert, um die Datenmenge zu erhöhen, die auf dem Bildschirm angezeigt werden kann. Sie können jetzt aus vielen verschiedenen Filteroptionen für eine Spalte auswählen. Der Datentyp der Spalte bestimmt, welche Filteroptionen verfügbar sind. Die Spalte **Vollständiger Name** im Raster **Kontakte** weist beispielsweise andere Filteroptionen als die Spalte **Aktivitätstyp** im Raster **Aktivitäten** auf.


   > [!div class="mx-imgBorder"]
   > ![Rasterfilterung](media/filter-options.png "Rasterfilterung")
   

## <a name="grid-and-filter-navigation"></a>Raster- und Filternavigation

Wenn Sie Daten in einem Raster filtern, speichert die Hauptseite des Rasters den Filter, die Sortierreihenfolge und den Seitenzustand, wenn Sie von der Seite weg navigieren und dann zurückkehren. Die gleiche Funktionsweise ist auch gegeben, wenn die Daten z. B. nach Schnellsuche, Spalten oder Seitenzahl gefiltert sind. 

   > [!div class="mx-imgBorder"]
   > ![Seite wird im gleichen Zustand geöffnet, wenn zurücknavigiert wird](media/grid-remember-state-on-back-navigate.gif "Seite wird im gleichen Zustand geöffnet, wenn zurücknavigiert wird")

Die Navigationsleiste der Seite verwendet das erste sortierte Feld. Wenn keine Änderung an der Sortierreihenfolge vorgenommen wurde, verwendet die Navigationsleiste das primäre Feld.

   > [!div class="mx-imgBorder"]
   > ![Auswahl eines Filters auf der Navigationsleiste](media/jumpbar-filter-on-sorted-column.gif "Auswahl eines Filters auf der Navigationsleiste")
  
Wenn Sie auf das Hierarchiesymbol klicken, wechseln Sie zur Hierarchieansicht.

   > [!div class="mx-imgBorder"]
   > ![Hierarchiesymbol](media/grid-row-hierarchy-icon.png "Hierarchiesymbol")

Sie können auch das primäre Feld und Nachschlagefelder in einer neuen Registerkarte oder in einem neuen Fenster öffnen.

   > [!div class="mx-imgBorder"]
   > ![In neuem Fenster öffnen](media/newtab.png "In neuem Fenster öffnen")
  
  
## <a name="lookup-field-column"></a>Nachschlagefeldspalte

Wenn Sie eine Nachschlagespalte filtern, können Sie aus einer Liste die zu filternden Datensätze auswählen, anstatt die Daten manuell einzugeben. In der Nachschlagespalte **Hauptkontakt** können Sie beispielsweise den Kontaktnamen aus der Datensatzliste auswählen, nach dem gefiltert werden soll.

   > [!div class="mx-imgBorder"]
   > ![Nachschlagefilterung](media/lookup-filter.png "Nachschlagefilterung")

## <a name="date-filter"></a>Datumsfilter

Der robuste Filter **Datum** enthält viele verschiedene Werte wie **Am**, um nach einem genauen Datum zu suchen, oder **Nächste x Geschäftsjahre** bzw. **Im Finanzzeitraum**, um nach Jahr oder Quartal zu suchen.

   > [!div class="mx-imgBorder"]
   > ![Datumsfilterung](media/date-filter.png "Datumsfilterung")

## <a name="filter-the-list-of-activities"></a>Filtern der Aktivitätenliste

Sie können die Aktivitätenliste so filtern, dass nur relevante Einträge angezeigt werden. Sie können die Aktivitäten in einer Ansicht beispielsweise einschränken, indem Sie nach Aktivitätstyp filtern. Aktivitäten können also nach ihrem Typ (E-Mail, Aufgabe, Telefonanruf usw.) gefiltert werden.


   > [!div class="mx-imgBorder"]
   > ![Aktivitätsfilter](media/activity_filter.png "Aktivitätsfilter")


### <a name="known-issue"></a>Bekanntes Problem 

Wenn Sie das Standardanzeigeformat für Zahlen, Währungen, Uhrzeiten und Datumsangaben ändern und anschließend die Daten in einem Raster filtern, zeigt der Filter das ausgewählte Anzeigeformat nicht an. Die Filter werden weiterhin im Standardformat des Systems angezeigt, und in einigen Fällen funktioniert das Filtern möglicherweise überhaupt nicht. 

Legen Sie das Anzeigeformat für Zahlen, Währungen, Uhrzeiten und Datumsangaben wieder auf die Standardeinstellung fest. 

1. Klicken Sie in der rechten oberen Ecke auf das Zahnradsymbol ![Zahnradsymbol](media/selection-rule-gear-button.png) und anschließend auf **Personalisierungseinstellungen**.

2. Ändern Sie auf der Registerkarte **Formate** die Werte für Zahlen, Währungen, Uhrzeiten und Datumsangaben zurück in die Standardeinstellung.

    > [!div class="mx-imgBorder"] 
    > ![Formateinstellungen](media/default-format.png "Formateinstellungen")
    
Wir arbeiten an diesem Problem und veröffentlichen so schnell wie möglich Informationen zu einer Lösung.

  
## <a name="use-search-on-a-grid"></a>Verwenden der Suche in einem Raster

Wenn Sie die Option **Diese Ansicht durchsuchen** auf einer Rasterseite verwenden, sucht das System nach Daten in der aktuellen Ansicht. Im folgenden Beispiel führen Sie eine Suche im Raster **Kontakte** durch.

1. Navigieren Sie zum Raster **Kontakte**, und wählen Sie dann **Meine aktiven Kontakte** aus der Ansichtsliste aus.

    > [!div class="mx-imgBorder"]
    > ![Ansicht „Meine aktiven Kontakte“](media/myactive-contacts-view.png "Ansicht „Meine aktiven Kontakte“")

2. Klicken Sie auf **Diese Ansicht durchsuchen**, um nach Daten in der aktuellen Ansicht zu suchen.

    > [!div class="mx-imgBorder"]
    > ![Suchansicht](media/search-view.png "Diese Ansicht durchsuchen")

Das System durchsucht die Ansicht **Meine aktiven Kontakte** nach Daten und zeigt die Suchergebnisse an. Dabei werden die Spalten angezeigt, die in Ihrer aktuellen Ansicht verwendet werden.

   > [!div class="mx-imgBorder"]
   > ![Suchansicht](media/search-view2.png "Suchergebnisse des Befehls „Diese Ansicht durchsuchen“")


## <a name="use-the-quick-find-search-experience"></a>Verwenden der Schnellsuche

Sie können zur alten Schnellsuche zurückkehren, bei der die Schnellsucheansichtdefinition einer Entität für die Suche verwendet wird. Dafür benötigen Sie jedoch Administratorrechte.

1. Klicken Sie in der rechten oberen Ecke auf das Zahnradsymbol ![Zahnradsymbol](media/selection-rule-gear-button.png) und anschließend auf **Erweiterte Einstellungen**.

2. Navigieren Sie zu **Einstellungen** > **Verwaltung** > **Systemeinstellungen**.

3. Wählen Sie auf der Registerkarte **Allgemein** unter **Schnellsuche einrichten** **Ja** für die Option **Use quick find view of an entity for searching on grids and sub-grids** (Schnellsucheansicht einer Entität für Suche in Rastern und Unterrastern verwenden) aus.



