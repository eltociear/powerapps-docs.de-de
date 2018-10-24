---
title: Webressourceneigenschaften für modellgesteuerte App-Hauptformulare in PowerApps | Microsoft-Dokumentation
description: Informationen zu Webressourceneigenschaften für Hauptformulare
Keywords: Main form; Web resource properties; Dynamics 365
author: Mattp123
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.author: matp
manager: kvivek
ms.date: 06/27/2018
ms.service: crm-online
ms.topic: article
ms.assetid: 82cd41ea-95b0-4606-9e7d-43eb5ce9ecd6
ms.openlocfilehash: a08ca32b1d300d4302064940e65fd1d067c3ade6
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "39687482"
---
# <a name="web-resource-properties-for-model-driven-app-forms"></a>Webressourceneigenschaften für modellgesteuerte App-Formulare

Sie können Webressourcen in einem Formular hinzufügen oder bearbeiten, um es für App-Benutzer ansprechender oder nützlicher zu machen. Im Formular aktivierte Webressourcen sind Bilder oder Steuerelemente für HTML-Dateien.

> [!NOTE]
> Silverlight-Webressourcen sind veraltet und funktionieren auf dem Client mit der einheitlichen Oberfläche nicht.

## <a name="access-web-resource-properties"></a>Zugreifen auf Eigenschaften von Webressourcen

Beim Anzeigen eines Formulars:
- **Beim Hinzufügen einer Webressource**: Wählen Sie die Registerkarte aus (z.B. **Allgemein** oder **Notizen**), auf der Sie sie einfügen möchten, und wählen Sie dann auf der Registerkarte **Einfügen** die Option **Webressource** aus.<br />![Einfügen einer Webressource](media/insert-web-resource.png)
- **Beim Bearbeiten einer Webressource**: Wählen Sie eine Formularregisterkarte und die Webressource aus, die Sie bearbeiten möchten, und wählen Sie dann auf der Registerkarte **Start** die Option **Eigenschaften ändern** aus. <br />![Ändern der Eigenschaften von Webressourcen](media/web-resource-change-properties.png)

Dadurch wird das Dialogfeld **Webressource hinzufügen** oder **Webressourceneigenschaften** geöffnet.

![Dialogfeld „Webressource hinzufügen“](media/add-web-resource-dialog.png)


## <a name="web-resource-properties"></a>Webressourceneigenschaften

 Das Dialogfeld **Webressource hinzufügen** oder **Webressourceneigenschaften** enthält zwei, manchmal drei Registerkarten, je nach Art der Webressource.

### <a name="general-tab"></a>Registerkarte „Allgemein“

Diese Eigenschaften definieren die zu verwendende Webressource und ihr Verhalten.

|Feld|Beschreibung|
|--|--|
|**Webressource**|*Erforderlich.* Suchen Sie eine vorhandene Webressource, oder erstellen Sie eine neue. Verwenden Sie die Ansicht **Formular: aktivierte Webressourcen**, um nur HTML- und Bildwebressourcen aufzunehmen, die als visuelle Elemente in einem Formular hinzugefügt werden können.|
|**Name**|*Erforderlich.* Geben Sie einen Namen für das Webressourcen-Steuerelement ein, das dem Formular hinzugefügt wird. Mit diesem Wert wird das Steuerelement im Formular eindeutig identifiziert.|
|**Beschriftung**|*Erforderlich.* Wird automatisch basierend auf dem Wert im Feld **Name** generiert. Geben Sie lokalisierbaren Text für das Webressourcen-Steuerelement ein, das dem Formular hinzugefügt wird. Wählen Sie **Beschriftung im Formular anzeigen** aus, um den Text sichtbar zu machen.|
|**Standardmäßig sichtbar**|Ist diese Option aktiviert, wird die Webressource angezeigt, wenn das Formular geladen wird. Wenn Sie über eine Geschäftsregel oder ein Formularskript verfügen, um die Webressource nach Bedarf anzuzeigen, deaktivieren Sie dieses Feld. Weitere Informationen finden Sie unter [Ein- oder Ausblenden von Formularelementen](visibility-options-legacy.md)|
|**Für mobile Geräte aktivieren**|Wählen Sie diese Option aus, damit diese Webressource in mobilen Apps angezeigt wird.|

Legen Sie je nach Art der ausgewählten Webressource zusätzliche Eigenschaften fest.

Für HTML-Webressourcen werden folgende angezeigt:

![HTML-Webressourceneigenschaften](media/web-resource-general-html-properties.png)

|Feld|Beschreibung|
|--|--|
|**Benutzerdefinierte Parameter(daten)**|In der Regel Konfigurationsdaten, die als ein `data`-Abfragezeichenfolgen-Parameter an die HTML-Webressource übergeben werden. Skripts, die der HTML-Seite zugeordnet sind, können auf diese Daten zugreifen und sie verwenden, um das Verhalten der Seite zu ändern.|
|**Frameübergreifendes Skripting einschränken, wenn unterstützt**|Verwenden Sie diese Option, wenn Sie dem Inhalt in der HTML-Webressource nicht vollständig vertrauen. Weitere Informationen finden Sie unter [Dokumentation für Entwickler: Auswählen, ob frameübergreifendes Skripting eingeschränkt werden soll](/dynamics365/customer-engagement/developer/use-iframe-and-web-resource-controls-on-a-form#select-whether-to-restrict-cross-frame-scripting)|
|**Datensatzobjekt-Typcode u. eindeut. Bezeichner als Parameter übergeben**|Daten über den aktuellen Datensatz, der im Formular sichtbar ist, können an die HTML-Webressourcenseite übergeben werden, damit Skripts, die auf der Seite ausgeführt werden, auf Daten über den Datensatz zugreifen können. Weitere Informationen finden Sie unter: <br />[Übergeben von Parametern an Webressourcen](#pass-parameters-to-web-resources)<br />[Dokumentation für Entwickler: Übergeben kontextbezogener Informationen zum Datensatz](/dynamics365/customer-engagement/developer/use-iframe-and-web-resource-controls-on-a-form#pass-contextual-information-about-the-record)|

Für Bildwebressourcen haben Sie die Möglichkeit, einen **Alternativtext** anzugeben. Dies ist wichtig für Hilfstechnologien, die die Seite für alle Benutzer zugänglich machen.

<!-- TODO: Why are Custom Parameters available to pass to image web resources? -->

### <a name="formatting-tab"></a>Registerkarte „Formatierung“

Die auf der Registerkarte **Formatierung** angezeigten Optionen variieren basierend auf dem Typ der eingefügten Webressource und dem Kontext, in den sie eingefügt wird. Dazu gehören die Angabe der anzuzeigenden Anzahl von Spalten und Zeilen, die Angabe, ob ein Rahmen angezeigt wird, und das Bildlaufverhalten.

![Formatierungseigenschaften für Webressourcen](media/web-resource-formatting-properties.png)

|Eigenschaft|Beschreibung|  
|--------------|-----------------|
|**Wählen Sie die Anzahl der Spalten aus, die vom Steuerelement belegt werden**|Wenn der Abschnitt mit der Webressource mehrere Spalten enthält, können Sie die Anzahl der zu belegenden Felder bis zu der Anzahl der im Abschnitt enthaltenen Spalten festlegen.|  
|**Wählen Sie die Anzahl der Zeilen für das Steuerelement aus**|Sie können die Höhe der Webressource steuern, indem Sie eine Anzahl von Zeilen angeben oder **Automatisch erweitern, um verfügbaren Bereich auszufüllen** auswählen, damit die Höhe der Webressource in den verfügbaren Bereich erweitert werden kann.|  
|**Wählen Sie den Bildlauftyp für den IFRAME aus**|Eine HTML-Webressource wird dem Formular mithilfe eines IFRAME hinzugefügt.<br /><br /> - **Nach Bedarf**: Bildlaufleisten werden angezeigt, wenn die Größe der Webressource den verfügbaren Bereich übersteigt.<br />- **Immer**: Bildlaufleisten werden immer angezeigt.<br />- **Nie**: Bildlaufleisten werden nie angezeigt.|  
|**Rahmen anzeigen**|Zeigt einen Rahmen um die Webressource an.|  


### <a name="dependencies-tab"></a>Registerkarte „Abhängigkeiten“

Eine Webressource kann mit Feldern im Formular über ein Skript interagieren. Wenn ein Feld aus dem Formular entfernt wird, kann das Skript in der Webressource beschädigt werden. Fügen Sie alle von Skripts in der Webressource referenzierten Felder unter **Abhängige Felder** hinzu, damit sie nicht versehentlich entfernt werden können.

![Abhängigkeitseigenschaften für Webressourcen](media/web-resource-dependency-properties.png)
  
<a name="BKMK_PassingParametersToWebResource"></a> 
 
## <a name="pass-parameters-to-web-resources"></a>Übergeben von Parametern an Webressourcen 

Eine HTML-Webressource kann Parameter akzeptieren, die als Abfragezeichenfolgen-Parameter übergeben werden.  
  
Informationen zum Datensatz können übergeben werden, indem die Option **Datensatzobjekt-Typcode u. eindeut. Bezeichner als Parameter übergeben** aktiviert wird. Wenn die Informationen in das Feld **Benutzerdefinierte Parameter(daten)** eingegeben werden, werden sie mit dem Parameter „data“ übergeben. Die übergebenen Werte sind:  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|`data`|Dieser Parameter wird nur übergeben, wenn Text für **Benutzerdefinierte Parameter(daten)** angegeben wurde.|  
|`orglcid`|Die LCID der Standardsprache der Organisation.|  
|`orgname`|Der Name der Organisation.|  
|`userlcid`|Die bevorzugte Sprach-LCID des Benutzers.|  
|`type`|**Bitte nicht verwenden.** Der Typcode der Entität. Dieser numerische Wert kann für benutzerdefinierte Entitäten in verschiedenen Organisationen unterschiedlich sein. Verwenden Sie stattdessen den Typnamen der Entität.|  
|`typename`|Der Typname der Entität.|  
|`id`|Der ID-Wert des Datensatzes. Dieser Parameter erhält erst einen Wert, wenn der Datensatz der Entität gespeichert wird.|  
  
Andere Parameter sind nicht zulässig, und die Webressource wird nicht geöffnet, wenn andere Parameter verwendet werden. Wenn Sie mehrere Werte übergeben müssen, kann der Parameter „data“ überladen werden, um weitere Parameter aufzunehmen.

Weitere Informationen finden Sie unter [Dokumentation für Entwickler: Übergeben kontextbezogener Informationen zum Datensatz](/dynamics365/customer-engagement/developer/use-iframe-and-web-resource-controls-on-a-form#pass-contextual-information-about-the-record)

### <a name="see-also"></a>Siehe auch

[Erstellen oder Bearbeiten von Webressourcen, um eine App zu erweitern](create-edit-web-resources.md)<br />
[Verwenden des Hauptformulars und seiner Komponenten](use-main-form-and-components.md)
