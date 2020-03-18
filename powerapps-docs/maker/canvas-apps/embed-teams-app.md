---
title: Einbetten einer APP in Teams | Microsoft-Dokumentation
description: Sie können eine in Power apps erstellte app in Microsoft Teams einbetten, um Sie freizugeben.
author: matthewbolanos
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 03/16/2020
ms.author: mabolan
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 088e817c8ef829b340032af577193888079c832a
ms.sourcegitcommit: cf492063eca27fdf73459ff2f9134f2ca04ee766
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79436832"
---
# <a name="embed-an-app-in-teams"></a>Einbetten einer App in Teams

Sie können eine von Ihnen erstellte App freigeben, indem Sie Sie direkt in Microsoft Teams einbetten. Wenn Sie fertig sind, können Benutzer **+** auswählen, um Ihre APP zu einem **ihrer** teamchannels oder Konversationen in dem Team hinzuzufügen, in dem Sie sich befinden. Die APP wird als Kachel für das **Team unter Registerkarten**angezeigt.

Ein Administrator kann die APP hochladen, sodass er für **alle** Teams in Ihrem Mandanten im **Abschnitt alle Registerkarten**angezeigt wird. Weitere Informationen finden Sie [unter Freigeben einer APP in Microsoft Teams](https://docs.microsoft.com/power-platform/admin/embed-app-teams).

> [!NOTE]
> Benutzerdefinierte App-Richtlinien müssen festgelegt werden, damit benutzerdefinierte apps hochgeladen werden können Wenn Sie Ihre APP nicht in Teams einbetten können, wenden Sie sich an Ihren Administrator, um festzustellen, ob [benutzerdefinierte App-Einstellungen](https://docs.microsoft.com/MicrosoftTeams/teams-custom-app-policies-and-settings#custom-app-policy-and-settings)eingerichtet wurden.

## <a name="prerequisites"></a>Erforderliche Komponenten

- Sie benötigen eine gültige [powerapps-Lizenz](https://docs.microsoft.com/power-platform/admin/pricing-billing-skus).
- Zum Einbetten einer APP in Teams benötigen Sie eine vorhandene APP, die [mit powerapps erstellt](data-platform-create-app.md)wurde.

## <a name="download-the-app"></a>Herunterladen der App

1. Melden Sie sich bei [make.powerapps.com](https://make.powerapps.com)an, und wählen Sie dann im Menü **apps** aus.

    ![Liste der apps anzeigen](./media/embed-teams-app/file-apps2.png "Anzeigen der App-Liste")

2. Wählen Sie **Weitere Aktionen** (...) für die APP aus, die Sie in Teams freigeben möchten, und wählen Sie dann **zu Teams hinzufügen**aus.

    ![App-Details](./media/embed-teams-app/add-to-teams.png "Zu Teams hinzufügen")

3. Wählen Sie im Bereich zu Teams hinzufügen die Option **herunterladen**aus. Powerapps generiert dann die Manifest-Datei des Teams mithilfe der APP-Beschreibung und des Logos, das Sie bereits in Ihrer APP festgelegt haben.

    ![App-Details](./media/embed-teams-app/download-app.png "App herunterladen")

## <a name="add-the-app-as-a-personal-app"></a>Hinzufügen der App als persönliche App

1. Wählen Sie im linken Navigationsbereich **apps** aus, und wählen Sie dann **benutzerdefinierte App hochladen**aus, um die APP als persönliche APP oder als Registerkarte zu einem Kanal oder einer Konversation hinzuzufügen.

    > [!NOTE]
    > Die **benutzerdefinierte App hochladen** wird nur angezeigt, wenn Ihr Team Administrator eine [benutzerdefinierte App-Richtlinie](https://docs.microsoft.com/microsoftteams/teams-app-setup-policies) erstellt und das **Hochladen von benutzerdefinierten apps**aktiviert hat.

    ![App als Registerkarte hinzufügen](./media/embed-teams-app/upload-custom-app.png "Hochladen einer benutzerdefinierten App")

2. Wählen Sie **Hinzufügen** , um die APP als persönliche App hinzuzufügen, oder wählen Sie **zum Team hinzufügen** aus, um die APP als Registerkarte innerhalb eines vorhandenen Kanals oder einer Konversation hinzuzufügen

## <a name="publish-the-app-to-the-teams-catalog"></a>Veröffentlichen der APP im Teams-Katalog

Wenn Sie ein Administrator sind, können Sie [die APP](https://docs.microsoft.com/microsoftteams/tenant-apps-catalog-teams) auch im Microsoft Teams-Katalog veröffentlichen.

## <a name="use-context-from-teams"></a>Kontext aus Teams verwenden

Um tief integrierte apps mit Teams zu erstellen, können Sie die Kontext Variablen des Teams mit der `Param()`-Funktion verwenden. Verwenden Sie beispielsweise die folgende Formel in der **Fill** -Eigenschaft des Bildschirms, um den Hintergrund der App basierend auf dem Design des Benutzers innerhalb von Teams zu ändern:

```
Switch(
        Param("theme"),
        "dark",
        RGBA(
            32,
            31,
            31,
            1
        ),
        "contrast",
        RGBA(
            0,
            0,
            0,
            1
        ),
        RGBA(
            243,
            242,
            241,
            1
        )
    )
```

Um die APP zu testen, veröffentlichen Sie Sie, und geben Sie Sie dann in Teams wieder.

Die folgenden Kontext Variablen von Teams werden unterstützt:

- locale
- channelId
- channelType
- chatid
- groupId
- hostclienttype
- subentityid
- TeamID
- Teamtyp
- Design
- userteamrole

> [!NOTE]
> Diese Funktion wurde im März 2020 hinzugefügt. Wenn Sie Ihre APP zuvor in Teams eingebettet haben, müssen Sie die APP ggf. erneut zu Teams hinzufügen, um diese Funktion nutzen zu können.

## <a name="improve-the-performance-of-your-app"></a>Verbessern Sie die Leistung Ihrer APP

Optional können Sie Ihre APP innerhalb von Teams vorab laden, um die Leistung zu verbessern.

1. Melden Sie sich bei [make.powerapps.com](https://make.powerapps.com)an, und wählen Sie dann im Menü **apps** aus.

2. Wählen Sie **Weitere Aktionen** (...) für die APP aus, die Sie in Teams freigeben möchten, und wählen Sie dann **Einstellungen**aus.

3. Wechseln **Sie im**Einstellungsbereich **zum vorab laden der APP, um die Leistung** zu verbessern. Die APP wird dann vorab geladen, wenn Sie in Teams eingebettet ist.

    ![App-Details](./media/embed-teams-app/preload-app.png "App vorab laden, um die Leistung zu verbessern")

4. Damit die Änderungen wirksam werden, entfernen Sie Ihre APP, und fügen Sie Sie wieder den Teams hinzu.

> [!NOTE]
> Dadurch können Benutzer die APP-Datei herunterladen, während die Authentifizierung für eingebettete Szenarien ausgeführt wird. Die Benutzer können die APP jedoch erst nach erfolgreicher Authentifizierung ausführen. Dadurch wird sichergestellt, dass Ihre APP-Daten für nicht authentifizierte Benutzer nicht verfügbar sind.

### <a name="see-also"></a>Siehe auch

[Willkommen bei Microsoft Teams](https://docs.microsoft.com/MicrosoftTeams/teams-overview)
