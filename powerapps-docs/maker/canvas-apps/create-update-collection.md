---
title: Erstellen und Aktualisieren einer Sammlung in einer Canvas-App | Microsoft-Dokumentation
description: Erstellen Sie eine Sammlung in einer Canvas-APP, fügen Sie der Auflistung Elemente hinzu, und entfernen Sie ein oder alle Elemente daraus.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 01/28/2019
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: b124a27119a7b91572bdfef563e0f99e9d5da08d
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2019
ms.locfileid: "74731778"
---
# <a name="create-and-update-a-collection-in-a-canvas-app"></a>Erstellen und Aktualisieren einer Sammlung in einer Canvas-App

Verwenden Sie eine Sammlung zum Speichern von Daten, die Benutzer in ihrer App verwalten können. Eine Sammlung ist eine Gruppe von ähnlichen Elementen, z. b. Produkte in einer Produktliste. Weitere Informationen zu verschiedenen Variablen Typen, z. b. Sammlungen, finden Sie Untergrund Legendes zu [Canvas-App-Variablen](working-with-variables.md).

## <a name="prerequisites"></a>Voraussetzungen

- [Registrieren](../signup-for-powerapps.md) Sie sich für powerapps, und [melden](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) Sie sich dann mit den Anmelde Informationen an, die Sie bei der Registrierung verwendet haben.
- Erstellen Sie eine APP, oder öffnen Sie eine vorhandene app in powerapps.
- Erfahren Sie, wie Sie [ein Steuer](add-configure-controls.md) Element in powerapps konfigurieren.

## <a name="create-a-multicolumn-collection"></a>Erstellen einer Sammlung mit mehreren Spalten

1. Fügen Sie in powerapps Studio ein **Text Eingabe** -Steuerelement hinzu.

    ![Einfügen eines Text Eingabe-Steuer Elements](./media/create-update-collection/add-textbox.png)

1. Benennen Sie das Steuerelement um, indem Sie im linken Navigationsbereich die Auslassungs Punkte auswählen, **Umbenennen**auswählen und dann **ProductName**eingeben.

    ![Umbenennen eines Steuer Elements](./media/create-update-collection/rename-textbox.png)

1. Fügen Sie ein **Dropdown** -Steuerelement hinzu.

    ![Dropdown Liste hinzufügen](./media/create-update-collection/add-dropdown.png)

1. Benennen Sie die **Farben**des **Dropdown** -Steuer Elements um, und stellen Sie sicher, dass die **Items** -Eigenschaft in der Eigenschaften Liste ausgewählt ist.

    ![Items-Eigenschaft](./media/create-update-collection/items-property.png)

1. Ersetzen Sie in der Bearbeitungs Leiste **dropdownsample** durch diesen Ausdruck:

    `["Red","Green","Blue"]`

1. Fügen Sie ein **Schalt** Flächen-Steuerelement hinzu, legen Sie dessen **Text** -Eigenschaft auf **"Add"** fest, und legen **Sie die onselect** -Eigenschaft auf diese Formel

    ```powerapps-dot
    Collect(
        ProductList,
        {
            Product: ProductName.Text,
            Color: Colors.Selected.Value
        }
    )
    ```

1. Drücken Sie F5, geben Sie Text in **ProductName**ein, wählen Sie eine Option in **Farben**aus, und klicken Sie dann auf **Hinzufügen**.

    ![Vorschau der APP](./media/create-update-collection/preview-add.png)

1. Wiederholen Sie den vorherigen Schritt mindestens zwei weitere Male, und drücken Sie dann ESC.

1. Wählen Sie im Menü **Datei** die Option **Sammlungen** aus, um die von Ihnen erstellte Sammlung anzuzeigen.

    ![Sammlung anzeigen](./media/create-update-collection/show-collection.png)

## <a name="show-a-collection"></a>Sammlung anzeigen

1. Hinzufügen eines **vertikalen Katalog** -Steuer Elements.

    ![Hinzufügen eines vertikalen Katalogs](./media/create-update-collection/add-gallery.png)

1. Legen Sie die **Items** -Eigenschaft des Katalogs auf **productList**fest.

1. Legen Sie im **Daten** Bereich das Feld Untertitel auf **Color**fest, und legen Sie das Feld Title auf **Product**fest.

    ![Legen Sie die Items-Eigenschaft des Katalogs fest, und ändern Sie die angezeigten Felder.](./media/create-update-collection/configure-gallery.png)

1. Schließen Sie den Bereich **Daten** , wählen Sie den Katalog aus, und legen Sie dann das **layoutfeld** auf **Titel und Untertitel**fest.

    ![Legen Sie die Items-Eigenschaft des Katalogs fest, und ändern Sie die angezeigten Felder.](./media/create-update-collection/change-layout.png)

    Ihr Bildschirm ähnelt dem folgenden Beispiel:

    ![Beispiel des ersten Bildschirms](./media/create-update-collection/screen-example1.png)

## <a name="remove-one-or-all-items"></a>Entfernen eines oder aller Elemente

1. Wählen Sie die Katalog Vorlage aus, indem Sie am unteren Rand des Katalogs klicken oder tippen und dann auf das Stift Symbol in der Nähe der oberen linken Ecke klicken oder tippen.

    ![Katalog Vorlage auswählen](./media/create-update-collection/select-template.png)

1. Fügen Sie der Katalog Vorlage ein **Papierkorb** Symbol hinzu.

    ![Papierkorb Symbol hinzufügen](./media/create-update-collection/trash-icon.png)

1. Legen **Sie die onselect** -Eigenschaft des Symbols auf die folgende Formel fest:

    `Remove(ProductList, ThisItem)`

1. Fügen Sie außerhalb des Katalogs eine Schaltfläche hinzu, legen Sie die **Text** -Eigenschaft auf **"Clear"** fest, und legen **Sie die onselect** -Eigenschaft auf diese Formel fest:

    `Clear(ProductList)`

1. Wenn Sie die Alt-Taste gedrückt halten, wählen Sie das **Papierkorb** Symbol für ein Element aus, um das Element aus der Auflistung zu entfernen, oder klicken Sie auf die Schaltfläche **Löschen** , um alle Elemente aus der Sammlung zu entfernen

## <a name="put-a-sharepoint-list-into-a-collection"></a>Einfügen einer SharePoint-Liste in eine Sammlung

1. [Herstellen einer Verbindung mit einer SharePoint-Liste](connections/connection-sharepoint-online.md#create-a-connection)

1. Fügen Sie eine Schaltfläche hinzu, und legen Sie die folgende Funktion für die **[OnSelect](controls/properties-core.md)** -Eigenschaft fest, ersetzen Sie hierbei *ListName* durch den Namen der SharePoint-Liste:<br>

    `Collect(MySPCollection, ListName)`

    Diese Funktion erstellt eine Sammlung namens **MySPCollection**, die die gleichen Daten wie Ihre SharePoint-Liste enthält.

1. Halten Sie die ALT-TASTE gedrückt, und wählen Sie die Schaltfläche aus.

1. optionale Um eine Vorschau der erstellten Sammlung anzuzeigen, wählen Sie im Menü **Datei** die Option **Sammlungen** aus.

Informationen zum Anzeigen von Daten aus einer SharePoint-Liste (z. b. Datumsangaben, Auswahlmöglichkeiten und Personen) in einem Katalog: [Anzeigen von Listen Spalten in einem](connections/connection-sharepoint-online.md#show-list-columns-in-a-gallery)Katalog. Weitere Informationen zum Anzeigen von Daten in einem Formular (mit Dropdown Listen, Datums-und Personen adressierern): [Formular Steuerelemente bearbeiten und Formular anzeigen](controls/control-form-detail.md).

## <a name="next-steps"></a>Nächste Schritte

- Lesen Sie das [Referenz Thema](functions/function-clear-collect-clearcollect.md) für die **Collect** -Funktion.
- Erfahren Sie, wie Sie Daten in einer Auflistung mithilfe der Funktionen " [AddColumns", "dropcolumns", "renamecolumns" und "showcolumns](functions/function-table-shaping.md) " strukturieren.
