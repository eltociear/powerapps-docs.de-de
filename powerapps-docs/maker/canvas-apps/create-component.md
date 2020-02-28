---
title: Erstellen einer Komponente für Canvas-apps | Microsoft-Dokumentation
description: Einführung in wiederverwendbare Komponenten für Canvas-apps
author: yifwang
ms.service: powerapps
ms.topic: article
ms.date: 02/20/2020
ms.author: yifwang
ms.reviewer: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 3c2864a7953e115c650ff5cee879d2a1227acdb4
ms.sourcegitcommit: 59f0b3adc56279b5673cbf04b4a55bd7678e1ea7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/28/2020
ms.locfileid: "77911199"
---
# <a name="create-a-component-for-canvas-apps"></a>Erstellen einer Komponente für Canvas-apps

> [!IMPORTANT]
> Dieses Feature befindet sich noch in der öffentlichen Vorschau Phase. Weitere Informationen finden Sie unter [Experimentelle Features und Previewfunktionen](working-with-experimental.md).

Komponenten sind wiederverwendbare Bausteine für Canvas-apps, damit App-Ersteller benutzerdefinierte Steuerelemente erstellen können, die in einer APP oder über eine App mithilfe der [Komponentenbibliothek](component-library.md)verwendet werden. Komponenten können erweiterte Funktionen verwenden, wie z. b. benutzerdefinierte Eigenschaften, und komplexe Funktionen ermöglichen. In diesem Artikel werden die Komponenten Konzepte und einige Beispiele vorgestellt.

Komponenten sind nützlich, um größere apps mit ähnlichen Steuerelement Mustern zu entwickeln. Wenn Sie eine Komponenten Definition innerhalb der APP aktualisieren, spiegeln alle Instanzen in der APP Ihre Änderungen wider. Komponenten reduzieren auch die Duplizierung von Aktivitäten, indem Sie das Kopieren/Einfügen von Steuerelementen und das Verbessern der Leistung vermeiden. Komponenten helfen außerdem beim Erstellen von kollaborativer Entwicklung und Standardisieren von Aussehen und fühlen in einer Organisation, wenn Sie eine [Komponentenbibliothek](component-library.md)verwenden.

## <a name="components-in-canvas-app"></a>Komponenten in der Canvas-App

Sie können eine Komponente innerhalb einer APP erstellen, wie in diesem Artikel erläutert, oder indem Sie eine neue Komponente in einer [Komponentenbibliothek](component-library.md)erstellen. Eine Komponentenbibliothek sollte für Anforderungen verwendet werden, um Komponenten über mehrere App-Bildschirme zu verwenden. Sie können die vorhandenen Komponenten auch in eine vorhandene oder eine neue Komponentenbibliothek kopieren.

Wechseln Sie zur Struktur **Ansicht**, wählen Sie die Registerkarte **Komponenten** aus, und wählen Sie dann **neue Komponente**aus, um eine Komponente innerhalb einer APP zu erstellen:

![Erstellen einer neuen benutzerdefinierten Komponente mithilfe der Strukturansicht](./media/create-component/insert-new-component-treeview.png)

Wenn Sie **neue Komponente** auswählen, wird eine leere Canvas geöffnet. Sie können Steuerelemente als Teil der Komponenten Definition auf der Canvas hinzufügen. Wenn Sie eine Komponente im Zeichenbereich bearbeiten, aktualisieren Sie Instanzen derselben Komponente in anderen APP-Bildschirmen. Apps, die eine bereits erstellte Komponente wieder verwenden, können auch Komponenten Updates empfangen, nachdem Sie Komponenten Änderungen veröffentlicht haben.

Sie können eine Komponente aus der Liste der vorhandenen Komponenten im linken Navigationsbereich auswählen, nachdem Sie einen Bildschirm ausgewählt haben. Wenn Sie eine Komponente auswählen, legen Sie eine Instanz dieser Komponente auf dem Bildschirm ab. genau so, wie Sie ein-Steuerelement einfügen.

In der APP verfügbare Komponenten werden unter **benutzerdefinierte** Kategorie in der Liste der Komponenten in der Strukturansicht aufgeführt. Importierte Komponenten Bibliotheken sind unter **Bibliotheks Komponenten** Kategorie aufgeführt:

![Komponenten in die APP einfügen](./media/create-component/insert-components.png)

> [!NOTE]
> Die in diesem Artikel erläuterten Komponenten unterscheiden sich vom Komponenten Framework von powerapps, das Entwicklern und Entwicklern das Erstellen von Code Komponenten für Modell gesteuerte und Canvas-Apps ermöglicht. Weitere Informationen finden Sie unter [Übersicht über das Komponenten Framework von powerapps](https://docs.microsoft.com/powerapps/developer/component-framework/overview).

## <a name="scope"></a>Gültigkeitsbereich

Betrachten Sie eine Komponente als gekapseltes schwarzes Feld mit Eigenschaften als Schnittstelle. Sie können nicht von außerhalb der Komponente auf Steuerelemente in der Komponente zugreifen. Und Sie können nicht innerhalb der Komponente auf etwas außerhalb der Komponente verweisen. Ausnahme sind Datenquellen, die von der APP und ihren Komponenten gemeinsam genutzt werden. Durch Bereichs Einschränkungen bleibt der Datenvertrag einer Komponente einfach und zusammenhängend, und Sie trägt zum Aktivieren von Komponenten Definitions Updates bei, insbesondere für apps mit Komponenten Bibliotheken. Sie können den Datenvertrag der Komponente aktualisieren, indem Sie eine oder mehrere benutzerdefinierte Eigenschaften erstellen.

> [!NOTE]
> Sie können Instanzen von Komponenten in einen Bildschirm innerhalb einer Komponentenbibliothek einfügen und den Bildschirm zu Testzwecken in der Vorschau anzeigen. Beachten Sie außerdem, dass die Komponentenbibliothek bei der Verwendung von [powerapps Mobile](https://powerapps.microsoft.com/downloads/)nicht angezeigt wird.

## <a name="custom-properties"></a>Benutzerdefinierte Eigenschaften

Eine Komponente kann Eingabewerte empfangen und Daten ausgeben, wenn Sie eine oder mehrere benutzerdefinierte Eigenschaften erstellen. Diese Szenarien sind erweitert und erfordern das Verständnis von [Formeln](formula-reference.md) und Bindungs Verträgen.

Die **Eingabe Eigenschaft** gibt an, wie eine Komponente Daten empfängt, die in der Komponente verwendet werden sollen. Eingabe Eigenschaften werden im rechten Bereich auf der Registerkarte **Eigenschaften** angezeigt, wenn eine Instanz der Komponente ausgewählt wird. Sie können Eingabe Eigenschaften mit Ausdrücken oder Formeln konfigurieren, so wie Sie Standardeigenschaften in anderen Steuerelementen konfigurieren. Andere Steuerelemente verfügen über Eingabe Eigenschaften, z. b. die **default** -Eigenschaft eines **Text Eingabe** -Steuer Elements.

Die **Output-Eigenschaft** wird zum Ausgeben des Daten-oder Komponenten Zustands verwendet. Beispielsweise ist die **ausgewählte** Eigenschaft in einem Katalog **-Steuerelement eine Ausgabe** Eigenschaft. Wenn Sie eine Output-Eigenschaft erstellen, können Sie bestimmen, welche anderen Steuerelemente auf den Komponenten Zustand verweisen können.

In der folgenden exemplarischen Vorgehensweise werden diese Konzepte ausführlicher erläutert.

## <a name="create-an-example-component"></a>Erstellen einer Beispiel Komponente

In diesem Beispiel erstellen Sie eine Menü Komponente, die der folgenden Grafik ähnelt. Und Sie können den Text später ändern, um ihn in mehreren Bildschirmen, Apps oder beidem zu verwenden:

![Endgültiger Katalog](./media/create-component/menu-instance-new.png)

> [!NOTE]
> Beim Erstellen von Komponenten für die Wiederverwendung empfiehlt sich die Verwendung der [Komponentenbibliothek](component-library.md) . Durch das Aktualisieren von Komponenten innerhalb einer App werden die Komponenten Updates nur innerhalb der app verfügbar. Wenn Sie Komponenten aus einer APP in eine andere importieren, werden neue Updates für Komponenten in der ursprünglichen APP nicht an die APP weitergegeben, die diese Komponenten zuvor importiert hat. Wenn Sie die Komponentenbibliothek verwenden, werden Sie aufgefordert, Komponenten zu aktualisieren, wenn die Komponenten in einer Bibliothek aktualisiert und veröffentlicht werden.

### <a name="create-a-new-component"></a>Neue Komponente erstellen

1. Melden Sie sich bei [make.powerapps.com](https://make.powerapps.com)an.

1. Wählen Sie **apps** aus, und wählen Sie **Canvas app from Blank aus**. 

1. Geben Sie einen APP-Namen an, wählen Sie ein beliebiges Layout und dann **Erstellen**aus.

1. Wählen Siein der Strukturansicht **Komponenten** aus, und wählen Sie dann **neue Komponente** aus, um eine neue Komponente zu erstellen.

    ![Erstellen einer neuen benutzerdefinierten Komponente mithilfe der Strukturansicht](./media/create-component/insert-new-component-treeview.png)

1. Wählen Sie die neue Komponente im linken Navigationsbereich aus, und wählen Sie dann die Auslassungs Punkte (...) und dann **Umbenennen**. Geben oder fügen Sie den Namen in **MenuComponent**ein.

1. Legen Sie im rechten Bereich die Breite der Komponente auf **150** und die Höhe auf **250**fest, und wählen Sie dann **neue benutzerdefinierte Eigenschaft**aus. Sie können auch die Höhe & Breite auf einen beliebigen anderen Wert festlegen.

    ![Neue Eigenschaft](./media/create-component/new-property.png)

1. Geben oder fügen Sie in den Feldern **Anzeige Name**, **Eigenschaftsname**und **Beschreibung** Text als *Elemente*ein.

    ![Anzeige Name, Eigenschaftsname, Beschreibungs Felder](./media/create-component/property-names.png)

    Fügen Sie Leerzeichen nicht in den Eigenschaftsnamen ein, da Sie mit diesem Namen auf die Komponente verweisen, wenn Sie eine Formel schreiben. Beispielsweise **componentname. PropertyName**.

    Der Anzeige Name wird im rechten Bereich auf der Registerkarte **Eigenschaften** angezeigt, wenn Sie die Komponente auswählen. Ein beschreibender Anzeige Name hilft Ihnen und anderen Herstellern dabei, den Zweck dieser Eigenschaft nachzuvollziehen. Die **Beschreibung** wird in einer QuickInfo angezeigt, wenn Sie auf der Registerkarte **Eigenschaften** mit dem Mauszeiger auf den anzeigen Amen dieser Eigenschaft zeigen.

1. Wählen Sie in der Liste **Datentyp** die Option **Tabelle**aus, und wählen Sie dann **Erstellen**aus.

    ![Datentyp der Eigenschaft](./media/create-component/property-data-type.png)

    Die **Items** -Eigenschaft wird auf Grundlage des angegebenen Datentyps auf einen Standardwert festgelegt. Sie können den Wert auf einen Wert festlegen, der Ihren Anforderungen entspricht. Wenn Sie den Datentyp **Tabelle** oder **Datensatz**angegeben haben, können Sie den Wert der **Items** -Eigenschaft so ändern, dass er mit dem Datenschema identisch ist, das Sie in die Komponente eingeben möchten. In diesem Fall ändern Sie den Wert in eine Liste von Zeichen folgen.

    Sie können den Wert der Eigenschaft in der Bearbeitungs Leiste festlegen, wenn Sie den Namen der Eigenschaft auf der Registerkarte **Eigenschaften** des rechten Bereichs auswählen.

    ![Benutzerdefinierte Eingabe Eigenschaft auf der Registerkarte "Eigenschaften"](./media/create-component/properties-tab.png)

    Wie die nächste Abbildung zeigt, können Sie auch den Wert der Eigenschaft auf der Registerkarte **erweitert** im rechten Bereich bearbeiten.

1. Legen Sie die **Items** -Eigenschaft der Komponente auf diese Formel fest:

    ```powerapps-dot
    Table({Item:"SampleText"})
    ```

    ![Formel](./media/create-component/set-component-items.png)

1. Fügen Sie in der Komponente ein **leeres vertikales** Katalog-Steuerelement ein, und wählen Sie im Eigenschaften Bereich **Layout** als **Titel**aus.

1. Stellen Sie sicher, dass in der Eigenschaften Liste die **Items** -Eigenschaft angezeigt wird (wie in der Standardeinstellung). Legen Sie dann den Wert dieser Eigenschaft auf diesen Ausdruck fest:

    ```powerapps-dot
    MenuComponent.Items
    ```

    Auf diese Weise liest die **Items** -Eigenschaft **des Katalog-Steuer Elements** und hängt von der **Eigenschaft Input-** Eigenschaft der Komponente ab.

1. Optional: Legen Sie die **borderdicke** -Eigenschaft des Katalog **-Steuer Elements** auf **1** und die **templatesize** -Eigenschaft auf **50**fest. Sie können auch Werte für die Rahmen Stärke und die Vorlagen Größe entsprechend einem beliebigen anderen Wert aktualisieren.

### <a name="add-component-to-a-screen"></a>Hinzufügen einer Komponente zu einem Bildschirm

Als Nächstes fügen Sie die Komponente einem Bildschirm hinzu und geben eine Tabelle mit Zeichen folgen an, die von der Komponente angezeigt werden soll.

1. Wählen Sie in der linken Navigationsleiste die Liste der Bildschirme aus, und wählen Sie dann den Standard Bildschirm aus.

    ![Standard Bildschirm](./media/create-component/default-screen.png)

1. Öffnen Sie auf der Registerkarte **Einfügen** das Menü **Komponenten** , und wählen Sie dann **MenuComponent**aus.

    ![Einfügen](./media/create-component/insert.png)

    Die neue Komponente hat standardmäßig den Namen **MenuComponent_1** .

1. Legen Sie die **Items** -Eigenschaft **MenuComponent_1** auf diese Formel fest:

    ```powerapps-dot
    Table({Item:"Home"}, {Item:"Admin"}, {Item:"About"}, {Item:"Help"})
    ```

    Diese Instanz ähnelt dieser Grafik, aber Sie können den Text und andere Eigenschaften jeder Instanz anpassen.

    ![Endgültiger Katalog](./media/create-component/menu-instance-new.png)

### <a name="create-and-use-output-property"></a>Ausgabe Eigenschaft erstellen und verwenden

Bisher haben Sie eine Komponente erstellt und einer app hinzugefügt. Als Nächstes erstellen Sie eine Ausgabe Eigenschaft, die das Element widerspiegelt, das der Benutzer im Menü auswählt.

1. Öffnen Sie die Liste der Komponenten, und wählen Sie dann **MenuComponent**aus.

1. Wählen Sie im rechten Bereich die Registerkarte **Eigenschaften** aus, und wählen Sie dann **neue benutzerdefinierte Eigenschaft**aus.

1. Geben oder fügen Sie in den Feldern **Anzeige Name**, **Eigenschaftsname**und **Beschreibung** den Text **Selected**ein.

1. Wählen Sie unter **Eigenschaftentyp**die Option **Ausgabe**, und wählen Sie dann **Erstellen**aus.

    ![Eigenschaftentyp als Ausgabe](./media/create-component/output-property-type.png)

1. Legen Sie auf der Registerkarte **erweitert** den Wert der **ausgewählten** Eigenschaft auf diesen Ausdruck fest, und passen Sie ggf. die Zahl im Katalognamen an:

    ```powerapps-dot
    Gallery1.Selected.Item
    ```

    ![Erweiterter Bereich](./media/create-component/advance.png)

1. Fügen Sie auf dem Standard Bildschirm der App eine Bezeichnung hinzu, und legen Sie deren **Text** -Eigenschaft auf diesen Ausdruck fest. passen Sie ggf. die Zahl im Komponentennamen an:

    ```powerapps-dot
    MenuComponent_1.Selected
    ```

    **MenuComponent_1** ist der Standardname einer Instanz, nicht der Name der Komponenten Definition. Sie können eine beliebige Instanz umbenennen.

1. Wenn Sie die Alt-Taste gedrückt halten, wählen Sie jedes Element im Menü aus.

    Das **Label** -Steuerelement spiegelt das Menü Element wider, das Sie zuletzt ausgewählt haben.

## <a name="import-and-export-components"></a>Importieren und Exportieren von Komponenten

> [!NOTE]
> Diese Funktion wird als veraltet markiert. [Komponenten Bibliotheken](component-library.md) sind die empfohlene Methode, um die Komponenten in den apps wiederzuverwenden. Wenn Sie die Komponentenbibliothek verwenden, verwaltet eine APP Abhängigkeiten von den verwendeten Komponenten. Der APP-Ersteller wird benachrichtigt, wenn die Updates für abhängige Komponenten verfügbar werden. Daher sollten stattdessen alle neuen wiederverwendbaren Komponenten in den Komponenten Bibliotheken erstellt werden.

### <a name="import-components-from-another-app"></a>Importieren von Komponenten aus einer anderen APP

Wenn Sie mindestens eine Komponente aus einer APP in eine andere importieren möchten, wählen Sie im Menü **Einfügen** die Option **Komponenten Importieren** aus, und verwenden Sie dann die Dropdown Liste **Benutzer** definiert Oder mithilfe von **Komponenten** in der Strukturansicht im linken Navigationsbereich.

In einem Dialogfeld werden alle apps aufgelistet, die Komponenten enthalten, für die Sie über die Berechtigung zum Bearbeiten verfügen. Wählen Sie eine APP aus, und wählen Sie dann **importieren** aus, um die neueste veröffentlichte Version aller Komponenten in der APP zu importieren. Nachdem Sie mindestens eine Komponente importiert haben, können Sie Ihre Kopie bearbeiten und beliebig löschen.

![Dialogfeld "Komponenten Importieren"](./media/create-component/import-component-screen.png)

Sie können eine APP mit vorhandenen Komponenten lokal in einer Datei speichern und die Datei dann wieder verwenden, indem Sie Sie importieren. Sie können die-Datei verwenden, um Komponenten in eine andere APP zu importieren.

Wenn die APP eine geänderte Version derselben Komponente enthält, werden Sie aufgefordert, zu entscheiden, ob die geänderte Version ersetzt oder der Import abgebrochen werden soll. 

Nachdem Sie Komponenten in einer App erstellt haben, können andere apps die Komponenten aus dieser app nutzen, indem Sie Sie importieren.

### <a name="export-components-from-your-app"></a>Exportieren von Komponenten aus Ihrer APP

Sie können Komponenten in eine Datei exportieren und zum Importieren in eine andere app herunterladen.

Wählen Sie im Abschnitt " **Komponenten** " in der linken Navigationsstruktur Ansicht die Option zum **Exportieren von Komponenten**

![Exportieren von Komponenten (TreeView)](./media/create-component/export-components-treeview.png)

Sie können auch das Menü **Einfügen** verwenden und dann stattdessen **benutzerdefiniertes** Dropdown Menü auswählen.

![Menü zum Einfügen von Komponenten exportieren](./media/create-component/export-components-insert-menu.png)

Wenn Sie **Komponenten exportieren** auswählen, werden die Komponenten in eine Datei heruntergeladen:

![Komponente herunterladen](./media/create-component/download-component.png)

Die heruntergeladene Komponenten Datei verwendet die Dateinamenerweiterung " *. msapp* ". 

### <a name="import-components-from-exported-components-file"></a>Importieren von Komponenten aus der exportierten Komponenten Datei

Wenn Sie Komponenten aus einer exportierten Komponenten Datei importieren möchten, wählen Sie im Menü **Einfügen** die Option **Komponenten Importieren** aus. Verwenden Sie anschließend die **benutzerdefinierte** Dropdown Liste, oder verwenden Sie die **Komponenten** in der Strukturansicht im linken Navigationsbereich. Wählen Sie im Dialogfeld Komponenten die Option **Datei importieren** , anstatt andere Komponenten oder apps auszuwählen:

![Komponenten Datei importieren](./media/create-component/import-component-file.png)

Navigieren Sie im Dialogfeld **Öffnen** zum Speicherort der Komponenten Datei, und wählen Sie **Öffnen** aus, um die Komponenten in der APP zu importieren.

### <a name="import-components-from-exported-app"></a>Importieren von Komponenten aus der exportierten App

Sie können eine APP lokal mithilfe der **Datei** -> Option " **Speichern** unter" speichern:

![APP speichern](./media/create-component/save-app-locally.png)

Nachdem Sie die APP gespeichert haben, können Sie die Komponenten dieser App mithilfe derselben Methode zum Importieren von Komponenten aus einer Datei wieder verwenden. Befolgen Sie die Schritte im Abschnitt Importieren von Komponenten aus der exportierten Komponenten Datei weiter oben.

## <a name="known-limitations"></a>Bekannte Einschränkungen

- Datenquellen, Formulare und Datentabellen können nicht mit-Komponenten gespeichert werden.
- Sammlungen in-Komponenten werden nicht unterstützt.
- Sie können eine Komponente nicht in einen Katalog oder ein Formular einfügen.
- Eine Master Instanz einer Komponente ist ein lokaler Master, der der APP zugeordnet ist. Wenn Sie eine Master Instanz ändern, spiegeln nur Kopien der Komponente innerhalb der APP die Änderung wider. Kopien in anderen apps bleiben unverändert, es sei denn, Sie importieren die Komponentenbibliothek erneut. Alle Master Instanzen in diesen apps werden automatisch erkannt und aktualisiert.
- Beim Importieren einer Komponente können keine Mediendateien paketieren.
- Komponenten unterstützen die [**updatecontext**](./functions/function-updatecontext.md) -Funktion nicht, Sie können jedoch Variablen in einer Komponente erstellen und aktualisieren, indem Sie die [**set**](functions/function-set.md) -Funktion verwenden. Der Gültigkeitsbereich dieser Variablen ist auf die Komponente beschränkt, aber Sie können über benutzerdefinierte Ausgabe Eigenschaften von außerhalb der Komponente darauf zugreifen.

## <a name="next-steps"></a>Nächste Schritte

Erlernen Sie die [Komponentenbibliothek](component-library.md) , um ein Repository wiederverwendbarer Komponenten zu erstellen.