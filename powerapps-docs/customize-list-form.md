---
title: Anpassen eines SharePoint-Listenformulars mit PowerApps | Microsoft-Dokumentation
description: Passen Sie ein Listenformular in SharePoint mithilfe von PowerApps an.
services: 
suite: powerapps
documentationcenter: na
author: skjerland
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 02/05/2018
ms.author: sharik
ms.openlocfilehash: a1ebe4011619b0a2baaa3b9a98579bb22d02774e
ms.sourcegitcommit: 290e81488ec5c2e0bb820ef0e3b7f5c0f54c80eb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/09/2018
---
# <a name="customize-a-sharepoint-list-form-using-powerapps"></a>Anpassen eines SharePoint-Listenformulars mit PowerApps

Sie können jetzt in PowerApps jedes SharePoint-Listenformular leicht anpassen. Sie können viele der Aktionen, die Sie in InfoPath zum Anpassen von SharePoint-Listenformularen ausgeführt haben, jetzt mit PowerApps inline in einem Browser ausführen. Und PowerApps bietet Ihnen noch viele weitere Möglichkeiten!

PowerApps ist direkt in SharePoint integriert – Sie müssen keine weitere App auf Ihren Computer herunterladen. Und mit PowerApps können Sie individuell angepasste Formulare erstellen, ohne Code schreiben zu müssen. Die Formulare werden nach der Veröffentlichung in die SharePoint-Liste eingebettet und sind für alle Benutzer der Liste verfügbar.

Und weil PowerApps nahtlos in SharePoint integriert ist, besteht keine Notwendigkeit, Formulare an zwei Stellen zu verwalten: Berechtigungen werden von SharePoint geerbt und in SharePoint verwaltet. Zudem erhalten Sie durch die Integration von PowerApps in SharePoint Zugriff auf viele leistungsstarke Features, z.B. Analytics-Berichte, leicht zu verwendende Point-and-Click-Regeln für bedingte Formatierung und Verbindungen mit anderen Datenquellen.

Sind Sie zum Anpassen bereit? Lassen Sie uns loslegen!

## <a name="create-a-custom-list-form-app-in-powerapps"></a>Erstellen einer benutzerdefinierten Listenformular-App in PowerApps

> [!NOTE]
> Die Option **Formulare anpassen** ist nicht verfügbar oder wird möglicherweise nicht ordnungsgemäß ausgeführt, wenn die SharePoint-Liste Datentypen enthält, die von PowerApps nicht unterstützt werden.

Klicken oder tippen Sie in der SharePoint-Liste auf **PowerApps** in der Befehlszeile, und klicken oder tippen Sie anschließend auf **Formulare anpassen**. Dadurch wird PowerApps Studio für Web in einem Browser geöffnet und eine Formular-App mit einem einzelnen Bildschirm generiert, wie im folgenden Beispiel gezeigt.

![Formular-App mit einzelnem Bildschirm](./media/customize-list-form/list-form-app.png)

Sie können jederzeit zur SharePoint-Liste zurückkehren, indem Sie in PowerApps Studio für Web links oben auf **Zurück zu SharePoint** klicken oder tippen.

## <a name="customize-the-list-form"></a>Anpassen des Listenformulars

PowerApps bietet viele Möglichkeiten zum Anpassen des Formulars. Hier sind einige Beispiele:

* [Ändern der Größe und Ausrichtung](set-aspect-ratio-portrait-landscape.md)
* [Formatieren des Texts](controls/properties-text.md)
* [Hinzufügen von Bildern](add-images-pictures-audio-video.md) oder [Diagrammen](use-line-pie-bar-chart.md)
* [Hinzufügen von benutzerdefinierter Datenüberprüfung](functions/function-validate.md)
* [Hinzufügen von Regeln](working-with-rules.md)
* [Erstellen zusätzlicher Ansichten](https://powerapps.microsoft.com/blog/separate-custom-forms/)

Nehmen wir zur Veranschaulichung an, das Formular enthält das Feld **AccountID**, das nicht angezeigt werden soll.

![Feld „AccountID“ auswählen](./media/customize-list-form/select-card.png)

Das Feld lässt sich in PowerApps einfach ausblenden – deaktivieren Sie einfach in den Optionen für die Formularanpassung das Kontrollkästchen **AccountID**.

![Kontrollkästchen „AccountID“ deaktivieren](./media/customize-list-form/checkbox.png)

Schritt-für-Schritt-Anweisungen zum Ausblenden von Feldern und Vornehmen weiterer Formularänderungen finden Sie unter [Anpassen von Formularen in PowerApps](customize-forms-sharepoint.md). Eine vollständige Liste der Ressourcen finden Sie in der [Dokumentation zu Microsoft PowerApps](https://docs.microsoft.com/powerapps/).

## <a name="save-and-publish-the-list-form-back-to-sharepoint"></a>Speichern und Veröffentlichen des Listenformulars in SharePoint

1. Wenn Sie fertig sind, klicken oder tippen Sie auf **Datei** und dann auf **Speichern**. Dadurch werden die Änderungen in der PowerApps-Formular-App gespeichert.

1. Um das Formular wieder in SharePoint zu veröffentlichen, damit es von anderen Benutzern verwendet werden kann, klicken oder tippen Sie auf **In SharePoint veröffentlichen**. Sie müssen sich keine Gedanken über die Freigabe des Formulars machen – das Formular erbt die Berechtigungen aus der SharePoint-Liste.

    ![Veröffentlichen in SharePoint](./media/customize-list-form/publish-to-sharepoint.png)  

## <a name="view-your-list-form-in-sharepoint"></a>Anzeigen des Listenformulars in SharePoint

1. Um das angepasste Formular anzuzeigen, klicken oder tippen Sie auf **Zurück zu SharePoint**, und klicken oder tippen Sie dann auf ein beliebiges Element in der SharePoint-Liste. Das Formular wird inline auf der rechten Seite des Browserfensters geöffnet.

    ![Formular inline in SharePoint öffnen](./media/customize-list-form/list-form-open.png)

1. Wenn Sie [das Formular weiter anpassen](sharepoint-form-integration.md) möchten, klicken oder tippen Sie auf **Anpassen**, und nehmen Sie dann die Änderungen vor. Wenn Sie fertig sind, müssen Sie die Änderungen speichern.

    ![Schaltfläche „Anpassen“](./media/customize-list-form/customize-button.png)

    Sie können das Formular so oft anpassen und speichern, wie Sie möchten. Die Änderungen werden jedoch erst in SharePoint angezeigt, wenn Sie auf **In SharePoint veröffentlichen** klicken oder tippen.

## <a name="toggle-between-using-the-default-sharepoint-form-and-the-custom-form"></a>Wechseln zwischen der Verwendung des SharePoint-Standardformulars und des benutzerdefinierten Formulars

1. Klicken oder tippen Sie in der Liste in SharePoint auf **Einstellungen**, auf **Listeneinstellungen** und dann auf **Formulareinstellungen**.

1. Klicken oder tippen Sie auf der Seite **Formulareinstellungen** auf eine der folgenden Einstellungen, und klicken oder tippen Sie dann auf **OK**.

    * **Das SharePoint-Standardformular verwenden** – Für die Liste wird das SharePoint-Standardformular verwendet.

    * **In PowerApps erstelltes benutzerdefiniertes Formular verwenden** – In SharePoint wird das Formular verwendet, das Sie in PowerApps angepasst haben. (Alternativ können Sie das Formular über die Seite **Speichern** von PowerApps Studio für Web erneut veröffentlichen.)

    Sie können nach Bedarf zwischen den Optionen wechseln.

    ![Optionen von „Formulareinstellungen“](./media/customize-list-form/form-settings.png)

## <a name="delete-the-custom-list-form"></a>Löschen des benutzerdefinierten Listenformulars

1. Klicken oder tippen Sie in der Liste in SharePoint auf **Einstellungen**, auf **Listeneinstellungen** und dann auf **Formulareinstellungen**.

1. Klicken oder tippen Sie auf der Seite **Formulareinstellungen** auf **Das SharePoint-Standardformular verwenden**, und klicken oder tippen Sie dann unter der Option **In PowerApps erstelltes benutzerdefiniertes Formular verwenden** auf **Benutzerdefiniertes Formular löschen**. Dadurch wird das benutzerdefinierte Formular, das Sie in PowerApps erstellt haben, gelöscht, und das Formular wird auf ein SharePoint-Standardformular zurückgesetzt.

    ![Benutzerdefiniertes Formular löschen](./media/customize-list-form/use-default-sharepoint.png)

## <a name="top-questions-about-list-form-customization"></a>Wichtige Fragen zur Anpassung von Listenformularen

### <a name="customizing-forms-versus-creating-apps"></a>Anpassen von Formularen oder Erstellen von Apps

**F:** Wie unterscheidet sich ein angepasstes Listenformular von einer eigenständigen App, die ich in SharePoint oder PowerApps erstelle?

**A:** Die Listenformular-App, die Sie in SharePoint erstellen, ist ein besonderer Typ von PowerApps-App, der nur in einer SharePoint-Liste verwendet werden kann. Diese Listenformular-Apps werden nicht in der Liste der Apps in PowerApps Studio für Web oder PowerApps Mobile angezeigt, und Sie können sie nicht außerhalb der SharePoint-Liste ausführen.

**F:** Wann sollte ich ein benutzerdefiniertes Listenformular und wann eine eigenständige App erstellen?

**A:** Wenn die Benutzer mit SharePoint auf das Formular zugreifen sollen und Sie anpassen möchten, wie Benutzer Listenelemente erstellen, anzeigen oder bearbeiten, empfiehlt es sich, in SharePoint ein benutzerdefiniertes Listenformular zu erstellen. Wenn Sie eine umfassend angepasste App für die Benutzer erstellen möchten, die sie unabhängig von der SharePoint-Website verwenden können, empfiehlt sich das Erstellen einer eigenständigen App.

**F:** Kann ich ein Listenformular anpassen und für dieselbe Liste eine eigenständige App erstellen?

**A:** Ja. Eigenständige Apps und benutzerdefinierte Listenformulare sind voneinander unabhängig. Sie können sie einzeln anpassen und verwalten.

**F:** Sind die Features zum Anpassen eines Listenformulars die gleichen wie die Features zum Anpassen einer eigenständigen App?

**A:** Ja. Sie können genau wie für eigenständige Apps [Steuerelemente hinzufügen und konfigurieren](add-configure-controls.md), [Verbindungen mit verfügbaren Datenquellen herstellen](add-data-connection.md) oder [eigene Datenquellen hinzufügen](register-custom-api.md).

**F:** Kann ich benutzerdefinierte Listenformulare in einer anderen Umgebung als der Standardumgebung meiner Organisation erstellen?

**A:** Nein. Derzeit können Sie benutzerdefinierte Listenformulare nur in der PowerApps-Standardumgebung Ihrer Organisation erstellen. Sie können keine benutzerdefinierten Listenformulare in einer anderen Umgebung erstellen oder zu einer anderen Umgebung migrieren.

### <a name="managing-your-custom-list-form"></a>Verwalten des benutzerdefinierten Listenformulars

**F:** Wie erhalte ich einen direkten Link zu meinem Listenformular, den ich für andere Benutzer freigeben kann?

**A:** Öffnen Sie in der SharePoint-Liste das Formular, und klicken oder tippen Sie dann auf **Link kopieren**.

**F:** Kann ich ein Listenformular aktualisieren, ohne dass die Änderungen für andere Personen angezeigt werden?

**A:** Ja. Sie können das Formular so oft ändern und speichern, wie Sie möchten. Die Änderungen werden jedoch erst für andere Benutzer angezeigt, wenn Sie auf **[In SharePoint veröffentlichen](customize-list-form.md#save-and-publish-the-list-form-back-to-sharepoint)** klicken oder tippen.

**F:** Kann ich eine frühere Version wiederherstellen, wenn mir beim Anpassen eines Listenformulars ein Fehler unterläuft?

**A:** Ja. Wenn Sie am Formular Änderungen vornehmen, diese Änderungen speichern und dann feststellen, dass Ihnen ein Fehler unterlaufen ist, können Sie mithilfe von PowerApps eine frühere Version wiederherstellen:

1. Klicken oder tippen Sie in der SharePoint-Liste auf **PowerApps** in der Befehlszeile, und klicken oder tippen Sie anschließend auf **Formulare anpassen**.

1. Klicken oder tippen Sie in PowerApps Studio für Web auf **Datei**, auf **Speichern** und dann auf **Alle Versionen anzeigen**. Die Seite **Versionen** wird in einer neuen Browserregisterkarte geöffnet.

    > [!NOTE]
    > Wenn die Schaltfläche **Alle Versionen anzeigen** nicht angezeigt wird, klicken Sie auf **Speichern**. Anschließend wird die Schaltfläche angezeigt.

1. Lassen Sie die Seite oder Browserregisterkarte **Versionen** geöffnet, und kehren Sie zur Seite **Speichern** in der anderen Browserregisterkarte zurück. Klicken oder tippen Sie dann auf den Pfeil am oberen Rand des linken Navigationsbereichs, und klicken oder tippen Sie auf **Zurück zu SharePoint**, um das Formular zu entsperren und PowerApps Studio für Web zu schließen.

1. Kehren Sie zur Seite **Versionen** in der anderen Browserregisterkarte zurück, suchen Sie die Version, die Sie wiederherstellen möchten, und klicken Sie dann auf **Wiederherstellen**.

    > [!NOTE]
    > Wenn Sie die Fehlermeldung erhalten, dass die Wiederherstellung fehlgeschlagen ist, da das Formular von einem anderen Benutzer gesperrt ist, warten Sie, bis der Benutzer das Formular entsperrt, und wiederholen Sie den Vorgang.

**F:** Kann ich ein benutzerdefiniertes Listenformular aus einer Liste in eine andere verschieben?

**A:** Nein. Diese Funktionalität wird derzeit nicht unterstützt.

### <a name="administering-custom-list-forms"></a>Verwalten von benutzerdefinierten Listenformularen

**F:** Wie gebe ich mein benutzerdefiniertes Listenformular für andere Benutzer frei?

**A:** Sie müssen das Formular nicht freigeben – es erbt die Berechtigungen aus der SharePoint-Liste. Wenn Sie es angepasst haben, [veröffentlichen Sie es einfach wieder in SharePoint](customize-list-form.md#save-and-publish-the-list-form-back-to-sharepoint), damit es von anderen Benutzern verwendet werden kann.

**F:** Wer kann Listenformulare anpassen?

**A:** Jeder Benutzer mit SharePoint-Berechtigungen zum Verwalten, Entwerfen oder Bearbeiten der zugehörigen Liste.

**F:** Benötige ich eine PowerApps-Lizenz, um benutzerdefinierte Listenformulare zu erstellen und zu verwenden?

**A:** Wenn Sie über einen [Office 365-Plan mit PowerApps](pricing-billing-skus.md#licenses) verfügen, können Sie benutzerdefinierte Listenformulare erstellen und verwenden.

**F:** Was geschieht, wenn Gastbenutzer auf eine Liste zuzugreifen, die ein benutzerdefiniertes Formular aufweist?

**A:** Gastbenutzer erhalten eine Fehlermeldung, wenn sie versuchen, auf ein Listenformular zuzugreifen, das mit PowerApps angepasst wurde.

**F:** Wie erhalte ich als Administrator eine Liste aller benutzerdefinierten Formulare in meiner Organisation?

**A:** Wenn Sie ein Mandantenadministrator für PowerApps sind oder über Umgebungsadministratorberechtigungen für die PowerApps-Standardumgebung Ihrer Organisation verfügen, gehen Sie wie folgt vor:

1. Wechseln Sie zum [PowerApps Admin Center](https://admin.powerapps.com), und wählen Sie in der Liste der Umgebungen die Standardumgebung für Ihre Organisation aus.

1. Klicken oder tippen Sie oben auf der Seite für die Standardumgebung auf **Ressourcen**.

1. Suchen Sie in der Liste der Apps nach Apps mit dem App-Typ **SharePoint-Formular** – dies sind die angepassten Formulare.

    ![Liste der benutzerdefinierten Formulare](./media/customize-list-form/all-customized-forms.png)
