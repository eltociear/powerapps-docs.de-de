---
title: Zu verstehen, Datensatz Verweise und polymorphen Suchvorgänge | Microsoft-Dokumentation
description: Arbeiten Sie mit Datensatz-Verweise und polymorphen Suchvorgänge in Canvas-apps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 05/05/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 99024b447841668bd887571a269c2fb14f5f5289
ms.sourcegitcommit: f6c9e525130a03b8c76f0a4b4e90419604c5823c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2019
ms.locfileid: "65527087"
---
# <a name="understand-record-references-and-polymorphic-lookups-in-canvas-apps"></a>Grundlegendes zu Datensatz Verweise und polymorphen Suchvorgänge in Canvas-apps

Wenn Sie in der Schule eine Forschungsarbeit geschrieben haben, werden Sie wahrscheinlich eine Liste Ihrer Verweise am Ende angegeben. Sie nicht haben eine Kopie der tatsächlichen Hintergrundmaterial einschließen, die Sie aber stattdessen einen Weblink, Titel und Autor oder andere Informationen verwendet, damit ein Benutzer die ursprüngliche Quelle nachverfolgen zu kann. Sie kombiniert verschiedene Arten von Datenquellen in eine einzelne Liste Zeitungsartikeln neben audioaufzeichnungen, jeweils mit eigenen spezifische Details für einen entsprechenden Eintrag aus. Wikipedia-Artikeln häufig kann beispielsweise eine [langen Liste von verweisen](https://en.wikipedia.org/wiki/Microsoft#References).

In der Canvas-apps arbeiten Sie häufig mit Kopien von Datensätzen, die aus Datenquellen heruntergeladen. Sie verwenden die [ **LookUp** ](functions/function-filter-lookup.md) und [ **Filter** ](functions/function-filter-lookup.md) Funktionen und die [ **Katalog** ](controls/control-gallery.md) des Steuerelements **ausgewählte** Eigenschaft, um den bestimmten Datensatz zu identifizieren, die Sie möchten. Alle Datensätze aus **Filter** oder **ausgewählte** werden von demselben Typ, damit Sie Felder mit einem einfachen verwenden können. *Feld* Notation. Diese Kopien enthalten häufig Referenzinformationen, daher können Sie verwenden die [ **Patch** ](functions/function-patch.md) Funktion, um die ursprüngliche Quelle zu aktualisieren.

Canvas-apps unterstützen auch *aufzeichnen Verweise*. Viel bezieht sich wie ein Forschungsarbeit Verweis und ein Datensatzverweis auf einen Datensatz ohne eine vollständige Kopie der Datei. Ein solchen Verweis kann zu einem Datensatz in einer beliebigen Entität verweisen.  Wie in der Forschungsarbeit Verweise, können Sie auch Datensätze aus unterschiedlichen Entitäten in einer einzelnen Spalte kombinieren.

Viele Vorgänge für Datensatz-Verweise sind identisch mit der Arbeit mit Datensätzen. Sie können Datensätze Verweise miteinander und vollständige Datensätze vergleichen. Legen Sie einen Datensatz Verweis-Wert, mit der **Patch** funktioniert genauso wie eine Suche mit einem vollständigen Datensatz.

Es gibt einen wichtigen Nutzung Unterschied: Sie können nicht direkt auf die Felder eines Datensatzes Verweises zugreifen, ohne zuerst herzustellen, auf welche Entität sie verweist. Dies ist da Canvas-apps erfordern, dass alle Typen bekannt sein, wenn Sie Formeln schreiben. Da Sie nicht den Typ eines Verweises Datensatz wissen erst die app ausgeführt wird, wird Sie nicht das einfache verwenden. *Feld* Notation direkt. Müssen Sie zuerst dynamisch bestimmen den Entitätstyp mit dem [ **IsType** ](functions/function-astype-istype.md) Funktion, und klicken Sie dann zu verwenden. *Feld* Notation für das Ergebnis der [ **AsType** ](functions/function-astype-istype.md) Funktion.

*Entitätstyp* bezieht sich auf das Schema der jeder Datensatz in einer Entität. Jede Entität verfügt über einen eindeutigen Satz von Feldern mit verschiedenen Namen und Datentypen. Jeder Datensatz der Entität erbt, die der Struktur vorhanden. zwei Datensätze haben denselben Entitätstyp aus, wenn sie von derselben Entität stammen.

## <a name="polymorphic-lookups"></a>Polymorphe Suchvorgänge

Common Data Service unterstützt die Beziehungen zwischen den Datensätzen. Jeder Datensatz in die **Konten** Entität verfügt über eine **Hauptkontaktperson** Nachschlagefeld für einen Datensatz in die **Kontakte** Entität. Die Suche nur auf einen Datensatz in verweisen **Kontakte** und kann nicht mit einem Datensatz im, z. B. die **Teams** Entität. Letztes Detail wichtig, ist da Sie immer wissen, welche Felder wird für die Suche verfügbar sein.

Common Data Service unterstützt auch polymorphen vor, die auf einen Datensatz aus Entität in einem Satz verweisen können. Z. B. die **Besitzer** Feld verweisen auf einen Datensatz in die **Benutzer** Entität oder die **Teams** Entität. Das gleiche Nachschlagefeld in verschiedenen Datensätzen konnte auf Datensätze in verschiedenen Entitäten verweisen. In diesem Fall Sie nicht immer wissen, welche Felder werden zur Verfügung.  

Canvas-Datensatz Verweise wurden entwickelt, für die Arbeit mit polymorphen Suchvorgänge in gängigen Data Service. Sie können auch Datensatzebene verweisen außerhalb dieses Kontexts, handelt es sich wie die beiden Konzepte unterscheiden.

Beginnen Sie im nächsten Abschnitt, um diese Konzepte zu untersuchen, durch die Arbeit mit der **Besitzer** Suche.

## <a name="show-the-fields-of-a-record-owner"></a>Zeigen Sie die Felder eines Datensatzes-Besitzers

Jede Entität in Common Data Service umfasst eine **Besitzer** Feld. Dieses Feld kann nicht entfernt werden, kann nicht hinzugefügt werden, einen anderen und es ist immer ein Wert erforderlich.

Zum Anzeigen dieses Felds im der **Konto** Entität:

1. Open [dieser Website](http://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).
1. Wählen Sie in der linken Navigationsleiste auf **Daten** > **Entitäten**.
1. Wählen Sie in der Liste der Entitäten, **Konto**.
1. Öffnen Sie in der oberen rechten Ecke die Filterliste (die nastaven NA hodnotu **Standard** standardmäßig), und wählen Sie dann **alle**.
1. Scrollen Sie nach unten, bis die **Besitzer** Feld angezeigt wird.

> [!div class="mx-imgBorder"]
> ![Besitzerfeld auf die Entität "Account"](media/working-with-references/owner-field.png)

Dieses Nachschlagefelds kann zu einem Datensatz verweisen, entweder die **Teams** Entität oder die **Benutzer** Entität. Nicht jeder Datensatz in dieser Entitäten haben, Berechtigungen für eine **Besitzer**; aktivieren Sie die unterstützten Rollen aus, wenn ein Problem auftreten.

Diese Abbildung zeigt einen einfachen Katalog mit **Konten**, wobei die **Konten** -Entität wurde für die app als eine Datenquelle hinzugefügt:

> [!div class="mx-imgBorder"]
> ![Konten, die in einem Katalog-Steuerelement angezeigt](media/working-with-references/accounts-gallery.png)

> [!IMPORTANT]
> In diesem Thema werden die Grafiken anzeigen, einige Namen und andere Werte, die nicht Teil der Beispieldaten, die bereitgestellt wird, mit Common Data Service. Die Schritte veranschaulichen, genau wie die Steuerelemente für ein bestimmtes Ergebnis zu konfigurieren, aber Ihre Erfahrungen sind die Daten für Ihre Organisation abhängig.

Um den Besitzer der einzelnen Konten im Katalog angezeigt, Sie könnten versucht sein, verwenden Sie die Formel **ThisItem.Owner.Name**. Jedoch dem Namensfeld in der **Team** Entität ist **Teamname**, und das Feld "Name" in der **Benutzer** Entität **vollständigen Namen**. Die app nicht wissen, welche Art der Suche Sie arbeiten mit bis Sie die app ausführen, und kann er variieren zwischen Datensätzen in der **Konten** Entität.

Sie benötigen eine Formel, die an diese Abweichung anpassen kann. Sie müssen auch die Datenquellen hinzufügen, für die Entität, die Typen **Besitzer** kann (in diesem Fall **Benutzer** und **Teams**). Fügen Sie diese drei Datenquellen zu Ihrer app hinzu:

> [!div class="mx-imgBorder"]
> ![Konten, Teams und Benutzern Entitäten in den Bereich "Daten"](media/working-with-references/accounts-datasources.png)

Mit diesen Datenquellen in platzieren, und diese Formel verwenden, um den Namen eines Benutzers oder eines Teams anzuzeigen:

```powerapps-dot
If( IsType( ThisItem.Owner, [@Teams] ),
    "Team: " & AsType( ThisItem.Owner, [@Teams] ).'Team Name',
    "User: " & AsType( ThisItem.Owner, [@Users] ).'Full Name' )
```

> [!div class="mx-imgBorder"]
> ![Konten, die in einem Katalog-Steuerelement angezeigt wird, mit dem Besitzer-Feld angezeigt](media/working-with-references/accounts-displayowner.png)

In dieser Formel die **IsType** Tests funktioniert die **Besitzer** Feld für die **Teams** Entität. Ist dieses Entitätstyps die **AsType** Funktion wandelt es diesen auf eine **Team** Datensatz. An diesem Punkt können Sie alle Felder der Zugriff auf die **Teams** Entität, einschließlich **Teamname**, mithilfe von *. Feld* Notation. Wenn **IsType** bestimmt wird, die die **Besitzer** wird nicht von ein Datensatz in die **Teams** Entität, in das Feld muss einen Datensatz in die **Benutzer** Entität da die **Besitzer** ist ein Pflichtfeld (nicht *leere*).

Sie verwenden die [globale mehrdeutigkeitsvermeidung Operator](functions/operators.md#disambiguation-operator) für **[@Teams]** und **[@Users]** um sicherzustellen, dass Sie mit den globalen Typ verwenden. Nicht in diesem Fall erforderlich, aber es ist ein sollte zur guten Gewohnheit, zu. 1: n Beziehungen in des Katalogs Datensatzebene häufig Konflikten, und diese Vorgehensweise wird diese Verwirrung vermieden.

Um alle Felder eines Datensatzes Verweises verwenden zu können, müssen Sie zunächst mithilfe der **AsType** Funktion, um ihn in einen bestimmten Typ umwandeln. Kann nicht zugegriffen werden Felder, die direkt aus der **Besitzer** Feld, da das System welche Entitätstyp unbekannt ist, die Sie verwenden möchten.

Die **AsType** Funktion einen Fehler zurück, wenn die **Besitzer** Feld entspricht nicht dem Entitätstyp, der angefordert wird, damit Sie verwenden können, die **IfError** Funktion, um diese Formel zu vereinfachen. Aktivieren Sie die experimentelle Funktion **fehlerverwaltung auf Formelebene**:

> [!div class="mx-imgBorder"]
> ![Experimentelle wechseln Sie zur fehlerverwaltung auf Formelebene aktivieren](media/working-with-references/accounts-iferror.png)

Durch diese Ersetzen der vorstehende Formel:

```powerapps-dot
IfError(
    "Team: " & AsType( ThisItem.Owner, [@Teams] ).'Team Name',
    "User: " & AsType( ThisItem.Owner, [@Users] ).'Full Name' )
```

## <a name="filter-based-on-an-owner"></a>Filtern nach Besitzer

Herzlichen Glückwunsch: Sie haben den schwierigsten Aspekt der Arbeit mit einem Datensatzverweis abgeschlossen. Andere Anwendungsfälle sind unter Umständen einfacher, da Zugriff auf Felder des Datensatzes nicht. Ein typischer Fall akzeptiert als filtern, die in diesem Abschnitt lernen Sie.

Hinzufügen einer **Kombinationsfeld** steuern, über den Katalog, und legen Sie diese Eigenschaften des neuen Steuerelements:

- **Elemente**: `Users`
- **SelectMultiple**: `false`

> [!div class="mx-imgBorder"]
> ![Kombinationsfeld-Steuerelement über den Katalog mit für Benutzer Festlegen der Items-Eigenschaft hinzugefügt werden](media/working-with-references/filter-insert-combobox.png)

Um den Katalog von einem bestimmten Benutzer aus dieser Kombinationsfeld ausgewählte zu filtern, Festlegen des Katalogs **Elemente** -Eigenschaft auf diese Formel.

```powerapps-dot
Filter( Accounts, Owner = ComboBox1.Selected )
```

> [!div class="mx-imgBorder"]
> ![Gefilterter Katalog, die basierend auf dem Wert in das Kombinationsfeld-Steuerelement](media/working-with-references/filter-accounts.png)

> [!IMPORTANT]
> Die Anweisungen in diesem Thema sind genau, wenn Sie die Schritte genau befolgen. Jede Formel, die an ein Steuerelement, mit dem Namen verweist schlägt jedoch fehl, wenn das Steuerelement über einen anderen Namen besitzt. Wenn Sie zu löschen und ein Steuerelement desselben Typs hinzufügen, wird die Anzahl am Ende der Name des Steuerelements geändert. Für jede Formel, die einen Fehler anzeigt, vergewissern Sie sich, dass sie die richtigen Namen aller Steuerelemente enthält.

Sie müssen nicht verwenden **IsType** oder **AsType** , da Sie Datensätze Verweise zu anderen Datensatz verweisen oder vollständige Datensätze vergleichen können. Die app kann den Entitätstyp des **ComboBox1.Selected** , weil sie abgeleitet ist die **Benutzer** Entität. Konten, die für die der Besitzer eines Teams ist, wird nicht das Filterkriterium entsprechen.

Sie können durch die Unterstützung durch einen Benutzer oder ein Team Filtern etwas originellere abrufen.

1. Schaffen Sie Speicherplatz am oberen Rand des Bildschirms durch Ändern der Größe der Galerie und Verschieben im Kombinationsfeld, fügen Sie eine [ **Radio** Steuerelement](controls/control-radio.md) über den Katalog, und legen Sie diese Eigenschaften für das neue Steuerelement:

    - **Elemente**: `[ "All", "Users", "Teams" ]`
    - **Layout**: `Layout.Horizontal`

1. Für die **Kombinationsfeld** steuern, legen Sie diese Eigenschaft (wenn das Kombinationsfeld nicht mehr angezeigt wird, wählen Sie **Benutzer** im Optionsfeld-Steuerelement):

    - **Visible**: `Radio1.Selected.Value = "Users"`

1. Kopieren Sie die **Kombinationsfeld** steuern, verschieben Sie die Kopie direkt über das Original und legen Sie dann diese Eigenschaften für die Kopie:

    - **Elemente**: `Teams`
    - **Visible**: `Radio1.Selected.Value = "Teams"`

    Die app wird nur ein Kombinationsfeld zu einem Zeitpunkt den Status des Optionsfeld-Steuerelements in Abhängigkeit angezeigt. Da sie direkt über voneinander sind, werden sie angezeigt, dasselbe Steuerelement sein, das seinen Inhalt zu ändern.

1. Legen Sie schließlich die **Elemente** Eigenschaft der **Katalog** -Steuerelements auf diese Formel:

    ```powerapps-dot
    Filter( Accounts,
        Radio1.Selected.Value = "All"
        Or (Radio1.Selected.Value = "Users" And Owner = ComboBox1.Selected)
        Or (Radio1.Selected.Value = "Teams" And Owner = ComboBox1_1.Selected)
    )
    ```

    > [!div class="mx-imgBorder"]
    > ![gefilterter Katalog zeigt alle Datensätze oder einen bestimmten Benutzer oder ein team](media/working-with-references/filter-combobox.png)

Mit diesen Änderungen können Sie zeigen alle Datensätze oder Filtern basierend auf der ein Benutzer oder ein Team:

> [!div class="mx-imgBorder"]
> ![Animation, die verschiedene gefilterte Ergebnisse angezeigt. Basis auf der Radio-Steuerelement und Kombinationsfeld Felder](media/working-with-references/filter-allthree.gif)

Die Formel ist vollständig delegierbar. Der Teil, der das Optionsfeld-Werte zu vergleichen, ist eine Konstante in allen Datensätzen und wird ausgewertet, bevor der Rest des Filters in Common Data Service gesendet wird.

Wenn Sie nach dem Typ des Besitzers filtern möchten, können Sie mithilfe der **IsType** -Funktion, aber es ist nicht noch delegiert:

> [!div class="mx-imgBorder"]
> ![Filtern Sie, indem Sie mit der IsType Besitzertyp](media/working-with-references/filter-bytype.png)

## <a name="update-the-owner-by-using-patch"></a>Aktualisieren Sie den Besitzer, indem Sie Patch

Aktualisieren der **Besitzer** Feld in die gleiche Weise wie jede andere Suche. So setzen das momentan ausgewählte Konto Besitzer auf das erste Team:

```powerapps-dot
Patch( Accounts, Gallery1.Selected, { Owner: First( Teams ) } )
```

Dieser Ansatz nicht in einem normalen Suchvorgang unterscheiden, da die app den Typ der weiß, dass **erste (Teams)**. Wenn Sie den ersten Benutzer stattdessen möchten, ersetzen Sie den Teil mit **erste (Benutzer)**. Die **Patch** Funktion weiß, dass die **Besitzer** Feld kann entweder diese zwei Entitätstypen festgelegt werden.

So fügen Sie diese Funktion zur app hinzu:

1. In der **Strukturansicht** wählen Sie im Bereich der **Radio** -Steuerelement und die beiden **Kombinationsfeld** Steuerelemente zur gleichen Zeit.

1. Wählen Sie auf die Auslassungszeichen **diese Elemente kopieren**:

    > [!div class="mx-imgBorder"]
    > ![Kopieren von mehreren Steuerelementen, die unter Verwendung der Strukturansicht](media/working-with-references/patch-copy.png)

1. Wählen Sie im gleichen Menü **einfügen**:

    > [!div class="mx-imgBorder"]
    > ![Fügen Sie mehrere Steuerelemente, die unter Verwendung der Strukturansicht](media/working-with-references/patch-paste.png)

1. Verschieben Sie die kopierte Steuerelemente auf der rechten Seite des Katalogs:

    > [!div class="mx-imgBorder"]
    > ![Verschoben von kopierten Steuerelemente rechts neben dem Katalog](media/working-with-references/patch-position.png)

1. Wählen Sie den kopierten **Radio** steuern, und klicken Sie dann diese Eigenschaften ändern:

    - Artikel: `[ "Users", "Teams" ]`
    - Standardwert: `If( IsType( Gallery1.Selected.Owner, Users ), "Users", "Teams" )`

    > [!div class="mx-imgBorder"]
    > ![Entfernt die Auswahl aller aus dem Optionsfeld-Steuerelement](media/working-with-references/patch-noall.png) 

1. In der **Radio** Option **Benutzer** , damit die **Kombinationsfeld** -Steuerelement, das Benutzer aufgeführt sind, wird angezeigt.

1. Wählen Sie die sichtbaren **Kombinationsfeld** steuern, und legen Sie die **DefaultSelectedItems** -Eigenschaft auf diese Formel:

    ```powerapps-dot
    If( IsType( Gallery1.Selected.Owner, Users ),
        AsType( Gallery1.Selected.Owner, Users ),
        Blank()
    )
    ```

    > [!div class="mx-imgBorder"]
    > ![Default-Eigenschaftensatz für das Kombinationsfeld für den Benutzer](media/working-with-references/patch-default-users.png)

1. In der **Radio** Option **Teams** , damit die **Kombinationsfeld** -Steuerelement, das Teams listet sichtbar ist.

1. Wählen Sie die **Radio** Steuerelement auszuführende Auswahl von den jetzt nicht sichtbare **Kombinationsfeld** -Steuerelement für Benutzer.

1. Wählen Sie die sichtbaren **Kombinationsfeld** für Teams, die steuern, und legen Sie dessen **DefaultSelectedItems** -Eigenschaft auf diese Formel:

    ```powerapps-dot
    If( IsType( Gallery1.Selected.Owner, Teams ),
        AsType( Gallery1.Selected.Owner, Teams ),
        Blank()
    )
    ```

    > [!div class="mx-imgBorder"]
    > ![Default-Eigenschaftensatz für das Kombinationsfeld für Teams](media/working-with-references/patch-default-teams.png)

1. Fügen Sie eine **Schaltfläche** steuern, verschieben Sie es unter der **Kombinationsfeld** steuern, und legen Sie dann auf der Schaltfläche " **Text** Eigenschaft, um `"Patch Owner"`.

1. Legen Sie die **OnSelect** -Eigenschaft der Schaltfläche auf diese Formel:

    ```powerapps-dot
    Patch( Accounts, Gallery1.Selected,
        { Owner: If( Radio1_1.Selected.Value = "Users",
                ComboBox1_2.Selected,
                ComboBox1_3.Selected ) } )
    ```

    > [!div class="mx-imgBorder"]
    > ![Formel, festgelegt auf Schaltflächen-Steuerelement](media/working-with-references/patch-button.png)

Das kopierte **Radio** und **Kombinationsfeld** Steuerelemente zeigen den Besitzer für das momentan ausgewählte Konto im Katalog. Mit den gleichen-Steuerelementen können Sie den Besitzer des Kontos auf jeden Team oder der Benutzer durch Auswählen der Schaltfläche festlegen:

> [!div class="mx-imgBorder"]
> ![Animation mit Patch des Besitzers entweder mit einem Benutzer oder ein Team](media/working-with-references/patch-allthree.gif)

## <a name="show-the-owner-by-using-a-form"></a>Zeigen Sie den Besitzer über ein Formular an

Sie können anzeigen, eine **Besitzer** Feld in einem Formular, indem Sie eine benutzerdefinierte Karte hinzufügen. Während ich dies schreibe, können Sie den Wert des Felds ein Formularsteuerelement nicht ändern.

1. Fügen Sie eine **Bearbeitungsformular** zu steuern, und klicken Sie dann die Größe und verschieben Sie es auf der unteren rechten Ecke.

1. Auf der **Eigenschaften** Registerkarte im rechten Bereich, und Öffnen der **Datenquelle** aus, und wählen Sie dann **Konten**:

    > [!div class="mx-imgBorder"]
    > ![Formular-Steuerelement zeigt zusätzliche Felder mit leeren Werten](media/working-with-references/form-insert.png)  

1. Festlegen des Formulars **Element** Eigenschaft `Gallery1.Selected`:

    > [!div class="mx-imgBorder"]
    > ![Formular-Steuerelement, die zusätzliche Felder aufgefüllt, die aus dem ausgewählten Element im Katalog anzeigen](media/working-with-references/form-item.png)

1. Auf der **Eigenschaften** im rechten Bereich auf der Registerkarte **Bearbeitungsfelder**.

1. In der **Felder** Bereich, wählen Sie die Auslassungspunkte, und wählen Sie dann **benutzerdefinierte Karte hinzufügen**:

    > [!div class="mx-imgBorder"]
    > ![Befehl zum Hinzufügen einer benutzerdefinierten Karte](media/working-with-references/form-customcard.png)

    Die neue Karte wird am unteren Rand des Formularsteuerelements angezeigt.

1. Ändern der Größe der Karte nach Bedarf, um den gesamten Text anzeigen:

    > [!div class="mx-imgBorder"]
    > ![Eingefügte benutzerdefinierte Karte, die leer](media/working-with-references/form-inserted-customcard.png)

1. Fügen Sie eine **Bezeichnung** in der benutzerdefinierten Karte zu steuern, und legen Sie der Bezeichnung des **Text** Eigenschaft, um die Formel, die Sie in der Galerie verwendet:

    ```powerapps-dot
    If( IsType( ThisItem.Owner, Teams ),
        "Team: " & AsType( ThisItem.Owner, Teams ).'Team Name',
        "User: " & AsType( ThisItem.Owner, Users ).'Full Name' )
    ```

    > [!div class="mx-imgBorder"]
    > ![Benutzerdefinierte Karte, die das Feld Besitzer werden in ein Label-Steuerelement angezeigt.](media/working-with-references/form-displayowner.png)

Für jede Auswahl in der Galerie weitere Felder des Kontos, einschließlich der Besitzer des Datensatzes im Formular angezeigt werden. Wenn Sie den Besitzer ändern, mit der **Patch** Schaltfläche das Formularsteuerelement wird auch gezeigt, die diese Änderung.

> [!div class="mx-imgBorder"]
> ![Animation, die das Formularsteuerelement reagieren auf Änderungen im Katalog anzeigen](media/working-with-references/form-allthree.gif)

## <a name="show-the-fields-of-a-customer"></a>Die Felder eines Kunden anzeigen

In Common Data Service den **Kunden** Nachschlagefeld ist eine weitere polymorphe Suche, die sehr ähnlich ist **Besitzer**.

**Besitzer** ist auf eine pro Entität, doch Entitäten zählen 0 (null), ein oder mehrere **Kunden** Nachschlagefelder. Die **Kontakte** enthält Systementität. die **Firmenname** Feld, das ist eine **Kunden** Nachschlagefeld:

> [!div class="mx-imgBorder"]
> ![Feld "Company Name" als Kunden-Datentyp, der nicht unbedingt mit Entität "Contact"](media/working-with-references/customer-companyname.png)

Sie können weitere hinzufügen **Kunden** Nachschlagefelder für eine Entität auswählen der **Kunden** Datentyp für ein neues Feld:

![Kundendaten aus der Liste der Datentypen eingeben, wenn Sie ein Feld erstellen](media/working-with-references/customer-datatype.png)

Ein **Kunden** Nachschlagefeld kann zu einem Datensatz verweisen, entweder die **Konten** Entität oder die **Kontakte** Entität. Verwenden Sie die **IsType** und **AsType** Funktionen mit diese Entitäten ist jetzt ein guter Zeitpunkt, um sie als Datenquellen hinzuzufügen (lassen Sie **Teams** und **Benutzer**  vorhanden):

> [!div class="mx-imgBorder"]
> ![Konten, Teams, Benutzer und Kontakte Entitäten in den Bereich "Daten"](media/working-with-references/customer-datasources.png)

Die Behandlung von der **Kunden** und **Besitzer** Felder sind so ähnlich, dass Sie die app buchstäblich kopieren können (**Datei** > **speichern als**, und geben Sie dann auf einen anderen Namen), und nehmen Sie diese einfache Änderungen vor:

| Location | **Besitzer** Beispiel | **Kunden** Beispiel |
|----------|-----------|------------------|
| überall | **Besitzer** | **"Customer Name"** |
| überall | **Benutzer** | **Konten** |
| überall | **Teams** | **Kontakte** |
| Der Katalog **Elemente** Eigenschaft | **Konten** | **Kontakte** |
| Des Formulars **Elemente** Eigenschaft | **Konten** | **Kontakte** |
| Das erste Argument von **Patch**<br>in der Schaltfläche **OnSelect** Eigenschaft | **Konten** | **Kontakte** |
| Filtern des Radio **Elemente** Eigenschaft | **[&nbsp;"All"&nbsp;"Benutzer",&nbsp;"Teams"&nbsp;]** | **[&nbsp;"All"&nbsp;"Konten"&nbsp;"Contacts"&nbsp;]** |
| Patchen des Radio **Elemente** Eigenschaft | **[ "Users", "Teams" ]** | **[ "Accounts", "Contacts" ]** |
| Das Kombinationsfeld **Visible** Eigenschaft | **"Benutzer"** und **"Teams"** | **"Konten"** und **"Contacts"** |

Beispielsweise der neue Katalog müssen dies **Elemente** Eigenschaft:

```powerapps-dot
Filter( Contacts,
    Radio1.Selected.Value = "All"
    Or (Radio1.Selected.Value = "Accounts" And 'Company Name' = ComboBox1.Selected)
    Or (Radio1.Selected.Value = "Contacts" And 'Company Name' = ComboBox1_1.Selected)
)
```

> [!div class="mx-imgBorder"]
> ![Kunden-app, die die app Besitzer abgeleitet sind, mit einfachen Änderungen angewendet](media/working-with-references/customer-simple-update.png)

Zwei wichtige Unterschiede zwischen **Kunden** und **Besitzer** benötigen Sie ein Update auf die Formeln in den Katalog und das Formular:

1. 1: n Beziehungen zwischen **Konten** und **Kontakte** haben Vorrang vor, wenn Sie diese Entitätstypen anhand des Namens verweisen. Anstelle von **Konten**, verwenden Sie  **\[ \@Konten]**; anstelle von **Kontakte**, verwenden Sie  **\[ \@ Kontakte]**. Mithilfe der [globale mehrdeutigkeitsvermeidung Operator](functions/operators.md#disambiguation-operator) Sie sicherstellen, dass der Entitätstyp im sprechen **IsType** und **AsType**. Dieses Problem besteht nur im Datensatzkontext der Katalog und Form-Steuerelemente.

1. Die **Besitzer** Feld muss einen Wert aufweisen, aber **Kunden** Felder möglich *leere*. Um das richtige Ergebnis ohne einen Typnamen anzuzeigen, zu testen, in diesem Fall mit der [ **IsBlank** Funktion](functions/function-isblank-isempty.md), und zeigen Sie stattdessen eine leere Textzeichenfolge.

Beide dieser Änderungen sind in die gleiche Formel, die in der benutzerdefinierten Karte in der Form angezeigt wird, als auch die **Text** Eigenschaft des Katalogs Label-Steuerelement:

```powerapps-dot
If( IsBlank( ThisItem.'Company Name' ), "",
    IsType( ThisItem.'Company Name', [@Accounts] ),
        "Account: " & AsType( ThisItem.'Company Name', [@Accounts] ).'Account Name',
    "Contact: " & AsType( ThisItem.'Company Name', [@Contacts] ).'Full Name'
)
```

> [!div class="mx-imgBorder"]
> ![Aktualisieren Sie auf die Texteigenschaft des Label-Steuerelement im Katalog Untertitel](media/working-with-references/customer-update.png)

Mit diesen Änderungen können Sie anzeigen und Ändern der **Firmenname** -Feld in der **Kontakte** Entität:

> [!div class="mx-imgBorder"]
> ![Animation anzeigen, ändern die Auswahl in die Kontakte-basierte Änderungen in die anderen Steuerelemente und Formular für Katalog-Steuerelement](media/working-with-references/customer-allthree.gif)

> [!NOTE]
> Während ich dies schreibe, **Kunden** suchen, haben diese Einschränkungen:
>
> - Sie können eine Liste anhand eines bestimmten Datensatzes innerhalb nicht filtern die **Kontakte** oder **Konten** Entitäten. Der Filter Optionsfeld-Steuerelement im vorherigen Beispiel funktioniert nicht.
> - Das einzige Kunde-Feld, das funktioniert, wird der systemdefinierte **'Company Name'** auf die **Kontakte** -Entität, die im vorherigen Beispiel verwendet wurde. Hinzufügen eines benutzerdefinierten kundenfelds wird noch nicht unterstützt.
> - Feld "Kunde" kann nicht gelöscht werden, mithilfe von **Patch** auf festgelegt ist, dass *leere*.

## <a name="understand-regarding-lookup-fields"></a>Zum Verstehen von Nachschlagefeldern

Die **im Hinblick auf** Nachschlagefeld unterscheidet sich etwas von denjenigen, die Sie in diesem Thema bereits mit gearbeitet haben. Sie beginnen mit der Anwendung der Muster, die weiter oben in diesem Thema beschrieben, und klicken Sie dann erfahren Sie, andere Tricks.

Beginnen Sie einfach mit der **Faxe** Entität. Diese Entität verfügt über eine polymorphe **im Hinblick auf** Nachschlagefeld, die auf verweisen kann **Konten**, **Kontakte**, und anderen Entitäten. Sie können die app ausführen, für die **Kunden** und ändern Sie ihn für **Faxe**:

| Location | **Kunden** Beispiel | **Faxe** Beispiel |
|----------|-----------|------------------|
| überall | **"Customer Name"** | **in Bezug auf** |
| Der Katalog **Elemente** Eigenschaft | **Kontakte** | **Faxe** |
| Des Formulars **Elemente** Eigenschaft | **Kontakte** | **Faxe** |
| Das erste Argument von **Patch**<br> in der Schaltfläche **OnSelect** Eigenschaft | **Kontakte** | **Faxe** |

In diesem Fall müssen Sie eine Datenquelle hinzufügen: Diese werden derzeit für **Faxe**. Auf der **Ansicht** Registerkarte **Datenquellen**:

> [!div class="mx-imgBorder"]
> ![Datenbereich mit dem-Konten, Teams, Benutzer, Kontakte und Faxe Entitäten](media/working-with-references/faxes-datasources.png)

Ein wichtiger Unterschied für **im Hinblick auf** ist, dass es nicht auf **Konten** und **Kontakte**. In der Tat ist die Liste der Entitäten mit benutzerdefinierten Entitäten erweiterbar. Die meisten der app ohne Änderung aufnehmen können, jedoch müssen Sie die Formel für die Bezeichnung im Katalog und im Formular aktualisieren:

```powerapps-dot
If( IsBlank( ThisItem.Regarding ), "",
    IsType( ThisItem.Regarding, [@Accounts] ),
        "Account: " & AsType( ThisItem.Regarding, [@Accounts] ).'Account Name',
    IsType( ThisItem.Regarding, [@Contacts] ),
        "Contacts: " & AsType( ThisItem.Regarding, [@Contacts] ).'Full Name',
    ""
)
```

> [!div class="mx-imgBorder"]
> ![Aktualisierter Text-Eigenschaft für das Steuerelement für Untertitel für in Bezug auf Suchvorgänge](media/working-with-references/regarding-label.png)

Nachdem Sie diese Änderungen vorgenommen haben, arbeiten Sie mit der **im Hinblick auf** Suche genau wie Sie die **Besitzer** und **Kunden** suchen:

> [!div class="mx-imgBorder"]
> ![Animation, die Änderungen anzeigt, in dem Faxe basierend Updates auf die anderen Steuerelemente und Formular für Katalog-Steuerelement](media/working-with-references/regarding-allthree.gif)

> [!NOTE]
> Während ich dies schreibe, **im Hinblick auf** suchen, haben diese Einschränkungen:
>
> - Sie können keine Liste basierend auf einem bestimmten Datensatz filtern. Der Filter Optionsfeld-Steuerelement im vorherigen Beispiel funktioniert nicht.
> - Entsprechender Kontodatensatz dem Betrefffeld kann nicht gelöscht werden, mithilfe von **Patch** auf festgelegt ist, dass *leere*.

## <a name="understand-regarding-relationships"></a>Zum Verstehen von Beziehungen

**Im Hinblick auf** unterscheidet sich von **Besitzer** und **Kunden** , da der erste Wert eine n: 1 Beziehung umfasst. Definitionsgemäß eine umgekehrte, 1: n Beziehung ermöglicht Ihnen das Schreiben von **erste (Konten). Faxe**.

Wir sichern, und sehen Sie sich die Definitionen für Entitäten. In Common Data Service Entitäten wie z. B. **Faxe**, **Aufgaben**, **-e-Mails**, **Anmerkungen zu dieser**, **Telefonanrufe**, **Buchstaben**, und **Chats** wird [ *Aktivitäten*](../../developer/common-data-service/activity-entities.md). Sie können auch eigene erstellen [benutzerdefinierte Aktivitätsentitäten](../../developer/common-data-service/custom-activities.md). Wenn Sie anzeigen oder erstellen Sie eine Aktivitätsentität, die Einstellungen werden angezeigt, unter **Weitere Einstellungen**:

![Aktivität-Entity-Einstellung, wenn eine Entität erstellen](media/working-with-references/activity-entitytype.png)

Andere Entitäten können zu einer Aktivitätsentität verknüpft werden, wenn sie als aktiviert sind ein *Aktivitätsaufgabe* in den Einstellungen von der Entität. **Konten**, **Kontakte**, und viele andere Standardentitäten bestimmt sind (in diesem Fall unter **Weitere Einstellungen**):

![Aktivität-Einstellung beim Erstellen einer Entitätstyps](media/working-with-references/activity-entityuse.png)

Alle Aktivitätsentitäten und Aktivitäten / Aufgaben Entitäten haben eine implizite Beziehung. Wenn Sie den Filter ändern **alle** wählen Sie am oberen Rand des Bildschirms, der **Faxe** Entität, und wählen Sie dann die **Beziehungen** Registerkarte alle Entitäten, die als Ziel einer seinkönnen **Im Hinblick auf** Suche angezeigt werden:

> [!div class="mx-imgBorder"]
> ![Beziehungen der Entität Faxe in Bezug auf n: 1 Beziehungen anzeigen](media/working-with-references/activity-manytoone.png)

Wenn Sie Beziehungen Anzeigen der **Konten** Entität, die alle Entitäten, die als Quelle werden soll, können ein **im Hinblick auf** Feld "Suche" angezeigt:

> [!div class="mx-imgBorder"]
> ![Beziehungen zwischen der Entität "Account" in Bezug auf die 1: n Beziehungen anzeigen](media/working-with-references/activity-onetomany.png)

Was bedeutet was?

- Wenn Sie Formeln erstellen, müssen Sie berücksichtigen, dass die Liste der Aktivitätsentitäten ist nicht fest, und können Ihre eigenen erstellen. Die Formel muss entsprechend eine Aktivitätsentität verarbeitet werden, die Sie nicht erwartet haben.
- Aktivität-Aufgaben und Aktivitäten haben eine 1: n Beziehung. Sie können ganz einfach für alle Faxe bitten, die mit einem Konto beziehen.

Um dieses Konzept in der app zu untersuchen:

1. Fügen Sie einem anderen Bildschirm hinzu:

    > [!div class="mx-imgBorder"]
    > ![Fügen Sie einen leeren Bildschirm](media/working-with-references/activitypointer-newscreen.png)

1. Ein Katalog-Steuerelement einfügen, ändern Sie die Größe und verschieben Sie sie auf der linken Seite des Bildschirms.

1. Auf der **Eigenschaften** Registerkarte den rechten Bereich festlegen des Katalogs **Elemente** zu **Konten**:

    > [!div class="mx-imgBorder"]
    > ![Legen Sie die Elemente auf Konten im Eigenschaftenbereich](media/working-with-references/activitypointer-accounts.png)

1. Legen Sie das Layout des Katalogs auf **Titel**, und legen Sie dann auf das Feld "Titel" **Kontoname**:

    > [!div class="mx-imgBorder"]
    > ![Festlegen Sie Layout für den Titel für Katalog-Steuerelement im Eigenschaftenbereich.](media/working-with-references/activitypointer-account-name.png)

1. Fügen Sie eine zweite Katalog hinzu, ändern Sie die Größe und verschieben Sie sie auf die rechte Seite des Bildschirms.

1. Legen Sie des neuen Katalogs **Elemente** Eigenschaft `Gallery2.Selected.Faxes`.

    Dieser Schritt gibt die gefilterte Liste von Faxnachrichten für ein bestimmtes Konto zurück:

    > [!div class="mx-imgBorder"]
    > ![Set-Items-Eigenschaft für die Faxe basierten Katalog-Steuerelement](media/working-with-references/activitypointer-faxes.png)

1. Legen Sie das Layout des Katalogs auf **Titel und Untertitel**, und legen Sie dann auf das Feld "Titel" zum Anzeigen der **Betreff** Feld (Kleinbuchstaben sein kann **Betreff**):

    > [!div class="mx-imgBorder"]
    > ![Festlegen von Titel, Feld "Betreff"](media/working-with-references/activitypointer-subject.png)

Wenn Sie ein Element in der Liste der Konten auswählen, zeigt die Liste der Faxe Faxnachrichten für nur das betreffende Konto an.

> [!div class="mx-imgBorder"]
> ![Animation, die mit der Auswahl im Katalog der Liste von Faxnachrichten für Konten](media/working-with-references/activitypointer-allthree.gif)

## <a name="activity-entity"></a>Aktivitätsentität

Wie im vorherigen Abschnitt beschrieben, können Sie alle Faxe für ein Konto anzeigen. Sie können jedoch auch alle Aktivitäten für ein Konto, einschließlich der Faxe, e-Mail-Nachrichten, Anrufe und andere Interaktionen anzeigen.

Für das zweite Szenario, Sie verwenden die **Aktivität** Entität. Sie können diese Entität anzeigen, indem einschalten **alle** in der Ecke oben rechts, um den Filter aus der Liste der Entitäten zu entfernen:

> [!div class="mx-imgBorder"]
> ![Liste der Entitäten, die die Aktivitätsentität anzeigen](media/working-with-references/activitypointer-entity.png)

Die **Aktivität** Entität ist ein Sonderfall. Jedes Mal, wenn Sie einen Eintrag zum Hinzufügen der **Faxe** Entität, erstellt das System außerdem einen Datensatz in die **Aktivität** Entität mit den Feldern, die für alle Aktivitätsentitäten gelten. Dieser Felder **Betreff** am interessantesten ist.

Sie können alle Aktivitäten anzeigen, ändern Sie nur eine Zeile im vorherigen Beispiel. Ersetzen Sie dies `Gallery2.Selected.Faxes` mit `Gallery2.Selected.Activities`:

> [!div class="mx-imgBorder"]
> ![Änderung der Items-Eigenschaft für den zweiten Katalog, und Ändern von Faxnachrichten in Aktivitäten](media/working-with-references/activitypointer-gallery.png)

Datensätzen stammen die **Aktivität** Entität, aber Sie können dennoch den **IsType** Funktion, um zu identifizieren, welche Art von Aktivität, die sie sind. Bevor Sie in diesem Fall verwenden **IsType** mit einem Entitätstyp angehören müssen Sie die Datenquelle hinzufügen:

> [!div class="mx-imgBorder"]
> ![Bereich "Daten" für alle Entitäten, die erforderlich sind, für die IsType-Funktion](media/working-with-references/activity-datasources.png)

Mit dieser Formel, können Sie den Datensatztyp in ein Label-Steuerelement im Katalog anzeigen:

```powerapps-dot
If( IsType( ThisItem, [@Faxes] ), "Fax",
    IsType( ThisItem, [@'Phone Calls'] ), "Phone Call",
    IsType( ThisItem, [@'Email Messages'] ), "Email Message",
    IsType( ThisItem, [@Chats] ), "Chat",
    "Unknown"
)
```

> [!div class="mx-imgBorder"]
> ![Legen Sie Texteigenschaft auf die Formel, die Informationen für Faxe, Telefonanrufe und andere Aktivitäten anzeigen](media/working-with-references/activitypointer-type.png)

Sie können auch **AsType** Zugriff auf Felder des angegebenen Typs. Beispielsweise diese Formel bestimmt den Typ der einzelnen Aktivitäten und, für die Telefonanrufe, zeigt die Phone Anzahl, und rufen die Richtung von der **Telefonnummern** Entität:

```powerapps-dot
If( IsType( ThisItem, [@Faxes] ), "Fax",
    IsType( ThisItem, [@'Phone Calls'] ),
       "Phone Call: " &
       AsType( ThisItem, [@'Phone Calls'] ).'Phone Number' &
       " (" & AsType( ThisItem, [@'Phone Calls'] ).Direction & ")",
    IsType( ThisItem, [@'Email Messages'] ), "Email Message",
    IsType( ThisItem, [@Chats] ), "Chat",
    "Unknown"
)
```

> [!div class="mx-imgBorder"]
> ![Erweiterte Text-Eigenschaft mit weiteren Informationen für einen Anruf](media/working-with-references/activitypointer-phonecall.png)

Daher zeigt die app eine vollständige Liste der Aktivitäten. Die **Betreff** Feld für alle Arten von Aktivitäten, angezeigt wird, ob die Formel werden oder nicht berücksichtigt. Für die Arten von Aktivitäten, denen Sie kennen, können Sie ihren Namen und Typ-spezifische Informationen zu jeder Aktivität anzeigen:

> [!div class="mx-imgBorder"]
> ![Bildschirm mit Informationen für verschiedene Arten von Aktivitäten abgeschlossen](media/working-with-references/activitypointer-complete.png)

## <a name="notes-entity"></a>Anmerkungen zu dieser Entität

Bis jetzt alle die **im Hinblick auf** Beispiele wurden anhand der Aktivitäten, aber die **Anmerkungen zu dieser** Entität darstellt, einen weiteren Fall.

Wenn Sie eine Entität erstellen, können Sie Anlagen aktivieren:

![Aktivieren von Anlagen und Hinweise, wenn eine Entität erstellt](media/working-with-references/notes-entity.png)

Wenn Sie dieses Kontrollkästchen aktivieren, erstellen Sie eine **im Hinblick auf** Beziehung mit der **Anmerkungen zu dieser** Entität wie die folgende Grafik zeigt, für die **Konten** Entität:

> [!div class="mx-imgBorder"]
> ![Entität "Account" Anmerkungen zu dieser Beziehung anzeigt, über eine 1: n Beziehung](media/working-with-references/notes-relationships.png)

Als dieser Unterschied ist, verwenden Sie die **im Hinblick auf** Suche auf die gleiche Weise, in denen Sie die Aktivitäten verwenden. Entitäten, die aktiviert sind, für Anlagen eine 1: n Beziehung, um aufweisen **Anmerkungen zu dieser**, wie in diesem Beispiel:

`First( Accounts ).Notes`

> [!NOTE]
> Während ich dies schreibe, der **im Hinblick auf** Lookup nicht zur Verfügung, für die **Anmerkungen zu dieser** Entität. Sie können nicht gelesen werden, oder filtern Sie basierend auf den **im Hinblick auf** Feld, und Sie können keine legen Sie das Feld mit **Patch**.
>
> Allerdings das Gegenteil **Anmerkungen zu dieser** 1: n Beziehung ist verfügbar, sodass Sie eine Liste der Anmerkungen zu dieser Version für einen Datensatz filtern können, die für Anlagen aktiviert ist. Können Sie auch die [ **Relate** ](functions/function-relate-unrelate.md) Funktion, um einen Kommentar zu einer Datensatzes des **Anmerkungen zu dieser** Tabelle, aber der Hinweis muss zuerst erstellt werden, wie im folgenden Beispiel:
>
>`Relate( ThisItem.Notes, Patch( Notes, Defaults( Notes ), { Title: "A new note" } ) )`

## <a name="activity-parties"></a>Aktivitätsparteien

Während ich dies schreibe unterstützen Canvas-apps keine Aktivitätsparteien.
