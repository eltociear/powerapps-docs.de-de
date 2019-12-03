---
title: Einbetten einer APP in Teams | Microsoft-Dokumentation
description: Sie können eine in Power apps erstellte app in Microsoft Teams einbetten, um Sie freizugeben.
author: matthewbolanos
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/29/2019
ms.author: mabolan
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: a12cd7c17a6aca93f254cc2e2cb89cb848245392
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2019
ms.locfileid: "74731504"
---
# <a name="embed-an-app-in-teams"></a>Einbetten einer App in Teams

Sie können eine von Ihnen erstellte Power-App freigeben, indem Sie Sie direkt in Microsoft Teams einbetten. Wenn Sie fertig sind, können Benutzer **+** auswählen, um Ihre APP zu einem **ihrer** teamchannels oder Konversationen in dem Team hinzuzufügen, in dem Sie sich befinden. Die APP wird als Kachel für das **Team unter Registerkarten**angezeigt.

Ein Administrator kann die APP hochladen, sodass er für **alle** Teams in Ihrem Mandanten im **Abschnitt alle Registerkarten**angezeigt wird. Weitere Informationen finden Sie [unter Freigeben einer APP in Microsoft Teams](https://docs.microsoft.com/power-platform/admin/embed-app-teams).

> [!NOTE]
> Benutzerdefinierte App-Richtlinien müssen festgelegt werden, damit benutzerdefinierte apps hochgeladen werden können Wenn Sie Ihre APP nicht in Teams einbetten können, wenden Sie sich an Ihren Administrator, um festzustellen, ob [benutzerdefinierte App-Einstellungen](https://docs.microsoft.com/MicrosoftTeams/teams-custom-app-policies-and-settings#custom-app-policy-and-settings)eingerichtet wurden.

## <a name="prerequisites"></a>Voraussetzungen

- Sie benötigen eine gültige [powerapps-Lizenz](https://docs.microsoft.com/power-platform/admin/pricing-billing-skus).
- Zum Einbetten einer APP in Teams benötigen Sie eine vorhandene APP, die [mit powerapps erstellt](data-platform-create-app.md)wurde.

## <a name="download-the-app"></a>Herunterladen der APP

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

## <a name="publish-the-app-to-the-teams-catalogue"></a>Veröffentlichen der APP im Teams-Katalog

Wenn Sie ein Administrator sind, können Sie [die APP](https://docs.microsoft.com/microsoftteams/tenant-apps-catalog-teams) auch im Microsoft Teams-Katalog veröffentlichen.

### <a name="see-also"></a>Siehe auch

[Willkommen bei Microsoft Teams](https://docs.microsoft.com/MicrosoftTeams/teams-overview)
