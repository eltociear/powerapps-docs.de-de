---
title: Authentifizierungsidentität für ein Portal festlegen | MicrosoftDocs
description: Anleitungen zum Festlegen der Authentifizierungsidentität für ein Portal.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/18/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 2faab3a6f41bbcd9a239c52fb00ce27919347879
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2020
ms.locfileid: "2980316"
---
# <a name="set-authentication-identity-for-a-portal"></a>Eine Authentifizierungsidentität für ein Portal festlegen

Portale stellen die Authentifizierungsfunktionalität auf Basis der [ASP.NET-Identität](https://www.asp.net/identity)-API bereit. Die ASP.NET-Identität basiert wiederum auf dem [OWIN](https://www.asp.net/aspnet/overview/owin-and-katana)-Framework, das auch eine wichtigen Komponente des Authentifizierungssystems ist. Die bereitgestellten Dienste umfassen:

- Lokale Benutzeranmeldung (Benutzername und Kennwort)
- Externe Benutzeranmeldung durch Drittanbieter-Identitätsanbieter (Social-Anbieter)
- Zweistufige Authentifizierung per E-Mail
- Bestätigen der E-Mail-Adresse
- Kennwortwiederherstellung
- Einladungscodeanmeldung zur Registrierung vorgenerierter Kontaktdatensätze

> [!NOTE]
> Das Feld **Mobiltelefon bestätigt** im Portalkontaktformular der Kontaktentität dient derzeit keinem Zweck. Dieses Feld darf nur verwendet werden, wenn von Adxstudio Portals aktualisiert wird.

## <a name="requirements"></a>Anforderungen

Portale erfordern:

- Portal-Basis
- [!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)]-Identität
- [!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)]-Identitäts-Workflows – Lösungspakete

## <a name="authentication-overview"></a>Authentifizierungsübersicht

Zurückkehrende Portalbesucher können sich über lokale Benutzeranmeldeinformationen oder externe Identitätsanbieterkonten authentifizieren. Ein neuer Besucher kann ein neues Benutzerkonto registrieren, indem er einen Benutzernamen und ein Kennwort angibt oder sich über einen externen Anbieter anmeldet. Besucher, die einen Einladungscode erhalten haben (durch den Portaladministrator), können den Code bei der Anmeldung für ein neues Benutzerkonto nutzen.

**Zugehörige Websiteeinstellungen:**

- `Authentication/Registration/Enabled`
- `Authentication/Registration/LocalLoginEnabled`
- `Authentication/Registration/ExternalLoginEnabled`
- `Authentication/Registration/OpenRegistrationEnabled`
- `Authentication/Registration/InvitationEnabled`
- `Authentication/Registration/RememberMeEnabled`
- `Authentication/Registration/ResetPasswordEnabled`

### <a name="sign-in-by-using-a-local-identity-or-external-identity"></a>Anmeldung mit einer lokalen oder externen Identität

![Mit einem lokalen Konto anmelden](../media/sign-in-local-account.png "Mit einem lokalen Konto anmelden")  

### <a name="sign-up-by-using-a-local-identity-or-external-identity"></a>Registrierung mit einer lokalen oder externen Identität

![Für ein neues lokales Konto registrieren](../media/register-new-local-account.png "Für ein neues lokales Konto registrieren")  

### <a name="redeem-an-invitation-code-manually"></a>Manuelles Einlösen eines Einladungscodes

![Mit Einladungscode registrieren](../media/sign-up-invitation-code.png "Mit Einladungscode registrieren")  

## <a name="forgot-password-or-password-reset"></a>Kennwort vergessen oder Kennwortzurücksetzung 

Zurückkehrende Benutzer, die eine Kennwortzurücksetzung benötigen (und bereits zuvor eine E-Mail-Adresse für ihr Benutzerprofil angegeben haben), können das Senden eines Kennwortzurücksetzungstokens an ihr E-Mail-Konto anfordern. Ein Zurücksetzungstoken ermöglicht es dem Besitzer, ein neues Kennwort zu wählen. Alternativ kann das Token verworfen werden. So bleibt das ursprüngliche Kennwort des Benutzers unverändert.

**Zugehörige Websiteeinstellungen:**

- `Authentication/Registration/ResetPasswordEnabled`
- `Authentication/Registration/ResetPasswordRequiresConfirmedEmail`

**Verwandter Prozess**: Kennwortrücksetzung an Kontakt senden

1.  Passen Sie die E-Mail nach Bedarf im Workflow an.
2.  Die E-Mail zum Start des Prozesses senden.
3.  Der Besucher wird zur Überprüfung der E-Mail aufgefordert.
4.  Der Besucher empfängt die Kennwortrücksetzungs-E-Mail mit Anleitungen.
5.  Der Besucher kehrt zum Rücksetzungsformular zurück.
6.  Das Rücksetzungskennwort ist vollständig.

## <a name="redeem-an-invitation"></a>Eine Einladung einlösen

Das Einlösen eines Einladungscodes ermöglicht die Zuordnung eines registrierenden Besuchers zu einem vorhandenen Kontakt, der im voraus für den Besucher Vorbereitung wurde. Üblicherweise werden die Einladungscodes per E-Mail versendet. Für Code, die über andere Kanäle gesendet werden, steht jedoch ein allgemeines Codesendungsformular zur Verfügung. Nachdem ein gültiger Einladungscode gesendet wurde, findet der normale Prozess der Benutzerregistrierung statt, um das neue Benutzerkonto einzurichten.

**Zugehörige Websiteeinstellungen:**

`Authentication/Registration/InvitationEnabled`

**Verwandter Prozess**: Einladung senden

Die E-Mail, die durch den Workflow gesendet wird, muss mit der URL für die Einladungseinlöseseite im Portal angepasst werden: https://portal.contoso.com/register/?returnurl=%2f&invitation={Invitation Code(Einladung)}

1. Erstellen einer Einladung für einen neuen Kontakt.

    ![Erstellen einer Einladung für einen neuen Kontakt](../media/create-invitation.png "Erstellen einer Einladung für einen neuen Kontakt")  

2. Anpassen und Speichern der neuen Einladung.

    ![Eine neue Einladung anpassen](../media/customize-new-invitation.png "Eine neue Einladung anpassen")  

3. Prozess: Einladung senden
4. Passen Sie die Einladungs-E-Mail an.
5. Die Einladungs-E-Mail öffnet die Einlösungsseite.
6. Der Benutzer registriert sich mithilfe des übermittelten Einladungscodes.

    ![Mit Einladungscode registrieren](../media/sign-up-invitation-code.png "Mit Einladungscode registrieren")  

## <a name="manage-user-accounts-through-profile-pages"></a>Benutzerkonten durch Profilseiten verwalten

Authentifizierte Benutzer verwalten ihre Benutzerkonten über die Navigationsleiste **Sicherheit** der Profilseite. Benutzer sind nicht auf das einzelne lokale oder externe Konto eingeschränkt, das sie zur Registrierungszeit wählen. Benutzer mit einem externen Konto können ein lokales Konto erstellen, indem sie einen Benutzernamen und ein Kennwort verwenden. Benutzer, die mit einem lokalen Konto begonnen haben, können mehrere externe Identitäten zu ihrem Konto zuordnen. Auf der Profilseite wird der Benutzer außerdem daran erinnert, seine E-Mail-Adresse zu bestätigen, indem eine Bestätigungs-E-Mail an das Konto gesendet wird.

**Zugehörige Websiteeinstellungen:**

- `Authentication/Registration/LocalLoginEnabled`
- `Authentication/Registration/ExternalLoginEnabled`
- `Authentication/Registration/TwoFactorEnabled`

## <a name="set-or-change-a-password"></a>Ein Kennwort festlegen oder ändern

Ein Benutzer mit einem vorhandenen lokalen Konto kann ein neues Kennwort festlegen, indem er das ursprüngliche Kennwort eingibt. Ein Benutzer ohne lokales Konto kann einen Benutzernamen und ein Kennwort wählen, um ein neues lokales Konto einzurichten. Der Benutzername kann nicht mehr geändert werden.

**Zugehörige Websiteeinstellungen:**

`Authentication/Registration/LocalLoginEnabled`

**Entsprechender Prozess:**
- Erstellen Sie einen Benutzernamen und ein Kennwort.
- Ändern Sie ein vorhandenes Kennwort.

## <a name="confirm-an-email-address"></a>Eine E-Mail-Adresse bestätigen

Das Ändern einer E-Mail-Adresse (bzw. das erstmalige Festlegen) führt dazu, dass sie den Status „Nicht bestätigt” erhält. Der Benutzer kann eine Bestätigungs-E-Mail an die neue E-Mail-Adresse anfordern. Diese enthält Anweisungen an den Benutzer für das Abschließen des E-Mail-Bestätigungsprozesses.

**Verwandter Prozess**: Eine E-Mail-Bestätigung an einen Kontakt senden

1. Passen Sie die E-Mail nach Bedarf im Workflow an. 
2. Der Benutzer sendet eine neue E-Mail-Nachricht, die in einem unbestätigten Status ist.
3. Der Benutzer überprüft die E-Mail zur Bestätigung.
4. Prozess: E-Mail-Bestätigung an Kontakt senden
5. Passen Sie die Bestätigungs-E-Mail an.
6. Der Benutzer klickt auf den Bestätigungslink, um den Bestätigungsprozess abzuschließen.

> [!NOTE]
> Stellen Sie sicher, dass die primäre E-Mail für den Kontakt angegeben ist, da die Bestätigungs-E-Mail nur an die primäre E-Mail-Adresse (emailaddress1) des Kontakts gesendet wird. Die Bestätigungs-Mail wird nicht an die sekundäre (emailaddress2) oder alternative E-Mail-Adresse (emailaddress3) des Kontaktdatensatzes gesendet.

## <a name="enable-two-factor-authentication"></a>Zweistufige Authentifizierung aktivieren

Die zweistufige Authentifizierung verbessert die Sicherheit von Benutzerkonten, da der Besitz der bestätigten E-Mail-Adresse nachgewiesen werden muss, zusätzlich zur Standardanmeldung über ein lokales oder externes Konto. Einem Benutzer, der sich mit einem Konto mit aktivierter zweistufigen Authentifizierung anmeldet, wird ein Sicherheitscode zur Bestätigung an die E-Mail-Adresse gesendet, die dem Konto zugeordnet ist. Der Sicherheitscode muss gesendet werden, um den Anmeldungsprozess abzuschließen. Ein Benutzer kann festlegen, dass der Browser die erfolgreiche Überprüfung speichert. So muss der Sicherheitscode bei nachfolgenden Anmeldungen über denselben Browser nicht mehr eingegeben werden. Diese Funktion wird für jedes Benutzerkonto einzeln aktiviert und erforderlich jeweils eine Bestätigung per E-Mail.

> [!WARNING]
> Wenn Sie die Websiteeinstellung mit dem Namen **Authentication/Registration/MobilePhoneEnabled** erstellen und aktivieren, um die Vorgängerfunktion zu aktivieren, tritt ein Fehler auf. Diese Standortseinstellung wird nicht standardmäßig bereitgestellt und nicht von den Portalen unterstützt.

**Zugehörige Websiteeinstellungen:**

- `Authentication/Registration/TwoFactorEnabled`
- `Authentication/Registration/RememberBrowserEnabled`

**Verwandter Prozess**: Zweistufigen E-Mail-Code an Kontakt senden

1. Aktivieren Sie die zweistufige Authentifizierung.
2. Auswählen des Empfangs des Sicherheitscodes per E-Mail.
3. Warten Sie auf die E-Mail, die den Sicherheitscode enthält.
4. Prozess: Zweistufigen E-Mail-Code an Kontakt senden
5. Die zweistufige Authentifizierung kann deaktiviert werden.

## <a name="manage-external-accounts"></a>Verwalten von externen Konten

Ein authentifizierter Benutzer verbindet (registriert) möglicherweise mehrere externe Identitäten mit seinem Benutzerkonto, eine von jedem des konfigurierten Identitätsanbieters. Nachdem die Identitäten verbunden sind, kann sich der Benutzern mit jeder der verbundenen Identitäten anmelden. Vorhandene Identitäten können auch getrennt werden, solange eine externe oder lokale Identität vorhanden bleibt.

**Zugehörige Websiteeinstellungen:**

- `Authentication/Registration/ExternalLoginEnabled`

**Website-Einstellungen für externen Identitätsanbieter**

1.  Wählen Sie einen Provider aus, um ihn mit Ihrem Benutzerkonto zu verbinden.

    ![Verwalten von externen Konten](../media/manage-external-accounts.png "Verwalten von externen Konten")  

2.  Melden Sie sich an, indem Sie den Anbieter verwenden, den Sie verbinden möchten.

Der Anbieter ist jetzt verbunden. Der Anbieter kann auch getrennt werden.

## <a name="enable-aspnet-identity-authentication"></a>ASP.NET-Identitätsauthentifizierung aktivieren

Folgendes beschreibt die Einstellungen zum Aktivieren/Deaktivieren verschiedener Authentifizierungsfunktionen und -verhalten:


|                        Website-Einstellungsname                        |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  Beschreibung                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
|-----------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|          Authentication/Registration/LocalLoginEnabled          |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     Aktiviert oder deaktiviert die Anmeldung über lokale Konto mit Benutzername (oder E-Mail) und Kennwort. Standard: false                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|          Authentication/Registration/LocalLoginByEmail          |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               Aktiviert oder deaktiviert die lokale Anmeldung über ein E-Mail-Adressen-Feld anstelle eines Benutzernamenfelds. Standard: false                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
|        Authentication/Registration/ExternalLoginEnabled         |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  Aktiviert oder deaktiviert die externe Anmeldung und Registrierung. Standard: true                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|          Authentication/Registration/RememberMeEnabled          |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          Aktivieren oder deaktivieren einer "Angemeldet bleiben"-Kontrollkästchen bei der lokalen Anmeldung über das authentifizierte Sitzungen auch nach dem Schließen des Webbrowsers dauerhaft erhalten bleiben. Standard: true                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|          Authentication/Registration/TwoFactorEnabled           |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        Aktiviert oder deaktiviert die Option für die zweistufige Authentifizierung. Benutzer mit einer bestätigten E-Mail-Adresse können die zweistufige Authentifizierung nutzen, um zusätzliche Sicherheit zu erhalten. Standard: false                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
|       Authentication/Registration/RememberBrowserEnabled        |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                Aktivieren oder deaktivieren einer "Angemeldet bleiben"-Kontrollkästchen zur Überprüfung der zweiten Stufe (E-Mail-Code), damit die Überprüfung der zweiten Stufe für den aktuellen Browser beibehalten wird. Der Benutzer muss die Überprüfung der zweiten Stufe nicht für nachfolgende Anmeldungen übergeben, solange derselbe Browser verwendet wird. Standard: true                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
|        Authentication/Registration/ResetPasswordEnabled         |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         Aktiviert oder deaktiviert die Kennwortrücksetzungsfunktion. Standard: true                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| Authentication/Registration/ResetPasswordRequiresConfirmedEmail |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               Aktiviert oder deaktiviert die Kennwortrücksetzung nur für bestätigte E-Mail-Adressen. Wenn aktiviert können unbestätigte E-Mail-Adressen nicht für Kennwortrücksetzungsanweisungen verwendet werden. Standard: false                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
|   Authentication/Registration/TriggerLockoutOnFailedPassword    |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          Aktiviert oder deaktiviert die Aufzeichnung fehlgeschlagener Kennwortversuche. Wenn deaktiviert, werden keine Benutzerkonten gesperrt. Standard: true                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|             Authentication/Registration/IsDemoMode              |                                                                                                                                                                                                                                                                                                                                                                                                                                                                          Aktiviert oder deaktiviert eine Kennzeichnung für eine Demonstrationsumgebung, die nur in Entwicklungs- oder Demoumgebungen verwendet wird. Aktivieren Sie diese Einstellung nicht in der Produktionsumgebung. Der Demomodus erfordert, dass der Webbrowser lokal auf dem Webanwendungsserver ausgeführt wird. Wenn der Demomodus aktiviert ist, werden der Kennwortrücksetzungscode und der Code für die zweistufige Authentifizierung zum schnelleren Zugriff für den Benutzer angezeigt. Standard: false                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|    Authentication/Registration/LoginButtonAuthenticationType    | Wenn ein Portal nur einen einzigen externen Identitätsanbieter erfordert (für die Authentifizierung), dann sorgt diese Option dafür, dass die **Anmeldungsschaltfläche** in der Kopfnavigationsleiste direkt auf die Anmeldeseite des externen Identitätsanbieters verweist (statt auf ein zwischengeschaltetes Anmeldungsformular und eine Seite zur Auswahl des Identitätsanbieters zu verweisen). Nur ein einzelner Identitätsanbieter kann für diese Aktion ausgewählt werden. Geben Sie den [AuthenticationType](https://msdn.microsoft.com/library/microsoft.owin.security.authenticationoptions.authenticationtype.aspx)-Wert des Anbieters an.<br>Für die Konfiguration einer einmaligen Anmeldung mittels OpenIdConnect, beispielsweise Azure Active Directory B2C, müssen Benutzer die Autorität bereitstellen.<br>Die akzeptierten Werte für OAuth2-basierte Anbieter sind: `Facebook, Google, Yahoo, [!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)], LinkedIn, Yammer,` oder `Twitter`<br>Für WS-Federation basierte Anbieter verwenden Sie den Wert, der für die Websiteeinstellungen `Authentication/WsFederation/ADFS/AuthenticationType` und `Authentication/WsFederation/[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]/\[provider\]/AuthenticationType` angegeben ist. Beispiele: https://adfs.contoso.com/adfs/services/trust, Facebook-0123456789, Google, Yahoo!, URI:[!INCLUDE[pn-ms-windows-short](../../../includes/pn-ms-windows-short.md)]LiveID. |
|                                                                 |                                                                                                                                                                                                                                                                                                  |

## <a name="enable-or-disable-user-registration"></a>Aktivieren oder Deaktivieren der Benutzerregistrierung

Folgendes beschreibt die Einstellungen zur Aktivierung und Deaktivierung der Benutzerregistrierungs-(Anmelde)-Optionen:

| Website-Einstellungsname                                   | Beschreibung                                                                                                                                                                             |
|-----------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Authentication/Registration/Enabled                 | Aktiviert oder deaktiviert alle Formulare für die Benutzerregistrierung. Die Registrierung für die anderen Einstellungen aktiviert sein, damit dieser Abschnitt aktiv wird. Standard: true                                   |
| Authentication/Registration/OpenRegistrationEnabled | Aktiviert oder deaktiviert Registrierungsformular zum Erstellen neuer lokaler Benutzer. Das Registrierungsformular ermöglicht jedem Besucher die Erstellung eines neuen Benutzerkontos. Standard: true |
| Authentication/Registration/InvitationEnabled       | Aktiviert oder deaktiviert Einladungscode-Einlösungsformular zur Registrierung von Benutzern mit Einladungscode. Standard: true                                                               |
|Authentication/Registration/CaptchaEnabled|Aktiviert oder deaktiviert Captcha auf der Benutzerregistrierungsseite. Standard: false<br>**Hinweis**: Diese Standortseinstellung Möglicherweise standardmäßig nicht verfügbar. Um dieses Feature zu aktivieren, müssen Sie die Standorteinstellung KnowledgeManagement/DisplayNotes erstellen und den Wert auf true festlegen. |
||

> [!NOTE]
> Stellen Sie sicher, dass die primäre E-Mail für den Benutzer angeben ist, da der Registrierung mit der primären E-Mail-Adresse(emailaddress1) des Benutzers erfolgt. Der Benutzer kann nicht mit einer sekundären E-Mail-Adresse (emailaddress2) oder alternativem E-Mail-Adresse (emailaddress3) des Kontaktdatensatzes angemeldet werden.

## <a name="user-credential-validation"></a>Benutzeranmeldeinformationsüberprüfung

Folgendes beschreibt die Einstellungen zur Anpassung von Benutzernamen- und Kennwortüberprüfungsparametern. Die Überprüfung tritt auf, wenn sich Benutzer mit einem lokalen Konto anmelden oder ein Kennwort ändern.

| Website-Einstellungsname                                                       | Beschreibung                                                                                                                                                                                         |
|-------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Authentication/UserManager/PasswordValidator/EnforcePasswordPolicy      | Ob das Kennwort Zeichen aus drei der folgenden Kategorien enthält:<br><ul><li>Großbuchstaben der Europäischen Sprachen (A bis Z mit diakritischen, griechischen und kyrillischen Zeichen)</li><li>Kleinbuchstaben der Europäischen Sprachen (a bis z, scharfes s mit diakritischen, griechischen und kyrillischen Zeichen)</li><li>Base 10-Ziffern (0 bis 9)</li><li>Nicht alphanumerische Zeichen (Sonderzeichen) (zum Beispiel: !, $, \#, %)</li></ul>Standard: true. Weitere Information: [Kennwortrichtlinie](https://technet.microsoft.com/library/hh994562(v=ws.10).aspx).                                                                                                           |  
| Authentication/UserManager/UserValidator/AllowOnlyAlphanumericUserNames | Ob nur alphanumerische Zeichen für den Benutzernamen zugelassen sind. Standard: false. Weitere Informationen: [UserValidator<TUser, TKey>.AllowOnlyAlphanumericUserNames](https://msdn.microsoft.com/library/dn613211.aspx).                                                          |  
| Authentication/UserManager/UserValidator/RequireUniqueEmail             | Ob eine eindeutige E-Mail-Adresse zum Überprüfen des Benutzers erforderlich ist. Standard: true. Weitere Informationen: [UserValidator<TUser, TKey>.RequireUniqueEmail](https://msdn.microsoft.com/library/dn613213.aspx).                                                                   |  
| Authentication/UserManager/PasswordValidator/RequiredLength             | Die minimale Kennwortlänge. Standard: 8 Weitere Informationen: [PasswordValidator.RequiredLength](https://msdn.microsoft.com/library/microsoft.aspnet.identity.passwordvalidator.requiredlength.aspx).                                       |  
| Authentication/UserManager/PasswordValidator/RequireNonLetterOrDigit    | Ob das Kennwort nicht alphanumerische Zeichen oder Zahlen erfordert. Standard: false. Weitere Informationen: [PasswordValidator.RequireNonLetterOrDigit](https://msdn.microsoft.com/library/microsoft.aspnet.identity.passwordvalidator.requirenonletterordigit.aspx). |  
| Authentication/UserManager/PasswordValidator/RequireDigit               | Ob das Kennwort ein Zahlen erfordert (von 0 bis 9). Standard: false. Weitere Informationen: [PasswordValidator.RequireDigit](https://msdn.microsoft.com/library/microsoft.aspnet.identity.passwordvalidator.requiredigit.aspx).                |  
| Authentication/UserManager/PasswordValidator/RequireLowercase           | Ob das Kennwort einen Kleinbuchstaben erfordert (von a bis z). Standard: false. Weitere Informationen: [PasswordValidator.RequireLowercase](https://msdn.microsoft.com/library/microsoft.aspnet.identity.passwordvalidator.requirelowercase.aspx).        |  
| Authentication/UserManager/PasswordValidator/RequireUppercase           | Ob das Kennwort einen Großbuchstaben erfordert (von A bis Z). Standard: false. Weitere Informationen: [PasswordValidator.RequireUppercase](https://msdn.microsoft.com/library/microsoft.aspnet.identity.passwordvalidator.requireuppercase.aspx).       | 
|| 

## <a name="user-account-lockout-settings"></a>Einstellung für die Sperrung von Benutzerkonten

Folgendes beschreibt die Einstellungen, mit denen definiert wird, wann und wie ein Konto für die Authentifizierung gesperrt wird. Falls eine bestimmte Anzahl fehlgeschlagener Anmeldeversuche in einem kurzen Zeitraum erkannt wird, wird das Benutzerkonto für einen bestimmten Zeitraum gesperrt. Nach diesem Zeitraum kann der Benutzer erneut eine Anmeldung ausführen.

| Website-Einstellungsname                                               | Beschreibung                                                                                                                                                                                                                                     |
|-----------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Authentication/UserManager/UserLockoutEnabledByDefault          | Gibt an, ob die Sperrung von Benutzer beim Erstellen von Benutzern aktiv ist. Standard: true. Weitere Informationen: [UserManager<TUser, TKey>.UserLockoutEnabledByDefault](https://msdn.microsoft.com/library/dn613214.aspx).                                                                                                  |  
| Authentication/UserManager/DefaultAccountLockoutTimeSpan        | Der Standardzeitraum für den eine Benutzer nach Erreichen von Authentication/UserManager/MaxFailedAccessAttemptsBeforeLockout ausgesperrt ist. Standard: 24:00:00 (1 Tag). Weitere Informationen: [UserManager<TUser, TKey>.DefaultAccountLockoutTimeSpan](https://msdn.microsoft.com/library/dn613201.aspx).                 |  
| Authentication/UserManager/MaxFailedAccessAttemptsBeforeLockout | Die maximale Anzahl der Zugriffsversuchen, bevor ein Benutzer gesperrt wird (sofern die Sperre aktiviert ist). Standard: 5 Weitere Informationen: [UserManager<TUser, TKey>.MaxFailedAccessAttemptsBeforeLockout](https://msdn.microsoft.com/library/dn613202.aspx).                                                                        |  
| Authentication/ApplicationCookie/ExpireTimeSpan                 | Der Standardzeitraum für die Gültigkeit der Cookieauthentifizierungssitzung. Standard: 24:00:00 (1 Tag). Weitere Informationen: [CookieAuthenticationOptions.ExpireTimeSpan](https://msdn.microsoft.com/library/microsoft.owin.security.cookies.cookieauthenticationoptions.expiretimespan(v=vs.113).aspx). |
||  

## <a name="cookie-authentication-site-settings"></a>Cookie-Authentifizierungswebsiteeinstellungen

Einstellungen zum Ändern des Standardauthentifizierungscookie-Verhaltens. Definiert durch die [CookieAuthenticationOptions](https://msdn.microsoft.com/library/microsoft.owin.security.cookies.cookieauthenticationoptions.aspx)-Klasse.

| Website-Einstellungsname   | Beschreibung       |
|----------------------|------------------------------------------------|
| Authentication/ApplicationCookie/AuthenticationType                      | Der Typ des Anwendungsauthentifizierungscookie. Standard: ApplicationCookie. Weitere Informationen: [AuthenticationOptions::AuthenticationType](https://msdn.microsoft.com/library/dn300391.aspx).  |
| Authentication/ApplicationCookie/CookieName                              | Bestimmt den Cookiename, der zur Beibehaltung der Identität verwendet wird. Standard: .AspNet.Cookies. Weitere Informationen: [CookieAuthenticationOptions::CookieName](https://msdn.microsoft.com/library/dn385537.aspx).  |
| Authentication/ApplicationCookie/CookieDomain                            | Bestimmt die Domäne, die verwendet wird, um das Cookie zu erstellen. Weitere Informationen: [CookieAuthenticationOptions::CookieDomain](https://msdn.microsoft.com/library/dn385536.aspx).  |
| Authentication/ApplicationCookie/CookiePath                              | Bestimmt den Pfad, der verwendet wird, um das Cookie zu erstellen. Standard: /. Weitere Informationen: [CookieAuthenticationOptions::CookiePath](https://msdn.microsoft.com/library/dn385539.aspx). |
| Authentication/ApplicationCookie/CookieHttpOnly                          | Bestimmt, ob der Browser zulassen soll, dass auf das Cookie durch clientseitiges JavaScript zugegriffen wird. Standard: true. Weitere Informationen: [CookieAuthenticationOptions::CookieHttpOnly](https://msdn.microsoft.com/library/dn385540.aspx).                     |
| Authentication/ApplicationCookie/CookieSecure                            | Bestimmt, ob das Cookie nur durch eine HTTPS-Anforderung übermittelt werden soll. Standard: SameAsRequest. Weitere Informationen: [CookieAuthenticationOptions::CookieSecure](https://msdn.microsoft.com/library/dn385538.aspx).  |
| Authentication/ApplicationCookie/ExpireTimeSpan                          | Steuert, für wie lange das Anwendungscookie ab dem Erstellungszeitpunkt gültig bleibt. Standard: 14 Tage. Weitere Informationen: [CookieAuthenticationOptions::ExpireTimeSpan](https://msdn.microsoft.com/library/microsoft.owin.security.cookies.cookieauthenticationoptions.expiretimespan(v=vs.113).aspx).  |
| Authentication/ApplicationCookie/SlidingExpiration                       | Die SlidingExpiration ist auf „true” festgelegt, um die Middleware anzuweisen, jedes Mal ein neues Cookie mit einem neuen Ablaufdatum erneut auszustellen, wenn sie eine Anforderung verarbeitet, die das Ablauffenster um mehr als die Hälfte durchlaufen hat. Standard: true. Weitere Informationen: [CookieAuthenticationOptions::SlidingExpiration](https://msdn.microsoft.com/library/dn385548.aspx). |
| Authentication/ApplicationCookie/LoginPath                               | Die LoginPath-Eigenschaft informiert die Middleware darüber, dass sie einen ausgehenden Statuscode „401 Nicht autorisiert” in eine 302-Umleitung zu dem angegebenen Anmeldepfad ändern soll. Standard: ~/signin. Weitere Informationen: [CookieAuthenticationOptions::LoginPath](https://msdn.microsoft.com/library/dn385541.aspx).                                            |
| Authentication/ApplicationCookie/LogoutPath                              | Wenn der LogoutPath der Middleware angegeben wird, dann wird eine Anforderung an diesen Pfad basierend auf dem ReturnUrlParameter umgeleitet. Weitere Informationen: [CookieAuthenticationOptions::LogoutPath](https://msdn.microsoft.com/library/dn385545.aspx).               |
| Authentication/ApplicationCookie/ReturnUrlParameter                      | Der ReturnUrlParameter bestimmt den Namen des Abfragezeichenfolgenparameters, der durch die Middleware angefügt wird, wenn ein Statuscode „401 Nicht autorisiert” in einen 302-Umleitungscode zum Anmeldepfad geändert wird. Weitere Informationen: [CookieAuthenticationOptions::ReturnUrlParameter](https://msdn.microsoft.com/library/dn385546.aspx).                           |
| Authentication/ApplicationCookie/SecurityStampValidator/ValidateInterval | Der Zeitraum zwischen Sicherheitsstempelüberprüfungen. Standard: 30 Minuten. Weitere Informationen: [SecurityStampValidator::OnValidateIdentity](https://msdn.microsoft.com/library/microsoft.aspnet.identity.owin.securitystampvalidator.onvalidateidentity.aspx).                    |
| Authentication/TwoFactorCookie/AuthenticationType                        | Der Typ des zweistufigen Authentifizierungscookie. Standard: TwoFactorCookie. Weitere Informationen: [AuthenticationOptions::AuthenticationType](https://msdn.microsoft.com/library/dn300391.aspx).            |
| Authentication/TwoFactorCookie/ExpireTimeSpan                            | Steuert, für wie lange das zweistufige Cookie ab dem Erstellungszeitpunkt gültig bleibt. Standard: 5 Minuten. Weitere Informationen: [CookieAuthenticationOptions::ExpireTimeSpan](https://msdn.microsoft.com/library/dn385543.aspx).     |
|||

### <a name="see-also"></a>Siehe auch

[Konfigurieren der Portalauthentifizierung](configure-portal-authentication.md)  
[OAuth2-Anbietereinstellungen für Portale](configure-oauth2-settings.md)  
[OpenID Connect-Anbietereinstellungen für Portale](configure-openid-settings.md)  
[WS-Federation-Anbietereinstellungen für Portale](configure-ws-federation-settings.md)  
[SAML 2.0-Anbietereinstellungen für Portale](configure-saml2-settings.md)  
