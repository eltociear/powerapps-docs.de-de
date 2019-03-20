---
title: Beziehen und Verknüpfung mit Funktionen | Microsoft-Dokumentation
description: Referenzinformationen Sie, einschließlich Syntax und Beispielen, für die Relate und Verknüpfung mit Funktionen in PowerApps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 01/22/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: c50b2452829f0878c40ccf5f2e47010596bc0b7b
ms.sourcegitcommit: eef2d6d9a9c7f5c8a44b9734817f59dc0eac3ecf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/07/2019
ms.locfileid: "57801593"
---
# <a name="relate-and-unrelate-functions-in-powerapps"></a>Beziehen Sie und Verknüpfung mit Funktionen in PowerApps

Beziehen Sie und Verknüpfung mit Datensätzen von zwei Entitäten über eine 1: n- oder m: n Beziehung.

## <a name="description"></a>Beschreibung

Die **Relate** -Funktion verknüpft den zwei Datensätzen über eine 1: n- oder m: n Beziehung in Common Data Service (CDS) für Apps. Die **Unrelate** Funktion kehrt den Prozesses um, und entfernt den Link.

Für 1: n Beziehungen hat die viele Entität ein Fremdschlüsselfeld, verweist auf einen Datensatz, der eine Entität. **Im Zusammenhang** setzt dieses Feld auf einen bestimmten Datensatz, der eine Entität zeigen während **Unrelate** setzt dieses Feld auf *leere*. Wenn das Feld bereits festgelegt ist **Relate** wird aufgerufen, wird der vorhandene Link zugunsten von neuen Link verloren gehen. Sie können dieses Feld auch festlegen, mit der [ **Patch** ](function-patch.md) Funktion oder ein **[Bearbeitungsformular](../controls/control-form-detail.md)** Steuerelement; verwenden Sie nicht benötigen die **Relate**  Funktion.

Für m: n Beziehungen behält das System, das die Datensätze verknüpft eine ausgeblendete Jointabelle. Diese Jointabelle kann nicht direkt zugegriffen werden; Lesen Sie nur über eine 1: n Projektion und festgelegt werden kann die **Relate** und **Unrelate** Funktionen. Keine verknüpften Entität hat einen Fremdschlüssel.

Die Daten für die Entität, die Sie im ersten Argument angeben, werden entsprechend die Änderung aktualisiert werden, aber die Daten für die Entität, die Sie im zweiten Argument angeben, wird nicht. Dass die Daten manuell sein müssen aktualisiert werden, mit der **[aktualisieren](function-refresh.md)** Funktion, um das Ergebnis des Vorgangs anzuzeigen.

Diese Funktionen nicht erstellen oder Löschen eines Datensatzes. Klicken sie nur verknüpfen oder Verknüpfung mit zwei Datensätze, die bereits vorhanden.

Sie können diese Funktionen nur in [verhaltensformeln](../working-with-formulas-in-depth.md).

> [!NOTE]
> Diese Funktionen sind Teil der eine Funktion der Vorschauversion, und ihr Verhalten ist nur verfügbar, wenn die **relationale Daten, Optionssätze und weitere neue Features für CDS** aktiviert ist. Dies ist eine Einstellung auf app-Ebene, die standardmäßig für neue apps aktiviert ist. Um dieses Feature-Switch zu suchen, öffnen Sie die **Datei** , wählen Sie im Menü **Anwendungseinstellungen**, und wählen Sie dann **Erweiterte Einstellungen**. Wir sind sehr an Ihrem Feedback interessiert und würden uns freuen, wenn Sie uns in den [PowerApps-Communityforen](https://powerusers.microsoft.com/t5/Expressions-and-Formulas/bd-p/How-To) Ihre Meinung mitteilen würden.

## <a name="syntax"></a>Syntax

**Relate**( *Entity1RelatedTable*, *Entity2Record* )

* *Entity1RelatedTable* : erforderlich. Einen Datensatz der *' Entity1 '*, die Tabelle der *Entity2* Datensätze, die über eine 1: n- oder m: n Beziehung verknüpft.
* *Entity2Record* : erforderlich. Die *Entity2* Datensatz der Beziehung hinzu.

**Verknüpfung mit**( *Entity1RelatedTable*, *Entity2Record* )

* *Entity1RelatedTable* : erforderlich. Einen Datensatz der *' Entity1 '*, die Tabelle der *Entity2* Datensätze, die über eine 1: n- oder m: n Beziehung verknüpft.
* *Entity2Record* : erforderlich. Die *Entity2* Datensatz aus der Beziehung zu entfernen.

## <a name="examples"></a>Beispiele

Erwägen Sie eine **Produkte** Entität mit dem die folgenden Beziehungen, wie in der [PowerApps-Portal-Entity-Viewer](../../common-data-service/create-edit-entities-portal.md):

| Anzeigename der Beziehung | Verknüpfte Entität | Beziehungstyp |
| --- | --- |
| Produkt-Reservierung | Reservierung | 1: n |
| Produkt &harr; wenden Sie sich an | Kontakt | M: n |

**Produkte** und **Reservierungen** beziehen sich über eine 1: N-Beziehung.  Verbinden Sie den ersten Datensatz der **Reservierungen** Entität mit den ersten Datensatz der **Produkte** Entität:

`Relate( First( Products ).Reservations, First( Reservations ) )`

So entfernen Sie die Beziehung zwischen diesen Datensätzen:

`Unrelate( First( Products ).Reservations, First( Reservations ) )`

Zu keinem Zeitpunkt haben wir erstellen oder entfernen "oder" einen Datensatz, der nur die Beziehung zwischen den Datensätzen wurde geändert.

**Produkte** und **Kontakte** beziehen sich durch eine m: N-Beziehung.  Verbinden Sie den ersten Datensatz der **Kontakte** Entität mit den ersten Datensatz der **Produkte** Entität:

`Relate( First( Products ).Contacts, First( Contacts ) )`

Als m: N Beziehungen sind symmetrisch, es könnte auch dies getan haben in die entgegengesetzte Richtung:

`Relate( First( Contacts ).Products, First( Products ) )`

So entfernen Sie die Beziehung zwischen diesen Datensätzen:

`Unrelate( First( Products ).Contacts, First( Contacts ) )`

oder:

`Unrelate( First( Contacts ).Products, First( Products ) )`

Die exemplarische Vorgehensweise, folgt, wird genau diese Vorgänge für diese Entitäten, die mit einer app mit **Katalog** und **Kombinationsfeld** Steuerelementen zum Auswählen der betroffenen Datensätze.

Diese Beispiele richten sich nach den Beispieldaten, die in Ihrer Umgebung installiert wird. Entweder [erstellen eine testumgebung, einschließlich Beispieldaten](../../model-driven-apps/overview-model-driven-samples.md#get-sample-apps) oder [Hinzufügen von Beispieldaten zu einer vorhandenen Umgebung](../../model-driven-apps/overview-model-driven-samples.md#install-or-uninstall-sample-data).

### <a name="one-to-many"></a>1: n

#### <a name="relate-function"></a>**Im Zusammenhang** Funktion

Erstellen Sie zunächst eine einfache app, um anzuzeigen, und weisen Sie die Reservierungen, die mit einem Produkt zugeordnet sind.

1. Erstellen Sie eine [Tablet-app mit leerer App](../data-platform-create-app-scratch.md).

1. Auf der **Ansicht** Registerkarte **Datenquellen**.

1. In der **Daten** wählen Sie im Bereich **Datenquelle hinzufügen** > **Common Data Service** > **Produkte**  >  **Verbinden**.  

    Die Products-Entität stammt die Beispieldaten oben geladen.

     ![Fügen Sie der Products-Entität als eine Datenquelle hinzu.](media/function-relate-unrelate/products-connect.png)

1. Auf der **einfügen** hinzu ein Leerzeichen vertikal **[Katalog](../controls/control-gallery.md)** Steuerelement.

1. Stellen Sie sicher, dass das Steuerelement, das Sie gerade hinzugefügt haben, mit dem Namen wird **Gallery1**, und klicken Sie dann verschieben, und passen Sie es die linke Seite des Bildschirms zu füllen.

1. Auf der **Eigenschaften** Registerkarte **Gallery1**des **Elemente** Eigenschaft **Produkte** und die zugehörige **Layout** auf **Gruppenbild und der**.

    ![Konfigurieren von ProductsGallery](media/function-relate-unrelate/products-gallery.png)

1. In **Gallery1**, sicher, dass die **Bezeichnung** -Steuerelement heißt **Title1**, und legen Sie dann die **Text** Eigenschaft  **ThisItem.Name**.

    ![Konfigurieren Sie die Bezeichnung in Gallery1](media/function-relate-unrelate/products-title.png)

1. Wählen Sie den Bildschirm, um zu vermeiden, das das nächste Element einfügen **Gallery1**.  Hinzufügen einer zweiten Leerzeichen vertikal **Katalog** steuern, und stellen Sie sicher, dass sie den Namen **Gallery2**.

    **Gallery2** zeigt die Reservierungen für den der Benutzer im wählt Produkt **Gallery1**.

1. Verschiebe und verkleinere **Gallery2** zum Ausfüllen der oberen rechten Quadranten des Bildschirms.

1. (optional) Fügen Sie den blauen **Bezeichnung** Steuerelement oben **Gallery2**, wie in die folgenden Abbildung dargestellt.

1. Legen Sie in der Bearbeitungsleiste die **Elemente** Eigenschaft **Gallery2** zu **Gallery1.Selected.Reservations**.

    ![Konfigurieren Sie Gallery2-Elemente](media/function-relate-unrelate/reservations-gallery.png)

1. Legen Sie im Eigenschaftenbereich **Gallery2**des **Layout** zu **Titel**.

    ![Gallery2 Layout konfigurieren](media/function-relate-unrelate/reservations-gallery-right.png)

1. In **Gallery2**, Hinzufügen einer **[Kombinationsfeld](../controls/control-combo-box.md)** steuern, stellen Sie sicher, dass sie den Namen **ComboBox1**, und klicken Sie dann Verschiebe und verkleinere sie, um die Blockierung zu vermeiden der Bei anderen Steuerelementen in **Gallery2**.

1. Auf der **Eigenschaften** Registerkarte **ComboBox1**des **Elemente** Eigenschaft **Produkte**.

    ![Festlegen der Items-Eigenschaft auf Produkte](media/function-relate-unrelate/reservations-combo-right.png)

1. Scrollen Sie in der **Eigenschaften** Registerkarte, und legen Sie **ComboBox1**des **Mehrfachauswahl zulassen** Eigenschaft **aus**.

    ![Ermöglichen die Mehrfachauswahl auf Off](media/function-relate-unrelate/reservations-singleselect-right.png)

1. Legen Sie in der Bearbeitungsleiste **ComboBox1**des **DefaultSelectedItems** Eigenschaft **ThisItem. "Produkt reserviert"**.

    ![Legen Sie DefaultSelectedItems für ReserveCombo](media/function-relate-unrelate/reservations-combo.png)

1. In **Gallery2**legen **NextArrow2**des **OnSelect** -Eigenschaft auf diese Formel:

    ```powerapps-dot
    Relate( ComboBox1.Selected.Reservations, ThisItem )
    ```

    Wenn der Benutzer dieses Symbol auswählt, ändert sich die aktuelle Reservierung für das Produkt, die der Benutzer im ausgewählt **ComboBox1**.

    ![Konfigurieren von NextArrow2](media/function-relate-unrelate/reservations-relate.png)

1. Drücken Sie F5, um die app im Vorschaumodus zu testen.

Mit dieser app kann Benutzer eine Reservierung ein Produkt in eine andere verschieben. Der Benutzer kann für eine Reservierung auf ein Produkt, in ein anderes Produkt auswählen **ComboBox1** und wählen Sie dann **NextArrow2** so ändern Sie diese Reservierung.

![Veranschaulichen der Relate-Funktion in 1: n app](media/function-relate-unrelate/reservations-reassign.gif)

#### <a name="unrelate-function"></a>**Verknüpfung mit** Funktion

An diesem Punkt können Sie die Beziehung zwischen den Datensätzen in eine andere verschieben, aber Sie können die Beziehung nicht vollständig entfernen. Sie können die **Unrelate** Funktion, um einen Datensatz für die Reservierung von einem Produkt zu trennen.

1. Auf der **Ansicht** Registerkarte **Datenquellen**.

1. In der **Daten** wählen Sie im Bereich **Datenquelle hinzufügen** > **Common Data Service** > **Reservierungen**  >  **Verbinden**.

1. In **Gallery2**legen die **OnSelect** Formel zum **NextArrow2** auf diese Formel:

    ```powerapps-dot
    If( IsBlank( ComboBox1.Selected ),
        Unrelate( Gallery1.Selected.Reservations, ThisItem ),
        Relate( ComboBox1.Selected.Reservations, ThisItem )
    );
    Refresh( Reservations )
    ```
    ![Richtige Symbol "konfigurieren"](media/function-relate-unrelate/reservations-relate-unrelate.png)

1. Kopie **Gallery2** in die Zwischenablage, und drücken STRG + C.

1. Fügen Sie ein Duplikat eines **Gallery2** auf den gleichen Bildschirm durch Drücken von STRG + V, und verschieben Sie sie an der unteren rechten Quadranten des Bildschirms.

1. (optional) Wenn Sie eine Bezeichnung, die oben genannten hinzugefügt **Gallery2**, wiederholen Sie die vorherigen beiden Schritte für diese Bezeichnung.

1. Stellen Sie sicher, dass das Duplikat der **Gallery2** heißt **Gallery2_1**, und legen Sie dann die **Elemente** -Eigenschaft auf diese Formel:

    ```powerapps-dot
    Filter( Reservations, IsBlank( 'Product Reservation' ) )
    ```

    Es wird eine delegierungswarnung, aber es nicht relevant, mit der geringeren Menge an Daten in diesem Beispiel.

    ![Festlegen der Items-Eigenschaft des Gallery2_1](media/function-relate-unrelate/reservations-lost.png)

Mit diesen Änderungen, können Benutzer die Auswahl im Löschen **ComboBox1** für einen Kontakt, wenn diese Person ein Produkt reserviert noch nicht. Kontakte, die ein Produkt reserviert haben, die in angezeigt **Gallery2_1** , in denen Benutzer können jeden Kontakt zu einem Produkt zuweisen.

   ![Veranschaulichen Sie der Relate und Verknüpfung mit Funktionen in 1: n app](media/function-relate-unrelate/reservations-lostandfound.gif)

### <a name="many-to-many"></a>M: n

#### <a name="create-a-many-to-many-relationship"></a>Erstellen einer m: n Beziehung

Die Beispieldaten keine m: n Beziehung enthalten, aber Sie erstellen ein zwischen der Products-Entität und der Kontakt-Entität. Benutzer können mehrere Kontakte und jeden Kontakt zu mehr als ein Produkt jedes Produkt in Beziehung stehen.

1. Von [auf dieser Seite](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)Option **Daten** im linken Navigationsbereich, und klicken Sie anschließend **Entitäten**.

    ![Öffnen der Liste mit Entitäten](media/function-relate-unrelate/entity-list.png)

1. Ändern Sie den Entity-Filter, um alle Entitäten enthalten.

    Beispiel-Entitäten werden nicht standardmäßig angezeigt.

    ![Entität Filter entfernen](media/function-relate-unrelate/entity-all.png)

1. Führen Sie einen Bildlauf nach unten, öffnen Sie die **Produkt** Entität, und wählen **Beziehungen**.

    ![Registerkarte "Beziehungen" für die Product-Entität](media/function-relate-unrelate/entity-relationships.png)

1. Wählen Sie **Beziehung hinzufügen** > **m: n**.

    ![M: n Beziehung hinzufügen](media/function-relate-unrelate/entity-manytomany.png)

1. Wählen Sie die **wenden Sie sich an** Entität für die Beziehung.

    ![Wählen Sie die Entität "Contact"](media/function-relate-unrelate/entity-contact.png)

1. Wählen Sie **Fertig** > **Entität speichern**.

    ![Liste der Beziehungen für die Products-Entität](media/function-relate-unrelate/entity-done.png)

#### <a name="relate-and-unrelate-contacts-with-one-or-more-products"></a>Beziehen Sie und Verknüpfung mit Kontakte mit einem oder mehreren Produkten

Erstellen Sie eine andere app, das diesem ähnelt, die, das Sie zuvor in diesem Thema erstellt haben, aber die neue app bietet eine m: n Beziehung. Alle Kontakte werden mehrere Produkte anstelle nur eines reservieren.

1. Erstellen Sie in einer leeren app für Tablets **Gallery1** als die [obenstehend](#one-to-many) in diesem Thema wird beschrieben.

1. Fügen Sie einen anderen Leerzeichen vertikal **Katalog** steuern, stellen Sie sicher, dass sie den Namen **Gallery2**, und klicken Sie dann in der oberen rechten Ecke des Bildschirms zu verschieben.

    Weiter unten in diesem Thema fügen Sie eine **Kombinationsfeld** festlegen, unter **Gallery2**.

1. Legen Sie in der Bearbeitungsleiste **Gallery2**des **Elemente** Eigenschaft **Gallery1.Selected.Contacts**.

    ![Konfigurieren von ContactsGallery](media/function-relate-unrelate/contacts-gallery.png)

1. Auf der **Eigenschaften** Registerkarte **Layout** zu **Gruppenbild und der**.

    ![Konfigurieren von ContactsGallery](media/function-relate-unrelate/contacts-gallery-right.png)

1. In **Gallery2**, sicher, dass die **Bezeichnung** -Steuerelement heißt **Title2**, und legen Sie dann die **Text** Eigenschaft  **ThisItem. 'Full Name'**.

    In diesem Steuerelement wird kein Text angezeigt, bis Sie dieses Verfahren abzuschließen, und weisen Sie einen Kontakt zu einem Produkt.

    ![Wenden Sie sich an Namen anzeigen](media/function-relate-unrelate/contacts-title.png)

1. Löschen Sie **NextArrow2**, fügen Sie eine **Abbrechen** Symbol, und stellen Sie sicher, dass sie den Namen **icon1**.

1. Legen Sie die **Abbrechen** Symbols **OnSelect** -Eigenschaft auf diese Formel: 

    ```powerapps-dot
    Unrelate( Gallery1.Selected.Contacts, ThisItem )
    ```

    ![Symbol "Abbrechen" Konfigurieren](media/function-relate-unrelate/contacts-unrelate.png)

1. Auf der **Ansicht** Registerkarte **Datenquellen**.

1. In der **Daten** wählen Sie im Bereich **Datenquelle hinzufügen** > **Common Data Service** > **Kontakte**  >  **Verbinden**.

1. Unter **Gallery2**, Hinzufügen einer **Kombinationsfeld** steuern, stellen Sie sicher, dass sie den Namen **ComboBox1**, und legen Sie dann die **Elemente** Eigenschaft **Kontakte**.

    ![Konfigurieren Sie die Eigenschaft des Kombinationsfeld Elemente](media/function-relate-unrelate/contacts-combo.png)

1. Auf der **Eigenschaften** Registerkarte **Mehrfachauswahl zulassen** zu **aus**.

    ![Konfigurieren Sie das Kombinationsfeld "Layout"-Eigenschaft](media/function-relate-unrelate/contacts-combo-right.png)

1. Fügen Sie eine **hinzufügen** Symbol, und legen Sie dessen **OnSelect** -Eigenschaft auf diese Formel: 

    ```powerapps-dot
    Relate( Gallery1.Selected.Contacts, ComboBox1.Selected )
    ```

    ![Symbol zum Hinzufügen von konfigurieren](media/function-relate-unrelate/contacts-relate.png)

Mit dieser app können Benutzer jetzt kostenlos beziehen und Verknüpfung mit der eine Gruppe von Kontakten für jedes Produkt.

- Um einen Kontakt zu einem Produkt hinzuzufügen, wählen Sie den Kontakt im Kombinationsfeld am unteren Rand des Bildschirms, und wählen Sie dann die **hinzufügen** Symbol.
- Um einen Kontakt aus einem Produkt zu entfernen, wählen die **Abbrechen** Symbol für diesen Kontakt.

    Im Gegensatz zur 1-n-ermöglicht eine m: n Beziehung, mehrere Produkte ein Kontakt zugeordnet werden soll.

![Veranschaulichen Sie der Relate und Verknüpfung mit Funktionen in m: n app](media/function-relate-unrelate/contacts-relate-unrelate.gif)

#### <a name="in-reverse-relate-and-unrelate-products-with-multiple-contacts"></a>In umgekehrter Reihenfolge: beziehen und Verknüpfung mit Produkten mit mehreren Kontakten

M: n Beziehungen sind symmetrisch. Sie können das Beispiel, um einen Kontakt Produkte hinzu, und dann zwischen den beiden Bildschirmen angezeigt, wie die Beziehung aus jeder Richtung wird kippen erweitern.

1. Legen Sie die **OnVisible** Eigenschaft **Screen1** zu **aktualisieren (Produkte)**.

    Wenn Sie eine 1: n- oder m: n Beziehung, nur die Daten der Entität des ersten Arguments aktualisieren die **Relate** oder **Unrelate** Aufruf aktualisiert wird. Die zweite muss aktualisiert werden, manuell, wenn Sie zwischen den Bildschirmen der app spiegeln möchten.

    ![Visible-Eigenschaft wird auf die Funktion "Refresh" festgelegt.](media/function-relate-unrelate/contacts-refresh.png)

1. Doppelte **Screen1**.

    Das Duplikat den Namen **Screen1_1** und bilden die Grundlage für die Beziehungen aus der Contacts-Seite ansehen.

    ![Duplizieren eines Bildschirms](media/function-relate-unrelate/contacts-duplicate.png)

1. Um die reverse-Ansicht zu erstellen, ändern Sie diese Formeln, die Steuerelemente der **Screen1_1**:

    - Screen1_1.OnVisible = `Refresh( Contacts )`
    - Gallery1_1.Items = `Contacts`
    - Title1_1.Text = `ThisItem.'Full Name'`
    - Label1_1.Text = `"Selected Contact Products"`
    - Gallery2_1.Items = `Gallery1_1.Selected.Products`
    - Title2_1.Text = `ThisItem.Name`
    - Icon1_1.OnSelect = `Unrelate( Gallery1_1.Selected.Products, ThisItem )`
    - ComboBox1_1.Items = `Products`
    - Icon2_1.OnSelect = `Relate( Gallery1_1.Selected.Products, ComboBox1_1.Selected )`

    Das Ergebnis ähnelt dem vorherigen Bildschirm sieht jedoch wird die Beziehung zwischen der **Kontakte** Seite.

    ![Anzeigen von m: n Beziehung mit Kontakten ab](media/function-relate-unrelate/reverse-screen.png)

1. Einfügen einer **Pfeile Drehfeld** Symbol, und legen seine **OnSelect** Eigenschaft, um **navigieren (Screen1, None)**.  Führen Sie auf das gleiche **Screen1** mit der Formel **Navigate (Screen1_1, None)**.

    ![Fügen Sie die Navigation zwischen Bildschirmen](media/function-relate-unrelate/reverse-navigate.png)

Mit diesem Bildschirm "Neu" können Benutzer einen Kontakt zu einem Produkt hinzufügen und bringen Sie in einen Überblick über die Kontakte und finden Sie unter dem zugehörigen Produkt. Beziehungen sind symmetrisch und freigegebenen zwischen den beiden Bildschirmen.

![Zeigen Sie m: n Beziehung von beiden Seiten](media/function-relate-unrelate/contacts-reverse.gif)
