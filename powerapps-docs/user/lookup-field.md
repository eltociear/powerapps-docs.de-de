---
title: Verwenden des Nachschlage Felds für einen Datensatz | MicrosoftDocs
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 10/28/2019
ms.author: mkaur
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: e2f267e0dd0b61324da381a3f7f7e13677b997ee
ms.sourcegitcommit: 7c1e70e94d75140955518349e6f9130ce3fd094e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2019
ms.locfileid: "73026081"
---
#  <a name="use-the-lookup-field-on-a-record"></a>Verwenden des Nachschlagefelds für einen Datensatz

Die Suche unterstützt Sie bei der Auswahl von Datensätzen aus einer verknüpften Entität. Wenn Sie eine verknüpfte Entität auswählen und Suchkriterien eingeben (z. b. einen Namen oder eine e-Mail-Adresse), beginnt die Suche automatisch mit der Auflösung des partiellen Texts und zeigt alle entsprechenden Datensätze Wenn keine Datensätze angezeigt werden, nachdem Sie den vollständigen Text Ihres Such Kriteriums eingegeben haben, wird eine Meldung angezeigt, die besagt, dass keine Datensätze vorhanden sind.

Beispielsweise können Sie nach dem Namen **Adrian dumitrascu**suchen. Wenn Sie **AD**eingeben, werden mögliche übereinstimmende Datensätze automatisch aufgefüllt und angezeigt.

  > [!div class="mx-imgBorder"]
  > ![Füllt automatisch übereinstimmende Datensätze auf](media/automatically-populate-matching-records.png "Füllt automatisch übereinstimmende Datensätze auf")
  
>[!NOTE] 
>Ein Administrator kann die Kriterien definieren, die von der Suche zum Auflösen von partiellem Suchtext verwendet werden.

Sie können auch einen neuen Datensatz erstellen, indem Sie die Schaltfläche **neu** auswählen. Sie müssen über ausreichende Berechtigungen verfügen, um die **neue** Schaltfläche anzuzeigen und einen Datensatz zu erstellen. Wenn Sie das Suchfeld auswählen, werden die fünf zuletzt verwendeten Datensätze zusammen mit fünf bevorzugten Datensätzen angezeigt. Welche Datensätze angezeigt werden, hängt von Ihrem Ansichts Verlauf und den Favoriten ab, die Sie angeheftet haben. 

Wenn Sie z. b. nur über drei Datensätze in ihrem Verlauf verfügen, werden diese drei in der Suche angezeigt, zusammen mit sieben ihrer bevorzugten Datensätze. Wenn Sie keine Favoriten angeheftet haben, werden nur die zuletzt angezeigten Datensätze angezeigt.

## <a name="types-of-lookups"></a>Typen von Such Vorgängen

Suchvorgänge werden wie folgt klassifiziert: 

- **Einfache Suche:** Wählen Sie einen einzelnen Datensatz in einem Feld aus einer einzelnen Entität aus. 

- **Partylist-Type-Felder:** Verwenden Sie, um mehrere Datensätze aus mehreren Entitäten in einer Suche auszuwählen. Verwenden Sie die Felder Partylist-Type, um mehrere Datensätze auszuwählen. Auf diese Weise können Sie jeden Datensatz hinzufügen, indem Sie eine neue Suche mehrmals durchführen. Jedes Mal, wenn Sie einen Datensatz auswählen, können Sie eine neue Suche nach einem anderen Datensatz durchführen.
  
- **Felder vom Typ "betrifft":** Verwenden Sie, um einen einzelnen Datensatz aus mehreren Entitäten in einer Suche auszuwählen. 

## <a name="search-in-a-lookup-field"></a>Suchen in einem Nachschlage Feld 
Wenn Sie nach einer Suche suchen möchten, wählen Sie das Textfeld aus, und geben Sie die Suchkriterien ein. Wenn die aktuellen Datensätze für Ihre Suche aktiviert sind, werden die aktuellen Datensätze angezeigt, wenn Sie das Textfeld auswählen.

  > [!div class="mx-imgBorder"]
  > ![Such Feld durchsuchen](media/MRU.png "Such Feld durchsuchen")  

## <a name="browse-in-a-lookup-field"></a>Suchen in einem Nachschlage Feld
Wenn Sie nach einer Suche suchen möchten, wählen Sie das Symbol für die Suche (Lupen) aus. Eine vollständige Liste der Elemente wird in der Dropdown Liste angezeigt.

  > [!div class="mx-imgBorder"]
  > ![Suchen eines Nachschlage Felds](media/MRU_1.png "Suchen eines Nachschlage Felds")  
 
## <a name="most-recently-used-record-type-images"></a>Zuletzt verwendete Abbild Daten Satz Typen
Die Liste der zuletzt verwendeten Datensätze zeigt ein Bild, das Sie bei der Unterscheidung zwischen Daten Satz Typen unterstützt.

  > [!div class="mx-imgBorder"]
  > ![Suchfelder zeigt Bild an](media/Lookup_03-MRU_Entity_Images_56[1].png "Suchfelder zeigt Bild an")  
  
## <a name="record-type-selection-list"></a>Auswahlliste für Daten Satz Typen  
Wenn Ergebnisse mehrere Daten Satz Typen umfassen, sehen Sie, wie viele Typen von Datensätzen vorhanden sind, und wählen Sie Sie aus der Liste aus.

  > [!div class="mx-imgBorder"]
  > ![Sehen Sie, wie viele Datensätze](media/Lookup_04-MultipleEntityTypes[1].gif "Sehen Sie, wie viele Datensätze")  
  
## <a name="create-a-new-record-if-you-dont-find-an-existing-record"></a>Neuen Datensatz erstellen, wenn kein vorhandener Datensatz gefunden wird

Wenn Sie keinen Datensatz finden, wählen Sie im Suchbereich **neu** aus, um einen neuen Datensatz zu erstellen.


### <a name="replace-an-existing-record-from-a-lookup-field"></a>Ersetzen eines vorhandenen Datensatzes aus einem Nachschlage Feld

Sie können einen vorhandenen Datensatz ersetzen, indem Sie einfache und in Bezug stehende Suchvorgänge verwenden. Suchen Sie nach einem Datensatz. Wählen Sie dann den Datensatz aus, und ersetzen Sie ihn durch einen neuen Datensatz.

### <a name="change-a-view-in-a-lookup-field"></a>Ändern einer Ansicht in einem Nachschlage Feld 

Durch die Auswahl von **Ansicht ändern** können Sie Folgendes bestimmen:
 - Wie Sie Datensätze anzeigen möchten, z. b. Kontakte, die **eingehalten werden**, **Kontaktansicht**oder **aktive Kontakte**.
 - Was Sie in den Datensätzen anzeigen möchten, z. b. Name, e-Mail-Adresse oder Telefonnummer. Wenn Sie z. b. nur die Kontakte anzeigen möchten, die Sie befolgen, wählen Sie Ansicht \> **Kontakte** **ändern** aus. Nur die folgenden Kontakte werden angezeigt, wie hier dargestellt. 

    ![Kontakt Typen für die Änderungs Ansicht](media/change-view.png "Kontakt Typen für die Änderungs Ansicht")

>[!IMPORTANT] 
>Die Option zum **Ändern der Ansicht** ist nicht sichtbar, wenn der Administrator die Option nicht für die Anzeige in ihren Ansichten konfiguriert hat.

### <a name="choose-from-multiple-records"></a>Aus mehreren Datensätzen auswählen

Wenn bei der Suche mehr Datensätze in einem Feld enthalten sind, als in den verfügbaren Anzeigebereich passen, wird der Anzeigebereich reduziert – d. h., die Datensätze, die in den Anzeigebereich passen, werden neben der Anzahl der Datensätze angezeigt, die nicht angezeigt werden. Wählen Sie die Zahl aus, um alle Datensätze anzuzeigen. Die folgenden Abbildungen zeigen den Unterschied zwischen reduzierten und nicht reduzierten Feldern.

**Prallte**

![Reduzierter Anzeigebereich für mehrfach Suche](media/collapsed-multi-lookup-display-area.png "Reduzierter Anzeigebereich für mehrfach Suche")


**Nicht reduziert:**

![Nicht reduzierter Anzeigebereich für mehrfach Suche](media/non-collapsed-multi-lookup-display-area.png "Nicht reduzierter Anzeigebereich für mehrfach Suche")
