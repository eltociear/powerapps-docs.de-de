---
title: Übersicht über das Admin Center für Power Apps-Portale | Microsoft-Dokumentation
description: Informationen zum Admin Center für Power Apps-Portale
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 0996704ccbc10f81b95c41d86234ca626a33a345
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2019
ms.locfileid: "2867397"
---
# <a name="power-apps-portals-admin-center"></a>Admin Center für Power Apps-Portale

Das Admin Center für Power Apps-Portale ermöglicht die Durchführung erweiterter administrativer Vorgänge auf Portalen. Das Admin Center ist verfügbar, wenn ein Portal ordnungsgemäß bereitgestellt wird.

## <a name="open-power-apps-portals-admin-center"></a>Öffnen Sie das Admin Center für Power Apps-Portale

1. Wechseln Sie zum Abschnitt **Kürzlich verwendete Apps** auf der Power Apps-Homepage, und suchen Sie Ihr Portal.

    > [!div class=mx-imgBorder]
    > ![Neueste Apps](../media/recent-apps.png "Neueste Apps")  

2. Wählen Sie **Weitere Befehle (...)** > **Einstellungen** aus.

    > [!div class=mx-imgBorder]
    > ![Option Portaleinstellungen](../media/portal-settings-option.png "Option Portaleinstellungen")

3. Wählen Sie unter **Portaleinstellungen** die Option **Administration** aus.

    > [!div class=mx-imgBorder]
    > ![Bereich Portaleinstellungen](../media/portal-settings-admin.png "Bereich Portaleinstellungen")

## <a name="add-yourself-as-an-owner-of-the-azure-ad-application"></a>Fügen Sie sich als Besitzer der Azure AD-Anwendung hinzu

Wenn Sie kein globaler Administrator sind und Sie versuchen, ein bereits bereitgestelltes Portal zu verwalten oder die Bereitstellung erneut zu senden, wenn sie gescheitert ist, müssen Sie der Besitzer der Azure Active Directory (Azure AD)-Anwendung sein, die mit dem Portal verbunden ist.

1. Gehen Sie zum Power Apps Admin-Center für Portale und öffnen Sie die Registerkarte **Portaldetails**.

2. Kopieren Sie den Wert aus dem Feld **Anwendungs-ID**.

    > [!div class=mx-imgBorder]
    > ![Registerkarte Portaldetails](../media/portal-details-admin.png "Registerkarte Portaldetails")

3. Gehen Sie zur Azure AD, das Ihrem Tenant zugeordnet ist. [!include[](../../../includes/proc-more-information.md)] [Ein nicht verwaltetes Verzeichnis als Administrator in Azure Active Directory übernehmen](https://docs.microsoft.com/azure/active-directory/active-directory-manage-o365-subscription)

4. In Azure AD suchen Sie nach der App-Registrierung mithilfe der Anwendungs-ID, die Sie kopiert haben. Gegebenenfalls müssen Sie von **Meine Apps** auf **Alle Apps** ändern.

5. Fügen Sie Benutzer oder Gruppen als Besitzer dieser App-Anmeldung hinzu. [!include[](../../../includes/proc-more-information.md)] [Verwalten von Zugriff auf Apps](https://docs.microsoft.com/azure/active-directory/active-directory-managing-access-to-apps)

    > [!Note]
    > Diese Aufgabe kann vom einem globalen Administrator Ihrer Organisation oder dem vorhandenen Besitzers dieser Anwendung ausgeführt werden.

6. Nachdem Sie sich selbst als Besitzer hinzugefügt haben, öffnen Sie die Power Apps Portaladministrator-Centerseite erneut.