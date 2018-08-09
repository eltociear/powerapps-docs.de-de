---
title: Herunterladen einer Liste der aktiven Benutzer in Ihrem Mandanten | Microsoft-Dokumentation
description: In diesem Schnellstart erfahren Sie, wie Sie eine Liste der aktiven Benutzer in Ihrem Mandanten herunterladen können.
author: jimholtz
ms.service: powerapps
ms.component: pa-admin
ms.topic: quickstart
ms.date: 03/21/2018
ms.author: jimholtz
ms.openlocfilehash: e2c00f4ab10b2dc6cecc63d9539ffcf86a5bfcb8
ms.sourcegitcommit: 2e7b621066cdc3e7be329d5213ecfee0b4223641
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/30/2018
ms.locfileid: "39348855"
---
# <a name="download-a-list-of-active-users-in-your-tenant"></a>Herunterladen einer Liste der aktiven Benutzer in Ihrem Mandanten
Wenn Sie über globale Administratorberechtigungen für Office 365 oder über Mandantenberechtigungen für Azure Active Directory verfügen, können Sie eine Liste der aktiven Benutzer in Ihrem Mandanten herunterladen, über die Sie nachverfolgen können, wer auf PowerApps und bzw. oder Microsoft Flow zugegriffen hat und welche Lizenzen den Benutzern zugewiesen sind.

In diesem Artikel erfahren Sie, wie Sie eine Liste der aktiven Benutzer als CSV-Datei herunterladen können und wie Sie diese Liste anschließend in Excel öffnen können.

Damit Sie die in diesem Artikel beschriebenen Schritte ausführen können, benötigen Sie globale Administratorrechte für Office 365 oder Mandantenadministratorrechte für Azure Active Directory.

## <a name="sign-in-to-the-powerapps-admin-center"></a>Anmelden im PowerApps Admin Center
Melden Sie sich unter [https://admin.powerapps.com]([https://admin.powerapps.com) im Admin Center an.

## <a name="download-the-list-of-users"></a>Herunterladen der Benutzerliste
Klicken oder tippen Sie im Navigationsbereich erst auf **Benutzerlizenzen** und dann auf **Download a list of active user licenses** (Eine Liste der aktiven Benutzerlizenzen herunterladen).

![Datei > Freigeben](./media/admin-view-user-licenses/download-list.png)

Die Liste der Benutzer wird in einer CSV-Datei heruntergeladen. Dies kann einige Minuten dauern. Achten Sie darauf, das Fenster erst zu schließen, wenn die Liste vollständig heruntergeladen wurde. Ansonsten müssen Sie den Download möglicherweise neu starten.

## <a name="view-the-list"></a>Anzeigen der Liste
Öffnen Sie die heruntergeladene CSV-Datei anschließend in Excel. Die Liste enthält u.a. den Namen, die E-Mail-Adresse und den Lizenztyp der einzelnen Benutzer.

Ein *aktiver Benutzer* ist ein Benutzer, der mindestens einmal auf das Produkt zugegriffen hat. Da in der Liste nur aktive Benutzer enthalten sind, können Sie darin keine Benutzer finden, die zwar über Lizenzen für PowerApps und Microsoft Flow verfügen, aber noch nie auf diese Produkte zugegriffen haben. Im [Office 365 Admin Center](https://support.office.com/article/Assign-or-remove-licenses-for-Office-365-for-business-997596b5-4173-4627-b915-36abac6786dc) können Sie alle Benutzerlizenzen abrufen.

Das folgende Beispiel zeigt zwei Benutzer, die über unterschiedliche Lizenzen für PowerApps und Microsoft Flow verfügen. Jane Doe hat über ein Abonnement für Office 365 Zugriff und John Doe verfügt über Testlizenzen für beide Produkte.

![Datei > Freigeben](./media/admin-view-user-licenses/table2.png)

Wenn ein Benutzer die Organisation verlassen hat, steht **Unbekannt** in den Spalten **Benutzername** und **E-Mail-Adresse**. Wenn in der Liste **Unbekannt** steht, aber keine Benutzer die Organisation verlassen haben, warten Sie einige Minuten und laden die Liste dann erneut herunter.

Um Benutzerlizenzen hinzuzufügen, öffnen Sie das [Office 365 Admin Center](https://support.office.com/article/Assign-or-remove-licenses-for-Office-365-for-business-997596b5-4173-4627-b915-36abac6786dc).

## <a name="next-steps"></a>Nächste Schritte
In diesem Artikel wurde erläutert, wie Sie eine Liste der aktiven Benutzer in Ihrem Mandanten herunterladen können. Fahren Sie mit dem nächsten Artikel fort, um zu erfahren, wie Sie eine Liste der Apps herunterladen und anzeigen, die in Ihren Umgebungen erstellt wurden.

> [!div class="nextstepaction"]
> [Download a list of apps created in your environments (Herunterladen einer Liste der Apps, die in Ihrer Umgebung erstellt wurden)](admin-view-apps.md)
