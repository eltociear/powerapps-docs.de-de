---
title: Erstellen einer Beziehung zwischen Entitäten, mithilfe eines Suchfelds | Microsoft Docs
description: Schrittweise Anleitung zur Erstellung einer Beziehung zwischen Entitäten in PowerApps mithilfe eines Suchfelds.
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.component: cds
ms.topic: conceptual
ms.date: 02/21/2019
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: ac4b57853e6dfc4c0969a4207538e15db0b58bc8
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "2757530"
---
# <a name="create-a-relationship-between-entities"></a>Erstellen einer Beziehung zwischen Entitäten
Daten in einer Entität beziehen sich häufig auf Daten in einer anderen Entität. Beispielsweise haben Sie eine **Lehrer**- und **Klasse**-Entität, und die **Klasse**-Entität weist möglicherweise eine Suchbeziehung mit der **Lehrer**-Entität, um zu veranschaulichen, welcher Lehrer welche Klasse unterrichtet. Sie können ein Suchfeld verwenden, um Daten aus der Entität **Lehrer** anzuzeigen. Dies wird allgemein als ein Suchfeld bezeichnet.

## <a name="define-a-relationship"></a>Eine Beziehung definieren
Sie können verschiedene Beziehungstypen aus einer Entität zur anderen erstellen (oder zwischen einer Entität und sich selbst). Jede Entität kann eine Beziehung mit mehr als einer Entität haben und jede Entität kann mehr als eine Beziehung zu einer anderen Entität haben. Einige allgemeinen Beziehungstypen sind:

* **Viel zu eine** - In diesem Beziehungstyp kann jeder Datensatz in Entität A mit mehr als einem Datensatz in Entität B übereinstimmen , aber jeder Datensatz in Entität B kann nur einen Datensatz in Entität A entsprechen. Z. B. hat eine Klasse ein Klassenzimmer. Dies ist der gebräuchlichste Beziehungstyp und wird in der Feldliste als **Suchfeld** angezeigt
* **Eine zu viele** - In diesem Beziehungstyp kann jeder Datensatz in Entität B mit mehr als einem Datensatz in Entität A übereinstimmen , aber jeder Datensatz in Entität A kann nur einen Datensatz in Entität B entsprechen. Z. B. hat ein Lehrer, der mehrere Klassen unterrichtet.
* **Viele zu viele** - In diesem Beziehungstyp kann jeder Datensatz in Entität A mehr als einem Datensatz in Entität B entsprechen und umgekehrt. Beispielsweise besuchen Schüler viele Klassen, und jede Klasse kann mehrere Schüler haben.

Darüber hinaus können Sie erweitertes Kaskadierungsverhalten bei n: 1 und 1: n-Beziehungen festlegen, wenn für die übergeordnete Entität eine Aktion ausgeführt wird.

## <a name="add-a-lookup-field-many-to-one-relationship"></a>Hinzufügen eines Suchfelds (Viele zu eine-Beziehung)

Um einer Entität eine Suchbeziehung hinzuzufügen, erstellen Sie eine Beziehung in der Registerkarte **Beziehungen** die geben Sie die Entität an, mit der Sie eine Beziehung erstellen möchten.

1. Auf [powerapps.com](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), erweitern Sie den Abschnitt **Daten** und klicken oder tippen Sie im linken Navigationsbereich **Entitäten**.

2. Klicken oder tippen Sie auf eine vorhandene Entität oder [Erstellen Sie eine neue Entität](data-platform-create-entity.md)

3. Klicken Sie auf **Beziehungen**.

4. Klicken Sie auf **Beziehung hinzufügen**. Dadurch wird ein neuer Bereich geöffnet, in dem Sie die Entität auswählen können, mit der Sie eine Beziehung erstellen möchten. Wählen Sie die Entität aus dem Dropdownmenü **Verknüpfte Entität** aus.

    > [!div class="mx-imgBorder"] 
    > ![n:1-Beziehung](./media/data-platform-cds-newrelationship/manytoone-1.png "n:1-Beziehung")

5. Wenn Sie eine Entität ausgewählt haben, werden die Suchfelder in der primären Entität angezeigt, die standardmäßig dem Namen der Entität entsprechen (in diesem Beispiel Klassenzimmer), aber Sie können ihn nach Bedarf ändern.

    ![n:1-Beziehung](./media/data-platform-cds-newrelationship/manytoone-2.png "n:1-Beziehung")

6. Klicken Sie auf **Fertig**, um die Beziehung zu Ihrer Entität hinzuzufügen, und klicken Sie dann auf **Entität speichern**.

    > [!div class="mx-imgBorder"] 
    > ![n:1-Beziehung](./media/data-platform-cds-newrelationship/manytoone-3.png "n:1-Beziehung")

## <a name="add-a-one-to-many-relationship"></a>Eine Eine-zu-Viele-Beziehung hinzufügen

Um eine Eine-zu-Viele-Beziehung hinzuzufügen, erstellen Sie eine Beziehung in der Registerkarte **Beziehungen** die geben Sie die Entität an, mit der Sie eine Beziehung erstellen möchten.

1. Auf [powerapps.com](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), erweitern Sie den Abschnitt **Daten** und klicken oder tippen Sie im linken Navigationsbereich **Entitäten**.

2. Klicken oder tippen Sie auf eine vorhandene Entität oder [Erstellen Sie eine neue Entität](data-platform-create-entity.md)

3. Klicken Sie auf **Beziehungen**.

4. Klicken Sie auf den Pfeil nach unten auf der rechten Seite von **Beziehung hinzufügen**, damit Sie aus beiden Beziehungstypen auswählen können. Klicken Sie auf **Eine-zu-Viele** geklickt wird ein neuer, Bereich, damit Sie die Entität aus, für die Sie eine Beziehung erstellen möchten. Wählen Sie die Entität aus dem Dropdownmenü **Verknüpfte Entität** aus.
    > [!div class="mx-imgBorder"] 
    > ![1:n-Beziehung](./media/data-platform-cds-newrelationship/onetomany-1.png "1:n-Beziehung")

5. Wenn Sie eine Entität festgelegt wurde, wird die sich auf alle Felder der primären Entität, sie ist Standard mit dem Entitätsnamen (in diesem Beispiel Klasse) angezeigt, aber Sie können ihn nach Bedarf ändern.

    > [!NOTE]
    > Bei 1:n-Beziehungen wird das Suchfeld in der verknüpften Entität und nicht in der Entität aktuell ausgewählten Entität erstellt. Wenn Sie die Suche in der aktuellen Entität brauchen, erstellen Sie bitte eine n:1-Beziehung.

    > [!div class="mx-imgBorder"] 
    > ![1:n-Beziehung](./media/data-platform-cds-newrelationship/onetomany-2.png "1:n-Beziehung")

6. Klicken Sie auf **Fertig**, um die Beziehung zu Ihrer Entität hinzuzufügen, und klicken Sie dann auf **Entität speichern**.

    > [!div class="mx-imgBorder"] 
    > ![1:n-Beziehung](./media/data-platform-cds-newrelationship/onetomany-3.png "1:n-Beziehung")

## <a name="add-a-many-to-many-relationship"></a>Eine viele zu viele-Beziehung hinzufügen
Um eine Viele-zu-Viele-Beziehung hinzuzufügen, erstellen Sie eine Beziehung in der Registerkarte **Beziehungen**. Die geben Sie der Entität an, mit der Sie eine Beziehung erstellen möchten.

1. Auf [powerapps.com](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), erweitern Sie den Abschnitt **Daten** und klicken oder tippen Sie im linken Navigationsbereich **Entitäten**.

2. Klicken oder tippen Sie auf eine vorhandene Entität oder [Erstellen Sie eine neue Entität](data-platform-create-entity.md)

3. Klicken Sie auf **Beziehungen**.

4. Klicken Sie auf den Pfeil nach unten auf der rechten Seite von **Beziehung hinzufügen**, damit Sie aus beiden Beziehungstypen auswählen können. Klicken Sie auf **Viele-zu-Viele**. Damit wird ein neuer, Bereich geöffnet, in dem Sie die Entität auswählen, für die Sie eine Beziehung erstellen möchten. Wählen Sie die Entität aus dem Dropdownmenü **Verknüpfte Entität** aus.

5. Wenn Sie eine Entität ausgewählt haben, erscheinen die Namen für die Beziehung und die Beziehungsentität. Sie entsprechen standardmäßig den Namen der kombinierten Entitäten, aber Sie können sie nach Bedarf ändern.

    > [!div class="mx-imgBorder"] 
    > ![m:n-Beziehungen](./media/data-platform-cds-newrelationship/manytomany-1.png "m:n-Beziehungen")

6. Klicken Sie auf **Fertig**, um die Beziehung zu Ihrer Entität hinzuzufügen, und klicken Sie dann auf **Entität speichern**.


## <a name="add-advanced-relationship-behavior"></a>Hinzufügen erweiterten Beziehungsverhaltens

Beim Erstellen eines 1: n- oder n: 1-Beziehung können Sie auch erweitertes Verhalten festlegen.

![Erweitertes Verhalten](./media/data-platform-cds-newrelationship/advanced-1.png "Erweitertes Verhalten")

Diese Optionen werden auch als kaskadierende Verhaltensweisen bezeichnet, da sie die Hierarchie der verknüpften Entitäten hinab kaskadieren. Beispielsweise kann es erwünscht sein, die verwandten Tests und Hausaufgaben eines Schülers zu löschen, wenn ein Schüler aus dem System entfernt wird. Dieser Verhaltenstyp wird als übergeordnete Beziehung bezeichnet.

Andererseits entscheiden Sie möglicherweise, dass in der Hierarchie keine Aktionen nach unten kaskadieren sollen. Bei der Beziehung von Lehrer zur Klasse beispielsweise entscheiden Sie unter Umständen, dass die untergeordnete Entität (Klasse) *nicht* gelöscht wird, wenn ein übergeordnetes Element (Lehrer) gelöscht wird. Dies wird als eine verweisende Beziehung bezeichnet.

Während Sie Geschäftsdaten anpassen, indem Sie benutzerdefinierte Entitäten erstellen, oder wenn Sie vorhandene Common Data Model-Entitäten verwenden, erwägen Sie das Verhalten, das Sie benötigen und die Auswirkungen auf die gesamte Hierarchie der verknüpften Entitäten und wählen zwischen einer der folgenden Standardverhaltensweisen.

* **Referenziell, Verknüpfung entfernen:** Bei einer referenziellen Beziehung zwischen zwei Entitäten können Sie zu verknüpften Datensätzen wechseln. Aktionen, die Sie an einem Datensatz vornehmen, wirken sich jedoch nicht auf den anderen Datensatz aus. Wenn Sie z. B. eine 1: n-Beziehung zwischen Lehrern und Klassen haben, wirkt sich das Löschen eines Lehrers nicht auf auf der betreffenden Klasse aus.

* **Referenziell, Löschbeschränkung:** Bei einer solchen Beziehung zwischen zwei Entitäten können Sie zu verknüpften Datensätzen wechseln. Aktionen, die Sie am übergeordneten Datensatz vornehmen, wirken sich nicht auf den untergeordneten Datensatz aus. Der übergeordnete Datensatz kann jedoch nicht gelöscht werden, solange der untergeordnete Datensatz vorhanden ist. Dies ist hilfreich, wenn Sie untergeordnete Datensätze nicht verwaisen sollen. Dadurch muss der Benutzer alle untergeordneten Elemente löschen, bevor er das übergeordnete Element löscht.

    > [!div class="mx-imgBorder"] 
    > ![Referenziell, Löschbeschränkung](./media/data-platform-cds-newrelationship/advanced-3.png "Referenziell, Löschbeschränkung")

* **Übergeordnet:** Bei einer übergeordneten Beziehung zwischen zwei Entitäten wird jede Aktion für einen Datensatz der übergeordneten Entität auch für die Datensätze der untergeordneten Entitäten ausgeführt, die mit dem Datensatz der übergeordneten Entität verknüpft sind. Beispielsweise werden dadurch alle untergeordneten Datensätze gelöscht, wenn das übergeordnete Element gelöscht wird.

* **Angepasst:** In einer angepassten Beziehung zwischen zwei Entitäten wählen Sie das Verhalten, das mit einem Satz möglicher Aktionen verbunden ist. 

    > [!div class="mx-imgBorder"] 
    > ![Benutzerdefiniertes Verhalten](./media/data-platform-cds-newrelationship/advanced-2.png "Benutzerdefiniertes Verhalten")

Weitere Informationen zu Standardwerten und angepassten Verhaltensweisen: [Konfigurieren der Entitätsbeziehungsverhaltensweisen](entity-relationship-behavior.md).



## <a name="use-a-lookup-field-in-an-app"></a>Verwenden eines Suchfelds in einer App
Wenn Sie [automatisch eine App erstellen](../canvas-apps/data-platform-create-app.md), die aus einer Entität erstellt wird, die ein Suchfeld enthält, wird es als **Dropdown**-Steuerelement angezeigt, das Daten im Feld **Primärer Name** der Entität enthält.

## <a name="add-1n-and-nn-relationships-for-canvas-apps"></a>Hinzufügen von 1:N- und N:N-Beziehungen für Canvas-Anwendungen
Verwenden Sie die Funktion **Beziehung**, um zwei Datensätze über eine 1:n- oder m:n-Beziehung in Common Data Service zu verbinden. Mehr Informationen: [Verwandte und nicht verwandte Funktionen in PowerApps](../canvas-apps/functions/function-relate-unrelate.md)

## <a name="next-steps"></a>Nächste Schritte
* [Generieren Sie eine App, indem Sie Common Data Service verwenden](../canvas-apps/data-platform-create-app.md)
* [App ganz neu mit einer Common Data Service-Datenbank erstellen](../canvas-apps/data-platform-create-app-scratch.md)

