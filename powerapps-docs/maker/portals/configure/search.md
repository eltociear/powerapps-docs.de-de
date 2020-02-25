---
title: Globale Suche in Power Apps-Portalen | Microsoft-Dokumentation
description: Hier erfahren Sie, wie die globale Suche in einem Portal funktioniert.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 01/30/2020
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 9b2a2333c3e8422470521a7af135ea2c7d7040f2
ms.sourcegitcommit: 4349eefb1fd788f5e27d91319bc878ee9aba7a75
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2020
ms.locfileid: "3012624"
---
# <a name="search"></a>Search

In Power Apps-Portalen können Sie mit der globalen Suchfunktion des Portals nach Datensätzen über mehrere Entitäten hinweg suchen. Sie können auch innerhalb von Datensätzen der Entitätslisten suchen, indem Sie die Entitätsliste durchsuchen. 

Die Entitätslisten-Suchfunktion im Portal verwendet FetchXML im Backend, um die in der Entitätsliste definierten Spalten zu durchsuchen und die Ergebnisse anzuzeigen. 

Die globale Suche verwendet einen externen Suchindex, der auf Lucene.net basiert und für die gleichzeitige Suche in mehreren Entitäten und Feldern verwendet wird.

## <a name="global-search"></a>Globale Suche

Die globale Suche in den Portalen ermöglicht die Suche nach Datensätzen über mehrere Entitäten hinweg. Außerdem können Sie über mehrere Spalten hinweg suchen und konfigurieren, welche Spalten einer Entität durchsuchbar sind.

Zu den Vorteilen der globalen Suche gehört die Möglichkeit:
- Nach Übereinstimmungen für jedes Wort im Suchbegriff in jedem Entitätsfeld zu suchen Übereinstimmungen können flektierte Wörter enthalten, beispielsweise Stream, Streaming oder gestreamt.
- Ergebnisse aus allen durchsuchbaren Entitäten in einer einzelnen Liste sortiert nach Relevanz zurückzugeben, basierend auf Faktoren wie Zahl der entsprechenden Wörter oder ihrer Nähe zueinander im Text
- Übereinstimmungen in den Suchergebnissen hervorzuheben
- Facetoptionen zu bieten, mit denen die Suchergebnisse weiter gefiltert werden können

Je besser die Übereinstimmung, desto höher wird diese in den Ergebnissen der globalen Suche angezeigt. Eine Übereinstimmung hat eine größere Relevanz, wenn mehr Wörter vom Suchbegriff in unmittelbarer Nähe zueinander gefunden werden. Je kleiner der Text, in dem die Suchbegriffe gefunden werden, desto größer die Relevanz. Wenn Sie z. B. die Suchbegriffe in Unternehmensname und -adresse finden, kann es möglicherweise eine bessere Übereinstimmung sein als wenn die gleichen Wörter in einem langen Artikel weit voneinander entfernt gefunden werden. Da die Ergebnisse in einer einzelnen Liste zurückgegeben werden, sehen Sie eine Mischung von Datensätzen, die nacheinander angezeigt werden, und die übereinstimmenden werden hervorgehoben. 

In den nachfolgenden Abschnitten finden Sie Details zur Funktionsweise der globalen Suche in Power Apps-Portalen und verschiedene Konfigurationsmöglichkeiten.

## <a name="entities-searchable-in-portal-global-search"></a>Durchsuchbare Entitäten in der globalen Portalsuche

Die folgenden Entitäten können innerhalb einer Portalwebsite durchsucht werden, sofern die entsprechenden Lösungspakete installiert sind und die Suche zu einem Portal hinzugefügt wurde. Die indizierten Spalten bestehen aus den in der Suchansicht gefundenen Spalten, die angepasst werden können.  Jede Entität in der Liste hat ihre Standardattribute wie folgt indiziert:
- Knowledge-Artikel
    - Notizen und Anhang eines Wissensartikels sind ebenfalls durchsuchbar. Weitere Informationen: [Suche in Dateianhangsinhalt](search-file-attachment.md)
    - Es können nur die Artikel durchsucht werden, die veröffentlicht wurden und bei denen das Feld "Nur intern" auf false festgelegt ist.
- Blog 
- Blogbeitrag 
- Blogbeitragskommentar 
- Forum 
- Forenbeitrag 
- Forenthread 
- Idee 
- Ideenkommentar 
- Ideenforum 
- Webdatei 
    - Anlageninhalte von Webdateien können ebenfalls durchsucht werden. Weitere Informationen: [Suche in Dateianhangsinhalt](search-file-attachment.md)
- Webseite 
- Vorfall 

> [!NOTE]
> Außer den hier aufgeführten Entitäten kann keine andere Entität für die globale Suche in einem Portal aktiviert werden.

## <a name="fields-searchable-in-global-search"></a>Durchsuchbare Felder in der globalen Suche

Alle Felder, die in der durch die Einstellung Search/IndexQueryName für eine beliebige Entität definierten Ansicht verfügbar sind, werden in der globalen Suche indiziert und können durchsucht werden. 

Standardwert für Search/IndexQueryName ist "Portalsuche".

Wenn die Ansicht für keine Entität verfügbar ist, wird sie nicht indiziert und die Ergebnisse werden bei der globalen Suche nicht angezeigt.

> [!NOTE]
> Wenn Sie den Wert der Websiteeeinstellung Search/IndexQueryName ändern, müssen Sie eine manuelle Neuindizierung des Builds mit den Schritten auslösen, die im Abschnitt [Vollständigen Suchindex neu erstellen](#rebuild-full-search-index) definiert sind.

## <a name="related-site-settings"></a>Zugehörige Websiteeinstellungen

Die folgenden Websiteeinstellungen beziehen sich auf die globale Suche:

| Name    | Standardwert     | Beschreibung       |
|-----------------------|--------------------|-------------|
| Suche/Aktivieren | True  | Ein boolescher Wert, der angibt, ob die Suche aktiviert ist. Wenn Sie den Wert auf false setzen, wird die globale Suche im Portal deaktiviert.<br>Wenn Sie vorkonfigurierte Webvorlagen verwenden und diese Einstellung deaktivieren, wird das Suchfeld nicht in der Kopfzeile sowie auf der Suchseite angezeigt. Auch werden keine Ergebnisse zurückgegeben, selbst wenn die direkte URL für die Suchseite gefunden wird.  |
| Suche/Filter  | Inhalt:adx_webpage;Ereignisse:adx_event,adx_eventschedule;Blogs:adx_blog,adx_blogpost,adx_blogpostcomment;Foren:adx_communityforum,adx_communityforumthread,adx_communityforumpost;Ideen:adx_ideaforum,adx_idea,adx_ideacomment;Probleme:adx_issueforum,adx_issue,adx_issuecomment;Help Desk:incident | Eine Sammlung von Filteroptionen für logische Suchbegriffe. Wenn Sie hier einen Wert definieren, werden der globalen Suche Dropdown-Filteroptionen hinzugefügt. Dieser Wert sollte in Form von Name/Wert-Paaren vorliegen, wobei Name und Wert durch einen Doppelpunkt und Paare durch ein Semikolon getrennt sind. Zum Beispiel "Foren:adx_communityforum,adx_communityforumthread,adx_communityforumpost;Blogs:adx_blog,adx_blogpost,adx_blogpostcomment".  |
| Suchen/IndexQueryName   | Portalsuche  | Der Name der Systemansicht, die von der Portalsuchabfrage verwendet wird, um die Felder einer aktivierten Entität zu definieren, die indiziert und durchsucht werden.   |
| Suche/Abfrage  | +(@Query) _title:(@Query) _logicalname:adx_webpage\~0.9^0.2 -_logicalname:adx_webfile\~0.9 adx_partialurl:(@Query) _logicalname:adx_blogpost\~0.9^0.1 -_logicalname:adx_communityforumthread\~0.9   | Diese Einstellung fügt der Abfrage zusätzliche Gewichte und Filter hinzu, die ein Benutzer in das Standard-Suchfeld eingibt, das im Portal angezeigt wird. Im Standardwert ist @Query  der von einem Benutzer eingegebene Abfragetext.<br>Für Informationen darüber, wie Sie diesen Wert ändern können, folgen Sie [Lucene-Abfragesyntax](https://lucene.apache.org/core/old_versioned_docs/versions/2_9_1/queryparsersyntax.html).<br>**Wichtig**: Diese Gewichtung und Filterung gilt nur für das Suchfeld, das auf der Standardsuchseite des Portals erscheint. Wenn Sie Ihre eigene Suchseite mit Liquid-Suchtag erstellen, dann gilt diese Einstellung nicht. |
| Suchen/Wortstammerkennungen  | Englisch    | Die Sprache, die vom Wortstammerkennungsalgorithmus der Portalsuche verwendet wird.   |
| Suchen/FacetedView  | Wahr   | Dies ermöglicht Facets in den Suchergebnissen. Wenn auf True gesetzt, werden Facets zusammen mit den Ergebnissen auf der Suchseite angezeigt.  |
| Suchen/IndexNotesAttachments   | Wahr    | Gibt an, ob der Inhalt der Notizanhänge in Wissensdatenbankartikeln sowie in Webdateien indiziert werden soll. Standardmäßig ist dies auf False festgelegt. Weitere Informationen: [Suche in Dateianhangsinhalt](search-file-attachment.md)    |
| Suchen/RecordTypeFacetsEntities  | Blogs:adx_blog,adx_blogpost;Foren:adx_communityforum,adx_communityforumthread,adx_communityforumpost;Ideen:adx_ideaforum,adx_idea;Downloads:annotation,adx_webfile    | Dies legt fest, wie die Entitäten in der Datensatztyp-Facet auf der Suchseite gruppiert werden. Diese Einstellung hat das Format <br>“DisplayNameinRecordTypeFacet1:logicalnameofentity1,logicalnameofentity2; DisplayNameinRecordTypeFacet2:logicalnameofentity3,logicalnameofentity4” <br>Der Anzeigename in der Facet "Datensatztyp" wird auf der Benutzeroberfläche angezeigt. Diese Facetgruppe fasst das Ergebnis der in der Konfiguration definierten Entitäten zusammen.   |
| KnowledgeManagement/DisplayNotes | Wahr   | Gibt an, ob Anhänge von Wissensdatenbankartikeln indiziert werden sollen. Standardmäßig ist dies auf False festgelegt. |
|||

## <a name="related-content-snippets"></a>Zugehörige Inhaltsausschnitte

Die folgenden Inhaltsausschnitte beziehen sich auf die globale Suche:

| Name   | Standardwert  | Beschreibung   |
|------------------|-----------------|--------------------|
| Kopfzeile/Suche/Beschriftung| Search| Dieser Inhaltsausschnitt bestimmt den Wasserzeichentext, der im Suchfeld in der Portalkopfzeile angezeigt wird.<br>![Suchbeschriftung](../media/search-label.png "Suchbeschriftung")    |
| Kopfzeile/Suche/QuickInfo| Search  | Dieser Inhaltsausschnitt bestimmt den QuickInfotext, der angezeigt wird, wenn Sie mit dem Mauszeiger über das Suchsymbol in der Portalkopfzeile fahren.<br>![QuickInfo für Suche](../media/search-tooltip.png "QuickInfo für Suche")  |
| Suche/Standard/FilterText| Alle   | Dieses Inhalts-Snippet bestimmt den Standardtext, der in der Filterdropdownliste neben dem Suchfeld angezeigt wird.<br>![Suchfiltertext](../media/search-filter-text.png "Suchfiltertext")  |
| Suche/Facet/Alle| Alle| Dieser Inhaltsausschnitt bestimmt den Standardtext, der für "alle Datensatzfacets" in der Facet "Datensatztyp" der Suchergebnisseite angezeigt wird.<br>![Alle Facetten](../media/facet-all.png "Alle Facetten") |
| Suche/Facet/ClearConstraints   | Alle löschen  | Dieser Inhaltsausschnitt bestimmt die Beschriftung der Schaltfläche, die alle Facets der Suchergebnisseite zurücksetzt.<br>![Alle Facetten zurücksetzen](../media/facet-clear-all.png "Alle Facetten zurücksetzen") |
| Suche/Facet/Downloads   | Downloads   | Dieser Inhaltsausschnitt bestimmt die Beschriftung, die in den Suchergebnissen von Anmerkungsanhängen und Web-Dateidatensätzen in der Facet "Datensatztyp" angezeigt wird.<br>![Download-Facette](../media/facet-download.png "Download-Facette")|
| Suche/Facet/Weniger    | Weniger anzeigen  | Dieser Inhaltsausschnitt bestimmt die Beschriftung der Schaltfläche, die die Facetergebnisse reduziert.<br>![Weniger Facetten anzeigen](../media/facet-show-less.png "Weniger Facetten anzeigen") |
| Suche/Facet/ModifiedDate  | Änderungsdatum  | Dieser Inhaltsausschnitt bestimmt die Beschriftung der Kopfzeile, die für die Änderungsdatum-Facet angezeigt wird.<br>![Änderungsdatum](../media/facet-modified-date.png "Facette für Änderungsdatum")   |
| Suche/Facet/Mehr   | Mehr anzeigen  | Dieser Inhaltsausschnitt bestimmt die Beschriftung der Schaltfläche, die die Facetergebnisse erweitert.<br>![Mehr Facetten anzeigen](../media/facet-show-more.png "Mehr Facetten anzeigen")  |
| Suche/Facet/Produkt  | Produkte | Dieser Inhaltsausschnitt bestimmt die Beschriftung des Produktfacets.<br>![Produktfacette](../media/facet-product.png "Produktfacette")  |
| Suche/Facet/Bewertung   | Bewertung   | Dieser Inhaltsausschnitt bestimmt die Beschriftung des Bewertungsfacets.<br>![Bewertungsfacette](../media/facet-rating.png "Bewertungsfacette")  |
| Suche/Facet/RecordType   | Datensatztyp | Dieser Inhaltsausschnitt bestimmt die Beschriftung des Datensatztyp-Facets.<br>![Datensatztyp-Facette](../media/facet-record-type.png "Datensatztyp-Facette")     |
| Suche/Facet/SortOrder/AverageUserRating | Durchschnittliche Nutzerbewertung | Dieser Inhaltsausschnitt bestimmt die Beschriftung, die für die Option "Nach durchschnittlicher Benutzerbewertung sortieren" in der Sortierungsdropdown-Liste auf der Suchergebnissseite angezeigt wird.<br>![Sortieren nach durchschnittlicher Benutzerbewertung](../media/sort-avg-user-rating.png "Sortieren nach durchschnittlicher Benutzerbewertung")  |
| Suche/Facet/SortOrder/Relevanz| Relevanz| Dieser Inhaltsausschnitt bestimmt die Beschriftung, die für die Option "Nach Relevanz sortieren" in der Sortierungsdropdown-Liste auf der Suchergebnissseite angezeigt wird.<br>![Nach Relevanz sortieren](../media/sort-relevance.png "Nach Relevanz sortieren")|
| Suche/Facet/SortOrder/Ansichten| Anzahl angezeigt| Dieser Inhaltsausschnitt bestimmt die Beschriftung, die für die Option "Nach Anzahl der Ansichten sortieren" in der Sortierungsdropdown-Liste auf der Suchergebnissseite angezeigt wird.<br>![Sortieren nach Ansichtsanzahl](../media/sort-view-count.png "Sortieren nach Ansichtsanzahl")|
|||

## <a name="entity-specific-handling"></a>Entitätenspezifische Behandlung

- **Anfrage**: Standardmäßig sind nur die Anfragen durchsuchbar, die sich im Status **Abgeschlossen** befinden und bei denen das Feld **Im Internet veröffentlichen** auf **True** festgelegt ist. Dieses Verhalten kann geändert werden, indem Sie die Portalsuchansicht der Anfrageentität aktualisieren und die in der Portalsuchansicht verfügbaren Filter entfernen. Wenn diese Prüfung jedoch entfernt wird, ist es wichtig, dass die Kundenserviceanfragen-Webvorlage entsprechend angepasst wird, da diese Webvorlage alle Benutzer daran hindert, Anfragen anzuzeigen, die aktiv sind und nicht im Web veröffentlicht werden. Wenn die Webvorlage nicht geändert wird, werden Anfragen in den Suchergebnissen angezeigt. Wenn Sie sie jedoch auswählen, wird die Seite mit den Anfragedetails mit dem Fehler "Berechtigung verweigert" angezeigt.

- **Wissensdatenbank**: Es können nur die Wissensartikel gesucht werden, die sich im Status **Veröffentlicht** befinden und bei denen das Feld **Intern** auf **Nein** festgelegt ist. Dieses Verhalten kann nicht geändert werden. Wissensartikel haben auch spezielle Funktionen in den Suchergebnissen, die wie folgt sind:

    - **Facets**: Es gibt zwei spezielle Facets, die nur für Wissensartikel verfügbar sind und angezeigt werden, wenn Wissensartikel-Datensätze in den Suchergebnissen vorhanden sind.

        - **Bewertungsfacet**: Dieses Facet ermöglicht Ihnen, die Suchergebnisse anhand der durchschnittlichen Bewertung von Wissensartikeln zu filtern.

        - **Produktfacet**: Dieses Facet ermöglicht Ihnen, die Suchergebnisse anhand des zu den Wissensartikeln gehörenden Produkts zu filtern.

    - **Anlagensuche**: Mit dieser Funktion können Sie innerhalb der Anhänge oder Notizen zu einem Wissensartikel suchen. Damit können Sie in der Notizbeschreibung, dem Titel, dem Dateinamen der Anlage und dem Inhalt der Anlage von Notizen oder Anhängen, die im Portal angezeigt werden, suchen. Weitere Informationen: [Suche in Dateianhangsinhalt](search-file-attachment.md)

## <a name="special-characters-and-syntax-supported-by-search"></a>Sonderzeichen und Syntax unterstützt durch Suche

Im Rahmen der globalen Suche im Portal werden eine Vielzahl von Sonderzeichen und Syntaxen unterstützt, um die Suchergebnisse besser zu filtern. Diese Sonderzeichen und Syntaxen sind grob in folgende Gruppen unterteilt:

- **Begriff**: Jede von einem Benutzer eingegebene Suchanfrage wird in Begriffe und Operatoren zerlegt. Im Folgenden finden Sie die verschiedenen Begriffe: 

    - **Einzelbegriff**: Einzelbegriff ist ein einzelnes Wort. Zum Beispiel würde eine Abfrage {hello world} in zwei einzelne Begriffe zerlegt, „hello“ und „world“. Jeder einzelne Begriff wird separat gesucht. Daher werden in der Abfrage {hello world} alle Datensätze mit dem Begriff „hello“ oder „world“ in den Suchergebnissen angezeigt.

    - **Phrasen**: Eine Phrase ist eine Gruppe von Begriffen, die von doppelten Anführungszeichen ("") umgeben sind. Zum Beispiel würde eine Abfrage {“hello world”} als Phrase „hello world“ analysiert werden. Jede Phrase wird komplett durchsucht. Daher werden in der Abfrage {“hello world”} alle Datensätze mit dem vollständigen Ausdruck „hello world“ in den Suchergebnissen angezeigt und alle Datensätze, die nur „hello“ oder „world“ enthalten, nicht angezeigt.

    Jede Suchanfrage kann aus einem oder mehreren dieser Begriffe beliebigen Typs bestehen, die durch Boolesche Operatoren zu komplexen Suchanfragen kombiniert werden.

- **Begriffsmodifizierer**

    - **Platzhaltersuche**: Es gibt zwei Arten von Platzhaltern, die innerhalb einzelner Begriffe von Suchabfragen verwendet werden können (nicht innerhalb von Phrasenabfragen): Platzhaltersuche für einzelne Zeichen und Platzhaltersuche für mehrere Zeichen.

        - **Einzelzeichen-Platzhaltersuche**: Um eine Einzelzeichen-Platzhaltersuche durchzuführen, verwenden Sie das Fragezeichen (?) Symbol. Die Einzelzeichen-Platzhaltersuche sucht nach Begriffen, die mit dem ersetzten Einzelzeichen übereinstimmen. Um beispielsweise nach "text" oder "test" zu suchen, können Sie die Suchanfrage als "te?t" verwenden.

        - **Mehrstellige Platzhaltersuche**: Um eine mehrstellige Platzhaltersuche durchzuführen, verwenden Sie das Sternchen (\*) Symbol. Bei der mehrstelligen Platzhaltersuche wird nach null oder mehr Zeichen gesucht. Um z.B. nach Test, Tests oder Tester zu suchen, können Sie die Suchanfrage als "test *" verwenden. Sie können auch eine mehrstellige Wildcard-Suche in der Mitte der Abfrage verwenden. Zum Beispiel "te*t".

        > [!NOTE]
        > - Sie können kein * oder ? Symbol als ersten Buchstaben einer Suche verwenden.
        > - Eine Platzhaltersuche kann nicht in einer Phrasenabfrage verwendet werden. Wenn Sie beispielsweise die Abfrage als "hell* world" verwenden, werden keine Ergebnisse mit dem Text "hello world" angezeigt.

    - **Umkreissuche**: Mit der Umkreissuche können Sie nach Wörtern suchen, die sich in einem bestimmten Abstand voneinander befinden. Wenn Sie zum Beispiel die Ergebnisse finden wollen, bei denen die Wörter "Bild" und "verschwommen" innerhalb von 10 Wörtern vorkommen, können Sie diese mit der Umkreissuche finden.
    
        Um die Umkreissuche durchzuführen, verwenden Sie das Tilde-Symbol (~) am Ende der Abfrage. Wenn Sie zum Beispiel die Ergebnisse finden wollen, bei denen die Wörter "Bild" und "verschwommen" innerhalb von 10 Wörtern vorkommen, dann wäre die Abfrage "Bild verschwommen"~10.

    - **Relevanz eines Begriffs erhöhen**: Die globale Suche liefert die Relevanz der gefundenen Dokumente basierend auf den gefundenen Begriffen. Um die Relevanz eines Begriffs zu erhöhen, verwenden Sie das Caret-Symbol (^) mit einem Verstärkungsfaktor (eine Zahl) am Ende des gesuchten Begriffs. Je höher der Verstärkungsfaktor, desto relevanter wird der Begriff.

        Mit der Erhöhung können Sie die Relevanz eines Dokuments steuern, indem Sie dessen Begriffe erhöhen. Wenn Sie z.B. nach Smart TV suchen und möchten, dass der Begriff "Smart" relevanter wird, erhöhen Sie ihn mit dem Symbol ^ und dem Verstärkungsfaktor neben dem Begriff. Sie würden eingeben: TV Smart^4. Dadurch werden Dokumente mit dem Begriff Smart relevanter.

        Sie können z. B. auch Phrasenbegriffe erhöhen: "Smart TV"^4 "Neuer Fernseher". In diesem Fall würde der Begriff "Smart TV" im Vergleich zu "New TV" verstärkt werden.

        Standardmäßig ist der Verstärkungsfaktor 1. Obwohl der Verstärkungsfaktor positiv sein muss, kann er kleiner als 1 sein (z. B. 0,2).

- **Boolesche Operatoren**: Boolesche Operatoren erlauben es, Begriffe durch logische Operatoren zu kombinieren. Die globale Suche unterstützt OR, AND, NOT, "+" und "-" als Boolesche Operatoren.

    > [!NOTE]
    > Boolesche Operatoren müssen in Großbuchstaben geschrieben werden.

    - **OR**: Der Operator OR ist der standardmäßige Verknüpfungsoperator. Das heißt, wenn zwischen zwei Begriffen kein Boolescher Operator steht, wird der Operator OR verwendet. Der Operator OR verknüpft zwei Begriffe und findet einen passenden Datensatz, wenn einer der Begriffe in einem Datensatz vorhanden ist. Dies entspricht einer Union-Anweisung. Das Symbol || kann anstelle des Wortes OR verwendet werden. Beispielsweise sucht die Suchanfrage "Smart TV" (ohne Anführungszeichen) nach allen Datensätzen mit dem Wort Smart oder TV. Diese Abfrage kann auch als "Smart OR TV", "Smart || TV" geschrieben werden.

    - **AND:** Der AND-Operator findet Datensätze, in denen beide Begriffe irgendwo im Text eines einzelnen Dokuments vorkommen. Dies entspricht einer Überschneidung mit Sets Das Symbol && kann anstelle des Wortes AND verwendet werden. Beispielsweise sucht die Suchanfrage "Smart AND TV" (ohne Anführungszeichen) nach allen Datensätzen mit dem Wort Smart und TV. Diese Abfrage kann auch als "Smart && TV" geschrieben werden.

    - **NOT**: Der NOT-Operator schließt Datensätze aus, die den Begriff nach NOT enthalten. Dies entspricht einer Unterscheidung mit Sets. Das Symbol ! anstelle des Wortes NOT verwendet werden. Beispielsweise sucht die Suchanfrage "Smart NOT TV" (ohne Anführungszeichen) nach allen Datensätzen, die das Wort Smart enthalten, aber nicht das Wort TV. Diese Abfrage kann auch als "Smart ! TV" geschrieben werden.

    - **Plus (+)-Symbol**: Das Plus (+)-Symbol, auch bekannt als der erforderliche Operator, setzt voraus, dass der Begriff nach dem "+"-Symbol irgendwo in einem Datensatz vorhanden ist. Beispielsweise sucht die Suchabfrage "Smart + TV" nach allen Datensätzen, bei denen das Wort TV vorhanden sein muss, und das Wort Smart kann auch vorhanden sein. 

    - **Minus (–)-Symbol**: Das Minus (-)-Symbol, auch als Verbotsoperator bekannt, schließt Dokumente aus, die den Begriff nach dem "-"-Symbol enthalten. Beispielsweise sucht die Suchanfrage "Smart - TV" nach allen Datensätzen, bei denen das Wort Smart vorhanden ist und das Wort TV nicht vorhanden sein darf.

- **Gruppierung**: Die globale Suche im Portal unterstützt die Verwendung von Klammern zur Gruppierung von Klauseln zur Bildung von Unterabfragen. Dies kann sehr nützlich sein, wenn Sie die boolesche Logik einer Abfrage steuern wollen. Wenn Sie z.B. nach allen Datensätzen suchen möchten, bei denen entweder einer der Begriffe "HD" oder "Smart" vorhanden ist, aber das Wort TV immer vorhanden ist, dann kann die Abfrage als "(HD oder Smart) AND TV" geschrieben werden (ausgenommen Anführungszeichen).

## <a name="liquid-search-tag"></a>Liquid-Suchtag

Sie können die globale Suche des Portals aus Liquid-Vorlagen aufrufen, indem Sie den searchindex-Tag verwenden. Weitere Informationen: [Suchindex](../liquid/portals-entity-tags.md#searchindex)

> [!IMPORTANT]
> Wenn Sie das searchindex-Tag verwenden, werden Facets nicht als Teil der Ergebnisse zurückgegeben und können auch nicht als Filter verwendet werden.

## <a name="update-search-index"></a>Suchindex aktualisieren

Suchindex-Updates in Power Apps-Portalen erfolgen automatisch wie die Cache-Invalidierung. Diese wichtigen Dinge sind jedoch zu beachten:

- Alle suchaktivierten Entitäten müssen das Metadatenfeld "Änderungsbenachrichtigung" aktiviert haben, da sonst keine der Änderungen an das Portal gemeldet werden und der Suchindex nicht aktualisiert wird.

- Es kann bis zu 30 Minuten dauern, bis alle Änderungen in einer Portalsuche angezeigt werden. 95 Prozent der Änderungen werden jedoch innerhalb von 15 Minuten aktualisiert. Bei Anlagen kann es, abhängig von der Größe der Anlage, länger dauern.

- Es ist ratsam, den vollständigen Index nach einer Massendatenmigration oder Massenaktualisierung von Datensätzen innerhalb kurzer Zeit manuell neu aufzubauen. Details siehe [Vollständigen Suchindex neu erstellen](#rebuild-full-search-index).

## <a name="rebuild-full-search-index"></a>Erstellen Sie den vollständigen Suchindex neu.

Das Wiederaufbauen des vollständigen Suchenindexes ist erforderlich, wenn:

- Sie nehmen eine Metadatenänderung an den Sucheigenschaften vor, wie z. B. das Ändern bestimmter abfragespezifischer Websiteeinstellungen oder das Ändern der Suchansicht einer Entität usw.
- Es werden Massendatenmigrationen oder Updates durchgeführt.
- Ein Webseiteneintrag, der Ihrem Portal zugeordnet ist, wird in einer Common Data Service-Umgebung geändert.

Sie können auch einen kompletten Suchindex von einem Portal aus neu aufbauen.
1.  Melden Sie sich beim Portal als Administrator an.
2.  Navigieren Sie wie folgt zur URL: `<portal_path>/_services/about`
3.  Wählen Sie **Suchindex neu erstellen**.

> [!IMPORTANT]
> Der vollständige Neuaufbau eines Index ist ein sehr kostspieliger Vorgang und sollte nicht während der Hauptnutzungszeiten durchgeführt werden, da dies Ihr Portal zum Erliegen bringen kann.

## <a name="remove-an-entity-from-global-search"></a>Entfernen einer Entität aus der globalen Suche

Manchmal gibt es Anforderungen, bestimmte Entitäten vollständig aus der globalen Suche des Portals zu entfernen, um sicherzustellen, dass Ihre Kunden schnell die richtigen Ergebnisse erhalten.

Im folgenden Beispiel wird die Anfrage-Entität aus der globalen Suche des Portals entfernt.

### <a name="step-1-block-case-entity-from-getting-indexed"></a>Schritt 1: Blockieren Sie die Indizierung der Anfrage-Entität.

Um zu verhindern, dass die Anfrage-Entität indiziert wird, müssen Sie die Ansicht der Anfrage-Entität umbenennen, die die Datensätze definiert, die vom Portal indiziert werden sollen (definiert durch die Websiteeeinstellung Suche/IndexQueryName). Standardmäßig ist der Name dieser Ansicht "Portalsuche".

1.  Gehen Sie zu https://make.powerapps.com und wählen Sie Lösungen. 

    ![Lösungen](../media/solutions-page.png)

1. Suchen Sie nach **Standardlösung** und wählen Sie dann zum Öffnen Bearbeiten.

    ![Lösung bearbeiten](../media/edit-solution.png)

1. Suchen und bearbeiten Sie **Anfrage** Entität, um ihre Komponenten zu sehen. 

1. Wählen Sie **Ansichten** und dann **Portalsuche**, um es in einem Ansichtseditor zu öffnen.

1. Benennen Sie im Ansichtseditor die Ansicht entsprechend Ihren Anforderungen um. Stellen Sie sicher, dass der neue Name nicht den Begriff *Portalsuche* enthält. 

1. Speichern und veröffentlichen Sie die Änderungen und schließen Sie den Ansichtseditor.

1. Erstellen Sie den vollständigen Index anschließend neu, wie im Abschnitt [Vollständigen Suchindex neu erstellen](#rebuild-full-search-index) beschrieben.

> [!NOTE]
> In diesem Beispiel werden die Änderungen in einer nicht verwalteten Ebene vorgenommen, indem Sie die Ansicht direkt bearbeiten. Sie können dies auch über eine verwaltete Lösung durchführen.

### <a name="step-2-remove-case-entity-from-the-ui"></a>Schritt 2: Anfrageentität aus der Benutzeroberfläche entfernen

Nach dem Ausführen von Aktionen wie in Schritt 1 beschrieben, wird die Anfrageentität nicht mehr indiziert. Um die Anfrageentität aus den Bereichen der Benutzeroberfläche zu entfernen, müssen Sie die mit der globalen Suche des Portals verknüpfte Websiteeinstellung ändern. Die folgende Websiteeinstellung muss geändert werden:

Suchen/Filter: Dadurch wird die Anfrageentität aus den Filtern auf der Suchseite sowie dem Suchfeld in der Kopfzeile der Website entfernt. Der Standardwert ist: `Content:adx_webpage,adx_webfile;Blogs:adx_blog,adx_blogpost;Forums:adx_communityforum,adx_communityforumthread,adx_communityforumpost;Ideas:adx_ideaforum,adx_idea;Help Desk:incident;Knowledge:knowledgearticle`

Sie müssen `Help Desk:incident;` aus dem Wert dieser Websiteeinstellung löschen, damit die Vorfallentität aus den Filtern entfernt wird, die sich neben dem Suchfeld in der Benutzeroberfläche befindet.

Der geänderte Wert ist:

`Content:adx_webpage,adx_webfile;Blogs:adx_blog,adx_blogpost;Forums:adx_communityforum,adx_communityforumthread,adx_communityforumpost;Ideas:adx_ideaforum,adx_idea;Knowledge:knowledgearticle`

Sobald diese Seiteneinstellung geändert wurde, wird die Anfrageentität aus den Filtern auf der Suchseite und in der Kopfzeile entfernt.

![Suche auf Seite](../media/search-on-page.png "Suche auf Seite")

![Suche in Kopfzeile](../media/search-in-header.png "Suche in Kopfzeile")
