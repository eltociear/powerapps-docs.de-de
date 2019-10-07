---
title: Erstellen einer Detail Galerie in einer Canvas-App | Microsoft-Dokumentation
description: Erstellen eines Detail Katalogs in einer Canvas-App zum Verwalten von Daten für Northwind Traders
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 04/25/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 7a975669d1e22289b7152b830808631992389a1f
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/07/2019
ms.locfileid: "71991630"
---
# <a name="create-a-detail-gallery-in-a-canvas-app"></a>Erstellen einer Detail Galerie in einer Canvas-App

Befolgen Sie die Schritt-für-Schritt-Anleitungen zum Erstellen eines Detail Katalogs in einer Canvas-App zum Verwalten von fiktiven Daten in der Datenbank Northwind Traders. Dieses Thema ist Teil einer Reihe, in der erläutert wird, wie eine Geschäfts-App für relationale Daten in Common Data Service erstellt wird. Um optimale Ergebnisse zu erzielen, sollten Sie sich diese Themen in dieser Sequenz ansehen:

1. [Erstellen Sie eine Order Gallery](northwind-orders-canvas-part1.md).
1. [Erstellen Sie ein Zusammenfassungs Formular](northwind-orders-canvas-part2.md).
1. Erstellen Sie eine Detail Galerie (**dieses Thema**).

> [!div class="mx-imgBorder"]
> ![definition von Bildschirm Bereichen @ no__t-1

## <a name="prerequisites"></a>Voraussetzungen

Bevor Sie mit diesem Thema beginnen, müssen Sie die-Datenbank wie zuvor in diesem Thema beschrieben installieren. Sie müssen dann entweder den Order Gallery und das Zusammenfassungs Formular erstellen oder die **Northwind Orders (Canvas)-BEGIN Part 3-** APP öffnen, die bereits diesen Katalog und dieses Formular enthält.

## <a name="create-another-title-bar"></a>Erstellen einer weiteren Titelleiste

1. Wählen Sie am oberen Bildschirmrand das [**Label**](controls/control-text-box.md) -Steuerelement aus, das als Titelleiste fungiert, kopieren Sie es durch Drücken von STRG + C, und fügen Sie es durch Drücken von STRG + V ein:

    > [!div class="mx-imgBorder"]
    > ![copy, und fügen Sie die Titelleiste @ no__t-1 ein.

1. Ändern Sie die Größe, und verschieben Sie die Kopie so, dass Sie direkt unter dem Zusammenfassungs Formular angezeigt wird.

1. Entfernen Sie den Text aus der Kopie auf eine der folgenden Arten:

    - Doppelklicken Sie auf den Text, um ihn auszuwählen, und drücken Sie dann ENTF.
    - Legen Sie die **Text** -Eigenschaft der Bezeichnung auf eine leere Zeichenfolge ( **""** ) fest.

    > [!div class="mx-imgBorder"]
    > ![entfernen Sie den Text aus der Titelleiste Copy @ no__t-1.

## <a name="add-a-gallery"></a>Einen Katalog hinzufügen

1. Fügen Sie ein Katalog [ **-Steuerelement mit einem**](controls/control-gallery.md) **leeren vertikalen** Layout ein:

    > [!div class="mx-imgBorder"]
    > ![hinzu fügen eines leeren vertikalen Katalogs @ no__t-1

    Der neue Katalog, in dem die Bestelldetails angezeigt werden, wird in der oberen linken Ecke angezeigt:

    > [!div class="mx-imgBorder"]
    > ![default Location of Order-Details Gallery @ no__t-1

1. Schließen Sie den Bereich **Daten** , und ändern Sie dann die Größe, und verschieben Sie die Detail Galerie in die untere rechte Ecke unterhalb der neuen Titelleiste:

    > [!div class="mx-imgBorder"]
    > ![final Location of Order-Details Gallery @ no__t-1

1. Legen Sie die **Items** -Eigenschaft der Detail Galerie auf diese Formel fest:

    ```powerapps-dot
    Gallery1.Selected.'Order Details'
    ```

    > [!div class="mx-imgBorder"]
    > ![legen Sie die Items-Eigenschaft der Detail Galerie @ no__t-1 fest.

    Wenn ein Fehler angezeigt wird, vergewissern Sie sich, dass die Order Gallery den Namen **Gallery1** hat (im Struktur **Ansichts** Bereich in der Nähe des linken Rands). Wenn dieser Katalog einen anderen Namen hat, benennen Sie ihn **Gallery1**um.

    Sie haben die beiden Galerien soeben verknüpft. Wenn der Benutzer eine Bestellung im Order Gallery auswählt, identifiziert diese Auswahl einen Datensatz in der Entität **Orders** . Wenn diese Reihenfolge ein oder mehrere Zeilen Elemente enthält, wird der Datensatz in der Entität **Orders** mit einem oder mehreren Datensätzen in der Entität **Order Details** verknüpft, und Daten aus diesen Datensätzen werden im Detail Katalog angezeigt. Dieses Verhalten spiegelt die 1: n-Beziehung wider, die für Sie zwischen den Entitäten **Orders** und **Order Details** erstellt wurde. Die von Ihnen angegebene Formel "durchläuft" diese Beziehung mithilfe der Punkt Notation:

    > [!div class="mx-imgBorder"]
    > ![1: n-Beziehung zwischen der Orders-Entität und der Order Details-Entität @ no__t-1

## <a name="show-product-names"></a>Produktnamen anzeigen

1. Wählen Sie im Detail Katalog auf **der Registerkarte Einfügen die Option Element hinzufügen aus** , um die Katalog Vorlage auszuwählen:

    > [!div class="mx-imgBorder"]
    > ![wählen Sie die Vorlage für die Detail Galerie @ no__t-1 aus.

    Stellen Sie sicher, dass Sie die Katalog Vorlage anstelle der Galerie selbst ausgewählt haben. Das Begrenzungsfeld sollte sich leicht innerhalb der Galerie Grenzen und wahrscheinlich kürzer als die Höhe des Katalogs befinden. Wenn Sie Steuerelemente in diese Vorlage einfügen, werden Sie für jedes Element im Katalog wiederholt.

1. Fügen Sie auf der Registerkarte **Einfügen** eine Bezeichnung in die Detail Galerie ein.

    Die Bezeichnung sollte in der Galerie angezeigt werden. Wenn dies nicht der Fall ist, versuchen Sie es noch mal. Achten Sie jedoch darauf, die Vorlage des Katalogs auszuwählen, bevor Sie die Bezeichnung einfügen.

    > [!div class="mx-imgBorder"]
    > ![dem Detail Katalog eine Bezeichnung hinzufügen @ no__t-1

1. Legen Sie die **Text** -Eigenschaft der neuen Bezeichnung auf diese Formel fest:

    ```powerapps-dot
    ThisItem.Product.'Product Name'
    ```

    Wenn kein Text angezeigt wird, wählen Sie den Pfeil für die **Reihenfolge 0901** am unteren Rand der Auftrags Galerie aus.

1. Ändern Sie die Größe der Bezeichnung so, dass der vollständige Text angezeigt wird:

    > [!div class="mx-imgBorder"]
    > ![show Product Name in Order Details @ no__t-1

    Dieser Ausdruck führt einen Datensatz in der **Order Details** -Entität aus. Der Datensatz wird in **thisitem** über eine n:1-Beziehung zur **Order Products** -Entität gespeichert:

    > [!div class="mx-imgBorder"]
    > ![n:1-Beziehung zwischen der Order Details-Entität und der Order Product-Entität @ no__t-1

    Das Feld " **Produkt Name** " (und andere Felder, die Sie verwenden möchten) werden extrahiert:

    > [!div class="mx-imgBorder"]
    > ![felder in der Order Products-Entität @ no__t-1

## <a name="show-product-images"></a>Produkt Images anzeigen

1. Fügen Sie auf der Registerkarte **Einfügen** ein [**Bild**](controls/control-image.md) Steuerelement in die Detail Galerie ein:

    > [!div class="mx-imgBorder"]
    > ![insert Image-Steuerelement @ no__t-1

1. Ändern Sie die Größe, und verschieben Sie das Bild und die Bezeichnung nebeneinander.

    > [!TIP]
    > Für eine differenzierte Steuerung der Größe und Position eines Steuer Elements können Sie die Größe ändern oder verschieben, ohne die Alt-Taste gedrückt zu halten, und dann die Größe des Steuer Elements ändern, während Sie die Alt-Taste gedrückt halten:

    > [!div class="mx-imgBorder"]
    > ![move Image-Steuerelement @ no__t-1

1. Legen Sie die **Image** -Eigenschaft des Bilds auf diese Formel fest:

    ```powerapps-dot
    ThisItem.Product.Picture
    ```

    Auch hier verweist der Ausdruck auf ein Produkt, das mit diesem Bestell Detail verknüpft ist und das anzuzeigende **Bildfeld** extrahiert.

    > [!div class="mx-imgBorder"]
    > ![show Product Image @ no__t-1

1. Verringern Sie die Höhe der Vorlage des Katalogs, sodass mehr als ein Datensatz für die **Bestelldetails** gleichzeitig angezeigt wird:

    > [!div class="mx-imgBorder"]
    > ![kürzen Sie die Vorlage des Katalogs @ no__t-1

## <a name="show-product-quantity-and-cost"></a>Produktmenge und Kosten anzeigen

1. Fügen Sie auf der Registerkarte **Einfügen** eine andere Bezeichnung in die Detail Galerie ein, und ändern Sie dann die Größe, und verschieben Sie die neue Bezeichnung rechts neben den Produktinformationen.

1. Legen Sie die **Text** -Eigenschaft der neuen Bezeichnung auf diesen Ausdruck fest:

    ```powerapps-dot
    ThisItem.Quantity
    ```

    Diese Formel Ruft Informationen direkt aus der Entität " **Order Details** " (keine Beziehung erforderlich) ab.

    > [!div class="mx-imgBorder"]
    > ![show Product Menge @ no__t-1 

1. Ändern Sie auf der Registerkarte **Startseite** die Ausrichtung dieses Steuer Elements in **Rechts**:

    > [!div class="mx-imgBorder"]
    > ![änderungsausrichtung @ no__t-1

1. Fügen Sie auf der Registerkarte **Einfügen** eine andere Bezeichnung in die Detail Galerie ein, und ändern Sie dann die Größe, und verschieben Sie die Bezeichnung nach rechts neben der Bezeichnung Menge.

1. Legen Sie die **Text** -Eigenschaft der neuen Bezeichnung auf diese Formel fest:

    ```powerapps-dot
    Text( ThisItem.'Unit Price', "[$-en-US]$ #,###.00" )
    ```

    Wenn Sie das Sprachtag ( **[$-en-US]** ) nicht einschließen, wird es basierend auf Ihrer Sprache und Region für Sie hinzugefügt. Wenn Sie ein anderes Sprachtag verwenden, sollten Sie den **$** direkt nach der schließenden eckigen Klammer ( **]** ) entfernen und dann Ihr eigenes Währungssymbol an dieser Position hinzufügen.

    > [!div class="mx-imgBorder"]
    > ![show Unit Price @ no__t-1

1. Ändern Sie auf der Registerkarte **Startseite** die Ausrichtung dieses Steuer Elements in **Rechts**:

    > [!div class="mx-imgBorder"]
    > ![änderungsausrichtung @ no__t-1

1. Fügen Sie auf der Registerkarte **Einfügen** ein weiteres Label-Steuerelement in die Detail Galerie ein, und ändern Sie dann die Größe, und verschieben Sie die neue Bezeichnung rechts neben dem Einheitspreis.

1. Legen Sie die **Text** -Eigenschaft der neuen Bezeichnung auf diese Formel fest:

    ```powerapps-dot
    Text( ThisItem.Quantity * ThisItem.'Unit Price', "[$-en-US]$ #,###.00" )
    ```

    Wenn Sie das Sprachtag ( **[$-en-US]** ) nicht einschließen, wird es auf Grundlage ihrer Sprache und Region für Sie hinzugefügt. Wenn das Tag anders ist, sollten Sie ein eigenes Währungssymbol anstelle des **$** direkt nach der schließenden eckigen Klammer ( **]** ) verwenden.

    > [!div class="mx-imgBorder"]
    > ![show Extended Price @ no__t-1

1. Ändern Sie auf der Registerkarte **Startseite** die Ausrichtung dieses Steuer Elements in **Rechts**:

    > [!div class="mx-imgBorder"]
    > ![änderungsausrichtung @ no__t-1

    Das Hinzufügen von Steuerelementen zum Detail Katalog ist nun abgeschlossen.

1. Wählen Sie im Struktur **Ansichts** Bereich die Option **Screen1** aus, um sicherzustellen, dass die Detail Galerie nicht mehr ausgewählt ist.

## <a name="add-text-to-the-new-title-bar"></a>Hinzufügen von Text zur neuen Titelleiste

1. Fügen Sie auf der Registerkarte **Einfügen** eine andere Bezeichnung auf dem Bildschirm ein:

    > [!div class="mx-imgBorder"]
    > ![insert-Bezeichnung @ no__t-1

1. Ändern Sie die Größe, und verschieben Sie die neue Bezeichnung über die Abbildungen der Produkte in der zweiten Titelleiste, und ändern Sie dann die Farbe des Texts auf der Registerkarte **Start** in weiß.

1. Doppelklicken Sie auf den Text der Bezeichnung, und geben Sie dann **Product**:

    > [!div class="mx-imgBorder"]
    > ![ändern Sie den Bezeichnungs Text in Product @ no__t-1.

1. Kopieren Sie die Produktbezeichnung, und fügen Sie Sie ein. ändern Sie dann die Größe, und verschieben Sie die Kopie oberhalb der Spalte Menge.

1. Doppelklicken Sie auf den Text der neuen Bezeichnung, und geben Sie dann **Menge**ein:

    > [!div class="mx-imgBorder"]
    > ![ändern Sie den Bezeichnungs Text in "Menge @ no__t-1".

1. Kopieren Sie die Mengen Bezeichnung, und fügen Sie Sie ein, und ändern Sie dann die Größe, und verschieben Sie die Kopie oberhalb der Einheitspreis Spalte.

1. Doppelklicken Sie auf den Text der neuen Bezeichnung, und geben Sie dann **Unit Price (uniprice**) ein:

    > [!div class="mx-imgBorder"]
    > ![ändern Sie den Bezeichnungs Text in Unit Price @ no__t-1.

1. Kopieren Sie die Bezeichnung Unit-Price, und fügen Sie Sie ein, und ändern Sie dann die Größe, und verschieben Sie die Kopie oberhalb der Spalte Extended Price.

1. Doppelklicken Sie auf den Text der neuen Bezeichnung, und geben Sie dann **erweitert**ein:

    > [!div class="mx-imgBorder"]
    > ![ändern von Bezeichnungs Text in Extended @ no__t-1

## <a name="display-order-totals"></a>Gesamtsumme der anzeigen

1. Verringern Sie die Höhe des Detail Katalogs, um Platz für die Bestell Summen am unteren Bildschirmrand zu schaffen:

    > [!div class="mx-imgBorder"]
    > ![verkürzt Order-Details Gallery @ no__t-1

1. Kopieren Sie die Titelleiste in der Mitte des Bildschirms, und verschieben Sie Sie dann an den unteren Rand des Bildschirms:

    > [!div class="mx-imgBorder"]
    > Titelleiste ![copy und kopieren an den unteren Rand @ no__t-1

1. Kopieren Sie die Product-Bezeichnung, und fügen Sie Sie aus der mittleren Titelleiste ein, und verschieben Sie die Kopie dann in die untere Titelleiste, und zwar direkt links neben der Spalte **Menge** .

1. Doppelklicken Sie auf den Text der neuen Bezeichnung, und geben Sie den folgenden Text ein:<br>**Bestell Summen:**

    > [!div class="mx-imgBorder"]
    > ![add-Bezeichnung für Bestell Summen @ no__t-1

1. Kopieren Sie die Bezeichnung Order-Summen, und fügen Sie Sie ein, und ändern Sie dann die Größe, und verschieben Sie die Kopie rechts neben die Bezeichnung Order-Total.

1. Legen Sie die **Text** -Eigenschaft der neuen Bezeichnung auf diese Formel fest:

    ```powerapps-dot
    Sum( Gallery1.Selected.'Order Details', Quantity )
    ```

    Diese Formel zeigt eine Delegierungs Warnung an, Sie können Sie jedoch ignorieren, da keine einzelne Bestellung mehr als 500 Produkte enthalten wird.

1. Legen Sie auf der Registerkarte **Start** Seite die Textausrichtung der neuen Bezeichnung auf **right**fest:

    > [!div class="mx-imgBorder"]
    > ![änderungsausrichtung @ no__t-1

1. Kopieren Sie dieses Bezeichnung-Steuerelement, fügen Sie es ein, und ändern Sie dann die Größe, und verschieben Sie die Kopie in die **Erweiterte**

1. Legen Sie die **Text** -Eigenschaft der Kopie auf diese Formel fest:

    ```powerapps-dot
    Text( Sum( Gallery1.Selected.'Order Details', Quantity * 'Unit Price' ), "[$-en-US]$ #,###.00" )
    ```

    Diese Formel zeigt eine Delegierungs Warnung an, Sie können Sie jedoch ignorieren, da keine einzelne Bestellung mehr als 500 Produkte enthalten wird.

    > [!div class="mx-imgBorder"]
    > ![zeigt Gesamtkosten der Bestellung an no__t-1

## <a name="add-space-for-new-details"></a>Platz für neue Details hinzufügen

In einem beliebigen Katalog können Sie Daten anzeigen, aber Sie können Sie nicht aktualisieren oder Datensätze hinzufügen. In der Detail Galerie fügen Sie einen Bereich hinzu, in dem der Benutzer einen Datensatz in der **Order Details** -Entität konfigurieren und diesen Datensatz in eine Bestellung einfügen kann.

1. Verringern Sie die Höhe des Detail Katalogs genug, um Platz für einen Bearbeitungsbereich mit einem einzelnen Element in diesem Katalog zu schaffen.

    In diesem Bereich fügen Sie Steuerelemente hinzu, sodass der Benutzer ein Bestell Detail hinzufügen kann:

    > [!div class="mx-imgBorder"]
    > ![kürzen der Detail Galerie @ no__t-1

1. Fügen Sie auf der Registerkarte **Einfügen** eine Bezeichnung ein, und ändern Sie dann die Größe, und verschieben Sie Sie in die Detail Galerie.

    > [!div class="mx-imgBorder"]
    > ![insert a Label @ no__t-1

1. Doppelklicken Sie auf den Text der neuen Bezeichnung, und drücken Sie dann ENTF.

1. Legen Sie auf der Registerkarte **Startseite** die **Füllfarbe** der neuen Bezeichnung auf **LightBlue**fest:

    > [!div class="mx-imgBorder"]
    > ![füll Füllung ändern in hellblau @ no__t-1

## <a name="add-the-order-details-data-source"></a>Hinzufügen der Datenquelle "Order Details"

1. Wählen Sie auf der Registerkarte **Ansicht** die Option **Datenquellen**aus, und wählen Sie dann im Bereich **Daten** die Option **Datenquelle hinzufügen** aus:

    > [!div class="mx-imgBorder"]
    > ![add Data Source @ no__t-1

1. Wählen Sie **Common Data Service**aus:

    > [!div class="mx-imgBorder"]
    > ![select Common Data Service @ no__t-1

1. Geben Sie am oberen Rand des **Daten** Bereichs im Suchfeld **Order** ein, aktivieren Sie das Kontrollkästchen **Order Details** , und wählen Sie dann am unteren Rand des Fensters **verbinden** aus:

    > [!div class="mx-imgBorder"]
    > ![geben Sie Order Details-Entität @ no__t-1 an.

    Sie haben der APP soeben eine weitere Datenquelle hinzugefügt:

    > [!div class="mx-imgBorder"]
    > ![liste der Datenquellen @ no__t-1

    Sie müssen diese Datenquelle hinzufügen, da die APP zwar eine 1: n-Beziehung lesen kann, aber die APP kann noch keine Änderungen zurückschreiben. Die APP muss direkt mit der zugehörigen Entität Änderungen vornehmen.

1. Schließen Sie den **Daten** Bereich.

## <a name="select-a-product"></a>Produkt auswählen

1. Wählen Sie auf der Registerkarte **Einfügen** die Option Steuer **Elemente** > -Kombinations**Feld**aus:

    > [!div class="mx-imgBorder"]
    > Kombinations Feld "![insert" @ no__t-1

    Das Kombinations [**Feld**](controls/control-combo-box.md) -Steuerelement wird in der linken oberen Ecke angezeigt.

1. Legen Sie die **Items** -Eigenschaft des Kombinations Felds auf diese Formel fest:

    ```powerapps-dot
    Choices( 'Order Details'.Product )
    ```

    > [!div class="mx-imgBorder"]
    > ![legen Sie die Items-Eigenschaft des Kombinations Felds @ no__t-1 fest.

    Die [**Auswahl**](functions/function-choices.md) Funktion gibt eine Tabelle mit allen möglichen Werten für das Feld " **Product** " in der Entität " **Order Details** " zurück. Dieses Feld ist eine Suche in einer n:1-Beziehung, sodass die **Auswahl** alle Datensätze in der Entität " **Order Products** " zurückgibt.

    > [!NOTE]
    > Sie können auch **Optionen** mit Options Sätzen verwenden, um eine Tabelle mit allen Optionen zurückzugeben. Diese Vorgehensweise wurde von den Schritten nicht erwähnt, aber Sie haben Sie bereits verwendet, als Sie das Kombinations Feld hinzugefügt haben, das den **Auftrags Status** im Zusammenfassungs Formular anzeigt.

1. Öffnen Sie im Bereich **Daten** die **primäre Textliste** , und wählen Sie dann **nwind_productname**aus. 

1. Öffnen Sie die Liste **searchfield** , und wählen Sie dann **nwind_productname**aus.

    Sie geben den logischen Namen an, da der **Daten** Bereich in diesem Fall noch keine anzeigen Amen unterstützt:

    > [!div class="mx-imgBorder"]
    > ![legen Sie den Primärtext für das Kombinations Feld @ no__t-1 fest.

1. Schließen Sie den **Daten** Bereich.

1. Scrollen Sie in der Nähe des rechten Rands auf der Registerkarte **Eigenschaften** nach unten, deaktivieren Sie **Mehrfachauswahl zulassen**, und stellen Sie sicher, dass **Suche zulassen** aktiviert ist:

    > [!div class="mx-imgBorder"]
    > ![Die Mehrfachauswahl deaktivieren und Suche aktivieren @ no__t-1

1. Ändern Sie die Größe, und verschieben Sie das Kombinations Feld in den hellblauen Bereich, direkt unterhalb der Spalte Product-Name in der Detail Galerie:

    > [!div class="mx-imgBorder"]
    > Kombinations Feld "![move" @ no__t-1

    In diesem Kombinations Feld gibt der Benutzer einen Datensatz in der **Product** -Entität für den **Bestell Details** -Datensatz an, den die App erstellt.

1. Wenn Sie die Alt-Taste gedrückt halten, wählen Sie den Pfeil nach unten aus.

    > [!TIP]
    > Wenn Sie die Alt-Taste gedrückt halten, können Sie mit Steuerelementen in PowerApps Studio interagieren, ohne den Vorschaumodus zu öffnen.

1. Wählen Sie in der Liste der angezeigten Produkte ein Produkt aus:

    > [!div class="mx-imgBorder"]
    > ![wählen Sie im Kombinations Feld @ no__t-1 ein Produkt aus.

## <a name="add-a-product-image"></a>Hinzufügen eines Produkt Images

1. Wählen Sie auf der Registerkarte **Einfügen** die Option **Medien** > **Bild**aus:

    > [!div class="mx-imgBorder"]
    > ![insert Image-Steuerelement @ no__t-1

    Das [**Bild**](controls/control-image.md) Steuerelement wird in der oberen linken Ecke angezeigt:

    > [!div class="mx-imgBorder"]
    > ![standard Speicherort des Image-Steuer Elements @ no__t-1

1. Ändern Sie die Größe, und verschieben Sie das Bild in den hellblauen Bereich unter den anderen Produktbildern und neben dem Kombinations Feld.

1. Legen Sie für die **Image** -Eigenschaft des Bilds Folgendes fest:

    ```powerapps-dot
    ComboBox1.Selected.Picture
    ```

    > [!div class="mx-imgBorder"]
    > ![legen Sie die Image-Eigenschaft des Bilds @ no__t-1 fest.

    Sie verwenden denselben Trick, den Sie zum Anzeigen des Mitarbeiter Bilds im Zusammenfassungs Formular verwendet haben. Die **ausgewählte** Eigenschaft des Kombinations Felds gibt den gesamten Datensatz eines beliebigen Produkts zurück, das der Benutzer auswählt, einschließlich des **Bilds** .

## <a name="add-a-quantity-box"></a>Feld "Menge hinzufügen"

1. Wählen Sie auf der Registerkarte **Einfügen** die Option **Text** > **Texteingabe**:

    > [!div class="mx-imgBorder"]
    > ![add Text-Input Box @ no__t-1

    Das [**Text Eingabe**](controls/control-text-input.md) -Steuerelement wird in der oberen linken Ecke angezeigt:

    > [!div class="mx-imgBorder"]
    > ![default Location of Text-Input Box @ no__t-1

1. Ändern Sie die Größe, und verschieben Sie das Texteingabefeld nach rechts neben dem Kombinations Feld unter der Spalte Menge in der Detail Galerie:

    > [!div class="mx-imgBorder"]
    > ![größe ändern und Text verschieben-Eingabefeld @ no__t-1

    Wenn Sie dieses Texteingabefeld verwenden, gibt der Benutzer das Feld " **Menge** " des **Datensatzes "Bestell Details** " an.

1. Legen Sie die **default** -Eigenschaft dieses Steuer Elements auf **""** fest:

    > [!div class="mx-imgBorder"]
    > ![legen Sie die * * Default * *-Eigenschaft des Texteingabe Felds @ no__t-1 fest.

1. Legen Sie auf der Registerkarte **Home** die Textausrichtung dieses Steuer Elements auf **right**fest:

    > [!div class="mx-imgBorder"]
    > ![änderungsausrichtung @ no__t-1

## <a name="show-the-unit-and-extended-prices"></a>Anzeigen der Einheit und der erweiterten Preise

1. Fügen Sie auf der Registerkarte **Einfügen** ein **Label** -Steuerelement ein.

    Die Bezeichnung wird in der oberen linken Ecke des Bildschirms angezeigt:

    > [!div class="mx-imgBorder"]
    > ![insert a Label @ no__t-1

1. Ändern Sie die Größe, und verschieben Sie die Bezeichnung auf die Rechte Seite des Texteingabe-Steuer Elements, und legen Sie die **Text** -Eigenschaft der Bezeichnung auf diese Formel fest:

    ```powerapps-dot
    Text( ComboBox1.Selected.'List Price', "[$-en-US]$ #,###.00" )
    ```

    > [!div class="mx-imgBorder"]
    > ![legen Sie die Text-Eigenschaft der Bezeichnung @ no__t-1 fest.

    Dieses Steuerelement zeigt den **Listenpreis** aus der Entität " **Bestell Produkte** " an. Durch diesen Wert wird das Feld " **Unit Price** " im Datensatz " **Order Details** " bestimmt.

    > [!NOTE]
    > In diesem Szenario ist der Wert schreibgeschützt, aber andere Szenarien erfordern möglicherweise, dass der App-Benutzer ihn ändert. Verwenden Sie in diesem Fall ein **Text Eingabe** -Steuerelement, und legen Sie dessen **Standard** Eigenschaft auf **List Price**fest.

1. Legen Sie auf der Registerkarte **Start** Seite die Textausrichtung der Bezeichnung List-Price auf **right**fest:

    > [!div class="mx-imgBorder"]
    > ![änderungsausrichtung @ no__t-1

1. Kopieren Sie die Bezeichnung List-Price, und fügen Sie Sie ein, und ändern Sie dann die Größe, und verschieben Sie die Kopie nach rechts neben der Bezeichnung List-Price.

1. Legen Sie die **Text** -Eigenschaft der neuen Bezeichnung auf diese Formel fest:

    ```powerapps-dot
    Text( Value(TextInput1.Text) * ComboBox1.Selected.'List Price', "[$-en-US]$ #,###.00" )
    ```

    > [!div class="mx-imgBorder"]
    > ![legen Sie die Text-Eigenschaft der neuen Bezeichnung @ no__t-1 fest.

    Dieses Steuerelement zeigt den erweiterten Preis basierend auf der Menge an, die der App-Benutzer angegeben hat, und dem Listenpreis des Produkts, das der App-Benutzer ausgewählt hat. Es handelt sich lediglich um eine Informations Meldung für den Benutzer der app.

1. Doppelklicken Sie auf das Texteingabe-Steuerelement für Menge, und geben Sie dann eine Zahl ein.

    Die **Erweiterte** Preis Bezeichnung wird neu berechnet, um den neuen Wert anzuzeigen:

    > [!div class="mx-imgBorder"]
    > ![geben Sie eine Menge an, und zeigen Sie den erweiterten Preis @ no__t-1 an.

## <a name="add-an-add-icon"></a>Hinzufügen eines Symbols

1. Wählen Sie auf der Registerkarte **Einfügen** die Option **Symbole**aus  > **Hinzufügen**:

    > [!div class="mx-imgBorder"]
    > ![insert Add Icon @ no__t-1

    Das Symbol wird in der oberen linken Ecke des Bildschirms angezeigt.

    > [!div class="mx-imgBorder"]
    > ![standard Speicherort des Add-Symbols @ no__t-1

1. Ändern Sie die Größe, und verschieben Sie dieses Symbol an den rechten Rand des hellblauen Bereichs, und legen Sie dann die **onselect** -Eigenschaft des Symbols auf die folgende Formel fest:

    ```powerapps-dot
    Patch( 'Order Details',
        Defaults('Order Details'),
        {
            Order: Gallery1.Selected,
            Product: ComboBox1.Selected,
            Quantity: Value(TextInput1.Text),
            'Unit Price': ComboBox1.Selected.'List Price'
        }
    );
    Refresh( Orders );
    Reset( ComboBox1 );
    Reset( TextInput1 )
    ```

    > [!div class="mx-imgBorder"]
    > ![legen Sie die onselect-Eigenschaft des Symbols @ no__t-1 fest.

    Im Allgemeinen werden von der [**Patch**](functions/function-patch.md) -Funktion Datensätze aktualisiert und erstellt, und die spezifischen Argumente in dieser Formel bestimmen die genauen Änderungen, die die Funktion durchführt.

    - Mit dem ersten Argument wird die Datenquelle (in diesem Fall die Entität **Order Details** ) angegeben, in der die Funktion einen Datensatz aktualisiert oder erstellt.
    - Das zweite Argument gibt an, dass die Funktion einen Datensatz mit den Standardwerten für die **Order Details** -Entität erstellt, sofern im dritten Argument nicht anders angegeben.
    - Das dritte Argument gibt an, dass vier Spalten im neuen Datensatz Werte vom Benutzer enthalten.

      - Die Spalte **Order** enthält die Nummer der Reihenfolge, die der Benutzer im Order Gallery ausgewählt hat.
      - Die Spalte **Product** enthält den Namen des Produkts, das der Benutzer im Kombinations Feld, in dem Produkte angezeigt werden, ausgewählt hat.
      - Die Spalte **Menge** enthält den Wert, der vom Benutzer im Feld Texteingabe angegeben wurde.
      - Die Spalte **Einheitspreis** enthält den Listenpreis des Produkts, das der Benutzer für dieses Bestell Detail ausgewählt hat.

    > [!NOTE]
    > Sie können Formeln erstellen, die Daten aus beliebigen Spalten (in der Entität **Order Products** ) für das Produkt verwenden, das der App-Benutzer im Kombinations Feld auswählt, in dem Produkte angezeigt werden. Wenn der Benutzer einen Datensatz in der Entität " **Bestell Produkte** " auswählt, wird nicht nur der Name des Produkts in diesem Kombinations Feld angezeigt, sondern auch der Einzelpreis des Produkts in einer Bezeichnung. Jeder Such Wert in einer Canvas-App verweist auf einen vollständigen Datensatz, nicht nur auf einen Primärschlüssel.

    Die **Refresh** -Funktion stellt sicher, dass die **Orders** -Entität den Datensatz widerspiegelt, den Sie soeben der Entität **Order Details** hinzugefügt haben. Mit der **Reset** -Funktion werden die Daten für Produkt, Menge und Einheitspreis gelöscht, sodass der Benutzer auf einfache Weise weitere Bestelldetails für dieselbe Bestellung erstellen kann.

1. Drücken Sie F5, und wählen Sie dann das Symbol **Hinzufügen** aus.

    Die von Ihnen angegebenen Informationen werden in der Reihenfolge angezeigt:

    > [!div class="mx-imgBorder"]
    > ![animation zum Hinzufügen eines Bestelldetails @ no__t-1

1. optionale Fügen Sie der Bestellung ein weiteres Element hinzu.

1. Drücken Sie ESC, um den Vorschaumodus zu schließen.

## <a name="remove-an-order-detail"></a>Entfernen eines Bestelldetails

1. Wählen Sie in der Mitte des Bildschirms die Vorlage der Detail Galerie aus:

    > [!div class="mx-imgBorder"]
    > ![select Gallery Template @ no__t-1

1. Wählen Sie auf der Registerkarte **Einfügen** die Option **Symbole** > **Papierkorb**aus:

    > [!div class="mx-imgBorder"]
    > ![insert-Papierkorb Symbol @ no__t-1

    Das Papierkorb Symbol wird in der oberen linken Ecke der Galerie Vorlage angezeigt.

    > [!div class="mx-imgBorder"]
    > ![default Location of Icon @ no__t-1

1. Ändern Sie die Größe, und verschieben Sie das Papierkorb Symbol auf die Rechte Seite der Detail Galerie Vorlage, und legen **Sie die onselect** -Eigenschaft des Symbols auf die folgende Formel fest:

    ```powerapps-dot
    Remove( 'Order Details', ThisItem ); Refresh( Orders )
    ```

    > [!div class="mx-imgBorder"]
    > ![legen Sie die onselect-Eigenschaft des Symbols @ no__t-1 fest.

    Zum Zeitpunkt der Erstellung dieses Artikels können Sie einen Datensatz nicht direkt aus einer Beziehung entfernen, daher entfernt die [**Remove**](functions/function-remove-removeif.md) -Funktion einen Datensatz direkt aus der verknüpften Entität. **Thisitem** gibt den zu entfernenden Datensatz aus demselben Datensatz in der Detail Galerie an, in dem das Papierkorb Symbol angezeigt wird.

    Der Vorgang verwendet wiederum zwischengespeicherte Daten, sodass die **Aktualisierungs** Funktion der **Orders** -Entität mitteilt, dass die APP eine der zugehörigen Entitäten geändert hat.

1. Drücken Sie F5, um den Vorschaumodus zu öffnen, und wählen Sie dann das Papierkorb Symbol neben jedem Datensatz mit **Bestell Details** aus, den Sie aus der Bestellung entfernen möchten.

1. Versuchen Sie, verschiedene Bestelldetails in Ihren Bestellungen hinzuzufügen und zu entfernen:

    > [!div class="mx-imgBorder"]
    > ![animation zum Hinzufügen und Entfernen von Bestelldetails @ no__t-1

## <a name="in-conclusion"></a>Schlussfolgerung

Zur Wiederholung haben Sie einen weiteren Katalog hinzugefügt, um Bestelldetails und Steuerelemente zum Hinzufügen und Entfernen von Bestelldetails in der APP anzuzeigen. Sie haben diese Elemente verwendet:

- Ein zweites Katalog Steuerelement, das über eine 1: n-Beziehung mit der Order Gallery verknüpft ist: **Wenn gallery2. Items** =  @ no__t-2
- Eine n:1-Beziehung zwischen der Entität " **Order Details** " und der Entität " **Order Products** ": `ThisItem.Product.'Product Name'` und `ThisItem.Product.Picture`
- Die **Auswahl** Funktion zum erhalten einer Liste von Produkten: `Choices( 'Order Details'.Product' )`
- Die **ausgewählte** Eigenschaft eines Kombinations Felds als kompletter n:1-Datensatz: `ComboBox1.Selected.Picture` und `ComboBox1.Selected.'List Price'`
- Die **Patch** -Funktion zum Erstellen eines **Auftrags Detail** Datensatzes: `Patch( 'Order Details', Defaults( 'Order Details' ), ... )`
- Die **Remove** -Funktion zum Löschen eines **Order Details-Daten** Satzes: `Remove( 'Order Details', ThisItem )`

Diese Themenreihe war eine kurze exemplarische Vorgehensweise zur Verwendung von Common Data Service Beziehungen und Options Sätzen in einer Canvas-APP zu Schulungszwecken. Bevor Sie eine APP für die Produktion freigeben, sollten Sie die Feld Validierung, die Fehlerbehandlung und viele andere Faktoren berücksichtigen.
