---
title: Beispiele für Web API-Datenvorgänge (clientseitiges JavaScript) (Common Data Service)| Microsoft Docs
description: Dieses Thema enthält eine Beschreibung verschiedener Web-API-Beispiele, die mit clientseitigen JavaScript implementiert werden
ms.custom: ''
ms.date: 10/31/2018
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
ms.assetid: a32e9a04-7bc1-41dd-b9af-bb4f21a613c6
caps.latest.revision: 15
author: JimDaly
ms.author: jdaly
ms.reviewer: susikka
manager: annbe
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 6d7c4123187a860fcb910ddf932fec74502aebec
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748593"
---
# <a name="web-api-data-operations-samples-client-side-javascript"></a>Web API Datenoperationen Beispiele (Client-seitiges JavaScript)


Dieses Thema vermittelt ein allgemeines Verständnis über Web-API-Beispiele mit client-seitigem JavaScript. Während sich jedes Beispiel auf einen anderen Aspekt beim Common Data Service Web API fokussiert, folgen sie alle ähnlichen Prozessen und Strukturen, die in diesem Thema beschrieben werden.  

<a name="bkmk_listOfSamples"></a>   
## <a name="web-api-samples-using-client-side-javascript"></a>Web API Beispiele die clientseitiges JavaScript verwenden  
 Die folgenden Beispiele verwenden die Muster, die hier beschriebene werden:  
  
|Probe|Beispielgruppe|Beschreibung|  
|------------|------------------|-----------------|  
|[Beispiele grundlegender Web API-Operationen (clientseitiges JavaScript)](samples/basic-operations-client-side-javascript.md)|[Beispiel grundlegender Web-API-Operationen](web-api-basic-operations-sample.md)|Veranschaulicht, wie Common Data Service Entitätsdatensätze erstellt, abgerufen, aktualisiert, gelöscht zugeordnet und aufgehoben werden.|  
|[Web API-Abfragedatenbeispiele (clientseitiges JavaScript)](samples/query-data-client-side-javascript.md)|[Web API-Abfragedatenbeispiel](web-api-query-data-sample.md)|Veranschaulicht, wie OData v4 Abfragensyntax und -Funktionen und Common Data Service Abfragefunktionen verwendet werden. Enthält Veranschaulichung des Arbeitens von vordefinierten Abfragen und die Verwendung von FetchXML, um Abfragen ausführen.|  
|[Beispiele bedingter Web API-Operationen (clientseitiges JavaScript)](samples/conditional-operations-client-side-javascript.md)|[Beispiel bedingter Web-API-Operationen](web-api-conditional-operations-sample.md)|Veranschaulicht, wie bedingte Operationen ausgeführt werden. Die Verhaltensweisen der Vorgänge hängt von den Kriterien ab, die Sie angeben.|  
|[Beispiele von Web API-Funktionen und Aktionen (clientseitiges JavaScript)](samples/functions-actions-client-side-javascript.md)|[Web API-Funktionen- und Aktionen-Beispiel](web-api-functions-actions-sample.md)|Veranschaulicht, wie Sie gebundene/ungebundene Funktionen und Aktionen, einschließlich benutzerdefinierte Aktionen verwenden.|  
  
<a name="bkmk_howToDownload"></a>   
## <a name="how-to-download-the-source-code-for-the-sample"></a>Wie der Quellcode für das Beispiel heruntergeladen wird.  
 Der Quellcode für jedes Beispiel ist in der [MSDN-Codegalerie](https://code.msdn.microsoft.com/site/search?f%5b0%5d.type=user&f%5b0%5d.value=microsoft%20dynamics%20crm%20sdk%20documentation%20team) verfügbar. Der Link, um jedes Beispiels herunterzuladen ist in den einzelnen Seiten für dieses Beispiel enthalten.  
  
 Nachdem Sie das Beispiel heruntergeladen haben, extrahieren Sie die komprimierte Datei. Finden Sie die Microsoft Visual Studio 2015 Lösung für jedes Sample im C#-Ordner, da es sich bei dem Projekt um ein leeres ASP.NET Webanwendungsprojekt handelt. Eine Common Data Service-Lösung wird auch im Download bereitgestellt, den Sie importieren und ausführen können.  
  
> [!NOTE]
>  Weder Visual Studio noch ASP.NET sind erforderlich, um clientseitiges JavaScript für Common Data Service zu entwickeln, jedoch verlangt die MSDN Code Gallery-Site, dass Dateien als Container in eine Visual Studio aufgenommen werden.  Allerdings bietet Visual Studio eine gute Erfahrung beim Schreiben von JavaScript.  
  
<a name="bkmk_HowToImport"></a>   
## <a name="how-to-import-the-common-data-service-solution-that-contains-the-sample"></a>So importieren Sie die Common Data Service-Lösung, die das Beispiel enthält.  
 Für jeden Projekts finden Sie eine Common Data Service Datei für die verwaltete Lösung. Der Name dieser Datei hängt vom Projektnamen des Beispiel ab, aber der Dateiname endet mit  `_managed.zip`.  
  
 Wenn Sie die Common Data ServiceLösung für Ihren Common Data Service Server importieren, gehen Sie folgendermaßen vor:  
  
1.  Entpacken Sie den Inhalt der heruntergeladenen Zip-Datei und suchen Sie die Lösungsdatei Common Data Service, die ebenfalls eine Zip-Datei sein wird. Wenn Sie beispielsweise das Beispiel `Basic Operations` heruntergeladen haben, suchen Sie nach der Zip-Datei Common Data Service der Lösung mit dem Namen `WebAPIBasicOperations\WebAPIBasicOperations_1_0_0_0_managed.zip`.  
  
2.  Gehen Sie in der Benutzeroberfläche Common Data Service zu **Einstellungen > Lösungen**. Auf dieser Seite sind alle Lösungen auf Ihrem Common Data Service Server aufgelistet. Nachdem Sie die Lösung importiert haben, wird der Lösungsname für dieses Beispiel in dieser Liste dargestellt(z. B.: **Web API Grundlagen-Vorgänge**).  
  
3.  Klicken Sie auf **Importieren**und führen Sie die Schritte des Import-Assistenten aus, um den Importvorgang abzuschließen.  
  
<a name="bkmk_howToRunSample"></a>   
## <a name="how-to-run-the-sample-to-see-the-script-in-action"></a>Wie ein Beispiel ausgeführt wird, um das Skript in Aktion zu sehen  
 Das Beispielprogramm wird als Webressource im Common Data Serviceausgeführt. Die importierte Lösung stellt eine Konfigurationsseite bereit, die Ihnen eine Option gibt, um Beispieldaten zu behalten oder zu löschen und eine Schaltfläche, um das Beispielprogramm zu starten.
  
 Um das Beispiel auszuführen, gehen Sie wie folgt vor:  
  
1.  Wählen Sie auf der Seite **Alle Lösungen** in Common Data Service, klicken Sie auf den Lösungsnamen (z.: Link **Internet von Grundlagen-Vorgänge** ). Dies öffnet die Eigenschaften der Lösung in einem neuen Fenster.  
  
2.  Im linken Navigationsmenü klicken Sie auf **Konfiguration**  
  
3.  Klicken Sie auf die Schaltfläche **Anfangsbeispiel**, um den Beispielcode auszuführen.  
  
<a name="bkmk_commonElements"></a>   
## <a name="common-elements-found-in-each-sample"></a>Allgemeine Elemente in jedem Beispiel  
 In der folgenden Liste werden einige allgemeine Elemente markiert, die Beispiele in jedem dieser anzeigt.  
  
-   Die `Sdk.startSample`-Funktion wird verwendet, wenn ein Benutzer auf die Schaltfläche **Anfangsbeispiel** klickt. Die `Sdk.startSample`-Funktion initialisiert globale Variablen und startet den ersten Vorgang in der Kette.  
  
-   Programmausgabe und -Fehlermeldungen werden an die Debuggerkonsole des Browsers gesendet. Um die Ausgabe zu sehen, öffnen Sie das Konsolenfenster zuerst, bevor Sie das Beispiel ausführen.  Drücken Sie F12, um auf die Entwicklerwerkzeuge, einschließlich des Konsolenfensters, in den Browsern Internet Explorer und Microsoft Edge zuzugreifen.  
  
-   Diese Beispiele verwenden die browser native [ES6-Promise](https://msdn.microsoft.com/library/dn802826\(v=vs.94\).aspx) Implementierung für moderne Browser, die sie unterstützen. Für Internet Explorer verwendet dieses Beispiel das [ES6-Promise polyfill](https://github.com/stefanpenner/es6-promise), da Internet Explorer der einzige von Common Data Service unterstützte Browser ist, der keine native Unterstützung für diese Funktion hat.  
  
     Versprechen sind nicht erforderlich. Ähnliche Interaktionen können mithilfe der Rückruffunktionen ausgeführt werden.  
  
-   Die `Sdk.request`-Funktion bearbeitet die Anforderung anhand der Informationen, die als Parameter übergeben werden. Je nach Anforderung eines Beispiels können die weitergegebenen Parameter unterschiedlich sein. Weitere Informationen finden Sie im Quellcode dieses Beispiels.  
  
    ```javascript  
    /**  
     * @function request  
     * @description Generic helper function to handle basic XMLHttpRequest calls.  
     * @param {string} action - The request action. String is case-sensitive.  
     * @param {string} uri - An absolute or relative URI. Relative URI starts with a "/".  
     * @param {object} data - An object representing an entity. Required for create and update actions.  
     * @returns {Promise} - A Promise that returns either the request object or an error object.  
     */  
    Sdk.request = function (action, uri, data) {  
        if (!RegExp(action, "g").test("POST PATCH PUT GET DELETE")) { // Expected action verbs.  
            throw new Error("Sdk.request: action parameter must be one of the following: " +  
                "POST, PATCH, PUT, GET, or DELETE.");  
        }  
        if (!typeof uri === "string") {  
            throw new Error("Sdk.request: uri parameter must be a string.");  
        }  
        if ((RegExp(action, "g").test("POST PATCH PUT")) && (data === null || data === undefined)) {  
            throw new Error("Sdk.request: data parameter must not be null for operations that create or modify data.");  
        }  
  
        // Construct a fully qualified URI if a relative URI is passed in.  
        if (uri.charAt(0) === "/") {  
            uri = clientUrl + webAPIPath + uri;  
        }  
  
        return new Promise(function (resolve, reject) {  
            var request = new XMLHttpRequest();  
            request.open(action, encodeURI(uri), true);  
            request.setRequestHeader("OData-MaxVersion", "4.0");  
            request.setRequestHeader("OData-Version", "4.0");  
            request.setRequestHeader("Accept", "application/json");  
            request.setRequestHeader("Content-Type", "application/json; charset=utf-8");  
            request.onreadystatechange = function () {  
                if (this.readyState === 4) {  
                    request.onreadystatechange = null;  
                    switch (this.status) {  
                        case 200: // Success with content returned in response body.  
                        case 204: // Success with no content returned in response body.  
                            resolve(this);  
                            break;  
                        default: // All other statuses are unexpected so are treated like errors.  
                            var error;  
                            try {  
                                error = JSON.parse(request.response).error;  
                            } catch (e) {  
                                error = new Error("Unexpected Error");  
                            }  
                            reject(error);  
                            break;  
                    }  
  
                }  
            };  
            request.send(JSON.stringify(data));  
        });  
    };  
    ```  
  
     Die `Sdk.request`-Funktion gibt ein Versprechen zurück. Wenn die Anforderung, die vom Versprechen eingebunden ist, abgeschlossen ist, wird das Versprechen entweder aufgelöst oder abgelehnt. Wenn es abgeschlossen wird, ist die Funktion in der folgenden `then`-Methode bezeichnet. Wenn sie zurückgewiesen wird, wird die Funktion in der folgenden `catch`-Methode bezeichnet. Wenn die Funktion in der `then` Methode selber ein Versprechen zurück gibt, kann die Kette von Vorgängen in nachfolgenden `then` Methoden weitergeführt werden. Das Zurückgeben eines Versprechens gibt uns die Möglichkeit, diese Beispielvorgänge so zusammenzufassen, dass sie von vielen Entwicklern gegenüber traditionellen Rückruffunktionen bevorzugt wird. Weitere Informationen Promise Sie unter [JavaScript promise](https://msdn.microsoft.com/library/dn802826\(v=vs.94\).aspx).  
  
### <a name="see-also"></a>Siehe auch

[Verwenden der Common Data Service-Web-API](overview.md)<br />
[Web API Beispiele](web-api-samples.md)<br />
[Web API Beispiele (C#)](web-api-samples-csharp.md)   
 
