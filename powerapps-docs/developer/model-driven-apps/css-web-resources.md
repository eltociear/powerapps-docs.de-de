---
title: CSS Webressourcen (modellgesteuerte Apps) | Microsoft Docs
description: 'Verwendet Cascading Stylesheets (CSS), um Stylesheets zur Verwendung in Webseitenwebressourcen zu erstellen. '
keywords: ''
ms.date: 10/31/2018
ms.service:
  - powerapps
ms.custom:
  - ''
ms.topic: article
ms.assetid: a4e98fa7-930d-e320-5384-9f773775639b
author: JimDaly
ms.author: jdaly
manager: shilpas
ms.reviewer: null
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---

# <a name="css-web-resources"></a>CSS Webressourcen

<!-- https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/css-web-resources -->

Verwendet Cascading Stylesheets (CSS), um Stylesheets zur Verwendung in Webseitenwebressourcen zu erstellen.  
  
## <a name="capabilities-of-css-web-resources"></a>Funktionen von CSS-Webressourcen  
 Mit CSS-Webressourcen können Sie die Darstellung der Webseitenwebressourcen verwalten, indem Sie sie mit einer freigegebenen Bibliothek mit CSS-Formaten verknüpfen.  
  
### <a name="limitations-of-css-web-resources"></a>Einschränkungen von CSS-Webressourcen  
 Wie alle Webressourcen sind CSS-Webressourcen nur im entsprechenden Sicherheitskontext verfügbar. Nur lizenzierte Benutzer, die über die notwendigen Rechte verfügen, können darauf zugreifen.
  
## <a name="referencing-a-style-sheet-web-resource-from-a-webpage-web-resource"></a>Auf eine Stylesheetwebressource aus einer Webseitenwebressource verweisen  
 Alle Webressourcen können relative URLs verwenden, um aufeinander zu verweisen. Im folgenden Beispiel wird der Webseitenwebressource `sample_/content/contentpage.htm`, um auf die Stylesheetwebressource `sample_/styles/styles.css` zu verweisen, das folgende Beispiel dem Anfangselement von sample_ /content/contentpage.htm hinzugefügt:  
  
```html  
<link rel="stylesheet" type="text/css" href="../styles/styles.css" />  
```  
  
 Um auf ein Stylesheet von einem anderen Herausgeber zu verweisen, muss der Pfad den Lösungsherausgeberanpassungspräfix enthalten. Beispielsweise für die Seite `sample_/content/contentpage.htm`, um auf die Seite `MyIsv_/styles/styles.css` zu verweisen, wobei der href-Parameterwert `../../MyIsv_/styles/styles.css` sein sollte.  
  
> [!NOTE]
>  Verweise, die im Code zwischen der Webressourcen enthalten sind, werden als Lösungsabhängigkeiten nicht nachverfolgt.  
  
### <a name="see-also"></a>Siehe auch  
 [Webressourcen](web-resources.md)   
 [Verwenden von Webseite (HTML)-Webressourcen](webpage-html-web-resources.md)   
 [Verwenden von Webressourcen für Skripts (JScript)](script-jscript-web-resources.md)   
 [Verwenden von Daten (XML)-Webressourcen](data-xml-web-resources.md)   
 [Verwenden von Bild (JPG, PNG, GIF, ICO)-Webressourcen](image-web-resources.md)   
 [Verwenden von Silverlight (XAP)-Webressourcen](/dynamics365/customer-engagement/developer/silverlight-xap-web-resources)  
 [Verwenden von Stylesheet (XSL)-Webressourcen](stylesheet-xsl-web-resources.md)   
 [WebResource-Entität](../common-data-service/reference/entities/webresource.md)