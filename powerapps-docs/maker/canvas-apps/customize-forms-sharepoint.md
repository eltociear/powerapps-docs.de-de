---
title: Anpassen eines Formulars in einer Canvas-App | Microsoft-Dokumentation
description: Geben Sie in PowerApps an, welche Daten in einem Canvas-App-Formular in welcher Reihenfolge und in welchen Steuerelementen angezeigt werden sollen.
author: AFTOwen
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 03/17/2018
ms.author: anneta
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 1a6465a00f135489d594bad75b8a25942e05dd25
ms.sourcegitcommit: f4b71ea0996603b3358377a0da21b9e4428a287c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/02/2019
ms.locfileid: "58870929"
---
# <a name="customize-a-canvas-app-form-in-powerapps"></a>Anpassen eines Canvas-App-Formulars in PowerApps

Passen Sie in einer Canvas-App ein **Anzeigeformular**-Steuerelement und ein **Bearbeitungsformular**-Steuerelement an, sodass die wichtigsten Daten in der intuitivsten Reihenfolge angezeigt werden, damit Benutzer die Daten leicht verstehen und aktualisieren können.

Jedes Formular umfasst eine oder mehrere Karten, die jeweils Daten aus einer bestimmten Spalte in der Datenquelle anzeigen. Wenn Sie die in diesem Artikel beschriebenen Schritte ausführen, können Sie angeben, welche Karten in einem Formular angezeigt werden, und Karten innerhalb eines Formulars nach oben oder unten verschieben.

Wenn Sie mit der Canvas-Pps nicht vertraut sind, finden Sie unter [Was sind Canvas-apps?](getting-started.md).

## <a name="prerequisites"></a>Voraussetzungen

[Generieren einer App](data-platform-create-app.md) aus Common Data Service und [Anpassen des Katalogs](customize-layout-sharepoint.md) in dieser App.

## <a name="show-and-hide-cards"></a>Karten ein- und ausblenden

1. Melden Sie sich beim [PowerApps](http://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), und öffnen Sie dann die app, die Sie generiert und angepasst.

1. Geben Sie in der linken Navigationsleiste, oder fügen Sie **D** in die Suchleiste ein, um die Liste der Elemente zu filtern, und wählen Sie dann **DetailForm1**.

    > [!div class="mx-imgBorder"]
    > ![Detailbildschirm auswählen](./media/customize-forms-sharepoint/select-detailform.png)

1. Wählen Sie auf der Registerkarte **Eigenschaften** im rechten Bereich die Option **Felder bearbeiten** aus, um den Bereich **Felder** zu öffnen.

    > [!div class="mx-imgBorder"]
    > ![Bereich "Open Felder"](./media/customize-forms-sharepoint/edit-fields.png)

1. Blenden Sie ein Feld, z. B. **Beschreibung**, indem Sie mit dem Mauszeiger auf ihn, Sie auf die Auslassungspunkte (...), der angezeigt wird, und wählen dann **entfernen**.

    > [!div class="mx-imgBorder"]
    > ![Liste der Felder](./media/customize-forms-sharepoint/hide-fields.png)

1. Zeigen Sie dazu ein Feld **Feld hinzufügen**, eingeben oder Einfügen von in das Suchfeld, Kontrollkästchens des Felds, und wählen Sie dann die ersten paar Buchstaben, der den Namen des Felds **hinzufügen**.

    > [!div class="mx-imgBorder"]
    > ![Liste der Felder](./media/customize-forms-sharepoint/show-field.png)

## <a name="reorder-the-cards"></a>Karten anordnen

1. In der **Felder** ziehen Sie die **Kontoname** Feld an den Anfang der Liste der Felder.

    Die Karten in **DetailForm1** entsprechend die Änderung.

    > [!div class="mx-imgBorder"]
    > ![Karten neu angeordnet](./media/customize-forms-sharepoint/reordered-card.png)

1. (optional) Ordnen Sie die anderen Karten in der folgenden Reihenfolge neu an:

    - Kontoname
    - Anzahl der Mitarbeiter
    - Jahresumsatz
    - Telefon
    - Adresse 1: Straße 1
    - Adresse 1: Straße 2
    - Adresse 1: Stadt
    - Adresse 1: Postleitzahl

1. Geben Sie in der linken Navigationsleiste, oder fügen Sie **Ed** in die Suche, und klicken Sie anschließend **EditForm1** um es auszuwählen.

1. Wiederholen Sie die Schritte dieser und der vorherigen Prozedur, damit die Felder in **EditForm1** denen in **DetailForm1** gleichen.

## <a name="run-the-app"></a>Ausführen der App

1. Geben Sie in der linken Navigationsleiste, oder fügen Sie **Br** in die Suche, und klicken Sie anschließend **BrowseScreen1** um es auszuwählen.

1. Öffnen Sie den Vorschaumodus durch Drücken von F5 (oder durch Auswählen des Symbols **Preview** in der Nähe der oberen rechten Ecke).

    > [!div class="mx-imgBorder"]
    > ![„Preview“-Symbol](./media/customize-forms-sharepoint/open-preview.png)

1. Wählen Sie in der oberen rechten Ecke das Plussymbol zum Hinzufügen eines Eintrags in **EditScreen1**.

    > [!div class="mx-imgBorder"]
    > ![Hinzufügen eines Datensatzes](./media/customize-forms-sharepoint/add-record.png)

1. Fügen Sie beliebige Daten werden soll, und wählen Sie dann das Häkchen in der oberen rechten Ecke die Änderungen zu speichern und zum zurückkehren **BrowseScreen1**.

    > [!div class="mx-imgBorder"]
    > ![Datensatz speichern](./media/customize-forms-sharepoint/save-record.png)

1. Wählen Sie den Pfeil aus, für das Element, das Sie gerade erstellt haben, um angezeigt zu diesem Element in details **DetailScreen1**.

    > [!div class="mx-imgBorder"]
    > ![Pfeil nach rechts](./media/customize-forms-sharepoint/right-arrow.png)

1. Wählen Sie in der oberen rechten Ecke das Symbol "Bearbeiten" zum Aktualisieren des Datensatzes in **EditScreen1**.

    > [!div class="mx-imgBorder"]
    > ![Datensatz bearbeiten](./media/customize-forms-sharepoint/edit-record.png)

1. Ändern Sie die Informationen in einem oder mehreren Feldern, und wählen Sie dann das Häkchen in der oberen rechten Ecke die Änderungen zu speichern und zum zurückkehren **DetailScreen1**.

    > [!div class="mx-imgBorder"]
    > ![Änderungen speichern](./media/customize-forms-sharepoint/save-record.png)

1. Wählen Sie in der Nähe der oberen rechten Ecke das Papierkorb-Symbol, die den Datensatz zu löschen, die Sie gerade aktualisiert und um zurückzugeben **BrowseScreen1**.

    > [!div class="mx-imgBorder"]
    > ![Datensatz löschen](./media/customize-forms-sharepoint/delete-record.png)

1. Schließen Sie den Vorschaumodus durch Drücken von Esc (oder durch Auswahl des schließsymbols in der Nähe der oberen linken Ecke).

## <a name="next-steps"></a>Nächste Schritte

- [Speichern und Veröffentlichen](save-publish-app.md) Ihrer App.
- [Customize a card (Anpassen einer Karte)](customize-card.md) in Ihrer App.