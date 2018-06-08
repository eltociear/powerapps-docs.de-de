---
title: Erstellen eines Optionssatzes | Microsoft-Dokumentation
description: Hier finden Sie Schrittanleitungen zum Erstellen eines Optionssatzes.
author: clwesene
manager: kfile
ms.service: powerapps
ms.component: cds
ms.topic: conceptual
ms.date: 03/21/2018
ms.author: clwesene
ms.openlocfilehash: 188add46a8e52cfeb75ef1bb670ca3b457963024
ms.sourcegitcommit: 68fc13fdc2c991c499ad6fe9ae1e0f8dab597139
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34168594"
---
# <a name="create-an-option-set"></a>Erstellen eines Optionssatzes

Durch Optionssätze können Sie einem Benutzer innerhalb Ihrer App Dropdownlisten mit festen Werten hinzufügen, um die Datenkonsistenz zu gewährleisten. Diese werden in anderen Anwendungen manchmal als „Auswahlliste“ oder „Auswahlfeld“ bezeichnet. Ähnlich wie bei Entitäten gibt es Standardoptionssätze und die Möglichkeit, benutzerdefinierte Optionssätze für die Verwendung innerhalb Ihrer App zu erstellen.

Optionssätze können auf zwei Arten erstellt werden: aus der Liste „Optionssatz“ innerhalb des Portals oder direkt in einer Entität während der Erstellung eines Felds. Weitere Informationen zum Erstellen einer Entität finden Sie unter [Erstellen einer Entität](data-platform-create-entity.md).

## <a name="creating-an-option-set-while-adding-a-field"></a>Erstellen eines Optionssatzes während des Hinzufügens eines Felds

1. Erweitern Sie auf [powerapps.com](https://web.powerapps.com) den Bereich **Daten**, und klicken oder tippen Sie im linken Navigationsbereich auf **Entitäten**.

    ![Entitätsdetails](./media/data-platform-cds-create-entity/entitylist.png "Entitätsliste")

2. Klicken oder tippen Sie auf eine vorhandene Entität, oder [erstellen Sie eine neue Entität](data-platform-create-entity.md).

3. Fügen Sie ein neues Feld zu Ihrer Entität hinzu, indem Sie auf **Feld hinzufügen** klicken.

4. Geben Sie im Bereich „Neues Feld“ den **Anzeigenamen** für Ihr Feld ein. **Name** wird automatisch aufgefüllt und wird als eindeutiger Name für das Feld verwendet. Der **Anzeigename** wird verwendet, wenn das Feld Ihren Benutzern angezeigt wird. Der **Name** wird während des Erstellens Ihrer App in Ausdrücken und Formularen verwendet.

    ![Neues Feld](./media/data-platform-cds-create-entity/newfieldpanel.png "Bereich „Neues Feld“")

5. Klicken Sie auf die Dropdownliste **Datentyp**, und wählen Sie **Optionssatz** oder **Optionssatz mit Mehrfachauswahl** aus.

6. Klicken Sie auf die Dropdownliste **Optionssatz**, und wählen Sie **Neuer Optionssatz** aus.

    > [!NOTE]
    > Wenn ein vorhandener Optionssatz für Ihre Entität verwendet werden kann, können Sie diesen aus der Liste auswählen, ohne einen neuen zu erstellen.

    ![Liste „Optionssatz“](./media/data-platform-cds-newoptionset/fieldpanel-1.png "Option Set list")

7. Ein neuer Bereich wird geöffnet, um den Optionssatz zu erstellen. Der **Anzeigename** und der **Name** werden standardmäßig vom Namen des Felds abgeleitet, können jedoch nach Bedarf geändert werden. Klicken Sie auf **Neues Element hinzufügen**, um Ihre Liste von Optionen zu erstellen. Wiederholen Sie diesen Schritt, bis sämtliche Elemente erstellt wurden.

    ![Neuer Optionssatz](./media/data-platform-cds-newoptionset/field-optionsetpanel.png "New Option Set")

8. Wenn Sie Ihre Elemente eingegeben haben, klicken Sie auf **Speichern**, um Ihren Optionssatz zu erstellen.

    ![Neuer Optionssatz](./media/data-platform-cds-newoptionset/field-optionsetpanel-values.png "New Option Set")

9. Klicken Sie auf **Fertig**, um den Bereich „Neues Feld“ zu schließen. Klicken Sie dann auf **Entität speichern**, um Ihre Entität in Common Data Service zu speichern.

    > [!NOTE]
    > Sie können eines Ihrer Elemente als **Standard** für dieses Feld auswählen. Dieses wird standardmäßig ausgewählt, wenn Benutzer neue Datensätze in Ihrer Entität erstellen.

    ![Neues Feld](./media/data-platform-cds-newoptionset/fieldpanel-2.png "Bereich „Neues Feld“")

## <a name="creating-an-option-set-from-the-option-set-list"></a>Erstellen eines Optionssatzes aus der Liste „Optionssatz“

1. Erweitern Sie auf [powerapps.com](https://web.powerapps.com) den Bereich **Daten**, und klicken oder tippen Sie im linken Navigationsbereich auf **Optionssätze**.

    ![Optionssätze](./media/data-platform-cds-newoptionset/optionsetlist.png "Liste „Optionssatz“")

2. Klicken Sie auf **Neuer Optionssatz**.

3. Ein neuer Bereich wird geöffnet, um den Optionssatz zu erstellen. Geben Sie den **Anzeigenamen** und den **Namen** ein. Klicken Sie auf **Neues Element hinzufügen**, um Ihre Liste von Optionen zu erstellen. Wiederholen Sie diesen Schritt, bis sämtliche Elemente erstellt wurden.

    ![Optionssatz erstellen](./media/data-platform-cds-newoptionset/optionset-create.png "Option Set Create")

4. Wenn Sie Ihre Elemente eingegeben haben, klicken Sie auf **Speichern**, um Ihren Optionssatz zu erstellen.

    ![Neuer Optionssatz](./media/data-platform-cds-newoptionset/optionset-create-values.png "New Option Set")

5. Sie können diesen Optionssatz nun verwenden, indem Sie ein neues Feld in einer Entität erstellen.

## <a name="global-and-local-option-sets"></a>Globale und lokale Optionssätze

Standardmäßig werden Optionssätze als globale Optionssätze erstellt. Dadurch können diese für mehrere Entitäten verwendet werden. Beim Erstellen eines neuen Optionssatzes können Sie unter der Option **Mehr anzeigen** auswählen, einen Optionssatz **lokal** zu erstellen. Diese Option ist nicht über die Liste „Optionssatz“ verfügbar, sondern nur, wenn Sie einen Optionssatz erstellen, während Sie ein Feld hinzufügen. Lokale Optionssätze können nur von der Entität und dem Feld verwendet werden, für die sie erstellt wurden, nicht in anderen Entitäten. Dieser Ansatz wird nur erfahrenen Benutzern empfohlen, die einen lokalen Optionssatz benötigen.

> [!IMPORTANT]
> Sobald ein Optionssatz lokal oder global erstellt wurde, kann dies nicht mehr geändert werden.