---
title: Anpassen eines Formulars in einer Canvas-App | Microsoft-Dokumentation
description: Geben Sie in PowerApps an, welche Daten in einem Canvas-App-Formular in welcher Reihenfolge und in welchen Steuerelementen angezeigt werden sollen.
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
ms.openlocfilehash: 67e7e0074259731bb1d3c50474e8020e3f4fcf1b
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/07/2019
ms.locfileid: "71993194"
---
# <a name="customize-a-canvas-app-form-in-powerapps"></a>Anpassen eines Canvas-App-Formulars in PowerApps

Passen Sie in einer Canvas-App ein **Anzeigeformular**-Steuerelement und ein **Bearbeitungsformular**-Steuerelement an, sodass die wichtigsten Daten in der intuitivsten Reihenfolge angezeigt werden, damit Benutzer die Daten leicht verstehen und aktualisieren können.

Jedes Formular umfasst eine oder mehrere Karten, die jeweils Daten aus einer bestimmten Spalte in der Datenquelle anzeigen. Wenn Sie die in diesem Artikel beschriebenen Schritte ausführen, können Sie angeben, welche Karten in einem Formular angezeigt werden, und Karten innerhalb eines Formulars nach oben oder unten verschieben.

Wenn Sie mit Canvas-PPS nicht vertraut sind, finden Sie weitere Informationen unter [Was sind Canvas-apps?](getting-started.md).

## <a name="prerequisites"></a>Voraussetzungen

[Generieren einer App](data-platform-create-app.md) aus Common Data Service und [Anpassen des Katalogs](customize-layout-sharepoint.md) in dieser App.

## <a name="show-and-hide-cards"></a>Karten ein- und ausblenden

1. Melden Sie sich bei [powerapps](http://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)an, und öffnen Sie die APP, die Sie generiert und angepasst haben.

1. Geben oder fügen Sie in der linken Navigationsleiste in der Suchleiste **D** ein, um die Liste der Elemente zu filtern, und wählen Sie dann **DetailForm1**aus.

    > [!div class="mx-imgBorder"]
    > ![select-Detailbildschirm @ no__t-1

1. Wählen Sie auf der Registerkarte **Eigenschaften** im rechten Bereich die Option **Felder bearbeiten** aus, um den Bereich **Felder** zu öffnen.

    > [!div class="mx-imgBorder"]
    > ![open Fields Pane @ no__t-1

1. Blenden Sie ein Feld, z. b. eine **Beschreibung**, aus, indem Sie darauf zeigen, und wählen Sie die Auslassungs Punkte (...) aus, die angezeigt werden, und dann **Entfernen**

    > [!div class="mx-imgBorder"]
    > ![list of Fields @ no__t-1

1. Wenn Sie ein Feld auswählen, wählen **Sie Feld hinzufügen**aus, geben Sie die ersten Buchstaben des Feld namens in das Suchfeld ein, aktivieren Sie das Kontrollkästchen des Felds, und wählen **Sie dann hinzufügen**aus.

    > [!div class="mx-imgBorder"]
    > ![list of Fields @ no__t-1

## <a name="reorder-the-cards"></a>Karten anordnen

1. Ziehen Sie im Bereich **Felder** das Feld **Kontoname** an den oberen Rand der Liste der Felder.

    Die Karten in **DetailForm1** spiegeln die Änderung wider.

    > [!div class="mx-imgBorder"]
    > ![reordercards @ no__t-1

1. optionale Ordnen Sie die anderen Karten in diese Sequenz an:

    - Kontoname
    - Anzahl der Mitarbeiter
    - Jahresumsatz
    - Haupttelefon
    - Adresse 1: Straße 1
    - Adresse 1: Straße 2
    - Adresse 1: Stadt
    - Adresse 1: Zip/Postleitzahl

1. Geben oder fügen Sie in der linken Navigationsleiste in der Suchleiste " **Ed** " ein, und wählen Sie dann **EditForm1** aus, um es auszuwählen.

1. Wiederholen Sie die Schritte dieser und der vorherigen Prozedur, damit die Felder in **EditForm1** denen in **DetailForm1** gleichen.

## <a name="run-the-app"></a>Ausführen der App

1. Geben oder fügen Sie in der linken Navigationsleiste **Br** in die Suchleiste ein, und wählen Sie dann **BrowseScreen1** aus, um es auszuwählen.

1. Öffnen Sie den Vorschaumodus durch Drücken von F5 (oder durch Auswählen des Symbols **Preview** in der Nähe der oberen rechten Ecke).

    > [!div class="mx-imgBorder"]
    > ![preview-Symbol @ no__t-1

1. Klicken Sie in der oberen rechten Ecke auf das Pluszeichen, um einen Datensatz in **EditScreen1**hinzuzufügen.

    > [!div class="mx-imgBorder"]
    > ![add Datensatz @ no__t-1

1. Fügen Sie beliebige Daten hinzu, und wählen Sie dann das Häkchensymbol in der oberen rechten Ecke aus, um die Änderungen zu speichern und zu **BrowseScreen1**zurückzukehren.

    > [!div class="mx-imgBorder"]
    > ![save-Datensatz @ no__t-1

1. Wählen Sie den Pfeil für das soeben erstellte Element aus, um Details zu diesem Element in **DetailScreen1**anzuzeigen.

    > [!div class="mx-imgBorder"]
    > ![right Pfeil @ no__t-1

1. Wählen Sie in der oberen rechten Ecke das Bearbeitungs Symbol aus, um den Datensatz in **EditScreen1**zu aktualisieren.

    > [!div class="mx-imgBorder"]
    > ![edit-Datensatz @ no__t-1

1. Ändern Sie die Informationen in einem oder mehreren Feldern, und aktivieren Sie dann das Häkchen in der oberen rechten Ecke, um die Änderungen zu speichern und zu **DetailScreen1**zurückzukehren.

    > [!div class="mx-imgBorder"]
    > ![save Changes @ no__t-1

1. Wählen Sie in der Nähe der oberen rechten Ecke das Papierkorb Symbol aus, um den soeben aktualisierten Datensatz zu löschen und zu **BrowseScreen1**zurückzukehren.

    > [!div class="mx-imgBorder"]
    > ![delete-Datensatz @ no__t-1

1. Schließen Sie den Vorschaumodus durch Drücken der ESC-Taste (oder durch Auswählen des Schließ Symbols in der Nähe der oberen linken Ecke).

## <a name="next-steps"></a>Nächste Schritte

- [Speichern und Veröffentlichen](save-publish-app.md) Ihrer App.
- [Customize a card (Anpassen einer Karte)](customize-card.md) in Ihrer App.