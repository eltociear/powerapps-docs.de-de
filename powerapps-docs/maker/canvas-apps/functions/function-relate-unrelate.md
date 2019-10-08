---
title: Beziehung zwischen Funktionen und Funktionen | Microsoft-Dokumentation
description: Referenzinformationen, einschließlich Syntax und Beispielen, für die Funktionen "Beziehung" und "ohne Beziehung" in powerapps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 01/22/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: d8ba0cef60b268caafb57e18ae80a522905ba45b
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/07/2019
ms.locfileid: "71992748"
ms.PowerAppsDecimalTransform: true
---
# <a name="relate-and-unrelate-functions-in-powerapps"></a>Verknüpfen von Funktionen in powerapps

Verknüpfen von Datensätzen zweier Entitäten mithilfe einer 1: n-oder m:n-Beziehung.

## <a name="description"></a>Beschreibung

Die Funktion " **Verknüpfen** " verknüpft zwei Datensätze über eine 1: n-oder m:n-Beziehung in Common Data Service. Die Funktion " **ohne Beziehung** " kehrt den Prozess um und entfernt den Link.

Für 1: n-Beziehungen verfügt die viele Entität über ein Fremdschlüssel Feld, das auf einen Datensatz der eine Entität verweist. In **Beziehung** setzen legt dieses Feld so fest, dass es auf einen bestimmten Datensatz der einzelnen Entität verweist, ohne die **Beziehung** zu setzen legt dieses Feld auf *leer*fest. Wenn das Feld bereits festgelegt ist, wenn die **Beziehung** aufgerufen wird, geht der vorhandene Link zugunsten des neuen Links verloren. Sie können dieses Feld auch mit der [**Patch**](function-patch.md) -Funktion oder einem **[Bearbeitungs Formular](../controls/control-form-detail.md)** -Steuerelement festlegen. Sie müssen die Funktion "in **Beziehung** " nicht verwenden.

Bei m:n-Beziehungen behält das System, das die Datensätze verknüpft, eine verborgene jointabelle bei. Sie können nicht direkt auf diese jointabelle zugreifen. Sie kann nur über eine 1: n-Projektion gelesen und über die Funktionen "in **Beziehung** " und " **ohne Beziehung** " festgelegt werden. Keine der verknüpften Entitäten verfügt über einen Fremdschlüssel.

Die Daten für die Entität, die Sie im ersten Argument angeben, werden aktualisiert, um die Änderung widerzuspiegeln, aber die Daten für die Entität, die Sie im zweiten Argument angeben, werden nicht angezeigt. Diese Daten müssen manuell mit der **[Refresh](function-refresh.md)** -Funktion aktualisiert werden, um das Ergebnis des Vorgangs anzuzeigen.

Diese Funktionen erstellen oder löschen einen Datensatz nie. Es werden nur zwei bereits vorhandene Datensätze miteinander verknüpft bzw. nicht miteinander verknüpft.

Diese Funktionen können nur in [Verhaltens Formeln](../working-with-formulas-in-depth.md)verwendet werden.

> [!NOTE]
> Diese Funktionen sind Teil eines Vorschau Features, und ihr Verhalten ist nur verfügbar, wenn die **relationalen Daten, Optionssätze und andere neue Features für CDs** aktiviert sind. Dies ist eine Einstellung auf App-Ebene, die für neue apps standardmäßig aktiviert ist. Um diese Funktion zu finden, öffnen Sie das Menü **Datei** , wählen Sie **App-Einstellungen**und dann **Erweiterte Einstellungen**aus. Wir sind sehr an Ihrem Feedback interessiert und würden uns freuen, wenn Sie uns in den [PowerApps-Communityforen](https://powerusers.microsoft.com/t5/Expressions-and-Formulas/bd-p/How-To) Ihre Meinung mitteilen würden.

## <a name="syntax"></a>Syntax

**Beziehung**( *Entity1RelatedTable*; *Entity2Record* )

* *Entity1RelatedTable* : erforderlich. Für einen Datensatz von *Entity1*wird die Tabelle der *Entity2* -Datensätze über eine 1: n-oder m:n-Beziehung bezogen.
* *Entity2Record* : erforderlich. Der *Entity2* -Datensatz, der der Beziehung hinzugefügt werden soll.

**Ohne Beziehung**( *Entity1RelatedTable*; *Entity2Record* )

* *Entity1RelatedTable* : erforderlich. Für einen Datensatz von *Entity1*wird die Tabelle der *Entity2* -Datensätze über eine 1: n-oder m:n-Beziehung bezogen.
* *Entity2Record* : erforderlich. Der *Entity2* -Datensatz, der aus der Beziehung entfernt werden soll.

## <a name="examples"></a>Beispiele

Betrachten Sie eine **Products** -Entität mit den folgenden Beziehungen, wie im [Entity Viewer des powerapps-Portals](../../common-data-service/create-edit-entities-portal.md)gezeigt:

| Beziehungs Anzeige Name | Verwandte Entität | Beziehungstyp |
| --- | --- |
| Produkt Reservierung | Buchung | 1: n |
| Product &harr;-Kontakt | Kontakt | M:n-Zahl |

**Produkte** und **Reservierungen** sind über eine 1: n-Beziehung verknüpft.  So verknüpfen Sie den ersten Datensatz der **Reservations** -Entität mit dem ersten Datensatz der **Products** -Entität:

`Relate( First( Products ).Reservations; First( Reservations ) )`

So entfernen Sie die Beziehung zwischen diesen Datensätzen:

`Unrelate( First( Products ).Reservations; First( Reservations ) )`

Wir haben zu keinem Zeitpunkt erstellt oder entfernt oder einen Datensatz erstellt, nur die Beziehung zwischen Datensätzen wurde geändert.

**Produkte** und **Kontakte** sind über eine m:n-Beziehung verknüpft.  So verknüpfen Sie den ersten Datensatz der **Contacts** -Entität mit dem ersten Datensatz der **Products** -Entität:

`Relate( First( Products ).Contacts; First( Contacts ) )`

Da m:n-Beziehungen symmetrisch sind, können wir dies auch in umgekehrter Richtung durchgeführt haben:

`Relate( First( Contacts ).Products; First( Products ) )`

So entfernen Sie die Beziehung zwischen diesen Datensätzen:

`Unrelate( First( Products ).Contacts; First( Contacts ) )`

noch

`Unrelate( First( Contacts ).Products; First( Products ) )`

Die nachfolgende Exemplarische Vorgehensweise führt genau diese Vorgänge für diese Entitäten mithilfe einer APP mit **Katalog-und** Kombinations **Feld** -Steuerelementen für die Auswahl der beteiligten Datensätze aus.

Diese Beispiele hängen von den in Ihrer Umgebung installierten Beispiel Daten ab. Erstellen Sie entweder [eine Testumgebung mit Beispiel Daten](../../model-driven-apps/overview-model-driven-samples.md#get-sample-apps) [, oder fügen Sie einer vorhandenen Umgebung Beispiel Daten hinzu](../../model-driven-apps/overview-model-driven-samples.md#install-or-uninstall-sample-data).

### <a name="one-to-many"></a>1: n

#### <a name="relate-function"></a>Funktion **Verknüpfen**

Zuerst erstellen Sie eine einfache APP, um die Reservierungen anzuzeigen und neu zuzuweisen, die einem Produkt zugeordnet sind.

1. Erstellen Sie eine [Tablet-APP von einem leeren](../data-platform-create-app-scratch.md).

1. Klicken Sie auf der Registerkarte **Ansicht** auf **Datenquellen**.

1. Wählen Sie im Bereich **Daten** die Option **Datenquelle hinzufügen** > **Common Data Service** > **Produkte** > **Connect**aus.  

    Die Products-Entität ist Teil der oben geladenen Beispiel Daten.

     ![Hinzufügen der Products-Entität als Datenquelle](media/function-relate-unrelate/products-connect.png)

1. Fügen Sie auf der Registerkarte **Einfügen** ein leeres **[vertikales](../controls/control-gallery.md)** Katalog-Steuerelement hinzu.

1. Stellen Sie sicher, dass das soeben hinzugefügte Steuerelement den Namen **Gallery1**hat, und verschieben Sie es dann, und ändern Sie die Größe, um die linke Seite des Bildschirms auszufüllen.

1. Legen Sie auf der Registerkarte **Eigenschaften** die **Eigenschaft Items** von **Gallery1**auf **Products** und das **Layout** auf **Image und Title**fest.

    ![Konfigurieren von producout Gallery](media/function-relate-unrelate/products-gallery.png)

1. Stellen Sie in **Gallery1**sicher, dass das **Label** -Steuerelement den Namen **Title1**hat, und legen Sie dessen **Text** -Eigenschaft auf **ThisItem.Name**fest.

    ![Konfigurieren der Bezeichnung in Gallery1](media/function-relate-unrelate/products-title.png)

1. Wählen Sie den Bildschirm aus, um das Einfügen des nächsten Elements in **Gallery1**zu vermeiden.  Fügen Sie ein zweites leeres **vertikales** Katalog Steuerelement hinzu, und stellen Sie sicher, dass es den Namen **Wenn gallery2**

    **Wenn gallery2** zeigt die Reservierungen für jedes Produkt an, das der Benutzer in **Gallery1**auswählt.

1. Verschieben Sie die **Wenn gallery2** , und ändern Sie die Größe, um den oberen rechten Quadranten des Bildschirms auszufüllen.

1. optionale Fügen Sie das Steuerelement blaue **Bezeichnung** oberhalb von **Wenn gallery2**hinzu, wie in der nächsten Grafik dargestellt.

1. Legen Sie in der Bearbeitungs Leiste die **Items** -Eigenschaft von **Wenn gallery2** auf **Gallery1. Selected. Reservations**fest.

    ![Wenn gallery2 Elemente konfigurieren](media/function-relate-unrelate/reservations-gallery.png)

1. Legen Sie im Eigenschaften Bereich für das **Layout** von **Wenn gallery2**den Wert **Title**fest.

    ![Konfigurieren des wenn gallery2-Layouts](media/function-relate-unrelate/reservations-gallery-right.png)

1. Fügen Sie in **Wenn gallery2**ein Kombinations **[Feld](../controls/control-combo-box.md)** -Steuerelement hinzu, stellen Sie sicher, dass es **ComboBox1**lautet, und verschieben Sie es dann, und ändern Sie die Größe, um die Blockierung der anderen Steuerelemente in **Wenn gallery2**

1. Legen Sie auf der Registerkarte **Eigenschaften** die **Eigenschaft Items** von **ComboBox1**auf **Products**fest.

    ![Items-Eigenschaft auf Produkte festlegen](media/function-relate-unrelate/reservations-combo-right.png)

1. Führen Sie auf der Registerkarte **Eigenschaften** einen Bildlauf nach unten **durch, und legen Sie die**Option **Mehrfachauswahl zulassen** für **ComboBox1**

    ![Legen Sie Mehrfachauswahl zulassen auf aus fest.](media/function-relate-unrelate/reservations-singleselect-right.png)

1. Legen Sie in der Bearbeitungs Leiste die **defaultselecteditems** -Eigenschaft von **ComboBox1**auf **thisitem. ' Product Reservierung '** fest.

    ![Legen Sie defaultselecteditems für reservecombo fest.](media/function-relate-unrelate/reservations-combo.png)

1. Legen Sie in **Wenn gallery2**die **onselect** -Eigenschaft von **NextArrow2**auf diese Formel fest:

    ```powerapps-comma
    Relate( ComboBox1.Selected.Reservations; ThisItem )
    ```

    Wenn der Benutzer dieses Symbol auswählt, ändert sich die aktuelle Reservierung in das Produkt, das der Benutzer in **ComboBox1**ausgewählt hat.

    ![Konfigurieren von NextArrow2](media/function-relate-unrelate/reservations-relate.png)

1. Drücken Sie F5, um die APP im Vorschaumodus zu testen.

Mit dieser APP kann der Benutzer eine Reservierung von einem Produkt in ein anderes verschieben. Bei einer Reservierung für ein Produkt kann der Benutzer in **ComboBox1** ein anderes Produkt auswählen und dann **NextArrow2** auswählen, um die Reservierung zu ändern.

![Veranschaulichen der Funktion "Beziehung" in einer 1: n-App](media/function-relate-unrelate/reservations-reassign.gif)

#### <a name="unrelate-function"></a>Funktion **ohne Beziehung**

An diesem Punkt können Sie die Beziehung von einem Datensatz in einen anderen verschieben, aber Sie können die Beziehung nicht vollständig entfernen. Sie können die Funktion " **ohne Beziehung** " verwenden, um einen Reservierungsdaten Satz von einem beliebigen Produkt zu trennen.

1. Klicken Sie auf der Registerkarte **Ansicht** auf **Datenquellen**.

1. Wählen Sie im Bereich **Daten** die Option **Datenquelle hinzufügen** > **Common Data Service** > **Reservierungen** > **Connect**aus.

1. Legen Sie in **Wenn gallery2**die **onselect** -Formel für **NextArrow2** auf diese Formel fest:

    ```powerapps-comma
    If( IsBlank( ComboBox1.Selected );
        Unrelate( Gallery1.Selected.Reservations; ThisItem );
        Relate( ComboBox1.Selected.Reservations; ThisItem )
    );;
    Refresh( Reservations )
    ```
    ![Symbol "rechts konfigurieren"](media/function-relate-unrelate/reservations-relate-unrelate.png)

1. Kopieren Sie **Wenn gallery2** in die Zwischenablage, indem Sie Sie auswählen und dann STRG + C drücken.

1. Fügen Sie ein Duplikat von **Wenn gallery2** in denselben Bildschirm ein, indem Sie STRG + V drücken, und verschieben Sie es dann an den unteren Rand des Bildschirms.

1. optionale Wenn Sie eine Bezeichnung oberhalb von **Wenn gallery2**hinzugefügt haben, wiederholen Sie die vorherigen beiden Schritte für diese Bezeichnung.

1. Stellen Sie sicher, dass das Duplikat von **Wenn gallery2** den Namen **Gallery2_1**hat, und legen Sie dann dessen **Items** -Eigenschaft auf diese Formel fest:

    ```powerapps-comma
    Filter( Reservations; IsBlank( 'Product Reservation' ) )
    ```

    Es wird eine Delegierungs Warnung angezeigt, aber Sie ist nicht mit der kleinen Datenmenge in diesem Beispiel zu tun.

    ![Legen Sie die Items-Eigenschaft von Gallery2_1 fest.](media/function-relate-unrelate/reservations-lost.png)

Mit diesen Änderungen können Benutzer die Auswahl in **ComboBox1** für einen Kontakt löschen, wenn diese Person kein Produkt reserviert hat. Kontakte, die kein Produkt reserviert haben, werden in **Gallery2_1** angezeigt, wo Benutzer jeden Kontakt einem Produkt zuweisen können.

   ![Veranschaulichen der Beziehung zwischen Funktionen und deren Verknüpfung in der 1: n-App](media/function-relate-unrelate/reservations-lostandfound.gif)

### <a name="many-to-many"></a>M:n-Zahl

#### <a name="create-a-many-to-many-relationship"></a>Erstellen einer m:n-Beziehung

Die Beispiel Daten enthalten keine m:n-Beziehung, aber Sie erstellen eine Beziehung zwischen der Entität "Products" und der Entität "Contacts". Benutzer können jedes Produkt mit mehr als einem Kontakt und jedem Kontakt zu mehr als einem Produkt verknüpfen.

1. Wählen Sie auf [dieser Seite](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)die Option **Daten** in der linken Navigationsleiste aus, und wählen Sie dann **Entitäten**aus.

    ![Liste der Entitäten öffnen](media/function-relate-unrelate/entity-list.png)

1. Ändern Sie den Entitäts Filter, sodass er alle Entitäten einschließt.

    Standardmäßig werden Beispiel Entitäten nicht angezeigt.

    ![Entfernen des Entitäts Filters](media/function-relate-unrelate/entity-all.png)

1. Scrollen Sie nach unten, öffnen Sie die **Product** -Entität, und wählen Sie **Beziehungen**.

    ![Beziehungs Registerkarte für die Product-Entität](media/function-relate-unrelate/entity-relationships.png)

1. Wählen Sie **Beziehung hinzufügen**@no__t **-1**m:n-.

    ![M:n-Beziehung hinzufügen](media/function-relate-unrelate/entity-manytomany.png)

1. Wählen Sie die Entität **Contact** für die Beziehung aus.

    ![Auswählen der Entität "Contact"](media/function-relate-unrelate/entity-contact.png)

1. Wählen Sie **done** > **Entität speichern**aus.

    ![Liste der Beziehungen für die Products-Entität](media/function-relate-unrelate/entity-done.png)

#### <a name="relate-and-unrelate-contacts-with-one-or-more-products"></a>Beziehung zwischen Kontakten und einem oder mehreren Produkten

Sie erstellen eine andere APP, die dem zuvor in diesem Thema erstellten ähnelt, aber die neue App bietet eine m:n-Beziehung. Jeder Kontakt kann mehrere Produkte reservieren, anstatt nur einen zu verwenden.

1. Erstellen Sie in einer leeren App für Tablets **Gallery1** wie das [erste Verfahren](#one-to-many) in diesem Thema beschrieben.

1. Fügen Sie ein weiteres **leeres vertikales** Katalog-Steuerelement hinzu, stellen Sie sicher, dass es **Wenn gallery2**ist, und verschieben Sie es in die obere rechte Ecke des Bildschirms.

    Später in diesem Thema fügen Sie unter **Wenn gallery2**ein Kombinations **Feld** -Steuerelement hinzu.

1. Legen Sie in der Bearbeitungs Leiste die **Items** -Eigenschaft von **Wenn gallery2**auf **Gallery1. Selected. Contacts**fest.

    ![Konfigurieren von contacout Gallery](media/function-relate-unrelate/contacts-gallery.png)

1. Legen Sie auf der Registerkarte **Eigenschaften** **Layout** auf **Bild und Titel**fest.

    ![Konfigurieren von contacout Gallery](media/function-relate-unrelate/contacts-gallery-right.png)

1. Stellen Sie in **Wenn gallery2**sicher, dass das **Label** -Steuerelement den Namen **Title2**hat, und legen Sie dessen **Text** -Eigenschaft auf **thisitem. ' Full Name '** fest.

    In diesem Steuerelement wird erst dann Text angezeigt, wenn Sie dieses Verfahren abgeschlossen und einen Kontakt zu einem Produkt zugewiesen haben.

    ![Kontaktnamen anzeigen](media/function-relate-unrelate/contacts-title.png)

1. Löschen Sie **NextArrow2**, fügen Sie ein **Abbruch** Symbol ein, und stellen Sie sicher, dass der Name **icon1**lautet.

1. Legen **Sie die onselect** -Eigenschaft des **Cancel** -Symbols auf die folgende Formel fest: 

    ```powerapps-comma
    Unrelate( Gallery1.Selected.Contacts; ThisItem )
    ```

    ![Symbol "Abbrechen" Konfigurieren](media/function-relate-unrelate/contacts-unrelate.png)

1. Klicken Sie auf der Registerkarte **Ansicht** auf **Datenquellen**.

1. Wählen Sie im Bereich **Daten** die Option **Datenquelle hinzufügen** > **Common Data Service** > **Kontakte** > **Connect**aus.

1. Fügen Sie unter **Wenn gallery2**ein Kombinations **Feld** -Steuerelement hinzu, stellen Sie sicher, dass es den Namen **ComboBox1**hat, und legen Sie dann die Eigenschaft **Items** auf **Contacts**fest.

    ![Konfigurieren der Eigenschaft "Kombinations Feld Items"](media/function-relate-unrelate/contacts-combo.png)

1. Legen Sie auf der Registerkarte **Eigenschaften** die Option **Mehrfachauswahl zulassen** auf **aus**fest.

    ![Konfigurieren der Eigenschaft "Kombinations Feld Layout"](media/function-relate-unrelate/contacts-combo-right.png)

1. **Fügen Sie ein Add** -Symbol ein, und legen Sie dessen **onselect** -Eigenschaft auf diese Formel fest: 

    ```powerapps-comma
    Relate( Gallery1.Selected.Contacts; ComboBox1.Selected )
    ```

    ![Symbol "Add" Konfigurieren](media/function-relate-unrelate/contacts-relate.png)

Mit dieser APP können Benutzer eine Gruppe von Kontakten nun frei in Beziehung setzen und die Beziehung zu den einzelnen Produkten in Beziehung setzen.

- Wenn Sie einem Produkt einen Kontakt hinzufügen möchten, wählen Sie den Kontakt im Kombinations Feld unten auf dem Bildschirm aus, und wählen Sie dann das Symbol **Hinzufügen** aus.
- Um einen Kontakt von einem Produkt zu entfernen, wählen Sie das Symbol **Abbrechen** für diesen Kontakt aus.

    Anders als bei 1: n können Benutzer mit einer m:n-Beziehung denselben Kontakt mehreren Produkten zuordnen.

![Veranschaulichen der Beziehung zwischen Funktionen und deren Verknüpfung in einer m:n-App](media/function-relate-unrelate/contacts-relate-unrelate.gif)

#### <a name="in-reverse-relate-and-unrelate-products-with-multiple-contacts"></a>In umgekehrter Reihenfolge: in Beziehung zwischen Produkten und mehreren Kontakten

M:n-Beziehungen sind symmetrisch. Sie können das Beispiel erweitern, um einem kontaktprodukte hinzuzufügen und dann zwischen den beiden Bildschirmen zu wechseln, um anzuzeigen, wie die Beziehung von beiden Richtungen aus angezeigt wird.

1. Legen Sie die **onvisible** -Eigenschaft von **Screen1** auf **Refresh (Products)** fest.

    Wenn Sie eine 1: n-oder m:n-Beziehung aktualisieren, werden nur die Daten der ersten Argument Entität **des Beziehungs-oder** aufrufenden Aufrufes aktualisiert. Die zweite muss manuell aktualisiert werden, wenn Sie zwischen den Bildschirmen dieser App wechseln möchten.

    ![Festlegen der onvisible-Eigenschaft auf die Refresh-Funktion](media/function-relate-unrelate/contacts-refresh.png)

1. Doppelte **Screen1**.

    Das Duplikat erhält den Namen **Screen1_1** und bildet die Grundlage für die Betrachtung der Beziehungen von der Seite Kontakte.

    ![Duplizieren eines Bildschirms](media/function-relate-unrelate/contacts-duplicate.png)

1. Um die umgekehrte Ansicht zu erstellen, ändern Sie diese Formeln in den Steuerelementen von **Screen1_1**:

    - Screen1_1. onvisible = `Refresh( Contacts )`
    - Gallery1_1. Items = `Contacts`
    - Title1_1. Text = `ThisItem.'Full Name'`
    - Label1_1. Text = `"Selected Contact Products"`
    - Gallery2_1. Items = `Gallery1_1.Selected.Products`
    - Title2_1. Text = `ThisItem.Name`
    - Icon1_1. onselect = `Unrelate( Gallery1_1.Selected.Products; ThisItem )`
    - ComboBox1_1. Items = `Products`
    - Icon2_1. onselect = `Relate( Gallery1_1.Selected.Products; ComboBox1_1.Selected )`

    Das Ergebnis ähnelt dem vorherigen Bildschirm, wird jedoch in der Beziehung von der **Kontakt** Seite angezeigt.

    ![N:n-Beziehung beginnend mit Kontakten anzeigen](media/function-relate-unrelate/reverse-screen.png)

1. Fügen Sie ein **Pfeil nach unten** ein, und legen **Sie dessen onselect** -Eigenschaft auf **Navigate (Screen1, None)** fest.  Gehen Sie auf **Screen1** mit der Formel **Navigation (Screen1_1, None)** .

    ![Navigation zwischen Bildschirmen hinzufügen](media/function-relate-unrelate/reverse-navigate.png)

Mit diesem neuen Bildschirm können Benutzer einen Kontakt zu einem Produkt hinzufügen und dann zu einer Ansicht von Kontakten wechseln und das zugehörige Produktanzeigen. Die Beziehungen sind symmetrisch und werden von den beiden Bildschirmen gemeinsam genutzt.

![Veranschaulichen der n:n-Beziehung von beiden Seiten](media/function-relate-unrelate/contacts-reverse.gif)
