---
title: Erstellen eines Zusammenfassungs Formulars in einer Canvas-App | Microsoft-Dokumentation
description: Erstellen eines Zusammenfassungs Formulars in einer Canvas-App zum Verwalten von Daten für Northwind Traders
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 11/06/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 6f49057e55ea52dac98c92109752a05276eec831
ms.sourcegitcommit: 32542f1d17fee757dcdaf9c247f4051f59b86434
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "73741832"
---
# <a name="create-a-summary-form-in-a-canvas-app"></a>Erstellen eines Zusammenfassungs Formulars in einer Canvas-App

Befolgen Sie die Schritt-für-Schritt-Anleitungen zum Erstellen eines Zusammenfassungs Formulars in einer Canvas-App zum Verwalten von fiktiven Daten in der Datenbank Northwind Traders. Dieses Thema ist Teil einer Reihe, in der erläutert wird, wie eine Geschäfts-App für relationale Daten in Common Data Service erstellt wird. Um optimale Ergebnisse zu erzielen, sollten Sie sich diese Themen in dieser Sequenz ansehen:

1. [Erstellen Sie eine Order Gallery](northwind-orders-canvas-part1.md).
2. Erstellen Sie ein Zusammenfassungs Formular (**dieses Thema**).
3. [Erstellen Sie eine Detail Galerie](northwind-orders-canvas-part3.md).

> [!div class="mx-imgBorder"]
> ![Definition der Bildschirmbereiche](media/northwind-orders-canvas-part1/orders-parts.png)

## <a name="prerequisites"></a>Voraussetzungen

1. [Installieren Sie die Datenbank Northwind Traders und die apps](northwind-install.md).
1. Lesen Sie die [Übersicht über die Canvas-App](northwind-orders-canvas-overview.md) für Northwind Traders.
1. [Erstellen Sie die Order Gallery](northwind-orders-canvas-part1.md) selbst, oder öffnen Sie die APP **Northwind Orders (Canvas)-BEGIN Part 2** , die diesen Katalog bereits enthält.

## <a name="add-a-title-bar"></a>Hinzufügen einer Titelleiste

Erstellen Sie am oberen Rand der App eine Titelleiste, in der die Aktions Schaltflächen am Ende dieses Themas enthalten sind.

1. Wählen Sie im Struktur **Ansichts** Bereich die Option **Screen1** aus, um sicherzustellen, dass Sie der Order Gallery nicht versehentlich ein Steuerelement hinzufügen:

    > [!div class="mx-imgBorder"]
    > ![wählen Sie im Struktur Ansichts Bereich Screen1 aus](media/northwind-orders-canvas-part2/titlebar-01.png)

1. Wählen Sie auf der Registerkarte **Einfügen** die **Bezeichnung Bezeichnung** aus, um das Steuerelement [**Bezeichnung**](controls/control-text-box.md) einzufügen:

    > [!div class="mx-imgBorder"]
    > ![eine Bezeichnung einfügen](media/northwind-orders-canvas-part2/titlebar-02.png)

    Die neue Bezeichnung sollte nur einmal oberhalb der Galerie angezeigt werden. Wenn Sie in jedem Element des Katalogs angezeigt wird, löschen Sie die erste Instanz der Bezeichnung. Stellen Sie sicher, dass der Bildschirm ausgewählt ist (wie im vorherigen Schritt beschrieben), und fügen Sie dann die Bezeichnung erneut ein.

1. Verschieben Sie die neue Bezeichnung, und ändern Sie Sie so, dass Sie sich über den oberen Bildschirmrand erstreckt:

    > [!div class="mx-imgBorder"]
    > ![verschieben Sie die Bezeichnung, und ändern Sie die Größe](media/northwind-orders-canvas-part2/titlebar-03.png)

1. Doppelklicken Sie auf den Text der Bezeichnung, und geben Sie dann **Northwind Orders**ein.

    Ändern Sie alternativ die Text-Eigenschaft in der **Bearbeitungs** Leiste, um das gleiche Ergebnis zu erzielen:

    > [!div class="mx-imgBorder"]
    > ![ändern Sie den Text in der Titelleiste](media/northwind-orders-canvas-part2/titlebar-04.png)

1. Formatieren Sie die Bezeichnung auf der Registerkarte **Start** :
    - Vergrößern Sie den Schrift Grad auf 24 Punkte.
    - Legen Sie den Text fett.
    - Legen Sie den Text weiß.
    - Zentrieren Sie den Text.
    - Fügen Sie dem Hintergrund eine dunkelblaue Füllung hinzu.

    > [!div class="mx-imgBorder"]
    > ![Formatierungsoptionen auf der Registerkarte Home](media/northwind-orders-canvas-part2/titlebar-05.png)

## <a name="add-an-edit-form-control"></a>Bearbeitungs Formular-Steuerelement hinzufügen

In diesem Abschnitt fügen Sie Steuerelemente hinzu, um eine Zusammenfassung einer beliebigen Reihenfolge anzuzeigen, die der Benutzer im Katalog auswählt.

1. Fügen Sie auf der Registerkarte **Einfügen** ein [**Formular bearbeiten**](controls/control-form-detail.md) -Steuerelement ein:

    > [!div class="mx-imgBorder"]
    > ![ein Bearbeitungs Formular-Steuerelement hinzufügen](media/northwind-orders-canvas-part2/form-01.png)

    Standardmäßig wird das Formular in der oberen linken Ecke angezeigt, in dem andere Steuerelemente das Auffinden erschweren können:

    > [!div class="mx-imgBorder"]
    > ![Formular Steuerelement an Standard Speicherort bearbeiten](media/northwind-orders-canvas-part2/form-02.png)

1. Verschieben Sie das Formular, und ändern Sie die Größe so, dass es die obere rechte Ecke des Bildschirms in der Titelleiste abdeckt:

    > [!div class="mx-imgBorder"]
    > ![das Bearbeitungs Formular-Steuerelement verschieben und die Größe ändern](media/northwind-orders-canvas-part2/form-03.png)

1. Wählen Sie im Bereich **Eigenschaften** die Dropdown Leiste **Datenquelle** aus.

    > [!div class="mx-imgBorder"]
    > ![legen Sie die DataSource-Eigenschaft des Bearbeitungs Formular-Steuer Elements fest](media/northwind-orders-canvas-part2/form-04a.png)

1. Wählen Sie die Datenquelle **Orders** aus.

    > [!div class="mx-imgBorder"]
    > ![legen Sie die DataSource-Eigenschaft des Bearbeitungs Formular-Steuer Elements fest](media/northwind-orders-canvas-part2/form-04.png)

## <a name="add-and-arrange-fields"></a>Felder hinzufügen und anordnen

1. Wählen Sie auf der Registerkarte **Eigenschaften** in der Nähe des rechten Rands **Felder bearbeiten** aus, um den **Bereich Felder** zu öffnen.

    > [!div class="mx-imgBorder"]
    > ![den Bereich Felder öffnen](media/northwind-orders-canvas-part2/form-05.png)

1. Wenn der **Bereich Felder** nicht leer ist, entfernen Sie die Felder, die bereits eingefügt wurden.  

    > [!div class="mx-imgBorder"]
    > ![den Bereich Felder öffnen](media/northwind-orders-canvas-part2/form-06a.png)

1. Nachdem die Liste der Felder leer ist, wählen Sie **Feld hinzufügen**aus, und aktivieren Sie dann die Kontrollkästchen für die Felder **Customer** und **Employee** .

    > [!div class="mx-imgBorder"]
    > ![die Felder Customer und Employee dem Bearbeitungs Formular-Steuerelement hinzufügen](media/northwind-orders-canvas-part2/form-06b.png)

1. Scrollen Sie nach unten, bis diese Felder angezeigt werden, und aktivieren Sie dann die entsprechenden Kontrollkästchen:

    - **Anmerkungen**
    - **Bestelldatum**
    - **Bestellnummer**
    - **Bestell Status**
    - **Kostenpflichtiges Datum**

    > [!div class="mx-imgBorder"]
    > ![dem Bearbeitungs Formular-Steuerelement fünf weitere Felder hinzufügen](media/northwind-orders-canvas-part2/form-06c.png)

    > [!div class="mx-imgBorder"]
    > ![dem Bearbeitungs Formular-Steuerelement fünf weitere Felder hinzufügen](media/northwind-orders-canvas-part2/form-06d.png)

1. Wählen Sie unten im **Bereich "Felder** " die Option **Hinzufügen**aus, und schließen Sie dann den **Bereich Felder** .

    Das Formular zeigt sieben Felder an, die sich in einer anderen Reihenfolge befinden können:

    > [!div class="mx-imgBorder"]
    > ![Formular Formular bearbeiten zeigt sieben Felder an](media/northwind-orders-canvas-part2/form-08.png)

    > [!NOTE]
    > Wenn ein Feld ein rotes Fehler Symbol anzeigt, ist möglicherweise ein Problem aufgetreten, als Daten aus der Quelle abgerufen wurden. Aktualisieren Sie die Daten, um den Fehler zu beheben:
    >
    > 1. Klicken Sie auf der Registerkarte **Ansicht** auf die Option **Datenquellen**.
    > 1. Wählen Sie im Bereich **Daten** die Option **Datenquellen**aus.
    > 1. Wählen Sie neben **Orders**(...) die Auslassungs Punkte (...) aus, wählen Sie **Aktualisieren**aus, und schließen Sie dann den Bereich **Daten** .
    >
    > Wenn das Kombinations Feld für den Kunden-oder Mitarbeiter Namen weiterhin einen Fehler anzeigt, überprüfen Sie den **primären Text** und das Suchfeld jedes **Felds** , indem Sie es auswählen und dann den Bereich **Daten** öffnen. Für das Feld Customer müssen beide Felder auf **nwind_company**festgelegt werden. Für das Feld Mitarbeiter müssen beide Felder auf **nwind_lastname**festgelegt werden.

1. Wenn das Formular ausgewählt ist, ändern Sie die Anzahl der Spalten im Formular von 3 in 12 auf der Registerkarte **Eigenschaften** in der Nähe des rechten Rands.

    Durch diesen Schritt wird die Flexibilität beim Anordnen der Felder erhöht:

    > [!div class="mx-imgBorder"]
    > ![ändern Sie dann die Anzahl der Spalten im Bearbeitungs Formular-Steuerelement](media/northwind-orders-canvas-part2/form-08b.png)

    Viele UI-Entwürfe basieren auf 12-spaltigen Layouts, da Sie Zeilen von 1, 2, 3, 4, 6 und 12 Steuerelementen gleichmäßig abdecken können. In diesem Thema erstellen Sie Zeilen, die 1, 2 oder 4 Steuerelemente enthalten.

1. Verschieben und ändern Sie die Größe der Felder, indem Sie Ihre Handles genau wie jedes andere Steuerelement ziehen, damit jede Zeile diese Datenkarten in der angegebenen Reihenfolge enthält:

    - Erste Zeile: **Bestellnummer**, **Bestell Status**, **Bestelldatum**und **kostenpflichtiges Datum**
    - Zweite Zeile: **Kunde** und **Mitarbeiter**
    - Dritte Zeile: **Notizen**

    > [!NOTE]
    > Möglicherweise ist es einfacher, die Datenkarten für **Notizen**, **Kunden**und **Mitarbeiter** zu erweitern, bevor Sie Sie anordnen.

    > [!div class="mx-imgBorder"]
    > ![verschieben und Ändern der Größe von Feldern](media/northwind-orders-canvas-part2/form-rearrange.gif)

    Weitere Informationen zum Anordnen von Feldern in einem Formular finden Sie Untergrund Legendes [zum Layout von Daten Formularen für Canvas-apps](working-with-form-layout.md).

## <a name="hide-time-controls"></a>Zeit Steuerelemente ausblenden

In diesem Beispiel benötigen Sie die Zeit Teile der Datumsfelder nicht, da diese Ebene der Granularität den Benutzer ablenken kann. Wenn Sie Sie löschen, können Sie Probleme in Formeln verursachen, die von diesen Steuerelementen abhängig sind, um Datumswerte zu aktualisieren oder die Position eines anderen Steuer Elements in der Datenkarte festzulegen. Stattdessen blenden Sie die Zeit Steuerelemente aus, indem Sie Ihre **sichtbare** Eigenschaft festlegen.

1. Wählen Sie im Struktur **Ansichts** Bereich die Datenkarte **Order Date** aus.

    Die Karte hat möglicherweise einen anderen Namen, Sie enthält jedoch das **Bestelldatum**.

1. Wenn Sie die UMSCHALTTASTE gedrückt halten, wählen Sie die Steuerelemente Stunde, Minute und Doppelpunkt Trennzeichen in der Datenkarte **Order Date** aus.

    > [!div class="mx-imgBorder"]
    > ![wählen Sie die Zeit Steuerelemente in der Order Date-Karte aus](media/northwind-orders-canvas-part2/form-09.png)

1. Legen Sie die **Visible** -Eigenschaft der Steuerelemente auf **false**fest.

    Alle ausgewählten Steuerelemente werden nicht mehr im folgenden Format angezeigt:

    > [!div class="mx-imgBorder"]
    > ![legen Sie die Visible-Eigenschaft auf false fest.](media/northwind-orders-canvas-part2/form-10.png)

1. Ändern Sie die Größe des Steuer Elements für die [**Datums**](controls/control-date-picker.md) Auswahl, um das Abschlussdatum anzuzeigen:

    > [!div class="mx-imgBorder"]
    > ![Ändern der Größe des Steuer Elements für die Datumsauswahl](media/northwind-orders-canvas-part2/form-11.png)

    Als nächstes wiederholen Sie die letzten Schritte für das Feld **bezahlte Datums** Angaben.

1. Wählen Sie im Struktur **Ansichts** Bereich die Zeit Steuerelemente in der Datenkarte " **Paid Date** " aus:

    > [!div class="mx-imgBorder"]
    > ![wählen Sie auf der kostenpflichtigen Datums Karte Zeitsteuerung aus](media/northwind-orders-canvas-part2/form-12.png)

1. Legen Sie die **Visible** -Eigenschaft der ausgewählten Steuerelemente auf **false**fest:

    > [!div class="mx-imgBorder"]
    > ![legen Sie die Visible-Eigenschaft auf false fest.](media/northwind-orders-canvas-part2/form-13.png)

1. Ändern Sie die Größe der Datumsauswahl in der Karte mit dem **bezahlten Datum** :

    > [!div class="mx-imgBorder"]
    > ![Ändern der Größe des Steuer Elements für die Datumsauswahl](media/northwind-orders-canvas-part2/form-14.png)

## <a name="connect-the-order-gallery"></a>Verbinden der Order Gallery

1. Reduzieren Sie im Struktur **Ansichts** Bereich das Formular, um den Namen des Order Gallery leichter zu finden, und benennen Sie ihn ggf. in **Gallery1**um.

1. Legen Sie die **Item** -Eigenschaft des Zusammenfassungs Formulars auf diesen Ausdruck fest:

    ```powerapps-dot
    Gallery1.Selected
    ```

    > [!div class="mx-imgBorder"]
    > ![Eigenschaft "Element festlegen" im Formular](media/northwind-orders-canvas-part2/form-15.png)

    Das Formular zeigt eine Zusammenfassung der Reihenfolge an, in der der App-Benutzer in der Liste ausgewählt wird.

    > [!div class="mx-imgBorder"]
    > ![wählen Sie eine Reihenfolge in der Liste aus, um die Übersicht in der Form anzuzeigen](media/northwind-orders-canvas-part2/form-select.gif)

## <a name="replace-a-data-card"></a>Ersetzen einer Datenkarte

Die **Bestellnummer ist ein Bezeichner** , der Common Data Service automatisch zugewiesen wird, wenn Sie einen Datensatz erstellen. Dieses Feld verfügt standardmäßig über ein [**Text Eingabe**](controls/control-text-input.md) -Steuerelement, aber Sie ersetzen es durch eine Bezeichnung, sodass der Benutzer dieses Feld nicht bearbeiten kann.

1. Wählen Sie das Formular aus, wählen Sie auf der Registerkarte **Eigenschaften** in der Nähe des rechten Rands die Option **Felder bearbeiten** , und wählen Sie dann das Feld **Bestellnummer**

    > [!div class="mx-imgBorder"]
    > ![wählen Sie das Feld Order Number aus](media/northwind-orders-canvas-part2/alt-01.png)

1. Öffnen Sie die Liste der **Steuerelement Typen** :

    > [!div class="mx-imgBorder"]
    > ![die Liste * * Steuerelement Typen * * öffnen](media/northwind-orders-canvas-part2/alt-02.png)

1. Wählen Sie die Karte **Text Daten anzeigen** aus:

    > [!div class="mx-imgBorder"]
    > Wählen Sie ![die Datenkarte * * Text anzeigen * * aus](media/northwind-orders-canvas-part2/alt-02b.png)

1. Schließen Sie den **Bereich Felder** .

    Der Benutzer kann die Bestellnummer nicht mehr ändern:

    > [!div class="mx-imgBorder"]
    > ![Bestellnummer ist schreibgeschützt](media/northwind-orders-canvas-part2/alt-03.png)

1. Ändern Sie auf der Registerkarte **Home** den Schrift Grad der Bestellnummer in 20 Punkte, damit das Feld leichter zu finden ist:

    > [!div class="mx-imgBorder"]
    > ![ändern Sie den Schrift Grad der Bestellnummer](media/northwind-orders-canvas-part2/alt-04.png)

## <a name="use-a-many-to-one-relationship"></a>Verwenden einer n:1-Beziehung

Die Entität " **Orders** " hat eine n:1-Beziehung mit der Entität " **Employees** ": jeder Mitarbeiter kann viele Aufträge erstellen, jede Bestellung kann jedoch nur einem Mitarbeiter zugewiesen werden. Wenn der Benutzer einen Mitarbeiter im Kombinations [**Feld**](controls/control-combo-box.md) -Steuerelement auswählt, stellt die **ausgewählte** Eigenschaft den gesamten Datensatz dieses Mitarbeiters **aus der Employee** -Entität bereit. Daher können Sie ein [**Image**](controls/control-image.md) -Steuerelement so konfigurieren, dass es das Bild eines beliebigen Mitarbeiters anzeigt, den der Benutzer im Kombinations Feld auswählt.

1. Wählen Sie die Datenkarte **Employee** :

    > [!div class="mx-imgBorder"]
    > ![wählen Sie die Datenkarte "Employee" aus](media/northwind-orders-canvas-part2/employee-01.png)

1. Entsperren Sie die Datenkarte auf der Registerkarte " **erweitert** " in der Nähe des rechten Rands, damit Sie Formeln bearbeiten können, die zuvor schreibgeschützt waren:

    > [!div class="mx-imgBorder"]
    > ![die Datenkarte "Employee" entsperren](media/northwind-orders-canvas-part2/employee-02.png)

1. Verringern Sie die Breite des Kombinations Felds in der Datenkarte, um Platz für das Mitarbeiter Bild zu schaffen:

    > [!div class="mx-imgBorder"]
    > ![ändern Sie die Größe des Kombinations Feld-Steuer Elements](media/northwind-orders-canvas-part2/employee-03b.png)

1. Wählen Sie auf der Registerkarte **Einfügen** die Option **Medien**  > **Abbild**aus:

    > [!div class="mx-imgBorder"]
    > ![ein Bild einfügen](media/northwind-orders-canvas-part2/employee-04.png)

    In der Datenkarte wird ein Bild angezeigt, das zu einer Anpassung erweitert wird:

    > [!div class="mx-imgBorder"]
    > ![Mitarbeiterdaten Karte mit Abbild-Steuerelement](media/northwind-orders-canvas-part2/employee-05.png)

1. Ändern Sie die Größe des Bilds, und verschieben Sie es rechts neben dem Kombinations Feld:

    > [!div class="mx-imgBorder"]
    > ![verschieben und Ändern der Größe des Image-Steuer Elements](media/northwind-orders-canvas-part2/employee-06.png)

1. Legen Sie die **Image** -Eigenschaft des Bilds auf diese Formel fest, und ersetzen Sie ggf. die Zahl am Ende von datacardvalue:

    ```powerapps-dot
    DataCardValue7.Selected.Picture
    ```

    > [!div class="mx-imgBorder"]
    > ![die Image-Eigenschaft des Bilds fest](media/northwind-orders-canvas-part2/employee-07.png)

    Das Bild des ausgewählten Mitarbeiters wird angezeigt.

1. Wenn Sie die Alt-Taste gedrückt halten, wählen Sie einen anderen Mitarbeiter im Kombinations Feld aus, um zu bestätigen, dass das Bild ebenfalls geändert wird.

    > [!div class="mx-imgBorder"]
    > ![wählen Sie einen Mitarbeiter aus, um das Bild dieses Mitarbeiters anzuzeigen](media/northwind-orders-canvas-part2/employee-select.gif)

## <a name="add-a-save-icon"></a>Symbol "Speichern" hinzufügen

1. Wählen Sie im Struktur **Ansichts** Bereich die Option **Screen1**aus, und klicken Sie dann auf  > **Symbole** **Einfügen**  > **überprüfen**:

    > [!div class="mx-imgBorder"]
    > ![Symbol für das Häkchen einfügen](media/northwind-orders-canvas-part2/save-01.png)

    Das [**Häkchensymbol**](controls/control-shapes-icons.md) wird standardmäßig in der oberen linken Ecke angezeigt, sodass das Symbol durch andere Steuerelemente schwer zu finden ist:

    > [!div class="mx-imgBorder"]
    > ![Symbol am Standard Speicherort](media/northwind-orders-canvas-part2/save-02.png)

1. Ändern Sie auf der Registerkarte **Start** die **Color** -Eigenschaft des Symbols in weiß, ändern Sie die Größe des Symbols, und verschieben Sie es am rechten Rand der Titelleiste:

    > [!div class="mx-imgBorder"]
    > ![die Farbe, die Größe und den Speicherort des Symbol "Speichern" Konfigurieren](media/northwind-orders-canvas-part2/save-03.png)

1. Vergewissern Sie sich im Struktur **Ansichts** Bereich, dass der Name des Formulars **Form1**lautet, und legen Sie dann die **onselect** -Eigenschaft des Symbols auf die folgende Formel fest:

    ```powerapps-dot
    SubmitForm( Form1 )
    ```

    > [!div class="mx-imgBorder"]
    > ![die onselect-Eigenschaft des Save-Symbols fest](media/northwind-orders-canvas-part2/save-04.png)

    Wenn der Benutzer das Symbol auswählt, sammelt die [**SubmitForm**](functions/function-form.md) -Funktion alle geänderten Werte im Formular und übermittelt Sie an die Datenquelle. Punkte werden am oberen Bildschirmrand angezeigt, während die Daten übermittelt werden, und der Order Gallery spiegelt die Änderungen nach dem Abschluss des Vorgangs wider.

1. Legen Sie die **Display Mode** -Eigenschaft des Symbols auf die folgende Formel fest:

    ```powerapps-dot
    If( Form1.Unsaved, DisplayMode.Edit, DisplayMode.Disabled )
    ```

    > [!div class="mx-imgBorder"]
    > ![die Display Mode-Eigenschaft des Symbols fest](media/northwind-orders-canvas-part2/save-05.png)

    Wenn alle Änderungen im Formular gespeichert wurden, wird das Symbol deaktiviert und in der **disabledcolor**angezeigt, die Sie als nächstes festlegen.

1. Legen Sie die **disabledcolor** -Eigenschaft des Symbols auf diesen Wert fest:

    ```powerapps-dot
    Gray
    ```

    > [!div class="mx-imgBorder"]
    > ![die disabledcolor-Eigenschaft des Symbols fest](media/northwind-orders-canvas-part2/save-06.png)

    Der Benutzer kann die Änderungen in einer Bestellung speichern, indem er das Häkchensymbol aktiviert, das dann deaktiviert und abgedimmt wird, bis der Benutzer eine weitere Änderung vornimmt:

    > [!div class="mx-imgBorder"]
    > ![Speichern von Änderungen](media/northwind-orders-canvas-part2/save-submit.gif)

## <a name="add-a-cancel-icon"></a>Symbol "Abbrechen" hinzufügen

1. Wählen Sie auf der Registerkarte **Einfügen** die Option **Symbole**  > **Abbrechen**aus:

    > [!div class="mx-imgBorder"]
    > ![Symbol "Abbrechen" hinzufügen](media/northwind-orders-canvas-part2/save-07.png)

    Das Symbol wird standardmäßig in der oberen linken Ecke angezeigt, wo andere Steuerelemente das Symbol möglicherweise schwer zu finden machen:

    > [!div class="mx-imgBorder"]
    > ![Abbrechen-Symbol am Standard Speicherort](media/northwind-orders-canvas-part2/save-08.png)

1. Ändern Sie auf der Registerkarte **Startseite** die **Color** -Eigenschaft des Symbols in weiß, ändern Sie die Größe des Symbols, und verschieben Sie es links neben das Häkchensymbol:

    > [!div class="mx-imgBorder"]
    > ![ändern Sie die Farbe, die Größe und den Speicherort des Abbrechen-Symbols](media/northwind-orders-canvas-part2/save-09.png)

1. Legen **Sie die onselect** -Eigenschaft des Cancel-Symbols auf die folgende Formel fest:

    ```powerapps-dot
    ResetForm( Form1 )
    ```

    > [!div class="mx-imgBorder"]
    > ![die onselect-Eigenschaft des Cancel-Symbols fest](media/northwind-orders-canvas-part2/save-10.png)

    Die [**resetform-Funktion verwirft**](functions/function-form.md) alle Änderungen im Formular, die den ursprünglichen Zustand zurückgeben.

1. Legen Sie die **Display Mode** -Eigenschaft des Cancel-Symbols auf die folgende Formel fest:

    ```powerapps-dot
    If( Form1.Unsaved Or Form1.Mode = FormMode.New, DisplayMode.Edit, DisplayMode.Disabled )
    ```

    > [!div class="mx-imgBorder"]
    > ![die Display Mode-Eigenschaft des Cancel-Symbols fest](media/northwind-orders-canvas-part2/save-11.png)

    Diese Formel unterscheidet sich geringfügig von der eines für das Häkchensymbol. Das Symbol Abbrechen ist deaktiviert, wenn alle Änderungen gespeichert wurden oder sich das Formular im **neuen** Modus befindet, den Sie als nächstes aktivieren. In diesem Fall **verwirft resetform** den neuen Datensatz.

1. Legen Sie die **disabledcolor** -Eigenschaft des Cancel-Symbols auf diesen Wert fest:

    ```powerapps-dot
    Gray
    ```

    > [!div class="mx-imgBorder"]
    > ![die disabledcolor-Eigenschaft des Cancel-Symbols fest](media/northwind-orders-canvas-part2/save-12.png)

    Der Benutzer kann Änderungen an einer Bestellung abbrechen, und die Symbole zum Überprüfen und Abbrechen werden deaktiviert und abgeraten, wenn alle Änderungen gespeichert wurden:

    > [!div class="mx-imgBorder"]
    > ![speichern und Abbrechen von Änderungen](media/northwind-orders-canvas-part2/save-cancel.gif)

## <a name="add-an-add-icon"></a>Hinzufügen eines Symbols

1. Wählen Sie auf der Registerkarte **Einfügen** die Option **Symbole**  > **Hinzufügen**aus.

    > [!div class="mx-imgBorder"]
    > ![das Symbol "hinzufügen" hinzufügen](media/northwind-orders-canvas-part2/save-13.png)

    Das Symbol " **Hinzufügen** " wird standardmäßig in der oberen linken Ecke angezeigt, sodass es bei anderen Steuerelementen möglicherweise schwierig zu finden ist:

    > [!div class="mx-imgBorder"]
    > ![Standard Speicherort für das Symbol "hinzufügen"](media/northwind-orders-canvas-part2/save-14.png)

1. Legen Sie auf der Registerkarte **Start** die **Color** -Eigenschaft des Symbols hinzufügen auf weiß fest, ändern Sie die Größe des Symbols, und verschieben Sie es links neben das Symbol Abbrechen:

    > [!div class="mx-imgBorder"]
    > ![ändern Sie die Farbe, die Größe und den Speicherort des Add-Symbols](media/northwind-orders-canvas-part2/save-15.png)

1. Legen Sie die **onselect** -Eigenschaft des Add-Symbols auf die folgende Formel fest:

    ```powerapps-dot
    NewForm( Form1 )
    ```

    > [!div class="mx-imgBorder"]
    > ![die onselect-Eigenschaft des Add-Symbols fest](media/northwind-orders-canvas-part2/save-15b.png)

    Die [**NewForm**](functions/function-form.md) -Funktion zeigt einen leeren Datensatz im Formular an.  

1. Legen Sie die **Display Mode** -Eigenschaft des Add-Symbols auf die folgende Formel fest:

    ```powerapps-dot
    If( Form1.Unsaved Or Form1.Mode = FormMode.New, DisplayMode.Disabled, DisplayMode.Edit )
    ```

    > [!div class="mx-imgBorder"]
    > ![die Display Mode-Eigenschaft des Add-Symbols fest](media/northwind-orders-canvas-part2/save-16.png)

    Die Formel deaktiviert das Symbol "hinzufügen" unter folgenden Bedingungen:

    - Der Benutzer nimmt Änderungen vor, speichert oder storniert Sie jedoch nicht, was das Gegenteil von den Symbolen zum Überprüfen und Abbrechen ist.
    - Der Benutzer wählt das Symbol zum Hinzufügen aus, nimmt aber keine Änderungen vor.

1. Legen Sie die **disabledcolor** -Eigenschaft des Add-Symbols auf diesen Wert fest:

    ```powerapps-dot
    Gray
    ```

    > [!div class="mx-imgBorder"]
    > ![die disabledcolor-Eigenschaft des Add-Symbols festlegen](media/northwind-orders-canvas-part2/save-17.png)

    Der Benutzer kann eine Bestellung erstellen, wenn er keine Änderungen vornimmt, oder alle vorgenommenen Änderungen speichern oder Abbrechen. (Wenn der Benutzer dieses Symbol auswählt, kann er es erst wieder auswählen, wenn eine oder mehrere Änderungen vorgenommen und diese Änderungen gespeichert oder abgebrochen werden):

    > [!div class="mx-imgBorder"]
    > ![erstellen Sie eine Bestellung](media/northwind-orders-canvas-part2/save-new.gif)

> [!NOTE]
> Wenn Sie eine Bestellung erstellen und speichern, müssen Sie möglicherweise im Order Gallery einen Bildlauf nach unten durchführen, um die neue Bestellung anzuzeigen. Es hat keinen Gesamtpreis, da Sie noch keine Bestelldetails hinzugefügt haben.

## <a name="add-a-trash-icon"></a>Hinzufügen eines Papierkorb Symbols

1. Wählen Sie auf der Registerkarte **Einfügen** die Option **Symbole**  > **Papierkorb**aus.

    > [!div class="mx-imgBorder"]
    > ![ein Papierkorb Symbol einfügen](media/northwind-orders-canvas-part2/save-18.png)

    Standardmäßig wird das **Papierkorb** Symbol in der oberen linken Ecke angezeigt, in dem andere Steuerelemente das Auffinden erschweren können:

    > [!div class="mx-imgBorder"]
    > ![Standard Speicherort des Papierkorb Symbols](media/northwind-orders-canvas-part2/save-19.png)

1. Ändern Sie auf der Registerkarte **Startseite** die **Color** -Eigenschaft des Papierkorb Symbols in weiß, ändern Sie die Größe des Symbols, und verschieben Sie es links neben das Symbol "hinzufügen":

    > [!div class="mx-imgBorder"]
    > ![ändern Sie die Farbe, die Größe und den Speicherort des Papierkorb Symbols](media/northwind-orders-canvas-part2/save-20.png)

1. Legen **Sie die onselect** -Eigenschaft des Papierkorb Symbols auf die folgende Formel fest:

    ```powerapps-dot
    Remove( Orders, Gallery1.Selected )
    ```

    > [!div class="mx-imgBorder"]
    > ![legen Sie die onselect-Eigenschaft des Papierkorb Symbols fest](media/northwind-orders-canvas-part2/save-21.png)

    Die [**Remove**](functions/function-remove-removeif.md) -Funktion entfernt einen Datensatz aus einer Datenquelle. In dieser Formel entfernt die Funktion den Datensatz, der in der Order Gallery ausgewählt ist. Das Papierkorb Symbol wird in der Nähe des Zusammenfassungs Formulars (nicht der Order Gallery) angezeigt, weil das Formular weitere Details zum Datensatz anzeigt, sodass der Benutzer den Datensatz leichter identifizieren kann, den die Formel löscht.

1. Legen Sie die **Display Mode** -Eigenschaft für das Papierkorb Symbol auf diese Formel fest:

    ```powerapps-dot
    If( Form1.Mode = FormMode.New, DisplayMode.Disabled, DisplayMode.Edit )
    ```

    > [!div class="mx-imgBorder"]
    > ![die Display Mode-Eigenschaft des Papierkorb Symbols fest](media/northwind-orders-canvas-part2/save-22.png)

    Mit dieser Formel wird das Papierkorb Symbol deaktiviert, wenn der Benutzer einen Datensatz erstellt. Bis der Benutzer den Datensatz speichert, hat die **Remove** -Funktion keinen zu löschenden Datensatz.

1. Legen Sie die **disabledcolor** -Eigenschaft des Papierkorb Symbols auf diesen Wert fest:

    ```powerapps-dot
    Gray
    ```

    > [!div class="mx-imgBorder"]
    > ![die disabledcolor-Eigenschaft des Papierkorb Symbols fest](media/northwind-orders-canvas-part2/save-23.png)

    Der Benutzer kann eine Bestellung löschen.

    > [!div class="mx-imgBorder"]
    > ![Löschen von Bestellungen](media/northwind-orders-canvas-part2/save-delete.gif)

## <a name="summary"></a>FAS

Zur Wiederholung haben Sie ein Formular hinzugefügt, in dem der Benutzer eine Zusammenfassung der einzelnen Reihenfolge anzeigen und bearbeiten kann, und Sie haben die folgenden Elemente verwendet:

- Ein Formular, das Daten aus der **Orders** -Entität anzeigt: **Form1. DataSource =** `Orders`
- Eine Verbindung zwischen dem Formular und der Order Gallery: **Form1. Item =** `Gallery1.Selected`
- Ein alternatives Steuerelement für das Feld " **Order Number** ": **Text anzeigen**
- Eine n:1-Beziehung, um das Bild des Mitarbeiters in der **Employee** Data Card anzuzeigen: `DataCardValue1.Selected.Picture`
- Ein Symbol zum Speichern von Änderungen in einer Bestellung: `SubmitForm( Form1 )`
- Ein Symbol zum Abbrechen von Änderungen an einer Bestellung: `ResetForm( Form1 )`
- Ein Symbol zum Erstellen einer Bestellung: `NewForm( Form1 )`
- Ein Symbol zum Löschen einer Bestellung: `Remove( Orders, Gallery1.Selected )`

## <a name="next-step"></a>Nächster Schritt

Im nächsten Thema fügen Sie einen weiteren Katalog hinzu, um die Produkte in jeder Bestellung anzuzeigen, und Sie ändern diese Details mithilfe der [**Patch**](functions/function-patch.md) -Funktion.

> [!div class="nextstepaction"]
> [Erstellen der Detail Galerie](northwind-orders-canvas-part3.md)
