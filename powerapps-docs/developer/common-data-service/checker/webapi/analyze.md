---
title: Analyse aufrufen | Microsoft Docs
description: 'Erfahren Sie, wie Sie eine POST-Anforderung mithilfe der PowerApps-Überprüfungs-Web-API erstellen können, um den Analyseanforderungsauftrag zu initiieren.'
ms.custom: ''
ms.date: 06/04/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: a2c771f4-7eb6-4445-af2d-f775619ac3e8
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
---

# <a name="invoke-analysis"></a>Analyse aufrufen

[!INCLUDE [cc-beta-prerelease-disclaimer](../../../../includes/cc-beta-prerelease-disclaimer.md)]

Die Initiierung eines Analyseauftrags erfolgt, indem eine `POST`-Anforderung zur `analyze`-Route gesendet wird. Die Analyse kann ein langer laufender Prozess sein, der meist länger dauert als eine Minute. Die API nimmt zunächst einige grundlegende Überprüfungen vor, initiiert die Anforderung im Backend durch Senden eines Auftrags und antwortet dann mit einem 202-Statuscode und einem `Location`-Kopf oder mit den entsprechenden Fehlerdetails. Der `Location`-Kopfzeilenwert ist eine URL, die verwendet werden kann, um den Status der Anforderung zu überprüfen und die URLs der Ergebnisse zu erhalten. Es stehen verschiedenste Optionen über die `POST`-Aktion zur Verfügung, um den Auftrag entsprechend Ihren Kriterien anzupassen, wie die Liste von Regeln oder Regelsätzen, aus der Analyse auszuschließende Dateien und mehr. Sie können die Analyse mithilfe der folgenden `[Geographical URL]/api/analyze?api-version=1.0` initiieren.


> [!NOTE]
>  Es wird empfohlen, 15 bis 60 Sekunden zwischen den Statusprüfungen zu warten. Die Analyse wird in der Regel in nur 1 bis 5 Minuten ausgeführt.<br /> Die API erfordert ein OAuth-Token.

<a name="bkmk_headers"></a>

## <a name="headers"></a>Kopfzeilen

|Name|Typ|Erwarteter Wert|Erforderlich?|
|---|---|---|---|
|Autorisierung|Zeichenfolge|Das OAuth 1-Bearertoken mit Azure Active Directory (AAD)-Anwendungs-ID-Anspruch.|Ja|
|x-ms-tenant-id|GUID|Die ID des Mandanten für die Anwendung.|Ja|
|x-ms-correlation-id|GUID|Der Bezeichner für die Analyseausführung. Sie sollten dieselbe ID für die gesamte Ausführung angeben (Upload, Analyse, Status).|Ja|
|Akzeptieren|Objekt|`application/json, application/x-ms-sarif-v2`|Ja|
|Sprache-akzeptieren|Zeichenfolge|Sprachcode(s) (z. B. en-US). Der Standard ist en-US. Falls mehrere Sprachen angegeben sind, ist die erste die primäre Sprache. Allerdings sind alle Übersetzungen (sofern die Sprache unterstützt wird) enthalten.|Nein

<a name="bkmk_body"></a>

## <a name="body"></a>Textkörper

### <a name="commonly-used-options"></a>Allgemein verwendete Optionen:

|Eigenschaft|Typ|Erwarteter Wert|Erforderlich?|
|---|---|---|---|
|sasUriList|Zeichenfolgenarray|Eine Liste der URIs, die den Servicezugang bietet, um eine zentrale Lösung, eine ZIP-Datei mit mehreren Lösungsdateien oder ein Paket herunterzuladen.|Ja|
|ruleSets|Array von benutzerdefinierten|0 oder mehr|Nein|
|ruleSets.id|guid|Die ID des Regelsatzes, der gesucht werden kann, indem die Regelsatz-API abgefragt wird.|Nein, dies ist jedoch das, was Sie meist verwenden würden. Sie müssen entweder dies oder ruleCodes verwenden.|
|ruleCodes.code|Zeichenfolge|Die ID der gewünschten Regel, die gesucht werden kann, indem die Regelsatz- und Regel-APIs abgefragt werden.|Nein, Sie müssen entweder dies oder ruleSets verwenden.|
|fileExclusions|Zeichenfolgenarray|Eine Liste der auszuschließenden Dateinamen oder Dateinamenmuster. Unterstützung gibt es für die Verwendung von „*“ als Platzhalter am Anfang und/oder Ende eines Dateinamens (z. B. \*jquery.dll und \*jquery\*).|Nein|

<a name="bkmk_responses"></a>

## <a name="expected-responses"></a>Erwartete Antworten

|HTTP-Statuscode|Szenario|Ergebnis|
|---|---|---|
|202|Die Analyseanforderung wurde akzeptiert und der Statusprüfungs-URI wurde in der `Location`-Kopfzeile zurückgegeben|Kein Ergebnistext
|400|Eine Nicht-ZIP-Datei wurde gesendet, falsche Parameter, oder eine Datei wurde mit einem Virus eingeschlossen|Kein Ergebnistext|
|409|Eine Anfrage mit einem doppelten `x-ms-correlation-id`-Kopfzeilenwert wurde gesendet|Kein Ergebnistext|

### <a name="expected-response-headers"></a>Erwartete Antwortkopfzeilen

|Name|Typ|Erwarteter Wert|Erforderlich?|
|---|---|---|---|
|Location|Uri|URL zum Verwenden in Abfragen für den aktuellen Status und zum Abrufen der Ergebnisse|Ja|

<a name="bkmk_analyzeExample"></a>

## <a name="example-initiate-an-analysis"></a>Beispiel: eine Analyse initiieren

Dies ist ein Beispiel des Initiierens eines Analyseauftrags mit dem _AppSource Certification_-Regelsatz, einer einzelnen Datei und des Ausschließens von Dateien, die den Text _jquery_ und _json_ im Namen enthalten.

**Anforderung**

```http
POST [Geographical URI]/api/analyze?api-version=1.0
Accept: application/json
Content-Type: application/json; charset=utf-8
x-ms-correlation-id: 9E378E56-6F35-41E9-BF8B-C0CC88E2B832
x-ms-tenant-id: F2E60E49-CB87-4C24-8D4F-908813B22506

{
    "ruleSets": [{
        "id": "0ad12346-e108-40b8-a956-9a8f95ea18c9"
    }],
    "sasUriList": ["https://testenvfakelocation.blob.core.windows.net/mySolution.zip"],
    "fileExclusions": ["*jquery*", "*json*"]
}
```

**Antwort**

```http
HTTP/1.1 202 Accepted
Content-Type: application/json; charset=utf-8
Location: [Geographical URI]/api/status/9E378E56-6F35-41E9-BF8B-C0CC88E2B832&api-version=1.0
```

### <a name="see-also"></a>Siehe auch

[Verwenden der PowerApps-Überprüfungs-Web-API](overview.md)<br />
[Abrufen der Regelsatz-Liste](retrieve-rulesets.md)<br />
[Abrufen der Regel-Liste](retrieve-rules.md)<br />
[Hochladen einer Datei](upload-file.md)<br />
[Überprüfen des Analysestatus](check-status.md)<br />
