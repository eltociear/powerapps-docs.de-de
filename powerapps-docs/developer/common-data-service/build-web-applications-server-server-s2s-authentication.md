---
title: Erstellen von Webanwendungen mit Server-to-Server-Authentifizierung (Common Data Service) | Microsoft-Dokumentation
description: Verwenden Sie Server-zu-Server (S2S) Authentifizierung, um sicher und nahtlos mit Common Data Service mit unseren Webanwendungen und Services zu kommunizieren.. Die S2S-Authentifizierung ist der normale Weg, über den bei Microsoft AppSource registrierte Apps auf die Common Data Service-Daten der Abonnenten zugreifen.
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
ms.openlocfilehash: 0fc18f342257eaaa878107ae5b729c672c2f0433
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2019
ms.locfileid: "2861839"
---
# <a name="build-web-applications-using-server-to-server-s2s-authentication"></a>Erstellen von Webanwendungen mit Server-to-Server-Authentifizierung (S2S)

Verwenden Sie Server-zu-Server (S2S) Authentifizierung, um sicher und nahtlos mit Common Data Service mit unseren Webanwendungen und Services zu kommunizieren.. Die S2S-Authentifizierung ist der normale Weg, über den bei Microsoft AppSource registrierte Apps auf die Common Data Service-Daten der Abonnenten zugreifen.  

Die S2S-Authentifizierung bedeutet, dass Sie keine bezahlte Power Apps-Benutzerlizenz für die Verbindung mit den Common Data Service-Umgebungen benötigen. Es gibt keine Lizenzgebühr für das spezielle *Anwendungsbenutzer*-Konto, das Sie bei der S2S-Authentifizierung verwenden. Es gibt jedoch [Beschränkungen hinsichtlich der Anzahl der Anforderungen der Anwendungsbenutzer](https://docs.microsoft.com/power-platform/admin/api-request-limits-allocations#non-licensed-usersapplication-users), die ein Konto aufrufen kann. Mit der S2S-Authentifizierung wird ein spezielles nicht lizenziertes Anwendungsbenutzerkonto erstellt, das Informationen zur bei Azure Active Directory (Azure AD) registrierten Anwendung umfasst. Anstelle der Benutzeranmeldeinformationen wird die Anwendung basierend auf einem Dienstprinzipal authentifiziert, der durch einen Azure AD-Objekt-ID-Wert identifiziert wird, der im Benutzerdatensatz gespeichert ist. Der Anwendungsbenutzer wird einer benutzerdefinierten Sicherheitsrolle zugeordnet, die Arten von Daten und Vorgängen steuert, die die Anwendung ausführen kann.  

 Alle von Ihrer Anwendung oder dem Dienst mithilfe von S2S ausgeführten Vorgänge werden als Anwendungsbenutzer ausgeführt, statt als der Benutzer, der die Anwendung nutzt. Wenn die Anwendung Datenvorgänge im Auftrag eines bestimmten Benutzers ausführen soll (z. B. dem, der mit der Anwendung interagiert), können Sie Identitätswechsel anwenden, wenn die benutzerdefinierte Sicherheitsrolle auf den Anwendungsserviceprincipal angewendet wurde, der die erforderlichen Berechtigungen besitzt. Weitere Informationen: [Annehmen der Identität eines anderen Benutzers](impersonate-another-user.md)  

 Eine Webanwendung oder ein Service, der die S2S-Authentifizierung verwendet, ist für die Steuerung des Zugriffs auf die Daten verantwortlich, auf die er Zugriff besitzt. Dies wird in der Regel mit einem OpenID Connect-Anbieter durchgeführt. Weitere Informationen: <https://openid.net/connect/>.  

## <a name="server-to-server-authentication-scenarios"></a>Server-to-Server-Authentifizierungsszenarios  
 Es gibt zwei Seznarios, bei denen die S2S-Authentifizierung anwendet werden kann.  


|   Szenario    |   Beschreibung  |
|---------------|---------------|
| Mehrere Instanzen  | Dies ist das gebräuchlichste Szenario und das, das für über Microsoft AppSourceverteilte Apps verwendet wird.<br /><br /> Jeder Common Data Service-Mandant ist einem Azure AD Mandant zugeordnet. Ihre Webanwendung oder der Dienst ist mit Ihrem Azure AD Mandant registriert.<br /><br /> In diesem Szenario kann jeder Common Data Service-Mandant Ihre mögliche mehrinstanzenfähige Anwendung nutzen nachdem sie eine Zustimmung für den Zugriff auf den Mandaten erhalten hat.                                                           |
| Einzelne Instanz | Dieses Szenario gilt typischerweise für Common Data Service Umgebungen, die Apps für ihren eigenen Mandanten entwickeln wollen und nicht beabsichtigen, sie auf andere Common Data Service Umgebungen zu verteilen.<br /><br /> Eine Firma kann eine Webanwendung oder einen Service erstellen, um alle Common Data Service-Umgebungen für ihren Mandanten zu verbinden.<br /><br /> In diesem Szenario kann sich die Webanwendung oder der Dienst nur mit Common Data Service-Umgebungen über denselben Azure AD-Mandanten verbinden. |

 Beide Szenarien nutzen gemeinsame Elemente. Es gibt aber einige Unterschiede. Da Mehrfachinstanzen das gebräuchlichste Szenario sind, beschreibt der Inhalt von [Verwenden der Mehrfachinstanzen-Server-zu-Server-Authentifizierung](use-multi-tenant-server-server-authentication.md), wie Sie S2S in diesem Szenario verwenden können, einschließlich Notizen für Abweichungen bei der Einzelinstanzkonfiguration. 

[Verwenden der Mehrfachinstanzen-Server-zu-Server-Authentifizierung](use-single-tenant-server-server-authentication.md) bietet eine Übersicht über dieses Szenario und bezieht sich auf die Prozeduren, beschrieben im Inhalt der Mehrfachinstanz-S2S-Authentifizierung.  

### <a name="see-also"></a>Siehe auch  
  
[Verwenden Sie mehrinstanzenfähige Server-zu-Server-Authentifizierung](use-multi-tenant-server-server-authentication.md)<br/> 
[Verwenden der Einzel-Mandanten-Server-zu-Server-Authentifizierung](use-single-tenant-server-server-authentication.md)   
