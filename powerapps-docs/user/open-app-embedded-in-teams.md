---
title: Hinzufügen einer App zu Microsoft Teams | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie einem Microsoft Teams-Kanal eine App hinzufügen, damit alle Benutzer, für die die App freigeben wurde, diese in dem Kanal öffnen können.
author: mgblythe
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: quickstart
ms.date: 11/16/2018
ms.author: matp
ms.custom: ''
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 34fc4f9603ebfcb9944b871f211a6b1541235ed5
ms.sourcegitcommit: 483c777a1537ccab6a2a2da6a5d1fe4470dd0e7e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2019
ms.locfileid: "63321667"
---
# <a name="add-an-app-to-microsoft-teams"></a>Hinzufügen einer App zu Microsoft Teams

Bei Microsoft Teams handelt es sich im eine auf Chats basierende Plattform für die Zusammenarbeit, die auf Office 365-Technologien aufbaut. Sie können die Benutzerfreundlichkeit von Microsoft Teams verbessern, indem Sie Ihrem Kanal in Microsoft Teams mit PowerApps generierte Canvas-Apps hinzufügen. In diesem Thema erfahren Sie, wie Sie die Beispiel-App für Product Showcase erst zu dem Teams-Kanal hinzufügen und dann die App über diesen Kanal öffnen. 

![In Microsoft Teams eingebettete App](./media/open-app-embedded-in-teams/embedded-app.png)

Wenn Sie noch nicht bei PowerApps registriert sind, müssen Sie sich zuerst [kostenlos registrieren](https://web.powerapps.com/signup?redirect=marketing&email=).

## <a name="prerequisites"></a>Voraussetzungen

Sie benötigen hierzu ein [Office 365-Abonnement](https://signup.microsoft.com/Signup?OfferId=467eab54-127b-42d3-b046-3844b860bebf&dl=O365_BUSINESS_PREMIUM&ali=1) und einen [Kanal in Microsoft Teams](https://www.youtube.com/watch?v=he2f1quaR7M).

## <a name="sign-in-to-powerapps"></a>Anmelden bei PowerApps

Melden Sie sich unter [https://web.powerapps.com](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) in PowerApps an.

## <a name="add-an-app"></a>Hinzufügen einer App

1. Wählen Sie in Microsoft Teams ein Team und einen Kanal des Teams aus. In diesem Beispiel wird der Kanal **Allgemein** des Teams **Business Development** verwendet.

    ![](./media/open-app-embedded-in-teams/teams-select-channel.png)

2. Klicken Sie auf **+** , um eine Registerkarte hinzuzufügen.

    ![](./media/open-app-embedded-in-teams/teams-add-tab.png)

3. Klicken oder tippen Sie im Dialogfeld **Add a tab** (Registerkarte hinzufügen) auf **PowerApps**.

    ![](./media/open-app-embedded-in-teams/add-a-tab.png)

4. Klicken Sie auf **Beispiel-Apps** > **Product Showcase** > **Speichern**.

    ![](./media/open-app-embedded-in-teams/select-an-app.png)

    Die App kann jetzt im Kanal verwendet werden.

    ![](./media/open-app-embedded-in-teams/app-in-channel.png)

> [!NOTE]
> Beispiel-Apps werden standardmäßig automatisch freigegeben, aber Sie müssen Ihre eigenen Apps [freigeben](../maker/canvas-apps/share-app.md), bevor Sie sie zu Microsoft Teams hinzufügen können.

## <a name="open-an-app"></a>Öffnen einer App

1. Wählen Sie in Microsoft Teams das Team und den Kanal aus, der die App enthält.

    ![](./media/open-app-embedded-in-teams/teams-select-channel.png)

2. Klicken Sie auf die Registerkarte **Product Showcase**.

    ![](./media/open-app-embedded-in-teams/open-tab.png)

    Die App wird im Kanal geöffnet.

    ![](./media/open-app-embedded-in-teams/app-in-channel.png)

## <a name="known-issues"></a>Bekannte Probleme

In der Desktop-App für Microsoft Teams:

* Apps müssen Inhalte wie Bilder und PDF-Dateien über eine sichere (HTTPS-) Verbindung laden.
* Nicht alle Sensoren, z. B. **Acceleration**, **Compass** und **Location**, werden unterstützt.
* Nur diese Audioformate werden unterstützt: AAC, H264, Ogg Vorbis und WAV.

## <a name="clean-up-resources"></a>Bereinigen von Ressourcen

Wenn Sie die App aus dem Kanal entfernen möchten, klicken Sie erst auf die Registerkarte **Product Showcase** und anschließend auf **Entfernen**.

## <a name="next-steps"></a>Nächste Schritte

In diesem Thema haben Sie erfahren, wie Sie die Beispiel-App für Product Showcase erst zum Teams-Kanal hinzufügen und dann die App über diesen Kanal öffnen können. Weitere Informationen zu PowerApps finden Sie in den entsprechenden Tutorials.

> [!div class="nextstepaction"]
> [PowerApps-Tutorials](../maker/canvas-apps/get-started-create-from-blank.md)
