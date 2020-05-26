---
title: Annehmen der Identität eines anderen Benutzers (Common Data Service) | Microsoft-Dokumentation
description: Mit Hilfe eines Identitätswechsels können Sie die Geschäftslogik im Auftrag eines anderen Common Data Service-Benutzers ausführen, um eine gewünschte Funktion oder einen Service mit der entsprechenden rollen- und objektbasierten Sicherheit dieses imitierten Benutzers bereitzustellen.
ms.custom: ''
ms.date: 04/07/2020
ms.reviewer: pehecke
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: bc5f6ee0e852985213365ed54f118b0ce72cd1ce
ms.sourcegitcommit: 4a88daac42180283314f6bedee3d6810fd5a6c25
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/21/2020
ms.locfileid: "3275758"
---
# <a name="impersonate-another-user"></a>Annehmen der Identität eines anderen Benutzers

Mit Hilfe eines Identitätswechsels können Sie die Geschäftslogik im Auftrag eines anderen Common Data Service-Benutzers ausführen, um eine gewünschte Funktion oder einen Service mit der entsprechenden rollen- und objektbasierten Sicherheit dieses imitierten Benutzers bereitzustellen. 

Dies ist erforderlich, da die Common Data Service-Webdienste von verschiedenen Clients und Services im Auftrag eines Common Data Service-Benutzers aufgerufen werden können.

Identitätswechsel benötigt zwei unterschiedliche Benutzerkonten: 

|Identitätswechsler|Vertretener Benutzer|
|--|--|
|Benutzerkonto, das verwendet wird, wenn Code ausgeführt wird|Benutzerkonto, dass die Aufgabe im Auftrag ausgeführt wird.|

## <a name="required-privileges"></a>Erforderliche Berechtigungen

Der *Identitätenwechsler* erfordert das Recht **Vorgänge im Namen anderer Benutzer ausführen** (`prvActOnBehalfOfAnotherUser`), die in der Sicherheitsrolle **Delegieren** enthalten ist oder für alle Sicherheitsrollen aktiviert werden kann.

> [!NOTE]
> Beachten Sie, dass Benutzern mehr als einer Sicherheitsrolle zugeordnet werden können. Zuweisen einer Sicherheitsrolle **Stellvertretung** zu einem Benutzer können das `prvActOnBehalfOfAnotherUser` Recht sowie die Rechte aus allen anderen Sicherheitsrollen dem Benutzerkonto zugeordnet werden.

Die aktuelle Gruppe von Rechten, die verwendet wird, um Daten zu ändern, ist die Schnittmenge der Rechte, die der *Identitätsübernehmer* besitzt mit jeer des *Identitätennbenuzers*. 

In anderen Worten der *Identitätenübernehmer* kann *nur dann etwas tun, wenn* der *Identitätenübernehmer* und der *Identitätenbenutzer* über die dazu erforderlichen Rechte verfügen.

## <a name="impersonation-with-server-to-server-authentication"></a>Identitätenwechsel mit Server-zu-Server-Authentifizierung

Wenn Sie eine Webclient-Anwendung erstellen, die ein Benutzerkonto erfordert, das im Auftrag eines abonnierten Benutzers reagieren kann, können Sie das spezielle *Anwendungsbenutzer*-Konto nutzen, sodass Sie keine bezahlte Common Data Service-Benutzerlizenz verwenden müssen.

Weitere Informationen finden Sie unter: [Webanwendungen mit der Server-zu-Server-(S2S)-Authentifizierung erstellen.](build-web-applications-server-server-s2s-authentication.md).

## <a name="impersonate-another-user-using-the-web-api"></a>Annehmen eines anderen Benutzerkontos mit Web API

Um einen Benutzer zu imitieren, fügen Sie einen Anforderungskopf namens `CallerObjectId` mit einem GUID-Wert hinzu, der der Objekt-ID Azure Active Directory (AAD) des imitierten Benutzers entspricht, bevor Sie die Anforderung an den Webdienst senden. Die AAD-Objekt-ID des Benutzers ist im Verzeichnis [SystemUser.AzureActiveDirectoryObjectId](reference/entities/systemuser.md#BKMK_AzureActiveDirectoryObjectId) enthalten.

Weitere Informationen:[Annehmen eines anderen Benutzerkontos mit Web API](webapi/impersonate-another-user-web-api.md).


## <a name="impersonate-another-user-using-the-organization-service"></a>Annehmen eines anderen Benutzerkontos mit dem Unternehmensdienst

Zum Übernehmen der Identität von einem anderen Benutzer, legen Sie die `CallerId` Eigenschaft auf den Guid-Wert von der Identität des Benutzers fest. Die folgenden Klassen, die <xref:Microsoft.Xrm.Sdk.IOrganizationService> implementieren.  umfassen diese Eigenschaft.

- <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient>.<xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient.CallerId>
- <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceProxy>.<xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceProxy.CallerId>
- <xref:Microsoft.Xrm.Sdk.WebServiceClient.OrganizationWebProxyClient>.<xref:Microsoft.Xrm.Sdk.WebServiceClient.OrganizationWebProxyClient.CallerId>

## <a name="impersonate-another-user-using-plug-ins"></a>Übernehmen der Identität eines anderen Benutzers mithilfe von Plug-Ins

Sie können ein Plug-In registrieren, für das Sie einen Benutzer definieren können, für den der Vorgang verewendet werden soll. Innerhalb des Codes eines Plug-Ins können Sie diese Präferenzen überschreiben.
Weitere Informationen: [Annehmen der Identität eines Benutzers](impersonate-a-user.md)


### <a name="see-also"></a>Siehe auch

[Erstellen von Webanwendungen mit Server-to-Server-Authentifizierung (S2S)](build-web-applications-server-server-s2s-authentication.md)<br />
[Annehmen eines anderen Benutzerkontos mit Web API](webapi/impersonate-another-user-web-api.md)<br />
[Schreiben eines Plug-Ins](write-plug-in.md)
 