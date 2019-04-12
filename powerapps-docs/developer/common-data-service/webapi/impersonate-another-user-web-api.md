---
title: Wechsel der Identität eines Benutzers mithilfe der Web-API (Common Data Service) | Microsoft Docs
description: 'Der Identitätswechsel wird verwendet, um die Geschäftslogik (Code) im Auftrag eines anderen Common Data Service auszuführen, um eine gewünschte Funktion oder einen Service mithilfe der entsprechenden rollen- und objektbasierten Sicherheit dieses Benutzers auszuführen. Lesen Sie, wie Sie die Identität eines anderen Benutzers in Common Data Service mithilfe der Web-API wechseln können.'
ms.custom: ''
ms.date: 03/18/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: 74d07683-63ff-4d05-a434-dcfd44cd634d
caps.latest.revision: 9
author: brandonsimons
ms.author: jdaly
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---

<!-- TOD0: The higher level topic [Impersonate another user](../impersonate-another-user.md) should include all generic concepts.
This topic should only cover the Web API specific details -->


# <a name="impersonate-another-user-using-the-web-api"></a>Annehmen eines anderen Benutzerkontos mit Web API

Es gibt Zeiten, in denen Ihr Code im Namen eines anderen Benutzers Vorgänge ausführen muss. Wenn das Systemkonto, das Ihren Code ausführt, über die erforderlichen Berechtigungen verfügt, können Sie Vorgänge im Namen anderer Benutzer durchführen.  
  
<a name="bkmk_Requirementsforimpersonation"></a>

## <a name="requirements-for-impersonation"></a>Anforderungen für den Identitätswechsel

Der Identitätswechsel wird verwendet, um die Geschäftslogik (Code) im Auftrag eines anderen Common Data Service auszuführen, um eine gewünschte Funktion oder einen Service mithilfe der entsprechenden rollen- und objektbasierten Sicherheit dieses Benutzers auszuführen. Dies ist erforderlich, da die Common Data Service-Webdienste von verschiedenen Clients und Services im Auftrag eines Common Data Service-Benutzers aufgerufen werden können, etwa in einem Workflow oder einer benutzerdefinierten ISV-Lösung. Der Identitätswechsel betrifft zwei verschiedene Benutzerkonten: ein Benutzerkonto (A) wird bei der Ausführung von Code zur Ausführung einer Aufgabe im Auftrag eines anderen Benutzers (B) verwendet.  
  
Benutzerkonto (A) benötigt die Berechtigung `prvActOnBehalfOfAnotherUser`, die in der Sicherheitsrolle "Stellvertretung" enthalten ist. Die aktuelle Gruppe von Rechten, die verwendet wird, um Daten zu ändern, ist die Schnittmenge der Rechte, die der Stellvertreterbenutzer besitzt, und der des Benutzers, dessen Identität angenommen wird. In anderen Worten: Benutzer (A) kann nur dann etwas tun, wenn Benutzer (A) und der Benutzer (B), dessen Identität angenommen wird, über die dazu erforderlichen Rechte verfügen.  
  
<a name="bkmk_Howtoimpersonateauser"></a>

## <a name="how-to-impersonate-a-user"></a>So wird die Identität eines Benutzers angenommen

Es gibt zwei Möglichkeiten, um die Identität eines Benutzers anzunehmen. Beide sind möglich, indem ein Header mit der entsprechenden Benutzer-ID übergeben wird.

 1. **Bevorzugt:** Nehmen Sie die Identität eines Benutzers auf Basis der Azure Active Directory (AAD)-Objekt-ID an, indem Sie diesen Wert zusammen mit dem Header `CallerObjectId` übergeben.
2. **Legacy:** Um die Identität eines Benutzers auf Grundlage der systemuserid anzunehmen, können Sie `MSCRMCallerID` mit dem entsprechenden guid-Wert nutzen.

 In diesem Beispiel wird im Auftrag des Benutzers eine neue Firmenentität mit der Azure Active Directory-Objekt-ID `e39c5d16-675b-48d1-8e67-667427e9c084` erstellt.   
  
 **Anforderung**  
```http 
POST [Organization URI]/api/data/v9.0/accounts HTTP/1.1  
CallerObjectId: e39c5d16-675b-48d1-8e67-667427e9c084  
Accept: application/json  
Content-Type: application/json; charset=utf-8  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
  
{"name":"Sample Account created using impersonation"}  
```  
  
 **Antwort**  
```http 
HTTP/1.1 204 No Content  
OData-Version: 4.0  
OData-EntityId: [Organization URI]/api/data/v9.0/accounts(00000000-0000-0000-000000000003)  
```  
  
<a name="bkmk_Determinetheactualuser"></a>

## <a name="determine-the-actual-user"></a>Bestimmen des tatsächlichen Benutzers

Wenn eine Vorgang wie das Erstellen einer Entität mithilfe des Identitätswechsels ausgeführt wird, kann der Benutzer, der den Vorgang tatsächlich ausgeführt hat, über die Abfrage des Datensatzes in der Einzelwert-Navigationseigenschaft `createdonbehalfby` abgerufen werden. Eine entsprechende einwertigen modifiedonbehalfby-Navigationseigenschaft ist für Vorgänge verfügbar, durch die die Entität aktualisiert wird.  
  
 **Anforderung**

```http 
GET [Organization URI]/api/data/v9.0/accounts(00000000-0000-0000-000000000003)?$select=name&$expand=createdby($select=fullname),createdonbehalfby($select=fullname),owninguser($select=fullname) HTTP/1.1   
Accept: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
```  
  
 **Antwort**  
```http 
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
ETag: W/"506868"  
  
{
  "@odata.context": "[Organization URI]/api/data/v9.0/$metadata#accounts(name,createdby(fullname,azureactivedirectoryobjectid),createdonbehalfby(fullname,azureactivedirectoryobjectid),owninguser(fullname,azureactivedirectoryobjectid))/$entity",
  "@odata.etag": "W/\"2751197\"",
  "name": "Sample Account created using impersonation",
  "accountid": "00000000-0000-0000-000000000003",
  "createdby": {
    "@odata.etag": "W/\"2632435\"",
    "fullname": "Impersonated User",
    "azureactivedirectoryobjectid": "e39c5d16-675b-48d1-8e67-667427e9c084",
    "systemuserid": "75df116d-d9da-e711-a94b-000d3a34ed47",
    "ownerid": "75df116d-d9da-e711-a94b-000d3a34ed47"
  },
  "createdonbehalfby": {
    "@odata.etag": "W/\"2632445\"",
    "fullname": "Actual User",
    "azureactivedirectoryobjectid": "3d8bed3e-79a3-47c8-80cf-269869b2e9f0",
    "systemuserid": "278742b0-1e61-4fb5-84ef-c7de308c19e2",
    "ownerid": "278742b0-1e61-4fb5-84ef-c7de308c19e2"
  },
  "owninguser": {
    "@odata.etag": "W/\"2632435\"",
    "fullname": "Impersonated User",
    "azureactivedirectoryobjectid": "e39c5d16-675b-48d1-8e67-667427e9c084",
    "systemuserid": "75df116d-d9da-e711-a94b-000d3a34ed47",
    "ownerid": "75df116d-d9da-e711-a94b-000d3a34ed47"
  }
}
```  
  
### <a name="see-also"></a>Siehe auch

[Annehmen der Identität eines anderen Benutzers](../impersonate-another-user.md)<br />
[Annehmen eines anderen Benutzerkontos mit dem Unternehmensdienst](../impersonate-another-user.md#impersonate-another-user-using-the-organization-service)<br />
[Vorgänge mithilfe der Web-API ausführen](perform-operations-web-api.md)<br />
[HTTP-Anforderungen verfassen und Fehler beheben](compose-http-requests-handle-errors.md)<br />
[Datenabfrage mit Web-API](query-data-web-api.md)<br />
[Erstellen einer Entität mithilfe des Web-API](create-entity-web-api.md)<br />
[Abrufen einer Entität mithilfe des Web-API](retrieve-entity-using-web-api.md)<br />
[Entitäten aktualisieren und löschen mithilfe der Web API](update-delete-entities-using-web-api.md)<br />
[Entitäten zuordnen und Zuordnungen aufheben mithilfe der Web API](associate-disassociate-entities-using-web-api.md)<br />
[Nutzen von Web-API-Funktionen](use-web-api-functions.md)<br />
[Nutzen von Web-API-Aktionen](use-web-api-actions.md)<br />
[Ausführen von Batchbetrieben mithilfe der Web-API](execute-batch-operations-using-web-api.md)<br />
[Bedingte Vorgänge mithilfe der Web-API ausführen](perform-conditional-operations-using-web-api.md)
