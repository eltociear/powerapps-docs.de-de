---
title: iFrame-Eigenschaften für Hauptformulare in modellgesteuerten Apps in PowerApps | MicrosoftDocs
description: Grundlegendes zur iFrame-Eigenschaften für Hauptformulare
Keywords: Hauptformular; iFrame-Eigenschaften; Dynamics 365
author: Mattp123
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
ms.author: matp
manager: kvivek
ms.date: 06/18/2018
ms.service: powerapps
ms.topic: article
ms.assetid: 1b7e6a0c-18a9-47e2-aa7d-0cffb8c93b19
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="iframe-properties-for-model-driven-app-main-forms"></a>iFrame-Eigenschaften für Hauptformulare in modellgesteuerten Apps

Sie können iFrames einem Formular hinzufügen, um Inhalt von einer anderen Website in einem Formular zu integrieren. 

Gehen Sie folgendermaßen vor, um die iFrame-Eigenschaften anzuzeigen.

1.  Melden Sie sich bei [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an.

2.  Erweitern Sie **Daten** und wählen **Entitäten**, wählen Sie die Entität aus und wählen Sie die Registerkarte **Formulare**. 

3. Öffnen Sie in der Liste der Formulare ein Formular des Typs **Haupt**. Klicken Sie dann auf der Registerkarte **Einfügen** auf IFRAME, um die IFRAME-Eigenschaft anzuzeigen.

![iFrame-Eigenschaften](media/iframe-properties.png)


> [!NOTE]
> Formulare sind nicht zur Anzeige innerhalb eines iFrames entwickelt.  
  
|Tabstopp|Eigenschaft|Beschreibung|  
|---------|--------------|-----------------|  
|**Allgemein**|**Name**|**Erforderlich**: Ein eindeutiger Name für den iFrame. Der Name kann nur alphanumerische Zeichen und Unterstrichzeichen enthalten.|  
||**URL**|**Erforderlich**: Die URL für die in dem iFrame anzuzeigende Seite.|  
||**Code des Datensatzobjekttyps und eindeutige Bezeichner als Parameter übergeben**|Daten zu der Organisation, dem Benutzer und dem Datensatz können an den iFrame übergeben werden. Weitere Informationen: [Übergeben von Parametern an iFrame](#pass-parameters-to-iframes) |  
||**Bezeichnung**|**Erforderlich**: Eine für den iFrame anzuzeigende Beschriftung.|  
||**Beschriftung im Formular anzeigen**|Ob die Beschriftung angezeigt werden soll.|  
||**Frameübergreifendes Skripting einschränken, wenn unterstützt.**|Es gilt als Sicherheitsrisiko, zuzulassen, dass Seiten von einer anderen Website über Skripts mit der Dynamics 365-Anwendung interagieren. Verwenden Sie diese Option, um frameübergreifendes Skripting für Seiten, die Sie nicht kontrollieren, zu verhindern.<br /><br />|  
||**Standardmäßig sichtbar**|Die Anzeige des iFrames ist optional und kann durch Skripts gesteuert werden. Weitere Informationen: [Sichtbarkeitsoptionen](visibility-options-legacy.md)|
||**Für mobile Nutzung aktivieren**|Wählen Sie das Kontrollkästchen aus, um den iFrame für mobile Geräte zu aktivieren.|  
|**Formatierung**|**Wählen Sie die Anzahl der Spalten, die vom Steuerelement belegt werden**|Wenn der Abschnitt, der den iFrame enthält, mehr als eine Spalte enthält, können Sie festlegen, dass das Feld die Anzahl von Spalten belegt, die der Abschnitt enthält.|  
||**Wählen Sie die Anzahl der Zeilen für das Steuerelement aus**|Sie können die Höhe des iFrames steuern, indem Sie eine Zahl von Zeilen angeben.|  
||**Automatisch erweitern, um verfügbaren Bereich auszufüllen**|Anstatt die Höhe durch eine Zahl von Zeilen anzugeben, können Sie zulassen, dass die Höhe des iFrames den verfügbaren Raum einnimmt.|  
||**Wählen Sie den Bildlauftyp für den iFrame aus**|Sie haben drei Möglichkeiten:<br /><br /> - **Nach Bedarf**: Zeigen Sie Bildlaufleisten, wenn die Größe des iFrames größer ist als der verfügbare Platz.<br />- **Immer**: Bildlaufleisten immer anzeigen.<br />- **Nie**: Bildlaufleisten nie anzeigen.|  
||**Rahmen anzeigen**|Um den iFrame einen Rand anzeigen.|  
|**Abhängigkeiten**|**Abhängige Felder**|Ein iFrame kann per Skript mit Feldern im Formular interagieren. Wenn ein Feld aus dem Formular entfernt wird, kann das Skript in dem iFrame beschädigt werden. Fügen Sie von Skripten referenzierte Felder in dem iFrame den **Abhängigen Feldern** hinzu, damit sie nicht versehentlich entfernt werden können.|  
  
## <a name="pass-parameters-to-iframes"></a>Übergeben von Parametern an iFrames  
 Informationen zum Datensatz können übergeben werden, indem Sie die Option **Datensatzobjekt-Typcode u. eindeut. Bezeichner als Parameter übergeben** aktivieren. Die übergebenen Werte sind:  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|`orglcid`|Die Organisations-Standardsprachen-LCID.|  
|`orgname`|Der Name der Organisation.|  
|`userlcid`|Die bevorzugte Sprach-LCID des Benutzers|  
|`type`|Der Entitätstypcode. Dieser Wert kann benutzerdefinierte Entitäten für in den verschiedenen Organisationen unterscheiden. Verwenden Sie stattdessen `typename`.|  
|`typename`|Der Entitätstypname.|  
|`id`|Die ID des Datensatzes dieser Parameter verfügt über keinen Wert, bis der Entitätsdatensatz gespeichert wird.|  

## <a name="next-steps"></a>Nächste Schritte

[Verwenden des Hauptformulars und seiner Komponenten](use-main-form-and-components.md)
