---
title: Erstellen und Aktualisieren einer Sammlung in eine Canvas-app | Microsoft-Dokumentation
description: Erstellen einer Sammlung in eine Canvas-app, um die Auflistung Elemente hinzuzufügen und eine oder alle Elemente daraus entfernen.
author: aftowen
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 01/28/2019
ms.author: anneta
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: aca1b78262ac359689d66f687f902103740fa3a6
ms.sourcegitcommit: 826bde1eab3dd32d7bf9fa3f43ea069694845597
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/30/2019
ms.locfileid: "57800305"
---
# <a name="create-and-update-a-collection-in-a-canvas-app"></a>Erstellen und Aktualisieren einer Sammlung in eine Canvas-app

Verwenden Sie eine Sammlung zum Speichern von Daten, die Benutzer zu verwalten, können in Ihrer app. Eine Sammlung ist eine Gruppe von ähnlichen Elementen, z. B. Produkte in einer Produktliste. Weitere Informationen zu verschiedenen Typen von Variablen, z. B. Sammlungen: [Grundlegendes zu Canvas-Apps-Variablen](working-with-variables.md).

## <a name="prerequisites"></a>Voraussetzungen

- [Registrieren Sie sich](../signup-for-powerapps.md) für PowerApps, und [melden Sie sich an](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), indem Sie dieselben Anmeldeinformationen bereitstellen, die Sie bei der Registrierung angegeben haben.
- Erstellen Sie eine App, oder öffnen Sie eine vorhandene App in PowerApps.
- Erfahren Sie, wie Sie [ein Steuerelement](add-configure-controls.md) in PowerApps konfigurieren.

## <a name="create-a-multicolumn-collection"></a>Erstellen Sie eine Sammlung für mehrere Spalten

1. Fügen Sie in PowerApps Studio, eine **Texteingabe** Steuerelement.

    ![Fügen Sie ein Texteingabe-Steuerelement](./media/create-update-collection/add-textbox.png)

1. Benennen Sie das Steuerelement, indem Sie auf die Auslassungspunkte im linken Navigationsbereich, auswählen von **umbenennen**, und geben dann **ProductName**.

    ![Umbenennen eines Steuerelements](./media/create-update-collection/rename-textbox.png)

1. Hinzufügen einer **Dropdown** Steuerelement.

    ![Dropdown-Liste hinzufügen](./media/create-update-collection/add-dropdown.png)

1. Benennen Sie die **Dropdown** Steuerelement **Farben**, und stellen Sie sicher, dass die **Elemente** -Eigenschaft in der Liste ausgewählt ist.

    ![Items-Eigenschaft](./media/create-update-collection/items-property.png)

1. Ersetzen Sie in der Bearbeitungsleiste **DropDownSample** mit dem folgenden Ausdruck:

    `["Red","Green","Blue"]`

1. Hinzufügen einer **Schaltfläche** steuern, legen Sie seine **Text** Eigenschaft **"Hinzufügen"**, und legen Sie seine **OnSelect** -Eigenschaft auf diese Formel:

    ```powerapps-dot
    Collect(
        ProductList,
        {
            Product: ProductName.Text,
            Color: Colors.Selected.Value
        }
    )
    ```

1. Drücken Sie F5, geben Sie Text in **ProductName**, wählen Sie eine Option in **Farben**, und wählen Sie dann **hinzufügen**.

    ![Vorschau der app](./media/create-update-collection/preview-add.png)

1. Wiederholen Sie den vorherigen Schritt mindestens zwei weitere Male aus, und drücken Sie Esc.

1. Auf der **Datei** , wählen Sie im Menü **Sammlungen** der Sammlung angezeigt, die Sie erstellt.

    ![Auflistung anzeigen](./media/create-update-collection/show-collection.png)

## <a name="show-a-collection"></a>Anzeigen einer Auflistung

1. Hinzufügen eine vertikalen **Katalog** Steuerelement.

    ![Hinzufügen eines vertikalen Katalogs](./media/create-update-collection/add-gallery.png)

1. Festlegen des Katalogs **Elemente** Eigenschaft **ProductList**.

1. In der **Daten** Bereich legen Sie das Feld Untertitel **Farbe**, und legen Sie auf das Feld "Titel" **Produkt**.

    ![Festlegen Sie der Items-Eigenschaft des Katalogs, und ändern Sie die Felder, die es zeigt](./media/create-update-collection/configure-gallery.png)

1. Schließen der **Daten** Bereich, und legen Sie die **Layout** Feld **Titel und Untertitel**.

    ![Festlegen Sie der Items-Eigenschaft des Katalogs, und ändern Sie die Felder, die es zeigt](./media/create-update-collection/change-layout.png)

    Ihr Bildschirm sieht etwa wie in diesem Beispiel aus:

    ![Vom ersten Bildschirm wird](./media/create-update-collection/screen-example1.png)

## <a name="remove-one-or-all-items"></a>Entfernen Sie eine oder alle Elemente

1. Wählen Sie die Katalogvorlage durch Klicken oder tippen im unteren Bereich des Katalogs, und klicken oder tippen bearbeiten-Symbol in der Nähe der oberen linken Ecke.

    ![Wählen Sie Katalog: Vorlage](./media/create-update-collection/select-template.png)

1. Hinzufügen einer **Papierkorb** Symbol, um die Katalogvorlage.

    ![Papierkorbsymbol "hinzufügen"](./media/create-update-collection/trash-icon.png)

1. Legen Sie des Symbol " **OnSelect** -Eigenschaft auf diese Formel:

    `Remove(ProductList, ThisItem)`

1. Fügen Sie außerhalb des Katalogs, eine Schaltfläche hinzu, legen Sie seine **Text** Eigenschaft, um **"Clear"**, und legen Sie seine **OnSelect** -Eigenschaft auf diese Formel:

    `Clear(ProductList)`

1. Während Sie die Alt-Taste gedrückt halten, wählen Sie die **Papierkorb** Symbol für ein Element, das Element aus der Sammlung entfernen, oder wählen Sie die **löschen** Schaltfläche, um alle Elemente aus der Auflistung entfernt.

## <a name="put-a-sharepoint-list-into-a-collection"></a>Einfügen einer SharePoint-Liste in eine Sammlung

1. [Herstellen einer Verbindung mit einer SharePoint-Liste](connect-to-sharepoint.md)

1. Fügen Sie eine Schaltfläche hinzu, und legen Sie die folgende Funktion für die **[OnSelect](controls/properties-core.md)**-Eigenschaft fest, ersetzen Sie hierbei *ListName* durch den Namen der SharePoint-Liste:<br>

    `Collect(MySPCollection, ListName)`

    Diese Funktion erstellt eine Sammlung namens **MySPCollection**, die die gleichen Daten wie Ihre SharePoint-Liste enthält.

1. Halten Sie die ALT-TASTE gedrückt, und wählen Sie die Schaltfläche aus.

1. (optional) Um die Auflistung der Vorschau anzeigen, die Sie erstellt haben, wählen Sie **Sammlungen** auf die **Datei** Menü.

Informationen dazu, wie Sie Daten aus einer SharePoint-Liste (z. B. Datumsangaben, Optionen und Personen) in einem Katalog anzeigen: [Anzeigen von Daten in einem Katalog](connections/connection-sharepoint-online.md#show-data-in-a-gallery). Informationen zum Anzeigen der Daten in einem Formular (mit Dropdownliste, Datumsauswahl und Personenauswahl): [Bearbeiten von Form und Display Form-Steuerelemente](controls/control-form-detail.md).

## <a name="next-steps"></a>Nächste Schritte

- Überprüfen Sie die [Referenzthema](functions/function-clear-collect-clearcollect.md) für die **sammeln** Funktion.
- Informationen zum Strukturieren von Daten in einer Auflistung mithilfe der [AddColumns "," DropColumns "," RenameColumns "und" ShowColumns](functions/function-table-shaping.md) Funktionen.
