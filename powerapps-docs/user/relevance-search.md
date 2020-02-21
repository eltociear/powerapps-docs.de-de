---
title: Relevanzsuche| Microsoft-Dokumentation
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
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "76918783"
---
# <a name="using-relevance-search-to-search-for-records"></a>Verwenden der Relevanzsuche zum Suchen nach Datensätzen

## <a name="what-is-relevance-search"></a>Was ist die Relevanzsuche?

Die Relevanzsuche liefert schnell umfassende Ergebnisse für mehrere Entitäten in einer einzelnen Liste, sortiert nach Relevanz. Sie verwendet einen dedizierten Suchdienst, der extern zu Common Data Service (unterstützt von [!INCLUDE[pn_Windows_Azure](../includes/pn-windows-azure.md)]) ist, um die Suchleistung zu steigern.
  
Die Relevanzsuche bietet die folgenden Verbesserungen und Vorzüge:  
<!--note from editor: Edits to these list items are suggested, so they can be parallel throughout this section.-->  
- Verbesserte Leistung durch Verwendung von externer Indizierung und [!INCLUDE[pn_azure_shortest](../includes/pn-azure-shortest.md)]-Suchtechnologie.  
  
- Findet Übereinstimmungen mit einem beliebigen Wort im Suchbegriff in jedem beliebigen Feld der Entität, im Gegensatz zur Schnellsuche, bei der alle Wörter aus dem Suchbegriff in einem Feld gefunden werden müssen. 

- Findet Übereinstimmungen, die flektierte Wörter wie **Stream**, **Streaming** oder **gestreamt** enthalten.  
  
- Gibt Ergebnisse aus allen durchsuchbaren Entitäten in einer einzelnen Liste nach Relevanz sortiert zurück, je besser also die Übereinstimmung, desto weiter oben in der Liste wird das Ergebnis angezeigt. Ein Treffer hat eine höhere Relevanz, wenn mehr Wörter aus dem Suchbegriff in großer Nähe zueinander gefunden werden. Je kleiner die Textmenge ist, in der die Suchwörter gefunden werden, desto höher ist die Relevanz. Wenn Sie beispielsweise die Suchbegriffe im Namen und der Adresse eines Unternehmens finden, kann das eine größere Übereinstimmung sein, als die gleichen Wörter in einem langen Artikel zu finden, weit voneinander entfernt.
  
- Übereinstimmungen werden in der Ergebnisliste hervorgehoben. Wenn ein Suchbegriff mit einem Begriff in einem Datensatz übereinstimmt, wird der Begriff als kursiv und fett formatierter Text in Ihren Suchergebnissen angezeigt. 

    > [!NOTE]
    > - Bestimmte Wörter, die in einer Sprache sehr häufig verwendet werden (wie **der** oder **ein**) werden bei der Suche ignoriert, da sie nicht zur eindeutigen Identifizierung von Datensätzen beitragen. Da sie bei der Suche ignoriert werden, werden diese Wörter in den Ergebnissen auch nicht hervorgehoben.
    > - Hervorgehobene Begriffe werden oft als Teil des vollständigen Werts in einem Feld zurückgegeben, da nur die übereinstimmenden Begriffe hervorgehoben werden.  

- Die Suchergebnisse enthalten Treffer für Text in Dokumenten, die im Common Data Service gespeichert sind, einschließlich Text in Notizen, E-Mail-Anlagen oder Terminen. Die folgenden Dateiformate werden bei der Suche unterstützt: PDF, Microsoft Office-Dokumente, HTML, XML, ZIP, EML, unformatierter Text und JSON.  
  
- Sie können nach Datensätzen suchen, die mit Ihnen geteilt wurden, und nach Datensätzen, deren Besitzer Sie sind.  
  
  > [!NOTE]
  >  Hierarchische Sicherheitsmodelle werden nicht unterstützt. Selbst wenn eine Zeile im Common Data Service sichtbar ist, weil Sie über die hierarchische Sicherheit darauf Zugriff haben, werden die Ergebnisse in der Relevanzsuche nicht angezeigt.  
  
- Sie können außerdem nach Optionsmengen und Nachschlagevorgängen suchen. Nehmen wir beispielsweise an, Sie möchten das Konto eines Einzelhandelsgeschäfts finden, das **Arzneimittel** im Namen trägt. Wenn Sie nach **Arzneimittel-Einzelhandel** suchen, finden Sie das Ergebnis, weil es eine Übereinstimmung im Branchenfeld gibt, bei dem es sich um eine durchsuchbare Optionsmenge handelt.

  > [!NOTE]
  > - Die Relevanzsuche ist textbasiert und kann nur Felder vom Typ „Einzelne Textzeile“, „Mehrere Textzeilen“, „Optionsmengen“ oder „Nachschlagevorgänge“ suchen. Die Suche in numerischen Feldern oder Datumsfeldern wird nicht unterstützt.
  
- Sie können Suchsyntax in Ihren Suchbegriffen verwenden, um die gewünschten Ergebnisse zu erhalten. Geben Sie beispielsweise **Auto silber 2-türig** ein, um Treffer für jedes Wort im Suchbegriff in die Suchergebnisse aufzunehmen. Geben Sie **Auto+silber+2-türig** ein, um nur Treffer zu finden, die alle drei Wörter enthalten. Geben Sie **Auto&#124;silber&#124;2-türig** ein, um Ergebnisse zu erhalten, die **Auto** oder **silber** oder **2-türig** oder alle drei Wörter enthalten. Weitere Informationen zur Syntax, die Sie in Ihren Suchabfragen verwenden können, finden Sie unter [Einfache Abfragesyntax in Azure Cognitive Search](https://docs.microsoft.com/rest/api/searchservice/simple-query-syntax-in-azure-search).<!--note from editor: The "More information:" pattern is good when there aren't any additional modifiers, which you have here. -->
  
  > [!NOTE]
  > Die Relevanzsuche ist so konfiguriert, dass sie Übereinstimmungen mit beliebigen (anstelle von allen) Kriterien in einer Abfrage erfordert, was zu Ergebnissen führen kann, die von Ihren Erwartungen abweichen. Dies gilt vor allem, wenn boolesche Operatoren in der Abfrage enthalten sind.<!--note from editor: Via style guide, it's always capital "Boolean," and it's "might" instead of "may.-->

## <a name="enable-relevance-search"></a>Aktivieren der Relevanzsuche

Die Relevanzsuche ist standardmäßig deaktiviert. Ihr Administrator muss sie für die Organisation aktivieren und damit allen Benutzern in der Organisation die Verwendung erlauben. Nach dem Aktivieren der Relevanzsuche müssen Sie je nach Größe Ihrer Organisation bis zu einer Stunde (oder sogar länger) warten, bevor erste Ergebnisse der Relevanzsuche für Ihre Apps angezeigt werden. Bei kleineren Änderungen in indizierten Daten kann es bis zu 15 Minuten dauern, bis die Änderungen in Ihrem System sichtbar werden.

## <a name="switch-between-relevance-search-and-categorized-search"></a>Wechsel zwischen Relevanzsuche und Suche nach Kategorien

Wenn Ihre Organisation beide Suchoptionen (Relevanzsuche und Suche nach Kategorien) aktiviert hat, können Sie zwischen beiden wechseln.

1. Um zwischen den Suchtypen zu wechseln, wählen Sie in der Navigationsleiste **Suchen** aus.

2. Wählen Sie auf der linken Seite das Dropdownmenü aus, um zwischen **Relevanzsuche** und **Suche nach Kategorien** zu wechseln.

   > [!div class="mx-imgBorder"]
   > ![Wechsel zwischen Relevanzsuche und Suche nach Kategorien](media/switch-global-search.png "Wechsel zwischen Relevanzsuche und Suche nach Kategorien") 
    
## <a name="set-a-default-search-experience"></a>Festlegen einer Standardsuchumgebung

Wenn Ihre Organisation beide Suchoptionen aktiviert hat, können Sie eine Standardsuchumgebung in Ihren persönlichen Einstellungen auswählen.

1. Wählen Sie in der oberen rechten Ecke der Seite **Einstellungen** aus, und wählen Sie dann **Personalisierungseinstellungen** aus.  
  
   > [!div class="mx-imgBorder"]
   > ![Personalisierungseinstellungen](media/personalization-settings.png "Personalisierungseinstellungen")  

2. Wählen Sie auf der Registerkarte **Allgemein** im Abschnitt **Standardsuchumgebung auswählen** als **Standardsuchumgebung** Ihre Standardumgebung aus. 

   > [!div class="mx-imgBorder"]
   > ![Standardsuchumgebung auswählen](media/default-search-experience.png "Auswählen einer Standardsuchumgebung")  

## <a name="start-a-search"></a>Starten einer Suche 
 
1.  Wählen Sie in der oberen Navigationsleiste **Suche** aus.  

    > [!div class="mx-imgBorder"]
    > ![Schaltfläche „Globale Suche“](media/global-search-button.png "Globale Suche") 
  
2.  Geben Sie die Suchbegriffe in das Suchfeld ein, und wählen Sie dann **Suchen** aus.

    > [!div class="mx-imgBorder"]
    > ![Feld „Relevanzsuche“](media/relevance-search-box.png "Feld „Relevanzsuche“")   

## <a name="filter-records-with-facets"></a>Filtern von Datensätzen mit Facetten

Mit dem Common Data Service können Sie Ihre Suchergebnisse jetzt mithilfe von Facetten und Filtern eingrenzen. Facetten und Filter ermöglichen Ihnen das Untersuchen der Ergebnisse Ihrer aktuellen Suche, z. B. mit Drilldowns, ohne Ihre Suchbegriffe wieder und wieder begrenzen zu müssen.

Facetten stehen im äußerst linken Bereich zur Verfügung. Unmittelbar nach dem Ausführen einer Suche stehen für vier häufig verwendete Felder die folgenden globalen Facetten zur Verfügung:  
  
-   Datensatztyp  
  
-   Besitzer  
  
-   Erstellt am  
  
-   Geändert am  
  
### <a name="record-type-facets"></a>Datensatztypfacetten

Um Ihre Suchergebnisse auf eine bestimmte Entität einzugrenzen, wählen Sie die Entität im Abschnitt **Datensatztyp** aus.  
 
  > [!div class="mx-imgBorder"]
  > ![Datensatztyp-Facette zum Eingrenzen der Suchergebnisse](media/relevance-search-record-type-facet.png "Datensatztyp-Facette zum Eingrenzen der Suchergebnisse verwendet")  
  
Wenn Sie nach einem bestimmten Datensatztyp filtern, können Sie in Ihre Suchergebnisse Aktivitäten und Notizen einbeziehen, die im Zusammenhang mit dem von Ihnen ausgewählten Datensatz stehen. Aktivieren Sie dazu das Kontrollkästchen **Ähnliche Notizen und Aktivitäten**. Die Aktivitäten und Notizen werden in den Ergebnissen der obersten Ebene angezeigt.
 
  > [!div class="mx-imgBorder"]
  > ![Mit einem Datensatztyp zusammenhängende Notizen und Aktivitäten in die Suchergebnisse einschließen](media/relevance-search-record-type-facet-related-notes-activities.png "Mit einem Datensatztyp zusammenhängende Notizen und Aktivitäten in die Suchergebnisse einschließen")  
  
Suchergebnisse, die in E-Mail-Anlagen oder Terminentitäten gefunden werden, werden in den Suchergebnissen unter ihrem übergeordneten Datensatz angezeigt, entweder einer E-Mail oder einem Termin.  
  
Wenn Sie nach dem Datensatztyp eingrenzen, wechselt der Facettenbereich auf die ausgewählte Entität, und bis zu vier Facetten, die für die Entität spezifisch sind, werden angezeigt. Wenn Sie beispielsweise die Kontoentität auswählen, sehen Sie zusätzlich zu den globalen Facetten die Facette **Hauptkontakt**.  
  
Im Dialogfeld **Persönliche Optionen festlegen** können Sie darüber hinaus weitere Facetten aus den von Ihrem Systemadministrator oder Kunden für Sie festgelegten Facetten auswählen. Die Benutzereinstellung setzt die Standardeinstellung außer Kraft. [!INCLUDE[proc_more_information](../includes/proc-more-information.md)] [Konfigurieren von Facetten und Filtern für die Suche](#BKMK_ConfigureFacets)  
  
### <a name="text-based-facets"></a>Textbasierte Facetten

Alle Nachschlagevorgänge, Optionsmengen und Datensatztypen sind textbasierte Facetten. Beispielsweise besteht die textbasierte Facette „Owner“ (Besitzer) aus einer Liste mit Feldwerten und ihrer jeweiligen Anzahl.  
 
  > [!div class="mx-imgBorder"]
  > ![Textbasierte Facette in der Relevanzsuche](media/relevance-search-text-based-facets.png "Textbasierte Facette in der Relevanzsuche")  
  
Filter in diesen Facetten werden nach der Anzahl in absteigender Reihenfolge sortiert. Die vier häufigsten Facettenwerte werden standardmäßig angezeigt. Wenn mehr als vier Facettenwerte vorhanden sind, wird ein Link **MEHR ANZEIGEN** eingeblendet, den Sie auswählen können, um die Liste aufzuklappen und bis zu 15 häufigste Facettenwerte anzuzeigen. Wählen Sie die einzelnen Werte aus, um die Suchergebnisse so zu filtern, dass nur Datensätze angezeigt werden, in denen das Feld den von Ihnen ausgewählten Wert aufweist. Wenn Sie beispielsweise **Jim Glynn** auswählen, zeigen die Suchergebnisse alle Datensätze an, deren Besitzer Jim Glynn ist. Wenn Sie einen Nachschlagevorgang oder eine Optionsmenge als Facettenwert auswählen, werden die Suchergebnisse so gefiltert, dass nur Datensätze mit dem von Ihnen angegebenen Wert enthalten sind.  
  
### <a name="date-and-time-facets"></a>Datums- und Uhrzeitfacetten

Wie andere Facetten können Sie Datums- und Uhrzeitfacetten verwenden, um Suchergebnisse für eine bestimmte Zeit zu filtern und anzuzeigen. Um einen Wertebereich auszuwählen, ziehen Sie den Schieberegler, oder wählen Sie eine der vertikalen Spalten aus.  
 
  > [!div class="mx-imgBorder"]
  > ![Datums- und Uhrzeitfacetten für die Relevanzsuche](media/relevance-search-date-time-facets.png "Datums- und Uhrzeitfacetten für die Relevanzsuche")  

<a name="BKMK_ConfigureFacets"></a>

## <a name="configure-facets-and-filters"></a>Konfigurieren von Facetten und Filtern
  
> [!NOTE]
>  Ein Systemanpassungsprogramm kann die Standardumgebung für alle Entitäten festlegen, Sie können aber eigene Facetten und Filter konfigurieren.  
  
1. Wählen Sie in der oberen rechten Ecke **Einstellungen** aus, und wählen Sie dann **Personalisierungseinstellungen** aus.  
  
   > [!div class="mx-imgBorder"]
   > ![Personalisierungseinstellungen](media/personalization-settings.png "Personalisierungseinstellungen")
  
2. Wählen Sie auf der Registerkarte **Allgemein** im Abschnitt **Standardsuchumgebung auswählen** im Feld **Facetten und Filter** den Wert **Konfigurieren** aus.  

   > [!div class="mx-imgBorder"]
   > ![Konfigurieren von Facetten und Filtern](media/configure-facets-filters.png "Konfigurieren von Facetten und Filtern")  
  
3. Geben Sie im Dialogfeld **Facetten und Filter konfigurieren** die Facetten an, die Sie für eine Entität anzeigen möchten. Ihr Systemadministrator oder Systemanpassungsprogramm kann für alle Entitäten eine Standardumgebung einstellen, Sie können hier aber eine eigene festlegen.  
  
   - Wählen Sie in der Dropdownliste **Entität auswählen** eine Entität aus, für die Sie Facetten konfigurieren möchten. Diese Dropdownliste enthält nur die Entitäten, die für die Relevanzsuche aktiviert sind.  
  
   - Wählen Sie für die ausgewählte Entität bis zu vier Facettenfelder aus. Standardmäßig sind die ersten vier für Facetten geeigneten Felder in der Ansicht **Schnellsuche** für die ausgewählte Entität in der Liste ausgewählt. Zu jedem Zeitpunkt können nur vier Felder als Facetten ausgewählt sein.  
  
   Sie können mehrere Entitäten zugleich aktualisieren. Wenn Sie **OK** auswählen, werden die Änderungen für alle von Ihnen konfigurierten Änderungen gespeichert. Um für eine von Ihnen zuvor konfigurierte Entität zum Standardverhalten zurückzukehren, wählen Sie **Standard** aus.  
  
   > [!NOTE]
   > - Wenn ein Systemanpassungsprogramm ein Feld löscht oder seine Suchbarkeit aufhebt und Sie für dieses Feld eine Facette gespeichert haben, wird diese nicht mehr als Facette angezeigt.  
   >   -   Sie sehen nur die Felder, die in der Standardprojektmappe vorhanden sind und die von Ihrem Systemanpassungsprogramm als suchbar konfiguriert wurden.  
