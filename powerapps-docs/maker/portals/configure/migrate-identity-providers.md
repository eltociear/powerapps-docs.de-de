---
title: Migrieren von Identitäts Anbietern zu Azure AD B2C | MicrosoftDocs
description: Erfahren Sie, wie Sie Identitäts Anbieter zu Azure AD B2C migrieren.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/18/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: a57398d08e190140a3383aef29825f4c08e90363
ms.sourcegitcommit: 57b968b542fc43737330596d840d938f566e582a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72978299"
---
# <a name="migrate-identity-providers-to-azure-ad-b2c"></a>Identitäts Anbieter zu Azure AD B2C migrieren

Das Portal unterstützt ein konfigurierbares Sicherheitssystem, mit dem unsere Kunden mehrere Authentifizierungssysteme unterstützen können. Das Portal enthält neben dem Verbund mit externen Identitäts Anbietern auch eigene lokale Anmelde Informationen, indem Standardprotokolle wie z. b. oidc, SAML und WS-Federation verwendet werden. Es wird empfohlen, nur Azure AD B2C Identitäts Anbieter für die Authentifizierung zu verwenden und andere Identitäts Anbieter als veraltet zu kennzeichnen. 

## <a name="marking-an-identity-provider-as-deprecate"></a>Markieren eines Identitäts Anbieters als veraltet

Sie können Ihr Portal so konfigurieren, dass andere Identitäts Anbieter als veraltet markiert werden, und Benutzer können zu Azure AD B2C Identitäts Anbieter migrieren. 

Die folgenden Site Einstellungen werden verwendet, um die Veraltung von Identitäts Anbietern zu steuern:

| Name  | Beschreibung  |
|--------|--------|
| Authentifizierung/Registrierung/loczuordnung deprecated | Ein true-oder false-Wert. Wenn diese Einstellung auf "true" festgelegt ist, wird das lokale Konto als veraltet markiert. Der Benutzer des Portals muss zu einem nicht veralteten Konto migrieren. Standardmäßig ist der Wert auf false festgelegt. |
| Authentication/[Protokoll]/[Anbieter]/deprecated  | Ein true-oder false-Wert. Wenn diese Einstellung auf "true" festgelegt ist, wird das jeweilige Konto als veraltet markiert. Der Benutzer des Portals muss zu einem nicht veralteten Konto migrieren. Standardmäßig ist der Wert auf false festgelegt. |
|||

Wenn ein Portalbenutzer versucht, sich anzumelden, und Sie mindestens einen Identitäts Anbieter als veraltet markiert haben, wird das veraltete Konto auf der Seite angezeigt. Im folgenden Beispiel wird ein Microsoft-Konto als veraltet markiert.

![Beispiel für ein veraltet Konto](../media/gdpr-deprecate-account.png "Beispiel für ein veraltet Konto")

Der Text auf dem Bildschirm für den Legacy Authentifizierungs Anbieter kann mithilfe des folgenden Inhalts Ausschnitts geändert werden:

| Name                                               | Typ | Value                         |
|----------------------------------------------------|------|-------------------------------|
| Konto/SignIn/signinexternaldepre-edformüberschrift | Text | Mit einem Legacy Konto anmelden |
|||

> [!NOTE]
> Die veralteten Identitäts Anbieter werden nicht angezeigt, wenn ein Benutzer eine Einladung für ein Portal registriert oder einlöst.

## <a name="migrating-a-deprecated-identity-provider-to-a-new-identity-provider"></a>Migrieren eines veralteten Identitäts Anbieters zu einem neuen Identitäts Anbieter

Wenn sich ein Benutzer im Portal mit einem veralteten Identitäts Anbieter anmeldet, zeigt der Bildschirm für die Konto Migration eine Meldung an, dass Sie sich mit einem nicht als veraltet markierten Identitäts Anbieter anmelden kann. Wenn sich der Benutzer mit dem nicht veralteten Identitäts Anbieter anmeldet, wird das Benutzerkonto dem neuen Anbieter zugeordnet.

![Beispiel für die Konto Migration](../media/gdpr-account-migration.png "Beispiel für die Konto Migration")

Die Meldung auf dem Bildschirm für die Konto Migration kann mithilfe der folgenden Inhalts Ausschnitte geändert werden:

| Name                                         | Typ | Value                                                                                                                                                                                                                |
|----------------------------------------------|------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Konto/Konvertierung/PageTitle                 | Text | Konto Migration                                                                                                                                                                                                    |
| Konto/Konvertierung/Seiten Kopie                  | HTML | Sie haben sich mit einem Konto angemeldet, das nicht mehr unterstützt wird. Um dieses Portal weiterhin verwenden zu können, müssen Sie zu einem anderen Konto migrieren. Wählen Sie die Schaltfläche unten aus, um sich mit einem neuen oder vorhandenen unterstützten Konto anzumelden. |
| Konto/Konvertierung/signinexternalformüber Schrift | Text | Melden Sie sich mit einem unterstützten Konto an.                                                                                                                                                                                     |
|||

Im Portal können mehrere Identitäten einem einzelnen Kontaktdaten Satz zugeordnet werden. Wenn mehrere Anbieter veraltet sind, muss ein Portalbenutzer den Nutzungsbedingungen mehrmals zustimmen. Wenn ein Benutzer sich mit einem veralteten Identitäts Anbieter anmeldet, wird der Konto Migrationsprozess für jeden veralteten Anbieter initiiert, und der Kontaktdaten Satz wird nach der Konto Migration dem nicht veralteten Anbieter zugeordnet.

Beispiel: das Portal unterstützt Microsoft-Konto (MSA), Google und Facebook als Identitäts Anbieter für die Authentifizierung. Wenn Sie Google und Facebook als veraltete Anbieter markieren und ein Portalbenutzer nur Google und Facebook als Identitäts Anbieter für die Authentifizierung verwendet, erhält der Benutzer die Konto Migrations Nachricht, wenn er versucht, sich mit einem dieser beiden Anbieter anzumelden. Wenn sich der Benutzer mit MSA anmeldet, wird MSA dem Kontaktdaten Satz des Benutzers hinzugefügt. Der Benutzer verfügt jetzt nur über MSA als den unterstützten Authentifizierungs Identitäts Anbieter.

Wenn ein Portalbenutzer einen neuen Identitäts Anbieter auswählt und die Identität bereits einem anderen Kontaktdaten Satz zugeordnet ist, wird eine Fehlermeldung angezeigt. Sie können die Fehlermeldung mithilfe der folgenden Inhalts Ausschnitte konfigurieren:

| Name                                                     | Typ | Value                                                                                                                               |
|----------------------------------------------------------|------|-------------------------------------------------------------------------------------------------------------------------------------|
| Konto/SignIn/accountkonversionidentityusederrorüber Schrift | Text | Konto Konvertierungs Fehler                                                                                                            |
| Konto/SignIn/accountkonversionidentityusederrortext    | HTML | Dieses Konto ist bereits vorhanden. Schließen Sie den Browser, starten Sie den Prozess neu, und wählen Sie auf der Seite Konto Migration ein anderes Konto aus. |
|||

## <a name="disabling-local-login"></a>Der lokale Anmelde Name wird deaktiviert.

Sie können ein Portal so konfigurieren, dass die lokale Anmeldung mithilfe der `Authentication/Registration/LocalLoginDeprecated` Site Einstellung deaktiviert wird. Wenn jemand versucht, sich mit lokalen Anmelde Informationen anzumelden, wird der Bildschirm für die Konto Migration zusammen mit der Anweisung angezeigt, sich mit einem nicht veralteten Identitäts Anbieter anzumelden. Wenn das Konto migriert wird, werden die lokalen Anmelde Informationen für den Benutzer deaktiviert.

> [!NOTE]
> Wenn Sie die lokale Anmeldung als veraltet markieren, kann der Benutzer sich nicht für ein neues Konto registrieren.

Das folgende Feld wird im Kontaktdaten Satz des Portals hinzugefügt, um anzugeben, ob der lokale Anmelde Name für einen Benutzer deaktiviert ist:
- **Lokale Anmeldung deaktiviert**: gibt an, dass sich der Kontakt mit dem lokalen Konto nicht mehr beim Portal anmelden kann. Standardmäßig ist die Einstellung auf " **Nein**" festgelegt. Dieses Feld ist auf " **Ja** " festgelegt, wenn das Konto eines Benutzers zu einem nicht veralteten Identitäts Anbieter migriert wird und die lokale Anmeldung deaktiviert ist.

    ![Lokale Anmeldung deaktiviert](../media/local-login-disabled.png "Lokale Anmeldung deaktiviert")
