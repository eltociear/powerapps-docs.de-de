---
title: Überprüfen des Analysestatus | Microsoft Docs
description: Erfahren Sie, wie Sie eine GET-Anforderung mithilfe der PowerApps Überprüfungs-Web-API erstellen können, um den Status eines Analyseanforderungsauftrags zu überprüfen.
ms.custom: ''
ms.date: 06/04/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
ms.assetid: 6e2abe2d-2205-4d15-9e0f-5975ccc0484e
caps.latest.revision: 21
author: mhuguet
ms.author: mhuguet
ms.reviewer: pehecke
manager: maustinjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 97b244b59bccbde9c8e20a86723133af07d4eb2b
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748434"
---
# <a name="check-for-analysis-status"></a>Überprüfen des Analysestatus

[!INCLUDE [cc-beta-prerelease-disclaimer](../../../../includes/cc-beta-prerelease-disclaimer.md)]

Eine URL wird als Bestandteil der `Location`-Kopfzeile als Antwort auf eine Anfrage an die `analyze`-API zurückgegeben. Sie muss verwendet werden, um über HTTP `GET` den Analyseauftragsstatus abzufragen. Wenn der Analyseauftrag beendet ist, enthält der Antworttext die URL oder die Liste der URLs, in die die Ergebnisausgabe heruntergeladen werden kann. Rufen Sie diesen URI ab, bis der HTTP-Statuscode „200“ zurückgegeben wird. Während der Auftrag noch ausgeführt wird, wird ein HTTP-Statuscode „202“ mit der `Location`-Kopfzeile zurückgegeben, mit dem gleichen URI, der von `analyze` zurückgegeben werden wurde. Nachdem eine 200-Antwort zurückgegeben wurde, enthält die `resultFileUris`-Eigenschaft die einzelnen (oder die Liste aus) herunterladbaren Speicherorte der Ausgabe in einer ZIP-Datei. Eine formatierte [Static Analysis Results Interchange Format (SARIF)](https://sarifweb.azurewebsites.net) V2-Datei ist in diesem ZIP-Download enthalten, d. h. eine formatierte `JSON`-Datei, die die Ergebnisse der Analyse umfasst. Der Antworttext enthält ein `IssueSummary`-Objekt, das eine Zusammenfassung der Anzahl der gefundenen Probleme enthält.

> [!NOTE]
>  Es wird empfohlen, 15 bis 60 Sekunden zwischen den Statusprüfungen zu warten. Die Analyse wird in der Regel in nur 1 bis 5 Minuten ausgeführt.<br />
>  Diese API erfordert ein OAuth-Token, das ein Token für dieselbe Client-Anwendung sein muss, die den Analyseauftrag initiiert hat.

<a name="bkmk_headers"></a>

## <a name="headers"></a>Kopfzeilen

|Name|Typ|Erwarteter Wert|Erforderlich?|
|---|---|---|---|
|Autorisierung|Zeichenfolge|Das OAuth 1-Bearertoken mit AAD-Anwendungs-ID-Anspruch.|Ja|
|x-ms-tenant-id|GUID|Die ID des Mandanten für die Anwendung.|Ja|
|x-ms-correlation-id|GUID|Der Bezeichner für die Analyseausführung. Sie sollten dieselbe ID für die gesamte Ausführung angeben (Upload, Analyse, Status)|Ja|

<a name="bkmk_responses"></a>

## <a name="expected-responses"></a>Erwartete Antworten

|HTTP-Statuscode|Szenario|Ergebnis|
|---|---|---|
|200|Mindestens ein Ergebnis wurde gefunden.|Siehe das Beispiel unten. Ein Ergebnis wird zurückgegeben.|
|202|Wird noch verarbeitet|Siehe das Beispiel unten. Ein Ergebnis wird zurückgegeben.|
|403|Verboten|Der Anforderer ist nicht der Gleiche wie der Ersteller der Anforderung für die Analyse.|
|404|Nicht gefunden|Die Analyseanforderung konnte mit dem in der URL bereitgestellten Verweis nicht gefunden werden.|

### <a name="expected-response-headers"></a>Erwartete Antwortkopfzeilen

|Name|Typ|Erwarteter Wert|Erforderlich?|
|---|---|---|---|
|Location|URI|URI zum Verwenden in Abfragen für den aktuellen Status und zum Abrufen der Ergebnisse|Ja|

### <a name="expected-response-body"></a>Erwarteter Antworttext

In der folgenden Tabelle wird die Struktur der Antwort für jede Anfrage (nur HTTP-200- oder -202-Antwort) dargestellt.

|Eigenschaft|Typ|Erwarteter Wert|Erforderlich?|
|---|---|---|---|
|privacyPolicy|Zeichenfolge|Der URI der Datenschutzrichtlinien.|Ja|
|Fortschritt|int|Ein Wert von 0-100 (Fertigstellungsprozentsatz), wobei 10 bedeutet, dass die Verarbeitung etwa zu 10 % vollständig ist.|Ja|
|runCorrelationId|GUID|Der Anforderungsbezeichner, der in jeder Anforderung enthalten ist. Dieser kann bei Bedarf zur Korrelation zur Anforderung verwendet werden.|Ja|
|Status|Zeichenfolge|`InProgress` wird zurückgegeben, wenn der Auftrag immer noch verarbeitet wird. `Failed` wird zurückgegeben, wenn ein katastrophales Problem beim Verarbeiten des Auftrags auf dem Server aufgetreten ist. Es sollte weitere Details in der Fehlereigenschaft geben. `Finished` wird zurückgegeben, wenn der Auftrag erfolgreich ohne Probleme abgeschlossen wurde. `FinishedWithErrors` wird zurückgegeben, wenn der Auftrag erfolgreich abgeschlossen wurde, jedoch mindestens eine Regel nicht fehlerfrei abgeschlossen wurde. Dies ist lediglich ein Hinweis für Sie, damit Sie wissen, dass der Bericht unter Umständen nicht vollständig ist. Microsoft ist sich dieser Probleme im Backend bewusst und arbeitet daran, die einzelnen Punkte zu diagnostizieren und anzugehen.|Ja|
|resultFileUris|Zeichenfolgenarray|Eine Liste der URIs, die direkten Download der Ausgabe gewähren. Es sollte eine pro Datei geben, die in der ursprünglichen API-Analyse-Aufruf enthalten war.|Nr. Dies ist nur enthalten, wenn das Verarbeiten abgeschlossen wurde.|
|issueSummary|IssueSummary|Eigenschaften unten aufgeführt|Nr. Dies ist nur enthalten, wenn das Verarbeiten abgeschlossen wurde.|
|issueSummary.criticalIssueCount|int|Anzahl der identifizierten Probleme, die einen kritischen Schweregrad im Ergebnis haben|Ja|
|issueSummary.highIssueCount|int|Anzahl der identifizierten Probleme, die einen hohen Schweregrad im Ergebnis haben|Ja|
|issueSummary.mediumIssueCount|int|Anzahl der identifizierten Probleme, die einen mittleren Schweregrad im Ergebnis haben|Ja|
|issueSummary.lowIssueCount|int|Anzahl der identifizierten Probleme, die einen niedrigen Schweregrad im Ergebnis haben|Ja|
|issueSummary.informationalIssueCount|int|Anzahl der identifizierten Probleme, die einen informativen Schweregrad im Ergebnis haben|Ja|

<a name="bkmk_checkStatusDone"></a>

## <a name="example-status-check-when-done"></a>Beispiel: Statusprüfung, wenn fertig

Dieses Beispiel gibt einen Statusprüfungsaufruf mit dem Ergebnis aus, dass es ein Abschluss ist.

**Anforderung**

```http
GET [Geographical URI]/api/status/9E378E56-6F35-41E9-BF8B-C0CC88E2B832&api-version=1.0
Accept: application/json
Content-Type: application/json; charset=utf-8
x-ms-correlation-id: 9E378E56-6F35-41E9-BF8B-C0CC88E2B832
x-ms-tenant-id: F2E60E49-CB87-4C24-8D4F-908813B22506
```

**Antwort**

```http
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8

{
    "privacyPolicy":"https://go.microsoft.com/fwlink/?LinkID=310140",
    "progress":100,
    "resultFileUris":["https://fakeblob.blob.core.windows.net/report-files/mySolution.zip?sv=2017-11-09&sr=b&sig=xyz&se=2019-06-11T20%3A27%3A59Z&sp=rd"],"runCorrelationId":"9E378E56-6F35-41E9-BF8B-C0CC88E2B832","status":"Finished","issueSummary":
    {
        "informationalIssueCount":0,
        "lowIssueCount":0,
        "mediumIssueCount":302,
        "highIssueCount":30,
        "criticalIssueCount":0
    }
}
```


### <a name="see-also"></a>Siehe auch

[Verwenden der PowerApps-Überprüfungs-Web-API](overview.md)<br />
[Abrufen der Regelsatz-Liste](retrieve-rulesets.md)<br />
[Abrufen der Regel-Liste](retrieve-rules.md)<br />
[Hochladen einer Datei](upload-file.md)<br />
[Analyse aufrufen](analyze.md)<br />
