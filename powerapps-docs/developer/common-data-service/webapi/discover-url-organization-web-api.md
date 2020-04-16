---
title: Ermitteln Sie die URL für Ihre Organisation (Common Data Service) | Microsoft Docs
description: Verwenden Sie den Ermittlungsdienst, um die Organisationen (Instanzen) zu finden, zu denen der angemeldete Benutzer gehört
ms.custom: ''
ms.date: 1/16/2020
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
ms.reviewer: pehecke
manager: kvivek
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: bc68a5ae74c72f2dbc9a8240253574348d85a7cd
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155090"
---
# <a name="discover-the-url-for-your-organization"></a>Die URL für Ihre Organisation entdecken

[!INCLUDE [cc-discovery-service-description](../includes/cc-discovery-service-description.md)]

Wenn Sie mit der OData V4 RESTful-API auf den Discovery-Dienst zugreifen, können Sie der Dienstanforderung Standard `$filter` und `$select` Parameter hinzufügen, um die zurückgegebene Liste der Instance-Daten anzupassen.

> [!IMPORTANT]
> - Ab dem 2. März 2020 wird der *regionale* Suchdienst [veraltet sein](/power-platform/important-changes-coming#regional-discovery-service-is-deprecated). Anwendungen müssen den globalen Ermittlungsdienst verwenden, der in dieser Thema dokumentiert ist.  
> - Für Dynamics 365 US Government-Benutzer ist ein *globaler* Suchdienst Endpunkt für **GCC** und **GCC High** Benutzer verfügbar, und die URL unterscheidet sich von der regulären globalen Suchdienst-URL. Weitere Informationen: [Dynamics 365 Government-URLs](https://docs.microsoft.com/dynamics365/customer-engagement/admin/government/microsoft-dynamics-365-government#dynamics-365-us-government-urls).

  
## <a name="information-provided-by-the-discovery-service"></a>Informationen, die vom Ermittlungsdienst bereitgestellt werden 
 
Organisationsinformationen werden in der `Instance` Entität des Ermittlungsdiensts gespeichert.  Um die Art der Informationen anzuzeigen, die in dieser Entität enthalten sind, senden Sie eine HTTP GET-Anforderung zum Service für eine Ihrer Instanzen.  
  
```http  
GET https://globaldisco.crm.dynamics.com/api/discovery/v2.0/Instances(UniqueName='myorg')  
```  
  
Im oben genannten Beispiel wird der globale Ermittlungsdienst verwendet, um die Organisationsinformationen der Instanz mit einem eindeutigen Namen "myorg" abzurufen. Weitere Details zu dieser Anforderung werden später in diesem Thema ausführlicher dargelegt.  

### <a name="scope-of-the-returned-information"></a>Umfang der zurückgegebenen Informationen

Für den globalen Ermittlungsdienst gibt der Entitätssatz `Instances` den Entitätssatz zurück, auf den der Benutzer an allen geografischen Orten Zugriff hat, wenn keine Filter angewendet wurden.   Die zurückgegebenen Daten haben einen Umfang, wie unten beschrieben.  
  
-   Enthält alle Instanzen in der Handelscloud, wo der Benutzer bereitgestellt und aktiviert ist, außer dass Sovereign-Couds-Instanzen nicht zurückgegeben werden
-   Enthält nicht Instanzen, bei denen das Konto des Benutzers deaktiviert ist
-   Enthält keine Instanzen, bei denen Benutzer auf Basis einer Instanzsicherheitsgruppe gefiltert wurden
-   Umfasst nicht Instanzen, auf die der Benutzer Zugriff hat, da er ein stellvertretender Administrator ist
-   Wenn der aufrufende Benutzer Zugriff auf keine Instanzen hat, gibt die Antwort einfach eine leere Liste zurück

## <a name="how-to-access-the-discovery-service"></a>Zugreifen auf den Ermittlungsdienst

Im Allgemeinen hat die Web-API-Adresse vom Ermittlungsdienst das folgende Format: `<service base address>/api/discovery/`.  Sie können die Web-API-Adressen und Versionsnummer für Ihre Bereitstellung einfach in der Common Data Service Webanwendung finden, indem Sie zu **Einstellungen > Anpassung > Entwicklerressourcen** navigieren  
  
### <a name="common-data-service-discovery-services"></a>Common Data Service-Suchdienste  

Die Dienstbasisadresse des globalen Ermittlungsdiensts ist: `https://globaldisco.crm.dynamics.com/`. Dies führt als Ergebnis zur Serviceadresse von `https://globaldisco.crm.dynamics.com/api/discovery/`.  
  
## <a name="using-the-discovery-service"></a>Verwenden des Suchdiensts  

Ein Entitätssatz mit der Bezeichnung `Instances` wird zum Abrufen von Instanzinformationen verwendet. Sie können `$select` und `$filter` mit der Instanzentität verwenden, die für das Filtern der zurückgegebenen Daten festgelegt wurde. Sie können auch mithilfe `$metadata` das Metadatendokument des Services abrufen.  
  
### <a name="authentication"></a>Authentifizierung

Für den Zugriff auf den Ermittlungsdienst ist eine Authentifizierung mit einem Oauth Zugriffstoken erforderlich.

Wenn der Ermittlungsdienst für die OAuth-Authentifizierung konfiguriert ist, löst eine Anforderung, die an die Service-Web-API ohne einen Zugriffstoken gesendet wird, eine Trägerabfrage mit der Autorität des allgemeinen Endpunkts und der Ressourcenkennung des Service aus.

### <a name="cors-support"></a>CORS-Support

Der Ermittlungsdienst unterstützt den CORS-Standard für den ursprungsübergreifenden Zugriff. Für weitere Informationen zu CORS-Support siehe [Verwenden von OAuth mit Cross-Origin Resource Sharing, um eine Single Page-Anwendung zu verbinden](../oauth-cross-origin-resource-sharing-connect-single-page-application.md)  
  
### <a name="examples"></a>Beispiele  
  
-   Rufen Sie die Details einer bestimmten Instanz ab. Wenn Sie die GUID auslassen, werden alle Instanzen zurückgegeben, auf die der authentifizierte Benutzer Zugriff hat.  
  
    ```http      
    GET https://globaldisco.crm.dynamics.com/api/discovery/v2.0/Instances(<guid>)
    ```  
  
-   Sie können das UniqueName-Attribut als Alternativschlüssel verwenden.  
  
    ```http  
    GET https://globaldisco.crm.dynamics.com/api/discovery/v2.0/Instances(UniqueName='myorg')  
    ```  
  
-   Rufen Sie eine Liste verfügbarer Instanzen ab, die nach Produktionstyp gefiltert sind.  
  
    ```http  
    GET https://globaldisco.crm.dynamics.com/api/discovery/v2.0/Instances?$select=DisplayName,Description&$filter=Type+eq+0   
    ```  
  
## <a name="see-also"></a>Siehe auch

[Suchdienst Beispiel (C#)](samples/global-discovery-service-csharp.md)

