---
title: Erstellen und Bearbeiten von öffentlichen Ansichten oder Systemansichten für modellgesteuerte Apps mithilfe des App-Designers mit PowerApps | MicrosoftDocs
description: 'Erfahren Sie jetzt, wie Ansichten mithilfe des App-Designers erstellt oder bearbeitet werden'
keywords: ''
ms.date: 05/24/2018
ms.service: crm-online
ms.custom: null
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
author: Mattp123
ms.assetid: 666ab3f3-abda-468c-b248-3a0b410286b0
ms.author: matp
manager: kvivek
ms.reviewer: null
ms.suite: null
ms.tgt_pltfrm: null
caps.latest.revision: 1
topic-status: Drafting
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="tutorial-create-and-edit-public-or-system-model-driven-app-views-by-using-the-app-designer"></a>Lernprogramm: Erstellen und Bearbeiten von öffentlichen oder Systemansichten für modellgesteuerte Apps mit dem App-Designer

In diesem Lernprogramm führen Sie mehrere Aufgaben aus, die erforderlich sind, um mit Ansichten zu arbeiten, z. B. Erstellen einer öffentliche Ansicht, Hinzufügen einer vorhandene Ansicht zu einer App und Ändern von Spalten, Filtern und der Sortierreihenfolge für eine Ansicht.

In PowerApps-Ansichten definieren Sie, wie Datensätze für eine bestimmten Entität angezeigt werden. Mit einer Ansicht wird Folgendes definiert:
-  Die anzuzeigenden Spalten (Attribute)
-  Die Breite der Spalten
-  Wie die Datensätze standardmäßig sortiert werden
-  Welche Filter angewendet werden sollen, um zu bestimmen, welche Datensätze standardmäßig in der Liste angezeigt werden

Üblicherweise werden Ansichten in drei Typen klassifiziert:
- **Persönlich:** Einzelne Benutzer können persönliche Ansichten gemäß ihren persönlichen Anforderungen erstellen. Diese Ansichten werden nur dem Benutzer angezeigt, der sie erstellt hat, und jeder anderen Person, für die der Ersteller sie freigibt. 
- **Öffentlich:** Als App-Entwickler können Sie öffentliche Ansichten erstellen und bearbeiten, sodass sie Ihren organisatorischen Anforderungen entsprechen. Diese Ansichten sind verfügbar in der Ansichtsauswahl, und Sie können sie in Unterrastern in einem Formular oder als Liste in einem Dashboard verwenden.
- **System:** Als App-Entwickler können Sie Systemansichten auch ändern, um die Anforderungen Ihrer Organisation zu erfüllen. Dies sind spezielle Ansichten, von denen die Anwendung abhängig ist: Sie existieren für Systementitäten oder werden automatisch erstellt, wenn Sie benutzerdefinierte Entitäten erstellen. Diese Ansichten sind für einige oder alle Benutzer verfügbar, abhängig von den Berechtigungen.

Weitere Informationen: [Grundlegendes zu Ansichten](create-edit-views.md)

## <a name="create-a-public-view-in-powerapps"></a>Erstellen oder Bearbeiten einer öffentlichen Ansicht in PowerApps
Als App-Entwickler können Sie öffentliche Ansichten mithilfe von PowerApps erstellen und bearbeiten.
1. Wählen Sie auf der Seite [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) die Option **Modellgesteuert** (unterer linker Teil des Navigationsbereichs).  

     ![Modellgesteuerter Entwurfsmodus](media/model-driven-switch.png)

    > [!IMPORTANT]
    > "Wenn der **Modell-angetrieben** Entwurfsmodus nicht verfügbar ist, müssen Sie ggf eine [Umgebung erstellen](https://docs.microsoft.com/powerapps/administrator/create-environment).   
  
2.  Erweitern Sie **Daten** und wählen **Entitäten**, wählen Sie die Entität aus und wählen Sie die Registerkarte **Anzeigen**. 

3. Wählen Sie **Ansicht hinzufügen** in der Symbolleiste. 

4. Geben Sie im Dialogfeld **Eigenschaften anzeigen** einen Namen und optional eine Beschreibung ein und wählen Sie dann **OK** aus. 
    
5. Wählen Sie im Ansicht-Designer **Spalten hinzufügen** aus, um weitere Spalten hinzuzufügen, die in der Ansicht angezeigt werden sollen. Weitere Informationen: [Hinzufügen einer Spalte zu einer Ansicht](#add-a-column-to-your-view)
6. Wählen Sie **Filterkriterien bearbeiten** aus, um die Filterung auf folgende Weise zu ändern: 
    -  Um Filterkriterien anzuwenden, um Daten verfeinern, die in der Ansicht angezeigt werden. Weitere Informationen: [Definieren von Filterkriterien](#define-filter-criteria). 
    - Zum Gruppieren der Filter mit den Optionen **UND** oder **ODER**, und um die Daten, die in der Ansicht angezeigt werden, noch weiter einzugrenzen. Weitere Informationen: [Mehrere Filter gruppieren](#group-multiple-filters)
7. Wählen Sie **Sortierung gruppieren** aus, um die Reihenfolge der Daten zu ändern, indem Sie die primäre und sekundäre Sortierreihenfolge für Spalten konfigurieren. Weitere Informationen: [Festlegen der primären und sekundären Sortierreihenfolge für Spalten](#set-primary-and-secondary-sort-order-for-columns)
8. (Optional) Konfigurieren Sie die Spaltenbreite: 
  
    a. Wählen Sie eine Spalte aus. Die Registerkarte **Eigenschaften** wird geöffnet.
    
    b. Konfigurieren Sie **Breite festlegen** mit der Spaltenbreite, die angezeigt werden soll.
    
    > [!NOTE]
    > Der Spaltenbreitenwert reicht von 25 Pixel bis 300 Pixel.
9. (Optional) Ändern Sie die Reihenfolge der Spalten, indem Sie eine Spalte an die Position ziehen, an die Sie sie verschieben möchten. 

    Sie sehen eine visuelle Anzeige, wenn Sie die Spalte über eine Position halten, an die sie verschoben werden kann.

    ![Ändern der Spaltenreihenfolge](media/ViewAppDesigner_ReorderColumn.png "Ändern der Spaltenreihenfolge in einer Ansicht")

    > [!NOTE]
    > Sie können auch die Spaltenreihenfolge ändern, indem Sie Tastenkombinationen verwenden. Schneiden Sie eine Spalte aus, indem Sie Strg+X drücken und eine Spalte auswählen. Fügen Sie sie dann ein, indem Sie Strg+V drücken. Die Spalte wird an die Position rechts neben der ausgewählten Spalte verschoben.
10. (Optional) Fügen Sie ein Symbol oder eine Datei an eine Spalte an, um von anderen Spalten während der Laufzeit zu unterscheiden. Weitere Informationen: [Definieren einer Webressource](#define-a-web-resource)
11. **Speichern und schließen** Sie die Ansicht. 
12. Wählen Sie **Veröffentlichen**, um die Ansicht für andere Benutzer der Organisation bereitzustellen. 
   

## <a name="open-and-add-a-view-in-the-app-designer"></a>Öffnen und Hinzufügen einer Ansicht im App-Designer

Im Folgenden wird erläutert, wie Sie eine Ansicht im App-Designer öffnen und hinzufügen.
1. Wählen Sie im Projektmappen-Explorer die Option **Apps** aus, und wählen Sie dann die App aus, die Sie bearbeiten möchten, um sie im App-Designer zu öffnen. 

2. Wählen Sie im Abschnitt **Entitätsansicht** die Option **Ansichten** aus.

    In diesem Beispiel haben wir **Ansichten** der Entität **Firma** ausgewählt.

    ![App-Designer-Ansicht](media/ViewAppDesigner_AccountAppDesignerView.png "App-Designer-Ansicht der Firmenentität")

3. Wenn eine Ansicht hinzugefügt werden soll, wählen Sie sie unter Verwendung von Ansichtstypen wie „Öffentlich, „Erweiterte Suche“, „Zugeordnet“ und „Suche“ aus. Die Ansicht wird der Liste **Ansichten** automatisch hinzugefügt.

    > [!NOTE]
    > Ansichten werden basierend auf der Entität angezeigt, die Sie ausgewählt haben. Wenn Sie beispielsweise **Firma** auswählen, werden Ansichten, die mit der Firmenentität verknüpft sind, angezeigt.

Weitere Informationen zum App-Designer: [Gestalten Sie benutzerdefinierte Unternehmens-Apps mit dem App Designer](design-custom-business-apps-using-app-designer.md)


## <a name="add-a-column-to-your-view"></a>Hinzufügen einer Spalte zu einer Ansicht
In Ansichten werden Datensätze in einer Tabelle angezeigt, die Zeilen und Spalten enthalten. Jede Zeile stellt einen Datensatz dar, und die Felder, die Sie aus dem Datensatz anzeigen, werden durch die Spalten bestimmt, die Sie der Ansicht hinzufügen.

1. Wählen Sie im App-Designer auf der Registerkarte **Komponenten** die Liste **Spaltenattribute** entweder für **Primäre Entität** oder **Verknüpfte Entität** aus.

    ![Hinzufügen einer Spalte](media/ViewAppDesigner_AddColumn.png "Hinzufügen einer Spalte zu einer Ansicht") 

2. Wählen Sie in der Liste das gewünschte Attribut aus, und ziehen Sie es auf die Spaltenüberschrift. Sie können das Attribut auch hinzufügen, indem Sie darauf doppelklicken.
3. Wiederholen Sie Schritt 2, bis Sie alle Attribute hinzugefügt haben, die in die Ansicht angezeigt werden sollen.

Wenn Sie Attribute hinzufügen, ziehen Sie sie an eine Position unter den vorhandenen Spaltenüberschriften. Sie können auch Spalten verschieben, nachdem Sie sie der Ansicht hinzugefügt haben.


## <a name="define-filter-criteria"></a>Definieren von Filterkriterien
Sie können Filterkriterien festlegen, sodass nur eine Teilmenge der Datensätze in einer Ansicht angezeigt wird. Wenn ein Benutzer die Ansicht öffnet, werden nur Datensätze angezeigt, die den definierten Filterkriterien entsprechen. Sie können Felder der primären und der verknüpften Entitäten auswählen, nach denen gefiltert werden soll.
1. Im App-Designer erweitern Sie den Abschnitt **Filterkriterien**.
   
    ![Festlegen von Filterkriterien](media/ViewAppDesigner_FilterCriteria.png "Festlegen von Filterkriterien") 

2. Wählen Sie **Filter hinzufügen** aus.
3. Wählen Sie ein Attribut aus der Dropdownliste der ersten Spalte aus. 
4. Wählen Sie einen Operator aus der Dropdownliste der zweiten Spalte aus.

    ![Festlegen eines Operators für Filterkriterien](media/ViewAppDesigner_FilterCriteriaOption.png "Festlegen eines Operators für Filterkriterien")

5. Geben Sie einen Wert für den Filter in der dritten Spalte ein.

Zusätzlich zur primären Entität können Sie Daten basierend auf den Attributen von verknüpften Entitäten filtern. 

1. Wählen Sie auf der Registerkarte **Komponenten** die Liste **Spaltenattribute** für **Verknüpfte Entität** aus. Wählen Sie den Pfeil nach unten **Entität wählen** im obersten Feld und dann die gewünschte Entität aus.

    Dadurch wird ein separater Abschnitt hinzugefügt.

2. Wiederholen Sie die Schritte 2 bis 5 aus dem vorherigen Verfahren.

Weitere Informationen: [Erstellen und Bearbeiten von Beziehungen zwischen Entitäten](../common-data-service/create-edit-entity-relationships.md)

## <a name="group-multiple-filters"></a>Gruppieren mehrerer Filter
Sie können der Ansicht mehrere Filter hinzufügen, wenn Sie Datensätze filtern möchten, indem Sie mehr als ein Feld verwenden. 

1. Wählen Sie die zu gruppierenden Filter aus.
    ![Festlegen von Gruppenfiltern](media/ViewAppDesigner_GroupFilter.png "Festlegen von Gruppenfiltern")
2. Wählen Sie „Gruppieren Und“ oder „Gruppieren Oder“ aus, um die Filter zu gruppieren.
    ![Gruppieren der Filterauswahl](media/ViewAppDesigner_GroupFilterSelection.png "Auswählen eines Gruppenfilters") Bei Auswahl von **Gruppieren Und** werden in der Ansicht nur Datensätze angezeigt, die beiden Kriterien entsprechen. Wenn Sie **Gruppieren Oder** auswählen, werden Datensätze, die eines der Filterkriterien erfüllen, angezeigt. Um beispielsweise nur Datensätze mit hoher oder normaler Priorität und dem Status „Aktiv“ anzuzeigen, wählen Sie **Gruppieren Und** aus.

Sie können Filter aus einer Gruppe entfernen, indem Sie die Gruppe auswählen und dann **Gruppierung aufheben** auswählen. 

## <a name="set-primary-and-secondary-sort-order-for-columns"></a>Festlegen der primären und sekundären Sortierreihenfolge für Spalten
Wenn eine Ansicht geöffnet wird, werden die Datensätze, die darin angezeigt werden, in der Reihenfolge sortiert, die Sie festgelegt haben, als Sie die Ansicht erstellt haben.   Standardmäßig werden Datensätze nach der ersten Spalte in einer Ansicht sortiert, wenn keine Sortierreihenfolge ausgewählt ist. Sie können nach einer einzelnen Spalte sortieren oder zwei Spalten auswählen, nach denen sortiert werden soll – eine primäre und eine sekundäre. Wenn die Ansicht geöffnet wird, werden die Datensätze zuerst nach der Spalte sortiert, die Sie für die primäre Sortierreihenfolge verwenden möchten, und dann nach der Spalte, die Sie für die sekundäre Sortierreihenfolge verwenden möchten. 

> [!NOTE]
> Sie können die primäre und die sekundäre Sortierreihenfolge nur für Spaltenattribute festlegen, die Sie von der primären Entität aus hinzugefügt haben.

1. Wählen Sie die Spalte aus, die Sie zum Sortieren verwenden möchten.
2. Wählen Sie den Abwärtspfeil und dann **Primäre Sortierung** oder **Sekundäre Sortierung** aus.
 
    ![Sortieren von Datensätzen](media/ViewAppDesigner_SortRecords.png "Sortieren von Datensätzen basierend auf der primären und sekundären Sortierreihenfolge") 

Wenn Sie die Spalte entfernen, die Sie für die primäre Sortierreihenfolge ausgewählt haben, wird die Spalte, die Sie für die sekundäre Sortierreihenfolge ausgewählt haben, die primäre.

## <a name="define-a-web-resource"></a>Definieren einer Webressource
Geben Sie eine Webressource des Skriptstyps an, die mit einer Spalte in der Ansicht verknüpft werden soll. Mit diesen Skripts können Symbole für Spalten angezeigt werden.

1. Wählen Sie die Spalte aus, der Sie eine Webressource hinzufügen möchten.
2. Wählen Sie auf der Registerkarte **Eigenschaften** die Option **Erweitert** aus.
3. Wählen Sie in der Dropdownliste **Webressource** die Webressource, die Sie verwenden möchten.
4. Geben Sie im Feld **Funktionsname** einen Funktionsnamen ein.

## <a name="edit-a-public-or-system-view"></a>Bearbeiten einer öffentlichen Ansicht oder Systemansicht
Sie können die Darstellung einer öffentlichen oder Systemansicht ändern, indem Spalten hinzugefügt, konfiguriert oder entfernt werden.
1. Wählen Sie in der Liste **Ansichten** für eine Entität den Dropdownpfeil **Verweisliste anzeigen** ![Dropdown](media/DownArrow.png "Dropdownpfeil") aus.
    ![Bearbeiten einer Ansicht](media/ViewAppDesigner_EditView.png "Bearbeiten einer öffentlichen Ansicht oder Systemansicht")
2. Wählen Sie neben der zu bearbeitenden Ansicht die Option **Ansicht-Designer öffnen** ![Ansicht-Designer öffnen](media/dynamics365-open-designer.png "Ansicht-Designer öffnen") aus. 

    Die Ansicht wird im Ansicht-Designer geöffnet. 

Wenn Sie eine öffentliche oder Systemansicht bearbeiten, müssen Sie Ihre Änderungen speichern und veröffentlichen, bevor sie in der Anwendung sichtbar sind.


## <a name="community-tools"></a>Community-Tools
**Ansichts-Layout-Replikator** und **Ansicht-Designer** sind die Tools, die von der XrmToolbox-Community für Dynamics 365 Customer Engagement entwickelt wurden.

Weitere Informationen: [Entwicklertools](https://docs.microsoft.com/dynamics365/customer-engagement/developer/developer-tools).

> [!NOTE]
> Diese Tools werden von XrmToolBox bereitgestellt und werden nicht von Microsoft unterstützt. Wenn Sie Fragen zu dem Tool haben, setzen Sie sich bitte mit dem Herausgeber in Verbindung. Weitere Informationen: [XrmToolBox](https://www.xrmtoolbox.com/). 

### <a name="next-steps"></a>Nächste Schritte
[1:N (1: n) oder N:1-Beziehungen erstellen](../common-data-service/create-edit-1n-relationships.md)
