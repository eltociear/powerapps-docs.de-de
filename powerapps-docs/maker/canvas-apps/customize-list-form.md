---
title: Anpassen eines SharePoint-Listenformulars | Microsoft-Dokumentation
description: Verwenden Sie powerapps, um das Formular anzupassen, mit dem Benutzereinträge in einer SharePoint-Liste erstellen und aktualisieren.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 10/24/2019
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 61cf2ad5926daf8b1b5bea6310b9fb29563208e2
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2019
ms.locfileid: "74731692"
---
# <a name="customize-a-sharepoint-list-form-by-using-power-apps"></a>Anpassen eines SharePoint-Listen Formulars mithilfe von powerapps

Sie können das Formular für eine SharePoint-Liste problemlos anpassen, indem Sie Power apps in einem Browser öffnen. Sie müssen keinen herkömmlichen Code (wie C#) schreiben oder eine weitere App (wie InfoPath) herunterladen. Wenn Sie Ihre Änderungen veröffentlichen, wird das Formular in die SharePoint-Liste eingebettet, sodass es von allen Benutzern verwendet werden kann. In powerapps können Sie auch Analyseberichte überprüfen, auf einfache Weise bedingte Formatierungen erstellen und eine Verbindung mit anderen Datenquellen herstellen.

Für die in diesem Artikel beschriebenen Schritte benötigen Sie eine einfache Liste, um nachvollziehen zu können, wie die Anpassung funktioniert. Anschließend können Sie diese Konzepte auf Ihre eigene Liste anwenden.

> [!NOTE]
> - Wenn die Option **Formulare anpassen** nicht verfügbar ist oder für Ihre Liste nicht ordnungsgemäß funktioniert, kann Sie Datentypen enthalten, die von [powerapps nicht unterstützt](connections/connection-sharepoint-online.md#known-issues)werden. Sie können Ihr Formular nicht in eine andere Liste oder [Umgebung](working-with-environments.md) verschieben. 
> - Benutzerdefinierte Formulare für Listen werden nur in generischen Listen unterstützt. Unterstützung für generische Dokument Bibliotheken wird in Kürze verfügbar sein. Benutzerdefinierte Listen-und Bibliotheks Vorlagen werden zurzeit nicht unterstützt. einschließlich, aber nicht beschränkt auf Listen wie Ankündigungen, Kontakte und Aufgaben.

## <a name="create-a-list"></a>Liste erstellen

Erstellen Sie auf einer SharePoint-Website eine Liste, und fügen Sie diese Spalten dann der Liste hinzu:

- **Details** (ja/nein)
- **Price** (Währung)
- **Availability** (Datum ohne Uhrzeit)
- **Color** (Auswahl)

> [!div class="mx-imgBorder"]
> ![wählen Sie Website Inhalte > neue > Liste aus, geben Sie den Namen der Liste ein, und klicken Sie auf erstellen. Wählen Sie für jede Spalte Spalte hinzufügen aus, geben Sie den Auflistungstyp an (Ja/Nein, Währung, Datum, Auswahl), geben Sie den Listennamen an (Details, Preis, Verfügbarkeit, Farbe), und wählen Sie speichern aus.](./media/customize-list-form/create-list.gif)

## <a name="open-the-form"></a>Formular öffnen

1. Wählen Sie in der Befehlsleiste **powerapps**aus, und wählen Sie dann **Formular anpassen aus**.

    Powerapps Studio wird auf der gleichen Browser Registerkarte geöffnet.

1. Wenn das Dialogfeld **Willkommen bei Power apps Studio** geöffnet wird, wählen Sie über **springen**aus.

> [!div class="mx-imgBorder"]
> Wählen Sie in der Befehlsleiste die Option powerapps aus, und wählen Sie dann Formular anpassen aus. ![ Powerapps Studio wird auf der gleichen Browser Registerkarte geöffnet. Wenn das Dialogfeld Willkommen bei Power apps Studio geöffnet wird, wählen Sie überspringen aus.](./media/customize-list-form/create-form.gif)

## <a name="move-and-remove-a-field"></a>Verschieben und Entfernen eines Felds

1. Ziehen Sie das Feld **Availability** an den unteren Rand der Liste der Felder.

    Die Felder werden in der von Ihnen angegebenen Reihenfolge angezeigt.

1. Zeigen Sie auf das Feld **Anlagen** , wählen Sie die Auslassungs Punkte (...) aus, die angezeigt werden, und wählen Sie dann **Entfernen**aus.

    Das angegebene Feld verschwindet im Formular.

> [!div class="mx-imgBorder"]
> ![ziehen Sie das Feld "Availability" an den unteren Rand der Liste der Felder. Zeigen Sie auf das Feld Anlagen, wählen Sie die Auslassungs Punkte (...) aus, die angezeigt werden, und wählen Sie dann entfernen aus.](./media/customize-list-form/move-remove-fields.gif)

## <a name="set-conditional-formatting"></a>Festlegen bedingter Formatierung

Sie können die Felder **Price**, **Availability** und **Colors** so konfigurieren, dass sie nur angezeigt werden, wenn **Details** auf „Yes“ (Ja) festgelegt ist.

1. Erweitern Sie in der linken Navigationsleiste **Details_DataCard1**, und notieren Sie sich die Zahl, die am Ende von **datacardvalue**angezeigt wird.

1. Legen Sie die **Visible** -Eigenschaft der **Farben**, der **Verfügbarkeit**und der **Preis** Karten auf diese Formel fest (ersetzen Sie ggf. die Zahl durch die Zahl, die Sie im vorherigen Schritt notiert haben):

    **If (DataCardValue2. Value = True, true)**

1. Halten Sie die ALT-TASTE gedrückt, und tippen oder klicken Sie mehrmals auf den Schalter **Details**.

    Die drei von Ihnen konfigurierten Felder werden angezeigt und wieder ausgeblendet.

> [!div class="mx-imgBorder"]
> Beachten Sie ![in der linken Navigationsleiste die Zahl, die am Ende von datacardvalue angezeigt wird. Legen Sie die Eigenschaft Sichtbarkeit der Farben, der Verfügbarkeit und der Preiskarten auf diese Formel fest. Halten Sie die Alt-Taste gedrückt, und wählen Sie das Detail Steuerelement mehrmals aus.](./media/customize-list-form/conditional-format.gif)

## <a name="save-and-publish-the-form"></a>Speichern und Veröffentlichen des Formulars

1. Öffnen Sie das Menü **Datei**, klicken Sie auf **Speichern**, und wählen Sie dann zweimal **In SharePoint veröffentlichen**.

1. Klicken Sie in der oberen linken Ecke auf den Zurück-Pfeil, und klicken Sie dann auf **Zurück zu SharePoint**.

> [!div class="mx-imgBorder"]
> ![öffnen Sie das Menü Datei, wählen Sie speichern aus, und wählen Sie dann zweimal in SharePoint veröffentlichen aus. Wählen Sie in der oberen linken Ecke den rückwärts Pfeil aus, und wählen Sie dann zurück zu SharePoint aus.](./media/customize-list-form/save-form.gif)

## <a name="further-customize-your-form"></a>Weiteres Anpassen des Formulars

1. Öffnen Sie die Liste, wählen Sie in der Befehlsleiste **neu** aus, und wählen Sie dann am oberen Rand des Formulars die Option **Anpassen** aus.

1. Passen Sie Ihr Formular auf verschiedene Weise an, z. b. in den folgenden Themen:

    - Ändern Sie die Größe, Ausrichtung oder beides (Sie können das Formular z.B. [breiter machen](set-aspect-ratio-portrait-landscape.md))
    - [Passen](working-with-cards.md) Sie mindestens eine Karte an (ändern Sie z. b. den Anzeige Text oder das Eingabe Steuerelement einer Karte).
    - Erstellen Sie ein [Nachschlagefeld](sharepoint-lookup-fields.md).

    Weitere Informationen finden Sie unter [verstehen der Integration von SharePoint-Formularen](sharepoint-form-integration.md).

## <a name="use-the-default-form"></a>Verwenden des Standardformulars

1. Öffnen Sie über Ihre Liste in SharePoint die Einstellungen (über das Zahnradsymbol in der oberen rechten Ecke), und klicken Sie dann auf **Listeneinstellungen**.

2. Wählen Sie unter **Allgemeine Einstellungen** **Formulareinstellungen** aus.

3. Wählen Sie eine der folgenden Optionen in den **Formulareinstellungen**, und klicken Sie dann auf **OK**.

    - **Das SharePoint-Standardformular verwenden**: Wenn ein Benutzer Ihre Liste öffnet und auf der Befehlsleiste auf **Neu** klickt, wird das Standardformular für die Liste angezeigt.

    - **Verwenden eines benutzerdefinierten Formulars, das in powerapps erstellt wurde** : Wenn ein Benutzer die Liste öffnet und in der Befehlsleiste **neu** auswählt, wird das benutzerdefinierte Formular angezeigt. (Alternativ können Sie das Formular erneut in Power apps veröffentlichen.)

    Sie können nach Bedarf zwischen den Optionen wechseln.

    ![Optionen von „Formulareinstellungen“](./media/customize-list-form/form-settings.png)

## <a name="delete-the-custom-form"></a>Benutzerdefiniertes Formular löschen

1. Öffnen Sie über Ihre Liste in SharePoint die Einstellungen (über das Zahnradsymbol in der oberen rechten Ecke), und klicken Sie dann auf **Listeneinstellungen**.

1. Wählen Sie unter **Allgemeine Einstellungen** **Formulareinstellungen** aus.

1. Wählen Sie in den **Formulareinstellungen** **Das SharePoint-Standardformular verwenden** und dann **Delete custom form** (Benutzerdefiniertes Formular löschen) aus.

    ![Benutzerdefiniertes Formular löschen](./media/customize-list-form/use-default-sharepoint.png)

## <a name="q--a"></a>Q & A

### <a name="forms-vs-apps"></a>Vergleich: Formulare und Apps

**F:** Wie unterscheidet sich ein angepasstes Formular von einer eigenständigen APP, die ich aus SharePoint oder powerapps erstelle?

**A:** Wenn Sie das Formular für eine SharePoint-Liste anpassen, wird das Formular nicht als app in powerapps Studio oder Power Apps Mobile angezeigt. Sie können das Formular nur über die Liste öffnen, für die es erstellt wurde.

**F:** Wann sollte ich ein Formular zum Verwalten von Daten in einer SharePoint-Liste anpassen, und wann sollte ich eine eigenständige App erstellen?

**A:** Passen Sie ein Formular an, wenn Sie möchten, dass Benutzer Daten in SharePoint verwalten (z.B. in einem Desktopbrowser). Erstellen Sie eine App, wenn Sie möchten, dass Benutzer Daten außerhalb von SharePoint verwalten (z.B. auf einem mobilen Gerät).

**F:** Kann ich ein Formular anpassen und für dieselbe Liste eine App erstellen?

**A:** Ja.

**F:** Kann ich eine Liste anpassen und eine App mit den gleichen Features erstellen?

**A:** Ja.

**F:** Kann ich ein Formular in einer anderen Umgebung als der Standardumgebung meiner Organisation anpassen?

**A:** Nein.

### <a name="manage-your-custom-form"></a>Verwalten des benutzerdefinierten Formulars

**F:** Wie kann ich mein Formular unkompliziert mit anderen teilen?

**A:** Öffnen Sie das Formular, wählen Sie **Link kopieren**aus, und senden Sie dann den Link an jeden, der das Formular verwenden möchten.

**F:** Kann ich ein Formular aktualisieren, ohne dass die Änderungen für andere Personen angezeigt werden?

**A:** Ja. Sie können das Formular so oft ändern und speichern, wie Sie möchten. Die Änderungen werden jedoch erst für andere Benutzer sichtbar, wenn Sie zweimal auf **In SharePoint veröffentlichen** klicken.

**F:** Kann ich eine frühere Version wiederherstellen, wenn mir beim Anpassen eines Listenformulars ein Fehler unterläuft?

**A:** Ja.

1. Öffnen Sie Ihre Liste, klicken Sie auf der Befehlsleiste auf **PowerApps**, und wählen Sie dann **Customize forms** (Formulare anpassen) aus.

1. Wählen Sie in powerapps Studio **Datei**aus, und klicken Sie dann auf **alle Versionen**anzeigen. Die Seite **Versionen** wird in einer neuen Browserregisterkarte geöffnet.

    > [!NOTE]
    > Wenn die Schaltfläche **Alle Versionen anzeigen** nicht angezeigt wird, klicken Sie auf **Speichern**. Anschließend wird die Schaltfläche angezeigt.

1. Wechseln Sie in der anderen Browser Registerkarte zurück zur Seite **Speichern** , klicken oder tippen Sie auf den Pfeil am oberen Rand des linken Navigationsbereichs, und klicken oder tippen Sie auf **zurück zu SharePoint** , **um das Formular** zu entsperren und powerapps Studio zu schließen.

1. Kehren Sie zur Seite **Versionen** auf der anderen Browserregisterkarte zurück, suchen Sie die Version, die Sie wiederherstellen möchten, und klicken Sie dann auf **Wiederherstellen**.

    > [!NOTE]
    > Wenn Sie eine Fehlermeldung erhalten, die besagt, dass die Wiederherstellung fehlgeschlagen ist, weil das Formular von einem anderen Benutzer gesperrt ist, warten Sie, bis der Benutzer das Formular entsperrt, und versuchen Sie es dann erneut

**F:** Kann ich mein Formular aus einer Liste in eine andere verschieben?

**A:** Nein.

### <a name="administer-your-custom-form"></a>Verwalten des benutzerdefinierten Formulars

**F:** Wie gebe ich mein Formular frei?

**A:** Sie müssen das Formular nicht freigeben – das Formular erbt Berechtigungen von der SharePoint-Liste. Wenn Sie es angepasst haben, [veröffentlichen Sie es einfach wieder in SharePoint](customize-list-form.md#save-and-publish-the-form), damit es von anderen Benutzern verwendet werden kann.

**F:** Wer kann Formulare anpassen?

**A:** Jeder Benutzer mit SharePoint-Berechtigungen zum Verwalten, Entwerfen oder Bearbeiten der zugehörigen Liste.

**F:** Benötige ich eine powerapps-Lizenz, um benutzerdefinierte Listen Formulare zu erstellen oder zu verwenden?

**A:** Sie benötigen einen [Office 365-Plan, der powerapps enthält](https://docs.microsoft.com/power-platform/admin/pricing-billing-skus#licenses).

**F:** Was geschieht, wenn Gastbenutzer auf eine Liste zuzugreifen, die ein benutzerdefiniertes Formular aufweist?

**A:** Gastbenutzer erhalten eine Fehlermeldung, wenn Sie versuchen, auf ein Listen Formular zuzugreifen, das mit powerapps angepasst wurde.

**F:** Wie erhalte ich als Administrator eine Liste aller benutzerdefinierten Formulare in meiner Organisation?

**A:** Wenn Sie ein Mandanten Administrator für Power apps sind oder Sie über Umgebungs Administrator Berechtigungen für die Standardumgebung von Power Apps ihrer Organisation verfügen, gehen Sie wie folgt vor:

1. Wählen Sie im [powerapps Admin Center](https://admin.powerapps.com)in der Liste der Umgebungen die Standardumgebung für Ihre Organisation aus.

1. Wählen Sie oben auf der Seite für die Standardumgebung **Ressourcen** aus.

1. Suchen Sie in der Liste der apps nach Apps mit einem **SharePoint-Formular** -App-Typ – Dies sind die angepassten Formulare.

    ![Liste der benutzerdefinierten Formulare](./media/customize-list-form/all-customized-forms.png)
