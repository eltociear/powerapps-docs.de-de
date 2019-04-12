---
title: Erstellen von Webanwendungen mit Server-zu-Server (S2S) Authentifizierung (Common Data Service) | Microsoft Docs
description: 'Verwenden Sie Server-zu-Server (S2S) Authentifizierung, um sicher und nahtlos mit Common Data Service mit unseren Webanwendungen und Services zu kommunizieren. Die S2S-Authentifizierung ist die gängige Methode, mit der auf Microsoft AppSource registrierte Anwendungen auf die Common Data Service-Daten ihrer Abonnenten zugreifen.'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: paulliew
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="build-web-applications-using-server-to-server-s2s-authentication"></a>Erstellen von Webanwendungen mit Server-to-Server-Authentifizierung (S2S)

Verwenden Sie Server-zu-Server (S2S) Authentifizierung, um sicher und nahtlos mit Common Data Service mit unseren Webanwendungen und Services zu kommunizieren. Die S2S-Authentifizierung ist die gängige Methode, mit der auf Microsoft AppSource registrierte Anwendungen auf die Common Data Service-Daten ihrer Abonnenten zugreifen.  

 Die S2S-Authentifizierung bedeutet, dass Sie keine bezahlte PowerApps-Benutzerlizenz für die Verbindung mit den Common Data Service-Umgebungen benötigen. Es gibt keine Lizenzgebühr für das spezielle *Anwendungsbenutzer*-Konto, das Sie bei der S2S-Authentifizierung verwenden. Mit der S2S-Authentifizierung wird ein spezielles nicht lizenziertes -Anwendungsbenutzerkonto erstellt, das Informationen zu in Azure Active Directory (Azure AD) registrierten Anwendung umfasst . Anstelle der Benutzeranmeldeinformationen, wird die Anwendung basierend auf einem Serviceprinzipal authentifiziert, der durch einen Azure AD Objekt-ID-Wert identifiziert wird, der im Anwendungs-Benutzerdatensatz gespeichert ist. Der Anwendungsbenutzer wird einer benutzerdefinierten Sicherheitsrolle zugeordnet, die Arten von Daten und Vorgängen steuert, die die Anwendung ausführen kann.  

 Alle von Ihrer Anwendung oder dem Dienst mithilfe von S2S ausgeführten Vorgänge werden als Anwendungsbenutzer ausgeführt, statt als der Benutzer, der die Anwendung nutzt. Wenn die Anwendung Datenvorgänge im Auftrag eines bestimmten Benutzers ausführen soll (z. B. dem, der mit der Anwendung interagiert), können Sie Identitätswechsel anwenden, wenn die benutzerdefinierte Sicherheitsrolle auf den Anwendungsserviceprincipal angewendet wurde, der die erforderlichen Berechtigungen besitzt. Weitere Informationen: [Annehmen der Identität eines anderen Benutzers](impersonate-another-user.md)  

 Eine Webanwendung oder ein Service, der die S2S-Authentifizierung verwendet, ist für die Steuerung des Zugriffs auf die Daten verantwortlich, auf die er Zugriff besitzt. Dies wird in der Regel mit einem OpenID Connect-Anbieter durchgeführt. Weitere Informationen: <http://openid.net/connect/>.  

## <a name="server-to-server-authentication-scenarios"></a>Server-to-Server-Authentifizierungsszenarios  
 Es gibt zwei Seznarios, bei denen die S2S-Authentifizierung anwendet werden kann.  


|   Szenario    |   Beschreibung  |
|---------------|---------------|
| Mehrere Instanzen  | Dies ist das gebräuchlichste Szenario und das, das für über Microsoft AppSource verteilte Apps verwendet wird.<br /><br /> Jeder Common Data Service-Mandant ist einem Azure AD-Mandant zugeordnet. Ihre Webanwendung oder der Dienst ist mit Ihrem Azure AD Mandant registriert.<br /><br /> In diesem Szenario kann jeder Common Data Service-Mandant Ihre mögliche mehrinstanzenfähige Anwendung nutzen, nachdem sie eine Zustimmung für den Zugriff auf den Mandaten erhalten hat.                                                           |
| Einzelne Instanz | Dieses Szenario gilt typischerweise für Common Data Service-Umgebungen, die Apps für ihren eigenen Mandanten entwickeln wollen und nicht beabsichtigen, sie auf andere [Common Data Service-Umgebungen zu verteilen.<br /><br /> Eine Firma kann eine Webanwendung oder einen Service erstellen, um alle Common Data Service-Umgebungen für ihren Mandanten zu verbinden.<br /><br /> In diesem Szenario kann sich die Webanwendung oder der Dienst nur mit Common Data Service-Umgebungen in über denselben Azure AD-Mandanten verbinden. |

 Beide Szenarien nutzen gemeinsame Elemente. Es gibt aber einige Unterschiede. Da Mehrfachinstanzen das gebräuchlichste Szenario sind, beschreibt der Inhalt von [Verwenden der Mehrfachinstanzen-Server-zu-Server-Authentifizierung](use-multi-tenant-server-server-authentication.md), wie Sie S2S in diesem Szenario verwenden können, einschließlich Notizen für Abweichungen bei der Einzelinstanzkonfiguration. 

[Verwenden der Mehrfachinstanzen-Server-zu-Server-Authentifizierung](use-single-tenant-server-server-authentication.md) bietet eine Übersicht über dieses Szenario und bezieht sich auf die Prozeduren, beschrieben im Inhalt der Mehrfachinstanz-S2S-Authentifizierung.  

### <a name="see-also"></a>Siehe auch  
  
[Verwenden Sie mehrinstanzenfähige Server-zu-Server-Authentifizierung](use-multi-tenant-server-server-authentication.md)<br/> 
[Verwenden der Einzel-Mandanten-Server-zu-Server-Authentifizierung](use-single-tenant-server-server-authentication.md)   
