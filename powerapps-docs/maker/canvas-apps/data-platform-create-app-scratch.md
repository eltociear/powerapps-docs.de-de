---
title: Erstellen einer Canvas-App von Grund auf mit Common Data Service | Microsoft-Dokumentation
description: Erstellen Sie in powerapps eine Canvas-App zum Hinzufügen, aktualisieren und Löschen von Datensätzen in Common Data Service.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 05/21/2019
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 48cd98481cff354d4e54cb54dc38865f6dfa6a14
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2019
ms.locfileid: "74679682"
---
# <a name="create-a-canvas-app-from-scratch-using-common-data-service"></a>Erstellen einer Canvas-App von Grund auf mit Common Data Service

Erstellen Sie eine Canvas-App, um Daten zu verwalten, die in Common Data Service gespeichert sind. Verwenden Sie dazu (integrierte) Standardentitäten, (von Ihrem Unternehmen erstellte) benutzerdefinierte Entitäten oder beides.

Wenn Sie eine APP aus Common Data Service erstellen, müssen Sie keine Verbindung von powerapps erstellen, wie dies bei Datenquellen wie SharePoint, Dynamics 365 oder Salesforce der Fall ist. Sie müssen nur die Entitäten angeben, die Sie in der App anzeigen bzw. verwalten möchten.

## <a name="prerequisites"></a>Voraussetzungen

- Bevor Sie eine APP von Grund auf neu erstellen, machen Sie sich mit den Grundlagen von Power apps vertraut, indem Sie [eine APP](data-platform-create-app.md) erstellen und [dann den Katalog, die](customize-layout-sharepoint.md) [Formulare](customize-forms-sharepoint.md)und die [Karten](customize-card.md)der APP anpassen.
- [Wechseln Sie in eine Umgebung](working-with-environments.md), in der mithilfe von einfachen Daten eine Datenbank erstellt wurde. Wenn Sie über eine entsprechende Lizenz verfügen, können Sie dafür eine [Umgebung erstellen](../../administrator/create-environment.md).
- Um eine App erstellen zu können, müssen Sie der Sicherheitsrolle [Umgebungsersteller](https://docs.microsoft.com/power-platform/admin/database-security#predefined-security-roles) zugewiesen sein.

## <a name="open-a-blank-app"></a>Öffnen einer leeren App

1. Melden Sie sich bei [PowerApps](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an.

1. Wählen Sie unter **Eigene App erstellen** die Option **Canvas-App ohne Vorlage** aus.

    ![Kachel für leere App](./media/data-platform-create-app-scratch/blank-app.png)

1. Geben Sie einen Namen für Ihre App an, wählen Sie **Telefon** aus, und klicken Sie dann auf **Erstellen**.

    Sie können auch für Tablets eine App von Grund auf neu erstellen. In diesem Thema geht es jedoch um das Erstellen einer App für Smartphones.

## <a name="specify-an-entity"></a>Angeben einer Entität

1. Wählen Sie in der Mitte des Bildschirms **Mit Daten verbinden** aus.

1. Klicken Sie im Bereich **Daten** auf **Common Data Service**, aktivieren Sie das Kontrollkästchen bei **Konten**, und klicken Sie anschließend auf **Verbinden**.

1. Schließen Sie den Bereich **Daten**, indem Sie in der oberen rechten Ecke das Symbol zum Schließen auswählen.

## <a name="add-a-list-screen"></a>Hinzufügen einer Listenanzeige

1. Wählen Sie auf der Registerkarte **Start** den Pfeil nach unten für **Neuer Bildschirm** aus, und klicken Sie dann auf **Liste**.

    ![Hinzufügen einer Listenanzeige](./media/data-platform-create-app-scratch/list-screen.png)

1. Klicken Sie in der linken Navigationsleiste auf **BrowseGallery1**, und legen Sie dann den Wert für die Eigenschaft **Elemente** auf die folgende Formel fest:

    `SortByColumns(Search(Accounts, TextSearchBox1.Text, "name"), "name", If(SortDescending1, SortOrder.Descending, SortOrder.Ascending))`

    Diese Formel gibt Folgendes an:

   - Im Katalog sollten die Daten aus der Entität **Accounts** angezeigt werden.
   - Die Daten sollten in aufsteigender Reihenfolge angezeigt werden, bis der Benutzer auf die Schaltfläche „Sortieren“ klickt, um die Reihenfolge umzukehren.
   - Wenn der Benutzer mindestens ein Zeichen in die Suchleiste eintippt bzw. einfügt (**TextSearchBox1**), werden in der Liste nur die Konten angezeigt, in denen das **Namensfeld** die vom Benutzer angegebenen Zeichen enthält.

     Sie können [diese sowie viele weitere Funktionen](formula-reference.md) verwenden, um anzugeben, wie Ihre App angezeigt werden und sich verhalten soll.

     ![Festlegen der Items-Eigenschaft des Katalogs](./media/data-platform-create-app-scratch/gallery-items.png)

1. Legen Sie das Layout des Katalogs fest, damit nur die Namen der einzelnen Konten angezeigt werden, und konfigurieren Sie die Titelleiste, um das Wort **Durchsuchen** anzuzeigen. Dies wird unter [Customize a gallery (Anpassen eines Katalogs)](customize-layout-sharepoint.md) beschrieben.

    ![Bildschirm zum Durchsuchen](./media/data-platform-create-app-scratch/final-browse.png)

1. Zeigen Sie in der linken Navigationsleiste auf **Screen1**, klicken Sie auf die Auslassungspunkte (...), und klicken Sie anschließend auf **Löschen**.

1. Zeigen Sie in der linken Navigationsleiste auf **Screen2**, klicken Sie auf die Auslassungspunkte (...), und klicken Sie anschließend auf **Umbenennen**.

1. Geben bzw. fügen Sie **BrowseScreen** ein, und benennen Sie den Katalog in dieser Anzeige in **BrowseGallery** um.

    ![Katalog: Bildschirm zum Durchsuchen umbenennen](./media/data-platform-create-app-scratch/rename-browse.png)

## <a name="add-a-form-screen"></a>Hinzufügen eines Formularbildschirm

1. Wiederholen Sie den ersten Schritt des letzten Vorgangs, aber fügen Sie einen **Formularbildschirm** anstelle eines **Listenbildschirms** hinzu.

1. Legen Sie die Formulareigenschaft **DataSource** auf **Konten** und die Eigenschaft **Element** auf **BrowseGallery.Selected** fest. Dies wird auf der Registerkarte **Erweitert** im rechten Bereich angezeigt.

    ![Festlegen der Eigenschaften „Datasource“ und „Item“ des Formulars](./media/data-platform-create-app-scratch/form-datasource.png)

1. Wählen Sie auf der Registerkarte **Eigenschaften** im rechten **Bereich Felder bearbeiten** aus, um den **Bereich Felder** zu öffnen.

1. Klicken Sie auf **Feld hinzufügen**, und aktivieren Sie anschließend die Kontrollkästchen der folgenden Felder:

    - **Kontoname**
    - **Adresse 1: Straße 1**
    - **Adresse 1: Ort**
    - **Adresse 1: Zip/Postleitzahl**
    - **Anzahl der Mitarbeiter**
    - **Jahresumsatz**

    > [!NOTE]
    > Außerhalb dieses Szenarios können Sie ein benutzerdefiniertes Feld erstellen, indem Sie **Neues Feld**auswählen, die erforderlichen Informationen bereitstellen und dann **abgeschlossen**auswählen. Weitere Informationen finden Sie unter [Erstellen eines Felds](../common-data-service/create-edit-field-portal.md#create-a-field).<br><br>![](media/data-platform-create-app-scratch/choose-or-add-fields.png "Select and add a field")

1. Klicken Sie auf **Hinzufügen**.

1. Legen Sie die **Text**-Eigenschaft der Titelleiste auf **Create/Edit** (Erstellen/Bearbeiten) fest.

    Auf dem Bildschirm werden dann die vorgenommenen Änderungen angezeigt.

    ![Festlegen der Eigenschaften „Datasource“ und „Item“ des Formulars](./media/data-platform-create-app-scratch/field-list.png)

1. Bennen Sie diese Anzeige in **FormScreen** um.

## <a name="configure-icons"></a>Konfigurieren von Symbolen

1. Legen Sie unter **BrowseScreen** die Eigenschaft **OnSelect** für den kreisförmigen Pfeil im oberen Bereich des Bildschirms auf die folgende Formel fest:

    `Refresh(Accounts)`

    ![Symbol zum Aktualisieren](./media/data-platform-create-app-scratch/refresh-icon.png)

1. Legen Sie die Eigenschaft **OnSelect** für das Pluszeichen auf die folgende Formel fest:

    `NewForm(EditForm1); Navigate(FormScreen, ScreenTransition.None)`

    ![Symbol „Hinzufügen“](./media/data-platform-create-app-scratch/plus-icon.png)

1. Legen Sie die Eigenschaft **OnSelect** für den ersten Pfeil nach rechts auf die folgende Formel fest:

    `EditForm(EditForm1); Navigate(FormScreen, ScreenTransition.None)`

    ![Symbol „Weiter“](./media/data-platform-create-app-scratch/next-icon.png)

1. Legen Sie unter **FormScreen** die Eigenschaft **OnSelect** für das Symbol „Abbrechen“ auf die folgende Formel fest:

    `ResetForm(EditForm1);Navigate(BrowseScreen, ScreenTransition.None)`

    ![Symbol „Abbrechen“](./media/data-platform-create-app-scratch/cancel-icon.png)

1. Legen Sie die Eigenschaft **OnSelect** für das Häkchensymbol auf die folgende Formel fest:

    `SubmitForm(EditForm1); Navigate(BrowseScreen, ScreenTransition.None)`

    ![Häkchensymbol](./media/data-platform-create-app-scratch/checkmark-icon.png)

1. Wählen Sie auf der Registerkarte **Einfügen** die Option **Symbole** und dann das **Papierkorbsymbol** aus.

1. Legen Sie für das **Papierkorbsymbol** die **Color**-Eigenschaft auf **Weiß** und die **OnSelect**-Eigenschaft auf die folgende Formel fest:

    `Remove(Accounts, BrowseGallery.Selected); Navigate(BrowseScreen, ScreenTransition.None)`

    ![Papierkorbsymbol](./media/data-platform-create-app-scratch/trash-icon.png)

## <a name="test-the-app"></a>Testen der App

1. Klicken Sie in der linken Navigationsleiste auf **BrowseScreen**, und öffnen Sie dann die Vorschau, indem Sie F5 drücken (oder auf das Wiedergabesymbol in der oberen rechten Ecke klicken).

    ![Vorschau öffnen](./media/data-platform-create-app-scratch/open-preview.png)

1. Lassen Sie die Liste abwechselnd in aufsteigender und absteigender Reihenfolge anzeigen, und filtern Sie diese nach einem oder mehreren Zeichen im Kontonamen.

1. Fügen Sie ein Konto hinzu, bearbeiten Sie dieses, und beginnen Sie mit dem Update des Kontos. Verwerfen Sie jedoch Ihre Änderungen, und löschen Sie das Konto.

## <a name="next-steps"></a>Nächste Schritte

- [Verknüpfen Sie diese App mit einer Projektmappe](add-app-solution.md), damit Sie diese beispielsweise in einer anderen Umgebung bereitstellen oder sie auf AppSource veröffentlichen können.
- [Öffnen Sie mindestens eine Beispiel-App](open-and-run-a-sample-app.md), um verschiedene App-Typen zu untersuchen, die Sie erstellen können.
