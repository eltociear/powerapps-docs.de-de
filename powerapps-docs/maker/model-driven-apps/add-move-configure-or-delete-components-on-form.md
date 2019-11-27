---
title: Hinzufügen, Konfigurieren, Verschieben oder Löschen von Komponenten in einem Formular | Microsoft-Dokumentation
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
ms.openlocfilehash: a40b0b9e5fc64856be931a2407a451c8d27ef8ec
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2702365"
---
# <a name="add-configure-move-or-delete-components-on-a-form"></a>Hinzufügen, Konfigurieren, Verschieben oder Löschen von Komponenten in einem Formular  
Mithilfe des Formulardesigners können Entwickler ganz einfach beliebte Komponenten wie z. B. [Unterraster](form-designer-add-configure-subgrid.md), [Schnellansichten](form-designer-add-configure-quickview.md), Kreis-Knopf-Steuerelemente, Schieberegler usw. hinzufügen und konfigurieren.

## <a name="add-components-to-a-form"></a>Hinzufügen von Komponenten zu einem Formular
Um Komponenten zu einem Formular hinzuzufügen, verwenden Sie den Bereich **Komponenten**. Im Bereich **Komponenten** können Sie auch nach schnell nach Komponenten suchen.  

> [!div class="mx-imgBorder"] 
> ![](media/FormDesignerComponentsPane.PNG "Components pane")

### <a name="add-components-to-a-form-using-drag-and-drop"></a>Hinzufügen von Komponenten zu einem Formular mithilfe von Drag & Drop
> [!NOTE]
> Wenn Sie Komponenten mithilfe von Drag & Drop hinzufügen oder verschieben, beachten Sie, dass die Formularvorschau reagiert und möglicherweise mehrere Abschnittsspalten als gestapelt rendert. Um sicherzustellen, dass die hinzugefügte oder verschobene Komponente in der richtigen Abschnittsspalte ist, legen Sie sie oder fügen Sie sie verankert in ein anderes Feld oder in eine andere Komponente ab/ein, das bzw. die sich bereits in dieser Abschnittsspalte befindet.
1. Öffnen Sie den Formulardesigner, um ein Formular zu erstellen oder zu bearbeiten. Weitere Informationen: [Erstellen von Formularen](create-and-edit-forms.md#create-a-form) oder [Bearbeiten von Formularen](create-and-edit-forms.md#edit-a-form)
2. Wählen Sie in der Befehlsleiste **Komponente hinzufügen** oder im linken Bereich **Komponenten** aus, um eine Liste der verfügbaren Komponenten anzuzeigen. Sie können auch den Mauszeiger über eine Komponente in der Liste bewegen, um ein Vorschaubild, eine Beschreibung und andere Details der Komponente anzuzeigen.
3. Suchen oder scrollen Sie im Bereich **Komponenten**, um die Komponente zu suchen, die hinzugefügt werden soll, und wählen Sie sie aus.
4. Ziehen Sie die Komponente zur Formularvorschau, und legen Sie sie dort ab. Wenn Sie die Komponente in die Formularvorschau ziehen, sehen Sie Ablageziele, wo Sie die Komponente hinzufügen können. 

   Beachten Sie Folgendes: 
    - Komponenten können vor oder hinter einer vorhandenen Komponente bzw. einem vorhandenen Feld abgelegt werden.
    - Komponenten können auch in den leeren Bereich in einem Abschnitt abgelegt werden. In diesem Fall wird die Komponente in einem verfügbaren Bereich hinzugefügt, um die Felder und Komponenten gleichmäßig auf die Abschnittsspalten zu verteilen.
    - Durch das Hovern über eine Registerkartenkopfzeile beim Ziehen einer Komponente wird die gerade ausgewählte Registerkarte geändert, sodass Sie die Komponente zu einer anderen Registerkarte hinzufügen können.
    - Wenn Sie die Komponente ablegen, wird in den meisten Fällen ein Dialogfeld angezeigt, in dem Sie die Eigenschaften der Komponente konfigurieren können. Stellen Sie sicher, dass Sie alle erforderlichen Eigenschaften der Komponente konfiguriert haben. 
5. Im Dialogfeld zur Konfiguration der Eigenschaften der Komponente sind unter **Komponente anzeigen auf** die Optionen **Web**, **Mobil** und **Tablet** standardmäßig ausgewählt, um sicherzustellen, dass die Komponente bei Anzeige des Formulars im Web, in der mobilen App bzw. in der Tablet-App angezeigt wird. Je nach Ihren Anforderungen können Sie einige dieser Optionen deaktivieren, um die Verwendung der Komponente einzuschränken. **Fertig** auswählen
6. Wiederholen Sie die Schritte 3 bis 5, um weitere Komponenten hinzuzufügen.
7. Wählen Sie in der Befehlsleiste **Speichern** aus, um das Formular zu speichern, oder wählen Sie **Veröffentlichen** aus, wenn Sie die Änderungen speichern und für Benutzer sichtbar anzeigen möchten. 

### <a name="add-components-for-a-field-on-the-form"></a>Hinzufügen von Komponenten für ein Feld im Formular
1. Öffnen Sie den Formulardesigner, um ein Formular zu erstellen oder zu bearbeiten. Weitere Informationen: [Erstellen von Formularen](create-and-edit-forms.md#create-a-form) oder [Bearbeiten von Formularen](create-and-edit-forms.md#edit-a-form)
2. Wählen Sie in der Formularvorschau ein vorhandenes Feld aus.
3. Wählen Sie im Eigenschaftenfenster unter dem Bereich **Komponenten** die Option **+ Komponente**.
4. Das Dialogfeld **Komponente hinzufügen** wird mit einer Liste von Komponenten angezeigt, die für den aktuellen Feldtyp verfügbar sind. Sie können auch den Mauszeiger über eine Komponente in der Liste bewegen, um ein Vorschaubild, eine Beschreibung und andere Details der Komponente anzuzeigen.
5. Suchen oder scrollen Sie im Dialogfeld **Komponente hinzufügen**, um die Komponente zu suchen, die hinzugefügt werden soll, und wählen Sie sie aus.
   In den meisten Fällen wird ein Dialogfeld angezeigt, in dem Sie die Eigenschaften der Komponente konfigurieren können. Stellen Sie sicher, dass Sie alle erforderlichen Eigenschaften der Komponente konfiguriert haben.
6. Im Dialogfeld zur Konfiguration der Eigenschaften der Komponente sind unter **Komponente anzeigen auf** die Optionen **Web**, **Mobil** und **Tablet** standardmäßig ausgewählt, um sicherzustellen, dass die Komponente bei Anzeige des Formulars im Web, in der mobilen App bzw. in der Tablet-App angezeigt wird. Je nach Ihren Anforderungen können Sie einige dieser Optionen deaktivieren, um die Verwendung der Komponente einzuschränken. Wählen Sie **Fertig** aus.
7. Wiederholen Sie die Schritte 2 bis 6, wenn Sie weitere Komponenten zum gleichen Feld oder zu einem anderen Feld hinzufügen möchten.
8. Wählen Sie in der Befehlsleiste **Speichern** aus, um das Formular zu speichern, oder wählen Sie **Veröffentlichen** aus, wenn Sie die Änderungen speichern und für Benutzer sichtbar anzeigen möchten.

## <a name="configure-components-on-a-form"></a>Konfigurieren von Komponenten in einem Formular
1. Öffnen Sie den Formulardesigner, um ein Formular zu erstellen oder zu bearbeiten. Weitere Informationen: [Erstellen von Formularen](create-and-edit-forms.md#create-a-form) oder [Bearbeiten von Formularen](create-and-edit-forms.md#edit-a-form)
2. Wählen Sie in der Formularvorschau ein vorhandenes Feld aus.
3. Wählen Sie im Eigenschaftenfenster unter dem Bereich **Komponenten** die Komponente aus, die Sie konfigurieren möchten.
4. Möglicherweise wird ein Dialogfeld angezeigt, um die Eigenschaften der Komponente zu konfigurieren. Ändern Sie die Eigenschaften der Komponente nach Bedarf, und wählen Sie **Fertig** aus.
5. Wiederholen Sie die Schritte 2 bis 4, um weitere Komponenten für das gleiche Feld oder ein anderes Feld zu konfigurieren.
6. Wählen Sie in der Befehlsleiste **Speichern** aus, um das Formular zu speichern, oder wählen Sie **Veröffentlichen** aus, wenn Sie die Änderungen speichern und für Benutzer sichtbar anzeigen möchten.

## <a name="move-components-on-a-form"></a>Verschieben von Komponenten in einem Formular
Sie können Komponenten in einem Formular entweder per Drag & Drop oder durch Ausschneiden und Einfügen verschieben. 

### <a name="move-components-on-a-form-using-drag-and-drop"></a>Verschieben von Komponenten in einem Formular mithilfe von Drag & Drop
1. Öffnen Sie den Formulardesigner, um ein Formular zu erstellen oder zu bearbeiten. Weitere Informationen: [Erstellen von Formularen](create-and-edit-forms.md#create-a-form) oder [Bearbeiten von Formularen](create-and-edit-forms.md#edit-a-form)
2. Wählen Sie in der Formularvorschau die gewünschte Komponente aus, und verschieben Sie sie per Drag & Drop. Wenn Sie die Komponente in die Formularvorschau ziehen, sehen Sie Ablageziele, wohin Sie die Komponente verschieben können.     

   Beachten Sie Folgendes: 
    - Komponenten können vor oder hinter einer vorhandenen Komponente bzw. einem vorhandenen Feld abgelegt werden.
    - Komponenten können auch in den leeren Bereich in einem Abschnitt abgelegt werden. In diesem Fall wird die Komponente in einem verfügbaren Bereich hinzugefügt, um die Komponenten und Felder gleichmäßig auf die Abschnittsspalten zu verteilen.
    - Durch das Hovern über eine Registerkartenkopfzeile beim Ziehen einer Komponente wird die gerade ausgewählte Registerkarte geändert, sodass Sie die Komponente zu einer anderen Registerkarte hinzufügen können.   
4. Wiederholen Sie die Schritte 2 bis 3, um weitere Komponenten zu verschieben.
5. Wählen Sie in der Befehlsleiste **Speichern** aus, um das Formular zu speichern, oder wählen Sie **Veröffentlichen** aus, wenn Sie die Änderungen speichern und für Benutzer sichtbar anzeigen möchten. 

### <a name="move-components-on-a-form-using-cut-and-paste"></a>Verschieben von Komponenten in einem Formular mithilfe von Ausschneiden und Einfügen
1. Öffnen Sie den Formulardesigner, um ein Formular zu erstellen oder zu bearbeiten. Weitere Informationen: [Erstellen von Formularen](create-and-edit-forms.md#create-a-form) oder [Bearbeiten von Formularen](create-and-edit-forms.md#edit-a-form)
2. Wählen Sie in der Formularvorschau die Komponente aus, die verschoben werden soll.
3. Wählen Sie in der Befehlsleiste **Ausschneiden** aus.
4. Wählen Sie in der Formularvorschau eine andere vorhandene Komponente, ein Feld oder einen Abschnitt aus. Sie können auch zu einer anderen Registerkarte wechseln.
5. Wählen Sie in der Befehlsleiste **Einfügen** oder das Chevron aus, und wählen Sie dann **Einfügen vor** aus.     

   Beachten Sie Folgendes:
    - Wenn Sie **Einfügen** auswählen, wird die verschobene Komponente hinter der vorhandenen Komponente bzw. dem Feld eingefügt. 
    - Wenn Sie **Einfügen vor** auswählen, wird die verschobene Komponente vor der vorhandenen Komponente bzw. dem Feld eingefügt.
    - Wenn Sie einen Abschnitt auswählen, wird die verschobene Komponente in einem verfügbaren Bereich hinzugefügt, um die Komponenten und Felder gleichmäßig auf die Abschnittsspalten zu verteilen. Die Aktion **Einfügen vor** ist nicht zutreffend und daher in diesem Fall nicht verfügbar.
6. Wiederholen Sie die Schritte 2 bis 5 oben, wenn Sie mehr Komponenten verschieben möchten.
7. Wählen Sie in der Befehlsleiste **Speichern** aus, um das Formular zu speichern, oder wählen Sie **Veröffentlichen** aus, wenn Sie die Änderungen speichern und für Benutzer sichtbar anzeigen möchten. 

## <a name="delete-components-on-a-form"></a>Löschen von Komponenten in einem Formular
1. Öffnen Sie den Formulardesigner, um ein Formular zu erstellen oder zu bearbeiten. Weitere Informationen: [Erstellen von Formularen](create-and-edit-forms.md#create-a-form) oder [Bearbeiten von Formularen](create-and-edit-forms.md#edit-a-form)
2. Wählen Sie in der Formularvorschau die Komponente aus, die Sie aus dem Formular entfernen möchten, und wählen Sie anschließend in der Befehlsleiste **Löschen** aus. 
3. Wiederholen Sie Schritt 2, wenn Sie mehr Komponenten löschen möchten.
4. Wählen Sie in der Befehlsleiste **Speichern** aus, um das Formular zu speichern, oder wählen Sie **Veröffentlichen** aus, wenn Sie die Änderungen speichern und für Benutzer sichtbar anzeigen möchten. 

     > [!NOTE]
     >   -  Wenn Sie eine Komponente versehentlich löschen, wählen Sie in der Befehlsleiste **Rückgängig** aus, um das Formular in seinen vorherigen Zustand zurückzusetzen. 
     >   -  Sie können keine Komponente löschen, die gesperrt ist oder ein Pflichtfeld verwendet, das nirgendwo sonst im Formular vorhanden ist. 

### <a name="see-also"></a>Siehe auch
[Übersicht über den modellgestützten Formulardesigner](form-designer-overview.md)  
[Erstellen, Bearbeiten oder Konfigurieren von Formularen mit dem Formulardesigner](create-and-edit-forms.md)  
[Hinzufügen, Konfigurieren, Verschieben oder Löschen von Feldern in einem Formular](add-move-or-delete-fields-on-form.md)  
[Hinzufügen, Konfigurieren, Verschieben oder Löschen von Abschnitten in einem Formular](add-move-or-delete-sections-on-form.md)  
[Hinzufügen, Konfigurieren, Verschieben oder Löschen von Registerkarten in einem Formular](add-move-or-delete-tabs-on-form.md)  
[Konfigurieren von Kopfzeileneigenschaften im Formulardesigner](form-designer-header-properties.md)  
[Hinzufügen und Konfigurieren einer Unterraster-Komponente in einem Formular](form-designer-add-configure-subgrid.md)  
[Hinzufügen und Konfigurieren einer Schnellansichts-Komponente in einem Formular](form-designer-add-configure-quickview.md)  
[Konfigurieren einer Suchkomponente in einem Formular](form-designer-add-configure-lookup.md)  
[Verwenden der Strukturansicht im Formulardesigner](using-tree-view-on-form.md)  
[Erstellen und Bearbeiten von Feldern](../common-data-service/create-edit-field-portal.md)  
