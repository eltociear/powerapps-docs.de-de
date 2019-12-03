---
title: Anpassen eines Formulars in einer Canvas-App | Microsoft-Dokumentation
description: In powerapps geben Sie an, welche Daten in einem Canvas-App-Formular angezeigt werden sollen, in welcher Reihenfolge Sie angezeigt werden und in welchen Steuerelementen Sie angezeigt werden.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 03/17/2018
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: f522f520c0f0f042e73932630980dee93bc5c89c
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2019
ms.locfileid: "74731762"
---
# <a name="customize-a-canvas-app-form-in-power-apps"></a>Anpassen eines Canvas-App-Formulars in powerapps

Passen Sie in einer Canvas-App ein **Anzeigeformular**-Steuerelement und ein **Bearbeitungsformular**-Steuerelement an, sodass die wichtigsten Daten in der intuitivsten Reihenfolge angezeigt werden, damit Benutzer die Daten leicht verstehen und aktualisieren können.

Jedes Formular umfasst eine oder mehrere Karten, die jeweils Daten aus einer bestimmten Spalte in der Datenquelle anzeigen. Wenn Sie die in diesem Artikel beschriebenen Schritte ausführen, können Sie angeben, welche Karten in einem Formular angezeigt werden, und Karten innerhalb eines Formulars nach oben oder unten verschieben.

Wenn Sie mit Canvas-PPS nicht vertraut sind, finden Sie weitere Informationen unter [Was sind Canvas-apps?](getting-started.md).

## <a name="prerequisites"></a>Voraussetzungen

[Generieren einer App](data-platform-create-app.md) aus Common Data Service und [Anpassen des Katalogs](customize-layout-sharepoint.md) in dieser App.

## <a name="show-and-hide-cards"></a>Karten ein- und ausblenden

1. Melden Sie sich bei [powerapps](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)an, und öffnen Sie die APP, die Sie generiert und angepasst haben.

1. Geben oder fügen Sie in der linken Navigationsleiste in der Suchleiste **D** ein, um die Liste der Elemente zu filtern, und wählen Sie dann **DetailForm1**aus.

    > [!div class="mx-imgBorder"]
    > ![Detailbildschirm auswählen](./media/customize-forms-sharepoint/select-detailform.png)

1. Wählen Sie auf der Registerkarte **Eigenschaften** im rechten Bereich die Option **Felder bearbeiten** aus, um den Bereich **Felder** zu öffnen.

    > [!div class="mx-imgBorder"]
    > ![Bereich Felder öffnen](./media/customize-forms-sharepoint/edit-fields.png)

1. Blenden Sie ein Feld, z. b. eine **Beschreibung**, aus, indem Sie darauf zeigen, und wählen Sie die Auslassungs Punkte (...) aus, die angezeigt werden, und dann **Entfernen**

    > [!div class="mx-imgBorder"]
    > ![Liste der Felder](./media/customize-forms-sharepoint/hide-fields.png)

1. Wenn Sie ein Feld auswählen, wählen **Sie Feld hinzufügen**aus, geben Sie die ersten Buchstaben des Feld namens in das Suchfeld ein, aktivieren Sie das Kontrollkästchen des Felds, und wählen **Sie dann hinzufügen**aus.

    > [!div class="mx-imgBorder"]
    > ![Liste der Felder](./media/customize-forms-sharepoint/show-field.png)

## <a name="reorder-the-cards"></a>Karten anordnen

1. Ziehen Sie im Bereich **Felder** das Feld **Kontoname** an den oberen Rand der Liste der Felder.

    Die Karten in **DetailForm1** spiegeln die Änderung wider.

    > [!div class="mx-imgBorder"]
    > ![neu geordnete Karten](./media/customize-forms-sharepoint/reordered-card.png)

1. optionale Ordnen Sie die anderen Karten in diese Sequenz an:

    - Kontoname
    - Anzahl der Mitarbeiter
    - Jahresumsatz
    - Haupttelefon
    - Adresse 1: Straße 1
    - Adresse 1: Straße 2
    - Adresse 1: Stadt
    - Adresse 1: PLZ

1. Geben oder fügen Sie in der linken Navigationsleiste in der Suchleiste " **Ed** " ein, und wählen Sie dann **EditForm1** aus, um es auszuwählen.

1. Wiederholen Sie die Schritte dieser und der vorherigen Prozedur, damit die Felder in **EditForm1** denen in **DetailForm1** gleichen.

## <a name="run-the-app"></a>Ausführen der App

1. Geben oder fügen Sie in der linken Navigationsleiste **Br** in die Suchleiste ein, und wählen Sie dann **BrowseScreen1** aus, um es auszuwählen.

1. Öffnen Sie den Vorschaumodus durch Drücken von F5 (oder durch Auswählen des Symbols **Preview** in der Nähe der oberen rechten Ecke).

    > [!div class="mx-imgBorder"]
    > ![Vorschau Symbol](./media/customize-forms-sharepoint/open-preview.png)

1. Klicken Sie in der oberen rechten Ecke auf das Pluszeichen, um einen Datensatz in **EditScreen1**hinzuzufügen.

    > [!div class="mx-imgBorder"]
    > ![Datensatz hinzufügen](./media/customize-forms-sharepoint/add-record.png)

1. Fügen Sie beliebige Daten hinzu, und wählen Sie dann das Häkchensymbol in der oberen rechten Ecke aus, um die Änderungen zu speichern und zu **BrowseScreen1**zurückzukehren.

    > [!div class="mx-imgBorder"]
    > ![Daten Satz speichern](./media/customize-forms-sharepoint/save-record.png)

1. Wählen Sie den Pfeil für das soeben erstellte Element aus, um Details zu diesem Element in **DetailScreen1**anzuzeigen.

    > [!div class="mx-imgBorder"]
    > ![Pfeil nach rechts](./media/customize-forms-sharepoint/right-arrow.png)

1. Wählen Sie in der oberen rechten Ecke das Bearbeitungs Symbol aus, um den Datensatz in **EditScreen1**zu aktualisieren.

    > [!div class="mx-imgBorder"]
    > ![bearbeiten](./media/customize-forms-sharepoint/edit-record.png)

1. Ändern Sie die Informationen in einem oder mehreren Feldern, und aktivieren Sie dann das Häkchen in der oberen rechten Ecke, um die Änderungen zu speichern und zu **DetailScreen1**zurückzukehren.

    > [!div class="mx-imgBorder"]
    > ![Änderungen speichern](./media/customize-forms-sharepoint/save-record.png)

1. Wählen Sie in der Nähe der oberen rechten Ecke das Papierkorb Symbol aus, um den soeben aktualisierten Datensatz zu löschen und zu **BrowseScreen1**zurückzukehren.

    > [!div class="mx-imgBorder"]
    > ![DELETE-Datensatz](./media/customize-forms-sharepoint/delete-record.png)

1. Schließen Sie den Vorschaumodus durch Drücken der ESC-Taste (oder durch Auswählen des Schließ Symbols in der Nähe der oberen linken Ecke).

## <a name="next-steps"></a>Nächste Schritte

- [Speichern und Veröffentlichen](save-publish-app.md) Ihrer App.
- [Customize a card (Anpassen einer Karte)](customize-card.md) in Ihrer App.