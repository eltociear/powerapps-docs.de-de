---
title: Webbildressourcen (modellgesteuerte Apps) | Microsoft Docs
description: Infos zu Bildwebressourcen, um Bilder zur Verwendung bereitzustellen.
ms.custom: ''
ms.date: 03/11/2020
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: KumarVivek
ms.author: kvivek
manager: shilpas
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: a55cebde012018b68aac06cf144e1b91a9e065f5
ms.sourcegitcommit: 4a88daac42180283314f6bedee3d6810fd5a6c25
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/21/2020
ms.locfileid: "3275930"
---
# <a name="image-web-resources"></a>Image-Webressourcen

Verwenden Sie Bild-Webressourcen, um Bilder zur Verwendung in modellbasierten Apps verfügbar zu machen.  

Es gibt 5 Arten von Bild-Webressourcen: 
* PNG-Format
* JPG-Format
* GIF-Format
* ICO-Format
* Vektorformat (SVG)

> [!NOTE]
> Mit den modellbasierten Apps wurden Webressourcen im Vektorformat (SVG) hinzugefügt.

  
<a name="BKMK_Capabilities"></a>   
## <a name="capabilities-of-image-web-resources"></a>Verwendungsmöglichkeiten für Bildwebressourcen  
 Mithilfe von BWebressourcen können Sie Bilder dort hinzufügen, wo sie benötigt werden. Zu den häufigen Verwendungsweisen gehören:  
  
- Benutzerdefinierte Entitätssymbole  
- Symbole für benutzerdefinierte Menüband-Steuerelemente und `SiteMap`-Unterbereiche  
- Dekorative Grafiken für Entitätsformulare und Webseiten-Webressourcen  
- Hintergrundbilder, die von CSS-Webressourcen verwendet werden  

Verwenden Sie Vektorformat (SVG)-Webressourcen für alle Symbole, die in der Anwendung angezeigt werden. Vektorbilder werden als skalierbare Vektorgrafiken (Scalable Vector Graphics, SVG), ein XML-basiertes Vektorbildformat, definiert. Der Vorteil von Vektorbildern gegenüber anderen Bildwebressourcen ist ihre Skalierbarkeit. Sie können ein Vektorbild definieren und es wiederverwenden, anstatt Bilder in mehreren Größen zu bereitzustellen. Sie verwenden diese mit einer neuen <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata>.<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.IconVectorName> Eigenschaft zum Definieren des Symbols einer benutzerdefinierten Entität anstelle der `IconLargeName`, `IconMediumName` oder `IconSmallName`-Eigenschaften.

> [!NOTE]
> Vektorformat (SVG)-Webressourcen werden wie [Skript (JScript)](/powerapps/developer/model-driven-apps/script-jscript-web-resources)-Webressourcen behandelt und weisen die gleichen Sicherheitsrisiken wie Skript (JScript)-Webressourcen auf, da SVG-Dateien das Einbetten von JScript ermöglichen.
  
<a name="BKMK_Limitations"></a>   
## <a name="limitations-of-image-web-resources"></a>Einschränkungen von Bildwebressourcen  
 Wie alle Webressourcen verwenden Bildwebressourcen den Sicherheitskontext. Nur lizenzierte Benutzer, die über die notwendigen Rechte verfügen, können darauf zugreifen.  
 
  
<a name="BKMK_ReferenceFromWebPageWebResource"></a>   
## <a name="reference-an-image-web-resource-from-a-webpage-web-resource"></a>Verweisen einer Bildwebressource aus einer Webseitenwebressource  
 Alle Webressourcen können relative URLs verwenden, um aufeinander zu verweisen. Im folgenden Beispiel, für die Webseite (HTML)-Webressource new_/content/contentpage.htm, um auf die Bildwebressource new_/Images/image1.png zu verweisen, fügen Sie den folgenden HTML-Code hinzu zu new_/content/contentpage.htm:  
  
```html  
<img src="../Images/image1.png" />  
```  
  
<a name="BKMK_ReferenceFromForm"></a>   
## <a name="reference-an-image-web-resource-from-a--form"></a>Verweisen Sie auf eine Bildwebressource aus einem -Formular  
  
#### <a name="add-an-image-to-an-entity-form"></a>Hinzufügen eines Bilds zu einem Entitätsformular  
  
1.  Wechseln Sie zum Formular-Editor für eine Entität.  
  
2.  Wählen Sie wo in dem Formular Sie das Bild hinzufügen möchten.  
  
3.  Klicken Sie auf der Registerkarte **Einfügen** auf **Webressource**.  
  
4.  Wählen Sie auf der Registerkarte **Allgemein** das Webressourcenbild aus, das Sie hinzufügen möchten.  
  
5.  Geben Sie einen Namen für die Webressource an. Sie können auch ein Etikett und einen Alternativtext angeben.  
  
6.  Auf der Registerkarte **Formatieren** können Sie Folgendes definieren:  
  
    -   Die Anzahl der Spalten, die die Bilder verwenden sollen.  
  
    -   Die Anzahl der Zeilen, die die Bilder verwenden sollen, oder ob der verfügbare Platz automatisch erweitert werden soll.  
  
    -   Die Größe des Bildes, anhand der folgenden Optionen:  
  
        - **Strecken**  
  
        - **Strecken (Seitenverhältnis beibehalten)**  
  
        - **Original**  
  
        - **Specific**  
  
    -   Wenn Sie "Spezifisch" auswählen, können Sie die gewünschte Höhe und Breite in Pixeln angeben.  
  
7.  Klicken Sie auf **OK**.  
  
8.  Sie müssen Ihre Änderungen speichern und das Formular veröffentlichen, bevor Benutzer das Bild in dem Formular sehen können.  
  
<a name="BKMK_ReferenceWithWebResourcedirective"></a>   
## <a name="reference-an-image-web-resource-from-a-ribbon-element-or-from-the-site-map-subarea"></a>Verweisen auf eine Bildwebressource von einem Menübandelement oder aus dem Siteübersichtsunterbereich  
 Verwenden Sie die `$webresource:`-Direktive zur Angabe eines Webressourcenbild anzugeben zur Verwendung als Symbol im Menüband oder in der Anwendungsnavigation mit SiteMap. Das folgende Beispiel zeigt, wie Symbole für eine Schaltfläche auf dem Menüband angegeben werden.  
  
```xml  
<Button Id="MyISV.opportunity.form.actions.FlyoutAnchor.Button.1" Image16by16="$webresource:new_/icons/oneIcon16.png" Image32by32="$webresource:new_/icons/oneIcon32.png"/>  
```  
  
> [!NOTE]
> Die Verwendung der `$webresource:`-Direktive fügt eine Lösungsabhängigkeit hinzu, die verhindert, dass die referenzierten Bildwebressourcen gelöscht werden, solange sie von einer anderen Lösungskomponente verwendet werden.  
  
### <a name="see-also"></a>Siehe auch  
 [Webressourcen](web-resources.md)   
 [Verwendung von Web-Seiten (HTML) Web-Ressourcen](webpage-html-web-resources.md)   
 [Verwendung von Style Sheet (CSS) Webressourcen](css-web-resources.md)   
 [Benutzung von Skript (JScript)-Webressourcen](script-jscript-web-resources.md)   
 [Verwenden von Daten (XML) Web-Ressourcen](data-xml-web-resources.md)   
 [Benutzung von Silverlight (XAP)-Webressourcen](/dynamics365/customer-engagement/developer/silverlight-xap-web-resources)  
 [Verwendung von Stylesheet (XSL)-Webressourcen](stylesheet-xsl-web-resources.md)
