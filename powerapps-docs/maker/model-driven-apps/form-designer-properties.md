---
title: Im Formulardesigner verfügbare Eigenschaften | MicrosoftDocs
ms.custom: ''
ms.date: 08/26/2019
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
- Power Apps maker portal impact
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 7a30c6b59b5426cea7fc265112ac24ebe8efd36d
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2019
ms.locfileid: "2868113"
---
# <a name="properties-available-in-the-form-designer"></a>Im Formulardesigner verfügbare Eigenschaften

Im rechten Bereich des modellgetriebenen Formular-Designers können Sie im Eigenschaftsbereich die Eigenschaften eines beliebigen Elements, das in der Vorschau oder in der Baumansicht ausgewählt wurde, schnell anzeigen und aktualisieren. 

> [!div class="mx-imgBorder"] 
> ![](media/form-designer-property-pane.png "Form designer property pane")

## <a name="form-properties"></a>Formulareigenschaften

|Name  |Beschreibung  |
|---------|---------|
|**Titel**     | Geben Sie einen Namen ein, der für Benutzer sinnvoll ist. Dieser Name wird bei Auswahl des Formulars angezeigt. Wenn mehrere für die Entität konfigurierte Formulare verwendet werden können, wird dieser Name verwendet, um verschiedene Formulare voneinander zu unterscheiden. <br /> Diese Eigenschaft ist erforderlich.        |
|**Beschreibung**     |  Geben Sie eine Beschreibung ein, die erläutert, wodurch sich dieses Formular von anderen Hauptformularen unterscheidet. Diese Beschreibung wird nur in der Liste der Formulare für eine Entität im Lösungs-Explorer angezeigt.        |
|**Maximale Breite**     | Legen Sie eine maximale Breite (in Pixeln) fest, um die Breite des Formulars zu beschränken. Der Standardwert ist 1900. <br /> Diese Eigenschaft ist erforderlich.       |
|**Bild anzeigen**      | Zeigen Sie das **Primäre Bild** der Entität an, falls eins festgelegt wurde. Mit dieser Einstellung kann das Bildfeld in der Überschrift dieses Formulars angezeigt werden. <br /> Siehe Aktivieren oder Deaktivieren von Entitätsoptionen für weitere Informationen zu Entitätsoptionen.         |


## <a name="tab-properties"></a>Eigenschaften der Registerkarte

|Fläche   |Name  |Beschreibung  |
|---------|---------|---------|
|**Anzeigeoptionen**      | **Registerkartenbeschriftung**      | Die lokalisierbare Beschriftung für die Registerkarte, die für Benutzer sichtbar ist. <br /> Diese Eigenschaft ist erforderlich.         |
| **Anzeigeoptionen**      |  **Name**     |  Der eindeutige Name für die Registerkarte, der verwendet wird, wenn auf sie in Skripts verwiesen wird. Der Name kann nur alphanumerische Zeichen und Unterstrichzeichen enthalten. <br />Diese Eigenschaft ist erforderlich.      |
| **Anzeigeoptionen**      |  **Registerkarte standardmäßig erweitern**      |  Der Status der Registerkarte kann durch Formularskripts oder durch Klicken auf die Beschriftung zwischen erweitert und reduziert gewechselt werden. Wählen Sie den Standardstatus für die Registerkarte.       |
| **Anzeigeoptionen**      | **Registerkarte ausblenden**     | Wenn diese Option ausgewählt ist, wird die Registerkarte standardmäßig ausgeblendet und kann mithilfe von Code angezeigt werden.       |
| **Anzeigeoptionen**      | **Auf Telefon ausblenden**     |  Um eine verkürzte Version dieses Formulars auf Smartphone-Bildschirmen anzuzeigen, können Registerkarten ausgeblendet werden.     |
| **Formatierung**   | **Layout**     |  Registerkarten können bis zu drei Spalten haben. Verwenden Sie diese Optionen, um die Anzahl der Spalten festzulegen, sowie, welchen Prozentsatz der gesamten Breite sie ausfüllen sollen.      |


## <a name="section-properties"></a>Abschnittseigenschaften

|Fläche   |Name  |Beschreibung  |
|---------|---------|---------|
|**Anzeigeoptionen**      | **Abschnittsbeschriftung**    | Die lokalisierbare Beschriftung für den Abschnitt, die für Benutzer sichtbar ist. <br /> Diese Eigenschaft ist erforderlich.      |
|**Anzeigeoptionen**      | **Name**    | Der eindeutige Name für den Abschnitt, der verwendet wird, wenn auf sie in Skripts verwiesen wird. Der Name kann nur alphanumerische Zeichen und Unterstrichzeichen enthalten. <br /> Diese Eigenschaft ist erforderlich.        |
|**Anzeigeoptionen**      | **Beschriftung ausblenden**   |  Wenn diese Option ausgewählt ist, wird die Abschnittsbeschriftung ausgeblendet.  |
|**Anzeigeoptionen**      | **Auswahl sperren**    | Sperren Sie diesen Abschnitt, damit er nicht entfernt werden kann.      |
|**Anzeigeoptionen**      | **Abschnitt auswählen**     | Wenn diese Option ausgewählt ist, wird der Abschnitt standardmäßig ausgeblendet und kann mithilfe von Code angezeigt werden.      |
|**Anzeigeoptionen**      | **Auf Telefon ausblenden**     |  Um eine verkürzte Version dieses Formulars auf Smartphone-Bildschirmen anzuzeigen, können Abschnitte ausgeblendet werden.     |
|**Formatierung**     |  **Spalten**    |  Geben Sie maximal vier Spalten für den Abschnitt an.      |

## <a name="field-properties"></a>Feldeigenschaften

|Fläche  |Name  |Beschreibung  |
|---------|---------|---------|
|**Anzeigeoptionen**     | **Feldbeschriftung**    | Standardmäßig entspricht die Beschriftung dem Anzeigenamen des Felds. Sie können diesen Namen für das Formular überschreiben, indem Sie hier eine andere Beschriftung eingeben.       |
|**Anzeigeoptionen**     |  **Feldname**    | Der Name des Felds. Dieser kommt von den Feldeigenschaften der Entität und ist schreibgeschützt.     |
|**Anzeigeoptionen**     | **Beschriftung ausblenden**     | Wenn diese Option ausgewählt ist, wird die Feldbeschriftung ausgeblendet.      |
|**Anzeigeoptionen**     | **Schreibgeschütztes Feld**    | Wenn diese Option ausgewählt ist, kann der Feldwert nicht bearbeitet werden.      |
|**Anzeigeoptionen**     |  **Feld sperren**   |  Sperren Sie dieses Feld, damit es nicht entfernt werden kann.     |
|**Anzeigeoptionen**     |  **Feld ausblenden**     | Wenn diese Option ausgewählt ist, wird das Feld standardmäßig ausgeblendet und kann mithilfe von Code angezeigt werden.      |
|**Anzeigeoptionen**     |  **Auf Telefon ausblenden**    | Um eine verkürzte Version dieses Formulars auf Smartphone-Bildschirmen anzuzeigen, können Felder ausgeblendet werden.         |
|**Formatierung**     | **Feldbreite**      |  Wenn der Abschnitt, der die Felder enthält, mehr als eine Spalte enthält, können Sie festlegen, dass das Feld die Anzahl von Spalten belegt, die der Abschnitt enthält.       |

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
