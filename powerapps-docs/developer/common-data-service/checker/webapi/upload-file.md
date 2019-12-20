---
title: Hochladen einer Datei für die Analyse | Microsoft Docs
description: Sehen Sie sich an, wie Sie eine POST-Anfrage mithilfe der Power Apps-Überprüfungs-Web-API stellen, um eine Datei für die Analyse hochzuladen.
ms.custom: ''
ms.date: 06/04/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
ms.assetid: 08d7d73b-1377-4d3f-b8ef-5c89b19dd735
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
ms.openlocfilehash: f2e83835e80c2393b9b97077c51338c55dd1c3e4
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2019
ms.locfileid: "2861803"
---
# <a name="upload-a-file-for-analysis"></a>Hochladen einer Datei für die Analyse

[!INCLUDE [cc-beta-prerelease-disclaimer](../../../../includes/cc-beta-prerelease-disclaimer.md)]

Der Start eines Analyseauftrags erfordert einen Pfad zu einem Azure-Blob, der über eine URL aufgerufen werden kann. Die Möglichkeit, eine Datei mithilfe des Uploadservices in den Azure-Blob-Speicher in der angegebenen Geografie hochzuladen, wird bereitgestellt. Es ist nicht erforderlich, die API zum Hochladen zu verwenden, um eine Analyse auszuführen. Sie können Dateien mithilfe einer `POST`-Abfrage in Folgendes hochladen: `[Geographical URI]/api/upload?api-version=1.0`. Hochladen einer Datei mit bis zu 30 MB wird unterstützt. Für alle größeren Dateien müssen Sie Ihren eigenen extern zugänglichen Azure-Speicher und eine eigene SAS-URI bereitstellen.

> [!NOTE]
>  Die API erfordert ein OAuth-Token.

<a name="bkmk_headers"></a>

## <a name="headers"></a>Kopfzeilen

|Name|Typ|Erwarteter Wert|Erforderlich?|
|---|---|---|---|
|Autorisierung|Zeichenfolge|Das OAuth 1-Bearertoken mit Azure Active Directory (AAD)-Anwendungs-ID-Anspruch.|Ja|
|x-ms-tenant-id|GUID|Die ID des Mandanten für die Anwendung.|Ja|
|x-ms-correlation-id|GUID|Der Bezeichner für die Analyseausführung. Sie sollten dieselbe ID für die gesamte Ausführung angeben (Upload, Analyse, Status).|Ja|
|Inhaltstyp|Objekt|mehrteilig/Formulardaten|Ja|
|Inhaltsdisposition|Objekt|Enthalten die Namen- und Dateinamenparameter, beispielsweise:<br />`form-data; name="solution1.zip"; filename="solution1.zip"`|Ja|

<a name="bkmk_responses"></a>

## <a name="expected-responses"></a>Erwartete Antworten

|HTTP-Statuscode|Szenario|Ergebnis|
|---|---|---|
|200|Upload erfolgt|Kein Ergebnistext|
|400|Eine Nicht-ZIP-Datei wurde gesendet, falsche Parameter, oder eine Datei wurde mit einem Virus eingeschlossen|Kein Ergebnistext|
|413|Datei ist zu groß|Kein Ergebnistext|

<a name="bkmk_upload"></a>

## <a name="example-upload-a-file"></a>Beispiel: Hochladen einer Datei

Dieses Beispiel veranschaulicht, wie eine Datei hochgeladen werden kann, die analysiert werden soll.

**Anforderung**

```http
POST [Geographical URI]/api/upload
Accept: application/json
x-ms-correlation-id: 9E378E56-6F35-41E9-BF8B-C0CC88E2B832
x-ms-tenant-id: F2E60E49-CB87-4C24-8D4F-908813B22506
Content-Type: multipart/form-data
Content-Disposition: form-data; name=mySolution.zip; filename=mySolution.zip
```

**Antwort**

```http
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8

["https://mystorage.blob.core.windows.net/solution-files/0a4cd700-d1d0-4ef8-8318-e4844cc1636c/mySolution.zip?sv=2017-11-09&sr=b&sig=xyz&se=2019-06-11T19%3A05%3A20Z&sp=rd"]
```

### <a name="see-also"></a>Siehe auch

[Verwenden der Power Apps-Überprüfungs-Web-API](overview.md)<br />
[Abrufen der Regelsatz-Liste](retrieve-rulesets.md)<br />
[Abrufen der Regel-Liste](retrieve-rules.md)<br />
[Analyse aufrufen](analyze.md)<br />
[Überprüfen des Analysestatus](check-status.md)<br />