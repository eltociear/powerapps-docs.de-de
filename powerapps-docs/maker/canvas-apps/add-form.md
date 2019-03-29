---
title: Anzeigen, bearbeiten oder Hinzufügen eines Eintrags in einer Canvas-app | Microsoft-Dokumentation
description: Mithilfe eines Canvas-App-Formulars können Sie einen Datensatz aus einer Tabelle in der Datenquelle anzeigen, bearbeiten oder hinzufügen.
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 10/06/2017
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: e94aa48ed3fba1b4591e196e3b81d3fb0f76666f
ms.sourcegitcommit: 5c098a62f66a2f33418967fdce9363bd529e0fc1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/28/2019
ms.locfileid: "58581022"
---
# <a name="show-edit-or-add-a-record-in-a-canvas-app"></a>Anzeigen, bearbeiten oder Hinzufügen eines Eintrags in einer Canvas-app

In einer Canvas-app hinzufügen und Konfigurieren einer **[Anzeige](controls/control-form-detail.md)** Formularsteuerelement, um alle Felder in einem Datensatz, anzuzeigen, können Sie auch hinzufügen und Konfigurieren einer **[bearbeiten](controls/control-form-detail.md)** Formularsteuerelement, das ein Feld in einem Datensatz bearbeiten, Hinzufügen eines Datensatzes und speichern Sie die Änderungen an einer Datenquelle.

## <a name="prerequisites"></a>Voraussetzungen

- Erfahren Sie, wie Sie in PowerApps [ein Steuerelement hinzufügen und konfigurieren](add-configure-controls.md).
- Laden Sie [diese Excel-Datei](https://az787822.vo.msecnd.net/documentation/get-started-from-data/FlooringEstimates.xlsx) mit Beispieldaten für dieses Lernprogramm herunter.
- Laden Sie die Excel-Datei in ein [Cloudspeicherkonto](connections/cloud-storage-blob-connections.md) hoch, z.B. in OneDrive for Business.
- Erstellen oder öffnen Sie eine app für Telefone, [fügen Sie eine Verbindung](add-data-connection.md) auf die **FlooringEstimates** -Tabelle in der Excel-Datei.

    Sie können ein Formular hinzufügen, um eine Tablet-app, aber es wird nicht in diesem Thema überein, da das Formular drei Spalten in der Standardeinstellung verfügen.

- Wenn Sie eine vorhandene app öffnen [fügen Sie einen Bildschirm](add-screen-context-variables.md) zuzuweisen.

## <a name="add-a-form-and-show-data"></a>Hinzufügen eines Formulars und Anzeigen von Daten
1. Fügen Sie auf einen leeren Bildschirm, einen **[Dropdown](controls/control-drop-down.md)** steuern, und nennen Sie sie **ChooseProduct**.

    > [!NOTE]
   > Weitere Informationen zum Hinzufügen und Umbenennen eines Steuerelements sowie zum Festlegen einer Eigenschaft finden Sie unter [Hinzufügen und Konfigurieren eines Steuerelements](add-configure-controls.md).

1. Auf der **Eigenschaften** Registerkarte im rechten Bereich legen Sie **Elemente** zu `FlooringEstimates` und **Wert** zu `Name`.

    ![Festlegen der Items-Eigenschaft des Formulars](./media/add-form/items-property.png)

    In der Liste werden Namen von Bodenbelägen aus der Datenquelle aufgeführt.

1. Hinzufügen einer **bearbeiten** Formularsteuerelement, verschieben Sie es unter **ChooseProduct**, und Ändern der Größe des Formulars, sodass der Großteil des Bildschirms abzudecken.

    ![Ein Formular hinzufügen](./media/add-form/add-a-form.png)

    > [!NOTE]
   > In diesem Thema wird beschrieben, die **bearbeiten** Formularsteuerelement, gleiche Prinzipien gelten jedoch auf die **Anzeige** Formularsteuerelement.

1. Festlegen des Formulars **[DataSource](controls/control-form-detail.md)** Eigenschaft **FlooringEstimates** und die zugehörige **[Element](controls/control-form-detail.md)** Eigenschaft Diese Formel:

    `First(Filter(FlooringEstimates, Name=ChooseProduct.Selected.Value))`

   Mit dieser Formel wird angegeben, dass im Formular nach abgeschlossener Konfiguration der Datensatz angezeigt wird, den der Benutzer in **ChooseProduct** auswählt.

1. Auf der **Eigenschaften** im rechten Bereich auf der Registerkarte **Bearbeitungsfelder**.

    ![Bearbeiten von Feldern](./media/add-form/edit-fields.png)

1. Wählen Sie im Bereich **Felder** die Option **Feld hinzufügen** aus, aktivieren Sie jeweils das Kontrollkästchen für jedes Feld, und klicken Sie auf **Hinzufügen**.

    ![Hinzufügen von Feldern](./media/add-form/add-fields.png)

1. Wählen Sie die Auslassungspunkte (...) neben **Feld hinzufügen**Option **alle reduzieren**, und ziehen Sie dann **Namen** am Anfang der Liste.

    ![Posunout Pole](./media/add-form/move-field.png)

    Die **bearbeiten** Formularsteuerelement zeigt Ihre Änderung.

    ![Formular anzeigen](./media/add-form/show-form1.png)

## <a name="set-the-card-type-for-a-field"></a>Festlegen des Kartentyps für ein Feld
1. In der **Felder** Bereich, erweitern Sie die **Preis** Feld den Pfeil nach unten auswählen.

1. Öffnen der **Steuerelementtyp** aus, und wählen Sie dann **Schieberegler bearbeiten**.

    ![Schieberegler bearbeiten](./media/add-form/edit-slider.png)

    In der Form die **Preis** Feld eine **Schieberegler** steuern anstelle von einer **Texteingabe** Steuerelement.

1. (optional) Gehen Sie zum Ändern des Steuerelements für die **Übersicht** Feld eine **mehrzeiligen Text bearbeiten** Steuerelement.

## <a name="edit-form-only-save-changes"></a>(Nur „Formular bearbeiten“) Speichern der Änderungen

1. Benennen Sie das Formular **EditForm**.

1. Fügen Sie ein **[Button](controls/control-button.md)**-Steuerelement (Schaltfläche) hinzu, und legen Sie seine **[OnSelect](controls/properties-core.md)**-Eigenschaft auf diese Formel fest:

   `SubmitForm(EditForm)`

1. Drücken Sie F5, um die Vorschau zu öffnen, ändern Sie den Namen eines Produkts, und wählen Sie dann auf die Schaltfläche, die Sie erstellt haben.

    Die **[SubmitForm](functions/function-form.md)** Funktion speichert die Änderungen an der Datenquelle.

1. (optional) Schließen Sie die Vorschau durch Drücken von Esc (oder durch Auswahl des schließsymbols in der oberen rechten Ecke).

## <a name="next-steps"></a>Nächste Schritte
Erfahren Sie mehr über das Arbeiten mit [Formularen](working-with-forms.md) und [Formeln](working-with-formulas.md).
