---
title: Hinzufügen einer eingebetteten Canvas-App in einem modellgesteuerten Formular | MicrosoftDocs
ms.custom: ''
ms.date: 06/25/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- PowerApps
author: Aneesmsft
ms.author: matp
manager: kvivek
tags:
- Power Apps maker portal impact
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: d229edaec03642c594eb8057927fcf44beadf7c5
ms.sourcegitcommit: 861ba8e719fa16899d14e4a628f9087b47206993
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2019
ms.locfileid: "2872779"
---
# <a name="add-an-embedded-canvas-app-on-a-model-driven-form"></a>Hinzufügen einer eingebetteten Canvas-App in einem modellgesteuerten Formular
In diesem Artikel wird erläutert, wie Sie eine neue Canvas-App in einem modellgesteuerten Formular einbetten.

Stellen Sie sich vor, dass Sie eine neue Canvas-App erstellen und sie in einem Hauptformular für die Entität „Firmen” einbetten möchten. Gehen Sie dazu wie folgt vor: 

1.  Melden Sie sich bei [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an.
2.  [Erstellen oder Bearbeiten des Hauptformulars](create-and-edit-forms.md) einer Entität, Entität „Firmen” in unserem Beispiel. 
3.  Wählen Sie in der Befehlsleiste **In klassischen Modus wechseln**, um das Formular im klassischen Formular-Designer zu öffnen.
4.  Wählen Sie im klassischen Formular-Designer den Abschnitt auf dem Formular aus, in dem die eingebettete Canvas-App angezeigt werden soll.
5.  Fügen Sie im Feldbereich ein Pflichtfeld hinzu, z. B. **Firmenname**.
      > [!IMPORTANT]
      > Verwenden Sie immer ein Pflichtfeld, das garantiert einen Wert hat. Wenn Ihr Feld keinen Wert hat, wird Ihre eingebettete Canvas-App nicht aktualisiert, wenn sich die Daten auf dem Hostmodell-basierten Formular ändern.
6.  Wenn das Feld ausgewählt ist, wählen Sie auf der Registerkarte **Start** in der Gruppe **Bearbeiten** die Option **Eigenschaften ändern**.
7.  Wählen Sie im Dialogfeld **Feldeigenschaften** die **Steuerelemente**-Registerkarte aus.
8.  Wählen Sie auf der Registerkarte **Steuerelemente** die Option **Steuerelement hinzufügen** aus.
9.  Wählen Sie im Dialogfeld **Steuerelement hinzufügen** in der Liste der verfügbarer Steuerelemente **Canvas-App** und dann **Hinzufügen** aus.
10. Wählen Sie im Dialogfeld **Feldeigenschaften** in der Liste der Steuerelemente die Option **Canvas-App** und wählen Sie dann die Option **Web** aus.
11. Im Abschnitt unter der Steuerelementliste wird die Liste der Eigenschaften angezeigt, die für das Canvas-App-Steuerelement verfügbar sind.
     - Die Eigenschaft **Entitätsname** gibt die Entität an, die die Daten an Ihre eingebettete Canvas-App liefert. Sie wird auf die Entität festgelegt, die das Feld enthält, das Sie in einem früheren Schritt hinzugefügt haben.
         - Beachten Sie, dass, obwohl diese Eigenschaft veränderbar erscheint, die Änderung keinen Einfluss auf die eingebettete Canvas-App hat. Sie soll lediglich als Referenz für Siedienen.
     - Die Eigenschaft **App ID** gibt die ID der eingebetteten Canvas-App an. Sie wird bei Erstellung der Canvas-App automatisch generiert und eingetragen.
         - Beachten Sie, dass jede Änderung des Wertes **App ID** die Verknüpfung von dem modellgestützten Formular zur eingebetteten Canvas-App unterbricht.
12. Zum Erstellen oder Bearbeiten Ihrer Canvas-App wählen Sie **Anpassen** aus: Dadurch wird Power Apps Studio in einer neuen Registerkarte geöffnet.
       > [!NOTE]
       > Wenn das Öffnen von Power Apps Studio aufgrund eines Popupblockers des Webbrowsers blockiert ist, müssen Sie die Website make.powerapps.com aktivieren oder den Popupblocker vorübergehend deaktivieren und dann erneut **Anpassen** auswählen.
13. Beachten Sie in Power Apps Studio, dass sich im linken Bereich ein spezielles **ModelDrivenFormIntegration**-Steuerelement befindet. Dieses Steuerelement ist dafür verantwortlich, Kontextdaten aus dem Hostmodell-basierten Formular in die eingebettete Canvas-App zu bringen.
14. Achten Sie darauf, ob ein [Canvas-App-Formularsteuerelement](../canvas-apps/controls/control-form-detail.md) automatisch zu Ihrer eingebetteten Canvas-App hinzugefügt wurde und die vom modellgesteuerten Hostformular über das ModelDrivenFormIntegration-Steuerelement weitergegebenen Daten angezeigt werden. 
15. Wählen Sie die Registerkarte **Ansicht** und dann **Datenquellen** aus. Beachten Sie, dass eine Datenquelle für die übergeordnete Entität Ihres modellgesteuerten Hostformulars, „Firmen” in diesem Fall, automatisch zu Ihrer eingebetteten Canvas-App hinzugefügt wurde.
16. Wählen Sie das Steuerelement **Form1** und achten Sie darauf, dass die Eigenschaft **Datenquelle** auf **Firmen** gesetzt ist.
17. Wenn das Steuerelement **Form1** weiterhin ausgewählt ist, achten Sie darauf, dass die Eigenschaft **Element** auf **ModelDrivenFormIntegration.Item** gesetzt ist.
    > [!NOTE]
    > Die eingebettete Canvas-App hat vom modellgesteuerten Hostformular über ModelDrivenFormIntegration.Item vollen Zugriff auf den Datensatz. Wenn Sie beispielsweise den Wert eines Felds mit dem Namen **AccountNumber** und den Anzeigenamen **Firmennummer** abrufen möchten, können Sie **ModelDrivenFormIntegration.Item.accountnumber** oder **ModelDrivenFormIntegration.Item.'Account Number'** verwenden.
18. Wählen Sie im Eigenschaftenbereich rechts neben **Felder** die Option **Felder bearbeiten** aus.
19. Wählen Sie **+ Feld hinzufügen**, um dem Canvas-App-Formular ein weiteres Feld hinzuzufügen oder vorhandene Felder per Drag & Drop neu anzuordnen. Schließen Sie den Datenbereich, wenn Sie mit dem Hinzufügen und der Neuanordnung von Feldern fertig sind.
20. Wählen Sie die Registerkarte **Datei**, und dann **Speichern** aus.
21. Wählen Sie die Registerkarte **Die Cloud**. Geben Sie der App einen eindeutigen Namen und wählen Sie dann **Speichern**, unten rechts. Beachten Sie Folgendes: 
    -  Wenn Sie eine App zum ersten mal speichern, wird die App automatisch veröffentlicht.
      -  Bei späterem Speichern, wählen Sie **Veröffentlichen** und dann **Diese Version veröffentlichen**, um Ihre Änderungen zur Verfügung stellen.
22. Klicken Sie im Menü auf **Zurück**.
23. Wählen Sie die Browserregisterkarte aus, bei der der klassische Formular-Designer geöffnet ist. Beachten Sie, dass die Eigenschaft **App ID** des Canvas-App-Steuerelements nun einen automatisch ausgefüllten Wert hat.
    > [!NOTE]
    > - Der Formular-Designer verfügt über eine direkte Verbindung zu Power Apps Studio, das in einem früheren Schritt in einer anderen Browserregisterkarte geöffnet wurde.
    > - Der Formular-Designer wartet darauf, dass die App-ID an ihn gesendet wird. 
    > - Die App-ID wird zum Formular-Designer gesendet, wenn die App gespeichert wird.
24. Wählen Sie im Dialogfeld **Feldeigenschaften** die **Anzeige**-Registerkarte aus.
25. Löschen Sie **Beschriftung anzeigen** auf dem Formular und wählen Sie dann **OK**.
    -   Wenn Sie bereits eine Canvas-App in dieses Formular eingebettet haben, wird eine Meldung angezeigt, "Nur eine Canvas-App kann in einem Formular aktiviert werden". Wenn Sie die neue Canvas-App hinzufügen, müssen Sie zuerst [die aktuelle eingebettete Canvas-App deaktivieren](embedded-canvas-app-guidelines.md#disable-an-embedded-canvas-app). Anschließend [aktivieren Sie die neue eingebettete Canvas-App](embedded-canvas-app-guidelines.md#enable-an-embedded-canvas-app).
26. Wählen Sie auf der Registerkarte **Start** **Speichern** und dann **Veröffentlichen** aus.

Nachdem Sie eine eingebettete Canvas-App zu Ihrem modellgestützten Formular hinzugefügt haben, teilen Sie Ihre eingebettete Canvas-App mit anderen Benutzern. Weitere Informationen: [Teilen einer eingebetteten Canvas-App](share-embedded-canvas-app.md).

Wenn Benutzer eine modellgestützte App (nur Einheitliche Oberfläche) öffnen, die das von Ihnen geänderte Formular enthält, sehen sie die eingebettete Canvas-App auf dem Formular. Wenn Sie den Datensatz ändern, der auf dem Hauptformular angezeigt wird, ändert sich der Datenkontext, der an das Formular übergeben wird, und die eingebettete App wird aktualisiert, um die relevanten Daten anzuzeigen.

In diesem Thema erfahren Sie, wie Sie mit der Einbettung einer Canvas-App in einem modellgestützen Formular beginnen. Sie können die eingebettete Canvas-App weiter anpassen, um Daten aus einer Vielzahl von Datenquellen zu verbinden und einzubringen. Verwenden Sie die Funktionen Filter, Suche und LookUp und den vom Hostmodell-basierten Formular übergebenen Kontext, um bestimmte Datensätze in diesen Datenquellen zu filtern oder zu finden. Verwenden Sie den WYSIWYG-Canvas-App-Editor, um einfach die Benutzeroberfläche zu entwerfen, die Ihren Anforderungen entspricht.

## <a name="see-also"></a>Siehe auch
[Einbetten einer Canvas-App in einem modellgesteuerten Formular](embed-canvas-app-in-form.md) <br />
[Bearbeiten einer Canvas-App, die in einem modellgesteuerten Formular eingebettet ist](embedded-canvas-app-edit-classic-designer.md) <br />
[Anpassen der Bildschirmgröße und Ausrichtung einer Canvas-App, die in einem modellgesteuerten Formular eingebettet ist](embedded-canvas-app-customize-screen.md) <br />
[Führen Sie vordefinierte Aktionen aus einer eingebetteten Canvas-App auf dem Hostformular aus](embedded-canvas-app-actions.md) <br />
[Eigenschaften und Aktionen des ModelDrivenFormIntegration-Steuerelements](embedded-canvas-app-properties-actions.md) <br />
[Teilen einer eingebetteten Canvas-App](share-embedded-canvas-app.md) <br />
[Richtlinien zum Arbeiten mit eingebetteten Canvas-Apps](embedded-canvas-app-guidelines.md) <br />
[Migrieren von eingebetteten Canvas-Apps in modellgesteuerten Formularen, die mithilfe der öffentlichen Vorschauversion als die neueste Version erstellt wurden](embedded-canvas-app-migrate-from-preview.md) <br />
