---
title: 'Hinzufügen, Konfigurieren, Verschieben oder Löschen von Feldern in einem Formular | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 08/26/2019
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

# <a name="add-configure-move-or-delete-fields-on-a-form"></a>Hinzufügen, Konfigurieren, Verschieben oder Löschen von Feldern in einem Formular  
Sie können Felder mithilfe des Formulardesigners hinzufügen, konfigurieren, verschieben oder löschen.

## <a name="add-fields-to-a-form"></a>Hinzufügen von Feldern zu einem Formular
Um Felder zu einem Formular hinzuzufügen, verwenden Sie den Bereich **Felder**. Im Bereich **Felder** können Sie zum schnellen Finden von Feldern filtern und durchsuchen. Sie können sich auch nur nicht verwendete Felder anzeigen lassen. 

> [!div class="mx-imgBorder"] 
>    ![](media/FormDesignerFieldsPane.png "Felder-Bereich")

### <a name="add-fields-to-a-form-using-drag-and-drop"></a>Hinzufügen von Feldern zu einem Formular mithilfe des Ziehens und Ablegens
> [!NOTE]
> Wenn Sie Felder mithilfe des Ziehens und Ablegens hinzufügen oder verschieben, beachten Sie, dass die Formularvorschau reagiert und möglicherweise mehrere Abschnittsspalten als gestapelt rendert. Um sicherzustellen, dass das hinzugefügte oder verschobene Feld in der richtigen Abschnittsspalte ist, legen Sie es oder fügen Sie es verankert in ein anderes Feld ab/ein, das bereits in dieser Abschnittsspalte ist.
1. Öffnen Sie den Formulardesigner, um ein Formular zu erstellen oder zu bearbeiten. Weitere Informationen: [Erstellen von Formularen](create-and-edit-forms.md#create-a-form) oder [Bearbeiten von Formularen](create-and-edit-forms.md#edit-a-form)
2. Wählen Sie in der Befehlsleiste **Feld hinzufügen** oder wählen Sie im linken Bereich **Felder** aus.  Der Bereich **Felder** ist standardmäßig geöffnet, wenn der Formulardesigner geöffnet wird. 
3. Suchen, filtern oder scrollen Sie im Bereich **Felder**, um das Feld zu finden, das Sie hinzufügen möchten. Wenn Sie ein Feld nicht finden können, ist möglicherweise bereits im Formular enthalten. Deaktivieren Sie **Nur unbenutzte Felder anzeigen**, um alle Felder anzuzeigen, auch die, die bereits dem Formular hinzugefügt wurden. 
4. Wählen Sie im Bereich **Felder** ein Feld aus und ziehen Sie es in die Formularvorschau. Wenn Sie das Feld in die Formularvorschau ziehen, sehen Sie Ablageziele, wo Sie das Feld hinzufügen können. 
5. Ziehen Sie das Feld in den gewünschten Speicherort. Beachten Sie Folgendes: 
    - Felder können vor oder hinter einer vorhandenen Komponente bzw. einem vorhandenen Feld abgelegt werden.
    - Felder können auch in den leeren Bereich in einem Abschnitt abgelegt werden. In diesem Fall wird das Feld in einem verfügbaren Bereich hinzugefügt, um die Felder und Komponenten gleichmäßig auf die Abschnittsspalten zu verteilen.
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

## <a name="configure-fields-on-a-form"></a>Konfigurieren von Feldern in einem Formular
Dies sind die verfügbaren Eigenschaften für die Konfiguration eines Felds, wenn Sie ein Formular mithilfe des Formulardesigners erstellen oder bearbeiten.

## <a name="field-properties"></a>Feldeigenschaften

|Fläche  |Name  |Beschreibung  |
|---------|---------|---------|
|**Anzeigeoptionen** | **Feldbeschriftung** | Standardmäßig entspricht die Beschriftung dem Anzeigenamen des Felds. Sie können diesen Namen für das Formular überschreiben, indem Sie hier eine andere Beschriftung eingeben. <br /><br />Diese Eigenschaft ist erforderlich. |
|**Anzeigeoptionen** |  **Feldname** | Der Name des Felds. Dieser kommt von den Feldeigenschaften der Entität und ist schreibgeschützt. |
|**Anzeigeoptionen** | **Beschriftung ausblenden** | Wenn diese Option ausgewählt ist, wird die Feldbeschriftung ausgeblendet. |
|**Anzeigeoptionen** | **Schreibgeschütztes Feld** | Wenn diese Option ausgewählt ist, kann der Feldwert nicht bearbeitet werden. |
|**Anzeigeoptionen** | **Feld sperren** |  Sperren Sie dieses Feld, damit es nicht entfernt werden kann. |
|**Anzeigeoptionen** | **Feld ausblenden** | Wenn diese Option ausgewählt ist, wird das Feld standardmäßig ausgeblendet und kann mithilfe von Code angezeigt werden. |
|**Anzeigeoptionen** | **Auf Telefon ausblenden** | Um eine verkürzte Version dieses Formulars auf Smartphone-Bildschirmen anzuzeigen, können Felder ausgeblendet werden. |
|**Formatierung** | **Feldbreite** |  Wenn der Abschnitt, der die Felder enthält, mehr als eine Spalte enthält, können Sie festlegen, dass das Feld die Anzahl von Spalten belegt, die der Abschnitt enthält. |

## <a name="move-fields-on-a-form"></a>Verschieben von Feldern in einem Formular
Sie können Felder in einem Formular entweder per Drag & Drop oder durch Ausschneiden und Einfügen verschieben. 

### <a name="move-fields-on-a-form-using-drag-and-drop"></a>Verschieben von Feldern in einem Formular mithilfe des Ziehens und Ablegens
1. Öffnen Sie den Formulardesigner, um ein Formular zu erstellen oder zu bearbeiten. Weitere Informationen: [Erstellen von Formularen](create-and-edit-forms.md#create-a-form) oder [Bearbeiten von Formularen](create-and-edit-forms.md#edit-a-form)
2. Wählen Sie in der Formularvorschau das gewünschte Feld aus, und verschieben Sie es per Drag & Drop. Wenn Sie das Feld in die Formularvorschau ziehen, sehen Sie Ablageziele, in die Sie das Feld verschieben können. 
   Beachten Sie Folgendes:
    - Felder können vor oder hinter einer vorhandenen Komponente bzw. einem vorhandenen Feld abgelegt werden.
    - Felder können auch in den leeren Bereich in einem Abschnitt abgelegt werden. In diesem Fall wird das Feld in einem verfügbaren Bereich hinzugefügt, um die Felder und Komponenten gleichmäßig auf die Abschnittsspalten zu verteilen.
    - Durch das Hovern über eine Registerkartenkopfzeile beim Ziehen eines Felds wird die gerade ausgewählte Registerkarte geändert, sodass Sie das Feld zu einer anderen Registerkarte hinzufügen können.   
3. Wiederholen Sie Schritt 2 oben, wenn Sie mehr Felder verschieben möchten.
4. Wählen Sie in der Befehlsleiste **Speichern** aus, um das Formular zu speichern, oder wählen Sie **Veröffentlichen** aus, wenn Sie die Änderungen speichern und für Benutzer sichtbar anzeigen möchten. 

### <a name="move-fields-on-a-form-using-cut-and-paste"></a>Verschieben von Feldern in einem Formular mithilfe von Ausschneiden und Einfügen
1. Öffnen Sie den Formulardesigner, um ein Formular zu erstellen oder zu bearbeiten. Weitere Informationen: [Erstellen von Formularen](create-and-edit-forms.md#create-a-form) oder [Bearbeiten von Formularen](create-and-edit-forms.md#edit-a-form)
2. Wählen Sie in der Formularvorschau das Feld aus, das verschoben werden soll.
3. Wählen Sie in der Befehlsleiste **Ausschneiden** aus.
4. Wählen Sie in der Formularvorschau ein anderes vorhandenes Feld, eine Komponente oder einen Abschnitt aus. Sie können auch zu einer anderen Registerkarte wechseln.
5. Wählen Sie in der Befehlsleiste **Einfügen** oder das Chevron aus, und wählen Sie dann **Einfügen vor** aus.      Beachten Sie Folgendes:
     - Wenn Sie **Einfügen** auswählen, wird das verschobene Feld hinter dem vorhandenen Feld bzw. der Komponente eingefügt. 
     - Wenn Sie **Einfügen vor** auswählen, wird das verschobene Feld vor dem vorhandenen Feld bzw. der Komponente eingefügt.
     - Wenn Sie einen Abschnitt auswählen, wird das verschobene Feld in einem verfügbaren Bereich hinzugefügt, um die Felder und Komponenten gleichmäßig auf die Abschnittsspalten zu verteilen. Die Aktion **Einfügen vor** ist nicht zutreffend und daher in diesem Fall nicht verfügbar.
6. Wiederholen Sie die Schritte 2-5 oben, wenn Sie mehr Felder verschieben möchten.
7. Wählen Sie in der Befehlsleiste **Speichern** aus, um das Formular zu speichern, oder wählen Sie **Veröffentlichen** aus, wenn Sie die Änderungen speichern und für Benutzer sichtbar anzeigen möchten. 

## <a name="delete-fields-on-a-form"></a>Löschen von Feldern in einem Formular
1. Öffnen Sie den Formulardesigner, um ein Formular zu erstellen oder zu bearbeiten. Weitere Informationen: [Erstellen von Formularen](create-and-edit-forms.md#create-a-form) oder [Bearbeiten von Formularen](create-and-edit-forms.md#edit-a-form)
2. Wählen Sie in der Formularvorschau das Feld aus, das Sie aus dem Formular löschen möchten. 
3. Wählen Sie in der Befehlsleiste **Löschen** aus. 
4. Wiederholen Sie die Schritte 2 bis 3, wenn Sie mehr Felder löschen möchten.
5. Wählen Sie in der Befehlsleiste **Speichern** aus, um das Formular zu speichern, oder wählen Sie **Veröffentlichen** aus, wenn Sie die Änderungen speichern und für Benutzer sichtbar anzeigen möchten. 

     > [!NOTE]
     >   -  Wenn Sie ein Feld versehentlich löschen, wählen Sie in der Befehlsleiste **Rückgängig** aus, um das Formular in seinen vorherigen Zustand zurückzusetzen. 
     >   -  Sie können kein Feld löschen, das gesperrt oder erforderlich ist und das nicht irgendwo sonst im Formular vorhanden ist. 

## <a name="create-a-new-field-on-the-entity-when-editing-a-form"></a>Erstellen eines neuen Felds für die Entität bei der Bearbeitung eines Formulars 
1. Öffnen Sie den Formulardesigner, um ein Formular zu erstellen oder zu bearbeiten. Weitere Informationen: [Erstellen von Formularen](create-and-edit-forms.md#create-a-form) oder [Bearbeiten von Formularen](create-and-edit-forms.md#edit-a-form)
2. Wählen Sie in der Befehlsleiste **Feld hinzufügen** oder im linken Bereich **Felder** aus. Der Bereich **Felder** ist standardmäßig geöffnet, wenn der Formulardesigner geöffnet wird. 
3. Wählen Sie im Bereich **Felder** die Option **+ Neues Feld** aus.
4. Geben Sie im Dialogfeld **Neues Feld** den **Anzeigenamen** und **Namen** für das Feld an.
5. Wählen Sie im Dialogfeld **Neues Feld** die Option **Datentyp** aus, und konfigurieren Sie alle weiteren erforderlichen Eigenschaften des Felds.

     > [!NOTE]
     >   -  Einige Feldtypen sind nicht verfügbar, wenn Sie ein Feld im Formulardesigner erstellen. Wenn ein gewünschter Feldtyp nicht verfügbar ist, können Sie die Schritte unter [Erstellen und Bearbeiten von Feldern für Common Data Service mithilfe des PowerApps-Portals](../common-data-service/create-edit-field-portal.md) ausführen.

6. Wählen Sie **Fertig**, um ein neues Feld für die Entität zu erstellen. Das Feld wird im Bereich **Felder** angezeigt.
7. Wenn Sie das neu erstellte Feld zum Formular hinzufügen möchten, führen Sie die Schritte unter [**Hinzufügen von Feldern zu einem Formular**](add-move-or-delete-fields-on-form.md#add-fields-to-a-form) aus.

     > [!NOTE]
     >  Wenn ein Feld für die Entität erstellt wird, ist es nicht auf das aktuelle Formular begrenzt, sondern kann auch an anderen Stellen verwendet werden.

### <a name="see-also"></a>Siehe auch
[Übersicht über den modellgestützten Formulardesigner](form-designer-overview.md)  
[Erstellen, Bearbeiten oder Konfigurieren von Formularen mit dem Formulardesigner](create-and-edit-forms.md)  
[Hinzufügen, Konfigurieren, Verschieben oder Löschen von Komponenten in einem Formular](add-move-configure-or-delete-components-on-form.md)  
[Hinzufügen, Konfigurieren, Verschieben oder Löschen von Abschnitten in einem Formular](add-move-or-delete-sections-on-form.md)  
[Hinzufügen, Konfigurieren, Verschieben oder Löschen von Registerkarten in einem Formular](add-move-or-delete-tabs-on-form.md)  
[Konfigurieren von Kopfzeileneigenschaften im Formulardesigner](form-designer-header-properties.md)  
[Hinzufügen und Konfigurieren einer Unterraster-Komponente in einem Formular](form-designer-add-configure-subgrid.md)  
[Hinzufügen und Konfigurieren einer Schnellansichts-Komponente in einem Formular](form-designer-add-configure-quickview.md)  
[Konfigurieren einer Suchkomponente in einem Formular](form-designer-add-configure-lookup.md)  
[Verwenden der Strukturansicht im Formulardesigner](using-tree-view-on-form.md)  
[Erstellen und Bearbeiten von Feldern](../common-data-service/create-edit-field-portal.md)  
