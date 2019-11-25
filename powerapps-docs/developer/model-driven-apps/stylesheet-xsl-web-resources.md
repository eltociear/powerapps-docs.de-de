---
title: Stylesheet (XSL)-Webressourcen (modellgesteuerte Apps) | Microsoft Docs
description: Infos zur Verwendung von Stylesheet (XSL) Webressourcen zum Umwandeln von XML-Daten.
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
ms.openlocfilehash: 4b4c0145cae08ecc144c48eb4dfe1d0e32ea22d2
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "2753534"
---
# <a name="stylesheet-xsl-web-resources"></a>XSL-Webressourcen (Stylesheet)

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/stylesheet-xsl-web-resources -->


Verwenden Sie XSL-Webressourcen (Stylesheet), um XML-Daten zu transformieren.  
  
## <a name="capabilities-of-xsl-web-resources"></a>Verwendungsmöglichkeiten für XSL-Webressourcen  
 Verwenden Sie XSL-Webressourcen, um XML-Daten zu transformieren, die von Ihrer Lösung verwendet werden.  
  
 Folgende Webressourcen arbeiten zusammen, um eine Seite zu rendern, die eine Tabelle mit den Daten in der XML-Webressource anzeigt. Die Quelldateien für diese Webressourcen sind Teil des Beispiels zum Importieren von Webressourcen, das im Ordner **filestoimport** enthalten ist. Herunterladen der Beispiel-[Importdateien als Webressourcen](https://code.msdn.microsoft.com/Import-files-as-web-f84ad8dc).  
  
 **HTML-Webressource:** sample_/ImportWebResources/Content/ShowData.htm  
 ```html  
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "https://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">  
<html>  
<head>  
 <title></title>  
 <script src="Script/Script.js" type="text/javascript"></script>  
 <link href="CSS/Styles.css" rel="stylesheet" type="text/css" />  
</head>  
<body onload="SDK.ImportWebResources.showData()">  
 <div id="results" />  
</body>  
</html>  
```  
  
 **XSL-Webressource:** sample_/ImportWebResources/XSL/Transform.xslt  
 ```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xsl:stylesheet version="1.0"  
                xmlns:xsl="https://www.w3.org/1999/XSL/Transform"  
                xmlns:msxsl="urn:schemas-microsoft-com:xslt"  
                exclude-result-prefixes="msxsl"  
>  
 <xsl:output method="xml"  
             indent="yes"/>  
  
 <xsl:template match="@* | node()">  
  <xsl:copy>  
   <xsl:apply-templates select="@* | node()"/>  
  </xsl:copy>  
 </xsl:template>  
  
 <xsl:template match="people">  
  <xsl:element name="table">  
   <xsl:element name="thead">  
    <xsl:element name="tr">  
     <xsl:element name="th">  
      <xsl:text>First Name</xsl:text>  
     </xsl:element>  
     <xsl:element name="th">  
      <xsl:text>Last Name</xsl:text>  
     </xsl:element>  
    </xsl:element>  
   </xsl:element>  
   <xsl:element name="tbody">  
    <xsl:apply-templates />  
   </xsl:element>  
  </xsl:element>  
  
 </xsl:template>  
  
 <xsl:template match="person">  
  <xsl:element name="tr">  
   <xsl:element name="td">  
    <xsl:value-of select="@firstName"/>  
   </xsl:element>  
   <xsl:element name="td">  
    <xsl:value-of select="@lastName"/>  
   </xsl:element>  
  </xsl:element>  
  
 </xsl:template>  
  
</xsl:stylesheet>  
  
```  
  
 **XML-Webressource:** sample_/ImportWebResources/Data/Data.xml  
 ```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<people>  
 <person firstName="Apurva"  
         lastName="Dalia" />  
 <person firstName="Ofer"  
         lastName="Daliot" />  
 <person firstName="Jim"  
         lastName="Daly" />  
 <person firstName="Ryan"  
         lastName="Danner" />  
 <person firstName="Mike"  
         lastName="Danseglio" />  
 <person firstName="Alex"  
         lastName="Darrow" />  
</people>  
```  
  
 **Skript-Webressource:** sample_/ImportWebResources/Script/Script.js  
 ```javascript  
//If the SDK namespace object is not defined, create it.  
if (typeof (SDK) == "undefined")  
{ SDK = {}; }  
// Create Namespace container for functions in this library;  
SDK.ImportWebResources = {  
 dataFile: "Data/Data.xml",  
 transformFile: "XSL/Transform.xslt",  
 showData: function () {  
  
  //Create an XML document from the Data.xml file  
  var dataXml = new ActiveXObject("Msxml2.DOMDocument.6.0");  
  dataXml.async = false;  
  dataXml.load(this.dataFile);  
  
  //Create an XML document from the Transform.xslt file  
  var transformXSLT = new ActiveXObject("Msxml2.DOMDocument.6.0");  
  transformXSLT.async = false;  
  transformXSLT.load(this.transformFile);  
  
  // Set the innerHTML of the results area to the output of the transformation.  
  var resultsArea = document.getElementById("results");  
  resultsArea.innerHTML = dataXml.transformNode(transformXSLT);  
 }  
  
}  
```  
  
 **CSS Webressource**: sample_/ImportWebResources/CSS/Styles.css  
 ```css
body  
{  
    font-family: Calibri;  
}  
table  
{  
    border: 1px solid gray;  
    border-collapse: collapse;  
}  
th  
{  
    text-align: left;  
    border: 1px solid gray;  
}  
td  
{  
    border: 1px solid gray;  
}  
```  
  
### <a name="see-also"></a>Siehe auch  
 [Webressourcen](web-resources.md)   
 [Verwenden von Webseite (HTML)-Webressourcen](webpage-html-web-resources.md)   
 [Verwenden von Stylesheet(CSS)-Webressourcen](css-web-resources.md)   
 [Verwenden von Webressourcen für Skripts (JScript)](script-jscript-web-resources.md)   
 [Verwenden von Daten (XML)-Webressourcen](data-xml-web-resources.md)   
 [Verwenden von Bild (JPG, PNG, GIF)-Webressourcen](image-web-resources.md)   
