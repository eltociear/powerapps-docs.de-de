---
title: Relevanzsuche | MicrosoftDocs
ms.custom: ''
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 1/28/2020
ms.author: mduelae
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 3a78e555c8818144b41935715ab9f983c7d9714b
ms.sourcegitcommit: 303d5aed44f2bbb406cabeb6b9c8474d738d9114
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "76918783"
---
# <a name="using-relevance-search-to-search-for-records"></a>Verwenden der relevanzsuche zum Suchen nach Datensätzen

## <a name="what-is-relevance-search"></a>Was ist relevantes suchen?

Die relevanzsuche liefert schnelle und umfassende Ergebnisse für mehrere Entitäten in einer einzigen Liste, sortiert nach Relevanz. Der Dienst verwendet einen dedizierten Suchdienst, der extern für Common Data Service ([!INCLUDE[pn_Windows_Azure](../includes/pn-windows-azure.md)]) verwendet wird, um die Suchleistung zu verbessern.
  
Die relevanzsuche bietet die folgenden Verbesserungen und Vorteile:  
<!--note from editor: Edits to these list items are suggested, so they can be parallel throughout this section.-->  
- Verbessert die Leistung durch die Verwendung externer Indizierungs-und [!INCLUDE[pn_azure_shortest](../includes/pn-azure-shortest.md)] Suchtechnologie.  
  
- Findet Übereinstimmungen mit einem beliebigen Wort im Suchbegriff in einem beliebigen Feld in der Entität, verglichen mit der Schnellsuche, in der alle Wörter aus dem Suchbegriff in einem Feld gefunden werden müssen. 

- Sucht nach Übereinstimmungen, die unveränderliche Wörter wie **Stream**, **Streaming**oder Streamingeinschließen.  
  
- Gibt Ergebnisse aus allen durchsuchbaren Entitäten in einer einzelnen Liste nach Relevanz sortiert zurück. je besser die Übereinstimmung ist, desto höher wird das Ergebnis in der Liste angezeigt. Eine Entsprechung hat eine höhere Relevanz, wenn mehr Wörter aus dem Suchbegriff in unmittelbarer Nähe zueinander gefunden werden. Je kleiner die Text Menge, in der die Suchwörter gefunden werden, desto höher die Relevanz. Wenn Sie z. b. die Suchbegriffe in einem Firmennamen und einer Adresse finden, ist es möglicherweise besser, die gleichen Wörter in einem langen Artikel zu finden, weit voneinander entfernt.
  
- Markiert die Übereinstimmungen in der Ergebnisliste. Wenn ein Suchbegriff mit einem Begriff in einem Datensatz übereinstimmt, wird der Begriff in den Suchergebnissen als fett formatierter und kursiv formatierter Text angezeigt. 

    > [!NOTE]
    > - Bestimmte Wörter, die sehr häufig in einer Sprache verwendet werden (z. b **. oder)** , werden während der Suche ignoriert, da Sie nicht bei **der** eindeutigen Identifizierung von Datensätzen helfen. Da Sie während der Suche ignoriert werden, werden diese Wörter ebenfalls nicht in den Ergebnissen hervorgehoben.
    > - Hervorgehobene Begriffe werden oft als Teil des vollständigen Werts in einem Feld zurückgegeben, da nur die übereinstimmenden Begriffe hervorgehoben werden.  

- Enthält Suchergebnisse für Text in einem Dokument, das in Common Data Service gespeichert ist, einschließlich Text in Notizen, e-Mail-Anlagen oder Terminen. Die folgenden Dateiformate werden für die Suche unterstützt: PDF, Microsoft Office Dokumente, HTML, XML, ZIP, eml, nur-Text und JSON.  
  
- Ermöglicht es Ihnen, Datensätze zu suchen, die für Sie freigegeben wurden, und Datensätze, die Sie besitzen.  
  
  > [!NOTE]
  >  Hierarchische Sicherheitsmodelle werden nicht unterstützt. Auch wenn eine Zeile in Common Data Service angezeigt wird, weil Sie über hierarchische Sicherheit darauf zugreifen können, wird das Ergebnis nicht in der relevanzsuche angezeigt.  
  
- Mit können Sie auch nach Options Sätzen und Such Vorgängen suchen. Nehmen wir beispielsweise an, Sie möchten ein Einzelhandelsgeschäfts Konto suchen, das über **Pharmaceuticals** im Namen verfügt. Wenn Sie nach dem **pharmazeutischen Einzelhandel**suchen, finden Sie das Ergebnis, weil es eine Entsprechung für das Feld "Industry" gibt, bei dem es sich um eine durchsuchbare Option handelt.

  > [!NOTE]
  > - Die relevanzsuche ist Text basiert und kann nur nach Feldern vom Typ "einzelne Textzeile", mehreren Textzeilen, Options Sätzen oder Such Vorgängen suchen. Das Suchen in Feldern vom numerischen Datentyp oder dem Date-Datentyp wird nicht unterstützt.
  
- Ermöglicht die Verwendung von Syntax in Ihrem Suchbegriff, um die gewünschten Ergebnisse zu erhalten. Geben Sie z. b. **Auto Silver 2-Door** ein, um Übereinstimmungen für jedes Wort im Suchbegriff in den Suchergebnissen einzuschließen. Geben Sie **Car + Silver +2-Door** ein, um nur Übereinstimmungen zu suchen, die alle drei Wörter enthalten. Geben **Sie&#124;Car&#124;Silver 2-Door** ein, um Ergebnisse zu erhalten, die **Auto** , **Silver** oder **2-Door**oder alle drei Wörter enthalten. Weitere Informationen zur Syntax, die Sie in ihren Such Abfragen verwenden können, finden Sie unter [einfache Abfrage Syntax in Azure kognitive Suche](https://docs.microsoft.com/rest/api/searchservice/simple-query-syntax-in-azure-search).<!--note from editor: The "More information:" pattern is good when there aren't any additional modifiers, which you have here. -->
  
  > [!NOTE]
  > Die relevanzsuche ist so konfiguriert, dass Übereinstimmungen mit beliebigen (statt allen) Kriterien in einer Abfrage erforderlich sind, was zu Ergebnissen führen kann, die sich von Ihren Erwartungen unterscheiden. Dies trifft vor allem dann zu, wenn boolesche Operatoren in der Abfrage enthalten sind.<!--note from editor: Via style guide, it's always capital "Boolean," and it's "might" instead of "may.-->

## <a name="enable-relevance-search"></a>Relevanzsuche aktivieren

Die relevanzsuche ist standardmäßig deaktiviert. Ihr Administrator muss Sie für die Organisation aktivieren, damit alle Benutzer in der Organisation Sie verwenden können. Nachdem die relevanzsuche aktiviert ist, müssen Sie möglicherweise bis zu einer Stunde oder mehr warten, je nach Größe Ihres Unternehmens, bevor Sie mit dem Anzeigen der Ergebnisse der relevanzsuche für Ihre apps beginnen. Kleinere Änderungen an indizierten Daten können bis zu 15 Minuten in Ihrem System angezeigt werden.

## <a name="switch-between-relevance-search-and-categorized-search"></a>Zwischen relevanzsuche und kategorisierter Suche wechseln

Wenn Ihre Organisation beide Suchoptionen (relevanzsuche und kategorisierte Suche) aktiviert hat, können Sie zwischen den beiden wechseln.

1. Wählen Sie auf der Navigationsleiste **Suchen**aus, um zwischen den Suchtypen zu wechseln.

2. Wählen Sie auf der linken Seite das Dropdown Menü aus, um zwischen der **relevanzsuche** oder der **kategorisierten Suche**zu wechseln.

   > [!div class="mx-imgBorder"]
   > ![Zwischen Relevanz und kategorisierter Suche wechseln](media/switch-global-search.png "Zwischen relevanzsuche und kategorisierter Suche wechseln") 
    
## <a name="set-a-default-search-experience"></a>Standard Suchvorgang festlegen

Wenn Ihre Organisation beide Suchoptionen aktiviert hat, können Sie in Ihren persönlichen Einstellungen eine Standardsuche auswählen.

1. Wählen Sie in der oberen rechten Ecke der Seite **Einstellungen**aus, und wählen Sie dann **Personalisierungs Einstellungen**aus.  
  
   > [!div class="mx-imgBorder"]
   > ![Personalisierungs Einstellungen](media/personalization-settings.png "Personalisierungs Einstellungen")  

2. Wählen Sie auf der Registerkarte **Allgemein** im Abschnitt **Wählen Sie die Standardsuche** aus, um die Standardeinstellung für die **Suche**auszuwählen. 

   > [!div class="mx-imgBorder"]
   > ![Standard Suchvorgang auswählen](media/default-search-experience.png "Standard Suchvorgang auswählen")  

## <a name="start-a-search"></a>Suche starten 
 
1.  Wählen Sie in der oberen Navigationsleiste **Suchen**aus.  

    > [!div class="mx-imgBorder"]
    > ![Globale Such Schaltfläche](media/global-search-button.png "Globale Suche") 
  
2.  Geben Sie die Suchwörter in das Suchfeld ein, und klicken Sie dann auf **Suchen**.

    > [!div class="mx-imgBorder"]
    > ![Relevantes Suchfeld](media/relevance-search-box.png "Relevantes Suchfeld")   

## <a name="filter-records-with-facets"></a>Datensätze mit Facetten Filtern

Mit Common Data Service können Sie nun die Suchergebnisse mithilfe von Facetten und Filtern verfeinern. Mit Facetten und Filtern können Sie einen Drilldown für die Ergebnisse der aktuellen Suche durchführen, ohne die Suchbegriffe wiederholt verfeinern zu müssen.

Facetten sind im linken Bereich verfügbar. Unmittelbar nach dem Durchführen einer Suche sind die folgenden globalen Facetten für vier gängige Felder verfügbar:  
  
-   Datensatztyp  
  
-   Owner  
  
-   Erstellt am  
  
-   Geändert am  
  
### <a name="record-type-facets"></a>Facetten von Daten Satz Typen

Um die Suchergebnisse auf eine bestimmte Entität einzugrenzen, wählen Sie die Entität im Abschnitt **Daten Satz Typen** aus.  
 
  > [!div class="mx-imgBorder"]
  > ![Datensatz-typaspekt zum Eingrenzen der Suchergebnisse](media/relevance-search-record-type-facet.png "Der Datensatz zum Eingrenzen der Suchergebnisse.")  
  
Wenn Sie nach einem bestimmten Daten Satz Typen filtern, können Sie in den Suchergebnissen Aktivitäten und Notizen einschließen, die mit dem ausgewählten Datensatz verknüpft sind. Aktivieren Sie hierzu das Kontrollkästchen **Verwandte Notizen & Aktivitäten** . Die Aktivitäten und Notizen werden in den Ergebnissen der obersten Ebene angezeigt.
 
  > [!div class="mx-imgBorder"]
  > ![Einschließen von Notizen und Aktivitäten im Zusammenhang mit einem Daten Satz Typen in den Suchergebnissen](media/relevance-search-record-type-facet-related-notes-activities.png "Einschließen von Notizen und Aktivitäten im Zusammenhang mit einem Daten Satz Typen in den Suchergebnissen")  
  
Suchergebnisse, die in e-Mail-Anlagen oder Termin Entitäten gefunden werden, werden in den Suchergebnissen unter ihrem übergeordneten Datensatz angezeigt (entweder e-Mail oder Termin).  
  
Wenn Sie den Typ des Datensatzes verfeinern, wechselt der facetbereich zur ausgewählten Entität, und es werden bis zu vier Facetten angezeigt, die für die Entität spezifisch sind. Wenn Sie beispielsweise die Entität "Account" (Konto) auswählen, wird neben den globalen Facetten auch der **primäre Kontakt** Aspekt angezeigt.  
  
Im Dialogfeld **Persönliche Optionen festlegen** können Sie auch andere Facetten auswählen, die von Ihrem Systemadministrator oder Kunden zur Verfügung gestellt wurden. Die Benutzereinstellung überschreibt die Standardeinstellung. [!INCLUDE[proc_more_information](../includes/proc-more-information.md)] [Konfigurieren von Facetten und Filtern für die Suche](#BKMK_ConfigureFacets)  
  
### <a name="text-based-facets"></a>Text basierte Facetten

Alle Lookups, Optionssätze und Daten Satz Typen sind textbasierte Facetten. Der textbasierte facetbesitzer besteht z. b. aus einer Liste von Feldwerten und ihren entsprechenden Zählungen.  
 
  > [!div class="mx-imgBorder"]
  > ![Text basierter Aspekt bei der relevanzsuche](media/relevance-search-text-based-facets.png "Text basierter Aspekt bei der relevanzsuche")  
  
Filter in diesen Facetten werden nach Anzahl in absteigender Reihenfolge sortiert. Die ersten vier Facetwerte werden standardmäßig angezeigt. Wenn mehr als vier Facetwerte vorhanden sind, wird ein Link **anzeigen angezeigt** , den Sie auswählen können, um die Liste zu erweitern und bis zu 15 Top-facewerte anzuzeigen. Wählen Sie die einzelnen Werte aus, um die Suchergebnisse zu filtern und nur Datensätze anzuzeigen, in denen das Feld den von Ihnen ausgewählten Wert aufweist. Wenn Sie z. b. **Jim Glynn**auswählen, werden in den Suchergebnissen alle Datensätze angezeigt, bei denen der Besitzer Jim Glynn ist. Wenn Sie einen Lookup-oder Options Satz-facewert auswählen, werden die Suchergebnisse so gefiltert, dass Sie nur Datensätze mit dem von Ihnen angegebenen Wert enthalten.  
  
### <a name="date-and-time-facets"></a>Datums-und Uhrzeit Facetten

Wie andere Facetten können Sie Datums-und Zeit Facetten verwenden, um Suchergebnisse für einen bestimmten Zeitraum zu filtern und anzuzeigen. Wenn Sie einen Wertebereich auswählen möchten, ziehen Sie den Schieberegler, oder wählen Sie eine der vertikalen Spalten aus.  
 
  > [!div class="mx-imgBorder"]
  > ![Datums-und Uhrzeit Facetten für die relevanzsuche](media/relevance-search-date-time-facets.png "Datums-und Uhrzeit Facetten für die relevanzsuche")  

<a name="BKMK_ConfigureFacets"></a>

## <a name="configure-facets-and-filters"></a>Konfigurieren von Facetten und Filtern
  
> [!NOTE]
>  Ein systemanpassungsprogramm kann die Standardeinstellung für alle Entitäten festlegen, aber Sie können Ihre eigenen Facetten und Filter konfigurieren.  
  
1. Klicken Sie in der oberen rechten Ecke auf **Einstellungen**, und wählen Sie dann **Personalisierungs Einstellungen**aus.  
  
   > [!div class="mx-imgBorder"]
   > ![Personalisierungs Einstellungen](media/personalization-settings.png "Personalisierungs Einstellungen")
  
2. Wählen Sie auf der Registerkarte **Allgemein** im Abschnitt **Standard Suchfunktion auswählen** für das Feld **Facetten und Filter** die Option **Konfigurieren**aus.  

   > [!div class="mx-imgBorder"]
   > ![Konfigurieren von Facetten und Filtern](media/configure-facets-filters.png "Konfigurieren von Facetten und Filtern")  
  
3. Geben Sie im Dialogfeld **Facetten und Filter konfigurieren** die Facetten an, die Sie für eine Entität sehen möchten. Der Systemadministrator oder benutzerdefinierte benutzerdefinierte Benutzer können für alle Entitäten eine Standardeinstellung festlegen, aber Sie können hier einen eigenen Wert festlegen.  
  
   - Wählen Sie in der Dropdown Liste **Entität auswählen** eine Entität aus, für die Sie Facetten konfigurieren möchten. Diese Dropdown Liste enthält nur die Entitäten, für die die relevanzsuche aktiviert ist.  
  
   - Wählen Sie für die ausgewählte Entität bis zu vier facetfelder aus. Standardmäßig sind die ersten vier "facetable"-Felder in der Ansicht " **Schnellsuche** " für die ausgewählte Entität in der Liste ausgewählt. Es können immer nur vier Felder als Facetten ausgewählt werden.  
  
   Sie können mehrere Entitäten gleichzeitig aktualisieren. Wenn Sie auf **OK**klicken, werden die Änderungen für alle Entitäten gespeichert, die Sie konfiguriert haben. Wenn Sie das Standardverhalten für eine Entität wiederherstellen möchten, die Sie zuvor konfiguriert haben, wählen Sie **Standard**aus.  
  
   > [!NOTE]
   > - Wenn ein System-Anpassungsprogramm ein Feld löscht oder es nicht mehr durchsuchbar ist, und Sie ein facetelement für dieses Feld gespeichert haben, wird es nicht mehr als facettyp angezeigt.  
   >   -   Sie sehen nur die Felder, die in der Standard Projekt Mappe vorhanden sind und die von Ihrem systemanpassungsprogramm als durchsuchbar konfiguriert wurden.  
