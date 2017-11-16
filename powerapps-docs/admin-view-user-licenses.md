---
title: Anzeigen von Benutzerlizenzen | Microsoft-Dokumentation
description: "Administratoren können eine Liste der Benutzerlizenzen für PowerApps und Microsoft Flow herunterladen."
services: 
suite: powerapps
documentationcenter: na
author: manasmamsft
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 05/02/2017
ms.author: manasma
ms.openlocfilehash: ba60c227b287532f6abe2e2b2e88f6cbe7dd0cd3
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2017
---
# <a name="identify-powerapps-users-in-your-organization"></a>Ermitteln der PowerApps-Benutzer in Ihrer Organisation
Als globaler Administrator für Office 365 oder Mandantenadministrator für Azure Active Directory können Sie eine Liste der Benutzer in Ihrer Organisation herunterladen, die nicht nur über Lizenzen für PowerApps und/oder Microsoft Flow verfügen, sondern auch auf eines dieser Produkte zugegriffen haben. Die Liste enthält u.a. den Namen, die E-Mail-Adresse und den Lizenztyp der einzelnen Benutzer. Beispiele für Benutzerlizenzen:

* Testlizenz für PowerApps oder Microsoft Flow
* Zugriff auf beide Produkte über eine Office 365-Lizenz
* Zugriff auf beide Produkte über eine Dynamics 365-Lizenz
* Zugriff über PowerApps- und Microsoft Flow-Pläne

## <a name="download-the-list-of-users"></a>Herunterladen der Benutzerliste
1. Klicken oder tippen Sie im PowerApps Admin Center am linken Rand auf **Benutzerlizenzen**.
   
    **Wichtig:** Diese Option ist nur für globale Administratoren von Office 365 und Mandantenadministratoren von Azure Active Directory verfügbar.
   
    ![Datei > Freigeben](./media/admin-view-user-licenses/leftnav.png)
2. Klicken oder tippen Sie auf **Download a list of active user licenses** (Liste der aktiven Benutzerlizenzen herunterladen).
   
    ![Datei > Freigeben](./media/admin-view-user-licenses/download-list.png)
   
    Der Download der Datei kann einige Minuten dauern. Warten Sie, bis die CSV-Datei heruntergeladen wurde, und öffnen Sie sie dann in Excel.
   
    **Hinweis:** Wenn Sie das Fenster schließen, bevor der Dateidownload abgeschlossen ist, müssen Sie den Vorgang möglicherweise von vorne beginnen.

Dieses Beispiel zeigt zwei Benutzer, die über unterschiedliche Lizenzen für PowerApps und Microsoft Flow verfügen. Jane Doe hat über ein Abonnement für Office 365 Zugriff und John Doe verfügt über Testlizenzen für beide Produkte.

![Datei > Freigeben](./media/admin-view-user-licenses/table2.png)

Benutzer mit Lizenzen für PowerApps und Microsoft Flow, die noch nie auf diese Produkte zugegriffen haben, werden in der Liste nicht aufgeführt. Im [Office 365 Admin Center][1] können Sie alle Benutzerlizenzen abrufen.

Wenn ein Benutzer die Organisation verlassen hat, steht **Unbekannt** in Spalten wie **Benutzername** und **E-Mail-Adresse**. Wenn in der Liste **Unbekannt** steht, aber keine Benutzer die Organisation verlassen haben, warten Sie einige Minuten und laden die Liste dann erneut herunter.

Um Benutzerlizenzen hinzuzufügen, öffnen Sie das [Office 365 Admin Center][1].

<!--Reference links in article-->
[1]:https://support.office.com/article/Assign-or-remove-licenses-for-Office-365-for-business-997596b5-4173-4627-b915-36abac6786dc
