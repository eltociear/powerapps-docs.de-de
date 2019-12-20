---
title: Ermitteln Sie die URL für Ihre Organisation mithilfe der Web-API (Common Data Service) | Microsoft Docs
description: Hier erfahren Sie, wie Sie Web-API verwenden können, um die zur Laufzeit die Organisationen zu erkunden, oder Instanzen, zu denen der angemeldete Benutzer gehört.
ms.custom: ''
ms.date: 04/22/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
ms.assetid: 2db13b4e-0e7c-4f25-b7be-70a612fb96e2
caps.latest.revision: 18
author: JimDaly
ms.author: jdaly
ms.reviewer: susikka
manager: annbe
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 0d4f785d266604d51d099a5b56885b6ad32b6249
ms.sourcegitcommit: d03915b4e2583327526b448ec10474cedfd7efe0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2019
ms.locfileid: "2854123"
---
# <a name="discover-the-url-for-your-organization-using-the-web-api"></a>Ermitteln Sie die URL für Ihre Organisation mithilfe der Web-API.

[!INCLUDE [cc-discovery-service-description](../includes/cc-discovery-service-description.md)]

Mit dem Web API Discovery Service können Sie die Standardparameter `$filter` und `$select` für eine Web API Service-Anforderung verwenden, um die zurückgegebene Liste der Instanzdaten anzupassen.
<!-- TODO should only talk about the global discovery service -->

## <a name="global-discovery-service"></a>Globaler Suchdienst

Zusätzlich zu Ermittlungsdiensten für bestimmte Datencenter, die für den 2011 (SOAP)-Endpunkt verfügbar sind, und durch die Web-API, gibt es auch einen globalen Ermittlungsdienst nur für Web-API, der sich über alle betriebsbereiten Datencenter erstreckt. Weitere Informationen zu dem Ermittlungsdienst für den 2011-Endpunkt finden Sie unter [Discovery Service](../org-service/discovery-service.md).

> [!NOTE]
> Es wird empfohlen, dass Benutzer vom bisherigen regionalen Suchdienst (`https://disco.crm.dynamics.com`) zum globalen Suchdienst (`https://globaldisco.crm.dynamics.com`) wechseln.
> 
> Für Dynamics 365 US Government-Benutzer ist der globale Suchdienst für **GCC**- und **GCC High**-Benutzer verfügbar, und die URL unterscheidet sich von der regulären globalen Suchdienst-URL. Weitere Informationen: [Dynamics 365 Government-URLs](https://docs.microsoft.com/dynamics365/customer-engagement/admin/government/microsoft-dynamics-365-government#dynamics-365-us-government-urls).

  
## <a name="information-provided-by-the-discovery-service"></a>Informationen, die vom Ermittlungsdienst bereitgestellt werden 
 
 Organisationsinformationen werden in der Entität `Instance` des Ermittlungsdiensts gespeichert.  Um die Art der Informationen anzuzeigen, die in dieser Entität enthalten sind, senden Sie eine HTTP GET-Anforderung zum Service für eine Ihrer Instanzen.  
  
```http  
GET https://globaldisco.crm.dynamics.com/api/discovery/v1.0/Instances(UniqueName='myorg')  
```  
  
Im oben genannten Beispiel wird der globale Ermittlungsdienst von Common Data Service verwendet, um die Organisationsinformationen der Instanz mit einem eindeutigen Namen "myorg" abzurufen. Weitere Details zu dieser Anforderung werden später in diesem Thema ausführlicher behandelt.  

 

  
### <a name="scope-of-the-returned-information"></a>Umfang der zurückgegebenen Informationen

Für den globalen Ermittlungsdienst gibt der Entitätssatz `Instances` den Entitätssatz zurück, auf den der Benutzer an allen geografischen Orten Zugriff hat, wenn keine Filter angewendet werden.   Die zurückgegebenen Daten haben einen Umfang, wie unten beschrieben.  
  
-   Enthält alle Instanzen in der Handelscloud, wo der Benutzer bereitgestellt und aktiviert ist, außer dass Sovereign-Couds-Instanzen nicht zurückgegeben werden
-   Enthält nicht Instanzen, bei denen das Konto des Benutzers deaktiviert ist
-   Enthält keine Instanzen, bei denen Benutzer auf Basis einer Instanzsicherheitsgruppe gefiltert wurden
-   Umfasst nicht Instanzen, auf die der Benutzer Zugriff hat, da er ein stellvertretender Administrator ist
-   Wenn der aufrufende Benutzer Zugriff auf keine Instanzen hat, gibt die Antwort einfach eine leere Liste zurück

## <a name="how-to-access-the-discovery-services"></a>Wie erfolgt der Zugriff auf die Ermittlungsdienste

Im Allgemeinen hat die Web-API-Adresse des Ermittlungsdiensts das folgende Format: `<service base address>/api/discovery/`.  Die Adressen für jeden Bereitstellungstyp werden unten identifiziert. Sie können die Web-API-Adressen und Versionsnummer für Ihre Bereitstellung einfach in der Common Data Service-Webanwendung finden, indem Sie zu **Einstellungen > Anpassung > Entwicklerressourcen** navigieren  
  
### <a name="common-data-service-discovery-services"></a>Common Data Service-Suchdienste  

Die Dienstbasisadresse des globalen Ermittlungsdiensts ist: `https://globaldisco.crm.dynamics.com/`. Dies führt als Ergebnis zur Serviceadresse von `https://globaldisco.crm.dynamics.com/api/discovery/`.  
  
## <a name="using-the-discovery-service"></a>Verwenden des Suchdiensts  

Ein Entitätssatz mit der Bezeichnung `Instances` wird zum Abrufen von Instanzinformationen verwendet. Sie können `$select` und `$filter` mit der Instanzentität verwenden, die für das Filtern der zurückgegebenen Daten festgelegt wurde. Sie können auch mithilfe `$metadata` das Metadatendokument des Services abrufen.  
  
### <a name="authentication"></a>Authentifizierung

Common Data Service-Web-API-Instanzen des Ermittlungsdiensts benötigen die Authentifizierung mit OAuth-Zugriffstokens.

Wenn der Ermittlungsdienst für die OAuth-Authentifizierung konfiguriert ist, löst eine Anforderung, die an die Service-Web-API ohne einen Zugriffstoken gesendet wird, eine Trägerabfrage mit der Autorität des "allgemeinen" Endpunkts und der Ressourcenkennung des Service aus.
### <a name="cors-support"></a>CORS-Support

Die Ermittlungsdienst-Web-API unterstützt den CORS-Standard für den ursprungsübergreifenden Zugriff, wie das für die Web-API zutrifft.  Für weitere Informationen zu CORS-Support siehe [Verwenden von OAuth mit Cross-Origin Resource Sharing, um eine Single Page-Anwendung zu verbinden](../oauth-cross-origin-resource-sharing-connect-single-page-application.md)  
  
### <a name="examples"></a>Beispiele  
  
-   Rufen Sie die Details einer bestimmten Instanz ab. Wenn Sie die GUID auslassen, werden alle Instanzen zurückgegeben, auf die der authentifizierte Benutzer Zugriff hat.  
  
    ```http      
    GET https://globaldisco.crm.dynamics.com/api/discovery/v1.0/Instances(<guid>)
    GET https://disco.crm.dynamics.com/api/discovery/v9.0/Instances(<guid>)  
    ```  
  
-   Sie können das UniqueName-Attribut als Alternativschlüssel verwenden.  
  
    ```http  
    GET https://globaldisco.crm.dynamics.com/api/discovery/v1.0/Instances(UniqueName='myorg')  
    ```  
  
-   Rufen Sie eine Liste verfügbarer Instanzen ab, die nach Produktionstyp gefiltert sind.  
  
    ```http  
    GET https://globaldisco.crm.dynamics.com/api/discovery/v1.0/Instances?$select=DisplayName,Description&$filter=Type+eq+0   
    ```  
  
-   Rufen Sie den Kennungseigenschaftswert einer bestimmten Instanz ab.  
  
    ```http  
    GET https://disco.crm.dynamics.com/api/discovery/v9.0/Instances(UniqueName='myorg')/Id/$value  
    ```

## <a name="see-also"></a>Siehe auch

[Web API Globaler Discovery Service-Beispiel (C#)](samples/global-discovery-service-csharp.md)

