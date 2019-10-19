---
title: Einbetten einer powerapps-app in Teams | Microsoft-Dokumentation
description: Sie können eine APP einbetten, die in powerapps in Microsoft Teams erstellt wurde, um Sie freizugeben.
author: jimholtz
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 09/09/2019
ms.author: jimholtz
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: ba08437dc144fc81aa9748163b1005222735cb69
ms.sourcegitcommit: a560630f5ee83629a7236ae774fc0c8195b95efa
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "70842234"
---
# <a name="embed-a-powerapps-app-in-teams"></a>Einbetten einer powerapps-app in Teams 

Sie können powerapps freigeben, die Sie erstellt haben, indem Sie Sie direkt in Microsoft Teams einbetten. Wenn Sie fertig sind, können Benutzer **+** auswählen, um Ihre APP zu einem **ihrer** teamchannels oder Konversationen in dem Team hinzuzufügen, in dem Sie sich befinden. Die APP wird als Kachel für das **Team unter Registerkarten**angezeigt. 

Ein Administrator kann die APP hochladen, sodass er für **alle** Teams in Ihrem Mandanten im **Abschnitt alle Registerkarten**angezeigt wird. Weitere Informationen finden Sie [unter Freigeben einer APP in Microsoft Teams](https://docs.microsoft.com/en-us/power-platform/admin/embed-app-teams).

> [!NOTE]
> Benutzerdefinierte App-Richtlinien müssen festgelegt werden, damit benutzerdefinierte apps hochgeladen werden können Wenn Ihre APP nicht in Teams eingebettet werden kann, wenden Sie sich an Ihren Administrator, um festzustellen, ob [benutzerdefinierte App-Einstellungen](https://docs.microsoft.com/MicrosoftTeams/teams-custom-app-policies-and-settings#custom-app-policy-and-settings)eingerichtet wurden. 

## <a name="prerequisites"></a>Voraussetzungen

- [Powerapps-Lizenz](https://docs.microsoft.com/power-platform/admin/pricing-billing-skus)
- Erstellen einer Canvas-App

## <a name="locate-your-powerapps-guid"></a>Suchen Sie die GUID ihrer PowerApp.

Suchen Sie die GUID ihrer PowerApp, die Sie in einem späteren Schritt verwenden möchten, und notieren Sie Sie.

1. Melden Sie sich bei [https://web.powerapps.com](https://web.powerapps.com)an, und wählen Sie dann im Menü **apps** aus.

   > [!div class="mx-imgBorder"] 
   > ![Liste der apps anzeigen](./media/embed-teams-app/file-apps2.png "Anzeigen der App-Liste")

2. Wählen Sie **Weitere Befehle** (...) für die APP aus, die Sie in Teams freigeben möchten, und wählen Sie dann **Details**aus.

   > [!div class="mx-imgBorder"] 
   > ![App-Details](./media/embed-teams-app/app-details.png "App-Details")


3. Notieren Sie die **App-ID** für die spätere Verwendung.

   > [!div class="mx-imgBorder"] 
   > ![App-Details](./media/embed-teams-app/app-details2.png "App-Details")

## <a name="install-app-studio"></a>Installieren von App Studio

Sie können diese Schritte überspringen, wenn APP Studio bereits installiert ist. 

1. Wählen Sie in Teams links unten im Menü Teams (![Symbol "Apps](./media/embed-teams-app/apps-icon.png "Symbol "Apps"")") die Option **apps** aus.

2. Suchen Sie im Suchfeld nach "App Studio", und wählen Sie es aus.

   > [!div class="mx-imgBorder"] 
   > ![App Studio](./media/embed-teams-app/store-app-studio.png "App Studio")

3. Wählen Sie **Installieren**aus. 

   > [!div class="mx-imgBorder"] 
   > ![Installieren von App Studio](./media/embed-teams-app/install-app-studio.png "Installieren von App Studio")

4. Wählen Sie für die App-Funktion **Öffnen** aus.

   > [!div class="mx-imgBorder"] 
   > ![App Studio öffnen](./media/embed-teams-app/open-app-studio.png "App Studio öffnen")

## <a name="create-a-teams-app-for-your-powerapp"></a>Erstellen einer Teams-App für Ihre PowerApp

1. Öffnen Sie App Studio in Teams.

   > [!div class="mx-imgBorder"] 
   > ![App Studio öffnen](./media/embed-teams-app/open-app-studio2.png "App Studio öffnen")

2. Wählen Sie die Registerkarte **Manifest-Editor** aus, und wählen Sie dann unter Willkommen die Option **neue APP erstellen** aus.

   > [!div class="mx-imgBorder"] 
   > ![Neue APP erstellen](./media/embed-teams-app/create-new-app.png "Neue Rolle erstellen")

3. Geben Sie auf der Seite "App- **Details** " Informationen zu Ihrer APP ein.  Für die APP-ID-GUID sollten Sie die oben aufgezeichnete APP-ID-GUID ihrer PowerApp verwenden.  Dadurch wird das Duplizieren von Teams-Apps für eine bestimmte PowerApp vermieden.
 
   > [!div class="mx-imgBorder"] 
   > ![Informationen ausfüllen](./media/embed-teams-app/fill-in-info-about-app.png "Informationen ausfüllen")

   |Felder  |Beschreibung  |
   |---------|---------|
   |**APP-Namen** |    |
   |Kurzname     | Erforderlich. Der kurze Anzeige Name für die app. maximal 30 Zeichen.        |
   |Langer Name     | Der vollständige Name der APP, der verwendet wird, wenn der vollständige Name der APP länger als 30 Zeichen ist.       | 
   |**Identifi**     |         |
   |APP-ID     | Erforderlich. Der eindeutige von Microsoft generierte Bezeichner für diese APP.        |
   |Paketname     | Erforderlich. Ein eindeutiger Bezeichner für diese APP. Es wird empfohlen, die umgekehrte Domänen Notation zu verwenden; Beispiel: com. example. <AppName>.       |
   |Version     | Erforderlich. Die Version der bestimmten app. Wenn Sie etwas in ihrem Manifest aktualisieren, muss die Version ebenfalls inkrementiert werden.     |
   |**Beschreibungen**    |     |
   | Kurze Beschreibung    | Erforderlich. Eine kurze Beschreibung ihrer App-Funktion, die verwendet wird, wenn Speicherplatz begrenzt ist. 80 Zeichenlimit.   |
   | Lange Beschreibung    | Erforderlich. Die vollständige Beschreibung Ihrer APP.     |
   | **Entwicklerinformationen**    |     |
   | Name    | Erforderlich. Der Anzeige Name für das Unternehmen oder den Entwickler.     |
   | Website    | Erforderlich. Die https://-URL zur Website für Ihre APP über powerapps.com. Wenn eine Person Ihre APP installiert, wird die Seite "About Your App" angezeigt. Er sollte mit der Webversion Ihrer APP auf powerapps.com verknüpft werden.   |
   | **App-URLs**    | Diese Links werden zusammen mit der Website-URL **auf der Seite** "Info" angezeigt.     |
   | Datenschutzbestimmungen    | Erforderlich. Die https://-URL zur Datenschutzrichtlinie des Entwicklers. [Beispiel](https://go.microsoft.com/fwlink/p/?LinkID=698505).   |
   | Nutzungsbedingungen    | Erforderlich. Die https://-URL für die Nutzungsbedingungen des Entwicklers.  [Beispiel](https://go.microsoft.com/fwlink/p/?LinkID=698507).  |
   | **BR**    |     |
   | Vollständige Farbe    | Ein relativer Dateipfad zu einem vollständigen Farb-, 192x192 PNG-Symbol.    |
   | Transparenter Umriss    |Ein relativer Dateipfad zu einem transparenten x 32-PNG-Umriss Symbol.     |
   | Akzentfarbe    | Eine Farbe, die zusammen mit und als Hintergrund für Ihre Umriss Symbole verwendet werden soll.     |

Weitere Informationen finden Sie unter [Manifest-Editor](https://docs.microsoft.com/microsoftteams/platform/get-started/get-started-app-studio#manifest-editor) und [Manifest-Schema](https://docs.microsoft.com/microsoftteams/platform/resources/schema/manifest-schema).

4. Scrollen Sie nach unten zum brandingabschnitt, und fügen Sie Ihre Logos und die gewünschte Akzentfarbe für Ihre APP hinzu.  Dies sind die Logos, die für Ihre APP in Teams angezeigt werden. 

   > [!div class="mx-imgBorder"] 
   > ![Branding und Registerkarten](./media/embed-teams-app/branding-tabs.png "Branding und Registerkarten")

5. Wählen Sie unter **Funktionen**die Option **Registerkarten**aus.

6. Klicken Sie unter **Team Registerkarte** auf **Hinzufügen**.

   > [!div class="mx-imgBorder"] 
   > ![Team Registerkarte hinzufügen](./media/embed-teams-app/team-tab-add.png "Team Registerkarte hinzufügen")

7. Fügen Sie die Konfigurations-URL Ihrer APP im Eingabefeld "Konfigurations-URL" unter Verwendung des folgenden Formats hinzu: `https://apps.powerapps.com/teams/settings/<PowerApp ID>`

   Ersetzen Sie `<PowerApp ID>` durch die zuvor aufgezeichnete APP-ID-GUID.

   Wählen Sie den [Bereich](https://docs.microsoft.com/microsoftteams/platform/concepts/tabs/tabs-overview#tab-scope) aus, in dem Ihre APP angezeigt werden soll. Stellen Sie sicher, dass **Update Konfiguration** aktiviert ist, und wählen Sie dann **Speichern**aus.

   > [!div class="mx-imgBorder"] 
   > ![Konfigurations-URL](./media/embed-teams-app/configuration-url.png "Konfigurations-URL")

8. Wählen Sie unter **Fertig**stellen die Option **gültige Domänen**aus. Fügen Sie **apps.powerapps.com** und **apps.Preview.powerapps.com** als gültige Domänen für die Anwendung Teams hinzu.

   > [!div class="mx-imgBorder"] 
   > ![Gültige Domänen hinzufügen](./media/embed-teams-app/add-valid-domains.png "Gültige Domänen hinzufügen")

9. Wählen Sie unter **Fertig**stellen die Option **Testen und verteilen**aus. Wählen Sie unter **Installieren**die Option **Installieren**aus.

   > [!div class="mx-imgBorder"] 
   > ![Wählen Sie installieren](./media/embed-teams-app/test-distribute-app.png "Wählen Sie installieren")

10. Wählen Sie das Team aus, in dem Sie die APP installieren möchten, und klicken Sie dann auf **Installieren**.

    > [!div class="mx-imgBorder"] 
    > ![Zu Team Installation hinzufügen](./media/embed-teams-app/new-app-add-to-team.png "Zu Team Installation hinzufügen")
11. Wenn Sie eine Instanz dieser APP sofort einem Kanal hinzufügen möchten, wählen Sie den Kanal aus, in dem Sie die APP verwenden möchten, und wählen Sie **Einrichten**aus.

    > [!div class="mx-imgBorder"] 
    > ![Wählen Sie einrichten aus.](./media/embed-teams-app/app-now-available.png "Wählen Sie einrichten aus.")

12. Wählen Sie **Speichern**.

## <a name="add-the-app-as-a-tab"></a>Hinzufügen der App als Registerkarte

Wenn Sie die APP als Registerkarte zu einem Kanal oder einer Konversation hinzufügen möchten, wählen Sie **+** aus, und wählen Sie dann unter **Registerkarten für das Team** Ihre APP aus 

> [!div class="mx-imgBorder"] 
> ![App als Registerkarte hinzufügen](./media/embed-teams-app/add-app-as-tab.png "App als Registerkarte hinzufügen")

Die APP wird jetzt als Registerkarte angezeigt.

> [!div class="mx-imgBorder"] 
> ![App als Registerkarte](./media/embed-teams-app/app-as-tab.png "App als Registerkarte")

### <a name="see-also"></a>Siehe auch
[Willkommen bei Microsoft Teams](https://docs.microsoft.com/MicrosoftTeams/teams-overview)<br />
[Für Administratoren: Einbetten einer APP in Microsoft Teams](https://docs.microsoft.com/power-platform/admin/share-app-teams)
