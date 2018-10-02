---
title: Konfigurieren von Dashboards für interaktive Funktionen in PowerApps | Microsoft Docs
description: Informationen zum Konfigurieren von Dashboards für interaktive Funktionen in PowerApps
keywords: Interaktive Dashboards; Customer Service; Microsoft Dynamics 365; Interaktiver Servicehub
author: Mattp123
ms.author: matp
manager: kvivek
ms.custom: ''
ms.date: 05/21/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
ms.assetid: d1446a95-14bf-4b15-a905-72fce07f4c76
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="configure-model-driven-app-interactive-experience-dashboards"></a>Informationen zum Konfigurieren von Dashboards für interaktive Funktionen

Dashboards für interaktive Funktionen können ein zentraler Arbeitsbereich für App-Benutzer sein, wie beispielsweise Servicebeauftragte, damit sie Arbeitsauslastungsinformationen anzeigen können und tätig werden können. Sie sind vollständig konfigurierbar, auf Sicherheits-Rolle basierend und liefern Arbeitsauslastungsinformationen für mehrere Streams in Echtzeit. Interaktive Dashboardbenutzer müssen nicht die ganze Anwendung durchgehen, um nach einem bestimmten Datensatz zu suchen. Sie können direkt vom Dashboard aus daraufhin handeln. 

 Es gibt zwei Arten von Dashboards mit interaktiven Funktionen: Streamübersichts- und Streamdetail-Dashboards. Darüber hinaus können Streamübersichts-Dashboard homepage- oder entitätsspezifische Dashboards sein. Die entitätsspezifischen Dashboards werden in einem anderen Teil der Benutzeroberfläche konfiguriert und teilweise mit den entitätsspezifischen Konfigurationsinformationen vorab geladen.  
  
 Die Streamübersichts-Dashboards zeigen Daten in Echtzeit für mehrere Datenstreams an. Es gibt keine Begrenzung darüber, wie viele Streams Sie am Dashboard konfigurieren können. Die Daten in einem Stream können nur auf einer Entität, basieren, aber jeder Stream kann auf Basis einer anderen Entität basiert werden. In entitätsspezifischen Dashboards basieren alle Streams auf derselben Entität. Die Daten fließen aus verschiedenen Ansichten oder Warteschlangen, beispielsweise **Meine Aktivitäten**, **Meine Anfragen** oder **Anfragen in der Banking-Warteschlange**. 
  
 Die Streamdetail-Dashboards zeigen Echtzeitdaten über einen Stream basierend auf einer Entitätsansicht oder Warteschlange an. Die Kacheln befinden sich auf der rechten Seite der Dashboards und werden immer angezeigt. Die Streamdetail-Dashboards sind in der Regel für Serviceleiter und -Manager der Ebene 2 hilfreich, die weniger aber komplexere oder eskalierte Anfragen überwachen.  
  
 Streamübersichts- und Streamdetail-Dashboard enthalten Diagramme, die Ihnen die Anzahl relevanter Datensätzen bereitstellen, z. B. Anfragen nach Priorität oder Status. Diese Diagramme agieren auch als visuelle Filter. Die visuellen Filter (interaktive Diagramme) basieren mehreren Entitäten, und in den Streamdetail-Dashboards definiert die Entität im Datenstream die visuelle Filterentität.   
  
 Benutzer können zusätzliche Filterung mit globalem Filter und Zeitrahmenfilter anwenden. Der globale Filter funktioniert auf Feldebene für alle Diagramme sowie für Streams und Kacheln, die auf der Filterentität basieren. Sie geben die Filterentität an, wenn Sie die visuellen Filter konfigurieren. 
  
> [!NOTE]
>  Die interaktiven Dashboards sind lösungsfähig und können erst exportiert und dann in verschiedene Umgebungen als Lösung importiert werden. Die Warteschlangen, auf den die Streams und Kacheln basieren, sind jedoch nicht lösungsfähig. Bevor die Dashboardlösung in das Zielsystem importiert wird, muss die Warteschlange im Zielsystem in **Einstellungen** > **Serviceverwaltung** > **Warteschlangen** manuell erstellt werden. Nachdem Sie die Warteschlangen erstellt haben, importieren Sie die Dashboardlösung zum Zielsystem und bearbeiten Sie die Streams und Kacheln, die auf den Warteschlangen basieren, um die neu erstellten Warteschlangen entsprechend zuzuweisen.  
  
 Die Abbildungen in diesem Thema zeigen Streamübersichts- und Streamdetail-Dashboards mit deren Kopfzeilenbereich. Unter der Kopfzeile finden Sie visuelle Filter und Streams. In Streamdetail-Dashboard finden Sie auch Kacheln. Für jeden Dashboardtyp können Sie aus verschiedenen Layouts auswählen, die auch angezeigt werden. Die Dashboardkopfzeile enthält die folgenden Steuerelemente und auswählbaren Symbole, von links nach rechts: Dashboardauswahl, Aktualisierung, Symbol für visuellen Filter, Symbol für globalen Filter und Zeitrahmenfilter.  
  
### <a name="multi-stream-dashboard-standard-view"></a>Streamübersichts-Dashboard-Standardansicht  
 Im Streamübersichts-Dashboard wird oben eine Reihe visueller Filter mit den Datenstreams darunter angezeigt.  
 
![Streamübersichts-Dashboard](../model-driven-apps/media/interactive-dashboards-multi-stream.png) 
   
### <a name="multi-stream-dashboard-tile-view"></a>Streamübersichts-Dashboard-Kachelansicht  
 Dasselbe Dashboard, nur in der Kachelansicht.  
  
 ![Kachelansicht Streamübersichts-Dashboard](../model-driven-apps/media/interactive-dashboards-multi-stream-tiles.png "Kachelansicht Streamübersichts-Dashboard")  
  
### <a name="multi-stream-dashboard-layouts"></a>Streamübersichts-Dashboard-Layouts  
 Für Streamübersichts-Dashboards können Sie vier verschiedene Layouts auswählen.  

 > [!div class="mx-imgBorder"] 
 > ![Layouts Streamübersichts-Dashboard](../model-driven-apps/media/interactive-dashboards-multi-stream-layout.png "Layouts Streamübersichts-Dashboard")  
  
### <a name="multi-stream-entity-specific-dashboard"></a>Entitätsspezifisches Streamübersichts-Dashboard.  
 Das entitätsspezifische Dashboard für die `Case`-Entität wird hier gezeigt.  
  
 ![Dashboard mit offenen Fällen](../model-driven-apps/media/interactive-dashboard-cases-dashboard.PNG "Dashboard mit offenen Fällen")  
  
### <a name="single-stream-dashboard"></a>Streamdetail-Dashboard  
 Das Streamdetail-Dashboard enthält den Datenstream auf den linken Seite und visuelle Filter und Kacheln auf der rechten Seite.  
  
 ![Interaktives Streamdetail-Dashboard für den Servicehub](../model-driven-apps/media/interactive-dashboards-single-stream.png "Interaktives Streamdetail-Dashboard für den Servicehub")  
  
### <a name="single-stream-dashboard-layouts"></a>Streamdetail-Dashboard-Layouts  
 Für Streamdetail-Dashboards können Sie vier verschiedene Layouts auswählen.  
 
 > [!div class="mx-imgBorder"] 
 > ![Layouts Streamdetail-Dashboard.](../model-driven-apps/media/interactive-dashboards-single-stream-layout.png "Layouts Streamdetail-Dashboard.")  
  
<a name="BKMK_Enable"></a>   
## <a name="configure-entities-fields-and-security-roles-for-the-interactive-dashboards"></a>Konfigurieren von Entitäten, Feldern und Sicherheitsrollen für die interaktiven Dashboards  
 Wenn Sie interaktive Dashboards konfigurieren, sollten Sie zunächst Entitäten, Felder und Sicherheitsrollen für die interaktive Erfahrung aktivieren.  
  
### <a name="entities-enabled-for-interactive-experience"></a>Entitäten, die für interaktive Funktionen aktiviert sind
 Alle Entitäten, die auf der einheitlichen Oberfläche unterstützt werden, werden für das interaktive Funktionen-Dashboard aktiviert.
  
### <a name="configure-fields"></a>Konfigurieren von Feldern  
 Damit ein Feld im globalen Filter angezeigt wird und in der Datenstreamsortierung enthalten ist, müssen zwei Flags, wie im Beispiel unten veranschaulicht, für das Feld **IsEscalated** der Anfrageentität, festgelegt werden.  

 > [!div class="mx-imgBorder"] 
 > ![Ein Feld für einen globalen Filter aktivieren und sortieren](../model-driven-apps/media/global-filter-sort-8.png "Ein Feld für einen globalen Filter aktivieren und sortieren")  
  
### <a name="configure-global-filter-fields"></a>Konfigurieren von globalen Filterfeldern  
 Damit ein Feld wird im globalen Filter angezeigt wird, müssen Sie das Flag **Erscheint im globalen Filter in Interaktive Funktionen** für dieses Feld festlegen. Die Felder, die Sie konfigurieren, werden im globalen Filter-Flyoutfenster angezeigt, wenn in der Dashboardkopfzeile auf das Symbol für den globalen Filter geklickt wird. In Flyoutfenster können die Servicemitarbeiter die Felder auswählen, auf denen sie global filtern möchten, z. B. in Diagrammen und ebenfalls in Streams und Kacheln, die auf der Filterentität basieren. Weitere Informationen zur Filterentität finden Sie im Abschnitt "Konfigurieren eines interaktiven Streamübersichts-Dashboards" später in diesem Thema.  
  
 Das Flyoutfenster für den globalen Filter wird hier gezeigt:  
  
 ![Zwei globale Filterfelder einfügen](../model-driven-apps/media/interactive-dashboards-global-filter-two-fields.png "Zwei globale Filterfelder einfügen")  
  
> [!NOTE]
>  Wenn Sie einen visuellen Filter (interaktives Diagramm) konfigurieren, der auf Felder wie "Priorität" bzw. "Status" basiert, ist es eine bewährte Methode, die Anzeige dieser Felder (Priorität, Status) auch im globalen Filter zu aktivieren.  
  
Im folgenden Verfahren werden die Schritte zum Festlegen des globalen Filter-Flags beschrieben:
  
1. Öffnen Sie den [Lösungs-Explorer](advanced-navigation.md#solution-explorer).  
  
2. Erweitern Sie unter **Komponenten** den Ordner **Entitäten**, und erweitern Sie dann die gewünschte Entität. Wenn die gewünschte Entität nicht angezeigt wird, wählen Sie **Vorhandenes Element hinzufügen** aus, um sie hinzuzufügen.  
  
3.  Wählen Sie im Navigationsbereich **Felder** aus, und doppelklicken Sie im Raster auf das Feld, das Sie aktivieren möchten.  
  
4.  Aktiveren Sie auf der Registerkarte **Allgemein** das Kontrollkästchen **Wird im globalen Filter in interaktiven Funktionen angezeigt**. Klicken Sie auf **Speichern und schließen**.  
  
5.  Wählen Sie **Veröffentlichen** aus, damit die Änderungen wirksam werden.  
  
6.  Wählen Sie **Clientanpassungen vorbereiten** aus.  
  
### <a name="configure-sortable-fields"></a>Konfigurieren von sortierbaren Feldern  
 Damit ein Feld in den Sortierungsstreamdaten verwendet werden kann, müssen Sie das Flag **Sortierbar im Dashboard Interaktive Funktionen** für dieses Feld festlegen. Die Felder, die Sie zum Sortieren konfigurieren, werden in der Dropdownliste im Flyout-Dialogfeld **Eigenschaft bearbeiten** angezeigt, wenn der Benutzer die Schaltfläche für **Mehr (...)** in der Streamkopfzeile auswählt. Die folgende Abbildung zeigt das Flyout-Dialogfeld mit der Liste der für das Sortieren verfügbaren Felder in der **Sortieren nach**-Dropdownliste. Die Standardsortierung ist stets im Feld **Geändert am** festgelegt.  
  
 ![Nach Dropdownliste sortieren](../model-driven-apps/media/interactive-dashboard-sortable-fields-dropdown.png "Nach Dropdownliste sortieren")  
  
Im folgenden Verfahren werden die Schritte zum Festlegen des Flags für das Sortieren beschrieben:
  
1. Öffnen Sie den [Lösungs-Explorer](advanced-navigation.md#solution-explorer).   
2. Erweitern Sie unter **Komponenten** den Ordner **Entitäten**, und erweitern Sie dann die gewünschte Entität. Wenn die Standardentität nicht angezeigt wird, wählen Sie **Vorhandenes Element hinzufügen** aus, um sie hinzuzufügen.  
  
3.  Wählen Sie im Navigationsbereich **Felder** aus, und doppelklicken Sie im Raster auf das Feld, das Sie aktivieren möchten.  
  
4.  Aktiveren Sie auf der Registerkarte **Allgemein** das Kontrollkästchen **Im Dashboard für interaktive Funktionen sortierbar**. Klicken Sie auf **Speichern und schließen**.  
  
5.  Wählen Sie **Veröffentlichen** aus, damit die Änderungen wirksam werden.  
  
6.  Wählen Sie **Clientanpassungen vorbereiten** aus.  
  
### <a name="enable-security-roles"></a>Sicherheitsrollen aktivieren  
 Wählen Sie Sicherheitsrollen aus, mit denen interaktive Dashboards angezeigt werden können, und aktivieren Sie diese.  
  
Im folgenden Verfahren werden die Schritte zum Aktivieren der Sicherheitsrollen für interaktive Funktionen beschrieben.
  
1. Öffnen Sie den [Lösungs-Explorer](advanced-navigation.md#solution-explorer).  
  
2. Wählen Sie unter **Komponenten** die Option **Dashboards** aus.  
  
4.  Wählen Sie im Raster das gewünschte interaktive Dashboard aus, und wählen Sie **Sicherheitsrollen aktivieren** auf der Taskleiste aus.  
  
5.  Wählen Sie im Dialogfeld **Sicherheitsrollen zuweisen** die Option **Nur für ausgewählte Sicherheitsrollen anzeigen** aus und Wählen Sie die Rollen aus, die Sie aktivieren möchten. Wählen Sie **OK** aus.  
  
6.  Wählen Sie **Veröffentlichen** aus, damit die Änderungen wirksam werden.  
  
7.  Wählen Sie **Clientanpassungen vorbereiten** aus.  
  
 ![Sicherheitsrollen aktivieren](../model-driven-apps/media/interactive-dashboards-enable-security-roles.png "Sicherheitsrollen aktivieren")  
  
 ![Sicherheitsrollen zuweisen](../model-driven-apps/media/interactive-dashboards-assign-security-roles.png "Sicherheitsrollen zuweisen")  
  
<a name="BKMK_Configure"></a>   
## <a name="configure-interactive-experience-dashboards"></a>Konfigurieren von Dashboards für interaktive Funktionen  
 In den folgenden Abschnitten wird das Konfigurieren verschiedener Typen von interaktiven Dashboards beschrieben.  
  
### <a name="configure-a-multi-stream-interactive-dashboard-using-the-4-column-layout"></a>Konfigurieren Sie ein interaktives Dashboard mit mehreren Streams mithilfe des Layouts mit 4 Spalten.  
 
1.  Melden Sie sich bei [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an.

2.  Wählen Sie **Modellgesteuert** (unten links) aus.  
  
3.  Wählen Sie **Daten** > **Entitäten** > die gewünschte Entität aus. 

4.  Wählen Sie die Registerkarte **Dashboards** und anschließend auf der Symbolleiste die Option **Dashboard hinzufügen** aus.  
  
5.  Wählen Sie das Layout aus, entweder mit einer Spaltenbreite von 2, 3 oder 4.  
  
6.  Wenn das Dashboardformular geöffnet wird, geben Sie die Filterungsinformationen oben im Formular ein, wie hier beschrieben.  
 
 > [!div class="mx-imgBorder"] 
 > ![Visuelle Filter hinzufügen](../model-driven-apps/media/interactive-dashboards-add-visual-filters.png "Visuelle Filter hinzufügen")  
  
   - **Filterentität**: Die visuellen Filter (interaktive Diagramme) und globalen Filterattribute basieren auf dieser Entität.  
      
    - **Entitätsansicht**: Die visuellen Filter (interaktive Diagramme) basieren auf dieser Ansicht.  
      
    - **Filtern nach**: Das Feld, für das der Zeitrahmenfilter gilt.  
      
    - **Zeitrahmen**: Der standardmäßige Zeitrahmenfilterwert für das Feld **Filtern nach**.  
      
 Nachdem Sie die Filterungsinformationen angegeben haben, starten Sie das Hinzufügen von Komponenten für die Diagramme und die Datenstreams. Um eine Komponente hinzufügen, wählen Sie das Element in der Mitte des Diagramms oder des Streams aus. Wenn das Dialogfeld angezeigt wird, geben Sie die erforderlichen Informationen ein (wie in den folgenden Abbildungen zu sehen).  
  
 Fügen Sie das Ringdiagramm **Anfragen nach Priorität** hinzu:
  
 > [!div class="mx-imgBorder"] 
 > ![Eine Ringdiagrammkomponente hinzufügen.](../model-driven-apps/media/interactive-dashboards-add-chart-circle.png "Eine Ringdiagrammkomponente hinzufügen.")  
  
 Einige Diagramme oder Kreisdiagramme oder Balkendiagramme Rendern die Datenanzeige, die im System gespeichert werden. Die Ring- und Tag-Diagramme werden als statische Bilder geladen und zeigen nicht die Vorschau der tatsächlichen Daten.  
  
> [!NOTE]
>  Die Diagramme, die für die visuellen Filter konfiguriert sind, können die Felder der Entität **Filter** sowie verbundene Entitäten benutzen. Wenn Sie Diagramme benutzen, die auf Feldern verbundener Entitäten basieren, können die Kundendienstmitarbeiter Diagramme unter Verwendung dieser Felder der verbundenen Entitäten filtern. Die Felder, die auf der verbundenen Entität basieren, haben das folgende Format im Diagrammkonfigurationsfenster: "Feldname (Entitätsname)", z. B. das Feld **Geändert von (Stellvertretung)**. Um Mehrfachentitätsdiagramme zu erstellen, müssen Sie Felder einer verbundenen Entität allen Ansichten hinzufügen und diese Felder dann bei der Erstellung von Diagrammen verwenden.  
 
 > [!div class="mx-imgBorder"] 
 > ![Diagramme für visuelle Filter erstellen](../model-driven-apps/media/interactive-dashboard-visual-charts-x-y-axes.PNG "Diagramme für visuelle Filter erstellen")  
  
 Anschließend konfigurieren Sie die Streams. Genau wie beim Hinzufügen von Komponenten in den Diagrammen, wählen Sie das Element im Streambereich aus. Wenn der Dialog erscheint, wählen Sie **Ansicht** oder **Warteschlange** aus, abhängig davon, auf welchem Element Sie den Stream verwenden möchten. Geben Sie die erforderlichen Informationen wie in den folgenden Abbildungen ein.  
  
> [!NOTE]
>  Die **Warteschlangenoption** ist im Dialogfeld nur für warteschlangenfähige Entitäten verfügbar. Wenn die Entität nicht warteschlangenfähig ist, wird die **Warteschlangenoption** für Entitätendashboards nicht im Dialogfeld angezeigt. Sie können für Entitäten, die nicht warteschlangenfähig sind, nur die **Ansichtsoption** im Dashboard-Stream verwenden.  
  
 Konfigurieren Sie den Stream für **Für Bearbeitung verfügbare Elemente**, wie hier dargestellt:  
  
 ![Einen Stream meiner aktiven Fälle hinzufügen.](../model-driven-apps/media/interactive-dashboards-add-stream-case.png "Einen Stream meiner aktiven Fälle hinzufügen.")  
  
 Die folgende Abbildung ist ein Beispiel des Diagrammbereichs; von links nach rechts: Ring-Diagramm, Tag-Diagramm und Balkendiagramm.  
 
 > [!div class="mx-imgBorder"] 
 > ![Alle interaktiven Diagramme](../model-driven-apps/media/interactive-dashboards-add-all-charts.png "Alle interaktiven Diagramme")  
  
 Diese Abbildung ist ein Beispiel des Streambereichs mit mehreren Streams:  
 
 > [!div class="mx-imgBorder"] 
 > ![Alle Streams hinzufügen](../model-driven-apps/media/interactive-dashboards-add-all-streams.png "Alle Streams hinzufügen")  
  
 Nach dem Konfigurieren des Dashboards, speichern Sie es und veröffentlichen Sie die Anpassungen, damit die Änderungen wirksam werden. Wergewissern Sie sich auch, **Clientanpassungen vorbereiten** auszuwählen.  
  
#### <a name="edit-or-delete-individual-streams-of-an-existing-dashboard"></a>Bearbeiten oder Löschen einzelner Streams eines vorhandenen Dashboards  
  
1. Melden Sie sich bei [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an.   
  
2. Wählen Sie **Modellgesteuert** (unten links), **Daten** > **Entitäten** > die gewünschte Entität aus. Wählen Sie auf die Registerkarte **Dashboards** aus.  
  
     -ODER-  
   
   Öffnen Sie den [Projektmappen-Explorer](advanced-navigation.md#solution-explorer) und dann unter **Komponenten** die Option **Dashboards** aus.
  
3.  Wählen Sie im Gitter das interaktive Dashboard aus, das Sie bearbeiten möchten, um es zu öffnen.  
  
4.  Wählen Sie den zu bearbeitenden Stream aus, um ihn auszuwählen, und wählen Sie dann **Komponente bearbeiten** aus.  
  
5.  Abhängig davon, ob Sie dem Stream eine Ansicht oder eine Warteschlange hinzufügen möchten, wählen Sie die Ansichts- oder die Warteschlangendetails für den Stream aus, und wählen Sie dann **Festlegen** aus.  
  
6.  Wählen Sie **Speichern** aus.  
  
 Sie können einen einzelnen Stream auch aus einem Dashboard löschen. Wählen Sie dazu den Stream aus, und wählen Sie dann auf der Befehlsleiste die Option **Löschen** aus.  
  
### <a name="configure-an-entity-specific-dashboard"></a>Konfigurieren eines entitätsspezifischen Dashboards  
 Ein entitätsspezifisches Dashboard ist ein Streamübersichts-Dashboard. Das Konfigurieren dieses Dashboard verläuft ähnlich wie das Konfigurieren eines Homepage-Streamübersichts-Dashboards, aber es geschieht an einer anderen Position der Benutzeroberfläche und es gibt weitere kleine Unterschiede. Anstatt eine Entität auszuwählen, sind beispielsweise einige Felder im entitätsspezifischen Dashboard für die Entität, für die Sie das Dashboard erstellen, voreingestellt.  
  
1.  Melden Sie sich bei [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an.

2.  Wählen Sie **Modellgesteuert** (unten links) aus.  
  
3.  Wählen Sie **Daten** > **Entitäten** > die gewünschte Entität aus. 

4.  Wählen Sie die Registerkarte **Dashboards** und anschließend auf der Symbolleiste die Option **Dashboard hinzufügen** aus.  
  
5.  Wählen Sie das Layout aus, entweder mit einer Spaltenbreite von 2, 3 oder 4.    
  
6.  Wenn das Dashboardformular geöffnet wird, wird für **Filternentitäten** die Entität vorgeeinstellt, für die Sie das Dashboard erstellen. Die **Entitätsansicht** Dropdownliste enthält die verfügbaren Ansichten für die Entität. Wählen Sie die Ansicht aus und füllen Sie restlichen erforderlichen Informationen auf der Seite aus.  
  
 Der Rest des Setups ähnelt sehr der Einrichtung des Streamübersichts-Homepage-Dashboards, die im vorherigen Abschnitt beschrieben wurde.  
  
### <a name="configure-a-single-stream-dashboard"></a>Konfigurieren eines Streamdetail-Dashboards  
 Das Konfigurieren eines Streamdetail-Dashboard verläuft ähnlich wie das Konfigurieren von Streamübersichts-Dashboard. Alle Benutzeroberfläche-Navigationsschritte sind identisch beispielsweise wie das Streamübersichts-Dashboard. Sie können ein Layout mit Kacheln oder ohne Kacheln wählen. Wenn die Kacheln enthalten sind, werden sie immer im Dashboard angezeigt. Um eine Kachel zu konfigurieren, wählen Sie das Symbol in der Mitte Kachel aus. Wenn das Fenster **Kachel hinzufügen** angezeigt wird, geben Sie die erforderlichen Daten ein. Die folgende Abbildung zeigt ein Beispiel für ein Kachel-Setup.  
  
 ![Einem Streamdetail-Dashboard eine Kachel hinzufügen.](../model-driven-apps/media/interactive-dashboard-add-tile-single-stream.png "Einem Streamdetail-Dashboard eine Kachel hinzufügen.")  
  
<a name="BKMK_ConfigureColors"></a>   
## <a name="configure-dashboard-colors"></a>Dashboardfarben konfigurieren  
 Für alle Typfelder wie **Optionssatz** und **Zwei Optionen** , wie **Anfragetyp**, **IsEscalated** oder **Priorität** der `Case`-Entität, können Sie eine bestimmte Farbe konfigurieren, die in Diagrammen und Streams für bestimmte Feldwerte angezeigt wird. Beispielsweise können Anfragen mit hoher Priorität im interaktiven Diagramm in Rot angezeigt werden, Anfragen mit mittlerer Priorität in Blau und solche mit geringer Priorität in Grün. In den Streams befindet sich eine dünne vertikale Linie in Farbe neben der Arbeitselementbeschreibung.  
  
> [!NOTE]
>  Die Farbkennzeichnung ist für die Tagdiagramme und -Ringdiagramme verfügbar. Diese Diagramme erscheinen auf dem Dashboard in Weiß, Grau und Schwarz.  
  
1.  Öffnen Sie den [Lösungs-Explorer](advanced-navigation.md#solution-explorer).  
2.  Erweitern Sie unter **Komponenten** den Ordner **Entitäten**, und erweitern Sie dann die gewünschte Entität. Wenn die gewünschte Entität nicht angezeigt wird, wählen Sie **Vorhandenes Element hinzufügen** aus, um sie hinzuzufügen.  
  
3.  Wählen Sie im Navigationsbereich die Option **Felder** aus. Doppelklicken Sie im Raster auf das Feld, dessen Farbe Sie konfigurieren möchten.  
  
4.  Wählen Sie auf der Registerkarte **Allgemein** im Teilbereich **Typ** die Option **Ja** aus, und wählen Sie anschließend **Bearbeiten** aus.  
  
5.  Wenn das Dialogfeld **Listenwert ändern** angezeigt wird, geben Sie im Textfeld **Farbe** den neuen Wert ein. Wählen Sie **OK** aus.  
  
     Klicken Sie auf **Speichern und schließen**.  
  
7.  Wählen Sie **Veröffentlichen** aus, damit die Änderungen wirksam werden.  
  
Im folgenden Beispiel ändern wir die Farbe für das Feld **IsEscalated**. Verwenden der Schaltfläche **Bearbeiten**, um das Dialogfeld **Listenwert ändern** zu öffnen:  
 
 > [!div class="mx-imgBorder"] 
 > ![Farbe im Dashboard ändern](../model-driven-apps/media/interactive-dashboards-change-color-edit-button.PNG "Farbe im Dashboard ändern")  
  
Wenn das Dialogfeld **Listenwert bearbeiten** angezeigt wird, wählen Sie die Farbe, wie hier gezeigt:  
  
 ![Die Dashboard-Farbe ändern](../model-driven-apps/media/interactive-dashboards-modify-color-value.png "Die Dashboard-Farbe ändern")  
  
### <a name="next-steps"></a>Nächste Schritte  
 
[Erstellen oder Bearbeiten eines Dashboards](create-edit-dashboards.md)
 

