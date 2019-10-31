---
title: 'Beispiel: Webzugriff über ein Plugin (Common Data Service) | Microsoft Docs'
description: 'Dieses Beispiel zeigt, wie man ein Plug-in schreibt, das auf Ressourcen im Web (Netzwerk) zugreifen kann.'
ms.custom: ''
ms.date: 8/19/2019
ms.reviewer: ''
ms.service: powerapps
ms.topic: samples
author: JimDaly
ms.author: pehecke
manager: kvivek
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="sample-web-access-from-a-plug-in"></a>Beispiel: Webzugriff von einem Plug-in aus

Dieses Beispiel zeigt, wie man ein Plug-in schreibt, das auf Web-(Netzwerk-)Ressourcen wie einen Webservice oder Feed zugreifen kann. Es wird auch gezeigt, wie man die für diesen Anruf zulässige Zeitdauer begrenzt. Sie können das Beispiel von [hier](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/WebAccessPlugin) herunterladen.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

1. Um eine lokale Kopie zu erhalten, laden Sie den [Beispielbericht](https://github.com/Microsoft/PowerApps-Samples) herunter, oder klonen Sie ihn. Dieses Beispiel befindet sich unter PowerApps-Samples-master\cds\orgsvc\C#\WebAccessPlugin.
1. Es gibt zwei verschiedene Beispiele für Plug-in-Klassen: 
    - Das WebClientPlugin verwendet [WebClient Class](/dotnet/api/system.net.webclient).
    - Das HttpClientPlugin verwendet [HttpClient Class](/dotnet/api/system.net.http.httpclient).
1. Öffnen Sie die Beispiellösung in Visual Studio, navigieren Sie zu den Eigenschaften des Projekts und vergewissern Sie sich, dass die Assembly während des Builds signiert wird. Drücken Sie F6, um die Assembly des Samples zu erstellen (WebAccessPlugin.dll).
1. Führen Sie das Plug-in-Registrierungstool aus und registrieren Sie die Baugruppe in der Sandbox und Datenbank des Common Data Service-Servers. 
1. Geben Sie für beide Plug-In-Typen bei der Registrierung eines Schrittes eine Web-URI-Zeichenfolge (z.B. `http://www.microsoft.com`) im unsicheren Konfigurationsfeld an.
    - Der Standardwert `http://www.bing.com` wird verwendet, wenn kein Wert angegeben wird.
1. Verwenden Sie eine App oder einen Schreibcode, um den entsprechenden Vorgang auszuführen, um die Nachricht und die Entität aufzurufen, auf der Sie das Plug-in registriert haben.
1. Wenn das Plug-in ausgeführt wird und die Dauer des Aufrufs die 15-Sekunden-Grenze überschreitet, wird ein Fehler ausgelöst. Andernfalls sollte es gelingen.
1. Wenn Sie mit dem Testen fertig sind, heben Sie die Registrierung der Assembly auf und gehen Sie wie folgt vor.

## <a name="what-this-sample-does"></a>Funktionsweise:

Wenn das Plug-in ausgeführt wird, lädt es Webseitendaten von der angegebenen Webservice-Adresse (oder der Standardadresse) herunter. Wenn die Anforderung die 15-Sekunden-Grenze überschreitet, wird eine [InvalidPluginExecutionException](/dotnet/api/microsoft.xrm.sdk.invalidpluginexecutionexception) ausgelöst und Details in das Plugin Trace Log geschrieben.

- Wenn das Plugin `WebClientPlugin` fehlschlägt, schreibt es etwa folgendes in das Plugin Trace Log:
    ```
    Downloading the target URI: http://www.bing.com
    Exception: Microsoft.Xrm.Sdk.InvalidPluginExecutionException: The timeout elapsed while attempting to issue the request. ---> System.Net.WebException: The operation has timed out
      at System.Net.WebClient.DownloadDataInternal(Uri address, WebRequest& request)
      at System.Net.WebClient.DownloadData(Uri address)
      at PowerApps.Samples.WebClientPlugin.Execute(IServiceProvider serviceProvider)
      --- End of inner exception stack trace ---
      at PowerApps.Samples.WebClientPlugin.Execute(IServiceProvider serviceProvider)
    ```

- Wenn das Plugin `HttpClientPlugin` fehlschlägt, schreibt es etwa folgendes in das Plugin Trace Log:
    ```
    Downloading the target URI: http://www.bing.com
    Inner Exceptions:
      Exception: System.Threading.Tasks.TaskCanceledException: A task was canceled.
    Exception: Microsoft.Xrm.Sdk.InvalidPluginExecutionException: An exception occurred while attempting to issue the request.
       at PowerApps.Samples.HttpClientPlugin.Execute(IServiceProvider serviceProvider)
    ```
    Die [TaskCanceledException](/dotnet/api/system.threading.tasks.taskcanceledexception) ist etwas zweideutig bezüglich der Ursache für das Abbrechen der Aufgabe. Eine umfassendere Lösung, die zeigt, wie man Fehler aufgrund von Timeouts explizit erkennt, finden Sie in diesem Blogbeitrag: [Bessere Timeout-Verarbeitung mit HttpClient](https://thomaslevesque.com/2018/02/25/better-timeout-handling-with-httpclient/).

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

### <a name="setup"></a>Einrichten

1. Überprüft den unsicheren Konfigurationsparameter des Assemblies auf einen Webadressenwert, ansonsten wird der Standardwert verwendet.
2. Je nachdem, welches Plug-in registriert ist, wird entweder die Klasse [WebClient Class](/dotnet/api/system.net.webclient) oder [HttpClient Class](/dotnet/api/system.net.http.httpclient) von der `Execute`-Methode des Plug-ins verwendet, um Webseiten-Daten herunterzuladen.
3. Wenn der Aufruf die angegebene Dauer von 15 Sekunden überschreitet, wird eine [InvalidPluginExecutionException](/dotnet/api/microsoft.xrm.sdk.invalidpluginexecutionexception) ausgelöst und Details über den Fehler in das Plugin Trace Log geschrieben.

### <a name="demonstrate"></a>Demonstrieren

#### <a name="webclientplugin-plugin"></a>WebClientPlugin Plugin Plugin

1. Verwendet eine abgeleitete `CustomWebClient`-Klasse, um die Eigenschaft [WebRequest.Timeout](/dotnet/api/system.net.webrequest.timeout) einzustellen, die in der Klasse `WebClient` nicht verfügbar ist.

   ````
    /// <summary>
    /// A class derived from WebClient with 15 second timeout and KeepAlive disabled
    /// </summary>
    public class CustomWebClient : WebClient
    {
      protected override WebRequest GetWebRequest(Uri address)
      {
        HttpWebRequest request = (HttpWebRequest)base.GetWebRequest(address);
        if (request != null)
        {
          request.Timeout = 15000; //15 Seconds
          request.KeepAlive = false;
          
        }
        return request;
      }
    }
    ````

1. Verwendet die [WebClient.DownloadData Methode](/dotnet/api/system.net.webclient.downloaddata), um die Daten von der Ressource herunterzuladen.
1. Zeigt, wie man die erwartete [WebException Class](/dotnet/api/system.net.webexception) analysiert und die [Status-Eigenschaft](/dotnet/api/system.net.webexception.status) verwendet, um festzustellen, ob die Ursache des Fehlers auf ein Timeout zurückzuführen ist.

#### <a name="httpclientplugin-plugin"></a>HttpClientPlugin-Plugin-Plugin

1. Verwendet die [HttpClient Class](/dotnet/api/system.net.http.httpclient) und setzt die [Timeout-Eigenschaft](/dotnet/api/system.net.http.httpclient.timeout), um die zulässige Zeit für die Ausführung der Operation zu begrenzen.
1. Fängt die erwartete [AggregateException Class](/dotnet/api/system.aggregateexception) ab und untersucht die inneren Ausnahmen auf die erwartete [TaskCanceledException](/dotnet/api/system.threading.tasks.taskcanceledexception).


### <a name="see-also"></a>Siehe auch

[Zugriff auf externe Web-Ressourcen](../../access-web-services.md)<br/>
[Registrieren eines Plug-Ins](../../register-plug-in.md)