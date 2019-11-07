---
title: Erstellen einer Order Gallery in einer Canvas-App | Microsoft-Dokumentation
description: Erstellen einer Order Gallery in einer Canvas-App zum Verwalten von Daten für Northwind Traders
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
ms.openlocfilehash: bbc6111800a817ecb71eec60fdba1d2dabd6c698
ms.sourcegitcommit: 32542f1d17fee757dcdaf9c247f4051f59b86434
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "73741503"
---
# <a name="create-an-order-gallery-in-a-canvas-app"></a>Erstellen einer Order Gallery in einer Canvas-App

Befolgen Sie die Schritt-für-Schritt-Anleitungen zum Erstellen einer Order Gallery in einer Canvas-App zum Verwalten von fiktiven Daten in der Datenbank Northwind Traders. Dieses Thema ist Teil einer Reihe, in der erläutert wird, wie eine Geschäfts-App für relationale Daten in Common Data Service erstellt wird. Um optimale Ergebnisse zu erzielen, sollten Sie sich diese Themen in dieser Sequenz ansehen:

1. Erstellen Sie eine Bestell Galerie (**dieses Thema**).
1. [Erstellen Sie ein Zusammenfassungs Formular](northwind-orders-canvas-part2.md).
1. [Erstellen Sie eine Detail Galerie](northwind-orders-canvas-part3.md).

> [!div class="mx-imgBorder"]
> ![Definition der Bildschirmbereiche](media/northwind-orders-canvas-part1/orders-parts.png)

## <a name="prerequisites"></a>Voraussetzungen

- [Installieren Sie die Datenbank Northwind Traders und die apps](northwind-install.md).
- Lesen Sie die [Übersicht über die Canvas-App](northwind-orders-canvas-overview.md) für Northwind Traders.

## <a name="create-a-blank-app"></a>Erstellen einer leeren App

1. [Melden Sie sich bei powerapps an](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), und erstellen Sie dann eine leere Tablet-app.

    > [!div class="mx-imgBorder"]
    > ![Canvas-App aus einer leeren Kachel](media/northwind-orders-canvas-part1/start-01.png)

1. Benennen Sie Ihre APP, und wählen Sie dann **Erstellen**aus.

    > [!div class="mx-imgBorder"]
    > ![Canvas-App aus einem leeren Dialogfeld](media/northwind-orders-canvas-part1/start-02.png)

    PowerApps Studio wird geöffnet, damit Sie Ihrer APP Datenquellen und Steuerelemente hinzufügen können:

    > [!div class="mx-imgBorder"]
    > ![PowerApps Studio](media/northwind-orders-canvas-part1/start-03.png)

## <a name="add-the-data"></a>Hinzufügen der Daten

1. Wählen Sie auf der Registerkarte **Ansicht** die Option **Datenquellen**:

    > [!div class="mx-imgBorder"]
    > Wählen Sie ![Sicht, Datenquellen, Datenquelle hinzufügen aus](media/northwind-orders-canvas-part1/datasource-01.png)

1. Geben Sie **Orders** in das Suchfeld ein:

    > [!div class="mx-imgBorder"]
    > ![Liste der Verbindungen](media/northwind-orders-canvas-part1/datasource-02.png)

1. Wählen Sie die Datenquelle **Orders** aus, die in Ihrer APP verwendet werden soll:

    > [!div class="mx-imgBorder"]
    > ![Liste der Entitäten](media/northwind-orders-canvas-part1/datasource-03.png)

    Die **Orders** -Entität enthält viele Felder verschiedener Typen:

    > [!div class="mx-imgBorder"]
    > ![Liste der Felder in der Entität "Orders"](media/northwind-orders-canvas-part1/datasource-05.png)

    Jedes Feld verfügt über einen **anzeigen Amen** und einen **Namen**, der manchmal als logischer Name bezeichnet wird. Beide Namen verweisen auf dasselbe. Im Allgemeinen verwenden Sie den anzeigen Amen, wenn Sie eine APP erstellen, aber einige Fälle erfordern den eher kryptischen **Namen**, wie in einer Prozedur beschrieben.

1. Wenn Sie mit Bildschirmen und Steuerelementen weiter arbeiten, klicken Sie in PowerApps Studio auf der linken Seite auf die Struktur **Ansicht** zurück, indem Sie das Symbol mit den drei gestapelten Quadraten drücken. Sie können jederzeit zu den **Datenquellen** zurückkehren, indem Sie das Zylinder Symbol drücken.

## <a name="create-the-order-gallery"></a>Erstellen der Order Gallery

1. **Wählen Sie** auf der Registerkarte **Einfügen** die Option Katalog  > **leerer vertikal** aus, [**um ein Katalog**](controls/control-gallery.md) -Steuerelement hinzuzufügen, das die Aufträge anzeigt.

    > [!div class="mx-imgBorder"]
    > ![INSERT, Gallery, leeres vertikales](media/northwind-orders-canvas-part1/orders-01.png)

    Das Steuerelement wird in den Zeichenbereich eingefügt, und es wird ein auslaufendem Dialogfeld mit der Frage angezeigt, mit welcher Datenquelle eine Verbindung hergestellt wird  


    > [!div class="mx-imgBorder"]
    > ![Eigenschaft "Elemente festlegen" der Galerie](media/northwind-orders-canvas-part1/orders-02.png)

1. Wir könnten es hier direkt mit **Aufträgen** verbinden, aber stattdessen möchten wir die Sortierreihenfolge des Katalogs steuern.  Ignorieren Sie das Dialogfeld "ausführen", und legen Sie in der Bearbeitungs Leiste die **Items** -Eigenschaft des Katalogs auf die folgende Formel fest:

    ```powerapps-dot
    Sort( Orders, 'Order Number', Descending )
    ```

    Die [**Sortier**](functions/function-sort.md) Funktion ordnet die Liste so an, dass die neueste Bestellung (mit der höchsten Bestellnummer) zuerst angezeigt wird.

    > [!div class="mx-imgBorder"]
    > ![Eigenschaft "Elemente festlegen" der Galerie](media/northwind-orders-canvas-part1/orders-02b.png)

1. Nach einigen Augenblicken wird die Ergebnis Ansicht unterhalb der Bearbeitungs Leiste angezeigt.  Ziehen Sie den Pfeil auf der linken Seite nach unten, um das Ergebnis der Formel anzuzeigen.  Scrollen Sie nach rechts, um die Spalte **Order Number** anzuzeigen, und stellen Sie sicher, dass Sie wie gewünscht (höchste bis niedrigste) sortiert ist.  

    > [!div class="mx-imgBorder"]
    > ![Eigenschaft "Elemente festlegen" der Galerie](media/northwind-orders-canvas-part1/orders-02c.png)

1. Öffnen Sie auf der Registerkarte **Eigenschaften** in der Nähe des rechten Rands die **Layoutliste** :

    > [!div class="mx-imgBorder"]
    > ![Liste der Layoutoptionen](media/northwind-orders-canvas-part1/orders-03.png)

1. Wählen Sie in der Liste der Optionen **Titel und Untertitel**aus:

    > [!div class="mx-imgBorder"]
    > ![wählen Sie ein Layout aus](media/northwind-orders-canvas-part1/orders-04.png)

    In der Vorlage des Katalogs werden zwei [**Label**](controls/control-text-box.md) -Steuerelemente hinzugefügt. Standardmäßig zeigen diese Steuerelemente zwei Spalten der **Orders** -Entität an, die Sie als nächstes ändern werden. Die Vorlage des Katalogs wird für jeden Datensatz in der Entität vertikal repliziert.

1. Wählen Sie auf der Registerkarte **Eigenschaften** in der Nähe des rechten Rands die Option **Bearbeiten** (neben **Felder**).

    > [!div class="mx-imgBorder"]
    > ![wählen Sie ein Layout aus](media/northwind-orders-canvas-part1/orders-04b.png)

1. Wählen Sie im Bereich **Daten** die Option **Title1** (oder wählen Sie in der Vorlage des Katalogs die obere Bezeichnung aus).

1. Legen Sie in der Bearbeitungs Leiste die **Text** -Eigenschaft der Bezeichnung auf den folgenden Ausdruck fest:

    ```powerapps-dot
    "Order " & ThisItem.'Order Number'
    ```

    > [!div class="mx-imgBorder"]
    > ![die Text-Eigenschaft der Titel Bezeichnung fest](media/northwind-orders-canvas-part1/orders-06.png)

    Die Bestellnummer wird oben in jedem Galerie Element angezeigt. In der Galerie Vorlage gewährt **thisitem** Zugriff auf alle Felder in der Entität **Order** .

1. Wählen Sie im Bereich **Daten** die Option **Subtitle1** (oder wählen Sie in der Vorlage des Katalogs die untere Bezeichnung aus):

    > [!div class="mx-imgBorder"]
    > ![wählen Sie Untertitel Bezeichnung aus](media/northwind-orders-canvas-part1/orders-07.png)

1. Legen Sie in der Bearbeitungs Leiste die **Text** -Eigenschaft der Bezeichnung auf den folgenden Ausdruck fest:

    ```powerapps-dot
    ThisItem.Customer.Company
    ```

    > [!div class="mx-imgBorder"]
    > die Text-Eigenschaft der Untertitel Bezeichnung ![fest](media/northwind-orders-canvas-part1/orders-08.png)

    Nachdem Sie diese Formel eingegeben haben, kann ein roter Wellenlinien Fehler für einen Moment angezeigt werden. Der Fehler sollte eindeutig sein, wenn Sie etwas außerhalb der Bearbeitungs Leiste auswählen und dann den Cursor an die Bearbeitungs Leiste zurückgeben. Wenn der Fehler weiterhin auftritt oder kein Wert angezeigt wird, klicken Sie auf die Registerkarte **Ansicht** , wählen Sie **Datenquellen**aus, und aktualisieren Sie dann die Entität **Orders** , indem Sie die Auslassungs Punkte (...) rechts neben dem Namen der Datenquelle auswählen.

    Wenn Sie **thisitem. Customer**angeben, nutzen Sie eine n:1-Beziehung zwischen den Entitäten Orders und **Customers** , und rufen Sie den Kundendaten Satz ab, der mit den einzelnen **Aufträgen** verknüpft ist. Aus dem Kundendaten Satz extrahieren Sie Daten in der Spalte **Company** , um Sie anzuzeigen.

    Sie können alle Beziehungen der **Orders** -Entität zu anderen Entitäten, einschließlich der **Customer** -Entität, anzeigen:

    > [!div class="mx-imgBorder"]
    > ![Liste der Beziehungen](media/northwind-orders-canvas-part1/orders-09.png)

1. Schließen Sie den Bereich **Daten** , indem Sie in der oberen rechten Ecke das Symbol zum Schließen (x) auswählen.

## <a name="show-each-orders-status"></a>Status der einzelnen Bestellungen anzeigen

In diesem Verfahren fügen Sie Speicherplatz im Katalog für eine Bezeichnung hinzu und konfigurieren ihn so, dass er den Status jeder Bestellung in einer anderen Farbe auf der Grundlage der Daten anzeigt.

1. Reduzieren Sie in der Vorlage des Katalogs die Breite der ersten Bezeichnung **Title1**:

    > [!div class="mx-imgBorder"]
    > ![Title1 in der Galerie Vorlage](media/northwind-orders-canvas-part1/status-01.png)

1. Wiederholen Sie den vorherigen Schritt mit der zweiten Bezeichnung **Subtitle1**:

    > [!div class="mx-imgBorder"]
    > ![Subtitle1 in der Galerie Vorlage](media/northwind-orders-canvas-part1/status-02.png)

1. Wählen Sie mit ausgewählter Katalog Vorlage (oder einem Steuerelement in der Vorlage) auf der Registerkarte **Einfügen** die Option **Bezeichnung** aus:

    > [!div class="mx-imgBorder"]
    > ![eine Bezeichnung hinzufügen](media/northwind-orders-canvas-part1/status-03.png)

1. Verschieben Sie die neue Bezeichnung rechts neben der Bezeichnung **Title1** :

    > [!div class="mx-imgBorder"]
    > ![eine Bezeichnung verschieben und die Größe der Bezeichnung ändern](media/northwind-orders-canvas-part1/status-04.png)

1. Legen Sie die **Text** -Eigenschaft der neuen Bezeichnung auf diesen Ausdruck fest:

    ```powerapps-dot
    ThisItem.'Order Status'
    ```

    > [!div class="mx-imgBorder"]
    > ![legen Sie die Text-Eigenschaft fest](media/northwind-orders-canvas-part1/status-05.png)

    In der Entität **Orders** enthält das Feld **Bestellstatus** einen Wert aus der Option **Auftrags** Status. Ein Options Satz ähnelt einer Enumeration in anderen Programmier Tools. Jeder Satz von Optionen wird in der Datenbank definiert, sodass Benutzer nur die Optionen angeben können, die in der Gruppe vorliegen. Die Option **Auftrags Status** ist auch global und nicht lokal, sodass Sie Sie in anderen Entitäten verwenden können:

    > [!div class="mx-imgBorder"]
    > ![Auftrags Status-Option festgelegt](media/northwind-orders-canvas-part1/status-06.png)

    Jede Option in einem Satz weist einen Namen auf, der angezeigt wird, wenn Sie ihn in einer Bezeichnung anzeigen. Diese Namen können lokalisiert werden, und die APP erkennt dieselbe Option, unabhängig davon, ob ein englischsprachiger Benutzer **Apple**auswählt, ein französischer Benutzer die **Pomme**auswählt oder ein spanischer Benutzer **Manzana**auswählt. Aus diesem Grund ist es nicht möglich, eine Formel zu erstellen, die eine hart codierte Zeichenfolge für eine Option stützt, wie in diesem Thema später veranschaulicht wird.

    In Formeln müssen Sie den **Order-Status** in einfache Anführungszeichen einschließen, da er ein Leerzeichen enthält. Dieser Name funktioniert jedoch genauso wie jeder andere Name in powerapps, wie z. b. **Kunden** oder **Firmen**.

1. Vergrößern Sie auf der Registerkarte **Home** den Schrift Grad der Status Bezeichnung auf 20 Punkte, und richten Sie den Text rechtsbündig aus:

    > [!div class="mx-imgBorder"]
    > ![Ändern der Schriftgröße und der Ausrichtung](media/northwind-orders-canvas-part1/status-07.png)

1. Legen Sie in der Bearbeitungs Leiste die **Color** -Eigenschaft der Status Bezeichnung auf diese Formel fest:

    ```powerapps-dot
    Switch( ThisItem.'Order Status',
        'Orders Status'.Closed, Green,
        'Orders Status'.New, Black,
        'Orders Status'.Invoiced, Blue,
        'Orders Status'.Shipped, Purple
    )
    ```

    > [!div class="mx-imgBorder"]
    > ![legen Sie die Color-Eigenschaft der Status Bezeichnung fest](media/northwind-orders-canvas-part1/status-08.png)

    Powerapps hindert Sie daran, eine Formel zu erstellen, die für jede Option in einer Menge eine hart codierte Zeichenfolge zurückgibt, da solche Formeln zu unpassenden Ergebnissen führen können, wenn die Optionsnamen lokalisiert werden. Stattdessen bestimmt die **Switch** -Funktion die Farbe basierend auf der Zeichenfolge, die in der Bezeichnung basierend auf den Einstellungen des Benutzers angezeigt wird.

    Wenn diese Formel vorhanden ist, werden unterschiedliche Statuswerte in anderen Farben angezeigt, wie in der vorherigen Abbildung gezeigt.

## <a name="display-each-orders-total"></a>Anzeigen der Gesamtsumme der Bestellung

1. Wählen Sie das erste Element im Katalog aus, bei dem es sich um die Vorlage des Katalogs handelt:

    > [!div class="mx-imgBorder"]
    > ![wählen Sie die Katalog Vorlage aus](media/northwind-orders-canvas-part1/aggregate-01.png)

1. Wählen Sie auf der Registerkarte **Einfügen** die **Bezeichnung Bezeichnung** , um eine weitere Bezeichnung hinzuzufügen:

    > [!div class="mx-imgBorder"]
    > ![eine Bezeichnung hinzufügen](media/northwind-orders-canvas-part1/aggregate-02.png)

1. Verschieben Sie die neue Bezeichnung, sodass Sie unter der Status Bezeichnung angezeigt wird:

    > [!div class="mx-imgBorder"]
    > ![ändern Sie die Größe, und verschieben Sie die neue Bezeichnung](media/northwind-orders-canvas-part1/aggregate-03.png)

1. Legen Sie in der Bearbeitungs Leiste die **Text** -Eigenschaft der neuen Bezeichnung auf diese Formel fest:

    ```powerapps-dot
    Text( Sum( ThisItem.'Order Details', Quantity * 'Unit Price' ), "[$-en-US]$ #,###.00" )
    ```

    > [!div class="mx-imgBorder"]
    > ![Formel zum Berechnen der Gesamtkosten der Bestellung](media/northwind-orders-canvas-part1/aggregate-04.png)

    In dieser Formel fügt die [**Sum**](functions/function-aggregates.md) -Funktion die Datensätze in der **Order Details** -Entität hinzu, die mit jedem Datensatz in der **Order** -Entität über eine 1: n-Beziehung verknüpft sind. Diese Zeilen Elemente bilden jede Bestellung, und Sie verwenden die gleiche 1: n-Beziehung, um die Zeilen Elemente im unteren rechten Bereich des Bildschirms anzuzeigen und zu bearbeiten.

    Diese Formel zeigt eine blaue Unterstreichung und eine [Delegierungs Warnung](delegation-overview.md) an, da Common Data Service die Delegierung komplexer Aggregatfunktionen (z. b. die Summe einer Multiplikation) nicht unterstützt. Diese Informationen können ignoriert werden, da in diesem Beispiel keine Reihenfolge mehr als 500 Zeilen Elemente enthalten. Wenn dies für eine andere APP erforderlich ist, können Sie diesen Grenzwert in den **App-Einstellungen**erhöhen.

    Die [**Text**](functions/function-text.md) -Funktion in dieser Formel fügt ein Währungssymbol hinzu und formatiert das Ergebnis mit Tausenden und Dezimaltrennzeichen. Wie bereits geschrieben, enthält die Formel das Sprachtag für US-Englisch (**[$-en-US]**) und ein Dollarsymbol (**$**). Wenn Sie das Sprachtag entfernen, wird es basierend auf den Spracheinstellungen durch eins ersetzt, und in der Bezeichnung werden die entsprechenden Formate für dieses Tag angezeigt. Wenn Sie das Dollarsymbol verlassen, wird in der Bezeichnung basierend auf den Einstellungen des Benutzers das entsprechende Währungssymbol angezeigt. Sie können jedoch erzwingen, dass ein anderes Symbol angezeigt wird, indem Sie das Dollarsymbol durch das gewünschte Dollarsymbol ersetzen.

1. Ändern Sie auf der Registerkarte **Home** den Schrift Grad der neuesten Bezeichnung in 20 Punkte, und richten Sie den Text rechtsbündig aus:

    > [!div class="mx-imgBorder"]
    > ![Ändern des Schrift Grads und der Ausrichtung einer Bezeichnung](media/northwind-orders-canvas-part1/aggregate-05.png)

1. Verschieben Sie den Katalog an den linken Rand des Bildschirms, und verringern Sie die Breite des Katalogs, um Speicherplatz zu schließen.

1. Vergrößern Sie die Höhe des Katalogs, sodass diese fast so groß wie der Bildschirm ist, aber lassen Sie für eine Titelleiste, die Sie am Anfang des nächsten Themas hinzufügen, einen kleinen Raum, den Sie hinzufügen:

    > [!div class="mx-imgBorder"]
    > ![verschieben und Ändern der Größe des Katalogs](media/northwind-orders-canvas-part1/aggregate-06.png)

## <a name="summary"></a>FAS

Zur Wiederholung haben Sie begonnen, eine Canvas-App mit einem Bildschirm zu erstellen, indem Sie die Order Gallery hinzufügen, die die folgenden Elemente enthält:

- Ein Ausdruck, mit dem die Bestellnummer angezeigt wird: `"Orders " & ThisItem.OrderNumber`
- Ein Feld in einer n:1-Beziehung: `ThisItem.Customer.Company`
- Eine Bezeichnung, die den Namen einer Option in einer Menge anzeigt: `ThisItem.'Order Status'`
- Eine Bezeichnung, die das Format ändert, je nachdem, welche Option in einer Menge die Bezeichnung anzeigt: `Switch( ThisItem.'Order Status', 'Orders Status'.Closed, Green, ...`
- Eine komplexe Aggregatfunktion über eine 1: n-Beziehung: `Sum( ThisItem.'Order Details', Quantity * 'Unit Price' )`

## <a name="next-topic"></a>Nächstes Thema

Im nächsten Thema fügen Sie ein [**Formular bearbeiten**](controls/control-form-detail.md) -Steuerelement hinzu, um eine Zusammenfassung der vom Benutzer im soeben erstellten Katalog ausgewählten Reihenfolge anzuzeigen und zu bearbeiten.

> [!div class="nextstepaction"]
> [Erstellen des Zusammenfassungs Formulars](northwind-orders-canvas-part2.md)
