---
title: Entitäten zuordnen und Zuordnungen aufheben mithilfe der Web-API (Common Data Service)| Microsoft-Dokumentation
description: Lesen Sie, wie eine Referenz auf eine sammlungwertige Navigationseigenschaft hinzuzufügen, eine Referenz zu entfernen und eine vorhandene Referenz mithilfe der Web-API zu ändern.
ms.custom: ''
ms.date: 10/31/2018
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
ms.assetid: ad4e4eac-117a-4958-9df0-b7353305b0c7
caps.latest.revision: 13
author: JimDaly
ms.author: jdaly
ms.reviewer: susikka
manager: annbe
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 1b1aee98b1fb6048c875ef41672d105cb096ed1a
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748501"
---
# <a name="associate-and-disassociate-entities-using-the-web-api"></a>Entitäten zuordnen und Zuordnungen aufheben mithilfe der Web API

Es gibt einige Methoden, die Sie anwenden können, um Entitäten zuzuordnen und solche Zuordnungen wieder aufzuheben. Welche Methode Sie anwenden, hängt davon ab, ob Sie die Entitäten erstellen oder aktualisieren, und davon, ob Sie im Kontext der referenzierten oder der referenzierenden Entität arbeiten.  

<a name="bkmk_Addareferencetoacollection"></a>

## <a name="add-a-reference-to-a-collection-valued-navigation-property"></a>Fügen Sie eine Referenz auf eine sammlungswertige Navigationseigenschaft hinzu

 Das folgende Beispiel zeigt, wie man eine vorhandene Verkaufschancenentität mit dem Wert `opportunityid` von `00000000-0000-0000-0000-000000000001` zur sammlungwertigen `opportunity_customer_accounts` Navigationseigenschaft für eine Firmenentität mit dem Wert `accountid` von `00000000-0000-0000-0000-000000000002` verbindet. Dieses ist eine 1:n-Beziehung, aber Sie können die gleiche Operation für eine N:N-Beziehung durchführen.  
  
**Anforderung**  
```http  
POST [Organization URI]/api/data/v9.0/accounts(00000000-0000-0000-0000-000000000002)/opportunity_customer_accounts/$ref HTTP/1.1   
Content-Type: application/json   
Accept: application/json   
OData-MaxVersion: 4.0   
OData-Version: 4.0  
  
{  
"@odata.id":"[Organization URI]/api/data/v9.0/opportunities(00000000-0000-0000-0000-000000000001)"  
}  
```  
  
**Antwort**  
```http 
HTTP/1.1 204 No Content  
OData-Version: 4.0  
```  
  
<a name="bkmk_Removeareferencetoanentity"></a>

## <a name="remove-a-reference-to-an-entity"></a>Entfernen Sie eine Referenz auf eine Entität

 Nutzen Sie eine DELETE-Anfrage, um eine Referenz auf eine Entität zu entfernen. Die Weise, wie Sie dies tun, ist unterschiedlich, abhängig davon, ob Sie sich auf eine sammlungswertige Navigationseigenschaft oder auf eine einzelwertige Navigationseigenschaft beziehen.  
  
 **Anforderung**  
 Für eine sammlungswertige Navigationseigenschaft verwenden Sie das Folgende.  
  
```http  
DELETE [Organization URI]/api/data/v9.0/accounts(00000000-0000-0000-0000-000000000002)/opportunity_customer_accounts/$ref?$id=[Organization URI]/api/data/v9.0/opportunities(00000000-0000-0000-0000-000000000001) HTTP/1.1  
Accept: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
```  
  
 Oder, verwenden Sie dieses.  
  
```http 
DELETE [Organization URI]/api/data/v9.0/accounts(00000000-0000-0000-0000-000000000002)/opportunity_customer_accounts(00000000-0000-0000-0000-000000000001)/$ref HTTP/1.1  
Accept: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
```  
  
 **Anforderung**  
 Für eine einzelwertige Navigationseigenschaft entfernen Sie den `$id` Querystring-Parameter.  
  
```http 
DELETE [Organization URI]/api/data/v9.0/opportunities(00000000-0000-0000-0000-000000000001)/customerid_account/$ref HTTP/1.1  
Accept: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
```  
  
 **Antwort**  
 Eine erfolgreiche Antwort hat auf jeden Fall Status 204.  
  
```http 
HTTP/1.1 204 No Content  
OData-Version: 4.0  
```  
  
<a name="bkmk_Changethereferenceinasingle"></a>
 
## <a name="change-the-reference-in-a-single-valued-navigation-property"></a>Ändern Sie die Referenz in einer einzelwertigen Navigationseigenschaft

 Sie können Entitäten zuweisen, indem Sie den Wert einer einzelwertigen Navigationseigenschaft unter Verwendung einer PUT-Anfrage mit dem folgenden Muster einstellen.  
  
 **Anforderung**

```http 
PUT [Organization URI]/api/data/v9.0/opportunities(00000000-0000-0000-0000-000000000001)/customerid_account/$ref HTTP/1.1  
Content-Type: application/json  
Accept: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
  
{  
 "@odata.id":"[Organization URI]/api/data/v9.0/accounts(00000000-0000-0000-0000-000000000002)"  
}  
```  
  
 **Antwort**  

```http 
HTTP/1.1 204 No Content  
OData-Version: 4.0  
```  
  
<a name="bkmk_Associateentitiesoncreate"></a>

## <a name="associate-entities-on-create"></a>Entitäten bei Erstellung zuordnen

 Wie in [Erstellen verbundener Entitäten in einen Vorgang](create-entity-web-api.md#bkmk_CreateRelated) beschrieben ist, können neue Entitäten mit Beziehungen mithilfe von *deep insert* erstellt werden.  
  
<a name="bkmk_Associateentitiesonupdate"></a>

## <a name="associate-entities-on-update-using-single-valued-navigation-property"></a>Zuordnen von Entitäten beim Update mithilfe der einzelwertigen Navigationseigenschaft

 Sie können Entitäten beim Update unter Verwendung der gleichen Message verbinden, die im [Basic update](update-delete-entities-using-web-api.md#bkmk_update) beschrieben wird, aber Sie müssen die Anmerkung @odata.bind verwenden, um den Wert einer einzelwertigen Navigationseigenschaft einzustellen. Das folgende Beispiel ändert die Firma, die mit einer Verkaufschance verknüpft ist, unter Verwendung der einzelwertigen `customerid_account` Navigationseigenschaft.  
  
 **Anforderung**

```http 
PATCH [Organization URI]/api/data/v9.0/opportunities(00000000-0000-0000-0000-000000000001) HTTP/1.1  
Content-Type: application/json  
Accept: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
  
{  
 "customerid_account@odata.bind":"[Organization URI]/api/data/v9.0/accounts(00000000-0000-0000-0000-000000000002)"  
}  
```  
  
 **Antwort**  

```http 
HTTP/1.1 204 No Content  
OData-Version: 4.0  
```  
<a name="bkmk_Associateentitiesonupdate_multi"></a>

## <a name="associate-entities-on-update-using-collection-valued-navigation-property"></a>Zuordnen von Entitäten beim Update mithilfe der sammlungswertigen Navigationseigenschaft

Im folgenden Beispiel wird gezeigt, wie mehrere Entitäten [ActivityParty](../reference/entities/activityparty.md) mit einer Entität [Email](../reference/entities/email.md) mit der sammlungswertigen Navigationseigenschaft zugeordnet werden `email_activity_parties`.

> [!NOTE]
> Die Zuordnung mehrerer Entitäten zu einer Entität beim Update ist ein spezielles Szenario, das nur mit <xref href="Microsoft.Dynamics.CRM.activityparty?text=activityparty EntityType" /> möglich ist.

**Anforderung**

```HTTP
PUT [Organization URI]/api/data/v9.0/emails(2479d20d-3a39-e711-8145-e0071b6a2001)/email_activity_parties
Content-Type: application/json  
Accept: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0

{
    "value": [
        {
            "partyid_contact@odata.bind":"contacts(a30d4045-fc46-e711-8115-e0071b66df51)",
            "participationtypemask":3
            
        },
        {
            "partyid_contact@odata.bind":"contacts(1dcdda07-3a39-e711-8145-e0071b6a2001)",
            "participationtypemask":2
            
        }
        ]
}
```

**Antwort**

```HTTP
HTTP/1.1 204 No Content  
OData-Version: 4.0 
```

### <a name="see-also"></a>Siehe auch

 [Beispiel grundlegender Web-API-Operationen (C#)](samples/basic-operations-csharp.md)   
 [Beispiele grundlegender Web API-Operationen (clientseitiges JavaScript)](samples/basic-operations-client-side-javascript.md)   
 [Vorgänge mithilfe der Web-API ausführen](perform-operations-web-api.md)   
 [HTTP-Anforderungen verfassen und Fehler beheben](compose-http-requests-handle-errors.md)   
 [Datenabfrage mit Web-API](query-data-web-api.md)   
 [Erstellen einer Entität mithilfe des Web-API](create-entity-web-api.md)   
 [Abrufen einer Entität mithilfe des Web-API](retrieve-entity-using-web-api.md)   
 [Entitäten aktualisieren und löschen mithilfe der Web API](update-delete-entities-using-web-api.md)   
 [Nutzen von Web-API-Funktionen](use-web-api-functions.md)   
 [Nutzen von Web-API-Aktionen](use-web-api-actions.md)   
 [Ausführen von Batchbetrieben mithilfe der Web-API](execute-batch-operations-using-web-api.md)   
 [Annehmen eines anderen Benutzerkontos mit Web API](impersonate-another-user-web-api.md)   
 [Bedingte Vorgänge mithilfe der Web-API ausführen](perform-conditional-operations-using-web-api.md)
