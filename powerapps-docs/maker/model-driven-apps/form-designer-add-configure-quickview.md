---
title: Hinzufügen und Konfigurieren einer Schnellansichtskomponente in einem Formular | MicrosoftDocs
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

# <a name="add-and-configure-a-quick-view-component-on-a-form"></a>Hinzufügen und Konfigurieren einer Schnellansichtskomponente in einem Formular  
Ein Hauptformular, das die Details eines Datensatzes anzeigt, kann mit einer Schnellansichtskomponente schreibgeschützte Details eines Bezugsdatensatzes (Lookup) anzeigen. Die von der Schnellansichtskomponente angezeigten Daten werden durch die Schnellansichtsform der zugehörigen Entität definiert. Wenn es keinen Bezugsdatensatz gibt, z.B. eine Nachschlage, wird die Schnellansichtskomponente automatisch ausgeblendet.

## <a name="add-a-quick-view-component"></a>Hinzufügen einer Schnellansichtskomponente
Sie fügen eine Schnellansichtskomponente auf die gleiche Weise hinzu wie jede andere Komponente. Mehr Informationen: [Komponenten auf einem Formular hinzufügen, konfigurieren, verschieben oder löschen](add-move-configure-or-delete-components-on-form.md)

## <a name="configure-a-quick-view-component"></a>Konfigurieren einer Schnellansichtskomponente
Dies sind die Eigenschaften, die bei der Verwendung einer Schnellansichtskomponente auf einem Formular mit dem Formulardesigner konfiguriert werden können.


<!--note from editor: "Drop-down" should be used only as an adjective. In the following table, is it a list? A menu? (It's used three times in line 44.) --> 


|Fläche   |Name  |Beschreibung  |
|---------|---------|---------|
|**Anzeigeoptionen** | **Beschriftung** | Das lokalisierbare Label für die für Benutzer sichtbare Schnellansicht. <br /><br /> Diese Eigenschaft ist erforderlich. |
| **Anzeigeoptionen** | **Name** |  Der eindeutige Name für die Schnellansicht, die beim Referenzieren in Skripten verwendet wird. Der Name kann nur alphanumerische Zeichen und Unterstrichzeichen enthalten. <br /> <br />Diese Eigenschaft ist erforderlich. |
| **Anzeigeoptionen**  | **Beschriftung ausblenden** |  Wenn diese Option ausgewählt ist, ist das Schnellansichts-Label ausgeblendet. |
| **Anzeigeoptionen**  | **Schnellansichtsformulare** |  Eine Liste von Schnellansichtsformularen, die App-Benutzern angezeigt werden. <br /><br />So konfigurieren Sie die Liste der Schnellansichtsformulare <br /><br /> Wählen Sie **Formulare auswählen ...**, und wählen Sie dann in der Dropdown-Liste **Lookup** ein Lookup-Feld aus, in dem Sie ein Schnellansichtsformular anzeigen möchten. <br /><br />Abhängig von dem Nachschlagefeld, das Sie in der Dropdown-Liste **Lookup** auswählen, werden Dropdown-Listen angezeigt, mit denen Sie Schnellansichtsformulare für ein oder mehrere Objekte auswählen können. |

## <a name="see-also"></a>Siehe auch
[Übersicht über den modellgestützten Formulardesigner](form-designer-overview.md)  
[Erstellen, Bearbeiten oder Konfigurieren von Formularen mit dem Formulardesigner](create-and-edit-forms.md)  
[Hinzufügen, Konfigurieren, Verschieben oder Löschen von Feldern in einem Formular](add-move-or-delete-fields-on-form.md)  
[Hinzufügen, Konfigurieren, Verschieben oder Löschen von Komponenten in einem Formular](add-move-configure-or-delete-components-on-form.md)  
[Hinzufügen, Konfigurieren, Verschieben oder Löschen von Abschnitten in einem Formular](add-move-or-delete-sections-on-form.md)  
[Hinzufügen, Konfigurieren, Verschieben oder Löschen von Registerkarten in einem Formular](add-move-or-delete-tabs-on-form.md)  
[Konfigurieren von Kopfzeileneigenschaften im Formulardesigner](form-designer-header-properties.md)  
[Hinzufügen und Konfigurieren einer Unterraster-Komponente in einem Formular](form-designer-add-configure-subgrid.md)  
[Konfigurieren einer Suchkomponente in einem Formular](form-designer-add-configure-lookup.md)  
[Verwenden der Strukturansicht im Formulardesigner](using-tree-view-on-form.md)  
[Erstellen und Bearbeiten von Feldern](../common-data-service/create-edit-field-portal.md)  
