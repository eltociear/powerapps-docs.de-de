---
title: 'Hinzufügen, Verschieben oder Löschen von Abschnitten in einem Formular mithilfe des Formulardesigners | MicrosoftDocs'
ms.custom: ''
ms.date: 04/21/2019
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
  - PowerApps maker portal impact
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="add-move-or-delete-sections-on-a-form"></a>Hinzufügen, Verschieben oder Löschen von Abschnitten in einem Formular 
[!INCLUDE [cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

Ergänzen, verschieben oder löschen Sie Abschnitte in einem Formular mithilfe des Formulardesigners. 

> [!NOTE]
> Wenn Sie Abschnitte mithilfe des Ziehens und Ablegens hinzufügen oder verschieben, beachten Sie, dass die Formularvorschau reagiert und möglicherweise mehrere Registerkartenspalten als gestapelt rendert. Um sicherzustellen, dass der hinzugefügte oder verschobene Abschnitt in der richtigen Registerkartenspalte ist, legen Sie ihn oder fügen Sie ihn verankert in einen anderen Abschnitt ab/ein, der bereits in dieser Registerkartenspalte ist.

## <a name="add-sections-to-a-form"></a>Hinzufügen von Abschnitten zu einem Formular
Um Abschnitte zu einem Formular hinzuzufügen, verwenden Sie den Bereich **Layouts**. 

> [!div class="mx-imgBorder"] 
> ![](media/layouts-pane.png "Layout-Bereich")

  > [!NOTE]
  >   Abschnitte können nur in Hauptformularen und Schnellansichtsformularen hinzugefügt werden. Weitere Informationen: [Formulartypen](types-forms.md)

### <a name="add-sections-to-a-form-using-drag-and-drop"></a>Hinzufügen von Abschnitten zu einem Formular mithilfe des Ziehens und Ablegens

1. Öffnen Sie den Formulardesigner, um ein Formular zu erstellen oder zu bearbeiten. Weitere Informationen: [Erstellen von Formularen](create-and-edit-forms.md#create-a-form) oder [Bearbeiten von Formularen](create-and-edit-forms.md#edit-a-form)
2. Wählen Sie in der Befehlsleiste **Steuerelement hinzufügen** oder wählen Sie im linken Bereich **Layouts** aus. 
3. Wählen Sie im Bereich **Layouts** ein Abschnittsteuerelement aus und ziehen Sie es in die Formularvorschau. Wenn Sie den Abschnitt in die Formularvorschau ziehen, sehen Sie Ablageziele, wo Sie den Abschnitt hinzufügen können. 
4. Ziehen Sie den Abschnitt in den gewünschten Speicherort. Beachten Sie Folgendes: 
    - Abschnitte können vor oder hinter einem vorhandenen Abschnitt abgelegt werden.
    - Abschnitte können auch im leeren Bereich in einer Registerkarte abgelegt werden. In diesem Fall wird der Abschnitt in einem verfügbaren Bereich hinzugefügt, um die Abschnitte gleichmäßig auf die Registerkartenspalten zu verteilen.
    - Durch das Hovern über eine Registerkartenkopfzeile beim Ziehen eines Abschnitts wird die gerade ausgewählte Registerkarte geändert, sodass Sie den Abschnitt zu einer anderen Registerkarte hinzufügen können.   
5. Wiederholen Sie die Schritte 3-4 oben, wenn Sie mehr Abschnitte hinzufügen möchten.
6. Wählen Sie in der Befehlsleiste **Speichern** aus, um das Formular zu speichern, oder wählen Sie **Veröffentlichen** aus, wenn Sie die Änderungen speichern und für Benutzer sichtbar anzeigen möchten. 

### <a name="add-sections-to-a-form-using-selection"></a>Hinzufügen von Abschnitten zu einem Formular mithilfe der Auswahl 

1. Öffnen Sie den Formulardesigner, um ein Formular zu erstellen oder zu bearbeiten. Weitere Informationen: [Erstellen von Formularen](create-and-edit-forms.md#create-a-form) oder [Bearbeiten von Formularen](create-and-edit-forms.md#edit-a-form)
2. Wählen Sie in der Formularvorschau einen anderen vorhandenen Abschnitt oder Registerkarte aus. Beachten Sie Folgendes:
    - Wenn Sie einen bestehenden Abschnitt auswählen, wird der neue Abschnitt hinter dem bestehenden Abschnitt hinzugefügt. 
    - Wenn Sie eine Registerkarte auswählen, wird der neue Abschnitt in einem verfügbaren Bereich hinzugefügt, um die Abschnitte gleichmäßig auf die Registerkartenspalten zu verteilen. 
3. Wählen Sie in der Befehlsleiste **Steuerelement hinzufügen** oder wählen Sie im linken Bereich **Layouts** aus.  
4. Wählen Sie im Bereich **Layouts** ein Abschnittsteuerelement aus, um es dem Formular hinzuzufügen. Alternativ können Sie **...** neben dem gewünschten Abschnittsteuerelement auswählen und dann **Zur ausgewählten Registerkarte hinzufügen** klicken. 
5. Wiederholen Sie die Schritte 2-4 oben, wenn Sie mehr Abschnitte hinzufügen möchten.
6. Wählen Sie in der Befehlsleiste **Speichern** aus, um das Formular zu speichern, oder wählen Sie **Veröffentlichen** aus, wenn Sie die Änderungen speichern und für Benutzer sichtbar anzeigen möchten. 

## <a name="move-sections-on-a-form"></a>Verschieben von Abschnitten in einem Formular

### <a name="move-sections-on-a-form-using-drag-and-drop"></a>Verschieben von Abschnitten in einem Formular mithilfe des Ziehens und Ablegens

1. Öffnen Sie den Formulardesigner, um ein Formular zu erstellen oder zu bearbeiten. Weitere Informationen: [Erstellen von Formularen](create-and-edit-forms.md#create-a-form) oder [Bearbeiten von Formularen](create-and-edit-forms.md#edit-a-form)
2. Wählen Sie in der Formularvorschau die Abschnittsbeschriftung oder leere Fläche in dem Abschnitt aus, den Sie verschieben möchten, und starten Sie die Ziehaktion. Wenn Sie den Abschnitt in die Formularvorschau ziehen, sehen Sie Ablageziele, in die Sie den Abschnitt verschieben können. 
3. Ziehen Sie den Abschnitt in den gewünschten Speicherort. Beachten Sie Folgendes: 
    - Abschnitte können vor oder hinter einem vorhandenen Abschnitt abgelegt werden.
    - Abschnitte können auch im leeren Bereich in einer Registerkarte abgelegt werden. In diesem Fall wird der Abschnitt in einem verfügbaren Bereich hinzugefügt, um die Abschnitte gleichmäßig auf die Registerkartenspalten zu verteilen.
    - Durch das Hovern über eine Registerkartenkopfzeile beim Ziehen eines Abschnitts wird die gerade ausgewählte Registerkarte geändert, sodass Sie den Abschnitt zu einer anderen Registerkarte hinzufügen können.   
4. Wiederholen Sie die Schritte 2-3 oben, wenn Sie mehr Abschnitte verschieben möchten.
5. Wählen Sie in der Befehlsleiste **Speichern** aus, um das Formular zu speichern, oder wählen Sie **Veröffentlichen** aus, wenn Sie die Änderungen speichern und für Benutzer sichtbar anzeigen möchten. 

### <a name="move-sections-on-a-form-using-cut-and-paste"></a>Verschieben von Abschnitten in einem Formular mithilfe von Ausschneiden und Einfügen

1. Öffnen Sie den Formulardesigner, um ein Formular zu erstellen oder zu bearbeiten. Weitere Informationen: [Erstellen von Formularen](create-and-edit-forms.md#create-a-form) oder [Bearbeiten von Formularen](create-and-edit-forms.md#edit-a-form)
2. Wählen Sie in der Formularvorschau den Abschnitt aus, das verschoben werden soll.
3. Wählen Sie in der Befehlsleiste **Ausschneiden** aus.
4. Wählen Sie in der Formularvorschau einen anderen vorhandenen Abschnitt oder Registerkarte aus. Sie können auch zu einer anderen Registerkarte wechseln.
5. Wählen Sie in der Befehlsleiste **Einfügen** oder das Chevron aus, und wählen Sie dann **Einfügen vor** aus. Beachten Sie Folgendes: 
    - Wenn Sie **Einfügen** auswählen, wird der verschobene Abschnitt hinter dem vorhandenen Abschnitt eingefügt. 
    - Wenn Sie **Einfügen vor** auswählen, wird der verschobene Abschnitt vor dem vorhandenen Abschnitt eingefügt.
    - Wenn Sie eine Registerkarte auswählen, wird der verschobene Abschnitt in einem verfügbaren Bereich hinzugefügt, um die Abschnitte gleichmäßig auf die Registerkartenspalten zu verteilen. Die Aktion **Einfügen vor** ist nicht zutreffend und daher in diesem Fall nicht verfügbar.
6. Wiederholen Sie die Schritte 2-5 oben, wenn Sie mehr Abschnitte verschieben möchten.
7. Wählen Sie in der Befehlsleiste **Speichern** aus, um das Formular zu speichern, oder wählen Sie **Veröffentlichen** aus, wenn Sie die Änderungen speichern und für Benutzer sichtbar anzeigen möchten. 

## <a name="delete-sections-on-a-form"></a>Löschen von Abschnitten in einem Formular
1. Öffnen Sie den Formulardesigner, um ein Formular zu erstellen oder zu bearbeiten. Weitere Informationen: [Erstellen von Formularen](create-and-edit-forms.md#create-a-form) oder [Bearbeiten von Formularen](create-and-edit-forms.md#edit-a-form)
2. Wählen Sie in der Formularvorschau den Abschnitt aus, den Sie aus dem Formular löschen möchten. 
3. Wählen Sie in der Befehlsleiste **Löschen** aus.
4. Wiederholen Sie die Schritte 2-3 oben, wenn Sie mehr Abschnitte löschen möchten.
4. Wählen Sie in der Befehlsleiste **Speichern** aus, um das Formular zu speichern, oder wählen Sie **Veröffentlichen** aus, wenn Sie die Änderungen speichern und für Benutzer sichtbar anzeigen möchten. 

    > [!NOTE]
    >   - Abschnitte können nur in Hauptformularen und Schnellansichtsformularen gelöscht werden. Weitere Informationen: [Formulartypen](types-forms.md)
    >   - Wenn Sie einen Abschnitt versehentlich löschen, wählen Sie in der Befehlsleiste **Rückgängig** aus, um das Formular in seinen vorherigen Zustand zurückzusetzen. 
    >   - Sie können einen Abschnitt nicht löschen, der benötigte oder gesperrte Felder enthält. 
    >   - Sie können keinen gesperrten Abschnitt löschen. 
    >   - Eine Registerkarte muss mindestens einen Abschnitt in jeder Registerkartenspalte haben. Wenn Sie den letzten verbleibenden Abschnitt in einer Registerkartenspalte löschen, wird ein neuer Abschnitt automatisch hinzugefügt. 

### <a name="see-also"></a>Siehe auch
[Übersicht über den modellgestützten Formulardesigner](form-designer-overview.md)  
[Erstellen oder Bearbeiten von Formularen mit dem Formulardesigner](create-and-edit-forms.md)  
[Ergänzen, Verschieben oder Löschen von Feldern in einem Formular mithilfe des Formulardesigners](add-move-or-delete-fields-on-form.md)  
[Hinzufügen, Verschieben oder Löschen von Registerkarten in einem Formular mithilfe des Formulardesigners](add-move-or-delete-tabs-on-form.md)  
[Im Formulardesigner verfügbare Eigenschaften](form-designer-properties.md)  
[Verwenden der Strukturansicht im Formulardesigner](using-tree-view-on-form.md)  
[Erstellen und Bearbeiten von Feldern](../common-data-service/create-edit-field-portal.md) 
