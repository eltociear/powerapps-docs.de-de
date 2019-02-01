---
title: Erstellen und Bearbeiten von Formularen mit dem modellgestützen Formulardesigner | MicrosoftDocs
ms.custom: ''
ms.date: 12/13/2018
ms.reviewer: ''
ms.service: crm-online
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

# <a name="create-and-edit-forms-using-the-form-designer"></a>Erstellen und Bearbeiten von Formularen mit dem Formulardesigner 
[!INCLUDE [cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

Verwenden Sie den Formulardesigner, um neue Formulare für modellgestützte Apps zu erstellen und zu entwerfen.

> [!IMPORTANT]
> Der neue modellgestützte Formulardesigner unterstützt derzeit nur das Erstellen und Bearbeiten von Hauptformularen. Weitere Informationen: [Formulartypen](types-forms.md)

## <a name="create-a-form"></a>Ein Formular erstellen 
1. Melden Sie sich bei [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an. 
2. Erweitern Sie **Daten** im linken Navigationsbereich und wählen Sie **Entitäten**. 
3. Wählen Sie eine Entität, beispielsweise Firmenentität, und wählen Sie dann die **Formular**-Registerkarte 
4. Wählen Sie **Formular hinzufügen** und dann **Haputformular (Vorschau)** aus.     
    Die Inhalte des neuen Formulars werden mithilfe der vorhandenen Hauptformulardefinition ausgefüllt. Wenn mehrere Hauptformulare vorhanden sind, wird das oberste Formular der Formularreihenfolge verwendet, um das neue Formular auszufüllen. 
5. Aktivieren Sie **Speichern**, um das Formular zu speichern, oder wählen Sie **Veröffentlichen** wenn Sie die Änderungen speichern und für App-Benutzer sichtbar anzeigen möchten.  

## <a name="edit-a-form"></a>Bearbeiten eines Formulars 
1. Melden Sie sich bei [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an. 
2. Erweitern Sie im linken Navigationsbereich, wählen Sie **Daten** und dann **Entitäten** aus. 
3. Wählen Sie eine Entität, beispielsweise Firmenentität, und wählen Sie dann die **Formular**-Registerkarte
4. Wählen Sie das Formular aus, das Sie bearbeiten möchten, und wählen Sie dann **Formular bearbeiten (Vorschau)** aus.  
   Sie können auch **...** neben dem gewünschten Formular auswählen und dann **Formular bearbeiten (Vorschau)** anklicken. 
5. Aktivieren Sie **Speichern**, um das Formular zu speichern, oder wählen Sie **Veröffentlichen** wenn Sie die Änderungen speichern und für App-Benutzer sichtbar anzeigen möchten. 

## <a name="add-and-remove-fields"></a>Hinzufügen und Entfernen von Feldern 
Um Felder aus einem Formular hinzufügen und entfernen, verwenden Sie den Bereich Felder. Im Bereich Felder können Sie zum schnellen Finden von Feldern filtern und durchsuchen. Sie können sich auch nur nicht verwendete Felder anzeigen lassen. 

### <a name="add-a-field"></a>Hinzufügen eines Felds
1. Öffnen Sie den Formulardesigner, um ein Formular zu erstellen oder zu bearbeiten. Weitere Informationen: [Erstellen von Formularen](#create-a-form) und [Bearbeiten von Formularen](#edit-a-form)
2. Wählen Sie in der Formularvorschau ein anderes vorhandenes Feld oder einen Abschnitt aus. 
    - Wenn Sie ein bestehendes Feld auswählen, wird das neue Feld unterhalb des bestehenden Feldes hinzugefügt. 
    - Wenn Sie einen Abschnitt auswählen, wird das neue Feld in einem verfügbaren Bereich hinzugefügt, um die Felder gleichmäßig auf die Spalten zu verteilen. 
3. Wählen Sie **Feld hinzufügen** oder wählen Sie im linken Bereich **Felder** aus.  
   Der Bereich Felder ist standardmäßig geöffnet, wenn der Formulardesigner geöffnet wird. 
4. Suchen, filtern oder scrollen Sie im Bereich **Felder**, um das Feld zu finden, das Sie hinzufügen möchten. 
   Wenn Sie ein Feld nicht finden können, ist möglicherweise bereits im Formular enthalten. Löschen Sie **Nur unbenutzte Felder anzeigen**, um alle Felder anzuzeigen, auch die, die bereits dem Formular hinzugefügt wurden. 
5. Wählen Sie im Bereich **Felder** ein Feld aus, um es dem Formular hinzuzufügen. <br />
   Alternativ können Sie **...** neben dem gewünschten Feld auswählen und dann **Zum ausgewählten Abschnitt hinzufügen** klicken. 
6. Wählen Sie **Speichern**, um das Formular zu speichern, oder **Veröffentlichen**, wenn Sie speichern und Ihre Änderungen für Endbenutzer sichtbar machen möchten. 

### <a name="remove-a-field"></a>Entfernen eines Felds
1. Öffnen Sie den Formulardesigner, um ein Formular zu erstellen oder zu bearbeiten. Weitere Informationen: [Erstellen von Formularen](#create-a-form) und [Bearbeiten von Formularen](#edit-a-form)
2. Wählen Sie in der Formularvorschau das Feld aus, das Sie aus dem Formular entfernen möchten. 
3. Wählen Sie **Löschen**. <br />
4. Wählen Sie **Speichern** aus. 

    > [!NOTE]
    >   -  Wenn Sie ein Feld versehentlich entfernen, wählen Sie **Rückgängig**, um die Aktion zurückzusetzen. 
    >   -  Sie können ein erforderliches oder gesperrtes Feld nicht entfernen. 

## <a name="add-and-remove-tabs-and-sections"></a>Hinzufügen und Entfernen von Registerkarten und Abschnitten 
Um eine Registerkarte oder einen Abschnitt in einem Formular hinzuzufügen oder zu entfernen, verwenden Sie den Bereich Layouts. 

### <a name="add-a-tab"></a>Registerkarte hinzufügen
1. Öffnen Sie den Formulardesigner, um ein Formular zu erstellen oder zu bearbeiten. Weitere Informationen: [Erstellen von Formularen](#create-a-form) und [Bearbeiten von Formularen](#edit-a-form) 
2. Wählen Sie in der Formularvorschau eine andere vorhandene Registerkarte oder das Formular aus. 
    - Wenn Sie eine vorhandene Registerkarte auswählen, wird die neue Registerkarte rechts neben der bestehenden Registerkarte hinzugefügt. 
    - Wenn Sie das Formular auswählen, wird die neue Registerkarte als die ganz rechte Registerkarte im Formular hinzugefügt. 
3. Wählen Sie **Steuerelement hinzufügen** oder wählen Sie im linken Bereich **Layouts** aus.  
4. Wählen Sie im Fenster **Layouts** ein Registerkartensteuerelement, wie z.B. eine **Registerkarte mit 2 Spalten**, um es dem Formular hinzuzufügen. <br />
   Alternativ können Sie **...** neben dem gewünschten Registerkartensteuerelement auswählen und dann **Zum Formular hinzufügen** klicken.  
5. Wählen Sie **Speichern** aus. 


### <a name="remove-a-tab"></a>Entfernen einer Registerkarte
1. Öffnen Sie den Formulardesigner, um ein Formular zu erstellen oder zu bearbeiten. Weitere Informationen: [Erstellen von Formularen](#create-a-form) und [Bearbeiten von Formularen](#edit-a-form)
2. Wählen Sie in der Formularvorschau die Registerkarte, die Sie löschen möchten, und wählen Sie dann **Löschen**. 
3. Wählen Sie **Speichern** aus. 
    > [!NOTE]
    >    - Wenn Sie ein Feld versehentlich löschen, wählen Sie **Rückgängig**, um die Löschen-Aktion zurückzusetzen. 
    >     - Ein Formular muss mindestens eine Registerkarte haben. Sie können eine Registerkarte nicht löschen, wenn sie die einzige Registerkarte im Formular ist. 
    >    - Sie können eine Registerkarte nicht löschen, die gesperrte Abschnitte enthält. 
    >    - Sie können eine Registerkarte nicht löschen, die Abschnitte mit benötigten oder gesperrten Feldern enthält. 

### <a name="add-a-section"></a>Abschnitt hinzufügen 
1. Öffnen Sie den Formulardesigner, um ein Formular zu erstellen oder zu bearbeiten. Weitere Informationen: [Erstellen von Formularen](#create-a-form) und [Bearbeiten von Formularen](#edit-a-form)
2. Wählen Sie in der Formularvorschau einen anderen vorhandenen Abschnitt oder ein Feld aus. 
    - Wenn Sie einen bestehenden Abschnitt auswählen, wird der neue Abschnitt unterhalb des bestehenden Abschnitts hinzugefügt. 
    - Wenn Sie eine Registerkarte auswählen, wird der neue Abschnitt unten der ersten Spalte der Registerkarte hinzugefügt. 
3. Wählen Sie **Steuerelement hinzufügen** oder wählen Sie im linken Bereich **Layouts** aus.
4. Wählen Sie im Bereich **Layouts** ein Abschnittsteuerelement aus, um es dem Formular hinzuzufügen. <br />
   Alternativ können Sie **...** neben dem gewünschten Abschnittsteuerelement auswählen und dann **Zur ausgewählten Registerkarte hinzufügen** klicken.      
5. Wählen Sie **Speichern** aus. 
 

### <a name="delete-a-section"></a>Einen Abschnitt löschen 
1. Öffnen Sie den Formulardesigner, um ein Formular zu erstellen oder zu bearbeiten. Weitere Informationen: [Erstellen von Formularen](#create-a-form) und [Bearbeiten von Formularen](#edit-a-form) 
2. Wählen Sie in der Formularvorschau den Abschnitt, den Sie löschen möchten, und wählen Sie dann **Löschen**.  
3. Wählen Sie **Speichern** aus. 
    > [!NOTE]
    >    - Wenn Sie einen Abschnitt versehentlich löschen, wählen Sie **Rückgängig**, um die Löschen-Aktion zurückzusetzen. 
    >    - Eine Registerkarte muss mindestens einen Abschnitt in jeder Spalte haben.  
    >    - Sie können einen Abschnitt nicht löschen, wenn er der einzige in der Registerkartenspalte ist. 
    >    - Sie können keinen gesperrten Abschnitt löschen. 
    >    - Sie können einen Abschnitt nicht löschen, der benötigte oder gesperrte Felder enthält. 
 
## <a name="use-the-tree-view"></a>Verwenden der Strukturansicht 
Der Bereich Strukturansicht zeigt eine visuelle Hierarchie der Steuerelemente und Felder auf dem Formular an. Die Symbole in der Strukturansicht helfen Ihnen, die Art des Feldes oder des Steuerelements schnell zu erkennen. 

Sie können die Strukturansicht auch nutzen, um Felder und Steuerelemente auszuwählen, die sich im Formular befinden. Die Strukturansicht ist außerdem nützlich, wenn Sie ausgeblendete Elemente auswählen möchten, die aus diesem Grund nicht in der Formularvorschau angezeigt werden. 

Sie können Knoten in der Strukturansicht erweitern oder reduzieren, um die Elemente innerhalb eines Knotens anzuzeigen oder auszublenden. Wenn Sie ein Element in einer Strukturansicht auswählen, wird es in der Formularvorschau markiert, und der Eigenschaftenbereich zeigt die Eigenschaften für das Element an. 

   ![Strukturansicht](media/tree-view.png)

### <a name="open-the-tree-view"></a>Strukturansicht öffnen 
1. Öffnen Sie den Formulardesigner, um ein Formular zu erstellen oder zu bearbeiten. Weitere Informationen: [Erstellen von Formularen](#create-a-form) und [Bearbeiten von Formularen](#edit-a-form)  
2. Wählen Sie im linken Bereich **Strukturansicht** aus.

## <a name="see-also"></a>Siehe auch
[Übersicht über den modellgestützten Formulardesigner](form-designer-overview.md) <br />
[Erstellen und Bearbeiten von Feldern](../common-data-service/create-edit-field-portal.md)
