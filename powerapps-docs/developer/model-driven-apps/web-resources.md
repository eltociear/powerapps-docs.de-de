---
title: Webressourcen (modellgesteuerte Apps) | Microsoft Docs
description: 'Webressourcen sind virtuelle Dateien, die in der "CDS für Apps"-Datenbank gespeichert sind und die Sie mithilfe einer eindeutigen URL-Adresse abrufen können.'
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
# <a name="web-resources-in-model-driven-apps"></a>Webressourcen in modellgesteuerten Apps

<!-- https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/web-resources -->


Webressourcen sind *virtuelle Dateien*, die in der "Common Data Services für Apps"-Datenbank gespeichert sind und die Sie mithilfe einer eindeutigen URL-Adresse abrufen können.  
  
<a name="BKMK_CapabilitiesOfWebResources"></a>   
## <a name="capabilities-of-web-resources"></a>Verwendungsmöglichkeiten für Webressourcen  
 Webressourcen sind Dateien, die verwendet werden können, um die "CDS für Apps"-Webanwendung zu erweitern, beispielsweise HTML-Dateien, JavaScript und CSS sowie verschiedene Bildformate. Sie können Webressourcen in Formularanpassungen, die `SiteMap` oder im Anwendungsmenüband verwenden, da auf sie mithilfe der URL-Syntax verwiesen werden kann.  
  
 Die URL-Syntax für Webressourcen ermöglicht relative Pfadverweise. Mit den Entwicklungswerkzeugen können Sie eine Gruppe voneinander abhängiger Dateien auf einem Entwicklungsserver erstellen, indem Sie Dateitypen verwenden, die mit Webressourcen kompatibel sind. Wenn Sie dann eine einheitliche Namenskonvention und relative Pfadverweise verwenden, funktioniert die Website, nachdem Sie alle Dateien in CDS für Apps hochgeladen haben.
  
 Da Webressourcen in CDS für Apps gespeichert werden und Lösungskomponenten sind, können sie einfach exportiert und in anderen "CDS für Apps"-Organisationen installiert werden. Webressourcen sind auch für Benutzer von CDS für Apps für Microsoft Office Outlook mit Offlinezugriff verfügbar, wenn sie offline sind, da sie mit den Daten des Benutzers synchronisiert werden.  
  
 Sie können den Formular-Editor verwenden, um formularfähige Webressourcen Ihren Entitätsformularen hinzuzufügen und um sie zu konfigurieren.  
  
 Da Webressourcen als Datensätze in der Datenbank gespeichert sind, können sie mit den Standardtechniken zum Erstellen, Abrufen und Aktualisieren von Datensätzen programmgesteuert verwaltet werden. Textbasierte Webressourcen (JScript, CSS, XML, SXL, RESX und HTML) können in der Anwendung bearbeitet und gespeichert werden.  
  
<a name="BKMK_LimitationsOfWebResources"></a>   
### <a name="limitations-of-web-resources"></a>Einschränkungen für Webressourcen  
 Es gibt keinen Webressourcentyp, der die Funktionalität einer   ASP.NET(.aspx) -Seite unterstützt, um Code auf dem Server auszuführen. Webressourcen sind auf statische Dateien begrenzt oder auf Dateien, die im Browser verarbeitet werden. Eine Webressource kann Code enthalten, der im Browser verarbeitet wird, um Webdienstaufrufe zur Interaktion mit "CDS für Apps"-Daten auszuführen.
  
 Webressourcen sind nur verfügbar, wenn Sie den Sicherheitskontext für "CDS für Apps"-Webanwendungen verwenden. Nur lizenzierte "CDS für Apps"-Benutzer, die über die notwendigen Rechte verfügen, können darauf zugreifen.  
  
#### <a name="size-limitations"></a>Größeneinschränkungen  
Die maximale Größe für Dateien, die hochgeladen werden können, wird durch die Organization.MaxUploadFileSize-Eigenschaft bestimmt. Diese Eigenschaft wird in der Dynamics 365-Anwendung auf der Registerkarte E-Mail in den Systemeinstellungen festgelegt. Mit dieser Einstellung wird die Größe von Dateien begrenzt, die an E-Mail-Nachrichten, Notizen und Webressourcen angefügt werden können. Die Standardeinstellung ist 5 MB.
  
<a name="BKMK_WebResourceTypes"></a>   
## <a name="web-resource-types"></a>Webressourcentypen  
 Sie können zehn Dateiformate verwenden, um Webressourcen zu erstellen. In der folgenden Tabelle sind für jedes Dateiformat die zulässigen Dateierweiterungen und der entsprechende Typwert aufgeführt.  
  
|Datei|Dateierweiterungen|Typ|  
|----------|---------------------|----------|  
|Webseite (HTML)|.htm, .html|1|  
|Stylesheet (CSS)|.css|2|  
|Skript (JScript)|.js|3|  
|Daten (XML)|.xml|4|  
|Bild (PNG)|.png|5|  
|Bild (JPG)|.jpg|6|  
|Bild (GIF)|.gif|7|  
|Silverlight (XAP)|.xap|8|  
|StyleSheet (XSL)|.xsl, .xslt|9|  
|Bild (ICO)|.ico|10|  
|Vektorformat (SVG)|.svg|11|  
|Zeichenfolge (RESX)|.resx|12|  
  
<a name="BKMK_ReferencingWebResources"></a>   
## <a name="reference-web-resources"></a>Auf Webressourcen verweisen  
 Es gibt mehrere Möglichkeiten, die Sie verwenden können, um auf Webressourcen zu verweisen.  
  
> [!NOTE]
>  -   Sofern möglich, sollten Sie die `$webresource`-Direktive verwenden. Nur Verweise, welche in den SiteMap- oder Menübandbefehlen die `$webresource`-Direktive verwenden, richten Abhängigkeiten ein. Abhängigkeiten werden nicht erstellt, indem eine Webressource auf eine andere verweist.  
>       - Erstellen Sie zum Anzeigen einer Silverlight-Webressource außerhalb eines Entitätsformulars oder Diagramms eine HTML-Webressource als Hostseite für die Silverlight-Webressource. Verwenden Sie dann die "$webresource:"-Direktive, um die HTML-Webressource zu öffnen.
  
<a name="BKMK_WebResourceDirective"></a>   
### <a name="webresource-directive"></a>$webresource-Direktive  
 Sie sollten immer die `$webresource`-Direktive verwenden, wenn Sie auf eine Webressource aus einem Menübandsteuerelement oder einem `SiteMap`-Unterbereich verweisen. Verwenden Sie die `$webresource`-Direktive überall dort, wo XML einen URL-Wert ermöglicht. Das folgende Beispiel zeigt, wie dies gemacht wird.  
  
```xml  
$webresource:<name of Web Resource>  
```  
  
> [!NOTE]
>  Bei Verwendung der `$webresource`-Direktive werden von CDS für Apps Lösungsabhängigkeiten erstellt oder aktualisiert.  
  
### <a name="xrmnavigationopenwebresource"></a>Xrm.Navigation.openWebResource  
 Die Funktion Xrm.Navigation.[openWebResource](clientapi/reference/Xrm-Navigation/openWebResource.md) öffnet eine HTML-Webressource in einem neuen Fenster, wobei als Parameter der Name der Webressource, beliebige Abfragezeichenfolgendaten für den Datenparameter sowie Informationen über Höhe und Breite des Fensters übergeben werden können.  
  
 Die generierte URL enthält das eindeutige GUID-Token, so dass die zwischengespeicherte Webressource geladen wird.  
  
<a name="BKMK_RelativeUrl"></a>   
### <a name="relative-url"></a>Relative URL  
 Wenn Sie auf eine Webressource aus Bereichen verweisen müssen, welche die Verwendung der `$webresource:`-Direktive nicht unterstützen, können Sie eine relative URL verwenden. Dazu sollten Sie eine einheitliche Namenskonvention für die Webressourcen verwenden, die einer virtuellen Dateistruktur entspricht. Das Anpassungspräfix für den Lösungsherausgeber wird dem Namen der Webressource immer als Präfix vorangestellt. Es kann einen virtuellen "Stamm"-Ordner für alle Webressourcen angeben, die mit diesem Herausgeber hinzugefügt werden. Sie können dann das Schrägstrichzeichen (/) verwenden, um eine Ordnerstruktur zu simulieren, die durch den Webserver berücksichtigt wird.  
  
 Von einer anderen Webressource sollten Sie immer relative URLs für Verweise untereinander verwenden. Damit beispielsweise die Webseiten-Webressource `new_/content/contentpage.htm` auf die CSS-Webressource `new_/Styles/styles.css` zugreifen kann, stellen Sie die Verbindung wie folgt her:  
  
```html  
<link rel="stylesheet" type="text/css" href="../styles/styles.css" />  
```  
  
 Damit die Webseiten-Webressource `new_/content/contentpage.htm` die Webseiten-Webressource `isv_/foldername/dialogpage.htm` öffnen kann, stellen Sie die Verbindung wie folgt her:  
  
```html  
<a href="../../isv_/foldername/dialogpage.htm">Dialog Page</a>  
```  
  
> [!NOTE]
>  Verwenden Sie keine relative URL mit dem Webressourcen- Ordner als Stammpfad für die URL. Verwenden Sie beispielsweise nicht Folgendes: `/WebResources/<name of web resource>`. Wenn ein Benutzer mehr als einer Organisation auf einem Server angehört, wird dieser Pfad immer auf die Standardorganisation des Benutzers verweisen. Wenn der Benutzer die standardmäßige Organisation nicht verwendet und die erwartete Webressource nicht in der Standardorganisation des Benutzers enthalten ist, tritt ein "File not Found"-Fehler auf, selbst wenn die Webressource in der Organisation enthalten ist, in welcher der Benutzer derzeit arbeitet.  
  
<a name="BKMK_FullUrl"></a>   
### <a name="full-url"></a>Vollständiges URL  
 Das folgende Beispiel zeigt das Format einer URL, die zur Anzeige von Webressourcen verwendet werden kann.  
  
```  
<CDS for Apps URL>/WebResources/<name of web resource>  
```  
  
 Die Anwendung wird diese URL verarbeiten und die Datei mit der aktuelle Version der Webressource zurückgeben. Diese URL sieht folgendermaßen aus:  
  
```  
<CDS for Apps URL>/%7B<version value>%7D/WebResources/<name of web resource>  
```  
  
 Der Versionen-Wert wird aktualisiert, wenn Sie Anpassungen veröffentlichen, sodass sichergestellt ist, dass der Browser die zuletzt zwischengespeicherte Version der Webressource verwendet. Verwenden Sie deshalb einen relativen Pfad zu einer Webressource, die Xrm.Naviation.[openWebResource](clientapi/reference/Xrm-Navigation/openWebResource.md)-Funktion oder die [$webresource Directive](web-resources.md#BKMK_WebResourceDirective) (wenn möglichlich) , da der Versionen-Wert automatisch eingefügt wird. Bei umfangreichen Webressourcen kann es zu signifikanten Leistungsbeeinträchtigungen kommen, wenn Sie nicht die zwischengespeicherte Version der Datei verwenden.  
  
 Das folgende Beispiel zeigt eine URL für CDS für Apps, wobei `MyOrganization` der Name Ihrer Organisation ist und `new_/test/test.htm` der Name der Webressource:  
  
```  
https://MyOrganization.crm.dynamics.com/WebResources/new_/test/test.htm  
```  
  
> [!NOTE]
>  Das Einfügen des Zeichens "/" und einer Dateinamenerweiterung im Namen der Webressource ist eine bewährte Methode.  
  
  
 Wenn Sie Code schreiben, der auf eine Webressource verweist die für CDS für Apps funktioniert, sollten Sie die [getClientUrl](clientapi/reference/Xrm-Utility/getGlobalContext/getClientUrl.md)-Funktion verwenden.

## <a name="community-tools"></a>Community-Tools

**WebResources-Manager** ist ein Tool, das die XrmToolbox-Community für CDS für Apps entwickelt hat. Weitere Informationen finden Sie im Thema [Entwicklertools](developer-tools.md) für von der Community entwickelte Tools.

> [!NOTE]
> Die Communitytools sind kein Produkt von CDS for Apps und es wird kein Support für die Communitytools angeboten. Wenn Sie Fragen zu dem Tool haben, setzen Sie sich bitte mit dem Herausgeber in Verbindung. Weitere Informationen: [XrmToolBox](https://www.xrmtoolbox.com). 
  
### <a name="see-also"></a>Siehe auch  

 [Erstellen von barrierefreien Webressourcen](create-accessible-web-resources.md)<br />
 [Webseite (HTML)-Webressourcen](webpage-html-web-resources.md)<br />
 [Webressourcen für Skripts (JScript)](script-jscript-web-resources.md)<br />
 [Bildwebressourcen](image-web-resources.md)<br />
 [XSL-Webressourcen (Stylesheet)](stylesheet-xsl-web-resources.md)<br />
 [Webressourcen von Daten (XML)](data-xml-web-resources.md)<br />
 [CSS-Webressourcen (Stylesheet)](css-web-resources.md)<br />
 [WebResource-Entitätsreferenz](../common-data-service/reference/entities/webresource.md)<br />
 [Beispiel: Mehrere Werte über den Datenparameter an eine Webressource übergeben](sample-pass-multiple-values-web-resource-through-data-parameter.md)<br />
 [Beispiel: Importieren von Dateien als Webressourcen](sample-import-files-web-resources.md)<br />
 [Webressourcenentwicklung mithilfe des Fiddler-AutoResponder verbessern](streamline-javascript-development-fiddler-autoresponder.md)
