---
title: Azure AD B2C Anbieter Einstellungen für Portale | MicrosoftDocs
description: Anweisungen zum Aktivieren der Azure AD B2C Anbieter Einstellungen für Portale.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/18/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 5f902dd900e074c2e6b3f08f8848475dcd907ee4
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73542840"
---
# <a name="azure-ad-b2c-provider-settings-for-portals"></a>Azure AD B2C-Anbietereinstellungen für Portale

mit [!include[Azure](../../../includes/pn-azure-shortest.md)] Active Directory (Azure AD) werden Office 365-und Dynamics 365-Dienste für die Mitarbeiter-oder interne Authentifizierung ermöglicht. [!include[Azure](../../../includes/pn-azure-shortest.md)] Active Directory B2C ist eine Erweiterung für dieses Authentifizierungs Modell, das die Anmeldung externer Kunden über lokale Anmelde Informationen und den Verbund mit verschiedenen allgemeinen Identitäts Anbietern ermöglicht.

Der Besitzer eines Portals kann das Portal so konfigurieren, dass [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C als Identitäts Anbieter akzeptiert wird. [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C unterstützt Open ID Connect für den Verbund.

Wenn Sie [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C als Identitäts Anbieter für Ihr Portal konfigurieren, werden mehrere Werte generiert, die Sie später beim Konfigurieren des Portals verwenden werden. Sie können diese Werte in der folgenden Tabelle notieren. Ersetzen Sie beim Konfigurieren des Portals den Variablennamen durch die Werte, die Sie hier notieren.

| Variablen Name     | Value | Beschreibung                                                           |
|-------------------|-------|-----------------------------------------------------------------------|
| Anwendungs Name  |       | Der Name der Anwendung, die das Portal als vertrauende Seite darstellt. |
| Anwendungs-ID    |       | Die Anwendungs-ID, die der in Azure Active Directory B2C erstellten Anwendung zugeordnet ist.  |
| Richtlinie-SignIn-URL |       | Die im Metadatenendpunkt definierte URL des Ausstellers (ISS).                |
| Verbund Name   |       | Ein eindeutiger Name zum Identifizieren des Typs des Verbund Anbieters, z. b. "B2C". Diese wird in Namen von Standorteinstellungen verwendet, um Konfigurationseinstellungen für diesen bestimmten Anbieter zu gruppieren.                                                                      |
| | | |

### <a name="use-azure-ad-b2c-as-an-identity-provider-for-your-portal"></a>Verwenden von Azure AD B2C als Identitäts Anbieter für Ihr Portal

1. Melden Sie sich bei Ihrem [Azure-Portal](https://portal.azure.com/)an.
2. [Erstellen Sie einen Azure AD B2C](https://docs.microsoft.com/azure/active-directory-b2c/active-directory-b2c-get-started)Mandanten.
3. Wählen Sie in der linken Navigationsleiste **[!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C** aus.
4. [Erstellen](https://docs.microsoft.com/azure/active-directory-b2c/active-directory-b2c-app-registration#register-a-web-application)Sie eine Azure-Anwendung.

   > [!Note]
   > Wählen Sie für das Feld **implizites Flow zulassen** die Option **Ja** aus, und geben Sie im Feld **Antwort-URL** die Portal-URL an. Der Wert im Feld **Antwort-URL** sollte das Format [Portal Domäne]/SignIn-[Verbund Name] aufweisen. Beispielsweise `https://contosocommunity.microsoftcrmportals.com/signin-B2C`.

5. Kopieren Sie den Anwendungsnamen, und geben Sie ihn als Wert für Anwendungsname in der obigen Tabelle ein.
6. Kopieren Sie die Anwendungs-ID, und geben Sie Sie als Wert von "Application-ID" in der obigen Tabelle ein.
7. [Erstellen Sie eine Registrierungs-oder Anmelde Richtlinie](https://docs.microsoft.com/azure/active-directory-b2c/active-directory-b2c-reference-policies#create-a-sign-up-or-sign-in-policy).
8. Wählen Sie die Richtlinie aus, und klicken Sie dann auf **Bearbeiten**.
9. Wählen Sie **Token, Sitzung & SSO-Konfiguration**aus.
10. Wählen Sie in der **anspruchsliste Aussteller (ISS)** die URL mit **/TFP** im Pfad aus.
11. Speichern Sie die Richtlinie.
12. Wählen Sie die URL im **Metadatenendpunkt für dieses Richtlinien Feld aus** .
13. Kopieren Sie den Wert des Felds Aussteller, und geben Sie ihn als Wert von Policy-SignIn-URL in der obigen Tabelle ein. 

## <a name="portal-configuration"></a>Portal Konfiguration

Nachdem Sie den B2C-Mandanten in [!include[Azure](../../../includes/pn-azure-shortest.md)]erstellt und konfiguriert haben, müssen Sie das Portal für den Verbund mit [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C mithilfe des Open ID Connect-Protokolls konfigurieren. Sie müssen einen eindeutigen Namen für Ihren Verbund erstellen, um AD B2C zu [!include[Azure](../../../includes/pn-azure-shortest.md)]&mdash;z. b. B2C&mdash;und ihn als Wert der Verbund *Namen* Variablen in der obigen Tabelle speichern.

### <a name="configure-your-portal"></a>Konfigurieren des Portals
1. Öffnen Sie die Portal Verwaltungs-app.
2. Wechseln Sie zu **Portale** > **Websites**.
3. Wählen Sie den Website-Datensatz aus, für den [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C aktiviert werden muss.
4. Wechseln Sie zu **Site Einstellungen**.
5. Erstellen Sie die folgenden Standorteinstellungen:
   -   **Name**: Authentication/openidconnect/[Verbund Name]/Authority

       **Wert**: [Policy-SignIn-URL]
   -   **Name**: Authentication/openidconnect/[Verbund Name]/ClientID

       **Wert**: [Application-ID]
   -   **Name**: Authentication/openidconnect/[Verbund Name]/RedirectUri

       **Wert**: [Portal Domäne]/SignIn-[Verbund Name]

       Beispielsweise `https://mysite.com/signin-b2c` 
6. Erstellen Sie die folgende Standort Einstellung, um eine Verbund Abmeldung zu unterstützen:
   - **Name**: Authentication/openidconnect/[Verbund Name]/ExternalLogoutEnabled

     **Wert**: true
7. Um das Portal für einen einzelnen Identitäts Anbieter hart zu codieren, erstellen Sie die folgende Website Einstellung:
   - **Name**: Authentication/Registration/loginbuttonauthenticationtype

     **Wert**: [Policy-SignIn-URL]

8. Um die Kenn Wort Zurücksetzung zu unterstützen, erstellen Sie die [hier](#password-reset)beschriebenen erforderlichen Site Einstellungen.
9. Um die Anspruchs Zuordnung zu unterstützen, erstellen Sie die [hier](#claims-mapping)beschriebenen erforderlichen Site Einstellungen.

Eine umfassende Liste verwandter Site Einstellungen finden Sie [hier](#related-site-settings).

### <a name="password-reset"></a>Kenn Wort Zurücksetzung

Die folgenden Standorteinstellungen sind erforderlich, wenn Sie die Kenn Wort Zurücksetzung mit [!include[Azure](../../../includes/pn-azure-shortest.md)] lokalen AD B2C-Konten unterstützen möchten:

| Standort Einstellung                                                        | Beschreibung                                                                                                          |
|---------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------|
| Authentication/openidconnect/[Verbund Name/passwordresetpolicyid | Die ID der Richtlinie zum Zurücksetzen des Kennworts.                                                                                     |
| Authentication/openidconnect/[Verbund Name]/ValidIssuers         | Eine durch Trennzeichen getrennte Liste von Ausstellern, die [Policy-SignIn-URL] und den Aussteller der Richtlinie zum Zurücksetzen von Kenn Wörtern enthält. |
|Authentication/openidconnect/[Verbund Name]/DefaultPolicyId | ID der Anmeldungs-oder Registrierungs Richtlinie.|
|||

### <a name="related-site-settings"></a>Verwandte Site Einstellungen

Sie können die folgenden Site Einstellungen in Portalen erstellen oder konfigurieren, um [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C als Identitäts Anbieter zu unterstützen:


| Standort Einstellung                                                         | Beschreibung                                                                                                                                                                                                                                                        |
|----------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Authentifizierung/Registrierung/profiredirectenabled                   | Gibt an, ob Benutzer nach erfolgreicher Anmeldung an die Profilseite umgeleitet werden können. Standardmäßig ist der Wert auf true festgelegt.                                                                                                                                            |
| Authentifizierung/Registrierung/emailconfirmationaktivierte                 | Gibt an, ob e-Mail-Überprüfung erforderlich ist Standardmäßig ist der Wert auf true festgelegt.                                                                                     |
| Authentifizierung/Registrierung/loczuordnung aktiviert                        | Gibt an, ob eine lokale Anmeldung erforderlich ist. Standardmäßig ist der Wert auf true festgelegt.                                                                        |
| Authentifizierung/Registrierung/externzuweisung aktiviert                     | Aktiviert oder deaktiviert die externe Authentifizierung.       |
| Authentifizierung/Registrierung/azuleloginaktivierte                      | Aktiviert oder deaktiviert [!include[Azure](../../../includes/pn-azure-shortest.md)] AD als externen Identitäts Anbieter. Standardmäßig ist der Wert auf true festgelegt.                                                                                                                                                                      |
| Authentication/openidconnect/[Verbund Name]/ExternalLogoutEnabled | Aktiviert oder deaktiviert die Verbund Abmeldung. Wenn diese Einstellung auf "true" festgelegt ist, werden Benutzer bei der Abmeldung vom Portal an die Benutzeroberflächen für die Verbund Anmeldung umgeleitet. Wenn diese Einstellung auf "false" festgelegt ist, werden Benutzer nur aus dem Portal abgemeldet. Standardmäßig ist der Wert auf false festgelegt.               |
| Authentifizierung/logintrackingenabled                                  | Aktiviert oder deaktiviert die Nachverfolgung der letzten Anmeldung des Benutzers. Wenn der Wert auf true festgelegt ist, werden das Datum und die Uhrzeit im **letzten erfolgreichen Anmelde** Feld des Contact-Datensatzes angezeigt. Standardmäßig ist diese Einstellung auf "false" festgelegt.                                                            |
| Authentication/openidconnect/[Verbund Name]/RegistrationEnabled   | Aktiviert oder deaktiviert die Registrierungs Anforderung für den vorhandenen Identitäts Anbieter. Wenn diese Option auf true festgelegt ist, wird die Registrierung für den vorhandenen Anbieter nur aktiviert, wenn für die Website Einstellung Authentifizierung/Registrierung/aktiviert ebenfalls der Wert true festgelegt ist. Standardmäßig ist der Wert auf true festgelegt. |
|Authentication/openidconnect/[Verbund Name]/PostLogoutRedirectUri |Gibt die URL im Portal an, zu der umgeleitet werden soll, nachdem ein Benutzer sich abgemeldet hat. |
| | |

### <a name="related-content-snippet"></a>Code Ausschnitt für verwandte Inhalte

Wenn die Registrierung für einen Benutzer deaktiviert ist, nachdem der Benutzer eine Einladung eingelöst hat, können Sie eine Meldung mit dem folgenden Inhalts Ausschnitt anzeigen:

**Name**: Account/Register/registrationdisabledmessage

**Wert**: die Registrierung wurde deaktiviert.

## <a name="customize-the-includeazureincludespn-azure-shortestmd-ad-b2c-user-interface"></a>Anpassen der [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C-Benutzeroberfläche

[!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C unterstützt die Anpassung der Benutzeroberfläche. Sie können die Benutzer Darstellung für Registrierungs-und Anmelde Szenarien anpassen.

### <a name="step-1-create-a-web-template"></a>Schritt 1: Erstellen einer Webvorlage
Erstellen Sie eine Webvorlage mit den folgenden Werten:

**Name**: [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C-Seite "Benutzer definiert"

**Quelle**: Verwenden Sie die folgende Beispiel-Web-Vorlagen Quell-HTML.

```html
<!DOCTYPE html>
<html lang=en-US>
  <head>
    <meta charset=utf-8>
    <meta name=viewport content=width=device-width, initial-scale=1.0>
    <meta http-equiv=X-UA-Compatible content=IE=edge>
    <title>
      {{ page.title | h }}
    </title>
                        <link href={{ request.url | base }}/bootstrap.min.css rel=stylesheet>
                        <link href={{ request.url | base }}/theme.css rel=stylesheet>
                        <style>
                          .page-heading {
            padding-top: 20px;
      }
      .page-copy {
            margin-bottom: 40px;
      }
      .highlightError {
        border: 1px solid #cb2027!important;
        background-color: #fce8e8!important;
      }
      .attrEntry .error.itemLevel {
        display: none;
        color: #cb2027;
        font-size: .9em;
      }
      .error {
        color: #cb2027;
      }
      .entry {
        padding-top: 8px;
        padding-bottom: 0!important;
      }
      .entry-item {
        margin-bottom: 20px;
      }
      .intro {
        display: inline;
        margin-bottom: 5px;
      }
      .pageLevel {
          width: 293px;
          text-align: center;
          margin-top: 5px;
          padding: 5px;
          font-size: 1.1em;
          height: auto;
      }
      #panel, .pageLevel, .panel li, label {
          display: block;
      }
      #forgotPassword {
          font-size: .75em;
          padding-left: 5px;
      }
      #createAccount {
          margin-left: 5px;
      }
      .working {
          display: none;
          background: url(data:image/gif;base64,R0lGODlhbgAKAPMAALy6vNze3PTy9MTCxOTm5Pz6/Ly+vNTS1Pz+/�N0Jp6BUJ9EBIISAQAh+QQJCQAKACxRAAIABgAGAAAEE1ClYU4RIIMTdCaegVCfRASCEgEAOw==) no-repeat;
          height: 10px;
          width: auto;
      }
      .divider {
        margin-top: 20px;
        margin-bottom: 10px;
      }
      .divider h2 {
        display: table;
        white-space: nowrap;
        font-size: 1em;
        font-weight: 700;
      }
      .buttons {
        margin-top: 10px;
      }
      button {
            width:auto;
            min-width:50px;
            height:32px;
            margin-top:2px;
            -moz-border-radius:0;
            -webkit-border-radius:0;
            border-radius:0;
            background:#2672E6;
            border:1px solid #FFF;
            color:#fff;
            transition:background 1s ease 0s;
            font-size:100%;
            padding:0 2px
      }

      button:hover {
            background:#0F3E83;
            border:1px solid #3079ed;
            -moz-box-shadow:0 0 0;
            -webkit-box-shadow:0 0 0;
            box-shadow:0 0 0
      }
      .password-label label {
        display: inline-block;
        vertical-align: baseline;
      }
      img {
            border:0
      }
      .divider {
            margin-top:20px;
            margin-bottom:10px
      }
      .divider h2 {
            display:table;
            white-space:nowrap;
            font-size:1em;
            font-weight:700
      }
      .divider h2:after,.divider h2:before {
            border-top:1px solid #B8B8B8;
            content:'';
            display:table-cell;
            position:relative;
            top:.7em;
            width:50%
      }
      .divider h2:before {
            right:1.8%
      }
      .divider h2:after {
            left:1.8%
      }
      .verificationErrorText {
            color:#D63301
      }
      .options div {
            display:inline-block;
            vertical-align:top;
            margin-top:7px
      }
      .accountButton,.accountButton:hover {
            background-image:url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACAAAAAgCAMAAABEpIrGAAAAh1BMVEX///9QUFBOTk5LS0tERERCQkI/Pz9ISEg6OjpGRkZNTU08PDyAgID09PSlpaWWlpZxcXFgYGBZWVlUVFT6+vrx8fHt7e3s7Ozo6Oji4uLJycnGxsa4uLiqqqqgoKCNjY2JiYmGhoZra2tmZmb7+/vu7u7d3d3U1NTNzc2+vr67u7usrKx7e3vprNQnAAAA8klEQVQ4y63Q127DMAxAUZpDwyMeSdqsNqu7/f/va6zahgGJKAr0vgk6DyQh+6V/BiTOOeNRA9zuAWBdM6WBlPDTvaUUoAuMrT0mgNvA1IJjQB3MKjACvp6DK0WAH+agtH8H9jQHLUUgz7Uhx8xOXzNESxirLCYA2mw8tacI5FyIYXq8A9ge2Qs6oTnw2e2ruho2rjBcXJ4ADh3jBOQLQnVhRFx2gNDZ4ACogbHXj/ft9Dj5AcgbJFu5AThQWuYBIGmgtAFQo4EFB+CPGthJAPypgY3BHsheA5UNwLyAvsYNoDyroKUe4EoFTQ/yDtTONvsGUJ8KTUYyH+UAAAAASUVORK5CYII=);
            background-repeat:no-repeat
      }
      .accountButton {
            border:1px solid #FFF;
            color:#FFF;
            margin-left:0;
            margin-right:2px;
            transition:background-color 1s ease 0s;
            -moz-border-radius:0;
            -webkit-border-radius:0;
            border-radius:0;
            text-align:center;
            word-wrap:break-word;
            height:34px;
            width:158px;
            padding-left:30px;
            background-color:#505050;
      }
      .accountButton:hover {
            background-color:#B9B9B9;
            border:1px solid #FFF;
            -moz-box-shadow:0 0 0;
            -webkit-box-shadow:0 0 0;
            box-shadow:0 0 0
      }
      .accountButton:focus {
            outline:gold solid 1px
      }
      #MicrosoftAccountExchange {
            background-image:url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACAAAAAgCAMAAABEpIrGAAAAPFBMVEU1pe/////t+v4uoe5btvNixPVVwfUsoe9tyfXU7/y95vu24vrd9f5NtfLH6/ys3/o/sPE6qfD2/f+f2vnAysuQAAAAaElEQVQ4y93SORKAIAwFUEGCsoT1/nd1JkkDFhY24qt+8VMkk20lu6DAaVBOBsVKsuO8aYo08IqlYyxoRTQExfyKheRIgu5Yl4KoVhSUgNOhoiYRsmb5g2u+LtzXDNOhjKgoAZ9/8k8uZWsGqcIav5wAAAAASUVORK5CYII=);
            background-color:#33A7F2
      }
      #MicrosoftAccountExchange:hover {
            background-color:#ADDBF9
      }
      #GoogleExchange {
            background-image:url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACAAAAAgCAMAAABEpIrGAAAAb1BMVEXcTkH////cTD/bSj3ZQDLYOyzaRDbeV0vbSDrZPS/66Obyv7rsnpfpkorjcWfgZlvXOCr++Pj5393haFz88/L88fD67Or319T1zsv1zsrxuLPuqaLuqKLoi4LlfXTgYlbWMyTWMiPwtrHwta/fXVH/sCIIAAAAmElEQVQ4y+2RyQ7DIBBDMcwAIXvovqXb/39jRaX0AEmr5px3tSV7PGLhX6TVRFpN61l9zPNS6kn9gDcXO67zDnCnO2BCiNIyMtgKKJgyY2zQ68JEDtqju0nFTcOsxPUMw1GDDUqt+tY51/YNVlhvacTgEfCDIY0Q/lkBSg4RaUmmDo4/JdMzHy1Q2ejMeCj6PrXQP5+1MI8X0Y4HL4c826EAAAAASUVORK5CYII=);
            background-color:#DC4E41
      }
      #GoogleExchange:hover {
            background-color:#F1B8B3
      }
      #TwitterExchange {
            background-image:url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACAAAAAgCAMAAABEpIrGAAAAdVBMVEVgqd3///9Ypdtdp9xaptxSotpQodlNn9lWo9pUo9rX6Pa+2vGTw+iLvuZlqt79/P7K4PO62O+y0+6hyutysuD2+fzi7vne6/fT5PTE3fKs0O2lzeuZx+l7tuJqrd71+Pzz9vzn8PnQ4/SCueSAueNsrt9InNh7sQwBAAAAwklEQVQ4y92PRw6EMAwAXeIkdBbY3uv/n7gSAoLDD5hbPCPZgZVihEgYgNSUpmfS7bfbtHS2nReyL2Qoc+yp8ZRAwCEWjgGAPQ7sssKoAGsWBrrgyMZCwD77Uel+59E3Tt14xZ7qlY7BRf1CDgeMKMw8sBXGlKxWtLGvHCgkQ80m0YHpjjq4sQ74pn1mISLJVSAMiwJO98l/TWSNF1eGKzqKfZ7Vj0mnHHwodpP+WIYlZP373DTtVWxYr2FD3pOBdfIHhOAHYHQI9VgAAAAASUVORK5CYII=);
            background-color:#60A9DD
      }
      #TwitterExchange:hover {
            background-color:#BFDCF1
      }
      #FacebookExchange {
            background-image:url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACAAAAAgCAMAAABEpIrGAAAAaVBMVEU7W5z///85Wps3WJsiRo8xU5fw8vYyUpY0VZiAj70pS5OBkb0vUpb7+fwsTpTR1ud6irllerBPaqX09fnx8vfs7fSQoMZxg7VsgLNGY6FCX58ZP4v++/7r7vTZ3OupstGIlsFWcalDYaCK3qwDAAAAnklEQVQ4y+XQyw7CIBAFUBgc5VUoWGtb3/7/RyoYkyZAiSsXvdt7kstA/hRg/B0GpZ6byQ3Dw0NBaH+lMYRle3T0kwayACRdBrr/gnN+QtpQWv8cR4DswiUAjozlz4RdF8AmlnmwjaDQImoZwQkRedoToUS7D+ColGoTwQidx8oEQDMHN1MBva5MOL70SCHuE1TOhOpHrRt0FWAOP4IX8PsG2qEOR30AAAAASUVORK5CYII=);
            background-color:#3B5B9C
      }
      #FacebookExchange:hover {
            background-color:#B0BDD7
      }
      #LinkedInExchange {
            background-image:url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACAAAAAgCAMAAABEpIrGAAAAb1BMVEUAe7b///8AdrMklscAc7EAeLUAcbB5ttifzeMqmckAdLIAaqz7+/6PxeAShr0CgLkAba4nmMctksTv9Puw1eij0OWGvNtfrNJNo80YjMAeib/D4vGt3Oy82+yfzOOCvtyJvdx3tddirtI/ncoxmMj9KsrQAAAAw0lEQVQ4y9WSVw7DIAxAG8CkjJDVzO5x/zMWk0RNJaB/kfo+sGUeCMvstgI4J7F9aS5NxSLnTWLpZVDgexTqIiycUNBhgTxRyCKPYJ3dl7sITCkO+FyLXaWU310DscASOesf3ahWChGJ5cb4ASO5Joiu2EegWEmZa1c3yUwOHmHNuQgJup4CgF8YlKpcMhKvkNmb1REz6hdetsyziIBldv8lpH8ouGm28zQFCu2SOSAXlJYGYCgpFThEMFPm/zCryja8Acy7CRfMrcKPAAAAAElFTkSuQmCC);
            background-color:#0077B5
      }
      #LinkedInExchange:hover {
            background-color:#99CAE1
      }
      #AmazonExchange {
            background-image:url(https://images-na.ssl-images-amazon.com/images/G/01/lwa/btnLWA_gold_156x32.png);
            background-color:#FFF;
            color:transparent
      }

      #next {
            -moz-user-select:none;
            user-select:none;
            cursor:pointer;
            width:auto;
            padding-left:10px;
            padding-right:10px;
            height:30.5px;
            -moz-border-radius:0;
           -webkit-border-radius:0;
            border-radius:0;
            background:#2672E6;
            border:1px solid #FFF;
            color:#fff;
            transition:background 1s ease 0s;
            font-size:100%
      }
      #next:hover {
            background:#0F3E83;
            border:1px solid #FFF;
            box-shadow:0 0 0
      }
      #next:hover,.accountButton:hover {
            -moz-box-shadow:0 0 0;
            -webkit-box-shadow:0 0 0;
            box-shadow:0 0 0;
      }
                        </style>
  </head>
  <body>
    <div class=navbar navbar-inverse navbar-static-top role=navigation>
      <div class=container>
        <div class=navbar-header>
          <div class=visible-xs-block>
            {{ snippets[Mobile Header] }}
          </div>
          <div class=visible-sm-block visible-md-block visible-lg-block navbar-brand>
            {{ snippets[Navbar Left] }}
          </div>
        </div>
      </div>
    </div>
    <div class=container>
      <div class=page-heading>
        <ul class=breadcrumb>
          <li>
            <a href={{ request.url | base }} title=Home>Home</a>
          </li>
          <li class=active>{{ page.title | h}}</li>
        </ul>
        {% include 'Page Header' %}
     </div>
     <div class=row>
      <div class=col-md-12>
        {% include 'Page Copy' %}
        <div id=api></div>
      </div>
     </div>
    </div>
    <footer role=contentinfo>
      <div class=footer-top hidden-print>
        <div class=container>
          <div class=row>
            <div class=col-md-6 col-sm-12 col-xs-12 text-left>
               {{ snippets[About Footer] }}
            </div>
            <div class=col-md-6 col-sm-12 col-xs-12 text-right>
              <ul class=list-social-links>
                <li><a href=#><span class=sprite sprite-facebook_icon></span></a></li>
                <li><a href=#><span class=sprite sprite-twitter_icon></span></a></li>
                <li><a href=#><span class=sprite sprite-email_icon></span></a></li>
              </ul>
            </div>
          </div>
        </div>
      </div>
      <div class=footer-bottom hidden-print>
        <div class=container>
          <div class=row>
            <div class=col-md-4 col-sm-12 col-xs-12 text-left>
               {{ snippets[Footer] | liquid }}
            </div>
            <div class=col-md-8 col-sm-12 col-xs-12 text-left >
            </div>   
          </div>
        </div>
      </div>
    </footer>
  </body>
</html>
```
### <a name="step-2-create-a-page-template"></a>Schritt 2: Erstellen einer Seitenvorlage

Erstellen Sie die folgende Seitenvorlage:
- **Name**: [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C-Seite "Benutzer definiert"
- **Typ**: Webvorlage
- **Webvorlage**: [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C-Seite "Benutzer definiert"
- **Kopf-und Fußzeile der Website verwenden**: Deaktivieren Sie dieses Kontrollkästchen.

### <a name="step-3-create-a-webpage"></a>Schritt 3: Erstellen einer Webseite

Erstellen Sie die folgende Webseite:
- **Name**: anmelden
- Über **geordnetes** Element Seite: Startseite
- **Partielle URL**: Azure-AD-B2C-Sign-in
- **Seitenvorlage**: [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C-Seite "Benutzer definiert"
- **Veröffentlichungsstatus**: veröffentlicht

### <a name="step-4-create-site-settings"></a>Schritt 4: Erstellen von Site Einstellungen

Website Einstellungen sind erforderlich, um Cross-Origin Resource Sharing (cors) zu konfigurieren, damit [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C die benutzerdefinierte Seite anfordern und die Anmelde-oder Anmelde Benutzeroberfläche einfügen kann. Erstellen Sie die folgenden Site Einstellungen.

| Name                              | Value                             |
|-----------------------------------|-----------------------------------|
| HTTP/Access-Control-Allow-Methods | Get, Optionen                      |
| HTTP/Access-Control-Allow-Origin  | `https://login.microsoftonline.com` |
| | |

Eine umfassende Liste mit anderen cors-Einstellungen finden Sie [unter cors-Protokoll Unterstützung](../add-web-resource.md#cors-protocol-support).

### <a name="step-5-includeazureincludespn-azure-shortestmd-configuration"></a>Schritt 5: [!include[Azure](../../../includes/pn-azure-shortest.md)] Konfiguration

1. Melden Sie sich bei Ihrem [!include[Azure portal](../../../includes/pn-azure-portal.md)]an.
2. Navigieren Sie zum Blatt " **[!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C** -Mandanten Verwaltung".
3. Navigieren Sie zu **Einstellungen** > Registrierungs **-oder Anmelde Richtlinien**. Eine Liste der verfügbaren Richtlinien wird angezeigt.
4. Wählen Sie die Richtlinie aus, die Sie bearbeiten möchten.
5. Wählen Sie **Bearbeiten**aus.
6. Wählen Sie **Richtlinie bearbeiten** > **Seite Anpassung der Benutzeroberfläche** > **einheitliche Registrierungs-oder Anmeldeseite aus** .
7. Legen Sie **benutzerdefinierte Seite verwenden** auf **Ja**fest.
8. Legen Sie **benutzerdefinierter Seiten-URI** auf die URL der benutzerdefinierten Seiten Webseite [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C fest, die in Schritt 3 dieses Verfahrens erstellt wurde. Beispielsweise `https://mydomain.com/azure-ad-b2c-sign-in`.
9. Wählen Sie **OK** aus.

## <a name="claims-mapping"></a>Anspruchs Zuordnung

Wenn sich Benutzer zum ersten Mal oder später anmelden, stellt der Verbund Identitäts Anbieter Ansprüche basierend auf seiner Datenbank im Hinblick auf die Benutzeranmeldung bereit. Diese Ansprüche können im Identitäts Anbieter konfiguriert werden.

### <a name="includeazureincludespn-azure-shortestmd-ad-b2c-email-claims"></a>e-Mail-Ansprüche [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C

[!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C den e-Mail-Anspruch als Sammlung sendet. Das Portal nimmt die erste in der Sammlung angegebene e-Mail als primäre e-Mail-Adresse des Kontakts an.

### <a name="claims-to-support-sign-up-scenarios"></a>Ansprüche zur Unterstützung von Registrierungs Szenarien

Wenn ein neuer Kunde, der nicht in Common Data Service vorhanden ist, bereitgestellt wird, können die eingehenden Ansprüche verwendet werden, um einen Ausgangswert für den neuen Kontaktdaten Satz zu erstellen, der vom Portal erstellt wird. Allgemeine Ansprüche können vor-und Nachname, e-Mail-Adresse und Telefonnummer enthalten, Sie sind jedoch konfigurierbar. Die folgende Standort Einstellung ist erforderlich:

**Name**: Authentication/openidconnect/[Verbund Name]/RegistrationClaimsMapping

**Description**: Liste der logischen Name-/Anspruch-Paare, die verwendet werden, um Anspruchs Werte Attributen in dem während der Registrierung erstellten Kontaktdaten Satz zuzuordnen.

**Format**: attribute1 = claim1, attribute2 = claim2, attribute3 = claim3

Beispiel: FirstName =<https://schemas.xmlsoap.org/ws/2005/05/identity/claims/givenname,lastname=https://schemas.xmlsoap.org/ws/2005/05/identity/claims/surname,jobtitle=jobTitle>

> [!NOTE]
> Stellen Sie sicher, dass Sie die e-Mail-Adresse der primären e-Mail (EmailAddress1) des Kontakts zuordnen. Wenn Sie dem Kontaktdaten Satz sekundäre e-Mail (EmailAddress2) oder Alternative e-Mail-Adresse (EmailAddress3) hinzugefügt und der e-Mail zugeordnet haben, werden dem Kontakt keine Identitätsinformationen hinzugefügt, und ein neuer wird mit der für die Registrierung verwendeten e-Mail-Adresse erstellt. die primäre e-Mail-Adresse (EmailAddress1).

### <a name="claims-to-support-sign-in-scenarios"></a>Ansprüche zur Unterstützung von Anmelde Szenarien

Die Daten in Common Data Service und im Identitäts Anbieter sind nicht direkt verknüpft, sodass die Daten möglicherweise nicht mehr synchronisiert werden. Das Portal sollte über eine Liste von Ansprüchen verfügen, die Sie von jedem Anmelde Ereignis annehmen möchten, das in Common Data Service aktualisiert werden soll. Diese Ansprüche können eine Teilmenge der Ansprüche sein, die aus einem Anmelde Szenario stammen. Dies muss getrennt von der Zuordnung von Anmelde Ansprüchen konfiguriert werden, da Sie einige wichtige Portal Attribute möglicherweise nicht überschreiben möchten. Die folgende Standort Einstellung ist erforderlich:

**Name**: Authentication/openidconnect/[Verbund Name]/LoginClaimsMapping

**Beschreibung**: Liste der logischen Name-/Anspruch-Paare, die verwendet werden, um Anspruchs Werte Attributen in dem Kontaktdaten Satz zuzuordnen, der nach der Anmeldung erstellt wurde.

**Format**: attribute1 = claim1, attribute2 = claim2, attribute3 = claim3

Beispiel: FirstName =<https://schemas.xmlsoap.org/ws/2005/05/identity/claims/givenname,lastname=https://schemas.xmlsoap.org/ws/2005/05/identity/claims/surname,jobtitle=jobTitle> 

Der Anspruchs Name ist das Feld Anspruchstyp, das neben dem-Attribut in den Anwendungs Ansprüchen der Anmelde Richtlinien aufgeführt ist.

### <a name="allow-auto-association-to-a-contact-record-based-on-email"></a>Automatische Zuordnung zu einem Kontaktdaten Satz basierend auf e-Mail zulassen 

Kunden, die Kontaktdaten Sätze mit zugeordneten e-Mails haben, starten dann eine Website, auf der sich Ihre externen Benutzer mit [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C über einen e-Mail-Überprüfungsmechanismus anmelden. Die neue Anmeldung sollte dem vorhandenen Kontaktdaten Satz zugeordnet werden, anstatt einen doppelten Datensatz zu erstellen. Mit dieser Funktion wird nur ein Kontakt, der keine aktive Identität besitzt, erfolgreich zugeordnet, und die e-Mail-Adresse muss eindeutig sein (nicht im Zusammenhang mit mehreren Kontaktdaten Sätzen). Die folgende Standort Einstellung ist erforderlich:

**Name**: Authentication/[Protokoll]/[Anbieter]/AllowContactMappingWithEmail

**Description**: gibt an, ob Kontakte einer entsprechenden e-Mail zugeordnet werden. Wenn diese Einstellung auf "true" festgelegt ist, wird ein eindeutiger Kontaktdaten Satz mit einer übereinstimmenden e-Mail-Adresse zugeordnet. Anschließend wird der externe Identitäts Anbieter dem Kontakt automatisch zugewiesen, nachdem sich der Benutzer erfolgreich angemeldet hat. Standardmäßig ist der Wert auf false festgelegt.
