---
title: Erstellen, Bearbeiten oder Konfigurieren von Formularen mit dem modellgesteuerten Formulardesigner | MicrosoftDocs
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
- Power Apps maker portal impact
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 3d35a73f02a1df1e3d5fd51f422b2b24263f53b5
ms.sourcegitcommit: 861ba8e719fa16899d14e4a628f9087b47206993
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2019
ms.locfileid: "2875616"
---
# <a name="create-edit-or-configure-forms-using-the-form-designer"></a>Erstellen, Bearbeiten oder Konfigurieren von Formularen mit dem Formulardesigner 
Verwenden Sie den Formulardesigner, um Formulare für modellgesteuerte Apps zu erstellen, zu bearbeiten oder zu konfigurieren. 

> [!IMPORTANT]
> Der neue modellgesteuerte Formulardesigner unterstützt derzeit nicht das Bearbeiten von Kartenformularen. Weitere Informationen: [Formulartypen](types-forms.md)

## <a name="create-a-form"></a>Ein Formular erstellen 
1. Melden Sie sich bei [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an. 
2. Erweitern Sie **Daten** im linken Navigationsbereich und wählen Sie **Entitäten**. 
3. Wählen Sie eine Entität, beispielsweise Firmenentität, und wählen Sie dann die **Formular**-Registerkarte 
4. Wählen Sie **Formular hinzufügen** aus, und wählen Sie dann eines der folgenden Attribute aus
    - **Hauptformular**  
    Die Inhalte des neuen Formulars werden mithilfe der vorhandenen Hauptformulardefinition ausgefüllt. Wenn mehrere Hauptformulare vorhanden sind, wird das oberste Formular der Formularreihenfolge verwendet, um das neue Formular auszufüllen. 
    - **Formular für Schnellerfassung**
    - **Schnellansichtsformular**
5. Wenn Sie die Formularänderungen abgeschlossen haben, wählen Sie **Speichern** aus, um das Formular zu speichern, oder wählen Sie **Veröffentlichen** aus, wenn Sie die Änderungen speichern und für App-Benutzer sichtbar anzeigen möchten.  

## <a name="edit-a-form"></a>Bearbeiten eines Formulars 
1. Melden Sie sich bei [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an. 
2. Erweitern Sie **Daten** im linken Navigationsbereich und wählen Sie **Entitäten**. 
3. Wählen Sie eine Entität, beispielsweise Firmenentität, und wählen Sie dann die **Formular**-Registerkarte
4. Wählen Sie den zu bearbeitenden Formularnamen aus.  
    - Sie können auch die Zeile für ein Formular und dann in der Befehlsleiste **Formular bearbeiten** auswählen
    - Eine weitere Alternative ist, **...** neben dem Formularnamen und dann im Menü **Formular bearbeiten** auszuwählen. 
5. Wenn Sie die Formularänderungen abgeschlossen haben, wählen Sie **Speichern** aus, um das Formular zu speichern, oder wählen Sie **Veröffentlichen** aus, wenn Sie die Änderungen speichern und für App-Benutzer sichtbar anzeigen möchten. 

## <a name="configure-a-form"></a>Konfigurieren eines Formulars
Dies sind die verfügbaren Eigenschaften für die Konfiguration eines Formulars, wenn Sie ein Formular mithilfe des Formulardesigners erstellen oder bearbeiten.

|Name  |Beschreibung  |
|---------|---------|
|**Titel**  | Geben Sie einen aussagekräftigen Namen für andere Entwickler und App-Benutzer ein. Dieser Name wird App-Benutzern angezeigt. Wenn Benutzer Zugriff auf mehrere Formulare für eine Entität haben, wird dieser Name verwendet, um verschiedene Formulare voneinander zu unterscheiden. <br /><br />Diese Eigenschaft ist erforderlich. |
|**Beschreibung** |  Geben Sie eine Beschreibung ein, die erläutert, wodurch sich das Formular von anderen Hauptformularen unterscheidet. Diese Beschreibung wird Entwicklern nur in der Liste der Formulare für eine Entität im Lösungs-Explorer angezeigt. |
|**Maximale Breite** | Legen Sie eine maximale Breite (in Pixeln) fest, um die Breite des Formulars zu beschränken. Der Standardwert ist 1900. <br /><br />Diese Eigenschaft ist erforderlich. |
|**Bild anzeigen** | Zeigen Sie das **Primäre Bild** der Entität an, falls eins festgelegt wurde. Mit dieser Einstellung kann das Bildfeld in der Überschrift des Formulars angezeigt werden. <br /><br /> Siehe Aktivieren oder Deaktivieren von Entitätsoptionen für weitere Informationen zu Entitätsoptionen. |

## <a name="see-also"></a>Siehe auch
[Übersicht über den modellgestützten Formulardesigner](form-designer-overview.md)  
[Hinzufügen, Konfigurieren, Verschieben oder Löschen von Feldern in einem Formular](add-move-or-delete-fields-on-form.md)  
[Hinzufügen, Konfigurieren, Verschieben oder Löschen von Komponenten in einem Formular](add-move-configure-or-delete-components-on-form.md)  
[Hinzufügen, Konfigurieren, Verschieben oder Löschen von Abschnitten in einem Formular](add-move-or-delete-sections-on-form.md)  
[Hinzufügen, Konfigurieren, Verschieben oder Löschen von Registerkarten in einem Formular](add-move-or-delete-tabs-on-form.md)  
[Konfigurieren von Kopfzeileneigenschaften im Formulardesigner](form-designer-header-properties.md)  
[Hinzufügen und Konfigurieren einer Unterraster-Komponente in einem Formular](form-designer-add-configure-subgrid.md)  
[Hinzufügen und Konfigurieren einer Schnellansichts-Komponente in einem Formular](form-designer-add-configure-quickview.md)  
[Konfigurieren einer Suchkomponente in einem Formular](form-designer-add-configure-lookup.md)  
[Verwenden der Strukturansicht im Formulardesigner](using-tree-view-on-form.md)  
[Erstellen und Bearbeiten von Feldern](../common-data-service/create-edit-field-portal.md)  
