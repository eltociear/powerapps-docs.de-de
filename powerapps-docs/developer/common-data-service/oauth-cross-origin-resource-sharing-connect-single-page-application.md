---
title: Verwenden von OAuth mit Cross-Origin Resource Sharing zum Verbinden einer Single Page-Anwendung (Common Data Service für Apps)| Microsoft Docs
description: 'Erfahren Sie, wie Sie OAuth mit Cross-Origin Resource Sharing verwenden, um eine Single Page-Anwendung mit zu verbinden'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
  - Dynamics 365 (online)
ms.assetid: oauth-cross-origin-resource-sharing-connect-single-page-application
caps.latest.revision: 11
author: paulliew
ms.author: jdaly
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
<!-- https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/oauth-cross-origin-resource-sharing-connect-single-page-application 

-->
# <a name="use-oauth-with-cross-origin-resource-sharing-to-connect-a-single-page-application"></a>Verwenden von OAuth mit Cross-Origin Resource Sharing, um eine Single Page-Anwendung zu verbinden

Sie können eine Single Page Apps (SPAs) erstellen, die JavaScript verwendet, um mit Common Data Service für Apps-Daten zu arbeiten. Um dies zu ermöglichen, wird Cross-Origin Resource Sharing (CORS) aktiviert, so das SPAs die Browsereinschränkungen, die normalerweise Anforderungen über Domänengrenzen hinweg beschränken, umgehen können.  
  
> [!NOTE]
>  Die CORS-Unterstützung wird nur bei Verwendung der Web-API bereitgestellt. Sie können den Organisationsservice oder den veralteten Organisationsdatendienst nicht verwendet.  
  
<a name="bkmk_Spas_and_same_origin_policy"></a> 
  
## <a name="spas-and-same-origin-policy"></a>SPAs und die Same-Origin-Richtlinie  

SPAs hängen von der extensiven Nutzung von clientseitigem JavaScript ab, um eine einzige dynamische Seite zu erstellen, die keine neue Seiten laden muss. Stattdessen nutzen Sie XMLHTTPRequests, um Daten sowie andere Ressourcen vom Server anzuzeigen. SPAs funktionieren gut, wenn die Daten und die Ressource in der gleichen Domäne wie die Anwendung sind. Um den Zugriff auf Daten und Ressourcen in anderen Domänen zu schützen, setzen alle modernen Browser eine Same-Origin-Richtlinie durch. Diese verhindert, dass Daten von Websites in einer anderen Domäne verwendet werden. CORS bietet eine Möglichkeit, Zugriff auf Ressourcen einer anderen Domäne zu erhalten. Eine SPA für den Zugriff auf CDS für Apps-Daten ohne CORS zu erstellen ist keine brauchbare Option.  
  
<a name="bkmk_use_cors"></a>

## <a name="use-cors-with-common-data-service-for-apps"></a>Verwenden von CORS mit Common Data Service für Apps 
 
Die [Cross-Origin Resource Sharing-Spezifikation](http://www.w3.org/TR/cors/) stellt eine genaue Beschreibung der Implementierung und Nutzung von CORS bereit. Sie beschreibt die verschiedenen Header und Preflight-Anforderungen, die Sie für CORS benötigen. Die guten Nachricht ist, dass Sie kein Experte in CORS sein müssen, um es mit CDS für Apps zu nutzen. Der serverseitige Teil wurde schon für Sie erledigt. Sie müssen nur noch wissen, wie Sie ihn nutzen.  Sie müssen nicht die alle internen Arbeitsweise von CORS verstehen, um es mit CDS für Apps zu nutzen. Stattdessen können Sie die [Azure Active Directory Authentication Library für JavaScript](https://github.com/AzureAD/azure-activedirectory-library-for-js) (adal.js) verwenden. Sie kümmert sich um die meisten Dinge von CORS. Da CDS für Apps über Azure Active Directory authentifiziert werden, stellt ADAL.js die unterstützte Methode für die Authentifizierung von SPA-Benutzern dar.  
  
<a name="bkmk_how_adaljs_works"></a>

## <a name="how-adaljs-works"></a>So arbeitet adal.js

Die Kernbibliothek ist `adal.js`. Sie können auf minimierte Version dieser Bibliothek unter [https://secure.aadcdn.microsoftonline-p.com/lib/1.0.0/js/adal.min.js](https://secure.aadcdn.microsoftonline-p.com/lib/1.0.0/js/adal.min.js) zugreifen. Das Github- Projekt und die Dokumentation finden Sie unter [https://github.com/AzureAD/azure-activedirectory-library-for-js](https://github.com/AzureAD/azure-activedirectory-library-for-js).  
  
Die adal.js-Bibliothek enthält die Low-Level-Funktionen zur Authentifizierung über OAuth2. Adal.js ist so konzipiert, dass es mit anderen Frameworks verwendet werden kann. Es gibt z. B. eine `adal-angular.js`-Bibliothek, die dazu konzipiert ist, mit dem Angular-Framework verwendet zu werden. Sie arbeiten mit dieser Bibliothek, indem Sie bestimmte Konfigurationseigenschaften festlegen und dann warten, bis ein Ereignis eintritt, dass den Interaktionsfluss startet. Dies kann die z. B. der Aufruf der `login`-Funktion sein, oder, wenn die Anwendung Routingfunktionen hat, kann die Authentifizierung über die Konfiguration des Controllers für die Route gestartet werden.  
  
Wenn eine Authentifizierung erforderlich ist, wird der Benutzer auf die Anmeldeseite weitergeleitet. Dort kann er Anmeldeinformationen eingeben. Nach der erfolgreichen Authentifizierung wird er mit Token-Informationen als Fragment (über `#`) der URL zurück zur aufrufenden Seite geleitet. Dies ermöglicht der SPA das Abrufen des Tokens und das lokale oder sitzungsgebundene Speichern im Browser. Dies bedeutet, dass die gesamte Seite nach der Authentifizierung neu geladen wird. Dieses Mal stehen jedoch Informationen zum autorisierten Benutzer zur Verfügung, und die Anwendung kann den Vorgang fortsetzen, um die CDS für Apps-Web-API oder andere Ressourcen aufzurufen.  
  
Beim Aufrufen der CDS für Apps-Web-API Sie den Token-Wert in einen Anmeldungs-Header mit Ihrem XMLHTPPRequest einbinden. Da Tokens Ablaufdaten haben sollten Sie dafür sorgen, dass es nicht abläuft, während der Benutzer die SPA verwendet. Beachten Sie, dass die Eingabe neuer Anmeldeinformationen erfordert, dass der gesamte Inhalt der SPA-Seite an die Anmeldeseite übertragen wird. Dadurch würde eine sehr schlechte Benutzerfreundlichkeit zur Folge haben, wenn es geschehen würde, während Benutzern gerade aktiv ist. Um dieses zu vermeiden, verpacken Sie die Web-API-Aufrufe in einer `acquireToken`-Funktion, so dass Sie die Gültigkeit des Tokens ggf. überprüfen und es bei Bedarf ohne Wechsel zu Anmeldeseite aktualisieren können.  
  
<a name="bkmk_preparing_to_use_adaljs"></a>

## <a name="preparing-to-use-adaljs-with-a-spa"></a>Vorbereiten der Nutzung von ADAL.js mit einer SPA

 Um die SPA für adal.js zu konfigurieren müssen Sie folgendes durchführen:  
  
1.  Registrieren Sie die Anwendung beim Azure Active Directory-Mandaten  
2.  Exportieren Sie das registrierte Anwendungsmanifest und bearbeiten Sie dieses, um OAuth2 Implicit Flow zuzulassen. Importieren Sie anschließend die JSON-Datei zurück in die Anwendungsregistrierung.  
3.  Legen Sie Konfigurationsvariablen in der SPA mit Informationen aus dieser Registrierung fest.  
     Sie müssen die folgenden einbeziehen:  
  
    -   Die URL für die CDS für Apps-Organisation  
    -   Der Name des Active Directory-Mandanten, den Ihrer Organisation zur Authentifizierung nutzt.  
    -   Die Client-ID, die Sie erhalten, wenn Sie die Anwendung registrieren  
    -   Die URL, über die die SPA während der Entwicklung bereitgestellt oder debugged wird  


 Die Serie erforderlicher Schritte wird beschrieben in [Exemplarische Vorgehensweise: SPA-Anwendung mit adal.js registrieren und konfigurieren](walkthrough-registering-configuring-simplespa-application-adal-js.md).  
  
### <a name="see-also"></a>Siehe auch

[OAuth verwenden, um eine Verbindung mit CDS für Apps-Webdiensten herzustellen](connect-web-services-using-oauth.md)   


