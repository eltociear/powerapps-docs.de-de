---
title: Azure AD B2C-Anbietereinstellungen für Portale | MicrosoftDocs
description: Anweisungen zum Aktivieren von Azure AD B2C-Anbietereinstellungen für Portale.
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
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "2755485"
---
# <a name="azure-ad-b2c-provider-settings-for-portals"></a>Azure AD B2C-Anbietereinstellungen für Portale

[!include[Azure](../../../includes/pn-azure-shortest.md)] Active Directory (Azure AD) unterstützt Office 365 und Dynamics 365-Dienste für Mitarbeiter oder interne Authentifizierung. [!include[Azure](../../../includes/pn-azure-shortest.md)] Active Directory B2C ist eine Erweiterung zu diesem Authentifizierungsmodell, das Anmeldungen von externen Debitoren über lokale Anmeldeinformationen und einen Verbund mit verschiedenen gemeinsamen sozialen Identitätsanbietern aktiviert.

Ein Portalbesitzer kann das Portal so konfigurieren, dass [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C als Identitätsanbieter akzeptiert wird. [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C unterstützt Open ID Connect für Verbunde.

Beim Konfigurieren von [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C als Identitätsanbieter für Ihr Portal werden mehrere Werte erstellt, die Sie später beim Konfigurieren des Portals verwenden. Sie können diese Werte in der folgenden Tabelle finden. Ersetzen Sie beim Konfigurieren des Portals den Variablennamen durch die hier angegebenen Werte.

| Variablenname     | Wert | Beschreibung                                                           |
|-------------------|-------|-----------------------------------------------------------------------|
| Anwendungsname  |       | Name der Anwendung, die das Portal als vertrauende Seite darstellt |
| Anwendungs-ID    |       | Die Anwendungs-ID, die mit der in Azure Active Directory B2C erstellten Anwendung verknüpft ist.  |
| Richtlinien-Anmeldungs-URL |       | Die im Metadatenendpunkt definierte Aussteller-URL (iss).                |
| Verbundname   |       | Ein eindeutiger Name zur Identifizierung des Typs des Verbundanbieters wie beispielsweise „B2C”. Dieser wird in den Website-Einstellungsnamen verwendet, um Konfigurationseinstellungen für diesen speziellen Anbieter zu gruppieren.                                                                      |
| | | |

### <a name="use-azure-ad-b2c-as-an-identity-provider-for-your-portal"></a>Verwenden von Azure AD B2C als Identitätsanbieter für Ihr Portal

1. Melden Sie sich bei Ihrem [Azure-Portal](https://portal.azure.com/) an.
2. [Erstellen Sie einen Azure AD B2C Mandanten](https://docs.microsoft.com/azure/active-directory-b2c/active-directory-b2c-get-started).
3. Wählen Sie auf der Navigationsleiste ganz links **[!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C**.
4. [Erstellen einer Azure-Anwendung](https://docs.microsoft.com/azure/active-directory-b2c/active-directory-b2c-app-registration#register-a-web-application).

   > [!Note]
   > Sie müssen **Ja** für das Feld **Impliziten Fluss zulassen** auswählen und Ihre Portal-URL im Feld **Antwort-URL** angeben. Der Wert im Feld **Antwort-URL** sollte das Format [Portaldomäne]/Anmelde-[Verbundname] aufweisen. Zum Beispiel: `https://contosocommunity.microsoftcrmportals.com/signin-B2C`.

5. Kopieren Sie den Anwendungsnamen, und geben Sie ihn als Wert für den Anwendungsnamen in der vorherigen Tabelle ein.
6. Kopieren Sie die Anwendungs-ID, und geben Sie sie als Wert für die Anwendungs-ID in der vorherigen Tabelle ein.
7. [Erstellen einer Registrierungs- oder Anmelderichtlinie](https://docs.microsoft.com/azure/active-directory-b2c/active-directory-b2c-reference-policies#create-a-sign-up-or-sign-in-policy).
8. Wählen Sie die Richtlinie aus, und wählen Sie dann **Bearbeiten** aus.
9. Wählen Sie **Token-, Sitzungs- und SSO-Konfiguration** aus.
10. Wählen Sie in der Liste **Ausstelleranspruch (iss)** die URL aus, deren Pfad **/tfp** enthält.
11. Speichern Sie die Richtlinie.
12. Klicken Sie auf die URL im Feld **Metadatenendpunkte für diese Richtlinie**.
13. Kopieren Sie den Wert des Ausstellerfelds, und geben Sie diesen als Wert der Richtlinien-Anmeldungs-URL in der vorherigen Tabelle ein. 

## <a name="portal-configuration"></a>Portalkonfiguration

Wenn Sie den B2C-Mandanten in [!include[Azure](../../../includes/pn-azure-shortest.md)] erstellt und konfiguriert haben, müssen Sie das Portal mithilfe des Open ID Connect-Protokolls so konfigurieren, dass es mit [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C verbunden wird. Sie müssen einen eindeutigen Namen für den Verbund mit [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C&mdash; erstellen, wie beispielsweise B2C&mdash;, und diesen als Wert der Variablen *Verbundname* in der vorherigen Tabelle speichern.

### <a name="configure-your-portal"></a>Konfigurieren Ihres Portals
1. Öffnen Sie die Portalverwaltungs-App.
2. Navigieren Sie zu **Portale** > **Websites**.
3. Wählen Sie den Websitedatensatz aus, für den [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C aktiviert werden muss.
4. Wechseln Sie zu **Websiteeinstellungen**.
5. Erstellen Sie die folgenden Websiteeinstellungen:
   -   **Name**: Authentication/OpenIdConnect/[Federation-Name]/Authority

       **Wert**: [Policy-Signin-URL]
   -   **Name**: Authentication/OpenIdConnect/[Federation-Name]/ClientId

       **Wert**: [Application-ID]
   -   **Name**: Authentication/OpenIdConnect/[Federation-Name]/RedirectUri

       **Wert**: [portal domain]/signin-[Federation-Name]

       Zum Beispiel `https://mysite.com/signin-b2c` 
6. Um eine verbundbasierten Abmeldung zu unterstützen, erstellen Sie die folgenden Websiteeinstellungen:
   - **Name**: Authentication/OpenIdConnect/[Federation-Name]/ExternalLogoutEnabled

     **Wert**: true
7. Zum Hartcodieren Ihres Portals für einen einzigen Identitätsanbieter erstellen Sie die folgenden Websiteeinstellungen:
   - **Name**: Authentication/Registration/LoginButtonAuthenticationType

     **Wert**: [Policy-Signin-URL]

8. Um die Kennwortrücksetzung zu unterstützen, erstellen Sie die erforderlichen Websiteeinstellungen, die [hier](#password-reset) beschrieben sind.
9. Um die Anspruchszuordnung zu unterstützen, erstellen Sie die erforderlichen Websiteeinstellungen, die [hier](#claims-mapping) beschrieben sind.

Eine vollständige Liste mit verknüpften Websiteeinstellungen finden Sie [hier](#related-site-settings).

### <a name="password-reset"></a>Kennwort zurücksetzen

Die folgenden Websiteeinstellungen sind erforderlich, wenn Sie die Kennwortrücksetzung für lokale [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C-Konten unterstützen möchten:

| Website-Einstellung                                                        | Beschreibung                                                                                                          |
|---------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------|
| Authentication/OpenIdConnect/[Federation-Name/PasswordResetPolicyId | ID der Richtlinie für die Kennwortrücksetzung.                                                                                     |
| Authentication/OpenIdConnect/[Federation-Name]/ValidIssuers         | Eine durch Komma getrennte Liste von Ausstellern, die die [Richtlinien-Anmeldungs-URL] und den Aussteller der Richtlinie für die Kennwortrücksetzung umfasst. |
|Authentication/OpenIdConnect/[Federation-Name]/DefaultPolicyId | ID der Anmeldungs- oder Registrierungsrichtlinie.|
|||

### <a name="related-site-settings"></a>Zugehörige Websiteeinstellungen

Sie können die folgenden Websiteeinstellungen in Portalen erstellen oder konfigurieren, um [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C als Identitätsanbieter zu unterstützen:


| Website-Einstellung                                                         | Beschreibung                                                                                                                                                                                                                                                        |
|----------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Authentication/Registration/ProfileRedirectEnabled                   | Gibt an, ob das Portal Benutzer nach erfolgreichen Anmeldung zur Profilseite weiterleiten kann. Standardmäßig ist dies auf "true" gesetzt.                                                                                                                                            |
| Authentication/Registration/EmailConfirmationEnabled                 | Gibt an, ob eine E-Mail-Überprüfung erforderlich ist. Standardmäßig ist dies auf "true" gesetzt.                                                                                     |
| Authentication/Registration/LocalLoginEnabled                        | Gibt an, ob eine lokale Anmeldung erforderlich ist. Standardmäßig ist dies auf "true" gesetzt.                                                                        |
| Authentication/Registration/ExternalLoginEnabled                     | Aktiviert oder deaktiviert die externe Authentifizierung.       |
| Authentication/Registration/AzureADLoginEnabled                      | Aktiviert oder deaktiviert [!include[Azure](../../../includes/pn-azure-shortest.md)] AD als externen Identitätsanbieter. Standardmäßig ist dies auf "true" gesetzt.                                                                                                                                                                      |
| Authentication/OpenIdConnect/[Federation-Name]/ExternalLogoutEnabled | Aktiviert oder deaktiviert die verbundbasierte Abmeldung. Wenn "true" festgelegt ist, werden Benutzer zur verbundbasierten Abmeldeoberfläche weitergeleitet, wenn sie sich vom Portal abmelden. Wenn "false" festgelegt ist, werden Benutzer nur vom Portal abgemeldet. Standardmäßig ist dies auf "false" gesetzt.               |
| Authentication/LoginTrackingEnabled                                  | Aktiviert oder deaktiviert die Nachverfolgung der letzten Anmeldung des Benutzers. Wenn "true" festgelegt ist, werden das Datum und die Uhrzeit im Feld **Letzte erfolgreiche Anmeldung** auf dem Kontaktdatensatz angezeigt. Standardmäßig ist dies auf "false" gesetzt.                                                            |
| Authentication/OpenIdConnect/[Federation-Name]/RegistrationEnabled   | Aktiviert oder deaktiviert die Registrierungsanforderung für den vorhandenen Identitätsanbieter. Wenn "true" festgelegt ist, wird die Registrierung für den vorhandenen Anbieter nur aktiviert, wenn für die Websiteeinstellung Authentication/Registration/Enabled auch "true" festgelegt ist. Standardmäßig ist dies auf "true" gesetzt. |
|Authentication/OpenIdConnect/[Federation-Name]/PostLogoutRedirectUri |Gibt die URL innerhalb des Portals an, zu der ein Benutzer nach der Abmeldung weitergeleitet wird. |
| | |

### <a name="related-content-snippet"></a>Zugehöriger Inhaltsausschnitt

Wenn die Registrierung für einen Benutzer deaktiviert wird, nachdem der Benutzer eine Einladung eingelöst hat, können Sie mithilfe des folgenden Inhaltsausschnitts eine Meldung anzeigen:

**Name**: Account/Register/RegistrationDisabledMessage

**Wert**: Registrierung wurde deaktiviert.

## <a name="customize-the-includeazureincludespn-azure-shortestmd-ad-b2c-user-interface"></a>Anpassen der [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C-Benutzeroberfläche

[!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C unterstützt die Anpassung der Benutzeroberfläche. Sie können die Benutzeroberfläche für Anmelde- und Abmeldeszenarien anpassen.

### <a name="step-1-create-a-web-template"></a>Schritt 1: Erstellen einer Webvorlage
Erstellen Sie eine Webvorlage, indem Sie die folgenden Werte verwenden:

**Name**: benutzerdefinierte [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C-Seite

**Quelle**: Verwenden Sie die folgende Beispiel-Webvorlagen-Quell-HTML.

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
### <a name="step-2-create-a-page-template"></a>Schritt 2: Erstellen einer Seitenvorlagen

Erstellen Sie die folgende Seitenvorlage:
- **Name**: benutzerdefinierte [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C-Seite
- **Typ**: Webvorlage
- **Webvorlage**: benutzerdefinierte [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C-Seite
- **Kopf- und Fußzeile der Website verwenden**: Deaktivieren Sie dieses Kontrollkästchen.

### <a name="step-3-create-a-webpage"></a>Schritt 3: Erstellen einer Webseite

Erstellen Sie die folgende Webseite:
- **Name**: Anmelden
- **Übergeordnete** Seite: Startseite
- **Teil-URL**: azure-ad-b2c-sign-in
- **Seitenvorlage**: benutzerdefinierte [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C-Seite
- **Veröffentlichungsstatus**: Veröffentlicht

### <a name="step-4-create-site-settings"></a>Schritt 4: Erstellen von Websiteeinstellungen

Websiteeinstellungen sind erforderlich, um die ursprungsübergreifende Ressourcenfreigabe (Cross-Origin Resource Sharing, CORS) zu konfigurieren, damit [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C die benutzerdefinierte Seite anfordern und die Anmelde- oder Registrierungsbenutzeroberfläche einfügen kann. Erstellen Sie die folgenden Websiteeinstellungen.

| Name                              | Wert                             |
|-----------------------------------|-----------------------------------|
| HTTP/Access-Control-Allow-Methods | GET, OPTIONEN                      |
| HTTP/Access-Control-Allow-Origin  | `https://login.microsoftonline.com` |
| | |

Eine vollständige Liste mit weiteren CORS-Einstellungen finden Sie unter [CORS-Protokollunterstützung](../add-web-resource.md#cors-protocol-support).

### <a name="step-5-includeazureincludespn-azure-shortestmd-configuration"></a>Schritt 5: [!include[Azure](../../../includes/pn-azure-shortest.md)]-Konfiguration

1. Melden Sie sich bei Ihrem [!include[Azure portal](../../../includes/pn-azure-portal.md)] an.
2. Navigieren Sie zum Blatt **[!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C-Mandantenverwaltung**.
3. Navigieren Sie zu **Einstellungen** > **Registrierungs- oder Anmelderichtlinien**. Eine Liste der verfügbaren Richtlinien wird angezeigt.
4. Wählen Sie die Richtlinie aus, die Sie bearbeiten möchten.
5. Wählen Sie **Bearbeiten** aus.
6. Wählen Sie **Richtlinie bearbeiten** > **Seite für die Benutzeroberflächenanpassung** > **Einheitliche Seite für Registrierung oder Anmeldung** aus.
7. Legen Sie für **Benutzerdefinierte Seite verwenden** **Ja** fest.
8. Legen Sie für **Benutzerdefinierter Seiten-URI** die URL der Webseite der benutzerdefinierten [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C-Seite fest, die in Schritt 3 dieses Verfahrens erstellt wurde. Zum Beispiel: `https://mydomain.com/azure-ad-b2c-sign-in`.
9. Wählen Sie **OK** aus.

## <a name="claims-mapping"></a>Anspruchszuordnung

Wenn Benutzer sich anmelden, entweder zum ersten Mal oder später, stellt der verbundbasierte Identitätsanbieter basierend auf seiner Datenbank hinsichtlich der Anmeldungen der Benutzer Ansprüche bereit. Diese Ansprüche sind im Identitätsanbieter konfigurierbar.

### <a name="includeazureincludespn-azure-shortestmd-ad-b2c-email-claims"></a>[!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C-E-Mail-Ansprüche

[!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C sendet den E-Mail-Anspruch als Sammlung. Das Portal nimmt die erste E-Mail-Adresse, die in der Sammlung bereitgestellt wird, als die primäre E-Mail-Adresse der Kontaktperson an.

### <a name="claims-to-support-sign-up-scenarios"></a>Ansprüche zur Unterstützung von Registrierszenarien

Wenn ein neuer Kunde, der in Common Data Service nicht vorhanden ist, bereitgestellt wird, können die eingehenden Ansprüche verwendet werden, um den neuen Kontaktdatensatz zu seeden, den das Portal erstellen wird. Allgemeine Ansprüche können den Vor- und Nachnamen, die E-Mail-Adresse und die Telefonnummer enthalten, sie sind jedoch konfigurierbar. Die folgende Websiteeinstellung ist erforderlich:

**Name**: Authentication/OpenIdConnect/[Federation-Name]/RegistrationClaimsMapping

**Beschreibung**: Liste mit Paaren von logischen Namen und Ansprüchen, die verwendet werden können, um Anspruchswerte Attributen im Kontaktdatensatz zuzuordnen, der während der Registrierung erstellt wurde.

**Format**: attribute1=claim1,attribute2=claim2,attribute3=claim3

Beispielsweise ist das name<https://schemas.xmlsoap.org/ws/2005/05/identity/claims/givenname,lastname=https://schemas.xmlsoap.org/ws/2005/05/identity/claims/surname,jobtitle=jobTitle>

> [!NOTE]
> Stellen Sie sicher, dass Sie die E-Mail-Adresse der primären E-Mail-Adresse (emailaddress1) des Kontakts zuordnen. Wenn Sie eine sekundäre E-Mail-Adresse (emailaddress2) oder eine alternative E-Mail-Adresse (emailaddress3) im Kontaktdatensatz hinzugefügt haben und sie der E-Mail-Adresse zugeordnet haben, werden dem Kontakt keine Identitätsinformationen hinzugefügt und es wird ein neuer Kontakt mit der E-Mail-Adresse erstellt, die für die Registrierung verwendet wurde und die durch die primäre E-Mail-Adresse (emailaddress1) festgelegt ist.

### <a name="claims-to-support-sign-in-scenarios"></a>Ansprüche zur Unterstützung von Anmeldeszenarien

Die Daten in Common Data Service und im Identitätsanbieter werden nicht direkt zugeordnet, sodass die Daten möglicherweise die Synchronisierung verlieren. Dieses Portal sollte eine Liste von Ansprüchen enthalten, die Sie in einer beliebigen Anmeldungsereignis annehmen möchten, um in Common Data Service zu aktualisieren. Diese Ansprüche können eine Teilmenge oder gleich der Berechtigungen sein, die von einem Anmeldeszenario hereinkommen. Dies muss unabhängig von der Zuordnung der Anmeldeansprüche konfiguriert werden, da Sie vielleicht einige Schlüsselportalattribute nicht überschreiben möchten. Die folgende Websiteeinstellung ist erforderlich:

**Name**: Authentication/OpenIdConnect/[Federation-Name]/LoginClaimsMapping

**Beschreibung**: Liste mit Paaren von logischen Namen und Ansprüchen, die verwendet werden können, um Anspruchswerte Attributen im Kontaktdatensatz zuzuordnen, der nach der Anmeldung erstellt wurde.

**Format**: attribute1=claim1, attribute2=claim2, attribute3=claim3

Beispielsweise ist das name<https://schemas.xmlsoap.org/ws/2005/05/identity/claims/givenname,lastname=https://schemas.xmlsoap.org/ws/2005/05/identity/claims/surname,jobtitle=jobTitle> 

Der Anspruchsname ist das Feld ANSPRUCHSTYP, das neben dem Attribut in den Anwendungsansprüchen der Anmelderichtlinien aufgeführt ist.

### <a name="allow-auto-association-to-a-contact-record-based-on-email"></a>Zulassen der automatischen Zuordnung zu einem Kontaktdatensatz auf Grundlage der E-Mail-Adresse 

Kunden, die Kontaktdatensätze mit verknüpften E-Mail-Adressen aufweisen, können eine Website starten, bei der die externen Benutzer sich mit [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C über einen E-Mail-Validierungsmechanismus anmelden. Die neue Anmeldung sollte dem vorhandenen Kontaktdatensatz zugeordnet werden, anstatt einen doppelten Datensatz zu erstellen. Diese Funktion ordnet nur Kontakte erfolgreich zu, die keine aktive Identität aufweisen, und die E-Mail-Adresse muss eindeutig (nicht mit mehreren Kontaktdatensätzen verknüpft) sein. Die folgende Websiteeinstellung ist erforderlich:

**Name**: Authentication/[Protocol]/[Provider]/AllowContactMappingWithEmail

**Beschreibung**: Gibt an, ob Kontakte einer entsprechenden E-Mail-Adresse zugeordnet werden. Wenn "true" festgelegt ist, ordnet diese Einstellung einen Kontaktdatensatz einer entsprechenden E-Mail-Adresse zu und weist den externen Identitätsanbieter dann automatisch dem Kontakt zu, wenn der Benutzer sich erfolgreich angemeldet hat. Standardmäßig ist dies auf "false" gesetzt.
