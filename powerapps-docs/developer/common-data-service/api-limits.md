---
title: API-Limits (Common Data Service) | Microsoft-Dokumentation
description: Verstehen Sie die Begrenzungen für API-Anforderungen.
ms.custom: ''
ms.date: 03/21/2019
ms.reviewer: kvivek
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: bsimons
manager: annbe
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: d6b332b1e71a8d440c02cc79f7566eec59533cce
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "2753082"
---
# <a name="api-limits"></a>API-Begrenzungen

Wir begrenzen die Anzahl der API-Anforderungen, die von jedem Benutzer erteilt werden können, pro Organisationsinstanz in einem fünfminütigen gleitenden Fenster. Außerdem beschränken wir die Anzahl der gleichzeitigen Anforderungen, die auf einmal eingehen können.  Wenn einer dieser Grenzwerte überschritten wird, gibt die Plattform eine Ausnahme zurück.

Die Beschränkung stellt sicher, dass Benutzer, die Anwendungen ausführen, sich nicht aufgrund vorhandener Ressourceneinschränkungen gegenseitig stören. Die Grenzwerte haben keine Auswirkungen auf normale Plattformbenutzer. Nur Anwendungen, die eine sehr große Anzahl an API-Anforderungen ausführen, sind möglicherweise betroffen. Er bietet einen gewissen Schutz vor dem unwillkürlichen und unerwarteten Anstieg des Anforderungsvolumens, das die Verfügbarkeit und Leistungsfähigkeit der Common Data Service-Plattform gefährdet.

Da Plug-Ins und benutzerdefinierte Workflow-Aktivitäten auf dem Server unabhängig eines angemeldeten Benutzers ausgeführt werden, zählen Aufrufe vom Plugin-Code nicht zu diesem externen API-Aufruflimit.

Falls bei Ihrer Anwendung die Möglichkeit besteht, diese Begrenzung zu überschreiten, beachten Sie bitte die Leitlinien, die Sie im Abschnitt [Was ist zu tun, wenn meine Anwendung die Begrenzung überschreitet?](#what-should-i-do-if-my-application-exceeds-the-limit) unten finden.

## <a name="what-happens-when-the-limit-is-exceeded"></a>Was geschieht, wenn die Begrenzung überschritten wird?

Wenn die Begrenzung überschritten wird, wird für alle Anforderungen desselben Benutzers eine Fehlerantwort zurückgegeben.

Wenn Sie die .NET-SDK-Assemblys verwenden, reagiert die Plattform mit einem `FaultException<OrganizationServiceFault>` WCF-Fehler.  

| Fehlercode | Meldung |
|------------|-------------------------------------|
|`-2147015902`|`Number of requests exceeded the limit of 4000, measured over time window of 300 seconds.`|
|`-2147015903`|`Combined execution time of incoming requests exceeded limit of 1,200,000 milliseconds over time window of 300 seconds. Decrease number of concurrent requests or reduce the duration of requests and try again later.`|
|`-2147015898`|`Number of concurrent requests exceeded the limit of X`|

Wenn Sie HTTP-Anforderungen verwenden, beinhaltet die Antwort dieselbe Nachricht aber mit:<br />
`StatusCode` : `429`

Von allen Anforderungen werden diese Fehlerantworten zurückgegeben, bis das Volumen der API-Anforderungen unter die Begrenzung fällt. Wenn Sie diese Antworten erhalten, sollten von Ihrer Anwendung keine weiteren API-Anforderungen mehr gesendet werden, bis das Volumen der Anforderungen unterhalb der Begrenzung liegt.

## <a name="what-should-i-do-if-my-application-exceeds-the-limit"></a>Was muss ich tun, wenn meine Anwendung die Begrenzung überschreitet?

Wenn von Ihrer Anwendung die Begrenzung überschritten wird, gibt die Fehlerantwort vom Server möglicherweise an, wie lange Sie warten sollten, bis Sie weitere Anforderungen übermitteln. Das Antwortobjekt ist etwas anders, wenn Sie SDK-Assemblys oder HTTP-Anforderungen verwenden.

Eine Diskussion zu bewährten Methoden finden Sie unter [Bewährte Methoden in der Azure-Architektur zur Behandlung von vorübergehenden Fehlern](/azure/architecture/best-practices/transient-faults)

[Das Polly-Projekt](https://www.thepollyproject.org/) ist eine Bibliothek mit Funktionen zum Umgang mit vorübergehenden Fehlern mithilfe von Ausführungsrichtlinien.

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

[Verwendung der Common Data Service Web-API](webapi/overview.md)<br />
[ Common Data Service Organisationsdienst nutzen](org-service/overview.md)<br />
[Ausführen von Batchbetrieben mithilfe der Web-API](webapi/execute-batch-operations-using-web-api.md)<br />
[Verwenden von "ExecuteMultiple" zur Verbesserung der Leistung bei Massendatenlast](org-service/execute-multiple-requests.md)
