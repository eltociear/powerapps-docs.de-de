---
title: Einbetten einer PowerApps-app in Teams | Microsoft-Dokumentation
description: Sie können eine app in PowerApps in Microsoft Teams freigeben erstelltes einbetten.
author: jimholtz
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 05/29/2019
ms.author: jimholtz
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: d17b02cc87bb219474aade955a2910f12fcf7f27
ms.sourcegitcommit: 2376c1f1f3431bca52a8deb9b966ce1fe9f88da0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/30/2019
ms.locfileid: "66381384"
---
# <a name="embed-a-powerapps-app-in-teams"></a>Einbetten einer PowerApps-app in Teams 

Sie können eine PowerApps freigeben, die Sie erstellt haben, durch die sie direkt in Microsoft Teams-Einbettung. Benutzer können auswählen, wenn abgeschlossen, **+** keines Ihrer app hinzufügen **Ihre** team-Kanäle oder Konversationen in das Team Sie befinden sich im. Die app angezeigt wird, als Kachel unter **Registerkarten für Ihr Team**. 

Ein Administrator kann Hochladen der app, damit er angezeigt wird **alle** Teams in Ihrem Mandanten, unter der **alle Registerkarten Abschnitt**. Finden Sie unter [Freigeben einer app in Microsoft Teams](https://review.docs.microsoft.com/en-us/power-platform/admin/embed-app-teams?branch=JimHoltzWorkBranch).

> [!NOTE]
> Team benutzerdefinierte app-Richtlinien müssen festgelegt werden, um das Hochladen von benutzerdefinierten apps zu ermöglichen. Wenn dies nicht möglich, Ihre app in Teams einzubetten, überprüfen Sie Ihren Administrator, um festzustellen, ob sie Setup haben [benutzerdefinierte app-Einstellungen](https://docs.microsoft.com/MicrosoftTeams/teams-custom-app-policies-and-settings#custom-app-policy-and-settings). 

## <a name="prerequisites"></a>Voraussetzungen

- [Haben Sie eine PowerApps-Lizenz](https://docs.microsoft.com/power-platform/admin/pricing-billing-skus)
- Erstellt eine Canvas-app

## <a name="locate-your-powerapps-guid"></a>Suchen Ihrer PowerApp GUID

Suchen und notieren Sie sich Ihrer PowerApp GUID zur Verwendung in einem späteren Schritt.

1. Melden Sie sich beim [ https://web.powerapps.com ](https://web.powerapps.com), und wählen Sie dann **Apps** im Menü.

   > [!div class="mx-imgBorder"] 
   > ![Zeigt eine Liste der apps](./media/embed-teams-app/file-apps2.png "Liste der apps anzeigen")

2. Wählen Sie **weitere Befehle** (...) für die app, die Sie verwenden möchten, in Teams, und wählen Sie dann **Details**.

   > [!div class="mx-imgBorder"] 
   > ![App-Details](./media/embed-teams-app/app-details.png "App-Details")

3. Datensatz der **App-ID** für die spätere Verwendung.

   > [!div class="mx-imgBorder"] 
   > ![App-Details](./media/embed-teams-app/app-details2.png "App-Details")

## <a name="install-app-studio"></a>Installieren von App Studio

Sie können diese Schritte überspringen, wenn die App Studio bereits installiert ist. 

1. Wählen Sie in Teams **Apps** in der linken unteren Ecke des Teams Menüs (![Symbol "Apps"](./media/embed-teams-app/apps-icon.png "Symbol \"Apps\"")).

2. Suchen Sie nach "App Studio" in das Suchfeld, und wählen Sie ihn.

   > [!div class="mx-imgBorder"] 
   > ![App Studio](./media/embed-teams-app/store-app-studio.png "App Studio")

3. Wählen Sie **installieren**. 

   > [!div class="mx-imgBorder"] 
   > ![Installieren von App Studio](./media/embed-teams-app/install-app-studio.png "App Studio installieren")

4. Wählen Sie **öffnen** für das App-Feature.

   > [!div class="mx-imgBorder"] 
   > ![Öffnen Sie die App Studio](./media/embed-teams-app/open-app-studio.png "App Studio öffnen")

## <a name="create-a-teams-app-for-your-powerapp"></a>Erstellen einer app für die Teams für Ihrer PowerApp

1. Öffnen Sie in Teams die App Studio aus.

   > [!div class="mx-imgBorder"] 
   > ![Öffnen Sie die App Studio](./media/embed-teams-app/open-app-studio2.png "App Studio öffnen")

2. Wählen Sie die **Manifest-Editor** Registerkarte, und wählen Sie dann **Erstellen einer neuen app** unter Willkommen.

   > [!div class="mx-imgBorder"] 
   > ![Neue Anwendung erstellen](./media/embed-teams-app/create-new-app.png "neue app erstellen")

3. Geben Sie Informationen zu Ihrer app in der **App-Details** Seite.  Für die App-ID-GUID sollten Sie Ihrer PowerApp-App-ID-GUID verwenden, die Sie oben notiert haben.  Dadurch werden die Duplizierung von Teams-apps für eine bestimmte PowerApp vermieden.
 
   > [!div class="mx-imgBorder"] 
   > ![Geben Sie Informationen](./media/embed-teams-app/fill-in-info-about-app.png "geben Informationen")

   |Felder  |Beschreibung  |
   |---------|---------|
   |**App-Namen** |    |
   |Kurzname     | Erforderlich. Der kurze Anzeigename für die app. maximal 30 Zeichen.        |
   |Langer name     | Der vollständige Name der app verwendet, wenn der vollständige app-Name 30 Zeichen überschreitet.       | 
   |**Kennung**     |         |
   |App-ID     | Erforderlich. Der eindeutige Microsoft generierter Bezeichner für diese app.        |
   |Paketname     | Erforderlich. Ein eindeutiger Bezeichner für diese app. Es wird empfohlen, mithilfe der Notation für Domäne; z. B. com.example. <AppName>.       |
   |Version     | Erforderlich. Die Version des der jeweiligen app. Wenn Sie etwas in Ihrem Manifest aktualisieren, muss die Version ebenfalls erhöht.     |
   |**Eine Beschreibung**    |     |
   | Kurzbeschreibung    | Erforderlich. Eine kurze Beschreibung der Ihre app-Erfahrung, die verwendet werden, wenn der Speicherplatz begrenzt ist. maximal 80 Zeichen.   |
   | Lange Beschreibung    | Erforderlich. Die vollständige Beschreibung der app.     |
   | **Informationen für Entwickler**    |     |
   | Name    | Erforderlich. Der Anzeigename für den Firmen- oder Entwicklername.     |
   | Website    | Erforderlich. Die URL https:// der Website für Ihre app über powerapps.com. Wenn ein Benutzer Ihre app installiert wird ein "zu Ihrer app" die Seite wird angezeigt. Sie sollten auf die Webversion Ihrer App auf powerapps.com verknüpfen.   |
   | **App-URLs**    | Diese Links angezeigt wird, der **zu** Seite zusammen mit der Website-URL.     |
   | Datenschutzbestimmungen    | Erforderlich. Die URL https:// Datenschutzrichtlinie des Entwicklers. [Beispiel](https://go.microsoft.com/fwlink/p/?LinkID=698505).   |
   | Nutzungsbedingungen    | Erforderlich. Die URL https:// Nutzungsbedingungen des Entwicklers.  [Beispiel](https://go.microsoft.com/fwlink/p/?LinkID=698507).  |
   | **Branding**    |     |
   | Vollständige Farbe    | Ein relativer Pfad zu einer vollständigen Farbe 192 x 192 PNG-Symbol.    |
   | Transparenten Umriss    |Ein relativer Pfad zu einer transparenten Umriss für 32 x 32 PNG.     |
   | Farbe für Akzente    | Eine Farbe in Verbindung mit und als Hintergrund für die Gliederung Symbole verwendet werden soll.     |

Weitere Informationen finden Sie unter [Manifest-Editor](https://docs.microsoft.com/microsoftteams/platform/get-started/get-started-app-studio#manifest-editor) und [Manifestschema](https://docs.microsoft.com/microsoftteams/platform/resources/schema/manifest-schema).

4. Scrollen Sie im Abschnitt Branding, und fügen Sie Ihre Logos und der Farbe für Akzente für Ihre app gewünscht hinzu.  Hierbei handelt es sich um die Logos, die für Ihre app in Teams angezeigt werden. 

   > [!div class="mx-imgBorder"] 
   > ![Branding und Registerkarten](./media/embed-teams-app/branding-tabs.png "Branding und Registerkarten")

5. Klicken Sie unter **Funktionen**Option **Registerkarten**.

6. Klicken Sie unter **Registerkarte Team** wählen **hinzufügen**.

   > [!div class="mx-imgBorder"] 
   > ![Registerkarte "Team" Add](./media/embed-teams-app/team-tab-add.png "Registerkarte Team hinzufügen")

7. Fügen Sie die URL Ihrer app-Konfiguration in das Eingabefeld "Konfigurations-URL", mit dem folgenden Format: `https://web.powerapps.com/webplayer/teamsapptabsettings?appid=<PowerApp ID>`

   Ersetzen Sie dies `<PowerApp ID>` mit der App-ID-GUID, die Sie oben notiert haben.

   Wählen Sie die [Bereich](https://docs.microsoft.com/microsoftteams/platform/concepts/tabs/tabs-overview#tab-scope) für Ihre app angezeigt werden. Stellen Sie sicher **können Konfiguration aktualisieren** aktiviert ist, und wählen Sie dann **speichern**.

   > [!div class="mx-imgBorder"] 
   > ![Konfigurations-URL](./media/embed-teams-app/configuration-url.png "Konfigurations-URL")

8. Klicken Sie unter **Fertig stellen**Option **gültige Domänen**. Hinzufügen **apps.powerapps.com** und **apps.preview.powerapps.com** als gültige Domänen für die Anwendung des Teams.

   > [!div class="mx-imgBorder"] 
   > ![Fügen Sie gültige Domänen](./media/embed-teams-app/add-valid-domains.png "gültige Domänen hinzufügen")

9. Klicken Sie unter **Fertig stellen**Option **testen und Verteilen von**. Klicken Sie unter **installieren**Option **installieren**.

   > [!div class="mx-imgBorder"] 
   > ![Wählen Sie die Installation](./media/embed-teams-app/test-distribute-app.png "Installation auswählen")

10. Wählen Sie das Team die app installiert werden sollen, und wählen Sie dann **installieren**.

    > [!div class="mx-imgBorder"] 
    > ![Hinzufügen, installieren Sie team](./media/embed-teams-app/new-app-add-to-team.png "zur Installation team hinzufügen")

11. Wenn Sie eine Instanz der app direkt in einem Kanal hinzufügen möchten, wählen Sie den Kanal, der die app, und wählen in verwenden möchten **einrichten**.

    > [!div class="mx-imgBorder"] 
    > ![Wählen Sie Sie](./media/embed-teams-app/app-now-available.png "einrichten auswählen")

12. Wählen Sie **Speichern**.

## <a name="add-the-app-as-a-tab"></a>Die app als Registerkarte hinzufügen

Wählen Sie zum Hinzufügen der app als Registerkarte Kanal oder Unterhaltung **+** , und klicken Sie dann unter **Registerkarten für Ihr Team** wählen Sie Ihre app. 

> [!div class="mx-imgBorder"] 
> ![App als Registerkarte hinzufügen](./media/embed-teams-app/add-app-as-tab.png "app als Registerkarte hinzufügen")

Die app wird jetzt als Registerkarte angezeigt.

> [!div class="mx-imgBorder"] 
> ![App als Registerkarte](./media/embed-teams-app/app-as-tab.png "App als Registerkarte")

### <a name="see-also"></a>Siehe auch
[Willkommen bei Microsoft Teams](https://docs.microsoft.com/MicrosoftTeams/teams-overview)<br />
[Für Administratoren: Einbetten einer app in Microsoft Teams](https://docs.microsoft.com/power-platform/admin/share-app-teams)