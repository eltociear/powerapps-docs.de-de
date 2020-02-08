---
title: Filtern von Daten in Rastern | MicrosoftDocs
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 02/03/2019
ms.author: mkaur
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 2cfe55db19b5d8a7aeed86169a188455686cf81b
ms.sourcegitcommit: 68a31e3fa4d1635ccf4cd8bd9da5fba1bfecefa4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/06/2020
ms.locfileid: "77051965"
---
# <a name="use-grid-filters"></a>Verwenden von Raster Filtern 

Raster in der vereinheitlichten Oberfläche wurden verbessert, um die Datenmenge zu erhöhen, die auf dem Bildschirm angezeigt werden kann. Nun können Sie aus vielen verschiedenen Filteroptionen für eine Spalte auswählen. der Typ der Daten in der Spalte bestimmt, welche Filteroptionen verfügbar sind. Beispielsweise weist die Spalte **Vollständiger Name** im Feld **Kontakte** verschiedene Filteroptionen auf als die Spalte **Aktivitätstyp** im **Aktivitäts Raster.**


   > [!div class="mx-imgBorder"]
   > ![Raster Filterung](media/filter-options.png "Raster Filterung")
   

## <a name="grid-and-filter-navigation"></a>Raster-und Filter Navigation

Wenn Sie Daten in einem Raster filtern, speichert die Haupt Raster Seite den Filter, die Sortierreihenfolge und den Seiten Zustand, wenn Sie zu der Seite navigieren und dann zur Seite zurückkehren. Dies funktioniert genauso, wenn Daten nach Schnellsuche, Spalten Filterung, Seitenzahl usw. gefiltert werden. 

   > [!div class="mx-imgBorder"]
   > ![Wenn Sie zurück zur Seite navigieren, wird Sie in demselben Zustand geöffnet.](media/grid-remember-state-on-back-navigate.gif "Wenn Sie zurück zur Seite navigieren, wird Sie in demselben Zustand geöffnet.")

Die Seitensprung Leiste verwendet das erste sortierte Feld. Wenn keine Änderung an der Sortierreihenfolge vorgenommen wurde, verwendet die Sprung Leiste das primäre Feld.

   > [!div class="mx-imgBorder"]
   > ![Filter auf der Sprung Leiste auswählen](media/jumpbar-filter-on-sorted-column.gif "Filter auf der Sprung Leiste auswählen")
  
Wenn Sie das Hierarchie Symbol auswählen, navigieren Sie zur Hierarchie Ansicht.

   > [!div class="mx-imgBorder"]
   > ![Hierarchie Symbol](media/grid-row-hierarchy-icon.png "Symbol "Hierarchie"")

Sie können auch primäre Feld-und Nachschlage Felder in einer neuen Registerkarte oder einem neuen Fenster öffnen.

   > [!div class="mx-imgBorder"]
   > ![In neuem Fenster öffnen](media/newtab.png "[In neuem Fenster öffnen")
   
   
### <a name="known-issue"></a>Bekannte Probleme

Wenn Sie das Standard Anzeige Format für Number, Currency, Time oder Date ändern und dann Daten in einem Raster filtern, zeigt der Filter das ausgewählte Anzeige Format nicht an. Die Filter werden weiterhin im Standardformat des Systems angezeigt, und in einigen Fällen funktioniert das Filtern möglicherweise überhaupt nicht. 

Um das Problem zu beheben, legen Sie das Anzeige Format für Anzahl, Währung, Uhrzeit und Datum auf die Standardeinstellung zurück. 

1. Wählen Sie in der oberen rechten Ecke das Zahnrad Symbol ![Zahnrad Symbol](media/selection-rule-gear-button.png)aus, und wählen Sie dann **Personalisierungs Einstellungen**aus.

2. Ändern Sie auf der Registerkarte **Formate** die Werte für Anzahl, Währung, Uhrzeit und Datum wieder in die Standardeinstellung.

    > [!div class="mx-imgBorder"] 
    > ![Format Einstellungen](media/default-format.png "Format Einstellungen")
    
    
  Wir arbeiten an diesem Problem. Überprüfen Sie die Verfügbarkeit. 



## <a name="preview-new-grid-filters-and-search-option"></a>Vorschau: neue Raster Filter und Suchoption

Dieser Abschnitt ist für Funktionen für den frühen Zugriff vorgesehen. Sie können sich früh entscheiden, diese Features in Ihrer Umgebung zu aktivieren. Auf diese Weise können Sie diese Features testen und Sie dann in ihren Umgebungen übernehmen. Informationen dazu, wie Sie diese Features aktivieren, finden [Sie unter Opt in 2020 Release Wave 1 Updates](https://docs.microsoft.com/power-platform/admin/opt-in-early-access-updates).


   > [!NOTE]
   > Ändern Sie das Standard Anzeige Format für Zeit, Anzahl, Währung, Uhrzeit oder Datum nicht, da hierdurch ein Problem verursacht wird. Weitere Informationen finden Sie unter [bekanntes Problem](https://docs.microsoft.com/powerapps/user/grid-filters#known-issue).

### <a name="lookup-field-column"></a>Spalte für Nachschlage Feld

Wenn Sie nach einer Such Spalte filtern, können Sie aus einer Liste von Datensätzen auswählen, nach denen gefiltert werden soll, anstatt Sie manuell einzugeben. Beispielsweise können Sie in einer **primären Kontakt** Such Spalte den Kontaktnamen aus der Liste der Datensätze auswählen, nach denen gefiltert werden soll.

   > [!div class="mx-imgBorder"]
   > ![Such Filterung](media/lookup-filter.png "Such Filterung")

### <a name="date-filter"></a>Datumsfilter

Der robuste **Datums** Filter umfasst viele verschiedene Werte, aus denen Sie auswählen können, z. b. ein **, um nach** einem exakten Datum zu suchen, oder das **Nächste X-Geschäftsjahr** oder **in einem Geschäfts Zeitraum** , um nach Jahr oder Quartal zu suchen.

   > [!div class="mx-imgBorder"]
   > ![Datums Filterung](media/date-filter.png "Datums Filterung")

### <a name="filter-the-list-of-activities"></a>Filtern der Liste der Aktivitäten

Sie können die Liste der Aktivitäten filtern, um nur diejenigen anzuzeigen, die für Sie von Interesse sind. Beispielsweise können Sie die Aktivitäten, die Sie in einer Ansicht sehen, mit dem Aktivitätstyp Filter weiter einschränken. Mit dem Aktivitätstyp Filter können Sie Aktivitäten filtern, die auf dem Typ basieren, z. b. e-Mail, Aufgabe, Telefonanruf usw.


   > [!div class="mx-imgBorder"]
   > ![Aktivitäts Filter](media/activity_filter.png "Aktivitäts Filter")


#### <a name="known-issue"></a>Bekannte Probleme

Wenn Sie das Standard Anzeige Format für Number, Currency, Time oder Date ändern und dann Daten in einem Raster filtern, zeigt der Filter das ausgewählte Anzeige Format nicht an. Die Filter werden weiterhin im Standardformat des Systems angezeigt, und in einigen Fällen funktioniert das Filtern möglicherweise überhaupt nicht. 

Um das Problem zu beheben, legen Sie das Anzeige Format für Anzahl, Währung, Uhrzeit und Datum auf die Standardeinstellung zurück. 

1. Wählen Sie in der oberen rechten Ecke das Zahnrad Symbol ![Zahnrad Symbol](media/selection-rule-gear-button.png)aus, und wählen Sie dann **Personalisierungs Einstellungen**aus.

2. Ändern Sie auf der Registerkarte **Formate** die Werte für Anzahl, Währung, Uhrzeit und Datum wieder in die Standardeinstellung.

    > [!div class="mx-imgBorder"] 
    > ![Format Einstellungen](media/default-format.png "Format Einstellungen")
    
    
Wir arbeiten an diesem Problem. Überprüfen Sie die Verfügbarkeit. 
  
### <a name="use-search-on-a-grid"></a>Verwenden der Suche in einem Raster

Wenn Sie die Option **diese Ansicht suchen** auf einer Raster Seite verwenden, sucht das System in der Sicht, in der Sie sich gerade befinden, nach Daten. Im folgenden Beispiel führen Sie eine Suche im **Kontakt** Raster aus.

1. Wechseln Sie zum **Kontakt** Raster, und wählen Sie dann in der Liste der Ansichten **meine aktiven Kontakte** aus.

    > [!div class="mx-imgBorder"]
    > ![Meine aktive Kontaktansicht](media/myactive-contacts-view.png "Meine aktive Kontaktansicht")

2. Wählen Sie **diese Ansicht durchsuchen** aus, um Daten in der Ansicht zu suchen, in der Sie sich befinden.

    > [!div class="mx-imgBorder"]
    > ![Such Ansicht](media/search-view.png "Diese Ansicht durchsuchen")

Das System sucht in der Ansicht " **meine aktive Kontakte** " nach Daten und zeigt die Suchergebnisse an, indem die gleichen Spalten verwendet werden, die in der aktuellen Ansicht verwendet werden.

   > [!div class="mx-imgBorder"]
   > ![Such Ansicht](media/search-view2.png "Suchergebnisse im Befehl "diese Ansicht durchsuchen"")


#### <a name="use-the-quick-find-search-experience"></a>Verwenden Sie die Schnellsuche

Sie benötigen Administrator Berechtigungen, um zur alten Schnellsuche-Suchfunktion zurückzukehren, die die Schnellsuche-Sicht Definition einer Entität zum Durchführen von Such Vorgängen verwendet.

1. Wählen Sie in der oberen rechten Ecke das Zahnrad Symbol ![Zahnrad Symbol](media/selection-rule-gear-button.png), und klicken Sie dann auf **Erweiterte Einstellungen**.

2. Wechseln Sie zu **Einstellungen** > **Verwaltung** > **System Einstellungen**.

3. Wählen Sie auf der Registerkarte **Allgemein** unter **Schnellsuche einrichten**die Option **Ja** aus, um die **Schnellsuche-Ansicht einer Entität für die Suche in Raster und unter Raster zu verwenden**.



