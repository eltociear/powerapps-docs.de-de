---
title: Verwenden von OAuth 2.0, um den Flow mit IHrem Portal zu gewährleisten| MicrosoftDocs
description: Erfahren Sie, wie Sie clientseitige Aufrufe an externe APIs durchführen und diese mit Hilfe des Flows zur implizierten OAuth-Genehmigung in Ihrem Portal sichern können.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 38a1ac18a5c978c7b39d6dee85afcb9adf334534
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "2755814"
---
# <a name="use-oauth-20-implicit-grant-flow-within-your-portal"></a>Verwenden des Flows zur implizierten OAuth 2.0-Genehmigung innerhalb des Portals 

Mit dieser Funktion können Kunden clientseitige Aufrufe von externen APIs durchführen und sichern, indem sie den Flow zur implizierten OAuth-Genehmigung verwenden. Er bietet einen Endpunkt, um sichere Zugriffstoken zu erhalten, die die Benutzeridentitätsinformationen enthalten, die von externen APIs für die Autorisierung gemäß des Flows zur implizierten OAuth 2.0-Genehmigung verwendet werden müssen. Die Identitätsinformationen eines angemeldeten Benutzers werden in eine sichere Weise an externe AJAX-Aufrufe übergeben. Dieses Vorgehen hilft nicht nur Entwicklern, den Authentifizierungskontext zu übergeben, sondern hilft auch Benutzern, ihre APIs mit dieser Funktion zu sichern.

Der Flows zur implizierten OAuth 2.0-Genehmigung unterstützt Endpunkte, die ein Client aufrufen kann, um ein ID-Token abzurufen. Zwei Endpunkte werden zu diesem Zweck verwendet: [authorize](#authorize-endpoint-details) und [token](#token-endpoint-details).

## <a name="authorize-endpoint-details"></a>Details zum authorize-Endpunkt 

Die URL für den authorize-Endpunkt: `<portal_url>/_services/auth/authorize`. Der authorize-Endpunkt unterstützt die folgenden Parameter:

| Parameter   | Erforderlich? | Beschreibung                             |
|---------------|-----------|---------------------------------------|
| client_id      | Ja       | Eine Zeichenfolge, die bei einem Aufruf des authorize-Endpunkts übergeben wird. Sie müssen sicherstellen, dass die Client-ID [beim Portal registriert ist](#register-client-id-for-implicit-grant-flow). Andernfalls wird ein Fehler angezeigt. Die Client-ID wird in den Berechtigungen des Token als `aud` und im Parameter als `appid` hinzugefügt und kann von Clients verwendet werden, um zu überprüfen, ob das Token für ihre App zurückgesendet wird.<br>Die maximale Länge beträgt 36 Zeichen. Nur alphanumerische Zeichen und Bindestriche werden unterstützt. |
| redirect_uri      | Ja       | URL des Portals, auf dem Authentifizierungsantworten gesendet und empfangen werden können. Sie muss für die jeweilige `client_id` registriert werden, die im Aufruf verwendet wird, und sollte genau denselben registrierten Wert haben.            |
| state       | Nein        | Ein in der Anforderung enthaltener Wert, der auch in der Tokenantwort zurückgegeben wird. Dies kann eine Zeichenfolge jeden Inhalts sein, den Sie verwenden möchten. Normalerweise wird ein nach dem Zufallsprinzip generierter eindeutiger Wert verwendet, um Cross-Site Request Forgery-Angriffe zu vermeiden.<br>Die maximale Länge beträgt 20 Zeichen.              |
| nonce   | Nein        | Ein Zeichenfolgenwert, der vom Client gesendet werden, der im resultierenden ID-Token als Berechtigung enthalten ist. Der Client kann dann diesen Wert überprüfen, um Token-Replay-Angriffe zu verringern. Die maximale Länge beträgt 20 Zeichen.      |
| response_type         | Nein        | Dieser Parameter unterstützt nur `token` als Wert. Dies ermöglicht der App, sofort ein Zugriffstoken vom authorize-Endpunkt zu erhalten, ohne eine zweiten Anforderung an den authorize-Endpunkt zu senden.                               |
|||

### <a name="successful-response"></a>Erfolgreiche Antwort

Der authorize-Endpunkt gibt die folgenden Werte in der Antwort-URL als Fragment zurück:

- **token**: Wird als JSON-Web-Token (JWT) zurückgegeben, das durch den privaten Schlüssel des Portals digital signiert ist.
- **state**: Wenn ein state-Parameter in der Anforderung enthalten ist, sollte derselbe Wert in der Antwort enthalten sein. Die App sollte sicherstellen, dass die Statuswerte in der Anforderung und in der Antwort identisch sind.
- **expires_in**: Die Zeit, während der das Zugriffstoken gültig ist (in Sekunden).

Beispielsweise sieht eine erfolgreiche Reaktion wie folgt aus:

```
GET https://aadb2cplayground.azurewebsites.net/#token=eyJ0eXAiOiJKV1QiLCJhbGciOI1NisIng1dCI6Ik5HVEZ2ZEstZnl0aEV1Q&expires_in=3599&state=arbitrary_data_you_sent_earlier
```

### <a name="error-response"></a>Fehlerantwort

Der Fehler im authorize-Endpunkt wird als JSON-Dokument mit folgenden Werten zurückgegeben:

- **Fehler-ID**: Eindeutiger Bezeichner des Fehlers.
- **Fehlermeldung**: Eine spezifische Fehlermeldung, die Ihnen helfen kann, die Ursache des Authentifizierungsfehlers zu identifizieren.
- **Korrelations-ID**: Eine GUID, die für Debugzwecke verwendet wird. Wenn Sie die Diagnoseprotokollierung aktiviert haben, ist in den Serverfehlerfehlerprotokollen die Korrelations-ID vorhanden.
- **Zeitstempel**: Datum und Uhrzeit der Fehlergenerierung.

Die Fehlermeldung wird in der Standardsparche des angemeldeten Benutzers angezeigt. Wenn der Benutzer nicht angemeldet ist, wird die Anmeldeseite angezeigt, damit der Benutzer sich anmelden kann. Beispielsweise sieht eine Fehlerantwort wie folgt aus:

```
{"ErrorId": "PortalSTS0001", "ErrorMessage": "Client Id provided in the request is not a valid client Id registered for this portal. Please check the parameter and try again.", "Timestamp": "4/5/2019 10:02:11 AM", "CorrelationId": "7464eb01-71ab-44bc-93a1-f221479be847" }
```

## <a name="token-endpoint-details"></a>Tokenendpunktdetails

Sie können ein Token auch abrufen, indem Sie eine Anforderung an den Endpunkt `/token` vornehmen. Er unterscheidet sich vom Autorisierungsendpunkt wie folgt: Der Autorisierungsendpunkt verarbeitet die Tokenlogik in einer separaten Seite (redirect_uri), während der Tokenendpunkt die Tokenlogik auf derselben Seite verarbeitet. Die URL für den Tokenendpunkt: `<portal_url>/_services/auth/token`. Der Tokenendpunkt unterstützt die folgenden Parameter:

| Parameter   | Erforderlich? | Beschreibung                             |
|---------------|-----------|---------------------------------------|
| client_id      | Nein       | Eine Zeichenfolge, die bei einem Aufruf des authorize-Endpunkts übergeben wird. Sie müssen sicherstellen, dass die Client-ID [beim Portal registriert ist](#register-client-id-for-implicit-grant-flow). Andernfalls wird ein Fehler angezeigt. Die Client-ID wird in den Berechtigungen des Token als `aud` und im Parameter als `appid` hinzugefügt und kann von Clients verwendet werden, um zu überprüfen, ob das Token für ihre App zurückgesendet wird.<br>Die maximale Länge beträgt 36 Zeichen. Nur alphanumerische Zeichen und Bindestriche werden unterstützt. |
| redirect_uri      | Nein       | URL des Portals, auf dem Authentifizierungsantworten gesendet und empfangen werden können. Sie muss für die jeweilige `client_id` registriert werden, die im Aufruf verwendet wird, und sollte genau denselben registrierten Wert haben.            |
| state       | Nein        | Ein in der Anforderung enthaltener Wert, der auch in der Tokenantwort zurückgegeben wird. Dies kann eine Zeichenfolge jeden Inhalts sein, den Sie verwenden möchten. Normalerweise wird ein nach dem Zufallsprinzip generierter eindeutiger Wert verwendet, um Cross-Site Request Forgery-Angriffe zu vermeiden.<br>Die maximale Länge beträgt 20 Zeichen.              |
| nonce   | Nein        | Ein Zeichenfolgenwert, der vom Client gesendet werden, der im resultierenden ID-Token als Berechtigung enthalten ist. Der Client kann dann diesen Wert überprüfen, um Token-Replay-Angriffe zu verringern. Die maximale Länge beträgt 20 Zeichen.      |
| response_type         | Nein        | Dieser Parameter unterstützt nur `token` als Wert. Dies ermöglicht der App, sofort ein Zugriffstoken vom authorize-Endpunkt zu erhalten, ohne eine zweiten Anforderung an den authorize-Endpunkt zu senden.                               |
|||

> [!NOTE]
> Auch wenn die Parameter `client_id`, `redirect_uri`, `state` und `nonce` optional sind, wird empfohlen, sie zu verwenden, um sicherzustellen, dass Ihre Integrationen sicher sind.

### <a name="successful-response"></a>Erfolgreiche Antwort

Der Tokenendpunkt gibt „state“ und „expires_in“ als Antwortheader und das Token im Formulartextkörper zurück.

### <a name="error-response"></a>Fehlerantwort

Der Fehler im Tokenendpunkt wird als JSON-Dokument mit folgenden Werten zurückgegeben:

- **Fehler-ID**: Eindeutiger Bezeichner des Fehlers.
- **Fehlermeldung**: Eine spezifische Fehlermeldung, die Ihnen helfen kann, die Ursache des Authentifizierungsfehlers zu identifizieren.
- **Korrelations-ID**: Eine GUID, die für Debugzwecke verwendet wird. Wenn Sie die Diagnoseprotokollierung aktiviert haben, ist in den Serverfehlerfehlerprotokollen die Korrelations-ID vorhanden.
- **Zeitstempel**: Datum und Uhrzeit der Fehlergenerierung.

Die Fehlermeldung wird in der Standardsparche des angemeldeten Benutzers angezeigt. Wenn der Benutzer nicht angemeldet ist, wird die Anmeldeseite angezeigt, damit der Benutzer sich anmelden kann. Beispielsweise sieht eine Fehlerantwort wie folgt aus:

```
{"ErrorId": "PortalSTS0001", "ErrorMessage": "Client Id provided in the request is not a valid client Id registered for this portal. Please check the parameter and try again.", "Timestamp": "4/5/2019 10:02:11 AM", "CorrelationId": "7464eb01-71ab-44bc-93a1-f221479be847" }
```

## <a name="validate-id-token"></a>Überprüfen des ID-Tokens

Nur ein ID-Token abzurufen reicht für die Benutzerauthentifizierung nicht aus. Sie müssen die Signatur des Tokens auch überprüfen und die Berechtigungen im Token basierend auf den Anforderungen der App verifizieren. Der öffentliche Tokenendpunkt bietet den öffentlichen Schlüssel des Portals, mit dem die Signatur des Tokens überprüft werden kann, die vom Portal bereitgestellt wird. Die URL für den öffentlichen Tokenendpunkt: `<portal_url>/_services/auth/publickey`.

## <a name="turn-implicit-grant-flow-on-or-off"></a>Flow zur implizierten Genehmigung aktivieren oder deaktivieren

Standardmäßig wird der Flow zur implizierten Genehmigung aktiviert. Wenn Sie den Flow zur implizierten Genehmigung deaktivieren möchten, müssen Sie den Wert der Siteeinstellung **Connector/ImplicitGrantFlowEnabled** auf **False** setzen.

Wenn diese Site-Einstellung im Portal nicht verfügbar ist, müssen Sie [eine neue Site-Einstellung](configure/configure-site-settings.md#manage-portal-site-settings) mit dem entsprechenden Wert erstellen.

## <a name="configure-token-validity"></a>Tokengültigkeit konfigurieren

Standardmäßig ist das Token für 15 Minuten gültig. Wenn die Gültigkeit des Tokens ändern möchten, müssen Sie den Wert der Site-Einstellung **ImplicitGrantFlow/TokenExpirationTime** auf den gewünschten Wert festlegen. Der Wert muss in Sekunden angegeben werden. Der maximale Wert 1 kann Stunde sein, und der minimale Wert muss 1 Minute sein. Wenn ein falscher Wert angegeben wird (z. B. alphanumerische Zeichen), wird der Standardwert 15 verwendet. Wenn Sie einen Wert über dem maximalen Wert oder unter dem minimalen Wert angeben, wird das Maximum bzw. der minimale Wert standardmäßig verwendet.

Wenn Sie beispielsweise die Tokengültigkeit auf 30 Minuten festlegen, legen Sie den Wert der Siteeinstellung **ImplicitGrantFlow/TokenExpirationTime** auf **1800** fest. Um die Tokengültigkeit auf 1 Stunde festzulegen, legen Sie den Wert der Siteeinstellung **ImplicitGrantFlow/TokenExpirationTime** auf **3600** fest.

## <a name="register-client-id-for-implicit-grant-flow"></a>Client-ID für Flow zur implizierten Genehmigung registrieren

Sie müssen die Client-ID mit dem Portal registrieren, für das dieser Flow zugelassen ist. Wenn Sie eine Client-ID registrieren möchen, müssen Sie die folgenden Siteeinstellungen erstellen:

|Website-Einstellung|Value|
|------|------|
|ImplicitGrantFlow/RegisteredClientId|Die gültigen Client-ID-Werte, die für dieses Portal zulässig sind. Die Werte muss durch ein Semikolon getrennt werden und können alphanumerische Zeichen und Bindestriche enthalten. Die maximale Länge beträgt 36 Zeichen.|
|ImplicitGrantFlow/{ClientId}/RedirectUri|Die gültigen URIs, die für eine bestimmte Client-ID zulässig sind. Die Werte müssen durch ein Semikolon getrennt werden. Die bereitgestellte URL muss eine gültige Webseite des Portals sein.|
|||

## <a name="sample-code"></a>Beispielcode

Sie können den folgenden Beispielcode verwenden, um mit der Verwendung der implizierten OAuth 2.0-Genehmigung mit PowerApps-Portal-APIs zu beginnen.

### <a name="use-portal-oauth-token-with-an-external-web-api"></a>Verwenden Sie das Portal-OAuth-Token für externe Web API

Dieses Beispiel ist ein ASP.NET-basiertes Projekt und dient zur Validierung des von PowerApps-Portalen ausgegebenen ID-Tokens. Das vollständige Beispiel finden Sie hier: [Verwenden Sie Portal-OAuth-Token für externe Web API](https://github.com/microsoft/PowerApps-Samples/tree/master/portals/ExternalWebApiConsumingPortalOAuthTokenSample).

### <a name="authorize-endpoint-sample"></a>Endpunkt-Muster autorisieren

Dieses Beispiel veranschaulicht, wie Endpunktrücksendungen das ID-Token als Fragment in der URL zurückgibt. Es deckt auch die Statusprüfung, die in der impliziten Erteilung unterstützt wird. Das Beispiel finden Sie hier:[Autorisieren Sie Endpunktbeispiel](https://github.com/microsoft/PowerApps-Samples/blob/master/portals/AuthorizeEndpoint.js).

### <a name="token-endpoint-sample"></a>Token-Endpunktbeispiele

Dieses Beispiel zeigt, wie Sie die Funktion getAuthenticationToken verwenden können, um ein ID-Token über den Token-Endpunkt in PowerApps-Portalen abzurufen. Das Beispiel finden Sie hier: [Token-Endpunktbeispiel](https://github.com/microsoft/PowerApps-Samples/blob/master/portals/TokenEndpoint.js).
