---
title: Verwenden des Nachschlagefelds für einen Datensatz | Microsoft-Dokumentation
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 11/06/2019
ms.author: mkaur
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: bdb1b0bf1a500087f11804f6da55d1c3abe2eaf3
ms.sourcegitcommit: 6acc6ac7cc1749e9681d5e55c96613033835d294
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "3303551"
---
#  <a name="use-the-lookup-field-on-a-record"></a>Verwenden des Nachschlagefelds für einen Datensatz

Mit der Nachschlagefunktion können Sie Datensätze aus einer verknüpften Entität auswählen. Wenn Sie eine verknüpfte Entität auswählen und Suchkriterien eingeben (z. B. einen Namen oder eine E-Mail-Adresse), beginnt die Nachschlagefunktion automatisch mit der Auflösung des partiellen Texts und zeigt alle übereinstimmenden Datensätze an. Wenn nach der Eingabe des Volltextes Ihrer Suchkriterien keine Datensätze angezeigt werden, wird eine Meldung angezeigt, die besagt, dass es keine Datensätze gibt.

Sie können beispielsweise nach dem Namen **Adrian Dumitrascu** suchen. Wenn Sie eine **Anzeige** eingeben, werden mögliche übereinstimmende Datensätze automatisch ausgefüllt und angezeigt.

  > [!div class="mx-imgBorder"]
  > ![Füllt automatisch übereinstimmende Datensätze](media/automatically-populate-matching-records.png "Übereinstimmende Datensätze werden automatisch aufgefüllt")
  
>[!NOTE] 
>Ein Administrator kann die Kriterien definieren, die die Nachschlage für die Auflösung von Teilsuchtexten verwendet.

Außerdem können Sie einen neuen Datensatz erstellen, indem Sie auf die Schaltfläche **Neu** klicken. Sie müssen über ausreichende Berechtigungen verfügen, um die Schaltfläche **Neu** anzuzeigen und einen Datensatz zu erstellen. Wenn Sie das Suchfeld auswählen, werden die fünf zuletzt verwendeten Datensätze zusammen mit fünf Favoriten angezeigt. Welche Datensätze angezeigt werden, hängt von Ihrem Ansichtsverlauf und den Favoriten ab, die Sie festgelegt haben. 

Wenn Sie beispielsweise nur drei Datensätze in Ihrer Historie haben, zeigt die Suchfunktion diese drei zusammen mit sieben Ihrer Lieblingsdatensätze an. Wenn Sie keine Favoriten angeheftet haben, werden nur die zuletzt verwendeten Datensätze angezeigt.

## <a name="types-of-lookups"></a>Nachschlagearten

Nachschlagevorgänge werden folgendermaßen klassifiziert: 

- **Einfaches Nachschlagen:** Wählen Sie einen einzelnen Datensatz in einem Feld aus einer einzelnen Entität aus. 

- **Felder vom Typ PartyList:** Verwenden Sie diese Option, um mehrere Datensätze aus mehreren Entitäten in einer Suche auszuwählen. Verwenden Sie Felder vom Typ Partyliste, um mehrere Datensätze auszuwählen. Auf diese Weise können Sie jeden Datensatz hinzufügen, indem Sie eine neue Suche durchführen, und zwar mehrmals. Jedes Mal, wenn Sie einen Datensatz auswählen, können Sie eine neue Suche nach einem anderen Datensatz durchführen.
  
- **Felder vom Typ Regarding:** Verwenden Sie diese Option, um einen einzelnen Datensatz aus mehreren Entitäten in einer Suche auszuwählen. 

## <a name="search-in-a-lookup-field"></a>Suche in einem Nachschlagefeld 
Sie können über ein Nachschlagefeld suchen, indem Sie auf das Textfeld klicken und ihre Suchkriterien eingeben. Wenn zuletzt verwendete Datensätze für das Nachschlagen aktiviert sind, werden diese angezeigt, wenn Sie auf das Textfeld klicken.

  > [!div class="mx-imgBorder"]
  > ![Durchsuchen eines Nachschlagefelds](media/MRU.png "Durchsuchen eines Nachschlagefelds")  
  
>[!NOTE]   
> Das Standardsuchergebnis für die Nachschlagesuche ist **Beginnt mit**. Das bedeutet, dass die Ergebnisse Datensätze sind, die mit einem bestimmten Wort beginnen. Wenn Sie z. B. nach **Alpine Ski House** suchen möchten, geben Sie **alp** in das Suchfeld ein. Wenn Sie **ski** eingeben, wird der Datensatz nicht im Suchergebnis angezeigt.
>
> Verwenden Sie für eine Platzhaltersuche Sternchen: Geben Sie beispielsweise \*ski oder \*ski\* ein.

## <a name="browse-in-a-lookup-field"></a>Durchsuchen eines Nachschlagefelds
Sie können das Nachschlagefeld durchsuchen, indem Sie auf das Nachschlagesymbol (Lupe) klicken. Ein Dropdownmenü mit allen Elementen wird daraufhin angezeigt.

  > [!div class="mx-imgBorder"]
  > ![Durchsuchen eines Nachschlagefelds](media/MRU_1.png "Durchsuchen eines Nachschlagefelds")  
 
## <a name="most-recently-used-record-type-images"></a>Bilder für zuletzt verwendete Datensatztypen
In der Liste der zuletzt verwendeten Datensätze werden Bilder angezeigt, damit Sie die Datensatztypen unterscheiden können.

>[!NOTE] 
>Zuletzt verwendete Datensätze werden nicht nach Suchbegriff, ausgewählter Ansicht oder zugehörigen Datensätzen gefiltert.

  > [!div class="mx-imgBorder"]
  > ![Nachschlagefeld mit Bild](media/Lookup_03-MRU_Entity_Images_56[1].png "Nachschlagefeld mit Bild")  
  
## <a name="record-type-selection-list"></a>Auswahlliste für Datensatztyp  
Wenn die Ergebnisse mehrere Datensatztypen umfassen, wird angezeigt, wie viele Datensatztypen vorliegen. Dann können Sie diese aus der Liste auswählen.

  > [!div class="mx-imgBorder"]
  > ![Anzahl der Datensätze](media/Lookup_04-MultipleEntityTypes[1].gif "Anzahl der Datensätze")  
  
## <a name="create-a-new-record-if-you-dont-find-an-existing-record"></a>Erstellen eines neuen Datensatzes, wenn kein Datensatz vorhanden ist

Wenn Sie einen Datensatz nicht finden, wählen Sie im Suchbereich **Neu**, um einen neuen Datensatz anzulegen.


### <a name="replace-an-existing-record-from-a-lookup-field"></a>Ersetzt einen vorhandenen Datensatz aus einem Nachschlagefeld.

Sie können einen vorhandenen Datensatz ersetzen, indem Sie einfache und betrachtende Lookups verwenden. Suche nach einem Datensatz. Wählen Sie dann den Datensatz aus und ersetzen Sie ihn durch einen neuen Datensatz.

### <a name="change-a-view-in-a-lookup-field"></a>Ändern einer Ansicht in einem Nachschlagefeld 

Durch die Auswahl von **Ansicht ändern** können Sie festlegen:
 - Wie Sie Datensätze wie z. B. **Verfolgte Kontakte**, **Kontakte-Nachschlageansicht** oder **Aktive Kontakte** anzeigen möchten.
 - Was Sie in den Datensätzen anzeigen möchten, wie z. B. Name, E-Mail oder Telefonnummer. Wenn Sie beispielsweise nur die Kontakte anzeigen möchten, denen Sie folgen, wählen Sie **Ansicht ändern** \> **Kontakte ändern, die verfolgt werden**. Wie hier veranschaulicht wird, werden nur die Kontakte angezeigt, denen Sie folgen. 

    ![Ändern der angezeigten Kontakte](media/change-view.png "Ändern der angezeigten Kontakte")

### <a name="filter-by-only-my-records-or-filter-by-related-primary-contact"></a>Filterung nach eigenen Datensätzen oder nach entsprechendem Hauptkontakt

Wenn Sie zusätzliche Filter anwenden möchten, klicken Sie im Menü **Ansicht ändern** auf die Option **Only my records** (Nur meine Datensätze) oder auf **Filter by related Primary Contact** (Nach entsprechendem Hauptkontakt filtern).

![Hinzufügen weiterer Filter](media/extra_filters.png "Hinzufügen weiterer Filter")

### <a name="choose-from-multiple-records"></a>Auswahl aus mehreren Datensätzen

Wenn bei der Suche mehr Datensätze in einem Feld enthalten sind als in den verfügbaren Anzeigebereich passen, wird der Anzeigebereich reduziert. Neben den Datensätzen, die in den Anzeigebereich passen, wird dann die Anzahl der Datensätze angezeigt, die nicht angezeigt werden. Um alle Datensätze anzuzeigen, wählen Sie die Nummer aus. Die folgenden Bilder zeigen den Unterschied zwischen zusammengeklappten und nicht zusammengeklappten Feldern.

**Zusammengeklappt:**

![Zusammengeklappter Multi-Lookup-Anzeigebereich](media/collapsed-multi-lookup-display-area.png "Reduzierter Anzeigebereich für Mehrfachsuche")


**Nicht zusammengeklappt:**

![Nicht reduzierter Anzeigebereich für Mehrfachsuche](media/non-collapsed-multi-lookup-display-area.png "Nicht reduzierter Anzeigebereich für Mehrfachsuche")
