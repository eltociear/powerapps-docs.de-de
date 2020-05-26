---
title: CSS-Webressourcen (modellgesteuerte Apps) | Microsoft Docs
description: 'Verwenden Sie Cascading Stylesheets (CSS)-Webressourcen, um Stylesheets zur Verwendung in Webseiten-Webressourcen zu erstellen. '
keywords: ''
ms.date: 10/31/2018
ms.service: powerapps
ms.topic: article
ms.assetid: a4e98fa7-930d-e320-5384-9f773775639b
author: Nkrb
ms.author: nabuthuk
manager: shilpas
ms.reviewer: ''
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 7a6b628c1c59de02078f96abf3a46abe21e446cf
ms.sourcegitcommit: 4a88daac42180283314f6bedee3d6810fd5a6c25
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/21/2020
ms.locfileid: "3275826"
---
# <a name="css-web-resources"></a>CSS Webressourcen

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/css-web-resources -->

Verwenden Sie Cascading Stylesheets (CSS)-Webressourcen, um Stylesheets zur Verwendung in Webseiten-Webressourcen zu erstellen.  
  
## <a name="capabilities-of-css-web-resources"></a>Funktionen von CSS-Webressourcen  
 Mit CSS-Webressourcen können Sie die Darstellung der Webseiten-Webressourcen verwalten, indem Sie sie mit einer freigegebenen Bibliothek mit CSS-Formaten verknüpfen.  
  
### <a name="limitations-of-css-web-resources"></a>Einschränkungen von CSS-Webressourcen  
 Wie alle Webressourcen sind CSS-Webressourcen nur im Sicherheitskontext verfügbar. Nur lizenzierte Benutzer, die über die notwendigen Rechte verfügen, können darauf zugreifen.
  
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
 [Verwendung von Web-Seiten (HTML) Web-Ressourcen](webpage-html-web-resources.md)   
 [Benutzung von Skript (JScript)-Webressourcen](script-jscript-web-resources.md)   
 [Verwenden von Daten (XML) Web-Ressourcen](data-xml-web-resources.md)   
 [Verwendung von Bildern (JPG, PNG, GIF) Web-Ressourcen](image-web-resources.md)   
 [Benutzung von Silverlight (XAP)-Webressourcen](/dynamics365/customer-engagement/developer/silverlight-xap-web-resources)  
 [Verwendung von Stylesheet (XSL)-Webressourcen](stylesheet-xsl-web-resources.md)   
 [WebResource-Entität](../common-data-service/reference/entities/webresource.md)
