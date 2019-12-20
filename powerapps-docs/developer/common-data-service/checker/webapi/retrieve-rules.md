---
title: Abrufen der Regelliste | Microsoft Docs
description: Sehen Sie sich an, wie Sie eine GET-Anfrage mithilfe der Power Apps-Überprüfungs-Web-API stellen, um die Liste der verfügbaren Regeln abzurufen.
ms.custom: ''
ms.date: 06/04/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
ms.assetid: a8dc3019-c49e-48e4-a646-8a3a3fecd3a6
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
ms.openlocfilehash: 54db18819f22b01195fa1462395fc2be17f5ec74
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2019
ms.locfileid: "2861823"
---
# <a name="retrieve-the-list-of-rules"></a>Abrufen der Regelliste

[!INCLUDE [cc-beta-prerelease-disclaimer](../../../../includes/cc-beta-prerelease-disclaimer.md)]

Regeln werden zusammen mit einem Regelsatz gruppiert. Eine Regel kann in keinem Regelsatz oder in mehreren Regelsätzen enthalten sein. Verwenden Sie eine `GET`-Abfrage, um eine Liste aller verfügbaren Regeln, Regeln in einem Regelsatz oder in Regelsätzen zu ermitteln, indem Sie die API `[Geographical URI]/api/rule` aufrufen. Es gibt einige Variationen zum Anrufen dieser API, jedoch wird am häufigsten die Regelliste für einen bestimmten Regelsatz abgerufen.

> [!NOTE]
>  Die API erfordert kein OAuth-Token, kann jedoch eines akzeptieren, wenn es angegeben wird.

<a name="bkmk_headers"></a>

## <a name="headers"></a>Kopfzeilen

|Name|Typ|Erwarteter Wert|Erforderlich?|
|---|---|---|---|
|Sprache-akzeptieren|Zeichenfolge|Der Sprachcode (z. B. en-US). Der Standard ist en-US.|Nein

<a name="bkmk_params"></a>

## <a name="parameters"></a>Parameter

|Name|Typ|Erwarteter Wert|Erforderlich?|
|---|---|---|---|
|Regelsatz|Zeichenfolge|Der Name, die ID des Regelsatzes oder eine Liste von Regelsatz-IDs oder Namen, die durch ein Komma oder ein Semikolon getrennt sind (z. B. „Lösungsprüfer”).|Nein|
|includeMessageFormats|bool|Wenn dies auf `true` eingestellt ist, wird die Liste mit möglichen Message-Variationen in die Ergebnisse der Sprachanfragen aufgenommen, sofern verfügbar. Dies ist für Übersetzungen in mehrere Sprachen hilfreich. Wenn dies nicht erforderlich ist, geben Sie diesen Parameter nicht an oder geben Sie `false` als Wert fest, da dieser Parameter die Größe der Antwort erhöhen wird und die Verarbeitungszeit erhöhen kann.|Nein|

<a name="bkmk_responses"></a>

## <a name="expected-responses"></a>Erwartete Antworten

|HTTP-Statuscode|Szenario|Ergebnis|
|---|---|---|
|200|Mindestens ein Ergebnis wurde gefunden.|Siehe das Beispiel unten. Mindestens ein Ergebnis kann zurückgegeben werden.|
|204|Es wurden keine Ergebnisse gefunden.|Keine Ergebnisse in Antworttext.|

### <a name="expected-response-body"></a>Erwarteter Antworttext

In der folgenden Tabelle wird die Struktur der Antwort für jede Anfrage (nur HTTP-200-Antwort) dargestellt.

|Eigenschaft|Typ|Erwarteter Wert|Erforderlich?|
|---|---|---|---|
|Code|Zeichenfolge|Der Bezeichner der Regel, manchmal als Regel-ID bezeichnet.|Ja|
|Zusammenfassung|Zeichenfolge|Eine Zusammenfassung der Regel.|Ja|
|description|Zeichenfolge|Eine ausführlichere Beschreibung der Regel.|Ja|
|guidanceUrl|URI|Die URL, unter der die veröffentlichten Anweisungen zu finden sind. Es gibt unter Umständen Fälle, in denen es keinen speziellen unterstützenden Anweisungsartikel gibt.|Ja|
|einschließlich|Boolescher Wert|Signalisiert dem Service, dass die Regel in der Analyse berücksichtigt werden soll. Dies wird `true` für diese API sein.|Nein|
|messageTemplates|Array|Dieser Eigenschaftswert wird nur berücksichtigt, wenn `includeMessageFormats` `true` lautet.|Nein|
|messageTemplates.ruleId|Zeichenfolge| Gibt denselben ID-Wert wie die `code`-Eigenschaft zurück.|Ja|
|messageTemplates.messageTemplateId|Zeichenfolge| Ein Bezeichner, der im Static Analysis Results Interchange Format (SARIF)-Bericht verwendet wird, um eine Problem-Message-Variation für die Regel zu signalisieren.|Ja|
|messageTemplates.messageTemplate|Zeichenfolge|Der Text der Message-Variation für das Problemszenario, für das die Regel Berichte erstellt. Dies ist eine Formatzeichenfolge, die unter Umständen Tokens enthält, in denen Argumente, die im SARIF-Bericht enthalten sind und verwendet werden können, um eine ausführliche Message zu erstellen.|Ja|

<a name="bkmk_retrieveForRuleset"></a>

## <a name="example-retrieve-rules-for-a-ruleset-in-another-language"></a>Beispiel: Regeln für einen Regelsatz in einer anderen Sprache abrufen

In diesem Beispiel werden Daten für alle Regeln im *Lösungsprüfungs*-Regelsatz in der französischen Sprache zurückgegeben. Falls die gewünschte Sprache Englisch ist, entfernen Sie einfach die Kopfzeile „Sprache-akzeptieren”.

**Anforderung**

```http
GET [Geographical URI]/api/rule?ruleset=083A2EF5-7E0E-4754-9D88-9455142DC08B&api-version=1.0
x-ms-correlation-id: 9E378E56-6F35-41E9-BF8B-C0CC88E2B832
Accept: application/json
Content-Type: application/json; charset=utf-8
Accept-Language: fr
```

**Antwort**

```http
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8

[
    {
        "description": "Ne pas implémenter d’activités de workflow Microsoft Dynamics CRM 4.0",
        "guidanceUrl": "https://go.microsoft.com/fwlink/?LinkID=398563&error=il-avoid-crm4-wf&client=PAChecker",
        "include": true,
        "code": "il-avoid-crm4-wf",
        "summary": "Ne pas implémenter d’activités de workflow Microsoft Dynamics CRM 4.0",
        "howToFix": {
            "summary": ""
        }
    },
    {
        "description": "Utiliser InvalidPluginExecutionException dans des plug-ins et activités de workflow",
        "guidanceUrl": "https://go.microsoft.com/fwlink/?LinkID=398563&error=il-use-standard-exception&client=PAChecker",
        "include": true,
        "code": "il-use-standard-exception",
        "summary": "Utiliser InvalidPluginExecutionException dans des plug-ins et activités de workflow",
        "howToFix": {
            "summary": ""
        }
    },
...
]
```

<a name="bkmk_retrieveAll"></a>

## <a name="example-retrieve-all"></a>Beispiel: alle abrufen

In diesem Beispiel werden Daten für alle verfügbaren Regeln zurückgegeben.

**Anforderung**

```http
GET [Geographical URI]/api/rule?api-version=1.0
Accept: application/json
Content-Type: application/json; charset=utf-8
```

**Antwort**

```http
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8

[
    {
        "description": "Retrieve specific columns for an entity via query APIs",
        "guidanceUrl": "https://go.microsoft.com/fwlink/?LinkID=398563&error=il-specify-column&client=PAChecker",
        "include": true,
        "code": "il-specify-column",
        "summary": "Retrieve specific columns for an entity via query APIs",
        "howToFix": {
            "summary": ""
        }
    },
    {
        "description": "Do not duplicate plug-in step registration",
        "guidanceUrl": "https://go.microsoft.com/fwlink/?LinkID=398563&error=meta-remove-dup-reg&client=PAChecker",
        "include": true,
        "code": "meta-remove-dup-reg",
        "summary": "Do not duplicate plug-in step registration",
        "howToFix": {
            "summary": ""
        }
    },
...
]
```

<a name="bkmk_retrieveForRuleset"></a>

## <a name="example-retrieve-for-a-ruleset-with-message-formats"></a>Beispiel: für einen Regelsatz mit Message-Formaten abrufen

In diesem Beispiel werden Daten für alle Regeln im *Lösungsprüfungs*-Regelsatz in der französischen Sprache zurückgegeben. Falls die gewünschte Sprache Englisch ist, entfernen Sie einfach die Kopfzeile „Sprache-akzeptieren”.

**Anforderung**

```http
GET [Geographical URI]/api/rule?ruleset=083A2EF5-7E0E-4754-9D88-9455142DC08B&includeMessageFormats=true&api-version=1.0
Accept: application/json
Content-Type: application/json; charset=utf-8
```

**Antwort**

```http
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8

[
    {
        "description": "Do not implement Microsoft Dynamics CRM 4.0 workflow activities",
        "guidanceUrl": "https://go.microsoft.com/fwlink/?LinkID=398563&error=il-avoid-crm4-wf&client=PAChecker",
        "include": true,
        "code": "il-avoid-crm4-wf",
        "summary": "Do not implement Microsoft Dynamics CRM 4.0 workflow activities",
        "howToFix": {
            "summary": ""
        },
        "messageTemplates": [
            {
                "ruleId": "il-avoid-crm4-wf",
                "messageTemplateId": "message1",
                "messageTemplate": "Update the {0} class to derive from System.Workflow.Activities.CodeActivity, refactor Execute method implementation, and remove Microsoft.Crm.Workflow.CrmWorkflowActivityAttribute from type"
            },
            {
                "ruleId": "il-avoid-crm4-wf",
                "messageTemplateId": "message2",
                "messageTemplate": "Change the {0} property's type from {1} to {2} Argument &lt;T&gt; type"
            },
            {
                "ruleId": "il-avoid-crm4-wf",
                "messageTemplateId": "message3",
                "messageTemplate": "Replace the Microsoft.Crm.Workflow.Crm{0}Attribute with Microsoft.Xrm.Sdk.Workflow.{0}Attribute"
            },
            {
                "ruleId": "il-avoid-crm4-wf",
                "messageTemplateId": "message4",
                "messageTemplate": "Remove the {0} System.Workflow.ComponentModel.DependencyProperty type field"
            }
        ]
    },
    {
        "description": "Use InvalidPluginExecutionException in plug-ins and workflow activities",
        "guidanceUrl": "https://go.microsoft.com/fwlink/?LinkID=398563&error=il-use-standard-exception&client=PAChecker",
        "include": true,
        "code": "il-use-standard-exception",
        "summary": "Use InvalidPluginExecutionException in plug-ins and workflow activities",
        "howToFix": {
            "summary": ""
        },
        "messageTemplates": [
            {
                "ruleId": "il-use-standard-exception",
                "messageTemplateId": "message1",
                "messageTemplate": "An unguarded throw of type {0} was detected. Refactor this code to either throw an exception of type InvalidPluginExecutionException or guard against thrown exceptions of other types."
            },
            {
                "ruleId": "il-use-standard-exception",
                "messageTemplateId": "message2",
                "messageTemplate": "An unguarded rethrow of type {0} was detected. Refactor this code to either throw an exception of type InvalidPluginExecutionException or guard against thrown exceptions of other types."
            }
        ]
    },
...
]
```

### <a name="see-also"></a>Siehe auch

[Verwenden der Power Apps-Überprüfungs-Web-API](overview.md)<br />
[Abrufen der Regelsatz-Liste](retrieve-rulesets.md)<br />
[Hochladen einer Datei](upload-file.md)<br />
[Analyse aufrufen](analyze.md)<br />
[Überprüfen des Analysestatus](check-status.md)<br />