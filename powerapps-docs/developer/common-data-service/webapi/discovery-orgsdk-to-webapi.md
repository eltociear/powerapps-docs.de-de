---
title: Ändern Sie Ihren Code, um den globalen Suchdienst zu nutzen (Common Data Service) | Microsoft Docs
description: Aktualisieren Sie Ihren Anwendungscode, um Suchdienst-Aufrufe mithilfe einer modernen RESTful API durchzuführen.
ms.custom: ''
ms.date: 1/16/2020
ms.reviewer: pehecke
ms.service: powerapps
ms.topic: article
author: bpevans
ms.author: bevans
manager: kvivek
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: ca4a6ad8d86999a878ce51d8fffe08039230a12f
ms.sourcegitcommit: 6b2961308c41867756ecdd55f55eccbebf70f7f0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2020
ms.locfileid: "2975898"
---
# <a name="modify-your-code-to-use-global-discovery-service"></a>Ändern Sie Ihren Code, um den globalen Suchdienst zu verwenden

Die Suchdienst APIs können von Ihrer Anwendung verwendet werden, um Geschäftsorganisationsinstanzen zu ermitteln, auf die der Anwendungsbenutzer Zugriff hat. Wenn Ihre Anwendung derzeit die Organisationsdienst-API auf dem SOAP-Endpunkt 2011 verwendet, um Organisationsinstanzen zu ermitteln, können Sie die Schritte in dieser Thema ausführen und Ihre Anwendung mithilfe der OData V4 RESTful-API mit der globalen Suchdienst URL in Den Zugriff auf Organisationsdetails konvertieren. Wenn Ihre Anwendung mithilfe der regionalen Suchdienst-URL auf den Suchdienst zugreift, müssen Sie den Anwendungscode von der Verwendung der regionalen URL in die globale Suchdienst-URL ändern.

Eine detaillierte Beschreibung der Verwendung des Suchdienstes mit der RESTful-API finden Sie auf der Seite [URL für Ihre Organisation suchen](/powerapps/developer/common-data-service/webapi/discover-url-organization-web-api).

> [!IMPORTANT]
> Beim Zugriff auf den Suchdienst wird dringend empfohlen, dass Ihre Anwendung den *globalen* Suchdienst-Endpunkt verwendet (https://globaldisco.crm.dynamics.com) und nicht den *regionalen* Suchdienst-Endpunkt, der am 2. März 2020 [veraltet](/power-platform/important-changes-coming#regional-discovery-service-is-deprecated) sein wird. Der globale Suchdienst ist nur verfügbar, wenn die RESTful-API verwendet wird.

Der Rest dieses Dokuments beschreibt die Änderungen, die möglicherweise erforderlich sind, um den Discovery Dienst mithilfe der RESTful-API aufzurufen.

## <a name="authentication"></a>Authentifizierung
Für den Zugriff auf den Suchdienst mithilfe der RESTful-API ist eine Authentifizierung mit einer Oauth 2.0-Zugriffstoken erforderlich.
Wenn Ihr Anwendungscode WS-Trust SAML-Token für die Authentifizierung verwendet, müssen Sie den Anwendungscode ändern, um ein Oauth 2.0-Token von Azure Active Directory (AD) abzurufen, und dieses Token dann im Autorisierungsheader der Discovery Service-API-Aufrufe hinzufügen. Weitere Informationen: [Verwendung von OAuth mit Common Data Service](../authenticate-oauth.md).

## <a name="odata-api-calls"></a>OData-API-Aufrufe
Die unten gezeigten HTTP-Beispielanforderungen werden von der RESTful-API des Suchdienstes unterstützt. In diesen Beispielen werden die Instanzen-API verwendet, um dieselben Organisationsdaten wie die <xref:Microsoft.Xrm.Sdk.Discovery.RetrieveOrganizationsRequest> und <xref:Microsoft.Xrm.Sdk.Discovery.RetrieveOrganizationRequest> Nachrichtenanforderungen der Organisationsdienst-API zurückzugeben.

-    Abrufen aller Instanzen für den Benutzer in allen Regionen.
```http  
GET https://globaldisco.crm.dynamics.com/api/discovery/v2.0/Instances
```  
-    Abrufen aller Instanzen für den Benutzer in einer spezifischen Region.
```http  
GET  https://globaldisco.crm.dynamics.com/api/discovery/v2.0/Instances(Region={region})
```
Antwort
```javascript
{
  "value":[
    {
      "Id":"<GUID>",
      "UniqueName":"myorg",
      "UrlName":"orgurlname",
      "FriendlyName":"My Org",
      "State":0,
      "Version":"<Version>",
      "Url":"https://orgurlname.crm.dynamics.com",
      "ApiUrl":"https://orgurlname.api.crm.dynamics.com"
    }
  ]
}
```

-    Einzelne Instanz nach ID abrufen
```http  
GET https://globaldisco.crm.dynamics.com/api/discovery/v2.0/Instances(<guid>)
```  
-    Einzelne Instanz nach eindeutigem Namen abrufen
```http  
GET https://globaldisco.crm.dynamics.com/api/discovery/v2.0/Instances(UniqueName='myorg')  
```  

Antwort
```javascript
{
  "Id":"<GUID>",
  "UniqueName":"myorg",
  "UrlName":"orgurlname",
  "FriendlyName":"My Org",
  "State":0,
  "Version":"<Version>",
  "Url":"https://orgurlname.crm.dynamics.com",
  "ApiUrl":"https://orgurlname.api.crm.dynamics.com"
}
```

## <a name="mapping-of-fields"></a>Zuordnen von Feldern
Die folgende Tabelle zeigt die Feldzuordnung in den Antworten, die vom Ermittlungsdienst zurückgegeben werden, wenn die beiden APIs verwendet werden. Diese gelten für alle oben genannten Beispielaufrufe.

Antwortfeld (SOAP Endpunkt) |    Antwortfeld (OData V4 RESTful Endpunkt)
------------------------------------|---------------------------------
Endpunkte[WebApplication] | Url
Endpunkt[OrganizationService]  | {ApiUrl}/XRMServices/2011/Organization.svc
Endpunkt[OrganizationDataService] |{ApiUrl}//XRMServices/2011/OrganizationData.svc
FriendlyName|FriendlyName
OrganizationId|Kennung
OrganizationVersion|Version
Status | Status<br/><ul><li>0 : Aktiviert</li><li>1 : Deaktiviert</li><ul>
UniqueName|UniqueName
UrlName|UrlName

## <a name="deprecated-api-call"></a>Veralteter API-Aufruf
Die Organisationsdienst-API-Nachricht GetUserIdByExternalId wird in der RESTful-API nicht unterstützt.

## <a name="see-also"></a>Siehe auch
[Suchdienste](/powerapps/developer/common-data-service/discovery-service)

[Verwenden der Common Data Service-Web-API](/powerapps/developer/common-data-service/webapi/discover-url-organization-web-api)
