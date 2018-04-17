---
title: Hinzufügen einer App zu Microsoft Teams | Microsoft-Dokumentation
description: Fügen Sie einem Microsoft Teams-Kanal eine App hinzu, damit alle Benutzer, für die die App freigeben wurde, diese in diesem Kanal öffnen können.
services: ''
suite: powerapps
documentationcenter: na
author: mgblythe
manager: anneta
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: quickstart
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 01/18/2018
ms.author: mblythe
ms.openlocfilehash: 02248cc3e98f256df36bb6a57fac6e66c684a8bf
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2018
---
# <a name="quickstart-add-an-app-to-microsoft-teams"></a>Schnellstart: Hinzufügen einer App zu Microsoft Teams

Bei Microsoft Teams handelt es sich im eine auf Chats basierende Plattform für die Zusammenarbeit, die auf Office 365-Technologien aufbaut. Sie können die Benutzerfreundlichkeit von Microsoft Teams verbessern, indem Sie Ihrem Kanal in Microsoft Teams mit PowerApps generierte Canvas-Apps hinzufügen. In diesem Schnellstart erfahren Sie, wie Sie die Beispiel-App für Product Showcase erst zu dem Teams-Kanal hinzufügen und dann die App über diesen Kanal öffnen. 

![In Microsoft Teams eingebettete App](./media/open-app-embedded-in-teams/embedded-app.png)

Wenn Sie noch nicht bei PowerApps registriert sind, müssen Sie sich zuerst [kostenlos registrieren](https://web.powerapps.com/signup?redirect=marketing&email=).

## <a name="prerequisites"></a>Voraussetzungen

Sie benötigen für diesen Schnellstart ein [Office 365-Abonnement](https://signup.microsoft.com/Signup?OfferId=467eab54-127b-42d3-b046-3844b860bebf&dl=O365_BUSINESS_PREMIUM&ali=1) und einen [Kanal in Microsoft Teams](https://www.youtube.com/watch?v=he2f1quaR7M).

## <a name="sign-in-to-powerapps"></a>Anmelden bei PowerApps

Melden Sie sich unter [https://web.powerapps.com]([https://web.powerapps.com) in PowerApps an.

## <a name="add-an-app"></a>Hinzufügen einer App

1. Wählen Sie in Microsoft Teams ein Team und einen Kanal des Teams aus. In diesem Beispiel wird der Kanal **Allgemein** des Teams **Business Development** verwendet.

    ![](./media/open-app-embedded-in-teams/teams-select-channel.png)

2. Klicken Sie auf **+**, um eine Registerkarte hinzuzufügen.

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
* Nur diese Audio-Formate werden unterstützt: AAC, H264 OGG Vorbis und WAV.

## <a name="clean-up-resources"></a>Bereinigen von Ressourcen

Wenn Sie die App aus dem Kanal entfernen möchten, klicken Sie erst auf die Registerkarte **Product Showcase** und anschließend auf **Entfernen**.

## <a name="next-steps"></a>Nächste Schritte

In diesem Schnellstart haben Sie erfahren, wie Sie die Beispiel-App für Product Showcase erst zum Teams-Kanal hinzufügen und dann die App über diesen Kanal öffnen können. Weitere Informationen zu PowerApps finden Sie in den entsprechenden Tutorials.

> [!div class="nextstepaction"]
> [PowerApps-Tutorials](../maker/canvas-apps/get-started-create-from-blank.md)