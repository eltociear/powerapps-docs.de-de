---
title: Script (JScript)-Webressourcen (modellgesteuerte Apps) | Microsoft Docs
description: 'Infos zum Verwenden von JavaScript-Webressourcen (JavaScript), um eine Bibliothek von JavaScript-Funktionen zu erstellen, auf die von überall aus zugegriffen werden kann.'
ms.custom: ''
ms.date: 10/31/2018
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
---
# <a name="script-jscript-web-resources"></a>Webressourcen für Skripts (JScript)

<!-- https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/script-jscript-web-resources -->

Verwenden Sie Script(JScript)-Webressourcen, um eine Bibliothek von JavaScript-Funktionen zu erstellen, auf die von überall aus zugegriffen werden kann.  
  
<a name="BKMK_capabilities"></a>   
## <a name="capabilities-of-script-web-resources"></a>Verwendungsmöglichkeiten für Script-Webressourcen  
 Mit JavaScript-Webressourcen können Sie Code, der in den Formularskripten, in Webressourcen der Webseite (HTML) oder in Menübandbefehlen, verwendet wird, leistungsfähiger verwalten, indem sie mit den freigegebenen Bibliothek der JavaScript-Funktionen verknüpft werden.  
  
<a name="BKMK_limitations"></a>   
## <a name="limitations-of-script-web-resources"></a>Einschränkungen für Skriptwebressourcen  
 Wie alle Webressourcen verwenden JavaScript-Webressourcen den Sicherheitskontext modellgestützter Apps. Nur lizenzierte Benutzer, die über die notwendigen Rechte verfügen, können darauf zugreifen.  
  
> [!NOTE]
>  Verweise, die im Code zwischen der Webressourcen enthalten sind, werden als Lösungsabhängigkeiten nicht nachverfolgt.  
  
<a name="BKMK_Using"></a>   
## <a name="using-javascript-libraries"></a>Verwenden von JavaScript-Bibliotheken  
 Weitere Informationen zum Entwickeln und Testen von JavScript-Bibliotheken sowie darüber, wie sie Menübandbefehlen und Formularereignissen zugeordnet werden, finden Sie unter [Clientskripting mit JavaScript](client-scripting.md).  
  
<a name="BKMK_Referencing"></a>   
## <a name="referencing-a-script-web-resource-from-a-webpage-web-resource"></a>Verweisen einer Skriptwebressource aus einer Webseitenwebressource  
 Alle Webressourcen können relative URLs verwenden, um aufeinander zu verweisen. Fügen Sie im folgenden Beispiel, damit die Webseitenwebressource `new_/content/contentpage.htm` auf die JavaScript-Webressource `new_/scripts/myScript.js` verweist, den folgenden HTML-Code dem Anfangselement von `new_/content/contentpage.htm` hinzu.  
  
```html  
<script type="text/jscript" src="../scripts/myScript.js"></script>  
```  
  
 Um auf ein JavaScript von einem anderen Herausgeber zu verweisen, muss der Pfad das Anpassungspräfix für diesen Hersteller einschließen. Damit beispielsweise die Seite `new_/content/contentpage.htm` die Seite `src` `MyIsv_/scripts/customscripts.js` verweist, sollte der Attributswert `../../MyIsv_/scripts/customscripts.js` angegeben werden.  
  
### <a name="see-also"></a>Siehe auch  
 [Clientskripting mit JavaScript](client-scripting.md)   
 [Webressourcen](web-resources.md)   
 [Verwenden von Webseite (HTML)-Webressourcen](webpage-html-web-resources.md)   
 [Verwenden von Stylesheet (CSS)-Webressourcen](css-web-resources.md)   
 [Verwenden von Daten (XML)-Webressourcen](data-xml-web-resources.md)   
 [Verwenden von Bild (JPG, PNG, GIF, ICO)-Webressourcen](image-web-resources.md)   
 [Verwenden von Stylesheet (XSL)-Webressourcen](stylesheet-xsl-web-resources.md)   
 [Webressourcenentwicklung mithilfe des Fiddler-AutoResponder verbessern](streamline-javascript-development-fiddler-autoresponder.md)    
