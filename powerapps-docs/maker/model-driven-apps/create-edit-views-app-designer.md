---
title: Erstellen und Bearbeiten von öffentlichen Ansichten oder Systemansichten für modellgesteuerte Apps mit Power Apps | MicrosoftDocs
description: Erfahren Sie jetzt, wie Ansichten mithilfe des App-Designers erstellt oder bearbeitet werden
keywords: ''
ms.date: 03/23/2020
ms.service: powerapps
ms.custom: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: 666ab3f3-abda-468c-b248-3a0b410286b0
ms.author: matp
manager: kvivek
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
caps.latest.revision: 1
topic-status: Drafting
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 10aa1623cbc3ff90788257641afd71ac0e149375
ms.sourcegitcommit: 9f2694bd14d70798310b89a4673672c1bfad989d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/26/2020
ms.locfileid: "3166836"
---
# <a name="create-and-edit-public-or-system-model-driven-app-views"></a>Erstellen und Bearbeiten von öffentlichen Ansichten oder Systemansichten für modellgesteuerte Apps

In diesem Thema führen Sie mehrere Aufgaben aus, die erforderlich sind, um mit Ansichten zu arbeiten, z. B. Erstellen einer öffentliche Ansicht, Hinzufügen einer vorhandene Ansicht zu einer App und Ändern von Spalten, Filtern und der Sortierreihenfolge für eine Ansicht.

In Power Apps definieren Ansichten, wie Datensätze für eine bestimmten Entität angezeigt werden. Mit einer Ansicht wird Folgendes definiert:
-  Die anzuzeigenden Spalten (Attribute)
-  Die Breite der Spalten
-  Wie die Datensätze standardmäßig sortiert werden
-  Welche Filter angewendet werden sollen, um zu bestimmen, welche Datensätze standardmäßig in der Liste angezeigt werden

Üblicherweise werden Ansichten in drei Typen klassifiziert:
- **Persönlich:** Einzelne Benutzer können persönliche Ansichten gemäß ihren persönlichen Anforderungen erstellen. Diese Ansichten werden nur dem Benutzer angezeigt, der sie erstellt hat, und jeder anderen Person, für die der Ersteller sie freigibt. 
- **Öffentlich:** Als App-Entwickler können Sie öffentliche Ansichten erstellen und bearbeiten, sodass sie Ihren organisatorischen Anforderungen entsprechen. Diese Ansichten sind verfügbar in der Ansichtsauswahl, und Sie können sie in Unterrastern in einem Formular oder als Liste in einem Dashboard verwenden.
- **System:** Als App-Entwickler können Sie Systemansichten auch ändern, um die Anforderungen Ihrer Organisation zu erfüllen. Dies sind spezielle Ansichten, von denen die Anwendung abhängig ist: Sie existieren für Systementitäten oder werden automatisch erstellt, wenn Sie benutzerdefinierte Entitäten erstellen. Diese Ansichten sind für einige oder alle Benutzer verfügbar, abhängig von den Berechtigungen.

Weitere Informationen: [Grundlegendes zu Ansichten](create-edit-views.md)

## <a name="create-a-public-view-in-power-apps"></a>Erstellen einer öffentlichen Ansicht in Power Apps
Als App-Entwickler können Sie öffentliche Ansichten mithilfe von Power Apps erstellen und bearbeiten.
1. Melden Sie sich bei [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an.  

2.  Erweitern Sie **Daten** und wählen **Entitäten**, wählen Sie die Entität aus und wählen Sie die Registerkarte **Anzeigen**. 

3. Wählen Sie **Ansicht hinzufügen** in der Symbolleiste. 

4. Geben Sie im Dialogfeld **Erstellen einer Ansicht** einen Namen und optional eine Beschreibung ein und wählen Sie dann **OK** aus. 
    
5. Wählen Sie im Ansicht-Designer die Plus-Schaltfläche aus, um weitere Spalten hinzuzufügen, die in der Ansicht angezeigt werden sollen. Weitere Informationen: [Hinzufügen einer Spalte zur Anzeige im App-Designer](#add-a-column-to-your-view-in-app-designer) 

   ![Spalte hinzufügen](../common-data-service/media/add-column-to-view.png)

6. Im Ansicht-Designer können Sie die folgenden Aufgaben ausführen: 
   - Um die Spaltenfilterung zu ändern wählen Sie die Kopfzeile der Spalte, die Sie filtern wollen und dann im Dropdown **Filtern nach**.
   - Um die Spaltensortierung zu ändern, wählen Sie die Kopfzeile der Spalte, die Sie filtern wollen und dann **Sortieren A-Z** oder **Sortieren Z-A**.
   - Konfigurieren Sie die Spaltenbreite, indem Sie auf die Spalte klicken und sie auf die die gewünschte Position ziehen.
   - Ändern Sie die Reihenfolge der Spalten, indem Sie eine Spalte an die Position ziehen, an die Sie sie verschieben möchten. 

    > [!NOTE]
    > Sie können die Spaltenreihenfolge auch ändern, indem Sie auf die Spaltenüberschrift klicken und **Nach rechts** oder **Nach links** auswählen.

10. Wählen Sie **Veröffentlichen**, um die Ansicht zu speichern und für andere Benutzer der Organisation bereitzustellen. 
   

## <a name="work-with-views-in-app-designer"></a>Verwenden von Ansichten im App-Designer
Die folgenden Abschnitte beschreiben, wie Sie Ansichten im App-Designer erstellen und bearbeiten.

### <a name="open-and-add-a-view-in-the-app-designer"></a>Öffnen und Hinzufügen einer Ansicht im App-Designer

Im Folgenden wird erläutert, wie Sie eine Ansicht im App-Designer öffnen und hinzufügen.
1. Wählen Sie in Power Apps die Option **Apps** aus dem linken Navigationsbereich **...** neben der gewünschten App und dann **Bearbeiten** aus. 

2. Wählen Sie im App-Designer im Abschnitt **Entitätsansicht** die Option **Ansichten** aus.

    In diesem Beispiel haben wir **Ansichten** der Entität **Firma** ausgewählt.

    ![App-Designer-Ansicht](media/ViewAppDesigner_AccountAppDesignerView.png "App-Designer-Ansicht der Entität Konto")

3. Wenn eine Ansicht hinzugefügt werden soll, wählen Sie sie unter Verwendung von Ansichtstypen wie „Öffentlich, „Erweiterte Suche“, „Zugeordnet“ und „Suche“ aus. Die Ansicht wird der Liste **Ansichten** automatisch hinzugefügt.

    > [!NOTE]
    > Ansichten werden basierend auf der Entität angezeigt, die Sie ausgewählt haben. Wenn Sie beispielsweise **Firma** auswählen, werden Ansichten, die mit der Firmenentität verknüpft sind, angezeigt.

Weitere Informationen zum App-Designer: [Gestalten Sie benutzerdefinierte Unternehmens-Apps mit dem App Designer](design-custom-business-apps-using-app-designer.md)


### <a name="add-a-column-to-your-view-in-app-designer"></a>Fügen Sie Ihrer Ansicht im App-Designer eine Spalte hinzu
In Ansichten werden Datensätze in einer Tabelle angezeigt, die Zeilen und Spalten enthalten. Jede Zeile stellt einen Datensatz dar, und die Felder, die Sie aus dem Datensatz anzeigen, werden durch die Spalten bestimmt, die Sie der Ansicht hinzufügen.

1. Wählen Sie im App Designer die gewünschte Entitäts-Ansicht und dann Bearbeiten im rechten Bereich neben der Ansicht, die Sie bearbeiten möchten (Zeichenstiftschaltfläche).  
2. Wählen Sie auf der Registerkarte **Komponenten** die Liste **Spaltenattribute** entweder für **Primäre Entität** oder **Verknüpfte Entität** aus.

    ![Hinzufügen einer Spalte](media/ViewAppDesigner_AddColumn.png "Hinzufügen einer Spalte zu einer Ansicht") 

3. Wählen Sie in der Liste das gewünschte Attribut aus, und ziehen Sie es auf die Spaltenüberschrift. Sie können das Attribut auch hinzufügen, indem Sie darauf doppelklicken.
4. Wiederholen Sie Schritt 3, bis Sie alle Attribute hinzugefügt haben, die in der Ansicht angezeigt werden sollen.

Wenn Sie Attribute hinzufügen, ziehen Sie sie an eine Position unter den vorhandenen Spaltenüberschriften. Sie können auch Spalten verschieben, nachdem Sie sie der Ansicht hinzugefügt haben.


### <a name="define-filter-criteria-in-app-designer"></a>Definieren von Filterkriterien im App-Designer
Sie können Filterkriterien festlegen, sodass nur eine Teilmenge der Datensätze in einer Ansicht angezeigt wird. Wenn ein Benutzer die Ansicht öffnet, werden nur Datensätze angezeigt, die den definierten Filterkriterien entsprechen. Sie können Felder der primären und der verknüpften Entitäten auswählen, nach denen gefiltert werden soll.
1. Im App-Designer erweitern Sie den Abschnitt **Filterkriterien**.
   
    ![Filterkriterien einstellen](media/ViewAppDesigner_FilterCriteria.png "Filterkriterien einstellen") 

2. Wählen Sie **Filter hinzufügen** aus.
3. Wählen Sie ein Attribut aus der Dropdownliste der ersten Spalte aus. 
4. Wählen Sie einen Operator aus der Dropdownliste der zweiten Spalte aus.

    ![Filterkriterienoperator einstellen](media/ViewAppDesigner_FilterCriteriaOption.png "Filterkriterienoperator einstellen")

5. Geben Sie einen Wert für den Filter in der dritten Spalte ein.

Zusätzlich zur primären Entität können Sie Daten basierend auf den Attributen von verknüpften Entitäten filtern. 

1. Wählen Sie auf der Registerkarte **Komponenten** die Liste **Spaltenattribute** für **Verknüpfte Entität** aus. Wählen Sie den Pfeil nach unten **Entität wählen** im obersten Feld und dann die gewünschte Entität aus.

    Dadurch wird ein separater Abschnitt hinzugefügt.

2. Wiederholen Sie die Schritte 2 bis 5 aus dem vorherigen Verfahren.

Weitere Informationen: [Erstellen und Bearbeiten von Beziehungen zwischen Entitäten](../common-data-service/create-edit-entity-relationships.md)

#### <a name="group-multiple-filters-in-app-designer"></a>Gruppieren Sie mehrere Filter im App-Designer
Sie können der Ansicht mehrere Filter hinzufügen, wenn Sie Datensätze filtern möchten, indem Sie mehr als ein Feld verwenden. 

1. Wählen Sie die zu gruppierenden Filter aus.
    ![Gruppenfiltern einstellen](media/ViewAppDesigner_GroupFilter.png "Gruppenfiltern festlegen")
2. Wählen Sie „Gruppieren Und“ oder „Gruppieren Oder“ aus, um die Filter zu gruppieren.
    ![Gruppenfilterauswahl](media/ViewAppDesigner_GroupFilterSelection.png "Gruppenfilter auswählen") Bei der Auswahl von **Gruppieren Und** werden in der Ansicht nur Datensätze angezeigt, die beiden Kriterien entsprechen. Wenn Sie **Gruppieren Oder** auswählen, werden Datensätze, die eines der Filterkriterien erfüllen, angezeigt. Um beispielsweise nur Datensätze mit hoher oder normaler Priorität und dem Status „Aktiv“ anzuzeigen, wählen Sie **Gruppieren Und** aus.

Sie können Filter aus einer Gruppe entfernen, indem Sie die Gruppe auswählen und dann **Gruppierung aufheben** auswählen. 

### <a name="set-primary-and-secondary-sort-order-for-columns-in-app-designer"></a>Festlegen der primären und sekundären Sortierreihenfolge für Spalten im App-Designer
Wenn eine Ansicht geöffnet wird, werden die Datensätze, die darin angezeigt werden, in der Reihenfolge sortiert, die Sie festgelegt haben, als Sie die Ansicht erstellt haben.   Standardmäßig werden Datensätze nach der ersten Spalte in einer Ansicht sortiert, wenn keine Sortierreihenfolge ausgewählt ist. Sie können nach einer einzelnen Spalte sortieren oder zwei Spalten auswählen, nach denen sortiert werden soll – eine primäre und eine sekundäre. Wenn die Ansicht geöffnet wird, werden die Datensätze zuerst nach der Spalte sortiert, die Sie für die primäre Sortierreihenfolge verwenden möchten, und dann nach der Spalte, die Sie für die sekundäre Sortierreihenfolge verwenden möchten. 

> [!NOTE]
> Sie können die primäre und die sekundäre Sortierreihenfolge nur für Spaltenattribute festlegen, die Sie von der primären Entität aus hinzugefügt haben.

1. Wählen Sie die Spalte aus, die Sie zum Sortieren verwenden möchten.
2. Wählen Sie den Abwärtspfeil und dann **Primäre Sortierung** oder **Sekundäre Sortierung** aus.
 
    ![Sortieren von Datensätzen](media/ViewAppDesigner_SortRecords.png "Sortieren von Datensätzen basierend auf der primären und sekundären Sortierreihenfolge") 

Wenn Sie die Spalte entfernen, die Sie für die primäre Sortierreihenfolge ausgewählt haben, wird die Spalte, die Sie für die sekundäre Sortierreihenfolge ausgewählt haben, die primäre.

### <a name="define-a-web-resource-in-app-designer"></a>Definieren einer Webressource im Anwendungs-Designer
Geben Sie eine Webressource des Skriptstyps an, die mit einer Spalte in der Ansicht verknüpft werden soll. Mit diesen Skripts können Symbole für Spalten angezeigt werden.

1. Wählen Sie die Spalte aus, der Sie eine Webressource hinzufügen möchten.
2. Wählen Sie auf der Registerkarte **Eigenschaften** die Option **Erweitert** aus.
3. Wählen Sie in der Dropdownliste **Webressource** die Webressource, die Sie verwenden möchten.
4. Geben Sie im Feld **Funktionsname** einen Funktionsnamen ein.

### <a name="edit-a-public-or-system-view-in-app-designer"></a>Bearbeiten einer öffentlichen- oder einer Systemansicht im Anwendungs-Designer
Sie können die Darstellung einer öffentlichen oder Systemansicht ändern, indem Spalten hinzugefügt, konfiguriert oder entfernt werden.
1. Wählen Sie in der Liste **Ansichten** für eine Entität den Dropdownpfeil **Verweisliste anzeigen** ![Dropdown](media/DownArrow.png "Dropdownpfeil") aus.
    ![Ansicht bearbeiten](media/ViewAppDesigner_EditView.png "Bearbeiten einer öffentlichen Ansicht oder Systemansicht")
2. Wählen Sie neben der zu bearbeitenden Ansicht die Option **Ansicht-Designer öffnen** ![Ansicht-Designer öffnen](media/dynamics365-open-designer.png "Ansicht-Designer öffnen") aus. 

    Die Ansicht wird im Ansicht-Designer geöffnet. 

Wenn Sie eine öffentliche oder Systemansicht bearbeiten, müssen Sie Ihre Änderungen speichern und veröffentlichen, bevor sie in der Anwendung sichtbar sind.


## <a name="community-tools"></a>Community-Tools
**Ansichts-Layout-Replikator** und **Ansicht-Designer** sind die Tools, die von der XrmToolbox-Community für Power Apps-Apps entwickelt wurden.

Weitere Informationen: [Entwicklertools](/powerapps/developer/common-data-service/developer-tools).

> [!NOTE]
> Diese Tools werden von XrmToolBox bereitgestellt und werden nicht von Microsoft unterstützt. Wenn Sie Fragen zu dem Tool haben, setzen Sie sich bitte mit dem Herausgeber in Verbindung. Weitere Informationen: [XrmToolBox](https://www.xrmtoolbox.com/). 

### <a name="next-steps"></a>Nächste Schritte
[1:N (1: n) oder N:1-Beziehungen erstellen](../common-data-service/create-edit-1n-relationships.md)
