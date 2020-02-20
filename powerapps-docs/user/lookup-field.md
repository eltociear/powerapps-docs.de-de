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
ms.openlocfilehash: 4ef67695603f3badeba92f46c6da90e21715c98b
ms.sourcegitcommit: 01fefd7a06bf5d6509acd0bb54ea6479208cbbc8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/19/2019
ms.locfileid: "74177847"
---
#  <a name="use-the-lookup-field-on-a-record"></a>Verwenden des Nachschlagefelds für einen Datensatz

Mit der Nachschlagefunktion können Sie Datensätze aus einer verknüpften Entität auswählen. Wenn Sie eine verknüpfte Entität auswählen und Suchkriterien eingeben (z. B. einen Namen oder eine E-Mail-Adresse), beginnt die Nachschlagefunktion automatisch mit der Auflösung des partiellen Texts und zeigt alle übereinstimmenden Datensätze an. Wenn keine Datensätze angezeigt werden, nachdem Sie den vollständigen Text Ihres Suchkriteriums eingegeben haben, wird eine Meldung angezeigt, dass keine Datensätze vorhanden sind.

Beispielsweise könnten Sie nach dem Namen **Adrian Dumitrascu** suchen. Wenn Sie **ad** eingeben, werden mögliche übereinstimmende Datensätze automatisch aufgefüllt und angezeigt.

  > [!div class="mx-imgBorder"]
  > ![Übereinstimmende Datensätze werden automatisch aufgefüllt](media/automatically-populate-matching-records.png "Übereinstimmende Datensätze werden automatisch aufgefüllt")
  
>[!NOTE] 
>Ein Administrator kann die Kriterien festlegen, die die Nachschlagefunktion für das Auflösen partieller Suchtexte verwendet.

Sie können auch einen neuen Datensatz erstellen, indem Sie auf die Schaltfläche **Neu** klicken. Sie müssen über ausreichende Berechtigungen verfügen, damit die Schaltfläche **Neu** angezeigt wird und Sie einen Datensatz erstellen können. Wenn Sie das Nachschlagefeld auswählen, werden die fünf zuletzt verwendeten Datensätze und die fünf bevorzugten Datensätze angezeigt. Welche Datensätze angezeigt werden, hängt von Ihrem Ansichtsverlauf und den Favoriten ab, die Sie angeheftet haben. 

Wenn beispielsweise nur drei Datensätze in Ihrem Verlauf vorhanden sind, werden diese drei und sieben Ihrer bevorzugten Datensätze von der Nachschlagefunktion angezeigt. Wenn Sie keine Favoriten angeheftet haben, werden nur die zuletzt verwendeten Datensätze angezeigt.

## <a name="types-of-lookups"></a>Nachschlagearten

Nachschlagevorgänge werden folgendermaßen klassifiziert: 

- **Einfaches Nachschlagen:** Wählen Sie einen einzelnen Datensatz in einem Feld einer einzelnen Entität aus. 

- **PartyList-Felder:** Verwenden Sie diese, um mehrere Datensätze aus mehreren Entitäten beim Nachschlagen auszuwählen. Verwenden Sie PartyList-Felder, um mehrere Datensätze auszuwählen. So können Sie einzelne Datensätze hinzufügen, indem Sie mehrmals eine neue Suche durchführen. Jedes Mal, wenn Sie einen Datensatz auswählen, können Sie eine neue Suche nach einem anderen Datensatz durchführen.
  
- **Regarding-Felder:** Verwenden Sie diese, um einen Datensatz aus mehreren Entitäten beim Nachschlagen auszuwählen. 

## <a name="search-in-a-lookup-field"></a>Suche in einem Nachschlagefeld 
Sie können über ein Nachschlagefeld suchen, indem Sie auf das Textfeld klicken und ihre Suchkriterien eingeben. Wenn zuletzt verwendete Datensätze für das Nachschlagen aktiviert sind, werden diese angezeigt, wenn Sie auf das Textfeld klicken.

  > [!div class="mx-imgBorder"]
  > ![Durchsuchen eines Nachschlagefelds](media/MRU.png "Durchsuchen eines Nachschlagefelds")  
  
>[!NOTE]   
> Das Standardsuchergebnis für die Nachschlage suche ist „Beginnt mit“. Das bedeutet, dass die Ergebnisse Datensätze sind, die mit einem bestimmten Wort beginnen. Wenn Sie z. B. nach **Alpine Ski House** suchen möchten, geben Sie **alp** in das Suchfeld ein. Wenn Sie **ski** eingeben, wird der Datensatz nicht im Suchergebnis angezeigt.
>
> Bei einer Platzhaltersuche werden Sternchen verwendet: Geben Sie beispielsweise *ski oder *Ski ein.

## <a name="browse-in-a-lookup-field"></a>Durchsuchen eines Nachschlagefelds
Sie können das Nachschlagefeld durchsuchen, indem Sie auf das Nachschlagesymbol (Lupe) klicken. Ein Dropdownmenü mit allen Elementen wird daraufhin angezeigt.

  > [!div class="mx-imgBorder"]
  > ![Durchsuchen eines Nachschlagefelds](media/MRU_1.png "Durchsuchen eines Nachschlagefelds")  
 
## <a name="most-recently-used-record-type-images"></a>Bilder für zuletzt verwendete Datensatztypen
In der Liste der zuletzt verwendeten Datensätze werden Bilder angezeigt, damit Sie die Datensatztypen unterscheiden können.

>[!NOTE] 
>Zuletzt verwendete Datensätze werden nicht nach Suchbegriff oder ausgewählter Ansicht gefiltert.

  > [!div class="mx-imgBorder"]
  > ![Nachschlagefeld mit Bild](media/Lookup_03-MRU_Entity_Images_56[1].png "Nachschlagefeld mit Bild")  
  
## <a name="record-type-selection-list"></a>Auswahlliste für Datensatztyp  
Wenn die Ergebnisse mehrere Datensatztypen umfassen, wird angezeigt, wie viele Datensatztypen vorliegen. Dann können Sie diese aus der Liste auswählen.

  > [!div class="mx-imgBorder"]
  > ![Anzahl der Datensätze](media/Lookup_04-MultipleEntityTypes[1].gif "Anzahl der Datensätze")  
  
## <a name="create-a-new-record-if-you-dont-find-an-existing-record"></a>Erstellen eines neuen Datensatzes, wenn kein Datensatz vorhanden ist

Wenn Sie keine Datensätze finden, klicken Sie im Nachschlagebereich auf **Neu**, um einen neuen Datensatz zu erstellen.


### <a name="replace-an-existing-record-from-a-lookup-field"></a>Ersetzen eines vorhandenen Datensatzes über ein Nachschlagefeld

Sie können einen vorhandenen Datensatz ersetzen, während Sie einfache und Regarding-Nachschlagefunktionen nutzen. Suchen Sie nach einem Datensatz. Wählen Sie dann den Datensatz aus, und ersetzen Sie ihn durch einen neuen Datensatz.

### <a name="change-a-view-in-a-lookup-field"></a>Ändern der Ansicht in einem Nachschlagefeld 

Sie können Folgendes festlegen, indem Sie auf **Ansicht ändern** klicken:
 - Wie Datensätze wie **Contacts Being Followed** (Kontakte, denen Sie folgen), **Suchansicht: Kontakte** oder **Aktive Kontakte** angezeigt werden sollen
 - Welche Merkmale dieser Datensätze angezeigt werden sollen, z. B. Name, E-Mail-Adresse oder Telefonnummer: Wenn Sie beispielsweise nur die Kontakte anzeigen möchten, denen Sie folgen, klicken Sie auf **Ansicht ändern** \> **Contacts being followed** (Kontakte, denen Sie folgen). Wie hier veranschaulicht wird, werden nur die Kontakte angezeigt, denen Sie folgen. 

    ![Ändern der angezeigten Kontakte](media/change-view.png "Ändern der angezeigten Kontakte")

>[!IMPORTANT] 
>Die Option **Ansicht ändern** wird nicht angezeigt, wenn der Administrator nicht festgelegt hat, dass diese in Ihrer Ansicht angezeigt wird.

### <a name="choose-from-multiple-records"></a>Auswahl aus mehreren Datensätzen

Wenn bei der Suche mehr Datensätze in einem Feld enthalten sind als in den verfügbaren Anzeigebereich passen, wird der Anzeigebereich reduziert. Neben den Datensätzen, die in den Anzeigebereich passen, wird dann die Anzahl der Datensätze angezeigt, die nicht angezeigt werden. Klicken Sie auf die Zahl, um alle Datensätze anzuzeigen. Auf den folgenden Abbildungen werden die Unterschiede zwischen reduzierten und nicht reduzierten Feldern angezeigt.

**Reduziert:**

![Reduzierter Anzeigebereich für Mehrfachsuche](media/collapsed-multi-lookup-display-area.png "Reduzierter Anzeigebereich für Mehrfachsuche")


**Nicht reduziert:**

![Nicht reduzierter Anzeigebereich für Mehrfachsuche](media/non-collapsed-multi-lookup-display-area.png "Nicht reduzierter Anzeigebereich für Mehrfachsuche")
