---
title: 'Hinzufügen, Konfigurieren, Verschieben oder Löschen von Registerkarten in einem Formular mithilfe des Formulardesigners | Microsoft-Dokumentation'
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

# <a name="add-configure-move-or-delete-tabs-on-a-form"></a>Hinzufügen, Konfigurieren, Verschieben oder Löschen von Registerkarten in einem Formular  
Ergänzen, verschieben oder löschen Sie Registerkarten in einem Formular mithilfe des Formulardesigners.

## <a name="add-tabs-to-a-form"></a>Hinzufügen von Registerkarten zu einem Formular
Um Registerkarten zu einem Formular hinzuzufügen, verwenden Sie den Bereich **Komponenten**.  

> [!div class="mx-imgBorder"] 
> ![](media/FormDesignerComponentsLayout.png "Layoutkomponenten")
   
  > [!NOTE]
  >  Registerkarten können nur in Hauptformularen hinzugefügt werden. Weitere Informationen: [Formulartypen](types-forms.md)

### <a name="add-tabs-to-a-form-using-drag-and-drop"></a>Hinzufügen von Registerkarten zu einem Formular mithilfe des Ziehens und Ablegens
1. Öffnen Sie den Formulardesigner, um ein Formular zu erstellen oder zu bearbeiten. Weitere Informationen: [Erstellen von Formularen](create-and-edit-forms.md#create-a-form) oder [Bearbeiten von Formularen](create-and-edit-forms.md#edit-a-form)
2. Wählen Sie in der Befehlsleiste **Komponente hinzufügen** oder im linken Bereich **Komponenten** aus. 
3. Wählen Sie im Bereich **Komponenten** eine Registerkartenkomponente aus, und ziehen Sie sie in die Formularvorschau.     Wenn Sie die Registerkarte in die Formularvorschau ziehen, sehen Sie Ablageziele, wo Sie die Registerkarte hinzufügen können. Beachten Sie Folgendes: 
    - Registerkarten können vor oder hinter vorhandenen Registerkarten abgelegt werden, indem Sie die Maus über die Registerkartenkopfzeilen bewegen.
    - Registerkarten können auch vor oder hinter der aktuellen Registerkarte abgelegt werden, indem Sie die Maus über den linken oder rechten Rand der aktuellen Registerkarte bewegen.
4. Wiederholen Sie Schritt 3 oben, wenn Sie mehr Registerkarten hinzufügen möchten.
5. Wählen Sie in der Befehlsleiste **Speichern** aus, um das Formular zu speichern, oder wählen Sie **Veröffentlichen** aus, wenn Sie die Änderungen speichern und für Benutzer sichtbar anzeigen möchten. 

### <a name="add-tabs-to-a-form-using-selection"></a>Hinzufügen von Registerkarten zu einem Formular mithilfe der Auswahl 
1. Öffnen Sie den Formulardesigner, um ein Formular zu erstellen oder zu bearbeiten. Weitere Informationen: [Erstellen von Formularen](create-and-edit-forms.md#create-a-form) oder [Bearbeiten von Formularen](create-and-edit-forms.md#edit-a-form)
2. Wählen Sie in der Formularvorschau eine andere vorhandene Registerkarte oder das Formular aus. Beachten Sie Folgendes:
    - Wenn Sie eine vorhandene Registerkarte auswählen, wird die neue Registerkarte hinter der bestehenden Registerkarte hinzugefügt. 
    - Wenn Sie das Formular auswählen, wird die neue Registerkarte als die letzte Registerkarte im Formular hinzugefügt. 
3. Wählen Sie in der Befehlsleiste **Komponente hinzufügen** oder im linken Bereich **Komponenten** aus.  
4. Wählen Sie im Bereich **Komponenten** eine Registerkartenkomponente aus, um sie dem Formular hinzuzufügen. Alternativ können Sie **...** neben der gewünschten Registerkartenkomponente auswählen und dann **Zum Formular hinzufügen** klicken. 
5. Wiederholen Sie die Schritte 2-4 oben, wenn Sie mehr Registerkarten hinzufügen möchten.
6. Wählen Sie in der Befehlsleiste **Speichern** aus, um das Formular zu speichern, oder wählen Sie **Veröffentlichen** aus, wenn Sie die Änderungen speichern und für Benutzer sichtbar anzeigen möchten. 

## <a name="configure-tabs-on-a-form"></a>Konfigurieren von Registerkarten in einem Formular
Dies sind die verfügbaren Eigenschaften für die Konfiguration einer Registerkarte, wenn Sie ein Formular mithilfe des Formulardesigners erstellen oder bearbeiten.

|Fläche   |Name  |Beschreibung  |
|---------|---------|---------|
|**Anzeigeoptionen** | **Registerkartenbeschriftung** | Die lokalisierbare Beschriftung für die Registerkarte, die für Benutzer sichtbar ist. <br /><br />Diese Eigenschaft ist erforderlich. |
| **Anzeigeoptionen** |  **Name**  |  Der eindeutige Name für die Registerkarte, der verwendet wird, wenn auf sie in Skripts verwiesen wird. Der Name kann nur alphanumerische Zeichen und Unterstrichzeichen enthalten. <br /><br />Diese Eigenschaft ist erforderlich. |
| **Anzeigeoptionen** |  **Registerkarte standardmäßig erweitern** |  Der Status der Registerkarte kann durch Formularskripts oder durch Klicken auf die Beschriftung zwischen erweitert und reduziert gewechselt werden. Wählen Sie den Standardstatus für die Registerkarte. |
| **Anzeigeoptionen** | **Registerkarte ausblenden** | Wenn diese Option ausgewählt ist, wird die Registerkarte standardmäßig ausgeblendet und kann mithilfe von Code angezeigt werden. |
| **Anzeigeoptionen** | **Auf Telefon ausblenden** |  Um eine verkürzte Version dieses Formulars auf Smartphone-Bildschirmen anzuzeigen, können Registerkarten ausgeblendet werden. |
| **Formatierung** | **Layout** |  Registerkarten können bis zu drei Spalten haben. Verwenden Sie diese Optionen, um die Anzahl der Spalten festzulegen, sowie, welchen Prozentsatz der gesamten Breite sie ausfüllen sollen. |

## <a name="move-tabs-on-a-form"></a>Verschieben von Registerkarten in einem Formular
Sie können Registerkarten in einem Formular entweder per Drag & Drop oder durch Ausschneiden und Einfügen verschieben. 

### <a name="move-tabs-on-a-form-using-drag-and-drop"></a>Verschieben von Registerkarten in einem Formular mithilfe des Ziehens und Ablegens
1. Öffnen Sie den Formulardesigner, um ein Formular zu erstellen oder zu bearbeiten. Weitere Informationen: [Erstellen von Formularen](create-and-edit-forms.md#create-a-form) oder [Bearbeiten von Formularen](create-and-edit-forms.md#edit-a-form)
2. Wählen Sie in der Formularvorschau die Registerkartenkopfzeile der gewünschten Registerkarte aus, und verschieben Sie sie per Drag & Drop. Wenn Sie die Registerkarte in die Formularvorschau ziehen, sehen Sie Ablageziele, wo Sie die Registerkarte verschieben können. Beachten Sie Folgendes:
    - Registerkarten können vor oder hinter vorhandenen Registerkarten abgelegt werden, indem Sie die Maus über die Registerkartenkopfzeilen bewegen.
    - Registerkarten können auch vor oder hinter der aktuellen Registerkarte abgelegt werden, indem Sie die Maus über den linken oder rechten Rand der aktuellen Registerkarte bewegen.
3. Wiederholen Sie Schritt 2, wenn Sie mehr Registerkarten verschieben möchten.
4. Wählen Sie in der Befehlsleiste **Speichern** aus, um das Formular zu speichern, oder wählen Sie **Veröffentlichen** aus, wenn Sie die Änderungen speichern und für Benutzer sichtbar anzeigen möchten. 

### <a name="move-tabs-on-a-form-using-cut-and-paste"></a>Verschieben von Registerkarten in einem Formular mithilfe von Ausschneiden und Einfügen
1. Öffnen Sie den Formulardesigner, um ein Formular zu erstellen oder zu bearbeiten. Weitere Informationen: [Erstellen von Formularen](create-and-edit-forms.md#create-a-form) oder [Bearbeiten von Formularen](create-and-edit-forms.md#edit-a-form)
2. Wählen Sie in der Formularvorschau die Registerkarte aus, die verschoben werden soll.
3. Wählen Sie in der Befehlsleiste **Ausschneiden** aus.
4. Wählen Sie in der Formularvorschau eine andere vorhandene Registerkarte oder das Formular aus.
5. Wählen Sie in der Befehlsleiste **Einfügen** oder das Chevron aus, und wählen Sie dann **Einfügen vor** aus.      Beachten Sie Folgendes: 
    - Wenn Sie **Einfügen** auswählen, wird die verschobene Registerkarte hinter der vorhandenen Registerkarte eingefügt. 
    - Wenn Sie **Einfügen vor** auswählen, wird die verschobene Registerkarte vor der vorhandenen Registerkarte eingefügt.
    - Wenn Sie das Formular auswählen, wird die verschobene Registerkarte als die letzte Registerkarte im Formular hinzugefügt. Die Aktion **Einfügen vor** ist nicht zutreffend und daher in diesem Fall nicht verfügbar.
6. Wiederholen Sie die Schritte 2-5 oben, wenn Sie mehr Registerkarten verschieben möchten.
7. Wählen Sie in der Befehlsleiste **Speichern** aus, um das Formular zu speichern, oder wählen Sie **Veröffentlichen** aus, wenn Sie die Änderungen speichern und für Benutzer sichtbar anzeigen möchten. 

## <a name="delete-tabs-on-a-form"></a>Löschen von Registerkarten in einem Formular
1. Öffnen Sie den Formulardesigner, um ein Formular zu erstellen oder zu bearbeiten. Weitere Informationen: [Erstellen von Formularen](create-and-edit-forms.md#create-a-form) oder [Bearbeiten von Formularen](create-and-edit-forms.md#edit-a-form)
2. Wählen Sie in der Formularvorschau die Registerkarte aus, die Sie aus dem Formular löschen möchten. 
3. Wählen Sie in der Befehlsleiste **Löschen** aus.
4. Wiederholen Sie die Schritte 2-3 oben, wenn Sie mehr Registerkarten löschen möchten.
4. Wählen Sie in der Befehlsleiste **Speichern** aus, um das Formular zu speichern, oder wählen Sie **Veröffentlichen** aus, wenn Sie die Änderungen speichern und für Benutzer sichtbar anzeigen möchten. 

    > [!NOTE]
    >   - Registerkarten können nur in Hauptformularen gelöscht werden. Weitere Informationen: [Formulartypen](types-forms.md)
    >   - Wenn Sie eine Registerkarte versehentlich löschen, wählen Sie in der Befehlsleiste **Rückgängig** aus, um das Formular in seinen vorherigen Zustand zurückzusetzen. 
    >   - Sie können eine Registerkarte nicht löschen, die Abschnitte mit benötigten oder gesperrten Feldern enthält. 
    >   - Sie können eine Registerkarte nicht löschen, die gesperrte Abschnitte enthält. 
    >   - Ein Formular muss mindestens eine Registerkarte haben. Sie können eine Registerkarte nicht löschen, wenn sie die letzte verbleibende Registerkarte im Formular ist. 

### <a name="see-also"></a>Siehe auch
[Übersicht über den modellgestützten Formulardesigner](form-designer-overview.md)  
[Erstellen, Bearbeiten oder Konfigurieren von Formularen mit dem Formulardesigner](create-and-edit-forms.md)  
[Hinzufügen, Konfigurieren, Verschieben oder Löschen von Feldern in einem Formular](add-move-or-delete-fields-on-form.md)  
[Hinzufügen, Konfigurieren, Verschieben oder Löschen von Komponenten in einem Formular](add-move-configure-or-delete-components-on-form.md)  
[Hinzufügen, Konfigurieren, Verschieben oder Löschen von Abschnitten in einem Formular](add-move-or-delete-sections-on-form.md)  
[Konfigurieren von Kopfzeileneigenschaften im Formulardesigner](form-designer-header-properties.md)  
[Hinzufügen und Konfigurieren einer Unterraster-Komponente in einem Formular](form-designer-add-configure-subgrid.md)  
[Hinzufügen und Konfigurieren einer Schnellansichts-Komponente in einem Formular](form-designer-add-configure-quickview.md)  
[Konfigurieren einer Suchkomponente in einem Formular](form-designer-add-configure-lookup.md)  
[Verwenden der Strukturansicht im Formulardesigner](using-tree-view-on-form.md)  
[Erstellen und Bearbeiten von Feldern](../common-data-service/create-edit-field-portal.md)  
