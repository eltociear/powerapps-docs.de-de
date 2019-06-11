---
title: Erstellen Sie eine Zusammenfassung Formular in einer Canvas-app | Microsoft-Dokumentation
description: Erstellen Sie eine Zusammenfassung Formular in einer Canvas-app zum Verwalten von Daten für Northwind Traders
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 04/25/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 5c40cb030241d142a2ee2a68d32f7fb839a350ff
ms.sourcegitcommit: 55bc11ac6a964f22301c9fdadb06ee34e1399f83
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66806742"
ms.PowerAppsDecimalTransform: true
---
# <a name="create-a-summary-form-in-a-canvas-app"></a>Erstellen Sie eine Zusammenfassung Formular in einer Canvas-app

Führen Sie schrittweise Anleitungen zum Erstellen einer Zusammenfassung Formulars in einer Canvas-app für die Verwaltung von fiktiven Daten in der Datenbank Northwind Traders ein. Dieses Thema ist Teil einer Reihe, die erklärt, wie Sie eine Geschäfts-app auf relationalen Daten in Common Data Service zu erstellen. Erkunden Sie diese Themen in dieser Sequenz, für optimale Ergebnisse:

1. [Erstellen eines Katalogs Reihenfolge](northwind-orders-canvas-part1.md).
2. Erstellen Sie ein Formular summary (**in diesem Thema**).
3. [Erstellen Sie einen Katalog Detail](northwind-orders-canvas-part3.md).

> [!div class="mx-imgBorder"]
> ![Definition der Bildschirmbereiche](media/northwind-orders-canvas-part1/orders-parts.png)

## <a name="prerequisites"></a>Voraussetzungen

1. [Installieren Sie die Datenbank Northwind Traders und apps](northwind-install.md).
1. Überprüfen Sie die [Überblick über die Canvas-app](northwind-orders-canvas-overview.md) für Northwind Traders.
1. [Erstellen des Katalogs Reihenfolge](northwind-orders-canvas-part1.md) selbst, oder Sie öffnen die **Northwind Orders (Canvas) – Teil 2 beginnen** -app, die diesem Katalog bereits enthält.

## <a name="add-a-title-bar"></a>Hinzufügen einer Titelleiste

Erstellen Sie im oberen Bereich der app eine Titelleiste angezeigt wird, die Aktionsschaltflächen am Ende dieses Themas enthalten wird.

1. In der **Strukturansicht** wählen Sie im Bereich **Screen1** um sicherzustellen, dass Sie nicht versehentlich ein Steuerelement im Katalog Reihenfolge hinzufügen:

    > [!div class="mx-imgBorder"]
    > ![Wählen Sie im Strukturansichtsbereich Screen1](media/northwind-orders-canvas-part2/titlebar-01.png)

1. Auf der **einfügen** Registerkarte **Bezeichnung** zum Einfügen einer [ **Bezeichnung** ](controls/control-text-box.md) Steuerelement:

    > [!div class="mx-imgBorder"]
    > ![Fügen Sie eine Bezeichnung](media/northwind-orders-canvas-part2/titlebar-02.png)

    Die neue Bezeichnung sollte nur einmal über den Katalog angezeigt werden. Wenn sie in jedem Element des Katalogs angezeigt wird, löschen Sie die erste Instanz die Bezeichnung, stellen Sie sicher, dass der Bildschirm ausgewählt ist, (wie in der vorherige Schritt beschrieben), und fügen Sie die Bezeichnung dann erneut.

1. Verschieben Sie und ändern Sie die neue Bezeichnung, um den oberen Rand des Bildschirms umfassen:

    > [!div class="mx-imgBorder"]
    > ![Verschieben Sie und ändern Sie die Bezeichnung](media/northwind-orders-canvas-part2/titlebar-03.png)

1. Doppelklicken Sie auf den Text der Bezeichnung, und geben Sie **Northwind Orders**.

    Ändern Sie alternativ die **Text** Eigenschaft in der Bearbeitungsleiste auf das gleiche Ergebnis zu erzielen:

    > [!div class="mx-imgBorder"]
    > ![Ändern Sie den Text in der Titelleiste](media/northwind-orders-canvas-part2/titlebar-04.png)

1. Auf der **Startseite** Registerkarte, formatieren Sie die Bezeichnung:
    - Erhöhen Sie die 24 Punkt Schriftgröße an.
    - Legen Sie den Text fett formatiert.
    - Legen Sie den Text weiß.
    - Der Text im Mittelpunkt.
    - Fügen Sie in den Hintergrund einer Füllung dunkelblaue hinzu.

    > [!div class="mx-imgBorder"]
    > ![Formatieren von Optionen auf der Registerkarte "Home"](media/northwind-orders-canvas-part2/titlebar-05.png)

## <a name="add-an-edit-form-control"></a>Fügen Sie ein Edit-Formular-Steuerelement hinzu

In diesem Abschnitt fügen Sie Steuerelemente, um eine Zusammenfassung der beliebiger Reihenfolge angezeigt werden, die der Benutzer im Katalog auswählt.

1. Auf der **einfügen** Registerkarte ein [ **Bearbeitungsformular** ](controls/control-form-detail.md) Steuerelement:

    > [!div class="mx-imgBorder"]
    > ![Fügen Sie ein Edit-Formular-Steuerelement hinzu](media/northwind-orders-canvas-part2/form-01.png)

    Standardmäßig wird das Formular angezeigt in der oberen linken Ecke, in denen möglicherweise andere Steuerelemente nur schwer ermitteln, zu vereinfachen:

    > [!div class="mx-imgBorder"]
    > ![Formularsteuerelement im Standardspeicherort bearbeiten](media/northwind-orders-canvas-part2/form-02.png)

1. Verschieben und ändern Sie die Größe des Formulars, sodass Sie oben rechts auf dem Bildschirm unter der Titelleiste behandelt:

    > [!div class="mx-imgBorder"]
    > ![Verschiebe und verkleinere Sie das Steuerelement zum Formular bearbeiten](media/northwind-orders-canvas-part2/form-03.png)

1. Legen Sie in der Bearbeitungsleiste die **DataSource** -Eigenschaft des Formulars auf diesen Wert:

    ```powerapps-comma
    Orders
    ```

    > [!div class="mx-imgBorder"]
    > ![Legen Sie die DataSource-Eigenschaft des Formularsteuerelements bearbeiten](media/northwind-orders-canvas-part2/form-04.png)

    Sie können dieselbe Eigenschaft festlegen, der **Eigenschaften** Registerkarte am rechten Rand, aber diese Ansatz dem Formular Felder, die Sie benötigen nicht hinzugefügt. Wenn Sie die Bearbeitungsleiste verwenden, bleibt das Formular leer.

## <a name="add-and-arrange-fields"></a>Hinzufügen und Anordnen von Feldern

1. In der **Eigenschaften** Registerkarte am rechten Rand, wählen **Bearbeitungsfelder** zum Öffnen der **Felder** Bereich:

    > [!div class="mx-imgBorder"]
    > ![Öffnen Sie den Bereich "Felder"](media/northwind-orders-canvas-part2/form-05.png)

1. In der **Felder** wählen Sie im Bereich **Feld hinzufügen**, und wählen Sie dann die Kontrollkästchen für die **Kunden** und **Mitarbeiter** Felder.

    > [!div class="mx-imgBorder"]
    > ![Fügen Sie die Kunden- und Mitarbeiterdaten Felder, um das Steuerelement zum Formular bearbeiten](media/northwind-orders-canvas-part2/form-06.png)

1. Scrollen Sie nach unten, bis diese Felder angezeigt werden, und wählen Sie dann die entsprechenden Kontrollkästchen zu deaktivieren:

    - **Anmerkungen**
    - **Auftragsdatum**
    - **Bestellnummer**
    - **Auftragsstatus**
    - **Datum der Zahlung**

    > [!div class="mx-imgBorder"]
    > ![Fügen Sie fünf weitere Felder, um das Steuerelement zum Formular bearbeiten](media/northwind-orders-canvas-part2/form-07.png)

1. Am unteren Rand der **Felder** wählen Sie im Bereich **hinzufügen**, und schließen Sie dann die **Felder** Bereich.

    Das Formular zeigt sieben Felder:

    > [!div class="mx-imgBorder"]
    > ![Edit-Formular-Steuerelement zeigt sieben Felder](media/northwind-orders-canvas-part2/form-08.png)

    > [!NOTE]
    > Wenn ein Feld ein rotes Fehlersymbol angezeigt wird, ein Problem ist möglicherweise aufgetreten, wenn Daten aus der Quelle abgerufen wurde. Aktualisieren Sie die Daten, um den Fehler zu beheben:
    >
    > 1. Klicken Sie auf der Registerkarte **Ansicht** auf **Datenquellen**.
    > 1. In der **Daten** wählen Sie im Bereich **Datenquellen**.
    > 1. Neben **Bestellungen**, wählen Sie die Auslassungspunkte (...), wählen Sie **aktualisieren**, und schließen Sie dann die **Daten** Bereich.
    >
    > Wenn das Kombinationsfeld für den Namen der Kunden oder Mitarbeiter weiterhin einen Fehler angezeigt, überprüfen Sie die **primärer Text** und **SearchField** der jedes Feld, und öffnen Sie anschließend die **Daten** im Bereich. Für Feld "Kunde", beide Felder festgelegt werden soll, um **Nwind_company**. Für die Employee-Feld, beide Felder festgelegt werden soll, um **Nwind_lastname**.

1. Ändern Sie mit ausgewähltem Formular die Anzahl der Spalten im Formular von 3 bis 12 in der **Eigenschaften** Registerkarte am rechten Rand.

    Dieser Schritt bietet mehr Flexibilität, wie Sie die Felder anordnen:

    > [!div class="mx-imgBorder"]
    > ![Ändern Sie Anzahl der Spalten in das Steuerelement zum Formular bearbeiten](media/northwind-orders-canvas-part2/form-08b.png)

    Viele Benutzeroberflächendesigns basieren auf 12-spaltiges Layouts, da sie gleichmäßig die Zeilen 1, 2, 3, 4, 6 und 12-Steuerelementen aufnehmen können. In diesem Thema erstellen Sie eine Übersicht der Zeilen, die 1, 2 oder 4-Steuerelemente enthalten.

1. Verschieben Sie und ändern Sie die Felder durch Ziehen die Handles, wie jedes andere Steuerelement, sodass jede Zeile dieser Datenkarten in der angegebenen Reihenfolge enthält:

    - Erste Zeile: **Bestellnummer**, **Bestellstatus**, **Order Date**, und **bezahlt Datum**
    - Zweite Zeile: **Kunden** und **Mitarbeiter**
    - Dritte Zeile: **Anmerkungen**

    > [!NOTE]
    > Sie finden es vielleicht einfacher erweitern die **Anmerkungen zu dieser**, **Kunden**, und **Mitarbeiter** Daten wurde, bevor Sie diese anordnen können.

    > [!div class="mx-imgBorder"]
    > ![Verschiebe und verkleinere Sie Felder](media/northwind-orders-canvas-part2/form-rearrange.gif)

    Weitere Informationen dazu, wie Sie die Felder in einem Formular anordnen: [Grundlegendes zum Layout von Datenformularen für Canvas-apps](working-with-form-layout.md).

## <a name="hide-time-controls"></a>Ausblenden von Steuerelementen für Zeit

In diesem Beispiel benötigen Sie nicht den Uhrzeitteil von die Datumsfelder enthalten, da den Benutzer diesen Grad an Granularität abgelenkt werden kann. Wenn Sie diese löschen, können Sie Probleme in Formeln verursachen, die für diese Steuerelemente Date-Werten zu aktualisieren oder bestimmen die Position eines anderen Steuerelements auf der Datenkarte basieren. Stattdessen werden Sie durch Festlegen der Zeitauswahl Ausblenden ihrer **Visible** Eigenschaft.

1. In der **Strukturansicht** wählen Sie im Bereich der **Bestelldatum** Datenkarte.

    Die Karte kann einen anderen Namen haben, enthält aber **Bestelldatum**.

1. Halten Sie die UMSCHALTTASTE gedrückt, wählen Sie die Stunde, Minute und Doppelpunkt als Trennzeichen Steuerelemente in der **Bestelldatum** Datenkarte.

    > [!div class="mx-imgBorder"]
    > ![Wählen Sie die Zeitauswahl auf Order Date-Karte](media/northwind-orders-canvas-part2/form-09.png)

1. Festlegen der Steuerelemente **Visible** Eigenschaft **"false"** .

    Alle ausgewählten Steuerelemente nicht mehr aus dem Formular angezeigt:

    > [!div class="mx-imgBorder"]
    > ![Visible-Eigenschaft auf "false" festgelegt.](media/northwind-orders-canvas-part2/form-10.png)

1. Ändern der Größe der [ **Datumsauswahl** ](controls/control-date-picker.md) Steuerelement, das vollständige Datum anzuzeigen:

    > [!div class="mx-imgBorder"]
    > ![Ändern der Größe der Datumsauswahl-Steuerelement](media/northwind-orders-canvas-part2/form-11.png)

    Als Nächstes müssen Sie für die letzten Schritte wiederholen der **bezahlt Datum** Feld.

1. In der **Strukturansicht** wählen Sie im Bereich die Zeit, in steuert der **bezahlt Datum** Datenkarte:

    > [!div class="mx-imgBorder"]
    > ![Wählen Sie-Steuerelement in kostenpflichtigen-Date-Karte](media/northwind-orders-canvas-part2/form-12.png)

1. Legen Sie die ausgewählten Steuerelemente **Visible** Eigenschaft **"false"** :

    > [!div class="mx-imgBorder"]
    > ![Visible-Eigenschaft auf "false" festgelegt.](media/northwind-orders-canvas-part2/form-13.png)

1. Ändern der Größe der Datumsauswahl in die **Datum bezahlt** Karte:

    > [!div class="mx-imgBorder"]
    > ![Ändern der Größe der Datumsauswahl-Steuerelement](media/northwind-orders-canvas-part2/form-14.png)

## <a name="connect-the-order-gallery"></a>Verbinden Sie den Order-Katalog

1. In der **Strukturansicht** , reduzieren Sie das Formular, um den Namen des Katalogs Reihenfolge leichter zu finden, und klicken Sie dann bei Bedarf, benennen Sie sie in **Gallery1**.

1. Legen Sie die Zusammenfassung des **Element** Eigenschaft auf den folgenden Ausdruck:

    ```powerapps-comma
    Gallery1.Selected
    ```

    > [!div class="mx-imgBorder"]
    > ![Set-Item-Eigenschaft des Formulars](media/northwind-orders-canvas-part2/form-15.png)

    Das Formular zeigt eine Zusammenfassung der gewünschten Reihenfolge der app-Benutzer in der Liste auswählt.

    > [!div class="mx-imgBorder"]
    > ![Wählen Sie einen Auftrag in der Liste, um die Übersicht über die im Formular anzuzeigen.](media/northwind-orders-canvas-part2/form-select.gif)

## <a name="replace-a-data-card"></a>Ersetzen einer Datenkarte

**Bestellnummer** ist ein Bezeichner, die Common Data Service automatisch zugewiesen, wenn Sie einen Datensatz erstellen. Dieses Feld hat eine [ **Texteingabe** ](controls/control-text-input.md) Steuerelement standardmäßig aber ersetzen Sie es mit einer Bezeichnung, damit der Benutzer dieses Feld nicht bearbeiten kann.

1. Wählen Sie das Formular, **Bearbeitungsfelder** in die **Eigenschaften** Registerkarte am rechten Rand, und wählen Sie dann die **Bestellnummer** Feld:

    > [!div class="mx-imgBorder"]
    > ![Wählen Sie das Zahlenfeld Reihenfolge](media/northwind-orders-canvas-part2/alt-01.png)

1. Öffnen der **Steuerelementtyp** Liste:

    > [!div class="mx-imgBorder"]
    > ![Öffnen der ** Steuerelementliste Typ **](media/northwind-orders-canvas-part2/alt-02,png)

1. Wählen Sie die **Anzeigetext** Datenkarte:

    > [!div class="mx-imgBorder"]
    > ![Wählen Sie die ** Ansicht Text ** Datenkarte](media/northwind-orders-canvas-part2/alt-02b.png)

1. Schließen der **Felder** Bereich.

    Der Benutzer kann die Bestellnummer nicht mehr ändern:

    > [!div class="mx-imgBorder"]
    > ![Bestellnummer ist schreibgeschützt](media/northwind-orders-canvas-part2/alt-03.png)

1. Auf der **Startseite** Registerkarte, die Bestellnummer Schriftgrad auf 20 Punkt ändern, sodass das Feld leichter zu finden ist:

    > [!div class="mx-imgBorder"]
    > ![Ändern Sie die Bestellnummer Schriftgrad](media/northwind-orders-canvas-part2/alt-04.png)

## <a name="use-a-many-to-one-relationship"></a>Verwenden Sie eine viele-zu-eins-Beziehung

Die **Bestellungen** Entität verfügt über eine n: 1 Beziehung mit der **Mitarbeiter** Entität: jeder Mitarbeiter kann viele Aufträge erstellen, aber jede Bestellung kann nur einem Mitarbeiter zugewiesen werden. Wenn der Benutzer wählt einen Mitarbeiter in der [ **Kombinationsfeld** ](controls/control-combo-box.md) -Steuerelement, dessen **ausgewählte** Eigenschaft bietet dieses Mitarbeiters gesamten Datensatz aus der **Mitarbeiter**  Entität. Daher können Sie konfigurieren eine [ **Image** ](controls/control-image.md) -Steuerelement an dem Bild der alle Mitarbeiter der Benutzer im Kombinationsfeld auswählt.

1. Wählen Sie die **Mitarbeiter** Datenkarte:

    > [!div class="mx-imgBorder"]
    > ![Wählen Sie die Employee-Daten-Karte](media/northwind-orders-canvas-part2/employee-01.png)

1. In der **erweitert** Registerkarte am rechten Rand, die Datenkarte zu entsperren, damit Sie Formeln bearbeiten können, die zuvor schreibgeschützt waren:

    > [!div class="mx-imgBorder"]
    > ![Entsperren Sie die Employee-Daten-Karte](media/northwind-orders-canvas-part2/employee-02.png)

1. Reduzieren Sie die Breite des Kombinationsfelds, um Platz für die Mitarbeiter-Bild zu machen, in der Datenkarte:

    > [!div class="mx-imgBorder"]
    > ![Die Größe des Kombinationsfeld-Steuerelements](media/northwind-orders-canvas-part2/employee-03b.png)

1. Auf der **einfügen** Registerkarte **Media** > **Image**:

    > [!div class="mx-imgBorder"]
    > ![Ein Bild einfügen](media/northwind-orders-canvas-part2/employee-04.png)

    Ein Bild angezeigt wird, in der Datenkarte, der erweitert wird, um es zu berücksichtigen:

    > [!div class="mx-imgBorder"]
    > ![Mitarbeiter Datenkarte mit Image-Steuerelement](media/northwind-orders-canvas-part2/employee-05.png)

1. Die Bildgröße aus, und verschieben Sie es rechts neben dem Kombinationsfeld:

    > [!div class="mx-imgBorder"]
    > ![Verschiebe und verkleinere Sie das Image-Steuerelement](media/northwind-orders-canvas-part2/employee-06.png)

1. Legen Sie die **Image** -Eigenschaft des Bildes auf diese Formel, und Ersetzen Sie dabei die Zahl am Ende des DataCardValue bei Bedarf:

    ```powerapps-comma
    DataCardValue7.Selected.Picture
    ```

    > [!div class="mx-imgBorder"]
    > ![Legen Sie die Image-Eigenschaft des Images](media/northwind-orders-canvas-part2/employee-07.png)

    Das Bild des ausgewählten Mitarbeiters wird angezeigt.

1. Halten Sie die Alt-Taste gedrückt markieren ein anderes Mitarbeiters im Kombinationsfeld, um zu bestätigen, dass das Bild auch geändert.

    > [!div class="mx-imgBorder"]
    > ![Wählen Sie einen Mitarbeiter des Mitarbeiters Bild angezeigt.](media/northwind-orders-canvas-part2/employee-select.gif)

## <a name="add-a-save-icon"></a>Ein Symbol "Speichern" hinzufügen "

1. In der **Strukturansicht** wählen Sie im Bereich **Screen1**, und wählen Sie dann **einfügen** > **Symbole**  >  **Überprüfen**:

    > [!div class="mx-imgBorder"]
    > ![Fügen Sie Häkchen Symbol](media/northwind-orders-canvas-part2/save-01.png)

    Die [ **überprüfen** ](controls/control-shapes-icons.md) Symbol angezeigt wird in der oberen linken Ecke wird standardmäßig, in denen möglicherweise andere Steuerelemente das Symbol nur schwer ermitteln, stellen:

    > [!div class="mx-imgBorder"]
    > ![Symbol im Standardspeicherort](media/northwind-orders-canvas-part2/save-02.png)

1. Auf der **Startseite** Registerkarte die **Farbe** Eigenschaft des Symbols, das weiß, Skalieren das Symbol und verschieben Sie sie am rechten Rand der Titelleiste angezeigt:

    > [!div class="mx-imgBorder"]
    > ![Konfigurieren Sie die Farbe, Größe und das Speichern Symbol](media/northwind-orders-canvas-part2/save-03.png)

1. In der **Strukturansicht** Bereich bestätigen, dass es sich bei den Namen des Formulars wird **Form1**, und legen Sie dann auf des Symbol " **OnSelect** -Eigenschaft auf diese Formel:

    ```powerapps-comma
    SubmitForm( Form1 )
    ```

    > [!div class="mx-imgBorder"]
    > ![Legen Sie den Speichervorgang Symbols OnSelect-Eigenschaft](media/northwind-orders-canvas-part2/save-04.png)

    Wenn der Benutzer das Symbol auswählt, wird die [ **SubmitForm** ](functions/function-form.md) Funktion geänderte Werte in der Form sammelt und sendet sie an der Datenquelle. Punkte März am oberen Rand des Bildschirms, die Daten übermittelt werden, und die Order-Katalog werden die Änderungen wider, nachdem der Prozess abgeschlossen wurde.

1. Legen Sie des Symbol " **" DisplayMode "** -Eigenschaft auf diese Formel:

    ```powerapps-comma
    If( Form1.Unsaved; DisplayMode.Edit; DisplayMode.Disabled )
    ```

    > [!div class="mx-imgBorder"]
    > ![Legen Sie das Symbol "DisplayMode-Eigenschaft](media/northwind-orders-canvas-part2/save-05.png)

    Wenn alle Änderungen in das Formular gespeichert wurden, wird das Symbol ist deaktiviert und wird in der **DisabledColor**, die Sie als Nächstes festgelegt werden.

1. Legen Sie des Symbol " **DisabledColor** -Eigenschaft auf diesen Wert:

    ```powerapps-comma
    Gray
    ```

    > [!div class="mx-imgBorder"]
    > ![Legen Sie das Symbol "DisabledColor-Eigenschaft](media/northwind-orders-canvas-part2/save-06.png)

    Der Benutzer kann Änderungen einer Bestellung speichern, indem Sie auf das Symbol Kontrollkästchen, das dann deaktiviert und abgeblendet, bis der Benutzer eine andere Änderung vorgenommen:

    > [!div class="mx-imgBorder"]
    > ![Speichern von Änderungen](media/northwind-orders-canvas-part2/save-submit.gif)

## <a name="add-a-cancel-icon"></a>Fügen Sie ein Symbol "Abbrechen" hinzu.

1. Auf der **einfügen** Registerkarte **Symbole** > **Abbrechen**:

    > [!div class="mx-imgBorder"]
    > ![Symbol "Abbrechen" hinzufügen](media/northwind-orders-canvas-part2/save-07.png)

    Das Symbol wird in der oberen linken Ecke standardmäßig, in denen möglicherweise andere Steuerelemente das Symbol suchen erschweren:

    > [!div class="mx-imgBorder"]
    > ![Symbol "Abbrechen" im Standardspeicherort](media/northwind-orders-canvas-part2/save-08.png)

1. Auf der **Startseite** Registerkarte, ändern Sie das Symbol des **Farbe** Eigenschaft weiß, das Symbol ändern der Größe und verschieben Sie es auf der linken Seite das Symbol Kontrollkästchen:

    > [!div class="mx-imgBorder"]
    > ![Ändern der Farbe, Größe und Speicherort für das Symbol "Abbrechen"](media/northwind-orders-canvas-part2/save-09.png)

1. Legen Sie des Symbol "Abbrechen" des **OnSelect** -Eigenschaft auf diese Formel:

    ```powerapps-comma
    ResetForm( Form1 )
    ```

    > [!div class="mx-imgBorder"]
    > ![Legen Sie das Symbol "Abbrechen" des OnSelect-Eigenschaft](media/northwind-orders-canvas-part2/save-10.png)

    Die [ **"resetform"** ](functions/function-form.md) Funktion verwirft alle Änderungen in das Formular, das an den ursprünglichen Zustand zurückgegeben.

1. Legen Sie des Symbol "Abbrechen" des **"DisplayMode"** -Eigenschaft auf diese Formel:

    ```powerapps-comma
    If( Form1.Unsaved Or Form1.Mode = FormMode.New; DisplayMode.Edit; DisplayMode.Disabled )
    ```

    > [!div class="mx-imgBorder"]
    > ![Legen Sie das Symbol "Abbrechen" des DisplayMode-Eigenschaft](media/northwind-orders-canvas-part2/save-11.png)

    Diese Formel unterscheidet sich geringfügig von der für das Symbol Kontrollkästchen. Das Symbol "Abbrechen" ist deaktiviert, wenn alle Änderungen gespeichert wurden oder das Formular in **neu** Modus, den Sie als Nächstes ermöglichen. In diesem Fall **"resetform"** verwirft den neuen Datensatz.

1. Legen Sie des Symbol "Abbrechen" des **DisabledColor** -Eigenschaft auf diesen Wert:

    ```powerapps-comma
    Gray
    ```

    > [!div class="mx-imgBorder"]
    > ![Legen Sie das Symbol "Abbrechen" des DisabledColor-Eigenschaft](media/northwind-orders-canvas-part2/save-12.png)

    Der Benutzer kann Änderungen an einer Bestellung abbrechen, und die Symbole für Überprüfung und "Abbrechen" deaktiviert und abgeblendet, wenn alle Änderungen gespeichert wurden:

    > [!div class="mx-imgBorder"]
    > ![Speichern und Abbrechen von Änderungen](media/northwind-orders-canvas-part2/save-cancel.gif)

## <a name="add-an-add-icon"></a>Ein Symbol hinzufügen "hinzufügen"

1. Auf der **einfügen** Registerkarte **Symbole** > **hinzufügen**.

    > [!div class="mx-imgBorder"]
    > ![Fügen Sie ein Symbol hinzufügen](media/northwind-orders-canvas-part2/save-13.png)

    Die **hinzufügen** Symbol wird angezeigt, in der oberen linken Ecke standardmäßig, in denen möglicherweise andere Steuerelemente nur schwer ermitteln, zu vereinfachen:

    > [!div class="mx-imgBorder"]
    > ![Der Standardspeicherort der hinzufügen-Symbol](media/northwind-orders-canvas-part2/save-14.png)

1. Auf der **Startseite** Registerkarte die **Farbe** Eigenschaft des Symbols, das weiß, Skalieren das Symbol und verschieben Sie es links neben dem Symbol "Abbrechen" hinzufügen:

    > [!div class="mx-imgBorder"]
    > ![Ändern der Farbe, Größe und Position des Symbols hinzufügen](media/northwind-orders-canvas-part2/save-15.png)

1. Legen Sie des Symbols zum Hinzufügen des **OnSelect** -Eigenschaft auf diese Formel:

    ```powerapps-comma
    NewForm( Form1 )
    ```

    > [!div class="mx-imgBorder"]
    > ![Legen Sie das Symbol zum Hinzufügen der OnSelect-Eigenschaft](media/northwind-orders-canvas-part2/save-15b.png)

    Die [ **NewForm** ](functions/function-form.md) Funktion zeigt einen leeren Datensatz in der Form.  

1. Legen Sie des Symbols zum Hinzufügen des **"DisplayMode"** -Eigenschaft auf diese Formel:

    ```powerapps-comma
    If( Form1.Unsaved Or Form1.Mode = FormMode.New; DisplayMode.Disabled; DisplayMode.Edit )
    ```

    > [!div class="mx-imgBorder"]
    > ![Legen Sie das Symbol zum Hinzufügen der DisplayMode-Eigenschaft](media/northwind-orders-canvas-part2/save-16.png)

    Die Formel wird das Symbol zum Hinzufügen unter diesen Bedingungen deaktiviert:

    - Der Benutzer nimmt Änderungen vor, aber nicht speichern oder Abbrechen, dies ist das entgegengesetzte Verhalten aus den Symbolen überprüfen "und" Abbrechen.
    - Der Benutzer wählt das Symbol zum Hinzufügen, aber es werden keine Änderungen.

1. Legen Sie des Symbols zum Hinzufügen des **DisabledColor** -Eigenschaft auf diesen Wert:

    ```powerapps-comma
    Gray
    ```

    > [!div class="mx-imgBorder"]
    > ![Legen Sie das Symbol zum Hinzufügen des DisabledColor-Eigenschaft](media/northwind-orders-canvas-part2/save-17.png)

    Der Benutzer kann einen Auftrag erstellen, wenn sie keine Änderungen vornehmen, oder sie speichern oder Abbrechen von Änderungen, die sie vorgenommen haben. (Wenn der Benutzer dieses Symbol auswählt, können nicht sie es erneut auswählen, bis sie eine oder mehrere Änderungen vornehmen, und klicken Sie dann speichern oder diese Änderungen verwerfen):

    > [!div class="mx-imgBorder"]
    > ![Erstellen eines Auftrags](media/northwind-orders-canvas-part2/save-new.gif)

> [!NOTE]
> Wenn Sie erstellen und speichern Sie eine Bestellung, müssen Sie möglicherweise nach unten scrollen, in der Order-Galerie, um Ihre neue Bestellung anzeigen. Es muss nicht Gesamtpreis, da Sie die Details für die Bestellung noch hinzugefügt haben.

## <a name="add-a-trash-icon"></a>Ein Papierkorbsymbol "hinzufügen"

1. Auf der **einfügen** Registerkarte **Symbole** > **Papierkorb**.

    > [!div class="mx-imgBorder"]
    > ![Fügen Sie ein Papierkorbsymbol](media/northwind-orders-canvas-part2/save-18.png)

    Die **Papierkorb** Symbol wird angezeigt, in der oberen linken Ecke standardmäßig, in denen möglicherweise andere Steuerelemente nur schwer ermitteln, zu vereinfachen:

    > [!div class="mx-imgBorder"]
    > ![Standardspeicherort für das Papierkorb-Symbol](media/northwind-orders-canvas-part2/save-19.png)

1. Auf der **Startseite** Registerkarte, wechseln Sie des Papierkorbsymbol **Farbe** Eigenschaft weiß, das Symbol ändern der Größe und verschieben Sie es auf der linken Seite, der das Symbol zum Hinzufügen:

    > [!div class="mx-imgBorder"]
    > ![Ändern der Farbe, Größe und Speicherort für das Papierkorb-Symbol](media/northwind-orders-canvas-part2/save-20.png)

1. Legen Sie des Papierkorbsymbol **OnSelect** -Eigenschaft auf diese Formel:

    ```powerapps-comma
    Remove( Orders; Gallery1.Selected )
    ```

    > [!div class="mx-imgBorder"]
    > ![Legen Sie das Papierkorbsymbol OnSelect-Eigenschaft](media/northwind-orders-canvas-part2/save-21.png)

    Die [ **entfernen** ](functions/function-remove-removeif.md) -Funktion entfernt einen Datensatz aus einer Datenquelle. In dieser Formel entfernt die Funktion den Datensatz, der im Order-Katalog ausgewählt ist. Das Papierkorb-Symbol wird in der Nähe der kombinierten Formular (nicht der Reihenfolge Gallery) angezeigt, da das Formular zeigt weitere Details zu dem Datensatz, damit der Benutzer den Datensatz, den die Formel gelöscht werden, leichter identifizieren kann.

1. Legen Sie des Papierkorbsymbol **"DisplayMode"** -Eigenschaft auf diese Formel:

    ```powerapps-comma
    If( Form1.Mode = FormMode.New; DisplayMode.Disabled; DisplayMode.Edit )
    ```

    > [!div class="mx-imgBorder"]
    > ![Legen Sie das Papierkorbsymbol DisplayMode-Eigenschaft](media/northwind-orders-canvas-part2/save-22.png)

    Diese Formel wird das Papierkorbsymbol deaktiviert, wenn der Benutzer einen Datensatz erstellt. Bis der Benutzer den Datensatz, speichert die **entfernen** Funktion hat keinen Datensatz zu löschen.

1. Legen Sie des Papierkorbsymbol **DisabledColor** -Eigenschaft auf diesen Wert:

    ```powerapps-comma
    Gray
    ```

    > [!div class="mx-imgBorder"]
    > ![Legen Sie das Papierkorbsymbol DisabledColor-Eigenschaft](media/northwind-orders-canvas-part2/save-23.png)

    Der Benutzer kann es sich um eine Bestellung löschen.

    > [!div class="mx-imgBorder"]
    > ![Löschen von Aufträgen](media/northwind-orders-canvas-part2/save-delete.gif)

## <a name="summary"></a>Zusammenfassung

Zusammenfassend lässt sich sagen, haben Sie ein Formular, in dem der Benutzer kann anzeigen und bearbeiten Sie eine Zusammenfassung jedes Auftrags, und Sie verwendet diese Elemente, hinzugefügt:

- Ein Formular, das zeigt, Daten aus der **Bestellungen** Entität: **Form1.DataSource =** `Orders`
- Eine Verbindung zwischen dem Formular und dem Order-Katalog: **Form1.Item =** `Gallery1.Selected`
- Ein alternativer-Steuerelement für die **Bestellnummer** Feld: **Text anzeigen**
- Eine n: 1 Beziehung zum Anzeigen des Mitarbeiters Bild in der **Mitarbeiter** Datenkarte: `DataCardValue1.Selected.Picture`
- Ein Symbol, einen Auftrag zu speichern: `SubmitForm( Form1 )`
- Ein Symbol zum Abbrechen von Änderungen an einer Bestellung: `ResetForm( Form1 )`
- Ein Symbol, um einen Auftrag zu erstellen: `NewForm( Form1 )`
- Ein Symbol, um einen Auftrag zu löschen: `Remove( Orders; Gallery1.Selected )`

## <a name="next-step"></a>Nächster Schritt

Im nächsten Thema, fügen Sie einen anderen Katalog, um die Produkte in jeder Bestellung anzeigen und ändern Sie diese Details mit der [ **Patch** ](functions/function-patch.md) Funktion.

> [!div class="nextstepaction"]
> [Erstellen des Detail-Katalogs](northwind-orders-canvas-part3.md)
