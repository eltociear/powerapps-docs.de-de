---
title: Verwenden des impliziten OAuth 2,0-Zuweisungs Flusses innerhalb Ihres Portals | MicrosoftDocs
description: Erfahren Sie, wie Sie Client seitige Aufrufe externer APIs durchführen und diese mithilfe des impliziten OAuth-Berechtigungs Flusses im Portal sichern.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 06db149e5f86696ecffae38fe05e23198d72ecb5
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/11/2019
ms.locfileid: "72974504"
---
# <a name="use-oauth-20-implicit-grant-flow-within-your-portal"></a>Verwenden des impliziten OAuth 2,0-Zuweisungs Flusses innerhalb Ihres Portals 

Diese Funktion ermöglicht es einem Kunden, Client seitige Aufrufe externer APIs vorzunehmen und diese mithilfe des impliziten OAuth-Berechtigungs Flusses zu sichern. Es bietet einen Endpunkt zum Abrufen sicherer Zugriffs Token, die Benutzer Identitätsinformationen enthalten, die von externen APIs für die Autorisierung nach dem impliziten OAuth 2,0-Grant-Flow verwendet werden. Die Identitätsinformationen eines angemeldeten Benutzers werden auf sichere Weise an die externen AJAX-Aufrufe übermittelt. Dies hilft Entwicklern nicht nur, den Authentifizierungs Kontext zu übergeben, sondern auch Benutzern zu helfen, ihre APIs mithilfe dieses Mechanismus zu schützen.

Der implizite OAuth 2,0-Zuweisungs Fluss unterstützt Endpunkte, die ein Client zum Abrufen eines ID-Tokens abrufen kann. Zu diesem Zweck werden zwei Endpunkte verwendet: [autorisieren](#authorize-endpoint-details) und [Token](#token-endpoint-details).

## <a name="authorize-endpoint-details"></a>Endpunkt Details autorisieren 

Die URL für Autorisierungs Endpunkt lautet: `<portal_url>/_services/auth/authorize`. Der Autorisierungs Endpunkt unterstützt die folgenden Parameter:

| Parameter   | Erforderlich? | Beschreibung                             |
|---------------|-----------|---------------------------------------|
| client_id      | Ja       | Eine Zeichenfolge, die beim Ausführen eines Aufrufes an den Autorisierungs Endpunkt übermittelt wird. Sie müssen sicherstellen, dass die Client-ID im [Portal registriert](#register-client-id-for-implicit-grant-flow)ist. Andernfalls wird ein Fehler angezeigt. Die Client-ID wird in Ansprüchen im Token als `aud` und `appid` Parameter hinzugefügt und kann von Clients verwendet werden, um zu überprüfen, ob das zurückgegebene Token für Ihre APP verwendet wird.<br>Die maximale Länge beträgt 36 Zeichen. Nur alphanumerische Zeichen und Bindestriche werden unterstützt. |
| redirect_uri      | Ja       | Die URL des Portals, an die Authentifizierungs Antworten gesendet und empfangen werden können. Sie muss für die jeweilige `client_id` registriert werden, die im-Befehl verwendet wird, und sollte genau dem Wert entsprechen, der registriert ist.            |
| Land       | Nein        | Ein in der Anforderung enthaltener Wert, der auch in der tokenantwort zurückgegeben wird. Dabei kann es sich um eine Zeichenfolge von Inhalten handeln, die Sie verwenden möchten. Normalerweise wird ein zufällig generierter eindeutiger Wert verwendet, um Website übergreifende Anforderungs Fälschungs Angriffe zu verhindern.<br>Die maximale Länge beträgt 20 Zeichen.              |
| Nonce   | Nein        | Ein Zeichen folgen Wert, der vom Client gesendet wird, der im resultierenden ID-Token als Anspruch enthalten ist. Der Client kann diesen Wert dann überprüfen, um Token-Replay-Angriffe zu verringern. Die maximale Länge beträgt 20 Zeichen.      |
| response_type         | Nein        | Dieser Parameter unterstützt nur `token` als Wert. Dadurch kann Ihre APP sofort ein Zugriffs Token vom Autorisierungs Endpunkt empfangen, ohne dass eine zweite Anforderung an den Autorisierungs Endpunkt gesendet werden muss.                               |
|||

### <a name="successful-response"></a>Erfolgreiche Antwort

Der Autorisierungs Endpunkt gibt die folgenden Werte in der Antwort-URL als Fragment zurück:

- **Token**: das Token wird als JSON Web Token (JWT) zurückgegeben, das vom privaten Schlüssel des Portals digital signiert wurde.
- **State**: Wenn ein Status Parameter in der Anforderung enthalten ist, sollte der gleiche Wert in der Antwort angezeigt werden. Die APP sollte überprüfen, ob die Statuswerte in der Anforderung und in der Antwort identisch sind.
- **expires_in**: die Zeitspanne, für die das Zugriffs Token gültig ist (in Sekunden).

Eine erfolgreiche Antwort sieht z. b. wie folgt aus:

```
GET https://aadb2cplayground.azurewebsites.net/#token=eyJ0eXAiOiJKV1QiLCJhbGciOI1NisIng1dCI6Ik5HVEZ2ZEstZnl0aEV1Q&expires_in=3599&state=arbitrary_data_you_sent_earlier
```

### <a name="error-response"></a>Fehler Antwort

Der Fehler im Autorisierungs Endpunkt wird als JSON-Dokument mit den folgenden Werten zurückgegeben:

- **Fehler-ID**: eindeutiger Bezeichner des Fehlers.
- **Fehlermeldung**: eine spezifische Fehlermeldung, mit der Sie die Grundursache eines Authentifizierungsfehlers identifizieren können.
- **Korrelations-ID**: eine GUID, die zu Debugzwecken verwendet wird. Wenn Sie die Diagnoseprotokollierung aktiviert haben, ist die Korrelations-ID in den Server Fehlerprotokollen enthalten.
- **Timestamp**: Datum und Uhrzeit, zu der der Fehler generiert wird.

Die Fehlermeldung wird in der Standardsprache des angemeldeten Benutzers angezeigt. Wenn der Benutzer nicht angemeldet ist, wird die Anmeldeseite angezeigt, damit sich der Benutzer anmelden kann. Eine Fehler Antwort sieht z. b. wie folgt aus:

```
{"ErrorId": "PortalSTS0001", "ErrorMessage": "Client Id provided in the request is not a valid client Id registered for this portal. Please check the parameter and try again.", "Timestamp": "4/5/2019 10:02:11 AM", "CorrelationId": "7464eb01-71ab-44bc-93a1-f221479be847" }
```

## <a name="token-endpoint-details"></a>Details zum tokenendpunkt

Sie können auch ein Token erhalten, indem Sie eine Anforderung an den `/token`-Endpunkt senden. Dies unterscheidet sich vom Autorisierungs Endpunkt in der Art und Weise, wie der Autorisierungs Endpunkt die tokenlogik auf einer separaten Seite (redirect_uri) behandelt, während der tokenendpunkt die tokenlogik auf derselben Seite verarbeitet. Die URL für den tokenendpunkt lautet: `<portal_url>/_services/auth/token`. Der tokenendpunkt unterstützt die folgenden Parameter:

| Parameter   | Erforderlich? | Beschreibung                             |
|---------------|-----------|---------------------------------------|
| client_id      | Nein       | Eine Zeichenfolge, die beim Ausführen eines Aufrufes an den Autorisierungs Endpunkt übermittelt wird. Sie müssen sicherstellen, dass die Client-ID im [Portal registriert](#register-client-id-for-implicit-grant-flow)ist. Andernfalls wird ein Fehler angezeigt. Die Client-ID wird in Ansprüchen im Token als `aud` und `appid` Parameter hinzugefügt und kann von Clients verwendet werden, um zu überprüfen, ob das zurückgegebene Token für Ihre APP verwendet wird.<br>Die maximale Länge beträgt 36 Zeichen. Nur alphanumerische Zeichen und Bindestriche werden unterstützt. |
| redirect_uri      | Nein       | Die URL des Portals, an die Authentifizierungs Antworten gesendet und empfangen werden können. Sie muss für die jeweilige `client_id` registriert werden, die im-Befehl verwendet wird, und sollte genau dem Wert entsprechen, der registriert ist.            |
| Land       | Nein        | Ein in der Anforderung enthaltener Wert, der auch in der tokenantwort zurückgegeben wird. Dabei kann es sich um eine Zeichenfolge von Inhalten handeln, die Sie verwenden möchten. Normalerweise wird ein zufällig generierter eindeutiger Wert verwendet, um Website übergreifende Anforderungs Fälschungs Angriffe zu verhindern.<br>Die maximale Länge beträgt 20 Zeichen.              |
| Nonce   | Nein        | Ein Zeichen folgen Wert, der vom Client gesendet wird, der im resultierenden ID-Token als Anspruch enthalten ist. Der Client kann diesen Wert dann überprüfen, um Token-Replay-Angriffe zu verringern. Die maximale Länge beträgt 20 Zeichen.      |
| response_type         | Nein        | Dieser Parameter unterstützt nur `token` als Wert. Dadurch kann Ihre APP sofort ein Zugriffs Token vom Autorisierungs Endpunkt empfangen, ohne dass eine zweite Anforderung an den Autorisierungs Endpunkt gesendet werden muss.                               |
|||

> [!NOTE]
> Obwohl `client_id`-, `redirect_uri`-, `state`-und `nonce`-Parameter optional sind, empfiehlt es sich, diese zu verwenden, um sicherzustellen, dass Ihre Integrationen sicher sind.

### <a name="successful-response"></a>Erfolgreiche Antwort

Der tokenendpunkt gibt State und expires_in als Antwortheader und Token im Formular Text zurück.

### <a name="error-response"></a>Fehler Antwort

Der Fehler in einem tokenendpunkt wird als JSON-Dokument mit den folgenden Werten zurückgegeben:

- **Fehler-ID**: eindeutiger Bezeichner des Fehlers.
- **Fehlermeldung**: eine spezifische Fehlermeldung, mit der Sie die Grundursache eines Authentifizierungsfehlers identifizieren können.
- **Korrelations-ID**: eine GUID, die zu Debugzwecken verwendet wird. Wenn Sie die Diagnoseprotokollierung aktiviert haben, ist die Korrelations-ID in den Server Fehlerprotokollen enthalten.
- **Timestamp**: Datum und Uhrzeit, zu der der Fehler generiert wird.

Die Fehlermeldung wird in der Standardsprache des angemeldeten Benutzers angezeigt. Wenn der Benutzer nicht angemeldet ist, wird eine Anmeldeseite angezeigt, auf der sich der Benutzer anmelden kann. Eine Fehler Antwort sieht z. b. wie folgt aus:

```
{"ErrorId": "PortalSTS0001", "ErrorMessage": "Client Id provided in the request is not a valid client Id registered for this portal. Please check the parameter and try again.", "Timestamp": "4/5/2019 10:02:11 AM", "CorrelationId": "7464eb01-71ab-44bc-93a1-f221479be847" }
```

## <a name="validate-id-token"></a>ID-Token überprüfen

Das Herstellen eines ID-Tokens reicht nicht aus, um den Benutzer zu authentifizieren. Außerdem müssen Sie die Signatur des Tokens überprüfen und die Ansprüche im Token basierend auf den Anforderungen Ihrer APP überprüfen. Der öffentliche Token-Endpunkt stellt den öffentlichen Schlüssel des Portals bereit, der zum Überprüfen der Signatur des Tokens verwendet werden kann, das vom Portal bereitgestellt wird. Die URL für den öffentlichen Token-Endpunkt lautet: `<portal_url>/_services/auth/publickey`.

## <a name="turn-implicit-grant-flow-on-or-off"></a>Aktivieren oder Deaktivieren des impliziten Zuweisungs Flusses

Standardmäßig ist der implizite Zuweisungs Fluss aktiviert. Wenn Sie den impliziten Zuweisungs Fluss deaktivieren möchten, legen Sie den Wert der Site Einstellung **Connector/implicitgrantflowenabled** auf **false**fest.

Wenn diese Standort Einstellung in Ihrem Portal nicht verfügbar ist, müssen Sie [eine neue Website Einstellung](configure/configure-site-settings.md#manage-portal-site-settings) mit dem entsprechenden Wert erstellen.

## <a name="configure-token-validity"></a>Tokengültigkeit konfigurieren

Standardmäßig ist das Token 15 Minuten gültig. Wenn Sie die Gültigkeit des Tokens ändern möchten, legen Sie den Wert der Website Einstellung **implicitgrantflow/tokenexpirationtime** auf den erforderlichen Wert fest. Der Wert muss in Sekunden angegeben werden. Der Maximalwert kann eine Stunde betragen, und der minimale Wert muss 1 Minute betragen. Wenn ein falscher Wert angegeben wird (z. b. alphanumerische Zeichen), wird der Standardwert von 15 Minuten verwendet. Wenn Sie einen Wert angeben, der größer ist als der Maximalwert oder kleiner als der minimale Wert, werden standardmäßig die maximal-und Mindestwerte verwendet.

Legen Sie z. b. für die Gültigkeitsdauer des Tokens einen Wert von 30 Minuten fest, und legen Sie den Wert der Website Einstellung **implicitgrantflow/tokenexpirationtime** auf **1800**fest. Um die Gültigkeitsdauer des Tokens auf 1 Stunde festzulegen, legen Sie den Wert der Website Einstellung **implicitgrantflow/tokenexpirationtime** auf **3600**fest.

## <a name="register-client-id-for-implicit-grant-flow"></a>Registrieren der Client-ID für den impliziten Zuweisungs Fluss

Sie müssen die Client-ID bei dem Portal registrieren, für das dieser Flow zulässig ist. Sie müssen die folgenden Standorteinstellungen erstellen, um eine Client-ID zu registrieren:

|Standort Einstellung|Value|
|------|------|
|Implicitgrantflow/registeredclientid|Die gültigen Client-ID-Werte, die für dieses Portal zulässig sind. Die Werte müssen durch ein Semikolon getrennt werden und können alphanumerische Zeichen und Bindestriche enthalten. Die maximale Länge beträgt 36 Zeichen.|
|Implicitgrantflow/{ClientID}/redirecturi|Die gültigen Umleitungs-URIs, die für eine bestimmte Client-ID zulässig sind. Die Werte müssen durch ein Semikolon getrennt werden. Die angegebene URL muss eine gültige Webseite des Portals sein.|
|||

## <a name="sample-code"></a>Beispielcode

Verwenden Sie den folgenden Beispielcode für die ersten Schritte bei der Verwendung der impliziten OAuth 2,0-Gewährung mit powerapps-Portale-APIs.

### <a name="use-portal-oauth-token-with-an-external-web-api"></a>Verwenden des OAuth-Portal Tokens mit einer externen Web-API

Bei diesem Beispiel handelt es sich um ein ASP.NET basiertes Projekt, das zum Überprüfen des von powerapps-Portalen ausgestellten ID-Tokens verwendet wird. Das komplette Beispiel finden Sie hier: [Verwenden des OAuth-Portal Tokens mit einer externen Web-API](https://github.com/microsoft/PowerApps-Samples/tree/master/portals/ExternalWebApiConsumingPortalOAuthTokenSample).

### <a name="authorize-endpoint-sample"></a>Beispiel für Autorisierungs Endpunkt

Dieses Beispiel zeigt, wie der Autorisierungs Endpunkt das ID-Token als Fragment in der umgeleiteten URL zurückgibt. Außerdem wird die in impliziter Gewährung unterstützte Zustands Überprüfung behandelt. Das Beispiel finden Sie hier: [Beispiel für Autorisieren eines Endpunkts](https://github.com/microsoft/PowerApps-Samples/blob/master/portals/AuthorizeEndpoint.js).

### <a name="token-endpoint-sample"></a>Beispiel für tokenendpunkt

Dieses Beispiel zeigt, wie Sie die getauthenticationtoken-Funktion verwenden können, um ein ID-Token mithilfe des tokenendpunkts in powerapps-Portalen abzurufen. Das Beispiel finden Sie hier: [Beispiel für tokenendpunkt](https://github.com/microsoft/PowerApps-Samples/blob/master/portals/TokenEndpoint.js).
