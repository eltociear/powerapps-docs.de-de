---
title: Grundlegendes zu Daten Satz verweisen und polymorphen suchen | Microsoft-Dokumentation
description: Arbeiten mit Daten Satz verweisen und polymorphen suchen in Canvas-apps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 09/14/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 0b1c81dd808b224ca30d9de3d4bab252a2676cf4
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73542311"
ms.PowerAppsDecimalTransform: true
---
# <a name="understand-record-references-and-polymorphic-lookups-in-canvas-apps"></a>Grundlegendes zu Daten Satz verweisen und polymorphen Such Vorgängen in Canvas-apps

Wenn Sie ein Forschungspapier in der Schule geschrieben haben, haben Sie wahrscheinlich am Ende eine Liste ihrer Referenzen bereitgestellt. Sie haben keine Kopie des eigentlichen Hintergrund Materials, das Sie verwendet haben, sondern eine Webverknüpfung, einen Buch Titel und Autor oder andere Informationen enthalten, damit jemand die ursprüngliche Quelle nachvollziehen kann. Sie haben verschiedene Arten von Quellen in einer einzigen Liste gemischt, und zwar neben Audioaufzeichnungen, die jeweils über eigene spezifische Details für ein richtiges Zitat verfügen. Beispielsweise enthalten Wikipedia-Artikel häufig eine [lange Liste von verweisen](https://en.wikipedia.org/wiki/Microsoft#References).

In Canvas-apps arbeiten Sie häufig mit Kopien von Datensätzen, die aus Datenquellen heruntergeladen wurden. Verwenden Sie die [**Such**](functions/function-filter-lookup.md) -und [**Filter**](functions/function-filter-lookup.md) Funktionen und die **ausgewählte** Eigenschaft des Katalog [ **-Steuer Elements, um den gewünschten**](controls/control-gallery.md) Datensatz zu identifizieren. Alle Datensätze aus **Filter** oder **ausgewählt** sind vom gleichen Entitätstyp, sodass Sie Felder mit einem einfachen verwenden können. *Feld* Notation. Diese Kopien enthalten häufig Referenzinformationen, sodass Sie die [**Patch**](functions/function-patch.md) -Funktion verwenden können, um die ursprüngliche Quelle zu aktualisieren.

Canvas-apps unterstützen auch *Daten Satz Verweise*. Ähnlich wie bei einem Forschungspapier Verweis verweist ein Daten Satz Verweis auf einen Datensatz, ohne dass er eine komplette Kopie enthält. Ein solcher Verweis kann auf einen Datensatz in einer beliebigen Entität verweisen. Ebenso wie Research-Paper References können Sie Datensätze aus verschiedenen Entitäten in einer einzelnen Spalte kombinieren.

Viele Vorgänge für Daten Satz Verweise sind identisch mit der Arbeit mit Datensätzen. Sie können Daten Satz Verweise untereinander und vollständige Datensätze vergleichen. Sie können den Wert eines Daten Satz Verweises mit der **Patch** -Funktion genauso wie bei der Suche mit einem vollständigen Datensatz festlegen.

Es gibt einen wichtigen Verwendungs Unterschied: Sie können nicht direkt auf die Felder eines Daten Satz Verweises zugreifen, ohne zuerst festzulegen, auf welche Entität er verweist. Dies liegt daran, dass Canvas-apps erfordern, dass beim Schreiben von Formeln alle Typen bekannt sind. Da Sie den Typ eines Daten Satz Verweises erst kennen, wenn die app ausgeführt wird, können Sie die einfache nicht verwenden. Die *Feld* Notation direkt. Sie müssen zuerst den Entitätstyp mit der [**istype**](functions/function-astype-istype.md) -Funktion dynamisch bestimmen und dann verwenden. *Feld* Notation für das Ergebnis der [**astype**](functions/function-astype-istype.md) -Funktion.

Der *Entitätstyp* verweist auf das Schema der einzelnen Datensätze in einer Entität. Jede Entität verfügt über einen eindeutigen Satz von Feldern mit unterschiedlichen Namen und Datentypen. Jeder Datensatz der Entität erbt diese Struktur. zwei Datensätze weisen denselben Entitätstyp auf, wenn Sie aus derselben Entität stammen.

## <a name="polymorphic-lookups"></a>Polymorphe Suchvorgänge

Common Data Service unterstützt Beziehungen zwischen Datensätzen. Jeder Datensatz in der Entität **Accounts** verfügt über ein **Primäres Kontakt** Suchfeld zu einem Datensatz in der Entität **Contacts** . Die Suche kann nur auf einen Datensatz in **Kontakten** verweisen und kann nicht auf einen Datensatz in, z. h. die **Teams** -Entität, verweisen. Das letzte Detail ist wichtig, da Sie immer wissen, welche Felder für die Suche verfügbar sind.

Common Data Service unterstützt auch polymorphe Lookups, die auf einen Datensatz von einer beliebigen Entität in einer Menge verweisen können. Beispielsweise kann das Feld " **Owner** " auf einen Datensatz in der Entität " **Users** " oder " **Teams** " verweisen. Das gleiche Nachschlage Feld in verschiedenen Datensätzen kann auf Datensätze in unterschiedlichen Entitäten verweisen. In diesem Fall wissen Sie nicht immer, welche Felder verfügbar sein werden.

Canvas-Daten Satz Verweise wurden zum Arbeiten mit polymorphen suchen in Common Data Service entwickelt. Sie können Daten Satz Verweise auch außerhalb dieses Kontexts verwenden, sodass sich die beiden Konzepte unterscheiden.

Im nächsten Abschnitt erfahren Sie, wie Sie diese Konzepte durcharbeiten mit der **Besitzer** Suche untersuchen.

## <a name="show-the-fields-of-a-record-owner"></a>Anzeigen der Felder eines Daten Satz Besitzers

Jede Entität in Common Data Service enthält ein **Besitzer** Feld. Dieses Feld kann nicht entfernt werden, Sie können kein weiteres hinzufügen, und es ist immer ein Wert erforderlich.

So zeigen Sie dieses Feld in der Entität " **Account** " an:

1. Öffnen Sie [diese powerapps-Website](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).
1. Wählen Sie in der linken Navigationsleiste **Daten**  > **Entitäten**aus.
1. Wählen Sie in der Liste der Entitäten die Option **Konto**aus.
1. Öffnen Sie in der oberen rechten Ecke die Filterliste (standardmäßig standardmäßig auf **Standard** festgelegt), und wählen Sie dann **alle**aus.
1. Scrollen Sie nach unten, bis das Feld **Besitzer** angezeigt wird.

 > [!div class="mx-imgBorder"]
 > ![Feld "Besitzer" für Konto Entität](media/working-with-references/owner-field.png)

Dieses Nachschlage Feld kann auf einen Datensatz von der **Teams** -Entität oder der **Users** -Entität verweisen. Nicht jeder Datensatz in diesen Entitäten hat die Berechtigung, **Besitzer**zu sein. Überprüfen Sie die unterstützten Rollen, wenn ein Problem auftritt.

Diese Grafik zeigt einen einfachen Katalog mit **Konten**, bei denen die Entität **Accounts** der App als Datenquelle hinzugefügt wurde:

> [!div class="mx-imgBorder"]
> ![Konten, die in einem Galerie Steuerelement angezeigt werden](media/working-with-references/accounts-gallery.png)

> [!IMPORTANT]
> In diesem Thema zeigen die Grafiken einige Namen und andere Werte, die nicht Teil der Beispiel Daten sind, die mit Common Data Service ausgeliefert werden. Die Schritte veranschaulichen, wie Sie Steuerelemente für ein bestimmtes Ergebnis konfigurieren, aber Ihre Benutzeroberflächen unterscheiden sich je nach den Daten für Ihre Organisation.

Wenn Sie den Besitzer der einzelnen Konten im Katalog anzeigen möchten, können Sie die Formel **ThisItem.Owner.Name**verwenden. Allerdings lautet das Feld Name in der **Team** Entität **Teamname**, und das Feld Name in der Entität **User** ist **Vollständiger Name**. Die APP kann nicht erkennen, mit welcher Art von Suche Sie arbeiten, bis Sie die app ausführen, und Sie kann zwischen den Datensätzen in der Entität **Accounts** variieren.

Sie benötigen eine Formel, die an diese Varianz angepasst werden kann. Außerdem müssen Sie die Datenquellen für die Entitäts Typen hinzufügen, die **Besitzer** sein könnten (in diesem Fall **Benutzer** und **Teams**). Fügen Sie die folgenden drei Datenquellen zu Ihrer APP hinzu:

> [!div class="mx-imgBorder"]
> ![Konten, Teams und Benutzer Entitäten im Datenbereich](media/working-with-references/accounts-datasources.png)

Wenn diese Datenquellen vorhanden sind, verwenden Sie diese Formel, um entweder den Namen eines Benutzers oder eines Teams anzuzeigen:

```powerapps-comma
If( IsType( ThisItem.Owner; [@Teams] );
    "Team: " & AsType( ThisItem.Owner; [@Teams] ).'Team Name';
    "User: " & AsType( ThisItem.Owner; [@Users] ).'Full Name' )
```

> [!div class="mx-imgBorder"]
> ![Konten, die in einem Katalog-Steuerelement angezeigt](media/working-with-references/accounts-displayowner.png) werden

In dieser Formel testet die **istype** -Funktion das Feld " **Owner** " auf die Entität " **Teams** ". Wenn dies der Entitätstyp ist, wandelt die **astype** -Funktion Sie in einen **Team** Daten Satz um. An diesem Punkt können Sie auf alle Felder der **Teams** -Entität, einschließlich **Teamname**, zugreifen, indem Sie verwenden *. Feld* Notation. Wenn **istype** feststellt, dass der **Besitzer** kein Datensatz in der Entität " **Teams** " ist, muss dieses Feld ein Datensatz in der Entität " **Users** " sein, da das Feld " **Owner** " erforderlich ist (darf nicht *leer*sein).

Sie verwenden den [globalen mehrdeutigkeits Operator](functions/operators.md#disambiguation-operator) für **[@Teams]** und **[@Users]** , um sicherzustellen, dass Sie den globalen Entitätstyp verwenden. Sie benötigen Sie in diesem Fall nicht, aber es ist eine gute Gewohnheit, Sie zu bilden. 1: n-Beziehungen verursachen häufig einen Konflikt im Daten Satz Bereich des Katalogs, und diese Vorgehensweise vermeidet diese Verwirrung.

Um Felder eines Daten Satz Verweises verwenden zu können, müssen Sie zuerst die **astype** -Funktion verwenden, um Sie in einen bestimmten Entitätstyp umzuwandeln. Sie können nicht direkt aus dem Feld " **Besitzer** " auf Felder zugreifen, da das System nicht weiß, welcher Entitätstyp Sie verwenden möchten.

Die **astype** -Funktion gibt einen Fehler zurück, wenn das Feld " **Owner** " nicht mit dem angeforderten Entitätstyp identisch ist, sodass Sie die **IFERROR** -Funktion verwenden können, um diese Formel zu vereinfachen. Aktivieren Sie zunächst die experimentelle Funktion zur **Fehler Verwaltung auf Formel Ebene**:

> [!div class="mx-imgBorder"]
> ![experimentellen Switch, um die Fehler Verwaltung auf Formel Ebene zu aktivieren](media/working-with-references/accounts-iferror.png)

Ersetzen Sie dann die vorherige Formel durch diese:

```powerapps-comma
IfError(
    "Team: " & AsType( ThisItem.Owner; [@Teams] ).'Team Name';
    "User: " & AsType( ThisItem.Owner; [@Users] ).'Full Name' )
```

## <a name="filter-based-on-an-owner"></a>Filtern basierend auf einem Besitzer

Herzlichen Glückwunsch – Sie haben den schwierigsten Aspekt bei der Arbeit mit einem Daten Satz Verweis abgeschlossen. Andere Anwendungsfälle sind komplizierter, da Sie nicht auf die Felder des Datensatzes zugreifen. Nehmen Sie als Punkt den Filter, den Sie in diesem Abschnitt untersuchen.

Fügen Sie oberhalb des Katalogs ein Kombinations **Feld** -Steuerelement hinzu, und legen Sie diese Eigenschaften für das neue Steuerelement fest:

- **Elemente**: `Users`
- **Selectmultiple**: `false`

> [!div class="mx-imgBorder"]
> ![hinzugefügtes Kombinations Feld-Steuerelement oberhalb der Galerie mit der Eigenschaft "Items" auf "](media/working-with-references/filter-insert-combobox.png) Benutzer"

Um den Katalog nach einem bestimmten Benutzer zu filtern, der in diesem Kombinations Feld ausgewählt ist, legen Sie die **Items** -Eigenschaft des Katalogs auf die folgende Formel fest:

```powerapps-comma
Filter( Accounts; Owner = ComboBox1.Selected )
```

> [!div class="mx-imgBorder"]
> ![gefilterte Galerie basierend auf dem im Kombinations Feld-Steuerelement festgelegten Wert](media/working-with-references/filter-accounts.png)

> [!IMPORTANT]
> Die Anweisungen in diesem Thema sind genau, wenn Sie die Schritte genau befolgen. Jede Formel, die auf ein Steuerelement mit dem Namen verweist, schlägt jedoch fehl, wenn das Steuerelement einen anderen Namen hat. Wenn Sie ein Steuerelement desselben Typs löschen und hinzufügen, ändert sich die Zahl am Ende des Namens des Steuer Elements. Vergewissern Sie sich bei jeder Formel, die einen Fehler anzeigt,, dass Sie die korrekten Namen aller Steuerelemente enthält.

Sie müssen **istype** oder **astype** nicht verwenden, da Sie Verweis Verweise auf andere Daten Satz Verweise oder vollständige Datensätze vergleichen. Die APP kennt den Entitätstyp von **ComboBox1. Selected** , weil Sie von der Entität **Users** abgeleitet ist. Konten, für die der Besitzer ein Team ist, entsprechen nicht dem Filter Kriterium.

Sie können eine kleine Fantasie erzielen, indem Sie die Filterung durch einen Benutzer oder ein Team unterstützen.

1. Nehmen Sie im oberen Bereich des Bildschirms einen Bereich, indem Sie die Größe des Katalogs ändern und das Kombinations Feld verschieben, ein [ **Radio** -Steuer](controls/control-radio.md) Element oberhalb des Katalogs einfügen und dann diese Eigenschaften für das neue Steuerelement festlegen:

    - **Elemente**: `[ "All"; "Users"; "Teams" ]`
    - **Layout**: `Layout.Horizontal`

1. Legen Sie für das Kombinations **Feld** -Steuerelement diese Eigenschaft fest (wenn das Kombinations Feld nicht mehr angezeigt wird, wählen Sie **Benutzer** im Optionsfeld Steuerelement aus):

    - **Sichtbar**: `Radio1.Selected.Value = "Users"`

1. Kopieren und fügen Sie das Kombinations **Feld** -Steuerelement ein, verschieben Sie die Kopie direkt über das Original, und legen Sie dann diese Eigenschaften für die Kopie fest:

    - **Elemente**: `Teams`
    - **Sichtbar**: `Radio1.Selected.Value = "Teams"`

    Die APP zeigt jeweils nur ein Kombinations Feld an, abhängig vom Zustand des Steuer Elements. Da Sie sich direkt oberhalb voneinander befinden, scheinen Sie das gleiche Steuerelement zu sein, das ihren Inhalt ändert.

1. Legen Sie abschließend die **Items** -Eigenschaft des Katalog **-Steuer Elements** auf diese Formel fest:

    ```powerapps-comma
    Filter( Accounts;
        Radio1.Selected.Value = "All"
        Or (Radio1.Selected.Value = "Users" And Owner = ComboBox1.Selected)
        Or (Radio1.Selected.Value = "Teams" And Owner = ComboBox1_1.Selected)
    )
    ```

    > [!div class="mx-imgBorder"]
    > ![gefilterte Galerie, die alle Datensätze oder einen bestimmten Benutzer oder ein bestimmtes Team anzeigt](media/working-with-references/filter-combobox.png)

Mit diesen Änderungen können Sie alle Datensätze anzeigen oder basierend auf einem Benutzer oder einem Team filtern:

> [!div class="mx-imgBorder"]
> ![Animation mit verschiedenen gefilterten Ergebnissen basierend auf dem Optionsfeld Steuerelement und den Kombinations Feldern](media/working-with-references/filter-allthree.gif)

Die Formel kann vollständig delegiert werden. Der Teil, der die Optionsfeld Werte vergleicht, ist eine Konstante für alle Datensätze und wird ausgewertet, bevor der Rest des Filters an Common Data Service gesendet wird.

Wenn Sie nach dem Typ des Besitzers filtern möchten, können Sie die **istype** -Funktion verwenden, aber Sie ist noch nicht delegierbar.

> [!div class="mx-imgBorder"]
> ![Filtern nach Besitzertyp mithilfe von istype](media/working-with-references/filter-bytype.png)

## <a name="update-the-owner-by-using-patch"></a>Aktualisieren des Besitzers mithilfe von Patch

Sie können das Feld " **Owner** " auf die gleiche Weise wie bei jeder anderen Suche aktualisieren. So legen Sie den Besitzer des aktuell ausgewählten Kontos auf das erste Team fest:

```powerapps-comma
Patch( Accounts; Gallery1.Selected; { Owner: First( Teams ) } )
```

Diese Vorgehensweise unterscheidet sich nicht von einer normalen Suche, da die APP den Typ der **ersten (Teams)** kennt. Wenn Sie den ersten Benutzer stattdessen verwenden möchten, ersetzen Sie diesen Teil durch den **ersten (Benutzer)** . Die **Patch** -Funktion weiß, dass das Feld " **Owner** " auf einen dieser beiden Entitäts Typen festgelegt werden kann.

So fügen Sie die Funktion der APP hinzu:

1. Wählen Sie im Struktur **Ansichts** Bereich das Optionsfeld **Steuerelement und die beiden** Kombinations **Feld** -Steuerelemente gleichzeitig aus.

1. Wählen Sie im Menü "Ellipsen" die Option **diese Elemente kopieren**aus.

    > [!div class="mx-imgBorder"]
    > ![eine Kopie mehrerer Steuerelemente mithilfe der Strukturansicht](media/working-with-references/patch-copy.png)

1. Wählen Sie im gleichen Menü **Einfügen**aus.

    > [!div class="mx-imgBorder"]
    > ![Einfügen mehrerer Steuerelemente mithilfe der Strukturansicht](media/working-with-references/patch-paste.png)

1. Verschieben Sie die kopierten Steuerelemente auf die Rechte Seite des Katalogs.

    > [!div class="mx-imgBorder"]
    > ![haben kopierte Steuerelemente auf die Rechte Seite der Galerie verschoben](media/working-with-references/patch-position.png)

1. Wählen Sie das **kopierte** Optionsfeld aus, und ändern Sie dann die folgenden Eigenschaften:

    - Elemente: `[ "Users"; "Teams" ]`
    - Standard: `If( IsType( Gallery1.Selected.Owner; Users ); "Users"; "Teams" )`

    > [!div class="mx-imgBorder"]
    > ![die gesamte Auswahl aus dem Steuerelement "Radio" entfernt](media/working-with-references/patch-noall.png) 

1. Wählen Sie im options **Feld** **Benutzer** aus, damit das Kombinations Feld **-Steuerelement** , das Benutzer auflistet, sichtbar ist.

1. Wählen Sie das sichtbare Kombinations **Feld** -Steuerelement aus, und legen Sie dann die **defaultselecteditems** -Eigenschaft auf diese Formel fest:

    ```powerapps-comma
    If( IsType( Gallery1.Selected.Owner; Users );
        AsType( Gallery1.Selected.Owner; Users );
        Blank()
    )
    ```

    > [!div class="mx-imgBorder"]
    > ![Standardeigenschaften Satz für das Kombinations Feld "Benutzer"](media/working-with-references/patch-default-users.png)

1. Wählen Sie im options **Feld** **Teams** aus, sodass das Kombinations Feld **-Steuerelement** , das die Teams auflistet, sichtbar ist.

1. Wählen Sie **das Options** Feld Steuerelement aus, um die Auswahl vom jetzt unsichtbar-Kombinations **Feld** -Steuerelement für Benutzer zu entfernen.

1. Wählen Sie das sichtbare Kombinations **Feld** -Steuerelement für Teams aus, und legen Sie dann die Eigenschaft **defaultselecteditems** auf diese Formel fest:

    ```powerapps-comma
    If( IsType( Gallery1.Selected.Owner; Teams );
        AsType( Gallery1.Selected.Owner; Teams );
        Blank()
    )
    ```

    > [!div class="mx-imgBorder"]
    > ![Standardeigenschaften Satz für das Kombinations Feld "Teams"](media/working-with-references/patch-default-teams.png)

1. Fügen Sie ein **Schalt** Flächen-Steuerelement ein, verschieben Sie es unter das Kombinations **Feld** -Steuerelement, und legen Sie die **Text** -Eigenschaft der Schaltfläche auf `"Patch Owner"`

1. Legen **Sie die onselect** -Eigenschaft der Schaltfläche auf die folgende Formel fest:

    ```powerapps-comma
    Patch( Accounts; Gallery1.Selected;
        { Owner: If( Radio1_1.Selected.Value = "Users";
                ComboBox1_2.Selected;
                ComboBox1_3.Selected ) } )
    ```

    > [!div class="mx-imgBorder"]
    > ![Formel für Schaltflächen-Steuerelement](media/working-with-references/patch-button.png)

In den **kopierten** **Steuerelementen für** Options Felder und Kombinations Felder wird der Besitzer des aktuell ausgewählten Kontos im Katalog angezeigt. Mit denselben Steuerelementen können Sie den Besitzer des Kontos auf ein beliebiges Team oder einen Benutzer festlegen, indem Sie die Schaltfläche auswählen:

> [!div class="mx-imgBorder"]
> ![Animation, die den Patch des Besitzers mit einem Benutzer oder einem Team anzeigt](media/working-with-references/patch-allthree.gif)

## <a name="show-the-owner-by-using-a-form"></a>Anzeigen des Besitzers mithilfe eines Formulars

Sie können ein **Besitzer** Feld innerhalb eines Formulars anzeigen, indem Sie eine benutzerdefinierte Karte hinzufügen. Zum Zeitpunkt der Erstellung dieses Artikels können Sie den Wert des Felds nicht mit einem Formular Steuerelement ändern.

1. Fügen Sie ein **Bearbeitungs Formular** -Steuerelement ein, und ändern Sie dann die Größe, und verschieben Sie es in die untere rechte Ecke.

1. Öffnen Sie die Liste **Datenquelle** auf der Registerkarte **Eigenschaften** in der Nähe der rechten Seite des Bildschirms, und wählen Sie dann **Konten**aus.

    > [!div class="mx-imgBorder"]
    > ![Formular Steuerelement, das zusätzliche Felder mit leeren Werten anzeigt](media/working-with-references/form-insert.png)  

1. Legen Sie die **Item** -Eigenschaft des Formulars auf `Gallery1.Selected` fest.

    > [!div class="mx-imgBorder"]
    > ![Formular Steuerelement, das zusätzliche Felder anzeigt, die aus dem ausgewählten Element im Katalog aufgefüllt werden](media/working-with-references/form-item.png)

1. Wählen Sie auf der Registerkarte **Eigenschaften** in der Nähe der rechten Seite des Bildschirms die Option **Felder bearbeiten**aus.

1. Wählen Sie im **Bereich Felder** die Auslassungs Punkte aus, und wählen Sie dann **benutzerdefinierte Karte hinzufügen**aus.

    > [!div class="mx-imgBorder"]
    > ![Befehl zum Hinzufügen einer benutzerdefinierten Karte](media/working-with-references/form-customcard.png)

    Die neue Karte wird am unteren Rand des Formular Steuer Elements angezeigt.

1. Ändern Sie die Größe der Karte nach Bedarf, um den gesamten Text anzuzeigen.

    > [!div class="mx-imgBorder"]
    > ![eingefügte benutzerdefinierte Karte leer](media/working-with-references/form-inserted-customcard.png)

1. Fügen Sie ein **Label** -Steuerelement in die benutzerdefinierte Karte ein, und legen Sie dann die **Text** -Eigenschaft der Bezeichnung auf die im Katalog verwendete Formel fest:

    ```powerapps-comma
    If( IsType( ThisItem.Owner; Teams );
        "Team: " & AsType( ThisItem.Owner; Teams ).'Team Name';
        "User: " & AsType( ThisItem.Owner; Users ).'Full Name' )
    ```

    > [!div class="mx-imgBorder"]
    > ![benutzerdefinierte Karte, die das Besitzer Feld in einem Label-Steuerelement anzeigt](media/working-with-references/form-displayowner.png)

Für jede Auswahl im Katalog werden weitere Felder des Kontos, einschließlich des Besitzers des Datensatzes, im Formular angezeigt. Wenn Sie den Besitzer mithilfe der **patchschaltfläche** ändern, zeigt das Formular Steuerelement auch diese Änderung an.

> [!div class="mx-imgBorder"]
> ![Animation, die anzeigt, dass das Formular Steuerelement auf Änderungen im Katalog reagiert](media/working-with-references/form-allthree.gif)

## <a name="show-the-fields-of-a-customer"></a>Anzeigen der Felder eines Kunden

In Common Data Service handelt es sich bei dem Feld für die **Kunden** Suche um eine weitere polymorphe Suche, die dem **Besitzer**sehr ähnlich ist.

Der **Besitzer** ist auf einen pro Entität beschränkt, aber Entitäten können NULL, ein oder mehrere **Kunden** Suchfelder enthalten. Die Entität " **Contacts** " enthält das Feld " **Firmen Name** ", bei dem es sich um ein **Kunden** Suchfeld handelt.

> [!div class="mx-imgBorder"]
> ![Contact-Entität, die das Feld Firmen Name als nicht erforderlicher Kunden Datentyp anzeigt](media/working-with-references/customer-companyname.png)

Sie können einer Entität weitere **Kunden** Suchfelder hinzufügen, indem Sie den **Customer** -Datentyp für ein neues Feld auswählen.

![Kunden Datentyp aus der Liste der Datentypen beim Erstellen eines Felds](media/working-with-references/customer-datatype.png)

Ein **Kunden** Suchfeld kann auf einen Datensatz entweder von der **Accounts** -Entität oder der **Contacts** -Entität verweisen. Sie verwenden die **istype** -und **astype** -Funktionen für diese Entitäten. nun ist es ein guter Zeitpunkt, Sie als Datenquellen hinzuzufügen (Sie können **Teams** und **Benutzer** an Ort und Stelle lassen).

> [!div class="mx-imgBorder"]
> ![Konten, Teams, Benutzer und Kontakte Entitäten im Datenbereich](media/working-with-references/customer-datasources.png)

Die Behandlung der Felder " **Kunde** " und " **Besitzer** " ist so ähnlich, dass Sie die APP buchstäblich kopieren können (**Datei**  >  "**Speichern**unter" und dann einen anderen Namen) und diese einfachen Ersetzungen vornehmen:

| Ort | **Besitzer** Beispiel | **Kunden** Beispiel |
|----------|-----------|------------------|
| Jahres | **Eigentor** | **"Kunden Name"** |
| Jahres | **Nutzers** | **Buchhaltungs** |
| Jahres | **Teams** | **Partner** |
| **Items** -Eigenschaft des Katalogs | **Buchhaltungs** | **Partner** |
| **Items** -Eigenschaft des Formulars | **Buchhaltungs** | **Partner** |
| Das erste Argument von **Patch**<br>in der **onselect** -Eigenschaft der Schaltfläche | **Buchhaltungs** | **Partner** |
| Eigenschaft ' **Items** ' Filtern | **[&nbsp;"All";&nbsp;"Users";&nbsp;"Teams"&nbsp;]** | **[&nbsp;"All";&nbsp;"Accounts";&nbsp;"Contacts"&nbsp;]** |
| **Items** -Eigenschaft des patchradios | **["Users"; "Teams"]** | **["Accounts"; "Contacts"]** |
| **Sichtbare** Eigenschaft des Kombinations Felds | **"Benutzer"** und **"Teams"** | **"Accounts"** und **"Contacts** " |

Der neue Katalog sollte z. b. über diese **Items** -Eigenschaft verfügen:

```powerapps-comma
Filter( Contacts;
    Radio1.Selected.Value = "All"
    Or (Radio1.Selected.Value = "Accounts" And 'Company Name' = ComboBox1.Selected)
    Or (Radio1.Selected.Value = "Contacts" And 'Company Name' = ComboBox1_1.Selected)
)
```

> [!div class="mx-imgBorder"]
> ![Kunden-APP, die von der Besitzer-App abgeleitet wurde und einfache Änderungen angewendet wurden](media/working-with-references/customer-simple-update.png)

Zwei wichtige Unterschiede zwischen **Kunde** und **Besitzer** erfordern ein Update der Formeln innerhalb des Katalogs und des Formulars:

1. 1: n-Beziehungen zwischen **Konten** und **Kontakten** haben Vorrang, wenn Sie auf diese Entitäts Typen anhand ihres Namens verweisen. Verwenden Sieanstelle von Konten **\[\@Konten]** ; Verwenden Sieanstelle von Kontakten **\[\@Kontakte]** . Mit dem [globalen mehrdeutigkeits Operator](functions/operators.md#disambiguation-operator)stellen Sie sicher, dass Sie auf den Entitätstyp in **istype** und **astype**verweisen. Dieses Problem ist nur im Daten Satz Kontext der Katalog-und Formular Steuerelemente vorhanden.

1. Das Feld " **Besitzer** " muss über einen Wert verfügen, **Kunden** Felder können jedoch *leer*sein. Um das richtige Ergebnis ohne Typnamen anzuzeigen, testen Sie diesen Fall mit der [ **isblank** -Funktion](functions/function-isblank-isempty.md), und zeigen Sie stattdessen eine leere Text Zeichenfolge an.

Beide Änderungen befinden sich in derselben Formel, die auf der benutzerdefinierten Karte im Formular und in der **Text** -Eigenschaft des Label-Steuer Elements des Katalogs angezeigt wird:

```powerapps-comma
If( IsBlank( ThisItem.'Company Name' ); "";
    IsType( ThisItem.'Company Name'; [@Accounts] );
        "Account: " & AsType( ThisItem.'Company Name'; [@Accounts] ).'Account Name';
    "Contact: " & AsType( ThisItem.'Company Name'; [@Contacts] ).'Full Name'
)
```

> [!div class="mx-imgBorder"]
> ![Eigenschaft ' Text aktualisieren ' des Untertitel Label-Steuer Elements in der Galerie](media/working-with-references/customer-update.png)

Mit diesen Änderungen können Sie das Feld " **Unternehmens Name** " in der Entität " **Kontakte** " anzeigen und ändern.

> [!div class="mx-imgBorder"]
> ![Animation, die zeigt, wie die Auswahl eines Kontakts die anderen Steuerelemente und das Formular ändert](media/working-with-references/customer-allthree.gif)

## <a name="understand-regarding-lookup-fields"></a>Informationen zu Nachschlage Feldern

Das Nachschlage Feld " **betrifft** " unterscheidet sich geringfügig von denen, mit denen Sie in diesem Thema bereits gearbeitet haben. Zuerst wenden Sie zunächst die Muster an, die in diesem Thema beschrieben werden. Anschließend lernen Sie weitere Tricks kennen.

Sie können einfach mit der **Faxe** -Entität beginnen. Diese Entität hat ein polymorph **für** das Nachschlage Feld, das auf **Konten**, **Kontakte**und andere Entitäten verweisen kann. Sie können die APP für **Kunden** nutzen und für **Faxe**ändern.

| Ort | **Kunden** Beispiel | **Faxe** -Beispiel |
|----------|-----------|------------------|
| Jahres | **"Kunden Name"** | **Auf** |
| **Items** -Eigenschaft des Katalogs | **Partner** | **Empfangen** |
| **Items** -Eigenschaft des Formulars | **Partner** | **Empfangen** |
| Das erste Argument von **Patch**<br> in der **onselect** -Eigenschaft der Schaltfläche | **Partner** | **Empfangen** |

Auch hier müssen Sie eine Datenquelle hinzufügen: dieses Mal für **Faxe**. Wählen Sie auf der Registerkarte **Ansicht** die Option **Datenquellen**:

> [!div class="mx-imgBorder"]
> ![Datenbereich mit Konten, Teams, Benutzern, Kontakten und faxentitäten](media/working-with-references/faxes-datasources.png)

Ein wichtiger Unterschied **in Bezug** darauf ist, dass er nicht auf **Konten** und **Kontakte**beschränkt ist. Tatsächlich ist die Liste der Entitäten mit benutzerdefinierten Entitäten erweiterbar. Der größte Teil der APP kann diesen Punkt unverändert lassen, aber Sie müssen die Formel für die Bezeichnung im Katalog und in dem Formular aktualisieren:

```powerapps-comma
If( IsBlank( ThisItem.Regarding ); "";
    IsType( ThisItem.Regarding; [@Accounts] );
        "Account: " & AsType( ThisItem.Regarding; [@Accounts] ).'Account Name';
    IsType( ThisItem.Regarding; [@Contacts] );
        "Contacts: " & AsType( ThisItem.Regarding; [@Contacts] ).'Full Name';
    ""
)
```

> [!div class="mx-imgBorder"]
> ![aktualisierte Text-Eigenschaft für das Untertitel-Steuerelement für Informationen zu Such Vorgängen](media/working-with-references/regarding-label.png)

Nachdem Sie diese Änderungen vorgenommen haben, arbeiten Sie mit der Suche **in Bezug auf** die Suche, ebenso wie der **Besitzer** und die **Kunden** Suchvorgänge.

> [!div class="mx-imgBorder"]
> ![Animation, die zeigt, wie die Auswahl eines Elements im Katalog die anderen Steuerelemente und das Formular ändert](media/working-with-references/regarding-allthree.gif)

## <a name="understand-regarding-relationships"></a>Informationen zu Beziehungen

Unter **scheidet sich** von **Besitzer** und **Kunde** , da die erste Beziehung eine n:1-Beziehung einschließt. Definitionsgemäß können Sie mit einer umgekehrten 1: n-Beziehung **zunächst (Konten) schreiben. Faxe**.

Sehen wir uns nun die Entitäts Definitionen an. In Common Data Service werden Entitäten wie **Faxe**, **Tasks**, **e-Mails**, **Notizen**, **Telefonanrufe**, **Buchstaben**und **Chats** als [*Aktivitäten*](../../developer/common-data-service/activity-entities.md)bezeichnet. Sie können auch eigene [benutzerdefinierte Aktivitäts Entitäten](../../developer/common-data-service/custom-activities.md)erstellen. Wenn Sie eine Aktivitäts Entität anzeigen oder erstellen, werden die Einstellungen unter **Weitere Einstellungen**angezeigt.

![Aktivitäts Entitäts Einstellung beim Erstellen einer Entität](media/working-with-references/activity-entitytype.png)

Andere Entitäten können mit einer Aktivitäts Entität verknüpft werden, wenn Sie als *Aktivitäts Aufgabe* in den Einstellungen der Entität aktiviert sind. **Konten**, **Kontakte**und viele andere Standard Entitäten sind so festgelegt (auch unter **Weitere Einstellungen**).

![Aktivität ' Aktivitäts Aufgabe ' beim Erstellen einer Entität](media/working-with-references/activity-entityuse.png)

Alle Aktivitäts Entitäten und Aktivitäts Aufgaben Entitäten verfügen über eine implizite Beziehung. Wenn Sie den Filter oben auf dem Bildschirm auf **alle** ändern, wählen Sie die **Faxe** -Entität aus, und wählen Sie dann die Registerkarte **Beziehungen** aus. alle Entitäten, die als Ziel für eine **bezüglich** der Suche gelten können, werden angezeigt.

> [!div class="mx-imgBorder"]
> ![Beziehungen der Faxe-Entität, die für n:1-Beziehungen angezeigt werden](media/working-with-references/activity-manytoone.png)

Wenn Sie die Beziehungen für die Entität **Accounts** anzeigen, werden alle Entitäten angezeigt, **die als Quelle für ein Nachschlage** Feld angezeigt werden können.

> [!div class="mx-imgBorder"]
> ![Beziehungen der Konto Entität, die in Bezug auf 1: n-Beziehungen angezeigt werden](media/working-with-references/activity-onetomany.png)

Was bedeutet das alles?

- Wenn Sie Formeln schreiben, müssen Sie Bedenken, dass die Liste der Aktivitäts Entitäten nicht korrigiert ist, und Sie können eigene erstellen. Die Formel muss eine Aktivitäts Entität, die Sie nicht erwartet haben, ordnungsgemäß behandeln.
- Aktivitäts Tasks und Aktivitäten haben eine 1: n-Beziehung. Sie können problemlos nach allen Faxe Fragen, die sich auf ein Konto beziehen.

So untersuchen Sie dieses Konzept in der APP:

1. Einen weiteren Bildschirm hinzufügen.

    > [!div class="mx-imgBorder"]
    > ![einen leeren Bildschirm einfügen](media/working-with-references/activitypointer-newscreen.png)

1. Fügen Sie ein Katalog-Steuerelement ein, ändern Sie die Größe, und verschieben Sie es dann auf die linke Seite des Bildschirms.

1. Legen Sie auf der Registerkarte **Eigenschaften** in der Nähe der rechten Seite des Bildschirms die **Elemente** des Katalogs auf **Accounts**fest.

    > [!div class="mx-imgBorder"]
    > ![Elemente auf Konten im Eigenschaften Bereich festlegen](media/working-with-references/activitypointer-accounts.png)

1. Legen Sie das Layout des Katalogs auf **Title**fest, und legen Sie dann das Feld Title auf **Account Name**fest.

    > [!div class="mx-imgBorder"]
    > ![im Eigenschaften Bereich Layout auf Titel für Galerie Steuerelement festlegen](media/working-with-references/activitypointer-account-name.png)

1. Fügen Sie einen zweiten Katalog hinzu, ändern Sie die Größe, und verschieben Sie ihn dann auf die Rechte Seite des Bildschirms.

1. Legen Sie die **Items** -Eigenschaft des neuen Katalogs auf `Gallery2.Selected.Faxes` fest.

    In diesem Schritt wird die gefilterte Liste der Faxe für ein bestimmtes Konto zurückgegeben.

    > [!div class="mx-imgBorder"]
    > ![legen Sie die Items-Eigenschaft des Katalogs fest, der Faxe anzeigt](media/working-with-references/activitypointer-faxes.png)

1. Legen Sie das Layout des Katalogs auf **Titel und Untertitel**fest, und legen Sie dann das Feld Titel so fest, dass das Feld **Betreff** (in klein **Buchstaben) angezeigt**wird.

    > [!div class="mx-imgBorder"]
    > ![Titel auf Betreff-Feld festlegen](media/working-with-references/activitypointer-subject.png)

Wenn Sie ein Element in der Liste der Konten auswählen, werden in der Liste der Faxe Faxe nur für dieses Konto angezeigt.

> [!div class="mx-imgBorder"]
> ![Animation, die die Auswahl in der Konten Galerie anzeigt, die die Liste der Faxe steuert](media/working-with-references/activitypointer-allthree.gif)

## <a name="activity-entity"></a>Aktivitäts Entität

Wie im vorherigen Abschnitt beschrieben, können Sie alle Faxe für ein Konto anzeigen. Sie können jedoch auch alle Aktivitäten für ein Konto anzeigen, einschließlich Faxe, e-Mail-Nachrichten, Telefonanrufe und andere Interaktionen.

Im letzteren Szenario verwenden Sie die Entität **Activity** . Sie können diese Entität anzeigen, indem Sie **alle** in der oberen rechten Ecke aktivieren, um den Filter aus der Liste der Entitäten zu entfernen.

> [!div class="mx-imgBorder"]
> ![Liste der Entitäten, die die Aktivitäts Entität anzeigt](media/working-with-references/activitypointer-entity.png)

Die **Aktivitäts** Entität ist eine besondere. Wenn Sie der **Faxe** -Entität einen Datensatz hinzufügen, erstellt das System auch einen Datensatz in der **Aktivitäts** Entität mit den Feldern, die für alle Aktivitäts Entitäten gemeinsam sind. Diese Felder sind eine der interessantesten **Themen** .

Sie können alle Aktivitäten anzeigen, indem Sie im vorherigen Beispiel nur eine Zeile ändern. Ersetzen Sie `Gallery2.Selected.Faxes` durch `Gallery2.Selected.Activities`.

> [!div class="mx-imgBorder"]
> ![Änderung der Items-Eigenschaft für den zweiten Katalog, Ändern von Faxe in Aktivitäten](media/working-with-references/activitypointer-gallery.png)

Datensätze stammen aus der **Aktivitäts** Entität, aber Sie können trotzdem die **istype** -Funktion verwenden, um zu ermitteln, welche Art von Aktivität Sie sind. Vor der Verwendung von **istype** mit einem Entitätstyp müssen Sie die Datenquelle hinzufügen.

> [!div class="mx-imgBorder"]
> ![Datenbereich, der alle Entitäten anzeigt, die für die istype-Funktion erforderlich sind](media/working-with-references/activity-datasources.png)

Mit dieser Formel können Sie den Daten Satz Typen in einem Label-Steuerelement innerhalb des Katalogs anzeigen:

```powerapps-comma
If( IsType( ThisItem; [@Faxes] ); "Fax";
    IsType( ThisItem; [@'Phone Calls'] ); "Phone Call";
    IsType( ThisItem; [@'Email Messages'] ); "Email Message";
    IsType( ThisItem; [@Chats] ); "Chat";
    "Unknown"
)
```

> [!div class="mx-imgBorder"]
> ![legen Sie die Text-Eigenschaft auf "Formel" fest, um Informationen für Faxe, Telefonanrufe und andere Aktivitäten anzuzeigen](media/working-with-references/activitypointer-type.png)

Sie können auch **astype** verwenden, um auf die Felder des jeweiligen Typs zuzugreifen. Mit dieser Formel wird z. b. der Typ der einzelnen Aktivitäten bestimmt, und bei Telefon anrufen werden die Telefonnummer und die Telefonnummer der **Telefonnummern** -Entität angezeigt:

```powerapps-comma
If( IsType( ThisItem; [@Faxes] ); "Fax";
    IsType( ThisItem; [@'Phone Calls'] );
       "Phone Call: " &
       AsType( ThisItem; [@'Phone Calls'] ).'Phone Number' &
       " (" & AsType( ThisItem; [@'Phone Calls'] ).Direction & ")";
    IsType( ThisItem; [@'Email Messages'] ); "Email Message";
    IsType( ThisItem; [@Chats] ); "Chat";
    "Unknown"
)
```

> [!div class="mx-imgBorder"]
> ![erweiterte Text Eigenschaft mit weiteren Informationen für einen Telefonanruf](media/working-with-references/activitypointer-phonecall.png)

Folglich zeigt die APP eine komplette Liste der Aktivitäten an. Das **Betrefffeld** wird für alle Arten von Aktivitäten angezeigt, und zwar unabhängig davon, ob die Formel Sie berücksichtigt. Für Typen von Aktivitäten, die Sie kennen, können Sie deren Typnamen und typspezifische Informationen zu jeder Aktivität anzeigen.

> [!div class="mx-imgBorder"]
> ![ausgefülltes Bildschirm, der Informationen für verschiedene Arten von Aktivitäten anzeigt](media/working-with-references/activitypointer-complete.png)

## <a name="notes-entity"></a>Notes-Entität

Bis jetzt basieren alle **in Bezug** auf die Beispiele auf Aktivitäten, aber die **Notes** -Entität stellt einen anderen Fall dar.

Beim Erstellen einer Entität können Sie Anlagen aktivieren.

> [!div class="mx-imgBorder"]
> ![Aktivieren von Anlagen und Notizen beim Erstellen einer Entität](media/working-with-references/notes-entity.png)

Wenn Sie das Kontrollkästchen zum Aktivieren von Anlagen aktivieren, erstellen Sie eine Beziehungs Beziehung mit der **Notizen** -Entität, **wie in dieser** Abbildung für die **Accounts** -Entität gezeigt:

> [!div class="mx-imgBorder"]
> ![Konto Entität, die eine Beziehung zu Notizen über eine 1: n-Beziehung anzeigt](media/working-with-references/notes-relationships.png)

Abgesehen von diesem Unterschied verwenden Sie die Suche in Bezug auf die Suche in **Bezug** auf die Verwendung von Aktivitäten. Für Anlagen aktivierte Entitäten verfügen über eine 1: n-Beziehung zu **Notizen**, wie in diesem Beispiel:

`First( Accounts ).Notes`

> [!NOTE]
> Zum Zeitpunkt der Erstellung dieses Artikels **ist die "** **Hinweise** "-Entität nicht verfügbar. Sie können nicht anhand des Felds "Informationen" lesen oder filtern, und Sie können **das Feld nicht** mithilfe von " **Patch**" festlegen.
>
> Allerdings ist die 1: n-Beziehung mit den umgekehrten **hinweisen** verfügbar, sodass Sie eine Liste der Notizen für einen Datensatz filtern können, der für Anlagen aktiviert ist. Sie können auch die Funktion "in [**Beziehung**](functions/function-relate-unrelate.md) " verwenden, um der **Notizen** -Tabelle eines Datensatzes einen Hinweis hinzuzufügen, aber der Hinweis muss zuerst erstellt werden, wie in diesem Beispiel:
>
>`Relate( ThisItem.Notes; Patch( Notes; Defaults( Notes ); { Title: "A new note" } ) )`

## <a name="activity-parties"></a>Aktivitäts Parteien

Zum Zeitpunkt der Erstellung dieses Artikels werden Aktivitäts Parteien von Canvas-apps nicht unterstützt.