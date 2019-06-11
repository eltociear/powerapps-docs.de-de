---
title: Erstellen Sie einen Details-Katalog in einer Canvas-app | Microsoft-Dokumentation
description: Erstellen Sie einen Details-Katalog in einer Canvas-app, um Daten für Northwind Traders zu verwalten.
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
ms.openlocfilehash: 9549b8f389cf696cf3fc8e4659da6b418383ac6e
ms.sourcegitcommit: e85072f7a80da308c4caabe20adbf2509588ca57
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66760957"
ms.PowerAppsDecimalTransform: true
---
# <a name="create-a-detail-gallery-in-a-canvas-app"></a>Erstellen Sie einen Details-Katalog in einer Canvas-app

Führen Sie schrittweise Anweisungen zum Erstellen eines Katalogs Details in einer Canvas-app für die Verwaltung von fiktiven Daten in der Datenbank Northwind Traders ein. Dieses Thema ist Teil einer Reihe, die erklärt, wie Sie eine Geschäfts-app auf relationalen Daten in Common Data Service zu erstellen. Erkunden Sie diese Themen in dieser Sequenz, für optimale Ergebnisse:

1. [Erstellen eines Katalogs Reihenfolge](northwind-orders-canvas-part1.md).
1. [Erstellen Sie eine Zusammenfassung Formular](northwind-orders-canvas-part2.md).
1. Erstellen Sie einen Details-Katalog (**in diesem Thema**).

> [!div class="mx-imgBorder"]
> ![Definition der Bildschirmbereiche](media/northwind-orders-canvas-part1/orders-parts.png)

## <a name="prerequisites"></a>Voraussetzungen

Bevor Sie in diesem Thema beginnen, installieren Sie die Datenbank, wie weiter oben in diesem Thema beschrieben. Müssen Sie Sie dann dem Order-Katalog und die Zusammenfassung Form zu erstellen oder öffnen Sie die **Northwind Orders (Canvas) – Teil 3 beginnen** -app, die bereits dem Katalog und dieses Formular enthält.

## <a name="create-another-title-bar"></a>Erstellen Sie eine andere Titelleiste

1. Wählen Sie am oberen Rand des Bildschirms, das [ **Bezeichnung** ](controls/control-text-box.md) -Steuerelement als Titelleiste, kopieren Sie sie durch Drücken von STRG + C, und fügen Sie ihn dann durch Drücken von STRG-v:

    > [!div class="mx-imgBorder"]
    > ![Kopieren Sie und fügen Sie die Titelleiste](media/northwind-orders-canvas-part3/details-01.png)

1. Die Größe und verschieben Sie die Kopie, sodass es direkt unter der Zusammenfassung Formular angezeigt wird.

1. Entfernen Sie den Text aus der Kopie in einer der folgenden Methoden:

    - Doppelklicken Sie auf den Text, um es auszuwählen, und drücken Sie ENTF.
    - Legen Sie die Bezeichnung des **Text** Eigenschaft auf eine leere Zeichenfolge ( **""** ).

    > [!div class="mx-imgBorder"]
    > ![Entfernen Sie den Text aus der Kopie der Titelleiste](media/northwind-orders-canvas-part3/details-02.png)

## <a name="add-a-gallery"></a>Einen Katalog hinzufügen

1. Fügen Sie eine [ **Katalog** ](controls/control-gallery.md) steuern Sie mit einem **Leerzeichen vertikal** Layout:

    > [!div class="mx-imgBorder"]
    > ![Hinzufügen eines leeren vertikalen Katalogs](media/northwind-orders-canvas-part3/details-03.png)

    Der neue Katalog, der Auftragsdetails angezeigt wird, wird in der oberen linken Ecke angezeigt:

    > [!div class="mx-imgBorder"]
    > ![Der Standardspeicherort des Auftragsdetails Katalogs](media/northwind-orders-canvas-part3/details-04.png)

1. Schließen der **Daten** Bereich, und klicken Sie dann Ändern der Größe und Verschieben der Detail-Katalog in der Ecke unten rechts unterhalb der Titelleiste für die neue:

    > [!div class="mx-imgBorder"]
    > ![Endgültige Position der Auftragsdetails Katalog](media/northwind-orders-canvas-part3/details-05.png)

1. Legen Sie die **Elemente** -Eigenschaft des Katalogs auf diese Formel Detail:

    ```powerapps-comma
    Gallery1.Selected.'Order Details'
    ```

    > [!div class="mx-imgBorder"]
    > ![Festlegen der Items-Eigenschaft des Katalogs detail](media/northwind-orders-canvas-part3/details-06.png)

    Wenn ein Fehler angezeigt wird, vergewissern Sie sich, dass die Order-Katalog den Namen **Gallery1** (in der **Strukturansicht** Bereich am linken Rand). Wenn Sie diesen Katalog über einen anderen Namen aufweist, benennen Sie sie **Gallery1**.

    Sie haben nur die beiden Kataloge verknüpft. Wenn der Benutzer eine Bestellung in der Order-Galerie auswählt, identifiziert die Auswahl ein Datensatzes in die **Bestellungen** Entität. Wenn, dass der Auftrag über mindestens eine Zeile enthält Elemente, den Datensatz in die **Bestellungen** Entität verknüpft ist, auf eine oder mehrere Datensätze in der **Bestelldetails** Entität und Daten aus diesen Datensätzen angezeigt wird, im Detail-Katalog. Dies spiegelt wider, die 1: n Beziehung, die für Sie zwischen erstellt wurde die **Bestellungen** und **Bestelldetails** Entitäten. Die Formel, die Sie angegeben haben führt"" dieser Beziehung Sie mithilfe der Punktnotation:

    > [!div class="mx-imgBorder"]
    > ![1: n Beziehung zwischen der Orders-Entität und der Order Details-Entität](media/northwind-orders-canvas-part3/schema-orders-rel.png)

## <a name="show-product-names"></a>Anzeigen der Produktnamen

1. Wählen Sie den Katalog Detail **Hinzufügen eines Elements aus der Registerkarte "Einfügen"** um die Katalogvorlage auszuwählen:

    > [!div class="mx-imgBorder"]
    > ![Wählen Sie die Vorlage für den Katalog detail](media/northwind-orders-canvas-part3/details-07.png)

    Stellen Sie sicher, dass Sie die Katalogvorlage anstelle der eigentlichen Sammlung ausgewählt haben. Das umgebende Feld sollte etwas innerhalb des Katalogs Grenzen und wahrscheinlich des Katalogs Höhe kleiner sein. Wie Sie Steuerelemente in dieser Vorlage einfügen, werden sie für jedes Element im Katalog wiederholt.

1. Auf der **einfügen** Registerkarte, fügen Sie eine Bezeichnung, im Detail-Katalog.

    Die Bezeichnung sollte innerhalb des Katalogs angezeigt werden; Wenn dies nicht der Fall, versuchen Sie es erneut, aber Achten Sie darauf, die Vorlage des Katalogs auswählen, bevor Sie die Bezeichnung einfügen.

    > [!div class="mx-imgBorder"]
    > ![Eine Bezeichnung im Katalog Details hinzufügen](media/northwind-orders-canvas-part3/details-08.png)

1. Legen Sie die neuen Bezeichnung **Text** -Eigenschaft auf diese Formel:

    ```powerapps-comma
    ThisItem.Product.'Product Name'
    ```

    Wenn kein Text angezeigt wird, wählen Sie den Pfeil für **Reihenfolge 0901** im unteren Bereich des Katalogs Reihenfolge.

1. Ändern Sie die Bezeichnung, sodass der vollständige Text angezeigt wird:

    > [!div class="mx-imgBorder"]
    > ![Produktname wird in den Details der Bestellung anzeigen.](media/northwind-orders-canvas-part3/details-09.png)

    Dieser Ausdruck führt Sie aus einem Datensatz in die **Bestelldetails** Entität. Der Datensatz wird, verbleibt in **ThisItem** an die **Bestellprodukte** Entität über eine n: 1 Beziehung:

    > [!div class="mx-imgBorder"]
    > ![Viele-zu-eins-Beziehung zwischen der Order Details-Entität und die Reihenfolge Product-Entität](media/northwind-orders-canvas-part3/schema-orderdetails-rel.png)

    Die **Produktname** Feld (und anderen Feldern, die Sie wahrscheinlich) extrahiert werden:

    > [!div class="mx-imgBorder"]
    > ![Felder in der Reihenfolge Products-Entität](media/northwind-orders-canvas-part3/schema-products-fields.png)

## <a name="show-product-images"></a>Anzeigen der Produktbilder

1. Auf der **einfügen** Registerkarte ein [ **Image** ](controls/control-image.md) Steuerelement in der Galerie Detail:

    > [!div class="mx-imgBorder"]
    > ![Image-Steuerelement einfügen](media/northwind-orders-canvas-part3/details-10.png)

1. Die Größe und verschieben Sie das Abbild und die Bezeichnung, die parallel angeboten werden.

    > [!TIP]
    > Präzise Steuerung der Größe und die Position eines Steuerelements starten Sie zum Ändern der Größe oder verschieben, ohne die Alt-Taste drücken, und fahren Sie mit der Größe oder Position des Steuerelements, während Sie die Alt-Taste gedrückt halten:

    > [!div class="mx-imgBorder"]
    > ![Verschieben Sie die Image-Steuerelement](media/northwind-orders-canvas-part3/details-11.png)

1. Das Bild des **Image** -Eigenschaft auf diese Formel:

    ```powerapps-comma
    ThisItem.Product.Picture
    ```

    Der Ausdruck verweist auf ein Produkt, das mit dieser verknüpft ist in diesem Fall zu bestellen, Details und das Extrahieren der **Bild** anzuzeigende Feld.

    > [!div class="mx-imgBorder"]
    > ![Produktbild anzeigen](media/northwind-orders-canvas-part3/details-12.png)

1. Reduzieren Sie die Höhe der Vorlage des Katalogs, also, mehr als eine **Order Detail** Datensatz zu einem Zeitpunkt angezeigt wird:

    > [!div class="mx-imgBorder"]
    > ![Verkürzen Sie die Vorlage des Katalogs](media/northwind-orders-canvas-part3/details-13.png)

## <a name="show-product-quantity-and-cost"></a>Produktmenge und Kosten anzeigen

1. Auf der **einfügen** Registerkarte, fügen Sie eine andere Bezeichnung im Detail-Katalog, und klicken Sie dann ändern Sie die Größe und verschieben Sie die neue Bezeichnung rechts neben die Produktinformationen.

1. Legen Sie die neuen Bezeichnung **Text** Eigenschaft auf den folgenden Ausdruck:

    ```powerapps-comma
    ThisItem.Quantity
    ```

    Diese Formel Ruft die Informationen direkt aus der **Bestelldetails** Entität (keine Beziehung erforderlich).

    > [!div class="mx-imgBorder"]
    > ![Produktmenge anzeigen](media/northwind-orders-canvas-part3/details-13b.png) 

1. Auf der **Startseite** Registerkarte, Ändern der Ausrichtung dieses Steuerelements auf **rechts**:

    > [!div class="mx-imgBorder"]
    > ![Ändern der Ausrichtung](media/northwind-orders-canvas-part3/details-14.png)

1. Auf der **einfügen** Registerkarte, fügen Sie eine andere Bezeichnung im Katalog Detail, und klicken Sie dann ändern Sie die Größe und verschieben Sie die Bezeichnung rechts neben der Bezeichnung Menge.

1. Legen Sie die neuen Bezeichnung **Text** -Eigenschaft auf diese Formel:

    ```powerapps-comma
    Text( ThisItem.'Unit Price'; "[$-en-US]$ #,###.00" )
    ```

    Wenn Sie nicht den Sprach-Tag enthalten ( **[$-En-US]** ), wird er hinzugefügt werden, basierend auf Ihre Sprache und Region. Wenn Sie eine andere Sprachtag verwenden, sollten Sie zum Entfernen der **$** direkt nach dem Schließen eckige Klammer ( **]** ), und fügen Sie dann Ihre eigenen Währungssymbol an dieser Position.

    > [!div class="mx-imgBorder"]
    > ![Anzeigen der Preis pro Einheit](media/northwind-orders-canvas-part3/details-15.png)

1. Auf der **Startseite** Registerkarte, Ändern der Ausrichtung dieses Steuerelements auf **rechts**:

    > [!div class="mx-imgBorder"]
    > ![Ändern der Ausrichtung](media/northwind-orders-canvas-part3/details-16.png)

1. Auf der **einfügen** Registerkarte, fügen Sie einen anderen Label-Steuerelement im Detail-Katalog, und klicken Sie dann ändern Sie die Größe und verschieben Sie die neue Bezeichnung rechts neben der Preis.

1. Legen Sie die neuen Bezeichnung **Text** -Eigenschaft auf diese Formel:

    ```powerapps-comma
    Text( ThisItem.Quantity * ThisItem.'Unit Price'; "[$-en-US]$ #,###.00" )
    ```

    In diesem Fall, wenn Sie nicht den Sprach-Tag enthalten ( **[$-En-US]** ), wird er hinzugefügt werden, basierend auf Ihre Sprache und Region. Wenn das Tag anders ist, sollten Sie mit Ihren eigenen Währungssymbol statt der **$** direkt nach dem Schließen eckige Klammer ( **]** ).

    > [!div class="mx-imgBorder"]
    > ![Erweiterte Preis anzeigen](media/northwind-orders-canvas-part3/details-17.png)

1. Auf der **Startseite** Registerkarte, Ändern der Ausrichtung dieses Steuerelements auf **rechts**:

    > [!div class="mx-imgBorder"]
    > ![Ändern der Ausrichtung](media/northwind-orders-canvas-part3/details-18.png)

    Hinzufügen von Steuerelementen im Detail-Katalog ist jetzt fertig.

1. In der **Strukturansicht** wählen Sie im Bereich **Screen1** um sicherzustellen, dass der Detail-Katalog nicht mehr ausgewählt ist.

## <a name="add-text-to-the-new-title-bar"></a>Hinzufügen von Text in die neue Titelleiste

1. Auf der **einfügen** Registerkarte, fügen Sie eine andere Bezeichnung auf dem Bildschirm:

    > [!div class="mx-imgBorder"]
    > ![Beschriftung einfügen](media/northwind-orders-canvas-part3/details-19.png)

1. Ändern der Größe und verschieben Sie die neue Bezeichnung über die Bilder der Produkte in der zweiten Titelleiste, und ändern Sie die Farbe des Texts auf Weiß auf die **Startseite** Registerkarte.

1. Doppelklicken Sie auf der Bezeichnungstext, und geben Sie **Produkt**:

    > [!div class="mx-imgBorder"]
    > ![Ändern von Beschriftungstext Produkt](media/northwind-orders-canvas-part3/details-20.png)

1. Kopieren und Einfügen der Product-Bezeichnung, und klicken Sie dann Ändern der Größe und verschieben Sie die Kopie über der Mengenspalte.

1. Doppelklicken Sie auf die neue Bezeichnung Text, und geben Sie **Menge**:

    > [!div class="mx-imgBorder"]
    > ![Ändern von Beschriftungstext Menge](media/northwind-orders-canvas-part3/details-21.png)

1. Kopieren und Einfügen die Bezeichnung für Menge und Größe, und verschieben Sie die Kopie oberhalb der Einzelpreis Spalte.

1. Doppelklicken Sie auf die neue Bezeichnung Text, und geben Sie **Unit Price**:

    > [!div class="mx-imgBorder"]
    > ![Ändern von Beschriftungstext zum Preis pro Einheit](media/northwind-orders-canvas-part3/details-22.png)

1. Kopieren und Einfügen der Einzelpreis Bezeichnung, und klicken Sie dann ändern Sie die Größe und verschieben oberhalb der Endpreis Spalte.

1. Doppelklicken Sie auf den Text, der die neue Bezeichnung, und geben Sie **erweiterte**:

    > [!div class="mx-imgBorder"]
    > ![Ändern von Beschriftungstext auf Extended](media/northwind-orders-canvas-part3/details-23.png)

## <a name="display-order-totals"></a>Die Reihenfolge Gesamtergebnisse anzeigen

1. Reduzieren Sie die Höhe des Detail Katalog aus, um Platz für die Auftragssummen am unteren Rand des Bildschirms zu machen:

    > [!div class="mx-imgBorder"]
    > ![Verkürzen Sie die Auftragsdetails Katalog](media/northwind-orders-canvas-part3/sum-01.png)

1. Kopieren und fügen Sie die Titelleiste in der Mitte der Bildschirm, und klicken Sie dann die Kopie in den unteren Rand des Bildschirms verschieben:

    > [!div class="mx-imgBorder"]
    > ![Kopieren Sie die Titelleiste, und verschieben Sie die Kopie an den unteren Rand](media/northwind-orders-canvas-part3/sum-02.png)

1. Kopieren und fügen Sie die Bezeichnung "Product" über die mittleren Titelleiste, und verschieben Sie die Kopie dann in die Titelleiste des nach unten, nur auf der linken Seite des der **Menge** Spalte.

1. Doppelklicken Sie auf die neue Bezeichnung Text, und geben Sie diesen Text:<br>**Gesamtbetrag der Bestellung:**

    > [!div class="mx-imgBorder"]
    > ![Bezeichnung für die Auftragssummen hinzufügen](media/northwind-orders-canvas-part3/sum-03.png)

1. Kopieren und Einfügen der Auftragssummen Bezeichnung, und klicken Sie dann ändern Sie die Größe und rechts neben die Auftragssummen Bezeichnung verschieben.

1. Legen Sie die neuen Bezeichnung **Text** -Eigenschaft auf diese Formel:

    ```powerapps-comma
    Sum( Gallery1.Selected.'Order Details'; Quantity )
    ```

    Diese Formel wird eine delegierungswarnung, jedoch können Sie diese ignorieren, da keine einzelnen Auftrag mehr als 500 Produkten enthält.

1. Auf der **Startseite** Registerkarte, auf die neue Bezeichnung textausrichtung festgelegt **rechts**:

    > [!div class="mx-imgBorder"]
    > ![Ändern der Ausrichtung](media/northwind-orders-canvas-part3/sum-04.png)

1. Kopieren und Einfügen diesen Label-Steuerelement, und klicken Sie dann ändern Sie die Größe und verschieben Sie die Kopie in die **erweiterte** Spalte.

1. Legen Sie der Kopiervorgangs des **Text** -Eigenschaft auf diese Formel:

    ```powerapps-comma
    Text( Sum( Gallery1.Selected.'Order Details'; Quantity * 'Unit Price' ); "[$-en-US]$ #,###.00" )
    ```

    Diese Formel wird eine delegierungswarnung, jedoch können Sie diese ignorieren, da keine einzelnen Auftrag mehr als 500 Produkten enthält.

    > [!div class="mx-imgBorder"]
    > ![Gesamtkosten der Reihenfolge anzeigen](media/northwind-orders-canvas-part3/sum-05.png)

## <a name="add-space-for-new-details"></a>Speicherplatz für neue Details hinzufügen

In einem Katalog Sie können Daten anzeigen, aber nicht aktualisieren oder Hinzufügen von Datensätzen. Unter den Details-Katalog, fügen Sie einen Bereich, in denen der Benutzer kann einen Datensatz im konfigurieren, der **Bestelldetails** Entität und einfügen, die in einer Bestellung aufzeichnen.

1. Reduzieren Sie die Höhe des Detail-Katalogs genug Platz für einen einzelnen Element bearbeiten Speicherplatz unter diesen Katalog vornehmen.

    In diesem Bereich werden Sie Steuerelemente hinzufügen, damit der Benutzer eine Details zur Bestellung hinzufügen kann:

    > [!div class="mx-imgBorder"]
    > ![Kürzen Sie den Katalog Details](media/northwind-orders-canvas-part3/add-details-01.png)

1. Auf der **einfügen** Registerkarte, fügen Sie eine Bezeichnung, und klicken Sie dann ändern Sie die Größe und verschieben Sie es unter den Details-Katalog.

    > [!div class="mx-imgBorder"]
    > ![Fügen Sie eine Bezeichnung](media/northwind-orders-canvas-part3/add-details-02.png)

1. Doppelklicken Sie auf den Text, der die neue Bezeichnung, und drücken Sie ENTF.

1. Auf der **Startseite** Registerkarte, legen Sie die neuen Bezeichnung **füllen** Farbe **Hellblau**:

    > [!div class="mx-imgBorder"]
    > ![Ändern Sie Bezeichnung Füllung auf Hellblau](media/northwind-orders-canvas-part3/add-details-03.png)

## <a name="add-the-order-details-data-source"></a>Die Order Details-Datenquelle hinzufügen

1. Auf der **Ansicht** Registerkarte **Datenquellen**, und wählen Sie dann **Datenquelle hinzufügen** in die **Daten** Bereich:

    > [!div class="mx-imgBorder"]
    > ![Hinzufügen einer Datenquelle](media/northwind-orders-canvas-part3/add-details-04.png)

1. Wählen Sie **Common Data Service**:

    > [!div class="mx-imgBorder"]
    > ![Wählen Sie Common Data Service](media/northwind-orders-canvas-part3/add-details-05.png)

1. Am oberen Rand der **Daten** im Bereich **Reihenfolge** wählen Sie in das Suchfeld der **Order Details** aus, und wählen Sie dann **Connect** an die Ende des Bereichs:

    > [!div class="mx-imgBorder"]
    > ![Angeben von Order Details-Entität](media/northwind-orders-canvas-part3/add-details-06.png)

    Sie haben soeben eine andere Datenquelle für die app hinzugefügt:

    > [!div class="mx-imgBorder"]
    > ![Liste der Datenquellen](media/northwind-orders-canvas-part3/add-details-07.png)

    Sie müssen diese Datenquelle hinzufügen, daran, auch wenn die app über eine 1: n Beziehung gelesen werden können, die app noch Zurückschreiben von Änderungen nicht möglich. Die app muss direkt mit der verknüpften Entität ändern.

1. Schließen der **Daten** Bereich.

## <a name="select-a-product"></a>Wählen Sie ein Produkt

1. Auf der **einfügen** Registerkarte **Steuerelemente** > **Kombinationsfeld**:

    > [!div class="mx-imgBorder"]
    > ![Fügen Sie im Kombinationsfeld](media/northwind-orders-canvas-part3/add-details-08.png)

    Die [ **Kombinationsfeld** ](controls/control-combo-box.md) Steuerelement angezeigt wird, in der oberen linken Ecke.

1. Festlegen des Kombinationsfelds **Elemente** -Eigenschaft auf diese Formel:

    ```powerapps-comma
    Choices( 'Order Details'.Product )
    ```

    > [!div class="mx-imgBorder"]
    > ![Legen Sie das Kombinationsfeld für den Box-Items-Eigenschaft](media/northwind-orders-canvas-part3/add-details-09.png)

    Die [ **Auswahlmöglichkeiten** ](functions/function-choices.md) Funktionsergebnis ist eine Tabelle aller möglichen Werte für die **Produkt** -Feld in der **Order Details** Entität. Dieses Feld ist eine Suche in einer n: 1 Beziehung, also **Auswahlmöglichkeiten** gibt alle Datensätze in der **Bestellprodukte** Entität.

    > [!NOTE]
    > Sie können auch **Auswahlmöglichkeiten** mit Optionssätze für eine Tabelle mit allen Optionen zurück. Die Schritte dieser Ansatz jedoch nicht erwähnt, aber verwendet bereits verwendet werden, wenn Sie im Kombinationsfeld hinzugefügt, die zeigt, **Bestellstatus** in der Zusammenfassung Form.

1. In der **Daten** , öffnen Sie im Bereich der **primärer Text** aus, und wählen Sie dann **Nwind_productname**. 

1. Öffnen der **SearchField** aus, und wählen Sie dann **Nwind_productname**.

    Geben Sie den logischen Namen, da die **Daten** Bereich Anzeigenamen noch in diesem Fall unterstützt nicht:

    > [!div class="mx-imgBorder"]
    > ![Legen Sie den primären Text für das Kombinationsfeld](media/northwind-orders-canvas-part3/add-details-10.png)

1. Schließen der **Daten** Bereich.

1. In der **Eigenschaften** Registerkarte am rechten Rand, scrollen Sie nach unten, deaktivieren Sie **Mehrfachauswahl zulassen**, und stellen sicher, dass **zulassen suchen** aktiviert ist:

    > [!div class="mx-imgBorder"]
    > ![Deaktivieren Sie die Auswahl mehrerer und aktivieren Sie die Suche](media/northwind-orders-canvas-part3/add-details-12.png)

1. Die Größe und Position im Kombinationsfeld in den Bereich von hellblaue, direkt unter der Produktname Spalte im Detail-Katalog:

    > [!div class="mx-imgBorder"]
    > ![Verschieben Sie im Kombinationsfeld](media/northwind-orders-canvas-part3/add-details-13.png)

    In diesem Kombinationsfeld wird der Benutzer einen Datensatz im Angeben der **Produkt** Entität für die **Order Details** Datensatz, der die app zu erstellen, wird.

1. Während Sie die Alt-Taste gedrückt halten, wählen Sie das Kombinationsfeld-Pfeil.

    > [!TIP]
    > Indem Sie die Alt-Taste gedrückt halten, können Sie Daten mit Steuerelementen in PowerApps Studio interagieren, ohne im Vorschaumodus zu öffnen.

1. Wählen Sie in der Liste der Produkte, die angezeigt wird, ein Produkt aus:

    > [!div class="mx-imgBorder"]
    > ![Wählen Sie ein Produkt im Kombinationsfeld](media/northwind-orders-canvas-part3/add-details-14.png)

## <a name="add-a-product-image"></a>Hinzufügen eines Produkts-Images

1. Auf der **einfügen** Registerkarte **Media** > **Image**:

    > [!div class="mx-imgBorder"]
    > ![Image-Steuerelement einfügen](media/northwind-orders-canvas-part3/add-details-15.png)

    Die [ **Image** ](controls/control-image.md) Steuerelement in der oberen linken Ecke angezeigt wird:

    > [!div class="mx-imgBorder"]
    > ![Der Standardspeicherort der Image-Steuerelement](media/northwind-orders-canvas-part3/add-details-16.png)

1. Die Größe und Position des Bilds in den Bereich hellblaue, unter der anderen Produktbilder und neben dem Kombinationsfeld.

1. Legen Sie die **Image** -Eigenschaft des Bildes an:

    ```powerapps-comma
    ComboBox1.Selected.Picture
    ```

    > [!div class="mx-imgBorder"]
    > ![Legen Sie die Image-Eigenschaft des Images](media/northwind-orders-canvas-part3/add-details-17.png)

    Sie verwenden die gleiche Lösung wie früher, um Mitarbeiter in der Zusammenfassung Form angezeigt. Die **ausgewählte** Eigenschaft des Kombinationsfelds gibt den gesamten Datensatz, der alle Produkte, die der Benutzer auswählt, einschließlich der **Bild** Feld.

## <a name="add-a-quantity-box"></a>Fügen Sie das Menge hinzu

1. Auf der **einfügen** Registerkarte **Text** > **Texteingabe**:

    > [!div class="mx-imgBorder"]
    > ![Texteingabe-Feld hinzufügen](media/northwind-orders-canvas-part3/add-details-18.png)

    Die [ **Texteingabe** ](controls/control-text-input.md) Steuerelement in der oberen linken Ecke angezeigt wird:

    > [!div class="mx-imgBorder"]
    > ![Standardspeicherort für die Texteingabe-Feld](media/northwind-orders-canvas-part3/add-details-19.png)

1. Ändern der Größe und verschieben Sie das Texteingabe-Feld nach rechts des Kombinationsfelds, unter der Spalte "Quantity" in der Galerie Detail:

    > [!div class="mx-imgBorder"]
    > ![Die Größe und Position der Texteingabe-Feld](media/northwind-orders-canvas-part3/add-details-20.png)

    Durch die Verwendung dieses Dialogfelds Texteingabe des Benutzers geben die **Menge** Feld der **Bestelldetails** Datensatz.

1. Legen Sie die **Standard** Eigenschaft dieses Steuerelements auf **""** :

    > [!div class="mx-imgBorder"]
    > ![Legen Sie die ** Standard **-Eigenschaft das Texteingabe-Feld](media/northwind-orders-canvas-part3/add-details-21,png)

1. Auf der **Startseite** Registerkarte, legen Sie die Ausrichtung des Texts dieses Steuerelements auf **rechts**:

    > [!div class="mx-imgBorder"]
    > ![Ändern der Ausrichtung](media/northwind-orders-canvas-part3/add-details-22.png)

## <a name="show-the-unit-and-extended-prices"></a>Die Einheit und erweiterte Preise anzeigen

1. Auf der **einfügen** Registerkarte ein **Bezeichnung** Steuerelement.

    Die Bezeichnung wird in der oberen linken Ecke des Bildschirms angezeigt:

    > [!div class="mx-imgBorder"]
    > ![Fügen Sie eine Bezeichnung](media/northwind-orders-canvas-part3/add-details-23.png)

1. Ändern der Größe und verschieben Sie die Bezeichnung rechts neben dem Texteingabe Steuerelement und legen Sie die Bezeichnung des **Text** -Eigenschaft auf diese Formel:

    ```powerapps-comma
    Text( ComboBox1.Selected.'List Price'; "[$-en-US]$ #,###.00" )
    ```

    > [!div class="mx-imgBorder"]
    > ![Legen Sie die Bezeichnung des Text-Eigenschaft](media/northwind-orders-canvas-part3/add-details-24.png)

    Dieses Steuerelement zeigt die **Listenpreis** aus der **Bestellprodukte** Entität. Dieser Wert bestimmt die **Unit Price** Feld der **Bestelldetails** Datensatz.

    > [!NOTE]
    > In diesem Szenario der Wert ist schreibgeschützt, aber anderen Szenarien können aufrufen, für den app-Benutzer ändern. In diesem Fall verwenden Sie eine **Texteingabe** steuern, und legen dessen **Standard** Eigenschaft **Listenpreis**.

1. Auf der **Startseite** Registerkarte, legen Sie die Ausrichtung des Texts der Listenpreis Bezeichnung auf **rechts**:

    > [!div class="mx-imgBorder"]
    > ![Ändern der Ausrichtung](media/northwind-orders-canvas-part3/add-details-25.png)

1. Kopieren und Einfügen der Listenpreis Bezeichnung, und klicken Sie dann ändern Sie die Größe und verschieben Sie die Kopie auf der rechten Seite der Listenpreis Bezeichnung.

1. Legen Sie die neuen Bezeichnung **Text** -Eigenschaft auf diese Formel:

    ```powerapps-comma
    Text( Value(TextInput1.Text) * ComboBox1.Selected.'List Price'; "[$-en-US]$ #,###.00" )
    ```

    > [!div class="mx-imgBorder"]
    > ![Legen Sie die neue Bezeichnung Text-Eigenschaft](media/northwind-orders-canvas-part3/add-details-27.png)

    Dieses Steuerelement zeigt den erweiterten Preis basierend auf der Menge, die der app-Benutzer angegeben und den Listenpreis des Produkts, das der app-Benutzer ausgewählt. Es ist lediglich zur Informationen für den app-Benutzer.

1. Doppelklicken Sie auf die Texteingabe-Steuerelement für eine Menge aus, und geben Sie eine Zahl.

    Die **erweiterte** Preis Bezeichnung neu berechnet, um den neuen Wert anzuzeigen:

    > [!div class="mx-imgBorder"]
    > ![Geben Sie eine Menge aus, und zeigen Sie die erweiterten Preises](media/northwind-orders-canvas-part3/add-details-28.png)

## <a name="add-an-add-icon"></a>Ein Symbol hinzufügen "hinzufügen"

1. Auf der **einfügen** Registerkarte **Symbole** > **hinzufügen**:

    > [!div class="mx-imgBorder"]
    > ![Symbol zum Hinzufügen von einfügen](media/northwind-orders-canvas-part3/add-details-29.png)

    Das Symbol wird in der oberen linken Ecke des Bildschirms angezeigt.

    > [!div class="mx-imgBorder"]
    > ![Der Standardspeicherort der hinzufügen-Symbol](media/northwind-orders-canvas-part3/add-details-30.png)

1. Ändern der Größe und verschieben Sie dieses Symbol an den rechten Rand des Bereichs hellblaue und legen Sie dann auf des Symbol " **OnSelect** -Eigenschaft auf diese Formel:

    ```powerapps-comma
    Patch( 'Order Details';
        Defaults('Order Details');
        {
            Order: Gallery1.Selected;
            Product: ComboBox1.Selected;
            Quantity: Value(TextInput1.Text);
            'Unit Price': ComboBox1.Selected.'List Price'
        }
    );;
    Refresh( Orders );;
    Reset( ComboBox1 );;
    Reset( TextInput1 )
    ```

    > [!div class="mx-imgBorder"]
    > ![Legen Sie das Symbol "OnSelect-Eigenschaft](media/northwind-orders-canvas-part3/add-details-31.png)

    Im Allgemeinen die [ **Patch** ](functions/function-patch.md) Funktion aktualisiert, und Datensätze erstellt und bestimmten Argumenten in der folgenden Formel bestimmt die genauen Änderungen beschrieben, die die Funktion machen werden.

    - Das erste Argument gibt die Datenquelle (in diesem Fall die **Bestelldetails** Entity) in dem die Funktion zu aktualisieren oder erstellen Sie einen Eintrag.
    - Das zweite Argument gibt an, dass die Funktion mit den Standardwerten für einen Datensatz erstellt die **Bestelldetails** Entität sofern nicht anders in das dritte Argument angegeben.
    - Das dritte Argument gibt an, dass vier Spalten im neuen Datensatz Werte des Benutzers enthält.

      - Die **Reihenfolge** Spalte enthält die Anzahl von der Reihenfolge, in der Benutzer im Katalog der Reihenfolge ausgewählt.
      - Die **Produkt** Spalte enthält den Namen des Produkts, dass der Benutzer, der im Kombinationsfeld ausgewählt, die Produkte angezeigt.
      - Die **Menge** Spalte enthält den Wert, der der Benutzer in das Texteingabe-Feld angegeben.
      - Die **Unit Price** Spalte enthält den Listenpreis des Produkts, das der Benutzer für diese Bestelldetails ausgewählt.

    > [!NOTE]
    > Sie können Formeln, mit denen Daten aus einer beliebigen Spalte erstellen (in der **Bestellprodukte** Entität) für alle Produkte der app-Benutzer im Kombinationsfeld auswählt, die Produkte angezeigt. Wenn der Benutzer wählt einen Datensatz in die **Bestellprodukte** Entität nicht nur wird den Namen des Produkts, die in diesem im Kombinationsfeld angezeigt, sondern auch der Einzelpreis des Produkts in einer Bezeichnung angezeigt wird. Jede Suchwert in einer Canvas-app verweist auf einen vollständigen Datensatz, nicht nur einen Primärschlüssel.

    Die **aktualisieren** Funktion wird sichergestellt, dass die **Bestellungen** Entität spiegelt wider, den Datensatz, den Sie gerade hinzugefügt haben die **Bestelldetails** Entität. Die **zurücksetzen** Funktion löscht die Product, Quantity und Einzelpreis Daten, damit der Benutzer eine andere Details zur Bestellung für die gleiche Bestellung einfacher erstellen kann.

1. Drücken Sie F5, und wählen Sie dann die **hinzufügen** Symbol.

    Die Reihenfolge entspricht, die Informationen, die Sie angegeben haben:

    > [!div class="mx-imgBorder"]
    > ![Animation ein Details zur Bestellung hinzufügen](media/northwind-orders-canvas-part3/add-details.gif)

1. (optional) Fügen Sie ein anderes Element der Bestellung hinzu.

1. Drücken Sie Esc, um das Schließen des Vorschaumodus.

## <a name="remove-an-order-detail"></a>Entfernen Sie ein Order-detail

1. Wählen Sie in der Mitte des Bildschirms die Vorlage des Katalogs Details ein:

    > [!div class="mx-imgBorder"]
    > ![Wählen Sie Katalog: Vorlage](media/northwind-orders-canvas-part3/remove-details-01.png)

1. Auf der **einfügen** Registerkarte **Symbole** > **Papierkorb**:

    > [!div class="mx-imgBorder"]
    > ![Fügen Sie den Papierkorb-Symbol](media/northwind-orders-canvas-part3/remove-details-02.png)

    Das Papierkorb-Symbol wird in der oberen linken Ecke des Katalogs-Vorlage.

    > [!div class="mx-imgBorder"]
    > ![Der Standardspeicherort des Symbols](media/northwind-orders-canvas-part3/remove-details-03.png)

1. Ändern der Größe und verschieben Sie das Papierkorbsymbol auf die rechte Seite der Vorlage für die Details des Katalogs auf das Symbol des **OnSelect** -Eigenschaft auf diese Formel:

    ```powerapps-comma
    Remove( 'Order Details'; ThisItem );; Refresh( Orders )
    ```

    > [!div class="mx-imgBorder"]
    > ![Legen Sie das Symbol "OnSelect-Eigenschaft](media/northwind-orders-canvas-part3/remove-details-04.png)

    Während ich dies schreibe, kann nicht Entfernen eines Eintrags direkt über eine Beziehung, sodass die [ **entfernen** ](functions/function-remove-removeif.md) -Funktion entfernt einen Eintrag aus der verknüpften Entität direkt. **ThisItem** gibt an, zu entfernen, der Datensatz stammt aus den gleichen Datensatz im Detail-Katalog, in dem das Papierkorb-Symbol angezeigt wird.

    In diesem Fall der Vorgang verwendet zwischengespeicherte Daten, also die **aktualisieren** Funktion informiert die **Bestellungen** Entität aus, für die app, die eine der zugehörigen Entitäten geändert wurde.

1. Drücken Sie F5 zum Öffnen des Vorschaumodus, und wählen Sie dann das Papierkorbsymbol neben jeder **Bestelldetails** Datensatz, der aus dem Auftrag entfernt werden sollen.

1. Versuchen Sie es hinzufügen und Entfernen von verschiedenen Bestelldetails aus Ihre Bestellungen:

    > [!div class="mx-imgBorder"]
    > ![Animation hinzufügen und Entfernen von Auftragsdetails](media/northwind-orders-canvas-part3/remove-details.gif)

## <a name="in-conclusion"></a>Zusammenfassung

Zusammenfassend lässt sich sagen, haben Sie einen anderen Katalog zum Anzeigen von Auftragsdetails und Steuerelemente hinzufügen und entfernen eine Order-Details in der app hinzugefügt. Sie haben diese Elemente verwendet:

- Ein zweite Katalog-Steuerelement, das mit dem Order-Katalog über eine 1: n Beziehung verknüpft ist: **Gallery2.Items** = `Gallery1.Selected.'Order Details'`
- Eine n: 1 Beziehung aus der **Bestelldetails** Entität, die die **Bestellprodukte** Entität: `ThisItem.Product.'Product Name'` und `ThisItem.Product.Picture`
- Die **Auswahlmöglichkeiten** Funktion, um eine Liste der Produkte abzurufen: `Choices( 'Order Details'.Product' )`
- Die **ausgewählte** Eigenschaft eines Kombinationsfelds als die vollständige viele-zu-eins Datensatz verknüpfte: `ComboBox1.Selected.Picture` und `ComboBox1.Selected.'List Price'`
- Die **Patch** Funktion zum Erstellen einer **Bestelldetails** Datensatz: `Patch( 'Order Details'; Defaults( 'Order Details' ); ... )`
- Die **entfernen** Funktion zum Löschen einer **Bestelldetails** Datensatz: `Remove( 'Order Details'; ThisItem )`

Diese Reihe von Themen wurde eine kurze exemplarische Vorgehensweise zur Verwendung von Common Data Service-Beziehungen und Option wird in einer Canvas-app zu Lernzwecken. Bevor Sie jede app in der produktionsumgebung veröffentlichen, sollten Sie feldvalidierung, Fehlerbehandlung und viele andere Faktoren.
