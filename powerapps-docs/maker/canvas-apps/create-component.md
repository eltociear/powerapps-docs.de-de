---
title: Erstellen Sie eine Komponente für Canvas-apps | Microsoft-Dokumentation
description: Einführung in die wiederverwendbarkeit von Komponenten für Canvas-apps
author: yifwang
ms.service: powerapps
ms.topic: article
ms.date: 12/12/2018
ms.author: yifwang
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 0a20218d3670775f67b26c907ce5a3a54fa0af7b
ms.sourcegitcommit: aa9f78c304fe46922aecfe3b3fadb6bda72dfb23
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2019
ms.locfileid: "66216667"
---
# <a name="create-a-component-for-canvas-apps"></a>Erstellen Sie eine Komponente für Canvas-apps

> [!IMPORTANT]
> Diese Funktion ist noch experimentell und standardmäßig deaktiviert. Weitere Informationen finden Sie unter [experimentell und Vorschaufunktionen](working-with-experimental.md).

Komponenten sind wiederverwendbare Bausteine für Canvas-apps, damit app-Entwickler Erstellen benutzerdefinierter Steuerelemente in einer app oder für apps verwenden können. Erweiterte Funktionen, beispielsweise die benutzerdefinierten Eigenschaften ermöglichen Sie es komplexe Funktionen in Komponenten. Dieser Artikel enthält Konzepte der Komponente und einige Beispiele.

Komponenten sind hilfreich bei der Erstellung von größeren apps, die ähnliche Steuerelementmuster verfügen. Wenn Sie eine Komponentendefinition aktualisieren, werden alle Instanzen in der app Ihre Änderungen wider. Sie können die Leistung auch verbessern, indem Sie eine oder mehrere Komponenten verwenden, da Sie nicht kopieren und Einfügen von Steuerelementen, die Duplikate Mehraufwand. Komponenten auch gemeinsame Entwicklung vereinfacht und standardisiert Aussehen und Verhalten in einer Organisation.

## <a name="prerequisite"></a>Voraussetzung

Öffnen der **Anwendungseinstellungen** auf **Erweiterte Einstellungen**, und aktivieren Sie die Funktion, als auch sicherstellen, dass **verbesserte app-Rendering** ist ebenfalls aktiviert.

## <a name="component-canvas"></a>Komponente canvas

Sie können eine Komponente mit dem Erstellen der **Komponenten** Menü auf der **einfügen** Registerkarte oder, wie in der nächsten Grafik dargestellt, in der linken Navigationsleiste auf. Diese Liste zeigt die Komponenten, die in der app, sortiert nach Zeitpunkt der Erstellung definiert sind.

![Listenansicht der Komponente](./media/create-component/list-view.png)

Unabhängig davon, welchen Ansatz Sie nutzen, eine leere Leinwand wird angezeigt, in dem Sie Steuerelemente als Teil der Komponentendefinition hinzufügen können. Wenn Sie eine Komponente im Zeichenbereich bearbeiten, aktualisieren Sie die Instanzen der gleichen Komponente in anderen app-Bildschirme und andere apps.

Wenn Sie einen Bildschirm ausgewählt haben, können Sie eine Komponente auswählen, aus der Liste der vorhandenen Komponenten in der linken Navigationsleiste klicken oder die **Komponenten** Menü auf der **einfügen** Registerkarte. Wenn Sie eine Komponente auswählen, fügen Sie eine Instanz dieser Komponente auf dem Bildschirm, wie Sie ein Steuerelement einfügen.

## <a name="scope"></a>Umfang

Stellen Sie sich eine Komponente als eine gekapselte Blackbox mit Eigenschaften wie die Schnittstelle. Steuerelemente in der Komponente von außerhalb der Komponente kann nicht auf, und Sie können nicht auf irgendetwas außerhalb der Komponente aus, in der Komponente verweisen. Wenn Sie versuchen, tritt ein Fehler auf. Bereichseinschränkungen behalten den Datenvertrag von einer Komponente aus, einfach und zusammenhängende, und es hilft, nahtlose Komponente-Definitionsupdates, insbesondere für apps zu ermöglichen. Sie können den Datenvertrag der Komponente aktualisieren, indem Sie eine oder mehrere benutzerdefinierte Eigenschaften erstellen.

## <a name="variables"></a>Variablen

Komponenten unterstützen nicht die **"updatecontext"** -Funktion, aber Sie können Variablen erstellen oder aktualisieren in einer Komponente mithilfe der **festgelegt** Funktion. Der Bereich dieser Variablen auf die Komponente beschränkt ist, aber Sie können von außerhalb der Komponente zugreifen, durch die Nutzung von benutzerdefinierten Eigenschaften.

## <a name="import-and-export"></a>Importieren und exportieren

Wählen Sie zum Importieren von ein oder mehrere Komponenten aus einer app in einer anderen **importieren Komponenten** in der Dropdown-Liste der Komponenten. Ein Dialogfeld listet alle apps, die Komponenten enthalten, die Berechtigung zum Bearbeiten. Wählen Sie eine app, und wählen Sie dann **importieren** So importieren Sie die neueste veröffentlichte Version der Komponenten in dieser app. Nachdem Sie mindestens eine Komponente importiert haben, können Ihre Kopie bearbeiten und löschen, die Sie nicht benötigen.

> [!div class="mx-imgBorder"]
> ![Importieren Komponenten (Dialogfeld)](./media/create-component/import-components.png)

Wenn Sie eine Komponente exportiert haben, erstellen Sie eine lokale Datei, die in einer anderen app importiert werden kann. Wenn die app eine geänderte Version der gleichen Komponente enthält, werden Sie aufgefordert zu entscheiden, ob die geänderte Version ersetzen oder der Import Abbrechen. 

## <a name="custom-properties"></a>Benutzerdefinierte Eigenschaften

Eine Komponente kann empfangen der Eingabewerten und Daten ausgeben, wenn Sie eine oder mehrere benutzerdefinierte Eigenschaften erstellen. Diese Szenarien sind erweiterte und müssen Sie verstehen, Formeln und Verträge zu binden.

Eine input-Eigenschaft ist, wie eine Komponente empfängt, auf Daten in der Komponente verwendet werden. Eingabeeigenschaften angezeigt, der **Eigenschaften** Registerkarte im rechten Bereich, wenn eine Instanz der Komponente ausgewählt ist. Sie können mit Ausdrücken oder Formeln Eingabeeigenschaften konfigurieren, ebenso, wie Sie die Standardeigenschaften in anderen Steuerelementen konfigurieren. Andere Steuerelemente haben Eigenschaften, geben Sie z. B. die **Standard** Eigenschaft eine **Texteingabe** Steuerelement.

Ausgabeeigenschaften können Daten oder eine Komponente einen Status ausgeben. Z. B. die **ausgewählte** Eigenschaft für eine **Katalog** Steuerelement ist eine Output-Eigenschaft. Wenn Sie eine Output-Eigenschaft erstellen, können Sie bestimmen, was andere Steuerelemente verweisen können, um den Komponentenstatus.

Weitere in dieser exemplarischen Vorgehensweise werden diese Konzepte erläutert.

## <a name="create-an-example-component"></a>Erstellen Sie eine Beispielkomponente

In diesem Beispiel erstellen Sie eine Menükomponente, die ähnelt dieser Abbildung und in dem Sie den Text ändern und in mehreren Bildschirmen, apps oder beides verwenden können:

![Endgültiger Katalog](./media/create-component/menu-instance.png)

1. Erstellen Sie in PowerApps Studio eine leere app.

1. Klicken Sie in der linken Navigationsleiste auf die Liste der Komponenten öffnen, und wählen Sie dann **neue Komponente**.

    ![Liste der Komponenten](./media/create-component/component-list.png)

1. Beim zeigen auf die neue Komponente, wählen Sie die Auslassungspunkte (...), **umbenennen**, und fügen oder geben Sie dann **MenuComponent**.

1. Legen Sie im rechten Bereich, der Komponente-Breite auf **150** und seine Höhe zu **250**, und wählen Sie dann **neue benutzerdefinierte Eigenschaft**.

    ![Neue Eigenschaft](./media/create-component/new-property.png)

1. In der **Anzeigenamen**, **Eigenschaftennamen**, und **Beschreibung** Felder geben oder fügen Sie **Elemente**.

    ![Anzeigename, Namen, Beschreibung Felder](./media/create-component/property-names.png)

    Wenn Sie einen Eigenschaftennamen angeben, keine Leerzeichen enthalten, da Sie beim Schreiben einer Formel mit diesem Namen für die Komponente verweisen werden (z. B. **ComponentName.PropertyName**).

    Der Anzeigename wird angezeigt, auf die **Eigenschaften** Registerkarte im rechten Bereich, wenn Sie die Komponente auswählen. Ein beschreibenden Anzeigenamen können Sie und andere Entwickler den Zweck dieser Eigenschaft verstanden haben. Die **Beschreibung** in einer QuickInfo angezeigt wird, wenn Sie auf den Anzeigenamen dieser Eigenschaft im zeigen die **Eigenschaften** Registerkarte.

1. In der **Datentyp** Liste **Tabelle**, und wählen Sie dann **erstellen**.

    ![Datentyp der Eigenschaft](./media/create-component/property-data-type.png)

    Die **Elemente** -Eigenschaftensatz auf einen Standardwert basierend auf dem Datentyp, den Sie angegeben, aber Sie können sie festlegen, um ein Wert, der Ihren Anforderungen entspricht. Wenn Sie den Datentyp angegeben **Tabelle** oder **Datensatz**, empfiehlt es sich zum Ändern des Werts, der die **Elemente** Eigenschaft, um das Datenschema zu entsprechen, die in der Komponente eingegeben werden sollen. In diesem Fall müssen Sie es in eine Liste von Zeichenfolgen ändern.

    Sie können den Wert der Eigenschaft in der Bearbeitungsleiste festlegen, wenn Sie den Namen der Eigenschaft wählen Sie auf die **Eigenschaften** Registerkarte im rechten Bereich.

    ![Benutzerdefinierte input-Eigenschaft auf der Registerkarte "Eigenschaften"](./media/create-component/properties-tab.png)

    Sie können auch die nächste Abbildung zeigt den Wert der Eigenschaft zu bearbeiten, auf die **erweitert** Registerkarte im rechten Bereich.

1. Legen Sie der Komponente **Elemente** -Eigenschaft auf diese Formel:

    ```powerapps-dot
    Table({Item:"SampleText"})
    ```

    ![Formel](./media/create-component/set-component-items.png)

1. Fügen Sie in der Komponente, die ein Leerzeichen vertikal **Katalog** Steuerelement.

1. Stellen Sie sicher, dass die Eigenschaftenliste die **Elemente** Eigenschaft (genauso wie in der Standardeinstellung), und legen Sie den Wert dieser Eigenschaft auf den folgenden Ausdruck:

    ```powerapps-dot
    MenuComponent.Items
    ```

    Auf diese Weise die **Elemente** Eigenschaft der **Katalog** -Steuerelement liest und hängt von der **Elemente** input-Eigenschaft der Komponente.

1. Festlegen der **Katalog** des Steuerelements **BorderThickness** Eigenschaft **1** und die zugehörige **TemplateSize** Eigenschaft **50**.

1. In der Vorlage des den **Katalog** Steuerelement, fügen einen **Bezeichnung** Steuerelement.

    ![Fügen Sie Bezeichnung hinzu, und legen Sie die Rahmen des Katalogs](./media/create-component/add-label.png)

Als Nächstes Sie die Komponente zu einem Bildschirm hinzufügen und geben Sie eine Tabelle mit Zeichenfolgen für die Komponente angezeigt.

1. Wählen Sie in der linken Navigationsleiste die Liste von Bildschirmen, und wählen Sie dann auf den Bildschirm.

    ![Standardbildschirm](./media/create-component/default-screen.png)

1. Auf der **einfügen** Registerkarte Öffnen der **Komponenten** Menü, und wählen Sie dann **MenuComponent**.

    ![Einfügen](./media/create-component/insert.png)

    Die neue Komponente wird mit dem Namen **MenuComponent_1** standardmäßig.

1. Legen Sie die **Elemente** Eigenschaft **MenuComponent_1** auf diese Formel:

    ```powerapps-dot
    Table({Item:"Home"}, {Item:"Admin"}, {Item:"About"}, {Item:"Help"})
    ```

    Diese Instanz ähnelt dieser Abbildung, aber Sie können den Text und andere Eigenschaften der einzelnen Instanzen anpassen.

    ![Endgültiger Katalog](./media/create-component/menu-instance.png)

Bisher haben Sie eine Komponente erstellt und an eine app hinzugefügt. Als Nächstes erstellen Sie eine Output-Eigenschaft, die das Element darstellt, das der Benutzer im Menü auswählt.

1. Öffnen Sie die Liste der Komponenten, und wählen Sie dann **MenuComponent**.

1. Wählen Sie im rechten Bereich die **Eigenschaften** Registerkarte, und wählen Sie dann **neue benutzerdefinierte Eigenschaft**.

1. In der **Anzeigenamen**, **Eigenschaftennamen**, und **Beschreibung** Felder geben oder fügen Sie **ausgewählte**.

1. Klicken Sie unter **Eigenschaftentyp**Option **Ausgabe**, und wählen Sie dann **erstellen**.

1. Auf der **erweitert** Registerkarte, legen Sie den Wert, der die **ausgewählte** Eigenschaft auf den folgenden Ausdruck, der die Zahl in der Name des Katalogs anpassen, bei Bedarf:

    ```powerapps-dot
    Gallery1.Selected.Item
    ```

    ![Bereich "Erweitert"](./media/create-component/advance.png)

1. Klicken Sie auf dem Standardbildschirm der app, fügen Sie eine Bezeichnung hinzu, und legen dessen **Text** Eigenschaft auf den folgenden Ausdruck, der die Zahl in den Namen der Komponente anpassen, falls erforderlich:

    ```powerapps-dot
    MenuComponent_1.Selected
    ```

    Beachten Sie, dass **MenuComponent_1** lautet der Name einer Instanz, die nicht den Namen der Komponentendefinition. Sie können eine beliebige Instanz umbenennen.

1. Während Sie die Alt-Taste gedrückt halten, wählen Sie alle Elemente im Menü aus.

    Die **Bezeichnung** -Steuerelement wider, das Menüelement, das Sie zuletzt ausgewählt.

## <a name="known-limitations"></a>Bekannte Einschränkungen

- Während ich dies schreibe, werden nicht Datenquellen mit Komponenten, gespeichert, sodass Formulare und Datentabellen deaktiviert sind.
- PowerApps unterstützt keine Auflistungen in Komponenten.
- Sie können keine Komponente in einem Katalog, einem Formular oder eine Datenkarte einfügen.
- Eine master Instanz einer Komponente ist eine lokale Master- und deren Bereich auf die app. Wenn Sie eine master-Instanz ändern, werden nur Kopien von der Komponente in der app die Änderung zu übernehmen. Kopien in anderen apps bleiben gleich, es sei denn, Sie die Bibliothek erneut importieren. Alle master-Instanzen in diesen apps werden automatisch erkannt und aktualisiert werden.
- Medien-Rohdateien kann nicht gepackt werden, wenn Sie eine Komponente importieren.
