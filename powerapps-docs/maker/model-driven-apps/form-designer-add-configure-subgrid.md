---
title: Hinzufügen und Konfigurieren einer Sub-Grid-Komponente auf einem Formular | MicrosoftDocs
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
ms.openlocfilehash: e46d12b61438890bfa71e1298f5745b6d23e55e3
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2703465"
---
<!-- note from editor: I recommend removing the hyphen from "sub-grid" based on the style guide entry for sub: https://styleguides.azurewebsites.net/Styleguide/Read?id=2700&topicid=28872. I didn't change it here because I don't know how wide an impact that might have. -->


# <a name="add-and-configure-a-sub-grid-component-on-a-form"></a>Hinzufügen und Konfigurieren einer Sub-Grid-Komponente auf einem Formular  
Ein Formular, das die Details eines Datensatzes anzeigt, kann eine Sub-Grid-Komponente verwenden, um eine Liste von verwandten oder nicht verwandten Datensätzen in einem tabellarischen Format anzuzeigen. Mit dem Formular-Designer können Hersteller eine Sub-Grid-Komponente hinzufügen und konfigurieren.

## <a name="add-a-sub-grid-component"></a>Hinzufügen einer Sub-Grid-Komponente
Sie fügen eine Sub-Grid-Komponente auf die gleiche Weise hinzu wie jede andere Komponente. Mehr Informationen: [Komponenten auf einem Formular hinzufügen, konfigurieren, verschieben oder löschen](add-move-configure-or-delete-components-on-form.md)

## <a name="configure-a-sub-grid-component"></a>Konfigurieren einer Sub-Grid-Komponente
Dies sind die Eigenschaften, die konfiguriert werden können, wenn Sie eine Sub-Grid-Komponente auf einem Formular mit dem Formulardesigner verwenden.


|Fläche   |Name  |Beschreibung  |
|---------|---------|---------|
| **Anzeigeoptionen** | **Beschriftung** | Die lokalisierbare Bezeichnung für das für Benutzer sichtbare Sub-Grid. <br /><br />Diese Eigenschaft ist erforderlich.|
| **Anzeigeoptionen** |  **Name** |  Der eindeutige Name für das Sub-Grid, das bei der Referenz in Skripten verwendet wird. Der Name kann nur alphanumerische Zeichen und Unterstrichzeichen enthalten. <br /><br />Diese Eigenschaft ist erforderlich. |
| **Anzeigeoptionen** | **Auf Telefon ausblenden** |  Das Sub-Grid kann ausgeblendet werden, um eine komprimierte Version des Formulars auf Handy-Bildschirmen anzuzeigen. |
| **Anzeigeoptionen** | **Zeigen Sie Bezugsdatensätze an** |  Wenn diese Option ausgewählt ist, zeigt das Sub-Grid nur Datensätze an, die sich auf den aktuellen Datensatz beziehen, der auf dem Formular angezeigt wird. <br /><br />Die Dropdown-Liste **Entität** wird auch auf die Liste der Entitäten gefiltert, die mit der aktuellen Entität in Beziehung stehen. |
| **Anzeigeoptionen** | **Entität** |  Die Entität, deren Datensätze Sie im Sub-Grid anzeigen möchten. <br /><br />Wenn **Beziehungsdatensätze anzeigen** ausgewählt ist, wird die Liste der Entitäten gefiltert, um nur Entitäten anzuzeigen, die mit der aktuellen Entität verknüpft sind. Zusätzlich zum Entitätsnamen wird in Klammern auch der Name des Lookup-Feldes angezeigt. |
| **Anzeigeoptionen** | **Standardansicht** |  Die Ansicht der in der Eigenschaft **Entity** ausgewählten Entität, die verwendet wird, um die Liste der Datensätze im Sub-Grid abzurufen und anzuzeigen. |
| **Anzeigeoptionen** | **Erlauben Sie Benutzern, die Ansicht zu ändern**. |  Wenn ausgewählt, können App-Benutzer von der **Standardansicht** zu einer anderen Ansicht der in der **Entity**-Eigenschaft ausgewählten Entität wechseln. |
| **Anzeigeoptionen** | **Alle Ansichten anzeigen** |  Wenn diese Option ausgewählt ist, können App-Benutzer von der **Standardansicht** zu allen anderen Ansichten der Entität wechseln, die in der Eigenschaft **Entity** ausgewählt wurde. <br /><br />Diese Eigenschaft ist nur verfügbar, wenn **Benutzern erlauben, die Ansicht zu ändern** ausgewählt ist. |
| **Anzeigeoptionen** | **Ausgewählte Ansichten** |  Eine Liste von Ansichten der in der Eigenschaft **Entität** ausgewählten Entität, die App-Benutzer von der **Standardansicht** aus ändern können. <br /><br />Diese Eigenschaft ist nur verfügbar, wenn **Benutzern erlauben, die Ansicht zu ändern** ausgewählt ist und **Alle Ansichten anzeigen** gelöscht ist. |

## <a name="see-also"></a>Siehe auch
[Übersicht über den modellgestützten Formulardesigner](form-designer-overview.md)  
[Erstellen, Bearbeiten oder Konfigurieren von Formularen mit dem Formulardesigner](create-and-edit-forms.md)  
[Hinzufügen, Konfigurieren, Verschieben oder Löschen von Feldern in einem Formular](add-move-or-delete-fields-on-form.md)  
[Hinzufügen, Konfigurieren, Verschieben oder Löschen von Komponenten in einem Formular](add-move-configure-or-delete-components-on-form.md)  
[Hinzufügen, Konfigurieren, Verschieben oder Löschen von Abschnitten in einem Formular](add-move-or-delete-sections-on-form.md)  
[Hinzufügen, Konfigurieren, Verschieben oder Löschen von Registerkarten in einem Formular](add-move-or-delete-tabs-on-form.md)  
[Konfigurieren von Kopfzeileneigenschaften im Formulardesigner](form-designer-header-properties.md)  
[Hinzufügen und Konfigurieren einer Schnellansichts-Komponente in einem Formular](form-designer-add-configure-quickview.md)  
[Konfigurieren einer Suchkomponente in einem Formular](form-designer-add-configure-lookup.md)  
[Verwenden der Strukturansicht im Formulardesigner](using-tree-view-on-form.md)  
[Erstellen und Bearbeiten von Feldern](../common-data-service/create-edit-field-portal.md)  
