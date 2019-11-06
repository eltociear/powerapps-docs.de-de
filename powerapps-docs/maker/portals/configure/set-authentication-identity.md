---
title: Festlegen der Authentifizierungs Identität für ein Portal | MicrosoftDocs
description: Anweisungen zum Festlegen der Authentifizierungs Identität für ein Portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/18/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 44b45a019b786da01dc686ecb69f068ce1d7eef8
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73542675"
---
# <a name="set-authentication-identity-for-a-portal"></a>Festlegen der Authentifizierungs Identität für ein Portal

Portale bieten Authentifizierungsfunktionen, die auf der [ASP.net Identity](https://www.asp.net/identity) -API erstellt wurden. ASP.net Identity wird wiederum auf dem [owin](https://www.asp.net/aspnet/overview/owin-and-katana) -Framework erstellt, das auch eine wichtige Komponente des Authentifizierungssystems ist. Die bereitgestellten Dienste umfassen Folgendes:

- Lokale Anmeldung (Benutzername/Kennwort)
- Externe (Social Provider) Benutzeranmeldung über Identitäts Anbieter von Drittanbietern
- Zweistufige Authentifizierung mit e-Mail
- E-Mail-Adresse
- Kenn Wort Wiederherstellung
- Einladungscode Registrierung zum Registrieren von vorab generierten Kontaktdaten Sätzen

> [!NOTE]
> Das Feld " **Mobiltelefon bestätigt** " im Kontaktformular des Portals der Entität "Contact" hat derzeit keinen Zweck. Dieses Feld darf nur beim Upgrade von adxstudio-Portalen verwendet werden.

## <a name="requirements"></a>Anforderungen

Portale erfordern Folgendes:

- Portale (Basis)
- [!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)] Identität
- Lösungspakete für [!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)] Identitäts Workflows

## <a name="authentication-overview"></a>Authentifizierung (Übersicht)

Das Zurückgeben von Portal Besuchern kann sich mithilfe lokaler Benutzer Anmelde Informationen oder externer Identitäts Anbieter Konten authentifizieren. Ein neuer Besucher kann sich für ein neues Benutzerkonto registrieren, indem er entweder einen Benutzernamen und ein Kennwort bereitstellt oder sich über einen externen Anbieter anmeldet. Besucher, die einen Einladungscode (vom Portaladministrator) gesendet haben, haben die Möglichkeit, den Code bei der Registrierung für ein neues Benutzerkonto einzulösen.

**Verwandte Site Einstellungen:**

- `Authentication/Registration/Enabled`
- `Authentication/Registration/LocalLoginEnabled`
- `Authentication/Registration/ExternalLoginEnabled`
- `Authentication/Registration/OpenRegistrationEnabled`
- `Authentication/Registration/InvitationEnabled`
- `Authentication/Registration/RememberMeEnabled`
- `Authentication/Registration/ResetPasswordEnabled`

### <a name="sign-in-by-using-a-local-identity-or-external-identity"></a>Melden Sie sich mit einer lokalen Identität oder einer externen Identität an.

![Anmelden mit einem lokalen Konto](../media/sign-in-local-account.png "Anmelden mit einem lokalen Konto")  

### <a name="sign-up-by-using-a-local-identity-or-external-identity"></a>Registrieren mithilfe einer lokalen Identität oder einer externen Identität

![Registrieren Sie sich für ein neues lokales Konto.](../media/register-new-local-account.png "Registrieren Sie sich für ein neues lokales Konto.")  

### <a name="redeem-an-invitation-code-manually"></a>Manuelles Einlösen eines Einladungs Codes

![Registrieren mithilfe eines Einladungs Codes](../media/sign-up-invitation-code.png "Registrieren mithilfe eines Einladungs Codes")  

## <a name="forgot-password-or-password-reset"></a>Kennwort oder Kenn Wort Zurücksetzung vergessen 

Wenn Besucher zurückgegeben werden, die eine Kenn Wort Zurücksetzung benötigen (und zuvor eine e-Mail-Adresse in Ihrem Benutzerprofil angegeben haben), kann ein Token zum Zurücksetzen des Kennworts angefordert werden Mit einem Token zum Zurücksetzen kann der Besitzer ein neues Kennwort auswählen. Alternativ kann das Token abgebrochen werden, sodass das ursprüngliche Kennwort des Benutzers unverändert bleibt.

**Verwandte Site Einstellungen:**

- `Authentication/Registration/ResetPasswordEnabled`
- `Authentication/Registration/ResetPasswordRequiresConfirmedEmail`

**Verwandter Prozess:** Senden einer Kenn Wort Zurücksetzung an einen Kontakt

1.  Passen Sie die e-Mail-Adresse im Workflow nach Bedarf an.
2.  Senden Sie die e-Mail, um den Prozess aufzurufen.
3.  Der Besucher wird aufgefordert, eine e-Mail zu überprüfen.
4.  Der Besucher empfängt das Kennwort zum Zurücksetzen des Kennworts mit Anweisungen.
5.  Der Besucher kehrt zum Zurücksetzungs Formular zurück.
6.  Das Zurücksetzen des Kennworts ist fertiggestellt.

## <a name="redeem-an-invitation"></a>Einlösen einer Einladung

Durch das Einlösen eines Einladungs Codes kann ein registrierter Besucher einem vorhandenen Kontaktdaten Satz zugeordnet werden, der speziell für diesen Besucher vorbereitet wurde. In der Regel werden die Einladungs Codes per e-Mail gesendet, Sie können jedoch ein allgemeines Code Übermittlungs Formular verwenden, um Codes über andere Kanäle zu senden. Nachdem ein gültiger Einladungscode übermittelt wurde, wird der normale Benutzer Registrierungsvorgang (Registrierung) durchgeführt, um das neue Benutzerkonto einzurichten.

**Verwandte Site Einstellungen:**

`Authentication/Registration/InvitationEnabled`

**Verwandter Prozess:** Einladung senden

Die von diesem Workflow gesendete e-Mail muss angepasst werden, indem die URL zur Seite "einlösen" im Portal verwendet wird: https://portal.contoso.com/register/?returnurl=%2f&invitation={Invitation Code (Einladung)}

1. Erstellen Sie eine Einladung für einen neuen Kontakt.

    ![Eine Einladung für einen neuen Kontakt erstellen](../media/create-invitation.png "Eine Einladung für einen neuen Kontakt erstellen")  

2. Passen Sie die neue Einladung an, und speichern Sie Sie.

    ![Anpassen einer neuen Einladung](../media/customize-new-invitation.png "Anpassen einer neuen Einladung")  

3. Prozess: Einladung senden
4. Anpassen der Einladungs-e-Mail.
5. Die Einladungs-e-Mail öffnet die Seite einlösen.
6. Der Benutzer meldet sich mithilfe des übermittelten Einladungs Codes an.

    ![Registrieren mit einem Einladungscode](../media/sign-up-invitation-code.png "Registrieren mithilfe eines Einladungs Codes")  

## <a name="manage-user-accounts-through-profile-pages"></a>Verwalten von Benutzerkonten über Profilseiten

Authentifizierte Benutzer verwalten ihre Benutzerkonten über die Navigationsleiste **Sicherheit** der Seite Profil. Benutzer sind nicht auf das einzelne lokale Konto oder ein einzelnes externes Konto beschränkt, das Sie zum Zeitpunkt der Benutzerregistrierung ausgewählt haben. Benutzer mit einem externen Konto können ein lokales Konto erstellen, indem Sie einen Benutzernamen und ein Kennwort anwenden. Benutzer, die mit einem lokalen Konto gestartet haben, können auswählen, dass Ihrem Konto mehrere externe Identitäten zugeordnet werden sollen. Auf der Profilseite wird der Benutzer auch daran erinnert, seine e-Mail-Adresse zu bestätigen, indem eine Bestätigungs-e-Mail angefordert wird, die an das e-Mail-Konto

**Verwandte Site Einstellungen:**

- `Authentication/Registration/LocalLoginEnabled`
- `Authentication/Registration/ExternalLoginEnabled`
- `Authentication/Registration/TwoFactorEnabled`

## <a name="set-or-change-a-password"></a>Festlegen oder Ändern eines Kennworts

Ein Benutzer, der ein vorhandenes lokales Konto hat, kann ein neues Kennwort anwenden, indem er das ursprüngliche Kennwort bereitstellt. Ein Benutzer, der nicht über ein lokales Konto verfügt, kann einen Benutzernamen und ein Kennwort auswählen, um ein neues lokales Konto einzurichten. Der Benutzername kann nicht geändert werden, nachdem er festgelegt wurde.

**Verwandte Site Einstellungen:**

`Authentication/Registration/LocalLoginEnabled`

**Verwandter Prozess:**
- Erstellen Sie einen Benutzernamen und ein Kennwort.
- Ändern Sie ein vorhandenes Kennwort.

## <a name="confirm-an-email-address"></a>E-Mail-Adresse bestätigen

Wenn Sie eine e-Mail-Adresse ändern (oder zum ersten Mal festlegen), wird Sie in einen nicht bestätigten Zustand versetzt. Der Benutzer kann eine Bestätigungs-e-Mail anfordern, um an die neue e-Mail-Adresse gesendet zu werden, und die e-Mail enthält Anweisungen für den Benutzer, um den e-Mail-Bestätigungsprozess abzuschließen.

**Verwandter Prozess:** Senden einer e-Mail-Bestätigung an einen Kontakt

1. Passen Sie die e-Mail-Adresse im Workflow nach Bedarf an. 
2. Der Benutzer sendet eine neue e-Mail, die sich in einem nicht bestätigten Zustand befindet.
3. Der Benutzer überprüft die Bestätigung per e-Mail.
4. Prozess: e-Mail-Bestätigung an Kontakt senden
5. Anpassen der Bestätigungs-e-Mail.
6. Der Benutzer klickt auf den Bestätigungslink, um den Bestätigungs Vorgang abzuschließen.

> [!NOTE]
> Stellen Sie sicher, dass die primäre e-Mail-Adresse für den Kontakt angegeben ist, weil die Bestätigungs-e-Mail nur an die primäre e-Mail (EmailAddress1) des Kontakts gesendet wird. Die Bestätigungs-e-Mail wird nicht an die sekundäre e-Mail (EmailAddress2) oder an eine Alternative e-Mail-Adresse (EmailAddress3) des Kontaktdaten Satzes gesendet.

## <a name="enable-two-factor-authentication"></a>Aktivieren der zweistufigen Authentifizierung

Das Feature für die zweistufige Authentifizierung erhöht die Benutzerkonten Sicherheit, indem es zusätzlich zur Standardanmeldung für lokales oder externes Konto einen Nachweis des Besitzes einer bestätigten e-Mail erfordert. Ein Benutzer, der versucht, sich bei einem Konto anzumelden, für das die zweistufige Authentifizierung aktiviert ist, wird ein Sicherheitscode an die bestätigte e-Mail gesendet, die Ihrem Konto zugeordnet ist. Der Sicherheitscode muss übermittelt werden, um den Anmeldevorgang abzuschließen. Ein Benutzer kann sich entscheiden, den Browser zu merken, der die Überprüfung erfolgreich ausgeführt hat, sodass der Sicherheitscode für nachfolgende Anmeldungen desselben Browsers nicht erforderlich ist. Jedes Benutzerkonto aktiviert dieses Feature einzeln und erfordert eine bestätigte e-Mail-Adresse.

> [!WARNING]
> Wenn Sie die **Authentifizierungs-/Registrierungs-/mobilephoneaktivierte** Website Einstellung erstellen und aktivieren, um die Legacy-Funktionalität zu aktivieren, tritt ein Fehler auf. Diese Standort Einstellung wird nicht standardmäßig bereitgestellt und nicht von Portalen unterstützt.

**Verwandte Site Einstellungen:**

- `Authentication/Registration/TwoFactorEnabled`
- `Authentication/Registration/RememberBrowserEnabled`

**Verwandter Prozess:** Senden von zweistufiger e-Mail an einen Kontakt

1. Aktivieren Sie die zweistufige Authentifizierung.
2. Wählen Sie aus, ob der Sicherheitscode per e-Mail empfangen werden soll.
3. Warten Sie auf die e-Mail, die den Sicherheitscode enthält.
4. Prozess: senden Sie eine e-Mail mit zweistufiger Code an contact.
5. Die zweistufige Authentifizierung kann deaktiviert werden.

## <a name="manage-external-accounts"></a>Externe Konten verwalten

Ein authentifizierter Benutzer kann mehrere externe Identitäten mit Ihrem Benutzerkonto verbinden (registrieren), eines von jedem konfigurierten Identitäts Anbieter. Nachdem die Identitäten verbunden sind, kann der Benutzer sich anmelden, indem er eine der verbundenen Identitäten verwendet. Vorhandene Identitäten können auch getrennt werden, solange eine einzelne externe oder lokale Identität weiterhin besteht.

**Verwandte Site Einstellungen:**

- `Authentication/Registration/ExternalLoginEnabled`

**Website Einstellungen für externe Identitäts Anbieter**

1.  Wählen Sie einen Anbieter aus, um eine Verbindung mit Ihrem Benutzerkonto herzustellen.

    ![Externe Konten verwalten](../media/manage-external-accounts.png "Externe Konten verwalten")  

2.  Melden Sie sich mit dem Anbieter an, mit dem Sie eine Verbindung herstellen möchten.

Der Anbieter ist nun verbunden. Der Anbieter kann auch getrennt werden.

## <a name="enable-aspnet-identity-authentication"></a>Aktivieren der ASP.net-Identitäts Authentifizierung

Im folgenden werden die Einstellungen zum Aktivieren und deaktivieren verschiedener Authentifizierungs Features und Verhalten beschrieben:


|                        Name der Standort Einstellung                        |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  Beschreibung                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
|-----------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|          Authentifizierung/Registrierung/loczuordnung aktiviert          |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     Aktiviert oder deaktiviert die Anmeldung lokaler Konten auf der Grundlage eines Benutzernamens (oder einer e-Mail) und eines Kennworts. Standardwert: false                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|          Authentifizierung/Registrierung/locsorginbyemail          |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               Aktiviert oder deaktiviert die Anmeldung eines lokalen Kontos mit einem e-Mail-Adressfeld anstelle eines username-Felds. Standardwert: false                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
|        Authentifizierung/Registrierung/externzuweisung aktiviert         |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  Aktiviert oder deaktiviert die Anmeldung und Registrierung externer Konten. Standardwert: true                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|          Authentifizierung/Registrierung/Erinnerungs fähig          |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          Wird eine Erinnerung ausgewählt oder gelöscht? Aktivieren Sie das Kontrollkästchen bei der lokalen Anmeldung, um zuzulassen, dass authentifizierte Sitzungen beibehalten werden, auch wenn der Webbrowser geschlossen wird. Standardwert: true                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|          Authentifizierung/Registrierung/twofactoraktiviert           |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        Aktiviert oder deaktiviert die Option, mit der Benutzer die zweistufige Authentifizierung aktivieren können. Benutzer mit einer bestätigten e-Mail-Adresse können die zusätzliche Sicherheit der zweistufigen Authentifizierung wählen. Standardwert: false                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
|       Authentifizierung/Registrierung/Erinnerungs Browser aktiviert        |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                Einen Browser für die Erinnerung auswählen oder löschen? Aktivieren Sie das Kontrollkästchen für die zweistufige Überprüfung (e-Mail-Code), um die zweistufige Überprüfung für den aktuellen Browser beizubehalten. Der Benutzer ist nicht verpflichtet, die zweistufige Überprüfung für nachfolgende Anmeldungen zu übergeben, solange derselbe Browser verwendet wird. Standardwert: true                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
|        Authentifizierung/Registrierung/resetpasswordenabled         |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         Aktiviert oder deaktiviert das Feature zum Zurücksetzen des Kennworts. Standardwert: true                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| Authentifizierung/Registrierung/resetpasswordrequiresconfirmedemail |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               Aktiviert oder deaktiviert nur die Kenn Wort Zurücksetzung für bestätigte e-Mail-Adressen. Wenn diese Option aktiviert ist, können nicht bestätigte e-Mail-Adressen verwendet werden, um Anweisungen zum Zurücksetzen von Standardwert: false                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
|   Authentifizierung/Registrierung/triggerlockoutonfailedpassword    |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          Aktiviert oder deaktiviert das Aufzeichnen von fehlgeschlagenen Kenn Wort versuchen. Wenn diese Option deaktiviert ist, werden die Benutzerkonten nicht gesperrt. Standardwert: true                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|             Authentifizierung/Registrierung/isdemomode              |                                                                                                                                                                                                                                                                                                                                                                                                                                                                          Aktiviert oder deaktiviert ein demomodusflag, das nur in Entwicklungs-oder Demonstrations Umgebungen verwendet wird. Aktivieren Sie diese Einstellung nicht in Produktionsumgebungen. Der Demomodus erfordert auch, dass der Webbrowser lokal auf dem Webanwendungs Server ausgeführt wird. Wenn der Demomodus aktiviert ist, werden dem Benutzer der Code zum Zurücksetzen des Kennworts und der zweite Faktor Code angezeigt, um schnell darauf zugreifen zu können. Standardwert: false                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|    Authentifizierung/Registrierung/loginbuttonauthenticationtype    | Wenn für ein Portal nur ein einzelner externer Identitäts Anbieter erforderlich ist (um die gesamte Authentifizierung zu verarbeiten), kann die **Anmelde Schaltfläche** der Header Navigationsleiste direkt mit der Anmeldeseite dieses externen Identitäts Anbieters verknüpft werden (stattdessen mit dem zwischen die Auswahl Seite für das lokale Anmeldeformular und den Identitäts Anbieter). Für diese Aktion kann nur ein einziger Identitäts Anbieter ausgewählt werden. Geben Sie den [AuthenticationType](https://msdn.microsoft.com/library/microsoft.owin.security.authenticationoptions.authenticationtype.aspx) -Wert des Anbieters an.<br>Bei einer Single Sign-on Konfiguration mit openidconnect, wie z. b. der Verwendung von Azure Active Directory B2C, muss der Benutzer die Autorität bereitstellen.<br>Für OAuth2-basierte Anbieter sind folgende Werte zulässig: `Facebook, Google, Yahoo, [!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)], LinkedIn, Yammer,` oder `Twitter`<br>Verwenden Sie für WS-Verbund-basierte Anbieter den Wert, der für die `Authentication/WsFederation/ADFS/AuthenticationType`-und `Authentication/WsFederation/[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]/\[provider\]/AuthenticationType`-Standorteinstellungen angegeben ist. Beispiele: https://adfs.contoso.com/adfs/services/trust , Facebook-0123456789, Google, Yahoo!, URI:[!INCLUDE[pn-ms-windows-short](../../../includes/pn-ms-windows-short.md)] LiveID. |
|                                                                 |                                                                                                                                                                                                                                                                                                  |

## <a name="enable-or-disable-user-registration"></a>Aktivieren oder Deaktivieren der Benutzerregistrierung

Im folgenden werden die Einstellungen zum Aktivieren und Deaktivieren der Optionen für die Benutzerregistrierung (Registrierung) beschrieben:

| Name der Standort Einstellung                                   | Beschreibung                                                                                                                                                                             |
|-----------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Authentifizierung/Registrierung/aktiviert                 | Aktiviert oder deaktiviert alle Arten der Benutzerregistrierung. Die Registrierung muss aktiviert sein, damit die anderen Einstellungen in diesem Abschnitt wirksam werden. Standardwert: true                                   |
| Authentifizierung/Registrierung/openregistrationaktiviert | Aktiviert oder deaktiviert das Registrierungsformular für die Registrierung zum Erstellen neuer lokaler Benutzer. Das Registrierungsformular ermöglicht allen anonymen Besuchern des Portals, ein neues Benutzerkonto zu erstellen. Standardwert: true |
| Authentifizierung/Registrierung/invitationaktivierte       | Aktiviert oder deaktiviert das einlöseformular für Einladungscode zum Registrieren von Benutzern, die über Einladungs Codes verfügen. Standardwert: true                                                               |
|Authentifizierung/Registrierung/captchaaktivierte|Aktiviert oder deaktiviert CAPTCHA auf der Seite für die Benutzerregistrierung. Standardwert: false<br>**Hinweis**: diese Site Einstellung ist möglicherweise standardmäßig nicht verfügbar. Um Captcha zu aktivieren, müssen Sie die Website Einstellung erstellen und deren Wert auf "true" festlegen. |
||

> [!NOTE]
> Stellen Sie sicher, dass die primäre e-Mail-Adresse für den Benutzer angegeben ist, da die Registrierung über die primäre e-Mail (EmailAddress1) des Benutzers erfolgt. Der Benutzer kann nicht mithilfe der sekundären e-Mail-Adresse (EmailAddress2) oder der alternativen e-Mail (EmailAddress3) des Kontaktdaten Satzes registriert werden.

## <a name="user-credential-validation"></a>Validierung der Benutzer Anmelde Informationen

Im folgenden werden die Einstellungen zum Anpassen von Parametern für Benutzernamen und Kenn Wort Validierung beschrieben. Die Überprüfung erfolgt, wenn Benutzer sich für ein neues lokales Konto registrieren oder ein Kennwort ändern.

| Name der Standort Einstellung                                                       | Beschreibung                                                                                                                                                                                         |
|-------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Authentication/usermanager/passwordvalidator/enforcepasswordpolicy      | Gibt an, ob das Kennwort Zeichen aus drei der folgenden Kategorien enthält:<br><ul><li>Großbuchstaben von europäischen Sprachen (A bis Z, mit diakritischen Zeichen, Griechisch und Kyrillisch Zeichen)</li><li>Kleinbuchstaben von europäischen Sprachen (a bis z, Sharp-s mit diakritischen Zeichen, Griechisch und Kyrillisch Zeichen)</li><li>Basis 10 Ziffern (0 bis 9)</li><li>Nicht alphanumerische Zeichen (Sonderzeichen) (z. b.!, $, \#,%)</li></ul>Standardwert: true. Weitere Informationen finden Sie unter Kenn [Wort Richtlinie](https://technet.microsoft.com/library/hh994562(v=ws.10).aspx).                                                                                                           |  
| Authentication/usermanager/uservalidator/zugeordneralpha anumericusernames | Gibt an, ob nur alphanumerische Zeichen für den Benutzernamen zulässig sind. Standardwert: false. Weitere Informationen finden Sie [unter: uservalidator < tuser, TKey >. ](https://msdn.microsoft.com/library/dn613211.aspx)"" Zugeordnet ist.                                                          |  
| Authentication/usermanager/uservalidator/Requirements uniqueemail             | Gibt an, ob eine eindeutige e-Mail-Adresse zum Überprüfen des Benutzers erforderlich ist. Standardwert: true. Weitere Informationen finden Sie [unter: uservalidator < tuser, TKey >. ](https://msdn.microsoft.com/library/dn613213.aspx)Requirements-e-Mail-Nachricht.                                                                   |  
| Authentication/usermanager/passwordvalidator/Requirements dlength             | Die mindestens erforderliche Kenn Wort Länge. Standardwert: 8. Weitere Informationen finden Sie unter [passwordvalidator. Requirements dlength](https://msdn.microsoft.com/library/microsoft.aspnet.identity.passwordvalidator.requiredlength.aspx).                                       |  
| Authentication/usermanager/passwordvalidator/requungonletterordigit    | Gibt an, ob für das Kennwort ein nicht Buchstabe oder Ziffern Zeichen erforderlich ist. Standardwert: false. Weitere Informationen finden Sie unter: [passwordvalidator. requunononletterordigit](https://msdn.microsoft.com/library/microsoft.aspnet.identity.passwordvalidator.requirenonletterordigit.aspx). |  
| Authentication/usermanager/passwordvalidator/Requirements Digit               | Gibt an, ob für das Kennwort eine numerische Ziffer (von 0 bis 9) erforderlich ist. Standardwert: false. Weitere Informationen finden Sie unter [passwordvalidator. Requirements Digit](https://msdn.microsoft.com/library/microsoft.aspnet.identity.passwordvalidator.requiredigit.aspx).                |  
| Authentication/usermanager/passwordvalidator/Requirements lowercase           | Gibt an, ob das Kennwort einen Kleinbuchstaben (von a bis z) erfordert. Standardwert: false. Weitere Informationen finden Sie unter [passwordvalidator. Requirements lowercase](https://msdn.microsoft.com/library/microsoft.aspnet.identity.passwordvalidator.requirelowercase.aspx).        |  
| Authentication/usermanager/passwordvalidator/Requirements UpperCase           | Gibt an, ob das Kennwort einen Großbuchstaben (von A bis Z) erfordert. Standardwert: false. Weitere Informationen finden Sie unter [passwordvalidator. Requirements UpperCase](https://msdn.microsoft.com/library/microsoft.aspnet.identity.passwordvalidator.requireuppercase.aspx).       | 
|| 

## <a name="user-account-lockout-settings"></a>Einstellungen für die Benutzerkonto Sperre

Im folgenden werden die Einstellungen beschrieben, die definieren, wie und wann ein Konto von der Authentifizierung gesperrt wird. Wenn innerhalb eines kurzen Zeitraums eine bestimmte Anzahl von fehlgeschlagenen Kenn Wort versuchen erkannt wird, wird das Benutzerkonto für einen bestimmten Zeitraum gesperrt. Die Verwendung kann nach Ablauf der Sperrfrist erneut versuchen.

| Name der Standort Einstellung                                               | Beschreibung                                                                                                                                                                                                                                     |
|-----------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Authentication/usermanager/userlockoutenabledbydefault          | Gibt an, ob die Benutzer Sperre aktiviert ist, wenn Benutzer erstellt werden. Standardwert: true. Weitere Informationen finden Sie [unter: usermanager < tuser, TKey >. Userlockoutenabledbydefault](https://msdn.microsoft.com/library/dn613214.aspx).                                                                                                  |  
| Authentifizierung/usermanager/defaultaccountlockouttimespan        | Die Standardzeit Spanne, für die ein Benutzer gesperrt wird, nachdem Authentication/usermanager/maxfailedaccessttforelockout erreicht wurde. Standardwert: 24:00:00 (1 Tag). Weitere Informationen finden Sie [unter: usermanager < tuser, TKey >. Defaultaccountlockouttimespan](https://msdn.microsoft.com/library/dn613201.aspx).                 |  
| Authentifizierung/usermanager/maxfailedaccessder zbeforelockout | Die maximal zulässige Anzahl von Zugriffsversuchen, bevor ein Benutzer gesperrt wird (wenn die Sperre aktiviert ist). Standardwert: 5. Weitere Informationen finden Sie [unter: usermanager < tuser, TKey >. Maxfailedaccessder zbeforelockout](https://msdn.microsoft.com/library/dn613202.aspx).                                                                        |  
| Authentication/applicationcookie/expiretimespan                 | Die Standardzeit Spanne, für die Cookie-Authentifizierungs Sitzungen gültig sind. Standardwert: 24:00:00 (1 Tag). Weitere Informationen finden Sie unter [cookieauthenticationoptions. expiretimespan](https://msdn.microsoft.com/library/microsoft.owin.security.cookies.cookieauthenticationoptions.expiretimespan(v=vs.113).aspx). |
||  

## <a name="cookie-authentication-site-settings"></a>Website Einstellungen für die Cookie-Authentifizierung

Einstellungen zum Ändern des Standard Verhaltens des Authentifizierungs Cookies. Definiert durch die [cookieauthenticationoptions](https://msdn.microsoft.com/library/microsoft.owin.security.cookies.cookieauthenticationoptions.aspx) -Klasse.

| Name der Standort Einstellung   | Beschreibung       |
|----------------------|------------------------------------------------|
| Authentication/applicationcookie/AuthenticationType                      | Der Typ des Anwendungs Authentifizierungs Cookies. Standardwert: applicationcookie. Weitere Informationen finden Sie unter [authenticationoptions:: AuthenticationType](https://msdn.microsoft.com/library/dn300391.aspx).  |
| Authentication/applicationcookie/CookieName                              | Bestimmt den Namen des Cookies, der zum Beibehalten der Identität verwendet wird. Standardwert:. ASPNET. Cookies. Weitere Informationen finden Sie unter [cookieauthenticationoptions:: CookieName](https://msdn.microsoft.com/library/dn385537.aspx).  |
| Authentifizierung/applicationcookie/Cookiedomäne                            | Bestimmt die Domäne, die zum Erstellen des Cookies verwendet wird. Weitere Informationen finden Sie unter [cookieauthenticationoptions:: CookieDomain](https://msdn.microsoft.com/library/dn385536.aspx).  |
| Authentication/applicationcookie/Cookiepfad                              | Bestimmt den Pfad, der zum Erstellen des Cookies verwendet wird. Standard:/. Weitere Informationen finden Sie unter [cookieauthenticationoptions:: CookiePath](https://msdn.microsoft.com/library/dn385539.aspx). |
| Authentication/applicationcookie/cookiehttponly                          | Bestimmt, ob der Browser den Zugriff auf das Cookie durch Client seitiges JavaScript zulassen soll. Standardwert: true. Weitere Informationen finden Sie unter [cookieauthenticationoptions:: cookiehttponly](https://msdn.microsoft.com/library/dn385540.aspx).                     |
| Authentication/applicationcookie/cookiesecure                            | Bestimmt, ob das Cookie nur über eine HTTPS-Anforderung übertragen werden soll. Standard: sameasrequest. Weitere Informationen finden Sie unter [cookieauthenticationoptions:: cookiesecure](https://msdn.microsoft.com/library/dn385538.aspx).  |
| Authentication/applicationcookie/expiretimespan                          | Steuert, wie lange das Anwendungs Cookie von dem Zeitpunkt, an dem es erstellt wird, gültig bleibt. Standardwert: 14 Tage. Weitere Informationen finden Sie unter [cookieauthenticationoptions:: expiretimespan](https://msdn.microsoft.com/library/microsoft.owin.security.cookies.cookieauthenticationoptions.expiretimespan(v=vs.113).aspx).  |
| Authentication/applicationcookie/slidingExpiration                       | "SlidingExpiration" ist auf "true" festgelegt, um die Middleware anzuweisen, ein neues Cookie mit einer neuen Ablaufzeit jederzeit auszugeben, wenn eine Anforderung verarbeitet wird, die größer als die Hälfte des Ablaufzeit Fensters ist. Standardwert: true. Weitere Informationen finden Sie unter [cookieauthenticationoptions:: slidingExpiration](https://msdn.microsoft.com/library/dn385548.aspx). |
| Authentication/applicationcookie/loginpath                               | Die loginpath-Eigenschaft informiert die Middleware darüber, dass Sie den Statuscode "ausgehende 401 nicht autorisiert" in eine 302-Umleitung auf den angegebenen Anmelde Pfad ändern sollte. Standardwert: ~/SignIn. Weitere Informationen finden Sie unter [cookieauthenticationoptions:: loginpath](https://msdn.microsoft.com/library/dn385541.aspx).                                            |
| Authentication/applicationcookie/logoutpath                              | Wenn logoutpath die Middleware bereitstellt, wird eine Anforderung an diesen Pfad basierend auf dem "kehrnurlparameter" umgeleitet. Weitere Informationen finden Sie unter [cookieauthenticationoptions:: logoutpath](https://msdn.microsoft.com/library/dn385545.aspx).               |
| Authentication/applicationcookie/rückkehrnurlparameter                      | Der "kehrnurlparameter" bestimmt den Namen des Abfrage Zeichen folgen Parameters, der von der Middleware angefügt wird, wenn der Statuscode "401 nicht autorisiert" in eine 302-Umleitung auf den Anmelde Pfad geändert wird. Weitere Informationen finden Sie unter [cookieauthenticationoptions:: rückkehrnurlparameter](https://msdn.microsoft.com/library/dn385546.aspx).                           |
| Authentication/applicationcookie/securitystampvalidator/ValidateInterval | Der Zeitraum zwischen den Überprüfungen des Sicherheits Stempels. Standardwert: 30 Minuten. Weitere Informationen finden Sie unter [securitystampvalidator:: onvalidateidentity](https://msdn.microsoft.com/library/microsoft.aspnet.identity.owin.securitystampvalidator.onvalidateidentity.aspx).                    |
| Authentication/twofactorcookie/AuthenticationType                        | Der Typ des zweistufigen Authentifizierungs Cookies. Standard: twofactor Cookie. Weitere Informationen finden Sie unter [authenticationoptions:: AuthenticationType](https://msdn.microsoft.com/library/dn300391.aspx).            |
| Authentication/twofactorcookie/expiretimespan                            | Steuert, wie lange das zweistufige Cookie von dem Zeitpunkt, an dem es erstellt wird, gültig bleibt. Standard: 5 Minuten. Weitere Informationen finden Sie unter [cookieauthenticationoptions:: expiretimespan](https://msdn.microsoft.com/library/dn385543.aspx).     |
|||

### <a name="see-also"></a>Siehe auch

[Konfigurieren der Portal Authentifizierung](configure-portal-authentication.md)  
[OAuth2-Anbieter Einstellungen für Portale](configure-oauth2-settings.md)  
[Open ID Connect-Anbieter Einstellungen für Portale](configure-openid-settings.md)  
[WS-Verbund-Anbieter Einstellungen für Portale](configure-ws-federation-settings.md)  
[SAML 2,0-Anbieter Einstellungen für Portale](configure-saml2-settings.md)  
