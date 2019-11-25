---
title: Webseite (HTML) Webressourcen (modellgesteuerte Apps) | Microsoft Docs
description: Dieses Thema befasst sich damit, wie HTML-Webressourcen implementiert werden sowie ihre Funktionen und Einschränkungen
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
ms.openlocfilehash: 642d4f74e8d4e0c613bbc42381fecd4418f93030
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "2754547"
---
# <a name="webpage-html-web-resources"></a>Webressourcen der Webseite (HTML)

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/webpage-html-web-resources -->

Verwenden Sie Webressourcen der Webseite (HTML), um Benutzeroberflächenelemente für Clienterweiterungen zu erstellen.

<a name="BKMK_Capabilities"></a>

## <a name="capabilities-of-html-web-resources"></a>Verwendungsmöglichkeiten von HTML-Webressourcen

Da eine HTML-Webressource einfach nur zum Browser des Benutzers gestreamt wird, kann sie alle möglichen Inhalte enthalten, die im Browser des Benutzers gerendert werden.  

<a name="BKMK_Limitations"></a>

## <a name="limitations-of-html-web-resources"></a>Einschränkungen bei HTML-Webressourcen  

- Eine HTML-Webressource kann keinen Code enthalten, der auf dem Server ausgeführt werden muss. ASP.NET-Seiten können nicht als HTML-Webressourcen hochgeladen werden.

- HTML-Webressourcen können nur eine begrenzte Anzahl von Abfragezeichenfolgenparametern annehmen. [Parameter an HTML-Webressourcen übergeben](webpage-html-web-resources.md#BKMK_PassingParametersToWebResources)  

<a name="BKMK_UsingTextEditor"></a>

## <a name="use-the-text-editor-for-html-web-resources"></a>Texteditor für HTML-Webressourcen verwenden

 Der im Webressourcenformular bereitgestellte Texteditor ist für sehr einfache HTML-Bearbeitungsaktionen vorgesehen. Bei anspruchsvolleren HTML-Dokumenten sollten Sie den Code in einem externen Editor bearbeiteten und über die Schaltfläche **Durchsuchen** den Inhalt der Datei hochladen.

 Eine komplexere HTML-Seite, die Skripte benötigt, um die Inhalte der Seite zu rendern, beginnt beispielsweise wie das folgende Beispiel.

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

 Nachdem das Dokument im Texteditor geöffnet und gespeichert wurde, ändert sich der HTML-Code wie folgt:  

```html
<HTML><HEAD><TITLE></TITLE>
<META charset=utf-8></HEAD>
<BODY contentEditable=true onload=SDK.ImportWebResources.showData()>
<SCRIPT type=text/javascript src="Script/Script.js"></SCRIPT>
 <LINK rel=stylesheet type=text/css href="CSS/Styles.css">
<DIV id=results></DIV></BODY></HTML>
```

<a name="BKMK_PreventEditing"></a>

## <a name="prevent-editing-of-web-resources-for-managed-solutions"></a>Bearbeiten von Webressourcen für verwaltete Lösungen verhindern

Da der HTML-Code in Webressourcen mithilfe des Texteditors geändert werden kann, wird empfohlen, dass Sie verwaltete Eigenschaften verwenden, um festzulegen, dass komplexe HTML-Webressourcen bei verwalteten Lösungen nicht angepasst werden können. Öffnen Sie bei der Anzeige von Webressourcen im Lösungsfenster das Dialogfeld **Verwaltete Eigenschaften**, um die Eigenschaft **Anpassbar** auf `false` festzulegen.  

<a name="BKMK_ReferencingOtherWebResources"></a>

## <a name="reference-other-web-resources-from-an-html-web-resource"></a>Von einer HTML-Webressource auf andere Webressourcen verweisen

 Sie können einen Satz zugehöriger Dateien außerhalb von modellgesteuerten Apps erstellen, die irgendeinen der Webressourcendateitypen verwenden. Wenn Sie darauf achten, immer relative Pfade zu verwenden und jede Webressource mit einer einheitlichen Namenskonvention zu importieren, die die Ordnerstruktur Ihrer Website widerspiegelt, werden Sie feststellen, dass die HTML-Webressource Links zu verwandten CSS-, XML-, JScript-, Bild- und Silverlight-Dateien unterhält, die als Webressourcen importiert wurden.  

 Beispiel: Sie erstellen ein Webanwendungsprojekt, das die folgende [Ordner]/Dateistruktur verwendet:  

-   page.htm

-   [Formatvorlagen]

    -   style.css
  
-   [Skripte] 
  
    -   script.js
  
 Wenn Sie diese Dateien als Webressourcen importieren, können Sie folgende Benennung wählen, wobei das Lösungsherausgeberanpassungspräfix "Neu" lautet:  
  
-   `new_/page.htm`  
  
-   `new_/Styles/style.css`  
  
-   `new_/Scripts/script.js`  
  
 Wenn Sie sich an dieses Muster halten, kann Ihre `new_/page.htm`-HTML-Webressource auf herkömmliche Art und Weise auf die anderen Dateien verweisen und dabei relative Pfade verwenden, wie das folgende Beispiel veranschaulicht.  

```html
<script src="Scripts/script.js" type="text/javascript"></script>
<link href="Styles/style.css" rel="stylesheet" type="text/css" />
```

 Das Lösungsherausgeberanpassungspräfix wird ein virtueller Stammverzeichnisordner für alle Webressourcen in der Lösung. Wenn Sie das Anpassungspräfix ändern, werden die relativen Pfade innerhalb der HTML-Webressourcen nicht geändert.  
  
> [!NOTE]
>  - Eine HTML-Webressource, die einem Formular hinzugefügt wurde, kann keine globalen Objekte verwenden, die von der JavaScript-Bibliothek definiert werden, die im Formular geladen wird. Eine HTML-Webressource kann mit den `Xrm.Page`- oder `Xrm.Utility`-Objekten innerhalb des Formulars kommunizieren, indem `parent.Xrm.Page` oder `parent.Xrm.Utility` verwendet wird, aber auf globale Objekte, die über Formularskripts definiert wurden, kann nicht mithilfe des übergeordneten Elements zugegriffen werden. Sie sollten alle Bibliotheken, die eine HTML-Webressource innerhalb der HTML-Webressource benötigen, laden, damit sie nicht von den Skripts abhängig sind, die im Formular geladen werden.  
> - Verweise, die im Code zwischen der Webressourcen enthalten sind, werden als Lösungsabhängigkeiten nicht nachverfolgt.  

 Da Webressourcen auch für Benutzer von Dynamics 365 for Microsoft Office Outlook mit Offlinezugang heruntergeladen werden, haben Benutzer Zugriff auf Webressourceninhalte, während sie offline arbeiten.  

<a name="BKMK_PassingParametersToWebResources"></a>

## <a name="pass-parameters-to-html-web-resources"></a>Parameter an HTML-Webressourcen übergeben

 Eine HTML-Webressource kann nur Parameter annehmen, die in der folgenden Tabelle aufgeführt werden.

|Parameter|Name|Beschreibung|
|---------------|----------|-----------------|
|typename|Entitätsname|Der Name der Entität.|
|typ|Entitätstypcode|Eine ganze Zahl, die eindeutig die Entität in einer bestimmten Organisation identifiziert.|
|ID|Objekt-GUID|Die GUID, die einen Datensatz darstellt.|
|orgname|Organisationsname|Der eindeutige Name der Organisation.|
|userlcid|Benutzersprachcode|Die Sprachcode-ID, die vom aktuellen Benutzer verwendet wird.|
|orglcid|Organisationssprachcode|Die Sprachcode-ID, die die Ausgangssprache für die Organisation darstellt.|
|-Daten|Optionaler Datenparameter|Ein optionaler Wert, der übergeben werden kann.|
|formid|Formular-ID|Die GUID, die eine Formular-ID darstellt.|
|entrypoint|Eingangspunkt|Ein Zeichenfolgenwert. Dieser Parameter ist dazu bestimmt, als optionaler Wert an Webressourcen übergeben zu werden, die als die benutzerdefinierter Hilfeinhalt für eine Entität geöffnet werden. Wenn er aktiviert ist, enthält die benutzerdefinierte Hilfe-URL den Wert "form" oder "hierarchychart".|
|pagemode||Nur zur internen Verwendung.|
|Sicherheit||Nur zur internen Verwendung.|
|tabSet||Nur zur internen Verwendung.|

 Wenn im Datenparameter mehrere Werte übergeben werden, werden diese automatisch kodiert. Es muss auch eine Logik enthalten sein, um die verschiedenen Parameter mit Hilfe von Skripten in Ihrer HTML-Webressource zu dekodieren. Dieses [Beispiel: Übergeben mehrerer Werte an eine Webressource mit dem Datenparameter](sample-pass-multiple-values-web-resource-through-data-parameter.md)-Thema zeigt eine Methode zum Übergeben von mehreren Parameterwerten.  

### <a name="see-also"></a>Siehe auch
 [Webressourcen](web-resources.md)   
 [Erstellen von barrierefreien Webressourcen](create-accessible-web-resources.md)   
 [Verwenden von Stylesheet(CSS)-Webressourcen](css-web-resources.md)   
 [Verwenden von Webressourcen für Skripts (JScript)](script-jscript-web-resources.md)   
 [Verwenden von Daten (XML)-Webressourcen](data-xml-web-resources.md)   
 [Verwenden von Bild (JPG, PNG, GIF, ICO)-Webressourcen](image-web-resources.md)   
 [Verwenden von Stylesheet (XSL)-Webressourcen](stylesheet-xsl-web-resources.md)
