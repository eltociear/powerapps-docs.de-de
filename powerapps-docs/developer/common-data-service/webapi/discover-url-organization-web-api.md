---
title: Ermitteln Sie die URL für Ihre Organisation mit Web API (Common Data Service for Apps)| Microsoft Docs
description: 'Hier erfahren Sie, wie Sie Web-API verwenden können, um die zur Laufzeit die Organisationen zu erkunden, oder Instanzen, zu denen der angemeldete Benutzer gehört.'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: 2db13b4e-0e7c-4f25-b7be-70a612fb96e2
caps.latest.revision: 18
author: brandonsimons
ms.author: jdaly
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="discover-the-url-for-your-organization-using-the-web-api"></a>Ermitteln Sie die URL für Ihre Organisation mithilfe der Web-API.

[!INCLUDE [cc-discovery-service-description](../includes/cc-discovery-service-description.md)]

Mit dem Web API Discovery Service können Sie die Standardparameter `$filter` und `$select` für eine Web API Service-Anforderung verwenden, um die zurückgegebene Liste der Instanzdaten anzupassen.
<!-- TODO should only talk about the global discovery service -->
Zusätzlich zu Ermittlungsdiensten für bestimmte Datencenter, die für den 2011 (SOAP)-Endpunkt verfügbar sind, und durch die Web-API, gibt es auch einen globalen Ermittlungsdienst nur für Web-API, der sich über alle betriebsbereiten Datencenter erstreckt. Weitere Informationen zu dem Ermittlungsdienst für den 2011-Endpunkt finden Sie unter [Discovery Service](../org-service/discovery-service.md).

  
## <a name="information-provided-by-the-discovery-service"></a>Informationen, die vom Ermittlungsdienst bereitgestellt werden 
 
 Organisationsinformationen werden in der Entität `Instance` des Ermittlungsdiensts gespeichert.  Um die Art der Informationen anzuzeigen, die in dieser Entität enthalten sind, senden Sie eine HTTP GET-Anforderung zum Service für eine Ihrer Instanzen.  
  
```http  
GET https://globaldisco.crm.dynamics.com/api/discovery/v1.0/Instances(UniqueName='myorg')  
```  
  
Im oben genannten Beispiel wird der globale Ermittlungsdienst von CDS for Apps verwendet, um die Organisationsinformationen der Instanz mit einem eindeutigen Namen "myorg" abzurufen. Weitere Details zu dieser Anforderung werden später in diesem Thema ausführlicher behandelt.  
  
### <a name="scope-of-the-returned-information"></a>Umfang der zurückgegebenen Informationen

Für den globalen Ermittlungsdienst gibt der Entitätssatz `Instances` den Entitätssatz zurück, auf den der Benutzer an allen geografischen Orten Zugriff hat, wenn keine Filter angewendet werden.   Die zurückgegebenen Daten haben einen Umfang, wie unten beschrieben.  
  
-   Enthält alle Instanzen in der Handelscloud, wo der Benutzer bereitgestellt und aktiviert ist, außer dass Sovereign-Couds-Instanzen nicht zurückgegeben werden
-   Enthält nicht Instanzen, bei denen das Konto des Benutzers deaktiviert ist
-   Enthält keine Instanzen, bei denen Benutzer auf Basis einer Instanzsicherheitsgruppe gefiltert wurden
-   Umfasst nicht Instanzen, auf die der Benutzer Zugriff hat, da er ein stellvertretender Administrator ist
-   Wenn der aufrufende Benutzer Zugriff auf keine Instanzen hat, gibt die Antwort einfach eine leere Liste zurück

## <a name="how-to-access-the-discovery-services"></a>Wie erfolgt der Zugriff auf die Ermittlungsdienste

Im Allgemeinen hat die Web-API-Adresse des Ermittlungsdiensts das folgende Format: `<service base address>/api/discovery/`.  Die Adressen für jeden Bereitstellungstyp werden unten identifiziert. Sie können die Web-API-Adressen und Versionsnummer für Ihre Bereitstellung einfach in der CDS for Apps-Webanwendung finden, indem Sie zu **Einstellungen > Anpassung > Entwicklerressourcen** navigieren  
  
### <a name="cds-for-apps-discovery-services"></a>CDS für App-Suchdienste  

Die Dienstbasisadresse des globalen Ermittlungsdiensts ist: `https://globaldisco.crm.dynamics.com/`. Dies führt als Ergebnis zur Serviceadresse von `https://globaldisco.crm.dynamics.com/api/discovery/`.  
  
<!-- TODO:
The service base address of the Discovery service for a datacenter is : `https://disco.crm[N].dynamics.com/`. This results in the Discovery service address of `https://disco.crm[N].dynamics.com/api/discovery/`. Each datacenter has an N number associated with it. For a complete list of available CDS for Apps datacenters, and their N numbers,  see [Download endpoints using Developer resources page](../developer-resources-page.md).   -->
  
## <a name="using-the-discovery-service"></a>Verwenden des Suchdiensts  

Ein Entitätssatz mit der Bezeichnung `Instances` wird zum Abrufen von Instanzinformationen verwendet. Sie können `$select` und `$filter` mit der Instanzentität verwenden, die für das Filtern der zurückgegebenen Daten festgelegt wurde. Sie können auch mithilfe `$metadata` das Metadatendokument des Services abrufen.  
  
### <a name="authentication"></a>Authentifizierung

CDS for Apps-Web-API-Instanzen des Ermittlungsdiensts benötigen die Authentifizierung mit OAuth-Zugriffstokens. Lokale oder IFD-Instanzen der Ermittlungs-Web-API übernehmen das Authentifizierungsmodell ihrer Bereitstellung. Dabei unterstützen sie entweder die Integrierte Windows-Authentifizierung (IWA) oder OAuth-Tokens von einem vertrauenswürdigen Tokenanbieter. Webanwendungssitzungs-Authentifizierung wird nicht unterstützt.  
  
Wenn der Ermittlungsdienst für die OAuth-Authentifizierung konfiguriert ist, löst eine Anforderung, die an die Service-Web-API ohne einen Zugriffstoken gesendet wird, eine Trägerabfrage mit der Autorität des "allgemeinen" Endpunkts und der Ressourcenkennung des Service aus.  Wenn in ähnlicher Weise eine lokale Bereitstellung für OAuth konfiguriert wird, gibt eine Trägerabfrage die lokale Autoritäts-URL sowie die Ressourcenkennung des Service zurück.  
  
### <a name="web-api-versioning"></a>Web-API-Versionsverwaltung

Versionsverwaltung des Ermittlungsdiensts für ein Datencenter oder lokal/IFD wird unterstützt und ist konsistent mit Versionsnummerierung, wie sie vom Organisationsdienst verwendet wird . Der globale Ermittlungsdienst von CDS for Apps ist jedoch nicht an die Versionsnummer der CDS for Apps-Bereitstellung gebunden. Stattdessen verwendet der globale Service seine eigene Versionsnummerierung. Zum jetzigen Zeitpunkt befindet sich der globalen Suchdienst von CDS for Apps in der Version 1.0 (v1.0). Beispiel:  
  
```http  
GET https://globaldisco.crm.dynamics.com/api/discovery/v1.0/Instances(UniqueName='myorg')  
```  
  
### <a name="cors-support"></a>CORS-Support

Die Ermittlungsdienst-Web-API unterstützt den CORS-Standard für den ursprungsübergreifenden Zugriff, wie das für die Web-API zutrifft.  Für weitere Informationen zu CORS-Support siehe [Verwenden von OAuth mit Cross-Origin Resource Sharing, um eine Single Page-Anwendung zu verbinden](../oauth-cross-origin-resource-sharing-connect-single-page-application.md)  
  
### <a name="examples"></a>Beispiele  
  
-   Rufen Sie die Details einer bestimmten Instanz ab. Wenn Sie die GUID auslassen, werden alle Instanzen zurückgegeben, auf die der authentifizierte Benutzer Zugriff hat.  
  
    ```http  
    GET https://disco.crm.dynamics.com/api/discovery/v8.1/Instances(<guid>)  
    GET https://dev.crm.external.contoso.com/api/discovery/v8.1/Instances(<guid>)  
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
    GET https://disco.crm.dynamics.com/api/discovery/v8.1/Instances(UniqueName='myorg')/Id/$value  
    ```

<!-- TODO: Add a see also section -->