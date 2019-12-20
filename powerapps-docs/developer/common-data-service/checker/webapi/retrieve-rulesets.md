---
title: Abrufen der Regelsatz-Liste | Microsoft Docs
description: Sehen Sie sich an, wie Sie eine GET-Abfrage mithilfe der Power Apps-Überprüfungs-Web-API stellen, um die Liste der verfügbaren Regelsätze abzurufen.
ms.custom: ''
ms.date: 06/04/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
ms.assetid: 23c9391c-1697-47a3-a8f2-eedd5c862874
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
ms.openlocfilehash: 4bafe4b4e3b287644d9f43d616ae0d2a91274d8a
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2019
ms.locfileid: "2861815"
---
# <a name="retrieve-the-list-of-rulesets"></a>Abrufen der Regelsatz-Liste

[!INCLUDE [cc-beta-prerelease-disclaimer](../../../../includes/cc-beta-prerelease-disclaimer.md)]

Regeln werden zusammen mit einem Regelsatz gruppiert. Regelsätze können eine oder mehrere Regeln haben, es gibt keine Beschränkung. Eine Regel kann in keinem Regelsatz oder in mehreren Regelsätzen enthalten sein. Verwenden Sie eine `GET`-Abfrage, um eine Liste aller verfügbaren Regelsätze zu ermitteln, indem Sie die API, [Geografische URI]/api/ruleset, aufrufen.

> [!NOTE]
>  Die API erfordert kein OAuth-Token, kann jedoch eines akzeptieren, wenn es angegeben wird.

<a name="bkmk_responses"></a>

## <a name="expected-responses"></a>Erwartete Antworten

|HTTP-Statuscode|Szenario|Ergebnis|
|---|---|---|
|200|Mindestens ein Ergebnis wurde gefunden.|Siehe Beispiel unten. Mindestens ein Ergebnis kann zurückgegeben werden.|
|204|Es wurden keine Ergebnisse gefunden.|Es wird kein Ergebnisantworttext zurückgegeben.|

### <a name="expected-response-body"></a>Erwarteter Antworttext

In der folgenden Tabelle wird die Struktur der Antwort für jede Anfrage (nur HTTP-200-Antwort) dargestellt.

|Eigenschaft|Typ|Erwarteter Wert|Erforderlich?|
|---|---|---|---|
|ID|Guid|Bezeichner des Regelsatzes|Ja|
|Name|Zeichenfolge|Anzeigename des Regelsatzes|Ja|

<a name="bkmk_retrieve"></a>

## <a name="example-retrieve-all-rulesets"></a>Beispiel: alle Regelsätze abrufen

In diesem Beispiel werden Daten für alle verfügbaren Regelsätze zurückgegeben.

**Anforderung**

```http
GET [Geographical URI]/api/ruleset?api-version=1.0
Accept: application/json
x-ms-correlation-id: 9E378E56-6F35-41E9-BF8B-C0CC88E2B832
Content-Type: application/json; charset=utf-8
```

**Antwort**

```http
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8

[
    {
        "id": "083a2ef5-7e0e-4754-9d88-9455142dc08b",
        "name": "AppSource Certification"
    },
    {
        "id": "0ad12346-e108-40b8-a956-9a8f95ea18c9",
        "name": "Solution Checker"
    }
]
```

### <a name="see-also"></a>Siehe auch

[Verwenden der Power Apps-Überprüfungs-Web-API](overview.md)<br />
[Abrufen der Regel-Liste](retrieve-rules.md)<br />
[Hochladen einer Datei](upload-file.md)<br />
[Analyse aufrufen](analyze.md)<br />
[Überprüfen des Analysestatus](check-status.md)<br />