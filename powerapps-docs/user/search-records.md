---
title: Suchen nach Datensätzen in Modell gesteuerten apps | MicrosoftDocs
ms.custom: ''
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 10/03/2019
ms.author: mduelae
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 26903543232025f43f935a403800ed27170e3123
ms.sourcegitcommit: 7c46e7ce889e2f1c5352ed2e705b0bb8968f2a89
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71941006"
---
# <a name="search-for-records-in-an-app"></a>Suchen nach Datensätzen in einer APP

Mithilfe der relevanzsuche oder der kategorisierten Suche in Common Data Service können Sie nach Datensätzen in mehreren Entitäten suchen. 

- Die relevanzsuche liefert schnelle und umfassende Ergebnisse für mehrere Entitäten in einer einzigen Liste, sortiert nach Relevanz. Der Dienst verwendet einen dedizierten Suchdienst, der extern Common Data Service (durch [!INCLUDE[pn_Windows_Azure](../includes/pn-windows-azure.md)]) verwendet wird, um die Suchleistung zu verbessern. 
- Die kategorisierte Suche gibt Suchergebnisse gruppiert nach Entitäts Typen zurück, z. b. Konten, Kontakte oder Leads.

Normalerweise ist die kategorisierte Suche die Standard Suchoption. Wenn die relevanzsuche jedoch von Ihrer Organisation aktiviert ist, wird Sie zur standardmäßigen Suchfunktion.  

Wenn Sie nur Datensätze von einem Typ suchen möchten, können Sie die Ansicht Schnellsuche im Raster der Entität verwenden.
  
## <a name="normal-quick-find-categorized-search"></a>Normale Schnellsuche (kategorisierte Suche) 

Mit "kategorisiert" können Sie Datensätze durchsuchen, die mit einem bestimmten Wort beginnen oder einen Platzhalter verwenden.
  
- **Beginnt mit**: Zu den Ergebnissen zählen Datensätze, die mit einem bestimmten Wort beginnen. Wenn Sie z. b. nach "Alpine Ski House" suchen möchten, geben Sie " **Alm** " in das Suchfeld ein. Wenn Sie **Ski**eingeben, wird der Datensatz nicht angezeigt.  
  
- Platz **Halter:** Beispiel: * Ski oder * Ski @ no__t-0. 
  
## <a name="relevance-search"></a>Relevanzsuche
  
  Die relevanzsuche ist zusätzlich zu anderen Common Data Service suchen verfügbar, mit denen Sie bereits vertraut sind. Sie können die Schnellsuche mit einer einzelnen Entität im Entity Grid oder in der multientity-Schnellsuche (als kategorisierte Suche bezeichnet) weiter verwenden, wenn die relevanzsuche aktiviert ist. Um umfassendere und schnellere Ergebnisse zu erzielen, empfehlen wir die Verwendung der relevanzsuche.  

 Die relevanzsuche bietet die folgenden Verbesserungen und Vorteile:  
  
- Verbessert die Leistung mit externer Indizierung und [!INCLUDE[pn_azure_shortest](../includes/pn-azure-shortest.md)]-Suchtechnologie.  
  
- Findet Übereinstimmungen mit einem beliebigen Wort im Suchbegriff in einem beliebigen Feld in der Entität. Übereinstimmungen können flektionale Wörter wie **Stream**, **Streaming oder Streaming**einschließen.  
  
- Gibt Ergebnisse aus allen durchsuchbaren Entitäten in einer einzelnen Liste nach Relevanz sortiert zurück, basierend auf Faktoren wie der Anzahl von übereinstimmenden Wörtern oder Ihrer Nähe zueinander im Text.  
  
- Markiert die Übereinstimmungen in der Ergebnisliste.  

- Sie finden Suchergebnisse für Text in einem Dokument, das in Common Data Service gespeichert ist, einschließlich Text in Notizen, e-Mail-Anlagen oder Terminen. Die folgenden Dateiformate werden für die Suche unterstützt: PDF, Microsoft Office Dokumente, HTML, XML, ZIP, eml, Plain Text und JSON.  
  
- Sie können nach Datensätzen suchen, die für Sie freigegeben wurden, sowie auf Datensätze, die Sie besitzen.  
  
  > [!NOTE]
  >  Hierarchische Sicherheitsmodelle werden nicht unterstützt.  Auch wenn eine Zeile in Common Data Service angezeigt wird, weil Sie über hierarchische Sicherheit darauf zugreifen können, wird das Ergebnis nicht in der relevanzsuche angezeigt.  
  
- Sie können auch nach Options Sätzen und Lookups suchen. Nehmen wir beispielsweise an, Sie möchten ein Einzelhandelsgeschäfts Konto suchen, das über **Pharmaceuticals** im Namen verfügt. Wenn Sie nach dem **pharmazeutischen Einzelhandel**suchen, finden Sie das Ergebnis, weil es eine Entsprechung für das Feld "Industry" gibt, bei dem es sich um eine durchsuchbare Option handelt.  
  
  Da Ihre Ergebnisse eine Mischung aus Entitäten enthalten können, können Sie die Suchergebnisse auf eine bestimmte Entität eingrenzen, indem Sie in der Dropdown Liste **Filter mit** eine Entität auswählen. Wenn Sie nach einem bestimmten Daten Satz Typen filtern, können Sie in den Suchergebnissen Aktivitäten und Notizen für den ausgewählten Datensatz einschließen. Aktivieren Sie hierzu das Kontrollkästchen **Aktivitäten und Notizen für ausgewählte Datensätze suchen** rechts neben der Dropdown Liste **Filter mit** . Das Kontrollkästchen wird aktiviert, nachdem Sie in der Dropdown Liste **Filter mit** einen Datensatz ausgewählt haben. Sie wird gelöscht, wenn Sie keine Entität in der Liste **Filter with** ausgewählt haben. Die Aktivitäten und Notizen werden als Ergebnisse der obersten Ebene zurückgegeben.
  
  > [!NOTE]
  > - Die relevanzsuche ist standardmäßig deaktiviert. Ihr Administrator muss Sie für die Organisation aktivieren. Nachdem die relevanzsuche aktiviert ist, müssen Sie möglicherweise bis zu einer Stunde oder mehr warten, je nach Größe Ihres Unternehmens, bevor Sie mit dem Anzeigen der Ergebnisse der relevanzsuche für Ihre apps beginnen. Kleinere Änderungen an indizierten Daten können bis zu 15 Minuten in Ihrem System angezeigt werden.
  > - Durch Aktivieren der relevanzsuche können alle Benutzer in der Organisation diese verwenden.  
  > - Die relevanzsuche ist Text basiert und kann nur nach Feldern vom Typ "einzelne Textzeile", mehreren Textzeilen, Options Sätzen oder Such Vorgängen suchen. Das Suchen in Feldern vom numerischen Datentyp oder dem Date-Datentyp wird nicht unterstützt. 
  
 Obwohl bei der relevanzsuche Übereinstimmungen mit einem beliebigen Wort im Suchbegriff in einem beliebigen Feld in einer Entität gefunden werden, müssen Sie im Feld "Schnellsuche @ no__t-0", auch wenn die Volltextsuche aktiviert ist @ no__t-1Alle Wörter aus dem Suchbegriff in einem Feld gefunden werden.  
  
 Je besser die Suche in der relevanzsuche, desto höher wird in den Ergebnissen angezeigt. Eine Entsprechung hat eine höhere Relevanz, wenn mehr Wörter aus dem Suchbegriff in unmittelbarer Nähe zueinander gefunden werden. Je kleiner die Text Menge, in der die Suchwörter gefunden werden, desto höher die Relevanz. Wenn Sie z. b. die Suchbegriffe in einem Firmennamen und einer Adresse finden, ist dies möglicherweise eine bessere Übereinstimmung als die Wörter in einem großen Artikel, die weit voneinander getrennt sind. Da die Ergebnisse in einer einzigen Liste zurückgegeben werden, können Sie eine Mischung aus Datensätzen sehen, die nacheinander angezeigt werden, z. b. Konten, Verkaufschancen, Leads usw. Die übereinstimmenden Wörter in der Liste werden hervorgehoben.  
  
 Verwenden Sie die Syntax im Suchbegriff, um die gewünschten Ergebnisse zu erhalten. Geben Sie z. b. **Auto Silver 2-Door** ein, um Übereinstimmungen für jedes Wort im Suchbegriff in den Suchergebnissen einzuschließen. Geben Sie **Car + Silver +2-Door** ein, um nur Übereinstimmungen zu suchen, die alle drei Wörter enthalten. Geben **Sie&#124;Car&#124;Silver 2-Door** ein, um Ergebnisse zu erhalten, die **Auto** , **Silver** oder **2-Door**oder alle drei Wörter enthalten. Weitere Informationen zur Syntax, die Sie in ihren Such Abfragen verwenden können: [Einfache Abfrage Syntax in Azure Search](https://docs.microsoft.com/rest/api/searchservice/simple-query-syntax-in-azure-search)


> [!NOTE]
> Sie sehen Treffer Markierungen, wenn der Suchbegriff mit einem Begriff in Ihrer APP übereinstimmt. Die Treffer Highlights werden in den Suchergebnissen als Fett und kursiv formatierter Text angezeigt. Diese werden häufig als Teil des vollständigen Werts in einem Feld zurückgegeben, da nur die übereinstimmenden Begriffe hervorgehoben werden. 
  
  
<a name=" #BKMK_DefaultOption "></a>
## <a name="switch-between-relevance-and-categorized-search"></a>Zwischen Relevanz und kategorisierter Suche wechseln

Wenn Ihre Organisation sowohl Suchoptionen (Relevanz als auch kategorisierte Suche) aktiviert hat, können Sie zwischen den beiden wechseln.

1. Um zwischen den Suchtypen zu wechseln, wählen Sie auf der Navigationsleiste die Schaltfläche **Suchen** aus.

2. Wählen Sie auf der linken Seite das Dropdown Menü aus, um zwischen der **relevanzsuche** oder der **kategorisierten Suche**zu wechseln.

   > [!div class="mx-imgBorder"]
   > ![Wechsel zwischen Relevanz und kategorisierter Suche](media/switch-search.png "Wechseln zwischen Relevanz und kategorisierter Suche") 
    
### <a name="set-a-default-experience"></a>Standarddarstellung festlegen

Wenn Ihre Organisation beide Suchoptionen aktiviert hat, können Sie in Ihren persönlichen Einstellungen eine Standardsuche auswählen.

1. Klicken Sie in der oberen rechten Ecke der Seite auf **Einstellungen** , und wählen Sie dann **Personalisierungs Einstellungen**aus.  
  
   > [!div class="mx-imgBorder"]
   > ![Standard Suchvorgang auswählen]wählen(media/relevance-search-personal-settings.png "Sie Standard Such") Vorgang aus.  

2. Wählen Sie auf der Registerkarte **Allgemein** im Abschnitt **Wählen Sie die Standardsuche** aus, um die Standardeinstellung für die **Suche**auszuwählen. 

   > [!div class="mx-imgBorder"]
   > ![Standard Suchvorgang auswählen]wählen(media/default.png "Sie Standard Such") Vorgang aus.  
 


## <a name="start-a-search"></a>Suche starten 
 
1.  Wählen Sie in der oberen Navigationsleiste die Schaltfläche **Suchen** aus.  
  
2.  Geben Sie die Suchbegriffe in das Suchfeld ein, und wählen Sie dann die Schaltfläche **Suchen** aus.   

    > [!div class="mx-imgBorder"]
    > Such ![Option]((media/search-option.png "Suchoption") )  
  
## <a name="filter-categorized-search-results"></a>Filtern kategorisierter Suchergebnisse 
  
-   Wenn Sie Ergebnisse nach einem Daten Satz Typen filtern möchten, wählen Sie auf dem Suchbildschirm im Dropdown Feld **Filter mit:** einen Daten Recordtyp aus.  
  
-   Um alle Daten Satz Typen zu suchen, wählen Sie im Dropdown Feld **Filtern mit:** **keine** aus.  

    > [!div class="mx-imgBorder"]
    > Such(media/filter-search.png "Filter") ![Suche Filtern]  

## <a name="filter-records-with-facets-works-with-relevance-search"></a>Datensätze mit Facetten Filtern (funktioniert mit der relevanzsuche)  
 Mit Common Data Service können Sie nun die Suchergebnisse mithilfe von Facetten und Filtern verfeinern. Facetten sind im linken Bereich verfügbar. Unmittelbar nach dem Durchführen einer Suche sind die folgenden globalen Facetten für vier gängige Felder verfügbar:  
  
-   Daten Satz Typen  
  
-   Owner  
  
-   Erstellt am  
  
-   Geändert am  
  
### <a name="record-type-facets"></a>Facetten von Daten Satz Typen  
 Um die Suchergebnisse auf eine bestimmte Entität einzugrenzen, wählen Sie die Entität im Abschnitt **Daten Satz Typen** aus.  
 
  > [!div class="mx-imgBorder"]
  > ![Datensatz für Datensatz-Typ zum Eingrenzen der Suchergebnis](media/relevance-search-record-type-facet.png "Daten Satz-Typ-Facette zum Einschränken der Suchergebnisse")  
  
 Wenn Sie nach einem bestimmten Daten Satz Typen filtern, können Sie in den Suchergebnissen Aktivitäten und Notizen einschließen, die mit dem ausgewählten Datensatz verknüpft sind. Aktivieren Sie hierzu das Kontrollkästchen **Verwandte Notizen & Aktivitäten** . Die Aktivitäten und Notizen werden in den Ergebnissen der obersten Ebene angezeigt.  
  
 
  > [!div class="mx-imgBorder"]
  > ![Einschließen von Notizen und Aktivitäten im Zusammenhang mit einem Daten Satz Typen in den Suchergebnissen](media/relevance-search-record-type-facet-related-notes-activities.png "enthalten Hinweise und Aktivitäten im Zusammenhang mit einem Daten Satz Typen in den Suchergebnissen") .  
  
 Suchergebnisse, die in e-Mail-Anlagen oder Termin Entitäten gefunden werden, werden in den Suchergebnissen unter ihrem übergeordneten Datensatz angezeigt (entweder e-Mail oder Termin).  
  
 Wenn Sie den Typ des Datensatzes verfeinern, wechselt der facetbereich zur ausgewählten Entität, und es werden bis zu vier Facetten angezeigt, die für die Entität spezifisch sind. Wenn Sie beispielsweise die Entität "Account" (Konto) auswählen, wird neben den globalen Facetten auch der **primäre Kontakt** Aspekt angezeigt.  
  
 Im Dialogfeld **Persönliche Optionen festlegen** können Sie auch andere Facetten auswählen, die von Ihrem Systemadministrator oder Kunden zur Verfügung gestellt wurden. Die Benutzereinstellung überschreibt die Standardeinstellung. [!INCLUDE[proc_more_information](../includes/proc-more-information.md)]: [Facetten und Filter für die Suche konfigurieren](#BKMK_ConfigureFacets)  
  
### <a name="text-based-facets"></a>Text basierte Facetten  
 Alle Lookups, Optionssätze und Daten Satz Typen sind textbasierte Facetten. Der textbasierte facetbesitzer besteht z. b. aus einer Liste von Feldwerten und ihren entsprechenden Zählungen.  
 
  > [!div class="mx-imgBorder"]
  > ![Textbasierter Aspekt in der relevanzsuche](media/relevance-search-text-based-facets.png "textbasierter Aspekt bei der relevanzsuche")  
  
 Filter in diesen Facetten werden nach Anzahl in absteigender Reihenfolge sortiert. Die ersten vier Facetwerte werden standardmäßig angezeigt. Wenn mehr als vier Facetwerte vorhanden sind, wird ein Link **anzeigen angezeigt** , den Sie auswählen können, um die Liste zu erweitern und bis zu 15 Top-facewerte anzuzeigen. Wählen Sie die einzelnen Werte aus, um die Suchergebnisse zu filtern und nur Datensätze anzuzeigen, in denen das Feld den von Ihnen ausgewählten Wert aufweist. Wenn Sie z. b. **Kim Abercrombie**auswählen, werden in den Suchergebnissen alle Datensätze angezeigt, bei denen der Besitzer Kim Abercrombie ist. Wenn Sie einen Lookup-oder Options Satz-facewert auswählen, werden die Suchergebnisse so gefiltert, dass Sie nur Datensätze mit dem von Ihnen angegebenen Wert enthalten.  
  
### <a name="date-and-time-facets"></a>Datums-und Uhrzeit Facetten  
 Wie andere Facetten können Sie Datums-und Zeit Facetten verwenden, um Suchergebnisse für einen bestimmten Zeitraum zu filtern und anzuzeigen. Wenn Sie einen Wertebereich auswählen möchten, ziehen Sie den Schieberegler, oder wählen Sie eine der vertikalen Spalten aus.  
 
  > [!div class="mx-imgBorder"]
  > ![Datums-und Uhrzeit Facetten für](media/relevance-search-date-time-facets.png "Datums-und Zeit Facetten") der relevanzsuche bei der relevanzsuche  
  
<a name="BKMK_ConfigureFacets"></a>   
### <a name="configure-facets-and-filters-for-the-search"></a>Konfigurieren von Facetten und Filtern für die Suche  
 Mit Facetten und Filtern können Sie einen Drilldown für die Ergebnisse der aktuellen Suche durchführen, ohne den Suchbegriff wiederholt verfeinern zu müssen. Konfigurieren Sie die gewünschten Facetten und Filter im Dialogfeld " **Persönliche Optionen festlegen** ".  
  
> [!NOTE]
>  Die Systemanpassung kann die Standardeinstellung für alle Entitäten festlegen, aber Sie können Ihre eigenen Facetten und Filter konfigurieren.  
  
#### <a name="to-configure-facets-for-yourself"></a>So konfigurieren Sie Facetten für sich selbst  
  
1. Klicken Sie in der oberen rechten Ecke der Seite auf **Einstellungen** , und wählen Sie dann **Personalisierungs Einstellungen**aus.  
  
   > [!div class="mx-imgBorder"]
   > ![Standard Suchvorgang auswählen]wählen(media/relevance-search-personal-settings.png "Sie Standard Such") Vorgang aus.  
  
2. Wählen Sie auf der Registerkarte **Allgemein** im Abschnitt **Standard Suchfunktion auswählen** für das Feld **Facetten und Filter** die Option **Konfigurieren**aus.  
  
3. Geben Sie im Dialogfeld **Facetten und Filter konfigurieren** die Facetten an, die Sie für eine Entität sehen möchten. Der Systemadministrator oder benutzerdefinierte benutzerdefinierte Benutzer können für alle Entitäten eine Standardeinstellung festlegen, aber Sie können hier einen eigenen Wert festlegen.  
  
   - Wählen Sie in der Dropdown Liste **Entität auswählen** eine Entität aus, für die Sie Facetten konfigurieren möchten. Diese Dropdown Liste enthält nur die Entitäten, für die die relevanzsuche aktiviert ist.  
  
   - Wählen Sie für die ausgewählte Entität bis zu vier facetfelder aus. Standardmäßig sind die ersten vier Facetten fähigen Felder in der Ansicht **Schnellsuche** für die ausgewählte Entität in der Liste ausgewählt. Es können immer nur vier Felder als Facetten ausgewählt werden.  
  
     Sie können mehrere Entitäten gleichzeitig aktualisieren. Wenn Sie auf **OK**klicken, werden die Änderungen für alle Entitäten gespeichert, die Sie konfiguriert haben. Wenn Sie das Standardverhalten für eine Entität wiederherstellen möchten, die Sie zuvor konfiguriert haben, wählen Sie **Standard**aus.  
  
   > [!NOTE]
   > - Wenn ein System-Anpassungsprogramm ein Feld löscht oder es nicht mehr durchsuchbar ist, und Sie ein facetelement für dieses Feld gespeichert haben, wird es nicht mehr als facettyp angezeigt.  
   >   -   Sie sehen nur die Felder, die in der Standard Projekt Mappe vorhanden sind und die von Ihrem systemanpassungsprogramm als durchsuchbar konfiguriert wurden.  
  
 
