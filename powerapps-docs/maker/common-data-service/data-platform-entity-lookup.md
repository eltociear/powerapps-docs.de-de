---
title: 'Erstellen einer Beziehung zwischen Entitäten, mithilfe eines Suchfelds | Microsoft Docs'
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
---

# <a name="create-a-relationship-between-entities"></a>Erstellen einer Beziehung zwischen Entitäten
Daten in einer Entität beziehen sich häufig auf Daten in einer anderen Entität. Beispielsweise haben Sie eine **Lehrer**- und **Klasse**-Entität, und die **Klasse**-Entität weist möglicherweise eine Suchbeziehung mit der **Lehrer**-Entität, um zu veranschaulichen, welcher Lehrer welche Klasse unterrichtet. Sie können ein Suchfeld verwenden, um Daten aus der Entität **Lehrer** anzuzeigen. Dies wird allgemein als ein Suchfeld bezeichnet.

## <a name="define-a-relationship"></a>Eine Beziehung definieren
Sie können verschiedene Beziehungstypen aus einer Entität zur anderen erstellen (oder zwischen einer Entität und sich selbst). Jede Entität kann eine Beziehung mit mehr als einer Entität haben und jede Entität kann mehr als eine Beziehung zu einer anderen Entität haben. Einige allgemeinen Beziehungstypen sind:

* **Viel zu eine** - In diesem Beziehungstyp kann jeder Datensatz in Entität A mit mehr als einem Datensatz in Entität B übereinstimmen , aber jeder Datensatz in Entität B kann nur einen Datensatz in Entität A entsprechen. Z. B. hat eine Klasse ein Klassenzimmer. Dies ist der gebräuchlichste Beziehungstyp und wird in der Feldliste als **Suchfeld** angezeigt
* **Eine zu viele** - In diesem Beziehungstyp kann jeder Datensatz in Entität B mit mehr als einem Datensatz in Entität A übereinstimmen , aber jeder Datensatz in Entität A kann nur einen Datensatz in Entität B entsprechen. Z. B. hat ein Lehrer, der mehrere Klassen unterrichtet.
* **Viele zu viele** - In diesem Beziehungstyp kann jeder Datensatz in Entität A mehr als einem Datensatz in Entität B entsprechen und umgekehrt. Beispielsweise besuchen Schüler viele Klassen, und jede Klasse kann mehrere Schüler haben.

## <a name="add-a-lookup-field-many-to-one-relationship"></a>Hinzufügen eines Suchfelds (Viele zu eine-Beziehung)

Um einer Entität eine Suchbeziehung hinzuzufügen, erstellen Sie eine Beziehung in der Registerkarte **Beziehungen** die geben Sie die Entität an, mit der Sie eine Beziehung erstellen möchten.

1. Auf [powerapps.com](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), erweitern Sie den Abschnitt **Daten** und klicken oder tippen Sie im linken Navigationsbereich **Entitäten**.

    ![Entitätsdetails](./media/data-platform-cds-create-entity/entitylist.png "Entitätsliste")

2. Klicken oder tippen Sie auf eine vorhandene Entität oder [Erstellen Sie eine neue Entität](data-platform-create-entity.md)

3. Klicken Sie auf **Beziehungen**.

4. Klicken Sie auf **Beziehung hinzufügen**. Dadurch wird ein neuer Bereich geöffnet, in dem Sie die Entität auswählen können, mit der Sie eine Beziehung erstellen möchten. Wählen Sie die Entität aus dem Dropdownmenü **Verknüpfte Entität** aus.

    > [!div class="mx-imgBorder"] 
    > ![Viele zu Eine-Beziehung](./media/data-platform-cds-newrelationship/manytoone-1.png "Viele zu Eine-Beziehung")

5. Wenn Sie eine Entität ausgewählt haben, werde die Suchfelder in der primären Entität angezeigt und standardmäßig dem Namen der Entitäten entsprechen (in diesem Beispiel Klassenzimmer), aber Sie können ihn nach Bedarf ändern.

    ![Viele zu Eine-Beziehung](./media/data-platform-cds-newrelationship/manytoone-2.png "Viele zu Eine-Beziehung")

6. Klicken Sie auf **Fertig**, um die Beziehung zu Ihrer Entität hinzuzufügen, und klicken Sie dann auf **Entität speichern**.

    > [!div class="mx-imgBorder"] 
    > ![Viele zu Eine-Beziehung](./media/data-platform-cds-newrelationship/manytoone-3.png "Viele zu Eine-Beziehung")

## <a name="add-a-one-to-many-relationship"></a>Eine Eine-zu-Viele-Beziehung hinzufügen

Um eine Eine-zu-Viele-Beziehung hinzuzufügen, erstellen Sie eine Beziehung in der Registerkarte **Beziehungen** die geben Sie die Entität an, mit der Sie eine Beziehung erstellen möchten.

1. Auf [powerapps.com](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), erweitern Sie den Abschnitt **Daten** und klicken oder tippen Sie im linken Navigationsbereich **Entitäten**.

    ![Entitätsdetails](./media/data-platform-cds-create-entity/entitylist.png "Entitätsliste")

2. Klicken oder tippen Sie auf eine vorhandene Entität oder [Erstellen Sie eine neue Entität](data-platform-create-entity.md)

3. Klicken Sie auf **Beziehungen**.

4. Klicken Sie auf den Pfeil nach unten auf der rechten Seite von **Beziehung hinzufügen**, damit Sie aus beiden Beziehungstypen auswählen können. Klicken Sie auf **Eine-zu-Viele** geklickt wird ein neuer, Bereich, damit Sie die Entität aus, für die Sie eine Beziehung erstellen möchten. Wählen Sie die Entität aus dem Dropdownmenü **Verknüpfte Entität** aus.

    ![Eine zu Viele-Beziehung](./media/data-platform-cds-newrelationship/onetomany-1.png "Eine zu viele-Beziehung")

5. Wenn Sie eine Entität festgelegt wurde, wird die sich auf alle Felder der primären Entität, sie ist Standard mit dem Entitätsnamen (in diesem Beispiel Klasse) angezeigt, aber Sie können ihn nach Bedarf ändern.

    > [!NOTE]
    > Bei 1:n-Beziehungen wird das Suchfeld in der verknüpften Entität und nicht in der Entität aktuell ausgewählten Entität erstellt. Wenn Sie die Suche in der aktuellen Entität brauchen, erstellen Sie bitte eine n:1-Beziehung.

    > [!div class="mx-imgBorder"] 
    > ![Eine zu Viele-Beziehung](./media/data-platform-cds-newrelationship/onetomany-2.png "Eine zu viele-Beziehung")

6. Klicken Sie auf **Fertig**, um die Beziehung zu Ihrer Entität hinzuzufügen, und klicken Sie dann auf **Entität speichern**.

    > [!div class="mx-imgBorder"] 
    > ![Eine zu Viele-Beziehung](./media/data-platform-cds-newrelationship/onetomany-3.png "Eine zu viele-Beziehung")

## <a name="add-a-many-to-many-relationship"></a>Eine viele zu viele-Beziehung hinzufügen

Momentan ist dies nur für das erweiterte Menü verfügbar. Klicken Sie in der PowerApps-Homepage im linken Menü auf "Erweitert". Informationen dazu, wie die Beziehung erstellt wird finden Sie unter [Erstellen von N:N-Beziehungen](/dynamics365/customer-engagement/customize/create-and-edit-nn-many-to-many-relationships)

## <a name="use-a-lookup-field-in-an-app"></a>Verwenden eines Suchfelds in einer App
Wenn Sie [automatisch eine App erstellen](../canvas-apps/data-platform-create-app.md), die aus einer Entität erstellt wird, die ein Suchfeld enthält, wird es als **Dropdown**-Steuerelement angezeigt, das Daten im Feld **Primärer Name** der Entität enthält.

## <a name="add-1n-and-nn-relationships-for-canvas-apps"></a>Hinzufügen von 1:N- und N:N-Beziehungen für Canvas-Anwendungen
Verwenden Sie die Funktion **Relate**, um zwei Datensätze über eine 1:n- oder n:n-Beziehung im Common Data Service zu verbinden. Mehr Informationen: [Verwandte und nicht verwandte Funktionen in PowerApps](../canvas-apps/functions/function-relate-unrelate.md)

## <a name="next-steps"></a>Nächste Schritte
* [Generieren einer App mit einer Common Data Service-Datenbank](../canvas-apps/data-platform-create-app.md)
* [Erstellen einer App von Grund auf einer Common Data Service-Datenbank](../canvas-apps/data-platform-create-app-scratch.md)

