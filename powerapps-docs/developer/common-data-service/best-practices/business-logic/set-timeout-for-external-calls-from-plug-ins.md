---
title: Timeout einstellen bei externen Aufrufen in einem Plugin | MicrosoftDocs
description: 'Begrenzen Sie den Zeitraum, in dem externe Aufrufe eine Antwort innerhalb von Plugins erwarten.'
services: ''
suite: powerapps
documentationcenter: na
author: JimDaly
manager: ryjones
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 08/19/2019
ms.author: jdaly
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="set-timeout-when-making-external-calls-in-a-plug-in"></a>Timeout einstellen bei externen Anrufen in einem Plug-in

**Kategorie**: Leistung

**Wirkungspotential**: Hoch

<a name='symptoms'></a>

## <a name="symptoms"></a>Symptome

Wenn ein Plug-in externe Webanfragen stellt, die nicht schnell reagieren, wartet das Plug-in auf die volle Standard-Timeout-Periode, bevor es fehlschlägt. Diese Dauer kann zu einer langen Transaktion führen, die andere Operationen bewirken kann. Wenn das Plug-in registriert ist:

- Synchron können die Benutzer Folgendes erleben:

    - Nicht reaktionsfähige, modellgetriebene Anwendungen
    - Langsame Kundeninteraktionen
    - Der Browser reagiert nicht mehr.

- Asynchron können Plug-in-Ausführungen einen längeren Zeitraum in Anspruch nehmen, bevor sie fehlschlagen. 

<a name='guidance'></a>

## <a name="guidance"></a>Anleitung

Der Standard-Timeout-Wert für .Net Http-Clients beträgt 100 Sekunden, also nur 20 Sekunden weniger als die Zeit, die dem Plugin zur Verfügung steht. Es ist am besten, eine voraussichtliche Basiszeit festzulegen, zu der ein aufrufender Dienst antworten wird. Je länger sie diese normale Reaktionszeit überschreitet, desto höher ist die Wahrscheinlichkeit, dass sie letztendlich scheitert. Als Best Practice für die Leistung ist es am besten, schnell auszufallen, anstatt die standardmäßige Timeout-Periode ablaufen zu lassen. Sie sollten die Zeitspanne steuern, in der Ihr Aufruf an den externen Dienst wartet.

Der Timeout-Wert, den Sie einstellen sollten, hängt vom Dienst ab. Wenn Sie beispielsweise die Leistung des Dienstes überwachen können, können Sie eine Dauer bestimmen, bei der 99,999% der Anfragen erfolgreich sind, und Ihre Timeout-Periode mit einigen Sekunden Puffer auf diese Dauer einstellen. Dadurch wird verhindert, dass die gelegentlichen Ausreißer einen übermäßigen Einfluss auf die Leistung Ihres Plugins haben.

Wenn Sie [System.Net.Http.Http.HttpClient Class](/dotnet/api/system.net.http.httpclient) verwenden, können Sie den Wert `Timeout` explizit setzen, wie in diesem Beispiel gezeigt, indem Sie den Timeout auf 15 Sekunden einstellen.

```csharp
using (HttpClient client = new HttpClient())
{
  client.Timeout = TimeSpan.FromMilliseconds(15000); //15 seconds
  client.DefaultRequestHeaders.ConnectionClose = true; //Set KeepAlive to false
  

  HttpResponseMessage response =  client.GetAsync(webAddress).Result; //Make sure it is synchonrous
  response.EnsureSuccessStatusCode();

  string responseText = response.Content.ReadAsStringAsync().Result; //Make sure it is synchonrous
  tracingService.Trace(responseText);
  //Log success in the Plugin Trace Log:
  tracingService.Trace("HttpClientPlugin completed successfully.");
}
```

Wenn Sie [System.Net.WebClient Class](/dotnet/api/system.net.webclient) verwenden, müssen Sie eine abgeleitete Klasse erstellen und die Basis [GetWebRequest Methode](/dotnet/api/system.net.webclient.getwebrequest) überschreiben, um den Timeout einzustellen:

```csharp
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
```

Dann können Sie diese Klasse in Ihrem Plugin-Code verwenden:

```csharp
using (CustomWebClient client = new CustomWebClient())
{
  byte[] responseBytes = client.DownloadData(webAddress);
  string response = Encoding.UTF8.GetString(responseBytes);
  tracingService.Trace(response);
  //Log success in the Plugin Trace Log:
  tracingService.Trace("WebClientPlugin completed successfully.");
}
```

<a name='seealso'></a>

### <a name="see-also"></a>Siehe auch

[Beispiel: Webzugriff über ein Sandkasten-Plug-In](../../org-service/samples/web-access-plugin.md)<br />
[KeepAlive auf falsch setzen, wenn Sie mit externen Hosts in einem Plug-in interagieren](set-keepalive-false-interacting-external-hosts-plugin.md)
