---
title: 'Schnellstart: Herunterladen einer Liste der Apps, die in Ihren Umgebungen erstellt wurden | Microsoft-Dokumentation'
description: In diesem Schnellstart erfahren Sie, wie Sie eine Liste der Apps herunterladen können, die in Ihren Umgebungen erstellt wurden.
author: jimholtz
ms.service: powerapps
ms.component: pa-admin
ms.topic: quickstart
ms.date: 03/21/2018
ms.author: jimh
ms.openlocfilehash: d9c379ca95bb299c56639bb01803f45c1744d8f2
ms.sourcegitcommit: 68fc13fdc2c991c499ad6fe9ae1e0f8dab597139
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34552597"
---
# <a name="quickstart-download-a-list-of-apps-created-in-your-environments"></a>Schnellstart: Herunterladen einer Liste der Apps, die in Ihren Umgebungen erstellt wurden
Wenn Sie über die Umgebungsadministratorrolle verfügen, können Sie eine Liste der Apps abrufen und herunterladen, die Sie in den Umgebungen erstellt haben, die Sie verwalten. Wenn Sie über globale Administratorberechtigungen für 365 oder über Mandandenadministratorberechtigungen für Azure Active Directory verfügen, können Sie eine Liste der Apps herunterladen, die Sie in allen Umgebungen Ihrer Organisation erstellt haben.

In diesem Schnellstart erfahren Sie, wie Sie eine Liste der Apps, die in einer einzelnen Umgebung erstellt wurden, als CSV-Datei herunterladen können und wie Sie diese Liste anschließend in Excel öffnen können.

## <a name="prerequisites"></a>Voraussetzungen
 Für diesen Schnellstart sind die folgenden Elemente erforderlich:
 * Entweder eine Lizenz von PowerApps-Plan 2 oder von Microsoft Flow-Tarif 2. Sie können sich alternativ auch für eine [kostenlose Testversion von PowerApps-Plan 2](https://web.powerapps.com/signup?redirect=marketing&email=) registrieren.
 * PowerApps-Umgebungsadministratorberechtigungen, globale Office 365-Administratorberechtigungen oder Azure Active Directory-Mandantenadministratorberechtigungen. Weitere Informationen finden Sie unter [Environments administration in PowerApps (Verwalten von Umgebungen in PowerApps)](environments-administration.md).

## <a name="sign-in-to-the-powerapps-admin-center"></a>Anmelden im PowerApps Admin Center
Melden Sie sich unter [https://admin.powerapps.com]([https://admin.powerapps.com) im Admin Center an.

## <a name="download-the-list-of-apps"></a>Herunterladen der App-Liste
1. Klicken oder tippen Sie im Navigationsbereich erst auf **Umgebungen** und dann auf die Umgebung, für die Sie die Liste der Apps herunterladen möchten.

    ![Datei > Freigeben](./media/admin-view-apps/environment.png)
2. Klicken oder tippen Sie auf der Registerkarte **Ressourcen** erst auf **Apps** und dann auf **Download the list of apps** (Die Liste der Apps herunterladen).

    ![Datei > Freigeben](./media/admin-view-apps/resources-app.png)

    Die Liste der Apps wird als CSV-Datei heruntergeladen. Dies kann einige Minuten dauern. Achten Sie darauf, das Fenster erst zu schließen, wenn die Liste vollständig heruntergeladen wurde. Ansonsten müssen Sie den Download möglicherweise neu starten.

## <a name="view-the-list"></a>Anzeigen der Liste
Öffnen Sie die heruntergeladene CSV-Datei anschließend in Excel. Die Liste enthält den Anzeigenamen der App, den Besitzer der App, alle Connectors, die von der App zum Verbinden mit Datenquellen verwendet werden, sowie weitere Informationen.

![Datei > Freigeben](./media/admin-view-apps/excel-view.png)

## <a name="next-steps"></a>Nächste Schritte
In diesem Schnellstart haben Sie erfahren, wie Sie eine Liste der Apps herunterladen können, die in einer bestimmten Umgebung in Ihrer Organisation erstellt wurden, und wie Sie diese Liste anschließend abrufen können. Im nächsten Schritt erfahren Sie, wie Sie in Ihrer Organisation erstellte Apps verwalten.

> [!div class="nextstepaction"]
> [Verwalten von in Ihrer Organisation erstellten Apps](admin-manage-apps.md)
