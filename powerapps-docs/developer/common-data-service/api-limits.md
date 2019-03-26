---
title: API-Einschränkungen (Common Data Service für Apps) | Microsoft Docs
description: Verstehen Sie die Begrenzungen für API-Anforderungen.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: MicroSri
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="api-limits"></a>API-Begrenzungen

Ab 19. März 2018 wird die Anzahl der API-Anforderungen, die von jedem Benutzer erteilt werden können, pro Organisationsinstanz innerhalb eines fünfminütigen Intervalls begrenzt. Wenn dieser Grenzwert überschritten wird, wird eine Ausnahme durch die Plattform ausgelöst.

Mit dieser Einschränkung wird sichergestellt, dass Benutzer nicht durch andere Benutzer beeinträchtigt werden, die Anwendungen mit außerordentlich hohen Anforderungen an Server ausführen. Die Einschränkung hat keine Auswirkungen auf normale Plattformbenutzer. Nur Anwendungen, die eine sehr große Anzahl an API-Anforderungen ausführen, sind betroffen. Gemäß der Analyse von Telemetriedaten liegt dieser Grenzwert innerhalb des Rahmens der meisten Anwendungen, die eine große Anzahl an API-Anforderungen ausführen. Er bietet einen gewissen Schutz vor dem unwillkürlichen und unerwarteten Anstieg des Anforderungsvolumens, das die Verfügbarkeit und Leistungsfähigkeit der Common Data Service for Apps-Plattform gefährdet.

Falls bei Ihrer Anwendung die Möglichkeit besteht, diese Begrenzung zu überschreiten, beachten Sie bitte die Leitlinien, die Sie im Abschnitt [Was ist zu tun, wenn meine Anwendung die Begrenzung überschreitet?](#what-should-i-do-if-my-application-exceeds-the-limit) unten finden.

## <a name="what-is-the-limit"></a>Wie hoch ist die Begrenzung?

Jeder Benutzer kann bis zu 60.000 API-Anforderungen pro Organisationsinstanz innerhalb eines fünfminütigen gleitenden Intervalls erteilen.

## <a name="what-happens-when-the-limit-is-exceeded"></a>Was geschieht, wenn die Begrenzung überschritten wird?

Wenn die Begrenzung überschritten wird, werden bei sämtlichen weiteren Anforderungen Fehlerantworten zurückgegeben.

Wenn Sie die .NET SDK-Assemblys verwenden, reagiert die Plattform mit einem `FaultException<OrganizationServiceFault>` WCF-Fehler mit dem Fehlercode `-2147015902` und der Meldung `Number of requests exceeded the limit of 60000, measured over time window of 300 seconds.`

Wenn Sie HTTP-Anforderungen verwenden, beinhaltet die Antwort diese Eigenschaften:<br />
`StatusCode` : `429`<br />
`Message` : `Number of requests exceeded the limit of 60000, measured over time window of 300 seconds.`

Von allen Anforderungen werden diese Fehlerantworten zurückgegeben, bis das Volumen der API-Anforderungen unter die Begrenzung fällt. Wenn Sie diese Antworten erhalten, sollten von Ihrer Anwendung keine weiteren API-Anforderungen mehr gesendet werden, bis das Volumen der Anforderungen unterhalb der Begrenzung liegt.

## <a name="how-is-this-limit-calculated"></a>Wie wird dieser Grenzwert berechnet?

Innerhalb einer Organisationsinstanz werden API-Anforderungen, die von jedem der lizenzierten Benutzer vorgenommen werden (einschließlich der lizenzierten Identität, die zum Ausführen der Automatisierung verwendet wird) anhand dieser Begrenzung gemessen. Die Plattform misst die Anzahl der API-Anforderungen, die in fünf Minuten erteilt werden, wobei sie ständig im Rahmen eines bestimmten Zeitraums gleitet. Während jedes Messintervalls wird am Ende von fünf Minuten die Anzahl der vom Benutzer erteilten API-Anforderungen gezählt. In der Abbildung unten erteilen drei Benutzer API-Aufrufanforderungen über einen sechsminütigen Zeitraum.  

![api-limit-implementation](media/api-limit-implementation-1.png)

|Intervall|Beschreibung|
|--|--|
|A|Am Ende von fünf Minuten beträgt die Gesamtanzahl von API-Anforderungen für Benutzer eins 6.000, für Benutzer zwei 3.000 und für Benutzer drei 10.000.|
|F|Bei 5+X Minuten, wobei X ein konstanter Zeitabschnitt ist (beispielsweise ein paar Sekunden), was die gleitende Intervallkonstante ist, wird von der Plattform die Gesamtanzahl für jeden dieser Benutzer gemessen, die immer noch aktiv sind. Gemäß dem Diagramm oben wäre dies Benutzer 1 = 7.000, Benutzer 2 = 6.000 und Benutzer 3 = 25.000. Alle kumulativen Anzahlen sind immer noch unterhalb der Begrenzung von 60.000. Das heißt, dass keine Verhaltensänderung für diese Benutzer erwartet wird.|
|C|Mit der Zeit und sobald 5+2X erreicht werden, erteilt Benutzer drei ungefähr 40.000 API-Anforderungen, während Benutzer eins und Benutzer zwei jeweils 8.000 und 9.000 Aufrufe vornehmen. Dies führt dazu, dass Benutzer drei 65.000 API-Anforderungen innerhalb von fünf Minuten erreicht, was bewirkt, dass 5.000 (65.000-60.000=5.000) seiner Anforderungen abgelehnt werden.|

> [!NOTE]
> Anforderungen, die mehrere API-Anforderungen, wie <xref:Microsoft.Xrm.Sdk.Messages.ExecuteMultipleRequest> oder <xref:Microsoft.Xrm.Sdk.Messages.ExecuteTransactionRequest> mithilfe der .NET SDK-Assemblys oder `$batch` mithilfe der Web-API ausführen, zählen als einzelne Anforderung, um diese Begrenzung zu berechnen. Allerdings müssen diese API-Anforderungen die [Laufzeitbegrenzungen](org-service/execute-multiple-requests.md#limitations) für diese Typen von Vorgängen einhalten.

## <a name="what-should-i-do-if-my-application-exceeds-the-limit"></a>Was muss ich tun, wenn meine Anwendung die Begrenzung überschreitet?

Wenn von Ihrer Anwendung die Begrenzung überschritten wird, gibt die Fehlerantwort vom Server an, wie lange Sie warten sollten, bis Sie weitere Anforderungen übermitteln. Das Antwortobjekt ist etwas anders, wenn Sie SDK-Assemblys oder HTTP-Anforderungen verwenden.

Eine Diskussion zu bewährten Methoden finden Sie unter [Bewährte Methoden in der Azure-Architektur zur Behandlung von vorübergehenden Fehlern](/azure/architecture/best-practices/transient-faults)

[Das Polly-Projekt](http://www.thepollyproject.org/) ist eine Bibliothek mit Funktionen zum Umgang mit vorübergehenden Fehlern mithilfe von Ausführungsrichtlinien.

### <a name="http-requests"></a>HTTP-Anforderungen

Wenn Sie HTTP-Anforderungen verwenden, können Sie nach der `Retry-After`-HTTP-Kopfzeile suchen, die in der Fehlerantwort enthalten ist. Diese enthält einen Wert in Sekunden, der angibt, wie lange Sie warten müssen, bis Sie eine Folgeanforderung erteilen. Weitere Informationen: [MDN-Webdokumente – Neuversuch danach](https://developer.mozilla.org/docs/Web/HTTP/Headers/Retry-After)

### <a name="sdk-assemblies"></a>SDK-Assemblys

Wenn Sie die SDK-Assemblys verwenden, können Sie nach der `Retry-After`-Verzögerung in der <xref:Microsoft.Xrm.Sdk.OrganizationServiceFault>.<xref:Microsoft.Xrm.Sdk.BaseServiceFault.ErrorDetails> Eigenschaft, mithilfe des Schlüssels `"Retry-After"`suchen. Der zurückgegebene Wert ist ein [TimeSpan](/dotnet/api/system.timespan)-Objekt.

### <a name="net-sdk-assembly-example"></a>.NET SDK-Assembly-Beispiel

Im folgenden Beispiel wird die [„Retry”-Klasse](#retry-class) verwendet, die unten beschrieben wird, um ein Konto mithilfe der Methode <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.RetrieveMultiple*>-abzurufen. Methode. Wenn die Anforderung fehlschlägt, weil eine API-Begrenzung überschritten wurde, wartet die Klasse `Retry` gemäß einer Verzögerung, die vom Server festgelegt ist und versucht es erneut.

```csharp
var qe = new QueryExpression("account") { TopCount = 1 };
EntityCollection result = Retry.Do(() => service.RetrieveMultiple(qe));
```

#### <a name="retry-class"></a>„Retry”-Klasse

Die `Retry`-Klasse zeigt, wie Anforderungen wiederholt werden, die mit vorübergehenden Fehlern basierend auf bekannten <xref:Microsoft.Xrm.Sdk.OrganizationServiceFault>-Fehlercodes fehlschlagen. Die `Retry`-Klasse wartet vor dem Neuversuch. Wenn vom Fehler eine Wiederholungsverzögerung angegeben wird, wartet sie gemäß der vom Server angegebenen Verzögerung. Anderenfalls wird ein exponentieller Backoff verwendet, um die Verzögerung auf Grundlage der Anzahl der vorgenommenen Wiederholungsversuche zu berechnen.

```csharp
using System;
using System.ServiceModel;
using System.Threading;

public class Retry
{
    private const int RateLimitExceededErrorCode = -2147015902;

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
        if (ex.Detail.ErrorCode == RateLimitExceededErrorCode)
        {
            return true;
        }

        return false;
    }
}

```



### <a name="see-also"></a>Siehe auch

[CDS für App-Webdienste verwenden](webapi/overview.md)<br />
[Verwenden des CDS für App-Organisations-Service](org-service/overview.md)<br />
[Ausführen von Batchbetrieben mithilfe der Web-API](webapi/execute-batch-operations-using-web-api.md)<br />
[Verwenden von "ExecuteMultiple" zur Verbesserung der Leistung bei Massendatenlast](org-service/execute-multiple-requests.md)
