---
title: Service Protection API-Beschränkungen (Common Data Service) | Microsoft Docs
description: Verstehen Sie die Serviceschutzgrenzen für API-Anforderungen.
ms.custom: ''
ms.date: 11/23/2019
ms.reviewer: pehecke
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: f46360623cd3cf530f9d6b2a0c7c1aecd3c66c0c
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3156482"
---
# <a name="service-protection-api-limits"></a>API-Grenzwerte für den Serviceschutz

Um eine konsistente Verfügbarkeit und Leistung für alle zu gewährleisten, wenden wir einige Einschränkungen für die Verwendung von APIs anwenden. Wir begrenzen die Anzahl der gleichzeitigen Verbindungen pro Benutzerkonto, die Anzahl der API-Anforderungen pro Verbindung und die Ausführungszeit, die für jede Verbindung verwendet werden kann. Diese werden innerhalb eines fünfminütigen Schiebefensters ausgewertet. Wenn einer dieser Grenzwerte überschritten wird, gibt die Plattform eine Ausnahme zurück.

Der Serviceschutz API Grenzwert stellt sicher, dass Benutzer, die Anwendungen ausführen, sich nicht aufgrund vorhandener Ressourceneinschränkungen gegenseitig stören. Die Grenzwerte haben keine Auswirkungen auf normale Plattformbenutzer. Nur Anwendungen, die eine sehr große Anzahl an API-Anforderungen ausführen, sind möglicherweise betroffen. Der Grenzwert bietet einen gewissen Schutz vor dem unwillkürlichen und unerwarteten Anstieg des Anforderungsvolumens, das die Verfügbarkeit und Leistungsfähigkeit der Common Data Service Plattform gefährdet.

Da Plug-Ins und benutzerdefinierte Workflow-Aktivitäten auf dem Server unabhängig eines angemeldeten Benutzers ausgeführt werden, zählen Aufrufe vom Plugin-Code nicht zu diesen Serviceschutz API-Aufruflimit. 

## <a name="limits"></a>Begrenzungen

> [!IMPORTANT]
> Diese Grenzwerte gelten pro Webserver. Jede Skalierungsgruppe verfügt über mehrere Webserver, die je nach Lastenausgleich jede Anforderung verarbeiten können. Diese Zahlen repräsentieren einen einzelnen Webserver und daher aufgrund dieser Grenzwerte das niedrigstmögliche Durchsatzniveau. Ihr tatsächlicher Durchsatz sollte höher sein.
> 
> Sie werden signifikante Unterschiede zwischen Testumgebungen und Produktionsumgebungen feststellen. Testumgebungen sind weniger Ressourcen zugeordnet, sodass sie diese Grenzwerte leichter erreichen als Produktionsumgebungen.
> 
> Konzentrieren Sie sich nicht zu sehr auf die Zahlen hier. Es ist wichtig zu verstehen, dass Anwendungen, die von umfangreichen Datenoperationen abhängen, so konzipiert sein sollten, dass sie auf vom Server gesendete Signale reagieren, um anzuzeigen, wann die Grenzwerte erreicht sind. Versuchen Sie nicht, hard-Code-Lösungen basierend auf den Zahlen zu verwenden. Verwenden Sie stattdessen die unten beschriebenen Techniken, um den höchstmöglichen Durchsatz zu erzielen, indem Sie auf die vom Dienst gesendeten Signale reagieren.

Serviceschutzbeschränkungen gehen davon aus, dass die Anwendung mehrere Threads verwendet, um die Leistung zu maximieren. Jeder Thread stellt eine separate Verbindung dar und jede Verbindung wird in einem Schiebefenster von 5 Minuten (300 Sekunden) ausgewertet.

Innerhalb dieses 5-minütigen Schiebefensters gibt es drei Aspekte, die wie in der folgenden Tabelle beschrieben gemessen werden:

|Kennzahl|Beschreibung|Limit pro Webserver|
|--|--|--|
|Anzahl von Anforderungen|Die tatsächliche Anzahl der Anfragen pro Verbindung.|6000|
|Ausführungszeit|Die kombinierte Dauer für alle Verbindungen, die dasselbe Benutzerkonto verwenden| 20 Minuten (1200 Sekunden)|
|Anzahl Verbindungen|Die Anzahl der Verbindungen, die dasselbe Benutzerkonto verwenden|52|

Die Kombination von **Anzahl der Anfragen** und **Ausführungszeit** berücksichtigt die Tatsache, dass einige Vorgänge mehr Systemressourcen erfordern als andere. Das Ausführen einer komplexen Abfrage erfordert mehr Systemressourcen als das Erstellen oder Aktualisieren eines einzelnen Datensatzes.

Während API-Aufrufe aus Plug-In-Code nicht mit der Anzahl der Anforderungen verrechnet werden, wird die Ausführungszeit dieser Aufrufe auf den ursprünglichen Aufruf angewendet.

Bei einigen bekannten Systemvorgängen mit langer Laufzeit, wie z. B. ImportSolution, wird die Ausführungszeit nicht vollständig in die Berechnung des Grenzwerts einbezogen. Der Beitrag dieser Aufrufe zur Limitberechnung ist auf 5 Minuten begrenzt, wenn die tatsächliche Ausführungszeit größer ist.

Falls bei Ihrer Anwendung die Möglichkeit besteht, diese Limitenbegrenzung zu überschreiten, beachten Sie bitte die Leitlinien, die Sie im Abschnitt [Was ist zu tun, wenn meine Anwendung die Begrenzung überschreitet?](#what-should-i-do-if-my-application-exceeds-the-limit) unten finden.

Abhängig von der Art der Daten, die Sie verarbeiten, können Sie die Anzahl der gleichzeitigen Verbindungen anpassen, um den maximalen Durchsatz zu erzielen. Wenn jede Operation relativ schnell ist, verwenden Sie mehr Verbindungen.

## <a name="what-happens-when-the-limit-is-exceeded"></a>Was geschieht, wenn die Begrenzung überschritten wird?

Wenn die Begrenzung überschritten wird, wird für alle Anforderungen derselben Verbindung eine Fehlerantwort zurückgegeben.

Wenn Sie die .NET-SDK-Assemblys verwenden, reagiert die Plattform mit einem `FaultException<OrganizationServiceFault>` WCF-Fehler.  

| Fehlercode | Meldung |
|------------|-------------------------------------|
|`-2147015902`|`Number of requests exceeded the limit of 6000, measured over time window of 300 seconds.`|
|`-2147015903`|`Combined execution time of incoming requests exceeded limit of 1,200,000 milliseconds over time window of 300 seconds. Decrease number of concurrent requests or reduce the duration of requests and try again later.`|
|`-2147015898`|`Number of concurrent requests exceeded the limit of 52`|

Wenn Sie HTTP-Anforderungen mit der Web-API verwenden, beinhaltet die Antwort dieselbe Nachricht aber mit:<br />
`StatusCode` : `429`

Von allen Anforderungen werden diese Fehlerantworten zurückgegeben, bis das Volumen der API-Anforderungen unter die Begrenzung fällt. Wenn Sie diese Antworten erhalten, sollten von Ihrer Anwendung keine weiteren API-Anforderungen mehr gesendet werden, bis das Volumen der Anforderungen unterhalb der Begrenzung liegt.

> [!TIP]
> Wenn Sie HTTP-Anforderungen mit der Web-API verwenden, können Sie die verbleibenden Grenzwerte mit den folgenden HTTP Header verfolgen:
> 
> |Kopfzeile  |Wertbeschreibung  |
> |---------|---------|
> |`x-ms-ratelimit-burst-remaining-xrm-requests` |Die verbleibende Anzahl von Anforderungen für diese Verbindung|
> |`x-ms-ratelimit-time-remaining-xrm-requests`  |Die kombinierte verbleibende Dauer für alle Verbindungen, die dasselbe Benutzerkonto verwenden|

## <a name="what-should-i-do-if-my-application-exceeds-the-limit"></a>Was muss ich tun, wenn meine Anwendung die Begrenzung überschreitet?

Wenn von Ihrer Anwendung die Begrenzung überschritten wird, gibt die Fehlerantwort vom Server möglicherweise an, wie lange Sie warten sollten, bis Sie weitere Anforderungen übermitteln. Das Antwortobjekt ist etwas anders, wenn Sie SDK-Assemblys oder HTTP-Anforderungen mit der Web-API verwenden.

Eine Diskussion zu bewährten Methoden finden Sie unter [Bewährte Methoden in der Azure-Architektur zur Behandlung von vorübergehenden Fehlern](/azure/architecture/best-practices/transient-faults)

[Das Polly-Projekt](https://www.thepollyproject.org/) ist eine Bibliothek mit Funktionen zum Umgang mit vorübergehenden Fehlern mithilfe von Ausführungsrichtlinien.

### <a name="http-requests-with-the-web-api"></a>HTPP Anforderungen funktionieren mit der Web-API

Wenn Sie auf einen 429-Fehlercode stoßen, können Sie nach dem `Retry-After` HTTP Header suchen, der in der Fehlerantwort enthalten ist. Diese enthält einen Wert in Sekunden, der angibt, wie lange Sie warten müssen, bis Sie eine Folgeanforderung erteilen. Weitere Informationen: [MDN-Webdokumente – Neuversuch danach](https://developer.mozilla.org/docs/Web/HTTP/Headers/Retry-After)

### <a name="sdk-assemblies"></a>SDK-Assemblys

> [!NOTE]
> Sie müssen diese Muster nicht anwenden, wenn:
>
>  - Ihr Code wird in einem Plug-In oder in einer benutzerdefinierten Workflowaktivität ausgeführt. Sie müssen diese Muster nicht anwenden, da in diesen Fällen keine Serviceschutzbeschränkungen angewendet werden.
>  - Sie verwenden <xref:Microsoft.Xrm.Tooling.Connector>.<xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient>. Diese Muster sind in diesen Client integriert. Dies ist die empfohlene Proxy-Klasse für Client-Anwendungen.
>
> Sie müssen diese Muster anwenden, wenn Sie das <xref:Microsoft.Xrm.Sdk.Client>.<xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceProxy> verwenden oder <xref:Microsoft.Xrm.Sdk.WebServiceClient>.<xref:Microsoft.Xrm.Sdk.WebServiceClient.OrganizationWebProxyClient> Proxy-Klassen.

Wenn Sie die SDK-Assemblys mit den <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceProxy> oder <xref:Microsoft.Xrm.Sdk.WebServiceClient.OrganizationWebProxyClient> Proxy-Klassen verwenden, können Sie nach dem `Retry-After` Verzögerungswert in <xref:Microsoft.Xrm.Sdk.OrganizationServiceFault>.<xref:Microsoft.Xrm.Sdk.BaseServiceFault.ErrorDetails> suchen Eigenschaft, mithilfe des Schlüssels `"Retry-After"`suchen. Der zurückgegebene Wert ist ein [TimeSpan](/dotnet/api/system.timespan)-Objekt.

## <a name="net-sdk-assembly-example"></a>.NET SDK-Assembly-Beispiel

Im folgenden Beispiel wird die [„Retry”-Klasse](#retry-class) verwendet, die unten beschrieben wird, um ein Konto mithilfe der Methode <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.RetrieveMultiple*>-abzurufen. Methode. Wenn die Anforderung fehlschlägt, weil eine API-Begrenzung überschritten wurde, wartet die Klasse `Retry` gemäß einer Verzögerung, die vom Server festgelegt ist und versucht es erneut.

```csharp
var qe = new QueryExpression("account") { TopCount = 1 };
EntityCollection result = Retry.Do(() => service.RetrieveMultiple(qe));
```

### <a name="retry-class"></a>„Retry”-Klasse

Die `Retry`-Klasse zeigt, wie Anforderungen wiederholt werden, die mit vorübergehenden Fehlern basierend auf bekannten <xref:Microsoft.Xrm.Sdk.OrganizationServiceFault>-Fehlercodes fehlschlagen. Die `Retry`-Klasse wartet vor dem Neuversuch. Wenn vom Fehler eine Wiederholungsverzögerung angegeben wird, wartet sie gemäß der vom Server angegebenen Verzögerung. Anderenfalls wird ein exponentieller Backoff verwendet, um die Verzögerung auf Grundlage der Anzahl der vorgenommenen Wiederholungsversuche zu berechnen.

```csharp
using System;
using System.ServiceModel;
using System.Threading;

public class Retry
{
    private const int RateLimitExceededErrorCode = -2147015902;
    private const int TimeLimitExceededErrorCode = -2147015903;
    private const int ConcurrencyLimitExceededErrorCode = -2147015898;

    public static TResult Do<TResult>(Func<TResult> func, int maxRetries = 3)
    {
        int retryCount = 0;

        while (true)
        {
            try
            {
                return func();
            }
            catch (FaultException<Microsoft.Xrm.Sdk.OrganizationServiceFault> ex) 
                when (IsTransientError(ex))
            {
                if (++retryCount >= maxRetries)
                {
                    throw;
                }

                if (ex.Detail.ErrorCode == RateLimitExceededErrorCode)
                {
                    // Use Retry-After delay when specified
                    delay = (TimeSpan)ex.Detail.ErrorDetails["Retry-After"];
                }
                else
                {
                    // else use exponential backoff delay
                    delay = TimeSpan.FromSeconds(Math.Pow(2, retryCount));
                }

                Thread.Sleep(delay);
            }
        }
    }

    private static bool IsTransientError(FaultException<Microsoft.Xrm.Sdk.OrganizationServiceFault> ex)
    {
        // You can add more transient fault codes to retry here
        if (ex.Detail.ErrorCode == RateLimitExceededErrorCode ||
            ex.Detail.ErrorCode == TimeLimitExceededErrorCode ||
            ex.Detail.ErrorCode == ConcurrencyLimitExceededErrorCode)
        {
            return true;
        }

        return false;
    }
}
```

### <a name="see-also"></a>Siehe auch

[Verwalten Power Platform / Lizenzierung und Lizenzverwaltung / Anforderungsgrenzen und -zuordnungen](/power-platform/admin/api-request-limits-allocations)<br />
[Common Data Service Übersicht über API-Grenzwerte](../../maker/common-data-service/api-limits-overview.md)<br />
[Verwendung der Common Data Service Web-API](webapi/overview.md)<br />
[Verwendung von Common Data Service Organisationsdienst](org-service/overview.md)
