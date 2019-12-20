---
title: Verwenden der Power Apps-Überprüfungs-Web-API | Microsoft-Dokumentation
description: Die Power Apps-Überprüfungs-Web-API bietet eine Entwicklungserfahrung, die für eine Vielzahl von Programmiersprachen, Plattformen und Geräte verwendet werden kann
ms.custom: ''
ms.date: 06/3/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
ms.assetid: 0d5f7579-304a-4d28-ba73-df30722205eb
caps.latest.revision: 1
author: mhuguet
ms.author: mhuguet
ms.reviewer: pehecke
manager: maustinjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: eed1556726cb947d7eba6b8f94ceed538f669ea3
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2019
ms.locfileid: "2861811"
---
# <a name="use-the-power-apps-checker-web-api"></a>Verwenden der Power Apps-Überprüfungs-Web-API

[!INCLUDE [cc-beta-prerelease-disclaimer](../../../../includes/cc-beta-prerelease-disclaimer.md)]

Die Power Apps-Überprüfungs-Web-API bietet einen Mechanismus für das Ausführen statischer Analyseprüfungen hinsichtlich Anpassungen und Erweiterungen für die Common Data Service-Plattform. Sie ist für Ersteller und Entwickler verfügbar, um umfangreiche Prüfungen der statischen Analyse auf Ihren Lösungen für einen Satz von Regeln der bewährten Methode ausführen, um problematische Muster schnell zu ermitteln. Der Service bietet die Logik für die [Lösungsprüferfunktion](../../../../maker/common-data-service/use-powerapps-checker.md) im Power Apps-Ersteller-[Portal](https://make.powerapps.com) und ist als Teil der Automatisierung für [Anwendungen enthalten, die über AppSource eingereicht werden](../../publish-app-appsource.md). Das direkte Interagieren mit dem Service auf diese Weise ermöglicht eine Analyse von Lösungen, die in den lokalen (alle unterstützten Versionen) und Online-Umgebungen enthalten sind.

 > [!IMPORTANT]
 >
 > - Die Web-API für die Power Apps-Überprüfung ist eine Vorschaufunktion.
 > - [!INCLUDE[cc_preview_features_definition](../../../../includes/cc-preview-features-definition.md)]

<a name="bkmk_altApproaches"></a>

## <a name="alternative-approaches"></a>Alternative Ansätze

Bevor Sie sich die Details dazu ansehen, wie Sie auf der untersten Ebene mit Web-APIs interagieren, sollten Sie sich überlegen, stattdessen unser PowerShell-Modul Microsoft.PowerApps.Checker.PowerShell zu nutzen. Dies ist ein vollständig unterstütztes Tool, das in der [PowerShell-Galerie](https://www.powershellgallery.com) verfügbar ist. Die aktuelle Einschränkung besteht darin, dass Windows PowerShell erforderlich ist. Wenn Sie diese Bedingung nicht erfüllen können, ist wahrscheinlich eine direkte Interaktion mit den APIs die beste Methode.

<a name="bkmk_getStarted"></a>

## <a name="getting-started"></a>Erste Schritte

Beachten Sie unbedingt, dass eine Lösungsanalyse zu einem langen Prozess führen kann. Es kann normalerweise sechzig Sekunden bis zu fünf Minuten dauern, abhängig von vielen Faktoren, wie der Zahl, Größe und Komplexität von Anpassungen und Code. Der Analysefluss ist asynchron und besteht aus mehreren Schritten, beginnend mit der Initiierung eines Analyseauftrags mit dem Status „API”, der verwendet wird, um den Auftragsabschluss abzufragen. Ein Beispielfluss für eine Analyse lautet wie folgt: 

1. OAuth-Token besorgen
2. Anrufupload (parallel für jede Datei)
3. Anrufanalyse (führt den Analyseauftrag ein)
4. Anrufstatus bis zum Abschluss (Schleife mit einer Pause zwischen Anrufen bis zum Ende signalisiert wird oder Schwellenwerte erfüllt werden)
5. Laden Sie die Ergebnisse der bereitgestellten SAS-URI herunter.

Einige Variationen sind:

- Schließen einer Suche des Regelsatzes oder der Regeln als Vorschritt ein. Allerdings kann es etwas schneller sein, eine Weiterleitung an eine konfigurierte oder hartcodierte Regelsatz-ID durchzuführen. Es wird empfohlen, einen Regelsatz zu verwenden, der Ihre Anforderungen erfüllt.
- Sie können entscheiden, den Uploadmechanismus nicht zu verwenden (siehe Upload für Beschränkungen).

Sie müssen die Folgenden bestimmen:

- [Welche Geografie?](#determine-a-geography)
- [Welche Version?](#versioning)
- [Welche Regelsätze und Regeln?](#rulesets-and-rules)
- [Was ist Ihre Mandanten-ID?](#find-your-tenant-id)

In den folgenden Themen finden Sie Dokumentationen zu den einzelnen APIs:

[Abrufen der Regelsatz-Liste](retrieve-rulesets.md)<br />
[Abrufen der Regel-Liste](retrieve-rules.md)<br />
[Hochladen einer Datei](upload-file.md)<br />
[Analyse aufrufen](analyze.md)<br />
[Überprüfen des Analysestatus](check-status.md)<br />

<a name="bkmk_geo"></a>

## <a name="determine-a-geography"></a>Geografie bestimmen

Beim Interagieren mit dem Power Apps-Überprüfungsservice werden Dateien zusammen mit den generierten Berichten vorübergehend in Azure gespeichert. Wenn Sie eine spezielle API für die Geografie verwenden, können Sie steuern, wo die Daten gespeichert werden. Es wird empfohlen, dieselbe Geografie für jeden API-Aufruf im Analyselebenszyklus zu verwenden. Jede Geografie kann aufgrund unseres mehrstufigen sicheren Bereitstellungsansatzes zu einem bestimmten Zeitpunkt eine andere Version haben. So können wir eine vollständige Versionskompatibilität sicherstellen. Außerdem kann dies die Ausführungszeit verringern, da die Daten in einigen Fällen einen kürzeren Weg haben. Im Folgenden finden Sie die verfügbaren Geografien:

|Azure-Rechenzentrum|Name|Geografie|Basis-URI|
|---|---|---|---|
|Öffentlich|Vorschau|Vereinigte Staaten|unitedstatesfirstrelease.api.advisor.powerapps.com|
|Öffentlich|Produktion|Vereinigte Staaten|unitedstates.api.advisor.powerapps.com|
|Öffentlich|Produktion|Europa|europe.api.advisor.powerapps.com|
|Öffentlich|Produktion|Asien|asia.api.advisor.powerapps.com|
|Öffentlich|Produktion|Australien|australia.api.advisor.powerapps.com|
|Öffentlich|Produktion|Japan|japan.api.advisor.powerapps.com|
|Öffentlich|Produktion|Indien|india.api.advisor.powerapps.com|
|Öffentlich|Produktion|Kanada|canada.api.advisor.powerapps.com|
|Öffentlich|Produktion|Südamerika|southamerica.api.advisor.powerapps.com|
|Öffentlich|Produktion|Vereinigtes Königreich|unitedkingdom.api.advisor.powerapps.com|

> [!NOTE]
>  Sie können auswählen, ob Sie die Vorschaugeographie verwenden möchten, um die neuesten Funktionen und Änderungen früher nutzen zu können. Beachten Sie jedoch, dass für die Vorschau nur Azure-Regionen in den USA verwendet werden.

<a name="bkmk_versioning"></a>

## <a name="versioning"></a>Versionsverwaltung

Dies ist zwar nicht erforderlich, es wird jedoch empfohlen, den API-Versionsabfragezeichenfolgen-Parameter mit der gewünschten API-Version zu verwenden. Die aktuelle API-Version ist 1.0. Beispielsweise finden Sie eine Regelsatz-HTTP-Abfrage, in der angegeben wird, dass die API-Version 1.0 verwendet werden soll:

`https://unitedstatesfirstrelease.api.advisor.powerapps.com/api/ruleset?api-version=1.0`

Wenn dies nicht angegeben wird, wird die aktuelle API-Version standardmäßig verwendet. Die Verwendung einer expliziten Versionsnummer wird empfohlen, da die Version entsprechend inkrementiert wird, wenn wichtige Änderungen eingeführt werden. Wenn die Versionsnummer in einer Abfrage angegeben wird, wird die Abwärtskompatibilitätsunterstützung in späteren (numerisch größeren) Versionen beibehalten.

<a name="bkmk_rules"></a>

## <a name="rulesets-and-rules"></a>Regelsätze und Regeln

Die Power Apps-Überprüfung erfordert bei der Ausführung eine Liste mit Regeln. Diese Regeln können im Formular der einzelnen Regeln oder einer Gruppierung von Regeln bereitgestellt werden, auch als *Regelsatz* bezeichnet. Ein Regelsatz ist eine bequeme Möglichkeit, eine Gruppe von Regeln anzugeben, statt jede Regeln einzeln anzugeben. Beispielsweise verwendet die Lösungsüberprüfungsfunktion einen Regelsatz namens *Lösungsprüfung*. Wenn neue Regeln hinzugefügt oder entfernt werden, berücksichtigt der Service diese Änderungen automatisch, ohne dass eine Änderung durch die nutzende Anwendung erforderlich wird. Wenn Sie angeben, dass die Liste mit Regeln nicht wie oben beschrieben automatisch geändert werden darf. Dann können die Regeln einzeln angegeben werden.
Regelsätze können eine oder mehrere Regeln haben, es gibt keine Beschränkung. Eine Regel kann in keinem Regelsatz oder in mehreren Regelsätzen enthalten sein. Sie können eine Liste aller Regelsätze abrufen, indem Sie die API wie folgt aufrufen: `[Geographical URL]/api/ruleset`. Dieser Endpunkt ist offen und erfordert keine Authentifizierung.

### <a name="solution-checker-ruleset"></a>Lösungsprüfer-Regelsatz

Der Lösungsprüfer-Regelsatz enthält eine Reihe von wirksamen Regeln, die Chancen für falsch positive Ergebnisse beinhalten. Wenn Sie eine vorhandene Lösung analysieren, wird empfohlen, mit diesem Regelsatz zu starten. Dieser Regelsatz wird von der [Lösungsprüferfunktion](../../../../maker/common-data-service/use-powerapps-checker.md) verwendet.

### <a name="appsource-certification-ruleset"></a>AppSource-Zertifizierungsregelsatz

Beim Veröffentlichen von Anwendungen bei AppSource müssen Sie Ihre Anwendungen zertifizieren lassen. [Bei AppSource veröffentlichte Anwendungen](../../publish-app-appsource.md) sind erforderlich, um einen qualitativ hochwertigen Standard zu erfüllen. Der AppSource-Zertifizierungsregelsatz enthält die Regeln, die Teil des Lösungsprüfer-Regelsatzes sind, sowie weitere Regeln, um sicherzustellen, dass nur qualitativ hochwertige Anwendungen im Store veröffentlicht werden. Einige der AppSource-Zertifizierungsregeln sind anfälliger für falsch positive Ergebnisse und erfordern unter Umständen zusätzliche Aufmerksamkeit, um die Fehler zu beheben.

<a name="bkmk_tenant"></a>

## <a name="find-your-tenant-id"></a>Suchen der Mandanten-ID

Die ID Ihres Mandanten ist erforderlich, um mit den APIs zu interagieren, die ein Token erfordern. [In diesem Artikel](https://docs.microsoft.com/onedrive/find-your-office-365-tenant-id) erhalten Sie Informationen dazu, wie Sie die Mandanten-ID erhalten können. Sie können auch PowerShell-Befehle verwenden, um die Mandanten-ID abzurufen. Im folgenden Beispiel werden die Cmdlets im [AzureAD-Modul](https://docs.microsoft.com/powershell/module/azuread/?view=azureadps-2.0) verwendet.

```powershell
# Login to AAD as your user
Connect-AzureAD

# Establish your tenant ID
$tenantId = (Get-AzureADTenantDetail).ObjectId
```

Die Mandanten-ID ist der Wert der `ObjectId`-Eigenschaft, der von `Get-AzureADTenantDetail` zurückgegeben wird. Sie sehen sie möglicherweise nach dem Anmelden, wenn Sie das Connect-AzureAD-Cmdlet in der Cmdlet-Ausgabe verwenden. In diesem Fall wird sie `TenantId` genannt.

<a name="bkmk_auth"></a>

## <a name="authentication-and-authorization"></a>Authentifizierung und Autorisierung

 Die Abfrage von Regeln und Regelsätzen erfordert kein OAuth-Token, aber bei allen anderen APIs wird das Token benötigt. Die APIs unterstützen die Autorisierungsermittlung, indem alle der APIs aufgerufen werden, die ein Token erfordern. Die Antwort ist ein nicht autorisierter HTTP-Statuscode von 401 mit einer WWW-Authentifizierungskopfzeile, der Autorisierungs-URI und der Ressourcen-ID. Sie sollten auch Ihre Mandanten-ID in der `x-ms-tenant-id`-Kopfzeile angeben. Unter [Power Apps-Prüfungsauthentifizierung und -autorisierung](/powershell/powerapps/overview#powerapps-checker-authentication-and-authorization) erhalten Sie weitere Informationen. Unten finden Sie ein Beispiel für eine Antwortkopfzeile, die von einer API-Abfrage zurückgegeben wird:

```http
WWW-Authenticate →Bearer authorization_uri="https://login.microsoftonline.com/0082fff7-33c5-44c9-920c-c2009943fd1e", resource_id="https://api.advisor.powerapps.com/"
```

Sobald Sie diese Informationen haben, können Sie die Azure Active Directory-Authentifizierungsbibliothek (ADAL) oder einige andere Mechanismen verwenden, um das Token abzurufen. Unten finden Sie ein Beispiel, wie Sie dies mithilfe von C# und der [ADAL-Bibliothek, Version 4.5.1](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/4.5.1) erledigen können:

```c#
// Call the status URI as it is the most appropriate to use with a GET.
// The GUID here is just random, but needs to be there.
Uri queryUri = new Uri($"{targetServiceUrl}/api/status/4799049A-E623-4B2A-818A-3A674E106DE5");
AuthenticationParameters authParams = null;

using (var client = new HttpClient())
{
    var request = new HttpRequestMessage(HttpMethod.Get, queryUri);
    request.Headers.Add("x-ms-tenant-id", tenantId.ToString());

    // NOTE - It is highly recommended to use async/await
    using (var response = client.SendAsync(request).GetAwaiter().GetResult())
    {
        if (response.StatusCode == System.Net.HttpStatusCode.Unauthorized)
        {
            // NOTE - It is highly recommended to use async/await
            authParams = AuthenticationParameters.CreateFromUnauthorizedResponseAsync(response).GetAwaiter().GetResult();
        }
        else
        {
            throw new Exception($"Unable to connect to the service for authorization information. {response.ReasonPhrase}");
        }
    }
}
```

Sobald Sie das Token abgerufen haben, wird es empfohlen, dass Sie dasselbe Token für nachfolgende Aufrufe im Abfragelebenszyklus angeben. Bei zusätzlichen Abfragen ist wahrscheinlich der Abruf eines neuen Tokens aus Sicherheitsgründen gerechtfertigt.

<a name="bkmk_transport"></a>

## <a name="transport-security"></a>Transportsicherheit
Um die beste Verschlüsselung sicherzustellen, unterstützt der Prüfservice nur die Kommunikation mithilfe der Transport Layer Security (TLS) 1.2 und höher. Bewährte Verfahren zu .NET und TLS finden Sie unter [Bewährte Verfahren zu Transport Layer Security (TLS) mit dem .NET-Framework](https://docs.microsoft.com/dotnet/framework/network-programming/tls).

<a name="bkmk_report"></a>

## <a name="report-format"></a>Berichtsformat

Das Ergebnis der Lösungsanalyse ist eine ZIP-Datei, die einen oder mehrere Berichte in einem standardisierten JSON-Format enthält. Das Berichtsformat basiert auf statischen Analyseergebnissen, die im Static Analysis Results Interchange Format (SARIF) vorliegen. Es gibt Tools, mit denen SARIF-Dokumente abgerufen werden können und damit interagiert werden kann. Auf dieser [Website](https://sarifweb.azurewebsites.net/) finden Sie weitere Details. Der Service nutzt Versionen zwei des [OASIS-Standards](https://docs.oasis-open.org/sarif/sarif/v2.0/sarif-v2.0.html).


### <a name="see-also"></a>Siehe auch

[Abrufen der Regelsatz-Liste](retrieve-rulesets.md)<br />
[Abrufen der Regel-Liste](retrieve-rules.md)<br />
[Hochladen einer Datei](upload-file.md)<br />
[Analyse aufrufen](analyze.md)<br />
[Überprüfen des Analysestatus](check-status.md)<br />