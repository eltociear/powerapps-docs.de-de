---
title: Verwenden der vereinfachten Authentifizierungs- und Identitätsanbieterkonfiguration (Vorschau) | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie die schnelle, einfache und vereinfachte Portalkonfiguration für die Authentifizierung verwenden.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 05/05/2020
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 6dc6fc21c32c044a49ff9364dbf0c3c95bcb04cf
ms.sourcegitcommit: 13a78a66408d39b4bc90a72613b0d303abc07b1b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/06/2020
ms.locfileid: "3338217"
---
# <a name="simplified-authentication-and-identity-provider-configuration-preview"></a>Vereinfachte Authentifizierungs- und Identitätsanbieterkonfiguration (Vorschau)

[Dieses Thema ist Teil der Dokumentation zur Vorabversion und kann geändert werden.]

Das Einrichten der Authentifizierung ist eine zentrale Anpassung in jedem Portal. Die vereinfachte Konfiguration des Identitätsanbieters in Power Apps-Portalen bieten In-App-Anleitungen für die Einrichtung von Identitätsanbietern und abstrahieren die Komplexität der Einrichtung. Hersteller und Administratoren können das Portal problemlos für unterstützte Identitätsanbieter konfigurieren.

> [!NOTE]
> Die Funktion für die vereinfachte Authentifizierungs- und Identitätsanbieterkonfiguration befindet sich in der Vorschau. Um auf diese Vorschaufunktion zugreifen zu können, müssen Sie die [Power Apps-Vorschau](https://make.preview.powerapps.com) verwenden. Nachdem diese Vorschaufunktion allgemein verfügbar ist, können Sie von [Power Apps](https://make.powerapps.com) darauf zugreifen. Sie können diese Vorschaufunktion für Ihr Portal nicht aktivieren oder deaktivieren. Weitere Informationen zu Vorschaufunktionen finden Sie unter [Informationen zu Vorschaufeatures und experimentellen Features in Power Apps](https://docs.microsoft.com/powerapps/maker/canvas-apps/working-with-experimental-preview). 

## <a name="overview"></a>Überblick

Sie können Portalidentitätsanbieter über die [Power Apps-Vorschau](https://make.preview.powerapps.com) aktivieren, deaktivieren und konfigurieren, indem Sei die vereinfachte Konfiguration der Portalauthentifizierung verwenden. Nachdem Sie einen Identitätsanbieter ausgewählt haben, können Sie den Anweisungen folgen, um die Anbietereinstellungen einfach einzugeben, anstatt [die Authentifizierung manuell einzugeben](set-authentication-identity.md).

### <a name="authentication-settings"></a>Authentifizierungseinstellungen

So beginnen Sie mit der Konfiguration eines Identitätsanbieters für Ihr Portal:

1. Gehen Sie zur [Power Apps-Vorschau](https://make.preview.powerapps.com).

1. Wählen Sie im linken Navigationsbereich die Option **Apps** aus.

    ![Apps auswählen](media/use-simplified-authentication-configuration/select-apps.png "Apps auswählen")

1. Wählen Sie aus der Liste der verfügbaren Apps Ihr Portal aus.

1. Wählen Sie im Menü oben **Einstellungen** aus. Sie können auch **Weitere Befehle** (**...**) und dann **Einstellungen** auswählen.

    ![Einstellungen auswählen](media/use-simplified-authentication-configuration/select-settings.png "Einstellungen auswählen")

1. Wählen Sie in den Einstellungen auf der rechten Seite Ihres Arbeitsbereichs die Option **Authentifizierungseinstellungen** aus.

    ![Authentifizierungseinstellungen](media/use-simplified-authentication-configuration/portal-settings-right-pane.png "Authentifizierungseinstellungen")

Sie sehen eine Liste der Identitätsanbieter, die Sie konfigurieren können.

![Identitätsanbieter](media/use-simplified-authentication-configuration/portal-authentication-settings.png "Identitätsanbieter")

> [!NOTE]
> Power Apps-Portale unterstützen mehrere Identitätsanbieter. Die vereinfachte Konfigurationsfunktion für Authentifizierung und Identitätsanbieter unterstützt derzeit jedoch nur die oben aufgeführten Identitätsanbieter.

#### <a name="authentication-settings-from-the-portal-details-page"></a>Authentifizierungseinstellungen auf der Seite „Portaldetails“

Sie können die Identitätsanbieter auch auf der Seite „Portaldetails“ anzeigen.

1. Wählen Sie aus der Liste der verfügbaren Apps Ihr Portal aus.

1. Wählen Sie aus dem oberen Menü **Details** aus. Sie können auch **Weitere Befehle** (**...**) und dann **Details** auswählen.

    ![Details auswählen](media/use-simplified-authentication-configuration/select-details.png "Details auswählen")

Auf der Detailseite wird der Abschnitt **Identitätsanbieter** angezeigt.

![Portal-Details](media/use-simplified-authentication-configuration/portal-details.png "Portal-Details")

> [!NOTE]
> Wenn Sie **Alle anzeigen** über die Seite „Portaldetails“ auswählen, gelangen Sie zur vollständigen Liste der Identitätsanbieter.

## <a name="general-authentication-settings"></a>Allgemeine Authentifizierungseinstellungen

Sie können die folgenden allgemeinen Authentifizierungseinstellungen konfigurieren, indem Sie **Authentifizierungseinstellungen** auf der Seite **Identitätsanbieter** auswählen.

![Allgemeine Authentifizierungseinstellungen](media/use-simplified-authentication-configuration/general-authentication-settings.png "Allgemeine Authentifizierungseinstellungen")

- **Externer Anmeldename** – Ist diese Option auf **Aus** eingestellt, wird die Registrierung und Anmeldung eines externen Kontos deaktiviert und versteckt.
<br>Die externe Authentifizierung wird von der ASP.NET Identity API bereitgestellt. In diesem Fall werden die Kontoanmeldeinformationen und die Kennwortverwaltung von Identitätsanbietern von Drittanbietern wie z. B. Facebook, LinkedIn, Google, Twitter und Microsoft verwaltet. Benutzer melden sich für den Zugriff beim Portal an, indem sie eine externe Identität für die Portalregistrierung auswählen. Nach der Registrierung hat eine externe Identität Zugriff auf dieselben Features wie ein lokales Konto. Informationen zu verknüpften Websiteeinstellungen finden Sie unter [Externe Konten verwalten](set-authentication-identity.md#manage-external-accounts).

- **[Offene Registrierung](configure-portal-authentication.md#open-registration)** – Ist diese Option auf **Aus** eingestellt, wird die Registrierung eines externen Kontos deaktiviert und versteckt.

Sie können auch auf der Seite mit den Portaldetails zu den allgemeinen Authentifizierungseinstellungen wechseln, indem Sie **Einstellungen** in der oberen rechten Ecke des Abschnitts **Identitätsanbieter** auswählen.

![Allgemeine Authentifizierungseinstellungen auf der Seite „Portaldetails“](media/use-simplified-authentication-configuration/general-settings-from-details.png "Allgemeine Authentifizierungseinstellungen auf der Seite „Portaldetails“")

### <a name="default-identity-provider"></a>Standardmäßiger Identitätsanbieter

Sie können einen beliebigen Identitätsanbieter als Standard festlegen. Wenn ein Identitätsanbieter als Standard festgelegt ist, werden Benutzer, die sich beim Portal anmelden, nicht zur Anmeldeseite des Portals umgeleitet. Stattdessen wird bei der Anmeldung standardmäßig immer der ausgewählte Anbieter verwendet.

![Standardmäßiger Identitätsanbieter](media/use-simplified-authentication-configuration/set-default.png "Standardmäßiger Identitätsanbieter")

> [!IMPORTANT]
> Wenn Sie einen Identitätsanbieter als Standard festlegen, haben Benutzer keine Möglichkeit, einen anderen Identitätsanbieter auszuwählen.

Nachdem Sie einen Identitätsanbieter als Standard festgelegt haben, können Sie **Als Standard entfernen** auswählen, um es als Standard entfernen. Wenn Sie einen Identitätsanbieter als Standard entfernen, werden Benutzer zur Anmeldeseite des Portals weitergeleitet und können aus den von Ihnen aktivierten Identitätsanbietern auswählen.

> [!NOTE]
> Sie können nur einen konfigurierten Identitätsanbieter als Standard festlegen. Die Option **Als Standard festlegen** wird verfügbar, nachdem Sie einen Identitätsanbieter konfiguriert haben.

## <a name="add-configure-or-delete-an-identity-provider"></a>Hinzufügen, Konfigurieren oder Löschen eines Identitätsanbieters

Standardmäßig werden mehrere Identitätsanbieter hinzugefügt, die Sie konfigurieren können. Sie können zusätzliche Azure Active Directory (Azure AD) B2C-Anbieter hinzufügen oder die verfügbaren Oauth 2.0-Anbieter wie LinkedIn und Microsoft konfigurieren.

> [!NOTE]
> - Sie können die Konfiguration der [lokalen Anmeldung](configure-portal-authentication.md) und des Azure Active Directory-Anbieters bei Verwendung dieser Schnittstelle nicht ändern.
> - Sie können nur eine Instanz jedes Identitätsanbietertyps für Oauth 2.0 verwenden, z B. **Facebook**, **LinkedIn**, **Google**, **Twitter** und **Microsoft**.
> - Es kann einige Minuten dauern, bis Aktualisierungen der Konfiguration des Identitätsanbieters im Portal angezeigt werden. Um Ihre Änderungen sofort zu übernehmen, können Sie [das Portal neu starten](../admin/admin-overview.md#open-power-apps-portals-admin-center).

### <a name="add-or-configure-a-provider"></a>Hinzufügen oder Konfigurieren eines Anbieters

Wählen Sie zum Hinzufügen eines Identitätsanbieters **Anbieter hinzufügen** aus den **Authentifizierungseinstellungen** aus.

![Anbieter aus den Einstellungen hinzufügen](media/use-simplified-authentication-configuration/add-provider-from-settings.png "Anbieter aus den Einstellungen hinzufügen")

Sie können auch **Anbieter hinzufügen** von der Seite „Portaldetails“ auswählen.

![Anbieter aus der Seite „Details“ hinzufügen](media/use-simplified-authentication-configuration/add-provider-from-details.png "Anbieter aus der Seite „Details“ hinzufügen")

Sie können aus der verfügbaren Liste der Anbieter auswählen, einen Namen eingeben und dann **Weiter** auswählen, um die Anbietereinstellungen zu konfigurieren.

![Neuen Anbieter hinzufügen](media/use-simplified-authentication-configuration/add-provider.png "Neuen Anbieter hinzufügen")

> [!NOTE]
> Der hier eingegebene **Anbietername** wird auf der Anmeldeseite für Benutzer als Text auf der Schaltfläche angezeigt, die sie bei der Auswahl dieses Anbieters verwenden.

Wählen Sie zum Konfigurieren eines Anbieters **zum Konfigurieren klicken** (oder wählen Sie **Weitere Befehle** (**...**) und dann **Konfigurieren**) aus.

![Einen Anbieter konfigurieren](media/use-simplified-authentication-configuration/configure-provider.png "Einen Anbieter konfigurieren")

> [!NOTE]
> Sie können **Anbieter hinzufügen** oder **Konfigurieren** verwenden, um zum ersten Mal einen Anbieter hinzuzufügen oder zu konfigurieren. Nachdem Sie einen Anbieter konfiguriert haben, können Sie ihn bearbeiten. Sie können auch den Hyperlink für den Anbieternamen auswählen, um die Konfigurationsoptionen schnell zu öffnen.

Die Konfigurationsschritte nach der Auswahl von **Weiter** hängt vom Typ des ausgewählten Identitätsanbieters ab. Zum Beispiel unterscheidet sich die Azure Active Directory B2C-Konfiguration von der Einrichtung von LinkedIn. Weitere Informationen zum Konfigurieren des Anbieters Ihrer Wahl finden Sie in den anbieterspezifischen Abschnitten weiter unten in diesem Artikel.

### <a name="edit-a-provider"></a>Einen Anbieter bearbeiten

Nachdem Sie einen Anbieter hinzugefügt und konfiguriert haben, sehen Sie den Anbieter im Status **Aktiviert** auf den Seiten für Portaleinstellungen oder Details.

Um einen von Ihnen konfigurierten Anbieter zu bearbeiten, wählen Sie ihn aus, wählen Sie dann **Weitere Befehle** (**...**) und dann **Konfiguration bearbeiten**.

![Einen Anbieter bearbeiten](media/use-simplified-authentication-configuration/edit-provider.png "Einen Anbieter bearbeiten")

Informationen zum Bearbeiten der Einstellungen für den von Ihnen ausgewählten Anbietertyp finden Sie in den anbieterspezifischen Abschnitten weiter unten in diesem Artikel.

### <a name="delete-a-provider"></a>Einen Anbieter löschen

Um einen Identitätsanbieter zu löschen, wählen Sie **Weitere Befehle** (**...**) und dann **Löschen**.

![Einen Anbieter löschen](media/use-simplified-authentication-configuration/delete-provider.png "Einen Anbieter löschen")

Durch das Löschen eines Anbieters wird Ihre Anbieterkonfiguration für den ausgewählten Anbietertyp gelöscht, und der Anbieter wird wieder für die Konfiguration verfügbar.

> [!NOTE]
> Wenn Sie einen Anbieter löschen, wird nur die Portalkonfiguration für den Anbieter gelöscht. Wenn Sie beispielsweise den LinkedIn-Anbieter löschen, bleiben Ihre LinkedIn-App und Ihre App-Konfiguration erhalten. Ebenso wird, wenn Sie den Azure Active Directory B2C-Anbieter löschen, nur die Portalkonfiguration gelöscht; Die Azure-Mandant-Konfiguration für diesen Anbieter wird nicht geändert.

## <a name="configure-the-azure-active-directory-b2c-provider"></a>Konfigurieren des Azure Active Directory B2C-Anbieters

### <a name="step-1---configure-the-azure-active-directory-b2c-application"></a>Schritt 1 – Azure Active Directory B2C-Anwendung konfigurieren

![Azure AD B2C-App konfigurieren](media/use-simplified-authentication-configuration/configure-ad-b2c-step1.png "Azure AD B2C-App konfigurieren")

Zur Verwendung von Azure AD B2C als Identitätsanbieter:

1. [Erstellen und Konfigurieren Sie einen Azure AD B2C-Mandanten](https://docs.microsoft.com/azure/active-directory-b2c/tutorial-create-tenant).

1. [Registrieren Sie eine Anwendung](https://docs.microsoft.com/azure/active-directory-b2c/tutorial-register-applications?tabs=applications#register-a-web-application) in Ihrem Mandanten. Verwenden Sie die **Antwort-URL**, die im Assistenten beim Konfigurieren der Anwendung bereitgestellt wird.

    > [!NOTE]
    > Sie müssen **Ja** für das Feld **Impliziten Flow zulassen** auswählen und Ihre Portal-URL im Feld **Antwort-URL** festlegen.

1. [Flow erstellen](https://docs.microsoft.com/azure/active-directory-b2c/tutorial-create-user-flows#create-a-sign-up-and-sign-in-user-flow). Optional können Sie einen [Benutzerflow für die Kennwortzurücksetzung erstellen](https://docs.microsoft.com/azure/active-directory-b2c/tutorial-create-user-flows#create-a-password-reset-user-flow).

1. [Konfigurieren Sie die Token-Kompatibilität](https://docs.microsoft.com/azure/active-directory-b2c/configure-tokens#configure-token-compatibility) mit einer **Ausstelleranspruch (iss)**-URL, die **tfp** enthält. Weitere Informationen: [Token-Kompatibilität](https://docs.microsoft.com/azure/active-directory-b2c/tokens-overview#compatibility)

### <a name="step-2---configure-site-settings"></a>Schritt 2 – Konfigurieren von Websiteeinstellungen

Konfigurieren Sie die folgenden Websiteeinstellungen und Richtlinien zum Zurücksetzen des Kennworts für Ihren Azure AD B2C-Anbieter.

![Konfigurieren von Websiteeinstellungen](media/use-simplified-authentication-configuration/configure-ad-b2c-step2.png "Konfigurieren von Websiteeinstellungen")

- **Autoritative Stelle** – Die Aussteller-URL, die in den Metadaten des Benutzerflows der Anmelde- und Anmelderichtlinie definiert ist.
<br> Um die Aussteller-URL abzurufen:

   1. Öffnen Sie den Benutzerflow für die Registrierung und Anmeldung, den Sie in [Schritt 1](#step-1---configure-the-azure-active-directory-b2c-application) erstellt haben. Für diesen Schritt müssen Sie zum Azure AD B2C-Mandanten im [Azure-Portal](https://portal.azure.com) wechseln.
   1. Wählen Sie **Benutzerflow ausführen** im Dialogfeld **Öffnen** und dann oben die URL aus, um das Konfigurationsdokument zu öffnen. <br> Die URL bezieht sich auf das *Konfigurationsdokument für den OpenID Connect-Identitätsanbieter*, auch bekannt als *OpenID-/well-known-Konfigurationsendpunkt*.
   1. Kopieren Sie die URL des **Ausstellers** aus dem Konfigurationsdokument, das in einem neuen Browser geöffnet wird.  

- **Client-ID** – Geben Sie die **Anwendungs-ID** der Azure AD B2C-Anwendung ein, die Sie in [Schritt 1](#step-1---configure-the-azure-active-directory-b2c-application) erstellt haben.

- **Umleitungs-URI** – Geben Sie die Portal-URL ein. <br> Sie müssen den Umleitungs-URI nur ändern, wenn Sie einen benutzerdefinierten Domänennamen verwenden.

#### <a name="password-reset-settings"></a>Einstellungen für die Kennwortzurücksetzung

- **Standardrichtlinien-ID** – Geben Sie den Namen des Registrierungs- und Anmeldebenutzerflows ein, den Sie in [Schritt 1](#step-1---configure-the-azure-active-directory-b2c-application) erstellt haben. Dem Namen wird das Präfix *B2C_1* vorangestellt.

- **ID der Kennwortrücksetzrichtlinie** – Geben Sie den Namen des Kennwortrücksetzungsbenutzerflows ein, den Sie in [Schritt 1](#step-1---configure-the-azure-active-directory-b2c-application) erstellt haben. Dem Namen wird das Präfix *B2C_1* vorangestellt.

- **Gültige Aussteller** – Eine durch Kommas getrennte Liste von Aussteller-URLs für den Benutzerflow für die Registrierung und Anmeldung sowie den Benutzerflow zum Zurücksetzen des Kennworts, den Sie in [Schritt 1](#step-1---configure-the-azure-active-directory-b2c-application) erstellt haben. 
<br> Öffnen Sie jeden Flow und führen Sie die folgenden Schritte unter **Autoritative Stelle** weiter oben in diesem Abschnitt, um die Aussteller-URLs für den Benutzerflow für die Registrierung und Anmeldung sowie den Benutzerflow zum Zurücksetzen des Kennworts abzurufen.

Weitere Informationen zu den Websiteeinstellungen finden Sie unter [verknüpfte Websiteeinstellungen](azure-ad-b2c.md#related-site-settings).

### <a name="step-3---configure-additional-settings"></a>Schritt 3 – Konfigurieren von zusätzlichen Einstellungen

Sie haben die Möglichkeit, zusätzliche Einstellungen für den Azure AD B2C-Identitätsanbieter zu konfigurieren.

![Konfigurieren von zusätzlichen Einstellungen](media/use-simplified-authentication-configuration/configure-ad-b2c-step3.png "Konfigurieren von zusätzlichen Einstellungen")

- **Zuordnung von Registrierungsansprüchen** – Liste mit Paaren von logischen Namen und Ansprüchen, die verwendet werden können, um Anspruchswerte zuzuordnen, die von Azure AD B2C zurückgegeben wurden, Attributen im Kontaktdatensatz zuzuordnen, die während der Registrierung erstellt wurden. <br> Wenn Sie beispielsweise **Position (jobTitle)** und **Postleitzahl (postalCode)** als **Benutzerattribute** in Ihrem Benutzerflow aktiviert haben und Sie die entsprechenden Felder für die Entität Kontakt**Position (jobtitle)** und **Adresse 1: Postleitzahl (address1_postalcode)** aktualisieren möchten, geben Sie die Anspruchzuordnung folgendermaßen ein: ```jobtitle=jobTitle,address1_postalcode=postalCode```.
- **Zuordnung von Anmeldungsansprüchen** – Liste mit Paaren von logischen Namen und Ansprüchen, die verwendet werden können, um Anspruchswerte zuzuordnen, die von Azure AD B2C zurückgegeben wurden, Attributen im Kontaktdatensatz zuzuordnen, die während der Registrierung erstellt wurden. <br> Wenn Sie beispielsweise **Position (jobTitle)** und **Postleitzahl (postalCode)** als **Anwendungsansprüche** in Ihrem Benutzerflow aktiviert haben und Sie die entsprechenden Felder für die Entität Kontakt**Position (jobtitle)** und **Adresse 1: Postleitzahl (address1_postalcode)** aktualisieren möchten, geben Sie die Anspruchzuordnung folgendermaßen ein: ```jobtitle=jobTitle,address1_postalcode=postalCode```.
- **Externe Abmeldung** – Aktiviert oder deaktiviert die verbundbasierte Abmeldung. Wenn **Ein** festgelegt ist, werden Benutzer zur verbundbasierten Abmeldeoberfläche weitergeleitet, wenn sie sich vom Portal abmelden. Wenn **Aus** festgelegt ist, werden Benutzer nur vom Portal abgemeldet.
- **Zuordnung von Kontakt und E-Mail-Adresse**: Gibt an, ob Kontakte einer entsprechenden E-Mail-Adresse zugeordnet werden. Wenn **Ein** festgelegt ist, ordnet diese Einstellung einen Kontaktdatensatz einer entsprechenden E-Mail-Adresse zu und weist den externen Identitätsanbieter dann automatisch dem Kontakt zu, wenn der Benutzer sich erfolgreich anmeldet.
- **Registrierung aktiviert** – Stellen Sie die [offene Registrierung](configure-portal-authentication.md#open-registration) für Ihr Portal ein oder aus. Setzen Sie diesen Schalter auf **Aus**, wird die Registrierung eines externen Kontos deaktiviert und versteckt.

Wählen Sie **Bestätigen** aus, um eine Zusammenfassung Ihrer Konfiguration anzuzeigen und die Identitätskonfiguration abzuschließen.

Weitere Informationen zur Anspruchszuordnung finden Sie unter [Szenarios für die Zuordnung von Azure AD B2C-Ansprüchen](azure-ad-b2c.md#claims-mapping).

Weitere Informationen zum Konfigurieren von Azure AD B2C-Identitätsanbietern, finden Sie unter [Azure AD B2C-Anbietereinstellungen für Portale](azure-ad-b2c.md#customize-the--ad-b2c-user-interface).

## <a name="configure-the-facebook-provider"></a>Konfigurieren des Facebook-Anbieters

![Facebook-App konfigurieren](media/use-simplified-authentication-configuration/configure-facebook.png "Facebook-App konfigurieren")

Um **Facebook** als Identitätsanbieter zu verwenden, müssen Sie [eine App in Facebook](https://developers.facebook.com) mit einer Weiterleitungs-URL erstellen.

Die Weiterleitungs-URL wird von der Facebook-App verwendet, um Benutzer nach erfolgreicher Authentifizierung zum Portal umzuleiten. Wenn Ihr Portal einen benutzerdefinierten Domainnamen verwendet, haben Sie möglicherweise eine andere URL als die hier angegebene.

**Portalwebsite-Einstellungen** für Facebook:

- **Client-ID** – Eine eindeutige App-ID, die von Facebook für Ihre App generiert wird.
- **Geheimer Clientschlüssel** – Der App-Geheimschlüssel für Ihre Facebook-App.

Wie Sie zusätzliche Einstellungen für Facebook konfigurieren, erfahren Sie unter [Zusätzliche Einstellungen für Oauth 2-Anbieter konfigurieren](#configure-additional-settings-for-oauth-2-providers).

Weitere Informationen zum Konfigurieren von OAuth 2-Anbietern, finden Sie unter [OAuth 2-Anbietereinstellungen für Portale](configure-oauth2-settings.md).

## <a name="configure-the-linkedin-provider"></a>Konfigurieren des LinkedIn-Anbieters

![Konfigurieren der LinkedIn-App](media/use-simplified-authentication-configuration/configure-linkedin.png "Konfigurieren der LinkedIn-App")

Um **LinkedIn** als Identitätsanbieter zu verwenden, müssen Sie [eine App in LinkedIn](https://www.linkedin.com/developers/apps) mit einer Weiterleitungs-URL erstellen.

Die Weiterleitungs-URL wird von der LinkedIn-App verwendet, um Benutzer nach erfolgreicher Authentifizierung zum Portal umzuleiten. Wenn Ihr Portal einen benutzerdefinierten Domainnamen verwendet, haben Sie möglicherweise eine andere URL als die hier angegebene.

**Portalwebsite-Einstellungen** für LinkedIn:

- **Client-ID** – Eine eindeutige App-ID, die von LinkedIn für Ihre App generiert wird.
- **Geheimer Clientschlüssel** – Der App-Geheimschlüssel für Ihre LinkedIn-App.

Wie Sie zusätzliche Einstellungen für LinkedIn konfigurieren, erfahren Sie unter [Zusätzliche Einstellungen für Oauth 2-Anbieter konfigurieren](#configure-additional-settings-for-oauth-2-providers).

Weitere Informationen zum Konfigurieren von OAuth 2-Anbietern, finden Sie unter [OAuth 2-Anbietereinstellungen für Portale](configure-oauth2-settings.md).

## <a name="configure-the-google-provider"></a>Konfigurieren des Google-Anbieters

![Konfigurieren der Google-App](media/use-simplified-authentication-configuration/configure-google.png "Konfigurieren der Google-App")

Um **Google** als Identitätsanbieter zu verwenden, müssen Sie [eine App in Google](https://console.developers.google.com/) mit einer Weiterleitungs-URL erstellen.

Die Weiterleitungs-URL wird von der Google-App verwendet, um Benutzer nach erfolgreicher Authentifizierung zum Portal umzuleiten. Wenn Ihr Portal einen benutzerdefinierten Domainnamen verwendet, haben Sie möglicherweise eine andere URL als die hier angegebene.

**Portalwebsite-Einstellungen** für Google:

- **Client-ID** – Eine eindeutige App-ID, die von Google für Ihre App generiert wird.
- **Geheimer Clientschlüssel** – Der von Google für Ihre App generierte geheime Clientschlüssel.

Wie Sie zusätzliche Einstellungen für Google konfigurieren, erfahren Sie unter [Zusätzliche Einstellungen für Oauth 2-Anbieter konfigurieren](#configure-additional-settings-for-oauth-2-providers).

Weitere Informationen zum Konfigurieren von OAuth 2-Anbietern, finden Sie unter [OAuth 2-Anbietereinstellungen für Portale](configure-oauth2-settings.md).

## <a name="configure-the-twitter-provider"></a>Konfigurieren des Twitter-Anbieters

![Konfigurieren der Twitter-App](media/use-simplified-authentication-configuration/configure-twitter.png "Konfigurieren der Twitter-App")

Um **Twitter** als Identitätsanbieter zu verwenden, müssen Sie [eine App in Twitter](https://developer.twitter.com/apps) mit einer Weiterleitungs-URL erstellen.

Die Weiterleitungs-URL wird von der Twitter-App verwendet, um Benutzer nach erfolgreicher Authentifizierung zum Portal umzuleiten. Wenn Ihr Portal einen benutzerdefinierten Domainnamen verwendet, haben Sie möglicherweise eine andere URL als die hier angegebene.

**Portalwebsite-Einstellungen** für Twitter:

- **Client-ID** – Eine eindeutige App-ID, die von Twitter für Ihre App generiert wird.
- **Geheimer Clientschlüssel** – Der von Twitter für Ihre App generierte geheime Clientschlüssel.

Wie Sie **zusätzliche Einstellungen** für Twitter konfigurieren, erfahren Sie unter [Zusätzliche Einstellungen für Oauth 2-Anbieter konfigurieren](#configure-additional-settings-for-oauth-2-providers).

Weitere Informationen zum Konfigurieren von OAuth 2-Anbietern, finden Sie unter [OAuth 2-Anbietereinstellungen für Portale](configure-oauth2-settings.md).

## <a name="configure-the-microsoft-provider"></a>Konfigurieren des Microsoft-Anbieters

![Konfigurieren der Microsoft-App](media/use-simplified-authentication-configuration/configure-microsoft.png "Konfigurieren der Microsoft-App")

Um **Microsoft** als Identitätsanbieter zu verwenden, müssen Sie [eine App im Azure-Portal](https://aka.ms/AppRegistrations) mit einer Weiterleitungs-URL erstellen.

Die Weiterleitungs-URL wird von der Microsoft-App verwendet, um Benutzer nach erfolgreicher Authentifizierung zum Portal umzuleiten. Wenn Ihr Portal einen benutzerdefinierten Domainnamen verwendet, haben Sie möglicherweise eine andere URL als die hier angegebene.

**Portalwebsite-Einstellungen** für Microsoft:

- **Client-ID** – Eine eindeutige App-ID, die von Microsoft für Ihre App generiert wird.
- **Geheimer Clientschlüssel** – Der von Microsoft für Ihre App generierte geheime Clientschlüssel.

Wie Sie **zusätzliche Einstellungen** für Microsoft konfigurieren, erfahren Sie unter [Zusätzliche Einstellungen für Oauth 2-Anbieter konfigurieren](#configure-additional-settings-for-oauth-2-providers).

Weitere Informationen zum Konfigurieren von OAuth 2-Anbietern, finden Sie unter [OAuth 2-Anbietereinstellungen für Portale](configure-oauth2-settings.md).

## <a name="configure-additional-settings-for-oauth-2-providers"></a>Konfigurieren zusätzlicher Einstellungen für Oauth 2-Anbieter

Die zusätzlichen Authentifizierungseinstellungen in diesem Abschnitt gelten für die Anbieter **Facebook**, **Twitter**, **Microsoft**, **LinkedIn** und **Google**.

![Konfigurieren von zusätzlichen Einstellungen](media/use-simplified-authentication-configuration/additional-oauth-settings.png "Konfigurieren von zusätzlichen Einstellungen")

- **Authentifizierungstyp** – Der Middleware-Typ für die OWIN-Authentifizierung: [AuthenticationOptions.AuthenticationType](https://docs.microsoft.com/previous-versions/aspnet/mt152183(v=vs.113)?redirectedfrom=MSDN). Zum Beispiel: https://sts.windows.net/contoso.onmicrosoft.com/.
- **Authentifizierungsmodus** – Der Middleware-Modus für die OWIN-Authentifizierung: [AuthenticationOptions.AuthenticationMode](https://docs.microsoft.com/previous-versions/aspnet/mt152179(v=vs.113)?redirectedfrom=MSDN).
- **Backchannel-Timeout** – Timeoutwert in Millisekunden für die Back-Channel-Kommunikation: [MicrosoftAccountAuthenticationOptions.BackchannelTimeout](https://docs.microsoft.com/previous-versions/aspnet/mt174421(v=vs.113)?redirectedfrom=MSDN).
- **Rückrufpfad** – Der Anforderungspfad innerhalb des Basispfades der Anwendung an die der Benutzer-Agent verwiesen wird: [MicrosoftAccountAuthenticationOptions.CallbackPath](https://docs.microsoft.com/previous-versions/aspnet/mt174433(v=vs.113)?redirectedfrom=MSDN).
- **Als Authentifizierungstyp anmelden** – Der Name einer weiteren Authentifizierungs-Middleware, die für die tatsächliche Ausstellung einer Benutzeranspruchsidentität verantwortlich ist: [MicrosoftAccountAuthenticationOptions.SignInAsAuthenticationType](https://docs.microsoft.com/previous-versions/aspnet/mt174430(v=vs.113)?redirectedfrom=MSDN).
- **Umfang** – Eine durch Kommas getrennte Liste der anzufordernden Berechtigungen: [MicrosoftAccountAuthenticationOptions.Scope](https://docs.microsoft.com/previous-versions/aspnet/mt174435(v=vs.113)?redirectedfrom=MSDN).
- **Registrierung aktiviert**: Aktiviert oder deaktiviert die Registrierungsanforderung für den vorhandenen Identitätsanbieter. Wenn deaktiviert, wird dem Benutzer die Registrierung mit einem Fehler verweigert, wenn für den Benutzer kein Kontaktdatensatz vorhanden ist. Wenn aktiviert, wird die Benutzerregistrierung für einen neuen Benutzer nur gewährt, wenn für die Websiteeinstellung **Authentication/Registration/Enabled** auch "true" festgelegt ist.

Weitere Informationen finden Sie unter [OAuth 2-Websiteeinstellungen](configure-oauth2-settings.md#create-site-settings-by-using-oauth2).

### <a name="see-also"></a>Siehe auch

- [Festlegen der Authentifizierungsidentität für ein Portal](set-authentication-identity.md)
- [Azure AD-Anbietereinstellungen konfigurieren](azure-ad-b2c.md)
- [OAuth2-Anbietereinstellungen konfigurieren](configure-oauth2-settings.md)
