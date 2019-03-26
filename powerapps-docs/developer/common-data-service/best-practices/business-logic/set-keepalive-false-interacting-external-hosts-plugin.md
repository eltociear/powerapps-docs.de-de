---
title: 'Setzen Sie KeepAlive auf false, wenn Sie mit externen Hosts in einem Plugin interagieren | MicrosoftDocs'
description: 'Die KeepAlive-Eigenschaft, die im HTTP-Request-Header auf true gesetzt oder nicht explizit als false definiert ist, kann zu längeren Ausführungszeiten von Plug-Ins führen.'
services: ''
suite: powerapps
documentationcenter: na
author: jowells
manager: austinj
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 12/12/2018
ms.author: jowells
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="set-keepalive-to-false-when-interacting-with-external-hosts-in-a-plug-in"></a>KeepAlive auf falsch setzen, wenn Sie mit externen Hosts in einem Plug-in interagieren

**Kategorie**: Leistung

**Wirkungspotential**: Hoch

<a name='symptoms'></a>

## <a name="symptoms"></a>Symptome

Wenn ein Plug-in externe Web-Anfragen stellt und versucht, `KeepAlive` auf einer geschlossenen Verbindung zu verwenden, kann das Plug-in die Web-Anfrage letztendlich nicht ausführen. Wenn das Plug-in jedoch registriert ist:

- Synchron können die Benutzer Folgendes erleben:

    - Nicht reaktionsfähige, modellgetriebene Anwendungen
    - Langsame Kundeninteraktionen
    - Der Browser reagiert nicht mehr.

- Asynchron können Plug-in-Ausführungen einen längeren Zeitraum in Anspruch nehmen, bevor sie fehlschlagen. 

<a name='guidance'></a>

## <a name="guidance"></a>Anleitung

1. In HTTP 1.1 gelten alle Verbindungen als persistent (`KeepAlive` ist wahr), sofern nicht anders angegeben. Da Plug-Ins isoliert laufen, übersetzt der Sandbox-Dienst sie in kurzlebige Ausführungen, die im Allgemeinen nicht von `KeepAlive` profitieren würden. Um Probleme bei der Verbindung zu externen Diensten zu vermeiden, empfehlen wir, `KeepAlive` innerhalb von Plug-Ins zu deaktivieren. Wenn Ihr spezieller externer Dienst aus Performance-Gründen von der Verwendung persistenter Sitzungen profitieren würde, senden Sie aktiv eine `KeepAlive` im Abstand von der Hälfte des Leerlauf-Timeout (30 Sekunden), damit die Verbindung nicht geschlossen wird.

Die folgenden Beispiele zeigen, wie Sie `KeepAlive` explizit auf false definieren, je nachdem, mit welcher Methode Sie eine Verbindung zu einem externen Dienst herstellen:

- `HttpWebRequest` 
    ```csharp
    HttpWebRequest req = WebRequest.Create("https://www.contoso.com/api/stuff") as HttpWebRequest;
    
    if (req != null)
    {
        req.KeepAlive = false;
        HttpWebResponse response = (HttpWebResponse)req.GetResponse();
    }
    ```

-  `WebClient` 
    ```csharp
    private string RequestString(Uri location)
    {
        using (var client = new MyWebClient())
        {
            return client.DownloadString(location);
        }
    }

    internal class MyWebClient : WebClient
    {
        // Overrides the GetWebRequest method and sets keep alive to false
        protected override WebRequest GetWebRequest(Uri address)
        {
            HttpWebRequest req = (HttpWebRequest)base.GetWebRequest(address);
            req.KeepAlive = false;

            return req;
        }
    }
    ```

- `WCF ClientBase< T >`-Instanz 
    ```csharp
    OrganizationServiceClient client = null;
    
    try
    {
        var address = new EndpointAddress("https://www.contoso.com/Custom.svc");
        var transport = new HttpsTransportBindingElement();
        transport.KeepAliveEnabled = false;
    
        var binding = new CustomBinding(transport);
    
        client = new OrganizationServiceClient(binding, address);
    
        WhoAmIResponse response = client.Execute(new WhoAmIRequest()) as WhoAmIResponse;
    }
    catch (Exception ex)
    {
        client.Abort();
    }
    finally
    {
        client.Close();
    }
    ```

- `WCF ChannelFactory< TChannel >` Static-Methode 
    ```csharp
    IRequestChannel channel = null;
    try
    {
        var address = new EndpointAddress("https://www.contoso.com/Custom.svc");
        var transport = new HttpsTransportBindingElement();
        transport.KeepAliveEnabled = false;
    
        var binding = new CustomBinding(transport);
    
        channel = ChannelFactory<IRequestChannel>.CreateChannel(binding, address);
    
        Message request = Message.CreateMessage(MessageVersion.Soap12, "some action", "message body");
        Message response = channel.Request(request);
    }
    catch (Exception ex)
    {
        channel.Abort();
    }
    finally
    {
        channel.Close();
    }
    ```

- `WCF ChannelFactory< TChannel >`-Instanz 
    ```csharp
    ChannelFactory<IRequestChannel> factory = null;
    IRequestChannel channel = null;
    try
    {
        var address = new EndpointAddress("https://www.contoso.com/Custom.svc");
        var transport = new HttpsTransportBindingElement();
        transport.KeepAliveEnabled = false;
    
        var binding = new CustomBinding(transport);
    
        factory = new ChannelFactory<IRequestChannel>(binding, address);
        channel = factory.CreateChannel();
    
        Message request = Message.CreateMessage(MessageVersion.Soap12, "some action", "message body");
        Message response = channel.Request(request);
    }
    catch (Exception ex)
    {
        channel.Abort();
        factory.Abort();
    }
    finally
    {
        channel.Close();
        factory.Close();
    }
    ```

<a name='problem'></a>

## <a name="problematic-patterns"></a>Problematische Muster

Um den Standardwert von `KeepAlive` für die Nicht-WCF-Interaktionen zu überschreiben, sollte der Ansatz gewählt werden, HttpWebRequest zu nutzen, um die Interaktionen mit dem Webserver durchzuführen, aber zuerst die Eigenschaft `KeepAlive` auf false zu setzen.

Die folgenden Beispiele zeigen das problematische Muster basierend auf der Methode, mit der Sie eine Verbindung zu einem externen Dienst herstellen:

> [!WARNING]
> Diese Muster sollten vermieden werden.

- `HttpWebRequest`

    ```csharp
    WebRequest request = WebRequest.Create("https://www.contoso.com/api/stuff");
    //KeepAlive not explicitly defined as true.  However, default behavior is KeepAlive = true.
    HttpWebResponse response = (HttpWebResponse)request.GetResponse();
    response.Close();
    ```

- `WebClient`

    ```csharp
    using (var client = new WebClient())
    {
        string url = "https://www.contoso.com/api/stuff";
        //KeepAlive not explicitly defined as true.  However, default behavior is KeepAlive = true.
        string result = client.DownloadString(url);
    }
    ```

- `WCF ClientBase< T >`-Instanz

    ```csharp
    OrganizationServiceClient client = null;
    
    try
    {
        var address = new EndpointAddress("https://www.contoso.com/Custom.svc");
        var binding = new BasicHttpsBinding();
        //KeepAlive not explicitly defined as true.  However, default behavior is KeepAlive = true.
        client = new OrganizationServiceClient(binding, address);
    
        WhoAmIResponse response = client.Execute(new WhoAmIRequest()) as WhoAmIResponse;
    }
    catch (Exception ex)
    {
        client.Abort();
    }
    finally
    {
        client.Close();
    }
    ```

- `WCF ChannelFactory< TChannel >` Static-Methode

    ```csharp
    IRequestChannel channel = null;
    try
    {
        var address = new EndpointAddress("https://www.contoso.com/Custom.svc");
        var binding = new BasicHttpsBinding();
        //KeepAlive not explicitly defined as true.  However, default behavior is KeepAlive = true.
    
        channel = ChannelFactory<IRequestChannel>.CreateChannel(binding, address);
    
        Message request = Message.CreateMessage(MessageVersion.Soap12, "some action", "message body");
        Message response = channel.Request(request);
    }
    catch (Exception ex)
    {
        channel.Abort();
    }
    finally
    {
        channel.Close();
    }
    ```

- `WCF ChannelFactory< TChannel >`-Instanz

    ```csharp
    ChannelFactory<IRequestChannel> factory = null;
    IRequestChannel channel = null;
    try
    {
        var address = new EndpointAddress("https://www.contoso.com/Custom.svc");
        var binding = new BasicHttpsBinding();
        //KeepAlive not explicitly defined as true.  However, default behavior is KeepAlive = true.
    
        factory = new ChannelFactory<IRequestChannel>(binding, address);
        channel = factory.CreateChannel();
    
        Message request = Message.CreateMessage(MessageVersion.Soap12, "some action", "message body");
        Message response = channel.Request(request);
    }
    catch (Exception ex)
    {
        channel.Abort();
        factory.Abort();
    }
    finally
    {
        channel.Close();
        factory.Close();
    }
    ```

<a name='additional'></a>

## <a name="additional-information"></a>Weitere Informationen

Plug-Ins, die mit externen Diensten interagieren, können zu ungewöhnlich verlängerten Ausführungszeiten führen. Das Problem ist auf die ([KeepAlive-Eigenschaft](https://msdn.microsoft.com/library/system.net.httpwebrequest.keepalive.aspx)) von HTTP-Anfragen zurückzuführen, die an externe Webserver ausgegeben werden. Wenn die Eigenschaft `KeepAlive` auf true gesetzt oder gar nicht definiert ist (Standardverhalten ist wahr), kann der Sandbox-Client auf dem Server weiterhin versuchen, eine persistente Sitzung zu verwenden, obwohl die Sitzung aufgrund der Konfiguration des Netzwerkgeräts abgelaufen ist. Die Ursache für die verlängerte Ausführungszeit liegt darin, dass das Netzwerk die Anfrage erneut versucht, bis die Verbindung letztendlich zurückgesetzt wird.

> [!IMPORTANT]
> Dies betrifft alle Codes, die HTTP-Requests an einen Webserver mit [System.Net.WebClient](https://msdn.microsoft.com/library/system.net.webclient.aspx), [System.Net.WebRequest](https://msdn.microsoft.com/library/system.net.webrequest.aspx) oder [System.Net.HttpWebRequest](https://msdn.microsoft.com/library/system.net.httpwebrequest.aspx) sowie Windows Communications Foundation (WCF) Client-Kommunikation über eine HTTP-Transportbindung direkt oder indirekt über [ChannelFactory<TChannel>](https://docs.microsoft.com/dotnet/api/system.servicemodel.channelfactory-1) oder [ClientBase<T>](https://docs.microsoft.com/dotnet/api/system.servicemodel.clientbase-1) initiieren.

Dieses Verhalten ist für Endbenutzer und die traditionelle Protokollierung transparent, da die Ausführung auf Verzögerungen im Netzwerk zurückzuführen ist.  Wenn das Plug-in als synchrones Ereignis registriert wurde, konnten Benutzer während der registrierten Vorgänge intermittierende Performance-Probleme auftreten, die zu einer mangelnden Reaktionsfähigkeit modellgetriebener Anwendungen führen konnten.  Wenn das Plug-in asynchron registriert ist, wird das Problem nur beobachtet, wenn die Ausführungszeiten des Plug-ins überprüft werden und die Ausführung länger dauert als normal oder erwartet.

<a name='seealso'></a>

### <a name="see-also"></a>Siehe auch

[Beispiel: Webzugriff über ein Sandkasten-Plug-In](../../org-service/samples/web-access-plugin.md)<br />
[Load Balancing (WCF)](https://msdn.microsoft.com/library/ms730128.aspx)<br />
[HttpTransportBindingElement.KeepAliveEnabled-Eigenschaft](https://msdn.microsoft.com/library/system.servicemodel.channels.httptransportbindingelement.keepaliveenabled.aspx)<br />
[HttpWebRequest.KeepAlive-Eigenschaft](https://msdn.microsoft.com/library/system.net.httpwebrequest.keepalive.aspx)<br />
