---
title: Globale Suche in powerapps-Portalen | MicrosoftDocs
description: Erfahren Sie, wie die globale Suche in einem Portal funktioniert.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: da142a452e903b890b1b395262771228e245140c
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73551621"
---
# <a name="search"></a>Search

In den powerapps-Portalen können Sie mithilfe der globalen Suchfunktion des Portals nach Datensätzen über mehrere Entitäten suchen. Mithilfe der Suchfunktion für die Entitäts Liste können Sie auch in Datensätzen von Entitäts Listen suchen. 

Die Suchfunktion für die Entitäts Liste im Portal verwendet fetchxml im Back-End, um die in der Liste der Entitäten definierten Spalten zu durchsuchen und die Ergebnisse anzuzeigen. 

Die globale Suche verwendet einen externen Suchindex, der auf Lucene.NET basiert und verwendet wird, um in mehreren Entitäten und Feldern gleichzeitig zu suchen.

## <a name="global-search"></a>Globale Suche

Die globale Suche in Portalen ermöglicht Ihnen die Suche nach Datensätzen für mehrere Entitäten. Außerdem können Sie über mehrere Spalten hinweg suchen und konfigurieren, welche Spalten einer Entität durchsuchbar sind.

Zu den Vorteilen der globalen Suche zählen die folgenden Möglichkeiten:
- Findet Übereinstimmungen mit einem beliebigen Wort im Suchbegriff in einem beliebigen Feld in der Entität. Übereinstimmungen können flektionale Wörter wie Stream, Streaming oder Streaming einschließen.
- Gibt Ergebnisse aus allen durchsuchbaren Entitäten in einer einzelnen Liste nach Relevanz sortiert zurück, basierend auf Faktoren wie der Anzahl von übereinstimmenden Wörtern oder Ihrer Nähe zueinander im Text.
- Markieren Sie die Übereinstimmungen in den Suchergebnissen.
- Stellen Sie Facetten Optionen bereit, die zum weiteren Filtern von Suchergebnissen verwendet werden können.

Je besser die Übereinstimmung bei der globalen Suche ist, desto höher wird Sie in den Ergebnissen angezeigt. Eine Entsprechung hat eine höhere Relevanz, wenn mehr Wörter aus dem Suchbegriff in unmittelbarer Nähe zueinander gefunden werden. Je kleiner die Text Menge, in der die Suchwörter gefunden werden, desto höher die Relevanz. Wenn Sie z. b. die Suchbegriffe in einem Firmennamen und einer Adresse finden, ist dies möglicherweise eine bessere Übereinstimmung als die Wörter in einem großen Artikel, die weit voneinander getrennt sind. Da die Ergebnisse in einer einzelnen Liste zurückgegeben werden, sehen Sie eine Mischung aus Datensätzen, die nacheinander angezeigt werden, wobei die entsprechenden Funktionsweisen hervorgehoben sind. 

In den folgenden Abschnitten wird erläutert, wie die globale Suche in powerapps-Portalen funktioniert und die verschiedenen verfügbaren Konfigurationsoptionen beschrieben werden.

## <a name="entities-searchable-in-portal-global-search"></a>Entitäten durchsuchbar im Portal globale Suche

Die folgenden Entitäten können in einer Portal Website durchsucht werden, sofern die entsprechenden Projektmappenpakete installiert sind und die Suche zu einem Portal hinzugefügt wurde. Die indizierten Spalten bestehen aus den in der Such Ansicht gefundenen Spalten, die angepasst werden können.  Für jede Entität in der Liste ist der Standardsatz von Attributen indiziert, wie hier aufgeführt:
- Wissensartikel
    - Hinweise und Anhang eines Wissens Daten Bank Artikels sind ebenfalls durchsuchbar. Weitere Informationen: [Suchen in Datei Anlagen Inhalt](search-file-attachment.md)
    - Artikel können nur durchsucht werden, wenn Sie veröffentlicht werden und Ihr internes einziges Feld auf false festgelegt ist.
- Blog 
- Blog Beitrag 
- Blog Beitrag-Kommentar 
- Forum 
- Forumsbeitrag 
- Forums Thread 
- Idee 
- Ideen Kommentar 
- Ideen Forum 
- Webdatei 
    - Der Inhalt der Anlage ist auch durchsuchbar. Weitere Informationen: [Suchen in Datei Anlagen Inhalt](search-file-attachment.md)
- Webseite 
- Incident 

> [!NOTE]
> Abgesehen von den hier aufgeführten Entitäten können keine anderen Entitäten für die globale Suche in einem Portal aktiviert werden.

## <a name="fields-searchable-in-global-search"></a>In globaler Suche durch suchbare Felder

Alle Felder, die in der von der Such-/indexqueryname-Website Einstellung für eine Entität definierten Ansicht verfügbar sind, werden in der globalen Suche indiziert und sind durchsuchbar. 

Der Standardwert für Search/indexqueryname ist "Portal Suche".

Wenn die Sicht nicht für eine Entität verfügbar ist, wird Sie nicht indiziert, und die Ergebnisse werden nicht in der globalen Suche angezeigt.

> [!NOTE]
> Wenn Sie den Wert der Such-/indexqueryname-Website Einstellung ändern, müssen Sie einen manuellen neuindex des Builds mithilfe der im Abschnitt [Rebuild Full Search Index](#rebuild-full-search-index) definierten Schritte ausführen.

## <a name="related-site-settings"></a>Verwandte Site Einstellungen

Die folgenden Standorteinstellungen beziehen sich auf die globale Suche:

| Name    | Standardwert     | Beschreibung       |
|-----------------------|--------------------|-------------|
| Suchen/aktivieren | True  | Ein boolescher Wert, der angibt, ob die Suche aktiviert ist. Wenn Sie den Wert auf false festlegen, wird die globale Suche im Portal deaktiviert.<br>Wenn Sie voreingestellte Webvorlagen verwenden und diese Einstellung deaktivieren, wird das Suchfeld nicht in der Kopfzeile und auf der Suchseite angezeigt. Außerdem werden keine Ergebnisse zurückgegeben, auch wenn die direkte URL für die Suchseite getroffen wird.  |
| Suchen/filtern  | Inhalt: adx_webpage; Ereignisse: adx_event, adx_eventschedule; Blogs: adx_blog, adx_blogpost, adx_blogpostcomment; Foren: adx_communityforum, adx_communityforumthread, adx_communityforumpost; Ideen: adx_ideaforum, adx_idea, adx_ideacomment; Probleme: adx_issueforum, adx_issue, adx_issuecomment; Helpdesk: Incident | Eine Auflistung von Filteroptionen für den logischen Such Namen. Wenn Sie hier einen Wert definieren, werden dem globalen Suchvorgang Dropdown Filteroptionen hinzugefügt. Dieser Wert sollte in Form von Name-Wert-Paaren vorliegen, wobei Name und Wert durch einen Doppelpunkt getrennt sind, und Paare, die durch ein Semikolon voneinander getrennt sind. Beispiel: "Foren: adx_communityforum, adx_communityforumthread, adx_communityforumpost; Blogs: adx_blog, adx_blogpost, adx_blogpostcomment ".  |
| Search/indexqueryname   | Portal Suche  | Der Name der Systemansicht, die von der Portal Suchabfrage verwendet wird, um die Felder einer aktivierten Entität zu definieren, die indiziert und durchsucht werden.   |
| Suchen/Abfragen  | \+ (@Query) _title:(@Query) _logicalname: adx_webpage\~0.9 ^ 0,2-_logicalname: adx_webfile\~0,9 adx_partialurl:(@Query) _logicalname: adx_blogpost\~0.9 ^ 0,1-_logicalname: adx_communityforumthread\~0,9   | Diese Einstellung fügt der Abfrage, die ein Benutzer in das Standard Suchfeld eingibt, das im Portal angezeigt wird, zusätzliche Gewichtungen und Filter hinzu. Im Standardwert ist @Query der von einem Benutzer eingegebene Abfragetext.<br>Weitere Informationen zum Ändern dieses Werts finden Sie in der [Lucene-Abfrage Syntax](https://lucene.apache.org/core/old_versioned_docs/versions/2_9_1/queryparsersyntax.html).<br>**Wichtig**: Diese Gewichtung und Filterung gilt nur für das Suchfeld, das auf der Standard Suchseite des Portals angezeigt wird. Wenn Sie einen Liquid-Suchtag zum Erstellen einer eigenen Suchseite verwenden, gilt diese Einstellung nicht. |
| Suchen/Wort Stamm Erkennung  | Englisch    | Die Sprache, die vom Wort Stamm Algorithmus der Portal Suche verwendet wird.   |
| Suchen/facetedview  | True   | Dies ermöglicht Facetten in den Suchergebnissen. Wenn diese Einstellung auf "true" festgelegt ist, werden Facetten und Ergebnisse auf der Suchseite angezeigt.  |
| Such-/indexnotesanlagen   | True    | Gibt an, ob der Inhalt von Notizen Anlagen in Knowledge Base-Artikeln und-Webdateien indiziert werden soll. Standardmäßig ist der Wert auf false festgelegt. Weitere Informationen: [Suchen in Datei Anlagen Inhalt](search-file-attachment.md)    |
| Search/recordtypefaketsentities  | Blogs: adx_blog, adx_blogpost; Foren: adx_communityforum, adx_communityforumthread, adx_communityforumpost; Ideas: adx_ideaforum, adx_idea; Downloads: Annotation, adx_webfile    | Dadurch wird festgelegt, wie die Entitäten in der Daten Satz Typen auf der Suchseite gruppiert werden. Diese Einstellung weist das folgende Format auf: <br>"DisplayNameinRecordTypeFacet1:logicalnameofentity1,logicalnameofentity2; DisplayNameinRecordTypeFacet2:logicalnameofentity3,logicalnameofentity4" <br>Der Anzeige Name in der Datensatz-Typansicht wird in der Benutzeroberfläche angezeigt. Diese facetgruppe kombiniert das Ergebnis der Entitäten, die in der Konfiguration definiert sind.   |
| Knowledgemanagement/displaynotes | True   | Gibt an, ob Anlagen von Knowledge Base-Artikeln indiziert werden sollen. Standardmäßig ist der Wert auf false festgelegt. |
|||

## <a name="related-content-snippets"></a>Verwandte Inhalts Ausschnitte

Die folgenden Inhalts Ausschnitte stehen im Zusammenhang mit der globalen Suche:

| Name   | Standardwert  | Beschreibung   |
|------------------|-----------------|--------------------|
| Header/Suche/Bezeichnung| Search| Mit diesem Inhalts Ausschnitt wird der Wasserzeichen Text bestimmt, der im Suchfeld im Portal angezeigt wird.<br>![Bezeichnung suchen](../media/search-label.png "Bezeichnung suchen")    |
| Header/Suche/QuickInfo| Search  | Dieser Inhalts Ausschnitt bestimmt den QuickInfo-Text, der angezeigt wird, wenn Sie mit dem Mauszeiger auf das Suchsymbol im Portal Header zeigen.<br>![QuickInfo suchen](../media/search-tooltip.png "QuickInfo suchen")  |
| Suchen/Standard/Filtertext| Allen   | Dieser Inhalts Ausschnitt bestimmt den Standardtext, der in der Dropdown Liste Filter neben dem Suchfeld angezeigt wird.<br>![Suchfiltertext](../media/search-filter-text.png "Suchfiltertext")  |
| Suchen/Facetten/alle| Allen| Mit diesem Inhalts Ausschnitt wird der Standardtext, der für "alle Datensätze" angezeigt wird, im facettyp der Suchergebnisseite ermittelt.<br>![Alle Facetten](../media/facet-all.png "Alle Facetten") |
| Such-/Face-/Clear-Einschränkungen   | Alle löschen  | Dieser Inhalts Ausschnitt bestimmt die Bezeichnung der Schaltfläche, die alle auf der Seite Suchergebnisse angewendeten Facetten zurücksetzt.<br>![Alle Facetten zurücksetzen](../media/facet-clear-all.png "Alle Facetten zurücksetzen") |
| Suche/Facetten/Downloads   | Lädt   | Mit diesem Inhalts Ausschnitt wird die Bezeichnung bestimmt, die in den Suchergebnissen von Anmerkung-Anlagen und Webdatei Einträgen im facettyp "Datensatz" angezeigt wird.<br>![Facetten Download](../media/facet-download.png "Facetten Download")|
| Suche/Facetten/weniger    | Weniger anzeigen  | Dieser Inhalts Ausschnitt bestimmt die Bezeichnung der Schaltfläche, mit der Facetten Ergebnisse reduziert werden.<br>![Weniger Facetten anzeigen](../media/facet-show-less.png "Weniger Facetten anzeigen") |
| Suchen/Facetten/ModifiedDate  | Änderungsdatum  | Dieser Inhalts Ausschnitt bestimmt die Bezeichnung des Headers, der für den geänderten Datums Aspekt angezeigt wird.<br>![Änderungsdatum](../media/facet-modified-date.png "Modifizierter Datums Aspekt")   |
| Suche/Facetten/mehr   | Mehr anzeigen  | Dieser Inhalts Ausschnitt bestimmt die Bezeichnung der Schaltfläche, die facetergebnisse erweitert.<br>![Weitere Facetten anzeigen](../media/facet-show-more.png "Weitere Facetten anzeigen")  |
| Suche/Facette/Produkt  | Rodu | Mit diesem Inhalts Ausschnitt wird die Bezeichnung für den Produkt Aspekt bestimmt.<br>![Produkt Aspekt](../media/facet-product.png "Produkt Aspekt")  |
| Suche/Facetten/Bewertung   | Bewertung   | Mit diesem Inhalts Ausschnitt wird die Bezeichnung der Bewertungs Facette bestimmt.<br>![Bewertungs Aspekt](../media/facet-rating.png "Bewertungs Aspekt")  |
| Such-/Face-/Record-Typ   | Daten Satz Typen | Mit diesem Inhalts Ausschnitt wird die Bezeichnung des facettyp Aspekts bestimmt.<br>![Facetyp](../media/facet-record-type.png "Facetyp")     |
| Search/Face/sortor/averageuserrating | Durchschnittliche Benutzerbewertungen | Mit diesem Inhalts Ausschnitt wird die Bezeichnung festgelegt, die für die Option "nach durchschnittlicher Benutzerbewertungen sortieren" in der Dropdown Liste Sortierung auf der Seite mit den Suchergebnissen angezeigt wird.<br>![Nach durchschnittlicher Benutzer Bewertung sortieren](../media/sort-avg-user-rating.png "Nach durchschnittlicher Benutzer Bewertung sortieren")  |
| Suche/Facetten/sortor/Relevanz| Bedeutungs| Mit diesem Inhalts Ausschnitt wird die Bezeichnung festgelegt, die für die Option "nach Relevanz sortieren" in der Dropdown Liste Sortierung auf der Seite mit den Suchergebnissen angezeigt wird.<br>![Nach Relevanz sortieren](../media/sort-relevance.png "Nach Relevanz sortieren")|
| Suchen/Facetten/sortoren/Sichten| Ansichts Anzahl| Mit diesem Inhalts Ausschnitt wird die Bezeichnung festgelegt, die für die Option "Sortierung nach Ansichts Anzahl" in der Dropdown Liste "Sortierung" auf der Seite mit den Suchergebnissen angezeigt wird.<br>![Nach Ansichts Anzahl sortieren](../media/sort-view-count.png "Nach Ansichts Anzahl sortieren")|
|||

## <a name="entity-specific-handling"></a>Entitäts spezifische Behandlung

- **Groß-/Kleinschreibung**: die einzigen Fälle, die durchsucht werden können, befinden sich im Zustand " **aufgelöst** ", wenn das Feld **in Web veröffentlichen** auf **true**festgelegt ist. Dieses Verhalten kann geändert werden, indem Sie die Portal Suchansicht der Case-Entität aktualisieren und die in der Portal Such Ansicht verfügbaren Filter entfernen. Wenn diese Überprüfung jedoch entfernt wird, muss unbedingt sichergestellt werden, dass die Webvorlage Customer Service – Case entsprechend geändert wird, da diese Webvorlage alle Benutzer daran hindert, Fälle anzuzeigen, die aktiv sind und nicht im Web veröffentlicht werden. Wenn die Webvorlage nicht geändert wird, werden die Fälle in den Suchergebnissen angezeigt. Wenn Sie Sie jedoch auswählen, wird die Webseite mit dem Fall Detail mit dem Fehler "Berechtigung verweigert" angezeigt.

- **Knowledge Base**: Wissens Daten Bank Artikel können nur durchsucht werden, wenn Sie den Status " **veröffentlicht** " aufweisen und das **interne** Feld auf " **Nein**" festgelegt ist. Dieses Verhalten kann nicht geändert werden. Für Wissens Daten Bank Artikel stehen in den Suchergebnissen auch folgende besondere Funktionen zur Verfügung:

    - **Facetten**: zwei besondere Facetten sind nur für Wissens Daten Bank Artikel verfügbar und werden angezeigt, wenn in den Suchergebnissen Datensätze für Wissens Daten Bank Artikel verfügbar sind.

        - **Bewertungs Aspekt**: diese Facette ermöglicht Ihnen das Filtern von Suchergebnissen basierend auf der durchschnittlichen Bewertung von Wissens Daten Bank Artikeln.

        - **Produkt Aspekt**: diese Facette ermöglicht Ihnen das Filtern von Suchergebnissen basierend auf dem Produkt, das den Wissens Daten Bank Artikeln zugeordnet ist.

    - Anlagen **Suche**: Diese Funktion ermöglicht es Ihnen, in den Anlagen oder Notizen zu suchen, die einem Wissens Daten Bank Artikel zugeordnet sind. Auf diese Weise können Sie die Beschreibung, den Titel, den Anhang-Dateinamen und den Anlagen Inhalt von Notizen oder Anlagen, die im Portal verfügbar gemacht werden, suchen. Weitere Informationen: [Suchen in Datei Anlagen Inhalt](search-file-attachment.md)

## <a name="special-characters-and-syntax-supported-by-search"></a>Von Search unterstützte Sonderzeichen und Syntax

Im Rahmen der globalen Suche im Portal werden eine Vielzahl von Sonderzeichen und Syntaxen unterstützt, um die Suchergebnisse besser zu filtern. Diese Sonderzeichen und Syntaxen sind weitgehend in die folgenden Gruppen unterteilt:

- **Begriff**: jede von einem Benutzer für die Suche eingegebene Abfrage wird in Begriffe und Operatoren analysiert. Im folgenden sind die Arten von Begriffen aufgeführt: 

    - **Single Term**: Single Term ist ein einzelnes Wort. Beispielsweise würde eine Abfrage "{Hello World}" in zwei einzelne Begriffe analysiert werden: "Hello" und "World". Jeder einzelne Begriff wird separat durchsucht. In der Abfrage "{Hello World}" werden daher alle Datensätze mit dem Begriff "Hello" oder "World" in den Suchergebnissen angezeigt.

    - Ausdrücke **: ein**Ausdruck ist eine Gruppe von Begriffen, die in doppelten Anführungszeichen ("") eingeschlossen ist. Beispielsweise würde eine Abfrage "{" Hello World "} als Ausdruck" Hello World "analysiert werden. Jeder Ausdruck wird vollständig durchsucht. In der Abfrage "{" Hello World "} werden daher alle Datensätze mit dem vollständigen Ausdruck" Hello World "in den Suchergebnissen angezeigt, und alle Datensätze, die nur" Hello "oder" World "aufweisen, werden nicht angezeigt.

    Jede Suchabfrage kann aus einem oder mehreren dieser Begriffe eines beliebigen Typs bestehen, die mithilfe von booleschen Operatoren kombiniert werden, um komplexe Abfragen zu erstellen.

- **Benennungs modifiziererer**

    - Platzhalter **Suche**: Es gibt zwei Arten von Platzhaltern, die innerhalb einzelner Begriffe von Such Abfragen (nicht innerhalb von Ausdrucksabfragen) verwendet werden können: die Suche mit einem Platzhalter für einzelne Zeichen und die Suche nach mehreren Zeichen Platzhaltern.

        - Suche mit einem Platzhalter für **einzelne Zeichen**: Verwenden Sie das Fragezeichen Symbol (?), um die Suche nach einem einzelnen Zeichen Platzhalter auszuführen. Die Platzhalter Suche mit nur einem Zeichen sucht nach Begriffen, die mit dem jeweils ausgetauschten einzelnen Zeichen identisch sind. Wenn Sie z. b. nach "Text" oder "Test" suchen möchten, können Sie die Suchabfrage als "te? t" verwenden.

        - **Suche nach mehreren Zeichen**Platzhaltern: Verwenden Sie das Sternchen-Symbol (\*), um eine Suche nach einem Platzhalter für mehrere Zeichen auszuführen. Suchvorgänge für mehrere Zeichen suchen nach NULL oder mehr Zeichen. Wenn Sie z. b. nach Test, Tests oder Tester suchen möchten, können Sie die Suchabfrage als "Test *" verwenden. In der Mitte der Abfrage können Sie auch die Suche mit mehreren Zeichen Platzhaltern verwenden. Beispiel: "te*t".

        > [!NOTE]
        > - Sie können "*" oder "?" nicht verwenden. Symbol als erstes Zeichen einer Suche.
        > - Die Platzhalter Suche kann nicht in einer Ausdrucks Abfrage verwendet werden. Wenn Sie z. b. Abfrage als "hell * Welt" verwenden, werden keine Ergebnisse mit dem Text "Hello World" angezeigt.

    - **Near-Suche**: die Near-Suche ermöglicht Ihnen das Durchsuchen von Wörtern, die sich in einer bestimmten Entfernung voneinander befinden. Wenn Sie z. b. Ergebnisse für die Wörter "Bild" und "blurry" in 10 Wörtern zueinander sehen möchten, können Sie die Near-Suche verwenden.
    
        Verwenden Sie das tildesymbol (~) am Ende der Abfrage, um Near-Suchvorgänge durchzuführen. Wenn z. b. Ergebnisse für die Wörter "Bild" und "blurry" innerhalb von 10 Wörtern zueinander angezeigt werden sollen, wäre die Abfrage "Bild Blurry" ~ 10.

    - **Erhöhung eines Begriffs**: die globale Suche bietet die Relevanzstufe der übereinstimmenden Dokumente basierend auf den gefundenen Begriffen. Um einen Begriff zu erhöhen, verwenden Sie das Caretzeichen (^) mit einem Boost-Faktor (eine Zahl) am Ende des gesuchten Begriffs. Je höher der Boost Faktor ist, desto relevanter ist der Begriff.

        Mithilfe von Verstärkung können Sie die Relevanz eines Dokuments steuern, indem Sie den Begriff erhöhen. Wenn Sie z. b. nach Smart TV suchen und der Begriff "intelligent" relevanter sein soll, können Sie ihn mit dem Symbol "^" zusammen mit dem "Boost"-Faktor neben dem Begriff erhöhen. Geben Sie Folgendes ein: Smart ^ 4 TV. Dadurch werden Dokumente mit dem Begriff "Smart" relevanter angezeigt.

        Sie können auch Ausdrücken von Ausdrücken wie im folgenden Beispiel: Smart TV ^ 4 New TV. In diesem Fall würde der Ausdruck "Smart TV" im Vergleich zu "New TV" verstärkt werden.

        Standardmäßig ist der Boost-Faktor 1. Obwohl der Verstärkungsfaktor positiv sein muss, kann er kleiner als 1 sein (z. b. 0,2).

- **Boolesche Operatoren**: Boolesche Operatoren ermöglichen das Kombinieren von Begriffen durch Logik Operatoren. Die globale Suche unterstützt or, and, not, "+" und "-" als boolesche Operatoren.

    > [!NOTE]
    > Boolesche Operatoren müssen in Großbuchstaben geschrieben werden.

    - **Oder**: der or-Operator ist der standardmäßige konjunktionsoperator. Dies bedeutet, dass, wenn kein boolescher Operator zwischen zwei Begriffen vorhanden ist, der or-Operator verwendet wird. Der or-Operator verknüpft zwei Begriffe und findet einen übereinstimmenden Datensatz, wenn eines der Begriffe in einem Datensatz vorhanden ist. Dies entspricht einer Union mithilfe von Sets. Das Symbol | | kann anstelle des Worts oder verwendet werden. Beispielsweise wird durch die Suchabfrage "Smart TV" (ohne Anführungszeichen) nach allen Datensätzen gesucht, in denen das Wort Intelligent oder TV enthalten ist. Diese Abfrage kann auch als "Smart or TV", "Intelligent | | TV ".

    - **Und:** Der and-Operator entspricht Datensätzen, in denen beide Begriffe an beliebiger Stelle im Text eines einzelnen Dokuments vorhanden sind. Dies entspricht einer Schnittmenge unter Verwendung von Sets. Das Symbol & & kann anstelle des Worts und verwendet werden. Beispielsweise werden durch die Suchabfrage "Intelligent and TV" (ohne Anführungszeichen) alle Datensätze mit den Wörtern "intelligent" und "TV" durchsucht. Diese Abfrage kann auch als "Smart & & TV" geschrieben werden.

    - **Not**: der Not-Operator schließt Datensätze aus, die den Begriff after not enthalten. Dies entspricht einem Unterschied bei der Verwendung von Sets. Das Symbol! kann anstelle des Worts not verwendet werden. Die Suchabfrage "Smart Not TV" (ohne Anführungszeichen) sucht beispielsweise nach allen Datensätzen mit dem Wort "intelligent", aber nicht mit dem Wort "TV". Diese Abfrage kann auch als "Intelligent! TV ".

    - **Plus (+)-Symbol**: das Pluszeichen (+), auch als erforderlicher Operator bezeichnet, erfordert, dass der Begriff nach dem "+"-Symbol irgendwo in einem Datensatz vorhanden ist. Die Suchabfrage "Smart + TV" sucht beispielsweise nach allen Datensätzen, in denen das Wort "TV" vorhanden sein muss, und das Wort "Smart" ist möglicherweise ebenfalls vorhanden. 

    - **Minuszeichen (–)** : das Minuszeichen (-), das auch als Operator "verboten" bezeichnet wird, schließt Dokumente aus, die den Begriff nach dem Symbol "-" enthalten. Die Suchabfrage "Smart-TV" sucht z. b. nach allen Datensätzen, in denen das Wort Intelligent vorhanden ist, und das Wort TV darf nicht vorhanden sein.

- **Gruppierung**: die globale Suche im Portal unterstützt die Verwendung von Klammern zum Gruppieren von Klauseln zum bilden von Unterabfragen. Dies kann sehr nützlich sein, wenn Sie die boolesche Logik für eine Abfrage steuern möchten. Wenn Sie z. b. nach allen Datensätzen suchen möchten, in denen entweder eine der Begriffe "HD" oder "intelligent" vorhanden ist, aber das Wort TV immer vorhanden ist, kann die Abfrage als "(HD oder Intelligent) und TV" (ohne Anführungszeichen) geschrieben werden.

## <a name="liquid-search-tag"></a>Liquid-Suchtag

Sie können die globale Suche des Portals aus Liquid-Vorlagen mit dem Tag SearchIndex aufrufen. Weitere Informationen: [SearchIndex](../liquid/portals-entity-tags.md#searchindex)

> [!IMPORTANT]
> Wenn Sie das SearchIndex-Tag verwenden, werden Facetten nicht als Teil der Ergebnisse zurückgegeben und können nicht als Filter angewendet werden.

## <a name="update-search-index"></a>Suchindex aktualisieren

Such Index Updates in powerapps-Portalen werden automatisch wie die Cache Validierung ausgeführt. Beachten Sie die folgenden wichtigen Punkte:

- Für alle Such aktivierten Entitäten muss das Flag für die Änderungs Benachrichtigungs Metadaten aktiviert sein, da das Portal andernfalls nicht über die Änderungen benachrichtigt wird und der Suchindex nicht aktualisiert wird.

- Es kann bis zu 30 Minuten dauern, bis jede Änderung in einer Portal Suche berücksichtigt wird. 95 Prozent der Änderungen werden jedoch innerhalb von 15 Minuten aktualisiert. Wenn Anlagen beteiligt sind, kann es je nach Größe der Anlage länger dauern.

- Es ist ratsam, den vollständigen Index manuell neu zu erstellen, nachdem Sie eine Massendaten Migration oder Massen Aktualisierungen von Datensätzen innerhalb eines kurzen Zeitraums durchgeführt haben. Weitere Informationen finden Sie unter [Rebuild Full Search Index](#rebuild-full-search-index).

## <a name="rebuild-full-search-index"></a>Vollständigen Suchindex neu erstellen

Die Neuerstellung eines vollständigen Suchindexes ist immer erforderlich:

- Sie nehmen eine Änderung an den Such Eigenschaften vor, wie z. b. das Ändern bestimmter Abfrage spezifischer Standorteinstellungen oder das Ändern der Such Ansicht einer Entität usw.
- Massendaten Migration oder Updates werden ausgeführt.
- Ein Website Daten Satz, der Ihrem Portal zugeordnet ist, wird in einer Common Data Service Umgebung geändert.

Sie können auch einen vollständigen Suchindex aus einem Portal neu erstellen.
1.  Melden Sie sich beim Portal als Administrator an.
2.  Navigieren Sie wie folgt zur URL: `<portal_path>/_services/about`
3.  Wählen Sie **Such Index neu erstellen**aus.

> [!IMPORTANT]
> Eine vollständige indexneu Erstellung ist ein sehr aufwändiger Vorgang und sollte nicht während der Haupt Nutzungszeiten durchgeführt werden, da dadurch Ihr Portal heruntergefahren werden kann.

## <a name="remove-an-entity-from-global-search"></a>Entfernen einer Entität aus der globalen Suche

Manchmal müssen Sie bestimmte Entitäten aus der globalen Portal Suche vollständig entfernen, um sicherzustellen, dass Ihre Kunden schnell die richtigen Ergebnisse erhalten.

Im folgenden Beispiel wird die Entität "Case" aus der globalen Suche des Portals entfernt.

### <a name="step-1-block-case-entity-from-getting-indexed"></a>Schritt 1: Blockieren der Indizierung der Case-Entität

Wenn Sie die Indizierung der Case-Entität blockieren möchten, müssen Sie die Sicht der Case-Entität umbenennen, die den zu indizierenden Daten Satz Satz durch das Portal definiert (definiert durch die Site Einstellung Search/indexqueryname). Standardmäßig ist der Name dieser Ansicht Portal Suche.

1.  Öffnen Sie die [Portal Verwaltungs-App](configure-portal.md).

2.  Wählen Sie auf der Symbolleiste oben auf der Seite das Symbol " **Einstellungen** " aus, und wählen Sie dann **Erweiterte Einstellungen**aus.

2.  Wechseln Sie zu **Einstellungen** > **Anpassung** > **passen Sie das System**an.

    ![Anpassen des Systems](../media/customize-system.png "Anpassen des Systems")

3.  Wechseln Sie im Dialogfeld Anpassung im linken Navigationsbereich zu **Komponenten** > **Entitäten** > **Case** . 

4.  Erweitern Sie die **Case** -Entität, und wählen Sie **Sichten**

5.  Wählen Sie die **Portal Suchansicht** aus der Liste aus, und öffnen Sie Sie im Ansicht-Editor.

    ![Fall Ansicht](../media/case-view.png "Fall Ansicht")

6.  Wählen Sie im Ansicht-Editor **Eigenschaften anzeigen**aus.

    ![Editor anzeigen](../media/view-editor.png "Editor anzeigen")

7.  Benennen Sie die Ansicht entsprechend der Anforderung um. Stellen Sie sicher, dass der neue Name nicht den Begriff "Portal Suche" enthält.

    ![Eigenschaften anzeigen](../media/view-properties.png "Eigenschaften anzeigen")

8.  Speichern Sie die Änderungen, und schließen Sie den Ansichts-Editor.

9.  Wählen Sie **Alle Anpassungen veröffentlichen** aus.

10. Erstellen Sie den vollständigen Index neu, wie im Abschnitt [Rebuild Full Search Index](#rebuild-full-search-index) beschrieben.

> [!NOTE]
> In diesem Beispiel nehmen wir Änderungen an einer nicht verwalteten Ebene vor, indem wir die Ansicht direkt bearbeiten. Dies ist auch über eine verwaltete Lösung möglich.

### <a name="step-2-remove-case-entity-from-the-ui"></a>Schritt 2: Entfernen der Case-Entität aus der Benutzeroberfläche

Nachdem Sie die in Schritt 1 beschriebenen Aktionen durchgeführt haben, wird die Entität "Case" nicht mehr indiziert. Um die Case-Entität aus Oberflächen Oberflächen Bereichen zu entfernen, müssen Sie die Website Einstellungen ändern, die mit der globalen Portal Suche verknüpft sind. Die folgende Website Einstellung muss geändert werden:

suchen/filtern: Dadurch wird die Entität "Case" aus Filtern auf der Suchseite und das Suchfeld in der Kopfzeile der Website entfernt. Standardmäßig ist der Wert: `Content:adx_webpage,adx_webfile;Blogs:adx_blog,adx_blogpost;Forums:adx_communityforum,adx_communityforumthread,adx_communityforumpost;Ideas:adx_ideaforum,adx_idea;Help Desk:incident;Knowledge:knowledgearticle`

Sie müssen `Help Desk:incident;` aus dem Wert dieser Standort Einstellung löschen, damit die incidententität aus Filtern entfernt wird, die in der Benutzeroberfläche neben dem Suchfeld angezeigt werden.

Der geänderte Wert lautet wie folgt:

`Content:adx_webpage,adx_webfile;Blogs:adx_blog,adx_blogpost;Forums:adx_communityforum,adx_communityforumthread,adx_communityforumpost;Ideas:adx_ideaforum,adx_idea;Knowledge:knowledgearticle`

Nachdem diese Standort Einstellung geändert wurde, wird die Entität "Case" aus den Filtern auf der Suchseite und in der Kopfzeile entfernt.

![Auf Seite suchen](../media/search-on-page.png "Auf Seite suchen")

![In Kopfzeile suchen](../media/search-in-header.png "In Kopfzeile suchen")
