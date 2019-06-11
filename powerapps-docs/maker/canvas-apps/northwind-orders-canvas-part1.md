---
title: Erstellen Sie einen Order-Katalog in einer Canvas-app | Microsoft-Dokumentation
description: Erstellen eines Order-Katalogs in einer Canvas-app, um Daten für Northwind Traders zu verwalten.
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
ms.openlocfilehash: 94d6c104cb888bb13f3724231d7891d622f5377b
ms.sourcegitcommit: e85072f7a80da308c4caabe20adbf2509588ca57
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66761003"
ms.PowerAppsDecimalTransform: true
---
# <a name="create-an-order-gallery-in-a-canvas-app"></a>Erstellen Sie einen Order-Katalog in einer Canvas-app

Führen Sie schrittweise Anweisungen zum Erstellen eines Katalogs Reihenfolge in einer Canvas-app für die Verwaltung von fiktiven Daten in der Datenbank Northwind Traders ein. Dieses Thema ist Teil einer Reihe, die erklärt, wie Sie eine Geschäfts-app auf relationalen Daten in Common Data Service zu erstellen. Erkunden Sie diese Themen in dieser Sequenz, für optimale Ergebnisse:

1. Erstellen eines Katalogs Reihenfolge (**in diesem Thema**).
1. [Erstellen Sie eine Zusammenfassung Formular](northwind-orders-canvas-part2.md).
1. [Erstellen Sie einen Katalog Detail](northwind-orders-canvas-part3.md).

> [!div class="mx-imgBorder"]
> ![Definition der Bildschirmbereiche](media/northwind-orders-canvas-part1/orders-parts.png)

## <a name="prerequisites"></a>Voraussetzungen

- [Installieren Sie die Datenbank Northwind Traders und apps](northwind-install.md).
- Lesen Sie die [Überblick über die Canvas-app](northwind-orders-canvas-overview.md) für Northwind Traders.

## <a name="create-a-blank-app"></a>Erstellen einer leeren App

1. [Melden Sie sich bei PowerApps](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), und klicken Sie dann eine leere Tablet-app zu erstellen.

    > [!div class="mx-imgBorder"]
    > ![Canvas-app aus leere Kachel](media/northwind-orders-canvas-part1/start-01.png)

1. Benennen Sie Ihre app den, Sie, und wählen Sie dann **erstellen**.

    > [!div class="mx-imgBorder"]
    > ![Canvas-app aus leer (Dialogfeld)](media/northwind-orders-canvas-part1/start-02.png)

    PowerApps Studio wird geöffnet, sodass Sie Datenquellen und Steuerelementen zu Ihrer app hinzufügen können:

    > [!div class="mx-imgBorder"]
    > ![PowerApps Studio](media/northwind-orders-canvas-part1/start-03.png)

1. Aktivieren einer [experimentelles Feature](working-with-experimental.md) für und das Ergebnis einer Formel direkt über die Bearbeitungsleiste ein.

    1. Auf der **Datei** , wählen Sie im Menü **Anwendungseinstellungen**, und wählen Sie dann **Erweiterte Einstellungen**.
    1. Führen Sie einen Bildlauf zum unteren Rand der Liste der Features, und klicken Sie dann aktivieren **aktivieren Bearbeitungsleiste Ergebnisansicht**:

        > [!div class="mx-imgBorder"]
        > ![Liste der experimentelle features](media/northwind-orders-canvas-part1/start-04.png)

1. Wählen Sie in der oberen linken Ecke den Pfeil, um zu den leeren Zeichenbereich zurückzukehren.

## <a name="add-the-data"></a>Fügen Sie die Daten

1. Auf der **Ansicht** Registerkarte **Datenquellen**, und wählen Sie dann **Datenquelle hinzufügen** in die **Daten** Bereich:

    > [!div class="mx-imgBorder"]
    > ![Wählen Sie die Ansicht, Datenquellen, Datenquelle hinzufügen](media/northwind-orders-canvas-part1/datasource-01.png)

1. Wählen Sie **Common Data Service**.

    Wenn **Common Data Service** nicht angezeigt, in der Liste der Verbindungen wählen **neue Verbindung**, und fügen Sie es.

    > [!div class="mx-imgBorder"]
    > ![Liste der Verbindungen](media/northwind-orders-canvas-part1/datasource-02.png)

1. Unter **Entität auswählen**, Typ **Bestellungen**, wählen die **Bestellungen** Kontrollkästchen, und wählen Sie dann **Connect**:

    > [!div class="mx-imgBorder"]
    > ![Liste der Entitäten](media/northwind-orders-canvas-part1/datasource-03.png)

    Sie hinzugefügt haben die **Bestellungen** -Datenquelle, die Ihre app:

    > [!div class="mx-imgBorder"]
    > ![Bereich "Daten"](media/northwind-orders-canvas-part1/datasource-04.png)

    Die **Bestellungen** Entität enthält viele Felder verschiedener Typen:

    > [!div class="mx-imgBorder"]
    > ![Liste der Felder in der Orders-Entität](media/northwind-orders-canvas-part1/datasource-05.png)

    Jedes Feld verfügt über eine **Anzeigenamen** und ein **Namen**, die manchmal aufgerufen wird, des logischen Namens. Beide Namen verweisen auf die gleiche Sache. Im Allgemeinen werden Sie den Anzeigenamen verwenden, erstellen Sie eine app, aber manchmal erfordern mehr unverständlich **Namen**, wie in einer Prozedur beschrieben.

1. Schließen Sie in PowerApps Studio, die **Daten** Bereich durch das Schließen-Symbol (X) in der oberen rechten Ecke auswählen.

## <a name="create-the-order-gallery"></a>Erstellen des Order-Katalogs

1. Auf der **einfügen** Registerkarte **Katalog** > **Leerzeichen vertikal** Hinzufügen einer [ **Katalog** ](controls/control-gallery.md)-Steuerelement, das die Bestellungen angezeigt werden.

    > [!div class="mx-imgBorder"]
    > ![INSERT, Katalog, Leerzeichen vertikal](media/northwind-orders-canvas-part1/orders-01.png)

1. Legen Sie in der Bearbeitungsleiste den Text des Katalogs **Elemente** -Eigenschaft auf diese Formel:

    ```powerapps-comma
    Sort( Orders; 'Order Number'; Descending )
    ```

    Die [ **Sortierreihenfolge** ](functions/function-sort.md) -Funktion sortiert die Liste, damit die neueste Reihenfolge (mit der höchsten Anzahl von Reihenfolge) ersten angezeigt wird.

    > [!div class="mx-imgBorder"]
    > ![Festlegen der Items-Eigenschaft des Katalogs](media/northwind-orders-canvas-part1/orders-02.png)

1. In der **Eigenschaften** Registerkarte neben dem rechten Rand, und Öffnen der **Layout** Liste:

    > [!div class="mx-imgBorder"]
    > ![Liste der Optionen für layout](media/northwind-orders-canvas-part1/orders-03.png)

1. Wählen Sie in der Liste der Optionen, **Titel und Untertitel**:

    > [!div class="mx-imgBorder"]
    > ![Wählen Sie ein layout](media/northwind-orders-canvas-part1/orders-04.png)

    Zwei [ **Bezeichnung** ](controls/control-text-box.md) Steuerelemente in der Vorlage des Katalogs hinzugefügt werden. Standardmäßig werden diese Steuerelemente zwei Spalten angezeigt, mit die **Bestellungen** -Entität, die Sie als Nächstes geändert werden. Vorlage des Katalogs wird für jeden Datensatz in Entität vertikal repliziert.

1. Wenn Sie geschlossen haben die **Daten** wählen Sie im Bereich **bearbeiten** (neben **Felder**) in der **Eigenschaften** Registerkarte am rechten Rand.

1. In der **Daten** wählen Sie im Bereich **Title1** (oder wählen Sie die obere Bezeichnung in der Vorlage des Katalogs).

1. Legen Sie in der Bearbeitungsleiste den Text der Bezeichnung **Text** Eigenschaft auf den folgenden Ausdruck:

    ```powerapps-comma
    "Order " & ThisItem.'Order Number'
    ```

    > [!div class="mx-imgBorder"]
    > ![Legen Sie die Beschriftung "Titel" Text-Eigenschaft](media/northwind-orders-canvas-part1/orders-06.png)

    Die Bestellnummer wird am oberen Rand jedes Katalogelement unterschiedlich angezeigt. In der Katalogvorlage **ThisItem** gewährt Zugriff auf alle Felder in der **Reihenfolge** Entität.

1. In der **Daten** wählen Sie im Bereich **Subtitle1** (oder wählen Sie die untere Bezeichnung in der Vorlage des Katalogs):

    > [!div class="mx-imgBorder"]
    > ![Wählen Sie Untertitel-Bezeichnung](media/northwind-orders-canvas-part1/orders-07.png)

1. Legen Sie in der Bearbeitungsleiste den Text der Bezeichnung **Text** Eigenschaft auf den folgenden Ausdruck:

    ```powerapps-comma
    ThisItem.Customer.Company
    ```

    > [!div class="mx-imgBorder"]
    > ![Festlegen der Untertitel der Label Text-Eigenschaft](media/northwind-orders-canvas-part1/orders-08.png)

    Nachdem Sie diese Formel eingegeben haben, kann es eine rote verschnörkelte einen Moment lang angezeigt. Der Fehler sollte behoben, wenn Sie, alle Elemente außerhalb der Bearbeitungsleiste auswählen, und klicken Sie dann den Cursor in die Bearbeitungsleiste zurückgegeben. Wenn der Fehler weiterhin auftritt, oder Sie keinen Wert sehen aus, wählen Sie die **Ansicht** Registerkarte **Datenquellen**, und aktualisieren Sie dann die **Bestellungen** Entität, indem Sie auf die Auslassungspunkte (...), die rechts neben dem Namen der Datenquelle.

    Beim Angeben von **ThisItem.Customer**, nutzen Sie eine viele-zu-eins-Beziehung zwischen der **Bestellungen** und **Kunden** Entitäten und den Kundendatensatz abrufen die wird jeder Bestellung zugeordnet. Aus den Kundendatensatz, sind Sie Extrahieren von Daten in die **Unternehmen** Spalte zum Anzeigen.

    Können Sie anzeigen, alle Beziehungen aus der **Bestellungen** Entität, die andere Entitäten, einschließlich der **Kunden** Entität:

    > [!div class="mx-imgBorder"]
    > ![Liste der Beziehungen](media/northwind-orders-canvas-part1/orders-09.png)

1. Schließen Sie die **Daten** Bereich durch das Schließen-Symbol (X) in der oberen rechten Ecke auswählen.

## <a name="show-each-orders-status"></a>Anzeigen des Status des Auftrags

In diesem Verfahren Sie Speicherplatz im Katalog für eine Bezeichnung hinzufügen und konfigurieren Sie sie zum Anzeigen des Status des Auftrags in einer anderen Farbe auf Grundlage der Daten.

1. In der Vorlage des Katalogs, reduzieren Sie die Breite der ersten Bezeichnung **Title1**:

    > [!div class="mx-imgBorder"]
    > ![Title1 in der Vorlage des Katalogs](media/northwind-orders-canvas-part1/status-01.png)

1. Wiederholen Sie den vorherigen Schritt mit der zweiten Bezeichnung **Subtitle1**:

    > [!div class="mx-imgBorder"]
    > ![Subtitle1 in der Vorlage des Katalogs](media/northwind-orders-canvas-part1/status-02.png)

1. Der Katalog-Vorlage (oder ein Steuerelement in der Vorlage) ausgewählt haben, wählen Sie **Bezeichnung** auf die **einfügen** Registerkarte:

    > [!div class="mx-imgBorder"]
    > ![Fügen Sie eine Bezeichnung hinzu](media/northwind-orders-canvas-part1/status-03.png)

1. Verschieben Sie die neue Bezeichnung rechts neben der **Title1** Bezeichnung:

    > [!div class="mx-imgBorder"]
    > ![Verschieben und Ändern der Größe einer Bezeichnung](media/northwind-orders-canvas-part1/status-04.png)

1. Legen Sie die **Text** Eigenschaft, der die neue Bezeichnung auf den folgenden Ausdruck:

    ```powerapps-comma
    ThisItem.'Order Status'
    ```

    > [!div class="mx-imgBorder"]
    > ![Legen Sie die Text-Eigenschaft](media/northwind-orders-canvas-part1/status-05.png)

    In der **Bestellungen** Entität, die **Bestellstatus** Feld enthält einen Wert aus der **Status der Bestellung** Optionssatz. Ein Optionssatz ähnelt einer Enumeration in anderen Programmiersprachen kennen. Jeder Satz von Optionen wird in der Datenbank definiert, damit Benutzer nur diejenigen Optionen angeben können, die in der Gruppe sind. Die **Status der Bestellung** Optionssatz ist auch global, nicht lokal, sodass Sie es in anderen Entitäten verwenden können:

    > [!div class="mx-imgBorder"]
    > ![Optionssatz Status sortiert](media/northwind-orders-canvas-part1/status-06.png)

    Jede Option in einem Satz hat einen Namen, der angezeigt wird, wenn Sie diese in eine Bezeichnung angezeigt. Diese Namen lokalisiert werden können, und, ob ein Englischer Benutzer auswählt, erkennt die app die gleiche Option **Apple**, wählt ein französischer Benutzer **Pomme**, oder Spanisch Auswahl **Manzana**. Aus diesem Grund können nicht Sie erstellen eine Formel, die auf eine hartcodierte Zeichenfolge eine Option basiert wie weiter unten in diesem Thema wird veranschaulicht.

    In Formeln verwenden, müssen Sie umschließen **Bestellstatus** mit einfachen Anführungszeichen, da es sich um ein Leerzeichen enthält. Jedoch diesem Namen funktioniert genauso wie alle anderen Namen in PowerApps, z. B. **Kunden** oder **Unternehmen**, verfügt.

1. Auf der **Startseite** Registerkarte, erhöhen Sie den Schriftgrad der statusbezeichnung auf 20 Punkt und der Text rechts ausrichten:

    > [!div class="mx-imgBorder"]
    > ![Schriftgrad ändern und Ausrichtung](media/northwind-orders-canvas-part1/status-07.png)

1. Legen Sie in der Bearbeitungsleiste die **Farbe** -Eigenschaft der statusbezeichnung auf diese Formel:

    ```powerapps-comma
    Switch( ThisItem.'Order Status';
        'Orders Status'.Closed; Green;
        'Orders Status'.New; Black;
        'Orders Status'.Invoiced; Blue;
        'Orders Status'.Shipped; Purple
    )
    ```

    > [!div class="mx-imgBorder"]
    > ![Legen Sie die Color-Eigenschaft für die Beschriftung für status](media/northwind-orders-canvas-part1/status-08.png)

    PowerApps verhindert, dass Sie erstellen eine Formel, die auf eine hartcodierte Zeichenfolge für jede einzelne Option in einer Gruppe abhängig sind, da Formeln ungeeignete Ergebnissen führen können, wenn die Optionsnamen lokalisiert werden. Stattdessen die **Switch** Funktion bestimmt die Farbe basierend auf eine beliebige Zeichenfolge, die in die Bezeichnung, die basierend auf den Einstellungen des Benutzers angezeigt wird.

    Mit dieser Formel vorhanden werden Sie verschiedene Status-Werte als die vorherige Abbildung zeigt in unterschiedlichen Farben dargestellt, angezeigt.

## <a name="display-each-orders-total"></a>Anzeigen des Auftrags insgesamt

1. Wählen Sie das erste Element im Katalog, der Vorlage des Katalogs ist:

    > [!div class="mx-imgBorder"]
    > ![Wählen Sie die Katalogvorlage](media/northwind-orders-canvas-part1/aggregate-01.png)

1. Auf der **einfügen** Registerkarte **Bezeichnung** eine andere Bezeichnung hinzufügen:

    > [!div class="mx-imgBorder"]
    > ![Fügen Sie eine Bezeichnung hinzu](media/northwind-orders-canvas-part1/aggregate-02.png)

1. Verschieben Sie die neue Bezeichnung, sodass er unter der statusbezeichnung angezeigt wird:

    > [!div class="mx-imgBorder"]
    > ![Ändern der Größe und verschieben Sie die neue Bezeichnung](media/northwind-orders-canvas-part1/aggregate-03.png)

1. Legen Sie in der Bearbeitungsleiste, der neuen Bezeichnung **Text** -Eigenschaft auf diese Formel:

    ```powerapps-comma
    Text( Sum( ThisItem.'Order Details'; Quantity * 'Unit Price' ); "[$-en-US]$ #,###.00" )
    ```

    > [!div class="mx-imgBorder"]
    > ![Formel zum Berechnen der Gesamtkosten des Auftrags](media/northwind-orders-canvas-part1/aggregate-04.png)

    In dieser Formel die [ **Summe** ](functions/function-aggregates.md) Funktion addiert die Datensätze in der **Bestelldetails** Entität, die jeden Datensatz in zugeordnet sind die **Reihenfolge**Entität über eine 1: n Beziehung. Diese Einzelposten besteht jede Bestellung, und die gleiche 1: n Beziehung verwenden Sie zum Anzeigen und bearbeiten die Positionen in der unteren rechten Bereich des Bildschirms.

    Diese Formel wird eine blaue Unterstreichung und [delegierungswarnung](delegation-overview.md) da Common Data Service Delegierung von komplexen Aggregatfunktionen (z. B. die Summe der eine Multiplikation) nicht unterstützt. Diese Informationen können Sie ignorieren, da keine Reihenfolge, in diesem Beispiel mehr als 500 Positionen enthält. Wenn für eine andere app erforderlich, Sie dieses Limit in erhöhen können **Anwendungseinstellungen**.

    Die [ **Text** ](functions/function-text.md) Funktion in der folgenden Formel ein Währungssymbol hinzugefügt und formatiert das Ergebnis mit Tausenden und Dezimaltrennzeichen. Laut enthält die Formel den Sprach-Tag für die USA Englisch ( **[$-En-US]** ) und einem Dollar-Symbol ( **$** ). Wenn Sie den Sprach-Tag entfernen, wird es durch eine auf Grundlage von spracheinstellungen ersetzt, und die Bezeichnung zeigt die entsprechenden Formate für dieses Tag. Wenn Sie Dollarsymbols lassen, wird die Bezeichnung auf das entsprechende Währungssymbol basierend auf den Einstellungen des Benutzers angezeigt. Sie können jedoch erzwingen, dass ein anderes Symbol angezeigt, die durch Ersetzen des Dollarsymbols mit derjenigen, die Sie bevorzugen.

1. Auf der **Startseite** Registerkarte, ändern Sie den Schriftgrad des die aktuelle Bezeichnung auf 20 Punkt und der Text rechts ausrichten:

    > [!div class="mx-imgBorder"]
    > ![Ändern Sie den Schriftgrad und die Ausrichtung einer Bezeichnung](media/northwind-orders-canvas-part1/aggregate-05.png)

1. Verschieben Sie den Katalog auf dem linken Rand des Bildschirms, und verringern Sie der Breite des Katalogs, um Speicherplatz zu schließen.

1. Erhöhen des Katalogs Höhe, sodass er fast so groß sein wie der Bildschirm ist, aber ein wenig Platz am Anfang für eine Titelleiste angezeigt wird, die Sie zu Beginn des nächsten Themas hinzufügen müssen:

    > [!div class="mx-imgBorder"]
    > ![Verschiebe und verkleinere Sie den Katalog](media/northwind-orders-canvas-part1/aggregate-06.png)

## <a name="summary"></a>Zusammenfassung

Zusammenfassend lässt sich sagen, Sie erstellen eine einzelnen Bildschirm Canvas-app durch das Hinzufügen von des Order-Katalogs, der diese Elemente enthält, gestartet:

- Ein Ausdruck, der die Reihenfolgennummer angezeigt werden soll: `"Orders " & ThisItem.OrderNumber`
- Ein Feld in einer n: 1 Beziehung: `ThisItem.Customer.Company`
- Eine Bezeichnung, die mit dem Namen einer Option in einer Gruppe angezeigt: `ThisItem.'Order Status'`
- Eine Bezeichnung, die sich, das Ändern auf die Bezeichnung, welche Option in einem Satz zeigt basiert: `Switch( ThisItem.'Order Status'; 'Orders Status'.Closed; Green; ...`
- Eine komplexe aggregate-Funktion über eine 1: n Beziehung: `Sum( ThisItem.'Order Details'; Quantity * 'Unit Price' )`

## <a name="next-topic"></a>Nächstes Thema

Im nächsten Thema, fügen Sie eine [ **Bearbeitungsformular** ](controls/control-form-detail.md) Steuerelement zum Anzeigen und bearbeiten, die eine Zusammenfassung von Was anordnen, dass den Benutzer wählt in der Galerie, die Sie gerade erstellt haben.

> [!div class="nextstepaction"]
> [Erstellen Sie das Formular Zusammenfassung](northwind-orders-canvas-part2.md)