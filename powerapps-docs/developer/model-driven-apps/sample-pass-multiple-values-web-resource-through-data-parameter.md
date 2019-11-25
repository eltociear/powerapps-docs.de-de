---
title: 'Beispiel: Übergeben mehrerer Werte über den Datenparameter an eine Webressource (modellgestützte Apps) | Microsoft Docs'
description: Dieses Beispiel stellt eine Technik dar, um zusätzliche Werte innerhalb eines einzelnen Parameters zu übergeben und sie anschließend innerhalb Ihrer Webressource zu verarbeiten.
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
ms.openlocfilehash: 2a4b4a6bf2da6cc6588a0fcf8b7523bae1c7da5f
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "2753586"
---
# <a name="sample-pass-multiple-values-to-a--web-resource-through-the-data-parameter"></a>Beispiel: Mehrere Werte über den Datenparameter an eine Webressource übergeben

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-pass-multiple-values-web-resource-through-data-parameter -->

Eine (HTML) Webressourcenseite kann nur einen einzelnen benutzerdefinierten Parameter, den `data`-Parameter akzeptieren. Um mehr als einen Wert innerhalb des Datenparameters zu übergeben, müssen Sie die Parameter innerhalb Ihrer Seite kodieren und dekodieren.  
  
 Diese Seite stellt eine Technik dar, um zusätzliche Werte innerhalb eines einzelnen Parameters zu übergeben und sie anschließend innerhalb Ihrer Webressource zu verarbeiten. 
  
## <a name="sample-html-web-resource"></a>Beispiel-HTML-Webressource  
 Der folgende HTML-Code stellt eine (HTML) Webressource Webseite dar, die ein Skript enthält, das drei Funktionen definiert:  
  
- **getDataParam**: Aufgerufen vom `body.onload`-Ereignis, ruft diese Funktion alle Abfragezeichenfolgenparameter ab, die an die Seite übergeben wurden, und sucht solche namens `data`.  
  
- **parseDataValue**: Empfängt die Datenparameter von `getDataParam` und erstellt eine DHTML-Tabelle, um alle Werte anzuzeigen, die innerhalb des `data`-Parameters übergeben wurden.  
  
  > [!NOTE]
  >  Alle Zeichen, die in der Abfragezeichenfolge enthalten sind, werden mithilfe der [encodeURIComponent-Methode](https://msdn.microsoft.com/library/xh9be5xc\(v=VS.85\).aspx) kodiert. Diese Funktion verwendet die JavaScript [decodeURIComponent-Methode](https://msdn.microsoft.com/library/91b80x6x\(VS.85\).aspx), um die übergebenen Werte zu decodieren.  
  
- **noParams**: Zeigt eine Meldung an, wenn keine Parameter an die Seite übergeben werden.  
  
```html  
<!DOCTYPE html >  
<html lang="en-us">  
<head>  
 <title>Show Data Parameters Page</title>  
 <style type="text/css">  
  body  
  {  
   font-family: Segoe UI, Tahoma, Arial;  
   background-color: #d6e8ff;  
  }  
  tbody  
  {  
   background-color: white;  
  }  
  th  
  {  
   background-color: black;  
   color: White;  
  }  
 </style>  
 <script type="text/javascript">  
  document.onreadystatechange = function () {  
   if (document.readyState == "complete") {  
    getDataParam();  
   }  
  }  
  
  function getDataParam() {  
   //Get the any query string parameters and load them  
   //into the vals array  
  
   var vals = new Array();  
   if (location.search != "") {  
    vals = location.search.substr(1).split("&");  
    for (var i in vals) {  
     vals[i] = vals[i].replace(/\+/g, " ").split("=");  
    }  
    //look for the parameter named 'data'  
    var found = false;  
    for (var i in vals) {  
     if (vals[i][0].toLowerCase() == "data") {  
      parseDataValue(vals[i][1]);  
      found = true;  
      break;  
     }  
    }  
    if (!found)  
    { noParams(); }  
   }  
   else {  
    noParams();  
   }  
  }  
  
  function parseDataValue(datavalue) {  
   if (datavalue != "") {  
    var vals = new Array();  
  
    var message = document.createElement("p");  
    setText(message, "These are the data parameters values that were passed to this page:");  
    document.body.appendChild(message);  
  
    vals = decodeURIComponent(datavalue).split("&");  
    for (var i in vals) {  
     vals[i] = vals[i].replace(/\+/g, " ").split("=");  
    }  
  
    //Create a table and header using the DOM  
    var oTable = document.createElement("table");  
    var oTHead = document.createElement("thead");  
    var oTHeadTR = document.createElement("tr");  
    var oTHeadTRTH1 = document.createElement("th");  
    setText(oTHeadTRTH1, "Parameter");  
    var oTHeadTRTH2 = document.createElement("th");  
    setText(oTHeadTRTH2, "Value");  
    oTHeadTR.appendChild(oTHeadTRTH1);  
    oTHeadTR.appendChild(oTHeadTRTH2);  
    oTHead.appendChild(oTHeadTR);  
    oTable.appendChild(oTHead);  
    var oTBody = document.createElement("tbody");  
    //Loop through vals and create rows for the table  
    for (var i in vals) {  
     var oTRow = document.createElement("tr");  
     var oTRowTD1 = document.createElement("td");  
     setText(oTRowTD1, vals[i][0]);  
     var oTRowTD2 = document.createElement("td");  
     setText(oTRowTD2, vals[i][1]);  
  
     oTRow.appendChild(oTRowTD1);  
     oTRow.appendChild(oTRowTD2);  
     oTBody.appendChild(oTRow);  
    }  
  
    oTable.appendChild(oTBody);  
    document.body.appendChild(oTable);  
   }  
   else {  
    noParams();  
   }  
  }  
  
  function noParams() {  
   var message = document.createElement("p");  
   setText(message, "No data parameter was passed to this page");  
  
   document.body.appendChild(message);  
  }  
  //Added for cross browser support.  
  function setText(element, text) {  
   if (typeof element.innerText != "undefined") {  
    element.innerText = text;  
   }  
   else {  
    element.textContent = text;  
   }  
  
  }  
 </script>  
</head>  
<body>  
</body>  
</html>  
  
```  
  
#### <a name="using-this-page"></a>Verwendung dieser Seite  
  
1.  Erstellen Sie mithilfe des Beispielcodes eine Webseiten-Webressource namens "new_/ShowDataParams.htm".  
  
     Die Parameter, die Sie übergeben möchten, sind: `first=First Value&second=Second Value&third=Third Value`  
  
    > [!NOTE]
    >  Wenn Sie statische Parameters mithilfe des Webressource-Eigenschaftendialogfelds im Formular-Editor hinzufügen, können Sie einfach die Parameter einfügen, ohne sie in das Feld **Custom Parameter(data)** zu kodieren. Diese Werte werden für Sie codiert, aber Sie müssen sie noch decodieren und die Werte in der Seite extrahieren.  
  
2.  Bei dynamischen Werte, die im Code generiert werden, verwenden Sie die `encodeURIComponent`-Methode auf den Parametern. Die codierten Werte sollten sein:  
  
     `first%3DFirst%20Value%26second%3DSecond%20Value%26third%3DThird%20Value`  
  
     Öffnen Sie die Seite, indem Sie die codierten Parameter als Wert des Datenparameters übergeben:  
  
    ```  
    https://<server name>/WebResources/new_/ShowDataParams.htm?data=first%3DFirst%20Value%26second%3DSecond%20Value%26third%3DThird%20Value  
    ```  
  
    > [!NOTE]
    >  Wenn Sie die Webressource zu einem Formular hinzugefügt haben und die nicht-codierten Parameter in das Feld **Custom Parameters(data)** eingefügt haben, können Sie das Formular nur in einer Vorschau anzeigen.  
  
3.  Das `new_/ShowDataParams.htm` zeigt eine dynamisch generierte Tabelle an:  
  
    |Parameter|Wert|  
    |---------------|-----------|  
    |erste|Erster Wert|  
    |zweite|Zweiter Wert|  
    |dritte|Dritter Wert|  
  
### <a name="how-it-works"></a>Funktionsweise  
 Um auf die Werte zuzugreifen, die im Datenabfragezeichenfolgenparameterwert eingebetet sind, können Sie in der Webseiten-Webressource den Wert des Datenparameters extrahieren und dann Code verwenden, um die Zeichenfolge in en Array aufzuspalten, um auf jedes Namewertpaar einzeln zuzugreifen.  
  
 Wenn die Seite geladen wird, wird die `getDataParam`-Funktion aufgerufen. Diese Funktion identifiziert die Datenparameter und übergibt den Wert an die Funktion `ParseDataValue`. Wenn kein Datenparameter gefunden wird, wird die `noParams`-Funktion der Seite eine Nachricht anstelle der Tabelle hinzufügen.  
  
 Die Funktion `ParseDataValue` verwendet eine ähnliche Logik wie in `getDataParam`, um die benutzerdefinierten Parameterbegrenzer zu suchen, um en Array von Namewertpaaren zu erstellen. Dann generiert sie eine Tabelle und fügt sie dem ansonsten leeren document.body an.  
  
### <a name="see-also"></a>Siehe auch  
 [Webressourcen](web-resources.md)   
 [Beispiel: Importieren von Dateien als Webressourcen](sample-import-files-web-resources.md)   
 [Webseite (HTML)-Webressourcen](webpage-html-web-resources.md)   
