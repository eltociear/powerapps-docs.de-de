---
title: Konfigurieren einer Lookup-Komponente auf einem Formular | MicrosoftDocs".
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
ms.openlocfilehash: 8ba09c46a46d0a4d40891419e1f6eb787f75f096
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2703905"
---
# <a name="configure-a-lookup-component-on-a-form"></a>Konfigurieren einer Lookup-Komponente auf einem Formular  
Ein Lookup-Feld kann verwendet werden, um auf einen Datensatz in einer anderen Entität zu verweisen. Eine Lookup-Komponente wird automatisch verwendet, wenn ein Lookup-Feld zu einem Formular hinzugefügt wird. Hersteller können eine Lookup-Komponente mit Hilfe des Formular-Designers konfigurieren.

## <a name="configure-a-lookup-component"></a>Konfigurieren einer Lookup-Komponente
Dies sind die Eigenschaften, die konfiguriert werden können, wenn Sie eine Lookup-Komponente in einem Formular mit dem Formulardesigner verwenden.


<!--from editor: "Drop-down" should only be an adjective. In the following table, is it a list? A menu? -->


|Fläche  |Name  |Beschreibung  |
|---------|---------|---------|
| **Anzeigeoptionen** | **Entität** |  Die zugehörige Entität, mit der sich das Lookup-Feld verbindet. |
| **Anzeigeoptionen** | **Standardansicht** |  Die Ansicht der in der Eigenschaft **Entity** ausgewählten Entität, mit der die Liste der Datensätze abgerufen und angezeigt werden kann, die App-Benutzer in der Dropdown-Liste Lookup auswählen können. |
| **Anzeigeoptionen** | **Erlauben Sie Benutzern, die Ansicht zu ändern**. |  Wenn ausgewählt, können App-Benutzer von der **Standardansicht** zu einer anderen Ansicht der in der **Entity**-Eigenschaft ausgewählten Entität wechseln. |
| **Anzeigeoptionen** | **Alle Ansichten anzeigen** |  Wenn diese Option ausgewählt ist, können App-Benutzer von der **Standardansicht** zu allen anderen Ansichten der Entität wechseln, die in der Eigenschaft **Entity** ausgewählt wurde. <br /><br />Diese Eigenschaft ist nur verfügbar, wenn **Benutzern erlauben, die Ansicht zu ändern** ausgewählt ist. |
| **Anzeigeoptionen** | **Ausgewählte Ansichten** |  Eine Liste von Ansichten der Entität, die in der **Entity**-Eigenschaft ausgewählt wurde, zu der App-Benutzer von der **Standardansicht** wechseln können. <br /><br />Diese Eigenschaft ist nur verfügbar, wenn **Benutzern erlauben, die Ansicht zu ändern** ausgewählt ist und **Alle Ansichten anzeigen** nicht ausgewählt ist. |

## <a name="see-also"></a>Siehe auch
[Übersicht über den modellgestützten Formulardesigner](form-designer-overview.md)  
[Erstellen, Bearbeiten oder Konfigurieren von Formularen mit dem Formulardesigner](create-and-edit-forms.md)  
[Hinzufügen, Konfigurieren, Verschieben oder Löschen von Feldern in einem Formular](add-move-or-delete-fields-on-form.md)  
[Hinzufügen, Konfigurieren, Verschieben oder Löschen von Komponenten in einem Formular](add-move-configure-or-delete-components-on-form.md)  
[Hinzufügen, Konfigurieren, Verschieben oder Löschen von Abschnitten in einem Formular](add-move-or-delete-sections-on-form.md)  
[Hinzufügen, Konfigurieren, Verschieben oder Löschen von Registerkarten in einem Formular](add-move-or-delete-tabs-on-form.md)  
[Konfigurieren von Kopfzeileneigenschaften im Formulardesigner](form-designer-header-properties.md)  
[Hinzufügen und Konfigurieren einer Unterraster-Komponente in einem Formular](form-designer-add-configure-subgrid.md)  
[Hinzufügen und Konfigurieren einer Schnellansichts-Komponente in einem Formular](form-designer-add-configure-quickview.md)  
[Verwenden der Strukturansicht im Formulardesigner](using-tree-view-on-form.md)  
[Erstellen und Bearbeiten von Feldern](../common-data-service/create-edit-field-portal.md)  
