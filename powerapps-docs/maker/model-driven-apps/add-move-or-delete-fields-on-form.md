---
title: 'Hinzufügen, Verschieben oder Löschen von Feldern in einem Formular | MicrosoftDocs'
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

# <a name="add-move-or-delete-fields-on-a-form"></a>Hinzufügen, Verschieben oder Löschen von Feldern in einem Formular  
[!INCLUDE [cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

Ergänzen, verschieben und entfernen Sie Felder mithilfe des Formulardesigners.

> [!NOTE]
> Wenn Sie Felder mithilfe des Ziehens und Ablegens hinzufügen oder verschieben, beachten Sie, dass die Formularvorschau reagiert und möglicherweise mehrere Abschnittsspalten als gestapelt rendert. Um sicherzustellen, dass das hinzugefügte oder verschobene Feld in der richtigen Abschnittsspalte ist, legen Sie es oder fügen Sie es verankert in ein anderes Feld ab/ein, das bereits in dieser Abschnittsspalte ist.

## <a name="add-fields-to-a-form"></a>Hinzufügen von Feldern zu einem Formular
Um Felder zu einem Formular hinzuzufügen, verwenden Sie den Bereich **Felder**. Im Bereich **Felder** können Sie zum schnellen Finden von Feldern filtern und durchsuchen. Sie können sich auch nur nicht verwendete Felder anzeigen lassen. 

> [!div class="mx-imgBorder"] 
> ![](media/fields-pane.png "Felder-Bereich")

### <a name="add-fields-to-a-form-using-drag-and-drop"></a>Hinzufügen von Feldern zu einem Formular mithilfe des Ziehens und Ablegens

1. Öffnen Sie den Formulardesigner, um ein Formular zu erstellen oder zu bearbeiten. Weitere Informationen: [Erstellen von Formularen](create-and-edit-forms.md#create-a-form) oder [Bearbeiten von Formularen](create-and-edit-forms.md#edit-a-form)
2. Wählen Sie in der Befehlsleiste **Feld hinzufügen** oder wählen Sie im linken Bereich **Felder** aus.  Der Bereich **Felder** ist standardmäßig geöffnet, wenn der Formulardesigner geöffnet wird. 
3. Suchen, filtern oder scrollen Sie im Bereich **Felder**, um das Feld zu finden, das Sie hinzufügen möchten. Wenn Sie ein Feld nicht finden können, ist möglicherweise bereits im Formular enthalten. Deaktivieren Sie **Nur unbenutzte Felder anzeigen**, um alle Felder anzuzeigen, auch die, die bereits dem Formular hinzugefügt wurden. 
4. Wählen Sie im Bereich **Felder** ein Feld aus und ziehen Sie es in die Formularvorschau. Wenn Sie das Feld in die Formularvorschau ziehen, sehen Sie Ablageziele, wo Sie das Feld hinzufügen können. 
5. Ziehen Sie das Feld in den gewünschten Speicherort. Beachten Sie Folgendes: 
    - Felder können vor oder hinter einem vorhandenen Feld abgelegt werden.
    - Felder können auch in den leeren Bereich in einem Abschnitt abgelegt werden. In diesem Fall wird das Feld in einem verfügbaren Bereich hinzugefügt, um die Felder gleichmäßig auf die Abschnittsspalten zu verteilen.
    - Durch das Hovern über eine Registerkartenkopfzeile beim Ziehen eines Felds wird die gerade ausgewählte Registerkarte geändert, sodass Sie das Feld zu einer anderen Registerkarte hinzufügen können.   
6. Wiederholen Sie die Schritte 3-5 oben, wenn Sie mehr Felder hinzufügen möchten.
7. Wählen Sie in der Befehlsleiste **Speichern** aus, um das Formular zu speichern, oder wählen Sie **Veröffentlichen** aus, wenn Sie die Änderungen speichern und für Benutzer sichtbar anzeigen möchten. 

### <a name="add-fields-to-a-form-using-selection"></a>Hinzufügen von Feldern zu einem Formular mithilfe der Auswahl 

1. Öffnen Sie den Formulardesigner, um ein Formular zu erstellen oder zu bearbeiten. Weitere Informationen: [Erstellen von Formularen](create-and-edit-forms.md#create-a-form) oder [Bearbeiten von Formularen](create-and-edit-forms.md#edit-a-form)
2. Wählen Sie in der Formularvorschau ein anderes vorhandenes Feld oder einen Abschnitt aus. Beachten Sie Folgendes:
    - Wenn Sie ein bestehendes Feld auswählen, wird das neue Feld hinter dem bestehenden Feld hinzugefügt. 
    - Wenn Sie einen Abschnitt auswählen, wird das neue Feld in einem verfügbaren Bereich hinzugefügt, um die Felder gleichmäßig auf die Abschnittsspalten zu verteilen. 
3. Wählen Sie in der Befehlsleiste **Feld hinzufügen** oder wählen Sie im linken Bereich **Felder** aus. Der Bereich **Felder** ist standardmäßig geöffnet, wenn der Formulardesigner geöffnet wird. 
4. Suchen, filtern oder scrollen Sie im Bereich **Felder**, um das Feld zu finden, das Sie hinzufügen möchten. Wenn Sie ein Feld nicht finden können, ist möglicherweise bereits im Formular enthalten. Deaktivieren Sie **Nur unbenutzte Felder anzeigen**, um alle Felder anzuzeigen, auch die, die bereits dem Formular hinzugefügt wurden. 
5. Wählen Sie im Bereich **Felder** ein Feld aus, um es dem Formular hinzuzufügen. Alternativ können Sie **...** neben dem gewünschten Feld auswählen und dann **Zum ausgewählten Abschnitt hinzufügen** klicken. 
6. Wiederholen Sie die Schritte 2-5 oben, wenn Sie mehr Felder hinzufügen möchten.
7. Wählen Sie in der Befehlsleiste **Speichern** aus, um das Formular zu speichern, oder wählen Sie **Veröffentlichen** aus, wenn Sie die Änderungen speichern und für Benutzer sichtbar anzeigen möchten. 

## <a name="move-fields-on-a-form"></a>Verschieben von Feldern in einem Formular

### <a name="move-fields-on-a-form-using-drag-and-drop"></a>Verschieben von Feldern in einem Formular mithilfe des Ziehens und Ablegens

1. Öffnen Sie den Formulardesigner, um ein Formular zu erstellen oder zu bearbeiten. Weitere Informationen: [Erstellen von Formularen](create-and-edit-forms.md#create-a-form) oder [Bearbeiten von Formularen](create-and-edit-forms.md#edit-a-form)
2. Wählen Sie in der Formularvorschau das Feld aus, das Sie verschieben möchten, und starten Sie die Ziehaktion. Wenn Sie das Feld in die Formularvorschau ziehen, sehen Sie Ablageziele, in die Sie das Feld verschieben können. 
3. Ziehen Sie das Feld in den gewünschten Speicherort. Beachten Sie Folgendes: 
    - Felder können vor oder hinter einem vorhandenen Feld abgelegt werden.
    - Felder können auch in den leeren Bereich in einem Abschnitt abgelegt werden. In diesem Fall wird das Feld in einem verfügbaren Bereich hinzugefügt, um die Felder gleichmäßig auf die Abschnittsspalten zu verteilen.
    - Durch das Hovern über eine Registerkartenkopfzeile beim Ziehen eines Felds wird die gerade ausgewählte Registerkarte geändert, sodass Sie das Feld zu einer anderen Registerkarte hinzufügen können.   
4. Wiederholen Sie die Schritte 2-3 oben, wenn Sie mehr Felder verschieben möchten.
5. Wählen Sie in der Befehlsleiste **Speichern** aus, um das Formular zu speichern, oder wählen Sie **Veröffentlichen** aus, wenn Sie die Änderungen speichern und für Benutzer sichtbar anzeigen möchten. 

    > [!NOTE]
    >   Das Verschieben von Feldern in Kopf- und Fußzeilen mithilfe des Ziehens und Ablegens wird noch nicht unterstützt. 

### <a name="move-fields-on-a-form-using-cut-and-paste"></a>Verschieben von Feldern in einem Formular mithilfe von Ausschneiden und Einfügen

1. Öffnen Sie den Formulardesigner, um ein Formular zu erstellen oder zu bearbeiten. Weitere Informationen: [Erstellen von Formularen](create-and-edit-forms.md#create-a-form) oder [Bearbeiten von Formularen](create-and-edit-forms.md#edit-a-form)
2. Wählen Sie in der Formularvorschau das Feld aus, das verschoben werden soll.
3. Wählen Sie in der Befehlsleiste **Ausschneiden** aus.
4. Wählen Sie in der Formularvorschau ein anderes vorhandenes Feld oder einen Abschnitt aus. Sie können auch zu einer anderen Registerkarte wechseln.
5. Wählen Sie in der Befehlsleiste **Einfügen** oder das Chevron aus, und wählen Sie dann **Einfügen vor** aus. Beachten Sie Folgendes:
    - Wenn Sie **Einfügen** auswählen, wird das verschobene Feld hinter dem vorhandenen Feld eingefügt. 
    - Wenn Sie **Einfügen vor** auswählen, wird das verschobene Feld vor dem vorhandenen Feld eingefügt.
    - Wenn Sie einen Abschnitt auswählen, wird das verschobene Feld in einem verfügbaren Bereich hinzugefügt, um die Felder gleichmäßig auf die Abschnittsspalten zu verteilen. Die Aktion **Einfügen vor** ist nicht zutreffend und daher in diesem Fall nicht verfügbar.
6. Wiederholen Sie die Schritte 2-5 oben, wenn Sie mehr Felder verschieben möchten.
7. Wählen Sie in der Befehlsleiste **Speichern** aus, um das Formular zu speichern, oder wählen Sie **Veröffentlichen** aus, wenn Sie die Änderungen speichern und für Benutzer sichtbar anzeigen möchten. 

## <a name="delete-fields-on-a-form"></a>Löschen von Feldern in einem Formular
1. Öffnen Sie den Formulardesigner, um ein Formular zu erstellen oder zu bearbeiten. Weitere Informationen: [Erstellen von Formularen](create-and-edit-forms.md#create-a-form) oder [Bearbeiten von Formularen](create-and-edit-forms.md#edit-a-form)
2. Wählen Sie in der Formularvorschau das Feld aus, das Sie aus dem Formular löschen möchten. 
3. Wählen Sie in der Befehlsleiste **Löschen** aus. 
4. Wiederholen Sie die Schritte 2-3 oben, wenn Sie mehr Felder löschen möchten.
5. Wählen Sie in der Befehlsleiste **Speichern** aus, um das Formular zu speichern, oder wählen Sie **Veröffentlichen** aus, wenn Sie die Änderungen speichern und für Benutzer sichtbar anzeigen möchten. 

     > [!NOTE]
     >   -  Wenn Sie ein Feld versehentlich löschen, wählen Sie in der Befehlsleiste **Rückgängig** aus, um das Formular in seinen vorherigen Zustand zurückzusetzen. 
     >   -  Sie können ein erforderliches oder gesperrtes Feld nicht löschen. 

### <a name="see-also"></a>Siehe auch
[Übersicht über den modellgestützten Formulardesigner](form-designer-overview.md)  
[Erstellen oder Bearbeiten von Formularen mit dem Formulardesigner](create-and-edit-forms.md)  
[Hinzufügen, Verschieben oder Löschen von Abschnitten in einem Formular mithilfe des Formulardesigners](add-move-or-delete-sections-on-form.md)  
[Hinzufügen, Verschieben oder Löschen von Registerkarten in einem Formular mithilfe des Formulardesigners](add-move-or-delete-tabs-on-form.md)  
[Im Formulardesigner verfügbare Eigenschaften](form-designer-properties.md)  
[Konfigurieren von Kopfzeileneigenschaften im Formulardesigner](form-designer-header-properties.md)  
[Verwenden der Strukturansicht im Formulardesigner](using-tree-view-on-form.md)  
[Erstellen und Bearbeiten von Feldern](../common-data-service/create-edit-field-portal.md)
