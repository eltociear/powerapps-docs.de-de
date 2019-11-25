---
title: Identitätsanbieter nach Azure AD B2C migrieren | MicrosoftDocs
description: Identitätsanbieter nach Azure AD B2C migrieren.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/18/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: a57398d08e190140a3383aef29825f4c08e90363
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2708877"
---
# <a name="migrate-identity-providers-to-azure-ad-b2c"></a>Identitätsanbieter nach Azure AD B2C migrieren

Das Portal unterstützt ein konfigurierbares Sicherheitssystem, mit dem unsere Kunden mehrere Authentifizierungssysteme unterstützen können. Das Portal enthält seine eigenen lokalen Anmeldeinformationen und stellt darüber hinaus auch einen Verbund mit externen Identitätsanbietern mithilfe von Standardprotokollen her, wie OIDC, SAML und WS-Verbund. Zukünftig wird empfohlen, dass Sie nur den Identitätsanbieter Azure AD B2C für die Authentifizierung verwenden und dass Sie andere Identitätsanbieter als veraltet einstufen. 

## <a name="marking-an-identity-provider-as-deprecate"></a>Einen Identitätsanbeiter als veraltet markieren

Sie können Ihr Portal so konfigurieren, dass andere Identitätsanbieter als veraltet markiert werden und es Benutzern ermöglicht wird, zum Identitätsanbeiter Azure AD B2C zu migrieren. 

Die folgenden Website-Einstellungen werden verwendet, um die Markierung von Identitätsanbietern als veraltet zu steuern:

| Name  | Beschreibung  |
|--------|--------|
| Authentication/Registration/LocalLoginDeprecated | Ein Wert „wahr” oder „falsch”. Bei Festlegung auf wahr wird das lokale Konto als veraltet markiert. Der Portalbenutzer wird dazu aufgefordert, zu einem nicht veralteten Konto zu migrieren. Standardmäßig ist dies auf "false" gesetzt. |
| Authentication/[protocol]/[provider]/Deprecated  | Ein Wert „wahr” oder „falsch”. Bei Festlegung auf wahr wird das spezifische Konto als veraltet markiert. Der Portalbenutzer wird dazu aufgefordert, zu einem nicht veralteten Konto zu migrieren. Standardmäßig ist dies auf "false" gesetzt. |
|||

Wenn ein Portalbenutzer versucht, sich anzumelden und Sie mindestens einen Identitätsanbieter als veraltet gekennzeichnet haben, wird das veraltete Konto auf der Seite angezeigt. Im folgenden Beispiel wird ein Microsoft-Konto als veraltet markiert.

![Beispiel von veraltetem Konto](../media/gdpr-deprecate-account.png "Beispiel von veraltetem Konto")

Der Text im Bildschirm für den Vorgängerauthentifizierungsanbieter kann geändert werden, indem Sie den folgenden Inhaltsausschnitt verwenden:

| Name                                               | Typ | Value                         |
|----------------------------------------------------|------|-------------------------------|
| Account/Signin/SignInExternalDeprecatedFormHeading | Text | Mit einem früheren Konto anmelden |
|||

> [!NOTE]
> Die veralteten Identitätsanbieter werden nicht angezeigt, wenn ein Benutzer sich registriert oder eine Einladung für ein Portal einlöst.

## <a name="migrating-a-deprecated-identity-provider-to-a-new-identity-provider"></a>Einen veralteten Identitätsanbieter zu einem neuen Identitätsanbieter migrieren

Wenn sich ein Portalbenutzer mit einem veralteten Identitätsanbieter anmeldet, wird vom Migrationsbildschirm eine Meldung angezeigt, sich mit einem nicht veralteten Identitätsanbieter anzumelden. Wenn sich der Benutzer mit dem nicht-veralteten Identitätsanbieter anmeldet, wird das Benutzerkonto dem neuen Anbieter zugeordnet.

![Kontomigrationsbeispiel](../media/gdpr-account-migration.png "Kontomigrationsbeispiel")

Die Meldung auf dem Bildschirm für die Kontomigration kann mithilfe der folgenden Inhaltsausschnitte geändert werden:

| Name                                         | Typ | Value                                                                                                                                                                                                                |
|----------------------------------------------|------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Account/Conversion/PageTitle                 | Text | Kontomigration                                                                                                                                                                                                    |
| Account/Conversion/PageCopy                  | HTML | Sie haben sich mit einem Konto angemeldet, das nicht mehr unterstützt wird. Um das Portal weiterhin benutzen zu können, müssen Sie zu einem anderen Konto migrieren. Wählen Sie die Schaltfläche unten aus, um sich mit einem neuen oder vorhandenen unterstützten Konto anzumelden. |
| Account/Conversion/SignInExternalFormHeading | Text | Melden Sie sich mit einem unterstützten Konto an.                                                                                                                                                                                     |
|||

Das Portal lässt zu, dass mehrere Identitäten einem einzigen Kontaktdatensatz zugeordnet werden. Wenn mehrere Anbieter veraltet sind, muss ein Portalbenutzer den Geschäftsbedingungen mehrere Male zustimmen. Immer wenn sich ein Benutzer mit einem veralteten Identitätsanbieter anmeldet, wird der Kontomigrationsprozess für jeden veralteten Anbieter initiiert und der Kontaktdatensatz wird nach der Kontomigration dem nicht veralteten Anbieter zugeordnet.

Beispiel: Dieses Portal unterstützt Microsoft-Konto (MSA), Google und Facebook als Identitätsanbieter für die Authentifizierung. Wenn Sie Google und Facebook als veraltete Anbieter markieren und ein Portalbenutzer nur Google und Facebook als Identitätsanbieter für die Authentifizierung hat, erhält der Benutzer die Kontomigrationsmeldung, wenn er versucht, sich unter Verwendung eines der beiden Anbieter anzumelden. Wenn der Benutzer sich mithilfe von MSA anmeldet, wird MSA zum Kontaktdatensatz des Benutzers hinzugefügt. Der Benutzer hat jetzt nur MSA als unterstützten Authentifizierungsidentitätsanbieter.

Wenn ein Portalbenutzer einen neuen Identitätsanbieter auswählt und die Identität bereits einem anderen Kontaktdatensatz zugeordnet ist, wird eine Fehlermeldung angezeigt. Sie können die Fehlermeldung mithilfe der folgenden Inhaltsausschnitte konfigurieren:

| Name                                                     | Typ | Value                                                                                                                               |
|----------------------------------------------------------|------|-------------------------------------------------------------------------------------------------------------------------------------|
| Account/Signin/AccountConversionIdentityUsedErrorHeading | Text | Fehler bei der Kontokonvertierung                                                                                                            |
| Account/Signin/AccountConversionIdentityUsedErrorText    | HTML | Dieses Konto ist bereits vorhanden. Schließen Sie Ihren Browser, starten Sie den Prozess erneut, und wählen Sie ein anderes Konto auf der Seite „Kontomigration” aus. |
|||

## <a name="disabling-local-login"></a>Lokale Anmeldung deaktivieren

Sie können ein Portal so konfigurieren, dass die lokal Anmeldung deaktiviert wird, indem Sie die Website-Einstellung `Authentication/Registration/LocalLoginDeprecated` verwenden. Wenn jemand versucht, sich mithilfe von lokalen Anmeldeinformationen anzumelden, wird der Kontomigrationsbildschirm zusammen mit der Anweisung angezeigt, sich mit einem nicht veralteten Identitätsanbieter anzumelden. Wenn das Firma migriert wird, werden lokale Anmeldeinformationen für den Benutzer deaktiviert.

> [!NOTE]
> Wenn Sie die lokale Anmeldung als veraltet markieren, kann sich der Benutzer nicht für ein neues Konto registrieren.

Das folgende Feld wird im Portal-Kontaktdatensatz hinzugefügt, um anzugeben, ob die lokale Anmeldung für einen Benutzer deaktiviert ist:
- **Lokale Anmeldung deaktiviert**: Gibt an, dass sich der Kontakt nicht mehr mit dem lokalen Konto im Portal anmelden kann. Standardmäßig ist dies auf **Nein** festgelegt. Dieses Feld wird auf **Ja** festgelegt, wenn das Konto eines Benutzers zu einem nicht veralteten Identitätsanbieter migriert ist und die lokale Anmeldung deaktiviert ist.

    ![Lokale Anmeldung deaktiviert](../media/local-login-disabled.png "Lokale Anmeldung deaktiviert")
