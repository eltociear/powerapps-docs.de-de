---
title: Übersicht über das powerapps-Portal Admin Center | MicrosoftDocs
description: Informationen zum powerapps-Portal Admin Center.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 6f8434a6a395931fc4edfe02913f47536b4a709d
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73543075"
---
# <a name="powerapps-portals-admin-center"></a>Powerapps-Portale Admin Center

Das Admin Center für die powerapps-Portale ermöglicht das Ausführen erweiterter administrativer Aktionen in Portalen. Das Admin Center ist verfügbar, wenn ein Portal erfolgreich bereitgestellt wurde.

## <a name="open-powerapps-portals-admin-center"></a>Powerapps-Portale Admin Center öffnen

1. Wechseln Sie auf der powerapps-Startseite zum Abschnitt **zuletzt verwendete apps** , und suchen Sie Ihr Portal.

    > [!div class=mx-imgBorder]
    > ![Zuletzt verwendete apps](../media/recent-apps.png "Zuletzt verwendete apps")  

2. Wählen Sie **Weitere Befehle (...)**  > **Einstellungen**aus.

    > [!div class=mx-imgBorder]
    > ![Option "Portal Einstellungen"](../media/portal-settings-option.png "Option "Portal Einstellungen"")

3. Wählen Sie im Bereich " **Portal Einstellungen** " die Option **Verwaltung**aus.

    > [!div class=mx-imgBorder]
    > ![Bereich "Portal Einstellungen"](../media/portal-settings-admin.png "Bereich "Portal Einstellungen"")

## <a name="add-yourself-as-an-owner-of-the-azure-ad-application"></a>Fügen Sie sich als Besitzer der Azure AD Anwendung hinzu.

Wenn Sie kein globaler Administrator sind und versuchen, ein Portal zu verwalten, das bereits bereitgestellt wurde, oder wenn Sie die Bereitstellung bei einem Fehler erneut übermitteln, müssen Sie der Besitzer der Azure Active Directory (Azure AD)-Anwendung sein, die mit Ihrem Portal verbunden ist.

1. Wechseln Sie zum powerapps-Portal Admin Center, und öffnen Sie die Registerkarte " **Portal Details** ".

2. Kopieren Sie den Wert aus dem Feld **Anwendungs-ID** .

    > [!div class=mx-imgBorder]
    > ![Registerkarte "Portals"](../media/portal-details-admin.png "Registerkarte "Portals"")

3. Wechseln Sie zu Azure AD, die Ihrem Mandanten zugeordnet ist. [!include[](../../../includes/proc-more-information.md)] [übernehmen Sie ein nicht verwaltetes Verzeichnis als Administrator in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-manage-o365-subscription)

4. Suchen Sie in Azure AD nach der APP-Registrierung, indem Sie die von Ihnen kopierte Anwendungs-ID verwenden. Möglicherweise müssen Sie von " **meine apps** " zu " **alle apps**" wechseln.

5. Fügen Sie Benutzer oder Gruppen als Besitzer dieser APP-Registrierung hinzu. [!include[](../../../includes/proc-more-information.md)] [Verwalten des Zugriffs auf apps](https://docs.microsoft.com/azure/active-directory/active-directory-managing-access-to-apps)

    > [!Note]
    > Diese Aufgabe kann entweder von einem globalen Administrator Ihrer Organisation oder dem vorhandenen Besitzer dieser Anwendung ausgeführt werden.

6. Nachdem Sie sich selbst als Besitzer hinzugefügt haben, öffnen Sie die Seite "powerapps-Portale Admin Center" erneut.