---
title: Erstellen einer Komponente für Canvas-apps | Microsoft-Dokumentation
description: Einführung in wiederverwendbare Komponenten für Canvas-apps
author: yifwang
ms.service: powerapps
ms.topic: article
ms.date: 12/12/2018
ms.author: yifwang
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 857ca2c78da5b3a7ced4d4d09dfb335fab02d47c
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2019
ms.locfileid: "74678693"
ms.PowerAppsDecimalTransform: true
---
# <a name="create-a-component-for-canvas-apps"></a>Erstellen einer Komponente für Canvas-apps

> [!IMPORTANT]
> Diese Funktion ist in der Standardeinstellung immer noch experimentell und deaktiviert. Weitere Informationen finden Sie unter [experimentelle Features und Vorschau Features](working-with-experimental.md).

Komponenten sind wiederverwendbare Bausteine für Canvas-apps, damit App-Ersteller benutzerdefinierte Steuerelemente erstellen können, die in einer APP oder zwischen Apps verwendet werden können. Erweiterte Funktionen, wie z. b. benutzerdefinierte Eigenschaften, ermöglichen komplexe Funktionen in-Komponenten. In diesem Artikel werden die Komponenten Konzepte und einige Beispiele vorgestellt.

Komponenten sind nützlich, um größere apps mit ähnlichen Steuerelement Mustern zu entwickeln. Wenn Sie eine Komponenten Definition aktualisieren, spiegeln alle Instanzen in der APP Ihre Änderungen wider. Sie können die Leistung auch verbessern, indem Sie eine oder mehrere Komponenten verwenden, da Sie keine Steuerelemente kopieren und einfügen, wodurch der Verwaltungsaufwand dupliziert wird. Komponenten erleichtern außerdem die gemeinsame Entwicklung und standardisieren das Aussehen und fühlen in einer Organisation.

## <a name="prerequisite"></a>Voraussetzung

Öffnen Sie den Bildschirm **App-Einstellungen** , wählen Sie **Erweiterte Einstellungen**aus, und aktivieren Sie die Funktion, und stellen Sie sicher, dass das **verbesserte App-Rendering** ebenfalls aktiviert ist.

## <a name="component-canvas"></a>Komponentenbereich

Sie können eine Komponente über das Menü **Komponenten** auf der Registerkarte **Einfügen** oder, wie in der nächsten Abbildung gezeigt, auf der linken Navigationsleiste erstellen. Diese Liste zeigt die Komponenten, die in der APP definiert sind, sortiert nach Erstellungszeit.

![Komponenten Listenansicht](./media/create-component/list-view.png)

Unabhängig davon, welche Herangehensweise Sie annehmen, wird eine leere Canvas angezeigt, in der Sie Steuerelemente als Teil der Komponenten Definition hinzufügen können. Wenn Sie eine Komponente im Zeichenbereich bearbeiten, aktualisieren Sie Instanzen derselben Komponente in anderen APP-Bildschirmen und anderen apps.

Wenn Sie einen Bildschirm auswählen, können Sie eine Komponente aus der Liste der vorhandenen Komponenten in der linken Navigationsleiste oder im Menü **Komponenten** auf der Registerkarte **Einfügen** auswählen. Wenn Sie eine Komponente auswählen, fügen Sie eine Instanz dieser Komponente auf dem Bildschirm ein, und zwar genau so, wie Sie ein Steuerelement einfügen.

## <a name="scope"></a>Umfang

Betrachten Sie eine Komponente als gekapseltes schwarzes Feld mit Eigenschaften als Schnittstelle. Sie können nicht von außerhalb der Komponente auf Steuerelemente in der Komponente zugreifen, und Sie können nicht innerhalb der Komponente auf Elemente außerhalb der Komponente verweisen. Wenn Sie versuchen, wird ein Fehler angezeigt. Bereichs Einschränkungen sorgen dafür, dass der Datenvertrag einer Komponente einfach und zusammenhängend ist, und Sie hilft, nahtlose Komponenten Definitions Updates zu ermöglichen, insbesondere für apps. Sie können den Datenvertrag der Komponente aktualisieren, indem Sie eine oder mehrere benutzerdefinierte Eigenschaften erstellen.

## <a name="variables"></a>Instan

Komponenten unterstützen die **updatecontext** -Funktion nicht, Sie können jedoch Variablen in einer Komponente erstellen und aktualisieren, indem Sie die **set** -Funktion verwenden. Der Gültigkeitsbereich dieser Variablen ist auf die Komponente beschränkt, aber Sie können von außerhalb der Komponente auf Sie zugreifen, indem Sie benutzerdefinierte Ausgabe Eigenschaften nutzen.

## <a name="import-and-export"></a>Importieren und exportieren

Wenn Sie eine oder mehrere Komponenten aus einer APP in eine andere importieren möchten, wählen Sie in der Dropdown Liste der Komponenten die Option **Komponenten Importieren** aus. In einem Dialogfeld werden alle apps aufgelistet, die Komponenten enthalten, für die Sie über die Berechtigung zum Bearbeiten verfügen. Wählen Sie eine APP aus, und wählen Sie dann **importieren** aus, um die neueste veröffentlichte Version aller Komponenten in der APP zu importieren. Nachdem Sie mindestens eine Komponente importiert haben, können Sie Ihre Kopie bearbeiten und beliebig löschen.

> [!div class="mx-imgBorder"]
> ![Dialogfeld "Komponenten Importieren"](./media/create-component/import-components.png)

Wenn Sie eine Komponente exportieren, erstellen Sie eine lokale Datei, die Sie in eine andere App importieren können. Wenn die APP eine geänderte Version derselben Komponente enthält, werden Sie aufgefordert, zu entscheiden, ob die geänderte Version ersetzt oder der Import abgebrochen werden soll. 

## <a name="custom-properties"></a>Benutzerdefinierte Eigenschaften

Eine Komponente kann Eingabewerte empfangen und Daten ausgeben, wenn Sie eine oder mehrere benutzerdefinierte Eigenschaften erstellen. Diese Szenarien sind erweitert und erfordern das Verständnis von Formeln und Bindungs Verträgen.

Eine Eingabe Eigenschaft gibt an, wie eine Komponente Daten empfängt, die in der Komponente verwendet werden sollen. Eingabe Eigenschaften werden im rechten Bereich auf der Registerkarte **Eigenschaften** angezeigt, wenn eine Instanz der Komponente ausgewählt wird. Sie können Eingabe Eigenschaften mit Ausdrücken oder Formeln konfigurieren, so wie Sie Standardeigenschaften in anderen Steuerelementen konfigurieren. Andere Steuerelemente verfügen über Eingabe Eigenschaften, z. b. die **default** -Eigenschaft eines **Text Eingabe** -Steuer Elements.

Ausgabe Eigenschaften können den Daten-oder Komponenten Status ausgeben. Beispielsweise ist die **ausgewählte** Eigenschaft in einem Katalog **-Steuerelement eine Ausgabe** Eigenschaft. Wenn Sie eine Output-Eigenschaft erstellen, können Sie bestimmen, welche anderen Steuerelemente auf den Komponenten Zustand verweisen können.

In dieser exemplarischen Vorgehensweise werden diese Konzepte ausführlicher erläutert.

## <a name="create-an-example-component"></a>Erstellen einer Beispiel Komponente

In diesem Beispiel erstellen Sie eine Menü Komponente, die dieser Grafik ähnelt und in der Sie den Text ändern und in mehreren Bildschirmen, Apps oder beidem verwenden können:

![Endgültiger Katalog](./media/create-component/menu-instance.png)

1. Erstellen Sie in powerapps Studio eine leere app.

1. Öffnen Sie in der linken Navigationsleiste die Liste der Komponenten, und klicken Sie dann auf **neue Komponente**.

    ![Liste der Komponenten](./media/create-component/component-list.png)

1. Wenn Sie auf die neue Komponente zeigen, wählen Sie die Auslassungs Punkte (...) aus, wählen Sie **Umbenennen**aus, und geben oder fügen Sie **MenuComponent**ein.

1. Legen Sie im rechten Bereich die Breite der Komponente auf **150** und die Höhe auf **250**fest, und wählen Sie dann **neue benutzerdefinierte Eigenschaft**aus.

    ![Neue Eigenschaft](./media/create-component/new-property.png)

1. Geben oder fügen Sie in den Feldern **Anzeige Name**, **Eigenschaftsname**und **Beschreibung** **Elemente**ein, oder fügen Sie Sie ein.

    ![Anzeige Name, Eigenschaftsname, Beschreibungs Felder](./media/create-component/property-names.png)

    Wenn Sie einen Eigenschaftsnamen angeben, dürfen Sie keine Leerzeichen einschließen, da Sie mit diesem Namen auf die Komponente verweisen, wenn Sie eine Formel schreiben (z **. b. "componentname. PropertyName**").

    Der Anzeige Name wird im rechten Bereich auf der Registerkarte **Eigenschaften** angezeigt, wenn Sie die Komponente auswählen. Ein beschreibender Anzeige Name hilft Ihnen und anderen Herstellern dabei, den Zweck dieser Eigenschaft nachzuvollziehen. Die **Beschreibung** wird in einer QuickInfo angezeigt, wenn Sie auf der Registerkarte **Eigenschaften** mit dem Mauszeiger auf den anzeigen Amen dieser Eigenschaft zeigen.

1. Wählen Sie in der Liste **Datentyp** die Option **Tabelle**aus, und wählen Sie dann **Erstellen**aus.

    ![Datentyp der Eigenschaft](./media/create-component/property-data-type.png)

    Die **Items** -Eigenschaft wird auf einen Standardwert festgelegt, der auf dem angegebenen Datentyp basiert, aber Sie können Sie auf einen Wert festlegen, der Ihren Anforderungen entspricht. Wenn Sie den Datentyp **Tabelle** oder **Datensatz**angegeben haben, können Sie den Wert der **Items** -Eigenschaft so ändern, dass er mit dem Datenschema identisch ist, das Sie in die Komponente eingeben möchten. In diesem Fall ändern Sie den Wert in eine Liste von Zeichen folgen.

    Sie können den Wert der Eigenschaft in der Bearbeitungs Leiste festlegen, wenn Sie den Namen der Eigenschaft auf der Registerkarte **Eigenschaften** des rechten Bereichs auswählen.

    ![Benutzerdefinierte Eingabe Eigenschaft auf der Registerkarte "Eigenschaften"](./media/create-component/properties-tab.png)

    Wie die nächste Abbildung zeigt, können Sie auch den Wert der Eigenschaft auf der Registerkarte **erweitert** im rechten Bereich bearbeiten.

1. Legen Sie die **Items** -Eigenschaft der Komponente auf diese Formel fest:

    ```powerapps-comma
    Table({Item:"SampleText"})
    ```

    ![Formel](./media/create-component/set-component-items.png)

1. Fügen Sie in der-Komponente ein leeres **vertikales** Katalog Steuerelement ein.

1. Stellen Sie sicher, dass in der Eigenschaften Liste die **Items** -Eigenschaft (wie standardmäßig) angezeigt wird, und legen Sie dann den Wert dieser Eigenschaft auf diesen Ausdruck fest:

    ```powerapps-comma
    MenuComponent.Items
    ```

    Auf diese Weise liest die **Items** -Eigenschaft **des Katalog-Steuer Elements** und hängt von der **Eigenschaft Input-** Eigenschaft der Komponente ab.

1. Legen Sie die **borderdicke** -Eigenschaft des Katalog **-Steuer Elements** auf **1** und die **templatesize** -Eigenschaft auf **50**fest.

1. Fügen Sie in der Vorlage des **Katalog** -Steuer Elements ein Label **-Steuerelement** hinzu.

    ![Bezeichnung hinzufügen und Rahmen des Katalogs festlegen](./media/create-component/add-label.png)

Als Nächstes fügen Sie die Komponente einem Bildschirm hinzu und geben eine Tabelle mit Zeichen folgen an, die von der Komponente angezeigt werden soll.

1. Wählen Sie in der linken Navigationsleiste die Liste der Bildschirme aus, und wählen Sie dann den Standard Bildschirm aus.

    ![Standard Bildschirm](./media/create-component/default-screen.png)

1. Öffnen Sie auf der Registerkarte **Einfügen** das Menü **Komponenten** , und wählen Sie dann **MenuComponent**aus.

    ![Setze](./media/create-component/insert.png)

    Die neue Komponente hat standardmäßig den Namen **MenuComponent_1** .

1. Legen Sie die **Items** -Eigenschaft **MenuComponent_1** auf diese Formel fest:

    ```powerapps-comma
    Table({Item:"Home"}; {Item:"Admin"}; {Item:"About"}; {Item:"Help"})
    ```

    Diese Instanz ähnelt dieser Grafik, aber Sie können den Text und andere Eigenschaften jeder Instanz anpassen.

    ![Endgültiger Katalog](./media/create-component/menu-instance.png)

Bisher haben Sie eine Komponente erstellt und einer app hinzugefügt. Als Nächstes erstellen Sie eine Ausgabe Eigenschaft, die das Element widerspiegelt, das der Benutzer im Menü auswählt.

1. Öffnen Sie die Liste der Komponenten, und wählen Sie dann **MenuComponent**aus.

1. Wählen Sie im rechten Bereich die Registerkarte **Eigenschaften** aus, und wählen Sie dann **neue benutzerdefinierte Eigenschaft**aus.

1. Geben oder fügen Sie in den Feldern **Anzeige Name**, **Eigenschaftsname**und **Beschreibung** den Text **Selected**ein.

1. Wählen Sie unter **Eigenschaftentyp**die Option **Ausgabe**, und wählen Sie dann **Erstellen**aus.

1. Legen Sie auf der Registerkarte **erweitert** den Wert der **ausgewählten** Eigenschaft auf diesen Ausdruck fest, und passen Sie ggf. die Zahl im Katalognamen an:

    ```powerapps-comma
    Gallery1.Selected.Item
    ```

    ![Erweiterter Bereich](./media/create-component/advance.png)

1. Fügen Sie auf dem Standard Bildschirm der App eine Bezeichnung hinzu, und legen Sie deren **Text** -Eigenschaft auf diesen Ausdruck fest. passen Sie ggf. die Zahl im Komponentennamen an:

    ```powerapps-comma
    MenuComponent_1.Selected
    ```

    Beachten Sie, dass **MenuComponent_1** der Standardname einer-Instanz und nicht der Name der Komponenten Definition ist. Sie können eine beliebige Instanz umbenennen.

1. Wenn Sie die Alt-Taste gedrückt halten, wählen Sie jedes Element im Menü aus.

    Das **Label** -Steuerelement spiegelt das Menü Element wider, das Sie zuletzt ausgewählt haben.

## <a name="known-limitations"></a>Bekannte Einschränkungen

- Zum Zeitpunkt der Erstellung dieses Artikels werden Datenquellen nicht mit Komponenten gespeichert, sodass Formulare und Datentabellen deaktiviert werden.
- Power Apps unterstützt keine Sammlungen in-Komponenten.
- Eine Komponente kann nicht in einen Katalog, ein Formular oder eine Datenkarte eingefügt werden.
- Eine Master Instanz einer Komponente ist ein lokaler Master, der der APP zugeordnet ist. Wenn Sie eine Master Instanz ändern, spiegeln nur Kopien der Komponente innerhalb der APP die Änderung wider. Kopien in anderen apps bleiben unverändert, es sei denn, Sie importieren die Komponentenbibliothek erneut. Alle Master Instanzen in diesen apps werden automatisch erkannt und aktualisiert.
- Beim Importieren einer Komponente können keine Mediendateien paketieren.
