---
title: Anzeigen einer Liste von Elementen in einer Canvas-App | Microsoft-Dokumentation
description: Verwenden Sie einen Katalog, um eine Liste der Elemente in Ihrer Canvas-App anzuzeigen, und filtern Sie die Liste, indem Sie ein Kriterium angeben.
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 09/28/2017
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: f45948bc16f036669a09ed2c566c60440d24a797
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "61528029"
ms.PowerAppsDecimalTransform: true
---
# <a name="show-a-list-of-items-in-powerapps"></a>Anzeigen einer Liste mit Elementen in PowerApps

Sie können eine Liste von Elementen aus beliebigen Datenquellen anzeigen, indem Sie Ihrer Canvas-App ein **[Katalog](controls/control-gallery.md)**-Steuerelement hinzufügen. In diesem Thema wird Excel als Datenquelle verwendet. Filtern Sie die Liste, indem Sie das **Katalog**-Steuerelement so konfigurieren, dass nur die Elemente angezeigt werden, die dem Filterkriterium in einem **[Texteingabe](controls/control-text-input.md)**-Steuerelement entsprechen.

## <a name="prerequisites"></a>Voraussetzungen

- Erfahren Sie, wie Sie in PowerApps [ein Steuerelement hinzufügen und konfigurieren](add-configure-controls.md).

- Einrichten der Beispieldaten:
    1. Laden Sie [diese Excel-Datei](https://az787822.vo.msecnd.net/documentation/get-started-from-data/FlooringEstimates.xlsx) mit Beispieldaten für dieses Lernprogramm herunter.

    2. Laden Sie die Excel-Datei in ein [Cloudspeicherkonto](connections/cloud-storage-blob-connections.md) hoch, z.B. in OneDrive for Business.

- Öffnen Sie eine leere app:
    1. [Melden Sie sich bei PowerApps an](http://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).

    1. Wählen Sie unter **Eigene App erstellen** die Option **Canvas-App ohne Vorlage** aus.

    1. Geben Sie einen Namen für Ihre App an, wählen Sie **Telefon** aus, und klicken Sie dann auf **Erstellen**.

    1. Falls das Dialogfeld **Willkommen bei PowerApps Studio** angezeigt wird, klicken Sie auf **Überspringen**.

    1. [Fügen Sie eine Verbindung](add-data-connection.md) mit der **FlooringEstimates**-Tabelle in der Excel-Datei hinzu.

## <a name="add-a-gallery-to-a-blank-screen"></a>Hinzufügen eines Katalogs zu einem leeren Bildschirm

1. Auf der **einfügen** Registerkarte **Katalog**, und wählen Sie dann **vertikale**.

    ![Vertikalen Katalog hinzufügen](./media/add-gallery/gallery-dropdown.png)

1. Auf der **Eigenschaften** Registerkarte im rechten Bereich, und Öffnen der **Elemente** aus, und wählen Sie dann **Flooring Estimates**.

    ![Flooring estimates](./media/add-gallery/select-layout.png)

1. (optional) In der **Layout** wählen eine andere Option.

## <a name="add-a-gallery-in-a-screen"></a>Hinzufügen eines Katalogs in einem Bildschirm

1. Auf der **Startseite** Registerkarte **neuer Bildschirm** > **listenbildschirm**.

    Einen Bildschirm mit einer **Katalog** -Steuerelement und andere Steuerelemente, wie etwa eine Suchleiste angezeigt wird.

1. Legen Sie die **Items**-Eigenschaft des Katalogs auf `FlooringEstimates` fest.

    Im **Katalog**-Steuerelement werden die Beispieldaten angezeigt.

    ![Anzeigen von Daten](./media/add-gallery/show-data-default.png)

## <a name="add-a-control-to-the-gallery-control"></a>Hinzufügen eines Steuerelements zum Katalog-Steuerelement
Bevor Sie andere Anpassungen vornehmen, sicher, dass das Layout für Ihre **Katalog** Steuerelement am ehesten entspricht, was Sie möchten. Von dort aus können Sie weiter anpassen der **Katalog** Vorlage, die bestimmt, wie alle Daten in die **Katalog** -Steuerelement angezeigt wird.

1. Wählen Sie die Vorlage durch Klicken oder tippen am unteren Rand der **Katalog** Steuerelement auswählen und dann auf das Stiftsymbol in der oberen linken Ecke.

    ![Bearbeiten der Katalogvorlage](./media/add-gallery/edit-item.png)

2. Fügen Sie bei ausgewählter Vorlage ein **[Label](controls/control-text-box.md)**-Steuerelement (Bezeichnung) hinzu, verschieben Sie es, und ändern Sie seine Größe, sodass es sich nicht mit anderen Steuerelementen in der Vorlage überschneidet.

    ![Bezeichnung hinzufügen](./media/add-gallery/add-text-box.png)

3. Wählen Sie den Katalog, und wählen Sie dann **bearbeiten** neben **Felder** auf die **Eigenschaften** Registerkarte im rechten Bereich.

4. Wählen Sie die soeben in diesem Verfahren hinzugefügte Bezeichnung aus, und öffnen Sie die hervorgehobene Liste im Bereich **Daten**.

    ![Dropdownliste öffnen](./media/add-gallery/open-dropdown.png)

5. Klicken oder tippen Sie in dieser Liste auf **Price** (Preis).

    Im **Katalog**-Steuerelement werden die neuen Werte angezeigt.

    ![Endgültiger Katalog](./media/add-gallery/final-gallery.png)

## <a name="filter-and-sort-a-gallery"></a>Filtern und Sortieren von einem Katalog
Die **[Items](controls/properties-core.md)**-Eigenschaft eines **Katalog**-Steuerelements bestimmt, welche Elemente angezeigt werden. In diesem Verfahren konfigurieren Sie diese Eigenschaft, sodass es bestimmt auch, welche Datensätze basierend auf Filterkriterien, und in welcher Reihenfolge angezeigt werden.

![Symbol "Suche Box" und "Sortieren"](./media/add-gallery/text-search-box.png)

1. Legen Sie die **[Items](controls/properties-core.md)**-Eigenschaft des **Katalog**-Steuerelements auf diese Formel fest:

    ```powerapps-comma
    Sort
        (If
            (IsBlank(TextSearchBox1.Text);
            FlooringEstimates;
            Filter(
                FlooringEstimates;
                TextSearchBox1.Text in Text(Name)
            )
        );
        Name;
        If(
            SortDescending1;
            SortOrder.Descending;
            SortOrder.Ascending
        )
    )
    ```

    Weitere Informationen zu den Funktionen in dieser Formel finden Sie unter [formula reference (Formelreferenz)](formula-reference.md).

1. Doppelklicken Sie auf das Suchfeld ein, und klicken Sie dann geben Sie einen Produktnamen ganz oder teilweise.

    Nur die Elemente, die das Filterkriterium erfüllen angezeigt werden.

1. Während Sie die Alt-Taste drücken, das Sortiersymbol einmal oder mehrmals auf um die Sortierreihenfolge zu wechseln.

    Die Datensätze Umschalten zwischen aufsteigender und absteigender alphabetischer Reihenfolge basierend auf den Namen des Produkts.

## <a name="highlight-the-selected-item"></a>Hervorheben des ausgewählten Elements
Legen Sie die **Katalog** des Steuerelements **TemplateFill** Eigenschaft, um eine Formel, die wie in diesem Beispiel, aber Sie können verschiedene Farben geben, wenn Sie möchten:

**If(ThisItem.IsSelected; LightCyan; White)**

## <a name="change-the-default-selection"></a>Ändern der Standardauswahl
Legen Sie die **Default**-Eigenschaft des **Katalog**-Steuerelements auf den Datensatz fest, der standardmäßig ausgewählt sein soll. Sie können beispielsweise angeben, das fünfte Element in der **FlooringEstimates** Datenquelle:

**Last(FirstN(FlooringEstimates; 5))**

In diesem Beispiel geben Sie das erste Element in der Kategorie **Hardwood** der Datenquelle **FlooringEstimates** an:

**First(Filter(FlooringEstimates; Category = "Hardwood"))**

## <a name="next-steps"></a>Nächste Schritte
Informationen zum Arbeiten mit [Formularen](working-with-forms.md) und [Formeln](working-with-formulas.md).
