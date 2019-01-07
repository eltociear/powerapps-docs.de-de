---
title: Verwenden von IFrame- und Webressourcen-Steuerelementen in einem Formular (modellgestützte Apps) | Microsoft Docs
description: 'Durch IFRAME- und Webressourcensteuerelemente wird der eingebettete Inhalt von einem anderen Ort aus auf den Seiten mithilfe eines HTML-IFRAME-Elements gesteuert.  '
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
# <a name="use-iframe-and-web-resource-controls-on-a-form"></a>Verwenden von IFRAME- und Webressourcen-Steuerelementen in einem Formular

<!-- https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/use-iframe-and-web-resource-controls-on-a-form -->


Durch IFRAME- und Webressourcensteuerelemente wird der eingebettete Inhalt von einem anderen Ort aus auf den Seiten mithilfe eines HTML-IFRAME-Elements gesteuert.  

> [!NOTE]
>  Die Designs, die Sie für das Formular auswählen, werden auch für den Dynamics 365 for Outlook-Lesebereich und die Formulare verwendet, die von Dynamics 365 tablets verwendet werden. Webressourcen und IFrames werden nicht mithilfe des Dynamics 365 for Outlook-Lesebereichs angezeigt, sie werden jedoch in Dynamics 365 for tablets unterstützt. Wenn der IFRAME vom Zugriff auf das `Xrm`-Objekt der Seite oder von Formularereignishandlern abhängt, sollten Sie den IFRAME so konfigurieren, dass er standardmäßig nicht sichtbar ist.  

 Sie können einen IFRAME verwenden, um den Inhalt einer anderen Website in einem Formular anzuzeigen, beispielsweise in einer ASP.NET-Seite. Anzeigen eines Entitätsformulars mit einem IFrame, der eingebettet in einem anderen Entitätsformular ist, wird nicht unterstützt.  

 Sie können eine der folgenden Webressourcen verwenden, um den Inhalt von Webressourcen in einem Formular anzuzeigen:  

-   [Webseite (HTML)-Webressourcen](webpage-html-web-resources.md)  

-   [Bild- (JPG, PNG, GIF, ICO)-Webressourcen](image-web-resources.md)  


 Die folgende Abschnitte beschreiben Ihre Optionen, wenn diese Steuerelemente mehr als statische Inhalte anzeigen sollen.  

<a name="BKMK_IframeSecurity"></a>   
## <a name="select-whether-to-restrict-cross-frame-scripting"></a>Auswählen, ob frameübergreifendes Skripting eingeschränkt werden soll  
 Verwenden Sie die Option **Frameübergreifendes Skripting einschränken, wenn unterstützt**, wenn Sie dem Inhalt, der in einem IFRAME angezeigt wird, nicht vollständig vertrauen. Wenn diese Option ausgewählt ist, besitzt der IFRAME den Attributsatz, der in der folgenden Tabelle aufgeführt ist.  


|        Attribut        |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        Beschreibung                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
|-------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `security="restricted"` |                                                                                                                                                                                                                                                                                                    Dieses Attribut wird nur von Versionen von Internet Explorer ab Version 6 unterstützt. Das Sicherheitsattribut wendet die Benutzersicherheitseinstellung "Eingeschränkte Sites" auf die Quelldatei des IFRAME an. (Zoneneinstellungen sind auf der Registerkarte **Sicherheit** des Dialogfelds **Internetoptionen** zu finden.) Standardmäßig ist die Skipterstellung in der Zone für eingeschränkte Sites nicht aktiviert. Durch Ändern der Sicherheitseinstellungen der Zone können unterschiedliche negative Ergebnisse auftreten, einschließlich das Zulassen der Ausführung von Skripts. Weitere Informationen finden Sie unter [Sicherheitsattribute](https://msdn.microsoft.com/library/ie/ms534622.aspx).                                                                                                                                                                                                                                                                                                     |
|      `sandbox=""`       | Für Browser, die dieses Attribut unterstützen, ist der Inhalt im IFRAME im Wesentlichen darauf beschränkt, nur Informationen anzuzeigen. Die folgenden Einschränkungen können angewendet werden:<br /><br /> -   Browser-Plug-Ins sind deaktiviert.<br />-   Skripts und Formulare sind deaktiviert.<br />-   Links zu anderen Browserkontexten sind deaktiviert.<br />-   Inhalt wird wie aus einer anderen Domänen behandelt, auch wenn die Domäne identisch ist.<br /><br /> Dieses Attribut wird durch W3C definiert und wird von den folgenden Browsern unterstützt:<br /><br /> - Internet Explorer 10, Internet Explorer 11 und Microsoft Edge <br />- Google Chrome<br />- Apple Safari<br />- Mozilla Firefox<br /><br /> Weitere Informationen zum Sandkastenattribut finden Sie unter:<br /><br /> -   [Sichern der Website mit HTML5 Sandbox](https://msdn.microsoft.com/hh563496)<br />-   [WC3 Sandbox-Attribut](http://dev.w3.org/html5/spec-author-view/the-iframe-element.html)<br />-   [Sandkasten](https://msdn.microsoft.com/library/ie/hh673561.aspx) |

<a name="BKMK_EnableIFrameCommunicationAcrossDomains"></a>   

### <a name="enabling-iframe-communication-across-domains"></a>Aktivieren der IFRAME-Kommunikation über Domänengrenzen hinweg  
 Manchmal möchten Sie die Kommunikation für einen IFRAME aktivieren, der Inhalt auf einer anderen Domäne enthält. `Window.postMessage` ist eine Browsermethode, die diese Funktionen für Versionen von Internet Explorer ab Internet Explorer 8 bereitstellt. Google Chrome, Mozilla Firefox und Apple Safari unterstützen sie auch. Weitere Informationen zu `postMessage` finden Sie in den folgenden Blogbeiträgen:  

-   [Domänenübergreifende Aufrufe an das übergeordnete Formular](http://blogs.msdn.com/b/devkeydet/archive/2012/02/14/cross-domain-calls-to-the-parent-crm-2011-form.aspx)  

-   [Dokumentübergreifendes Messaging und RPC](https://msdn.microsoft.com/magazine/ff800814.aspx)  

<a name="BKMK_PassContextualInformation"></a>   

## <a name="pass-contextual-information-about-the-record"></a>Übergeben kontextbezogener Informationen zum Datensatz  
 Sie können kontextbezogene Informationen durch Übergeben von Parametern an die im Steuerelement definierte URL bereitstellen. Die Seite, die im Frame angezeigt wird, muss in der Lage zu sein, übergebene Parameter zu verarbeiten. Alle Parameter in der folgenden Tabelle werden übergeben, wenn der IFRAME oder die Webressource mit der Option **Datensatzobjekt-Typcode u. eindeut. Bezeichner als Parameter übergeben** konfiguriert ist.  

 Sie können angeben, ob alle Parameter in der folgenden Tabelle übergeben werden.  


| Parameter  |        Name        |                                 Beschreibung                                 |
|------------|--------------------|-----------------------------------------------------------------------------|
| `typename` |    Entitätsname     |                           Der Name der Entität.                           |
|   `type`   |  Entitätstypcode  | Die ganze Zahl, die eindeutig die Entität in einer bestimmten Organisation identifiziert. |
|    `id`    |    Objekt-GUID     |                      Eine GUID, die einen Datensatz darstellt.                       |
| `orgname`  | Organisationsname  |                    Der eindeutige Name der Organisation.                     |
| `userlcid` | Benutzersprachcode |    Die Sprachcode-ID, die vom aktuellen Benutzer verwendet wird.     |

 [!INCLUDE[languagecode](../../includes/languagecode.md)]  

> [!NOTE]
>  Es ist empfehlenswert, den Entitätsnamen statt des Typcodes zu verwenden, da der Entitätstypcode für benutzerdefinierte Entitäten möglicherweise je nach CDS für Apps-Organisation verschieden ist.  

### <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die URL ohne Parameter gezeigt:  

```  
http://myserver/mypage.aspx  
```  

 Im folgenden Beispiel wird die URL mit Parameter gezeigt:  

```  
http://myserver/mypage.aspx?id=%7bB2232821-A775-DF11-8DD1-00155DBA3809%7d&orglcid=1033&orgname=adventureworkscycle&type=1&typename=account&userlcid=1033  
```  

### <a name="read-passed-parameters"></a>Lesen von übergebenen Parametern  

 Übergebene Parameter werden in der Regel auf der ASPX-Zielseite mithilfe der **HttpRequest.QueryString**-Eigenschaft gelesen. Auf einer HTML-Seite kann der Zugriff auf die Parameter mit der **window.location.search**-Eigenschaft in JavaScript erfolgen. Weitere Informationen finden Sie unter [HttpRequest.QueryString-Eigenschaft](http://msdn2.microsoft.com/library/system.web.httprequest.querystring.aspx) und [search-Eigenschaft](http://msdn2.microsoft.com/library/ms534620.aspx).  

<a name="BKMK_PassFormData"></a>  

## <a name="pass-form-data"></a>Übergeben von Formulardaten  

 Verwenden Sie die [getValue](clientapi/reference/controls/getValue.md)-Methode für die Attribute, die Daten enthalten, die Sie an die andere Website übergeben möchten, und erstellen Sie eine Zeichenfolge aus den Abfragezeichenfolgenargumenten, die die andere Seite verwenden kann. Verwenden Sie dann [Field OnChange Event](clientapi/reference/events/attribute-onchange.md), [IFRAME OnReadyStateComplete Event](clientapi/reference/events/onreadystatecomplete.md) oder [Tab TabStateChange Event](clientapi/reference/events/tabstatechange.md) und die [setSrc](clientapi/reference/controls/setSrc.md)-Methode, um Ihre Parameter an die Eigenschaft `src` des IFRAMEs oder der Webressource anzuüfgen.  

 Wenn Sie den Datenparameter verwenden, um Daten an eine Silverlight-Webressource zu übergeben, können Sie die [getData](clientapi/reference/controls/getData.md)- und [setData](clientapi/reference/controls/setData.md)-Methoden verwenden, um den Wert zu ändern, der über den Datenparameter übergeben wird. Für Webseiten-Webressourcen (HTML) verwenden Sie die [setSrc](clientapi/reference/controls/setSrc.md)-Methode, um den `querystring`-Parameter direkt zu bearbeiten.  

 Vermeiden Sie die Anwendung des [OnLoad-Ereignisses](clientapi/reference/events/form-onload.md). IFRAMES und Webressourcen werden asynchron geladen und der Frame ist möglicherweise noch nicht vollständig geladen, bevor das `Onload`-Ereignisskript abgeschlossen wird. Dies kann dazu führen, dass die Eigenschaft `src` des IFRAMEs oder der Webressource, die Sie geändert haben, durch den Standardwert des IFRAMES oder der Webressourceneigenschaft URL überschrieben wird.  

<a name="BKMK_ChangeThePage"></a>   

## <a name="change-the-url"></a>Ändern der URL  

 Sie möchten möglicherweise das Ziel von IFRAME basierend auf Überlegungen zu den Daten im Formular oder ob der Benutzer offline arbeitet ändern. Sie können das Ziel von IFRAME dynamisch festlegen.  

> [!NOTE]
>  Wenn Sie die Zielseite für den IFRAME ändern, werden Parameter nicht automatisch an den neuen URL-Parameter übergeben. Sie müssen Abfragezeichenfolgenparameter an die URL anfügen, bevor Sie die Methode `setSrc` verwenden.  

### <a name="example"></a>Beispiel  

 Im folgenden Beispiel wird gezeigt, wie die Eigenschaft `src` für den IFRAME und alle potenziellen Parameter mithilfe des Ereignisses `onChange` eines Optionssatzfelds festgelegt wird.  

```javascript  
//Get the value of an option set attribute  
var value = Xrm.Page.data.entity.attributes.get("new_pagechooser").getValue();  
var newTarget = "";  
//Set the target based on the value of the option set  
switch (value) {  
    case 100000001:  
        newTarget = "http://myServer/test/pageOne.aspx";  
        break;  
    default:  
        newTarget = "http://myServer/test/pageTwo.aspx";  
        break;  
}  
//Get the default URL for the IFRAME, which includes the   
// query string parameters  
var IFrame = Xrm.Page.ui.controls.get("IFRAME_test");  
var Url = IFrame.getSrc();  
// Capture the parameters  
var params = Url.substr(Url.indexOf("?"));  
//Append the parameters to the new page URL  
newTarget = newTarget + params;  
// Use the setSrc method so that the IFRAME uses the  
// new page with the existing parameters  
IFrame.setSrc(newTarget);  
```  

## <a name="see-also"></a>Siehe auch  

 [Clientskripting mit JavaScript](client-scripting.md)   
 

