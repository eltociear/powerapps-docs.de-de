---
title: Anpassen eines SharePoint-Listenformulars | Microsoft-Dokumentation
description: Verwenden Sie PowerApps, um das Formular anzupassen, über das Benutzer Einträge in einer SharePoint-Liste erstellen und bearbeiten.
author: AFTOwen
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 12/17/2018
ms.author: anneta
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 711d8029f0f8353efcdff5bea8cbb1402884502f
ms.sourcegitcommit: 647e183c070c2159b790c7813a7be1d60b2551bd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/01/2019
ms.locfileid: "58765477"
---
# <a name="customize-a-sharepoint-list-form-by-using-powerapps"></a>Anpassen eines SharePoint-Listenformulars mit PowerApps

Sie können das Formular für eine SharePoint-Liste leicht anpassen, wenn Sie PowerApps in einem Browser öffnen. Sie müssen keinen herkömmlichen Code (wie C#) schreiben oder eine weitere App (wie InfoPath) herunterladen. Wenn Sie Ihre Änderungen veröffentlichen, wird das Formular in die SharePoint-Liste eingebettet, sodass es von allen Benutzern verwendet werden kann. Sie können sich in PowerApps auch Analyseberichte ansehen, im Handumdrehen bedingte Formatierungen erstellen und eine Verbindung mit anderen Datenquellen herstellen.

Für die in diesem Artikel beschriebenen Schritte benötigen Sie eine einfache Liste, um nachvollziehen zu können, wie die Anpassung funktioniert. Anschließend können Sie diese Konzepte auf Ihre eigene Liste anwenden.

> [!NOTE]
> Wenn die Option **Formulare anpassen** nicht verfügbar ist oder nicht ordnungsgemäß für Ihre Liste ausgeführt wird, enthält diese möglicherweise Datentypen, die [von PowerApps nicht unterstützt werden](connections/connection-sharepoint-online.md#known-issues). Sie können Ihr Formular nicht in eine andere Liste oder [Umgebung](working-with-environments.md) verschieben.

## <a name="create-a-list"></a>Erstellen Sie eine Liste

Erstellen Sie eine Liste, und klicken Sie dann fügen Sie diese Spalten in dieser Liste hinzu, auf einer SharePoint-Website:

- **Details** (ja/nein)
- **Price** (Währung)
- **Availability** (Datum ohne Uhrzeit)
- **Color** (Auswahl)

> [!div class="mx-imgBorder"]
> ![Wählen Sie die Website-Inhalte > Neu > auflisten, geben Sie den Listennamen und select erstellen. Wählen Sie für jede Spalte, Hinzufügen einer Spalte aus, geben Sie den "List" (Ja/Nein, Währung, Datum, Wahl), geben Sie den Listennamen (Details, Preise, Verfügbarkeit, Farbe), und wählen Sie speichern.](./media/customize-list-form/create-list.gif)

## <a name="open-the-form"></a>Öffnen Sie das Formular

1. Wählen Sie in der Befehlsleiste **PowerApps**, und wählen Sie dann **Formular anpassen**.

    PowerApps Studio wird auf der gleichen Registerkarte im Browser geöffnet.

1. Falls das Dialogfeld **Willkommen bei PowerApps Studio** geöffnet wird, wählen Sie **Überspringen** aus.

> [!div class="mx-imgBorder"]
> ![Klicken Sie auf der Befehlsleiste wählen Sie PowerApps, und wählen Sie dann das Formular anpassen. PowerApps Studio wird auf der gleichen Registerkarte im Browser geöffnet. Wenn die Willkommen bei PowerApps Studio-Dialogfeld geöffnet wird, wählen Sie überspringen.](./media/customize-list-form/create-form.gif)

## <a name="move-and-remove-a-field"></a>Verschieben und Entfernen von Feldern

1. Ziehen Sie die **Verfügbarkeit** Feld am Ende der Liste der Felder.

    Felder, die in den, die von Ihnen angegebenen Reihenfolge angezeigt werden.

1. Zeigen Sie auf die **Anlagen** Feld, wählen Sie die Auslassungspunkte (...), die angezeigt wird, und wählen Sie dann **entfernen**.

    Das Feld, das Sie angeben, nicht mehr auf das Formular.

> [!div class="mx-imgBorder"]
> ![Ziehen Sie das Feld für die Verfügbarkeit am Ende der Liste der Felder ein. Zeigen Sie auf das Feld "Anlagen", wählen Sie die Auslassungspunkte (...), die angezeigt wird, und wählen Sie dann auf Entfernen.](./media/customize-list-form/move-remove-fields.gif)

## <a name="set-conditional-formatting"></a>Festlegen bedingter Formatierung

Sie können die Felder **Price**, **Availability** und **Colors** so konfigurieren, dass sie nur angezeigt werden, wenn **Details** auf „Yes“ (Ja) festgelegt ist.

1. Erweitern Sie in der linken Navigationsleiste auf **Details_DataCard1**, und notieren Sie sich die Zahl, die am Ende angezeigt **DataCardValue**.

1. Legen Sie die **Sichtbarkeit** Eigenschaft der **Farbe**, **Verfügbarkeit**, und **Preis** Karten auf diese Formel (ersetzen, falls erforderlich, die wird mit dem Sie im vorherigen Schritt notiert haben):

    **If(DataCardValue2.Value = true, true)**

1. Halten Sie die ALT-TASTE gedrückt, und tippen oder klicken Sie mehrmals auf den Schalter **Details**.

    Die drei von Ihnen konfigurierten Felder werden angezeigt und wieder ausgeblendet.

> [!div class="mx-imgBorder"]
> ![Beachten Sie in der linken Navigationsleiste auf die Zahl, die am Ende der DataCardValue angezeigt wird. Die Visibility-Eigenschaft, der die Farbe, Verfügbarkeit und Preis Karten auf diese Formel festgelegt. Halten Sie die Alt-Taste gedrückt, und wählen Sie das Detailsteuerelement mehrere Male.](./media/customize-list-form/conditional-format.gif)

## <a name="save-and-publish-the-form"></a>Speichern Sie und veröffentlichen Sie das Formular

1. Öffnen Sie das Menü **Datei**, klicken Sie auf **Speichern**, und wählen Sie dann zweimal **In SharePoint veröffentlichen**.

1. Klicken Sie in der oberen linken Ecke auf den Zurück-Pfeil, und klicken Sie dann auf **Zurück zu SharePoint**.

> [!div class="mx-imgBorder"]
> ![Öffnen Sie das Menü "Datei", wählen Sie speichern, und wählen Sie dann zweimal auf in SharePoint veröffentlichen. Wählen Sie den zurück-Pfeil, und wählen Sie dann wieder in SharePoint, in der oberen linken Ecke.](./media/customize-list-form/save-form.gif)

## <a name="further-customize-your-form"></a>Das Formular weiter anpassen

1. Öffnen Sie die Liste, wählen Sie **neu** im Befehl, und klicken Sie anschließend **anpassen** im oberen Bereich des Formulars.

1. Passen Sie Ihr Formular eine Vielzahl von Möglichkeiten, wie z. B. diejenigen, die die folgenden Themen beschreiben:

    - Ändern Sie die Größe, Ausrichtung oder beides (Sie können das Formular z.B. [breiter machen](set-aspect-ratio-portrait-landscape.md))
    - [Anpassen einer oder mehreren Karten](working-with-cards.md) (z. B. Ändern einer Karte Text oder Eingabe Steuerung der Anzeige).
    - Erstellen Sie ein [Nachschlagefeld](sharepoint-lookup-fields.md).

    Weitere Informationen finden Sie unter: [Verstehen der Integration von SharePoint-Formularen](sharepoint-form-integration.md)

## <a name="use-the-default-form"></a>Verwenden des Standardformulars

1. Öffnen Sie über Ihre Liste in SharePoint die Einstellungen (über das Zahnradsymbol in der oberen rechten Ecke), und klicken Sie dann auf **Listeneinstellungen**.

2. Wählen Sie unter **Allgemeine Einstellungen** **Formulareinstellungen** aus.

3. Wählen Sie eine der folgenden Optionen in den **Formulareinstellungen**, und klicken Sie dann auf **OK**.

    - **Das SharePoint-Standardformular verwenden**: Wenn ein Benutzer Ihre Liste öffnet und auf der Befehlsleiste auf **Neu** klickt, wird das Standardformular für die Liste angezeigt.

    - **Use a custom form created in PowerApps** (Das in PowerApps erstellte Formular verwenden): Wenn ein Benutzer Ihre Liste öffnet und auf der Befehlsleiste auf **Neu** klickt, wird Ihr benutzerdefiniertes Formular angezeigt. (Alternativ können Sie das Formular auch erneut in PowerApps veröffentlichen).

    Sie können nach Bedarf zwischen den Optionen wechseln.

    ![Optionen von „Formulareinstellungen“](./media/customize-list-form/form-settings.png)

## <a name="delete-the-custom-form"></a>Benutzerdefiniertes Formular löschen

1. Öffnen Sie über Ihre Liste in SharePoint die Einstellungen (über das Zahnradsymbol in der oberen rechten Ecke), und klicken Sie dann auf **Listeneinstellungen**.

1. Wählen Sie unter **Allgemeine Einstellungen** **Formulareinstellungen** aus.

1. Wählen Sie in den **Formulareinstellungen** **Das SharePoint-Standardformular verwenden** und dann **Delete custom form** (Benutzerdefiniertes Formular löschen) aus.

    ![Benutzerdefiniertes Formular löschen](./media/customize-list-form/use-default-sharepoint.png)

## <a name="q--a"></a>HÄUFIG GESTELLTE FRAGEN

### <a name="forms-vs-apps"></a>Vergleich: Formulare und Apps

**Q:** Wie unterscheidet ein angepasstes Formular in eine eigenständige app, den ich in SharePoint oder PowerApps erstelle?

**A:** Wenn Sie das Formular für eine SharePoint-Liste anpassen, nicht das Formular als app in PowerApps Studio oder PowerApps Mobile angezeigt. Sie können das Formular nur über die Liste öffnen, für die es erstellt wurde.

**Q:** Wann sollten Sie ein Formular zum Verwalten von Daten in einer SharePoint-Liste anpassen, und wann sollte ich eine eigenständige app erstellen?

**A:** Anpassen eines Formulars an, wenn Sie möchten, dass Ihre Benutzer zum Verwalten von Daten ohne SharePoint (z. B. in einem Desktopbrowser). Erstellen Sie eine App, wenn Sie möchten, dass Benutzer Daten außerhalb von SharePoint verwalten (z.B. auf einem mobilen Gerät).

**Q:** Kann ich Anpassen eines Formulars, und erstellen Sie eine app für die gleiche Liste?

**A:** Ja.

**Q:** Kann ich anpassen eine Liste und erstellen Sie eine app, indem die gleichen Funktionen?

**A:** Ja.

**Q:** Kann ich in meiner Organisation ein Formular in einer anderen Umgebung als standardumgebung anpassen?

**A:** Nein.

### <a name="manage-your-custom-form"></a>Verwalten des benutzerdefinierten Formulars

**Q:** Wie kann ich mein Formular einfach für andere Benutzer freigeben?

**A:** Öffnen Sie das Formular, wählen Sie **Link kopieren**, und senden Sie dann auf den Link für alle Benutzer das Formular verwendet werden sollen.

**Q:** Kann ich meine Form aktualisieren, ohne dass die Änderungen für andere Benutzer sichtbar?

**A:** Ja. Sie können das Formular so oft ändern und speichern, wie Sie möchten. Die Änderungen werden jedoch erst für andere Benutzer sichtbar, wenn Sie zweimal auf **In SharePoint veröffentlichen** klicken.

**Q:** Wenn ich ein Listenformular anpassen und ein Fehler unterläuft, kann ich eine frühere Version wiederherstellen?

**A:** Ja.

1. Öffnen Sie Ihre Liste, klicken Sie auf der Befehlsleiste auf **PowerApps**, und wählen Sie dann **Customize forms** (Formulare anpassen) aus.

1. Klicken Sie in PowerApps Studio auf **Datei** und dann auf **Alle Versionen anzeigen**. Die Seite **Versionen** wird in einer neuen Browserregisterkarte geöffnet.

    > [!NOTE]
    > Wenn die Schaltfläche **Alle Versionen anzeigen** nicht angezeigt wird, klicken Sie auf **Speichern**. Anschließend wird die Schaltfläche angezeigt.

1. Lassen Sie die Seite oder Browserregisterkarte **Versionen** geöffnet, und kehren Sie zur Seite **Speichern** auf der anderen Browserregisterkarte zurück. Klicken oder tippen Sie dann auf den Pfeil am oberen Rand des linken Navigationsbereichs, und klicken oder tippen Sie auf **Zurück zu SharePoint**, um das Formular zu entsperren und PowerApps Studio zu schließen.

1. Kehren Sie zur Seite **Versionen** auf der anderen Browserregisterkarte zurück, suchen Sie die Version, die Sie wiederherstellen möchten, und klicken Sie dann auf **Wiederherstellen**.

    > [!NOTE]
    > Wenn Sie die Fehlermeldung erhalten, dass die Wiederherstellung fehlgeschlagen ist, da das Formular von einem anderen Benutzer gesperrt ist, warten Sie, bis der Benutzer das Formular entsperrt, und wiederholen Sie den Vorgang.

**Q:** Kann ich mein Formular aus einer Liste in ein anderes verschieben?

**A:** Nein.

### <a name="administer-your-custom-form"></a>Verwalten des benutzerdefinierten Formulars

**Q:** Wie gebe ich mein Formular frei?

**A:** Sie müssen nicht die Form gemeinsam verwenden – das Formular erbt die Berechtigungen aus der SharePoint-Liste. Wenn Sie es angepasst haben, [veröffentlichen Sie es einfach wieder in SharePoint](customize-list-form.md#save-and-publish-the-form), damit es von anderen Benutzern verwendet werden kann.

**Q:** Wer kann Formulare anpassen?

**A:** Jeder Benutzer mit SharePoint-Berechtigungen zum Verwalten, entwerfen oder Bearbeiten der zugehörigen Liste.

**Q:** Benötige ich eine PowerApps-Lizenz zum Erstellen oder verwenden benutzerdefinierte Listenformulare?

**A:** Sie müssen eine [Office 365-Plan, der PowerApps umfasst](https://docs.microsoft.com/power-platform/admin/pricing-billing-skus.md#licenses).

**Q:** Was geschieht, wenn der Gastbenutzer die Möglichkeit, eine Liste zuzugreifen, die ein benutzerdefiniertes Formular aufweist?

**A:** Gastbenutzer erhalten eine Fehlermeldung angezeigt, wenn sie versuchen, ein Listenformular zuzugreifen, die mit PowerApps angepasst wurde.

**Q:** Als Administrator wie erhalte eine Liste aller benutzerdefinierten Formulare in meiner Organisation ich?

**A:** Wenn Sie ein mandantenadministrator für PowerApps oder Sie die Umgebung-Administratorberechtigungen auf den PowerApps-standardumgebung Ihrer Organisation haben, führen Sie folgende Schritte aus:

1. Wählen Sie im [PowerApps Admin Center](https://admin.powerapps.com) in der Liste der Umgebungen die Standardumgebung für Ihre Organisation aus.

1. Wählen Sie oben auf der Seite für die Standardumgebung **Ressourcen** aus.

1. Suchen Sie in der Liste der Apps nach Apps mit dem App-Typ **SharePoint-Formular** – dies sind die angepassten Formulare.

    ![Liste der benutzerdefinierten Formulare](./media/customize-list-form/all-customized-forms.png)
