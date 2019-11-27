---
title: Erstellen eines Optionssatzes | Microsoft Docs
description: Schrittweise Anweisungen, um einem Optionssatz zu erstellen.
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.component: cds
ms.topic: conceptual
ms.date: 03/21/2018
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 6f3f47882800252c91de0efc572954f7397ac251
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "2757618"
---
# <a name="create-an-option-set"></a>Einen Optionssatz erstellen

Mit Optionssätzen können Sie Drop-Down-Listen mit festen Werten für einen Benutzer in Ihrer App einschließen, um die Datenkonsistenz sicherzustellen. Diese werden in anderen Anwendungen gelegentlich als Auswahllisten oder Auswahlfelder bezeichnet. Ähnlich wie bei Entitäten gibt es beide Standardoptionssätze und die Möglichkeit zum Erstellen benutzerdefinierter Optionssätze zur Verwendung innerhalb Ihrer App.

Optionssätze können auf zwei Arten erstellt werden, entweder in der Optionssatzliste innerhalb des Portals oder direkt in einer Entität beim Erstellen eines Felds. Weitere Informationen darüber, wie Sie eine Entität erstellen finden Sie unter [Erstellen einer Entität](data-platform-create-entity.md).

## <a name="creating-an-option-set-while-adding-a-field"></a>Erstellen eines Optionssatzes beim Hinzufügen eines Felds.

1. Auf [powerapps.com](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), erweitern Sie den Abschnitt **Daten** und klicken oder tippen Sie im linken Navigationsbereich **Entitäten**.

    ![Entitätsdetails](./media/data-platform-cds-create-entity/entitylist.png "Entitätsliste")

2. Klicken oder tippen Sie auf eine vorhandene Entität oder [Erstellen Sie eine neue Entität](data-platform-create-entity.md)

3. Fügen Sie Ihrer Entität ein neues Feld hinzu, indem Sie auf **Feld hinzufügen** klicken.

4. Geben Sie im neuen Feldbereich den **Anzeigename** für Ihr Feld ein. **Name** wird automatisch aufgefüllt und als eindeutiger Name für Ihr Feld verwendet. Der **Anzeigename** wird verwendet, wenn dieses Feld Ihren Benutzern angezeigt wird, der **Name** wird in Ausdrücken und Formeln verwendet, wenn Sie Ihre App erstellen in.

    > [!div class="mx-imgBorder"] 
    > ![Neues Feld](./media/data-platform-cds-create-entity/newfieldpanel.png "Neuer Feldbereich")

5. Klicken Sie auf das Dropdown **Datentyp** und wählen Sie **Optionssatz** oder **MultiSelect-Optionssatz**.

6. Klicken Sie auf das Dropdown **Optionssatz** und wählen Sie **Neuer Optionssatz** aus

    > [!NOTE]
    > Wenn ein vorhandener Optionssatz für Ihre Entität verwendet werden kann, können Sie ihn aus dieser Liste auswählen, ohne einen neuen zu erstellen.

    ![Optionssatzliste](./media/data-platform-cds-newoptionset/fieldpanel-1.png "Optionssatzliste")

7. Ein neuer Bereich wird geöffnet, um den Optionssatz zu erstellen, **Anzeigename** und **Name** stammen standardmäßig vom Namen des Felds, können jedoch nach Bedarf geändert werden. Klicken Sie auf **Neues Element hinzufügen**, um das Erstellen Ihrer Optionsliste zu starten. Wiederholen Sie diesen Schritt, bis alle Ihre Elemente erstellt wurden.

    > [!div class="mx-imgBorder"] 
    > ![Neuer Optionssatz](./media/data-platform-cds-newoptionset/field-optionsetpanel.png "Neuer Optionssatz")

8. Nachdem Sie Ihre Elemente eingegeben haben, klicken Sie auf **Speichern**, um den Optionssatz zu erstellen.

    > [!div class="mx-imgBorder"] 
    > ![Neuer Optionssatz](./media/data-platform-cds-newoptionset/field-optionsetpanel-values.png "Neuer Optionssatz")

9. Klicken Sie auf **Fertig**, um den Feldbereich zu schließen, und dann auf **Entität speichern**, um Ihre Entität in Common Data Service zu speichern.

    > [!NOTE]
    > Sie können eines Ihrer Elemente als den **Standard** für dieses Feld auswählen, und es wird standardmäßig ausgewählt, wenn Benutzer neue Datensätze in der Entität erstellen.

    > [!div class="mx-imgBorder"] 
    > ![Neues Feld](./media/data-platform-cds-newoptionset/fieldpanel-2.png "Neuer Feldbereich")

## <a name="creating-an-option-set-from-the-option-set-list"></a>Erstellen eines Optionssatzes aus der Optionssatzliste

1. Auf [powerapps.com](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), erweitern Sie den Abschnitt **Daten** und klicken oder tippen Sie im linken Navigationsbereich **Optionssätze**.

    > [!div class="mx-imgBorder"] 
    > ![Optionssätze](./media/data-platform-cds-newoptionset/optionsetlist.png "Optionssatzliste")

2. Klicken Sie auf **Neuer Optionssatz**

3. Ein neuer Bereich wird geöffnet, um den Optionssatz zu erstellen, geben Sie den **Anzeigename** und den **Name** ein. Klicken Sie auf **Neues Element hinzufügen**, um das Erstellen Ihrer Optionsliste zu starten. Wiederholen Sie diesen Schritt, bis alle Ihre Elemente erstellt wurden.

    > [!div class="mx-imgBorder"] 
    > ![Optionssatz erstellen](./media/data-platform-cds-newoptionset/optionset-create.png "Optionssatz erstellen")

4. Nachdem Sie Ihre Elemente eingegeben haben, klicken Sie auf **Speichern**, um den Optionssatz zu erstellen.

    > [!div class="mx-imgBorder"] 
    > ![Neuer Optionssatz](./media/data-platform-cds-newoptionset/optionset-create-values.png "Neuer Optionssatz")

5. Sie können nun diesen Optionssatz verwenden, indem Sie ein neues Feld in einer Entität erstellen.

## <a name="global-and-local-option-sets"></a>Globale und lokale Optionssätze

Standardmäßig werden Optionssätze als globale Optionssätze erstellt, sodass sie in mehreren Entitäten wiederverwendet werden können. Unter der Option **Weitere anzeigen** können Sie einen Optionssatz **lokal** machen, wenn Sie einen neuen Optionssatz erstellen. Diese Option ist nur verfügbar, wenn ein Optionssatz beim Hinzufügen eines Felds erstellt wird, und nicht über die Optionssatzliste. Lokale Optionssätze können nur von der Entität und das Feld verwendet werden, für die sie erstellt wurden. Sie können nicht für andere Entitäten wiederverwendet werden. Diese Methode wird nur für fortgeschrittene Benutzer empfohlen, die eine bestimmte Anforderung für einen lokalen Optionssatz erfüllen müssen.

> [!IMPORTANT]
> Sobald ein Optionssatz lokal oder global erstellt wurde, kann dies nicht mehr geändert werden.
