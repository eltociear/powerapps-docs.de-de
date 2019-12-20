---
title: Webressourceneigenschaften für Hauptformulare in modellgesteuerten Apps in Power Apps | Microsoft-Dokumentation
description: Grundlegendes zur Webressourceneigenschaften für Hauptformulare
Keywords: Hauptformular; Webressourceneigenschaften; Dynamics 365
author: Mattp123
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.author: matp
manager: kvivek
ms.date: 04/03/2019
ms.service: powerapps
ms.topic: article
ms.assetid: 82cd41ea-95b0-4606-9e7d-43eb5ce9ecd6
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 7784c70c2559aeecb5fabb7f44efdfc644f55b33
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2019
ms.locfileid: "2867453"
---
# <a name="web-resource-properties-for-model-driven-app-forms"></a>Webressourceneigenschaften für modellgesteuerte App-Formulare

Webressourcen können Sie in einem Formular hinzufügen oder bearbeiten, um sie für mehr App-Benutzer anziehend oder nützlich zu gestalten. Formularfähige Webressourcen sind Bilder oder HTML-Dateien Steuerelemente.

> [!NOTE]
> Silverlight-Webressourcen sind veraltet und funktionieren nicht im Client der Einheitlichen Oberfläche.

## <a name="access-web-resource-properties"></a>Zugriff auf Webressourceneigenschaften

Beim Anzeigen eines Formulars:
- **Um eine Webressource hinzuzufügen:**: Wählen Sie die Registerkarte aus (beispielsweise **Allgemein** oder **Notizen**), auf der Sie die Webressource einfügen möchten, und wählen Sie dann auf der Registerkarte **Einfügen** die Option **Webressource** aus.<br />![Webressource einfügen](media/insert-web-resource.png)
- **Zum Bearbeiten einer Webressource**: Wählen Sie eine Formularregisterkarte und die zu bearbeitende Webressource aus, und wählen Sie dann auf der Registerkarte **Start** die Option **Eigenschaften ändern** aus. <br />![Webressourceneigenschaften ändern](media/web-resource-change-properties.png)

Dadurch wird das Dialogfeld **Webressource hinzufügen** oder **Webressourceneigenschaften** geöffnet.

![Webressource-Dialog hinzufügen](media/add-web-resource-dialog.png)

> [!IMPORTANT]
> Sie müssen die Option **Standardmäßig sichtbar** auswählen, damit die Webressource im Formular erscheint und für Benutzer zur Verfügung steht.

## <a name="web-resource-properties"></a>Eigenschaften von Webressourcen

 Das Dialogfeld **Webressource hinzufügen** oder **Webressourceneigenschaften** hat zwei, manchmal drei Registerkarten, je nach Art der Webressource.

### <a name="general-tab"></a>Registerkarte "Allgemein"

Diese Eigenschaften definieren die zu verwendende Webressource und wie sie sich verhalten soll.

|Feld|Beschreibung|
|--|--|
|**Webressource**|*Erforderlich.* Suchen Sie eine bestehende Webressource oder erstellen Sie eine neue. Verwenden Sie die Ansicht **Formularfähige Webressourcen**, um nur HTML- und Bild-Webressourcen aufzunehmen, die als visuelle Elemente in ein Formular eingefügt werden können.|
|**Name**|*Erforderlich.* Geben Sie einen Namen für das Webressource-Steuerelement an, das dem Formular hinzugefügt wird. Dieser Wert identifiziert eindeutig das Steuerelement im Formular.|
|**Bezeichnung**|*Erforderlich.* Wird automatisch auf Basis des Feldwertes **Name** generiert. Geben Sie einen lokalisierbaren Text für das Webressource-Steuerelement an, das dem Formular hinzugefügt wird. Wählen Sie **Beschriftung im Formular anzeigen** aus, wenn Sie dieses sichtbar machen möchten.|
|**Standardmäßig sichtbar**|Solange dies aktiviert ist, wird die Web-Ressource beim Laden des Formulars sichtbar sein. Wenn Sie eine Geschäftsregel oder ein Formularskript haben, das die Webressource bei Bedarf anzeigt, deaktivieren Sie dieses Feld. Weitere Informationen: [Anzeigen oder Ausblenden von Formularelementen](visibility-options-legacy.md)|
|**Für mobile Nutzung aktivieren**|Wählen Sie diese Option, um diese Web-Ressource in mobilen Apps sichtbar zu machen.|

Je nachdem, welche Art von Webressource Sie auswählen, legen Sie zusätzliche Eigenschaften fest.

Für HTML-Webressourcen werden diese angezeigt:

![HTML-Webressourceneigenschaften](media/web-resource-general-html-properties.png)

|Feld|Beschreibung|
|--|--|
|**Benutzerdefinierte Parameter(daten)**|Normalerweise Konfigurationsdaten, die der HTML-Webressource als `data` Abfragezeichenfolgenparameter übergeben werden . Skripte, die der HTML-Seite zugeordnet sind, können auf diese Daten zugreifen und damit das Verhalten der Seite ändern.|
|**Frameübergreifendes Skripting einschränken, wenn unterstützt.**|Verwenden Sie diese Option, wenn Sie dem Inhalt der HTML-Webressource nicht vollständig vertrauen. Weitere Informationen: [: Dokumentation für Entwickler: Wählen Sie aus, ob frameübergreifendes Skripting eingeschränkt werden soll](/dynamics365/customer-engagement/developer/use-iframe-and-web-resource-controls-on-a-form#select-whether-to-restrict-cross-frame-scripting)|
|**Code des Datensatzobjekttyps und eindeutigen Bezeichner als Parameter übergeben**|Daten über den aktuellen Datensatz, die im Formular sichtbar sind, können an die HTML-Webressourcenseite übergeben werden, so dass das auf der Seite laufende Skript auf Daten über den Datensatz zugreifen kann. Weitere Informationen: <br />[Parameter an Webressourcen übergeben](#pass-parameters-to-web-resources)<br />[Dokumentation für Entwickler: Übergeben kontextbezogener Informationen zum Datensatz](/dynamics365/customer-engagement/developer/use-iframe-and-web-resource-controls-on-a-form#pass-contextual-information-about-the-record)|

Für Bildwebressourcen haben Sie die Möglichkeit, **Alternativen Text** anzugeben, was für assistive Technologien wichtig ist, die die Seite für jeden zugänglich machen.

<!-- TODO: Why are Custom Parameters available to pass to image web resources? -->

### <a name="formatting-tab"></a>Registerkarte Formatierung

Auf der Registerkarte **Formatierung** basieren die Optionen auf dem Typ der eingefügten Webressource dem Kontext, in dem sie eingefügt wird. Diese Optionen umfassen das Angeben der Anzahl der angezeigten Spalten und Zeilen, das Anzeigen eines Rahmens sowie das Bildlaufverhalten.

![Eigenschaften zur Formatierung von Webressourcen](media/web-resource-formatting-properties.png)

|Eigenschaft|Beschreibung|  
|--------------|-----------------|
|**Wählen Sie die Anzahl der Spalten, die vom Steuerelement belegt werden**|Wenn der Abschnitt, der die Webressource enthält, mehr als eine Spalte enthält, können Sie festlegen, dass das Feld die Anzahl von Spalten belegt, die der Abschnitt enthält.|  
|**Wählen Sie die Anzahl der Zeilen für das Steuerelement aus**|Sie können die Höhe der Webressource steuern, indem Sie eine Anzahl von Zeilen angeben oder **Automatisch erweitern, um den verfügbaren Bereich auszufüllen** auswählen, um die Höhe der Webressource auf den verfügbaren Speicherplatz zu erweitern.|  
|**Wählen Sie den Bildlauftyp für den IFRAME aus**|Dem Formular wird eine HTML-Webressource mit einem IFRAME hinzugefügt.<br /><br /> - **Nach Bedarf**: Zeigen Sie Bildlaufleisten, wenn die Größe der Webressource größer ist als der verfügbare Platz.<br />- **Immer**: Bildlaufleisten immer anzeigen.<br />- **Nie**: Bildlaufleisten nie anzeigen.|  
|**Rahmen anzeigen**|Um die Webressource einen Rand anzeigen.|  


### <a name="dependencies-tab"></a>Registerkarte Abhängigkeiten

Eine Webressource kann per Skript mit Feldern im Formular interagieren. Wenn ein Feld aus dem Formular entfernt wird, kann das Skript in der Webressource beschädigt werden. Fügen Sie von Skripten referenzierte Felder in der Webressource den **Abhängigen Feldern** hinzu, damit sie nicht versehentlich entfernt werden können.

![Webressourcenabhängigkeitseigenschaften](media/web-resource-dependency-properties.png)
  
<a name="BKMK_PassingParametersToWebResource"></a> 
 
## <a name="pass-parameters-to-web-resources"></a>Parameter an Webressourcen übergeben 

Eine HTML-Webressource kann Parameter annehmen, die als Abfragezeichenfolgenparameter übergeben werden.  
  
Informationen zum Datensatz können übergeben werden, indem Sie die Option **Datensatzobjekt-Typcode u. eindeut. Bezeichner als Parameter übergeben** aktivieren. Wenn Informationen in das Feld **Benutzerdefinierte Parameter(daten)** eingegeben werden, werden sie mithilfe des Datenparameters übergeben. Die übergebenen Werte sind:  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|`data`|Dieser Parameter wird nur übergeben, wenn Text für **Benutzerdefinierte Parameter(daten)** bereitgestellt wird.|  
|`orglcid`|Die Organisations-Standardsprachen-LCID.|  
|`orgname`|Der Name der Organisation.|  
|`userlcid`|Die bevorzugte Sprach-LCID des Benutzers|  
|`type`|**Verwenden Sie dies nicht.** Der Entitätstypcode. Dieser numerische Wert kann für benutzerdefinierte Entitäten in verschiedenen Organisationen unterschiedlich sein. verwenden Sie stattdessen den Namen des Entitätstyps.|  
|`typename`|Der Entitätstypname.|  
|`id`|Die ID des Datensatzes Dieser Parameter verfügt über keinen Wert, bis der Datensatz gespeichert wird.|  
  
Alle anderen Parameter sind nicht zulässig, und die Webressource wird nicht geöffnet, wenn andere Parameter verwendet werden. Wenn Sie mehrere Werte übergeben müssen, kann der Datenparameter überladen werden, um mehr Parameter zu enthalten.

Weitere Informationen: [Dokumentation für Entwickler: Übergeben kontextbezogener Informationen zum Datensatz](/dynamics365/customer-engagement/developer/use-iframe-and-web-resource-controls-on-a-form#pass-contextual-information-about-the-record)

### <a name="see-also"></a>Siehe auch

[Erstellen oder Bearbeiten von Webressourcen, um eine App zu erweitern](create-edit-web-resources.md)<br />
[Verwenden des Hauptformulars und seiner Komponenten](use-main-form-and-components.md)
