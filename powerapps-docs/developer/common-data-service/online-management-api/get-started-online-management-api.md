---
title: Erste Schritte mit der Online Management API für Common Data Service| MicrosoftDocs
description: Enthält grundlegende Informationen, die Ihnen den Einstieg in die Online Admin API für Common Data Service erleichtern.
ms.date: 09/30/2019
ms.service: powerapps
ms.topic: conceptual
ms.assetid: c292c148-01f0-41f6-a2fe-7ed05a01a733
author: KumarVivek
ms.author: kvivek
manager: annbe
search.audienceType:
- developer
search.app:
- PowerApps
ms.openlocfilehash: 22ea4e2dc02ee272af3cb8fa916d8d20219b6b6a
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "2752954"
---
# <a name="get-started-with-online-management-api"></a>Erste Schritte mitOnline Management API 

Dieses Thema enthält grundlegende Informationen, die Ihnen den Einstieg in die Online Admin API für Common Data Service erleichtern.

## <a name="office-365-admin-roles"></a>Office 365 Administratorrollen

Um die Online Management API zu verwenden, müssen Ihnen folgende Administratorrollen im Office 365 Tenant zugewiesen sein:

- Globaler Administrator
- Serviceadministrator.

Weitere Information zu diesen Rollen finden Sie unter [Informationen zu Office 365 Administratorrollen](https://support.office.com/article/About-Office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d)

## <a name="service-url"></a>Dienst-URL

Der Service URL definiert die Endpunktadresse zum Zugreifen auf REST-API. Um beliebige Aktionen mithilfe der Online Verwaltung API auszuführen, müssen Sie die Anforderungs-URL im folgenden Format angeben:

`{ServiceUrl}/api/v1.2/{resource}`

Sie können beispielsweise folgende URL mit einer **GET** Anforderung übergeben, um die Instanzen im Office Office 365 Mandanten in Nordamerika abzurufen:

`https://admin.services.crm.dynamics.com/api/v1.2/instances`


Die folgende Tabelle listet die Service-URLs der Online Management API für weltweite Office 365 Rechenzentren auf.

|Speicherort | Dienst-URL |
|---------|-------------|
|Nordamerika | https://admin.services.crm.dynamics.com |
|Nordamerika 2 | https://admin.services.crm9.dynamics.com |
|Europa, Naher Osten und Afrika (EMEA) | https://admin.services.crm4.dynamics.com |
|Asien-Pazifik (APAC) | https://admin.services.crm5.dynamics.com |
|Ozeanien | https://admin.services.crm6.dynamics.com |
|Japan (JPN) | https://admin.services.crm7.dynamics.com |
|Südamerika | https://admin.services.crm2.dynamics.com |
|Indien (IND) | https://admin.services.crm8.dynamics.com |
|Kanada | https://admin.services.crm3.dynamics.com |
|Vereinigtes Königreich | https://admin.services.crm11.dynamics.com |
|Frankreich | https://admin.services.crm12.dynamics.com |

## <a name="standard-headers"></a>Standardkopfzeilen

Die Online Management API hat folgenden Standardanforderung und Antwortheader.

### <a name="request-headers"></a>Auftragskopfzeilen

| Kopfzeile | Typ | Beschreibung  |
|--------|------|--------------|
|**Sprache-akzeptieren**|String|Gibt die bevorzugte Sprache für die Antwort an. Weitere Informationen zur Kopfzeile: [Sprache-akzeptieren (MDN-Internet-Dokumente)](https://developer.mozilla.org/docs/Web/HTTP/Headers/Accept-Language)|
|**Autorisierung**|String|Gibt die Anmeldeinformationen an, um einen Benutzer mit dem Online Management-API-Dienst zu authentifizieren. Weitere Informationen zur Kopfzeile: [Autorisierung (MDN-Internet-Dokumente)](https://developer.mozilla.org/docs/Web/HTTP/Headers/Authorization)|

Informationen zum Festlegen dieser Kopfzeilen in Ihrer Anfrage finden Sie unter [Authentifizieren Sie sich, um die Online Online Management-API zu verwenden](authentication.md).

### <a name="response-headers"></a>Antwortheader

| Kopfzeile | Beschreibung  |
|--------|--------------|
|**Vorgang-Speicherort**|Für Vorgänge mit langer Laufzeit gibt es den Speicherort der Vorgangsabfrage an, um den Status zu überprüfen. Beispiel:<br />`https://admin.services.crm.dynamics.com/operations/{operationid}`|
|**Wiederholung-nach**|Für Vorgänge mit langer Laufzeit gibt es die empfohlene Zeitperiode in Sekunden an, nach der der Vorgangsstatus erneut abzufragen ist. Beispiel: **30**|
    
### <a name="related-topics"></a>Verwandte Themen  

[Authentifizieren Sie sich, um die Online Management API zu verwenden](authentication.md)

[Vorgänge, die von Online Management API unterstützt werden](operations-supported.md)

[Online Management API-Referenz](/rest/api/admin.services.crm.dynamics.com)
