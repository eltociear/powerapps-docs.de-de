---
title: Erkennen von doppelten Daten mit der Web-API (Common Data Service) | Microsoft-Dokumentation
description: Lesen Sie, wie Sie mit dem MSCRM.SuppressDuplicateDetections-Header und der Common Data Service-Web-API Duplikate erkennen.
ms.custom: ''
ms.date: 04/06/2020
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
ms.assetid: AE107774-4545-44B4-94C8-A0271EFA7876
caps.latest.revision: 11
author: susikka
ms.author: susikka
manager: shujoshi
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 0a32cc136d9876cdf84acd80a2f5229449115876
ms.sourcegitcommit: 49b69129262a9b530e69508e84c3822b742066df
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/07/2020
ms.locfileid: "3233694"
---
# <a name="detect-duplicate-data-using-the-web-api"></a>Erkennen von doppelten Daten mit der Web-API

Common Data Service WEB API erlaubt es, doppelte Datensätze eines vorhandenen Datensatzes zu erkennen, um Richtigkeit der Daten zu wahren. Ausführliche Informationen zum Erkennen von doppelten Daten mithilfe des Codes, finden Sie unter [Erkennen von doppelten Daten mit Code](../detect-duplicate-data-with-code.md) 

## <a name="detect-duplicates-during-create-operation"></a>Erkennen von Duplikaten beim Vorgang "Erstellen"

Verwenden Sie `MSCRM.SuppressDuplicateDetection` Kopfzeile während `POST`, um während der Erstellung einen doppelten Datensatz eines vorhandenen Datensatzes zu erkennen. Der Wert, der zur Kopfzeile `MSCRM.SuppressDuplicateDetection` zugewiesen wird, bestimmt, ob der Erstellten- oder der Aktualisierungsvorgang abgeschlossen werden kann:

- `true` – Den Datensatz nicht erstellen oder aktualisieren, wenn ein Duplikat gefunden wird.
- `false` – Den Datensatz nicht erstellen oder aktualisieren, wenn ein Duplikat gefunden wird.

> [!NOTE]
> Das Übergeben des optionalen Parameters `CalculateMatchCodeSynchronously` ist nicht erforderlich. Die Zuordnungscodes, die verwendet werden, um Duplikate zu erkennen, werden synchron berechnet, unabhängig von dem Wert, der in diesen Parameter übergeben wird.

Verwenden Sie die Voreinstellungskopfzeile `MSCRM.SuppressDuplicateDetection`, und legen Sie deren Wert in der Internet API-Anforderung auf `false` fest.


> [!NOTE]
> Stellen Sie sicher, dass entsprechende Duplikaterkennungsregeln vorhanden sind. Common Data Service enthält standardmäßige Duplikaterkennungsregeln für Firmen, Kontakte und Leads, jedoch nicht für andere Datensatztypen. Wenn das System Duplikate für andere Datensatztypen erkennen soll, müssen Sie eine neue Regel erstellen. <br/>- Informationen darüber, wie Sie eine Duplikaterkennungsregel mithilfe der Benutzeroberfläche erstellen, finden Sie unter [Einrichten einer Duplikaterkennungsregel, um Ihre Daten sauber zu halten](/dynamics365/customer-engagement/admin/set-up-duplicate-detection-rules-keep-data-clean).<br/>- Weitere Informationen zum Erstellen von Duplikaterkennungsregeln mit Code [vgl. Duplikaterkennungsregeln](../duplicaterule-entities.md). 



<a name="bkmk_create"></a>

###  <a name="example-detect-duplicates-during-create-operation-using-the-web-api"></a>Beispiel: Erkennen Sie Duplikate beim Erstellen-Vorgang mit Internet-API

Im folgenden Beispiel wird veranschaulicht, wie Duplikate während und `Create` und `Update` Vorgängen mithilfe der Kopfzeile `MSCRM.SuppressDuplicateDetection` in der Internet API-Anforderung festgestellt werden.

**Anforderung**
```http
POST [Organization URI]/org1/api/data/v9.0/leads HTTP/1.1
If-None-Match: null
OData-Version: 4.0
OData-MaxVersion: 4.0
Content-Type: application/json
Accept: application/json
MSCRM.SuppressDuplicateDetection: false

{
    "firstname":"Monte",
    "lastname":"Orton",
    "emailaddress1":"monteorton@example.com"
}
```
Wenn ein Leaddatensatz mit demselben `emailaddress1`-Attribut vorhanden ist, wird die folgende Antwort zurückgegeben.

**Antwort**
```json
HTTP/1.1 500 Internal Server Error  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0

{
    "error": {
        "code": "0x80040333",
        "message": "A record was not created or updated because a duplicate of the current record already exists."
    }
}
```
Weisen Sie einen Wert `true` zur `MSCRM.SuppressDuplicateDetection`-Kopfzeile zu, um die Erstellung eines doppelten Datensatzes zu erlauben.

<a name="bkmk_update"></a>

## <a name="detect-duplicates-during-update-operation"></a>Erkennen von Duplikaten beim Vorgang "Update"

Legen Sie den Wert der `MSCRM.SuppressDuplicateDetection`-Kopfzeile zu `false` in Ihrer `PATCH`-Anforderung fest, um die Erstellung eines doppelten Datensatzes während des Aktualisierungsvorgangs zu vermeiden. Standardmäßig wird die Duplikaterkennung unterdrückt, wenn Sie Datensätze mithilfe der Internet API aktualisieren.

###  <a name="example-detect-duplicates-during-update-operation-using-the-web-api"></a>Beispiel: Erkennen Sie Duplikate beim Update-Vorgang mit der Web-API

Das Beispiel, das angezeigt wird unten, versucht, einen Entitätsdatensatz des vorhandenen Leads zu aktualisieren, das denselben Wert des Attributs `emailaddress1` (beispielsweise ein bestehender Datensatz) enthält.

**Anforderung**
```http
PATCH [Organization URI]/api/data/v9.0/leads(c4567bb6-47a3-e711-811b-e0071b6ac1b1) HTTP/1.1
If-None-Match: null
OData-Version: 4.0
OData-MaxVersion: 4.0
Content-Type: application/json
Accept: application/json
MSCRM.SuppressDuplicateDetection: false

{
    "firstname":"Monte",
    "lastname":"Orton",
    "emailaddress1":"monteorton@example.com"
}
```  

**Antwort**
```json  
HTTP/1.1 500 Internal Server Error  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0

{
    "error": {
        "code": "0x80040333",
        "message": "A record was not created or updated because a duplicate of the current record already exists."
    }
}
```

### <a name="see-also"></a>Siehe auch

[Duplikaterkennung mithilfe des Organisation-Service](../org-service/detect-duplicate-data.md)